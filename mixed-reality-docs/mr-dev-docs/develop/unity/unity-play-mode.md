---
title: 使用全息远程处理预览你的工作
description: 在不部署应用的情况下，在播放模式下使用全息远程处理在设备上预览应用程序更改。
author: keveleigh
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: Unity，远程处理，全息远程处理，全息远程处理播放器，HoloLens，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity 播放模式
ms.openlocfilehash: 0c71791c80a5e84ee48241baa756064a800e5a41
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757209"
---
# <a name="preview-your-work-with-holographic-remoting"></a>使用全息远程处理预览你的工作

可以使用全息远程处理实时将全息内容流式传输到 HoloLens 2。 这是一种快速调试应用程序的绝佳方式，无需生成和部署完整项目。 

处理 Unity 项目的一种快速方法是使用 "播放模式"，该模式在计算机上的 Unity 编辑器中本地运行你的应用程序。 Unity 使用全息远程处理提供一种在真实 HoloLens 设备上快速预览内容的方式。 播放模式还可与附加到开发 PC 的 Windows Mixed Reality 耳机一起使用。

## <a name="holographic-remoting-setup"></a>全息远程处理安装

1. 首先，需要从 HoloLens 2 上的 Microsoft Store[安装全息远程处理播放器应用程序](https://www.microsoft.com/store/productId/9NBLGGH4SV40)
2. 在 HoloLens 2 上运行全息远程处理播放机应用程序，你将看到要连接到的版本号和 IP 地址
    * 你需要使用版本2.4 或更高版本才能使用 OpenXR 插件

    ![在 HoloLens 中运行的全息远程处理播放机的屏幕截图](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a>采用全息远程处理的 Unity 播放模式

通过全息远程处理，你可以在你的计算机上的应用程序中运行应用程序时，在 HoloLens 上体验你的应用程序。 注视、手势、语音和空间映射输入会从您的 HoloLens 发送到您的 PC。 然后，将呈现的帧发送回 HoloLens。 这是一种快速调试应用程序的绝佳方式，无需生成和部署完整项目。

[!INCLUDE[](includes/unity-play-mode.md)]

全息远程处理需要快速的 PC 和 Wi-Fi 的连接。 可以在 [全息远程处理播放机](../platform-capabilities-and-apis/holographic-remoting-player.md) 文档中找到更多详细信息。

为了获得最佳结果，请确保应用正确设置了 [焦点](focus-point-in-unity.md)。 这有助于全息远程处理最好地使场景适应无线连接的延迟。

## <a name="see-also"></a>另请参阅

* [全息远程播放器](../platform-capabilities-and-apis/holographic-remoting-player.md)
