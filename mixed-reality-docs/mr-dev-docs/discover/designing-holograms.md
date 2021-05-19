---
title: 设计全息影像
description: 通过 Microsoft 的新设计全息影像应用程序了解混合现实。
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK， 混合现实工具包， 全息影像， 设计全息影像， 学习， 示例应用， 混合现实头戴显示设备， 虚拟现实头戴显示设备， 什么是虚拟现实
ms.openlocfilehash: 6e37c3f1ba98f202addb9c323632bca8bffae3b6
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143629"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="64762-104">设计全息影像的制作</span><span class="sxs-lookup"><span data-stu-id="64762-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="64762-105">请允许一个小的加载窗口，以说明此页上的所有冷 GIF 和嵌入式视频。</span><span class="sxs-lookup"><span data-stu-id="64762-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="64762-106">了解如何为混合现实进行设计可能很难，因为媒体并不总是能很好地转换为 2D 设计过程。</span><span class="sxs-lookup"><span data-stu-id="64762-106">Learning how to design for mixed reality can be hard because the medium doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="64762-107">在 Microsoft，我们创建了一个免费应用，HoloLens 2帮助你第一手了解混合现实 UX 设计的基本知识。</span><span class="sxs-lookup"><span data-stu-id="64762-107">Here at Microsoft, we've created a free app for the HoloLens 2 to help you learn the fundamentals of mixed reality UX Design firsthand.</span></span> <span data-ttu-id="64762-108">设计全息影像应用的独特方法深入探讨混合现实行为、提示和建议，以帮助你创建自己的具有吸引力且令人惊叹的 HoloLens 应用。</span><span class="sxs-lookup"><span data-stu-id="64762-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="64762-109">从 Microsoft 混合现实设计Microsoft Store下载应用并学习！</span><span class="sxs-lookup"><span data-stu-id="64762-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="64762-110">下载设计全息影像应用</span><span class="sxs-lookup"><span data-stu-id="64762-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![设计全息影像演示房间中头部跟踪场景的动画 GIF](images/designing-holograms/demo-room.gif)

<span data-ttu-id="64762-112&quot;>*设计全息影像的演示 (也称为&quot;房屋")*</span><span class="sxs-lookup"><span data-stu-id="64762-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="64762-113">针对混合现实进行设计</span><span class="sxs-lookup"><span data-stu-id="64762-113">Designing for mixed reality</span></span>

<span data-ttu-id="64762-114">和许多人一样，我过去设计移动应用。</span><span class="sxs-lookup"><span data-stu-id="64762-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="64762-115">从 2D 设计世界开始，进入空间计算领域（现在一切都位于全球）是一个显著转变。</span><span class="sxs-lookup"><span data-stu-id="64762-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="64762-116">在混合现实中，应用不再局限于 2D 屏幕;事实上，它们几乎是免费的，放置在现实世界中并与真实对象交互。</span><span class="sxs-lookup"><span data-stu-id="64762-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="64762-117">就我来说，将 3D 体验连接到传统的 2D 设计过程是混合现实开发最具挑战性方面。</span><span class="sxs-lookup"><span data-stu-id="64762-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="64762-118">在与客户的聊天中，我听说过"我了解要包含哪些功能以及如何启动和运行这些功能。</span><span class="sxs-lookup"><span data-stu-id="64762-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="64762-119">这是代码，我可以按照文档和教程操作，但用户体验如何？</span><span class="sxs-lookup"><span data-stu-id="64762-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="64762-120">有很多功能、不同的输入选项、不同的方案和物理环境，这一点非常巨大"。</span><span class="sxs-lookup"><span data-stu-id="64762-120">So many features, different input options, different scenarios, and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="64762-121">![从圣马力诺2中的 HoloLens 2 设计研讨会开始的图像，位于旧金山 ](images/designing-holograms/workshop.jpeg)
 *2 的 Hololens 2 设计研讨会* 中</span><span class="sxs-lookup"><span data-stu-id="64762-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="64762-122">机会</span><span class="sxs-lookup"><span data-stu-id="64762-122">An opportunity to teach</span></span>

<span data-ttu-id="64762-123">这并不是很明显，但会出现一个极好的机会，将混合现实用作一种用于教授的媒介。</span><span class="sxs-lookup"><span data-stu-id="64762-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="64762-124">设计全息影像是介绍混合现实设计概念和建议的视觉体验。</span><span class="sxs-lookup"><span data-stu-id="64762-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="64762-125">这只是你以及演示混合现实设计概念的虚拟老师。</span><span class="sxs-lookup"><span data-stu-id="64762-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="64762-126">一切都是从第三人的角度来看，它在自己的空间中实现了丰富的体验。</span><span class="sxs-lookup"><span data-stu-id="64762-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="64762-127">*设计全息影像尾端视频*</span><span class="sxs-lookup"><span data-stu-id="64762-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="64762-128">探索娃房子</span><span class="sxs-lookup"><span data-stu-id="64762-128">Exploring the doll house</span></span>

<span data-ttu-id="64762-129">娃房子是我们在整个应用程序中使用的虚拟环境。</span><span class="sxs-lookup"><span data-stu-id="64762-129">The doll house is the virtual environment we use throughout the app.</span></span> <span data-ttu-id="64762-130">环境为 80 x 60 x 40-cm，其中包含大多数房间共有的基本元素，如墙壁、灯、家具、桌子和电视。</span><span class="sxs-lookup"><span data-stu-id="64762-130">The environment is an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="64762-131">娃房子是应用程序体验的主要 protagonist，因此我们需要确保它在任何环境中都能正常工作。</span><span class="sxs-lookup"><span data-stu-id="64762-131">The doll house is the main protagonist of the app experience, so we needed to make sure it would work great in any environment.</span></span> <span data-ttu-id="64762-132">将其视为一个小型演示空间，用于可视化各种混合现实概念。</span><span class="sxs-lookup"><span data-stu-id="64762-132">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="64762-133">*Dollhouse 调整行为的视频*</span><span class="sxs-lookup"><span data-stu-id="64762-133">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="64762-134">1:1 与1:10 原型</span><span class="sxs-lookup"><span data-stu-id="64762-134">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="64762-135">我们最初假设，1:1 的演示会令人吃惊，几乎与查看真实的老师一样。</span><span class="sxs-lookup"><span data-stu-id="64762-135">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="64762-136">用户将看到老师在实际生活中看到的一切内容。</span><span class="sxs-lookup"><span data-stu-id="64762-136">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="64762-137">但是，我们立即意识到存在以下几个问题：</span><span class="sxs-lookup"><span data-stu-id="64762-137">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="64762-138">大多数开发人员会在办公室或比演示房间小的房间内运行应用程序，因此不适合。</span><span class="sxs-lookup"><span data-stu-id="64762-138">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="64762-139">显示是累加的，这意味着整个虚拟环境将覆盖在用户的空间上。</span><span class="sxs-lookup"><span data-stu-id="64762-139">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="64762-140">这可能会使两个表（可能为 double couches）和不对齐的墙壁产生混淆。</span><span class="sxs-lookup"><span data-stu-id="64762-140">That can get confusing with two tables, maybe double couches, and walls that don’t align.</span></span>
- <span data-ttu-id="64762-141">最差的一个虚拟环境受到视场的严格约束。</span><span class="sxs-lookup"><span data-stu-id="64762-141">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="64762-142">当我们尝试了一个微型 1：10 刻度时，结果是一个真实的房间的精彩眼睛视图。</span><span class="sxs-lookup"><span data-stu-id="64762-142">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room.</span></span> <span data-ttu-id="64762-143">你可以同时从任何角度查看所有正在进行的所有内容。</span><span class="sxs-lookup"><span data-stu-id="64762-143">You could see everything that was going on from any angle all at the same time.</span></span> <span data-ttu-id="64762-144">最令人意外的是，大多数测试人员发现查看小版本更沉浸式，然后他们从未切换回 1：1 比例。</span><span class="sxs-lookup"><span data-stu-id="64762-144">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="64762-145">因此，我们决定实际放弃 1：1 版本，并避免适应 UI 和应用的其他方面所需的额外工作。</span><span class="sxs-lookup"><span data-stu-id="64762-145">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="64762-146">![比例为 1：1 的视图字段，比例为 ](images/designing-holograms/1-1-scale.png)
 *1：1*</span><span class="sxs-lookup"><span data-stu-id="64762-146">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="64762-147">![比例为 1：10 的视图字段，比例为 ](images/designing-holograms/1-10-scale.png)
 *1：10*</span><span class="sxs-lookup"><span data-stu-id="64762-147">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="64762-148">使用 混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="64762-148">Using Mixed Reality Capture</span></span>

<span data-ttu-id="64762-149">此应用的最特征之一是使用 混合现实捕获来教授和演示混合现实设计概念。</span><span class="sxs-lookup"><span data-stu-id="64762-149">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="64762-150">Microsoft 在混合现实捕获有一个工作室。</span><span class="sxs-lookup"><span data-stu-id="64762-150">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="64762-151">Microsoft 还将此技术许可给其他工作室，包括华盛顿特区的头像维度、洛杉矶的 Metastage、伦敦的 Dimension Studios、位于意大利的 SK Telecom 和位于意大利的 Volucap。</span><span class="sxs-lookup"><span data-stu-id="64762-151">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="64762-152">可在此处找到有关 混合现实捕获 [工作室的信息](https://www.microsoft.com/mixed-reality/capture-studios)。</span><span class="sxs-lookup"><span data-stu-id="64762-152">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="64762-153">*来自旧金山 混合现实捕获 Studio 中 106 个相机之一的 Daniel Escudero 的原始视频。*</span><span class="sxs-lookup"><span data-stu-id="64762-153">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="64762-154">捕获过程会生成关键帧网格、法线和纹理，这些网格、法线和纹理可以作为 OBJ/PNG 文件传送，供进一步后期制作，或准备好播放为 H.264 压缩 MP4 文件。</span><span class="sxs-lookup"><span data-stu-id="64762-154">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="64762-155">这些文件可以导入 Unity、Unreal、Native 和 WebXR 项目中。</span><span class="sxs-lookup"><span data-stu-id="64762-155">These files can be imported into Unity, Unreal, Native, and WebXR projects.</span></span> <span data-ttu-id="64762-156">文件可以在 Windows、iOS、Mac、Android、Magic Leap 和 Playstation VR 中运行。</span><span class="sxs-lookup"><span data-stu-id="64762-156">Files can run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="64762-157">*提供的捕获播放器，用于分析包含带音频和嵌入网格的视频的 mp4。*</span><span class="sxs-lookup"><span data-stu-id="64762-157">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="64762-158">操作捕获和虚拟对象</span><span class="sxs-lookup"><span data-stu-id="64762-158">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="64762-159">混合现实捕获生成人员或动物的虚拟表示形式，但有时可能需要这些字符来与其他虚拟对象交互。</span><span class="sxs-lookup"><span data-stu-id="64762-159">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="64762-160">下面两个示例演示了我们处理场景以实现此效果的不同方式。</span><span class="sxs-lookup"><span data-stu-id="64762-160">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="64762-161">打印头注视调整</span><span class="sxs-lookup"><span data-stu-id="64762-161">Head Gaze Adjustment</span></span>

<span data-ttu-id="64762-162">Headgaze 调整使你可以在运行时移动已捕获人员的标题，这意味着你可以获得用户的捕获面。</span><span class="sxs-lookup"><span data-stu-id="64762-162">Headgaze adjustment lets you move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="64762-163">在我们的示例中，我们使用它来显示所需的视图和字段的字段。</span><span class="sxs-lookup"><span data-stu-id="64762-163">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="64762-164">下面是一个移动 gameobject，它作为打印头注视的目标来查看。</span><span class="sxs-lookup"><span data-stu-id="64762-164">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="64762-165">当我们将目标从一侧移到另一侧时，捕获的开头将如下所示。</span><span class="sxs-lookup"><span data-stu-id="64762-165">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="64762-166">我们使用这一技巧来确保空闲捕获始终面对存放在娃房子不同部分的全息影像。</span><span class="sxs-lookup"><span data-stu-id="64762-166">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![在 Unity 中的目标 gameobject 之后，在运行时移动捕获的头](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="64762-168">*当 Unity 中的目标 gameobject 后，将在运行时移动捕获的头。*</span><span class="sxs-lookup"><span data-stu-id="64762-168">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="64762-169">同步动画对象</span><span class="sxs-lookup"><span data-stu-id="64762-169">Syncing Animated Objects</span></span>

<span data-ttu-id="64762-170">第二个是动画处理要与捕获移动同步的对象。</span><span class="sxs-lookup"><span data-stu-id="64762-170">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="64762-171">在应用程序的不同部分，每隔五帧导入一个特定捕获的顺序 Obj。</span><span class="sxs-lookup"><span data-stu-id="64762-171">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="64762-172">然后，Obj 在场景中进行动画处理，以确保它们与捕获的相应帧匹配。</span><span class="sxs-lookup"><span data-stu-id="64762-172">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="64762-173">这是一种令人厌烦的动画处理和 keyframing 的过程，但结果很好。</span><span class="sxs-lookup"><span data-stu-id="64762-173">It’s a tedious process of animating and keyframing, but the result is great.</span></span> <span data-ttu-id="64762-174">你现在可以看到混合现实捕获与非捕获对象的交互。</span><span class="sxs-lookup"><span data-stu-id="64762-174">You can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![在混合现实捕获和 UI 面板之间同步动画](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="64762-176">*在混合现实捕获和 UI 面板之间同步动画*</span><span class="sxs-lookup"><span data-stu-id="64762-176">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="64762-177">UI 创作过程</span><span class="sxs-lookup"><span data-stu-id="64762-177">UI creative process</span></span>

<span data-ttu-id="64762-178">开始使用 UI 设计时，我们想要展示全息影像必须提供的一些神奇的做法。</span><span class="sxs-lookup"><span data-stu-id="64762-178">When we started the UI design, we wanted to show some of the magic and possibility that holograms have to offer.</span></span> <span data-ttu-id="64762-179">在三维世界中，简单地显示静态2D 窗口和文本框并不合适。</span><span class="sxs-lookup"><span data-stu-id="64762-179">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world.</span></span> <span data-ttu-id="64762-180">许多可能性不会显示，因此，我们决定从一开始就放弃这种可能性，并充分利用全息 3D 空间。</span><span class="sxs-lookup"><span data-stu-id="64762-180">Many of the possibilities at hand just don't show up, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="64762-181">最初，我们从向面板、图标和文本信息添加一些粗细开始。</span><span class="sxs-lookup"><span data-stu-id="64762-181">At first, we started with adding some thickness to the panels, icons, and text information.</span></span> <span data-ttu-id="64762-182">不过，作为用户，我所看到的是一个文本框。</span><span class="sxs-lookup"><span data-stu-id="64762-182">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="64762-183">包含图像的文本框，但我们不存在。</span><span class="sxs-lookup"><span data-stu-id="64762-183">Text boxes with images, but we aren't there.</span></span> <span data-ttu-id="64762-184">我们进一步利用混合现实工具包和 MRTK (器) 器。</span><span class="sxs-lookup"><span data-stu-id="64762-184">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="64762-185">MRTK 着色器成为功能强大的工具，我们利用其模具功能向面板添加负深度。</span><span class="sxs-lookup"><span data-stu-id="64762-185">The MRTK shaders became a powerful tool, and we made use of its stencil features to add negative depth to the panels.</span></span> <span data-ttu-id="64762-186">这意味着，图标现在显示在透明面板后面，而不是在文本框前面添加元素。</span><span class="sxs-lookup"><span data-stu-id="64762-186">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="64762-187">现在，作为用户，我不再可以在现实世界中复制它，这是全息幻像开始发生的地方。</span><span class="sxs-lookup"><span data-stu-id="64762-187">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="64762-188">此外，作为一个不想阅读的用户，我已在物理世界做很多工作。</span><span class="sxs-lookup"><span data-stu-id="64762-188">Also as a user I don’t really like to read, I do a lot already in the physical world.</span></span>

<span data-ttu-id="64762-189">显然，图标比简单文本的效果要强很多，为了提供更强大的指导，我随后开始创建一组动画对象和头像，每个图标都讲述一个有关各自方案中正在完成的工作及其使用方式的小故事。</span><span class="sxs-lookup"><span data-stu-id="64762-189">Obviously icons work a lot better than simple text does, to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![交互式全息菜单系统的动画 GIF](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="64762-191">核心概念</span><span class="sxs-lookup"><span data-stu-id="64762-191">Core concepts</span></span>

<span data-ttu-id="64762-192">**头部跟踪和眼动跟踪**</span><span class="sxs-lookup"><span data-stu-id="64762-192">**Head Tracking and Eye Tracking**</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="64762-193">**手部跟踪**</span><span class="sxs-lookup"><span data-stu-id="64762-193">**Hand Tracking**</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

<span data-ttu-id="64762-194">**空间感知**</span><span class="sxs-lookup"><span data-stu-id="64762-194">**Spatial Awareness**</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

<span data-ttu-id="64762-195">**全息帧**</span><span class="sxs-lookup"><span data-stu-id="64762-195">**Holographic frame**</span></span>

![用户通过动画 GIF 来四处查看，其中突出显示了全息帧](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="64762-197">**坐标系统**</span><span class="sxs-lookup"><span data-stu-id="64762-197">**Coordinate systems**</span></span>

![用户通过动画 GIF 来四处查看仓库，其中突出显示了坐标系统](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="64762-199">**眼动跟踪**</span><span class="sxs-lookup"><span data-stu-id="64762-199">**Eye tracking**</span></span>

![用户查看固定全息影像的动画 GIF，其中突出显示了眼睛凝视射线](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="64762-201">**房间扫描可视化和空间映射**</span><span class="sxs-lookup"><span data-stu-id="64762-201">**Room scan visualization and spatial mapping**</span></span>

![要映射的仓库内所有图面的动画 GIF](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="64762-203">**场景理解**</span><span class="sxs-lookup"><span data-stu-id="64762-203">**Scene understanding**</span></span>

![正在识别的仓库中对象的动画 GIF](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="64762-205">**手动射线的点和提交**</span><span class="sxs-lookup"><span data-stu-id="64762-205">**Point and commit with hand rays**</span></span>

![用户的动画 GIF，其中突出显示了手 ray](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="64762-207">"试用"</span><span class="sxs-lookup"><span data-stu-id="64762-207">"Try it out" moments</span></span>

<span data-ttu-id="64762-208">设计全息影像会讲授混合现实概念，但它也允许您在房间内试用它们。</span><span class="sxs-lookup"><span data-stu-id="64762-208">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="64762-209">在其中一些说明后，我们将会暂停，并将您娃房子并进入互动时间。</span><span class="sxs-lookup"><span data-stu-id="64762-209">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="64762-210">下面是这些交互式对话的一些示例：</span><span class="sxs-lookup"><span data-stu-id="64762-210">Here are some examples of those interactive moments:</span></span>

![手写帧的动画 GIF，其中显示了是否检测到指针以及何时进入视图的字段](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="64762-212">*在检测到指针和进入视图字段时显示的手写跟踪帧。*</span><span class="sxs-lookup"><span data-stu-id="64762-212">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![与碰撞 crystals 交互的动画 GIF](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="64762-214">*与 crystals 的交互发生交互*</span><span class="sxs-lookup"><span data-stu-id="64762-214">*Interacting with colliding crystals through far interaction*</span></span>

![浏览近乎交互实用的动画 GIF](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="64762-216">*探索近交互实用*</span><span class="sxs-lookup"><span data-stu-id="64762-216">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="64762-217">关于团队</span><span class="sxs-lookup"><span data-stu-id="64762-217">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="64762-218"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="64762-218"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="64762-219"><i>领先技术设计人员</i></span><span class="sxs-lookup"><span data-stu-id="64762-219"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="64762-220">Dan 是设计全息影像的创造性主管，当前作为旧金山的 Microsoft 混合现实院校的设计主管，以前是伦敦的 Microsoft 混合现实工作室之一中的设计器。</span><span class="sxs-lookup"><span data-stu-id="64762-220">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="64762-221"><b>圣马丁 Wettig</b></span><span class="sxs-lookup"><span data-stu-id="64762-221"><b>Martin Wettig</b></span></span><br><span data-ttu-id="64762-222"><i>高级三维艺术家</i></span><span class="sxs-lookup"><span data-stu-id="64762-222"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="64762-223">圣马丁使三维艺术和 UI 设计在设计全息影像上，以前是 Microsoft 的一个混合现实工作室的高级三维音乐家。</span><span class="sxs-lookup"><span data-stu-id="64762-223">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist at one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="64762-224">非常感谢你对混合现实设计团队共享如此多的知识，并为 [对象理论](https://objecttheory.com/) 的令人惊叹的用户提供有关项目中每个步骤的重要团队。</span><span class="sxs-lookup"><span data-stu-id="64762-224">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge, and to the amazing folks at [Object Theory](https://objecttheory.com/) for being essential teammates through every step of the project.</span></span> <span data-ttu-id="64762-225">感谢你的出色人才，感谢你对设计的兴趣和出色的眼睛。</span><span class="sxs-lookup"><span data-stu-id="64762-225">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="64762-226">下载设计全息影像应用</span><span class="sxs-lookup"><span data-stu-id="64762-226">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)