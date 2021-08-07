---
title: 将 WebXR 与 Windows Mixed Reality
description: 了解在沉浸式头戴显示设备上运行的 WebXR Windows Mixed Reality的基础知识。
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR、WinMR、WebAR、WebVR、WindowsMixedReality、HoloLens、windows 混合现实、web vr、web xr、web mr、web ar、360、360 视频、360 视频、360 照片、360 照片、360 内容、沉浸式 Web、沉浸式 Web、IW
ms.openlocfilehash: e670135cb00db26082b73f8465390a686de6a3e946bbffa561f9df90085970f8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216263"
---
# <a name="webxr-overview"></a>WebXR 概述

## <a name="javascript-development"></a>JavaScript 开发

JavaScript 是世界上最常用的编程语言之一！ 它简单、轻量且在 Web 上广泛使用。 利用 JavaScript 和 Web 技能，创建更具吸引力的混合现实体验。

## <a name="mixed-reality-applications-on-the-web"></a>Web 上的混合现实应用程序

混合现实功能通过使用 [WebXR](webxr-overview.md)在 Web 上提供。 可以在支持 WebXR 的兼容浏览器中 (VR) 和增强现实 (AR) 内容，而无需安装任何其他软件或插件。 可以将同一浏览器用于物理设备（如 HoloLens 2）。

[**WebXR**](https://www.w3.org/TR/webxr/)设备 API 用于访问虚拟现实 **(VR)** 和增强现实 **(AR)** 设备，包括 Web 上的传感器和头安装 **显示器**。 WebXR 设备 API 目前Microsoft Edge Chrome 版本 79 及更高版本支持 WebXR 作为默认版本。 可以在 上查看 WebXR 的最新浏览器[caniuse.com。](https://caniuse.com/#search=webxr)

> [!NOTE]
> **WebVR** 已弃用，在当前浏览器中不可用，因此不应用于任何新开发。 需要将任何现有的 **WebVR** 实现转发到 **WebXR**。

### <a name="viewing-webxr"></a>查看 WebXR

可以在新应用和[Firefox](https://mixedreality.mozilla.org/firefox-reality/)Reality 上Windows Mixed Reality WebXR [Microsoft Edge](../../whats-new/new-microsoft-edge.md)体验。
若要测试浏览器是否支持 WebXR，可以在浏览器中导航到 [WebXR](https://immersive-web.github.io/webxr-samples/) 示例

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>可以使用什么来开发沉浸式 Web 体验？

以下列表显示了用于构建沉浸式体验的 JavaScript 框架和 API，这些体验当前占据市场，并已被混合现实 JavaScript 开发人员广泛接受和采用：

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon 是一种 JavaScript 3D 引擎，可轻松地开发 3D 内容和沉浸式应用程序。 在开始使用沉浸式应用程序之前，建议先了解Babylon.js基础知识。<br/><br/>- 了解如何使用"入门"babylon.js 3D [应用程序](https://doc.babylonjs.com/start)。<br/>- 使用 babylon.js Playground 播放 3D 示例及其 [源代码](https://doc.babylonjs.com/examples/)<br/>- 深入了解 [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>- 了解如何开始使用我们的教程创建第一个 ["Hello World！"应用](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![BabylonJS 徽标](images/babylon.js.example.png) |
|[**A 帧**](https://aframe.io/) <br/><br/>框架是一种声明性 JavaScript 框架，用于开始使用 Web 中的虚拟现实。 有关详细信息，请查看 [A-Frame](https://aframe.io/docs/1.2.0/introduction/) 文档。 |![A 帧](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js是用于创建沉浸式体验的常用 3D 库。 在文档页 [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) 浏览示例，详细了解 [相关内容](https://threejs.org/examples/#webgl_animation_cloth)。 |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>可以使用 WebGL API 直接访问 WebXR 设备 API。 WebGL (Web 图形库) 是一个 JavaScript API，用于在任何兼容的 Web 浏览器中呈现高性能交互式 3D 和 2D 图形，而无需使用插件。 |![WebGL](images/webgl.example.png)  |

## <a name="see-also"></a>另请参阅

* [WebXR 概述](webxr-overview.md)
* [WebXR 设备 API 规范](https://immersive-web.github.io/webxr/)
* [WebXR 设备 API 文档](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [WebXR 示例](https://immersive-web.github.io/webxr-samples/)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [使用 Babylon.js 创建 WebXR 体验](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [游戏板 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) [和游戏板扩展](https://w3c.github.io/gamepad/extensions.html)
* [Windows Mixed Reality和新的Microsoft Edge](../../whats-new/new-microsoft-edge.md)
* [处理 WebGL 中丢失的上下文](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [沉浸式 Web 社区组](https://www.w3.org/community/immersive-web/)
* [沉浸式 Web W3C Github](https://github.com/immersive-web)