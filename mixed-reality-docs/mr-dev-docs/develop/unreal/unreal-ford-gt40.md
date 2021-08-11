---
title: Ford GT40 体验
description: 请继续探索在 Unreal 中通过 MRTK 创建 Ford GT40 混合现实HoloLens 2应用。
author: hferrone
ms.author: v-hferrone
ms.date: 3/23/2021
ms.topic: article
keywords: Unreal， Unreal Engine 4， UE4， HoloLens， HoloLens 2， 混合现实， 部署到设备， 电脑， 文档， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
appliesto:
- HoloLens 2
ms.openlocfilehash: 17314cca69148e73ee11fcd4cdc5359a5dbae4cf84b609bafb6cc75d477ec26f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200602"
---
# <a name="the-making-of-the-ford-gt40-experience"></a>Ford GT40 体验的制作
![Ford GT40 特大图像](images/ford-gt40-hero_1920.jpg)

*"PRE-MRTK，使用 Unreal HoloLens 2开发时有点繁琐，因为所有空间交互必须用 C++ 手动编码。适用于 Unreal 的 MRTK 使许多相同的任务变得简单。我估计它会将初始原型所需的时间缩减一半。"* - Developer Software Developer-Rodriguez

*"Ford GT40 体验证明，高保真 HoloLens 2 应用可以在几个月内完成，预算适中，但仍提供影响很大的结果。"*  - Daniel Cheetham，Happy Finish 首席创新官

使用混合现实 Toolkit (MRTK) for Unreal，创意生产公司 Happy Finish 提供了一个 HoloLens 2 体验，提供对 Ford GT40（在 24 小时的 Le Mans 中一次在 Le Mans 中比分一比 24 的英雄车）的新观点！

使用一系列自然直观的空间交互，用户可以探索 GT40 的美观、性能和工程，所有这些都以利用 Unreal Engine 提供的高视觉保真度的方式提供。 整个项目的软件开发由单个开发人员在三个月内完成，由 MRTK 针对 Unreal 的可视化脚本和设计环境实现。

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>从 Microsoft Store HoloLens 2
如果有HoloLens 2，可以直接在设备中下载并安装应用。

<a href='//www.microsoft.com/store/apps/9p4vllktfvfp?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="the-ask"></a>询问

Happy Finish 是领先的创意生产公司之一，其客户群包括 Ford、Microsoft、Microsoft、Microsoft、Netflix、Vodafone 和其他家庭名称。 该公司以高端照片修饰机构开始，在通过 3D 空间设计和交互将自身对沉浸式故事讲述的卓越表现扩展到电影和 CGI 之前，将其分支到电影和 CGI。

2020 年年中，Microsoft 与 Happy Finish 合作，生成了一个演示应用，该应用可帮助展示新的混合现实 Toolkit (MRTK) for Unreal 启用的可能性，该应用基于 Unreal 引擎中 HoloLens 2 的支持。 此时，该公司已有两个成功的 Unreal on-HoloLens 2项目。 这两种产品都适用于一个全球认可的消费者品牌，该品牌选择 HoloLens 2 上的 Unreal 作为内部 R&D/B2B 销售工具，以提升视觉保真度，以最佳展示该客户的高端产品。

虽然解决方案本身将留在 Happy Finish，但它必须满足几个关键准则。 首先，它必须专注于企业方案，以说明 Unreal 在游戏行业HoloLens 2的实用工具。 其次，它只能用于设备，这意味着它可以充当独立演示，无需网络连接和外部处理能力即可获取目标帧速率和视觉质量。 第三，它应将 MRTK 支持的直观交互范围混合到无缝的自然体验中。 最后，建议的解决方案应展示 Unreal 引擎本身固有的视觉保真度和其他优势，例如着色器效率。 

鉴于这些指导原则，Happy Finish 开始探索可能性，提出混合现实体验的想法，该体验使用空间交互传达品牌、高价值产品的价值。 在考虑包括监视、相机、汽车和专用飞机的一系列对象后，Happy Finish 最终决定使用 Ford GT40，这是一个汽车图例，在 1966 年，当 Ford 在 24 小时《Le Mans》中以 24 小时之差在《Le Mans》中击球时，这一汽车图例在 2019 年《Ford 与即开》中展示了这一点。 

从现有 Happy Finish 客户端 Ford 获得支持后，该公司开始对经典汽车图标提供全新的视角。

## <a name="the-solution"></a>解决方案

工作于 2020 年 5 月 7 日开始。 获取 GT40 模型文件后，一位 3D 艺术家花费了三周时间优化多边形模型、UV 映射、重新绘制纹理贴图，并尽可能将这些贴图压缩成尽可能少的纹理。 技术艺术家并行工作，对 3D 艺术家的输出进行基准测试，确定给定目标帧速率的最佳纹理大小，并找出在 Unreal 中应用自定义着色器的最佳方法。 所有这些预生产工作都是为了优化设备内体验。

创意总监 Alex Lambert 在预生产工作完成后输入了图片。 他一开始观看了 Ford 与为时，思考了如何围绕场景和交互将叙述一起组织在一起。 此外，他收集了 UI 艺术家的视觉参考，例如 GT40 仪表板的图像和 Le Mans 比赛场的视觉对象，并收集了适用于声音设计器的 GT40 的录音。

借助定义和优化的叙述性预生产资产，已登记了软件开发人员 Rodriguez，以将所有这些资产汇集在一起。 Rodriguez 在发布 Unreal 的 MRTK 之前HoloLens 2两个 Unreal on-on-HoloLens 2项目的开发人员。

MRTK for Unreal 提供的价值在早期变得明显，帮助 Rodriguez 在一周内提供初始原型。 他实现了三种独特的方案，分别针对 Lambert 识别的 GT40 的每个关键方面：其美观、性能和工程。 对于每个方案，Rodriguez 都使用 MRTK 将预生产阶段的优化 3D 资产集成到一系列空间交互中。 

借助适用于 Unreal 的 MRTK，Rodriguez 使用可视化 Unreal Motion Graphics (UMG) UI 设计器构建每个方案，而无需在 C++ 中实现所有内容。 [UX Tools for](https://www.unrealengine.com/marketplace/product/mixed-reality-ux-tools)Unreal（MRTK 中包含 UX 构建基块和组件的插件）为 [Unreal Blueprint](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/index.html) 提供了用于输入模拟、直观编写手部交互脚本、可按下按钮、3D 图像操作、表面磁力等的 Unreal 蓝图，所有这些都在无代码、拖放设计环境中提供。

Rodriguez 说："Pre-MRTK，HoloLens 2 Unreal 进行开发有点繁琐，因为所有空间交互必须用 C++ 手动编码。" "适用于 Unreal 的 MRTK 使许多相同的任务变得简单。 我估计它会将初始原型所需的时间缩减一半。"

有了原型后，团队开始每周迭代来优化体验。 "这是当混合现实捕获和Windows 设备门户非常有用时，"Lambert 说。 "我使用它们捕获了设计评审，将我的反馈广播给其他人，并协作处理更改。 如果没有此类工具，就无法实现这种隔离工作。"

![Unreal 编辑器 Ford GT40 应用运行，轮组件按顺序布局](images/ford-gt40-img-04.JPG)

当 Lambert 请求更改（例如重新定位 UI 元素或更改按钮的行为）时，Rodriguez 实现了它们。 虽然某些更改需要小代码调整，但大多数更改是在 Unreal 可视化设计器中处理的。 Rodriguez 说："我对于能够以多快的速度进行 iterate，感到意外。" "没有浪费时间;我将在设计器中做出更改，然后按 play 立即在设备上查看它。 MRTK 确实简化了我的工作。"

Rodriguez 还回顾一下，所有开发工具的生产就绪情况让 Rodriguez 感叹。 "从初始原型到最终生产，我们进展顺利，无需返回并重新实现或优化代码中的一些内容，"他表示。  

## <a name="the-final-build"></a>最终生成

Happy Finish 于 2020 年 7 月 28 HoloLens 2完成 Ford GT40 Experience for HoloLens 2，为汽车竞赛提供了全新的视角。 体验从欢迎屏幕开始，然后指导用户通过抓取 Ford 徽标，将其放置在平面上（如表或桌面）来设置定位点。 

### <a name="beauty"></a>美

美观 **部分** 将用户带到 GT40 配置器，该配置器在旋转的旋转台上显示 GT40，类似于在汽车展上显示物理汽车的方式。 用户可以应用不同的滚轮选项，从不同的配色方案中选择，然后打开和关闭门和 (或启动，因为他们在英国) 。 在整个美观体验中，用户可以拾取汽车并自由操作它，以进一步查看。

![设备上运行的 GT40 配置器的动画 GIF](images/ford-gt40-img-05.gif)

### <a name="performance"></a>性能

**性能** 段展示了 GT40 的速度和持续性。 配音器首先介绍了如何开发汽车，以及如何在亚利桑那州的 Ford's Kingman 中完成其节奏，其中 3D 视觉对象在测试轨道上显示 GT40 动态。性能段简介结束时，配音图标会提示用户"按 Le Mans 按钮点击竞赛路径"。

![设备上运行的 GT40 速度和持续性应用的动画 GIF](images/ford-gt40-img-06.gif)

性能段的第二部分展示了 GT40 在驱动程序可能经历的 24 小时 Le Mans 条件下的情况，该活动每年在位于法国 Le Mans 附近的 Sarthe 线路上进行。 3D 视图显示 Le Mans 轨道上的汽车动态，并提供了使汽车速度更快或更慢的按钮。 GT40 的模拟速度计和步速计图像浮动在"竞赛场"视图上方，背景中显示更多的竞赛遥测数据。 用户可以在日视图和晚上视图之间以及干和雨驾驶条件之间进行切换，从而提供 Ken Miles 和其他 GT40 驱动程序在实际竞赛中经历的真实而真实的视角。

### <a name="engineering"></a>工程

Ford GT40 Experience 的工程部分展示了一项工程创新，这些创新有助于 Ford 赢得比赛：能够在一分钟内更改手部和板，而所有其他团队需要 20-30 分钟。  使用直观的手势，用户可以操作 GT40 滚轮和滚轮程序集的详细 3D 模型。 若要展开程序集，用户选取一个 lug 形针，将其与滚轮上的中心锁对齐，逆时针旋转它，然后将它从滚轮中拉取。 其他手势用于移除下手的和板、将其替换为新手部、折叠程序集，然后重新锁定中心锁。 在后台，计时器显示运行时间，让用户查看他们能否像 Le Mans 的井站工作人员一样快速完成该过程。

![设备上运行的 GT40 工程体验的动画 GIF](images/ford-gt40-img-07.gif)

可以从[Microsoft](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp?activetab=pivot:overviewtab)应用商店下载 Ford GT40 体验，使拥有 HoloLens 2 的任何人都可以探索 Happy Finish 如何为竞赛汽车带来全新的视角。

### <a name="getting-impressive-visual-fidelity"></a>获得令人惊叹的视觉保真度

虽然 Ford GT40 体验支持的空间交互范围本身非常出色，但体验所传递的创意和视觉保真度确实让体验更加出色。 通过优化 3D 模型和使用 Unreal 自定义着色器，Happy Finish 达到每秒 60 帧的目标，即使应用的性能段接近 315，000 个多边形。 

Lambert 说："我们非常满意我们如何将一组流畅、直观的交互汇集到一个一致且具有吸引力的叙述中。" "显然，Unreal Engine 在 HoloLens 2开启了一个新的机会世界，让混合现实体验更加令人意外和有趣。 不提升视觉保真度并不总是企业应用程序在 HoloLens 2 的最终目标，但在这种情况下，对 HoloLens 2 上的 Unreal 的支持将变得无用。"

### <a name="rapid-solution-delivery"></a>快速解决方案交付

与最终用户 Ford GT40 Experience 一样令人感叹的是，Happy Finish 交付了它，整个项目（从预生产到最终交付）在 12 周内完成。 总之，项目消耗了 1088 小时的工作，细分如下：创意总监 (80 小时) ，UX 设计器 (56 小时) ，UI 设计器 (40 小时) ， 声音设计器 (40 小时) 、3D/技术艺术家 (328 小时) 、软件开发人员 (408 小时) 、技术总监 (40 小时) 、制作者 (56 小时) 和质量保证 (40 小时) 。

负责公司的交互式部门主管 Happy Finish 的首席创新官 Daniel Cheetham 表示："总之，我们非常接近原始项目估算值。" "Ford GT40 体验证明，高保真 HoloLens 2 应用可以在几个月内完成，预算适中，但仍提供影响很大的结果。" 

从开发的角度来看，基于他之前在 HoloLens 2 上的 Unreal 经验，Rodriguez 估计，Unreal 的 MRTK 将他所需的时间和精力减少了一半。 此外，他注意到 MRTK 如何帮助从未使用过 HoloLens 2开发人员。 "当其他开发人员表示他们对混合现实感兴趣时，我鼓励他们直接进入，安装 HoloLens 2开发堆栈和 MRTK，然后进行开发。 MRTK 使生成应用变得简单快捷，并且 Unreal 视觉对象编辑器运行良好，你甚至不需要HoloLens 2设备。 一切正常，一切正常。"

### <a name="potential-azure-service-enhancements"></a>潜在的 Azure 服务增强功能

Lambert 发现 Azure 混合现实服务可用于增强 Ford GT40 体验的多种方式，例如使用 Azure 空间定位点提供在现实世界中锚定的多用户体验。 "从创造性的角度来看，Azure 空间定位点通过其提供的功能来提供一系列全新的可能性，使其能够在我们的物理世界中映射、保留和还原3D 内容或关注点，" 他说。

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