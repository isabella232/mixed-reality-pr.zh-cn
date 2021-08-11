---
title: 案例研究 - 在混合现实中表示人类
description: 当我们不能只创建出色的元素，而是利用混合现实中最真实的环境、对象和人员捕获时，会出现什么类型的机会？
author: mavitazk
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality， 人类， 头像， 混合现实捕获， 音量视频
ms.openlocfilehash: db21b6b02ce76403c2c59e37384c1c1602d8a63e003a8b5b6601c5daf7b9c2a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228513"
---
# <a name="case-study---representing-humans-in-mixed-reality"></a>案例研究 - 在混合现实中表示人类

James Turrell 使用浅色进行设计。 单步执行他的工作会模糊自己的深度和焦点感。 墙看起来既接近又无限，亮度让位给阴影。 通过仔细平衡光的颜色和光线来设计的不熟悉的感知。 [Turrell 将这些眼睛描述](https://www.sculpture.org/documents/scmag02/nov02/turrell/turrell.shtml)为"用眼睛感觉"，这是一种扩展自己对现实的理解的方式。  像 Turrell 想象的那样，出色的世界是利用我们感觉的强大工具，这与当今混合现实中的沉浸式环境不同。

![Wide Out - James Turrell (1998) ](../develop/platform-capabilities-and-apis/images/wide-out-james-turrell.jpg)

## <a name="how-do-you-represent-complex-real-world-environments-in-mixed-reality"></a>如何在混合现实中表示复杂的实际环境？

在沉浸式体验中表示 Turrell 的工作是一项极具吸引力的挑战。 照明、缩放和空间音频提供了表示他工作的机会。 虽然展示的几何环境需要相对简单的三维建模，但二者对于艺术家的焦点是次要的：光对感知的影响。

Turrell 的悲观、超现实最小是他工作的标志，但如果我们想要在混合现实中用更复杂的材料来表示一个展示，那又如何呢？

![中国 - Ai Wei以 (2013) ](../develop/platform-capabilities-and-apis/images/bang-ai-weiwie.jpg)

2013 年，艺术家 Ai Wei在[](https://www.designboom.com/art/ai-weiwei-bang-installation-at-venice-art-biennale-2013/)Ve以 Biennale 的 886 名艺术家为特色，创作了一部有关艺术的切线作品。 每个水桶都来自一个中国式飞船受到高度重视的纪元，这些便子在代之间传递。 工具本身（树的难解、块的精度、其仔细放置）对于 Ai 对现代文化的评论至关重要。

艺术家通过真实性传递艺术家的消息。 它们真实的表示形式对于体验至关重要，这带来了一项技术挑战：手动处理每个 886 个便器将非常详尽且成本高昂。 建模和定位需要多久？ 如何维护材料的真实性？ 从头重新创建这些对象从许多方面成为对图稿本身的解释。 如何保留艺术家的意图？

## <a name="methods-of-capturing-mixed-reality-assets"></a>捕获混合现实资产的方法

从头开始创建内容的替代项是捕获真实内容。 通过不断推进的一组捕获方法，我们可以开发混合现实中发现的每个核心资产类型的真实表示形式 (环境、对象和用户) 。

广泛的类别包括从众所周知的 2D 视频到最新形式的音量视频。 对于 Ai Wei一的展示，扫描 (通常称为其基本技术，照片测量) 可以在创建展示期间使用，并扫描每个便器本身。 360° 照片和视频捕获是另一种利用整个展示中定位的高质量全向相机来虚拟化体验的方法。 使用这些技术，可以开始了解规模感，理想情况下，需要足够详细的细节来了解每个块的步幅。 所有这些虽然以数字形式存在，但允许在现实中实现新的视点和透视。

![2D 到 Volumetric 视频](../develop/platform-capabilities-and-apis/images/2d-to-volumetric-video.png)

当我们不能只创建出色的元素，而是利用混合现实中最真实的环境、对象和人员捕获时，会出现什么类型的机会？ 探索这些方法之间的重叠有助于确定媒体的方向。

对于环境和对象，360° 图像处理软件正在不断发展，包括照片测量的元素。 将深度信息与场景隔离，高级 360° 视频有助于减轻在查看虚拟场景时头部卡在一条水波中感。

对于人们来说，合并和扩展运动捕获和扫描的新方法正在出现：运动捕获为将详细的人类运动引入视觉效果和视觉化字符打下基础，而扫描具有高级功能，可以捕获人脸和手等详细的人类视觉对象。 随着渲染技术的发展，名为"音量控制视频"的新方法基于这些技术，结合视觉和深度信息来创建下一代的 3D 人类捕获。

## <a name="volumetric-video-and-the-pursuit-of-authentic-human-capture"></a>Volumetric 视频和真实人类捕获的制作

人类是讲述故事的中心- 从最文字意义上讲：人类说话、执行或作为故事的主题。 当今早期沉浸式体验的一些最沉浸式和眼动时刻是社交。 从在房间中一起共享混合现实体验，到在全新的环境中看到你的好友。 人类元素甚至使最出色的现实，一个现实。

![VR 中的Howhow](../develop/platform-capabilities-and-apis/images/mindshow-in-vr-640px.jpg)

沉浸式体验中的头像在故事讲述中启用了一种新的故事。 最新应用正在重新思考虚拟人体所有权的概念，并设置一个代跃点来消除人之间的距离。 [像Howhow 这样的](https://mindshow.com/)公司正在开发利用头像的创意工具，让用户拥有全新的角色和角色。 另 [一些公司](https://en.wikipedia.org/wiki/Uncanny_valley)正在探索"探索"表达式的方法，这是一种潜在的无限创意机会， (人类) 属性的本质和必要特征。 如今，这种缺乏真实性有助于避免人类等同[](https://en.wikipedia.org/wiki/Uncanny_valley)的低谷，以及日常开发人员的一系列技术问题。 出于这些 (和更多) ，非现实头像很可能将成为可预见未来的默认值。 然而，虽然真实性对混合现实带来了巨大的挑战，但一些关键场景需要人类在 *3D 空间中的真实表示形式*。

在 Microsoft，Microsoft Research 的一个小团队在过去数年中一直开发一种通过一种形式的音量视频捕获人类的方法。 目前的过程类似于视频制作：而不是将移动应用于已放大的资产，而是完整的 3D 录制。 实时捕获性能和图像 - 这不是艺术家的工作，而是真实表示形式。 虽然技术刚开始扩展到商业应用程序，但音量限制视频的含义对于 Microsoft 对更多个人计算的愿景 [至关重要](https://www.youtube.com/watch?v=tcyj-_IEWt8)。

![Volumetric 视频 SIGGRAPH 2015](../develop/platform-capabilities-and-apis/images/volumetric-video-siggraph-2015.gif)

真正的人类捕获在混合现实中解锁新的独特体验类别。 看到你所识别的人，无论是名人、同事还是朋友，在数字媒体中都前所未有地创造一种深度的友同。 他们的面部、表情、动作中的细微差别都是他们是谁的一部分。 当我们可以在 3D 空间中捕获这些人类质量时，哪些机会会解锁？

如今，该团队正在通过关注娱乐和教育等行业来推动音量视频的界限[：Actiongram](https://www.microsoft.com/p/actiongram/9nblggh5ftmt)以创意字符和名人为特色，[](https://www.youtube.com/watch?v=BwWueXlsOrA)以创建混合现实故事。 [目标：Mars 展示](https://www.jpl.nasa.gov/news/news.php?feature=6220)（现在位于 NASA 的太空中心）提供一个容量级视频，该视频由宇航员将一名宇航员使用。Aldrin。 此体验使访问者能够与"小马"一起在月球表面四处浏览，同时他引入了人类对月球的冒号。

## <a name="humans-are-fundamental-to-mixed-reality"></a>人类是混合现实的基础

设计使这些视频看起来很自然的方式会带来挑战，但团队却看到了巨大的潜力。 随着技术更易于访问，从录制移动到实时捕获，这些机会将会扩展。

[Holoportation](https://www.microsoft.com/research/project/holoportation-3/) 是一项基于相同基本技术、真实捕获视觉和深度信息以及实时呈现结果的科研工作。 团队正在探索现实人类表示形式对于会话和共享体验的未来意味着什么。 当从世界上任何位置将某人的三维捕获添加到环境中时，会发生什么情况？

![对话的未来](../develop/platform-capabilities-and-apis/images/girl-with-dress.jpg)

从将新级别的沉浸式分层到日常应用（如 Skype）到彻底改变数字会议与商务旅行的概念， 音量容量视频开启了独特的场景：一位专家在远地大陆上虚拟培训医生，或者数字朋友，他们坐在房间的长相和房间中。 向混合现实体验添加真实的人类表示形式将从根本上改变数字会议与商务旅行的概念。

正如 James Turrell 的抽象艺术和 Ai Wei以关键真实性提供自己独特的技术挑战一样，将人类表示为创意头像和真实捕获的方法也一样。 鉴于另一个，不能忽略其中一个，探索每个功能的潜力将有助于我们了解这一新空间中的人类交互。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Mark Vitazko" width="60" height="60" src="images/mark-vitazko.jpg"></td>
<td style="border-style: none"><b>Mark Vitazko</b><br>用户体验设计师 @Microsoft</td>
</tr>
</table>
