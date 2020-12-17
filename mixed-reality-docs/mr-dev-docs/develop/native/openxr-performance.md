---
title: OpenXR 性能
description: 调试 OpenXR 应用程序的 GPU 性能。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，DirectX，本机，本机应用，自定义引擎，中间件，性能，优化，GPU 调试，RenderDoc，PIX
ms.openlocfilehash: 7199b29067094d402348f00a9d26b93cf7e5393e
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613171"
---
# <a name="openxr-performance"></a><span data-ttu-id="9b717-104">OpenXR 性能</span><span class="sxs-lookup"><span data-stu-id="9b717-104">OpenXR performance</span></span>

<span data-ttu-id="9b717-105">在 HoloLens 2 上，有多种方法可通过提交撰写数据 `xrEndFrame` ，这可能会导致后期处理和性能下降。</span><span class="sxs-lookup"><span data-stu-id="9b717-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame`, which can result in post-processing and noticeable performance penalties.</span></span>
<span data-ttu-id="9b717-106">若要避免性能降低，请[提交 `XrCompositionProjectionLayer` ](openxr-best-practices.md#use-a-single-projection-layer)具有以下特征的单一：</span><span class="sxs-lookup"><span data-stu-id="9b717-106">To avoid poor performance, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>
* [<span data-ttu-id="9b717-107">使用纹理数组存在</span><span class="sxs-lookup"><span data-stu-id="9b717-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="9b717-108">使用主要颜色存在格式</span><span class="sxs-lookup"><span data-stu-id="9b717-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="9b717-109">使用建议的视图维度</span><span class="sxs-lookup"><span data-stu-id="9b717-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="9b717-110">不设置 `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` 标志</span><span class="sxs-lookup"><span data-stu-id="9b717-110">Don't set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="9b717-111">将设置 `XrCompositionLayerDepthInfoKHR` `minDepth` 为 0.0 f，将设置 `maxDepth` 为 1.0 f</span><span class="sxs-lookup"><span data-stu-id="9b717-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="9b717-112">为了获得更好的性能，请考虑：</span><span class="sxs-lookup"><span data-stu-id="9b717-112">For better performance, consider:</span></span>
* [<span data-ttu-id="9b717-113">使用16位深度格式</span><span class="sxs-lookup"><span data-stu-id="9b717-113">Using the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="9b717-114">进行实例绘制调用</span><span class="sxs-lookup"><span data-stu-id="9b717-114">Making instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
