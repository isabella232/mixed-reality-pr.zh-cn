---
title: 自定义全息远程处理数据通道
description: 自定义数据通道可用于通过已建立的全息远程处理连接发送用户数据。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens，远程处理，全息远程处理，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，数据通道
ms.openlocfilehash: 6fd2bbd8ce2dedc3b13674576a23a0484ebe1419
ms.sourcegitcommit: 99ae85159b7cf75f919021771ebb8299868beea9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97102902"
---
# <a name="custom-holographic-remoting-data-channels"></a><span data-ttu-id="47544-104">自定义全息远程处理数据通道</span><span class="sxs-lookup"><span data-stu-id="47544-104">Custom Holographic Remoting data channels</span></span>

>[!NOTE]
><span data-ttu-id="47544-105">本指南特定于 HoloLens 2 上的全息远程处理。</span><span class="sxs-lookup"><span data-stu-id="47544-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="47544-106">使用自定义数据通道通过建立的远程处理连接发送自定义数据。</span><span class="sxs-lookup"><span data-stu-id="47544-106">Use custom data channels to send custom data over an established remoting connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="47544-107">自定义数据通道需要自定义远程应用和自定义播放器应用，因为它允许两个自定义应用之间的通信。</span><span class="sxs-lookup"><span data-stu-id="47544-107">Custom data channels require a custom remote app and a custom player app, as it allows for communication between the two custom apps.</span></span>

>[!TIP]
><span data-ttu-id="47544-108">可以在 [全息远程处理示例 github 存储库](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中的远程和播放器示例中找到简单的乒乓球示例。</span><span class="sxs-lookup"><span data-stu-id="47544-108">A simple ping-pong example can be found in the remote and player samples inside the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span> <span data-ttu-id="47544-109">在 ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` SampleRemoteMain/SamplePlayerMain 文件中取消注释，以启用示例代码。</span><span class="sxs-lookup"><span data-stu-id="47544-109">Uncomment ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` inside the SampleRemoteMain.h / SamplePlayerMain.h files to enable the sample code.</span></span>


## <a name="create-a-custom-data-channel"></a><span data-ttu-id="47544-110">创建自定义数据通道</span><span class="sxs-lookup"><span data-stu-id="47544-110">Create a custom data channel</span></span>


<span data-ttu-id="47544-111">若要创建自定义数据通道，需要以下字段：</span><span class="sxs-lookup"><span data-stu-id="47544-111">To create a custom data channel, the following fields are required:</span></span>
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

<span data-ttu-id="47544-112">成功建立连接后，你可以从远程端和/或播放机创建新的数据通道。</span><span class="sxs-lookup"><span data-stu-id="47544-112">After a connection is successfully established, you can create new data channels from either the remote side, the player side, or both.</span></span> <span data-ttu-id="47544-113">RemoteContext 和 PlayerContext 都提供 ```CreateDataChannel()``` 创建数据通道的方法。</span><span class="sxs-lookup"><span data-stu-id="47544-113">Both the RemoteContext and the PlayerContext provide a ```CreateDataChannel()``` method for creating data channels.</span></span> <span data-ttu-id="47544-114">第一个参数是用于在后续操作中标识数据通道的通道 ID。</span><span class="sxs-lookup"><span data-stu-id="47544-114">The first parameter is the channel ID, which is used to identify the data channel in subsequent operations.</span></span> <span data-ttu-id="47544-115">第二个参数是优先级，它指定此通道的数据被传输到另一方的优先级。</span><span class="sxs-lookup"><span data-stu-id="47544-115">The second parameter is the priority, which specifies the priority with which data of this channel is transferred to the other side.</span></span> <span data-ttu-id="47544-116">远程端的有效通道 Id 是从0到，包括63和64，最127高可达。</span><span class="sxs-lookup"><span data-stu-id="47544-116">Valid channel IDs on the remote side are from 0 up to and including 63, and 64 up to and including 127 for the player side.</span></span> <span data-ttu-id="47544-117">有效优先级为 ```Low``` ```Medium``` (两侧的、或 ```High```) 。</span><span class="sxs-lookup"><span data-stu-id="47544-117">Valid priorities are ```Low```, ```Medium```, or ```High``` (on both sides).</span></span>

<span data-ttu-id="47544-118">在 **远程** 端开始创建数据通道：</span><span class="sxs-lookup"><span data-stu-id="47544-118">To start the creation of a data channel on the **remote** side:</span></span>
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

<span data-ttu-id="47544-119">若要开始在 **播放机** 端创建数据通道：</span><span class="sxs-lookup"><span data-stu-id="47544-119">To start the creation of a data channel on the **player** side:</span></span>
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
><span data-ttu-id="47544-120">若要创建新的自定义数据通道，只需一方 (远程或玩家) 需要调用 ```CreateDataChannel``` 方法。</span><span class="sxs-lookup"><span data-stu-id="47544-120">To create a new custom data channel, only one side (either remote or player) needs to call the ```CreateDataChannel``` method.</span></span>

## <a name="handling-custom-data-channel-events"></a><span data-ttu-id="47544-121">处理自定义数据通道事件</span><span class="sxs-lookup"><span data-stu-id="47544-121">Handling custom data channel events</span></span>

<span data-ttu-id="47544-122">若要建立自定义数据通道， ```OnDataChannelCreated``` 需要在播放机和远程端)  (处理事件。</span><span class="sxs-lookup"><span data-stu-id="47544-122">To establish a custom data channel, the ```OnDataChannelCreated``` event needs to be handled (on both the player and the remote side).</span></span> <span data-ttu-id="47544-123">它在用户数据通道已由任一端创建时触发，并提供一个 ```IDataChannel``` 对象，该对象可用于通过此通道发送和接收数据。</span><span class="sxs-lookup"><span data-stu-id="47544-123">It triggers when a user data channel has been created by either side and provides a ```IDataChannel``` object, which can be used to send and receive data over this channel.</span></span>

<span data-ttu-id="47544-124">若要在事件上注册侦听器 ```OnDataChannelCreated``` ：</span><span class="sxs-lookup"><span data-stu-id="47544-124">To register a listener on the ```OnDataChannelCreated``` event:</span></span>
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

<span data-ttu-id="47544-125">若要在收到数据时获得通知，请 ```OnDataReceived``` 在 ```IDataChannel``` 处理程序提供的对象上注册事件 ```OnDataChannelCreated``` 。</span><span class="sxs-lookup"><span data-stu-id="47544-125">To get notified when data is received, register to the ```OnDataReceived``` event on the ```IDataChannel``` object provided by the ```OnDataChannelCreated``` handler.</span></span> <span data-ttu-id="47544-126">注册到 ```OnClosed``` 事件，以在数据通道关闭时获得通知。</span><span class="sxs-lookup"><span data-stu-id="47544-126">Register to the ```OnClosed``` event, to get notified when the data channel has been closed.</span></span>

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

## <a name="sending-data"></a><span data-ttu-id="47544-127">发送数据</span><span class="sxs-lookup"><span data-stu-id="47544-127">Sending data</span></span>

<span data-ttu-id="47544-128">若要通过自定义数据通道发送数据，请使用 ```IDataChannel::SendData()``` 方法。</span><span class="sxs-lookup"><span data-stu-id="47544-128">To send data over a custom data channel, use the ```IDataChannel::SendData()``` method.</span></span> <span data-ttu-id="47544-129">第一个参数是 ```winrt::array_view<const uint8_t>``` 应发送的数据的。</span><span class="sxs-lookup"><span data-stu-id="47544-129">The first parameter is a ```winrt::array_view<const uint8_t>``` to the data that should be send.</span></span> <span data-ttu-id="47544-130">第二个参数指定应重新发送数据的位置，直到另一方确认接收。</span><span class="sxs-lookup"><span data-stu-id="47544-130">The second parameter specifies where the data should be resend, until the other side acknowledge the reception.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="47544-131">如果网络条件不正确，则相同的数据包可能会到达一次以上。</span><span class="sxs-lookup"><span data-stu-id="47544-131">In case of bad network conditions, the same data packet might arrive more than once.</span></span> <span data-ttu-id="47544-132">接收代码必须能够处理这种情况。</span><span class="sxs-lookup"><span data-stu-id="47544-132">The receiving code must be able to handle this situation.</span></span>

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a><span data-ttu-id="47544-133">关闭自定义数据通道</span><span class="sxs-lookup"><span data-stu-id="47544-133">Closing a custom data channel</span></span>

<span data-ttu-id="47544-134">若要关闭自定义数据通道，请使用 ```IDataChannel::Close()``` 方法。</span><span class="sxs-lookup"><span data-stu-id="47544-134">To close a custom data channel, use the ```IDataChannel::Close()``` method.</span></span> <span data-ttu-id="47544-135">```OnClosed```自定义数据通道关闭后，事件会通知两端。</span><span class="sxs-lookup"><span data-stu-id="47544-135">Both sides will be notified by the ```OnClosed``` event once the custom data channel has been closed.</span></span>

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a><span data-ttu-id="47544-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47544-136">See Also</span></span>
* [<span data-ttu-id="47544-137">使用 Windows Mixed Reality Api 编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="47544-137">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="47544-138">使用 OpenXR Api 编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="47544-138">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="47544-139">编写自定义全息远程处理播放器应用</span><span class="sxs-lookup"><span data-stu-id="47544-139">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="47544-140">全息远程处理故障排除和限制</span><span class="sxs-lookup"><span data-stu-id="47544-140">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="47544-141">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="47544-141">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="47544-142">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="47544-142">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
