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
# <a name="optimize-window"></a>优化窗口

"MRTK 优化" 窗口是一个实用工具，可帮助自动执行和通知配置混合现实项目的过程，以便在 Unity 中获得最佳 [性能](../../performance/perf-getting-started.md) 。 此工具通常侧重于呈现配置，当设置为正确预设时，可以节省毫秒的处理。

*活动生成目标* 是项目当前作为编译 [目标的生成平台](https://docs.unity3d.com/Manual/BuildSettings.html)。

*性能目标* 指示优化工具针对的设备终结点类型。

- *AR 耳机* 是移动类设备，如 HoloLens
- *VR 独立* 设备，如 Oculus 或寻找
- *VR 受限* 是电脑设备，例如 Samsung 太空、Oculus RIFT 或 HTC naopak 等。

![MRTK 优化窗口性能目标](../images/performance/OptimizeWindowPerformanceTarget.jpg)

## <a name="setting-optimizations"></a>设置优化

"设置优化" 选项卡介绍了 Unity 项目的一些重要呈现配置。 本部分可帮助自动执行，并通知你应更改哪些设置以获得最佳性能。

绿色复选图标表示已在项目/场景中为此特定设置配置了最优值。 黄色警告图标表示可以提高当前配置。 单击给定节中的关联按钮会自动将 Unity 项目/场景中的该设置配置为更最优的值。

![MRTK 优化窗口设置](../images/performance/OptimizeWindow_Settings.png)

### <a name="single-pass-instanced-rendering"></a>单次传递实例呈现

[单一传递实例呈现](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 是混合现实应用程序的最有效呈现路径。 此配置可确保每个眼睛仅执行一次渲染管道，并且在两个眼睛之间实例化绘图调用。

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

该工具还提供多边形计数统计信息。 这对于快速标识在给定场景中具有最大多边形复杂度的 Gameobject 很有帮助，以便进行优化。

### <a name="unity-ui-raycast-analysis"></a>Unity UI raycast 分析

图形 raycast 操作在 MRTK 中按指针执行，以确定是否有任何 Unity UI 元素处于焦点。 这些 raycasts 的开销可能很高，并且有助于提高性能，不需要在结果中返回的 UI 元素应禁用为 raycast 目标。 每个 [图形](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic.html) 元素都具有 [`Graphic.raycastTarget`](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/UI.Graphic-raycastTarget.html) 属性。 此工具将搜索启用了此属性的文本 UI 元素，因此可能会被禁用。

## <a name="shader-analysis"></a>着色器分析

[Unity 标准着色器](https://docs.unity3d.com/Manual/shader-StandardShader.html)可以为游戏产生非常高质量的视觉效果，但通常不适合用于混合现实应用程序的性能需求，尤其是因为此类应用程序通常是 GPU 限制的。 因此，建议开发人员利用 [MRTK 标准着色器](../rendering/mrtk-standard-shader.md) 来平衡美观 & 图形功能与性能。

" *着色器分析* " 选项卡使用 Unity 标准着色器扫描当前项目的资产文件夹，如果需要，则不使用混合现实工具包的所有材料提供着色。 一旦发现，开发人员就可以转换所有材料或使用适当的按钮单独转换。

![MRTK 优化窗口设置着色器分析](../images/performance/OptimizeWindow_ShaderAnalysis.png)

## <a name="see-also"></a>另请参阅

- [性能](../../performance/perf-getting-started.md)
- [全息影像稳定化](../../performance/hologram-stabilization.md)
