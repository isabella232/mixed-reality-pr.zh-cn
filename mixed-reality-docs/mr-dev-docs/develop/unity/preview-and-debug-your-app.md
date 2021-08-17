---
title: 使用全息远程处理和播放模式预览和调试应用
description: 使用全息远程处理和播放模式预览和调试应用
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr， unity， hololens， hololens 2， 混合现实， MRTK， 混合现实 Toolkit， 增强现实， 虚拟现实， 混合现实头戴显示设备， 学习， 教程， 入门， 全息远程处理， 桌面， 预览， 调试
ms.openlocfilehash: fe15d55037f09c47fe1e8a1dd996d0c69480f7b2
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203832"
---
# <a name="preview-and-debug-your-app-using-holographic-remoting-and-play-mode"></a>使用全息远程处理和播放模式预览和调试应用

本文介绍全息远程处理的以下用例： 

- **想要在开发过程中** 预览和调试应用：可以在电脑的 Unity 编辑器中以播放模式在本地运行应用，将体验流式传输HoloLens。 这提供了一种在不生成和部署完整项目的情况下快速调试应用的方法。 我们将这种类型的应用称为全息 _远程处理播放模式预览应用_。 来自虚拟HoloLens（凝视、手势、语音和空间映射）的输入将发送到电脑，其中的内容在虚拟沉浸式视图中呈现。 然后，将呈现的帧发送到HoloLens。 

若要详细了解全息远程处理，请参阅 [全息远程处理概述](../platform-capabilities-and-apis/holographic-remoting-overview.md)

请注意，如果希望电脑的资源为应用提供电源，而不是依赖于[](use-pc-resources.md)板载资源，HoloLens全息远程处理。

## <a name="set-up-holographic-remoting"></a>设置全息远程处理

若要使用全息远程处理，需要从应用程序上的 Microsoft Store[](../platform-capabilities-and-apis/holographic-remoting-player.md)安装全息远程播放器HoloLens。 如下所述，下载并运行应用后，你将看到要连接到的版本号和 IP 地址。 **需要 v2.4 或更高版本才能使用 OpenXR 插件**。

全息远程处理需要快速的电脑和Wi-Fi连接。 可以在上面链接的全息远程处理播放器一文找到更多详细信息。

![在远程处理中运行的全息远程处理播放器的HoloLens](images/openxr-features-img-01.png)

[!INCLUDE[](includes/unity-play-mode.md)]

## <a name="see-also"></a>另请参阅
* [全息远程播放器](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [教程：电脑全息远程处理入门](tutorials/mr-learning-pc-holographic-remoting-01.md)
* [教程：创建全息远程处理电脑应用程序](tutorials/mr-learning-pc-holographic-remoting-02.md)
