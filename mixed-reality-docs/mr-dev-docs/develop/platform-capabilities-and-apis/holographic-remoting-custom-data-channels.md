---
title: 自定义全息远程处理数据通道
description: 自定义数据通道可用于通过已建立的全息远程处理连接发送用户数据。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens，远程处理，全息远程处理，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，数据通道
ms.openlocfilehash: a11fe0bb023ae34692015585f6e1689db4330ac7
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582609"
---
# <a name="custom-holographic-remoting-data-channels"></a>自定义全息远程处理数据通道

>[!NOTE]
>本指南特定于 HoloLens 2 上的全息远程处理。

使用自定义数据通道通过建立的远程处理连接发送自定义数据。

>[!IMPORTANT]
>自定义数据通道需要自定义远程应用和自定义播放器应用，因为它允许两个自定义应用之间的通信。

>[!TIP]
>可以在 [全息远程处理示例 github 存储库](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中的远程和播放器示例中找到简单的乒乓球示例。 在 ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` SampleRemoteMain/SamplePlayerMain 文件中取消注释，以启用示例代码。


## <a name="create-a-custom-data-channel"></a>创建自定义数据通道


若要创建自定义数据通道，需要以下字段：
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

成功建立连接后，你可以从远程端和/或播放机创建新的数据通道。 RemoteContext 和 PlayerContext 都提供 ```CreateDataChannel()``` 创建数据通道的方法。 第一个参数是用于在后续操作中标识数据通道的通道 ID。 第二个参数是优先级，它指定此通道的数据被传输到另一方的优先级。 远程端的有效通道 Id 是从0到，包括63和64，最127高可达。 有效优先级为 ```Low``` ```Medium``` (两侧的、或 ```High```) 。

在 **远程** 端开始创建数据通道：
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

若要开始在 **播放机** 端创建数据通道：
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>若要创建新的自定义数据通道，只需一方 (远程或玩家) 需要调用 ```CreateDataChannel``` 方法。

## <a name="handling-custom-data-channel-events"></a>处理自定义数据通道事件

若要建立自定义数据通道， ```OnDataChannelCreated``` 需要在播放机和远程端)  (处理事件。 它在用户数据通道已由任一端创建时触发，并提供一个 ```IDataChannel``` 对象，该对象可用于通过此通道发送和接收数据。

若要在事件上注册侦听器 ```OnDataChannelCreated``` ：
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

若要在收到数据时获得通知，请 ```OnDataReceived``` 在 ```IDataChannel``` 处理程序提供的对象上注册事件 ```OnDataChannelCreated``` 。 注册到 ```OnClosed``` 事件，以在数据通道关闭时获得通知。

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

若要通过自定义数据通道发送数据，请使用 ```IDataChannel::SendData()``` 方法。 第一个参数是 ```winrt::array_view<const uint8_t>``` 应发送的数据的。 第二个参数指定应重新发送数据的位置，直到另一方确认接收。 

>[!IMPORTANT]
>如果网络条件不正确，则相同的数据包可能会到达一次以上。 接收代码必须能够处理这种情况。

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>关闭自定义数据通道

若要关闭自定义数据通道，请使用 ```IDataChannel::Close()``` 方法。 ```OnClosed```自定义数据通道关闭后，事件会通知两端。

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>另请参阅
* [使用 Windows Mixed Reality Api 编写全息远程处理远程应用](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR Api 编写全息远程处理远程应用](holographic-remoting-create-remote-openxr.md)
* [编写自定义全息远程处理播放器应用](holographic-remoting-create-player.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)