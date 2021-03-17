---
title: Unity 中的空间锚
description: 了解如何在 Unity 混合现实应用程序中创建、存储和提取空间锚。
author: hferrone
ms.author: v-hferrone
ms.date: 03/16/2021
ms.topic: article
keywords: Unity，空间锚，定位存储，HoloLens，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 665cdae56f271a061972922af835ff64bdc35496
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623617"
---
# <a name="spatial-anchors-in-unity"></a><span data-ttu-id="ba3f9-104">Unity 中的空间锚</span><span class="sxs-lookup"><span data-stu-id="ba3f9-104">Spatial Anchors in Unity</span></span>

<span data-ttu-id="ba3f9-105">空间锚点在应用程序会话之间将全息区保存在实际空间内。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-105">Spatial anchors save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="ba3f9-106">保存到 HoloLens 的锚定存储中后，可以在不同的会话中找到并加载它们，在没有 internet 连接的情况下是理想的备选方案。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-106">Once saved in the HoloLens' anchor store, they can be found and loaded in different sessions and are an ideal fallback when there's no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba3f9-107">本地定位点存储在设备上，而 Azure 空间定位点存储在云中。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-107">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="ba3f9-108">如果你想要使用 Azure 云服务来存储定位点，我们有一个文档可指导你如何集成 [Azure 空间定位点](../mixed-reality-cloud-services.md#azure-spatial-anchors)。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-108">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span></span> <span data-ttu-id="ba3f9-109">请注意，你可在同一项目中使用本地定位点和 Azure 定位点，不会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-109">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="understanding-anchors"></a><span data-ttu-id="ba3f9-110">了解定位点</span><span class="sxs-lookup"><span data-stu-id="ba3f9-110">Understanding Anchors</span></span>

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a><span data-ttu-id="ba3f9-111">使用 AnchorStore</span><span class="sxs-lookup"><span data-stu-id="ba3f9-111">Using the AnchorStore</span></span>

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="ba3f9-112">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="ba3f9-112">Next Development Checkpoint</span></span>

<span data-ttu-id="ba3f9-113">如果遵循我们所说的 Unity 开发检查点旅程，就是探索混合现实核心构建基块的过程。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-113">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="ba3f9-114">从这里，你可以继续了解下一部分基础知识：</span><span class="sxs-lookup"><span data-stu-id="ba3f9-114">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ba3f9-115">空间映射</span><span class="sxs-lookup"><span data-stu-id="ba3f9-115">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="ba3f9-116">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="ba3f9-116">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ba3f9-117">共享体验</span><span class="sxs-lookup"><span data-stu-id="ba3f9-117">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="ba3f9-118">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-118">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba3f9-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba3f9-119">See Also</span></span>
* [<span data-ttu-id="ba3f9-120">空间锚点持久性</span><span class="sxs-lookup"><span data-stu-id="ba3f9-120">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="ba3f9-121"><a href="/azure/spatial-anchors" target="_blank">Azure 空间定位点</a></span><span class="sxs-lookup"><span data-stu-id="ba3f9-121"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="ba3f9-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">用于 Unity 的 Azure 空间定位点 SDK</a></span><span class="sxs-lookup"><span data-stu-id="ba3f9-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
* [<span data-ttu-id="ba3f9-123">体验规模</span><span class="sxs-lookup"><span data-stu-id="ba3f9-123">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="ba3f9-124">空间阶段</span><span class="sxs-lookup"><span data-stu-id="ba3f9-124">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="ba3f9-125">Unity 中的失跟</span><span class="sxs-lookup"><span data-stu-id="ba3f9-125">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="ba3f9-126">空间定位点</span><span class="sxs-lookup"><span data-stu-id="ba3f9-126">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="ba3f9-127">Unity 中的共享体验</span><span class="sxs-lookup"><span data-stu-id="ba3f9-127">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)