---
title: 手部物理扩展服务
description: description 手部物理扩展服务。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 401a9d31ed3fbbe0c3e02cb95ffebb024f882fd9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143429"
---
# <a name="hand-physics-extension-services"></a>手部物理扩展服务

手部物理服务支持严格的人体碰撞事件，以及与手部表达的交互。

## <a name="getting-started-with-hand-physics-extension-service"></a>手部物理扩展服务入门

将手部物理服务添加到扩展服务列表中，并使用默认配置文件。

启用后，使用任何碰撞体的 IsTrigger 属性接收来自所有 10 位数字（如果 (）的碰撞) 。

### <a name="prerequisites"></a>先决条件

- 已启用扩展服务
- 将适当的预制名分配到手指/手部。

## <a name="recommendations"></a>建议

虽然服务默认为"默认"层，但建议为 HandPhysics 对象使用单独的层。 否则，可能有不需要的碰撞和/或不准确的光线广播。
