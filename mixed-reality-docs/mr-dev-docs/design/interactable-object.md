---
title: 可交互对象
description: 了解如何触发事件，提供视觉提示，以及与混合现实应用程序中的对象进行交互。
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: 混合现实，控件，交互，提示，ui，ux，混合现实耳机，windows mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，音频
ms.openlocfilehash: 0e9f4dc09e3c4a4c38ffeb1a9042f39996918e36
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300462"
---
# <a name="interactable-object"></a>可交互对象

![Interactible 对象](images/UX_Hero_Interactable.jpg)

"Button" 是一种用于在二维抽象环境中触发事件的比喻。 在这三维混合现实世界中，我们不必再局限于这种抽象领域。 任何内容都可以是触发事件的 **种不可交互对象** 。 种不可交互对象可以是从表上的咖啡杯到 midair 中的气球的任何内容。 在某些情况下（例如，在对话框 UI 中），我们仍要使用传统按钮。 按钮的可视化表示形式取决于上下文。

<br>

---

## <a name="important-properties-of-the-interactable-object"></a>种不可交互对象的重要属性

### <a name="visual-cues"></a>视觉提示

视觉提示是传感器的提示，由眼睛接收，由视觉对象系统在视觉对象中进行处理。 由于视觉对象系统在很多物种中是主导的，尤其是在人们看来，直观提示是了解世界上的信息。

由于全息对象与混合现实中的实际环境混合，因此很难理解您可以与哪些对象交互。 对于你的体验中的任何种不可交互对象，为每个输入状态提供不同的视觉提示非常重要。 这可以帮助用户了解你的体验的哪个部分是种不可交互的，并通过使用一致的交互方法使用户更自信。

<br>

---

### <a name="far-interactions"></a>远距离交互

对于用户可与 "注视"、"手 ray" 和 "运动控制器" 射线交互的任何对象，我们建议为这三个输入状态提供不同的视觉提示：

:::row:::
    :::column:::
       ![具有默认状态的种不可交互对象](images/interactibleobject-states-default.jpg)<br>
       **默认 (观察) 状态**<br>
        对象的默认空闲状态。
    光标不在对象上。 未检测到手写。
    :::column-end:::
    :::column:::
       ![具有目标和悬停状态的种不可交互对象](images/interactibleobject-states-targeted.jpg)<br>
        **目标 (悬停) 状态**<br>
        当对象面向注视光标时，指的是指邻近的或运动控制器的指针。
    光标位于对象上。 已检测到手型，准备就绪。
    :::column-end:::
    :::column:::
       ![具有按下状态的种不可交互对象](images/interactibleobject-states-pressed.jpg)<br>
       **按下状态**<br>
        如果按下了按压按钮，请按下或运动控制器的选择按钮。
    光标位于对象上。 检测到手型，并攻丝。
    :::column-end:::
:::row-end:::

<br>

---

您可以使用诸如突出显示或缩放等方法为用户输入状态提供视觉提示。 在混合现实中，可以在 "开始" 菜单和应用栏按钮中查找可视化不同输入状态的示例。 

下面是 **全息按钮** 上这些状态的外观：

:::row:::
    :::column:::
       ![处于默认状态的全息按钮](images/MRTK_InteractableState-default.jpg)<br>
       **默认 (观察) 状态**<br>
    :::column-end:::
    :::column:::
       ![目标和悬停状态的全息按钮](images/MRTK_InteractableState-targeted.jpg)<br>
        **目标 (悬停) 状态**<br>
    :::column-end:::
    :::column:::
       ![处于按下状态的全息按钮](images/MRTK_InteractableState-pressed.jpg)<br>
       **按下状态**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>接近交互 (直接)  

HoloLens 2 支持已表述的手动跟踪输入，这允许您与对象进行交互。 如果没有 haptic 的反馈和完美的深度认识，则很难判断你手中的距离是从一个对象还是正在触摸。 务必提供足够的视觉提示来传达对象的状态，特别是根据对象的状态。

使用视觉反馈传达以下状态：
* **默认 (观察)**：对象的默认空闲状态。
* **悬停**：当手接近全息图时，请更改视觉对象，以便与全息图建立通信。 
* **距离和交互点**：作为一种方法，即使用全息图，设计反馈来传达投影的交互点，以及从对象到手指的距离
* **联系人开始**：更改视觉对象 (光源、颜色) ，传达触摸已发生的情况
* **Grasped**：在 Grasped 对象时更改视觉对象 (光源、颜色) 
* **联系人结束**：在触摸结束时，更改视觉对象 (光源、颜色) 

<br>

---

:::row:::
    :::column:::
        ![悬停 (远处) ](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **悬停 (远处)**<br>
        根据手的邻近性突出显示。
    :::column-end:::
    :::column:::
        ![悬停 (接近) ](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **悬停 (接近)**<br>
        根据与手型的距离突出显示大小变化。
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![触摸/按](images/640px-interactibleobject-states-near-press.jpg)<br>
        **触摸/按**<br>
        视觉对象和音频反馈。
    :::column-end:::
    :::column:::
        ![掌握](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **掌握**<br>
        视觉对象和音频反馈。
    :::column-end:::
:::row-end:::

<br>

<br>

---

[HoloLens 2 上的按钮](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)是如何可视化不同输入交互状态的示例：

:::row:::
    :::column:::
        ![默认](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **默认值**<br>
    :::column-end:::
    :::column:::
        ![悬停](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **悬停**<br>
        显示基于近程的照明效果。
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![触控](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **触控**<br>
        显示波纹效果。
    :::column-end:::
    :::column:::
        ![请按](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **请按**<br>
        移动前面板。
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>HoloLens 2 上的 "环" 视觉提示<br>
        在 HoloLens 2 上，有一个额外的视觉提示，可帮助用户了解深度。 当手指更接近对象时，其手指附近的圆圈会显示并缩小。 当达到按下状态时，环最终汇聚为一个点。 此视觉对象 affordance 可帮助用户了解其在对象中的距离。<br>
        <br>
        *视频循环：基于与边界框的邻近的视觉反馈示例*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![视觉对象反馈](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>音频提示

对于直接交互，正确的音频反馈可显著改善用户体验。 使用音频反馈来传达以下提示：
* **联系人开始**：触控开始时播放声音
* **联系人结束**：在 touch 端上播放声音
* **开始获取**：开始播放时播放声音
* **抓取结束**：在抓取结束时播放声音

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>语音命令<br>
        对于任何种不可交互对象，支持替代交互选项非常重要。 默认情况下，我们建议为种不可交互的任何对象支持 [语音命令](../out-of-scope/voice-design.md) 。 若要改善可发现性，还可以在悬停状态中提供工具提示。<br>
        <br>
        *Image：语音命令的工具提示*
    :::column-end:::
        :::column:::
       ![语音命令](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a>重设大小建议

为了确保可以轻松地接触所有种不可交互对象，我们建议确保种不可交互根据其从用户的距离来确定最小大小。 视觉角度通常以视觉弧的度数来度量。视觉角度基于用户眼睛与对象之间的距离并保持不变，而目标的物理大小可能会随用户更改的距离而更改。 若要根据用户的距离确定对象的必要物理大小，请尝试使用视觉角度计算器（如 [此](https://elvers.us/perception/visualAngle/)类）。

下面是有关种不可交互内容的最小大小建议。

### <a name="target-size-for-direct-hand-interaction"></a>直接手动交互的目标大小

| 距离 | 查看角度 | 大小 |
|---------|---------|---------|
| 45厘米  | 不小于2° | 1.6 x 1.6 厘米 |

![直接手动交互的目标大小](images/TargetSizingNear.jpg)<br>
*直接手动交互的目标大小*

<br>

### <a name="target-size-for-buttons"></a>按钮的目标大小

创建直接交互的按钮时，建议使用较大的最小 3.2 x 3.2 厘米，以确保有足够的空间来包含图标，并可能有一些文本。

| 距离 | 最小大小 |
|---------|---------|
| 45厘米  | 3.2 x 3.2 厘米 |

![按钮的目标大小](images/TargetSizingButtons.png)<br>
*按钮的目标大小*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>手动 ray 或注视交互的目标大小
| 距离 | 查看角度 | 大小 |
|---------|---------|---------|
| 2 m  | 不小于1° | 3.5 x 3.5 厘米 |

![手动 ray 或注视交互的目标大小](images/TargetSizingFar.jpg)<br>
*手动 ray 或注视交互的目标大小*

<br>

---

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a>MRTK 中的种不可交互对象 (Unity 的混合现实工具包) 

在 **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 中，可以使用脚本 [**种不可交互**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) 使对象对各种类型的输入交互状态进行响应。 它支持各种类型的主题，这些主题允许您通过控制对象属性（如颜色、大小、材料和着色器）来定义可视状态。

* [可交互](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [Button](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)
* [手动交互示例场景](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

MixedRealityToolkit 的标准着色器提供了各种选项 **，例如，可** 帮助您创建视觉对象和音频提示。

* [MRTK 标准着色器](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

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
