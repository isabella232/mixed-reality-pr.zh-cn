---
title: JavaScript 开发概述
description: 使用适用于 web、移动和 windows 沉浸式耳机的 JavaScript 进行混合现实开发的概述。
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: JavaScript，WebXR，WinMR，WebAR，WebVR，WindowsMixedReality，HoloLens，windows mixed reality，web vr，web xr，web mr，web ar，360，360视频，360视频，360照片，360照片，360内容，沉浸式 web，沉浸式 web，IW，immersiveweb
ms.openlocfilehash: 311241d9dec6f5d086a45766c040b1b2b9eb4128
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394341"
---
# <a name="javascript-development-overview"></a><span data-ttu-id="96817-104">JavaScript 开发概述</span><span class="sxs-lookup"><span data-stu-id="96817-104">JavaScript development overview</span></span>

<span data-ttu-id="96817-105">JavaScript 是世界上最常用的编程语言之一！</span><span class="sxs-lookup"><span data-stu-id="96817-105">JavaScript is one of the most popular programming languages in the world!</span></span> <span data-ttu-id="96817-106">它在 web 上简单、轻便、广泛使用。</span><span class="sxs-lookup"><span data-stu-id="96817-106">It's simple, lightweight, and widely used on the web.</span></span> <span data-ttu-id="96817-107">利用你的 JavaScript 和 web 技能的强大功能，创建更具吸引力的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="96817-107">Leverage the power of your JavaScript and web skills to create more engaging Mixed Reality experiences.</span></span>

## <a name="mixed-reality-applications-on-the-web"></a><span data-ttu-id="96817-108">Web 上的混合现实应用程序</span><span class="sxs-lookup"><span data-stu-id="96817-108">Mixed Reality applications on the web</span></span>

<span data-ttu-id="96817-109">混合现实功能在 web 上可通过使用 [WebXR](webxr-overview.md)来使用。</span><span class="sxs-lookup"><span data-stu-id="96817-109">Mixed Reality features are available on the web by the use of [WebXR](webxr-overview.md).</span></span> <span data-ttu-id="96817-110">你可以查看虚拟现实 (VR) 并在已启用兼容 WebXR 的浏览器中 (AR) 内容，而无需安装任何其他软件或插件。</span><span class="sxs-lookup"><span data-stu-id="96817-110">You can see virtual reality (VR) and augmented reality (AR) content in a compatible WebXR-enabled browser without installing any additional software or plugins.</span></span> <span data-ttu-id="96817-111">可以将该浏览器与与 HoloLens 2 类似的物理设备一起使用。</span><span class="sxs-lookup"><span data-stu-id="96817-111">You can use that same browser with a physical device like the HoloLens 2.</span></span> <span data-ttu-id="96817-112">有关更多详细信息，请查看我们的 [WebXR](webxr-overview.md) 文档。</span><span class="sxs-lookup"><span data-stu-id="96817-112">Check out our [WebXR](webxr-overview.md) documentation for more details.</span></span>

> [!NOTE]
> <span data-ttu-id="96817-113">**WebVR** 已被弃用，并且在当前浏览器中不可用，因此不应将其用于任何新的开发。</span><span class="sxs-lookup"><span data-stu-id="96817-113">**WebVR** is deprecated and is not available in current browsers, hence it should not be used for any new development.</span></span> <span data-ttu-id="96817-114">需要将任何现有的 **WebVR** 实现迁移到 **WebXR**。</span><span class="sxs-lookup"><span data-stu-id="96817-114">You will need to migrate any existing **WebVR** implementations forward to **WebXR**.</span></span>

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a><span data-ttu-id="96817-115">我可以使用哪些内容来开发沉浸式 web 体验？</span><span class="sxs-lookup"><span data-stu-id="96817-115">What can I use to develop immersive web experiences?</span></span>

<span data-ttu-id="96817-116">下面的列表显示了用于构建大为市场的沉浸式体验的 JavaScript 框架和 Api，以及混合现实 JavaScript 开发人员广泛接受和采用的 Api：</span><span class="sxs-lookup"><span data-stu-id="96817-116">The following list shows the JavaScript frameworks and APIs for building immersive experiences that currently dominate the market and are widely accepted and adopted by Mixed Reality JavaScript developers:</span></span>

|  |  |
| --- | --- |
|[<span data-ttu-id="96817-117">**Babylon.js**</span><span class="sxs-lookup"><span data-stu-id="96817-117">**Babylon.js**</span></span>](https://doc.babylonjs.com/)<br/><br/> <span data-ttu-id="96817-118">Babylon 是一个 JavaScript 3D 引擎，可轻松开发3D 内容和沉浸式应用程序。</span><span class="sxs-lookup"><span data-stu-id="96817-118">Babylon is a JavaScript 3D engine that makes developing 3D content and immersive applications easy.</span></span> <span data-ttu-id="96817-119">在开始利用沉浸式应用程序之前，我们建议了解 Babylon.js 开发的基础知识。</span><span class="sxs-lookup"><span data-stu-id="96817-119">Before getting started with immersive applications, we recommend to learn the basics of Babylon.js development.</span></span><br/><br/><span data-ttu-id="96817-120">-了解如何 [通过 babylon.js 入门](https://doc.babylonjs.com/start)来构建3d 应用程序。</span><span class="sxs-lookup"><span data-stu-id="96817-120">- Learn how to build 3D applications with babylon.js [Getting started](https://doc.babylonjs.com/start).</span></span><br/><span data-ttu-id="96817-121">-使用 babylon.js[板块](https://doc.babylonjs.com/examples/)的三维示例和源代码</span><span class="sxs-lookup"><span data-stu-id="96817-121">- Play with 3D examples and their source code using babylon.js [Playground](https://doc.babylonjs.com/examples/)</span></span><br/><span data-ttu-id="96817-122">-深入了解 [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)</span><span class="sxs-lookup"><span data-stu-id="96817-122">- Dive deeper into [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)</span></span><br/><span data-ttu-id="96817-123">-了解如何开始学习教程 [创建第一个 "Hello World！" 应用](tutorials/babylonjs-webxr-helloworld/introduction-01.md)</span><span class="sxs-lookup"><span data-stu-id="96817-123">- Learn how to get started with our tutorials [Create your first "Hello World!" app](tutorials/babylonjs-webxr-helloworld/introduction-01.md)</span></span>|![BabylonJS 徽标](images/babylon.js.example.png) |
|[<span data-ttu-id="96817-125">**A 帧**</span><span class="sxs-lookup"><span data-stu-id="96817-125">**A-Frame**</span></span>](https://aframe.io/) <br/><br/><span data-ttu-id="96817-126">框架是一种声明性的 JavaScript 框架，用于在 web 中开始虚拟现实。</span><span class="sxs-lookup"><span data-stu-id="96817-126">A-frame is a declarative JavaScript framework to get started with Virtual Reality in the web.</span></span> <span data-ttu-id="96817-127">有关详细信息，请参阅 [框架文档](https://aframe.io/docs/1.2.0/introduction/) 。</span><span class="sxs-lookup"><span data-stu-id="96817-127">Check out the [A-Frame documentation](https://aframe.io/docs/1.2.0/introduction/) to learn more.</span></span> |![A 帧](images/a-frame.example.png)  |
|[<span data-ttu-id="96817-129">**Three.js**</span><span class="sxs-lookup"><span data-stu-id="96817-129">**Three.js**</span></span>](https://threejs.org) <br/><br/><span data-ttu-id="96817-130">Three.js 是一个流行的3D 库，用于创建沉浸式体验。</span><span class="sxs-lookup"><span data-stu-id="96817-130">Three.js is a popular 3D library for creating immersive experiences.</span></span> <span data-ttu-id="96817-131">通过浏览[示例](https://threejs.org/examples/#webgl_animation_cloth)，了解有关[three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene)在文档页中的详细信息。</span><span class="sxs-lookup"><span data-stu-id="96817-131">Learn more about [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) in documentation page and by exploring [examples](https://threejs.org/examples/#webgl_animation_cloth).</span></span> |![Three.js](images/three.js.example.png)  |
|[<span data-ttu-id="96817-133">**WebGL**</span><span class="sxs-lookup"><span data-stu-id="96817-133">**WebGL**</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/><span data-ttu-id="96817-134">可以通过使用 WebGL Api 直接访问 WebXR 设备 Api。</span><span class="sxs-lookup"><span data-stu-id="96817-134">You can access the WebXR Device APIs directly by using WebGL APIs.</span></span> <span data-ttu-id="96817-135">WebGL (Web 图形库) 是一个 JavaScript API，用于在任何兼容的 Web 浏览器中呈现高性能的交互式3D 和2D 图形，而无需使用插件。</span><span class="sxs-lookup"><span data-stu-id="96817-135">WebGL (Web Graphics Library) is a JavaScript API for rendering high-performance interactive 3D and 2D graphics within any compatible web browser without the use of plug-ins.</span></span> |![WebGL](images/webgl.example.png)  |

## <a name="next-steps"></a><span data-ttu-id="96817-137">后续步骤</span><span class="sxs-lookup"><span data-stu-id="96817-137">Next steps</span></span>

<span data-ttu-id="96817-138">了解如何开始学习教程。</span><span class="sxs-lookup"><span data-stu-id="96817-138">Learn how to get started with our tutorials.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="96817-139">创建第一个 "Hello World！" 应用</span><span class="sxs-lookup"><span data-stu-id="96817-139">Create your first "Hello World!" app</span></span>](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

## <a name="see-also"></a><span data-ttu-id="96817-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96817-140">See Also</span></span>

* [<span data-ttu-id="96817-141">WebXR 概述</span><span class="sxs-lookup"><span data-stu-id="96817-141">WebXR Overview</span></span>](webxr-overview.md)
* [<span data-ttu-id="96817-142">WebXR 设备 API 规范</span><span class="sxs-lookup"><span data-stu-id="96817-142">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="96817-143">WebXR 设备 API 文档</span><span class="sxs-lookup"><span data-stu-id="96817-143">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="96817-144">Immersiveweb.dev</span><span class="sxs-lookup"><span data-stu-id="96817-144">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="96817-145">WebXR 示例</span><span class="sxs-lookup"><span data-stu-id="96817-145">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="96817-146">使用 Babylon.js 创建 WebXR 体验</span><span class="sxs-lookup"><span data-stu-id="96817-146">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="96817-147">Windows Mixed Reality 和新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="96817-147">Windows Mixed Reality and the new Microsoft Edge</span></span>](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="96817-148">沉浸式 Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="96817-148">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="96817-149">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="96817-149">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="96817-150">[游戏板 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 和 [游戏板扩展](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="96817-150">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
