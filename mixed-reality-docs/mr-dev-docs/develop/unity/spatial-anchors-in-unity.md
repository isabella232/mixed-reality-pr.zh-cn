---
title: Unity 中的世界锁定和空间锚
description: 了解如何在 Unity 混合现实应用程序中使用全球锁定工具和空间锚。
author: hferrone
ms.author: v-hferrone
ms.date: 04/7/2021
ms.topic: article
keywords: Unity，空间锚，定位存储，HoloLens，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，世界锁定工具，全息影像
ms.openlocfilehash: 4fc982244a766bb34f15b356d608f2aad18f7a88
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528809"
---
# <a name="world-locking-and-spatial-anchors-in-unity"></a><span data-ttu-id="949f0-104">Unity 中的世界锁定和空间锚</span><span class="sxs-lookup"><span data-stu-id="949f0-104">World locking and spatial anchors in Unity</span></span>

![世界锁定工具英雄图像](images/wlt-img-01.jpeg)

<span data-ttu-id="949f0-106">在创建混合现实应用程序的过程中，你可以将你的全息影像固定在原地、与你一起移动，或者，在某些情况下，相对于其他全息影像的位置是很大的。</span><span class="sxs-lookup"><span data-stu-id="949f0-106">Getting your holograms to stay in place, move with you, or in some cases position themselves relative to other holograms is a big part of creating Mixed Reality applications.</span></span> <span data-ttu-id="949f0-107">本文将指导你使用全球锁定工具来完成我们推荐的解决方案，但我们还将介绍如何在 Unity 项目中手动设置空间锚。</span><span class="sxs-lookup"><span data-stu-id="949f0-107">This article will take you through our recommended solution using World Locking Tools, but we'll also cover manually setting up spatial anchors in your Unity projects.</span></span> <span data-ttu-id="949f0-108">在跳转到任何代码之前，请务必了解 Unity 如何在其自己的引擎中协调空间和定位点。</span><span class="sxs-lookup"><span data-stu-id="949f0-108">Before we jump into any code, it's important to understand how Unity handles coordinate space and anchors in its own engine.</span></span>

## <a name="world-scale-coordinate-systems"></a><span data-ttu-id="949f0-109">全球坐标系统</span><span class="sxs-lookup"><span data-stu-id="949f0-109">World-scale coordinate systems</span></span>

<span data-ttu-id="949f0-110">目前，编写游戏、数据可视化应用程序或虚拟现实应用时，典型的方法是建立一个绝对 **世界坐标系统** ，所有其他坐标都可以可靠地映射回。</span><span class="sxs-lookup"><span data-stu-id="949f0-110">Today, when writing games, data visualization apps, or virtual reality apps, the typical approach is to establish one absolute **world coordinate system** that all other coordinates can reliably map back to.</span></span> <span data-ttu-id="949f0-111">在该环境中，始终可以找到一个稳定的转换，用于定义该世界中任意两个对象之间的关系。</span><span class="sxs-lookup"><span data-stu-id="949f0-111">In that environment, you can always find a stable transform that defines a relationship between any two objects in that world.</span></span> <span data-ttu-id="949f0-112">如果未移动这些对象，则其相对转换始终保持不变。</span><span class="sxs-lookup"><span data-stu-id="949f0-112">If you didn't move those objects, their relative transforms would always remain the same.</span></span> <span data-ttu-id="949f0-113">在呈现纯粹的虚拟世界时，这种全局坐标系统很容易获得，在这种情况下，你可以提前了解所有几何。</span><span class="sxs-lookup"><span data-stu-id="949f0-113">This kind of global coordinate system is easy to get right when rendering a purely virtual world where you know all of the geometry in advance.</span></span> <span data-ttu-id="949f0-114">如今，房间内的 VR 应用通常建立此类绝对房间级坐标系统，并将其原点置于地面上。</span><span class="sxs-lookup"><span data-stu-id="949f0-114">Room-scale VR apps today typically establish this kind of absolute room-scale coordinate system with its origin on the floor.</span></span>

<span data-ttu-id="949f0-115">与此相反，untethered mixed reality 设备（如 HoloLens）对世界有动态的传感器驱动理解，随着用户的周围时间的推移而不断调整其知识，因为他们在一座建筑的整个楼层走出了很多时间。</span><span class="sxs-lookup"><span data-stu-id="949f0-115">In contrast, an untethered mixed reality device such as HoloLens has a dynamic sensor-driven understanding of the world, continuously adjusting its knowledge over time of the user's surroundings as they walk many meters across an entire floor of a building.</span></span> <span data-ttu-id="949f0-116">在全球范围内，如果你将所有全息影像都置于一个简单的硬坐标系中，则这些全息影像将最终偏移一段时间，无论是在世界上还是相对的。</span><span class="sxs-lookup"><span data-stu-id="949f0-116">In a world-scale experience, if you placed all your holograms in a naive rigid coordinate system, those holograms would end up drifting over time, either based on the world or relative to each other.</span></span>

<span data-ttu-id="949f0-117">例如，耳机当前可能相信世界上的两个位置相隔4米，然后在以后优化此理解，了解位置实际上是3.9 米。</span><span class="sxs-lookup"><span data-stu-id="949f0-117">For example, the headset may currently believe two locations in the world to be 4 meters apart, and then later refine that understanding, learning that the locations are in fact 3.9 meters apart.</span></span> <span data-ttu-id="949f0-118">如果这些全息影像最初在一个硬坐标系中相隔4米，则其中一个将始终从真实世界向下显示0.1 米。</span><span class="sxs-lookup"><span data-stu-id="949f0-118">If those holograms had initially been placed 4 meters apart in a single rigid coordinate system, one of them would then always appear 0.1 meters off from the real world.</span></span>

<span data-ttu-id="949f0-119">您可以手动将 **空间锚定** 到 Unity 中，以便在用户为移动设备时，在物理世界中维护全息影像的位置，但这 sacrifices 了虚拟世界内的自我一致性。</span><span class="sxs-lookup"><span data-stu-id="949f0-119">You can manually place **spatial anchors** in Unity to maintain a hologram's position in the physical world when the user is mobile - however, this sacrifices the self-consistency within the virtual world.</span></span> <span data-ttu-id="949f0-120">不同的定位点会不断地彼此移动，同时也会在全局坐标空间中移动。</span><span class="sxs-lookup"><span data-stu-id="949f0-120">Different anchors are constantly moving in relation to one another, and are also moving through the global coordinate space.</span></span> <span data-ttu-id="949f0-121">在此方案中，简单的任务（例如布局）变得困难且物理学模拟出现问题。</span><span class="sxs-lookup"><span data-stu-id="949f0-121">In this scenario, simple tasks like layout become difficult and physics simulation problematic.</span></span>

<span data-ttu-id="949f0-122">**世界上的锁定工具** 为您提供了这两种世界的最大优势，即在用户四处移动时，使用内部的空间锚点内部提供的稳定坐标系统。</span><span class="sxs-lookup"><span data-stu-id="949f0-122">**World Locking Tools** gets you the best of both worlds, stabilizing a single rigid coordinate system using an internal supply of spatial anchors spread throughout the virtual scene as the user moves around.</span></span> <span data-ttu-id="949f0-123">这些工具会分析照相机的坐标，并分析每个帧的空间锚。</span><span class="sxs-lookup"><span data-stu-id="949f0-123">The tools analyze the coordinates of the camera and those spatial anchors every frame.</span></span> <span data-ttu-id="949f0-124">不是更改世界上所有内容的坐标来补偿用户头坐标中的更正，而只是修复 head 的坐标。</span><span class="sxs-lookup"><span data-stu-id="949f0-124">Instead of changing the coordinates of everything in the world to compensate for the corrections in the coordinates of the user's head, the tools just fix the head's coordinates instead.</span></span>

## <a name="choosing-your-world-locking-approach"></a><span data-ttu-id="949f0-125">选择您的全球锁定方法</span><span class="sxs-lookup"><span data-stu-id="949f0-125">Choosing your world locking approach</span></span>

* <span data-ttu-id="949f0-126">**我们建议** 使用 **全球锁定工具** 来满足所有全息图定位需求。</span><span class="sxs-lookup"><span data-stu-id="949f0-126">**Our recommendation** is to use **World Locking Tools** for all your hologram positioning needs.</span></span> 
    * <span data-ttu-id="949f0-127">世界锁定工具提供了一个稳定的坐标系，可最大程度地减少虚拟和实际标记之间的明显不一致。</span><span class="sxs-lookup"><span data-stu-id="949f0-127">World Locking Tools provides a stable coordinate system that minimizes the visible inconsistencies between virtual and real world markers.</span></span> <span data-ttu-id="949f0-128">另一种方法是，它将整个场景与共享的锚池一起锁定，而不是使用该组自己的单独定位点锁定每组对象。</span><span class="sxs-lookup"><span data-stu-id="949f0-128">Put another way, it world-locks the entire scene with a shared pool of anchors, rather than locking each group of objects with the group's own individual anchor.</span></span>
* <span data-ttu-id="949f0-129">**对于使用 OpenXR 或 WINDOWS XR 插件的 Unity 2019/2020**，需要使用 **ARAnchorManager**</span><span class="sxs-lookup"><span data-stu-id="949f0-129">**For Unity 2019/2020 using OpenXR or the Windows XR Plugin**, you need to use **ARAnchorManager**</span></span>
* <span data-ttu-id="949f0-130">**对于较旧的 Unity 版本或 WSA** 项目，需要使用 **WorldAnchor**</span><span class="sxs-lookup"><span data-stu-id="949f0-130">**For older Unity versions or WSA** projects, you need to use **WorldAnchor**</span></span>

## <a name="setting-up-world-locking"></a><span data-ttu-id="949f0-131">设置世界锁定</span><span class="sxs-lookup"><span data-stu-id="949f0-131">Setting up world locking</span></span> 

[!INCLUDE[](includes/world-locking/world-locking-setup.md)]

## <a name="persistent-world-locking"></a><span data-ttu-id="949f0-132">持久世界锁定</span><span class="sxs-lookup"><span data-stu-id="949f0-132">Persistent world locking</span></span>

<span data-ttu-id="949f0-133">空间锚点在应用程序会话之间将全息区保存在实际空间内。</span><span class="sxs-lookup"><span data-stu-id="949f0-133">Spatial anchors save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="949f0-134">保存到 HoloLens 的锚定存储中后，可以在不同的会话中找到并加载它们，在没有 internet 连接的情况下是理想的备选方案。</span><span class="sxs-lookup"><span data-stu-id="949f0-134">Once saved in the HoloLens' anchor store, they can be found and loaded in different sessions and are an ideal fallback when there's no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="949f0-135">本地定位点存储在设备上，而 Azure 空间定位点存储在云中。</span><span class="sxs-lookup"><span data-stu-id="949f0-135">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="949f0-136">如果你想要使用 Azure 云服务来存储定位点，我们有一个文档可指导你如何集成 [Azure 空间定位点](../mixed-reality-cloud-services.md#azure-spatial-anchors)。</span><span class="sxs-lookup"><span data-stu-id="949f0-136">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span></span> <span data-ttu-id="949f0-137">请注意，你可在同一项目中使用本地定位点和 Azure 定位点，不会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="949f0-137">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

[!INCLUDE[](includes/world-locking/world-locking-persistence.md)]

## <a name="sharing-coordinate-spaces"></a><span data-ttu-id="949f0-138">共享坐标空间</span><span class="sxs-lookup"><span data-stu-id="949f0-138">Sharing coordinate spaces</span></span> 

<span data-ttu-id="949f0-139">如果要共享世界锁定的坐标空间，请查看我们的综合性 [共享体验文档](shared-experiences-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="949f0-139">If you want to share a world locked coordinate space, check out our comprehensive [shared experience documentation](shared-experiences-in-unity.md).</span></span>

<span data-ttu-id="949f0-140">请注意，世界锁定工具中尚不直接支持 Azure 空间锚点，因此共享体验将要求你手动创建空间锚。</span><span class="sxs-lookup"><span data-stu-id="949f0-140">Note that Azure Spatial Anchors is not yet supported directly within World Locking Tools, and so shared experiences will require you to manually create spatial anchors.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="949f0-141">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="949f0-141">Next Development Checkpoint</span></span>

<span data-ttu-id="949f0-142">如果遵循我们所说的 Unity 开发检查点旅程，就是探索混合现实核心构建基块的过程。</span><span class="sxs-lookup"><span data-stu-id="949f0-142">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="949f0-143">从这里，你可以继续了解下一部分基础知识：</span><span class="sxs-lookup"><span data-stu-id="949f0-143">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="949f0-144">空间映射</span><span class="sxs-lookup"><span data-stu-id="949f0-144">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="949f0-145">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="949f0-145">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="949f0-146">共享体验</span><span class="sxs-lookup"><span data-stu-id="949f0-146">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="949f0-147">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="949f0-147">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="949f0-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="949f0-148">See Also</span></span>
* [<span data-ttu-id="949f0-149">全球锁定工具简介</span><span class="sxs-lookup"><span data-stu-id="949f0-149">World Locking Tools introduction</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/IntroFAQ.html)
* [<span data-ttu-id="949f0-150">快速入门指南</span><span class="sxs-lookup"><span data-stu-id="949f0-150">Quickstart guides</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/QuickStart.html)
* [<span data-ttu-id="949f0-151">教程</span><span class="sxs-lookup"><span data-stu-id="949f0-151">Tutorials</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Samples/Tutorial/01_Minimal/01_Minimal.html)
* [<span data-ttu-id="949f0-152">示例</span><span class="sxs-lookup"><span data-stu-id="949f0-152">Samples</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/SampleApplications.html)
* [<span data-ttu-id="949f0-153">空间锚点持久性</span><span class="sxs-lookup"><span data-stu-id="949f0-153">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="949f0-154"><a href="/azure/spatial-anchors" target="_blank">Azure 空间定位点</a></span><span class="sxs-lookup"><span data-stu-id="949f0-154"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="949f0-155"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">用于 Unity 的 Azure 空间定位点 SDK</a></span><span class="sxs-lookup"><span data-stu-id="949f0-155"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
* [<span data-ttu-id="949f0-156">体验规模</span><span class="sxs-lookup"><span data-stu-id="949f0-156">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="949f0-157">空间阶段</span><span class="sxs-lookup"><span data-stu-id="949f0-157">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="949f0-158">Unity 中的失跟</span><span class="sxs-lookup"><span data-stu-id="949f0-158">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="949f0-159">空间定位点</span><span class="sxs-lookup"><span data-stu-id="949f0-159">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="949f0-160">Unity 中的共享体验</span><span class="sxs-lookup"><span data-stu-id="949f0-160">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
