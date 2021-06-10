---
title: Unity 播放模式
description: 了解如何在 Unity 编辑器中使用播放模式在设备上预览应用程序更改，而无需部署应用。
author: keveleigh
ms.author: kurtie
ms.date: 05/21/2021
ms.topic: article
keywords: Unity， 远程处理， 全息远程处理， 全息远程处理播放器， HoloLens， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， unity 播放模式
ms.openlocfilehash: caa9d7bf11104ee168fda24fc369de490feb7817
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547095"
---
# <a name="unity-play-mode"></a><span data-ttu-id="39f89-104">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="39f89-104">Unity Play Mode</span></span>

<span data-ttu-id="39f89-105">处理 Unity 项目的一种快速方法就是使用"播放模式"，该模式在电脑上的 Unity 编辑器中本地运行应用。</span><span class="sxs-lookup"><span data-stu-id="39f89-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="39f89-106">Unity 使用全息远程处理提供在真实 HoloLens 设备上预览内容的快速方法。</span><span class="sxs-lookup"><span data-stu-id="39f89-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="39f89-107">播放模式还可以与连接到开发电脑Windows Mixed Reality头戴显示设备一起使用。</span><span class="sxs-lookup"><span data-stu-id="39f89-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="39f89-108">全息远程处理设置</span><span class="sxs-lookup"><span data-stu-id="39f89-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="39f89-109">首先，需要 [从](https://www.microsoft.com/store/productId/9NBLGGH4SV40) 应用程序上的应用程序安装全息远程Microsoft Store应用HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="39f89-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="39f89-110">在 HoloLens 2 运行 Holographic Remoting Player 应用，你将看到要连接到的版本号和 IP 地址</span><span class="sxs-lookup"><span data-stu-id="39f89-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="39f89-111">需要 v2.4 或更高版本来使用 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="39f89-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![在 HoloLens 中运行的全息远程处理播放器的屏幕截图](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="39f89-113">Unity 编辑器播放模式下的全息远程处理</span><span class="sxs-lookup"><span data-stu-id="39f89-113">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="39f89-114">在项目中生成 UWP Unity Visual Studio，然后打包并部署到 HoloLens 2 设备可能需要一些时间。</span><span class="sxs-lookup"><span data-stu-id="39f89-114">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="39f89-115">一种解决方案是启用全息编辑器远程处理功能，该功能允许使用"播放"模式将 C# 脚本直接调试到HoloLens 2设备。</span><span class="sxs-lookup"><span data-stu-id="39f89-115">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="39f89-116">此方案可避免生成 UWP 包以及将其部署到远程设备的开销。</span><span class="sxs-lookup"><span data-stu-id="39f89-116">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="39f89-117">按照全息远程 [处理设置中的步骤操作](#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="39f89-117">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="39f89-118">打开 **Windows > XR > OpenXR 编辑器远程处理**：</span><span class="sxs-lookup"><span data-stu-id="39f89-118">Open **Windows > XR > OpenXR Editor Remoting**:</span></span>

    ![Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-features-img-02.png)

3. <span data-ttu-id="39f89-120">输入从全息远程处理应用获取的 IP 地址，然后选择" **启用编辑器远程处理"**</span><span class="sxs-lookup"><span data-stu-id="39f89-120">Input the IP address you get from the Holographic Remoting app, and select **Enable Editor Remoting**</span></span>

    ![Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了"功能"](images/openxr-features-img-03.png)

<span data-ttu-id="39f89-122">现在，可以单击"播放"按钮，将 Unity 应用播放到 HoloLens 上的全息远程处理应用中。</span><span class="sxs-lookup"><span data-stu-id="39f89-122">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="39f89-123">还可以将 [脚本Visual Studio Unity，](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) 以在播放模式下调试 C# 脚本。</span><span class="sxs-lookup"><span data-stu-id="39f89-123">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="39f89-124">从版本 0.1.0 起，全息远程处理运行时不支持定位点，ARAnchorManager 功能将不能通过远程处理工作。</span><span class="sxs-lookup"><span data-stu-id="39f89-124">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="39f89-125">此功能将在未来版本中推出。</span><span class="sxs-lookup"><span data-stu-id="39f89-125">This feature is coming in future releases.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="39f89-126">使用全息远程处理的 Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="39f89-126">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="39f89-127">使用全息远程处理，可以在 HoloLens 上体验应用，同时该应用在电脑上的 Unity 编辑器中运行。</span><span class="sxs-lookup"><span data-stu-id="39f89-127">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="39f89-128">凝视、手势、语音和空间映射输入从 HoloLens 发送到电脑。</span><span class="sxs-lookup"><span data-stu-id="39f89-128">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="39f89-129">然后，渲染的帧将发送回 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="39f89-129">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="39f89-130">这是在不生成和部署完整项目的情况下快速调试应用的一种好方法。</span><span class="sxs-lookup"><span data-stu-id="39f89-130">This is a great way to quickly debug your app without building and deploying a full project.</span></span>

[!INCLUDE[](includes/unity-play-mode.md)]

<span data-ttu-id="39f89-131">全息远程处理需要快速的电脑和Wi-Fi连接。</span><span class="sxs-lookup"><span data-stu-id="39f89-131">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="39f89-132">可以在全息远程处理播放器 [文档中找到](../platform-capabilities-and-apis/holographic-remoting-player.md) 更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="39f89-132">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="39f89-133">为获得最佳结果，请确保应用正确设置 [焦点](focus-point-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="39f89-133">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="39f89-134">这有助于全息远程处理以最佳方式使场景适应无线连接的延迟。</span><span class="sxs-lookup"><span data-stu-id="39f89-134">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="39f89-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39f89-135">See Also</span></span>

* [<span data-ttu-id="39f89-136">全息远程播放器</span><span class="sxs-lookup"><span data-stu-id="39f89-136">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
