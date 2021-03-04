---
title: 可交互对象
description: 了解如何触发事件，提供视觉提示，以及与混合现实应用程序中的对象进行交互。
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: 混合现实，控件，交互，提示，ui，ux，混合现实耳机，windows mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，音频
ms.openlocfilehash: b93092b597d0267c1169cf823b1a5c1fa03c3c3f
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759873"
---
# <a name="interactable-object"></a><span data-ttu-id="8c55d-104">可交互对象</span><span class="sxs-lookup"><span data-stu-id="8c55d-104">Interactable object</span></span>

![Interactible 对象](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="8c55d-106">"Button" 是一种用于在二维抽象环境中触发事件的比喻。</span><span class="sxs-lookup"><span data-stu-id="8c55d-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="8c55d-107">在这三维混合现实世界中，我们不必再局限于这种抽象领域。</span><span class="sxs-lookup"><span data-stu-id="8c55d-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="8c55d-108">任何内容都可以是触发事件的 **种不可交互对象** 。</span><span class="sxs-lookup"><span data-stu-id="8c55d-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="8c55d-109">种不可交互对象可以是从表上的咖啡杯到 midair 中的气球的任何内容。</span><span class="sxs-lookup"><span data-stu-id="8c55d-109">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="8c55d-110">在某些情况下（例如，在对话框 UI 中），我们仍要使用传统按钮。</span><span class="sxs-lookup"><span data-stu-id="8c55d-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="8c55d-111">按钮的可视化表示形式取决于上下文。</span><span class="sxs-lookup"><span data-stu-id="8c55d-111">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="8c55d-112">种不可交互对象的重要属性</span><span class="sxs-lookup"><span data-stu-id="8c55d-112">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="8c55d-113">视觉提示</span><span class="sxs-lookup"><span data-stu-id="8c55d-113">Visual cues</span></span>

<span data-ttu-id="8c55d-114">视觉提示是传感器的提示，由眼睛接收，由视觉对象系统在视觉对象中进行处理。</span><span class="sxs-lookup"><span data-stu-id="8c55d-114">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="8c55d-115">由于视觉对象系统在很多物种中是主导的，尤其是在人们看来，直观提示是了解世界上的信息。</span><span class="sxs-lookup"><span data-stu-id="8c55d-115">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="8c55d-116">由于全息对象与混合现实中的实际环境混合，因此很难理解您可以与哪些对象交互。</span><span class="sxs-lookup"><span data-stu-id="8c55d-116">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="8c55d-117">对于你的体验中的任何种不可交互对象，为每个输入状态提供不同的视觉提示非常重要。</span><span class="sxs-lookup"><span data-stu-id="8c55d-117">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="8c55d-118">这可以帮助用户了解你的体验的哪个部分是种不可交互的，并通过使用一致的交互方法使用户更自信。</span><span class="sxs-lookup"><span data-stu-id="8c55d-118">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="8c55d-119">远距离交互</span><span class="sxs-lookup"><span data-stu-id="8c55d-119">Far interactions</span></span>

<span data-ttu-id="8c55d-120">对于用户可与 "注视"、"手 ray" 和 "运动控制器" 射线交互的任何对象，我们建议为这三个输入状态提供不同的视觉提示：</span><span class="sxs-lookup"><span data-stu-id="8c55d-120">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="8c55d-121">![具有默认状态的种不可交互对象](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-121">![Interactable object with default state](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="8c55d-122">**默认 (观察) 状态**</span><span class="sxs-lookup"><span data-stu-id="8c55d-122">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="8c55d-123">对象的默认空闲状态。</span><span class="sxs-lookup"><span data-stu-id="8c55d-123">Default idle state of the object.</span></span>
    <span data-ttu-id="8c55d-124">光标不在对象上。</span><span class="sxs-lookup"><span data-stu-id="8c55d-124">The cursor isn't on the object.</span></span> <span data-ttu-id="8c55d-125">未检测到手写。</span><span class="sxs-lookup"><span data-stu-id="8c55d-125">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8c55d-126">![具有目标和悬停状态的种不可交互对象](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-126">![Interactable object with target and hover state](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="8c55d-127">**目标 (悬停) 状态**</span><span class="sxs-lookup"><span data-stu-id="8c55d-127">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="8c55d-128">当对象面向注视光标时，指的是指邻近的或运动控制器的指针。</span><span class="sxs-lookup"><span data-stu-id="8c55d-128">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="8c55d-129">光标位于对象上。</span><span class="sxs-lookup"><span data-stu-id="8c55d-129">The cursor is on the object.</span></span> <span data-ttu-id="8c55d-130">已检测到手型，准备就绪。</span><span class="sxs-lookup"><span data-stu-id="8c55d-130">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8c55d-131">![具有按下状态的种不可交互对象](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-131">![Interactable object with pressed state](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="8c55d-132">**按下状态**</span><span class="sxs-lookup"><span data-stu-id="8c55d-132">**Pressed state**</span></span><br>
        <span data-ttu-id="8c55d-133">如果按下了按压按钮，请按下或运动控制器的选择按钮。</span><span class="sxs-lookup"><span data-stu-id="8c55d-133">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="8c55d-134">光标位于对象上。</span><span class="sxs-lookup"><span data-stu-id="8c55d-134">The cursor is on the object.</span></span> <span data-ttu-id="8c55d-135">检测到手型，并攻丝。</span><span class="sxs-lookup"><span data-stu-id="8c55d-135">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="8c55d-136">您可以使用诸如突出显示或缩放等方法为用户输入状态提供视觉提示。</span><span class="sxs-lookup"><span data-stu-id="8c55d-136">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="8c55d-137">在混合现实中，可以在 "开始" 菜单和应用栏按钮中查找可视化不同输入状态的示例。</span><span class="sxs-lookup"><span data-stu-id="8c55d-137">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="8c55d-138">下面是 **全息按钮** 上这些状态的外观：</span><span class="sxs-lookup"><span data-stu-id="8c55d-138">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="8c55d-139">![处于默认状态的全息按钮](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-139">![Holographic button in default state](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="8c55d-140">**默认 (观察) 状态**</span><span class="sxs-lookup"><span data-stu-id="8c55d-140">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8c55d-141">![目标和悬停状态的全息按钮](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-141">![Holographic button in target and hover state](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="8c55d-142">**目标 (悬停) 状态**</span><span class="sxs-lookup"><span data-stu-id="8c55d-142">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8c55d-143">![处于按下状态的全息按钮](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-143">![Holographic button in pressed state](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="8c55d-144">**按下状态**</span><span class="sxs-lookup"><span data-stu-id="8c55d-144">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="8c55d-145">接近交互 (直接) </span><span class="sxs-lookup"><span data-stu-id="8c55d-145">Near interactions (direct)</span></span> 

<span data-ttu-id="8c55d-146">HoloLens 2 支持已表述的手动跟踪输入，这允许您与对象进行交互。</span><span class="sxs-lookup"><span data-stu-id="8c55d-146">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="8c55d-147">如果没有 haptic 的反馈和完美的深度认识，则很难判断你手中的距离是从一个对象还是正在触摸。</span><span class="sxs-lookup"><span data-stu-id="8c55d-147">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="8c55d-148">务必提供足够的视觉提示来传达对象的状态，特别是根据对象的状态。</span><span class="sxs-lookup"><span data-stu-id="8c55d-148">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="8c55d-149">使用视觉反馈传达以下状态：</span><span class="sxs-lookup"><span data-stu-id="8c55d-149">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="8c55d-150">**默认 (观察)**：对象的默认空闲状态。</span><span class="sxs-lookup"><span data-stu-id="8c55d-150">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="8c55d-151">**悬停**：当手接近全息图时，请更改视觉对象，以便与全息图建立通信。</span><span class="sxs-lookup"><span data-stu-id="8c55d-151">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="8c55d-152">**距离和交互点**：作为一种方法，即使用全息图，设计反馈来传达投影的交互点，以及从对象到手指的距离</span><span class="sxs-lookup"><span data-stu-id="8c55d-152">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="8c55d-153">**联系人开始**：更改视觉对象 (光源、颜色) ，传达触摸已发生的情况</span><span class="sxs-lookup"><span data-stu-id="8c55d-153">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="8c55d-154">**Grasped**：在 Grasped 对象时更改视觉对象 (光源、颜色) </span><span class="sxs-lookup"><span data-stu-id="8c55d-154">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="8c55d-155">**联系人结束**：在触摸结束时，更改视觉对象 (光源、颜色) </span><span class="sxs-lookup"><span data-stu-id="8c55d-155">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="8c55d-156">![悬停 (远处) ](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="8c55d-157">**悬停 (远处)**</span><span class="sxs-lookup"><span data-stu-id="8c55d-157">**Hover (Far)**</span></span><br>
        <span data-ttu-id="8c55d-158">根据手的邻近性突出显示。</span><span class="sxs-lookup"><span data-stu-id="8c55d-158">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8c55d-159">![悬停 (接近) ](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-159">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="8c55d-160">**悬停 (接近)**</span><span class="sxs-lookup"><span data-stu-id="8c55d-160">**Hover (Near)**</span></span><br>
        <span data-ttu-id="8c55d-161">根据与手型的距离突出显示大小变化。</span><span class="sxs-lookup"><span data-stu-id="8c55d-161">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="8c55d-162">![触摸/按](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-162">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="8c55d-163">**触摸/按**</span><span class="sxs-lookup"><span data-stu-id="8c55d-163">**Touch / press**</span></span><br>
        <span data-ttu-id="8c55d-164">视觉对象和音频反馈。</span><span class="sxs-lookup"><span data-stu-id="8c55d-164">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8c55d-165">![掌握](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-165">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="8c55d-166">**掌握**</span><span class="sxs-lookup"><span data-stu-id="8c55d-166">**Grasp**</span></span><br>
        <span data-ttu-id="8c55d-167">视觉对象和音频反馈。</span><span class="sxs-lookup"><span data-stu-id="8c55d-167">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="8c55d-168">[HoloLens 2 上的按钮](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)是如何可视化不同输入交互状态的示例：</span><span class="sxs-lookup"><span data-stu-id="8c55d-168">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="8c55d-169">![默认](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="8c55d-170">**默认**</span><span class="sxs-lookup"><span data-stu-id="8c55d-170">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8c55d-171">![悬停](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-171">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="8c55d-172">**悬停**</span><span class="sxs-lookup"><span data-stu-id="8c55d-172">**Hover**</span></span><br>
        <span data-ttu-id="8c55d-173">显示基于近程的照明效果。</span><span class="sxs-lookup"><span data-stu-id="8c55d-173">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="8c55d-174">![触控](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-174">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="8c55d-175">**触控**</span><span class="sxs-lookup"><span data-stu-id="8c55d-175">**Touch**</span></span><br>
        <span data-ttu-id="8c55d-176">显示波纹效果。</span><span class="sxs-lookup"><span data-stu-id="8c55d-176">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8c55d-177">![请按](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-177">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="8c55d-178">**请按**</span><span class="sxs-lookup"><span data-stu-id="8c55d-178">**Press**</span></span><br>
        <span data-ttu-id="8c55d-179">移动前面板。</span><span class="sxs-lookup"><span data-stu-id="8c55d-179">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="8c55d-180">HoloLens 2 上的 "环" 视觉提示</span><span class="sxs-lookup"><span data-stu-id="8c55d-180">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="8c55d-181">在 HoloLens 2 上，有一个额外的视觉提示，可帮助用户了解深度。</span><span class="sxs-lookup"><span data-stu-id="8c55d-181">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="8c55d-182">当手指更接近对象时，其手指附近的圆圈会显示并缩小。</span><span class="sxs-lookup"><span data-stu-id="8c55d-182">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="8c55d-183">当达到按下状态时，环最终汇聚为一个点。</span><span class="sxs-lookup"><span data-stu-id="8c55d-183">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="8c55d-184">此视觉对象 affordance 可帮助用户了解其在对象中的距离。</span><span class="sxs-lookup"><span data-stu-id="8c55d-184">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="8c55d-185">*视频循环：基于与边界框的邻近的视觉反馈示例*</span><span class="sxs-lookup"><span data-stu-id="8c55d-185">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="8c55d-186">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="8c55d-186">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="8c55d-187">![视觉对象反馈](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="8c55d-187">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="8c55d-188">音频提示</span><span class="sxs-lookup"><span data-stu-id="8c55d-188">Audio cues</span></span>

<span data-ttu-id="8c55d-189">对于直接交互，正确的音频反馈可显著改善用户体验。</span><span class="sxs-lookup"><span data-stu-id="8c55d-189">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="8c55d-190">使用音频反馈来传达以下提示：</span><span class="sxs-lookup"><span data-stu-id="8c55d-190">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="8c55d-191">**联系人开始**：触控开始时播放声音</span><span class="sxs-lookup"><span data-stu-id="8c55d-191">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="8c55d-192">**联系人结束**：在 touch 端上播放声音</span><span class="sxs-lookup"><span data-stu-id="8c55d-192">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="8c55d-193">**开始获取**：开始播放时播放声音</span><span class="sxs-lookup"><span data-stu-id="8c55d-193">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="8c55d-194">**抓取结束**：在抓取结束时播放声音</span><span class="sxs-lookup"><span data-stu-id="8c55d-194">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="8c55d-195">语音命令</span><span class="sxs-lookup"><span data-stu-id="8c55d-195">Voice commanding</span></span><br>
        <span data-ttu-id="8c55d-196">对于任何种不可交互对象，支持替代交互选项非常重要。</span><span class="sxs-lookup"><span data-stu-id="8c55d-196">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="8c55d-197">默认情况下，我们建议为种不可交互的任何对象支持 [语音命令](../out-of-scope/voice-design.md) 。</span><span class="sxs-lookup"><span data-stu-id="8c55d-197">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="8c55d-198">若要改善可发现性，还可以在悬停状态中提供工具提示。</span><span class="sxs-lookup"><span data-stu-id="8c55d-198">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="8c55d-199">*Image：语音命令的工具提示*</span><span class="sxs-lookup"><span data-stu-id="8c55d-199">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![语音命令](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="8c55d-201">重设大小建议</span><span class="sxs-lookup"><span data-stu-id="8c55d-201">Sizing recommendations</span></span> 

<span data-ttu-id="8c55d-202">为了确保可以轻松地接触所有种不可交互对象，我们建议确保种不可交互根据其从用户的距离来确定最小大小。</span><span class="sxs-lookup"><span data-stu-id="8c55d-202">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="8c55d-203">视觉角度通常以视觉弧的度数来度量。视觉角度基于用户眼睛与对象之间的距离并保持不变，而目标的物理大小可能会随用户更改的距离而更改。</span><span class="sxs-lookup"><span data-stu-id="8c55d-203">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="8c55d-204">若要根据用户的距离确定对象的必要物理大小，请尝试使用视觉角度计算器（如 [此](https://elvers.us/perception/visualAngle/)类）。</span><span class="sxs-lookup"><span data-stu-id="8c55d-204">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="8c55d-205">下面是有关种不可交互内容的最小大小建议。</span><span class="sxs-lookup"><span data-stu-id="8c55d-205">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="8c55d-206">直接手动交互的目标大小</span><span class="sxs-lookup"><span data-stu-id="8c55d-206">Target size for direct hand interaction</span></span>

| <span data-ttu-id="8c55d-207">距离</span><span class="sxs-lookup"><span data-stu-id="8c55d-207">Distance</span></span> | <span data-ttu-id="8c55d-208">查看角度</span><span class="sxs-lookup"><span data-stu-id="8c55d-208">Viewing angle</span></span> | <span data-ttu-id="8c55d-209">大小</span><span class="sxs-lookup"><span data-stu-id="8c55d-209">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="8c55d-210">45厘米</span><span class="sxs-lookup"><span data-stu-id="8c55d-210">45 cm</span></span>  | <span data-ttu-id="8c55d-211">不小于2°</span><span class="sxs-lookup"><span data-stu-id="8c55d-211">no smaller than 2°</span></span> | <span data-ttu-id="8c55d-212">1.6 x 1.6 厘米</span><span class="sxs-lookup"><span data-stu-id="8c55d-212">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="8c55d-213">![直接手动交互的目标大小](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-213">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="8c55d-214">*直接手动交互的目标大小*</span><span class="sxs-lookup"><span data-stu-id="8c55d-214">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="8c55d-215">按钮的目标大小</span><span class="sxs-lookup"><span data-stu-id="8c55d-215">Target size for buttons</span></span>

<span data-ttu-id="8c55d-216">创建直接交互的按钮时，建议使用较大的最小 3.2 x 3.2 厘米，以确保有足够的空间来包含图标，并可能有一些文本。</span><span class="sxs-lookup"><span data-stu-id="8c55d-216">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="8c55d-217">距离</span><span class="sxs-lookup"><span data-stu-id="8c55d-217">Distance</span></span> | <span data-ttu-id="8c55d-218">最小大小</span><span class="sxs-lookup"><span data-stu-id="8c55d-218">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="8c55d-219">45厘米</span><span class="sxs-lookup"><span data-stu-id="8c55d-219">45 cm</span></span>  | <span data-ttu-id="8c55d-220">3.2 x 3.2 厘米</span><span class="sxs-lookup"><span data-stu-id="8c55d-220">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="8c55d-221">![按钮的目标大小](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="8c55d-221">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="8c55d-222">*按钮的目标大小*</span><span class="sxs-lookup"><span data-stu-id="8c55d-222">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="8c55d-223">手动 ray 或注视交互的目标大小</span><span class="sxs-lookup"><span data-stu-id="8c55d-223">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="8c55d-224">距离</span><span class="sxs-lookup"><span data-stu-id="8c55d-224">Distance</span></span> | <span data-ttu-id="8c55d-225">查看角度</span><span class="sxs-lookup"><span data-stu-id="8c55d-225">Viewing angle</span></span> | <span data-ttu-id="8c55d-226">大小</span><span class="sxs-lookup"><span data-stu-id="8c55d-226">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="8c55d-227">2 m</span><span class="sxs-lookup"><span data-stu-id="8c55d-227">2 m</span></span>  | <span data-ttu-id="8c55d-228">不小于1°</span><span class="sxs-lookup"><span data-stu-id="8c55d-228">no smaller than 1°</span></span> | <span data-ttu-id="8c55d-229">3.5 x 3.5 厘米</span><span class="sxs-lookup"><span data-stu-id="8c55d-229">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="8c55d-230">![手动 ray 或注视交互的目标大小](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c55d-230">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="8c55d-231">*手动 ray 或注视交互的目标大小*</span><span class="sxs-lookup"><span data-stu-id="8c55d-231">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="8c55d-232">MRTK 中的种不可交互对象 (Unity 的混合现实工具包) </span><span class="sxs-lookup"><span data-stu-id="8c55d-232">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="8c55d-233">在 **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 中，可以使用脚本 [**种不可交互**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) 使对象对各种类型的输入交互状态进行响应。</span><span class="sxs-lookup"><span data-stu-id="8c55d-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="8c55d-234">它支持各种类型的主题，这些主题允许您通过控制对象属性（如颜色、大小、材料和着色器）来定义可视状态。</span><span class="sxs-lookup"><span data-stu-id="8c55d-234">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="8c55d-235">种不可交互</span><span class="sxs-lookup"><span data-stu-id="8c55d-235">Interactable</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/interactable.md)
* [<span data-ttu-id="8c55d-236">Button</span><span class="sxs-lookup"><span data-stu-id="8c55d-236">Button</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md)
* [<span data-ttu-id="8c55d-237">手动交互示例场景</span><span class="sxs-lookup"><span data-stu-id="8c55d-237">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="8c55d-238">MixedRealityToolkit 的标准着色器提供了各种选项 **，例如，可** 帮助您创建视觉对象和音频提示。</span><span class="sxs-lookup"><span data-stu-id="8c55d-238">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="8c55d-239">MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="8c55d-239">MRTK Standard Shader</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/rendering/mrtk-standard-shader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="8c55d-240">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c55d-240">See also</span></span>

* [<span data-ttu-id="8c55d-241">光标</span><span class="sxs-lookup"><span data-stu-id="8c55d-241">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="8c55d-242">手部射线</span><span class="sxs-lookup"><span data-stu-id="8c55d-242">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="8c55d-243">Button</span><span class="sxs-lookup"><span data-stu-id="8c55d-243">Button</span></span>](button.md)
* [<span data-ttu-id="8c55d-244">可交互对象</span><span class="sxs-lookup"><span data-stu-id="8c55d-244">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="8c55d-245">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="8c55d-245">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="8c55d-246">操作</span><span class="sxs-lookup"><span data-stu-id="8c55d-246">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8c55d-247">手动菜单</span><span class="sxs-lookup"><span data-stu-id="8c55d-247">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="8c55d-248">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="8c55d-248">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="8c55d-249">对象集合</span><span class="sxs-lookup"><span data-stu-id="8c55d-249">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="8c55d-250">语音命令</span><span class="sxs-lookup"><span data-stu-id="8c55d-250">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="8c55d-251">键盘</span><span class="sxs-lookup"><span data-stu-id="8c55d-251">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="8c55d-252">工具提示</span><span class="sxs-lookup"><span data-stu-id="8c55d-252">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="8c55d-253">平板</span><span class="sxs-lookup"><span data-stu-id="8c55d-253">Slate</span></span>](slate.md)
* [<span data-ttu-id="8c55d-254">滑块</span><span class="sxs-lookup"><span data-stu-id="8c55d-254">Slider</span></span>](slider.md)
* [<span data-ttu-id="8c55d-255">着色器</span><span class="sxs-lookup"><span data-stu-id="8c55d-255">Shader</span></span>](shader.md)
* [<span data-ttu-id="8c55d-256">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="8c55d-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="8c55d-257">显示进度</span><span class="sxs-lookup"><span data-stu-id="8c55d-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="8c55d-258">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="8c55d-258">Surface magnetism</span></span>](surface-magnetism.md)
