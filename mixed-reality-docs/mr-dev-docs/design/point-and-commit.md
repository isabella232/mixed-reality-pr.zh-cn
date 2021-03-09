---
title: 使用手指向和提交
description: 了解混合现实应用程序中针对手势支持的指向和提交输入模型的基础知识。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, 交互, 设计, HoloLens, 手, 远距, 指向和提交, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, HoloLens, 手部射线, 对象操作, MRTK, 混合现实工具包, DoF
ms.openlocfilehash: 8196b67f103bae346ba4da065ee6045ff231b004
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759863"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="62fa9-104">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="62fa9-104">Point and commit with hands</span></span>

![光标](images/UX_Hero_HandRay.jpg)

<span data-ttu-id="62fa9-106">“用手指向和提交”是一种输入模型，它使用户能够对无法触及的 2D 和 3D 内容进行定位、选择和操作。</span><span class="sxs-lookup"><span data-stu-id="62fa9-106">Point and commit with hands is an input model that lets users target, select, and manipulate out of reach 2D and 3D content.</span></span> <span data-ttu-id="62fa9-107">这种“远程”交互技术是混合现实所独有的，因为人类不会自然地以这种方式与现实世界交互。</span><span class="sxs-lookup"><span data-stu-id="62fa9-107">This "far" interaction technique is unique to mixed reality because humans don't naturally interact with the real world that way.</span></span> <span data-ttu-id="62fa9-108">例如，在超级英雄电影《X 战警》中，角色 [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) 能够用手操控远处的对象。</span><span class="sxs-lookup"><span data-stu-id="62fa9-108">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) can manipulate far objects in the distance with his hands.</span></span> <span data-ttu-id="62fa9-109">这是人类在现实中无法做到的。</span><span class="sxs-lookup"><span data-stu-id="62fa9-109">This isn't something humans can do in reality.</span></span> <span data-ttu-id="62fa9-110">在 HoloLens (AR) 和混合现实 (MR) 中，我们赋予了用户这种神奇的力量，打破了现实世界的物理约束。</span><span class="sxs-lookup"><span data-stu-id="62fa9-110">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power to break the physical constraint of the real world.</span></span> <span data-ttu-id="62fa9-111">这不仅能让用户享受到愉悦的全息体验，还能让互动更加有效、高效。</span><span class="sxs-lookup"><span data-stu-id="62fa9-111">Not only is it a fun holographic experience, but it also makes user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="62fa9-112">设备支持</span><span class="sxs-lookup"><span data-stu-id="62fa9-112">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="62fa9-113"><strong>输入模型</strong></span><span class="sxs-lookup"><span data-stu-id="62fa9-113"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="62fa9-114"><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="62fa9-114"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="62fa9-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="62fa9-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="62fa9-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="62fa9-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="62fa9-117">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="62fa9-117">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="62fa9-118">❌ 不支持</span><span class="sxs-lookup"><span data-stu-id="62fa9-118">❌ Not supported</span></span></td>
     <td><span data-ttu-id="62fa9-119">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="62fa9-119">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="62fa9-120">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="62fa9-120">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="62fa9-121">“用手指向和提交”是使用新的铰接式手跟踪系统的新功能之一。</span><span class="sxs-lookup"><span data-stu-id="62fa9-121">_"Point and commit with hands"_ is one of the new features that use the new articulated hand-tracking system.</span></span> <span data-ttu-id="62fa9-122">该输入模型也是沉浸式头戴显示设备上通过使用运动控制器实现的主要输入模式。</span><span class="sxs-lookup"><span data-stu-id="62fa9-122">This input model is also the primary input model on immersive headsets by using motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="62fa9-123">手部射线</span><span class="sxs-lookup"><span data-stu-id="62fa9-123">Hand rays</span></span>

<span data-ttu-id="62fa9-124">在 HoloLens 2 上，我们创造了一种从用户手掌中心射出的手部射线。</span><span class="sxs-lookup"><span data-stu-id="62fa9-124">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="62fa9-125">该射线被视为手的延伸。</span><span class="sxs-lookup"><span data-stu-id="62fa9-125">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="62fa9-126">圆环形光标连接到射线的末端，以指示射线与目标对象相交的位置。</span><span class="sxs-lookup"><span data-stu-id="62fa9-126">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="62fa9-127">然后光标所指向的对象可以接收来自手的手势命令。</span><span class="sxs-lookup"><span data-stu-id="62fa9-127">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="62fa9-128">该基本手势命令通过使用拇指和食指进行隔空敲击动作来触发。</span><span class="sxs-lookup"><span data-stu-id="62fa9-128">This basic gestural command is triggered by using the thumb and index finger to do the air-tap action.</span></span> <span data-ttu-id="62fa9-129">通过使用手射线指向和隔空敲击以提交，用户可以激活某个按钮或超链接。</span><span class="sxs-lookup"><span data-stu-id="62fa9-129">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="62fa9-130">借助更多的复合手势，用户可以在 Web 内容中导航，并从远处操纵 3D 对象。</span><span class="sxs-lookup"><span data-stu-id="62fa9-130">With more composite gestures, users can navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="62fa9-131">手部射线的视觉设计也应对这些指向和提交状态做出反应，如下所述：</span><span class="sxs-lookup"><span data-stu-id="62fa9-131">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="62fa9-132">![手部射线指向](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="62fa9-132">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="62fa9-133">**“指向”状态**</span><span class="sxs-lookup"><span data-stu-id="62fa9-133">**Pointing state**</span></span><br>
        <span data-ttu-id="62fa9-134">在指向状态下，射线是虚线，光标是圆环形状  。</span><span class="sxs-lookup"><span data-stu-id="62fa9-134">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="62fa9-135">![手部射线提交](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="62fa9-135">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="62fa9-136">**“提交”状态**</span><span class="sxs-lookup"><span data-stu-id="62fa9-136">**Commit state**</span></span><br>
        <span data-ttu-id="62fa9-137">在提交状态下，光线变为实线，光标缩小为点  。</span><span class="sxs-lookup"><span data-stu-id="62fa9-137">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="transition-between-near-and-far"></a><span data-ttu-id="62fa9-138">在远近之间转换</span><span class="sxs-lookup"><span data-stu-id="62fa9-138">Transition between near and far</span></span>

<span data-ttu-id="62fa9-139">我们没有使用“食指指向”这样的特定手势来引导射线，而是将射线设计为从用户手掌中心发出。</span><span class="sxs-lookup"><span data-stu-id="62fa9-139">Instead of using specific gestures like "pointing with index finger" to direct the ray, we designed the ray to comout out from the center of the users' palm.</span></span> <span data-ttu-id="62fa9-140">这样，我们解放并留出了五根手指来做更多的操控性手势，如捏和抓。</span><span class="sxs-lookup"><span data-stu-id="62fa9-140">This way, we've released and reserved the Five Fingers for more manipulative gestures like pinch and grab.</span></span> <span data-ttu-id="62fa9-141">通过这种设计，我们只创建了一个心理模型 - 同一组手势用于远交互和近交互。</span><span class="sxs-lookup"><span data-stu-id="62fa9-141">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="62fa9-142">可以使用相同的抓取手势来操纵不同距离的对象。</span><span class="sxs-lookup"><span data-stu-id="62fa9-142">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="62fa9-143">射线的调用是自动的，并且基于邻近度，如下所述：</span><span class="sxs-lookup"><span data-stu-id="62fa9-143">The invocation of the rays is automatic and proximity-based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="62fa9-144">![近操作](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="62fa9-144">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="62fa9-145">**近操作**</span><span class="sxs-lookup"><span data-stu-id="62fa9-145">**Near manipulation**</span></span><br>
        <span data-ttu-id="62fa9-146">当对象在手臂长度范围（大约 50 cm）内时，射线会自动关闭，支持近距交互。</span><span class="sxs-lookup"><span data-stu-id="62fa9-146">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="62fa9-147">![远操作](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="62fa9-147">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="62fa9-148">**远操作**</span><span class="sxs-lookup"><span data-stu-id="62fa9-148">**Far manipulation**</span></span><br>
        <span data-ttu-id="62fa9-149">当对象距离超过 50 cm 时，将启用射线。</span><span class="sxs-lookup"><span data-stu-id="62fa9-149">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="62fa9-150">转换应该顺利无缝。</span><span class="sxs-lookup"><span data-stu-id="62fa9-150">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="62fa9-151">2D 平板电脑交互</span><span class="sxs-lookup"><span data-stu-id="62fa9-151">2D slate interaction</span></span>

<span data-ttu-id="62fa9-152">2D 盖板是装有 Web 浏览器等 2D 应用内容的全息容器。</span><span class="sxs-lookup"><span data-stu-id="62fa9-152">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="62fa9-153">与 2D 平板电脑进行远距离交互的设计理念是使用手部射线进行瞄准，并隔空敲击以进行选择。</span><span class="sxs-lookup"><span data-stu-id="62fa9-153">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="62fa9-154">在用手部射线瞄准目标后，用户可以通过隔空敲击来触发超链接或按钮。</span><span class="sxs-lookup"><span data-stu-id="62fa9-154">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="62fa9-155">他们可以用一只手“隔空敲击并拖动”来上下滚动盖板内容。</span><span class="sxs-lookup"><span data-stu-id="62fa9-155">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="62fa9-156">使用两只手进行隔空敲击和拖动的相对运动可以放大和缩小平板电脑内容。</span><span class="sxs-lookup"><span data-stu-id="62fa9-156">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="62fa9-157">在角落和边缘处瞄准手部射线可显示最接近的可视操作元素。</span><span class="sxs-lookup"><span data-stu-id="62fa9-157">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="62fa9-158">通过“抓取和拖动”操作视觉元素，用户可通过边角视觉元素进行统一缩放，然后通过边缘视觉元素重排盖板。</span><span class="sxs-lookup"><span data-stu-id="62fa9-158">By "grab and drag" manipulation affordances, users can do uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="62fa9-159">用户可以通过抓取并拖动 2D 盖板顶部的全息条来移动整个盖板。</span><span class="sxs-lookup"><span data-stu-id="62fa9-159">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="62fa9-160">![2D 盖板交互单击](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="62fa9-160">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="62fa9-161">**单击**</span><span class="sxs-lookup"><span data-stu-id="62fa9-161">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="62fa9-162">![2D 盖板交互滚动](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="62fa9-162">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="62fa9-163">**滚动**</span><span class="sxs-lookup"><span data-stu-id="62fa9-163">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="62fa9-164">![2D 盖板交互缩放](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="62fa9-164">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="62fa9-165">**缩放**</span><span class="sxs-lookup"><span data-stu-id="62fa9-165">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="62fa9-166">**操作 2D 盖板**</span><span class="sxs-lookup"><span data-stu-id="62fa9-166">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="62fa9-167">用户在角落或边缘处指向手部射线可显示最接近的可视操作元素。</span><span class="sxs-lookup"><span data-stu-id="62fa9-167">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="62fa9-168">通过对视觉元素应用操作手势，用户可通过边角视觉元素进行统一缩放，然后通过边缘视觉元素重排盖板。</span><span class="sxs-lookup"><span data-stu-id="62fa9-168">By applying a manipulation gesture on the affordance, users can do uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="62fa9-169">通过在 2D 盖板顶部的全息条上应用操纵手势，用户可以移动整个盖板。</span><span class="sxs-lookup"><span data-stu-id="62fa9-169">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>

<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="62fa9-170">3D 对象操作</span><span class="sxs-lookup"><span data-stu-id="62fa9-170">3D object manipulation</span></span>

<span data-ttu-id="62fa9-171">在直接操作中，用户可以通过两种方式操纵 3D 对象：基于视觉元素的操作和非基于视觉元素的操作。</span><span class="sxs-lookup"><span data-stu-id="62fa9-171">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="62fa9-172">在指向和提交模型中，用户能够通过手部射线实现完全相同的任务。</span><span class="sxs-lookup"><span data-stu-id="62fa9-172">In the point and commit model, users can achieve exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="62fa9-173">不需要额外的学习。</span><span class="sxs-lookup"><span data-stu-id="62fa9-173">No extra learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="62fa9-174">基于可视操作元素的操作</span><span class="sxs-lookup"><span data-stu-id="62fa9-174">Affordance-based manipulation</span></span>

<span data-ttu-id="62fa9-175">用户使用手部射线指向并显示边框和可视操作元素。</span><span class="sxs-lookup"><span data-stu-id="62fa9-175">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="62fa9-176">用户可在边框上应用操作手势来移动整个对象，在边缘视觉元素上应用操作手势来旋转对象，以及在边角视觉元素上应用操作手势以进行统一的缩放。</span><span class="sxs-lookup"><span data-stu-id="62fa9-176">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="62fa9-177">![3D 对象操作远移动](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="62fa9-177">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="62fa9-178">**移动**</span><span class="sxs-lookup"><span data-stu-id="62fa9-178">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="62fa9-179">![3D 对象操作远旋转](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="62fa9-179">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="62fa9-180">**旋转**</span><span class="sxs-lookup"><span data-stu-id="62fa9-180">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="62fa9-181">![3D 对象操作远缩放](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="62fa9-181">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="62fa9-182">**缩放**</span><span class="sxs-lookup"><span data-stu-id="62fa9-182">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::

### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="62fa9-183">非基于视觉元素的操作</span><span class="sxs-lookup"><span data-stu-id="62fa9-183">Non-affordance-based manipulation</span></span>

<span data-ttu-id="62fa9-184">用户用手部射线指向以显示边界框，然后直接对其应用操作手势。</span><span class="sxs-lookup"><span data-stu-id="62fa9-184">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="62fa9-185">如果用一只手进行操作，对象的平移和旋转将与手的移动和方向相关联。</span><span class="sxs-lookup"><span data-stu-id="62fa9-185">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="62fa9-186">如果用两只手进行操作，用户可以根据两只手的相对运动来平移、缩放和旋转对象。</span><span class="sxs-lookup"><span data-stu-id="62fa9-186">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="62fa9-187">本能手势</span><span class="sxs-lookup"><span data-stu-id="62fa9-187">Instinctual gestures</span></span>

<span data-ttu-id="62fa9-188">指向和提交的本能手势的概念类似于[用手直接操作](direct-manipulation.md)的概念。</span><span class="sxs-lookup"><span data-stu-id="62fa9-188">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="62fa9-189">用户在 3D 对象上执行的手势是由 UI 视觉元素的设计引导的。</span><span class="sxs-lookup"><span data-stu-id="62fa9-189">The gestures users do on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="62fa9-190">例如，一个小的控制点可能会促使用户用拇指和食指来捏，而用户可能希望用全部五根手指来抓一个较大的对象。</span><span class="sxs-lookup"><span data-stu-id="62fa9-190">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to use all Five Fingers to grab a larger object.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="62fa9-191">![本能手势远的小型对象](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="62fa9-191">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="62fa9-192">**小型对象**</span><span class="sxs-lookup"><span data-stu-id="62fa9-192">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="62fa9-193">![本能手势远的中型对象](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="62fa9-193">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="62fa9-194">**中型对象**</span><span class="sxs-lookup"><span data-stu-id="62fa9-194">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="62fa9-195">![本能手势远的大型对象](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="62fa9-195">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="62fa9-196">**大型对象**</span><span class="sxs-lookup"><span data-stu-id="62fa9-196">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="62fa9-197">手部与 6 DoF 控制器之间的对称设计</span><span class="sxs-lookup"><span data-stu-id="62fa9-197">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="62fa9-198">远程交互的指向和提交概念最初是为混合现实门户 (MRP) 创建和定义的。</span><span class="sxs-lookup"><span data-stu-id="62fa9-198">The concept of point and commit for far interaction was created and defined for the Mixed Reality Portal (MRP).</span></span> <span data-ttu-id="62fa9-199">在此场景下，用户戴上沉浸式头戴显示设备，通过运动控制器与 3D 对象进行交互。</span><span class="sxs-lookup"><span data-stu-id="62fa9-199">In this scenario, a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="62fa9-200">运动控制器射出光线来指向和操纵远处的对象。</span><span class="sxs-lookup"><span data-stu-id="62fa9-200">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="62fa9-201">控制器上有用于进一步提交不同操作的按钮。</span><span class="sxs-lookup"><span data-stu-id="62fa9-201">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="62fa9-202">我们应用射线的交互模式，并将其与双手关联。</span><span class="sxs-lookup"><span data-stu-id="62fa9-202">We apply the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="62fa9-203">借助这种对称设计，熟悉 MRP 的用户在使用 HoloLens 2 时不需要学习另一种交互模式来进行远距离指向和操纵，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="62fa9-203">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLens 2, and the other way around.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="62fa9-204">![带控制器的射线的对称设计](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="62fa9-204">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="62fa9-205">**控制器射线**</span><span class="sxs-lookup"><span data-stu-id="62fa9-205">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="62fa9-206">![带手的射线的对称设计](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="62fa9-206">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="62fa9-207">**手部射线**</span><span class="sxs-lookup"><span data-stu-id="62fa9-207">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="62fa9-208">Unity 的 MRTK（混合现实工具包）中的手部射线</span><span class="sxs-lookup"><span data-stu-id="62fa9-208">Hand ray in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="62fa9-209">默认情况下，MRTK 提供一个手部射线 prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers))，其视觉状态与 shell 的系统手部射线相同。</span><span class="sxs-lookup"><span data-stu-id="62fa9-209">By default, MRTK provides a hand ray prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) which has the same visual state as the shell's system hand ray.</span></span> <span data-ttu-id="62fa9-210">它分配在 MRTK 的输入配置文件的“指针”下。</span><span class="sxs-lookup"><span data-stu-id="62fa9-210">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="62fa9-211">在沉浸式头戴显示设备中，相同的射线会用于运动控制器。</span><span class="sxs-lookup"><span data-stu-id="62fa9-211">In an immersive headset, the same rays are used for the motion controllers.</span></span>

* [<span data-ttu-id="62fa9-212">MRTK - 指针配置文件</span><span class="sxs-lookup"><span data-stu-id="62fa9-212">MRTK - Pointer profile</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/mixed-reality-configuration-guide.md#pointer-configuration)
* [<span data-ttu-id="62fa9-213">MRTK - 输入系统</span><span class="sxs-lookup"><span data-stu-id="62fa9-213">MRTK - Input system</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md)
* [<span data-ttu-id="62fa9-214">MRTK - 指针</span><span class="sxs-lookup"><span data-stu-id="62fa9-214">MRTK - Pointers</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md)

---

## <a name="see-also"></a><span data-ttu-id="62fa9-215">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62fa9-215">See also</span></span>
* [<span data-ttu-id="62fa9-216">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="62fa9-216">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="62fa9-217">凝视和提交</span><span class="sxs-lookup"><span data-stu-id="62fa9-217">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="62fa9-218">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="62fa9-218">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="62fa9-219">手 - 手势</span><span class="sxs-lookup"><span data-stu-id="62fa9-219">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="62fa9-220">本能交互</span><span class="sxs-lookup"><span data-stu-id="62fa9-220">Instinctual interactions</span></span>](interaction-fundamentals.md)