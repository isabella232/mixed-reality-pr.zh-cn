---
title: Quality Fundamentals
description: 了解设计混合现实应用程序的质量基础知识。
author: qianw211
ms.author: v-qianwen
ms.date: 07/15/2021
ms.topic: article
keywords: 质量基础，案例研究，项目，示例，MRTK，混合现实 Toolkit，Unity，示例应用，示例应用，开源，Microsoft Store，HoloLens，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: 69c6a55b95937c0c6af4920f6ffe0929eebe76ee
ms.sourcegitcommit: 82f7db75d8ecc7ac89c76b0db504126cbcb8f16d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2021
ms.locfileid: "129647525"
---
# <a name="quality-fundamentals"></a>Quality Fundamentals

质量基础知识是一个 HoloLens 2 应用程序，它演示了构建强大的混合现实体验的基础知识。  我们现在可以通过选择应用中提供的选项来亲身常见的环境、设计和性能问题，而不是只是了解和阅读有关混合现实的质量问题。

若要下载并安装此应用，请参阅应用下载页面：

> [!div class="nextstepaction"]
> [Quality Fundamentals](https://www.microsoft.com/p/quality-fundamentals/9mwz852q88fw?activetab=pivot:overviewtab)

![质量基础主页](images\qf-homepage.jpg)

在此示例应用程序中，我们将了解：

>[!div class = "checklist"]
> * [设备 i/o 和环境](#device-io-and-environment)：环境因素对性能的影响 HoloLens。
> * [空间锚](#anchor-fundamentals)：如何使用空间锚点将全息影像与物理空间对齐。
> * [全息稳定性和保真度](#stability-and-fidelity)：探索有助于提高全息影像稳定性和保真度的技术。
> * [3d 资产基础知识](#3d-asset-fundamentals)：如何优化3d 资产以保持高视觉保真。 

## <a name="device-io-and-environment"></a>设备 i/o 和环境

HoloLens 上启动质量基础应用。 应用的主页出现后，请选择 " **设备 i/o 和环境**"。  我们将探讨 HoloLens 传感器和周围环境如何影响空间映射、跟踪和放置全息影像。 

### <a name="surfaces"></a>表面

具有镜像完成的镜像或表面会将有关对象形状的 HoloLens 传感器混淆。  在图面上反射的对象可能会被设备解释为变化的环境，这可能会导致设备丢失跟踪。  如果镜像面出现 HoloLens 的问题，请考虑添加屏幕或 closable 百叶窗。

有关详细信息，请参阅[HoloLens 环境注意事项](/hololens/hololens-environment-considerations)中[的空间中的表面](/hololens/hololens-environment-considerations#surfaces-in-a-space)。

### <a name="lighting"></a>照明

HoloLens 性能可能会受到非常低或非常明亮的光源的负面影响。  HoloLens 上的跟踪传感器需要大约 500-1000 lux 的光才能以最佳方式操作。 可以使用 luxmeter 或移动应用来测量空间中的光线量。

有关详细信息，请参阅[HoloLens 环境注意事项](/hololens/hololens-environment-considerations)中的[光照](/hololens/hololens-environment-considerations?branch=pr-en-us-3071#lighting)。

## <a name="anchor-fundamentals"></a>锚基准

若要了解如何使用空间锚点将全息影像与物理空间对齐，请在应用主页上选择 " **定位 Fundametals** "。

在应用的此部分中，我们将探讨以下用户方案：

>[!div class = "checklist"]
> * 当没有任何定位点应用于对象时，会发生什么情况。
> * 在将多个空间锚点用于一组对象时。
> * 使用 QR 代码在多个协作者之间共享空间锚。
> * 空间中超大型对象的定位定位。

有关详细信息，请参阅[混合现实](../../design/spatial-anchors.md)文档中的[空间锚](../../design/spatial-anchors.md)。

## <a name="stability-and-fidelity"></a>稳定性和保真度

在应用程序主页上，选择 " **稳定性和保真** " 以了解如何提高全息影像的稳定性。

我们将探讨以下关键概念：

>[!div class = "checklist"]
> * [帧速率](#frame-rate)。
> * [后期阶段 reprojection (LSR) ](#late-stage-reprojection-lsr)。
> * [Z-反击](#z-fighting)。
> * [消除锯齿](#anti-aliasing)。

### <a name="frame-rate"></a>帧速率

为了尽可能提供最好的全息影像体验，应用程序开发人员必须在每秒 (FPS) 维护60帧。  在应用程序的此部分中，在不同的三角形计数选项之间切换，以体验不同帧速率之间的差异。

![三角形计数优化](images\qf-triangle-count-optimization.png)

有关详细信息，请参阅[全息图稳定性](../platform-capabilities-and-apis/hologram-stability.md)一文中的[帧速率](../platform-capabilities-and-apis/hologram-stability.md#frame-rate)。

### <a name="late-stage-reprojection-lsr"></a>后期阶段 reprojection (LSR) 

当用户在其空间中移动时，Reprojection 用于使全息影像稳定。  尝试使用此部分应用提供的不同 reprojection 选项，以查看全息图质量之间的差异。

![尝试不同的 reprojection 选项，以体验不同之处。](images\qf-lsr-modes.jpg)

有关详细信息，请参阅全息图[稳定性](../platform-capabilities-and-apis/hologram-stability.md)一文中的[reprojection](../platform-capabilities-and-apis/hologram-stability.md#reprojection) 。

### <a name="z-fighting"></a>Z 冲突

当混合现实应用程序无法识别哪个对象位于另一个对象之前，会发生 Z 反击。  您会注意到全息对象的闪烁，因为这些对象需要相同的 z 深度值。  通过更改全息对象的位置，在这种情况下，在自行车上体验 z 反击的效果。

![通过对象放置实现 z 向处理体验。](images\qf-z-fighting.jpg)

有关 z 反击的详细信息，请参阅在[适用于 Unity 的推荐设置](./recommended-settings-for-unity.md)一文中[启用深度缓冲区共享](./recommended-settings-for-unity.md#enable-depth-buffer-sharing)。

### <a name="anti-aliasing"></a>消除锯齿

消除锯齿是一种技术，用于平滑影像中的曲线和对角线的锯齿边缘。  在应用程序的此部分中，体验对显示的文本和自行车辐射的别名影响。  

## <a name="3d-asset-fundamentals"></a>3D 资产基础知识

在应用程序主页上，选择 " **3D 资产基础知识** " 以了解如何优化3d 资产以满足帧速率要求，同时保持高视觉保真。

我们将探讨以下关键概念：

>[!div class = "checklist"]
> * [三角形计数](#triangle-count)。
> * [着色器通过](#shader-passes)。
> * [绘图调用](#draw-calls)。
> * [Finale](#finale)。

### <a name="triangle-count"></a>三角形计数

选择自行车型号的数量和复杂性，以根据 FPS 体验视觉差异。

![选择不同的三角形计数选项可查看帧速率效果。](images\qf-3d-asset-visible-triangles.jpg)

有关详细信息，请参阅 [资产创建过程](../../design/asset-creation-process.md)。

### <a name="shader-passes"></a>着色器通过

选择自行车数和不同的着色器选项，以根据 FPS 体验视觉对象差异。

![选择不同的着色器选项以查看对帧速率的影响。](images\qf-3d-asset-shader-complexity.jpg)

有关详细信息，请参阅 [MRTK 标准着色器](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)。

### <a name="draw-calls"></a>绘图调用

绘图调用是对图形卡的消耗大量资源的调用。  在应用程序的此部分中，体验第一次体验，因为绘图调用数会影响 FPS。

![应优化绘图调用以提高性能。](images\qf-3d-asset-draw-calls.jpg)

请参阅 [CPU 到 GPU 的性能建议](./performance-recommendations-for-unity.md#cpu-to-gpu-performance-recommendations)。

### <a name="finale"></a>Finale

在这里，我们可以探索可以显示多少完全优化的自行车，还可以考虑到优化技术的保真度级别。

![使用的优化方法。](images\qf-3d-asset-finale.jpg)

## <a name="next-steps"></a>后续步骤

探索其他混合现实示例方案：

   > [!div class="nextstepaction"]
   > [示例和功能应用](../features-and-samples.md)