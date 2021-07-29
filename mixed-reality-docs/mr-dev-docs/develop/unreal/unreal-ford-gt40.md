---
title: Ford GT40 体验
description: 请参阅，了解如何将 Ford GT40 混合现实应用程序与 Unreal 中的 MRTK for HoloLens 2 结合在一起。
author: hferrone
ms.author: v-hferrone
ms.date: 3/23/2021
ms.topic: article
keywords: Unreal，Unreal Engine 4，UE4，HoloLens，HoloLens 2，混合现实，部署到设备，PC，文档，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
appliesto:
- HoloLens 2
ms.openlocfilehash: e634d75af92509372209d8e7c0cde2833127c128
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757190"
---
# <a name="the-making-of-the-ford-gt40-experience"></a>Ford GT40 体验
![Ford GT40 英雄图像](images/ford-gt40-hero_1920.jpg)

*"预 MRTK，使用 Unreal 进行 HoloLens 2 开发有点枯燥，因为所有空间交互都必须手动编码。Unreal 的 MRTK 对这些任务进行了很多简单的操作。我估计它会缩短初始原型所需的时间。 "* -Rodriguez，软件开发人员

*"Ford GT40 体验证明，高保真 HoloLens 2 应用只需几个月就能完成，但仍有一个适度的预算，但仍能提供高度的有影响力结果。"*  -Daniel Cheetham，首席创新官员，快乐

使用混合现实 Toolkit (用于 Unreal 的 MRTK) ，创造性的生产公司会获得更好的 HoloLens 2 体验，在 Ford GT40 上提供了一种全新的观点，即在 Le 传奇的24小时击败 Ferrari 的 Mans 赛车！

通过使用一系列自然和直观的空间交互，用户可以探索 GT40's 的美、性能和工程，这一切都以利用 Unreal 引擎提供的高视觉保真度的方式提供。 整个项目的软件开发已由一位开发人员在不到三个月的时间内完成，MRTK 适用于 Unreal 的 visual 脚本和设计环境。

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>从 HoloLens 2 中的 Microsoft Store 下载应用
如果有 HoloLens 2 设备，则可以直接在设备中下载并安装应用。

<a href='//www.microsoft.com/store/apps/9p4vllktfvfp?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="the-ask"></a>Ask

令人满意的是世界领先的创新生产公司之一，其中包含、Ford、Microsoft、佼佼者、Netflix、Vodafone 和其他家庭名称。 该公司将其作为一家高端照片润色机构开始，并将其分散到胶片和 CGI 中，然后使用三维空间设计和交互向沉浸式故事分享提供卓越的优势。

在2020年，Microsoft 已完成生成演示应用程序，该应用程序可帮助展示新的混合现实 Toolkit (MRTK) 对 Unreal 引擎中的 HoloLens 2 的支持。 此时，该公司已在其皮带下有两个成功的 HoloLens 2 Unreal 项目。 这两种方法都适用于全球公认的消费者品牌，这为内部 R&D/B2B 销售工具选择了 HoloLens 2 Unreal，以实现高视觉保真，以最大程度地展示客户自己的高端产品。

尽管解决方案本身会成为一项令人满意的解决方案，但它必须满足几个关键指导原则。 首先，必须专注于企业应用场景，以说明 Unreal 在游戏行业外 HoloLens 2 的实用程序。 其次，它必须只是设备，这意味着它可以作为独立的演示，无需网络连接和外部处理能力即可获得目标帧速率和视觉质量。 第三，它应将 MRTK 支持的直观交互的范围混合到无缝且自然的体验。 最后，提议的解决方案应展示 Unreal 引擎本身固有的视觉保真和其他优势，如着色器效率。 

考虑到这些准则后，他们会开始顺利地集体讨论各种可能性，同时提供一种混合现实体验的理念，使用空间互动传达品牌名称、高价值产品的价值。 考虑到包含监视、照相机、汽车和私有 jets 的一系列对象之后，满意度最终决定了 Ford GT40，这是一个汽车图例，该图例实现了 Ford 在 Le Ferrari 的24小时内出名1966，如 2019 Mans 胶卷流行与 Ford 中所示。 

从 Ford 获得购买后，现有的令人满意的完成客户端，公司设置为提供有关经典汽车的全新观点。

## <a name="the-solution"></a>解决方案

从 2020 5 月7日开始的工作。 获取 GT40 模型文件后，三维音乐家花了三周的时间来优化多边形模型、UV 地图、重绘纹理地图，并将这些地图压缩为尽可能少的纹理。 技术音乐家并行处理三维音乐家的输出，确定给定目标帧速率的最佳纹理尺寸，并确定在 Unreal 中应用自定义着色器的最佳方式。 所有此预生产工作都是为了优化设备上的体验。

创意主管 Alex 朗伯在预生产工作完成后进入了图片。 他通过观看 Ford 与 Ferrari 来开始，思考一下如何将围绕方案和交互的叙述融合在一起。 他还为 UI 艺术家收集了可视参考，如 GT40 仪表板的图像和 Le Mans racetrack 的视觉对象，以及为声音设计器提供的 GT40 的录制录音。

在现有的叙述和优化的预生产资产的情况下，将登记兼职软件开发人员 Rodriguez。 Rodriguez 在之前的两个 Unreal HoloLens 2 项目上，已经完成了的 MRTK，Unreal 的已发布。

MRTK for Unreal 提供的值在初期就变得很明显，有助于 Rodriguez 在一周内传递初始原型。 他实现了三个独特的方案，每个方案分别针对朗伯标识的 GT40 的每个主要方面：其美、性能和工程。 对于每个方案，Rodriguez 使用 MRTK 将优化3D 资产从预生产阶段集成到一系列空间交互。 

使用 MRTK for Unreal，Rodriguez 使用 visual Unreal 运动图形构建每个方案 (UMG) UI 设计器，而无需实现 c + + 中的所有操作。 [适用于 Unreal 的 Ux 工具](https://www.unrealengine.com/marketplace/product/mixed-reality-ux-tools)（包含 MRTK 内的 UX 构建基块和组件的插件）为用户提供了输入模拟、可视化脚本编写的表面交互、pressable 按钮、三维图像操作、表面磁性等的 [Unreal 蓝图](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/index.html) ，这一切都在无代码、拖放设计环境中。

"预 MRTK，使用 Unreal 进行 HoloLens 2 开发有点枯燥，因为所有空间交互都必须手动编码，即" c + + "中的" Rodriguez "。 "MRTK for Unreal 对这些任务进行了很多简单的操作。 我估计它会缩短初始原型所需的时间。 "

使用现有原型，团队开始每周迭代，以优化体验。 "这就是当混合现实捕获功能和 Windows 设备门户非常有用时，" 朗伯 "。 "我用它们来捕获设计评审，将我的反馈广播给其他人，并协作处理更改。 采用与此类工具相同的隔离方式。 "

![Unreal editor Ford GT40 应用程序运行时按顺序排列的色轮组件](images/ford-gt40-img-04.JPG)

由于朗伯请求更改，如重定位 UI 元素或更改按钮的行为，Rodriguez 实现它们。 虽然某些更改需要进行较小的代码调整，但大多数更改都是在 Unreal 可视化设计器中处理的。 "我很惊讶于我可以循环访问的速度，" 说 Rodriguez。 "未浪费时间;我将在设计器中进行更改，然后按 "播放" 立即在设备上查看。 MRTK 真正简化了工作。 "

Rodriguez 还通过生产就绪的所有开发工具的工作方式来召回深刻印象。 "我们通过最终生产顺利实现了初始原型，无需返回并在代码中重新实现或优化内容。" 他说。  

## <a name="the-final-build"></a>最终生成

祝您在2020年7月28日完成 HoloLens 2 的 Ford GT40 体验，在传奇赛车上提供全新的观点。 经验从 "欢迎" 屏幕开始，然后指导用户通过获取 Ford 徽标来设置定位点，并将其放置在平面表面上，如表或桌面。 

### <a name="beauty"></a>优点

该 **便利段将** 用户转到 GT40 配置器，该配置器将 GT40 显示在旋转的支座上，类似于在汽车显示屏上显示的实际汽车。 用户可以应用不同的色轮选项，从不同的配色方案中进行选择，并打开和关闭门和干线 (或启动，因为它们在英国) 中调用。 在丰富的体验中，用户可以选择汽车，并自由地对其进行操作，以便更仔细地查看。

![设备上运行的 GT40 配置器的动画 GIF](images/ford-gt40-img-05.gif)

### <a name="performance"></a>性能

**性能** 段展示了 GT40's 速度和持续性。 Voiceover 首先介绍汽车的开发方式，并通过三维视觉对象在节奏上的 Ford，在测试轨上显示 GT40。当性能段结束时，voiceover 将提示用户 "按下" Mans "按钮来点击 racetrack。

![设备上运行的 GT40 速度和持续性应用的动画 GIF](images/ford-gt40-img-06.gif)

性能段的第二部分将在 Le Mans 的24小时内出现的条件驱动程序的范围内出现 GT40，它每年都在的 Sarthe 附近的。 三维视图显示 Le Mans 轨上的运动车，其中包含用于使汽车更快或更慢的按钮。 Racetrack 视图上方 GT40's 模拟速度计和流速浮动的图像，在后台显示更多争用遥测。 用户可以在 "日" 和 "晚间" 视图之间进行切换，并在 "干燥" 和 "湿" 等状态之间切换，从而为在实际比赛中体验到的 Ken 英里和其他 GT40 驱动程序提供逼真而逼真的观点。

### <a name="engineering"></a>工程

Ford GT40 体验的 **工程** 细分展示了帮助 Ford 赢得竞赛的工程创新之一：与所有其他团队所需的20-30 分钟相比，能够在不到一分钟的时间内更改刹车 rotors 和 pad。 使用直观的手势，用户可以操作 GT40 轮和刹车程序集的详细3D 模型。 若要展开该程序集，用户需要选取一个 lug 扳手，使其与滑轮上的中心锁对齐，逆时针旋转，然后将其拉离滚轮。 其他笔势用于删除磨损的刹车 rotors 和 pad，将它们替换为新的，折叠程序集，并 resecure 中心锁。 在后台，计时器显示已用时间，让用户看到他们能否尽快完成该时间，使其能够在 Le Mans 上完成此过程。

![在设备上运行的 GT40 工程体验的动画 GIF](images/ford-gt40-img-07.gif)

Ford GT40 体验可[从 Microsoft 应用商店下载](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp?activetab=pivot:overviewtab)，使具有 HoloLens 2 的任何人都可以探索如何完成为传奇赛车提供全新的观点。

### <a name="getting-impressive-visual-fidelity"></a>获得深刻的视觉保真

虽然 Ford GT40 体验支持的空间交互范围非常令人印象深刻，但体验的创造性和视觉保真确实使其成为了其亮点。 通过其3D 模型优化和 Unreal 自定义着色器的使用，每秒的最大值为60帧的目标，即使应用的性能段接近315000个多边形。 

"我非常喜欢我们如何才能将一组流畅、直观的交互操作集中到一个连贯的和有吸引力的叙述中"。 "很明显，HoloLens 2 上的 Unreal 引擎的强大功能可为您提供更惊人、令人兴奋的混合现实体验的新机会。 对 HoloLens 2 上的企业应用程序而言，真正的视觉保真并非始终是最终目标，但在这种情况下，对 HoloLens 2 的支持 Unreal 变得非常宝贵。 "

### <a name="rapid-solution-delivery"></a>快速解决方案交付

与最终用户的 Ford GT40 体验相比，最终用户的经验是如何迅速完成交付的，整个项目（从预生产到最终交付），只需在12周内完成即可完成。 总而言之，该项目消耗了1088小时的工作量，按以下方式分解：创造性总监 (80 小时) ，UX 设计器 (56 小时) ，UI 设计器 (40 小时数) ，的语音设计器 (40 小时) ，3D/技术艺术家 (328 小时) ，软件开发人员 (408 小时数) 

"总之，我们已与最初的项目估算非常接近，" 说 Daniel Cheetham，首席创新官员的工作是公司的交互式部门。 "Ford GT40 体验证明，高保真 HoloLens 2 应用只需几个月就能完成，但仍有一个适度的预算，但仍能提供高度的有影响力结果。" 

从开发的角度来看，基于其在 HoloLens 2 上的 Unreal，Rodriguez 估计 MRTK for Unreal 会缩短其部分所需的总时间和工作量。 他还说明了 MRTK 如何帮助从未开始使用 HoloLens 2 入门的开发人员。 "当其他开发人员说他们对混合现实感兴趣时，我鼓励他们只需进入，安装 HoloLens 2 开发堆栈和 MRTK，然后继续。 MRTK 使构建应用程序的速度变得简单简单，Unreal 的可视化编辑器的工作方式非常好，甚至不需要 HoloLens 2 设备即可开始使用。 这并不复杂，一切都是有效的。 "

### <a name="potential-azure-service-enhancements"></a>潜在的 Azure 服务增强功能

朗伯可以通过多种方式来使用 Azure mixed reality 服务来增强 Ford GT40 体验，例如使用 Azure 空间锚，提供定位在现实世界中的多用户体验。 "从创造性的角度来看，Azure 空间定位点通过其提供的功能来提供一系列全新的可能性，使其能够在我们的物理世界中映射、保留和还原3D 内容或关注点，" 他说。

朗伯还 envisions 在使用更详细的复杂3D 模型时，azure 远程呈现或流式处理应用程序的方式可用于实现所需的帧速率。 "我们必须在 Unreal 中实现一些高度优化的自定义着色器，使其达到每秒60帧的设备目标，" 他解释了。 "借助 Azure 远程渲染，我们可以执行更多操作，更轻松地执行此操作，而无需花费大量工作量来优化多边形模型、重绘纹理图等。"

### <a name="endless-new-possibilities"></a>全新的可能性

那么，接下来要做什么呢？ Ford 对 Ford GT40 体验的反馈一直在充分，旨在进一步讨论未来 HoloLens 2 项目的完成和 Ford。 在与 Ford 的关系外部，满意的完成已经开始 HoloLens 2 上的新项目，其中 MRTK for Unreal 将是最适用于大多数用户体验的基础构建基块。 

"我们一直在为每个新项目维护一种技术无关的方法，建议哪种工具集最适合帮助客户端实现所需的结果。" Cheetham。 "这就是，HoloLens 2 已成为混合现实的现实标准（尤其是在企业中），在这两个设备功能和支持生态系统普适性相的情况下，在所有其他选项上需要肩负。"

根据 Cheetham，全球流行病在潜在客户之间产生了沉浸式混合现实的巨大新兴趣。 "我们比以往任何时候都更忙，因为有大约50% 的潜在客户正在讨论一种混合现实选项，" 他说。 "关键是让人们来尝试一下。 你随时都可以告诉他们有关混合现实的信息，但当你向他们提供对自己的体验 HoloLens 2 时，它们会立即获得游戏转换器。 对 HoloLens 2 中的 Unreal 引擎的支持仅增加了我们可以提供的价值，使我们能够提供视觉上令人惊叹的体验，以确保甚至最苛刻的客户端。 "

## <a name="try-it-out"></a>试试看！

> [!div class="nextstepaction"]
> [下载 Ford GT40 应用程序](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

请查看我们对 GitHub 上的 HoloLens 2 或[MRTK for Unreal 的](https://github.com/microsoft/MixedRealityToolkit-Unreal)[混合现实开发简介](../development.md)。

<!-- ## About the team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>Lead Game Designer</i><br>Jack currently works on Mixed Reality experiences for Microsoft, including HoloLens 2 projects and AltspaceVR, and was previously a designer on the HoloLens platform team.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Summer Wu</b><br><i>Producer</i><br>Summer works on the mixed reality developer platform and heads the team’s Unreal Engine related efforts.</td>
</tr>
</table> -->