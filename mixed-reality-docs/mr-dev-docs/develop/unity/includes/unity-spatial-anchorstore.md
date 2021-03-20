---
ms.openlocfilehash: bb2df8c85dd05981c1438bdb076b0aad16c7efd7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719917"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

另外一个名为 **XRAnchorStore** 的 API 允许在会话之间保留定位点。 XRAnchorStore 是设备上保存的定位点的表示形式。 定位点可以从 Unity 场景中的 **ARAnchors** 保存、从存储加载到新 **ARAnchors** 或从存储中删除。

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

若要查看保留/unpersisting 定位点的完整示例，请查看 [Mixed Reality OpenXR 插件示例场景](../openxr-getting-started.md#hololens-2-samples)中的定位点 > 定位点示例 GameObject 和 AnchorsSample 脚本：

![在 Unity 编辑器中打开的 "层次结构" 面板的屏幕截图，其中突出显示了定位点示例](../images/openxr-features-img-04.png)

![在 Unity 编辑器中打开的检查器面板屏幕截图，其中突出显示了定位点示例脚本](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 插件](#tab/winxr)

名为 **XRAnchorStore** 的 API 允许在会话之间保留定位点。 XRAnchorStore 是设备上保存的定位点的表示形式。 定位点可以从 Unity 场景中的 **ARAnchors** 保存、从存储加载到新 **ARAnchors** 或从存储中删除。

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

**WorldAnchorStore** 是创建全息体验的关键，其中全息在应用程序的实例上保持特定的实际位置。 然后，用户可以在所需位置固定各个全息影像，稍后在对应用程序的许多应用程序的同一位置进行查找。

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

## <a name="persisting-holograms-for-multiple-devices"></a>为多台设备保留全息影像

你可以使用 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a> 从本地 WorldAnchor 创建持久的云锚点，你的应用可以在多个 HoloLens、IOS 和 Android 设备上查找，即使这些设备同时不存在。  由于云锚点是永久性的，随着时间的推移，多台设备可以看到相对于同一物理位置中的定位点呈现的内容。

若要开始在 Unity 中构建共享体验，请尝试执行5分钟的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间锚点 Unity 快速入门</a>。

启动并运行 Azure 空间锚点后，便可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中创建和定位锚</a>。
