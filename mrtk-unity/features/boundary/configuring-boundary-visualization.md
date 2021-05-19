---
title: 配置边界可视化
description: 在 MRTK 中配置边界系统的详细信息
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 边界系统，
ms.openlocfilehash: 36717493107b129a7200dd3f912bcbdc3337b9a1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144491"
---
# <a name="configuring-the-boundary-visualization"></a>配置边界可视化效果

边界 *可视化配置文件* 提供用于为边界系统配置视觉外观和其他相关参数的选项。 边界可视化效果附加到场景中的混合现实 Playspace 对象，并随用户进行远程传送。

## <a name="general-settings"></a>常规设置

![边界可视化常规设置](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a>边界高度

边界高度指示应在平面上方呈现边界上限的距离。 默认值为 3 米。

## <a name="floor-settings"></a>楼层设置

![边界可视化楼层设置](../images/boundary/BoundaryVisualizationFloorSettings.png)

**显示**

指示是否创建地平面并添加到场景中。 默认值为 true。

**材料**

指示应在创建地平面时使用的材料。

**缩放**

指示要创建的地平面的大小（以米为单位）。 默认比例为 3 米 x 3 米正方形。

**物理层**

应在其上设置地平面的层。 默认值 *为默认层* 。

## <a name="play-area-settings"></a>播放区域设置

![边界可视化效果播放区域设置](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

**显示**

指示是否创建播放区域矩形并将其添加到场景中。 默认值为 true。

**材料**

指示创建播放区域对象时应使用的材料。

**物理层**

应在其上设置播放区域的层。 默认值为 *Ignore Raycast* 层。

## <a name="tracked-area-settings"></a>跟踪区域设置

![边界可视化跟踪区域设置](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

**显示**

指示是否创建跟踪区域的轮廓并将其添加到场景中。 默认值为 true。

**材料**

指示创建跟踪区域轮廓时应使用的材料。

**物理层**

应在其上设置跟踪区域的层。 默认值为 *Ignore Raycast* 层。

## <a name="boundary-wall-settings"></a>边界墙壁设置

![边界可视化边界墙壁设置](../images/boundary/BoundaryVisualizationWallSettings.png)

**显示**

指示是否要创建边界墙壁，并将其添加到场景中。 默认值为 false。

**材料**

指示在创建边界墙壁时应使用的材料。

**物理层**

应在其上设置边界壁的层。 默认值为 *Ignore Raycast* 层。

> [!NOTE]
> 将边界墙壁组件设置为除 *Ignore Raycast* 以外的物理层可能会阻止用户与场景中的对象进行交互。

## <a name="boundary-ceiling-settings"></a>边界上限设置

![边界可视化边界上限设置](../images/boundary/BoundaryVisualizationCeilingSettings.png)

**显示**

指示是否创建边界上限平面并添加到场景中。 默认值为 false。

**材料**

指示在创建边界上限平面时应该使用的材料。

**物理层**

应设置边界墙的层。 默认值为 Ignore *Raycast* 层。

> [!NOTE]
> 将边界上限组件设置为"忽略 *光线* 广播"之外的物理层可能会阻止用户与场景中的对象交互。

## <a name="see-also"></a>另请参阅

- [边界 API 文档](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [边界系统](boundary-system-getting-started.md)
