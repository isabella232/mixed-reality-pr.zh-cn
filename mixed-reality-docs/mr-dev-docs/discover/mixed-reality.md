---
title: 什么是混合现实？
description: 探讨混合现实，展示如何在混合现实范围内使用 AR 和 VR 设备。
author: brandonbray
ms.author: branbray
ms.date: 08/26/2020
ms.topic: article
keywords: 混合现实, 全息, AR, VR, MR, XR, 增强现实, 虚拟现实, 说明, 案例研究, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 什么是虚拟现实, 什么是增强现实
ms.localizationpriority: high
ms.openlocfilehash: e524312b2e479b1c3d05039403aba10de864ae18
ms.sourcegitcommit: 5603dc9f6511707cb8b215f20f6c6485ef480538
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/16/2021
ms.locfileid: "112230209"
---
# <a name="what-is-mixed-reality"></a><span data-ttu-id="19552-104">什么是混合现实？</span><span class="sxs-lookup"><span data-stu-id="19552-104">What is Mixed Reality?</span></span>

![在 HoloLens 2 用手进行点选和提交](images/02_MixedRealitySlashMixedReality.png)

<span data-ttu-id="19552-106">混合现实是物理世界和数字世界的混合，开启了人、计算机与环境交互之间的联系。</span><span class="sxs-lookup"><span data-stu-id="19552-106">Mixed Reality is a blend of physical and digital worlds, unlocking the links between human, computer, and environment interaction.</span></span> <span data-ttu-id="19552-107">这一新的现实基于计算机视觉、图形处理能力、显示技术和输入系统的进步。</span><span class="sxs-lookup"><span data-stu-id="19552-107">This new reality is based on advancements in computer vision, graphical processing power, display technology, and input systems.</span></span> <span data-ttu-id="19552-108">但是，“混合现实”一词由 Paul Milgram 和 Fumio Kishino 在其 1994 年发表的论文 [A Taxonomy of Mixed Reality Visual Displays](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)（混合现实视频显示的分类法）中提到。</span><span class="sxs-lookup"><span data-stu-id="19552-108">However, the term *Mixed Reality* was introduced in a 1994 paper by Paul Milgram and Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)."</span></span> <span data-ttu-id="19552-109">此论文探讨了“虚拟连续体”的概念以及应用于显示内容的类别分类法。</span><span class="sxs-lookup"><span data-stu-id="19552-109">Their paper explored the concept of the *virtuality continuum* and the categorization of taxonomy applied to displays.</span></span> <span data-ttu-id="19552-110">从那此后，混合现实的应用包括以下各项，已经超越了显示内容：</span><span class="sxs-lookup"><span data-stu-id="19552-110">Since then, the application of Mixed Reality has gone beyond displays to include:</span></span>
* <span data-ttu-id="19552-111">环境输入</span><span class="sxs-lookup"><span data-stu-id="19552-111">Environmental input</span></span>
* <span data-ttu-id="19552-112">空间音效</span><span class="sxs-lookup"><span data-stu-id="19552-112">Spatial sound</span></span>
* <span data-ttu-id="19552-113">真实和虚拟空间中的位置和定位</span><span class="sxs-lookup"><span data-stu-id="19552-113">Locations and positioning in both real and virtual spaces</span></span>

<span data-ttu-id="19552-114">![混合现实范围图像](images/mixedrealityspectrum-worlds.png)</span><span class="sxs-lookup"><span data-stu-id="19552-114">![The Mixed Reality spectrum image](images/mixedrealityspectrum-worlds.png)</span></span><br>
<span data-ttu-id="19552-115">插图：混合现实是将物理世界与数字世界相融合的结果。</span><span class="sxs-lookup"><span data-stu-id="19552-115">*Image: Mixed Reality is the result of blending the physical world with the digital world.*</span></span>

<br>

---

## <a name="environmental-input-and-perception"></a><span data-ttu-id="19552-116">环境输入和感知</span><span class="sxs-lookup"><span data-stu-id="19552-116">Environmental input and perception</span></span>

<span data-ttu-id="19552-117">过去几十年来，对人类输入与计算机输入之间关系的探索一直在继续，从而形成了称作“人机交互”(HCI) 的学科。</span><span class="sxs-lookup"><span data-stu-id="19552-117">Over the past several decades, exploration into the relationship between human and computer input has continued, leading to the discipline known as *human computer interaction* or HCI.</span></span> <span data-ttu-id="19552-118">人类输入是通过不同的方式进行的，包括键盘、鼠标、触摸、笔迹、语音，甚至 Kinect 骨骼跟踪。</span><span class="sxs-lookup"><span data-stu-id="19552-118">Human input happens through different means, including keyboards, mice, touch, ink, voice, and even Kinect skeletal tracking.</span></span>

<span data-ttu-id="19552-119">传感器和处理技术的进步为计算机环境输入创造了新领域。</span><span class="sxs-lookup"><span data-stu-id="19552-119">Advancements in sensors and processing are creating new areas of computer input from environments.</span></span> <span data-ttu-id="19552-120">计算机与环境之间的交互是对环境的理解或认知，这就是 Windows 中显示环境信息的 API 称作[感知 API](/uwp/api/Windows.Perception) 的原因。</span><span class="sxs-lookup"><span data-stu-id="19552-120">The interaction between computers and environments is environmental understanding or *perception*, which is why the API names in Windows that reveal environmental information are called the [perception APIs](/uwp/api/Windows.Perception).</span></span> <span data-ttu-id="19552-121">环境输入捕获如下所述的信息：用户在世界上的位置（[头部跟踪](../design/coordinate-systems.md)）、表面和边界（[空间映射](../design/spatial-mapping.md)和[场景理解](../design/scene-understanding.md)）、环境照明、环境音效、对象识别和定位。</span><span class="sxs-lookup"><span data-stu-id="19552-121">Environmental input captures things like a person's position in the world ([head tracking](../design/coordinate-systems.md)), surfaces, and boundaries ([spatial mapping](../design/spatial-mapping.md) and [scene understanding](../design/scene-understanding.md)), ambient lighting, environmental sound, object recognition, and location.</span></span>

<br>

<span data-ttu-id="19552-122">![显示计算机、人类与环境之间的交互的文氏图](images/mixed-reality-venn-diagram-300px.png)</span><span class="sxs-lookup"><span data-stu-id="19552-122">![Venn diagram showing interactions between computers, humans and environments](images/mixed-reality-venn-diagram-300px.png)</span></span><br><span data-ttu-id="19552-123"> \
*插图\：* 计算机、人类与环境之间的交互。</span><span class="sxs-lookup"><span data-stu-id="19552-123"> \
*Image: The interactions between computers, humans, and environments.*</span></span>

<br>

<span data-ttu-id="19552-124">计算机处理、人类输入和环境输入 - 这三者的组合为创建真正的混合现实体验奠定了基础。</span><span class="sxs-lookup"><span data-stu-id="19552-124">The combination of all three - **computer processing, human input, and environmental input** - sets the stage for creating true Mixed Reality experiences.</span></span> <span data-ttu-id="19552-125">物理世界中的运动转换为数字世界中的运动。</span><span class="sxs-lookup"><span data-stu-id="19552-125">Movement through the physical world translates to movement in the digital world.</span></span> <span data-ttu-id="19552-126">物理世界中的边界会影响数字世界中的应用体验，例如玩游戏。</span><span class="sxs-lookup"><span data-stu-id="19552-126">Boundaries in the physical world influence application experiences, such as game play, in the digital world.</span></span> <span data-ttu-id="19552-127">如果没有环境输入，体验就无法在物理现实与数字现实之间进行融合。</span><span class="sxs-lookup"><span data-stu-id="19552-127">Without environmental input, experiences can't blend between physical and digital realities.</span></span><br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a><span data-ttu-id="19552-128">混合现实范围</span><span class="sxs-lookup"><span data-stu-id="19552-128">The Mixed Reality spectrum</span></span>

<span data-ttu-id="19552-129">由于混合现实融合了物理世界和数字世界，这两种现实定义了称作“虚拟连续体”的范围的两个极端。</span><span class="sxs-lookup"><span data-stu-id="19552-129">Since Mixed Reality blends both physical and digital worlds, these two realities define the polar ends of a spectrum known as the virtuality continuum.</span></span> <span data-ttu-id="19552-130">我们将这一系列的现实称作“混合现实范围”。</span><span class="sxs-lookup"><span data-stu-id="19552-130">We refer to the array of realities as the *Mixed Reality spectrum*.</span></span> <span data-ttu-id="19552-131">左侧是物理现实，是人类所在的环境。</span><span class="sxs-lookup"><span data-stu-id="19552-131">On the left-hand side, we have the physical reality that we as humans exist in.</span></span> <span data-ttu-id="19552-132">右侧是对应的数字现实。</span><span class="sxs-lookup"><span data-stu-id="19552-132">On the right-hand side, we have the corresponding digital reality.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a><span data-ttu-id="19552-133">增强现实与虚拟现实</span><span class="sxs-lookup"><span data-stu-id="19552-133">Augmented vs. virtual reality</span></span>

<span data-ttu-id="19552-134">目前市场上的大多数手机几乎都不具备环境理解功能。</span><span class="sxs-lookup"><span data-stu-id="19552-134">Most mobile phones on the market today have little to no environmental understanding capabilities.</span></span> <span data-ttu-id="19552-135">它们提供的体验无法混合物理现实和数字现实。</span><span class="sxs-lookup"><span data-stu-id="19552-135">The experiences they offer can't mix physical and digital realities.</span></span> <span data-ttu-id="19552-136">在物理世界的视频流中叠加图形的体验是“增强现实”。 </span><span class="sxs-lookup"><span data-stu-id="19552-136">The experiences that overlay graphics on video streams of the physical world are *augmented reality*.</span></span> <span data-ttu-id="19552-137">遮挡视线以呈现数字体验的体验是“虚拟现实”。 </span><span class="sxs-lookup"><span data-stu-id="19552-137">The experiences that occlude your view to present a digital experience are *virtual reality*.</span></span> <span data-ttu-id="19552-138">在增强现实和虚拟现实之间实现的体验形成了“混合现实”：</span><span class="sxs-lookup"><span data-stu-id="19552-138">The experiences enabled between augmented and virtual reality form *Mixed Reality*:</span></span>
* <span data-ttu-id="19552-139">从物理世界开始，我们可以放置一个数字对象（例如全息影像），就如同它就在那里一样。</span><span class="sxs-lookup"><span data-stu-id="19552-139">Starting with the physical world, placing a digital object, such as a hologram, as if it was there.</span></span>
* <span data-ttu-id="19552-140">从物理世界开始，另一人（头像）的数字表示形式会显示他（她）在留下便条时所处的位置。</span><span class="sxs-lookup"><span data-stu-id="19552-140">Starting with the physical world, a digital representation of another person--an avatar--shows the location where they were standing when leaving notes.</span></span> <span data-ttu-id="19552-141">换而言之，这种体验代表不同时间点的异步协作。</span><span class="sxs-lookup"><span data-stu-id="19552-141">In other words, experiences that represent asynchronous collaboration at different points in time.</span></span>
* <span data-ttu-id="19552-142">从数字世界开始，物理世界中的物理边界（例如墙壁和家具）在体验中以数字形式显示，以帮助用户避开物理对象。</span><span class="sxs-lookup"><span data-stu-id="19552-142">Starting with a digital world, physical boundaries from the physical world like walls and furniture appear digitally within the experience to help users avoid physical objects.</span></span>

<br>

<span data-ttu-id="19552-143">![混合现实范围](images/mixedrealityspectrum.png)</span><span class="sxs-lookup"><span data-stu-id="19552-143">![The Mixed Reality spectrum](images/mixedrealityspectrum.png)</span></span><br>
<span data-ttu-id="19552-144">插图：混合现实范围</span><span class="sxs-lookup"><span data-stu-id="19552-144">*Image: The Mixed Reality spectrum*</span></span>

<br>

<span data-ttu-id="19552-145">当今的大部分增强现实和虚拟现实产品/服务仅代表了此范围的一小部分，且被认为是较大混合现实范围的子集。</span><span class="sxs-lookup"><span data-stu-id="19552-145">Most augmented reality and virtual reality offerings available today represent a small part of this spectrum and are considered subsets of the larger Mixed Reality spectrum.</span></span> <span data-ttu-id="19552-146">Windows 10 的开发考虑到了整个范围，可以融合现实世界中人员、地点和物品的数字表示形式。</span><span class="sxs-lookup"><span data-stu-id="19552-146">Windows 10 is built with the entire spectrum in mind, and allows blending digital representations of people, places, and things with the real world.</span></span>


## <a name="devices-and-experiences"></a><span data-ttu-id="19552-147">设备和体验</span><span class="sxs-lookup"><span data-stu-id="19552-147">Devices and experiences</span></span>

<span data-ttu-id="19552-148">有两种主要类型的设备可以提供 Windows Mixed Reality 体验：</span><span class="sxs-lookup"><span data-stu-id="19552-148">There are two main types of devices that deliver Windows Mixed Reality experiences:</span></span>
1. <span data-ttu-id="19552-149">全息设备的特征是能够将数字内容放入真实世界，就像是这些内容就在那里。</span><span class="sxs-lookup"><span data-stu-id="19552-149">**Holographic devices** are characterized by the device's ability to place digital content in the real world as if it were there.</span></span>
2. <span data-ttu-id="19552-150">沉浸式设备的特征是能够创建“存在感”- 隐藏物理世界，将其替换为数字体验。</span><span class="sxs-lookup"><span data-stu-id="19552-150">**Immersive devices** are characterized by the device's ability to create a sense of "presence"--hiding the physical world, and replacing it with a digital experience.</span></span>

<table>
<tr>
<th width="30%"> <span data-ttu-id="19552-151">特征</span><span class="sxs-lookup"><span data-stu-id="19552-151">Characteristic</span></span></th><th width="35%"> <span data-ttu-id="19552-152">全息设备</span><span class="sxs-lookup"><span data-stu-id="19552-152">Holographic devices</span></span></th><th width="35%"> <span data-ttu-id="19552-153">沉浸式设备</span><span class="sxs-lookup"><span data-stu-id="19552-153">Immersive devices</span></span></th>
</tr><tr>
<td><span data-ttu-id="19552-154"><strong>示例设备</strong></span><span class="sxs-lookup"><span data-stu-id="19552-154"><strong>Example device</strong></span></span></td><td> <span data-ttu-id="19552-155">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="19552-155">Microsoft HoloLens</span></span><br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> <span data-ttu-id="19552-156">Samsung HMD Odyssey+</span><span class="sxs-lookup"><span data-stu-id="19552-156">Samsung HMD Odyssey+</span></span><br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><span data-ttu-id="19552-157"><strong>显示器</strong></span><span class="sxs-lookup"><span data-stu-id="19552-157"><strong>Display</strong></span></span></td><td> <span data-ttu-id="19552-158">看透显示内容。</span><span class="sxs-lookup"><span data-stu-id="19552-158">See-through display.</span></span> <span data-ttu-id="19552-159">可让用户在戴上头戴显示设备时观看物理环境。</span><span class="sxs-lookup"><span data-stu-id="19552-159">Allows user to see the physical environment while wearing the headset.</span></span></td><td> <span data-ttu-id="19552-160">不透明显示。</span><span class="sxs-lookup"><span data-stu-id="19552-160">Opaque display.</span></span> <span data-ttu-id="19552-161">在戴上头戴显示设备时阻挡物理环境。</span><span class="sxs-lookup"><span data-stu-id="19552-161">Blocks out the physical environment while wearing the headset.</span></span></td>
</tr><tr>
<td><span data-ttu-id="19552-162"><strong>移动</strong></span><span class="sxs-lookup"><span data-stu-id="19552-162"><strong>Movement</strong></span></span></td><td> <span data-ttu-id="19552-163">六度自由全方位运动，支持旋转和平移。</span><span class="sxs-lookup"><span data-stu-id="19552-163">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td><td> <span data-ttu-id="19552-164">六度自由全方位运动，支持旋转和平移。</span><span class="sxs-lookup"><span data-stu-id="19552-164">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td>
</tr>
</table> 


> [!NOTE]
> <span data-ttu-id="19552-165">设备是与单独的电脑保持连接或拴定状态（通过 USB 数据线或 Wi-Fi）还是保持独立状态（断开连接），并不能反映设备是全息设备还是沉浸式设备。</span><span class="sxs-lookup"><span data-stu-id="19552-165">Whether a device is connected to or tethered to a separate PC (via USB cable or Wi-Fi) or self-contained (untethered) doesn't reflect whether a device is holographic or immersive.</span></span> <span data-ttu-id="19552-166">可改善运动性的功能会改善体验，而全息设备和沉浸式设备都可以保持连接或断开连接状态。</span><span class="sxs-lookup"><span data-stu-id="19552-166">Features that improve mobility lead to better experiences, and both holographic and immersive devices could be tethered or untethered.</span></span>

<span data-ttu-id="19552-167">技术进步创造了混合现实体验，但目前还没有能兼容所有相关体验的设备。</span><span class="sxs-lookup"><span data-stu-id="19552-167">Technological advancement enables Mixed Reality experiences, but there aren't any devices today that can run experiences across the entire spectrum.</span></span> <span data-ttu-id="19552-168">Windows 10 为设备制造商和开发人员提供了一个通用的混合现实平台。</span><span class="sxs-lookup"><span data-stu-id="19552-168">Windows 10 provides a common Mixed Reality platform for both device manufacturers and developers.</span></span> <span data-ttu-id="19552-169">当今的设备可以支持混合现实范围内的某个特定范围，而新设备扩展了该范围。</span><span class="sxs-lookup"><span data-stu-id="19552-169">Devices today can support a specific range within the Mixed Reality spectrum, with new devices expanding that range.</span></span> <span data-ttu-id="19552-170">未来，全息设备将变得有沉浸感，而沉浸式设备也将变得更有全息感。</span><span class="sxs-lookup"><span data-stu-id="19552-170">In the future, holographic devices will be immersive, and immersive devices will be more holographic.</span></span>

<br>

<span data-ttu-id="19552-171">![混合现实范围内的设备类型](images/Final_WhatIsMixedReality07.png)</span><span class="sxs-lookup"><span data-stu-id="19552-171">![Device types in the Mixed Reality spectrum](images/Final_WhatIsMixedReality07.png)</span></span><br>
<span data-ttu-id="19552-172">插图：设备在混合现实范围内所处的位置</span><span class="sxs-lookup"><span data-stu-id="19552-172">*Image: Where devices exist on the Mixed Reality spectrum*</span></span>

<span data-ttu-id="19552-173">最好是考虑应用程序或游戏开发人员想要创建的体验类型。</span><span class="sxs-lookup"><span data-stu-id="19552-173">It's best to think what type of experience an application or game developer wants to create.</span></span> <span data-ttu-id="19552-174">体验往往面向混合现实范围内的特定点或部分。</span><span class="sxs-lookup"><span data-stu-id="19552-174">The experiences will typically target a specific point or part on the spectrum.</span></span> <span data-ttu-id="19552-175">开发人员应考虑所要面向的设备功能。</span><span class="sxs-lookup"><span data-stu-id="19552-175">Developers should consider the capabilities of devices they want to target.</span></span> <span data-ttu-id="19552-176">依赖于物理世界的体验最好是在 HoloLens 上运行。</span><span class="sxs-lookup"><span data-stu-id="19552-176">Experiences that rely on the physical world will run best on HoloLens.</span></span>
* <span data-ttu-id="19552-177">**向左（接近物理现实）。**</span><span class="sxs-lookup"><span data-stu-id="19552-177">**Towards the left (near physical reality).**</span></span> <span data-ttu-id="19552-178">用户保留在其物理环境中，永远不相信他们已离开该环境。</span><span class="sxs-lookup"><span data-stu-id="19552-178">Users remain present in their physical environment and are never made to believe they have left that environment.</span></span>
* <span data-ttu-id="19552-179">中间（完全混合现实）。</span><span class="sxs-lookup"><span data-stu-id="19552-179">**In the middle (fully Mixed Reality).**</span></span> <span data-ttu-id="19552-180">这些体验融合了真实世界和数字世界。</span><span class="sxs-lookup"><span data-stu-id="19552-180">These experiences blend the real world and the digital world.</span></span> <span data-ttu-id="19552-181">电影[勇敢者的游戏](https://en.wikipedia.org/wiki/Jumanji)的观众能够适应故事发生地的房子与丛林环境融合后的物理结构。</span><span class="sxs-lookup"><span data-stu-id="19552-181">Viewers who have seen the movie [Jumanji](https://en.wikipedia.org/wiki/Jumanji) can reconcile how the physical structure of the house where the story took place was blended with a jungle environment.</span></span>
* <span data-ttu-id="19552-182">**向右（接近数字现实）。**</span><span class="sxs-lookup"><span data-stu-id="19552-182">**Towards the right (near digital reality).**</span></span> <span data-ttu-id="19552-183">用户将体验到一个数字环境，并且不会意识到其周围物理环境中发生的情况。</span><span class="sxs-lookup"><span data-stu-id="19552-183">Users experience a digital environment, and are unaware of what occurs in the physical environment around them.</span></span>

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="19552-184">下一个发现检查点</span><span class="sxs-lookup"><span data-stu-id="19552-184">Next Discovery Checkpoint</span></span>

<span data-ttu-id="19552-185">如果你按安排的[发现之旅](get-started-with-mr.md)操作，则你正在了解混合现实的基本知识。</span><span class="sxs-lookup"><span data-stu-id="19552-185">If you're following the [discovery journey](get-started-with-mr.md) we've laid out, you're in the midst of exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="19552-186">从这里，你可以进入下一基本主题：</span><span class="sxs-lookup"><span data-stu-id="19552-186">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="19552-187">什么是全息图？</span><span class="sxs-lookup"><span data-stu-id="19552-187">What is a hologram?</span></span>](hologram.md)
