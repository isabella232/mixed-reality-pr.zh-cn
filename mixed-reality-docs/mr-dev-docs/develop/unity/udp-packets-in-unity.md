---
title: Unity UWP 应用中的 UDP 数据包
description: 了解如何设置 Unity UWP 应用，以通过安全网络发送和接收 UDP 数据包。
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP， UWP， Unity， UDP 数据包， 套接字， 客户端服务器， 终结点， 网络， 远程计算机， 数据报ocket， 示例， .net
ms.openlocfilehash: a24498384ccb2018f62f00523bf33764d2ef7c019dec0cfd8fc70d86b55a81bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192553"
---
# <a name="udp-packets-in-unity-uwp-apps"></a>Unity UWP 应用中的 UDP 数据包

可以在 Unity 应用中设置通用 Windows 平台 (UWP) ，以在 UDP 套接字客户端和服务器的帮助下接收 UDP 数据包。 UDP 套接字不会在两个终结点上保持连接，因此它们是远程计算机之间网络的快速简单解决方案。 但是，你将负责检查数据包是否到达其目标，因为 UDP 套接字不会自动这样做。

## <a name="setup"></a>设置

打开项目HoloLens manifest.js文件，并确保已启用：
* **Internet (客户端&服务器)** 
* **专用网络 (客户端&服务器) 。**

## <a name="build-your-socket-client-and-server"></a>生成套接字客户端和服务器 

按照有关生成 [基本 UDP 套接字客户端和服务器 的说明进行操作](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server)。 你将使用 [DatagramSocket](/uwp/api/Windows.Networking.Sockets.DatagramSocket) 类通过 UDP 发送和接收数据，并形成回显客户端和服务器。 我们还建议通读本文中的其他资源部分，因为它们适用于更自定义且更复杂的用例。 

> [!IMPORTANT]
> 如果在将 UDP 数据包从电脑发送到电脑时遇到问题，请检查网络是否允许这些操作。 如果网络以任何方式阻止 UDP 数据包，HoloLens设备将无法侦听这些数据包。

可以从以下链接下载完整的 DatagramSocket UDP 示例应用：

> [!div class="nextstepaction"]
> [安装工具](/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a>另请参阅 
* [使用共享数据库全息影像 Azure Blob 存储/UDP 多播的试验](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)