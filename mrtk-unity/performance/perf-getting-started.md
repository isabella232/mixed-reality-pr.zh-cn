---
title: 性能入门
description: 用于了解和调整 MRTK 中性能的文档。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 1ddc057c7f3966375d512a5e4a714dce093412e6
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144860"
---
# <a name="performance"></a>性能

## <a name="getting-started"></a>入门

合理化性能的最简单方法是通过帧速率，或者应用程序每秒呈现一次图像的次数。 必须满足目标帧速率，如目标平台所述 (例如， [Windows Mixed Reality](/windows/mixed-reality/understanding-performance-for-mixed-reality)、 [Oculus](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)等) 。 例如，在 HoloLens 上，目标帧速率为 60 FPS。 低帧率应用程序可能会导致 deteriorated 的用户体验，如之后实际上加剧 [全息度稳定性](../performance/hologram-stabilization.md)、世界跟踪、手动跟踪等。 为帮助开发人员跟踪和实现高质量的帧速率，混合现实工具包提供各种工具和脚本。

### <a name="visual-profiler"></a>可视化探查器

若要在开发生存期内持续跟踪性能，强烈建议始终在运行 & 调试应用程序时显示以帧速率显示的视觉对象。 混合现实工具包提供 [可视化探查器](../features/diagnostics/using-visual-profiler.md) 诊断工具，该工具提供有关应用程序视图中当前 FPS 和内存使用率的实时信息。 可视化探查器可以通过[MRTK 配置文件检查器](../configuration/mixed-reality-configuration-guide.md)下的[诊断系统设置](../features/diagnostics/diagnostics-system-getting-started.md)进行配置。

此外，在设备上运行时，使用可视化探查器跟踪帧速率，而不是在 Unity 编辑器或模拟器中运行，这一点特别重要。 在具有 [发布配置版本](/visualstudio/debugger/how-to-set-debug-and-release-configurations?preserve-view=true&view=vs-2019)的设备上运行时，将描述最准确的性能结果。

> [!NOTE]
> 如果构建 Windows Mixed Reality，请部署 [主配置版本](/windows/mixed-reality/exporting-and-building-a-unity-visual-studio-solution#building_and_deploying_a_unity_visual_studio_solution)

![可视化探查器接口](../features/images/Diagnostics/VisualProfiler.png)

### <a name="optimize-window"></a>优化窗口

" [MRTK 优化" 窗口](../features/tools/optimize-window.md) 提供了信息和自动化工具，可帮助混合现实开发人员设置其环境以实现最佳性能，并识别其场景 & 资产中的潜在瓶颈。 Unity 中的某些密钥配置可帮助为混合现实项目提供相当多的优化结果。

通常，这些设置涉及非常适合混合现实呈现配置。 与传统 3D 图形开发相比，混合现实应用程序是唯一的，因为有两 (屏幕，即 两只眼睛) 整个场景呈现。

可以通过利用 MRTK 优化窗口在 Unity 项目中自动配置下面引用的建议设置。

![MRTK 优化窗口设置](../features/images/performance/OptimizeWindow_Settings.png)

### <a name="unity-profiler"></a>Unity Profiler

[Unity Profiler](https://docs.unity3d.com/Manual/ProfilerWindow.html)是一种有用的工具，可用于在帧级别调查应用程序性能的详细信息。

#### <a name="time-spent-on-the-cpu"></a>CPU 上花费的时间

![示例 Unity Profiler Graph](../features/images/performance/UnityProfilerGraph.png)

为了保持舒适帧速率 (每秒 60 帧) ，应用程序需要实现最大帧时间 16.6 毫秒的 CPU 时间。 为了帮助确定 MRTK 功能的成本，Microsoft Mixed Reality Toolkit 包含一个标记，用于针对代码路径 (帧) 循环。 这些标记使用以下格式来帮助了解使用的特定功能：

```
[MRTK] className.methodName
```

> [!Note]
> 方法名称后可能有其他数据。 这用于标识有条件执行的、可能成本高昂的功能，对应用程序代码进行少量更改可能会避免这些功能。

![示例 Unity Profiler 层次结构](../features/images/performance/UnityProfilerHierarchy.png)

本示例已扩展层次结构，以显示在分析帧期间 WindowsMixedRealityArticulatedHand 类的 UpdateHandData 方法消耗 0.44 毫秒的 CPU 时间。 此数据可用于帮助确定性能问题是与应用程序代码相关还是与系统中其他位置相关。

强烈建议开发人员以类似的方式检测应用程序代码。 应用程序代码检测的主要关注区域位于事件处理程序中，因为这些方法在引发事件时向 MRTK 更新循环收费。 MRTK 更新循环中的帧时间过长可能表示事件处理程序方法中的代码成本高昂。

## <a name="recommended-settings-for-unity"></a>建议用于 Unity 的设置

### <a name="single-pass-instanced-rendering"></a>Single-Pass 实例呈现

Unity 中的 XR 的默认呈现配置为 [多步](https://docs.unity3d.com/ScriptReference/StereoRenderingPath.MultiPass.html)。 此设置指示 Unity 执行整个渲染管道两次，一次针对每个眼睛。 这可以通过选择 [单一传递实例呈现](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 来进行优化。 此配置利用 [呈现目标阵列](https://en.wikipedia.org/wiki/Multiple_Render_Targets) ，使其能够在每个眼睛的适当 [渲染目标](https://en.wikipedia.org/wiki/Render_Target) 中执行单个绘图调用。 此外，此模式允许在呈现管道的单个执行中完成所有呈现。 因此，选择单个 Pass 实例呈现作为混合现实应用程序的呈现路径可 [节省大量时间，这是 CPU & GPU](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) ，是推荐的呈现配置。

但是，为了每个网格都发出单个绘图调用，每个网格都必须支持 [GPU 实例](https://docs.unity3d.com/Manual/GPUInstancing.html) 化。 实例化允许 GPU 跨两个眼睛多路复用调用。 Unity 内置着色 [器和 MRTK 标准着色器](../features/rendering/mrtk-standard-shader.md) 默认情况下包含着色器代码中必要的实例化说明。 如果为 Unity 编写自定义着色器，则可能需要更新这些着色器以支持单一传递实例呈现。

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

Unity 提供了 [预设来控制](https://docs.unity3d.com/Manual/class-QualitySettings.html) 每个平台终结点的呈现质量。 这些预设控制可启用的图形功能，如阴影、抗锯齿、全局照明等。 建议降低这些设置，并优化在呈现过程中执行的计算数目。

*步骤1：* 更新混合现实 Unity 项目以使用 *低质量* 级别设置  
**编辑**  > **项目设置**，然后选择 "**质量**" 类别 > 为 UWP 平台选择 *低质量*

*步骤2：* 对于每个 Unity 场景文件，禁用 [实时全局照明](https://docs.unity3d.com/Manual/LightMode-Realtime.html)  
**窗口**  > **呈现**  > **照明设置**  > [取消 *选中"实时全球照明"*](https://docs.unity3d.com/Manual/GlobalIllumination.html)

### <a name="depth-buffer-sharing-hololens"></a>HoloLens (深度缓冲区) 

如果针对 Windows Mixed Reality平台（尤其是 HoloLens）进行开发，在 *"XR* 设置"下启用深度缓冲区共享有助于全息 [影像稳定](../performance/hologram-stabilization.md)。 但是，深度缓冲区的处理可能会产生性能成本，尤其是在使用 [24 位深度格式 时](https://docs.unity3d.com/ScriptReference/PlayerSettings.VRWindowsMixedReality-depthBufferFormat.html)。 因此， *强烈建议将* 深度缓冲区配置为 16 位精度。

如果[由于位](https://en.wikipedia.org/wiki/Z-fighting)格式较低而发生 z 冲突，请确认所有[](https://docs.unity3d.com/Manual/class-Camera.html)相机的远剪裁平面设置为应用程序可能的最低值。 默认情况下，Unity 将远剪裁平面设置为 1000m。 在 HoloLens 上，50 米远的剪辑平面通常足以用于大多数应用程序方案。

> [!NOTE]
> 如果使用 *16 位* 深度格式 ，则所需的模具缓冲区效果将不起作用，因为 [Unity](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 不会在此设置中创建模具缓冲区。 相反 *，如果选择 24* 位深度格式，通常会在终结点图形平台上创建一个 8 位模具缓冲区（如果适用）。
>
> 如果使用需要模具缓冲区的 [Mask](https://docs.unity3d.com/Manual/script-Mask.html) 组件，请考虑改为使用 [RectMask2D，](https://docs.unity3d.com/Manual/script-RectMask2D.html) 它不需要模具缓冲区，因此可以与 *16* 位深度格式 结合使用。

> [!NOTE]
> 若要快速确定场景中哪些对象不会以可视方式写入深度缓冲区，可以使用 MRTK 配置文件中的[](../configuration/mixed-reality-configuration-guide.md#editor-utilities)"编辑器设置"下的"呈现深度缓冲区"实用工具。

### <a name="optimize-mesh-data"></a>优化网格数据

" [优化网格数据](https://docs.unity3d.com/ScriptReference/PlayerSettings-stripUnusedMeshComponents.html) "设置尝试删除应用程序中未使用的顶点属性。 设置通过运行生成中每个网格上每个材料上的每个着色器传递来实现此目标。 这适用于游戏数据大小和运行时性能，但可能会极大地阻碍生成时间。

建议在开发过程中禁用此设置，并在创建 "主" 生成期间重新启用。 此设置可在 "**编辑**  >  **项目设置**  >  **播放器**  >  **其他设置**" "  >  **优化网格数据**" 下找到。

## <a name="general-recommendations"></a>常规建议

对于混合现实开发人员而言，性能可能是不明确的不断变化的挑战，而合理化性能的知识非常大。 不过，还需要了解一些常规建议，以便了解如何使用应用程序的性能。

简化应用程序在 *CPU* 或 *GPU* 上运行的部分的执行，从而识别应用是否已被任一组件所绑定，都非常有用。  可能存在跨这两个处理单元的瓶颈和一些需要仔细调查的独特方案。 但对于入门，最好抓住应用程序的执行时间最长的时间。

### <a name="gpu-bounded"></a>GPU 限制

由于混合现实应用程序的大多数平台都在使用 [stereoscopic 呈现](https://en.wikipedia.org/wiki/Stereoscopy)，因此很常见的情况是 GPU 限制，这是因为呈现 "全宽" 屏幕的性质。 Futhermore 的移动混合现实平台（如 HoloLens 或 Oculus）将受到移动类 CPU & GPU 处理能力的限制。

当重点介绍 GPU 时，通常有两个重要阶段，应用程序必须每隔一帧就能完成。

1. 执行 [顶点着色器](https://en.wikipedia.org/wiki/Shader#Vertex_shaders)
2. 执行 [像素着色器](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) (也称为片段着色器) 

如果没有深入探讨计算机图形 & [渲染管道](https://en.wikipedia.org/wiki/Graphics_pipeline)的复杂字段，则每个着色器阶段都是在 GPU 上运行以生成以下项目的程序。

1. 顶点着色器将网格顶点转换为屏幕空间中的坐标 (即 按顶点执行的代码) 
2. 像素着色器计算给定像素和网格片段的绘图颜色 (即 每像素的代码执行) 

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

Unity 中降低性能的最常见错误之一是在运行时克隆材料。 如果 GameObject 共享相同的材料且/或网格相同，则可以通过静态批处理、动态批处理和 *[GPU](https://docs.unity3d.com/Manual/GPUInstancing.html)* 实例化等 *[](https://docs.unity3d.com/Manual/DrawCallBatching.html)* 技术，将 *[](https://docs.unity3d.com/Manual/DrawCallBatching.html)* GameObject 优化为单个绘图调用。 但是，如果开发人员在运行时修改 [呈现器材料](https://docs.unity3d.com/ScriptReference/Renderer-material.html) 的属性，则 Unity 将创建分配的材料的克隆副本。

例如，如果一个场景中有一个100的多维数据集，则开发人员可能需要在运行时为每个多维数据集分配一种独特的颜色。 C # 中的 [*呈现*](https://docs.unity3d.com/ScriptReference/Material-color.html) 器的访问权限将使 Unity 在内存中为此特定呈现器/GameObject 创建一个新材料。 每个100多维数据集都有其自己的材料，因此它们不能合并为一个绘图调用，而是会成为100，将来自 CPU 的调用请求绘制到 GPU。

为了克服这一障碍，并为每个多维数据集分配唯一的颜色，开发人员应利用 [MaterialPropertyBlock](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html)。

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

Unity 提供了编辑器中内置的极佳性能工具。

- [Unity 探查器](https://docs.unity3d.com/Manual//Profiler.html)
- [Unity 框架调试器](https://docs.unity3d.com/Manual/FrameDebugger.html)

如果估计一个着色器与另一个着色器之间的粗略性能折衷，则编译每个着色器并查看每个着色器阶段的操作数很有用。 为此，可以选择 [着色器资产](https://docs.unity3d.com/Manual/class-Shader.html) ，并单击 " *编译和显示代码* " 按钮。 这将编译所有着色器变体，并打开 visual studio 并显示结果。 注意：生成的统计信息结果可能因使用给定着色器对材料启用的功能而异。 Unity 只会编译当前项目中直接使用的着色器变体。

Unity 标准着色器统计信息示例

![Unity 标准着色器统计信息1](../features/images/performance/UnityStandardShader-Stats.PNG)

MRTK 标准着色器统计信息示例

![MRTK 标准着色器统计信息2](../features/images/performance/MRTKStandardShader-Stats.PNG)

## <a name="see-also"></a>另请参阅

### <a name="unity"></a>Unity

- [适用于初学者的 Unity 性能优化](https://www.youtube.com/watch?v=1e5WY2qf600)
- [Unity 性能优化教程](https://unity3d.com/learn/tutorials/topics/performance-optimization)
- [Unity 优化最佳做法](https://docs.unity3d.com/Documentation/Manual/BestPracticeUnderstandingPerformanceInUnity.html)
- [优化图形性能](https://docs.unity3d.com/Manual/OptimizingGraphicsPerformance.html)
- [移动优化实用指南](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

- [适用于 Unity 的推荐设置](/windows/mixed-reality/recommended-settings-for-unity)
- [了解混合现实的性能](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [针对 Unity 的性能建议](/windows/mixed-reality/performance-recommendations-for-unity)
- [Windows Unity 的事件跟踪指南](https://docs.unity3d.com/uploads/ExpertGuides/Analyzing_your_game_performance_using_Event_Tracing_for_Windows.pdf)

### <a name="oculus"></a>Oculus

- [性能准则](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-guidelines/)
- [性能工具](https://developer.oculus.com/documentation/pcsdk/latest/concepts/dg-performance-tools/)

### <a name="mesh-optimization"></a>网格优化

- [优化3D 模型](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [转换和优化实时3D 模型的最佳做法](/dynamics365/mixed-reality/import-tool/best-practices)