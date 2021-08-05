---
title: 丢失跟踪服务
description: MRTK 中的 LostTracking 服务概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 3b12378780a9d57217b88de9fdcbc97d0f94c57200efd20fd30054b31aee669f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212629"
---
# <a name="lost-tracking-service"></a>丢失跟踪服务

![丢失跟踪](../images/lost-tracking/LostTrackingVisualization.jpg)

丢失跟踪扩展服务为丢失跟踪状态提供 HoloLens shell 样式动画视觉对象。

## <a name="how-to-use-lost-tracking-extensions"></a>如何使用丢失跟踪扩展

在 MRTK 配置文件中，向扩展添加 **丢失的跟踪服务** 。 分配包含 **LostTrackingVisualPrefab** 的 **DefaultLostTrackingServiceProfile** 。

<img src="../images/lost-tracking/LostTracking_Extensions.png" width="550" alt="Lost Tracking Extension">
