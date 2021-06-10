---
title: 可交互对象
description: 了解如何触发事件、提供视觉提示以及与混合现实应用程序中的对象进行交互。
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: 混合现实， 控件， 交互， 提示， ui， ux， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， HoloLens， MRTK， 混合现实工具包， 音频
ms.openlocfilehash: 8a68006d68b985f8d26a3d1a11e4d52fcfb5acb5
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600436"
---
# <a name="interactable-object"></a>可交互对象

![可交互对象](images/UX_Hero_Interactable.jpg)

按钮一直是在 2D 抽象世界触发事件的一种暗念。 在三维混合现实世界，我们不必再局限于这个抽象世界。 任何内容都可以是 **触发事件的** 可交互对象。 可交互对象可以是任何内容，从表上的咖啡杯到中间的气球。 在某些情况下（例如，在对话框 UI 中）我们仍然使用传统按钮。 按钮的可视化表示形式取决于上下文。

<br>

---

## <a name="important-properties-of-the-interactable-object"></a>可交互对象的重要属性

### <a name="visual-cues"></a>视觉提示

视觉提示是来自光的传感器提示，由眼睛接收，在视觉感知期间由视觉系统处理。 由于视觉系统在许多种类（尤其是人类）中处于主导状态，因此视觉提示是了解世界方式的一大信息源。

由于全息对象与混合现实中的真实环境混合在一起，因此可能很难理解可以交互的对象。 对于体验中任何可交互的对象，为每种输入状态提供不同的视觉提示非常重要。 这有助于用户了解你体验的哪个部分是可交互的，并且通过使用一致的交互方法使用户确信。

<br>

---

### <a name="far-interactions"></a>远交互

对于用户可以与凝视、手部射线和运动控制器射线交互的任何对象，建议针对这三种输入状态使用不同的视觉提示：

:::row:::
    :::column:::
       ![具有默认状态可交互的对象](images/interactibleobject-states-default.jpg)<br>
       **默认 (观察) 状态**<br>
        对象的默认空闲状态。
    光标不在 对象上。 未检测到手部。
    :::column-end:::
    :::column:::
       ![具有目标状态和悬停状态可交互的对象](images/interactibleobject-states-targeted.jpg)<br>
        **目标 (将鼠标) 状态**<br>
        当对象以凝视光标、手指邻近或运动控制器指针为目标时。
    光标位于 对象上。 检测到手部，准备就绪。
    :::column-end:::
    :::column:::
       ![具有按下状态可交互的对象](images/interactibleobject-states-pressed.jpg)<br>
       **按下状态**<br>
        使用敲击手势按下对象时，按手指或运动控制器的"选择"按钮。
    光标位于 对象上。 检测到手部，点击了空气。
    :::column-end:::
:::row-end:::

<br>

---

可以使用突出显示或缩放等技术为用户输入状态提供视觉提示。 在混合现实中，可以在应用栏按钮上找到可视化“开始”菜单输入状态的示例。 

全息按钮上的这些状态 **如下所示**：

:::row:::
    :::column:::
       ![默认状态下的全息按钮](images/MRTK_InteractableState-default.jpg)<br>
       **默认 (观察) 状态**<br>
    :::column-end:::
    :::column:::
       ![处于"目标"和"悬停"状态中的全息按钮](images/MRTK_InteractableState-targeted.jpg)<br>
        **目标 (将鼠标) 状态**<br>
    :::column-end:::
    :::column:::
       ![已按下的全息按钮](images/MRTK_InteractableState-pressed.jpg)<br>
       **按下状态**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>近 (直接)  

HoloLens 2支持手部跟踪输入，可用于与对象交互。 如果没有视觉反馈和完美深度感知，就很难判断手离对象有多远或者是否触摸了它。 必须提供足够的视觉提示来传达对象的状态，尤其是基于该对象的手的状态。

使用视觉反馈传达以下状态：
* **默认 (观察) ：** 对象的默认空闲状态。
* **悬** 停：当手靠近全息影像时，更改视觉对象以传达以全息影像为目标的手。 
* **距离和交互点**：当手接近全息影像时，设计反馈来传达预测的交互点，以及手指与对象的距离
* **联系人开始**：更改视觉对象 (浅色) 来传达触摸已发生
* **已抓取**：在 (时更改) 颜色颜色
* **联系人结束**：在触摸 (更改视觉对象) 浅色、颜色或颜色

<br>

---

:::row:::
    :::column:::
        ![将鼠标 (远) ](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **将鼠标 (远)**<br>
        根据手的邻近度突出显示。
    :::column-end:::
    :::column:::
        ![将鼠标 (") ](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **将鼠标 (")**<br>
        突出显示基于手部距离的大小更改。
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![触摸/按](images/640px-interactibleobject-states-near-press.jpg)<br>
        **触摸/按**<br>
        视觉对象和音频反馈。
    :::column-end:::
    :::column:::
        ![把握](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **把握**<br>
        视觉对象和音频反馈。
    :::column-end:::
:::row-end:::

<br>

<br>

---

图标 [上的HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) 是如何可视化不同输入交互状态的示例：

:::row:::
    :::column:::
        ![默认](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **默认**<br>
    :::column-end:::
    :::column:::
        ![悬停](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **悬停**<br>
        展示基于邻近感应的照明效果。
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
        **按**<br>
        移动前板。
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>上显示"环"视觉提示HoloLens 2<br>
        在HoloLens 2，有一个额外的视觉提示，可帮助用户感知深度。 当手指靠近对象时，可显示一个靠近其手指的环并缩小。 当达到按下状态时，环最终会聚合为点。 此视觉视觉视觉元素可帮助用户了解它们与对象距离有多远。<br>
        <br>
        *视频循环：基于边界框邻近性进行视觉反馈的示例*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![有关手部邻近感应的视觉反馈](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>音频提示

对于直接手部交互，适当的音频反馈可以显著提高用户体验。 使用音频反馈传达以下提示：
* **联系人开始**：触摸开始时播放声音
* **接触端**：在触摸端播放声音
* **抓取开始**：开始抓取时播放声音
* **抓取端**：在抓取端播放声音

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>语音命令<br>
        对于任何可交互对象，必须支持备用交互选项。 默认情况下，建议任何 [可交互](../out-of-scope/voice-design.md) 的对象都支持语音命令。 为了提高可发现性，还可以在悬停状态期间提供工具提示。<br>
        <br>
        *图像：语音命令的工具提示*
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

* [可交互](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [Button](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)
* [手动交互示例场景](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

MixedRealityToolkit 的标准着色器提供了各种选项 **，例如，可** 帮助您创建视觉对象和音频提示。

* [MRTK 标准着色器](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

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