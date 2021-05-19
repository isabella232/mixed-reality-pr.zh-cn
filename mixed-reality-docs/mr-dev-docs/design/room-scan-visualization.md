---
title: 房间扫描可视化
description: 需要空间映射的应用程序使用设备跨时间和跨会话收集数据。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，应用模式，设计，HoloLens，房间扫描，空间映射，网格，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens
ms.openlocfilehash: 8c7f1ae95cfdb520e84835f7fd5d78522e62e341
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143613"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="f0d81-104">房间扫描可视化</span><span class="sxs-lookup"><span data-stu-id="f0d81-104">Room scan visualization</span></span>

<span data-ttu-id="f0d81-105">需要空间映射的应用程序依赖于设备跨时间和跨会话收集数据。</span><span class="sxs-lookup"><span data-stu-id="f0d81-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="f0d81-106">映射数据的完整性和质量取决于许多因素，包括用户的探索量、自浏览以来经过的时间，以及设备和门等对象是否在设备扫描区域后移动。</span><span class="sxs-lookup"><span data-stu-id="f0d81-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="f0d81-107">为了确保有用的空间映射数据，应用程序开发人员有多种选择：</span><span class="sxs-lookup"><span data-stu-id="f0d81-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="f0d81-108">依赖于可能已收集的内容。</span><span class="sxs-lookup"><span data-stu-id="f0d81-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="f0d81-109">此数据最初可能是不完整的。</span><span class="sxs-lookup"><span data-stu-id="f0d81-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="f0d81-110">要求用户使用布隆手势进入 Windows Mixed Reality 主页，并浏览他们希望用于体验的领域。</span><span class="sxs-lookup"><span data-stu-id="f0d81-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="f0d81-111">他们可以使用分流来确认设备是否知道所有必要的区域。</span><span class="sxs-lookup"><span data-stu-id="f0d81-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="f0d81-112">在自己的应用程序中生成自定义浏览体验。</span><span class="sxs-lookup"><span data-stu-id="f0d81-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="f0d81-113">在所有这些情况下，系统会存储浏览过程中收集的实际数据，而应用程序无需执行此操作。</span><span class="sxs-lookup"><span data-stu-id="f0d81-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span> <span data-ttu-id="f0d81-114">若要查看房间扫描视觉对象的运行情况，请查看下面 [的设计全息影像-空间感知]() 视频演示：</span><span class="sxs-lookup"><span data-stu-id="f0d81-114">If you'd like to see room scan visualization in action, check out our [Designing Holograms - Spatial Awareness]() video demo below:</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

## <a name="device-support"></a><span data-ttu-id="f0d81-115">设备支持</span><span class="sxs-lookup"><span data-stu-id="f0d81-115">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f0d81-116"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="f0d81-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f0d81-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f0d81-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f0d81-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="f0d81-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f0d81-119">房间扫描可视化</span><span class="sxs-lookup"><span data-stu-id="f0d81-119">Room scan visualization</span></span></td>
        <td><span data-ttu-id="f0d81-120">✔️</span><span class="sxs-lookup"><span data-stu-id="f0d81-120">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="f0d81-121">构建自定义扫描体验</span><span class="sxs-lookup"><span data-stu-id="f0d81-121">Building a custom scanning experience</span></span>

<span data-ttu-id="f0d81-122">应用程序可以在体验开始时分析空间映射数据，判断他们是否希望用户执行额外的步骤来提高其完整性和质量。</span><span class="sxs-lookup"><span data-stu-id="f0d81-122">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="f0d81-123">如果分析表明质量应该提高，开发人员应提供一种可视化对象，使其在世界上叠加以指示：</span><span class="sxs-lookup"><span data-stu-id="f0d81-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="f0d81-124">用户附近的用户总数需要成为体验的一部分</span><span class="sxs-lookup"><span data-stu-id="f0d81-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="f0d81-125">用户应在何处着手改善数据</span><span class="sxs-lookup"><span data-stu-id="f0d81-125">Where the user should go to improve data</span></span>

<span data-ttu-id="f0d81-126">用户不知道什么是 "良好" 扫描。</span><span class="sxs-lookup"><span data-stu-id="f0d81-126">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="f0d81-127">如果系统要求他们评估扫描（平面度、距离实际墙的距离等）时，需要显示或告知他们要查找什么。</span><span class="sxs-lookup"><span data-stu-id="f0d81-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="f0d81-128">开发人员应实现反馈循环，包括在扫描或探索阶段刷新空间映射数据。</span><span class="sxs-lookup"><span data-stu-id="f0d81-128">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="f0d81-129">在许多情况下，最好告诉用户需要执行哪些操作才能获得必要的扫描质量。</span><span class="sxs-lookup"><span data-stu-id="f0d81-129">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="f0d81-130">例如，查看上限、查看装饰后，等等。</span><span class="sxs-lookup"><span data-stu-id="f0d81-130">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="f0d81-131">缓存空间映射与连续空间映射</span><span class="sxs-lookup"><span data-stu-id="f0d81-131">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="f0d81-132">空间映射数据是应用程序可以使用的最重数据源数据。</span><span class="sxs-lookup"><span data-stu-id="f0d81-132">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="f0d81-133">若要避免性能问题（如丢弃的帧或断点）问题，应谨慎使用此数据。</span><span class="sxs-lookup"><span data-stu-id="f0d81-133">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="f0d81-134">在体验期间主动扫描既有利又有害，因此你需要根据体验决定使用哪种方法。</span><span class="sxs-lookup"><span data-stu-id="f0d81-134">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="f0d81-135">缓存的空间映射</span><span class="sxs-lookup"><span data-stu-id="f0d81-135">Cached spatial mapping</span></span>

<span data-ttu-id="f0d81-136">如果有缓存的空间映射数据，应用程序通常会拍摄空间映射数据的快照，并在此体验期间使用此快照。</span><span class="sxs-lookup"><span data-stu-id="f0d81-136">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="f0d81-137">**优点**</span><span class="sxs-lookup"><span data-stu-id="f0d81-137">**Benefits**</span></span>
* <span data-ttu-id="f0d81-138">降低运行体验时系统开销，从而显著提升功率、热性能和 CPU 性能。</span><span class="sxs-lookup"><span data-stu-id="f0d81-138">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="f0d81-139">主体验的更简单实现，因为它不会因空间数据更改而中断。</span><span class="sxs-lookup"><span data-stu-id="f0d81-139">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="f0d81-140">空间数据的任何后期处理（用于物理、图形和其他目的）的一次成本。</span><span class="sxs-lookup"><span data-stu-id="f0d81-140">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="f0d81-141">**缺点**</span><span class="sxs-lookup"><span data-stu-id="f0d81-141">**Drawbacks**</span></span>
* <span data-ttu-id="f0d81-142">实际对象或人员的移动不会由缓存的数据反映。</span><span class="sxs-lookup"><span data-stu-id="f0d81-142">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="f0d81-143">例如，应用程序可能会认为门在现在关闭时打开。</span><span class="sxs-lookup"><span data-stu-id="f0d81-143">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="f0d81-144">可能更多的应用程序内存用于维护数据的缓存版本。</span><span class="sxs-lookup"><span data-stu-id="f0d81-144">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="f0d81-145">此方法的一个好情况是受控环境或表顶级游戏。</span><span class="sxs-lookup"><span data-stu-id="f0d81-145">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="f0d81-146">连续空间映射</span><span class="sxs-lookup"><span data-stu-id="f0d81-146">Continuous spatial mapping</span></span>

<span data-ttu-id="f0d81-147">某些应用程序可能依赖于继续扫描来刷新空间映射数据。</span><span class="sxs-lookup"><span data-stu-id="f0d81-147">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="f0d81-148">**优点**</span><span class="sxs-lookup"><span data-stu-id="f0d81-148">**Benefits**</span></span>
* <span data-ttu-id="f0d81-149">无需在应用程序中提前构建单独的扫描或浏览体验。</span><span class="sxs-lookup"><span data-stu-id="f0d81-149">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="f0d81-150">尽管有一些延迟，但现实世界对象的移动可能会反映出来。</span><span class="sxs-lookup"><span data-stu-id="f0d81-150">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="f0d81-151">**弊端**</span><span class="sxs-lookup"><span data-stu-id="f0d81-151">**Drawbacks**</span></span>
* <span data-ttu-id="f0d81-152">实现主要体验的复杂性更高。</span><span class="sxs-lookup"><span data-stu-id="f0d81-152">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="f0d81-153">额外的图形和物理学处理可能产生的开销，因为需要对这些系统进行增量引入。</span><span class="sxs-lookup"><span data-stu-id="f0d81-153">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="f0d81-154">高功率、热量和 CPU 影响。</span><span class="sxs-lookup"><span data-stu-id="f0d81-154">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="f0d81-155">此方法的一种很好的情况是，全息影像应与移动对象进行交互，例如，地面驱动器上的一只是处于打开或关闭状态的全息汽车。</span><span class="sxs-lookup"><span data-stu-id="f0d81-155">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0d81-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0d81-156">See also</span></span>

* [<span data-ttu-id="f0d81-157">空间映射</span><span class="sxs-lookup"><span data-stu-id="f0d81-157">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="f0d81-158">坐标系统</span><span class="sxs-lookup"><span data-stu-id="f0d81-158">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="f0d81-159">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="f0d81-159">Spatial sound design</span></span>](spatial-sound-design.md)