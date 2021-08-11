---
title: Kippy 的转义的制作
description: 随着我们一起探索 Kippy 的 Escape 混合现实应用程序在 Unreal Engine HoloLens 2开发。
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Unreal， Unreal Engine 4， UE4， HoloLens， HoloLens 2， 混合现实， 部署到设备， 电脑， 文档， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
appliesto:
- HoloLens 2
ms.openlocfilehash: 96799de948cf9e1cbca89b7e781f3f830fbc005810680d1164d04acb757b1a09
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208178"
---
# <a name="the-making-of-kippys-escape"></a>Kippy 转义的制作
![Kippy 的 Escape 英雄图像](images/KippysEscape_1920.jpg)

Kippy 机器人唤醒，发现自己被一个岛所依赖。 由你提供解决问题的帽来帮助它找到返回火箭飞船的路径！ 打开HoloLens 2，[然后](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd)从 Microsoft Store 下载应用，或者从 GitHub 克隆存储库，[](https://github.com/microsoft/MixedReality-Unreal-KippysEscape)确保 Kippy 主页安全！  

> [!IMPORTANT]
> 如果要从 GitHub 存储库生成 Kippy 的 Escape，请确保使用 **Unreal Engine 4.25** 或更高版本。

Kippy 的 Escape 是一个[](/hololens/hololens2-hardware)HoloLens 2 Unreal Engine 4 和混合现实[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal)构建的开源示例应用。 本文将指导你完成从第一项原则和视觉设计到实现和优化体验的过程。 有关使用 MRTK UX Tools 开发混合现实应用程序的信息，请参阅 [Unreal 开发概述](unreal-development-overview.md)。

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>从 Microsoft Store HoloLens 2
如果有HoloLens 2，可以直接在设备中下载并安装应用。

<a href='//www.microsoft.com/store/apps/9nbd7gl86vkd?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="first-principles"></a>第一原则 

在设置创建 Kippy 的 Escape 时，我们的目标是创建一个体验，以突出显示[Unreal Engine](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html)的 HoloLens 2 支持、HoloLens 2 的功能和混合现实 Toolkit。 我们希望激励开发人员想象他们可以通过 Unreal 和 HoloLens 2。  

我们针对体验提供了三个指导原则：需要有趣、交互，并且具有较低的进入障碍。 我们希望体验足够直观，即使是第一次混合现实用户也不需要教程即可完成。  

## <a name="designing-the-game"></a>设计游戏 

该HoloLens 2可以访问如今在游戏方面发现其他功能的设计功能。 可以使用手直接推送或操作对象，也可以以眼动跟踪为目标。 这些关键功能隐藏了我们在 Kippy 的 Escape 中构建的一些有趣时刻。  

使用独特的HoloLens 2功能作为游戏设计的指南，我们提供了几个小型环境方案。 岛有意义，因为它们可以根据不同的球员身高进行调整，并提供了一些桥概念。 我们登陆时的主题是""技术，其理念是有人用每个岛提供的奇特能量构建了一个机器，利用着一种奇怪的能源。 每个岛都有其自己的外观，这是一个有助于创造视觉兴趣的详细信息。 在建模和文本处理之间实现良好的平衡会保持绘制调用的低性能，因此设计样式化外观时已考虑这一点。 

![早期游戏设计 ](images/kippys-escape/kippys-escape-img-01.png)
 *描绘了体验外观的一些早期草图*

![呈现第二个岛 ](images/kippys-escape/kippys-escape-img-02.png)
 *的第二个岛呈现*

为了在简短的生产计划内保持一致，我们一致认为浮动字符可以捕获意图和情感，而无需严格的动画周期。 因此 Kippy 已出生！ 它通过眼睛和最小的声音效果来模拟几个不同的表达式，以帮助引导玩家在整个体验中。 

![Kippy 通过眼睛显示不同的表达式](images/kippys-escape/kippys-escape-img-03.gif)

*Kippy 通过眼睛显示不同的表达式*

![如果用户花费太长时间解决难题，Kippy 会提示用户](images/kippys-escape/kippys-escape-img-04.gif)

*如果用户花费太长时间解决难题，Kippy 会提示用户*

除了字符和环境设计之外，我们还努力让游戏感觉有趣。 眼动跟踪使我们能够发射材料属性和声音属性，这些特性突出显示了游戏的关键部分。 空间音频有助于让玩家周围的水平感觉像家一样。 能够抓取对象、按钮和操作滑块可推动创新玩家参与。 请务必确保这些连接点感觉自然。 

![当用户的手接近桥电缆时，桥电缆的末端会亮起](images/kippys-escape/kippys-escape-img-05.gif)

*当用户的手接近桥电缆时，桥电缆的末端会亮起*

## <a name="building-the-game-mechanics"></a>构建游戏机制 

Kippy 的 Escape 在很大程度上依赖于混合现实 UX Tools 组件，使游戏交互 - 即手部交互参与者、边界控件、操控器、滑块和按钮。   

手 [部交互执行](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) 组件支持直接和远地操作全息影像。 在 Kippy 的 Escape 开始时，用户有机会设置游戏的位置。 手部射线从用户的手部延伸，可以轻松操作远离你的大全息影像，如下图 gif 所示。  

![手部交互执行组件 gif](images/kippys-escape/kippys-escape-img-06.gif)

占位符场景本身可以使用 UX Tools 边界控件组件进行拖动 [和](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/BoundsControl.html) 旋转。  

第二个岛上，用户必须选取 gem，将其放在匹配的槽中。 gem 具有 [附加的](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html) 操控器，允许用户拾取并放置它们。 

![操控器示例 gif](images/kippys-escape/kippys-escape-img-07.gif)

可 [按下](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html) 按钮是打开第三个岛供其使用的关键。  

![可按下按钮示例 gif](images/kippys-escape/kippys-escape-img-08.gif)

滑块 [组件](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PinchSlider.html) 出现在第四个岛上，触发要引发的最后一个桥。  

![滑块组件示例 gif](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>优化HoloLens 2 

在构建在移动设备上运行的任何体验中，关注性能至关重要。 Unreal 4.25 包含支持移动多视图的主要更新，可显著减少渲染开销并提高帧速率。 建议在[优化时查看](performance-recommendations-for-unreal.md)其他建议的性能设置HoloLens 2 Unreal 进行开发。  

物理对象在性能方面仍很昂贵，因此使用了几个更智能的解决方法。 例如，第三个"桥"需要堆积一些阻塞桥的碎片。 除了强制影响作为物理对象的对象的粒子外，它触发交换，将静态分子切换为一种爆炸粒子效果。 

![gif 优化HoloLens 2示例](images/kippys-escape/kippys-escape-img-10.gif) 

我们还通过将绘制调用从 400 多个缩减到 ~260 个： 
* 降低网格复杂性
* 组合网格
* 删除一些初始动态照明元素

虽然我们可能会完成更多工作，但我们认为这是性能和视觉质量之间的良好平衡。  

## <a name="try-it-out"></a>试试看！ 

启动HoloLens 2，[然后](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd)从 Microsoft Store 下载应用，或者从 GitHub 克隆存储库并自己生成[](https://github.com/microsoft/MixedReality-Unreal-KippysEscape)应用！  

## <a name="about-the-team"></a>关于团队

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>首席游戏设计器</i><br>Jack 目前负责 Microsoft 的混合现实体验，HoloLens 2项目和 AltspaceVR，以前是 HoloLens 平台团队的设计人员。</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>五</b><br><i>创建器</i><br>在混合现实开发人员平台上工作，并领导团队的 Unreal Engine 相关工作。</td>
</tr>
</table>

特别感谢 [Framestore 的好友](https://www.framestore.com/) 帮助我们将 Kippy 的转义带进生命。 从字符开发到资产设计，到游戏编程，他们在此项目上的协作至关重要。