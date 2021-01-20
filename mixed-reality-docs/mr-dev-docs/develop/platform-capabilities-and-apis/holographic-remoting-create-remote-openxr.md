---
title: '编写全息远程处理远程应用 (OpenXR) '
description: 了解如何使用 OpenXR 将远程计算机上呈现的远程内容流式传输到 HoloLens 2，并将其与全息远程应用进行流式处理。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens，远程处理，全息远程处理，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，NuGet
ms.openlocfilehash: da3114b2c8c4e04d8da9296687f92d0b23945281
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581237"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>使用 OpenXR API 编写全息远程处理远程应用

>[!IMPORTANT]
>本文档介绍了如何使用 [OPENXR API](../native/openxr.md)为 HoloLens 2 和 Windows Mixed Reality 耳机创建远程应用程序。 **HoloLens (第一代)** 的远程应用程序必须使用 NuGet **包版本1.x。** 这意味着，为 HoloLens 2 编写的远程应用程序与 HoloLens 1 不兼容，反之亦然。 可在 [此处](add-holographic-remoting.md)找到 HoloLens 1 的文档。

全息远程处理应用可将远程呈现的内容流式传输到 HoloLens 2 和 Windows Mixed Reality 沉浸式头。 你还可以访问更多系统资源，并将远程 [沉浸式视图](../../design/app-views.md) 集成到现有的台式计算机软件中。 远程应用从 HoloLens 2 接收输入数据流，在虚拟沉浸式视图中呈现内容，并将内容帧流式传输回 HoloLens 2。 使用标准 Wi-fi 建立连接。 全息远程处理通过 NuGet 数据包添加到桌面或 UWP 应用。 需要其他代码来处理连接并在沉浸式视图中呈现。 典型的远程处理连接的延迟最低为50毫秒。 播放机应用可以实时报告滞后时间。

此页面上的所有代码和工作项目都可以在 " [全息远程处理示例 github 存储库](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)" 中找到。

## <a name="prerequisites"></a>先决条件

好的起点是基于 OpenXR 的桌面或 UWP 应用。 有关详细信息，请参阅 [OpenXR](../native/openxr-getting-started.md)入门。

>[!IMPORTANT]
>使用全息远程处理的任何应用都应该编写为使用 [多线程单元](//windows/win32/com/multithreaded-apartments)。 支持使用 [单线程单元](//windows/win32/com/single-threaded-apartments) ，但会导致在播放过程中出现欠最佳的性能，并且可能会断断续续。 使用 c + +/WinRT [WinRT：： init_apartment](//windows/uwp/cpp-and-winrt-apis/get-started) 多线程单元是默认值。

## <a name="get-the-holographic-remoting-nuget-package"></a>获取全息远程处理 NuGet 包

将 NuGet 包添加到 Visual Studio 中的项目时需要执行以下步骤。
1. 在 Visual Studio 中打开项目。
2. 右键单击项目节点，然后选择 "**管理 NuGet 包 ...** "
3. 在出现的面板中，选择 " **浏览** "，然后搜索 "全息远程处理"。
4. 选择 " **OpenXr**"，确保 **选择最新** 的2.x 版本，并选择 " **安装**"。
5. 如果显示 " **预览** " 对话框，请选择 **"确定"**。
6. 弹出 "许可协议" 对话框后，选择 " **我接受** "。
7. 对以下 NuGet 包重复步骤3到6： OpenXR、OpenXR

>[!NOTE]
>NuGet 包的版本1.x 仍适用于想要面向 HoloLens **1 的开发** 人员。 有关详细信息，请参阅 [将全息远程处理 (HoloLens (第一代) # B3 ](add-holographic-remoting.md)。

## <a name="select-the-holographic-remoting-openxr-runtime"></a>选择全息远程处理 OpenXR 运行时

在远程应用程序中需要执行的第一步是选择全息远程处理 OpenXR 运行时，这是 OpenXr NuGet 包的一部分。 为此，可以将 ```XR_RUNTIME_JSON``` 环境变量设置为应用中文件的 RemotingXR.js路径。 OpenXR 加载程序使用此环境变量来不使用系统默认 OpenXR 运行时，而是重定向到全息远程处理 OpenXR 运行时。 使用 OpenXr NuGet 包时，文件中的 RemotingXR.js会自动复制到输出文件夹，OpenXR 运行时选择通常如下所示。

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

## <a name="create-xrinstance-with-holographic-remoting-extension"></a>创建包含全息远程处理扩展的 XrInstance

典型的 OpenXR 应用程序的第一步是选择 OpenXR 扩展并创建 XrInstance。 OpenXR 核心规范不提供任何远程处理特定的 API。 出于此原因，全息远程处理会引入其自己的名为的 OpenXR 扩展 ```XR_MSFT_holographic_remoting``` 。 确保在调用 xrCreateInstance 时， ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` 包含在 XrInstanceCreateInfo 中。

>[!TIP]
>默认情况下，只会将应用程序的呈现内容传输到在 HoloLens 2 上或在 Windows Mixed Reality 耳机上运行的全息远程处理播放机。 若要在远程电脑上显示呈现的内容，通过实例的窗口交换链，全息远程处理提供了名为的第二个 OpenXR 扩展 ```XR_MSFT_holographic_remoting_frame_mirroring``` 。 如果希望使用该功能，请确保也使用启用此扩展 ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` 。

>[!IMPORTANT]
>若要了解全息远程处理 OpenXR 扩展 API，请查看可在[全息远程处理示例 github 存储库](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中找到的[规范](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html)。

## <a name="connect-to-the-device"></a>连接到设备

远程应用创建 XrInstance 并通过 xrGetSystem 查询 XrSystemId 后，可以建立与播放机设备的连接。

>[!WARNING]
> 全息远程处理 OpenXR 运行时在建立连接后，只能提供特定于设备的数据，例如查看配置或环境混合模式。 ```xrEnumerateViewConfigurations```、 ```xrEnumerateViewConfigurationViews``` 、 ```xrGetViewConfigurationProperties``` 、 ```xrEnumerateEnvironmentBlendModes``` 和 ```xrGetSystemProperties``` 将为你显示默认值，这与在完全连接之前连接到在 HoloLens 2 上运行的播放机时通常会获得的值相匹配。
强烈建议不要在建立连接之前调用这些方法。 在成功创建 XrSession 并且会话状态至少为 XR_SESSION_STATE_READY 后，将使用这些方法。

可以通过以下方式配置常规属性（例如最大比特率、启用音频、视频编解码器或深度缓冲流解析） ```xrRemotingSetContextPropertiesMSFT``` 。

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

可以通过以下两种方式之一来完成连接。
1) 远程应用连接到设备上运行的播放机。
2) 设备上运行的播放机连接到远程应用。

若要建立从远程应用到播放机设备的连接，请调用 ```xrRemotingConnectMSFT``` 方法，该方法通过结构指定主机名和端口  ```XrRemotingConnectInfoMSFT``` 。 全息远程处理播放器使用的端口为 **8265**。

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

可以通过调用方法来侦听远程应用上的传入连接 ```xrRemotingListenMSFT``` 。 可以通过结构指定握手端口和传输端口 ```XrRemotingListenInfoMSFT``` 。 握手端口用于初始握手。 然后通过传输端口发送数据。 默认情况下，使用 **8265** 和 **8266** 。

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

在调用或时，必须断开连接状态 ```xrRemotingConnectMSFT``` ```xrRemotingListenMSFT``` 。 你可以在创建 XrInstance 后随时获取连接状态，并通过查询 XrSystemId ```xrRemotingGetConnectionStateMSFT``` 。

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

可用的连接状态为：
- XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT

>[!IMPORTANT]
> ```xrRemotingConnectMSFT``````xrRemotingListenMSFT```尝试通过 xrCreateSession 创建 XrSession 之前，必须先调用或。 如果尝试在连接状态为时创建 XrSession，则 ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` 会话创建会成功，但会话状态将立即转换为 XR_SESSION_STATE_LOSS_PENDING。

全息远程处理的实现 ```xrCreateSession``` 支持等待建立连接。 可以调用 ```xrRemotingConnectMSFT``` ，也可以 ```xrRemotingListenMSFT``` 立即调用，这将阻止并等待建立连接。 超时固定为10秒。 如果在这段时间内可以建立连接，则 XrSession 创建将成功，并且会话状态将转换为 XR_SESSION_STATE_READY。 如果无法建立连接，则会话创建也会成功，但会立即转换为 XR_SESSION_STATE_LOSS_PENDING。

通常，连接状态为 XrSession 状态的几个。 对连接状态所做的任何更改也会影响会话状态。 例如，如果连接状态从切换 `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` 到 ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` 会话状态，则也会转换为 XR_SESSION_STATE_LOSS_PENDING。

## <a name="handling-remoting-specific-events"></a>处理特定于远程处理的事件

全息远程处理 OpenXR 运行时公开了三个事件，这些事件对于监视连接状态很重要。
1) ```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```：已成功建立与设备的连接时触发。
2) ```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```：如果已建立的连接已关闭或无法建立连接，则触发。
3) ```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```：侦听传入连接启动时。

这些事件放置在队列中，远程应用必须通过规律性从队列中读取 ```xrPollEvent``` 。

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

## <a name="preview-streamed-content-locally"></a>在本地预览流式处理内容

若要在发送到设备的远程应用中显示相同的内容， ```XR_MSFT_holographic_remoting_frame_mirroring``` 可使用扩展。 使用此扩展，你可以使用 ```XrRemotingFrameMirrorImageInfoMSFT``` 未链接到 XrFrameEndInfo 的 xrEndFrame 将纹理提交到，如下所示。

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

上面的示例使用 DX11 交换链纹理，并在调用 xrEndFrame 后立即显示该窗口。 使用不限于交换链纹理，无需额外的 GPU 同步。 有关使用情况和约束的详细信息，请参阅 [扩展规范](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring)。
如果远程应用使用的是 DX12，请使用 XrRemotingFrameMirrorImageD3D12MSFT 而不是 XrRemotingFrameMirrorImageD3D11MSFT。

## <a name="see-also"></a>另请参阅
* [编写自定义全息远程处理播放器应用](holographic-remoting-create-player.md)
* [使用全息远程处理建立安全连接](holographic-remoting-secure-connection.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)