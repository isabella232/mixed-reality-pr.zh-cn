---
title: 了解混合现实的性能
description: 了解用于分析和优化 Windows Mixed Reality 应用性能的高级信息和详细信息。
author: hferrone
ms.author: v-hferrone
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，性能，优化，CPU，GPU
ms.openlocfilehash: 5012c30dce1ca4149324c916355922086a33c258
ms.sourcegitcommit: 6725b83adf13f6573faacb27db2bcaafe80df472
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615123"
---
# <a name="understanding-performance-for-mixed-reality"></a><span data-ttu-id="120db-104">了解混合现实的性能</span><span class="sxs-lookup"><span data-stu-id="120db-104">Understanding performance for mixed reality</span></span>

<span data-ttu-id="120db-105">本文介绍了如何了解混合现实应用的性能的重要性。</span><span class="sxs-lookup"><span data-stu-id="120db-105">This article is an introduction to understanding the significance of performance for your Mixed Reality app.</span></span>  <span data-ttu-id="120db-106">如果你的应用程序不能以最佳帧速率运行，用户体验会大大降低。</span><span class="sxs-lookup"><span data-stu-id="120db-106">User experience can be greatly degraded if your application doesn't run at optimal frame rate.</span></span> <span data-ttu-id="120db-107">全息影像会显得不稳定，因此，对环境的打印头跟踪是不准确的，导致用户体验不佳。</span><span class="sxs-lookup"><span data-stu-id="120db-107">Holograms will appear unstable and head tracking of the environment will be inaccurate, leading to a poor experience for the user.</span></span> <span data-ttu-id="120db-108">对于混合现实开发而言，必须将性能视为第一类功能，而不是波兰语任务。</span><span class="sxs-lookup"><span data-stu-id="120db-108">Performance must be considered a first class feature for mixed reality development and not a polish task.</span></span>

<span data-ttu-id="120db-109">下面列出了每个目标平台的高性能帧速率值。</span><span class="sxs-lookup"><span data-stu-id="120db-109">The performant framerate values for each target platform are listed below.</span></span>

| <span data-ttu-id="120db-110">平台</span><span class="sxs-lookup"><span data-stu-id="120db-110">Platform</span></span> | <span data-ttu-id="120db-111">目标帧速率</span><span class="sxs-lookup"><span data-stu-id="120db-111">Target Frame Rate</span></span> |
|----------|-------------------|
| [<span data-ttu-id="120db-112">HoloLens</span><span class="sxs-lookup"><span data-stu-id="120db-112">HoloLens</span></span>](/hololens/hololens1-hardware) | <span data-ttu-id="120db-113">60 FPS</span><span class="sxs-lookup"><span data-stu-id="120db-113">60 FPS</span></span> |
| [<span data-ttu-id="120db-114">Windows Mixed Reality 超 Pc</span><span class="sxs-lookup"><span data-stu-id="120db-114">Windows Mixed Reality Ultra PCs</span></span>](../../discover/immersive-headset-hardware-details.md) | <span data-ttu-id="120db-115">90 FPS</span><span class="sxs-lookup"><span data-stu-id="120db-115">90 FPS</span></span> |
| [<span data-ttu-id="120db-116">Windows Mixed Reality Pc</span><span class="sxs-lookup"><span data-stu-id="120db-116">Windows Mixed Reality PCs</span></span>](../../discover/immersive-headset-hardware-details.md) | <span data-ttu-id="120db-117">60 FPS</span><span class="sxs-lookup"><span data-stu-id="120db-117">60 FPS</span></span> |

<span data-ttu-id="120db-118">下面的框架概述了命中目标帧速率的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="120db-118">The framework below outlines best practices for hitting target frame rates.</span></span> <span data-ttu-id="120db-119">建议阅读有关 [unity 的性能建议一文](../unity/performance-recommendations-for-unity.md) ，了解在 unity 环境中测量和提高帧率的技巧。</span><span class="sxs-lookup"><span data-stu-id="120db-119">We recommend reading the [performance recommendations for Unity article](../unity/performance-recommendations-for-unity.md) for tips on measuring and improving framerate in the Unity environment.</span></span>

## <a name="understanding-performance-bottlenecks"></a><span data-ttu-id="120db-120">了解性能瓶颈</span><span class="sxs-lookup"><span data-stu-id="120db-120">Understanding performance bottlenecks</span></span>

<span data-ttu-id="120db-121">如果你的应用程序具有绩效不佳的帧速率，则第一步是分析并了解应用程序的计算工作量。</span><span class="sxs-lookup"><span data-stu-id="120db-121">If your app has an underperforming framerate, the first step is to analyze and understand where your application is computationally intensive.</span></span> <span data-ttu-id="120db-122">有两个主要处理器负责呈现场景： CPU 和 GPU，分别处理混合现实应用的不同方面。</span><span class="sxs-lookup"><span data-stu-id="120db-122">There are two primary processors responsible for the work to render your scene: the CPU and the GPU, each handling different aspects of your Mixed Reality app.</span></span> <span data-ttu-id="120db-123">瓶颈可能出现在以下三个关键位置：</span><span class="sxs-lookup"><span data-stu-id="120db-123">The three key places where bottlenecks may occur are:</span></span> 

1. <span data-ttu-id="120db-124">**应用线程-CPU** -
    负责应用逻辑，包括处理输入、动画、物理学和其他应用逻辑。</span><span class="sxs-lookup"><span data-stu-id="120db-124">**App Thread - CPU** -
 Responsible for your app logic, including processing input, animations, physics, and other app logic.</span></span>
2. <span data-ttu-id="120db-125">**将线程 CPU 呈现到 gpu** ，负责将绘图调用提交到 gpu。</span><span class="sxs-lookup"><span data-stu-id="120db-125">**Render Thread - CPU to GPU** - Responsible for submitting your draw calls to the GPU.</span></span> <span data-ttu-id="120db-126">当应用程序想要呈现某个对象（如多维数据集或模型）时，此线程会向 GPU 发送请求以执行操作。</span><span class="sxs-lookup"><span data-stu-id="120db-126">When your app wants to render an object such as a cube or model, this thread sends a request to the GPU to do the operations.</span></span>
3. <span data-ttu-id="120db-127">**GPU** -最常见的情况是处理应用程序的图形管道，以将3d 数据 (模型、纹理等) 转换为像素。</span><span class="sxs-lookup"><span data-stu-id="120db-127">**GPU** - Most commonly handles the graphics pipeline of your application to transform 3D data (models, textures, and so on) into pixels.</span></span> <span data-ttu-id="120db-128">它最终会生成一个要提交到设备屏幕的二维图像。</span><span class="sxs-lookup"><span data-stu-id="120db-128">It ultimately produces a 2D image to submit to your device's screen.</span></span>

![帧的生存期](images/lifetime-of-a-frame.png)

<span data-ttu-id="120db-130">通常情况下，HoloLens 应用程序将被绑定到 GPU，但并不总是如此。</span><span class="sxs-lookup"><span data-stu-id="120db-130">Generally, HoloLens applications will be GPU bound, but not always.</span></span> <span data-ttu-id="120db-131">使用下面的工具和技术来了解你的特定应用程序的瓶颈所在。</span><span class="sxs-lookup"><span data-stu-id="120db-131">Use the tools and techniques below to understand where your particular app is bottlenecked.</span></span>

## <a name="how-to-analyze-your-application"></a><span data-ttu-id="120db-132">如何分析应用程序</span><span class="sxs-lookup"><span data-stu-id="120db-132">How to analyze your application</span></span>

<span data-ttu-id="120db-133">有许多工具可让你了解混合现实应用程序的性能配置文件和潜在瓶颈。</span><span class="sxs-lookup"><span data-stu-id="120db-133">There are many tools that allow you to understand the performance profile and potential bottlenecks in your mixed reality application.</span></span> 

<span data-ttu-id="120db-134">下面是一些常用工具，可帮助你收集应用程序的深入分析信息：</span><span class="sxs-lookup"><span data-stu-id="120db-134">Below are some common tools to help you gather deep profiling information for your application:</span></span>
- [<span data-ttu-id="120db-135">Intel 图形性能分析器</span><span class="sxs-lookup"><span data-stu-id="120db-135">Intel Graphics Performance Analyzers</span></span>](https://software.intel.com/gpa)
- [<span data-ttu-id="120db-136">Visual Studio 图形调试器</span><span class="sxs-lookup"><span data-stu-id="120db-136">Visual Studio Graphics Debuggers</span></span>](/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [<span data-ttu-id="120db-137">Unity 探查器</span><span class="sxs-lookup"><span data-stu-id="120db-137">Unity Profiler</span></span>](https://docs.unity3d.com/Manual/Profiler.html)
- [<span data-ttu-id="120db-138">Unity 框架调试器</span><span class="sxs-lookup"><span data-stu-id="120db-138">Unity Frame Debugger</span></span>](https://docs.unity3d.com/Manual/FrameDebugger.html)
- [<span data-ttu-id="120db-139">Unreal Insights</span><span class="sxs-lookup"><span data-stu-id="120db-139">Unreal Insights</span></span>](../unreal/unreal-insights.md)
- [<span data-ttu-id="120db-140">PIX</span><span class="sxs-lookup"><span data-stu-id="120db-140">PIX</span></span>](https://devblogs.microsoft.com/pix/)
- [<span data-ttu-id="120db-141">Unreal 中的 GPU Pofiling</span><span class="sxs-lookup"><span data-stu-id="120db-141">GPU Pofiling in Unreal</span></span>](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/GPU/index.html)

### <a name="how-to-profile-in-any-environment"></a><span data-ttu-id="120db-142">如何在任何环境中进行分析</span><span class="sxs-lookup"><span data-stu-id="120db-142">How to profile in any environment</span></span>

<span data-ttu-id="120db-143">确定应用是 GPU 还是 CPU 限制的一种方法是降低呈现器目标输出的分辨率。</span><span class="sxs-lookup"><span data-stu-id="120db-143">One way to determine if your app is GPU or CPU bound is to lower the resolution of the render target output.</span></span> <span data-ttu-id="120db-144">通过减少要计算的像素数，你可以减少 GPU 负载。</span><span class="sxs-lookup"><span data-stu-id="120db-144">By reducing the number of pixels to calculate, you'll reduce your GPU load.</span></span> <span data-ttu-id="120db-145">设备将呈现为一个较小的纹理，然后显示一个示例，显示最终图像。</span><span class="sxs-lookup"><span data-stu-id="120db-145">The device will render to a smaller texture, then up-sample to display your final image.</span></span>

<span data-ttu-id="120db-146">降低呈现分辨率后，如果：</span><span class="sxs-lookup"><span data-stu-id="120db-146">After lowering rendering resolution, if:</span></span>
1) <span data-ttu-id="120db-147">应用程序的帧速率增加，则可能 **会\*\*\*\*绑定 GPU**</span><span class="sxs-lookup"><span data-stu-id="120db-147">Application framerate **increases**, then you're likely **GPU Bound**</span></span>
1) <span data-ttu-id="120db-148">应用程序的以帧速率为 **变化**，则可能是 **CPU 已绑定**</span><span class="sxs-lookup"><span data-stu-id="120db-148">Application framerate **unchanged**, then you're likely **CPU Bound**</span></span>

>[!NOTE]
><span data-ttu-id="120db-149">Unity 提供了在运行时通过 *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性轻松修改应用程序的呈现目标解析的能力。</span><span class="sxs-lookup"><span data-stu-id="120db-149">Unity provides the ability to easily modify the render target resolution of your application at runtime through the *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property.</span></span> <span data-ttu-id="120db-150">设备上提供的最终映像具有固定的分辨率。</span><span class="sxs-lookup"><span data-stu-id="120db-150">The final image presented on device has a fixed resolution.</span></span> <span data-ttu-id="120db-151">平台将采样低分辨率输出，以生成更高分辨率的图像，以便在显示时呈现。</span><span class="sxs-lookup"><span data-stu-id="120db-151">The platform will sample the lower resolution output to build a higher resolution image for rendering on displays.</span></span> 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a><span data-ttu-id="120db-152">如何改进应用程序</span><span class="sxs-lookup"><span data-stu-id="120db-152">How to improve your application</span></span>

### <a name="cpu-performance-recommendations"></a><span data-ttu-id="120db-153">CPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="120db-153">CPU performance recommendations</span></span>

<span data-ttu-id="120db-154">通常，在 CPU 上混合现实应用程序中的大部分工作都涉及到执行场景的 "模拟" 和处理应用程序逻辑。</span><span class="sxs-lookup"><span data-stu-id="120db-154">Generally, most work in a mixed reality application on the CPU involves doing the "simulation" of the scene and processing your application logic.</span></span> <span data-ttu-id="120db-155">以下区域用于优化：</span><span class="sxs-lookup"><span data-stu-id="120db-155">The following areas are targeted for optimization:</span></span>

- <span data-ttu-id="120db-156">动画</span><span class="sxs-lookup"><span data-stu-id="120db-156">Animations</span></span>
- <span data-ttu-id="120db-157">物理</span><span class="sxs-lookup"><span data-stu-id="120db-157">Physics</span></span>
- <span data-ttu-id="120db-158">内存分配</span><span class="sxs-lookup"><span data-stu-id="120db-158">Memory allocations</span></span>
- <span data-ttu-id="120db-159">复杂算法 (即</span><span class="sxs-lookup"><span data-stu-id="120db-159">Complex algorithms (i.e</span></span> <span data-ttu-id="120db-160">反向运动，路径查找) </span><span class="sxs-lookup"><span data-stu-id="120db-160">inverse kinematics, path-finding)</span></span>

### <a name="gpu-performance-recommendations"></a><span data-ttu-id="120db-161">GPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="120db-161">GPU performance recommendations</span></span>

#### <a name="understanding-bandwidth-vs-fill-rate"></a><span data-ttu-id="120db-162">了解带宽与填充速率</span><span class="sxs-lookup"><span data-stu-id="120db-162">Understanding bandwidth vs. fill rate</span></span>
<span data-ttu-id="120db-163">在 GPU 上呈现帧时，应用程序可以按内存带宽或填充速率进行绑定。</span><span class="sxs-lookup"><span data-stu-id="120db-163">When rendering a frame on the GPU, an application is either bound by memory bandwidth or fill rate.</span></span>

- <span data-ttu-id="120db-164">**内存带宽** 是 GPU 可从内存执行读取和写入操作的速率</span><span class="sxs-lookup"><span data-stu-id="120db-164">**Memory bandwidth** is the rate of reads and writes the GPU can do from memory</span></span>
    - <span data-ttu-id="120db-165">若要确定带宽限制，请降低纹理质量并检查帧速率是否已提高。</span><span class="sxs-lookup"><span data-stu-id="120db-165">To identify bandwidth limitations, reduce texture quality and check if the framerate has improved.</span></span>
    - <span data-ttu-id="120db-166">在 Unity 中，在 "**编辑**   >  **项目设置**  >  **[质量" 设置](https://docs.unity3d.com/Manual/class-QualitySettings.html)** 中更改纹理质量。</span><span class="sxs-lookup"><span data-stu-id="120db-166">In Unity, change **Texture Quality** in **Edit** > **Project Settings** > **[Quality Settings](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.</span></span>
- <span data-ttu-id="120db-167">**填充速率** 是指每秒可以通过 GPU 绘制的像素。</span><span class="sxs-lookup"><span data-stu-id="120db-167">**Fill rate** refers to the pixels that can be drawn per second by the GPU.</span></span>
    - <span data-ttu-id="120db-168">若要确定填充速率限制，请降低显示分辨率，并检查是否改进了帧速率。</span><span class="sxs-lookup"><span data-stu-id="120db-168">To identify fill rate limitations, lower the display resolution and check if framerate improved.</span></span> 
    - <span data-ttu-id="120db-169">在 Unity 中，使用  *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性</span><span class="sxs-lookup"><span data-stu-id="120db-169">In Unity, use the  *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property</span></span>

<span data-ttu-id="120db-170">内存带宽一般涉及优化到以下任一操作：</span><span class="sxs-lookup"><span data-stu-id="120db-170">Memory bandwidth generally involves optimizations to either:</span></span>
1) <span data-ttu-id="120db-171">更低的纹理分辨率</span><span class="sxs-lookup"><span data-stu-id="120db-171">Lower texture resolutions</span></span>
2) <span data-ttu-id="120db-172">使用更少纹理 (法线、镜面等) </span><span class="sxs-lookup"><span data-stu-id="120db-172">Use fewer textures (normals, specular, and so on)</span></span>

<span data-ttu-id="120db-173">填充速率侧重于减少需要为最终呈现的像素计算的操作的数量，包括：</span><span class="sxs-lookup"><span data-stu-id="120db-173">Fill rate is focused on reducing the number of operations that need to be computed for a final rendered pixel, including:</span></span>
1) <span data-ttu-id="120db-174">要呈现/处理的对象数</span><span class="sxs-lookup"><span data-stu-id="120db-174">Number of objects to render/process</span></span>
2) <span data-ttu-id="120db-175">每个着色器的操作数</span><span class="sxs-lookup"><span data-stu-id="120db-175">Number of operations per shader</span></span>
3) <span data-ttu-id="120db-176">最终结果 (几何着色器、后处理效果等的 GPU 阶段数) </span><span class="sxs-lookup"><span data-stu-id="120db-176">Number of GPU stages to final result (geometry shaders, post-processing effects, and so on)</span></span>
4) <span data-ttu-id="120db-177">显示分辨率 (呈现的像素数) </span><span class="sxs-lookup"><span data-stu-id="120db-177">Number of pixels to render (display resolution)</span></span>

#### <a name="reduce-polygon-count"></a><span data-ttu-id="120db-178">减少多边形计数</span><span class="sxs-lookup"><span data-stu-id="120db-178">Reduce polygon count</span></span>

<span data-ttu-id="120db-179">较大的多边形计数会导致更多的 GPU 操作，因此减少场景中 [的多边形数量](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) 会减少渲染时间。</span><span class="sxs-lookup"><span data-stu-id="120db-179">Higher polygon counts result in more operations for the GPU, so [reducing the number of polygons](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) in your scene reduces the render time.</span></span> <span data-ttu-id="120db-180">还有其他一些因素会使几何变得昂贵，但多边形计数是确定呈现场景所需的工作量的最简单指标。</span><span class="sxs-lookup"><span data-stu-id="120db-180">There are other factors that make shading the geometry expensive, but polygon count is the simplest metric to determine how much work it will take to render a scene.</span></span>

#### <a name="limit-overdraw"></a><span data-ttu-id="120db-181">限制过度绘制</span><span class="sxs-lookup"><span data-stu-id="120db-181">Limit overdraw</span></span>

<span data-ttu-id="120db-182">当显示多个对象，但在屏幕上未显示过度绘制（因为它们已被 occluding 对象隐藏）时，会发生高。</span><span class="sxs-lookup"><span data-stu-id="120db-182">High overdraw occurs when multiple objects are rendered but not shown on screen as they're hidden by an occluding object.</span></span> <span data-ttu-id="120db-183">想象一下，看看有对象后面的墙。</span><span class="sxs-lookup"><span data-stu-id="120db-183">Imagine looking at a wall that has objects behind it.</span></span> <span data-ttu-id="120db-184">所有几何都将进行处理以便呈现，但只需呈现不透明的墙壁，这将导致不必要的操作。</span><span class="sxs-lookup"><span data-stu-id="120db-184">All of the geometry would be processed for rendering, but only the opaque wall needs to be rendered, which results in unnecessary operations.</span></span>

#### <a name="shaders"></a><span data-ttu-id="120db-185">着色器</span><span class="sxs-lookup"><span data-stu-id="120db-185">Shaders</span></span>

<span data-ttu-id="120db-186">着色器是在 GPU 上运行的小程序，执行以下两个重要步骤：</span><span class="sxs-lookup"><span data-stu-id="120db-186">Shaders are small programs that run on the GPU and do two important steps in rendering:</span></span>
1) <span data-ttu-id="120db-187">确定哪些顶点应该绘制在顶点着色器 (的哪个顶点) </span><span class="sxs-lookup"><span data-stu-id="120db-187">Determining which vertices should be drawn and where they are in screen space (the Vertex shader)</span></span>
    - <span data-ttu-id="120db-188">对于每个网格，顶点着色器都按顶点执行。</span><span class="sxs-lookup"><span data-stu-id="120db-188">The Vertex shader is executed per vertex for every mesh.</span></span>
2) <span data-ttu-id="120db-189">确定像素着色器 (的每个像素的颜色) </span><span class="sxs-lookup"><span data-stu-id="120db-189">Determining the color of each pixel (the Pixel shader)</span></span>
    - <span data-ttu-id="120db-190">像素着色器按每个像素执行，并由几何图形呈现给目标呈现纹理。</span><span class="sxs-lookup"><span data-stu-id="120db-190">The Pixel shader is executed per pixel and rendered by the geometry to the target render texture.</span></span>

<span data-ttu-id="120db-191">通常，着色器会执行许多转换和照明计算。</span><span class="sxs-lookup"><span data-stu-id="120db-191">Typically, shaders do many transformations and lighting calculations.</span></span> <span data-ttu-id="120db-192">尽管复杂的照明模型、阴影和其他操作可能会产生极好的结果，但它们也具有价格。</span><span class="sxs-lookup"><span data-stu-id="120db-192">Although complex lighting models, shadows, and other operations can generate fantastic results, they also come with a price.</span></span> <span data-ttu-id="120db-193">减少着色器中计算的操作数可以极大地减少 GPU 每帧所需的工作量。</span><span class="sxs-lookup"><span data-stu-id="120db-193">Reducing the number of operations computed in shaders can greatly reduce the work needed for the GPU per frame.</span></span>

##### <a name="shader-coding-recommendations"></a><span data-ttu-id="120db-194">着色器编码建议</span><span class="sxs-lookup"><span data-stu-id="120db-194">Shader coding recommendations</span></span>

- <span data-ttu-id="120db-195">尽可能使用双线性筛选</span><span class="sxs-lookup"><span data-stu-id="120db-195">Use bilinear filtering, whenever possible</span></span>
- <span data-ttu-id="120db-196">重新排列表达式以使用 MAD 内部函数执行相乘并同时添加</span><span class="sxs-lookup"><span data-stu-id="120db-196">Rearrange expressions to use MAD intrinsics to do a multiply and an add at the same time</span></span>
- <span data-ttu-id="120db-197">在 CPU 上尽可能 Precalculate，并将其作为常量传递给材料</span><span class="sxs-lookup"><span data-stu-id="120db-197">Precalculate as much as possible on the CPU and pass as constants to the material</span></span>
- <span data-ttu-id="120db-198">**优选从像素着色器移动到顶点着色器的操作**</span><span class="sxs-lookup"><span data-stu-id="120db-198">**Favor moving operations from the pixel shader to the vertex shader**</span></span>
    - <span data-ttu-id="120db-199">通常，顶点的数目要小于 (720p 的像素数为921600像素，1080p 为2073600像素，依此类推) </span><span class="sxs-lookup"><span data-stu-id="120db-199">Generally, the number of vertices is much smaller than the number of pixels (720p is 921,600 pixels, 1080p is 2,073,600 pixels, and so on)</span></span>

#### <a name="remove-gpu-stages"></a><span data-ttu-id="120db-200">删除 GPU 阶段</span><span class="sxs-lookup"><span data-stu-id="120db-200">Remove GPU stages</span></span>

<span data-ttu-id="120db-201">后期处理效果可能比较昂贵并增加应用程序的填充率，包括诸如 MSAA 这样的抗锯齿技术。</span><span class="sxs-lookup"><span data-stu-id="120db-201">Post-processing effects can be expensive and increase the fill rate of your application, including anti-aliasing techniques like MSAA.</span></span> <span data-ttu-id="120db-202">在 HoloLens 上，我们建议避免使用这些技术和其他着色器阶段，如几何、球面和计算着色器。</span><span class="sxs-lookup"><span data-stu-id="120db-202">On HoloLens, we recommended avoiding these techniques and additional shader stages such as geometry, hull, and compute shaders.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="120db-203">内存建议</span><span class="sxs-lookup"><span data-stu-id="120db-203">Memory recommendations</span></span>

<span data-ttu-id="120db-204">过多的内存分配和释放操作可能导致性能不一致、冻结帧以及其他不利行为。</span><span class="sxs-lookup"><span data-stu-id="120db-204">Excessive memory allocation and deallocation operations can result in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="120db-205">在 Unity 中进行开发时，了解内存的注意事项尤其重要，因为内存管理由垃圾回收器控制。</span><span class="sxs-lookup"><span data-stu-id="120db-205">It's especially important to understand memory considerations when developing in Unity, since memory management is controlled by the garbage collector.</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="120db-206">对象池</span><span class="sxs-lookup"><span data-stu-id="120db-206">Object pooling</span></span>

<span data-ttu-id="120db-207">对象池是一种常用技术，可降低对象的连续分配和释放的成本。</span><span class="sxs-lookup"><span data-stu-id="120db-207">Object pooling is a popular technique to reduce the cost of continuous allocations and deallocations of objects.</span></span> <span data-ttu-id="120db-208">此技术是通过以下方式实现的：分配一个由相同对象构成的较大池并重复使用此池中非活动的可用实例，而不是在各个时间内不断生成和销毁对象。</span><span class="sxs-lookup"><span data-stu-id="120db-208">This is done by allocating a large pool of identical objects and reusing inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="120db-209">对象池非常适合应用中生存期可变的可重用组件。</span><span class="sxs-lookup"><span data-stu-id="120db-209">Object pools are great for reuseable components that have variable lifetime during an app.</span></span>

## <a name="see-also"></a><span data-ttu-id="120db-210">另请参阅</span><span class="sxs-lookup"><span data-stu-id="120db-210">See also</span></span>
- [<span data-ttu-id="120db-211">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="120db-211">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
- [<span data-ttu-id="120db-212">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="120db-212">Recommended settings for Unity</span></span>](../unity/recommended-settings-for-unity.md)
- [<span data-ttu-id="120db-213">针对 Unreal 的性能建议</span><span class="sxs-lookup"><span data-stu-id="120db-213">Performance recommendations for Unreal</span></span>](../unreal/performance-recommendations-for-unreal.md)
- [<span data-ttu-id="120db-214">Unreal 中的材料建议</span><span class="sxs-lookup"><span data-stu-id="120db-214">Material recommendations in Unreal</span></span>](../unreal/unreal-materials.md)
- [<span data-ttu-id="120db-215">优化3D 模型</span><span class="sxs-lookup"><span data-stu-id="120db-215">Optimize 3D models</span></span>](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [<span data-ttu-id="120db-216">转换和优化实时3D 模型的最佳做法</span><span class="sxs-lookup"><span data-stu-id="120db-216">Best practices for converting and optimizing real-time 3D Models</span></span>](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)
- [<span data-ttu-id="120db-217">适用于 Unreal 的艺术家和设计人员性能准则</span><span class="sxs-lookup"><span data-stu-id="120db-217">Performance guidelines for artists and designers for Unreal</span></span>](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/Guidelines/index.html)
- [<span data-ttu-id="120db-218">Unreal 的 VR 最佳实践</span><span class="sxs-lookup"><span data-stu-id="120db-218">VR best practices for Unreal</span></span>](https://docs.unrealengine.com/en-US/SharingAndReleasing/XRDevelopment/VR/DevelopVR/ContentSetup/index.html)
