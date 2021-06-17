---
title: 可交互对象
description: 了解如何触发事件、提供视觉提示以及与混合现实应用程序中的对象进行交互。
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: 混合现实， 控件， 交互， 提示， ui， ux， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， HoloLens， MRTK， 混合现实工具包， 音频
ms.openlocfilehash: b25c25a6dd48bcc85a556787099734d147d18df2
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110219"
---
# <a name="interactable-object"></a><span data-ttu-id="cbd92-104">可交互对象</span><span class="sxs-lookup"><span data-stu-id="cbd92-104">Interactable object</span></span>

![可交互对象](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="cbd92-106">按钮一直是在 2D 抽象世界触发事件的一种暗念。</span><span class="sxs-lookup"><span data-stu-id="cbd92-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="cbd92-107">在三维混合现实世界，我们不必再局限于这个抽象世界。</span><span class="sxs-lookup"><span data-stu-id="cbd92-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="cbd92-108">任何内容都可以是 **触发事件的** 可交互对象。</span><span class="sxs-lookup"><span data-stu-id="cbd92-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="cbd92-109">可交互对象可以是任何内容，从表上的咖啡杯到中间的气球。</span><span class="sxs-lookup"><span data-stu-id="cbd92-109">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="cbd92-110">在某些情况下（例如，在对话框 UI 中）我们仍然使用传统按钮。</span><span class="sxs-lookup"><span data-stu-id="cbd92-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="cbd92-111">按钮的可视化表示形式取决于上下文。</span><span class="sxs-lookup"><span data-stu-id="cbd92-111">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="cbd92-112">可交互对象的重要属性</span><span class="sxs-lookup"><span data-stu-id="cbd92-112">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="cbd92-113">视觉提示</span><span class="sxs-lookup"><span data-stu-id="cbd92-113">Visual cues</span></span>

<span data-ttu-id="cbd92-114">视觉提示是来自光的传感器提示，由眼睛接收，在视觉感知期间由视觉系统处理。</span><span class="sxs-lookup"><span data-stu-id="cbd92-114">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="cbd92-115">由于视觉系统在许多种类（尤其是人类）中处于主导状态，因此视觉提示是了解世界方式的一大信息源。</span><span class="sxs-lookup"><span data-stu-id="cbd92-115">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="cbd92-116">由于全息对象与混合现实中的真实环境混合在一起，因此可能很难理解可以交互的对象。</span><span class="sxs-lookup"><span data-stu-id="cbd92-116">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="cbd92-117">对于体验中任何可交互的对象，为每种输入状态提供不同的视觉提示非常重要。</span><span class="sxs-lookup"><span data-stu-id="cbd92-117">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="cbd92-118">这有助于用户了解你体验的哪个部分是可交互的，并且通过使用一致的交互方法使用户确信。</span><span class="sxs-lookup"><span data-stu-id="cbd92-118">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="cbd92-119">远交互</span><span class="sxs-lookup"><span data-stu-id="cbd92-119">Far interactions</span></span>

<span data-ttu-id="cbd92-120">对于用户可以与凝视、手部射线和运动控制器射线交互的任何对象，建议针对这三种输入状态使用不同的视觉提示：</span><span class="sxs-lookup"><span data-stu-id="cbd92-120">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="cbd92-121">![具有默认状态可交互的对象](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-121">![Interactable object with default state](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="cbd92-122">**默认 (观察) 状态**</span><span class="sxs-lookup"><span data-stu-id="cbd92-122">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="cbd92-123">对象的默认空闲状态。</span><span class="sxs-lookup"><span data-stu-id="cbd92-123">Default idle state of the object.</span></span>
    <span data-ttu-id="cbd92-124">光标不在 对象上。</span><span class="sxs-lookup"><span data-stu-id="cbd92-124">The cursor isn't on the object.</span></span> <span data-ttu-id="cbd92-125">未检测到手部。</span><span class="sxs-lookup"><span data-stu-id="cbd92-125">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="cbd92-126">![具有目标状态和悬停状态可交互的对象](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-126">![Interactable object with target and hover state](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="cbd92-127">**目标 (将鼠标) 状态**</span><span class="sxs-lookup"><span data-stu-id="cbd92-127">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="cbd92-128">当对象以凝视光标、手指邻近或运动控制器指针为目标时。</span><span class="sxs-lookup"><span data-stu-id="cbd92-128">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="cbd92-129">光标位于 对象上。</span><span class="sxs-lookup"><span data-stu-id="cbd92-129">The cursor is on the object.</span></span> <span data-ttu-id="cbd92-130">检测到手部，准备就绪。</span><span class="sxs-lookup"><span data-stu-id="cbd92-130">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="cbd92-131">![具有按下状态可交互的对象](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-131">![Interactable object with pressed state](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="cbd92-132">**按下状态**</span><span class="sxs-lookup"><span data-stu-id="cbd92-132">**Pressed state**</span></span><br>
        <span data-ttu-id="cbd92-133">使用敲击手势按下对象时，按手指或运动控制器的"选择"按钮。</span><span class="sxs-lookup"><span data-stu-id="cbd92-133">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="cbd92-134">光标位于 对象上。</span><span class="sxs-lookup"><span data-stu-id="cbd92-134">The cursor is on the object.</span></span> <span data-ttu-id="cbd92-135">检测到手部，点击了空气。</span><span class="sxs-lookup"><span data-stu-id="cbd92-135">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="cbd92-136">可以使用突出显示或缩放等技术为用户输入状态提供视觉提示。</span><span class="sxs-lookup"><span data-stu-id="cbd92-136">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="cbd92-137">在混合现实中，可以在应用栏按钮上找到可视化“开始”菜单输入状态的示例。</span><span class="sxs-lookup"><span data-stu-id="cbd92-137">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="cbd92-138">全息按钮上的这些状态 **如下所示**：</span><span class="sxs-lookup"><span data-stu-id="cbd92-138">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="cbd92-139">![默认状态下的全息按钮](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-139">![Holographic button in default state](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="cbd92-140">**默认 (观察) 状态**</span><span class="sxs-lookup"><span data-stu-id="cbd92-140">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="cbd92-141">![处于"目标"和"悬停"状态中的全息按钮](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-141">![Holographic button in target and hover state](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="cbd92-142">**目标 (将鼠标) 状态**</span><span class="sxs-lookup"><span data-stu-id="cbd92-142">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="cbd92-143">![已按下的全息按钮](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-143">![Holographic button in pressed state](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="cbd92-144">**按下状态**</span><span class="sxs-lookup"><span data-stu-id="cbd92-144">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="cbd92-145">近 (直接) </span><span class="sxs-lookup"><span data-stu-id="cbd92-145">Near interactions (direct)</span></span> 

<span data-ttu-id="cbd92-146">HoloLens 2支持手部跟踪输入，可用于与对象交互。</span><span class="sxs-lookup"><span data-stu-id="cbd92-146">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="cbd92-147">如果没有视觉反馈和完美深度感知，就很难判断手离对象有多远或者是否触摸了它。</span><span class="sxs-lookup"><span data-stu-id="cbd92-147">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="cbd92-148">必须提供足够的视觉提示来传达对象的状态，尤其是基于该对象的手的状态。</span><span class="sxs-lookup"><span data-stu-id="cbd92-148">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="cbd92-149">使用视觉反馈传达以下状态：</span><span class="sxs-lookup"><span data-stu-id="cbd92-149">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="cbd92-150">**默认 (观察) ：** 对象的默认空闲状态。</span><span class="sxs-lookup"><span data-stu-id="cbd92-150">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="cbd92-151">**悬** 停：当手靠近全息影像时，更改视觉对象以传达以全息影像为目标的手。</span><span class="sxs-lookup"><span data-stu-id="cbd92-151">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="cbd92-152">**距离和交互点**：当手接近全息影像时，设计反馈来传达预测的交互点，以及手指与对象的距离</span><span class="sxs-lookup"><span data-stu-id="cbd92-152">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="cbd92-153">**联系人开始**：更改视觉对象 (浅色) 来传达触摸已发生</span><span class="sxs-lookup"><span data-stu-id="cbd92-153">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="cbd92-154">**已抓取**：在 (时更改) 颜色颜色</span><span class="sxs-lookup"><span data-stu-id="cbd92-154">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="cbd92-155">**联系人结束**：在触摸 (更改视觉对象) 浅色、颜色或颜色</span><span class="sxs-lookup"><span data-stu-id="cbd92-155">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="cbd92-156">![将鼠标 (远) ](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="cbd92-157">**将鼠标 (远)**</span><span class="sxs-lookup"><span data-stu-id="cbd92-157">**Hover (Far)**</span></span><br>
        <span data-ttu-id="cbd92-158">根据手的邻近度突出显示。</span><span class="sxs-lookup"><span data-stu-id="cbd92-158">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cbd92-159">![将鼠标 (") ](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-159">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="cbd92-160&quot;>**将鼠标 (")**</span><span class="sxs-lookup"><span data-stu-id="cbd92-160">**Hover (Near)**</span></span><br>
        <span data-ttu-id="cbd92-161">突出显示基于手部距离的大小更改。</span><span class="sxs-lookup"><span data-stu-id="cbd92-161">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="cbd92-162">![触摸/按](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-162">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="cbd92-163">**触摸/按**</span><span class="sxs-lookup"><span data-stu-id="cbd92-163">**Touch / press**</span></span><br>
        <span data-ttu-id="cbd92-164">视觉对象和音频反馈。</span><span class="sxs-lookup"><span data-stu-id="cbd92-164">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cbd92-165">![把握](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-165">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="cbd92-166">**把握**</span><span class="sxs-lookup"><span data-stu-id="cbd92-166">**Grasp**</span></span><br>
        <span data-ttu-id="cbd92-167">视觉对象和音频反馈。</span><span class="sxs-lookup"><span data-stu-id="cbd92-167">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="cbd92-168">图标 [上的HoloLens 2](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) 是如何可视化不同输入交互状态的示例：</span><span class="sxs-lookup"><span data-stu-id="cbd92-168">A [button on HoloLens 2](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="cbd92-169">![默认](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="cbd92-170">**默认**</span><span class="sxs-lookup"><span data-stu-id="cbd92-170">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cbd92-171">![悬停](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-171">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="cbd92-172">**悬停**</span><span class="sxs-lookup"><span data-stu-id="cbd92-172">**Hover**</span></span><br>
        <span data-ttu-id="cbd92-173">展示基于邻近感应的照明效果。</span><span class="sxs-lookup"><span data-stu-id="cbd92-173">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="cbd92-174">![触控](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-174">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="cbd92-175">**触控**</span><span class="sxs-lookup"><span data-stu-id="cbd92-175">**Touch**</span></span><br>
        <span data-ttu-id="cbd92-176">显示波纹效果。</span><span class="sxs-lookup"><span data-stu-id="cbd92-176">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cbd92-177">![请按](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-177">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="cbd92-178">**按**</span><span class="sxs-lookup"><span data-stu-id="cbd92-178">**Press**</span></span><br>
        <span data-ttu-id="cbd92-179">移动前板。</span><span class="sxs-lookup"><span data-stu-id="cbd92-179">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="cbd92-180">上显示"环"视觉提示HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cbd92-180">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="cbd92-181">在HoloLens 2，有一个额外的视觉提示，可帮助用户感知深度。</span><span class="sxs-lookup"><span data-stu-id="cbd92-181">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="cbd92-182">当手指靠近对象时，可显示一个靠近其手指的环并缩小。</span><span class="sxs-lookup"><span data-stu-id="cbd92-182">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="cbd92-183">当达到按下状态时，环最终会聚合为点。</span><span class="sxs-lookup"><span data-stu-id="cbd92-183">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="cbd92-184">此视觉视觉视觉元素可帮助用户了解它们与对象距离有多远。</span><span class="sxs-lookup"><span data-stu-id="cbd92-184">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="cbd92-185">*视频循环：基于边界框邻近性进行视觉反馈的示例*</span><span class="sxs-lookup"><span data-stu-id="cbd92-185">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="cbd92-186">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="cbd92-186">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="cbd92-187">![有关手部邻近感应的视觉反馈](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="cbd92-187">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="cbd92-188">音频提示</span><span class="sxs-lookup"><span data-stu-id="cbd92-188">Audio cues</span></span>

<span data-ttu-id="cbd92-189">对于直接手部交互，适当的音频反馈可以显著提高用户体验。</span><span class="sxs-lookup"><span data-stu-id="cbd92-189">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="cbd92-190">使用音频反馈传达以下提示：</span><span class="sxs-lookup"><span data-stu-id="cbd92-190">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="cbd92-191">**联系人开始**：触摸开始时播放声音</span><span class="sxs-lookup"><span data-stu-id="cbd92-191">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="cbd92-192">**接触端**：在触摸端播放声音</span><span class="sxs-lookup"><span data-stu-id="cbd92-192">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="cbd92-193">**抓取开始**：开始抓取时播放声音</span><span class="sxs-lookup"><span data-stu-id="cbd92-193">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="cbd92-194">**抓取端**：在抓取端播放声音</span><span class="sxs-lookup"><span data-stu-id="cbd92-194">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="cbd92-195">语音命令</span><span class="sxs-lookup"><span data-stu-id="cbd92-195">Voice commanding</span></span><br>
        <span data-ttu-id="cbd92-196">对于任何可交互对象，必须支持备用交互选项。</span><span class="sxs-lookup"><span data-stu-id="cbd92-196">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="cbd92-197">默认情况下，建议任何 [可交互](../out-of-scope/voice-design.md) 的对象都支持语音命令。</span><span class="sxs-lookup"><span data-stu-id="cbd92-197">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="cbd92-198">为了提高可发现性，还可以在悬停状态期间提供工具提示。</span><span class="sxs-lookup"><span data-stu-id="cbd92-198">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="cbd92-199">*图像：语音命令的工具提示*</span><span class="sxs-lookup"><span data-stu-id="cbd92-199">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![语音命令](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a><span data-ttu-id="cbd92-201">重设大小建议</span><span class="sxs-lookup"><span data-stu-id="cbd92-201">Sizing recommendations</span></span>

<span data-ttu-id="cbd92-202">为了确保可以轻松地接触所有种不可交互对象，我们建议确保种不可交互根据其从用户的距离来确定最小大小。</span><span class="sxs-lookup"><span data-stu-id="cbd92-202">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="cbd92-203">视觉角度通常以视觉弧的度数来度量。视觉角度基于用户眼睛与对象之间的距离并保持不变，而目标的物理大小可能会随用户更改的距离而更改。</span><span class="sxs-lookup"><span data-stu-id="cbd92-203">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="cbd92-204">若要根据用户的距离确定对象的必要物理大小，请尝试使用视觉角度计算器（如 [此](https://elvers.us/perception/visualAngle/)类）。</span><span class="sxs-lookup"><span data-stu-id="cbd92-204">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="cbd92-205">下面是有关种不可交互内容的最小大小建议。</span><span class="sxs-lookup"><span data-stu-id="cbd92-205">Below are the recommendations for minimum sizes of interactable content.</span></span>

### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="cbd92-206">直接手动交互的目标大小</span><span class="sxs-lookup"><span data-stu-id="cbd92-206">Target size for direct hand interaction</span></span>

| <span data-ttu-id="cbd92-207">距离</span><span class="sxs-lookup"><span data-stu-id="cbd92-207">Distance</span></span> | <span data-ttu-id="cbd92-208">查看角度</span><span class="sxs-lookup"><span data-stu-id="cbd92-208">Viewing angle</span></span> | <span data-ttu-id="cbd92-209">大小</span><span class="sxs-lookup"><span data-stu-id="cbd92-209">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="cbd92-210">45厘米</span><span class="sxs-lookup"><span data-stu-id="cbd92-210">45 cm</span></span>  | <span data-ttu-id="cbd92-211">不小于2°</span><span class="sxs-lookup"><span data-stu-id="cbd92-211">no smaller than 2°</span></span> | <span data-ttu-id="cbd92-212">1.6 x 1.6 厘米</span><span class="sxs-lookup"><span data-stu-id="cbd92-212">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="cbd92-213">![直接手动交互的目标大小](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-213">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="cbd92-214">*直接手动交互的目标大小*</span><span class="sxs-lookup"><span data-stu-id="cbd92-214">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="cbd92-215">按钮的目标大小</span><span class="sxs-lookup"><span data-stu-id="cbd92-215">Target size for buttons</span></span>

<span data-ttu-id="cbd92-216">创建直接交互的按钮时，建议使用较大的最小 3.2 x 3.2 厘米，以确保有足够的空间来包含图标，并可能有一些文本。</span><span class="sxs-lookup"><span data-stu-id="cbd92-216">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="cbd92-217">距离</span><span class="sxs-lookup"><span data-stu-id="cbd92-217">Distance</span></span> | <span data-ttu-id="cbd92-218">最小大小</span><span class="sxs-lookup"><span data-stu-id="cbd92-218">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="cbd92-219">45厘米</span><span class="sxs-lookup"><span data-stu-id="cbd92-219">45 cm</span></span>  | <span data-ttu-id="cbd92-220">3.2 x 3.2 厘米</span><span class="sxs-lookup"><span data-stu-id="cbd92-220">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="cbd92-221">![按钮的目标大小](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="cbd92-221">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="cbd92-222">*按钮的目标大小*</span><span class="sxs-lookup"><span data-stu-id="cbd92-222">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="cbd92-223">手动 ray 或注视交互的目标大小</span><span class="sxs-lookup"><span data-stu-id="cbd92-223">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="cbd92-224">距离</span><span class="sxs-lookup"><span data-stu-id="cbd92-224">Distance</span></span> | <span data-ttu-id="cbd92-225">查看角度</span><span class="sxs-lookup"><span data-stu-id="cbd92-225">Viewing angle</span></span> | <span data-ttu-id="cbd92-226">大小</span><span class="sxs-lookup"><span data-stu-id="cbd92-226">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="cbd92-227">2 m</span><span class="sxs-lookup"><span data-stu-id="cbd92-227">2 m</span></span>  | <span data-ttu-id="cbd92-228">不小于1°</span><span class="sxs-lookup"><span data-stu-id="cbd92-228">no smaller than 1°</span></span> | <span data-ttu-id="cbd92-229">3.5 x 3.5 厘米</span><span class="sxs-lookup"><span data-stu-id="cbd92-229">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="cbd92-230">![手动 ray 或注视交互的目标大小](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="cbd92-230">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="cbd92-231">*手动 ray 或注视交互的目标大小*</span><span class="sxs-lookup"><span data-stu-id="cbd92-231">*Target size for hand ray or gaze interaction*</span></span>

<br>

---

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="cbd92-232">MRTK 中的种不可交互对象 (Unity 的混合现实工具包) </span><span class="sxs-lookup"><span data-stu-id="cbd92-232">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="cbd92-233">在 **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 中，可以使用脚本 [**种不可交互**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) 使对象对各种类型的输入交互状态进行响应。</span><span class="sxs-lookup"><span data-stu-id="cbd92-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="cbd92-234">它支持各种类型的主题，这些主题允许您通过控制对象属性（如颜色、大小、材料和着色器）来定义可视状态。</span><span class="sxs-lookup"><span data-stu-id="cbd92-234">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="cbd92-235">可交互</span><span class="sxs-lookup"><span data-stu-id="cbd92-235">Interactable</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [<span data-ttu-id="cbd92-236">Button</span><span class="sxs-lookup"><span data-stu-id="cbd92-236">Button</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)
* [<span data-ttu-id="cbd92-237">手动交互示例场景</span><span class="sxs-lookup"><span data-stu-id="cbd92-237">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="cbd92-238">MixedRealityToolkit 的标准着色器提供了各种选项 **，例如，可** 帮助您创建视觉对象和音频提示。</span><span class="sxs-lookup"><span data-stu-id="cbd92-238">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>

* [<span data-ttu-id="cbd92-239">MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="cbd92-239">MRTK Standard Shader</span></span>](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="cbd92-240">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cbd92-240">See also</span></span>

* [<span data-ttu-id="cbd92-241">光标</span><span class="sxs-lookup"><span data-stu-id="cbd92-241">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="cbd92-242">手部射线</span><span class="sxs-lookup"><span data-stu-id="cbd92-242">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="cbd92-243">Button</span><span class="sxs-lookup"><span data-stu-id="cbd92-243">Button</span></span>](button.md)
* [<span data-ttu-id="cbd92-244">可交互对象</span><span class="sxs-lookup"><span data-stu-id="cbd92-244">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="cbd92-245">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="cbd92-245">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="cbd92-246">操作</span><span class="sxs-lookup"><span data-stu-id="cbd92-246">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="cbd92-247">手动菜单</span><span class="sxs-lookup"><span data-stu-id="cbd92-247">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="cbd92-248">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="cbd92-248">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="cbd92-249">对象集合</span><span class="sxs-lookup"><span data-stu-id="cbd92-249">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="cbd92-250">语音命令</span><span class="sxs-lookup"><span data-stu-id="cbd92-250">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="cbd92-251">键盘</span><span class="sxs-lookup"><span data-stu-id="cbd92-251">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="cbd92-252">工具提示</span><span class="sxs-lookup"><span data-stu-id="cbd92-252">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="cbd92-253">平板</span><span class="sxs-lookup"><span data-stu-id="cbd92-253">Slate</span></span>](slate.md)
* [<span data-ttu-id="cbd92-254">滑块</span><span class="sxs-lookup"><span data-stu-id="cbd92-254">Slider</span></span>](slider.md)
* [<span data-ttu-id="cbd92-255">着色器</span><span class="sxs-lookup"><span data-stu-id="cbd92-255">Shader</span></span>](shader.md)
* [<span data-ttu-id="cbd92-256">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="cbd92-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="cbd92-257">显示进度</span><span class="sxs-lookup"><span data-stu-id="cbd92-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="cbd92-258">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="cbd92-258">Surface magnetism</span></span>](surface-magnetism.md)