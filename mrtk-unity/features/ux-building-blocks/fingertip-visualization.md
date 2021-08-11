---
title: 指尖可视化
description: MRTK 中手指可视化的概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，手指
ms.openlocfilehash: 1df1740692a2c24213f34ffa6e52c135c7e7d14f96e7d99668feab82f879f756
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193284"
---
# <a name="fingertip-visualization"></a>指尖可视化

![手指可视化主要](../images/fingertip/MRTK_FingertipVisualization_Main.png)

手指 affordance 可帮助用户识别与目标对象之间的距离。 环形形状视觉对象根据从手指到对象的距离调整其大小。 手指可视化主要由 `FingerCursor` (资产/MRTK/SDK/功能/UX/prototyping/cursor/FingerCursor prefab)  (和脚本) ，该脚本将作为 *prefab* 的 cursor PokePointer 生成。 可视化对象的其他组件包括 *ProximityLight* 脚本和 *MixedRealityStandard* 着色器。

## <a name="how-to-use-the-fingertip-visualization"></a>如何使用手指可视化

默认情况下，手指可视化将在配置为生成 FingerCursor 的任何 Unity 场景中运行。 FingerCursor 的生成发生在 *DefaultMixedRealityToolkitConfigurationProfile* 下的中：

*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > PokePointer > FingerCursor*

在高级别上，手指可视化效果的工作方式是使用邻近光源在任何接受近程光源的邻近表面上投影彩色渐变。 然后，手指光标查找任何附近的种不可交互图面（由父级确定 `IMixedRealityNearPointer(s)` ），以便在手指向图面移动时，将手指环与表面对齐。 手指的一种方法是，使用 MixedRealityStandard 着色器的圆角属性动态动态显示手指环。

## <a name="example-scene"></a>示例场景

你可以在几乎所有适用于有表述的动手操作的场景中找到手指可视化示例，但在 [HandInteractionExample 场景](../example-scenes/hand-interaction-examples.md)中会突出。

![手指可视化状态](../images/fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a>检查器属性

**FingerCursor** 许多 finger 游标属性都是从基游标类继承的。 重要属性包括在 MixedRealityStandard 着色器中驱动手指环形动画的远/近处面边距和宽度。 对于其他属性，请将鼠标悬停在检查器工具提示上。

<img src="../images/fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Cursor Inspector">

**ProximityLight** 邻近感应光源设置控制光线在表面附近的外观。 居中、中间和外颜色控制光线的渐变外观，可以根据应用程序的调色板进行定制定制。 请注意，颜色是 HDR (高动态范围) ，以使用户能够将近程光源变亮到一个以上的值。 对于其他属性，请将鼠标悬停在检查器工具提示上。

**MixedRealityStandard 着色器** MixedRealityStandard 着色器用于 MRTK 中的许多效果。 手指可视化对象的两个设置非常重要，即 "接近淡化" 和 "邻近感应"。 近乎淡化允许对象以相机的形式淡入/淡出，或者接近它们。 请确保选中 "灯"，以允许近程光源来驱动淡化 (而不是相机) 。 可以反转 "淡出开始" 和 "淡出完成" 的值，以反转淡化。 对于想要使邻近感应变亮的任何表面，请选中 "邻近感应"。 对于其他属性，请将鼠标悬停在检查器工具提示上。

<img src="../images/fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Shader Inspector">
