---
title: 将 WebVR 与 Windows Mixed Reality 一起使用
description: 介绍 WebVR，以及如何在 Windows Mixed Reality 耳机上与 Microsoft Edge 结合使用。
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，WebVR，Edge，Microsoft Edge，web 浏览
ms.openlocfilehash: 92f1d00c7f635c88a727732fb743996a654ba775
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725598"
---
# <a name="using-webvr-with-windows-mixed-reality"></a>将 WebVR 与 Windows Mixed Reality 一起使用

>[!IMPORTANT]
>大多数新式 web 浏览器的 WebVR 支持 WebXR，这是为取代了 VR 耳机创建沉浸式 web 体验的新标准。 请安装 [新的 Microsoft Edge](using-microsoft-edge.md) for WebXR 支持。

## <a name="what-is-webvr"></a>什么是 WebVR

[WebVR](https://webvr.info) 是一个开放规范，可让你在浏览器中获得 VR 权限。 如果某个网站实现 WebVR 支持并提供3D 内容，则它可以在耳机中显示沉浸式内容，同时提供用户同意。

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a>WebVR 与在 VR 中浏览网站之间的区别是什么

WebVR 是一种技术，允许网站作者将 VR 功能添加到页面。 页面使用 WebVR API 来显示三维内容 (例如360度视频或3D 模型，或将三维游戏) 到整个耳机。 **示例：** 在 [cnn.com/vr](http://cnn.com/vr)上查看360视频。 如果页面支持 WebVR，它将添加一个按钮或其他用户界面元素，您可以选择该按钮来进入 VR。

在 VR 中浏览 web 意味着在戴上耳机时使用 Edge 浏览器，这是 Cliffhouse 中的2D 应用程序石板。

## <a name="do-all-websites-support-webvr"></a>所有网站支持 WebVR

不是。 网站作者必须选择使用 WebVR，他们可能会为特定的浏览器、耳机和控制器创建优化的网站。 某些 WebVR 内容仅针对 mobile VR 设备进行了优化。 另外，请记住，网站需要显式创建和提供 WebVR 内容。 具有一些 WebVR 兼容内容的站点数每天都在增长。

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a>我可以使用我的 Naopak/Oculus 等来查看 Microsoft Edge 中的 WebVR 内容

不是。 需要 Windows Mixed Reality 耳机才能使用 WebVR。 但是，你可以在另一个浏览器中访问 WebVR 内容;请参阅位于以下位置的兼容设备和浏览器的完整列表： [WebVR. rocks](http://webvr.rocks/)。

## <a name="where-can-i-find-the-webvr-developer-documentation"></a>在哪里可以找到 WebVR 开发人员文档

开发人员文档位于此处： [WebVR 开发人员文档](https://docs.microsoft.com/microsoft-edge/webvr/)。

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a>我发现了一个具有 WebVR 的网站，该网站在 Windows Mixed Reality 中不起作用。 我该怎么办

你可以在 [问题跟踪](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)程序中直接向 Microsoft Edge 浏览器团队报告断开的网站，也可以通过 twitter 使用 [#EdgeBug 井号标签](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)来向其报告。

你还可以在 "类别" 下使用 Windows 反馈中心应用记录 bug：

Microsoft Edge-> 网站问题

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a>如果 WebVR 工作，则可以测试哪一种不错的页面

请参阅 [webvr.info 示例](http://webvr.info/samples/XX-vr-controllers.html)。

## <a name="how-do-i-set-up-webvr"></a>如何实现设置 WebVR

若要在 Windows Mixed Reality 耳机上体验 WebVR 内容 (使用硬件或模拟) ，你必须：

1. 确保你的耳机已连接。
2. 在桌面上或在混合现实中启动 Microsoft Edge。
3. 导航到启用了 WebVR 的页。
4. 在页面中选择 "输入 VR" 按钮 (该按钮的位置和视觉表示形式可能因网站) 而异。 它看起来可能类似于： \
   ![VR Goggles 映像](images/75px-enter-vr.png)
5. 首次在特定域上尝试输入 VR 时，浏览器将要求同意使用沉浸式视图，并选择 "是"： ![首次尝试在特定域上进入 VR 时显示的同意 UI](images/1053px-Webvr-consent-ui.png)
6. 你的耳机应该开始显示 WebVR 内容。

## <a name="see-also"></a>另请参阅

* [> WebVR 的疑难解答](webvr-questions.md)
* [如何进入你的第一个 WebVR 体验](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [在 Windows Mixed Reality 中使用游戏和应用](using-games-and-apps-in-windows-mixed-reality.md)
* [混合现实主页](your-mixed-reality-home.md)
* [跟踪系统](tracking-system.md)
* [运动控制器](controllers-in-wmr.md)
* [SteamVR](using-steamvr-with-windows-mixed-reality.md)
* [申报反馈](filing-feedback.md)
