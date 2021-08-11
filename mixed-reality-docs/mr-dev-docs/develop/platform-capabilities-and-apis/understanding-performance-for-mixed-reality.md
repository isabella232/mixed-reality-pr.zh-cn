---
title: 了解混合现实的性能
description: 了解高级信息和详细信息，以分析和优化Windows Mixed Reality性能。
author: hferrone
ms.author: v-hferrone
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality， 混合现实， 虚拟现实， VR， MR， 性能， 优化， CPU， GPU
ms.openlocfilehash: 394198011c40f0b90e2c5579f7e0ad8c4019b2a8cefcb1859c544afcbce47df6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193552"
---
# <a name="understanding-performance-for-mixed-reality"></a>了解混合现实的性能

本文介绍了解混合现实应用性能的重要性。  如果应用程序未以最佳帧速率运行，用户体验可能会大大下降。 全息影像看起来不稳定，并且环境的头部跟踪将不准确，从而导致用户体验不佳。 性能必须被视为混合现实开发的第一类功能，而不是一项出色任务。

我们最近发布了一个称为"质量基础"的应用程序，该应用程序涵盖常见性能、设计和环境问题以及适用于HoloLens 2解决方案。 对于以下内容，此应用是一个很好的可视化演示。

> [!div class="nextstepaction"]
> [下载质量基础应用](https://www.microsoft.com/en-us/p/quality-fundamentals/9mwz852q88fw)

下面列出了每个目标平台的"性能帧速率"值。

| 平台 | 目标帧速率 |
|----------|-------------------|
| [HoloLens](/hololens/hololens1-hardware) | 60 FPS |
| [Windows Mixed Reality Ultra个人电脑](../../discover/immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality个人电脑](../../discover/immersive-headset-hardware-details.md) | 60 FPS |

以下框架概述了达到目标帧速率的最佳实践。 建议阅读 Unity [的性能建议一文](../unity/performance-recommendations-for-unity.md) ，获取有关在 Unity 环境中测量和改进帧速率的提示。

## <a name="understanding-performance-bottlenecks"></a>了解性能瓶颈

如果应用帧速率不佳，则第一步是分析和了解应用程序的计算密集型位置。 有两个主要处理器负责渲染场景的工作：CPU 和 GPU，每个处理器处理混合现实应用的不同方面。 可能会发生瓶颈的三个关键位置是： 

1. **应用线程 - CPU** -
    负责应用逻辑，包括处理输入、动画、物理和其他应用逻辑。
2. **呈现线程 - CPU 到 GPU** - 负责将绘图调用提交到 GPU。 当应用想要呈现对象（如多维数据集或模型）时，此线程会向 GPU 发送请求以执行操作。
3. **GPU** - 最常处理应用程序的图形管道，以将三维数据 (模型、纹理等) 转换为像素。 它最终会生成一个 2D 图像，以提交到设备的屏幕。

![帧的生存期](images/lifetime-of-a-frame.png)

通常，HoloLens应用程序将绑定到 GPU，但并不总是绑定。 使用以下工具和技术了解特定应用出现瓶颈的地方。

## <a name="how-to-analyze-your-application"></a>如何分析应用程序

有许多工具可用于了解混合现实应用程序中的性能配置文件和潜在瓶颈。 

下面是一些常用工具，可帮助你收集应用程序的深入分析信息：
- [Intel 图形性能分析器](https://software.intel.com/gpa)
- [Visual Studio图形调试器](/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity 帧调试器](https://docs.unity3d.com/Manual/FrameDebugger.html)
- [Unreal Insights](../unreal/unreal-insights.md)
- [Pix](https://devblogs.microsoft.com/pix/)
- [Unreal 中的 GPU Pofiling](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/GPU/index.html)

### <a name="how-to-profile-in-any-environment"></a>如何在任何环境中分析

确定应用是 GPU 还是 CPU 绑定的一种方式是降低呈现器目标输出的分辨率。 通过减少要计算的像素数，可以减少 GPU 负载。 设备将呈现为较小的纹理，然后向上采样以显示最终图像。

降低渲染分辨率后，如果：
1) 应用程序帧 **速率增加**，那么你可能是 **GPU 绑定**
1) 应用程序帧 **速率保持不变**，则可能是 **CPU 绑定**

>[!NOTE]
>Unity 提供通过 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性在运行时轻松修改应用程序的呈现器目标分辨率的能力。 设备上显示的最终图像具有固定分辨率。 平台将采样较低分辨率的输出，以生成更高的分辨率图像，以在显示器上呈现。 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>如何改进应用程序

### <a name="cpu-performance-recommendations"></a>CPU 性能建议

通常，CPU 上的混合现实应用程序中大多数工作都涉及对场景进行"模拟"和处理应用程序逻辑。 以下区域针对优化：

- 动画
- 物理
- 内存分配
- 复杂算法 (，即 反向运动，路径查找) 

### <a name="gpu-performance-recommendations"></a>GPU 性能建议

#### <a name="understanding-bandwidth-vs-fill-rate"></a>了解带宽与填充速率
在 GPU 上呈现帧时，应用程序受内存带宽或填充速率的约束。

- **内存** 带宽是 GPU 可以从内存进行读取和写入的速率
    - 若要确定带宽限制，请降低纹理质量，并检查帧速率是否提高了。
    - 在 Unity 中，在"编辑 **质量****"Project 设置**  >    >  **[中设置](https://docs.unity3d.com/Manual/class-QualitySettings.html)** 纹理质量。
- **填充** 速率是指 GPU 每秒可绘制的像素数。
    - 若要确定填充速率限制，请降低显示分辨率并检查帧速率是否提高。 
    - 在 Unity 中，使用  *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性

内存带宽通常涉及以下任一项的优化：
1) 较低的纹理分辨率
2) 使用较少的纹理 (法线、反射等) 

填充速率侧重于减少需要为最终呈现的像素计算的操作数，包括：
1) 要呈现/处理的对象数
2) 每个着色器的操作数
3) GPU 阶段到最终结果的数量 (几何着色器、后处理效果等) 
4) 要呈现的像素数 (显示分辨率) 

#### <a name="reduce-polygon-count"></a>减少多边形计数

多边形计数越高，GPU 的操作就越长，因此减少场景中[](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)的多边形数可减少呈现时间。 还有其他一些因素会导致对几何图形进行着色，但多边形计数是确定渲染场景需要多少工作的最简单指标。

#### <a name="limit-overdraw"></a>限制过度绘制

呈现多个对象但不在屏幕上显示时，会发生高过度绘制，因为它们被遮挡对象隐藏。 Imagine后有对象的墙。 所有几何图形都将被处理用于呈现，但只需要呈现不透明的墙，这导致不必要的操作。

#### <a name="shaders"></a>着色器

着色器是小型程序，在 GPU 上运行，在呈现中执行两个重要步骤：
1) 确定应在顶点着色器中绘制的顶点及其在屏幕空间中 (位置) 
    - 顶点着色器按每个网格的顶点执行。
2) 确定像素着色器 (像素的颜色) 
    - 像素着色器按像素执行，由几何图形呈现到目标呈现纹理。

通常，着色器执行许多转换和照明计算。 尽管复杂的照明模型、阴影和其他操作可能会生成出色的结果，但也会带来一个价格。 减少着色器中计算的操作数可以大大减少每个帧 GPU 所需的工作。

##### <a name="shader-coding-recommendations"></a>着色器编码建议

- 尽可能使用双线筛选
- 重新排列表达式以使用 MAD 内部函数同时执行乘法和加法
- 在 CPU 上尽可能预先计算，将常量传递给材料
- **优选从像素着色器移动到顶点着色器的操作**
    - 通常，顶点的数目要小于 (720p 的像素数为921600像素，1080p 为2073600像素，依此类推) 

#### <a name="remove-gpu-stages"></a>删除 GPU 阶段

后期处理效果可能比较昂贵并增加应用程序的填充率，包括诸如 MSAA 这样的抗锯齿技术。 在 HoloLens 中，我们建议避免使用这些技术和其他着色器阶段，如几何、球面和计算着色器。

## <a name="memory-recommendations"></a>内存建议

过多的内存分配和释放操作可能导致性能不一致、冻结帧以及其他不利行为。 在 Unity 中进行开发时，了解内存的注意事项尤其重要，因为内存管理由垃圾回收器控制。

#### <a name="object-pooling"></a>对象池

对象池是一种常用技术，可降低对象的连续分配和释放的成本。 此技术是通过以下方式实现的：分配一个由相同对象构成的较大池并重复使用此池中非活动的可用实例，而不是在各个时间内不断生成和销毁对象。 对象池非常适合应用中生存期可变的可重用组件。

## <a name="see-also"></a>另请参阅
- [针对 Unity 的性能建议](../unity/performance-recommendations-for-unity.md)
- [建议用于 Unity 的设置](../unity/recommended-settings-for-unity.md)
- [针对 Unreal 的性能建议](../unreal/performance-recommendations-for-unreal.md)
- [Unreal 中的材料建议](../unreal/unreal-materials.md)
- [优化3D 模型](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [转换和优化实时3D 模型的最佳做法](/dynamics365/mixed-reality/import-tool/best-practices)
- [适用于 Unreal 的艺术家和设计人员性能准则](https://docs.unrealengine.com/en-US/TestingAndOptimization/PerformanceAndProfiling/Guidelines/index.html)
- [Unreal 的 VR 最佳实践](https://docs.unrealengine.com/en-US/SharingAndReleasing/XRDevelopment/VR/DevelopVR/ContentSetup/index.html)