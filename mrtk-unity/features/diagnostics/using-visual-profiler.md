---
title: 使用可视探查器
description: 在 MRTK 中使用可视化探查器的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 4830615fd55a39614dd775dd7628938ee3af1c3b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143717"
---
# <a name="using-the-visual-profiler"></a>使用可视化探查器

VisualProfiler 提供了一个易于使用的应用程序内视图，用于查看混合现实应用程序的性能。 所有混合现实工具包平台都支持探查器，包括：

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
- [帧图](#frame-graph)
- [内存利用率](#memory-utilization)

### <a name="frame-rate"></a>帧速率

接口的左上角是帧速率，以每秒帧数为单位。 为了获得最佳用户体验和舒适感，此值应尽可能高。

特定平台和硬件配置将在可实现的最大帧速率中起很大的作用。 一些常见目标值包括：

- Microsoft HoloLens：60
- Windows Mixed Reality Ultra：90

> [!NOTE]
> 由于在 [默认 MRC 处于活动状态时，在 HoloLens 上出现帧速率限制](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)，因此在捕获视频和照片时，视觉探查器会隐藏自身。 可以在诊断系统配置文件中覆盖此设置。

### <a name="frame-time"></a>帧时间

帧速率右侧的帧时间（以毫秒为单位）用于 CPU。 若要实现前面提到的目标帧速率，应用程序可以在每个帧中花费以下时间量：

- 60 fps：16.6 毫秒
- 90 fps：11.1 毫秒

在未来版本中计划添加 GPU 时间。

### <a name="frame-graph"></a>框架关系图

框架关系图提供了应用程序帧速率历史记录的图形显示。

![可视化探查器丢失框架关系图](../images/diagnostics/VisualProfilerMissedFrames.png)

使用应用程序时，查找未命中的帧，这表明应用程序未达到其目标帧速率，可能需要优化工作。

### <a name="memory-utilization"></a>内存利用率

内存使用率显示使你能够轻松了解当前视图对应用程序的内存消耗的影响。

![可视化探查器内存图](../images/diagnostics/VisualProfilerMemory.png)

使用应用程序时，查找总内存使用量。 关键指示器包括接近内存限制和使用情况的快速更改。

## <a name="customizing-the-visual-profiler"></a>自定义可视化探查器

可视化探查器的外观和行为可通过诊断系统配置文件进行自定义。 有关详细信息，请参阅 [配置诊断系统](configuring-diagnostics.md) 。

## <a name="see-also"></a>另请参阅

- [诊断系统](diagnostics-system-getting-started.md)
- [配置诊断系统](configuring-diagnostics.md)