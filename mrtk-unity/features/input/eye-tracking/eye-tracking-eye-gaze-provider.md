---
title: 眼动跟踪注视提供者
description: MRTK 中的眼睛查看器文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，EyeTracking，EyeGaze，
ms.openlocfilehash: ef50a55d52a5dad9f424c8af8139565e02542b6c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144024"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a>在 Unity 脚本中访问目视跟踪数据

本文假设已了解如何在 MRTK 场景中设置目视跟踪 (参阅 [基本 MRTK 安装程序以使用目视跟踪](eye-tracking-basic-setup.md)) 。
在 MonoBehaviour 脚本中访问眼睛跟踪数据非常简单！ 只需使用 *CoreServices. InputSystem. EyeGazeProvider*。

## <a name="imixedrealityeyegazeprovider"></a>IMixedRealityEyeGazeProvider

MRTK 中的目视跟踪配置通过接口进行配置 [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) 。 使用 [CoreServices](eye-tracking-eye-gaze-provider.md) 可在运行时在工具包中注册默认的注视提供程序实现。
的有用属性 `EyeGazeProvider` 如下所述。

- **IsEyeTrackingEnabled**：如果用户已选择使用目视跟踪进行注视，则为 True。

- **IsEyeCalibrationValid**：指示用户的目视跟踪校准是否有效。
如果值尚未从目视跟踪系统收到数据，则返回 "null"。
它可能无效，因为用户跳过了眼睛跟踪校准。

- **IsEyeTrackingEnabledAndValid**：指示当前目视跟踪数据当前是否用于注视。

- **IsEyeTrackingDataValid**：如果目视跟踪数据可用，则为 True。
由于超时 (应该会使用户处于稳定状态，但) 或缺少跟踪硬件或权限时，此功能可能会变得不可用。
查看缺少的 [眼睛校准通知示例](eye-tracking-is-user-calibrated.md) ，该示例说明如何检测用户是否引人注目，并显示相应的通知。

- **GazeOrigin**： "注视" 射线的原点。
请注意，如果 "IsEyeGazeValid" 为 false，则将返回 *打印头* 注视原点。

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