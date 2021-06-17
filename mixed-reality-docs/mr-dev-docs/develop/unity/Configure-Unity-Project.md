---
title: 在没有 MRTK 的情况下配置项目
description: 了解如何在没有混合现实工具包的情况下为Windows Mixed Reality Unity 项目。
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity， 混合现实， 开发， 入门， 新项目， Windows Mixed Reality， UWP， XR， 性能
ms.openlocfilehash: c496dc415ff09eea3015b5195e131554c43a98f1
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110253"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="836e8-104">配置项目时不使用 MRTK</span><span class="sxs-lookup"><span data-stu-id="836e8-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="836e8-105">Windows Mixed Reality (WMR) 是作为操作系统的一Windows 10引入的 Microsoft 平台。</span><span class="sxs-lookup"><span data-stu-id="836e8-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="836e8-106">使用 WMR 平台，可以生成在全息和 VR 显示设备上呈现数字内容的应用程序。</span><span class="sxs-lookup"><span data-stu-id="836e8-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="836e8-107">虽然 Microsoft 和社区已创建开放源代码工具，例如混合现实工具包 [ (MRTK) ， ](/windows/mixed-reality/mrtk-unity/configuration/usingupm) 这些工具将自动设置 WMR 环境，但许多开发人员希望从头构建自己的体验。</span><span class="sxs-lookup"><span data-stu-id="836e8-107">While Microsoft and the community have created open source tools such as the [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="836e8-108">以下文档将演示如何正确设置混合现实开发项目，无论你是否使用 MRTK。</span><span class="sxs-lookup"><span data-stu-id="836e8-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="836e8-109">需要更改的设置分为两类：每项目设置和按场景设置。</span><span class="sxs-lookup"><span data-stu-id="836e8-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="836e8-110">以后始终可以导入 MRTK，因此先执行手动路由不会有什么损失。</span><span class="sxs-lookup"><span data-stu-id="836e8-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="836e8-111">如果选择 WMR 手动设置，则需要更改的设置将细分为两个类别：每个项目和每个场景。</span><span class="sxs-lookup"><span data-stu-id="836e8-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="836e8-112">每项目设置</span><span class="sxs-lookup"><span data-stu-id="836e8-112">Per-project settings</span></span>

<span data-ttu-id="836e8-113">如果面向桌面 VR，我们建议使用默认情况下在新的 Unity 项目上选择的 PC 独立平台：</span><span class="sxs-lookup"><span data-stu-id="836e8-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中突出显示了"MAC &独立平台"](images/wmr-config-img-3.png)

<span data-ttu-id="836e8-115">如果面向 HoloLens 2，则需要切换到以下通用 Windows 平台：</span><span class="sxs-lookup"><span data-stu-id="836e8-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="836e8-116">选择 **"文件>生成设置..."**</span><span class="sxs-lookup"><span data-stu-id="836e8-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="836e8-117">在 **通用 Windows 平台** 列表中选择"交换平台 **"，然后选择"切换平台"**</span><span class="sxs-lookup"><span data-stu-id="836e8-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="836e8-118">将“体系结构”设置为“ARM 64” </span><span class="sxs-lookup"><span data-stu-id="836e8-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="836e8-119">将“目标设备”设置为“HoloLens” </span><span class="sxs-lookup"><span data-stu-id="836e8-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="836e8-120">将“生成类型”设置为“D3D” </span><span class="sxs-lookup"><span data-stu-id="836e8-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="836e8-121">将“UWP SDK”设置为“最近安装的版本” </span><span class="sxs-lookup"><span data-stu-id="836e8-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="836e8-122">将“生成配置”设置为“发布”，因为调试存在已知的性能问题 </span><span class="sxs-lookup"><span data-stu-id="836e8-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Unity 编辑器中打开的"生成设置"窗口的屏幕截图，其中通用 Windows 平台突出显示](images/wmr-config-img-4.png)

<span data-ttu-id="836e8-124">设置平台后，需要让 Unity 知道在导出时创建[](../../design/app-views.md)沉浸式视图而不是 2D 视图。</span><span class="sxs-lookup"><span data-stu-id="836e8-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="836e8-125">对于 XRSDK</span><span class="sxs-lookup"><span data-stu-id="836e8-125">For XRSDK</span></span> 

1. <span data-ttu-id="836e8-126">在 Unity 编辑器中，导航到"编辑 **>项目设置"，然后选择\*\*\*\*"XR 插件管理"**</span><span class="sxs-lookup"><span data-stu-id="836e8-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="836e8-127">选择 **"安装 XR 插件管理"**</span><span class="sxs-lookup"><span data-stu-id="836e8-127">Select **Install XR Plugin Management**</span></span>

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-5.png)

3. <span data-ttu-id="836e8-129">选择 **"启动时初始化 XR"，\*\*\*\*然后选择Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="836e8-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-7.png)

4. <span data-ttu-id="836e8-131">展开 **"XR 插件管理"部分，** 然后选择 **"Univeral Windows 平台设置"** 选项卡</span><span class="sxs-lookup"><span data-stu-id="836e8-131">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="836e8-132">如果使用的是 Unity 2020 或更高版本，则会看到用于检查 **OpenXR** 或 **Windows Mixed Reality。**</span><span class="sxs-lookup"><span data-stu-id="836e8-132">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="836e8-133">可以选择任一运行时。</span><span class="sxs-lookup"><span data-stu-id="836e8-133">You can choose either runtime.</span></span>  <span data-ttu-id="836e8-134">如果你专门针对 HoloLens 2 或 HP Reverb G2 进行开发，并决定试用 **OpenXR，** 请选择 OpenXR 框，查看使用适用于 Unity 的混合现实 [OpenXR](openxr-getting-started.md) 插件指南，在返回到本教程之前，请正确设置这些设备</span><span class="sxs-lookup"><span data-stu-id="836e8-134">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="836e8-135">从 Unity 2020 LTS 开始，Microsoft 将采用 OpenXR 开发。</span><span class="sxs-lookup"><span data-stu-id="836e8-135">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="836e8-136">迁移到此路径时，在 Unity 2021.1 中，Windows XR 插件将在 2021.2 中弃用并删除，使 OpenXR 成为唯一受支持的路径。</span><span class="sxs-lookup"><span data-stu-id="836e8-136">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="836e8-137">有关详细信息，请参阅 [使用混合现实 OpenXR 插件](openxr-getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="836e8-137">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="836e8-138">如果决定选择"深度提交 **Windows Mixed Reality，** 请选中所有框，将"深度提交模式"设置为"深度 **16 位"**</span><span class="sxs-lookup"><span data-stu-id="836e8-138">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中Windows Mixed Reality部分](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="836e8-140">对于旧版 XR</span><span class="sxs-lookup"><span data-stu-id="836e8-140">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="836e8-141">旧版 XR 在 Unity 2019 中已弃用，在 Unity 2020 中已删除。</span><span class="sxs-lookup"><span data-stu-id="836e8-141">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="836e8-142">从 **"生成设置..."** 打开" **播放器设置..."。窗口** 并展开 **"XR 设置"** 组</span><span class="sxs-lookup"><span data-stu-id="836e8-142">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="836e8-143">在 **"XR 设置"** 部分中 **，选择"** 支持的虚拟现实"以添加"虚拟现实设备"列表</span><span class="sxs-lookup"><span data-stu-id="836e8-143">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="836e8-144">将 **深度格式设置为** **16 位深度** 并启用 **深度缓冲区共享**</span><span class="sxs-lookup"><span data-stu-id="836e8-144">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="836e8-145">将 **立体声渲染模式设置为\*\*\*\*单通道实例**</span><span class="sxs-lookup"><span data-stu-id="836e8-145">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="836e8-146">如果要 **使用全息远程处理** ，请选择"支持的 WSA 全息远程处理"</span><span class="sxs-lookup"><span data-stu-id="836e8-146">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中突出显示了"播放器设置"部分](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="836e8-148">更新清单</span><span class="sxs-lookup"><span data-stu-id="836e8-148">Updating the manifest</span></span>

<span data-ttu-id="836e8-149">应用现在可以处理全息渲染和空间输入。</span><span class="sxs-lookup"><span data-stu-id="836e8-149">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="836e8-150">但是，应用需要在其清单中声明相应的功能，以利用某些功能。</span><span class="sxs-lookup"><span data-stu-id="836e8-150">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="836e8-151">可以通过在"发布设置"和"功能"中>播放器通用 Windows 平台 > **设置>功能**。</span><span class="sxs-lookup"><span data-stu-id="836e8-151">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="836e8-152">建议在 Unity 中创建清单声明，以将其包括在导出的所有将来项目中。</span><span class="sxs-lookup"><span data-stu-id="836e8-152">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="836e8-153">为混合现实启用常用 Unity API 的适用功能包括：</span><span class="sxs-lookup"><span data-stu-id="836e8-153">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="836e8-154">功能</span><span class="sxs-lookup"><span data-stu-id="836e8-154">Capability</span></span>  |  <span data-ttu-id="836e8-155">需要该功能的 API</span><span class="sxs-lookup"><span data-stu-id="836e8-155">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="836e8-156">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="836e8-156">SpatialPerception</span></span>  |  <span data-ttu-id="836e8-157">SurfaceObserver (访问 HoloLens 上的空间映射网格) 头戴显示设备常规空间跟踪不需要 [](../../design/spatial-mapping.md) &mdash; *任何功能*</span><span class="sxs-lookup"><span data-stu-id="836e8-157">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="836e8-158">网络摄像头</span><span class="sxs-lookup"><span data-stu-id="836e8-158">WebCam</span></span>  |  <span data-ttu-id="836e8-159">PhotoCapture 和 VideoCapture</span><span class="sxs-lookup"><span data-stu-id="836e8-159">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="836e8-160">PicturesLibrary / VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="836e8-160">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="836e8-161">PhotoCapture 或 VideoCapture， (捕获的内容存储时分别) </span><span class="sxs-lookup"><span data-stu-id="836e8-161">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="836e8-162">麦克风</span><span class="sxs-lookup"><span data-stu-id="836e8-162">Microphone</span></span>  |  <span data-ttu-id="836e8-163">VideoCapture (捕获音频) 、听写Recognizer、GrammarRecognizer 和 KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="836e8-163">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="836e8-164">InternetClient</span><span class="sxs-lookup"><span data-stu-id="836e8-164">InternetClient</span></span>  |  <span data-ttu-id="836e8-165">DictationRecognizer (和 以使用 Unity Profiler) </span><span class="sxs-lookup"><span data-stu-id="836e8-165">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="836e8-166">质量设置</span><span class="sxs-lookup"><span data-stu-id="836e8-166">Quality settings</span></span>

<span data-ttu-id="836e8-167">HoloLens 具有移动类 GPU。</span><span class="sxs-lookup"><span data-stu-id="836e8-167">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="836e8-168">如果应用面向 HoloLens，则首先需要从应用中针对最快性能进行优化的质量设置开始，以确保它保持全帧速率。</span><span class="sxs-lookup"><span data-stu-id="836e8-168">If your app is targeting HoloLens, you'll want to start off with the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate.</span></span>  <span data-ttu-id="836e8-169">在开发中取得进一步进展后，可以考虑提高质量设置，以找到质量和性能之间的正确平衡：</span><span class="sxs-lookup"><span data-stu-id="836e8-169">Once you have your are further along in your development you may consider upping the quality settings to find the right balance of quality and performance:</span></span> 

1. <span data-ttu-id="836e8-170">选择 **"编辑>项目设置>质量"**</span><span class="sxs-lookup"><span data-stu-id="836e8-170">Select **Edit > Project Settings > Quality**</span></span> 
2. <span data-ttu-id="836e8-171">选择 Windows **应用商店徽标** **下的**   下拉列表，然后选择" **非常低"。**</span><span class="sxs-lookup"><span data-stu-id="836e8-171">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="836e8-172">当"Windows 应用商店"列中的框和"非常低"行为绿色时，你会知道设置已正确应用</span><span class="sxs-lookup"><span data-stu-id="836e8-172">You'll know the setting is applied correctly when the box in the Windows Store column and Very Low row is green</span></span> 
3. <span data-ttu-id="836e8-173">在" **阴影"**   部分中，选择" **禁用阴影"**</span><span class="sxs-lookup"><span data-stu-id="836e8-173">In the **Shadows** section, select **Disable Shadows**</span></span> 

<span data-ttu-id="836e8-174">![Unity 编辑器中打开的项目设置窗口的屏幕截图，其中突出显示了"质量设置"部分](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="836e8-174">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="836e8-175">*Unity 质量设置*</span><span class="sxs-lookup"><span data-stu-id="836e8-175">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="836e8-176">按场景设置</span><span class="sxs-lookup"><span data-stu-id="836e8-176">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="836e8-177">Unity 相机设置</span><span class="sxs-lookup"><span data-stu-id="836e8-177">Unity camera settings</span></span>

<span data-ttu-id="836e8-178">选中 **"支持虚拟现实** "后 [，Unity 相机](camera-in-unity.md) 组件将处理头部 [跟踪和立体声渲染](../platform-capabilities-and-apis/rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="836e8-178">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="836e8-179">这意味着，无需将主相机对象替换为自定义相机。</span><span class="sxs-lookup"><span data-stu-id="836e8-179">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="836e8-180">如果应用专门针对 HoloLens，则需要更改一些设置，以优化设备的透明显示。</span><span class="sxs-lookup"><span data-stu-id="836e8-180">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="836e8-181">这些设置允许全息内容向物理世界显示：</span><span class="sxs-lookup"><span data-stu-id="836e8-181">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="836e8-182">在" **层次结构"中**，选择 **"主相机"**</span><span class="sxs-lookup"><span data-stu-id="836e8-182">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="836e8-183">在 **"检查** 器"面板中，将转换位置设置为 **0、0、0，** 以便用户头部的位置从 Unity 世界原点开始。</span><span class="sxs-lookup"><span data-stu-id="836e8-183">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="836e8-184">将 **"清除标志"\*\*\*\*更改为"纯色"。**</span><span class="sxs-lookup"><span data-stu-id="836e8-184">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="836e8-185">将"**背景色"** 更改为 **"RGBA 0，0，0，0"。**</span><span class="sxs-lookup"><span data-stu-id="836e8-185">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="836e8-186">在 HoloLens 中，黑色呈现为透明。</span><span class="sxs-lookup"><span data-stu-id="836e8-186">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="836e8-187">更改 **裁剪平面 - 接近** [HoloLens 建议](camera-in-unity.md#using-clipping-planes) 0.85 (米) 。</span><span class="sxs-lookup"><span data-stu-id="836e8-187">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#using-clipping-planes) 0.85 (meters).</span></span>

<span data-ttu-id="836e8-188">![Unity 编辑器中打开的检查器选项卡的屏幕截图](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="836e8-188">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="836e8-189">*Unity 相机设置*</span><span class="sxs-lookup"><span data-stu-id="836e8-189">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="836e8-190">如果删除并创建新相机，请确保新相机标记为 **MainCamera**。</span><span class="sxs-lookup"><span data-stu-id="836e8-190">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="836e8-191">后续步骤</span><span class="sxs-lookup"><span data-stu-id="836e8-191">Next steps</span></span>

<span data-ttu-id="836e8-192">项目准备就绪后，可以开始开发混合现实体验：</span><span class="sxs-lookup"><span data-stu-id="836e8-192">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="836e8-193">添加 [核心构建基块](unity-development-overview.md#2-core-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="836e8-193">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="836e8-194">查看可用的 [平台功能和 API](unity-development-overview.md#3-advanced-features)</span><span class="sxs-lookup"><span data-stu-id="836e8-194">Check out available [platform capabilities and APIs](unity-development-overview.md#3-advanced-features)</span></span>
* <span data-ttu-id="836e8-195">了解如何 [部署应用](../platform-capabilities-and-apis/using-visual-studio.md#)</span><span class="sxs-lookup"><span data-stu-id="836e8-195">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#)</span></span>
* <span data-ttu-id="836e8-196">使用 [混合现实模拟器](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="836e8-196">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="836e8-197">另请参阅</span><span class="sxs-lookup"><span data-stu-id="836e8-197">See also</span></span>
* [<span data-ttu-id="836e8-198">安装工具</span><span class="sxs-lookup"><span data-stu-id="836e8-198">Install the tools</span></span>](../install-the-tools.md)