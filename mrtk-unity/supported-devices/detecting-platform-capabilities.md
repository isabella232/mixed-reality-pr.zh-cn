---
title: 检测PlatformCapabilities
description: MRTK 支持的不同功能的详细信息
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 功能，
ms.openlocfilehash: 62e03c6d47deb079d3460759b5c694dd258a7767
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852337"
---
# <a name="detecting-platform-capabilities"></a>检测平台功能

MRTK 的一个常见问题涉及了解 (特定设备，例如Microsoft HoloLens 2) 运行应用程序。 确定确切的硬件在不同平台上可能很有挑战性。 相反，MRTK 提供了在运行时识别特定功能的方法， (例如，当前设备终结点是否支持手部) 。

## <a name="capabilities"></a>功能

混合现实工具包提供 枚举，该枚举定义应用程序可在运行时查询的一组 [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) 功能。

### <a name="input-system-capabilities"></a>输入系统功能

默认 MRTK 输入系统支持查询以下功能：

| 功能 | 说明 |
|---|---|
| HandHand | 表达手部输入 |
| EyeTracking | 眼睛凝视目标 |
| GGVHand | 凝视手势-语音手部输入 |
| MotionController | 运动控制器输入 |
| VoiceCommand | 使用应用定义的关键字的语音命令 |
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
