---
title: Unity 中的持久性
description: 持久性允许用户将单个全息影像固定到任何位置，然后在应用的许多用途中稍后找到它。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、持久性、Unity、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备
ms.openlocfilehash: 9283191c024cbe33ecda3946a4e9bcbd5f3708c21a3578484b547207ee70a49b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208967"
---
# <a name="persistence-in-unity"></a>Unity 中的持久性

**命名空间***：UnityEngine.XR.WSA.Persistence*<br>
**类***：WorldAnchorStore*

WorldAnchorStore 是创建全息体验的关键，全息影像位于应用程序实例的特定真实位置。 然后，用户可以将单个全息影像固定到任何想要的位置，并稍后在同一位置找到它们，而多次使用你的应用。

## <a name="how-to-persist-holograms-across-sessions"></a>如何跨会话保留全息影像

使用 WorldAnchorStore，可以跨会话保留 WorldAnchor 的位置。 若要实际跨会话保留全息影像，需要单独跟踪使用特定世界定位点的 GameObject。 通常，使用世界定位点创建 GameObject 根目录，并且使用本地位置偏移量锚定子全息影像。

从以前的会话中加载全息影像：
1. 获取 WorldAnchorStore
2. 加载与世界定位点相关的应用数据，这些数据提供世界定位点的 ID
3. 从世界定位点 ID 加载世界定位点

保存全息影像供将来会话使用：
1. 获取 WorldAnchorStore
2. 保存指定 ID 世界定位点
3. 保存与世界定位点相关的应用数据以及 ID

### <a name="getting-the-worldanchorstore"></a>获取 WorldAnchorStore

你需要保留对 WorldAnchorStore 的引用，以便知道何时可以执行操作。 由于这是一个异步调用，因此可能需要在启动后立即调用：

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

在这种情况下，StoreLoaded 是 WorldAnchorStore 完成加载时处理程序：

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

现在，我们引用了 WorldAnchorStore，我们将使用它来保存和加载特定的世界定位点。

### <a name="saving-a-worldanchor"></a>保存 WorldAnchor

若要保存，只需命名要保存的名称，并将其传递到之前要保存的 WorldAnchor 中。 注意：尝试将两个定位点保存到同一字符串将失败 (存储。Save 将返回 false) 。 在保存新保存之前删除以前的保存：

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a>加载 WorldAnchor

要加载的 和 ：

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

此外，我们可以使用 store。删除 () 删除之前保存和存储的定位点。清除 () 删除以前保存的所有数据。

### <a name="enumerating-existing-anchors"></a>枚举现有定位点

若要发现以前存储的定位点，请调用 GetAllIds。

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>保留多个设备的全息影像

可以使用<a href="/azure/spatial-anchors/overview" target="_blank">Azure</a>空间定位点从本地 WorldAnchor 创建持久云定位点，然后应用可以在多个 HoloLens、iOS 和 Android 设备上找到它，即使这些设备同时不在一起。  由于云定位点是持久性的，因此随着时间的推移，多个设备都可以在同一物理位置查看相对于该定位点呈现的内容。

若要开始在 Unity 中构建共享体验，请尝试 5 分钟的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间定位点 Unity 快速入门</a>。

使用 Azure 空间定位点启动并运行后，可以在 Unity 中创建 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">和查找定位点</a>。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们布局的 Unity 开发检查点之旅，则你正在探索混合现实核心构建基块。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [空间映射](spatial-mapping-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅
* [空间定位点持久性](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">适用于 Unity 的 Azure 空间定位点 SDK</a>