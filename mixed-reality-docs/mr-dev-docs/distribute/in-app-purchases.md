---
title: 应用内购买
description: 了解如何在混合现实应用中使用 2D XAML 视图和 stock Windows 操作系统弹出窗口进行应用内购买。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 应用内购买，hololens，XAML，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: dfc5a0cfcc7a4d63147a753c8892d65dfae5e495
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582952"
---
# <a name="in-app-purchases"></a><span data-ttu-id="f341e-104">应用内购买</span><span class="sxs-lookup"><span data-stu-id="f341e-104">In-app purchases</span></span>

<span data-ttu-id="f341e-105">HoloLens 支持应用内购买，但有一些工作需要进行设置。</span><span class="sxs-lookup"><span data-stu-id="f341e-105">In-app purchases are supported in HoloLens, but there's some work to set them up.</span></span>

<span data-ttu-id="f341e-106">若要在应用购买功能中使用，你必须：</span><span class="sxs-lookup"><span data-stu-id="f341e-106">To use the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="f341e-107">创建 XAML [2d 视图](../design/app-views.md) 以显示为一个石板</span><span class="sxs-lookup"><span data-stu-id="f341e-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="f341e-108">切换到它以激活放置，这会使沉浸式视图</span><span class="sxs-lookup"><span data-stu-id="f341e-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="f341e-109">调用 API： await [CurrentApp. RequestProductPurchaseAsync ( "DurableItemIAPName" ) ;](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="f341e-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="f341e-110">此 API 将显示 "常用 Windows 操作系统" 弹出窗口，其中显示了应用内购买名称、说明和价格。</span><span class="sxs-lookup"><span data-stu-id="f341e-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="f341e-111">然后，用户可以选择 "购买选项"。</span><span class="sxs-lookup"><span data-stu-id="f341e-111">The user can then choose purchase options.</span></span> <span data-ttu-id="f341e-112">操作完成后，应用将需要显示 UI，这允许用户切换回其 [沉浸式视图](../design/app-views.md)。</span><span class="sxs-lookup"><span data-stu-id="f341e-112">Once the action is completed, the app will need to present UI, which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="f341e-113">对于面向基于桌面的 Windows Mixed Reality 沉浸式耳机的应用程序，无需在调用 RequestProductPurchaseAsync API 之前手动切换到 XAML 视图。</span><span class="sxs-lookup"><span data-stu-id="f341e-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it isn't required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>