---
title: 应用内购买
description: 混合现实应用支持应用内购买，但有一些工作需要对它们进行设置。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 应用内购买，hololens
ms.openlocfilehash: 7174fe555322216b7e547055aaaf7879c01d8f23
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677342"
---
# <a name="in-app-purchases"></a><span data-ttu-id="0a56e-104">应用内购买</span><span class="sxs-lookup"><span data-stu-id="0a56e-104">In-app purchases</span></span>

<span data-ttu-id="0a56e-105">HoloLens 中支持应用内购买，但有一些工作需要进行设置。</span><span class="sxs-lookup"><span data-stu-id="0a56e-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="0a56e-106">若要利用应用购买功能，你必须：</span><span class="sxs-lookup"><span data-stu-id="0a56e-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="0a56e-107">创建 XAML [2d 视图](../design/app-views.md) 以显示为一个石板</span><span class="sxs-lookup"><span data-stu-id="0a56e-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="0a56e-108">切换到它以激活放置，这会使沉浸式视图</span><span class="sxs-lookup"><span data-stu-id="0a56e-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="0a56e-109">调用 API： await [CurrentApp. RequestProductPurchaseAsync ( "DurableItemIAPName" ) ;](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="0a56e-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="0a56e-110">此 API 将显示 "常用 Windows 操作系统" 弹出窗口，其中显示了应用内购买名称、说明和价格。</span><span class="sxs-lookup"><span data-stu-id="0a56e-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="0a56e-111">然后，用户可以选择 "购买选项"。</span><span class="sxs-lookup"><span data-stu-id="0a56e-111">The user can then choose purchase options.</span></span> <span data-ttu-id="0a56e-112">操作完成后，应用将需要显示允许用户切换回其 [沉浸式视图](../design/app-views.md)的 UI。</span><span class="sxs-lookup"><span data-stu-id="0a56e-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="0a56e-113">对于面向基于桌面的 Windows Mixed Reality 沉浸式耳机的应用程序，无需在调用 RequestProductPurchaseAsync API 之前手动切换到 XAML 视图。</span><span class="sxs-lookup"><span data-stu-id="0a56e-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
