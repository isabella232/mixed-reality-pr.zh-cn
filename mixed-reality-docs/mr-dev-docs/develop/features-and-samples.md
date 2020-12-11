---
title: 示例和功能应用
description: 看看 HoloLens 的可用功能示例。
author: hferrone
ms.author: jemccull
ms.date: 12/3/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 了解, 示例, MRTK, 研究模式, HoloLens 2, qr 码, WebRTC, 混合现实捕获, 全息远程处理, UX Tools
ms.localizationpriority: high
ms.openlocfilehash: 2624949dd21b4c8e14ed45f152d41900b5f91faf
ms.sourcegitcommit: 924f8c1ceb93c378f800cf88d82944cf80f092bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2020
ms.locfileid: "96615534"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="0a8f2-104">示例和功能应用</span><span class="sxs-lookup"><span data-stu-id="0a8f2-104">Samples and feature apps</span></span>

![图片显示了一名佩戴 HoloLens 并手动操控全息影像的用户](unreal/images/unreal-developer.jpg)

<span data-ttu-id="0a8f2-106">每次开发历程都会先回顾其他开发人员成功构建的内容，混合现实也不例外。</span><span class="sxs-lookup"><span data-stu-id="0a8f2-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="0a8f2-107">目前，我们所有的教程和示例应用均基于 Unity 或 Unreal。</span><span class="sxs-lookup"><span data-stu-id="0a8f2-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="0a8f2-108">在我们为其他引擎和平台制作内容时，“目录”中的相关标题下会列出这些内容。</span><span class="sxs-lookup"><span data-stu-id="0a8f2-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="0a8f2-109">示例应用</span><span class="sxs-lookup"><span data-stu-id="0a8f2-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="0a8f2-110">功能示例</span><span class="sxs-lookup"><span data-stu-id="0a8f2-110">Feature samples</span></span>

<span data-ttu-id="0a8f2-111">下面列出的功能示例与我们的文档中介绍的特定实现相对应，并涵盖了一系列开发平台和硬件设备。</span><span class="sxs-lookup"><span data-stu-id="0a8f2-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="research-mode"></a><span data-ttu-id="0a8f2-112">研究模式</span><span class="sxs-lookup"><span data-stu-id="0a8f2-112">Research Mode</span></span>

<span data-ttu-id="0a8f2-113">第一代 HoloLens 引入了研究模式，用于访问设备上的主要传感器，尤其适用于不打算部署的研究应用程序。</span><span class="sxs-lookup"><span data-stu-id="0a8f2-113">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="0a8f2-114">以下应用程序示例是访问和记录研究模式流以及使用[内部函数和外部函数](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)的示例。</span><span class="sxs-lookup"><span data-stu-id="0a8f2-114">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="0a8f2-115">参考文章</span><span class="sxs-lookup"><span data-stu-id="0a8f2-115">Reference article</span></span> | <span data-ttu-id="0a8f2-116">示例应用程序</span><span class="sxs-lookup"><span data-stu-id="0a8f2-116">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="0a8f2-117">研究模式</span><span class="sxs-lookup"><span data-stu-id="0a8f2-117">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="0a8f2-118">HoloLens（第一代）</span><span class="sxs-lookup"><span data-stu-id="0a8f2-118">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="0a8f2-119">研究模式</span><span class="sxs-lookup"><span data-stu-id="0a8f2-119">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="0a8f2-120">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="0a8f2-120">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="0a8f2-121">QR 码</span><span class="sxs-lookup"><span data-stu-id="0a8f2-121">QR codes</span></span>

<span data-ttu-id="0a8f2-122">HoloLens 2 可以检测头戴显示设备周围环境中的 QR 码，从而在每个代码的真实位置建立坐标系统。</span><span class="sxs-lookup"><span data-stu-id="0a8f2-122">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="0a8f2-123">参考文章</span><span class="sxs-lookup"><span data-stu-id="0a8f2-123">Reference article</span></span> | <span data-ttu-id="0a8f2-124">示例</span><span class="sxs-lookup"><span data-stu-id="0a8f2-124">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="0a8f2-125">QR 码</span><span class="sxs-lookup"><span data-stu-id="0a8f2-125">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="0a8f2-126">Unity 中的 QR 码跟踪</span><span class="sxs-lookup"><span data-stu-id="0a8f2-126">QR code tracking in Unity</span></span>](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

### <a name="webrtc"></a><span data-ttu-id="0a8f2-127">WebRTC</span><span class="sxs-lookup"><span data-stu-id="0a8f2-127">WebRTC</span></span>

<span data-ttu-id="0a8f2-128">MixedReality-WebRTC 项目是一系列组件，可帮助混合现实应用开发人员将对等音频、视频和数据实时通信集成到其应用程序 WebRTC 组件（基于用于实时通信 (RTC) 的 WebRTC 协议）中，受大多数新式网络浏览器支持。</span><span class="sxs-lookup"><span data-stu-id="0a8f2-128">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="0a8f2-129">参考文章</span><span class="sxs-lookup"><span data-stu-id="0a8f2-129">Reference article</span></span> | <span data-ttu-id="0a8f2-130">示例</span><span class="sxs-lookup"><span data-stu-id="0a8f2-130">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="0a8f2-131">WebRTC</span><span class="sxs-lookup"><span data-stu-id="0a8f2-131">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="0a8f2-132">WebRTC 示例应用</span><span class="sxs-lookup"><span data-stu-id="0a8f2-132">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="0a8f2-133">全息混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="0a8f2-133">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="0a8f2-134">混合现实捕获 (MRC) 捕获将真实世界和数字世界混合成照片或视频的第一人称体验，并与他人实时共享你所看到的内容。</span><span class="sxs-lookup"><span data-stu-id="0a8f2-134">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="0a8f2-135">参考文章</span><span class="sxs-lookup"><span data-stu-id="0a8f2-135">Reference article</span></span> | <span data-ttu-id="0a8f2-136">示例</span><span class="sxs-lookup"><span data-stu-id="0a8f2-136">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="0a8f2-137">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="0a8f2-137">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="0a8f2-138">混合现实捕获示例</span><span class="sxs-lookup"><span data-stu-id="0a8f2-138">Mixed Reality Capture samples</span></span>](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="0a8f2-139">全息远程处理</span><span class="sxs-lookup"><span data-stu-id="0a8f2-139">Holographic Remoting</span></span>

<span data-ttu-id="0a8f2-140">全息远程处理播放器是一款伴侣应用，可连接到支持全息远程处理的电脑应用和游戏。</span><span class="sxs-lookup"><span data-stu-id="0a8f2-140">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="0a8f2-141">全息远程处理通过 Wi-Fi 连接将全息内容从电脑实时流式传输到 Microsoft HoloLens，受 HoloLens（第一代）和 HoloLens 2 支持。</span><span class="sxs-lookup"><span data-stu-id="0a8f2-141">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="0a8f2-142">参考文章</span><span class="sxs-lookup"><span data-stu-id="0a8f2-142">Reference article</span></span> | <span data-ttu-id="0a8f2-143">示例</span><span class="sxs-lookup"><span data-stu-id="0a8f2-143">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="0a8f2-144">全息远程处理</span><span class="sxs-lookup"><span data-stu-id="0a8f2-144">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="0a8f2-145">全息远程处理示例</span><span class="sxs-lookup"><span data-stu-id="0a8f2-145">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |