---
title: 自定义全息远程处理数据通道
description: 自定义数据通道可用于通过已建立的全息远程处理连接发送用户数据。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、数据通道
ms.openlocfilehash: 1adda10aa7792eaeab0ac32cb37d73dcfd2b58e6
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184708"
---
# <a name="custom-holographic-remoting-data-channels-c"></a>自定义全息远程处理数据通道 (C++) 

>[!NOTE]
>本指南特定于全息远程处理HoloLens 2。

使用自定义数据通道通过已建立的远程处理连接发送自定义数据。

>[!IMPORTANT]
>自定义数据通道需要自定义远程应用和自定义播放器应用，因为它允许在两个自定义应用之间通信。

>[!TIP]
>可以在全息远程处理示例 [github](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)存储库 内的远程和播放器示例中找到一个简单的 ping-pong 示例。 取消注释 ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` SampleRemoteMain.h / SamplePlayerMain.h 文件以启用示例代码。


## <a name="create-a-custom-data-channel"></a>创建自定义数据通道


若要创建自定义数据通道，需要以下字段：
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

成功建立连接后，可以从远程端和/或播放器端创建新的数据通道。 RemoteContext 和 PlayerContext 都提供 ```CreateDataChannel()``` 用于创建数据通道的方法。 第一个参数是通道 ID，用于在后续操作中标识数据通道。 第二个参数是优先级，它指定此通道的数据传输到另一侧的优先级。 远程端的有效通道 ID 从 0 到 63（包括 63）到 64（包括播放器端 127）。 有效优先级为 ```Low``` ```Medium``` 、 ```High``` 或 (两侧) 。

若要开始在远程端创建数据 **通道，** 请执行以下操作：
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

若要开始在播放器端创建数据 **通道** ，请：
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>若要创建新的自定义数据通道，只需 (远程或播放器) 调用 ```CreateDataChannel``` 方法。

## <a name="handling-custom-data-channel-events"></a>处理自定义数据通道事件

若要建立自定义数据通道，需要在播放器和远程 (上 ```OnDataChannelCreated``` 处理事件) 。 当任一方创建用户数据通道并提供 对象时，它触发，该对象可用于通过此通道 ```IDataChannel``` 发送和接收数据。

若要在事件上注册侦听器 ```OnDataChannelCreated``` ，请：
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

若要在接收到数据时收到通知，请在处理程序 ```OnDataReceived``` 提供的 ```IDataChannel``` 对象上注册 到 ```OnDataChannelCreated``` 事件。 注册到 ```OnClosed``` 事件，以在数据通道关闭时收到通知。

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a>发送数据

若要通过自定义数据通道发送数据，请使用 ```IDataChannel::SendData()``` 方法。 第一个参数 ```winrt::array_view<const uint8_t>``` 是应发送的数据的 。 第二个参数指定应在另一端确认接收之前重新发送数据的地方。 

>[!IMPORTANT]
>如果网络状况不佳，同一数据包可能会多次到达。 接收代码必须能够处理这种情况。

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>关闭自定义数据通道

若要关闭自定义数据通道，请使用 ```IDataChannel::Close()``` 方法。 自定义数据通道关闭后，事件会通知双方 ```OnClosed``` 。

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>另请参阅
* [全息远程处理概述](holographic-remoting-overview.md)
* [使用远程 API 编写全息远程Windows Mixed Reality应用](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR API 编写全息远程处理远程应用](holographic-remoting-create-remote-openxr.md)
* [编写自定义全息远程处理播放器应用](holographic-remoting-create-player.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)