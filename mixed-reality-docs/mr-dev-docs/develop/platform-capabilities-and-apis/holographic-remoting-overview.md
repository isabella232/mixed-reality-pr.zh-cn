---
title: 全息远程处理概述
description: 了解什么是全息远程处理，以及它可以如何受益于你的开发过程。
author: hferrone
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实 Toolkit，增加现实，虚拟现实，混合现实耳机，学习，教程，入门，全息远程处理，桌面，预览
ms.openlocfilehash: 52b69f942797b1f0a6a9bcc5276a49d4d2cebba5
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184598"
---
# <a name="holographic-remoting-overview"></a>全息远程处理概述

可以使用全息远程处理实时将全息内容流式传输到 HoloLens。 这有两个主要用途，这一点非常重要：

1.  (Unity 或 Unreal) ：**你希望在开发过程中预览和调试应用**：你可以在计算机上以播放模式在 Unity 编辑器中本地运行你的应用，并将体验流式传输到你的 HoloLens。 这提供了一种快速调试应用的方法，无需生成和部署完整项目。 我们将此类应用程序称为 _全息远程处理播放模式预览应用程序_。

    - [了解有关在 Unity 中预览和调试应用的详细信息](../unity/preview-and-debug-your-app.md)

    - [详细了解如何在 Unreal 中预览和调试应用程序](../unreal/unreal-streaming.md)

1.  (Unity、Unreal 或 c + +) ：**希望电脑的资源可以为应用程序提供支持，而不是依赖于 HoloLens 的板资源**：可以创建和构建包含全息远程处理功能的应用程序。 用户遇到 HoloLens 上的应用程序，但该应用程序实际在电脑上运行，这使它能够利用电脑更强大的资源。 如果你的应用程序具有高分辨率资产或型号，并且你不希望帧速率受到影响，这会特别有用。 我们将此类应用程序称为 _全息远程处理远程应用_。

    - [了解有关在 Unity 中使用 PC 资源的详细信息](../unity/use-pc-resources.md)

    - [详细了解如何在 Unreal 中使用电脑资源](../unreal/unreal-streaming.md)

    - [使用 (c + + Windows Mixed Reality api 编写全息远程处理远程应用) ](holographic-remoting-create-remote-wmr.md)

    - [使用 OpenXR Api 编写全息远程处理远程应用 (c + +) ](holographic-remoting-create-remote-openxr.md)

在这两种情况下，来自 HoloLens 的输入（"注视"、"手势"、"语音" 和 "空间" 映射）都将发送到 PC，内容呈现在虚拟沉浸式视图中，然后将呈现的帧发送到 HoloLens。 

## <a name="see-also"></a>另请参阅

* [全息远程播放器](holographic-remoting-player.md)
* [教程： PC 全息远程处理入门](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [教程：创建全息远程电脑应用程序](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
