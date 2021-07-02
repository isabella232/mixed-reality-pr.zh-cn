---
title: 体验设置
description: 有关 MRTK 的不同体验设置的文档
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: ab3a449b064d4a1c8f2bf76154f7a25c688693e1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177356"
---
# <a name="experience-settings"></a>体验设置

为混合现实创建 UI 的难题之一是跨不同体验。 通过 MRTK，你可以 `Target Experience Scale` 为场景设置和， `Content Offset` 将配置以下各项，以适合目标规模。

- 混合现实场景内容
- 边界系统

  ![MRTK 配置文件中的体验设置](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a>目标体验规模

**目标体验规模** 指定了经验的设计环境。 它可以采用以下值。

* *OrientationOnly* -一种只利用耳机方向且重心对齐的体验。 坐标系统原点位于 head 级别。
* 已 *就位设计，旨在* 实现现有用途。 坐标系统原点在楼层级。
* 持续-为静止使用而 *设计的体验*。 坐标系统原点在楼层级。
* *房间* -一种体验，旨在支持在房间内移动。 坐标系统原点在楼层级。
* *世界* -一种经验，旨在利用和迁移到现实世界。 坐标系统原点位于 head 级别。

## <a name="content-offset"></a>内容偏移

此参数指定当 **对齐类型** 设置为 **与体验规模一致** 时，将 [混合现实场景内容](scene-content.md)偏移的地面的高度
