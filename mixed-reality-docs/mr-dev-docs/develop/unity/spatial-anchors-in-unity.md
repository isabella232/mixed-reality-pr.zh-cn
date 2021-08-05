---
title: Unity 中的世界锁定和空间锚
description: 了解如何在 Unity 混合现实应用程序中使用全球锁定工具和空间锚。
author: hferrone
ms.author: v-hferrone
ms.date: 04/7/2021
ms.topic: article
keywords: Unity，空间定位点，定位存储区，HoloLens，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，世界锁定工具，全息影像
ms.openlocfilehash: 34ef74ab968bff04188b1010eb4c863fd73d76ee6b1dd8a0bd89c7d4232a2be9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208835"
---
# <a name="world-locking-and-spatial-anchors-in-unity"></a>Unity 中的世界锁定和空间锚

![世界锁定工具英雄图像](images/wlt-img-01.jpeg)

在创建混合现实应用程序的过程中，你可以将你的全息影像固定在原地、与你一起移动，或者，在某些情况下，相对于其他全息影像的位置是很大的。 本文将指导你使用全球锁定工具来完成我们推荐的解决方案，但我们还将介绍如何在 Unity 项目中手动设置空间锚。 在跳转到任何代码之前，请务必了解 Unity 如何在其自己的引擎中协调空间和定位点。

## <a name="world-scale-coordinate-systems"></a>全球坐标系统

目前，编写游戏、数据可视化应用程序或虚拟现实应用时，典型的方法是建立一个绝对 **世界坐标系统** ，所有其他坐标都可以可靠地映射回。 在该环境中，始终可以找到一个稳定的转换，用于定义该世界中任意两个对象之间的关系。 如果未移动这些对象，则其相对转换始终保持不变。 在呈现纯粹的虚拟世界时，这种全局坐标系统很容易获得，在这种情况下，你可以提前了解所有几何。 如今，房间内的 VR 应用通常建立此类绝对房间级坐标系统，并将其原点置于地面上。

与此相反，untethered mixed reality 设备（如 HoloLens）对世界有动态的传感器驱动理解，随着用户的周围时间的推移而不断调整其知识，因为他们会在一座建筑的整个楼层走出很多时间。 在全球范围内，如果你将所有全息影像都置于一个简单的硬坐标系中，则这些全息影像将最终偏移一段时间，无论是在世界上还是相对的。

例如，耳机当前可能相信世界上的两个位置相隔4米，然后在以后优化此理解，了解位置实际上是3.9 米。 如果这些全息影像最初在一个硬坐标系中相隔4米，则其中一个将始终从真实世界向下显示0.1 米。

您可以手动将 **空间锚定** 到 Unity 中，以便在用户为移动设备时，在物理世界中维护全息影像的位置，但这 sacrifices 了虚拟世界内的自我一致性。 不同的定位点会不断地彼此移动，同时也会在全局坐标空间中移动。 在此方案中，简单的任务（例如布局）变得困难且物理学模拟出现问题。

**世界上的锁定工具** 为您提供了这两种世界的最大优势，即在用户四处移动时，使用内部的空间锚点内部提供的稳定坐标系统。 这些工具会分析照相机的坐标，并分析每个帧的空间锚。 不是更改世界上所有内容的坐标来补偿用户头坐标中的更正，而只是修复 head 的坐标。

## <a name="choosing-your-world-locking-approach"></a>选择您的全球锁定方法

* **我们建议** 使用 **全球锁定工具** 来满足所有全息图定位需求。 
    * 世界锁定工具提供了一个稳定的坐标系，可最大程度地减少虚拟和实际标记之间的明显不一致。 另一种方法是，它将整个场景与共享的锚池一起锁定，而不是使用该组自己的单独定位点锁定每组对象。
* **对于使用 OpenXR 或 Windows XR 插件的 Unity 2019/2020**，需要使用 **ARAnchorManager**
* **对于较旧的 Unity 版本或 WSA** 项目，需要使用 **WorldAnchor**

## <a name="setting-up-world-locking"></a>设置世界锁定 

[!INCLUDE[](includes/world-locking/world-locking-setup.md)]

## <a name="persistent-world-locking"></a>持久世界锁定

空间锚点在应用程序会话之间将全息区保存在实际空间内。 保存到 HoloLens 的锚定存储区后，可以在不同的会话中找到并加载这些位置，在没有 internet 连接的情况下是理想的备选方案。

> [!IMPORTANT]
> 本地定位点存储在设备上，而 Azure 空间定位点存储在云中。 如果你想要使用 Azure 云服务来存储定位点，我们有一个文档可指导你如何集成 [Azure 空间定位点](../mixed-reality-cloud-services.md#azure-spatial-anchors)。 请注意，你可在同一项目中使用本地定位点和 Azure 定位点，不会发生冲突。

[!INCLUDE[](includes/world-locking/world-locking-persistence.md)]

## <a name="sharing-coordinate-spaces"></a>共享坐标空间 

如果要共享世界锁定的坐标空间，请查看我们的综合性 [共享体验文档](shared-experiences-in-unity.md)。

请注意，世界锁定工具中尚不直接支持 Azure 空间锚点，因此共享体验将要求你手动创建空间锚。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所说的 Unity 开发检查点旅程，就是探索混合现实核心构建基块的过程。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [空间映射](spatial-mapping-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅
* [全球锁定工具简介](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/IntroFAQ.html)
* [快速入门指南](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/QuickStart.html)
* [教程](https://microsoft.github.io/MixedReality-WorldLockingTools-Samples/Tutorial/01_Minimal/01_Minimal.html)
* [示例](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/SampleApplications.html)
* [空间锚点持久性](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">用于 Unity 的 Azure 空间定位点 SDK</a>
* [体验规模](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [空间阶段](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Unity 中的失跟](tracking-loss-in-unity.md)
* [空间定位点](../../design/spatial-anchors.md)
* [Unity 中的共享体验](shared-experiences-in-unity.md)
