---
title: 将 WebVR 与 Windows Mixed Reality
description: 了解 WebVR 的基础知识、如何在 Microsoft Edge头戴显示Windows Mixed Reality上使用它以及常见的故障排除问题。
ms.topic: article
keywords: Windows Mixed Reality、混合现实、虚拟现实、VR、MR、WebVR、Edge、Microsoft Edge、Web 浏览
ms.openlocfilehash: f61fff3c8d5083236c10d79d3824c489111f8d2be2138984f5613f295849bdf2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214121"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>将 WebVR 与 Windows Mixed Reality

>[!IMPORTANT]
>大多数新式 Web 浏览器已弃用对 WebVR 的支持，以支持 WebXR（为 VR 头戴显示设备创建沉浸式 Web 体验的新标准）。 请安装[新的 Microsoft Edge](using-microsoft-edge.md) WebXR 支持。

## <a name="what-is-webvr"></a>什么是 WebVR

[WebVR](https://webvr.info) 是一种开放规范，使你能够从浏览器体验 VR。 如果网站实现 WebVR 支持并提供 3D 内容，则它可以在用户同意的情况下在头戴显示设备中显示沉浸式内容。

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>WebVR 与在 VR 中浏览 Web 之间有什么区别

WebVR 是一种允许网站作者向页面添加 VR 功能的技术。 WebVR API 由页面用于显示 3D 内容 (例如 360 度视频、3D 模型或 3D 游戏) 整个头戴显示设备。 **示例：** 在 上观看 360 [cnn.com/vr。](http://cnn.com/vr) 如果页面支持 WebVR，它将添加一个按钮或其他 UI 元素，可以选择该元素来输入 VR。

在 VR 中浏览 Web 意味着在戴头戴显示设备时使用 Edge 浏览器，作为一个 2D 应用在一个功能区内使用。

## <a name="do-all-websites-support-webvr"></a>是否所有网站都支持 WebVR

不是。 网站作者必须选择使用 WebVR，他们可能会为特定浏览器、头戴显示设备和控制器创建优化站点。 某些 WebVR 内容仅针对移动 VR 设备进行了优化。 此外，请记住，网站需要显式创建和提供 WebVR 内容。 具有一些 WebVR 兼容内容的站点数每天都在增长。

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>能否使用 Vive/Oculus 等来查看 webVR 内容Microsoft Edge

不是。 需要Windows Mixed Reality头戴显示设备才能在 Edge 中使用 WebVR。 但是，可以在另一个浏览器中访问 WebVR 内容;请参阅兼容设备和浏览器的完整列表，网址为[：WebVR.rocks。](http://webvr.rocks/)

## <a name="where-can-i-find-the-webvr-developer-documentation"></a>在哪里可以找到 WebVR 开发人员文档

开发人员文档位于 [：WebVR 开发人员文档](/microsoft-edge/webvr/)。

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a>我发现了一个 WebVR 网站，该网站在 Windows Mixed Reality。 我该怎么办

可以直接向问题跟踪器中的 Microsoft Edge浏览器团队报告损坏的站点，或者[](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)使用哈希标记 通过 twitter #EdgeBug[报告](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)。

还可使用类别下的应用Windows 反馈中心 bug：

Microsoft Edge -> 网站问题

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a>测试 WebVR 是否正常工作的不错页面

请参阅 [webvr.info 示例](http://webvr.info/samples/XX-vr-controllers.html)。

## <a name="how-do-i-set-up-webvr"></a>如何实现设置 WebVR

若要使用硬件或模拟设备Windows Mixed Reality头戴显示设备 (WebVR) ，必须：

1. 确保头戴显示设备已连接。
2. 在Microsoft Edge桌面或混合现实中启动应用程序。
3. 导航到已启用 WebVR 的页面。
4. 选择页面中的"输入 VR"按钮 (按钮的位置和视觉表示形式可能因网站设置) 。 它看起来可能类似于：\
   ![VR Goggles 图像](images/75px-enter-vr.png)
5. 首次尝试在特定的域上输入 VR 时，浏览器会请求同意使用沉浸式视图，请选择"是"： ![首次尝试输入特定域上的 VR 时显示的同意 UI](images/1053px-Webvr-consent-ui.png)
6. 头戴显示设备应开始显示 WebVR 内容。

## <a name="see-also"></a>另请参阅

* [WebVR >疑难解答](webvr-questions.md)
* [如何进入第一个 WebVR 体验](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [在应用程序中使用游戏Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [混合现实主页](your-mixed-reality-home.md)
* [跟踪系统](tracking-system.md)
* [运动控制器](controllers-in-wmr.md)
* [SteamVR](using-steamvr-with-windows-mixed-reality.md)
* [提交反馈](filing-feedback.md)