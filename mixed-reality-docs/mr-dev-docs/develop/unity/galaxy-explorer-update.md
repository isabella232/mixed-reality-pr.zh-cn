---
title: 针对 HoloLens 2 的 Galaxy 资源管理器创建
description: 了解我们的团队如何在 GitHub 上更新 HoloLens 2 的 Galaxy 资源管理器开源项目。
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: galaxy 资源管理器，案例研究，项目，示例，MRTK，混合现实工具包，Unity，示例应用，示例应用，开源，Microsoft Store，HoloLens，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: d3a31204275b2d2a9f1f1ea1c283993d2e0285ed
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009577"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a><span data-ttu-id="5d58c-104">针对 HoloLens 2 的 Galaxy 资源管理器创建</span><span class="sxs-lookup"><span data-stu-id="5d58c-104">The Making of Galaxy Explorer for HoloLens 2</span></span>

<span data-ttu-id="5d58c-105">欢迎使用适用于 HoloLens 2 应用程序的已更新 Galaxy 资源管理器！</span><span class="sxs-lookup"><span data-stu-id="5d58c-105">Welcome to the updated Galaxy Explorer for HoloLens 2 application!</span></span> <span data-ttu-id="5d58c-106">[Galaxy 资源管理器](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer "星系探索者") 最初是作为一种开源应用程序开发的， (第一代) 通过共享你的想法计划，这是许多人的第一种混合现实体验之一。</span><span class="sxs-lookup"><span data-stu-id="5d58c-106">[Galaxy Explorer](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer "Galaxy Explorer") was originally developed as an open-source application for HoloLens (first gen) through the Share Your Idea program, and is one of the first mixed reality experiences many people had.</span></span> <span data-ttu-id="5d58c-107">现在我们正在更新它，以获得 [HoloLens 2 的全新功能](https://www.microsoft.com/hololens/hardware)。</span><span class="sxs-lookup"><span data-stu-id="5d58c-107">Now we're updating it for the [new and exciting capabilities of HoloLens 2](https://www.microsoft.com/hololens/hardware).</span></span>

<span data-ttu-id="5d58c-108">作为 [Microsoft 混合现实工作室](galaxy-explorer-update.md#mixed-reality-studios)之一，我们通常会开发商业级解决方案，并在整个创意和开发过程中在目标平台上开发 & 测试。</span><span class="sxs-lookup"><span data-stu-id="5d58c-108">As one of the [Microsoft Mixed Reality Studios](galaxy-explorer-update.md#mixed-reality-studios), we usually develop commercial grade solutions and are developing & testing on target platforms throughout the creative and development process.</span></span> <span data-ttu-id="5d58c-109">我们将使用 (的框架和工具（例如) [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) ）来着手此项目，并将其提供给我们和社区，我们想要将你带入。</span><span class="sxs-lookup"><span data-stu-id="5d58c-109">We're embarking on this project using the frameworks and tools (like [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)) as they become available to us and the community - and we want to bring you along for the ride.</span></span>

<span data-ttu-id="5d58c-110">正如原始 Galaxy 资源管理器， [我们的团队](galaxy-explorer-update.md#meet-the-team) 将在 [GitHub 上提供项目](https://github.com/Microsoft/GalaxyExplorer) ，以确保社区具有完全访问权限。</span><span class="sxs-lookup"><span data-stu-id="5d58c-110">Just like the original Galaxy Explorer, [our team](galaxy-explorer-update.md#meet-the-team) will be [open sourcing the project on GitHub](https://github.com/Microsoft/GalaxyExplorer) to ensure the community has full access.</span></span> <span data-ttu-id="5d58c-111">我们还将在这里记录我们的旅程，以全面了解我们如何从 MRTK v1 迁移到 MRTK v2，使用 HoloLens 2 中提供的新功能增强了体验，并确保了 Galaxy 资源管理器保持了多平台体验。</span><span class="sxs-lookup"><span data-stu-id="5d58c-111">We'll also be documenting our journey here in complete transparency about how we ported from MRTK v1 to MRTK v2, enhanced the experience with new features available in HoloLens 2, and ensured that Galaxy Explorer remained a multi-platform experience.</span></span> <span data-ttu-id="5d58c-112">无论你是在 HoloLens (第一代) 、HoloLens 2、Windows Mixed Reality 耳机还是 Windows 10 桌面上查看 Galaxy 资源管理器，我们都需要确保你充分利用我们的旅程！</span><span class="sxs-lookup"><span data-stu-id="5d58c-112">Whether you're viewing Galaxy Explorer on HoloLens (first gen), HoloLens 2, a Windows Mixed Reality headset or on your Windows 10 desktop, we want to make sure you're enjoying the journey as much as we are!</span></span>

<span data-ttu-id="5d58c-113">此页将随着我们在项目中的进展而扩展，并提供指向更详细的文章、代码、设计项目和其他 MRTK 文档的链接，为你提供内幕的项目。</span><span class="sxs-lookup"><span data-stu-id="5d58c-113">This page will expand as we progress through the project with links to more detailed articles, code, design artifacts, and additional MRTK documentation to provide you with an insider's look at the project.</span></span>

## <a name="unveiling-the-new-logo"></a><span data-ttu-id="5d58c-114">揭示新徽标</span><span class="sxs-lookup"><span data-stu-id="5d58c-114">Unveiling the new logo</span></span>

<span data-ttu-id="5d58c-115">我们很高兴开始使用新的 Galaxy 资源管理器徽标的预览！</span><span class="sxs-lookup"><span data-stu-id="5d58c-115">We're excited to kick off with a preview of the new Galaxy Explorer logo!</span></span> <span data-ttu-id="5d58c-116">通过采用银河的方式将献给支付给原始徽标，我们设计出了真实的可视化效果，并更新了版式以提供更新式的外观。</span><span class="sxs-lookup"><span data-stu-id="5d58c-116">While paying homage to the original logo by featuring the Milky Way, we've designed a realistic visualization and updated the typography to provide a more modern feel.</span></span> <span data-ttu-id="5d58c-117">徽标中包含的抢先了解可查看其中一个新图标。</span><span class="sxs-lookup"><span data-stu-id="5d58c-117">Included in the logo is a sneak peek at one of the new icons.</span></span>

![新建 Galaxy 资源管理器徽标](images/ge-update-app-icon.png)

<span data-ttu-id="5d58c-119">徽标的设计和版式将为用户界面元素的总体外观和感觉设置音调。</span><span class="sxs-lookup"><span data-stu-id="5d58c-119">The design and typography of the logo will set the tone for the overall look and feel of UI elements throughout the experience.</span></span> 

## <a name="thinking-about-interactions"></a><span data-ttu-id="5d58c-120">考虑交互</span><span class="sxs-lookup"><span data-stu-id="5d58c-120">Thinking about interactions</span></span>

<span data-ttu-id="5d58c-121">作为一录音室，我们兴奋了将 Galaxy 资源管理器移植到 HoloLens 2 的权限。</span><span class="sxs-lookup"><span data-stu-id="5d58c-121">As a creative studio, we were ecstatic about the privilege to port Galaxy Explorer to HoloLens 2.</span></span> <span data-ttu-id="5d58c-122">我们知道，我们希望体验成为新设备的庆祝，并说明混合现实能力仅受想像的限制。</span><span class="sxs-lookup"><span data-stu-id="5d58c-122">We knew from the start that we wanted the experience to be a celebration of the new device and to demonstrate that Mixed Reality empowerment is limited only by the imagination.</span></span>

<span data-ttu-id="5d58c-123">HoloLens 2 使用户能够以自然的方式触摸、抓住和移动全息影像–它们的响应方式非常类似于真实的对象。</span><span class="sxs-lookup"><span data-stu-id="5d58c-123">HoloLens 2 allows users to touch, grasp, and move holograms in ways that feel natural – they respond a lot like real objects.</span></span> <span data-ttu-id="5d58c-124">完全表述的手模型非常惊人，因为这样可以让用户看起来自然。</span><span class="sxs-lookup"><span data-stu-id="5d58c-124">Fully articulated hand models are amazing, because it lets users do what feels natural.</span></span> <span data-ttu-id="5d58c-125">例如，每个人都以略有不同的方式挑选一个杯，而不是实施一种特殊的方式来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="5d58c-125">For example, everybody picks up a cup slightly differently – and instead of enforcing one particular way to do it, HoloLens 2 lets you do it your way.</span></span>

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

<span data-ttu-id="5d58c-126">这是第一代 HoloLens 设备上基于 Air 的接口的重大更改。</span><span class="sxs-lookup"><span data-stu-id="5d58c-126">This is a significant change from the Air Tap-based interfaces on first-generation HoloLens devices.</span></span> <span data-ttu-id="5d58c-127">用户现在可以 "关闭" 和 "个人"，而不是从距离交互。</span><span class="sxs-lookup"><span data-stu-id="5d58c-127">Instead of interacting with holograms from a distance, users can now get "up close and personal".</span></span> <span data-ttu-id="5d58c-128">将现有的体验移植到 HoloLens 2 或规划新的体验时，请务必熟悉全息影像的直接操作。</span><span class="sxs-lookup"><span data-stu-id="5d58c-128">When porting existing experiences over to HoloLens 2 or planning new ones, it's important to make yourself familiar with the direct manipulation of holograms.</span></span>

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a><span data-ttu-id="5d58c-129">直接操作与空间中的远距离</span><span class="sxs-lookup"><span data-stu-id="5d58c-129">Direct manipulation vs. the vast distances in space</span></span>

<span data-ttu-id="5d58c-130">这是一种神奇的体验，可以抓住并抓住行星。</span><span class="sxs-lookup"><span data-stu-id="5d58c-130">It's a magical experience to reach out, grab a planet and hold it in your hand.</span></span> <span data-ttu-id="5d58c-131">这种方法的挑战在于太阳系的大小–非常巨大！</span><span class="sxs-lookup"><span data-stu-id="5d58c-131">The challenge with this approach is the size of the solar system – it's huge!</span></span> <span data-ttu-id="5d58c-132">用户需要浏览其空间，使每个行星都能与其交互。</span><span class="sxs-lookup"><span data-stu-id="5d58c-132">The user would need to walk around their room to get close to each planet to interact with it.</span></span>

<span data-ttu-id="5d58c-133">为了使用户能够与远离远处的对象进行交互，MRTK 提供了从用户掌上走出的手的光线，作为手型的延伸。</span><span class="sxs-lookup"><span data-stu-id="5d58c-133">To allow users to interact with objects that are farther away, MRTK offers hand rays that shoot out from the center of the user's palm, acting as an extension of the hand.</span></span> <span data-ttu-id="5d58c-134">环形光标连接到射线的末尾，以指示该射线与目标对象相交的位置。</span><span class="sxs-lookup"><span data-stu-id="5d58c-134">A donut-shaped cursor is attached to the end of the ray to indicate where the ray intersects with a target object.</span></span> <span data-ttu-id="5d58c-135">然后光标所指向的对象可以接收来自手的手势命令。</span><span class="sxs-lookup"><span data-stu-id="5d58c-135">The object that the cursor lands on can then receive gestural commands from the hand.</span></span> 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

<span data-ttu-id="5d58c-136">在 "Galaxy 资源管理器" 的原始版本中，用户将以 "注视" 光标为地球，然后单击 "空中" 将其调近。</span><span class="sxs-lookup"><span data-stu-id="5d58c-136">In the original version of Galaxy Explorer, the user would target a planet with the gaze cursor and then air tap to call it closer.</span></span> <span data-ttu-id="5d58c-137">将体验移植到 HoloLens 2 的最简单方法是采用这种行为，并使用手型来选择行星。</span><span class="sxs-lookup"><span data-stu-id="5d58c-137">The easiest way to port the experience to HoloLens 2 is to take this behavior and use hand rays to select planets.</span></span> <span data-ttu-id="5d58c-138">虽然这是正常运行的，但仍希望获得更多的功能。</span><span class="sxs-lookup"><span data-stu-id="5d58c-138">While this was functional, it left us wanting more.</span></span>

### <a name="back-to-the-drawing-board"></a><span data-ttu-id="5d58c-139">返回绘图板</span><span class="sxs-lookup"><span data-stu-id="5d58c-139">Back to the drawing board</span></span>

<span data-ttu-id="5d58c-140">我们一起介绍了可在现有交互基础上构建的 ideate。</span><span class="sxs-lookup"><span data-stu-id="5d58c-140">We came together to ideate what could be built on top of the existing interactions.</span></span> <span data-ttu-id="5d58c-141">思维方式：尽管 HoloLens 2 允许用户以自然的方式与全息影像交互，但全息影像按定义不是真实的。</span><span class="sxs-lookup"><span data-stu-id="5d58c-141">The thinking was: Although HoloLens 2 allows users to interact with holograms in natural, realistic ways, holograms are by definition not real.</span></span> <span data-ttu-id="5d58c-142">因此，只要用户的交互是变得合理的，就不会有可能与真正的对象进行交互，而是不是很重要。</span><span class="sxs-lookup"><span data-stu-id="5d58c-142">So as long as an interaction is plausible for the user, it doesn't matter if that interaction would be possible with a real object or not – we can make it possible.</span></span>

<span data-ttu-id="5d58c-143">我们研究的一个概念就是基于 telekinesis –处理对象的能力。</span><span class="sxs-lookup"><span data-stu-id="5d58c-143">One concept that we explored was based on telekinesis – the power to manipulate objects with one's mind.</span></span> <span data-ttu-id="5d58c-144">通常，在超大英雄电影中，一个人会与他们的想法联系起来，并将一个对象调入他们的手中。</span><span class="sxs-lookup"><span data-stu-id="5d58c-144">Often seen in super hero movies, a person would reach out with their mind and call an object into their open hand.</span></span> <span data-ttu-id="5d58c-145">我们将使用一种更多的方法进行介绍，并提供该概念如何工作的快速草图。</span><span class="sxs-lookup"><span data-stu-id="5d58c-145">We played around with the idea some more and came up with a quick sketch of how the concept could work.</span></span>

![强制抓取交互的概念](images/ge-update-interactions-concept-force-grab.png)

<span data-ttu-id="5d58c-147">用户会将手型点指向地球，这将提供目标反馈。</span><span class="sxs-lookup"><span data-stu-id="5d58c-147">The user would point the hand ray at a planet, which would provide target feedback.</span></span> <span data-ttu-id="5d58c-148">随着用户的张开，世界将通过神奇强制向用户拉取，直到其接近，才能获取它。</span><span class="sxs-lookup"><span data-stu-id="5d58c-148">As the user then extends their open hand, the planet would be pulled towards the user by a magical force until it's close enough to grab it.</span></span> <span data-ttu-id="5d58c-149">因此，我们要实现交互：强制获取的名称。</span><span class="sxs-lookup"><span data-stu-id="5d58c-149">Hence our name for the interaction: force grab.</span></span> <span data-ttu-id="5d58c-150">由于用户会将地球向外推，它会再次返回到其轨道。</span><span class="sxs-lookup"><span data-stu-id="5d58c-150">As the user would push away the planet with their open hand, it would return again to its orbit.</span></span>

### <a name="force-grab-prototyping"></a><span data-ttu-id="5d58c-151">强制获取抽取原型</span><span class="sxs-lookup"><span data-stu-id="5d58c-151">Force grab prototyping</span></span>

<span data-ttu-id="5d58c-152">接下来，我们创建了多个原型来测试概念：交互的整体效果如何？</span><span class="sxs-lookup"><span data-stu-id="5d58c-152">We then created multiple prototypes to test the concept: How does the interaction feel overall?</span></span> <span data-ttu-id="5d58c-153">被调用的对象是否会在用户前面停止或一直到其上，直到放置？</span><span class="sxs-lookup"><span data-stu-id="5d58c-153">Should the called object stop in front of the user or stick to their hands until placed?</span></span> <span data-ttu-id="5d58c-154">调用对象是否应在调用时更改大小或缩放？</span><span class="sxs-lookup"><span data-stu-id="5d58c-154">Should the called object change size or scale while being called?</span></span>

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a><span data-ttu-id="5d58c-155">在应用程序中实现强制抓取</span><span class="sxs-lookup"><span data-stu-id="5d58c-155">Implementing force grab into the application</span></span>

<span data-ttu-id="5d58c-156">当我们在行星上尝试抓住强制时，我们意识到我们不得不改变阳历系统的刻度。</span><span class="sxs-lookup"><span data-stu-id="5d58c-156">When we tried the force grab on planets, we realized that we had to change the scale of the solar system.</span></span> <span data-ttu-id="5d58c-157">事实证明，阳历系统的准确、中等大小的表示形式对于用户来说很难理解和导航，他们不知道要查找的位置。</span><span class="sxs-lookup"><span data-stu-id="5d58c-157">It turned out that an accurate, medium-sized representation of the solar system is difficult for users to understand and navigate - they didn't know where to look.</span></span> <span data-ttu-id="5d58c-158">但是，小型表示形式使得某些行星太小，无法轻松选择。</span><span class="sxs-lookup"><span data-stu-id="5d58c-158">However, a small-sized-representation made some planets too small to be easily selected.</span></span> <span data-ttu-id="5d58c-159">因此，行星的大小和阳历之间的间距设计为在中等大小的房间内自如，同时保持相对准确性。</span><span class="sxs-lookup"><span data-stu-id="5d58c-159">As a result, the size of the planets and the spacing between solar objects was designed to feel comfortable within a medium-sized room while maintaining relative accuracy.</span></span>

<span data-ttu-id="5d58c-160">在开发冲刺（sprint）的更高阶段，我们已有足够的高手，足以让 MSFT 混合现实专家参与，因此我们努力将其输入作为专家测试人员并在强制抓取交互中快速迭代。</span><span class="sxs-lookup"><span data-stu-id="5d58c-160">During the later stages of our development sprint, we were lucky enough to have fellow MSFT Mixed Reality experts in-house, so we got to work getting their input as expert testers and doing quick iterations on the force grab interaction.</span></span>

![来自 Kam 测试 Galaxy 资源管理器的预览版本](images/ge-update-user-testing.png)

<span data-ttu-id="5d58c-162">图片：来自 Kam，高级设计主管，测试 Galaxy 资源管理器的工作。</span><span class="sxs-lookup"><span data-stu-id="5d58c-162">In picture: Jenny Kam, Senior Design Lead, testing a work-in-progress of Galaxy Explorer.</span></span>

### <a name="adding-affordances-for-targeting"></a><span data-ttu-id="5d58c-163">为目标添加实用</span><span class="sxs-lookup"><span data-stu-id="5d58c-163">Adding affordances for targeting</span></span>

<span data-ttu-id="5d58c-164">在 HoloLens 2 上 vspackage 时，我们发现，即使新的交互是自然而直观的，全息影像仍保持不变：无权重或 tactile sensations。</span><span class="sxs-lookup"><span data-stu-id="5d58c-164">As we experimented on HoloLens 2, we found that even though the new interactions are natural and intuitive, holograms remain the same: with no weight or tactile sensations.</span></span> <span data-ttu-id="5d58c-165">由于全息影像并不提供用户在与对象交互时接收的自然反馈，因此我们需要创建它们。</span><span class="sxs-lookup"><span data-stu-id="5d58c-165">Since holograms don't provide natural feedback that humans are used to receiving when they interact with objects, we needed to create them.</span></span>

<span data-ttu-id="5d58c-166">我们考虑到了视觉对象和音频反馈，用户将为其交互的各个阶段提供这些反馈，因为强制获取机制是与 Galaxy 资源管理器进行交互的核心，所以我们做了很多迭代。</span><span class="sxs-lookup"><span data-stu-id="5d58c-166">We thought about the visual and audio feedback that users would be provided for the various stages of their interactions, and since the force grab mechanism is central to interacting with Galaxy Explorer, we did many iterations.</span></span> <span data-ttu-id="5d58c-167">目标是为交互的每个阶段查找音频和视觉反馈的适当平衡：集中于预期对象，将其调用给用户，然后将其发布。</span><span class="sxs-lookup"><span data-stu-id="5d58c-167">The aim was to find the right balance of audio and visual feedback for each stage of the interaction: focusing on the intended object, calling it to the user, and then releasing it.</span></span> <span data-ttu-id="5d58c-168">我们学到的是，与我们用于 HoloLens (第一代) 相比，需要更多的音频和视觉反馈来强化交互。</span><span class="sxs-lookup"><span data-stu-id="5d58c-168">What we learned is that more audio and visual feedback was required to reinforce the interaction than we were used to for HoloLens (first gen).</span></span>

![行星上的视觉对象实用](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a><span data-ttu-id="5d58c-170">添加实用以进行强制获取</span><span class="sxs-lookup"><span data-stu-id="5d58c-170">Adding affordances for force grab</span></span>
 
<span data-ttu-id="5d58c-171">随着音频和视觉对象实用的基本强制获取机制，我们了解了如何使选择的行星更易于用户理解。</span><span class="sxs-lookup"><span data-stu-id="5d58c-171">Once we had the basic force grab mechanism with audio and visual affordances, we looked at how to make selecting planets more user-friendly.</span></span> <span data-ttu-id="5d58c-172">要解决的主要问题是：由于太阳系是一个三维移动界面，因此用户可以更灵活地了解如何以一致的方式为对象提供目标。</span><span class="sxs-lookup"><span data-stu-id="5d58c-172">There were two main things to address: Because the solar system is a 3D moving interface, there's added complexity for users to learn how to target objects consistently.</span></span> <span data-ttu-id="5d58c-173">这是一种复杂的情况，那就是，在选择对象时，手型的速度很快，使行星迅速进入用户。</span><span class="sxs-lookup"><span data-stu-id="5d58c-173">This was compounded by the fact that the hand ray is fast at selecting an object, making planets move towards the user incredibly quickly.</span></span>

<span data-ttu-id="5d58c-174">我们使用三个方面的解决方案来做到这一点。</span><span class="sxs-lookup"><span data-stu-id="5d58c-174">We approached this with a three-pronged solution.</span></span> <span data-ttu-id="5d58c-175">第一种方法非常直观：降低选择过程的速度，使行星更自然地处理用户。</span><span class="sxs-lookup"><span data-stu-id="5d58c-175">The first was fairly intuitive: slow down the selection process so that planets approach the user at a more natural pace.</span></span> <span data-ttu-id="5d58c-176">调整速度后，我们必须重新访问音频和视觉对象实用，添加音频反馈作为向用户跟踪的行星。</span><span class="sxs-lookup"><span data-stu-id="5d58c-176">Once the speed was adjusted, we had to revisit the audio and visual affordances, adding audio feedback as the planet tracked towards the user.</span></span>

<span data-ttu-id="5d58c-177">解决方案的第二部分是使整个强制抓取交互成为有形的视觉对象。</span><span class="sxs-lookup"><span data-stu-id="5d58c-177">The second part of the solution was to make the visualization of the entire force grab interaction tangible.</span></span> <span data-ttu-id="5d58c-178">我们直观地显示了一条粗线条，它在与目标对象连接后，将其移至目标对象，然后将该对象移回用户喜欢的套索。</span><span class="sxs-lookup"><span data-stu-id="5d58c-178">We visualized a thick line that moves towards the targeted object once the hand ray connects with it, and then brings the object back to the user - like a lasso.</span></span> 

![用于强制抓取的视觉 "套索" 实用](images/ge-update-lasso-affordances.png)

<span data-ttu-id="5d58c-180">最后，我们优化了太阳系的规模，以便用户看好行星，并将其作为目标。</span><span class="sxs-lookup"><span data-stu-id="5d58c-180">Finally, we optimized the scale of the solar system so that the planets were large enough for the user's gaze and hand ray to target them.</span></span> 

<span data-ttu-id="5d58c-181">这三项改进允许用户进行精确选择，并以直观的方式为他们打电话。</span><span class="sxs-lookup"><span data-stu-id="5d58c-181">These three improvements allowed users to make accurate selections, calling planets to them in an intuitive way.</span></span> <span data-ttu-id="5d58c-182">总体而言，最终强制获取的效果是在太阳系中获得更具沉浸和交互性的体验。</span><span class="sxs-lookup"><span data-stu-id="5d58c-182">Overall, the effect of the final force grab is a more immersive and interactive experience in the solar system.</span></span>

## <a name="spotlight-on-jupiter"></a><span data-ttu-id="5d58c-183">在木星上聚焦</span><span class="sxs-lookup"><span data-stu-id="5d58c-183">Spotlight on Jupiter</span></span>

<span data-ttu-id="5d58c-184">以银河的方式创建日光体是一种 humbling 体验。</span><span class="sxs-lookup"><span data-stu-id="5d58c-184">Creating the solar bodies of the Milky Way was a humbling experience.</span></span> <span data-ttu-id="5d58c-185">具体而言，木星的独特特性使其对瞧可见。</span><span class="sxs-lookup"><span data-stu-id="5d58c-185">In particular, the unique characteristics of Jupiter make it a sight to behold.</span></span> <span data-ttu-id="5d58c-186">它是气体巨量的最大和最大的质量，比所有其他行星组合的质量大。</span><span class="sxs-lookup"><span data-stu-id="5d58c-186">It's the largest and most colorful of the gas giants, and contains more mass than all other planets combined.</span></span> <span data-ttu-id="5d58c-187">Turbulence 和 cloud dynamics 的非常大的大小和 mesmerizing 带区 prefect，以实现特别的艺术。</span><span class="sxs-lookup"><span data-stu-id="5d58c-187">Its sheer size and mesmerizing bands of turbulence and cloud dynamics are prefect for special artistic attention.</span></span>

### <a name="geometry-and-meshes"></a><span data-ttu-id="5d58c-188">几何图形和网格</span><span class="sxs-lookup"><span data-stu-id="5d58c-188">Geometry and meshes</span></span>

<span data-ttu-id="5d58c-189">作为一气体，木星的外部 shell 包含 gaseous 层。</span><span class="sxs-lookup"><span data-stu-id="5d58c-189">As a gas giant, Jupiter's outer shells consists of gaseous layers.</span></span> <span data-ttu-id="5d58c-190">它的快速旋转速度、内部热交换和 Coriolis 强制的结合会创建色彩丰富的层和流，并将其形成 swirling cloud 皮带和 vortices。</span><span class="sxs-lookup"><span data-stu-id="5d58c-190">The combination of its fast rotational speed, inner heat exchange, and Coriolis forces creates colorful layers and streams that form into swirling cloud belts and vortices.</span></span> <span data-ttu-id="5d58c-191">捕获这个非常复杂的美式是创建太阳系的关键所在。</span><span class="sxs-lookup"><span data-stu-id="5d58c-191">Capturing this intricate beauty was key in creating our solar system.</span></span>

<span data-ttu-id="5d58c-192">很显然，使用流畅的技术（如流体模拟）和带预计算流的动画纹理就没有问题。</span><span class="sxs-lookup"><span data-stu-id="5d58c-192">It was immediately clear that using visualizing techniques like fluid simulations and animated textures with precomputed streams were out of question.</span></span> <span data-ttu-id="5d58c-193">将此方法与其他任何情况同时进行模拟所需的计算能力会对性能产生重大的不利影响。</span><span class="sxs-lookup"><span data-stu-id="5d58c-193">The computing power required to simulate this in combination with everything else happening simultaneously would have had significant detrimental impacts on performance.</span></span> 

![木星对象概述](images/ge-update-jupiter-shells-complete.jpg)

<span data-ttu-id="5d58c-195">接下来的一种方法是 "冒烟和镜像" 解决方案，其中包括覆盖透明的纹理层，每个层都有一个用于处理旋转网格的组合的特定方面。</span><span class="sxs-lookup"><span data-stu-id="5d58c-195">The next approach was a 'smoke-and-mirror' solution, consisting of overlaying transparent texture layers, each of which addressed a specific aspect of the atmospheric movement, compiled on a composition of rotating meshes.</span></span>

<span data-ttu-id="5d58c-196">在下图中，可以在左侧看到内部外壳。</span><span class="sxs-lookup"><span data-stu-id="5d58c-196">In the image below, you can see the inner shell on the left.</span></span> <span data-ttu-id="5d58c-197">此材料层为组合提供了背景，以防止在构成云的多层之间出现任何小的间隙。</span><span class="sxs-lookup"><span data-stu-id="5d58c-197">This mat layer provided a background to the composition to guard against any small gaps between the multiple layers that made up the clouds.</span></span> <span data-ttu-id="5d58c-198">由于层的缓慢旋转，它还在更快速的移动带之间提供可视缓冲区，以帮助在各个层上构建视觉对象。</span><span class="sxs-lookup"><span data-stu-id="5d58c-198">Because of the layer's slow rotation, it also served as a visual buffer between the faster moving bands to help build visual unity throughout the layers.</span></span>

<span data-ttu-id="5d58c-199">将此定位点设置到模型后，移动云层随后会投影到下面所示的中间和右侧网格上。</span><span class="sxs-lookup"><span data-stu-id="5d58c-199">After setting this anchor to the model, the moving cloud layers were then projected on the middle and right meshes seen below.</span></span>

![带分隔 shell 的木星对象概述](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a><span data-ttu-id="5d58c-201">绘制</span><span class="sxs-lookup"><span data-stu-id="5d58c-201">Texturing</span></span>

<span data-ttu-id="5d58c-202">现有纹理被分为三部分纹理阿特拉斯：上部的第三个主机是 motionless 层，其中包含间距以提供视差效果，中间部分包含快速移动的外部流，第三部分包含慢速旋转内部基底层。</span><span class="sxs-lookup"><span data-stu-id="5d58c-202">The existing texture was separated into a three-part texture atlas: The upper third hosts a motionless layer of clouds with gaps to provide a parallax effect, the middle section contains the fast moving outer streams, and the lower third contains a slowly rotating inner base layer.</span></span>

<span data-ttu-id="5d58c-203">特征很棒的红点还分成了不同的移动部件，并将其插入到其他不可见的纹理区域中。</span><span class="sxs-lookup"><span data-stu-id="5d58c-203">The characteristic Great Red Spot was also separated into its various moving parts and then inserted into an otherwise invisible area of the texture.</span></span> <span data-ttu-id="5d58c-204">可以在下图的中间部分中将这些组件看作 toned speckles。</span><span class="sxs-lookup"><span data-stu-id="5d58c-204">These components can be seen as the red-toned speckles in the middle section of the image below.</span></span>

<span data-ttu-id="5d58c-205">由于每个带区都有特定的方向和速度，因此纹理分别应用于每个网格。</span><span class="sxs-lookup"><span data-stu-id="5d58c-205">Because each band has a specific direction and speed, the texture was applied to each mesh individually.</span></span> <span data-ttu-id="5d58c-206">然后，这些网格具有一个公共中心点和一个透视点，这使得 concentrically 可以对整个表面进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="5d58c-206">The meshes then had a common center and pivot point, which made it possible to concentrically animate the whole surface.</span></span>

![木星纹理概述](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a><span data-ttu-id="5d58c-208">旋转和纹理行为</span><span class="sxs-lookup"><span data-stu-id="5d58c-208">Rotation and texture behavior</span></span>

<span data-ttu-id="5d58c-209">设置好木星的视觉组合后，需要确保正确计算和应用旋转和轨道速度。</span><span class="sxs-lookup"><span data-stu-id="5d58c-209">Once the the visual composition of Jupiter was set, we needed to ensure the rotation and orbit speeds were properly calculated and applied accordingly.</span></span> <span data-ttu-id="5d58c-210">木星大约需要9小时才能完成完整的旋转。</span><span class="sxs-lookup"><span data-stu-id="5d58c-210">It takes roughly 9 hours for Jupiter to complete a full rotation.</span></span> <span data-ttu-id="5d58c-211">由于其差异旋转，这是一个定义。</span><span class="sxs-lookup"><span data-stu-id="5d58c-211">This is a matter of definition due to its Differential Rotation.</span></span> <span data-ttu-id="5d58c-212">因此，赤道几内亚流已设置为 "主流"，采用3600帧进行完全旋转。</span><span class="sxs-lookup"><span data-stu-id="5d58c-212">Therefore the equatorial stream has been set as a 'master stream', taking 3600 frames for a full rotation.</span></span> <span data-ttu-id="5d58c-213">每个其他层都需要将旋转速度提高为3600，以匹配其初始位置，例如，600、900、1200、1800等。</span><span class="sxs-lookup"><span data-stu-id="5d58c-213">Every other layer needed to have a rotational speed as a factor of 3600 in order to match its initial position, allowing, e.g.,  600, 900, 1200, 1800 etc.</span></span>

![木星 shell 纹理](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a><span data-ttu-id="5d58c-215">很棒的红点</span><span class="sxs-lookup"><span data-stu-id="5d58c-215">The Great Red Spot</span></span>

<span data-ttu-id="5d58c-216">单独旋转的流提供了良好的视觉印象，但当观察到关闭范围时，会详细说明。</span><span class="sxs-lookup"><span data-stu-id="5d58c-216">The individually rotating streams provided a good visual impression, but lacked in detail when observed at close range.</span></span>

<span data-ttu-id="5d58c-217">最引人注目的部分是木星的好红点，因此我们创建了一组专门用于展示它的网格和纹理。</span><span class="sxs-lookup"><span data-stu-id="5d58c-217">The most eye-catching part was Jupiter's Great Red Spot, so we created a set of meshes and textures specifically to showcase it.</span></span>
 
<span data-ttu-id="5d58c-218">我们使用了类似于木星带区的一种机制：一组旋转部分彼此组合在一起，同时在其 "主要层" 下进行分组，以确保无论 rest 移动的速度如何，它们都保持不变。</span><span class="sxs-lookup"><span data-stu-id="5d58c-218">We used a similar mechanism as with Jupiter's bands: a set of rotating parts was composed on top of each other, while also being grouped under its 'master layer' to ensure they remain in position no matter how fast the rest moves.</span></span>

<span data-ttu-id="5d58c-219">当网格设置好后，应用了激烈 vortex 的不同层，并且每个光盘随后进行了动画处理，中心部分的移动速度最快，并且随着它向外移动时，rest 会逐渐下降。</span><span class="sxs-lookup"><span data-stu-id="5d58c-219">When the meshes were set up and in place, different layers of the stormy vortex were applied and each disc was then animated individually, the center pieces moving fastest, with the rest progressively slowing down as it moving outwards.</span></span>

![木星优秀 Red 点网格](images/ge-update-great-red-spot-mesh.jpg)

<span data-ttu-id="5d58c-221">该组合也具有与每个其他网格相同的透视，同时还保持其从其原始 y 轴倾斜 (！ ) ，以允许自由地对旋转进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="5d58c-221">The composition also had the same pivot as every other mesh, while also keeping its tilt from its original y-axis (!) to allow freedom in animating the rotation.</span></span> <span data-ttu-id="5d58c-222">3600帧是基本速率，每一层的系数为一段旋转。</span><span class="sxs-lookup"><span data-stu-id="5d58c-222">3600 frames is the base rate, with each layer having a factor of this as a period of rotation.</span></span>

![木星极红点纹理](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a><span data-ttu-id="5d58c-224">直接在 Unity 中获取</span><span class="sxs-lookup"><span data-stu-id="5d58c-224">Getting it right in Unity</span></span>

<span data-ttu-id="5d58c-225">在 Unity 中实现此功能时，需要记住几个关键事项。</span><span class="sxs-lookup"><span data-stu-id="5d58c-225">There are a couple of key things to keep in mind when implementing this in Unity.</span></span>

<span data-ttu-id="5d58c-226">当处理大型透明层集时，Unity 很容易混淆。</span><span class="sxs-lookup"><span data-stu-id="5d58c-226">Unity is easily confused when dealing with large sets of transparent layers.</span></span> <span data-ttu-id="5d58c-227">解决方法是复制每个网格的纹理材料，并对每个材料以5为递增的方式应用升序的渲染器队列值。</span><span class="sxs-lookup"><span data-stu-id="5d58c-227">The solution was to duplicate the texture material for each mesh and apply ascending Render Queue values progressively from the inner to the outer by 5 to each material.</span></span>

<span data-ttu-id="5d58c-228">结果是，内部 shell 的 Render Queue 值为 3000 (默认值为) ，toned 外部的静态外边缘的值为3005，而 fast 白色的外部云则为3010。</span><span class="sxs-lookup"><span data-stu-id="5d58c-228">The result was the inner shell had a Render Queue value of 3000 (default), the static red-toned outer later had a value of 3005, the fast white outer clouds had 3010.</span></span> <span data-ttu-id="5d58c-229"> (从内部层到外部层) 的良好的红色点在此模型中的值为3025。</span><span class="sxs-lookup"><span data-stu-id="5d58c-229">The Great Red Spot (progressing from inner to outer layer), finished with a value of 3025 in this model.</span></span>

![木星最终对象](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a><span data-ttu-id="5d58c-231">最后的处理</span><span class="sxs-lookup"><span data-stu-id="5d58c-231">Final touches</span></span>

<span data-ttu-id="5d58c-232">首次设置带纹理的木星层，证明该层不足以实现实现。</span><span class="sxs-lookup"><span data-stu-id="5d58c-232">The textured Jupiter layers were set up at first, which proved to be insufficient for implementation.</span></span>

<span data-ttu-id="5d58c-233">原来的行星标准着色器及其所有变体通过脚本（SunLightReceiver，MRTK 标准着色器不支持）接收其照明信息。</span><span class="sxs-lookup"><span data-stu-id="5d58c-233">The original Planet Standard shader, and all of its variations, receive their lighting information via a script, the SunLightReceiver, which is not supported by the MRTK Standard shader.</span></span>

<span data-ttu-id="5d58c-234">只需交换着色器并不是一种解决方案，因为行星标准着色器不支持带有透明胶片的纹理地图。</span><span class="sxs-lookup"><span data-stu-id="5d58c-234">Simply swapping the shaders wasn't a solution because the Planet Standard shader doesn't support texture maps with transparencies.</span></span> <span data-ttu-id="5d58c-235">我们编辑了此着色器，使木星生成按预期方式工作。</span><span class="sxs-lookup"><span data-stu-id="5d58c-235">We edited this shader to make the Jupiter build work as intended.</span></span>

<span data-ttu-id="5d58c-236">最后，需要设置 Alpha 混合，方法是将源 Blend 设置为10，将目标混合设置为5。</span><span class="sxs-lookup"><span data-stu-id="5d58c-236">Finally, the Alpha Blends needed to be set up by setting the Source Blend to 10 and the Destination Blend to 5.</span></span>

![木星 Unity 属性](images/ge-update-jupiter-unity-render-queue.jpg)

<span data-ttu-id="5d58c-238">可以在 Galaxy 资源管理器中查看木星的最终呈现！</span><span class="sxs-lookup"><span data-stu-id="5d58c-238">You can see the final rendering of Jupiter in Galaxy Explorer!</span></span>

## <a name="meet-the-team"></a><span data-ttu-id="5d58c-239">认识团队</span><span class="sxs-lookup"><span data-stu-id="5d58c-239">Meet the team</span></span> 

<span data-ttu-id="5d58c-240">混合现实工作室团队由设计人员、三维音乐家、用户专家、开发人员、项目经理和工作室主管组成。</span><span class="sxs-lookup"><span data-stu-id="5d58c-240">Our Mixed Reality studio team is made up of designers, 3D artists, UX specialists, developers, a program manager, and a studio head.</span></span> <span data-ttu-id="5d58c-241">我们遍布世界各地的 hail：华南、加拿大、德国、以色列、日本、英国和美国。</span><span class="sxs-lookup"><span data-stu-id="5d58c-241">We hail from all over the world: Belgium, Canada, Germany, Israel, Japan, the United Kingdom, and the United States.</span></span> <span data-ttu-id="5d58c-242">我们是一位丰富的团队，来自于不同的背景：游戏-传统和独立、数字营销、卫生保健和科学。</span><span class="sxs-lookup"><span data-stu-id="5d58c-242">We're a multidisciplinary team that comes from a diverse background: gaming - both traditional and indie, digital marketing, health care and science.</span></span>

<span data-ttu-id="5d58c-243">我们很高兴为 HoloLens 2 创建 Galaxy 资源管理器，并更新 HoloLens (第一代) 、VR 和桌面版本。</span><span class="sxs-lookup"><span data-stu-id="5d58c-243">We're excited to create Galaxy Explorer for HoloLens 2, and to update the HoloLens (first gen), VR, and desktop versions.</span></span> 

![Galaxy 资源管理器团队](images/ge-update-team-image.png)

<span data-ttu-id="5d58c-245">从左到右： Artemis Tsouflidou (开发人员) 、Angie Teickner (可视化设计器) 、David Janer (UX 设计器) 、刘娜 Garrett (交付 & 生产主管) 、Yasushi Zonno (创造性潜在客户) 、Eline Ledent (开发人员) 和 Ben Turner (Sr-1a) 。</span><span class="sxs-lookup"><span data-stu-id="5d58c-245">On top from left to right: Artemis Tsouflidou (Developer), Angie Teickner (Visual Designer), David Janer (UX Designer), Laura Garrett (Delivery & Production Lead), Yasushi Zonno (Creative Lead), Eline Ledent (Developer), and Ben Turner (Sr. Developer).</span></span>
<span data-ttu-id="5d58c-246">从左到右： Amit Rojtblat (技术艺术家) ，圣马丁 Wettig (3D 艺术家) ，Dirk Songuer (Studio Head) 。</span><span class="sxs-lookup"><span data-stu-id="5d58c-246">Bottom from left to right: Amit Rojtblat (Technical Artist), Martin Wettig (3D Artist), and Dirk Songuer (Studio Head).</span></span>
<span data-ttu-id="5d58c-247">不重要： Tim Gerken (技术组长) 和 Oscar Salandin (可视化设计器) 。</span><span class="sxs-lookup"><span data-stu-id="5d58c-247">Not featured: Tim Gerken (Tech Lead) and Oscar Salandin (Visual Designer).</span></span>

## <a name="additional-information"></a><span data-ttu-id="5d58c-248">其他信息</span><span class="sxs-lookup"><span data-stu-id="5d58c-248">Additional information</span></span>

### <a name="mixed-reality-studios"></a><span data-ttu-id="5d58c-249">混合现实工作室</span><span class="sxs-lookup"><span data-stu-id="5d58c-249">Mixed Reality Studios</span></span>

<span data-ttu-id="5d58c-250">Microsoft 混合现实工作室团队-位于美洲、欧洲和 Asia-Pacific 中，是用户体验设计、全息计算、AR/VR 技术和三维开发方面的专家;包括3D 资产创建、DirectX、Unity 和 Unreal。</span><span class="sxs-lookup"><span data-stu-id="5d58c-250">Microsoft Mixed Reality Studio teams - located in the Americas, Europe, and Asia-Pacific - are experts in user experience design, holographic computing, AR/VR technologies, and 3D development; including 3D asset creation, DirectX, Unity and Unreal.</span></span> <span data-ttu-id="5d58c-251">我们帮助构想预期的先期备货、设计、构建和交付解决方案，同时使客户能够在其组织中创造实实在在的影响。</span><span class="sxs-lookup"><span data-stu-id="5d58c-251">We help envision desired futures, design, build and deliver solutions, while enabling customers to create measurable impact across their organization.</span></span> <span data-ttu-id="5d58c-252">录音室与超过22000个 Microsoft 服务专业人员密切合作，以实现企业应用程序集成、采用、操作和支持。</span><span class="sxs-lookup"><span data-stu-id="5d58c-252">The studios work closely with over 22,000 Microsoft Services professionals for enterprise application integration, adoption, operations, and support.</span></span>
