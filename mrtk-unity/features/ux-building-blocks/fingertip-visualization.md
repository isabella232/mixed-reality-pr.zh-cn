---
title: 手指可视化效果
description: MRTK 中的手指提示可视化概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 指尖
ms.openlocfilehash: af23fdb9b618e276b7442405e54b7dccd141e4ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177529"
---
# <a name="fingertip-visualization"></a>手指可视化效果

![手指可视化效果主](../images/fingertip/MRTK_FingertipVisualization_Main.png)

触指可让用户识别与目标对象的距离。 环形状视觉对象根据从手指到对象的距离调整其大小。 手指可视化效果主要由 `FingerCursor` (Assets/MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab)  (和脚本) （生成为一个 *CursorePointer* 的光标预制）控制。 可视化效果的其他组件包括 *ProximityLight* 脚本和 *MixedRealityStandard 着色* 器。

## <a name="how-to-use-the-fingertip-visualization"></a>如何使用手指可视化效果

默认情况下，手指可视化效果在配置为生成 FingerCursor 的任何 Unity 场景中都工作。 FingerCursor 的生成发生在 *DefaultMixedRealityToolkitConfigurationProfile* 下：

*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile >用户 > FingerCursor*

从较高层面看，手指可视化效果的工作原理是使用邻近光在接受邻近光的任何附近表面上绘制彩色渐变。 然后，手指光标会查找任何附近的可交互表面（由父级确定）以在手指向表面移动时将手指环与表面 `IMixedRealityNearPointer(s)` 对齐。 当手指接近表面时，手指环也使用 MixedRealityStandard 着色器圆角属性进行动态动画处理。

## <a name="example-scene"></a>示例场景

可以在几乎任何使用手部表达的场景中找到手部可视化示例，但在 [HandInteractionExample 场景中非常突出](../example-scenes/hand-interaction-examples.md)。

![手指可视化状态](../images/fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a>检查器属性

**FingerCursor** 许多手指光标属性都继承自基游标类。 重要属性包括驱动 MixedRealityStandard 着色器中手指环动画的远/近表面边距和宽度。 对于其他属性，请将鼠标悬停在检查器工具提示上。

<img src="../images/fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Cursor Inspector">

**ProximityLight** 邻近光设置控制光在靠近和远离表面时的外观。 中间、中间和外部颜色控制光的渐变外观，并可根据应用程序的调色板进行自定义定制。 请注意，颜色是 HDR (高动态范围) ，允许用户将邻近光变亮为高于 1 的值。 对于其他属性，请将鼠标悬停在检查器工具提示上。

**MixedRealityStandard 着色器** MixedRealityStandard 着色器用于 MRTK 中的许多效果。 对于手部可视化来说，重要的两个设置是"Near Fade"和"Proximity Light"。 "近淡出"允许对象在照相机或光线靠近时淡入/淡出。 请确保选中"光"，以允许邻近光驱动淡 (，而不是相机) 。 可以反转"Fade Begin"和"Fade Complete"的值来反转淡入淡出。 检查"邻近感应光"，了解希望邻近光变亮的任何表面。 对于其他属性，请将鼠标悬停在检查器工具提示上。

<img src="../images/fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Shader Inspector">
