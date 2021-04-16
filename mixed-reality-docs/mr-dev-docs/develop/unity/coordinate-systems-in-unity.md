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
# <a name="coordinate-systems-in-unity"></a>Unity 中的坐标系统

Windows Mixed Reality 在各种经验范围内支持应用，从仅限方向和大规模应用，再到房间规模的应用。 在 HoloLens 上，你可以进一步构建全球规模的应用程序，让用户经历5米以上的工作，探索一座建筑的整个楼层。

在 Unity 中构建混合现实体验的第一步是了解 [坐标系统，并选择应用将面向的体验扩展](../../design/coordinate-systems.md) 。

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>构建仅限方向或固定规模的体验

**命名空间：** *UnityEngine. XR*<br>
**类型：** *XRDevice*

若要生成 **仅限方向** 或 **固定规模的体验**，需将 Unity 设置为静止跟踪空间类型。 静止跟踪空间会将 Unity 的世界坐标系统设置为跟踪 [固定的引用框架](../../design/coordinate-systems.md#spatial-coordinate-systems)。 在静止跟踪模式下，显示在面板默认位置之前的编辑器中的内容 (向前) 在应用启动时将显示在用户的前面。

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**命名空间：** *UnityEngine. XR*<br>
**类型：** *InputTracking*

对于纯粹的 **仅限方向的体验** ，例如360度的视频查看器 (其中位置标题更新会破坏错觉) ，可以设置 [XR。InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) 为 true：

```cs
InputTracking.disablePositionalTracking = true;
```

对于 **大规模体验**，若要让用户在以后 recenter 原位置，可以调用 [XR。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 方法：

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>构建大规模或会议室规模的体验

**命名空间：** *UnityEngine. XR*<br>
**类型：** *XRDevice*

对于 **大规模** 或 **房间规模的体验**，需要相对于楼层放置内容。 使用 **[空间阶段](../../design/coordinate-systems.md#spatial-coordinate-systems)**（表示用户在首次运行期间设置的已定义的层级来源和可选房间边界）的原因。

若要确保 Unity 在地面级别使用其世界坐标系统进行操作，可以设置和测试 Unity 是否正在使用 RoomScale 跟踪空间类型：

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
* 如果 SetTrackingSpaceType 返回 true，则 Unity 已成功切换其世界坐标系统以跟踪 [引用的阶段框架](../../design/coordinate-systems.md#spatial-coordinate-systems)。
* 如果 SetTrackingSpaceType 返回 false，则 Unity 无法切换到引用的阶段框架，原因可能是用户尚未在其环境中设置楼层。 虽然错误的返回值不常见，但如果在不同的空间中设置了阶段，并且在用户未设置新阶段的情况下将设备移动到当前房间，则会发生这种情况。

应用成功设置 RoomScale 跟踪空间类型后，放置在 y = 0 平面上的内容将显示在地面上。 位于0，0，0的原点将是用户在房间设置期间考验的特定位置，并以-Z 表示在安装过程中的正向方向。

**命名空间：** *UnityEngine. XR*<br>
**类型：** *边界*

在脚本代码中，你可以在 UnityEngine 类型上调用 TryGetGeometry 方法来获取边界多边形，并指定 "TrackedArea" 的边界类型。 如果用户定义了边界 (你获取了) 的顶点列表，则可以安全地向用户提供一个 **会议室规模的体验** ，用户可在其中浏览你创建的场景。

> [!NOTE]
> 当用户接近边界时，系统将自动渲染边界。 您的应用程序不需要使用此多边形来呈现边界本身。 不过，您可以选择使用此边界多边形布局场景对象，以确保用户可以在不 teleporting 的情况下以物理方式访问这些对象：

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>构建全球范围的体验

**命名空间：** *UnityEngine. XR*<br>
**类型：** *WorldAnchor*

对于 HoloLens 上真正的 **全球规模体验** ，让用户游离5米以上，你将需要超出用于房间规模体验的新技术。 你将使用的一项关键方法是创建一个 [空间定位点](../../design/coordinate-systems.md#spatial-anchors) ，以便在物理世界中精确地锁定影像的分类，无论用户漫游到多远，然后 [在以后的会话中再次查找这些全息影像](../../design/coordinate-systems.md#spatial-anchor-persistence)。

在 Unity 中，可以通过将 **WorldAnchor** Unity 组件添加到 GameObject 来创建空间锚。

### <a name="adding-a-world-anchor"></a>添加世界锚

若要添加世界定位点，请 <WorldAnchor> 使用要锚定的转换在游戏对象上调用 AddComponent () 。

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

就这么简单！ 现在，此游戏对象将锚定到其在物理世界中的当前位置-你可能会看到其 Unity 世界坐标在一段时间后会略微调整，以确保物理对齐。 使用 [持久性](persistence-in-unity.md) 在未来的应用程序会话中再次查找此定位位置。

### <a name="removing-a-world-anchor"></a>删除世界锚

如果不再希望 GameObject 锁定到物理世界位置，并且不打算将其移动到此帧，则可以只在世界锚点组件上调用销毁。

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

如果要将 GameObject 移动到此帧，则需改为调用 DestroyImmediate。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>移动世界定位的 GameObject

GameObject 在世界锚点上时无法移动。 如果需要将 GameObject 移动到此框架，需要执行以下操作：
1. DestroyImmediate 世界锚组件
2. 移动 GameObject
3. 向 GameObject 添加新的世界锚点组件。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>处理 Locatability 更改

在物理环境中，可能无法在某个时间点定位 WorldAnchor。 如果出现这种情况，则 Unity 不会更新定位对象的转换。 在应用程序运行时，这也可能会更改。 如果无法处理 locatability 中的更改，则会导致对象不显示在世界上正确的物理位置。

若要获得有关 locatability 更改的通知：
1. 订阅 OnTrackingChanged 事件
2. 处理事件

每当基础空间锚点在正在定位的状态与不能定位的状态之间发生变化时，将调用 **OnTrackingChanged** 事件。

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

然后处理事件：

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

有时会立即定位锚点。 在这种情况下，当 AddComponent () 返回时，定位点的 isLocated 属性将设置为 true <WorldAnchor> 。 因此，不会触发 OnTrackingChanged 事件。 清理模式是在附加定位点后使用初始 IsLocated 状态调用 OnTrackingChanged 处理程序。

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>跨设备共享锚

使用 <a href="/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a> ，从本地 WorldAnchor 创建持久的云锚点，你的应用可以在多个 HoloLens、IOS 和 Android 设备上找到它。  通过在多个设备之间共享公用空间定位点，每个用户都可以查看相对于同一物理位置中的定位点呈现的内容。  这可实现实时共享体验。

若要开始在 Unity 中构建共享体验，请尝试执行5分钟的 <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间锚点 Unity 快速入门</a>。

启动并运行 Azure 空间锚点后，便可以 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中创建和定位锚</a>。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所说的 Unity 开发检查点旅程，就是探索混合现实核心构建基块的过程。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [凝视](gaze-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅
* [体验规模](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [空间阶段](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Unity 中的失跟](tracking-loss-in-unity.md)
* [空间定位点](../../design/spatial-anchors.md)
* [Unity 中的持久性](persistence-in-unity.md)
* [Unity 中的共享体验](shared-experiences-in-unity.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">用于 Unity 的 Azure 空间定位点 SDK</a>