---
title: Unreal 中的本地空间定位点
description: 了解如何在 Unreal 混合现实应用程序中使用、保存和管理空间定位点。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, 空间定位点, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: d44610ea0632dbc93941096007e60e4ae7be53e1
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009977"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="3f1d2-104">Unreal 中的本地空间定位点</span><span class="sxs-lookup"><span data-stu-id="3f1d2-104">Local Spatial Anchors in Unreal</span></span>

<span data-ttu-id="3f1d2-105">空间定位点以 ARPin 的形式在应用程序会话之间保存真实空间中的全息影像。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-105">Spatial anchors save holograms in real-world space between application sessions as **ARPin** s.</span></span> <span data-ttu-id="3f1d2-106">ARPin 保存在 HoloLens 的定位点存储中后，便可以在以后的会话中加载，当未连接 Internet 时，这就是理想的备用选项。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-106">Once saved in the HoloLens' anchor store, ARPin's can be loaded in future sessions and are an ideal fallback option when there's no internet connectivity.</span></span>

> [!NOTE]
> <span data-ttu-id="3f1d2-107">UE 4.25 中的定位点函数在 4.26 版中已过时，应替换为更新的函数。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-107">Anchor functions from UE 4.25 are obsolete in 4.26 and should be replaced with newer ones.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="3f1d2-108">本地定位点存储在设备上，而 Azure 空间定位点存储在云中。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-108">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="3f1d2-109">如果你想要使用 Azure 云服务来存储定位点，我们有一个文档可指导你如何集成 [Azure 空间定位点](unreal-azure-spatial-anchors.md)。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-109">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="3f1d2-110">请注意，你可在同一项目中使用本地定位点和 Azure 定位点，不会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-110">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="3f1d2-111">检查定位点存储</span><span class="sxs-lookup"><span data-stu-id="3f1d2-111">Checking the anchor store</span></span>

<span data-ttu-id="3f1d2-112">在保存或加载定位点之前，需要检查定位点存储是否已准备就绪。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-112">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="3f1d2-113">在定位点存储准备就绪之前，调用任何 HoloLens 定位点函数都不会成功。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-113">Calling any of the HoloLens anchor functions before the anchor store is ready won't succeed.</span></span>  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a><span data-ttu-id="3f1d2-114">保存定位点</span><span class="sxs-lookup"><span data-stu-id="3f1d2-114">Saving anchors</span></span>

<span data-ttu-id="3f1d2-115">一旦应用程序具有需要固定到世界的组件，就可以按以下顺序将其保存到定位点存储中：</span><span class="sxs-lookup"><span data-stu-id="3f1d2-115">Once the application has a component you need to pin to the world, it can be saved to the anchor store with the following sequence:</span></span> 

[!INCLUDE[](includes/tabs-sa-2.md)]

<span data-ttu-id="3f1d2-116">细分如下：</span><span class="sxs-lookup"><span data-stu-id="3f1d2-116">Breaking this down:</span></span>
1. <span data-ttu-id="3f1d2-117">在已知位置生成 Actor。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-117">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="3f1d2-118">使用该位置和基于 Actor 的类的名称创建 ARPin。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-118">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="3f1d2-119">将 Actor 添加到 ARPin并将引脚保存到 HoloLens 定位点存储。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-119">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="3f1d2-120">选择的定位点名称必须是唯一的，因此在本示例中是当前时间戳。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-120">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="3f1d2-121">如果定位点成功保存到定位点存储，则可以在 HoloLens 设备门户的“系统”>“映射管理器”>“设备上已保存的定位点文件”下看到定位点。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-121">If the anchor is successfully saved to the anchor store, you can see it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="3f1d2-122">加载定位点</span><span class="sxs-lookup"><span data-stu-id="3f1d2-122">Loading anchors</span></span>

<span data-ttu-id="3f1d2-123">当应用程序启动时，可以使用以下蓝图将组件还原到其定位点位置：</span><span class="sxs-lookup"><span data-stu-id="3f1d2-123">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

[!INCLUDE[](includes/tabs-sa-3.md)]

<span data-ttu-id="3f1d2-124">细分如下：</span><span class="sxs-lookup"><span data-stu-id="3f1d2-124">Breaking this down:</span></span>
1. <span data-ttu-id="3f1d2-125">循环访问定位点存储中的所有定位点。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-125">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="3f1d2-126">按标识生成 Actor。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-126">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="3f1d2-127">将该 Actor 从定位点存储固定到 ARPin。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-127">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="3f1d2-128">必须按标识生成 Actor，这一点很重要，因为定位点负责根据全息影像的保存位置在世界中重新定位全息影像。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-128">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="3f1d2-129">因此，此处添加的任何变形都将增加定位点的偏移量。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-129">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="3f1d2-130">还将查询定位点 ID，以便根据定位点的保存名称来生成不同的 Actor。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-130">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="3f1d2-131">删除定位点</span><span class="sxs-lookup"><span data-stu-id="3f1d2-131">Removing anchors</span></span> 

<span data-ttu-id="3f1d2-132">完成定位点后，可以使用“从 WMRAnchor 存储中删除 ARPin”和“从 WMRAnchor 存储中删除所有 ARPin”组件来清除单个定位点或整个定位点存储 。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-132">When you're done with an anchor, you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> <span data-ttu-id="3f1d2-133">请记住，空间定位点仍处于测试阶段，因此，请务必查看是否有更新的信息和功能。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-133">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="3f1d2-134">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="3f1d2-134">Next Development Checkpoint</span></span>

<span data-ttu-id="3f1d2-135">如果你遵循我们规划的 Unreal 开发历程，则你处于探索 MRTK 核心基础知识的过程之中。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-135">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="3f1d2-136">从这里，你可以继续了解下一部分基础知识：</span><span class="sxs-lookup"><span data-stu-id="3f1d2-136">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="3f1d2-137">Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="3f1d2-137">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)

<span data-ttu-id="3f1d2-138">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="3f1d2-138">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3f1d2-139">HoloLens 摄像头</span><span class="sxs-lookup"><span data-stu-id="3f1d2-139">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="3f1d2-140">你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="3f1d2-140">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f1d2-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f1d2-141">See also</span></span>

* [<span data-ttu-id="3f1d2-142">Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="3f1d2-142">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="3f1d2-143">空间定位点</span><span class="sxs-lookup"><span data-stu-id="3f1d2-143">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="3f1d2-144">坐标系统</span><span class="sxs-lookup"><span data-stu-id="3f1d2-144">Coordinate systems</span></span>](../../design/coordinate-systems.md)
