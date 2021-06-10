---
ms.openlocfilehash: 96da41f28533c227fb106d8842907747f34098ec
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2021
ms.locfileid: "110349922"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="98063-101">世界锁定工具 (推荐) </span><span class="sxs-lookup"><span data-stu-id="98063-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="98063-102">默认情况下，世界锁定工具将跨会话还原 Unity 相对于物理世界坐标系。</span><span class="sxs-lookup"><span data-stu-id="98063-102">By default, World Locking Tools will restore Unity's coordinate system relative to the physical world across sessions.</span></span> <span data-ttu-id="98063-103">这意味着，在进入和重新运行应用程序后，若要让全息影像在物理世界中显示相同的位置，则全息影像只需再次具有相同的"姿势"。</span><span class="sxs-lookup"><span data-stu-id="98063-103">This means that to have a hologram appear the same place in the physical world after quitting and re-running the application, the hologram only needs to have the same Pose again.</span></span>

![Unity 检查器中的世界锁定上下文组件](../../images/world-locking-tools-img-02.png)

<span data-ttu-id="98063-105">如果应用程序需要更精细的控制，可以在检查器中禁用自动保存和自动加载，并按文档 的持久性部分中所述从脚本管理[持久性。](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html)</span><span class="sxs-lookup"><span data-stu-id="98063-105">If the application needs finer control, **Auto-Save** and **Auto-Load** may be disabled in the inspector, and persistence managed from a script as described in the [persistence section of the documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="98063-106">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="98063-106">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="98063-107">使用名为 **XRAnchorStore** 的其他 API，可以在会话之间持久保存定位点。</span><span class="sxs-lookup"><span data-stu-id="98063-107">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="98063-108">XRAnchorStore 是设备上保存的定位点的表示形式。</span><span class="sxs-lookup"><span data-stu-id="98063-108">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="98063-109">可以从 Unity 场景中的 **ARAnchors** 持久保存定位点，从存储加载到新的 **ARAnchors** 中，或者从存储中删除定位点。</span><span class="sxs-lookup"><span data-stu-id="98063-109">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="98063-110">这些定位点将保存并加载到同一设备上。</span><span class="sxs-lookup"><span data-stu-id="98063-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="98063-111">在将来的版本中，通过 Azure 空间定位点支持跨设备定位点存储。</span><span class="sxs-lookup"><span data-stu-id="98063-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

### <a name="namespaces"></a><span data-ttu-id="98063-112">命名空间</span><span class="sxs-lookup"><span data-stu-id="98063-112">Namespaces</span></span>

<span data-ttu-id="98063-113">对于 **Unity 2020 和 OpenXR：**</span><span class="sxs-lookup"><span data-stu-id="98063-113">For **Unity 2020 and OpenXR**:</span></span> 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

<span data-ttu-id="98063-114">或 **Unity 2019/2020 + Windows XR 插件**：</span><span class="sxs-lookup"><span data-stu-id="98063-114">or **Unity 2019/2020 + Windows XR Plugin**:</span></span> 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a><span data-ttu-id="98063-115">公共方法</span><span class="sxs-lookup"><span data-stu-id="98063-115">Public methods</span></span>

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

### <a name="getting-an-anchor-store-reference"></a><span data-ttu-id="98063-116">获取定位点存储引用</span><span class="sxs-lookup"><span data-stu-id="98063-116">Getting an anchor store reference</span></span> 

<span data-ttu-id="98063-117">若要使用 **Unity 2020 和 OpenXR** 加载 XRAnchorStore，请使用 XRAnchorSubsystem（ARAnchorManager 的子系统）上的扩展方法：</span><span class="sxs-lookup"><span data-stu-id="98063-117">To load the XRAnchorStore with **Unity 2020 and OpenXR**, use extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="98063-118">若要使用 **Unity 2019/2020** 和 Windows XR 插件加载 XRAnchorStore，请使用 XRReferencePointSubsystem (Unity 2019) 或 XRAnchorSubsystem (Unity 2020) （ARReferencePointManager/ARAnchorManager 的子系统）上的扩展方法：</span><span class="sxs-lookup"><span data-stu-id="98063-118">To load the XRAnchorStore with **Unity 2019/2020 and the Windows XR Plugin**, use the extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a><span data-ttu-id="98063-119">加载定位点存储</span><span class="sxs-lookup"><span data-stu-id="98063-119">Loading an anchor store</span></span>

<span data-ttu-id="98063-120">若要在 **Unity 2020 和 OpenXR** 中加载定位点存储，请从 ARAnchorManager 的子系统访问它，如下所示：</span><span class="sxs-lookup"><span data-stu-id="98063-120">To load an anchor store in **Unity 2020 and OpenXR**, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="98063-121">或者使用 **Unity 2019/2020 和 Windows XR 插件**：</span><span class="sxs-lookup"><span data-stu-id="98063-121">or with **Unity 2019/2020 and the Windows XR Plugin**:</span></span>

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="98063-122">若要查看保留/取消持久化定位点的完整示例，请查看混合现实 [OpenXR](../../openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2)插件示例场景中的定位点 -> 定位点示例 GameObject 和 AnchorsSample.cs 脚本：</span><span class="sxs-lookup"><span data-stu-id="98063-122">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../../openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2):</span></span>

![在 Unity 编辑器中打开的层次结构面板的屏幕截图，其中突出显示了定位点示例](../../images/openxr-features-img-04.png)

![Unity 编辑器中打开的检查器面板的屏幕截图，其中突出显示了定位点示例脚本](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[<span data-ttu-id="98063-125">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="98063-125">WorldAnchor</span></span>](#tab/worldanchor)

<span data-ttu-id="98063-126">**WorldAnchorStore** 是创建全息体验的关键，全息影像位于应用程序实例的特定真实位置。</span><span class="sxs-lookup"><span data-stu-id="98063-126">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="98063-127">然后，用户可以将单个全息影像固定到任何想要的位置，并稍后在同一位置找到它们，而多次使用你的应用。</span><span class="sxs-lookup"><span data-stu-id="98063-127">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="98063-128">\**命名空间\*\*\*：UnityEngine.XR.WSA.Persistence*</span><span class="sxs-lookup"><span data-stu-id="98063-128">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="98063-129">\**类\*\*\*：WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="98063-129">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="98063-130">使用 WorldAnchorStore，可以跨会话保留 WorldAnchor 的位置。</span><span class="sxs-lookup"><span data-stu-id="98063-130">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="98063-131">若要实际跨会话保留全息影像，需要单独跟踪使用特定世界定位点的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="98063-131">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="98063-132">通常，使用世界定位点创建 GameObject 根目录，并且使用本地位置偏移量锚定子全息影像。</span><span class="sxs-lookup"><span data-stu-id="98063-132">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="98063-133">从以前的会话中加载全息影像：</span><span class="sxs-lookup"><span data-stu-id="98063-133">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="98063-134">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="98063-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="98063-135">加载与世界定位点相关的应用数据，这些数据提供世界定位点的 ID</span><span class="sxs-lookup"><span data-stu-id="98063-135">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="98063-136">从世界定位点 ID 加载世界定位点</span><span class="sxs-lookup"><span data-stu-id="98063-136">Load a world anchor from its ID</span></span>

<span data-ttu-id="98063-137">保存全息影像供将来会话使用：</span><span class="sxs-lookup"><span data-stu-id="98063-137">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="98063-138">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="98063-138">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="98063-139">保存指定 ID 世界定位点</span><span class="sxs-lookup"><span data-stu-id="98063-139">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="98063-140">保存与世界定位点相关的应用数据以及 ID</span><span class="sxs-lookup"><span data-stu-id="98063-140">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="98063-141">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="98063-141">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="98063-142">你需要保留对 WorldAnchorStore 的引用，以便知道何时可以执行操作。</span><span class="sxs-lookup"><span data-stu-id="98063-142">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="98063-143">由于这是一个异步调用，因此可能需要在启动后立即调用：</span><span class="sxs-lookup"><span data-stu-id="98063-143">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="98063-144">在这种情况下，StoreLoaded 是 WorldAnchorStore 完成加载时处理程序：</span><span class="sxs-lookup"><span data-stu-id="98063-144">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="98063-145">现在，我们引用了 WorldAnchorStore，我们将使用它来保存和加载特定的世界定位点。</span><span class="sxs-lookup"><span data-stu-id="98063-145">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="98063-146">保存 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="98063-146">Saving a WorldAnchor</span></span>

<span data-ttu-id="98063-147">若要保存，只需命名要保存的名称，并将其传递到之前要保存的 WorldAnchor 中。</span><span class="sxs-lookup"><span data-stu-id="98063-147">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="98063-148">注意：尝试将两个定位点保存到同一字符串将失败 (存储。Save 将返回 false) 。</span><span class="sxs-lookup"><span data-stu-id="98063-148">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="98063-149">在保存新保存之前删除以前的保存：</span><span class="sxs-lookup"><span data-stu-id="98063-149">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="98063-150">加载 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="98063-150">Loading a WorldAnchor</span></span>

<span data-ttu-id="98063-151">要加载的 和 ：</span><span class="sxs-lookup"><span data-stu-id="98063-151">And to load:</span></span>

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

<span data-ttu-id="98063-152">此外，我们可以使用 store。删除 () 删除之前保存和存储的定位点。清除 () 删除以前保存的所有数据。</span><span class="sxs-lookup"><span data-stu-id="98063-152">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="98063-153">枚举现有定位点</span><span class="sxs-lookup"><span data-stu-id="98063-153">Enumerating Existing Anchors</span></span>

<span data-ttu-id="98063-154">若要发现以前存储的定位点，请调用 GetAllIds。</span><span class="sxs-lookup"><span data-stu-id="98063-154">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="98063-155">保留多个设备的全息影像</span><span class="sxs-lookup"><span data-stu-id="98063-155">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="98063-156">可以使用 <a href="/azure/spatial-anchors/overview" target="_blank">Azure</a> 空间定位点从本地 WorldAnchor 创建持久云定位点，然后应用可跨多个 HoloLens、iOS 和 Android 设备找到该定位点，即使这些设备同时不在一起。</span><span class="sxs-lookup"><span data-stu-id="98063-156">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="98063-157">由于云定位点是持久性的，因此随着时间的推移，多个设备都可以在同一物理位置查看相对于该定位点呈现的内容。</span><span class="sxs-lookup"><span data-stu-id="98063-157">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="98063-158">若要开始在 Unity 中构建共享体验，请尝试 5 分钟的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间定位点 Unity 快速入门</a>。</span><span class="sxs-lookup"><span data-stu-id="98063-158">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="98063-159">使用 Azure 空间定位点启动并运行后，可以在 Unity 中创建 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">和查找定位点</a>。</span><span class="sxs-lookup"><span data-stu-id="98063-159">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
