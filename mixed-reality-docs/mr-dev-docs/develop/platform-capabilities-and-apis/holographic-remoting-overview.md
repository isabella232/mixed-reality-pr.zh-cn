---
title: 全息远程处理概述
description: 了解什么是全息远程处理，以及它如何为开发过程带来好处。
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr， unity， hololens， hololens 2， 混合现实， MRTK， 混合现实 Toolkit， 增强现实， 虚拟现实， 混合现实头戴显示设备， 学习， 教程， 入门， 全息远程处理， 桌面， 预览
ms.openlocfilehash: 1b20590429b7df209e805ed8e94de5a6010bdbb609edc10fc5854cd4df86f64c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217113"
---
# <a name="holographic-remoting-overview"></a>全息远程处理概述

将全息渲染支持添加到电脑应用或游戏时，该应用可以将全息内容实时流式HoloLens 2流式传输。 这是在不生成和部署完整项目的情况下快速调试应用的一种好方法。 凝视、手势、语音和空间映射输入从 HoloLens 2 发送到电脑，内容使用电脑的更大系统资源在虚拟沉浸式视图中呈现，然后呈现的帧将发送回 HoloLens 2。 全息远程处理还可用于Windows Mixed Reality头戴显示设备。

通过应用程序包将全息远程处理添加到桌面或 UWP NuGet，然后使用标准 Wi-Fi 建立连接。 需要其他代码来处理连接，并呈现在沉浸式视图中。 典型的远程处理连接延迟最低为 50 毫秒。 设备使用可实时报告延迟的"播放器"应用显示流式传输的内容。

如果你是 Unity 开发人员，还可以在 Play 模式下的 Unity 编辑器中运行应用，以使用全息远程处理。

## <a name="see-also"></a>另请参阅
* [全息远程播放器](holographic-remoting-player.md)
* [使用远程 API 编写全息远程Windows Mixed Reality应用](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR API 编写全息远程处理远程应用](holographic-remoting-create-remote-openxr.md)
* [教程：电脑全息远程处理入门](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [教程：创建全息远程处理电脑应用程序](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
