---
ms.openlocfilehash: 61fe8754192c1fbd0634fd9d1e1994327599321b
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748544"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

使用 MRTK for Unity 中的 [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace)类，将"目标刻度"设置为"房间"**或**"长期 **"：** 

![MRTK 设置窗口](../../images/mrtk-target-scale.png)

MRTK 应自动处理播放空间和相机的位置，但请仔细检查：

![MRTK playspace](../../images/mrtk-playspace.png)

1. 在" **层次结构"面板** 中，展开 **"MixedRealityPlayspace** GameObject"并找到 **"主相机"** 子对象
2. 在"**检查器**"面板中，找到 **"转换**"组件，将"位置"更改为 (**X： 0， Y： 0， Z： 0)**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

在 [XRInputSubsystem 上设置跟踪源模式](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)。 获取子系统后，调用 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)：

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
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

若要 **获得长期缩放****或房间** 缩放体验，需要相对于楼层放置内容。 使用空间阶段 来推理用户楼层，该 **[](../../../../design/coordinate-systems.md#spatial-coordinate-systems)** 空间阶段表示用户在首次运行期间设置的已定义的楼层原点和可选房间边界。

若要确保 Unity 使用其世界坐标系在楼层运行，可以设置并测试 Unity 是否正在使用 RoomScale 跟踪空间类型：

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

* 如果 SetTrackingSpaceType 返回 true，Unity 已成功切换其世界坐标系，以跟踪 [引用 的阶段框架](../../../../design/coordinate-systems.md#spatial-coordinate-systems)。
* 如果 SetTrackingSpaceType 返回 false，Unity 将无法切换到引用的阶段框架，原因可能是用户尚未设置其环境中楼层。 虽然 false 返回值并不常见，但如果在不同房间中设置了阶段，并且设备移动到当前房间，而用户未设置新阶段，则可能会发生此情况。

应用成功设置 RoomScale 跟踪空间类型后，放置在 y=0 平面上的内容将显示在楼层上。 0、0、0 的原点将是用户在房间设置期间在楼层中旋转的特定位置，-Z 表示他们在安装过程中面向的向前方向。