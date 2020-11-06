---
title: 将 WebXR 与 Windows Mixed Reality 一起使用
description: 使用和开发 Windows Mixed Reality 中的 WebXR 概述
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR，WinMR，WebAR，WebVR，WindowsMixedReality，HoloLens，windows mixed reality，web vr，web xr，web mr，web ar，360，360视频，360视频，360照片，360照片，360内容，沉浸式 web，immersiveweb，IW
ms.openlocfilehash: b72d4968e59e3e631138b1ecfd17ca9bbdd95c84
ms.sourcegitcommit: 8fd127aff85b77778bd7a75c5ec5215d27ecf21a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2020
ms.locfileid: "93416868"
---
# <a name="webxr-overview"></a><span data-ttu-id="6b988-104">WebXR 概述</span><span class="sxs-lookup"><span data-stu-id="6b988-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="6b988-105">什么是 WebXR</span><span class="sxs-lookup"><span data-stu-id="6b988-105">What is WebXR</span></span>

<span data-ttu-id="6b988-106">**WebXR 设备 API** 用于访问 **虚拟现实 (VR)** 并增加了 **(AR) 设备的现实 AR** ，包括 **传感器** 和在 **Web** 上 **装入的打印头** 。</span><span class="sxs-lookup"><span data-stu-id="6b988-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="6b988-107">WebXR 设备 API 目前在 Microsoft Edge 中提供，Chrome 版本79及更高版本支持 WebXR 作为默认值。</span><span class="sxs-lookup"><span data-stu-id="6b988-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="6b988-108">可以在 [caniuse.com](https://caniuse.com/#search=webxr)上检查 WebXR 的最新浏览器支持状态。</span><span class="sxs-lookup"><span data-stu-id="6b988-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="6b988-109">详细了解 [Windows Mixed Reality 和新的 Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)新增 [功能](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) 部分。</span><span class="sxs-lookup"><span data-stu-id="6b988-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="6b988-110">查看 WebXR</span><span class="sxs-lookup"><span data-stu-id="6b988-110">Viewing WebXR</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b988-111">Microsoft Edge (传统) 仅支持在当前浏览器中不可用的已弃用的 API。</span><span class="sxs-lookup"><span data-stu-id="6b988-111">Microsoft Edge (Legacy) only supports WebVR, a deprecated API that is not available in current browsers.</span></span> <span data-ttu-id="6b988-112">但是，基于 Chromium 的新的 **[边缘浏览器](../../whats-new/new-microsoft-edge.md)** 支持 WebXR，适用于 Windows Mixed Reality 中的 VR 原型。</span><span class="sxs-lookup"><span data-stu-id="6b988-112">However, the new **[Chromium-based Edge browser](../../whats-new/new-microsoft-edge.md)** supports WebXR and is available for VR prototyping in Windows Mixed Reality.</span></span> <span data-ttu-id="6b988-113">WebVR 将无法在新的基于 Chromium 的边缘浏览器中使用。</span><span class="sxs-lookup"><span data-stu-id="6b988-113">WebVR will not be available in the new Chromium-based Edge browser.</span></span>
> 
> <span data-ttu-id="6b988-114">如果你正在寻找一种方法，以便在今天的 HoloLens 2 上构建 WebXR 原型，请查看 [Firefox 现实](https://mixedreality.mozilla.org/firefox-reality/)。</span><span class="sxs-lookup"><span data-stu-id="6b988-114">If you're looking for a way to prototype WebXR on HoloLens 2 today, check out [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>

<span data-ttu-id="6b988-115">若要测试你的浏览器是否支持 WebXR，你可以在浏览器中导航到 [WebXR 示例](https://immersive-web.github.io/webxr-samples/) 。</span><span class="sxs-lookup"><span data-stu-id="6b988-115">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b988-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b988-116">See Also</span></span>

* [<span data-ttu-id="6b988-117">WebXR 设备 API 规范</span><span class="sxs-lookup"><span data-stu-id="6b988-117">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="6b988-118">WebXR 设备 API 文档</span><span class="sxs-lookup"><span data-stu-id="6b988-118">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="6b988-119">Immersiveweb</span><span class="sxs-lookup"><span data-stu-id="6b988-119">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="6b988-120">WebXR 示例</span><span class="sxs-lookup"><span data-stu-id="6b988-120">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="6b988-121">Windows Mixed Reality 和新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="6b988-121">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="6b988-122">沉浸式 Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="6b988-122">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="6b988-123">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="6b988-123">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="6b988-124">[游戏板 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 和 [游戏板扩展](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="6b988-124">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="6b988-125">处理 WebGL 中丢失的上下文</span><span class="sxs-lookup"><span data-stu-id="6b988-125">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="6b988-126">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="6b988-126">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="6b988-127">glTF</span><span class="sxs-lookup"><span data-stu-id="6b988-127">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="6b988-128">使用 Babylon.js 创建 WebXR 体验</span><span class="sxs-lookup"><span data-stu-id="6b988-128">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="6b988-129">沉浸式 web 社区组</span><span class="sxs-lookup"><span data-stu-id="6b988-129">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
