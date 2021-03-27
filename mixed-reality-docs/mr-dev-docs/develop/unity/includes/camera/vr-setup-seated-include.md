---
ms.openlocfilehash: c7e5be36420ef14fe5aaeaafb49c0a990942339f
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636266"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

使用 MRTK for Unity 中的 [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 类，并将 **目标规模** 设置为 " **固定**"：

![MRTK 设置窗口](../../images/mrtk-target-scale.png)

MRTK 应自动处理 playspace 和相机的位置，但最好仔细检查：

![MRTK playspace](../../images/mrtk-playspace.png)

1. 从 " **层次结构** " 面板中，展开 " **MixedRealityPlayspace** " GameObject 并查找 " **照相机** " 子对象
2. 在 **检查器** 面板中，找到 **转换** 组件，并将 **位置** 更改为 **(X：0，Y：0，Z： 0)**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

在 [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)上设置跟踪源模式。 获取子系统后，调用 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)：

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

和使用 Unity 的 [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)。

![层次结构中的 XR 远程测试机组](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. 请参阅 **Windows 应用商店播放机设置** 中的 "**其他设置**" 部分
2. 选择 **Windows Mixed Reality** 作为设备，在较旧版本的 Unity 中，它可能作为 **Windows 全息** 列出
3. 选择 **支持的虚拟现实**

由于主相机对象会自动标记为相机，因此 Unity 会支持移动和平移。

>[!NOTE]
>需要在应用的每个场景中将这些设置应用到相机。
>
>默认情况下，当你在 Unity 中创建新场景时，它将包含层次结构中的一个主相机 GameObject，其中包括相机组件，但未正确应用下面的设置。

**命名空间：** *UnityEngine. XR*<br>
**类型：** *XRDevice*

若要生成 **仅限方向** 或 **固定规模的体验**，需将 Unity 设置为静止跟踪空间类型。 静止跟踪空间会将 Unity 的世界坐标系统设置为跟踪 [固定的引用框架](../../../../design/coordinate-systems.md#spatial-coordinate-systems)。 在静止跟踪模式下，显示在面板默认位置之前的编辑器中的内容 (向前) 在应用启动时将显示在用户的前面。

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

如果要构建大规模的 [体验](../../../../design/coordinate-systems.md)，可以通过调用 XR，在用户的当前头部位置 recenter Unity 的世界原点 **[。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法。