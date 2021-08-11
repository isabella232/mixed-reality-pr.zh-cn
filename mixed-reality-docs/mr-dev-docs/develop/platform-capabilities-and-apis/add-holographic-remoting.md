---
title: 添加全息远程处理
description: 了解如何安装、配置和使用全息远程处理通过网络将全息影像呈现到 HoloLens 设备。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality，全息影像，全息远程处理，远程渲染，网络渲染，HoloLens，远程全息影像，混合现实耳机，Windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: ecfc49477e202b08303160e54ce986577a9d79eb387dc1edb1bc33c63644615f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198853"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a>添加全息远程处理 (HoloLens (第一代) ) 

>[!IMPORTANT]
> 本文档介绍了如何为 HoloLens 1 创建主机应用程序。 用于 **HoloLens (第一代)** 的主机应用程序必须使用 NuGet 包版本 1.x. x. x. x. x. **x**。 这意味着，为 HoloLens 1 编写的主机应用程序与 HoloLens 2 不兼容，反之亦然。

## <a name="hololens-2"></a>HoloLens 2

使用全息远程处理的 HoloLens 开发人员需要更新其应用程序，使其与 HoloLens 2 兼容。 这需要 NuGet 包的新版本的全息远程处理。 在连接到 HoloLens 2 上的全息远程处理播放机时，请确保使用 "NuGet" 或更高版本的全息远程处理包，否则连接将会失败。

>[!NOTE]
> 可在[此处](holographic-remoting-create-remote-wmr.md)找到特定于 HoloLens 2 的指南。


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>将全息远程处理添加到桌面或 UWP 应用

本页介绍如何向桌面或 UWP 应用添加全息远程处理。

使用全息远程处理，你的应用程序可以以台式计算机或 UWP 设备（如 Xbox One）上托管的全息内容为目标 HoloLens。 你还可以访问更多的系统资源，使远程 [沉浸式视图](../../design/app-views.md) 可以集成到现有的台式计算机软件中。 远程处理主机应用从 HoloLens 接收输入数据流，在虚拟沉浸式视图中呈现内容，并将内容帧流回 HoloLens。 使用标准 Wi-fi 建立连接。 若要使用远程处理，请使用 NuGet 包将全息远程处理添加到桌面或 UWP 应用，然后编写代码来处理连接并呈现沉浸式视图。 帮助程序库包括在代码示例中，用于简化设备连接的处理任务。

典型的远程处理连接的延迟最低为50毫秒。 播放机应用可以实时报告滞后时间。

>[!NOTE]
>本文中的代码片段当前演示了如何 [使用 c +](../native/creating-a-holographic-directx-project.md)+/cx 中的 c + +/cx 而不是 c + + 17 兼容 c + +/WinRT。  概念与 c + +/WinRT 项目等效，但你需要转换代码。

### <a name="get-the-remoting-nuget-packages"></a>获取远程处理 NuGet 包

按照以下步骤获取用于全息远程处理的 NuGet 包，并从项目中添加引用：
1. 在 Visual Studio 中转到你的项目。
2. 右键单击项目节点，然后选择 "**管理 NuGet 包 ...** "
3. 在出现的面板中，selecct **浏览** 并搜索 "全息远程处理"。
4. 选择 **"** selecct **安装**"。
5. 如果显示 " **预览** " 对话框，请选择 **"确定"**。
6. 当 "许可协议" 对话框出现时，选择 " **我接受** "。

### <a name="create-the-holographicstreamerhelpers"></a>创建 HolographicStreamerHelpers

首先，需要将 HolographicStreamerHelpers 的实例添加到将处理远程处理的类。

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

还需要跟踪连接状态。 如果要呈现预览，则需要有要将其复制到的纹理。 还需要一些功能，如连接状态锁定，某些存储 HoloLens 的 IP 地址等的方法。

```cpp
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>初始化 HolographicStreamerHelpers 并连接到 HoloLens

若要连接到 HoloLens 设备，请创建 HolographicStreamerHelpers 的实例并连接到目标 IP 地址。 需要设置视频帧大小以匹配 HoloLens 显示宽度和高度，因为全息远程处理库要求编码器和解码器分辨率完全匹配。

```cpp
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

设备连接是异步的。 应用需要为连接、断开连接和帧发送事件提供事件处理程序。

OnConnected 事件可以更新 UI，开始呈现，等等。 在我们的桌面代码示例中，我们使用 "已连接" 消息更新窗口标题。

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

OnDisconnected 事件可以处理重新连接、UI 更新等。 在此示例中，如果发生暂时性故障，则重新连接。

```cpp
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

当远程处理组件准备好发送帧时，您的应用程序将有机会在 SendFrameEvent 中创建它的副本。 在这里，我们将帧复制到一个交换链，以便可以在预览窗口中显示它。

```cpp
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a>呈现全息内容

若要使用远程处理呈现内容，请在桌面或 UWP 应用中设置一个虚拟 IFrameworkView，并处理远程处理中的全息帧。 此视图使用相同的方式来使用所有 Windows 全息 api，但设置略有不同。

全息空间和语音组件来自 HolographicRemotingHelpers 类，而不是自行创建：

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

不在 Run 方法中使用更新循环，而是通过桌面或 UWP 应用程序的主循环来提供滴答更新。 这允许桌面或 UWP 应用保持对消息处理的控制。

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

全息应用视图的 Tick () 方法完成更新、绘图、现有循环的一次迭代。

```cpp
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

全息应用视图的更新、呈现和呈现循环与 HoloLens 上运行时的效果完全相同，但你有权访问台式计算机上更多的系统资源。 您可以呈现更多的三角形，更多的绘图走刀，执行更多物理学，并使用 x64 进程加载需要 2 GB 以上 RAM 的内容。

### <a name="disconnect-and-end-the-remote-session"></a>断开并结束远程会话

断开连接-例如，当用户单击 UI 按钮断开连接时，HolographicStreamerHelpers 上的断开连接 () ，然后释放对象。

```cpp
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a>获取远程处理播放机

Windows 全息远程处理播放机在 Windows 应用商店中提供，作为要连接到的远程处理主机应用的终结点。 若要获取 Windows 全息远程处理播放器，请从 HoloLens 访问 Windows 应用商店，搜索远程处理并下载应用。 远程处理播放机包含一项功能，可用于在屏幕上显示统计信息，这在调试远程处理主机应用时非常有用。

## <a name="notes-and-resources"></a>备注和资源

全息应用视图需要提供一种方法来为你的应用提供 Direct3D 设备，该设备必须用于初始化全息空间。 应用应使用此 Direct3D 设备复制和显示预览框架。

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**代码示例：** 提供完整的 [全息远程处理代码示例](https://github.com/Microsoft/HoloLensCompanionKit) ，其中包含一个全息应用程序视图，该视图与用于桌面 WIN32、uwp DirectX 和具有 XAML 的 uwp 的远程处理和远程处理主机项目兼容。 

**调试说明：** 全息远程处理库可能会引发第一次异常。 这些异常在调试会话中可能会显示，具体取决于目前处于活动状态的 Visual Studio 异常设置。 这些例外由全息远程处理库在内部捕获，可被忽略。
