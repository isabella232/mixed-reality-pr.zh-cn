---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603373"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="8efaf-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="8efaf-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

> [!NOTE]
> <span data-ttu-id="8efaf-102">这些定位点将保存并加载到同一设备上。</span><span class="sxs-lookup"><span data-stu-id="8efaf-102">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="8efaf-103">未来版本中将通过 Azure 空间锚点支持跨设备锚定存储。</span><span class="sxs-lookup"><span data-stu-id="8efaf-103">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="8efaf-104">若要加载 XRAnchorStore，该插件会在 XRAnchorSubsystem （ARAnchorManager 的子系统）上提供扩展方法：</span><span class="sxs-lookup"><span data-stu-id="8efaf-104">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="8efaf-105">若要使用此扩展方法，请按如下所示从 ARAnchorManager 的子系统访问它：</span><span class="sxs-lookup"><span data-stu-id="8efaf-105">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="8efaf-106">若要查看保留/unpersisting 定位点的完整示例，请查看 [Mixed Reality OpenXR 插件示例场景](../openxr-getting-started.md#hololens-2-samples)中的定位点 > 锚样品 GameObject 和 AnchorsSample.cs 脚本：</span><span class="sxs-lookup"><span data-stu-id="8efaf-106">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![在 Unity 编辑器中打开的 "层次结构" 面板的屏幕截图，其中突出显示了定位点示例](../images/openxr-features-img-04.png)

![在 Unity 编辑器中打开的检查器面板屏幕截图，其中突出显示了定位点示例脚本](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="8efaf-109">Unity 2019/2020 + Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="8efaf-109">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

> [!NOTE]
> <span data-ttu-id="8efaf-110">这些定位点将保存并加载到同一设备上。</span><span class="sxs-lookup"><span data-stu-id="8efaf-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="8efaf-111">未来版本中将通过 Azure 空间锚点支持跨设备锚定存储。</span><span class="sxs-lookup"><span data-stu-id="8efaf-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="8efaf-112">若要加载 XRAnchorStore，该插件在 XRReferencePointSubsystem (Unity 2019) 或 XRAnchorSubsystem (Unity 2020) （ARReferencePointManager/ARAnchorManager 的子系统）上提供扩展方法：</span><span class="sxs-lookup"><span data-stu-id="8efaf-112">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="8efaf-113">若要使用此扩展方法，请按以下方式从 ARAnchorManager 的子系统访问它： Unity 2019：</span><span class="sxs-lookup"><span data-stu-id="8efaf-113">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="8efaf-114">对于 Unity 2020：</span><span class="sxs-lookup"><span data-stu-id="8efaf-114">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="8efaf-115">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="8efaf-115">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="8efaf-116">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="8efaf-116">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="8efaf-117">**类：** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="8efaf-117">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="8efaf-118">WorldAnchorStore 可让你在不同的会话中持久保存 WorldAnchor 的位置。</span><span class="sxs-lookup"><span data-stu-id="8efaf-118">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="8efaf-119">若要在会话中实际保留全息影像，需要单独跟踪使用特定世界锚点的 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="8efaf-119">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="8efaf-120">通常，使用世界定位点创建 GameObject 根是有意义的，并使子影像由其定位到本地位置偏移量。</span><span class="sxs-lookup"><span data-stu-id="8efaf-120">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="8efaf-121">从以前的会话加载全息影像：</span><span class="sxs-lookup"><span data-stu-id="8efaf-121">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="8efaf-122">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="8efaf-122">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="8efaf-123">加载与世界定位点相关的应用数据，它提供世界锚的 ID</span><span class="sxs-lookup"><span data-stu-id="8efaf-123">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="8efaf-124">从其 ID 加载世界定位点</span><span class="sxs-lookup"><span data-stu-id="8efaf-124">Load a world anchor from its ID</span></span>

<span data-ttu-id="8efaf-125">为将来的会话保存全息影像：</span><span class="sxs-lookup"><span data-stu-id="8efaf-125">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="8efaf-126">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="8efaf-126">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="8efaf-127">保存指定 ID 的世界定位点</span><span class="sxs-lookup"><span data-stu-id="8efaf-127">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="8efaf-128">保存与世界锚点相关的应用数据以及 ID</span><span class="sxs-lookup"><span data-stu-id="8efaf-128">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="8efaf-129">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="8efaf-129">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="8efaf-130">您需要保留对 WorldAnchorStore 的引用，以便您知道何时可以执行某个操作。</span><span class="sxs-lookup"><span data-stu-id="8efaf-130">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="8efaf-131">由于这是一个异步调用，可能很快就会启动，因此需要调用：</span><span class="sxs-lookup"><span data-stu-id="8efaf-131">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="8efaf-132">在此示例中，StoreLoaded 是 WorldAnchorStore 完成加载时的处理程序：</span><span class="sxs-lookup"><span data-stu-id="8efaf-132">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="8efaf-133">现在，我们有了一个对 WorldAnchorStore 的引用，我们将使用它来保存和加载特定世界锚。</span><span class="sxs-lookup"><span data-stu-id="8efaf-133">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="8efaf-134">保存 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="8efaf-134">Saving a WorldAnchor</span></span>

<span data-ttu-id="8efaf-135">若要保存，只需命名要保存的内容，并将其传递到 WorldAnchor 我们要保存的时间。</span><span class="sxs-lookup"><span data-stu-id="8efaf-135">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="8efaf-136">注意：尝试将两个定位点保存到相同的字符串将 (存储中失败。Save 将返回 false) 。</span><span class="sxs-lookup"><span data-stu-id="8efaf-136">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="8efaf-137">保存新的 save 之前，请先将其删除：</span><span class="sxs-lookup"><span data-stu-id="8efaf-137">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="8efaf-138">加载 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="8efaf-138">Loading a WorldAnchor</span></span>

<span data-ttu-id="8efaf-139">并加载：</span><span class="sxs-lookup"><span data-stu-id="8efaf-139">And to load:</span></span>

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

<span data-ttu-id="8efaf-140">我们还可以使用 store。删除 () 删除之前保存并存储的定位点。清除 () 删除以前保存的所有数据。</span><span class="sxs-lookup"><span data-stu-id="8efaf-140">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="8efaf-141">枚举现有锚</span><span class="sxs-lookup"><span data-stu-id="8efaf-141">Enumerating Existing Anchors</span></span>

<span data-ttu-id="8efaf-142">若要发现以前存储的定位点，请调用 GetAllIds。</span><span class="sxs-lookup"><span data-stu-id="8efaf-142">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="8efaf-143">构建全球范围的体验</span><span class="sxs-lookup"><span data-stu-id="8efaf-143">Building a world-scale experience</span></span>

<span data-ttu-id="8efaf-144">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="8efaf-144">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="8efaf-145">**类型：** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="8efaf-145">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="8efaf-146">对于 HoloLens 上真正的 **全球规模体验** ，让用户游离5米以上，你将需要超出用于房间规模体验的新技术。</span><span class="sxs-lookup"><span data-stu-id="8efaf-146">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="8efaf-147">你将使用的一项关键方法是创建一个 [空间定位点](../../../design/coordinate-systems.md#spatial-anchors) ，以便在物理世界中精确地锁定影像的分类，无论用户漫游到多远，然后 [在以后的会话中再次查找这些全息影像](../../../design/coordinate-systems.md#spatial-anchor-persistence)。</span><span class="sxs-lookup"><span data-stu-id="8efaf-147">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="8efaf-148">在 Unity 中，可以通过将 **WorldAnchor** Unity 组件添加到 GameObject 来创建空间锚。</span><span class="sxs-lookup"><span data-stu-id="8efaf-148">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="8efaf-149">添加世界锚</span><span class="sxs-lookup"><span data-stu-id="8efaf-149">Adding a World Anchor</span></span>

<span data-ttu-id="8efaf-150">若要添加世界定位点，请 `AddComponent<WorldAnchor>()` 使用要锚定的转换，对游戏对象调用。</span><span class="sxs-lookup"><span data-stu-id="8efaf-150">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="8efaf-151">就这么简单！</span><span class="sxs-lookup"><span data-stu-id="8efaf-151">That's it!</span></span> <span data-ttu-id="8efaf-152">现在，此游戏对象将锚定到其在物理世界中的当前位置-你可能会看到其 Unity 世界坐标在一段时间后会略微调整，以确保物理对齐。</span><span class="sxs-lookup"><span data-stu-id="8efaf-152">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="8efaf-153">请参阅 [加载世界定位点](#loading-a-worldanchor) ，在未来的应用程序会话中再次查找此定位位置。</span><span class="sxs-lookup"><span data-stu-id="8efaf-153">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="8efaf-154">删除世界锚</span><span class="sxs-lookup"><span data-stu-id="8efaf-154">Removing a World Anchor</span></span>

<span data-ttu-id="8efaf-155">如果不再希望 GameObject 锁定到物理世界位置，并且不打算将其移动到此帧，则可以只在世界锚点组件上调用销毁。</span><span class="sxs-lookup"><span data-stu-id="8efaf-155">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="8efaf-156">如果要将 GameObject 移动到此帧，则需改为调用 DestroyImmediate。</span><span class="sxs-lookup"><span data-stu-id="8efaf-156">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="8efaf-157">移动世界定位的 GameObject</span><span class="sxs-lookup"><span data-stu-id="8efaf-157">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="8efaf-158">GameObject 在世界锚点上时无法移动。</span><span class="sxs-lookup"><span data-stu-id="8efaf-158">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="8efaf-159">如果需要将 GameObject 移动到此框架，需要执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="8efaf-159">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="8efaf-160">DestroyImmediate 世界锚组件</span><span class="sxs-lookup"><span data-stu-id="8efaf-160">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="8efaf-161">移动 GameObject</span><span class="sxs-lookup"><span data-stu-id="8efaf-161">Move the GameObject</span></span>
3. <span data-ttu-id="8efaf-162">向 GameObject 添加新的世界锚点组件。</span><span class="sxs-lookup"><span data-stu-id="8efaf-162">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="8efaf-163">处理 Locatability 更改</span><span class="sxs-lookup"><span data-stu-id="8efaf-163">Handling Locatability Changes</span></span>

<span data-ttu-id="8efaf-164">在物理环境中，可能无法在某个时间点定位 WorldAnchor。</span><span class="sxs-lookup"><span data-stu-id="8efaf-164">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="8efaf-165">如果出现这种情况，则 Unity 不会更新定位对象的转换。</span><span class="sxs-lookup"><span data-stu-id="8efaf-165">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="8efaf-166">在应用程序运行时，这也可能会更改。</span><span class="sxs-lookup"><span data-stu-id="8efaf-166">This also can change while an app is running.</span></span> <span data-ttu-id="8efaf-167">如果无法处理 locatability 中的更改，则会导致对象不显示在世界上正确的物理位置。</span><span class="sxs-lookup"><span data-stu-id="8efaf-167">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="8efaf-168">若要获得有关 locatability 更改的通知：</span><span class="sxs-lookup"><span data-stu-id="8efaf-168">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="8efaf-169">订阅 OnTrackingChanged 事件</span><span class="sxs-lookup"><span data-stu-id="8efaf-169">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="8efaf-170">处理事件</span><span class="sxs-lookup"><span data-stu-id="8efaf-170">Handle the event</span></span>

<span data-ttu-id="8efaf-171">每当基础空间锚点在正在定位的状态与不能定位的状态之间发生变化时，将调用 **OnTrackingChanged** 事件。</span><span class="sxs-lookup"><span data-stu-id="8efaf-171">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="8efaf-172">然后处理事件：</span><span class="sxs-lookup"><span data-stu-id="8efaf-172">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="8efaf-173">有时会立即定位锚点。</span><span class="sxs-lookup"><span data-stu-id="8efaf-173">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="8efaf-174">在这种情况下，当 AddComponent () 返回时，定位点的 isLocated 属性将设置为 true <WorldAnchor> 。</span><span class="sxs-lookup"><span data-stu-id="8efaf-174">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="8efaf-175">因此，不会触发 OnTrackingChanged 事件。</span><span class="sxs-lookup"><span data-stu-id="8efaf-175">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="8efaf-176">清理模式是在附加定位点后使用初始 IsLocated 状态调用 OnTrackingChanged 处理程序。</span><span class="sxs-lookup"><span data-stu-id="8efaf-176">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="8efaf-177">为多台设备保留全息影像</span><span class="sxs-lookup"><span data-stu-id="8efaf-177">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="8efaf-178">你可以使用 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a> 从本地 WorldAnchor 创建持久的云锚点，你的应用可以在多个 HoloLens、IOS 和 Android 设备上查找，即使这些设备同时不存在。</span><span class="sxs-lookup"><span data-stu-id="8efaf-178">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="8efaf-179">由于云锚点是永久性的，随着时间的推移，多台设备可以看到相对于同一物理位置中的定位点呈现的内容。</span><span class="sxs-lookup"><span data-stu-id="8efaf-179">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="8efaf-180">若要开始在 Unity 中构建共享体验，请尝试执行5分钟的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间锚点 Unity 快速入门</a>。</span><span class="sxs-lookup"><span data-stu-id="8efaf-180">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="8efaf-181">启动并运行 Azure 空间锚点后，便可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中创建和定位锚</a>。</span><span class="sxs-lookup"><span data-stu-id="8efaf-181">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
