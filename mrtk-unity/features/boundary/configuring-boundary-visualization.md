---
title: 配置边界可视化
description: 用于在 MRTK 中配置边界系统的详细信息
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，边界系统，
ms.openlocfilehash: 0f1a9edd9f9a31e7ba20f630406b299909a4864c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121245"
---
# <a name="configuring-the-boundary-visualization"></a>配置边界可视化

*边界可视化配置文件* 提供了为边界系统配置视觉美观和其他相关参数的选项。 边界可视化效果连接到场景中的 Mixed Reality Playspace 对象，并与用户一起传送。

## <a name="general-settings"></a>常规设置

![边界可视化常规设置](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a>边界高度

边界高度指示应呈现边界上限的地面上的距离。 默认值为3米。

## <a name="floor-settings"></a>楼层设置

![边界视觉对象设置](../images/boundary/BoundaryVisualizationFloorSettings.png)

**显示**

指示是否要创建楼层面并将其添加到场景中。 默认值为 true。

**材料**

指示在创建地面平面时应使用的材料。

**规模**

指示要创建的地面平面的大小（以米为单位）。 默认刻度为3米 x 3 米正方形。

**物理层**

应在其上设置地面平面的层。 默认值为 *默认* 层。

## <a name="play-area-settings"></a>播放区域设置

![边界可视化播放区域设置](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

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

指示是否要创建边界上限平面，并将其添加到场景中。 默认值为 false。

**材料**

指示在创建边界上限平面时应使用的材料。

**物理层**

应在其上设置边界壁的层。 默认值为 *Ignore Raycast* 层。

> [!NOTE]
> 将边界上限组件设置为除 *Ignore Raycast* 以外的物理层可能会阻止用户与场景中的对象进行交互。

## <a name="see-also"></a>另请参阅

- [边界 API 文档](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [边界系统](boundary-system-getting-started.md)
