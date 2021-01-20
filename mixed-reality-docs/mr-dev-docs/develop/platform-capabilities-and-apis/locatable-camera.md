---
title: 可定位相机
description: 有关短期正面相机相机、工作原理以及开发人员可用的配置文件和分辨率的一般信息。
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: 照相机，hololens，彩色相机，正面朝，hololens 2，cv，计算机视觉，基准，标记，qr 码，qr，照片，视频
ms.openlocfilehash: bc478aa658b26eb3a4efb16c62d0874b12992e78
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583624"
---
# <a name="locatable-camera"></a><span data-ttu-id="4e19f-104">可定位相机</span><span class="sxs-lookup"><span data-stu-id="4e19f-104">Locatable camera</span></span>

<span data-ttu-id="4e19f-105">HoloLens 包含在设备前面安装的面向世界的相机，使应用能够查看用户看到的内容。</span><span class="sxs-lookup"><span data-stu-id="4e19f-105">HoloLens includes a world-facing camera mounted on the front of the device, which enables apps to see what the user sees.</span></span> <span data-ttu-id="4e19f-106">开发人员可以访问和控制照相机，就像在 smartphone、笔记本或台式机上的彩色照相机一样。</span><span class="sxs-lookup"><span data-stu-id="4e19f-106">Developers have access to and control of the camera, just as they would for color cameras on smartphones, portables, or desktops.</span></span> <span data-ttu-id="4e19f-107">在 mobile 和 desktop 上工作的相同通用 windows [media capture](/uwp/api/Windows.Media.Capture.MediaCapture) 和 windows Media foundation Api 在 HoloLens 上工作。</span><span class="sxs-lookup"><span data-stu-id="4e19f-107">The same universal windows [media capture](/uwp/api/Windows.Media.Capture.MediaCapture) and windows media foundation APIs that work on mobile and desktop work on HoloLens.</span></span> <span data-ttu-id="4e19f-108">Unity [已包装这些 Windows api](../unity/locatable-camera-in-unity.md) ，以便在 HoloLens 上抽象相机使用情况功能。</span><span class="sxs-lookup"><span data-stu-id="4e19f-108">Unity [has wrapped these windows APIs](../unity/locatable-camera-in-unity.md) to abstract camera usage features on HoloLens.</span></span> <span data-ttu-id="4e19f-109">功能任务包括拍摄定期照片和视频 (有或不包含全息影像) 并定位相机在场景上的位置和透视。</span><span class="sxs-lookup"><span data-stu-id="4e19f-109">Feature tasks include taking regular photos and videos (with or without holograms) and locating the camera's position in and perspective on the scene.</span></span>

## <a name="device-camera-information"></a><span data-ttu-id="4e19f-110">设备照相机信息</span><span class="sxs-lookup"><span data-stu-id="4e19f-110">Device camera information</span></span>

### <a name="hololens-first-generation"></a><span data-ttu-id="4e19f-111">HoloLens (第一代) </span><span class="sxs-lookup"><span data-stu-id="4e19f-111">HoloLens (first-generation)</span></span>

* <span data-ttu-id="4e19f-112">固定的照片/视频 (PV) 带有自动白平衡、自动曝光和完整图像处理管道的相机。</span><span class="sxs-lookup"><span data-stu-id="4e19f-112">Fixed focus photo/video (PV) camera with auto white balance, auto exposure, and full image-processing pipeline.</span></span>
* <span data-ttu-id="4e19f-113">当照相机处于活动状态时，面向世界的白色隐私 LED 将发亮</span><span class="sxs-lookup"><span data-stu-id="4e19f-113">White Privacy LED facing the world will illuminate whenever the camera is active</span></span>
* <span data-ttu-id="4e19f-114">摄像头支持以下模式 (所有模式均为16:9 纵横比) 为30、24、20、15和 5 fps：</span><span class="sxs-lookup"><span data-stu-id="4e19f-114">The camera supports the following modes (all modes are 16:9 aspect ratio) at 30, 24, 20, 15, and 5 fps:</span></span>

  |  <span data-ttu-id="4e19f-115">视频</span><span class="sxs-lookup"><span data-stu-id="4e19f-115">Video</span></span>  |  <span data-ttu-id="4e19f-116">预览</span><span class="sxs-lookup"><span data-stu-id="4e19f-116">Preview</span></span>  |  <span data-ttu-id="4e19f-117">正常</span><span class="sxs-lookup"><span data-stu-id="4e19f-117">Still</span></span>  |  <span data-ttu-id="4e19f-118">视图的水平字段 (H-FOV) </span><span class="sxs-lookup"><span data-stu-id="4e19f-118">Horizontal Field of View (H-FOV)</span></span> |  <span data-ttu-id="4e19f-119">建议的用法</span><span class="sxs-lookup"><span data-stu-id="4e19f-119">Suggested usage</span></span> | 
  |----------|----------|----------|----------|----------|
  |  <span data-ttu-id="4e19f-120">1280x720</span><span class="sxs-lookup"><span data-stu-id="4e19f-120">1280x720</span></span> |  <span data-ttu-id="4e19f-121">1280x720</span><span class="sxs-lookup"><span data-stu-id="4e19f-121">1280x720</span></span> |  <span data-ttu-id="4e19f-122">1280x720</span><span class="sxs-lookup"><span data-stu-id="4e19f-122">1280x720</span></span> |  <span data-ttu-id="4e19f-123">45度</span><span class="sxs-lookup"><span data-stu-id="4e19f-123">45 deg</span></span>  |  <span data-ttu-id="4e19f-124">) 视频抖动 (默认模式</span><span class="sxs-lookup"><span data-stu-id="4e19f-124">(default mode with video stabilization)</span></span> | 
  |  <span data-ttu-id="4e19f-125">不适用</span><span class="sxs-lookup"><span data-stu-id="4e19f-125">N/A</span></span> |  <span data-ttu-id="4e19f-126">不适用</span><span class="sxs-lookup"><span data-stu-id="4e19f-126">N/A</span></span> |  <span data-ttu-id="4e19f-127">2048x1152</span><span class="sxs-lookup"><span data-stu-id="4e19f-127">2048x1152</span></span> |  <span data-ttu-id="4e19f-128">67度</span><span class="sxs-lookup"><span data-stu-id="4e19f-128">67 deg</span></span> |  <span data-ttu-id="4e19f-129">最高分辨率静止图像</span><span class="sxs-lookup"><span data-stu-id="4e19f-129">Highest resolution still image</span></span> | 
  |  <span data-ttu-id="4e19f-130">1408x792</span><span class="sxs-lookup"><span data-stu-id="4e19f-130">1408x792</span></span> |  <span data-ttu-id="4e19f-131">1408x792</span><span class="sxs-lookup"><span data-stu-id="4e19f-131">1408x792</span></span> |  <span data-ttu-id="4e19f-132">1408x792</span><span class="sxs-lookup"><span data-stu-id="4e19f-132">1408x792</span></span> |  <span data-ttu-id="4e19f-133">48度</span><span class="sxs-lookup"><span data-stu-id="4e19f-133">48 deg</span></span> |  <span data-ttu-id="4e19f-134">Overscan (在视频稳定性之前填充) 分辨率</span><span class="sxs-lookup"><span data-stu-id="4e19f-134">Overscan (padding) resolution before video stabilization</span></span> | 
  |  <span data-ttu-id="4e19f-135">1344x756</span><span class="sxs-lookup"><span data-stu-id="4e19f-135">1344x756</span></span> |  <span data-ttu-id="4e19f-136">1344x756</span><span class="sxs-lookup"><span data-stu-id="4e19f-136">1344x756</span></span> |  <span data-ttu-id="4e19f-137">1344x756</span><span class="sxs-lookup"><span data-stu-id="4e19f-137">1344x756</span></span> |  <span data-ttu-id="4e19f-138">67度</span><span class="sxs-lookup"><span data-stu-id="4e19f-138">67 deg</span></span> |  <span data-ttu-id="4e19f-139">带有 overscan 的大型 FOV 视频模式</span><span class="sxs-lookup"><span data-stu-id="4e19f-139">Large FOV video mode with overscan</span></span> | 
  |  <span data-ttu-id="4e19f-140">896x504</span><span class="sxs-lookup"><span data-stu-id="4e19f-140">896x504</span></span> |  <span data-ttu-id="4e19f-141">896x504</span><span class="sxs-lookup"><span data-stu-id="4e19f-141">896x504</span></span> |  <span data-ttu-id="4e19f-142">896x504</span><span class="sxs-lookup"><span data-stu-id="4e19f-142">896x504</span></span> |  <span data-ttu-id="4e19f-143">48度</span><span class="sxs-lookup"><span data-stu-id="4e19f-143">48 deg</span></span> |  <span data-ttu-id="4e19f-144">图像处理任务的低功率/低分辨率模式</span><span class="sxs-lookup"><span data-stu-id="4e19f-144">Low power / Low-resolution mode for image-processing tasks</span></span> | 

### <a name="hololens-2"></a><span data-ttu-id="4e19f-145">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4e19f-145">HoloLens 2</span></span>

* <span data-ttu-id="4e19f-146">自动聚焦照片/视频 (PV) 带有自动白平衡、自动曝光和完整图像处理管道的相机。</span><span class="sxs-lookup"><span data-stu-id="4e19f-146">Auto-focus photo/video (PV) camera with auto white balance, auto exposure, and full image-processing pipeline.</span></span>
* <span data-ttu-id="4e19f-147">当照相机处于活动状态时，世界上的白色隐私 LED 将会亮起。</span><span class="sxs-lookup"><span data-stu-id="4e19f-147">White Privacy LED facing the world will illuminate whenever the camera is active.</span></span>
* <span data-ttu-id="4e19f-148">HoloLens 2 支持不同的相机配置文件。</span><span class="sxs-lookup"><span data-stu-id="4e19f-148">HoloLens 2 supports different camera profiles.</span></span> <span data-ttu-id="4e19f-149">了解如何 [发现和选择相机功能](//windows/uwp/audio-video-camera/camera-profiles)。</span><span class="sxs-lookup"><span data-stu-id="4e19f-149">Learn how to [discover and select camera capabilities](//windows/uwp/audio-video-camera/camera-profiles).</span></span>
* <span data-ttu-id="4e19f-150">摄像头支持以下配置文件和分辨率 (所有视频模式16:9 纵横比) ：</span><span class="sxs-lookup"><span data-stu-id="4e19f-150">The camera supports the following profiles and resolutions (all video modes are 16:9 aspect ratio):</span></span>
  
  | <span data-ttu-id="4e19f-151">配置文件</span><span class="sxs-lookup"><span data-stu-id="4e19f-151">Profile</span></span>                                         | <span data-ttu-id="4e19f-152">视频</span><span class="sxs-lookup"><span data-stu-id="4e19f-152">Video</span></span>     | <span data-ttu-id="4e19f-153">预览</span><span class="sxs-lookup"><span data-stu-id="4e19f-153">Preview</span></span>   | <span data-ttu-id="4e19f-154">正常</span><span class="sxs-lookup"><span data-stu-id="4e19f-154">Still</span></span>     | <span data-ttu-id="4e19f-155">帧速率</span><span class="sxs-lookup"><span data-stu-id="4e19f-155">Frame rates</span></span> | <span data-ttu-id="4e19f-156">视图的水平字段 (H-FOV) </span><span class="sxs-lookup"><span data-stu-id="4e19f-156">Horizontal Field of View (H-FOV)</span></span> | <span data-ttu-id="4e19f-157">建议的用法</span><span class="sxs-lookup"><span data-stu-id="4e19f-157">Suggested usage</span></span>                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | <span data-ttu-id="4e19f-158">旧，0 BalancedVideoAndPhoto，100</span><span class="sxs-lookup"><span data-stu-id="4e19f-158">Legacy,0  BalancedVideoAndPhoto,100</span></span>             | <span data-ttu-id="4e19f-159">2272x1278</span><span class="sxs-lookup"><span data-stu-id="4e19f-159">2272x1278</span></span> | <span data-ttu-id="4e19f-160">2272x1278</span><span class="sxs-lookup"><span data-stu-id="4e19f-160">2272x1278</span></span> |           | <span data-ttu-id="4e19f-161">15.30</span><span class="sxs-lookup"><span data-stu-id="4e19f-161">15.30</span></span>       | <span data-ttu-id="4e19f-162">64.69</span><span class="sxs-lookup"><span data-stu-id="4e19f-162">64.69</span></span>                            | <span data-ttu-id="4e19f-163">高质量视频录制</span><span class="sxs-lookup"><span data-stu-id="4e19f-163">High-quality video recording</span></span>                |
  | <span data-ttu-id="4e19f-164">旧，0 BalancedVideoAndPhoto，100</span><span class="sxs-lookup"><span data-stu-id="4e19f-164">Legacy,0  BalancedVideoAndPhoto,100</span></span>             | <span data-ttu-id="4e19f-165">896x504</span><span class="sxs-lookup"><span data-stu-id="4e19f-165">896x504</span></span>   | <span data-ttu-id="4e19f-166">896x504</span><span class="sxs-lookup"><span data-stu-id="4e19f-166">896x504</span></span>   |           | <span data-ttu-id="4e19f-167">15.30</span><span class="sxs-lookup"><span data-stu-id="4e19f-167">15.30</span></span>       | <span data-ttu-id="4e19f-168">64.69</span><span class="sxs-lookup"><span data-stu-id="4e19f-168">64.69</span></span>                            | <span data-ttu-id="4e19f-169">用于高质量照片捕获的预览流</span><span class="sxs-lookup"><span data-stu-id="4e19f-169">Preview stream for high-quality photo capture</span></span> |
  | <span data-ttu-id="4e19f-170">旧，0 BalancedVideoAndPhoto，100</span><span class="sxs-lookup"><span data-stu-id="4e19f-170">Legacy,0  BalancedVideoAndPhoto,100</span></span>             |           |           | <span data-ttu-id="4e19f-171">3904x2196</span><span class="sxs-lookup"><span data-stu-id="4e19f-171">3904x2196</span></span> |             | <span data-ttu-id="4e19f-172">64.69</span><span class="sxs-lookup"><span data-stu-id="4e19f-172">64.69</span></span>                            | <span data-ttu-id="4e19f-173">优质照片捕获</span><span class="sxs-lookup"><span data-stu-id="4e19f-173">High-quality photo capture</span></span>                  |
  | <span data-ttu-id="4e19f-174">BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="4e19f-174">BalancedVideoAndPhoto, 120</span></span>                       | <span data-ttu-id="4e19f-175">1952x1100</span><span class="sxs-lookup"><span data-stu-id="4e19f-175">1952x1100</span></span> | <span data-ttu-id="4e19f-176">1952x1100</span><span class="sxs-lookup"><span data-stu-id="4e19f-176">1952x1100</span></span> | <span data-ttu-id="4e19f-177">1952x1100</span><span class="sxs-lookup"><span data-stu-id="4e19f-177">1952x1100</span></span> | <span data-ttu-id="4e19f-178">15.30</span><span class="sxs-lookup"><span data-stu-id="4e19f-178">15.30</span></span>       | <span data-ttu-id="4e19f-179">64.69</span><span class="sxs-lookup"><span data-stu-id="4e19f-179">64.69</span></span>                            | <span data-ttu-id="4e19f-180">长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="4e19f-180">Long duration scenarios</span></span>                     |
  | <span data-ttu-id="4e19f-181">BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="4e19f-181">BalancedVideoAndPhoto, 120</span></span>                       | <span data-ttu-id="4e19f-182">1504x846</span><span class="sxs-lookup"><span data-stu-id="4e19f-182">1504x846</span></span>  | <span data-ttu-id="4e19f-183">1504x846</span><span class="sxs-lookup"><span data-stu-id="4e19f-183">1504x846</span></span>  |           | <span data-ttu-id="4e19f-184">15.30</span><span class="sxs-lookup"><span data-stu-id="4e19f-184">15.30</span></span>       | <span data-ttu-id="4e19f-185">64.69</span><span class="sxs-lookup"><span data-stu-id="4e19f-185">64.69</span></span>                            | <span data-ttu-id="4e19f-186">长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="4e19f-186">Long duration scenarios</span></span>                     |
  | <span data-ttu-id="4e19f-187">视频会议，100</span><span class="sxs-lookup"><span data-stu-id="4e19f-187">VideoConferencing,100</span></span>                           | <span data-ttu-id="4e19f-188">1952x1100</span><span class="sxs-lookup"><span data-stu-id="4e19f-188">1952x1100</span></span> | <span data-ttu-id="4e19f-189">1952x1100</span><span class="sxs-lookup"><span data-stu-id="4e19f-189">1952x1100</span></span> | <span data-ttu-id="4e19f-190">1952x1100</span><span class="sxs-lookup"><span data-stu-id="4e19f-190">1952x1100</span></span> | <span data-ttu-id="4e19f-191">15、30、60</span><span class="sxs-lookup"><span data-stu-id="4e19f-191">15,30,60</span></span>    | <span data-ttu-id="4e19f-192">64.69</span><span class="sxs-lookup"><span data-stu-id="4e19f-192">64.69</span></span>                            | <span data-ttu-id="4e19f-193">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="4e19f-193">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="4e19f-194">视频会议，100</span><span class="sxs-lookup"><span data-stu-id="4e19f-194">Videoconferencing,100</span></span>                           | <span data-ttu-id="4e19f-195">1504x846</span><span class="sxs-lookup"><span data-stu-id="4e19f-195">1504x846</span></span>  | <span data-ttu-id="4e19f-196">1504x846</span><span class="sxs-lookup"><span data-stu-id="4e19f-196">1504x846</span></span>  |           | <span data-ttu-id="4e19f-197">5、15、30、60</span><span class="sxs-lookup"><span data-stu-id="4e19f-197">5,15,30,60</span></span>  | <span data-ttu-id="4e19f-198">64.69</span><span class="sxs-lookup"><span data-stu-id="4e19f-198">64.69</span></span>                            | <span data-ttu-id="4e19f-199">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="4e19f-199">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="4e19f-200">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="4e19f-200">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="4e19f-201">1920x1080</span><span class="sxs-lookup"><span data-stu-id="4e19f-201">1920x1080</span></span> | <span data-ttu-id="4e19f-202">1920x1080</span><span class="sxs-lookup"><span data-stu-id="4e19f-202">1920x1080</span></span> | <span data-ttu-id="4e19f-203">1920x1080</span><span class="sxs-lookup"><span data-stu-id="4e19f-203">1920x1080</span></span> | <span data-ttu-id="4e19f-204">15、30</span><span class="sxs-lookup"><span data-stu-id="4e19f-204">15,30</span></span>       | <span data-ttu-id="4e19f-205">64.69</span><span class="sxs-lookup"><span data-stu-id="4e19f-205">64.69</span></span>                            | <span data-ttu-id="4e19f-206">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="4e19f-206">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="4e19f-207">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="4e19f-207">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="4e19f-208">1280x720</span><span class="sxs-lookup"><span data-stu-id="4e19f-208">1280x720</span></span>  | <span data-ttu-id="4e19f-209">1280x720</span><span class="sxs-lookup"><span data-stu-id="4e19f-209">1280x720</span></span>  | <span data-ttu-id="4e19f-210">1280x720</span><span class="sxs-lookup"><span data-stu-id="4e19f-210">1280x720</span></span>  | <span data-ttu-id="4e19f-211">15、30</span><span class="sxs-lookup"><span data-stu-id="4e19f-211">15,30</span></span>       | <span data-ttu-id="4e19f-212">64.69</span><span class="sxs-lookup"><span data-stu-id="4e19f-212">64.69</span></span>                            | <span data-ttu-id="4e19f-213">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="4e19f-213">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="4e19f-214">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="4e19f-214">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="4e19f-215">1128x636</span><span class="sxs-lookup"><span data-stu-id="4e19f-215">1128x636</span></span>  |           |           | <span data-ttu-id="4e19f-216">15、30</span><span class="sxs-lookup"><span data-stu-id="4e19f-216">15,30</span></span>       | <span data-ttu-id="4e19f-217">64.69</span><span class="sxs-lookup"><span data-stu-id="4e19f-217">64.69</span></span>                            | <span data-ttu-id="4e19f-218">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="4e19f-218">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="4e19f-219">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="4e19f-219">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="4e19f-220">960x540</span><span class="sxs-lookup"><span data-stu-id="4e19f-220">960x540</span></span>   |           |           | <span data-ttu-id="4e19f-221">15、30</span><span class="sxs-lookup"><span data-stu-id="4e19f-221">15,30</span></span>       | <span data-ttu-id="4e19f-222">64.69</span><span class="sxs-lookup"><span data-stu-id="4e19f-222">64.69</span></span>                            | <span data-ttu-id="4e19f-223">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="4e19f-223">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="4e19f-224">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="4e19f-224">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="4e19f-225">760x428</span><span class="sxs-lookup"><span data-stu-id="4e19f-225">760x428</span></span>   |           |           | <span data-ttu-id="4e19f-226">15、30</span><span class="sxs-lookup"><span data-stu-id="4e19f-226">15,30</span></span>       | <span data-ttu-id="4e19f-227">64.69</span><span class="sxs-lookup"><span data-stu-id="4e19f-227">64.69</span></span>                            | <span data-ttu-id="4e19f-228">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="4e19f-228">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="4e19f-229">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="4e19f-229">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="4e19f-230">640x360</span><span class="sxs-lookup"><span data-stu-id="4e19f-230">640x360</span></span>   |           |           | <span data-ttu-id="4e19f-231">15、30</span><span class="sxs-lookup"><span data-stu-id="4e19f-231">15,30</span></span>       | <span data-ttu-id="4e19f-232">64.69</span><span class="sxs-lookup"><span data-stu-id="4e19f-232">64.69</span></span>                            | <span data-ttu-id="4e19f-233">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="4e19f-233">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="4e19f-234">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="4e19f-234">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="4e19f-235">500x282</span><span class="sxs-lookup"><span data-stu-id="4e19f-235">500x282</span></span>   |           |           | <span data-ttu-id="4e19f-236">15、30</span><span class="sxs-lookup"><span data-stu-id="4e19f-236">15,30</span></span>       | <span data-ttu-id="4e19f-237">64.69</span><span class="sxs-lookup"><span data-stu-id="4e19f-237">64.69</span></span>                            | <span data-ttu-id="4e19f-238">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="4e19f-238">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="4e19f-239">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="4e19f-239">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="4e19f-240">424x240</span><span class="sxs-lookup"><span data-stu-id="4e19f-240">424x240</span></span>   |           |           | <span data-ttu-id="4e19f-241">15、30</span><span class="sxs-lookup"><span data-stu-id="4e19f-241">15,30</span></span>       | <span data-ttu-id="4e19f-242">64.69</span><span class="sxs-lookup"><span data-stu-id="4e19f-242">64.69</span></span>                            | <span data-ttu-id="4e19f-243">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="4e19f-243">Video conferencing, long duration scenarios</span></span> |

> [!NOTE]
> <span data-ttu-id="4e19f-244">客户可以利用 [混合现实捕获](/hololens/holographic-photos-and-videos) 来获取应用的视频或照片，其中包括全息影像和视频抖动。</span><span class="sxs-lookup"><span data-stu-id="4e19f-244">Customers can leverage [mixed reality capture](/hololens/holographic-photos-and-videos) to take videos or photos of your app, which include holograms and video stabilization.</span></span>
>
><span data-ttu-id="4e19f-245">作为开发人员，如果你希望在客户捕获内容时能够更好地显示你的应用程序，请考虑创建应用程序时应考虑的一些事项。</span><span class="sxs-lookup"><span data-stu-id="4e19f-245">As a developer, there are considerations you should take into account when creating your app if you want it to look as good as possible when a customer captures content.</span></span> <span data-ttu-id="4e19f-246">你还可以在应用中直接启用 (和自定义) 混合现实捕获。</span><span class="sxs-lookup"><span data-stu-id="4e19f-246">You can also enable (and customize) mixed reality capture from directly within your app.</span></span> <span data-ttu-id="4e19f-247">在 [混合现实捕获](mixed-reality-capture-for-developers.md)中了解更多开发人员。</span><span class="sxs-lookup"><span data-stu-id="4e19f-247">Learn more at [mixed reality capture for developers](mixed-reality-capture-for-developers.md).</span></span>

## <a name="locating-the-device-camera-in-the-world"></a><span data-ttu-id="4e19f-248">在世界各地查找设备照相机</span><span class="sxs-lookup"><span data-stu-id="4e19f-248">Locating the Device Camera in the World</span></span>

<span data-ttu-id="4e19f-249">当 HoloLens 拍摄照片和视频时，捕获的帧包括世界上相机的位置和照相机的镜头型号。</span><span class="sxs-lookup"><span data-stu-id="4e19f-249">When HoloLens takes photos and videos, the captured frames include the location of the camera in the world and the lens model of the camera.</span></span> <span data-ttu-id="4e19f-250">这样，应用程序就可以在现实世界中为补充式的图像处理方案提供有关相机位置的原因。</span><span class="sxs-lookup"><span data-stu-id="4e19f-250">This allows applications to reason about the position of the camera in the real world for augmented imaging scenarios.</span></span> <span data-ttu-id="4e19f-251">开发人员可以使用他们最喜爱的图像处理或自定义计算机视觉库，创造性地滚动自己的方案。</span><span class="sxs-lookup"><span data-stu-id="4e19f-251">Developers can creatively roll their own scenarios using their favorite image processing or custom computer vision libraries.</span></span>

<span data-ttu-id="4e19f-252">HoloLens 文档中其他地方的 "照相机" 可能指的是应用呈现) 的 (的 "虚拟游戏摄像机"。</span><span class="sxs-lookup"><span data-stu-id="4e19f-252">"Camera" elsewhere in HoloLens documentation may refer to the "virtual game camera" (the frustum the app renders to).</span></span> <span data-ttu-id="4e19f-253">除非另有指示，否则，此页上的 "照相机" 指的是实际的 RGB 颜色相机。</span><span class="sxs-lookup"><span data-stu-id="4e19f-253">Unless denoted otherwise, "camera" on this page refers to the real-world RGB color camera.</span></span>

### <a name="using-unity"></a><span data-ttu-id="4e19f-254">使用 Unity</span><span class="sxs-lookup"><span data-stu-id="4e19f-254">Using Unity</span></span>

<span data-ttu-id="4e19f-255">若要从 "CameraIntrinsics" 和 "CameraCoordinateSystem" 中转到应用程序/全球坐标系统，请按照 [Unity 中](../unity/locatable-camera-in-unity.md) 的可定位照相机一文中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="4e19f-255">To go from the 'CameraIntrinsics' and 'CameraCoordinateSystem' to your application/world coordinate system, follow the instructions in the [Locatable camera in Unity](../unity/locatable-camera-in-unity.md) article.</span></span>  <span data-ttu-id="4e19f-256">CameraToWorldMatrix 由 PhotoCaptureFrame 类自动提供，因此你无需担心下面讨论的 CameraCoordinateSystem 转换。</span><span class="sxs-lookup"><span data-stu-id="4e19f-256">CameraToWorldMatrix is automatically provided by PhotoCaptureFrame class, and so you don't need to worry about the CameraCoordinateSystem transforms discussed below.</span></span>

### <a name="using-mediaframereference"></a><span data-ttu-id="4e19f-257">使用 MediaFrameReference</span><span class="sxs-lookup"><span data-stu-id="4e19f-257">Using MediaFrameReference</span></span>

<span data-ttu-id="4e19f-258">如果 you'r 使用 [MediaFrameReference](//uwp/api/windows.media.capture.frames.mediaframereference) 类从照相机读取图像帧，则会应用这些说明。</span><span class="sxs-lookup"><span data-stu-id="4e19f-258">These instructions apply if you'r using the [MediaFrameReference](//uwp/api/windows.media.capture.frames.mediaframereference) class to read image frames from the camera.</span></span>

<span data-ttu-id="4e19f-259">每个图像帧都 (照片或视频) 在捕获时是否包括位于照相机的[SpatialCoordinateSystem](//uwp/api/windows.perception.spatial.spatialcoordinatesystem) ，可使用[MediaFrameReference](//uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)的[坐标系](//uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem)属性访问。</span><span class="sxs-lookup"><span data-stu-id="4e19f-259">Each image frame (whether photo or video) includes a [SpatialCoordinateSystem](//uwp/api/windows.perception.spatial.spatialcoordinatesystem) rooted at the camera at the time of capture, which can be accessed using the [CoordinateSystem](//uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) property of your [MediaFrameReference](//uwp/api/Windows.Media.Capture.Frames.MediaFrameReference).</span></span> <span data-ttu-id="4e19f-260">每个帧都包含对相机镜头型号的说明，可在 [CameraIntrinsics](//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 属性中找到。</span><span class="sxs-lookup"><span data-stu-id="4e19f-260">Each frame contains a description of the camera lens model, which can be found in the [CameraIntrinsics](//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) property.</span></span> <span data-ttu-id="4e19f-261">这些转换一起为每个像素定义了三维空间中的射线，表示生成像素的 photons 所采用的路径。</span><span class="sxs-lookup"><span data-stu-id="4e19f-261">Together, these transforms define for each pixel a ray in 3D space representing the path taken by the photons that produced the pixel.</span></span> <span data-ttu-id="4e19f-262">通过获取从帧的坐标系统到某个其他坐标 (系统的转换（例如，从 [固定的引用帧](../../design/coordinate-systems.md#stationary-frame-of-reference)) 进行转换，可以将这些光线与应用程序中的其他内容相关。</span><span class="sxs-lookup"><span data-stu-id="4e19f-262">These rays can be related to other content in the app by obtaining the transform from the frame's coordinate system to some other coordinate system (e.g. from a [stationary frame of reference](../../design/coordinate-systems.md#stationary-frame-of-reference)).</span></span> 

<span data-ttu-id="4e19f-263">每个图像框架提供以下内容：</span><span class="sxs-lookup"><span data-stu-id="4e19f-263">Each image frame provides the following:</span></span>
* <span data-ttu-id="4e19f-264">像素数据 (RGB/NV12/JPEG/等格式) </span><span class="sxs-lookup"><span data-stu-id="4e19f-264">Pixel Data (in RGB/NV12/JPEG/etc. format)</span></span>
* <span data-ttu-id="4e19f-265">捕获位置的[SpatialCoordinateSystem](//uwp/api/windows.perception.spatial.spatialcoordinatesystem)</span><span class="sxs-lookup"><span data-stu-id="4e19f-265">A [SpatialCoordinateSystem](//uwp/api/windows.perception.spatial.spatialcoordinatesystem) from the location of capture</span></span>
* <span data-ttu-id="4e19f-266">包含照相机镜头模式的 [CameraIntrinsics](//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 类</span><span class="sxs-lookup"><span data-stu-id="4e19f-266">A [CameraIntrinsics](//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) class containing the lens mode of the camera</span></span>

<span data-ttu-id="4e19f-267">[HolographicFaceTracking 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)演示了查询照相机坐标系统和自己的应用程序坐标系统之间的转换的相当直接的方法。</span><span class="sxs-lookup"><span data-stu-id="4e19f-267">The [HolographicFaceTracking sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) shows the fairly straightforward way to query for the transform between the camera's coordinate system and your own application coordinate systems.</span></span>

### <a name="using-media-foundation"></a><span data-ttu-id="4e19f-268">使用媒体基础</span><span class="sxs-lookup"><span data-stu-id="4e19f-268">Using Media Foundation</span></span>

<span data-ttu-id="4e19f-269">如果使用媒体基础直接从照相机读取图像帧，则可以使用每个帧的 [MFSampleExtension_CameraExtrinsics 属性](/windows/win32/medfound/mfsampleextension-cameraextrinsics) 和 [MFSampleExtension_PinholeCameraIntrinsics 特性](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) 来相对于应用程序的其他坐标系统定位相机帧，如下面的示例代码所示：</span><span class="sxs-lookup"><span data-stu-id="4e19f-269">If you are using Media Foundation directly to read image frames from the camera, you can use each frame's [MFSampleExtension_CameraExtrinsics attribute](/windows/win32/medfound/mfsampleextension-cameraextrinsics) and [MFSampleExtension_PinholeCameraIntrinsics attribute](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) to locate camera frames relative to your application's other coordinate systems, as shown in this sample code:</span></span>

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a><span data-ttu-id="4e19f-270">失真错误</span><span class="sxs-lookup"><span data-stu-id="4e19f-270">Distortion Error</span></span>

<span data-ttu-id="4e19f-271">在 HoloLens 上，视频和静态图像流在系统的图像处理管道中 undistorted，然后才能将帧提供给应用程序 (预览流包含) 的原始扭曲帧。</span><span class="sxs-lookup"><span data-stu-id="4e19f-271">On HoloLens, the video and still image streams are undistorted in the system's image-processing pipeline before the frames are made available to the application (the preview stream contains the original distorted frames).</span></span> <span data-ttu-id="4e19f-272">由于只有 CameraIntrinsics 可用，因此应用程序必须假定图像帧表示完美的 pinhole 相机。</span><span class="sxs-lookup"><span data-stu-id="4e19f-272">Because only the CameraIntrinsics are made available, applications must assume image frames represent a perfect pinhole camera.</span></span>

<span data-ttu-id="4e19f-273">在 HoloLens (第一代) 上，在帧元数据中使用 CameraIntrinsics 时，图像处理器中的 undistortion 函数可能仍会导致最多10个像素的错误。</span><span class="sxs-lookup"><span data-stu-id="4e19f-273">On HoloLens (first-generation), the undistortion function in the image processor may still leave an error of up to 10 pixels when using the CameraIntrinsics in the frame metadata.</span></span> <span data-ttu-id="4e19f-274">在许多用例中，此错误并不重要，但如果将全息影像与真实的海报/标记对齐，则会注意到 <10-px 的偏移量 (约为2米离开) 的全息影像的 11 mm，这可能导致此扭曲错误。</span><span class="sxs-lookup"><span data-stu-id="4e19f-274">In many use cases, this error won't matter, but if you're aligning holograms to real world posters/markers, for example, and you notice a <10-px offset (roughly 11 mm for holograms positioned 2 meters away), this distortion error could be the cause.</span></span> 

## <a name="locatable-camera-usage-scenarios"></a><span data-ttu-id="4e19f-275">定位照相机使用方案</span><span class="sxs-lookup"><span data-stu-id="4e19f-275">Locatable Camera Usage Scenarios</span></span>

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a><span data-ttu-id="4e19f-276">在捕获照片或视频的世界中显示照片或视频</span><span class="sxs-lookup"><span data-stu-id="4e19f-276">Show a photo or video in the world where it was captured</span></span>

<span data-ttu-id="4e19f-277">设备照相机帧附带了 "相机到世界" 转换，可用于显示在拍摄映像时设备的确切位置。</span><span class="sxs-lookup"><span data-stu-id="4e19f-277">The Device Camera frames come with a "Camera To World" transform, that can be used to show exactly where the device was when the image was taken.</span></span> <span data-ttu-id="4e19f-278">例如，你可以将一个小全息图标放在此位置 (MultiplyPoint (System.numerics.vector2) # A3，甚至在相机的方向上绘制一个小箭头 (CameraToWorld (MultiplyVector) # A7。</span><span class="sxs-lookup"><span data-stu-id="4e19f-278">For example, you could position a small holographic icon at this location (CameraToWorld.MultiplyPoint(Vector3.zero)) and even draw a little arrow in the direction that the camera was facing (CameraToWorld.MultiplyVector(Vector3.forward)).</span></span>

### <a name="tag--pattern--poster--object-tracking"></a><span data-ttu-id="4e19f-279">标记/模式/海报/对象跟踪</span><span class="sxs-lookup"><span data-stu-id="4e19f-279">Tag / Pattern / Poster / Object Tracking</span></span>

<span data-ttu-id="4e19f-280">许多混合现实应用程序使用可识别的图像或视觉模式在空间中创建以可跟踪点。</span><span class="sxs-lookup"><span data-stu-id="4e19f-280">Many mixed reality applications use a recognizable image or visual pattern to create a trackable point in space.</span></span> <span data-ttu-id="4e19f-281">然后，使用该对象相对于该点呈现对象，或创建一个已知位置。</span><span class="sxs-lookup"><span data-stu-id="4e19f-281">This is then used to render objects relative to that point or create a known location.</span></span> <span data-ttu-id="4e19f-282">某些情况下，HoloLens 包括查找标有 fiducials 的现实世界对象 (例如，带有 QR 码的电视显示器) ，将全息影像置于 fiducials 上，并与已设置为通过 Wi-fi 与 HoloLens 通信的非 HoloLens 设备直观配对。</span><span class="sxs-lookup"><span data-stu-id="4e19f-282">Some uses for HoloLens include finding a real world object tagged with fiducials (e.g. a TV monitor with a QR code), placing holograms over fiducials, and visually pairing with non-HoloLens devices like tablets that have been set up to communicate with HoloLens via Wi-Fi.</span></span>

<span data-ttu-id="4e19f-283">你需要几个事项来识别视觉对象模式，并将对象放置在应用程序世界空间中：</span><span class="sxs-lookup"><span data-stu-id="4e19f-283">You'll need a few things to recognize a visual pattern and place an object in the applications world space:</span></span>
1. <span data-ttu-id="4e19f-284">图像模式识别工具包，如 QR 码、AR 标记、面部查找器、圆形跟踪器、OCR 等。</span><span class="sxs-lookup"><span data-stu-id="4e19f-284">An image pattern recognition toolkit, such as QR code, AR tags, face finder, circle trackers, OCR etc.</span></span>
2. <span data-ttu-id="4e19f-285">在运行时收集图像帧，并将其传递到识别层</span><span class="sxs-lookup"><span data-stu-id="4e19f-285">Collect image frames at runtime, and pass them to the recognition layer</span></span>
3. <span data-ttu-id="4e19f-286">将其图像位置 Unproject 为世界位置，或可能是世界光线。</span><span class="sxs-lookup"><span data-stu-id="4e19f-286">Unproject their image locations back into world positions, or likely world rays.</span></span> 
4. <span data-ttu-id="4e19f-287">将虚拟模型放置在这些世界位置</span><span class="sxs-lookup"><span data-stu-id="4e19f-287">Position your virtual models over these world locations</span></span>

<span data-ttu-id="4e19f-288">一些重要的图像处理链接：</span><span class="sxs-lookup"><span data-stu-id="4e19f-288">Some important image-processing links:</span></span>
* [<span data-ttu-id="4e19f-289">OpenCV</span><span class="sxs-lookup"><span data-stu-id="4e19f-289">OpenCV</span></span>](https://opencv.org/)
* [<span data-ttu-id="4e19f-290">QR 标记</span><span class="sxs-lookup"><span data-stu-id="4e19f-290">QR Tags</span></span>](https://en.wikipedia.org/wiki/QR_code)
* [<span data-ttu-id="4e19f-291">FaceSDK</span><span class="sxs-lookup"><span data-stu-id="4e19f-291">FaceSDK</span></span>](https://research.microsoft.com/projects/facesdk/)
* [<span data-ttu-id="4e19f-292">Microsoft Translator</span><span class="sxs-lookup"><span data-stu-id="4e19f-292">Microsoft Translator</span></span>](https://www.microsoft.com/translator/business)

<span data-ttu-id="4e19f-293">保持交互应用程序帧速率非常重要，尤其是在处理长时间运行的图像识别算法时。</span><span class="sxs-lookup"><span data-stu-id="4e19f-293">Keeping an interactive application frame-rate is critical, especially when dealing with long-running image recognition algorithms.</span></span> <span data-ttu-id="4e19f-294">出于此原因，我们通常使用以下模式：</span><span class="sxs-lookup"><span data-stu-id="4e19f-294">For this reason, we commonly use the following pattern:</span></span>
1. <span data-ttu-id="4e19f-295">主线程：管理照相机对象</span><span class="sxs-lookup"><span data-stu-id="4e19f-295">Main Thread: manages the camera object</span></span>
2. <span data-ttu-id="4e19f-296">主线程： (async) 请求新帧</span><span class="sxs-lookup"><span data-stu-id="4e19f-296">Main Thread: requests new frames (async)</span></span>
3. <span data-ttu-id="4e19f-297">主线程：将新帧传递到跟踪线程</span><span class="sxs-lookup"><span data-stu-id="4e19f-297">Main Thread: pass new frames to tracking thread</span></span>
4. <span data-ttu-id="4e19f-298">跟踪线程：处理收集关键点的图像</span><span class="sxs-lookup"><span data-stu-id="4e19f-298">Tracking Thread: processes image to collect key points</span></span>
5. <span data-ttu-id="4e19f-299">主线程：移动虚拟模型以匹配找到的关键点</span><span class="sxs-lookup"><span data-stu-id="4e19f-299">Main Thread: moves virtual model to match found key points</span></span>
6. <span data-ttu-id="4e19f-300">主线程：从步骤2重复</span><span class="sxs-lookup"><span data-stu-id="4e19f-300">Main Thread: repeat from step 2</span></span>

<span data-ttu-id="4e19f-301">某些图像标记系统仅提供单个像素位置 (其他部分提供完全转换，在这种情况下，不需要此部分) ，这相当于可能的位置。</span><span class="sxs-lookup"><span data-stu-id="4e19f-301">Some image marker systems only provide a single pixel location (others provide the full transform in which case this section won't be needed), which equates to a ray of possible locations.</span></span> <span data-ttu-id="4e19f-302">若要访问单个3d 位置，我们可以利用多个射线，并按大致交集查找最终结果。</span><span class="sxs-lookup"><span data-stu-id="4e19f-302">To get to a single 3d location, we can then leverage multiple rays and find the final result by their approximate intersection.</span></span> <span data-ttu-id="4e19f-303">为此需要：</span><span class="sxs-lookup"><span data-stu-id="4e19f-303">To do this, you'll need to:</span></span>
1. <span data-ttu-id="4e19f-304">获取正在收集多个照相机图像的循环</span><span class="sxs-lookup"><span data-stu-id="4e19f-304">Get a loop going collecting multiple camera images</span></span>
2. <span data-ttu-id="4e19f-305">查找关联的功能点及其世界光线</span><span class="sxs-lookup"><span data-stu-id="4e19f-305">Find the associated feature points, and their world rays</span></span>
3. <span data-ttu-id="4e19f-306">如果有一个功能字典，每个功能都有多个世界光线，则可以使用以下代码来解决这些光线的交集：</span><span class="sxs-lookup"><span data-stu-id="4e19f-306">When you have a dictionary of features, each with multiple world rays, you can use the following code to solve for the intersection of those rays:</span></span>

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

<span data-ttu-id="4e19f-307">如果有两个或多个跟踪的标记位置，则可以将建模的场景定位到适合用户的当前方案。</span><span class="sxs-lookup"><span data-stu-id="4e19f-307">Given two or more tracked tag locations, you can position a modeled scene to fit the user's current scenario.</span></span> <span data-ttu-id="4e19f-308">如果无法假定重心，则需要三个标记位置。</span><span class="sxs-lookup"><span data-stu-id="4e19f-308">If you can't assume gravity, then you'll need three tag locations.</span></span> <span data-ttu-id="4e19f-309">在许多情况下，我们使用颜色方案，其中白色球体表示实时跟踪标记位置，蓝色球体表示建模标记位置。</span><span class="sxs-lookup"><span data-stu-id="4e19f-309">In many cases, we use a color scheme where white spheres represent real-time tracked tag locations, and blue spheres represent modeled tag locations.</span></span> <span data-ttu-id="4e19f-310">这允许用户以直观方式衡量对齐质量。</span><span class="sxs-lookup"><span data-stu-id="4e19f-310">This allows the user to visually gauge the alignment quality.</span></span> <span data-ttu-id="4e19f-311">我们假定在所有应用程序中都进行以下设置：</span><span class="sxs-lookup"><span data-stu-id="4e19f-311">We assume the following setup in all our applications:</span></span>
* <span data-ttu-id="4e19f-312">两个或更多模型标记位置</span><span class="sxs-lookup"><span data-stu-id="4e19f-312">Two or more modeled tag locations</span></span>
* <span data-ttu-id="4e19f-313">一个 "校准空间"，场景是标记的父项</span><span class="sxs-lookup"><span data-stu-id="4e19f-313">One 'calibration space', which in the scene is the parent of the tags</span></span>
* <span data-ttu-id="4e19f-314">相机功能标识符</span><span class="sxs-lookup"><span data-stu-id="4e19f-314">Camera feature identifier</span></span>
* <span data-ttu-id="4e19f-315">行为，这会移动校准空间，以使模型标记与实时标记对齐 (建议移动父空间，而不是模型标记本身，因为其他连接是相对于它们) 的位置。</span><span class="sxs-lookup"><span data-stu-id="4e19f-315">Behavior, which moves the calibration space to align the modeled tags with the real-time tags (we're careful to move the parent space, not the modeled markers themselves, because other connect is positions relative to them).</span></span>

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a><span data-ttu-id="4e19f-316">使用 Led 或其他识别器库跟踪或确定标记为静止或移动现实世界对象/面部</span><span class="sxs-lookup"><span data-stu-id="4e19f-316">Track or Identify Tagged Stationary or Moving real-world objects/faces using LEDs or other recognizer libraries</span></span>

<span data-ttu-id="4e19f-317">示例:</span><span class="sxs-lookup"><span data-stu-id="4e19f-317">Examples:</span></span>
* <span data-ttu-id="4e19f-318">工业机器人，其中包含 Led (或用于速度缓慢移动对象的 QR 码) </span><span class="sxs-lookup"><span data-stu-id="4e19f-318">Industrial robots with LEDs (or QR codes for slower moving objects)</span></span>
* <span data-ttu-id="4e19f-319">标识并识别房间中的对象</span><span class="sxs-lookup"><span data-stu-id="4e19f-319">Identify and recognize objects in the room</span></span>
* <span data-ttu-id="4e19f-320">标识并识别房间中的人员，例如，将全息联系人卡片置于面部上</span><span class="sxs-lookup"><span data-stu-id="4e19f-320">Identify and recognize people in the room, for example placing holographic contact cards over faces</span></span>

## <a name="see-also"></a><span data-ttu-id="4e19f-321">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4e19f-321">See also</span></span>
* [<span data-ttu-id="4e19f-322">定位相机示例</span><span class="sxs-lookup"><span data-stu-id="4e19f-322">Locatable camera sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [<span data-ttu-id="4e19f-323">Unity 中的可定位相机</span><span class="sxs-lookup"><span data-stu-id="4e19f-323">Locatable camera in Unity</span></span>](../unity/locatable-camera-in-unity.md)
* [<span data-ttu-id="4e19f-324">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="4e19f-324">Mixed reality capture</span></span>](/hololens/holographic-photos-and-videos)
* [<span data-ttu-id="4e19f-325">面向开发人员的混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="4e19f-325">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="4e19f-326">媒体捕获简介</span><span class="sxs-lookup"><span data-stu-id="4e19f-326">Media capture introduction</span></span>](/windows/uwp/audio-video-camera/)
* [<span data-ttu-id="4e19f-327">全息面部跟踪示例</span><span class="sxs-lookup"><span data-stu-id="4e19f-327">Holographic face tracking sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)