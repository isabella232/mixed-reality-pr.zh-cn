---
title: MRTK 101 - 如何使用混合现实工具包 Unity 进行常见的空间交互（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）
description: 如何使用混合现实工具包 Unity 进行基本的交互（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, 混合现实工具包, Windows Mixed Reality, 设计, 示例应用, 控件
ms.localizationpriority: high
ms.openlocfilehash: d10de5c9f16e0caa289d5110647b4c45a8a8fcf9
ms.sourcegitcommit: 83c9373fe5b2e07cdab921b6cab3fdd418307003
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2020
ms.locfileid: "94386261"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a><span data-ttu-id="42eec-104">MRTK 101：如何使用混合现实工具包 Unity 进行常见的空间交互</span><span class="sxs-lookup"><span data-stu-id="42eec-104">MRTK 101: How to use Mixed Reality Toolkit Unity for common spatial interactions</span></span>
![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="42eec-106">了解如何使用 MRTK 在混合现实中实现最常用的交互模式。</span><span class="sxs-lookup"><span data-stu-id="42eec-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="42eec-107">如何在 Unity 编辑器中模拟输入交互？</span><span class="sxs-lookup"><span data-stu-id="42eec-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="42eec-108">如何抓取和移动对象？</span><span class="sxs-lookup"><span data-stu-id="42eec-108">How to grab and move an object?</span></span>
- <span data-ttu-id="42eec-109">如何调整对象的大小？</span><span class="sxs-lookup"><span data-stu-id="42eec-109">How to resize an object?</span></span>
- <span data-ttu-id="42eec-110">如何精确移动或旋转对象？</span><span class="sxs-lookup"><span data-stu-id="42eec-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="42eec-111">如何使对象响应输入事件？</span><span class="sxs-lookup"><span data-stu-id="42eec-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="42eec-112">如何添加视觉反馈？</span><span class="sxs-lookup"><span data-stu-id="42eec-112">How to add visual feedback?</span></span>
- <span data-ttu-id="42eec-113">如何添加音频反馈？</span><span class="sxs-lookup"><span data-stu-id="42eec-113">How to add audio feedback?</span></span>
- <span data-ttu-id="42eec-114">如何使用 HoloLens 2 样式按钮预制件？</span><span class="sxs-lookup"><span data-stu-id="42eec-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="42eec-115">如何使对象跟随你？</span><span class="sxs-lookup"><span data-stu-id="42eec-115">How to make an object follow you?</span></span>
- <span data-ttu-id="42eec-116">如何使对象朝向你？</span><span class="sxs-lookup"><span data-stu-id="42eec-116">How to make an object face you?</span></span>

> [!NOTE]
> <span data-ttu-id="42eec-117">本文已经过更新，反映了 [MRTK v2.5.1 版本](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)中的更改</span><span class="sxs-lookup"><span data-stu-id="42eec-117">This article has been updated to reflect the changes in [MRTK v2.5.1 release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span></span>

<span data-ttu-id="42eec-118">本页中的所有内容都可在 Unity 中使用 MRTK 的输入模拟进行测试。</span><span class="sxs-lookup"><span data-stu-id="42eec-118">All contents in this page can be tested in Unity editor with MRTK's Input Simulation.</span></span> <span data-ttu-id="42eec-119">如果你还没有，可按照 [MRTK 安装指南 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 安装最新版本的 MRTK。</span><span class="sxs-lookup"><span data-stu-id="42eec-119">If you haven't, follow [MRTK Installation Guide (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) to install the latest version of MRTK.</span></span>

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a><span data-ttu-id="42eec-120">如何在 Unity 编辑器中模拟输入交互？</span><span class="sxs-lookup"><span data-stu-id="42eec-120">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="42eec-121">MRTK 支持编辑器中的输入模拟。</span><span class="sxs-lookup"><span data-stu-id="42eec-121">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="42eec-122">只需单击 Unity 的播放按钮即可运行场景。</span><span class="sxs-lookup"><span data-stu-id="42eec-122">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="42eec-123">请使用这些键来模拟输入。</span><span class="sxs-lookup"><span data-stu-id="42eec-123">Use these keys to simulate input.</span></span>
<span data-ttu-id="42eec-124">按 W、A、S、D 键可移动相机。</span><span class="sxs-lookup"><span data-stu-id="42eec-124">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="42eec-125">在按住鼠标右键的同时移动鼠标可以四处浏览。</span><span class="sxs-lookup"><span data-stu-id="42eec-125">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="42eec-126">若要显示模拟手形图标，请按空格键（右手）或左 Shift 键（左手）。若要在视图中保留模拟手形图标，请按 T 或 Y 键。若要旋转模拟手形图标，请按 Q 或 E（水平旋转）/R 或 F（垂直旋转）</span><span class="sxs-lookup"><span data-stu-id="42eec-126">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="42eec-127">在 MRTK 文档中详细了解输入模拟</span><span class="sxs-lookup"><span data-stu-id="42eec-127">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-an-object"></a><span data-ttu-id="42eec-128">如何抓取和移动对象？</span><span class="sxs-lookup"><span data-stu-id="42eec-128">How to grab and move an object?</span></span>
<span data-ttu-id="42eec-129">若要使对象可抓取，请分配以下两个脚本：ObjectManipulator.cs 和 NearInteractionGrabbable.cs （根据精确手动跟踪输入直接抓取）ObjectManipulator 支持近距交互和远距交互 。</span><span class="sxs-lookup"><span data-stu-id="42eec-129">To make an object grabbable, assign these two scripts: **ObjectManipulator.cs** and **NearInteractionGrabbable.cs** (for direct grab with articulated hand tracking input) ObjectManipulator supports both near and far interactions.</span></span> <span data-ttu-id="42eec-130">可以使用 HoloLens 2 的精确手动跟踪输入（近距）、手部射线（远距）、运动控制器光束（远距）、HoloLens 凝视光标和隔空敲击（远距）来抓取和移动对象。</span><span class="sxs-lookup"><span data-stu-id="42eec-130">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a><span data-ttu-id="42eec-131">如何调整对象的大小？</span><span class="sxs-lookup"><span data-stu-id="42eec-131">How to resize an object?</span></span>
<span data-ttu-id="42eec-132">ObjectManipulator.cs 支持双手缩放/旋转。</span><span class="sxs-lookup"><span data-stu-id="42eec-132">**ObjectManipulator.cs** supports two-handed scale/rotation.</span></span> <span data-ttu-id="42eec-133">此功能适用于各种输入类型，例如 HoloLens 2 的精确手动输入、HoloLens 1 的凝视 + 手势输入，以及 Windows Mixed Reality 沉浸式头戴显示设备的运动控制器输入。</span><span class="sxs-lookup"><span data-stu-id="42eec-133">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="42eec-134">在 MRTK 文档中详细了解对象处理程序</span><span class="sxs-lookup"><span data-stu-id="42eec-134">Learn more about Object Manipulator in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="42eec-135">如何精确移动或旋转对象？</span><span class="sxs-lookup"><span data-stu-id="42eec-135">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="42eec-136">将 BoundsControl.cs 分配到某个对象以使用边界框（用于缩放和旋转对象的界面）。</span><span class="sxs-lookup"><span data-stu-id="42eec-136">Assign **BoundsControl.cs** to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="42eec-137">默认情况下，该脚本会显示 HoloLens 1 样式的蓝色控点和线条。</span><span class="sxs-lookup"><span data-stu-id="42eec-137">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="42eec-138">若要使用基于 HoloLens 2 样式邻近性的动画控点，需要分配预制件和材料。</span><span class="sxs-lookup"><span data-stu-id="42eec-138">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [<span data-ttu-id="42eec-139">在 MRTK 文档中详细了解边界控制</span><span class="sxs-lookup"><span data-stu-id="42eec-139">Learn more about Bounds Control in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a><span data-ttu-id="42eec-140">如何使对象响应输入事件？</span><span class="sxs-lookup"><span data-stu-id="42eec-140">How to make an object respond to input events?</span></span>
<span data-ttu-id="42eec-141">将 PointerHandler.cs 分配到某个对象。</span><span class="sxs-lookup"><span data-stu-id="42eec-141">Assign **PointerHandler.cs** to an object.</span></span> <span data-ttu-id="42eec-142">在检查器中，可使用事件 OnPointerDown()、OnPointerUp()、OnPointerClicked() 和 OnPointerDragged()。若要在脚本中使用这些事件，请实现 IMixedRealityPointerHandler。</span><span class="sxs-lookup"><span data-stu-id="42eec-142">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement **IMixedRealityPointerHandler**.</span></span>

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="42eec-143">在 MRTK 文档中详细了解输入系统</span><span class="sxs-lookup"><span data-stu-id="42eec-143">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="42eec-144">如何添加视觉反馈？</span><span class="sxs-lookup"><span data-stu-id="42eec-144">How to add visual feedback?</span></span>
<span data-ttu-id="42eec-145">将 Interactable.cs 分配到某个对象。</span><span class="sxs-lookup"><span data-stu-id="42eec-145">Assign **Interactable.cs** to an object.</span></span> <span data-ttu-id="42eec-146">在检查器中，添加目标对象并创建新主题。</span><span class="sxs-lookup"><span data-stu-id="42eec-146">In the inspector, add target object and create a new theme.</span></span> <span data-ttu-id="42eec-147">使用 Interactable 的主题配置文件可以轻松将视觉反馈添加到所有可用的输入交互状态。</span><span class="sxs-lookup"><span data-stu-id="42eec-147">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="42eec-148">Interactable 提供各种类型的主题，包括着色器主题，该主题可用于控制每种交互状态的着色器的属性。</span><span class="sxs-lookup"><span data-stu-id="42eec-148">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="42eec-149">在 MRTK 文档中详细了解 Interactable</span><span class="sxs-lookup"><span data-stu-id="42eec-149">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="42eec-150">视觉反馈的另一个重要构建基块是 MRTK 标准着色器。</span><span class="sxs-lookup"><span data-stu-id="42eec-150">Another important building block for visual feedback is the **MRTK Standard Shader**.</span></span> <span data-ttu-id="42eec-151">使用 MRTK 标准着色器可以轻松添加视觉反馈效果，例如悬停光线和邻近光线。</span><span class="sxs-lookup"><span data-stu-id="42eec-151">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="42eec-152">由于 MRTK 标准着色器占用的计算资源要比 Unity 标准着色器少得多，因此你可以创建高性能的体验。</span><span class="sxs-lookup"><span data-stu-id="42eec-152">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="42eec-153">创建新材料，然后选择着色器的“混合现实工具包”>“标准”。</span><span class="sxs-lookup"><span data-stu-id="42eec-153">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="42eec-154">或者，可以选择某个使用 MRTK 标准着色器的现有材料。</span><span class="sxs-lookup"><span data-stu-id="42eec-154">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="42eec-155">在 MRTK 文档中详细了解 MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="42eec-155">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="42eec-156">如何添加音频反馈？</span><span class="sxs-lookup"><span data-stu-id="42eec-156">How to add audio feedback?</span></span>
<span data-ttu-id="42eec-157">将 AudioSource 添加到某个对象。</span><span class="sxs-lookup"><span data-stu-id="42eec-157">Add **AudioSource** to an object.</span></span> <span data-ttu-id="42eec-158">然后，在公开输入事件的脚本（例如 Interactable.cs 或 PointerHandler.cs）中，将带有 AudioSource 的对象分配到该事件，并选择 AudioSource.PlayOneShot()。</span><span class="sxs-lookup"><span data-stu-id="42eec-158">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object with AudioSource to the event and select **AudioSource.PlayOneShot()**.</span></span> <span data-ttu-id="42eec-159">可以使用自己的音频剪辑，或从 MRTK 的音频资产中进行选择。</span><span class="sxs-lookup"><span data-stu-id="42eec-159">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a><span data-ttu-id="42eec-160">如何使用 HoloLens 2 样式按钮预制件？</span><span class="sxs-lookup"><span data-stu-id="42eec-160">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="42eec-161">MRTK 提供各种类型的 HoloLens 2 shell (OS) 样式按钮。</span><span class="sxs-lookup"><span data-stu-id="42eec-161">MRTK provides various types of HoloLens 2's shell (OS) style buttons.</span></span> <span data-ttu-id="42eec-162">它可在按钮表面上提供复杂的视觉反馈，例如邻近光线、压缩框和波纹效果 - 这些反馈可提高用户的置信度。</span><span class="sxs-lookup"><span data-stu-id="42eec-162">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface that improve the user's confidence.</span></span>

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="42eec-163">只需将某个 HoloLens 2 样式的可按按钮预制件拖放到场景中即可。</span><span class="sxs-lookup"><span data-stu-id="42eec-163">Simply drag and drop one of the **HoloLens 2 style pressable button prefab** into your scene.</span></span> <span data-ttu-id="42eec-164">该预制件将使用前面介绍的 Interactable.cs。</span><span class="sxs-lookup"><span data-stu-id="42eec-164">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="42eec-165">可以使用 Interactable 中公开的事件（例如 OnClick()）来触发操作。</span><span class="sxs-lookup"><span data-stu-id="42eec-165">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="42eec-166">在 MRTK 文档中详细了解按钮预制件</span><span class="sxs-lookup"><span data-stu-id="42eec-166">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a><span data-ttu-id="42eec-167">如何使对象跟随你？</span><span class="sxs-lookup"><span data-stu-id="42eec-167">How to make an object follow you?</span></span>
<span data-ttu-id="42eec-168">将 RadialView.cs 或 Follow.cs 脚本分配到某个对象 。</span><span class="sxs-lookup"><span data-stu-id="42eec-168">Assign **RadialView.cs** or **Follow.cs** script to an object.</span></span> <span data-ttu-id="42eec-169">此脚本是解算器脚本系列的一部分，可用于在 3D 空间中实现各种类型的对象定位。</span><span class="sxs-lookup"><span data-stu-id="42eec-169">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="42eec-170">将自动添加 SolverHandler.cs。</span><span class="sxs-lookup"><span data-stu-id="42eec-170">**SolverHandler.cs** will be automatically added.</span></span>
<span data-ttu-id="42eec-171">下面是 RadialView 配置的一个示例，它可以实现“惰性跟踪”追随行为，就如同使用 HoloLens shell 中的“开始”菜单一样。</span><span class="sxs-lookup"><span data-stu-id="42eec-171">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="42eec-172">可以指定最小/最大距离和最小/最大视图角度。</span><span class="sxs-lookup"><span data-stu-id="42eec-172">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="42eec-173">以下示例演示如何在 0.4 到 0.8 米范围内以 15° 的视图角度定位对象。</span><span class="sxs-lookup"><span data-stu-id="42eec-173">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="42eec-174">调整“线性插值时间”值，以加快或减慢定位更新的速度。</span><span class="sxs-lookup"><span data-stu-id="42eec-174">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="42eec-175">在 MRTK 文档中详细了解解算器</span><span class="sxs-lookup"><span data-stu-id="42eec-175">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a><span data-ttu-id="42eec-176">如何使对象朝向你？</span><span class="sxs-lookup"><span data-stu-id="42eec-176">How to make an object face you?</span></span>
<span data-ttu-id="42eec-177">将 Billboard.cs 脚本分配到某个对象。</span><span class="sxs-lookup"><span data-stu-id="42eec-177">Assign **Billboard.cs** script to an object.</span></span> <span data-ttu-id="42eec-178">不管你处于哪个位置，该对象都会朝向你。</span><span class="sxs-lookup"><span data-stu-id="42eec-178">It will always face you, regardless of your position.</span></span> <span data-ttu-id="42eec-179">可以指定枢轴选项。</span><span class="sxs-lookup"><span data-stu-id="42eec-179">You can specify the pivot axis option.</span></span>

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="42eec-180">准备好创建令人惊叹的混合现实体验了吗？</span><span class="sxs-lookup"><span data-stu-id="42eec-180">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="42eec-181">请访问以下页面来详细了解 MRTK 和混合现实。</span><span class="sxs-lookup"><span data-stu-id="42eec-181">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="42eec-182">关于作者</span><span class="sxs-lookup"><span data-stu-id="42eec-182">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="42eec-183"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="42eec-183"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="42eec-184">用户体验设计师 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="42eec-184">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="next-development-checkpoint"></a><span data-ttu-id="42eec-185">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="42eec-185">Next Development Checkpoint</span></span>

<span data-ttu-id="42eec-186">如果遵循我们规划的 Unity 的开发检查点旅程，则你在探索 MRTK 核心构建基块的过程中。</span><span class="sxs-lookup"><span data-stu-id="42eec-186">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="42eec-187">从这里，你可以进入下一个构建基块：</span><span class="sxs-lookup"><span data-stu-id="42eec-187">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="42eec-188">摄像头</span><span class="sxs-lookup"><span data-stu-id="42eec-188">Camera</span></span>](camera-in-unity.md)

<span data-ttu-id="42eec-189">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="42eec-189">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="42eec-190">共享体验</span><span class="sxs-lookup"><span data-stu-id="42eec-190">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="42eec-191">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="42eec-191">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="42eec-192">另请参阅</span><span class="sxs-lookup"><span data-stu-id="42eec-192">See also</span></span>
* [<span data-ttu-id="42eec-193">MRTK 安装指南 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="42eec-193">MRTK Installation Guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="42eec-194">混合现实工具包 - Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="42eec-194">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="42eec-195">MRTK 文档门户 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="42eec-195">MRTK Documentation Portal (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="42eec-196">HoloToolkit 到 MRTK 的移植指南</span><span class="sxs-lookup"><span data-stu-id="42eec-196">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
