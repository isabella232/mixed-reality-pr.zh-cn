---
title: 将 WebXR 与 Windows Mixed Reality 一起使用
description: 了解有关使用和开发 Windows Mixed Reality 沉浸式耳机上运行的 WebXR 应用程序的基础知识。
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR，WinMR，WebAR，WebVR，WindowsMixedReality，HoloLens，windows mixed reality，web vr，web xr，web mr，web ar，360，360视频，360视频，360照片，360照片，360内容，沉浸式 web，immersiveweb，IW
ms.openlocfilehash: 0954d6554acea8474548a3703de35971a76f7770
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088476"
---
# <a name="webxr-overview"></a><span data-ttu-id="d266b-104">WebXR 概述</span><span class="sxs-lookup"><span data-stu-id="d266b-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="d266b-105">什么是 WebXR</span><span class="sxs-lookup"><span data-stu-id="d266b-105">What is WebXR</span></span>

<span data-ttu-id="d266b-106">[**WebXR 设备 API**](https://www.w3.org/TR/webxr/)用于访问 **虚拟现实 (VR)** 并增加了 **(AR) 设备的现实 AR** ，包括 **传感器** 和在 **Web** 上 **装入的打印头**。</span><span class="sxs-lookup"><span data-stu-id="d266b-106">The [**WebXR Device API**](https://www.w3.org/TR/webxr/) is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="d266b-107">WebXR 设备 API 目前在 Microsoft Edge 中提供，Chrome 版本79及更高版本支持 WebXR 作为默认值。</span><span class="sxs-lookup"><span data-stu-id="d266b-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="d266b-108">可以在 [caniuse.com](https://caniuse.com/#search=webxr)上检查 WebXR 的最新浏览器支持状态。</span><span class="sxs-lookup"><span data-stu-id="d266b-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="d266b-109">查看 WebXR</span><span class="sxs-lookup"><span data-stu-id="d266b-109">Viewing WebXR</span></span>

<span data-ttu-id="d266b-110">可以在 [Windows Mixed reality 和新的 Microsoft Edge](/windows/mixed-reality/whats-new/new-microsoft-edge) 和 [Firefox 现实](https://mixedreality.mozilla.org/firefox-reality/)中查看 WebXR experinces。</span><span class="sxs-lookup"><span data-stu-id="d266b-110">You can view WebXR experinces on [Windows Mixed Reality and the new Microsoft Edge](/windows/mixed-reality/whats-new/new-microsoft-edge) and [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>
<span data-ttu-id="d266b-111">若要测试你的浏览器是否支持 WebXR，你可以在浏览器中导航到 [WebXR 示例](https://immersive-web.github.io/webxr-samples/) 。</span><span class="sxs-lookup"><span data-stu-id="d266b-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="d266b-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d266b-112">See Also</span></span>

* [<span data-ttu-id="d266b-113">使用 Babylon.js 创建 WebXR 体验</span><span class="sxs-lookup"><span data-stu-id="d266b-113">Using Babylon.js to create WebXR experiences</span></span>](/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-helloworld/introduction-01)
* [<span data-ttu-id="d266b-114">WebXR 设备 API 规范</span><span class="sxs-lookup"><span data-stu-id="d266b-114">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="d266b-115">WebXR 设备 API 文档</span><span class="sxs-lookup"><span data-stu-id="d266b-115">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="d266b-116">Immersiveweb.dev</span><span class="sxs-lookup"><span data-stu-id="d266b-116">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="d266b-117">WebXR 示例</span><span class="sxs-lookup"><span data-stu-id="d266b-117">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="d266b-118">Windows Mixed Reality 和新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="d266b-118">Windows Mixed Reality and the new Microsoft Edge</span></span>](/windows/mixed-reality/whats-new/new-microsoft-edge)
* [<span data-ttu-id="d266b-119">沉浸式 Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="d266b-119">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="d266b-120">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="d266b-120">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="d266b-121">[游戏板 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 和 [游戏板扩展](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="d266b-121">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="d266b-122">处理 WebGL 中丢失的上下文</span><span class="sxs-lookup"><span data-stu-id="d266b-122">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="d266b-123">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="d266b-123">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="d266b-124">glTF</span><span class="sxs-lookup"><span data-stu-id="d266b-124">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="d266b-125">沉浸式 web 社区组</span><span class="sxs-lookup"><span data-stu-id="d266b-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
