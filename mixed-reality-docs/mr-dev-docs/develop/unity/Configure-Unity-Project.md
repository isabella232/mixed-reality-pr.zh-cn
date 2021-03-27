---
title: 在不 MRTK 的情况下配置项目
description: 了解如何在没有混合现实工具包的情况下为 Windows Mixed Reality 配置新的 Unity 项目。
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity，混合现实，开发，入门，新项目，Windows Mixed Reality，UWP，XR，性能
ms.openlocfilehash: 5889a76941c36e24f600df5a459440d93bdd4c64
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636389"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="9e73d-104">配置项目时不使用 MRTK</span><span class="sxs-lookup"><span data-stu-id="9e73d-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="9e73d-105">Windows Mixed Reality (WMR) 是作为 Windows 10 操作系统的一部分引入的 Microsoft 平台。</span><span class="sxs-lookup"><span data-stu-id="9e73d-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="9e73d-106">WMR 平台使你能够生成在全息和 VR 显示设备上呈现数字内容的应用程序。</span><span class="sxs-lookup"><span data-stu-id="9e73d-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="9e73d-107">尽管 Microsoft 和社区创建了开源工具，例如 [混合现实工具包 (MRTK) ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 将自动设置 WMR 环境，但许多开发人员希望从根本上构建他们的经验。</span><span class="sxs-lookup"><span data-stu-id="9e73d-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="9e73d-108">如果你使用的是 MRTK，则以下文档将演示如何正确设置用于混合现实开发的项目。</span><span class="sxs-lookup"><span data-stu-id="9e73d-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="9e73d-109">需要更改的设置分为两类：每个项目的设置和每场景设置。</span><span class="sxs-lookup"><span data-stu-id="9e73d-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="9e73d-110">你始终可以在以后导入 MRTK，因此，不会产生要首先进行手动路由的损失。</span><span class="sxs-lookup"><span data-stu-id="9e73d-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="9e73d-111">如果选择 WMR 手动设置，则需要更改的设置将分为两个类别：每个项目和每场景。</span><span class="sxs-lookup"><span data-stu-id="9e73d-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="9e73d-112">每个项目的设置</span><span class="sxs-lookup"><span data-stu-id="9e73d-112">Per-project settings</span></span>

<span data-ttu-id="9e73d-113">如果面向的是 Desktop VR，建议使用默认情况下在新 Unity 项目上选择的 PC 独立平台：</span><span class="sxs-lookup"><span data-stu-id="9e73d-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![在 unity 编辑器中打开的 "生成设置" 窗口的屏幕截图，其中突出显示了 Mac & 独立平台](images/wmr-config-img-3.png)

<span data-ttu-id="9e73d-115">如果面向的是 HoloLens 2，则需要切换到通用 Windows 平台：</span><span class="sxs-lookup"><span data-stu-id="9e73d-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="9e73d-116">选择 **文件 > 生成设置 ...**</span><span class="sxs-lookup"><span data-stu-id="9e73d-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="9e73d-117">选择 "平台" 列表中的 "**通用 Windows 平台**"，然后选择 "**切换平台**"</span><span class="sxs-lookup"><span data-stu-id="9e73d-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="9e73d-118">将 **体系结构** 设置为 **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="9e73d-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="9e73d-119">将 **目标设备** 设置为 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="9e73d-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="9e73d-120">将 **生成类型** 设置为 **D3D**</span><span class="sxs-lookup"><span data-stu-id="9e73d-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="9e73d-121">将 **UWP SDK** 设置为 **安装的最新版本**</span><span class="sxs-lookup"><span data-stu-id="9e73d-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="9e73d-122">将 **生成配置** 设置为 **发布** ，因为调试存在已知的性能问题</span><span class="sxs-lookup"><span data-stu-id="9e73d-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![在 unity 编辑器中打开的生成设置窗口的屏幕截图，其中通用 Windows 平台突出显示](images/wmr-config-img-4.png)

<span data-ttu-id="9e73d-124">设置平台后，需要让 Unity 知道在导出后创建 [沉浸式视图](../../design/app-views.md) 而不是2d 视图。</span><span class="sxs-lookup"><span data-stu-id="9e73d-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="9e73d-125">对于 XRSDK</span><span class="sxs-lookup"><span data-stu-id="9e73d-125">For XRSDK</span></span> 

1. <span data-ttu-id="9e73d-126">在 Unity 编辑器中，导航到 "**编辑 > 项目设置**"，然后选择 " **XR 插件管理**"</span><span class="sxs-lookup"><span data-stu-id="9e73d-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="9e73d-127">选择 "**安装 XR 插件管理**"</span><span class="sxs-lookup"><span data-stu-id="9e73d-127">Select **Install XR Plugin Management**</span></span>

![在 unity 编辑器中打开的 "项目设置" 窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-5.png)

3. <span data-ttu-id="9e73d-129">选择 **"启动时初始化 XR" 和 "** **Windows Mixed Reality** "</span><span class="sxs-lookup"><span data-stu-id="9e73d-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![在 unity 编辑器中打开的 "项目设置" 窗口的屏幕截图，其中突出显示了 XR 插件管理](images/wmr-config-img-7.png)

4. <span data-ttu-id="9e73d-131">展开 " **XR 插件管理** " 部分，并选择 " **通用 Windows 平台设置** " 选项卡</span><span class="sxs-lookup"><span data-stu-id="9e73d-131">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="9e73d-132">如果使用的是 Unity 2020 或更高版本，则会看到用于检查 **OpenXR** 或 **Windows Mixed Reality** 的选项。</span><span class="sxs-lookup"><span data-stu-id="9e73d-132">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="9e73d-133">您可以选择 "运行时"。</span><span class="sxs-lookup"><span data-stu-id="9e73d-133">You can choose either runtime.</span></span>  <span data-ttu-id="9e73d-134">如果你要专门针对 HoloLens 2 或 HP 回音 G2 进行开发，并决定尝试 **OpenXR**，请选择 "OpenXR" 框，并查看本指南，以 [了解如何使用适用于 Unity 的 Mixed Reality OpenXR 插件](openxr-getting-started.md) 为这些设备正确设置，然后再返回到本教程</span><span class="sxs-lookup"><span data-stu-id="9e73d-134">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="9e73d-135">从 Unity 2020 LTS 开始，Microsoft 正在接纳 OpenXR 的开发。</span><span class="sxs-lookup"><span data-stu-id="9e73d-135">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="9e73d-136">随着我们迁移到此路径，在 Unity 2021.1 中，Windows XR 插件将被弃用并在2021.2 中删除，从而使 OpenXR 成为唯一支持的路径。</span><span class="sxs-lookup"><span data-stu-id="9e73d-136">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="9e73d-137">可以在 [使用混合现实 OpenXR 插件](openxr-getting-started.md)中找到详细信息。</span><span class="sxs-lookup"><span data-stu-id="9e73d-137">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="9e73d-138">如果决定选择 **Windows Mixed Reality** 插件，请选中所有复选框，并将 **深度提交模式** 设置为 **深度16位**</span><span class="sxs-lookup"><span data-stu-id="9e73d-138">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![突出显示了 Windows Mixed Reality 部分的 "项目设置" 窗口的屏幕截图已在 unity 编辑器中打开](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="9e73d-140">对于旧版 XR</span><span class="sxs-lookup"><span data-stu-id="9e73d-140">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="9e73d-141">旧版 XR 在 Unity 2019 中已弃用，并已在 Unity 2020 中删除。</span><span class="sxs-lookup"><span data-stu-id="9e73d-141">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="9e73d-142">从生成设置中打开 **播放机设置** ... **窗口** 并展开 **XR 设置** 组</span><span class="sxs-lookup"><span data-stu-id="9e73d-142">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="9e73d-143">在 " **XR 设置** " 部分中，选择 " **支持的虚拟现实** " 以添加虚拟现实设备列表</span><span class="sxs-lookup"><span data-stu-id="9e73d-143">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="9e73d-144">将 **深度格式** 设置为 **16 位深度** 并启用 **深度缓冲共享**</span><span class="sxs-lookup"><span data-stu-id="9e73d-144">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="9e73d-145">将 **立体声渲染模式** 设置为 **单一传递实例**</span><span class="sxs-lookup"><span data-stu-id="9e73d-145">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="9e73d-146">如果要使用全息远程处理，请选择 " **支持 WSA 全息远程处理** "</span><span class="sxs-lookup"><span data-stu-id="9e73d-146">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![突出显示了 "播放机设置" 部分的 "项目设置" 窗口的屏幕截图](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="9e73d-148">更新清单</span><span class="sxs-lookup"><span data-stu-id="9e73d-148">Updating the manifest</span></span>

<span data-ttu-id="9e73d-149">您的应用程序现在可以处理全息呈现和空间输入。</span><span class="sxs-lookup"><span data-stu-id="9e73d-149">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="9e73d-150">但是，你的应用程序需要在其清单中声明相应的功能，才能利用某些功能。</span><span class="sxs-lookup"><span data-stu-id="9e73d-150">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="9e73d-151">可以通过转到 " **播放机设置" > "通用 Windows 平台 >" 发布设置 "> 功能**，找到项目功能。</span><span class="sxs-lookup"><span data-stu-id="9e73d-151">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="9e73d-152">建议在 Unity 中创建清单声明，以将其包含在所有以后导出的项目中。</span><span class="sxs-lookup"><span data-stu-id="9e73d-152">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="9e73d-153">为混合现实启用常用 Unity Api 的适用功能包括：</span><span class="sxs-lookup"><span data-stu-id="9e73d-153">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="9e73d-154">功能</span><span class="sxs-lookup"><span data-stu-id="9e73d-154">Capability</span></span>  |  <span data-ttu-id="9e73d-155">需要功能的 Api</span><span class="sxs-lookup"><span data-stu-id="9e73d-155">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="9e73d-156">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="9e73d-156">SpatialPerception</span></span>  |  <span data-ttu-id="9e73d-157">SurfaceObserver (访问 HoloLens 上的 [空间映射](../../design/spatial-mapping.md)网格) &mdash; *无需对耳机进行常规空间跟踪*</span><span class="sxs-lookup"><span data-stu-id="9e73d-157">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="9e73d-158">网络摄像头</span><span class="sxs-lookup"><span data-stu-id="9e73d-158">WebCam</span></span>  |  <span data-ttu-id="9e73d-159">PhotoCapture 和 VideoCapture</span><span class="sxs-lookup"><span data-stu-id="9e73d-159">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="9e73d-160">PicturesLibrary/VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="9e73d-160">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="9e73d-161">PhotoCapture 或 VideoCapture，分别 (存储捕获的内容) </span><span class="sxs-lookup"><span data-stu-id="9e73d-161">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="9e73d-162">麦克风</span><span class="sxs-lookup"><span data-stu-id="9e73d-162">Microphone</span></span>  |  <span data-ttu-id="9e73d-163">捕获音频) 、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer 时的 VideoCapture (</span><span class="sxs-lookup"><span data-stu-id="9e73d-163">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="9e73d-164">InternetClient</span><span class="sxs-lookup"><span data-stu-id="9e73d-164">InternetClient</span></span>  |  <span data-ttu-id="9e73d-165">DictationRecognizer (并使用 Unity 探查器) </span><span class="sxs-lookup"><span data-stu-id="9e73d-165">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="9e73d-166">质量设置</span><span class="sxs-lookup"><span data-stu-id="9e73d-166">Quality settings</span></span>

<span data-ttu-id="9e73d-167">HoloLens 具有移动类 GPU。</span><span class="sxs-lookup"><span data-stu-id="9e73d-167">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="9e73d-168">如果你的应用面向 HoloLens，你需要先将应用中的质量设置调整为最快的性能，以确保它保持完整的帧速率。</span><span class="sxs-lookup"><span data-stu-id="9e73d-168">If your app is targeting HoloLens, you'll want to start off with the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate.</span></span>  <span data-ttu-id="9e73d-169">在开发中进一步发展之后，可以考虑 upping 质量设置，以找出适当的质量和性能平衡：</span><span class="sxs-lookup"><span data-stu-id="9e73d-169">Once you have your are further along in your development you may consider upping the quality settings to find the right balance of quality and performance:</span></span> 

1. <span data-ttu-id="9e73d-170">选择 " **编辑 > 项目设置 > 质量**"</span><span class="sxs-lookup"><span data-stu-id="9e73d-170">Select **Edit > Project Settings > Quality**</span></span> 
2. <span data-ttu-id="9e73d-171">选择  **Windows 应用商店** 徽标下的 **下拉列表**   ，并选择 " **非常低**"。</span><span class="sxs-lookup"><span data-stu-id="9e73d-171">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="9e73d-172">如果 Windows 应用商店列和极低的行中的框为绿色，将知道设置正确应用</span><span class="sxs-lookup"><span data-stu-id="9e73d-172">You'll know the setting is applied correctly when the box in the Windows Store column and Very Low row is green</span></span> 
3. <span data-ttu-id="9e73d-173">在 **阴影**   部分，选择 " **禁用阴影**"</span><span class="sxs-lookup"><span data-stu-id="9e73d-173">In the **Shadows** section, select **Disable Shadows**</span></span> 

<span data-ttu-id="9e73d-174">![突出显示了 "质量设置" 部分的 "项目设置" 窗口的屏幕截图](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="9e73d-174">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="9e73d-175">*Unity 质量设置*</span><span class="sxs-lookup"><span data-stu-id="9e73d-175">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="9e73d-176">每场景设置</span><span class="sxs-lookup"><span data-stu-id="9e73d-176">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="9e73d-177">Unity 照相机设置</span><span class="sxs-lookup"><span data-stu-id="9e73d-177">Unity camera settings</span></span>

<span data-ttu-id="9e73d-178">如果选中 " **支持虚拟现实** "，则 [Unity 相机](camera-in-unity.md) 组件会处理 [头跟踪和 stereoscopic 呈现](../platform-capabilities-and-apis/rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="9e73d-178">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="9e73d-179">这意味着不需要使用自定义相机替换主相机对象。</span><span class="sxs-lookup"><span data-stu-id="9e73d-179">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="9e73d-180">如果你的应用程序专门面向 HoloLens，则需要更改一些设置以优化设备的透明显示。</span><span class="sxs-lookup"><span data-stu-id="9e73d-180">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="9e73d-181">这些设置允许你的全息内容透过物理环境显示：</span><span class="sxs-lookup"><span data-stu-id="9e73d-181">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="9e73d-182">在 **层次结构** 中，选择 **主相机**</span><span class="sxs-lookup"><span data-stu-id="9e73d-182">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="9e73d-183">在 " **检查器** " 面板中，将转换 **位置** 设置为 **0，0，0，** 以使用户头部的位置从 Unity 世界原点开始。</span><span class="sxs-lookup"><span data-stu-id="9e73d-183">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="9e73d-184">将 **清除标志** 更改为 **纯色**。</span><span class="sxs-lookup"><span data-stu-id="9e73d-184">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="9e73d-185">将 **背景** 色更改为 **RGBA 0，0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="9e73d-185">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="9e73d-186">在 HoloLens 中，黑色呈现为透明。</span><span class="sxs-lookup"><span data-stu-id="9e73d-186">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="9e73d-187">更改 **剪辑平面-接近** 于 [HoloLens 建议](camera-in-unity.md#using-clipping-planes) 0.85 (米) 。</span><span class="sxs-lookup"><span data-stu-id="9e73d-187">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#using-clipping-planes) 0.85 (meters).</span></span>

<span data-ttu-id="9e73d-188">![在 Unity 编辑器中打开的 "检查器" 选项卡的屏幕截图](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="9e73d-188">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="9e73d-189">*Unity 照相机设置*</span><span class="sxs-lookup"><span data-stu-id="9e73d-189">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9e73d-190">如果删除并创建新相机，请确保将新相机标记为 " **MainCamera**"。</span><span class="sxs-lookup"><span data-stu-id="9e73d-190">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9e73d-191">后续步骤</span><span class="sxs-lookup"><span data-stu-id="9e73d-191">Next steps</span></span>

<span data-ttu-id="9e73d-192">现在，你的项目已准备就绪，可以开始开发混合现实体验：</span><span class="sxs-lookup"><span data-stu-id="9e73d-192">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="9e73d-193">添加 [核心构建基块](unity-development-overview.md#2-core-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="9e73d-193">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="9e73d-194">查看可用 [的平台功能和 api](unity-development-overview.md#3-advanced-features)</span><span class="sxs-lookup"><span data-stu-id="9e73d-194">Check out available [platform capabilities and APIs](unity-development-overview.md#3-advanced-features)</span></span>
* <span data-ttu-id="9e73d-195">了解如何 [部署应用](../platform-capabilities-and-apis/using-visual-studio.md#)</span><span class="sxs-lookup"><span data-stu-id="9e73d-195">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#)</span></span>
* <span data-ttu-id="9e73d-196">使用 [混合现实模拟器](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="9e73d-196">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="9e73d-197">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9e73d-197">See also</span></span>
* [<span data-ttu-id="9e73d-198">安装工具</span><span class="sxs-lookup"><span data-stu-id="9e73d-198">Install the tools</span></span>](../install-the-tools.md)