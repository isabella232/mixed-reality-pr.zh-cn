---
title: 性能
description: 用于了解和调整 MRTK 中的预格式的文档。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 6c8e060af585d7994774ea0bb575b6e5172b9558
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281760"
---
# <a name="performance"></a><span data-ttu-id="92d36-104">性能</span><span class="sxs-lookup"><span data-stu-id="92d36-104">Performance</span></span>

## <a name="getting-started"></a><span data-ttu-id="92d36-105">入门</span><span class="sxs-lookup"><span data-stu-id="92d36-105">Getting started</span></span>

<span data-ttu-id="92d36-106">使性能合理化的最简单方法是帧速率或应用程序每秒呈现图像次数。</span><span class="sxs-lookup"><span data-stu-id="92d36-106">The easiest way to rationalize performance is via framerate or how many times your application can render an image per second.</span></span> <span data-ttu-id="92d36-107">必须满足目标帧速率，如目标平台所述， (帧速率</span><span class="sxs-lookup"><span data-stu-id="92d36-107">It is important to meet the target framerate, as outlined by the platform being targeted (i.e</span></span> <span data-ttu-id="92d36-108">[](/windows/mixed-reality/understanding-performance-for-mixed-reality) [Windows Mixed Reality、Oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)等) 。</span><span class="sxs-lookup"><span data-stu-id="92d36-108">[Windows Mixed Reality](/windows/mixed-reality/understanding-performance-for-mixed-reality), [Oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/), etc).</span></span> <span data-ttu-id="92d36-109">例如，在HoloLens，目标帧速率为 60 FPS。</span><span class="sxs-lookup"><span data-stu-id="92d36-109">For example, on HoloLens, the target framerate is 60 FPS.</span></span> <span data-ttu-id="92d36-110">帧速率较低的应用程序可能会导致用户体验变长，例如全息影像稳定化、[](../performance/hologram-stabilization.md)世界跟踪、手部跟踪等。</span><span class="sxs-lookup"><span data-stu-id="92d36-110">Low framerate applications can result in deteriorated user experiences such as worsened [hologram stabilization](../performance/hologram-stabilization.md), world tracking, hand tracking, and more.</span></span> <span data-ttu-id="92d36-111">为了帮助开发人员跟踪并实现质量帧速率，混合现实Toolkit提供各种工具和脚本。</span><span class="sxs-lookup"><span data-stu-id="92d36-111">To help developers track and achieve quality framerate, the Mixed Reality Toolkit provides a variety of tools and scripts.</span></span>

### <a name="visual-profiler"></a><span data-ttu-id="92d36-112">可视化探查器</span><span class="sxs-lookup"><span data-stu-id="92d36-112">Visual profiler</span></span>

<span data-ttu-id="92d36-113">若要在开发生存期内持续跟踪性能，强烈建议在运行帧速率视觉对象时始终显示&调试应用程序。</span><span class="sxs-lookup"><span data-stu-id="92d36-113">To continuously track performance over the lifetime of development, it is highly recommended to always show a framerate visual while running & debugging an application.</span></span> <span data-ttu-id="92d36-114">混合现实Toolkit提供了[Visual Profiler](../features/diagnostics/using-visual-profiler.md)诊断工具，该工具提供有关应用程序视图中当前 FPS 和内存使用情况实时信息。</span><span class="sxs-lookup"><span data-stu-id="92d36-114">The Mixed Reality Toolkit provides the [Visual Profiler](../features/diagnostics/using-visual-profiler.md) diagnostic tool which gives real-time information about the current FPS and memory usage in application view.</span></span> <span data-ttu-id="92d36-115">可以通过"诊断系统"配置 Visual Profiler，设置"MRTK[配置文件检查](../features/diagnostics/diagnostics-system-getting-started.md)[器"下](../configuration/mixed-reality-configuration-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="92d36-115">The Visual Profiler can be configured via the [Diagnostics System Settings](../features/diagnostics/diagnostics-system-getting-started.md) under the [MRTK Profiles Inspector](../configuration/mixed-reality-configuration-guide.md).</span></span>

<span data-ttu-id="92d36-116">此外，在设备上运行时，使用 Visual Profiler 跟踪帧速率尤为重要，而不是在 Unity 编辑器或仿真器中运行。</span><span class="sxs-lookup"><span data-stu-id="92d36-116">Furthermore, it is particularly important to utilize the Visual Profiler to track framerate when running on the device as opposed to running in Unity editor or an emulator.</span></span> <span data-ttu-id="92d36-117">使用发布配置版本 在设备上运行时，将描述最 [准确的性能结果](/visualstudio/debugger/how-to-set-debug-and-release-configurations?preserve-view=true&view=vs-2019)。</span><span class="sxs-lookup"><span data-stu-id="92d36-117">The most accurate performance results will be depicted when running on the device with [Release configuration builds](/visualstudio/debugger/how-to-set-debug-and-release-configurations?preserve-view=true&view=vs-2019).</span></span>

> [!NOTE]
> <span data-ttu-id="92d36-118">如果生成时Windows Mixed Reality，则使用 MASTER[配置生成进行部署](/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)</span><span class="sxs-lookup"><span data-stu-id="92d36-118">If building for Windows Mixed Reality, deploy with [MASTER configuration builds](/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)</span></span>

![Visual Profiler 接口](../features/images/Diagnostics/VisualProfiler.png)

### <a name="optimize-window"></a><span data-ttu-id="92d36-120">优化窗口</span><span class="sxs-lookup"><span data-stu-id="92d36-120">Optimize window</span></span>

<span data-ttu-id="92d36-121">[MRTK 优化窗口](../features/tools/optimize-window.md)提供了信息和自动化工具，以帮助混合现实开发人员设置其环境，以便获得最佳的性能结果，并确定其场景中的潜在瓶颈&资产。</span><span class="sxs-lookup"><span data-stu-id="92d36-121">The [MRTK Optimize Window](../features/tools/optimize-window.md) offers information and automation tools to help mixed reality developers set up their environment for the best performing results and identify potential bottlenecks in their scene & assets.</span></span> <span data-ttu-id="92d36-122">Unity 中的某些关键配置可以帮助为混合现实项目提供大幅优化的结果。</span><span class="sxs-lookup"><span data-stu-id="92d36-122">Certain key configurations in Unity can help deliver substantially more optimized results for mixed reality projects.</span></span>

<span data-ttu-id="92d36-123">通常，这些设置涉及非常适合混合现实呈现配置。</span><span class="sxs-lookup"><span data-stu-id="92d36-123">Generally, these settings involve rendering configurations that are ideal for mixed reality.</span></span> <span data-ttu-id="92d36-124">与传统 3D 图形开发相比，混合现实应用程序是唯一的，因为有两 (屏幕，即</span><span class="sxs-lookup"><span data-stu-id="92d36-124">Mixed reality applications are unique compared to traditional 3D graphics development in that there are two screens (i.e</span></span> <span data-ttu-id="92d36-125">两只眼睛) 整个场景呈现。</span><span class="sxs-lookup"><span data-stu-id="92d36-125">two eyes) to render for the entire scene.</span></span>

<span data-ttu-id="92d36-126">可以通过利用 MRTK 优化窗口在 Unity 项目中自动配置下面引用的建议设置。</span><span class="sxs-lookup"><span data-stu-id="92d36-126">The recommended settings referenced below can be auto-configured in a Unity project by leveraging the MRTK Optimize Window.</span></span>

![MRTK 优化窗口设置](../features/images/performance/OptimizeWindow_Settings.png)

### <a name="unity-profiler"></a><span data-ttu-id="92d36-128">Unity Profiler</span><span class="sxs-lookup"><span data-stu-id="92d36-128">Unity Profiler</span></span>

<span data-ttu-id="92d36-129">[Unity Profiler](https://docs.unity3d.com/Manual/ProfilerWindow.html)是一种有用的工具，可用于在帧级别调查应用程序性能的详细信息。</span><span class="sxs-lookup"><span data-stu-id="92d36-129">The [Unity Profiler](https://docs.unity3d.com/Manual/ProfilerWindow.html) is a useful tool to investigate details of application performance at a frame-by-frame level.</span></span>

#### <a name="time-spent-on-the-cpu"></a><span data-ttu-id="92d36-130">CPU 上花费的时间</span><span class="sxs-lookup"><span data-stu-id="92d36-130">Time spent on the CPU</span></span>

![示例 Unity Profiler Graph](../features/images/performance/UnityProfilerGraph.png)

<span data-ttu-id="92d36-132">为了保持舒适帧速率 (每秒 60 帧) ，应用程序需要实现最大帧时间 16.6 毫秒的 CPU 时间。</span><span class="sxs-lookup"><span data-stu-id="92d36-132">To maintain comfortable frame rates (typically 60 frames per second), applications need to achieve a maximum frame time of 16.6 milliseconds of CPU time.</span></span> <span data-ttu-id="92d36-133">为了帮助确定 MRTK 功能的成本，Microsoft Mixed Reality Toolkit包含一个标记，用于每个帧 (代码) 内循环。</span><span class="sxs-lookup"><span data-stu-id="92d36-133">To help identify the cost of MRTK functionality, the Microsoft Mixed Reality Toolkit contains a markers for inner loop (per frame) code paths.</span></span> <span data-ttu-id="92d36-134">这些标记使用以下格式来帮助了解使用的特定功能：</span><span class="sxs-lookup"><span data-stu-id="92d36-134">These markers use the following format, to assist in understanding the specific functionality being utilized:</span></span>

```
[MRTK] className.methodName
```

> [!Note]
> <span data-ttu-id="92d36-135">方法名称后可能有其他数据。</span><span class="sxs-lookup"><span data-stu-id="92d36-135">There may be additional data following the method name.</span></span> <span data-ttu-id="92d36-136">这用于标识有条件执行的、可能成本高昂的功能，对应用程序代码进行少量更改可能会避免这些功能。</span><span class="sxs-lookup"><span data-stu-id="92d36-136">This is used to identify conditionally executed, potentially expensive functionality that may be avoided by small changes to application code.</span></span>

![示例 Unity Profiler 层次结构](../features/images/performance/UnityProfilerHierarchy.png)

<span data-ttu-id="92d36-138">本示例已扩展层次结构，以显示在分析帧期间 WindowsMixedRealityArticulatedHand 类的 UpdateHandData 方法消耗 0.44 毫秒的 CPU 时间。</span><span class="sxs-lookup"><span data-stu-id="92d36-138">In this example, the hierarchy has been expanded to show that the UpdateHandData method of WindowsMixedRealityArticulatedHand class is consuming 0.44 ms of CPU time during the frame being analyzed.</span></span> <span data-ttu-id="92d36-139">此数据可用于帮助确定性能问题是与应用程序代码相关还是与系统中其他位置相关。</span><span class="sxs-lookup"><span data-stu-id="92d36-139">This data can be used to help determine if a performance issue is related to application code or from elsewhere in the system.</span></span>

<span data-ttu-id="92d36-140">强烈建议开发人员以类似的方式检测应用程序代码。</span><span class="sxs-lookup"><span data-stu-id="92d36-140">It is highly recommended that developers instrument application code in a similar fashion.</span></span> <span data-ttu-id="92d36-141">应用程序代码检测的主要关注区域位于事件处理程序中，因为这些方法在引发事件时向 MRTK 更新循环收费。</span><span class="sxs-lookup"><span data-stu-id="92d36-141">Primary areas of focus for application code instrumentation is within event handlers as these methods are charged to the MRTK update loop as events are raised.</span></span> <span data-ttu-id="92d36-142">MRTK 更新循环中的帧时间过长可能表示事件处理程序方法中的代码成本高昂。</span><span class="sxs-lookup"><span data-stu-id="92d36-142">High frame times within the MRTK update loop can be indicative of expensive code in event handler methods.</span></span>

## <a name="recommended-settings-for-unity"></a><span data-ttu-id="92d36-143">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="92d36-143">Recommended settings for Unity</span></span>

### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="92d36-144">Single-Pass实例呈现</span><span class="sxs-lookup"><span data-stu-id="92d36-144">Single-Pass Instanced rendering</span></span>

<span data-ttu-id="92d36-145">Unity 中 XR 的默认呈现配置是 [多传递](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html)。</span><span class="sxs-lookup"><span data-stu-id="92d36-145">The default rendering configuration for XR in Unity is [Multi-pass](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html).</span></span> <span data-ttu-id="92d36-146">此设置指示 Unity 执行整个呈现管道两次，每个眼睛执行一次。</span><span class="sxs-lookup"><span data-stu-id="92d36-146">This setting instructs Unity to execute the entire render pipeline twice, once for each eye.</span></span> <span data-ttu-id="92d36-147">这可以通过改为选择"单 [通道实例呈现"进行优化](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 。</span><span class="sxs-lookup"><span data-stu-id="92d36-147">This can be optimized by selecting [Single Pass Instanced rendering](https://docs.unity3d.com/Manual/SinglePassInstancing.html) instead.</span></span> <span data-ttu-id="92d36-148">此配置利用 [呈现器](https://en.wikipedia.org/wiki/Multiple_Render_Targets) 目标数组，能够执行单个绘制调用，该调用将实例放入每个眼睛 [的适当](https://en.wikipedia.org/wiki/Render_Target) 呈现目标。</span><span class="sxs-lookup"><span data-stu-id="92d36-148">This configuration leverages [render target arrays](https://en.wikipedia.org/wiki/Multiple_Render_Targets) to be able to perform a single draw call that instances into the appropriate [render target](https://en.wikipedia.org/wiki/Render_Target) for each eye.</span></span> <span data-ttu-id="92d36-149">此外，此模式允许在单个呈现管道执行中完成所有呈现。</span><span class="sxs-lookup"><span data-stu-id="92d36-149">Furthermore, this mode allows all rendering to be done in a single execution of the rendering pipeline.</span></span> <span data-ttu-id="92d36-150">因此，选择"单次传递实例呈现"作为混合现实应用程序的呈现路径可以在 CPU 和 GPU 上节省大量 [&，](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) 这是推荐的呈现配置。</span><span class="sxs-lookup"><span data-stu-id="92d36-150">Thus, selecting Single Pass Instanced rendering as the rendering path for a mixed reality application can [save substantial time on both the CPU & GPU](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) and is the recommended rendering configuration.</span></span>

<span data-ttu-id="92d36-151">但是，若要针对每个眼睛发出每个网格的单个绘图调用，所有着色器都必须支持 [GPU](https://docs.unity3d.com/Manual/GPUInstancing.html) 实例化。</span><span class="sxs-lookup"><span data-stu-id="92d36-151">However, in order to issue a single draw call for each mesh to each eye, [GPU instancing](https://docs.unity3d.com/Manual/GPUInstancing.html) must be supported by all shaders.</span></span> <span data-ttu-id="92d36-152">实例化允许 GPU 跨两只眼睛多路绘制调用。</span><span class="sxs-lookup"><span data-stu-id="92d36-152">Instancing allows the GPU to multiplex draw calls across both eyes.</span></span> <span data-ttu-id="92d36-153">默认情况下，Unity 内置着色器以及 [MRTK 标准](../features/rendering/mrtk-standard-shader.md) 着色器在着色器代码中包含必要的实例化说明。</span><span class="sxs-lookup"><span data-stu-id="92d36-153">Unity built-in shaders as well as the [MRTK Standard shader](../features/rendering/mrtk-standard-shader.md) by default contain the necessary instancing instructions in shader code.</span></span> <span data-ttu-id="92d36-154">但是，如果为 Unity 编写自定义着色器，可能需要更新这些着色器以支持单通道实例呈现。</span><span class="sxs-lookup"><span data-stu-id="92d36-154">If writing custom shaders though for Unity, these shaders may need to be updated to support Single Pass Instanced rendering.</span></span>

#### <a name="example-code-for-custom-shader"></a>[<span data-ttu-id="92d36-155">自定义着色器的示例代码</span><span class="sxs-lookup"><span data-stu-id="92d36-155">Example Code for Custom Shader</span></span>](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

```
struct appdata
{
    float4 vertex : POSITION;
    float2 uv : TEXCOORD0;

    UNITY_VERTEX_INPUT_INSTANCE_ID //Insert
};

struct v2f
{
    float2 uv : TEXCOORD0;
    float4 vertex : SV_POSITION;

    UNITY_VERTEX_OUTPUT_STEREO //Insert
};

v2f vert (appdata v)
{
    v2f o;

    UNITY_SETUP_INSTANCE_ID(v); //Insert
    UNITY_INITIALIZE_OUTPUT(v2f, o); //Insert
    UNITY_INITIALIZE_VERTEX_OUTPUT_STEREO(o); //Insert

    o.vertex = UnityObjectToClipPos(v.vertex);

    o.uv = v.uv;

    return o;
}
```

### <a name="quality-settings"></a><span data-ttu-id="92d36-156">质量设置</span><span class="sxs-lookup"><span data-stu-id="92d36-156">Quality settings</span></span>

<span data-ttu-id="92d36-157">Unity [提供预设来控制每个](https://docs.unity3d.com/Manual/class-QualitySettings.html) 平台终结点的呈现质量。</span><span class="sxs-lookup"><span data-stu-id="92d36-157">Unity provides [presets to control quality](https://docs.unity3d.com/Manual/class-QualitySettings.html) of rendering for each platform endpoint.</span></span> <span data-ttu-id="92d36-158">这些预设控制可以启用的图形功能，例如阴影、抗锯齿、全局照明等。</span><span class="sxs-lookup"><span data-stu-id="92d36-158">These presets control what graphical features can be enabled such as shadows, anti-aliasing, global illumination, and more.</span></span> <span data-ttu-id="92d36-159">建议降低这些设置，并优化呈现期间执行的计算数。</span><span class="sxs-lookup"><span data-stu-id="92d36-159">It is recommended to lower these settings and optimize the number of calculations performed during rendering.</span></span>

<span data-ttu-id="92d36-160">*步骤 1：* 更新混合现实 Unity 项目以使用 *低质量* 级别设置</span><span class="sxs-lookup"><span data-stu-id="92d36-160">*Step 1:* Update mixed reality Unity projects to use the *Low Quality* level setting</span></span>  
<span data-ttu-id="92d36-161">**编辑**  > **Project 设置，** 然后选择"质量"类别 *>为* UWP 平台选择"低质量"</span><span class="sxs-lookup"><span data-stu-id="92d36-161">**Edit** > **Project Settings**, then select the **Quality** category >  Select *Low Quality* for the UWP Platform</span></span>

<span data-ttu-id="92d36-162">*步骤 2：* 对于每个 Unity 场景文件，请禁用 [实时全局照明](https://docs.unity3d.com/Manual/LightMode-Realtime.html)</span><span class="sxs-lookup"><span data-stu-id="92d36-162">*Step 2:* For every Unity scene file, disable [real-time Global Illumination](https://docs.unity3d.com/Manual/LightMode-Realtime.html)</span></span>  
<span data-ttu-id="92d36-163">**窗口**  > **呈现**  > **照明设置**  > [取消 *选中"实时全球照明"*](https://docs.unity3d.com/Manual/GlobalIllumination.html)</span><span class="sxs-lookup"><span data-stu-id="92d36-163">**Window** > **Rendering** > **Lighting Settings** > [Uncheck *Real-time Global Illumination*](https://docs.unity3d.com/Manual/GlobalIllumination.html)</span></span>

### <a name="depth-buffer-sharing-hololens"></a><span data-ttu-id="92d36-164">深度缓冲区共享 (HoloLens) </span><span class="sxs-lookup"><span data-stu-id="92d36-164">Depth buffer sharing (HoloLens)</span></span>

<span data-ttu-id="92d36-165">如果针对 Windows Mixed Reality 平台（尤其是 HoloLens）进行开发，在 *XR* 设置 启用深度缓冲区共享有助于全息 [影像稳定](../performance/hologram-stabilization.md)。</span><span class="sxs-lookup"><span data-stu-id="92d36-165">If developing for the Windows Mixed Reality platform and in particular HoloLens, enabling *Depth Buffer Sharing* under *XR Settings* can help with [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="92d36-166">但是，深度缓冲区的处理可能会产生性能成本，尤其是在使用 [24 位深度格式 时](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html)。</span><span class="sxs-lookup"><span data-stu-id="92d36-166">However, processing of the depth buffer can incur a performance cost, particularly if using [24-bit depth format](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html).</span></span> <span data-ttu-id="92d36-167">因此， *强烈建议将* 深度缓冲区配置为 16 位精度。</span><span class="sxs-lookup"><span data-stu-id="92d36-167">Thus, it is *highly recommended* to configure the depth buffer to 16-bit precision.</span></span>

<span data-ttu-id="92d36-168">如果[由于位](https://en.wikipedia.org/wiki/Z-fighting)格式较低而发生 z 冲突，请确认所有[](https://docs.unity3d.com/Manual/class-Camera.html)相机的远剪裁平面设置为应用程序可能的最低值。</span><span class="sxs-lookup"><span data-stu-id="92d36-168">If [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) occurs due to the lower bit format, confirm the [far clip plane](https://docs.unity3d.com/Manual/class-Camera.html) of all cameras is set to the lowest possible value for the application.</span></span> <span data-ttu-id="92d36-169">默认情况下，Unity 将远剪裁平面设置为 1000m。</span><span class="sxs-lookup"><span data-stu-id="92d36-169">Unity by default sets a far clip plane of 1000m.</span></span> <span data-ttu-id="92d36-170">在HoloLens，对于大多数应用程序方案，50 米远的剪辑平面通常已足够。</span><span class="sxs-lookup"><span data-stu-id="92d36-170">On HoloLens, a far clip plane of 50m is generally more than enough for most application scenarios.</span></span>

> [!NOTE]
> <span data-ttu-id="92d36-171">如果使用 *16 位* 深度格式 ，则所需的模具缓冲区效果将不起作用，因为 [Unity](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 不会在此设置中创建模具缓冲区。</span><span class="sxs-lookup"><span data-stu-id="92d36-171">If using *16-bit depth format*, stencil buffer required effects will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="92d36-172">相反 *，如果选择 24* 位深度格式，通常会在终结点图形平台上创建一个 8 位模具缓冲区（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="92d36-172">Selecting *24-bit depth format* conversely will generally create an 8-bit stencil buffer, if applicable on the endpoint graphics platform.</span></span>
>
> <span data-ttu-id="92d36-173">如果使用需要模具缓冲区的 [Mask](https://docs.unity3d.com/Manual/script-Mask.html) 组件，请考虑改为使用 [RectMask2D，](https://docs.unity3d.com/Manual/script-RectMask2D.html) 它不需要模具缓冲区，因此可以与 *16* 位深度格式 结合使用。</span><span class="sxs-lookup"><span data-stu-id="92d36-173">If using a [Mask component](https://docs.unity3d.com/Manual/script-Mask.html) which requires the stencil buffer, consider using [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) instead, which does not require the stencil buffer and thus can be used in conjunction with a *16-bit depth format*.</span></span>

> [!NOTE]
> <span data-ttu-id="92d36-174">若要快速确定场景中哪些对象未以可视方式写入深度缓冲区，可以使用 MRTK 配置文件中 [](../configuration/mixed-reality-configuration-guide.md#editor-utilities)"编辑器"设置"呈现 *深度缓冲区*"实用工具。</span><span class="sxs-lookup"><span data-stu-id="92d36-174">To quickly determine which objects in a scene do not write to the depth buffer visually, one can use the [*Render Depth Buffer* utility](../configuration/mixed-reality-configuration-guide.md#editor-utilities) under the *Editor Settings* in the MRTK Configuration profile.</span></span>

### <a name="optimize-mesh-data"></a><span data-ttu-id="92d36-175">优化网格数据</span><span class="sxs-lookup"><span data-stu-id="92d36-175">Optimize Mesh Data</span></span>

<span data-ttu-id="92d36-176">" [优化网格数据](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html) "设置尝试删除应用程序中未使用的顶点属性。</span><span class="sxs-lookup"><span data-stu-id="92d36-176">The [Optimize Mesh Data](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html) settings tries to remove unused vertex attributes within your application.</span></span> <span data-ttu-id="92d36-177">设置通过运行生成中每个网格上每个材料上的每个着色器传递来实现此目标。</span><span class="sxs-lookup"><span data-stu-id="92d36-177">The setting performs this by running over every shader pass in every material that is on every mesh in the build.</span></span> <span data-ttu-id="92d36-178">这适用于游戏数据大小和运行时性能，但可能会极大地阻碍生成时间。</span><span class="sxs-lookup"><span data-stu-id="92d36-178">This is good for game data size and runtime performance but can drastically hinder build times.</span></span>

<span data-ttu-id="92d36-179">建议在开发期间禁用此设置，并创建"主"生成期间重新启用此设置。</span><span class="sxs-lookup"><span data-stu-id="92d36-179">It is recommended to disable this setting during development and re-enable during "Master" build creation.</span></span> <span data-ttu-id="92d36-180">可以在"编辑播放器""其他Project 设置  >    >    >  **优化网格**  >  **设置"下找到设置**。</span><span class="sxs-lookup"><span data-stu-id="92d36-180">The setting can be found under **Edit** > **Project Settings** > **Player** > **Other Settings** > **Optimize Mesh Data**.</span></span>

## <a name="general-recommendations"></a><span data-ttu-id="92d36-181">常规建议</span><span class="sxs-lookup"><span data-stu-id="92d36-181">General recommendations</span></span>

<span data-ttu-id="92d36-182">对于混合现实开发人员来说，性能可能是不明确且不断变化的挑战，使性能合理化的知识范围非常广泛。</span><span class="sxs-lookup"><span data-stu-id="92d36-182">Performance can be an ambiguous and constantly changing challenge for mixed reality developers and the spectrum of knowledge to rationalize performance is vast.</span></span> <span data-ttu-id="92d36-183">不过，对于了解如何实现应用程序的性能，有一些常规建议。</span><span class="sxs-lookup"><span data-stu-id="92d36-183">There are some general recommendations for understanding how to approach performance for an application though.</span></span>

<span data-ttu-id="92d36-184">将应用程序的执行简化为在 *CPU* 或 *GPU* 上运行的片段非常有用，从而确定应用是否受任一组件的约束。</span><span class="sxs-lookup"><span data-stu-id="92d36-184">It is useful to simplify the execution of an application into the pieces that run on the *CPU* or the *GPU* and thus identify whether an app is bounded by either component.</span></span>  <span data-ttu-id="92d36-185">可能同时存在跨处理单元的瓶颈，以及必须仔细调查的一些独特方案。</span><span class="sxs-lookup"><span data-stu-id="92d36-185">There can be bottlenecks that span both processing units and some unique scenarios that have to be carefully investigated.</span></span> <span data-ttu-id="92d36-186">但是，对于入门，可以掌握应用程序执行时间最多的位置。</span><span class="sxs-lookup"><span data-stu-id="92d36-186">However, for getting started, it is good to grasp where an application is executing for the most amount of time.</span></span>

### <a name="gpu-bounded"></a><span data-ttu-id="92d36-187">GPU 边界</span><span class="sxs-lookup"><span data-stu-id="92d36-187">GPU bounded</span></span>

<span data-ttu-id="92d36-188">由于混合现实应用程序的大多数平台都使用立体声[](https://en.wikipedia.org/wiki/Stereoscopy)渲染，因此由于呈现"双宽"屏幕的性质，GPU 绑定很常见。</span><span class="sxs-lookup"><span data-stu-id="92d36-188">Since most platforms for mixed reality applications are utilizing [stereoscopic rendering](https://en.wikipedia.org/wiki/Stereoscopy), it is very common to be GPU-bounded due to the nature of rendering a "double-wide" screen.</span></span> <span data-ttu-id="92d36-189">此外，移动混合现实平台（如 HoloLens 或 Oculus Quest）将受限于移动类 CPU 和 GPU &处理能力。</span><span class="sxs-lookup"><span data-stu-id="92d36-189">Futhermore, mobile mixed reality platforms such as HoloLens or Oculus Quest will be limited by mobile-class CPU & GPU processing power.</span></span>

<span data-ttu-id="92d36-190">专注于 GPU 时，应用程序通常需要完成每个帧的两个重要阶段。</span><span class="sxs-lookup"><span data-stu-id="92d36-190">When focusing on the GPU, there are generally two important stages that an application must complete every frame.</span></span>

1. <span data-ttu-id="92d36-191">执行 [顶点着色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)</span><span class="sxs-lookup"><span data-stu-id="92d36-191">Execute the [vertex shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)</span></span>
2. <span data-ttu-id="92d36-192">执行 [像素着色器 (](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) 也称为片段着色器) </span><span class="sxs-lookup"><span data-stu-id="92d36-192">Execute the [pixel shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) (also known as the fragment shader)</span></span>

<span data-ttu-id="92d36-193">如果不深入了解计算机图形和& [的复杂字段，](https://en.wikipedia.org/wiki/Graphics_pipeline)每个着色器阶段都是一个在 GPU 上运行的程序，用于生成以下内容。</span><span class="sxs-lookup"><span data-stu-id="92d36-193">Without deep diving into the complex field of computer graphics & [rendering pipelines](https://en.wikipedia.org/wiki/Graphics_pipeline), each shader stage is a program that runs on the GPU to produce the following.</span></span>

1. <span data-ttu-id="92d36-194">顶点着色器将网格顶点转换为屏幕空间中的坐标 (即</span><span class="sxs-lookup"><span data-stu-id="92d36-194">Vertex shaders transform mesh vertices to coordinates in screen-space (i.e</span></span> <span data-ttu-id="92d36-195">每个顶点所执行) </span><span class="sxs-lookup"><span data-stu-id="92d36-195">code executed per vertex)</span></span>
2. <span data-ttu-id="92d36-196">像素着色器计算给定像素和网格片段绘制的颜色 (即</span><span class="sxs-lookup"><span data-stu-id="92d36-196">Pixel shaders calculate the color to draw for a given pixel and mesh fragment (i.e</span></span> <span data-ttu-id="92d36-197">代码按像素执行) </span><span class="sxs-lookup"><span data-stu-id="92d36-197">code execute per pixel)</span></span>

<span data-ttu-id="92d36-198">在性能优化方面，通常更希望专注于优化像素着色器中的操作。</span><span class="sxs-lookup"><span data-stu-id="92d36-198">In regards to performance tuning, it is usually more fruitful to focus on optimizing the operations in the pixel shader.</span></span> <span data-ttu-id="92d36-199">应用程序可能只需要绘制一个只有 8 个顶点的立方体。</span><span class="sxs-lookup"><span data-stu-id="92d36-199">An application may only need to draw a cube which will just be 8 vertices.</span></span> <span data-ttu-id="92d36-200">但是，多维数据集占用的屏幕空间可能为数百万像素。</span><span class="sxs-lookup"><span data-stu-id="92d36-200">However, the screen space that cube occupies is likely on the order of millions of pixels.</span></span> <span data-ttu-id="92d36-201">因此，如果像素着色器比顶点着色器减少，则通过使用10个操作降低着色器代码可以节省更多的工作。</span><span class="sxs-lookup"><span data-stu-id="92d36-201">Thus, reducing shader code by say 10 operations can save significantly more work if reduced on the pixel shader than the vertex shader.</span></span>

<span data-ttu-id="92d36-202">这是利用 [MRTK 标准着色器](../features/rendering/mrtk-standard-shader.md) 的主要原因之一，因为在此着色器中，此着色器 & 顶点与 Unity 标准着色器相比，在实现可比较的美观结果时，通常会执行更少的指令。</span><span class="sxs-lookup"><span data-stu-id="92d36-202">This is one of the primary reasons for leveraging the [MRTK Standard shader](../features/rendering/mrtk-standard-shader.md) as this shader generally executes many less instructions per pixel & vertex than the Unity Standard shader while achieving comparable aesthetic results.</span></span>

|    <span data-ttu-id="92d36-203">CPU 优化</span><span class="sxs-lookup"><span data-stu-id="92d36-203">CPU Optimizations</span></span>      |             <span data-ttu-id="92d36-204">GPU 优化</span><span class="sxs-lookup"><span data-stu-id="92d36-204">GPU Optimizations</span></span>              |
|---------------------------|--------------------------------------------|
| <span data-ttu-id="92d36-205">应用模拟逻辑</span><span class="sxs-lookup"><span data-stu-id="92d36-205">App simulation logic</span></span>      | <span data-ttu-id="92d36-206">呈现操作</span><span class="sxs-lookup"><span data-stu-id="92d36-206">Rendering operations</span></span> |
| <span data-ttu-id="92d36-207">简化物理学</span><span class="sxs-lookup"><span data-stu-id="92d36-207">Simplify Physics</span></span>          | <span data-ttu-id="92d36-208">减少光照计算</span><span class="sxs-lookup"><span data-stu-id="92d36-208">Reduce lighting calculations</span></span> |
| <span data-ttu-id="92d36-209">简化动画</span><span class="sxs-lookup"><span data-stu-id="92d36-209">Simplify Animations</span></span>       | <span data-ttu-id="92d36-210">减少绘制对象的 & # 数量</span><span class="sxs-lookup"><span data-stu-id="92d36-210">Reduce polygon count & # of drawable objects</span></span> |
| <span data-ttu-id="92d36-211">管理垃圾回收</span><span class="sxs-lookup"><span data-stu-id="92d36-211">Manage Garbage Collection</span></span> | <span data-ttu-id="92d36-212">减少透明对象的数目</span><span class="sxs-lookup"><span data-stu-id="92d36-212">Reduce # of transparent objects</span></span> |
| <span data-ttu-id="92d36-213">缓存引用</span><span class="sxs-lookup"><span data-stu-id="92d36-213">Cache References</span></span>          | <span data-ttu-id="92d36-214">避免处理后/全屏效果</span><span class="sxs-lookup"><span data-stu-id="92d36-214">Avoid post-processing/full-screen effects</span></span>  |

### <a name="draw-call-instancing"></a><span data-ttu-id="92d36-215">绘制调用实例化</span><span class="sxs-lookup"><span data-stu-id="92d36-215">Draw call instancing</span></span>

<span data-ttu-id="92d36-216">Unity 中最常见的错误之一就是在运行时克隆材料。</span><span class="sxs-lookup"><span data-stu-id="92d36-216">One of the most common mistakes in Unity that reduces performance is cloning materials at runtime.</span></span> <span data-ttu-id="92d36-217">如果 Gameobject 共享相同的材料和/或相同的网格，则可以通过诸如 *[静态批处理](https://docs.unity3d.com/Manual/DrawCallBatching.html)*、 *[动态批处理](https://docs.unity3d.com/Manual/DrawCallBatching.html)* 和 *[GPU 实例](https://docs.unity3d.com/Manual/GPUInstancing.html)* 化之类的技术将其优化成单个绘图调用。</span><span class="sxs-lookup"><span data-stu-id="92d36-217">If GameObjects share the same material and/or are the same mesh, they can be optimized into single draw calls via techniques such as *[static batching](https://docs.unity3d.com/Manual/DrawCallBatching.html)*, *[dynamic batching](https://docs.unity3d.com/Manual/DrawCallBatching.html)*, and *[GPU Instancing](https://docs.unity3d.com/Manual/GPUInstancing.html)*.</span></span> <span data-ttu-id="92d36-218">但是，如果开发人员在运行时修改 [呈现器材料](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 的属性，则 Unity 将创建分配的材料的克隆副本。</span><span class="sxs-lookup"><span data-stu-id="92d36-218">However, if developer's modify properties of a [Renderer's material](https://docs.unity3d.com/ScriptReference/Renderer-material.html) at runtime, Unity will create a clone copy of the assigned material.</span></span>

<span data-ttu-id="92d36-219">例如，如果一个场景中有一个100的多维数据集，则开发人员可能需要在运行时为每个多维数据集分配一种独特的颜色。</span><span class="sxs-lookup"><span data-stu-id="92d36-219">For example, if there are a 100 cubes in a scene, a developer may want to assign a unique color to each at runtime.</span></span> <span data-ttu-id="92d36-220">C # 中的 [*呈现*](https://docs.unity3d.com/ScriptReference/Material-color.html) 器的访问权限将使 Unity 在内存中为此特定呈现器/GameObject 创建一个新材料。</span><span class="sxs-lookup"><span data-stu-id="92d36-220">The access of [*renderer.material.color*](https://docs.unity3d.com/ScriptReference/Material-color.html) in C# will make Unity create a new material in memory for this particular renderer/GameObject.</span></span> <span data-ttu-id="92d36-221">每个100多维数据集都有其自己的材料，因此它们不能合并为一个绘图调用，而是会成为100，将来自 CPU 的调用请求绘制到 GPU。</span><span class="sxs-lookup"><span data-stu-id="92d36-221">Each of the 100 cubes will have its own material and thus they cannot be merged together into one draw call, but instead will become 100 draw call requests from the CPU to the GPU.</span></span>

<span data-ttu-id="92d36-222">为了克服这一障碍，并为每个多维数据集分配唯一的颜色，开发人员应利用 [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)。</span><span class="sxs-lookup"><span data-stu-id="92d36-222">To overcome this obstacle and still assign a unique color per cube, developers should leverage [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span></span>

```c#
private PropertyBlock m_PropertyBlock ;
private Renderer myRenderer;

private void Start()
{
     myRenderer = GetComponent<Renderer>();
     m_PropertyBlock = new MaterialPropertyBlock();
}

private void ChangeColor()
{
    // Creates a copy of the material once for this renderer
    myRenderer.material.color = Color.red;

    // vs.

    // Retains instancing capability for renderer
    m_PropertyBlock.SetColor("_Color", Color.red);
    myRenderer.SetPropertyBlock(m_PropertyBlock);
}
```

## <a name="unity-performance-tools"></a><span data-ttu-id="92d36-223">Unity 性能工具</span><span class="sxs-lookup"><span data-stu-id="92d36-223">Unity performance tools</span></span>

<span data-ttu-id="92d36-224">Unity 提供了编辑器中内置的极佳性能工具。</span><span class="sxs-lookup"><span data-stu-id="92d36-224">Unity provides great performance tools that are built into the editor.</span></span>

- [<span data-ttu-id="92d36-225">Unity 探查器</span><span class="sxs-lookup"><span data-stu-id="92d36-225">Unity Profiler</span></span>](https://docs.unity3d.com/Manual//Profiler.html)
- [<span data-ttu-id="92d36-226">Unity 框架调试器</span><span class="sxs-lookup"><span data-stu-id="92d36-226">Unity Frame Debugger</span></span>](https://docs.unity3d.com/Manual/FrameDebugger.html)

<span data-ttu-id="92d36-227">如果估计一个着色器与另一个着色器之间的粗略性能折衷，则编译每个着色器并查看每个着色器阶段的操作数很有用。</span><span class="sxs-lookup"><span data-stu-id="92d36-227">If estimating the rough performance tradeoff between one shader and another, it is useful to compile each shader and view the number of operations per shader stage.</span></span> <span data-ttu-id="92d36-228">为此，可以选择 [着色器资产](https://docs.unity3d.com/Manual/class-Shader.html) ，并单击 " *编译和显示代码* " 按钮。</span><span class="sxs-lookup"><span data-stu-id="92d36-228">This can be done by selecting a [shader asset](https://docs.unity3d.com/Manual/class-Shader.html) and clicking the *Compile and show code* button.</span></span> <span data-ttu-id="92d36-229">这将编译所有着色器变体，并打开 visual studio 并显示结果。</span><span class="sxs-lookup"><span data-stu-id="92d36-229">This will compile all the shader variants and open visual studio with the results.</span></span> <span data-ttu-id="92d36-230">注意：生成的统计信息结果可能因使用给定着色器对材料启用的功能而异。</span><span class="sxs-lookup"><span data-stu-id="92d36-230">Note: The statistic results produced may vary depending on what features have been enabled on materials utilizing the given shader.</span></span> <span data-ttu-id="92d36-231">Unity 只会编译当前项目中直接使用的着色器变体。</span><span class="sxs-lookup"><span data-stu-id="92d36-231">Unity will only compile the shader variants being directly used in the current project.</span></span>

<span data-ttu-id="92d36-232">Unity 标准着色器统计信息示例</span><span class="sxs-lookup"><span data-stu-id="92d36-232">Unity Standard shader statistics example</span></span>

![Unity 标准着色器统计信息1](../features/images/performance/UnityStandardShader-Stats.PNG)

<span data-ttu-id="92d36-234">MRTK 标准着色器统计信息示例</span><span class="sxs-lookup"><span data-stu-id="92d36-234">MRTK Standard shader statistics example</span></span>

![MRTK 标准着色器统计信息2](../features/images/performance/MRTKStandardShader-Stats.PNG)

## <a name="see-also"></a><span data-ttu-id="92d36-236">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92d36-236">See also</span></span>

### <a name="unity"></a><span data-ttu-id="92d36-237">Unity</span><span class="sxs-lookup"><span data-stu-id="92d36-237">Unity</span></span>

- [<span data-ttu-id="92d36-238">适用于初学者的 Unity 性能优化</span><span class="sxs-lookup"><span data-stu-id="92d36-238">Unity Performance Optimization for Beginners</span></span>](https://www.youtube.com/watch?v=1e5WY2qf600)
- [<span data-ttu-id="92d36-239">Unity 性能优化教程</span><span class="sxs-lookup"><span data-stu-id="92d36-239">Unity Performance Optimization Tutorials</span></span>](https://unity3d.com/learn/tutorials/topics/performance-optimization)
- [<span data-ttu-id="92d36-240">Unity 优化最佳做法</span><span class="sxs-lookup"><span data-stu-id="92d36-240">Unity Optimization Best Practices</span></span>](https://docs.unity3d.com/Documentation/Manual/BestPracticeUnderstandingPerformanceInUnity.html)
- [<span data-ttu-id="92d36-241">优化图形性能</span><span class="sxs-lookup"><span data-stu-id="92d36-241">Optimizing graphics performance</span></span>](https://docs.unity3d.com/Manual/OptimizingGraphicsPerformance.html)
- [<span data-ttu-id="92d36-242">移动优化实用指南</span><span class="sxs-lookup"><span data-stu-id="92d36-242">Mobile Optimization Practical Guide</span></span>](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html)

### <a name="windows-mixed-reality"></a><span data-ttu-id="92d36-243">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="92d36-243">Windows Mixed Reality</span></span>

- [<span data-ttu-id="92d36-244">适用于 Unity 的建议设置</span><span class="sxs-lookup"><span data-stu-id="92d36-244">Recommended Settings for Unity</span></span>](/windows/mixed-reality/recommended-settings-for-unity)
- [<span data-ttu-id="92d36-245">了解混合现实的性能</span><span class="sxs-lookup"><span data-stu-id="92d36-245">Understanding Performance for Mixed Reality</span></span>](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [<span data-ttu-id="92d36-246">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="92d36-246">Performance recommendations for Unity</span></span>](/windows/mixed-reality/performance-recommendations-for-unity)
- [<span data-ttu-id="92d36-247">Windows Unity 指南的事件跟踪</span><span class="sxs-lookup"><span data-stu-id="92d36-247">Event Tracing for Windows Unity Guide</span></span>](https://docs.unity3d.com/uploads/ExpertGuides/Analyzing_your_game_performance_using_Event_Tracing_for_Windows.pdf)

### <a name="oculus"></a><span data-ttu-id="92d36-248">Oculus</span><span class="sxs-lookup"><span data-stu-id="92d36-248">Oculus</span></span>

- [<span data-ttu-id="92d36-249">性能准则</span><span class="sxs-lookup"><span data-stu-id="92d36-249">Performance Guidelines</span></span>](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)
- [<span data-ttu-id="92d36-250">性能工具</span><span class="sxs-lookup"><span data-stu-id="92d36-250">Performance Tools</span></span>](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-tools/)

### <a name="mesh-optimization"></a><span data-ttu-id="92d36-251">网格优化</span><span class="sxs-lookup"><span data-stu-id="92d36-251">Mesh optimization</span></span>

- [<span data-ttu-id="92d36-252">优化3D 模型</span><span class="sxs-lookup"><span data-stu-id="92d36-252">Optimize 3D models</span></span>](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [<span data-ttu-id="92d36-253">转换和优化实时3D 模型的最佳做法</span><span class="sxs-lookup"><span data-stu-id="92d36-253">Best practices for converting and optimizing real-time 3D models</span></span>](/dynamics365/mixed-reality/import-tool/best-practices)
