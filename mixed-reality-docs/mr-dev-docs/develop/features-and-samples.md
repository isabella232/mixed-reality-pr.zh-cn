---
title: 示例和功能应用
description: 跟进了解所有可用于 HoloLens 的 Microsoft 示例和混合现实功能应用。
author: hferrone
ms.author: jemccull
ms.date: 6/7/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 了解, 示例, MRTK, 研究模式, HoloLens 2, qr 码, WebRTC, 混合现实捕获, 全息远程处理, UX Tools
ms.localizationpriority: high
ms.openlocfilehash: 78a9e343fde4a6cbc23268f0be353577498d67b6
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906893"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="3dcfd-104">示例和功能应用</span><span class="sxs-lookup"><span data-stu-id="3dcfd-104">Samples and feature apps</span></span>

![图片显示了一名佩戴 HoloLens 并手动操控全息影像的用户](unreal/images/unreal-developer.jpg)

<span data-ttu-id="3dcfd-106">每次开发历程都会先回顾其他开发人员成功构建的内容，混合现实也不例外。</span><span class="sxs-lookup"><span data-stu-id="3dcfd-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="3dcfd-107">目前，我们所有的教程和示例应用均基于 Unity 或 Unreal。</span><span class="sxs-lookup"><span data-stu-id="3dcfd-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="3dcfd-108">在我们为其他引擎和平台制作内容时，“目录”中的相关标题下会列出这些内容。</span><span class="sxs-lookup"><span data-stu-id="3dcfd-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="3dcfd-109">示例应用</span><span class="sxs-lookup"><span data-stu-id="3dcfd-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="3dcfd-110">功能示例</span><span class="sxs-lookup"><span data-stu-id="3dcfd-110">Feature samples</span></span>

<span data-ttu-id="3dcfd-111">下面列出的功能示例与我们的文档中介绍的特定实现相对应，并涵盖了一系列开发平台和硬件设备。</span><span class="sxs-lookup"><span data-stu-id="3dcfd-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="openxr"></a><span data-ttu-id="3dcfd-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="3dcfd-112">OpenXR</span></span>

<span data-ttu-id="3dcfd-113">对于使用 Unity 2020 生成 HoloLens 2 或混合现实应用程序的开发人员，可以使用 OpenXR 插件来代替 WindowsXR 插件，以更好地实现跨平台兼容性。</span><span class="sxs-lookup"><span data-stu-id="3dcfd-113">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span> <span data-ttu-id="3dcfd-114">混合现实 OpenXR 插件还适用于最新的混合现实工具包 2.7。</span><span class="sxs-lookup"><span data-stu-id="3dcfd-114">The Mixed Reality OpenXR Plugin also works well with latest Mixed Reality Toolkit 2.7.</span></span>

<br>

| <span data-ttu-id="3dcfd-115">参考文章</span><span class="sxs-lookup"><span data-stu-id="3dcfd-115">Reference article</span></span> | <span data-ttu-id="3dcfd-116">示例</span><span class="sxs-lookup"><span data-stu-id="3dcfd-116">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="3dcfd-117">使用 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="3dcfd-117">Using the OpenXR plugin</span></span>](./unity/xr-project-setup.md) | [<span data-ttu-id="3dcfd-118">混合现实 OpenXR 与 Unity 示例</span><span class="sxs-lookup"><span data-stu-id="3dcfd-118">Mixed Reality OpenXR with Unity samples</span></span>](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) |
| <span data-ttu-id="3dcfd-119">空值</span><span class="sxs-lookup"><span data-stu-id="3dcfd-119">N/A</span></span> | [<span data-ttu-id="3dcfd-120">OpenXR MRTK Base Unity 项目</span><span class="sxs-lookup"><span data-stu-id="3dcfd-120">OpenXR MRTK Base Unity project</span></span>](https://github.com/microsoft/UnityOpenXRMRTKBase) |

### <a name="research-mode"></a><span data-ttu-id="3dcfd-121">研究模式</span><span class="sxs-lookup"><span data-stu-id="3dcfd-121">Research Mode</span></span>

<span data-ttu-id="3dcfd-122">第一代 HoloLens 引入了研究模式，用于访问设备上的主要传感器，尤其适用于不打算部署的研究应用程序。</span><span class="sxs-lookup"><span data-stu-id="3dcfd-122">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="3dcfd-123">以下应用程序示例是访问和记录研究模式流以及使用[内部函数和外部函数](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)的示例。</span><span class="sxs-lookup"><span data-stu-id="3dcfd-123">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="3dcfd-124">参考文章</span><span class="sxs-lookup"><span data-stu-id="3dcfd-124">Reference article</span></span> | <span data-ttu-id="3dcfd-125">示例应用程序</span><span class="sxs-lookup"><span data-stu-id="3dcfd-125">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="3dcfd-126">研究模式</span><span class="sxs-lookup"><span data-stu-id="3dcfd-126">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="3dcfd-127">HoloLens（第一代）</span><span class="sxs-lookup"><span data-stu-id="3dcfd-127">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="3dcfd-128">研究模式</span><span class="sxs-lookup"><span data-stu-id="3dcfd-128">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="3dcfd-129">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3dcfd-129">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="3dcfd-130">QR 码</span><span class="sxs-lookup"><span data-stu-id="3dcfd-130">QR codes</span></span>

<span data-ttu-id="3dcfd-131">HoloLens 2 可以检测头戴显示设备周围环境中的 QR 码，从而在每个代码的真实位置建立坐标系统。</span><span class="sxs-lookup"><span data-stu-id="3dcfd-131">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="3dcfd-132">参考文章</span><span class="sxs-lookup"><span data-stu-id="3dcfd-132">Reference article</span></span> | <span data-ttu-id="3dcfd-133">示例</span><span class="sxs-lookup"><span data-stu-id="3dcfd-133">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="3dcfd-134">QR 码</span><span class="sxs-lookup"><span data-stu-id="3dcfd-134">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="3dcfd-135">Unity 中的 QR 码跟踪</span><span class="sxs-lookup"><span data-stu-id="3dcfd-135">QR code tracking in Unity</span></span>](https://github.com/microsoft/MixedReality-QRCode-Sample) |

### <a name="scene-understanding"></a><span data-ttu-id="3dcfd-136">场景理解</span><span class="sxs-lookup"><span data-stu-id="3dcfd-136">Scene understanding</span></span>

<span data-ttu-id="3dcfd-137">场景理解为混合现实开发人员提供了结构化的高级别环境表示，旨在直观地为环境感知型应用程序进行开发。</span><span class="sxs-lookup"><span data-stu-id="3dcfd-137">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="3dcfd-138">场景理解通过组合现有混合现实运行时（如高度准确但结构化空间映射较少的运行时）和新的 AI 驱动运行时的功能来实现这一点。</span><span class="sxs-lookup"><span data-stu-id="3dcfd-138">Scene understanding does this by combining the power of existing mixed reality runtimes, like the highly accurate but less structured spatial mapping and new AI driven runtimes.</span></span>

<br>

| <span data-ttu-id="3dcfd-139">参考文章</span><span class="sxs-lookup"><span data-stu-id="3dcfd-139">Reference article</span></span> | <span data-ttu-id="3dcfd-140">示例</span><span class="sxs-lookup"><span data-stu-id="3dcfd-140">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="3dcfd-141">场景理解</span><span class="sxs-lookup"><span data-stu-id="3dcfd-141">Scene understanding</span></span>](../design/scene-understanding.md) | [<span data-ttu-id="3dcfd-142">混合现实场景理解示例</span><span class="sxs-lookup"><span data-stu-id="3dcfd-142">Mixed Reality Scene Understanding samples</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples) |

### <a name="webrtc"></a><span data-ttu-id="3dcfd-143">WebRTC</span><span class="sxs-lookup"><span data-stu-id="3dcfd-143">WebRTC</span></span>

<span data-ttu-id="3dcfd-144">MixedReality-WebRTC 项目是一系列组件，可帮助混合现实应用开发人员将对等音频、视频和数据实时通信集成到其应用程序 WebRTC 组件（基于用于实时通信 (RTC) 的 WebRTC 协议）中，受大多数新式网络浏览器支持。</span><span class="sxs-lookup"><span data-stu-id="3dcfd-144">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="3dcfd-145">参考文章</span><span class="sxs-lookup"><span data-stu-id="3dcfd-145">Reference article</span></span> | <span data-ttu-id="3dcfd-146">示例</span><span class="sxs-lookup"><span data-stu-id="3dcfd-146">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="3dcfd-147">WebRTC</span><span class="sxs-lookup"><span data-stu-id="3dcfd-147">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="3dcfd-148">WebRTC 示例应用</span><span class="sxs-lookup"><span data-stu-id="3dcfd-148">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="3dcfd-149">全息混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="3dcfd-149">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="3dcfd-150">混合现实捕获 (MRC) 捕获将真实世界和数字世界混合成照片或视频的第一人称体验，并与他人实时共享你所看到的内容。</span><span class="sxs-lookup"><span data-stu-id="3dcfd-150">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="3dcfd-151">参考文章</span><span class="sxs-lookup"><span data-stu-id="3dcfd-151">Reference article</span></span> | <span data-ttu-id="3dcfd-152">示例</span><span class="sxs-lookup"><span data-stu-id="3dcfd-152">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="3dcfd-153">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="3dcfd-153">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="3dcfd-154">混合现实捕获示例</span><span class="sxs-lookup"><span data-stu-id="3dcfd-154">Mixed Reality Capture samples</span></span>](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="3dcfd-155">全息远程处理</span><span class="sxs-lookup"><span data-stu-id="3dcfd-155">Holographic Remoting</span></span>

<span data-ttu-id="3dcfd-156">全息远程处理播放器是一款伴侣应用，可连接到支持全息远程处理的电脑应用和游戏。</span><span class="sxs-lookup"><span data-stu-id="3dcfd-156">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="3dcfd-157">全息远程处理通过 Wi-Fi 连接将全息内容从电脑实时流式传输到 Microsoft HoloLens，受 HoloLens（第一代）和 HoloLens 2 支持。</span><span class="sxs-lookup"><span data-stu-id="3dcfd-157">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="3dcfd-158">参考文章</span><span class="sxs-lookup"><span data-stu-id="3dcfd-158">Reference article</span></span> | <span data-ttu-id="3dcfd-159">示例</span><span class="sxs-lookup"><span data-stu-id="3dcfd-159">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="3dcfd-160">全息远程处理</span><span class="sxs-lookup"><span data-stu-id="3dcfd-160">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="3dcfd-161">全息远程处理示例</span><span class="sxs-lookup"><span data-stu-id="3dcfd-161">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |