---
title: Unity 播放模式
description: 在 Unity 编辑器中使用播放模式，无需部署应用即可在设备上预览所做的更改。
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，远程处理，全息远程处理，全息远程处理播放器，HoloLens，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity 播放模式
ms.openlocfilehash: 396e441903fe7b567c6329ca4d207ce893a07825
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010608"
---
# <a name="unity-play-mode"></a><span data-ttu-id="73b37-104">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="73b37-104">Unity Play Mode</span></span>

<span data-ttu-id="73b37-105">处理 Unity 项目的一种快速方法是使用 "播放模式"，该模式在计算机上的 Unity 编辑器中本地运行你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="73b37-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="73b37-106">Unity 使用全息远程处理提供一种在真实的 HoloLens 设备上快速预览内容的方式。</span><span class="sxs-lookup"><span data-stu-id="73b37-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="73b37-107">播放模式还可与附加到开发 PC 的 Windows Mixed Reality 耳机一起使用。</span><span class="sxs-lookup"><span data-stu-id="73b37-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="73b37-108">采用全息远程处理的 Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="73b37-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="73b37-109">通过全息远程处理，你可以在你的电脑上的应用程序中运行你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="73b37-109">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="73b37-110">注视、手势、语音和空间映射输入将从你的 HoloLens 发送到你的电脑。</span><span class="sxs-lookup"><span data-stu-id="73b37-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="73b37-111">然后，将呈现的帧发送回 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="73b37-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="73b37-112">这是一种快速调试应用程序的绝佳方式，无需生成和部署完整项目。</span><span class="sxs-lookup"><span data-stu-id="73b37-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="73b37-113">在 HoloLens 上，中转到 **Microsoft Store** 并安装 **[全息远程处理播放器](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。</span><span class="sxs-lookup"><span data-stu-id="73b37-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="73b37-114">在 HoloLens 上，启动 **全息远程处理播放器** 应用。</span><span class="sxs-lookup"><span data-stu-id="73b37-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="73b37-115">在 Unity 中，单击 " **窗口** " 菜单，展开 " **XR** " 子菜单，然后选择 " **全息模拟**"。</span><span class="sxs-lookup"><span data-stu-id="73b37-115">In Unity, go to the **Window** menu, expand the **XR** submenu, and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="73b37-116">将 **仿真模式** 设置为 **远程设备**。</span><span class="sxs-lookup"><span data-stu-id="73b37-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="73b37-117">对于 **远程计算机**，请输入 HOLOLENS 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="73b37-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="73b37-118">选择“连接”  。</span><span class="sxs-lookup"><span data-stu-id="73b37-118">Select **Connect**.</span></span> <span data-ttu-id="73b37-119">应会看到 **连接状态** 更改为 " **已连接** "，并且会在 HoloLens 中看到屏幕显示为空白。</span><span class="sxs-lookup"><span data-stu-id="73b37-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="73b37-120">选择 " **播放** " 按钮，开始播放模式并在 HoloLens 上体验应用。</span><span class="sxs-lookup"><span data-stu-id="73b37-120">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="73b37-121">全息远程处理需要快速的 PC 和 Wi-Fi 的连接。</span><span class="sxs-lookup"><span data-stu-id="73b37-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="73b37-122">可以在 [全息远程处理播放机](../platform-capabilities-and-apis/holographic-remoting-player.md) 文档中找到更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="73b37-122">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="73b37-123">为了获得最佳结果，请确保应用正确设置了 [焦点](focus-point-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="73b37-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="73b37-124">这有助于全息远程处理最好地使场景适应无线连接的延迟。</span><span class="sxs-lookup"><span data-stu-id="73b37-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="73b37-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73b37-125">See Also</span></span>
* [<span data-ttu-id="73b37-126">全息远程播放器</span><span class="sxs-lookup"><span data-stu-id="73b37-126">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
