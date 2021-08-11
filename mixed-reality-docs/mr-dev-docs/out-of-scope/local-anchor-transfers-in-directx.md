---
title: DirectX 中的本地定位点传输
description: 了解如何通过传输、HoloLens和序列化空间定位点来同步两个设备。
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、同步、空间定位点、传输、多人游戏、视图、方案、演练、示例代码、传输、本地定位点传输、定位点导出、定位点导入
ms.openlocfilehash: df00e323267aa398ba45cfd7a7234c04ce8eca85f2ff3be9b6c9ddee67264085
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195652"
---
# <a name="local-anchor-transfers-in-directx"></a>DirectX 中的本地定位点传输

在无法使用<a href="/azure/spatial-anchors" target="_blank">Azure</a>空间定位点的情况下，本地定位点传输使一HoloLens设备能够导出要由第二个设备导入HoloLens定位点。

>[!NOTE]
>与 <a href="/azure/spatial-anchors" target="_blank">Azure</a>空间定位点相比，本地定位点传输提供更可靠的定位点召回，此方法不支持 iOS 和 Android 设备。

>[!NOTE]
>本文中的代码片段当前演示如何使用 C++/CX，而不是 C++17 兼容的 C++/WinRT，如 [C++](../develop/native/creating-a-holographic-directx-project.md)全息项目模板 中使用的。  这些概念等效于 C++/WinRT 项目，但需要转换代码。

## <a name="transferring-spatial-anchors"></a>传输空间定位点

可以使用[SpatialAnchorTransferManager](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager)Windows Mixed Reality设备之间传输空间定位点。 通过此 API，你可以将定位点与查找世界上的确切位置所需的所有支持传感器数据捆绑在一起，然后在另一台设备上导入该捆绑包。 第二台设备上的应用导入该定位点后，每个应用都可以使用该共享空间定位点的坐标系统呈现全息影像，该系统随后将出现在现实世界中的同一位置。

请注意，空间定位点无法在不同设备类型之间传输，例如HoloLens沉浸式头戴显示设备可能无法定位空间定位点。  传输的定位点也与 iOS 或 Android 设备不兼容。

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>将应用设置为使用 spatialPerception 功能

必须先向应用授予使用 SpatialPerception 功能的权限，然后才能使用 [SpatialAnchorTransferManager](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager)。 这是必需的，因为传输空间定位点涉及共享一段时间在定位点附近收集的传感器图像，这些图像可能包括敏感信息。

在应用的 package.appxmanifest 文件中声明此功能。 下面的示例说明：

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

此功能来自 **uap2** 命名空间。 若要在清单中访问此命名空间，请作为 *xlmns* 属性包括在 Package &lt;> 元素中。 下面的示例说明：

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**注意：** 应用需要在运行时请求该功能，然后才能访问 SpatialAnchor 导出/导入 API。 请参阅[以下示例中的 RequestAccessAsync。](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager)

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>使用 SpatialAnchorTransferManager 导出定位点数据来序列化定位点数据

代码示例中包含一个帮助程序函数，用于 ([SpatialAnchor) 序列化](/uwp/api/Windows.Perception.Spatial.SpatialAnchor) 。 此导出 API 序列化将字符串与定位点关联的键值对集合中的所有定位点。

```
// ExportAnchorDataAsync: Exports a byte buffer containing all of the anchors in the given collection.
//
// This function will place data in a buffer using a std::vector<byte>. The ata buffer contains one or more
// Anchors if one or more Anchors were successfully imported; otherwise, it is ot modified.
//
task<bool> SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
    vector<byte>* anchorByteDataOut,
    IMap<String^, SpatialAnchor^>^ anchorsToExport
    )
{
```

首先，我们需要设置数据流。 这将允许我们 1.) 使用 TryExportAnchorsAsync 将数据放在应用拥有的缓冲区中，2.) 从导出的字节缓冲区流（WinRT 数据流）读取数据，该缓冲区是 std：：vector 字节 &lt;>。

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

我们需要请求访问空间数据的权限，包括系统导出的定位点。

```
// Request access to spatial data.
auto accessRequestedTask = create_taskSpatialAnchorTransferManager::RequestAccessAsync()).then([anchorsToExport, utputStream](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
        // Export the indicated set of anchors.
        return create_task(SpatialAnchorTransferManager::TryExportAnchorsAsync(
            anchorsToExport,
            outputStream
            ));
    }
    else
    {
        // Access is denied.
        return task_from_result<bool>(false);
    }
});
```

如果我们获取了权限并导出了定位点，我们可以读取数据流。 在这里，我们还将展示如何创建用于读取数据的 DataReader 和 InputStream。

```
// Get the input stream for the anchor byte stream.
IInputStream^ inputStream = stream->GetInputStreamAt(0);
// Create a DataReader, to get bytes from the anchor byte stream.
DataReader^ reader = ref new DataReader(inputStream);
return accessRequestedTask.then([anchorByteDataOut, stream, reader](bool nchorsExported)
{
    if (anchorsExported)
    {
        // Get the size of the exported anchor byte stream.
        size_t bufferSize = static_cast<size_t>(stream->Size);
        // Resize the output buffer to accept the data from the stream.
        anchorByteDataOut->reserve(bufferSize);
        anchorByteDataOut->resize(bufferSize);
        // Read the exported anchor store into the stream.
        return create_task(reader->LoadAsync(bufferSize));
    }
    else
    {
        return task_from_result<size_t>(0);
    }
```

从流中读取字节后，可以将它们保存到自己的数据缓冲区，如下所示。

```
}).then([anchorByteDataOut, reader](size_t bytesRead)
{
    if (bytesRead > 0)
    {
        // Read the bytes from the stream, into our data output buffer.
        reader->ReadBytes(Platform::ArrayReference<byte>(&(*anchorByteDataOut)[0], bytesRead));
        return true;
    }
    else
    {
        return false;
    }
});
};
```

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>通过使用 SpatialAnchorTransferManager 将定位点数据导入系统来反初始化定位点数据

代码示例中包含一个帮助程序函数，用于加载以前导出的数据。 此反序列化函数提供键值对的集合，类似于 SpatialAnchorStore 提供的集合 - 只不过我们从另一个源（例如网络套接字）获得了此数据。 可以在脱机存储、使用应用内内存或应用 SpatialAnchorStore (应用) 数据之前处理和推理这些数据。

```
// ImportAnchorDataAsync: Imports anchors from a byte buffer that was previously exported.
//
// This function will import all anchors from a data buffer into an in-memory ollection of key, value
// pairs that maps String objects to SpatialAnchor objects. The Spatial nchorStore is not affected by
// this function unless you provide it as the target collection for import.
//
task<bool> SpatialAnchorImportExportHelper::ImportAnchorDataAsync(
    std::vector<byte>& anchorByteDataIn,
    IMap<String^, SpatialAnchor^>^ anchorMapOut
    )
{
```

首先，我们需要创建流对象来访问定位点数据。 我们将将数据从缓冲区写入系统缓冲区，因此，我们将创建一个写入内存中数据流的 DataWriter，以便实现将定位点从字节缓冲区作为 SpatialAnchors 放入系统的目标。

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

同样，我们需要确保应用有权导出空间定位点数据，其中可能包含有关用户环境的私有信息。

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

如果允许访问，我们可以将缓冲区中的字节写入系统数据流。

```
// Write the bytes to the stream.
        byte* anchorDataFirst = &anchorByteDataIn[0];
        size_t anchorDataSize = anchorByteDataIn.size();
        writer->WriteBytes(Platform::ArrayReference<byte>(anchorDataFirst, anchorDataSize));
        // Store the stream.
        return create_task(writer->StoreAsync());
    }
    else
    {
        // Access is denied.
        return task_from_result<size_t>(0);
    }
```

如果我们成功地在数据流中存储了字节，我们可以尝试使用 SpatialAnchorTransferManager 导入该数据。

```
}).then([writer, stream](unsigned int bytesWritten)
{
    if (bytesWritten > 0)
    {
        // Try to import anchors from the byte stream.
        return create_task(writer->FlushAsync())
            .then([stream](bool dataWasFlushed)
        {
            if (dataWasFlushed)
            {
                // Get the input stream for the anchor data.
                IInputStream^ inputStream = stream->GetInputStreamAt(0);
                return create_task(SpatialAnchorTransferManager::TryImportAnchorsAsync(inputStream));
            }
            else
            {
                return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
            }
        });
    }
    else
    {
        return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
    }
```

如果能够导入数据，我们将获取将字符串与定位点关联的键值对的地图视图。 我们可以将这些数据加载到自己的内存中数据收集中，并使用该集合查找我们感兴趣的定位点。

```
}).then([anchorMapOut](task<Windows::Foundation::Collections::IMapView<String^, SpatialAnchor^>^>  previousTask)
{
    try
    {
        auto importedAnchorsMap = previousTask.get();
        // If the operation was successful, we get a set of imported anchors.
        if (importedAnchorsMap != nullptr)
        {
            for each (auto& pair in importedAnchorsMap)
            {
                // Note that you could look for specific anchors here, if you know their key values.
                auto const& id = pair->Key;
                auto const& anchor = pair->Value;
                // Append "Remote" to the end of the anchor name for disambiguation.
                std::wstring idRemote(id->Data());
                idRemote += L"Remote";
                String^ idRemoteConst = ref new String (idRemote.c_str());
                // Store the anchor in the current in-memory anchor map.
                anchorMapOut->Insert(idRemoteConst, anchor);
            }
            return true;
        }
    }
    catch (Exception^ exception)
    {
        OutputDebugString(L"Error: Unable to import the anchor data buffer bytes into the in-memory anchor collection.\n");
    }
    return false;
});
}
```

**注意：** 正如可以导入定位点一样，并不一定意味着可以将其用于。 定位点可能位于其他房间，或完全位于另一个物理位置;在接收定位点的设备具有有关创建定位点的环境的足够可视信息之前，定位点将找不到，以还原定位点相对于已知当前环境的位置。 在继续尝试将定位点用于实时内容之前，客户端实现应尝试定位相对于本地坐标系或引用框架的定位点。 例如，尝试定期定位相对于当前坐标系的定位点，直到定位点开始可定位。

## <a name="special-considerations"></a>特殊注意事项

[TryExportAnchorsAsync](/uwp/api/Windows.Perception.Spatial.SpatialAnchorTransferManager) API 允许将多个[SpatialAnchors](/uwp/api/Windows.Perception.Spatial.SpatialAnchor)导出到同一不透明的二进制 blob 中。 但是，Blob 将包含哪些数据存在细微差异，具体取决于单个 SpatialAnchor 还是多个 SpatialAnchors 是在单个调用中导出的。

### <a name="export-of-a-single-spatialanchor"></a>导出单个 SpatialAnchor

Blob 在 SpatialAnchor 附近包含环境的表示形式，以便可以在导入 SpatialAnchor 的设备上识别环境。 导入完成后，新的 SpatialAnchor 将可供设备使用。 假设用户最近位于定位点附近，则定位点将可定位，并可以呈现附加到 SpatialAnchor 的全息影像。 这些全息影像会显示在导出 SpatialAnchor 的原始设备上相同的物理位置。

![导出单个 SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>导出多个 SpatialAnchors

与导出单个 SpatialAnchor 一样，Blob 包含所有指定 SpatialAnchors 邻近的环境中的表示形式。 此外，如果包含的 SpatialAnchors 位于同一物理空间中，则 blob 包含有关它们之间的连接的信息。 这意味着，如果导入两个附近的 SpatialAnchors，则即使设备仅识别第一个 SpatialAnchor 周围的环境，也能够找到附加到第二个 SpatialAnchor 的全息影像，因为 Blob 中包含了足够的数据来计算两个 SpatialAnchors 之间的转换。 如果分别导出了两个 SpatialAnchors (对 TryExportSpatialAnchors) 的两次单独调用，则 blob 中可能没有足够的数据，因此附加到第二个 SpatialAnchor 的全息影像在找到第一个 SpatialAnchor 时可能没有足够的数据。

![使用单个 TryExportAnchorsAsync 调用导出的多个定位点](images/multipleanchors.png) ![使用单独的 TryExportAnchorsAsync 调用导出的多个定位点](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>示例：使用 Windows：：Networking：：StreamSocket 发送定位点数据

在这里，我们提供了一个示例，了解如何通过 TCP 网络发送导出的定位点数据来使用导出的定位点数据。 这来自 HolographicSpatialAnchorTransferSample。

WinRT StreamSocket 类使用 PPL 任务库。 如果发生网络错误，则使用重新引发的异常将错误返回到链中的下一个任务。 异常包含指示错误状态的 HRESULT。

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>将 Windows：：Networking：：StreamSocketListener 与 TCP 一起用于发送导出的定位点数据

创建侦听连接的服务器实例。

```
void SampleAnchorTcpServer::ListenForConnection()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocketListener^ streamSocketListener = m_socketServer;
    if (streamSocketListener == nullptr)
    {
        OutputDebugString(L"Server listening for client.\n");
        // Create the web socket connection.
        streamSocketListener = ref new StreamSocketListener();
        streamSocketListener->Control->KeepAlive = true;
        streamSocketListener->BindEndpointAsync(
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        streamSocketListener->ConnectionReceived +=
            ref new Windows::Foundation::TypedEventHandler<StreamSocketListener^, StreamSocketListenerConnectionReceivedEventArgs^>(
                std::bind(&SampleAnchorTcpServer::OnConnectionReceived, this, _1, _2)
                );
        m_socketServer = streamSocketListener;
    }
    else
    {
        OutputDebugString(L"Error: Stream socket listener not created.\n");
    }
}
```

收到连接后，使用客户端套接字连接发送定位点数据。

```
void SampleAnchorTcpServer::OnConnectionReceived(StreamSocketListener^ listener, StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    m_socketForClient = args->Socket;
    if (m_socketForClient != nullptr)
    {
        // In this example, when the client first connects, we catch it up to the current state of our anchor set.
        OutputToClientSocket(m_spatialAnchorHelper->GetAnchorMap());
    }
}
```

现在，我们可以开始发送包含导出的定位点数据的数据流。

```
void SampleAnchorTcpServer::OutputToClientSocket(IMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    m_anchorTcpSocketStreamWriter = ref new DataWriter(m_socketForClient->OutputStream);
    OutputDebugString(L"Sending stream to client.\n");
    SendAnchorDataStream(anchorsToSend).then([this](task<bool> previousTask)
    {
        try
        {
            bool success = previousTask.get();
            if (success)
            {
                OutputDebugString(L"Anchor data sent!\n");
            }
            else
            {
                OutputDebugString(L"Error: Anchor data not sent.\n");
            }
        }
        catch (Exception^ exception)
        {
            HandleException(exception);
            OutputDebugString(L"Error: Anchor data was not sent.\n");
        }
    });
}
```

必须先发送标头数据包，然后才能发送流本身。 此标头数据包的长度必须为固定长度，并且还必须指示作为定位点数据流的可变字节数组的长度;对于本示例，我们没有要发送的其他标头数据，因此标头为 4 字节，包含 32 位无符号整数。

```
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataLengthMessage(size_t dataStreamLength)
{
    unsigned int arrayLength = dataStreamLength;
    byte* data = reinterpret_cast<byte*>(&arrayLength);
    m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    return create_task(m_anchorTcpSocketStreamWriter->StoreAsync()).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            OutputDebugString(L"Anchor data length stored in stream; Flushing stream.\n");
            return create_task(m_anchorTcpSocketStreamWriter->FlushAsync());
        }
        else
        {
            OutputDebugString(L"Error: Anchor data length not stored in stream.\n");
            return task_from_result<bool>(false);
        }
    });
}
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataStreamIMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    return SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
        &m_exportedAnchorStoreBytes,
        anchorsToSend
        ).then([this](bool anchorDataExported)
    {
        if (anchorDataExported)
        {
            const size_t arrayLength = m_exportedAnchorStoreBytes.size();
            if (arrayLength > 0)
            {
                OutputDebugString(L"Anchor data was exported; sending data stream length message.\n");
                return SendAnchorDataLengthMessage(arrayLength);
            }
        }
        OutputDebugString(L"Error: Anchor data was not exported.\n");
        // No data to send.
        return task_from_result<bool>(false);
```

将流长度（以字节为单位）发送到客户端后，我们可以继续将数据流本身写入套接字流。 这会使定位点存储字节发送到客户端。

```
}).then([this](bool dataLengthSent)
    {
        if (dataLengthSent)
        {
            OutputDebugString(L"Data stream length message sent; writing exported anchor store bytes to stream.\n");
            m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0], m_exportedAnchorStoreBytes.size()));
            return create_task(m_anchorTcpSocketStreamWriter->StoreAsync());
        }
        else
        {
            OutputDebugString(L"Error: Data stream length message not sent.\n");
            return task_from_result<size_t>(0);
        }
    }).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            PrintWstringToDebugConsole(
                std::to_wstring(bytesStored) +
                L" bytes of anchor data written and stored to stream; flushing stream.\n"
                );
        }
        else
        {
            OutputDebugString(L"Error: No anchor data bytes were written to the stream.\n");
        }
        return task_from_result<bool>(false);
    });
}
```

如本主题前面所述，我们必须准备好处理包含网络错误状态消息的异常。 对于意外的错误，我们可以将异常信息写入调试控制台，如下所示。 这将为我们提供一个线索，了解如果代码示例无法完成连接或无法完成定位点数据的发送，将发生的情况。

```
void SampleAnchorTcpServer::HandleException(Exception^ exception)
{
    PrintWstringToDebugConsole(
        std::wstring(L"Connection error: ") +
        exception->ToString()->Data() +
        L"\n"
        );
}
```

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>将 Windows：：Networking：：StreamSocket 与 TCP 一起用于接收导出的定位点数据

首先，我们必须连接到服务器。 此代码示例演示如何创建和配置 StreamSocket，以及创建可用于使用套接字连接获取网络数据的 DataReader。

**注意：** 如果运行此示例代码，请确保在启动客户端之前配置并启动服务器。

```
task<bool> SampleAnchorTcpClient::ConnectToServer()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocket^ streamSocket = m_socketClient;
    // Have we connected yet?
    if (m_socketClient == nullptr)
    {
        OutputDebugString(L"Client is attempting to connect to server.\n");
        EndpointPair^ endpointPair = ref new EndpointPair(
            SampleAnchorTcpCommon::m_clientHost,
            SampleAnchorTcpCommon::m_tcpPort,
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        // Create the web socket connection.
        m_socketClient = ref new StreamSocket();
        // The client connects to the server.
        return create_task(m_socketClient->ConnectAsync(endpointPair, SocketProtectionLevel::PlainSocket)).then([this](task<void> previousTask)
        {
            try
            {
                // Try getting all exceptions from the continuation chain above this point.
                previousTask.get();
                m_anchorTcpSocketStreamReader = ref new DataReader(m_socketClient->InputStream);
                OutputDebugString(L"Client connected!\n");
                m_anchorTcpSocketStreamReader->InputStreamOptions = InputStreamOptions::ReadAhead;
                WaitForAnchorDataStream();
                return true;
            }
            catch (Exception^ exception)
            {
                if (exception->HResult == 0x80072741)
                {
                    // This code sample includes a very simple implementation of client/server
                    // endpoint detection: if the current instance tries to connect to itself,
                    // it is determined to be the server.
                    OutputDebugString(L"Starting up the server instance.\n");
                    // When we return false, we'll start up the server instead.
                    return false;
                }
                else if ((exception->HResult == 0x8007274c) || // connection timed out
                    (exception->HResult == 0x80072740)) // connection maxed at server end
                {
                    // If the connection timed out, try again.
                    ConnectToServer();
                }
                else if (exception->HResult == 0x80072741)
                {
                    // No connection is possible.
                }
                HandleException(exception);
                return true;
            }
        });
    }
    else
    {
        OutputDebugString(L"A StreamSocket connection to a server already exists.\n");
        return task_from_result<bool>(true);
    }
}
```

建立连接后，可以等待服务器发送数据。 为此，我们在流数据读取器上调用 LoadAsync。

我们收到的第一组字节应始终为标头数据包，它指示上一节中所述的定位点数据流字节长度。

```
void SampleAnchorTcpClient::WaitForAnchorDataStream()
{
    if (m_anchorTcpSocketStreamReader == nullptr)
    {
        // We have not connected yet.
        return;
    }
    OutputDebugString(L"Waiting for server message.\n");
    // Wait for the first message, which specifies the byte length of the string data.
    create_task(m_anchorTcpSocketStreamReader->LoadAsync(SampleAnchorTcpCommon::c_streamHeaderByteArrayLength)).then([this](unsigned int numberOfBytes)
    {
        if (numberOfBytes > 0)
        {
            OutputDebugString(L"Server message incoming.\n");
            return ReceiveAnchorDataLengthMessage();
        }
        else
        {
            OutputDebugString(L"0-byte async task received, awaiting server message again.\n");
            WaitForAnchorDataStream();
            return task_from_result<size_t>(0);
        }
```

...

```
task<size_t> SampleAnchorTcpClient::ReceiveAnchorDataLengthMessage()
{
    byte data[4];
    m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    unsigned int lengthMessageSize = *reinterpret_cast<unsigned int*>(data);
    if (lengthMessageSize > 0)
    {
        OutputDebugString(L"One or more anchors to be received.\n");
        return task_from_result<size_t>(lengthMessageSize);
    }
    else
    {
        OutputDebugString(L"No anchors to be received.\n");
        ConnectToServer();
    }
    return task_from_result<size_t>(0);
}
```

收到标头数据包后，我们知道应期望的定位点数据字节数。 我们可以继续从流中读取这些字节。

```
}).then([this](size_t dataStreamLength)
    {
        if (dataStreamLength > 0)
        {
            std::wstring debugMessage = std::to_wstring(dataStreamLength);
            debugMessage += L" bytes of anchor data incoming.\n";
            OutputDebugString(debugMessage.c_str());
            // Prepare to receive the data stream in one or more pieces.
            m_anchorStreamLength = dataStreamLength;
            m_exportedAnchorStoreBytes.clear();
            m_exportedAnchorStoreBytes.resize(m_anchorStreamLength);
            OutputDebugString(L"Loading byte stream.\n");
            return ReceiveAnchorDataStream();
        }
        else
        {
            OutputDebugString(L"Error: Anchor data size not received.\n");
            ConnectToServer();
            return task_from_result<bool>(false);
        }
    });
}
```

下面是用于接收定位点数据流的代码。 同样，我们将首先从流加载字节;此操作可能需要一些时间才能完成，因为 StreamSocket 等待从网络接收该字节量。

加载操作完成后，我们可以读取该字节数。 如果收到定位点数据流预期字节数，可以继续导入定位点数据;如果不是，则一定存在某种错误。 例如，当服务器实例在可以完成发送数据流之前终止，或者网络在客户端可以接收整个数据流之前关闭时，可能会发生这种情况。

```
task<bool> SampleAnchorTcpClient::ReceiveAnchorDataStream()
{
    if (m_anchorStreamLength > 0)
    {
        // First, we load the bytes from the network socket.
        return create_task(m_anchorTcpSocketStreamReader->LoadAsync(m_anchorStreamLength)).then([this](size_t bytesLoadedByStreamReader)
        {
            if (bytesLoadedByStreamReader > 0)
            {
                // Once the bytes are loaded, we can read them from the stream.
                m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0],
                    bytesLoadedByStreamReader));
                // Check status.
                if (bytesLoadedByStreamReader == m_anchorStreamLength)
                {
                    // The whole stream has arrived. We can process the data.
                    // Informational message of progress complete.
                    std::wstring infoMessage = std::to_wstring(bytesLoadedByStreamReader);
                    infoMessage += L" bytes read out of ";
                    infoMessage += std::to_wstring(m_anchorStreamLength);
                    infoMessage += L" total bytes; importing the data.\n";
                    OutputDebugStringW(infoMessage.c_str());
                    // Kick off a thread to wait for a new message indicating another incoming anchor data stream.
                    WaitForAnchorDataStream();
                    // Process the data for the stream we just received.
                    return SpatialAnchorImportExportHelper::ImportAnchorDataAsync(m_exportedAnchorStoreBytes, m_spatialAnchorHelper->GetAnchorMap());
                }
                else
                {
                    OutputDebugString(L"Error: Fewer than expected anchor data bytes were received.\n");
                }
            }
            else
            {
                OutputDebugString(L"Error: No anchor bytes were received.\n");
            }
            return task_from_result<bool>(false);
        });
    }
    else
    {
        OutputDebugString(L"Warning: A zero-length data buffer was sent.\n");
        return task_from_result<bool>(false);
    }
}
```

同样，我们必须准备好处理未知的网络错误。

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

就这么简单！ 现在，你应该有足够的信息来尝试找到通过网络收到的定位点。 同样，请注意，客户端必须具有足够的可视跟踪数据，使空间能够成功找到定位点;如果无法立即正常工作，请尝试四处移动一段时间。 如果仍然不起作用，请让服务器发送更多定位点，并使用网络通信来同意适用于客户端的定位点。 你可以通过下载 HolographicSpatialAnchorTransferSample、配置客户端和服务器 ip 以及将其部署到客户端和服务器 HoloLens 设备来尝试此方法。

## <a name="see-also"></a>另请参阅
* [并行模式库 (PPL)](/cpp/parallel/concrt/parallel-patterns-library-ppl)
* [Windows。StreamSocket](/uwp/api/Windows.Networking.Sockets.StreamSocket)
* [Windows。StreamSocketListener](/uwp/api/Windows.Networking.Sockets.StreamSocketListener)