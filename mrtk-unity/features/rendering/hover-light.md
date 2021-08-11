---
title: 悬停灯光
description: 有关 MRTK 中具有示例的 HoverLight 的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 悬停光，
ms.openlocfilehash: 948a0772cd2fad667984d8d5507664e4346a507e84b03c873eccf8d3f1e66532
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198579"
---
# <a name="hover-light"></a>悬停灯光

是 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 一[种Fluent Design System](https://www.microsoft.com/design/fluent/)范例，它模拟在对象表面附近[](https://docs.unity3d.com/Manual/Lighting.html)悬停的点光。 通常用于远地交互，应用程序可以通过 组件控制悬停灯 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 的属性。

对于受混合现实环境/标准着色器Toolkit材料，必须启用 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) *悬* 停光属性。 

> [!Note]
> 默认情况下，MRTK/标准着色器最多支持两个，但会缩放以支持四个，然后支持 10 个，因为向场景中添加了更多 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 光。

## <a name="examples"></a>示例

MRTK 中的大多数场景都使用 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 。 可以在 MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab 上找到最常见的用例

**HoverLightExamples** 场景还演示了行为的用法，可在 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) MRTK/Examples/Demos/StandardShader/Scene/

## <a name="advanced-usage"></a>高级用法

一次 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 只能有[](https://docs.unity3d.com/ScriptReference/Material.html)10 个材料进行照明。 如果项目需要超过 10 个才能影响材料，下面的示例代码 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 将演示如何实现此目的。 [](https://docs.unity3d.com/ScriptReference/Material.html)

> [!Note]
> 材料 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 进行多次 [着色会增加](https://docs.unity3d.com/ScriptReference/Material.html) 像素着色器指令，并会影响性能。 **请在项目中分析这些更改。**

*如何将可用数量从 10 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 个增加至 12 个。*

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 10

// to:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 12

// 2) Within MRTK/Core/Utilities/StandardShader/HoverLight.cs change:

private const int hoverLightCountHigh = 10;

// to:

private const int hoverLightCountHigh = 12;
```

> [!NOTE]
> 如果 Unity 记录如下所示的警告，则必须重启 Unity，更改才能生效。
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a>另请参阅

* [MRTK 标准着色器](mrtk-standard-shader.md)
