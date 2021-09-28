---
title: 在 Windows Mixed Reality 中使用 WebXR
description: 了解有关使用和开发 Windows Mixed Reality 沉浸式耳机上运行的 WebXR 应用程序的基础知识。
author: yonet
ms.author: v-vtieto
ms.date: 09/24/2021
ms.topic: article
keywords: WebXR，WinMR，WebAR，WebVR，WindowsMixedReality，HoloLens，windows mixed reality，web vr，web xr，web mr，web ar，360，360视频，360视频，360照片，360照片，360内容，沉浸式 web，immersiveweb，IW
ms.openlocfilehash: b0ab1eab5f1c3e546dde367c2cdb992fba7b452d
ms.sourcegitcommit: 3176df29fb0c9508751bd370f1211031d50d2c14
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/28/2021
ms.locfileid: "129148692"
---
# <a name="javascript-development-with-webxr"></a>使用 WebXR 的 JavaScript 开发

JavaScript 是世界上最常用的编程语言之一！ 它在 Web 上简单、轻便、广泛使用。 利用你的 JavaScript 和 Web 技能的强大功能，创建更具吸引力的混合现实体验。

## <a name="mixed-reality-applications-on-the-web"></a>Web 上的混合现实应用程序

混合现实功能通过 [WebXR](webxr-overview.md)在 Web 上提供。 你可以查看虚拟现实 (VR) 并在已启用兼容 WebXR 的浏览器中 (AR) 内容，而无需安装任何其他软件或插件。 可以将该浏览器与 HoloLens 2 等物理设备一起使用。

[**WebXR 设备 API**](https://www.w3.org/TR/webxr/)用于访问虚拟现实 (VR) 并增加了 (AR) 设备（包括传感器和安装在 Web 上的显示）的现实。 WebXR 设备 API Microsoft Edge 和 Chrome 版本79上提供，更高版本支持 WebXR 作为默认值。 可以在 [caniuse.com](https://caniuse.com/#search=webxr)上检查 WebXR 的最新浏览器支持状态。

> [!NOTE]
> **WebVR** 已被弃用，并且在当前浏览器中不可用，因此不应将其用于任何新的开发。 需要将任何现有的 **WebVR** 实现迁移到 **WebXR**。

| WebXR 功能 | 可用性 |
|---------|---------|
|[WebXR 设备 API (w3.org) ](https://www.w3.org/TR/webxr/) | Windows 桌面上的 Edge 81 <br>Hololens 2 上的 Edge 91|
|[WebXR 扩充的现实模块级别 1 (w3.org) ](https://www.w3.org/TR/webxr-ar-module-1/)|边缘91。 仅 Hololens 2|
|[WebXR 手型输入模块 (w3.org) ](https://www.w3.org/TR/webxr-hand-input-1/)|边缘93。 仅 Hololens 2|
|[WebXR 锚定模块 (immersive-web.github.io) ](https://immersive-web.github.io/anchors/)|边缘93。 仅 Hololens 2|
|[WebXR 命中测试模块 (immersive-web.github.io) ](https://immersive-web.github.io/hit-test/)|边缘93。 仅 Hololens 2 |

### <a name="viewing-webxr"></a>查看 WebXR

可以通过[新的 Microsoft Edge](../../whats-new/new-microsoft-edge.md)和[Firefox 现实](https://mixedreality.mozilla.org/firefox-reality/)浏览器 Windows Mixed Reality 来查看 WebXR 体验。
若要测试你的浏览器是否支持 WebXR，你可以在浏览器中导航到 [WebXR 示例](https://immersive-web.github.io/webxr-samples/) 。

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>我可以使用哪些内容来开发沉浸式 Web 体验？

下面的列表显示了用于构建大为市场的沉浸式体验的 JavaScript 框架和 Api，以及混合现实 JavaScript 开发人员广泛接受和采用的 Api：

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon 是一个 JavaScript 3D 引擎，可轻松开发3D 内容和沉浸式应用程序。 在开始利用沉浸式应用程序之前，我们建议你了解 Babylon.js 开发的基础知识。<br/><br/>-了解如何通过 babylon.js 生成3D 应用 [程序：入门](https://doc.babylonjs.com/start)<br/>-使用 babylon.js 的三维示例和源代码： [板块](https://doc.babylonjs.com/examples/)<br/>-深入了解 [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>-了解如何开始学习教程： [创建第一个 "Hello World！" 应用](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![BabylonJS 徽标](images/babylon.js.example.png) |
|[**A 帧**](https://aframe.io/) <br/><br/>框架是一种声明性的 JavaScript 框架，可用于在 Web 上开始虚拟现实。 若要了解详细信息，请查看 [框架文档](https://aframe.io/docs/1.2.0/introduction/) |![A 帧](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js 是一个流行的3D 库，用于创建沉浸式体验。 详细了解 [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) 并 [浏览示例](https://threejs.org/examples/#webgl_animation_cloth)。 |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>可以通过使用 WebGL Api 直接访问 WebXR 设备 Api。 WebGL (Web 图形库) 是一个 JavaScript API，用于在任何兼容的 Web 浏览器中呈现高性能的交互式3D 和2D 图形，而无需使用插件。 |![WebGL](images/webgl.example.png)  |

## <a name="see-also"></a>另请参阅

* [WebXR 设备 API 规范](https://immersive-web.github.io/webxr/)
* [WebXR 设备 API 文档](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [WebXR 示例](https://immersive-web.github.io/webxr-samples/)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [使用 Babylon.js 创建 WebXR 体验](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [游戏板 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 和 [游戏板扩展](https://w3c.github.io/gamepad/extensions.html)
* [Windows Mixed Reality 和新的 Microsoft Edge](../../whats-new/new-microsoft-edge.md)
* [处理 WebGL 中丢失的上下文](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [沉浸式 web 社区组](https://www.w3.org/community/immersive-web/)
* [沉浸式 Web W3C Github](https://github.com/immersive-web)

## <a name="next-steps--tutorials"></a>后续步骤-教程

> [!div class="nextstepaction"]
> [使用 Babylon.js创建第一个 WebXR 应用程序 ](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

> [!div class="nextstepaction"]
> [使用 Babylon.js在 WebXR 中生成钢琴 ](tutorials/babylonjs-webxr-piano/introduction-01.md)
