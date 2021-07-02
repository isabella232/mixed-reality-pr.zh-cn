---
title: 输入动画文件格式
description: MRTK 中有关输入动画二进制文件格式规范的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 400212d80833f5d8dfbb3c5265c755ed2e127131
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177007"
---
# <a name="input-animation-file-format"></a>输入动画文件格式

## <a name="overall-structure"></a>整体结构

输入动画二进制文件以64位整数幻数开头。 此数字在十六进制表示法中的值为 `0x6a8faf6e0f9e42c6` ，并且可用于标识有效的输入动画文件。

接下来的八个字节是声明文件的主版本号和次版本号的两个 Int32 值。

文件的其余部分由动画数据占用，动画数据在版本号之间可能会更改。

| 部分 | 类型 |
|---------|------|
| 幻数 | Int64 |
| 主要版本号 | Int32 |
| 次版本号 | Int32 |
| 动画数据 | _请参阅版本部分_ |

## <a name="version-11"></a>版本 1.1

输入动画数据由三个布尔值组成，这些布尔值指示动画是否包含相机、手和眼睛数据，后跟一系列动画曲线。 曲线存在取决于这些布尔值的值。 每条曲线可以有不同数量的关键帧。

| 部分 | 类型 | 说明 |
|---------|------|------|
| 具有照相机姿势 | 布尔 | |
| 具有手写数据 | 布尔 | |
| 有眼睛| 布尔 | |
| 照相机 | [姿势曲线](#pose-curves) | 仅当具有照相机姿势时 |
| 手动跟踪 | [布尔曲线](#boolean-curve) | 仅当有手写数据为 true 时 |
| 手动跟踪权限 | [布尔曲线](#boolean-curve) | 仅当有手写数据为 true 时 |
| 左收缩 | [布尔曲线](#boolean-curve) | 仅当有手写数据为 true 时 |
| 手动收缩权限 | [布尔曲线](#boolean-curve) | 仅当有手写数据为 true 时 |
| 手动接头靠左 | [接合曲线](#joint-pose-curves) | 仅当有手写数据为 true 时 |
| 右侧接头 | [接合曲线](#joint-pose-curves) | 仅当有手写数据为 true 时 |
| 眼睛 | [射线曲线](#ray-curves)] | 仅当有眼睛为 true 时 |

## <a name="version-10"></a>版本 1.0

输入动画数据由一系列动画曲线组成。 动画曲线的数量和含义是固定的，但是每条曲线可以有不同数量的关键帧。

| 部分 | 类型 |
|---------|------|
| 照相机 | [姿势曲线](#pose-curves) |
| 手动跟踪 | [布尔曲线](#boolean-curve) |
| 手动跟踪权限 | [布尔曲线](#boolean-curve) |
| 左收缩 | [布尔曲线](#boolean-curve) |
| 手动收缩权限 | [布尔曲线](#boolean-curve) |
| 手动接头靠左 | [接合曲线](#joint-pose-curves) |
| 右侧接头 | [接合曲线](#joint-pose-curves) |

### <a name="joint-pose-curves"></a>接合曲线

每个局都存储一系列接点动画曲线。 联接的数目是固定的，为每个接合存储一组姿势曲线。

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
| 索引提示 | [姿势曲线](#pose-curves) |
| MiddleMetacarpal | [姿势曲线](#pose-curves) |
| MiddleKnuckle | [姿势曲线](#pose-curves) |
| MiddleMiddleJoint | [姿势曲线](#pose-curves) |
| MiddleDistalJoint | [姿势曲线](#pose-curves) |
| 中间提示 | [姿势曲线](#pose-curves) |
| RingMetacarpal | [姿势曲线](#pose-curves) |
| RingKnuckle | [姿势曲线](#pose-curves) |
| RingMiddleJoint | [姿势曲线](#pose-curves) |
| RingDistalJoint | [姿势曲线](#pose-curves) |
| 环提示 | [姿势曲线](#pose-curves) |
| PinkyMetacarpal | [姿势曲线](#pose-curves) |
| UckyKnuckle | [姿势曲线](#pose-curves) |
| PinkyMiddleJoint | [姿势曲线](#pose-curves) |
| PinkyDistalJoint | [姿势曲线](#pose-curves) |
| 浅色提示 | [姿势曲线](#pose-curves) |

### <a name="pose-curves"></a>姿势曲线

姿势曲线是位置向量的 3 条动画曲线序列，后跟 4 条旋转四元数的动画曲线。

| 部分 | 类型 |
|---------|------|
| 位置 X | [浮点曲线](#float-curve) |
| 位置 Y | [浮点曲线](#float-curve) |
| 位置 Z | [浮点曲线](#float-curve) |
| 旋转 X | [浮点曲线](#float-curve) |
| 旋转 Y | [浮点曲线](#float-curve) |
| 旋转 Z | [浮点曲线](#float-curve) |
| 旋转 W | [浮点曲线](#float-curve) |

### <a name="ray-curves"></a>光线曲线

射线曲线是原向量的 3 条动画曲线序列，后跟方向向量的 3 条动画曲线。

| 部分 | 类型 |
|---------|------|
| 源 X | [浮点曲线](#float-curve) |
| 源 Y | [浮点曲线](#float-curve) |
| 源 Z | [浮点曲线](#float-curve) |
| 方向 X | [浮点曲线](#float-curve) |
| 方向 Y | [浮点曲线](#float-curve) |
| 方向 Z | [浮点曲线](#float-curve) |

### <a name="float-curve"></a>浮点曲线

浮点曲线是完全成熟的 Bézier 曲线，具有可变数量的关键帧。 每个关键帧都存储时间和曲线值，以及每个关键帧左侧和右侧之间的切线和权重。

| 部分 | 类型 |
|---------|------|
| 预包装模式 | Int32， [包装模式](#wrap-mode) |
| 后包装模式 | Int32， [包装模式](#wrap-mode) |
| 关键帧数 | Int32 |
| 关键帧 | [Float 关键帧](#float-keyframe) |

### <a name="float-keyframe"></a>Float 关键帧

float 关键帧将切值和权重值与基本时间和值一起存储。

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

布尔曲线是开/关值的简单序列。 每个关键帧上的曲线值会立即翻转。

| 部分 | 类型 |
|---------|------|
| 预包装模式 | Int32， [包装模式](#wrap-mode) |
| 后包装模式 | Int32， [包装模式](#wrap-mode) |
| 关键帧数 | Int32 |
| 关键帧 | [布尔关键帧](#boolean-keyframe) |

### <a name="boolean-keyframe"></a>布尔关键帧

布尔关键帧仅存储时间和值。

| 部分 | 类型 |
|---------|------|
| 时间 | Float32 |
| 值 | Float32 |

### <a name="wrap-mode"></a>换行模式

预换模式和后包装模式的语义遵循 [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) 定义。 它们是以下位的组合：

| 值 | 含义 |
|-------|---------|
| 0 | 默认值：读取设置更高的默认重复模式。 |
| 1 | 一次：当时间到达动画剪辑的末尾时，该剪辑将自动停止播放，时间将重置为剪辑的开头。 |
| 2 | 循环：当时间到达动画剪辑的末尾时，时间将在开始时继续。 |
| 4 | PingPong：当时间到达动画剪辑的末尾时，时间将在开头和结尾之间 ping 回。 |
| 8 | ClampForever：播放动画。 当它到达末尾时，它将持续播放最后一帧，并且永远不会停止播放。 |

### <a name="weighted-mode"></a>加权模式

加权模式的语义遵循 [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) 定义。

| 值 | 含义 |
|-------|---------|
| 0 | 无：计算曲线段时，排除 inWeight 或 outWeight。 |
| 1 | In：计算上一条曲线段时包括 inWeight。 |
| 2 | Out：计算下一个曲线段时包括 outWeight。 |
| 3 | 两者：计算曲线段时包括 inWeight 和 outWeight。 |
