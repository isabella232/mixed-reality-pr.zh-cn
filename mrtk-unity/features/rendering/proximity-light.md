---
title: 邻近感应灯
description: 有关 MRTK 中示例的邻近感应的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 1adf4d1d70313c917d63224b91a14d995d1888c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145007"
---
# <a name="proximity-light"></a><span data-ttu-id="cdc30-104">邻近感应灯</span><span class="sxs-lookup"><span data-stu-id="cdc30-104">Proximity Light</span></span>

<span data-ttu-id="cdc30-105">[`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight)是一个[熟知的设计系统](https://www.microsoft.com/design/fluent/)模式，它模拟悬停在对象表面附近的 "渐变反点光"。</span><span class="sxs-lookup"><span data-stu-id="cdc30-105">A [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a "gradient inverse point light" hovering near the surface of an object.</span></span> <span data-ttu-id="cdc30-106">应用程序通常用于接近交互，应用程序可以通过组件控制近程灯光的属性 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 。</span><span class="sxs-lookup"><span data-stu-id="cdc30-106">Often used for near interactions, the application can control the properties of a Proximity Light via the [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) component.</span></span>

<span data-ttu-id="cdc30-107">若要使需要受 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) *混合现实工具包/标准* 着色器 *影响的材料* ，必须启用该属性。</span><span class="sxs-lookup"><span data-stu-id="cdc30-107">For a material to be influenced by a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Proximity Light* property must be enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="cdc30-108">[`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight)默认情况下支持最多两个。</span><span class="sxs-lookup"><span data-stu-id="cdc30-108">Up to two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) are supported by default.</span></span>

## <a name="examples"></a><span data-ttu-id="cdc30-109">示例</span><span class="sxs-lookup"><span data-stu-id="cdc30-109">Examples</span></span>

<span data-ttu-id="cdc30-110">MRTK 内的大多数场景都利用 [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 。</span><span class="sxs-lookup"><span data-stu-id="cdc30-110">Most scenes within the MRTK utilize a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight).</span></span> <span data-ttu-id="cdc30-111">最常见的用例可在 MRTK/SDK/Features/UX/Prototyping/cursor/FingerCursor prefab 中找到。</span><span class="sxs-lookup"><span data-stu-id="cdc30-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="cdc30-112">高级用法</span><span class="sxs-lookup"><span data-stu-id="cdc30-112">Advanced Usage</span></span>

<span data-ttu-id="cdc30-113">默认情况下， [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 每次只能将两个 [材料](https://docs.unity3d.com/ScriptReference/Material.html) 照亮一次。</span><span class="sxs-lookup"><span data-stu-id="cdc30-113">By default only two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="cdc30-114">如果项目需要两个以上的 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 内容来影响 [材料](https://docs.unity3d.com/ScriptReference/Material.html) ，下面的示例代码演示如何实现此目的。</span><span class="sxs-lookup"><span data-stu-id="cdc30-114">If your project requires more than two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="cdc30-115">有很多 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 光线[](https://docs.unity3d.com/ScriptReference/Material.html)会增加像素着色器指令，并会影响性能。</span><span class="sxs-lookup"><span data-stu-id="cdc30-115">Having many [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="cdc30-116">请在项目中分析这些更改。</span><span class="sxs-lookup"><span data-stu-id="cdc30-116">Please profile these changes within your project.</span></span>

<span data-ttu-id="cdc30-117">*如何将可用的数量 [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) 从两个增加到四个。*</span><span class="sxs-lookup"><span data-stu-id="cdc30-117">*How to increase the number of available [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) from two to four.*</span></span>

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
> <span data-ttu-id="cdc30-118">如果 Unity 记录类似于下面的警告，则必须重启 Unity，然后更改才能生效。</span><span class="sxs-lookup"><span data-stu-id="cdc30-118">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a><span data-ttu-id="cdc30-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cdc30-119">See also</span></span>

* [<span data-ttu-id="cdc30-120">MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="cdc30-120">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
