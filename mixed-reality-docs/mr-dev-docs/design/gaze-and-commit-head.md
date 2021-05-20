---
title: 头部凝视和提交
description: 开始处理打印头和提交输入模型，包括目标大小、位置和稳定。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality，注视，注视目标，交互，设计，混合现实耳机，windows mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，目标，焦点，平滑
ms.openlocfilehash: 74f963a6b450d1fb7f1302886a01c12cf79ce28a
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196512"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="7bdd6-104">头部凝视和提交</span><span class="sxs-lookup"><span data-stu-id="7bdd6-104">Head-gaze and commit</span></span>

<span data-ttu-id="7bdd6-105">"[注视](gaze-and-commit.md)" 和 "提交" 输入 _模型是一_ 种特殊情况，涉及到对象以用户头方向为目标。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with a users head direction.</span></span> <span data-ttu-id="7bdd6-106">您可以使用辅助输入来操作目标，例如，手型手势和 "选择" 语音命令。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-106">You can act on the target with a secondary input, such as the hand gesture air tap or "Select" voice command.</span></span> 

## <a name="device-support"></a><span data-ttu-id="7bdd6-107">设备支持</span><span class="sxs-lookup"><span data-stu-id="7bdd6-107">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7bdd6-108"><strong>输入模型</strong></span><span class="sxs-lookup"><span data-stu-id="7bdd6-108"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="7bdd6-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="7bdd6-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="7bdd6-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="7bdd6-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="7bdd6-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="7bdd6-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7bdd6-112">头部凝视和提交</span><span class="sxs-lookup"><span data-stu-id="7bdd6-112">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="7bdd6-113">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="7bdd6-113">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="7bdd6-114">✔️推荐（第三个选择 - <a href="interaction-fundamentals.md">查看其他选项</a>）</span><span class="sxs-lookup"><span data-stu-id="7bdd6-114">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="7bdd6-115">➕ 备用选项</span><span class="sxs-lookup"><span data-stu-id="7bdd6-115">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="head-and-eye-tracking-design-concepts-demo"></a><span data-ttu-id="7bdd6-116">标题和眼睛跟踪设计概念演示</span><span class="sxs-lookup"><span data-stu-id="7bdd6-116">Head and eye tracking design concepts demo</span></span>

<span data-ttu-id="7bdd6-117">若要查看标题和目视跟踪的设计概念，请参阅下面的 **设计全息影像-打印头跟踪和眼睛跟踪** 视频演示。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-117">If you'd like to see Head and Eye Tracking design concepts in action, check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below.</span></span> <span data-ttu-id="7bdd6-118">完成后，请继续详细了解特定主题。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-118">When you've finished, continue on for a more detailed dive into specific topics.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="7bdd6-119">*此视频取自 "设计全息影像" HoloLens 2 应用。下载并在 [此处](https://aka.ms/dhapp)享受完全体验。*</span><span class="sxs-lookup"><span data-stu-id="7bdd6-119">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="7bdd6-120">目标大小调整和反馈</span><span class="sxs-lookup"><span data-stu-id="7bdd6-120">Target sizing and feedback</span></span>

<span data-ttu-id="7bdd6-121">一直看着头注视向量，可用于精细定位，但通常最适用于毛目标-获取更大的目标。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-121">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring larger targets.</span></span> <span data-ttu-id="7bdd6-122">1度到1.5 度的最小目标大小允许成功的用户操作在大多数情况下，尽管目标为3度，但通常允许更高的速度。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-122">Minimum target sizes of 1 degree to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="7bdd6-123">用户的目标大小实际上是一个二维区域，即使对于3D 元素也是如此。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-123">The size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="7bdd6-124">提供一些突出的提示，指出某个元素处于 "活动" 状态， (用户为其设定目标) 很有用。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-124">Providing some salient cue that an element is "active" (that the user is targeting it) is helpful.</span></span> <span data-ttu-id="7bdd6-125">这可能包括处理方式（如可见的 "悬停" 效果、音频突出显示或单击），或通过元素清晰显示光标。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-125">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="7bdd6-126">![2 米远处的最佳目标大小](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7bdd6-126">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="7bdd6-127">*最佳目标大小，以2米到远处*</span><span class="sxs-lookup"><span data-stu-id="7bdd6-127">*Optimal target size at 2-meter distance*</span></span>

<br>

<span data-ttu-id="7bdd6-128">![突出显示凝视目标对象的示例](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7bdd6-128">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="7bdd6-129">*突出显示凝视目标对象的示例*</span><span class="sxs-lookup"><span data-stu-id="7bdd6-129">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="7bdd6-130">目标位置</span><span class="sxs-lookup"><span data-stu-id="7bdd6-130">Target placement</span></span>

<span data-ttu-id="7bdd6-131">用户经常无法在其视图字段中找到太高或较低的 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-131">Users often fail to find UI elements located either too high or low in their field of view.</span></span> <span data-ttu-id="7bdd6-132">其中的大多数关注点在其主要关注点的周围，这大致在目视。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-132">Most of their attention ends up on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="7bdd6-133">将大多数目标放在视平线位置附近的某个合理范围内可能有所帮助。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-133">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="7bdd6-134">考虑到用户往往随时专注于相对较小的可视区域 (视觉的注意圆环大约是 10 度) ，在概念上将 UI 元素分组到相关程度后，当用户将视线移到某个区域时，可以使用从项到项的注意链接行为。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-134">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree they're related conceptually can use attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="7bdd6-135">在设计 UI 时，请注意 HoloLens 和沉浸式头戴显示设备之间视野的巨大差异。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-135">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="7bdd6-136">![在 Galaxy Explorer 中使用分组 UI 元素简化凝视目标设定的示例](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="7bdd6-136">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="7bdd6-137&quot;>*在 Galaxy Explorer 中使用分组 UI 元素简化凝视目标设定的示例*</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;7bdd6-137&quot;>*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name=&quot;improving-targeting-behaviors&quot;></a><span data-ttu-id=&quot;7bdd6-138&quot;>改进目标设定行为</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;7bdd6-138&quot;>Improving targeting behaviors</span></span>

<span data-ttu-id=&quot;7bdd6-139&quot;>如果可以确定或近似地确定用户目标目标，则接受近乎错过的交互尝试会很有帮助，就像它们的目标正确一样。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;7bdd6-139&quot;>If user intent to target something can be determined or closely approximated, it can be helpful to accept near miss interaction attempts as though they were targeted correctly.</span></span> <span data-ttu-id=&quot;7bdd6-140&quot;>下面是一些可以合并到混合现实体验中的成功方法：</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;7bdd6-140&quot;>Here's a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name=&quot;head-gaze-stabilization-gravity-wells&quot;></a><span data-ttu-id=&quot;7bdd6-141&quot;>头部凝视防抖动（“重力井”）</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;7bdd6-141&quot;>Head-gaze stabilization (&quot;gravity wells")</span></span>

<span data-ttu-id="7bdd6-142">这应该会在大多数或所有时间打开。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-142">This should be turned on most or all of the time.</span></span> <span data-ttu-id="7bdd6-143">此方法可消除用户可能由于查找和说话行为而移动的自然头部和头部抖动。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-143">This technique removes the natural head and neck jitters that users might have as well movement because of looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="7bdd6-144">最邻近链接算法</span><span class="sxs-lookup"><span data-stu-id="7bdd6-144">Closest link algorithms</span></span>

<span data-ttu-id="7bdd6-145">这些算法最适合具有稀疏交互式内容的区域。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-145">These algorithms work best in areas with sparse interactive content.</span></span> <span data-ttu-id="7bdd6-146">如果确定用户尝试与之交互的可能性很高，则可以通过假设一定的意向级别来补充其目标能力。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-146">If there's a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="7bdd6-147">备份和发布操作</span><span class="sxs-lookup"><span data-stu-id="7bdd6-147">Backdating and postdating actions</span></span>

<span data-ttu-id="7bdd6-148">此机制非常适合需要快速完成的任务。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-148">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="7bdd6-149">当用户快速完成一系列目标定位和激活操作时，假设一些意向会很有用。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-149">When a user is moving through a series of targeting and activation maneuvers at speed, it's useful to assume some intent.</span></span> <span data-ttu-id="7bdd6-150">此外，允许遗漏的步骤针对用户在点击之前或经过 (50 毫秒之前或之后稍稍聚焦的目标（在 50 毫秒之前/之后）有效，这一点也很有用) 。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-150">It's also useful to allow missed steps to act on targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="7bdd6-151">平滑处理</span><span class="sxs-lookup"><span data-stu-id="7bdd6-151">Smoothing</span></span>

<span data-ttu-id="7bdd6-152">此机制可用于路径移动，减少由于自然头部移动特征而出现轻微抖动和抖动。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-152">This mechanism is useful for pathing movements, reducing the slight jitter and wobbles because of natural head movement characteristics.</span></span> <span data-ttu-id="7bdd6-153">对路径运动进行平滑处理时，按运动的大小和距离（而不是一段时间）平滑。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-153">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="7bdd6-154">磁吸</span><span class="sxs-lookup"><span data-stu-id="7bdd6-154">Magnetism</span></span>

<span data-ttu-id="7bdd6-155">此机制可视为更常规的最近链接算法版本-将光标绘制到目标，或只是增加命中框（不管是否可见）。因为用户通过使用交互布局的一些知识来更好地接近用户意向来接近可能的目标。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-155">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="7bdd6-156">对于小型目标，这非常强大。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-156">This can be powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="7bdd6-157">焦点粘性</span><span class="sxs-lookup"><span data-stu-id="7bdd6-157">Focus stickiness</span></span>

<span data-ttu-id="7bdd6-158">确定要为其提供哪些邻近的交互式元素时，焦点到，焦点将为当前聚焦的元素提供偏移。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-158">When determining which nearby interactive elements to give,  focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="7bdd6-159">当在两个元素之间的中间点处浮动时，这有助于减少不稳定的焦点切换行为。</span><span class="sxs-lookup"><span data-stu-id="7bdd6-159">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bdd6-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7bdd6-160">See also</span></span>

* [<span data-ttu-id="7bdd6-161">基于眼睛的交互</span><span class="sxs-lookup"><span data-stu-id="7bdd6-161">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="7bdd6-162">凝视和停留</span><span class="sxs-lookup"><span data-stu-id="7bdd6-162">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="7bdd6-163">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="7bdd6-163">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="7bdd6-164">手 - 手势</span><span class="sxs-lookup"><span data-stu-id="7bdd6-164">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="7bdd6-165">手 - 指向并提交</span><span class="sxs-lookup"><span data-stu-id="7bdd6-165">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="7bdd6-166">本能交互</span><span class="sxs-lookup"><span data-stu-id="7bdd6-166">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="7bdd6-167">语音输入</span><span class="sxs-lookup"><span data-stu-id="7bdd6-167">Voice input</span></span>](voice-input.md)