---
title: 优化窗口
description: MRTK 中的文档优化窗口
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 7ffc2173cc55c83f126f66002d9240cb349d7f59
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144317"
---
# <a name="optimize-window"></a><span data-ttu-id="9373c-104">优化窗口</span><span class="sxs-lookup"><span data-stu-id="9373c-104">Optimize window</span></span>

<span data-ttu-id="9373c-105">"MRTK 优化" 窗口是一个实用工具，可帮助自动执行和通知配置混合现实项目的过程，以便在 Unity 中获得最佳 [性能](../../performance/perf-getting-started.md) 。</span><span class="sxs-lookup"><span data-stu-id="9373c-105">The MRTK Optimize Window is a utility to help automate and inform in the process of configuring a mixed reality project for best [performance](../../performance/perf-getting-started.md) in Unity.</span></span> <span data-ttu-id="9373c-106">此工具通常侧重于呈现配置，当设置为正确预设时，可以节省毫秒的处理。</span><span class="sxs-lookup"><span data-stu-id="9373c-106">This tool generally focuses on rendering configurations that when set to the correct preset can save milliseconds of processing.</span></span>

<span data-ttu-id="9373c-107">*活动生成目标* 是项目当前作为编译 [目标的生成平台](https://docs.unity3d.com/Manual/BuildSettings.html)。</span><span class="sxs-lookup"><span data-stu-id="9373c-107">The *Active Build Target* is the [build platform currently targeted](https://docs.unity3d.com/Manual/BuildSettings.html) by the project for compiling.</span></span>

<span data-ttu-id="9373c-108">*性能目标* 指示优化工具针对的设备终结点类型。</span><span class="sxs-lookup"><span data-stu-id="9373c-108">The *Performance Target* instructs the optimize tool on what kind of device endpoints to target.</span></span>

- <span data-ttu-id="9373c-109">*AR 耳机* 是移动类设备，如 HoloLens</span><span class="sxs-lookup"><span data-stu-id="9373c-109">*AR Headsets* are mobile-class devices, such as HoloLens</span></span>
- <span data-ttu-id="9373c-110">*VR 独立* 设备，如 Oculus 或寻找</span><span class="sxs-lookup"><span data-stu-id="9373c-110">*VR Standalone* are mobile-class devices, such as the Oculus Go or Quest</span></span>
- <span data-ttu-id="9373c-111">*VR 受限* 是电脑设备，例如 Samsung 太空、Oculus RIFT 或 HTC naopak 等。</span><span class="sxs-lookup"><span data-stu-id="9373c-111">*VR Tethered* are PC-powered devices, such as the Samsung Odyssey, Oculus Rift or HTC Vive etc.</span></span>

![MRTK 优化窗口性能目标](../images/performance/OptimizeWindowPerformanceTarget.jpg)

## <a name="setting-optimizations"></a><span data-ttu-id="9373c-113">设置优化</span><span class="sxs-lookup"><span data-stu-id="9373c-113">Setting optimizations</span></span>

<span data-ttu-id="9373c-114">"设置优化" 选项卡介绍了 Unity 项目的一些重要呈现配置。</span><span class="sxs-lookup"><span data-stu-id="9373c-114">The settings optimization tab covers some of the important rendering configurations for a Unity project.</span></span> <span data-ttu-id="9373c-115">本部分可帮助自动执行，并通知你应更改哪些设置以获得最佳性能。</span><span class="sxs-lookup"><span data-stu-id="9373c-115">This section can help automate and inform you of which settings should be changed for the best performing results.</span></span>

<span data-ttu-id="9373c-116">绿色复选图标表示已在项目/场景中为此特定设置配置了最优值。</span><span class="sxs-lookup"><span data-stu-id="9373c-116">A green check icon means that an optimal value has been configured in the project/scene for this particular setting.</span></span> <span data-ttu-id="9373c-117">黄色警告图标表示可以提高当前配置。</span><span class="sxs-lookup"><span data-stu-id="9373c-117">A yellow warning icon indicates the current configuration can be improved.</span></span> <span data-ttu-id="9373c-118">单击给定节中的关联按钮会自动将 Unity 项目/场景中的该设置配置为更最优的值。</span><span class="sxs-lookup"><span data-stu-id="9373c-118">Clicking the associated button in a given section will auto-configure that setting in the Unity project/scene to a more optimal value.</span></span>

![MRTK 优化窗口设置](../images/performance/OptimizeWindow_Settings.png)

### <a name="single-pass-instanced-rendering"></a><span data-ttu-id="9373c-120">单次传递实例呈现</span><span class="sxs-lookup"><span data-stu-id="9373c-120">Single Pass Instanced rendering</span></span>

<span data-ttu-id="9373c-121">[单一传递实例呈现](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 是混合现实应用程序的最有效呈现路径。</span><span class="sxs-lookup"><span data-stu-id="9373c-121">[Single Pass instanced rendering](https://docs.unity3d.com/Manual/SinglePassInstancing.html) is the most efficient rendering path for mixed reality applications.</span></span> <span data-ttu-id="9373c-122">此配置可确保每个眼睛仅执行一次渲染管道，并且在两个眼睛之间实例化绘图调用。</span><span class="sxs-lookup"><span data-stu-id="9373c-122">This configuration ensures the render pipeline is executed only once for both eyes and that draw calls are instanced across both eyes.</span></span>

### <a name="depth-buffer-sharing"></a><span data-ttu-id="9373c-123">深度缓冲区共享</span><span class="sxs-lookup"><span data-stu-id="9373c-123">Depth buffer sharing</span></span>

<span data-ttu-id="9373c-124">为了提高 [全息影像稳定性，](../../performance/hologram-Stabilization.md)开发人员可以共享应用程序的深度缓冲区，该缓冲区为平台提供有关在渲染场景中稳定位置和要稳定哪些全息影像的平台信息。</span><span class="sxs-lookup"><span data-stu-id="9373c-124">To improve [hologram stabilization](../../performance/hologram-Stabilization.md), developers can share the application's depth buffer which gives the platform information on where and what holograms to stabilize in the rendered scene.</span></span>

### <a name="depth-buffer-format"></a><span data-ttu-id="9373c-125">深度缓冲区格式</span><span class="sxs-lookup"><span data-stu-id="9373c-125">Depth buffer format</span></span>

<span data-ttu-id="9373c-126">此外，对于 *AR 头* 戴显示设备，建议在启用深度缓冲区共享（与 24 位共享相比）时，使用 16 位深度格式。</span><span class="sxs-lookup"><span data-stu-id="9373c-126">Furthermore, for *AR Headsets*, it is recommended to utilize a 16-bit depth format when enabling depth buffer sharing compared to 24-bit.</span></span> <span data-ttu-id="9373c-127">这意味着精度较低，但会节省性能。</span><span class="sxs-lookup"><span data-stu-id="9373c-127">This means lower precision but saves on performance.</span></span> <span data-ttu-id="9373c-128">如果[由于](https://en.wikipedia.org/wiki/Z-fighting)像素深度计算精度较低而发生 z 冲突，则建议将远剪裁平面移近相机 (例如：50m 而不是 1000m) 。 [](https://docs.unity3d.com/Manual/class-Camera.html)</span><span class="sxs-lookup"><span data-stu-id="9373c-128">If [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) occurs because there is less precision in calculating depth for pixels, then it is recommended to move the [far clip plane](https://docs.unity3d.com/Manual/class-Camera.html) closer to the camera (ex: 50m instead of 1000m).</span></span>

> [!NOTE]
> <span data-ttu-id="9373c-129">如果使用 *16 位* 深度格式 ，则所需的模具缓冲区效果将不起作用，因为 [Unity](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 不会在此设置中创建模具缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9373c-129">If using *16-bit depth format*, stencil buffer required effects will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="9373c-130">相反 *，如果选择 24* 位深度格式，通常会在终结点图形平台上创建一个 [8](https://docs.unity3d.com/Manual/SL-Stencil.html)位模具缓冲区（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="9373c-130">Selecting *24-bit depth format* conversely will generally create an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html), if applicable on the endpoint graphics platform.</span></span>
>
> <span data-ttu-id="9373c-131">如果使用需要模具缓冲区的 [Mask](https://docs.unity3d.com/Manual/script-Mask.html) 组件，请考虑改为使用 [RectMask2D，](https://docs.unity3d.com/Manual/script-RectMask2D.html) 它不需要模具缓冲区，因此可以与 *16* 位深度格式 结合使用。</span><span class="sxs-lookup"><span data-stu-id="9373c-131">If using a [Mask component](https://docs.unity3d.com/Manual/script-Mask.html) which requires the stencil buffer, consider using [RectMask2D](https://docs.unity3d.com/Manual/script-RectMask2D.html) instead, which does not require the stencil buffer and thus can be used in conjunction with a *16-bit depth format*.</span></span>

### <a name="real-time-global-illumination"></a><span data-ttu-id="9373c-132">实时全球照明</span><span class="sxs-lookup"><span data-stu-id="9373c-132">Real-time Global Illumination</span></span>

<span data-ttu-id="9373c-133">[Unity 中的实时全局](https://docs.unity3d.com/Manual/GIIntro.html) 照明可以提供出色的美观效果，但成本非常高。</span><span class="sxs-lookup"><span data-stu-id="9373c-133">[Real-time Global illumination](https://docs.unity3d.com/Manual/GIIntro.html) in Unity can provide fantastic aesthetic results but at a very high cost.</span></span> <span data-ttu-id="9373c-134">全球照明在混合现实中非常昂贵，因此建议在开发中禁用此功能。</span><span class="sxs-lookup"><span data-stu-id="9373c-134">Global illumination lighting is very expensive in mixed reality and thus it is recommended to disable this feature in development.</span></span>

> [!NOTE]
> <span data-ttu-id="9373c-135">Unity 中的全局照明设置按场景设置，而不是在整个项目中设置一次。</span><span class="sxs-lookup"><span data-stu-id="9373c-135">Global illumination settings in Unity are set per-scene and not once across the entire project.</span></span>

## <a name="scene-analysis"></a><span data-ttu-id="9373c-136">场景分析</span><span class="sxs-lookup"><span data-stu-id="9373c-136">Scene analysis</span></span>

<span data-ttu-id="9373c-137">" *场景分析* "选项卡旨在告知开发人员场景中当前哪些元素对性能的影响最大。</span><span class="sxs-lookup"><span data-stu-id="9373c-137">The *Scene Analysis* tab is designed to inform developers on which elements currently in the scene will likely have the most impact on performance.</span></span>

![MRTK 优化窗口设置场景分析](../images/performance/OptimizeWindow_SceneAnalysis.png)

### <a name="lighting-analysis"></a><span data-ttu-id="9373c-139">照明分析</span><span class="sxs-lookup"><span data-stu-id="9373c-139">Lighting analysis</span></span>

<span data-ttu-id="9373c-140">本部分将检查场景中当前光线的数量，以及应禁用阴影的任何光。</span><span class="sxs-lookup"><span data-stu-id="9373c-140">This section will examine the number of lights currently in the scene, as well as any lights that should disable shadows.</span></span> <span data-ttu-id="9373c-141">阴影强制转换是一项非常昂贵的操作。</span><span class="sxs-lookup"><span data-stu-id="9373c-141">Shadow casting is a very expensive operation.</span></span>

### <a name="polygon-count-analysis"></a><span data-ttu-id="9373c-142">多边形计数分析</span><span class="sxs-lookup"><span data-stu-id="9373c-142">Polygon count analysis</span></span>

<span data-ttu-id="9373c-143">该工具还提供多边形计数统计信息。</span><span class="sxs-lookup"><span data-stu-id="9373c-143">The tool also provides polygon count statistics.</span></span> <span data-ttu-id="9373c-144">这对于快速标识在给定场景中具有最大多边形复杂度的 Gameobject 很有帮助，以便进行优化。</span><span class="sxs-lookup"><span data-stu-id="9373c-144">It can be very helpful to quickly identify which GameObjects have the highest polygon complexity in a given scene to target for optimizations.</span></span>

### <a name="unity-ui-raycast-analysis"></a><span data-ttu-id="9373c-145">Unity UI raycast 分析</span><span class="sxs-lookup"><span data-stu-id="9373c-145">Unity UI raycast analysis</span></span>

<span data-ttu-id="9373c-146">图形 raycast 操作在 MRTK 中按指针执行，以确定是否有任何 Unity UI 元素处于焦点。</span><span class="sxs-lookup"><span data-stu-id="9373c-146">Graphics raycast operations are performed per pointer in MRTK to determine if any Unity UI elements are in focus.</span></span> <span data-ttu-id="9373c-147">这些 raycasts 的开销可能很高，并且有助于提高性能，不需要在结果中返回的 UI 元素应禁用为 raycast 目标。</span><span class="sxs-lookup"><span data-stu-id="9373c-147">These raycasts can be quite expensive and to help improve performance, UI elements that do not need to be returned in the results should be disabled as raycast targets.</span></span> <span data-ttu-id="9373c-148">每个 [图形](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) 元素都具有 [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) 属性。</span><span class="sxs-lookup"><span data-stu-id="9373c-148">Every [Graphic](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) element has a [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) property.</span></span> <span data-ttu-id="9373c-149">此工具将搜索启用了此属性的文本 UI 元素，因此可能会被禁用。</span><span class="sxs-lookup"><span data-stu-id="9373c-149">This tool will search for text UI elements that have this property enabled and thus are likely candidates to be disabled.</span></span>

## <a name="shader-analysis"></a><span data-ttu-id="9373c-150">着色器分析</span><span class="sxs-lookup"><span data-stu-id="9373c-150">Shader analysis</span></span>

<span data-ttu-id="9373c-151">[Unity 标准着色器](https://docs.unity3d.com/Manual/shader-StandardShader.html)可以为游戏产生非常高质量的视觉效果，但通常不适合用于混合现实应用程序的性能需求，尤其是因为此类应用程序通常是 GPU 限制的。</span><span class="sxs-lookup"><span data-stu-id="9373c-151">The [Unity Standard shader](https://docs.unity3d.com/Manual/shader-StandardShader.html) can produce very high quality visual results for games but is not generally best suited for the performance needs of mixed reality applications, especially since such applications are generally GPU bounded.</span></span> <span data-ttu-id="9373c-152">因此，建议开发人员利用 [MRTK 标准着色器](../rendering/mrtk-standard-shader.md) 来平衡美观 & 图形功能与性能。</span><span class="sxs-lookup"><span data-stu-id="9373c-152">Thus, it is recommended to developers to utilize the [MRTK Standard shader](../rendering/mrtk-standard-shader.md) to balance aesthetics & graphical features with performance.</span></span>

<span data-ttu-id="9373c-153">" *着色器分析* " 选项卡使用 Unity 标准着色器扫描当前项目的资产文件夹，如果需要，则不使用混合现实工具包的所有材料提供着色。</span><span class="sxs-lookup"><span data-stu-id="9373c-153">The *Shader Analysis* tab scans the current project's Asset folder for materials using the Unity Standard shader or if desired, all materials not using Mixed Reality Toolkit provided shaders.</span></span> <span data-ttu-id="9373c-154">一旦发现，开发人员就可以转换所有材料或使用适当的按钮单独转换。</span><span class="sxs-lookup"><span data-stu-id="9373c-154">Once discovered, developers can convert all materials or convert individually using the appropriate buttons.</span></span>

![MRTK 优化窗口设置着色器分析](../images/performance/OptimizeWindow_ShaderAnalysis.png)

## <a name="see-also"></a><span data-ttu-id="9373c-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9373c-156">See also</span></span>

- [<span data-ttu-id="9373c-157">性能</span><span class="sxs-lookup"><span data-stu-id="9373c-157">Performance</span></span>](../../performance/perf-getting-started.md)
- [<span data-ttu-id="9373c-158">全息影像稳定化</span><span class="sxs-lookup"><span data-stu-id="9373c-158">Hologram Stabilization</span></span>](../../performance/hologram-stabilization.md)
