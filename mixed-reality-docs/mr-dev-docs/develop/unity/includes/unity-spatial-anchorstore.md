---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603373"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

> [!NOTE]
> 这些定位点将保存并加载到同一设备上。 未来版本中将通过 Azure 空间锚点支持跨设备锚定存储。

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

若要加载 XRAnchorStore，该插件会在 XRAnchorSubsystem （ARAnchorManager 的子系统）上提供扩展方法：

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

若要使用此扩展方法，请按如下所示从 ARAnchorManager 的子系统访问它：

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

若要查看保留/unpersisting 定位点的完整示例，请查看 [Mixed Reality OpenXR 插件示例场景](../openxr-getting-started.md#hololens-2-samples)中的定位点 > 锚样品 GameObject 和 AnchorsSample.cs 脚本：

![在 Unity 编辑器中打开的 "层次结构" 面板的屏幕截图，其中突出显示了定位点示例](../images/openxr-features-img-04.png)

![在 Unity 编辑器中打开的检查器面板屏幕截图，其中突出显示了定位点示例脚本](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 插件](#tab/winxr)

> [!NOTE]
> 这些定位点将保存并加载到同一设备上。 未来版本中将通过 Azure 空间锚点支持跨设备锚定存储。

``` cs
public class UnityEngine.XR.WindowsMR.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(TrackableId id, string name);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

若要加载 XRAnchorStore，该插件在 XRReferencePointSubsystem (Unity 2019) 或 XRAnchorSubsystem (Unity 2020) （ARReferencePointManager/ARAnchorManager 的子系统）上提供扩展方法：

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

若要使用此扩展方法，请按以下方式从 ARAnchorManager 的子系统访问它： Unity 2019：

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

对于 Unity 2020：

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)

**命名空间：** *UnityEngine. XR*<br>
**类：** *WorldAnchorStore*

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

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

在此示例中，StoreLoaded 是 WorldAnchorStore 完成加载时的处理程序：

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

现在，我们有了一个对 WorldAnchorStore 的引用，我们将使用它来保存和加载特定世界锚。

### <a name="saving-a-worldanchor"></a>保存 WorldAnchor

若要保存，只需命名要保存的内容，并将其传递到 WorldAnchor 我们要保存的时间。 注意：尝试将两个定位点保存到相同的字符串将 (存储中失败。Save 将返回 false) 。 保存新的 save 之前，请先将其删除：

```cs
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

```cs
private void LoadGame()
{
    // Save data about holograms positioned by this world anchor
    this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
    if (!this.savedRoot)
    {
        s// We didn't actually have the game root saved! We have to re-place our objects or start over
    }
}
```

我们还可以使用 store。删除 () 删除之前保存并存储的定位点。清除 () 删除以前保存的所有数据。

### <a name="enumerating-existing-anchors"></a>枚举现有锚

若要发现以前存储的定位点，请调用 GetAllIds。

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="building-a-world-scale-experience"></a>构建全球范围的体验

**命名空间：** *UnityEngine. XR*<br>
**类型：** *WorldAnchor*

对于 HoloLens 上真正的 **全球规模体验** ，让用户游离5米以上，你将需要超出用于房间规模体验的新技术。 你将使用的一项关键方法是创建一个 [空间定位点](../../../design/coordinate-systems.md#spatial-anchors) ，以便在物理世界中精确地锁定影像的分类，无论用户漫游到多远，然后 [在以后的会话中再次查找这些全息影像](../../../design/coordinate-systems.md#spatial-anchor-persistence)。

在 Unity 中，可以通过将 **WorldAnchor** Unity 组件添加到 GameObject 来创建空间锚。

### <a name="adding-a-world-anchor"></a>添加世界锚

若要添加世界定位点，请 `AddComponent<WorldAnchor>()` 使用要锚定的转换，对游戏对象调用。

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

就这么简单！ 现在，此游戏对象将锚定到其在物理世界中的当前位置-你可能会看到其 Unity 世界坐标在一段时间后会略微调整，以确保物理对齐。 请参阅 [加载世界定位点](#loading-a-worldanchor) ，在未来的应用程序会话中再次查找此定位位置。

### <a name="removing-a-world-anchor"></a>删除世界锚

如果不再希望 GameObject 锁定到物理世界位置，并且不打算将其移动到此帧，则可以只在世界锚点组件上调用销毁。

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

如果要将 GameObject 移动到此帧，则需改为调用 DestroyImmediate。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>移动世界定位的 GameObject

GameObject 在世界锚点上时无法移动。 如果需要将 GameObject 移动到此框架，需要执行以下操作：

1. DestroyImmediate 世界锚组件
2. 移动 GameObject
3. 向 GameObject 添加新的世界锚点组件。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>处理 Locatability 更改

在物理环境中，可能无法在某个时间点定位 WorldAnchor。 如果出现这种情况，则 Unity 不会更新定位对象的转换。 在应用程序运行时，这也可能会更改。 如果无法处理 locatability 中的更改，则会导致对象不显示在世界上正确的物理位置。

若要获得有关 locatability 更改的通知：

1. 订阅 OnTrackingChanged 事件
2. 处理事件

每当基础空间锚点在正在定位的状态与不能定位的状态之间发生变化时，将调用 **OnTrackingChanged** 事件。

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

然后处理事件：

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

有时会立即定位锚点。 在这种情况下，当 AddComponent () 返回时，定位点的 isLocated 属性将设置为 true <WorldAnchor> 。 因此，不会触发 OnTrackingChanged 事件。 清理模式是在附加定位点后使用初始 IsLocated 状态调用 OnTrackingChanged 处理程序。

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a>为多台设备保留全息影像

你可以使用 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a> 从本地 WorldAnchor 创建持久的云锚点，你的应用可以在多个 HoloLens、IOS 和 Android 设备上查找，即使这些设备同时不存在。  由于云锚点是永久性的，随着时间的推移，多台设备可以看到相对于同一物理位置中的定位点呈现的内容。

若要开始在 Unity 中构建共享体验，请尝试执行5分钟的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间锚点 Unity 快速入门</a>。

启动并运行 Azure 空间锚点后，便可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中创建和定位锚</a>。
