---
title: 什么是全息图？
description: HoloLens 使你可以查看与世界上出现在世界各地的光线和声音的三维全息影像，并与之交互。
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality，HoloLens，全息影像，设计，交互，混合现实耳机，Windows Mixed reality 耳机，增加的现实情况
ms.openlocfilehash: bef2c378dcba54d3ed3da33262153f35d72c3cba
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634328"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="7373d-104">什么是全息图？</span><span class="sxs-lookup"><span data-stu-id="7373d-104">What is a hologram?</span></span>

<span data-ttu-id="7373d-105">HoloLens 使你可以查看 **全息影像**，这是像像现实对象一样出现在世界各地的光线和声音的对象。</span><span class="sxs-lookup"><span data-stu-id="7373d-105">HoloLens lets you view **holograms**, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="7373d-106">全息影像可以响应您的[注视](../design/gaze-and-commit.md)、[手势](../design/gaze-and-commit.md#composite-gestures)和[语音命令](../design/voice-input.md)。</span><span class="sxs-lookup"><span data-stu-id="7373d-106">Holograms can respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures), and [voice commands](../design/voice-input.md).</span></span> <span data-ttu-id="7373d-107">它们甚至可以与您周围的 [真实表面](../design/spatial-mapping.md) 交互。</span><span class="sxs-lookup"><span data-stu-id="7373d-107">They can even interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="7373d-108">全息影像是世界上的数字对象。</span><span class="sxs-lookup"><span data-stu-id="7373d-108">Holograms are digital objects that are part of your world.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

## <a name="device-support"></a><span data-ttu-id="7373d-109">设备支持</span><span class="sxs-lookup"><span data-stu-id="7373d-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7373d-110"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="7373d-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="7373d-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="7373d-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="7373d-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="7373d-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="7373d-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="7373d-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7373d-114">全息影像</span><span class="sxs-lookup"><span data-stu-id="7373d-114">Holograms</span></span></td>
        <td><span data-ttu-id="7373d-115">✔️</span><span class="sxs-lookup"><span data-stu-id="7373d-115">✔️</span></span></td>
        <td><span data-ttu-id="7373d-116">✔️</span><span class="sxs-lookup"><span data-stu-id="7373d-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="7373d-117">全息图是由光和声音组成的</span><span class="sxs-lookup"><span data-stu-id="7373d-117">A hologram is made of light and sound</span></span>

### <a name="light"></a><span data-ttu-id="7373d-118">亮</span><span class="sxs-lookup"><span data-stu-id="7373d-118">Light</span></span>

<span data-ttu-id="7373d-119">HoloLens[呈现](../develop/platform-capabilities-and-apis/rendering.md)的全息影像会直接显示在用户眼睛的前方。</span><span class="sxs-lookup"><span data-stu-id="7373d-119">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of users' eyes.</span></span> <span data-ttu-id="7373d-120">全息影像向您的世界添加灯光，这意味着您可以看到来自显示器的光线和来自您的周围世界的光线。</span><span class="sxs-lookup"><span data-stu-id="7373d-120">Holograms add light to your world, which means that you see both the light from the display and the light from your surrounding world.</span></span> <span data-ttu-id="7373d-121">由于 HoloLens 使用添加灯光的加法显示，因此黑色颜色将呈现为透明。</span><span class="sxs-lookup"><span data-stu-id="7373d-121">Since HoloLens uses an additive display that adds light, the black color will be rendered transparent.</span></span> 

<span data-ttu-id="7373d-122">全息影像的外观和行为可能会非常不同。</span><span class="sxs-lookup"><span data-stu-id="7373d-122">Holograms can have very different appearances and behaviors.</span></span> <span data-ttu-id="7373d-123">有些是真实的、坚实的，而有些则是 cartoonish 和 ethereal。</span><span class="sxs-lookup"><span data-stu-id="7373d-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="7373d-124">您可以使用全息影像突出显示您的环境中的功能，或将其用作应用程序用户界面中的元素。</span><span class="sxs-lookup"><span data-stu-id="7373d-124">You can use holograms to highlight features in your environment or use them as elements in your app's user interface.</span></span>

![手动操作全息图](images/hologram-hands-940px.jpg)

### <a name="sound"></a><span data-ttu-id="7373d-126">声音</span><span class="sxs-lookup"><span data-stu-id="7373d-126">Sound</span></span>

<span data-ttu-id="7373d-127">全息影像还可以生成[声音](../design/spatial-sound.md)，这似乎来自你的环境中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="7373d-127">Holograms can also produce [sounds](../design/spatial-sound.md), which appear to come from a specific place in your environment.</span></span> <span data-ttu-id="7373d-128">在 HoloLens 上，声音来自两个位于你的耳上的扬声器。</span><span class="sxs-lookup"><span data-stu-id="7373d-128">On HoloLens, sound comes from two speakers that are located directly above your ears.</span></span> <span data-ttu-id="7373d-129">与全息显示器相同，扬声器是累加的，引入新声音，而不会阻止环境中的声音。</span><span class="sxs-lookup"><span data-stu-id="7373d-129">Same as the holographic displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="7373d-130">全息图可以放在世界上，也可以与你一起标记</span><span class="sxs-lookup"><span data-stu-id="7373d-130">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="7373d-131">当你有固定的 [空间来放置](../design/coordinate-systems.md) 全息图时，你可以在世界上准确地放置该位置。</span><span class="sxs-lookup"><span data-stu-id="7373d-131">When you have a fixed location for a hologram, you can [place](../design/coordinate-systems.md) it precisely at that point in the world.</span></span> <span data-ttu-id="7373d-132">在四处浏览时，全息图会显示在周围，就像物理对象一样。</span><span class="sxs-lookup"><span data-stu-id="7373d-132">As you walk around, the hologram appears stationary based on the world around you, just like a physical object.</span></span> <span data-ttu-id="7373d-133">如果使用 [空间锚点](../design/coordinate-systems.md#spatial-anchors) 固定对象，则系统甚至可以在以后回来时记住它的位置。</span><span class="sxs-lookup"><span data-stu-id="7373d-133">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin the object, the system can even remember where you left it when you come back later.</span></span>

![在零售空间中使用 Microsoft Dynamics 365 布局的两个男人](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="7373d-135">某些全息影像会按用户进行操作。</span><span class="sxs-lookup"><span data-stu-id="7373d-135">Some holograms follow the user instead.</span></span> <span data-ttu-id="7373d-136">它们将基于用户进行定位。</span><span class="sxs-lookup"><span data-stu-id="7373d-136">They position themselves based on the user.</span></span> <span data-ttu-id="7373d-137">您可以选择为您提供一个全息图，然后在到达另一个房间后将其放在墙壁上。</span><span class="sxs-lookup"><span data-stu-id="7373d-137">You can choose to bring a hologram with you, and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="7373d-138">**最佳做法**</span><span class="sxs-lookup"><span data-stu-id="7373d-138">**Best practices**</span></span>

* <span data-ttu-id="7373d-139">某些情况下，需要在整个体验中轻松发现和查看全息影像。</span><span class="sxs-lookup"><span data-stu-id="7373d-139">Some scenarios demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="7373d-140">此类定位有两个高级方法。</span><span class="sxs-lookup"><span data-stu-id="7373d-140">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="7373d-141">让我们将它们称为 " **显示锁定** " 和 " **正文锁定**"。</span><span class="sxs-lookup"><span data-stu-id="7373d-141">Let's call them **display-locked** and **body-locked**.</span></span>
   * <span data-ttu-id="7373d-142">**显示锁定** 的内容已锁定到显示设备。</span><span class="sxs-lookup"><span data-stu-id="7373d-142">**Display-locked** content is locked to the display device.</span></span> <span data-ttu-id="7373d-143">由于多种原因，这种类型的内容有点棘手，其中包括 "clingyness" 非自然的 ""，这使得许多用户感到沮丧并希望 "将其关闭"。</span><span class="sxs-lookup"><span data-stu-id="7373d-143">This type of content is tricky for several reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="7373d-144">一般而言，设计人员发现，更好的做法是避免显示锁定内容。</span><span class="sxs-lookup"><span data-stu-id="7373d-144">In general, designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="7373d-145">**正文锁定内容的** 包容性更多。</span><span class="sxs-lookup"><span data-stu-id="7373d-145">**Body-locked** content can be far more forgiving.</span></span> <span data-ttu-id="7373d-146">当您在三维空间中接入到用户的主体或注视着矢量时，会锁定正文。</span><span class="sxs-lookup"><span data-stu-id="7373d-146">Body-locking is when you tether a hologram to the user's body or gaze vector in 3D space.</span></span> <span data-ttu-id="7373d-147">许多经验都采用了一种正文锁定行为，其中全息图跟随用户的注视，这允许用户轮换其身体，而不会丢失全息影像。</span><span class="sxs-lookup"><span data-stu-id="7373d-147">Many experiences have adopted a body-locking behavior where the hologram follows the user's gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="7373d-148">合并延迟有助于使全息图移动更加自然。</span><span class="sxs-lookup"><span data-stu-id="7373d-148">Incorporating a delay helps the hologram movements to feel more natural.</span></span> <span data-ttu-id="7373d-149">例如，Windows 全息版 OS 的某些核心 UI 使用了一种外观上的外观锁定，用户将其看起来像是一种灵活的、弹性的延迟，同时用户会将其标头。</span><span class="sxs-lookup"><span data-stu-id="7373d-149">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="7373d-150">将全息图放置在舒适的观看距离上，通常会远离1-2 米。</span><span class="sxs-lookup"><span data-stu-id="7373d-150">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="7373d-151">如果元素必须在全息帧中连续，则允许元素偏移，或者考虑在用户更改其视图时将内容移至显示的一侧。</span><span class="sxs-lookup"><span data-stu-id="7373d-151">Allow elements to drift if they must be continually in the holographic frame, or consider moving your content to one side of the display when the user changes their point of view.</span></span> <span data-ttu-id="7373d-152">有关详细信息，请参阅 [billboarding and tag](../design/billboarding-and-tag-along.md) artilce。</span><span class="sxs-lookup"><span data-stu-id="7373d-152">For more information, see the [billboarding and tag-along](../design/billboarding-and-tag-along.md) artilce.</span></span>

<span data-ttu-id="7373d-153">**将全息影像置于最佳区域-介于 1.25 m 和 5 m 之间**</span><span class="sxs-lookup"><span data-stu-id="7373d-153">**Place holograms in the optimal zone - between 1.25 m and 5 m**</span></span>

<span data-ttu-id="7373d-154">双米是最佳观看距离。</span><span class="sxs-lookup"><span data-stu-id="7373d-154">Two meters is the most optimal viewing distance.</span></span> <span data-ttu-id="7373d-155">当你接近1米时，体验会开始下降。</span><span class="sxs-lookup"><span data-stu-id="7373d-155">The experience will start to degrade as you get closer than 1 meter.</span></span> <span data-ttu-id="7373d-156">在距离小于1米的位置上，定期移动的全息影像比静态全息影像更有可能出现问题。</span><span class="sxs-lookup"><span data-stu-id="7373d-156">At distances less than 1 meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="7373d-157">如果内容太近，请考虑适当地剪辑或淡化内容，因此你不会将用户剪到令人不愉快的观看体验。</span><span class="sxs-lookup"><span data-stu-id="7373d-157">Consider gracefully clipping or fading out your content when it gets too close, so you don't jar the user into an unpleasant viewing experience.</span></span>

![从用户放置全息影像的最佳距离。](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="7373d-159">全息图与您和您的世界交互</span><span class="sxs-lookup"><span data-stu-id="7373d-159">A hologram interacts with you and your world</span></span>

<span data-ttu-id="7373d-160">全息影像不只是关于光线和声音;它们也是您世界的一个活动部分。</span><span class="sxs-lookup"><span data-stu-id="7373d-160">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="7373d-161">用手看一个全息影像和手势，然后就可以开始使用全息图。</span><span class="sxs-lookup"><span data-stu-id="7373d-161">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="7373d-162">发出一个语音命令，然后再进行回复。</span><span class="sxs-lookup"><span data-stu-id="7373d-162">Give a voice command, and the hologram can reply.</span></span>

![一组政府实用工作人员组，使用 Microsoft HoloLens 2 在风场开发项目上协作](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="7373d-164">全息影像可以在其他地方实现不可能的个人交互。</span><span class="sxs-lookup"><span data-stu-id="7373d-164">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="7373d-165">因为 HoloLens 知道了它在世界中的位置，所以全息人物可以直接查看并与你进行对话。</span><span class="sxs-lookup"><span data-stu-id="7373d-165">Because the HoloLens knows where it is in the world, a holographic character can look at you directly in the eyes and start a conversation with you.</span></span>

<span data-ttu-id="7373d-166">全息图还可以与你的环境交互。</span><span class="sxs-lookup"><span data-stu-id="7373d-166">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="7373d-167">例如，您可以将一个全息弹跳球置于一个表上方。</span><span class="sxs-lookup"><span data-stu-id="7373d-167">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="7373d-168">然后，通过 [点击](../design/gaze-and-commit.md#composite-gestures)，观看球弹跳，并在其到达表时发出声音。</span><span class="sxs-lookup"><span data-stu-id="7373d-168">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce, and make sound as it hits the table.</span></span>

<span data-ttu-id="7373d-169">全息影像还可以由真实的对象封闭像素。</span><span class="sxs-lookup"><span data-stu-id="7373d-169">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="7373d-170">例如，全息人物可能会走出大门的门和背面。</span><span class="sxs-lookup"><span data-stu-id="7373d-170">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="7373d-171">**用于集成全息影像和现实世界的使用技巧**</span><span class="sxs-lookup"><span data-stu-id="7373d-171">**Tips for integrating holograms and the real world**</span></span>

* <span data-ttu-id="7373d-172">与 gravitational 规则相协调，可以更轻松地与和更可信相关。</span><span class="sxs-lookup"><span data-stu-id="7373d-172">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="7373d-173">例如：将一个全息狗置于 & 表上的花瓶，而不是让它们在空间中浮动。</span><span class="sxs-lookup"><span data-stu-id="7373d-173">For example: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="7373d-174">许多设计人员发现，他们可以通过在可信的表面上创建 "负阴影" 来集成更多的全息影像。</span><span class="sxs-lookup"><span data-stu-id="7373d-174">Many designers have found that they can integrate more believable holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="7373d-175">为此，可在两个全息图的地面上创建软光亮，然后从发光中减去 "阴影"。</span><span class="sxs-lookup"><span data-stu-id="7373d-175">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="7373d-176">软发光与现实世界中的灯光相集成。</span><span class="sxs-lookup"><span data-stu-id="7373d-176">The soft glow integrates with the light from the real world.</span></span> <span data-ttu-id="7373d-177">影子用于在环境中构建全息影像。</span><span class="sxs-lookup"><span data-stu-id="7373d-177">The shadow is used to ground the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a><span data-ttu-id="7373d-178">全息图</span><span class="sxs-lookup"><span data-stu-id="7373d-178">A hologram is what</span></span> <br><span data-ttu-id="7373d-179">你可以梦想</span><span class="sxs-lookup"><span data-stu-id="7373d-179">you can dream up</span></span><br>
        <span data-ttu-id="7373d-180">作为全息开发人员，您可以将您的创造性从2D 屏幕和世界各地突破起来。</span><span class="sxs-lookup"><span data-stu-id="7373d-180">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="7373d-181">*你* 将生成什么？</span><span class="sxs-lookup"><span data-stu-id="7373d-181">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="7373d-182">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="7373d-182">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="7373d-183">![客厅的全息虚世界](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="7373d-183">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="7373d-184">下一个发现检查点</span><span class="sxs-lookup"><span data-stu-id="7373d-184">Next Discovery Checkpoint</span></span>

<span data-ttu-id="7373d-185">你正处于 [发现旅程](get-started-with-mr.md) ，并探讨了混合现实的基本知识。</span><span class="sxs-lookup"><span data-stu-id="7373d-185">You're on the [discovery journey](get-started-with-mr.md) we've laid out, and exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="7373d-186">从这里，你可以进入下一基本主题：</span><span class="sxs-lookup"><span data-stu-id="7373d-186">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="7373d-187">扩展设计过程</span><span class="sxs-lookup"><span data-stu-id="7373d-187">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)