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
# <a name="using-the-visual-profiler"></a>使用可视化探查器

VisualProfiler 提供了一个易于使用的应用程序内视图，用于查看混合现实应用程序的性能。 所有混合现实平台都支持探查器Toolkit平台，包括：

- Microsoft HoloLens (第一代) 
- Microsoft HoloLens 2
- Windows Mixed Reality 沉浸式头戴显示设备
- OpenVR

开发应用程序时，请专注于场景的多个部分，因为 Visual Profiler 显示相对于当前视图的数据。

> [!IMPORTANT]
> 重点关注具有复杂对象、粒子效果或活动的场景部分。 这些因素和其他因素通常会导致应用程序性能降低和用户体验不理想。

## <a name="visual-profiler-interface"></a>可视化探查器接口

![Visual Profiler 接口](../images/diagnostics/VisualProfiler.png)

Visual Profiler 接口包括以下组件：

- [帧速率](#frame-rate)
- [帧时间](#frame-time)
- [帧Graph](#frame-graph)
- [内存使用率](#memory-utilization)

### <a name="frame-rate"></a>帧速率

接口的左上角是帧速率，以每秒帧数为单位。 为了获得最佳用户体验和舒适感，此值应尽可能高。

特定平台和硬件配置将在可实现的最大帧速率中起很大的作用。 一些常见目标值包括：

- Microsoft HoloLens：60
- Windows Mixed Reality Ultra：90

> [!NOTE]
> 由于[默认 MRC](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)处于活动状态时HoloLens帧速率限制，因此在捕获视频和照片时，可视化探查器会隐藏自身。 可以在诊断系统配置文件中重写此设置。

### <a name="frame-time"></a>帧时间

帧速率的右侧是 CPU 上的帧时间（以毫秒为单位）。 若要实现前面提到的目标帧速率，应用程序可以每帧花费以下时间：

- 60 fps：16.6 毫秒
- 90 fps：11.1 毫秒

计划在将来的版本中添加 GPU 时间。

### <a name="frame-graph"></a>帧图

帧图提供应用程序帧速率历史记录的图形显示。

![视觉探查器丢失的帧Graph](../images/diagnostics/VisualProfilerMissedFrames.png)

使用应用程序时，查找丢失的帧，这些帧指示应用程序未达到其目标帧速率，并且可能需要优化工作。

### <a name="memory-utilization"></a>内存利用率

通过内存利用率显示，可以轻松了解当前视图如何影响应用程序的内存消耗。

![Visual Profiler 内存Graph](../images/diagnostics/VisualProfilerMemory.png)

使用应用程序时，请查找总内存使用量。 关键指标包括接近内存限制和使用量快速变化。

## <a name="customizing-the-visual-profiler"></a>自定义可视化探查器

Visual Profiler 的外观和行为可通过诊断系统配置文件进行自定义。 有关详细信息 [，请参阅配置](configuring-diagnostics.md) 诊断系统。

## <a name="see-also"></a>另请参阅

- [诊断系统](diagnostics-system-getting-started.md)
- [配置诊断系统](configuring-diagnostics.md)
