---
title: WebVR 常见问题
description: Web 混合现实故障排除，超过了标准使用者支持文档。
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，故障排除，错误，帮助，支持，WebVR
ms.openlocfilehash: e03051008921f87e18cae3a9f6db369e54c56b94
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131931"
---
# <a name="webvr-faqs"></a>WebVR 常见问题

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>为什么在从边缘查看 VR 内容时看不到控制器

并非所有 WebVR 内容都是为支持运动控制器而编写的。 WebVR 允许内容开发人员支持不同类型的输入，例如游戏控制器或运动控制器。 如果你在站点上看不到控制器，则它可能不支持运动控制器。

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>为什么无法在沉浸式 WebVR 视图中使用鼠标

这是 WebVR 规范的一项可选功能。 并非所有浏览器都支持此功能，并且并不是所有的 WebVR 内容都是为了支持鼠标输入而编写的。 WebVR 允许内容开发人员支持不同类型的输入，例如鼠标、键盘、游戏控制器或运动控制器。 鼠标输入行为因浏览器而异。 在 Microsoft Edge 中，网站作者必须确保在向耳机提供时使用 "pointerlock" 才能正常工作。

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a>为什么无法查看来自 Youtube/Facebook/Vimeo/监护人的360学位视频，等等

WebVR 规范允许网站直接从浏览器启动 VR 体验，这些网站的作者目前尚未实现此规范。 在某些平台上，可以使用可下载的应用来查看这些供应商的 VR 内容。

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>为什么无法通过 Firefox 或 Chrome 进入 VR

目前，Windows Mixed Reality 设备目前仅支持 WebVR。

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>当我从网站输入 "VR" 时，为什么我在我的耳机中看到了空白屏幕

网站可能未实现对多 GPU 计算机的支持 (包括混合 GPU 便携式计算机) 。 尝试执行以下操作：

* 重载页面。
* 在台式计算机上，将耳机插入与显示 Microsoft Edge 的监视器相同的图形适配器中。 将两者插到更高的显卡，而不是集成图形适配器中。

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>从边缘观看视频时退出 VR 时，声音将继续播放，但边缘窗口灰显

这是在混合现实 Cliff 房子中从边缘运行 WebVR 时的已知问题。 若要解决此问题，请按键盘上的 esc 键，而不是按 windows 按钮退出 WebVR 体验，或通过选择并停止视频来激活灰显边缘窗口。

## <a name="can-i-use-webvr-on-the-hololens"></a>能否在 HoloLens 上使用 WebVR

Microsoft 目前还没有在 HoloLens 上公布有关 WebVR 的任何信息。

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>从边缘查看 WebVR 内容时，为什么我的视图处于地面级别

网站未正确支持 Windows Mixed Reality 耳机。 要解决此问题：

1. 将耳机置于空间的基底。
2. 使用 Microsoft Edge 在桌面上导航到 WebVR 页面， (不在混合现实) 内。
3. 选择 "Enter VR"。
4. 等待5到10秒，以完全进入沉浸式模式。
5. 戴上耳机。

## <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a>在某些 WebVR 体验中，显示器的分辨率非常低

这些网站不能正确支持高分辨率耳机。 解决方法：

* 如果从 (桌面启动 WebVR，而不是混合现实 Cliff 房子) ，请在选择 "输入 VR" 之前确保窗口最大化。
* 输入 VR 后，请避免调整 Microsoft Edge 窗口的大小。

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>为什么当我更改浏览器选项卡时 WebVR 沉浸式视图退出

这是预期行为。 出于安全原因，只有活动的浏览器选项卡可以访问连接的耳机。

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>为什么无法在特定的 WebVR 体验中听到音频

网站可能使用的是 Microsoft Edge 当前不支持的 OGG 音频文件格式。

你可以在 [问题跟踪](https://developer.microsoft.com/microsoft-edge/platform/issues/)程序中直接向 Microsoft Edge 浏览器团队报告断开的网站，也可以通过 twitter 使用 [#EdgeBug 井号标签](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)来向其报告。

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>为什么 haptic 反馈在 WebVR 中不能与运动控制器一起使用

Microsoft Edge 目前不支持 WebVR 游戏板 API 扩展上的 haptics。