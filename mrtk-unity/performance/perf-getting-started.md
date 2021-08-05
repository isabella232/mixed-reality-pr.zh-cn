---
title: 性能
description: 用于了解和调整 MRTK 中的预格式的文档。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 50128100d058b5ec3bca7eac523c78287ce657925c3ac116e4336174e34e75c8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211171"
---
# <a name="performance"></a>性能

## <a name="getting-started"></a>入门

使性能合理化的最简单方法是帧速率或应用程序每秒呈现图像次数。 必须满足目标帧速率，如目标平台所述， (帧速率 [](/windows/mixed-reality/understanding-performance-for-mixed-reality) [Windows Mixed Reality、Oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)等) 。 例如，在HoloLens，目标帧速率为 60 FPS。 帧速率较低的应用程序可能会导致用户体验变长，例如全息影像稳定化、[](../performance/hologram-stabilization.md)世界跟踪、手部跟踪等。 为了帮助开发人员跟踪并实现质量帧速率，混合现实Toolkit提供各种工具和脚本。

### <a name="visual-profiler"></a>可视化探查器

若要在开发生存期内持续跟踪性能，强烈建议在运行帧速率视觉对象时始终显示&调试应用程序。 混合现实Toolkit提供了[Visual Profiler](../features/diagnostics/using-visual-profiler.md)诊断工具，该工具提供有关应用程序视图中当前 FPS 和内存使用情况实时信息。 可以通过"诊断系统"配置 Visual Profiler，设置"MRTK[配置文件检查](../features/diagnostics/diagnostics-system-getting-started.md)[器"下](../configuration/mixed-reality-configuration-guide.md)。

此外，在设备上运行时，使用 Visual Profiler 跟踪帧速率尤为重要，而不是在 Unity 编辑器或仿真器中运行。 使用发布配置版本 在设备上运行时，将描述最 [准确的性能结果](/visualstudio/debugger/how-to-set-debug-and-release-configurations?preserve-view=true&view=vs-2019)。

> [!NOTE]
> 如果生成时Windows Mixed Reality，则使用 MASTER[配置生成进行部署](/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)

![Visual Profiler 接口](../features/images/Diagnostics/VisualProfiler.png)

### <a name="optimize-window"></a>优化窗口

[MRTK 优化窗口](../features/tools/optimize-window.md)提供了信息和自动化工具，以帮助混合现实开发人员设置其环境，以便获得最佳的性能结果，并确定其场景中的潜在瓶颈&资产。 Unity 中的某些关键配置可以帮助为混合现实项目提供大幅优化的结果。

通常，这些设置涉及非常适合混合现实呈现配置。 与传统 3D 图形开发相比，混合现实应用程序是唯一的，因为有两 (屏幕，即 两只眼睛) 整个场景呈现。

可以通过利用 MRTK 优化窗口在 Unity 项目中自动配置下面引用的建议设置。

![MRTK 优化窗口设置](../features/images/performance/OptimizeWindow_Settings.png)

### <a name="unity-profiler"></a>Unity Profiler

[Unity Profiler](https://docs.unity3d.com/Manual/ProfilerWindow.html)是一种有用的工具，可用于在帧级别调查应用程序性能的详细信息。

#### <a name="time-spent-on-the-cpu"></a>CPU 上花费的时间

![示例 Unity Profiler Graph](../features/images/performance/UnityProfilerGraph.png)

为了保持舒适帧速率 (每秒 60 帧) ，应用程序需要实现最大帧时间 16.6 毫秒的 CPU 时间。 为了帮助确定 MRTK 功能的成本，Microsoft Mixed Reality Toolkit包含一个标记，用于每个帧 (代码) 内循环。 这些标记使用以下格式来帮助了解使用的特定功能：

```
[MRTK] className.methodName
```

> [!Note]
> 方法名称后可能有其他数据。 这用于标识有条件执行的、可能成本高昂的功能，对应用程序代码进行少量更改可能会避免这些功能。

![示例 Unity Profiler 层次结构](../features/images/performance/UnityProfilerHierarchy.png)

本示例已扩展层次结构，以显示在分析帧期间 WindowsMixedRealityArticulatedHand 类的 UpdateHandData 方法消耗 0.44 毫秒的 CPU 时间。 此数据可用于帮助确定性能问题是与应用程序代码相关还是与系统中其他位置相关。

强烈建议开发人员以类似的方式检测应用程序代码。 应用程序代码检测的主要关注区域位于事件处理程序中，因为这些方法在引发事件时向 MRTK 更新循环收费。 MRTK 更新循环中的帧时间过长可能表示事件处理程序方法中的代码成本高昂。

## <a name="recommended-settings-for-unity"></a>建议用于 Unity 的设置

### <a name="single-pass-instanced-rendering"></a>Single-Pass实例呈现

Unity 中 XR 的默认呈现配置是 [多传递](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html)。 此设置指示 Unity 执行整个呈现管道两次，每个眼睛执行一次。 这可以通过改为选择"单 [通道实例呈现"进行优化](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 。 此配置利用 [呈现器](https://en.wikipedia.org/wiki/Multiple_Render_Targets) 目标数组，能够执行单个绘制调用，该调用将实例放入每个眼睛 [的适当](https://en.wikipedia.org/wiki/Render_Target) 呈现目标。 此外，此模式允许在单个呈现管道执行中完成所有呈现。 因此，选择"单次传递实例呈现"作为混合现实应用程序的呈现路径可以在 CPU 和 GPU 上节省大量 [&，](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) 这是推荐的呈现配置。

但是，若要针对每个眼睛发出每个网格的单个绘图调用，所有着色器都必须支持 [GPU](https://docs.unity3d.com/Manual/GPUInstancing.html) 实例化。 实例化允许 GPU 跨两只眼睛多路绘制调用。 默认情况下，Unity 内置着色器以及 [MRTK 标准](../features/rendering/mrtk-standard-shader.md) 着色器在着色器代码中包含必要的实例化说明。 但是，如果为 Unity 编写自定义着色器，可能需要更新这些着色器以支持单通道实例呈现。

#### <a name="example-code-for-custom-shader"></a>[自定义着色器的示例代码](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

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

### <a name="quality-settings"></a>质量设置

Unity [提供预设来控制每个](https://docs.unity3d.com/Manual/class-QualitySettings.html) 平台终结点的呈现质量。 这些预设控制可以启用的图形功能，例如阴影、抗锯齿、全局照明等。 建议降低这些设置，并优化呈现期间执行的计算数。

*步骤 1：* 更新混合现实 Unity 项目以使用 *低质量* 级别设置  
**编辑**  > **Project 设置，** 然后选择"质量"类别 *>为* UWP 平台选择"低质量"

*步骤 2：* 对于每个 Unity 场景文件，请禁用 [实时全局照明](https://docs.unity3d.com/Manual/LightMode-Realtime.html)  
**窗口**  > **呈现**  > **照明设置**  > [取消 *选中"实时全球照明"*](https://docs.unity3d.com/Manual/GlobalIllumination.html)

### <a name="depth-buffer-sharing-hololens"></a>深度缓冲区共享 (HoloLens) 

如果针对 Windows Mixed Reality 平台（尤其是 HoloLens）进行开发，在 *XR* 设置 启用深度缓冲区共享有助于全息 [影像稳定](../performance/hologram-stabilization.md)。 但是，深度缓冲区的处理可能会产生性能成本，尤其是在使用 [24 位深度格式 时](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html)。 因此， *强烈建议将* 深度缓冲区配置为 16 位精度。

如果[由于位](https://en.wikipedia.org/wiki/Z-fighting)格式较低而发生 z 冲突，请确认所有[](https://docs.unity3d.com/Manual/class-Camera.html)相机的远剪裁平面设置为应用程序可能的最低值。 默认情况下，Unity 将远剪裁平面设置为 1000m。 在HoloLens，对于大多数应用程序方案，50 米远的剪辑平面通常已足够。

> [!NOTE]
> 如果使用 *16 位* 深度格式 ，则所需的模具缓冲区效果将不起作用，因为 [Unity](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 不会在此设置中创建模具缓冲区。 相反 *，如果选择 24* 位深度格式，通常会在终结点图形平台上创建一个 8 位模具缓冲区（如果适用）。
>
> 如果使用需要模具缓冲区的 [Mask](https://docs.unity3d.com/Manual/script-Mask.html) 组件，请考虑改为使用 [RectMask2D，](https://docs.unity3d.com/Manual/script-RectMask2D.html) 它不需要模具缓冲区，因此可以与 *16* 位深度格式 结合使用。

> [!NOTE]
> 若要快速确定场景中哪些对象未以可视方式写入深度缓冲区，可以使用 MRTK 配置文件中 [](../configuration/mixed-reality-configuration-guide.md#editor-utilities)"编辑器"设置"呈现 *深度缓冲区*"实用工具。

### <a name="optimize-mesh-data"></a>优化网格数据

" [优化网格数据](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html) "设置尝试删除应用程序中未使用的顶点属性。 设置通过运行生成中每个网格上每个材料上的每个着色器传递来实现此目标。 这适用于游戏数据大小和运行时性能，但可能会极大地阻碍生成时间。

建议在开发期间禁用此设置，并创建"主"生成期间重新启用此设置。 可以在"编辑播放器""其他Project 设置  >    >    >  **优化网格**  >  **设置"下找到设置**。

## <a name="general-recommendations"></a>常规建议

对于混合现实开发人员来说，性能可能是不明确且不断变化的挑战，使性能合理化的知识范围非常广泛。 不过，对于了解如何实现应用程序的性能，有一些常规建议。

将应用程序的执行简化为在 *CPU* 或 *GPU* 上运行的片段非常有用，从而确定应用是否受任一组件的约束。  可能同时存在跨处理单元的瓶颈，以及必须仔细调查的一些独特方案。 但是，对于入门，可以掌握应用程序执行时间最多的位置。

### <a name="gpu-bounded"></a>GPU 边界

由于混合现实应用程序的大多数平台都使用立体声[](https://en.wikipedia.org/wiki/Stereoscopy)渲染，因此由于呈现"双宽"屏幕的性质，GPU 绑定很常见。 此外，移动混合现实平台（如 HoloLens 或 Oculus Quest）将受限于移动类 CPU 和 GPU &处理能力。

专注于 GPU 时，应用程序通常需要完成每个帧的两个重要阶段。

1. 执行 [顶点着色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)
2. 执行 [像素着色器 (](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) 也称为片段着色器) 

如果不深入了解计算机图形和& [的复杂字段，](https://en.wikipedia.org/wiki/Graphics_pipeline)每个着色器阶段都是一个在 GPU 上运行的程序，用于生成以下内容。

1. 顶点着色器将网格顶点转换为屏幕空间中的坐标 (即 每个顶点所执行) 
2. 像素着色器计算给定像素和网格片段绘制的颜色 (即 代码按像素执行) 

在性能优化方面，通常更希望专注于优化像素着色器中的操作。 应用程序可能只需要绘制一个只有 8 个顶点的立方体。 但是，多维数据集占用的屏幕空间可能为数百万像素。 因此，如果在像素着色器上减少比顶点着色器少 10 个操作，减少着色器代码可以显著节省更多工作。

这是利用 [MRTK](../features/rendering/mrtk-standard-shader.md) 标准着色器的主要原因之一，因为与 Unity 标准着色器相比，此着色器执行每个像素 & 顶点的指令通常更少，同时获得类似的美观结果。

|    CPU 优化      |             GPU 优化              |
|---------------------------|--------------------------------------------|
| 应用模拟逻辑      | 呈现操作 |
| 简化物理          | 减少照明计算 |
| 简化动画       | 减少多边形计数&可绘制对象数 |
| 管理垃圾回收 | 减少透明对象数 |
| 缓存引用          | 避免后处理/全屏效果  |

### <a name="draw-call-instancing"></a>绘制调用实例化

Unity 中降低性能的最常见错误之一是在运行时克隆材料。 如果 GameObject 共享相同的材料且/或网格相同，则可以通过静态批处理、动态批处理和 *[GPU](https://docs.unity3d.com/Manual/GPUInstancing.html)* 实例化等 *[](https://docs.unity3d.com/Manual/DrawCallBatching.html)* 技术，将 *[](https://docs.unity3d.com/Manual/DrawCallBatching.html)* GameObject 优化为单个绘图调用。 但是，如果开发人员在运行时修改呈现器材料的属性[](https://docs.unity3d.com/ScriptReference/Renderer-material.html)，Unity 将创建所分配材料的克隆副本。

例如，如果场景中有 100 个立方体，开发人员可能希望在运行时为每个立方体分配唯一的颜色。 访问 C# [*中的 renderer.material.color*](https://docs.unity3d.com/ScriptReference/Material-color.html) 将使 Unity 在内存中为此特定呈现器/GameObject 创建新的材料。 100 个立方体中每个都有其自己的材料，因此它们不能合并到一个绘图调用中，而是变成从 CPU 到 GPU 的 100 个绘图调用请求。

若要克服此障碍，并仍然为每个立方体分配唯一的颜色，开发人员应利用 [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)。

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

## <a name="unity-performance-tools"></a>Unity 性能工具

Unity 提供内置于编辑器中的出色性能工具。

- [Unity Profiler](https://docs.unity3d.com/Manual//Profiler.html)
- [Unity 帧调试器](https://docs.unity3d.com/Manual/FrameDebugger.html)

如果估计一个着色器与另一个着色器之间的大致性能权衡，则编译每个着色器并查看每个着色器阶段的操作数非常有用。 这可以通过选择 [着色器资产](https://docs.unity3d.com/Manual/class-Shader.html) 并单击"编译和显示代码 *"按钮* 完成。 这会编译所有着色器变体，并打开具有结果的 Visual Studio。 注意：生成的统计信息结果可能会有所不同，具体取决于已使用给定着色器对材料启用了哪些功能。 Unity 将仅编译当前项目中直接使用的着色器变体。

Unity 标准着色器统计信息示例

![Unity 标准着色器统计信息 1](../features/images/performance/UnityStandardShader-Stats.PNG)

MRTK 标准着色器统计信息示例

![MRTK 标准着色器统计信息 2](../features/images/performance/MRTKStandardShader-Stats.PNG)

## <a name="see-also"></a>另请参阅

### <a name="unity"></a>Unity

- [适合初学者的 Unity 性能优化](https://www.youtube.com/watch?v=1e5WY2qf600)
- [Unity 性能优化教程](https://unity3d.com/learn/tutorials/topics/performance-optimization)
- [Unity 优化最佳做法](https://docs.unity3d.com/Documentation/Manual/BestPracticeUnderstandingPerformanceInUnity.html)
- [优化图形性能](https://docs.unity3d.com/Manual/OptimizingGraphicsPerformance.html)
- [移动优化实用指南](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

- [建议设置 Unity 的推荐方法](/windows/mixed-reality/recommended-settings-for-unity)
- [了解混合现实的性能](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [针对 Unity 的性能建议](/windows/mixed-reality/performance-recommendations-for-unity)
- [适用于 Windows Unity 的事件跟踪指南](https://docs.unity3d.com/uploads/ExpertGuides/Analyzing_your_game_performance_using_Event_Tracing_for_Windows.pdf)

### <a name="oculus"></a>Oculus

- [性能准则](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)
- [性能工具](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-tools/)

### <a name="mesh-optimization"></a>网格优化

- [优化三维模型](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [转换和优化实时 3D 模型最佳做法](/dynamics365/mixed-reality/import-tool/best-practices)
