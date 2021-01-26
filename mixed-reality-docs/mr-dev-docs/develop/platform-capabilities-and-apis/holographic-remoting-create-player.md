---
title: 编写自定义全息远程处理播放器
description: 创建自定义 Hologaphic 远程处理应用，将远程计算机上呈现的内容显示到 HoloLens 2。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens，远程处理，全息远程处理，NuGet，应用清单，播放机上下文，远程应用，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 391650025398b4bdd89e30db1df7df5e3d6ab5f2
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810127"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="54096-104">编写自定义全息远程处理播放器应用</span><span class="sxs-lookup"><span data-stu-id="54096-104">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="54096-105">本文档介绍了如何为 HoloLens 2 创建自定义播放器应用程序。</span><span class="sxs-lookup"><span data-stu-id="54096-105">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="54096-106">为 HoloLens 2 编写的自定义播放器与为 HoloLens 1 编写的远程应用程序不兼容。</span><span class="sxs-lookup"><span data-stu-id="54096-106">Custom players written for HoloLens 2 are not compatible with remote applications written for HoloLens 1.</span></span> <span data-ttu-id="54096-107">这意味着两个应用程序必须使用 NuGet 包 **版本2.x。**</span><span class="sxs-lookup"><span data-stu-id="54096-107">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="54096-108">通过创建自定义的全息远程处理播放器应用程序，你可以创建一个自定义应用程序，该应用程序能够在你的 HoloLens 2 上的远程计算机上显示 [沉浸式视图](../../design/app-views.md) 。</span><span class="sxs-lookup"><span data-stu-id="54096-108">By creating a custom Holographic Remoting player app, you can create a custom application capable of displaying [immersive views](../../design/app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="54096-109">此页面上的所有代码和工作项目都可以在 " [全息远程处理示例 github 存储库](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)" 中找到。</span><span class="sxs-lookup"><span data-stu-id="54096-109">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="54096-110">使用全息远程处理播放机，你的应用可以显示桌面 PC 或 UWP 设备上 [呈现](rendering.md) 的全息内容，如 Xbox one，可以访问更多系统资源。</span><span class="sxs-lookup"><span data-stu-id="54096-110">A Holographic Remoting player lets your app display holographic content [rendered](rendering.md) on a desktop PC or UWP device like the Xbox One with access to more system resources.</span></span> <span data-ttu-id="54096-111">全息远程处理播放机应用将输入数据流式传输到全息远程处理远程应用程序，并将沉浸式视图作为视频和音频流接收回来。</span><span class="sxs-lookup"><span data-stu-id="54096-111">A Holographic Remoting player app streams input data to a Holographic Remoting remote application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="54096-112">使用标准 Wi-fi 建立连接。</span><span class="sxs-lookup"><span data-stu-id="54096-112">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="54096-113">若要创建播放机应用，请使用 NuGet 包将全息远程处理添加到 UWP 应用。</span><span class="sxs-lookup"><span data-stu-id="54096-113">To create a player app, use a NuGet package to add Holographic Remoting to your UWP app.</span></span> <span data-ttu-id="54096-114">然后编写代码来处理连接并显示沉浸式视图。</span><span class="sxs-lookup"><span data-stu-id="54096-114">Then write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="54096-115">先决条件</span><span class="sxs-lookup"><span data-stu-id="54096-115">Prerequisites</span></span>

<span data-ttu-id="54096-116">很好的起点是基于 DirectX 的基于 DirectX 的 UWP 应用，已经以 Windows Mixed Reality API 为目标。</span><span class="sxs-lookup"><span data-stu-id="54096-116">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="54096-117">有关详细信息，请参阅 [DirectX 开发概述](../native/directx-development-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="54096-117">For details see [DirectX development overview](../native/directx-development-overview.md).</span></span> <span data-ttu-id="54096-118">如果你没有现成的应用程序，并且想要从头开始， [c + + 全息项目模板](../native/creating-a-holographic-directx-project.md) 是一个不错的开端。</span><span class="sxs-lookup"><span data-stu-id="54096-118">If you don't have an existing app and want to start from scratch the [C++ holographic project template](../native/creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="54096-119">使用全息远程处理的任何应用都应该编写为使用 [多线程单元](/windows/win32/com/multithreaded-apartments)。</span><span class="sxs-lookup"><span data-stu-id="54096-119">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](/windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="54096-120">支持使用 [单线程单元](/windows/win32/com/single-threaded-apartments) ，但会导致在播放过程中出现欠最佳的性能，并且可能会断断续续。</span><span class="sxs-lookup"><span data-stu-id="54096-120">The use of a [single-threaded apartment](/windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="54096-121">使用 c + +/WinRT [WinRT：： init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) 多线程单元是默认值。</span><span class="sxs-lookup"><span data-stu-id="54096-121">When using C++/WinRT [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="54096-122">获取全息远程处理 NuGet 包</span><span class="sxs-lookup"><span data-stu-id="54096-122">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="54096-123">将 NuGet 包添加到 Visual Studio 中的项目时需要执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="54096-123">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="54096-124">在 Visual Studio 中打开项目。</span><span class="sxs-lookup"><span data-stu-id="54096-124">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="54096-125">右键单击项目节点，然后选择 "**管理 NuGet 包 ...** "</span><span class="sxs-lookup"><span data-stu-id="54096-125">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="54096-126">在出现的面板中，选择 " **浏览** "，然后搜索 "全息远程处理"。</span><span class="sxs-lookup"><span data-stu-id="54096-126">In the panel that appears, select **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="54096-127">选择 " **Microsoft**"，并选择 "安装"，并选择 "**安装** **"。**</span><span class="sxs-lookup"><span data-stu-id="54096-127">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and select **Install**.</span></span>
5. <span data-ttu-id="54096-128">如果显示 " **预览** " 对话框，请选择 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="54096-128">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="54096-129">当 "许可协议" 对话框出现时，选择 " **我接受** "。</span><span class="sxs-lookup"><span data-stu-id="54096-129">Select **I Accept** when the license agreement dialog appears.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="54096-130">```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```NuGet 包内部包含由全息远程处理公开的 API 的详细文档。</span><span class="sxs-lookup"><span data-stu-id="54096-130">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="54096-131">修改应用程序的 appxmanifest.xml</span><span class="sxs-lookup"><span data-stu-id="54096-131">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="54096-132">若要使应用程序了解 NuGet 包添加的 Microsoft.Holographic.AppRemoting.dll，需要对项目执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="54096-132">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="54096-133">在解决方案资源管理器右键单击 **appxmanifest.xml** 文件并选择 "**打开方式 ...** "</span><span class="sxs-lookup"><span data-stu-id="54096-133">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="54096-134">选择 " **XML (文本) 编辑器** "，然后选择 **"确定"**</span><span class="sxs-lookup"><span data-stu-id="54096-134">Select **XML (Text) Editor** and select **OK**</span></span>
3. <span data-ttu-id="54096-135">将以下行添加到文件中并保存</span><span class="sxs-lookup"><span data-stu-id="54096-135">Add the following lines to the file and save</span></span>
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a><span data-ttu-id="54096-136">创建播放机上下文</span><span class="sxs-lookup"><span data-stu-id="54096-136">Create the player context</span></span>

<span data-ttu-id="54096-137">作为第一步，应用程序应创建播放机上下文。</span><span class="sxs-lookup"><span data-stu-id="54096-137">As a first step the application should create a player context.</span></span>

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
><span data-ttu-id="54096-138">全息远程处理的工作原理是通过使用远程处理特定运行时替换作为 Windows 一部分的 Windows Mixed Reality 运行时。</span><span class="sxs-lookup"><span data-stu-id="54096-138">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="54096-139">这是在创建播放机上下文的过程中完成的。</span><span class="sxs-lookup"><span data-stu-id="54096-139">This is done during the creation of the player context.</span></span> <span data-ttu-id="54096-140">因此，在创建播放机上下文之前对任何 Windows Mixed Reality API 进行的任何调用都可能导致意外的行为。</span><span class="sxs-lookup"><span data-stu-id="54096-140">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="54096-141">推荐的方法是尽早创建播放机上下文，然后再与任何混合现实 API 交互。</span><span class="sxs-lookup"><span data-stu-id="54096-141">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="54096-142">永远不要混合通过任何 Windows Mixed Reality API 创建或检索的对象 ```PlayerContext::Create``` 。</span><span class="sxs-lookup"><span data-stu-id="54096-142">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="54096-143">接下来，可以通过调用 [CreateForCoreWindow](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)创建 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="54096-143">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a><span data-ttu-id="54096-144">连接到远程应用</span><span class="sxs-lookup"><span data-stu-id="54096-144">Connect to the remote app</span></span>

<span data-ttu-id="54096-145">播放机应用准备好呈现内容后，可以建立到远程应用的连接。</span><span class="sxs-lookup"><span data-stu-id="54096-145">Once the player app is ready for rendering content a connection to the remote app can be established.</span></span>

<span data-ttu-id="54096-146">可以通过以下方式之一建立连接：</span><span class="sxs-lookup"><span data-stu-id="54096-146">The connection can be established in one of the following ways:</span></span>
1) <span data-ttu-id="54096-147">在 HoloLens 2 上运行的播放机应用会连接到远程应用。</span><span class="sxs-lookup"><span data-stu-id="54096-147">The player app running on HoloLens 2 connects to the remote app.</span></span>
2) <span data-ttu-id="54096-148">远程应用连接到在 HoloLens 2 上运行的播放机应用。</span><span class="sxs-lookup"><span data-stu-id="54096-148">The remote app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="54096-149">若要从播放机应用连接到远程应用，请 ```Connect``` 在指定主机名和端口的播放机上下文上调用方法。</span><span class="sxs-lookup"><span data-stu-id="54096-149">To connect from the player app to the remote app call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="54096-150">默认端口为 **8265**。</span><span class="sxs-lookup"><span data-stu-id="54096-150">The default port is **8265**.</span></span>

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
><span data-ttu-id="54096-151">与任何 c + +/WinRT API 一样， ```Connect``` 都可能引发需要处理的 WinRT：： hresult_error。</span><span class="sxs-lookup"><span data-stu-id="54096-151">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="54096-152">可以通过调用方法来侦听播放机应用上的传入连接 ```Listen``` 。</span><span class="sxs-lookup"><span data-stu-id="54096-152">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="54096-153">在此调用过程中，可以同时指定握手端口和传输端口。</span><span class="sxs-lookup"><span data-stu-id="54096-153">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="54096-154">握手端口用于初始握手。</span><span class="sxs-lookup"><span data-stu-id="54096-154">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="54096-155">然后通过传输端口发送数据。</span><span class="sxs-lookup"><span data-stu-id="54096-155">The data is then sent over the transport port.</span></span> <span data-ttu-id="54096-156">默认情况下，使用端口号 **8265** 和 **8266** 。</span><span class="sxs-lookup"><span data-stu-id="54096-156">By default port number **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a><span data-ttu-id="54096-157">处理与连接相关的事件</span><span class="sxs-lookup"><span data-stu-id="54096-157">Handling connection-related events</span></span>

<span data-ttu-id="54096-158">```PlayerContext```公开了三个事件来监视连接的状态</span><span class="sxs-lookup"><span data-stu-id="54096-158">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="54096-159">OnConnected：已成功建立到远程应用程序的连接时触发。</span><span class="sxs-lookup"><span data-stu-id="54096-159">OnConnected: Triggered when a connection to the remote app has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="54096-160">OnDisconnected：如果已建立的连接终止或无法建立连接，则触发。</span><span class="sxs-lookup"><span data-stu-id="54096-160">OnDisconnected: Triggered if an established connection is terminated or a connection couldn't be established.</span></span>
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
><span data-ttu-id="54096-161">可能 ```ConnectionFailureReason``` 的值记录在 ```Microsoft.Holographic.AppRemoting.idl``` [文件](#idl)中。</span><span class="sxs-lookup"><span data-stu-id="54096-161">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="54096-162">OnListening：侦听传入连接时启动。</span><span class="sxs-lookup"><span data-stu-id="54096-162">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="54096-163">此外，还可以使用 ```ConnectionState``` 播放机上下文上的属性查询连接状态。</span><span class="sxs-lookup"><span data-stu-id="54096-163">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="54096-164">显示远程呈现的帧</span><span class="sxs-lookup"><span data-stu-id="54096-164">Display the remotely rendered frame</span></span>

<span data-ttu-id="54096-165">若要显示远程呈现的内容，请 ```PlayerContext::BlitRemoteFrame``` 在呈现 [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)时调用。</span><span class="sxs-lookup"><span data-stu-id="54096-165">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame``` while rendering a [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="54096-166">```BlitRemoteFrame``` 要求当前 HolographicFrame 的后台缓冲区绑定为呈现器目标。</span><span class="sxs-lookup"><span data-stu-id="54096-166">```BlitRemoteFrame``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="54096-167">可以通过[Direct3D11BackBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)属性从[HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters)接收后台缓冲区。</span><span class="sxs-lookup"><span data-stu-id="54096-167">The back buffer can be received from the [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="54096-168">调用时，会 ```BlitRemoteFrame``` 将远程应用程序中接收的最新帧复制到 HolographicFrame 的后台缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="54096-168">When called, ```BlitRemoteFrame``` copies the latest received frame from the remote application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="54096-169">此外，如果远程应用程序在呈现远程帧期间指定了焦点，则会设置焦点集。</span><span class="sxs-lookup"><span data-stu-id="54096-169">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="54096-170">```PlayerContext::BlitRemoteFrame``` 可能覆盖当前帧的焦点。</span><span class="sxs-lookup"><span data-stu-id="54096-170">```PlayerContext::BlitRemoteFrame``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="54096-171">若要指定回退焦点点，请在之前调用 [HolographicCameraRenderingParameters：： SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame``` 。</span><span class="sxs-lookup"><span data-stu-id="54096-171">To specify a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame```.</span></span> 
>- <span data-ttu-id="54096-172">若要覆盖远程焦点，请在之后调用 [HolographicCameraRenderingParameters：： SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame``` 。</span><span class="sxs-lookup"><span data-stu-id="54096-172">To overwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame```.</span></span>

<span data-ttu-id="54096-173">如果成功，则 ```BlitRemoteFrame``` 返回 ```BlitResult::Success_Color``` 。</span><span class="sxs-lookup"><span data-stu-id="54096-173">On success, ```BlitRemoteFrame``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="54096-174">否则，它将返回失败原因：</span><span class="sxs-lookup"><span data-stu-id="54096-174">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="54096-175">```BlitResult::Failed_NoRemoteFrameAvailable```：失败，因为没有可用的远程帧。</span><span class="sxs-lookup"><span data-stu-id="54096-175">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="54096-176">```BlitResult::Failed_NoCamera```：由于不存在任何照相机而失败。</span><span class="sxs-lookup"><span data-stu-id="54096-176">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>
- <span data-ttu-id="54096-177">```BlitResult::Failed_RemoteFrameTooOld```：由于远程帧太旧，导致失败 (请参阅 PlayerContext：： BlitRemoteFrameTimeout 属性) 。</span><span class="sxs-lookup"><span data-stu-id="54096-177">```BlitResult::Failed_RemoteFrameTooOld```: Failed because remote frame is too old (see PlayerContext::BlitRemoteFrameTimeout property).</span></span>

>[!IMPORTANT]
> <span data-ttu-id="54096-178">从版本 [2.1.0](holographic-remoting-version-history.md#v2.1.0) 开始，自定义播放器可以通过全息远程处理使用深度 reprojection。</span><span class="sxs-lookup"><span data-stu-id="54096-178">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) it is possible with a custom player to use depth reprojection via Holographic Remoting.</span></span>

<span data-ttu-id="54096-179">```BlitResult``````BlitResult::Success_Color_Depth```在下列条件下，也可以返回：</span><span class="sxs-lookup"><span data-stu-id="54096-179">```BlitResult``` can also return ```BlitResult::Success_Color_Depth``` under the following conditions:</span></span>

- <span data-ttu-id="54096-180">远程应用已通过 HolographicCameraRenderingParameters 提交深度缓冲区 [。 CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)。</span><span class="sxs-lookup"><span data-stu-id="54096-180">The remote app has committed a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>
- <span data-ttu-id="54096-181">自定义播放机应用在调用之前已绑定了有效的深度缓冲区 ```BlitRemoteFrame``` 。</span><span class="sxs-lookup"><span data-stu-id="54096-181">The custom player app has bound a valid depth buffer before calling ```BlitRemoteFrame```.</span></span>

<span data-ttu-id="54096-182">如果满足这些条件，则 ```BlitRemoteFrame``` 会将远程深度 array.blit 当前绑定的本地深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="54096-182">If these conditions are met ```BlitRemoteFrame``` will blit the remote depth into the currently bound local depth buffer.</span></span> <span data-ttu-id="54096-183">然后，您可以呈现其他本地内容，这将与远程呈现的内容具有深度交集。</span><span class="sxs-lookup"><span data-stu-id="54096-183">You can then render additional local content, which will have depth intersection with the remote rendered content.</span></span> <span data-ttu-id="54096-184">此外，还可以通过自定义播放机中的 [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) 来提交本地深度缓冲区，以获得远程和本地呈现内容的深度 reprojection。</span><span class="sxs-lookup"><span data-stu-id="54096-184">Additionally you can commit the local depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) in your custom player to have depth reprojection for remote and local rendered content.</span></span> <span data-ttu-id="54096-185">有关详细信息，请参阅 [深度 Reprojection](hologram-stability.md#reprojection) 。</span><span class="sxs-lookup"><span data-stu-id="54096-185">See [Depth Reprojection](hologram-stability.md#reprojection) for details.</span></span>

### <a name="projection-transform-mode"></a><span data-ttu-id="54096-186">投影转换模式</span><span class="sxs-lookup"><span data-stu-id="54096-186">Projection Transform Mode</span></span>

<span data-ttu-id="54096-187">一个问题是，在通过全息远程处理使用深度 reprojection 的情况下，可以使用与自定义播放器应用直接呈现的本地内容不同的投影转换来呈现远程内容。</span><span class="sxs-lookup"><span data-stu-id="54096-187">One problem, which surfaces when using depth reprojection via Holographic Remoting is that the remote content can be rendered with a different projection transform than local content directly rendered by your custom player app.</span></span> <span data-ttu-id="54096-188">常见的用例是在播放机端和远程端 (通过 [HolographicCamera：： SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) 和 [HolographicCamera：： SetFarPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) 为近和远平面指定不同的值。</span><span class="sxs-lookup"><span data-stu-id="54096-188">A common use-case is to specify different values for near and far plane (via [HolographicCamera::SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) and [HolographicCamera::SetFarPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) on the player side and the remote side.</span></span> <span data-ttu-id="54096-189">在这种情况下，如果播放机端上的投影转换应反映远程的接近/远平面距离或局部，则不清楚。</span><span class="sxs-lookup"><span data-stu-id="54096-189">In this case, it's not clear if the projection transform on the player side should reflect the remote near/far plane distances or the local ones.</span></span>

<span data-ttu-id="54096-190">从版本 [2.1.0](holographic-remoting-version-history.md#v2.1.0) 开始，可以通过来控制投影转换模式 ```PlayerContext::ProjectionTransformConfig``` 。</span><span class="sxs-lookup"><span data-stu-id="54096-190">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) you can control the projection transform mode via ```PlayerContext::ProjectionTransformConfig```.</span></span> <span data-ttu-id="54096-191">支持的值是：</span><span class="sxs-lookup"><span data-stu-id="54096-191">Supported values are:</span></span>

- <span data-ttu-id="54096-192">```Local``` - [HolographicCameraPose：:P rojectiontransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) 返回投影转换，该转换反映了 HolographicCamera 上的自定义播放器应用设置的近/远平面距离。</span><span class="sxs-lookup"><span data-stu-id="54096-192">```Local``` - [HolographicCameraPose::ProjectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) returns a projection transform, which reflects the near/far plane distances set by your custom player app on the HolographicCamera.</span></span>
- <span data-ttu-id="54096-193">```Remote``` -投影转换反映远程应用指定的近/远平面距离。</span><span class="sxs-lookup"><span data-stu-id="54096-193">```Remote``` - Projection transform reflects the near/far plane distances specified by the remote app.</span></span>
- <span data-ttu-id="54096-194">```Merged``` -与你的远程应用和自定义播放器应用的接近/远平面距离合并。</span><span class="sxs-lookup"><span data-stu-id="54096-194">```Merged``` - Near/Far plane distances from your remote app and your custom player app are merged.</span></span> <span data-ttu-id="54096-195">默认情况下，这是通过使用接近平面距离和最大平面距离的最小值来完成的。</span><span class="sxs-lookup"><span data-stu-id="54096-195">By default this is done by taking the minimum of the near plane distances and the maximum of the far plane distances.</span></span> <span data-ttu-id="54096-196">如果远程或本地侧反转，说远 < 接近，则会翻转远程近/远平面距离。</span><span class="sxs-lookup"><span data-stu-id="54096-196">In case either the remote or local side are inverted, say far < near, the remote near/far plane distances are flipped.</span></span>

## <a name="optional-set-blitremoteframetimeout"></a><span data-ttu-id="54096-197">可选：设置 BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span><span class="sxs-lookup"><span data-stu-id="54096-197">Optional: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span></span>
>[!IMPORTANT]
> <span data-ttu-id="54096-198">```PlayerContext::BlitRemoteFrameTimeout``` 从版本 [2.0.9](holographic-remoting-version-history.md#v2.0.9)开始支持。</span><span class="sxs-lookup"><span data-stu-id="54096-198">```PlayerContext::BlitRemoteFrameTimeout``` is supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 

<span data-ttu-id="54096-199">```PlayerContext::BlitRemoteFrameTimeout```如果未接收到新的远程帧，则属性指定重复使用远程帧的时间长度。</span><span class="sxs-lookup"><span data-stu-id="54096-199">The ```PlayerContext::BlitRemoteFrameTimeout``` property specifies the amount of time a remote frame is reused if no new remote frame is received.</span></span> 

<span data-ttu-id="54096-200">常见的用例是，如果在一段时间内没有收到新帧，BlitRemoteFrame 超时将显示空白屏幕。</span><span class="sxs-lookup"><span data-stu-id="54096-200">A common use-case is to enable the BlitRemoteFrame timeout to display a blank screen if no new frames are received for a certain amount of time.</span></span> <span data-ttu-id="54096-201">启用时，方法的返回类型 ```BlitRemoteFrame``` 还可用于切换到本地呈现的回退内容。</span><span class="sxs-lookup"><span data-stu-id="54096-201">When enabled the return type of the ```BlitRemoteFrame``` method can also be used to switch to a locally rendered fallback content.</span></span> 

<span data-ttu-id="54096-202">若要启用超时，请将属性值设置为等于或大于 100 ms 的持续时间。</span><span class="sxs-lookup"><span data-stu-id="54096-202">To enable the timeout, set the property value to a duration equal or greater than 100 ms.</span></span> <span data-ttu-id="54096-203">若要禁用超时，请将属性设置为零。</span><span class="sxs-lookup"><span data-stu-id="54096-203">To disable the timeout, set the property to zero duration.</span></span> <span data-ttu-id="54096-204">如果在设置的持续时间内启用了超时并且未收到任何远程帧，则 BlitRemoteFrame 将失败并返回， ```Failed_RemoteFrameTooOld``` 直到接收到新的远程帧。</span><span class="sxs-lookup"><span data-stu-id="54096-204">If the timeout is enabled and no remote frame is received for the set duration, BlitRemoteFrame will fail and return ```Failed_RemoteFrameTooOld``` until a new remote frame is received.</span></span>

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="54096-205">可选：获取有关最后一个远程帧的统计信息</span><span class="sxs-lookup"><span data-stu-id="54096-205">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="54096-206">若要诊断性能或网络问题，可以通过属性检索有关最后一个远程帧的统计信息 ```PlayerContext::LastFrameStatistics``` 。</span><span class="sxs-lookup"><span data-stu-id="54096-206">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="54096-207">在调用 HolographicFrame 期间更新统计信息 [：:P resentusingcurrentprediction](/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)。</span><span class="sxs-lookup"><span data-stu-id="54096-207">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="54096-208">有关详细信息，请参阅 ```PlayerFrameStatistics``` 文件中的文档 ```Microsoft.Holographic.AppRemoting.idl``` [](#idl)。</span><span class="sxs-lookup"><span data-stu-id="54096-208">For more information, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="54096-209">可选：自定义数据通道</span><span class="sxs-lookup"><span data-stu-id="54096-209">Optional: Custom data channels</span></span>

<span data-ttu-id="54096-210">自定义数据信道可用于通过已建立的远程处理连接发送用户数据。</span><span class="sxs-lookup"><span data-stu-id="54096-210">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="54096-211">有关详细信息，请参阅 [自定义数据通道](holographic-remoting-custom-data-channels.md) 。</span><span class="sxs-lookup"><span data-stu-id="54096-211">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="54096-212">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54096-212">See Also</span></span>
* [<span data-ttu-id="54096-213">使用 Windows Mixed Reality Api 编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="54096-213">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="54096-214">使用 OpenXR Api 编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="54096-214">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="54096-215">自定义全息远程处理数据通道</span><span class="sxs-lookup"><span data-stu-id="54096-215">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="54096-216">使用全息远程处理建立安全连接</span><span class="sxs-lookup"><span data-stu-id="54096-216">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="54096-217">全息远程处理故障排除和限制</span><span class="sxs-lookup"><span data-stu-id="54096-217">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="54096-218">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="54096-218">Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="54096-219">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="54096-219">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)