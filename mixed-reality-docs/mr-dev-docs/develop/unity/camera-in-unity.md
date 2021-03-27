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
# <a name="camera-setup-in-unity"></a><span data-ttu-id="129ea-104">Unity 中的照相机设置</span><span class="sxs-lookup"><span data-stu-id="129ea-104">Camera setup in Unity</span></span>

<span data-ttu-id="129ea-105">当你磨损混合现实耳机时，它将成为你的全息世界的中心。</span><span class="sxs-lookup"><span data-stu-id="129ea-105">When you wear a mixed reality headset, it becomes the center of your holographic world.</span></span> <span data-ttu-id="129ea-106">Unity [相机](https://docs.unity3d.com/Manual/class-Camera.html) 组件会自动处理 stereoscopic 渲染，并遵循打印头运动和旋转。</span><span class="sxs-lookup"><span data-stu-id="129ea-106">The Unity [Camera](https://docs.unity3d.com/Manual/class-Camera.html) component will automatically handle stereoscopic rendering and follow your head movement and rotation.</span></span> <span data-ttu-id="129ea-107">但是，若要完全优化视觉质量和 [全息图稳定性](../platform-capabilities-and-apis/hologram-stability.md)，应设置以下描述的相机设置。</span><span class="sxs-lookup"><span data-stu-id="129ea-107">However, to fully optimize visual quality and [hologram stability](../platform-capabilities-and-apis/hologram-stability.md), you should set the camera settings described below.</span></span>

## <a name="hololens-vs-vr-immersive-headsets"></a><span data-ttu-id="129ea-108">HoloLens 与 VR 沉浸式耳机</span><span class="sxs-lookup"><span data-stu-id="129ea-108">HoloLens vs VR immersive headsets</span></span>

<span data-ttu-id="129ea-109">Unity 相机组件上的默认设置适用于传统的3D 应用程序，这种应用程序需要 skybox 的背景，因为它们不是真实的。</span><span class="sxs-lookup"><span data-stu-id="129ea-109">The default settings on the Unity Camera component are for traditional 3D applications, which need a skybox-like background as they don't have a real world.</span></span>

* <span data-ttu-id="129ea-110">在 **[沉浸式头戴式耳机](../../discover/immersive-headset-hardware-details.md)** 上运行时，会呈现用户看到的所有内容，因此你可能需要保留 skybox。</span><span class="sxs-lookup"><span data-stu-id="129ea-110">When running on an **[immersive headset](../../discover/immersive-headset-hardware-details.md)**, you're rendering everything the user sees, and so you'll likely want to keep the skybox.</span></span>
* <span data-ttu-id="129ea-111">但是，当在 **全息耳机** （如 [HoloLens](/hololens/hololens2-hardware)）上运行时，真实环境应显示在照相机呈现的所有内容之后。</span><span class="sxs-lookup"><span data-stu-id="129ea-111">However, when running on a **holographic headset** like [HoloLens](/hololens/hololens2-hardware), the real world should appear behind everything the camera renders.</span></span> <span data-ttu-id="129ea-112">将相机背景设置为在 HoloLens (透明，黑色呈现为透明) 而不是 Skybox 纹理：</span><span class="sxs-lookup"><span data-stu-id="129ea-112">Set the camera background to be transparent (in HoloLens, black renders as transparent) instead of a Skybox texture:</span></span>
    1. <span data-ttu-id="129ea-113">选择 "层次结构" 面板中的主相机</span><span class="sxs-lookup"><span data-stu-id="129ea-113">Select the Main Camera in the Hierarchy panel</span></span>
    2. <span data-ttu-id="129ea-114">在 "检查器" 面板中，找到照相机组件，并将 "清除标志" 下拉列表从 "Skybox" 更改为纯色</span><span class="sxs-lookup"><span data-stu-id="129ea-114">In the Inspector panel, find the Camera component and change the Clear Flags dropdown from Skybox to Solid Color</span></span>
    3. <span data-ttu-id="129ea-115">选择背景色选取器并将 RGBA 值更改为 (0，0，0，0) </span><span class="sxs-lookup"><span data-stu-id="129ea-115">Select the Background color picker and change the RGBA values to (0, 0, 0, 0)</span></span>
        1. <span data-ttu-id="129ea-116">如果从代码设置此设置，则可以使用 Unity [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)</span><span class="sxs-lookup"><span data-stu-id="129ea-116">If setting this from code, you can use Unity's [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)</span></span>

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a><span data-ttu-id="129ea-117">照相机设置</span><span class="sxs-lookup"><span data-stu-id="129ea-117">Camera setup</span></span>

<span data-ttu-id="129ea-118">无论你开发的是哪种体验，主摄像机始终都是连接到设备的打印头显示的主要立体声呈现组件。</span><span class="sxs-lookup"><span data-stu-id="129ea-118">Whatever kind of experience you're developing, the Main Camera is always the primary stereo rendering component attached to your device's head-mounted display.</span></span> <span data-ttu-id="129ea-119">如果将用户的起始位置想像为 (X：0，Y：0，Z： 0) ，则可以更容易地设计应用程序。</span><span class="sxs-lookup"><span data-stu-id="129ea-119">It'll be easier to lay out your app if you imagine the starting position of the user as (X: 0, Y: 0, Z: 0).</span></span> <span data-ttu-id="129ea-120">由于摄像机正在跟踪用户的头移动，因此可以通过设置主摄像机的开始位置来设置用户的起始位置。</span><span class="sxs-lookup"><span data-stu-id="129ea-120">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

<span data-ttu-id="129ea-121">你需要进行的集中选择是要为 HoloLens 或 VR 沉浸式耳机进行开发。</span><span class="sxs-lookup"><span data-stu-id="129ea-121">The central choice you need to make is whether you're developing for HoloLens or VR immersive headsets.</span></span> <span data-ttu-id="129ea-122">完成此过程后，请跳到所应用的任何设置部分。</span><span class="sxs-lookup"><span data-stu-id="129ea-122">Once you've got that, skip to whichever setup section applies.</span></span>

### <a name="hololens-camera-setup"></a><span data-ttu-id="129ea-123">HoloLens 照相机设置</span><span class="sxs-lookup"><span data-stu-id="129ea-123">HoloLens camera setup</span></span>

<span data-ttu-id="129ea-124">对于 HoloLens 应用，需要对要锁定到场景环境的任何对象使用定位点。</span><span class="sxs-lookup"><span data-stu-id="129ea-124">For HoloLens apps, you need to use anchors for any objects you want to lock to the scene environment.</span></span> <span data-ttu-id="129ea-125">建议使用无限空间来最大程度地提高稳定性，并在多个房间中创建锚。</span><span class="sxs-lookup"><span data-stu-id="129ea-125">We recommend using unbounded space to maximize stability and create anchors in multiple rooms.</span></span>

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a><span data-ttu-id="129ea-126">VR 照相机设置</span><span class="sxs-lookup"><span data-stu-id="129ea-126">VR camera setup</span></span>

<span data-ttu-id="129ea-127">Windows Mixed Reality 在各种 [经验](../../design/coordinate-systems.md#mixed-reality-experience-scales)范围内支持应用，从仅限方向和大规模应用，再到房间规模的应用。</span><span class="sxs-lookup"><span data-stu-id="129ea-127">Windows Mixed Reality supports apps across a wide range of [experience scales](../../design/coordinate-systems.md#mixed-reality-experience-scales), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="129ea-128">在 HoloLens 上，你可以进一步构建全球规模的应用程序，让用户经历5米以上的工作，探索一座建筑的整个楼层。</span><span class="sxs-lookup"><span data-stu-id="129ea-128">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="129ea-129">在 Unity 中构建混合现实体验的第一步是确定应用的目标 [规模](../../design/coordinate-systems.md) ：</span><span class="sxs-lookup"><span data-stu-id="129ea-129">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](../../design/coordinate-systems.md) your app will target:</span></span>

* [<span data-ttu-id="129ea-130">方向或固定比例</span><span class="sxs-lookup"><span data-stu-id="129ea-130">Orientation or seated-scale</span></span>](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [<span data-ttu-id="129ea-131">办公室或房间规模</span><span class="sxs-lookup"><span data-stu-id="129ea-131">Standing or room-scale</span></span>](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [<span data-ttu-id="129ea-132">全球规模</span><span class="sxs-lookup"><span data-stu-id="129ea-132">World-scale</span></span>](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a><span data-ttu-id="129ea-133">会议室规模或共同体验</span><span class="sxs-lookup"><span data-stu-id="129ea-133">Room-scale or standing experiences</span></span>

> [!NOTE]
> <span data-ttu-id="129ea-134">如果要为 HL2 构建，我们建议创建一个目视的体验，或考虑使用 [场景理解来了解](../platform-capabilities-and-apis/scene-understanding-sdk.md) 场景的基底。</span><span class="sxs-lookup"><span data-stu-id="129ea-134">If you're building for HL2, we recommend creating an eye-level experience, or consider using [Scene Understanding](../platform-capabilities-and-apis/scene-understanding-sdk.md) to reason about the floor of your scene.</span></span>

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a><span data-ttu-id="129ea-135">未安装体验</span><span class="sxs-lookup"><span data-stu-id="129ea-135">Seated experiences</span></span>

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a><span data-ttu-id="129ea-136">设置相机背景</span><span class="sxs-lookup"><span data-stu-id="129ea-136">Setting up the camera background</span></span>

<span data-ttu-id="129ea-137">如果使用的是 MRTK，则会自动配置和管理照相机的背景。</span><span class="sxs-lookup"><span data-stu-id="129ea-137">If you're using MRTK, the camera's background is automatically configured and managed.</span></span> <span data-ttu-id="129ea-138">对于 XR SDK 或旧的 WSA 项目，建议在 HoloLens 上将相机的背景设置为纯色黑色，并将 skybox 设置为 "VR"。</span><span class="sxs-lookup"><span data-stu-id="129ea-138">For XR SDK or Legacy WSA projects, we recommend setting the camera's background to solid black on HoloLens and keeping the skybox for VR.</span></span>

## <a name="using-multiple-cameras"></a><span data-ttu-id="129ea-139">使用多个照相机</span><span class="sxs-lookup"><span data-stu-id="129ea-139">Using multiple cameras</span></span>

<span data-ttu-id="129ea-140">当场景中有多个照相机组件时，Unity 知道哪个照相机要用于 stereoscopic 呈现，具体取决于哪些 GameObject 具有 MainCamera 标记。</span><span class="sxs-lookup"><span data-stu-id="129ea-140">When there are multiple Camera components in the scene, Unity knows which camera to use for stereoscopic rendering based on which GameObject has the MainCamera tag.</span></span> <span data-ttu-id="129ea-141">在旧式 XR 中，它还使用此标记来同步头跟踪。</span><span class="sxs-lookup"><span data-stu-id="129ea-141">In legacy XR, it also uses this tag to sync head tracking.</span></span> <span data-ttu-id="129ea-142">在 XR SDK 中，head 跟踪由附加到相机的 TrackedPoseDriver 脚本驱动。</span><span class="sxs-lookup"><span data-stu-id="129ea-142">In XR SDK, head tracking is driven by a TrackedPoseDriver script attached to the camera.</span></span>

## <a name="sharing-depth-buffers"></a><span data-ttu-id="129ea-143">共享深度缓冲区</span><span class="sxs-lookup"><span data-stu-id="129ea-143">Sharing depth buffers</span></span>

<span data-ttu-id="129ea-144">将应用的深度缓冲区共享到 Windows 每个框架都将根据要呈现的耳机类型为应用程序提供以下两个增强功能之一：</span><span class="sxs-lookup"><span data-stu-id="129ea-144">Sharing your app's depth buffer to Windows each frame will give your app one of two boosts in hologram stability, based on the type of headset you're rendering for:</span></span>

* <span data-ttu-id="129ea-145">在提供深度缓冲区时， **VR 沉浸式耳机** 可以处理位置 reprojection，同时在位置和方向调整你的全息影像。</span><span class="sxs-lookup"><span data-stu-id="129ea-145">**VR immersive headsets** can take care of positional reprojection when a depth buffer is provided, adjusting your holograms for misprediction in both position and orientation.</span></span>
* <span data-ttu-id="129ea-146">**HoloLens 耳机** 具有几种不同的方法。</span><span class="sxs-lookup"><span data-stu-id="129ea-146">**HoloLens headsets** have a few different methods.</span></span> <span data-ttu-id="129ea-147">当提供了深度缓冲区时，HoloLens 1 将自动选择 [焦点](focus-point-in-unity.md) ，同时优化与最大内容相交的平面上的全息图稳定性。</span><span class="sxs-lookup"><span data-stu-id="129ea-147">HoloLens 1 will automatically select a [focus point](focus-point-in-unity.md) when a depth buffer is provided, optimizing hologram stability along the plane that intersects the most content.</span></span> <span data-ttu-id="129ea-148">HoloLens 2 将使用深度 LSR 来稳定内容 [ (请参阅备注) ](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)。</span><span class="sxs-lookup"><span data-stu-id="129ea-148">HoloLens 2 will stabilize content using [Depth LSR (see Remarks)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).</span></span>

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a><span data-ttu-id="129ea-149">使用剪辑平面</span><span class="sxs-lookup"><span data-stu-id="129ea-149">Using clipping planes</span></span>

<span data-ttu-id="129ea-150">在混合现实中，向用户呈现的内容太接近。</span><span class="sxs-lookup"><span data-stu-id="129ea-150">Rendering content too close to the user can be uncomfortable in mixed reality.</span></span> <span data-ttu-id="129ea-151">可以在相机组件上调整 [近和远的剪辑平面](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) 。</span><span class="sxs-lookup"><span data-stu-id="129ea-151">You can adjust the [near and far clip planes](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) on the Camera component.</span></span>

1. <span data-ttu-id="129ea-152">选择 "**层次结构**" 面板中的 **主相机**</span><span class="sxs-lookup"><span data-stu-id="129ea-152">Select the **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="129ea-153">在 " **检查器** " 面板中，找到 " **照相机** " 组件 **修剪平面** ，并将 " **Near** " 文本框从 **0.3** 更改为 **0.85**。</span><span class="sxs-lookup"><span data-stu-id="129ea-153">In the **Inspector** panel, find the **Camera** component **Clipping Planes** and change the **Near** textbox from **0.3** to **0.85**.</span></span> <span data-ttu-id="129ea-154">呈现更近的内容可能导致用户 discomfort，应根据 [渲染距离准则](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)加以避免。</span><span class="sxs-lookup"><span data-stu-id="129ea-154">Content rendered even closer can lead to user discomfort and should be avoided per the [render distance guidelines](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).</span></span>

## <a name="recentering-the-camera"></a><span data-ttu-id="129ea-155">Recentering 照相机</span><span class="sxs-lookup"><span data-stu-id="129ea-155">Recentering the camera</span></span>

<span data-ttu-id="129ea-156">如果要构建大规模的 [体验](../../design/coordinate-systems.md)，可以通过调用 XR，在用户的当前头部位置 recenter Unity 的世界原点 **[。InputTracking Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法在旧 XR 或 TRYRECENTER SDK 中的 **[XRInputSubsystem。](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)**</span><span class="sxs-lookup"><span data-stu-id="129ea-156">If you're building a [seated-scale experience](../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method in legacy XR or the **[XRInputSubsystem.TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** method in XR SDK.</span></span>

## <a name="teleportation"></a><span data-ttu-id="129ea-157">隐形传送</span><span class="sxs-lookup"><span data-stu-id="129ea-157">Teleportation</span></span>

<span data-ttu-id="129ea-158">此功能通常保留用于 VR 体验：</span><span class="sxs-lookup"><span data-stu-id="129ea-158">This feature is typically reserved for VR experiences:</span></span>

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a><span data-ttu-id="129ea-159">Reprojection 模式</span><span class="sxs-lookup"><span data-stu-id="129ea-159">Reprojection modes</span></span>

<span data-ttu-id="129ea-160">HoloLens 和沉浸式耳机都将 reproject 你的应用程序呈现的每个帧，以便在发出 photons 时，对用户实际头位置的任何 misprediction 进行调整。</span><span class="sxs-lookup"><span data-stu-id="129ea-160">Both HoloLens and immersive headsets will reproject each frame your app renders to adjust for any misprediction of the user's actual head position when photons are emitted.</span></span>

<span data-ttu-id="129ea-161">默认情况下：</span><span class="sxs-lookup"><span data-stu-id="129ea-161">By default:</span></span>

* <span data-ttu-id="129ea-162">如果应用为给定帧提供深度缓冲区，则 **VR 沉浸式耳机** 将负责定位 reprojection。</span><span class="sxs-lookup"><span data-stu-id="129ea-162">**VR immersive headsets** will take care of positional reprojection if the app provides a depth buffer for a given frame.</span></span> <span data-ttu-id="129ea-163">沉浸式耳机还会在位置和方向上调整 misprediction 的全息影像。</span><span class="sxs-lookup"><span data-stu-id="129ea-163">Immersive headsets will also adjust your holograms for misprediction in both position and orientation.</span></span> <span data-ttu-id="129ea-164">如果未提供深度缓冲区，则系统只会方向上的 mispredictions。</span><span class="sxs-lookup"><span data-stu-id="129ea-164">If a depth buffer isn't provided, the system will only correct mispredictions in orientation.</span></span>
* <span data-ttu-id="129ea-165">使用 HoloLens 2 的 **全息耳机**，无论应用是否提供其深度缓冲区，都将负责位置 reprojection。</span><span class="sxs-lookup"><span data-stu-id="129ea-165">**Holographic headsets** like HoloLens 2 will take care of positional reprojection whether the app provides its depth buffer or not.</span></span> <span data-ttu-id="129ea-166">在不使用 HoloLens 上的深度缓冲区的情况下，可能会出现位置 reprojection，因为呈现通常是由真实世界提供的稳定背景稀疏的。</span><span class="sxs-lookup"><span data-stu-id="129ea-166">Positional reprojection is possible without depth buffers on HoloLens as rendering is often sparse with a stable background provided by the real world.</span></span>

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="129ea-167">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="129ea-167">Next Development Checkpoint</span></span>

<span data-ttu-id="129ea-168">如果遵循我们所说的 Unity 开发旅程，就是在浏览 MRTK 核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="129ea-168">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="129ea-169">从这里，你可以继续了解下一部分基础知识：</span><span class="sxs-lookup"><span data-stu-id="129ea-169">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="129ea-170">凝视</span><span class="sxs-lookup"><span data-stu-id="129ea-170">Gaze</span></span>](gaze-in-unity.md)

<span data-ttu-id="129ea-171">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="129ea-171">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="129ea-172">共享体验</span><span class="sxs-lookup"><span data-stu-id="129ea-172">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="129ea-173">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="129ea-173">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="129ea-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="129ea-174">See also</span></span>

* [<span data-ttu-id="129ea-175">全息影像稳定性</span><span class="sxs-lookup"><span data-stu-id="129ea-175">Hologram stability</span></span>](../platform-capabilities-and-apis/hologram-stability.md)
* [<span data-ttu-id="129ea-176">体验规模</span><span class="sxs-lookup"><span data-stu-id="129ea-176">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="129ea-177">空间阶段</span><span class="sxs-lookup"><span data-stu-id="129ea-177">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="129ea-178">Unity 中的失跟</span><span class="sxs-lookup"><span data-stu-id="129ea-178">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="129ea-179">空间定位点</span><span class="sxs-lookup"><span data-stu-id="129ea-179">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="129ea-180">Unity 中的持久性</span><span class="sxs-lookup"><span data-stu-id="129ea-180">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="129ea-181">Unity 中的共享体验</span><span class="sxs-lookup"><span data-stu-id="129ea-181">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="129ea-182">Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="129ea-182">Azure Spatial Anchors</span></span>](/azure/spatial-anchors)
* [<span data-ttu-id="129ea-183">用于 Unity 的 Azure 空间定位点 SDK</span><span class="sxs-lookup"><span data-stu-id="129ea-183">Azure Spatial Anchors SDK for Unity</span></span>](/dotnet/api/Microsoft.Azure.SpatialAnchors)