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
# <a name="lost-tracking-service"></a>跟踪服务丢失

![丢失跟踪](../images/lost-tracking/LostTrackingVisualization.jpg)

丢失跟踪扩展服务HoloLens跟踪状态提供 shell 样式的动画视觉对象。

## <a name="how-to-use-lost-tracking-extensions"></a>如何使用丢失的跟踪扩展

在 MRTK 配置文件中，将 **"丢失跟踪服务"** 添加到"扩展"。 分配 **DefaultLostTrackingServiceProfile，** 其中包括 **LostTrackingVisualPrefab**。

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
