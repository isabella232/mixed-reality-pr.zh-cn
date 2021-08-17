---
title: '使用 C++ 脚本编写 (全息远程) '
description: 创建自定义 Hologaphic Remoting 应用，向用户显示远程计算机上呈现HoloLens 2。
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 7/30/2021
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理、NuGet、应用清单、播放器上下文、远程应用、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备
ms.openlocfilehash: 37388dc9cbf70cb7fccd742fb45e1e29c0ceb971
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184728"
---
# <a name="writing-a-custom-holographic-remoting-player-app-c"></a>使用 C++ 脚本编写自定义全息远程处理 () 

>[!IMPORTANT]
>本文档介绍如何为用户创建自定义播放器HoloLens 2。 为 HoloLens 2 编写的自定义播放器与为 HoloLens 1 编写的远程应用程序不兼容。 这意味着两个应用程序必须使用 NuGet **2.x.x 版**。

通过创建自定义全息远程处理播放器应用，可以创建一个自定义应用程序，该应用程序能够在远程计算机上显示沉浸式[](../../design/app-views.md)HoloLens 2。 可在全息远程处理示例 [github](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)存储库 找到此页上的所有代码和工作项目。

全息远程处理播放器可让应用显示桌面电脑或 UWP[](rendering.md)设备上呈现的全息内容，Xbox One访问更多系统资源。 全息远程处理播放器应用将输入数据流式传输至全息远程处理远程应用程序，并接收沉浸式视图作为视频和音频流。 使用标准 Wi-Fi 建立连接。 若要创建播放器应用，请使用NuGet包将全息远程处理添加到 UWP 应用。 然后编写代码来处理连接并显示沉浸式视图。 

## <a name="prerequisites"></a>必备条件

一个很好的起点是一个基于 DirectX 的工作 UWP 应用，该应用已面向 Windows Mixed Reality API。 有关详细信息，请参阅 [DirectX 开发概述](../native/directx-development-overview.md)。 如果没有现有应用，并且想要从头开始， [则 C++ 全息](../native/creating-a-holographic-directx-project.md) 项目模板是一个很好的起点。

>[!IMPORTANT]
>任何使用全息远程处理的应用都应创作为使用多 [线程单元](/windows/win32/com/multithreaded-apartments)。 支持使用 [单线程单元](/windows/win32/com/single-threaded-apartments) ，但会导致性能降低，并且可能在播放期间造成异常。 使用 C++/WinRT [winrt：：init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) 多线程单元是默认值。

## <a name="get-the-holographic-remoting-nuget-package"></a>获取全息远程处理NuGet包

若要将包添加到 NuGet 中的项目，需要执行Visual Studio。
1. 在 Visual Studio 中打开项目。
2. 右键单击项目节点，然后选择"**管理NuGet包..."**
3. 在出现的面板中，选择" **浏览"，** 然后搜索"全息远程处理"。
4. 选择 **"Microsoft.Holographic.Remoting"，** 确保选择最新的 **2.x.x** 版本，然后选择"安装 **"。**
5. 如果显示 **"预览"** 对话框，请选择"确定 **"。**
6. 显示 **许可协议对话框** 时，选择"我接受"。

>[!IMPORTANT]
><a name="idl"></a>应用程序 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 包NuGet包含全息远程处理公开的 API 的详细文档。

## <a name="modify-the-packageappxmanifest-of-the-application"></a>修改应用程序的 Package.appxmanifest

若要使应用程序知道Microsoft.Holographic.AppRemoting.dll包添加NuGet，需要对项目执行以下步骤：

1. 在解决方案资源管理器单击 **Package.appxmanifest** 文件，然后选择" **打开..."**
2. 选择 **"XML (文本) 编辑器"，** 然后选择"确定 **"**
3. 将以下行添加到文件并保存
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
## <a name="create-the-player-context"></a>创建播放器上下文

作为第一步，应用程序应创建播放器上下文。

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
>全息远程处理的工作原理是Windows Mixed Reality远程处理特定运行时Windows的一部分。 此操作是在创建播放器上下文期间完成。 因此，在创建播放器上下文之前Windows Mixed Reality API 的任何调用都可能会导致意外行为。 建议的方法是在与任何混合现实 API 交互之前尽早创建播放器上下文。 在调用 之前，切勿将通过任何 Windows Mixed Reality API 创建或检索的对象与 ```PlayerContext::Create``` 之后创建或检索的对象混合使用。

接下来，可以通过调用[HolographicSpace.CreateForCoreWindow 来创建 HolographicSpace。](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a>连接远程应用

播放器应用准备好呈现内容后，可以建立与远程应用的连接。

可以通过以下方式之一建立连接：
1) 在远程应用上运行HoloLens 2连接到远程应用。
2) 远程应用连接到在 HoloLens 2 上运行的播放器HoloLens 2。

若要从播放器应用连接到远程应用，请对播放器上下文调用 方法 ```Connect``` ，指定主机名和端口。 默认端口为 **8265。**

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
>与任何 C++/WinRT API 一样，可能会 ```Connect``` 引发 winrt：：hresult_error需要处理。

可以通过调用 方法来侦听播放器应用中的传入 ```Listen``` 连接。 在此调用过程中，可以同时指定握手端口和传输端口。 握手端口用于初始握手。 然后，通过传输端口发送数据。 默认情况下，使用端口号 **8265** 和 **8266。**

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


## <a name="handling-connection-related-events"></a>处理与连接相关的事件

```PlayerContext```公开三个事件以监视连接状态
1) OnConnected：成功建立与远程应用的连接时触发。
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnected：如果已建立的连接终止或无法建立连接，则触发。
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
>文件 ```ConnectionFailureReason``` 中记录了可能 ```Microsoft.Holographic.AppRemoting.idl``` [的值](#idl)。

3) OnListening：开始侦听传入连接时。
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

此外，可以使用播放器上下文中的 属性 ```ConnectionState``` 查询连接状态。
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>显示远程渲染的帧

若要显示远程呈现的内容，在 ```PlayerContext::BlitRemoteFrame``` 呈现全息帧 [时调用](/uwp/api/windows.graphics.holographic.holographicframe)。 

```BlitRemoteFrame``` 要求当前全息帧的后缓冲区绑定为呈现器目标。 可以通过[Direct3D11BackBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)属性从[HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters)接收后端缓冲区。

调用时， ```BlitRemoteFrame``` 将远程应用程序中收到的最新帧复制到 HolographicFrame 的 BackBuffer 中。 此外，如果远程应用程序在呈现远程帧期间指定了焦点，则设置焦点集。

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame``` 可能会覆盖当前帧的焦点。 
>- 若要指定回退焦点，请调用 之前的[HolographicCameraRenderingParameters：：SetFocusPoint。](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame``` 
>- 若要覆盖远程焦点，请之后调用[HolographicCameraRenderingParameters：：SetFocusPoint。](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame```

成功后， ```BlitRemoteFrame``` 返回 ```BlitResult::Success_Color``` 。 否则，它将返回失败原因：
- ```BlitResult::Failed_NoRemoteFrameAvailable```：失败，因为没有可用的远程帧。
- ```BlitResult::Failed_NoCamera```：由于没有摄像头，因此失败。
- ```BlitResult::Failed_RemoteFrameTooOld```：失败，因为远程帧太旧 (PlayerContext：：BlitRemoteFrameTimeout 属性) 。

>[!IMPORTANT]
> 从版本 [2.1.0](holographic-remoting-version-history.md#v2.1.0) 开始，自定义播放器可以通过全息远程处理使用深度重现。

```BlitResult``` 还可以在 ```BlitResult::Success_Color_Depth``` 下列条件下返回：

- 远程应用已通过 [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer 提交深度缓冲区](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)。
- 自定义播放器应用在调用 之前已绑定有效的深度缓冲区 ```BlitRemoteFrame``` 。

如果满足这些条件 ```BlitRemoteFrame``` ，则远程深度将转换为当前绑定的本地深度缓冲区。 然后，你可以呈现其他本地内容，这将与远程呈现的内容具有深度交集。 此外，可以通过自定义播放器中的 [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) 提交本地深度缓冲区，以对远程和本地呈现的内容进行深度重新投影。 有关详细信息 [，请参阅深度](hologram-stability.md#reprojection) 重现。

### <a name="projection-transform-mode"></a>投影转换模式

通过全息远程处理使用深度重新投影时，出现一个问题：远程内容的呈现方式与自定义播放器应用直接呈现的本地内容不同。 常见用例是通过播放器端和远程端上的 [HolographicCamera：：SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) 和 [HolographicCamera：：SetFarPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) 为近平面和远平面 (指定不同的值。 在这种情况下，并不清楚玩家端上的投影转换是应反映远程近/远平面距离还是本地平面距离。

从版本 [2.1.0](holographic-remoting-version-history.md#v2.1.0) 开始，可以通过 控制投影转换模式 ```PlayerContext::ProjectionTransformConfig``` 。 支持的值是：

- ```Local``` - [HolographicCameraPose：:P rojectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) 返回投影转换，该转换反映自定义播放器应用在 HolographicCamera 上设置的近/远平面距离。
- ```Remote``` - 投影转换反映远程应用指定的近/远平面距离。
- ```Merged``` - 与远程应用和自定义播放器应用之间的近/远平面距离合并。 默认情况下，这是通过取近平面距离的最小值和远平面距离的最大值来达到的。 如果远程端或本地端（例如远端<，则远程近/远平面距离会翻转。

## <a name="optional-set-blitremoteframetimeout"></a>可选：设置 BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimeout``` 从版本 [2.0.9 开始](holographic-remoting-version-history.md#v2.0.9)支持 。 

属性指定如果未收到新的远程帧，则重用 ```PlayerContext::BlitRemoteFrameTimeout``` 远程帧的时间。 

一个常见用例是，如果一段时间未收到新帧，则允许 BlitRemoteFrame 超时显示空白屏幕。 启用后，方法的返回类型还可用于 ```BlitRemoteFrame``` 切换到本地呈现的回退内容。 

若要启用超时，将 属性值设置为等于或大于 100 毫秒的持续时间。 若要禁用超时，将 属性设置为零持续时间。 如果超时处于启用状态，并且未在设置的持续时间内收到任何远程帧，BlitRemoteFrame 将失败并返回，直到收到新的 ```Failed_RemoteFrameTooOld``` 远程帧。

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>可选：获取有关最后一个远程帧的统计信息

若要诊断性能或网络问题，可以通过 属性检索有关最后一个远程帧的 ```PlayerContext::LastFrameStatistics``` 统计信息。 统计信息在调用 [HolographicFrame：:P ResentUsingCurrentPrediction 期间更新](/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)。

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

有关详细信息，请参阅 ```PlayerFrameStatistics``` 文件 中的 ```Microsoft.Holographic.AppRemoting.idl``` [文档](#idl)。

## <a name="optional-custom-data-channels"></a>可选：自定义数据通道

自定义数据通道可用于通过已建立的远程处理连接发送用户数据。 有关详细信息 [，请参阅](holographic-remoting-custom-data-channels.md) 自定义数据通道。

## <a name="see-also"></a>另请参阅
* [全息远程处理概述](holographic-remoting-overview.md)
* [使用远程 API 编写全息远程Windows Mixed Reality应用](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR API 编写全息远程处理远程应用](holographic-remoting-create-remote-openxr.md)
* [自定义全息远程处理数据通道](holographic-remoting-custom-data-channels.md)
* [使用全息远程处理建立安全连接](holographic-remoting-secure-connection.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)