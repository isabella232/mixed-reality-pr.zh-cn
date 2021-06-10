---
ms.openlocfilehash: 96da41f28533c227fb106d8842907747f34098ec
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2021
ms.locfileid: "110349922"
---
# <a name="world-locking-tools-recommended"></a>[世界锁定工具 (推荐) ](#tab/wlt)

默认情况下，世界锁定工具将跨会话还原 Unity 相对于物理世界坐标系。 这意味着，在进入和重新运行应用程序后，若要让全息影像在物理世界中显示相同的位置，则全息影像只需再次具有相同的"姿势"。

![Unity 检查器中的世界锁定上下文组件](../../images/world-locking-tools-img-02.png)

如果应用程序需要更精细的控制，可以在检查器中禁用自动保存和自动加载，并按文档 的持久性部分中所述从脚本管理[持久性。](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html)

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

使用名为 **XRAnchorStore** 的其他 API，可以在会话之间持久保存定位点。 XRAnchorStore 是设备上保存的定位点的表示形式。 可以从 Unity 场景中的 **ARAnchors** 持久保存定位点，从存储加载到新的 **ARAnchors** 中，或者从存储中删除定位点。

> [!NOTE]
> 这些定位点将保存并加载到同一设备上。 在将来的版本中，通过 Azure 空间定位点支持跨设备定位点存储。

### <a name="namespaces"></a>命名空间

对于 **Unity 2020 和 OpenXR：** 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

或 **Unity 2019/2020 + Windows XR 插件**： 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a>公共方法

```cs 
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

### <a name="getting-an-anchor-store-reference"></a>获取定位点存储引用 

若要使用 **Unity 2020 和 OpenXR** 加载 XRAnchorStore，请使用 XRAnchorSubsystem（ARAnchorManager 的子系统）上的扩展方法：

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

若要使用 **Unity 2019/2020** 和 Windows XR 插件加载 XRAnchorStore，请使用 XRReferencePointSubsystem (Unity 2019) 或 XRAnchorSubsystem (Unity 2020) （ARReferencePointManager/ARAnchorManager 的子系统）上的扩展方法：

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a>加载定位点存储

若要在 **Unity 2020 和 OpenXR** 中加载定位点存储，请从 ARAnchorManager 的子系统访问它，如下所示：

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

或者使用 **Unity 2019/2020 和 Windows XR 插件**：

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

若要查看保留/取消持久化定位点的完整示例，请查看混合现实 [OpenXR](../../openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2)插件示例场景中的定位点 -> 定位点示例 GameObject 和 AnchorsSample.cs 脚本：

![在 Unity 编辑器中打开的层次结构面板的屏幕截图，其中突出显示了定位点示例](../../images/openxr-features-img-04.png)

![Unity 编辑器中打开的检查器面板的屏幕截图，其中突出显示了定位点示例脚本](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

**WorldAnchorStore** 是创建全息体验的关键，全息影像位于应用程序实例的特定真实位置。 然后，用户可以将单个全息影像固定到任何想要的位置，并稍后在同一位置找到它们，而多次使用你的应用。

**命名空间***：UnityEngine.XR.WSA.Persistence*<br>
**类***：WorldAnchorStore*

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

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

在这种情况下，StoreLoaded 是 WorldAnchorStore 完成加载时处理程序：

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

现在，我们引用了 WorldAnchorStore，我们将使用它来保存和加载特定的世界定位点。

### <a name="saving-a-worldanchor"></a>保存 WorldAnchor

若要保存，只需命名要保存的名称，并将其传递到之前要保存的 WorldAnchor 中。 注意：尝试将两个定位点保存到同一字符串将失败 (存储。Save 将返回 false) 。 在保存新保存之前删除以前的保存：

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

要加载的 和 ：

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

此外，我们可以使用 store。删除 () 删除之前保存和存储的定位点。清除 () 删除以前保存的所有数据。

### <a name="enumerating-existing-anchors"></a>枚举现有定位点

若要发现以前存储的定位点，请调用 GetAllIds。

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>保留多个设备的全息影像

可以使用 <a href="/azure/spatial-anchors/overview" target="_blank">Azure</a> 空间定位点从本地 WorldAnchor 创建持久云定位点，然后应用可跨多个 HoloLens、iOS 和 Android 设备找到该定位点，即使这些设备同时不在一起。  由于云定位点是持久性的，因此随着时间的推移，多个设备都可以在同一物理位置查看相对于该定位点呈现的内容。

若要开始在 Unity 中构建共享体验，请尝试 5 分钟的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间定位点 Unity 快速入门</a>。

使用 Azure 空间定位点启动并运行后，可以在 Unity 中创建 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">和查找定位点</a>。
