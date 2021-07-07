---
title: MRTK-Unity 开发人员文档
description: 了解适用于 Unity 的混合现实工具包。
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK
ms.openlocfilehash: cf2aa536087af659abe7d124a4dd35ff0175de49
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177366"
---
# <a name="what-is-the-mixed-reality-toolkit"></a><span data-ttu-id="8d142-104">混合现实工具包指的是什么</span><span class="sxs-lookup"><span data-stu-id="8d142-104">What is the Mixed Reality Toolkit</span></span>

![混合现实工具包](features/images/Logo_MRTK_Unity_Banner.png)

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyXHW]

<span data-ttu-id="8d142-106">MRTK-Unity 是由 Microsoft 驱动的项目，它提供了一系列组件和功能来加速 Unity 中的跨平台 MR 应用开发。</span><span class="sxs-lookup"><span data-stu-id="8d142-106">MRTK-Unity is a Microsoft-driven project that provides a set of components and features, used to accelerate cross-platform MR app development in Unity.</span></span> <span data-ttu-id="8d142-107">以下是它的一些功能：</span><span class="sxs-lookup"><span data-stu-id="8d142-107">Here are some of its functions:</span></span>

* <span data-ttu-id="8d142-108">为空间交互和 UI 提供跨平台输入系统和构建基块。</span><span class="sxs-lookup"><span data-stu-id="8d142-108">Provides the **cross-platform input system and building blocks for spatial interactions and UI**.</span></span>
* <span data-ttu-id="8d142-109">通过编辑器内模拟实现快速原型制作，让你能够立即看到变化。</span><span class="sxs-lookup"><span data-stu-id="8d142-109">Enables **rapid prototyping** via in-editor simulation that allows you to see changes immediately.</span></span>
* <span data-ttu-id="8d142-110">作为可扩展的框架运行，使开发人员能够交换出核心组件。</span><span class="sxs-lookup"><span data-stu-id="8d142-110">Operates as an **extensible framework** that provides developers the ability to swap out core components.</span></span>
* <span data-ttu-id="8d142-111">支持一系列广泛的平台：</span><span class="sxs-lookup"><span data-stu-id="8d142-111">**Supports a wide range of platforms**:</span></span>

::: moniker range=">= mrtkunity-2021-05"
| <span data-ttu-id="8d142-112">平台</span><span class="sxs-lookup"><span data-stu-id="8d142-112">Platform</span></span> | <span data-ttu-id="8d142-113">支持的设备</span><span class="sxs-lookup"><span data-stu-id="8d142-113">Supported Devices</span></span> |
|---|---|
| <span data-ttu-id="8d142-114">OpenXR (Unity 2020.3.8+)</span><span class="sxs-lookup"><span data-stu-id="8d142-114">OpenXR (Unity 2020.3.8+)</span></span> | <span data-ttu-id="8d142-115">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8d142-115">Microsoft HoloLens 2</span></span> <br> <span data-ttu-id="8d142-116">Windows Mixed Reality 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="8d142-116">Windows Mixed Reality headsets</span></span> |
| <span data-ttu-id="8d142-117">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8d142-117">Windows Mixed Reality</span></span> | <span data-ttu-id="8d142-118">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="8d142-118">Microsoft HoloLens</span></span> <br> <span data-ttu-id="8d142-119">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8d142-119">Microsoft HoloLens 2</span></span> <br> <span data-ttu-id="8d142-120">Windows Mixed Reality 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="8d142-120">Windows Mixed Reality headsets</span></span>  |
| <span data-ttu-id="8d142-121">Oculus（Unity 2019.3 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="8d142-121">Oculus (Unity 2019.3 or newer)</span></span> | <span data-ttu-id="8d142-122">Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="8d142-122">Oculus Quest</span></span> |
| <span data-ttu-id="8d142-123">OpenVR</span><span class="sxs-lookup"><span data-stu-id="8d142-123">OpenVR</span></span> |  <span data-ttu-id="8d142-124">Windows Mixed Reality 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="8d142-124">Windows Mixed Reality headsets</span></span> <br> <span data-ttu-id="8d142-125">HTC Vive</span><span class="sxs-lookup"><span data-stu-id="8d142-125">HTC Vive</span></span> <br> <span data-ttu-id="8d142-126">Oculus Rift</span><span class="sxs-lookup"><span data-stu-id="8d142-126">Oculus Rift</span></span> |
| <span data-ttu-id="8d142-127">Ultraleap 手部跟踪</span><span class="sxs-lookup"><span data-stu-id="8d142-127">Ultraleap Hand Tracking</span></span> | <span data-ttu-id="8d142-128">Ultraleap Leap 运动控制器</span><span class="sxs-lookup"><span data-stu-id="8d142-128">Ultraleap Leap Motion controller</span></span> |
| <span data-ttu-id="8d142-129">移动型</span><span class="sxs-lookup"><span data-stu-id="8d142-129">Mobile</span></span> | <span data-ttu-id="8d142-130">iOS 和 Android</span><span class="sxs-lookup"><span data-stu-id="8d142-130">iOS and Android</span></span> |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| <span data-ttu-id="8d142-131">平台</span><span class="sxs-lookup"><span data-stu-id="8d142-131">Platform</span></span> | <span data-ttu-id="8d142-132">支持的设备</span><span class="sxs-lookup"><span data-stu-id="8d142-132">Supported Devices</span></span> |
|---|---|
| <span data-ttu-id="8d142-133">OpenXR（在 MRTK 2.6、Unity 2020.3.8+ 中为预览版）</span><span class="sxs-lookup"><span data-stu-id="8d142-133">OpenXR (Preview in MRTK 2.6, Unity 2020.3.8+)</span></span> | <span data-ttu-id="8d142-134">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8d142-134">Microsoft HoloLens 2</span></span> <br> <span data-ttu-id="8d142-135">Windows Mixed Reality 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="8d142-135">Windows Mixed Reality headsets</span></span> |
| <span data-ttu-id="8d142-136">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8d142-136">Windows Mixed Reality</span></span> | <span data-ttu-id="8d142-137">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="8d142-137">Microsoft HoloLens</span></span> <br> <span data-ttu-id="8d142-138">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8d142-138">Microsoft HoloLens 2</span></span> <br> <span data-ttu-id="8d142-139">Windows Mixed Reality 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="8d142-139">Windows Mixed Reality headsets</span></span>  |
| <span data-ttu-id="8d142-140">Oculus（Unity 2019.3 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="8d142-140">Oculus (Unity 2019.3 or newer)</span></span> | <span data-ttu-id="8d142-141">Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="8d142-141">Oculus Quest</span></span> |
| <span data-ttu-id="8d142-142">OpenVR</span><span class="sxs-lookup"><span data-stu-id="8d142-142">OpenVR</span></span> |  <span data-ttu-id="8d142-143">Windows Mixed Reality 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="8d142-143">Windows Mixed Reality headsets</span></span> <br> <span data-ttu-id="8d142-144">HTC Vive</span><span class="sxs-lookup"><span data-stu-id="8d142-144">HTC Vive</span></span> <br> <span data-ttu-id="8d142-145">Oculus Rift</span><span class="sxs-lookup"><span data-stu-id="8d142-145">Oculus Rift</span></span> |
| <span data-ttu-id="8d142-146">Ultraleap 手部跟踪</span><span class="sxs-lookup"><span data-stu-id="8d142-146">Ultraleap Hand Tracking</span></span> | <span data-ttu-id="8d142-147">Ultraleap Leap 运动控制器</span><span class="sxs-lookup"><span data-stu-id="8d142-147">Ultraleap Leap Motion controller</span></span> |
| <span data-ttu-id="8d142-148">移动型</span><span class="sxs-lookup"><span data-stu-id="8d142-148">Mobile</span></span> | <span data-ttu-id="8d142-149">iOS 和 Android</span><span class="sxs-lookup"><span data-stu-id="8d142-149">iOS and Android</span></span> |
::: moniker-end

## <a name="getting-started-with-mrtk"></a><span data-ttu-id="8d142-150">MRTK 入门</span><span class="sxs-lookup"><span data-stu-id="8d142-150">Getting started with MRTK</span></span>

<span data-ttu-id="8d142-151">如果你不熟悉 Unity 中的 MRTK 或混合现实开发，建议在设备或[模拟器](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)上安装并浏览 MRTK 示例中心示例应用程序。</span><span class="sxs-lookup"><span data-stu-id="8d142-151">If you're new to MRTK or Mixed Reality development in Unity, we recommend installing and exploring the MRTK Examples Hub sample application on your device or [emulator](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator).</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="8d142-152">下载 MRTK 示例中心应用</span><span class="sxs-lookup"><span data-stu-id="8d142-152">Download the MRTK Examples Hub app</span></span>](running-examples-hub.md)

<span data-ttu-id="8d142-153">在熟悉混合现实和 MRTK 的内容后，请安装所需的工具，并遵循初级级别 HoloLens 2 教程系列操作。</span><span class="sxs-lookup"><span data-stu-id="8d142-153">Once you've got the hang of what Mixed Reality and MRTK has to offer, install the necessary tools and follow our beginner level HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8d142-154">安装工具</span><span class="sxs-lookup"><span data-stu-id="8d142-154">Install the tools</span></span>](/windows/mixed-reality/develop/install-the-tools?tabs=unity)

> [!div class="nextstepaction"]
> [<span data-ttu-id="8d142-155">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="8d142-155">HoloLens 2 Tutorial Series</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

<span data-ttu-id="8d142-156">想要查看后台正在执行的情况？</span><span class="sxs-lookup"><span data-stu-id="8d142-156">Want to see what's going on under the hood?</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="8d142-157">在 GitHub 上了解 MRTK</span><span class="sxs-lookup"><span data-stu-id="8d142-157">Explore MRTK on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a><span data-ttu-id="8d142-158">文档</span><span class="sxs-lookup"><span data-stu-id="8d142-158">Documentation</span></span>

| <span data-ttu-id="8d142-159">[![发行说明](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-27-release-notes.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-159">[![Release notes](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-27-release-notes.md)</span></span><br/>[<span data-ttu-id="8d142-160">发行说明</span><span class="sxs-lookup"><span data-stu-id="8d142-160">Release Notes</span></span>](release-notes/mrtk-26-release-notes.md)| <span data-ttu-id="8d142-161">[![MRTK 概述](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-161">[![MRTK Overview](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span></span><br/>[<span data-ttu-id="8d142-162">MRTK 概述</span><span class="sxs-lookup"><span data-stu-id="8d142-162">MRTK Overview</span></span>](architecture/overview.md)|<span data-ttu-id="8d142-163">[![API 参考](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span><span class="sxs-lookup"><span data-stu-id="8d142-163">[![API Reference](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span></span><br/>[<span data-ttu-id="8d142-164">API 参考</span><span class="sxs-lookup"><span data-stu-id="8d142-164">API Reference</span></span>](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a><span data-ttu-id="8d142-165">生成状态</span><span class="sxs-lookup"><span data-stu-id="8d142-165">Build status</span></span>

| <span data-ttu-id="8d142-166">分支</span><span class="sxs-lookup"><span data-stu-id="8d142-166">Branch</span></span> | <span data-ttu-id="8d142-167">CI 状态</span><span class="sxs-lookup"><span data-stu-id="8d142-167">CI Status</span></span> | <span data-ttu-id="8d142-168">文档状态</span><span class="sxs-lookup"><span data-stu-id="8d142-168">Docs Status</span></span> |
|---|---|---|
| `main` |<span data-ttu-id="8d142-169">[![CI 状态](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span><span class="sxs-lookup"><span data-stu-id="8d142-169">[![CI Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span></span>|<span data-ttu-id="8d142-170">[![文档状态](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span><span class="sxs-lookup"><span data-stu-id="8d142-170">[![Docs Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span></span>

## <a name="feature-areas"></a><span data-ttu-id="8d142-171">功能区域</span><span class="sxs-lookup"><span data-stu-id="8d142-171">Feature areas</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="8d142-172">[![输入系统](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-172">[![Input System](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="8d142-173">**[输入系统](features/input/overview.md)**</span><span class="sxs-lookup"><span data-stu-id="8d142-173">**[Input System](features/input/overview.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-174">[![手部跟踪 (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-174">[![Hand Tracking (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="8d142-175">**[手部跟踪 <br> (HoloLens 2)](features/input/hand-tracking.md)**</span><span class="sxs-lookup"><span data-stu-id="8d142-175">**[Hand Tracking <br> (HoloLens 2)](features/input/hand-tracking.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-176">[![眼动跟踪 (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-176">[![Eye Tracking (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span></span><br>
        <span data-ttu-id="8d142-177">**[眼动跟踪 <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span><span class="sxs-lookup"><span data-stu-id="8d142-177">**[Eye Tracking <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-178">[![配置文件](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-178">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span></span><br>
        <span data-ttu-id="8d142-179">**[配置文件](configuration/mixed-reality-configuration-guide.md)**</span><span class="sxs-lookup"><span data-stu-id="8d142-179">**[Profiles](configuration/mixed-reality-configuration-guide.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="8d142-180">[![手部跟踪 (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](supported-devices/leap-motion-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-180">[![Hand Tracking (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](supported-devices/leap-motion-mrtk.md)</span></span><br>
        <span data-ttu-id="8d142-181">**[手部跟踪 <br/> (Ultraleap)](supported-devices/leap-motion-mrtk.md)**</span><span class="sxs-lookup"><span data-stu-id="8d142-181">**[Hand Tracking <br/> (Ultraleap)](supported-devices/leap-motion-mrtk.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-182">[![UI 控件](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="8d142-182">[![UI Controls](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span></span><br>
        <span data-ttu-id="8d142-183">**[UI 控件](#ux-building-blocks)**</span><span class="sxs-lookup"><span data-stu-id="8d142-183">**[UI Controls](#ux-building-blocks)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-184">[![求解器](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-184">[![Solvers](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span></span><br>
        <span data-ttu-id="8d142-185">**[求解器](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="8d142-185">**[Solvers](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-186">[![多场景管理器](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-186">[![Multi-Scene Manager](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="8d142-187">**[多场景<br/>管理器](features/scene-system/scene-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="8d142-187">**[Multi-Scene<br/> Manager](features/scene-system/scene-system-getting-started.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="8d142-188">[![空间感知](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-188">[![Spatial Awareness](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span></span><br>
        <span data-ttu-id="8d142-189">**[空间<br/>感知](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="8d142-189">**[Spatial <br/> Awareness](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-190">[![诊断工具](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-190">[![Diagnostic Tool](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="8d142-191">**[诊断<br/>工具](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="8d142-191">**[Diagnostic <br/> Tool](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-192">[![MRTK 标准着色器视图](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span><span class="sxs-lookup"><span data-stu-id="8d142-192">[![MRTK Standard Shader View](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span></span><br>
        <span data-ttu-id="8d142-193">**[MRTK 标准着色器示例视图](features/rendering/mrtk-standard-shader.md?q=shader)**</span><span class="sxs-lookup"><span data-stu-id="8d142-193">**[MRTK Standard Shader Example View](features/rendering/mrtk-standard-shader.md?q=shader)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-194">[![语音与听写](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-194">[![Speech & Dictation](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="8d142-195">**[语音](features/input/speech.md)<br/> & [听写](features/input/dictation.md)**</span><span class="sxs-lookup"><span data-stu-id="8d142-195">**[Speech](features/input/speech.md)<br/> & [Dictation](features/input/dictation.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="8d142-196">[![边界系统](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-196">[![Boundary System](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span></span><br>
        <span data-ttu-id="8d142-197">**[边界<br/>系统](features/boundary/boundary-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="8d142-197">**[Boundary <br/>System](features/boundary/boundary-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-198">[![编辑器内模拟](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-198">[![In-Editor Simulation](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="8d142-199">**[编辑器内<br/>模拟](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="8d142-199">**[In-Editor <br/> Simulation](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-200">[![实验性功能](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-200">[![Experimental Features](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span></span><br>
        <span data-ttu-id="8d142-201">**[实验性<br/>功能](contributing/experimental-features.md)**</span><span class="sxs-lookup"><span data-stu-id="8d142-201">**[Experimental <br/> Features](contributing/experimental-features.md)**</span></span><br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a><span data-ttu-id="8d142-202">UX 构建基块</span><span class="sxs-lookup"><span data-stu-id="8d142-202">UX building blocks</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="8d142-203">[![按钮](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) [按钮](features/ux-building-blocks/button.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-203">[![Button](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Button](features/ux-building-blocks/button.md)**</span></span><br>
        <span data-ttu-id="8d142-204">一种支持各种输入方法（包括 HoloLens 2 关节式手部）的按钮控件</span><span class="sxs-lookup"><span data-stu-id="8d142-204">A button control which supports various input methods, including HoloLens 2's articulated hand</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-205">[![边界控制](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) [边界控制](features/ux-building-blocks/bounds-control.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-205">[![Bounds Control](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Bounds Control](features/ux-building-blocks/bounds-control.md)**</span></span><br>
        <span data-ttu-id="8d142-206">用于模拟 3D 空间中的对象的标准 UI</span><span class="sxs-lookup"><span data-stu-id="8d142-206">Standard UI for manipulating objects in 3D space</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-207">[![对象操控器](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) [对象操控器](features/ux-building-blocks/object-manipulator.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-207">[![Object Manipulator](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Object Manipulator](features/ux-building-blocks/object-manipulator.md)**</span></span><br>
        <span data-ttu-id="8d142-208">用于通过单手或双手操控对象的脚本</span><span class="sxs-lookup"><span data-stu-id="8d142-208">Script for manipulating objects with one or two hands</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="8d142-209">[![场记板](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) [场记板](features/ux-building-blocks/slate.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-209">[![Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**</span></span><br>
        <span data-ttu-id="8d142-210">支持通过关节式手部输入进行滚动的 2D 样式平面</span><span class="sxs-lookup"><span data-stu-id="8d142-210">2D style plane which supports scrolling with articulated hand input</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-211">[![系统键盘](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) [系统键盘](features/ux-building-blocks/system-keyboard.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-211">[![System Keyboard](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[System Keyboard](features/ux-building-blocks/system-keyboard.md)**</span></span><br>
        <span data-ttu-id="8d142-212">用于在 Unity 中使用系统键盘的示例脚本</span><span class="sxs-lookup"><span data-stu-id="8d142-212">Example script of using the system keyboard in Unity</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-213">[![可交互](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) [可交互](features/ux-building-blocks/interactable.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-213">[![Interactable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactable](features/ux-building-blocks/interactable.md)**</span></span><br>
        <span data-ttu-id="8d142-214">用于使对象可与可视状态和主题支持进行交互的脚本</span><span class="sxs-lookup"><span data-stu-id="8d142-214">A script for making objects interactable with visual states and theme support</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="8d142-215">[![求解器](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) [求解器](features/ux-building-blocks/solvers/solver.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-215">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
        <span data-ttu-id="8d142-216">各种对象定位行为，例如尾随、跟随人体、常量视图大小和表面磁性</span><span class="sxs-lookup"><span data-stu-id="8d142-216">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-217">[![对象集合](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) [对象集合](features/ux-building-blocks/object-collection.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-217">[![Object Collection](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Object Collection](features/ux-building-blocks/object-collection.md)**</span></span><br>
        <span data-ttu-id="8d142-218">用于在三维形状中布设一组对象的脚本</span><span class="sxs-lookup"><span data-stu-id="8d142-218">Script for laying out an array of objects in a three-dimensional shape</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-219">[![工具提示](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) [工具提示](features/ux-building-blocks/tooltip.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-219">[![Tooltip](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Tooltip](features/ux-building-blocks/tooltip.md)**</span></span><br>
        <span data-ttu-id="8d142-220">具有灵活定位点/透视系统的注释 UI，可用于标记运动控制器和对象</span><span class="sxs-lookup"><span data-stu-id="8d142-220">Annotation UI with a flexible anchor/pivot system, which can be used for labeling motion controllers and objects</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="8d142-221">[![滑块](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) [滑块](features/ux-building-blocks/sliders.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-221">[![Slider](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Slider](features/ux-building-blocks/sliders.md)**</span></span><br>
        <span data-ttu-id="8d142-222">用于调整支持直接手部跟踪交互的值的滑块 UI</span><span class="sxs-lookup"><span data-stu-id="8d142-222">Slider UI for adjusting values supporting direct hand tracking interaction</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-223">[![MRTK 标准着色器](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) [MRTK 标准着色器](features/rendering/mrtk-standard-shader.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-223">[![MRTK Standard Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK Standard Shader](features/rendering/mrtk-standard-shader.md)**</span></span><br>
        <span data-ttu-id="8d142-224">MRTK 的标准着色器支持各种 Fluent 设计元素并提供高性能</span><span class="sxs-lookup"><span data-stu-id="8d142-224">MRTK's Standard shader supports various Fluent design elements with performance</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-225">[![手动菜单](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) [手动菜单](features/ux-building-blocks/hand-menu.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-225">[![Hand Menu](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Hand Menu](features/ux-building-blocks/hand-menu.md)**</span></span><br>
        <span data-ttu-id="8d142-226">使用手部约束求解器实现快速访问的手部锁定 UI</span><span class="sxs-lookup"><span data-stu-id="8d142-226">Hand-locked UI for quick access, using the Hand Constraint Solver</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="8d142-227">[![应用栏](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) [应用栏](features/ux-building-blocks/app-bar.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-227">[![App Bar](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[App Bar](features/ux-building-blocks/app-bar.md)**</span></span><br>
        <span data-ttu-id="8d142-228">用于边界控制的手动激活的 UI</span><span class="sxs-lookup"><span data-stu-id="8d142-228">UI for Bounds Control's manual activation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-229">[![指针](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[指针](features/input/pointers.md)**</span><span class="sxs-lookup"><span data-stu-id="8d142-229">[![Pointers](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Pointers](features/input/pointers.md)**</span></span><br>
        <span data-ttu-id="8d142-230">了解各种类型的指针</span><span class="sxs-lookup"><span data-stu-id="8d142-230">Learn about various types of pointers</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-231">[![指尖可视化](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) [指尖可视化](features/ux-building-blocks/fingertip-visualization.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-231">[![Fingertip Visualization](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip Visualization](features/ux-building-blocks/fingertip-visualization.md)**</span></span><br>
        <span data-ttu-id="8d142-232">指尖上的视觉可供性，可提高直接交互的置信度</span><span class="sxs-lookup"><span data-stu-id="8d142-232">Visual affordance on the fingertip which improves the confidence for the direct interaction</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="8d142-233">[![追踪菜单](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) [追踪菜单](features/ux-building-blocks/near-menu.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-233">[![Near Menu](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near Menu](features/ux-building-blocks/near-menu.md)**</span></span><br>
        <span data-ttu-id="8d142-234">用于追踪交互的浮动菜单 UI</span><span class="sxs-lookup"><span data-stu-id="8d142-234">Floating menu UI for the near interactions</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-235">[![空间感知入门](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) [空间感知视图](features/spatial-awareness/spatial-awareness-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-235">[![Spatial Awareness Getting started](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Spatial Awareness View](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
        <span data-ttu-id="8d142-236">让全息对象与物理环境进行交互</span><span class="sxs-lookup"><span data-stu-id="8d142-236">Make your holographic objects interact with the physical environments</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-237">[![语音命令](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) [语音命令](features/input/speech.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-237">[![Voice Command](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Voice Command](features/input/speech.md)**</span></span><br>
        <span data-ttu-id="8d142-238">用于集成语音输入的脚本和示例</span><span class="sxs-lookup"><span data-stu-id="8d142-238">Scripts and examples for integrating speech input</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="8d142-239">[![进度指示器](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) [进度指示器](features/ux-building-blocks/progress-indicator.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-239">[![Progress Indicator](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Progress Indicator](features/ux-building-blocks/progress-indicator.md)**</span></span><br>
        <span data-ttu-id="8d142-240">用于传达数据进度或操作的可视指示器</span><span class="sxs-lookup"><span data-stu-id="8d142-240">Visual indicator for communicating data process or operation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-241">[![对话框](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) [对话框](features/ux-building-blocks/dialog.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-241">[![Dialog](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Dialog](features/ux-building-blocks/dialog.md)**</span></span><br>
        <span data-ttu-id="8d142-242">用于请求用户确认或认可的 UI</span><span class="sxs-lookup"><span data-stu-id="8d142-242">UI for asking for user's confirmation or acknowledgement</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-243">[![手部指导](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) [手部指导](features/ux-building-blocks/hand-coach.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-243">[![Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**</span></span><br>
        <span data-ttu-id="8d142-244">在未告知手势时帮助引导用户的组件</span><span class="sxs-lookup"><span data-stu-id="8d142-244">Component that helps guide the user when the gesture has not been taught</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="8d142-245">[![手部物理服务](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/extensions/hand-physics-service.md) [手部物理服务 [实验性]](features/extensions/hand-physics-service.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-245">[![Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/extensions/hand-physics-service.md) **[Hand Physics Service [Experimental]](features/extensions/hand-physics-service.md)**</span></span><br>
        <span data-ttu-id="8d142-246">通过手部物理服务，可实现刚体碰撞事件和与关节式手部的交互</span><span class="sxs-lookup"><span data-stu-id="8d142-246">The hand physics service enables rigid body collision events and interactions with articulated hands</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-247">[![滚动集合](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) [滚动集合](features/ux-building-blocks/scrolling-object-collection.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-247">[![Scrolling Collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrolling Collection](features/ux-building-blocks/scrolling-object-collection.md)**</span></span><br>
        <span data-ttu-id="8d142-248">本机滚动 3D 对象的一个对象集合</span><span class="sxs-lookup"><span data-stu-id="8d142-248">An Object Collection that natively scrolls 3D objects</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-249">[![停靠](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) [停靠 [实验性]](features/experimental/dock.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-249">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Experimental]](features/experimental/dock.md)**</span></span><br>
        <span data-ttu-id="8d142-250">通过停靠功能，可将对象移入和移出预定位置</span><span class="sxs-lookup"><span data-stu-id="8d142-250">The Dock allows objects to be moved in and out of predetermined positions</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="8d142-251">[![眼动跟踪：目标选择](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) [眼动跟踪：目标选择](features/input/eye-tracking/eye-tracking-target-selection.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-251">[![Eye Tracking: Target Selection](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Eye Tracking: Target Selection](features/input/eye-tracking/eye-tracking-target-selection.md)**</span></span><br>
        <span data-ttu-id="8d142-252">将眼睛、语音和手部输入组合起来，以快速轻松地在场景中选择全息影像</span><span class="sxs-lookup"><span data-stu-id="8d142-252">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-253">[![眼动跟踪：导航](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) [眼动跟踪：导航](features/input/eye-tracking/eye-tracking-navigation.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-253">[![Eye Tracking: Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Eye Tracking: Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**</span></span><br>
        <span data-ttu-id="8d142-254">了解如何根据要查看的内容自动滚动文本或流畅地放大到聚焦内容</span><span class="sxs-lookup"><span data-stu-id="8d142-254">Learn how to auto-scroll text or fluently zoom into focused content based on what you are looking at</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8d142-255">[![眼动跟踪：热图](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) [眼动跟踪：热图](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)</span><span class="sxs-lookup"><span data-stu-id="8d142-255">[![Eye Tracking: Heat Map](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Eye Tracking: Heat Map](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span></span><br>
        <span data-ttu-id="8d142-256">记录、加载和直观显示用户已在你的应用中查找的内容的示例</span><span class="sxs-lookup"><span data-stu-id="8d142-256">Examples for logging, loading and visualizing what users have been looking at in your app</span></span>
    :::column-end:::
:::row-end:::

## <a name="tools"></a><span data-ttu-id="8d142-257">工具</span><span class="sxs-lookup"><span data-stu-id="8d142-257">Tools</span></span>

|  <span data-ttu-id="8d142-258">[![优化窗口](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [优化窗口](features/tools/optimize-window.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-258">[![Optimize Window](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimize Window](features/tools/optimize-window.md)</span></span> | <span data-ttu-id="8d142-259">[![依赖关系窗口](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [依赖关系窗口](features/tools/dependency-window.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-259">[![Dependency Window](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Dependency Window](features/tools/dependency-window.md)</span></span> | <span data-ttu-id="8d142-260">[![生成窗口](features/images/MRTK_Icon_BuildWindow.png)](features/tools/build-window.md) [生成窗口](features/tools/build-window.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-260">[![Build Window](features/images/MRTK_Icon_BuildWindow.png)](features/tools/build-window.md) [Build Window](features/tools/build-window.md)</span></span> | <span data-ttu-id="8d142-261">[![输入记录](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [输入记录](features/input-simulation/input-animation-recording.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-261">[![Input recording](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Input recording](features/input-simulation/input-animation-recording.md)</span></span> |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="8d142-262">自动配置混合现实项目来优化性能</span><span class="sxs-lookup"><span data-stu-id="8d142-262">Automate configuration of Mixed Reality projects for performance optimizations</span></span> | <span data-ttu-id="8d142-263">分析资产之间的依赖关系并确定未使用的资产</span><span class="sxs-lookup"><span data-stu-id="8d142-263">Analyze dependencies between assets and identify unused assets</span></span> |  <span data-ttu-id="8d142-264">为混合现实应用程序配置和执行端到端生成进程</span><span class="sxs-lookup"><span data-stu-id="8d142-264">Configure and execute an end-to-end build process for Mixed Reality applications</span></span> | <span data-ttu-id="8d142-265">在编辑器中记录和播放头部移动和手部跟踪数据</span><span class="sxs-lookup"><span data-stu-id="8d142-265">Record and playback head movement and hand tracking data in editor</span></span> |

## <a name="example-scenes"></a><span data-ttu-id="8d142-266">示例场景</span><span class="sxs-lookup"><span data-stu-id="8d142-266">Example scenes</span></span>

<span data-ttu-id="8d142-267">MRTK 提供了示例场景来演示如何使用 MRTK 的功能。</span><span class="sxs-lookup"><span data-stu-id="8d142-267">MRTK provides example scenes that demonstrate how to use MRTK's features.</span></span> <span data-ttu-id="8d142-268">可在 Assets/MRTK/Examples/Demos 文件夹下找到示例场景。</span><span class="sxs-lookup"><span data-stu-id="8d142-268">You can find the example scenes under Assets/MRTK/Examples/Demos folder.</span></span> <span data-ttu-id="8d142-269">请阅读[示例场景](running-example-scenes.md)页面，了解如何获取和运行示例场景。</span><span class="sxs-lookup"><span data-stu-id="8d142-269">Read the [Example scenes](running-example-scenes.md) page to learn how to acquire and run example scenes.</span></span> <span data-ttu-id="8d142-270">通过[手部交互示例场景](features/example-scenes/hand-interaction-examples.md)，可开始体验用于交互和 UI 的 MRTK 构建基块。</span><span class="sxs-lookup"><span data-stu-id="8d142-270">[Hand Interaction Examples scene](features/example-scenes/hand-interaction-examples.md) is a great place to start experiencing MRTK's building blocks for interactions and UI.</span></span>

<span data-ttu-id="8d142-271">[![示例场景 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-271">[![Example Scene 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="mrtk-examples-hub"></a><span data-ttu-id="8d142-272">MRTK 示例中心</span><span class="sxs-lookup"><span data-stu-id="8d142-272">MRTK examples hub</span></span>

<span data-ttu-id="8d142-273">通过 MRTK 示例中心，无需构建和部署各种示例场景即可在 MRTK 中试用它们。</span><span class="sxs-lookup"><span data-stu-id="8d142-273">With the MRTK Examples Hub, you can try various example scenes in MRTK without building and deploying each scene.</span></span>
<span data-ttu-id="8d142-274">可在 [MR 功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)中选择“混合现实工具包示例”包，为 HoloLens (x86)、HoloLens 2 (ARM) 和 Windows Mixed Reality 沉浸式头戴显示设备 (x64) 下载预生成的应用包。</span><span class="sxs-lookup"><span data-stu-id="8d142-274">You can download pre-built app packages for HoloLens(x86), HoloLens 2(ARM), and Windows Mixed Reality immersive headsets(x64) by selecting the "Mixed Reality Toolkit Examples" package in the [MR Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span></span> <span data-ttu-id="8d142-275">请务必[使用 Windows 设备门户在 HoloLens（第一代）上安装应用](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens)。</span><span class="sxs-lookup"><span data-stu-id="8d142-275">Make sure to [use the Windows Device Portal to install apps on HoloLens (1st gen)](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span></span> <span data-ttu-id="8d142-276">在 HoloLens 2 上，可通过 Microsoft Store 应用下载和安装 [MRTK 示例中心](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4)。</span><span class="sxs-lookup"><span data-stu-id="8d142-276">On HoloLens 2, you can download and install [MRTK Examples Hub through the Microsoft Store app](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span></span>

<span data-ttu-id="8d142-277">请查看[示例中心 README 页面](features/example-scenes/example-hub.md)，详细了解如何使用 MRTK 的场景系统和场景过渡服务创建多场景中心。</span><span class="sxs-lookup"><span data-stu-id="8d142-277">See [Examples Hub README page](features/example-scenes/example-hub.md) to learn about the details on creating a multi-scene hub with MRTK's scene system and scene transition service.</span></span>

<span data-ttu-id="8d142-278">[![示例场景中心](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="8d142-278">[![Example Scene Hub](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="sample-apps-made-with-mrtk"></a><span data-ttu-id="8d142-279">使用 MRTK 创建的示例应用</span><span class="sxs-lookup"><span data-stu-id="8d142-279">Sample apps made with MRTK</span></span>

| <span data-ttu-id="8d142-280">[![元素周期表](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="8d142-280">[![Periodic Table of the Elements](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span>| <span data-ttu-id="8d142-281">[![星系探索者](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="8d142-281">[![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span></span>| <span data-ttu-id="8d142-282">[![“表面”示例应用](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span><span class="sxs-lookup"><span data-stu-id="8d142-282">[![Surfaces sample app](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="8d142-283">[元素周期表](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)是一款开源示例应用，它演示了如何使用 MRTK 的输入系统和构建基块打造适合 HoloLens 和沉浸式头戴显示设备的应用体验。</span><span class="sxs-lookup"><span data-stu-id="8d142-283">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) is an open-source sample app which demonstrates how to use MRTK's input system and building blocks to create an app experience for HoloLens and Immersive headsets.</span></span> <span data-ttu-id="8d142-284">阅读迁移案例：[使用 MRTK v2 将“元素周期表”应用引入 HoloLens 2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="8d142-284">Read the porting story: [Bringing the Periodic Table of the Elements app to HoloLens 2 with MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span> |<span data-ttu-id="8d142-285">[星系探索者](https://github.com/Microsoft/GalaxyExplorer)是一款开源示例应用，它最初是 2016 年 3 月作为 HoloLens 的“分享你的创意”活动的一部分开发出来的。</span><span class="sxs-lookup"><span data-stu-id="8d142-285">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) is an open-source sample app that was originally developed in March 2016 as part of the HoloLens 'Share Your Idea' campaign.</span></span> <span data-ttu-id="8d142-286">而借助 MRTK v2，“星系探索者”应用已经过更新，具有适合 HoloLens 2 的新功能。</span><span class="sxs-lookup"><span data-stu-id="8d142-286">Galaxy Explorer has been updated with new features for HoloLens 2, using MRTK v2.</span></span> <span data-ttu-id="8d142-287">阅读文章：[创建适合 HoloLens 2 的“星系探索者”应用](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="8d142-287">Read the story: [The Making of Galaxy Explorer for HoloLens 2](/windows/mixed-reality/galaxy-explorer-update)</span></span> |<span data-ttu-id="8d142-288">[表面](https://github.com/microsoft/MRDL_Unity_Surfaces)是一款适合 HoloLens 2 的开源示例应用，它探讨了我们可如何使用视觉、音频和含义清晰的手部跟踪来创建触觉。</span><span class="sxs-lookup"><span data-stu-id="8d142-288">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) is an open-source sample app for HoloLens 2 which explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span> <span data-ttu-id="8d142-289">若要了解详细设计和开发案例，请查看混合现实开发日活动的研讨会：[从“表面”应用中学到的知识](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)</span><span class="sxs-lookup"><span data-stu-id="8d142-289">Check out Microsoft MR Dev Days session [Learnings from the Surfaces app](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) for the detailed design and development story.</span></span> |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a><span data-ttu-id="8d142-290">来自 2020 年混合现实开发日活动的研讨会视频</span><span class="sxs-lookup"><span data-stu-id="8d142-290">Session videos from Mixed Reality Dev Days 2020</span></span>

| <span data-ttu-id="8d142-291">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span><span class="sxs-lookup"><span data-stu-id="8d142-291">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span></span>| <span data-ttu-id="8d142-292">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span><span class="sxs-lookup"><span data-stu-id="8d142-292">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span></span>| <span data-ttu-id="8d142-293">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span><span class="sxs-lookup"><span data-stu-id="8d142-293">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="8d142-294">查看教程了解如何从头开始创建简单的 MRTK 应用。</span><span class="sxs-lookup"><span data-stu-id="8d142-294">Tutorial on how to create a simple MRTK app from start to finish.</span></span> <span data-ttu-id="8d142-295">了解交互概念和 MRTK 的多平台功能。</span><span class="sxs-lookup"><span data-stu-id="8d142-295">Learn about interaction concepts and MRTK’s multi-platform capabilities.</span></span> | <span data-ttu-id="8d142-296">深入了解 MRTK 的 UX 构建基块，它们可帮助你构建精美的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="8d142-296">Deep dive on the MRTK’s UX building blocks that help you build beautiful mixed reality experiences.</span></span> | <span data-ttu-id="8d142-297">介绍 MRTK 内部和外部的性能工具以及概述 MRTK 标准着色器。</span><span class="sxs-lookup"><span data-stu-id="8d142-297">An introduction to performance tools, both in MRTK and external, as well as an overview of the MRTK Standard Shader.</span></span> |

<span data-ttu-id="8d142-298">若要查看更多研讨会视频，请查看[混合现实开发日](/windows/mixed-reality/mr-dev-days-sessions)。</span><span class="sxs-lookup"><span data-stu-id="8d142-298">See [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions) to explore more session videos.</span></span>

## <a name="engage-with-the-community"></a><span data-ttu-id="8d142-299">与社区互动</span><span class="sxs-lookup"><span data-stu-id="8d142-299">Engage with the community</span></span>

* <span data-ttu-id="8d142-300">在 [Slack](https://holodevelopers.slack.com/) 上加入有关 MRTK 的对话。</span><span class="sxs-lookup"><span data-stu-id="8d142-300">Join the conversation around MRTK on [Slack](https://holodevelopers.slack.com/).</span></span> <span data-ttu-id="8d142-301">可通过[自动邀请发送程序](https://holodevelopersslack.azurewebsites.net/)加入 Slack 社区。</span><span class="sxs-lookup"><span data-stu-id="8d142-301">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

* <span data-ttu-id="8d142-302">在 [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) 上就 MRTK 的使用提问并附上 MRTK 标记。</span><span class="sxs-lookup"><span data-stu-id="8d142-302">Ask questions about using MRTK on [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) using the **MRTK** tag.</span></span>

* <span data-ttu-id="8d142-303">如果发现 MRTK 代码中有内容已损坏，请搜索[已知问题](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)或提出[新问题](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)。</span><span class="sxs-lookup"><span data-stu-id="8d142-303">Search for [known issues](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) or file a [new issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) if you find something broken in MRTK code.</span></span>

* <span data-ttu-id="8d142-304">若要就如何向 MRTK 贡献内容提问，请转到 Stack 上的 [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) 频道。</span><span class="sxs-lookup"><span data-stu-id="8d142-304">For questions about contributing to MRTK, go to the [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) channel on slack.</span></span>

<span data-ttu-id="8d142-305">此项目采用了 [Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。</span><span class="sxs-lookup"><span data-stu-id="8d142-305">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="8d142-306">有关详细信息，请参阅[行为准则常见问题解答](https://opensource.microsoft.com/codeofconduct/faq/)，如有任何其他问题或评论，请联系 [opencode@microsoft.com](mailto:opencode@microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="8d142-306">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a><span data-ttu-id="8d142-307">混合现实开发人员中心的有用资源</span><span class="sxs-lookup"><span data-stu-id="8d142-307">Useful resources on the Mixed Reality Dev Center</span></span>

| <span data-ttu-id="8d142-308">![发现](features/images/mrdevcenter/icon-discover.png) [发现](/windows/mixed-reality/)</span><span class="sxs-lookup"><span data-stu-id="8d142-308">![Discover](features/images/mrdevcenter/icon-discover.png) [Discover](/windows/mixed-reality/)</span></span>| <span data-ttu-id="8d142-309">![设计](features/images/mrdevcenter/icon-design.png) [设计](/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="8d142-309">![Design](features/images/mrdevcenter/icon-design.png) [Design](/windows/mixed-reality/design)</span></span>| <span data-ttu-id="8d142-310">![开发](features/images/mrdevcenter/icon-develop.png) [开发](/windows/mixed-reality/development)</span><span class="sxs-lookup"><span data-stu-id="8d142-310">![Develop](features/images/mrdevcenter/icon-develop.png) [Develop](/windows/mixed-reality/development)</span></span>| <span data-ttu-id="8d142-311">![分发)](features/images/mrdevcenter/icon-distribute.png) [分发](/windows/mixed-reality/implementing-3d-app-launchers)</span><span class="sxs-lookup"><span data-stu-id="8d142-311">![Distribute)](features/images/mrdevcenter/icon-distribute.png) [Distribute](/windows/mixed-reality/implementing-3d-app-launchers)</span></span>|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| <span data-ttu-id="8d142-312">了解如何打造适合 HoloLens 和沉浸式头戴显示设备 (VR) 的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="8d142-312">Learn to build mixed reality experiences for HoloLens and immersive headsets (VR).</span></span>          | <span data-ttu-id="8d142-313">获取设计指南。</span><span class="sxs-lookup"><span data-stu-id="8d142-313">Get design guides.</span></span> <span data-ttu-id="8d142-314">构建用户界面。</span><span class="sxs-lookup"><span data-stu-id="8d142-314">Build user interface.</span></span> <span data-ttu-id="8d142-315">了解交互和输入。</span><span class="sxs-lookup"><span data-stu-id="8d142-315">Learn interactions and input.</span></span>     | <span data-ttu-id="8d142-316">获取开发指南。</span><span class="sxs-lookup"><span data-stu-id="8d142-316">Get development guides.</span></span> <span data-ttu-id="8d142-317">了解相关技术。</span><span class="sxs-lookup"><span data-stu-id="8d142-317">Learn the technology.</span></span> <span data-ttu-id="8d142-318">了解相关科学。</span><span class="sxs-lookup"><span data-stu-id="8d142-318">Understand the science.</span></span>       | <span data-ttu-id="8d142-319">让应用做好供他人使用的准备，并考虑创建 3D 启动器。</span><span class="sxs-lookup"><span data-stu-id="8d142-319">Get your app ready for others and consider creating a 3D launcher.</span></span> |

## <a name="useful-resources-on-azure"></a><span data-ttu-id="8d142-320">Azure 上的有用资源</span><span class="sxs-lookup"><span data-stu-id="8d142-320">Useful resources on Azure</span></span>

| <span data-ttu-id="8d142-321">![空间定位点](features/images/mrdevcenter/icon-azurespatialanchors.png)</span><span class="sxs-lookup"><span data-stu-id="8d142-321">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span></span><br> [<span data-ttu-id="8d142-322">空间定位点</span><span class="sxs-lookup"><span data-stu-id="8d142-322">Spatial Anchors</span></span>](/azure/spatial-anchors/)| <span data-ttu-id="8d142-323">![语音服务](features/images/mrdevcenter/icon-azurespeechservices.png) [语音服务](/azure/cognitive-services/speech-service/)</span><span class="sxs-lookup"><span data-stu-id="8d142-323">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](/azure/cognitive-services/speech-service/)</span></span>| <span data-ttu-id="8d142-324">![视觉服务](features/images/mrdevcenter/icon-azurevisionservices.png) [视觉服务](/azure/cognitive-services/computer-vision/)</span><span class="sxs-lookup"><span data-stu-id="8d142-324">![Vision Services](features/images/mrdevcenter/icon-azurevisionservices.png) [Vision Services](/azure/cognitive-services/computer-vision/)</span></span>|
| :------------------------| :--------------------- | :---------------------- |
| <span data-ttu-id="8d142-325">空间定位点是一项跨平台的服务；借助它，你可使用一段时间内在各设备中位置不变的对象来创建混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="8d142-325">Spatial Anchors is a cross-platform service that allows you to create Mixed Reality experiences using objects that persist their location across devices over time.</span></span>| <span data-ttu-id="8d142-326">发现 Azure 支持的语音功能（例如语音转文本、说话人识别或语音翻译）并将其集成到应用程序中。</span><span class="sxs-lookup"><span data-stu-id="8d142-326">Discover and integrate Azure powered speech capabilities like speech to text, speaker recognition or speech translation into your application.</span></span>| <span data-ttu-id="8d142-327">使用视觉服务（例如计算机视觉、人脸检测、情感识别或视频索引器）标识和分析图像或视频内容。</span><span class="sxs-lookup"><span data-stu-id="8d142-327">Identify and analyze your image or video content using Vision Services like computer vision, face detection, emotion recognition or video indexer.</span></span> |

## <a name="how-to-contribute"></a><span data-ttu-id="8d142-328">如何参与</span><span class="sxs-lookup"><span data-stu-id="8d142-328">How to contribute</span></span>

<span data-ttu-id="8d142-329">可[参与](contributing/contributing.md)页面了解可如何向 MRTK 贡献内容。</span><span class="sxs-lookup"><span data-stu-id="8d142-329">Learn how you can contribute to MRTK at [Contributing](contributing/contributing.md).</span></span>

## <a name="getting-help"></a><span data-ttu-id="8d142-330">获取帮助</span><span class="sxs-lookup"><span data-stu-id="8d142-330">Getting help</span></span>

<span data-ttu-id="8d142-331">如果遇到 MRTK 导致的问题，或者对如何执行某些操作存在疑问，下面几项资源可提供帮助：</span><span class="sxs-lookup"><span data-stu-id="8d142-331">If you run into issues caused by MRTK or otherwise have questions about how to do something, there are a few resources that can help:</span></span>

* <span data-ttu-id="8d142-332">若要报告 bug，请在 GitHub 存储库上[提问](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose)。</span><span class="sxs-lookup"><span data-stu-id="8d142-332">For bug reports, please [file an issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) on the GitHub repo.</span></span>
* <span data-ttu-id="8d142-333">如有一文，请在 [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) 上进行联系，或在 Slack 上的 [mixed-reality-toolkit 频道](https://holodevelopers.slack.com/messages/C2H4HT858)中联系。</span><span class="sxs-lookup"><span data-stu-id="8d142-333">For questions, please reach out on either [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) or the [mixed-reality-toolkit channel](https://holodevelopers.slack.com/messages/C2H4HT858) on Slack.</span></span> <span data-ttu-id="8d142-334">可通过[自动邀请发送程序](https://holodevelopersslack.azurewebsites.net/)加入 Slack 社区。</span><span class="sxs-lookup"><span data-stu-id="8d142-334">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>