---
title: 设计适用于全息显示器的内容
description: 了解 HoloLens 设备上的全息显示器的设计准则和最佳实践。
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI 设计，全息显示，内容设计，深色主题，浅色主题，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实 Toolkit，设计，像素
ms.openlocfilehash: 1fab172f6d737b25e95b10a6dded2a5ab805e0086de8d0fae40c5a6a4ef7d805
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212934"
---
# <a name="designing-content-for-holographic-display"></a>设计适用于全息显示器的内容

![Ulnar 端位置](images/UX_Hero_DarkTheme.jpg)

设计全息显示器内容时，需要考虑几个元素，以便获得最佳体验。 下面列出了下面的一些建议，你可以在 ["颜色、光线和材料](color-light-and-materials.md) " 页面上详细了解全息版显示的特征。

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>大型表面上明亮的颜色挑战 

基于我们的 HoloLens 体验研究和测试，我们发现，在较大的显示器区域使用明亮的颜色可能会导致几个问题： 

**眼睛疲劳** 

由于全息显示是累加的，因此具有明亮颜色的全息影像会占用更少的颜色。 在较大的显示区域中，颜色明亮，很容易导致用户的眼睛疲劳。 

**手动封闭** 

明亮的颜色使用户在直接与对象交互时很难看到其手。 由于用户无法看到其手，因此很难感觉到该手指与目标表面之间的深度/距离。 Finger 游标有助于弥补此问题，但在明亮的表面上，它仍会有挑战性。 

![颜色和手封闭 ](images/color_handocclusion.jpg)
 *很难看到鲜艳的彩色内容 backplate*

**颜色一致性**

由于全息显示器的特性，显示屏上的一个较亮的区域可能会变得 blotchy。 通过使用暗色方案，你可以最大程度地减少此问题。 

## <a name="design-guidelines-for-color-choices"></a>颜色选择设计准则

**为 UI 背景使用暗色**

通过使用暗色方案，你可以最大程度地减少眼睛疲劳并改善直接交互的置信度。 

![用于 ](images/color_dark_examples.jpg)
 *内容背景的深色颜色示例* 的深色颜色示例

**使用 semibold 或粗体字体粗细**

HoloLens 允许你的体验显示漂亮的高分辨率文本。 但是，建议您避免使用细的字体粗细，如浅色或半光，因为垂直笔划可以在小字号内抖动。 

![ (上部面板的粗体或半粗体字体粗细) 会提高清晰度 ](images/color_font_examples.jpg)
 *粗体或半粗体字体粗细， (上面板) 提高清晰度*

**使用 MRTK 的 HolographicBackplate 材料**

HolographicBackplate 材料适用于 HoloLens shell 中的几个 UI 面板。 其中一项功能是在用户根据面板移动其位置时对用户可见的 iridescence 效果。 Backplate 颜色在一系列预定义的光谱上略有变化，从而创造生动生动的动态视觉效果，而不会干扰内容的可读性。 此微妙的颜色转变还用于弥补任何次要颜色不规则性。 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>透明或半透明 UI backplate 的挑战 

![透明 ](images/color_transparent_examples.jpg)
 *ui backplate 的* 透明 ui 示例

**视觉对象复杂性和辅助功能**

由于全息对象与物理环境混合，透明或半透明窗口上的内容或 UI 清晰度可能会下降。 此外，当透明全息对象重叠在一起时，这可能会使用户难以在不太深入的情况下进行交互。

**“性能”**

若要正确呈现透明或半透明对象，必须将其与存在于后台的任何对象进行排序和混合。 透明对象的排序具有适度的 CPU 开销，混合具有相当大的 GPU 开销，因为它不允许 GPU 通过 z 剔除来执行隐藏的图面删除 (例如 深度测试) 。 不允许隐藏的图面会增加最终呈现的像素所需的操作的数目。 这将导致更多压力填充率约束。

**LSR 技术的全息影像稳定性问题**

若要改善全息 reprojection 或全息图稳定性，应用程序可以为每个呈现的帧提交系统的深度缓冲区。 使用 reprojection 的深度缓冲区时，需要为每个颜色呈现的像素写入一个相应深度的深度缓冲区。 具有深度值的任何像素还应具有颜色值。 如果未遵循上述指导原则，呈现图像中缺少有效深度信息的区域可能会 reprojected 生成项目的方式，这通常作为类似于波形的失真显示。


## <a name="design-guidelines-for-transparent-elements"></a>透明元素的设计准则

**使用不透明的 UI 背景**

默认情况下，透明或半透明对象不会写入深度以允许进行适当的混合。 缓解此问题的方法包括：使用不透明对象，并确保半透明对象接近于不透明的对象 (例如，在不透明的 backplate) 前面添加半透明的按钮、强制半透明对象写入深度 (不适用于所有方案) ，或呈现代理对象，这些对象只在帧末尾提供深度值。

MRTK 中的解决方案-Unity：/windows/mixed-reality/mrtk-unity/performance/hologram-stabilization # 深层缓冲区共享  

通过使用纯和不透明的 backplate，我们可以确保可读性和交互置信度。

**最大程度地减少受影响的像素数**

如果项目必须使用透明对象，请尝试最大程度地减少受影响的像素数。 例如，如果某一对象仅在某些条件下可见 (如) 的加法光亮效果，则在该对象完全不可见时禁用该对象 (而不是将附加颜色设置为黑色) 。 对于使用带有 alpha 掩码的四核创建的简单二维形状，请考虑改为使用不透明着色器来创建形状的网格表示形式。 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>MRTK (混合现实 Toolkit 的深色 UI 示例) Unity

**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 提供了许多基于深色方案的 UI 构建基块示例。

* [邻近菜单](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/near-menu)
* [对话框](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)
* [手动菜单](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

<br>

---

## <a name="see-also"></a>另请参阅

* [颜色、光线和材料](color-light-and-materials.md)
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