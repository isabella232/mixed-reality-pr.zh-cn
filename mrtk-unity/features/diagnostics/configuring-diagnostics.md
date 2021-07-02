---
title: 配置诊断系统
description: 在 MRTK 中配置诊断的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: d81b441cd9bcd40846eb94320f6f7de1bbd2f0a8
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177256"
---
# <a name="configuring-the-diagnostics-system"></a><span data-ttu-id="d7eb8-104">配置诊断系统</span><span class="sxs-lookup"><span data-stu-id="d7eb8-104">Configuring the diagnostics system</span></span>

## <a name="general-settings"></a><span data-ttu-id="d7eb8-105">常规设置</span><span class="sxs-lookup"><span data-stu-id="d7eb8-105">General settings</span></span>

![诊断常规设置](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a><span data-ttu-id="d7eb8-107">启用详细日志记录</span><span class="sxs-lookup"><span data-stu-id="d7eb8-107">Enable verbose logging</span></span>

<span data-ttu-id="d7eb8-108">指示是否启用详细 MRTK 日志记录。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-108">Indicates whether or not verbose MRTK logging will be enabled.</span></span> <span data-ttu-id="d7eb8-109">这默认为 false，但可以启用 以获取详细的跟踪，使 MRTK 团队能够调试/深入解决问题。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-109">This defaults to false, but can be turned on to take detailed traces that allow the MRTK team to debug/dig into issues.</span></span> <span data-ttu-id="d7eb8-110">例如，在提交问题时，从编辑器或播放器 (附加 Unity 播放器日志) 有助于缩小 bug 和问题的来源。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-110">For example, when filing an issue, attaching the Unity player logs (either from the editor or from the player) can help narrow down the source of bugs and issues.</span></span>

<span data-ttu-id="d7eb8-111">请注意，此选项与是否启用诊断系统无关 - 此选项显示在诊断系统下，因为它是日志记录选项，但最终在较高级别运行，因为它会影响整个 MRTK 代码库的日志记录。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-111">Note that this option is independent of whether or not diagnostics system is enabled - this shows up under the diagnostics system because it's a logging option, but ultimately operates at a higher level because it affects logging across the entire MRTK codebase.</span></span>

### <a name="show-diagnostics"></a><span data-ttu-id="d7eb8-112">显示诊断信息</span><span class="sxs-lookup"><span data-stu-id="d7eb8-112">Show diagnostics</span></span>

<span data-ttu-id="d7eb8-113">指示诊断系统是否显示配置的诊断选项。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-113">Indicates whether or not the diagnostics system is to display the configured diagnostic options.</span></span>

<span data-ttu-id="d7eb8-114">禁用后，将隐藏所有配置的诊断选项。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-114">When disabled, all configured diagnostic options will be hidden.</span></span>

## <a name="profiler-settings"></a><span data-ttu-id="d7eb8-115">探查器设置</span><span class="sxs-lookup"><span data-stu-id="d7eb8-115">Profiler settings</span></span>

![诊断探查器设置](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a><span data-ttu-id="d7eb8-117">显示探查器</span><span class="sxs-lookup"><span data-stu-id="d7eb8-117">Show profiler</span></span>

<span data-ttu-id="d7eb8-118">指示是否显示 Visual Profiler。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-118">Indicates whether or not the Visual Profiler is to be displayed.</span></span>

### <a name="frame-sample-rate"></a><span data-ttu-id="d7eb8-119">帧采样率</span><span class="sxs-lookup"><span data-stu-id="d7eb8-119">Frame sample rate</span></span>

<span data-ttu-id="d7eb8-120">收集帧进行帧速率计算的时间量（以秒计）。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-120">The amount of time, in seconds to collect frames for frame rate calculation.</span></span> <span data-ttu-id="d7eb8-121">范围为 0 到 5 秒。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-121">The range is 0 to 5 seconds.</span></span>

### <a name="window-anchor"></a><span data-ttu-id="d7eb8-122">窗口定位点</span><span class="sxs-lookup"><span data-stu-id="d7eb8-122">Window anchor</span></span>

<span data-ttu-id="d7eb8-123">将探查器窗口锚定到视图端口的哪一部分。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-123">To what portion of the view port should the profiler window be anchored.</span></span> <span data-ttu-id="d7eb8-124">默认值为 Lower Center。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-124">The default value is Lower Center.</span></span>

### <a name="window-offset"></a><span data-ttu-id="d7eb8-125">窗口偏移量</span><span class="sxs-lookup"><span data-stu-id="d7eb8-125">Window offset</span></span>

<span data-ttu-id="d7eb8-126">从视图端口中心放置 Visual Profiler 的偏移量。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-126">The offset, from the center of the view port, to place the Visual Profiler.</span></span> <span data-ttu-id="d7eb8-127">偏移量将相对于 Window Anchor *属性* 的方向。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-127">The offset will be in the direction of the *Window Anchor* property.</span></span>

### <a name="window-scale"></a><span data-ttu-id="d7eb8-128">窗口缩放</span><span class="sxs-lookup"><span data-stu-id="d7eb8-128">Window scale</span></span>

<span data-ttu-id="d7eb8-129">应用于探查器窗口的大小乘数。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-129">Size multiplier applied to the profiler window.</span></span> <span data-ttu-id="d7eb8-130">例如，将值设置为 2 将窗口大小翻倍。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-130">For example, setting the value to 2 will double the window size.</span></span>

### <a name="window-follow-speed"></a><span data-ttu-id="d7eb8-131">窗口跟随速度</span><span class="sxs-lookup"><span data-stu-id="d7eb8-131">Window follow speed</span></span>

<span data-ttu-id="d7eb8-132">移动探查器窗口以保持视图端口内的可见性的速度。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-132">The speed at which to move the profiler window to maintain visibility within the view port.</span></span>

## <a name="programmatically-controlling-the-diagnostics-system"></a><span data-ttu-id="d7eb8-133">以编程方式控制诊断系统</span><span class="sxs-lookup"><span data-stu-id="d7eb8-133">Programmatically controlling the diagnostics system</span></span>

<span data-ttu-id="d7eb8-134">还可以在运行时切换诊断系统和探查器可见性。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-134">It's also possible to toggle the visibility of the diagnostics system and the profiler at runtime.</span></span> <span data-ttu-id="d7eb8-135">例如，下面的代码将隐藏诊断系统和探查器。</span><span class="sxs-lookup"><span data-stu-id="d7eb8-135">For example, the code below will hide the diagnostics system and profiler.</span></span>

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a><span data-ttu-id="d7eb8-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d7eb8-136">See also</span></span>

- [<span data-ttu-id="d7eb8-137">诊断系统</span><span class="sxs-lookup"><span data-stu-id="d7eb8-137">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="d7eb8-138">使用 Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="d7eb8-138">Using the Visual Profiler</span></span>](using-visual-profiler.md)
