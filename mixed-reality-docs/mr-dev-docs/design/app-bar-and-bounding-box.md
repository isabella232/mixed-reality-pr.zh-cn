---
title: 边界框和应用栏
description: 应用栏是一个对象级菜单，其中包含一系列按钮，它们显示在全息图边界的下边缘。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality，应用程序栏，边界箱，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包
ms.openlocfilehash: 0ccec5240854de9a7db6a79d5b90b97f1e6b81de
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299902"
---
# <a name="bounding-box-and-app-bar"></a>边界框和应用栏
!["边界" 是用于在混合现实中进行对象操作的标准接口。](images/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>什么是边界框？

"边界" 是用于在混合现实中进行对象操作的标准接口。 此功能向用户提供视觉提示，指出当前可以调整对象。 在 HoloLens 2 上，边界框适用于直接操作，并响应用户的 finger's 邻近性。 它显示了视觉反馈，可帮助用户感知与对象的距离。

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>缩放对象<br>
        边界框的角告诉用户该对象可以缩放。 句柄遵循用于调整刻度的广泛理解的模式。 此视觉提示向用户显示对象的总区域–即使它在调整模式外不可见。 如果没有此功能，则与另一个对象或表面对齐的对象可能看起来像是它不应存在的空间。<br>
        <br>
        *视频循环：通过边界框缩放对象*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens 通过边界框缩放对象的观点](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>旋转对象<br>
        边界框边缘的垂直矩形实用是旋转指示器。 这样，用户就可以更好地调整其放置的全息影像。 它们不仅可以进行调整和缩放，还可以进行旋转。<br>
        <br>
        *视频循环：通过边界框旋转对象*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens 通过边界框旋转对象的观点](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>HoloLens 2 上的现有视觉对象反馈<br>
        在 HoloLens 2 上，有一个额外的视觉提示，可帮助用户了解深度。 当手指更接近对象时，其手指附近的圆圈会显示并缩小。 当达到按下状态时，环最终汇聚为一个点。 此视觉对象 affordance 可帮助用户了解其在对象中的距离。<br>
        <br>
        *视频循环：基于与边界框的邻近的视觉反馈示例*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![视觉对象反馈](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**对于 Unity 应用开发，请参阅 [混合现实工具包中的边界框-Unity。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**

<br>

---

## <a name="what-is-the-app-bar"></a>什么是应用栏？

应用栏是一个对象级菜单，其中包含一系列在全息图边界的下边缘上显示的按钮。 此模式通常用于允许用户删除和调整全息影像。 应用栏的设计主要是在用户的环境中管理已放置对象的方式。 与边界框结合使用，用户可以完全控制对象在混合现实中的位置和方式。

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>应用栏追随用户<br>
        由于此模式与世界锁定的对象一起使用，因此当用户在对象周围移动时，应用栏将始终显示在最靠近用户的对象端。 虽然在技术上并不 billboarding，但此功能有效实现了相同的结果。 防止用户遮蔽或阻止在其环境中的其他位置可用的功能。 <br>
        <br>
        *视频循环：浏览全息图，应用栏跟随*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![浏览全息图。 应用栏如下所示。](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>MRTK (混合现实工具包) 适用于 Unity 的边界框
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 为边界框和应用栏提供脚本和 prototyping。 可以通过将 BoundingBox 脚本分配到任何对象来添加边界框。

* [MRTK-边界框](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


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
