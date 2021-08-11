---
title: 版式
description: 了解如何设计和实现文本，作为在混合现实应用体验中传递信息的重要元素。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality、设计、样式、字体、版式、ui、ux、文本、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、HoloLens
ms.openlocfilehash: 7df2386f3478c0b0b79d198a3342bc9a9a061f6e5a305baedcd91be9c2f09f04
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200273"
---
# <a name="typography"></a>版式

![示例中的版式HoloLens](images/typography-cover.png)<br>


文本是在应用体验中传递信息的重要元素。 就像2D 屏幕上的版式一样，目标应清晰且易懂。 借助混合现实三维方面，有机会以更大的方式影响文本和整体用户体验。

当我们讨论 3D 中的类型时，我们倾向于认为三维文本是放大的、音量的 3D 文本。 除了某些徽标类型设计和一些其他有限的应用程序外，外向文本往往会降低文本的可读性。 即使我们要为 3D 设计体验，我们还是使用 2D 作为类型，因为它更清晰且更易于阅读。

在HoloLens中，类型是使用基于累加色系统的光通过全息影像构造的。 与其他全息影像一样，类型可以放置在实际环境中，可在其中从任何角度锁定和观察类型。 [类型和环境之间的](https://en.wikipedia.org/wiki/Parallax)视差效果也会为体验增加深度。

## <a name="typography-in-mixed-reality"></a>混合现实中的版式

混合现实中的版式规则与其他任何位置没有什么不同。 物理世界和虚拟世界中的文本都需要清晰易读。 文本可以位于墙上，也可以叠加在物理对象上。 它可以随数字用户界面一起浮动。 无论使用何种上下文，我们都对阅读和识别应用相同的版式规则。

### <a name="create-clear-hierarchy"></a>创建清除层次结构

使用不同的类型大小和权重生成对比度和层次结构。 定义类型渐变并在整个应用体验中遵循它可提供具有一致信息层次结构的出色的用户体验。

![类型渐变示例](images/typography-ramp-1000px.jpg)<br>
*定义类型渐变，并在整个应用体验中遵循它*

### <a name="limit-your-fonts"></a>限制字体

避免在单个上下文中使用两个不同的字体系列。 字体过多会破坏体验的协调性和一致性，使信息更难使用。 在HoloLens，由于信息叠加在物理环境的顶部，因此使用过多的字体样式会降低体验。 Segoe UI是所有 Microsoft 数字设计的字体。 它在命令行管理 shell 中Windows Mixed Reality一致。 可以从"Segoe UI工具包"页下载Windows[字体文件](/windows/uwp/design-downloads/)。

[有关字体Segoe UI详细信息](/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>避免字体粗细

避免对 42 pt 下的类型大小使用浅色或半浅字体粗细，因为细垂直笔划会振动并降低可读性。 具有足够笔划粗细的新式字体效果良好。 例如，Helvetica 和 Arial 在HoloLens或粗体权重时清晰易读。

### <a name="color"></a>颜色

在HoloLens，由于全息影像是使用加法光系统构造的，因此白色文本非常清晰。 可以在"应用"和"应用""开始"菜单白色文本的示例。 即使白色文本在无底板的情况下HoloLens，复杂的物理背景也可能导致类型难以阅读。 我们建议在深色或彩色背景上使用白色文本，以提高用户的焦点，并尽量减少来自物理背景的干扰。

<br>


![我们建议在深色或彩色底板上使用白色文本。 ](images/typography-whiteonblack2-1000px.jpg)
*深色或彩色底板上的白色文本示例。*
<br>

若要使用深色文本，应该使用亮色底板使其可读。 在加法色系统中，黑色显示为透明。 这意味着，如果没有彩色底板，将看不到黑色文本。

:::row:::
    :::column:::
        ![黑色文本上的白色示例和白色文本上的黑色示例](images/typography-whiteonblack.png)<br>
        *黑色文本上的白色示例和白色文本上的黑色示例*<br>
    :::column-end:::
    :::column:::
        ![系统应用中的黑色文本示例 - 应用商店和设置](images/640px-typography-blackonwhite.jpg)<br>
        *系统应用中的黑色文本示例 - 应用商店和设置*<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a>建议的字号

如你预期，我们在电脑或平板电脑设备上使用的类型大小 (通常介于 12-32pt) 2 米的距离。 它取决于每种字体的特征，但根据我们的用户研究，建议的最小查看角度和字体高度通常约为 0.35°-0.4°/12.21-13.97 mm。 它大约是 35-40 pt，Unity 页面中的文本 [中引入了缩放](../develop/unity/text-in-unity.md) 因子。 

对于 0.45 m (45 cm) 的近交互，最小可读字体的查看角度和高度为 0.4°-0.5° / 3.14–3.9mm。 它大约是 9-12 pt，Unity 中的 [文本中引入了缩放因子](../develop/unity/text-in-unity.md)。

![近近交互范围 ](images/typography-distance-1000px.jpg)
 *和远交互范围内容*

### <a name="the-minimum-legible-font-size"></a>最小可读字号

| 距离 | 视角 | 文本高度 | 字号** |
|---------|---------|---------|---------|
| 45 cm (操作距离)  | 0.4°-0.5° | 3.14–3.9mm | 8.9–11.13pt |
| 2 m | 0.35°-0.4° | 12.21–13.97mm | 34.63-39.58 pt |

### <a name="the-comfortably-legible-font-size"></a>清晰易读的字号

| 距离 | 视角 | 文本高度 | 字号** |
|---------|---------|---------|---------|
| 45 cm (操作距离)  | 0.65°-0.8° | 5.1-6.3 mm | 14.47-17.8 pt |
| 2 m | 0.6°-0.75° | 20.9-26.2 mm | 59.4-74.2 pt |


Segoe UI (默认字体Windows) 在大多数情况下都运行良好。 避免使用小尺寸的浅色或半浅字体系列，因为细垂直笔划会振动，并且会降低可读性。 具有足够笔划粗细的新式字体效果良好。 例如，Helvetica 和 Arial 看起来很清晰，并且HoloLens具有正则或粗体粗细的字体。

**有关 Unity 中文本大小计算的更多详细信息，请参阅 [Unity 中的文本](../develop/unity/text-in-unity.md)**

![查看角度 ](images/Text_In_Unity_ViewingAngle.jpg)
 *查看距离、角度和文本高度*

<br>

---

## <a name="resources"></a>资源

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[Segoe 字体](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
     (Zip 文件) <br>
    ### <a name="hololens-fontbr"></a>[HoloLens字体](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
     (Zip 文件) <br>
    <br>
    *图像：HoloLens字体提供在图像中使用的符号标志Windows Mixed Reality。*
    :::column-end:::
        :::column:::
        ![该HoloLens字体提供在文本中使用的符号标志Windows Mixed Reality](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a>另请参阅

* [Unity 中的文本](../develop/unity/text-in-unity.md)
* [颜色、光线和材料](./color-light-and-materials.md)