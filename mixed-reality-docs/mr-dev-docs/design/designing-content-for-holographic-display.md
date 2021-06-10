---
title: 设计适用于全息显示器的内容
description: 了解 HoloLens 设备上全息显示的设计准则和最佳做法。
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI 设计， 全息显示， 内容设计， 深色主题， 浅色主题， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， HoloLens， MRTK， 混合现实工具包， 设计， 像素
ms.openlocfilehash: 2c68acb5478bfbd438c8bbb9dd2f8d9686bcefc5
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600316"
---
# <a name="designing-content-for-holographic-display"></a>设计适用于全息显示器的内容

![Ulnar 手部位置](images/UX_Hero_DarkTheme.jpg)

设计全息显示器的内容时，需要考虑几个元素，以获得最佳体验。 下面列出了一些建议，可以在"颜色、光线和材料"页上详细了解全息[显示器的特征。](color-light-and-materials.md)

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>大型表面上的亮色挑战 

根据我们的 HoloLens 体验研究与测试，我们发现在大量显示器中使用亮色可能会导致多个问题： 

**眼动** 

由于全息显示是累加性的，因此具有亮色的全息影像使用更多的光。 显示较大区域中的亮色、纯色很容易让用户感到眼动。 

**手部遮挡** 

亮色使得用户在直接与对象交互时难以看到手部。 由于用户看不到手部，因此很难感知手/手指与目标图面的深度/距离。 手指光标有助于弥补此问题，但它在亮白色表面上仍然具有挑战性。 

![颜色和手部遮挡 难以在亮色内容底板上 ](images/color_handocclusion.jpg)
 *看到手*

**颜色一致性**

由于全息显示器的特征，显示器上的大亮区域可能会变得浮点。 通过使用深色配色方案，可以最大程度地减少此问题。 

## <a name="design-guidelines-for-color-choices"></a>颜色选择的设计准则

**对 UI 背景使用深色**

通过使用深色配色方案，可以最大程度地减少眼动，并提高直接手部交互的置信度。 

![用于内容背景的深色颜色示例 用于内容背景 ](images/color_dark_examples.jpg)
 *的深色示例*

**使用半双曲或粗体字体粗细**

HoloLens 允许体验显示美观的高分辨率文本。 但是，建议避免字体粗细，如浅色或半浅，因为垂直笔划可能会以较小的字体大小抖动。 

![在上面板中 (粗或半粗体字体粗) 提高上面板上半 (粗或半粗体字体粗细) 提高 ](images/color_font_examples.jpg)
 *可读性*

**使用 MRTK 的 HolographicBackplate 材料**

HolographicBackplate 材料应用于 HoloLens shell 中的多个 UI 面板。 它的一个功能是一种网格效果，当用户基于面板移动其位置时，用户可以看到该效果。 反板颜色在预定义的色系中以小微方式移动，从而创建一种吸引力和动态视觉效果，而不会干扰内容的可读性。 这种细微的颜色变化还有助于补偿任何次要的颜色异常。 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>透明或半透明 UI 底板的挑战 

![透明 UI ](images/color_transparent_examples.jpg)
 *示例透明 UI 底板示例*

**视觉复杂性和可访问性**

由于全息对象与物理环境混合，因此透明或半透明窗口上的内容或 UI 可读性可能会下降。 此外，当透明全息对象彼此叠加时，由于深度令人困惑，用户难以交互。

**“性能”**

若要正确呈现透明或半透明对象，必须排序这些对象，并与存在于后台的任何对象混合。 透明对象的排序具有适度的 CPU 成本，混合具有相当的 GPU 成本，因为它不允许 GPU 通过 z-culling 执行隐藏表面 (即 深度测试) 。 不允许隐藏表面移除会增加最终呈现像素所需的操作数。 这会使填充速率受到更多压力约束。

**深度 LSR 技术的全息影像稳定性问题**

为了提高全息重新投影或全息影像稳定性，应用程序可以针对每个渲染帧向系统提交深度缓冲区。 使用深度缓冲区进行重新分析时，需要为每个颜色呈现的像素编写一个深度缓冲区，以对应深度。 具有深度值的任何像素也应具有颜色值。 如果未遵循上述指南，可能会以生成项目的方式重新重现呈现的图像中缺少有效深度信息的区域，这些项目通常以波形扭曲方式显示。


## <a name="design-guidelines-for-transparent-elements"></a>透明元素的设计准则

**使用不透明 UI 背景**

默认情况下，透明或半透明对象不会写入深度以允许适当的混合。 缓解此问题的方法包括：使用不透明对象，确保半透明对象显示在不透明对象附近 (如不透明底板) 前面的半透明按钮、强制半透明对象写入深度 (不适用于所有方案) 或呈现代理对象（仅在帧末尾提供深度值）。

MRTK-Unity 中的解决方案：/windows/mixed-reality/mrtk-unity/performance/hologram-stabilization#depth-buffer-sharing-in-unity  

通过使用实心不透明的底板，我们可以确保可读性和交互置信度。

**最小化受影响的像素数**

如果项目必须使用透明对象，请尝试最大程度地减少受影响的像素数。 例如，如果对象仅在特定条件下可见 (如累加光效果) ，则当对象完全不可见时 (禁用该对象，而不是将加法色设置为黑色) 。 对于使用带 alpha 掩码的四边形创建的简单 2D 形状，请考虑改为使用不透明着色器创建形状的网格表示形式。 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>MRTK 中的深色 UI (Mixed Reality Toolkit) for Unity

**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 基于深色配色方案提供了许多 UI 构建基块示例。

* [近菜单](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/near-menu)
* [对话框](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)
* [手部菜单](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)

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