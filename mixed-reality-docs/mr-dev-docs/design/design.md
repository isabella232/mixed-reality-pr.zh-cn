---
title: 开始设计和原型制作
description: 如果已做好创建方面的准备工作，请了解开始设计和原型制作所需的基本概念。
author: grbury
ms.author: grbury
ms.date: 08/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, 发现, 分发, 索引, 登陆页, 设计, 开发, 教程, 示例应用, 基础知识, 案例研究, 资源, HoloLens 操作指南, 开源项目, 核心概念, 交互
ms.openlocfilehash: 2ee127b05a8ad88e49eda6d088f84e895aeaf511
ms.sourcegitcommit: 4e618948e1e2e0baf4bb3e8b67513fa7716aa815
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2020
ms.locfileid: "94361685"
---
# <a name="start-designing-and-prototyping"></a>开始设计和原型制作

![混合现实设计摘要](images/design-hero-image.png)

混合现实应用程序与当今世界上任何其他应用程序都不同，设计它们是一项很难的工作。 你不仅要考虑到正在创建的真实世界和虚拟世界的新组合，还必须考虑它们带来的新型用户体验。 由于混合现实很大，因此我们在其设计范围内选择了要点，并在下面将它们布置为一系列检查点。 这些检查点应该是连续的，但如果你已经有了一定的了解，则可以随时跳转到以下任何部分。

## <a name="design-checkpoints"></a>设计检查点

使用以下检查点将应用程序创意和概念带入混合现实的世界。

### <a name="1-getting-started"></a>1.入门

与所有历程一样，设计混合现实应用程序的冒险之旅从基础开始。 我们建议你自行熟悉[什么是混合现实](../discover/mixed-reality.md)以及[什么是全息影像？](../discover/hologram.md)文章，让大脑为沉浸式设计做好准备。 完成通读后，你就可以开始混合现实设计历程了！

![来自“设计全息影像”应用的入门 GIF](images/HandTracking2.gif)

|  Checkpoint  |  业务成效  |
| --- | --- |
| [扩展设计过程](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | 亲眼见证从 Microsoft 内外的设计师处收集的混合现实设计过程 |
| [混合现实应用的类型](types-of-mixed-reality-apps.md) | 确定你的应用体验在混合现实范围内的位置 |
| [“设计全息影像”应用](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) | 了解混合现实 UX 设计的基础知识，只需深入了解混合现实行为以及与创建出色 HoloLens 应用相关的提示和建议即可（可在 HoloLens 2 中从 Microsoft Store 下载） |

### <a name="2-core-concepts"></a>2.核心概念

无论是针对 VR 还是 AR 进行开发，都有几个核心概念适用于设计流畅的沉浸式体验。 了解用户的观点、定位对象并确保每个人都舒适安全是你在历程的这一阶段的头等大事。 本部分结束时，你将有一个坚实的基础来进行交互设计。

![核心概念示例图像](images/fragments-750px.jpg)

|  概念  |  业务成效  |
| --- | --- |
| [全息帧](holographic-frame.md) | 了解用户佩戴着其头戴显示设备时如何看到覆盖到现实世界的内容 |
| [坐标系统](coordinate-systems.md) | 了解如何将全息影像置于世界上对用户有意义的各个位置，该位置可能是用户的物理室，也可能是你创建的某个虚拟领域 |
| [空间映射](spatial-mapping.md) | 在用户的世界中锚定对象，并利用真实世界的物理表面 |
| [舒适感注意事项](comfort.md) | 通过以模仿自然世界的方式创建和呈现沉浸式内容，确保用户的舒适感和安全性 |

### <a name="3-interaction-design"></a>3.交互设计

无论虚拟体验有多漂亮和拟真，如果不能进行交互，也都是没有用的。 本部分将向你介绍基本交互模型、手势和运动控制器、使用语音输入以及收集用户的眼部跟踪数据。 本部分结束后，你便已准备好处理设计历程中的最后一个大主题：用户体验。

![交互设计因素](images/UX_Hero_Manipulation.jpg)

|  概念  |  业务成效  |
| --- | --- |
| [交互模型](interaction-fundamentals.md) | 通过手部、眼部和语音输入向用户提供本能交互 |
| [手和运动控制器](hands-and-tools.md) | 了解如何在靠近用户手的位置触摸和操纵全息影像，或者通过精确的交互在远距离触摸和操纵全息影像 |
| [语音输入](voice-input.md) | 在沉浸式应用中使用语音命令作为输入来控制周围的全息影像和环境  |
| [眼部跟踪](eye-tracking.md) | 使用有关用户正在查看的内容的信息，在全息体验中增加一个新层次的上下文和人工理解 |

### <a name="4-user-experience-elements"></a>4.用户体验元素

现在你已经掌握了基本的交互，你可以专注于用户体验元素的更细微之处，以及如何使它们适应混合现实的独特环境。 你将了解常见的行为、资产设计、对象缩放和版式，所有这些都是为了使你的应用对用户尽可能地直观。 本部分标志着混合现实官方设计历程的结束，但在[后续步骤？](#whats-next)部分中还有更多资源供你继续了解。

![UX 元素](images/UX_Hero_BoundingBox.jpg)

|  概念  |  业务成效  |
| --- | --- |
| [常用控件和行为](app-patterns-landingpage.md) | 了解常用空间交互和 UI 构建基块 |
| [颜色、光线和材料](color-light-and-materials.md) | 设计适用于混合现实的质量资产，其考虑了颜色、照明和材料 |
| [对象规模](scale.md) | 整合尽可能多的现实世界视觉提示给我们，帮助你的用户了解对象的位置、大小以及组成部分 |
| [版式](typography.md) | 在三维空间中使用清晰可读的文本，为用户提供所需的重要信息 |

## <a name="whats-next"></a>下一步操作

设计师的工作一直在更新，尤其是在学习以新的范式创建沉浸式体验时。 以下各部分将带你跨越已完成的初学者级别设计材料并进入混合现实开发的世界。 这些主题和资源不按任何顺序排列，因此可随意探索！

### <a name="choose-a-prototyping-option"></a>选择原型制作选项  

:::row:::   
    :::column:::    
       [![了解 Unity](images/logo-unity.png)](https://learn.unity.com/)<br>
        **[了解 Unity](https://learn.unity.com/)**<br>
        了解如何使用 Unity 创建交互式体验。 从头至尾从实践中学习。
    :::column-end:::    
    :::column:::    
        [![混合现实工具包 (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)<br>
        **[混合现实工具包 (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**<br>  
        使用空间交互和 UI 构建基块，通过 Unity 立即开始混合现实设计和开发。   
    :::column-end:::
    :::column:::    
        [![混合现实设计实验室](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)<br>
        **[混合现实设计实验室](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**<br>  
        获取示例应用，这些应用会演示如何使用 MRTK 的构建基块来创建美好的混合现实体验。
    :::column-end:::        
    :::column:::    
        [![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)<br>
        **[Microsoft Maquette](https://www.maquette.ms/)**<br>  
        为 VR 而设计。 可以使用 Microsoft Maquette 快速便捷地进行沉浸式空间原型制作。 
    :::column-end:::    
:::row-end:::

<br>

---

### <a name="additional-resources"></a>其他资源

:::row:::
    :::column:::
       [![了解基础知识](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)<br>
        **[了解基础知识](../discover/get-started-with-mr.md#understand-the-basics)**<br>
        更好地了解是什么定义了混合现实，以及如何使用混合现实。
    :::column-end:::
    :::column:::
        [![参加活动](images/74-16.png)](../whats-new/sf-academy-events.md)<br>
         **[参加活动](../whats-new/sf-academy-events.md)**<br>
        查看硬件并获取动手教程，以便创建第一个 HoloLens 2 应用程序。
    :::column-end:::
    :::column:::
        [![安装工具](images/74-17.png)](../develop/install-the-tools.md)<br>
         **[安装工具](../develop/install-the-tools.md)**<br>
        使用安装清单获取为 HoloLens 和混合现实构建应用所需的工具。
    :::column-end:::
    :::column:::
        [![开始开发](images/74-18.png)](../develop/development.md)<br>
        **[开始开发](../develop/development.md)**<br>
        根据技能水平、工作风格或平台兴趣选择开发路径。
    :::column-end:::
:::row-end:::

<br>

<br>