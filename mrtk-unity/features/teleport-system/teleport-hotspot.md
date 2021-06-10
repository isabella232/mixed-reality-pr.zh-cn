---
title: Teleport 热点
description: 有关 MRTK 中 Teleport 热点组件的文档
author: RogPodge
ms.author: roliu
ms.date: 03/25/2021
ms.localizationpriority: medium
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， Teleport 系统， Teleport 热点
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 2d6160570b43ca931d46f4ec04c604b53b18d731
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647044"
---
# <a name="teleport-hotspot"></a>Teleport 热点

远程端口热点是可添加到 gameobject 的组件，以确保用户在远程传送到该位置时处于特定位置和方向。

## <a name="usage"></a>使用情况

### <a name="how-to-create-a-teleport-hotspot"></a>如何创建远程端口热点

若要创建远程端口热点，将 TeleportHotspot 组件添加到也具有碰撞体组件的对象。 

![Teleport 热点组件](../images/teleport/TeleportHotspotComponent.png)

现在，在 TeleportHotspot 上定向时，远程端口指针的指示器将更改颜色。 通过热点完成远程端口操作后，用户将远程传送到 TeleportHotspot 的中心。

如果选中替代方向标志，则用户的方向将匹配远程端口热点的方向。

![Teleport 热点示例](../images/teleport/TeleportHotspotExample.gif)
