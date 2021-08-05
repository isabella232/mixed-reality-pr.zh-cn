---
title: 创建空间感知数据提供程序
description: 介绍如何在 MRTK 中创建自定义数据提供程序
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 05186c418a7b0b7b143abc58be6a6afb64cb69f5a1c90c73ed516d51c2a5d8ea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188843"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a>创建空间感知系统数据提供程序

空间感知系统是一个可扩展的系统，用于向应用程序提供有关实际环境的数据。 若要添加对新硬件平台或新形式的空间感知数据的支持，可能需要自定义数据提供程序。

本文介绍如何 [为空间感知](../../architecture/systems-extensions-providers.md)系统创建自定义数据提供程序（也称为空间观察器）。 此处显示的示例代码来自 类实现，该类实现可用于在编辑器中加载 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) [3D 网格数据](spatial-object-mesh-observer.md)。

> [!NOTE]
> 可以在 文件夹中找到此示例中使用的完整 `Assets/MRTK/Providers/ObjectMeshObserver` 源代码。

## <a name="namespace-and-folder-structure"></a>命名空间和文件夹结构

可通过两种方式之一分发数据提供程序：

1. 第三方加载项
1. Microsoft Mixed Reality Toolkit

向 MRTK 提交新数据提供程序的审批过程将因情况而异，将在初始建议时传达。 可以通过创建新的功能请求类型问题 [*来提交* 建议](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)。

### <a name="third-party-add-on"></a>第三方加载项

**命名空间**

数据提供程序需要具有命名空间来缓解潜在的名称冲突。 建议命名空间包含以下组件。

- 生成加载项的公司名称
- 功能区域

例如，Contoso 公司创建和交付的空间感知数据提供程序可能是 *"Contoso.MixedReality.Toolkit。SpatialAwareness"*。

**文件夹结构**

建议将数据提供程序的源代码布局在文件夹层次结构中，如下图所示。

![文件夹结构示例](../images/spatial-awareness/ExampleProviderFolderStructure.png)

其中 *ContosoSpatialAwareness* 文件夹包含数据提供程序的实现，Editor文件夹包含检查器 (和任何其他特定于 Unity 编辑器的代码) ，而 *Profiles* 文件夹包含一个或多个预生成配置文件可脚本化对象。

### <a name="mrtk-submission"></a>MRTK 提交

**命名空间**

如果将空间感知系统数据提供程序提交到混合现实Toolkit [存储库](https://github.com/Microsoft/MixedRealityToolkit-Unity)，则命名空间 **必须以** Microsoft.MixedReality 开头。*Toolkit (：Microsoft.MixedReality.Toolkit。SpatialObjectMeshObserver)*

 和代码应位于 MRTK/Providers 文件夹下的文件夹中 (例如 *：MRTK/Providers/ObjectMeshObserver*) 。

**文件夹结构**

所有代码都应位于 MRTK/Providers 文件夹下的文件夹中 (例如：MRTK/Providers/ObjectMeshObserver) 。

## <a name="define-the-spatial-data-object"></a>定义空间数据对象

创建空间感知数据提供程序的第一步是确定数据类型，例如 (网格或平面) 向应用程序提供。

所有空间数据对象都必须实现 [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) 接口。

混合现实Toolkit基础提供了以下空间对象，这些空间对象可在新的数据访问提供程序中使用或扩展。

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a>实现数据提供程序

### <a name="specify-interface-andor-base-class-inheritance"></a>指定接口和/或基类继承

所有空间感知数据提供程序都必须实现 接口，该接口指定空间感知系统所需的 [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 最低功能。 MRTK 基础包括 [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) 类，该类提供此所需功能的默认实现。

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)类使用 接口来指示它为 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) SpatialAwarenessMesh 功能提供支持。

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>应用 MixedRealityDataProvider 属性

创建空间感知数据提供程序的一个关键步骤是将 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 属性应用于 类。 在空间感知配置文件中选中 (文件夹路径) ，此步骤将启用为数据访问接口设置默认配置文件和平台名称。

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealitySpatialAwarenessSystem),
    SupportedPlatforms.WindowsEditor | SupportedPlatforms.MacEditor | SupportedPlatforms.LinuxEditor,
    "Spatial Object Mesh Observer",
    "ObjectMeshObserver/Profiles/DefaultObjectMeshObserverProfile.asset",
    "MixedRealityToolkit.Providers")]
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>实现 IMixedRealityDataProvider 方法

定义 类后，下一步是提供 接口的 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 实现。

> [!NOTE]
> 类 [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) 通过 类 [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) 仅提供方法的空 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 实现。 这些方法的详细信息通常特定于数据提供程序。

数据提供程序应实现的方法包括：

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>实现数据提供程序逻辑

下一步是通过实现特定数据提供程序接口（例如 ）来添加数据提供程序的逻辑 [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) 。 数据提供程序的这一部分通常特定于平台。

### <a name="observation-change-notifications"></a>观察更改通知

为了允许应用程序响应设备对环境理解的更改，数据提供程序按照 接口中的定义引发 [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) 通知事件。

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 示例中的以下代码 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 演示添加网格数据时引发 和 事件。

```c#
// The data to be sent when mesh observation events occur.
// This member variable is initialized as part of the Initialize() method.
private MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> meshEventData = null;

/// <summary>
/// Sends the observations using the mesh data contained within the configured 3D model.
/// </summary>
private void SendMeshObjects()
{
    if (!sendObservations) { return; }

    if (spatialMeshObject != null)
    {
        MeshFilter[] meshFilters = spatialMeshObject.GetComponentsInChildren<MeshFilter>();
        for (int i = 0; i < meshFilters.Length; i++)
        {
            SpatialAwarenessMeshObject meshObject = SpatialAwarenessMeshObject.Create(
                meshFilters[i].sharedMesh,
                MeshPhysicsLayer,
                $"Spatial Object Mesh {currentMeshId}",
                currentMeshId,
                ObservedObjectParent);

            meshObject.GameObject.transform.localPosition = meshFilters[i].transform.position;
            meshObject.GameObject.transform.localRotation = meshFilters[i].transform.rotation;

            ApplyMeshMaterial(meshObject);

            meshes.Add(currentMeshId, meshObject);

            // Initialize the meshEventData variable with data for the added event.
            meshEventData.Initialize(this, currentMeshId, meshObject);
            // Raise the event via the spatial awareness system.
            SpatialAwarenessSystem?.HandleEvent(meshEventData, OnMeshAdded);

            currentMeshId++;
        }
    }

    sendObservations = false;
}
```

> [!NOTE]
> [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver)类不会引发 `OnObservationUpdated` 事件，因为 3D 模型只加载一次。 类中的 [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 实现提供了为观察到的网格 `OnObservationUpdated` 引发事件的示例。

### <a name="add-unity-profiler-instrumentation"></a>添加 Unity Profiler 检测

性能在混合现实应用程序中至关重要。 每个组件都会增加应用程序必须考虑到的一些开销。 为此，所有空间感知数据提供程序在内部循环和经常使用的代码路径中包含 Unity Profiler 检测非常重要。

建议在检测自定义提供程序时实现 MRTK 使用的模式。

```c#
        private static readonly ProfilerMarker UpdateObserverPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealitySpatialMeshObserver.UpdateObserver");

        /// <summary>
        /// Requests updates from the surface observer.
        /// </summary>
        private void UpdateObserver()
        {
            using (UpdateObserverPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> 用于标识探查器标记的名称是任意的。 MRTK 采用以下模式。
>
> "[product] className.methodName - 可选备注"
>
> 建议自定义数据提供程序遵循类似的模式，以帮助简化分析跟踪时特定组件和方法的标识。

## <a name="create-the-profile-and-inspector"></a>创建配置文件和检查器

在混合现实Toolkit中，数据提供程序是使用配置文件[配置的](../profiles/profiles.md)。

### <a name="define-the-profile"></a>定义配置文件

配置文件内容应镜像数据访问接口的可访问属性 (例如：更新间隔) 。 每个接口中定义的所有用户可配置属性都应与配置文件一起包含。

如果新的数据访问接口扩展了现有提供程序，则建议使用基类。 例如， 扩展 了 ，使客户能够 [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) 提供要用作环境数据的 3D 模型。

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Spatial Object Mesh Observer Profile",
    fileName = "SpatialObjectMeshObserverProfile",
    order = 100)]
public class SpatialObjectMeshObserverProfile : MixedRealitySpatialAwarenessMeshObserverProfile
{
    [SerializeField]
    [Tooltip("The model containing the desired mesh data.")]
    private GameObject spatialMeshObject = null;

    /// <summary>
    /// The model containing the desired mesh data.
    /// </summary>
    public GameObject SpatialMeshObject => spatialMeshObject;
}
```

属性可应用于配置文件类，使客户能够使用"创建资产""混合现实"Toolkit `CreateAssetMenu`   >    >    >  **配置文件"菜单创建配置文件** 实例。

### <a name="implement-the-inspector"></a>实现检查器

配置文件检查器是配置和查看配置文件内容的用户界面。 每个配置文件检查器都应扩展 [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 类。

`CustomEditor`属性通知 Unity 检查器应用到的资产类型。

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a>创建程序集 () 

混合现实Toolkit使用程序集定义 ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 文件来指定组件之间的依赖关系，以及帮助 Unity 减少编译时间。

建议为所有数据提供程序及其编辑器组件创建程序集定义文件。

使用 [前面示例中](#namespace-and-folder-structure) 的文件夹结构，ContosoSpatialAwareness 数据提供程序将存在两个 .asmdef 文件。

第一个程序集定义用于数据访问接口。 对于此示例，它将称为 ContosoSpatialAwareness，将位于示例的 *ContosoSpatialAwareness* 文件夹中。 此程序集定义必须指定对 Microsoft.MixedReality 的依赖关系。Toolkit及其依赖的其他任何程序集。

ContosoInputEditor 程序集定义将指定配置文件检查器以及任何特定于编辑器的代码。 此文件必须位于编辑器代码的根文件夹中。 此示例中的文件将位于 *ContosoSpatialAwareness\Editor* 文件夹中。 此程序集定义将包含对 ContosoSpatialAwareness 程序集的引用，以及：

- Microsoft.MixedReality。Toolkit
- Microsoft.MixedReality。Toolkit。Editor.Inspectors
- Microsoft.MixedReality。Toolkit。Editor.Utilities

## <a name="register-the-data-provider"></a>注册数据提供程序

创建后，可以将数据提供程序注册到空间感知系统，以在应用程序中使用。

![选择空间对象网格观察程序](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a>打包和分发

作为第三方组件分发的数据提供程序具有开发人员偏好的打包和分发的特定详细信息。 最常见的解决方案可能是生成 .unitypackage，然后通过 Unity 资产存储进行分发。

如果提交数据提供程序并将其作为 Microsoft Mixed Reality Toolkit 包的一部分接受，Microsoft MRTK 团队将打包并分发它作为 MRTK 产品/服务一部分。

## <a name="see-also"></a>另请参阅

- [空间感知系统](spatial-awareness-getting-started.md)
- [`IMixedRealitySpatialAwarenessObject` 接口](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [`BaseSpatialAwarenessObject` 类](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject` 类](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject` 类](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [`IMixedRealitySpatialAwarenessObserver` 接口](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [`BaseSpatialObserver` 类](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [`IMixedRealitySpatialAwarenessMeshObserver` 接口](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [`IMixedRealityDataProvider` 接口](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` 接口](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
