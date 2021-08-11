---
title: 颜色、光线和材料
description: 设计混合现实的内容需要仔细考虑所有视觉资产的颜色、照明和材料。
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、设计、颜色、光线、材料、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、HoloLens、MRTK、混合现实Toolkit
ms.openlocfilehash: 50789faa44e6786c0d9fd0b146daa84f459df451bedc52f06073e742ea8064a0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219851"
---
# <a name="color-light-and-materials"></a>颜色、光线和材料

![颜色、光线和材料](images/RemoteRendering.jpg)

设计混合现实的内容需要仔细考虑所有虚拟资产的颜色、照明和材料。 美观目的可能包括使用光线和材料来设置沉浸式环境的声音，而功能目的可能包括使用颜色来提醒用户即将发生的操作。 每个决策都必须根据体验的目标设备的机会和约束进行权衡。

下面是在沉浸式和全息头戴显示设备上呈现资产的特定指南。 其中许多与其他技术领域密切相关，相关主题列表可在本文末尾的 ["另](color-light-and-materials.md#see-also) 请参阅"部分找到。

## <a name="rendering-on-immersive-vs-holographic-devices"></a>在沉浸式与全息设备上呈现

与全息头戴显示设备中呈现的内容相比，沉浸式头戴显示设备中呈现的内容在视觉上会有所不同。 虽然沉浸式头戴显示设备通常像在 2D 屏幕上一样呈现内容，但全息头戴显示设备（如 HoloLens）使用颜色顺序、通配 RGB 显示器来呈现全息影像。

始终花时间在全息头戴显示设备中测试全息体验。 内容的外观（即使它是专为全息设备构建的）也会与辅助监视器、快照和旁观视图中的外观不同。 请记得演练设备体验，测试全息影像的照明，并观察来自 (以及上面和下方的场景) 呈现内容。 请务必在设备上使用一系列亮度设置进行测试。 所有用户不太可能共享一个假定默认值和一组不同的照明条件。

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>全息设备上呈现的基础

* **全息设备具有累加显示** 全息影像通过向现实世界中的光添加光创建-白色将呈现为亮色，而黑色则显示为透明。

* **颜色影响因用户环境而异** - 用户房间中有许多不同的照明条件。 创建具有适当对比度级别的内容，以帮助提高清晰度。

* **避免动态照明**– 全息影像在全息体验中均匀照明的照明效果最高效。 使用高级动态照明可能会超过移动设备的功能。 如果需要动态照明，建议使用混合现实和标准Toolkit[着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)。 

## <a name="designing-with-color"></a>使用颜色进行设计

由于累加显示的性质，某些颜色在全息显示器上可能有所不同。 某些颜色将在照明环境中弹出，而其他颜色则显示为影响较小。 当暖色跳转到前景时，冷颜色往往会重新进入背景。 在体验中浏览颜色时，请考虑以下因素：

* **呈现浅色** - 白色显示亮色，应谨慎使用。 在大多数情况下，请考虑 R 235 G 235 B 235 周围的白色值。 较大的亮区域可能会导致用户感到不便。 对于 UI 窗口的底板，建议使用深色。

* **呈现深色** - 由于附加显示的性质，深色颜色显示为透明。 纯黑色对象看起来与现实世界没有什么不同。 请参阅下面的 Alpha 通道。 若要提供"黑色"的外观，请尝试使用非常深的灰色 RGB 值，例如 16，16，16。

* **颜色一** 致性 - 通常全息影像呈现得足够亮，以便无论背景如何，都保持颜色一致性。 较大区域可能会变得浮点。 避免使用亮色、纯色的大型区域。

* **域**- HoloLens颜色"宽域"的好处，在概念上类似于 Adobe RGB。 因此，某些颜色可以在设备中显示不同的特性和表示形式。

* **Gamma** - 渲染图像的亮度和对比度因沉浸式和全息设备而异。 这些设备的差异通常会使颜色和阴影的深色区域更亮或更不亮。

* 颜色分离 **-** 也称为"颜色分解"或"颜色边"，在用户用眼睛跟踪对象时，最常见的是移动全息影像 (包括光标) 。

## <a name="technical-considerations"></a>技术注意事项

* **别名** - 考虑使用别名、锯齿或"锯齿步骤"，其中全息影像几何图形的边缘符合现实世界。 使用具有较高细节的纹理可能会影响此效果。 应映射纹理并启用筛选。 请考虑将全息影像的边缘淡入淡出，或添加一个纹理，以在对象周围创建黑色边缘边框。 如果可能，请避免使用精简几何图形。

* **Alpha 通道** - 对于未呈现全息影像的任何部分，必须清除 alpha 通道，使其完全透明。 保留 alpha 未定义会导致在从设备拍摄图像/视频时或使用旁观视图时产生可视项目。

* **纹理着色** - 由于光线在全息显示器中是累加的，因此最好避免使用较大的亮纯色区域，因为它们通常不会产生预期的视觉效果。

## <a name="design-guidelines-for-holographic-display"></a>全息显示设计准则

![颜色和手部遮挡](images/color_handocclusion.jpg)

设计全息显示器的内容时，需要考虑几个元素来获得最佳体验。 有关 [指南和建议，请访问](designing-content-for-holographic-display.md) 设计全息显示内容。

## <a name="storytelling-with-light-and-color"></a>浅色故事

浅色和颜色有助于使全息影像在用户环境中更加自然地显示，并为客户提供指导和帮助。 对于全息体验，在探索照明和颜色时，请考虑这些因素：

:::row:::
    :::column:::
* **Vignetting** - 对材料进行"vignette"效果有助于将用户焦点放在视场的中心。 此效果会使全息影像的材料从用户凝视向量的某一半径内变暗。 当用户从倾斜或扫视角度查看全息影像时，此功能也有效。

* **重点** - 通过对比颜色、亮度和照明来吸引对对象或交互点的注意。 有关故事讲述中照明方法的更详细介绍，请参阅 [像素像素](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf)图 - 计算机图形的照明方法。<br>
        <br>
        *图像：使用颜色来显示故事讲述元素的强调，如"片段"中的场景 [所示](https://www.microsoft.com/p/fragments/9nblggh5ggm8)。*
    :::column-end:::
        :::column:::
        ![使用颜色来显示故事讲述元素的强调，如片段场景中所示。](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::

## <a name="materials"></a>材料

:::row:::
    :::column:::
材料是制作真实全息影像的关键元素。 通过提供适当的视觉特征，你可以使引人注目的全息对象与物理环境很好地混合。 材料对于为各种类型的用户输入交互提供视觉反馈也很重要。  

[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) 为 MRTK 标准着色器提供了各种视觉效果选项，可用于视觉反馈。 例如，可以使用"邻近光"属性在用户手指接近对象表面时提供照明效果。 详细了解 [MRTK 标准着色器](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)
    :::column-end:::
        :::column:::
    *视频循环：基于边界框邻近性进行视觉反馈的示例* 
     ![有关手部邻近感应的视觉反馈](images/HoloLens2_Proximity.gif)

    :::column-end:::
:::row-end:::
<br>

---

## <a name="see-also"></a>另请参阅
* [设计适用于全息显示器的内容](designing-content-for-holographic-display.md)
* [颜色分离](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* [全息影像](../discover/hologram.md)
* [Microsoft 设计语言 - 颜色](https://www.microsoft.com/design/color)
* [通用Windows平台 - 颜色](/windows/uwp/style/color)