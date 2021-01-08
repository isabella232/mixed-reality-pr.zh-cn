---
title: OpenXR 性能
description: 了解如何调试 OpenXR mixed reality 应用程序的 GPU 性能。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，DirectX，本机，本机应用，自定义引擎，中间件，性能，优化，GPU 调试，RenderDoc，PIX
ms.openlocfilehash: 158bd2eef8f38f16a1fb5299d64335aca33a3b7f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006757"
---
# <a name="openxr-performance"></a>OpenXR 性能

在 HoloLens 2 上，有多种方法可通过提交撰写数据 `xrEndFrame` ，这可能会导致后期处理和性能下降。

若要避免性能降低，请[提交 `XrCompositionProjectionLayer` ](openxr-best-practices.md#use-a-single-projection-layer)具有以下特征的单一：

* [使用纹理数组存在](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [使用主要颜色存在格式](openxr-best-practices.md#select-a-swapchain-format)
* [使用建议的视图维度](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* 不设置 `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` 标志
* 将设置 `XrCompositionLayerDepthInfoKHR` `minDepth` 为 0.0 f，将设置 `maxDepth` 为 1.0 f

为了获得更好的性能，请考虑：

* [使用16位深度格式](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [进行实例绘制调用](openxr-best-practices.md#render-with-texture-array-and-vprt)
