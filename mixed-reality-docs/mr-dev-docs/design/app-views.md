---
title: 应用视图
description: 了解如何在 Windows Mixed Reality 应用程序中使用这两种视图：沉浸式视图和2d 视图。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 沉浸式视图，2d 视图，石板，应用，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实 Toolkit
ms.openlocfilehash: 1f779749938bfc8893f0e1f1f60c97549d30a24075b5b0926af61e2f88625b9c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191501"
---
# <a name="app-views"></a>应用视图

Windows 应用可以包含两种类型的视图：**沉浸式视图** 和 **2d 视图**。 应用可以在其各种沉浸和2D 视图之间切换，并将其2D 视图显示在监视器上作为一个窗口，或显示为一个石板。 至少具有一个沉浸式视图的应用会分类为 **混合现实应用**。 没有沉浸式视图的应用就是 2D 应用。

## <a name="immersive-views"></a>沉浸式视图

借助沉浸式视图，你的应用可以创建你周围世界的全息影像，或让用户沉浸在虚拟环境中。 当应用程序在沉浸式视图中绘制时，不会同时绘制 &mdash; 多个应用程序中的全息影像。 通过持续调整 [应用程序呈现](../develop/platform-capabilities-and-apis/rendering.md) 其场景的视角来匹配用户的头运动，你的应用可以呈现 [全球锁定](coordinate-systems.md) 的全息影像。 全球锁定的全息影像停留在现实世界中的一个固定点，或者可以呈现一个虚拟世界，在用户移动时保存其位置。

![在沉浸式视图中，可以在世界各地放置全息影像。](images/designoverview-940px.jpg)<br>
*在沉浸式视图中，可以在世界各地放置全息影像*

在[HoloLens](/hololens/hololens1-hardware)上，应用程序会在用户的实际周围环境上呈现其全息影像。 在[Windows Mixed Reality 沉浸式耳机](../discover/immersive-headset-hardware-details.md)上，用户看不到现实世界，因此你的应用程序必须呈现用户将看到的所有内容。

[Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) (包括你在环境中放置的 "开始"菜单和全息影像) 在沉浸式视图中不会呈现。 在 HoloLens 上，Cortana 中继在显示沉浸式视图时发生的任何系统通知，用户可以使用语音输入来响应。

在沉浸式视图中，应用还负责处理所有输入。 Windows Mixed Reality 中的输入由[注视](gaze-and-commit.md)，[手势](gaze-and-commit.md#composite-gestures) (仅 HoloLens) 、[语音和[运动控制器](motion-controllers.md) (仅) 沉浸式耳机。

## <a name="2d-views"></a>2D 视图

![围绕 Windows Mixed Reality home 确定多个2d 视图](images/teleportation-940px.png)<br>
*围绕 Windows Mixed Reality home 提供2d 视图的多个应用*

带有2d 视图的应用程序将出现在[Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) (有时称为 "shell" ) 作为虚拟石板，并与应用程序启动器以及用户在其世界中放置的其他全息影像一起呈现。 用户可以调整此石板，使其移动和缩放，但其大小仍保持固定分辨率。 如果您的应用程序的第一个视图是2D 视图，则您的2D 内容将填充用于启动该应用程序的同一个石板。

在台式机耳机上，你可以在现在的桌面监视器上运行通用 Windows 平台 (UWP) 应用。 这些应用现在已经呈现了2D 视图，并且其内容将在启动时自动显示在用户世界的某个石板上。 2D UWP 应用可以针对 **Windows。通用** 设备家族运行在台式机耳机上，在 HoloLens 上运行为清单。

2D 视图的一项关键用途是显示使用系统键盘的文本输入窗体。 由于 shell 无法在沉浸式视图顶部呈现，因此应用程序必须切换到2D 视图以显示系统键盘。 需要接受文本输入的应用需要切换到带有文本框的2D 视图。 当该文本框有焦点时，系统将显示系统键盘，允许用户输入文本。

应用可在桌面显示器和台式计算机上的已连接耳机上具有2D 视图。 例如，你可以使用其主2D 视图在桌面监视器上浏览边缘，以查找360度视频。 播放视频后，边缘将在耳机内启动辅助沉浸式视图以显示沉浸式视频内容。

## <a name="see-also"></a>另请参阅

* [应用模型](app-model.md)
* [更新混合现实的 2D UWP 应用](../develop/porting-apps/building-2d-apps.md)
* [获取 HolographicSpace](../develop/native/getting-a-holographicspace.md)
* [导航 Windows Mixed Reality 主页](../discover/navigating-the-windows-mixed-reality-home.md)
* [混合现实应用的类型](types-of-mixed-reality-apps.md)