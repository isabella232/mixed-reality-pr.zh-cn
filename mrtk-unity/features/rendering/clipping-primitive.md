---
title: 剪辑基元
description: 有关在 MRTK 中包含示例的剪辑基元的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，剪切基元，
ms.openlocfilehash: c3331084f87ccc57208426910d84ed7bef457bc1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176741"
---
# <a name="clipping-primitive"></a><span data-ttu-id="e80f8-104">剪辑基元</span><span class="sxs-lookup"><span data-stu-id="e80f8-104">Clipping primitive</span></span>

<span data-ttu-id="e80f8-105">这些 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 行为允许使用 MRTK 着色器来指定要在 [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox))  (基元的哪一侧与着色器结合使用，从而实现高性能、和形状剪辑。</span><span class="sxs-lookup"><span data-stu-id="e80f8-105">The [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors allow for performant [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) shape clipping with the ability to specify which side of the primitive to clip against (inside or outside) when used with MRTK shaders.</span></span>

![基元剪辑 gizmos](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> <span data-ttu-id="e80f8-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 在着色器中利用 [剪裁/放弃](https://developer.download.nvidia.com/cg/clip.html) 说明，并禁止 Unity 批量裁剪呈现器的功能。</span><span class="sxs-lookup"><span data-stu-id="e80f8-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) utilize [clip/discard](https://developer.download.nvidia.com/cg/clip.html) instructions within shaders and disable Unity's ability to batch clipped renderers.</span></span> <span data-ttu-id="e80f8-108">利用剪辑基元时，请考虑这些性能问题。</span><span class="sxs-lookup"><span data-stu-id="e80f8-108">Take these performance implications in mind when utilizing clipping primitives.</span></span>

<span data-ttu-id="e80f8-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane)、 [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) 和 [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 可用于轻松控制剪辑基元属性。</span><span class="sxs-lookup"><span data-stu-id="e80f8-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) can be used to easily control clipping primitive properties.</span></span> <span data-ttu-id="e80f8-110">将这些组件与以下着色器结合使用，以利用剪辑方案。</span><span class="sxs-lookup"><span data-stu-id="e80f8-110">Use these components with the following shaders to leverage clipping scenarios.</span></span>

- <span data-ttu-id="e80f8-111">*混合现实 Toolkit/标准*</span><span class="sxs-lookup"><span data-stu-id="e80f8-111">*Mixed Reality Toolkit/Standard*</span></span>
- <span data-ttu-id="e80f8-112">*混合现实 Toolkit/TextMeshPro*</span><span class="sxs-lookup"><span data-stu-id="e80f8-112">*Mixed Reality Toolkit/TextMeshPro*</span></span>
- <span data-ttu-id="e80f8-113">*混合现实 Toolkit/Text3DShader*</span><span class="sxs-lookup"><span data-stu-id="e80f8-113">*Mixed Reality Toolkit/Text3DShader*</span></span>

## <a name="examples"></a><span data-ttu-id="e80f8-114">示例</span><span class="sxs-lookup"><span data-stu-id="e80f8-114">Examples</span></span>

<span data-ttu-id="e80f8-115">**ClippingExamples** 和 **MaterialGallery** 场景演示了行为的使用情况 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) ，可在以下位置找到： MRTK/示例/演示/StandardShader/场景/</span><span class="sxs-lookup"><span data-stu-id="e80f8-115">The **ClippingExamples** and **MaterialGallery** scenes demonstrate usage of the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="e80f8-116">高级用法</span><span class="sxs-lookup"><span data-stu-id="e80f8-116">Advanced Usage</span></span>

<span data-ttu-id="e80f8-117">默认情况下， [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 一次只能剪裁一个 [呈现](https://docs.unity3d.com/ScriptReference/Renderer.html) 器。</span><span class="sxs-lookup"><span data-stu-id="e80f8-117">By default only one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) can clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) at a time.</span></span> <span data-ttu-id="e80f8-118">如果你的项目需要多个 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 来影响 [呈现](https://docs.unity3d.com/ScriptReference/Renderer.html)  器，下面的示例代码演示如何实现此目的。</span><span class="sxs-lookup"><span data-stu-id="e80f8-118">If your project requires more than one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) to influence a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html)  the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="e80f8-119">具有多个 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 剪辑 [呈现](https://docs.unity3d.com/ScriptReference/Renderer.html) 器将增加像素着色器指令，并将影响性能。</span><span class="sxs-lookup"><span data-stu-id="e80f8-119">Having multiple [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="e80f8-120">请在项目中分析这些更改。</span><span class="sxs-lookup"><span data-stu-id="e80f8-120">Please profile these changes within your project.</span></span>

<span data-ttu-id="e80f8-121">*如何将两个不同 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 的剪辑作为一个呈现方式。例如，同时 [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) ：*</span><span class="sxs-lookup"><span data-stu-id="e80f8-121">*How to have two different [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example a [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) and [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> <span data-ttu-id="e80f8-122">上述更改将产生额外的着色器编译时间。</span><span class="sxs-lookup"><span data-stu-id="e80f8-122">The above change will incur additional shader compilation time.</span></span>

<span data-ttu-id="e80f8-123">*如何将两个相同的 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 剪辑作为一个呈现。例如，同时提供两个 [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) ：*</span><span class="sxs-lookup"><span data-stu-id="e80f8-123">*How to have two of the same [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example two [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

```C#
// 1) Add the below MonoBehaviour to your project:

[ExecuteInEditMode]
public class SecondClippingBox : ClippingBox
{
    /// <inheritdoc />
    protected override string Keyword
    {
        get { return "_CLIPPING_BOX2"; }
    }

    /// <inheritdoc />
    protected override string ClippingSideProperty
    {
        get { return "_ClipBoxSide2"; }
    }

    /// <inheritdoc />
    protected override void Initialize()
    {
        base.Initialize();

        clipBoxSizeID = Shader.PropertyToID("_ClipBoxSize2");
        clipBoxInverseTransformID = Shader.PropertyToID("_ClipBoxInverseTransform2");
    }
}

// 2) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) add the following multi_compile pragma:

#pragma multi_compile _ _CLIPPING_BOX2

// 3) In the same shader change:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX)

// to:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX) || defined(_CLIPPING_BOX2)

// 4) In the same shader add the following shader variables:

#if defined(_CLIPPING_BOX2)
    fixed _ClipBoxSide2;
    float4 _ClipBoxSize2;
    float4x4 _ClipBoxInverseTransform2;
#endif

// 5) In the same shader change:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif

// to:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif
#if defined(_CLIPPING_BOX2)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize2.xyz, _ClipBoxInverseTransform2) * _ClipBoxSide2);
#endif
```

<span data-ttu-id="e80f8-124">最后，将 [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 和 SecondClippingBox 组件添加到场景，并为两个框指定相同的呈现器。</span><span class="sxs-lookup"><span data-stu-id="e80f8-124">Finally, add a [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) and SecondClippingBox component to your scene and specify the same renderer for both boxes.</span></span> <span data-ttu-id="e80f8-125">呈现器现在应同时被两个框同时剪切。</span><span class="sxs-lookup"><span data-stu-id="e80f8-125">The renderer should now be clipped by both boxes simultaneously.</span></span>

## <a name="see-also"></a><span data-ttu-id="e80f8-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e80f8-126">See also</span></span>

- [<span data-ttu-id="e80f8-127">MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="e80f8-127">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
