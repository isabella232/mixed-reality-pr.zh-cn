---
title: '将全息远程处理远程应用 (WMR) '
description: 了解如何流式传输远程计算机上呈现的远程内容，HoloLens 2 HolographicSpace 使用全息远程处理应用。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备NuGet
ms.openlocfilehash: 0d8f7149533de7f3f095761b13feeb91c319cda711c99b9101a13300a591fc2c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219211"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a>使用 HolographicSpace API 编写全息远程处理远程应用

>[!IMPORTANT]
>本文档介绍如何使用[HolographicSpace API](../native/getting-a-holographicspace.md)为 HoloLens 2远程应用程序。 第一代 **HoloLens (远程**) 必须使用NuGet **1.x.x 版**。 这意味着，为 HoloLens 2 编写的远程应用程序与 HoloLens 1 不兼容，反之亦然。 有关 HoloLens 1 的文档，可[在此处找到](add-holographic-remoting.md)。

全息远程处理应用可以将远程渲染的内容流式HoloLens 2 Windows Mixed Reality沉浸式头戴显示设备。 还可以访问更多系统资源，并将远程 [沉浸式视图集成到](../../design/app-views.md) 现有的桌面电脑软件中。 远程应用从 HoloLens 2 接收输入数据流，在虚拟沉浸式视图中呈现内容，将内容帧流式传输回HoloLens 2。 使用标准 Wi-Fi 建立连接。 全息远程处理通过数据包添加到桌面或 UWP NuGet应用。 需要其他代码来处理连接，并呈现在沉浸式视图中。 典型的远程处理连接延迟最低为 50 毫秒。 播放器应用可以实时报告延迟。

可在全息远程处理示例 [github](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)存储库 找到此页上的所有代码和工作项目。

## <a name="prerequisites"></a>先决条件

一个很好的起点是基于 DirectX 的桌面或 UWP 应用，它面向 [HolographicSpace API](../native/getting-a-holographicspace.md)。 有关详细信息，请参阅 [DirectX 开发概述](../native/directx-development-overview.md)。 [C++ 全息项目模板](../native/creating-a-holographic-directx-project.md)是一个很好的起点。

>[!IMPORTANT]
>任何使用全息远程处理的应用都应创作为使用多 [线程单元](/windows/win32/com/multithreaded-apartments)。 支持使用 [单线程单元](/windows/win32/com/single-threaded-apartments) ，但会导致性能降低，并且可能在播放期间造成异常。 使用 C++/WinRT [winrt：：init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) 多线程单元是默认值。



## <a name="get-the-holographic-remoting-nuget-package"></a>获取全息远程处理NuGet包

若要将包添加到 NuGet 中的项目，需要执行Visual Studio。
1. 在 Visual Studio 中打开项目。
2. 右键单击项目节点，然后选择"管理NuGet **包..."**
3. 在出现的面板中，选择" **浏览"，** 然后搜索"全息远程处理"。
4. 选择 **"Microsoft.Holographic.Remoting"，** 确保选择最新的 **2.x.x** 版本，然后选择"安装 **"。**
5. 如果显示 **"预览"** 对话框，请选择"确定 **"。**
6. 在 **弹出许可协议** 对话框时，选择"我接受"。

>[!NOTE]
>版本 **1.x.x** 的 NuGet 仍适用于想要面向 1 HoloLens的开发人员。 有关详细信息，请参阅[添加全息远程处理 (HoloLens (第一代) ) 。 ](add-holographic-remoting.md)

## <a name="create-the-remote-context"></a>创建远程上下文

作为第一步，应用程序应创建远程上下文。

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
>全息远程处理的工作原理是Windows Mixed Reality远程处理特定运行时Windows的一部分。 此操作是在创建远程上下文期间完成。 因此，在创建远程上下文之前Windows Mixed Reality API 的任何调用都可能会导致意外行为。 建议的方法是在与任何混合现实 API 交互之前尽早创建远程上下文。 在调用 CreateRemoteContext 之前，切勿将通过任何 Windows Mixed Reality API 创建或检索的对象与之后创建或检索的对象混合使用。

接下来需要创建全息空间。 不需要指定 CoreWindow。 没有 CoreWindow 的桌面应用只需传递 ```nullptr``` 。

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>连接设备

当远程应用准备好呈现内容时，可以建立与播放器设备的连接。

可以通过两种方式之一完成连接。
1) 远程应用连接到设备上运行的播放器。
2) 设备上运行的播放器连接到远程应用。

若要建立从远程应用到播放器设备的连接，请对远程上下文调用 方法，指定 ```Connect``` 主机名和端口。 全息远程处理播放器使用的端口为 **8265。**

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
>与任何 C++/WinRT API 一样，可能会引发 ```Connect``` winrt：：hresult_error需要处理。

>[!TIP]
>若要避免使用[C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)语言投影，可以包括全息远程处理包 ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` NuGet文件。 它包含基础 COM 接口的声明。 不过，建议使用 C++/WinRT。

可以通过调用 方法在远程应用上侦听传入 ```Listen``` 连接。 在此调用过程中，可以同时指定握手端口和传输端口。 握手端口用于初始握手。 然后，通过传输端口发送数据。 默认使用 **8265** **和 8266。**

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
>应用程序 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 包NuGet包含全息远程处理公开的 API 的详细文档。

## <a name="handling-remoting-specific-events"></a>处理远程处理特定事件

远程上下文公开三个事件，这些事件对于监视连接状态非常重要。
1) OnConnected：成功建立与设备的连接时触发。
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) OnDisconnected：如果已建立的连接已关闭或无法建立连接，则触发。
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
3) OnListening：开始侦听传入连接时。
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

此外，可以使用远程上下文中的 属性 ```ConnectionState``` 查询连接状态。
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>处理语音事件

使用远程语音接口，可以注册语音触发器HoloLens 2远程应用程序。

需要此附加成员来跟踪远程语音的状态。

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

首先需要检索远程语音接口。

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

然后，可以使用异步帮助程序方法初始化远程语音。 这应该异步完成，因为初始化可能需要相当长的时间。 [使用 C++/WinRT 的并发和](/windows/uwp/cpp-and-winrt-apis/concurrency) 异步操作介绍了如何使用 C++/WinRT 创作异步函数。

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

有两种方法可以指定要识别的短语。
1) 语音语法 xml 文件内的规范。 有关详细信息 [，请参阅如何创建基本 XML](/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) 语法。
2) 通过将它们传递到 字典向量中来指定 ```ApplyParameters``` 。

在 OnRecognizedSpeech 回调中，可以处理语音事件：

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

## <a name="preview-streamed-content-locally"></a>在本地预览流式处理的内容

若要在发送到设备的远程应用中显示相同的内容，可以使用远程 ```OnSendFrame``` 上下文的事件。 每次全息远程处理库将当前帧发送到远程设备时，都会 ```OnSendFrame``` 触发该事件。 这是将内容放入桌面或 UWP 窗口的理想时间。

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

## <a name="depth-reprojection"></a>深度重现

从版本 [2.1.0](holographic-remoting-version-history.md#v2.1.0)开始，全息远程处理支持 [深度重新投影](hologram-stability.md#reprojection)。 这要求将颜色缓冲区和深度缓冲区从远程应用程序流式处理到HoloLens 2。 默认情况下，启用深度缓冲区流式处理，并配置为使用颜色缓冲区的一半分辨率。 这一点可更改，如下所示：

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

请注意，如果不应使用默认值，则必须在建立与 HoloLens 2 ```ConfigureDepthVideoStream``` 的连接之前调用。 最佳位置是在创建远程上下文之后。 DepthBufferStreamResolution 的可能值为：

* Full_Resolution
* Half_Resolution
* Quarter_Resolution
* 已禁用 ([版本 2.1.3，](holographic-remoting-version-history.md#v2.1.3) 如果使用，则不创建其他深度视频) 

请记住，使用全分辨率深度缓冲区也会影响带宽要求，需要在提供的最大带宽值中考虑到这一点 ```CreateRemoteContext``` 。

除了配置分辨率外，还必须通过 [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)提交深度缓冲区。

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

若要验证深度重新保护是否HoloLens 2，可以通过以下工具启用深度可视化设备门户。 有关详细信息 [，请参阅验证深度是否已正确](hologram-stability.md#verifying-depth-is-set-correctly) 设置。

## <a name="optional-custom-data-channels"></a>可选：自定义数据通道

自定义数据信道可用于通过已建立的远程处理连接发送用户数据。 有关详细信息，请参阅 [自定义数据通道](holographic-remoting-custom-data-channels.md) 。

## <a name="see-also"></a>另请参阅
* [编写自定义全息远程处理播放器应用](holographic-remoting-create-player.md)
* [自定义全息远程处理数据通道](holographic-remoting-custom-data-channels.md)
* [使用全息远程处理建立安全连接](holographic-remoting-secure-connection.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)