---
title: 与 MRTK 和 XRSDK 入门
description: XRSDK 的 MRTK 的登陆页
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，XRSDK，
ms.openlocfilehash: ef6d8c9205a9d801e8cb0ec2690d77b74c72b5fb
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143523"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>MRTK 和 XR SDK 入门

XR SDK 是 unity [2019.3 和更高版本中的 unity 新 XR 管道](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)。 在 Unity 2019 中，它可替代现有的 XR 管道。 在 Unity 2020 中，它将成为 Unity 中唯一的 XR 管道。

## <a name="prerequisites"></a>先决条件

若要开始使用混合现实工具包，请按照 [提供的步骤](../install-the-tools.md#importing-the-mixed-reality-toolkit) 将 MRTK 添加到项目。

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>为 XR SDK 管道配置 Unity

XR SDK 管道当前支持3个平台： Windows Mixed Reality、Oculus 和 OpenXR。 以下各节将介绍为每个平台配置 XR SDK 所需的步骤。

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

进入 **Unity 的包管理器** 并安装 Windows XR 插件包，其中添加了对 XR SDK 上 Windows Mixed Reality 的支持。 这也会提取一些依赖项包。 

1. 确保已成功安装以下所有内容：
   * XR 插件管理
   * Windows XR 插件
   * XR 旧版输入帮助程序

2. 转到“编辑”>“项目设置”。
3. 单击 "项目设置" 窗口中的 XR 插件管理选项卡。
4. 请访问 "通用 Windows 平台设置"，并确保在 "插件提供程序" 下选中 "Windows Mixed Reality"。
5. 请确保已选中 "在启动时初始化 XR"。
6.  (**_编辑器中的 HoloLens 远程_** 处理是必需的，否则为可选) 转到"独立"设置，并确保Windows Mixed Reality插件提供程序下选中了"设置"。 另请确保选中"启动时初始化 XR"。

![选中"独立"选项卡的 XR 插件管理](images/xr-management-img-02.png)

7.  (**_可选_**) 单击"XR 插件管理"下的"Windows Mixed Reality"选项卡，并创建自定义设置配置文件以更改默认值。 如果设置列表已存在，则无需创建配置文件。

![选中 Windows 选项卡的 XR 插件管理](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. 按照 [如何使用 XR SDK 管道在 MRTK](../supported-devices/oculus-quest-mrtk.md) 中配置 Oculus Quest 指南操作到最后。 本指南概述了将 Unity 和 MRTK 配置为使用 Oculus Quest 的 XR SDK 管道所需的步骤。

### <a name="openxr-preview"></a>OpenXR (预览) 

> [!IMPORTANT]
> Unity 中的 OpenXR 仅在 Unity 2020.2 及更高版本上受支持。
>
> 目前，它还仅支持 x64 和 ARM64 生成。

1. 按照 [使用适用于 Unity 的混合现实 OpenXR 插件](/windows/mixed-reality/develop/unity/openxr-getting-started) 指南操作，包括配置 XR 插件管理和优化的步骤，将 OpenXR 插件安装到项目中。 确保已成功安装以下内容：
   1. XR 插件管理
   1. OpenXR 插件
   1. 混合现实 OpenXR 插件
1. 转到"编辑>项目设置"。
1. 单击"项目设置"窗口中的"XR 插件管理"选项卡。
1. 确保选中"启动时初始化 XR"。
1.  (**_可选_**) 如果面向 HoloLens 2，请确保位于 UWP 平台上，并选择 "Microsoft HoloLens 功能集"

![插件管理打开 XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> 如果预先存在的项目正在使用 MRTK 与 UPM，请确保以下行位于 MixedRealityToolkit 文件夹中的 **link.xml** 文件中。

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> 对于 MRTK 和 OpenXR 的初始版本，仅支持 HoloLens 2 表述的手势和 Windows Mixed Reality 运动控制器。 未来版本中将添加对其他硬件的支持。

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>为 XR SDK 管道配置 MRTK

如果使用的是 OpenXR，请选择 "DefaultOpenXRConfigurationProfile" 作为活动配置文件，或将其克隆以便进行自定义。

如果在 XR 插件管理配置（如 Windows Mixed Reality 或 Oculus）中使用其他 XR 运行时，请选择 "DefaultXRSDKConfigurationProfile" 作为活动配置文件，或将其克隆以便进行自定义。

这些配置文件在需要时设置为正确的系统和提供程序。 请参阅 [配置文件文档](../features/profiles/profiles.md#xr-sdk) ，以了解有关 XR SDK 的配置文件和示例支持的详细信息。

若要将现有配置文件迁移到 XR SDK，应更新以下服务和数据提供程序：

### <a name="camera"></a>照相机

从 [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![旧照相机设置](../features/images/xrsdk/CameraSystemLegacy.png)

to

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**和**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![XR SDK 照相机设置](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>输入

从 [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![旧输入设置](../features/images/xrsdk/InputSystemWMRLegacy.png)

to

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR__：

![OpenXR 输入设置](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__：

![XR SDK 输入设置](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>边界

从 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![旧边界设置](../features/images/xrsdk/BoundarySystemLegacy.png)

to

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK 边界设置](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>空间感知

从 [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![旧版空间感知设置](../features/images/xrsdk/SpatialAwarenessLegacy.png)

to

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| 正在学习 | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![XR SDK 空间感知设置](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>控制器映射

如果使用自定义控制器映射配置文件，请打开其中一个配置文件并运行混合现实工具包 -> 实用工具 -> Update -> 控制器映射配置文件菜单项，以确保定义新的 XR SDK 控制器类型。

## <a name="see-also"></a>另请参阅

* [Unity 中的 AR 开发入门](https://docs.unity3d.com/Manual/AROverview.html)
* [Unity 中的 VR 开发入门](https://docs.unity3d.com/Manual/VROverview.html)