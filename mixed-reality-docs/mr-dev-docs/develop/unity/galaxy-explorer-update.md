---
title: HoloLens 2 的 Galaxy 资源管理器的创建
description: 了解我们的团队如何更新 GitHub HoloLens 2 上的 Galaxy 资源管理器开源项目。
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: galaxy 资源管理器，案例研究，项目，示例，MRTK，混合现实 Toolkit，Unity，示例应用，示例应用，开源，Microsoft Store，HoloLens，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: 1e19f63f493eba2559cf60ef7c1224b7323ec825
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757066"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>HoloLens 2 的 Galaxy 资源管理器的创建

![新建 Galaxy 资源管理器徽标](../images/GalaxyExplorer2.jpg)


欢迎使用 HoloLens 2 应用程序的更新的 Galaxy 资源管理器！ [Galaxy 资源管理器](/windows/mixed-reality/galaxy-explorer "星系探索者")最初是作为开源应用程序开发的，它通过共享你的想法计划来 HoloLens (第一代) ，这是许多人的第一种混合现实体验之一。 现在我们正在更新它，以了解[HoloLens 2 的全新功能](https://www.microsoft.com/hololens/hardware)。

作为 [Microsoft 混合现实工作室](galaxy-explorer-update.md#mixed-reality-studios)之一，我们通常会开发商业级解决方案，并在整个创意和开发过程中在目标平台上开发 & 测试。 我们将使用 (的框架和工具（例如) [MRTK](mrtk-getting-started.md) ）来着手此项目，并将其提供给我们和社区，我们想要将你带入。

正如原始 Galaxy 资源管理器一样，[我们的团队](galaxy-explorer-update.md#meet-the-team)将在[GitHub 上寻找项目](https://github.com/Microsoft/GalaxyExplorer)，以确保社区具有完全访问权限。 我们还将在这里记录我们的旅程，以全面了解我们如何从 MRTK v1 迁移到 MRTK v2，通过 HoloLens 2 中提供的新功能增强了体验，并确保了 Galaxy 资源管理器保持了多平台体验。 无论你是在 HoloLens (第一代) 、HoloLens 2、Windows Mixed Reality 耳机还是 Windows 10 桌面上查看 Galaxy 资源管理器，我们都希望确保你喜欢的旅程非常好！

此页将随着我们在项目中的进展而扩展，并提供指向更详细的文章、代码、设计项目和其他 MRTK 文档的链接，为你提供内幕的项目。

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>从 HoloLens 2 中的 Microsoft Store 下载应用
如果有 HoloLens 2 设备，则可以直接在设备中下载并安装应用。

<a href='//www.microsoft.com/store/apps/9nblggh4q4jg?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="thinking-about-interactions"></a>考虑交互

作为一录音室，我们兴奋了将 Galaxy 资源管理器移植到 HoloLens 2 的权限。 我们知道，我们希望体验成为新设备的庆祝，并说明混合现实能力仅受想像的限制。

HoloLens 2 使用户能够以自然的方式触摸、抓住和移动全息影像–它们的响应方式非常类似于真实的对象。 完全表述的手模型非常惊人，因为这样可以让用户看起来自然。 例如，每个人都可以略有不同的方式，而不是实施一种特殊的方式来执行此操作，HoloLens 2 使你能够以你的方式执行此操作。

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

这是第一代 HoloLens 设备上基于 Air 的接口的重大更改。 用户现在可以 "关闭" 和 "个人"，而不是从距离交互。 在将现有的体验迁移到 HoloLens 2 或规划新的体验时，请务必熟悉全息影像的直接操作。

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a>直接操作与空间中的远距离

这是一种神奇的体验，可以抓住并抓住行星。 这种方法的挑战在于太阳系的大小–非常巨大！ 用户需要浏览其空间，使每个行星都能与其交互。

为了使用户能够与远离远处的对象进行交互，MRTK 提供了从用户掌上走出的手的光线，作为手型的延伸。 环形光标连接到射线的末尾，以指示该射线与目标对象相交的位置。 然后光标所指向的对象可以接收来自手的手势命令。 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

在 "Galaxy 资源管理器" 的原始版本中，用户将以 "注视" 光标为地球，然后单击 "空中" 将其调近。 将体验移植到 HoloLens 2 的最简单方法是采用此行为，并使用手型来选择行星。 虽然这是正常运行的，但仍希望获得更多的功能。

### <a name="back-to-the-drawing-board"></a>返回绘图板

我们一起介绍了可在现有交互基础上构建的 ideate。 思维方式：尽管 HoloLens 2 允许用户以自然的方式与全息影像交互，但全息影像按定义并不真实。 因此，只要用户的交互是变得合理的，就不会有可能与真正的对象进行交互，而是不是很重要。

我们研究的一个概念就是基于 telekinesis –处理对象的能力。 通常，在超大英雄电影中，一个人会与他们的想法联系起来，并将一个对象调入他们的手中。 我们将使用一种更多的方法进行介绍，并提供该概念如何工作的快速草图。

![强制抓取交互的概念](images/ge-update-interactions-concept-force-grab.png)

用户会将手型点指向地球，这将提供目标反馈。 随着用户的张开，世界将通过神奇强制向用户拉取，直到其接近，才能获取它。 因此，我们要实现交互：强制获取的名称。 由于用户会将地球向外推，它会再次返回到其轨道。

### <a name="force-grab-prototyping"></a>强制获取抽取原型

接下来，我们创建了多个原型来测试概念：交互的整体效果如何？ 被调用的对象是否会在用户前面停止或一直到其上，直到放置？ 调用对象是否应在调用时更改大小或缩放？

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a>在应用程序中实现强制抓取

当我们在行星上尝试抓住强制时，我们意识到我们不得不改变阳历系统的刻度。 事实证明，阳历系统的准确、中等大小的表示形式对于用户来说很难理解和导航，他们不知道要查找的位置。 但是，小型表示形式使得某些行星太小，无法轻松选择。 因此，行星的大小和阳历之间的间距设计为在中等大小的房间内自如，同时保持相对准确性。

在开发冲刺（sprint）的更高阶段，我们已有足够的高手，足以让 MSFT 混合现实专家参与，因此我们努力将其输入作为专家测试人员并在强制抓取交互中快速迭代。

![来自 Kam 测试 Galaxy 资源管理器的预览版本](images/ge-update-user-testing.png)

图片：来自 Kam，高级设计主管，测试 Galaxy 资源管理器的工作。

### <a name="adding-affordances-for-targeting"></a>为目标添加实用

在 HoloLens 2 上，我们发现，即使新的交互是自然且直观的，全息影像仍保持不变：无权重或 tactile sensations。 由于全息影像并不提供用户在与对象交互时接收的自然反馈，因此我们需要创建它们。

我们考虑到了视觉对象和音频反馈，用户将为其交互的各个阶段提供这些反馈，因为强制获取机制是与 Galaxy 资源管理器进行交互的核心，所以我们做了很多迭代。 目标是为交互的每个阶段查找音频和视觉反馈的适当平衡：集中于预期对象，将其调用给用户，然后将其发布。 我们学到的是，更多的音频和视觉反馈比我们用于 (第一代) HoloLens。

![行星上的视觉对象实用](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a>添加实用以进行强制获取
 
随着音频和视觉对象实用的基本强制获取机制，我们了解了如何使选择的行星更易于用户理解。 要解决的主要问题是：由于太阳系是一个三维移动界面，因此用户可以更灵活地了解如何以一致的方式为对象提供目标。 这是一种复杂的情况，那就是，在选择对象时，手型的速度很快，使行星迅速进入用户。

我们使用三个方面的解决方案来做到这一点。 第一种方法非常直观：降低选择过程的速度，使行星更自然地处理用户。 调整速度后，我们必须重新访问音频和视觉对象实用，添加音频反馈作为向用户跟踪的行星。

解决方案的第二部分是使整个强制抓取交互成为有形的视觉对象。 我们直观地显示了一条粗线条，它在与目标对象连接后，将其移至目标对象，然后将该对象移回用户喜欢的套索。 

![用于强制抓取的视觉 "套索" 实用](images/ge-update-lasso-affordances.png)

最后，我们优化了太阳系的规模，以便用户看好行星，并将其作为目标。 

这三项改进允许用户进行精确选择，并以直观的方式为他们打电话。 总体而言，最终强制获取的效果是在太阳系中获得更具沉浸和交互性的体验。

## <a name="spotlight-on-jupiter"></a>在木星上聚焦

以银河的方式创建日光体是一种 humbling 体验。 具体而言，木星的独特特性使其对瞧可见。 它是气体巨量的最大和最大的质量，比所有其他行星组合的质量大。 Turbulence 和 cloud dynamics 的非常大的大小和 mesmerizing 带区 prefect，以实现特别的艺术。

### <a name="geometry-and-meshes"></a>几何图形和网格

作为一气体，木星的外部 shell 包含 gaseous 层。 它的快速旋转速度、内部热交换和 Coriolis 强制的结合会创建色彩丰富的层和流，并将其形成 swirling cloud 皮带和 vortices。 捕获这个非常复杂的美式是创建太阳系的关键所在。

很显然，使用流畅的技术（如流体模拟）和带预计算流的动画纹理就没有问题。 将此方法与其他任何情况同时进行模拟所需的计算能力会对性能产生重大的不利影响。 

![木星对象概述](images/ge-update-jupiter-shells-complete.jpg)

接下来的一种方法是 "冒烟和镜像" 解决方案，其中包括覆盖透明的纹理层，每个层都有一个用于处理旋转网格的组合的特定方面。

在下图中，可以在左侧看到内部外壳。 此材料层为组合提供了背景，以防止在构成云的多层之间出现任何小的间隙。 由于层的缓慢旋转，它还在更快速的移动带之间提供可视缓冲区，以帮助在各个层上构建视觉对象。

将此定位点设置到模型后，移动云层随后会投影到下面所示的中间和右侧网格上。

![带分隔 shell 的木星对象概述](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a>绘制

现有纹理被分为三部分纹理阿特拉斯：上部的第三个主机是 motionless 层，其中包含间距以提供视差效果，中间部分包含快速移动的外部流，第三部分包含慢速旋转内部基底层。

特征很棒的红点还分成了不同的移动部件，并将其插入到其他不可见的纹理区域中。 可以在下图的中间部分中将这些组件看作 toned speckles。

由于每个带区都有特定的方向和速度，因此纹理分别应用于每个网格。 然后，这些网格具有一个公共中心点和一个透视点，这使得 concentrically 可以对整个表面进行动画处理。

![木星纹理概述](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a>旋转和纹理行为

设置好木星的视觉组合后，需要确保正确计算和应用旋转和轨道速度。 木星大约需要9小时才能完成完整的旋转。 由于其差异旋转，这是一个定义。 因此，赤道几内亚流已设置为 "主流"，采用3600帧进行完全旋转。 每个其他层都需要将旋转速度提高为3600，以匹配其初始位置，例如，600、900、1200、1800等。

![木星 shell 纹理](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a>很棒的红点

单独旋转的流提供了良好的视觉印象，但当观察到关闭范围时，会详细说明。

最引人注目的部分是木星的好红点，因此我们创建了一组专门用于展示它的网格和纹理。
 
我们使用了类似于木星带区的一种机制：一组旋转部分彼此组合在一起，同时在其 "主要层" 下进行分组，以确保无论 rest 移动的速度如何，它们都保持不变。

当网格设置好后，应用了激烈 vortex 的不同层，并且每个光盘随后进行了动画处理，中心部分的移动速度最快，并且随着它向外移动时，rest 会逐渐下降。

![木星优秀 Red 点网格](images/ge-update-great-red-spot-mesh.jpg)

该组合也具有与每个其他网格相同的透视，同时还保持其从其原始 y 轴倾斜 (！ ) ，以允许自由地对旋转进行动画处理。 3600帧是基本速率，每一层的系数为一段旋转。

![木星极红点纹理](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a>直接在 Unity 中获取

在 Unity 中实现此功能时，需要记住几个关键事项。

当处理大型透明层集时，Unity 很容易混淆。 解决方法是复制每个网格的纹理材料，并对每个材料以5为递增的方式应用升序的渲染器队列值。

结果是，内部 shell 的 Render Queue 值为 3000 (默认值为) ，toned 外部的静态外边缘的值为3005，而 fast 白色的外部云则为3010。  (从内部层到外部层) 的良好的红色点在此模型中的值为3025。

![木星最终对象](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a>最后的处理

首次设置带纹理的木星层，证明该层不足以实现实现。

原来的行星标准着色器及其所有变体通过脚本（SunLightReceiver，MRTK 标准着色器不支持）接收其照明信息。

只需交换着色器并不是一种解决方案，因为行星标准着色器不支持带有透明胶片的纹理地图。 我们编辑了此着色器，使木星生成按预期方式工作。

最后，需要设置 Alpha 混合，方法是将源 Blend 设置为10，将目标混合设置为5。

![木星 Unity 属性](images/ge-update-jupiter-unity-render-queue.jpg)

可以在 Galaxy 资源管理器中查看木星的最终呈现！

## <a name="meet-the-team"></a>认识团队 

混合现实工作室团队由设计人员、三维音乐家、用户专家、开发人员、项目经理和工作室主管组成。 我们遍布世界各地的 hail：华南、加拿大、德国、以色列、日本、英国和美国。 我们是一位丰富的团队，来自于不同的背景：游戏-传统和独立、数字营销、卫生保健和科学。

我们很高兴为 HoloLens 2 创建 Galaxy 资源管理器，并更新 HoloLens (第一代) 、VR 和桌面版本。 

![Galaxy 资源管理器团队](images/ge-update-team-image.png)

从左到右： Artemis Tsouflidou (开发人员) 、Angie Teickner (可视化设计器) 、David Janer (UX 设计器) 、刘娜 Garrett (交付 & 生产主管) 、Yasushi Zonno (创造性潜在客户) 、Eline Ledent (开发人员) 和 Ben Turner (Sr-1a) 。
从左到右： Amit Rojtblat (技术艺术家) ，圣马丁 Wettig (3D 艺术家) ，Dirk Songuer (Studio Head) 。
不重要： Tim Gerken (技术组长) 和 Oscar Salandin (可视化设计器) 。

## <a name="additional-information"></a>其他信息

### <a name="mixed-reality-studios"></a>混合现实工作室

Microsoft 混合现实工作室团队-位于美洲、欧洲和 Asia-Pacific 中，是用户体验设计、全息计算、AR/VR 技术和三维开发方面的专家;包括3D 资产创建、DirectX、Unity 和 Unreal。 我们帮助构想预期的先期备货、设计、构建和交付解决方案，同时使客户能够在其组织中创造实实在在的影响。 录音室与超过22000个 Microsoft 服务专业人员密切合作，以实现企业应用程序集成、采用、操作和支持。