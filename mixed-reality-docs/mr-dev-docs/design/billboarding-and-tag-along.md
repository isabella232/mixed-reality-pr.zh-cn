---
title: 公告和尾随
description: 了解如何在 billboarding 中使用对象，这种对象始终在混合现实应用程序中对用户进行操作。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，billboarding，标记和混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包
ms.openlocfilehash: 48c7aa28217a38c6c226b65a6e16ed7c950cec59
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299882"
---
# <a name="billboarding-and-tag-along"></a>公告和尾随

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>什么是 billboarding？

Billboarding 是一种可应用于混合现实中的对象的行为概念。 具有 billboarding 的对象始终向用户提供正面的定向。 文本和菜单系统是常见的用例，在此类情况下，用户在用户的环境中放置的静态对象 (全局锁定的) 在用户四处移动时可能会被遮住或不可读。

启用了 billboarding 的对象可以在用户的环境中自由旋转。 它们还可以根据设计注意事项限制为单个轴。 请记住，billboarded 对象在放置到其他对象时或在 HoloLens 中太接近扫描面时，可以将其夹扣或遮蔽。 为避免出现这种情况，请考虑在为 billboarding 启用轴旋转时对象可能产生的总空间。

<br>

---
## <a name="what-is-a-tag-along"></a>什么是标记？

标记-一起是可以添加到全息影像的行为概念。 标记靠后的对象试图停留在允许用户轻松交互的范围内。

![HoloLens 引脚面板是如何在标签上表现出的一个很好的示例](images/tagalong-1000px.jpg)<br>
*HoloLens "开始" 菜单是一个更好的标记和行为示例*

带标签的对象具有参数，可对其行为方式进行微调。 当用户在其环境中移动时，内容可以在用户的视觉上或传出。 随着您的移动，内容会通过向视图的边缘滑动来尝试停留在用户的绕中。 内容可能暂时不会显示，具体取决于用户的移动速度。 当用户 gazes 沿标记的对象时，它会更全面地进入视图。 将内容视为始终 "一目了然"，这样用户就不会忘记内容的方向。

额外参数可以通过橡皮带来使标记沿着对象的外观附加到用户的头。 抑制加速或减速为对象提供权重，使其感觉更真实地出现。 此春季行为是一种 affordance，可帮助用户构建准确的心理模型，说明如何进行标记。 当用户在标记沿模式下具有对象时，音频有助于提供其他提示。 音频应强化移动速度;迅速走下来应提供更为明显的声音效果，而在自然速度下，应具有最小或没有音频效果。

与真正的 head 锁定的内容一样，如果对象在用户的视图中变得很大或太过太多，则这些对象可能会 nauseating。 随着用户的浏览，快速停止，他们的感知告诉他们已停止。 它们的平衡通知他们打印头已停止转动，其视觉障碍会看到世界停止车。 但是，如果在用户停止时仍继续进行标记，则可能会混淆其感知。

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>Billboarding 和标记 (混合现实工具包) 适用于 Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 为 Billboarding 和标记的行为提供脚本。 将布告栏脚本分配到任何对象，以添加 billboarding 行为并使对象始终为你。 若要添加标记和行为，请使用 RadialView 脚本。 可以调整各种选项，如 lerping 时间、距离和角度。

* [MRTK-径向视图规划求解](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [MRTK-布告栏脚本](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


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
