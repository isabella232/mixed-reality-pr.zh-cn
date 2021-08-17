---
title: 添加全息远程处理
description: 了解如何安装、配置和使用全息远程处理，以通过HoloLens将全息影像渲染到远程设备。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality、全息影像、全息远程处理、远程渲染、网络渲染、HoloLens、远程全息影像、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备
ms.openlocfilehash: 3f9d3d23d18f680ce1001310e4ce49089edaae6a
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184618"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a>将全息远程处理 (HoloLens (第一代) ) 

>[!IMPORTANT]
> 本文档介绍了如何为第 1 HoloLens主机应用程序。 第一代 **HoloLens (主机**) 必须使用NuGet **1.x.x 版**。 这意味着为 HoloLens 1 编写的主机应用程序与 HoloLens 2 不兼容，反之亦然。

## <a name="hololens-2"></a>HoloLens 2

HoloLens全息远程处理的应用程序开发人员需要更新其应用，使其与 HoloLens 2。 这需要新版本的全息远程处理NuGet包。 在 HoloLens 2 上连接到全息远程处理播放器时，请务必使用全息远程处理 NuGet 包的版本 2.0.0.0 或以上版本，否则连接将失败。

>[!NOTE]
> 可在此处找到[HoloLens 2特定指南](holographic-remoting-create-remote-wmr.md)。


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>将全息远程处理添加到桌面或 UWP 应用

本页介绍如何将全息远程处理添加到桌面或 UWP 应用。

全息远程处理可让应用HoloLens桌面电脑或 UWP 设备上托管的全息内容（如 Xbox One）。 还可以访问更多系统资源，从而可以将远程沉 [浸式视图集成到](../../design/app-views.md) 现有的桌面电脑软件中。 远程处理主机应用从 HoloLens 接收输入数据流，在虚拟沉浸式视图中呈现内容，将内容帧流式传输回HoloLens。 使用标准 Wi-Fi 建立连接。 若要使用远程处理，请使用 NuGet 包将全息远程处理添加到桌面或 UWP 应用，然后编写代码来处理连接并呈现沉浸式视图。 帮助程序库包含在代码示例中，用于简化处理设备连接的任务。

典型的远程处理连接延迟最低为 50 毫秒。 播放器应用可以实时报告延迟。

>[!NOTE]
>本文中的代码片段当前演示如何使用 C++/CX，而不是 C++17 兼容的 C++/WinRT，如 [C++](../native/creating-a-holographic-directx-project.md)全息项目模板 中使用的。  这些概念等效于 C++/WinRT 项目，但需要转换代码。

### <a name="get-the-remoting-nuget-packages"></a>获取远程处理NuGet包

按照以下步骤获取NuGet远程处理包，然后从项目添加引用：
1. 转到项目中的Visual Studio。
2. 右键单击项目节点，然后选择"管理NuGet **包..."**
3. 在出现的面板中，删除"浏览 **"，然后** 搜索"全息远程处理"。
4. 选择 **"Microsoft.Holographic.Remoting"并** 单击"安装 **"。**
5. 如果显示 **"预览"** 对话框，请选择"确定 **"。**
6. 显示 **许可协议对话框** 时，选择"我接受"。

### <a name="create-the-holographicstreamerhelpers"></a>创建 HolographicStreamerHelpers

首先，我们需要将 HolographicStreamerHelpers 的实例添加到将处理远程处理的类。

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

还需要跟踪连接状态。 如果要呈现预览，需要具有纹理以将其复制到。 还需要一些内容，例如连接状态锁、存储 ip 地址HoloLens等。

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

若要连接到 HoloLens，请创建 HolographicStreamerHelpers 的实例并连接到目标 IP 地址。 需要设置视频帧大小以匹配HoloLens宽度和高度，因为全息远程处理库要求编码器分辨率和解码器分辨率完全匹配。

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

OnConnected 事件可以更新 UI、开始呈现等。 在桌面代码示例中，我们使用"已连接"消息更新窗口标题。

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

OnDisconnected 事件可以处理重新连接、UI 更新等。 此示例中，如果发生暂时性故障，我们将重新连接。

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

当远程处理组件准备好发送帧时，应用将有机会在 SendFrameEvent 中复制该帧。 在这里，我们将帧复制到交换链，以便可以在预览窗口中显示它。

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

若要使用远程处理呈现内容，在桌面或 UWP 应用中设置虚拟 IFrameworkView，并处理远程处理中的全息帧。 此视图Windows所有全息 API 的使用方式相同，但设置方式略有不同。

全息空间和语音组件来自 HolographicRemotingHelpers 类，而不是自己创建它们：

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

无需在 Run 方法中使用更新循环，而是从桌面或 UWP 应用的主循环提供时钟周期更新。 这样，桌面或 UWP 应用就仍可以控制消息处理。

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

全息应用视图的 Tick () 方法完成更新、绘制和呈现循环的一次迭代。

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

全息应用视图更新、呈现和呈现循环与在 HoloLens 上运行时完全相同，只不过你可以访问台式电脑上更多的系统资源。 可以呈现更多三角形、拥有更多绘图通道、执行更多物理操作，并使用 x64 进程加载需要超过 2 GB RAM 的内容。

### <a name="disconnect-and-end-the-remote-session"></a>断开连接并结束远程会话

若要断开连接（例如，当用户单击 UI 按钮断开连接时）请调用 HolographicStreamerHelpers () 断开连接"，然后释放 对象。

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

## <a name="get-the-remoting-player"></a>获取远程处理播放器

Windows应用存储中提供了Windows全息远程处理播放器，作为远程处理要连接到的主机应用的终结点。 若要获取Windows远程处理播放器，请从 Windows 访问 HoloLens 应用商店，搜索"远程处理"，然后下载该应用。 远程处理播放器包含一项功能，可在屏幕上显示统计信息，在调试远程处理主机应用时，此功能非常有用。

## <a name="notes-and-resources"></a>说明和资源

全息应用视图需要一种方法来为应用提供 Direct3D 设备，该设备必须用于初始化全息空间。 应用应使用此 Direct3D 设备复制并显示预览帧。

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**代码示例：** 提供了完整的 [全息远程](https://github.com/Microsoft/HoloLensCompanionKit) 处理代码示例，其中包括与使用 XAML 的桌面 Win32、UWP DirectX 和 UWP 的远程处理和远程处理主机项目兼容的全息应用程序视图。 

**调试说明：** 全息远程处理库可能会引发第一机会异常。 这些异常可能在调试会话中可见，具体取决于Visual Studio处于活动状态的异常设置。 这些异常由全息远程处理库在内部捕获，可以忽略。

## <a name="see-also"></a>另请参阅
* [全息远程处理概述](holographic-remoting-overview.md)
* [编写自定义全息远程处理播放器应用](holographic-remoting-create-player.md)
* [使用全息远程处理建立安全连接](holographic-remoting-secure-connection.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)