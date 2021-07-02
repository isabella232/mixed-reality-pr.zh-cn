---
title: 目视跟踪示例概述
description: 用于在 MRTK 中生成 eyetracking 的示例
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，EyeTracking，
ms.openlocfilehash: 4cdeaa10725e00ac1a041c3692d64c1bd6488854
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175546"
---
# <a name="eye-tracking-examples-overview"></a><span data-ttu-id="1530a-104">目视跟踪示例概述</span><span class="sxs-lookup"><span data-stu-id="1530a-104">Eye tracking examples overview</span></span>

<span data-ttu-id="1530a-105">本主题介绍了如何在 MRTK 中快速开始使用目视跟踪，方法是在 MRTK 眼跟踪示例 (资产/MRTK/示例/演示/EyeTracking) 上构建。</span><span class="sxs-lookup"><span data-stu-id="1530a-105">This topic describes how to quickly get started with eye tracking in MRTK by building on MRTK eye tracking examples (Assets/MRTK/Examples/Demos/EyeTracking).</span></span>
<span data-ttu-id="1530a-106">这些示例可让你体验我们的新神奇输入功能： **目视跟踪**！</span><span class="sxs-lookup"><span data-stu-id="1530a-106">These samples let you experience one of our new magical input capabilities: **Eye tracking**!</span></span>
<span data-ttu-id="1530a-107">此演示包括各种用例，从隐式的基于目视的激活到如何无缝地将有关所查看内容的信息与 **语音** 和 **手写** 输入相关。</span><span class="sxs-lookup"><span data-stu-id="1530a-107">The demo includes various use cases, ranging from implicit eye-based activations to how to seamlessly combine information about what you are looking at with **voice** and **hand** input.</span></span>
<span data-ttu-id="1530a-108">这样，用户就可以通过查看目标并说 _"选择"_ 或执行手动手势，在视图中快速轻松地选择和移动全息内容。</span><span class="sxs-lookup"><span data-stu-id="1530a-108">This enables users to quickly and effortlessly select and move holographic content across their view simply by looking at a target and saying _'Select'_ or performing a hand gesture.</span></span>
<span data-ttu-id="1530a-109">演示还包括一个用于目视定向滚动的示例、文本和图像在石板上的平移和缩放。</span><span class="sxs-lookup"><span data-stu-id="1530a-109">The demos also include an example for eye-gaze-directed scroll, pan and zoom of text and images on a slate.</span></span>
<span data-ttu-id="1530a-110">最后，还提供了一个示例，用于记录和直观显示二维石板上用户的视觉对象。</span><span class="sxs-lookup"><span data-stu-id="1530a-110">Finally, an example is provided for recording and visualizing the user's visual attention on a 2D slate.</span></span>
<span data-ttu-id="1530a-111">在下一节中，你将了解 MRTK 目视跟踪示例包 (资产/MRTK/示例/演示/EyeTracking) 中每个不同示例的详细信息，包括：</span><span class="sxs-lookup"><span data-stu-id="1530a-111">In the following section, you will find more details on what each of the different samples in the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking) includes:</span></span>

![目视跟踪场景列表](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

<span data-ttu-id="1530a-113">以下部分简要概述了各个目视跟踪演示的幕后内容。</span><span class="sxs-lookup"><span data-stu-id="1530a-113">The following section is a quick overview of what the individual eye tracking demo scenes are about.</span></span>
<span data-ttu-id="1530a-114">MRTK 目视跟踪演示场景已 [加载添加性地](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)，我们将在下面介绍如何设置。</span><span class="sxs-lookup"><span data-stu-id="1530a-114">The MRTK eye tracking demo scenes are [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html), which we will explain below how to set up.</span></span>

## <a name="overview-of-the-eye-tracking-demo-samples"></a><span data-ttu-id="1530a-115">目视跟踪演示示例概述</span><span class="sxs-lookup"><span data-stu-id="1530a-115">Overview of the eye tracking demo samples</span></span>

### <a name="eye-supported-target-selection"></a>[<span data-ttu-id="1530a-116">**目视支持的目标选择**</span><span class="sxs-lookup"><span data-stu-id="1530a-116">**Eye-Supported Target Selection**</span></span>](../input/eye-tracking/eye-tracking-target-selection.md)

<span data-ttu-id="1530a-117">本教程展示了访问眼睛数据以选择目标的便利。</span><span class="sxs-lookup"><span data-stu-id="1530a-117">This tutorial showcases the ease of accessing eye gaze data to select targets.</span></span>
<span data-ttu-id="1530a-118">它包括一个微妙但功能强大的反馈示例，可让用户自信地了解目标，而不会带来巨大的作用。</span><span class="sxs-lookup"><span data-stu-id="1530a-118">It includes an example for subtle yet powerful feedback to provide the user with the confidence that a target is focused without being overwhelming.</span></span>
<span data-ttu-id="1530a-119">此外，还提供了一个简单的智能通知示例，可在读取后自动消失。</span><span class="sxs-lookup"><span data-stu-id="1530a-119">In addition, there is a simple example of smart notifications that automatically disappear after being read.</span></span>

<span data-ttu-id="1530a-120">**摘要**：通过眼睛、语音和手写输入的组合来快速轻松地进行目标选择。</span><span class="sxs-lookup"><span data-stu-id="1530a-120">**Summary**: Fast and effortless target selections using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-navigation"></a>[<span data-ttu-id="1530a-121">**目视支持的导航**</span><span class="sxs-lookup"><span data-stu-id="1530a-121">**Eye-Supported Navigation**</span></span>](../input/eye-tracking/eye-tracking-navigation.md)

<span data-ttu-id="1530a-122">Imagine 您正在阅读有关远处显示或您的电子读者的某些信息，并且到达显示文本的末尾时，文本会自动向上滚动以显示更多内容。</span><span class="sxs-lookup"><span data-stu-id="1530a-122">Imagine that you are reading some information on a distant display or your e-reader and when you reach the end of the displayed text, the text automatically scrolls up to reveal more content.</span></span>
<span data-ttu-id="1530a-123">或者怎样才能直接缩放到你所关注的位置呢？</span><span class="sxs-lookup"><span data-stu-id="1530a-123">Or how about magically zooming directly toward where you were looking at?</span></span>
<span data-ttu-id="1530a-124">以下是本教程中有关目视支持的导航的一些示例展示。</span><span class="sxs-lookup"><span data-stu-id="1530a-124">These are some of the examples showcased in this tutorial regarding eye-supported navigation.</span></span>
<span data-ttu-id="1530a-125">此外，还提供了一种无人参与的3D 全息旋转示例，使其根据当前焦点自动旋转。</span><span class="sxs-lookup"><span data-stu-id="1530a-125">In addition, there is an example for hands-free rotation of 3D holograms by making them automatically rotate based on your current focus.</span></span>

<span data-ttu-id="1530a-126">**摘要**：使用眼睛、声音和手写输入的组合进行滚动、平移、缩放、3d 旋转。</span><span class="sxs-lookup"><span data-stu-id="1530a-126">**Summary**: Scroll, pan, zoom, 3D rotation using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-positioning"></a>[<span data-ttu-id="1530a-127">**目视支持的定位**</span><span class="sxs-lookup"><span data-stu-id="1530a-127">**Eye-Supported Positioning**</span></span>](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

<span data-ttu-id="1530a-128">本教程展示了一种名为 "Put" 的输入方案 [-](https://youtu.be/CbIn8p4_4CQ) 在早期的1980年中，可以从 MIT Media Lab 可追溯到 "信息检索"。</span><span class="sxs-lookup"><span data-stu-id="1530a-128">This tutorial shows an input scenario called [Put-That-There](https://youtu.be/CbIn8p4_4CQ) dating back to research from the MIT Media Lab in the early 1980's with eye, hand and voice input.</span></span>
<span data-ttu-id="1530a-129">思路非常简单：从眼睛中获益，实现快速目标选择和定位。</span><span class="sxs-lookup"><span data-stu-id="1530a-129">The idea is simple: Benefit from your eyes for fast target selection and positioning.</span></span>
<span data-ttu-id="1530a-130">只需查看一个全息图，说 _"放置此"_，就可以在想要放置它的位置寻找 _"！"_。</span><span class="sxs-lookup"><span data-stu-id="1530a-130">Simply look at a hologram and say _'put this'_, look over where you want to place it and say _'there!'_.</span></span>
<span data-ttu-id="1530a-131">为了更精确地定位全息图，你可以使用手中的其他输入、声音或控制器。</span><span class="sxs-lookup"><span data-stu-id="1530a-131">For more precisely positioning your hologram, you can use additional input from your hands, voice or controllers.</span></span>

<span data-ttu-id="1530a-132">**摘要**：使用眼睛、语音和手写输入 (*拖放*) 来定位全息影像。</span><span class="sxs-lookup"><span data-stu-id="1530a-132">**Summary**: Positioning holograms using eyes, voice and hand input (*drag-and-drop*).</span></span> <span data-ttu-id="1530a-133">使用眼睛和双手的眼睛支持的滑块。</span><span class="sxs-lookup"><span data-stu-id="1530a-133">Eye-supported sliders using eyes + hands.</span></span>

### <a name="visualization-of-visual-attention"></a><span data-ttu-id="1530a-134">**视觉对象视觉对象**</span><span class="sxs-lookup"><span data-stu-id="1530a-134">**Visualization of visual attention**</span></span>

<span data-ttu-id="1530a-135">基于用户所在位置的数据使极具强大的工具可评估设计的可用性，并识别高效工作流中的问题。</span><span class="sxs-lookup"><span data-stu-id="1530a-135">Data based on where users look makes an immensely powerful tool to assess usability of a design and to identify problems in efficient work streams.</span></span>
<span data-ttu-id="1530a-136">本教程介绍了不同的目视跟踪可视化效果，以及它们如何满足不同的需求。</span><span class="sxs-lookup"><span data-stu-id="1530a-136">This tutorial discusses different eye tracking visualizations and how they fit different needs.</span></span>
<span data-ttu-id="1530a-137">我们提供了用于记录和加载目视跟踪数据的基本示例，以及如何对其进行可视化的示例。</span><span class="sxs-lookup"><span data-stu-id="1530a-137">We provide basic examples for logging and loading eye tracking data and examples for how to visualize them.</span></span>

<span data-ttu-id="1530a-138">**摘要**：清单上 (热图) 的二维注意事项。</span><span class="sxs-lookup"><span data-stu-id="1530a-138">**Summary**: Two-dimensional attention map (heatmaps) on slates.</span></span> <span data-ttu-id="1530a-139">录制 & 重播目视跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="1530a-139">Recording & replaying eye tracking data.</span></span>

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a><span data-ttu-id="1530a-140">设置 MRTK 目视跟踪示例</span><span class="sxs-lookup"><span data-stu-id="1530a-140">Setting up the MRTK eye tracking samples</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1530a-141">先决条件</span><span class="sxs-lookup"><span data-stu-id="1530a-141">Prerequisites</span></span>

<span data-ttu-id="1530a-142">请注意，在设备上使用目视跟踪示例需要 HoloLens 2 和使用包的 appxmanifest.xml 上的 "注视输入" 功能生成的示例应用程序包。</span><span class="sxs-lookup"><span data-stu-id="1530a-142">Note that using the eye tracking samples on device requires a HoloLens 2 and a sample app package that is built with the "Gaze Input" capability on the package's AppXManifest.</span></span>

<span data-ttu-id="1530a-143">若要在设备上使用这些目视跟踪示例，请确保在 Visual Studio 中生成应用之前执行[以下步骤](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="1530a-143">In order to use these eye tracking samples on device, make sure to follow [these steps](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) prior to building the app in Visual Studio.</span></span>

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a><span data-ttu-id="1530a-144">1. Load EyeTrackingDemo-00-RootScene</span><span class="sxs-lookup"><span data-stu-id="1530a-144">1. Load EyeTrackingDemo-00-RootScene.unity</span></span>

<span data-ttu-id="1530a-145">*EyeTrackingDemo-00-RootScene* 是包含所有核心 MRTK 组件) 场景的基本 (_根_。</span><span class="sxs-lookup"><span data-stu-id="1530a-145">The *EyeTrackingDemo-00-RootScene* is the base (_root_) scene that has all the core MRTK components included.</span></span>
<span data-ttu-id="1530a-146">这是你首先需要加载的场景，你将在其中运行眼睛跟踪演示。</span><span class="sxs-lookup"><span data-stu-id="1530a-146">This is the scene that you need to load first and from which you will run the eye tracking demos.</span></span>
<span data-ttu-id="1530a-147">它具有图形场景菜单，可让你轻松地在将 [加载添加性地](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)的不同眼睛跟踪示例之间切换。</span><span class="sxs-lookup"><span data-stu-id="1530a-147">It features a graphical scene menu that allows you to easily switch between the different eye tracking samples which will be [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html).</span></span>

![目视跟踪示例中的场景菜单](../images/eye-tracking/mrtk_et_scenemenu.jpg)

<span data-ttu-id="1530a-149">根场景包括一些核心组件，这些组件将在添加性地加载的场景（如 MRTK 配置的配置文件和场景相机）之间保持。</span><span class="sxs-lookup"><span data-stu-id="1530a-149">The root scene includes a few core components that will persist across the additively loaded scenes, such as the MRTK configured profiles and scene camera.</span></span>
<span data-ttu-id="1530a-150">_MixedRealityBasicSceneSetup_ (参阅下面的屏幕截图) 包含一个脚本，该脚本将在启动时自动加载引用的场景。</span><span class="sxs-lookup"><span data-stu-id="1530a-150">The _MixedRealityBasicSceneSetup_ (see screenshot below) includes a script that will automatically load the referenced scene on startup.</span></span>
<span data-ttu-id="1530a-151">默认情况下，这是 _EyeTrackingDemo-TargetSelection_。</span><span class="sxs-lookup"><span data-stu-id="1530a-151">By default, this is _EyeTrackingDemo-02-TargetSelection_.</span></span>  

![OnLoadStartScene 脚本示例](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a><span data-ttu-id="1530a-153">2. 将场景添加到 "生成" 菜单</span><span class="sxs-lookup"><span data-stu-id="1530a-153">2. Adding scenes to the build menu</span></span>

<span data-ttu-id="1530a-154">若要在运行时加载附加场景，必须先将这些场景添加到 "生成" 菜单 _中设置 > "场景_。</span><span class="sxs-lookup"><span data-stu-id="1530a-154">To load additive scenes during runtime, you must add these scenes to your _Build Settings -> Scenes in Build_ menu first.</span></span>
<span data-ttu-id="1530a-155">根场景在列表中显示为第一个场景，这一点很重要：</span><span class="sxs-lookup"><span data-stu-id="1530a-155">It is important that the root scene is shown as the first scene in the list:</span></span>

![用于眼睛跟踪示例的 "构建设置场景" 菜单](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a><span data-ttu-id="1530a-157">3. 在 Unity 编辑器中播放眼睛跟踪示例</span><span class="sxs-lookup"><span data-stu-id="1530a-157">3. Play the eye tracking samples in the Unity editor</span></span>

<span data-ttu-id="1530a-158">将眼睛跟踪场景添加到生成设置并加载 _EyeTrackingDemo-00-RootScene_ 后，你可能需要检查的最后一件事是：是否已启用附加到 _MixedRealityBasicSceneSetup_ GameObject 的 _"OnLoadStartScene"_ 脚本？</span><span class="sxs-lookup"><span data-stu-id="1530a-158">After adding the eye tracking scenes to the Build Settings and loading the _EyeTrackingDemo-00-RootScene_, there is one last thing you may want to check: Is the _'OnLoadStartScene'_ script that is attached to the _MixedRealityBasicSceneSetup_ GameObject enabled?</span></span> <span data-ttu-id="1530a-159">这是为了让根场景知道要首先加载哪个演示场景。</span><span class="sxs-lookup"><span data-stu-id="1530a-159">This is to let the root scene know which demo scene to load first.</span></span>

![OnLoad_StartScene 脚本的示例](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

<span data-ttu-id="1530a-161">让我们开始吧！</span><span class="sxs-lookup"><span data-stu-id="1530a-161">Let's roll!</span></span> <span data-ttu-id="1530a-162">点击 _"播放"_！</span><span class="sxs-lookup"><span data-stu-id="1530a-162">Hit _"Play"_!</span></span>
<span data-ttu-id="1530a-163">此时会显示多个宝物，屏幕顶部会显示场景菜单。</span><span class="sxs-lookup"><span data-stu-id="1530a-163">You should see several gems appear and the scene menu at the top.</span></span>

![ET 目标选择场景中的示例屏幕截图](../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="1530a-165">你还应注意到游戏视图中心的小半透明圆圈。</span><span class="sxs-lookup"><span data-stu-id="1530a-165">You should also notice a small semitransparent circle at the center of your game view.</span></span>
<span data-ttu-id="1530a-166">这作为 _模拟眼睛_ (光标) 的指示器：只需按下鼠标 _右键_ ，然后移动鼠标更改其位置。</span><span class="sxs-lookup"><span data-stu-id="1530a-166">This acts as an indicator (cursor) of your _simulated eye gaze_: Simply press down the _right mouse button_ and move the mouse to change its position.</span></span>
<span data-ttu-id="1530a-167">当光标悬停在 gem 上时，您会注意到它将与当前查看的 gem 的中心对齐。</span><span class="sxs-lookup"><span data-stu-id="1530a-167">When the cursor is hovering over the gems, you will notice that it will snap to the center of the currently viewed gem.</span></span>
<span data-ttu-id="1530a-168">这是一种很好的方法，可用于测试在目标 _"查找"_ 时是否按预期触发事件。</span><span class="sxs-lookup"><span data-stu-id="1530a-168">This is a great way to test if events are triggered as expected when _"looking"_ at a target.</span></span>
<span data-ttu-id="1530a-169">请注意，通过鼠标控制的 _模拟眼睛_ 看不太太好了我们的快速和意外的眼睛运动。</span><span class="sxs-lookup"><span data-stu-id="1530a-169">Be aware that the _simulated eye gaze_ via mouse control is a rather poor supplement to our rapid and unintentional eye movements.</span></span>
<span data-ttu-id="1530a-170">不过，它非常适合于测试基本功能，然后再通过将其部署到 HoloLens 2 设备来循环访问设计。</span><span class="sxs-lookup"><span data-stu-id="1530a-170">However, it is great for testing the basic functionality before iterating on the design by deploying it to the HoloLens 2 device.</span></span>
<span data-ttu-id="1530a-171">返回到我们的眼睛跟踪示例场景：只要查看并可通过 "查看" 来销毁 gem，gem 就会旋转 .。。</span><span class="sxs-lookup"><span data-stu-id="1530a-171">Returning to our eye tracking sample scene: The gem rotates as long as being looked at and can be destroyed by "looking" at it and ...</span></span>

- <span data-ttu-id="1530a-172">按 _enter_ (模拟口述 "select" ) </span><span class="sxs-lookup"><span data-stu-id="1530a-172">Pressing _Enter_ (which simulates saying "select")</span></span>
- <span data-ttu-id="1530a-173">说 _"选择"_ 到麦克风</span><span class="sxs-lookup"><span data-stu-id="1530a-173">Saying _"select"_ into your microphone</span></span>
- <span data-ttu-id="1530a-174">按 _空格键_ 显示模拟手写输入时，请单击鼠标左键以执行模拟的挤压</span><span class="sxs-lookup"><span data-stu-id="1530a-174">While pressing _Space_ to show the simulated hand input, click the left mouse button to perform a simulated pinch</span></span>

<span data-ttu-id="1530a-175">我们更详细地介绍了如何在 [**目视支持的目标选择**](../input/eye-tracking/eye-tracking-target-selection.md) 教程中实现这些交互。</span><span class="sxs-lookup"><span data-stu-id="1530a-175">We describe in more detail how you can achieve these interactions in our [**Eye-Supported Target Selection**](../input/eye-tracking/eye-tracking-target-selection.md) tutorial.</span></span>

<span data-ttu-id="1530a-176">将光标上移到场景中的顶部菜单栏时，你会注意到当前悬停的项将会有变化。</span><span class="sxs-lookup"><span data-stu-id="1530a-176">When moving the cursor up to the top menu bar in the scene, you will notice that the currently hovered item will highlight subtly.</span></span>
<span data-ttu-id="1530a-177">您可以使用以上所述的提交方法之一来选择当前突出显示的项 (例如，按 _enter_) 。</span><span class="sxs-lookup"><span data-stu-id="1530a-177">You can select the currently highlighted item by using one of the above described commit methods (e.g., pressing _Enter_).</span></span>
<span data-ttu-id="1530a-178">这样，便可以在不同的目视跟踪示例场景之间切换。</span><span class="sxs-lookup"><span data-stu-id="1530a-178">This way you can switch between the different eye tracking sample scenes.</span></span>

### <a name="4-how-to-test-specific-sub-scenes"></a><span data-ttu-id="1530a-179">4. 如何测试特定的子场景</span><span class="sxs-lookup"><span data-stu-id="1530a-179">4. How to test specific sub scenes</span></span>

<span data-ttu-id="1530a-180">处理特定方案时，您可能不希望每次都浏览场景菜单。</span><span class="sxs-lookup"><span data-stu-id="1530a-180">When working on a specific scenario, you may not want to go through the scene menu every time.</span></span>
<span data-ttu-id="1530a-181">相反，你可能想要直接从当前正在处理的场景开始，按下 " _播放_ " 按钮。</span><span class="sxs-lookup"><span data-stu-id="1530a-181">Instead, you may want to start directly from the scene that you are currently working on when pressing the _Play_ button.</span></span>
<span data-ttu-id="1530a-182">没问题！</span><span class="sxs-lookup"><span data-stu-id="1530a-182">No problem!</span></span> <span data-ttu-id="1530a-183">下面是你可以执行的操作：</span><span class="sxs-lookup"><span data-stu-id="1530a-183">Here is what you can do:</span></span>

1. <span data-ttu-id="1530a-184">加载 _根_ 场景</span><span class="sxs-lookup"><span data-stu-id="1530a-184">Load the _root_ scene</span></span>
2. <span data-ttu-id="1530a-185">在 _根_ 场景中，禁用 _"OnLoadStartScene"_ 脚本</span><span class="sxs-lookup"><span data-stu-id="1530a-185">In the _root_ scene, disable the _'OnLoadStartScene'_ script</span></span>
3. <span data-ttu-id="1530a-186">将下面所述的眼睛跟踪测试场景之一 _拖放_ (或任何其他场景) 到 _层次结构_ 视图中，如下面的屏幕截图中所示。</span><span class="sxs-lookup"><span data-stu-id="1530a-186">_Drag and drop_ one of the eye tracking test scenes that are described below (or any other scene) into your _Hierarchy_ view as shown in the screenshot below.</span></span>

    ![加法场景示例](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. <span data-ttu-id="1530a-188">按下 _播放_</span><span class="sxs-lookup"><span data-stu-id="1530a-188">Press _Play_</span></span>

<span data-ttu-id="1530a-189">请注意，加载这样的子场景不是永久性的：这意味着，如果将应用程序部署到 HoloLens 2 设备，则它将只加载根场景 (，因为它会出现在生成设置) 的顶部。</span><span class="sxs-lookup"><span data-stu-id="1530a-189">Please note that loading the sub scene like this is not persistent: This means that if you deploy your app to the HoloLens 2 device, it will only load the root scene (assuming it appears at the top of your Build Settings).</span></span>
<span data-ttu-id="1530a-190">此外，当你与他人共享你的项目时，不会自动加载子场景。</span><span class="sxs-lookup"><span data-stu-id="1530a-190">Also, when you share your project with others, the sub scenes are not automatically loaded.</span></span>

---

<span data-ttu-id="1530a-191">现在，你已了解如何让 MRTK 目视跟踪示例场景工作，接下来让我们进一步深入了解如何选择你的眼睛： [目视支持的目标选择](../input/eye-tracking/eye-tracking-target-selection.md)。</span><span class="sxs-lookup"><span data-stu-id="1530a-191">Now that you know how to get the MRTK eye tracking example scenes to work, let's continue with diving deeper into how to select holograms with your eyes: [Eye-supported target selection](../input/eye-tracking/eye-tracking-target-selection.md).</span></span>

---
[<span data-ttu-id="1530a-192">返回 "MixedRealityToolkit" 中的眼睛跟踪</span><span class="sxs-lookup"><span data-stu-id="1530a-192">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](../input/eye-tracking/eye-tracking-Main.md)
