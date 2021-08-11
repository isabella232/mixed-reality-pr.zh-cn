---
title: 输入动画文件格式
description: 有关 MRTK 中的输入动画二进制文件格式规范的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: bf77d976c9c894e6cf455a3a6b0e0c538912af2a9e8f8e2c7e847ba6e4657140
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115222759"
---
# <a name="input-animation-file-format"></a>输入动画文件格式

## <a name="overall-structure"></a>整体结构

输入动画二进制文件以 64 位整数幻数开头。 此数字的十六进制表示法值为 ， `0x6a8faf6e0f9e42c6` 可用于标识有效的输入动画文件。

接下来的八个字节是两个 Int32 值，它们声明文件的主要版本号和次要版本号。

文件的其余部分由动画数据处理，这些数据可能在版本号之间更改。

| 部分 | 类型 |
|---------|------|
| 幻数 | Int64 |
| 主版本号 | Int32 |
| 次要版本号 | Int32 |
| 动画数据 | _请参阅版本部分_ |

## <a name="version-11"></a>版本 1.1

输入动画数据由三个布尔值组成，这些值指示动画是否包含 Camera、Hand 和 Eye Gaze 数据，后跟一系列动画曲线。 所呈现的曲线取决于这些布尔值的值。 每个曲线可以有不同的关键帧数。

| 部分 | 类型 | 说明 |
|---------|------|------|
| 具有相机姿势 | 布尔 | |
| 具有手部数据 | 布尔 | |
| 有眼睛凝视| 布尔 | |
| 照相机 | [姿势曲线](#pose-curves) | 仅在"具有相机姿势"为 true 时 |
| 手动跟踪左侧 | [布尔曲线](#boolean-curve) | 仅在"具有手部数据"为 true 时 |
| 手部跟踪右侧 | [布尔曲线](#boolean-curve) | 仅在"具有手部数据"为 true 时 |
| 向左收缩手部 | [布尔曲线](#boolean-curve) | 仅在"具有手部数据"为 true 时 |
| 右手收缩 | [布尔曲线](#boolean-curve) | 仅在"具有手部数据"为 true 时 |
| 左手部 | [联合姿势曲线](#joint-pose-curves) | 仅在"具有手部数据"为 true 时 |
| 手部右侧 | [联合姿势曲线](#joint-pose-curves) | 仅在"具有手部数据"为 true 时 |
| 眼睛凝视 | [光线曲线](#ray-curves)] | 仅在"有眼睛凝视"为 true 时 |

## <a name="version-10"></a>版本 1.0

输入动画数据由一系列动画曲线组成。 动画曲线的数量和含义是固定的，但每个曲线可以有不同的关键帧数。

| 部分 | 类型 |
|---------|------|
| 照相机 | [姿势曲线](#pose-curves) |
| 手动跟踪左侧 | [布尔曲线](#boolean-curve) |
| 手部跟踪右侧 | [布尔曲线](#boolean-curve) |
| 向左收缩手部 | [布尔曲线](#boolean-curve) |
| 右手收缩 | [布尔曲线](#boolean-curve) |
| 左手部 | [联合姿势曲线](#joint-pose-curves) |
| 手部右侧 | [联合姿势曲线](#joint-pose-curves) |

### <a name="joint-pose-curves"></a>联合姿势曲线

每手都存储一系列联合动画曲线。 联合数是固定的，并存储每个联合的一组姿势曲线。

| 部分 | 类型 |
|---------|------|
| 无 | [姿势曲线](#pose-curves) |
| 手腕 | [姿势曲线](#pose-curves) |
| Palm | [姿势曲线](#pose-curves) |
| ThumbMetacarpalJoint | [姿势曲线](#pose-curves) |
| ThumbProximalJoint | [姿势曲线](#pose-curves) |
| ThumbDistalJoint | [姿势曲线](#pose-curves) |
| ThumbTip | [姿势曲线](#pose-curves) |
| IndexMetacarpal | [姿势曲线](#pose-curves) |
| IndexKnuckle | [姿势曲线](#pose-curves) |
| IndexMiddleJoint | [姿势曲线](#pose-curves) |
| IndexDistalJoint | [姿势曲线](#pose-curves) |
| IndexTip | [姿势曲线](#pose-curves) |
| MiddleMetacarpal | [姿势曲线](#pose-curves) |
| MiddleKnuckle | [姿势曲线](#pose-curves) |
| MiddleMiddleJoint | [姿势曲线](#pose-curves) |
| MiddleDistalJoint | [姿势曲线](#pose-curves) |
| MiddleTip | [姿势曲线](#pose-curves) |
| RingMetacarpal | [姿势曲线](#pose-curves) |
| RingKnuckle | [姿势曲线](#pose-curves) |
| RingMiddleJoint | [姿势曲线](#pose-curves) |
| RingDistalJoint | [姿势曲线](#pose-curves) |
| RingTip | [姿势曲线](#pose-curves) |
| PinkyMetacarpal | [姿势曲线](#pose-curves) |
| PinkyKnuckle | [姿势曲线](#pose-curves) |
| PinkyMiddleJoint | [姿势曲线](#pose-curves) |
| PinkyDistalJoint | [姿势曲线](#pose-curves) |
| PinkyTip | [姿势曲线](#pose-curves) |

### <a name="pose-curves"></a>姿势曲线

姿势曲线是位置向量的3个动画曲线的序列，后跟旋转四元数的4个动画曲线。

| 部分 | 类型 |
|---------|------|
| 位置 X | [浮点曲线](#float-curve) |
| 位置 Y | [浮点曲线](#float-curve) |
| Z 轴位置 | [浮点曲线](#float-curve) |
| 旋转 X | [浮点曲线](#float-curve) |
| 旋转 Y | [浮点曲线](#float-curve) |
| 旋转 Z | [浮点曲线](#float-curve) |
| 旋转 W | [浮点曲线](#float-curve) |

### <a name="ray-curves"></a>射线曲线

Ray 曲线是原点向量的3个动画曲线的序列，后跟方向向量的3个动画曲线。

| 部分 | 类型 |
|---------|------|
| 原点 X | [浮点曲线](#float-curve) |
| 源 Y | [浮点曲线](#float-curve) |
| 原点 Z | [浮点曲线](#float-curve) |
| 方向 X | [浮点曲线](#float-curve) |
| 方向 Y | [浮点曲线](#float-curve) |
| Z 方向 | [浮点曲线](#float-curve) |

### <a name="float-curve"></a>浮点曲线

浮点曲线是使用可变数量的关键帧的完全成熟的贝塞尔曲线。 每个关键帧在每个关键帧的左侧和右侧存储时间和曲线值以及切线和权重。

| 部分 | 类型 |
|---------|------|
| 预包装模式 | Int32， [环绕模式](#wrap-mode) |
| 包装后模式 | Int32， [环绕模式](#wrap-mode) |
| 关键帧数量 | Int32 |
| 关键帧 | [浮点关键帧](#float-keyframe) |

### <a name="float-keyframe"></a>浮点关键帧

浮点型关键帧将相切和权重值与基本时间和值一起存储。

| 部分 | 类型 |
|---------|------|
| 时间 | Float32 |
| 值 | Float32 |
| InTangent | Float32 |
| OutTangent | Float32 |
| InWeight | Float32 |
| OutWeight | Float32 |
| WeightedMode | Int32， [加权模式](#weighted-mode) |

### <a name="boolean-curve"></a>布尔曲线

布尔曲线是开启/关闭值的简单序列。 在每个关键帧上，曲线的值会立即反转。

| 部分 | 类型 |
|---------|------|
| 预包装模式 | Int32， [环绕模式](#wrap-mode) |
| 包装后模式 | Int32， [环绕模式](#wrap-mode) |
| 关键帧数量 | Int32 |
| 关键帧 | [布尔关键帧](#boolean-keyframe) |

### <a name="boolean-keyframe"></a>布尔关键帧

布尔关键帧仅存储时间和值。

| 部分 | 类型 |
|---------|------|
| 时间 | Float32 |
| 值 | Float32 |

### <a name="wrap-mode"></a>环绕模式

前后换行模式的语义遵循 [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) 定义。 它们是以下位的组合：

| 值 | 含义 |
|-------|---------|
| 0 | 默认值：读取设置较高的默认重复模式。 |
| 1 | 一次：当时间到达动画剪辑的末尾时，剪辑会自动停止播放，时间将重置为剪辑的开始位置。 |
| 2 | 循环：当时间到达动画剪辑的末尾时，将在开始时继续进行。 |
| 4 | PingPong：当时间到达动画剪辑的末尾时，将在开始和结束之间 ping 回来。 |
| 8 | ClampForever：播放动画。 当它到达末尾时，它将一直播放最后一帧，而永远不会停止播放。 |

### <a name="weighted-mode"></a>加权模式

加权模式的语义遵循 [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) 定义。

| 值 | 含义 |
|-------|---------|
| 0 | None：在计算曲线段时不包括 inWeight 或 outWeight。 |
| 1 | In：计算上一曲线段时，包括 inWeight。 |
| 2 | Out：计算下一曲线段时包括 outWeight。 |
| 3 | 两者：在计算曲线段时，包括 inWeight 和 outWeight。 |
