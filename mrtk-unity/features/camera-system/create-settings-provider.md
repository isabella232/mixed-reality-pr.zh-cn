---
title: 创建相机设置提供程序
description: MRTK 中相机设置的数据提供程序
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 5efab728905cd9885bf49f54b1939f3957cc5815af00dc816a4044a3f659b3bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210694"
---
# <a name="creating-a-camera-settings-provider"></a>创建相机设置提供程序

照相机系统是一个可扩展系统，用于为特定于平台的照相机配置提供支持。 若要添加对新相机配置的支持，可能需要使用自定义设置提供程序。

> [!NOTE]
> 在此示例中使用的完整源代码位于 **MRTK/Providers/UnityAR** 文件夹中。

## <a name="namespace-and-folder-structure"></a>命名空间和文件夹结构

可以通过以下两种方式之一分发数据提供程序：

1. 第三方加载项
1. Microsoft Mixed Reality Toolkit 的一部分

向 MRTK 提交新数据提供程序的批准过程将根据具体情况发生变化，并将在初始提议时进行传达。 可以通过创建新的 [*功能请求* 类型问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)来提交建议。

### <a name="third-party-add-ons"></a>第三方加载项

**命名空间**

数据访问接口需要有一个命名空间来缓解潜在的名称冲突。 建议命名空间包括以下组件。

- 生成外接程序的公司名称
- 功能区域

例如，Contoso 公司创建和发运的相机设置提供者可能是 *"Toolkit MixedReality"。照相机 "*。

**文件夹结构**

建议在文件夹层次结构中排列数据提供程序的源代码，如下图所示。

![文件夹结构示例](../images/camera-system/ExampleProviderFolderStructure.png)

其中， *ContosoCamera* 文件夹包含数据提供程序的实现， *Editor* 文件夹包含检查器 (和任何其他特定于 Unity 编辑器的代码) ，而 profile *文件夹包含* 一个或多个预生成的配置文件可脚本化对象。

### <a name="mrtk-submission"></a>MRTK 提交

**命名空间**

如果正在将照相机设置提供程序提交到 [混合现实 Toolkit 存储库](https://github.com/Microsoft/MixedRealityToolkit-Unity)，则命名空间 **必须** 以 MixedReality 开头。Toolkit (例如： *MixedReality. Toolkit。CameraSystem*) 。

**文件夹结构**

所有代码都必须位于 MRTK/Providers 下的文件夹中 (例如： MRTK/Providers/UnityAR) 。

## <a name="define-the-camera-settings-object"></a>定义相机设置对象

创建照相机设置提供程序的第一步是确定数据类型 (例如：网格或平面将提供给应用程序) 。

所有空间数据对象必须实现 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 接口。

## <a name="implement-the-settings-provider"></a>实现设置提供程序

### <a name="specify-interface-andor-base-class-inheritance"></a>指定接口和/或基类继承

所有照相机设置提供程序必须实现 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 接口，该接口指定了照相机系统所需的最小功能。 MRTK foundation 包含类， [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) 该类提供所需功能的默认实现。

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>应用 MixedRealityDataProvider 特性

创建照相机设置提供程序的一个关键步骤是将属性应用于 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 类。 此步骤允许在照相机系统配置文件中选择默认配置文件和平台 () ，并在名称、文件夹路径等中进行选择。

```c#
    [MixedRealityDataProvider(
        typeof(IMixedRealityCameraSystem),
        SupportedPlatforms.Android | SupportedPlatforms.IOS,
        "Unity AR Foundation Camera Settings",
        "UnityAR/Profiles/DefaultUnityARCameraSettingsProfile.asset",
        "MixedRealityToolkit.Providers")]
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>实现 IMixedRealityDataProvider 方法

一旦定义了类，下一步就是提供接口的实现 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。

> [!NOTE]
> [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1)类通过 [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) 类为方法提供空实现 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 。 这些方法的详细信息通常是特定于数据访问接口的。

应由数据提供程序实现的方法如下：

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> 并非所有的设置提供程序都需要所有这些方法的实现。 强烈建议 `Destroy()` `Initialize()` 至少实现和。

### <a name="implement-the-data-provider-logic"></a>实现数据访问接口逻辑

下一步是通过实现来添加设置提供程序的逻辑 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 。 数据访问接口的此部分通常是特定于照相机配置的。

## <a name="create-the-profile-and-inspector"></a>创建配置文件和检查器

在混合现实 Toolkit 中，使用[配置文件](../profiles/profiles.md)配置数据访问接口。

### <a name="define-the-profile"></a>定义配置文件

配置文件内容应镜像开发人员可选择的配置选项。 每个接口中定义的任何用户可配置属性也应包含在配置文件中。

```c#
using UnityEngine.SpatialTracking;

namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CreateAssetMenu(
        menuName = "Mixed Reality Toolkit/Profiles/Unity AR Camera Settings Profile",
        fileName = "UnityARCameraSettingsProfile",
        order = 100)]
    public class UnityARCameraSettingsProfile : BaseCameraSettingsProfile
    {
        [SerializeField]
        [Tooltip("The portion of the device (ex: color camera) from which to read the pose.")]
        private ArTrackedPose poseSource = TrackedPoseDriver.TrackedPose.ColorCamera;

        /// <summary>
        /// The portion of the device (ex: color camera) from which to read the pose.
        /// </summary>
        public ArTrackedPose PoseSource => poseSource;

        [SerializeField]
        [Tooltip("The type of tracking (position and/or rotation) to apply.")]
        private ArTrackingType trackingType = TrackedPoseDriver.TrackingType.RotationAndPosition;

        /// <summary>
        /// The type of tracking (position and/or rotation) to apply.
        /// </summary>
        public ArTrackingType TrackingType => trackingType;

        [SerializeField]
        [Tooltip("Specifies when (during Update and/or just before rendering) to update the tracking of the pose.")]
        private ArUpdateType updateType = TrackedPoseDriver.UpdateType.UpdateAndBeforeRender;

        /// <summary>
        /// Specifies when (during Update and/or just before rendering) to update the tracking of the pose.
        /// </summary>
        public ArUpdateType UpdateType => updateType;
    }
}
```

`CreateAssetMenu`特性可应用到配置文件类，使客户能够使用 "**创建**  >  **资产**  >  **Mixed Reality Toolkit**  >  **配置文件**" 菜单创建配置文件实例。

### <a name="implement-the-inspector"></a>实现检查器

配置文件检查器是用于配置和查看配置文件内容的用户界面。 每个配置文件检查器应扩展此 [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 类。

`CustomEditor`属性向 Unity 通知该检查器应用到的资产类型。

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a>创建 () 的程序集定义

混合现实 Toolkit 使用程序集定义 ([asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 文件指定组件之间的依赖关系，并协助 Unity 减少编译时间。

建议为所有数据访问接口及其编辑器组件创建程序集定义文件。

使用前面示例中的 [文件夹结构](#namespace-and-folder-structure) ，ContosoCamera 数据提供程序有两个 asmdef 文件。

第一个程序集定义适用于数据访问接口。 在此示例中，它将被称为 ContosoCamera，并将位于该示例的 *ContosoCamera* 文件夹中。 此程序集定义必须指定对 MixedReality 的依赖关系。Toolkit 以及它所依赖的任何其他程序集。

ContosoCameraEditor 程序集定义将指定配置文件检查器和任何特定于编辑器的代码。 此文件必须位于编辑器代码的根文件夹中。 在此示例中，该文件将位于 *ContosoCamera\Editor* 文件夹中。 此程序集定义将包含对 ContosoCamera 程序集的引用以及：

- MixedReality。Toolkit
- MixedReality。Toolkit。编辑器. 检查器
- MixedReality。Toolkit。编辑器。实用工具

## <a name="register-the-data-provider"></a>注册数据提供程序

创建后，可以向照相机系统注册数据提供程序，以便在应用程序中使用。

![选择相机设置提供程序](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a>打包和分发

作为第三方组件分发的数据提供程序具有与开发人员首选项一起打包和分发的特定详细信息。 最常见的解决方案是生成 unitypackage，并通过 Unity 资产存储进行分发。

如果数据提供程序作为 Microsoft Mixed Reality Toolkit 包的一部分提交和接受，microsoft MRTK 团队会将其作为 MRTK 产品/服务的一部分进行打包和分发。

## <a name="see-also"></a>另请参阅

- [照相机系统概述](camera-system-overview.md)
- [`BaseCameraSettingsProvider` 类](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [`IMixedRealityCameraSettingsProvider` 交互](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [`IMixedRealityDataProvider` 交互](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
