---
title: 应用质量标准
description: 本文档介绍影响混合现实应用质量的主要因素。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 应用质量标准，混合现实，混合现实应用，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 3f6752c0a15ae7db21be1f4a6d2843339ab28a5c
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581264"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="fcc64-104">应用质量标准</span><span class="sxs-lookup"><span data-stu-id="fcc64-104">App quality criteria</span></span>

<span data-ttu-id="fcc64-105">本文档介绍影响混合现实应用质量的主要因素。</span><span class="sxs-lookup"><span data-stu-id="fcc64-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="fcc64-106">对于每个因素，提供以下信息</span><span class="sxs-lookup"><span data-stu-id="fcc64-106">For each factor, the following information is provided</span></span>
* <span data-ttu-id="fcc64-107">概述-质量因素及其重要原因的简短说明。</span><span class="sxs-lookup"><span data-stu-id="fcc64-107">Overview – a brief description of the quality factor and why it's important.</span></span>
* <span data-ttu-id="fcc64-108">设备影响-影响哪种类型的窗口混合现实设备。</span><span class="sxs-lookup"><span data-stu-id="fcc64-108">Device impact - which type of Window Mixed Reality device is affected.</span></span>
* <span data-ttu-id="fcc64-109">质量标准–如何评估质量因素。</span><span class="sxs-lookup"><span data-stu-id="fcc64-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="fcc64-110">如何衡量方法，以衡量问题 (或经验) 。</span><span class="sxs-lookup"><span data-stu-id="fcc64-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="fcc64-111">建议-概述提供更好的用户体验的方法。</span><span class="sxs-lookup"><span data-stu-id="fcc64-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="fcc64-112">资源-相关的开发人员和设计资源有助于创建更好的应用程序体验。</span><span class="sxs-lookup"><span data-stu-id="fcc64-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="fcc64-113">帧速率</span><span class="sxs-lookup"><span data-stu-id="fcc64-113">Frame rate</span></span>

<span data-ttu-id="fcc64-114">帧速率是全息图稳定性和用户舒适的第一个支柱。</span><span class="sxs-lookup"><span data-stu-id="fcc64-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="fcc64-115">低于建议目标的帧速率可能导致全息影像出现抖动，对体验的 believability 产生负面影响，并可能导致目视疲劳。</span><span class="sxs-lookup"><span data-stu-id="fcc64-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="fcc64-116">针对 Windows Mixed Reality 沉浸式耳机的目标帧速率为 60 Hz 或 90 Hz，具体取决于所支持的与 Windows Mixed Reality 兼容的计算机。</span><span class="sxs-lookup"><span data-stu-id="fcc64-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets is either 60 Hz or 90 Hz depending on which Windows Mixed Reality Compatible PCs you're supporting.</span></span> <span data-ttu-id="fcc64-117">对于 HoloLens，目标帧速率为 60 Hz。</span><span class="sxs-lookup"><span data-stu-id="fcc64-117">For HoloLens, the target frame rate is 60 Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="fcc64-118">设备影响</span><span class="sxs-lookup"><span data-stu-id="fcc64-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fcc64-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="fcc64-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fcc64-121">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-121">✔️</span></span></td>
        <td><span data-ttu-id="fcc64-122">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="fcc64-123">质量标准</span><span class="sxs-lookup"><span data-stu-id="fcc64-123">Quality criteria</span></span>

|  <span data-ttu-id="fcc64-124">最佳</span><span class="sxs-lookup"><span data-stu-id="fcc64-124">Best</span></span>  |  <span data-ttu-id="fcc64-125">适合</span><span class="sxs-lookup"><span data-stu-id="fcc64-125">Meets</span></span> |  <span data-ttu-id="fcc64-126">失败</span><span class="sxs-lookup"><span data-stu-id="fcc64-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="fcc64-127">应用一致地满足目标60设备的每秒帧数 (FPS) 超计算机上的 90 fps;和 60 fps。</span><span class="sxs-lookup"><span data-stu-id="fcc64-127">The app consistently meets frames per second (FPS) goal for target device: 60 fps on HoloLens; 90 fps on Ultra PCs; and 60 fps on mainstream PCs.</span></span> | <span data-ttu-id="fcc64-128">应用程序有间歇性的帧不会阻碍核心体验，或者 FPS 的速度一直低于所需的目标，但不会妨碍应用程序的体验。</span><span class="sxs-lookup"><span data-stu-id="fcc64-128">The app has intermittent frame drops not impeding the core experience, or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="fcc64-129">应用在每10秒或更短时间内每隔10秒或更短时间内遇到一次帧速率下降。</span><span class="sxs-lookup"><span data-stu-id="fcc64-129">The app is experiencing a drop in frame rate on average every 10 seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="fcc64-130">如何度量</span><span class="sxs-lookup"><span data-stu-id="fcc64-130">How to measure</span></span>

* <span data-ttu-id="fcc64-131">实时帧速率图通过 [Windows 设备门户](using-the-windows-device-portal.md#system-performance) 在 "系统性能" 下提供。</span><span class="sxs-lookup"><span data-stu-id="fcc64-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="fcc64-132">对于开发调试，请将帧速率诊断计数器添加到应用中。</span><span class="sxs-lookup"><span data-stu-id="fcc64-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="fcc64-133">查看示例计数器的资源。</span><span class="sxs-lookup"><span data-stu-id="fcc64-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="fcc64-134">当应用程序运行时，可以在设备中体验到帧速率下降。</span><span class="sxs-lookup"><span data-stu-id="fcc64-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="fcc64-135">如果全息图显示意外的抖动运动，则帧速率较低或稳定性平面可能是原因。</span><span class="sxs-lookup"><span data-stu-id="fcc64-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="fcc64-136">建议</span><span class="sxs-lookup"><span data-stu-id="fcc64-136">Recommendations</span></span>

* <span data-ttu-id="fcc64-137">在开发工作开始时添加帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="fcc64-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="fcc64-138">应评估出现帧速率下降的更改，并适当地将其解析为性能 bug。</span><span class="sxs-lookup"><span data-stu-id="fcc64-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="fcc64-139">资源</span><span class="sxs-lookup"><span data-stu-id="fcc64-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="fcc64-140">文档</span><span class="sxs-lookup"><span data-stu-id="fcc64-140">Documentation</span></span>

* [<span data-ttu-id="fcc64-141">了解混合现实的性能</span><span class="sxs-lookup"><span data-stu-id="fcc64-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="fcc64-142">全息图稳定性和帧速率</span><span class="sxs-lookup"><span data-stu-id="fcc64-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="fcc64-143">资产性能预算</span><span class="sxs-lookup"><span data-stu-id="fcc64-143">Asset performance budget</span></span>](../../design/asset-creation-process.md)
* [<span data-ttu-id="fcc64-144">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="fcc64-144">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="fcc64-145">工具和教程</span><span class="sxs-lookup"><span data-stu-id="fcc64-145">Tools and tutorials</span></span>

* [<span data-ttu-id="fcc64-146">混合现实工具包，FPS 计数器显示</span><span class="sxs-lookup"><span data-stu-id="fcc64-146">Mixed Reality Toolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="fcc64-147">混合现实工具包，着色器</span><span class="sxs-lookup"><span data-stu-id="fcc64-147">Mixed Reality Toolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="fcc64-148">外部引用</span><span class="sxs-lookup"><span data-stu-id="fcc64-148">External references</span></span>

* [<span data-ttu-id="fcc64-149">Unity，优化移动应用程序</span><span class="sxs-lookup"><span data-stu-id="fcc64-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="fcc64-150">全息影像稳定性</span><span class="sxs-lookup"><span data-stu-id="fcc64-150">Hologram stability</span></span>

<span data-ttu-id="fcc64-151">稳定的全息影像会提高应用程序的可用性和 believability，并为用户创建更舒适的查看体验。</span><span class="sxs-lookup"><span data-stu-id="fcc64-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="fcc64-152">全息图稳定性的质量是良好的应用开发和设备了解 (磁道) 其环境的能力。</span><span class="sxs-lookup"><span data-stu-id="fcc64-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="fcc64-153">尽管帧速率是稳定性的第一支柱，但其他因素可能会影响稳定性，其中包括：</span><span class="sxs-lookup"><span data-stu-id="fcc64-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="fcc64-154">使用 "稳定" 平面</span><span class="sxs-lookup"><span data-stu-id="fcc64-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="fcc64-155">与空间锚的距离</span><span class="sxs-lookup"><span data-stu-id="fcc64-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="fcc64-156">跟踪</span><span class="sxs-lookup"><span data-stu-id="fcc64-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="fcc64-157">设备影响</span><span class="sxs-lookup"><span data-stu-id="fcc64-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fcc64-158"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-158"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="fcc64-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fcc64-160">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="fcc64-161">质量标准</span><span class="sxs-lookup"><span data-stu-id="fcc64-161">Quality criteria</span></span>

|  <span data-ttu-id="fcc64-162">最佳</span><span class="sxs-lookup"><span data-stu-id="fcc64-162">Best</span></span>  |  <span data-ttu-id="fcc64-163">适合</span><span class="sxs-lookup"><span data-stu-id="fcc64-163">Meets</span></span> |  <span data-ttu-id="fcc64-164">失败</span><span class="sxs-lookup"><span data-stu-id="fcc64-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="fcc64-165">全息影像显示稳定。</span><span class="sxs-lookup"><span data-stu-id="fcc64-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="fcc64-166">辅助内容显示意外移动;或意外移动不会妨碍总体应用程序体验。</span><span class="sxs-lookup"><span data-stu-id="fcc64-166">Secondary content shows unexpected movement; or unexpected movement doesn't impede overall app experience.</span></span> | <span data-ttu-id="fcc64-167">帧中的主要内容显示意外移动。</span><span class="sxs-lookup"><span data-stu-id="fcc64-167">Primary content in frame shows unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="fcc64-168">如何度量</span><span class="sxs-lookup"><span data-stu-id="fcc64-168">How to measure</span></span>

<span data-ttu-id="fcc64-169">戴设备并观看体验：</span><span class="sxs-lookup"><span data-stu-id="fcc64-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="fcc64-170">从一侧到另一侧移动您的头。</span><span class="sxs-lookup"><span data-stu-id="fcc64-170">Move your head from side to side.</span></span> <span data-ttu-id="fcc64-171">如果全息影像显示意外移动，而稳定平面与焦距平面之间的不正确对齐，则可能的原因。</span><span class="sxs-lookup"><span data-stu-id="fcc64-171">If the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="fcc64-172">四处移动影像和环境，查找泳道和 jumpiness 等行为。</span><span class="sxs-lookup"><span data-stu-id="fcc64-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="fcc64-173">此类动作可能由设备不跟踪环境或到空间锚点的距离引起。</span><span class="sxs-lookup"><span data-stu-id="fcc64-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="fcc64-174">如果帧中有大的或多个全息影像，请在不同的深度观察全息影像行为，同时从一侧到另一侧，如果出现抖动，这可能是由稳定平面导致的。</span><span class="sxs-lookup"><span data-stu-id="fcc64-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="fcc64-175">建议</span><span class="sxs-lookup"><span data-stu-id="fcc64-175">Recommendations</span></span>

* <span data-ttu-id="fcc64-176">在开发工作开始时添加帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="fcc64-176">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="fcc64-177">使用 "稳定" 平面。</span><span class="sxs-lookup"><span data-stu-id="fcc64-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="fcc64-178">始终在其定位点的3米以内呈现定位的全息影像。</span><span class="sxs-lookup"><span data-stu-id="fcc64-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="fcc64-179">请确保您的环境已设置正确跟踪。</span><span class="sxs-lookup"><span data-stu-id="fcc64-179">Make sure your environment is set up for proper tracking.</span></span>
* <span data-ttu-id="fcc64-180">设计你的体验，以避免帧内处于不同焦点级别的全息影像。</span><span class="sxs-lookup"><span data-stu-id="fcc64-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="fcc64-181">资源</span><span class="sxs-lookup"><span data-stu-id="fcc64-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="fcc64-182">文档</span><span class="sxs-lookup"><span data-stu-id="fcc64-182">Documentation</span></span>

* [<span data-ttu-id="fcc64-183">全息图稳定性和帧速率</span><span class="sxs-lookup"><span data-stu-id="fcc64-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="fcc64-184">使用 "稳定" 平面进行案例研究</span><span class="sxs-lookup"><span data-stu-id="fcc64-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="fcc64-185">了解混合现实的性能</span><span class="sxs-lookup"><span data-stu-id="fcc64-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="fcc64-186">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="fcc64-186">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="fcc64-187">空间定位点</span><span class="sxs-lookup"><span data-stu-id="fcc64-187">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="fcc64-188">处理跟踪错误</span><span class="sxs-lookup"><span data-stu-id="fcc64-188">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="fcc64-189">固定的引用框架</span><span class="sxs-lookup"><span data-stu-id="fcc64-189">Stationary frame of reference</span></span>](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="fcc64-190">工具和教程</span><span class="sxs-lookup"><span data-stu-id="fcc64-190">Tools and tutorials</span></span>

* [<span data-ttu-id="fcc64-191">MR 配套包，Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="fcc64-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="fcc64-192">实面上的全息影像位置</span><span class="sxs-lookup"><span data-stu-id="fcc64-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="fcc64-193">使用物理 (对象的 Misalignments 的，如果要将其与另一个相对应) ，则可以清楚地指示全息影像和真实世界的非联合。</span><span class="sxs-lookup"><span data-stu-id="fcc64-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) are a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="fcc64-194">位置的准确性应与方案的需求相关;例如，常规表面布局可以使用空间图，但更准确的放置需要使用标记和校准。</span><span class="sxs-lookup"><span data-stu-id="fcc64-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="fcc64-195">设备影响</span><span class="sxs-lookup"><span data-stu-id="fcc64-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fcc64-196"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-196"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="fcc64-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fcc64-198">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-198">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="fcc64-199">质量标准</span><span class="sxs-lookup"><span data-stu-id="fcc64-199">Quality criteria</span></span>

|  <span data-ttu-id="fcc64-200">最佳</span><span class="sxs-lookup"><span data-stu-id="fcc64-200">Best</span></span>  |  <span data-ttu-id="fcc64-201">适合</span><span class="sxs-lookup"><span data-stu-id="fcc64-201">Meets</span></span> |  <span data-ttu-id="fcc64-202">失败</span><span class="sxs-lookup"><span data-stu-id="fcc64-202">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="fcc64-203">全息图通常以厘米到英寸的范围对齐。</span><span class="sxs-lookup"><span data-stu-id="fcc64-203">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="fcc64-204">如果需要更高的准确性，应用程序应为应用规范中的协作提供高效的方式。</span><span class="sxs-lookup"><span data-stu-id="fcc64-204">If you need more accuracy, the app should provide an efficient means for collaboration within the app spec.</span></span> | <span data-ttu-id="fcc64-205">NA</span><span class="sxs-lookup"><span data-stu-id="fcc64-205">NA</span></span> | <span data-ttu-id="fcc64-206">通过断开 surface 平面或远离表面，全息影像将与物理目标对象显示不对齐。</span><span class="sxs-lookup"><span data-stu-id="fcc64-206">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="fcc64-207">如果需要准确性，全息影像应满足方案的邻近规范。</span><span class="sxs-lookup"><span data-stu-id="fcc64-207">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="fcc64-208">如何度量</span><span class="sxs-lookup"><span data-stu-id="fcc64-208">How to measure</span></span>

* <span data-ttu-id="fcc64-209">放置在空间地图上的全息影像不应明显浮动在表面上方或下方。</span><span class="sxs-lookup"><span data-stu-id="fcc64-209">Holograms that are placed on spatial map shouldn't appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="fcc64-210">需要精确放置的全息影像应具有某种形式的标记和校准系统，这种系统对于方案的要求是准确的。</span><span class="sxs-lookup"><span data-stu-id="fcc64-210">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="fcc64-211">建议</span><span class="sxs-lookup"><span data-stu-id="fcc64-211">Recommendations</span></span>

* <span data-ttu-id="fcc64-212">空间映射适用于在不需要精度时将对象放置在图面上。</span><span class="sxs-lookup"><span data-stu-id="fcc64-212">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="fcc64-213">为了获得最佳的精度，请使用标记或海报来设置全息影像和 Xbox 控制器 (或一些手动对齐机制) 用于最终校准。</span><span class="sxs-lookup"><span data-stu-id="fcc64-213">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="fcc64-214">考虑将超大型全息图分解为逻辑部件，并将每个部件与图面对齐。</span><span class="sxs-lookup"><span data-stu-id="fcc64-214">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="fcc64-215">不正确地将 interpupillary 距离设置 (IPD) 也会影响全息图对齐。</span><span class="sxs-lookup"><span data-stu-id="fcc64-215">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="fcc64-216">始终将 HoloLens 配置为用户的 IPD。</span><span class="sxs-lookup"><span data-stu-id="fcc64-216">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="fcc64-217">资源</span><span class="sxs-lookup"><span data-stu-id="fcc64-217">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="fcc64-218">文档</span><span class="sxs-lookup"><span data-stu-id="fcc64-218">Documentation</span></span>

* [<span data-ttu-id="fcc64-219">空间映射放置</span><span class="sxs-lookup"><span data-stu-id="fcc64-219">Spatial mapping placement</span></span>](../../design/spatial-mapping.md#placement)
* [<span data-ttu-id="fcc64-220">房间扫描过程</span><span class="sxs-lookup"><span data-stu-id="fcc64-220">Room scanning process</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="fcc64-221">空间锚定最佳做法</span><span class="sxs-lookup"><span data-stu-id="fcc64-221">Spatial anchors best practices</span></span>](../../design/spatial-anchors.md#best-practices)
* [<span data-ttu-id="fcc64-222">处理跟踪错误</span><span class="sxs-lookup"><span data-stu-id="fcc64-222">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="fcc64-223">Unity 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="fcc64-223">Spatial mapping in Unity</span></span>](../unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="fcc64-224">Vuforia 开发概述</span><span class="sxs-lookup"><span data-stu-id="fcc64-224">Vuforia development overview</span></span>](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="fcc64-225">工具和教程</span><span class="sxs-lookup"><span data-stu-id="fcc64-225">Tools and tutorials</span></span>

* [<span data-ttu-id="fcc64-226">MR 工具包，空间映射库</span><span class="sxs-lookup"><span data-stu-id="fcc64-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="fcc64-227">MR 配套包，海报校准示例</span><span class="sxs-lookup"><span data-stu-id="fcc64-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="fcc64-228">MR 配套包，Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="fcc64-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="fcc64-229">外部引用</span><span class="sxs-lookup"><span data-stu-id="fcc64-229">External references</span></span>

* [<span data-ttu-id="fcc64-230">Lowes 案例研究，精度调整</span><span class="sxs-lookup"><span data-stu-id="fcc64-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="fcc64-231">轻松查看区域</span><span class="sxs-lookup"><span data-stu-id="fcc64-231">Viewing zone of comfort</span></span>

<span data-ttu-id="fcc64-232">应用开发人员通过在不同的深度放置内容和全息影像来控制用户的眼睛汇聚。</span><span class="sxs-lookup"><span data-stu-id="fcc64-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="fcc64-233">戴 HoloLens 的用户将始终适应 2.0 m 以维护一个清晰的图像，因为 HoloLens 显示固定在远离用户的光纤距离2.0 附近。</span><span class="sxs-lookup"><span data-stu-id="fcc64-233">Users wearing HoloLens will always accommodate to 2.0 m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0 m away from the user.</span></span> <span data-ttu-id="fcc64-234">内容深度不正确可能会导致 visual discomfort 或疲劳。</span><span class="sxs-lookup"><span data-stu-id="fcc64-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="fcc64-235">设备影响</span><span class="sxs-lookup"><span data-stu-id="fcc64-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fcc64-236"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-236"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="fcc64-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fcc64-238">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="fcc64-239">质量标准</span><span class="sxs-lookup"><span data-stu-id="fcc64-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="fcc64-240">最佳</span><span class="sxs-lookup"><span data-stu-id="fcc64-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="fcc64-241">将内容放到 2 m。</span><span class="sxs-lookup"><span data-stu-id="fcc64-241">Place content at 2 m.</span></span></li><li><span data-ttu-id="fcc64-242">如果无法将全息影像置于 2 m 个位置，并且无法避免聚合和便利设施之间发生冲突，则全息图位置的最佳区域介于 1.25 m 和 5 m 之间。</span><span class="sxs-lookup"><span data-stu-id="fcc64-242">When holograms cannot be placed at 2 m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25 m and 5 m.</span></span></li><li><span data-ttu-id="fcc64-243">在每种情况下，设计器都应该构建内容来鼓励用户交互 (例如，调整内容大小和默认位置参数) 。</span><span class="sxs-lookup"><span data-stu-id="fcc64-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="fcc64-244">除非方案不需要，否则应使用从 1 m 开始的淡出来实现剪辑平面。</span><span class="sxs-lookup"><span data-stu-id="fcc64-244">Unless not required by the scenario, a clipping plane should be implement with fade out starting at 1 m.</span></span></li><li><span data-ttu-id="fcc64-245">如果需要更密切地观察 motionless 全息图，内容不应超过50厘米。</span><span class="sxs-lookup"><span data-stu-id="fcc64-245">In cases where closer observation of a motionless hologram is required, the content shouldn't be closer than 50 cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="fcc64-246">适合</span><span class="sxs-lookup"><span data-stu-id="fcc64-246">Meets</span></span></td><td> <span data-ttu-id="fcc64-247">内容在查看和运动指导范围内，但不恰当地使用或不使用剪辑平面。</span><span class="sxs-lookup"><span data-stu-id="fcc64-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fcc64-248">失败</span><span class="sxs-lookup"><span data-stu-id="fcc64-248">Fail</span></span> </td><td> <span data-ttu-id="fcc64-249">内容显示太近 (通常 &lt; 为 1.25 m，或 &lt; 50 厘米用于需要更密切观察的静止全息影像。 ) </span><span class="sxs-lookup"><span data-stu-id="fcc64-249">Content is presented too close (typically &lt;1.25 m, or &lt;50 cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="fcc64-250">如何度量</span><span class="sxs-lookup"><span data-stu-id="fcc64-250">How to measure</span></span>

* <span data-ttu-id="fcc64-251">内容通常应为 2 m，但不会超过1.25 或大于 5 m。</span><span class="sxs-lookup"><span data-stu-id="fcc64-251">Content should typically be 2 m away, but no closer than 1.25 or further than 5 m.</span></span>
* <span data-ttu-id="fcc64-252">在少数例外情况下，将在从 1 m 开始的内容淡出的情况下，设置为85CM。</span><span class="sxs-lookup"><span data-stu-id="fcc64-252">With few exceptions, the HoloLens clipping render distance should be set to 85CM with fade out of content starting at 1 m.</span></span> <span data-ttu-id="fcc64-253">接近内容并记下剪辑平面效果。</span><span class="sxs-lookup"><span data-stu-id="fcc64-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="fcc64-254">固定内容不应比 50 cm 更近。</span><span class="sxs-lookup"><span data-stu-id="fcc64-254">Stationary content should not be closer than 50 cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="fcc64-255">建议</span><span class="sxs-lookup"><span data-stu-id="fcc64-255">Recommendations</span></span>

* <span data-ttu-id="fcc64-256">为 2 m 的最佳视图距离设计内容。</span><span class="sxs-lookup"><span data-stu-id="fcc64-256">Design content for the optimal viewing distance of 2 m.</span></span>
* <span data-ttu-id="fcc64-257">将剪辑渲染距离设置为85厘米，从 1 m 开始的内容淡出。</span><span class="sxs-lookup"><span data-stu-id="fcc64-257">Set the clipping render distance to 85 cm with fade out of content starting at 1 m.</span></span>
* <span data-ttu-id="fcc64-258">对于需要更近查看的静止全息影像，剪辑平面应不超过30厘米，并从剪切平面开始至少10厘米。</span><span class="sxs-lookup"><span data-stu-id="fcc64-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30 cm and fade out should start at least 10 cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="fcc64-259">资源</span><span class="sxs-lookup"><span data-stu-id="fcc64-259">Resources</span></span>

* [<span data-ttu-id="fcc64-260">呈现距离</span><span class="sxs-lookup"><span data-stu-id="fcc64-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="fcc64-261">Unity 中的焦点</span><span class="sxs-lookup"><span data-stu-id="fcc64-261">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)
* [<span data-ttu-id="fcc64-262">进行大规模试验</span><span class="sxs-lookup"><span data-stu-id="fcc64-262">Experimenting with scale</span></span>](../../design/scale.md#experimenting-with-scale)
* [<span data-ttu-id="fcc64-263">文本，建议的字号</span><span class="sxs-lookup"><span data-stu-id="fcc64-263">Text, Recommended font size</span></span>](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="fcc64-264">深度切换</span><span class="sxs-lookup"><span data-stu-id="fcc64-264">Depth switching</span></span>

<span data-ttu-id="fcc64-265">无论查看舒适问题的区域如何，用户都需要经常或快速地在近和远的焦距对象之间切换 (包括全息影像和现实世界内容) 可能会导致疲劳和一般 discomfort。</span><span class="sxs-lookup"><span data-stu-id="fcc64-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="fcc64-266">设备影响</span><span class="sxs-lookup"><span data-stu-id="fcc64-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fcc64-267"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-267"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="fcc64-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fcc64-269">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-269">✔️</span></span></td>
        <td><span data-ttu-id="fcc64-270">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="fcc64-271">质量标准</span><span class="sxs-lookup"><span data-stu-id="fcc64-271">Quality criteria</span></span>

|  <span data-ttu-id="fcc64-272">最佳</span><span class="sxs-lookup"><span data-stu-id="fcc64-272">Best</span></span>  |  <span data-ttu-id="fcc64-273">适合</span><span class="sxs-lookup"><span data-stu-id="fcc64-273">Meets</span></span> |  <span data-ttu-id="fcc64-274">失败</span><span class="sxs-lookup"><span data-stu-id="fcc64-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="fcc64-275">不会导致用户 unnaturally refocus 的有限或自然深度切换。</span><span class="sxs-lookup"><span data-stu-id="fcc64-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="fcc64-276">突然深度切换这是核心的，设计为应用程序体验，或由于意外的实际内容而产生的突然深度切换。</span><span class="sxs-lookup"><span data-stu-id="fcc64-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="fcc64-277">一致的深度切换或对应用程序体验不必要或核心的突然深度切换。</span><span class="sxs-lookup"><span data-stu-id="fcc64-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="fcc64-278">如何度量</span><span class="sxs-lookup"><span data-stu-id="fcc64-278">How to measure</span></span>

* <span data-ttu-id="fcc64-279">如果应用要求用户持续和/或突然改变深度焦点，则会出现深度切换问题。</span><span class="sxs-lookup"><span data-stu-id="fcc64-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="fcc64-280">建议</span><span class="sxs-lookup"><span data-stu-id="fcc64-280">Recommendations</span></span>

* <span data-ttu-id="fcc64-281">保持主要内容处于一致的焦点平面上，并确保 "稳定" 平面与焦点平面匹配。</span><span class="sxs-lookup"><span data-stu-id="fcc64-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="fcc64-282">这将减少 oculomotor 疲劳和意外的全息图移动。</span><span class="sxs-lookup"><span data-stu-id="fcc64-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="fcc64-283">资源</span><span class="sxs-lookup"><span data-stu-id="fcc64-283">Resources</span></span>

* [<span data-ttu-id="fcc64-284">呈现距离</span><span class="sxs-lookup"><span data-stu-id="fcc64-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="fcc64-285">Unity 中的焦点</span><span class="sxs-lookup"><span data-stu-id="fcc64-285">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="fcc64-286">使用空间音效</span><span class="sxs-lookup"><span data-stu-id="fcc64-286">Use of spatial sound</span></span>

<span data-ttu-id="fcc64-287">在 Windows Mixed Reality 中，音频引擎通过使用方向、距离和环境模拟模拟3D 声音，提供混合现实体验的听觉组件。</span><span class="sxs-lookup"><span data-stu-id="fcc64-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="fcc64-288">在应用程序中使用空间音效使开发人员能够将 (球的声音 convincingly 在三维空间中，) 整个用户。</span><span class="sxs-lookup"><span data-stu-id="fcc64-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3-dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="fcc64-289">然后，这些声音看起来就像是来自真实的物理对象，或是用户的环境中的混合现实影像。</span><span class="sxs-lookup"><span data-stu-id="fcc64-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="fcc64-290">空间音效是用于混合现实应用程序中的浸入式、可访问性和 UX 设计的强大工具。</span><span class="sxs-lookup"><span data-stu-id="fcc64-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="fcc64-291">设备影响</span><span class="sxs-lookup"><span data-stu-id="fcc64-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fcc64-292"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-292"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="fcc64-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fcc64-294">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-294">✔️</span></span></td>
        <td><span data-ttu-id="fcc64-295">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="fcc64-296">质量标准</span><span class="sxs-lookup"><span data-stu-id="fcc64-296">Quality criteria</span></span>

|  <span data-ttu-id="fcc64-297">最佳</span><span class="sxs-lookup"><span data-stu-id="fcc64-297">Best</span></span>  |  <span data-ttu-id="fcc64-298">适合</span><span class="sxs-lookup"><span data-stu-id="fcc64-298">Meets</span></span> |  <span data-ttu-id="fcc64-299">失败</span><span class="sxs-lookup"><span data-stu-id="fcc64-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="fcc64-300">声音以逻辑方式 spatialized，并适当地使用声音来帮助进行对象发现和用户反馈。</span><span class="sxs-lookup"><span data-stu-id="fcc64-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="fcc64-301">声音非常自然，与对象相关，并在整个方案中标准化。</span><span class="sxs-lookup"><span data-stu-id="fcc64-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="fcc64-302">空间音频适用于 believability，但它不能帮助用户提供反馈和发现。</span><span class="sxs-lookup"><span data-stu-id="fcc64-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="fcc64-303">听不到预期的声音，并且/或缺少声音来帮助用户在 UX 中 spatialized。</span><span class="sxs-lookup"><span data-stu-id="fcc64-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="fcc64-304">或在方案设计中不考虑或使用空间音频。</span><span class="sxs-lookup"><span data-stu-id="fcc64-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="fcc64-305">如何度量</span><span class="sxs-lookup"><span data-stu-id="fcc64-305">How to measure</span></span>

* <span data-ttu-id="fcc64-306">通常，相关声音应从目标全息影像发出 (例如，吠声音来自全息狗。 ) </span><span class="sxs-lookup"><span data-stu-id="fcc64-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="fcc64-307">应在整个 UX 中使用声音提示，以帮助用户在全息帧外提供反馈或了解操作。</span><span class="sxs-lookup"><span data-stu-id="fcc64-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="fcc64-308">建议</span><span class="sxs-lookup"><span data-stu-id="fcc64-308">Recommendations</span></span>

* <span data-ttu-id="fcc64-309">使用空间音频来帮助对象发现和用户界面。</span><span class="sxs-lookup"><span data-stu-id="fcc64-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="fcc64-310">真实声音比合成或非自然声音更好。</span><span class="sxs-lookup"><span data-stu-id="fcc64-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="fcc64-311">大多数声音应为 spatialized。</span><span class="sxs-lookup"><span data-stu-id="fcc64-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="fcc64-312">避免不可见的发射器。</span><span class="sxs-lookup"><span data-stu-id="fcc64-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="fcc64-313">避免空间屏蔽。</span><span class="sxs-lookup"><span data-stu-id="fcc64-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="fcc64-314">规范化所有声音。</span><span class="sxs-lookup"><span data-stu-id="fcc64-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="fcc64-315">资源</span><span class="sxs-lookup"><span data-stu-id="fcc64-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="fcc64-316">文档</span><span class="sxs-lookup"><span data-stu-id="fcc64-316">Documentation</span></span>

* [<span data-ttu-id="fcc64-317">空间音效</span><span class="sxs-lookup"><span data-stu-id="fcc64-317">Spatial sound</span></span>](../../design/spatial-sound.md)
* [<span data-ttu-id="fcc64-318">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="fcc64-318">Spatial sound design</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="fcc64-319">Unity 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="fcc64-319">Spatial sound in Unity</span></span>](../unity/spatial-sound-in-unity.md)
* [<span data-ttu-id="fcc64-320">案例研究，HoloTour 的空间音效</span><span class="sxs-lookup"><span data-stu-id="fcc64-320">Case study, Spatial sound for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="fcc64-321">案例研究，在 RoboRaid 中使用空间音效</span><span class="sxs-lookup"><span data-stu-id="fcc64-321">Case study, Using spatial sound in RoboRaid</span></span>](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="fcc64-322">工具和教程</span><span class="sxs-lookup"><span data-stu-id="fcc64-322">Tools and tutorials</span></span>

* [<span data-ttu-id="fcc64-323">混合现实工具包-空间音频</span><span class="sxs-lookup"><span data-stu-id="fcc64-323">Mixed Reality Toolkit - Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="fcc64-324">专注于全息帧 (FOV) 边界</span><span class="sxs-lookup"><span data-stu-id="fcc64-324">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="fcc64-325">设计良好的用户体验可以创建和维护围绕用户扩展的虚拟环境的有用上下文。</span><span class="sxs-lookup"><span data-stu-id="fcc64-325">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="fcc64-326">缓解 FOV 边界的影响涉及到精心设计的内容规模和上下文、使用空间音频、指导系统和用户的位置。</span><span class="sxs-lookup"><span data-stu-id="fcc64-326">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="fcc64-327">如果完成了正确的操作，该用户将感到不受 FOV 边界的影响，同时具有舒适的应用程序体验。</span><span class="sxs-lookup"><span data-stu-id="fcc64-327">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="fcc64-328">设备影响</span><span class="sxs-lookup"><span data-stu-id="fcc64-328">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fcc64-329"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-329"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="fcc64-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fcc64-331">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-331">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="fcc64-332">质量标准</span><span class="sxs-lookup"><span data-stu-id="fcc64-332">Quality criteria</span></span>

|  <span data-ttu-id="fcc64-333">最佳</span><span class="sxs-lookup"><span data-stu-id="fcc64-333">Best</span></span>  |  <span data-ttu-id="fcc64-334">适合</span><span class="sxs-lookup"><span data-stu-id="fcc64-334">Meets</span></span> |  <span data-ttu-id="fcc64-335">失败</span><span class="sxs-lookup"><span data-stu-id="fcc64-335">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="fcc64-336">用户永远不会失去上下文和查看。</span><span class="sxs-lookup"><span data-stu-id="fcc64-336">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="fcc64-337">为大对象提供了上下文帮助。</span><span class="sxs-lookup"><span data-stu-id="fcc64-337">Context assistance is provided for large objects.</span></span> <span data-ttu-id="fcc64-338">为框架外的对象提供了可发现性和查看指南。</span><span class="sxs-lookup"><span data-stu-id="fcc64-338">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="fcc64-339">通常，动画的动画设计和规模调整适用于舒适的观看体验。</span><span class="sxs-lookup"><span data-stu-id="fcc64-339">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="fcc64-340">用户永远不会丢失上下文，但在有限的情况下，可能需要额外的颈部运动。</span><span class="sxs-lookup"><span data-stu-id="fcc64-340">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="fcc64-341">在有限的情况下，规模会导致动态影像中断垂直或水平的帧，导致某些颈部运动查看全息影像。</span><span class="sxs-lookup"><span data-stu-id="fcc64-341">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="fcc64-342">若要查看全息影像，用户可能丢失上下文和/或一致的颈部运动。</span><span class="sxs-lookup"><span data-stu-id="fcc64-342">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="fcc64-343">如果没有适用于大全息对象的上下文指南，则可以轻松地在帧外移动对象，而无需发现指引，或者需要定期移动影像来查看。</span><span class="sxs-lookup"><span data-stu-id="fcc64-343">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="fcc64-344">如何度量</span><span class="sxs-lookup"><span data-stu-id="fcc64-344">How to measure</span></span>

* <span data-ttu-id="fcc64-345">由于要在边界处裁剪， (大) 全息图的上下文丢失或无法理解。</span><span class="sxs-lookup"><span data-stu-id="fcc64-345">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="fcc64-346">由于缺少引起注意的控制器或可快速移入和移出全息帧的内容，因此很难找到全息影像的位置。</span><span class="sxs-lookup"><span data-stu-id="fcc64-346">Locations of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="fcc64-347">方案需要定期和重复的向上和向下移动，才能完全查看疲劳的全息图。</span><span class="sxs-lookup"><span data-stu-id="fcc64-347">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="fcc64-348">建议</span><span class="sxs-lookup"><span data-stu-id="fcc64-348">Recommendations</span></span>

* <span data-ttu-id="fcc64-349">开始体验适合 FOV 的小对象，然后将视觉提示转换为较大版本。</span><span class="sxs-lookup"><span data-stu-id="fcc64-349">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="fcc64-350">使用空间音频和注意控制器来帮助用户查找 FOV 之外的内容。</span><span class="sxs-lookup"><span data-stu-id="fcc64-350">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="fcc64-351">尽可能避免在垂直剪裁 FOV 的全息影像。</span><span class="sxs-lookup"><span data-stu-id="fcc64-351">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="fcc64-352">为用户提供应用内指南以获得最佳观看位置。</span><span class="sxs-lookup"><span data-stu-id="fcc64-352">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="fcc64-353">资源</span><span class="sxs-lookup"><span data-stu-id="fcc64-353">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="fcc64-354">文档</span><span class="sxs-lookup"><span data-stu-id="fcc64-354">Documentation</span></span>

* [<span data-ttu-id="fcc64-355">全息帧</span><span class="sxs-lookup"><span data-stu-id="fcc64-355">Holographic frame</span></span>](../../design/holographic-frame.md)
* [<span data-ttu-id="fcc64-356">案例研究，HoloStudio UI 和交互设计知识</span><span class="sxs-lookup"><span data-stu-id="fcc64-356">Case Study, HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="fcc64-357">对象和环境的规模</span><span class="sxs-lookup"><span data-stu-id="fcc64-357">Scale of objects and environments</span></span>](../../design/scale.md)
* [<span data-ttu-id="fcc64-358">游标，直观提示</span><span class="sxs-lookup"><span data-stu-id="fcc64-358">Cursors, Visual cues</span></span>](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="fcc64-359">外部引用</span><span class="sxs-lookup"><span data-stu-id="fcc64-359">External references</span></span>

* [<span data-ttu-id="fcc64-360">关于 FOV 的 ado</span><span class="sxs-lookup"><span data-stu-id="fcc64-360">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="fcc64-361">内容对用户位置的响应</span><span class="sxs-lookup"><span data-stu-id="fcc64-361">Content reacts to user position</span></span>

<span data-ttu-id="fcc64-362">全息影像应以与 "实际" 对象相同的方式对用户位置做出反应。</span><span class="sxs-lookup"><span data-stu-id="fcc64-362">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="fcc64-363">一个值得注意的设计注意事项是 UI 元素，这些元素不一定会假设用户的位置为静止，并适应用户的动作。</span><span class="sxs-lookup"><span data-stu-id="fcc64-363">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="fcc64-364">设计可正确适应用户位置的应用将创建更可信的体验，并使其更易于使用。</span><span class="sxs-lookup"><span data-stu-id="fcc64-364">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="fcc64-365">设备影响</span><span class="sxs-lookup"><span data-stu-id="fcc64-365">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fcc64-366"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-366"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="fcc64-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fcc64-368">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-368">✔️</span></span></td>
        <td><span data-ttu-id="fcc64-369">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-369">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="fcc64-370">质量标准</span><span class="sxs-lookup"><span data-stu-id="fcc64-370">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="fcc64-371">最佳</span><span class="sxs-lookup"><span data-stu-id="fcc64-371">Best</span></span> </td><td> <span data-ttu-id="fcc64-372">内容和 UI 适应用户位置，使用户能够在预期用户移动范围内自然地与内容交互。</span><span class="sxs-lookup"><span data-stu-id="fcc64-372">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fcc64-373">适合</span><span class="sxs-lookup"><span data-stu-id="fcc64-373">Meets</span></span> </td><td> <span data-ttu-id="fcc64-374">UI 适应用户位置，但可能会妨碍关键内容的查看，要求用户调整其位置。</span><span class="sxs-lookup"><span data-stu-id="fcc64-374">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="fcc64-375">失败</span><span class="sxs-lookup"><span data-stu-id="fcc64-375">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="fcc64-376">UI 元素在移动过程中丢失或锁定，导致用户 unnaturally 返回 (或查找) 控件。</span><span class="sxs-lookup"><span data-stu-id="fcc64-376">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="fcc64-377">UI 元素限制主要内容的视图。</span><span class="sxs-lookup"><span data-stu-id="fcc64-377">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="fcc64-378">UI 移动并不针对观看距离和势头进行优化，特别是在带 <a href="../../design/billboarding-and-tag-along.md">标记的</a> ui 元素上。</span><span class="sxs-lookup"><span data-stu-id="fcc64-378">UI movement isn't optimized for viewing distance and momentum particularly with <a href="../../design/billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="fcc64-379">如何度量</span><span class="sxs-lookup"><span data-stu-id="fcc64-379">How to measure</span></span>

* <span data-ttu-id="fcc64-380">所有度量值都应在合理的方案范围内完成。</span><span class="sxs-lookup"><span data-stu-id="fcc64-380">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="fcc64-381">当用户移动发生变化时，不要尝试通过极端的用户移动来诱骗应用。</span><span class="sxs-lookup"><span data-stu-id="fcc64-381">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="fcc64-382">对于 UI 元素，不管用户移动如何，相关控件都应可用。</span><span class="sxs-lookup"><span data-stu-id="fcc64-382">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="fcc64-383">例如，如果用户正在使用缩放功能查看和浏览三维地图，则无论位置如何，缩放控件都应立即可供用户使用。</span><span class="sxs-lookup"><span data-stu-id="fcc64-383">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="fcc64-384">建议</span><span class="sxs-lookup"><span data-stu-id="fcc64-384">Recommendations</span></span>

* <span data-ttu-id="fcc64-385">用户是相机，它们控制移动。</span><span class="sxs-lookup"><span data-stu-id="fcc64-385">The user is the camera and they control the movement.</span></span> <span data-ttu-id="fcc64-386">让它们驱动器。</span><span class="sxs-lookup"><span data-stu-id="fcc64-386">Let them drive.</span></span>
* <span data-ttu-id="fcc64-387">对于文本和 menuing 系统，请考虑 billboarding，如果用户要四处移动，则可能会被全局锁定或遮住。</span><span class="sxs-lookup"><span data-stu-id="fcc64-387">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="fcc64-388">同时对需要关注用户的内容使用标记，同时允许用户查看它们前面的内容。</span><span class="sxs-lookup"><span data-stu-id="fcc64-388">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="fcc64-389">资源</span><span class="sxs-lookup"><span data-stu-id="fcc64-389">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="fcc64-390">文档</span><span class="sxs-lookup"><span data-stu-id="fcc64-390">Documentation</span></span>

* [<span data-ttu-id="fcc64-391">交互设计</span><span class="sxs-lookup"><span data-stu-id="fcc64-391">Interaction design</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="fcc64-392">颜色、光线和材料</span><span class="sxs-lookup"><span data-stu-id="fcc64-392">Color, light, and material</span></span>](../../design/color-light-and-materials.md)
* [<span data-ttu-id="fcc64-393">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="fcc64-393">Billboarding and tag-along</span></span>](../../design/billboarding-and-tag-along.md)
* [<span data-ttu-id="fcc64-394">本能交互</span><span class="sxs-lookup"><span data-stu-id="fcc64-394">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="fcc64-395">自我运动和用户位移</span><span class="sxs-lookup"><span data-stu-id="fcc64-395">Self-motion and user locomotion</span></span>](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a><span data-ttu-id="fcc64-396">输入交互清晰度</span><span class="sxs-lookup"><span data-stu-id="fcc64-396">Input interaction clarity</span></span>

<span data-ttu-id="fcc64-397">输入交互清晰度对于应用可用性至关重要，其中包括输入一致性、设计、交互方法的可发现性。</span><span class="sxs-lookup"><span data-stu-id="fcc64-397">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="fcc64-398">用户可以使用平台范围的常见交互，而无需 relearning。</span><span class="sxs-lookup"><span data-stu-id="fcc64-398">User can use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="fcc64-399">如果应用具有自定义输入，则应该清楚地传达并演示。</span><span class="sxs-lookup"><span data-stu-id="fcc64-399">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="fcc64-400">设备影响</span><span class="sxs-lookup"><span data-stu-id="fcc64-400">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fcc64-401"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-401"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="fcc64-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fcc64-403">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-403">✔️</span></span></td>
        <td><span data-ttu-id="fcc64-404">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-404">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="fcc64-405">质量标准</span><span class="sxs-lookup"><span data-stu-id="fcc64-405">Quality criteria</span></span>

|  <span data-ttu-id="fcc64-406">最佳</span><span class="sxs-lookup"><span data-stu-id="fcc64-406">Best</span></span>  |  <span data-ttu-id="fcc64-407">适合</span><span class="sxs-lookup"><span data-stu-id="fcc64-407">Meets</span></span> |  <span data-ttu-id="fcc64-408">失败</span><span class="sxs-lookup"><span data-stu-id="fcc64-408">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="fcc64-409">输入交互方法与 Windows Mixed Reality 提供的 [指南](../../design/interaction-fundamentals.md)一致。</span><span class="sxs-lookup"><span data-stu-id="fcc64-409">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](../../design/interaction-fundamentals.md).</span></span> <span data-ttu-id="fcc64-410">任何自定义输入都不应使用标准输入进行冗余 (而是使用标准交互) ，必须清楚地传达并向用户演示。</span><span class="sxs-lookup"><span data-stu-id="fcc64-410">Any custom input shouldn't be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="fcc64-411">与最佳方法相似，但自定义输入对于标准输入方法是冗余的。</span><span class="sxs-lookup"><span data-stu-id="fcc64-411">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="fcc64-412">用户仍可通过应用体验实现目标和进度。</span><span class="sxs-lookup"><span data-stu-id="fcc64-412">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="fcc64-413">难以理解输入法或按钮映射。</span><span class="sxs-lookup"><span data-stu-id="fcc64-413">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="fcc64-414">输入进行了大量自定义，不支持标准输入、无说明或可能会导致疲劳和舒适的问题。</span><span class="sxs-lookup"><span data-stu-id="fcc64-414">Input is heavily customized, doesn't support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="fcc64-415">如何度量</span><span class="sxs-lookup"><span data-stu-id="fcc64-415">How to measure</span></span>

* <span data-ttu-id="fcc64-416">应用使用一致 [的标准输入法。](../../design/interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="fcc64-416">The app uses consistent [standard input methods.](../../design/interaction-fundamentals.md)</span></span>
* <span data-ttu-id="fcc64-417">如果应用具有自定义输入，则会通过以下方法进行清晰的通信：</span><span class="sxs-lookup"><span data-stu-id="fcc64-417">If the app has custom input, it's clearly communicated through:</span></span>
* <span data-ttu-id="fcc64-418">首次运行体验</span><span class="sxs-lookup"><span data-stu-id="fcc64-418">First-run experience</span></span>
* <span data-ttu-id="fcc64-419">介绍屏幕</span><span class="sxs-lookup"><span data-stu-id="fcc64-419">Introductory screens</span></span>
* <span data-ttu-id="fcc64-420">工具提示</span><span class="sxs-lookup"><span data-stu-id="fcc64-420">Tooltips</span></span>
* <span data-ttu-id="fcc64-421">手部指导</span><span class="sxs-lookup"><span data-stu-id="fcc64-421">Hand coach</span></span>
* <span data-ttu-id="fcc64-422">帮助部分</span><span class="sxs-lookup"><span data-stu-id="fcc64-422">Help section</span></span>
* <span data-ttu-id="fcc64-423">语音朗读</span><span class="sxs-lookup"><span data-stu-id="fcc64-423">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="fcc64-424">建议</span><span class="sxs-lookup"><span data-stu-id="fcc64-424">Recommendations</span></span>

* <span data-ttu-id="fcc64-425">尽可能使用标准输入方法。</span><span class="sxs-lookup"><span data-stu-id="fcc64-425">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="fcc64-426">为非标准输入法提供演示、教程和工具提示。</span><span class="sxs-lookup"><span data-stu-id="fcc64-426">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="fcc64-427">在整个应用程序中使用一致的交互模型。</span><span class="sxs-lookup"><span data-stu-id="fcc64-427">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="fcc64-428">资源</span><span class="sxs-lookup"><span data-stu-id="fcc64-428">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="fcc64-429">文档</span><span class="sxs-lookup"><span data-stu-id="fcc64-429">Documentation</span></span>

* [<span data-ttu-id="fcc64-430">本能交互</span><span class="sxs-lookup"><span data-stu-id="fcc64-430">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="fcc64-431">种不可交互对象</span><span class="sxs-lookup"><span data-stu-id="fcc64-431">Interactable objects</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="fcc64-432">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="fcc64-432">Head-gaze and dwell</span></span>](../../design/gaze-and-dwell.md)
* [<span data-ttu-id="fcc64-433">游标</span><span class="sxs-lookup"><span data-stu-id="fcc64-433">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="fcc64-434">舒适，注视</span><span class="sxs-lookup"><span data-stu-id="fcc64-434">Comfort and gaze</span></span>](../../design/comfort.md#gaze-direction)
* [<span data-ttu-id="fcc64-435">语音输入</span><span class="sxs-lookup"><span data-stu-id="fcc64-435">Voice input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="fcc64-436">运动控制器</span><span class="sxs-lookup"><span data-stu-id="fcc64-436">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="fcc64-437">Unity 的输入移植指南</span><span class="sxs-lookup"><span data-stu-id="fcc64-437">Input porting guide for Unity</span></span>](../porting-apps/input-porting-guide-for-unity.md)
* [<span data-ttu-id="fcc64-438">Unity 中的键盘输入</span><span class="sxs-lookup"><span data-stu-id="fcc64-438">Keyboard input in Unity</span></span>](../unity/keyboard-input-in-unity.md)
* [<span data-ttu-id="fcc64-439">Unity 中的凝视</span><span class="sxs-lookup"><span data-stu-id="fcc64-439">Gaze in Unity</span></span>](../unity/gaze-in-unity.md)
* [<span data-ttu-id="fcc64-440">Unity 中的运动控制器</span><span class="sxs-lookup"><span data-stu-id="fcc64-440">Motion controllers in Unity</span></span>](../unity/motion-controllers-in-unity.md)
* [<span data-ttu-id="fcc64-441">Unity 中的手势</span><span class="sxs-lookup"><span data-stu-id="fcc64-441">Gestures in Unity</span></span>](../unity/gestures-in-unity.md)
* [<span data-ttu-id="fcc64-442">Unity 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="fcc64-442">Voice input in Unity</span></span>](../unity/voice-input-in-unity.md)
* [<span data-ttu-id="fcc64-443">DirectX 中的键盘、鼠标和控制器输入</span><span class="sxs-lookup"><span data-stu-id="fcc64-443">Keyboard, mouse, and controller input in DirectX</span></span>](./keyboard-mouse-and-controller-input-in-directx.md)
* [<span data-ttu-id="fcc64-444">DirectX 中的头部和眼部凝视</span><span class="sxs-lookup"><span data-stu-id="fcc64-444">Head and eye gaze in DirectX</span></span>](../native/gaze-in-directx.md)
* [<span data-ttu-id="fcc64-445">DirectX 中的手和运动控制器</span><span class="sxs-lookup"><span data-stu-id="fcc64-445">Hands and motion controllers in DirectX</span></span>](../native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="fcc64-446">DirectX 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="fcc64-446">Voice input in DirectX</span></span>](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="fcc64-447">工具和教程</span><span class="sxs-lookup"><span data-stu-id="fcc64-447">Tools and tutorials</span></span>

* [<span data-ttu-id="fcc64-448">案例研究：对更多个人计算的追求</span><span class="sxs-lookup"><span data-stu-id="fcc64-448">Case study: The pursuit of more personal computing</span></span>](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="fcc64-449">强制转换研究： HoloStudio UI 和交互设计知识</span><span class="sxs-lookup"><span data-stu-id="fcc64-449">Cast study: HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="fcc64-450">示例应用：元素的定期表</span><span class="sxs-lookup"><span data-stu-id="fcc64-450">Sample app: Periodic table of the elements</span></span>](../unity/periodic-table-of-the-elements.md)
* [<span data-ttu-id="fcc64-451">示例应用：农历模块</span><span class="sxs-lookup"><span data-stu-id="fcc64-451">Sample app: Lunar module</span></span>](../unity/lunar-module.md)

## <a name="interactable-objects"></a><span data-ttu-id="fcc64-452">种不可交互对象</span><span class="sxs-lookup"><span data-stu-id="fcc64-452">Interactable objects</span></span>

<span data-ttu-id="fcc64-453">"Button" 是一种用于在二维抽象环境中触发事件的比喻。</span><span class="sxs-lookup"><span data-stu-id="fcc64-453">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="fcc64-454">在这三维混合现实世界中，我们不必再局限于这种抽象领域。</span><span class="sxs-lookup"><span data-stu-id="fcc64-454">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="fcc64-455">任何内容都可以是触发事件的种不可交互对象。</span><span class="sxs-lookup"><span data-stu-id="fcc64-455">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="fcc64-456">种不可交互对象可表示为从桌子上的咖啡杯到悬浮的球标的任何内容。</span><span class="sxs-lookup"><span data-stu-id="fcc64-456">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="fcc64-457">无论采用何种形式，用户都应该通过视觉对象和音频提示清楚地识别种不可交互对象。</span><span class="sxs-lookup"><span data-stu-id="fcc64-457">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="fcc64-458">设备影响</span><span class="sxs-lookup"><span data-stu-id="fcc64-458">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fcc64-459"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-459"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="fcc64-460"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-460"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fcc64-461">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-461">✔️</span></span></td>
        <td><span data-ttu-id="fcc64-462">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-462">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="fcc64-463">质量标准</span><span class="sxs-lookup"><span data-stu-id="fcc64-463">Quality criteria</span></span>

|  <span data-ttu-id="fcc64-464">最佳</span><span class="sxs-lookup"><span data-stu-id="fcc64-464">Best</span></span>  |  <span data-ttu-id="fcc64-465">适合</span><span class="sxs-lookup"><span data-stu-id="fcc64-465">Meets</span></span> |  <span data-ttu-id="fcc64-466">失败</span><span class="sxs-lookup"><span data-stu-id="fcc64-466">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="fcc64-467">无论采用何种形式，都可以通过视觉对象和音频提示在三种状态下识别种不可交互对象：空闲、目标和选择。</span><span class="sxs-lookup"><span data-stu-id="fcc64-467">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="fcc64-468">"看起来，说它" 是显而易见的，始终在整个体验中使用。</span><span class="sxs-lookup"><span data-stu-id="fcc64-468">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="fcc64-469">对象经过缩放和分布，以允许错误释放目标。</span><span class="sxs-lookup"><span data-stu-id="fcc64-469">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="fcc64-470">用户可以通过音频或视觉对象反馈将对象识别为种不可交互，并可以定位和激活对象。</span><span class="sxs-lookup"><span data-stu-id="fcc64-470">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="fcc64-471">如果没有任何视觉对象或音频提示，用户将无法识别种不可交互对象。</span><span class="sxs-lookup"><span data-stu-id="fcc64-471">Given no visual or audio cues, user can't recognize an interactable object.</span></span> <span data-ttu-id="fcc64-472">交互是由于对象比例或对象之间的距离而容易出错。</span><span class="sxs-lookup"><span data-stu-id="fcc64-472">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="fcc64-473">如何度量</span><span class="sxs-lookup"><span data-stu-id="fcc64-473">How to measure</span></span>

* <span data-ttu-id="fcc64-474">种不可交互对象可识别为 "种不可交互";包括按钮、菜单和特定于应用的内容。</span><span class="sxs-lookup"><span data-stu-id="fcc64-474">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app-specific content.</span></span> <span data-ttu-id="fcc64-475">根据经验法则，在面向种不可交互对象时，应该有视觉和音频提示。</span><span class="sxs-lookup"><span data-stu-id="fcc64-475">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="fcc64-476">建议</span><span class="sxs-lookup"><span data-stu-id="fcc64-476">Recommendations</span></span>

* <span data-ttu-id="fcc64-477">使用视觉和音频反馈进行交互。</span><span class="sxs-lookup"><span data-stu-id="fcc64-477">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="fcc64-478">应为每个输入状态 (空闲、目标、选定) 提供可视反馈</span><span class="sxs-lookup"><span data-stu-id="fcc64-478">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="fcc64-479">应缩放种不可交互对象，并将其放置在错误释放目标位置。</span><span class="sxs-lookup"><span data-stu-id="fcc64-479">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="fcc64-480">分组的种不可交互对象 (例如菜单栏或列表) 应具有适当的目标间距。</span><span class="sxs-lookup"><span data-stu-id="fcc64-480">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="fcc64-481">支持语音命令的按钮和菜单应为命令关键字提供文本标签， ( "查看它" ) </span><span class="sxs-lookup"><span data-stu-id="fcc64-481">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="fcc64-482">资源</span><span class="sxs-lookup"><span data-stu-id="fcc64-482">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="fcc64-483">文档</span><span class="sxs-lookup"><span data-stu-id="fcc64-483">Documentation</span></span>

* [<span data-ttu-id="fcc64-484">可交互对象</span><span class="sxs-lookup"><span data-stu-id="fcc64-484">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="fcc64-485">Unity 中的文本</span><span class="sxs-lookup"><span data-stu-id="fcc64-485">Text in Unity</span></span>](../unity/text-in-unity.md)
* [<span data-ttu-id="fcc64-486">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="fcc64-486">Bounding box and App bar</span></span>](../../design/app-bar-and-bounding-box.md)
* [<span data-ttu-id="fcc64-487">语音输入</span><span class="sxs-lookup"><span data-stu-id="fcc64-487">Voice input</span></span>](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="fcc64-488">工具和教程</span><span class="sxs-lookup"><span data-stu-id="fcc64-488">Tools and tutorials</span></span>

* [<span data-ttu-id="fcc64-489">混合现实工具包-UX</span><span class="sxs-lookup"><span data-stu-id="fcc64-489">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="fcc64-490">房间扫描</span><span class="sxs-lookup"><span data-stu-id="fcc64-490">Room scanning</span></span>

<span data-ttu-id="fcc64-491">需要空间映射数据的应用程序依赖于设备在一段时间内和跨会话自动收集此数据，因为用户浏览其环境中的设备处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="fcc64-491">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="fcc64-492">此数据的完整性和质量取决于多个因素，包括用户的探索量、从浏览开始起经过的时间，以及从设备扫描区域以来是否移动了家具和门等对象。</span><span class="sxs-lookup"><span data-stu-id="fcc64-492">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="fcc64-493">许多应用程序会在体验开始时分析空间映射数据，以判断用户是否应执行额外的步骤来改善空间映射的完整性和质量。</span><span class="sxs-lookup"><span data-stu-id="fcc64-493">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="fcc64-494">如果用户需要扫描环境，请在扫描体验期间提供明确的指南。</span><span class="sxs-lookup"><span data-stu-id="fcc64-494">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="fcc64-495">设备影响</span><span class="sxs-lookup"><span data-stu-id="fcc64-495">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fcc64-496"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-496"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="fcc64-497"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-497"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fcc64-498">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-498">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="fcc64-499">质量标准</span><span class="sxs-lookup"><span data-stu-id="fcc64-499">Quality criteria</span></span>

|  <span data-ttu-id="fcc64-500">最佳</span><span class="sxs-lookup"><span data-stu-id="fcc64-500">Best</span></span>  |  <span data-ttu-id="fcc64-501">适合</span><span class="sxs-lookup"><span data-stu-id="fcc64-501">Meets</span></span> |  <span data-ttu-id="fcc64-502">失败</span><span class="sxs-lookup"><span data-stu-id="fcc64-502">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="fcc64-503">空间网格的可视化通知用户正在进行扫描。</span><span class="sxs-lookup"><span data-stu-id="fcc64-503">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="fcc64-504">用户清楚地了解要执行的操作以及扫描开始和停止的时间。</span><span class="sxs-lookup"><span data-stu-id="fcc64-504">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="fcc64-505">已提供空间网格的可视化效果，但用户可能并不清楚地知道要执行什么操作，并且不会提供任何进度信息。</span><span class="sxs-lookup"><span data-stu-id="fcc64-505">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="fcc64-506">没有网格的可视化效果。</span><span class="sxs-lookup"><span data-stu-id="fcc64-506">No visualization of mesh.</span></span> <span data-ttu-id="fcc64-507">没有向用户提供有关在何处查找或开始扫描的指导信息。</span><span class="sxs-lookup"><span data-stu-id="fcc64-507">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="fcc64-508">如何度量</span><span class="sxs-lookup"><span data-stu-id="fcc64-508">How to measure</span></span>

* <span data-ttu-id="fcc64-509">在所需的空间扫描过程中，会提供视觉和音频指南，指示在何处进行查找以及何时开始和停止扫描。</span><span class="sxs-lookup"><span data-stu-id="fcc64-509">During a required room scan, visual and audio guidance are provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="fcc64-510">建议</span><span class="sxs-lookup"><span data-stu-id="fcc64-510">Recommendations</span></span>

* <span data-ttu-id="fcc64-511">指示用户附近的用户总数需要成为体验的一部分。</span><span class="sxs-lookup"><span data-stu-id="fcc64-511">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="fcc64-512">在扫描开始和停止（例如进度指示器）时进行通信。</span><span class="sxs-lookup"><span data-stu-id="fcc64-512">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="fcc64-513">在扫描过程中使用网格的可视化效果。</span><span class="sxs-lookup"><span data-stu-id="fcc64-513">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="fcc64-514">提供视觉和音频提示，以鼓励用户在房间内查找和移动。</span><span class="sxs-lookup"><span data-stu-id="fcc64-514">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="fcc64-515">通知用户要在何处进行数据改进。</span><span class="sxs-lookup"><span data-stu-id="fcc64-515">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="fcc64-516">在许多情况下，最好向用户告诉用户需要执行哪些操作 (例如，查看天花板) ，以获得必要的扫描质量。</span><span class="sxs-lookup"><span data-stu-id="fcc64-516">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="fcc64-517">资源</span><span class="sxs-lookup"><span data-stu-id="fcc64-517">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="fcc64-518">文档</span><span class="sxs-lookup"><span data-stu-id="fcc64-518">Documentation</span></span>

* [<span data-ttu-id="fcc64-519">房间扫描可视化</span><span class="sxs-lookup"><span data-stu-id="fcc64-519">Room scan visualization</span></span>](../../design/room-scan-visualization.md)
* [<span data-ttu-id="fcc64-520">案例研究：扩展 HoloLens 的空间映射功能</span><span class="sxs-lookup"><span data-stu-id="fcc64-520">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="fcc64-521">案例研究： HoloTour 的空间音效设计</span><span class="sxs-lookup"><span data-stu-id="fcc64-521">Case study: Spatial sound design for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="fcc64-522">案例研究：在片段中创建沉浸式体验</span><span class="sxs-lookup"><span data-stu-id="fcc64-522">Case study: Creating an immersive experience in Fragments</span></span>](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="fcc64-523">工具和教程</span><span class="sxs-lookup"><span data-stu-id="fcc64-523">Tools and tutorials</span></span>

* [<span data-ttu-id="fcc64-524">混合现实工具包-UX</span><span class="sxs-lookup"><span data-stu-id="fcc64-524">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="fcc64-525">方向指示器</span><span class="sxs-lookup"><span data-stu-id="fcc64-525">Directional indicators</span></span>

<span data-ttu-id="fcc64-526">在混合现实应用中，内容可能在视图字段之外或由真实的对象封闭像素。</span><span class="sxs-lookup"><span data-stu-id="fcc64-526">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="fcc64-527">设计良好的应用可使用户更轻松地查找不可见的内容。</span><span class="sxs-lookup"><span data-stu-id="fcc64-527">A well-designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="fcc64-528">方向指示器向用户提醒重要内容，并为内容提供与用户位置相关的指导。</span><span class="sxs-lookup"><span data-stu-id="fcc64-528">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="fcc64-529">不可见内容的指南可以采用声音发射器、双向箭头或直接视觉提示的形式。</span><span class="sxs-lookup"><span data-stu-id="fcc64-529">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="fcc64-530">设备影响</span><span class="sxs-lookup"><span data-stu-id="fcc64-530">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fcc64-531"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-531"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="fcc64-532"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-532"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fcc64-533">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-533">✔️</span></span></td>
        <td><span data-ttu-id="fcc64-534">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-534">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="fcc64-535">质量标准</span><span class="sxs-lookup"><span data-stu-id="fcc64-535">Quality criteria</span></span>

|  <span data-ttu-id="fcc64-536">最佳</span><span class="sxs-lookup"><span data-stu-id="fcc64-536">Best</span></span>  |  <span data-ttu-id="fcc64-537">适合</span><span class="sxs-lookup"><span data-stu-id="fcc64-537">Meets</span></span> |  <span data-ttu-id="fcc64-538">失败</span><span class="sxs-lookup"><span data-stu-id="fcc64-538">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="fcc64-539">视觉对象和音频提示直接指导用户查看视图外的相关内容。</span><span class="sxs-lookup"><span data-stu-id="fcc64-539">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="fcc64-540">在内容的常规方向上指向用户的箭头或某个指示器。</span><span class="sxs-lookup"><span data-stu-id="fcc64-540">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="fcc64-541">相关内容超出了视图的范围，用户未提供不良或无位置指南。</span><span class="sxs-lookup"><span data-stu-id="fcc64-541">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="fcc64-542">如何度量</span><span class="sxs-lookup"><span data-stu-id="fcc64-542">How to measure</span></span>

* <span data-ttu-id="fcc64-543">视图的 user 字段之外的相关内容可通过视觉对象和/或音频提示来发现。</span><span class="sxs-lookup"><span data-stu-id="fcc64-543">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="fcc64-544">建议</span><span class="sxs-lookup"><span data-stu-id="fcc64-544">Recommendations</span></span>

* <span data-ttu-id="fcc64-545">当相关内容在用户的 "视图" 字段之外时，请使用方向指示器和音频提示来引导用户使用内容。</span><span class="sxs-lookup"><span data-stu-id="fcc64-545">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="fcc64-546">在许多情况下，可通过方向箭头首选直接直观的指南。</span><span class="sxs-lookup"><span data-stu-id="fcc64-546">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="fcc64-547">方向指示器不应内置于游标中。</span><span class="sxs-lookup"><span data-stu-id="fcc64-547">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="fcc64-548">资源</span><span class="sxs-lookup"><span data-stu-id="fcc64-548">Resources</span></span>

* [<span data-ttu-id="fcc64-549">全息帧</span><span class="sxs-lookup"><span data-stu-id="fcc64-549">Holographic frame</span></span>](../../design/holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="fcc64-550">数据加载</span><span class="sxs-lookup"><span data-stu-id="fcc64-550">Data loading</span></span>

<span data-ttu-id="fcc64-551">进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。</span><span class="sxs-lookup"><span data-stu-id="fcc64-551">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="fcc64-552">这可能意味着，当进度指示器可见时，用户不能与应用程序交互，还可以指示等待时间的长短。</span><span class="sxs-lookup"><span data-stu-id="fcc64-552">It can mean that the user can't interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="fcc64-553">设备影响</span><span class="sxs-lookup"><span data-stu-id="fcc64-553">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fcc64-554"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-554"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="fcc64-555"><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcc64-555"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fcc64-556">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-556">✔️</span></span></td>
        <td><span data-ttu-id="fcc64-557">✔️</span><span class="sxs-lookup"><span data-stu-id="fcc64-557">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="fcc64-558">质量标准</span><span class="sxs-lookup"><span data-stu-id="fcc64-558">Quality criteria</span></span>

|  <span data-ttu-id="fcc64-559">最佳</span><span class="sxs-lookup"><span data-stu-id="fcc64-559">Best</span></span>  |  <span data-ttu-id="fcc64-560">适合</span><span class="sxs-lookup"><span data-stu-id="fcc64-560">Meets</span></span> |  <span data-ttu-id="fcc64-561">失败</span><span class="sxs-lookup"><span data-stu-id="fcc64-561">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="fcc64-562">动画视觉对象指示器，其形式为进度栏或振铃，显示任何数据加载或处理过程中的进度。</span><span class="sxs-lookup"><span data-stu-id="fcc64-562">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="fcc64-563">视觉对象指示器提供有关等待时间的指导。</span><span class="sxs-lookup"><span data-stu-id="fcc64-563">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="fcc64-564">用户通知用户正在进行数据加载，但没有指示等待的时间。</span><span class="sxs-lookup"><span data-stu-id="fcc64-564">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="fcc64-565">用于任务的数据加载或处理指示器超过5秒。</span><span class="sxs-lookup"><span data-stu-id="fcc64-565">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="fcc64-566">如何度量</span><span class="sxs-lookup"><span data-stu-id="fcc64-566">How to measure</span></span>

* <span data-ttu-id="fcc64-567">在数据加载过程中，不会有超过5秒的空白状态。</span><span class="sxs-lookup"><span data-stu-id="fcc64-567">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="fcc64-568">建议</span><span class="sxs-lookup"><span data-stu-id="fcc64-568">Recommendations</span></span>

* <span data-ttu-id="fcc64-569">当用户可能认为此应用已停止或崩溃时，提供一种 animator 的数据加载。</span><span class="sxs-lookup"><span data-stu-id="fcc64-569">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="fcc64-570">合理的经验法则是任何可能需要5秒以上的 "正在进行" 的活动。</span><span class="sxs-lookup"><span data-stu-id="fcc64-570">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="fcc64-571">资源</span><span class="sxs-lookup"><span data-stu-id="fcc64-571">Resources</span></span>

* [<span data-ttu-id="fcc64-572">显示进度</span><span class="sxs-lookup"><span data-stu-id="fcc64-572">Displaying progress</span></span>](../../design/progress.md)