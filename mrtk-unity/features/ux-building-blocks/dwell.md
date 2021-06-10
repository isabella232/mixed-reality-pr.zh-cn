---
title: 停留
description: 停留交互
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: 停留，Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 18e69f001c8989234d1b75fb713796f079cacbdf
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647751"
---
# <a name="dwell"></a>停留

![停留英雄](../images/dwell/MRTK_UX_Dwell.png)

打印头和停留在某个人正忙于处理其他任务的情况下非常有用。 当语音不是100% 可靠或由于环境或社交限制而可用时，此功能也很有用。
MRTK 的停留示例演示了具有可配置的响应时间和视觉反馈的不同类型的 UI 组件。

有关设计建议，请参阅 [打印头和停留指导原则](/windows/mixed-reality/design/gaze-and-dwell-head) 。

## <a name="dwell-scripts"></a>停留脚本

- **DwellHandler**：将停留模态添加到 UI 目标。
- **DwellStateType**：停留处理程序的状态。
- **DwellUnityEvent**：停留事件的 Unity 事件。 包含指针引用。
- **BaseDwellPressableButton** ：触发 PressableButtonHoloLens2 prototyping 中的 OnClick () 事件的脚本 `Interactable` 。
- **ToggleDwellPressableButton** ：此脚本 `_BorderWidth` `dwellVisualImage` 使用 MRTK 标准着色器修改的属性。

## <a name="dwell-profiles"></a>停留配置文件
停留 **处理程序** 使用停留配置文件来配置各种阈值。
- **ButtonDwellProfile**
- **InstandDwellProfile**
- **DwellProfileWithDecay**

## <a name="prefabs"></a>Prototyping

这些 prototyping 是 HoloLens 2 样式 pressable 按钮 prototyping 的变体，它具有支持停留交互的附加组件。

- **PressableButtonHoloLens2_Dwell. prefab**
- **PressableButtonHoloLens2_32x96_Dwell. prefab**
- **PressableButtonHoloLens2ToggleDwell. prefab**
- **PressableButtonHoloLens2Toggle_32x96_Dwell. prefab**

这些 prototyping 具有附加的 backplate 组件 **QuadDwellVisual** ，用于可视化停留输入状态。 已分配 **HolographicBackPlateDwellVisual** 材料。 **ToggleDwellPressableButton** 将更新 MRTK 标准着色器的 **_BorderWidth** 属性，以可视化停留在的输入。

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a>示例场景

您可以在场景中找到示例 `DwellExample` 。 示例场景显示了容量耗尽 UI 示例和 Unity UI 示例。

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a>另请参阅

- [**按钮**](button.md)
- [**可交互**](interactable.md)
