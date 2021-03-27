---
ms.openlocfilehash: 5f990569ae4052377cba717b5526bb8ba51b8016
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636267"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

使用 MRTK for Unity 中的 [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace)类，并将 **目标规模** 设置为 "空间 **" 或 "** 目标"：

![MRTK 设置窗口](../../images/mrtk-target-scale.png)

MRTK 应自动处理 playspace 和相机的位置，但最好仔细检查：

![MRTK playspace](../../images/mrtk-playspace.png)

1. 从 " **层次结构** " 面板中，展开 " **MixedRealityPlayspace** " GameObject 并查找 " **照相机** " 子对象
2. 在 **检查器** 面板中，找到 **转换** 组件，并将 **位置** 更改为 **(X：0，Y：0，Z： 0)**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

在 [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)上设置跟踪源模式。 获取子系统后，调用 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)：

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
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

对于 **大规模** 或 **房间规模的体验**，需要相对于楼层放置内容。 使用 **[空间阶段](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**（表示用户在首次运行期间设置的已定义的层级来源和可选房间边界）的原因。

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

* 如果 SetTrackingSpaceType 返回 true，则 Unity 已成功切换其世界坐标系统以跟踪 [引用的阶段框架](../../../../design/coordinate-systems.md#spatial-coordinate-systems)。
* 如果 SetTrackingSpaceType 返回 false，则 Unity 无法切换到引用的阶段框架，原因可能是用户尚未在其环境中设置楼层。 虽然错误的返回值不常见，但如果在不同的空间中设置了阶段，并且在用户未设置新阶段的情况下将设备移动到当前房间，则会发生这种情况。

应用成功设置 RoomScale 跟踪空间类型后，放置在 y = 0 平面上的内容将显示在地面上。 位于0，0，0的原点将是用户在房间设置期间考验的特定位置，并以-Z 表示在安装过程中的正向方向。