---
title: 将 WebXR 与 Windows Mixed Reality 一起使用
description: 了解有关使用和开发 Windows Mixed Reality 沉浸式耳机上运行的 WebXR 应用程序的基础知识。
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR，WinMR，WebAR，WebVR，WindowsMixedReality，HoloLens，windows mixed reality，web vr，web xr，web mr，web ar，360，360视频，360视频，360照片，360照片，360内容，沉浸式 web，immersiveweb，IW
ms.openlocfilehash: 99cf5cf151c41252e43c6051c0d6281d33fe695a
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2021
ms.locfileid: "104909013"
---
# <a name="webxr-overview"></a>WebXR 概述

## <a name="what-is-webxr"></a>什么是 WebXR

**WebXR 设备 API** 用于访问 **虚拟现实 (VR)** 并增加了 **(AR) 设备的现实 AR** ，包括 **传感器** 和在 **Web** 上 **装入的打印头**。 WebXR 设备 API 目前在 Microsoft Edge 中提供，Chrome 版本79及更高版本支持 WebXR 作为默认值。 可以在 [caniuse.com](https://caniuse.com/#search=webxr)上检查 WebXR 的最新浏览器支持状态。

详细了解 [Windows Mixed Reality 和新的 Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)新增 [功能](/windows/mixed-reality/mrtk-porting-guide) 部分。

## <a name="viewing-webxr"></a>查看 WebXR

> [!IMPORTANT]
> Microsoft Edge (传统) 仅支持在当前浏览器中不可用的已弃用的 API。 但是，基于 Chromium 的新的 **[边缘浏览器](../../whats-new/new-microsoft-edge.md)** 支持 WebXR，适用于 Windows Mixed Reality 中的 VR 原型。 WebVR 将无法在新的基于 Chromium 的边缘浏览器中使用。
> 
> 如果你正在寻找一种方法，以便在今天的 HoloLens 2 上构建 WebXR 原型，请查看 [Firefox 现实](https://mixedreality.mozilla.org/firefox-reality/)。

若要测试你的浏览器是否支持 WebXR，你可以在浏览器中导航到 [WebXR 示例](https://immersive-web.github.io/webxr-samples/) 。

## <a name="see-also"></a>另请参阅

* [WebXR 设备 API 规范](https://immersive-web.github.io/webxr/)
* [WebXR 设备 API 文档](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [WebXR 示例](https://immersive-web.github.io/webxr-samples/)
* [Windows Mixed Reality 和新的 Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [沉浸式 Web W3C Github](https://github.com/immersive-web)
* [WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [游戏板 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 和 [游戏板扩展](https://w3c.github.io/gamepad/extensions.html)
* [处理 WebGL 中丢失的上下文](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [使用 Babylon.js 创建 WebXR 体验](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [沉浸式 web 社区组](https://www.w3.org/community/immersive-web/)