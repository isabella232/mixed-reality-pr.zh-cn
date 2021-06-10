---
ms.openlocfilehash: 3bffb5db8f4a36d04c2b408c939cbd2010a7def7
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748466"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

使用 MRTK for Unity 中的 [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace)类，将"目标 **刻度"设置为****"固定"：**

![MRTK 设置窗口](../../images/mrtk-target-scale.png)

MRTK 应自动处理播放空间和相机的位置，但请仔细检查：

![MRTK playspace](../../images/mrtk-playspace.png)

1. 在" **层次结构"面板** 中，展开 **"MixedRealityPlayspace** GameObject"并找到 **"主相机"** 子对象
2. 在"**检查器**"面板中，找到 **"转换**"组件，将"位置"更改为 (**X： 0， Y： 0， Z： 0)**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

在 [XRInputSubsystem 上设置跟踪源模式](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)。 获取子系统后，调用 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)：

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

使用 Unity 的 [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)。

![层次结构中的 XR 演练](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. 转到 Windows **应用商店播放器** 设置 **的其他设置部分**
2. 选择 **Windows Mixed Reality** 作为设备，在旧版 Unity 中可能会列为 **Windows Holographic**
3. 选择 **"支持的虚拟现实"**

由于主相机对象自动标记为照相机，Unity 支持所有移动和转换。

>[!NOTE]
>需要在应用的每个场景中将这些设置应用于相机。
>
>默认情况下，在 Unity 中创建新场景时，它将在层次结构中包含主相机 GameObject，其中包括相机组件，但没有正确应用以下设置。

**命名空间***：UnityEngine.XR*<br>
**类型***：XRDevice*

若要构建 **仅方向或****方向缩放** 体验，需要将 Unity 设置为"固定跟踪空间"类型。 固定跟踪空间设置 Unity 世界坐标系以跟踪 [固定参考框架](../../../../design/coordinate-systems.md#spatial-coordinate-systems)。 在"固定跟踪"模式下，当应用启动时，编辑器中位于相机默认位置前面的内容 (向前是 -Z) 会显示在用户的前面。

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**命名空间***：UnityEngine.XR*<br>
**类型***：InputTracking*

对于纯方向体验（如 360 度视频查看器 (位置头部更新会破坏假象) ，可以设置[XR。InputTracking.disablePositionalTracking 为](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html)true：

```cs
InputTracking.disablePositionalTracking = true;
```

若要 **获得固定缩放体验**，若要让用户稍后更晚地获得源，可以调用 [XR。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 方法：

```cs
InputTracking.Recenter();
```

如果要构建一种 [步进缩放](../../../../design/coordinate-systems.md)体验，可以通过调用 XR，在用户的当前头部位置使用最新的 Unity 世界 **[原点。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法。