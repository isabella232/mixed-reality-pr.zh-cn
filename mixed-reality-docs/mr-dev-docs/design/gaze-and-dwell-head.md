---
title: 头部凝视和停留
description: 开始大致了解头盔和停留输入模型，包括常见方案和设计原则。
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Mixed Reality，注视，停留，交互，设计，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，ux，指导原则，列表视图
ms.openlocfilehash: 2bfd984a466c1ccd3913e889ca57663800f46380
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007077"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="cdbce-104">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="cdbce-104">Head-gaze and dwell</span></span>

<span data-ttu-id="cdbce-105">手拿工具和零件，手势可能是没有意义或无法实现。</span><span class="sxs-lookup"><span data-stu-id="cdbce-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="cdbce-106">语音命令（例如手势）在某些情况下可能不可靠，例如在过度嘈杂的条件下。</span><span class="sxs-lookup"><span data-stu-id="cdbce-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="cdbce-107">此外，使用语音控制计算机并不是普遍常见的，但正日益盛行！</span><span class="sxs-lookup"><span data-stu-id="cdbce-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="cdbce-108">头部凝视和停留提供最熟悉且易于掌握的机制，可在 HoloLens 上实现抬头操作和解放双手的操作。</span><span class="sxs-lookup"><span data-stu-id="cdbce-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="cdbce-109">此外，头部凝视和停留 100% 可靠，与操作环境中不受噪声干扰和静音约束。</span><span class="sxs-lookup"><span data-stu-id="cdbce-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="cdbce-110">方案</span><span class="sxs-lookup"><span data-stu-id="cdbce-110">Scenarios</span></span>

<span data-ttu-id="cdbce-111">在人的手忙于处理其他任务的情况下，打印头和停留非常有用。</span><span class="sxs-lookup"><span data-stu-id="cdbce-111">Head-gaze and dwell is great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="cdbce-112">当语音不是100% 可靠或由于环境或社交限制而可用时，此功能也很有用。</span><span class="sxs-lookup"><span data-stu-id="cdbce-112">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span> <span data-ttu-id="cdbce-113">一个很好的例子是穿戴 HoloLens 的人在修理汽车发动机时获取参考信息。</span><span class="sxs-lookup"><span data-stu-id="cdbce-113">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="cdbce-114">倚靠在发动机舱内时，他们的手拿着工具或支撑着身体。</span><span class="sxs-lookup"><span data-stu-id="cdbce-114">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="cdbce-115">车库空间很大，工具不断敲打声和嘈杂声，难以使用语音命令。</span><span class="sxs-lookup"><span data-stu-id="cdbce-115">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="cdbce-116">通过打印头和停留，使用 HoloLens 的人员可以放心地浏览其参考材料，而不会中断工作流。</span><span class="sxs-lookup"><span data-stu-id="cdbce-116">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="cdbce-117">设备支持</span><span class="sxs-lookup"><span data-stu-id="cdbce-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="cdbce-118"><strong>输入模型</strong></span><span class="sxs-lookup"><span data-stu-id="cdbce-118"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="cdbce-119"><a href="../hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="cdbce-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="cdbce-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="cdbce-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="cdbce-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="cdbce-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="cdbce-122">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="cdbce-122">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="cdbce-123">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="cdbce-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="cdbce-124">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="cdbce-124">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="cdbce-125">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="cdbce-125">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="cdbce-126">设计原理</span><span class="sxs-lookup"><span data-stu-id="cdbce-126">Design principles</span></span>

<span data-ttu-id="cdbce-127">**避免“将凝视作为一种武器”**</span><span class="sxs-lookup"><span data-stu-id="cdbce-127">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="cdbce-128">头部凝视和停留需要直观的视觉反馈，但反馈过多会令人焦虑。</span><span class="sxs-lookup"><span data-stu-id="cdbce-128">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="cdbce-129">反馈应该有助于用户了解目标是什么，但不能根据自己的意图对其进行自动操作。</span><span class="sxs-lookup"><span data-stu-id="cdbce-129">The feedback should help a user know what they're targeting, but not autoselect it against their intent.</span></span> <span data-ttu-id="cdbce-130">在读取文本、图标和标签时，您需要为用户提供在选择之前吸收信息的时间。</span><span class="sxs-lookup"><span data-stu-id="cdbce-130">When reading text, icons, and labels, you need to provide users time to absorb the information before selecting.</span></span>
    
<span data-ttu-id="cdbce-131">**寻求适宜速度**</span><span class="sxs-lookup"><span data-stu-id="cdbce-131">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="cdbce-132">停留交互根据对导航的影响而使用不同的计时器 - 更频繁使用的功能通常将受益于更快的填充时间，而更具重要性的功能可能受益于更长的填充时间。</span><span class="sxs-lookup"><span data-stu-id="cdbce-132">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="cdbce-133">当使用填充效果来显示这些计时器时，填充颜色的动画曲线可对感知快速填充时间产生正面影响。</span><span class="sxs-lookup"><span data-stu-id="cdbce-133">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="cdbce-134">应进行仔细考虑，使用户能够基于快速/中速/慢速填充速度覆盖来做出决策。</span><span class="sxs-lookup"><span data-stu-id="cdbce-134">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="cdbce-135">**对摇摆不定效应说不**</span><span class="sxs-lookup"><span data-stu-id="cdbce-135">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="cdbce-136">后端效果是一种令人不安的头运动模式，当内容放置和打印头/停留控件强制用户重复查找和关闭时，就会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="cdbce-136">The yo-yo effect is an uncomfortable head movement pattern that happens when the content placement and head-gaze/dwell controls forces people to look up and down repeatedly.</span></span> <span data-ttu-id="cdbce-137">例如，使用底部的 "头盔" 和 "停留" 按钮的列表导航到 "停留" 循环，查找结果，查看 "停留" 等。</span><span class="sxs-lookup"><span data-stu-id="cdbce-137">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, and so on.</span></span> <span data-ttu-id="cdbce-138">生成的模式不舒服，因此建议将导航控件置于需要更少恢复的集中位置。</span><span class="sxs-lookup"><span data-stu-id="cdbce-138">The resulting pattern is uncomfortable, so we recommend placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="cdbce-139">根据其效果，放置停留按钮非常重要。</span><span class="sxs-lookup"><span data-stu-id="cdbce-139">Placement of dwell buttons based on their effects becomes important for comfort.</span></span>
<span data-ttu-id="cdbce-140">s</span><span class="sxs-lookup"><span data-stu-id="cdbce-140">s</span></span>
<br>

---

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="cdbce-141">UX 指南和最佳做法</span><span class="sxs-lookup"><span data-stu-id="cdbce-141">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="cdbce-142">目标大小</span><span class="sxs-lookup"><span data-stu-id="cdbce-142">Target sizes</span></span>

<span data-ttu-id="cdbce-143">若要轻松访问，打印头和停留目标必须足够大，以便能够完美地查看，并在指定时间的目标位置上保持一头稳定。</span><span class="sxs-lookup"><span data-stu-id="cdbce-143">To be easily accessible, head-gaze and dwell targets need to be large enough to look at comfortably, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="cdbce-144">建议最小目标大小为2度，以获得最舒适的体验。</span><span class="sxs-lookup"><span data-stu-id="cdbce-144">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="cdbce-145">视觉反馈</span><span class="sxs-lookup"><span data-stu-id="cdbce-145">Visual feedback</span></span>

<span data-ttu-id="cdbce-146">当使用径向填充来表示停留计时器时，请从按钮中心开始。</span><span class="sxs-lookup"><span data-stu-id="cdbce-146">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="cdbce-147">与在不同按钮上均采用不同方向相比，一致的响应可减少混淆。</span><span class="sxs-lookup"><span data-stu-id="cdbce-147">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="cdbce-148">此规则可以中断，但对于方向交互 (例如，向下导航/向下/向左/向右) 。</span><span class="sxs-lookup"><span data-stu-id="cdbce-148">This rule can be broken though for directional interactions (for example, nav up/down/left/right, and so on).</span></span> <span data-ttu-id="cdbce-149">例如，在 Microsoft Dynamics 365 指南中左右两侧填充“下一步”/“后退”时例外。</span><span class="sxs-lookup"><span data-stu-id="cdbce-149">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="cdbce-150">对于诸如关闭按钮之类的方案，请考虑从外部反色反色。</span><span class="sxs-lookup"><span data-stu-id="cdbce-150">Consider inverting radial fill from outside, for scenarios like toggling off a button.</span></span> <span data-ttu-id="cdbce-151">按下按钮的反向效果是一种出色的视觉模式。</span><span class="sxs-lookup"><span data-stu-id="cdbce-151">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="cdbce-152">渐进式披露</span><span class="sxs-lookup"><span data-stu-id="cdbce-152">Progressive disclosure</span></span>

<span data-ttu-id="cdbce-153">渐进式披露是指只显示与交互的每个阶段相关的详细信息。</span><span class="sxs-lookup"><span data-stu-id="cdbce-153">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="cdbce-154">对于停留，这意味着停留目标显示在突出显示 (例如，) 的列表控件中。</span><span class="sxs-lookup"><span data-stu-id="cdbce-154">For dwell, that means the dwell target is revealed on highlight (for example, in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="cdbce-155">过大的目标</span><span class="sxs-lookup"><span data-stu-id="cdbce-155">Oversized targets</span></span>

<span data-ttu-id="cdbce-156">停留区域可以比非活动图标大，以便于使用，例如 Microsoft Dynamics 365 指南中的“后退”按钮。</span><span class="sxs-lookup"><span data-stu-id="cdbce-156">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="cdbce-157">通过延迟反馈防止闪烁</span><span class="sxs-lookup"><span data-stu-id="cdbce-157">Prevent flickering with delayed feedback</span></span>

<span data-ttu-id="cdbce-158">在开始视觉反馈之前使用短暂的延迟，以避免当有人经过停留目标时闪烁。</span><span class="sxs-lookup"><span data-stu-id="cdbce-158">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="cdbce-159">对于按钮经常交互的按钮，请将延迟缩短，使应用程序感觉被动。</span><span class="sxs-lookup"><span data-stu-id="cdbce-159">For buttons interacted with frequently, keep the delay short so the application feels reactive.</span></span>
* <span data-ttu-id="cdbce-160">对于不常交互的按钮，更长的延迟可能适用于避免出现 twitchy 的界面。</span><span class="sxs-lookup"><span data-stu-id="cdbce-160">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>

<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="cdbce-161">UI 模式</span><span class="sxs-lookup"><span data-stu-id="cdbce-161">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="cdbce-162">高频率按钮</span><span class="sxs-lookup"><span data-stu-id="cdbce-162">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="cdbce-163">高频率按钮是通常在整个应用程序中使用的按钮。</span><span class="sxs-lookup"><span data-stu-id="cdbce-163">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="cdbce-164">其中一个很好的例子是 Microsoft Dynamics 365 指南中的“下一步”和“后退”按钮。</span><span class="sxs-lookup"><span data-stu-id="cdbce-164">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="cdbce-165">**建议**</span><span class="sxs-lookup"><span data-stu-id="cdbce-165">**Recommendations**</span></span><br>
  * <span data-ttu-id="cdbce-166">高频率按钮应该很大，更容易碰到打印头</span><span class="sxs-lookup"><span data-stu-id="cdbce-166">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="cdbce-167">保持近眼睛，以避免人体工学。</span><span class="sxs-lookup"><span data-stu-id="cdbce-167">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="cdbce-168">*图像： Microsoft Dynamics 365 "下一步" 按钮*</span><span class="sxs-lookup"><span data-stu-id="cdbce-168">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 "下一步" 按钮](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="cdbce-170">低频率按钮</span><span class="sxs-lookup"><span data-stu-id="cdbce-170">Low frequency buttons</span></span>

<span data-ttu-id="cdbce-171">低频率按钮是指在整个应用程序中不会定期交互的按钮。</span><span class="sxs-lookup"><span data-stu-id="cdbce-171">Low frequency buttons are buttons that aren't interacted with as regularly throughout the application.</span></span> <span data-ttu-id="cdbce-172">一个很好的例子是用于访问设置菜单的按钮，或用于清除所有工作的按钮。</span><span class="sxs-lookup"><span data-stu-id="cdbce-172">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="cdbce-173">尽量使这些按钮远离频繁进行头部凝视的路径，以避免意外激活。</span><span class="sxs-lookup"><span data-stu-id="cdbce-173">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="cdbce-174">确认</span><span class="sxs-lookup"><span data-stu-id="cdbce-174">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="cdbce-175">当某个操作有重大影响（如收费、删除工作或启动较长的过程）时，确认某个人要选择一个按钮很有用。</span><span class="sxs-lookup"><span data-stu-id="cdbce-175">When an action has significant impact, like charging money, deleting work, or starting a long process, it's useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="cdbce-176">**建议**</span><span class="sxs-lookup"><span data-stu-id="cdbce-176">**Recommendations**</span></span><br>
  * <span data-ttu-id="cdbce-177">在主按钮上突出显示选择内容。</span><span class="sxs-lookup"><span data-stu-id="cdbce-177">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="cdbce-178">在选择内容突出显示的同时显示停留目标。</span><span class="sxs-lookup"><span data-stu-id="cdbce-178">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="cdbce-179">对于辅助按钮，在头部凝视上显示停留目标。</span><span class="sxs-lookup"><span data-stu-id="cdbce-179">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="cdbce-180">*映像： Microsoft Dynamics 365 指南确认对话框*</span><span class="sxs-lookup"><span data-stu-id="cdbce-180">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南确认对话框](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="cdbce-182">切换按钮</span><span class="sxs-lookup"><span data-stu-id="cdbce-182">Toggle buttons</span></span>

<span data-ttu-id="cdbce-183">切换按钮需要一些细微的逻辑才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="cdbce-183">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="cdbce-184">当某个人 dwells 切换按钮并激活它时，他们需要退出按钮，然后返回以重新启动停留逻辑。</span><span class="sxs-lookup"><span data-stu-id="cdbce-184">When a person dwells on a toggle button and activates it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="cdbce-185">重要的是，togglable 按钮具有清晰的活动和非活动状态。</span><span class="sxs-lookup"><span data-stu-id="cdbce-185">It's important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="cdbce-186">列表视图</span><span class="sxs-lookup"><span data-stu-id="cdbce-186">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="cdbce-187">列表视图为打印头和停留输入提供了一个特定的挑战。</span><span class="sxs-lookup"><span data-stu-id="cdbce-187">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="cdbce-188">用户可以扫描内容，而无需围绕停留目标 tiptoe。</span><span class="sxs-lookup"><span data-stu-id="cdbce-188">People can scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="cdbce-189">**建议**</span><span class="sxs-lookup"><span data-stu-id="cdbce-189">**Recommendations**</span></span><br>
  * <span data-ttu-id="cdbce-190">在 gazed 但不开始停留在特定停留目标上时，将整个行突出显示，但不会开始停留。</span><span class="sxs-lookup"><span data-stu-id="cdbce-190">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="cdbce-191">突出显示行时，仅显示停留目标，以减少视觉干扰。</span><span class="sxs-lookup"><span data-stu-id="cdbce-191">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="cdbce-192">清楚地与停留目标的位置一致。</span><span class="sxs-lookup"><span data-stu-id="cdbce-192">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="cdbce-193">不要一次显示所有停留目标，以避免重复的 UI。</span><span class="sxs-lookup"><span data-stu-id="cdbce-193">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="cdbce-194">尽可能频繁地重复使用同一模式，以建立 UX 熟悉。</span><span class="sxs-lookup"><span data-stu-id="cdbce-194">Reuse the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="cdbce-195">*映像： Microsoft Dynamics 365 指南列表*</span><span class="sxs-lookup"><span data-stu-id="cdbce-195">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南列表](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="cdbce-197">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cdbce-197">See also</span></span>

* [<span data-ttu-id="cdbce-198">凝视和提交</span><span class="sxs-lookup"><span data-stu-id="cdbce-198">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="cdbce-199">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="cdbce-199">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="cdbce-200">手 - 手势</span><span class="sxs-lookup"><span data-stu-id="cdbce-200">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="cdbce-201">手 - 指向并提交</span><span class="sxs-lookup"><span data-stu-id="cdbce-201">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="cdbce-202">本能交互</span><span class="sxs-lookup"><span data-stu-id="cdbce-202">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="cdbce-203">语音输入</span><span class="sxs-lookup"><span data-stu-id="cdbce-203">Voice input</span></span>](voice-input.md)
