---
title: Unity 播放模式
description: 了解如何在 Unity 编辑器中使用播放模式在不部署应用的情况下预览设备上的应用程序更改。
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity，远程处理，全息远程处理，全息远程处理播放器，HoloLens，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity 播放模式
ms.openlocfilehash: b998233fda34beee0c98795a1efa2c86a53541ba
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392285"
---
# <a name="unity-play-mode"></a><span data-ttu-id="7dd7a-104">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="7dd7a-104">Unity Play Mode</span></span>

<span data-ttu-id="7dd7a-105">处理 Unity 项目的一种快速方法是使用 "播放模式"，该模式在计算机上的 Unity 编辑器中本地运行你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="7dd7a-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="7dd7a-106">Unity 使用全息远程处理提供一种在真实的 HoloLens 设备上快速预览内容的方式。</span><span class="sxs-lookup"><span data-stu-id="7dd7a-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="7dd7a-107">播放模式还可与附加到开发 PC 的 Windows Mixed Reality 耳机一起使用。</span><span class="sxs-lookup"><span data-stu-id="7dd7a-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="7dd7a-108">全息远程处理安装</span><span class="sxs-lookup"><span data-stu-id="7dd7a-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="7dd7a-109">首先，需要从 HoloLens 2 上的 Microsoft Store[安装全息远程处理播放器应用程序](https://www.microsoft.com/store/productId/9NBLGGH4SV40)</span><span class="sxs-lookup"><span data-stu-id="7dd7a-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="7dd7a-110">在 HoloLens 2 上运行全息远程处理播放器应用程序，你将看到要连接到的版本号和 IP 地址</span><span class="sxs-lookup"><span data-stu-id="7dd7a-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="7dd7a-111">你需要使用版本2.4 或更高版本才能使用 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="7dd7a-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens 中运行的全息远程处理播放机的屏幕截图](images/openxr-features-img-01.png)

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="7dd7a-113">采用全息远程处理的 Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="7dd7a-113">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="7dd7a-114">通过全息远程处理，你可以在你的电脑上的应用程序中运行你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="7dd7a-114">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="7dd7a-115">注视、手势、语音和空间映射输入将从你的 HoloLens 发送到你的电脑。</span><span class="sxs-lookup"><span data-stu-id="7dd7a-115">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="7dd7a-116">然后，将呈现的帧发送回 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="7dd7a-116">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="7dd7a-117">这是一种快速调试应用程序的绝佳方式，无需生成和部署完整项目。</span><span class="sxs-lookup"><span data-stu-id="7dd7a-117">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="7dd7a-118">全息远程处理需要快速的 PC 和 Wi-Fi 的连接。</span><span class="sxs-lookup"><span data-stu-id="7dd7a-118">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="7dd7a-119">可以在 [全息远程处理播放机](../platform-capabilities-and-apis/holographic-remoting-player.md) 文档中找到更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="7dd7a-119">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="7dd7a-120">为了获得最佳结果，请确保应用正确设置了 [焦点](focus-point-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="7dd7a-120">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="7dd7a-121">这有助于全息远程处理最好地使场景适应无线连接的延迟。</span><span class="sxs-lookup"><span data-stu-id="7dd7a-121">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="7dd7a-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7dd7a-122">See Also</span></span>

* [<span data-ttu-id="7dd7a-123">全息远程播放器</span><span class="sxs-lookup"><span data-stu-id="7dd7a-123">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
