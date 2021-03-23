---
title: 旁观视图
description: 从外部设备中将全息影像可视化，在外部显示器上显示或记录混合现实体验。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 旁观视图, iPhone, iOS, iPad, OpenCV, 相机, ARKit, HoloLens, 混合现实, MixedRealityToolkit, 演示, 录制
ms.openlocfilehash: aa85b54283b260447c36072b74031554e1aa1939
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "98583116"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="9e3ce-104">HoloLens 和 HoloLens 2 的旁观视图</span><span class="sxs-lookup"><span data-stu-id="9e3ce-104">Spectator View for HoloLens and HoloLens 2</span></span>

![记号笔](images/SpecViewPhoneHero.jpg)

<span data-ttu-id="9e3ce-106">当你戴上 HoloLens 时，很容易忘记没有戴上它的人无法体验到你所能体验到的神奇感受。</span><span class="sxs-lookup"><span data-stu-id="9e3ce-106">When you're wearing a HoloLens, it's easy to forget a person without one can't experience the same wonders you're seeing.</span></span> <span data-ttu-id="9e3ce-107">旁观视图可以让他人在 2D 屏幕上观看 HoloLens 用户看到的东西。</span><span class="sxs-lookup"><span data-stu-id="9e3ce-107">Spectator View lets others see what a HoloLens user sees on a 2D screen.</span></span> <span data-ttu-id="9e3ce-108">利用旁观视图，还可以通过快速且经济的方式在移动设备中录制高清全息影像，以及通过摄像机对全息影像进行高质量的录制。</span><span class="sxs-lookup"><span data-stu-id="9e3ce-108">It's also a fast and affordable approach to recording holograms in HD with mobile devices and getting great quality recordings of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="9e3ce-109">重要资源</span><span class="sxs-lookup"><span data-stu-id="9e3ce-109">Key Resources</span></span>

* [<span data-ttu-id="9e3ce-110">**GitHub 上的旁观视图**</span><span class="sxs-lookup"><span data-stu-id="9e3ce-110">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="9e3ce-111">**旁观视图文档**</span><span class="sxs-lookup"><span data-stu-id="9e3ce-111">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="9e3ce-112">**旁观视图示例**</span><span class="sxs-lookup"><span data-stu-id="9e3ce-112">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="9e3ce-113">用例</span><span class="sxs-lookup"><span data-stu-id="9e3ce-113">Use Cases</span></span>

* <span data-ttu-id="9e3ce-114">可以使用 iPhone 或 Android 设备录制混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="9e3ce-114">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="9e3ce-115">以全高清进行录制，对全息影像和阴影应用抗锯齿效果，可以经济高效且快速地捕获全息影像的视频。</span><span class="sxs-lookup"><span data-stu-id="9e3ce-115">Record in full HD and apply anti-aliasing to holograms and shadow for a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="9e3ce-116">将实时混合现实体验直接从 iPhone 或 iPad 流式传输到 Apple TV，没有任何延迟！</span><span class="sxs-lookup"><span data-stu-id="9e3ce-116">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="9e3ce-117">与来宾共享此体验：让非 HoloLens 用户直接在其手机或平板电脑上体验全息影像。</span><span class="sxs-lookup"><span data-stu-id="9e3ce-117">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="9e3ce-118">当前功能</span><span class="sxs-lookup"><span data-stu-id="9e3ce-118">Current Features</span></span>

* <span data-ttu-id="9e3ce-119">对全息影像进行空间同步，使每个人都能在完全相同的位置观看全息影像。</span><span class="sxs-lookup"><span data-stu-id="9e3ce-119">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="9e3ce-120">iOS（支持 ARKit 的设备）和 Android（支持 ARCore 的设备）支持。</span><span class="sxs-lookup"><span data-stu-id="9e3ce-120">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="9e3ce-121">多个 iOS 来宾。</span><span class="sxs-lookup"><span data-stu-id="9e3ce-121">Multiple iOS guests.</span></span>
<span data-ttu-id="9e3ce-122">录制视频 + 全息影像 + 环境音效 + 全息音效。</span><span class="sxs-lookup"><span data-stu-id="9e3ce-122">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="9e3ce-123">共享表，用于保存视频、通过电子邮件发送视频或将其与其他支持应用共享。</span><span class="sxs-lookup"><span data-stu-id="9e3ce-123">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="9e3ce-124">![标记](images/SpecViewPhoneDemo.jpg)
![标记](images/hololensspectatorview-500px.jpg) ![标记](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="9e3ce-124">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="9e3ce-125">下表显示了不同的旁观视图功能。</span><span class="sxs-lookup"><span data-stu-id="9e3ce-125">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="9e3ce-126">请选择最符合你的视频录制需求的选项：</span><span class="sxs-lookup"><span data-stu-id="9e3ce-126">Choose the option that best fits your video recording needs:</span></span>

|      <span data-ttu-id="9e3ce-127">功能</span><span class="sxs-lookup"><span data-stu-id="9e3ce-127">Functionality</span></span>                                | <span data-ttu-id="9e3ce-128">移动型</span><span class="sxs-lookup"><span data-stu-id="9e3ce-128">Mobile</span></span>                  |                    <span data-ttu-id="9e3ce-129">摄像机</span><span class="sxs-lookup"><span data-stu-id="9e3ce-129">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="9e3ce-130">高清质量</span><span class="sxs-lookup"><span data-stu-id="9e3ce-130">HD quality</span></span>                           |         <span data-ttu-id="9e3ce-131">全高清</span><span class="sxs-lookup"><span data-stu-id="9e3ce-131">Full HD</span></span>         |        <span data-ttu-id="9e3ce-132">专业质量摄影（取决于摄像机）</span><span class="sxs-lookup"><span data-stu-id="9e3ce-132">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="9e3ce-133">相机移动轻松</span><span class="sxs-lookup"><span data-stu-id="9e3ce-133">Easy camera movement</span></span>                 |            <span data-ttu-id="9e3ce-134">✔</span><span class="sxs-lookup"><span data-stu-id="9e3ce-134">✔</span></span>            |                      <span data-ttu-id="9e3ce-135">✔</span><span class="sxs-lookup"><span data-stu-id="9e3ce-135">✔</span></span>                      |
| <span data-ttu-id="9e3ce-136">第三人称视图</span><span class="sxs-lookup"><span data-stu-id="9e3ce-136">Third-person view</span></span>                    |            <span data-ttu-id="9e3ce-137">✔</span><span class="sxs-lookup"><span data-stu-id="9e3ce-137">✔</span></span>            |                      <span data-ttu-id="9e3ce-138">✔</span><span class="sxs-lookup"><span data-stu-id="9e3ce-138">✔</span></span>                      |
| <span data-ttu-id="9e3ce-139">可以流式传输到屏幕</span><span class="sxs-lookup"><span data-stu-id="9e3ce-139">Can be streamed to screens</span></span>           |            <span data-ttu-id="9e3ce-140">✔</span><span class="sxs-lookup"><span data-stu-id="9e3ce-140">✔</span></span>            |                      <span data-ttu-id="9e3ce-141">✔</span><span class="sxs-lookup"><span data-stu-id="9e3ce-141">✔</span></span>                      |
| <span data-ttu-id="9e3ce-142">可移植</span><span class="sxs-lookup"><span data-stu-id="9e3ce-142">Portable</span></span>                             |            <span data-ttu-id="9e3ce-143">✔</span><span class="sxs-lookup"><span data-stu-id="9e3ce-143">✔</span></span>            |                                             |
| <span data-ttu-id="9e3ce-144">无线</span><span class="sxs-lookup"><span data-stu-id="9e3ce-144">Wireless</span></span>                             |            <span data-ttu-id="9e3ce-145">✔</span><span class="sxs-lookup"><span data-stu-id="9e3ce-145">✔</span></span>            |                                             |
| <span data-ttu-id="9e3ce-146">其他必需硬件</span><span class="sxs-lookup"><span data-stu-id="9e3ce-146">Additional required hardware</span></span>         |     <span data-ttu-id="9e3ce-147">Android 手机、iPhone</span><span class="sxs-lookup"><span data-stu-id="9e3ce-147">Android phone, iPhone</span></span>    | <span data-ttu-id="9e3ce-148">HoloLens + 支架 + 三脚架 + 摄像机 + 电脑 + Unity</span><span class="sxs-lookup"><span data-stu-id="9e3ce-148">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="9e3ce-149">硬件投资</span><span class="sxs-lookup"><span data-stu-id="9e3ce-149">Hardware investment</span></span>                  |           <span data-ttu-id="9e3ce-150">低</span><span class="sxs-lookup"><span data-stu-id="9e3ce-150">Low</span></span>            |                     <span data-ttu-id="9e3ce-151">高</span><span class="sxs-lookup"><span data-stu-id="9e3ce-151">High</span></span>                    |
| <span data-ttu-id="9e3ce-152">跨平台</span><span class="sxs-lookup"><span data-stu-id="9e3ce-152">Cross-platform</span></span>                       |           <span data-ttu-id="9e3ce-153">Android、iOS</span><span class="sxs-lookup"><span data-stu-id="9e3ce-153">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="9e3ce-154">同步的内容</span><span class="sxs-lookup"><span data-stu-id="9e3ce-154">Synchronized content</span></span>                 |            <span data-ttu-id="9e3ce-155">✔</span><span class="sxs-lookup"><span data-stu-id="9e3ce-155">✔</span></span>            |                      <span data-ttu-id="9e3ce-156">✔</span><span class="sxs-lookup"><span data-stu-id="9e3ce-156">✔</span></span>                      |
| <span data-ttu-id="9e3ce-157">运行时设置持续时间</span><span class="sxs-lookup"><span data-stu-id="9e3ce-157">Runtime setup duration</span></span>               |         <span data-ttu-id="9e3ce-158">即时</span><span class="sxs-lookup"><span data-stu-id="9e3ce-158">Instant</span></span>          |                     <span data-ttu-id="9e3ce-159">慢</span><span class="sxs-lookup"><span data-stu-id="9e3ce-159">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="9e3ce-160">请参阅</span><span class="sxs-lookup"><span data-stu-id="9e3ce-160">See also</span></span>

* [<span data-ttu-id="9e3ce-161">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="9e3ce-161">Mixed reality capture</span></span>](/hololens/holographic-photos-and-videos) 
* [<span data-ttu-id="9e3ce-162">面向开发人员的混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="9e3ce-162">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="9e3ce-163">混合现实中的共享体验</span><span class="sxs-lookup"><span data-stu-id="9e3ce-163">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)