---
title: Unity 中的共享体验
description: 在 Unity 应用程序的多个用户之间共享相同的全息影像。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共享、定位、WorldAnchor、MR 共享250、WorldAnchorTransferBatch、SpatialPerception、Azure、Azure 空间锚，ASA，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 46588f84c39a48e22147d0fc246ceb8d5ee7c47d
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010087"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="1bb9a-104">Unity 中的共享体验</span><span class="sxs-lookup"><span data-stu-id="1bb9a-104">Shared experiences in Unity</span></span>

<span data-ttu-id="1bb9a-105">共享体验允许多个用户，每个用户都有自己的 HoloLens、iOS 或 Android 设备，共同查看同一个全息影像，并与之交互。</span><span class="sxs-lookup"><span data-stu-id="1bb9a-105">A shared experience lets multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram.</span></span> <span data-ttu-id="1bb9a-106">全息影像通过空间锚点共享定位在空间的固定点上。</span><span class="sxs-lookup"><span data-stu-id="1bb9a-106">Holograms are positioned at a fixed point in space through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="1bb9a-107">Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="1bb9a-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="1bb9a-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a>创建支持云的持久空间锚，你的应用可以在多个 HoloLens、IOS 和 Android 设备上查找。</span><span class="sxs-lookup"><span data-stu-id="1bb9a-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="1bb9a-109">通过在多个设备之间共享公用空间定位点，每个用户都可以查看相对于同一物理位置中的定位点呈现的内容。</span><span class="sxs-lookup"><span data-stu-id="1bb9a-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span> 

<span data-ttu-id="1bb9a-110">你还可以将 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a> 用于每个 HoloLens、IOS 和 Android 设备上的异步全息影像。</span><span class="sxs-lookup"><span data-stu-id="1bb9a-110">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="1bb9a-111">通过共享持久云空间锚点，多个设备可以在一段时间内观察到相同的持久全息图，即使这些设备同时不存在。</span><span class="sxs-lookup"><span data-stu-id="1bb9a-111">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="1bb9a-112">若要开始在 Unity 中构建共享体验，请尝试执行5分钟的 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间锚点 Unity 快速入门</a>。</span><span class="sxs-lookup"><span data-stu-id="1bb9a-112">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="1bb9a-113">设置 Azure 空间锚定后，可以 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中创建和定位锚</a>。</span><span class="sxs-lookup"><span data-stu-id="1bb9a-113">Once Azure Spatial Anchors is set up, you can <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="1bb9a-114">本地定位点传输</span><span class="sxs-lookup"><span data-stu-id="1bb9a-114">Local anchor transfers</span></span>

<span data-ttu-id="1bb9a-115">在不能使用 Azure 空间锚点的情况下， [本地定位点传输](../../out-of-scope/local-anchor-transfers-in-unity.md) 允许一个 hololens 设备导出一个定位点，以便另一个 hololens 可以导入它。</span><span class="sxs-lookup"><span data-stu-id="1bb9a-115">In situations where you can't use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor so that a second HoloLens can import it.</span></span>  <span data-ttu-id="1bb9a-116">IOS 和 Android 设备不支持此方法，提供比 Azure 空间定位点更少的定位回调。</span><span class="sxs-lookup"><span data-stu-id="1bb9a-116">This approach is not supported on iOS and Android devices, and provides less robust anchor recall than Azure Spatial Anchors.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="1bb9a-117">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="1bb9a-117">Next Development Checkpoint</span></span>

<span data-ttu-id="1bb9a-118">如果遵循我们所说的 Unity 开发旅程，就是探索混合现实平台功能和 Api。</span><span class="sxs-lookup"><span data-stu-id="1bb9a-118">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="1bb9a-119">从这里，你可以继续学习下一部分：</span><span class="sxs-lookup"><span data-stu-id="1bb9a-119">From here, you can continue to the next section:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1bb9a-120">可定位相机</span><span class="sxs-lookup"><span data-stu-id="1bb9a-120">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="1bb9a-121">或直接跳到在设备或模拟器上部署应用：</span><span class="sxs-lookup"><span data-stu-id="1bb9a-121">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1bb9a-122">部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳机</span><span class="sxs-lookup"><span data-stu-id="1bb9a-122">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="1bb9a-123">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#3-platform-capabilities-and-apis)。</span><span class="sxs-lookup"><span data-stu-id="1bb9a-123">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="1bb9a-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1bb9a-124">See also</span></span>
* [<span data-ttu-id="1bb9a-125">混合现实中的共享体验</span><span class="sxs-lookup"><span data-stu-id="1bb9a-125">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="1bb9a-126"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位点</a></span><span class="sxs-lookup"><span data-stu-id="1bb9a-126"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="1bb9a-127"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">用于 Unity 的 Azure 空间定位点 SDK</a></span><span class="sxs-lookup"><span data-stu-id="1bb9a-127"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
