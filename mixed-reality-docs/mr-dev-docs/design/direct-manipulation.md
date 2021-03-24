---
title: 用手直接操作
description: 了解直接操作，一种输入模型，用户可在此输入模型中用手直接接触全息影像。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, 凝视, 设定凝视目标, 交互, 设计, 手动近距, HoloLens, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, MRTK, 混合现实工具包, 按钮, 碰撞体, 边界框, 2D, 本能手势
ms.openlocfilehash: 8316452b8308e159612a81d097c352cf1d935362
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "101759319"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="acb4e-104">用手直接操作</span><span class="sxs-lookup"><span data-stu-id="acb4e-104">Direct manipulation with hands</span></span>

![Button](images/UX_Hero_Manipulation.jpg)

<span data-ttu-id="acb4e-106">直接操作是一个输入模型，涉及到用手直接触摸全息影像。</span><span class="sxs-lookup"><span data-stu-id="acb4e-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="acb4e-107">此概念后面的理念是使对象的行为如同在现实世界中一样自然。</span><span class="sxs-lookup"><span data-stu-id="acb4e-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="acb4e-108">只需按下按钮就能将其激活，抓取对象可以拾取对象，2D 内容的行为与在虚拟触摸屏上类似。</span><span class="sxs-lookup"><span data-stu-id="acb4e-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="acb4e-109">直接操作基于视觉元素，因此具备用户友好性。</span><span class="sxs-lookup"><span data-stu-id="acb4e-109">Direct manipulation is affordance-based, meaning it's user-friendly.</span></span> <span data-ttu-id="acb4e-110">没有任何符号手势可以向用户传授操作方法。</span><span class="sxs-lookup"><span data-stu-id="acb4e-110">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="acb4e-111">所有交互都是围绕一个可以触摸或抓取的可视元素构建的。</span><span class="sxs-lookup"><span data-stu-id="acb4e-111">All interactions are built around a visual element that you can touch or grab.</span></span> <span data-ttu-id="acb4e-112">它被视为一种“近距”输入模型，这意味着，它最好用于与手臂可触及范围内的内容进行交互。</span><span class="sxs-lookup"><span data-stu-id="acb4e-112">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

## <a name="device-support"></a><span data-ttu-id="acb4e-113">设备支持</span><span class="sxs-lookup"><span data-stu-id="acb4e-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="acb4e-114"><strong>输入模型</strong></span><span class="sxs-lookup"><span data-stu-id="acb4e-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="acb4e-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="acb4e-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="acb4e-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="acb4e-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
     <td><span data-ttu-id="acb4e-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="acb4e-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="acb4e-118">用手直接操作</span><span class="sxs-lookup"><span data-stu-id="acb4e-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="acb4e-119">❌ 不支持</span><span class="sxs-lookup"><span data-stu-id="acb4e-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="acb4e-120">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="acb4e-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="acb4e-121">➕ 支持。</span><span class="sxs-lookup"><span data-stu-id="acb4e-121">➕ Supported.</span></span>  <span data-ttu-id="acb4e-122">对于 UI，我们建议改为<a href="point-and-commit.md">使用手指向和提交</a>。</span><span class="sxs-lookup"><span data-stu-id="acb4e-122">For UI, we recommend <a href="point-and-commit.md">point and commit with hands</a> instead.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="acb4e-123">直接操作是 HoloLens 2 中的主要输入模型，使用最新的语音式手动跟踪系统。</span><span class="sxs-lookup"><span data-stu-id="acb4e-123">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="acb4e-124">还可以通过运动控制器在沉浸式头戴显示设备中使用该输入模型，但不建议将它用作对象操作以外的主要交互方式。</span><span class="sxs-lookup"><span data-stu-id="acb4e-124">The input model is also available on immersive headsets by using motion controllers, but isn't recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="acb4e-125">直接操作在 HoloLens（第 1 代）中不可用。</span><span class="sxs-lookup"><span data-stu-id="acb4e-125">Direct manipulation isn't available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="collidable-fingertip"></a><span data-ttu-id="acb4e-126">可碰撞指尖</span><span class="sxs-lookup"><span data-stu-id="acb4e-126">Collidable fingertip</span></span>

<span data-ttu-id="acb4e-127">在 HoloLens 2 上，用户的手部将被识别并解释为左右手骨架模型。</span><span class="sxs-lookup"><span data-stu-id="acb4e-127">On HoloLens 2, the user's hands are recognized and interpreted as left and right-hand skeletal models.</span></span> <span data-ttu-id="acb4e-128">为了实现直接用手触摸全息影像的思路，理想情况下，可将 5 个碰撞体附加到每个手部骨架模型的 5 个指尖。</span><span class="sxs-lookup"><span data-stu-id="acb4e-128">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="acb4e-129">但是，由于缺少触觉反馈，使用 10 个可碰撞指尖可能会导致全息影像中发生意外且不可预测的碰撞。</span><span class="sxs-lookup"><span data-stu-id="acb4e-129">However, because of the lack of tactile feedback, 10 collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="acb4e-130">建议只在每个食指上放置一个碰撞体。</span><span class="sxs-lookup"><span data-stu-id="acb4e-130">We suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="acb4e-131">可碰撞的食指指尖仍可充当涉及其他手指的各种触摸手势的触摸点。</span><span class="sxs-lookup"><span data-stu-id="acb4e-131">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers.</span></span> <span data-ttu-id="acb4e-132">触摸手势包括一指按压、一指点击、两指按压、五指按压，如下所示：</span><span class="sxs-lookup"><span data-stu-id="acb4e-132">Touch gestures include One-finger press, One-finger tap, Two-finger press, and Five-finger press, as shown below:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="acb4e-133">![可碰撞指尖](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-133">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="acb4e-134">**可碰撞指尖**</span><span class="sxs-lookup"><span data-stu-id="acb4e-134">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-135">![单指按下](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-135">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="acb4e-136">**单指按下**</span><span class="sxs-lookup"><span data-stu-id="acb4e-136">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-137">![单指点击](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-137">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="acb4e-138">**单指点击**</span><span class="sxs-lookup"><span data-stu-id="acb4e-138">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-139">![五指按下](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-139">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="acb4e-140">**五指按下**</span><span class="sxs-lookup"><span data-stu-id="acb4e-140">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="acb4e-141">球体碰撞体</span><span class="sxs-lookup"><span data-stu-id="acb4e-141">Sphere collider</span></span>

<span data-ttu-id="acb4e-142">如果不使用随机的一般形状，我们建议使用球体碰撞体。</span><span class="sxs-lookup"><span data-stu-id="acb4e-142">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="acb4e-143">然后即可以可视方式渲染它，以便为近距定位提供更好的线索。</span><span class="sxs-lookup"><span data-stu-id="acb4e-143">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="acb4e-144">该球体的直径应与食指的粗细相匹配，以提高触摸准确度。</span><span class="sxs-lookup"><span data-stu-id="acb4e-144">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="acb4e-145">可以通过调用手部 API 来更轻松地检索手指粗细的变量。</span><span class="sxs-lookup"><span data-stu-id="acb4e-145">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="acb4e-146">指尖光标</span><span class="sxs-lookup"><span data-stu-id="acb4e-146">Fingertip cursor</span></span>

<span data-ttu-id="acb4e-147">除了在食指指尖上渲染可碰撞球体以外，我们还创建了一个高级指尖光标来实现更好的近距定位体验。</span><span class="sxs-lookup"><span data-stu-id="acb4e-147">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to achieve a better near-targeting experience.</span></span> <span data-ttu-id="acb4e-148">它是附在食指上的一个圆环形光标。</span><span class="sxs-lookup"><span data-stu-id="acb4e-148">It's a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="acb4e-149">根据邻近性，它会对目标的方向和大小做出动态反应，下面提供了详述：</span><span class="sxs-lookup"><span data-stu-id="acb4e-149">According to proximity, it dynamically reacts to a target for orientation and size as detailed below:</span></span>

* <span data-ttu-id="acb4e-150">将食指移向全息影像时，该光标始终与全息影像的表面平行，在移动过程中会逐渐缩小其大小。</span><span class="sxs-lookup"><span data-stu-id="acb4e-150">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size.</span></span>
* <span data-ttu-id="acb4e-151">一旦手指接触到表面，该光标就会缩小为一个点，并发出触摸事件。</span><span class="sxs-lookup"><span data-stu-id="acb4e-151">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="acb4e-152">借助交互式反馈，用户可以实现高精度的近距定位任务，例如，触发超链接，或按下某个按钮，如下所示。</span><span class="sxs-lookup"><span data-stu-id="acb4e-152">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="acb4e-153">![指尖光标远](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-153">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="acb4e-154">**指尖光标远**</span><span class="sxs-lookup"><span data-stu-id="acb4e-154">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-155">![指尖光标近](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-155">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="acb4e-156">**指尖光标近**</span><span class="sxs-lookup"><span data-stu-id="acb4e-156">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-157">![指尖光标接触](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-157">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="acb4e-158">**指尖光标接触**</span><span class="sxs-lookup"><span data-stu-id="acb4e-158">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="acb4e-159">带有邻近着色器的边界框</span><span class="sxs-lookup"><span data-stu-id="acb4e-159">Bounding box with proximity shader</span></span>

<span data-ttu-id="acb4e-160">全息影像本身还需要能够提供视频和音频反馈，以补偿触觉反馈的缺失。</span><span class="sxs-lookup"><span data-stu-id="acb4e-160">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="acb4e-161">为此，我们提出了带有邻近着色器的边界框的概念。</span><span class="sxs-lookup"><span data-stu-id="acb4e-161">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="acb4e-162">边界框是包含一个 3D 对象的紧凑立体区域。</span><span class="sxs-lookup"><span data-stu-id="acb4e-162">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="acb4e-163">边界框提供名为“邻近着色器”的交互式渲染机制。</span><span class="sxs-lookup"><span data-stu-id="acb4e-163">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="acb4e-164">邻近着色器的行为：</span><span class="sxs-lookup"><span data-stu-id="acb4e-164">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="acb4e-165">![通过视觉反馈进行悬停（远）](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-165">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="acb4e-166">**悬停（远）**</span><span class="sxs-lookup"><span data-stu-id="acb4e-166">**Hover (far)**</span></span><br>
       <span data-ttu-id="acb4e-167">当食指处于某个范围内时，指尖光点会投射到边界框的表面。</span><span class="sxs-lookup"><span data-stu-id="acb4e-167">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-168">![通过视觉反馈进行悬停（近）](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-168">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="acb4e-169">**悬停（近）**</span><span class="sxs-lookup"><span data-stu-id="acb4e-169">**Hover (near)**</span></span><br>
        <span data-ttu-id="acb4e-170">当指尖更靠近表面时，光点会收缩。</span><span class="sxs-lookup"><span data-stu-id="acb4e-170">When the fingertip gets closer to the surface, the spotlight shrinks.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-171">![接触开始](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-171">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="acb4e-172">**接触开始**</span><span class="sxs-lookup"><span data-stu-id="acb4e-172">**Contact begins**</span></span><br>
       <span data-ttu-id="acb4e-173">一旦指尖接触到表面，整个边界框就会改变颜色，或生成视觉效果来反映触摸状态。</span><span class="sxs-lookup"><span data-stu-id="acb4e-173">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-174">![接触结束](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-174">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="acb4e-175">**接触结束**</span><span class="sxs-lookup"><span data-stu-id="acb4e-175">**Contact ends**</span></span><br>
       <span data-ttu-id="acb4e-176">还可以激活某种音效来增强视觉触摸反馈。</span><span class="sxs-lookup"><span data-stu-id="acb4e-176">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="acb4e-177">可按按钮</span><span class="sxs-lookup"><span data-stu-id="acb4e-177">Pressable button</span></span>

<span data-ttu-id="acb4e-178">现在，用户可以使用可碰撞指尖来与一个基本的全息图 UI 组件（例如，可按按钮）进行交互。</span><span class="sxs-lookup"><span data-stu-id="acb4e-178">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="acb4e-179">可按按钮是专门用手指直接按下的全息图按钮。</span><span class="sxs-lookup"><span data-stu-id="acb4e-179">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="acb4e-180">同样，由于缺少触觉反馈，可按按钮配备了两个机制来解决触觉反馈相关的问题。</span><span class="sxs-lookup"><span data-stu-id="acb4e-180">Again, because of the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="acb4e-181">第一个机制是上一部分已详述的带有邻近着色器的边界框。</span><span class="sxs-lookup"><span data-stu-id="acb4e-181">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="acb4e-182">该机制可以在用户接近和接触到某个按钮时提供更好的邻近感。</span><span class="sxs-lookup"><span data-stu-id="acb4e-182">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="acb4e-183">第二个机制是沉降。</span><span class="sxs-lookup"><span data-stu-id="acb4e-183">The second mechanism is depression.</span></span> <span data-ttu-id="acb4e-184">在指尖接触到按钮后，沉降可产生一种按入感。</span><span class="sxs-lookup"><span data-stu-id="acb4e-184">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="acb4e-185">此机制确保按钮在深度轴上如影随形地与指尖一起移动。</span><span class="sxs-lookup"><span data-stu-id="acb4e-185">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="acb4e-186">当指尖达到选定的深度（按下按钮），或者在移过按钮后脱离该深度（松开按钮）时，可以触发按钮。</span><span class="sxs-lookup"><span data-stu-id="acb4e-186">The button can be triggered when it reaches a chosen depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="acb4e-187">触发按钮时，应该添加音效来增强反馈。</span><span class="sxs-lookup"><span data-stu-id="acb4e-187">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="acb4e-188">![可按按钮远](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-188">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="acb4e-189">**手指远离**</span><span class="sxs-lookup"><span data-stu-id="acb4e-189">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-190">![可按按钮近](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-190">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="acb4e-191">**手指接近**</span><span class="sxs-lookup"><span data-stu-id="acb4e-191">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-192">![可按按钮接触开始](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-192">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="acb4e-193">**接触开始**</span><span class="sxs-lookup"><span data-stu-id="acb4e-193">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-194">![可按按钮按下](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-194">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="acb4e-195">**按下**</span><span class="sxs-lookup"><span data-stu-id="acb4e-195">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="acb4e-196">2D 盖板交互</span><span class="sxs-lookup"><span data-stu-id="acb4e-196">2D slate interaction</span></span>

<span data-ttu-id="acb4e-197">2D [盖板](slate.md)是用于承载 Web 浏览器等 2D 应用内容的全息容器。</span><span class="sxs-lookup"><span data-stu-id="acb4e-197">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="acb4e-198">通过直接操作来与 2D 盖板交互的设计概念和与物理触摸屏交互时一样。</span><span class="sxs-lookup"><span data-stu-id="acb4e-198">The design concept for interacting with a 2D slate via direct manipulation is the same as interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="acb4e-199">若要与盖板触点交互</span><span class="sxs-lookup"><span data-stu-id="acb4e-199">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="acb4e-200">![触控](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-200">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="acb4e-201">**触控**</span><span class="sxs-lookup"><span data-stu-id="acb4e-201">**Touch**</span></span><br>
       <span data-ttu-id="acb4e-202">使用食指按下某个超链接或按钮。</span><span class="sxs-lookup"><span data-stu-id="acb4e-202">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-203">![滚动](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-203">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="acb4e-204">**滚动**</span><span class="sxs-lookup"><span data-stu-id="acb4e-204">**Scroll**</span></span><br>
        <span data-ttu-id="acb4e-205">使用食指上下滚动盖板内容。</span><span class="sxs-lookup"><span data-stu-id="acb4e-205">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-206">![缩放](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-206">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="acb4e-207">**缩放**</span><span class="sxs-lookup"><span data-stu-id="acb4e-207">**Zoom**</span></span><br>
       <span data-ttu-id="acb4e-208">用户使用两根食指根据手指的相对运动来放大和缩小盖板内容。</span><span class="sxs-lookup"><span data-stu-id="acb4e-208">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="acb4e-209">操作 2D 平板电脑本身</span><span class="sxs-lookup"><span data-stu-id="acb4e-209">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="acb4e-210">![显示抓取和拖动功能的图形](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-210">![Graphic showing grab and drag feature](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="acb4e-211">**移动**</span><span class="sxs-lookup"><span data-stu-id="acb4e-211">**Move**</span></span><br>
       <span data-ttu-id="acb4e-212">将手移近边角和边缘，显示最靠近的可视操作元素。</span><span class="sxs-lookup"><span data-stu-id="acb4e-212">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="acb4e-213">抓取 2D 盖板顶层的全息条，以移动整个盖板。</span><span class="sxs-lookup"><span data-stu-id="acb4e-213">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-214">![显示缩放功能的图形](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-214">![Graphic showing scale feature](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="acb4e-215">**缩放**</span><span class="sxs-lookup"><span data-stu-id="acb4e-215">**Scale**</span></span><br>
        <span data-ttu-id="acb4e-216">抓取操作视觉元素，通过边角视觉元素执行统一的缩放。</span><span class="sxs-lookup"><span data-stu-id="acb4e-216">Grab the manipulation affordances and do uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-217">![重新排列](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-217">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="acb4e-218">**重新排列**</span><span class="sxs-lookup"><span data-stu-id="acb4e-218">**Reflow**</span></span><br>
       <span data-ttu-id="acb4e-219">抓取操作视觉元素，通过编译视觉元素进行重排。</span><span class="sxs-lookup"><span data-stu-id="acb4e-219">Grab the manipulation affordances and do reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="acb4e-220">3D 对象操作</span><span class="sxs-lookup"><span data-stu-id="acb4e-220">3D object manipulation</span></span>

<span data-ttu-id="acb4e-221">HoloLens 2 可让用户将边界框应用到每个 3D 对象，以便用手引导和操作 3D 全息图对象。</span><span class="sxs-lookup"><span data-stu-id="acb4e-221">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="acb4e-222">边界框通过其邻近着色器提供更好的深度感。</span><span class="sxs-lookup"><span data-stu-id="acb4e-222">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="acb4e-223">使用边界框可以通过两种设计方法来操作 3D 对象。</span><span class="sxs-lookup"><span data-stu-id="acb4e-223">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="acb4e-224">基于可视操作元素的操作</span><span class="sxs-lookup"><span data-stu-id="acb4e-224">Affordance-based manipulation</span></span>

<span data-ttu-id="acb4e-225">使用基于视觉元素的操作可以通过边界框及其周围的操作视觉元素来操作 3D 对象。</span><span class="sxs-lookup"><span data-stu-id="acb4e-225">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="acb4e-226">![显示对象边界框和移动功能的图形](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-226">![Graphic showing an objects bounding box and move feature](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="acb4e-227">**移动**</span><span class="sxs-lookup"><span data-stu-id="acb4e-227">**Move**</span></span><br>
       <span data-ttu-id="acb4e-228">一旦用户的手靠近某个 3D 对象，就会显示边界框和最靠近的视觉元素。</span><span class="sxs-lookup"><span data-stu-id="acb4e-228">As soon as a user's hand is close to a 3D object, the bounding box, and the nearest affordance are revealed.</span></span> <span data-ttu-id="acb4e-229">用户可以抓取边界框来移动整个对象。</span><span class="sxs-lookup"><span data-stu-id="acb4e-229">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-230">![显示用户抓取对象边缘进行旋转的图形](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-230">![Graphic showing user grabbing an objects edge to rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="acb4e-231">**旋转**</span><span class="sxs-lookup"><span data-stu-id="acb4e-231">**Rotate**</span></span><br>
        <span data-ttu-id="acb4e-232">用户可以抓取边缘视觉元素执行旋转操作。</span><span class="sxs-lookup"><span data-stu-id="acb4e-232">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-233">![显示用户抓取对象边角进行缩放的图形](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-233">![Graphic showing user grabbing an objects corner to scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="acb4e-234">**缩放**</span><span class="sxs-lookup"><span data-stu-id="acb4e-234">**Scale**</span></span><br>
       <span data-ttu-id="acb4e-235">用户可以抓取边角视觉元素进行统一缩放。</span><span class="sxs-lookup"><span data-stu-id="acb4e-235">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="acb4e-236">不基于视觉元素的操作</span><span class="sxs-lookup"><span data-stu-id="acb4e-236">Non-affordance-based manipulation</span></span>

<span data-ttu-id="acb4e-237">非基于视觉元素的操作不会将任何视觉元素附加到边界框。</span><span class="sxs-lookup"><span data-stu-id="acb4e-237">Non-affordance-based manipulation doesn't attach affordance to the bounding box.</span></span> <span data-ttu-id="acb4e-238">用户只能显示边界框，然后直接与它交互。</span><span class="sxs-lookup"><span data-stu-id="acb4e-238">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="acb4e-239">如果用一只手抓取边界框，则对象的平移和旋转将与手的动作和方向相关联。</span><span class="sxs-lookup"><span data-stu-id="acb4e-239">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="acb4e-240">用两只手抓取对象时，用户可以根据两只手的相对运动来平移、缩放和旋转该对象。</span><span class="sxs-lookup"><span data-stu-id="acb4e-240">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="acb4e-241">具体的操作需要精确。</span><span class="sxs-lookup"><span data-stu-id="acb4e-241">Specific manipulation requires precision.</span></span> <span data-ttu-id="acb4e-242">我们建议使用 **基于视觉元素的操作**，因为它提供较高的粒度级。</span><span class="sxs-lookup"><span data-stu-id="acb4e-242">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="acb4e-243">若要灵活操作，我们建议使用 **非基于视觉元素的操作**，因为它可以实现充满乐趣的即时体验。</span><span class="sxs-lookup"><span data-stu-id="acb4e-243">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="acb4e-244">本能手势</span><span class="sxs-lookup"><span data-stu-id="acb4e-244">Instinctual gestures</span></span>

<span data-ttu-id="acb4e-245">在 HoloLens（第 1 代）中，我们已向用户传授了几种预定义的手势，例如“开花”和“隔空敲击”。</span><span class="sxs-lookup"><span data-stu-id="acb4e-245">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="acb4e-246">对于 HoloLens 2，我们不要求用户记住任何符号手势。</span><span class="sxs-lookup"><span data-stu-id="acb4e-246">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="acb4e-247">用户与全息影像和内容交互所要使用的全部手势都是本能的。</span><span class="sxs-lookup"><span data-stu-id="acb4e-247">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="acb4e-248">实现本能手势的方法是通过 UI 视觉元素的设计帮助用户执行手势。</span><span class="sxs-lookup"><span data-stu-id="acb4e-248">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="acb4e-249">例如，如果我们建议用户使用夹紧的两根手指来抓取某个对象或控制点，该对象或控制点应该很小。</span><span class="sxs-lookup"><span data-stu-id="acb4e-249">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="acb4e-250">如果我们希望用户执行五指抓取，则该对象或控制点应该相对较大。</span><span class="sxs-lookup"><span data-stu-id="acb4e-250">If we want the user to do a five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="acb4e-251">与按钮类似，按钮微小会导致用户使用单个手指将其按下的手势受限。</span><span class="sxs-lookup"><span data-stu-id="acb4e-251">Similar to buttons, a tiny button would limit users to press it with a single finger.</span></span> <span data-ttu-id="acb4e-252">大按钮使用户更有可能用手掌将其按下。</span><span class="sxs-lookup"><span data-stu-id="acb4e-252">A large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="acb4e-253">![显示用户抓取小型对象并移动的图形](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-253">![Graphic showing user grabbing small object to move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="acb4e-254">**小型对象**</span><span class="sxs-lookup"><span data-stu-id="acb4e-254">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-255">![显示用户抓取中等大小对象并移动的图形](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-255">![Graphic showing user grabbing medium object to move](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="acb4e-256">**中型对象**</span><span class="sxs-lookup"><span data-stu-id="acb4e-256">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="acb4e-257">![显示用户抓取大型对象并移动的图形](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="acb4e-257">![Graphic showing user grabbing large object to move](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="acb4e-258">**大型对象**</span><span class="sxs-lookup"><span data-stu-id="acb4e-258">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="acb4e-259">手部与 6 DoF 控制器之间的对称设计</span><span class="sxs-lookup"><span data-stu-id="acb4e-259">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="acb4e-260">你可能已经注意到，我们可以在 AR 中的手部与 VR 中的运动控制器之间引入类似的交互方式。</span><span class="sxs-lookup"><span data-stu-id="acb4e-260">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="acb4e-261">使用这两种输入可在其各自的环境中触发直接操作。</span><span class="sxs-lookup"><span data-stu-id="acb4e-261">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="acb4e-262">在 HoloLens 2 中，用手近距抓取和拖放非常类似于在 WMR 运动控制器中抓取按钮。</span><span class="sxs-lookup"><span data-stu-id="acb4e-262">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="acb4e-263">因此，用户会熟悉这两个平台中的交互方式。如果你决定在平台之间移植应用程序，这种类似性会很有帮助。</span><span class="sxs-lookup"><span data-stu-id="acb4e-263">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application between platforms.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="acb4e-264">使用眼动跟踪进行优化</span><span class="sxs-lookup"><span data-stu-id="acb4e-264">Optimize with eye tracking</span></span>

<span data-ttu-id="acb4e-265">如果直接操作按预期方式运行，则用户可能会觉得它充满魔力。</span><span class="sxs-lookup"><span data-stu-id="acb4e-265">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="acb4e-266">但是，如果只能在无意触发全息影像的情况下才能四处移动手部，则直接操作可能会带来困扰。</span><span class="sxs-lookup"><span data-stu-id="acb4e-266">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="acb4e-267">眼动追踪可能有助于更好地识别用户的意图。</span><span class="sxs-lookup"><span data-stu-id="acb4e-267">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="acb4e-268">**何时**：减少无意中触发操作响应的情况。</span><span class="sxs-lookup"><span data-stu-id="acb4e-268">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="acb4e-269">眼动追踪可以更好地识别用户当前正在与哪个对象互动。</span><span class="sxs-lookup"><span data-stu-id="acb4e-269">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="acb4e-270">例如，假设你在伸手抓取一个现实的工具时正在阅读某段全息图（说明）文本。</span><span class="sxs-lookup"><span data-stu-id="acb4e-270">For example, imagine you're reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="acb4e-271">此外，你的手会意外地移过某些以前未曾注意到的交互式全息图按钮。</span><span class="sxs-lookup"><span data-stu-id="acb4e-271">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before.</span></span> <span data-ttu-id="acb4e-272">例如，也许这些按钮在用户的视场 (FoV) 以外。</span><span class="sxs-lookup"><span data-stu-id="acb4e-272">For example, it  may be outside the user's field-of-view (FoV).</span></span>

<span data-ttu-id="acb4e-273">如果用户有一段时间未注视某张全息影像，但检测到了该全息图的触摸或抓取事件，则有可能交互行为是意外发生的。</span><span class="sxs-lookup"><span data-stu-id="acb4e-273">If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, the interaction is likely unintentional.</span></span>

* <span data-ttu-id="acb4e-274">**哪一个**：除了解决误报激活以外，另一个示例反映了眼动跟踪可以更好地识别要抓取或点击的全息影像，因为从你的立场来看，精确的交点可能并不明确，尤其是多个全息影像相互靠近时。</span><span class="sxs-lookup"><span data-stu-id="acb4e-274">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="acb4e-275">尽管 HoloLens 2 上的眼动跟踪在如何准确确定视线方面存在限制，但对于近距交互，它仍可以提供帮助，因为使用手动输入交互时，存在深度差异。</span><span class="sxs-lookup"><span data-stu-id="acb4e-275">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be helpful for near interactions because of depth disparity when interacting with hand input.</span></span> <span data-ttu-id="acb4e-276">举例而言，这意味着有时难以确定手是全息影像的前面还是后面，因此无法精确抓取某个操作小组件。</span><span class="sxs-lookup"><span data-stu-id="acb4e-276">This means it's sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="acb4e-277">**何处**：使用有关用户正在使用快速投射手势观看的内容的信息。</span><span class="sxs-lookup"><span data-stu-id="acb4e-277">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="acb4e-278">抓取一幅全息影像，然后大致将它投射到预期目标。</span><span class="sxs-lookup"><span data-stu-id="acb4e-278">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="acb4e-279">尽管有时可以正常进行此操作，但快速执行手势可能会导致目标极不准确。</span><span class="sxs-lookup"><span data-stu-id="acb4e-279">While this sometimes works, quickly doing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="acb4e-280">但是，眼动跟踪可以提高手势的准确度。</span><span class="sxs-lookup"><span data-stu-id="acb4e-280">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="acb4e-281">Unity 的 MRTK（混合现实工具包）中的操作</span><span class="sxs-lookup"><span data-stu-id="acb4e-281">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="acb4e-282">有了 [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)，便可使用脚本 ObjectManipulator 轻松实现常见的操作行为 。</span><span class="sxs-lookup"><span data-stu-id="acb4e-282">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ObjectManipulator**.</span></span> <span data-ttu-id="acb4e-283">借助 ObjectManipulator，可以直接使用手或手部射线抓取和移动对象。</span><span class="sxs-lookup"><span data-stu-id="acb4e-283">With ObjectManipulator, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="acb4e-284">它还支持使用双手操作来缩放和旋转对象。</span><span class="sxs-lookup"><span data-stu-id="acb4e-284">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="acb4e-285">MRTK - 操作</span><span class="sxs-lookup"><span data-stu-id="acb4e-285">MRTK - Manipulation</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-manipulator.md)

---

## <a name="see-also"></a><span data-ttu-id="acb4e-286">另请参阅</span><span class="sxs-lookup"><span data-stu-id="acb4e-286">See also</span></span>

* [<span data-ttu-id="acb4e-287">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="acb4e-287">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="acb4e-288">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="acb4e-288">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="acb4e-289">本能交互</span><span class="sxs-lookup"><span data-stu-id="acb4e-289">Instinctual interactions</span></span>](interaction-fundamentals.md)