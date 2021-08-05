---
title: MRTK 和 XR SDK 入门
description: 使用 XR SDK 的 MRTK 登陆页
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity， HoloLens， HoloLens 2， 混合现实， 开发， MRTK， XRSDK， XR SDK
ms.openlocfilehash: 1560188d1a69f0083940a37da8c378691ee75a9d569c2c5088e0e3f614a44858
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188226"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>MRTK 和 XR SDK 入门

XR SDK 是 [Unity 2019.3](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)及更新的 Unity XR 管道。 在 Unity 2019 中，它提供了现有 XR 管道的替代项。 在 Unity 2020 中，它是 Unity 中唯一的 XR 管道。

## <a name="prerequisites"></a>先决条件

若要开始使用混合现实Toolkit，请按照[提供的步骤](../install-the-tools.md#importing-the-mixed-reality-toolkit)将 MRTK 添加到项目。

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>为 XR SDK 管道配置 Unity

XR SDK 管道目前支持 3 个平台：Windows Mixed Reality、Oculus 和 OpenXR。 以下部分将介绍为每个平台配置 XR SDK 所需的步骤。

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

转到 **Unity 的 程序包管理器** 并安装 Windows XR 插件包，该包添加了对 XR SDK Windows Mixed Reality的支持。 这也会下拉一些依赖项包。

1. 确保已成功安装以下各项：
   * XR 插件管理
   * WindowsXR 插件
   * XR 旧版输入帮助程序

2. 转到“编辑”>“项目设置”。
3. 单击"连接"窗口中的"XR 插件管理"Project 设置选项卡。
4. 转到"通用Windows平台"设置，并确保Windows Mixed Reality插件提供程序下选中了"配置"。
5. 确保选中"启动时初始化 XR"。
6.  (**_编辑器中_** 远程处理HoloLens必需，否则为可选) 转到"独立"设置，并确保Windows Mixed Reality插件提供程序下选中了"设置"。 另请确保选中"启动时初始化 XR"。

    ![选中"独立"选项卡的 XR 插件管理](images/xr-management-img-02.png)

7.  (**_可选_**) 单击"XR 插件管理"下的"Windows Mixed Reality"选项卡，并创建自定义设置配置文件以更改默认值。 如果设置列表已存在，则无需创建配置文件。

    ![XR 插件管理，Windows选项卡](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. 按照 [如何使用 XR SDK 管道在 MRTK](../supported-devices/oculus-quest-mrtk.md) 中配置 Oculus Quest 指南操作到最后。 本指南概述了将 Unity 和 MRTK 配置为使用 Oculus Quest 的 XR SDK 管道所需的步骤。

### <a name="openxr"></a>OpenXR

> [!IMPORTANT]
> Unity 中的 OpenXR 仅在 Unity 2020.2 及更高版本上受支持。
> 它还仅支持 x64、ARM 和 ARM64 生成。

1. 按照 [使用适用于 Unity 的混合现实 OpenXR 插件](/windows/mixed-reality/develop/unity/openxr-getting-started) 指南操作，包括配置 XR 插件管理和优化的步骤，将 OpenXR 插件安装到项目中。 确保已成功安装以下内容：
   1. XR 插件管理
   1. OpenXR 插件
   1. 混合现实 OpenXR 插件
1. 转到"编辑> Project 设置。
1. 单击"连接"窗口中的"XR 插件管理"Project 设置选项卡。
1. 确保选中"启动时初始化 XR"。
1.  (**_可选_**) 如果面向 HoloLens 2，请确保你位于 UWP 平台上，并选择"Microsoft HoloLens功能集"

![插件管理 OpenXR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> 如果有一个预先存在的项目正在使用 UPM 中的 MRTK，请确保以下行位于位于 MixedRealityToolkit.Generated 文件夹中的 **link.xml** 文件中。

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> 对于 MRTK 和 OpenXR 的初始版本，本机仅支持HoloLens 2手和Windows Mixed Reality运动控制器。 即将发布的版本中将添加对附加硬件的支持。

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>为 XR SDK 管道配置 MRTK

::: moniker range=">= mrtkunity-2021-05"
使用所有跨 Unity XR 管道配置的默认 MRTK 配置文件。 以前的"DefaultOpenXRConfigurationProfile"和"DefaultXRSDKConfigurationProfile"现已标记为已过时。
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
如果使用 OpenXR，请选择"DefaultOpenXRConfigurationProfile"作为活动配置文件，或克隆它进行自定义。

如果在 XR 插件管理配置（例如 Windows Mixed Reality 或 Oculus）中使用其他 XR 运行时，请选择"DefaultXRSDKConfigurationProfile"作为活动配置文件，或克隆它以进行自定义。

这些配置文件根据需要使用正确的系统和提供程序进行设置。 有关 [XR](../features/profiles/profiles.md#xr-sdk) SDK 的配置文件和示例支持，请参阅配置文件文档。
::: moniker-end

若要将现有配置文件迁移到 XR SDK，应更新以下服务和数据访问提供程序。
::: moniker range=">= mrtkunity-2021-05"
你将能够在 Unity 2019 的"XR SDK"选项卡下或 Unity 2020+的主/仅视图中看到新的数据访问提供程序，旧版 XR 不存在。

!["XR SDK"选项卡](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a>照相机

::: moniker range=">= mrtkunity-2021-05"
添加以下数据提供程序
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
从 [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![旧版相机设置](../features/images/xrsdk/CameraSystemLegacy.png)

to
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| OpenXR 插件 | WindowsXR 插件 |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| OpenXR 插件 | WindowsXR 插件 |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![XR SDK 相机设置](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>输入

::: moniker range=">= mrtkunity-2021-05"
添加以下数据提供程序
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
从 [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![旧输入设置](../features/images/xrsdk/InputSystemWMRLegacy.png)

to
::: moniker-end

| OpenXR 插件 | WindowsXR 插件 |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR：__

![OpenXR 输入设置](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality：__

![XR SDK 输入设置](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>边界

::: moniker range=">= mrtkunity-2021-05"
添加以下数据提供程序
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
从 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![旧边界设置](../features/images/xrsdk/BoundarySystemLegacy.png)

to
::: moniker-end

| OpenXR 插件 | WindowsXR 插件 |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK 边界设置](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>空间感知

::: moniker range=">= mrtkunity-2021-05"
添加以下数据提供程序
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
从 [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![旧版空间感知设置](../features/images/xrsdk/SpatialAwarenessLegacy.png)

to
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| OpenXR 插件 | WindowsXR 插件 |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (UWP)  | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (UWP)  |
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (非 UWP)  | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| OpenXR 插件 | WindowsXR 插件 |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![XR SDK 空间感知设置](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>控制器映射

如果使用自定义控制器映射配置文件，请打开其中一个，并运行混合现实 Toolkit -> 实用工具 -> 更新 -> 控制器映射配置文件菜单项，以确保定义新的 XR SDK 控制器类型。

## <a name="see-also"></a>另请参阅

* [Unity 中的 AR 开发入门](https://docs.unity3d.com/Manual/AROverview.html)
* [Unity 中的 VR 开发入门](https://docs.unity3d.com/Manual/VROverview.html)
