---
title: MRTK 标准着色器
description: MRTKStandardShader 文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，材料着色器
ms.openlocfilehash: 0a92388bc9be7c11967501709031f559f17f8966
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176441"
---
# <a name="mrtk-standard-shader"></a><span data-ttu-id="5830d-104">MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="5830d-104">MRTK standard shader</span></span>

![标准着色器示例](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)

<span data-ttu-id="5830d-106">MRTK 标准着色系统利用单个灵活的着色器，它可以实现类似于 Unity 的标准着色器的视觉对象，实现[Fluent Design System](https://www.microsoft.com/design/fluent/)原则，并使混合现实设备保持高性能。</span><span class="sxs-lookup"><span data-stu-id="5830d-106">MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implement [Fluent Design System](https://www.microsoft.com/design/fluent/) principles, and remain performant on mixed reality devices.</span></span>

## <a name="example-scenes"></a><span data-ttu-id="5830d-107">示例场景</span><span class="sxs-lookup"><span data-stu-id="5830d-107">Example scenes</span></span>

<span data-ttu-id="5830d-108">可以在下的 **MaterialGallery** 场景中找到着色器材料示例 `MRTK/Examples/Demos/StandardShader/Scenes/` 。</span><span class="sxs-lookup"><span data-stu-id="5830d-108">You can find the shader material examples in the **MaterialGallery** scene under `MRTK/Examples/Demos/StandardShader/Scenes/`.</span></span> <span data-ttu-id="5830d-109">此场景中的所有材料都使用 MRTK/Standard 着色器。</span><span class="sxs-lookup"><span data-stu-id="5830d-109">All materials in this scene are using the MRTK/Standard shader.</span></span>

![材料库](../images/mrtk-standard-shader/MRTK_MaterialGallery.jpg)

<span data-ttu-id="5830d-111">在下的 **StandardMaterialComparison** 场景中，可以找到比较场景来比较和测试 MRTK/standard 着色器示例 `MRTK/Examples/Demos/StandardShader/Scenes/` 。</span><span class="sxs-lookup"><span data-stu-id="5830d-111">You can find a comparison scene to compare and test the MRTK/Standard shader against the Unity/Standard shader example in the **StandardMaterialComparison** scene under `MRTK/Examples/Demos/StandardShader/Scenes/`.</span></span>

![材料比较](../images/mrtk-standard-shader/MRTK_StandardMaterialComparison.gif)

## <a name="architecture"></a><span data-ttu-id="5830d-113">体系结构</span><span class="sxs-lookup"><span data-stu-id="5830d-113">Architecture</span></span>

<span data-ttu-id="5830d-114">MRTK/Standard 着色系统是一个 "uber 着色器"，它使用 [Unity 的着色器的 "着色器" 程序变体功能](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) 根据材料属性自动生成最佳着色器代码。</span><span class="sxs-lookup"><span data-stu-id="5830d-114">The MRTK/Standard shading system is an "uber shader" that uses [Unity's shader program variant feature](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) to auto-generate optimal shader code based on material properties.</span></span> <span data-ttu-id="5830d-115">当用户在 "材料检查器" 中选择 "材料" 属性时，它们只会对已启用的功能产生性能开销。</span><span class="sxs-lookup"><span data-stu-id="5830d-115">When a user selects material properties in the material inspector, they only incur performance cost for features they have enabled.</span></span>

## <a name="material-inspector"></a><span data-ttu-id="5830d-116">材料检查器</span><span class="sxs-lookup"><span data-stu-id="5830d-116">Material inspector</span></span>

<span data-ttu-id="5830d-117">已调用 MRTK/Standard 着色器的自定义材料检查器 [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI) 。</span><span class="sxs-lookup"><span data-stu-id="5830d-117">A custom material inspector exists for the MRTK/Standard shader called [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI).</span></span> <span data-ttu-id="5830d-118">检查器自动启用/禁用着色器功能，基于用户选择和设置渲染状态 aides。</span><span class="sxs-lookup"><span data-stu-id="5830d-118">The inspector automatically enables/disables shader features, based on user selection and aides in setting up render state.</span></span> <span data-ttu-id="5830d-119">有关每个功能的详细信息， **请将鼠标悬停在 Unity 编辑器中的每个属性上，以获取工具提示。**</span><span class="sxs-lookup"><span data-stu-id="5830d-119">For more information about each feature **please hover over each property in the Unity Editor for a tooltip.**</span></span>

![材料检查器](../images/mrtk-standard-shader/MRTK_MaterialInspector.jpg)

<span data-ttu-id="5830d-121">检查器的第一个部分控制材料的渲染状态。</span><span class="sxs-lookup"><span data-stu-id="5830d-121">The first portion of the inspector controls the material's render state.</span></span> <span data-ttu-id="5830d-122">*渲染模式* 可确定何时以及如何呈现材料。</span><span class="sxs-lookup"><span data-stu-id="5830d-122">*Rendering Mode* determines when and how a material will be rendered.</span></span> <span data-ttu-id="5830d-123">MRTK/Standard 着色器的目标是镜像 [在 Unity/标准着色器中找到的呈现模式](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html)。</span><span class="sxs-lookup"><span data-stu-id="5830d-123">The aim of the MRTK/Standard shader is to mirror the [rendering modes found in the Unity/Standard shader](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html).</span></span> <span data-ttu-id="5830d-124">MRTK/Standard 着色器还包括一个用于完成用户控制的 *附加* 渲染模式和 *自定义* 呈现模式。</span><span class="sxs-lookup"><span data-stu-id="5830d-124">The MRTK/Standard shader also includes an *Additive* rendering mode and *Custom* rendering mode for complete user control.</span></span>

| <span data-ttu-id="5830d-125">呈现模式</span><span class="sxs-lookup"><span data-stu-id="5830d-125">Rendering Mode</span></span> |         <span data-ttu-id="5830d-126">说明</span><span class="sxs-lookup"><span data-stu-id="5830d-126">Description</span></span>                                                       |
|----------------|---------------------------------------------------------------------------|
| <span data-ttu-id="5830d-127">半透明</span><span class="sxs-lookup"><span data-stu-id="5830d-127">Opaque</span></span>         | <span data-ttu-id="5830d-128"> (默认) 适用于没有透明区域的普通实体对象。</span><span class="sxs-lookup"><span data-stu-id="5830d-128">(Default) Suitable for normal solid objects with no transparent areas.</span></span>    |
| <span data-ttu-id="5830d-129">剪影</span><span class="sxs-lookup"><span data-stu-id="5830d-129">Cutout</span></span>         | <span data-ttu-id="5830d-130">允许创建在不透明和透明区域之间具有硬边缘的透明效果。</span><span class="sxs-lookup"><span data-stu-id="5830d-130">Allows creation of transparent effects that have hard edges between the opaque and transparent areas.</span></span> <span data-ttu-id="5830d-131">在此模式下，没有半透明区域，纹理为100% 不透明或不可见。</span><span class="sxs-lookup"><span data-stu-id="5830d-131">In this mode, there are no semi-transparent areas, the texture is either 100% opaque, or invisible.</span></span> <span data-ttu-id="5830d-132">当使用透明度创建材料形状（如 vegetation）时，这非常有用。</span><span class="sxs-lookup"><span data-stu-id="5830d-132">This is useful when using transparency to create the shape of materials, such as vegetation.</span></span> |
| <span data-ttu-id="5830d-133">淡化</span><span class="sxs-lookup"><span data-stu-id="5830d-133">Fade</span></span>           | <span data-ttu-id="5830d-134">允许透明度值完全淡化对象，包括任何镜面高光或反射。</span><span class="sxs-lookup"><span data-stu-id="5830d-134">Allows the transparency values to entirely fade an object out, including any specular highlights or reflections it may have.</span></span> <span data-ttu-id="5830d-135">如果要使对象的动画淡入或淡出，此模式非常有用。它不适合呈现清晰的透明材料（如清晰的塑料或玻璃），因为反射和高光还会淡出。</span><span class="sxs-lookup"><span data-stu-id="5830d-135">This mode is useful if you want to animate an object fading in or out. It is not suitable for rendering realistic transparent materials such as clear plastic or glass because the reflections and highlights will also be faded out.</span></span> |
| <span data-ttu-id="5830d-136">透明</span><span class="sxs-lookup"><span data-stu-id="5830d-136">Transparent</span></span>    | <span data-ttu-id="5830d-137">适用于渲染真实的透明材料，如清晰的塑料或玻璃。</span><span class="sxs-lookup"><span data-stu-id="5830d-137">Suitable for rendering realistic transparent materials such as clear plastic or glass.</span></span> <span data-ttu-id="5830d-138">在此模式下，材料本身将根据纹理的 alpha 通道和颜色颜色) 的 alpha (来使用透明度值。</span><span class="sxs-lookup"><span data-stu-id="5830d-138">In this mode, the material itself will take on transparency values (based on the texture’s alpha channel and the alpha of the tint colour).</span></span> <span data-ttu-id="5830d-139">但是，反射和照明突出显示内容将在完全清晰的情况下保持可见，就像实际透明材料一样。</span><span class="sxs-lookup"><span data-stu-id="5830d-139">However, reflections and lighting highlights will remain visible at full clarity as is the case with real transparent materials.</span></span> |
| <span data-ttu-id="5830d-140">加法</span><span class="sxs-lookup"><span data-stu-id="5830d-140">Additive</span></span>       | <span data-ttu-id="5830d-141">启用一种加法混合模式，该模式将以前的像素颜色与当前像素颜色进行求和。</span><span class="sxs-lookup"><span data-stu-id="5830d-141">Enables an additive blending mode, which sums the previous pixel color with the current pixel color.</span></span> <span data-ttu-id="5830d-142">这是用于避免透明度排序问题的首选透明模式。</span><span class="sxs-lookup"><span data-stu-id="5830d-142">This is the preferred transparency mode to avoid transparency sorting issues.</span></span>     |
| <span data-ttu-id="5830d-143">自定义</span><span class="sxs-lookup"><span data-stu-id="5830d-143">Custom</span></span>         | <span data-ttu-id="5830d-144">允许手动控制呈现模式的每个方面。</span><span class="sxs-lookup"><span data-stu-id="5830d-144">Allows for every aspect of the rendering mode to be controlled manually.</span></span> <span data-ttu-id="5830d-145">仅适用于高级用途。</span><span class="sxs-lookup"><span data-stu-id="5830d-145">For advanced usage only.</span></span>   |

![呈现模式](../images/mrtk-standard-shader/MRTK_RenderingModes.jpg)

| <span data-ttu-id="5830d-147">精选模式</span><span class="sxs-lookup"><span data-stu-id="5830d-147">Cull Mode</span></span> |             <span data-ttu-id="5830d-148">说明</span><span class="sxs-lookup"><span data-stu-id="5830d-148">Description</span></span>                                                                                                                                                                       |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5830d-149">关</span><span class="sxs-lookup"><span data-stu-id="5830d-149">Off</span></span>       | <span data-ttu-id="5830d-150">禁用面部剔除。</span><span class="sxs-lookup"><span data-stu-id="5830d-150">Disables face culling.</span></span> <span data-ttu-id="5830d-151">如果需要双面网格，则只能将剔除设置为 Off。</span><span class="sxs-lookup"><span data-stu-id="5830d-151">Culling should only be set to Off when a two sided mesh is required.</span></span>                                                                                        |
| <span data-ttu-id="5830d-152">Front</span><span class="sxs-lookup"><span data-stu-id="5830d-152">Front</span></span>     | <span data-ttu-id="5830d-153">启用正面剔除。</span><span class="sxs-lookup"><span data-stu-id="5830d-153">Enables front face culling.</span></span>                                                                                                                                                        |
| <span data-ttu-id="5830d-154">返回</span><span class="sxs-lookup"><span data-stu-id="5830d-154">Back</span></span>      | <span data-ttu-id="5830d-155"> (默认) 启用 [背面剔除](https://en.wikipedia.org/wiki/Back-face_culling)。</span><span class="sxs-lookup"><span data-stu-id="5830d-155">(Default) Enables [back face culling](https://en.wikipedia.org/wiki/Back-face_culling).</span></span> <span data-ttu-id="5830d-156">应尽可能频繁地启用背面剔除以提高呈现性能。</span><span class="sxs-lookup"><span data-stu-id="5830d-156">Back face culling should be enabled as often as possible to improve rendering performance.</span></span> |

## <a name="performance"></a><span data-ttu-id="5830d-157">性能</span><span class="sxs-lookup"><span data-stu-id="5830d-157">Performance</span></span>

<span data-ttu-id="5830d-158">通过 Unity 标准着色器使用 MRTK 标准着色器的主要优点之一是性能。</span><span class="sxs-lookup"><span data-stu-id="5830d-158">One of the primary advantages to using the MRTK Standard shader over the Unity standard shader is performance.</span></span> <span data-ttu-id="5830d-159">MRTK 标准着色器可扩展，只利用启用的功能。</span><span class="sxs-lookup"><span data-stu-id="5830d-159">The MRTK Standard Shader is extensible to only utilize the features enabled.</span></span> <span data-ttu-id="5830d-160">不过，MRTK 标准着色器也已经编写，以将相当美观的结果作为 Unity 标准着色器提供，但成本要低得多。</span><span class="sxs-lookup"><span data-stu-id="5830d-160">However, the MRTK Standard shader has also been written to deliver comparable aesthetic results as the Unity Standard shader, but at a much lower cost.</span></span> <span data-ttu-id="5830d-161">比较着色器性能的一种简单方法是通过 GPU 上需要执行的操作的数量。</span><span class="sxs-lookup"><span data-stu-id="5830d-161">One simple way to compare shader performance is via the number of operations that needs to be performed on the GPU.</span></span> <span data-ttu-id="5830d-162">当然，根据启用的功能和其他呈现配置，计算量可能会波动。</span><span class="sxs-lookup"><span data-stu-id="5830d-162">Of course, the magnitude of calculations may fluctuate by features enabled and other rendering configurations.</span></span> <span data-ttu-id="5830d-163">但一般情况下，MRTK 标准着色器比 Unity 标准着色器执行的计算要少得多。</span><span class="sxs-lookup"><span data-stu-id="5830d-163">But, in general, the MRTK Standard shader performs significantly less computation than the Unity Standard shader.</span></span>

<span data-ttu-id="5830d-164">Unity 标准着色器统计信息示例</span><span class="sxs-lookup"><span data-stu-id="5830d-164">Unity Standard shader statistics example</span></span>

![Unity 标准着色器统计信息](../images/performance/UnityStandardShader-Stats.PNG)

<span data-ttu-id="5830d-166">MRTK 标准着色器统计信息示例</span><span class="sxs-lookup"><span data-stu-id="5830d-166">MRTK Standard shader statistics example</span></span>

![MRTK 标准着色器统计信息](../images/performance/MRTKStandardShader-Stats.PNG)

> [!NOTE]
> <span data-ttu-id="5830d-168">可以通过在 Unity 检查器中选择和查看 [着色器资产](https://docs.unity3d.com/Manual/class-Shader.html) ，然后单击 " *编译并显示代码* " 按钮，从而生成这些结果。</span><span class="sxs-lookup"><span data-stu-id="5830d-168">These results can be generated by selecting and viewing a [shader asset](https://docs.unity3d.com/Manual/class-Shader.html) in the Unity inspector, then clicking the *Compile and show code* button.</span></span>

## <a name="lighting"></a><span data-ttu-id="5830d-169">照明</span><span class="sxs-lookup"><span data-stu-id="5830d-169">Lighting</span></span>

<span data-ttu-id="5830d-170">MRTK/Standard 使用简单的近似值。</span><span class="sxs-lookup"><span data-stu-id="5830d-170">The MRTK/Standard uses a simple approximation for lighting.</span></span> <span data-ttu-id="5830d-171">由于此着色器不计算物理正确性和能源节省，因此它能够快速有效地呈现。</span><span class="sxs-lookup"><span data-stu-id="5830d-171">Because this shader does not calculate for physical correctness and energy conservation, it renders quickly and efficiently.</span></span> <span data-ttu-id="5830d-172">Blinn-Phong 是一种主要照明技术，它与菲涅尔衰减和基于图像的照明相混合，以使基于物理的照明接近。</span><span class="sxs-lookup"><span data-stu-id="5830d-172">Blinn-Phong is the primary lighting technique which is blended with Fresnel and image-based lighting to approximate physically-based lighting.</span></span> <span data-ttu-id="5830d-173">着色器支持以下照明技术：</span><span class="sxs-lookup"><span data-stu-id="5830d-173">The shader supports the following lighting techniques:</span></span>

### <a name="directional-light"></a><span data-ttu-id="5830d-174">定向光</span><span class="sxs-lookup"><span data-stu-id="5830d-174">Directional light</span></span>

<span data-ttu-id="5830d-175">着色器将遵循场景中第一个 Unity 方向光的方向、颜色和强度， (如果启用了) 。</span><span class="sxs-lookup"><span data-stu-id="5830d-175">The shader will respect the direction, color, and intensity of the first Unity Directional Light in the scene (if enabled).</span></span> <span data-ttu-id="5830d-176">不会将动态点光、污点光源或任何其他 Unity 光源视为实时照明。</span><span class="sxs-lookup"><span data-stu-id="5830d-176">Dynamic point lights, spot lights, or any other Unity light will not be considered in real time lighting.</span></span>

### <a name="spherical-harmonics"></a><span data-ttu-id="5830d-177">球形谐波</span><span class="sxs-lookup"><span data-stu-id="5830d-177">Spherical harmonics</span></span>

<span data-ttu-id="5830d-178">着色器使用 [球状谐波](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html)（如果已启用），将使用光源探测来估算场景中的灯。</span><span class="sxs-lookup"><span data-stu-id="5830d-178">The shader will use Light Probes to approximate lights in the scene using [Spherical Harmonics](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html), if enabled.</span></span> <span data-ttu-id="5830d-179">球形谐波计算按顶点执行以降低计算成本。</span><span class="sxs-lookup"><span data-stu-id="5830d-179">Spherical harmonics calculations are performed per vertex to reduce calculation cost.</span></span>

### <a name="lightmapping"></a><span data-ttu-id="5830d-180">Lightmapping</span><span class="sxs-lookup"><span data-stu-id="5830d-180">Lightmapping</span></span>

<span data-ttu-id="5830d-181">对于静态照明，着色器将遵循由 Unity 的 [Lightmapping 系统](https://docs.unity3d.com/Manual/Lightmapping.html)生成的 lightmaps。</span><span class="sxs-lookup"><span data-stu-id="5830d-181">For static lighting, the shader will respect lightmaps built by Unity's [Lightmapping system](https://docs.unity3d.com/Manual/Lightmapping.html).</span></span> <span data-ttu-id="5830d-182">只需将呈现器标记为 static (或 lightmap static) 才能使用 lightmaps。</span><span class="sxs-lookup"><span data-stu-id="5830d-182">Simply mark the renderer as static (or lightmap static) to use lightmaps.</span></span>

### <a name="hover-light"></a><span data-ttu-id="5830d-183">悬停灯光</span><span class="sxs-lookup"><span data-stu-id="5830d-183">Hover light</span></span>

* <span data-ttu-id="5830d-184">请参阅 [悬停灯光](hover-light.md)</span><span class="sxs-lookup"><span data-stu-id="5830d-184">See [Hover Light](hover-light.md)</span></span>

### <a name="proximity-light"></a><span data-ttu-id="5830d-185">邻近感应</span><span class="sxs-lookup"><span data-stu-id="5830d-185">Proximity light</span></span>

* <span data-ttu-id="5830d-186">查看 [邻近感应](proximity-light.md)</span><span class="sxs-lookup"><span data-stu-id="5830d-186">See [Proximity Light](proximity-light.md)</span></span>

## <a name="lightweight-scriptable-render-pipeline-support"></a><span data-ttu-id="5830d-187">轻型可编写脚本呈现管道支持</span><span class="sxs-lookup"><span data-stu-id="5830d-187">Lightweight Scriptable Render Pipeline support</span></span>

<span data-ttu-id="5830d-188">MRTK 包含一个升级路径，使开发人员能够使用 MRTK 着色器 (LWRP) 使用 Unity 的轻型可编写脚本呈现管道。</span><span class="sxs-lookup"><span data-stu-id="5830d-188">The MRTK contains an upgrade path to allow developers to utilize Unity's Lightweight Scriptable Render Pipeline (LWRP) with MRTK shaders.</span></span> <span data-ttu-id="5830d-189">在 Unity 2019.1.1 f1 和轻型 RP 5.7.2 包中进行了测试。</span><span class="sxs-lookup"><span data-stu-id="5830d-189">Tested in Unity 2019.1.1f1 and Lightweight RP 5.7.2 package.</span></span> <span data-ttu-id="5830d-190">有关 LWRP 入门的说明，请参阅 [此页](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html)。</span><span class="sxs-lookup"><span data-stu-id="5830d-190">or instructions on getting started with the LWRP, see [this page](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html).</span></span>

<span data-ttu-id="5830d-191">若要执行 MRTK 升级，请选择： **Mixed Reality Toolkit > 实用工具-> upgrade MRTK Standard 着色器**</span><span class="sxs-lookup"><span data-stu-id="5830d-191">To perform the MRTK upgrade, select: **Mixed Reality Toolkit -> Utilities -> Upgrade MRTK Standard Shader for Lightweight Render Pipeline**</span></span>

![lwrp 升级](../images/mrtk-standard-shader/MRTK_LWRPUpgrade.jpg)

<span data-ttu-id="5830d-193">升级完成后，MRTK/Standard 着色器将被更改，并且任何洋红色 (着色器错误) 材料应修复。</span><span class="sxs-lookup"><span data-stu-id="5830d-193">After the upgrade occurs, the MRTK/Standard shader will be altered and any magenta (shader error) materials should be fixed.</span></span> <span data-ttu-id="5830d-194">若要验证升级是否成功，请查看：**升级资产/MixedRealityToolkit/StandardAssets/着色器/MixedRealityStandard 用于轻量渲染管道** 的控制台。</span><span class="sxs-lookup"><span data-stu-id="5830d-194">To verify the upgrade successfully occurred, check the console for: **Upgraded Assets/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader for use with the Lightweight Render Pipeline.**</span></span>

## <a name="ugui-support"></a><span data-ttu-id="5830d-195">UGUI 支持</span><span class="sxs-lookup"><span data-stu-id="5830d-195">UGUI support</span></span>

<span data-ttu-id="5830d-196">MRTK 标准着色系统与 Unity 内置的 [UI 系统](https://docs.unity3d.com/Manual/UISystem.html)一起工作。</span><span class="sxs-lookup"><span data-stu-id="5830d-196">The MRTK Standard shading system works with Unity's built in [UI system](https://docs.unity3d.com/Manual/UISystem.html).</span></span> <span data-ttu-id="5830d-197">在 Unity UI 组件上，unity_ObjectToWorld 矩阵不是图形组件所在的本地转换的转换矩阵，而是它的父画布的转换矩阵。</span><span class="sxs-lookup"><span data-stu-id="5830d-197">On Unity UI components, the unity_ObjectToWorld matrix is not the transformation matrix of the local transform the Graphic component lives on but that of its parent Canvas.</span></span> <span data-ttu-id="5830d-198">许多 MRTK/标准着色器效果需要知道对象范围。</span><span class="sxs-lookup"><span data-stu-id="5830d-198">Many MRTK/Standard shader effects require object scale to be known.</span></span> <span data-ttu-id="5830d-199">若要解决此问题， [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) 将在 UI 网格构造过程中将缩放信息存储到 UV 通道特性中。</span><span class="sxs-lookup"><span data-stu-id="5830d-199">To solve this issue, the [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) will store scaling information into UV channel attributes during UI mesh construction.</span></span>

<span data-ttu-id="5830d-200">请注意，在使用 Unity 图像组件时，建议为源映像指定 "None (Sprite) "，以防止 Unity UI 生成额外顶点。</span><span class="sxs-lookup"><span data-stu-id="5830d-200">Note, when using a Unity Image component, it is recommended to specify "None (Sprite)" for the Source Image to prevent Unity UI from generating extra vertices.</span></span>

<span data-ttu-id="5830d-201">如果需要，MRTK 中的画布会提示添加一个 [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) ：</span><span class="sxs-lookup"><span data-stu-id="5830d-201">A Canvas within the MRTK will prompt for the addition of a [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) when one is required:</span></span>

![缩放网格效果](../images/mrtk-standard-shader/MRTK_ScaleMeshEffect.jpg)

## <a name="texture-combiner"></a><span data-ttu-id="5830d-203">纹理合并器</span><span class="sxs-lookup"><span data-stu-id="5830d-203">Texture combiner</span></span>

<span data-ttu-id="5830d-204">若要提高与 Unity 标准着色器每像素金属、平滑度、放射和封闭值的奇偶校验，可以通过 [通道封装](http://wiki.polycount.com/wiki/ChannelPacking)来控制。</span><span class="sxs-lookup"><span data-stu-id="5830d-204">To improve parity with the Unity Standard shader per pixel metallic, smoothness, emissive, and occlusion values can all be controlled via [channel packing](http://wiki.polycount.com/wiki/ChannelPacking).</span></span> <span data-ttu-id="5830d-205">例如：</span><span class="sxs-lookup"><span data-stu-id="5830d-205">For example:</span></span>

![通道映射示例](../images/mrtk-standard-shader/MRTK_ChannelMap.gif)

<span data-ttu-id="5830d-207">使用通道打包时，只需将一个纹理采样并加载到内存中，而不是使用四个单独的纹理。</span><span class="sxs-lookup"><span data-stu-id="5830d-207">When you use channel packing, you only have to sample and load one texture into memory instead of four separate ones.</span></span> <span data-ttu-id="5830d-208">当您在某个程序（如物质或 Photoshop）中编写纹理地图时，可以按如下所示对其进行打包：</span><span class="sxs-lookup"><span data-stu-id="5830d-208">When you write your texture maps in a program like Substance or Photoshop, you can hand pack them like the following:</span></span>

| <span data-ttu-id="5830d-209">通道</span><span class="sxs-lookup"><span data-stu-id="5830d-209">Channel</span></span> | <span data-ttu-id="5830d-210">属性</span><span class="sxs-lookup"><span data-stu-id="5830d-210">Property</span></span>             |
|---------|----------------------|
| <span data-ttu-id="5830d-211">Red</span><span class="sxs-lookup"><span data-stu-id="5830d-211">Red</span></span>     | <span data-ttu-id="5830d-212">银色</span><span class="sxs-lookup"><span data-stu-id="5830d-212">Metallic</span></span>             |
| <span data-ttu-id="5830d-213">绿色</span><span class="sxs-lookup"><span data-stu-id="5830d-213">Green</span></span>   | <span data-ttu-id="5830d-214">封闭</span><span class="sxs-lookup"><span data-stu-id="5830d-214">Occlusion</span></span>            |
| <span data-ttu-id="5830d-215">蓝色</span><span class="sxs-lookup"><span data-stu-id="5830d-215">Blue</span></span>    | <span data-ttu-id="5830d-216"> (灰度) 发射</span><span class="sxs-lookup"><span data-stu-id="5830d-216">Emission (Greyscale)</span></span> |
| <span data-ttu-id="5830d-217">Alpha</span><span class="sxs-lookup"><span data-stu-id="5830d-217">Alpha</span></span>   | <span data-ttu-id="5830d-218">平滑度</span><span class="sxs-lookup"><span data-stu-id="5830d-218">Smoothness</span></span>           |

<span data-ttu-id="5830d-219">或者，可以使用 MRTK 纹理合并器工具。</span><span class="sxs-lookup"><span data-stu-id="5830d-219">Or, you can use the MRTK Texture Combiner Tool.</span></span> <span data-ttu-id="5830d-220">若要打开该工具，请选择： **Mixed Reality Toolkit > 公用事业-> 纹理合并器**，这将打开以下窗口：</span><span class="sxs-lookup"><span data-stu-id="5830d-220">To open the tool, select: **Mixed Reality Toolkit -> Utilities -> Texture Combiner** which will open the below window:</span></span>

![纹理合并器示例](../images/mrtk-standard-shader/MRTK_TextureCombiner.jpg)

<span data-ttu-id="5830d-222">可以通过选择 Unity 标准着色器并单击 "从标准材料自动填充数据" 来自动填充此窗口。</span><span class="sxs-lookup"><span data-stu-id="5830d-222">This window can be automatically filled out by selecting a Unity Standard shader and clicking "Autopopulate from Standard Material."</span></span> <span data-ttu-id="5830d-223">或者，您可以手动指定纹理 (或常量值) 每个红色、绿色、蓝色或 alpha 通道。</span><span class="sxs-lookup"><span data-stu-id="5830d-223">Or, you can manually specify a texture (or constant value) per red, green, blue, or alpha channel.</span></span> <span data-ttu-id="5830d-224">纹理组合为 GPU 加速，无需输入纹理即可对 CPU 进行访问。</span><span class="sxs-lookup"><span data-stu-id="5830d-224">The texture combination is GPU accelerated and does not require the input texture to be CPU accessible.</span></span>

## <a name="additional-feature-documentation"></a><span data-ttu-id="5830d-225">其他功能文档</span><span class="sxs-lookup"><span data-stu-id="5830d-225">Additional feature documentation</span></span>

<span data-ttu-id="5830d-226">下面是 MRTK/Standard 着色器提供的一些功能详细信息的额外详细信息。</span><span class="sxs-lookup"><span data-stu-id="5830d-226">Below are extra details on a handful of feature details available with the MRTK/Standard shader.</span></span>

### <a name="primitive-clipping"></a><span data-ttu-id="5830d-227">基元剪辑</span><span class="sxs-lookup"><span data-stu-id="5830d-227">Primitive clipping</span></span>

![基元剪辑](../images/mrtk-standard-shader/MRTK_PrimitiveClipping.gif)

* <span data-ttu-id="5830d-229">请参阅 [剪辑基元](clipping-primitive.md)</span><span class="sxs-lookup"><span data-stu-id="5830d-229">See [Clipping Primitive](clipping-primitive.md)</span></span>

### <a name="mesh-outlines"></a><span data-ttu-id="5830d-230">网格轮廓</span><span class="sxs-lookup"><span data-stu-id="5830d-230">Mesh outlines</span></span>

<span data-ttu-id="5830d-231">许多网格大纲技术均使用 [post 处理](https://docs.unity3d.com/Manual/PostProcessingOverview.html) 技术完成。</span><span class="sxs-lookup"><span data-stu-id="5830d-231">Many mesh outline techniques are done using a [post processing](https://docs.unity3d.com/Manual/PostProcessingOverview.html) technique.</span></span> <span data-ttu-id="5830d-232">Post 处理提供了很好的大纲，但在许多混合现实设备上可能会占用大量资源。</span><span class="sxs-lookup"><span data-stu-id="5830d-232">Post processing provides great quality outlines, but can be prohibitively expensive on many Mixed Reality devices.</span></span> <span data-ttu-id="5830d-233">可以在下的  **OutlineExamples** 场景中找到演示网格轮廓用法的场景 `MRTK/Examples/Demos/StandardShader/Scenes/` 。</span><span class="sxs-lookup"><span data-stu-id="5830d-233">You can find a scene that demonstrates usage of mesh outlines in the  **OutlineExamples** scene under `MRTK/Examples/Demos/StandardShader/Scenes/`.</span></span>

<img src="../images/mrtk-standard-shader/MRTK_MeshOutline.jpg" width="900" alt="Mesh Outline">

<span data-ttu-id="5830d-234">[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) 和 [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) 可用于呈现围绕网格呈现器的轮廓。</span><span class="sxs-lookup"><span data-stu-id="5830d-234">[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) and [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) can be used to render an outline around a mesh renderer.</span></span> <span data-ttu-id="5830d-235">启用此组件会引入所述对象的其他呈现处理过程，但设计用于在移动混合现实设备上运行之前，而不使用任何 post 过程。</span><span class="sxs-lookup"><span data-stu-id="5830d-235">Enabling this component introduces an additional render pass of the object being outlined, but is designed to run performantly on mobile Mixed Reality devices and does not utilize any post processes.</span></span> <span data-ttu-id="5830d-236">这种效果的限制包括它不能很好地处理不是 (watertight 的对象，也不需要是两面) 并且在重叠对象上可能会出现深度排序问题。</span><span class="sxs-lookup"><span data-stu-id="5830d-236">Limitations of this effect include it not working well on objects which are not watertight (or required to be two sided) and depth sorting issues can occur on overlapping objects.</span></span>

<span data-ttu-id="5830d-237">大纲行为设计为与 MRTK/Standard 着色器结合使用。</span><span class="sxs-lookup"><span data-stu-id="5830d-237">The outline behaviors are designed to be used in conjunction with the MRTK/Standard shader.</span></span> <span data-ttu-id="5830d-238">大纲材料通常是一种可靠的 unlit 颜色，但可以配置为实现范围很大的效果。</span><span class="sxs-lookup"><span data-stu-id="5830d-238">Outline materials are usually a solid unlit color, but can be configured to achieve a wide array of effects.</span></span> <span data-ttu-id="5830d-239">大纲材料的默认配置如下所示：</span><span class="sxs-lookup"><span data-stu-id="5830d-239">The default configuration of a outline material is as follows:</span></span>

<img src="../images/mrtk-standard-shader/MRTK_OutlineMaterial.jpg" width="450" alt="Mesh Outline Material">

1. <span data-ttu-id="5830d-240">深度写入-应禁用轮廓材料，以确保轮廓不会阻止其他对象呈现。</span><span class="sxs-lookup"><span data-stu-id="5830d-240">Depth Write - should be disabled for outline materials to make sure the outline does not prevent other objects from rendering.</span></span>
2. <span data-ttu-id="5830d-241">顶点延伸-需要启用才能呈现轮廓。</span><span class="sxs-lookup"><span data-stu-id="5830d-241">Vertex Extrusion - needs to be enabled to render the outline.</span></span>
3. <span data-ttu-id="5830d-242">使用平滑法线-对于某些网格，此设置是可选的。</span><span class="sxs-lookup"><span data-stu-id="5830d-242">Use Smooth Normals - this setting is optional for some meshes.</span></span> <span data-ttu-id="5830d-243">在沿顶点法线移动顶点时进行延伸，某些网格沿默认的法线凸出会导致中断。</span><span class="sxs-lookup"><span data-stu-id="5830d-243">Extrusion occurs by moving a vertex along a vertex normal, on some meshes extruding along the default normals will cause discontinuities in the outline.</span></span> <span data-ttu-id="5830d-244">若要修复这些中断，可以选中此框，以使用由生成的另一组平滑法 [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)</span><span class="sxs-lookup"><span data-stu-id="5830d-244">To fix these discontinuities, you can check this box to use another set of smoothed normals which get generated by [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)</span></span>

<span data-ttu-id="5830d-245">[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) 是一个组件，可用于在网格上自动生成平滑的法线。</span><span class="sxs-lookup"><span data-stu-id="5830d-245">[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) is a component which can be used to automatically generate smoothed normals on a mesh.</span></span> <span data-ttu-id="5830d-246">此方法对在空间中共享同一位置的网格中的顶点进行分组，然后将这些顶点的法线取平均值。</span><span class="sxs-lookup"><span data-stu-id="5830d-246">This method groups vertices in a mesh that share the same location in space then averages the normals of those vertices.</span></span> <span data-ttu-id="5830d-247">此过程将创建基础网格的副本，并且应仅在需要时使用。</span><span class="sxs-lookup"><span data-stu-id="5830d-247">This process creates a copy of the underlying mesh and should be used only when required.</span></span>

<img src="../images/mrtk-standard-shader/MRTK_SmoothNormals.jpg" width="450" alt="Smooth Normals Outline">

1. <span data-ttu-id="5830d-248">通过生成的平滑法线 [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) 。</span><span class="sxs-lookup"><span data-stu-id="5830d-248">Smooth normals generated via [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother).</span></span>
2. <span data-ttu-id="5830d-249">使用默认的法线，请注意多维数据集拐角周围的项目。</span><span class="sxs-lookup"><span data-stu-id="5830d-249">Default normals used, notice the artifacts around the cube corners.</span></span>

### <a name="stencil-testing"></a><span data-ttu-id="5830d-250">模具测试</span><span class="sxs-lookup"><span data-stu-id="5830d-250">Stencil testing</span></span>

<span data-ttu-id="5830d-251">内置可配置的模具测试支持，可实现各种效果。</span><span class="sxs-lookup"><span data-stu-id="5830d-251">Built in configurable stencil test support to achieve a wide array of effects.</span></span> <span data-ttu-id="5830d-252">例如门户：</span><span class="sxs-lookup"><span data-stu-id="5830d-252">Such as portals:</span></span>

![模具测试](../images/mrtk-standard-shader/MRTK_StencilTest.gif)

### <a name="instanced-color-support"></a><span data-ttu-id="5830d-254">实例颜色支持</span><span class="sxs-lookup"><span data-stu-id="5830d-254">Instanced color support</span></span>

<span data-ttu-id="5830d-255">实例颜色支持为数千个 GPU 实例网格提供唯一的材料属性：</span><span class="sxs-lookup"><span data-stu-id="5830d-255">Instanced color support to give thousands of GPU instanced meshes unique material properties:</span></span>

![实例属性](../images/mrtk-standard-shader/MRTK_InstancedProperties.gif)

### <a name="triplanar-mapping"></a><span data-ttu-id="5830d-257">Triplanar 映射</span><span class="sxs-lookup"><span data-stu-id="5830d-257">Triplanar mapping</span></span>

<span data-ttu-id="5830d-258">Triplanar 映射是一种以编程方式为网格纹理的技术。</span><span class="sxs-lookup"><span data-stu-id="5830d-258">Triplanar mapping is a technique to programmatically texture a mesh.</span></span> <span data-ttu-id="5830d-259">通常在地形中使用，无需 Uv-11 或难以解包的网格。</span><span class="sxs-lookup"><span data-stu-id="5830d-259">Often used in terrain, meshes without UVs, or difficult to unwrap shapes.</span></span> <span data-ttu-id="5830d-260">此实现支持世界或本地空间投影、混合平滑度的规范和普通地图支持。</span><span class="sxs-lookup"><span data-stu-id="5830d-260">This implementation supports world or local space projection, the specification of blending smoothness, and normal map support.</span></span> <span data-ttu-id="5830d-261">请注意，使用的每个纹理都需要3个纹理样本，因此在性能方面非常严重。</span><span class="sxs-lookup"><span data-stu-id="5830d-261">Note, each texture used requires 3 texture samples, so use sparingly in performance critical situations.</span></span>

![triplanar](../images/mrtk-standard-shader/MRTK_TriplanarMapping.gif)

### <a name="vertex-extrusion"></a><span data-ttu-id="5830d-263">顶点延伸</span><span class="sxs-lookup"><span data-stu-id="5830d-263">Vertex extrusion</span></span>

<span data-ttu-id="5830d-264">世界空间中的顶点延伸。</span><span class="sxs-lookup"><span data-stu-id="5830d-264">Vertex extrusion in world space.</span></span> <span data-ttu-id="5830d-265">用于可视化拉伸的边界卷或转换为/out 网格。</span><span class="sxs-lookup"><span data-stu-id="5830d-265">Useful for visualizing extruded bounding volumes or transitions in/out meshes.</span></span>

![普通地图比例1](../images/mrtk-standard-shader/MRTK_VertexExtrusion.gif)

### <a name="miscellaneous"></a><span data-ttu-id="5830d-267">杂项</span><span class="sxs-lookup"><span data-stu-id="5830d-267">Miscellaneous</span></span>

<span data-ttu-id="5830d-268">用于控制 albedo 优化的复选框。</span><span class="sxs-lookup"><span data-stu-id="5830d-268">A checkbox to control albedo optimizations.</span></span> <span data-ttu-id="5830d-269">当未指定 albedo 纹理时，将禁用优化 albedo 操作。</span><span class="sxs-lookup"><span data-stu-id="5830d-269">As an optimization albedo operations are disabled when no albedo texture is specified.</span></span> <span data-ttu-id="5830d-270">这对于控制 [远程纹理加载](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html)很有用。</span><span class="sxs-lookup"><span data-stu-id="5830d-270">This is useful for controlling [remote texture loading](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html).</span></span>

<span data-ttu-id="5830d-271">只需选中此框：</span><span class="sxs-lookup"><span data-stu-id="5830d-271">Simply check this box:</span></span>

![albedo 分配](../images/mrtk-standard-shader/MRTK_AlbedoAssignment.jpg)

<span data-ttu-id="5830d-273">每个像素剪辑纹理、基于本地边缘的抗锯齿和普通地图缩放都受支持。</span><span class="sxs-lookup"><span data-stu-id="5830d-273">Per pixel clipping textures, local edge based anti aliasing, and normal map scaling are supported.</span></span>

![普通地图比例2](../images/mrtk-standard-shader/MRTK_NormalMapScale.gif)

## <a name="see-also"></a><span data-ttu-id="5830d-275">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5830d-275">See also</span></span>

* [<span data-ttu-id="5830d-276">可交互</span><span class="sxs-lookup"><span data-stu-id="5830d-276">Interactable</span></span>](../ux-building-blocks/interactable.md)
* [<span data-ttu-id="5830d-277">悬停灯光</span><span class="sxs-lookup"><span data-stu-id="5830d-277">Hover Light</span></span>](hover-light.md)
* [<span data-ttu-id="5830d-278">邻近感应灯</span><span class="sxs-lookup"><span data-stu-id="5830d-278">Proximity Light</span></span>](proximity-light.md)
* [<span data-ttu-id="5830d-279">剪辑基元</span><span class="sxs-lookup"><span data-stu-id="5830d-279">Clipping Primitive</span></span>](clipping-primitive.md)
