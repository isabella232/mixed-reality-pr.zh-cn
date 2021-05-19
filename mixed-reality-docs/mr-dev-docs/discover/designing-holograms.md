---
title: 设计全息影像
description: 通过 Microsoft 的新设计全息影像应用程序了解混合现实。
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK， 混合现实工具包， 全息影像， 设计全息影像， 学习， 示例应用， 混合现实头戴显示设备， 虚拟现实头戴显示设备， 什么是虚拟现实
ms.openlocfilehash: 6e37c3f1ba98f202addb9c323632bca8bffae3b6
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143629"
---
# <a name="the-making-of-designing-holograms"></a>设计全息影像的制作

> [!NOTE]
> 请允许一个小的加载窗口，以说明此页上的所有冷 GIF 和嵌入式视频。

了解如何为混合现实进行设计可能很难，因为媒体并不总是能很好地转换为 2D 设计过程。 在 Microsoft，我们创建了一个免费应用，HoloLens 2帮助你第一手了解混合现实 UX 设计的基本知识。 设计全息影像应用的独特方法深入探讨混合现实行为、提示和建议，以帮助你创建自己的具有吸引力且令人惊叹的 HoloLens 应用。 从 Microsoft 混合现实设计Microsoft Store下载应用并学习！

> [!div class="nextstepaction"]
> [下载设计全息影像应用](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![设计全息影像演示房间中头部跟踪场景的动画 GIF](images/designing-holograms/demo-room.gif)

*设计全息影像的演示 (也称为"房屋")*

## <a name="designing-for-mixed-reality"></a>针对混合现实进行设计

和许多人一样，我过去设计移动应用。 从 2D 设计世界开始，进入空间计算领域（现在一切都位于全球）是一个显著转变。 在混合现实中，应用不再局限于 2D 屏幕;事实上，它们几乎是免费的，放置在现实世界中并与真实对象交互。

就我来说，将 3D 体验连接到传统的 2D 设计过程是混合现实开发最具挑战性方面。 在与客户的聊天中，我听说过"我了解要包含哪些功能以及如何启动和运行这些功能。 这是代码，我可以按照文档和教程操作，但用户体验如何？ 有很多功能、不同的输入选项、不同的方案和物理环境，这一点非常巨大"。

![从圣马力诺2中的 HoloLens 2 设计研讨会开始的图像，位于旧金山 ](images/designing-holograms/workshop.jpeg)
 *2 的 Hololens 2 设计研讨会* 中

## <a name="an-opportunity-to-teach"></a>机会

这并不是很明显，但会出现一个极好的机会，将混合现实用作一种用于教授的媒介。

设计全息影像是介绍混合现实设计概念和建议的视觉体验。 这只是你以及演示混合现实设计概念的虚拟老师。 一切都是从第三人的角度来看，它在自己的空间中实现了丰富的体验。

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

*设计全息影像尾端视频*

## <a name="exploring-the-doll-house"></a>探索娃房子

娃房子是我们在整个应用程序中使用的虚拟环境。 环境为 80 x 60 x 40-cm，其中包含大多数房间共有的基本元素，如墙壁、灯、家具、桌子和电视。 娃房子是应用程序体验的主要 protagonist，因此我们需要确保它在任何环境中都能正常工作。 将其视为一个小型演示空间，用于可视化各种混合现实概念。

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
*Dollhouse 调整行为的视频*

### <a name="11-vs-110-prototypes"></a>1:1 与1:10 原型

我们最初假设，1:1 的演示会令人吃惊，几乎与查看真实的老师一样。 用户将看到老师在实际生活中看到的一切内容。 但是，我们立即意识到存在以下几个问题：

- 大多数开发人员会在办公室或比演示房间小的房间内运行应用程序，因此不适合。
- 显示是累加的，这意味着整个虚拟环境将覆盖在用户的空间上。 这可能会使两个表（可能为 double couches）和不对齐的墙壁产生混淆。
- 最差的一个虚拟环境受到视场的严格约束。

当我们尝试了一个微型 1：10 刻度时，结果是一个真实的房间的精彩眼睛视图。 你可以同时从任何角度查看所有正在进行的所有内容。 最令人意外的是，大多数测试人员发现查看小版本更沉浸式，然后他们从未切换回 1：1 比例。 因此，我们决定实际放弃 1：1 版本，并避免适应 UI 和应用的其他方面所需的额外工作。

![比例为 1：1 的视图字段，比例为 ](images/designing-holograms/1-1-scale.png)
 *1：1*

![比例为 1：10 的视图字段，比例为 ](images/designing-holograms/1-10-scale.png)
 *1：10*

## <a name="using-mixed-reality-capture"></a>使用 混合现实捕获

此应用的最特征之一是使用 混合现实捕获来教授和演示混合现实设计概念。

Microsoft 在混合现实捕获有一个工作室。 Microsoft 还将此技术许可给其他工作室，包括华盛顿特区的头像维度、洛杉矶的 Metastage、伦敦的 Dimension Studios、位于意大利的 SK Telecom 和位于意大利的 Volucap。 可在此处找到有关 混合现实捕获 [工作室的信息](https://www.microsoft.com/mixed-reality/capture-studios)。

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*来自旧金山 混合现实捕获 Studio 中 106 个相机之一的 Daniel Escudero 的原始视频。*

捕获过程会生成关键帧网格、法线和纹理，这些网格、法线和纹理可以作为 OBJ/PNG 文件传送，供进一步后期制作，或准备好播放为 H.264 压缩 MP4 文件。 这些文件可以导入 Unity、Unreal、Native 和 WebXR 项目中。 文件可以在 Windows、iOS、Mac、Android、Magic Leap 和 Playstation VR 中运行。

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*提供的捕获播放器，用于分析包含带音频和嵌入网格的视频的 mp4。*

## <a name="manipulating-captures-and-virtual-objects"></a>操作捕获和虚拟对象

混合现实捕获生成人员或动物的虚拟表示形式，但有时可能需要这些字符来与其他虚拟对象交互。 下面两个示例演示了我们处理场景以实现此效果的不同方式。

### <a name="head-gaze-adjustment"></a>打印头注视调整

Headgaze 调整使你可以在运行时移动已捕获人员的标题，这意味着你可以获得用户的捕获面。 在我们的示例中，我们使用它来显示所需的视图和字段的字段。 下面是一个移动 gameobject，它作为打印头注视的目标来查看。 当我们将目标从一侧移到另一侧时，捕获的开头将如下所示。

我们使用这一技巧来确保空闲捕获始终面对存放在娃房子不同部分的全息影像。 

![在 Unity 中的目标 gameobject 之后，在运行时移动捕获的头](images/designing-holograms/head-adjustment.gif)

*当 Unity 中的目标 gameobject 后，将在运行时移动捕获的头。*

### <a name="syncing-animated-objects"></a>同步动画对象

第二个是动画处理要与捕获移动同步的对象。 在应用程序的不同部分，每隔五帧导入一个特定捕获的顺序 Obj。 然后，Obj 在场景中进行动画处理，以确保它们与捕获的相应帧匹配。 这是一种令人厌烦的动画处理和 keyframing 的过程，但结果很好。 你现在可以看到混合现实捕获与非捕获对象的交互。

![在混合现实捕获和 UI 面板之间同步动画](images/designing-holograms/synced-objects.gif)

*在混合现实捕获和 UI 面板之间同步动画*

### <a name="ui-creative-process"></a>UI 创作过程

开始使用 UI 设计时，我们想要展示全息影像必须提供的一些神奇的做法。 在三维世界中，简单地显示静态2D 窗口和文本框并不合适。 许多可能性不会显示，因此，我们决定从一开始就放弃这种可能性，并充分利用全息 3D 空间。

最初，我们从向面板、图标和文本信息添加一些粗细开始。 不过，作为用户，我所看到的是一个文本框。 包含图像的文本框，但我们不存在。 我们进一步利用混合现实工具包和 MRTK (器) 器。 MRTK 着色器成为功能强大的工具，我们利用其模具功能向面板添加负深度。 这意味着，图标现在显示在透明面板后面，而不是在文本框前面添加元素。 现在，作为用户，我不再可以在现实世界中复制它，这是全息幻像开始发生的地方。 此外，作为一个不想阅读的用户，我已在物理世界做很多工作。

显然，图标比简单文本的效果要强很多，为了提供更强大的指导，我随后开始创建一组动画对象和头像，每个图标都讲述一个有关各自方案中正在完成的工作及其使用方式的小故事。

![交互式全息菜单系统的动画 GIF](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a>核心概念

**头部跟踪和眼动跟踪**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

**手部跟踪**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

**空间感知**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

**全息帧**

![用户通过动画 GIF 来四处查看，其中突出显示了全息帧](images/designing-holograms/FOVandFOI.gif)

**坐标系统**

![用户通过动画 GIF 来四处查看仓库，其中突出显示了坐标系统](images/designing-holograms/CoordinateSystems.gif)

**眼动跟踪**

![用户查看固定全息影像的动画 GIF，其中突出显示了眼睛凝视射线](images/designing-holograms/EyeTracking.gif)

**房间扫描可视化和空间映射**

![要映射的仓库内所有图面的动画 GIF](images/designing-holograms/SpatialMapping.gif)

**场景理解**

![正在识别的仓库中对象的动画 GIF](images/designing-holograms/SceneUnderstanding.gif)

**手动射线的点和提交**

![用户的动画 GIF，其中突出显示了手 ray](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a>"试用"

设计全息影像会讲授混合现实概念，但它也允许您在房间内试用它们。 在其中一些说明后，我们将会暂停，并将您娃房子并进入互动时间。 下面是这些交互式对话的一些示例：

![手写帧的动画 GIF，其中显示了是否检测到指针以及何时进入视图的字段](images/designing-holograms/try-out-1.gif)

*在检测到指针和进入视图字段时显示的手写跟踪帧。*

![与碰撞 crystals 交互的动画 GIF](images/designing-holograms/try-out-2.gif)

*与 crystals 的交互发生交互*

![浏览近乎交互实用的动画 GIF](images/designing-holograms/try-out-3.gif)

*探索近交互实用*

## <a name="about-the-team"></a>关于团队

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><b>Daniel Escudero</b><br><i>领先技术设计人员</i><br>Dan 是设计全息影像的创造性主管，当前作为旧金山的 Microsoft 混合现实院校的设计主管，以前是伦敦的 Microsoft 混合现实工作室之一中的设计器。</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>圣马丁 Wettig</b><br><i>高级三维艺术家</i><br>圣马丁使三维艺术和 UI 设计在设计全息影像上，以前是 Microsoft 的一个混合现实工作室的高级三维音乐家。</td>
</tr>
</table>

非常感谢你对混合现实设计团队共享如此多的知识，并为 [对象理论](https://objecttheory.com/) 的令人惊叹的用户提供有关项目中每个步骤的重要团队。 感谢你的出色人才，感谢你对设计的兴趣和出色的眼睛。

> [!div class="nextstepaction"]
> [下载设计全息影像应用](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)