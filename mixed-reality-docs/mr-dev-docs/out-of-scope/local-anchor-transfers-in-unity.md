---
title: Unity 中的本地定位点传输
description: 了解如何在 Unity 混合现实应用程序中HoloLens设备之间传输定位点。
author: fieldsjacksong
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: 共享、定位点、WorldAnchor、MR 共享 250、WorldAnchorTransferBatch、SpatialPerception、传输、本地定位点传输、定位点导出、定位点导入
ms.openlocfilehash: eaf25edbae39aab628277aa29f975f3d4d9d7374c796fd1b7b159053d4a46b95
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189124"
---
# <a name="local-anchor-transfers-in-unity"></a>Unity 中的本地定位点传输

在无法使用<a href="/azure/spatial-anchors" target="_blank">Azure</a>空间定位点的情况下，本地定位点传输使一HoloLens设备能够导出要由第二个设备导入HoloLens定位点。

>[!NOTE]
>与 <a href="/azure/spatial-anchors" target="_blank">Azure</a>空间定位点相比，本地定位点传输提供更可靠的定位点召回，此方法不支持 iOS 和 Android 设备。

### <a name="setting-the-spatialperception-capability"></a>设置 SpatialPerception 功能

为了使应用能够传输空间定位点，必须启用 *SpatialPerception* 功能。

如何启用 *SpatialPerception* 功能：
1. 在 Unity 编辑器中，打开"**播放器设置"** 窗格 ("编辑> Project 设置 >播放器) 
2. 单击"Windows **Store"** 选项卡
3. 展开 **"发布设置"，** 并检查"功能"列表中的 **"SpatialPerception"** 功能

>[!NOTE]
>如果已将 Unity 项目导出到 Visual Studio 解决方案，则需要导出到新文件夹，或在 Visual Studio 的[AppxManifest 中手动设置此功能](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。

### <a name="anchor-transfer"></a>定位点传输

**命名空间***：UnityEngine.XR.WSA.Sharing*<br>
**类型***：WorldAnchorTransferBatch*

若要传输 [WorldAnchor，](../develop/unity/coordinate-systems-in-unity.md)必须建立要传输的定位点。 其中一个HoloLens扫描其环境，并手动或以编程方式选择空间中的点作为共享体验的定位点。 然后，可以序列化表示此点的数据，并传输到体验中共享的其他设备。 然后，每个设备对定位点数据进行反序列化，并尝试在空间中查找该点。 若要使定位点传输正常工作，每台设备都必须在足够的环境中进行扫描，以便可以识别定位点表示的点。

### <a name="setup"></a>设置

此页上的示例代码包含几个需要初始化的字段：
1. *GameObject rootGameObject* 是 Unity 中的 *GameObject，* 其上具有 *WorldAnchor* 组件。 共享体验中的一个用户将放置此 *GameObject，* 将数据导出到其他用户。
2. *WorldAnchor gameRootAnchor* 是 *rootGameObject* 上的 *UnityEngine.XR.WSA.WorldAnchor。*
3. *byte[] importedData* 是每个客户端通过网络接收的序列化定位点的字节数组。

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a>导出

若要导出，我们只需要一个 *WorldAnchor，* 并知道我们将调用它，这样它才对接收应用有意义。 共享体验中的一个客户端将执行以下步骤来导出共享定位点：
1. 创建 *WorldAnchorTransferBatch*
2. 添加 *要传输的 WorldAnchors*
3. 开始导出
4. 在数据 *可用时处理 OnExportDataAvailable* 事件
5. 处理 *OnExportComplete* 事件

我们将创建 *一个 WorldAnchorTransferBatch* 来封装要传输的数据，然后将它导出为字节：

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

当数据可用时，在数据段可用时将字节发送到客户端或缓冲区，并通过所需的任何方式发送：

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

导出完成后，如果传输数据且序列化失败，请告知客户端放弃数据。 如果序列化成功，请告知客户端所有数据已传输，导入可以启动：

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a>导入

从发送方接收所有字节后，我们可以将数据导入回 *WorldAnchorTransferBatch，* 将根游戏对象锁定到同一物理位置。 注意：导入有时会暂时性失败，需要重试：

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

通过 *LockObject* 调用锁定 *GameObject* 后，它将具有一个 *WorldAnchor，* 它将保持它处于世界上相同的物理位置，但它可能位于 Unity 坐标空间中与其他用户不同的位置。