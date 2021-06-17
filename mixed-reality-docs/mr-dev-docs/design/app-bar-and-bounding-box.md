---
title: 边界框和应用栏
description: 应用栏是一个对象级菜单，其中包含一系列按钮，这些按钮显示在全息影像边界的底部边缘。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality、应用栏、边界框、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、HoloLens、MRTK、混合现实工具包
ms.openlocfilehash: 5c437b303ec5462179a1ddf43687aa1653419b08
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110098"
---
# <a name="bounding-box-and-app-bar"></a>边界框和应用栏
![边界是混合现实中对象操作的标准接口。](images/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>什么是边界框？

边界是混合现实中对象操作的标准接口。 此功能为用户提供一个视觉提示，指示对象当前可调整。 在HoloLens 2，边界框适用于直接手动操作，并响应用户手指的邻近性。 它显示视觉反馈，帮助用户感知与对象的距离。

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>缩放对象<br>
        边界框的角告知用户对象可以缩放。 句柄遵循广泛理解的调整缩放模式。 此视觉提示向用户显示对象的总区域 ， 即使它在调整模式之外不可见。 如果没有此功能，与另一个对象或图面对齐的对象的行为可能看起来就像周围存在不应存在的空间一样。<br>
        <br>
        *视频循环：通过边界框缩放对象*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![通过边界框缩放对象的 HoloLens 视图](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>旋转对象<br>
        边界框边缘上的垂直矩形设计是旋转指示器。 这样，用户可以更精细地调整其放置的全息影像。 它们不仅可以调整和缩放，现在还可以旋转。<br>
        <br>
        *视频循环：通过边界框旋转对象*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![通过边界框旋转对象的 HoloLens 视图](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>有关手动邻近感应的视觉HoloLens 2<br>
        在HoloLens 2，有一个额外的视觉提示，可帮助用户感知深度。 当手指靠近对象时，可显示一个靠近其手指的环并缩小。 当达到按下状态时，环最终会聚合为点。 此视觉视觉视觉元素可帮助用户了解它们与对象距离有多远。<br>
        <br>
        *视频循环：基于边界框邻近性进行视觉反馈的示例*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![有关手部邻近感应的视觉反馈](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**有关 Unity 应用开发，请参阅混合现实 [工具包 Unity 中的边界框。](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**

<br>

---

## <a name="what-is-the-app-bar"></a>什么是应用栏？

应用栏是一个对象级菜单，其中包含一系列显示在全息影像边界下边缘的按钮。 此模式通常用于让用户删除和调整全息影像。 应用栏主要用于管理用户环境中放置的对象。 与边界框一起，用户可以完全控制混合现实中对象的面向位置和方向。

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>应用栏跟随用户<br>
        由于此模式与被世界锁定的对象一起使用，因此，在用户围绕对象移动时，应用栏将始终显示在离用户最近的对象端。 虽然从技术上来说不是广告，但此功能实际上实现了相同的结果。 防止用户的位置遮挡或阻止功能，否则可从其环境中的不同位置获得这些功能。 <br>
        <br>
        *视频循环：遍历全息影像，应用栏如下所示*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![在全息影像周围移动。 应用栏如下所示。](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>适用于 Unity 的混合现实工具包 (MRTK) 边界框
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 为边界框和应用栏提供脚本和预制。 可以通过将 BoundingBox.cs 脚本分配给任何对象来添加边界框。

* [MRTK - 边界框](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


<br>

---


## <a name="see-also"></a>另请参阅

* [光标](cursors.md)
* [手部射线](point-and-commit.md)
* [Button](button.md)
* [可交互对象](interactable-object.md)
* [边界框和应用栏](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [手动菜单](hand-menu.md)
* [追踪菜单](near-menu.md)
* [对象集合](object-collection.md)
* [语音命令](voice-input.md)
* [键盘](keyboard.md)
* [工具提示](tooltip.md)
* [平板](slate.md)
* [滑块](slider.md)
* [着色器](shader.md)
* [公告和尾随](billboarding-and-tag-along.md)
* [显示进度](progress.md)
* [表面磁吸](surface-magnetism.md)