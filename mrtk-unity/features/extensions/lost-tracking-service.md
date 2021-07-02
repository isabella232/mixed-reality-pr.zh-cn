---
title: 跟踪服务丢失
description: MRTK 中的 LostTracking 服务概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 70274639326563b1f3c3a2061dcdbf824fd43709
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176226"
---
# <a name="lost-tracking-service"></a><span data-ttu-id="8087e-104">跟踪服务丢失</span><span class="sxs-lookup"><span data-stu-id="8087e-104">Lost tracking service</span></span>

![丢失跟踪](../images/lost-tracking/LostTrackingVisualization.jpg)

<span data-ttu-id="8087e-106">丢失跟踪扩展服务HoloLens跟踪状态提供 shell 样式的动画视觉对象。</span><span class="sxs-lookup"><span data-stu-id="8087e-106">Lost Tracking Extension Service provides HoloLens shell style animated visual for the lost tracking state.</span></span>

## <a name="how-to-use-lost-tracking-extensions"></a><span data-ttu-id="8087e-107">如何使用丢失的跟踪扩展</span><span class="sxs-lookup"><span data-stu-id="8087e-107">How to use lost tracking extensions</span></span>

<span data-ttu-id="8087e-108">在 MRTK 配置文件中，将 **"丢失跟踪服务"** 添加到"扩展"。</span><span class="sxs-lookup"><span data-stu-id="8087e-108">In MRTK Profile, add **Lost Tracking Service** to the Extensions.</span></span> <span data-ttu-id="8087e-109">分配 **DefaultLostTrackingServiceProfile，** 其中包括 **LostTrackingVisualPrefab**。</span><span class="sxs-lookup"><span data-stu-id="8087e-109">Assign **DefaultLostTrackingServiceProfile** which includes **LostTrackingVisualPrefab**.</span></span>

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
