---
title: 邻近感应灯
description: MRTK 中具有示例的邻近光文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 1be58cd22228258d51f63b2a4db0294bceaec1320640ecbbfa2795edde5e39bd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208317"
---
# <a name="proximity-light"></a>邻近感应灯

是 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 一[种Fluent Design System](https://www.microsoft.com/design/fluent/)范例，它模拟在对象表面附近悬停的"渐变反点光"。 通常用于近距交互，应用程序可以通过 组件控制邻近光 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 的属性。

对于受混合现实应用/标准着色器Toolkit材料，必须启用 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) *邻近* 光属性。 

> [!NOTE]
> 默认情况下最多 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 支持两个 。

## <a name="examples"></a>示例

MRTK 中的大多数场景都使用 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 。 可以在 MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab 上找到最常见的用例

## <a name="advanced-usage"></a>高级用法

默认情况下，一 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 次只有两 [个材料](https://docs.unity3d.com/ScriptReference/Material.html) 可以亮起。 如果项目需要两个以上才能影响 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) [材料，](https://docs.unity3d.com/ScriptReference/Material.html) 下面的示例代码将演示如何实现此目的。

> [!NOTE]
> 材料 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 进行多次 [着色会增加](https://docs.unity3d.com/ScriptReference/Material.html) 像素着色器指令，并会影响性能。 请在项目中分析这些更改。

*如何将可用数量从 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 2 增加至 4。*

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
> 如果 Unity 记录如下所示的警告，则必须重启 Unity，更改才能生效。
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a>另请参阅

* [MRTK 标准着色器](mrtk-standard-shader.md)
