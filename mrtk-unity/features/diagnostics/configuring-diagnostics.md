---
title: 配置诊断系统
description: 在 MRTK 中配置诊断的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 521ef71abd1ddf920863530a2a423c1080a135e5a404a26f1611fc14f92c2796
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198231"
---
# <a name="configuring-the-diagnostics-system"></a>配置诊断系统

## <a name="general-settings"></a>常规设置

![诊断常规设置](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a>启用详细日志记录

指示是否启用详细 MRTK 日志记录。 这默认为 false，但可以启用 以获取详细的跟踪，使 MRTK 团队能够调试/深入解决问题。 例如，在提交问题时，从编辑器或播放器 (附加 Unity 播放器日志) 有助于缩小 bug 和问题的来源。

请注意，此选项与是否启用诊断系统无关 - 此选项显示在诊断系统下，因为它是日志记录选项，但最终在较高级别运行，因为它会影响整个 MRTK 代码库的日志记录。

### <a name="show-diagnostics"></a>显示诊断信息

指示诊断系统是否显示配置的诊断选项。

禁用后，将隐藏所有配置的诊断选项。

## <a name="profiler-settings"></a>探查器设置

![诊断探查器设置](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a>显示探查器

指示是否显示 Visual Profiler。

### <a name="frame-sample-rate"></a>帧采样率

收集帧进行帧速率计算的时间量（以秒计）。 范围为 0 到 5 秒。

### <a name="window-anchor"></a>窗口定位点

将探查器窗口锚定到视图端口的哪一部分。 默认值为 Lower Center。

### <a name="window-offset"></a>窗口偏移量

从视图端口中心放置 Visual Profiler 的偏移量。 偏移量将相对于 Window Anchor *属性* 的方向。

### <a name="window-scale"></a>窗口缩放

应用于探查器窗口的大小乘数。 例如，将值设置为 2 将窗口大小翻倍。

### <a name="window-follow-speed"></a>窗口跟随速度

移动探查器窗口以保持视图端口内的可见性的速度。

## <a name="programmatically-controlling-the-diagnostics-system"></a>以编程方式控制诊断系统

还可以在运行时切换诊断系统和探查器可见性。 例如，下面的代码将隐藏诊断系统和探查器。

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a>另请参阅

- [诊断系统](diagnostics-system-getting-started.md)
- [使用 Visual Profiler](using-visual-profiler.md)
