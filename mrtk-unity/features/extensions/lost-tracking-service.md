---
title: 丢失跟踪服务
description: MRTK 中的 LostTracking 服务概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 96090b05c60cfaa6ff5d8c5e1dc7a58cc2658b71
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144528"
---
# <a name="lost-tracking-visualization"></a><span data-ttu-id="fa285-104">丢失跟踪可视化效果</span><span class="sxs-lookup"><span data-stu-id="fa285-104">Lost tracking visualization</span></span>

![丢失跟踪](../images/lost-tracking/LostTrackingVisualization.jpg)

<span data-ttu-id="fa285-106">丢失跟踪扩展服务为丢失的跟踪状态提供 HoloLens shell 样式的动画视觉对象。</span><span class="sxs-lookup"><span data-stu-id="fa285-106">Lost Tracking Extension Service provides HoloLens shell style animated visual for the lost tracking state.</span></span>

## <a name="how-to-use-lost-tracking-extensions"></a><span data-ttu-id="fa285-107">如何使用丢失的跟踪扩展</span><span class="sxs-lookup"><span data-stu-id="fa285-107">How to use lost tracking extensions</span></span>

<span data-ttu-id="fa285-108">在 MRTK 配置文件中，将 **"丢失跟踪服务"** 添加到"扩展"。</span><span class="sxs-lookup"><span data-stu-id="fa285-108">In MRTK Profile, add **Lost Tracking Service** to the Extensions.</span></span> <span data-ttu-id="fa285-109">分配 **DefaultLostTrackingServiceProfile，** 其中包括 **LostTrackingVisualPrefab**。</span><span class="sxs-lookup"><span data-stu-id="fa285-109">Assign **DefaultLostTrackingServiceProfile** which includes **LostTrackingVisualPrefab**.</span></span>

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
