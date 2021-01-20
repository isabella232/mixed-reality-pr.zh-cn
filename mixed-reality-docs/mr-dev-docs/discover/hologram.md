---
title: 什么是全息图？
description: HoloLens 使你可以查看与世界上出现在世界各地的光线和声音的三维全息影像，并与之交互。
author: hferrone
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，HoloLens，全息影像，设计，交互，混合现实耳机，windows Mixed reality 耳机，增加的现实情况
ms.openlocfilehash: cc6b4a4838e7a275b1ef3a45e54c4b894a04b9c2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583339"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="1518c-104">什么是全息图？</span><span class="sxs-lookup"><span data-stu-id="1518c-104">What is a hologram?</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


<span data-ttu-id="1518c-105">HoloLens 使你能够创建 **全息影像**，这是像像现实对象一样出现在世界各地的光线和声音的对象。</span><span class="sxs-lookup"><span data-stu-id="1518c-105">HoloLens lets you create **holograms**, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="1518c-106">全息影像会响应你的 [注视](../design/gaze-and-commit.md)、 [手势](../design/gaze-and-commit.md#composite-gestures)和 [语音命令](../design/voice-input.md)。</span><span class="sxs-lookup"><span data-stu-id="1518c-106">Holograms respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures), and [voice commands](../design/voice-input.md).</span></span> <span data-ttu-id="1518c-107">它们甚至可以与您周围的 [真实表面](../design/spatial-mapping.md) 交互。</span><span class="sxs-lookup"><span data-stu-id="1518c-107">They can even interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="1518c-108">利用全息影像，可以创建属于你的世界的数字对象。</span><span class="sxs-lookup"><span data-stu-id="1518c-108">With holograms, you can create digital objects that are part of your world.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="1518c-109">设备支持</span><span class="sxs-lookup"><span data-stu-id="1518c-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1518c-110"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="1518c-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="1518c-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="1518c-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="1518c-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="1518c-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="1518c-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="1518c-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1518c-114">全息影像</span><span class="sxs-lookup"><span data-stu-id="1518c-114">Holograms</span></span></td>
        <td><span data-ttu-id="1518c-115">✔️</span><span class="sxs-lookup"><span data-stu-id="1518c-115">✔️</span></span></td>
        <td><span data-ttu-id="1518c-116">✔️</span><span class="sxs-lookup"><span data-stu-id="1518c-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="1518c-117">全息图是由光和声音组成的</span><span class="sxs-lookup"><span data-stu-id="1518c-117">A hologram is made of light and sound</span></span>

<span data-ttu-id="1518c-118">HoloLens [呈现](../develop/platform-capabilities-and-apis/rendering.md) 的全息影像会直接显示在用户眼睛的前方。</span><span class="sxs-lookup"><span data-stu-id="1518c-118">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="1518c-119">全息影像为你的世界增加了灯光，这意味着你会看到来自显示器的灯光和来自你周围的光线。</span><span class="sxs-lookup"><span data-stu-id="1518c-119">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="1518c-120">HoloLens 不会从眼睛中去除光，因此无法用黑色呈现全息影像。</span><span class="sxs-lookup"><span data-stu-id="1518c-120">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="1518c-121">但黑色内容将显示为透明。</span><span class="sxs-lookup"><span data-stu-id="1518c-121">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="1518c-122">全息影像可以有许多不同的外观和行为。</span><span class="sxs-lookup"><span data-stu-id="1518c-122">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="1518c-123">有些是真实的、坚实的，而有些则是 cartoonish 和 ethereal。</span><span class="sxs-lookup"><span data-stu-id="1518c-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="1518c-124">你可以使用全息影像突出显示你的环境中的功能，或将其用作应用用户界面中的元素。</span><span class="sxs-lookup"><span data-stu-id="1518c-124">You can use holograms to highlight features in your surroundings or use them as elements in your app's user interface.</span></span>

![手动操作全息图](images/hologram-hands-940px.jpg)

<span data-ttu-id="1518c-126">全息影像还可以发出 [声音](../design/spatial-sound.md)，这会显示在周围的特定位置。</span><span class="sxs-lookup"><span data-stu-id="1518c-126">Holograms can also make [sounds](../design/spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="1518c-127">在 HoloLens 上，声音来自两个扬声器，它们直接位于你的耳上方，而不会覆盖它们。</span><span class="sxs-lookup"><span data-stu-id="1518c-127">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="1518c-128">与显示器类似，扬声器是累加的，引入新声音，而不会阻止环境中的声音。</span><span class="sxs-lookup"><span data-stu-id="1518c-128">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="1518c-129">全息图可以放在世界上，也可以与你一起标记</span><span class="sxs-lookup"><span data-stu-id="1518c-129">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="1518c-130">当你有一个特定位置用于全息图时，你可以在世界上准确地 [放置](../design/coordinate-systems.md) 该位置。</span><span class="sxs-lookup"><span data-stu-id="1518c-130">When you have a particular location for a hologram, you can [place](../design/coordinate-systems.md) it precisely at that point in the world.</span></span> <span data-ttu-id="1518c-131">在四处浏览时，全息图会根据您的世界来保持稳定。</span><span class="sxs-lookup"><span data-stu-id="1518c-131">As you walk around, the hologram appears stable based on the world around you.</span></span> <span data-ttu-id="1518c-132">如果使用 [空间锚点](../design/coordinate-systems.md#spatial-anchors) 固定对象，则系统甚至可以在以后回来时记住它的位置。</span><span class="sxs-lookup"><span data-stu-id="1518c-132">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin the object, the system can even remember where you left it when you come back later.</span></span>

![在零售空间中使用 Microsoft Dynamics 365 布局的两个男人](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="1518c-134">某些全息影像会按照用户的喜好进行操作，而不管用户在何处进行定位。</span><span class="sxs-lookup"><span data-stu-id="1518c-134">Some holograms follow the user instead, positioning themselves based on the user no matter where they walk.</span></span> <span data-ttu-id="1518c-135">你甚至可以选择将一段时间带到一段时间，然后将其放在墙上的另一个房间。</span><span class="sxs-lookup"><span data-stu-id="1518c-135">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="1518c-136">**最佳实践**</span><span class="sxs-lookup"><span data-stu-id="1518c-136">**Best practices**</span></span>
* <span data-ttu-id="1518c-137">在某些情况下，可能需要在整个体验中轻松发现和查看全息影像。</span><span class="sxs-lookup"><span data-stu-id="1518c-137">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="1518c-138">此类定位有两个高级方法。</span><span class="sxs-lookup"><span data-stu-id="1518c-138">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="1518c-139">让我们将它们称为 **"显示-锁定"** 和 **"正文锁定"**。</span><span class="sxs-lookup"><span data-stu-id="1518c-139">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="1518c-140">显示锁定的内容按位置 "锁定" 到设备显示。</span><span class="sxs-lookup"><span data-stu-id="1518c-140">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="1518c-141">由于多种原因，这种类型的内容有点棘手，其中包括 "clingyness" 非自然的 ""，这使得许多用户感到沮丧并希望 "将其关闭"。</span><span class="sxs-lookup"><span data-stu-id="1518c-141">This type of content is tricky for several reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="1518c-142">通常，许多设计人员发现，更好的做法是避免显示锁定内容。</span><span class="sxs-lookup"><span data-stu-id="1518c-142">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="1518c-143">主体锁定的方法远远 forgivable。</span><span class="sxs-lookup"><span data-stu-id="1518c-143">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="1518c-144">当您在三维空间中接入到用户的主体或注视着矢量时，会锁定正文。</span><span class="sxs-lookup"><span data-stu-id="1518c-144">Body-locking is when you tether a hologram to the user's body or gaze vector in 3d space.</span></span> <span data-ttu-id="1518c-145">许多经验都采用了一种正文锁定行为，其中全息图 "跟随" 用户看，这使用户可以旋转其身体，而不会丢失全息影像。</span><span class="sxs-lookup"><span data-stu-id="1518c-145">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="1518c-146">合并延迟有助于使全息图移动更加自然。</span><span class="sxs-lookup"><span data-stu-id="1518c-146">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="1518c-147">例如，Windows 全息版 OS 的某些核心 UI 使用的是正文锁定，这种情况下，用户将看起来像是一种灵活的、弹性的延迟，同时用户会将其标头。</span><span class="sxs-lookup"><span data-stu-id="1518c-147">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="1518c-148">将全息图放置在舒适的观看距离上，通常会远离1-2 米。</span><span class="sxs-lookup"><span data-stu-id="1518c-148">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="1518c-149">为必须在全息帧中连续的元素提供偏移量，或在用户更改其视图时考虑将内容动态显示在一侧。</span><span class="sxs-lookup"><span data-stu-id="1518c-149">Provide a drift amount for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="1518c-150">**将全息影像置于最佳区域-介于 1.25 m 和 5 m 之间**</span><span class="sxs-lookup"><span data-stu-id="1518c-150">**Place holograms in the optimal zone - between 1.25 m and 5 m**</span></span>

<span data-ttu-id="1518c-151">这两个指标最适用，体验会降低从1米开始的距离。</span><span class="sxs-lookup"><span data-stu-id="1518c-151">Two meters is the most optimal, and the experience will degrade the closer you get from 1 meter.</span></span> <span data-ttu-id="1518c-152">在接近1米的距离上，定期移动的全息影像比静态全息影像更有可能出现问题。</span><span class="sxs-lookup"><span data-stu-id="1518c-152">At distances nearer than 1 meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="1518c-153">当内容太近时，请考虑适当地剪辑或淡化内容，以便不会使用户成为意外体验。</span><span class="sxs-lookup"><span data-stu-id="1518c-153">Consider gracefully clipping or fading out your content when it gets too close so you don't jar the user into an unexpected experience.</span></span>

![从用户放置全息影像的最佳距离。](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="1518c-155">全息图与您和您的世界交互</span><span class="sxs-lookup"><span data-stu-id="1518c-155">A hologram interacts with you and your world</span></span>

<span data-ttu-id="1518c-156">全息影像不仅适用于灯光和声音;它们也是您世界的一个活动部分。</span><span class="sxs-lookup"><span data-stu-id="1518c-156">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="1518c-157">用手看一个全息影像和手势，然后就可以开始使用全息图。</span><span class="sxs-lookup"><span data-stu-id="1518c-157">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="1518c-158">向全息影像发出语音命令，然后可以回复。</span><span class="sxs-lookup"><span data-stu-id="1518c-158">Give a voice command to a hologram, and it can reply.</span></span>

![一组政府实用工作人员组，使用 Microsoft HoloLens 2 在风场开发项目上协作](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="1518c-160">全息影像实现了不可能在其他地方使用的个人交互。</span><span class="sxs-lookup"><span data-stu-id="1518c-160">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="1518c-161">因为 HoloLens 知道其在世界各地的位置，所以，当您在房间内浏览时，全息字符可以直接显示您的眼睛。</span><span class="sxs-lookup"><span data-stu-id="1518c-161">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="1518c-162">全息图还可以与你的环境交互。</span><span class="sxs-lookup"><span data-stu-id="1518c-162">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="1518c-163">例如，您可以将一个全息弹跳球置于一个表上方。</span><span class="sxs-lookup"><span data-stu-id="1518c-163">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="1518c-164">然后，通过 [点击](../design/gaze-and-commit.md#composite-gestures)，观看球弹跳，并在到达表时发出声音。</span><span class="sxs-lookup"><span data-stu-id="1518c-164">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce, and make sound when it hits the table.</span></span>

<span data-ttu-id="1518c-165">全息影像还可以由真实的对象封闭像素。</span><span class="sxs-lookup"><span data-stu-id="1518c-165">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="1518c-166">例如，全息人物可能会走出大门的门和背面。</span><span class="sxs-lookup"><span data-stu-id="1518c-166">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="1518c-167">**有关集成全息影像和现实世界的技巧**</span><span class="sxs-lookup"><span data-stu-id="1518c-167">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="1518c-168">与 gravitational 规则相协调，可以更轻松地与和更可信相关。</span><span class="sxs-lookup"><span data-stu-id="1518c-168">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="1518c-169">例如：将一个全息狗置于 & 表上的花瓶，而不是让它们在空间中浮动。</span><span class="sxs-lookup"><span data-stu-id="1518c-169">for example: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="1518c-170">许多设计人员发现，他们可以通过在可信的表面上创建 "负阴影" 来集成更多的全息影像。</span><span class="sxs-lookup"><span data-stu-id="1518c-170">Many designers have found that they can integrate more believable holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="1518c-171">为此，可在两个全息图的地面上创建软光亮，然后从发光中减去 "阴影"。</span><span class="sxs-lookup"><span data-stu-id="1518c-171">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="1518c-172">软发光与现实世界中的灯光相集成，后者使用阴影来表示环境中的全息影像。</span><span class="sxs-lookup"><span data-stu-id="1518c-172">The soft glow integrates with the light from the real world, which uses the shadow to ground the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a><span data-ttu-id="1518c-173">全息图</span><span class="sxs-lookup"><span data-stu-id="1518c-173">A hologram is whatever</span></span> <br><span data-ttu-id="1518c-174">你可以梦想</span><span class="sxs-lookup"><span data-stu-id="1518c-174">you can dream up</span></span><br>
        <span data-ttu-id="1518c-175">作为全息开发人员，您可以将您的创造性从2D 屏幕和世界各地突破起来。</span><span class="sxs-lookup"><span data-stu-id="1518c-175">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="1518c-176">*你* 将生成什么？</span><span class="sxs-lookup"><span data-stu-id="1518c-176">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="1518c-177">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="1518c-177">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="1518c-178">![客厅的全息虚世界](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="1518c-178">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="1518c-179">下一个发现检查点</span><span class="sxs-lookup"><span data-stu-id="1518c-179">Next Discovery Checkpoint</span></span>

<span data-ttu-id="1518c-180">如果你按安排的[发现之旅](get-started-with-mr.md)操作，则你正在了解混合现实的基本知识。</span><span class="sxs-lookup"><span data-stu-id="1518c-180">If you're following the [discovery journey](get-started-with-mr.md) we've laid out, you're in the midst of exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="1518c-181">从这里，你可以进入下一基本主题：</span><span class="sxs-lookup"><span data-stu-id="1518c-181">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="1518c-182">扩展设计过程</span><span class="sxs-lookup"><span data-stu-id="1518c-182">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)