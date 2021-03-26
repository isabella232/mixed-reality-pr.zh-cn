---
title: Unity UWP 应用中的 UDP 数据包
description: 了解如何设置 Unity UWP 应用，以便通过安全网络收发 UDP 数据包。
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP，UWP，Unity，UDP 数据包，套接字，客户端服务器，终结点，网络，远程计算机，datagramsocket，示例，.net
ms.openlocfilehash: b38897f228a62abeb63b7e2ffc0f2a98a840b781
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550517"
---
# <a name="udp-packets-in-unity-uwp-apps"></a><span data-ttu-id="085d6-104">Unity UWP 应用中的 UDP 数据包</span><span class="sxs-lookup"><span data-stu-id="085d6-104">UDP packets in Unity UWP apps</span></span>

<span data-ttu-id="085d6-105">可以通过将通用 Windows 平台 (UWP) Unity 应用来接收 udp 套接字客户端和服务器的 UDP 包。</span><span class="sxs-lookup"><span data-stu-id="085d6-105">You can setup your Universal Windows Platform (UWP) Unity apps to receive UDP packets with the help of a UDP socket client and server.</span></span> <span data-ttu-id="085d6-106">UDP 套接字并不在两个终结点上保持连接，因此它们是远程计算机之间网络连接的快速而简单的解决方案。</span><span class="sxs-lookup"><span data-stu-id="085d6-106">UDP sockets don't maintain connection on both endpoints, so they're a fast and simple solution for networking between remote machines.</span></span> <span data-ttu-id="085d6-107">但是，你将负责检查数据包是否到达其目标，因为 UDP 套接字不会自动执行此操作。</span><span class="sxs-lookup"><span data-stu-id="085d6-107">However, you'll be responsible for checking if the packets get to their destination, as UDP sockets don't do that automatically.</span></span>

## <a name="setup"></a><span data-ttu-id="085d6-108">设置</span><span class="sxs-lookup"><span data-stu-id="085d6-108">Setup</span></span>

<span data-ttu-id="085d6-109">打开项目 HoloLens manifest.js文件，并确保已启用：</span><span class="sxs-lookup"><span data-stu-id="085d6-109">Open your projects HoloLens manifest.json file and make sure you've enabled:</span></span>
* <span data-ttu-id="085d6-110">**Internet (客户端 & 服务器)**</span><span class="sxs-lookup"><span data-stu-id="085d6-110">**Internet (Client & Server)**</span></span> 
* <span data-ttu-id="085d6-111">**(客户端 & 服务器) 的专用网络**。</span><span class="sxs-lookup"><span data-stu-id="085d6-111">**Private Networks (Client & Server)**.</span></span>

## <a name="build-your-socket-client-and-server"></a><span data-ttu-id="085d6-112">构建套接字客户端和服务器</span><span class="sxs-lookup"><span data-stu-id="085d6-112">Build your socket client and server</span></span> 

<span data-ttu-id="085d6-113">按照说明 [生成基本的 UDP 套接字客户端和服务器](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server)。</span><span class="sxs-lookup"><span data-stu-id="085d6-113">Follow the instructions for [building a basic UDP socket client and server](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span></span> <span data-ttu-id="085d6-114">你将使用 [DatagramSocket](/uwp/api/Windows.Networking.Sockets.DatagramSocket) 类通过 UDP 发送和接收数据，并形成回音客户端和服务器。</span><span class="sxs-lookup"><span data-stu-id="085d6-114">You'll be using the [DatagramSocket](/uwp/api/Windows.Networking.Sockets.DatagramSocket) class to send and receive data over UDP and form an echo client and server.</span></span> <span data-ttu-id="085d6-115">我们还建议通读本文中的其他资源部分，因为它们适用于更多的自定义和复杂的用例。</span><span class="sxs-lookup"><span data-stu-id="085d6-115">We also recommend reading through the other resource sections in this article, as they apply to more customized and complex use cases.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="085d6-116">如果在将 UDP 数据包从 PC 发送到 PC 时遇到问题，请检查你的网络是否允许这些操作。</span><span class="sxs-lookup"><span data-stu-id="085d6-116">If you're having trouble sending UDP packets from PC to PC, check that your network allows these operations.</span></span> <span data-ttu-id="085d6-117">如果您的网络以任何方式阻止 UDP 数据包，则您的 HoloLens 设备将无法侦听它们。</span><span class="sxs-lookup"><span data-stu-id="085d6-117">If your network is blocking the UDP packets in any way, your HoloLens device won't be able to listen for them.</span></span>

<span data-ttu-id="085d6-118">可从以下链接下载完整的 DatagramSocket UDP 示例应用：</span><span class="sxs-lookup"><span data-stu-id="085d6-118">You can download a complete DatagramSocket UDP sample app from the link below:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="085d6-119">安装工具</span><span class="sxs-lookup"><span data-stu-id="085d6-119">Install the tools</span></span>](/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a><span data-ttu-id="085d6-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="085d6-120">See also</span></span> 
* [<span data-ttu-id="085d6-121">带有共享全息影像和 Azure Blob 存储/UDP 多播的试验</span><span class="sxs-lookup"><span data-stu-id="085d6-121">Experiments with Shared Holograms and Azure Blob Storage/UDP Multicasting</span></span>](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)