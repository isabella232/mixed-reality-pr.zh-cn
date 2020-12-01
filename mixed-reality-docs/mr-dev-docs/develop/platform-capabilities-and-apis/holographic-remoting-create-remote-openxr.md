---
title: '编写全息远程处理远程应用 (OpenXR) '
description: 通过创建全息远程处理远程应用，可将在远程计算机上呈现的远程内容流式传输到 HoloLens 2。 本文介绍如何实现此目的。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens，远程处理，全息远程处理，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，NuGet
ms.openlocfilehash: 7e46c67e7dac08759890fa66d540379991414aad
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2020
ms.locfileid: "96469491"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a><span data-ttu-id="ced1a-105">使用 OpenXR API 编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="ced1a-105">Writing a Holographic Remoting remote app using the OpenXR API</span></span>

>[!IMPORTANT]
><span data-ttu-id="ced1a-106">本文档介绍了如何使用 [OPENXR API](../native/openxr.md)为 HoloLens 2 和 Windows Mixed Reality 耳机创建远程应用程序。</span><span class="sxs-lookup"><span data-stu-id="ced1a-106">This document describes the creation of a remote application for HoloLens 2 and Windows Mixed Reality headsets using the [OpenXR API](../native/openxr.md).</span></span> <span data-ttu-id="ced1a-107">**HoloLens (第一代)** 的远程应用程序必须使用 NuGet **包版本1.x。**</span><span class="sxs-lookup"><span data-stu-id="ced1a-107">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="ced1a-108">这意味着，为 HoloLens 2 编写的远程应用程序与 HoloLens 1 不兼容，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="ced1a-108">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="ced1a-109">可在 [此处](add-holographic-remoting.md)找到 HoloLens 1 的文档。</span><span class="sxs-lookup"><span data-stu-id="ced1a-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="ced1a-110">通过创建全息远程处理远程应用，可将远程计算机上呈现的远程内容流式传输到 HoloLens 2 和沉浸式设备，例如 Windows Mixed Reality 耳机。</span><span class="sxs-lookup"><span data-stu-id="ced1a-110">By creating a Holographic Remoting remote app, remote content that is rendered on a remote machine can be streamed to HoloLens 2 and immersive devices like Windows Mixed Reality headsets.</span></span> <span data-ttu-id="ced1a-111">本文介绍如何实现此目的。</span><span class="sxs-lookup"><span data-stu-id="ced1a-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="ced1a-112">此页面上的所有代码和工作项目都可以在 " [全息远程处理示例 github 存储库](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)" 中找到。</span><span class="sxs-lookup"><span data-stu-id="ced1a-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="ced1a-113">使用全息远程处理，应用程序可以面向 HoloLens 2 和 Windows Mixed Reality 耳机，其中的全息内容呈现在台式计算机上或 UWP 设备（如 Xbox 设备）上，允许访问更多的系统资源，并使你能够将远程 [沉浸式视图](../../design/app-views.md) 集成到现有的台式计算机软件中。</span><span class="sxs-lookup"><span data-stu-id="ced1a-113">Holographic remoting allows an app to target HoloLens 2 and Windows Mixed Reality headsets with holographic content rendered on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="ced1a-114">远程应用从 HoloLens 2 接收输入数据流，在虚拟沉浸式视图中呈现内容，并将内容帧流式传输回 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="ced1a-114">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="ced1a-115">使用标准 Wi-fi 建立连接。</span><span class="sxs-lookup"><span data-stu-id="ced1a-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="ced1a-116">全息远程处理通过 NuGet 数据包添加到桌面或 UWP 应用。</span><span class="sxs-lookup"><span data-stu-id="ced1a-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="ced1a-117">需要其他代码来处理连接并在沉浸式视图中呈现。</span><span class="sxs-lookup"><span data-stu-id="ced1a-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="ced1a-118">典型的远程处理连接的延迟最低为50毫秒。</span><span class="sxs-lookup"><span data-stu-id="ced1a-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="ced1a-119">播放机应用可以实时报告滞后时间。</span><span class="sxs-lookup"><span data-stu-id="ced1a-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ced1a-120">先决条件</span><span class="sxs-lookup"><span data-stu-id="ced1a-120">Prerequisites</span></span>

<span data-ttu-id="ced1a-121">好的起点是基于 OpenXR 的桌面或 UWP 应用。</span><span class="sxs-lookup"><span data-stu-id="ced1a-121">A good starting point is a working OpenXR based Desktop or UWP app.</span></span> <span data-ttu-id="ced1a-122">有关详细信息，请参阅 [OpenXR](../native/openxr-getting-started.md)入门。</span><span class="sxs-lookup"><span data-stu-id="ced1a-122">For details see [Getting started with OpenXR](../native/openxr-getting-started.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="ced1a-123">使用全息远程处理的任何应用都应该编写为使用 [多线程单元](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)。</span><span class="sxs-lookup"><span data-stu-id="ced1a-123">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="ced1a-124">支持使用 [单线程单元](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) ，但会导致在播放过程中出现欠最佳的性能，并且可能会断断续续。</span><span class="sxs-lookup"><span data-stu-id="ced1a-124">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="ced1a-125">使用 c + +/WinRT [WinRT：： init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) 多线程单元是默认值。</span><span class="sxs-lookup"><span data-stu-id="ced1a-125">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="ced1a-126">获取全息远程处理 NuGet 包</span><span class="sxs-lookup"><span data-stu-id="ced1a-126">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="ced1a-127">将 NuGet 包添加到 Visual Studio 中的项目时需要执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="ced1a-127">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="ced1a-128">在 Visual Studio 中打开项目。</span><span class="sxs-lookup"><span data-stu-id="ced1a-128">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="ced1a-129">右键单击项目节点，然后选择 "**管理 NuGet 包 ...** "</span><span class="sxs-lookup"><span data-stu-id="ced1a-129">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="ced1a-130">在出现的面板中，单击 " **浏览** "，然后搜索 "全息远程处理"。</span><span class="sxs-lookup"><span data-stu-id="ced1a-130">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="ced1a-131">选择 " **OpenXr**"，确保 **选择最新** 的2.x 版本，然后单击 " **安装**"。</span><span class="sxs-lookup"><span data-stu-id="ced1a-131">Select **Microsoft.Holographic.Remoting.OpenXr**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="ced1a-132">如果 **预览** 对话框出现，请单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="ced1a-132">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="ced1a-133">显示的下一个对话框是许可协议。</span><span class="sxs-lookup"><span data-stu-id="ced1a-133">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="ced1a-134">单击 " **我接受** " 接受许可协议。</span><span class="sxs-lookup"><span data-stu-id="ced1a-134">Click on **I Accept** to accept the license agreement.</span></span>
7. <span data-ttu-id="ced1a-135">对以下 NuGet 包重复步骤3到6： OpenXR、OpenXR</span><span class="sxs-lookup"><span data-stu-id="ced1a-135">Repeat the steps 3 to 6 for the following NuGet Packages: OpenXR.Headers, OpenXR.Loader</span></span>

>[!NOTE]
><span data-ttu-id="ced1a-136">NuGet 包的版本1.x 仍适用于想要面向 HoloLens **1 的开发** 人员。</span><span class="sxs-lookup"><span data-stu-id="ced1a-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="ced1a-137">有关详细信息，请参阅 [将全息远程处理 (HoloLens (第一代) # B3 ](add-holographic-remoting.md)。</span><span class="sxs-lookup"><span data-stu-id="ced1a-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="select-the-holographic-remoting-openxr-runtime"></a><span data-ttu-id="ced1a-138">选择全息远程处理 OpenXR 运行时</span><span class="sxs-lookup"><span data-stu-id="ced1a-138">Select the Holographic Remoting OpenXR runtime</span></span>

<span data-ttu-id="ced1a-139">在远程应用程序中需要执行的第一步是选择 OpenXr NuGet 包中的全息远程处理 OpenXR 运行时。</span><span class="sxs-lookup"><span data-stu-id="ced1a-139">The first step you need to do in your remote app is to select the Holographic Remoting OpenXR runtime which is part of the Microsoft.Holographic.Remoting.OpenXr NuGet package.</span></span> <span data-ttu-id="ced1a-140">为此，可以将 ```XR_RUNTIME_JSON``` 环境变量设置为应用中文件的 RemotingXR.js路径。</span><span class="sxs-lookup"><span data-stu-id="ced1a-140">You can do this by setting the ```XR_RUNTIME_JSON``` environment variable to the path of the RemotingXR.json file within your app.</span></span> <span data-ttu-id="ced1a-141">OpenXR 加载程序使用此环境变量来不使用系统默认 OpenXR 运行时，而是重定向到全息远程处理 OpenXR 运行时。</span><span class="sxs-lookup"><span data-stu-id="ced1a-141">This environment variable is used by the OpenXR loader to not use the system default OpenXR runtime but instead redirect to the Holographic Remoting OpenXR runtime.</span></span> <span data-ttu-id="ced1a-142">使用 OpenXr NuGet 包时，文件中的 RemotingXR.js会在编译过程中自动复制到输出文件夹，因此 OpenXR 运行时选择通常如下所示。</span><span class="sxs-lookup"><span data-stu-id="ced1a-142">When using the Microsoft.Holographic.Remoting.OpenXr NuGet package the RemotingXR.json file is automatically copied during compilation to the output folder, thus the OpenXR runtime selection typically looks as follows.</span></span>

```cpp
bool EnableRemotingXR() {
    wchar_t executablePath[MAX_PATH];
    if (GetModuleFileNameW(NULL, executablePath, ARRAYSIZE(executablePath)) == 0) {
        return false;
    }
    
    std::filesystem::path filename(executablePath);
    filename = filename.replace_filename("RemotingXR.json");

    if (std::filesystem::exists(filename)) {
        SetEnvironmentVariableW(L"XR_RUNTIME_JSON", filename.c_str());
            return true;
        }

    return false;
}
```

## <a name="create-xrinstance-with-holographic-remoting-extension"></a><span data-ttu-id="ced1a-143">创建包含全息远程处理扩展的 XrInstance</span><span class="sxs-lookup"><span data-stu-id="ced1a-143">Create XrInstance with Holographic Remoting Extension</span></span>

<span data-ttu-id="ced1a-144">典型的 OpenXR 应用程序的第一步是选择 OpenXR 扩展并创建 XrInstance。</span><span class="sxs-lookup"><span data-stu-id="ced1a-144">The first step a typical OpenXR app is supposed to do is to select OpenXR extensions and create a XrInstance.</span></span> <span data-ttu-id="ced1a-145">OpenXR 核心规范不提供任何远程处理特定的 API。</span><span class="sxs-lookup"><span data-stu-id="ced1a-145">The OpenXR core specification does not provide any remoting specific API.</span></span> <span data-ttu-id="ced1a-146">出于此原因，全息远程处理会引入自己的名为的 OpenXR 扩展 ```XR_MSFT_holographic_remoting``` 。</span><span class="sxs-lookup"><span data-stu-id="ced1a-146">For that reason Holographic Remoting introduces it's own OpenXR extension named ```XR_MSFT_holographic_remoting```.</span></span> <span data-ttu-id="ced1a-147">确保在调用 xrCreateInstance 时， ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` 包含在 XrInstanceCreateInfo 中。</span><span class="sxs-lookup"><span data-stu-id="ced1a-147">Ensure that when you call xrCreateInstance the ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` is included in the XrInstanceCreateInfo.</span></span>

>[!TIP]
><span data-ttu-id="ced1a-148">默认情况下，只会将应用程序的呈现内容传输到在 HoloLens 2 上或在 Windows Mixed Reality 耳机上运行的全息远程处理播放机。</span><span class="sxs-lookup"><span data-stu-id="ced1a-148">By default the rendered content of your app is only streamed to the Holographic Remoting player either running on a HoloLens 2 or on a Windows Mixed Reality headsets.</span></span> <span data-ttu-id="ced1a-149">若要在远程电脑上显示呈现的内容，通过实例的窗口交换链，全息远程处理提供了名为的第二个 OpenXR 扩展 ```XR_MSFT_holographic_remoting_frame_mirroring``` 。</span><span class="sxs-lookup"><span data-stu-id="ced1a-149">To also display the rendered content on the remote PC, via a swap-chain of a window for instance, Holographic Remoting provides a second OpenXR extension named ```XR_MSFT_holographic_remoting_frame_mirroring```.</span></span> <span data-ttu-id="ced1a-150">如果希望使用该功能，请确保也使用启用此扩展 ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` 。</span><span class="sxs-lookup"><span data-stu-id="ced1a-150">Ensure to also enable this extension using ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` in case you want to use that functionality.</span></span>

>[!IMPORTANT]
><span data-ttu-id="ced1a-151">若要了解全息远程处理 OpenXR 扩展 API，请查看可在[全息远程处理示例 github 存储库](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到的[规范](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html)。</span><span class="sxs-lookup"><span data-stu-id="ced1a-151">To learn about the Holographic Remoting OpenXR extension API, check out the [specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) which can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="connect-to-the-device"></a><span data-ttu-id="ced1a-152">连接到设备</span><span class="sxs-lookup"><span data-stu-id="ced1a-152">Connect to the device</span></span>

<span data-ttu-id="ced1a-153">远程应用创建 XrInstance 并通过 xrGetSystem 查询 XrSystemId 后，可以建立与播放机设备的连接。</span><span class="sxs-lookup"><span data-stu-id="ced1a-153">After your remote app has created the XrInstance and queried the XrSystemId via xrGetSystem a connection to the player device can be established.</span></span>

>[!WARNING]
> <span data-ttu-id="ced1a-154">全息远程处理 OpenXR 运行时在建立连接后，只能提供特定于设备的数据，例如查看配置或环境混合模式。</span><span class="sxs-lookup"><span data-stu-id="ced1a-154">The Holographic Remoting OpenXR runtime is only able to provide device specific data such as view configurations or environment blend modes after a connection has been established.</span></span> <span data-ttu-id="ced1a-155">```xrEnumerateViewConfigurations```、 ```xrEnumerateViewConfigurationViews``` 、 ```xrGetViewConfigurationProperties``` 、 ```xrEnumerateEnvironmentBlendModes``` 和 ```xrGetSystemProperties``` 将为你显示默认值，这与在完全连接之前连接到在 HoloLens 2 上运行的播放机时通常会获得的值相匹配。</span><span class="sxs-lookup"><span data-stu-id="ced1a-155">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews```, ```xrGetViewConfigurationProperties```, ```xrEnumerateEnvironmentBlendModes```, and ```xrGetSystemProperties``` will give you default values, matching what you would typically get if you connect to a player running on a HoloLens 2, before being fully connected.</span></span>
<span data-ttu-id="ced1a-156">强烈建议不要在建立连接之前调用这些方法。</span><span class="sxs-lookup"><span data-stu-id="ced1a-156">It is strongly recommended to not call these methods before a connection has been established.</span></span> <span data-ttu-id="ced1a-157">在成功创建 XrSession 并且会话状态至少为 XR_SESSION_STATE_READY 后，建议使用这些方法。</span><span class="sxs-lookup"><span data-stu-id="ced1a-157">The suggestion is use these methods after the XrSession has been successfully created and the session state is at least XR_SESSION_STATE_READY.</span></span>

<span data-ttu-id="ced1a-158">可以通过以下方式配置常规属性（例如最大比特率、启用音频、视频编解码器或深度缓冲流解析） ```xrRemotingSetContextPropertiesMSFT``` 。</span><span class="sxs-lookup"><span data-stu-id="ced1a-158">General properties such as max bitrate, audio enabled, video codec, or depth buffer stream resolution can be configured via ```xrRemotingSetContextPropertiesMSFT``` as follows.</span></span>

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

<span data-ttu-id="ced1a-159">可以通过以下两种方式之一来完成连接。</span><span class="sxs-lookup"><span data-stu-id="ced1a-159">The connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="ced1a-160">远程应用连接到设备上运行的播放机。</span><span class="sxs-lookup"><span data-stu-id="ced1a-160">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="ced1a-161">设备上运行的播放机连接到远程应用。</span><span class="sxs-lookup"><span data-stu-id="ced1a-161">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="ced1a-162">若要建立从远程应用到播放机设备的连接，请调用 ```xrRemotingConnectMSFT``` 方法，该方法通过结构指定主机名和端口  ```XrRemotingConnectInfoMSFT``` 。</span><span class="sxs-lookup"><span data-stu-id="ced1a-162">To establish a connection from the remote app to the player device call the ```xrRemotingConnectMSFT``` method specifying the hostname and port via the  ```XrRemotingConnectInfoMSFT``` structure.</span></span> <span data-ttu-id="ced1a-163">全息远程处理播放器使用的端口为 **8265**。</span><span class="sxs-lookup"><span data-stu-id="ced1a-163">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

<span data-ttu-id="ced1a-164">可以通过调用方法来侦听远程应用上的传入连接 ```xrRemotingListenMSFT``` 。</span><span class="sxs-lookup"><span data-stu-id="ced1a-164">Listening for incoming connections on the remote app can be done by calling the ```xrRemotingListenMSFT``` method.</span></span> <span data-ttu-id="ced1a-165">可以通过结构指定握手端口和传输端口 ```XrRemotingListenInfoMSFT``` 。</span><span class="sxs-lookup"><span data-stu-id="ced1a-165">Both the handshake port and transport port can be specified via the ```XrRemotingListenInfoMSFT``` structure.</span></span> <span data-ttu-id="ced1a-166">握手端口用于初始握手。</span><span class="sxs-lookup"><span data-stu-id="ced1a-166">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="ced1a-167">然后通过传输端口发送数据。</span><span class="sxs-lookup"><span data-stu-id="ced1a-167">The data is then send over the transport port.</span></span> <span data-ttu-id="ced1a-168">默认情况下，使用 **8265** 和 **8266** 。</span><span class="sxs-lookup"><span data-stu-id="ced1a-168">By default **8265** and **8266** are used.</span></span>

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

<span data-ttu-id="ced1a-169">在调用或时，必须断开连接状态 ```xrRemotingConnectMSFT``` ```xrRemotingListenMSFT``` 。</span><span class="sxs-lookup"><span data-stu-id="ced1a-169">The connection state must be disconnected when you call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT```.</span></span> <span data-ttu-id="ced1a-170">你可以在创建 XrInstance 后随时获取连接状态，并通过查询 XrSystemId ```xrRemotingGetConnectionStateMSFT``` 。</span><span class="sxs-lookup"><span data-stu-id="ced1a-170">You can get the connection state at any point after you have created a XrInstance and queried for the XrSystemId via ```xrRemotingGetConnectionStateMSFT```.</span></span>

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

<span data-ttu-id="ced1a-171">可用的连接状态为：</span><span class="sxs-lookup"><span data-stu-id="ced1a-171">Available connection states are:</span></span>
- <span data-ttu-id="ced1a-172">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="ced1a-172">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span></span>
- <span data-ttu-id="ced1a-173">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span><span class="sxs-lookup"><span data-stu-id="ced1a-173">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span></span>
- <span data-ttu-id="ced1a-174">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="ced1a-174">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span></span>

>[!IMPORTANT]
> <span data-ttu-id="ced1a-175">```xrRemotingConnectMSFT``````xrRemotingListenMSFT```尝试通过 xrCreateSession 创建 XrSession 之前，必须先调用或。</span><span class="sxs-lookup"><span data-stu-id="ced1a-175">```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` must be called before trying to create a XrSession via xrCreateSession.</span></span> <span data-ttu-id="ced1a-176">如果尝试在连接状态为时创建 XrSession，则 ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` 会话创建会成功，但会话状态将立即转换为 XR_SESSION_STATE_LOSS_PENDING。</span><span class="sxs-lookup"><span data-stu-id="ced1a-176">If you try to create a XrSession while the connection state is ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session creation will succeed but the session state will immediately transition to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="ced1a-177">全息远程处理的实现 ```xrCreateSession``` 支持等待建立连接。</span><span class="sxs-lookup"><span data-stu-id="ced1a-177">Holographic Remoting's implementation of ```xrCreateSession``` supports waiting for a connection to be established.</span></span> <span data-ttu-id="ced1a-178">可以调用， ```xrRemotingConnectMSFT``` 也可以立即调用， ```xrRemotingListenMSFT``` ```xrCreateSession``` 它会阻止并等待建立连接。</span><span class="sxs-lookup"><span data-stu-id="ced1a-178">You can call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` immediately followed by a call to ```xrCreateSession``` which will block and wait for a connection to be established.</span></span> <span data-ttu-id="ced1a-179">超时固定为10秒。</span><span class="sxs-lookup"><span data-stu-id="ced1a-179">The timeout is fixed to 10 seconds.</span></span> <span data-ttu-id="ced1a-180">如果在这段时间内可以建立连接，则 XrSession 创建将成功，并且会话状态将转换为 XR_SESSION_STATE_READY。</span><span class="sxs-lookup"><span data-stu-id="ced1a-180">If a connection can be established within this time the XrSession creation will succeed and the session state will transition to XR_SESSION_STATE_READY.</span></span> <span data-ttu-id="ced1a-181">如果无法建立连接，则会话创建也会成功，但会立即转换为 XR_SESSION_STATE_LOSS_PENDING。</span><span class="sxs-lookup"><span data-stu-id="ced1a-181">In case no connection can be established the session creation also succeeds but immediately transitions to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="ced1a-182">通常，连接状态为 XrSession 状态的几个。</span><span class="sxs-lookup"><span data-stu-id="ced1a-182">In general the connection state is couple with the XrSession state.</span></span> <span data-ttu-id="ced1a-183">对连接状态所做的任何更改也会影响会话状态。</span><span class="sxs-lookup"><span data-stu-id="ced1a-183">Any change to the connection state also affects the session state.</span></span> <span data-ttu-id="ced1a-184">例如，如果连接状态从切换 `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` 到 ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` 会话状态，则也会转换为 XR_SESSION_STATE_LOSS_PENDING。</span><span class="sxs-lookup"><span data-stu-id="ced1a-184">For instance, if the connection state switches from `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` to ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session state will transition to XR_SESSION_STATE_LOSS_PENDING as well.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="ced1a-185">处理特定于远程处理的事件</span><span class="sxs-lookup"><span data-stu-id="ced1a-185">Handling Remoting specific events</span></span>

<span data-ttu-id="ced1a-186">全息远程处理 OpenXR 运行时公开三个事件，这些事件对于监视连接状态很重要。</span><span class="sxs-lookup"><span data-stu-id="ced1a-186">The Holographic Remoting OpenXR runtime exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="ced1a-187">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```：已成功建立与设备的连接时触发。</span><span class="sxs-lookup"><span data-stu-id="ced1a-187">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Triggered when a connection to the device has been successfully established.</span></span>
2) <span data-ttu-id="ced1a-188">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```：如果已建立的连接已关闭或无法建立连接，则触发。</span><span class="sxs-lookup"><span data-stu-id="ced1a-188">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Triggered if an established connection is closed or a connection could not be established.</span></span>
3) <span data-ttu-id="ced1a-189">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```：侦听传入连接启动时。</span><span class="sxs-lookup"><span data-stu-id="ced1a-189">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: When listening for incoming connections starts.</span></span>

<span data-ttu-id="ced1a-190">这些事件放置在队列中，远程应用必须通过规律性从队列中读取 ```xrPollEvent``` 。</span><span class="sxs-lookup"><span data-stu-id="ced1a-190">These events are placed in a queue and your remote app must read from the queue with regularity via ```xrPollEvent```.</span></span>

```cpp
auto pollEvent = [&](XrEventDataBuffer& eventData) -> bool {
    eventData.type = XR_TYPE_EVENT_DATA_BUFFER;
    eventData.next = nullptr;
    return CHECK_XRCMD(xrPollEvent(m_instance.Get(), &eventData)) == XR_SUCCESS;
};

XrEventDataBuffer eventData{};
while (pollEvent(eventData)) {
    switch (eventData.type) {
    
    ...
    
    case XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Listening on port %d",
                    reinterpret_cast<const XrRemotingEventDataListeningMSFT*>(&eventData)->listeningPort);
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Connected.");
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Disconnected - Reason: %d",
                    reinterpret_cast<const XrRemotingEventDataDisconnectedMSFT*>(&eventData)->disconnectReason);
        break;
    }
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="ced1a-191">在本地预览流式处理内容</span><span class="sxs-lookup"><span data-stu-id="ced1a-191">Preview streamed content locally</span></span>

<span data-ttu-id="ced1a-192">若要在发送到设备的远程应用中显示相同的内容， ```XR_MSFT_holographic_remoting_frame_mirroring``` 可使用扩展。</span><span class="sxs-lookup"><span data-stu-id="ced1a-192">To display the same content in the remote app that is send to the device the ```XR_MSFT_holographic_remoting_frame_mirroring``` extension can be used.</span></span> <span data-ttu-id="ced1a-193">使用此扩展可以向 xrEndFrame 提交纹理。</span><span class="sxs-lookup"><span data-stu-id="ced1a-193">With this extension you can submit a texture to xrEndFrame.</span></span> <span data-ttu-id="ced1a-194">这是通过使用 ```XrRemotingFrameMirrorImageInfoMSFT``` 链接到 XrFrameEndInfo 的结构来完成的，如下所示。</span><span class="sxs-lookup"><span data-stu-id="ced1a-194">This is done by using the ```XrRemotingFrameMirrorImageInfoMSFT``` structure which is chained to the XrFrameEndInfo as follows.</span></span>

```cpp
XrFrameEndInfo frameEndInfo{XR_TYPE_FRAME_END_INFO};
...

XrRemotingFrameMirrorImageD3D11MSFT mirrorImageD3D11{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_D3D11_MSFT)};
mirrorImageD3D11.texture = m_window->GetNextSwapchainTexture();

XrRemotingFrameMirrorImageInfoMSFT mirrorImageEndInfo{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_INFO_MSFT)};
mirrorImageEndInfo.image = reinterpret_cast<const XrRemotingFrameMirrorImageBaseHeaderMSFT*>(&mirrorImageD3D11);

frameEndInfo.next = &mirrorImageEndInfo;

xrEndFrame(m_session.Get(), &frameEndInfo);

m_window->PresentSwapchain();
```

<span data-ttu-id="ced1a-195">上面的示例使用 DX11 交换链纹理，并在调用 xrEndFrame 后立即显示该窗口。</span><span class="sxs-lookup"><span data-stu-id="ced1a-195">The example above uses a DX11 swap-chain texture and presents the window immediately after the call to xrEndFrame.</span></span> <span data-ttu-id="ced1a-196">使用不限于交换链纹理，无需额外的 GPU 同步。</span><span class="sxs-lookup"><span data-stu-id="ced1a-196">The usage is not restricted to swap-chain textures and no additional GPU synchronization is required.</span></span> <span data-ttu-id="ced1a-197">有关使用情况和约束的详细信息，请参阅 [扩展规范](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring)。</span><span class="sxs-lookup"><span data-stu-id="ced1a-197">For details on usage and constraints check out the [extension specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span></span>
<span data-ttu-id="ced1a-198">如果远程应用使用的是 DX12，请使用 XrRemotingFrameMirrorImageD3D12MSFT 而不是 XrRemotingFrameMirrorImageD3D11MSFT。</span><span class="sxs-lookup"><span data-stu-id="ced1a-198">If your remote app is using DX12 use XrRemotingFrameMirrorImageD3D12MSFT instead of XrRemotingFrameMirrorImageD3D11MSFT.</span></span>

## <a name="see-also"></a><span data-ttu-id="ced1a-199">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ced1a-199">See Also</span></span>
* [<span data-ttu-id="ced1a-200">编写自定义全息远程处理播放器应用</span><span class="sxs-lookup"><span data-stu-id="ced1a-200">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="ced1a-201">使用全息远程处理建立安全连接</span><span class="sxs-lookup"><span data-stu-id="ced1a-201">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="ced1a-202">全息远程处理故障排除和限制</span><span class="sxs-lookup"><span data-stu-id="ced1a-202">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="ced1a-203">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="ced1a-203">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="ced1a-204">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="ced1a-204">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
