---
title: '编写全息远程处理远程应用 (WMR) '
description: 通过创建在远程计算机上呈现的全息远程处理远程应用远程内容，可将其流式传输到 HoloLens 2。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens，远程处理，全息远程处理，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，NuGet
ms.openlocfilehash: 5eddcc117008ebc54eac11965592099601880d3e
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530221"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a><span data-ttu-id="e11b9-104">使用 HolographicSpace API 编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="e11b9-104">Writing a Holographic Remoting remote app using the HolographicSpace API</span></span>

>[!IMPORTANT]
><span data-ttu-id="e11b9-105">本文档介绍了如何使用 [HOLOGRAPHICSPACE API](../native/getting-a-holographicspace.md)创建用于 HoloLens 2 的远程应用程序。</span><span class="sxs-lookup"><span data-stu-id="e11b9-105">This document describes the creation of a remote application for HoloLens 2 using the [HolographicSpace API](../native/getting-a-holographicspace.md).</span></span> <span data-ttu-id="e11b9-106">**HoloLens (第一代)** 的远程应用程序必须使用 NuGet **包版本1.x。**</span><span class="sxs-lookup"><span data-stu-id="e11b9-106">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="e11b9-107">这意味着，为 HoloLens 2 编写的远程应用程序与 HoloLens 1 不兼容，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="e11b9-107">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="e11b9-108">可在 [此处](add-holographic-remoting.md)找到 HoloLens 1 的文档。</span><span class="sxs-lookup"><span data-stu-id="e11b9-108">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="e11b9-109">全息远程处理应用可将远程呈现的内容流式传输到 HoloLens 2 和 Windows Mixed Reality 沉浸式头。</span><span class="sxs-lookup"><span data-stu-id="e11b9-109">Holographic Remoting apps can stream remotely rendered content to HoloLens 2 and Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="e11b9-110">你还可以访问更多系统资源，并将远程 [沉浸式视图](../../design/app-views.md) 集成到现有的台式计算机软件中。</span><span class="sxs-lookup"><span data-stu-id="e11b9-110">You can also access more system resources and integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="e11b9-111">远程应用从 HoloLens 2 接收输入数据流，在虚拟沉浸式视图中呈现内容，并将内容帧流式传输回 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="e11b9-111">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="e11b9-112">使用标准 Wi-fi 建立连接。</span><span class="sxs-lookup"><span data-stu-id="e11b9-112">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="e11b9-113">全息远程处理通过 NuGet 数据包添加到桌面或 UWP 应用。</span><span class="sxs-lookup"><span data-stu-id="e11b9-113">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="e11b9-114">需要其他代码来处理连接并在沉浸式视图中呈现。</span><span class="sxs-lookup"><span data-stu-id="e11b9-114">Additional code is required which handles the connection and renders in an immersive view.</span></span> <span data-ttu-id="e11b9-115">典型的远程处理连接的延迟最低为50毫秒。</span><span class="sxs-lookup"><span data-stu-id="e11b9-115">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="e11b9-116">播放机应用可以实时报告滞后时间。</span><span class="sxs-lookup"><span data-stu-id="e11b9-116">The player app can report the latency in real time.</span></span>

<span data-ttu-id="e11b9-117">此页面上的所有代码和工作项目都可以在 " [全息远程处理示例 github 存储库](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)" 中找到。</span><span class="sxs-lookup"><span data-stu-id="e11b9-117">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e11b9-118">先决条件</span><span class="sxs-lookup"><span data-stu-id="e11b9-118">Prerequisites</span></span>

<span data-ttu-id="e11b9-119">一个很好的起点是基于 DirectX 的基于 DirectX 的桌面或 UWP 应用，以 [HOLOGRAPHICSPACE API](../native/getting-a-holographicspace.md)为目标。</span><span class="sxs-lookup"><span data-stu-id="e11b9-119">A good starting point is a working DirectX based Desktop or UWP app, which targets the [HolographicSpace API](../native/getting-a-holographicspace.md).</span></span> <span data-ttu-id="e11b9-120">有关详细信息，请参阅 [DirectX 开发概述](../native/directx-development-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e11b9-120">For details see [DirectX development overview](../native/directx-development-overview.md).</span></span> <span data-ttu-id="e11b9-121">[C + + 全息版项目模板](../native/creating-a-holographic-directx-project.md)是一个很好的起点。</span><span class="sxs-lookup"><span data-stu-id="e11b9-121">The [C++ holographic project template](../native/creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="e11b9-122">使用全息远程处理的任何应用都应该编写为使用 [多线程单元](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)。</span><span class="sxs-lookup"><span data-stu-id="e11b9-122">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="e11b9-123">支持使用 [单线程单元](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) ，但会导致在播放过程中出现欠最佳的性能，并且可能会断断续续。</span><span class="sxs-lookup"><span data-stu-id="e11b9-123">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="e11b9-124">使用 c + +/WinRT [WinRT：： init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) 多线程单元是默认值。</span><span class="sxs-lookup"><span data-stu-id="e11b9-124">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="e11b9-125">获取全息远程处理 NuGet 包</span><span class="sxs-lookup"><span data-stu-id="e11b9-125">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="e11b9-126">将 NuGet 包添加到 Visual Studio 中的项目时需要执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="e11b9-126">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="e11b9-127">在 Visual Studio 中打开项目。</span><span class="sxs-lookup"><span data-stu-id="e11b9-127">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="e11b9-128">右键单击项目节点，然后选择 "**管理 NuGet 包 ...** "</span><span class="sxs-lookup"><span data-stu-id="e11b9-128">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="e11b9-129">在出现的面板中，选择 " **浏览** "，然后搜索 "全息远程处理"。</span><span class="sxs-lookup"><span data-stu-id="e11b9-129">In the panel that appears, select **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="e11b9-130">选择 " **Microsoft**"，并选择 "安装"，并选择 "**安装** **"。**</span><span class="sxs-lookup"><span data-stu-id="e11b9-130">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and select **Install**.</span></span>
5. <span data-ttu-id="e11b9-131">如果显示 " **预览** " 对话框，请选择 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="e11b9-131">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="e11b9-132">弹出 "许可协议" 对话框后，选择 " **我接受** "。</span><span class="sxs-lookup"><span data-stu-id="e11b9-132">Select **I Accept** when the license agreement dialog pops up.</span></span>

>[!NOTE]
><span data-ttu-id="e11b9-133">NuGet 包的版本1.x 仍适用于想要面向 HoloLens **1 的开发** 人员。</span><span class="sxs-lookup"><span data-stu-id="e11b9-133">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="e11b9-134">有关详细信息，请参阅 [将全息远程处理 (HoloLens (第一代) # B3 ](add-holographic-remoting.md)。</span><span class="sxs-lookup"><span data-stu-id="e11b9-134">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="e11b9-135">创建远程上下文</span><span class="sxs-lookup"><span data-stu-id="e11b9-135">Create the remote context</span></span>

<span data-ttu-id="e11b9-136">第一步，应用程序应创建远程上下文。</span><span class="sxs-lookup"><span data-stu-id="e11b9-136">As a first step the application should create a remote context.</span></span>

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
><span data-ttu-id="e11b9-137">全息远程处理的工作原理是通过使用远程处理特定运行时替换作为 Windows 一部分的 Windows Mixed Reality 运行时。</span><span class="sxs-lookup"><span data-stu-id="e11b9-137">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="e11b9-138">这是在创建远程上下文的过程中完成的。</span><span class="sxs-lookup"><span data-stu-id="e11b9-138">This is done during the creation of the remote context.</span></span> <span data-ttu-id="e11b9-139">因此，在创建远程上下文之前对任何 Windows Mixed Reality API 进行的任何调用都可能导致意外的行为。</span><span class="sxs-lookup"><span data-stu-id="e11b9-139">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="e11b9-140">推荐的方法是尽早创建远程上下文，然后再与任何混合现实 API 交互。</span><span class="sxs-lookup"><span data-stu-id="e11b9-140">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="e11b9-141">永远不要混合在使用对象创建或检索到 CreateRemoteContext 之前，通过任何 Windows Mixed Reality API 创建或检索的对象。</span><span class="sxs-lookup"><span data-stu-id="e11b9-141">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="e11b9-142">接下来，需要创建全息空间。</span><span class="sxs-lookup"><span data-stu-id="e11b9-142">Next the holographic space needs to be created.</span></span> <span data-ttu-id="e11b9-143">不需要指定 CoreWindow。</span><span class="sxs-lookup"><span data-stu-id="e11b9-143">Specifying a CoreWindow isn't required.</span></span> <span data-ttu-id="e11b9-144">没有 CoreWindow 的桌面应用程序可以只传递一个 ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="e11b9-144">Desktop apps that don't have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="e11b9-145">连接到设备</span><span class="sxs-lookup"><span data-stu-id="e11b9-145">Connect to the device</span></span>

<span data-ttu-id="e11b9-146">当远程应用已准备好呈现内容时，可以建立与播放机设备的连接。</span><span class="sxs-lookup"><span data-stu-id="e11b9-146">When the remote app is ready for rendering content a connection to the player device can be established.</span></span>

<span data-ttu-id="e11b9-147">可以通过以下两种方式之一来完成连接。</span><span class="sxs-lookup"><span data-stu-id="e11b9-147">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="e11b9-148">远程应用连接到设备上运行的播放机。</span><span class="sxs-lookup"><span data-stu-id="e11b9-148">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="e11b9-149">设备上运行的播放机连接到远程应用。</span><span class="sxs-lookup"><span data-stu-id="e11b9-149">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="e11b9-150">若要建立从远程应用到播放机设备的连接，请 ```Connect``` 在远程上下文上调用方法，指定主机名和端口。</span><span class="sxs-lookup"><span data-stu-id="e11b9-150">To establish a connection from the remote app to the player device call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="e11b9-151">全息远程处理播放器使用的端口为 **8265**。</span><span class="sxs-lookup"><span data-stu-id="e11b9-151">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="e11b9-152">与任何 c + +/WinRT API 一样， ```Connect``` 都可能引发需要处理的 WinRT：： hresult_error。</span><span class="sxs-lookup"><span data-stu-id="e11b9-152">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="e11b9-153">若要避免使用 [c + +/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) 语言投影， ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` 可以包含位于全息远程处理 NuGet 包内的文件。</span><span class="sxs-lookup"><span data-stu-id="e11b9-153">To avoid using [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="e11b9-154">它包含基础 COM 接口的声明。</span><span class="sxs-lookup"><span data-stu-id="e11b9-154">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="e11b9-155">不过，建议使用 c + +/WinRT。</span><span class="sxs-lookup"><span data-stu-id="e11b9-155">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="e11b9-156">可以通过调用方法来侦听远程应用上的传入连接 ```Listen``` 。</span><span class="sxs-lookup"><span data-stu-id="e11b9-156">Listening for incoming connections on the remote app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="e11b9-157">在此调用过程中，可以同时指定握手端口和传输端口。</span><span class="sxs-lookup"><span data-stu-id="e11b9-157">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="e11b9-158">握手端口用于初始握手。</span><span class="sxs-lookup"><span data-stu-id="e11b9-158">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="e11b9-159">然后通过传输端口发送数据。</span><span class="sxs-lookup"><span data-stu-id="e11b9-159">The data is then sent over the transport port.</span></span> <span data-ttu-id="e11b9-160">默认情况下，使用 **8265** 和 **8266** 。</span><span class="sxs-lookup"><span data-stu-id="e11b9-160">By default **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="e11b9-161">```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```NuGet 包内部包含由全息远程处理公开的 API 的详细文档。</span><span class="sxs-lookup"><span data-stu-id="e11b9-161">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="e11b9-162">处理特定于远程处理的事件</span><span class="sxs-lookup"><span data-stu-id="e11b9-162">Handling Remoting specific events</span></span>

<span data-ttu-id="e11b9-163">远程上下文公开三个事件，这对于监视连接状态很重要。</span><span class="sxs-lookup"><span data-stu-id="e11b9-163">The remote context exposes three events, which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="e11b9-164">OnConnected：成功建立到设备的连接后触发。</span><span class="sxs-lookup"><span data-stu-id="e11b9-164">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="e11b9-165">OnDisconnected：如果已建立的连接已关闭或无法建立连接，则触发。</span><span class="sxs-lookup"><span data-stu-id="e11b9-165">OnDisconnected: Triggered if an established connection is closed or a connection couldn't be established.</span></span>
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) <span data-ttu-id="e11b9-166">OnListening：侦听传入连接时启动。</span><span class="sxs-lookup"><span data-stu-id="e11b9-166">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="e11b9-167">此外，还可以使用远程上下文中的属性查询连接状态 ```ConnectionState``` 。</span><span class="sxs-lookup"><span data-stu-id="e11b9-167">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="e11b9-168">处理语音事件</span><span class="sxs-lookup"><span data-stu-id="e11b9-168">Handling speech events</span></span>

<span data-ttu-id="e11b9-169">使用远程语音界面，可以向 HoloLens 2 注册语音触发器，并使其远程处理到远程应用程序。</span><span class="sxs-lookup"><span data-stu-id="e11b9-169">Using the remote speech interface it's possible to register speech triggers with HoloLens 2 and have them remoted to the remote application.</span></span>

<span data-ttu-id="e11b9-170">此附加成员是跟踪远程语音状态所必需的。</span><span class="sxs-lookup"><span data-stu-id="e11b9-170">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="e11b9-171">首先需要检索远程语音接口。</span><span class="sxs-lookup"><span data-stu-id="e11b9-171">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="e11b9-172">使用异步帮助器方法，你可以初始化远程语音。</span><span class="sxs-lookup"><span data-stu-id="e11b9-172">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="e11b9-173">这应异步完成，因为初始化可能需要相当长的时间。</span><span class="sxs-lookup"><span data-stu-id="e11b9-173">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="e11b9-174">[带有 c + +/WinRT 的并发和异步操作](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) 介绍了如何通过 c + + 编写异步函数/WinRT。</span><span class="sxs-lookup"><span data-stu-id="e11b9-174">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

<span data-ttu-id="e11b9-175">可以通过两种方法来指定要识别的短语。</span><span class="sxs-lookup"><span data-stu-id="e11b9-175">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="e11b9-176">语音语法 xml 文件中的规范。</span><span class="sxs-lookup"><span data-stu-id="e11b9-176">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="e11b9-177">有关详细信息，请参阅 [如何创建基本 XML 语法](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) 。</span><span class="sxs-lookup"><span data-stu-id="e11b9-177">See [How to create a basic XML Grammar](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="e11b9-178">通过将字典向量传入到来指定 ```ApplyParameters``` 。</span><span class="sxs-lookup"><span data-stu-id="e11b9-178">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="e11b9-179">在 OnRecognizedSpeech 回调中，可以处理语音事件：</span><span class="sxs-lookup"><span data-stu-id="e11b9-179">Inside the OnRecognizedSpeech callback, the speech events can then be processed:</span></span>

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="e11b9-180">在本地预览流式处理内容</span><span class="sxs-lookup"><span data-stu-id="e11b9-180">Preview streamed content locally</span></span>

<span data-ttu-id="e11b9-181">若要在发送到设备的远程应用中显示相同的内容， ```OnSendFrame``` 可以使用远程上下文的事件。</span><span class="sxs-lookup"><span data-stu-id="e11b9-181">To display the same content in the remote app that is sent to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="e11b9-182">```OnSendFrame```每次全息远程处理库将当前帧发送到远程设备时，都会触发事件。</span><span class="sxs-lookup"><span data-stu-id="e11b9-182">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="e11b9-183">这是获取内容并将其 array.blit 到桌面或 UWP 窗口的理想时机。</span><span class="sxs-lookup"><span data-stu-id="e11b9-183">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a><span data-ttu-id="e11b9-184">深度 Reprojection</span><span class="sxs-lookup"><span data-stu-id="e11b9-184">Depth Reprojection</span></span>

<span data-ttu-id="e11b9-185">从版本 [2.1.0](holographic-remoting-version-history.md#v2.1.0)开始，全息远程处理支持 [深度 Reprojection](hologram-stability.md#reprojection)。</span><span class="sxs-lookup"><span data-stu-id="e11b9-185">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0), Holographic Remoting supports [Depth Reprojection](hologram-stability.md#reprojection).</span></span> <span data-ttu-id="e11b9-186">这需要将颜色缓冲区和深度缓冲区从远程应用程序流式传输到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="e11b9-186">This requires both the color buffer and depth buffer to be streamed from the Remote application to the HoloLens 2.</span></span> <span data-ttu-id="e11b9-187">默认情况下，将启用深度缓冲区流式处理，并将其配置为使用一半分辨率的颜色缓冲区。</span><span class="sxs-lookup"><span data-stu-id="e11b9-187">By default depth buffer streaming is enabled and configured to use half the resolution of the color buffer.</span></span> <span data-ttu-id="e11b9-188">这可以按如下方式更改：</span><span class="sxs-lookup"><span data-stu-id="e11b9-188">This can be changed as follows:</span></span>

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

<span data-ttu-id="e11b9-189">请注意，如果不应使用默认值，则 ```ConfigureDepthVideoStream``` 必须在与 HoloLens 2 建立连接之前调用默认值。</span><span class="sxs-lookup"><span data-stu-id="e11b9-189">Note, if default values should not be used ```ConfigureDepthVideoStream``` must be called before establishing a connection to the HoloLens 2.</span></span> <span data-ttu-id="e11b9-190">最好的位置是创建远程上下文。</span><span class="sxs-lookup"><span data-stu-id="e11b9-190">The best place is right after you have created the remote context.</span></span> <span data-ttu-id="e11b9-191">DepthBufferStreamResolution 的可能值为：</span><span class="sxs-lookup"><span data-stu-id="e11b9-191">Possible values for DepthBufferStreamResolution are:</span></span>

* <span data-ttu-id="e11b9-192">Full_Resolution</span><span class="sxs-lookup"><span data-stu-id="e11b9-192">Full_Resolution</span></span>
* <span data-ttu-id="e11b9-193">Half_Resolution</span><span class="sxs-lookup"><span data-stu-id="e11b9-193">Half_Resolution</span></span>
* <span data-ttu-id="e11b9-194">Quarter_Resolution</span><span class="sxs-lookup"><span data-stu-id="e11b9-194">Quarter_Resolution</span></span>
* <span data-ttu-id="e11b9-195">已禁用 (使用版本 [2.1.3](holographic-remoting-version-history.md#v2.1.3) 添加，如果未使用，则不会创建其他深度视频流) </span><span class="sxs-lookup"><span data-stu-id="e11b9-195">Disabled (added with version [2.1.3](holographic-remoting-version-history.md#v2.1.3) and if used no additional depth video stream is created)</span></span>

<span data-ttu-id="e11b9-196">请记住，使用完全解析深度缓冲区还会影响带宽要求，并需要考虑到提供的最大带宽值 ```CreateRemoteContext``` 。</span><span class="sxs-lookup"><span data-stu-id="e11b9-196">Keep in mind that using a full resolution depth buffer also affects bandwidth requirements and needs to be accounted for in the maximum bandwidth value you provide to ```CreateRemoteContext```.</span></span>

<span data-ttu-id="e11b9-197">在配置分辨率旁边，还必须通过 HolographicCameraRenderingParameters 提交深度缓冲区 [。 CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)。</span><span class="sxs-lookup"><span data-stu-id="e11b9-197">Beside configuring the resolution, you also have to commit a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

<span data-ttu-id="e11b9-198">若要验证 reprojection 在 HoloLens 2 上是否正常工作，可以通过设备门户启用深度可视化工具。</span><span class="sxs-lookup"><span data-stu-id="e11b9-198">To verify if depth reprojection is correctly working on HoloLens 2, you can enable a depth visualizer via the Device Portal.</span></span> <span data-ttu-id="e11b9-199">有关详细信息，请参阅 [验证深度是否已正确设置](hologram-stability.md#verifying-depth-is-set-correctly) 。</span><span class="sxs-lookup"><span data-stu-id="e11b9-199">See [Verifying Depth is Set Correctly](hologram-stability.md#verifying-depth-is-set-correctly) for details.</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="e11b9-200">可选：自定义数据通道</span><span class="sxs-lookup"><span data-stu-id="e11b9-200">Optional: Custom data channels</span></span>

<span data-ttu-id="e11b9-201">自定义数据信道可用于通过已建立的远程处理连接发送用户数据。</span><span class="sxs-lookup"><span data-stu-id="e11b9-201">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="e11b9-202">有关详细信息，请参阅 [自定义数据通道](holographic-remoting-custom-data-channels.md) 。</span><span class="sxs-lookup"><span data-stu-id="e11b9-202">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="e11b9-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e11b9-203">See Also</span></span>
* [<span data-ttu-id="e11b9-204">编写自定义全息远程处理播放器应用</span><span class="sxs-lookup"><span data-stu-id="e11b9-204">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="e11b9-205">自定义全息远程处理数据通道</span><span class="sxs-lookup"><span data-stu-id="e11b9-205">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="e11b9-206">使用全息远程处理建立安全连接</span><span class="sxs-lookup"><span data-stu-id="e11b9-206">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="e11b9-207">全息远程处理故障排除和限制</span><span class="sxs-lookup"><span data-stu-id="e11b9-207">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="e11b9-208">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="e11b9-208">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="e11b9-209">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="e11b9-209">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
