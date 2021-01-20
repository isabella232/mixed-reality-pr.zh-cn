---
title: Unity 中的持久性
description: 通过使用持久性，你的用户可以根据需要将各个全息影像固定在何处，然后在应用的许多用途中查找它。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens，持久性，Unity，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 7d12764dac2259388fe57d3924165783eab3dac5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583492"
---
# <a name="persistence-in-unity"></a>Unity 中的持久性

**命名空间：** *UnityEngine. XR*<br>
**类：** *WorldAnchorStore*

WorldAnchorStore 是创建全息体验的关键，其中全息在应用程序的实例上保持特定的实际位置。 然后，用户可以在所需位置固定各个全息影像，稍后在对应用程序的许多应用程序的同一位置进行查找。

## <a name="how-to-persist-holograms-across-sessions"></a>如何跨会话保留全息影像

WorldAnchorStore 可让你在不同的会话中持久保存 WorldAnchor 的位置。 若要在会话中实际保留全息影像，需要单独跟踪使用特定世界锚点的 Gameobject。 通常，使用世界定位点创建 GameObject 根是有意义的，并使子影像由其定位到本地位置偏移量。

从以前的会话加载全息影像：
1. 获取 WorldAnchorStore
2. 加载与世界定位点相关的应用数据，它提供世界锚的 ID
3. 从其 ID 加载世界定位点

为将来的会话保存全息影像：
1. 获取 WorldAnchorStore
2. 保存指定 ID 的世界定位点
3. 保存与世界锚点相关的应用数据以及 ID

### <a name="getting-the-worldanchorstore"></a>获取 WorldAnchorStore

您需要保留对 WorldAnchorStore 的引用，以便您知道何时可以执行某个操作。 由于这是一个异步调用，可能很快就会启动，因此需要调用：

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

在此示例中，StoreLoaded 是 WorldAnchorStore 完成加载时的处理程序：

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

现在，我们有了一个对 WorldAnchorStore 的引用，我们将使用它来保存和加载特定世界锚。

### <a name="saving-a-worldanchor"></a>保存 WorldAnchor

若要保存，只需命名要保存的内容，并将其传递到 WorldAnchor 我们要保存的时间。 注意：尝试将两个定位点保存到相同的字符串将 (存储中失败。Save 将返回 false) 。 保存新的 save 之前，请先将其删除：

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

并加载：

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

我们还可以使用 store。删除 ( # A1 删除之前保存并存储的定位点。清除 ( # A3 以删除以前保存的所有数据。

### <a name="enumerating-existing-anchors"></a>枚举现有锚

若要发现以前存储的定位点，请调用 GetAllIds。

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>为多台设备保留全息影像

你可以使用 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a> 从本地 WorldAnchor 创建持久的云锚点，你的应用可以在多个 HoloLens、IOS 和 Android 设备上查找，即使这些设备同时不存在。  由于云锚点是永久性的，随着时间的推移，多台设备可以看到相对于同一物理位置中的定位点呈现的内容。

若要开始在 Unity 中构建共享体验，请尝试执行5分钟的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间锚点 Unity 快速入门</a>。

启动并运行 Azure 空间锚点后，便可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中创建和定位锚</a>。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所说的 Unity 开发检查点旅程，就是探索混合现实核心构建基块的过程。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [空间映射](spatial-mapping-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅
* [空间锚点持久性](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">用于 Unity 的 Azure 空间定位点 SDK</a>