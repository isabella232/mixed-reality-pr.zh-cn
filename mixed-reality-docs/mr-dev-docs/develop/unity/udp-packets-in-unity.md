---
title: Unity UWP 应用中的 UDP 数据包
description: 了解如何设置 Unity UWP 应用，以便通过安全网络收发 UDP 数据包。
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP，UWP，Unity，UDP 数据包，套接字，客户端服务器，终结点，网络，远程计算机，datagramsocket，示例，.net
ms.openlocfilehash: e4fbdc12a1f7fbca44e14f6ace89ef791a09608f
ms.sourcegitcommit: 8647702638f7600c51df1d89d76c761b52bdf0d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2021
ms.locfileid: "99566972"
---
# <a name="udp-packets-in-unity-uwp-apps"></a>Unity UWP 应用中的 UDP 数据包

可以通过将通用 Windows 平台 (UWP) Unity 应用来接收 udp 套接字客户端和服务器的 UDP 包。 UDP 套接字并不在两个终结点上保持连接，因此它们是远程计算机之间网络连接的快速而简单的解决方案。 但是，你将负责检查数据包是否到达其目标，因为 UDP 套接字不会自动执行此操作。

## <a name="setup"></a>设置

打开项目 HoloLens manifest.js文件，并确保已启用：
* **Internet (客户端 & 服务器)** 
* **(客户端 & 服务器) 的专用网络**。

## <a name="build-your-socket-client-and-server"></a>构建套接字客户端和服务器 

按照说明 [生成基本的 UDP 套接字客户端和服务器](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server)。 你将使用 [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) 类通过 UDP 发送和接收数据，并形成回音客户端和服务器。 我们还建议通读本文中的其他资源部分，因为它们适用于更多的自定义和复杂的用例。 

> [!IMPORTANT]
> 如果在将 UDP 数据包从 PC 发送到 PC 时遇到问题，请检查你的网络是否允许这些操作。 如果您的网络以任何方式阻止 UDP 数据包，则您的 HoloLens 设备将无法侦听它们。

可从以下链接下载完整的 DatagramSocket UDP 示例应用：

> [!div class="nextstepaction"]
> [安装工具](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a>另请参阅 
* [带有共享全息影像和 Azure Blob 存储/UDP 多播的试验](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)