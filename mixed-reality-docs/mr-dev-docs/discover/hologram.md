---
title: 什么是全息图？
description: HoloLens 使你可以查看与世界上出现在世界各地的光线和声音的三维全息影像，并与之交互。
author: hferrone
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，HoloLens，全息影像，设计，交互
ms.openlocfilehash: f902639e66246c9184750ebc58dbad1c04b2bb5a
ms.sourcegitcommit: cc27d31f0cebaf9fc4221a3300a9e3d73230b367
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/14/2020
ms.locfileid: "94631465"
---
# <a name="what-is-a-hologram"></a>什么是全息图？

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


通过 HoloLens，你可以创建 **全息影像** ，这些对象是在世界各地显示的光线和声音，就像它们是真实的对象一样。 全息影像会响应你的 [注视](../design/gaze-and-commit.md)、 [手势](../design/gaze-and-commit.md#composite-gestures) 和 [语音命令](../design/voice-input.md)，并可与你周围的 [实际表面](../design/spatial-mapping.md) 交互。 利用全息影像，可以创建属于你的世界的数字对象。

<br>


## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>全息影像</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a>全息图是由光和声音组成的

HoloLens [呈现](../develop/platform-capabilities-and-apis/rendering.md) 的全息影像会直接显示在用户眼睛的前方。 全息影像为你的世界增加了灯光，这意味着你会看到来自显示器的灯光和来自你周围的光线。 HoloLens 不会从眼睛中去除光，因此无法用黑色呈现全息影像。 但黑色内容将显示为透明。

全息影像可以有许多不同的外观和行为。 有些是真实的、坚实的，而有些则是 cartoonish 和 ethereal。 全息影像可以突出显示你的环境中的功能，并且它们可以是应用用户界面中的元素。

![手动操作全息图](images/hologram-hands-940px.jpg)

全息影像还可以发出 [声音](../design/spatial-sound.md)，这会显示在周围的特定位置。 在 HoloLens 上，声音来自两个扬声器，它们直接位于你的耳上方，而不会覆盖它们。 与显示器类似，扬声器是累加的，引入新声音，而不会阻止环境中的声音。

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>全息图可以放在世界上，也可以与你一起标记

如果你有想要在其中使用全息图的特定位置，则可以将其精确 [放置](../design/coordinate-systems.md) 在世界各地。 当您浏览该全息图时，它会相对于您的世界显得稳定。 如果使用 [空间锚点](../design/coordinate-systems.md#spatial-anchors) 将该对象牢固地固定到世界，则系统甚至可以在以后回来时记住它的位置。

![在零售空间中使用 Microsoft Dynamics 365 布局的两个男人](images/HLS19_retailLayoutHologram_001-940px.jpg)

某些全息影像会按用户进行操作。 这些基于标记的影像的位置本身相对于用户，而不管它们在何处。 你甚至可以选择将一段时间带到一段时间，然后将其放在墙上的另一个房间。

**最佳做法**
* 在某些情况下，可能需要在整个体验中轻松发现和查看全息影像。 此类定位有两个高级方法。 让我们将它们称为 **"显示-锁定"** 和 **"正文锁定"** 。
   * 显示锁定的内容按位置 "锁定" 到设备显示。 这是一种很难的原因，其中包括 "clingyness" 的非自然感觉，这使得许多用户感到沮丧并希望 "晃动它"。 通常，许多设计人员发现，更好的做法是避免显示锁定内容。
   * 主体锁定的方法远远 forgivable。 正文锁定是指受限用户的主体或注视，而将其置于3d 空间中以环绕用户的情况。 许多经验都采用了一种正文锁定行为，其中全息图 "跟随" 用户看，这使用户可以旋转其身体，而不会丢失全息影像。 合并延迟有助于使全息图移动更加自然。 例如，Windows 全息版 OS 的某些核心 UI 使用的是正文锁定，这种情况下，用户将看起来像是一种灵活的、弹性的延迟，同时用户会将其标头。
* 将全息图放置在舒适的观看距离上，通常会远离1-2 米。
* 为必须持续在全息帧中的元素提供一定数量的偏移，或在用户更改其视图时考虑将内容动态显示在一侧。

**将全息影像置于最佳区域-介于 1.25 m 和5分钟之间**

这两个指标最适用，体验会使你从一次计量获得更近的距离。 远距离超过一米，经常进行深入了解的全息影像比静态全息影像更有可能出现问题。 当内容太近时，请考虑适当地剪辑或淡化内容，以便不会使用户进入意外体验。

![从用户放置全息影像的最佳距离。](images/distanceguiderendering-950px.png)

<br>

---


## <a name="a-hologram-interacts-with-you-and-your-world"></a>全息图与您和您的世界交互

全息影像不仅适用于灯光和声音;它们也是您世界的一个活动部分。 用手看一个全息影像和手势，然后就可以开始使用全息图。 向全息影像发出语音命令，然后可以回复。

![一组政府实用工作人员组，使用 Microsoft HoloLens 2 在风场开发项目上协作](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

全息影像实现了不可能在其他地方使用的个人交互。 因为 HoloLens 知道其在世界各地的位置，所以，当您在房间内浏览时，全息字符可以直接显示您的眼睛。

全息图还可以与你的环境交互。 例如，您可以将一个全息弹跳球置于一个表上方。 然后，通过 [点击](../design/gaze-and-commit.md#composite-gestures)，观看球弹跳并在到达表时发出声音。

全息影像还可以由真实的对象封闭像素。 例如，全息人物可能会走出大门的门和背面。

**有关集成全息影像和现实世界的技巧**
* 与 gravitational 规则相协调，可以更轻松地与和更可信相关。 例如：将一个全息狗置于 & 表上的花瓶，而不是让它们浮于空间。
* 许多设计人员发现，他们甚至可以通过在 believably 的表面上创建 "负阴影" 来更好地集成全息影像。 为此，可在两个全息图的地面上创建软光亮，然后从发光中减去 "阴影"。 软发光与现实世界中的光线相集成，而阴影则是环境中的全息影像。

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a>全息图 <br>你可以梦想<br>
        作为全息开发人员，您可以将您的创造性从2D 屏幕和世界各地突破起来。<br><br>
        *你* 将生成什么？
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![客厅的全息虚世界](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a>下一个发现检查点

如果你按我们介绍的[发现之旅](get-started-with-mr.md)操作，那么你对混合现实基本知识的探索已完成了一部分了。 从这里，你可以进入下一基本主题： 

> [!div class="nextstepaction"]
> [扩展设计过程](case-study-expanding-the-design-process-for-mixed-reality.md)

