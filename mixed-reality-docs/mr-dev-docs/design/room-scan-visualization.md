---
title: 房间扫描可视化
description: 需要空间映射的应用程序使用设备跨时间和跨会话收集数据。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，应用模式，设计，HoloLens，房间扫描，空间映射，网格，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens
ms.openlocfilehash: f4ec072c8fde8d3e7e390bd837116a8262bac38b
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848254"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="64670-104">房间扫描可视化</span><span class="sxs-lookup"><span data-stu-id="64670-104">Room scan visualization</span></span>

<span data-ttu-id="64670-105">需要空间映射的应用程序依赖于设备跨时间和跨会话收集数据。</span><span class="sxs-lookup"><span data-stu-id="64670-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="64670-106">映射数据的完整性和质量取决于许多因素，包括用户的探索量、自浏览以来经过的时间，以及设备和门等对象是否在设备扫描区域后移动。</span><span class="sxs-lookup"><span data-stu-id="64670-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="64670-107">为了确保有用的空间映射数据，应用程序开发人员有多种选择：</span><span class="sxs-lookup"><span data-stu-id="64670-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="64670-108">依赖于可能已收集的内容。</span><span class="sxs-lookup"><span data-stu-id="64670-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="64670-109">此数据最初可能是不完整的。</span><span class="sxs-lookup"><span data-stu-id="64670-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="64670-110">要求用户使用布隆手势进入 Windows Mixed Reality 主页，并浏览他们希望用于体验的领域。</span><span class="sxs-lookup"><span data-stu-id="64670-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="64670-111">他们可以使用分流来确认设备是否知道所有必要的区域。</span><span class="sxs-lookup"><span data-stu-id="64670-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="64670-112">在自己的应用程序中生成自定义浏览体验。</span><span class="sxs-lookup"><span data-stu-id="64670-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="64670-113">在所有这些情况下，系统会存储浏览过程中收集的实际数据，而应用程序无需执行此操作。</span><span class="sxs-lookup"><span data-stu-id="64670-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="64670-114">设备支持</span><span class="sxs-lookup"><span data-stu-id="64670-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="64670-115"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="64670-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="64670-116"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="64670-116"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="64670-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="64670-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="64670-118">房间扫描可视化</span><span class="sxs-lookup"><span data-stu-id="64670-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="64670-119">✔️</span><span class="sxs-lookup"><span data-stu-id="64670-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="64670-120">构建自定义扫描体验</span><span class="sxs-lookup"><span data-stu-id="64670-120">Building a custom scanning experience</span></span>

<span data-ttu-id="64670-121">应用程序可以在体验开始时分析空间映射数据，判断他们是否希望用户执行额外的步骤来提高其完整性和质量。</span><span class="sxs-lookup"><span data-stu-id="64670-121">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="64670-122">如果分析表明质量应该提高，开发人员应提供一种可视化对象，使其在世界上叠加以指示：</span><span class="sxs-lookup"><span data-stu-id="64670-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="64670-123">用户附近的用户总数需要成为体验的一部分</span><span class="sxs-lookup"><span data-stu-id="64670-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="64670-124">用户应在何处着手改善数据</span><span class="sxs-lookup"><span data-stu-id="64670-124">Where the user should go to improve data</span></span>

<span data-ttu-id="64670-125">用户不知道什么是 "良好" 扫描。</span><span class="sxs-lookup"><span data-stu-id="64670-125">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="64670-126">如果要求评估扫描– flatness、与实际墙壁的距离等，则需要显示或告知要查找的内容。</span><span class="sxs-lookup"><span data-stu-id="64670-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="64670-127">开发人员应实现一个反馈循环，其中包括在扫描或浏览阶段刷新空间映射数据。</span><span class="sxs-lookup"><span data-stu-id="64670-127">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="64670-128">在许多情况下，最好告诉用户需要执行哪些操作才能获得必要的扫描质量。</span><span class="sxs-lookup"><span data-stu-id="64670-128">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="64670-129">例如，查看天花板，查看家具等。</span><span class="sxs-lookup"><span data-stu-id="64670-129">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="64670-130">缓存与连续空间映射</span><span class="sxs-lookup"><span data-stu-id="64670-130">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="64670-131">空间映射数据是最繁重的数据源应用程序可以使用的数据源。</span><span class="sxs-lookup"><span data-stu-id="64670-131">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="64670-132">若要避免性能问题（如丢弃的帧或断断续续），应仔细地使用此数据。</span><span class="sxs-lookup"><span data-stu-id="64670-132">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="64670-133">在体验期间进行的活动扫描可能既有益又有不利，因此你需要根据经验决定要使用哪种方法。</span><span class="sxs-lookup"><span data-stu-id="64670-133">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="64670-134">缓存空间映射</span><span class="sxs-lookup"><span data-stu-id="64670-134">Cached spatial mapping</span></span>

<span data-ttu-id="64670-135">如果缓存空间映射数据，应用程序通常会拍摄空间映射数据的快照，并在体验期间使用此快照。</span><span class="sxs-lookup"><span data-stu-id="64670-135">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="64670-136">**权益**</span><span class="sxs-lookup"><span data-stu-id="64670-136">**Benefits**</span></span>
* <span data-ttu-id="64670-137">降低了系统的系统开销，同时体验的性能大幅提高，并使 cpu 性能大幅提高。</span><span class="sxs-lookup"><span data-stu-id="64670-137">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="64670-138">由于空间数据中的更改不会中断，因此更简单的主要体验实现。</span><span class="sxs-lookup"><span data-stu-id="64670-138">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="64670-139">对于物理学、图形和其他用途的空间数据的任何 post 处理，只需一次。</span><span class="sxs-lookup"><span data-stu-id="64670-139">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="64670-140">**弊端**</span><span class="sxs-lookup"><span data-stu-id="64670-140">**Drawbacks**</span></span>
* <span data-ttu-id="64670-141">实际对象或人员的移动不会由缓存数据反映。</span><span class="sxs-lookup"><span data-stu-id="64670-141">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="64670-142">例如，应用程序可能会在现在关闭时考虑门处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="64670-142">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="64670-143">可能会有更多的应用程序内存来维护数据的缓存版本。</span><span class="sxs-lookup"><span data-stu-id="64670-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="64670-144">此方法的一个很好的例子是受控环境或表顶级游戏。</span><span class="sxs-lookup"><span data-stu-id="64670-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="64670-145">连续空间映射</span><span class="sxs-lookup"><span data-stu-id="64670-145">Continuous spatial mapping</span></span>

<span data-ttu-id="64670-146">某些应用程序可能依赖于继续扫描以刷新空间映射数据。</span><span class="sxs-lookup"><span data-stu-id="64670-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="64670-147">**权益**</span><span class="sxs-lookup"><span data-stu-id="64670-147">**Benefits**</span></span>
* <span data-ttu-id="64670-148">无需在应用程序中提前构建单独的扫描或浏览体验。</span><span class="sxs-lookup"><span data-stu-id="64670-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="64670-149">尽管有一些延迟，但现实世界对象的移动可能会反映出来。</span><span class="sxs-lookup"><span data-stu-id="64670-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="64670-150">**弊端**</span><span class="sxs-lookup"><span data-stu-id="64670-150">**Drawbacks**</span></span>
* <span data-ttu-id="64670-151">实现主要体验的复杂性更高。</span><span class="sxs-lookup"><span data-stu-id="64670-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="64670-152">额外的图形和物理学处理可能产生的开销，因为需要对这些系统进行增量引入。</span><span class="sxs-lookup"><span data-stu-id="64670-152">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="64670-153">高功率、热量和 CPU 影响。</span><span class="sxs-lookup"><span data-stu-id="64670-153">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="64670-154">此方法的一种很好的情况是，全息影像应与移动对象进行交互，例如，地面驱动器上的一只是处于打开或关闭状态的全息汽车。</span><span class="sxs-lookup"><span data-stu-id="64670-154">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="64670-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64670-155">See also</span></span>

* [<span data-ttu-id="64670-156">空间映射</span><span class="sxs-lookup"><span data-stu-id="64670-156">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="64670-157">坐标系统</span><span class="sxs-lookup"><span data-stu-id="64670-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="64670-158">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="64670-158">Spatial sound design</span></span>](spatial-sound-design.md)
