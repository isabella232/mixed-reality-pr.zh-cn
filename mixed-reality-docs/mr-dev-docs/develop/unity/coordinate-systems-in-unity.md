---
title: Unity 中的坐标系统
description: 了解如何在 Unity 中构建固定的、共同的、房间规模和全球混合的现实体验。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 坐标系统，空间坐标系统，仅限方向，固定比例大规模，房间规模，世界规模，360度，固定的，房间，房间，世界，，规模，位置，方向，Unity，定位，空间锚，世界锚，世界锁定，世界锁定，身体锚，世界锁定，，跟踪丢失，locatability，界限，recenter，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 91b1adf6dcf1c54d0d29a02bfb97ac4674a87c88
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528751"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="48a79-104">Unity 中的坐标系统</span><span class="sxs-lookup"><span data-stu-id="48a79-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="48a79-105">Windows Mixed Reality 在各种经验范围内支持应用，从仅限方向和大规模应用，再到房间规模的应用。</span><span class="sxs-lookup"><span data-stu-id="48a79-105">Windows Mixed Reality supports apps across a wide range of experience scales, from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="48a79-106">在 HoloLens 上，你可以进一步构建全球规模的应用程序，让用户经历5米以上的工作，探索一座建筑的整个楼层。</span><span class="sxs-lookup"><span data-stu-id="48a79-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="48a79-107">在 Unity 中构建混合现实体验的第一步是了解 [坐标系统，并选择应用将面向的体验扩展](../../design/coordinate-systems.md) 。</span><span class="sxs-lookup"><span data-stu-id="48a79-107">Your first step in building a mixed reality experience in Unity is to understand [coordinate systems and choose the experience scale](../../design/coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="48a79-108">构建仅限方向或固定规模的体验</span><span class="sxs-lookup"><span data-stu-id="48a79-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="48a79-109">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="48a79-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="48a79-110">**类型：** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="48a79-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="48a79-111">若要生成 **仅限方向** 或 **固定规模的体验**，需将 Unity 设置为静止跟踪空间类型。</span><span class="sxs-lookup"><span data-stu-id="48a79-111">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="48a79-112">静止跟踪空间会将 Unity 的世界坐标系统设置为跟踪 [固定的引用框架](../../design/coordinate-systems.md#spatial-coordinate-systems)。</span><span class="sxs-lookup"><span data-stu-id="48a79-112">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="48a79-113">在静止跟踪模式下，显示在面板默认位置之前的编辑器中的内容 (向前) 在应用启动时将显示在用户的前面。</span><span class="sxs-lookup"><span data-stu-id="48a79-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="48a79-114">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="48a79-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="48a79-115">**类型：** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="48a79-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="48a79-116">对于纯粹的 **仅限方向的体验** ，例如360度的视频查看器 (其中位置标题更新会破坏错觉) ，可以设置 [XR。InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) 为 true：</span><span class="sxs-lookup"><span data-stu-id="48a79-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="48a79-117">对于 **大规模体验**，若要让用户在以后 recenter 原位置，可以调用 [XR。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 方法：</span><span class="sxs-lookup"><span data-stu-id="48a79-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="48a79-118">构建大规模或会议室规模的体验</span><span class="sxs-lookup"><span data-stu-id="48a79-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="48a79-119">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="48a79-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="48a79-120">**类型：** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="48a79-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="48a79-121">对于 **大规模** 或 **房间规模的体验**，需要相对于楼层放置内容。</span><span class="sxs-lookup"><span data-stu-id="48a79-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="48a79-122">使用 **[空间阶段](../../design/coordinate-systems.md#spatial-coordinate-systems)**（表示用户在首次运行期间设置的已定义的层级来源和可选房间边界）的原因。</span><span class="sxs-lookup"><span data-stu-id="48a79-122">You reason about the user's floor using the **[spatial stage](../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="48a79-123">若要确保 Unity 在地面级别使用其世界坐标系统进行操作，可以设置和测试 Unity 是否正在使用 RoomScale 跟踪空间类型：</span><span class="sxs-lookup"><span data-stu-id="48a79-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* <span data-ttu-id="48a79-124">如果 SetTrackingSpaceType 返回 true，则 Unity 已成功切换其世界坐标系统以跟踪 [引用的阶段框架](../../design/coordinate-systems.md#spatial-coordinate-systems)。</span><span class="sxs-lookup"><span data-stu-id="48a79-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="48a79-125">如果 SetTrackingSpaceType 返回 false，则 Unity 无法切换到引用的阶段框架，原因可能是用户尚未在其环境中设置楼层。</span><span class="sxs-lookup"><span data-stu-id="48a79-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="48a79-126">虽然错误的返回值不常见，但如果在不同的空间中设置了阶段，并且在用户未设置新阶段的情况下将设备移动到当前房间，则会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="48a79-126">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="48a79-127">应用成功设置 RoomScale 跟踪空间类型后，放置在 y = 0 平面上的内容将显示在地面上。</span><span class="sxs-lookup"><span data-stu-id="48a79-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="48a79-128">位于0，0，0的原点将是用户在房间设置期间考验的特定位置，并以-Z 表示在安装过程中的正向方向。</span><span class="sxs-lookup"><span data-stu-id="48a79-128">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="48a79-129">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="48a79-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="48a79-130">**类型：** *边界*</span><span class="sxs-lookup"><span data-stu-id="48a79-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="48a79-131">在脚本代码中，你可以在 UnityEngine 类型上调用 TryGetGeometry 方法来获取边界多边形，并指定 "TrackedArea" 的边界类型。</span><span class="sxs-lookup"><span data-stu-id="48a79-131">In script code, you can then call the TryGetGeometry method on the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="48a79-132">如果用户定义了边界 (你获取了) 的顶点列表，则可以安全地向用户提供一个 **会议室规模的体验** ，用户可在其中浏览你创建的场景。</span><span class="sxs-lookup"><span data-stu-id="48a79-132">If the user defined a boundary (you get back a list of vertices), it's safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

> [!NOTE]
> <span data-ttu-id="48a79-133">当用户接近边界时，系统将自动渲染边界。</span><span class="sxs-lookup"><span data-stu-id="48a79-133">The system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="48a79-134">您的应用程序不需要使用此多边形来呈现边界本身。</span><span class="sxs-lookup"><span data-stu-id="48a79-134">Your app doesn't need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="48a79-135">不过，您可以选择使用此边界多边形布局场景对象，以确保用户可以在不 teleporting 的情况下以物理方式访问这些对象：</span><span class="sxs-lookup"><span data-stu-id="48a79-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="48a79-136">构建全球范围的体验</span><span class="sxs-lookup"><span data-stu-id="48a79-136">Building a world-scale experience</span></span>

<span data-ttu-id="48a79-137">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="48a79-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="48a79-138">**类型：** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="48a79-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="48a79-139">对于 HoloLens 上真正的 **全球规模体验** ，让用户游离5米以上，你将需要超出用于房间规模体验的新技术。</span><span class="sxs-lookup"><span data-stu-id="48a79-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="48a79-140">你将使用的一项关键方法是创建一个 [空间定位点](../../design/coordinate-systems.md#spatial-anchors) ，以便在物理世界中精确地锁定影像的分类，无论用户漫游到多远，然后 [在以后的会话中再次查找这些全息影像](../../design/coordinate-systems.md#spatial-anchor-persistence)。</span><span class="sxs-lookup"><span data-stu-id="48a79-140">One key technique you'll use is to create a [spatial anchor](../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="48a79-141">在 Unity 中，可以通过将 **WorldAnchor** Unity 组件添加到 GameObject 来创建空间锚。</span><span class="sxs-lookup"><span data-stu-id="48a79-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="48a79-142">添加世界锚</span><span class="sxs-lookup"><span data-stu-id="48a79-142">Adding a World Anchor</span></span>

<span data-ttu-id="48a79-143">若要添加世界定位点，请 <WorldAnchor> 使用要锚定的转换在游戏对象上调用 AddComponent () 。</span><span class="sxs-lookup"><span data-stu-id="48a79-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="48a79-144">就这么简单！</span><span class="sxs-lookup"><span data-stu-id="48a79-144">That's it!</span></span> <span data-ttu-id="48a79-145">现在，此游戏对象将锚定到其在物理世界中的当前位置-你可能会看到其 Unity 世界坐标在一段时间后会略微调整，以确保物理对齐。</span><span class="sxs-lookup"><span data-stu-id="48a79-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="48a79-146">使用 [持久性](persistence-in-unity.md) 在未来的应用程序会话中再次查找此定位位置。</span><span class="sxs-lookup"><span data-stu-id="48a79-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="48a79-147">删除世界锚</span><span class="sxs-lookup"><span data-stu-id="48a79-147">Removing a World Anchor</span></span>

<span data-ttu-id="48a79-148">如果不再希望 GameObject 锁定到物理世界位置，并且不打算将其移动到此帧，则可以只在世界锚点组件上调用销毁。</span><span class="sxs-lookup"><span data-stu-id="48a79-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="48a79-149">如果要将 GameObject 移动到此帧，则需改为调用 DestroyImmediate。</span><span class="sxs-lookup"><span data-stu-id="48a79-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="48a79-150">移动世界定位的 GameObject</span><span class="sxs-lookup"><span data-stu-id="48a79-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="48a79-151">GameObject 在世界锚点上时无法移动。</span><span class="sxs-lookup"><span data-stu-id="48a79-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="48a79-152">如果需要将 GameObject 移动到此框架，需要执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="48a79-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="48a79-153">DestroyImmediate 世界锚组件</span><span class="sxs-lookup"><span data-stu-id="48a79-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="48a79-154">移动 GameObject</span><span class="sxs-lookup"><span data-stu-id="48a79-154">Move the GameObject</span></span>
3. <span data-ttu-id="48a79-155">向 GameObject 添加新的世界锚点组件。</span><span class="sxs-lookup"><span data-stu-id="48a79-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="48a79-156">处理 Locatability 更改</span><span class="sxs-lookup"><span data-stu-id="48a79-156">Handling Locatability Changes</span></span>

<span data-ttu-id="48a79-157">在物理环境中，可能无法在某个时间点定位 WorldAnchor。</span><span class="sxs-lookup"><span data-stu-id="48a79-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="48a79-158">如果出现这种情况，则 Unity 不会更新定位对象的转换。</span><span class="sxs-lookup"><span data-stu-id="48a79-158">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="48a79-159">在应用程序运行时，这也可能会更改。</span><span class="sxs-lookup"><span data-stu-id="48a79-159">This also can change while an app is running.</span></span> <span data-ttu-id="48a79-160">如果无法处理 locatability 中的更改，则会导致对象不显示在世界上正确的物理位置。</span><span class="sxs-lookup"><span data-stu-id="48a79-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="48a79-161">若要获得有关 locatability 更改的通知：</span><span class="sxs-lookup"><span data-stu-id="48a79-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="48a79-162">订阅 OnTrackingChanged 事件</span><span class="sxs-lookup"><span data-stu-id="48a79-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="48a79-163">处理事件</span><span class="sxs-lookup"><span data-stu-id="48a79-163">Handle the event</span></span>

<span data-ttu-id="48a79-164">每当基础空间锚点在正在定位的状态与不能定位的状态之间发生变化时，将调用 **OnTrackingChanged** 事件。</span><span class="sxs-lookup"><span data-stu-id="48a79-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="48a79-165">然后处理事件：</span><span class="sxs-lookup"><span data-stu-id="48a79-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="48a79-166">有时会立即定位锚点。</span><span class="sxs-lookup"><span data-stu-id="48a79-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="48a79-167">在这种情况下，当 AddComponent () 返回时，定位点的 isLocated 属性将设置为 true <WorldAnchor> 。</span><span class="sxs-lookup"><span data-stu-id="48a79-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="48a79-168">因此，不会触发 OnTrackingChanged 事件。</span><span class="sxs-lookup"><span data-stu-id="48a79-168">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="48a79-169">清理模式是在附加定位点后使用初始 IsLocated 状态调用 OnTrackingChanged 处理程序。</span><span class="sxs-lookup"><span data-stu-id="48a79-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="48a79-170">跨设备共享锚</span><span class="sxs-lookup"><span data-stu-id="48a79-170">Sharing anchors across devices</span></span>

<span data-ttu-id="48a79-171">使用 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a> ，从本地 WorldAnchor 创建持久的云锚点，你的应用可以在多个 HoloLens、IOS 和 Android 设备上找到它。</span><span class="sxs-lookup"><span data-stu-id="48a79-171">Use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="48a79-172">通过在多个设备之间共享公用空间定位点，每个用户都可以查看相对于同一物理位置中的定位点呈现的内容。</span><span class="sxs-lookup"><span data-stu-id="48a79-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="48a79-173">这可实现实时共享体验。</span><span class="sxs-lookup"><span data-stu-id="48a79-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="48a79-174">若要开始在 Unity 中构建共享体验，请尝试执行5分钟的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间锚点 Unity 快速入门</a>。</span><span class="sxs-lookup"><span data-stu-id="48a79-174">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="48a79-175">启动并运行 Azure 空间锚点后，便可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中创建和定位锚</a>。</span><span class="sxs-lookup"><span data-stu-id="48a79-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="48a79-176">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="48a79-176">Next Development Checkpoint</span></span>

<span data-ttu-id="48a79-177">如果遵循我们所说的 Unity 开发检查点旅程，就是探索混合现实核心构建基块的过程。</span><span class="sxs-lookup"><span data-stu-id="48a79-177">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="48a79-178">从这里，你可以继续了解下一部分基础知识：</span><span class="sxs-lookup"><span data-stu-id="48a79-178">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="48a79-179">凝视</span><span class="sxs-lookup"><span data-stu-id="48a79-179">Gaze</span></span>](gaze-in-unity.md)

<span data-ttu-id="48a79-180">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="48a79-180">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="48a79-181">共享体验</span><span class="sxs-lookup"><span data-stu-id="48a79-181">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="48a79-182">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="48a79-182">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="48a79-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="48a79-183">See Also</span></span>
* [<span data-ttu-id="48a79-184">体验规模</span><span class="sxs-lookup"><span data-stu-id="48a79-184">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="48a79-185">空间阶段</span><span class="sxs-lookup"><span data-stu-id="48a79-185">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="48a79-186">Unity 中的失跟</span><span class="sxs-lookup"><span data-stu-id="48a79-186">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="48a79-187">空间定位点</span><span class="sxs-lookup"><span data-stu-id="48a79-187">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="48a79-188">Unity 中的持久性</span><span class="sxs-lookup"><span data-stu-id="48a79-188">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="48a79-189">Unity 中的共享体验</span><span class="sxs-lookup"><span data-stu-id="48a79-189">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="48a79-190"><a href="/azure/spatial-anchors" target="_blank">Azure 空间定位点</a></span><span class="sxs-lookup"><span data-stu-id="48a79-190"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="48a79-191"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">用于 Unity 的 Azure 空间定位点 SDK</a></span><span class="sxs-lookup"><span data-stu-id="48a79-191"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>