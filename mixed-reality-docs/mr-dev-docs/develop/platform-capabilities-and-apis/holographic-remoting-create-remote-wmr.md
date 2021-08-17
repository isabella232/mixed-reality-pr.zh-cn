---
title: '编写全息远程处理远程应用 (WMR) '
description: 了解如何流式传输远程计算机上呈现的远程内容，以使用 HolographicSpace 与全息远程处理应用程序 HoloLens 2。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens，远程处理，全息远程处理，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，NuGet
ms.openlocfilehash: 0c5943ff92ce797e39ec0d2d98c129fa91eb3f14
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184718"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a>使用 HolographicSpace API 编写全息远程处理远程应用

>[!IMPORTANT]
>本文档介绍如何使用[HolographicSpace API](../native/getting-a-holographicspace.md)创建用于 HoloLens 2 的远程应用程序。 适用于 **HoloLens (1 代)** 的远程应用程序必须使用 NuGet 包版本 1.x. x. x. x. x. **x**。 这意味着，为 HoloLens 2 编写的远程应用程序与 HoloLens 1 不兼容，反之亦然。 可在[此处](add-holographic-remoting.md)找到 HoloLens 1 的文档。

全息远程处理应用可将远程呈现的内容流式传输到 HoloLens 2 和 Windows Mixed Reality 沉浸式耳机。 你还可以访问更多系统资源，并将远程 [沉浸式视图](../../design/app-views.md) 集成到现有的台式计算机软件中。 远程应用从 HoloLens 2 接收输入数据流，在虚拟沉浸式视图中呈现内容，并将内容帧流回 HoloLens 2。 使用标准 Wi-fi 建立连接。 全息远程处理通过 NuGet 数据包添加到桌面或 UWP 应用。 需要其他代码来处理连接并在沉浸式视图中呈现。 典型的远程处理连接的延迟最低为50毫秒。 播放机应用可以实时报告滞后时间。

此页面上的所有代码和工作项目都可以在 " [全息远程处理示例 github 存储库](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)" 中找到。

## <a name="prerequisites"></a>必备条件

一个很好的起点是基于 DirectX 的基于 DirectX 的桌面或 UWP 应用，以 [HOLOGRAPHICSPACE API](../native/getting-a-holographicspace.md)为目标。 有关详细信息，请参阅 [DirectX 开发概述](../native/directx-development-overview.md)。 [C + + 全息版项目模板](../native/creating-a-holographic-directx-project.md)是一个很好的起点。

>[!IMPORTANT]
>使用全息远程处理的任何应用都应该编写为使用 [多线程单元](/windows/win32/com/multithreaded-apartments)。 支持使用 [单线程单元](/windows/win32/com/single-threaded-apartments) ，但会导致在播放过程中出现欠最佳的性能，并且可能会断断续续。 使用 c + +/WinRT [WinRT：： init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) 多线程单元是默认值。



## <a name="get-the-holographic-remoting-nuget-package"></a>获取全息远程处理 NuGet 包

若要将 NuGet 包添加到 Visual Studio 中的项目，需要执行以下步骤。
1. 在 Visual Studio 中打开项目。
2. 右键单击项目节点，然后选择 "**管理 NuGet 包 ...** "
3. 在出现的面板中，选择 " **浏览** "，然后搜索 "全息远程处理"。
4. 选择 " **Microsoft**"，并选择 "安装"，并选择 "**安装** **"。**
5. 如果显示 " **预览** " 对话框，请选择 **"确定"**。
6. 弹出 "许可协议" 对话框后，选择 " **我接受** "。

>[!NOTE]
>对于想要以 HoloLens 1 为目标的开发人员，NuGet 包 **的版本 1.x** 仍可用。 有关详细信息，请参阅[添加全息远程处理 (HoloLens (第一代) ) ](add-holographic-remoting.md)。

## <a name="create-the-remote-context"></a>创建远程上下文

第一步，应用程序应创建远程上下文。

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
>全息远程处理的工作原理是替换作为 Windows 的一部分的 Windows Mixed Reality 运行时。 这是在创建远程上下文的过程中完成的。 因此，在创建远程上下文之前，对任何 Windows Mixed Reality API 进行的任何调用都可能导致意外的行为。 推荐的方法是尽早创建远程上下文，然后再与任何混合现实 API 交互。 在调用 CreateRemoteContext 并随后创建或检索对象之前，不要混合通过任何 Windows Mixed Reality API 创建或检索的对象。

接下来，需要创建全息空间。 不需要指定 CoreWindow。 没有 CoreWindow 的桌面应用程序可以只传递一个 ```nullptr``` 。

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>连接设备

当远程应用已准备好呈现内容时，可以建立与播放机设备的连接。

可以通过以下两种方式之一来完成连接。
1) 远程应用连接到设备上运行的播放机。
2) 设备上运行的播放机连接到远程应用。

若要建立从远程应用到播放机设备的连接，请 ```Connect``` 在远程上下文上调用方法，指定主机名和端口。 全息远程处理播放器使用的端口为 **8265**。

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
>与任何 c + +/WinRT API 一样， ```Connect``` 都可能引发需要处理的 WinRT：： hresult_error。

>[!TIP]
>若要避免使用[c + +/WinRT](/windows/uwp/cpp-and-winrt-apis/)语言投影， ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` 可以包含位于全息远程处理 NuGet 包内的文件。 它包含基础 COM 接口的声明。 不过，建议使用 c + +/WinRT。

可以通过调用方法来侦听远程应用上的传入连接 ```Listen``` 。 在此调用过程中，可以同时指定握手端口和传输端口。 握手端口用于初始握手。 然后通过传输端口发送数据。 默认情况下，使用 **8265** 和 **8266** 。

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
>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```NuGet 包内部包含由全息远程处理公开的 API 的详细文档。

## <a name="handling-remoting-specific-events"></a>处理特定于远程处理的事件

远程上下文公开三个事件，这对于监视连接状态很重要。
1) OnConnected：成功建立到设备的连接后触发。
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
3) OnListening：侦听传入连接时启动。
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

此外，还可以使用远程上下文中的属性查询连接状态 ```ConnectionState``` 。
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>处理语音事件

使用远程语音接口，可以将语音触发器注册到 HoloLens 2 并使其远程处理到远程应用程序。

此附加成员是跟踪远程语音状态所必需的。

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

使用异步帮助器方法，你可以初始化远程语音。 这应异步完成，因为初始化可能需要相当长的时间。 [带有 c + +/WinRT 的并发和异步操作](/windows/uwp/cpp-and-winrt-apis/concurrency) 介绍了如何通过 c + + 编写异步函数/WinRT。

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

可以通过两种方法来指定要识别的短语。
1) 语音语法 xml 文件中的规范。 有关详细信息，请参阅 [如何创建基本 XML 语法](/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) 。
2) 通过将字典向量传入到来指定 ```ApplyParameters``` 。

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

## <a name="preview-streamed-content-locally"></a>在本地预览流式处理内容

若要在发送到设备的远程应用中显示相同的内容， ```OnSendFrame``` 可以使用远程上下文的事件。 ```OnSendFrame```每次全息远程处理库将当前帧发送到远程设备时，都会触发事件。 这是获取内容并将其 array.blit 到桌面或 UWP 窗口的理想时机。

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

## <a name="depth-reprojection"></a>深度 Reprojection

从版本 [2.1.0](holographic-remoting-version-history.md#v2.1.0)开始，全息远程处理支持 [深度 Reprojection](hologram-stability.md#reprojection)。 这需要将颜色缓冲区和深度缓冲区从远程应用程序流式传输到 HoloLens 2。 默认情况下，将启用深度缓冲区流式处理，并将其配置为使用一半分辨率的颜色缓冲区。 这可以按如下方式更改：

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

请注意，如果不应使用默认值，则 ```ConfigureDepthVideoStream``` 必须在建立与 HoloLens 2 的连接之前调用默认值。 最好的位置是创建远程上下文。 DepthBufferStreamResolution 的可能值为：

* Full_Resolution
* Half_Resolution
* Quarter_Resolution
* 已禁用 (使用版本 [2.1.3](holographic-remoting-version-history.md#v2.1.3) 添加，如果未使用，则不会创建其他深度视频流) 

请记住，使用完全解析深度缓冲区还会影响带宽要求，并需要考虑到提供的最大带宽值 ```CreateRemoteContext``` 。

在配置分辨率旁边，还必须通过 HolographicCameraRenderingParameters 提交深度缓冲区 [。 CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)。

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

若要验证 HoloLens 2 的深度 reprojection 是否正常工作，可以通过设备门户启用深度可视化工具。 有关详细信息，请参阅 [验证深度是否已正确设置](hologram-stability.md#verifying-depth-is-set-correctly) 。

## <a name="optional-custom-data-channels"></a>可选：自定义数据通道

自定义数据信道可用于通过已建立的远程处理连接发送用户数据。 有关详细信息，请参阅 [自定义数据通道](holographic-remoting-custom-data-channels.md) 。

## <a name="see-also"></a>另请参阅
* [全息远程处理概述](holographic-remoting-overview.md)
* [编写自定义全息远程处理播放器应用](holographic-remoting-create-player.md)
* [自定义全息远程处理数据通道](holographic-remoting-custom-data-channels.md)
* [使用全息远程处理建立安全连接](holographic-remoting-secure-connection.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)