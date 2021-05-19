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
# <a name="lost-tracking-visualization"></a>丢失跟踪可视化效果

![丢失跟踪](../images/lost-tracking/LostTrackingVisualization.jpg)

丢失跟踪扩展服务为丢失的跟踪状态提供 HoloLens shell 样式的动画视觉对象。

## <a name="how-to-use-lost-tracking-extensions"></a>如何使用丢失的跟踪扩展

在 MRTK 配置文件中，将 **"丢失跟踪服务"** 添加到"扩展"。 分配 **DefaultLostTrackingServiceProfile，** 其中包括 **LostTrackingVisualPrefab**。

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
