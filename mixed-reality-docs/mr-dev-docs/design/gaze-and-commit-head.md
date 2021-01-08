---
title: 头部凝视和提交
description: 开始处理打印头和提交输入模型，包括目标大小、位置和稳定。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality，注视，注视目标，交互，设计，混合现实耳机，windows mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，目标，焦点，平滑
ms.openlocfilehash: 13a040a8309d084fcfdbfa91cbd9d63b595b004a
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009447"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="21270-104">头部凝视和提交</span><span class="sxs-lookup"><span data-stu-id="21270-104">Head-gaze and commit</span></span>

<span data-ttu-id="21270-105">"[注视](gaze-and-commit.md)" 和 "提交" 输入 _模型是一_ 种特殊情况，涉及到对象以用户头方向为目标。</span><span class="sxs-lookup"><span data-stu-id="21270-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with a users head direction.</span></span> <span data-ttu-id="21270-106">您可以使用辅助输入来操作目标，例如，手型手势和 "选择" 语音命令。</span><span class="sxs-lookup"><span data-stu-id="21270-106">You can act on the target with a secondary input, such as the hand gesture air tap or "Select" voice command.</span></span> 

## <a name="device-support"></a><span data-ttu-id="21270-107">设备支持</span><span class="sxs-lookup"><span data-stu-id="21270-107">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="21270-108"><strong>输入模型</strong></span><span class="sxs-lookup"><span data-stu-id="21270-108"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="21270-109"><a href="../hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="21270-109"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="21270-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="21270-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="21270-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="21270-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="21270-112">头部凝视和提交</span><span class="sxs-lookup"><span data-stu-id="21270-112">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="21270-113">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="21270-113">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="21270-114">✔️推荐（第三个选择 - <a href="interaction-fundamentals.md">查看其他选项</a>）</span><span class="sxs-lookup"><span data-stu-id="21270-114">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="21270-115">➕ 备用选项</span><span class="sxs-lookup"><span data-stu-id="21270-115">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="21270-116">目标大小调整和反馈</span><span class="sxs-lookup"><span data-stu-id="21270-116">Target sizing and feedback</span></span>

<span data-ttu-id="21270-117">一直看着头注视向量，可用于精细定位，但通常最适用于毛目标-获取更大的目标。</span><span class="sxs-lookup"><span data-stu-id="21270-117">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring larger targets.</span></span> <span data-ttu-id="21270-118">1度到1.5 度的最小目标大小允许成功的用户操作在大多数情况下，尽管目标为3度，但通常允许更高的速度。</span><span class="sxs-lookup"><span data-stu-id="21270-118">Minimum target sizes of 1 degree to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="21270-119">用户的目标大小实际上是一个二维区域，即使对于3D 元素也是如此。</span><span class="sxs-lookup"><span data-stu-id="21270-119">The size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="21270-120">提供一些突出的提示，指出某个元素处于 "活动" 状态， (用户为其设定目标) 很有用。</span><span class="sxs-lookup"><span data-stu-id="21270-120">Providing some salient cue that an element is "active" (that the user is targeting it) is helpful.</span></span> <span data-ttu-id="21270-121">这可能包括处理方式（如可见的 "悬停" 效果、音频突出显示或单击），或通过元素清晰显示光标。</span><span class="sxs-lookup"><span data-stu-id="21270-121">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="21270-122">![2 米远处的最佳目标大小](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="21270-122">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="21270-123">*最佳目标大小，以2米到远处*</span><span class="sxs-lookup"><span data-stu-id="21270-123">*Optimal target size at 2-meter distance*</span></span>

<br>

<span data-ttu-id="21270-124">![突出显示凝视目标对象的示例](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="21270-124">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="21270-125">*突出显示凝视目标对象的示例*</span><span class="sxs-lookup"><span data-stu-id="21270-125">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="21270-126">目标位置</span><span class="sxs-lookup"><span data-stu-id="21270-126">Target placement</span></span>

<span data-ttu-id="21270-127">用户经常无法在其视图字段中找到太高或较低的 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="21270-127">Users often fail to find UI elements located either too high or low in their field of view.</span></span> <span data-ttu-id="21270-128">其中的大多数关注点在其主要关注点的周围，这大致在目视。</span><span class="sxs-lookup"><span data-stu-id="21270-128">Most of their attention ends up on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="21270-129">将大多数目标放在视平线位置附近的某个合理范围内可能有所帮助。</span><span class="sxs-lookup"><span data-stu-id="21270-129">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="21270-130">在任何时候，用户都可以专注于一个相对较小的视觉区域 (在视觉上，) 将视觉对象组合在一起，将 UI 元素分组到它们在概念上的相关程度，可以在用户将其看起来通过某个区域时，使用从项目到项目的 attentional。</span><span class="sxs-lookup"><span data-stu-id="21270-130">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree they're related conceptually can use attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="21270-131">在设计 UI 时，请注意 HoloLens 和沉浸式头戴显示设备之间视野的巨大差异。</span><span class="sxs-lookup"><span data-stu-id="21270-131">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="21270-132">![在 Galaxy Explorer 中使用分组 UI 元素简化凝视目标设定的示例](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="21270-132">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="21270-133">*在 Galaxy Explorer 中使用分组 UI 元素简化凝视目标设定的示例*</span><span class="sxs-lookup"><span data-stu-id="21270-133">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="21270-134">改进目标设定行为</span><span class="sxs-lookup"><span data-stu-id="21270-134">Improving targeting behaviors</span></span>

<span data-ttu-id="21270-135">如果用户意向面向某个对象，则可以确定或将其视为非常近似，这有助于接受接近的未命中交互尝试，就好像它们的目标是正确的一样。</span><span class="sxs-lookup"><span data-stu-id="21270-135">If user intent to target something can be determined or closely approximated, it can be helpful to accept near miss interaction attempts as though they were targeted correctly.</span></span> <span data-ttu-id="21270-136">下面是一些可在混合现实体验中结合使用的成功方法：</span><span class="sxs-lookup"><span data-stu-id="21270-136">Here's a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="21270-137">头部凝视防抖动（“重力井”）</span><span class="sxs-lookup"><span data-stu-id="21270-137">Head-gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="21270-138">这应该是最多或全部开启。</span><span class="sxs-lookup"><span data-stu-id="21270-138">This should be turned on most or all of the time.</span></span> <span data-ttu-id="21270-139">此方法可删除用户可能出于移动原因而移动的自然头和抖动。</span><span class="sxs-lookup"><span data-stu-id="21270-139">This technique removes the natural head and neck jitters that users might have as well movement because of looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="21270-140">最邻近链接算法</span><span class="sxs-lookup"><span data-stu-id="21270-140">Closest link algorithms</span></span>

<span data-ttu-id="21270-141">这些算法最适用于具有稀疏交互式内容的区域。</span><span class="sxs-lookup"><span data-stu-id="21270-141">These algorithms work best in areas with sparse interactive content.</span></span> <span data-ttu-id="21270-142">如果很有可能确定用户尝试与之交互的概率很高，则可以通过假定某些级别来补充其目标功能。</span><span class="sxs-lookup"><span data-stu-id="21270-142">If there's a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="21270-143">Backdating 和 postdating 操作</span><span class="sxs-lookup"><span data-stu-id="21270-143">Backdating and postdating actions</span></span>

<span data-ttu-id="21270-144">此机制非常适合需要快速完成的任务。</span><span class="sxs-lookup"><span data-stu-id="21270-144">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="21270-145">当用户在一系列目标和激活设法使其的同时进行时，可以采用某种目的。</span><span class="sxs-lookup"><span data-stu-id="21270-145">When a user is moving through a series of targeting and activation maneuvers at speed, it's useful to assume some intent.</span></span> <span data-ttu-id="21270-146">这对于在早期测试) 生效之前/之后（ (50 ms 之前/之后），允许缺少的步骤对用户具有特别关注的目标有很大的作用。</span><span class="sxs-lookup"><span data-stu-id="21270-146">It's also useful to allow missed steps to act on targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="21270-147">平滑处理</span><span class="sxs-lookup"><span data-stu-id="21270-147">Smoothing</span></span>

<span data-ttu-id="21270-148">这种机制对于路径移动非常有用，因为自然的移动特征会降低轻微的抖动和 wobbles。</span><span class="sxs-lookup"><span data-stu-id="21270-148">This mechanism is useful for pathing movements, reducing the slight jitter and wobbles because of natural head movement characteristics.</span></span> <span data-ttu-id="21270-149">对路径运动进行平滑处理时，按移动的大小和距离而不是一段时间来平滑。</span><span class="sxs-lookup"><span data-stu-id="21270-149">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="21270-150">磁吸</span><span class="sxs-lookup"><span data-stu-id="21270-150">Magnetism</span></span>

<span data-ttu-id="21270-151">此机制可被视为最近的链接算法的更通用版本，即根据目标绘制游标，或者只是直观或不增加 hitboxes，因为用户通过使用一些交互式布局了解来更好地利用用户意图来实现目标。</span><span class="sxs-lookup"><span data-stu-id="21270-151">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="21270-152">这对于小型目标可能非常强大。</span><span class="sxs-lookup"><span data-stu-id="21270-152">This can be powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="21270-153">焦点粘性</span><span class="sxs-lookup"><span data-stu-id="21270-153">Focus stickiness</span></span>

<span data-ttu-id="21270-154">确定要为其提供哪些邻近的交互式元素时，焦点到，焦点将为当前聚焦的元素提供偏移。</span><span class="sxs-lookup"><span data-stu-id="21270-154">When determining which nearby interactive elements to give,  focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="21270-155">当在两个元素之间的中间点处浮动时，这有助于减少不稳定的焦点切换行为。</span><span class="sxs-lookup"><span data-stu-id="21270-155">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="21270-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="21270-156">See also</span></span>

* [<span data-ttu-id="21270-157">基于眼睛的交互</span><span class="sxs-lookup"><span data-stu-id="21270-157">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="21270-158">凝视和停留</span><span class="sxs-lookup"><span data-stu-id="21270-158">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="21270-159">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="21270-159">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="21270-160">手 - 手势</span><span class="sxs-lookup"><span data-stu-id="21270-160">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="21270-161">手 - 指向并提交</span><span class="sxs-lookup"><span data-stu-id="21270-161">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="21270-162">本能交互</span><span class="sxs-lookup"><span data-stu-id="21270-162">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="21270-163">语音输入</span><span class="sxs-lookup"><span data-stu-id="21270-163">Voice input</span></span>](voice-input.md)



