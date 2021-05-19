---
title: 创建空间感知数据提供程序
description: 介绍如何在 MRTK 中创建自定义数据提供程序
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 04a0cdbd18f666b6a99c120eb28966234cc8c92d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145149"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a>创建空间感知系统数据提供程序

空间感知系统是一个可扩展的系统，用于向应用程序提供有关实际环境的数据。 若要添加对新硬件平台或新形式的空间感知数据的支持，可能需要自定义数据提供程序。

本文介绍如何 [为空间感知](../../architecture/systems-extensions-providers.md)系统创建自定义数据提供程序（也称为空间观察器）。 此处显示的示例代码来自 类实现，该类实现可用于在编辑器中加载 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) [3D 网格数据](spatial-object-mesh-observer.md)。

> [!NOTE]
> 可以在 文件夹中找到此示例中使用的完整 `Assets/MRTK/Providers/ObjectMeshObserver` 源代码。

## <a name="namespace-and-folder-structure"></a>命名空间和文件夹结构

可通过两种方式之一分发数据提供程序：

1. 第三方加载项
1. Microsoft Mixed Reality Toolkit 的一部分

向 MRTK 提交新数据提供程序的审批过程将因情况而异，将在初始建议时传达。 可以通过创建新的功能请求类型问题 [*来提交* 建议](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)。

### <a name="third-party-add-on"></a>第三方加载项

**命名空间**

数据提供程序需要具有命名空间来缓解潜在的名称冲突。 建议命名空间包含以下组件。

- 生成加载项的公司名称
- 功能区域

例如，Contoso 公司创建和交付的空间感知数据提供程序可能是 *"Contoso.MixedReality.Toolkit.SpatialAwareness"。*

**文件夹结构**

建议将数据提供程序的源代码布局在文件夹层次结构中，如下图所示。

![文件夹结构示例](../images/spatial-awareness/ExampleProviderFolderStructure.png)

其中， *ContosoSpatialAwareness* 文件夹包含数据提供程序的实现， *Editor* 文件夹包含检查器 (和任何其他特定于 Unity 编辑器的代码) ，而 profile *文件夹包含* 一个或多个预生成的配置文件可脚本化对象。

### <a name="mrtk-submission"></a>MRTK 提交

**命名空间**

如果将空间感知系统数据提供程序提交到 [混合现实工具包存储库](https://github.com/Microsoft/MixedRealityToolkit-Unity)，命名空间 **必须** 以 MixedReality 开头 (例如： *SpatialObjectMeshObserver*) 

 代码应位于 MRTK/Providers 下的文件夹中 (例如： *MRTK/providers/ObjectMeshObserver*) 。

**文件夹结构**

所有代码都应位于 MRTK/Providers 下的文件夹中 (例如： MRTK/Providers/ObjectMeshObserver) 。

## <a name="define-the-spatial-data-object"></a>定义空间数据对象

创建空间感知数据提供程序的第一步是确定数据类型 (例如：网格或平面将提供给应用程序) 。

所有空间数据对象必须实现 [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) 接口。

混合现实工具包基础提供了以下可以在新的数据提供程序中使用或扩展的空间对象。

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a>实现数据访问接口

### <a name="specify-interface-andor-base-class-inheritance"></a>指定接口和/或基类继承

所有空间感知数据提供程序必须实现 [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 接口，该接口指定空间感知系统所需的最小功能。 MRTK foundation 包含 [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) 类，该类提供此所需功能的默认实现。

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)接口由 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 类用来指示它提供对 SpatialAwarenessMesh 功能的支持。

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>应用 MixedRealityDataProvider 特性

创建空间感知数据提供程序的一个关键步骤是将属性应用于 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 类。 此步骤可用于设置数据提供程序的默认配置文件和平台 () ，以及在空间感知配置文件中选择的配置文件和平台，以及名称、文件夹路径等。

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

一旦定义了类，下一步就是提供接口的实现 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。

> [!NOTE]
> [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)类通过 [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) 类只为方法提供空实现 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。 这些方法的详细信息通常是特定于数据访问接口的。

应由数据提供程序实现的方法如下：

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>实现数据访问接口逻辑

下一步是通过实现特定的数据提供程序接口来添加数据提供程序的逻辑，例如 [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) 。 数据访问接口的此部分通常是特定于平台的。

### <a name="observation-change-notifications"></a>观察更改通知

为了使应用程序能够响应设备对环境的了解更改，数据访问接口会引发接口中定义的通知事件 [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) 。

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 示例中的以下代码 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 演示了添加网格数据时的引发和事件。

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
> [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver)类不会引发 `OnObservationUpdated` 事件，因为3d 模型仅加载一次。 类中的实现 [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 提供了为 `OnObservationUpdated` 观察到的网格引发事件的示例。

### <a name="add-unity-profiler-instrumentation"></a>添加 Unity 探查器检测

性能在混合现实应用程序中非常重要。 每个组件都增加了应用程序必须考虑的一些开销。 为此，在内部循环中包含 Unity 探查器检测和经常使用的代码路径，这一点非常重要。

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
> 用于标识探查器标记的名称是任意的。 MRTK 使用以下模式。
>
> "[product] className. 方法名称-可选注释"
>
> 建议自定义数据访问接口遵循类似的模式，以帮助在分析跟踪时简化特定组件和方法的标识。

## <a name="create-the-profile-and-inspector"></a>创建配置文件和检查器

在混合现实工具包中，数据访问接口是使用 [配置文件](../profiles/profiles.md)配置的。

### <a name="define-the-profile"></a>定义配置文件

配置文件内容应镜像数据提供程序的可访问属性， (例如：更新间隔) 。 每个接口中定义的所有用户可配置属性都应包含在配置文件中。

如果新的数据提供程序扩展了现有的提供程序，则鼓励使用基类。 例如， [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) 扩展 [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) 以使客户能够提供将用作环境数据的三维模型。

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

`CreateAssetMenu`特性可应用到配置文件类，使客户能够使用 "**创建**  >  **资产**  >  **混合现实工具包**  >  **配置文件**" 菜单创建配置文件实例。

### <a name="implement-the-inspector"></a>实现检查器

配置文件检查器是用于配置和查看配置文件内容的用户界面。 每个配置文件检查器应扩展此 [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 类。

`CustomEditor`属性向 Unity 通知该检查器应用到的资产类型。

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a>创建 () 的程序集定义

混合现实工具包使用程序集 [定义 () ](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html) 文件来指定组件之间的依赖关系，并协助 Unity 减少编译时间。

建议为所有数据访问接口及其编辑器组件创建程序集定义文件。

使用前面示例中的 [文件夹结构](#namespace-and-folder-structure) ，ContosoSpatialAwareness 数据提供程序有两个 asmdef 文件。

第一个程序集定义适用于数据访问接口。 对于此示例，它将称为 ContosoSpatialAwareness，将位于示例的 *ContosoSpatialAwareness* 文件夹中。 此程序集定义必须指定对 Microsoft.MixedReality.Toolkit 及其依赖的其他任何程序集的依赖关系。

ContosoInputEditor 程序集定义将指定配置文件检查器以及任何特定于编辑器的代码。 此文件必须位于编辑器代码的根文件夹中。 此示例中的文件将位于 *ContosoSpatialAwareness\Editor* 文件夹中。 此程序集定义将包含对 ContosoSpatialAwareness 程序集的引用，以及：

- Microsoft.MixedReality.Toolkit
- Microsoft.MixedReality.Toolkit.Editor.Inspectors
- Microsoft.MixedReality.Toolkit.Editor.Utilities

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
- [`IMixedRealityDataProvider` 交互](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` 交互](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
