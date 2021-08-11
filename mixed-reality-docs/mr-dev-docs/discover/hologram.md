---
title: 什么是全息图？
description: HoloLens 使你可以查看与世界上出现在世界各地的光线和声音的三维全息影像，并与之交互。
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality，HoloLens，全息影像，设计，交互，混合现实耳机，Windows Mixed reality 耳机，增加的现实情况
ms.openlocfilehash: e028fe6180bded26263fa47feb5acefc94570222e43f10fe85db5adf90307844
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202101"
---
# <a name="what-is-a-hologram"></a>什么是全息图？

HoloLens 使你可以查看 **全息影像**，这是像像现实对象一样出现在世界各地的光线和声音的对象。 全息影像可以响应您的[注视](../design/gaze-and-commit.md)、[手势](../design/gaze-and-commit.md#composite-gestures)和[语音命令](../design/voice-input.md)。 它们甚至可以与您周围的 [真实表面](../design/spatial-mapping.md) 交互。 全息影像是世界上的数字对象。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
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

### <a name="light"></a>亮

HoloLens[呈现](../develop/platform-capabilities-and-apis/rendering.md)的全息影像会直接显示在用户眼睛的前方。 全息影像向您的世界添加灯光，这意味着您可以看到来自显示器的光线和来自您的周围世界的光线。 由于 HoloLens 使用添加灯光的加法显示，因此黑色颜色将呈现为透明。 

全息影像的外观和行为可能会非常不同。 有些是真实的、坚实的，而有些则是 cartoonish 和 ethereal。 您可以使用全息影像突出显示您的环境中的功能，或将其用作应用程序用户界面中的元素。

![手动操作全息图](images/hologram-hands-940px.jpg)

### <a name="sound"></a>声音

全息影像还可以生成[声音](../design/spatial-sound.md)，这似乎来自你的环境中的特定位置。 在 HoloLens 上，声音来自两个位于你的耳上的扬声器。 与全息显示器相同，扬声器是累加的，引入新声音，而不会阻止环境中的声音。

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>全息图可以放在世界上，也可以与你一起标记

当你有固定的 [空间来放置](../design/coordinate-systems.md) 全息图时，你可以在世界上准确地放置该位置。 在四处浏览时，全息图会显示在周围，就像物理对象一样。 如果使用 [空间锚点](../design/coordinate-systems.md#spatial-anchors) 固定对象，则系统甚至可以在以后回来时记住它的位置。

![在零售空间中使用 Microsoft Dynamics 365 布局的两个男人](images/HLS19_retailLayoutHologram_001-940px.jpg)

某些全息影像会按用户进行操作。 它们将基于用户进行定位。 您可以选择为您提供一个全息图，然后在到达另一个房间后将其放在墙壁上。

**最佳实践**

* 某些情况下，需要在整个体验中轻松发现和查看全息影像。 此类定位有两个高级方法。 让我们将它们称为 " **显示锁定** " 和 " **正文锁定**"。
   * **显示锁定** 的内容已锁定到显示设备。 由于多种原因，这种类型的内容有点棘手，其中包括 "clingyness" 非自然的 ""，这使得许多用户感到沮丧并希望 "将其关闭"。 一般而言，设计人员发现，更好的做法是避免显示锁定内容。
   * **正文锁定内容的** 包容性更多。 当您在三维空间中接入到用户的主体或注视着矢量时，会锁定正文。 许多经验都采用了一种正文锁定行为，其中全息图跟随用户的注视，这允许用户轮换其身体，而不会丢失全息影像。 合并延迟有助于使全息图移动更加自然。 例如，Windows 全息版 OS 的某些核心 UI 使用了一种外观上的外观锁定，用户将其看起来像是一种灵活的、弹性的延迟，同时用户会将其标头。
* 将全息图放置在舒适的观看距离上，通常会远离1-2 米。
* 如果元素必须在全息帧中连续，则允许元素偏移，或者考虑在用户更改其视图时将内容移至显示的一侧。 有关详细信息，请参阅 [billboarding and tag](../design/billboarding-and-tag-along.md) artilce。

**将全息影像置于最佳区域-介于 1.25 m 和 5 m 之间**

双米是最佳观看距离。 当你接近1米时，体验会开始下降。 在距离小于1米的位置上，定期移动的全息影像比静态全息影像更有可能出现问题。 如果内容太近，请考虑适当地剪辑或淡化内容，因此你不会将用户剪到令人不愉快的观看体验。

![从用户放置全息影像的最佳距离。](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>全息图与您和您的世界交互

全息影像不只是关于光线和声音;它们也是您世界的一个活动部分。 用手看一个全息影像和手势，然后就可以开始使用全息图。 发出一个语音命令，然后再进行回复。

![一组政府实用工作人员组，使用 Microsoft HoloLens 2 在风场开发项目上协作](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

全息影像可以在其他地方实现不可能的个人交互。 因为 HoloLens 知道了它在世界中的位置，所以全息人物可以直接查看并与你进行对话。

全息图还可以与你的环境交互。 例如，您可以将一个全息弹跳球置于一个表上方。 然后，通过 [点击](../design/gaze-and-commit.md#composite-gestures)，观看球弹跳，并在其到达表时发出声音。

全息影像还可以由真实的对象封闭像素。 例如，全息人物可能会走出大门的门和背面。

**用于集成全息影像和现实世界的使用技巧**

* 与 gravitational 规则相协调，可以更轻松地与和更可信相关。 例如：将一个全息狗置于 & 表上的花瓶，而不是让它们在空间中浮动。
* 许多设计人员发现，他们可以通过在可信的表面上创建 "负阴影" 来集成更多的全息影像。 为此，可在两个全息图的地面上创建软光亮，然后从发光中减去 "阴影"。 软发光与现实世界中的灯光相集成。 影子用于在环境中构建全息影像。

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a>全息图 <br>你可以梦想<br>
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

你正处于 [发现旅程](get-started-with-mr.md) ，并探讨了混合现实的基本知识。 从这里，你可以进入下一基本主题： 

> [!div class="nextstepaction"]
> [扩展设计过程](case-study-expanding-the-design-process-for-mixed-reality.md)