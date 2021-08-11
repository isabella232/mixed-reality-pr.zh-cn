---
title: 体验设置
description: 有关 MRTK 的不同体验设置的文档
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 19d812ccfa9c0317e40dee2b7d03220848782cef955ba859a150b4f4adc8aa99
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203240"
---
# <a name="experience-settings"></a>体验设置

为混合现实创建 UI 的其中一个难题是跨不同体验保持一致。 使用 MRTK，你可以为场景设置 和 ，将以下内容配置为适合 `Target Experience Scale` `Content Offset` 目标规模的行为。

- 混合现实场景内容
- 边界系统

  ![体验设置 MRTK 配置文件中的配置](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a>目标体验缩放

" **目标体验** 规模"指定设计体验的环境。 它可以接受以下值。

* *OrientationOnly* - 一种仅利用头戴显示设备方向且与力对齐的体验。 坐标系统原点位于头级别。
* *下* 级 - 专为自己使用而设计的体验。 坐标系原点在楼层级别。
* *站* 式 - 专为固定固定使用而设计的体验。 坐标系原点在楼层级别。
* *房间* - 旨在支持整个房间移动的体验。 坐标系原点在楼层级别。
* *世界* - 旨在利用和移动物理世界的体验。 坐标系统原点位于头级别。

## <a name="content-offset"></a>内容偏移量

当对齐类型设置为"与体验刻度对齐"时 [](scene-content.md)，此参数指定楼层上方的高度以偏移混合现实 **场景内容**
