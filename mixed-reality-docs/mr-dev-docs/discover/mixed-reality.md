---
title: 什么是混合现实？
description: 探讨混合现实，展示如何在混合现实范围内使用 AR 和 VR 设备。
author: brandonbray
ms.author: branbray
ms.date: 08/26/2020
ms.topic: article
keywords: 混合现实, 全息, AR, VR, MR, XR, 增强现实, 虚拟现实, 说明, 案例研究, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 什么是虚拟现实, 什么是增强现实
ms.localizationpriority: high
ms.openlocfilehash: e524312b2e479b1c3d05039403aba10de864ae18
ms.sourcegitcommit: 5603dc9f6511707cb8b215f20f6c6485ef480538
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/16/2021
ms.locfileid: "112230209"
---
# <a name="what-is-mixed-reality"></a>什么是混合现实？

![在 HoloLens 2 用手进行点选和提交](images/02_MixedRealitySlashMixedReality.png)

混合现实是物理世界和数字世界的混合，开启了人、计算机与环境交互之间的联系。 这一新的现实基于计算机视觉、图形处理能力、显示技术和输入系统的进步。 但是，“混合现实”一词由 Paul Milgram 和 Fumio Kishino 在其 1994 年发表的论文 [A Taxonomy of Mixed Reality Visual Displays](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)（混合现实视频显示的分类法）中提到。 此论文探讨了“虚拟连续体”的概念以及应用于显示内容的类别分类法。 从那此后，混合现实的应用包括以下各项，已经超越了显示内容：
* 环境输入
* 空间音效
* 真实和虚拟空间中的位置和定位

![混合现实范围图像](images/mixedrealityspectrum-worlds.png)<br>
插图：混合现实是将物理世界与数字世界相融合的结果。

<br>

---

## <a name="environmental-input-and-perception"></a>环境输入和感知

过去几十年来，对人类输入与计算机输入之间关系的探索一直在继续，从而形成了称作“人机交互”(HCI) 的学科。 人类输入是通过不同的方式进行的，包括键盘、鼠标、触摸、笔迹、语音，甚至 Kinect 骨骼跟踪。

传感器和处理技术的进步为计算机环境输入创造了新领域。 计算机与环境之间的交互是对环境的理解或认知，这就是 Windows 中显示环境信息的 API 称作[感知 API](/uwp/api/Windows.Perception) 的原因。 环境输入捕获如下所述的信息：用户在世界上的位置（[头部跟踪](../design/coordinate-systems.md)）、表面和边界（[空间映射](../design/spatial-mapping.md)和[场景理解](../design/scene-understanding.md)）、环境照明、环境音效、对象识别和定位。

<br>

![显示计算机、人类与环境之间的交互的文氏图](images/mixed-reality-venn-diagram-300px.png)<br> 
*插图：* 计算机、人类与环境之间的交互。

<br>

计算机处理、人类输入和环境输入 - 这三者的组合为创建真正的混合现实体验奠定了基础。 物理世界中的运动转换为数字世界中的运动。 物理世界中的边界会影响数字世界中的应用体验，例如玩游戏。 如果没有环境输入，体验就无法在物理现实与数字现实之间进行融合。<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>混合现实范围

由于混合现实融合了物理世界和数字世界，这两种现实定义了称作“虚拟连续体”的范围的两个极端。 我们将这一系列的现实称作“混合现实范围”。 左侧是物理现实，是人类所在的环境。 右侧是对应的数字现实。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>增强现实与虚拟现实

目前市场上的大多数手机几乎都不具备环境理解功能。 它们提供的体验无法混合物理现实和数字现实。 在物理世界的视频流中叠加图形的体验是“增强现实”。  遮挡视线以呈现数字体验的体验是“虚拟现实”。  在增强现实和虚拟现实之间实现的体验形成了“混合现实”：
* 从物理世界开始，我们可以放置一个数字对象（例如全息影像），就如同它就在那里一样。
* 从物理世界开始，另一人（头像）的数字表示形式会显示他（她）在留下便条时所处的位置。 换而言之，这种体验代表不同时间点的异步协作。
* 从数字世界开始，物理世界中的物理边界（例如墙壁和家具）在体验中以数字形式显示，以帮助用户避开物理对象。

<br>

![混合现实范围](images/mixedrealityspectrum.png)<br>
插图：混合现实范围

<br>

当今的大部分增强现实和虚拟现实产品/服务仅代表了此范围的一小部分，且被认为是较大混合现实范围的子集。 Windows 10 的开发考虑到了整个范围，可以融合现实世界中人员、地点和物品的数字表示形式。


## <a name="devices-and-experiences"></a>设备和体验

有两种主要类型的设备可以提供 Windows Mixed Reality 体验：
1. 全息设备的特征是能够将数字内容放入真实世界，就像是这些内容就在那里。
2. 沉浸式设备的特征是能够创建“存在感”- 隐藏物理世界，将其替换为数字体验。

<table>
<tr>
<th width="30%"> 特征</th><th width="35%"> 全息设备</th><th width="35%"> 沉浸式设备</th>
</tr><tr>
<td><strong>示例设备</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>显示器</strong></td><td> 看透显示内容。 可让用户在戴上头戴显示设备时观看物理环境。</td><td> 不透明显示。 在戴上头戴显示设备时阻挡物理环境。</td>
</tr><tr>
<td><strong>移动</strong></td><td> 六度自由全方位运动，支持旋转和平移。</td><td> 六度自由全方位运动，支持旋转和平移。</td>
</tr>
</table> 


> [!NOTE]
> 设备是与单独的电脑保持连接或拴定状态（通过 USB 数据线或 Wi-Fi）还是保持独立状态（断开连接），并不能反映设备是全息设备还是沉浸式设备。 可改善运动性的功能会改善体验，而全息设备和沉浸式设备都可以保持连接或断开连接状态。

技术进步创造了混合现实体验，但目前还没有能兼容所有相关体验的设备。 Windows 10 为设备制造商和开发人员提供了一个通用的混合现实平台。 当今的设备可以支持混合现实范围内的某个特定范围，而新设备扩展了该范围。 未来，全息设备将变得有沉浸感，而沉浸式设备也将变得更有全息感。

<br>

![混合现实范围内的设备类型](images/Final_WhatIsMixedReality07.png)<br>
插图：设备在混合现实范围内所处的位置

最好是考虑应用程序或游戏开发人员想要创建的体验类型。 体验往往面向混合现实范围内的特定点或部分。 开发人员应考虑所要面向的设备功能。 依赖于物理世界的体验最好是在 HoloLens 上运行。
* **向左（接近物理现实）。** 用户保留在其物理环境中，永远不相信他们已离开该环境。
* 中间（完全混合现实）。 这些体验融合了真实世界和数字世界。 电影[勇敢者的游戏](https://en.wikipedia.org/wiki/Jumanji)的观众能够适应故事发生地的房子与丛林环境融合后的物理结构。
* **向右（接近数字现实）。** 用户将体验到一个数字环境，并且不会意识到其周围物理环境中发生的情况。

## <a name="next-discovery-checkpoint"></a>下一个发现检查点

如果你按安排的[发现之旅](get-started-with-mr.md)操作，则你正在了解混合现实的基本知识。 从这里，你可以进入下一基本主题： 

> [!div class="nextstepaction"]
> [什么是全息图？](hologram.md)
