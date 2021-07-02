---
title: 使用可视化探查器
description: 在 MRTK 中使用可视化探查器的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 018d6bf2087b73697a1e1f43e206c96ae25e1f21
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177225"
---
# <a name="using-the-visual-profiler"></a><span data-ttu-id="74f4b-104">使用可视化探查器</span><span class="sxs-lookup"><span data-stu-id="74f4b-104">Using the visual profiler</span></span>

<span data-ttu-id="74f4b-105">VisualProfiler 提供了一个易于使用的应用程序内视图，用于查看混合现实应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="74f4b-105">The VisualProfiler provides an easy to use, in-application view of a mixed reality application's performance.</span></span> <span data-ttu-id="74f4b-106">所有混合现实平台都支持探查器Toolkit平台，包括：</span><span class="sxs-lookup"><span data-stu-id="74f4b-106">The profiler is supported on all Mixed Reality Toolkit platforms, including:</span></span>

- <span data-ttu-id="74f4b-107">Microsoft HoloLens (第一代) </span><span class="sxs-lookup"><span data-stu-id="74f4b-107">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="74f4b-108">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="74f4b-108">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="74f4b-109">Windows Mixed Reality 沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="74f4b-109">Windows Mixed Reality immersive headsets</span></span>
- <span data-ttu-id="74f4b-110">OpenVR</span><span class="sxs-lookup"><span data-stu-id="74f4b-110">OpenVR</span></span>

<span data-ttu-id="74f4b-111">开发应用程序时，请专注于场景的多个部分，因为 Visual Profiler 显示相对于当前视图的数据。</span><span class="sxs-lookup"><span data-stu-id="74f4b-111">While developing an application, focus on multiple parts of the scene as the Visual Profiler displays data relative to the current view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="74f4b-112">重点关注具有复杂对象、粒子效果或活动的场景部分。</span><span class="sxs-lookup"><span data-stu-id="74f4b-112">Focus attention on portions of the scene with complex objects, particle effects or activity.</span></span> <span data-ttu-id="74f4b-113">这些因素和其他因素通常会导致应用程序性能降低和用户体验不理想。</span><span class="sxs-lookup"><span data-stu-id="74f4b-113">These and other factors often contribute to reduction in application performance and a less than ideal user experience.</span></span>

## <a name="visual-profiler-interface"></a><span data-ttu-id="74f4b-114">可视化探查器接口</span><span class="sxs-lookup"><span data-stu-id="74f4b-114">Visual profiler interface</span></span>

![Visual Profiler 接口](../images/diagnostics/VisualProfiler.png)

<span data-ttu-id="74f4b-116">Visual Profiler 接口包括以下组件：</span><span class="sxs-lookup"><span data-stu-id="74f4b-116">The Visual Profiler interface includes the following components:</span></span>

- [<span data-ttu-id="74f4b-117">帧速率</span><span class="sxs-lookup"><span data-stu-id="74f4b-117">Frame Rate</span></span>](#frame-rate)
- [<span data-ttu-id="74f4b-118">帧时间</span><span class="sxs-lookup"><span data-stu-id="74f4b-118">Frame Time</span></span>](#frame-time)
- [<span data-ttu-id="74f4b-119">帧Graph</span><span class="sxs-lookup"><span data-stu-id="74f4b-119">Frame Graph</span></span>](#frame-graph)
- [<span data-ttu-id="74f4b-120">内存使用率</span><span class="sxs-lookup"><span data-stu-id="74f4b-120">Memory Utilization</span></span>](#memory-utilization)

### <a name="frame-rate"></a><span data-ttu-id="74f4b-121">帧速率</span><span class="sxs-lookup"><span data-stu-id="74f4b-121">Frame rate</span></span>

<span data-ttu-id="74f4b-122">接口的左上角是帧速率，以每秒帧数为单位。</span><span class="sxs-lookup"><span data-stu-id="74f4b-122">In the upper-left corner of the interface is the frame rate, measured in frames per second.</span></span> <span data-ttu-id="74f4b-123">为了获得最佳用户体验和舒适感，此值应尽可能高。</span><span class="sxs-lookup"><span data-stu-id="74f4b-123">For the best user experience and comfort, this value should be as high as possible.</span></span>

<span data-ttu-id="74f4b-124">特定平台和硬件配置将在可实现的最大帧速率中起很大的作用。</span><span class="sxs-lookup"><span data-stu-id="74f4b-124">The specific platform and hardware configuration will play a significant role in the maximum achievable frame rate.</span></span> <span data-ttu-id="74f4b-125">一些常见目标值包括：</span><span class="sxs-lookup"><span data-stu-id="74f4b-125">Some common target values include:</span></span>

- <span data-ttu-id="74f4b-126">Microsoft HoloLens：60</span><span class="sxs-lookup"><span data-stu-id="74f4b-126">Microsoft HoloLens: 60</span></span>
- <span data-ttu-id="74f4b-127">Windows Mixed Reality Ultra：90</span><span class="sxs-lookup"><span data-stu-id="74f4b-127">Windows Mixed Reality Ultra: 90</span></span>

> [!NOTE]
> <span data-ttu-id="74f4b-128">由于[默认 MRC](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)处于活动状态时HoloLens帧速率限制，因此在捕获视频和照片时，可视化探查器会隐藏自身。</span><span class="sxs-lookup"><span data-stu-id="74f4b-128">Due to [frame rate throttling on HoloLens when default MRC is active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), the visual profiler hides itself while videos and photos are captured.</span></span> <span data-ttu-id="74f4b-129">可以在诊断系统配置文件中重写此设置。</span><span class="sxs-lookup"><span data-stu-id="74f4b-129">This setting can be overridden in the diagnostics system profile.</span></span>

### <a name="frame-time"></a><span data-ttu-id="74f4b-130">帧时间</span><span class="sxs-lookup"><span data-stu-id="74f4b-130">Frame time</span></span>

<span data-ttu-id="74f4b-131">帧速率的右侧是 CPU 上的帧时间（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="74f4b-131">To the right of the frame rate is the frame time, in milliseconds, spent on the CPU.</span></span> <span data-ttu-id="74f4b-132">若要实现前面提到的目标帧速率，应用程序可以每帧花费以下时间：</span><span class="sxs-lookup"><span data-stu-id="74f4b-132">To achieve the target frame rates mentioned previously, an application can spend the following amount of time per frame:</span></span>

- <span data-ttu-id="74f4b-133">60 fps：16.6 毫秒</span><span class="sxs-lookup"><span data-stu-id="74f4b-133">60 fps: 16.6 ms</span></span>
- <span data-ttu-id="74f4b-134">90 fps：11.1 毫秒</span><span class="sxs-lookup"><span data-stu-id="74f4b-134">90 fps: 11.1 ms</span></span>

<span data-ttu-id="74f4b-135">计划在将来的版本中添加 GPU 时间。</span><span class="sxs-lookup"><span data-stu-id="74f4b-135">GPU time is planned to be added in a future release.</span></span>

### <a name="frame-graph"></a><span data-ttu-id="74f4b-136">帧图</span><span class="sxs-lookup"><span data-stu-id="74f4b-136">Frame graph</span></span>

<span data-ttu-id="74f4b-137">帧图提供应用程序帧速率历史记录的图形显示。</span><span class="sxs-lookup"><span data-stu-id="74f4b-137">The frame graph provides a graphical display of the application frame rate history.</span></span>

![视觉探查器丢失的帧Graph](../images/diagnostics/VisualProfilerMissedFrames.png)

<span data-ttu-id="74f4b-139">使用应用程序时，查找丢失的帧，这些帧指示应用程序未达到其目标帧速率，并且可能需要优化工作。</span><span class="sxs-lookup"><span data-stu-id="74f4b-139">When using the application, look for missed frames which indicate that the application is not hitting its target frame rate and may need optimization work.</span></span>

### <a name="memory-utilization"></a><span data-ttu-id="74f4b-140">内存利用率</span><span class="sxs-lookup"><span data-stu-id="74f4b-140">Memory utilization</span></span>

<span data-ttu-id="74f4b-141">通过内存利用率显示，可以轻松了解当前视图如何影响应用程序的内存消耗。</span><span class="sxs-lookup"><span data-stu-id="74f4b-141">The memory utilization display allows for easy understanding of how the current view is impacting an application's memory consumption.</span></span>

![Visual Profiler 内存Graph](../images/diagnostics/VisualProfilerMemory.png)

<span data-ttu-id="74f4b-143">使用应用程序时，请查找总内存使用量。</span><span class="sxs-lookup"><span data-stu-id="74f4b-143">When using the application, look for total memory usage.</span></span> <span data-ttu-id="74f4b-144">关键指标包括接近内存限制和使用量快速变化。</span><span class="sxs-lookup"><span data-stu-id="74f4b-144">Key indicators include nearing the memory limit and rapid changes in usage.</span></span>

## <a name="customizing-the-visual-profiler"></a><span data-ttu-id="74f4b-145">自定义可视化探查器</span><span class="sxs-lookup"><span data-stu-id="74f4b-145">Customizing the visual profiler</span></span>

<span data-ttu-id="74f4b-146">Visual Profiler 的外观和行为可通过诊断系统配置文件进行自定义。</span><span class="sxs-lookup"><span data-stu-id="74f4b-146">The Visual Profiler's appearance and behavior are customizable via the diagnostics system profile.</span></span> <span data-ttu-id="74f4b-147">有关详细信息 [，请参阅配置](configuring-diagnostics.md) 诊断系统。</span><span class="sxs-lookup"><span data-stu-id="74f4b-147">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="74f4b-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74f4b-148">See also</span></span>

- [<span data-ttu-id="74f4b-149">诊断系统</span><span class="sxs-lookup"><span data-stu-id="74f4b-149">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="74f4b-150">配置诊断系统</span><span class="sxs-lookup"><span data-stu-id="74f4b-150">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)
