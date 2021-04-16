---
ms.openlocfilehash: 6229b258233f7a80ef6530edd6eb94774a0e54cf
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528765"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="091ef-101"> (推荐的全球锁定工具) </span><span class="sxs-lookup"><span data-stu-id="091ef-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="091ef-102">建议使用新的混合现实功能工具安装全球锁定工具。</span><span class="sxs-lookup"><span data-stu-id="091ef-102">We recommend installing World Locking Tools using the new Mixed Reality Feature Tool.</span></span> <span data-ttu-id="091ef-103">从下面的链接下载了混合现实功能工具之后，从 "**全球锁定工具**" 部分中选择 **WLT Core** 的最新版本：</span><span class="sxs-lookup"><span data-stu-id="091ef-103">Once you've downloaded the Mixed Reality Feature Tool from the link below, select the latest version of **WLT Core** from the **World Locking Tools** section:</span></span>

![选择了世界锁定工具的混合现实功能工具功能选择窗口](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="091ef-105">利用 MR 功能工具安装全球锁定工具</span><span class="sxs-lookup"><span data-stu-id="091ef-105">Install World Locking Tools with the MR Feature Tool</span></span>](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a><span data-ttu-id="091ef-106">自动安装</span><span class="sxs-lookup"><span data-stu-id="091ef-106">Automated setup</span></span>

<span data-ttu-id="091ef-107">当你的项目准备就绪时，请从混合现实工具包中运行 "配置场景" 实用程序 **> 实用程序 > 全球锁定工具**：</span><span class="sxs-lookup"><span data-stu-id="091ef-107">When your project is ready to go, run the configure scene utility from **Mixed Reality Toolkit > Utilities > World Locking Tools**:</span></span>

![选定了混合现实工具包菜单的 Unity 编辑器](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> <span data-ttu-id="091ef-109">可以随时重新运行 "配置场景" 实用工具。</span><span class="sxs-lookup"><span data-stu-id="091ef-109">The Configure scene utility can be rerun at any time.</span></span> <span data-ttu-id="091ef-110">例如，如果 AR 目标已从旧版本更改为 XR SDK，则应重新运行该示例。</span><span class="sxs-lookup"><span data-stu-id="091ef-110">For example, it should be rerun if the AR target has been changed from Legacy to XR SDK.</span></span> <span data-ttu-id="091ef-111">如果场景已正确配置，则运行该实用程序将不起作用。</span><span class="sxs-lookup"><span data-stu-id="091ef-111">If the scene is already properly configured, running the utility has no effect.</span></span>

### <a name="visualizers"></a><span data-ttu-id="091ef-112">可视化工具</span><span class="sxs-lookup"><span data-stu-id="091ef-112">Visualizers</span></span>

<span data-ttu-id="091ef-113">在早期开发过程中，添加可视化工具有助于确保 WLT 设置正确且工作正常。</span><span class="sxs-lookup"><span data-stu-id="091ef-113">During early development, adding visualizers can be helpful to ensure WLT is setup and working properly.</span></span> <span data-ttu-id="091ef-114">可以使用 "删除可视化工具" 实用工具将其从生产性能中删除，或者出于任何原因而不再需要。</span><span class="sxs-lookup"><span data-stu-id="091ef-114">They can be removed for production performance, or if for any reason are no longer needed, using the Remove visualizers utility.</span></span> <span data-ttu-id="091ef-115">有关可视化工具的更多详细信息，请参阅 [工具文档](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers)。</span><span class="sxs-lookup"><span data-stu-id="091ef-115">More details on the visualizers can be found in the [Tools documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="091ef-116">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="091ef-116">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="091ef-117">Mixed Reality OpenXR 插件通过实现 Unity 的 ARFoundation **ARAnchorManager** 提供基本的定位点功能。</span><span class="sxs-lookup"><span data-stu-id="091ef-117">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="091ef-118">若要了解有关 ARFoundation 中 ARAnchors 的基础知识，请访问 [AR 定位管理器的 ARFoundation 手册](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)。</span><span class="sxs-lookup"><span data-stu-id="091ef-118">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="worldanchor"></a>[<span data-ttu-id="091ef-119">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="091ef-119">WorldAnchor</span></span>](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="091ef-120">构建全球范围的体验</span><span class="sxs-lookup"><span data-stu-id="091ef-120">Building a world-scale experience</span></span>

<span data-ttu-id="091ef-121">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="091ef-121">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="091ef-122">**类型：** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="091ef-122">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="091ef-123">对于 HoloLens 上真正的 **全球规模体验** ，让用户游离5米以上，你将需要超出用于房间规模体验的新技术。</span><span class="sxs-lookup"><span data-stu-id="091ef-123">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="091ef-124">你将使用的一项关键方法是创建一个 [空间定位点](../../../../design/coordinate-systems.md#spatial-anchors) ，以便在物理世界中精确地锁定影像的分类，无论用户漫游到多远，然后 [在以后的会话中再次查找这些全息影像](../../../../design/coordinate-systems.md#spatial-anchor-persistence)。</span><span class="sxs-lookup"><span data-stu-id="091ef-124">One key technique you'll use is to create a [spatial anchor](../../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="091ef-125">在 Unity 中，可以通过将 **WorldAnchor** Unity 组件添加到 GameObject 来创建空间锚。</span><span class="sxs-lookup"><span data-stu-id="091ef-125">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="091ef-126">添加世界锚</span><span class="sxs-lookup"><span data-stu-id="091ef-126">Adding a World Anchor</span></span>

<span data-ttu-id="091ef-127">若要添加世界定位点，请 `AddComponent<WorldAnchor>()` 使用要锚定的转换，对游戏对象调用。</span><span class="sxs-lookup"><span data-stu-id="091ef-127">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="091ef-128">就这么简单！</span><span class="sxs-lookup"><span data-stu-id="091ef-128">That's it!</span></span> <span data-ttu-id="091ef-129">现在，此游戏对象将锚定到其在物理世界中的当前位置-你可能会看到其 Unity 世界坐标在一段时间后会略微调整，以确保物理对齐。</span><span class="sxs-lookup"><span data-stu-id="091ef-129">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="091ef-130">请参阅 [加载世界定位点](#loading-a-worldanchor) ，在未来的应用程序会话中再次查找此定位位置。</span><span class="sxs-lookup"><span data-stu-id="091ef-130">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="091ef-131">删除世界锚</span><span class="sxs-lookup"><span data-stu-id="091ef-131">Removing a World Anchor</span></span>

<span data-ttu-id="091ef-132">如果不再希望 GameObject 锁定到物理世界位置，并且不打算将其移动到此帧，则可以只在世界锚点组件上调用销毁。</span><span class="sxs-lookup"><span data-stu-id="091ef-132">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="091ef-133">如果要将 GameObject 移动到此帧，则需改为调用 DestroyImmediate。</span><span class="sxs-lookup"><span data-stu-id="091ef-133">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="091ef-134">移动世界定位的 GameObject</span><span class="sxs-lookup"><span data-stu-id="091ef-134">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="091ef-135">GameObject 在世界锚点上时无法移动。</span><span class="sxs-lookup"><span data-stu-id="091ef-135">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="091ef-136">如果需要将 GameObject 移动到此框架，需要执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="091ef-136">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="091ef-137">DestroyImmediate 世界锚组件</span><span class="sxs-lookup"><span data-stu-id="091ef-137">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="091ef-138">移动 GameObject</span><span class="sxs-lookup"><span data-stu-id="091ef-138">Move the GameObject</span></span>
3. <span data-ttu-id="091ef-139">向 GameObject 添加新的世界锚点组件。</span><span class="sxs-lookup"><span data-stu-id="091ef-139">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="091ef-140">处理 Locatability 更改</span><span class="sxs-lookup"><span data-stu-id="091ef-140">Handling Locatability Changes</span></span>

<span data-ttu-id="091ef-141">在物理环境中，可能无法在某个时间点定位 WorldAnchor。</span><span class="sxs-lookup"><span data-stu-id="091ef-141">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="091ef-142">如果出现这种情况，则 Unity 不会更新定位对象的转换。</span><span class="sxs-lookup"><span data-stu-id="091ef-142">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="091ef-143">在应用程序运行时，这也可能会更改。</span><span class="sxs-lookup"><span data-stu-id="091ef-143">This also can change while an app is running.</span></span> <span data-ttu-id="091ef-144">如果无法处理 locatability 中的更改，则会导致对象不显示在世界上正确的物理位置。</span><span class="sxs-lookup"><span data-stu-id="091ef-144">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="091ef-145">若要获得有关 locatability 更改的通知：</span><span class="sxs-lookup"><span data-stu-id="091ef-145">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="091ef-146">订阅 OnTrackingChanged 事件</span><span class="sxs-lookup"><span data-stu-id="091ef-146">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="091ef-147">处理事件</span><span class="sxs-lookup"><span data-stu-id="091ef-147">Handle the event</span></span>

<span data-ttu-id="091ef-148">每当基础空间锚点在正在定位的状态与不能定位的状态之间发生变化时，将调用 **OnTrackingChanged** 事件。</span><span class="sxs-lookup"><span data-stu-id="091ef-148">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="091ef-149">然后处理事件：</span><span class="sxs-lookup"><span data-stu-id="091ef-149">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="091ef-150">有时会立即定位锚点。</span><span class="sxs-lookup"><span data-stu-id="091ef-150">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="091ef-151">在这种情况下，当 AddComponent () 返回时，定位点的 isLocated 属性将设置为 true <WorldAnchor> 。</span><span class="sxs-lookup"><span data-stu-id="091ef-151">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="091ef-152">因此，不会触发 OnTrackingChanged 事件。</span><span class="sxs-lookup"><span data-stu-id="091ef-152">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="091ef-153">清理模式是在附加定位点后使用初始 IsLocated 状态调用 OnTrackingChanged 处理程序。</span><span class="sxs-lookup"><span data-stu-id="091ef-153">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```