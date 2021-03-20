---
ms.openlocfilehash: 05e2b87383bbc91b7fd8785230152e3549f4b22d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719752"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="6da07-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="6da07-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="6da07-102">Mixed Reality OpenXR 插件通过实现 Unity 的 ARFoundation **ARAnchorManager** 提供基本的定位点功能。</span><span class="sxs-lookup"><span data-stu-id="6da07-102">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="6da07-103">若要了解有关 ARFoundation 中 ARAnchors 的基础知识，请访问 [AR 定位管理器的 ARFoundation 手册](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)。</span><span class="sxs-lookup"><span data-stu-id="6da07-103">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="6da07-104">Unity 2019/2020 + Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="6da07-104">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="6da07-105">Mixed Reality OpenXR 插件通过实现 Unity 的 ARFoundation **ARAnchorManager** 提供基本的定位点功能。</span><span class="sxs-lookup"><span data-stu-id="6da07-105">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="6da07-106">若要了解有关 ARFoundation 中 ARAnchors 的基础知识，请访问 [AR 定位管理器的 ARFoundation 手册](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)。</span><span class="sxs-lookup"><span data-stu-id="6da07-106">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="6da07-107">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="6da07-107">Legacy WSA</span></span>](#tab/wsa)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="6da07-108">构建全球范围的体验</span><span class="sxs-lookup"><span data-stu-id="6da07-108">Building a world-scale experience</span></span>

<span data-ttu-id="6da07-109">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="6da07-109">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="6da07-110">**类型：** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="6da07-110">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="6da07-111">对于 HoloLens 上真正的 **全球规模体验** ，让用户游离5米以上，你将需要超出用于房间规模体验的新技术。</span><span class="sxs-lookup"><span data-stu-id="6da07-111">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="6da07-112">你将使用的一项关键方法是创建一个 [空间定位点](../../../design/coordinate-systems.md#spatial-anchors) ，以便在物理世界中精确地锁定影像的分类，无论用户漫游到多远，然后 [在以后的会话中再次查找这些全息影像](../../../design/coordinate-systems.md#spatial-anchor-persistence)。</span><span class="sxs-lookup"><span data-stu-id="6da07-112">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="6da07-113">在 Unity 中，可以通过将 **WorldAnchor** Unity 组件添加到 GameObject 来创建空间锚。</span><span class="sxs-lookup"><span data-stu-id="6da07-113">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="6da07-114">添加世界锚</span><span class="sxs-lookup"><span data-stu-id="6da07-114">Adding a World Anchor</span></span>

<span data-ttu-id="6da07-115">若要添加世界定位点，请 `AddComponent<WorldAnchor>()` 使用要锚定的转换，对游戏对象调用。</span><span class="sxs-lookup"><span data-stu-id="6da07-115">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="6da07-116">就这么简单！</span><span class="sxs-lookup"><span data-stu-id="6da07-116">That's it!</span></span> <span data-ttu-id="6da07-117">现在，此游戏对象将锚定到其在物理世界中的当前位置-你可能会看到其 Unity 世界坐标在一段时间后会略微调整，以确保物理对齐。</span><span class="sxs-lookup"><span data-stu-id="6da07-117">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="6da07-118">请参阅 [加载世界定位点](#loading-a-worldanchor) ，在未来的应用程序会话中再次查找此定位位置。</span><span class="sxs-lookup"><span data-stu-id="6da07-118">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="6da07-119">删除世界锚</span><span class="sxs-lookup"><span data-stu-id="6da07-119">Removing a World Anchor</span></span>

<span data-ttu-id="6da07-120">如果不再希望 GameObject 锁定到物理世界位置，并且不打算将其移动到此帧，则可以只在世界锚点组件上调用销毁。</span><span class="sxs-lookup"><span data-stu-id="6da07-120">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="6da07-121">如果要将 GameObject 移动到此帧，则需改为调用 DestroyImmediate。</span><span class="sxs-lookup"><span data-stu-id="6da07-121">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="6da07-122">移动世界定位的 GameObject</span><span class="sxs-lookup"><span data-stu-id="6da07-122">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="6da07-123">GameObject 在世界锚点上时无法移动。</span><span class="sxs-lookup"><span data-stu-id="6da07-123">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="6da07-124">如果需要将 GameObject 移动到此框架，需要执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="6da07-124">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="6da07-125">DestroyImmediate 世界锚组件</span><span class="sxs-lookup"><span data-stu-id="6da07-125">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="6da07-126">移动 GameObject</span><span class="sxs-lookup"><span data-stu-id="6da07-126">Move the GameObject</span></span>
3. <span data-ttu-id="6da07-127">向 GameObject 添加新的世界锚点组件。</span><span class="sxs-lookup"><span data-stu-id="6da07-127">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="6da07-128">处理 Locatability 更改</span><span class="sxs-lookup"><span data-stu-id="6da07-128">Handling Locatability Changes</span></span>

<span data-ttu-id="6da07-129">在物理环境中，可能无法在某个时间点定位 WorldAnchor。</span><span class="sxs-lookup"><span data-stu-id="6da07-129">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="6da07-130">如果出现这种情况，则 Unity 不会更新定位对象的转换。</span><span class="sxs-lookup"><span data-stu-id="6da07-130">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="6da07-131">在应用程序运行时，这也可能会更改。</span><span class="sxs-lookup"><span data-stu-id="6da07-131">This also can change while an app is running.</span></span> <span data-ttu-id="6da07-132">如果无法处理 locatability 中的更改，则会导致对象不显示在世界上正确的物理位置。</span><span class="sxs-lookup"><span data-stu-id="6da07-132">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="6da07-133">若要获得有关 locatability 更改的通知：</span><span class="sxs-lookup"><span data-stu-id="6da07-133">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="6da07-134">订阅 OnTrackingChanged 事件</span><span class="sxs-lookup"><span data-stu-id="6da07-134">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="6da07-135">处理事件</span><span class="sxs-lookup"><span data-stu-id="6da07-135">Handle the event</span></span>

<span data-ttu-id="6da07-136">每当基础空间锚点在正在定位的状态与不能定位的状态之间发生变化时，将调用 **OnTrackingChanged** 事件。</span><span class="sxs-lookup"><span data-stu-id="6da07-136">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="6da07-137">然后处理事件：</span><span class="sxs-lookup"><span data-stu-id="6da07-137">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="6da07-138">有时会立即定位锚点。</span><span class="sxs-lookup"><span data-stu-id="6da07-138">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="6da07-139">在这种情况下，当 AddComponent () 返回时，定位点的 isLocated 属性将设置为 true <WorldAnchor> 。</span><span class="sxs-lookup"><span data-stu-id="6da07-139">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="6da07-140">因此，不会触发 OnTrackingChanged 事件。</span><span class="sxs-lookup"><span data-stu-id="6da07-140">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="6da07-141">清理模式是在附加定位点后使用初始 IsLocated 状态调用 OnTrackingChanged 处理程序。</span><span class="sxs-lookup"><span data-stu-id="6da07-141">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```