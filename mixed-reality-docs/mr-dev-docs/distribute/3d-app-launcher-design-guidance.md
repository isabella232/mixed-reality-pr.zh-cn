---
title: 3D 应用启动器设计指南
description: 3D 应用启动器是用户混合现实房子中的 "物理" 对象，他们可以选择启动应用。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计，3D 应用程序启动器，沉浸式耳机，活动立方体
ms.openlocfilehash: 884d05b8b8ef7e15f5c65a411cf500b0d4dc598c
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677769"
---
# <a name="3d-app-launcher-design-guidance"></a>3D 应用启动器设计指南

当你在 Windows Mixed Reality 沉浸式 (VR) 耳机上，你可以输入 Windows Mixed Reality 主页，在山上和水 (周围的 cliff 上以房子显示，但你可以 [选择其他环境，甚至创建自己的](../design/add-custom-home-environments.md)) 。 在此家中，用户可以自由地按所需的方式排列和组织3D 对象和应用。 **3d 应用启动器** 是用户混合现实房子中的 "物理" 对象，他们可以选择启动应用。

![示例： Floaty 鸟3D 应用启动器](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Floaty 鸟3D 应用启动器示例 (虚构应用)*

## <a name="3d-app-launcher-creation-process"></a>3D 应用程序启动器创建过程

创建三维应用启动器有三个步骤：

1. 本文 (设计和 concepting) 
2. [建模和导出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 将其集成到应用程序中：
    * [UWP 应用](implementing-3d-app-launchers.md)
    * [Win32 应用](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>设计概念

### <a name="fantastic-yet-familiar"></a>太棒了

应用启动器所在的 Windows Mixed Reality 环境是部分熟悉的部分精巧/科幻。 最佳启动器遵循这一领域的规则。 考虑如何从应用程序中获取熟悉的代表对象，但要折上一些实际现实规则。 将产生幻数。

### <a name="intuitive"></a>直观

当你查看应用程序启动器时，启动你的应用程序的目的是非常明显，不会造成任何混淆。 例如，请确保您的启动器是您的应用程序的一个显而易见的代表，这不会对 Cliff 房子中的一 décor。 应用启动器应邀请人员触摸/选择。

![示例：全新备注3D 应用启动器](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*全新说明3D 应用启动器示例 (虚构应用)*

### <a name="home-scale"></a>主比例

Cliff 房子中的三维应用启动器及其默认大小对于空间中的其他 "物理" 对象应该是有意义的。 如果将您的启动器置于附近（比如，房屋植物或某个家具），则应在家中、按大小进行调整。 很好的起点是查看它如何以30立方米为单位显示，但请记住，如果用户喜欢，可以增加或减少。

### <a name="own-able"></a>自己可以

应用启动器应感觉到某个人很高兴能够在他们的空间中使用。 它们几乎都是通过这些内容来处理的，因此启动器应喜欢用户认为是足以寻找并保留附近的内容。

![示例： Astro 扭曲3D 应用启动器](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Astro)  (虚构应用程序启动器示例*

### <a name="recognizable"></a>识别

你的3D 应用程序启动器应立即将 "你的应用程序" 的品牌表达为看到它的人。 如果应用中有星形或特别可识别的对象，我们建议将其作为设计的一个很大的组成部分。 在混合现实世界中，对象对用户的兴趣比单独的徽标要多。 可识别对象快速、清晰地传达品牌。

### <a name="volumetric"></a>容量耗尽

您的应用程序只需将徽标置于平整平面上，并一整天就会调用它。 您的启动器应类似于用户空间中令人兴奋的、三维的物理对象。 一种很好的方法是假设您的应用程序将在 Macy 的感恩节日醒目中有一个气球。 问问自己，究竟是什么人在街道下出现了什么呢？ 所有查看角度看起来都很好？

:::row:::
    :::column:::
        ![仅徽标 ](images/20171016-140436-mixedreality-640px.jpg) *徽标*
    :::column-end:::
    :::column:::
        ![更能识别字符更可识别的字符 ](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![平面方法，而不是令人吃惊的方式，而不是令人吃惊的简单 ](images/20171016-155101-mixedreality-640px.jpg) *方法*
    :::column-end:::
    :::column:::
        ![容量耗尽方法更好地展示您的应用程序 ](images/20171016-161407-mixedreality-640px.jpg) *容量耗尽方法更好地展示您的应用程序*
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a>适用于三维模型的提示

* 规划应用程序启动器的维度时，会针对大致的30cm 多维数据集。 因此，1:1:1 大小的比率。
* 模型必须在10000多边形下。 [详细了解 (LODs 的三角形计数和详细级别) ](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* 在沉浸式耳机上测试。
* 在可能的情况下，将详细信息生成到模型的几何图形–不要依赖于纹理获取详细信息。
* 生成 "水紧密型" 闭合几何。 没有在中建模的孔。
* 使用对象中的自然材料。 想象一下在现实世界中手工制作。
* 请确保您的模型在不同的距离和大小上都能正常阅读。
* 模型准备就绪后，请阅读 [导出资产的准则](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)。

![纹理中包含微妙细节的模型](images/20171013-143334-mixedreality-640px.jpg)<br>
*纹理中包含微妙细节的模型*

### <a name="what-to-avoid"></a>要避免的内容

* 不要使用高对比度详细信息或较小、繁忙的模式和纹理。
* 不要使用精简几何-它在某种程度上并不能很好地工作，并且不会产生错误。
* 不要让模型的一部分扩展到超过1:1:1 大小的比率。 它将创建缩放问题。

![避免高对比度、小型繁忙模式](images/20171013-143603-mixedreality-640px.jpg)<br>
*避免高对比度、小型、繁忙的模式*

## <a name="how-to-handle-type"></a>如何处理类型

* 建议你的类型包含大约1/3 的应用启动器 (或多个) 。 类型主要是使用户了解你的启动程序，事实上，启动程序很好，因为它非常重要。
* 避免使类型成为超级类型-尝试将其放在应用程序启动器核心维度的范围内 (更多或更少) 。
* 平面类型可正常运行，但请注意，在某些角度和某些环境下，可能难以查看。 您可以考虑将它放在一个实体对象或背景上，以帮助解决此情况。
* 将维度添加到您的类型非常适合3D。 将类型的两侧的底纹着色为不同、更暗的颜色可帮助提高可读性。

:::row:::
    :::column:::
        ![从特定角度看，无背景的平面类型很难查看，在某些环境中， ](images/flattype-640px.png) *不能从特定角度和某些环境中查看无背景的平面类型*
    :::column-end:::
    :::column:::
        ![带有内置背景的类型可以正常工作 ](images/flattypeandbkg-640px.png) *，且内置背景可以正常工作*
    :::column-end:::
    :::column:::
        ![如果 ](images/20171016-160221-mixedreality-640px.jpg) *对边进行着色* ，则拉伸类型可以很好地工作
    :::column-end:::
:::row-end:::

**键入工作的颜色**

* 白色
* 黑色
* 亮半饱和颜色

![键入工作的颜色。](images/20171016-112111-mixedreality-640px.jpg)<br>
*键入工作的颜色*

### <a name="colors-to-avoid"></a>要避免的颜色

导致问题的类型可能包括：

* 中声
* 灰色
* 过度饱和颜色或 desaturated 颜色

![键入导致问题的颜色。](images/20171016-112246-mixedreality-640px.jpg)<br>
*键入导致问题的颜色*

## <a name="lighting"></a>照明

应用启动器的照明来自 Cliff 房子环境。 请确保在整个房子内的多个位置测试启动器，使其看起来很好。 好消息是，如果您按照本文档中的其他设计指南进行了，则您的启动器应该非常适合 Cliff 房子中的大多数照明。

很好的地方就是测试启动器在环境中的各种灯光上的外观，就是工作室、Media 房间、后 Patio (具体区域以及草地) 。 另一种好的测试是将它放在半轻和半阴影上，并查看其外观。

![请确保启动器在灯光和阴影中都看起来很好。](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*请确保启动程序在灯光和阴影中都看起来很好*

## <a name="texturing"></a>绘制

### <a name="authoring-your-textures"></a>创作纹理

三维应用启动器的结束格式将为 glb 文件，该文件使用 .PBR (以物理方式呈现) 管道。 这可能是一项棘手的过程-现在最好是使用技术音乐家（如果尚未这样做）。 如果你是无畏的 DIY，则在开始之前，请花时间 [研究并了解 .pbr 术语](https://wiki.polycount.com/wiki/PBR) ，在幕后，这将有助于你避免常见错误。 

![示例：全新备注应用](images/pbr-freshnote1-640px-500px.png)<br>
*全新说明3D 应用启动器示例 (虚构应用)*

### <a name="recommended-authoring-tool"></a>推荐的创作工具

建议通过 Allegorithmic 使用 [材料刷](https://www.allegorithmic.com/products/substance-painter) 来创作最终文件。 如果你不熟悉在物质刷中创作 .PBR 着色器，请参阅以下 [教程](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)。

如果你更熟悉其中的一个，则 (交替使用 [三维 Coat](https://3dcoat.com/home/)、 [Quixel Suite 2](https://quixel.se/suite2/)或 [Marmoset Toolbag](https://www.marmoset.co/toolbag/) 。 ) 

### <a name="best-practices"></a>最佳实践

* 如果你的应用启动器对象是为 .PBR 编写的，则为 Cliff 房子环境转换该对象应该非常简单。
* 着色器应为金属/粗糙度工作流– Unreal .PBR 着色器是一个关闭的传真。
* 导出纹理时，请牢记 [建议的纹理大小](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) 。
* 请确保为实时照明生成对象，这意味着：
  * 避免融入阴影-或绘制阴影
  * 避免纹理中的融入光照
  * 使用其中一个 .PBR 材料创作包获取为着色器生成的正确地图

## <a name="see-also"></a>请参阅

* [创建用于混合现实主页的3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [实现 3D 应用启动器（UWP 应用）](implementing-3d-app-launchers.md)
* [实现 3D 应用启动器（Win32 应用）](implementing-3d-app-launchers-win32.md)
