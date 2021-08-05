---
title: OpenXR 性能
description: 了解如何调试 OpenXR 混合现实应用程序的 GPU 性能。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、本机、本机应用、自定义引擎、中间件、性能、优化、GPU 调试、RenderDoc、PIX
ms.openlocfilehash: f4462da954a3b6093e47f03e75b460671e7638f406b761ad6e05689ab97b3ddc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213171"
---
# <a name="openxr-performance"></a>OpenXR 性能

在HoloLens 2，可以通过 多种方式提交组合数据，这可能会导致后期处理和 `xrEndFrame` 明显的性能下降。

为了避免性能不佳，[请提交具有以下 `XrCompositionProjectionLayer` ](openxr-best-practices.md#use-a-single-projection-layer)特征的单个 ：

* [使用纹理数组交换链](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [使用主颜色交换链格式](openxr-best-practices.md#select-a-swapchain-format)
* [使用建议的视图维度](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* 不设置 `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` 标志
* 将 设置为 `XrCompositionLayerDepthInfoKHR` `minDepth` 0.0f，将 `maxDepth` 设置为 1.0f

为了提高性能，请考虑：

* [使用 16 位深度格式](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [进行实例绘制调用](openxr-best-practices.md#render-with-texture-array-and-vprt)
