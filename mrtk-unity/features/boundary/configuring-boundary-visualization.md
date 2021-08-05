---
title: 配置边界可视化
description: 在 MRTK 中配置边界系统的详细信息
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 边界系统，
ms.openlocfilehash: 29ffe7826d797fd32387fab42f24232f98ab283740848b7fce928718f95f0fc9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211538"
---
# <a name="configuring-boundary-visualization"></a>配置边界可视化

边界 *可视化配置文件* 提供用于为边界系统配置视觉外观和其他相关参数的选项。 边界可视化效果附加到场景中的混合现实 Playspace 对象，并随用户进行远程传送。

## <a name="general-settings"></a>常规设置

![边界可视化常规设置](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a>边界高度

边界高度指示应在平面上方呈现边界上限的距离。 默认值为 3 米。

## <a name="floor-settings"></a>楼层设置

![边界可视化效果设置](../images/boundary/BoundaryVisualizationFloorSettings.png)

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

指示是否创建播放区域矩形并添加到场景中。 默认值为 true。

**材料**

指示在创建播放区域对象时应该使用的材料。

**物理层**

应在其上设置播放区域层。 默认值为 Ignore *Raycast* 层。

## <a name="tracked-area-settings"></a>跟踪的区域设置

![边界可视化跟踪区域设置](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

**显示**

指示是否创建跟踪区域轮廓并添加到场景中。 默认值为 true。

**材料**

指示在创建跟踪区域轮廓时应该使用的材料。

**物理层**

应设置所跟踪区域所基于的层。 默认值为 Ignore *Raycast* 层。

## <a name="boundary-wall-settings"></a>边界墙设置

![边界可视化边界墙设置](../images/boundary/BoundaryVisualizationWallSettings.png)

**显示**

指示是否创建边界墙平面并添加到场景中。 默认值为 false。

**材料**

指示在创建边界墙平面时应该使用的材料。

**物理层**

应设置边界墙的层。 默认值为 Ignore *Raycast* 层。

> [!NOTE]
> 将边界墙组件设置为"忽略光线广播"之外的物理层可能会阻止用户与场景中的对象交互。

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
