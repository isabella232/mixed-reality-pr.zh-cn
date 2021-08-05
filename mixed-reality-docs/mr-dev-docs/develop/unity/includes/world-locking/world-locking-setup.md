---
ms.openlocfilehash: e4ada87db2d9e483758030bf1bbe56dbacd7664ae7e1921540c0c7abfe14a7c7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208837"
---
# <a name="world-locking-tools-recommended"></a>[世界锁定工具 (推荐) ](#tab/wlt)

建议使用新的混合现实功能工具安装世界锁定工具。 从以下链接下载混合现实功能工具后，从"世界锁定工具"部分选择最新版本的 **WLT** **Core：**

![混合现实功能工具功能选择窗口，已选择"世界锁定工具"](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [使用 MR 功能工具安装世界锁定工具](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a>自动设置

当项目准备就绪后，从混合现实和世界锁定工具 **Toolkit >实用工具>场景实用工具**：

![选中了"混合现实"菜单Toolkit Unity 编辑器](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> 随时都可以重新运行"配置场景"实用工具。 例如，如果 AR 目标从旧版更改为 XR SDK，应重新运行它。 如果场景已正确配置，则运行实用工具不起作用。

### <a name="visualizers"></a>可视化工具

在早期开发过程中，添加可视化工具有助于确保 WLT 的设置和正常运行。 可以使用"删除可视化工具"实用工具删除它们，以提升生产性能;如果出于任何原因不再需要它们，也可以将其删除。 有关可视化工具的更多详细信息，请参阅工具 [文档](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers)。

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

混合现实 OpenXR 插件通过实现 Unity 的 ARFoundation **ARAnchorManager 提供基本定位点功能**。 若要了解 ARFoundation 中 ARAnchors 的基础知识，请访问 AR 定位点管理器 的 [ARFoundation 手册](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)。 

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a>构建全球规模的体验

**命名空间***：UnityEngine.XR.WSA*<br>
**类型***：WorldAnchor*

对于 **允许用户漫游** 超过 5 米HoloLens真正的世界规模的体验，除了用于房间缩放体验的新技术之外，还需要新技术。 你将使用的一个关键技术是创建空间定位点，[](../../../../design/coordinate-systems.md#spatial-anchors)以精确锁定物理世界中的全息影像群集，无论用户漫游了多远，然后在稍后的会话中再次找到这些全息[影像。](../../../../design/coordinate-systems.md#spatial-anchor-persistence)

在 Unity 中，通过将 **WorldAnchor** Unity 组件添加到 GameObject 来创建空间定位点。

### <a name="adding-a-world-anchor"></a>添加世界定位点

若要添加世界定位点，请对游戏对象调用要锚定在现实世界 `AddComponent<WorldAnchor>()` 中的转换。

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

就这么简单！ 此游戏对象现在将锚定到其当前在物理世界的位置 - 你可能会看到它的 Unity 世界坐标在一段时间稍作调整以确保物理对齐。 请参阅 [加载世界定位点](#loading-a-worldanchor) ，以在将来的应用会话中再次找到此定位位置。

### <a name="removing-a-world-anchor"></a>删除世界定位点

如果不再需要将 GameObject 锁定到物理世界位置，并且不打算移动此帧，则只需在 World Anchor 组件上调用 Destroy。

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

如果要移动 GameObject 此帧，则需要改为调用 DestroyImmediate。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>移动 World Anchored GameObject

当世界定位点位于 GameObject 上时，无法移动它。 如果需要移动此帧的 GameObject，需要：

1. DestroyImmediate World Anchor 组件
2. 移动 GameObject
3. 将新的 World Anchor 组件添加到 GameObject。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>处理可定位性更改

在一个时间点，WorldAnchor 可能无法位于物理世界。 如果发生这种情况，Unity 不会更新定位对象的转换。 在应用运行时，这也可能更改。 如果无法处理可定位性更改，则会导致对象未出现在世界上正确的物理位置。

若要获得有关可定位性更改的通知：：

1. 订阅 OnTrackingChanged 事件
2. 处理事件

每当基础空间定位点在可定位状态与不可定位状态之间发生更改时，将调用 **OnTrackingChanged** 事件。

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

然后处理 事件：

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

有时定位点会立即找到。 在这种情况下，当 AddComponent 返回时，定位点的 isLocated <WorldAnchor> 属性 () true。 因此，不会触发 OnTrackingChanged 事件。 一种干净模式是在附加定位点后，使用初始 IsLocated 状态调用 OnTrackingChanged 处理程序。

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```