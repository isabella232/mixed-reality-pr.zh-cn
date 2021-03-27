---
title: Unity 中的照相机设置
description: 了解如何设置和使用 Unity 的用于 Windows Mixed Reality 开发的主照相机进行全息渲染。
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，全息呈现，全息，沉浸式，聚焦点，深度缓冲，仅限方向，定位，不透明，透明，剪辑，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: d3f69c6cf1889587b23b68259f22b34b89b925a4
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636253"
---
# <a name="camera-setup-in-unity"></a>Unity 中的照相机设置

当你磨损混合现实耳机时，它将成为你的全息世界的中心。 Unity [相机](https://docs.unity3d.com/Manual/class-Camera.html) 组件会自动处理 stereoscopic 渲染，并遵循打印头运动和旋转。 但是，若要完全优化视觉质量和 [全息图稳定性](../platform-capabilities-and-apis/hologram-stability.md)，应设置以下描述的相机设置。

## <a name="hololens-vs-vr-immersive-headsets"></a>HoloLens 与 VR 沉浸式耳机

Unity 相机组件上的默认设置适用于传统的3D 应用程序，这种应用程序需要 skybox 的背景，因为它们不是真实的。

* 在 **[沉浸式头戴式耳机](../../discover/immersive-headset-hardware-details.md)** 上运行时，会呈现用户看到的所有内容，因此你可能需要保留 skybox。
* 但是，当在 **全息耳机** （如 [HoloLens](/hololens/hololens2-hardware)）上运行时，真实环境应显示在照相机呈现的所有内容之后。 将相机背景设置为在 HoloLens (透明，黑色呈现为透明) 而不是 Skybox 纹理：
    1. 选择 "层次结构" 面板中的主相机
    2. 在 "检查器" 面板中，找到照相机组件，并将 "清除标志" 下拉列表从 "Skybox" 更改为纯色
    3. 选择背景色选取器并将 RGBA 值更改为 (0，0，0，0) 
        1. 如果从代码设置此设置，则可以使用 Unity [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a>照相机设置

无论你开发的是哪种体验，主摄像机始终都是连接到设备的打印头显示的主要立体声呈现组件。 如果将用户的起始位置想像为 (X：0，Y：0，Z： 0) ，则可以更容易地设计应用程序。 由于摄像机正在跟踪用户的头移动，因此可以通过设置主摄像机的开始位置来设置用户的起始位置。

你需要进行的集中选择是要为 HoloLens 或 VR 沉浸式耳机进行开发。 完成此过程后，请跳到所应用的任何设置部分。

### <a name="hololens-camera-setup"></a>HoloLens 照相机设置

对于 HoloLens 应用，需要对要锁定到场景环境的任何对象使用定位点。 建议使用无限空间来最大程度地提高稳定性，并在多个房间中创建锚。

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a>VR 照相机设置

Windows Mixed Reality 在各种 [经验](../../design/coordinate-systems.md#mixed-reality-experience-scales)范围内支持应用，从仅限方向和大规模应用，再到房间规模的应用。 在 HoloLens 上，你可以进一步构建全球规模的应用程序，让用户经历5米以上的工作，探索一座建筑的整个楼层。

在 Unity 中构建混合现实体验的第一步是确定应用的目标 [规模](../../design/coordinate-systems.md) ：

* [方向或固定比例](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [办公室或房间规模](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [全球规模](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a>会议室规模或共同体验

> [!NOTE]
> 如果要为 HL2 构建，我们建议创建一个目视的体验，或考虑使用 [场景理解来了解](../platform-capabilities-and-apis/scene-understanding-sdk.md) 场景的基底。

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a>未安装体验

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a>设置相机背景

如果使用的是 MRTK，则会自动配置和管理照相机的背景。 对于 XR SDK 或旧的 WSA 项目，建议在 HoloLens 上将相机的背景设置为纯色黑色，并将 skybox 设置为 "VR"。

## <a name="using-multiple-cameras"></a>使用多个照相机

当场景中有多个照相机组件时，Unity 知道哪个照相机要用于 stereoscopic 呈现，具体取决于哪些 GameObject 具有 MainCamera 标记。 在旧式 XR 中，它还使用此标记来同步头跟踪。 在 XR SDK 中，head 跟踪由附加到相机的 TrackedPoseDriver 脚本驱动。

## <a name="sharing-depth-buffers"></a>共享深度缓冲区

将应用的深度缓冲区共享到 Windows 每个框架都将根据要呈现的耳机类型为应用程序提供以下两个增强功能之一：

* 在提供深度缓冲区时， **VR 沉浸式耳机** 可以处理位置 reprojection，同时在位置和方向调整你的全息影像。
* **HoloLens 耳机** 具有几种不同的方法。 当提供了深度缓冲区时，HoloLens 1 将自动选择 [焦点](focus-point-in-unity.md) ，同时优化与最大内容相交的平面上的全息图稳定性。 HoloLens 2 将使用深度 LSR 来稳定内容 [ (请参阅备注) ](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)。

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a>使用剪辑平面

在混合现实中，向用户呈现的内容太接近。 可以在相机组件上调整 [近和远的剪辑平面](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) 。

1. 选择 "**层次结构**" 面板中的 **主相机**
2. 在 " **检查器** " 面板中，找到 " **照相机** " 组件 **修剪平面** ，并将 " **Near** " 文本框从 **0.3** 更改为 **0.85**。 呈现更近的内容可能导致用户 discomfort，应根据 [渲染距离准则](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)加以避免。

## <a name="recentering-the-camera"></a>Recentering 照相机

如果要构建大规模的 [体验](../../design/coordinate-systems.md)，可以通过调用 XR，在用户的当前头部位置 recenter Unity 的世界原点 **[。InputTracking Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法在旧 XR 或 TRYRECENTER SDK 中的 **[XRInputSubsystem。](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)**

## <a name="teleportation"></a>隐形传送

此功能通常保留用于 VR 体验：

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a>Reprojection 模式

HoloLens 和沉浸式耳机都将 reproject 你的应用程序呈现的每个帧，以便在发出 photons 时，对用户实际头位置的任何 misprediction 进行调整。

默认情况下：

* 如果应用为给定帧提供深度缓冲区，则 **VR 沉浸式耳机** 将负责定位 reprojection。 沉浸式耳机还会在位置和方向上调整 misprediction 的全息影像。 如果未提供深度缓冲区，则系统只会方向上的 mispredictions。
* 使用 HoloLens 2 的 **全息耳机**，无论应用是否提供其深度缓冲区，都将负责位置 reprojection。 在不使用 HoloLens 上的深度缓冲区的情况下，可能会出现位置 reprojection，因为呈现通常是由真实世界提供的稳定背景稀疏的。

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所说的 Unity 开发旅程，就是在浏览 MRTK 核心构建基块。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [凝视](gaze-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅

* [全息影像稳定性](../platform-capabilities-and-apis/hologram-stability.md)
* [体验规模](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [空间阶段](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Unity 中的失跟](tracking-loss-in-unity.md)
* [空间定位点](../../design/spatial-anchors.md)
* [Unity 中的持久性](persistence-in-unity.md)
* [Unity 中的共享体验](shared-experiences-in-unity.md)
* [Azure 空间定位点](/azure/spatial-anchors)
* [用于 Unity 的 Azure 空间定位点 SDK](/dotnet/api/Microsoft.Azure.SpatialAnchors)