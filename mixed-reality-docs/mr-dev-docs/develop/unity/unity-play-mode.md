---
title: Unity 播放模式
description: 了解如何在 Unity 编辑器中使用播放模式在不部署应用的情况下预览设备上的应用程序更改。
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，远程处理，全息远程处理，全息远程处理播放器，HoloLens，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity 播放模式
ms.openlocfilehash: 35f80b0c217adfd5c5d14799dc882d5c504925aa
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333393"
---
# <a name="unity-play-mode"></a><span data-ttu-id="41737-104">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="41737-104">Unity Play Mode</span></span>

<span data-ttu-id="41737-105">处理 Unity 项目的一种快速方法是使用 "播放模式"，该模式在计算机上的 Unity 编辑器中本地运行你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="41737-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="41737-106">Unity 使用全息远程处理提供一种在真实的 HoloLens 设备上快速预览内容的方式。</span><span class="sxs-lookup"><span data-stu-id="41737-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="41737-107">播放模式还可与附加到开发 PC 的 Windows Mixed Reality 耳机一起使用。</span><span class="sxs-lookup"><span data-stu-id="41737-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="41737-108">全息远程处理安装</span><span class="sxs-lookup"><span data-stu-id="41737-108">Holographic Remoting setup</span></span>

1. <span data-ttu-id="41737-109">首先，需要从 HoloLens 2 上的 Microsoft Store[安装全息远程处理播放器应用程序](https://www.microsoft.com/store/productId/9NBLGGH4SV40)</span><span class="sxs-lookup"><span data-stu-id="41737-109">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="41737-110">在 HoloLens 2 上运行全息远程处理播放器应用程序，你将看到要连接到的版本号和 IP 地址</span><span class="sxs-lookup"><span data-stu-id="41737-110">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="41737-111">你需要使用版本2.4 或更高版本才能使用 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="41737-111">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens 中运行的全息远程处理播放机的屏幕截图](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="41737-113">Unity 编辑器播放模式下的全息远程处理</span><span class="sxs-lookup"><span data-stu-id="41737-113">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="41737-114">在 Visual Studio 项目中生成 UWP Unity 项目，然后将其打包并部署到 HoloLens 2 设备可能需要一些时间。</span><span class="sxs-lookup"><span data-stu-id="41737-114">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="41737-115">一种解决方案是启用全息编辑器远程处理功能，该功能使你能够通过网络将 "播放" 模式直接调试到 HoloLens 2 设备。</span><span class="sxs-lookup"><span data-stu-id="41737-115">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="41737-116">此方案可避免生成 UWP 包并将其部署到远程设备的系统开销。</span><span class="sxs-lookup"><span data-stu-id="41737-116">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="41737-117">按照[全息远程处理设置](#holographic-remoting-setup)中的步骤操作</span><span class="sxs-lookup"><span data-stu-id="41737-117">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="41737-118">打开 **Windows > XR > OpenXR 编辑器远程处理**：</span><span class="sxs-lookup"><span data-stu-id="41737-118">Open **Windows > XR > OpenXR Editor Remoting**:</span></span>

    ![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-features-img-02.png)

3. <span data-ttu-id="41737-120">输入从全息远程处理应用获取的 IP 地址，然后选择 "**启用编辑器远程处理**"</span><span class="sxs-lookup"><span data-stu-id="41737-120">Input the IP address you get from the Holographic Remoting app, and select **Enable Editor Remoting**</span></span>

    ![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了功能](images/openxr-features-img-03.png)

<span data-ttu-id="41737-122">现在，你可以单击 "播放" 按钮，将 Unity 应用播放到 HoloLens 上的全息远程处理应用。</span><span class="sxs-lookup"><span data-stu-id="41737-122">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="41737-123">还可以将 [脚本Visual Studio Unity，](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) 以在播放模式下调试 C# 脚本。</span><span class="sxs-lookup"><span data-stu-id="41737-123">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="41737-124">从版本 0.1.0 起，全息远程处理运行时不支持定位点，ARAnchorManager 功能将不能通过远程处理工作。</span><span class="sxs-lookup"><span data-stu-id="41737-124">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="41737-125">此功能将在未来版本中推出。</span><span class="sxs-lookup"><span data-stu-id="41737-125">This feature is coming in future releases.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="41737-126">使用全息远程处理的 Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="41737-126">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="41737-127">使用全息远程处理，可以在 HoloLens 上体验应用，同时该应用在电脑上的 Unity 编辑器中运行。</span><span class="sxs-lookup"><span data-stu-id="41737-127">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="41737-128">凝视、手势、语音和空间映射输入从 HoloLens 发送到电脑。</span><span class="sxs-lookup"><span data-stu-id="41737-128">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="41737-129">然后，渲染的帧将发送回 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="41737-129">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="41737-130">这是在不生成和部署完整项目的情况下快速调试应用的一种好方法。</span><span class="sxs-lookup"><span data-stu-id="41737-130">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="41737-131">在 HoloLens 上，转到Microsoft Store并安装 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。</span><span class="sxs-lookup"><span data-stu-id="41737-131">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="41737-132">在 HoloLens 上，启动 **全息远程处理播放器** 应用。</span><span class="sxs-lookup"><span data-stu-id="41737-132">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="41737-133">在 Unity 中，转到 **"窗口"** 菜单，展开 **XR** 子菜单，然后选择"**全息仿真"。**</span><span class="sxs-lookup"><span data-stu-id="41737-133">In Unity, go to the **Window** menu, expand the **XR** submenu, and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="41737-134">将 **仿真模式设置为\*\*\*\*"远程"到"设备"。**</span><span class="sxs-lookup"><span data-stu-id="41737-134">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="41737-135">对于 **"远程计算机**"，请输入 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="41737-135">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="41737-136">选择“**连接**”。</span><span class="sxs-lookup"><span data-stu-id="41737-136">Select **Connect**.</span></span> <span data-ttu-id="41737-137">应会看到" **连接状态"** 更改为"已 **连接"，** 并且看到屏幕在 HoloLens 中为空白。</span><span class="sxs-lookup"><span data-stu-id="41737-137">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="41737-138">选择" **播放** "按钮以启动播放模式，并体验 HoloLens 上的应用。</span><span class="sxs-lookup"><span data-stu-id="41737-138">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="41737-139">全息远程处理需要快速的电脑和Wi-Fi连接。</span><span class="sxs-lookup"><span data-stu-id="41737-139">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="41737-140">可以在全息远程处理播放器 [文档中找到](../platform-capabilities-and-apis/holographic-remoting-player.md) 更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="41737-140">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="41737-141">为获得最佳结果，请确保应用正确设置 [焦点](focus-point-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="41737-141">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="41737-142">这有助于全息远程处理以最佳方式使场景适应无线连接的延迟。</span><span class="sxs-lookup"><span data-stu-id="41737-142">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="41737-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41737-143">See Also</span></span>
* [<span data-ttu-id="41737-144">全息远程播放器</span><span class="sxs-lookup"><span data-stu-id="41737-144">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
