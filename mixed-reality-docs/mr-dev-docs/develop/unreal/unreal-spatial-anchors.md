---
title: Unreal 中的本地空间定位点
description: Unreal 中空间定位点使用指南
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, 空间定位点
ms.openlocfilehash: d223c451cbbf0fb4e2cc1392394d2fe771ec8069
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91697158"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="118ee-104">Unreal 中的本地空间定位点</span><span class="sxs-lookup"><span data-stu-id="118ee-104">Local Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="118ee-105">概述</span><span class="sxs-lookup"><span data-stu-id="118ee-105">Overview</span></span>

<span data-ttu-id="118ee-106">空间定位点用于在应用程序会话之间保存真实世界空间中的全息影像。</span><span class="sxs-lookup"><span data-stu-id="118ee-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="118ee-107">这些是通过 Unreal 以 ARPin 的形式出现的，并保存在 HoloLens 定位点存储中以便在未来会话中加载。</span><span class="sxs-lookup"><span data-stu-id="118ee-107">These get surfaced through Unreal as **ARPin** s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> <span data-ttu-id="118ee-108">当没有 Internet 连接时，本地定位点是理想的备用方案。</span><span class="sxs-lookup"><span data-stu-id="118ee-108">Local anchors are ideal as a fallback when there is no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="118ee-109">本地定位点存储在设备上，而 Azure 空间定位点存储在云中。</span><span class="sxs-lookup"><span data-stu-id="118ee-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="118ee-110">如果你想要使用 Azure 云服务来存储定位点，我们有一个文档可指导你如何集成 [Azure 空间定位点](unreal-azure-spatial-anchors.md)。</span><span class="sxs-lookup"><span data-stu-id="118ee-110">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="118ee-111">请注意，你可在同一项目中使用本地定位点和 Azure 定位点，不会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="118ee-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="118ee-112">检查定位点存储</span><span class="sxs-lookup"><span data-stu-id="118ee-112">Checking the anchor store</span></span>

<span data-ttu-id="118ee-113">在保存或加载定位点之前，需要检查定位点存储是否已准备就绪。</span><span class="sxs-lookup"><span data-stu-id="118ee-113">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="118ee-114">在定位点存储准备就绪之前，调用任何 HoloLens 定位点函数都不会成功。</span><span class="sxs-lookup"><span data-stu-id="118ee-114">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![空间定位点存储准备就绪](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="118ee-116">保存定位点</span><span class="sxs-lookup"><span data-stu-id="118ee-116">Saving anchors</span></span>

<span data-ttu-id="118ee-117">一旦应用程序的一个组件需要固定到世界，它可以按照以下顺序保存到定位点存储：</span><span class="sxs-lookup"><span data-stu-id="118ee-117">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![空间定位点保存](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="118ee-119">细分如下：</span><span class="sxs-lookup"><span data-stu-id="118ee-119">Breaking this down:</span></span>
1. <span data-ttu-id="118ee-120">在已知位置生成 Actor。</span><span class="sxs-lookup"><span data-stu-id="118ee-120">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="118ee-121">使用该位置和基于 Actor 的类的名称创建 ARPin。</span><span class="sxs-lookup"><span data-stu-id="118ee-121">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="118ee-122">将 Actor 添加到 ARPin并将引脚保存到 HoloLens 定位点存储。</span><span class="sxs-lookup"><span data-stu-id="118ee-122">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="118ee-123">选择的定位点名称必须是唯一的，因此在本示例中是当前时间戳。</span><span class="sxs-lookup"><span data-stu-id="118ee-123">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="118ee-124">如果定位点成功保存到定位点存储，则可以在 HoloLens 设备门户的“系统”>“映射管理器”>“设备上已保存的定位点文件”下检查定位点。</span><span class="sxs-lookup"><span data-stu-id="118ee-124">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device** .</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="118ee-125">加载定位点</span><span class="sxs-lookup"><span data-stu-id="118ee-125">Loading anchors</span></span>

<span data-ttu-id="118ee-126">当应用程序启动时，可以使用以下蓝图将组件还原到其定位点位置：</span><span class="sxs-lookup"><span data-stu-id="118ee-126">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![空间定位点加载](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="118ee-128">细分如下：</span><span class="sxs-lookup"><span data-stu-id="118ee-128">Breaking this down:</span></span>
1. <span data-ttu-id="118ee-129">循环访问定位点存储中的所有定位点。</span><span class="sxs-lookup"><span data-stu-id="118ee-129">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="118ee-130">按标识生成 Actor。</span><span class="sxs-lookup"><span data-stu-id="118ee-130">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="118ee-131">将该 Actor 从定位点存储固定到 ARPin。</span><span class="sxs-lookup"><span data-stu-id="118ee-131">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="118ee-132">必须按标识生成 Actor，这一点很重要，因为定位点负责根据全息影像的保存位置在世界中重新定位全息影像。</span><span class="sxs-lookup"><span data-stu-id="118ee-132">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="118ee-133">因此，此处添加的任何变形都将增加定位点的偏移量。</span><span class="sxs-lookup"><span data-stu-id="118ee-133">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="118ee-134">还将查询定位点 ID，以便根据定位点的保存名称来生成不同的 Actor。</span><span class="sxs-lookup"><span data-stu-id="118ee-134">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="118ee-135">删除定位点</span><span class="sxs-lookup"><span data-stu-id="118ee-135">Removing anchors</span></span> 

<span data-ttu-id="118ee-136">完成定位点后，可以使用“从 WMRAnchor 存储中删除 ARPin”和“从 WMRAnchor 存储中删除所有 ARPin”组件来清除单个定位点或整个定位点存储 。</span><span class="sxs-lookup"><span data-stu-id="118ee-136">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![空间定位点删除](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="118ee-138">请记住，空间定位点仍处于测试阶段，因此，请务必查看是否有更新的信息和功能。</span><span class="sxs-lookup"><span data-stu-id="118ee-138">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="118ee-139">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="118ee-139">Next Development Checkpoint</span></span>

<span data-ttu-id="118ee-140">如果你遵循我们规划的 Unreal 开发检查点历程，则你处于探索 MRTK 核心构建基块的过程之中。</span><span class="sxs-lookup"><span data-stu-id="118ee-140">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="118ee-141">从这里，你可以进入下一个构建基块：</span><span class="sxs-lookup"><span data-stu-id="118ee-141">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="118ee-142">Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="118ee-142">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)

<span data-ttu-id="118ee-143">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="118ee-143">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="118ee-144">HoloLens 摄像头</span><span class="sxs-lookup"><span data-stu-id="118ee-144">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="118ee-145">你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="118ee-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="118ee-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="118ee-146">See also</span></span>
* [<span data-ttu-id="118ee-147">Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="118ee-147">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="118ee-148">空间定位点</span><span class="sxs-lookup"><span data-stu-id="118ee-148">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="118ee-149">坐标系统</span><span class="sxs-lookup"><span data-stu-id="118ee-149">Coordinate systems</span></span>](../../design/coordinate-systems.md)
