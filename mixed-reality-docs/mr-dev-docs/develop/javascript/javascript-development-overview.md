---
title: JavaScript 开发概述
description: 使用适用于 web、移动和 windows 沉浸式耳机的 JavaScript 进行混合现实开发的概述。
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: JavaScript，WebXR，WinMR，WebAR，WebVR，WindowsMixedReality，HoloLens，windows mixed reality，web vr，web xr，web mr，web ar，360，360视频，360视频，360照片，360照片，360内容，沉浸式 web，沉浸式 web，IW，immersiveweb
ms.openlocfilehash: de6314b5651740eca23a9078d4b05e1d92344d1742ea433d7b924cbde4457b8c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210491"
---
# <a name="javascript-development-overview"></a>JavaScript 开发概述

JavaScript 是世界上最常用的编程语言之一！ 它在 web 上简单、轻便、广泛使用。 利用你的 JavaScript 和 web 技能的强大功能，创建更具吸引力的混合现实体验。

## <a name="mixed-reality-applications-on-the-web"></a>Web 上的混合现实应用程序

混合现实功能在 web 上可通过使用 [WebXR](webxr-overview.md)来使用。 你可以查看虚拟现实 (VR) 并在已启用兼容 WebXR 的浏览器中 (AR) 内容，而无需安装任何其他软件或插件。 可以将该浏览器与 HoloLens 2 等物理设备一起使用。 有关更多详细信息，请查看我们的 [WebXR](webxr-overview.md) 文档。

> [!NOTE]
> **WebVR** 已被弃用，并且在当前浏览器中不可用，因此不应将其用于任何新的开发。 需要将任何现有的 **WebVR** 实现迁移到 **WebXR**。

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>我可以使用哪些内容来开发沉浸式 web 体验？

下面的列表显示了用于构建大为市场的沉浸式体验的 JavaScript 框架和 Api，以及混合现实 JavaScript 开发人员广泛接受和采用的 Api：

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon 是一个 JavaScript 3D 引擎，可轻松开发3D 内容和沉浸式应用程序。 在开始利用沉浸式应用程序之前，我们建议了解 Babylon.js 开发的基础知识。<br/><br/>-了解如何 [通过 babylon.js 入门](https://doc.babylonjs.com/start)来构建3d 应用程序。<br/>-使用 babylon.js[板块](https://doc.babylonjs.com/examples/)的三维示例和源代码<br/>-深入了解 [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>-了解如何开始学习教程 [创建第一个 "Hello World！" 应用](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![BabylonJS 徽标](images/babylon.js.example.png) |
|[**A 帧**](https://aframe.io/) <br/><br/>框架是一种声明性的 JavaScript 框架，用于在 web 中开始虚拟现实。 有关详细信息，请参阅 [框架文档](https://aframe.io/docs/1.2.0/introduction/) 。 |![A 帧](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js 是一个流行的3D 库，用于创建沉浸式体验。 通过浏览[示例](https://threejs.org/examples/#webgl_animation_cloth)，了解有关[three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene)在文档页中的详细信息。 |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>可以通过使用 WebGL Api 直接访问 WebXR 设备 Api。 WebGL (Web 图形库) 是一个 JavaScript API，用于在任何兼容的 Web 浏览器中呈现高性能的交互式3D 和2D 图形，而无需使用插件。 |![WebGL](images/webgl.example.png)  |

## <a name="next-steps"></a>后续步骤

了解如何开始学习教程。

> [!div class="nextstepaction"]
> [创建第一个 "Hello World！" 应用](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

## <a name="see-also"></a>另请参阅

* [WebXR 概述](webxr-overview.md)
* [WebXR 设备 API 规范](https://immersive-web.github.io/webxr/)
* [WebXR 设备 API 文档](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [WebXR 示例](https://immersive-web.github.io/webxr-samples/)
* [使用 Babylon.js 创建 WebXR 体验](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality 和新的 Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [沉浸式 Web W3C Github](https://github.com/immersive-web)
* [WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [游戏板 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 和 [游戏板扩展](https://w3c.github.io/gamepad/extensions.html)
