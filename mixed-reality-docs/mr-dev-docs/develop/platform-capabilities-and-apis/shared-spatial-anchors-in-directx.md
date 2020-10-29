---
title: DirectX 中的共享空间定位点
description: 说明如何通过共享空间锚点来同步两个 HoloLens 设备。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens，同步，空间定位，传输，多人，查看，方案，演练，示例代码，Azure，Azure 空间锚，ASA
ms.openlocfilehash: 2d6485e46a9802e1ee7e5adc12d6e0d026c79ae9
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677358"
---
# <a name="shared-experiences-in-directx"></a><span data-ttu-id="1103a-104">DirectX 中的共享体验</span><span class="sxs-lookup"><span data-stu-id="1103a-104">Shared experiences in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="1103a-105">本文与旧版 WinRT 本机 Api 相关。</span><span class="sxs-lookup"><span data-stu-id="1103a-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="1103a-106">对于新的本机应用项目，建议使用 **[OPENXR API](../native/openxr-getting-started.md)** 。</span><span class="sxs-lookup"><span data-stu-id="1103a-106">For new native app projects, we recommend using the **[OpenXR API](../native/openxr-getting-started.md)** .</span></span>

<span data-ttu-id="1103a-107">共享体验是指多个用户，每个用户都有自己的 HoloLens、iOS 或 Android 设备，共同查看位于某个空间固定点的同一全息图并与之进行交互。</span><span class="sxs-lookup"><span data-stu-id="1103a-107">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="1103a-108">这是通过空间定位点共享来实现的。</span><span class="sxs-lookup"><span data-stu-id="1103a-108">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="1103a-109">Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="1103a-109">Azure Spatial Anchors</span></span>

<span data-ttu-id="1103a-110">你可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a> 来创建支持云的持久空间锚点，你的应用可以在多个 HoloLens、IOS 和 Android 设备上查找。</span><span class="sxs-lookup"><span data-stu-id="1103a-110">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="1103a-111">通过在多个设备之间共享公用空间定位点，每个用户都可以查看相对于同一物理位置中的定位点呈现的内容。</span><span class="sxs-lookup"><span data-stu-id="1103a-111">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="1103a-112">这可实现实时共享体验。</span><span class="sxs-lookup"><span data-stu-id="1103a-112">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="1103a-113">还可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间定位点</a>在 HoloLens、iOS 和 Android 设备上实现异步全息影像持久性。</span><span class="sxs-lookup"><span data-stu-id="1103a-113">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="1103a-114">通过共享持久的云空间定位点，多个设备可以随着时间推移观察相同的持久全息影像，即使这些设备没有同时出现，也是如此。</span><span class="sxs-lookup"><span data-stu-id="1103a-114">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="1103a-115">若要开始在 HoloLens 应用中构建共享体验，请尝试5分钟的 <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空间锚快速入门</a>。</span><span class="sxs-lookup"><span data-stu-id="1103a-115">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="1103a-116">启动并运行 Azure 空间锚点后，可以 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">在 HoloLens 上创建和查找锚</a>。</span><span class="sxs-lookup"><span data-stu-id="1103a-116">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="1103a-117">演练也适用于 <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> ，使你能够在所有设备上共享相同的定位标记。</span><span class="sxs-lookup"><span data-stu-id="1103a-117">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="1103a-118">本地定位点传输</span><span class="sxs-lookup"><span data-stu-id="1103a-118">Local anchor transfers</span></span>

<span data-ttu-id="1103a-119">在不能使用 Azure 空间锚点的情况下， [本地定位点传输](../../out-of-scope/local-anchor-transfers-in-directx.md) 允许一台 hololens 设备导出要由第二个 hololens 设备导入的定位点。</span><span class="sxs-lookup"><span data-stu-id="1103a-119">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-directx.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="1103a-120">请注意，此方法提供的定位回调比 Azure 空间定位点更少，并且不支持 iOS 和 Android 设备。</span><span class="sxs-lookup"><span data-stu-id="1103a-120">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="see-also"></a><span data-ttu-id="1103a-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="1103a-121">See also</span></span>
* [<span data-ttu-id="1103a-122">混合现实中的共享体验</span><span class="sxs-lookup"><span data-stu-id="1103a-122">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="1103a-123"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位点</a></span><span class="sxs-lookup"><span data-stu-id="1103a-123"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="1103a-124"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">用于 HoloLens 的 Azure 空间锚点 SDK</a></span><span class="sxs-lookup"><span data-stu-id="1103a-124"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchors SDK for HoloLens</a></span></span>