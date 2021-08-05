---
title: 3D 应用启动器设计指南
description: 3D 应用启动器是用户混合现实房屋中的"物理"对象，用户可以选择该对象来启动应用。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、设计、3D 应用启动器、沉浸式头戴显示设备、实时立方体、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、UWP、Win32、照明、颜色
ms.openlocfilehash: 2d93930d63b251aa91d77c96b4d5250baba54c51de50388f690b3588b1580761
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188483"
---
# <a name="3d-app-launcher-design-guidance"></a>3D 应用启动器设计指南

将沉浸式 WINDOWS MIXED REALITY VR (头戴显示设备) ，请输入Windows Mixed Reality设备。 该房屋被可视化为一个被水与水环绕的四面环上的房屋，但你可以选择[](../design/add-custom-home-environments.md)其他环境，甚至可以创建自己的) 。 在家庭空间中，用户可以随意排列和组织他们关心的任何方式的 3D 对象和应用。 **3D 应用启动器** 是用户混合现实房屋中的"物理"对象，用户可以选择该对象来启动应用。

![示例：Floaty Bird 3D 应用启动器](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Floaty Bird 3D 应用启动器示例 (虚构应用)*

## <a name="3d-app-launcher-creation-process"></a>3D 应用启动器创建过程

创建 3D 应用启动器有 3 个步骤：

1. 本文中的设计和 (概念) 
2. [建模和导出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 将其集成到应用程序中：
    * [UWP 应用](implementing-3d-app-launchers.md)
    * [Win32 应用](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>设计概念

### <a name="fantastic-yet-familiar"></a>非常熟悉

应用Windows Mixed Reality所位于的环境是一部分熟悉的环境，也是一部分"奇幻/sci-fi"。 最佳启动器遵循此世界的规则。 考虑如何从应用中获得熟悉的代表性对象，但会改变一些实际现实规则。 将产生 Magic。

### <a name="intuitive"></a>直观

查看应用启动器时，其用途（启动应用）应该是明显的，不应引起任何混淆。 例如，请确保启动器是应用的明显代表，它不会因为应用中的一点小花而悬崖小屋。 应用启动器应邀请用户进行触摸/选择。

![示例：全新注释 3D 应用启动器](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*新注释 3D 应用启动器示例 (虚构应用)*

### <a name="home-scale"></a>家庭规模

3D 应用启动器悬崖小屋其默认大小应该与空间中的其他"物理"对象有意义。 如果你将启动器放在房屋工厂或一些房屋旁边，它应感觉像家一样，大小不同。 一个很好的起点是查看它如何查看 30 厘米，但请记住，用户可以增加或减少它（如果愿意）。

### <a name="own-able"></a>自己能够

应用启动器应感觉就像一个人在空间中拥有的对象。 他们将几乎与这些事物围绕在一起，因此启动器应该像用户认为足以寻找并靠近你所需的内容一样。

![示例：Astro Warp 3D 应用启动器](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Astro Warp 3D 应用启动器示例 (虚构应用)*

### <a name="recognizable"></a>识别

3D 应用启动器应该立即向看到它的用户表达"应用的品牌"。 如果应用中有星形字符或特别可识别的对象，我们建议将该对象用作设计的重要部分。 在混合现实世界中，对象将吸引用户的兴趣，而不只是一个徽标。 可识别的对象快速清楚地传达品牌。

### <a name="volumetric"></a>体积

应用不仅仅是将徽标放在平面上并调用它一天。 启动器应像用户空间中一个令人心动的 3D 物理对象。 一个好方法是假设应用在 Macy 的"开天节"中将拥有一个气球。 问一下自己，当人们从街道走来时，它会是什么？ 从所有查看角度来看，什么看起来都不错？

:::row:::
    :::column:::
        ![仅徽标 ](images/20171016-140436-mixedreality-640px.jpg) *徽标*
    :::column-end:::
    :::column:::
        ![使用字符更可识别 ](images/20171016-140557-mixedreality-640px.jpg) *使用字符的可识别性*
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![平面方法（并不意外）感觉平面方法，这一 ](images/20171016-155101-mixedreality-640px.jpg) *点* 并不意外
    :::column-end:::
    :::column:::
        ![Volumetric 方法更好地展示应用 ](images/20171016-161407-mixedreality-640px.jpg) *Volumetric 方法，更好地展示应用*
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a>使用技巧 3D 模型

* 为应用启动器规划维度时，大约需要 30 cm 的多维数据集。 因此，大小比率为 1：1：1。
* 模型必须不足 10，000 个多边形。 [详细了解 LOD 的三角形计数和 (级别) ](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* 在沉浸式头戴显示设备上进行测试。
* 尽可能将详细信息生成到模型的几何图形中 – 不依赖于纹理了解详细信息。
* 生成"水紧密"闭合几何图形。 没有未建模的孔。
* 在 对象中使用自然材料。 Imagine现实世界中设计它。
* 确保模型在不同距离和大小下读取良好。
* 模型准备就绪后，请阅读导出 [资产准则](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)。

![纹理中具有细微细节的模型](images/20171013-143334-mixedreality-640px.jpg)<br>
*纹理中具有细微细节的模型*

### <a name="what-to-avoid"></a>要避免的内容

* 请勿使用高对比度详细信息或小型的繁忙模式和纹理。
* 请勿使用精简几何图形 – 它无法很好地在距离上工作，并且会损坏别名。
* 请勿让模型的某些部分超出 1：1：1 大小比。 这将创建缩放问题。

![避免高对比度、小忙模式](images/20171013-143603-mixedreality-640px.jpg)<br>
*避免高对比度、小型、繁忙模式*

## <a name="how-to-handle-type"></a>如何处理类型

* 我们建议你的类型占用大约 1/3 的应用启动器 (或) 。 类型是主要内容，它使用户知道启动器实际上是一个启动器，因此，如果它很大，就很好。
* 避免使类型成为超宽类型 - 尝试将其保持在应用启动器核心维度的范围内， (或) 。
* 平面类型可以正常工作，但在某些角度和某些环境中可能很难查看。 可以考虑在它后面放置一个可靠的对象或背景，以帮助实现此目的。
* 在 3D 中向类型添加维度感觉不错。 将类型的边着色为其他较深的颜色有助于提高可读性。

:::row:::
    :::column:::
        ![没有背景的平面类型可能难以从特定角度查看，在某些环境中，没有背景的平面类型在某些角度和特定环境中可能难以 ](images/flattype-640px.png) *查看*
    :::column-end:::
    :::column:::
        ![具有内置背景的类型可以很好地使用具有内置背景的类型 ](images/flattypeandbkg-640px.png) *可以很好地工作*
    :::column-end:::
    :::column:::
        ![如果对边进行着色，如果对边进行着色，拉伸类型可以很好地 ](images/20171016-160221-mixedreality-640px.jpg) *工作*
    :::column-end:::
:::row-end:::

**键入工作颜色**

* White
* 黑色
* 亮半饱和颜色

![键入正常工作的颜色。](images/20171016-112111-mixedreality-640px.jpg)<br>
*键入工作颜色*

### <a name="colors-to-avoid"></a>要避免的颜色

导致问题的类型颜色包括：

* 中音
* 灰色
* 过度饱和的颜色或不饱和的颜色

![键入导致问题的颜色。](images/20171016-112246-mixedreality-640px.jpg)<br>
*导致问题的类型颜色*

## <a name="lighting"></a>照明

应用启动器照明来自悬崖小屋环境。 请务必在整个房屋中的多个位置测试启动器，以便它在光线和阴影中看起来都不错。 好消息是，如果已遵循本文档中的其他设计指南，则启动器应采用良好的形状，适用于整个悬崖小屋。

测试启动器在环境中各种光线中的外观的不错位置是工作室、媒体房间、位于外的任何位置，以及位于背面 (环境的具体区域) 。 另一个不错的测试是，将它置于半浅和半阴影中，并查看它的外观。

![确保启动器在光线和阴影中都看起来良好。](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*确保启动器在浅色和阴影下看起来都不错*

## <a name="texturing"></a>纹理

### <a name="authoring-your-textures"></a>创作纹理

3D 应用启动器最终格式将是 .glb 文件，该文件使用 PBR (基于物理的渲染) 管道。 这可能是一个复杂的过程 - 现在，如果尚未使用技术艺术家，现在是一个不错的时候。 如果你是一位好心的 DIY-er，那么在开始之前，花时间研究并学习 [PBR](https://wiki.polycount.com/wiki/PBR) 术语以及发生的情况有助于避免常见错误。 

![示例：Fresh Note 应用](images/pbr-freshnote1-640px-500px.png)<br>
*新注释 3D 应用启动器示例 (虚构应用)*

### <a name="recommended-authoring-tool"></a>推荐的创作工具

我们建议使用 [由一位](https://www.allegorithmic.com/products/substance-painter) 作者为"管理"的"国家/服务"创作最终文件。 如果不熟悉在《元子》中创作 PBR 着色器，请观看以下 [教程](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)。

 ([3D-使用](https://3dcoat.com/home/)[、Quixel Suite 2](https://quixel.se/suite2/)或[Marmoset Toolbag，](https://www.marmoset.co/toolbag/)如果更熟悉其中一种，则也) 

### <a name="best-practices"></a>最佳实践

* 如果应用启动器对象是针对 PBR 创作的，则对于应用启动器环境，悬崖小屋转换。
* 着色器需要金属/粗糙度工作流程 - Unreal PBR 着色器是一个接近的简写。
* 导出纹理时，请记住 [建议的纹理](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) 大小。
* 请确保生成用于实时照明的对象，这意味着：
  * 避免烘焙阴影 – 或绘制的阴影
  * 避免纹理中的烘焙照明
  * 使用 PBR 材料创作包之一获取为着色器生成的正确地图

## <a name="see-also"></a>另请参阅

* [创建 3D 模型以用于混合现实主页](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [实现 3D 应用启动器（UWP 应用）](implementing-3d-app-launchers.md)
* [实现 3D 应用启动器（Win32 应用）](implementing-3d-app-launchers-win32.md)
