---
title: Unity 中的相机设置
description: 了解如何设置和使用 Unity 的主相机进行Windows Mixed Reality进行全息渲染。
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit， mixedrealitytoolkit， mixedrealitytoolkit-unity， 全息渲染， 全息， 沉浸式， 焦点， 深度缓冲区， 仅方向， 位置， 不透明， 透明， 剪辑， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
ms.openlocfilehash: 1ac8c16e7bdd6b85b05c837e1a27fbd1e4cf4489ccb03d10ea5e952b2656cbe8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212227"
---
# <a name="camera-setup-in-unity"></a>Unity 中的相机设置

当你使用混合现实头戴显示设备时，它将成为全息世界的中心。 Unity [相机](https://docs.unity3d.com/Manual/class-Camera.html) 组件将自动处理立体声渲染，并跟踪头部移动和旋转。 但是，若要完全优化视觉质量和 [全息影像稳定性](../platform-capabilities-and-apis/hologram-stability.md)，应设置下面所述的相机设置。

## <a name="hololens-vs-vr-immersive-headsets"></a>HoloLens与 VR 沉浸式头戴显示设备

Unity 相机组件上的默认设置适用于传统的 3D 应用程序，这些应用程序需要像 skybox 一样的背景，因为它们没有真实的环境。

* 在沉 **[浸式](../../discover/immersive-headset-hardware-details.md)** 头戴显示设备上运行时，你要呈现用户看到的所有内容，因此你可能想要保留 skybox。
* 但是，在全息头戴显示设备（如[](/hololens/hololens2-hardware)HoloLens）上运行时，现实世界应出现在相机呈现的所有内容后面。 将相机背景设置为透明 (HoloLens，黑色呈现为透明) 而不是 Skybox 纹理：
    1. 在"层次结构"面板中选择主相机
    2. 在"检查器"面板中，找到"相机"组件，将"清除标志"下拉列表从"Skybox"更改为"纯色"
    3. 选择"背景颜色选取器"，将 RGBA 值更改为 (0、0、0、0) 
        1. 如果通过代码设置此设置，可以使用 Unity 的 [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a>照相机设置

无论开发哪种体验，主相机始终是附加到设备头安装显示器的主立体声渲染组件。 如果将 (用户的起始位置想象成 x： 0， Y： 0， Z： 0) ，则设置应用布局会更容易。 由于主相机正在跟踪用户头部的移动，因此可以通过设置主相机的起始位置来设置用户的起始位置。

需要做出的中心选择是开发适用于 HoloLens或 VR 沉浸式头戴显示设备。 完成后，请跳到适用的任何设置部分。

### <a name="hololens-camera-setup"></a>HoloLens相机设置

对于HoloLens，需要为要锁定到场景环境的任何对象使用定位点。 我们建议使用无限空间来最大化稳定性，并在多个房间创建定位点。

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a>VR 相机设置

Windows Mixed Reality支持各种体验缩放的应用，从只面向方向[](../../design/coordinate-systems.md#mixed-reality-experience-scales)的应用和规模化应用，到房间规模应用。 在HoloLens，你可以进一步构建全球规模的应用，让用户能够步进 5 米以上，探索建筑物的整个楼层等。

在 Unity 中构建混合现实体验的第一步是确定 [应用的目标体验](../../design/coordinate-systems.md) 缩放：

* [方向或方向缩放](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [长期或房间缩放](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [全球规模](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a>房间缩放或长期体验

> [!NOTE]
> 如果要针对 HL2 进行构建，建议创建眼睛级体验，或考虑使用场景理解来[](../platform-capabilities-and-apis/scene-understanding-sdk.md)了解场景的楼层。

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a>固定体验

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a>设置相机背景

如果使用 MRTK，则会自动配置和管理相机的背景。 对于 XR SDK 或旧版 WSA 项目，我们建议在相机上将相机的背景设置为纯黑色HoloLens为 VR 保留 skybox。

## <a name="using-multiple-cameras"></a>使用多个相机

当场景中有多个相机组件时，Unity 根据哪个 GameObject 具有 MainCamera 标记，知道要使用哪个相机进行立体声渲染。 在旧版 XR 中，它还使用此标记来同步头跟踪。 在 XR SDK 中，头部跟踪由附加到相机的 TrackedPoseDriver 脚本驱动。

## <a name="sharing-depth-buffers"></a>共享深度缓冲区

根据渲染的头戴显示设备类型，共享应用的深度缓冲区Windows每个帧都会为应用提供全息影像稳定性的两个提升之一：

* **提供深度缓冲区时，VR** 沉浸式头戴显示设备可以处理位置重新保护，并调整全息影像，以判断位置和方向是否出现误用。
* **HoloLens头戴显示** 设备有一些不同的方法。 HoloLens 1 将在提供深度缓冲区时[](focus-point-in-unity.md)自动选择焦点，从而优化与最多内容相交的平面的全息影像稳定性。 HoloLens 2使用深度[LSR 稳定内容 (请参阅) 。 ](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a>使用剪切平面

在混合现实中，过于靠近用户的渲染内容可能会让人感到混乱。 可以在"相机 ["组件上](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) 调整近近剪裁平面。

1. 在" **层次结构"面板** 中选择 **主** 相机
2. 在"**检查器**"面板中，找到"**相机组件****剪辑** 平面"，将"附近"文本框从 **0.3** 更改为 **0.85。** 更近渲染的内容可能会导致用户感到难受，应该根据呈现距离准则[避免。](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)

## <a name="recentering-the-camera"></a>最近使用相机

如果要构建一种 [步进缩放](../../design/coordinate-systems.md)体验，可以通过调用 XR，在用户的当前头部位置使用最新的 Unity 世界 **[原点。旧版 XR 中的 InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法或 XR SDK 中的 **[XRInputSubsystem.TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** 方法。

## <a name="teleportation"></a>隐形传送

此功能通常保留用于 VR 体验：

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a>重新保护模式

HoloLens和沉浸式头戴显示设备都会重新重现应用呈现的每个帧，以针对发出光子时用户的实际头部位置的任何错误判断进行调整。

默认情况下：

* **如果应用为** 给定帧提供深度缓冲区，VR 沉浸式头戴显示设备将负责位置重新保护。 沉浸式头戴显示设备还会调整全息影像，以判断位置和方向的误用。 如果未提供深度缓冲区，则系统只会更正方向错误。
* **全息头** 戴显示设备HoloLens 2将负责位置重新投影，无论应用是否提供其深度缓冲区。 在没有深度缓冲区的情况下，位置重新HoloLens因为渲染通常是稀疏的，并且实际提供稳定的背景。

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们布局的 Unity 开发旅程，则你正在探索 MRTK 核心构建基块。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [凝视](gaze-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅

* [全息影像稳定性](../platform-capabilities-and-apis/hologram-stability.md)
* [体验缩放](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [空间阶段](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Unity 中的失跟](tracking-loss-in-unity.md)
* [空间定位点](../../design/spatial-anchors.md)
* [Unity 中的持久性](persistence-in-unity.md)
* [Unity 中的共享体验](shared-experiences-in-unity.md)
* [Azure 空间定位点](/azure/spatial-anchors)
* [适用于 Unity 的 Azure 空间定位点 SDK](/dotnet/api/Microsoft.Azure.SpatialAnchors)