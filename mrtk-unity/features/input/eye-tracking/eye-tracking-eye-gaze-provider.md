---
title: 眼动跟踪注视提供者
description: MRTK 中眼睛凝视提供程序的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， EyeTracking， EyeGaze，
ms.openlocfilehash: 9a62bdba0bc4bb2985e6c2ffc4e8e66a8f867681a5e51c9e5f235b29f3baaf50
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193189"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a>在 Unity 脚本中访问眼动跟踪数据

本文假设用户已了解如何在 MRTK 场景中设置眼动跟踪 (请参阅基本 [MRTK](eye-tracking-basic-setup.md) 设置以使用眼动跟踪) 。
在 MonoBehaviour 脚本中访问眼动跟踪数据非常简单！ 只需使用 *CoreServices.InputSystem.EyeGazeProvider*。

## <a name="imixedrealityeyegazeprovider"></a>IMixedRealityEyeGazeProvider

MRTK 中的眼动跟踪配置是通过 接口 [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) 配置的。 使用 [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) 提供在运行时在工具包中注册的默认凝视提供程序实现。
下面概述了 `EyeGazeProvider` 的有用属性。

- **IsEyeTrackingEnabled：** 如果用户已选择使用眼动跟踪进行凝视，则返回 True。

- **IsEyeCalibrationValid：** 指示用户的眼动跟踪校准是否有效。
如果值尚未从眼动跟踪系统接收数据，则返回"null"。
它可能无效，因为用户跳过了眼动跟踪校准。

- **IsEyeTrackingEnabledAndValid：** 指示当前眼动跟踪数据当前是否用于凝视。

- **IsEyeTrackingDataValid：** 如果眼动跟踪数据可用，则返回 True。
它可能由于超时超过而不可用， (用户闪烁时，它) 或缺少跟踪硬件或权限。
请查看我们的 [缺失眼校准通知示例](eye-tracking-is-user-calibrated.md) ，该示例说明如何检测用户是否进行眼校准，以及显示适当的通知。

- **GazeOrigin：** 凝视射线的来源。
请注意，如果"IsEyeGazeValid"为 false，这将返回头部凝视原点。 

- **GazeDirection：** 凝视射线的方向。
如果"IsEyeGazeValid"为 false，这将返回头部凝视方向。 

- HitInfo、HitPosition、HitNormal 等：有关当前目标的信息。  
同样， `IsEyeGazeValid` 如果 为 false，则这基于用户的 *头部凝* 视。

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a>使用 CoreServices.InputSystem.EyeGazeProvider 的示例

下面是 [FollowEyeGaze.cs 的示例](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze)：

- 获取用户正在查看的全息影像点：

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- 显示与用户当前正在查找的可视资产保持固定距离：

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a>另请参阅

- [MRTK 眼动跟踪概述](eye-tracking-main.md)
- [MRTK 眼动跟踪设置](eye-tracking-basic-setup.md)
- [MRTK 眼动跟踪校准](eye-tracking-is-user-calibrated.md)
- [HoloLens 2眼动跟踪文档](/windows/mixed-reality/eye-tracking)