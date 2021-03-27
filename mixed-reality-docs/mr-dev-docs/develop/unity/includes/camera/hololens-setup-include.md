---
ms.openlocfilehash: 7470690a96380184ead7319d4461005042c6db82
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636256"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

按照此 [分步教程](../../tutorials/mr-learning-base-01.md) 在 Unity 项目中添加和自动配置混合现实工具包。 还可以直接使用 MRTK for Unity 中的 [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 类，并将 **目标规模** 设置为 **World**：

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
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

可以将 [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) 用于 HoloLens 应用程序，该应用程序可以更好地使用定位点和 ARKit/ARCore。

![层次结构中的 AR 会话](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> AR 会话和相关功能需要安装 AR Foundation。

在不使用 ARSession 的情况下，也可以手动应用相机变化：

1. 选择 "**层次结构**" 面板中的 "**主相机**"
1. 在 **检查器** 面板中，找到 **转换** 组件，并将 **位置** 更改为 **(X：0，Y：0，Z： 0)**

   ![Unity 中的 "检查器" 窗格中的照相机](../../images/maincamera-350px.png)  
   *Unity 中的 "检查器" 窗格中的照相机*

1. 将 **TrackedPoseDriver** 添加到 **主摄像机**

# <a name="legacy-wsa"></a>[旧 WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. 选择 "**层次结构**" 面板中的 "**主相机**"
1. 在 **检查器** 面板中，找到 **转换** 组件，并将 **位置** 更改为 **(X：0，Y：0，Z： 0)**

   ![Unity 中的 "检查器" 窗格中的照相机](../../images/maincamera-350px.png)  
   *Unity 中的 "检查器" 窗格中的照相机*

1. 请参阅 **Windows 应用商店播放机设置** 中的 "**其他设置**" 部分
1. 选择 **Windows Mixed Reality** 作为设备，在较旧版本的 Unity 中，它可能作为 **Windows 全息** 列出
1. 选择 **支持的虚拟现实**

由于主相机对象会自动标记为相机，因此 Unity 会支持移动和平移。

>[!NOTE]
>需要在应用的每个场景中将这些设置应用到相机。
>
>默认情况下，当你在 Unity 中创建新场景时，它将包含层次结构中的一个主相机 GameObject，其中包括相机组件，但可能未正确应用这些设置。