---
title: 元素周期表
description: 了解如何使用不同的图面类型在三维空间布局对象的数组，使用带有元素示例应用的定期表的对象集合。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计，示例应用，控件，MRTK，混合现实工具包，Unity，示例应用，示例应用，开源，Microsoft Store，HoloLens，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: 19307b310d104f418e4f7739b0576c63407d83fd
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759733"
---
# <a name="periodic-table-of-the-elements"></a>元素周期表

>[!NOTE]
>本文讨论了我们在 [混合现实设计实验室](https://github.com/Microsoft/MRDesignLabs_Unity)中创建的探索示例，这是我们与混合现实应用开发的知识和建议。 我们设计相关的文章和代码将随着我们的新发现而发展。

[定期表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) 是 Microsoft 混合现实设计实验室的开源示例应用。 了解如何使用 **[对象集合](../../design/object-collection.md)** 在三维空间中布局对象的数组。 还将了解如何创建响应 HoloLens 标准输入的种不可交互对象。 您可以使用此项目的组件来创建自己的混合现实应用程序体验。

![元素应用的 Period 表](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a>演示视频 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

使用混合现实捕获记录了 HoloLens 2

## <a name="about-the-app"></a>关于应用

元素的周期性表在三维空间中直观显示化学元素及其每个属性。 它结合了 HoloLens 的基本交互，如注视和分流。 用户可以了解带有动画3D 模型的元素。 它们可以直观地了解元素的 electron shell 及其核心，这是由 protons 和 neutrons 组成的。

## <a name="background"></a>背景

在我首次体验 HoloLens 后，我知道我想在混合现实中试用定期表应用程序。 由于每个元素都有多个与文本一起显示的数据点，因此，我认为这对于浏览三维空间中的排版组合非常重要。 使用户有机会直观显示元素的 electron 模型是此项目的另一个有趣的部分。

## <a name="design"></a>设计

对于周期性表的默认视图，我想要将包含每个元素的 electron 模型的三维方框。 每个框的表面都是透明的，这样用户就可以大致了解元素的音量。 使用注视和空中点击，用户可以打开每个元素的详细视图。 为了使表视图和详细信息视图之间的过渡平滑和自然，我使其类似于实际生活中打开的方框的物理交互。

![设计草图](images/640px-sketch20170406.jpg)<br>
*设计草图*

在详细信息视图中，我想要将每个元素的信息可视化到三维空间中完美呈现的文本。 动画 3D electron 模型将显示在中心区域，并且可以从不同角度查看。

![交互](images/640px-periodictable-interaction.jpg)

![原型](images/640px-periodictable-prototypes.jpg)<br>
*交互原型*

用户可以通过点击表格底部的按钮来更改曲面类型，它们可以在平面、圆柱、球和散点之间切换。

## <a name="common-controls-and-patterns-used-in-this-app"></a>此应用中使用的公共控件和模式

### <a name="interactable-object-button"></a>种不可交互对象 (按钮) 

[种不可交互对象](../../design/interactable-object.md) 是一个对象，它可以响应基本的 HoloLens 输入。 它作为 prefab/script 提供，你可以轻松地将其应用于任何对象。 例如，你可以在场景种不可交互中发出咖啡杯，并对输入（如注视、分流、导航和操作手势）做出响应。 [了解详细信息](../../design/interactable-object.md)

![nteractable 对象](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>对象集合

[对象集合](../../design/object-collection.md) 是一个对象，可帮助您在不同的形状中布局多个对象。 它支持平面、圆柱、球面和散点图。 可以配置其他属性，如 radius、行数和间距。 [了解详细信息](../../design/object-collection.md)

![对象集合](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>技术详细信息

可在 [混合现实设计实验室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)上查找元素应用的定期表的脚本和 prototyping。

## <a name="porting-story-for-hololens-2"></a>针对 HoloLens 2 的移植故事

阅读有关如何用 HoloLens 2 的 instinctual 交互更新元素应用的定期表的文章。

[元素周期表 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>用户体验设计师 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另请参阅

* [MRTK 示例中心](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/example-scenes/example-hub.md) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [表面](sampleapp-surfaces.md) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [元素周期表 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [星系探索者 2.0](galaxy-explorer-update.md)