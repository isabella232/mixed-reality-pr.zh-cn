---
title: 邻近感应
description: 有关 MRTK 中示例的邻近感应的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 6e57a76d54d0f3f63ce8dcb80582e178effa39d9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176385"
---
# <a name="proximity-light"></a>邻近感应

[`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight)是一个[Fluent Design System](https://www.microsoft.com/design/fluent/)模式，它模拟悬停在对象表面附近的 "渐变反点光"。 应用程序通常用于接近交互，应用程序可以通过组件控制近程灯光的属性 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 。

对于受 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) *混合现实影响 Toolkit* 的材料，必须使用/标准着色器，并且必须启用 *近程光* 属性。

> [!NOTE]
> [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight)默认情况下支持最多两个。

## <a name="examples"></a>示例

MRTK 内的大多数场景都利用 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 。 最常见的用例可在 MRTK/SDK/Features/UX/Prototyping/cursor/FingerCursor prefab 中找到。

## <a name="advanced-usage"></a>高级用法

默认情况下， [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 每次只能将两个 [材料](https://docs.unity3d.com/ScriptReference/Material.html) 照亮一次。 如果项目需要两个以上的 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 内容来影响 [材料](https://docs.unity3d.com/ScriptReference/Material.html) ，下面的示例代码演示如何实现此目的。

> [!NOTE]
> 有很多 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 光线[](https://docs.unity3d.com/ScriptReference/Material.html)会增加像素着色器指令，并会影响性能。 请在项目中分析这些更改。

*如何将可用的数量 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 从两个增加到四个。*

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#define PROXIMITY_LIGHT_COUNT 2

// to:

#define PROXIMITY_LIGHT_COUNT 4

// 2) Within MRTK/Core/Utilities/StandardShader/ProximityLight.cs change:

private const int proximityLightCount = 2;

// to:

private const int proximityLightCount = 4;
```

> [!NOTE]
> 如果 Unity 记录类似于下面的警告，则必须重启 Unity，然后更改才能生效。
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a>另请参阅

* [MRTK 标准着色器](mrtk-standard-shader.md)
