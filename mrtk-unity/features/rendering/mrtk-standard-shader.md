---
title: MRTK 标准着色器
description: MRTKStandardShader 的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 材料着色器
ms.openlocfilehash: 8b570ebb023305cecbeca16b32832417a3f57cce
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145109"
---
# <a name="mrtk-standard-shader"></a><span data-ttu-id="d032e-104">MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="d032e-104">MRTK Standard Shader</span></span>

![标准着色器示例](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)

<span data-ttu-id="d032e-106">MRTK 标准着色系统利用单个灵活的着色器，该着色器可以实现类似于 Unity 标准着色器、实现 [Fluent Design System](https://www.microsoft.com/design/fluent/) 原则的视觉对象，并可在混合现实设备上保持性能。</span><span class="sxs-lookup"><span data-stu-id="d032e-106">MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implement [Fluent Design System](https://www.microsoft.com/design/fluent/) principles, and remain performant on mixed reality devices.</span></span>

## <a name="example-scenes"></a><span data-ttu-id="d032e-107">示例场景</span><span class="sxs-lookup"><span data-stu-id="d032e-107">Example scenes</span></span>

<span data-ttu-id="d032e-108">可以在 下的 **MaterialGallery** 场景中找到着色器材料示例 `MRTK/Examples/Demos/StandardShader/Scenes/` 。</span><span class="sxs-lookup"><span data-stu-id="d032e-108">You can find the shader material examples in the **MaterialGallery** scene under `MRTK/Examples/Demos/StandardShader/Scenes/`.</span></span> <span data-ttu-id="d032e-109">此场景中的所有材料都使用 MRTK/标准着色器。</span><span class="sxs-lookup"><span data-stu-id="d032e-109">All materials in this scene are using the MRTK/Standard shader.</span></span>

![材料库](../images/mrtk-standard-shader/MRTK_MaterialGallery.jpg)

<span data-ttu-id="d032e-111">可以在 下的 **StandardMaterialComparison** 场景中找到比较场景，以针对 Unity/标准着色器示例比较和测试 MRTK/Standard 着色器 `MRTK/Examples/Demos/StandardShader/Scenes/` 。</span><span class="sxs-lookup"><span data-stu-id="d032e-111">You can find a comparison scene to compare and test the MRTK/Standard shader against the Unity/Standard shader example in the **StandardMaterialComparison** scene under `MRTK/Examples/Demos/StandardShader/Scenes/`.</span></span>

![材料比较](../images/mrtk-standard-shader/MRTK_StandardMaterialComparison.gif)

## <a name="architecture"></a><span data-ttu-id="d032e-113">体系结构</span><span class="sxs-lookup"><span data-stu-id="d032e-113">Architecture</span></span>

<span data-ttu-id="d032e-114">MRTK/标准着色系统是一种"uber 着色器"，它使用 Unity 的着色器程序 [变体](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) 功能基于材料属性自动生成最佳着色器代码。</span><span class="sxs-lookup"><span data-stu-id="d032e-114">The MRTK/Standard shading system is an "uber shader" that uses [Unity's shader program variant feature](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) to auto-generate optimal shader code based on material properties.</span></span> <span data-ttu-id="d032e-115">当用户在材料检查器中选择材料属性时，他们只会对已启用的功能产生性能成本。</span><span class="sxs-lookup"><span data-stu-id="d032e-115">When a user selects material properties in the material inspector, they only incur performance cost for features they have enabled.</span></span>

## <a name="material-inspector"></a><span data-ttu-id="d032e-116">材料检查器</span><span class="sxs-lookup"><span data-stu-id="d032e-116">Material inspector</span></span>

<span data-ttu-id="d032e-117">对于名为 的 MRTK/标准着色器，存在自定义材料检查器 [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI) 。</span><span class="sxs-lookup"><span data-stu-id="d032e-117">A custom material inspector exists for the MRTK/Standard shader called [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI).</span></span> <span data-ttu-id="d032e-118">检查器根据用户选择自动启用/禁用着色器功能，并有助于设置呈现状态。</span><span class="sxs-lookup"><span data-stu-id="d032e-118">The inspector automatically enables/disables shader features, based on user selection and aides in setting up render state.</span></span> <span data-ttu-id="d032e-119">有关每项功能的信息，请将鼠标悬停在 Unity 编辑器中每个属性 **上，获取工具提示。**</span><span class="sxs-lookup"><span data-stu-id="d032e-119">For more information about each feature **please hover over each property in the Unity Editor for a tooltip.**</span></span>

![材料检查器](../images/mrtk-standard-shader/MRTK_MaterialInspector.jpg)

<span data-ttu-id="d032e-121">检查器的第一部分控制材料的呈现状态。</span><span class="sxs-lookup"><span data-stu-id="d032e-121">The first portion of the inspector controls the material's render state.</span></span> <span data-ttu-id="d032e-122">*呈现模式* 确定何时以及如何呈现材料。</span><span class="sxs-lookup"><span data-stu-id="d032e-122">*Rendering Mode* determines when and how a material will be rendered.</span></span> <span data-ttu-id="d032e-123">MRTK/标准着色器的目标是镜像 [Unity/标准](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html)着色器 中的呈现模式。</span><span class="sxs-lookup"><span data-stu-id="d032e-123">The aim of the MRTK/Standard shader is to mirror the [rendering modes found in the Unity/Standard shader](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html).</span></span> <span data-ttu-id="d032e-124">MRTK/标准着色器还包括加法呈现模式和 *自定义呈现模式*，用于完成用户控制。</span><span class="sxs-lookup"><span data-stu-id="d032e-124">The MRTK/Standard shader also includes an *Additive* rendering mode and *Custom* rendering mode for complete user control.</span></span>

| <span data-ttu-id="d032e-125">呈现模式</span><span class="sxs-lookup"><span data-stu-id="d032e-125">Rendering Mode</span></span> |         <span data-ttu-id="d032e-126">说明</span><span class="sxs-lookup"><span data-stu-id="d032e-126">Description</span></span>                                                       |
|----------------|---------------------------------------------------------------------------|
| <span data-ttu-id="d032e-127">半透明</span><span class="sxs-lookup"><span data-stu-id="d032e-127">Opaque</span></span>         | <span data-ttu-id="d032e-128"> (默认) 适用于没有透明区域的普通实体对象。</span><span class="sxs-lookup"><span data-stu-id="d032e-128">(Default) Suitable for normal solid objects with no transparent areas.</span></span>    |
| <span data-ttu-id="d032e-129">剪影</span><span class="sxs-lookup"><span data-stu-id="d032e-129">Cutout</span></span>         | <span data-ttu-id="d032e-130">允许创建在不透明和透明区域之间具有硬边缘的透明效果。</span><span class="sxs-lookup"><span data-stu-id="d032e-130">Allows creation of transparent effects that have hard edges between the opaque and transparent areas.</span></span> <span data-ttu-id="d032e-131">在此模式下，没有半透明区域，纹理为100% 不透明或不可见。</span><span class="sxs-lookup"><span data-stu-id="d032e-131">In this mode, there are no semi-transparent areas, the texture is either 100% opaque, or invisible.</span></span> <span data-ttu-id="d032e-132">当使用透明度创建材料形状（如 vegetation）时，这非常有用。</span><span class="sxs-lookup"><span data-stu-id="d032e-132">This is useful when using transparency to create the shape of materials, such as vegetation.</span></span> |
| <span data-ttu-id="d032e-133">淡化</span><span class="sxs-lookup"><span data-stu-id="d032e-133">Fade</span></span>           | <span data-ttu-id="d032e-134">允许透明度值完全淡化对象，包括任何镜面高光或反射。</span><span class="sxs-lookup"><span data-stu-id="d032e-134">Allows the transparency values to entirely fade an object out, including any specular highlights or reflections it may have.</span></span> <span data-ttu-id="d032e-135">如果要使对象的动画淡入或淡出，此模式非常有用。它不适合呈现清晰的透明材料（如清晰的塑料或玻璃），因为反射和高光还会淡出。</span><span class="sxs-lookup"><span data-stu-id="d032e-135">This mode is useful if you want to animate an object fading in or out. It is not suitable for rendering realistic transparent materials such as clear plastic or glass because the reflections and highlights will also be faded out.</span></span> |
| <span data-ttu-id="d032e-136">透明</span><span class="sxs-lookup"><span data-stu-id="d032e-136">Transparent</span></span>    | <span data-ttu-id="d032e-137">适用于渲染真实的透明材料，如清晰的塑料或玻璃。</span><span class="sxs-lookup"><span data-stu-id="d032e-137">Suitable for rendering realistic transparent materials such as clear plastic or glass.</span></span> <span data-ttu-id="d032e-138">在此模式下，材料本身将根据纹理的 alpha 通道和颜色颜色) 的 alpha (来使用透明度值。</span><span class="sxs-lookup"><span data-stu-id="d032e-138">In this mode, the material itself will take on transparency values (based on the texture’s alpha channel and the alpha of the tint colour).</span></span> <span data-ttu-id="d032e-139">但是，反射和照明突出显示内容将在完全清晰的情况下保持可见，就像实际透明材料一样。</span><span class="sxs-lookup"><span data-stu-id="d032e-139">However, reflections and lighting highlights will remain visible at full clarity as is the case with real transparent materials.</span></span> |
| <span data-ttu-id="d032e-140">加法</span><span class="sxs-lookup"><span data-stu-id="d032e-140">Additive</span></span>       | <span data-ttu-id="d032e-141">启用一种加法混合模式，该模式将以前的像素颜色与当前像素颜色进行求和。</span><span class="sxs-lookup"><span data-stu-id="d032e-141">Enables an additive blending mode, which sums the previous pixel color with the current pixel color.</span></span> <span data-ttu-id="d032e-142">这是用于避免透明度排序问题的首选透明模式。</span><span class="sxs-lookup"><span data-stu-id="d032e-142">This is the preferred transparency mode to avoid transparency sorting issues.</span></span>     |
| <span data-ttu-id="d032e-143">自定义</span><span class="sxs-lookup"><span data-stu-id="d032e-143">Custom</span></span>         | <span data-ttu-id="d032e-144">允许手动控制呈现模式的每个方面。</span><span class="sxs-lookup"><span data-stu-id="d032e-144">Allows for every aspect of the rendering mode to be controlled manually.</span></span> <span data-ttu-id="d032e-145">仅适用于高级用途。</span><span class="sxs-lookup"><span data-stu-id="d032e-145">For advanced usage only.</span></span>   |

![呈现模式](../images/mrtk-standard-shader/MRTK_RenderingModes.jpg)

| <span data-ttu-id="d032e-147">精选模式</span><span class="sxs-lookup"><span data-stu-id="d032e-147">Cull Mode</span></span> |             <span data-ttu-id="d032e-148">说明</span><span class="sxs-lookup"><span data-stu-id="d032e-148">Description</span></span>                                                                                                                                                                       |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d032e-149">关</span><span class="sxs-lookup"><span data-stu-id="d032e-149">Off</span></span>       | <span data-ttu-id="d032e-150">禁用面部剔除。</span><span class="sxs-lookup"><span data-stu-id="d032e-150">Disables face culling.</span></span> <span data-ttu-id="d032e-151">如果需要双面网格，则只能将剔除设置为 Off。</span><span class="sxs-lookup"><span data-stu-id="d032e-151">Culling should only be set to Off when a two sided mesh is required.</span></span>                                                                                        |
| <span data-ttu-id="d032e-152">Front</span><span class="sxs-lookup"><span data-stu-id="d032e-152">Front</span></span>     | <span data-ttu-id="d032e-153">启用正面剔除。</span><span class="sxs-lookup"><span data-stu-id="d032e-153">Enables front face culling.</span></span>                                                                                                                                                        |
| <span data-ttu-id="d032e-154">返回</span><span class="sxs-lookup"><span data-stu-id="d032e-154">Back</span></span>      | <span data-ttu-id="d032e-155"> (默认) 启用 [后退人脸剔除](https://en.wikipedia.org/wiki/Back-face_culling)。</span><span class="sxs-lookup"><span data-stu-id="d032e-155">(Default) Enables [back face culling](https://en.wikipedia.org/wiki/Back-face_culling).</span></span> <span data-ttu-id="d032e-156">应尽可能经常启用背面剔除以提高呈现性能。</span><span class="sxs-lookup"><span data-stu-id="d032e-156">Back face culling should be enabled as often as possible to improve rendering performance.</span></span> |

## <a name="performance"></a><span data-ttu-id="d032e-157">性能</span><span class="sxs-lookup"><span data-stu-id="d032e-157">Performance</span></span>

<span data-ttu-id="d032e-158">在 Unity 标准着色器上使用 MRTK 标准着色器的主要优势之一是性能。</span><span class="sxs-lookup"><span data-stu-id="d032e-158">One of the primary advantages to using the MRTK Standard shader over the Unity standard shader is performance.</span></span> <span data-ttu-id="d032e-159">MRTK 标准着色器可扩展，仅利用启用的功能。</span><span class="sxs-lookup"><span data-stu-id="d032e-159">The MRTK Standard Shader is extensible to only utilize the features enabled.</span></span> <span data-ttu-id="d032e-160">但是，还编写 MRTK 标准着色器，以提供与 Unity 标准着色器相当的美观效果，但成本要低得多。</span><span class="sxs-lookup"><span data-stu-id="d032e-160">However, the MRTK Standard shader has also been written to deliver comparable aesthetic results as the Unity Standard shader, but at a much lower cost.</span></span> <span data-ttu-id="d032e-161">比较着色器性能的一种简单方法是通过需要在 GPU 上执行的操作数。</span><span class="sxs-lookup"><span data-stu-id="d032e-161">One simple way to compare shader performance is via the number of operations that needs to be performed on the GPU.</span></span> <span data-ttu-id="d032e-162">当然，计算量可能会因启用的功能和其他呈现配置而波动。</span><span class="sxs-lookup"><span data-stu-id="d032e-162">Of course, the magnitude of calculations may fluctuate by features enabled and other rendering configurations.</span></span> <span data-ttu-id="d032e-163">但一般情况下，MRTK 标准着色器执行的计算比 Unity 标准着色器要少得多。</span><span class="sxs-lookup"><span data-stu-id="d032e-163">But, in general, the MRTK Standard shader performs significantly less computation than the Unity Standard shader.</span></span>

<span data-ttu-id="d032e-164">Unity 标准着色器统计信息示例</span><span class="sxs-lookup"><span data-stu-id="d032e-164">Unity Standard shader statistics example</span></span>

![Unity 标准着色器统计信息](../images/performance/UnityStandardShader-Stats.PNG)

<span data-ttu-id="d032e-166">MRTK 标准着色器统计信息示例</span><span class="sxs-lookup"><span data-stu-id="d032e-166">MRTK Standard shader statistics example</span></span>

![MRTK 标准着色器统计信息](../images/performance/MRTKStandardShader-Stats.PNG)

> [!NOTE]
> <span data-ttu-id="d032e-168">可以通过在 Unity 检查器中选择和查看 [](https://docs.unity3d.com/Manual/class-Shader.html)着色器资产，然后单击"编译和显示代码"按钮来 *生成* 这些结果。</span><span class="sxs-lookup"><span data-stu-id="d032e-168">These results can be generated by selecting and viewing a [shader asset](https://docs.unity3d.com/Manual/class-Shader.html) in the Unity inspector, then clicking the *Compile and show code* button.</span></span>

## <a name="lighting"></a><span data-ttu-id="d032e-169">照明</span><span class="sxs-lookup"><span data-stu-id="d032e-169">Lighting</span></span>

<span data-ttu-id="d032e-170">MRTK/Standard 对照明使用简单的近似值。</span><span class="sxs-lookup"><span data-stu-id="d032e-170">The MRTK/Standard uses a simple approximation for lighting.</span></span> <span data-ttu-id="d032e-171">由于此着色器不会计算物理正确性和能量消耗，因此它可以快速高效地呈现。</span><span class="sxs-lookup"><span data-stu-id="d032e-171">Because this shader does not calculate for physical correctness and energy conservation, it renders quickly and efficiently.</span></span> <span data-ttu-id="d032e-172">Blinn-Phong是主要照明技术，与 Fresnel 和基于图像的照明混合，以近似基于物理的照明。</span><span class="sxs-lookup"><span data-stu-id="d032e-172">Blinn-Phong is the primary lighting technique which is blended with Fresnel and image-based lighting to approximate physically-based lighting.</span></span> <span data-ttu-id="d032e-173">着色器支持以下照明技术：</span><span class="sxs-lookup"><span data-stu-id="d032e-173">The shader supports the following lighting techniques:</span></span>

### <a name="directional-light"></a><span data-ttu-id="d032e-174">定向光</span><span class="sxs-lookup"><span data-stu-id="d032e-174">Directional light</span></span>

<span data-ttu-id="d032e-175">如果启用，着色器将遵守场景中第一个 Unity 方向光的方向、颜色和 (强度) 。</span><span class="sxs-lookup"><span data-stu-id="d032e-175">The shader will respect the direction, color, and intensity of the first Unity Directional Light in the scene (if enabled).</span></span> <span data-ttu-id="d032e-176">动态点光、点光或其他任何 Unity 光不会在实时照明中考虑。</span><span class="sxs-lookup"><span data-stu-id="d032e-176">Dynamic point lights, spot lights, or any other Unity light will not be considered in real time lighting.</span></span>

### <a name="spherical-harmonics"></a><span data-ttu-id="d032e-177">球状球状</span><span class="sxs-lookup"><span data-stu-id="d032e-177">Spherical harmonics</span></span>

<span data-ttu-id="d032e-178">着色器使用 [球状谐波](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html)（如果已启用），将使用光源探测来估算场景中的灯。</span><span class="sxs-lookup"><span data-stu-id="d032e-178">The shader will use Light Probes to approximate lights in the scene using [Spherical Harmonics](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html), if enabled.</span></span> <span data-ttu-id="d032e-179">球形谐波计算按顶点执行以降低计算成本。</span><span class="sxs-lookup"><span data-stu-id="d032e-179">Spherical harmonics calculations are performed per vertex to reduce calculation cost.</span></span>

### <a name="lightmapping"></a><span data-ttu-id="d032e-180">Lightmapping</span><span class="sxs-lookup"><span data-stu-id="d032e-180">Lightmapping</span></span>

<span data-ttu-id="d032e-181">对于静态照明，着色器将遵循由 Unity 的 [Lightmapping 系统](https://docs.unity3d.com/Manual/Lightmapping.html)生成的 lightmaps。</span><span class="sxs-lookup"><span data-stu-id="d032e-181">For static lighting, the shader will respect lightmaps built by Unity's [Lightmapping system](https://docs.unity3d.com/Manual/Lightmapping.html).</span></span> <span data-ttu-id="d032e-182">只需将呈现器标记为 static (或 lightmap static) 才能使用 lightmaps。</span><span class="sxs-lookup"><span data-stu-id="d032e-182">Simply mark the renderer as static (or lightmap static) to use lightmaps.</span></span>

### <a name="hover-light"></a><span data-ttu-id="d032e-183">悬停灯光</span><span class="sxs-lookup"><span data-stu-id="d032e-183">Hover light</span></span>

* <span data-ttu-id="d032e-184">请参阅 [悬停灯光](hover-light.md)</span><span class="sxs-lookup"><span data-stu-id="d032e-184">See [Hover Light](hover-light.md)</span></span>

### <a name="proximity-light"></a><span data-ttu-id="d032e-185">邻近感应</span><span class="sxs-lookup"><span data-stu-id="d032e-185">Proximity light</span></span>

* <span data-ttu-id="d032e-186">查看 [邻近感应](proximity-light.md)</span><span class="sxs-lookup"><span data-stu-id="d032e-186">See [Proximity Light](proximity-light.md)</span></span>

## <a name="lightweight-scriptable-render-pipeline-support"></a><span data-ttu-id="d032e-187">轻型可编写脚本呈现管道支持</span><span class="sxs-lookup"><span data-stu-id="d032e-187">Lightweight Scriptable Render Pipeline support</span></span>

<span data-ttu-id="d032e-188">MRTK 包含一个升级路径，使开发人员能够使用 MRTK 着色器 (LWRP) 使用 Unity 的轻型可编写脚本呈现管道。</span><span class="sxs-lookup"><span data-stu-id="d032e-188">The MRTK contains an upgrade path to allow developers to utilize Unity's Lightweight Scriptable Render Pipeline (LWRP) with MRTK shaders.</span></span> <span data-ttu-id="d032e-189">在 Unity 2019.1.1 f1 和轻型 RP 5.7.2 包中进行了测试。</span><span class="sxs-lookup"><span data-stu-id="d032e-189">Tested in Unity 2019.1.1f1 and Lightweight RP 5.7.2 package.</span></span> <span data-ttu-id="d032e-190">有关 LWRP 入门的说明，请参阅 [此页](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html)。</span><span class="sxs-lookup"><span data-stu-id="d032e-190">or instructions on getting started with the LWRP, see [this page](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html).</span></span>

<span data-ttu-id="d032e-191">若要执行 MRTK 升级，请选择： **混合现实工具包-> 实用程序-> UPGRADE MRTK Standard 着色器**</span><span class="sxs-lookup"><span data-stu-id="d032e-191">To perform the MRTK upgrade, select: **Mixed Reality Toolkit -> Utilities -> Upgrade MRTK Standard Shader for Lightweight Render Pipeline**</span></span>

![lwrp 升级](../images/mrtk-standard-shader/MRTK_LWRPUpgrade.jpg)

<span data-ttu-id="d032e-193">升级完成后，MRTK/Standard 着色器将被更改，并且任何洋红色 (着色器错误) 材料应修复。</span><span class="sxs-lookup"><span data-stu-id="d032e-193">After the upgrade occurs, the MRTK/Standard shader will be altered and any magenta (shader error) materials should be fixed.</span></span> <span data-ttu-id="d032e-194">若要验证升级是否成功，请查看：**升级资产/MixedRealityToolkit/StandardAssets/着色器/MixedRealityStandard 用于轻量渲染管道** 的控制台。</span><span class="sxs-lookup"><span data-stu-id="d032e-194">To verify the upgrade successfully occurred, check the console for: **Upgraded Assets/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader for use with the Lightweight Render Pipeline.**</span></span>

## <a name="ugui-support"></a><span data-ttu-id="d032e-195">UGUI 支持</span><span class="sxs-lookup"><span data-stu-id="d032e-195">UGUI support</span></span>

<span data-ttu-id="d032e-196">MRTK 标准着色系统与 Unity 内置的 [UI 系统](https://docs.unity3d.com/Manual/UISystem.html)一起工作。</span><span class="sxs-lookup"><span data-stu-id="d032e-196">The MRTK Standard shading system works with Unity's built in [UI system](https://docs.unity3d.com/Manual/UISystem.html).</span></span> <span data-ttu-id="d032e-197">在 Unity UI 组件上，unity_ObjectToWorld 矩阵不是图形组件所在的本地转换的转换矩阵，而是它的父画布的转换矩阵。</span><span class="sxs-lookup"><span data-stu-id="d032e-197">On Unity UI components, the unity_ObjectToWorld matrix is not the transformation matrix of the local transform the Graphic component lives on but that of its parent Canvas.</span></span> <span data-ttu-id="d032e-198">许多 MRTK/标准着色器效果都需要了解对象规模。</span><span class="sxs-lookup"><span data-stu-id="d032e-198">Many MRTK/Standard shader effects require object scale to be known.</span></span> <span data-ttu-id="d032e-199">若要解决此问题， 将在 UI 网格构造期间将缩放信息存储 [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) 到 UV 通道属性中。</span><span class="sxs-lookup"><span data-stu-id="d032e-199">To solve this issue, the [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) will store scaling information into UV channel attributes during UI mesh construction.</span></span>

<span data-ttu-id="d032e-200">请注意，使用 Unity 图像组件时，建议为源图像指定"无 (子画面) "，以防止 Unity UI 生成额外的顶点。</span><span class="sxs-lookup"><span data-stu-id="d032e-200">Note, when using a Unity Image component, it is recommended to specify "None (Sprite)" for the Source Image to prevent Unity UI from generating extra vertices.</span></span>

<span data-ttu-id="d032e-201">当需要时，MRTK 中的画布将提示添加 [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) ：</span><span class="sxs-lookup"><span data-stu-id="d032e-201">A Canvas within the MRTK will prompt for the addition of a [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) when one is required:</span></span>

![缩放网格效果](../images/mrtk-standard-shader/MRTK_ScaleMeshEffect.jpg)

## <a name="texture-combiner"></a><span data-ttu-id="d032e-203">纹理合并器</span><span class="sxs-lookup"><span data-stu-id="d032e-203">Texture combiner</span></span>

<span data-ttu-id="d032e-204">若要提高与 Unity Standard 着色器每像素金属的奇偶校验，可通过通道封装 控制平滑度、半透明性和遮 [挡性值](http://wiki.polycount.com/wiki/ChannelPacking)。</span><span class="sxs-lookup"><span data-stu-id="d032e-204">To improve parity with the Unity Standard shader per pixel metallic, smoothness, emissive, and occlusion values can all be controlled via [channel packing](http://wiki.polycount.com/wiki/ChannelPacking).</span></span> <span data-ttu-id="d032e-205">例如：</span><span class="sxs-lookup"><span data-stu-id="d032e-205">For example:</span></span>

![通道映射示例](../images/mrtk-standard-shader/MRTK_ChannelMap.gif)

<span data-ttu-id="d032e-207">使用通道打包时，只需对一个纹理采样并加载到内存中，而不是四个单独的纹理。</span><span class="sxs-lookup"><span data-stu-id="d032e-207">When you use channel packing, you only have to sample and load one texture into memory instead of four separate ones.</span></span> <span data-ttu-id="d032e-208">在 Program 或 Photoshop 等程序中编写纹理贴图时，可以手动打包它们，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d032e-208">When you write your texture maps in a program like Substance or Photoshop, you can hand pack them like the following:</span></span>

| <span data-ttu-id="d032e-209">通道</span><span class="sxs-lookup"><span data-stu-id="d032e-209">Channel</span></span> | <span data-ttu-id="d032e-210">属性</span><span class="sxs-lookup"><span data-stu-id="d032e-210">Property</span></span>             |
|---------|----------------------|
| <span data-ttu-id="d032e-211">Red</span><span class="sxs-lookup"><span data-stu-id="d032e-211">Red</span></span>     | <span data-ttu-id="d032e-212">金属</span><span class="sxs-lookup"><span data-stu-id="d032e-212">Metallic</span></span>             |
| <span data-ttu-id="d032e-213">绿色</span><span class="sxs-lookup"><span data-stu-id="d032e-213">Green</span></span>   | <span data-ttu-id="d032e-214">封闭</span><span class="sxs-lookup"><span data-stu-id="d032e-214">Occlusion</span></span>            |
| <span data-ttu-id="d032e-215">蓝色</span><span class="sxs-lookup"><span data-stu-id="d032e-215">Blue</span></span>    | <span data-ttu-id="d032e-216">灰 (辐射) </span><span class="sxs-lookup"><span data-stu-id="d032e-216">Emission (Greyscale)</span></span> |
| <span data-ttu-id="d032e-217">Alpha</span><span class="sxs-lookup"><span data-stu-id="d032e-217">Alpha</span></span>   | <span data-ttu-id="d032e-218">平滑</span><span class="sxs-lookup"><span data-stu-id="d032e-218">Smoothness</span></span>           |

<span data-ttu-id="d032e-219">或者，可以使用 MRTK 纹理合并器工具。</span><span class="sxs-lookup"><span data-stu-id="d032e-219">Or, you can use the MRTK Texture Combiner Tool.</span></span> <span data-ttu-id="d032e-220">若要打开该工具，请选择：混合现实工具包 **-> 实用工具 ->纹理** 合并器，这将打开以下窗口：</span><span class="sxs-lookup"><span data-stu-id="d032e-220">To open the tool, select: **Mixed Reality Toolkit -> Utilities -> Texture Combiner** which will open the below window:</span></span>

![纹理合并器示例](../images/mrtk-standard-shader/MRTK_TextureCombiner.jpg)

<span data-ttu-id="d032e-222">可以通过选择 Unity 标准着色器并单击"从标准材料自动填充"来自动填充此窗口。</span><span class="sxs-lookup"><span data-stu-id="d032e-222">This window can be automatically filled out by selecting a Unity Standard shader and clicking "Autopopulate from Standard Material."</span></span> <span data-ttu-id="d032e-223">或者，可以为每个红色、 (、蓝色) alpha 通道手动指定纹理值或常数值。</span><span class="sxs-lookup"><span data-stu-id="d032e-223">Or, you can manually specify a texture (or constant value) per red, green, blue, or alpha channel.</span></span> <span data-ttu-id="d032e-224">纹理组合是 GPU 加速的，不需要输入纹理可供 CPU 访问。</span><span class="sxs-lookup"><span data-stu-id="d032e-224">The texture combination is GPU accelerated and does not require the input texture to be CPU accessible.</span></span>

## <a name="additional-feature-documentation"></a><span data-ttu-id="d032e-225">其他功能文档</span><span class="sxs-lookup"><span data-stu-id="d032e-225">Additional feature documentation</span></span>

<span data-ttu-id="d032e-226">下面是 MRTK/Standard 着色器提供的一些功能详细信息的额外详细信息。</span><span class="sxs-lookup"><span data-stu-id="d032e-226">Below are extra details on a handful of feature details available with the MRTK/Standard shader.</span></span>

### <a name="primitive-clipping"></a><span data-ttu-id="d032e-227">基元剪辑</span><span class="sxs-lookup"><span data-stu-id="d032e-227">Primitive clipping</span></span>

![基元剪辑](../images/mrtk-standard-shader/MRTK_PrimitiveClipping.gif)

* <span data-ttu-id="d032e-229">请参阅 [剪辑基元](clipping-primitive.md)</span><span class="sxs-lookup"><span data-stu-id="d032e-229">See [Clipping Primitive](clipping-primitive.md)</span></span>

### <a name="mesh-outlines"></a><span data-ttu-id="d032e-230">网格轮廓</span><span class="sxs-lookup"><span data-stu-id="d032e-230">Mesh outlines</span></span>

<span data-ttu-id="d032e-231">许多网格大纲技术均使用 [post 处理](https://docs.unity3d.com/Manual/PostProcessingOverview.html) 技术完成。</span><span class="sxs-lookup"><span data-stu-id="d032e-231">Many mesh outline techniques are done using a [post processing](https://docs.unity3d.com/Manual/PostProcessingOverview.html) technique.</span></span> <span data-ttu-id="d032e-232">Post 处理提供了很好的大纲，但在许多混合现实设备上可能会占用大量资源。</span><span class="sxs-lookup"><span data-stu-id="d032e-232">Post processing provides great quality outlines, but can be prohibitively expensive on many Mixed Reality devices.</span></span> <span data-ttu-id="d032e-233">可以在下的  **OutlineExamples** 场景中找到演示网格轮廓用法的场景 `MRTK/Examples/Demos/StandardShader/Scenes/` 。</span><span class="sxs-lookup"><span data-stu-id="d032e-233">You can find a scene that demonstrates usage of mesh outlines in the  **OutlineExamples** scene under `MRTK/Examples/Demos/StandardShader/Scenes/`.</span></span>

<img src="../images/mrtk-standard-shader/MRTK_MeshOutline.jpg" width="900" alt="Mesh Outline">

<span data-ttu-id="d032e-234">[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) 和 [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) 可用于呈现围绕网格呈现器的轮廓。</span><span class="sxs-lookup"><span data-stu-id="d032e-234">[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) and [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) can be used to render an outline around a mesh renderer.</span></span> <span data-ttu-id="d032e-235">启用此组件会引入所述对象的其他呈现处理过程，但设计用于在移动混合现实设备上运行之前，而不使用任何 post 过程。</span><span class="sxs-lookup"><span data-stu-id="d032e-235">Enabling this component introduces an additional render pass of the object being outlined, but is designed to run performantly on mobile Mixed Reality devices and does not utilize any post processes.</span></span> <span data-ttu-id="d032e-236">这种效果的限制包括它不能很好地处理不是 (watertight 的对象，也不需要是两面) 并且在重叠对象上可能会出现深度排序问题。</span><span class="sxs-lookup"><span data-stu-id="d032e-236">Limitations of this effect include it not working well on objects which are not watertight (or required to be two sided) and depth sorting issues can occur on overlapping objects.</span></span>

<span data-ttu-id="d032e-237">大纲行为设计为与 MRTK/Standard 着色器结合使用。</span><span class="sxs-lookup"><span data-stu-id="d032e-237">The outline behaviors are designed to be used in conjunction with the MRTK/Standard shader.</span></span> <span data-ttu-id="d032e-238">大纲材料通常是一种可靠的 unlit 颜色，但可以配置为实现范围很大的效果。</span><span class="sxs-lookup"><span data-stu-id="d032e-238">Outline materials are usually a solid unlit color, but can be configured to achieve a wide array of effects.</span></span> <span data-ttu-id="d032e-239">大纲材料的默认配置如下所示：</span><span class="sxs-lookup"><span data-stu-id="d032e-239">The default configuration of a outline material is as follows:</span></span>

<img src="../images/mrtk-standard-shader/MRTK_OutlineMaterial.jpg" width="450" alt="Mesh Outline Material">

1. <span data-ttu-id="d032e-240">深度写入-应禁用轮廓材料，以确保轮廓不会阻止其他对象呈现。</span><span class="sxs-lookup"><span data-stu-id="d032e-240">Depth Write - should be disabled for outline materials to make sure the outline does not prevent other objects from rendering.</span></span>
2. <span data-ttu-id="d032e-241">顶点延伸-需要启用才能呈现轮廓。</span><span class="sxs-lookup"><span data-stu-id="d032e-241">Vertex Extrusion - needs to be enabled to render the outline.</span></span>
3. <span data-ttu-id="d032e-242">使用平滑法线-对于某些网格，此设置是可选的。</span><span class="sxs-lookup"><span data-stu-id="d032e-242">Use Smooth Normals - this setting is optional for some meshes.</span></span> <span data-ttu-id="d032e-243">在沿顶点法线移动顶点时进行延伸，某些网格沿默认的法线凸出会导致中断。</span><span class="sxs-lookup"><span data-stu-id="d032e-243">Extrusion occurs by moving a vertex along a vertex normal, on some meshes extruding along the default normals will cause discontinuities in the outline.</span></span> <span data-ttu-id="d032e-244">若要修复这些中断，可以选中此框，以使用由生成的另一组平滑法 [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)</span><span class="sxs-lookup"><span data-stu-id="d032e-244">To fix these discontinuities, you can check this box to use another set of smoothed normals which get generated by [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)</span></span>

<span data-ttu-id="d032e-245">[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) 是一个组件，可用于在网格上自动生成平滑的法线。</span><span class="sxs-lookup"><span data-stu-id="d032e-245">[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) is a component which can be used to automatically generate smoothed normals on a mesh.</span></span> <span data-ttu-id="d032e-246">此方法对共享空间中相同位置的网格中的顶点进行分组，然后计算这些顶点的法线平均值。</span><span class="sxs-lookup"><span data-stu-id="d032e-246">This method groups vertices in a mesh that share the same location in space then averages the normals of those vertices.</span></span> <span data-ttu-id="d032e-247">此过程会创建基础网格的副本，应仅在需要时使用。</span><span class="sxs-lookup"><span data-stu-id="d032e-247">This process creates a copy of the underlying mesh and should be used only when required.</span></span>

<img src="../images/mrtk-standard-shader/MRTK_SmoothNormals.jpg" width="450" alt="Smooth Normals Outline">

1. <span data-ttu-id="d032e-248">通过 生成的平滑法线 [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) 。</span><span class="sxs-lookup"><span data-stu-id="d032e-248">Smooth normals generated via [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother).</span></span>
2. <span data-ttu-id="d032e-249">使用的默认法线，请注意围绕立方体角的项目。</span><span class="sxs-lookup"><span data-stu-id="d032e-249">Default normals used, notice the artifacts around the cube corners.</span></span>

### <a name="stencil-testing"></a><span data-ttu-id="d032e-250">模具测试</span><span class="sxs-lookup"><span data-stu-id="d032e-250">Stencil testing</span></span>

<span data-ttu-id="d032e-251">内置可配置模具测试支持，以实现各种效果。</span><span class="sxs-lookup"><span data-stu-id="d032e-251">Built in configurable stencil test support to achieve a wide array of effects.</span></span> <span data-ttu-id="d032e-252">例如门户：</span><span class="sxs-lookup"><span data-stu-id="d032e-252">Such as portals:</span></span>

![模具测试](../images/mrtk-standard-shader/MRTK_StencilTest.gif)

### <a name="instanced-color-support"></a><span data-ttu-id="d032e-254">实例颜色支持</span><span class="sxs-lookup"><span data-stu-id="d032e-254">Instanced color support</span></span>

<span data-ttu-id="d032e-255">实例颜色支持，为数千个 GPU 实例网格提供唯一的材料属性：</span><span class="sxs-lookup"><span data-stu-id="d032e-255">Instanced color support to give thousands of GPU instanced meshes unique material properties:</span></span>

![实例属性](../images/mrtk-standard-shader/MRTK_InstancedProperties.gif)

### <a name="triplanar-mapping"></a><span data-ttu-id="d032e-257">行程映射</span><span class="sxs-lookup"><span data-stu-id="d032e-257">Triplanar mapping</span></span>

<span data-ttu-id="d032e-258">三边形映射是一种以编程方式对网格进行纹理处理的技术。</span><span class="sxs-lookup"><span data-stu-id="d032e-258">Triplanar mapping is a technique to programmatically texture a mesh.</span></span> <span data-ttu-id="d032e-259">通常用于地形、没有 UV 的网格或难以解包形状。</span><span class="sxs-lookup"><span data-stu-id="d032e-259">Often used in terrain, meshes without UVs, or difficult to unwrap shapes.</span></span> <span data-ttu-id="d032e-260">此实现支持世界或本地空间投影、混合平滑度规范以及普通地图支持。</span><span class="sxs-lookup"><span data-stu-id="d032e-260">This implementation supports world or local space projection, the specification of blending smoothness, and normal map support.</span></span> <span data-ttu-id="d032e-261">请注意，使用的每个纹理都需要 3 个纹理样本，因此在性能关键的情况下请谨慎使用。</span><span class="sxs-lookup"><span data-stu-id="d032e-261">Note, each texture used requires 3 texture samples, so use sparingly in performance critical situations.</span></span>

![triplanar](../images/mrtk-standard-shader/MRTK_TriplanarMapping.gif)

### <a name="vertex-extrusion"></a><span data-ttu-id="d032e-263">顶点外泄</span><span class="sxs-lookup"><span data-stu-id="d032e-263">Vertex extrusion</span></span>

<span data-ttu-id="d032e-264">世界空间中的顶点外泄。</span><span class="sxs-lookup"><span data-stu-id="d032e-264">Vertex extrusion in world space.</span></span> <span data-ttu-id="d032e-265">用于可视化外向边界卷或内/出网格的转换。</span><span class="sxs-lookup"><span data-stu-id="d032e-265">Useful for visualizing extruded bounding volumes or transitions in/out meshes.</span></span>

![普通地图比例1](../images/mrtk-standard-shader/MRTK_VertexExtrusion.gif)

### <a name="miscellaneous"></a><span data-ttu-id="d032e-267">杂项</span><span class="sxs-lookup"><span data-stu-id="d032e-267">Miscellaneous</span></span>

<span data-ttu-id="d032e-268">用于控制 albedo 优化的复选框。</span><span class="sxs-lookup"><span data-stu-id="d032e-268">A checkbox to control albedo optimizations.</span></span> <span data-ttu-id="d032e-269">当未指定 albedo 纹理时，将禁用优化 albedo 操作。</span><span class="sxs-lookup"><span data-stu-id="d032e-269">As an optimization albedo operations are disabled when no albedo texture is specified.</span></span> <span data-ttu-id="d032e-270">这对于控制 [远程纹理加载](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html)很有用。</span><span class="sxs-lookup"><span data-stu-id="d032e-270">This is useful for controlling [remote texture loading](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html).</span></span>

<span data-ttu-id="d032e-271">只需选中此框：</span><span class="sxs-lookup"><span data-stu-id="d032e-271">Simply check this box:</span></span>

![albedo 分配](../images/mrtk-standard-shader/MRTK_AlbedoAssignment.jpg)

<span data-ttu-id="d032e-273">每个像素剪辑纹理、基于本地边缘的抗锯齿和普通地图缩放都受支持。</span><span class="sxs-lookup"><span data-stu-id="d032e-273">Per pixel clipping textures, local edge based anti aliasing, and normal map scaling are supported.</span></span>

![普通地图比例2](../images/mrtk-standard-shader/MRTK_NormalMapScale.gif)

## <a name="see-also"></a><span data-ttu-id="d032e-275">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d032e-275">See also</span></span>

* [<span data-ttu-id="d032e-276">可交互</span><span class="sxs-lookup"><span data-stu-id="d032e-276">Interactable</span></span>](../ux-building-blocks/interactable.md)
* [<span data-ttu-id="d032e-277">悬停灯光</span><span class="sxs-lookup"><span data-stu-id="d032e-277">Hover Light</span></span>](hover-light.md)
* [<span data-ttu-id="d032e-278">邻近感应灯</span><span class="sxs-lookup"><span data-stu-id="d032e-278">Proximity Light</span></span>](proximity-light.md)
* [<span data-ttu-id="d032e-279">剪辑基元</span><span class="sxs-lookup"><span data-stu-id="d032e-279">Clipping Primitive</span></span>](clipping-primitive.md)
