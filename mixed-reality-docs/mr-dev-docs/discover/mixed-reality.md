---
title: 什么是混合现实？
description: 探讨混合现实，展示如何在混合现实范围内使用 AR 和 VR 设备。
author: qianw211
ms.author: v-qianwen
ms.date: 07/01/2021
ms.topic: article
keywords: 混合现实, 全息, AR, VR, MR, XR, 增强现实, 虚拟现实, 说明, 案例研究, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 什么是虚拟现实, 什么是增强现实
ms.localizationpriority: high
ms.openlocfilehash: fc2686c409883e948f1e5f3a631060a66cd55849f998f94a201801ac10b65808
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115205030"
---
# <a name="what-is-mixed-reality"></a>什么是混合现实？

混合现实是计算领域的下一波浪潮，紧随其后的是大型机、电脑和智能手机。 混合现实正在消费者和企业之间成为主流。  它提供与居住空间数据、事务以及好友之间的本能交互，将我们从受屏幕束缚的体验中解放出来。  世界各地数以亿计的在线探索者通过他们的手持设备体验了混合现实。  移动 AR 提供了目前社交媒体上最主流的混合现实解决方案。 人们甚至可能没有意识到，他们在 Instagram 上使用的 AR 滤镜就是混合现实体验。  Microsoft 混合现实将真正令人惊叹的人体全息影像、高保真全息 3D 模型及周围的现实世界结合起来，将所有这些用户体验提升到新的水平。

![在 HoloLens 2 用手进行点选和提交](images/02_MixedRealitySlashMixedReality.png)

混合现实是物理世界和数字世界的混合，开启了人、计算机和环境之间的自然且直观的 3D 交互。 这种新的现实基于计算机视觉、图形处理、显示技术、输入系统和云计算的进步。 Paul Milgram 和 Fumio Kishino 在其 1994 年发表的论文“[A Taxonomy of Mixed Reality Visual Displays](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)”（混合现实视频显示的分类法）中首次引入“混合现实”一词。 该论文中探讨了“虚拟连续体”的概念以及视觉显示的分类法。 从那此后，混合现实的应用包括以下各项，已经超越了显示内容：

* 环境理解：空间映射和定位点。
* 人类理解：手动跟踪、目视跟踪和语音输入。
* 空间音效。
* 物理和虚拟空间中的位置和定位。
* 混合现实空间中的 3D 资产协作。

![混合现实范围图像](images/mixedrealityspectrum-worlds.png)<br>
插图：混合现实是将物理世界与数字世界相融合的结果。

<br>

---

## <a name="environmental-input-and-perception"></a>环境输入和感知

在过去几十年里，人机关系持续通过输入方式变化得到发展。  进而诞生了称作“人机交互”(HCI) 的新学科。 人类输入现可包括键盘、鼠标、触摸、笔迹、语音和 Kinect 骨骼跟踪。

传感器和处理能力的进步在于基于先进的输入方法创造出了计算机对环境的新感知。 这就是 Windows 中显示环境信息的 API 称作[感知 API](/uwp/api/Windows.Perception) 的原因。 环境输入可以捕获： 

* 某个人的身体在物理世界中的位置（[头部跟踪](../design/coordinate-systems.md)） 
* 对象、表面和边界（[空间映射](../design/spatial-mapping.md)和[场景理解](../design/scene-understanding.md)） 
* 环境照明和音效
* 对象识别
* 物理位置

<br>

![显示计算机、人类与环境之间的交互的文氏图](images/mixed-reality-venn-diagram-300px.png)<br> 
*插图：* 计算机、人类与环境之间的交互。

<br>

这三个基本元素的组合为创建真正的混合现实体验奠定了基础：

* 由云提供支持的计算机处理
* 先进的输入方法
* 环境感知

我们在物理世界中移动时，我们的运动将反映在数字现实中。 物理边界影响数字世界中的混合现实体验，如游戏或生产设施中基于任务的指导。 有了环境输入和感知，体验开始在物理现实与数字现实之间进行融合。

<br>

---

## <a name="the-mixed-reality-spectrum"></a>混合现实范围

混合现实融合了物理世界和数字世界。  这两种现实定义了称作“虚拟连续体”的范围的两个极端。 我们将这一系列的现实称作“混合现实范围”。  一端是人类所在的物理现实。 另一端是相对应的数字现实。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>增强现实与虚拟现实

目前市场上的大多数手机几乎都不具备环境感知功能。 这些手机提供的体验无法混合物理现实和数字现实。 

在物理世界中叠加图形、视频流或全息影像的体验称为“增强现实”。 遮挡视线以呈现全沉浸式数字体验的体验是“虚拟现实”。 在增强现实和虚拟现实之间实现的体验形成了“混合现实”，通过它可以：

* 在物理世界中放置一个数字对象（如全息影像），就如同它真实存在一样。
* 在物理世界中以个人的数字形式（虚拟形象）出现，以在不同的时间点与他人异步协作。
* 在虚拟现实中，物理边界（如墙壁和家具）以数字形式出现在体验中，帮助用户避开物理障碍物。

<br>

![混合现实范围](images/mixedrealityspectrum.png)<br>
插图：混合现实范围

<br>

当今的大部分增强现实和虚拟现实体验仅代表了混合现实的一小部分。 Windows 10 的开发考虑到了整个范围，可以融合现实世界中人员、地点和物品的数字表示形式。

## <a name="devices-and-experiences"></a>设备和体验

有两种主要类型的设备可以提供 Windows Mixed Reality 体验：
1. 全息设备的特征是能够将数字内容放入真实世界，就像是这些内容就在那里。
2. 沉浸式 VR 设备的特征是能够隐藏物理世界并将其替换为全沉浸式数字体验，从而创建“存在感”。

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
> 设备是与单独的电脑保持连接（通过 USB 数据线或 Wi-Fi）还是断开连接状态，并不能反映设备是全息设备还是沉浸式设备。 可改善运动性的功能会提供更好的体验。 全息设备和沉浸式设备都可以保持连接或断开连接状态。

混合现实体验是技术进步的结果。 目前还没有任何能兼容所有相关体验的设备。 Windows 10 为设备制造商和开发人员提供了一个通用的混合现实平台。 当今提供的任何设备都可以支持混合现实范围内的某个特定范围。 未来有望出现支持范围更广的新设备：全息设备将变得更有沉浸感，而沉浸式设备也将变得更具全息感。

<br>

![混合现实范围内的设备类型](images/Final_WhatIsMixedReality07.png)<br>
插图：设备在混合现实范围内所处的位置

作为应用程序或游戏开发人员，你要创建什么类型的体验？ 体验往往面向混合现实范围内的特定点或部分。 你需要考虑所要面向的设备功能。 依赖于物理世界的体验最好是在 HoloLens 上运行。

* **向左（接近物理现实）。** 用户保留在其物理现实中，并且不相信他们已离开该现实。
* 中间（完全混合现实）。 这些体验融合了真实世界和数字世界。 例如，在电影[勇敢者的游戏](https://en.wikipedia.org/wiki/Jumanji)中，故事发生地的房子与丛林环境融合后的物理结构。
* **向右（接近数字现实）。** 用户将体验数字现实，但不会意识到其周围的物理现实。

## <a name="next-discovery-checkpoint"></a>下一个发现检查点

你正处于我们为你安排的[探索之旅](get-started-with-mr.md)的起点，正在探索混合现实的基础知识。 从这里，你可以进入下一基本主题： 

> [!div class="nextstepaction"]
> [什么是全息图？](hologram.md)
