---
title: 了解混合现实的性能
description: 了解用于分析和优化 Windows Mixed Reality 应用性能的高级信息和详细信息。
author: hferrone
ms.author: v-vtieto
ms.date: 08/16/2021
ms.topic: article
keywords: Windows Mixed Reality，Mixed reality，虚拟现实，VR，先生，性能，优化，CPU，GPU
ms.openlocfilehash: 9304e4cd80f0929b87a29873ad07329700ec463f
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244198"
---
# <a name="understanding-performance-for-mixed-reality"></a>了解混合现实的性能

本文介绍了如何了解混合现实应用的性能的重要性。  如果你的应用程序不能以最佳帧速率运行，用户体验会大大降低。 全息影像会显得不稳定，因此不会对环境进行打印头跟踪，导致用户体验不佳。 对于混合现实开发而言，必须将性能视为第一类功能，而不是波兰语任务。

我们最近发布了一个名为 "质量基础" 的应用程序，该应用程序涵盖 HoloLens 2 应用的常见性能、设计和环境问题和解决方案。 此应用程序非常适合以下内容。

> [!div class="nextstepaction"]
> [下载质量基础应用](https://www.microsoft.com/en-us/p/quality-fundamentals/9mwz852q88fw)

下面列出了每个目标平台的高性能帧速率值。

| 平台 | 目标帧速率 |
|----------|-------------------|
| [HoloLens](/hololens/hololens1-hardware) | 60 FPS |
| [Windows Mixed Reality UltraPCs](../../discover/immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed RealityPCs](../../discover/immersive-headset-hardware-details.md) | 60 FPS |

下面的框架概述了命中目标帧速率的最佳实践。 有关在 Unity 环境中测量和提高帧率的提示，我们建议你阅读 [有关 unity 的性能建议一文](../unity/performance-recommendations-for-unity.md) 

## <a name="understanding-performance-bottlenecks"></a>了解性能瓶颈

如果你的应用程序具有绩效不佳的帧速率，则第一步是分析并了解应用程序的计算工作量。 有两个主要处理器负责呈现场景： CPU 和 GPU，分别处理混合现实应用的不同方面。 瓶颈可能出现在以下三个关键位置： 

1. **应用线程-CPU** -
    负责应用逻辑，包括处理输入、动画、物理学和其他应用逻辑。
2. **将线程 CPU 呈现到 gpu** ，负责将绘图调用提交到 gpu。 当应用程序想要呈现某个对象（如多维数据集或模型）时，此线程会向 GPU 发送请求以执行操作。
3. **GPU** -最常见的情况是处理应用程序的图形管道，以将3d 数据 (模型、纹理等) 转换为像素。 它最终会生成一个要提交到设备屏幕的二维图像。

![帧的生存期](images/lifetime-of-a-frame.png)

通常，HoloLens 应用程序将是 GPU 绑定的，但并不总是如此。 使用下面的工具和技术来了解你的特定应用程序的瓶颈所在。

## <a name="how-to-analyze-your-application"></a>如何分析应用程序

有许多工具可让你了解混合现实应用程序的性能配置文件和潜在瓶颈。 

下面是一些常用工具，可帮助你收集应用程序的深入分析信息：
- [Intel 图形性能分析器](https://software.intel.com/gpa)
- [Visual Studio图形调试器](/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [Unity 探查器](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity 框架调试器](https://docs.unity3d.com/Manual/FrameDebugger.html)
- [Unreal Insights](../unreal/unreal-insights.md)
- [PIX](https://devblogs.microsoft.com/pix/)
- [Unreal 中的 GPU Pofiling](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/GPU/index.html)

### <a name="how-to-profile-in-any-environment"></a>如何在任何环境中进行分析

确定应用是 GPU 还是 CPU 限制的一种方法是降低呈现器目标输出的分辨率。 通过减少要计算的像素数，你可以减少 GPU 负载。 设备将呈现为一个较小的纹理，然后显示一个示例，显示最终图像。

降低呈现分辨率后，如果：
1) 应用程序的帧速率增加，则可能 **会****绑定 GPU**
1) 应用程序的以帧速率为 **变化**，则可能是 **CPU 已绑定**

>[!NOTE]
>Unity 提供了在运行时通过 *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性轻松修改应用程序的呈现目标解析的能力。 设备上提供的最终映像具有固定的分辨率。 平台将采样低分辨率输出，以生成更高分辨率的图像，以便在显示时呈现。 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>如何改进应用程序

### <a name="cpu-performance-recommendations"></a>CPU 性能建议

通常，在 CPU 上混合现实应用程序中的大部分工作都涉及到执行场景的 "模拟" 和处理应用程序逻辑。 以下区域用于优化：

- 动画
- 物理
- 内存分配
- 复杂算法 (即 反向运动，路径查找) 

### <a name="gpu-performance-recommendations"></a>GPU 性能建议

#### <a name="understanding-bandwidth-vs-fill-rate"></a>了解带宽与填充速率
在 GPU 上呈现帧时，应用程序可以按内存带宽或填充速率进行绑定。

- **内存带宽** 是 GPU 可从内存执行读取和写入操作的速率
    - 若要确定带宽限制，请降低纹理质量并检查帧速率是否已提高。
    - 在 Unity 中，在 "**编辑**"   >  **Project 设置**  >  **[质量 "设置](https://docs.unity3d.com/Manual/class-QualitySettings.html)** 更改纹理质量。
- **填充速率** 是指每秒可以通过 GPU 绘制的像素。
    - 若要确定填充速率限制，请降低显示分辨率，并检查是否改进了帧速率。 
    - 在 Unity 中，使用  *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性

内存带宽一般涉及优化到以下任一操作：
1) 更低的纹理分辨率
2) 使用更少纹理 (法线、镜面等) 

填充速率侧重于减少需要为最终呈现的像素计算的操作的数量，包括：
1) 要呈现/处理的对象数
2) 每个着色器的操作数
3) 最终结果 (几何着色器、后处理效果等的 GPU 阶段数) 
4) 显示分辨率 (呈现的像素数) 

#### <a name="reduce-polygon-count"></a>减少多边形计数

较大的多边形计数会导致更多的 GPU 操作，因此减少场景中 [的多边形数量](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) 会减少渲染时间。 还有其他一些因素会使几何变得昂贵，但多边形计数是确定呈现场景所需的工作量的最简单指标。

#### <a name="limit-overdraw"></a>限制过度绘制

当显示多个对象，但在屏幕上未显示过度绘制（因为它们已被 occluding 对象隐藏）时，会发生高。 Imagine 查看在其后面有对象的墙。 所有几何都将进行处理以便呈现，但只需呈现不透明的墙壁，这将导致不必要的操作。

#### <a name="shaders"></a>着色器

着色器是在 GPU 上运行的小程序，执行以下两个重要步骤：
1) 确定哪些顶点应该绘制在顶点着色器 (的哪个顶点) 
    - 对于每个网格，顶点着色器都按顶点执行。
2) 确定像素着色器 (的每个像素的颜色) 
    - 像素着色器按每个像素执行，并由几何图形呈现给目标呈现纹理。

通常，着色器会执行许多转换和照明计算。 尽管复杂的照明模型、阴影和其他操作可能会产生极好的结果，但它们也具有价格。 减少着色器中计算的操作数可以极大地减少 GPU 每帧所需的工作量。

##### <a name="shader-coding-recommendations"></a>着色器编码建议

- 尽可能使用双线性筛选
- 重新排列表达式以使用 MAD 内部函数执行相乘并同时添加
- 在 CPU 上尽可能 Precalculate，并将其作为常量传递给材料
- **倾向于将操作从像素着色器移动到顶点着色器**
    - 通常，顶点数比像素数小得多 (720p 为 921，600 像素，1080p 为 2，073，600 像素，以此类) 

#### <a name="remove-gpu-stages"></a>删除 GPU 阶段

后期处理效果可能很昂贵，会增加应用程序的填充速率，包括 MSAA 等抗锯齿技术。 在HoloLens，我们建议避免这些技术和其他着色器阶段，例如几何图形、外壳和计算着色器。

## <a name="memory-recommendations"></a>内存建议

过多的内存分配和释放操作可能会导致性能不一致、帧冻结和其他有害行为。 在 Unity 中开发时了解内存注意事项尤为重要，因为内存管理由垃圾回收器控制。

#### <a name="object-pooling"></a>对象池

对象池是一种常用技术，用于降低连续分配和释放对象的成本。 此技术是通过以下方式实现的：分配一个由相同对象构成的较大池并重复使用此池中非活动的可用实例，而不是在各个时间内不断生成和销毁对象。 对象池非常适合应用中生存期可变的可重用组件。

## <a name="see-also"></a>另请参阅
- [针对 Unity 的性能建议](../unity/performance-recommendations-for-unity.md)
- [建议用于 Unity 的设置](../unity/recommended-settings-for-unity.md)
- [针对 Unreal 的性能建议](../unreal/performance-recommendations-for-unreal.md)
- [Unreal 中的材料建议](../unreal/unreal-materials.md)
- [优化三维模型](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [转换和优化实时三维模型最佳做法](/dynamics365/mixed-reality/import-tool/best-practices)
- [Unreal 的艺术家和设计人员的性能准则](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/Guidelines/index.html)
- [Unreal 的 VR 最佳做法](https://docs.unrealengine.com/en-US/SharingAndReleasing/XRDevelopment/VR/DevelopVR/ContentSetup/index.html)