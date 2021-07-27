---
title: 质量基础
description: 了解设计混合现实应用程序的质量基础。
author: qianw211
ms.author: v-qianwen
ms.date: 07/15/2021
ms.topic: article
keywords: 质量基础， 案例研究， 项目， 示例， MRTK， 混合现实 Toolkit， Unity， 示例应用， 示例应用， 开源， Microsoft Store， HoloLens， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
ms.openlocfilehash: e91ea1c69aeafaafa9c9bae30af6e5a288754764
ms.sourcegitcommit: cf8df1720ddb8236207ab581bc149edcc76e6199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2021
ms.locfileid: "114702894"
---
# <a name="quality-fundamentals"></a>质量基础

质量基础是一HoloLens 2应用，它演示了构建出色的混合现实体验的基础。  我们现在可以通过选择应用中提供的选项来第一手体验常见的环境、设计和性能问题以及解决方案，而不只是学习和阅读混合现实中的质量问题。

若要下载并安装应用，请转到应用下载页：

> [!div class="nextstepaction"]
> [质量基础](https://www.microsoft.com/p/quality-fundamentals/9mwz852q88fw?activetab=pivot:overviewtab)

![质量基础主页](images\qf-homepage.jpg)

在此示例应用中，我们将了解：

>[!div class = "checklist"]
> * [设备 I/O 和环境](#device-io-and-environment)：这些因素如何影响HoloLens性能。
> * [空间定位点](#anchor-fundamentals)：如何使用空间定位点将全息影像与物理空间对齐。
> * [全息稳定性和保真度](#stability-and-fidelity)：探索有助于提高图像稳定性和保真度全息影像。
> * [3D 资产基础](#3d-asset-fundamentals)：如何优化 3D 资产以保持高视觉保真度。 

## <a name="device-io-and-environment"></a>设备 I/O 和环境

在 HoloLens 上启动质量基础HoloLens。 应用主页出现后，选择"设备 **I/O 和环境"。**  我们将探讨图像传感器HoloLens环境如何影响空间映射、跟踪和全息影像的放置。 

### <a name="surfaces"></a>表面

具有镜像完成效果的镜像或表面可能会HoloLens对象形状的传感器混淆。  设备上反射的对象可能会被设备解释为不断变化的环境，这可能会导致设备失去跟踪。  如果镜像表面导致屏幕HoloLens，请考虑添加屏幕或可阻塞的百叶窗。

有关详细信息，请参阅[环境注意事项](/hololens/hololens-environment-considerations#surfaces-in-a-space)中的HoloLens[图面](/hololens/hololens-environment-considerations)。

### <a name="lighting"></a>照明

HoloLens性能可能会受到极低或极亮光条件负面影响。  目标上的跟踪传感器HoloLens 500-1000 照度，以最佳方式运行。 可以使用照度计或移动应用来测量空间中光量。

有关详细信息，请参阅[环境HoloLens](/hololens/hololens-environment-considerations?branch=pr-en-us-3071#lighting)[中的照明](/hololens/hololens-environment-considerations)。

## <a name="anchor-fundamentals"></a>定位点基础

若要了解如何使用空间定位点将全息影像与物理空间对齐，请在应用主页上选择"定位点基础"。

在应用的此部分，我们将探讨以下用户方案：

>[!div class = "checklist"]
> * 如果没有将定位点应用于对象，会发生什么情况。
> * 当对一组 对象使用多个空间定位点时。
> * 使用 QR 码在多个协作者之间共享空间定位点。
> * 空间中非常大的对象的定位点位置。

有关详细信息，请参阅混合[现实文档中](/windows/mixed-reality/design/spatial-anchors)[的空间定位](/windows/mixed-reality/design/spatial-anchors)点。

## <a name="stability-and-fidelity"></a>稳定性和保真度

在应用程序的主页上，选择" **稳定性和保** 真度"，了解如何提高全息影像稳定性。

我们将探讨以下关键概念：

>[!div class = "checklist"]
> * [帧速率](#frame-rate)。
> * [后期阶段重新 (LSR) 。 ](#late-stage-reprojection-lsr)
> * [Z 冲突](#z-fighting)。
> * [抗锯齿](#anti-aliasing)。

### <a name="frame-rate"></a>帧速率

为了尽可能提供最佳全息影像体验，应用程序开发人员必须在 FPS 应用程序中保持每秒 60 (帧) 。  在应用的此部分，在不同的三角形计数选项之间进行切换，以体验不同帧速率的差异。

![三角形计数优化](images\qf-triangle-count-optimization.png)

有关详细信息，请参阅 [全息影像](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability#frame-rate) 稳定性 [一文的帧速率](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability) 。

### <a name="late-stage-reprojection-lsr"></a>LSR (后期阶段) 

重新保护用于在用户四处移动时稳定全息影像。  尝试应用此部分提供的不同重现选项，了解全息影像质量的差异。

![尝试不同的重现选项来体验差异。](images\qf-lsr-modes.jpg)

有关详细信息，请参阅 [全息影像](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability#reprojection) 稳定性一文 [的重新保护](/windows/mixed-reality/develop/platform-capabilities-and-apis/hologram-stability) 。

### <a name="z-fighting"></a>Z 冲突

当混合现实应用程序无法识别哪个对象位于另一个对象前面时，将发生 Z 冲突。  当全息对象为相同的 z 深度值而闪烁时，你会注意到它们闪烁。  通过更改全息对象（本例中自行车上的徽标）的位置，体验应用中 z 冲突的影响。

![体验对象放置的 z 冲突。](images\qf-z-fighting.jpg)

有关 z 冲突的详细信息，请参阅在 Unity 的建议 [设置](/windows/mixed-reality/develop/unity/recommended-settings-for-unity#enable-depth-buffer-sharing) 中启用深度 [缓冲区](/windows/mixed-reality/develop/unity/recommended-settings-for-unity) 共享一文。

### <a name="anti-aliasing"></a>抗锯齿

抗锯齿是一种技术，用于平滑曲线上的锯齿边缘和全息影像中的对角线。  在应用的此部分，体验对显示的文本和自行车分支使用别名的影响。  

## <a name="3d-asset-fundamentals"></a>3D 资产基础

在应用程序的主页上，选择 **"3D 资产** 基础"，了解如何优化 3D 资产以满足帧速率要求，同时保持高视觉保真度。

我们将探讨以下关键概念：

>[!div class = "checklist"]
> * [三角形计数](#triangle-count)。
> * [着色器传递](#shader-passes)。
> * [绘制调用](#draw-calls)。
> * [Finale](#finale)。

### <a name="triangle-count"></a>三角形计数

选择自行车型号的数量和复杂性，以基于 FPS 体验视觉差异。

![选择不同的三角形计数选项以查看对帧速率的影响。](images\qf-3d-asset-visible-triangles.jpg)

有关详细信息，请参阅 [资产创建过程](/windows/mixed-reality/design/asset-creation-process)。

### <a name="shader-passes"></a>着色器传递

选择自行车数量和不同的着色器选项，以基于 FPS 体验视觉差异。

![选择不同的着色器选项以查看对帧速率的影响。](images\qf-3d-asset-shader-complexity.jpg)

有关详细信息，请参阅 [MRTK 标准着色器](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)。

### <a name="draw-calls"></a>绘制调用

绘图调用是图形卡的资源密集型调用。  在应用的此部分，请首先体验视觉差异，因为绘图调用数会影响 FPS。

![应优化绘图调用以提高性能。](images\qf-3d-asset-draw-calls.jpg)

请参阅 [CPU 到 GPU 性能建议](/windows/mixed-reality/develop/unity/performance-recommendations-for-unity#cpu-to-gpu-performance-recommendations)。

### <a name="finale"></a>结局

在这里，我们可以了解可以显示多少台完全优化的自行车，以及给定优化技术时可能的保真度。

![使用的优化技术。](images\qf-3d-asset-finale.jpg)

## <a name="next-steps"></a>后续步骤

探索其他混合现实示例方案：

   > [!div class="nextstepaction"]
   > [示例和功能应用](../features-and-samples.md)