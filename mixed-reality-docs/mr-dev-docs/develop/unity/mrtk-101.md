---
title: MRTK 101 - 使用通用空间交互
description: 对于 HoloLens 2、HoloLens、Windows Mixed Reality 和 Open VR，如何使用混合现实工具包 Unity 进行基本的交互。
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, 混合现实工具包, Windows Mixed Reality, 设计, 示例应用, 控件, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.localizationpriority: high
ms.openlocfilehash: ff3c6e055bca66fc5ad12548966140af8197235c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008937"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a><span data-ttu-id="80aa7-104">MRTK 101：如何使用混合现实工具包 Unity 进行常见的空间交互</span><span class="sxs-lookup"><span data-stu-id="80aa7-104">MRTK 101: How to use Mixed Reality Toolkit Unity for common spatial interactions</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="80aa7-106">了解如何使用 MRTK 在混合现实中实现最常用的交互模式。</span><span class="sxs-lookup"><span data-stu-id="80aa7-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="80aa7-107">如何在 Unity 编辑器中模拟输入交互？</span><span class="sxs-lookup"><span data-stu-id="80aa7-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="80aa7-108">如何抓取和移动对象？</span><span class="sxs-lookup"><span data-stu-id="80aa7-108">How to grab and move an object?</span></span>
- <span data-ttu-id="80aa7-109">如何调整对象的大小？</span><span class="sxs-lookup"><span data-stu-id="80aa7-109">How to resize an object?</span></span>
- <span data-ttu-id="80aa7-110">如何精确移动或旋转对象？</span><span class="sxs-lookup"><span data-stu-id="80aa7-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="80aa7-111">如何使对象响应输入事件？</span><span class="sxs-lookup"><span data-stu-id="80aa7-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="80aa7-112">如何添加视觉反馈？</span><span class="sxs-lookup"><span data-stu-id="80aa7-112">How to add visual feedback?</span></span>
- <span data-ttu-id="80aa7-113">如何添加音频反馈？</span><span class="sxs-lookup"><span data-stu-id="80aa7-113">How to add audio feedback?</span></span>
- <span data-ttu-id="80aa7-114">如何使用 HoloLens 2 样式按钮预制件？</span><span class="sxs-lookup"><span data-stu-id="80aa7-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="80aa7-115">如何使对象跟随你？</span><span class="sxs-lookup"><span data-stu-id="80aa7-115">How to make an object follow you?</span></span>
- <span data-ttu-id="80aa7-116">如何使对象朝向你？</span><span class="sxs-lookup"><span data-stu-id="80aa7-116">How to make an object face you?</span></span>

> [!NOTE]
> <span data-ttu-id="80aa7-117">本文已经过更新，反映了 [MRTK v2.5.1 版本](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)中的更改</span><span class="sxs-lookup"><span data-stu-id="80aa7-117">This article has been updated to reflect the changes in [MRTK v2.5.1 release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span></span>

<span data-ttu-id="80aa7-118">本页中的所有内容都可在 Unity 中使用 MRTK 的输入模拟进行测试。</span><span class="sxs-lookup"><span data-stu-id="80aa7-118">All contents in this page can be tested in Unity editor with MRTK's Input Simulation.</span></span> <span data-ttu-id="80aa7-119">如果你还没有，可按照 [MRTK 安装指南 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 安装最新版本的 MRTK。</span><span class="sxs-lookup"><span data-stu-id="80aa7-119">If you haven't, follow [MRTK Installation Guide (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) to install the latest version of MRTK.</span></span>

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a><span data-ttu-id="80aa7-120">如何在 Unity 编辑器中模拟输入交互？</span><span class="sxs-lookup"><span data-stu-id="80aa7-120">How to simulate input interactions in Unity editor?</span></span>

<span data-ttu-id="80aa7-121">MRTK 支持编辑器中的输入模拟。</span><span class="sxs-lookup"><span data-stu-id="80aa7-121">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="80aa7-122">单击 Unity 的播放按钮以运行场景，然后使用以下按键来模拟输入：</span><span class="sxs-lookup"><span data-stu-id="80aa7-122">Run your scene by clicking Unity's play button, then use the following keys to simulate input:</span></span>
- <span data-ttu-id="80aa7-123">按 W、A、S、D 键可移动相机。</span><span class="sxs-lookup"><span data-stu-id="80aa7-123">Press W, A, S, D keys to move the camera.</span></span>
- <span data-ttu-id="80aa7-124">在按住鼠标右键的同时移动鼠标可以四处浏览。</span><span class="sxs-lookup"><span data-stu-id="80aa7-124">Hold the right mouse button and move the mouse to look around.</span></span>
- <span data-ttu-id="80aa7-125">按空格键（右手）或左 Shift 键（左手）以显示模拟双手</span><span class="sxs-lookup"><span data-stu-id="80aa7-125">Press Space bar(Right hand) or left Shift key(Left hand) to bring up the simulated hands</span></span>
- <span data-ttu-id="80aa7-126">按 T 或 Y 键以将模拟双手保持在视野中</span><span class="sxs-lookup"><span data-stu-id="80aa7-126">Press T or Y keys to keep simulated hands in view</span></span>
- <span data-ttu-id="80aa7-127">按 Q 或 E（水平）/R 或 F（垂直）来旋转模拟双手</span><span class="sxs-lookup"><span data-stu-id="80aa7-127">Press Q or E(horizontal) / R or F(vertical) to rotate simulated hands</span></span>

<span data-ttu-id="80aa7-128">可以在 [MRTK 文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)中详细了解输入模拟。</span><span class="sxs-lookup"><span data-stu-id="80aa7-128">You can learn more about Input Simulation in the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).</span></span>

## <a name="how-to-grab-and-move-an-object"></a><span data-ttu-id="80aa7-129">如何抓取和移动对象？</span><span class="sxs-lookup"><span data-stu-id="80aa7-129">How to grab and move an object?</span></span>

<span data-ttu-id="80aa7-130">附加 ObjectManipulator.cs 和 NearInteractionGrabbable.cs 脚本，使对象可抓取 。</span><span class="sxs-lookup"><span data-stu-id="80aa7-130">Attach the **ObjectManipulator.cs** and **NearInteractionGrabbable.cs** scripts to make an object grabbable.</span></span> <span data-ttu-id="80aa7-131">ObjectManipulator 支持近距离和远距离交互。</span><span class="sxs-lookup"><span data-stu-id="80aa7-131">ObjectManipulator supports both near and far interactions.</span></span> <span data-ttu-id="80aa7-132">可以使用 HoloLens 2 的精确手动跟踪输入（近距）、手部射线（远距）、运动控制器光束（远距）、HoloLens 凝视光标和隔空敲击（远距）来抓取和移动对象。</span><span class="sxs-lookup"><span data-stu-id="80aa7-132">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), and HoloLens gaze cursor and air-tap(far).</span></span>

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a><span data-ttu-id="80aa7-133">如何调整对象的大小？</span><span class="sxs-lookup"><span data-stu-id="80aa7-133">How to resize an object?</span></span>
<span data-ttu-id="80aa7-134">ObjectManipulator.cs 支持双手缩放/旋转。</span><span class="sxs-lookup"><span data-stu-id="80aa7-134">**ObjectManipulator.cs** supports two-handed scale/rotation.</span></span> <span data-ttu-id="80aa7-135">此脚本适用于各种输入类型，例如 HoloLens 2 的精确手动输入、HoloLens 1 的凝视 + 手势输入，以及 Windows Mixed Reality 沉浸式头戴显示设备的运动控制器输入。</span><span class="sxs-lookup"><span data-stu-id="80aa7-135">The script works with various input types, such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="80aa7-136">在 MRTK 文档中详细了解对象处理程序</span><span class="sxs-lookup"><span data-stu-id="80aa7-136">Learn more about Object Manipulator in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="80aa7-137">如何精确移动或旋转对象？</span><span class="sxs-lookup"><span data-stu-id="80aa7-137">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="80aa7-138">将 BoundsControl.cs 分配到某个对象以使用边界框（用于缩放和旋转对象的界面）。</span><span class="sxs-lookup"><span data-stu-id="80aa7-138">Assign **BoundsControl.cs** to an object to use Bounding Box, which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="80aa7-139">默认情况下，该脚本会显示 HoloLens 1 样式的蓝色控点和线条。</span><span class="sxs-lookup"><span data-stu-id="80aa7-139">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="80aa7-140">若要使用基于 HoloLens 2 样式邻近性的动画控点，需要分配预制件和材料。</span><span class="sxs-lookup"><span data-stu-id="80aa7-140">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [<span data-ttu-id="80aa7-141">在 MRTK 文档中详细了解边界控制</span><span class="sxs-lookup"><span data-stu-id="80aa7-141">Learn more about Bounds Control in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a><span data-ttu-id="80aa7-142">如何使对象响应输入事件？</span><span class="sxs-lookup"><span data-stu-id="80aa7-142">How to make an object respond to input events?</span></span>
<span data-ttu-id="80aa7-143">将 PointerHandler.cs 分配到某个对象。</span><span class="sxs-lookup"><span data-stu-id="80aa7-143">Assign **PointerHandler.cs** to an object.</span></span> <span data-ttu-id="80aa7-144">在检查器中，可使用事件 OnPointerDown()、OnPointerUp()、OnPointerClicked() 和 OnPointerDragged()。若要在脚本中使用这些事件，请实现 IMixedRealityPointerHandler。</span><span class="sxs-lookup"><span data-stu-id="80aa7-144">In the inspector, you can use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement **IMixedRealityPointerHandler**.</span></span>

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="80aa7-145">在 MRTK 文档中详细了解输入系统</span><span class="sxs-lookup"><span data-stu-id="80aa7-145">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="80aa7-146">如何添加视觉反馈？</span><span class="sxs-lookup"><span data-stu-id="80aa7-146">How to add visual feedback?</span></span>
<span data-ttu-id="80aa7-147">将 Interactable.cs 分配到某个对象。</span><span class="sxs-lookup"><span data-stu-id="80aa7-147">Assign **Interactable.cs** to an object.</span></span> <span data-ttu-id="80aa7-148">在检查器中，添加目标对象并创建新主题。</span><span class="sxs-lookup"><span data-stu-id="80aa7-148">In the inspector, add target object and create a new theme.</span></span> <span data-ttu-id="80aa7-149">使用 Interactable 的主题配置文件可以轻松将视觉反馈添加到所有可用的输入交互状态。</span><span class="sxs-lookup"><span data-stu-id="80aa7-149">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="80aa7-150">Interactable 提供各种类型的主题，包括着色器主题，该主题可用于控制每种交互状态的着色器的属性。</span><span class="sxs-lookup"><span data-stu-id="80aa7-150">Interactable provides various types of themes including the shader theme, which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="80aa7-151">在 MRTK 文档中详细了解 Interactable</span><span class="sxs-lookup"><span data-stu-id="80aa7-151">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="80aa7-152">视觉反馈的另一个重要构建基块是 MRTK 标准着色器。</span><span class="sxs-lookup"><span data-stu-id="80aa7-152">Another important building block for visual feedback is the **MRTK Standard Shader**.</span></span> <span data-ttu-id="80aa7-153">使用 MRTK 标准着色器可以轻松添加视觉反馈效果，例如悬停光线和邻近光线。</span><span class="sxs-lookup"><span data-stu-id="80aa7-153">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="80aa7-154">由于 MRTK 标准着色器占用的计算资源要比 Unity 标准着色器少，因此你可以创建高性能的体验。</span><span class="sxs-lookup"><span data-stu-id="80aa7-154">Since MRTK Standard shader performs less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="80aa7-155">创建新材料，然后选择着色器的“混合现实工具包”>“标准”。</span><span class="sxs-lookup"><span data-stu-id="80aa7-155">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="80aa7-156">或者，可以选择某个使用 MRTK 标准着色器的现有材料。</span><span class="sxs-lookup"><span data-stu-id="80aa7-156">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="80aa7-157">在 MRTK 文档中详细了解 MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="80aa7-157">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="80aa7-158">如何添加音频反馈？</span><span class="sxs-lookup"><span data-stu-id="80aa7-158">How to add audio feedback?</span></span>
<span data-ttu-id="80aa7-159">将 AudioSource 添加到某个对象。</span><span class="sxs-lookup"><span data-stu-id="80aa7-159">Add **AudioSource** to an object.</span></span> <span data-ttu-id="80aa7-160">然后，在公开输入事件的脚本（例如 Interactable.cs 或 PointerHandler.cs）中，将带有 AudioSource 的对象分配到该事件，并选择 AudioSource.PlayOneShot()。</span><span class="sxs-lookup"><span data-stu-id="80aa7-160">Then, in the scripts that expose input events(e.g. Interactable.cs or PointerHandler.cs), assign the object with AudioSource to the event and select **AudioSource.PlayOneShot()**.</span></span> <span data-ttu-id="80aa7-161">可以使用自己的音频剪辑，或从 MRTK 的音频资产中进行选择。</span><span class="sxs-lookup"><span data-stu-id="80aa7-161">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a><span data-ttu-id="80aa7-162">如何使用 HoloLens 2 样式按钮预制件？</span><span class="sxs-lookup"><span data-stu-id="80aa7-162">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="80aa7-163">MRTK 提供了各种类型的 HoloLens 2 shell (OS) 样式按钮，包括邻近感应光、压缩框和按钮表面的波纹效果等视觉反馈，可增强用户的信心。</span><span class="sxs-lookup"><span data-stu-id="80aa7-163">MRTK provides various types of HoloLens 2's shell (OS) style buttons, including visual feedback like proximity light, compressing box, and a ripple effect on the button surface that improve the user's confidence.</span></span>

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="80aa7-164">将某个 HoloLens 2 样式的可按按钮预制件拖放到场景中即可。</span><span class="sxs-lookup"><span data-stu-id="80aa7-164">Drag and drop one of the **HoloLens 2 style pressable button prefab** into your scene.</span></span> <span data-ttu-id="80aa7-165">该预制件将使用前面介绍的 Interactable.cs。</span><span class="sxs-lookup"><span data-stu-id="80aa7-165">The prefab uses Interactable.cs introduced above.</span></span> <span data-ttu-id="80aa7-166">可以使用 Interactable 中公开的事件（例如 OnClick()）来触发操作。</span><span class="sxs-lookup"><span data-stu-id="80aa7-166">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="80aa7-167">在 MRTK 文档中详细了解按钮预制件</span><span class="sxs-lookup"><span data-stu-id="80aa7-167">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a><span data-ttu-id="80aa7-168">如何使对象跟随你？</span><span class="sxs-lookup"><span data-stu-id="80aa7-168">How to make an object follow you?</span></span>
<span data-ttu-id="80aa7-169">将 RadialView.cs 或 Follow.cs 脚本分配到某个对象 。</span><span class="sxs-lookup"><span data-stu-id="80aa7-169">Assign **RadialView.cs** or **Follow.cs** script to an object.</span></span> <span data-ttu-id="80aa7-170">此脚本是解算器脚本系列的一部分，可用于在 3D 空间中实现各种类型的对象定位。</span><span class="sxs-lookup"><span data-stu-id="80aa7-170">It's part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="80aa7-171">将自动添加 SolverHandler.cs。</span><span class="sxs-lookup"><span data-stu-id="80aa7-171">**SolverHandler.cs** will be automatically added.</span></span>
<span data-ttu-id="80aa7-172">下面是 RadialView 配置的一个示例，它可以实现“惰性跟踪”追随行为，就如同使用 HoloLens shell 中的“开始”菜单一样。</span><span class="sxs-lookup"><span data-stu-id="80aa7-172">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="80aa7-173">可以指定最小/最大距离和最小/最大视图角度。</span><span class="sxs-lookup"><span data-stu-id="80aa7-173">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="80aa7-174">以下示例演示如何在 0.4 到 0.8 米范围内以 15° 的视图角度定位对象。</span><span class="sxs-lookup"><span data-stu-id="80aa7-174">The example below shows positioning the object between 0.4 m and 0.8-m range within 15°.</span></span> <span data-ttu-id="80aa7-175">调整“线性插值时间”值，以加快或减慢定位更新的速度。</span><span class="sxs-lookup"><span data-stu-id="80aa7-175">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="80aa7-176">在 MRTK 文档中详细了解解算器</span><span class="sxs-lookup"><span data-stu-id="80aa7-176">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a><span data-ttu-id="80aa7-177">如何使对象朝向你？</span><span class="sxs-lookup"><span data-stu-id="80aa7-177">How to make an object face you?</span></span>
<span data-ttu-id="80aa7-178">将 Billboard.cs 脚本分配到某个对象。</span><span class="sxs-lookup"><span data-stu-id="80aa7-178">Assign **Billboard.cs** script to an object.</span></span> <span data-ttu-id="80aa7-179">不管你处于哪个位置，该对象都会朝向你。</span><span class="sxs-lookup"><span data-stu-id="80aa7-179">It will always face you, whatever your position.</span></span> <span data-ttu-id="80aa7-180">可以指定枢轴选项。</span><span class="sxs-lookup"><span data-stu-id="80aa7-180">You can specify the pivot axis option.</span></span>

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="80aa7-181">准备好创建令人惊叹的混合现实体验了吗？</span><span class="sxs-lookup"><span data-stu-id="80aa7-181">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="80aa7-182">请访问以下页面来详细了解 MRTK 和混合现实。</span><span class="sxs-lookup"><span data-stu-id="80aa7-182">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="80aa7-183">关于作者</span><span class="sxs-lookup"><span data-stu-id="80aa7-183">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="80aa7-184"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="80aa7-184"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="80aa7-185">用户体验设计师 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="80aa7-185">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="next-development-checkpoint"></a><span data-ttu-id="80aa7-186">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="80aa7-186">Next Development Checkpoint</span></span>

<span data-ttu-id="80aa7-187">如果遵循我们规划的 Unity 的开发检查点旅程，则你在探索 MRTK 核心构建基块的过程中。</span><span class="sxs-lookup"><span data-stu-id="80aa7-187">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="80aa7-188">从这里，你可以继续了解下一部分基础知识：</span><span class="sxs-lookup"><span data-stu-id="80aa7-188">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="80aa7-189">摄像头</span><span class="sxs-lookup"><span data-stu-id="80aa7-189">Camera</span></span>](camera-in-unity.md)

<span data-ttu-id="80aa7-190">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="80aa7-190">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="80aa7-191">共享体验</span><span class="sxs-lookup"><span data-stu-id="80aa7-191">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="80aa7-192">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="80aa7-192">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="80aa7-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="80aa7-193">See also</span></span>
* [<span data-ttu-id="80aa7-194">MRTK 安装指南 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="80aa7-194">MRTK Installation Guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="80aa7-195">混合现实工具包 - Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="80aa7-195">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="80aa7-196">MRTK 文档门户 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="80aa7-196">MRTK Documentation Portal (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="80aa7-197">HoloToolkit 到 MRTK 的移植指南</span><span class="sxs-lookup"><span data-stu-id="80aa7-197">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
