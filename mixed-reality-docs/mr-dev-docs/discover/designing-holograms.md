---
title: 设计全息影像
description: 通过 Microsoft 的新设计全息影像应用程序了解混合现实。
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK，混合现实 Toolkit，全息影像，设计全息影像，学习，示例应用，混合现实耳机，虚拟现实耳机，什么是虚拟现实
ms.openlocfilehash: fb60dabcd03d276a7d901ee5b2f061460fbfa05acfbdf226a8aee9325f160cff
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192369"
---
# <a name="the-making-of-designing-holograms"></a>设计全息影像

> [!NOTE]
> 请在此页上为所有的冷 Gif 和嵌入视频提供小的加载窗口。

Learning 如何设计混合现实很难，因为介质并不总是很好地转换为2d 设计过程。 在 Microsoft，我们为 HoloLens 2 创建了免费应用程序，帮助你了解混合现实 UX 设计亲身的基础知识。 设计全息影像应用程序的独特方法深入混合现实行为、提示和建议，帮助你自行创建富有吸引力的、令人惊叹的 HoloLens 应用。 从 Microsoft Store 免费下载应用，并从 Microsoft 混合现实设计团队那里了解！

> [!div class="nextstepaction"]
> [下载设计全息影像应用](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![设计全息图的演示房间中标题跟踪场景的动画 GIF](images/designing-holograms/demo-room.gif)

*设计全息图的演示房间 (也称为娃房子)*

## <a name="designing-for-mixed-reality"></a>混合现实设计

与许多人一样，我使用的是设计移动应用。 从2D 设计世界来，跳转到空间计算的完整，其中一切现在都在世界中，这是一项重大转变。 在混合现实中，应用不再局限于2D 屏幕;事实上，它们几乎是免费的，放在现实世界中，并与真实对象进行交互。

对于我来说，将3D 体验连接到传统的2D 设计过程是混合现实开发的最具挑战性的方面。 在与客户的对话中，我知道 "我知道要包含哪些功能以及如何让它们启动并运行"。 就是代码，我可以按照文档和教程操作，而是在用户体验方面？ 如此多的功能、不同的输入选项、不同的方案和物理环境，这一点很惊人。

![从旧金山的 ](images/designing-holograms/workshop.jpeg)
 *HoloLens 2 设计研讨会* HoloLens 2 的 san 中设计研讨会中的映像

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
- 并且最糟糕的是，所有虚拟环境都受视图的字段约束。

当我们尝试使用微型1:10 刻度时，结果是一个极好的鸟瞰视图。 你可以从任何角度查看所有内容。 最令人吃惊的是，大多数测试人员发现它很多地都可以看到较小的版本，然后他们永远无法切换回1:1 规模。 我们决定实际会弃用1:1 版本，并避免在 UI 和应用程序的其他方面进行调整所需的额外工作。

![具有 ](images/designing-holograms/1-1-scale.png)
 *1:1 刻度的* 1:1 缩放字段视图的视图字段

![具有 ](images/designing-holograms/1-10-scale.png)
 *1:10 刻度的* 1:10 缩放字段视图的视图字段

## <a name="using-mixed-reality-capture"></a>使用混合现实捕获

此应用程序的最重要特性之一是使用混合现实捕获来讲授和演示混合现实设计概念。

Microsoft 的 San 中有混合现实的捕获工作室。 Microsoft 还向其他工作室提供此技术，其中包括华盛顿特区的头像、洛杉矶、伦敦的 Dimension 工作室、首尔的 SK 电信和柏林上的 Volucap。 可在此处找到有关 [混合现实捕获工作室](https://www.microsoft.com/mixed-reality/capture-studios)的详细信息。

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*在 San 中，混合现实中的一106照相机的 Daniel Escudero 的原始胶片。*

捕获过程将生成一个 keyframed 的网格、法线和纹理，可将其作为 "OBJ/PNG" 文件传送，以便进一步后期生产，或准备好将其作为 " 这些文件可以导入到 Unity、Unreal、本机和 WebXR 项目中。 文件可在 Windows、iOS、Mac、Android、幻 Leap 和 Playstation VR 上运行。

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*提供的捕获播放机用于分析包含音频和嵌入网格的视频的 mp4。*

## <a name="manipulating-captures-and-virtual-objects"></a>操作捕获和虚拟对象

混合现实捕获会生成人员或动物的虚拟表示形式，但有时您可能需要这些字符与其他虚拟对象进行交互。 下面两个示例演示了我们处理场景以实现此效果的不同方式。

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

开始使用 UI 设计时，我们想要展示全息影像必须提供的一些神奇的做法。 在三维世界中，简单地显示静态2D 窗口和文本框并不合适。 很多情况下不会显示，因此，从现在开始，我们决定从该位置移走，充分利用全息的3D 空间。

首先，我们开始向面板、图标和文本信息添加一些粗细。 而且，作为用户，我看到的是一个文本框。 包含图像的文本框，但不存在。 我们通过利用混合现实 Toolkit (MRTK) 着色器进行进一步的介绍。 MRTK 着色器变成了一个功能强大的工具，并使用其模具功能向面板添加了消极的深度。 这意味着，图标现在显示在透明面板的后面，而不是在文本框前面添加元素。 我现在看到的是，我只是在现实世界中不能再复制，而这是一种开始使用全息幻的地方。 我也不是我想要阅读的，我还在现实世界中做了很多工作。

显然，图标的工作方式比简单文本更好，若要提供更为强大的指导，然后开始创建一组动画对象和头像，其中每个对象都告诉您在各自的方案中所执行的操作及其使用方式的一小部分。

![交互式全息菜单系统的动画 GIF](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a>核心概念

**标题跟踪和目视跟踪**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

**手部跟踪**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

**空间感知**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

**全息帧**

![用户的动画 GIF，其中突出显示了全息框架的 dollhouse](images/designing-holograms/FOVandFOI.gif)

**坐标系统**

![用户使用突出显示的坐标系统围绕 dollhouse 的动画 GIF](images/designing-holograms/CoordinateSystems.gif)

**眼动跟踪**

![用户的动画 GIF，其中突出显示了眼睛为眼睛的静止全息影像](images/designing-holograms/EyeTracking.gif)

**房间扫描可视化和空间映射**

![要映射的仓库内所有图面的动画 GIF](images/designing-holograms/SpatialMapping.gif)

**场景理解**

![正在识别的仓库中对象的动画 GIF](images/designing-holograms/SceneUnderstanding.gif)

**使用手部射线指向和提交**

![用户提升手部并突出显示手部射线的动画 GIF](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a>"试用"时刻

设计全息影像介绍混合现实概念，但也允许你在房间中试用它们。 经过一些解释后，我们将暂停，将你从房屋中出来，进入一个交互时刻。 下面是这些交互时刻的一些示例：

![手部跟踪帧的动画 GIF，显示何时检测到手以及何时进入视场](images/designing-holograms/try-out-1.gif)

*手部跟踪框，显示检测手的时间和进入视场的时间。*

![动画 GIF：通过远部交互与碰撞的卫星交互](images/designing-holograms/try-out-2.gif)

*通过远部交互与碰撞的球体交互*

![探索近交互元素的动画 GIF](images/designing-holograms/try-out-3.gif)

*探索近交互的可体验性*

## <a name="about-the-team"></a>关于团队

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><b>Daniel Escudero</b><br><i>首席技术设计器</i><br>Dan 是设计 全息影像 的创意总监，当前在旧金山担任 Microsoft Mixed Reality Academy 的设计主管，以前是伦敦 Microsoft 混合现实工作室之一的设计人员。</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>Martin Wettig</b><br><i>高级 3D 艺术家</i><br>Martin 领导 3D Art and UI Design on Designing 全息影像，以前是 Microsoft Mixed Reality Studios inIng InIng（德国）的一家 Microsoft 混合现实工作室的高级 3D 艺术家。</td>
</tr>
</table>

感谢混合现实设计团队分享了太多知识，并感谢对象理论的出色的人员，感谢他们作为项目[](https://objecttheory.com/)每个步骤的基本团队成员。 感谢你的出色人才，感谢你对设计的兴趣和出色的眼睛。

> [!div class="nextstepaction"]
> [下载设计全息影像应用](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)