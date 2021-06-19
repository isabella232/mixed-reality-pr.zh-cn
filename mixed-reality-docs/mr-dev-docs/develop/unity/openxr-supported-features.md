---
title: Unity 中支持 OpenXR 插件的功能
description: 了解 OpenXR 在 Unity 中支持混合现实开发的功能。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr， unity， hololens， hololens 2， 混合现实， MRTK， 混合现实工具包， 增强现实， 虚拟现实， 混合现实头戴显示设备， 学习， 教程， 入门
ms.openlocfilehash: e622cd617ccf67c0877b9064efe791743e4c34b6
ms.sourcegitcommit: c9d52f9529cabeaf912fffa6efc6599a9041a929
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112398050"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Unity 中支持混合现实 OpenXR 的功能

混合 **现实 OpenXR 插件** 包是 Unity 的 **OpenXR** 插件的扩展，支持一套适用于 HoloLens 2 Windows Mixed Reality 头戴显示设备的功能。 在继续之前，请确保为 [OpenXR 配置 Unity 项目](openxr-getting-started.md)。

## <a name="whats-supported"></a>支持的操作

目前支持以下功能：

* 支持适用于 HoloLens 2 的 UWP 应用程序，并针对HoloLens 2进行优化。
* 支持使用最新控制器配置文件和全息应用远程Windows Mixed Reality头戴显示设备使用 Win32 VR 应用程序。
* 使用定位点和未绑定空间进行世界规模跟踪。
* [定位点存储 API，用于将定位点](spatial-anchors-in-unity.md) HoloLens 2本地存储。
* [运动控制器和手部交互](#motion-controller-and-hand-interactions)，包括新的 HP Reverb G2 控制器。
* 使用 26 个接点和联合半径输入的表达手部跟踪。
* 眼睛凝视与HoloLens 2。
* 在) 上定位照片/视频 (PV HoloLens 2。
* 混合现实捕获 PV 相机使用第三个眼睛渲染。
* 支持 ["播放"HoloLens 2 Holographic Remoting](unity-play-mode.md#holographic-remoting-in-unity-editor-play-mode)应用，使开发人员无需生成和部署到设备即可调试脚本。
* 通过 MRTK OpenXR 提供程序支持 与 MRTK Unity 2.5.3 [及更高版本兼容](openxr-getting-started.md#using-mrtk-with-openxr-support)。
* 与 Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 或更高版本兼容。
*  (0.1.3) 支持从构建和部署的 Windows[](holographic-remoting-desktop.md)独立应用进行桌面应用全息远程处理。
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
| 握 | 握 | 敲击或敲击 |
| primaryButton | [X/A] - 按 | 隔空敲击 |
| secondaryButton | [Y/B] - 按 | |
| gripButton | 手柄 - 按 | |
| triggerButton | 触发器 - 按 | |
| menuButton | 菜单 | |

### <a name="aim-and-grip-poses"></a>目标与手柄姿势

可以通过 OpenXR 输入交互访问两组姿势：

* 手柄为在手中呈现对象而造成
* 目的是指向世界。

有关此设计以及两种姿势之间的差异，请参阅 [OpenXR 规范 - 输入子路径](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)。

InputFeatureUsages  DevicePosition、DeviceRotation、DeviceVelocity和 **DeviceAngularVelocity** 提供的姿势均表示 OpenXR 手柄姿势。   与手柄姿势相关的 InputFeatureUsages 在 Unity [的 CommonUsages 中定义](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)。

InputFeatureUsages  PointerPosition、PointerRotation、PointerVelocity和 **PointerAngularVelocity** 提供的姿势均表示 OpenXR 目标姿势。   这些 InputFeatureUsages 未在任何包含的 C# 文件中定义，因此需要定义自己的 InputFeatureUsages，如下所示：

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptics

有关在 Unity 的 XR 输入系统中使用 haptics 的信息，请参阅 Unity Manual [for Unity XR Input - Haptics （Unity XR 输入 - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)的 Unity 手册）。

## <a name="qr-codes"></a>QR 码

HoloLens 2 可以检测头戴显示设备周围环境中的 QR 码，从而在每个代码的真实位置建立坐标系统。 可以在 QR 代码跟踪 [文档中找到更多详细信息](../platform-capabilities-and-apis/qr-code-tracking.md) 。  使用 OpenXR 插件时，从[ `SpatialGraphNodeId` QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference)获取 ，并使用 `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API 查找 QR 代码。

有关参考，我们在 GitHub 上提供了一个[QR](https://github.com/yl-msft/QRTracking)跟踪示例项目，并详细介绍[ `SpatialGraphNode` 了 API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)的用法说明。

## <a name="troubleshooting"></a>故障排除

当在 HoloLens 2 上挂起和恢复 Unity 应用时，该应用无法正确恢复，这会导致 HoloLens 视图中出现 4 个旋转点。

* 将 **OpenXR** **项目设置中的** "深度提交模式"设置为"无"作为解决方法
