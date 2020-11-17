---
title: Unity 中的相机
description: 如何使用 Unity 用于 Windows Mixed Reality 开发的主照相机进行全息渲染。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，全息呈现，全息，沉浸式，聚焦点，深度缓冲，仅限方向，定位，不透明，透明，剪辑，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: c3c470634e2c5c9445ae8c0a29621971de22a92b
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677616"
---
# <a name="camera-in-unity"></a><span data-ttu-id="34de7-104">Unity 中的相机</span><span class="sxs-lookup"><span data-stu-id="34de7-104">Camera in Unity</span></span>

<span data-ttu-id="34de7-105">当你磨损混合现实耳机时，它将成为你的全息世界的中心。</span><span class="sxs-lookup"><span data-stu-id="34de7-105">When you wear a mixed reality headset, it becomes the center of your holographic world.</span></span> <span data-ttu-id="34de7-106">当你的项目具有 "Windows Mixed Reality" 所选的 "受支持的虚拟现实" 时，Unity [相机](https://docs.unity3d.com/Manual/class-Camera.html) 组件会自动处理 stereoscopic 渲染，并遵循你的头运动和旋转，因为设备 (会出现在 Windows 应用商店播放机设置) 的 "其他设置" 部分中。</span><span class="sxs-lookup"><span data-stu-id="34de7-106">The Unity [Camera](https://docs.unity3d.com/Manual/class-Camera.html) component will automatically handle stereoscopic rendering and will follow your head movement and rotation when your project has "Virtual Reality Supported" selected with "Windows Mixed Reality" as the device (in the Other Settings section of the Windows Store Player Settings).</span></span> <span data-ttu-id="34de7-107">在较旧版本的 Unity 中，这可能作为 "Windows 全息" 列出。</span><span class="sxs-lookup"><span data-stu-id="34de7-107">This may be listed as "Windows Holographic" in older versions of Unity.</span></span>

<span data-ttu-id="34de7-108">但是，若要完全优化视觉质量和 [全息图稳定性](../platform-capabilities-and-apis/hologram-stability.md)，应设置以下描述的相机设置。</span><span class="sxs-lookup"><span data-stu-id="34de7-108">However, to fully optimize visual quality and [hologram stability](../platform-capabilities-and-apis/hologram-stability.md), you should set the camera settings described below.</span></span>

>[!NOTE]
><span data-ttu-id="34de7-109">需要在应用的每个场景中将这些设置应用到相机。</span><span class="sxs-lookup"><span data-stu-id="34de7-109">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="34de7-110">默认情况下，当你在 Unity 中创建新场景时，它将包含层次结构中的一个主相机 GameObject，其中包括相机组件，但未正确应用下面的设置。</span><span class="sxs-lookup"><span data-stu-id="34de7-110">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

## <a name="holographic-vs-immersive-headsets"></a><span data-ttu-id="34de7-111">全息和沉浸式耳机</span><span class="sxs-lookup"><span data-stu-id="34de7-111">Holographic vs. immersive headsets</span></span>

<span data-ttu-id="34de7-112">Unity 相机组件上的默认设置适用于需要 skybox 的背景的传统3D 应用程序，因为这些应用程序不是真实的。</span><span class="sxs-lookup"><span data-stu-id="34de7-112">The default settings on the Unity Camera component are for traditional 3D applications which need a skybox-like background as they don't have a real world.</span></span>

* <span data-ttu-id="34de7-113">在 **[沉浸式头戴式耳机](../../discover/immersive-headset-hardware-details.md)** 上运行时，会呈现用户看到的所有内容，因此你可能需要保留 skybox。</span><span class="sxs-lookup"><span data-stu-id="34de7-113">When running on an **[immersive headset](../../discover/immersive-headset-hardware-details.md)**, you are rendering everything the user sees, and so you'll likely want to keep the skybox.</span></span>
* <span data-ttu-id="34de7-114">但是，当在 **全息耳机** （如 [HoloLens](../../hololens-hardware-details.md)）上运行时，真实环境应显示在照相机呈现的所有内容之后。</span><span class="sxs-lookup"><span data-stu-id="34de7-114">However, when running on a **holographic headset** like [HoloLens](../../hololens-hardware-details.md), the real world should appear behind everything the camera renders.</span></span> <span data-ttu-id="34de7-115">为此，请将相机背景设置为在 HoloLens (透明，黑色呈现为透明) 而不是 Skybox 纹理：</span><span class="sxs-lookup"><span data-stu-id="34de7-115">To do this, set the camera background to be transparent (in HoloLens, black renders as transparent) instead of a Skybox texture:</span></span>
    1. <span data-ttu-id="34de7-116">选择 "层次结构" 面板中的主相机</span><span class="sxs-lookup"><span data-stu-id="34de7-116">Select the Main Camera in the Hierarchy panel</span></span>
    2. <span data-ttu-id="34de7-117">在 "检查器" 面板中，找到照相机组件，并将 "清除标志" 下拉列表从 "Skybox" 更改为纯色</span><span class="sxs-lookup"><span data-stu-id="34de7-117">In the Inspector panel, find the Camera component and change the Clear Flags dropdown from Skybox to Solid Color</span></span>
    3. <span data-ttu-id="34de7-118">选择背景色选取器并将 RGBA 值更改为 (0，0，0，0) </span><span class="sxs-lookup"><span data-stu-id="34de7-118">Select the Background color picker and change the RGBA values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="34de7-119">您可以使用脚本代码，通过检查 [HolographicSettings](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)来确定头戴式耳机是沉浸还是全息。</span><span class="sxs-lookup"><span data-stu-id="34de7-119">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>

## <a name="positioning-the-camera"></a><span data-ttu-id="34de7-120">定位照相机</span><span class="sxs-lookup"><span data-stu-id="34de7-120">Positioning the Camera</span></span>

<span data-ttu-id="34de7-121">如果将用户的起始位置想像为 (X：0，Y：0，Z： 0) ，则可以更容易地设计应用程序。</span><span class="sxs-lookup"><span data-stu-id="34de7-121">It will be easier to lay out your app if you imagine the starting position of the user as (X: 0, Y: 0, Z: 0).</span></span> <span data-ttu-id="34de7-122">由于摄像机正在跟踪用户的头移动，因此可以通过设置主摄像机的开始位置来设置用户的起始位置。</span><span class="sxs-lookup"><span data-stu-id="34de7-122">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="34de7-123">选择 "层次结构" 面板中的 "主相机"</span><span class="sxs-lookup"><span data-stu-id="34de7-123">Select Main Camera in the Hierarchy panel</span></span>
2. <span data-ttu-id="34de7-124">在 "检查器" 面板中，找到转换组件，并将位置从 (X：0，Y：1，Z：-10) 更改为 (X：0，Y：0，Z： 0) </span><span class="sxs-lookup"><span data-stu-id="34de7-124">In the Inspector panel, find the Transform component and change the Position from (X: 0, Y: 1, Z: -10) to (X: 0, Y: 0, Z: 0)</span></span>

   <span data-ttu-id="34de7-125">![Unity 中的 "检查器" 窗格中的照相机](images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="34de7-125">![Camera in the Inspector pane in Unity](images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="34de7-126">*Unity 中的 "检查器" 窗格中的照相机*</span><span class="sxs-lookup"><span data-stu-id="34de7-126">*Camera in the Inspector pane in Unity*</span></span>

## <a name="clip-planes"></a><span data-ttu-id="34de7-127">剪辑平面</span><span class="sxs-lookup"><span data-stu-id="34de7-127">Clip planes</span></span>

<span data-ttu-id="34de7-128">在混合现实中，向用户呈现的内容太接近。</span><span class="sxs-lookup"><span data-stu-id="34de7-128">Rendering content too close to the user can be uncomfortable in mixed reality.</span></span> <span data-ttu-id="34de7-129">可以在相机组件上调整 [近和远的剪辑平面](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) 。</span><span class="sxs-lookup"><span data-stu-id="34de7-129">You can adjust the [near and far clip planes](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) on the Camera component.</span></span>

1. <span data-ttu-id="34de7-130">选择 "层次结构" 面板中的主相机</span><span class="sxs-lookup"><span data-stu-id="34de7-130">Select the Main Camera in the Hierarchy panel</span></span>
2. <span data-ttu-id="34de7-131">在 "检查器" 面板中，找到 "照相机" 组件剪辑平面，并将 "Near" 文本框从0.3 更改为85。</span><span class="sxs-lookup"><span data-stu-id="34de7-131">In the Inspector panel, find the Camera component Clipping Planes and change the Near textbox from 0.3 to .85.</span></span> <span data-ttu-id="34de7-132">呈现更近的内容可能导致用户 discomfort，应根据 [渲染距离准则](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)加以避免。</span><span class="sxs-lookup"><span data-stu-id="34de7-132">Content rendered even closer can lead to user discomfort and should be avoided per the [render distance guidelines](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).</span></span>

## <a name="multiple-cameras"></a><span data-ttu-id="34de7-133">多个照相机</span><span class="sxs-lookup"><span data-stu-id="34de7-133">Multiple Cameras</span></span>

<span data-ttu-id="34de7-134">如果场景中有多个照相机组件，则通过检查哪些 GameObject 具有 MainCamera 标记，Unity 知道哪个照相机要用于 stereoscopic 渲染和打印头跟踪。</span><span class="sxs-lookup"><span data-stu-id="34de7-134">When there are multiple Camera components in the scene, Unity knows which camera to use for stereoscopic rendering and head tracking by checking which GameObject has the MainCamera tag.</span></span>

## <a name="recentering-a-seated-experience"></a><span data-ttu-id="34de7-135">Recentering 体验</span><span class="sxs-lookup"><span data-stu-id="34de7-135">Recentering a seated experience</span></span>

<span data-ttu-id="34de7-136">如果要构建大规模的 [体验](../../design/coordinate-systems.md)，可以通过调用 XR，在用户的当前头部位置 recenter Unity 的世界原点 **[。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法。</span><span class="sxs-lookup"><span data-stu-id="34de7-136">If you're building a [seated-scale experience](../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>

## <a name="reprojection-modes"></a><span data-ttu-id="34de7-137">Reprojection 模式</span><span class="sxs-lookup"><span data-stu-id="34de7-137">Reprojection modes</span></span>

<span data-ttu-id="34de7-138">HoloLens 和沉浸式耳机都将 reproject 你的应用程序呈现的每个帧，以便在发出 photons 时，对用户实际头位置的任何 misprediction 进行调整。</span><span class="sxs-lookup"><span data-stu-id="34de7-138">Both HoloLens and immersive headsets will reproject each frame your app renders to adjust for any misprediction of the user's actual head position when photons are emitted.</span></span>

<span data-ttu-id="34de7-139">默认情况下：</span><span class="sxs-lookup"><span data-stu-id="34de7-139">By default:</span></span>

* <span data-ttu-id="34de7-140">**沉浸式耳机** 将执行位置 reprojection，如果应用为给定帧提供深度缓冲区，则在位置和方向调整你的全息影像。</span><span class="sxs-lookup"><span data-stu-id="34de7-140">**Immersive headsets** will perform positional reprojection, adjusting your holograms for misprediction in both position and orientation, if the app provides a depth buffer for a given frame.</span></span>  <span data-ttu-id="34de7-141">如果未提供深度缓冲区，则系统只会方向上的 mispredictions。</span><span class="sxs-lookup"><span data-stu-id="34de7-141">If a depth buffer is not provided, the system will only correct mispredictions in orientation.</span></span>
* <span data-ttu-id="34de7-142">如果应用程序提供了深度缓冲区，就像 HoloLens 这样的 **全息耳机** 会执行位置 reprojection。</span><span class="sxs-lookup"><span data-stu-id="34de7-142">**Holographic headsets** like HoloLens will perform positional reprojection whether the app provides its depth buffer or not.</span></span>  <span data-ttu-id="34de7-143">在不使用 HoloLens 上的深度缓冲区的情况下，可能会出现位置 reprojection，因为呈现通常是由真实世界提供的稳定背景稀疏的。</span><span class="sxs-lookup"><span data-stu-id="34de7-143">Positional reprojection is possible without depth buffers on HoloLens as rendering is often sparse with a stable background provided by the real world.</span></span>

<span data-ttu-id="34de7-144">如果你知道要使用严格的正文锁定内容构建 [仅限方向的体验](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) (例如360度的视频内容) ，则只能通过将 [HolographicSettings](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) 设置为 [HolographicReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)，将 reprojection 模式显式设置为 "方向"。</span><span class="sxs-lookup"><span data-stu-id="34de7-144">If you know that you are building an [orientation-only experience](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (e.g. 360-degree video content), you can explicitly set the reprojection mode to be orientation only by setting [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) to [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span></span>

## <a name="sharing-your-depth-buffers-with-windows"></a><span data-ttu-id="34de7-145">与 Windows 共享你的深度缓冲区</span><span class="sxs-lookup"><span data-stu-id="34de7-145">Sharing your depth buffers with Windows</span></span>

<span data-ttu-id="34de7-146">将应用的深度缓冲区共享到 Windows 每个框架都将根据要呈现的耳机类型为应用程序提供以下两个增强功能之一：</span><span class="sxs-lookup"><span data-stu-id="34de7-146">Sharing your app's depth buffer to Windows each frame will give your app one of two boosts in hologram stability, based on the type of headset you're rendering for:</span></span>

* <span data-ttu-id="34de7-147">当提供了深度缓冲区时，**沉浸式耳机** 可以执行位置 reprojection，同时调整 misprediction 在位置和方向上的影像。</span><span class="sxs-lookup"><span data-stu-id="34de7-147">**Immersive headsets** can perform positional reprojection when a depth buffer is provided, adjusting your holograms for misprediction in both position and orientation.</span></span>
* <span data-ttu-id="34de7-148">**全息耳机** 具有几种不同的方法。</span><span class="sxs-lookup"><span data-stu-id="34de7-148">**Holographic headsets** have a few different methods.</span></span> <span data-ttu-id="34de7-149">当提供了深度缓冲区时，HoloLens 1 将自动选择 [焦点](focus-point-in-unity.md) ，同时优化与最大内容相交的平面上的全息图稳定性。</span><span class="sxs-lookup"><span data-stu-id="34de7-149">HoloLens 1 will automatically select a [focus point](focus-point-in-unity.md) when a depth buffer is provided, optimizing hologram stability along the plane that intersects the most content.</span></span> <span data-ttu-id="34de7-150">HoloLens 2 将使用深度 LSR 来稳定内容 [ (请参阅备注) ](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)。</span><span class="sxs-lookup"><span data-stu-id="34de7-150">HoloLens 2 will stabilize content using [Depth LSR (see Remarks)](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).</span></span>

<span data-ttu-id="34de7-151">设置 Unity 应用是否将向 Windows 提供深度缓冲区：</span><span class="sxs-lookup"><span data-stu-id="34de7-151">To set whether your Unity app will provide a depth buffer to Windows:</span></span>

1. <span data-ttu-id="34de7-152">请参阅 **编辑**  >  **项目设置**  >  **播放器**  >  **通用 Windows 平台选项卡**  >  **XR 设置**。</span><span class="sxs-lookup"><span data-stu-id="34de7-152">Go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform tab** > **XR Settings**.</span></span>
2. <span data-ttu-id="34de7-153">展开 " **Windows Mixed REALITY SDK** " 项。</span><span class="sxs-lookup"><span data-stu-id="34de7-153">Expand the **Windows Mixed Reality SDK** item.</span></span>
3. <span data-ttu-id="34de7-154">选中或取消选中 " **启用深度缓冲共享** " 复选框。</span><span class="sxs-lookup"><span data-stu-id="34de7-154">Check or uncheck the **Enable Depth Buffer Sharing** check box.</span></span>  <span data-ttu-id="34de7-155">默认情况下，在新创建的项目中将选中此功能，因为此功能已添加到 Unity，并且默认情况下将为升级的旧项目取消选中。</span><span class="sxs-lookup"><span data-stu-id="34de7-155">This will be checked by default in new projects created since this feature was added to Unity and will be unchecked by default for older projects that were upgraded.</span></span>

<span data-ttu-id="34de7-156">向 Windows 提供深度缓冲区可以提高视觉质量，只要 Windows 可以使用在主摄像机上的 Unity 中已设置的近和远的平面，将深度缓冲区中的规范化的每像素深度值准确地映射回米的距离。</span><span class="sxs-lookup"><span data-stu-id="34de7-156">Providing a depth buffer to Windows can improve visual quality so long as Windows can accurately map the normalized per-pixel depth values in your depth buffer back to distances in meters, using the near and far planes you've set in Unity on the main camera.</span></span>  <span data-ttu-id="34de7-157">如果您的呈现器通过使用典型的方式来处理深度值，则通常情况下，您应该非常好，但是，在显示到现有颜色像素时，写入深度缓冲区的半透明渲染传递可能会混淆 reprojection。</span><span class="sxs-lookup"><span data-stu-id="34de7-157">If your render passes handle depth values in typical ways, you should generally be fine here, though translucent render passes that write to the depth buffer while showing through to existing color pixels can confuse the reprojection.</span></span>  <span data-ttu-id="34de7-158">如果你知道，你的 render pass 会使很多最终深度像素具有不准确的深度值，则你可能会通过取消选中 "启用深度缓冲区共享" 获得更好的视觉质量。 # # 下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="34de7-158">If you know that your render passes will leave many of your final depth pixels with inaccurate depth values, you are likely to get better visual quality by unchecking "Enable Depth Buffer Sharing".## Next Development Checkpoint</span></span>

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit-v2"></a><span data-ttu-id="34de7-159">带有混合现实工具包 v2 的自动场景和照相机设置</span><span class="sxs-lookup"><span data-stu-id="34de7-159">Automatic Scene and Camera Setup with Mixed Reality Toolkit v2</span></span>

<span data-ttu-id="34de7-160">按照将混合现实工具包 v2 添加到 Unity [项目中的分步指南操作](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) ，它将自动配置你的项目。</span><span class="sxs-lookup"><span data-stu-id="34de7-160">Follow the [step-by-step](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) guide to add Mixed Reality Toolkit v2 to your Unity project and it will configure your project automatically.</span></span> <span data-ttu-id="34de7-161">你还可以通过以下部分中的指南手动配置项目，而无需 MRTK。</span><span class="sxs-lookup"><span data-stu-id="34de7-161">You can also manually configure the project without MRTK with the guide in the section below.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="34de7-162">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="34de7-162">Next Development Checkpoint</span></span>

<span data-ttu-id="34de7-163">如果遵循我们规划的 Unity 的开发检查点旅程，则你在探索 MRTK 核心构建基块的过程中。</span><span class="sxs-lookup"><span data-stu-id="34de7-163">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="34de7-164">从这里，你可以进入下一个构建基块：</span><span class="sxs-lookup"><span data-stu-id="34de7-164">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="34de7-165">凝视</span><span class="sxs-lookup"><span data-stu-id="34de7-165">Gaze</span></span>](gaze-in-unity.md)

<span data-ttu-id="34de7-166">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="34de7-166">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="34de7-167">共享体验</span><span class="sxs-lookup"><span data-stu-id="34de7-167">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="34de7-168">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="34de7-168">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="34de7-169">请参阅</span><span class="sxs-lookup"><span data-stu-id="34de7-169">See also</span></span>

* [<span data-ttu-id="34de7-170">全息影像稳定性</span><span class="sxs-lookup"><span data-stu-id="34de7-170">Hologram stability</span></span>](../platform-capabilities-and-apis/hologram-stability.md)
* [<span data-ttu-id="34de7-171">MixedRealityToolkit prefab</span><span class="sxs-lookup"><span data-stu-id="34de7-171">MixedRealityToolkit Main Camera.prefab</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
