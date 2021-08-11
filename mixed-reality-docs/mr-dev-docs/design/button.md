---
title: Button
description: 了解如何使用按钮触发立即操作，这是一个混合现实的基础组件。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合现实，控件，交互，ui，ux，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实 Toolkit，按钮
ms.openlocfilehash: 602d5b8784c97676e29574e4a5b0ffb7b240f07c2c43bbe68e0f8bc49db9dd1f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219306"
---
# <a name="button"></a>Button

![Button](images/UX_Hero_Button.jpg)

利用按钮，用户可以在混合现实体验中触发即时操作。 在 HoloLens 2 中，按钮具有视觉提示和实用，可帮助用户提高交互置信度。 

:::row:::
    :::column:::
       ![显示了接近光效果的按钮](images/UX_Button_Affordance_ProximityLight.jpg)<br>
       **邻近感应灯**<br>
    :::column-end:::
    :::column:::
       ![所选的具有焦点突出显示效果的按钮](images/UX_Button_Affordance_FocusHighlight.jpg)<br>
        **焦点突出显示**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![所显示的压缩箱效果按下的按钮](images/UX_Button_Affordance_Compression.jpg)<br>
       **压缩箱**<br>
    :::column-end:::
    :::column:::
       ![所示的触发脉冲效果按下的按钮](images/UX_Button_Affordance_Pulse.jpg)<br>
        **触发暂停**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a>MRTK 中的按钮 (混合现实 Toolkit 为 Unity) 
**[MRTK for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 提供各种类型的 prototyping 按钮，包括用于 HoloLens 2 和 HoloLens (第一代) 的 shell 样式的按钮。 "HoloLens 2" 按钮 prefab 包含多个详细实用，有助于提高用户置信度：

* 基于邻近性的突出显示
* 压缩前端固定架
* 对触发器的脉冲效果。

* 有关更多说明和自定义示例，请查看 [MRTK-按钮](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) 。

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