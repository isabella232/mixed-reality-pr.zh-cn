---
ms.openlocfilehash: bb2df8c85dd05981c1438bdb076b0aad16c7efd7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719917"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="6d8f8-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="6d8f8-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="6d8f8-102">另外一个名为 **XRAnchorStore** 的 API 允许在会话之间保留定位点。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-102">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="6d8f8-103">XRAnchorStore 是设备上保存的定位点的表示形式。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-103">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="6d8f8-104">定位点可以从 Unity 场景中的 **ARAnchors** 保存、从存储加载到新 **ARAnchors** 或从存储中删除。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-104">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="6d8f8-105">这些定位点将保存并加载到同一设备上。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-105">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="6d8f8-106">未来版本中将通过 Azure 空间锚点支持跨设备锚定存储。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-106">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="6d8f8-107">若要加载 XRAnchorStore，该插件会在 XRAnchorSubsystem （ARAnchorManager 的子系统）上提供扩展方法：</span><span class="sxs-lookup"><span data-stu-id="6d8f8-107">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="6d8f8-108">若要使用此扩展方法，请按如下所示从 ARAnchorManager 的子系统访问它：</span><span class="sxs-lookup"><span data-stu-id="6d8f8-108">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="6d8f8-109">若要查看保留/unpersisting 定位点的完整示例，请查看 [Mixed Reality OpenXR 插件示例场景](../openxr-getting-started.md#hololens-2-samples)中的定位点 > 定位点示例 GameObject 和 AnchorsSample 脚本：</span><span class="sxs-lookup"><span data-stu-id="6d8f8-109">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![在 Unity 编辑器中打开的 "层次结构" 面板的屏幕截图，其中突出显示了定位点示例](../images/openxr-features-img-04.png)

![在 Unity 编辑器中打开的检查器面板屏幕截图，其中突出显示了定位点示例脚本](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="6d8f8-112">Unity 2019/2020 + Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="6d8f8-112">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="6d8f8-113">名为 **XRAnchorStore** 的 API 允许在会话之间保留定位点。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-113">An API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="6d8f8-114">XRAnchorStore 是设备上保存的定位点的表示形式。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-114">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="6d8f8-115">定位点可以从 Unity 场景中的 **ARAnchors** 保存、从存储加载到新 **ARAnchors** 或从存储中删除。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-115">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="6d8f8-116">这些定位点将保存并加载到同一设备上。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-116">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="6d8f8-117">未来版本中将通过 Azure 空间锚点支持跨设备锚定存储。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-117">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="6d8f8-118">若要加载 XRAnchorStore，该插件在 XRReferencePointSubsystem (Unity 2019) 或 XRAnchorSubsystem (Unity 2020) （ARReferencePointManager/ARAnchorManager 的子系统）上提供扩展方法：</span><span class="sxs-lookup"><span data-stu-id="6d8f8-118">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="6d8f8-119">若要使用此扩展方法，请按以下方式从 ARAnchorManager 的子系统访问它： Unity 2019：</span><span class="sxs-lookup"><span data-stu-id="6d8f8-119">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="6d8f8-120">对于 Unity 2020：</span><span class="sxs-lookup"><span data-stu-id="6d8f8-120">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="6d8f8-121">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="6d8f8-121">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="6d8f8-122">**WorldAnchorStore** 是创建全息体验的关键，其中全息在应用程序的实例上保持特定的实际位置。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-122">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="6d8f8-123">然后，用户可以在所需位置固定各个全息影像，稍后在对应用程序的许多应用程序的同一位置进行查找。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-123">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="6d8f8-124">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="6d8f8-124">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="6d8f8-125">**类：** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="6d8f8-125">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="6d8f8-126">WorldAnchorStore 可让你在不同的会话中持久保存 WorldAnchor 的位置。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-126">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="6d8f8-127">若要在会话中实际保留全息影像，需要单独跟踪使用特定世界锚点的 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-127">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="6d8f8-128">通常，使用世界定位点创建 GameObject 根是有意义的，并使子影像由其定位到本地位置偏移量。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-128">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="6d8f8-129">从以前的会话加载全息影像：</span><span class="sxs-lookup"><span data-stu-id="6d8f8-129">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="6d8f8-130">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="6d8f8-130">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="6d8f8-131">加载与世界定位点相关的应用数据，它提供世界锚的 ID</span><span class="sxs-lookup"><span data-stu-id="6d8f8-131">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="6d8f8-132">从其 ID 加载世界定位点</span><span class="sxs-lookup"><span data-stu-id="6d8f8-132">Load a world anchor from its ID</span></span>

<span data-ttu-id="6d8f8-133">为将来的会话保存全息影像：</span><span class="sxs-lookup"><span data-stu-id="6d8f8-133">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="6d8f8-134">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="6d8f8-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="6d8f8-135">保存指定 ID 的世界定位点</span><span class="sxs-lookup"><span data-stu-id="6d8f8-135">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="6d8f8-136">保存与世界锚点相关的应用数据以及 ID</span><span class="sxs-lookup"><span data-stu-id="6d8f8-136">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="6d8f8-137">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="6d8f8-137">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="6d8f8-138">您需要保留对 WorldAnchorStore 的引用，以便您知道何时可以执行某个操作。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-138">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="6d8f8-139">由于这是一个异步调用，可能很快就会启动，因此需要调用：</span><span class="sxs-lookup"><span data-stu-id="6d8f8-139">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="6d8f8-140">在此示例中，StoreLoaded 是 WorldAnchorStore 完成加载时的处理程序：</span><span class="sxs-lookup"><span data-stu-id="6d8f8-140">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="6d8f8-141">现在，我们有了一个对 WorldAnchorStore 的引用，我们将使用它来保存和加载特定世界锚。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-141">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="6d8f8-142">保存 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="6d8f8-142">Saving a WorldAnchor</span></span>

<span data-ttu-id="6d8f8-143">若要保存，只需命名要保存的内容，并将其传递到 WorldAnchor 我们要保存的时间。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-143">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="6d8f8-144">注意：尝试将两个定位点保存到相同的字符串将 (存储中失败。Save 将返回 false) 。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-144">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="6d8f8-145">保存新的 save 之前，请先将其删除：</span><span class="sxs-lookup"><span data-stu-id="6d8f8-145">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="6d8f8-146">加载 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="6d8f8-146">Loading a WorldAnchor</span></span>

<span data-ttu-id="6d8f8-147">并加载：</span><span class="sxs-lookup"><span data-stu-id="6d8f8-147">And to load:</span></span>

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

<span data-ttu-id="6d8f8-148">我们还可以使用 store。删除 () 删除之前保存并存储的定位点。清除 () 删除以前保存的所有数据。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-148">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="6d8f8-149">枚举现有锚</span><span class="sxs-lookup"><span data-stu-id="6d8f8-149">Enumerating Existing Anchors</span></span>

<span data-ttu-id="6d8f8-150">若要发现以前存储的定位点，请调用 GetAllIds。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-150">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="6d8f8-151">为多台设备保留全息影像</span><span class="sxs-lookup"><span data-stu-id="6d8f8-151">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="6d8f8-152">你可以使用 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a> 从本地 WorldAnchor 创建持久的云锚点，你的应用可以在多个 HoloLens、IOS 和 Android 设备上查找，即使这些设备同时不存在。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-152">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="6d8f8-153">由于云锚点是永久性的，随着时间的推移，多台设备可以看到相对于同一物理位置中的定位点呈现的内容。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-153">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="6d8f8-154">若要开始在 Unity 中构建共享体验，请尝试执行5分钟的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间锚点 Unity 快速入门</a>。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-154">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="6d8f8-155">启动并运行 Azure 空间锚点后，便可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中创建和定位锚</a>。</span><span class="sxs-lookup"><span data-stu-id="6d8f8-155">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
