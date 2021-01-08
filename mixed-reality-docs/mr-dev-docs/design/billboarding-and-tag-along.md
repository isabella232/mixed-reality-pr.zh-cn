---
title: 公告和尾随
description: 了解如何在 billboarding 中使用对象，这种对象始终在混合现实应用程序中对用户进行操作。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，billboarding，标记和混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包
ms.openlocfilehash: 92caa1bcd325cefecc6d3820b819cecfce6fc09c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009607"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="26f1d-104">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="26f1d-104">Billboarding and tag-along</span></span>

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="26f1d-105">什么是 billboarding？</span><span class="sxs-lookup"><span data-stu-id="26f1d-105">What is billboarding?</span></span>

<span data-ttu-id="26f1d-106">Billboarding 是一种可应用于混合现实中的对象的行为概念。</span><span class="sxs-lookup"><span data-stu-id="26f1d-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="26f1d-107">具有 billboarding 的对象始终向用户提供正面的定向。</span><span class="sxs-lookup"><span data-stu-id="26f1d-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="26f1d-108">文本和菜单系统是常见的用例，在此类情况下，用户在用户的环境中放置的静态对象 (全局锁定的) 在用户四处移动时可能会被遮住或不可读。</span><span class="sxs-lookup"><span data-stu-id="26f1d-108">Text and menu systems are common use cases, where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable when users move around.</span></span>

<span data-ttu-id="26f1d-109">启用了 billboarding 的对象可以在用户的环境中自由旋转。</span><span class="sxs-lookup"><span data-stu-id="26f1d-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="26f1d-110">它们还可以根据设计注意事项限制为单个轴。</span><span class="sxs-lookup"><span data-stu-id="26f1d-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="26f1d-111">请记住，billboarded 对象在放置到其他对象时或在 HoloLens 中太接近扫描面时，可以将其夹扣或遮蔽。</span><span class="sxs-lookup"><span data-stu-id="26f1d-111">Keep in mind, billboarded objects can clip or occlude themselves when placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="26f1d-112">为避免出现这种情况，请考虑在为 billboarding 启用轴旋转时对象可能产生的总空间。</span><span class="sxs-lookup"><span data-stu-id="26f1d-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="26f1d-113">什么是标记？</span><span class="sxs-lookup"><span data-stu-id="26f1d-113">What is a tag-along?</span></span>

<span data-ttu-id="26f1d-114">标记-一起是可以添加到全息影像的行为概念。</span><span class="sxs-lookup"><span data-stu-id="26f1d-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="26f1d-115">标记靠后的对象试图停留在允许用户轻松交互的范围内。</span><span class="sxs-lookup"><span data-stu-id="26f1d-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="26f1d-116">![HoloLens 引脚面板是如何在标签上表现出的一个很好的示例](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="26f1d-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="26f1d-117">*HoloLens "开始" 菜单是一个更好的标记和行为示例*</span><span class="sxs-lookup"><span data-stu-id="26f1d-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="26f1d-118">带标签的对象具有参数，可对其行为方式进行微调。</span><span class="sxs-lookup"><span data-stu-id="26f1d-118">Tag-along objects have parameters, which can fine-tune the way they behave.</span></span> <span data-ttu-id="26f1d-119">当用户在其环境中移动时，内容可以在用户的视觉上或传出。</span><span class="sxs-lookup"><span data-stu-id="26f1d-119">Content can be in or out of the user’s line of sight while the user moves around their environment.</span></span> <span data-ttu-id="26f1d-120">随着您的移动，内容会通过向视图的边缘滑动来尝试停留在用户的绕中。</span><span class="sxs-lookup"><span data-stu-id="26f1d-120">As you move, the content attempts to stay within the user’s periphery by sliding towards the edge of the view.</span></span> <span data-ttu-id="26f1d-121">内容可能暂时不会显示，具体取决于用户的移动速度。</span><span class="sxs-lookup"><span data-stu-id="26f1d-121">The content might be temporarily out of view depending on how quickly the user is moving.</span></span> <span data-ttu-id="26f1d-122">当用户 gazes 沿标记的对象时，它会更全面地进入视图。</span><span class="sxs-lookup"><span data-stu-id="26f1d-122">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="26f1d-123">将内容视为始终 "一目了然"，这样用户就不会忘记内容的方向。</span><span class="sxs-lookup"><span data-stu-id="26f1d-123">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="26f1d-124">额外参数可以通过橡皮带来使标记沿着对象的外观附加到用户的头。</span><span class="sxs-lookup"><span data-stu-id="26f1d-124">Extra parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="26f1d-125">抑制加速或减速为对象提供权重，使其感觉更真实地出现。</span><span class="sxs-lookup"><span data-stu-id="26f1d-125">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="26f1d-126">此春季行为是一种 affordance，可帮助用户构建准确的心理模型，说明如何进行标记。</span><span class="sxs-lookup"><span data-stu-id="26f1d-126">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="26f1d-127">当用户在标记沿模式下具有对象时，音频有助于提供其他提示。</span><span class="sxs-lookup"><span data-stu-id="26f1d-127">Audio helps provide other cues for when users have objects in tag-along mode.</span></span> <span data-ttu-id="26f1d-128">音频应强化移动速度;迅速走下来应提供更为明显的声音效果，而在自然速度下，应具有最小或没有音频效果。</span><span class="sxs-lookup"><span data-stu-id="26f1d-128">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect, while walking at a natural speed should have minimal or no audio effects.</span></span>

<span data-ttu-id="26f1d-129">与真正的 head 锁定的内容一样，如果对象在用户的视图中变得很大或太过太多，则这些对象可能会 nauseating。</span><span class="sxs-lookup"><span data-stu-id="26f1d-129">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="26f1d-130">随着用户的浏览，快速停止，他们的感知告诉他们已停止。</span><span class="sxs-lookup"><span data-stu-id="26f1d-130">As a user looks around, then quickly stops, their senses tell them they've stopped.</span></span> <span data-ttu-id="26f1d-131">它们的平衡通知他们打印头已停止转动，其视觉障碍会看到世界停止车。</span><span class="sxs-lookup"><span data-stu-id="26f1d-131">Their balance informs them that their head has stopped turning and their vision sees the world stop turning.</span></span> <span data-ttu-id="26f1d-132">但是，如果在用户停止时仍继续进行标记，则可能会混淆其感知。</span><span class="sxs-lookup"><span data-stu-id="26f1d-132">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="26f1d-133">Billboarding 和标记 (混合现实工具包) 适用于 Unity</span><span class="sxs-lookup"><span data-stu-id="26f1d-133">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="26f1d-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 为 Billboarding 和标记的行为提供脚本。</span><span class="sxs-lookup"><span data-stu-id="26f1d-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="26f1d-135">将 Billboard.cs 脚本分配到任何对象，以添加 billboarding 行为，并使对象始终为你所需的外观。</span><span class="sxs-lookup"><span data-stu-id="26f1d-135">Assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="26f1d-136">若要添加标记和行为，请使用 RadialView.cs 脚本。</span><span class="sxs-lookup"><span data-stu-id="26f1d-136">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="26f1d-137">可以调整各种选项，如 lerping 时间、距离和角度。</span><span class="sxs-lookup"><span data-stu-id="26f1d-137">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="26f1d-138">MRTK-径向视图规划求解</span><span class="sxs-lookup"><span data-stu-id="26f1d-138">MRTK - Radial View Solver</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [<span data-ttu-id="26f1d-139">MRTK-布告栏脚本</span><span class="sxs-lookup"><span data-stu-id="26f1d-139">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="26f1d-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26f1d-140">See also</span></span>

* [<span data-ttu-id="26f1d-141">光标</span><span class="sxs-lookup"><span data-stu-id="26f1d-141">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="26f1d-142">手部射线</span><span class="sxs-lookup"><span data-stu-id="26f1d-142">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="26f1d-143">Button</span><span class="sxs-lookup"><span data-stu-id="26f1d-143">Button</span></span>](button.md)
* [<span data-ttu-id="26f1d-144">可交互对象</span><span class="sxs-lookup"><span data-stu-id="26f1d-144">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="26f1d-145">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="26f1d-145">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="26f1d-146">操作</span><span class="sxs-lookup"><span data-stu-id="26f1d-146">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="26f1d-147">手动菜单</span><span class="sxs-lookup"><span data-stu-id="26f1d-147">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="26f1d-148">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="26f1d-148">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="26f1d-149">对象集合</span><span class="sxs-lookup"><span data-stu-id="26f1d-149">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="26f1d-150">语音命令</span><span class="sxs-lookup"><span data-stu-id="26f1d-150">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="26f1d-151">键盘</span><span class="sxs-lookup"><span data-stu-id="26f1d-151">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="26f1d-152">工具提示</span><span class="sxs-lookup"><span data-stu-id="26f1d-152">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="26f1d-153">平板</span><span class="sxs-lookup"><span data-stu-id="26f1d-153">Slate</span></span>](slate.md)
* [<span data-ttu-id="26f1d-154">滑块</span><span class="sxs-lookup"><span data-stu-id="26f1d-154">Slider</span></span>](slider.md)
* [<span data-ttu-id="26f1d-155">着色器</span><span class="sxs-lookup"><span data-stu-id="26f1d-155">Shader</span></span>](shader.md)
* [<span data-ttu-id="26f1d-156">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="26f1d-156">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="26f1d-157">显示进度</span><span class="sxs-lookup"><span data-stu-id="26f1d-157">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="26f1d-158">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="26f1d-158">Surface magnetism</span></span>](surface-magnetism.md)
