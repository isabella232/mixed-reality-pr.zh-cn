---
title: MRTK-Unity 开发人员文档
description: 了解适用于 Unity 的混合现实工具包。
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK
ms.openlocfilehash: cef4bcf671caaaf8d5cb7cdc639446c6c6e91fa0
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850433"
---
# <a name="what-is-the-mixed-reality-toolkit"></a><span data-ttu-id="13802-104">混合现实工具包指的是什么</span><span class="sxs-lookup"><span data-stu-id="13802-104">What is the Mixed Reality Toolkit</span></span>

![混合现实工具包](features/images/Logo_MRTK_Unity_Banner.png)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<span data-ttu-id="13802-106">MRTK-Unity 是由 Microsoft 驱动的项目，它提供了一系列组件和功能来加速 Unity 中的跨平台 MR 应用开发。</span><span class="sxs-lookup"><span data-stu-id="13802-106">MRTK-Unity is a Microsoft-driven project that provides a set of components and features, used to accelerate cross-platform MR app development in Unity.</span></span> <span data-ttu-id="13802-107">以下是它的一些功能：</span><span class="sxs-lookup"><span data-stu-id="13802-107">Here are some of its functions:</span></span>

* <span data-ttu-id="13802-108">为空间交互和 UI 提供跨平台输入系统和构建基块。</span><span class="sxs-lookup"><span data-stu-id="13802-108">Provides the **cross-platform input system and building blocks for spatial interactions and UI**.</span></span>
* <span data-ttu-id="13802-109">通过编辑器内模拟实现快速原型制作，让你能够立即看到变化。</span><span class="sxs-lookup"><span data-stu-id="13802-109">Enables **rapid prototyping** via in-editor simulation that allows you to see changes immediately.</span></span>
* <span data-ttu-id="13802-110">作为可扩展的框架运行，使开发人员能够交换出核心组件。</span><span class="sxs-lookup"><span data-stu-id="13802-110">Operates as an **extensible framework** that provides developers the ability to swap out core components.</span></span>
* <span data-ttu-id="13802-111">支持一系列广泛的平台：</span><span class="sxs-lookup"><span data-stu-id="13802-111">**Supports a wide range of platforms**:</span></span>

| <span data-ttu-id="13802-112">平台</span><span class="sxs-lookup"><span data-stu-id="13802-112">Platform</span></span> | <span data-ttu-id="13802-113">支持的设备</span><span class="sxs-lookup"><span data-stu-id="13802-113">Supported Devices</span></span> |
|---|---|
| <span data-ttu-id="13802-114">OpenXR（Unity 2020.2 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="13802-114">OpenXR (Unity 2020.2 or newer)</span></span> | <span data-ttu-id="13802-115">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="13802-115">Microsoft HoloLens 2</span></span> <br> <span data-ttu-id="13802-116">Windows Mixed Reality 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="13802-116">Windows Mixed Reality headsets</span></span> |
| <span data-ttu-id="13802-117">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="13802-117">Windows Mixed Reality</span></span> | <span data-ttu-id="13802-118">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="13802-118">Microsoft HoloLens</span></span> <br> <span data-ttu-id="13802-119">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="13802-119">Microsoft HoloLens 2</span></span> <br> <span data-ttu-id="13802-120">Windows Mixed Reality 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="13802-120">Windows Mixed Reality headsets</span></span>  |
| <span data-ttu-id="13802-121">Oculus（Unity 2019.3 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="13802-121">Oculus (Unity 2019.3 or newer)</span></span> | <span data-ttu-id="13802-122">Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="13802-122">Oculus Quest</span></span> |
| <span data-ttu-id="13802-123">OpenVR</span><span class="sxs-lookup"><span data-stu-id="13802-123">OpenVR</span></span> |  <span data-ttu-id="13802-124">Windows Mixed Reality 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="13802-124">Windows Mixed Reality headsets</span></span> <br> <span data-ttu-id="13802-125">HTC Vive</span><span class="sxs-lookup"><span data-stu-id="13802-125">HTC Vive</span></span> <br> <span data-ttu-id="13802-126">Oculus Rift</span><span class="sxs-lookup"><span data-stu-id="13802-126">Oculus Rift</span></span> |
| <span data-ttu-id="13802-127">Ultraleap 手部跟踪</span><span class="sxs-lookup"><span data-stu-id="13802-127">Ultraleap Hand Tracking</span></span> | <span data-ttu-id="13802-128">Ultraleap Leap 运动控制器</span><span class="sxs-lookup"><span data-stu-id="13802-128">Ultraleap Leap Motion controller</span></span> |
| <span data-ttu-id="13802-129">移动型</span><span class="sxs-lookup"><span data-stu-id="13802-129">Mobile</span></span> | <span data-ttu-id="13802-130">iOS 和 Android</span><span class="sxs-lookup"><span data-stu-id="13802-130">iOS and Android</span></span> |

## <a name="getting-started-with-mrtk"></a><span data-ttu-id="13802-131">MRTK 入门</span><span class="sxs-lookup"><span data-stu-id="13802-131">Getting started with MRTK</span></span>

<span data-ttu-id="13802-132">如果你不熟悉 Unity 中的 MRTK 或混合现实开发，我们建议在设备或模拟器上安装并浏览 MRTK 示例中心示例应用程序。</span><span class="sxs-lookup"><span data-stu-id="13802-132">If you're new to MRTK or Mixed Reality development in Unity, we recommend installing and exploring the MRTK Examples Hub sample application on your device or emulator.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="13802-133">下载 MRTK 示例中心应用</span><span class="sxs-lookup"><span data-stu-id="13802-133">Download the MRTK Examples Hub app</span></span>](running-examples-hub.md)

<span data-ttu-id="13802-134">在熟悉混合现实和 MRTK 的内容后，请安装所需的工具，并遵循初级级别 HoloLens 2 教程系列操作。</span><span class="sxs-lookup"><span data-stu-id="13802-134">Once you've got the hang of what Mixed Reality and MRTK has to offer, install the necessary tools and follow our beginner level HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="13802-135">安装工具</span><span class="sxs-lookup"><span data-stu-id="13802-135">Install the tools</span></span>](/windows/mixed-reality/develop/install-the-tools?tabs=unity)

> [!div class="nextstepaction"]
> [<span data-ttu-id="13802-136">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="13802-136">HoloLens 2 Tutorial Series</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

<span data-ttu-id="13802-137">想要查看后台正在执行的情况？</span><span class="sxs-lookup"><span data-stu-id="13802-137">Want to see what's going on under the hood?</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="13802-138">在 GitHub 上了解 MRTK</span><span class="sxs-lookup"><span data-stu-id="13802-138">Explore MRTK on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a><span data-ttu-id="13802-139">文档</span><span class="sxs-lookup"><span data-stu-id="13802-139">Documentation</span></span>

| <span data-ttu-id="13802-140">[![发行说明](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span><span class="sxs-lookup"><span data-stu-id="13802-140">[![Release notes](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span></span><br/>[<span data-ttu-id="13802-141">发行说明</span><span class="sxs-lookup"><span data-stu-id="13802-141">Release Notes</span></span>](release-notes/mrtk-26-release-notes.md)| <span data-ttu-id="13802-142">[![MRTK 概述](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span><span class="sxs-lookup"><span data-stu-id="13802-142">[![MRTK Overview](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span></span><br/>[<span data-ttu-id="13802-143">MRTK 概述</span><span class="sxs-lookup"><span data-stu-id="13802-143">MRTK Overview</span></span>](architecture/overview.md)|<span data-ttu-id="13802-144">[![API 参考](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span><span class="sxs-lookup"><span data-stu-id="13802-144">[![API Reference](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span></span><br/>[<span data-ttu-id="13802-145">API 参考</span><span class="sxs-lookup"><span data-stu-id="13802-145">API Reference</span></span>](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a><span data-ttu-id="13802-146">生成状态</span><span class="sxs-lookup"><span data-stu-id="13802-146">Build status</span></span>

| <span data-ttu-id="13802-147">分支</span><span class="sxs-lookup"><span data-stu-id="13802-147">Branch</span></span> | <span data-ttu-id="13802-148">CI 状态</span><span class="sxs-lookup"><span data-stu-id="13802-148">CI Status</span></span> | <span data-ttu-id="13802-149">文档状态</span><span class="sxs-lookup"><span data-stu-id="13802-149">Docs Status</span></span> |
|---|---|---|
| `main` |<span data-ttu-id="13802-150">[![CI 状态](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span><span class="sxs-lookup"><span data-stu-id="13802-150">[![CI Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span></span>|<span data-ttu-id="13802-151">[![文档状态](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span><span class="sxs-lookup"><span data-stu-id="13802-151">[![Docs Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span></span>

## <a name="feature-areas"></a><span data-ttu-id="13802-152">功能区域</span><span class="sxs-lookup"><span data-stu-id="13802-152">Feature areas</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="13802-153">[![输入系统](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="13802-153">[![Input System](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="13802-154">**[输入系统](features/input/overview.md)**</span><span class="sxs-lookup"><span data-stu-id="13802-154">**[Input System](features/input/overview.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-155">[![手部跟踪 (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="13802-155">[![Hand Tracking (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="13802-156">**[手部跟踪 <br> (HoloLens 2)](features/input/hand-tracking.md)**</span><span class="sxs-lookup"><span data-stu-id="13802-156">**[Hand Tracking <br> (HoloLens 2)](features/input/hand-tracking.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-157">[![眼动跟踪 (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span><span class="sxs-lookup"><span data-stu-id="13802-157">[![Eye Tracking (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span></span><br>
        <span data-ttu-id="13802-158">**[眼动跟踪 <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span><span class="sxs-lookup"><span data-stu-id="13802-158">**[Eye Tracking <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-159">[![配置文件](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="13802-159">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span></span><br>
        <span data-ttu-id="13802-160">**[配置文件](configuration/mixed-reality-configuration-guide.md)**</span><span class="sxs-lookup"><span data-stu-id="13802-160">**[Profiles](configuration/mixed-reality-configuration-guide.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="13802-161">[![手部跟踪 (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](supported-devices/leap-motion-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="13802-161">[![Hand Tracking (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](supported-devices/leap-motion-mrtk.md)</span></span><br>
        <span data-ttu-id="13802-162">**[手部跟踪 <br/> (Ultraleap)](supported-devices/leap-motion-mrtk.md)**</span><span class="sxs-lookup"><span data-stu-id="13802-162">**[Hand Tracking <br/> (Ultraleap)](supported-devices/leap-motion-mrtk.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-163">[![UI 控件](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="13802-163">[![UI Controls](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span></span><br>
        <span data-ttu-id="13802-164">**[UI 控件](#ux-building-blocks)**</span><span class="sxs-lookup"><span data-stu-id="13802-164">**[UI Controls](#ux-building-blocks)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-165">[![求解器](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span><span class="sxs-lookup"><span data-stu-id="13802-165">[![Solvers](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span></span><br>
        <span data-ttu-id="13802-166">**[求解器](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="13802-166">**[Solvers](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-167">[![多场景管理器](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="13802-167">[![Multi-Scene Manager](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="13802-168">**[多场景<br/>管理器](features/scene-system/scene-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="13802-168">**[Multi-Scene<br/> Manager](features/scene-system/scene-system-getting-started.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="13802-169">[![空间感知](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="13802-169">[![Spatial Awareness](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span></span><br>
        <span data-ttu-id="13802-170">**[空间<br/>感知](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="13802-170">**[Spatial <br/> Awareness](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-171">[![诊断工具](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="13802-171">[![Diagnostic Tool](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="13802-172">**[诊断<br/>工具](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="13802-172">**[Diagnostic <br/> Tool](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-173">[![MRTK 标准着色器视图](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span><span class="sxs-lookup"><span data-stu-id="13802-173">[![MRTK Standard Shader View](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span></span><br>
        <span data-ttu-id="13802-174">**[MRTK 标准着色器示例视图](features/rendering/mrtk-standard-shader.md?q=shader)**</span><span class="sxs-lookup"><span data-stu-id="13802-174">**[MRTK Standard Shader Example View](features/rendering/mrtk-standard-shader.md?q=shader)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-175">[![语音与听写](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="13802-175">[![Speech & Dictation](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="13802-176">**[语音](features/input/speech.md)<br/> & [听写](features/input/dictation.md)**</span><span class="sxs-lookup"><span data-stu-id="13802-176">**[Speech](features/input/speech.md)<br/> & [Dictation](features/input/dictation.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="13802-177">[![边界系统](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="13802-177">[![Boundary System](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span></span><br>
        <span data-ttu-id="13802-178">**[边界<br/>系统](features/boundary/boundary-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="13802-178">**[Boundary <br/>System](features/boundary/boundary-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-179">[![编辑器内模拟](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="13802-179">[![In-Editor Simulation](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="13802-180">**[编辑器内<br/>模拟](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="13802-180">**[In-Editor <br/> Simulation](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-181">[![实验性功能](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span><span class="sxs-lookup"><span data-stu-id="13802-181">[![Experimental Features](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span></span><br>
        <span data-ttu-id="13802-182">**[实验性<br/>功能](contributing/experimental-features.md)**</span><span class="sxs-lookup"><span data-stu-id="13802-182">**[Experimental <br/> Features](contributing/experimental-features.md)**</span></span><br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a><span data-ttu-id="13802-183">UX 构建基块</span><span class="sxs-lookup"><span data-stu-id="13802-183">UX building blocks</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="13802-184">[![按钮](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) [按钮](features/ux-building-blocks/button.md)</span><span class="sxs-lookup"><span data-stu-id="13802-184">[![Button](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Button](features/ux-building-blocks/button.md)**</span></span><br>
        <span data-ttu-id="13802-185">一种支持各种输入方法（包括 HoloLens 2 关节式手部）的按钮控件</span><span class="sxs-lookup"><span data-stu-id="13802-185">A button control which supports various input methods, including HoloLens 2's articulated hand</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-186">[![边界控制](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) [边界控制](features/ux-building-blocks/bounds-control.md)</span><span class="sxs-lookup"><span data-stu-id="13802-186">[![Bounds Control](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Bounds Control](features/ux-building-blocks/bounds-control.md)**</span></span><br>
        <span data-ttu-id="13802-187">用于模拟 3D 空间中的对象的标准 UI</span><span class="sxs-lookup"><span data-stu-id="13802-187">Standard UI for manipulating objects in 3D space</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-188">[![对象操控器](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) [对象操控器](features/ux-building-blocks/object-manipulator.md)</span><span class="sxs-lookup"><span data-stu-id="13802-188">[![Object Manipulator](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Object Manipulator](features/ux-building-blocks/object-manipulator.md)**</span></span><br>
        <span data-ttu-id="13802-189">用于通过单手或双手操控对象的脚本</span><span class="sxs-lookup"><span data-stu-id="13802-189">Script for manipulating objects with one or two hands</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="13802-190">[![场记板](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) [场记板](features/ux-building-blocks/slate.md)</span><span class="sxs-lookup"><span data-stu-id="13802-190">[![Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**</span></span><br>
        <span data-ttu-id="13802-191">支持通过关节式手部输入进行滚动的 2D 样式平面</span><span class="sxs-lookup"><span data-stu-id="13802-191">2D style plane which supports scrolling with articulated hand input</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-192">[![系统键盘](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) [系统键盘](features/ux-building-blocks/system-keyboard.md)</span><span class="sxs-lookup"><span data-stu-id="13802-192">[![System Keyboard](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[System Keyboard](features/ux-building-blocks/system-keyboard.md)**</span></span><br>
        <span data-ttu-id="13802-193">用于在 Unity 中使用系统键盘的示例脚本</span><span class="sxs-lookup"><span data-stu-id="13802-193">Example script of using the system keyboard in Unity</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-194">[![可交互](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) [可交互](features/ux-building-blocks/interactable.md)</span><span class="sxs-lookup"><span data-stu-id="13802-194">[![Interactable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactable](features/ux-building-blocks/interactable.md)**</span></span><br>
        <span data-ttu-id="13802-195">用于使对象可与可视状态和主题支持进行交互的脚本</span><span class="sxs-lookup"><span data-stu-id="13802-195">A script for making objects interactable with visual states and theme support</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="13802-196">[![求解器](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) [求解器](features/ux-building-blocks/solvers/solver.md)</span><span class="sxs-lookup"><span data-stu-id="13802-196">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
        <span data-ttu-id="13802-197">各种对象定位行为，例如尾随、跟随人体、常量视图大小和表面磁性</span><span class="sxs-lookup"><span data-stu-id="13802-197">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-198">[![对象集合](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) [对象集合](features/ux-building-blocks/object-collection.md)</span><span class="sxs-lookup"><span data-stu-id="13802-198">[![Object Collection](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Object Collection](features/ux-building-blocks/object-collection.md)**</span></span><br>
        <span data-ttu-id="13802-199">用于在三维形状中布设一组对象的脚本</span><span class="sxs-lookup"><span data-stu-id="13802-199">Script for laying out an array of objects in a three-dimensional shape</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-200">[![工具提示](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) [工具提示](features/ux-building-blocks/tooltip.md)</span><span class="sxs-lookup"><span data-stu-id="13802-200">[![Tooltip](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Tooltip](features/ux-building-blocks/tooltip.md)**</span></span><br>
        <span data-ttu-id="13802-201">具有灵活定位点/透视系统的注释 UI，可用于标记运动控制器和对象</span><span class="sxs-lookup"><span data-stu-id="13802-201">Annotation UI with a flexible anchor/pivot system, which can be used for labeling motion controllers and objects</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="13802-202">[![滑块](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) [滑块](features/ux-building-blocks/sliders.md)</span><span class="sxs-lookup"><span data-stu-id="13802-202">[![Slider](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Slider](features/ux-building-blocks/sliders.md)**</span></span><br>
        <span data-ttu-id="13802-203">用于调整支持直接手部跟踪交互的值的滑块 UI</span><span class="sxs-lookup"><span data-stu-id="13802-203">Slider UI for adjusting values supporting direct hand tracking interaction</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-204">[![MRTK 标准着色器](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) [MRTK 标准着色器](features/rendering/mrtk-standard-shader.md)</span><span class="sxs-lookup"><span data-stu-id="13802-204">[![MRTK Standard Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK Standard Shader](features/rendering/mrtk-standard-shader.md)**</span></span><br>
        <span data-ttu-id="13802-205">MRTK 的标准着色器支持各种 Fluent 设计元素并提供高性能</span><span class="sxs-lookup"><span data-stu-id="13802-205">MRTK's Standard shader supports various Fluent design elements with performance</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-206">[![手动菜单](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) [手动菜单](features/ux-building-blocks/hand-menu.md)</span><span class="sxs-lookup"><span data-stu-id="13802-206">[![Hand Menu](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Hand Menu](features/ux-building-blocks/hand-menu.md)**</span></span><br>
        <span data-ttu-id="13802-207">使用手部约束求解器实现快速访问的手部锁定 UI</span><span class="sxs-lookup"><span data-stu-id="13802-207">Hand-locked UI for quick access, using the Hand Constraint Solver</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="13802-208">[![应用栏](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) [应用栏](features/ux-building-blocks/app-bar.md)</span><span class="sxs-lookup"><span data-stu-id="13802-208">[![App Bar](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[App Bar](features/ux-building-blocks/app-bar.md)**</span></span><br>
        <span data-ttu-id="13802-209">用于边界控制的手动激活的 UI</span><span class="sxs-lookup"><span data-stu-id="13802-209">UI for Bounds Control's manual activation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-210">[![指针](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[指针](features/input/pointers.md)**</span><span class="sxs-lookup"><span data-stu-id="13802-210">[![Pointers](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Pointers](features/input/pointers.md)**</span></span><br>
        <span data-ttu-id="13802-211">了解各种类型的指针</span><span class="sxs-lookup"><span data-stu-id="13802-211">Learn about various types of pointers</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-212">[![指尖可视化](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) [指尖可视化](features/ux-building-blocks/fingertip-visualization.md)</span><span class="sxs-lookup"><span data-stu-id="13802-212">[![Fingertip Visualization](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip Visualization](features/ux-building-blocks/fingertip-visualization.md)**</span></span><br>
        <span data-ttu-id="13802-213">指尖上的视觉可供性，可提高直接交互的置信度</span><span class="sxs-lookup"><span data-stu-id="13802-213">Visual affordance on the fingertip which improves the confidence for the direct interaction</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="13802-214">[![追踪菜单](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) [追踪菜单](features/ux-building-blocks/near-menu.md)</span><span class="sxs-lookup"><span data-stu-id="13802-214">[![Near Menu](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near Menu](features/ux-building-blocks/near-menu.md)**</span></span><br>
        <span data-ttu-id="13802-215">用于追踪交互的浮动菜单 UI</span><span class="sxs-lookup"><span data-stu-id="13802-215">Floating menu UI for the near interactions</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-216">[![空间感知入门](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) [空间感知视图](features/spatial-awareness/spatial-awareness-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="13802-216">[![Spatial Awareness Getting started](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Spatial Awareness View](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
        <span data-ttu-id="13802-217">让全息对象与物理环境进行交互</span><span class="sxs-lookup"><span data-stu-id="13802-217">Make your holographic objects interact with the physical environments</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-218">[![语音命令](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) [语音命令](features/input/speech.md)</span><span class="sxs-lookup"><span data-stu-id="13802-218">[![Voice Command](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Voice Command](features/input/speech.md)**</span></span><br>
        <span data-ttu-id="13802-219">用于集成语音输入的脚本和示例</span><span class="sxs-lookup"><span data-stu-id="13802-219">Scripts and examples for integrating speech input</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="13802-220">[![进度指示器](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) [进度指示器](features/ux-building-blocks/progress-indicator.md)</span><span class="sxs-lookup"><span data-stu-id="13802-220">[![Progress Indicator](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Progress Indicator](features/ux-building-blocks/progress-indicator.md)**</span></span><br>
        <span data-ttu-id="13802-221">用于传达数据进度或操作的可视指示器</span><span class="sxs-lookup"><span data-stu-id="13802-221">Visual indicator for communicating data process or operation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-222">[![对话框](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) [对话框](features/ux-building-blocks/dialog.md)</span><span class="sxs-lookup"><span data-stu-id="13802-222">[![Dialog](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Dialog](features/ux-building-blocks/dialog.md)**</span></span><br>
        <span data-ttu-id="13802-223">用于请求用户确认或认可的 UI</span><span class="sxs-lookup"><span data-stu-id="13802-223">UI for asking for user's confirmation or acknowledgement</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-224">[![手部指导](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) [手部指导](features/ux-building-blocks/hand-coach.md)</span><span class="sxs-lookup"><span data-stu-id="13802-224">[![Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**</span></span><br>
        <span data-ttu-id="13802-225">在未告知手势时帮助引导用户的组件</span><span class="sxs-lookup"><span data-stu-id="13802-225">Component that helps guide the user when the gesture has not been taught</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="13802-226">[![手部物理服务](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) [手部物理服务 [实验性]](features/experimental/hand-physics-service.md)</span><span class="sxs-lookup"><span data-stu-id="13802-226">[![Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Hand Physics Service [Experimental]](features/experimental/hand-physics-service.md)**</span></span><br>
        <span data-ttu-id="13802-227">通过手部物理服务，可实现刚体碰撞事件和与关节式手部的交互</span><span class="sxs-lookup"><span data-stu-id="13802-227">The hand physics service enables rigid body collision events and interactions with articulated hands</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-228">[![滚动集合](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) [滚动集合](features/ux-building-blocks/scrolling-object-collection.md)</span><span class="sxs-lookup"><span data-stu-id="13802-228">[![Scrolling Collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrolling Collection](features/ux-building-blocks/scrolling-object-collection.md)**</span></span><br>
        <span data-ttu-id="13802-229">本机滚动 3D 对象的一个对象集合</span><span class="sxs-lookup"><span data-stu-id="13802-229">An Object Collection that natively scrolls 3D objects</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-230">[![停靠](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) [停靠 [实验性]](features/experimental/dock.md)</span><span class="sxs-lookup"><span data-stu-id="13802-230">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Experimental]](features/experimental/dock.md)**</span></span><br>
        <span data-ttu-id="13802-231">通过停靠功能，可将对象移入和移出预定位置</span><span class="sxs-lookup"><span data-stu-id="13802-231">The Dock allows objects to be moved in and out of predetermined positions</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="13802-232">[![眼动跟踪：目标选择](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) [眼动跟踪：目标选择](features/input/eye-tracking/eye-tracking-target-selection.md)</span><span class="sxs-lookup"><span data-stu-id="13802-232">[![Eye Tracking: Target Selection](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Eye Tracking: Target Selection](features/input/eye-tracking/eye-tracking-target-selection.md)**</span></span><br>
        <span data-ttu-id="13802-233">将眼睛、语音和手部输入组合起来，以快速轻松地在场景中选择全息影像</span><span class="sxs-lookup"><span data-stu-id="13802-233">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-234">[![眼动跟踪：导航](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) [眼动跟踪：导航](features/input/eye-tracking/eye-tracking-navigation.md)</span><span class="sxs-lookup"><span data-stu-id="13802-234">[![Eye Tracking: Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Eye Tracking: Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**</span></span><br>
        <span data-ttu-id="13802-235">了解如何根据要查看的内容自动滚动文本或流畅地放大到聚焦内容</span><span class="sxs-lookup"><span data-stu-id="13802-235">Learn how to auto-scroll text or fluently zoom into focused content based on what you are looking at</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="13802-236">[![眼动跟踪：热图](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) [眼动跟踪：热图](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)</span><span class="sxs-lookup"><span data-stu-id="13802-236">[![Eye Tracking: Heat Map](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Eye Tracking: Heat Map](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span></span><br>
        <span data-ttu-id="13802-237">记录、加载和直观显示用户已在你的应用中查找的内容的示例</span><span class="sxs-lookup"><span data-stu-id="13802-237">Examples for logging, loading and visualizing what users have been looking at in your app</span></span>
    :::column-end:::
:::row-end:::

## <a name="tools"></a><span data-ttu-id="13802-238">工具</span><span class="sxs-lookup"><span data-stu-id="13802-238">Tools</span></span>

|  <span data-ttu-id="13802-239">[![优化窗口](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [优化窗口](features/tools/optimize-window.md)</span><span class="sxs-lookup"><span data-stu-id="13802-239">[![Optimize Window](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimize Window](features/tools/optimize-window.md)</span></span> | <span data-ttu-id="13802-240">[![依赖关系窗口](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [依赖关系窗口](features/tools/dependency-window.md)</span><span class="sxs-lookup"><span data-stu-id="13802-240">[![Dependency Window](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Dependency Window](features/tools/dependency-window.md)</span></span> | ![“生成”窗口](features/images/MRTK_Icon_BuildWindow.png) <span data-ttu-id="13802-242">“生成”窗口</span><span class="sxs-lookup"><span data-stu-id="13802-242">Build Window</span></span> | <span data-ttu-id="13802-243">[![输入记录](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [输入记录](features/input-simulation/input-animation-recording.md)</span><span class="sxs-lookup"><span data-stu-id="13802-243">[![Input recording](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Input recording](features/input-simulation/input-animation-recording.md)</span></span> |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="13802-244">自动配置混合现实项目来优化性能</span><span class="sxs-lookup"><span data-stu-id="13802-244">Automate configuration of Mixed Reality projects for performance optimizations</span></span> | <span data-ttu-id="13802-245">分析资产之间的依赖关系并确定未使用的资产</span><span class="sxs-lookup"><span data-stu-id="13802-245">Analyze dependencies between assets and identify unused assets</span></span> |  <span data-ttu-id="13802-246">为混合现实应用程序配置和执行端到端生成进程</span><span class="sxs-lookup"><span data-stu-id="13802-246">Configure and execute an end-to-end build process for Mixed Reality applications</span></span> | <span data-ttu-id="13802-247">在编辑器中记录和播放头部移动和手部跟踪数据</span><span class="sxs-lookup"><span data-stu-id="13802-247">Record and playback head movement and hand tracking data in editor</span></span> |

## <a name="example-scenes"></a><span data-ttu-id="13802-248">示例场景</span><span class="sxs-lookup"><span data-stu-id="13802-248">Example scenes</span></span>

<span data-ttu-id="13802-249">在 [此示例场景](features/example-scenes/hand-interaction-examples.md)中，了解 MRTK 各种类型的交互和 UI 控件。</span><span class="sxs-lookup"><span data-stu-id="13802-249">Explore MRTK's various types of interactions and UI controls in [this example scene](features/example-scenes/hand-interaction-examples.md).</span></span>

<span data-ttu-id="13802-250">[![示例场景 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="13802-250">[![Example Scene 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="mrtk-examples-hub"></a><span data-ttu-id="13802-251">MRTK 示例中心</span><span class="sxs-lookup"><span data-stu-id="13802-251">MRTK examples hub</span></span>

<span data-ttu-id="13802-252">通过 MRTK 示例中心，可在 MRTK 中尝试各种示例场景。</span><span class="sxs-lookup"><span data-stu-id="13802-252">With the MRTK Examples Hub, you can try various example scenes in MRTK.</span></span>
<span data-ttu-id="13802-253">可在 [MR 功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)中选择“混合现实工具包示例”包，为 HoloLens (x86)、HoloLens 2 (ARM) 和 Windows Mixed Reality 沉浸式头戴显示设备 (x64) 下载预生成的应用包。</span><span class="sxs-lookup"><span data-stu-id="13802-253">You can download pre-built app packages for HoloLens(x86), HoloLens 2(ARM), and Windows Mixed Reality immersive headsets(x64) by selecting the "Mixed Reality Toolkit Examples" package in the [MR Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span></span> <span data-ttu-id="13802-254">请务必[使用 Windows 设备门户在 HoloLens（第一代）上安装应用](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens)。</span><span class="sxs-lookup"><span data-stu-id="13802-254">Make sure to [use the Windows Device Portal to install apps on HoloLens (1st gen)](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span></span> <span data-ttu-id="13802-255">在 HoloLens 2 上，可通过 Microsoft Store 应用下载和安装 [MRTK 示例中心](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4)。</span><span class="sxs-lookup"><span data-stu-id="13802-255">On HoloLens 2, you can download and install [MRTK Examples Hub through the Microsoft Store app](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span></span>

<span data-ttu-id="13802-256">请查看[示例中心 README 页面](features/example-scenes/example-hub.md)，详细了解如何使用 MRTK 的场景系统和场景过渡服务创建多场景中心。</span><span class="sxs-lookup"><span data-stu-id="13802-256">See [Examples Hub README page](features/example-scenes/example-hub.md) to learn about the details on creating a multi-scene hub with MRTK's scene system and scene transition service.</span></span>

<span data-ttu-id="13802-257">[![示例场景中心](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="13802-257">[![Example Scene Hub](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="sample-apps-made-with-mrtk"></a><span data-ttu-id="13802-258">使用 MRTK 创建的示例应用</span><span class="sxs-lookup"><span data-stu-id="13802-258">Sample apps made with MRTK</span></span>

| <span data-ttu-id="13802-259">[![元素周期表](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="13802-259">[![Periodic Table of the Elements](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span>| <span data-ttu-id="13802-260">[![星系探索者](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="13802-260">[![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span></span>| <span data-ttu-id="13802-261">[![“表面”示例应用](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span><span class="sxs-lookup"><span data-stu-id="13802-261">[![Surfaces sample app](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="13802-262">[元素周期表](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)是一款开源示例应用，它演示了如何使用 MRTK 的输入系统和构建基块打造适合 HoloLens 和沉浸式头戴显示设备的应用体验。</span><span class="sxs-lookup"><span data-stu-id="13802-262">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) is an open-source sample app which demonstrates how to use MRTK's input system and building blocks to create an app experience for HoloLens and Immersive headsets.</span></span> <span data-ttu-id="13802-263">阅读迁移案例：[使用 MRTK v2 将“元素周期表”应用引入 HoloLens 2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="13802-263">Read the porting story: [Bringing the Periodic Table of the Elements app to HoloLens 2 with MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span> |<span data-ttu-id="13802-264">[星系探索者](https://github.com/Microsoft/GalaxyExplorer)是一款开源示例应用，它最初是 2016 年 3 月作为 HoloLens 的“分享你的创意”活动的一部分开发出来的。</span><span class="sxs-lookup"><span data-stu-id="13802-264">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) is an open-source sample app that was originally developed in March 2016 as part of the HoloLens 'Share Your Idea' campaign.</span></span> <span data-ttu-id="13802-265">而借助 MRTK v2，“星系探索者”应用已经过更新，具有适合 HoloLens 2 的新功能。</span><span class="sxs-lookup"><span data-stu-id="13802-265">Galaxy Explorer has been updated with new features for HoloLens 2, using MRTK v2.</span></span> <span data-ttu-id="13802-266">阅读文章：[创建适合 HoloLens 2 的“星系探索者”应用](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="13802-266">Read the story: [The Making of Galaxy Explorer for HoloLens 2](/windows/mixed-reality/galaxy-explorer-update)</span></span> |<span data-ttu-id="13802-267">[表面](https://github.com/microsoft/MRDL_Unity_Surfaces)是一款适合 HoloLens 2 的开源示例应用，它探讨了我们可如何使用视觉、音频和含义清晰的手部跟踪来创建触觉。</span><span class="sxs-lookup"><span data-stu-id="13802-267">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) is an open-source sample app for HoloLens 2 which explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span> <span data-ttu-id="13802-268">若要了解详细设计和开发案例，请查看混合现实开发日活动的研讨会：[从“表面”应用中学到的知识](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)</span><span class="sxs-lookup"><span data-stu-id="13802-268">Check out Microsoft MR Dev Days session [Learnings from the Surfaces app](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) for the detailed design and development story.</span></span> |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a><span data-ttu-id="13802-269">来自 2020 年混合现实开发日活动的研讨会视频</span><span class="sxs-lookup"><span data-stu-id="13802-269">Session videos from Mixed Reality Dev Days 2020</span></span>

| <span data-ttu-id="13802-270">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span><span class="sxs-lookup"><span data-stu-id="13802-270">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span></span>| <span data-ttu-id="13802-271">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span><span class="sxs-lookup"><span data-stu-id="13802-271">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span></span>| <span data-ttu-id="13802-272">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span><span class="sxs-lookup"><span data-stu-id="13802-272">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="13802-273">查看教程了解如何从头开始创建简单的 MRTK 应用。</span><span class="sxs-lookup"><span data-stu-id="13802-273">Tutorial on how to create a simple MRTK app from start to finish.</span></span> <span data-ttu-id="13802-274">了解交互概念和 MRTK 的多平台功能。</span><span class="sxs-lookup"><span data-stu-id="13802-274">Learn about interaction concepts and MRTK’s multi-platform capabilities.</span></span> | <span data-ttu-id="13802-275">深入了解 MRTK 的 UX 构建基块，它们可帮助你构建精美的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="13802-275">Deep dive on the MRTK’s UX building blocks that help you build beautiful mixed reality experiences.</span></span> | <span data-ttu-id="13802-276">介绍 MRTK 内部和外部的性能工具以及概述 MRTK 标准着色器。</span><span class="sxs-lookup"><span data-stu-id="13802-276">An introduction to performance tools, both in MRTK and external, as well as an overview of the MRTK Standard Shader.</span></span> |

<span data-ttu-id="13802-277">若要查看更多研讨会视频，请查看[混合现实开发日](/windows/mixed-reality/mr-dev-days-sessions)。</span><span class="sxs-lookup"><span data-stu-id="13802-277">See [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions) to explore more session videos.</span></span>

## <a name="engage-with-the-community"></a><span data-ttu-id="13802-278">与社区互动</span><span class="sxs-lookup"><span data-stu-id="13802-278">Engage with the community</span></span>

* <span data-ttu-id="13802-279">在 [Slack](https://holodevelopers.slack.com/) 上加入有关 MRTK 的对话。</span><span class="sxs-lookup"><span data-stu-id="13802-279">Join the conversation around MRTK on [Slack](https://holodevelopers.slack.com/).</span></span> <span data-ttu-id="13802-280">可通过[自动邀请发送程序](https://holodevelopersslack.azurewebsites.net/)加入 Slack 社区。</span><span class="sxs-lookup"><span data-stu-id="13802-280">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

* <span data-ttu-id="13802-281">在 [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) 上就 MRTK 的使用提问并附上 MRTK 标记。</span><span class="sxs-lookup"><span data-stu-id="13802-281">Ask questions about using MRTK on [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) using the **MRTK** tag.</span></span>

* <span data-ttu-id="13802-282">如果发现 MRTK 代码中有内容已损坏，请搜索[已知问题](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)或提出[新问题](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues)。</span><span class="sxs-lookup"><span data-stu-id="13802-282">Search for [known issues](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) or file a [new issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) if you find something broken in MRTK code.</span></span>

* <span data-ttu-id="13802-283">若要就如何向 MRTK 贡献内容提问，请转到 Stack 上的 [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) 频道。</span><span class="sxs-lookup"><span data-stu-id="13802-283">For questions about contributing to MRTK, go to the [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) channel on slack.</span></span>

<span data-ttu-id="13802-284">此项目采用了 [Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。</span><span class="sxs-lookup"><span data-stu-id="13802-284">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="13802-285">有关详细信息，请参阅[行为准则常见问题解答](https://opensource.microsoft.com/codeofconduct/faq/)，如有任何其他问题或评论，请联系 [opencode@microsoft.com](mailto:opencode@microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="13802-285">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a><span data-ttu-id="13802-286">混合现实开发人员中心的有用资源</span><span class="sxs-lookup"><span data-stu-id="13802-286">Useful resources on the Mixed Reality Dev Center</span></span>

| <span data-ttu-id="13802-287">![发现](features/images/mrdevcenter/icon-discover.png) [发现](/windows/mixed-reality/)</span><span class="sxs-lookup"><span data-stu-id="13802-287">![Discover](features/images/mrdevcenter/icon-discover.png) [Discover](/windows/mixed-reality/)</span></span>| <span data-ttu-id="13802-288">![设计](features/images/mrdevcenter/icon-design.png) [设计](/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="13802-288">![Design](features/images/mrdevcenter/icon-design.png) [Design](/windows/mixed-reality/design)</span></span>| <span data-ttu-id="13802-289">![开发](features/images/mrdevcenter/icon-develop.png) [开发](/windows/mixed-reality/development)</span><span class="sxs-lookup"><span data-stu-id="13802-289">![Develop](features/images/mrdevcenter/icon-develop.png) [Develop](/windows/mixed-reality/development)</span></span>| <span data-ttu-id="13802-290">![分发)](features/images/mrdevcenter/icon-distribute.png) [分发](/windows/mixed-reality/implementing-3d-app-launchers)</span><span class="sxs-lookup"><span data-stu-id="13802-290">![Distribute)](features/images/mrdevcenter/icon-distribute.png) [Distribute](/windows/mixed-reality/implementing-3d-app-launchers)</span></span>|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| <span data-ttu-id="13802-291">了解如何打造适合 HoloLens 和沉浸式头戴显示设备 (VR) 的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="13802-291">Learn to build mixed reality experiences for HoloLens and immersive headsets (VR).</span></span>          | <span data-ttu-id="13802-292">获取设计指南。</span><span class="sxs-lookup"><span data-stu-id="13802-292">Get design guides.</span></span> <span data-ttu-id="13802-293">构建用户界面。</span><span class="sxs-lookup"><span data-stu-id="13802-293">Build user interface.</span></span> <span data-ttu-id="13802-294">了解交互和输入。</span><span class="sxs-lookup"><span data-stu-id="13802-294">Learn interactions and input.</span></span>     | <span data-ttu-id="13802-295">获取开发指南。</span><span class="sxs-lookup"><span data-stu-id="13802-295">Get development guides.</span></span> <span data-ttu-id="13802-296">了解相关技术。</span><span class="sxs-lookup"><span data-stu-id="13802-296">Learn the technology.</span></span> <span data-ttu-id="13802-297">了解相关科学。</span><span class="sxs-lookup"><span data-stu-id="13802-297">Understand the science.</span></span>       | <span data-ttu-id="13802-298">让应用做好供他人使用的准备，并考虑创建 3D 启动器。</span><span class="sxs-lookup"><span data-stu-id="13802-298">Get your app ready for others and consider creating a 3D launcher.</span></span> |

## <a name="useful-resources-on-azure"></a><span data-ttu-id="13802-299">Azure 上的有用资源</span><span class="sxs-lookup"><span data-stu-id="13802-299">Useful resources on Azure</span></span>

| <span data-ttu-id="13802-300">![空间定位点](features/images/mrdevcenter/icon-azurespatialanchors.png)</span><span class="sxs-lookup"><span data-stu-id="13802-300">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span></span><br> [<span data-ttu-id="13802-301">空间定位点</span><span class="sxs-lookup"><span data-stu-id="13802-301">Spatial Anchors</span></span>](/azure/spatial-anchors/)| <span data-ttu-id="13802-302">![语音服务](features/images/mrdevcenter/icon-azurespeechservices.png) [语音服务](/azure/cognitive-services/speech-service/)</span><span class="sxs-lookup"><span data-stu-id="13802-302">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](/azure/cognitive-services/speech-service/)</span></span>| <span data-ttu-id="13802-303">![视觉服务](features/images/mrdevcenter/icon-azurevisionservices.png) [视觉服务](/azure/cognitive-services/computer-vision/)</span><span class="sxs-lookup"><span data-stu-id="13802-303">![Vision Services](features/images/mrdevcenter/icon-azurevisionservices.png) [Vision Services](/azure/cognitive-services/computer-vision/)</span></span>|
| :------------------------| :--------------------- | :---------------------- |
| <span data-ttu-id="13802-304">空间定位点是一项跨平台的服务；借助它，你可使用一段时间内在各设备中位置不变的对象来创建混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="13802-304">Spatial Anchors is a cross-platform service that allows you to create Mixed Reality experiences using objects that persist their location across devices over time.</span></span>| <span data-ttu-id="13802-305">发现 Azure 支持的语音功能（例如语音转文本、说话人识别或语音翻译）并将其集成到应用程序中。</span><span class="sxs-lookup"><span data-stu-id="13802-305">Discover and integrate Azure powered speech capabilities like speech to text, speaker recognition or speech translation into your application.</span></span>| <span data-ttu-id="13802-306">使用视觉服务（例如计算机视觉、人脸检测、情感识别或视频索引器）标识和分析图像或视频内容。</span><span class="sxs-lookup"><span data-stu-id="13802-306">Identify and analyze your image or video content using Vision Services like computer vision, face detection, emotion recognition or video indexer.</span></span> |

## <a name="how-to-contribute"></a><span data-ttu-id="13802-307">如何参与</span><span class="sxs-lookup"><span data-stu-id="13802-307">How to contribute</span></span>

<span data-ttu-id="13802-308">可[参与](contributing/contributing.md)页面了解可如何向 MRTK 贡献内容。</span><span class="sxs-lookup"><span data-stu-id="13802-308">Learn how you can contribute to MRTK at [Contributing](contributing/contributing.md).</span></span>

## <a name="getting-help"></a><span data-ttu-id="13802-309">获取帮助</span><span class="sxs-lookup"><span data-stu-id="13802-309">Getting help</span></span>

<span data-ttu-id="13802-310">如果遇到 MRTK 导致的问题，或者对如何执行某些操作存在疑问，下面几项资源可提供帮助：</span><span class="sxs-lookup"><span data-stu-id="13802-310">If you run into issues caused by MRTK or otherwise have questions about how to do something, there are a few resources that can help:</span></span>

* <span data-ttu-id="13802-311">若要报告 bug，请在 GitHub 存储库上[提问](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose)。</span><span class="sxs-lookup"><span data-stu-id="13802-311">For bug reports, please [file an issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) on the GitHub repo.</span></span>
* <span data-ttu-id="13802-312">如有一文，请在 [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) 上进行联系，或在 Slack 上的 [mixed-reality-toolkit 频道](https://holodevelopers.slack.com/messages/C2H4HT858)中联系。</span><span class="sxs-lookup"><span data-stu-id="13802-312">For questions, please reach out on either [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) or the [mixed-reality-toolkit channel](https://holodevelopers.slack.com/messages/C2H4HT858) on Slack.</span></span> <span data-ttu-id="13802-313">可通过[自动邀请发送程序](https://holodevelopersslack.azurewebsites.net/)加入 Slack 社区。</span><span class="sxs-lookup"><span data-stu-id="13802-313">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>