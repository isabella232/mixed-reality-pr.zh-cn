---
title: 悬停灯
description: 有关 MRTK 中具有示例的 HoverLight 的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 悬停光，
ms.openlocfilehash: ed45d3345931376283cfca2372ac57459c777f6e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176728"
---
# <a name="hover-light"></a><span data-ttu-id="bf1f2-104">悬停灯</span><span class="sxs-lookup"><span data-stu-id="bf1f2-104">Hover light</span></span>

<span data-ttu-id="bf1f2-105">是 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 一[种Fluent Design System](https://www.microsoft.com/design/fluent/)范例，它模拟在对象表面附近[](https://docs.unity3d.com/Manual/Lighting.html)悬停的点光。</span><span class="sxs-lookup"><span data-stu-id="bf1f2-105">A [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a [point light](https://docs.unity3d.com/Manual/Lighting.html) hovering near the surface of an object.</span></span> <span data-ttu-id="bf1f2-106">通常用于远地交互，应用程序可以通过 组件控制悬停灯 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 的属性。</span><span class="sxs-lookup"><span data-stu-id="bf1f2-106">Often used for far away interactions, the application can control the properties of a Hover Light via the [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) component.</span></span>

<span data-ttu-id="bf1f2-107">对于受混合现实环境/标准着色器Toolkit材料，必须启用 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) *悬* 停光属性。 </span><span class="sxs-lookup"><span data-stu-id="bf1f2-107">For a material to be influenced by a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Hover Light* property must be enabled.</span></span>

> [!Note]
> <span data-ttu-id="bf1f2-108">默认情况下，MRTK/标准着色器最多支持两个，但会缩放以支持四个，然后支持 10 个，因为向场景中添加了更多 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 光。</span><span class="sxs-lookup"><span data-stu-id="bf1f2-108">The MRTK/Standard shader supports up to two [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) by default, but will scale to support four and then ten as more lights are added to the scene.</span></span>

## <a name="examples"></a><span data-ttu-id="bf1f2-109">示例</span><span class="sxs-lookup"><span data-stu-id="bf1f2-109">Examples</span></span>

<span data-ttu-id="bf1f2-110">MRTK 中的大多数场景都使用 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 。</span><span class="sxs-lookup"><span data-stu-id="bf1f2-110">Most scenes within the MRTK utilize a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight).</span></span> <span data-ttu-id="bf1f2-111">可以在 MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab 上找到最常见的用例</span><span class="sxs-lookup"><span data-stu-id="bf1f2-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab</span></span>

<span data-ttu-id="bf1f2-112">**HoverLightExamples** 场景还演示了行为的用法，可在 [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) MRTK/Examples/Demos/StandardShader/Scene/</span><span class="sxs-lookup"><span data-stu-id="bf1f2-112">The **HoverLightExamples** scene also demonstrates usage of [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="bf1f2-113">高级用法</span><span class="sxs-lookup"><span data-stu-id="bf1f2-113">Advanced Usage</span></span>

<span data-ttu-id="bf1f2-114">一次 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 只能有[](https://docs.unity3d.com/ScriptReference/Material.html)10 个材料进行照明。</span><span class="sxs-lookup"><span data-stu-id="bf1f2-114">Only ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="bf1f2-115">如果项目需要超过 10 个才能影响材料，下面的示例代码 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 将演示如何实现此目的。 [](https://docs.unity3d.com/ScriptReference/Material.html)</span><span class="sxs-lookup"><span data-stu-id="bf1f2-115">If your project requires more than ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!Note]
> <span data-ttu-id="bf1f2-116">材料 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 进行多次 [着色会增加](https://docs.unity3d.com/ScriptReference/Material.html) 像素着色器指令，并会影响性能。</span><span class="sxs-lookup"><span data-stu-id="bf1f2-116">Having many [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="bf1f2-117">**请在项目中分析这些更改。**</span><span class="sxs-lookup"><span data-stu-id="bf1f2-117">**Please profile these changes within your project.**</span></span>

<span data-ttu-id="bf1f2-118">*如何将可用数量从 10 [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) 个增加至 12 个。*</span><span class="sxs-lookup"><span data-stu-id="bf1f2-118">*How to increase the number of available [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) from ten to twelve.*</span></span>

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
> <span data-ttu-id="bf1f2-119">如果 Unity 记录如下所示的警告，则必须重启 Unity，更改才能生效。</span><span class="sxs-lookup"><span data-stu-id="bf1f2-119">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a><span data-ttu-id="bf1f2-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf1f2-120">See also</span></span>

* [<span data-ttu-id="bf1f2-121">MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="bf1f2-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
