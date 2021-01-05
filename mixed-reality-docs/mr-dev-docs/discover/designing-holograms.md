---
title: 设计全息影像
description: 通过 Microsoft 的新设计全息影像应用程序了解混合现实。
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK，混合现实工具包，全息影像，设计全息影像，学习，示例应用，混合现实耳机，虚拟现实耳机，什么是虚拟现实
ms.openlocfilehash: 2480b5e0b4dca502c746dad6f070226ffa8cd1f9
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757755"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="4fb06-104">设计全息影像的过程</span><span class="sxs-lookup"><span data-stu-id="4fb06-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="4fb06-105">请在此页上为所有的冷 Gif 和嵌入视频提供小的加载窗口。</span><span class="sxs-lookup"><span data-stu-id="4fb06-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="4fb06-106">了解如何设计混合现实很难，因为介质并不一定能顺利地转换为2D 设计过程。</span><span class="sxs-lookup"><span data-stu-id="4fb06-106">Learning how to design for mixed reality can be hard because the medium doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="4fb06-107">在 Microsoft，我们为 HoloLens 2 创建了免费应用，帮助你了解混合现实 UX 设计亲身的基础知识。</span><span class="sxs-lookup"><span data-stu-id="4fb06-107">Here at Microsoft, we've created a free app for the HoloLens 2 to help you learn the fundamentals of mixed reality UX Design firsthand.</span></span> <span data-ttu-id="4fb06-108">设计全息影像应用程序的独特方法深入混合现实行为、提示和建议，帮助你创建自己的富有吸引力的、令人惊叹的 HoloLens 应用。</span><span class="sxs-lookup"><span data-stu-id="4fb06-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="4fb06-109">从 Microsoft Store 免费下载应用，并从 Microsoft 混合现实设计团队那里了解！</span><span class="sxs-lookup"><span data-stu-id="4fb06-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4fb06-110">下载设计全息影像应用</span><span class="sxs-lookup"><span data-stu-id="4fb06-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![设计全息图的演示房间中标题跟踪场景的动画 GIF](images/designing-holograms/demo-room.gif)

<span data-ttu-id="4fb06-112">*设计全息图的演示房间 (也称为娃房子)*</span><span class="sxs-lookup"><span data-stu-id="4fb06-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="4fb06-113">混合现实设计</span><span class="sxs-lookup"><span data-stu-id="4fb06-113">Designing for mixed reality</span></span>

<span data-ttu-id="4fb06-114">与许多人一样，我使用的是设计移动应用。</span><span class="sxs-lookup"><span data-stu-id="4fb06-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="4fb06-115">从2D 设计世界来，跳转到空间计算的完整，其中一切现在都在世界中，这是一项重大转变。</span><span class="sxs-lookup"><span data-stu-id="4fb06-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="4fb06-116">在混合现实中，应用不再局限于2D 屏幕;事实上，它们几乎是免费的，放在现实世界中，并与真实对象进行交互。</span><span class="sxs-lookup"><span data-stu-id="4fb06-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="4fb06-117">对于我来说，将3D 体验连接到传统的2D 设计过程是混合现实开发的最具挑战性的方面。</span><span class="sxs-lookup"><span data-stu-id="4fb06-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="4fb06-118">在与客户的对话中，我知道 "我知道要包含哪些功能以及如何让它们启动并运行"。</span><span class="sxs-lookup"><span data-stu-id="4fb06-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="4fb06-119">就是代码，我可以按照文档和教程操作，而是在用户体验方面？</span><span class="sxs-lookup"><span data-stu-id="4fb06-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="4fb06-120">如此多的功能、不同的输入选项、不同的方案和物理环境，这一点很惊人。</span><span class="sxs-lookup"><span data-stu-id="4fb06-120">So many features, different input options, different scenarios, and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="4fb06-121">![从圣马力诺2中的 HoloLens 2 设计研讨会开始的图像，位于旧金山 ](images/designing-holograms/workshop.jpeg)
 *2 的 Hololens 2 设计研讨会* 中</span><span class="sxs-lookup"><span data-stu-id="4fb06-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="4fb06-122">机会</span><span class="sxs-lookup"><span data-stu-id="4fb06-122">An opportunity to teach</span></span>

<span data-ttu-id="4fb06-123">这并不是很明显，但会出现一个极好的机会，将混合现实用作一种用于教授的媒介。</span><span class="sxs-lookup"><span data-stu-id="4fb06-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="4fb06-124">设计全息影像是介绍混合现实设计概念和建议的视觉体验。</span><span class="sxs-lookup"><span data-stu-id="4fb06-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="4fb06-125">这只是你以及演示混合现实设计概念的虚拟老师。</span><span class="sxs-lookup"><span data-stu-id="4fb06-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="4fb06-126">一切都是从第三人的角度来看，它在自己的空间中实现了丰富的体验。</span><span class="sxs-lookup"><span data-stu-id="4fb06-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="4fb06-127">*设计全息影像尾端视频*</span><span class="sxs-lookup"><span data-stu-id="4fb06-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="4fb06-128">探索娃房子</span><span class="sxs-lookup"><span data-stu-id="4fb06-128">Exploring the doll house</span></span>

<span data-ttu-id="4fb06-129">娃房子是我们在整个应用程序中使用的虚拟环境。</span><span class="sxs-lookup"><span data-stu-id="4fb06-129">The doll house is the virtual environment we use throughout the app.</span></span> <span data-ttu-id="4fb06-130">环境为 80 x 60 x 40-cm，其中包含大多数房间共有的基本元素，如墙壁、灯、家具、桌子和电视。</span><span class="sxs-lookup"><span data-stu-id="4fb06-130">The environment is an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="4fb06-131">娃房子是应用程序体验的主要 protagonist，因此我们需要确保它在任何环境中都能正常工作。</span><span class="sxs-lookup"><span data-stu-id="4fb06-131">The doll house is the main protagonist of the app experience, so we needed to make sure it would work great in any environment.</span></span> <span data-ttu-id="4fb06-132">将其视为一个小型演示空间，用于可视化各种混合现实概念。</span><span class="sxs-lookup"><span data-stu-id="4fb06-132">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="4fb06-133">*Dollhouse 调整行为的视频*</span><span class="sxs-lookup"><span data-stu-id="4fb06-133">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="4fb06-134">1:1 与1:10 原型</span><span class="sxs-lookup"><span data-stu-id="4fb06-134">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="4fb06-135">我们最初假设，1:1 的演示会令人吃惊，几乎与查看真实的老师一样。</span><span class="sxs-lookup"><span data-stu-id="4fb06-135">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="4fb06-136">用户将看到老师在实际生活中看到的一切内容。</span><span class="sxs-lookup"><span data-stu-id="4fb06-136">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="4fb06-137">但是，我们立即意识到存在以下几个问题：</span><span class="sxs-lookup"><span data-stu-id="4fb06-137">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="4fb06-138">大多数开发人员会在办公室或比演示房间小的房间内运行应用程序，因此不适合。</span><span class="sxs-lookup"><span data-stu-id="4fb06-138">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="4fb06-139">显示是累加的，这意味着整个虚拟环境将覆盖在用户的空间上。</span><span class="sxs-lookup"><span data-stu-id="4fb06-139">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="4fb06-140">这可能会使两个表（可能为 double couches）和不对齐的墙壁产生混淆。</span><span class="sxs-lookup"><span data-stu-id="4fb06-140">That can get confusing with two tables, maybe double couches, and walls that don’t align.</span></span>
- <span data-ttu-id="4fb06-141">并且最糟糕的是，所有虚拟环境都受视图的字段约束。</span><span class="sxs-lookup"><span data-stu-id="4fb06-141">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="4fb06-142">当我们尝试使用微型1:10 刻度时，结果是一个极好的鸟瞰视图。</span><span class="sxs-lookup"><span data-stu-id="4fb06-142">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room.</span></span> <span data-ttu-id="4fb06-143">你可以从任何角度查看所有内容。</span><span class="sxs-lookup"><span data-stu-id="4fb06-143">You could see everything that was going on from any angle all at the same time.</span></span> <span data-ttu-id="4fb06-144">最令人吃惊的是，大多数测试人员发现它很多地都可以看到较小的版本，然后他们永远无法切换回1:1 规模。</span><span class="sxs-lookup"><span data-stu-id="4fb06-144">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="4fb06-145">我们决定实际会弃用1:1 版本，并避免在 UI 和应用程序的其他方面进行调整所需的额外工作。</span><span class="sxs-lookup"><span data-stu-id="4fb06-145">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="4fb06-146">![具有 ](images/designing-holograms/1-1-scale.png)
 *1:1 刻度的* 1:1 缩放字段视图的视图字段</span><span class="sxs-lookup"><span data-stu-id="4fb06-146">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="4fb06-147">![具有 ](images/designing-holograms/1-10-scale.png)
 *1:10 刻度的* 1:10 缩放字段视图的视图字段</span><span class="sxs-lookup"><span data-stu-id="4fb06-147">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="4fb06-148">使用混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="4fb06-148">Using Mixed Reality Capture</span></span>

<span data-ttu-id="4fb06-149">此应用程序的最重要特性之一是使用混合现实捕获来讲授和演示混合现实设计概念。</span><span class="sxs-lookup"><span data-stu-id="4fb06-149">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="4fb06-150">Microsoft 的 San 中有混合现实的捕获工作室。</span><span class="sxs-lookup"><span data-stu-id="4fb06-150">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="4fb06-151">Microsoft 还向其他工作室提供此技术，其中包括华盛顿特区的头像、洛杉矶、伦敦的 Dimension 工作室、首尔的 SK 电信和柏林上的 Volucap。</span><span class="sxs-lookup"><span data-stu-id="4fb06-151">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="4fb06-152">可在此处找到有关 [混合现实捕获工作室](https://www.microsoft.com/mixed-reality/capture-studios)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="4fb06-152">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="4fb06-153">*在 San 中，混合现实中的一106照相机的 Daniel Escudero 的原始胶片。*</span><span class="sxs-lookup"><span data-stu-id="4fb06-153">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="4fb06-154">捕获过程将生成一个 keyframed 的网格、法线和纹理，可将其作为 "OBJ/PNG" 文件传送，以便进一步后期生产，或准备好将其作为 "</span><span class="sxs-lookup"><span data-stu-id="4fb06-154">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="4fb06-155">这些文件可以导入到 Unity、Unreal、本机和 WebXR 项目中。</span><span class="sxs-lookup"><span data-stu-id="4fb06-155">These files can be imported into Unity, Unreal, Native, and WebXR projects.</span></span> <span data-ttu-id="4fb06-156">文件可在 Windows、iOS、Mac、Android、幻 Leap 和 Playstation VR 上运行。</span><span class="sxs-lookup"><span data-stu-id="4fb06-156">Files can run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="4fb06-157">*提供的捕获播放机用于分析包含音频和嵌入网格的视频的 mp4。*</span><span class="sxs-lookup"><span data-stu-id="4fb06-157">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="4fb06-158">操作捕获和虚拟对象</span><span class="sxs-lookup"><span data-stu-id="4fb06-158">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="4fb06-159">混合现实捕获会生成人员或动物的虚拟表示形式，但有时您可能需要这些字符与其他虚拟对象进行交互。</span><span class="sxs-lookup"><span data-stu-id="4fb06-159">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="4fb06-160">下面两个示例演示了我们处理场景以实现此效果的不同方式。</span><span class="sxs-lookup"><span data-stu-id="4fb06-160">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="4fb06-161">打印头注视调整</span><span class="sxs-lookup"><span data-stu-id="4fb06-161">Head Gaze Adjustment</span></span>

<span data-ttu-id="4fb06-162">Headgaze 调整使你可以在运行时移动已捕获人员的标题，这意味着你可以获得用户的捕获面。</span><span class="sxs-lookup"><span data-stu-id="4fb06-162">Headgaze adjustment lets you move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="4fb06-163">在我们的示例中，我们使用它来显示所需的视图和字段的字段。</span><span class="sxs-lookup"><span data-stu-id="4fb06-163">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="4fb06-164">下面是一个移动 gameobject，它作为打印头注视的目标来查看。</span><span class="sxs-lookup"><span data-stu-id="4fb06-164">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="4fb06-165">当我们将目标从一侧移到另一侧时，捕获的开头将如下所示。</span><span class="sxs-lookup"><span data-stu-id="4fb06-165">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="4fb06-166">我们使用这一技巧来确保空闲捕获始终面对存放在娃房子不同部分的全息影像。</span><span class="sxs-lookup"><span data-stu-id="4fb06-166">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![在 Unity 中的目标 gameobject 之后，在运行时移动捕获的头](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="4fb06-168">*当 Unity 中的目标 gameobject 后，将在运行时移动捕获的头。*</span><span class="sxs-lookup"><span data-stu-id="4fb06-168">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="4fb06-169">同步动画对象</span><span class="sxs-lookup"><span data-stu-id="4fb06-169">Syncing Animated Objects</span></span>

<span data-ttu-id="4fb06-170">第二个是动画处理要与捕获移动同步的对象。</span><span class="sxs-lookup"><span data-stu-id="4fb06-170">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="4fb06-171">在应用程序的不同部分，每隔五帧导入一个特定捕获的顺序 Obj。</span><span class="sxs-lookup"><span data-stu-id="4fb06-171">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="4fb06-172">然后，Obj 在场景中进行动画处理，以确保它们与捕获的相应帧匹配。</span><span class="sxs-lookup"><span data-stu-id="4fb06-172">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="4fb06-173">这是一种令人厌烦的动画处理和 keyframing 的过程，但结果很好。</span><span class="sxs-lookup"><span data-stu-id="4fb06-173">It’s a tedious process of animating and keyframing, but the result is great.</span></span> <span data-ttu-id="4fb06-174">你现在可以看到混合现实捕获与非捕获对象的交互。</span><span class="sxs-lookup"><span data-stu-id="4fb06-174">You can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![在混合现实捕获和 UI 面板之间同步动画](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="4fb06-176">*在混合现实捕获和 UI 面板之间同步动画*</span><span class="sxs-lookup"><span data-stu-id="4fb06-176">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="4fb06-177">UI 创作过程</span><span class="sxs-lookup"><span data-stu-id="4fb06-177">UI creative process</span></span>

<span data-ttu-id="4fb06-178">开始使用 UI 设计时，我们想要展示全息影像必须提供的一些神奇的做法。</span><span class="sxs-lookup"><span data-stu-id="4fb06-178">When we started the UI design, we wanted to show some of the magic and possibility that holograms have to offer.</span></span> <span data-ttu-id="4fb06-179">在三维世界中，简单地显示静态2D 窗口和文本框并不合适。</span><span class="sxs-lookup"><span data-stu-id="4fb06-179">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world.</span></span> <span data-ttu-id="4fb06-180">很多情况下不会显示，因此，从现在开始，我们决定从该位置移走，充分利用全息的3D 空间。</span><span class="sxs-lookup"><span data-stu-id="4fb06-180">Many of the possibilities at hand just don't show up, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="4fb06-181">首先，我们开始向面板、图标和文本信息添加一些粗细。</span><span class="sxs-lookup"><span data-stu-id="4fb06-181">At first, we started with adding some thickness to the panels, icons, and text information.</span></span> <span data-ttu-id="4fb06-182">而且，作为用户，我看到的是一个文本框。</span><span class="sxs-lookup"><span data-stu-id="4fb06-182">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="4fb06-183">包含图像的文本框，但不存在。</span><span class="sxs-lookup"><span data-stu-id="4fb06-183">Text boxes with images, but we aren't there.</span></span> <span data-ttu-id="4fb06-184">我们将使用混合现实工具包 (MRTK) 着色器进行进一步的介绍。</span><span class="sxs-lookup"><span data-stu-id="4fb06-184">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="4fb06-185">MRTK 着色器变成了一个功能强大的工具，并使用其模具功能向面板添加了消极的深度。</span><span class="sxs-lookup"><span data-stu-id="4fb06-185">The MRTK shaders became a powerful tool, and we made use of its stencil features to add negative depth to the panels.</span></span> <span data-ttu-id="4fb06-186">这意味着，图标现在显示在透明面板的后面，而不是在文本框前面添加元素。</span><span class="sxs-lookup"><span data-stu-id="4fb06-186">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="4fb06-187">我现在看到的是，我只是在现实世界中不能再复制，而这是一种开始使用全息幻的地方。</span><span class="sxs-lookup"><span data-stu-id="4fb06-187">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="4fb06-188">我也不是我想要阅读的，我还在现实世界中做了很多工作。</span><span class="sxs-lookup"><span data-stu-id="4fb06-188">Also as a user I don’t really like to read, I do a lot already in the physical world.</span></span>

<span data-ttu-id="4fb06-189">显然，图标的工作方式比简单文本更好，若要提供更为强大的指导，然后开始创建一组动画对象和头像，其中每个对象都告诉您在各自的方案中所执行的操作及其使用方式的一小部分。</span><span class="sxs-lookup"><span data-stu-id="4fb06-189">Obviously icons work a lot better than simple text does, to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![交互式全息菜单系统的动画 GIF](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="4fb06-191">核心概念</span><span class="sxs-lookup"><span data-stu-id="4fb06-191">Core concepts</span></span>

<span data-ttu-id="4fb06-192">**全息帧**</span><span class="sxs-lookup"><span data-stu-id="4fb06-192">**Holographic frame**</span></span>

![用户的动画 GIF，其中突出显示了全息框架的 dollhouse](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="4fb06-194">**坐标系统**</span><span class="sxs-lookup"><span data-stu-id="4fb06-194">**Coordinate systems**</span></span>

![用户使用突出显示的坐标系统围绕 dollhouse 的动画 GIF](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="4fb06-196">**眼动跟踪**</span><span class="sxs-lookup"><span data-stu-id="4fb06-196">**Eye tracking**</span></span>

![用户的动画 GIF，其中突出显示了眼睛为眼睛的静止全息影像](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="4fb06-198">**房间扫描可视化和空间映射**</span><span class="sxs-lookup"><span data-stu-id="4fb06-198">**Room scan visualization and spatial mapping**</span></span>

![要映射的 dollhouse 中的所有表面的动画 GIF](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="4fb06-200">**场景理解**</span><span class="sxs-lookup"><span data-stu-id="4fb06-200">**Scene understanding**</span></span>

![正在识别的 dollhouse 中的对象的动画 GIF](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="4fb06-202">**手动射线的点和提交**</span><span class="sxs-lookup"><span data-stu-id="4fb06-202">**Point and commit with hand rays**</span></span>

![用户的动画 GIF，其中突出显示了手 ray](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="4fb06-204">"试用"</span><span class="sxs-lookup"><span data-stu-id="4fb06-204">"Try it out" moments</span></span>

<span data-ttu-id="4fb06-205">设计全息影像会讲授混合现实概念，但它也允许您在房间内试用它们。</span><span class="sxs-lookup"><span data-stu-id="4fb06-205">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="4fb06-206">在其中一些说明后，我们将会暂停，并将您娃房子并进入互动时间。</span><span class="sxs-lookup"><span data-stu-id="4fb06-206">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="4fb06-207">下面是这些交互式对话的一些示例：</span><span class="sxs-lookup"><span data-stu-id="4fb06-207">Here are some examples of those interactive moments:</span></span>

![手写帧的动画 GIF，其中显示了是否检测到指针以及何时进入视图的字段](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="4fb06-209">*在检测到指针和进入视图字段时显示的手写跟踪帧。*</span><span class="sxs-lookup"><span data-stu-id="4fb06-209">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![与碰撞 crystals 交互的动画 GIF](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="4fb06-211">*与 crystals 的交互发生交互*</span><span class="sxs-lookup"><span data-stu-id="4fb06-211">*Interacting with colliding crystals through far interaction*</span></span>

![浏览近乎交互实用的动画 GIF](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="4fb06-213">*探索近交互实用*</span><span class="sxs-lookup"><span data-stu-id="4fb06-213">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="4fb06-214">关于团队</span><span class="sxs-lookup"><span data-stu-id="4fb06-214">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="4fb06-215"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="4fb06-215"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="4fb06-216"><i>领先技术设计人员</i></span><span class="sxs-lookup"><span data-stu-id="4fb06-216"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="4fb06-217">Dan 是设计全息影像的创造性主管，当前作为旧金山的 Microsoft 混合现实院校的设计主管，以前是伦敦的 Microsoft 混合现实工作室之一中的设计器。</span><span class="sxs-lookup"><span data-stu-id="4fb06-217">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="4fb06-218"><b>圣马丁 Wettig</b></span><span class="sxs-lookup"><span data-stu-id="4fb06-218"><b>Martin Wettig</b></span></span><br><span data-ttu-id="4fb06-219"><i>高级三维艺术家</i></span><span class="sxs-lookup"><span data-stu-id="4fb06-219"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="4fb06-220">圣马丁使三维艺术和 UI 设计在设计全息影像上，以前是 Microsoft 的一个混合现实工作室的高级三维音乐家。</span><span class="sxs-lookup"><span data-stu-id="4fb06-220">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist at one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="4fb06-221">非常感谢你对混合现实设计团队共享如此多的知识，并为 [对象理论](https://objecttheory.com/) 的令人惊叹的用户提供有关项目中每个步骤的重要团队。</span><span class="sxs-lookup"><span data-stu-id="4fb06-221">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge, and to the amazing folks at [Object Theory](https://objecttheory.com/) for being essential teammates through every step of the project.</span></span> <span data-ttu-id="4fb06-222">非常感谢您的热情，为您的热情和杰出的设计设计。</span><span class="sxs-lookup"><span data-stu-id="4fb06-222">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4fb06-223">下载设计全息影像应用</span><span class="sxs-lookup"><span data-stu-id="4fb06-223">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)