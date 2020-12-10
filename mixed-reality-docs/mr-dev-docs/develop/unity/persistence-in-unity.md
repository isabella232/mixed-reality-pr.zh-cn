---
title: Unity 中的持久性
description: 通过使用持久性，你的用户可以根据需要将各个全息影像固定在何处，然后在应用的许多用途中查找它。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens，持久性，Unity，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: d74f9c0a118c1886037c564073742ebedc7d0146
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010438"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="dbc6c-104">Unity 中的持久性</span><span class="sxs-lookup"><span data-stu-id="dbc6c-104">Persistence in Unity</span></span>

<span data-ttu-id="dbc6c-105">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="dbc6c-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="dbc6c-106">**类：** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="dbc6c-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="dbc6c-107">WorldAnchorStore 是创建全息体验的关键，其中全息在应用程序的实例上保持特定的实际位置。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="dbc6c-108">然后，用户可以在所需位置固定各个全息影像，稍后在对应用程序的许多应用程序的同一位置进行查找。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-108">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="dbc6c-109">如何跨会话保留全息影像</span><span class="sxs-lookup"><span data-stu-id="dbc6c-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="dbc6c-110">WorldAnchorStore 可让你在不同的会话中持久保存 WorldAnchor 的位置。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="dbc6c-111">若要在会话中实际保留全息影像，需要单独跟踪使用特定世界锚点的 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-111">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="dbc6c-112">通常，使用世界定位点创建 GameObject 根是有意义的，并使子影像由其定位到本地位置偏移量。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="dbc6c-113">从以前的会话加载全息影像：</span><span class="sxs-lookup"><span data-stu-id="dbc6c-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="dbc6c-114">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="dbc6c-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="dbc6c-115">加载与世界定位点相关的应用数据，它提供世界锚的 ID</span><span class="sxs-lookup"><span data-stu-id="dbc6c-115">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="dbc6c-116">从其 ID 加载世界定位点</span><span class="sxs-lookup"><span data-stu-id="dbc6c-116">Load a world anchor from its ID</span></span>

<span data-ttu-id="dbc6c-117">为将来的会话保存全息影像：</span><span class="sxs-lookup"><span data-stu-id="dbc6c-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="dbc6c-118">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="dbc6c-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="dbc6c-119">保存指定 ID 的世界定位点</span><span class="sxs-lookup"><span data-stu-id="dbc6c-119">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="dbc6c-120">保存与世界锚点相关的应用数据以及 ID</span><span class="sxs-lookup"><span data-stu-id="dbc6c-120">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="dbc6c-121">获取 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="dbc6c-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="dbc6c-122">您需要保留对 WorldAnchorStore 的引用，以便您知道何时可以执行某个操作。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-122">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="dbc6c-123">由于这是一个异步调用，可能很快就会启动，因此需要调用：</span><span class="sxs-lookup"><span data-stu-id="dbc6c-123">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="dbc6c-124">在此示例中，StoreLoaded 是 WorldAnchorStore 完成加载时的处理程序：</span><span class="sxs-lookup"><span data-stu-id="dbc6c-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="dbc6c-125">现在，我们有了一个对 WorldAnchorStore 的引用，我们将使用它来保存和加载特定世界锚。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-125">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="dbc6c-126">保存 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="dbc6c-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="dbc6c-127">若要保存，只需命名要保存的内容，并将其传递到 WorldAnchor 我们要保存的时间。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="dbc6c-128">注意：尝试将两个定位点保存到相同的字符串将 (存储中失败。Save 将返回 false) 。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="dbc6c-129">保存新的 save 之前，请先将其删除：</span><span class="sxs-lookup"><span data-stu-id="dbc6c-129">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="dbc6c-130">加载 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="dbc6c-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="dbc6c-131">并加载：</span><span class="sxs-lookup"><span data-stu-id="dbc6c-131">And to load:</span></span>

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

<span data-ttu-id="dbc6c-132">我们还可以使用 store。删除 ( # A1 删除之前保存并存储的定位点。清除 ( # A3 以删除以前保存的所有数据。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="dbc6c-133">枚举现有锚</span><span class="sxs-lookup"><span data-stu-id="dbc6c-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="dbc6c-134">若要发现以前存储的定位点，请调用 GetAllIds。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="dbc6c-135">为多台设备保留全息影像</span><span class="sxs-lookup"><span data-stu-id="dbc6c-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="dbc6c-136">你可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a> 从本地 WorldAnchor 创建持久的云锚点，你的应用可以在多个 HoloLens、IOS 和 Android 设备上查找，即使这些设备同时不存在。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="dbc6c-137">由于云锚点是永久性的，随着时间的推移，多台设备可以看到相对于同一物理位置中的定位点呈现的内容。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="dbc6c-138">若要开始在 Unity 中构建共享体验，请尝试执行5分钟的 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间锚点 Unity 快速入门</a>。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="dbc6c-139">启动并运行 Azure 空间锚点后，便可以 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中创建和定位锚</a>。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="dbc6c-140">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="dbc6c-140">Next Development Checkpoint</span></span>

<span data-ttu-id="dbc6c-141">如果遵循我们所说的 Unity 开发检查点旅程，就是探索混合现实核心构建基块的过程。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-141">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="dbc6c-142">从这里，你可以继续执行下一个构建基块：</span><span class="sxs-lookup"><span data-stu-id="dbc6c-142">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dbc6c-143">空间映射</span><span class="sxs-lookup"><span data-stu-id="dbc6c-143">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="dbc6c-144">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="dbc6c-144">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dbc6c-145">共享体验</span><span class="sxs-lookup"><span data-stu-id="dbc6c-145">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="dbc6c-146">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="dbc6c-146">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="dbc6c-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dbc6c-147">See Also</span></span>
* [<span data-ttu-id="dbc6c-148">空间锚点持久性</span><span class="sxs-lookup"><span data-stu-id="dbc6c-148">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="dbc6c-149"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位点</a></span><span class="sxs-lookup"><span data-stu-id="dbc6c-149"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="dbc6c-150"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">用于 Unity 的 Azure 空间定位点 SDK</a></span><span class="sxs-lookup"><span data-stu-id="dbc6c-150"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
