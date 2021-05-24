---
title: OpenXR 插件支持 Unity 中的功能
description: 发现 OpenXR 支持 Unity 中混合现实开发的功能。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，扩充现实，虚拟现实，混合现实耳机，学习，教程，入门
ms.openlocfilehash: e622cd617ccf67c0877b9064efe791743e4c34b6
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333369"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>混合现实 OpenXR 支持 Unity 中的功能

**Mixed Reality OpenXR 插件** 包是 Unity 的 **OpenXR 插件** 的扩展，支持用于 HoloLens 2 和 Windows Mixed Reality 耳机的一套功能。 在继续之前，请确保已 [为 OpenXR 配置](openxr-getting-started.md)了 Unity 项目。

## <a name="whats-supported"></a>支持的操作

目前支持以下功能：

* 支持 HoloLens 2 的 UWP 应用程序，并针对 HoloLens 2 应用程序模型进行优化。
* 支持适用于 Windows Mixed Reality 耳机的 Win32 VR 应用程序，包含最新控制器配置文件和全息应用远程处理。
* 使用定位点和无限空间进行世界规模跟踪。
* [用于将定位点保存](spatial-anchors-in-unity.md) 到 HoloLens 2 本地存储的定位存储 API。
* [运动控制器和手动交互](#motion-controller-and-hand-interactions)，包括新的 HP 回音 G2 控制器。
* 使用26个接合和接点输入的有向右跟踪。
* HoloLens 2 上的目视注视交互。
* 在 HoloLens 2 上查找 (PV) 相机的照片/视频。
* 混合现实通过 PV 相机使用第三种目视渲染来捕获。
* 支持 [通过全息远程处理应用 "播放" 到 HoloLens 2](unity-play-mode.md#holographic-remoting-in-unity-editor-play-mode)，使开发人员无需生成并部署到设备即可调试脚本。
* 与 MRTK Unity 2.5.3 和更高版本通过 [MRTK OpenXR 提供程序支持](openxr-getting-started.md#using-mrtk-with-openxr-support)兼容。
* 与 Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 或更高版本兼容。
*  (在 0.1.3) 中添加的功能支持从生成和部署的 Windows 独立应用进行 [桌面应用全息远程处理](holographic-remoting-desktop.md) 。
*  (0.1.4) 支持通过 SpatialGraphNode 在 HoloLens2 上跟踪 [QR](#qr-codes) 码
*  (0.2.0 中添加) 支持 **全息** 远程处理中的定位点
*  (0.2.0) 支持手部和 **手部网格跟踪**
*  (0.2.0) 支持使用 ARRaycastManager 进行平面检测和放置全息影像的 **ARPlaneSubsystems。** 
*  (0.9.0) 支持 **XRMeshSubsystem** 和 **ARMeshManager** 进行空间映射。
*  (0.9.0 中) 支持适用于 Windows 的 Azure 空间定位点 SDK 插件。 有关详细信息，请参阅 [GitHub 上的混合现实 + OpenXR Azure 空间定位点示例项目](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample)。
*  (0.9.1) 支持从生成和部署的 Windows UWP 应用进行桌面应用全息远程处理。
*  (0.9.4 版中添加) 支持 ARM 平台以及 ARM64 for HoloLens 2 应用程序。

## <a name="motion-controller-and-hand-interactions"></a>运动控制器和手部交互

若要了解有关 Unity 中混合现实交互的基础知识，请访问 [Unity XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)输入的 Unity 手册。 此 Unity 文档介绍了从控制器特定的输入到更通用 **InputFeatureUsage** 的映射、如何标识和分类可用的 XR 输入、如何从这些输入读取数据，等等。

混合现实 OpenXR 插件提供映射到标准 **InputFeatureUsage** 的其他输入交互配置文件，如下所示：

| InputFeatureUsage | HP Reverb G2 控制器 (OpenXR)  | HoloLens Hand (OpenXR)  |
| ---- | ---- | ---- |
| primary2DAxis | 操纵 杆 | |
| primary2DAxisClick | 下一步 - 单击 | |
| 触发器 | 触发器  | |
| 调整 | 调整 | 空中分流或挤压 |
| primaryButton | [X/A]-按 | 隔空敲击 |
| secondaryButton | [Y/B]-按 | |
| gripButton | 手柄-按 | |
| triggerButton | 触发器-按 | |
| menuButton | 菜单 | |

### <a name="aim-and-grip-poses"></a>瞄准并抓住姿势

通过 OpenXR 输入交互可以访问两组姿势：

* 用于呈现对象的手柄姿势
* 目标是指进入世界。

有关此设计的详细信息以及这两个姿势之间的差异，请参阅 [OpenXR 规范输入子路径](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)。

InputFeatureUsages **DevicePosition**、 **DeviceRotation**、 **DeviceVelocity** 和 **DeviceAngularVelocity** 提供的姿势都代表了 OpenXR **手柄** 的姿势。 与手柄姿势相关的 InputFeatureUsages 在 Unity 的 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)中定义。

InputFeatureUsages **PointerPosition**、 **PointerRotation**、 **PointerVelocity** 和 **PointerAngularVelocity** 提供的姿势均代表 OpenXR **aim** 姿势。 这些 InputFeatureUsages 未在任何包含的 C# 文件中定义，因此需要定义自己的 InputFeatureUsages，如下所示：

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptics

有关在 Unity 的 XR 输入系统中使用 haptics 的信息，请参阅 Unity Manual [for Unity XR Input - Haptics （Unity XR 输入 - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)的 Unity 手册）。

## <a name="qr-codes"></a>QR 码

HoloLens 2 可以检测头戴显示设备周围环境中的 QR 码，从而在每个代码的真实位置建立坐标系统。 可以在 QR 代码跟踪 [文档中找到更多详细信息](../platform-capabilities-and-apis/qr-code-tracking.md) 。  使用 OpenXR 插件时，从[ `SpatialGraphNodeId` QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference)获取 ，并使用 `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API 查找 QR 代码。

有关参考，我们在 GitHub 上提供了一个[QR](https://github.com/yl-msft/QRTracking)跟踪示例项目，并详细介绍[ `SpatialGraphNode` 了 API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)的用法说明。

## <a name="troubleshooting"></a>疑难解答

当在 HoloLens 2 上挂起和恢复 Unity 应用时，该应用无法正确恢复，这会导致 HoloLens 视图中出现 4 个旋转点。

* 将 **OpenXR** **项目设置中的** "深度提交模式"设置为"无"作为解决方法
