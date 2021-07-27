---
title: 优化窗口
description: MRTK 中的文档优化窗口
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 8b8928e9c723ffa9fd08d22866b8ee5748e38ace
ms.sourcegitcommit: 78746bef0e1ffe1480e89fed8cd30f6f8b389e8d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2021
ms.locfileid: "114713573"
---
# <a name="optimize-window"></a>优化窗口

MRTK 优化窗口是一个实用工具，可帮助在配置混合现实项目的过程中自动执行和通知，以在 Unity [中](../../performance/perf-getting-started.md) 实现最佳性能。 此工具通常侧重于呈现配置，如果设置为正确的预设，则可以节省毫秒的处理时间。

> [!NOTE]
> 可以通过 **从** Unity 编辑器的顶部栏菜单导航到"混合 **现实** 实用工具优化窗口"来打开"  >    >  优化窗口"。

*"活动生成* 目标"[是项目当前面向的](https://docs.unity3d.com/Manual/BuildSettings.html)生成平台，用于编译。

性能 *目标* 指示优化工具确定要面向的设备终结点类型。

- *AR 头* 戴显示设备是移动类设备，例如HoloLens
- *VR 独立* 版是移动类设备，例如 Oculus Go 或 Quest
- *VR Tethered* 是电脑支持的设备，例如 Samsung Odyssey、Oculus Rift 或 PC Vive 等。

![MRTK 优化窗口性能目标](../images/performance/OptimizeWindowPerformanceTarget.jpg)

## <a name="setting-optimizations"></a>设置优化

"设置优化"选项卡介绍了 Unity 项目的一些重要呈现配置。 本部分可帮助你自动执行，并告知应该更改哪些设置，以获得最佳性能结果。

绿色选中图标表示已在项目/场景中为此特定设置配置了最佳值。 黄色警告图标指示可以改进当前配置。 单击给定部分中的关联按钮将自动将 Unity 项目/场景中的该设置配置为更理想的值。

![MRTK 优化窗口设置](../images/performance/OptimizeWindow_Settings.png)

### <a name="single-pass-instanced-rendering"></a>单通道实例呈现

[单通道实例呈现](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 是混合现实应用程序最高效的呈现路径。 此配置可确保只对两只眼睛执行一次呈现管道，并且绘制调用在两只眼睛之间实例。

### <a name="depth-buffer-sharing"></a>深度缓冲区共享

为了提高 [全息影像稳定性，](../../performance/hologram-Stabilization.md)开发人员可以共享应用程序的深度缓冲区，该缓冲区为平台提供有关在渲染场景中稳定位置和要稳定哪些全息影像的平台信息。

### <a name="depth-buffer-format"></a>深度缓冲区格式

此外，对于 *AR 头* 戴显示设备，建议在启用深度缓冲区共享（与 24 位共享相比）时，使用 16 位深度格式。 这意味着精度较低，但会节省性能。 如果[由于](https://en.wikipedia.org/wiki/Z-fighting)像素深度计算精度较低而发生 z 冲突，则建议将远剪裁平面移近相机 (例如：50m 而不是 1000m) 。 [](https://docs.unity3d.com/Manual/class-Camera.html)

> [!NOTE]
> 如果使用 *16 位* 深度格式 ，则所需的模具缓冲区效果将不起作用，因为 [Unity](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 不会在此设置中创建模具缓冲区。 相反 *，如果选择 24* 位深度格式，通常会在终结点图形平台上创建一个 [8](https://docs.unity3d.com/Manual/SL-Stencil.html)位模具缓冲区（如果适用）。
>
> 如果使用需要模具缓冲区的 [Mask](https://docs.unity3d.com/Manual/script-Mask.html) 组件，请考虑改为使用 [RectMask2D，](https://docs.unity3d.com/Manual/script-RectMask2D.html) 它不需要模具缓冲区，因此可以与 *16* 位深度格式 结合使用。

### <a name="real-time-global-illumination"></a>实时全球照明

[Unity 中的实时全局](https://docs.unity3d.com/Manual/GIIntro.html) 照明可以提供出色的美观效果，但成本非常高。 全球照明在混合现实中非常昂贵，因此建议在开发中禁用此功能。

> [!NOTE]
> Unity 中的全局照明设置按场景设置，而不是在整个项目中设置一次。

## <a name="scene-analysis"></a>场景分析

" *场景分析* "选项卡旨在告知开发人员场景中当前哪些元素对性能的影响最大。

![MRTK 优化窗口设置场景分析](../images/performance/OptimizeWindow_SceneAnalysis.png)

### <a name="lighting-analysis"></a>照明分析

本部分将检查场景中当前光线的数量，以及应禁用阴影的任何光。 阴影强制转换是一项非常昂贵的操作。

### <a name="polygon-count-analysis"></a>多边形计数分析

该工具还提供多边形计数统计信息。 快速确定哪些 GameObject 在给定场景中具有最高多边形复杂性以针对优化非常有用。

### <a name="unity-ui-raycast-analysis"></a>Unity UI 光线广播分析

图形光线广播操作按 MRTK 中的指针执行，以确定是否有 Unity UI 元素聚焦。 这些光线广播可能非常昂贵，为了帮助提高性能，不应在结果中返回的 UI 元素应禁用为光线广播目标。 每个 [图形](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) 元素都有一个 [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) 属性。 此工具将搜索启用了此属性的文本 UI 元素，因此可能是要禁用的候选项。

## <a name="shader-analysis"></a>着色器分析

[Unity 标准着色器](https://docs.unity3d.com/Manual/shader-StandardShader.html)可以生成非常高质量的游戏视觉效果，但通常不适合混合现实应用程序的性能需求，尤其是此类应用程序通常受 GPU 限制。 因此，建议开发人员利用 [MRTK 标准](../rendering/mrtk-standard-shader.md) 着色器来平衡&与性能。

"*着色器分析*"选项卡使用 Unity 标准着色器扫描当前项目的"资产"文件夹中的材料，或者如果需要，所有未使用混合现实的材料Toolkit着色器。 发现后，开发人员可以使用相应的按钮转换所有材料或单独转换材料。

![MRTK 优化窗口设置器分析](../images/performance/OptimizeWindow_ShaderAnalysis.png)

## <a name="see-also"></a>另请参阅

- [性能](../../performance/perf-getting-started.md)
- [全息影像稳定](../../performance/hologram-stabilization.md)
