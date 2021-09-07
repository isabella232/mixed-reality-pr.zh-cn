---
ms.openlocfilehash: 047a77259d78ba8ea68002a5142080971900e305
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244250"
---
# <a name="world-locking-tools-recommended"></a>[ (推荐的全球锁定工具) ](#tab/wlt)

建议使用新的混合现实功能工具安装全球锁定工具。 从下面的链接下载了混合现实功能工具之后，从 "**全球锁定工具**" 部分中选择 **WLT Core** 的最新版本：

![选择了世界锁定工具的混合现实功能工具功能选择窗口](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [利用 MR 功能工具安装全球锁定工具](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a>自动安装

当你的项目准备就绪时，请从 **混合现实 > 世界锁定工具** 中运行配置场景实用程序：

![选定了混合现实 Toolkit 菜单的 Unity 编辑器](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> 可以随时重新运行 "配置场景" 实用工具。 例如，如果 AR 目标已从旧版本更改为 XR SDK，则应重新运行该示例。 如果场景已正确配置，则运行该实用程序将不起作用。

### <a name="visualizers"></a>可视化工具

在早期开发过程中，添加可视化工具有助于确保 WLT 设置正确且工作正常。 可以使用 "删除可视化工具" 实用工具将其从生产性能中删除，或者出于任何原因而不再需要。 有关可视化工具的更多详细信息，请参阅 [工具文档](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers)。

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

Mixed Reality OpenXR 插件通过实现 Unity 的 ARFoundation **ARAnchorManager** 提供基本的定位点功能。 若要了解有关 ARFoundation 中 ARAnchors 的基础知识，请访问 [AR 定位管理器的 ARFoundation 手册](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)。 

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a>构建全球范围的体验

**命名空间：** *UnityEngine. XR*<br>
**类型：** *WorldAnchor*

对于 HoloLens 上的真正 **世界规模的体验**，让用户游离5米以上，你将需要超出用于房间规模的体验的新技术。 你将使用的一项关键方法是创建一个 [空间定位点](../../../../design/coordinate-systems.md#spatial-anchors) ，以便在物理世界中精确地锁定影像的分类，无论用户漫游到多远，然后 [在以后的会话中再次查找这些全息影像](../../../../design/coordinate-systems.md#spatial-anchor-persistence)。

在 Unity 中，可以通过将 **WorldAnchor** Unity 组件添加到 GameObject 来创建空间锚。

### <a name="adding-a-world-anchor"></a>添加世界锚

若要添加世界定位点，请 `AddComponent<WorldAnchor>()` 使用要锚定的转换，对游戏对象调用。

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

就这么简单！ 现在，此游戏对象将锚定到其在物理世界中的当前位置-你可能会看到其 Unity 世界坐标在一段时间后会略微调整，以确保物理对齐。 请参阅 [加载世界定位点](#loading-a-worldanchor) ，在未来的应用程序会话中再次查找此定位位置。

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