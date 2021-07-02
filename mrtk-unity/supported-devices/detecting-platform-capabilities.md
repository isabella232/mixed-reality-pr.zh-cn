---
title: 检测平台功能
description: MRTK 支持的不同功能的详细信息
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，功能，
ms.openlocfilehash: 70d320e178f4635d74b5be6a1874eb4254801719
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175519"
---
# <a name="detecting-platform-capabilities"></a>检测平台功能

MRTK 的一个常见问题是需要知道哪个特定设备 (ex： Microsoft HoloLens 2) 用于运行应用程序。 在不同的平台上确定确切的硬件可能会有挑战性。 相反，MRTK 提供了一种在运行时标识特定功能的方法， (例如，如果当前设备终结点支持明确) 的操作。

## <a name="capabilities"></a>功能

混合现实 Toolkit 提供 [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) 枚举，用于定义应用程序可在运行时查询的一组功能。

### <a name="input-system-capabilities"></a>输入系统功能

默认的 MRTK 输入系统支持查询以下功能：

| 功能 | 说明 |
|---|---|
| ArticulatedHand | 明确表述的手写输入 |
| EyeTracking | 眼睛定位 |
| GGVHand | 注视手势-语音输入 |
| MotionController | 运动控制器输入 |
| VoiceCommand | 使用应用定义关键字的语音命令 |
| VoiceDictation | 语音到文本听写 |

下面的示例代码检查输入系统是否已加载数据提供程序，并支持有表述的指针。

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a>空间感知功能

默认的 MRTK 空间感知系统支持查询以下功能：

| 功能 | 说明 |
|---|---|
| SpatialAwarenessMesh | 空间网格 |
| SpatialAwarenessPlane | 空间平面 |
| SpatialAwarenessPoint | 空间点 |

此示例将检查空间感知系统是否已加载支持空间网格的数据访问接口。

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a>另请参阅

- [IMixedRealityCapabilityCheck API 文档](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [MixedRealityCapability 枚举文档](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
