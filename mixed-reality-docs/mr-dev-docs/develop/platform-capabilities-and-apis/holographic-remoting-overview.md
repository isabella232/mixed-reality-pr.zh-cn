---
title: 全息远程处理概述
description: 了解什么是全息远程处理，以及它可以如何受益于你的开发过程。
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实 Toolkit，增加现实，虚拟现实，混合现实耳机，学习，教程，入门，全息远程处理，桌面，预览
ms.openlocfilehash: 6eb3b9e9fe8811ab4666ef1beda0e48668bedbe6
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757384"
---
# <a name="holographic-remoting-overview"></a>全息远程处理概述

当你向电脑应用或游戏添加对全息着色的支持时，它允许应用实时将全息内容流式传输到你的 HoloLens 2。 这是一种快速调试应用程序的绝佳方式，无需生成和部署完整项目。 "注视"、"手势"、"声音" 和 "空间映射" 输入将从 HoloLens 2 发送到 pc，使用电脑的更大系统资源在虚拟沉浸式视图中呈现内容，然后将呈现的帧发送回 HoloLens 2。 全息远程处理也可用于 Windows Mixed Reality 沉浸式耳机。

通过 NuGet 包将全息远程处理添加到桌面或 UWP 应用，并使用标准 wi-fi 建立连接。 需要其他代码来处理连接并在沉浸式视图中呈现。 典型的远程处理连接的延迟最低为50毫秒。 你的设备将使用可实时报告延迟的 "播放机" 应用显示流内容。

如果你是一名 Unity 开发人员，还可以通过在 Unity 编辑器中以播放模式运行应用来使用全息远程处理。

## <a name="see-also"></a>另请参阅
* [全息远程播放器](holographic-remoting-player.md)
* [使用 Windows Mixed Reality api 编写全息远程处理远程应用](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR Api 编写全息远程处理远程应用](holographic-remoting-create-remote-openxr.md)
* [教程： PC 全息远程处理入门](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [教程：创建全息远程电脑应用程序](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
