---
title: 示例和功能应用
description: 跟进了解所有可用于 HoloLens 的 Microsoft 示例和混合现实功能应用。
author: hferrone
ms.author: jemccull
ms.date: 12/3/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 了解, 示例, MRTK, 研究模式, HoloLens 2, qr 码, WebRTC, 混合现实捕获, 全息远程处理, UX Tools
ms.localizationpriority: high
ms.openlocfilehash: 78cfc726bdffdb461a83bd1e9805d8f0e64b0f01
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583198"
---
# <a name="samples-and-feature-apps"></a>示例和功能应用

![图片显示了一名佩戴 HoloLens 并手动操控全息影像的用户](unreal/images/unreal-developer.jpg)

每次开发历程都会先回顾其他开发人员成功构建的内容，混合现实也不例外。 目前，我们所有的教程和示例应用均基于 Unity 或 Unreal。 在我们为其他引擎和平台制作内容时，“目录”中的相关标题下会列出这些内容。

## <a name="sample-apps"></a>示例应用

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a>功能示例

下面列出的功能示例与我们的文档中介绍的特定实现相对应，并涵盖了一系列开发平台和硬件设备。

### <a name="research-mode"></a>研究模式

第一代 HoloLens 引入了研究模式，用于访问设备上的主要传感器，尤其适用于不打算部署的研究应用程序。 以下应用程序示例是访问和记录研究模式流以及使用[内部函数和外部函数](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)的示例。

<br>

| 参考文章 | 示例应用程序 |
| --- | --- |
| [研究模式](platform-capabilities-and-apis/research-mode.md) | [HoloLens（第一代）](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [研究模式](platform-capabilities-and-apis/research-mode.md) | [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a>QR 码

HoloLens 2 可以检测头戴显示设备周围环境中的 QR 码，从而在每个代码的真实位置建立坐标系统。

<br>

| 参考文章 | 示例 |
| --- | --- |
| [QR 码](platform-capabilities-and-apis/qr-code-tracking.md) | [Unity 中的 QR 码跟踪](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

### <a name="webrtc"></a>WebRTC

MixedReality-WebRTC 项目是一系列组件，可帮助混合现实应用开发人员将对等音频、视频和数据实时通信集成到其应用程序 WebRTC 组件（基于用于实时通信 (RTC) 的 WebRTC 协议）中，受大多数新式网络浏览器支持。

<br>

| 参考文章 | 示例 |
| --- | --- |
| [WebRTC](https://microsoft.github.io/MixedReality-WebRTC) | [WebRTC 示例应用](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a>全息混合现实捕获

混合现实捕获 (MRC) 捕获将真实世界和数字世界混合成照片或视频的第一人称体验，并与他人实时共享你所看到的内容。

<br>

| 参考文章 | 示例 |
| --- | --- |
| [混合现实捕获](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [混合现实捕获示例](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a>全息远程处理

全息远程处理播放器是一款伴侣应用，可连接到支持全息远程处理的电脑应用和游戏。 全息远程处理通过 Wi-Fi 连接将全息内容从电脑实时流式传输到 Microsoft HoloLens，受 HoloLens（第一代）和 HoloLens 2 支持。

<br>

| 参考文章 | 示例 |
| --- | --- |
| [全息远程处理](platform-capabilities-and-apis/holographic-remoting-player.md) | [全息远程处理示例](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |