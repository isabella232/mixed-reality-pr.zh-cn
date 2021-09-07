---
title: Button
description: 了解如何使用按钮触发即时操作，按钮是混合现实的基础组件之一。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合现实， 控件， 交互， ui， ux， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， HoloLens， MRTK， 混合现实 Toolkit， 按钮
ms.openlocfilehash: 4b3a9bda852c7a83ee603c3f2340d44f4be89f4d
ms.sourcegitcommit: 4f1697b11e5638db9bbd0bd7a671d846d54c6389
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/23/2021
ms.locfileid: "122682960"
---
# <a name="button"></a>Button

![Button](images/UX_Hero_Button.jpg)

按钮是混合现实中最基础和最重要的 UI 元素之一。 它允许用户触发即时操作。 由于混合现实中没有任何物理反馈，因此提供足够的视觉和音频反馈以提高用户的交互置信度至关重要。 

在HoloLens 2设计中，基于许多设计迭代、原型制作和用户研究，我们集成了多个视觉视觉元素和音频提示，以帮助用户在空白空间中进行深度感知和交互。 

## <a name="visual-affordances"></a>视觉视觉元素

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWJHgW]


:::row:::
    :::column:::
       ![显示邻近光效果的按钮](images/UX_Button_Affordance_ProximityLight.jpg)<br>
       **邻近感应灯**<br>
    :::column-end:::
    :::column:::
       ![选中的按钮，其中显示了焦点突出显示效果](images/UX_Button_Affordance_FocusHighlight.jpg)<br>
        **焦点突出显示**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![按下的按钮，显示压缩压缩效果](images/UX_Button_Affordance_Compression.jpg)<br>
       **压缩机**<br>
    :::column-end:::
    :::column:::
       ![按下的按钮，显示触发器脉冲效果](images/UX_Button_Affordance_Pulse.jpg)<br>
        **触发时脉冲**<br>
    :::column-end:::
:::row-end:::

<br>

## <a name="audio-cues"></a>音频提示

正确的音频反馈可以显著提高用户体验。 HoloLens 2按钮提供音频反馈来传达以下提示：
* **联系人开始**：触摸开始时播放声音 (近交互) 
* **接触端**：在触摸端播放声音 (交互) 
* **收缩开始**：在收缩时播放声音选择 (与凝视或光线进行) 
* **收缩端**：在收缩释放时播放声音 (与凝视或光线进行) 

<br>

---

:::row:::
    :::column:::
        ## <a name="voice-commandingbr"></a>语音命令<br>
        对于混合现实中的任意按钮，必须支持备用交互选项。 默认情况下，建议任何按钮都支持语音命令。 在HoloLens 2按钮设计中，我们在悬停状态期间提供工具提示以提高可发现性。
    :::column-end:::
        :::column:::
       ![语音输入](images/UX_Hero_VoiceCommand.jpg)<br>
        *图像：语音命令的工具提示*
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a>重设大小建议

为了确保可以轻松接触所有可交互对象，我们建议确保可交互对象满足基于其与用户的距离的最小大小。 可视角度通常以可视弧度度量。视觉角度基于用户眼睛与对象之间的距离并保持恒定，而目标的物理大小可能会随着用户距离的变化而更改。 若要根据与用户的距离确定对象的必要物理大小，请尝试使用如下可视角度 [计算器](https://elvers.us/perception/visualAngle/)。

下面是有关可交互内容的最小大小的建议。

### <a name="target-size-for-direct-hand-interaction"></a>直接手部交互的目标大小

| 距离 | 视角 | 大小 |
|---------|---------|---------|
| 45 cm  | 不小于 2° | 1.6 x 1.6 cm |

![直接手部交互的目标大小](images/TargetSizingNear.jpg)<br>
*直接手部交互的目标大小*

<br>

### <a name="target-size-for-buttons"></a>按钮的目标大小

创建用于直接交互的按钮时，我们建议使用更大的最小大小 3.2 x 3.2 cm，以确保有足够的空间来包含图标和可能的文本。

| 距离 | 最小大小 |
|---------|---------|
| 45 cm  | 3.2 x 3.2 cm |

![按钮的目标大小](images/TargetSizingButtons.png)<br>
*按钮的目标大小*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>手部射线或凝视交互的目标大小
| 距离 | 视角 | 大小 |
|---------|---------|---------|
| 2 m  | 不小于 1° | 3.5 x 3.5 cm |

![手部射线或凝视交互的目标大小](images/TargetSizingFar.jpg)<br>
*手部射线或凝视交互的目标大小*

<br>

---

## <a name="design-guidelines"></a>设计准则

### <a name="avoid-transparent-backplate"></a>避免透明底板
使用按钮设计菜单 UI 时，建议使用不透明的反板。 出于以下原因，不建议使用透明底板：
* 很难与 交互，因为很难理解按钮触发事件必须有多深
* 复杂物理环境的可读性问题
* 全息影像深度 LSR 稳定技术时，通过透明盘显示的数据可能会显示运动效果问题。

有关 [全息显示的颜色](designing-content-for-holographic-display.md) 选择和指南的更多详细信息，请参阅设计全息显示内容。

![透明 UI ](images/color_transparent_examples.jpg)
 *示例透明 UI 底板示例*

<br>

### <a name="use-shared-backplate"></a>使用共享反板
对于多个按钮，建议使用共享反板，而不是单个按钮的反板。

* 降低视觉干扰和复杂性
* 清除分组  

![共享反板 ](images/Button_Design_SharedBackplate.png
)
 *示例 共享 UI 底板的示例*

<br>

---

## <a name="button-in-mrtk-mixed-reality-toolkit"></a>MRTK (Mixed Reality Toolkit) 
**[MRTK for Unity](/windows/mixed-reality/mrtk-unity/)** 和 **[MRTK for Unreal](/windows/mixed-reality/develop/unreal/unreal-mrtk-introduction)** 提供各种类型的按钮预制，包括HoloLens 2样式按钮。 "HoloLens 2"按钮组件包含本页中引入的所有视觉反馈和交互详细信息。 通过使用它，可以利用我们的设计人员、开发人员和研究人员进行的许多设计迭代和用户研究的结果。

有关更多说明和自定义示例，请查看 [MRTK -](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) 按钮。

<br>

---

## <a name="see-also"></a>另请参阅

* [光标](cursors.md)
* [手部射线](point-and-commit.md)
* [Button](button.md)
* [可交互对象](interactable-object.md)
* [边界框和应用栏](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [手动菜单](hand-menu.md)
* [追踪菜单](near-menu.md)
* [对象集合](object-collection.md)
* [语音命令](voice-input.md)
* [键盘](keyboard.md)
* [工具提示](tooltip.md)
* [平板](slate.md)
* [滑块](slider.md)
* [着色器](shader.md)
* [公告和尾随](billboarding-and-tag-along.md)
* [显示进度](progress.md)
* [表面磁吸](surface-magnetism.md)