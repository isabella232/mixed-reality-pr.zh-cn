---
title: 应用视图
description: Windows Mixed Reality 应用中的两种视图是沉浸式视图和2D 视图。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 沉浸式视图，2D 视图，石板，应用
ms.openlocfilehash: e625eca3adb7cd4a9dcd1f971917f008d5daa7d2
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677423"
---
# <a name="app-views"></a>应用视图

Windows 应用可以包含两种类型的视图： **沉浸式视图** 和 **2d 视图** 。 应用可以在其各种沉浸式视图与2D 视图之间进行切换，并将其2D 视图显示在监视器上作为一个窗口，或显示为一个石板。 至少具有一个沉浸式视图的应用会分类为 **混合现实应用** 。 永不具有沉浸式视图的应用为 **2d 应用** 。

## <a name="immersive-views"></a>沉浸式视图

借助沉浸式视图，你的应用可以创建你周围世界的全息影像，或让用户沉浸在虚拟环境中。 如果应用是在沉浸式视图中绘制的，则不会在同一时间同时绘制 &mdash; 多个应用的全息影像。 通过持续调整 [应用程序呈现](../develop/platform-capabilities-and-apis/rendering.md) 其场景的视角来匹配用户的头运动，你的应用可以呈现固定在现实世界的固定点的 [全球锁定](coordinate-systems.md) 全息影像，也可以呈现一个虚拟世界，使其在用户移动时保持其位置。

![在沉浸式视图中，可以在世界各地放置全息影像。](images/designoverview-940px.jpg)<br>
*在沉浸式视图中，可以在世界各地放置全息影像*

在 [HoloLens](https://docs.microsoft.com/hololens/hololens1-hardware)上，你的应用程序会在用户的真实环境上呈现其全息影像。 在 [Windows Mixed Reality 沉浸式耳机](../discover/immersive-headset-hardware-details.md)上，用户看不到现实世界，因此你的应用程序必须呈现用户将看到的所有内容。

[Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) (包括在环境中放置的 "开始" 菜单和全息影像) 在沉浸式视图中也不会呈现。 在 HoloLens 上，显示沉浸式视图时发生的任何系统通知都将被 Cortana 呼叫时中继，用户可以使用语音输入进行响应。

在沉浸式视图中，应用还负责处理所有输入。 Windows Mixed Reality 中的输入是由 [注视](gaze-and-commit.md)， [手势](gaze-and-commit.md#composite-gestures) (仅限) 、 [语音](voice-input.md) 和 [运动控制器](motion-controllers.md) (沉浸式) 耳机。

## <a name="2d-views"></a>2D 视图

![围绕 Windows Mixed Reality 主页布局的多个2D 视图](images/teleportation-940px.png)<br>
*围绕 Windows Mixed Reality 主页放置了2D 视图的多个应用*

带有2D 视图的应用程序将出现在 [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) (中，有时称为 "shell" ) 作为虚拟石板，并与应用程序启动器以及用户在其世界中放置的其他全息影像一起呈现。 用户可以调整此石板，使其移动和缩放，但不考虑其大小。 如果您的应用程序的第一个视图是2D 视图，则您的2D 内容将填充用于启动该应用程序的同一个石板。

在台式机耳机上，你可以在现在的桌面监视器上运行通用 Windows 平台 (UWP) 应用。 这些应用现在已经呈现了2D 视图，并且其内容将在启动时自动显示在用户世界的某个石板上。 2D UWP 应用可以面向 **Windows 通用** 设备家族，使其在桌面耳机和 HoloLens 上都以清单的形式运行。

2D 视图的一项关键用途是显示可使用系统键盘的文本输入窗体。 由于 shell 无法在沉浸式视图顶部呈现，因此应用必须切换到2D 视图以显示系统键盘。 需要接受文本输入的应用可以使用文本框切换到2D 视图。 当该文本框有焦点时，系统将显示系统键盘，允许用户输入文本。

请注意，在台式计算机上，应用可以在桌面监视器和连接的耳机上都有2D 视图。 例如，你可以使用其主2D 视图在桌面监视器上浏览边缘，以查找360度视频。 播放视频后，边缘将在耳机内启动辅助沉浸式视图以显示沉浸式视频内容。

## <a name="see-also"></a>请参阅

* [应用模型](app-model.md)
* [更新混合现实的 2D UWP 应用](../develop/porting-apps/building-2d-apps.md)
* [获取 HolographicSpace](../develop/native/getting-a-holographicspace.md)
* [导航 Windows Mixed Reality 主页](../discover/navigating-the-windows-mixed-reality-home.md)
* [混合现实应用的类型](types-of-mixed-reality-apps.md)
