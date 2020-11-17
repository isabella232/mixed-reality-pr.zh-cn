---
title: 为 Windows Mixed Reality 配置新的 Unity 项目
description: 有关为 Windows Mixed Reality 配置 Unity 项目的说明
author: thetuvix
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity，混合现实，开发，入门，新项目，Windows Mixed Reality，UWP，XR，性能
ms.openlocfilehash: cd7e6c5681c717c37368393a605998a2ab8e4175
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677666"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="3fa99-104">为 Windows Mixed Reality 配置新的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="3fa99-104">Configure a New Unity project for Windows Mixed Reality</span></span> 

## <a name="overview"></a><span data-ttu-id="3fa99-105">概述</span><span class="sxs-lookup"><span data-stu-id="3fa99-105">Overview</span></span>

<span data-ttu-id="3fa99-106">Windows Mixed Reality (WMR) 是作为 Windows 10 操作系统的一部分引入的 Microsoft 平台。</span><span class="sxs-lookup"><span data-stu-id="3fa99-106">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="3fa99-107">WMR 平台使你能够生成在全息和 VR 显示设备上呈现数字内容的应用程序。</span><span class="sxs-lookup"><span data-stu-id="3fa99-107">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="3fa99-108">设置 WMR 时，可以采用两个路径。</span><span class="sxs-lookup"><span data-stu-id="3fa99-108">When setting up for WMR, there are two paths you can take.</span></span> <span data-ttu-id="3fa99-109">第一种方法是安装 [混合现实工具包 (MRTK) ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)，它将自动设置 WMR 环境。</span><span class="sxs-lookup"><span data-stu-id="3fa99-109">Your first option is to install the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html), which will automatically set up the WMR environment.</span></span> <span data-ttu-id="3fa99-110">第二种方法是手动更改一些 Unity 设置以使用 WMR 进行滚动。</span><span class="sxs-lookup"><span data-stu-id="3fa99-110">The second option is to manually change a few Unity settings to get rolling with WMR.</span></span> 

> [!NOTE]
> <span data-ttu-id="3fa99-111">你始终可以在以后导入 MRTK，因此，不会产生要首先进行手动路由的损失。</span><span class="sxs-lookup"><span data-stu-id="3fa99-111">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="3fa99-112">如果选择 WMR 手动设置，则需要更改的设置将分为两个类别：每个项目和每场景。</span><span class="sxs-lookup"><span data-stu-id="3fa99-112">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="3fa99-113">每个项目的设置</span><span class="sxs-lookup"><span data-stu-id="3fa99-113">Per-project settings</span></span>

<span data-ttu-id="3fa99-114">需要为 WMR 更改的第一个设置是项目平台：</span><span class="sxs-lookup"><span data-stu-id="3fa99-114">The first setting you need to change for WMR is the project platform:</span></span> 
1. <span data-ttu-id="3fa99-115">选择 **文件 > 生成设置 ...**</span><span class="sxs-lookup"><span data-stu-id="3fa99-115">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="3fa99-116">选择 "平台" 列表中的 "**通用 Windows 平台**"，然后单击 "**切换平台**"</span><span class="sxs-lookup"><span data-stu-id="3fa99-116">Select **Universal Windows Platform** in the Platform list and click **Switch Platform**</span></span>
3. <span data-ttu-id="3fa99-117">将 **SDK** 设置为 **通用 10**</span><span class="sxs-lookup"><span data-stu-id="3fa99-117">Set **SDK** to **Universal 10**</span></span>
4. <span data-ttu-id="3fa99-118">将 **目标设备** 设置为 **任何设备** 以支持沉浸式耳机或切换到 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="3fa99-118">Set **Target device** to **Any Device** to support immersive headsets or switch to **HoloLens**</span></span>
5. <span data-ttu-id="3fa99-119">将 **生成类型** 设置为 **D3D**</span><span class="sxs-lookup"><span data-stu-id="3fa99-119">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="3fa99-120">将 **UWP SDK** 设置为 **安装的最新版本**</span><span class="sxs-lookup"><span data-stu-id="3fa99-120">Set **UWP SDK** to **Latest installed**</span></span>

<img src="images/unity-uwp-settings.png" width="550px" alt="Unity XR Settings">
<span data-ttu-id="3fa99-121">*Unity XR 设置*</span><span class="sxs-lookup"><span data-stu-id="3fa99-121">*Unity XR settings*</span></span>

<span data-ttu-id="3fa99-122">正确配置平台后，需要让 Unity 知道应用在导出时应创建 [沉浸式视图](../../design/app-views.md) 而不是2d 视图：</span><span class="sxs-lookup"><span data-stu-id="3fa99-122">After the platform is configured correctly, you need to let Unity know that your app should create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>
1. <span data-ttu-id="3fa99-123">从 "**生成设置 ...** " 窗口中，打开 "**播放机设置 ...** "</span><span class="sxs-lookup"><span data-stu-id="3fa99-123">From the **Build Settings...** window, open **Player Settings...**</span></span>
2. <span data-ttu-id="3fa99-124">选择通用 Windows 平台 "选项卡的" **设置** "，然后展开" **XR 设置** "组</span><span class="sxs-lookup"><span data-stu-id="3fa99-124">Select the **Settings for Universal Windows Platform** tab and expand the **XR Settings** group</span></span>
3. <span data-ttu-id="3fa99-125">在 " **XR 设置** " 部分中，选中 " **受支持的虚拟现实** " 复选框以添加 " **虚拟现实设备** " 列表。</span><span class="sxs-lookup"><span data-stu-id="3fa99-125">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add the **Virtual Reality Devices** list.</span></span>
4. <span data-ttu-id="3fa99-126">在 " **XR 设置** " 组中，确认 **"Windows Mixed Reality"** 列为受支持的设备。</span><span class="sxs-lookup"><span data-stu-id="3fa99-126">In the **XR Settings** group, confirm that **"Windows Mixed Reality"** is listed as a supported device.</span></span> <span data-ttu-id="3fa99-127"> (此选项可能在早期版本的 Unity 中显示为 **Windows 全息**) </span><span class="sxs-lookup"><span data-stu-id="3fa99-127">(this option may appear as **Windows Holographic** in older versions of Unity)</span></span>

<span data-ttu-id="3fa99-128">![Unity UWP 设置](images/xrsettings.png)</span><span class="sxs-lookup"><span data-stu-id="3fa99-128">![Unity UWP settings](images/xrsettings.png)</span></span><br>
<span data-ttu-id="3fa99-129">*Unity XR 设置*</span><span class="sxs-lookup"><span data-stu-id="3fa99-129">*Unity XR settings*</span></span>

### <a name="updating-the-manifest"></a><span data-ttu-id="3fa99-130">更新清单</span><span class="sxs-lookup"><span data-stu-id="3fa99-130">Updating the manifest</span></span>

<span data-ttu-id="3fa99-131">您的应用程序现在可以处理全息呈现和空间输入。</span><span class="sxs-lookup"><span data-stu-id="3fa99-131">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="3fa99-132">但是，你的应用程序需要在其清单中声明相应的功能，才能利用某些功能。</span><span class="sxs-lookup"><span data-stu-id="3fa99-132">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="3fa99-133">可以通过转到 " **播放机设置" > "通用 Windows 平台 >" 发布设置 "> 功能**，找到项目功能。</span><span class="sxs-lookup"><span data-stu-id="3fa99-133">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="3fa99-134">建议在 Unity 中创建清单声明，以将其包含在所有以后导出的项目中。</span><span class="sxs-lookup"><span data-stu-id="3fa99-134">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="3fa99-135">为混合现实启用常用 Unity Api 的适用功能包括：</span><span class="sxs-lookup"><span data-stu-id="3fa99-135">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="3fa99-136">功能</span><span class="sxs-lookup"><span data-stu-id="3fa99-136">Capability</span></span>  |  <span data-ttu-id="3fa99-137">需要功能的 Api</span><span class="sxs-lookup"><span data-stu-id="3fa99-137">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="3fa99-138">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="3fa99-138">SpatialPerception</span></span>  |  <span data-ttu-id="3fa99-139">SurfaceObserver (访问 HoloLens 上的 [空间映射](../../design/spatial-mapping.md)网格) &mdash; *无需对耳机进行常规空间跟踪*</span><span class="sxs-lookup"><span data-stu-id="3fa99-139">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="3fa99-140">网络摄像头</span><span class="sxs-lookup"><span data-stu-id="3fa99-140">WebCam</span></span>  |  <span data-ttu-id="3fa99-141">PhotoCapture 和 VideoCapture</span><span class="sxs-lookup"><span data-stu-id="3fa99-141">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="3fa99-142">PicturesLibrary/VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="3fa99-142">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="3fa99-143">PhotoCapture 或 VideoCapture，分别 (存储捕获的内容) </span><span class="sxs-lookup"><span data-stu-id="3fa99-143">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="3fa99-144">麦克风</span><span class="sxs-lookup"><span data-stu-id="3fa99-144">Microphone</span></span>  |  <span data-ttu-id="3fa99-145">捕获音频) 、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer 时的 VideoCapture (</span><span class="sxs-lookup"><span data-stu-id="3fa99-145">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="3fa99-146">InternetClient</span><span class="sxs-lookup"><span data-stu-id="3fa99-146">InternetClient</span></span>  |  <span data-ttu-id="3fa99-147">DictationRecognizer (并使用 Unity 探查器) </span><span class="sxs-lookup"><span data-stu-id="3fa99-147">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="3fa99-148">质量设置</span><span class="sxs-lookup"><span data-stu-id="3fa99-148">Quality settings</span></span>

<span data-ttu-id="3fa99-149">HoloLens 具有移动类 GPU。</span><span class="sxs-lookup"><span data-stu-id="3fa99-149">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="3fa99-150">如果你的应用面向 HoloLens，你需要调整应用中的质量设置以实现最快的性能，以确保它保持完整的帧速率：</span><span class="sxs-lookup"><span data-stu-id="3fa99-150">If your app is targeting HoloLens, you'll want the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate:</span></span>
1. <span data-ttu-id="3fa99-151">选择 "**编辑 > 项目设置 > 质量**"</span><span class="sxs-lookup"><span data-stu-id="3fa99-151">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="3fa99-152">选择 **Windows 应用商店** 徽标下的 **下拉列表**，并选择 "**非常低**"。</span><span class="sxs-lookup"><span data-stu-id="3fa99-152">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="3fa99-153">如果 Windows 应用商店列和 **极低** 的行中的框为绿色，则会知道设置正确应用。</span><span class="sxs-lookup"><span data-stu-id="3fa99-153">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

<span data-ttu-id="3fa99-154">![Unity 质量设置](images/getting-started-unity-quality-settings.jpg)</span><span class="sxs-lookup"><span data-stu-id="3fa99-154">![Unity quality settings](images/getting-started-unity-quality-settings.jpg)</span></span><br>
<span data-ttu-id="3fa99-155">*Unity 质量设置*</span><span class="sxs-lookup"><span data-stu-id="3fa99-155">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="3fa99-156">每场景设置</span><span class="sxs-lookup"><span data-stu-id="3fa99-156">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="3fa99-157">Unity 照相机设置</span><span class="sxs-lookup"><span data-stu-id="3fa99-157">Unity camera settings</span></span>

<span data-ttu-id="3fa99-158">如果选中 " **支持虚拟现实** "，则 [Unity 相机](camera-in-unity.md) 组件会处理 [头跟踪和 stereoscopic 呈现](../platform-capabilities-and-apis/rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="3fa99-158">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="3fa99-159">这意味着不需要使用自定义相机替换主相机对象。</span><span class="sxs-lookup"><span data-stu-id="3fa99-159">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="3fa99-160">如果你的应用程序专门面向 HoloLens，则需要更改一些设置以优化设备的透明显示。</span><span class="sxs-lookup"><span data-stu-id="3fa99-160">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="3fa99-161">这些设置允许你的全息内容透过物理环境显示：</span><span class="sxs-lookup"><span data-stu-id="3fa99-161">These settings allow your holographic content to show through to the physical world:</span></span>
1. <span data-ttu-id="3fa99-162">在 **层次结构** 中，选择 **主相机**</span><span class="sxs-lookup"><span data-stu-id="3fa99-162">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="3fa99-163">在 " **检查器** " 面板中，将转换 **位置** 设置为 **0，0，0，** 以使用户头部的位置从 Unity 世界原点开始。</span><span class="sxs-lookup"><span data-stu-id="3fa99-163">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="3fa99-164">将 **清除标志** 更改为 **纯色**。</span><span class="sxs-lookup"><span data-stu-id="3fa99-164">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="3fa99-165">将 **背景** 色更改为 **RGBA 0，0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="3fa99-165">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="3fa99-166">在 HoloLens 中，黑色呈现为透明。</span><span class="sxs-lookup"><span data-stu-id="3fa99-166">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="3fa99-167">更改 **剪辑平面-接近** 于 [HoloLens 建议](camera-in-unity.md#clip-planes) 0.85 (米) 。</span><span class="sxs-lookup"><span data-stu-id="3fa99-167">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="3fa99-168">![Unity 照相机设置](images/Unitycamerasettings.png)</span><span class="sxs-lookup"><span data-stu-id="3fa99-168">![Unity camera settings](images/Unitycamerasettings.png)</span></span><br>
<span data-ttu-id="3fa99-169">*Unity 照相机设置*</span><span class="sxs-lookup"><span data-stu-id="3fa99-169">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3fa99-170">如果删除并创建新相机，请确保将新相机标记为 " **MainCamera**"。</span><span class="sxs-lookup"><span data-stu-id="3fa99-170">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fa99-171">请参阅</span><span class="sxs-lookup"><span data-stu-id="3fa99-171">See also</span></span>
* [<span data-ttu-id="3fa99-172">MRTK - 安装指南 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="3fa99-172">MRTK - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="3fa99-173">MRTK - 文档主页 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="3fa99-173">MRTK - Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="3fa99-174">安装工具</span><span class="sxs-lookup"><span data-stu-id="3fa99-174">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="3fa99-175">Unity 开发概述</span><span class="sxs-lookup"><span data-stu-id="3fa99-175">Unity Development Overview</span></span>](unity-development-overview.md)
