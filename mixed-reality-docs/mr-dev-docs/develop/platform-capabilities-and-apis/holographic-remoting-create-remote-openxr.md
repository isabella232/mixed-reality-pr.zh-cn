---
title: '使用 OpenXR (全息远程处理) '
description: 了解如何流式传输远程计算机上呈现的远程内容，HoloLens 2 OpenXR 的全息远程处理应用。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备NuGet
ms.openlocfilehash: 6cf44bd031aec4b475d7496a999a3c7d4d40cae7cc921ff39cfe61698f3dd532
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212065"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>使用 OpenXR API 编写全息远程处理远程应用

>[!IMPORTANT]
>本文档介绍如何使用[OpenXR API](../native/openxr.md)为 HoloLens 2 Windows Mixed Reality头戴显示设备创建远程应用程序。 第一代 **HoloLens (远程**) 必须使用NuGet **1.x.x 版**。 这意味着，为 HoloLens 2 编写的远程应用程序与 HoloLens 1 不兼容，反之亦然。 有关 HoloLens 1 的文档，可[在此处找到](add-holographic-remoting.md)。

全息远程处理应用可以将远程渲染的内容流式HoloLens 2 Windows Mixed Reality沉浸式头戴显示设备。 还可以访问更多系统资源，并将远程 [沉浸式视图集成到](../../design/app-views.md) 现有的桌面电脑软件中。 远程应用从 HoloLens 2 接收输入数据流，在虚拟沉浸式视图中呈现内容，将内容帧流式传输回HoloLens 2。 使用标准 Wi-Fi 建立连接。 全息远程处理通过数据包添加到桌面或 UWP NuGet应用。 需要其他代码来处理连接，并呈现在沉浸式视图中。 典型的远程处理连接延迟最低为 50 毫秒。 播放器应用可以实时报告延迟。

可在全息远程处理示例 [github](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)存储库 找到此页上的所有代码和工作项目。

## <a name="prerequisites"></a>先决条件

一个很好的起点是基于 OpenXR 的桌面或 UWP 应用。 有关详细信息， [请参阅 OpenXR 入门](../native/openxr-getting-started.md)。

>[!IMPORTANT]
>任何使用全息远程处理的应用都应创作为使用多 [线程单元](/windows/win32/com/multithreaded-apartments)。 支持使用 [单线程单元](/windows/win32/com/single-threaded-apartments) ，但会导致性能降低，并且可能在播放期间造成异常。 使用 C++/WinRT [winrt：：init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) 多线程单元是默认值。

## <a name="get-the-holographic-remoting-nuget-package"></a>获取全息远程处理NuGet包

若要将包添加到 NuGet 中的项目，需要执行Visual Studio。
1. 在 Visual Studio 中打开项目。
2. 右键单击项目节点，然后选择"管理NuGet **包..."**
3. 在出现的面板中，选择" **浏览"，** 然后搜索"全息远程处理"。
4. 选择 **"Microsoft.Holographic.Remoting.OpenXr"，** 确保选择最新的 **2.x.x** 版本，然后选择"安装 **"。**
5. 如果显示 **"预览"** 对话框，请选择"确定 **"。**
6. 在 **弹出许可协议** 对话框时，选择"我接受"。
7. 针对以下包重复步骤 3 到 6 NuGet：OpenXR.Headers、OpenXR.Loader

>[!NOTE]
>版本 **1.x.x** 的 NuGet 仍适用于想要面向 1 HoloLens的开发人员。 有关详细信息，请参阅[添加全息远程处理 (HoloLens (第一代) ) 。 ](add-holographic-remoting.md)

## <a name="select-the-holographic-remoting-openxr-runtime"></a>选择全息远程处理 OpenXR 运行时

需要在远程应用中执行的第一步是选择全息远程处理 OpenXR 运行时，该运行时是 Microsoft.Holographic.Remoting.OpenXr NuGet包的一部分。 为此，可以将环境变量设置为应用内RemotingXR.js```XR_RUNTIME_JSON``` 文件的路径。 OpenXR 加载程序使用此环境变量来不使用系统默认 OpenXR 运行时，而是重定向到全息远程处理 OpenXR 运行时。 使用 Microsoft.Holographic.Remoting.OpenXr NuGet 包时，编译期间会自动将 RemotingXR.json 文件复制到输出文件夹，OpenXR 运行时选择通常如下所示。

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

## <a name="create-xrinstance-with-holographic-remoting-extension"></a>使用全息远程处理扩展创建 XrInstance

典型的 OpenXR 应用应该执行的第一步是选择 OpenXR 扩展并创建 XrInstance。 OpenXR 核心规范不提供任何特定于远程处理的 API。 因此，全息远程处理引入了自己的名为 的 OpenXR 扩展 ```XR_MSFT_holographic_remoting``` 。 确保在调用 xrCreateInstance 时 ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` ，XrInstanceCreateInfo 中包含 。

>[!TIP]
>默认情况下，应用的呈现内容仅流式传输至在远程设备或 Windows Mixed Reality 头戴显示设备上运行的全息远程HoloLens 2播放器。 为了在远程电脑上显示呈现的内容，例如，通过窗口的交换链，全息远程处理提供了名为 的第二个 OpenXR 扩展 ```XR_MSFT_holographic_remoting_frame_mirroring``` 。 如果想使用该功能，请确保也使用 ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` 启用此扩展。

>[!IMPORTANT]
>若要了解全息远程处理 OpenXR 扩展 API，请查看可在全息远程[](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html)处理示例 github 存储库 找到[的规范](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)。

## <a name="connect-to-the-device"></a>连接设备

远程应用创建 XrInstance 并查询 XrSystemId 后，可通过 xrGetSystem 建立与播放器设备的连接。

>[!WARNING]
> 全息远程处理 OpenXR 运行时只能在建立连接后提供设备特定的数据，例如视图配置或环境混合模式。 ```xrEnumerateViewConfigurations```、、、 和 将提供默认值，与在完全连接之前连接到在 HoloLens 2 上运行的播放器时 ```xrEnumerateViewConfigurationViews``` ```xrGetViewConfigurationProperties``` ```xrEnumerateEnvironmentBlendModes``` ```xrGetSystemProperties``` 通常获得的值匹配。
强烈建议在建立连接之前不调用这些方法。 成功创建 XrSession 并且会话状态至少为 XR_SESSION_STATE_READY。

可通过 配置常规属性，例如最大比特率、已启用音频、视频编解码器或深度缓冲区流 ```xrRemotingSetContextPropertiesMSFT``` 分辨率，如下所示。

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

可以通过以下两种方式之一完成连接。
1) 远程应用连接到设备上运行的播放器。
2) 设备上运行的播放器连接到远程应用。

若要建立从远程应用到播放器设备的连接，请调用 方法，通过 结构指定主机名 ```xrRemotingConnectMSFT``` 和  ```XrRemotingConnectInfoMSFT``` 端口。 全息远程处理播放器使用的端口为 **8265。**

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

可以通过调用 方法在远程应用上侦听传入 ```xrRemotingListenMSFT``` 连接。 可以通过 结构指定握手端口和传输 ```XrRemotingListenInfoMSFT``` 端口。 握手端口用于初始握手。 然后，通过传输端口发送数据。 默认使用 **8265** **和 8266。**

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

调用 或 时，连接状态必须 ```xrRemotingConnectMSFT``` 断开连接 ```xrRemotingListenMSFT``` 。 创建 XrInstance 并查询 XrSystemId 后，随时都可以获取连接状态 ```xrRemotingGetConnectionStateMSFT``` 。

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

可用连接状态包括：
- XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT

>[!IMPORTANT]
> ```xrRemotingConnectMSFT``````xrRemotingListenMSFT```在尝试通过 xrCreateSession 创建 XrSession 之前，必须调用 或 。 如果在连接状态为 时尝试创建 XrSession，则会话创建将成功，但会话状态将立即转换为 ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` XR_SESSION_STATE_LOSS_PENDING。

全息远程处理的 实现 ```xrCreateSession``` 支持等待建立连接。 可以调用 ```xrRemotingConnectMSFT``` 或 ```xrRemotingListenMSFT``` ，然后立即调用 ，这将阻止并等待建立连接。 超时固定为 10 秒。 如果此时可以建立连接，则 XrSession 创建将成功，并且会话状态将转换为XR_SESSION_STATE_READY。 如果无法建立连接，则会话创建也会成功，但会立即转换为XR_SESSION_STATE_LOSS_PENDING。

一般情况下，连接状态与 XrSession 状态是耦合的。 对连接状态的任何更改也会影响会话状态。 例如，如果连接状态从 切换到会话 `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` 状态，则也会XR_SESSION_STATE_LOSS_PENDING转换。

## <a name="handling-remoting-specific-events"></a>处理远程处理特定事件

全息远程处理 OpenXR 运行时公开三个事件，这三个事件对于监视连接状态非常重要。
1) ```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```：在成功建立与设备的连接时触发。
2) ```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```：如果已建立的连接已关闭或无法建立连接，则触发。
3) ```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```：开始侦听传入连接时。

这些事件放置在队列中，远程应用必须通过 定期从队列中读取 ```xrPollEvent``` 。

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

## <a name="preview-streamed-content-locally"></a>在本地预览流式处理的内容

若要在发送到设备的远程应用中显示相同的内容， ```XR_MSFT_holographic_remoting_frame_mirroring``` 可以使用扩展。 使用此扩展，可以使用未链接至 XrFrameEndInfo 的 将纹理提交到 ```XrRemotingFrameMirrorImageInfoMSFT``` xrEndFrame，如下所示。

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

上面的示例使用 DX11 交换链纹理，在调用 xrEndFrame 后立即显示窗口。 此用法不限于交换链纹理，也不需要额外的 GPU 同步。 有关用法和约束的详细信息，请查看扩展 [规范](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring)。
如果远程应用使用的是 DX12，请使用 XrRemotingFrameMirrorImageD3D12MSFT，而不是 XrRemotingFrameMirrorImageD3D11MSFT。

## <a name="see-also"></a>另请参阅
* [编写自定义全息远程处理播放器应用](holographic-remoting-create-player.md)
* [使用全息远程处理建立安全连接](holographic-remoting-secure-connection.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)