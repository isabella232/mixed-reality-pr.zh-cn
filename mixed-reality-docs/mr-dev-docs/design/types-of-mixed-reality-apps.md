---
title: 混合现实应用的类型
description: 了解混合现实平台可支持的各种经验，从完全的沉浸式环境到用户当前环境的轻型信息分层。
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计，应用模式，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens
ms.openlocfilehash: 8c9a051ff0b80461fe590efa37593bddb01c0e63
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848100"
---
# <a name="types-of-mixed-reality-apps"></a><span data-ttu-id="5dee2-104">混合现实应用的类型</span><span class="sxs-lookup"><span data-stu-id="5dee2-104">Types of mixed reality apps</span></span>

<span data-ttu-id="5dee2-105">开发 Windows Mixed Reality 应用的优点之一是平台可以支持的体验。</span><span class="sxs-lookup"><span data-stu-id="5dee2-105">One of the advantages of developing apps for Windows Mixed Reality is the spectrum of experiences the platform can support.</span></span> <span data-ttu-id="5dee2-106">从完全沉浸式的虚拟环境到用户当前环境中的光线信息分层，Windows Mixed Reality 提供了一组强大的工具，可将任何体验引入到生活中。</span><span class="sxs-lookup"><span data-stu-id="5dee2-106">From fully immersive, virtual environments, to light information layering over a user’s current environment, Windows Mixed Reality provides a robust set of tools to bring any experience to life.</span></span> <span data-ttu-id="5dee2-107">对于应用程序开发人员而言，在开发过程中及早了解其体验的位置，这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="5dee2-107">It's important for an app maker to understand early in their development process as to where along this spectrum their experience lies.</span></span> <span data-ttu-id="5dee2-108">此决定最终会影响应用设计的构成和开发的技术路径。</span><span class="sxs-lookup"><span data-stu-id="5dee2-108">This decision will ultimately impact both the app design makeup and the technological path for development.</span></span>

## <a name="enhanced-environment-apps-hololens-only"></a><span data-ttu-id="5dee2-109">增强的环境应用 (仅 HoloLens) </span><span class="sxs-lookup"><span data-stu-id="5dee2-109">Enhanced environment apps (HoloLens only)</span></span>

<span data-ttu-id="5dee2-110">混合现实可以带来价值的最强大的方式之一是让开发人员在用户的当前环境中设置数字信息或内容。</span><span class="sxs-lookup"><span data-stu-id="5dee2-110">One of the most powerful ways that mixed reality can bring value is letting developers place digital information or content in a user’s current environment.</span></span> <span data-ttu-id="5dee2-111">这种方法非常适用于现实世界中的数字内容的上下文位置至关重要的应用程序，在其体验过程中使用户的实际环境 "存在" 成为至关重要的。</span><span class="sxs-lookup"><span data-stu-id="5dee2-111">This approach is popular for apps where the contextual placement of digital content in the real world is paramount and keeping the user’s real world environment “present” during their experience is key.</span></span> <span data-ttu-id="5dee2-112">用户还可以轻松地在实际数字任务之间移动。</span><span class="sxs-lookup"><span data-stu-id="5dee2-112">Users can also move between real world digital tasks with ease.</span></span> <span data-ttu-id="5dee2-113">这使用户看到的混合现实应用确实成为其环境的一部分，因此更信任。</span><span class="sxs-lookup"><span data-stu-id="5dee2-113">This lends even more credence to the promise that the mixed reality apps the user sees are truly a part of their environment.</span></span>

<span data-ttu-id="5dee2-114">![增强的环境应用](images/enhancedenvironmentapps-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="5dee2-114">![Enhanced environment apps](images/enhancedenvironmentapps-640px.jpg)</span></span><br>
<span data-ttu-id="5dee2-115">*增强的环境应用*</span><span class="sxs-lookup"><span data-stu-id="5dee2-115">*Enhanced environment apps*</span></span>

<span data-ttu-id="5dee2-116">**示例使用**</span><span class="sxs-lookup"><span data-stu-id="5dee2-116">**Example uses**</span></span>
* <span data-ttu-id="5dee2-117">混合现实记事本样式应用，允许用户创建笔记并将其放置在其环境中</span><span class="sxs-lookup"><span data-stu-id="5dee2-117">A mixed reality notepad style app that allows users to create and place notes around their environment</span></span>
* <span data-ttu-id="5dee2-118">将混合现实电视应用置于舒适的位置以供观看</span><span class="sxs-lookup"><span data-stu-id="5dee2-118">A mixed reality television app placed in a comfortable spot for viewing</span></span>
* <span data-ttu-id="5dee2-119">放置在厨房岛之上的混合现实烹饪应用可帮助你的烹饪任务</span><span class="sxs-lookup"><span data-stu-id="5dee2-119">A mixed reality cooking app placed above the kitchen island to help a cooking task</span></span>
* <span data-ttu-id="5dee2-120">一种混合现实应用，为用户提供 "x 光线愿景" (也就是说，放置在上并模拟真实世界对象的一个全息图，同时允许用户查看 "内部 it" holographically) </span><span class="sxs-lookup"><span data-stu-id="5dee2-120">A mixed reality app that gives users the feeling of “x-ray vision” (that is, a hologram placed on top of and mimics a real world object, while allowing the user to see “inside it” holographically)</span></span>
* <span data-ttu-id="5dee2-121">混合现实批注放置在工厂中，用于为辅助角色指定必要的信息</span><span class="sxs-lookup"><span data-stu-id="5dee2-121">Mixed reality annotations placed throughout a factory to give worker’s necessary information</span></span>
* <span data-ttu-id="5dee2-122">在办公室空间中寻找混合现实方式</span><span class="sxs-lookup"><span data-stu-id="5dee2-122">Mixed reality way finding in an office space</span></span>
* <span data-ttu-id="5dee2-123">混合现实 tabletop 体验 (也就是说，棋盘游戏样式体验) </span><span class="sxs-lookup"><span data-stu-id="5dee2-123">Mixed reality tabletop experiences (that is, board game style experiences)</span></span>
* <span data-ttu-id="5dee2-124">混合现实通信应用，如 Skype</span><span class="sxs-lookup"><span data-stu-id="5dee2-124">Mixed reality communication apps like Skype</span></span>

## <a name="blended-environment-apps"></a><span data-ttu-id="5dee2-125">混合环境应用</span><span class="sxs-lookup"><span data-stu-id="5dee2-125">Blended environment apps</span></span>

<span data-ttu-id="5dee2-126">鉴于 Windows Mixed Reality 识别和映射用户环境的能力，它可以创建可在用户的空间上重叠的数字层。</span><span class="sxs-lookup"><span data-stu-id="5dee2-126">Given Windows Mixed Reality’s ability to recognize and map the user's environment, it's able to create a digital layer that can be overlaid on the user’s space.</span></span> <span data-ttu-id="5dee2-127">精简层会考虑用户环境的形状和边界，但是应用程序可能会选择转换最适合从而深入了解应用程序中用户的某些元素。</span><span class="sxs-lookup"><span data-stu-id="5dee2-127">Thin layer respects the shape and boundaries of the user’s environment, but the app may choose to transform certain elements best suited to immerse the user in the app.</span></span> <span data-ttu-id="5dee2-128">这称为混合环境应用。</span><span class="sxs-lookup"><span data-stu-id="5dee2-128">This is called a blended environment app.</span></span> <span data-ttu-id="5dee2-129">与增强的环境应用不同，混合环境应用程序可能只关心环境，以最好地使用其构成来鼓励特定的用户行为 (例如鼓励移动或浏览) ，或通过将元素替换为 (厨房计数器的更改来显示不同的平铺) 模式。</span><span class="sxs-lookup"><span data-stu-id="5dee2-129">Unlike an enhanced environment app, blended environment apps may only care enough about the environment to best use its makeup for encouraging specific user behavior (like encouraging movement or exploration) or by replacing elements with changes (a kitchen counter is skinned to show a different tile pattern).</span></span> <span data-ttu-id="5dee2-130">这种体验甚至可能会将元素转换为完全不同的对象，但仍会将对象的大致尺寸保持为其基本 (厨房岛会转换为犯罪 thriller 游戏) 的转储程序。</span><span class="sxs-lookup"><span data-stu-id="5dee2-130">This type of experience may even transform an element into an entirely different object, but still keep the rough dimensions of the object as its base (a kitchen island is transformed into a dumpster for a crime thriller game).</span></span>

<span data-ttu-id="5dee2-131">![混合环境应用](images/blendedenvironmentapps-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="5dee2-131">![Blended environment apps](images/blendedenvironmentapps-640px.jpg)</span></span><br>
<span data-ttu-id="5dee2-132">*混合环境应用*</span><span class="sxs-lookup"><span data-stu-id="5dee2-132">*Blended environment apps*</span></span>

<span data-ttu-id="5dee2-133">**示例使用**</span><span class="sxs-lookup"><span data-stu-id="5dee2-133">**Example uses**</span></span>
* <span data-ttu-id="5dee2-134">混合现实内部设计应用，可使用不同的颜色和模式绘制墙壁、countertops 或地面</span><span class="sxs-lookup"><span data-stu-id="5dee2-134">A mixed reality interior design app that can paint walls, countertops, or floors in different colors and patterns</span></span>
* <span data-ttu-id="5dee2-135">一种混合现实应用，允许汽车设计器将新的设计迭代置于现有汽车顶层的即将到来的汽车刷新之上</span><span class="sxs-lookup"><span data-stu-id="5dee2-135">A mixed reality app that allows an automotive designer to layer new design iterations for an upcoming car refresh on top of an existing car</span></span>
* <span data-ttu-id="5dee2-136">床已 "覆盖"，由儿童游戏中的混合现实水果支架替换</span><span class="sxs-lookup"><span data-stu-id="5dee2-136">A bed is “covered” and replaced by a mixed reality fruit stand in children’s game</span></span>
* <span data-ttu-id="5dee2-137">在犯罪 thriller 游戏中，桌面被 "覆盖" 并替换为混合现实转储程序</span><span class="sxs-lookup"><span data-stu-id="5dee2-137">A desk is “covered” and replaced with a mixed reality dumpster in a crime thriller game</span></span>
* <span data-ttu-id="5dee2-138">使用大致相同的形状和尺寸 "覆盖" 了悬挂灯笼并将其替换为 signpost</span><span class="sxs-lookup"><span data-stu-id="5dee2-138">A hanging lantern is “covered” and replaced with signpost using roughly the same shape and dimension</span></span>
* <span data-ttu-id="5dee2-139">一种应用，它允许用户在其真实或沉浸式世界中冲击孔洞，这会显示神奇世界</span><span class="sxs-lookup"><span data-stu-id="5dee2-139">An app that allows users to blast holes in their real or immersive world walls, which reveal a magical world</span></span>

## <a name="immersive-environment-apps"></a><span data-ttu-id="5dee2-140">沉浸式环境应用</span><span class="sxs-lookup"><span data-stu-id="5dee2-140">Immersive environment apps</span></span>

<span data-ttu-id="5dee2-141">沉浸式环境应用以完全更改用户世界的环境为中心，并可将其置于不同的时间和空间。</span><span class="sxs-lookup"><span data-stu-id="5dee2-141">Immersive environment apps are centered around an environment that completely changes the user’s world and can place them in a different time and space.</span></span> <span data-ttu-id="5dee2-142">这些环境非常真实，只是创建了沉浸式和 thrilling 的体验，只受应用程序创建者想像的限制。</span><span class="sxs-lookup"><span data-stu-id="5dee2-142">These environments can feel real, creating immersive and thrilling experiences that are only limited by the app creator’s imagination.</span></span> <span data-ttu-id="5dee2-143">与混合环境应用不同，一旦 Windows Mixed Reality 标识用户的空间，沉浸式环境应用可能会完全忽略用户的当前环境，并将其替换为自己的整个股票。</span><span class="sxs-lookup"><span data-stu-id="5dee2-143">Unlike blended environment apps, once Windows Mixed Reality identifies the user’s space, an immersive environment app may totally disregard the user’s current environment and replace it whole stock with one of its own.</span></span> <span data-ttu-id="5dee2-144">这些体验还可以分隔时间和空间，这意味着用户可以在一种沉浸式体验中走上罗马</span><span class="sxs-lookup"><span data-stu-id="5dee2-144">These experiences may also separate time and space, meaning a user could walk the streets of Rome in an immersive experience, while remaining relatively still in their real world space.</span></span> <span data-ttu-id="5dee2-145">实际环境的上下文对于沉浸式环境应用可能并不重要。</span><span class="sxs-lookup"><span data-stu-id="5dee2-145">Context of the real world environment may not be important to an immersive environment app.</span></span>

<span data-ttu-id="5dee2-146">![沉浸式环境应用](images/windows-mixed-reality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="5dee2-146">![Immersive environment apps](images/windows-mixed-reality-640px.jpg)</span></span><br>
<span data-ttu-id="5dee2-147">*沉浸式环境应用*</span><span class="sxs-lookup"><span data-stu-id="5dee2-147">*Immersive environment apps*</span></span>

<span data-ttu-id="5dee2-148">**示例使用**</span><span class="sxs-lookup"><span data-stu-id="5dee2-148">**Example uses**</span></span>
* <span data-ttu-id="5dee2-149">一个沉浸式应用，使用户能够浏览与他们自己的 (不同的空间，即演练一座著名的大楼、博物馆、受欢迎的城市) </span><span class="sxs-lookup"><span data-stu-id="5dee2-149">An immersive app that lets a user tour a space separate from their own (that is, walk through a famous building, museum, popular city)</span></span>
* <span data-ttu-id="5dee2-150">一个沉浸式应用，用于协调用户 (的活动或方案，即一种工作或性能) </span><span class="sxs-lookup"><span data-stu-id="5dee2-150">An immersive app that orchestrates an event or scenario around the user (that is, a battle or a performance)</span></span>

## <a name="see-also"></a><span data-ttu-id="5dee2-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5dee2-151">See also</span></span>

* [<span data-ttu-id="5dee2-152">开发概述</span><span class="sxs-lookup"><span data-stu-id="5dee2-152">Development overview</span></span>](../develop/development.md)
* [<span data-ttu-id="5dee2-153">应用模型</span><span class="sxs-lookup"><span data-stu-id="5dee2-153">App model</span></span>](app-model.md)
* [<span data-ttu-id="5dee2-154">应用视图</span><span class="sxs-lookup"><span data-stu-id="5dee2-154">App views</span></span>](app-views.md)
