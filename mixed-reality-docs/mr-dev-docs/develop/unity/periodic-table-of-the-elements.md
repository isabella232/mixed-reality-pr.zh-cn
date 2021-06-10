---
title: 元素周期表
description: 了解如何将对象集合与元素周期表示例应用一起，在具有各种图面类型的 3D 空间中布局对象数组。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality， 设计， 示例应用， 控件， MRTK， 混合现实工具包， Unity， 示例应用， 示例应用， 开源， Microsoft Store， HoloLens， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
ms.openlocfilehash: ed8c35fc6467322c25b92924b134f176fa4a9b47
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743412"
---
# <a name="periodic-table-of-the-elements"></a>元素周期表

>[!NOTE]
>本文讨论我们在混合现实设计实验室中创建的探索示例，我们在该实验室[](https://github.com/Microsoft/MRDesignLabs_Unity)中分享有关混合现实应用开发的学习和建议。 随着我们进行新的发现，与设计相关的文章和代码将不断发展。

[元素周期表是](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) Microsoft 混合现实设计实验室提供的开源示例应用。 了解如何使用对象集合 在具有各种图面类型的 3D 空间中布局 **[对象的数组](../../design/object-collection.md)**。 另请了解如何创建可交互对象，以响应 HoloLens 中的标准输入。 可以使用此项目的组件创建自己的混合现实应用体验。

![Elements 应用的周期表](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a>演示视频 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

使用 HoloLens 2 记录混合现实捕获

## <a name="about-the-app"></a>关于应用

元素周期表将三维空间中化学元素及其每个属性可视化。 它结合了 HoloLens 的基本交互，例如凝视和敲击。 用户可以了解具有动画 3D 模型的元素。 它们可以直观地了解元素的电子外壳及其由质子和中子组成。

## <a name="background"></a>背景

我第一次体验 HoloLens 后，知道我想在混合现实中试验定期表应用。 由于每个元素都有许多以文本显示的数据点，因此我认为在 3D 空间中浏览版式撰写是一个很好的主题。 为用户提供可视化元素电子模型的机会是此项目的另一个有趣部分。

## <a name="design"></a>设计

对于周期表的默认视图，我假设三维框将包含每个元素的电子模型。 每个框的图面是半透明的，以便用户可以大致了解元素的音量。 通过凝视和敲击，用户可以打开每个元素的详细视图。 为了在表视图和详细信息视图之间顺利且自然地转换，我使其类似于实际打开的框的物理交互。

![设计草图](images/640px-sketch20170406.jpg)<br>
*设计草图*

在详细信息视图中，我想要使用 3D 空间中美观呈现的文本可视化每个元素的信息。 动画 3D 电子模型显示在中心区域，可以从不同角度查看。

![交互](images/640px-periodictable-interaction.jpg)

![原型](images/640px-periodictable-prototypes.jpg)<br>
*交互原型*

用户可以通过通过按表底部的按钮来更改表面类型 - 它们可以在平面、柱面、球体和散点图之间切换。

## <a name="common-controls-and-patterns-used-in-this-app"></a>此应用中使用的常见控件和模式

### <a name="interactable-object-button"></a>可交互对象 (按钮) 

[可交互](../../design/interactable-object.md) 对象是一个对象，可以响应基本的 HoloLens 输入。 它作为预制/脚本提供，可轻松应用于任何对象。 例如，可以使场景中的咖啡杯交互，并响应凝视、敲击、导航和操作手势等输入。 [了解详细信息](../../design/interactable-object.md)

![nteractable 对象](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>对象集合

[对象](../../design/object-collection.md) 集合是一个对象，可帮助你以各种形状布局多个对象。 它支持平面、柱面、球体和散点图。 可以配置其他属性，例如半径、行数和间距。 [了解详细信息](../../design/object-collection.md)

![对象集合](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>技术详细信息

可以在混合现实设计实验室 GitHub 上找到 Elements 应用的周期表的脚本和 [预制件](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)。

## <a name="porting-story-for-hololens-2"></a>移植适用于 HoloLens 2

阅读有关如何使用元素应用周期表更新HoloLens 2性交互的信息。

[元素周期表 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>用户体验设计师 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另请参阅

* [MRTK 示例中心](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [表面](sampleapp-surfaces.md) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [元素周期表 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [星系探索者 2.0](galaxy-explorer-update.md)