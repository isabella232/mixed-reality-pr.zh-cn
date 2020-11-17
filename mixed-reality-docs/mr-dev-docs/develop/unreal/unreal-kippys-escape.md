---
title: Kippy 的转义
description: 按照我们的介绍，我们在 Unreal Engine 中探讨了如何在 Kippy 的
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Unreal，Unreal 引擎4，UE4，HoloLens，HoloLens 2，mixed reality，部署到设备，PC，文档，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
appliesto:
- HoloLens 2
ms.openlocfilehash: f5abfca4d5f85fd65aee77857d94a989122df310
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678946"
---
# <a name="the-making-of-kippys-escape"></a><span data-ttu-id="986a3-104">Kippy 的转义</span><span class="sxs-lookup"><span data-stu-id="986a3-104">The Making of Kippy's Escape</span></span>

<span data-ttu-id="986a3-105">自动唤醒机器人，使其 Kippy。</span><span class="sxs-lookup"><span data-stu-id="986a3-105">Kippy the robot wakes up to find itself stranded on an island.</span></span> <span data-ttu-id="986a3-106">你需要放在你的问题解决 hat 上，以帮助它找到返回到其火箭的途径！</span><span class="sxs-lookup"><span data-stu-id="986a3-106">It’s up to you to put on your problem-solving hat to help it find a path back to its rocket ship!</span></span> <span data-ttu-id="986a3-107">通过你 Microsoft Store 的 HoloLens 2 附带的内容，从 GitHub [下载应用程序](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) 或从 GitHub 克隆 [存储库](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) ，Kippy 主页安全！</span><span class="sxs-lookup"><span data-stu-id="986a3-107">Strap on your HoloLens 2 and [download the app](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) from the Microsoft Store or clone the [repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) from GitHub and get Kippy home safe!</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="986a3-108">如果要从 GitHub 存储库构建 Kippy 的转义，请确保使用的是 **Unreal Engine 4.25 或更高版本** 。</span><span class="sxs-lookup"><span data-stu-id="986a3-108">Make sure you're using **Unreal Engine 4.25 or later** if you're building Kippy's Escape from the GitHub repository.</span></span>

## <a name="overview"></a><span data-ttu-id="986a3-109">概述</span><span class="sxs-lookup"><span data-stu-id="986a3-109">Overview</span></span>

<span data-ttu-id="986a3-110">Kippy 的转义是使用 Unreal 引擎4和[混合现实 UX 工具（适用于 Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal)）生成的开源[HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware)示例应用。</span><span class="sxs-lookup"><span data-stu-id="986a3-110">Kippy’s Escape is an open-source [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware) sample app built with Unreal Engine 4 and [Mixed Reality UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal).</span></span> <span data-ttu-id="986a3-111">在此文章中，我们将指导你完成将 Kippy 的转义带入生活的过程，从第一个原则和视觉设计到实现和优化体验。</span><span class="sxs-lookup"><span data-stu-id="986a3-111">In this post, we’ll walk you through our process for bringing Kippy’s Escape to life, from first principles and visual design to implementing and optimizing the experience.</span></span> <span data-ttu-id="986a3-112">在 [Unreal 开发概述](unreal-development-overview.md)中，可以找到有关通过 MRTK UX 工具开发混合现实应用程序的详细信息。</span><span class="sxs-lookup"><span data-stu-id="986a3-112">You can find more information on developing Mixed Reality applications with MRTK UX Tools in the [Unreal development overview](unreal-development-overview.md).</span></span>

## <a name="first-principles"></a><span data-ttu-id="986a3-113">首要原则</span><span class="sxs-lookup"><span data-stu-id="986a3-113">First principles</span></span> 

<span data-ttu-id="986a3-114">在设置为创建 Kippy 的转义的过程中，我们的目标是创建一个可突出显示 [Unreal 引擎的 HoloLens 2 支持](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html)、hololens 2 功能和混合现实工具包的体验。</span><span class="sxs-lookup"><span data-stu-id="986a3-114">In setting out to create Kippy’s Escape, our goal was to create an experience that would highlight [Unreal Engine’s HoloLens 2 support](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html), the HoloLens 2’s capabilities, and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="986a3-115">我们想让开发人员想象一下他们可以通过 Unreal 和 HoloLens 2 创建的内容。</span><span class="sxs-lookup"><span data-stu-id="986a3-115">We wanted to inspire developers to imagine what they could create with Unreal and HoloLens 2.</span></span>  

<span data-ttu-id="986a3-116">我们提出了三个针对体验的指导原则：这是一项有趣的交互式工作，并面临进入的障碍。</span><span class="sxs-lookup"><span data-stu-id="986a3-116">We came up with three guiding principles for the experience: that it needed to be fun, interactive, and have a low barrier to entry.</span></span> <span data-ttu-id="986a3-117">我们希望经验非常直观，甚至首次混合现实用户都不需要教程。</span><span class="sxs-lookup"><span data-stu-id="986a3-117">We wanted the experience to be intuitive enough that even a first-time mixed reality user won’t need a tutorial to go through it.</span></span>  

## <a name="designing-the-game"></a><span data-ttu-id="986a3-118">设计游戏</span><span class="sxs-lookup"><span data-stu-id="986a3-118">Designing the game</span></span> 

<span data-ttu-id="986a3-119">HoloLens 2 可访问目前在游戏中的其他地方。</span><span class="sxs-lookup"><span data-stu-id="986a3-119">The HoloLens 2 has access to design features found nowhere else in gaming today.</span></span> <span data-ttu-id="986a3-120">对象可以使用您的手直接推送或操作，也可以使用目视跟踪来进行操作。</span><span class="sxs-lookup"><span data-stu-id="986a3-120">Objects can be directly pushed or manipulated using your hands or targeted with eye tracking.</span></span> <span data-ttu-id="986a3-121">这些关键功能在 Kippy 的转义中构建了一些有趣的时刻。</span><span class="sxs-lookup"><span data-stu-id="986a3-121">These key features are behind some of the fun moments we built out in Kippy’s Escape.</span></span>  

<span data-ttu-id="986a3-122">使用唯一的 HoloLens 2 功能作为游戏设计的指导，我们的作用域只是几个小环境方案。</span><span class="sxs-lookup"><span data-stu-id="986a3-122">Using the unique HoloLens 2 features as guidance for our game design, we scoped out a few small environment scenarios.</span></span> <span data-ttu-id="986a3-123">由于可以根据不同的播放机高度调整孤岛，并提供一些有趣的 bridge 创意。</span><span class="sxs-lookup"><span data-stu-id="986a3-123">Islands made a lot of sense because they can be adjusted for different player heights, and provided some entertaining bridge ideas.</span></span> <span data-ttu-id="986a3-124">从这里，我们着陆了古文明的主题与科幻技术的结合，这种想法表明有人通过刻录构建了一种奇怪的能源。</span><span class="sxs-lookup"><span data-stu-id="986a3-124">From there, we landed on the theme of ancient civilization meets sci-fi tech, with the idea that someone had built machinery over ruins harnessing a strange energy provided by each island.</span></span> <span data-ttu-id="986a3-125">每个孤岛都具有自己的外观，这是一项有助于创建视觉对象的详细信息。</span><span class="sxs-lookup"><span data-stu-id="986a3-125">The islands were each given their own look and feel, a detail that helped create visual interest.</span></span> <span data-ttu-id="986a3-126">建模和纹理间的一个良好平衡是为了使绘图调用对呈现性能的处理速度较低，因此，设计风格的外观是在设计时考虑的。</span><span class="sxs-lookup"><span data-stu-id="986a3-126">A good balance between modeling and texturing was top of mind to keep draw calls low for rendering performance, so a stylized look was designed with that in mind.</span></span> 

<span data-ttu-id="986a3-127">![早期游戏设计 ](images/kippys-escape/kippys-escape-img-01.png)
 *将一些更早的草图作为经验*</span><span class="sxs-lookup"><span data-stu-id="986a3-127">![Early game design sketches](images/kippys-escape/kippys-escape-img-01.png)
*Some early sketches for what the experience might look like*</span></span>

<span data-ttu-id="986a3-128">![第二个 ](images/kippys-escape/kippys-escape-img-02.png)
 *岛呈现* 的呈现</span><span class="sxs-lookup"><span data-stu-id="986a3-128">![Renderings of the second island](images/kippys-escape/kippys-escape-img-02.png)
*Renderings of the second island*</span></span>

<span data-ttu-id="986a3-129">为了保持较短的生产计划，我们同意在没有严格的动画周期的情况下，可以捕获意向和情感。</span><span class="sxs-lookup"><span data-stu-id="986a3-129">To keep within our short production schedule, we agreed that a floating character could capture intent and emotion without rigorous animation cycles.</span></span> <span data-ttu-id="986a3-130">那么 Kippy 是不是的。</span><span class="sxs-lookup"><span data-stu-id="986a3-130">And so Kippy was born!</span></span> <span data-ttu-id="986a3-131">它通过眼睛和简单沉默声音效果 emotes 几个不同的表达式，以帮助指导玩家体验。</span><span class="sxs-lookup"><span data-stu-id="986a3-131">It emotes a few different expressions through its eyes and through minimalistic vocal sound effects to help guide the player throughout the experience.</span></span> 

![Kippy 通过其眼睛显示不同的表达式](images/kippys-escape/kippys-escape-img-03.gif)

<span data-ttu-id="986a3-133">*Kippy 通过其眼睛显示不同的表达式*</span><span class="sxs-lookup"><span data-stu-id="986a3-133">*Kippy showing different expressions via its eyes*</span></span>

![如果用户需要花费很长时间来解决测验题，Kippy 会向用户提示](images/kippys-escape/kippys-escape-img-04.gif)

<span data-ttu-id="986a3-135">*如果用户需要花费很长时间来解决测验题，Kippy 会向用户提示*</span><span class="sxs-lookup"><span data-stu-id="986a3-135">*If the user takes too long to solve a puzzle, Kippy will give the user a hint*</span></span>

<span data-ttu-id="986a3-136">除了字符和环境设计外，我们还进行了 concerted 的工作，让游戏变得有趣。</span><span class="sxs-lookup"><span data-stu-id="986a3-136">Beyond the character and environment design, we made a concerted effort to make the game feel fun.</span></span> <span data-ttu-id="986a3-137">目视跟踪允许我们激发材料和声音属性，其中突出显示了游戏的关键部分。</span><span class="sxs-lookup"><span data-stu-id="986a3-137">Eye tracking allowed us to fire off material and sound attributes, which highlighted key pieces of the game.</span></span> <span data-ttu-id="986a3-138">空间音频有助于使这些级别在播放机的周围处于家里。</span><span class="sxs-lookup"><span data-stu-id="986a3-138">Spatial audio helped make the levels feel at home in the player’s surroundings.</span></span> <span data-ttu-id="986a3-139">能够抓住对象、推送按钮和操作滑块推动创新的播放器活动，因此确保这些连接点感觉很重要。</span><span class="sxs-lookup"><span data-stu-id="986a3-139">Being able to grab objects, push buttons and manipulate sliders drives innovative player engagements, so it was important to make sure these connection points felt natural.</span></span> 

![桥接电缆结束时，用户将对其进行接近](images/kippys-escape/kippys-escape-img-05.gif)

<span data-ttu-id="986a3-141">*桥接电缆结束时，用户将对其进行接近*</span><span class="sxs-lookup"><span data-stu-id="986a3-141">*The end of the bridge cable glows when the user’s hand approaches it*</span></span>

## <a name="building-the-game-mechanics"></a><span data-ttu-id="986a3-142">构建游戏机制</span><span class="sxs-lookup"><span data-stu-id="986a3-142">Building the game mechanics</span></span> 

<span data-ttu-id="986a3-143">Kippy 的转义很大程度上依赖于混合现实 UX 工具组件，以使游戏成为交互的（即手交互参与者、边界控件、操控器、滑杆和按钮）。</span><span class="sxs-lookup"><span data-stu-id="986a3-143">Kippy’s Escape relies heavily on Mixed Reality UX Tools components to make the game interactive - namely hand interaction actors, bounds controls, manipulators, sliders, and buttons.</span></span>   

<span data-ttu-id="986a3-144">[手动交互执行组件](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html)允许直接和远端操作全息影像。</span><span class="sxs-lookup"><span data-stu-id="986a3-144">The [hand interaction actor](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html) enables both direct and far manipulation of holograms.</span></span> <span data-ttu-id="986a3-145">在 Kippy 的转义开始时，用户有机会设置游戏的位置。</span><span class="sxs-lookup"><span data-stu-id="986a3-145">At the start of Kippy’s Escape, the user is given the opportunity to set the location of the game.</span></span> <span data-ttu-id="986a3-146">手动光标从用户的掌中进行扩展，可以轻松地操作距离较远的大全息影像，如以下 gif 所示。</span><span class="sxs-lookup"><span data-stu-id="986a3-146">Hand beams extending from the user’s palm make it easy to manipulate large holograms that are far away, as seen in the gif below.</span></span>  

![手动交互执行组件 gif](images/kippys-escape/kippys-escape-img-06.gif)

<span data-ttu-id="986a3-148">占位符场景本身可使用 UX 工具的 [边界控件](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/BoundsControl.html) 组件进行拖动和旋转。</span><span class="sxs-lookup"><span data-stu-id="986a3-148">The placeholder scene itself can be dragged and rotated using UX Tools’ [bounds control](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/BoundsControl.html) component.</span></span>  

<span data-ttu-id="986a3-149">在第二个岛上，用户必须选择宝物，并将其放入匹配的插槽中。</span><span class="sxs-lookup"><span data-stu-id="986a3-149">On the second island, the user must pick up gems and place them in their matching slots.</span></span> <span data-ttu-id="986a3-150">这些 gem 附加了操控器，这些 [操控](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html) 器允许用户选取它们并将其放置。</span><span class="sxs-lookup"><span data-stu-id="986a3-150">The gems have [manipulators](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html) attached to them that allow the user to pick them up and place them down.</span></span> 

![操控器示例 gif](images/kippys-escape/kippys-escape-img-07.gif)

<span data-ttu-id="986a3-152">[Pressable 按钮](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html)是在第三个岛上使用炸弹的关键所在。</span><span class="sxs-lookup"><span data-stu-id="986a3-152">A [pressable button](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html) is the key to bringing up bombs for use on the third island.</span></span>  

![Pressable 按钮示例 gif](images/kippys-escape/kippys-escape-img-08.gif)

<span data-ttu-id="986a3-154">第四个岛上会出现一个 [滑块](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PinchSlider.html) 组件，触发要引发的最终桥。</span><span class="sxs-lookup"><span data-stu-id="986a3-154">A [slider](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PinchSlider.html) component appears on the fourth island, triggering the final bridge to be raised.</span></span>  

![滑块组件示例 gif](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a><span data-ttu-id="986a3-156">针对 HoloLens 2 进行优化</span><span class="sxs-lookup"><span data-stu-id="986a3-156">Optimizing for HoloLens 2</span></span> 

<span data-ttu-id="986a3-157">对于在移动设备上运行的任何体验，请务必关注性能。</span><span class="sxs-lookup"><span data-stu-id="986a3-157">With any experience built to run on a mobile device, keeping an eye on performance is critical.</span></span> <span data-ttu-id="986a3-158">Unreal 4.25 包括一个用于支持移动多视图的主要更新，这大大减少了渲染开销并提升了帧速率。</span><span class="sxs-lookup"><span data-stu-id="986a3-158">Unreal 4.25 includes a major update to support for mobile multi-view, which significantly reduces rendering overhead and boosts frame-rate.</span></span> <span data-ttu-id="986a3-159">建议在进行优化时，使用 Unreal 来查看适用于 HoloLens 2 的其他 [建议性能设置](performance-recommendations-for-unreal.md) 。</span><span class="sxs-lookup"><span data-stu-id="986a3-159">We recommend checking out our other [recommended performance settings](performance-recommendations-for-unreal.md) for HoloLens 2 development with Unreal when you're optimizing.</span></span>  

<span data-ttu-id="986a3-160">物理学对象在性能方面仍会成本高昂，因此使用了一些巧妙的解决方法。</span><span class="sxs-lookup"><span data-stu-id="986a3-160">Physics objects still remain costly for performance, so a couple clever workarounds were used.</span></span> <span data-ttu-id="986a3-161">例如，第三个 "桥" 需要吹一些阻止方法的碎片。</span><span class="sxs-lookup"><span data-stu-id="986a3-161">For instance, the third “bridge” requires blowing up some debris blocking the stairway.</span></span> <span data-ttu-id="986a3-162">炸弹引爆不会将石子影响为物理学对象，而是通过切换静态石子来实现分解粒子效果。</span><span class="sxs-lookup"><span data-stu-id="986a3-162">Instead of having a force impact the stones as physics objects, the bomb detonation triggers a swap, switching the static stones for an exploding particle effect.</span></span> 

![针对 HoloLens 2 gif 优化的示例](images/kippys-escape/kippys-escape-img-10.gif) 

<span data-ttu-id="986a3-164">我们还将我们的绘图调用从400减少到 ~ 260：</span><span class="sxs-lookup"><span data-stu-id="986a3-164">We also cut down our draw calls from over 400 to  ~260 by:</span></span> 
* <span data-ttu-id="986a3-165">降低网格复杂性</span><span class="sxs-lookup"><span data-stu-id="986a3-165">Reducing mesh complexity</span></span>
* <span data-ttu-id="986a3-166">组合网格</span><span class="sxs-lookup"><span data-stu-id="986a3-166">Combining meshes</span></span>
* <span data-ttu-id="986a3-167">删除某些初始动态照明元素</span><span class="sxs-lookup"><span data-stu-id="986a3-167">Removing some of our initial dynamic lighting elements</span></span>

<span data-ttu-id="986a3-168">虽然我们可能还有更多的操作，但我们认为这是性能和视觉质量之间的良好平衡。</span><span class="sxs-lookup"><span data-stu-id="986a3-168">While there’s likely more we could have done, we felt that was a good balance between performance and visual quality.</span></span>  

## <a name="try-it-out"></a><span data-ttu-id="986a3-169">试试看！</span><span class="sxs-lookup"><span data-stu-id="986a3-169">Try it out!</span></span> 

<span data-ttu-id="986a3-170">启动 HoloLens 2 并从 Microsoft Store [下载](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) 应用程序，或从 GitHub 克隆 [存储库](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) 并自己生成应用！</span><span class="sxs-lookup"><span data-stu-id="986a3-170">Boot up your HoloLens 2 and [download](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) the app from the Microsoft Store, or clone the [repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) from GitHub and build the app yourself!</span></span>  

## <a name="about-the-team"></a><span data-ttu-id="986a3-171">关于团队</span><span class="sxs-lookup"><span data-stu-id="986a3-171">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><span data-ttu-id="986a3-172"><b>插孔抑符</b></span><span class="sxs-lookup"><span data-stu-id="986a3-172"><b>Jack Caron</b></span></span><br><span data-ttu-id="986a3-173"><i>线索游戏设计器</i></span><span class="sxs-lookup"><span data-stu-id="986a3-173"><i>Lead Game Designer</i></span></span><br><span data-ttu-id="986a3-174">插孔当前适用于 Microsoft 的混合现实体验，包括 HoloLens 2 项目和 AltspaceVR，以前是 HoloLens 平台团队的设计器。</span><span class="sxs-lookup"><span data-stu-id="986a3-174">Jack currently works on Mixed Reality experiences for Microsoft, including HoloLens 2 projects and AltspaceVR, and was previously a designer on the HoloLens platform team.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><span data-ttu-id="986a3-175"><b>夏季 Wu</b></span><span class="sxs-lookup"><span data-stu-id="986a3-175"><b>Summer Wu</b></span></span><br><span data-ttu-id="986a3-176"><i>创建器</i></span><span class="sxs-lookup"><span data-stu-id="986a3-176"><i>Producer</i></span></span><br><span data-ttu-id="986a3-177">夏季适用于混合现实开发人员平台，并领导团队与 Unreal 引擎相关的工作。</span><span class="sxs-lookup"><span data-stu-id="986a3-177">Summer works on the mixed reality developer platform and heads the team’s Unreal Engine related efforts.</span></span></td>
</tr>
</table>

<span data-ttu-id="986a3-178">特别感谢我们 [Framestore](https://www.framestore.com/) 的朋友，帮助我们将 Kippy 的转义转到下一级别。</span><span class="sxs-lookup"><span data-stu-id="986a3-178">Special thanks to our friends at [Framestore](https://www.framestore.com/) for helping us take Kippy’s Escape to the next level.</span></span> <span data-ttu-id="986a3-179">从字符开发到资产设计，再到游戏编程，对此项目的协作是 pivotal 的。</span><span class="sxs-lookup"><span data-stu-id="986a3-179">From character development, to asset design, to game programming, their collaboration on this project was pivotal.</span></span>  