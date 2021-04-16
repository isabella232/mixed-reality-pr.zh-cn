---
ms.openlocfilehash: 25e42ba872764a98d4cb966b5a4922cc1dea0dc9
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528767"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="725cd-101"> (推荐的全球锁定工具) </span><span class="sxs-lookup"><span data-stu-id="725cd-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="725cd-102">默认情况下，全球锁定工具将跨会话恢复 Unity 相对于物理世界的坐标系统。</span><span class="sxs-lookup"><span data-stu-id="725cd-102">By default, World Locking Tools will restore Unity's coordinate system relative to the physical world across sessions.</span></span> <span data-ttu-id="725cd-103">这意味着，在退出并重新运行应用程序后，使全息图在物理环境中出现的位置与此相同，全息图只需再次具有相同的姿势。</span><span class="sxs-lookup"><span data-stu-id="725cd-103">This means that to have a hologram appear the same place in the physical world after quitting and re-running the application, the hologram only needs to have the same Pose again.</span></span>

![Unity 检查器中的世界锁定上下文组件](../../images/world-locking-tools-img-02.png)

<span data-ttu-id="725cd-105">如果应用程序需要更精细的控制，则可以在检查器中禁用 **自动保存** 和 **自动加载** ，并从脚本中进行持久性管理，如 [文档的持久性部分](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html)中所述。</span><span class="sxs-lookup"><span data-stu-id="725cd-105">If the application needs finer control, **Auto-Save** and **Auto-Load** may be disabled in the inspector, and persistence managed from a script as described in the [persistence section of the documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="725cd-106">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="725cd-106">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="725cd-107">另外一个名为 **XRAnchorStore** 的 API 允许在会话之间保留定位点。</span><span class="sxs-lookup"><span data-stu-id="725cd-107">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="725cd-108">XRAnchorStore 是设备上保存的定位点的表示形式。</span><span class="sxs-lookup"><span data-stu-id="725cd-108">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="725cd-109">定位点可以从 Unity 场景中的 **ARAnchors** 保存、从存储加载到新 **ARAnchors** 或从存储中删除。</span><span class="sxs-lookup"><span data-stu-id="725cd-109">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="725cd-110">这些定位点将保存并加载到同一设备上。</span><span class="sxs-lookup"><span data-stu-id="725cd-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="725cd-111">未来版本中将通过 Azure 空间锚点支持跨设备锚定存储。</span><span class="sxs-lookup"><span data-stu-id="725cd-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

### <a name="namespaces"></a><span data-ttu-id="725cd-112">命名空间</span><span class="sxs-lookup"><span data-stu-id="725cd-112">Namespaces</span></span>

<span data-ttu-id="725cd-113">对于 **Unity 2020 和 OpenXR**：</span><span class="sxs-lookup"><span data-stu-id="725cd-113">For **Unity 2020 and OpenXR**:</span></span> 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

<span data-ttu-id="725cd-114">或 **Unity 2019/2020 + WINDOWS XR 插件**：</span><span class="sxs-lookup"><span data-stu-id="725cd-114">or **Unity 2019/2020 + Windows XR Plugin**:</span></span> 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a><span data-ttu-id="725cd-115">公共方法</span><span class="sxs-lookup"><span data-stu-id="725cd-115">Public methods</span></span>

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

### <a name="getting-an-anchor-store-reference"></a><span data-ttu-id="725cd-116">获取定位点存储区引用</span><span class="sxs-lookup"><span data-stu-id="725cd-116">Getting an anchor store reference</span></span> 

<span data-ttu-id="725cd-117">若要加载包含 **Unity 2020 和 OpenXR** 的 XRAnchorStore，请在 XRAnchorSubsystem 上使用 extension 方法，ARAnchorManager 的子系统：</span><span class="sxs-lookup"><span data-stu-id="725cd-117">To load the XRAnchorStore with **Unity 2020 and OpenXR**, use extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="725cd-118">若要将 XRAnchorStore 与 **unity 2019/2020 和 WINDOWS XR 插件** 一起使用，请使用 XRReferencePointSubsystem (unity 2019) 或 XRAnchorSubsystem (unity 2020) ，ARReferencePointManager/ARAnchorManager 的子系统：</span><span class="sxs-lookup"><span data-stu-id="725cd-118">To load the XRAnchorStore with **Unity 2019/2020 and the Windows XR Plugin**, use the extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a><span data-ttu-id="725cd-119">加载定位点存储</span><span class="sxs-lookup"><span data-stu-id="725cd-119">Loading an anchor store</span></span>

<span data-ttu-id="725cd-120">若要将定位存储加载到 **Unity 2020 和 OpenXR** 中，请按如下所示从 ARAnchorManager 的子系统访问它：</span><span class="sxs-lookup"><span data-stu-id="725cd-120">To load an anchor store in **Unity 2020 and OpenXR**, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="725cd-121">或包含 **Unity 2019/2020 和 WINDOWS XR 插件** 的：</span><span class="sxs-lookup"><span data-stu-id="725cd-121">or with **Unity 2019/2020 and the Windows XR Plugin**:</span></span>

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="725cd-122">若要查看保留/unpersisting 定位点的完整示例，请查看 [Mixed Reality OpenXR 插件示例场景](../../openxr-getting-started.md#hololens-2-samples)中的定位点 > 定位点示例 GameObject 和 AnchorsSample 脚本：</span><span class="sxs-lookup"><span data-stu-id="725cd-122">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../../openxr-getting-started.md#hololens-2-samples):</span></span>

![在 Unity 编辑器中打开的 "层次结构" 面板的屏幕截图，其中突出显示了定位点示例](../../images/openxr-features-img-04.png)

![在 Unity 编辑器中打开的检查器面板屏幕截图，其中突出显示了定位点示例脚本](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[<span data-ttu-id="725cd-125">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="725cd-125">WorldAnchor</span></span>](#tab/worldanchor)

<span data-ttu-id="725cd-126">**WorldAnchorStore** 是创建全息体验的关键，其中全息在应用程序的实例上保持特定的实际位置。</span><span class="sxs-lookup"><span data-stu-id="725cd-126">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="725cd-127">然后，用户可以在所需位置固定各个全息影像，稍后在对应用程序的许多应用程序的同一位置进行查找。</span><span class="sxs-lookup"><span data-stu-id="725cd-127">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="725cd-128">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="725cd-128">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="725cd-129">**类：** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="725cd-129">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="725cd-130">WorldAnchorStore 可让你在不同的会话中持久保存 WorldAnchor 的位置。</span><span class="sxs-lookup"><span data-stu-id="725cd-130">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="725cd-131">若要在会话中实际保留全息影像，需要单独跟踪使用特定世界锚点的 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="725cd-131">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="725cd-132">通常，使用世界定位点创建 GameObject 根是有意义的，并使子影像由其定位到本地位置偏移量。</span><span class="sxs-lookup"><span data-stu-id="725cd-132">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="725cd-133">从以前的会话加载全息影像：</span><span class="sxs-lookup"><span data-stu-id="725cd-133">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="725cd-134">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="725cd-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="725cd-135">加载与世界定位点相关的应用数据，它提供世界锚的 ID</span><span class="sxs-lookup"><span data-stu-id="725cd-135">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="725cd-136">从其 ID 加载世界定位点</span><span class="sxs-lookup"><span data-stu-id="725cd-136">Load a world anchor from its ID</span></span>

<span data-ttu-id="725cd-137">为将来的会话保存全息影像：</span><span class="sxs-lookup"><span data-stu-id="725cd-137">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="725cd-138">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="725cd-138">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="725cd-139">保存指定 ID 的世界定位点</span><span class="sxs-lookup"><span data-stu-id="725cd-139">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="725cd-140">保存与世界锚点相关的应用数据以及 ID</span><span class="sxs-lookup"><span data-stu-id="725cd-140">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="725cd-141">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="725cd-141">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="725cd-142">您需要保留对 WorldAnchorStore 的引用，以便您知道何时可以执行某个操作。</span><span class="sxs-lookup"><span data-stu-id="725cd-142">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="725cd-143">由于这是一个异步调用，可能很快就会启动，因此需要调用：</span><span class="sxs-lookup"><span data-stu-id="725cd-143">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="725cd-144">在此示例中，StoreLoaded 是 WorldAnchorStore 完成加载时的处理程序：</span><span class="sxs-lookup"><span data-stu-id="725cd-144">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="725cd-145">现在，我们有了一个对 WorldAnchorStore 的引用，我们将使用它来保存和加载特定世界锚。</span><span class="sxs-lookup"><span data-stu-id="725cd-145">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="725cd-146">保存 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="725cd-146">Saving a WorldAnchor</span></span>

<span data-ttu-id="725cd-147">若要保存，只需命名要保存的内容，并将其传递到 WorldAnchor 我们要保存的时间。</span><span class="sxs-lookup"><span data-stu-id="725cd-147">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="725cd-148">注意：尝试将两个定位点保存到相同的字符串将 (存储中失败。Save 将返回 false) 。</span><span class="sxs-lookup"><span data-stu-id="725cd-148">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="725cd-149">保存新的 save 之前，请先将其删除：</span><span class="sxs-lookup"><span data-stu-id="725cd-149">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="725cd-150">加载 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="725cd-150">Loading a WorldAnchor</span></span>

<span data-ttu-id="725cd-151">并加载：</span><span class="sxs-lookup"><span data-stu-id="725cd-151">And to load:</span></span>

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

<span data-ttu-id="725cd-152">我们还可以使用 store。删除 () 删除之前保存并存储的定位点。清除 () 删除以前保存的所有数据。</span><span class="sxs-lookup"><span data-stu-id="725cd-152">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="725cd-153">枚举现有锚</span><span class="sxs-lookup"><span data-stu-id="725cd-153">Enumerating Existing Anchors</span></span>

<span data-ttu-id="725cd-154">若要发现以前存储的定位点，请调用 GetAllIds。</span><span class="sxs-lookup"><span data-stu-id="725cd-154">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="725cd-155">为多台设备保留全息影像</span><span class="sxs-lookup"><span data-stu-id="725cd-155">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="725cd-156">你可以使用 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a> 从本地 WorldAnchor 创建持久的云锚点，你的应用可以在多个 HoloLens、IOS 和 Android 设备上查找，即使这些设备同时不存在。</span><span class="sxs-lookup"><span data-stu-id="725cd-156">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="725cd-157">由于云锚点是永久性的，随着时间的推移，多台设备可以看到相对于同一物理位置中的定位点呈现的内容。</span><span class="sxs-lookup"><span data-stu-id="725cd-157">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="725cd-158">若要开始在 Unity 中构建共享体验，请尝试执行5分钟的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间锚点 Unity 快速入门</a>。</span><span class="sxs-lookup"><span data-stu-id="725cd-158">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="725cd-159">启动并运行 Azure 空间锚点后，便可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中创建和定位锚</a>。</span><span class="sxs-lookup"><span data-stu-id="725cd-159">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
