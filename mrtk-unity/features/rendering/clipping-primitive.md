---
title: 剪辑基元
description: 有关在 MRTK 中具有示例的剪辑基元的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 剪辑基元，
ms.openlocfilehash: 35b7166045986df34eaf2c23161efc6379160ead
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145208"
---
# <a name="clipping-primitive"></a><span data-ttu-id="dafbb-104">剪辑基元</span><span class="sxs-lookup"><span data-stu-id="dafbb-104">Clipping Primitive</span></span>

<span data-ttu-id="dafbb-105">当与 MRTK 着色器一起使用时，行为允许执行性能、、 和形状剪辑，从而指定要针对 (内或) 剪裁基元的哪 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 一侧。</span><span class="sxs-lookup"><span data-stu-id="dafbb-105">The [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors allow for performant [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) shape clipping with the ability to specify which side of the primitive to clip against (inside or outside) when used with MRTK shaders.</span></span>

![基元剪辑 gizmos](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> <span data-ttu-id="dafbb-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 利用 [着色器中的剪辑/](https://developer.download.nvidia.com/cg/clip.html) 放弃指令，并禁用 Unity 批处理剪辑呈现器的能力。</span><span class="sxs-lookup"><span data-stu-id="dafbb-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) utilize [clip/discard](https://developer.download.nvidia.com/cg/clip.html) instructions within shaders and disable Unity's ability to batch clipped renderers.</span></span> <span data-ttu-id="dafbb-108">使用剪辑基元时，请注意这些性能影响。</span><span class="sxs-lookup"><span data-stu-id="dafbb-108">Take these performance implications in mind when utilizing clipping primitives.</span></span>

<span data-ttu-id="dafbb-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane)、 [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 和 可用于轻松控制剪辑基元属性。</span><span class="sxs-lookup"><span data-stu-id="dafbb-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) can be used to easily control clipping primitive properties.</span></span> <span data-ttu-id="dafbb-110">将这些组件与以下着色器一起用于利用剪辑方案。</span><span class="sxs-lookup"><span data-stu-id="dafbb-110">Use these components with the following shaders to leverage clipping scenarios.</span></span>

- <span data-ttu-id="dafbb-111">*混合现实工具包/标准*</span><span class="sxs-lookup"><span data-stu-id="dafbb-111">*Mixed Reality Toolkit/Standard*</span></span>
- <span data-ttu-id="dafbb-112">*混合现实工具包/TextMeshPro*</span><span class="sxs-lookup"><span data-stu-id="dafbb-112">*Mixed Reality Toolkit/TextMeshPro*</span></span>
- <span data-ttu-id="dafbb-113">*混合现实工具包/Text3DShader*</span><span class="sxs-lookup"><span data-stu-id="dafbb-113">*Mixed Reality Toolkit/Text3DShader*</span></span>

## <a name="examples"></a><span data-ttu-id="dafbb-114">示例</span><span class="sxs-lookup"><span data-stu-id="dafbb-114">Examples</span></span>

<span data-ttu-id="dafbb-115">**ClippingExamples 和** **MaterialGallery** 场景演示了行为的用法，可在 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) MRTK/Examples/Demos/StandardShader/Scenes/</span><span class="sxs-lookup"><span data-stu-id="dafbb-115">The **ClippingExamples** and **MaterialGallery** scenes demonstrate usage of the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="dafbb-116">高级用法</span><span class="sxs-lookup"><span data-stu-id="dafbb-116">Advanced Usage</span></span>

<span data-ttu-id="dafbb-117">默认情况下，一 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 次只能剪辑 [一个](https://docs.unity3d.com/ScriptReference/Renderer.html) 呈现器。</span><span class="sxs-lookup"><span data-stu-id="dafbb-117">By default only one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) can clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) at a time.</span></span> <span data-ttu-id="dafbb-118">如果项目需要多个来影响呈现 [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [器，下面的示例](https://docs.unity3d.com/ScriptReference/Renderer.html)  代码将演示如何实现此目的。</span><span class="sxs-lookup"><span data-stu-id="dafbb-118">If your project requires more than one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) to influence a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html)  the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="dafbb-119">呈现 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 器具有多个 [剪辑会增加](https://docs.unity3d.com/ScriptReference/Renderer.html) 像素着色器指令，并会影响性能。</span><span class="sxs-lookup"><span data-stu-id="dafbb-119">Having multiple [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="dafbb-120">请在项目中分析这些更改。</span><span class="sxs-lookup"><span data-stu-id="dafbb-120">Please profile these changes within your project.</span></span>

<span data-ttu-id="dafbb-121">*如何让两个不同的 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 剪辑呈现。例如， [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) 和 [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 同时：*</span><span class="sxs-lookup"><span data-stu-id="dafbb-121">*How to have two different [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example a [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) and [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> <span data-ttu-id="dafbb-122">上述更改将产生额外的着色器编译时间。</span><span class="sxs-lookup"><span data-stu-id="dafbb-122">The above change will incur additional shader compilation time.</span></span>

<span data-ttu-id="dafbb-123">*如何让两个同一 [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) 剪辑呈现。例如， [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 同时有两个：*</span><span class="sxs-lookup"><span data-stu-id="dafbb-123">*How to have two of the same [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example two [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

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

<span data-ttu-id="dafbb-124">最后，将 [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) 和 SecondClippingBox 组件添加到场景中，并同时为两个框指定相同的呈现器。</span><span class="sxs-lookup"><span data-stu-id="dafbb-124">Finally, add a [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) and SecondClippingBox component to your scene and specify the same renderer for both boxes.</span></span> <span data-ttu-id="dafbb-125">现在，两个框应同时剪辑呈现器。</span><span class="sxs-lookup"><span data-stu-id="dafbb-125">The renderer should now be clipped by both boxes simultaneously.</span></span>

## <a name="see-also"></a><span data-ttu-id="dafbb-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dafbb-126">See also</span></span>

- [<span data-ttu-id="dafbb-127">MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="dafbb-127">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
