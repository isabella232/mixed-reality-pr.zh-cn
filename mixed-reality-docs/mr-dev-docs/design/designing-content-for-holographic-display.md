---
title: 设计适用于全息显示器的内容
description: 全息显示器的设计准则和最佳实践
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI 设计，全息显示，内容设计，深色主题，浅色主题，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，设计，像素
ms.openlocfilehash: ea3fbda7aff80f0878521deb433c88b16abeab19
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702633"
---
# <a name="designing-content-for-holographic-display"></a>设计适用于全息显示器的内容

![Ulnar 端位置](images/UX_Hero_DarkTheme.jpg)

设计全息显示器内容时，需要考虑几个元素，以便获得最佳体验。 下面列出了下面的一些建议，你可以在 ["颜色、光线和材料](color-light-and-materials.md) " 页面上详细了解全息版显示的特征。

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>大型表面上明亮的颜色挑战 
基于用户的研究和测试各种类型的 HoloLens 体验，我们发现，在大区域显示中使用明亮的颜色可能会导致几个问题： 

**眼睛疲劳** 

由于全息显示是累加的，因此鲜艳颜色会使用更多灯光来显示全息影像。 在较大的显示区域中，颜色明亮，很容易导致用户的眼睛疲劳。 

**手动封闭** 

明亮的颜色使用户在直接与对象交互时很难看到其手。 由于用户无法看到其手，因此很难发现指针与目标表面之间的深度/距离。 Finger 游标有助于弥补此问题，但在明亮的表面上，它仍会有挑战性。 

![颜色和手封闭 ](images/color_handocclusion.jpg)
 *很难看到鲜艳的彩色内容 backplate*

**颜色一致性**

由于全息显示器的特性，显示屏上的一个较亮的区域可能会变得 blotchy。 通过使用暗色方案，你可以最大程度地减少此问题。 

## <a name="design-guidelines"></a>设计准则

**为 UI 背景使用暗色**

通过使用暗色方案，你可以最大程度地减少眼睛疲劳并改善直接交互的置信度。 

![深色 UI 示例 ](images/color_dark_examples.jpg)
 *用于内容背景的深色颜色*

**使用 semibold 或粗体字体粗细**

HoloLens 允许你的体验显示漂亮的高分辨率文本。 不过，建议您避免使用细的字体粗细，如浅色或半光，因为垂直笔划可以在小字号内抖动。 

![深色 UI ](images/color_font_examples.jpg)
 *(上面板的粗体或半粗字体粗细) 改善可读性*

**使用 MRTK 的 HolographicBackplate 材料**

HolographicBackplate 材料适用于 HoloLens shell 中的几个 UI 面板。 其中一项功能是用户在将其相对于面板之间移动时对其显示的 iridescence 效果。 Backplate 颜色在一系列预定义的光谱上略有变化，从而创造生动生动的动态视觉效果，而不会干扰内容的可读性。 此微妙的颜色转变还用于弥补任何次要颜色不规则性。 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>透明或半透明 UI backplate 的挑战 
![透明 ](images/color_transparent_examples.jpg)
 *ui backplate 的* 透明 ui 示例

**视觉对象复杂性和辅助功能**

由于全息对象与物理环境混合，因此透明或半透明窗口上的内容或 UI 的可读性可能会下降。 此外，当透明全息对象重叠在一起时，这可能会使用户难以在不太深入的情况下进行交互。

**“性能”**

若要正确呈现透明或半透明对象，必须将其与存在于后台的任何对象进行排序和混合。 透明对象的排序具有适度的 CPU 开销，混合具有相当大的 GPU 开销，因为它不允许 GPU 通过 z 剔除执行隐藏的图面 (例如 深度测试) 。 不允许隐藏面删除会增加需要为最终呈现的像素计算的操作的数量，从而增加对填充速率约束的压力。

**LSR 技术的全息影像稳定性问题**

若要改善全息 reprojection 或全息图稳定性，应用程序可以为每个呈现的帧提交系统的深度缓冲区。 使用 reprojection 的深度缓冲区时，一个规则是，对于呈现了相应深度值的每个颜色像素，都必须将其写入深度缓冲区 (并且具有深度值的任何像素也应) 颜色值。 如果未遵循以上指导原则，呈现图像中缺少有效深度信息的区域可能会 reprojected，从而产生 (通常作为类似于波形的扭曲) 出现的项目。


## <a name="design-guidelines"></a>设计准则
**使用不透明的 UI 背景**

默认情况下，透明或半透明对象不会写入深度以允许进行适当的混合。 缓解此问题的方法包括：使用不透明对象，并确保半透明对象接近于不透明的对象 (例如，在不透明的 backplate) 前面添加半透明的按钮、强制半透明对象写入深度 (不适用于所有方案) ，或呈现仅在帧末尾提供深度值的代理对象。

MRTK 中的解决方案-Unity： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity  

通过使用纯和不透明的 backplate，我们可以确保可读性和交互置信度。

**最大程度地减少受影响的像素数**

如果项目必须使用透明对象，请尝试最大程度地减少受影响的像素数。 例如，如果某一对象仅在某些条件下可见 (如) 的加法发光效果），则在该对象完全不可见时禁用该对象 (而不是将附加颜色设置为黑色) 。 对于使用带有 alpha 掩码的四核创建的简单二维形状，请考虑改为使用不透明着色器来创建形状的网格表示形式。 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>MRTK 中的深色 UI 示例 (混合现实工具包) 适用于 Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 提供了许多基于深色方案的 UI 构建基块示例。

* [邻近菜单](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [对话框](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [手动菜单](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)


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
