---
title: 将视频中的音频空间化
description: 了解如何将视频资产导入到 Unity 混合现实项目，并从视频 spatialize 音频。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality，unity，教程，hololens2，空间音频，MRTK，混合现实工具包，UWP，Windows 10，HRTF，头相关传输函数，回音，Microsoft Spatializer，视频导入，视频播放器
ms.openlocfilehash: 211d1e32a8137444d0f33d442a60067dcd77ca36
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007408"
---
# <a name="spatializing-audio-from-a-video"></a><span data-ttu-id="07770-104">将视频中的音频空间化</span><span class="sxs-lookup"><span data-stu-id="07770-104">Spatializing audio from a video</span></span>

<span data-ttu-id="07770-105">在 HoloLens 2 Unity 教程的 "空间音频" 模块的第三章中，你将：</span><span class="sxs-lookup"><span data-stu-id="07770-105">In this 3rd chapter of the spatial audio module of the HoloLens 2 Unity tutorials, you'll:</span></span>
* <span data-ttu-id="07770-106">导入视频并添加视频播放器</span><span class="sxs-lookup"><span data-stu-id="07770-106">Import a video and add a Video Player</span></span>
* <span data-ttu-id="07770-107">播放视频到 quadrangle</span><span class="sxs-lookup"><span data-stu-id="07770-107">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="07770-108">将音频从视频路由到 quadrangle，并 spatialize 音频</span><span class="sxs-lookup"><span data-stu-id="07770-108">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player"></a><span data-ttu-id="07770-109">导入视频并添加视频播放器</span><span class="sxs-lookup"><span data-stu-id="07770-109">Import a video and add a Video Player</span></span>

<span data-ttu-id="07770-110">将视频文件拖到 Unity 项目的 " **项目** " 窗格中。</span><span class="sxs-lookup"><span data-stu-id="07770-110">Drag a video file into the **Project** pane in your Unity project.</span></span> <span data-ttu-id="07770-111">可以从空间音频示例项目使用 [此视频](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) 。</span><span class="sxs-lookup"><span data-stu-id="07770-111">You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

![包含视频的资产文件夹](images/spatial-audio/assets-folder-with-video.png)

<span data-ttu-id="07770-113">调整视频剪辑的质量设置可以确保在 HoloLens 2 上顺畅地播放。</span><span class="sxs-lookup"><span data-stu-id="07770-113">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="07770-114">单击 " **项目** " 窗格中的视频文件。</span><span class="sxs-lookup"><span data-stu-id="07770-114">Click on the video file in the **Project** pane.</span></span> <span data-ttu-id="07770-115">然后在视频文件的 " **检查器** " 窗格中，覆盖 Windows 应用商店应用的设置，并执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="07770-115">Then in the **Inspector** pane for the video file, override the settings for Windows Store Apps, and:</span></span>
* <span data-ttu-id="07770-116">启用 **转码**</span><span class="sxs-lookup"><span data-stu-id="07770-116">Enable **Transcode**</span></span>
* <span data-ttu-id="07770-117">将 **编解码器** 设置为 H264</span><span class="sxs-lookup"><span data-stu-id="07770-117">Set **Codec** to H264</span></span>
* <span data-ttu-id="07770-118">将 **比特率模式** 设置为低</span><span class="sxs-lookup"><span data-stu-id="07770-118">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="07770-119">将 **空间质量** 设置为中等空间质量</span><span class="sxs-lookup"><span data-stu-id="07770-119">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="07770-120">完成这些调整后，视频文件的 " **检查器** " 窗格将如下所示：</span><span class="sxs-lookup"><span data-stu-id="07770-120">After these adjustments, the **Inspector** pane for the video file will look like this:</span></span>

![视频属性窗格](images/spatial-audio/video-property-pane.png)

<span data-ttu-id="07770-122">接下来 **，通过右键单击 "** **层次结构**" 窗格并选择 "**视频 > 视频播放器**： </span><span class="sxs-lookup"><span data-stu-id="07770-122">Next, add a **Video Player** object to the **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **Video -> Video Player**:</span></span>

![层次结构中的视频播放器](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="07770-124">播放视频到 quadrangle</span><span class="sxs-lookup"><span data-stu-id="07770-124">Play video onto a quadrangle</span></span>

<span data-ttu-id="07770-125">**视频播放器** 对象需要一个纹理游戏对象用于呈现视频。</span><span class="sxs-lookup"><span data-stu-id="07770-125">The **Video Player** object needs a textured game object on which to render the video.</span></span> <span data-ttu-id="07770-126">首先 **，通过** 右键单击 "**层次结构**" 窗格并选择 " **3d 对象-> 四个**：</span><span class="sxs-lookup"><span data-stu-id="07770-126">First, add a **Quad** to your **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **3D Object -> Quad**:</span></span>

![向层次结构添加四个](images/spatial-audio/add-quad-to-hierarchy.png)

<span data-ttu-id="07770-128">若要确保在应用程序启动时 **四个四** 个显示在用户前面，请将 **4** 的 "**位置**" 属性设置为 (0，0，2) ，并将 "**小数位数**" 属性设置为 (1.28，0.72，1) 。</span><span class="sxs-lookup"><span data-stu-id="07770-128">To ensure the **Quad** appears in front of the user when the application starts, set the **Position** property of the **Quad** to (0, 0, 2), and the **Scale** property to (1.28, 0.72, 1).</span></span> <span data-ttu-id="07770-129">进行这些更改后，**四** 个 "**检查器**" 窗格中的 "**转换**" 组件将如下所示：</span><span class="sxs-lookup"><span data-stu-id="07770-129">After these changes, the **Transform** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![四向转换](images/spatial-audio/quad-transform.png)

<span data-ttu-id="07770-131">若要为 **四** 个视频着色，请创建新的 **渲染纹理**。</span><span class="sxs-lookup"><span data-stu-id="07770-131">To texture the **Quad** with video, create a new **Render Texture**.</span></span> <span data-ttu-id="07770-132">在 " **项目** " 窗格中，右键单击并选择 " **创建-> 渲染纹理**"：</span><span class="sxs-lookup"><span data-stu-id="07770-132">In the **Project** pane, right-click and choose **Create -> Render Texture**:</span></span>

![创建着色纹理](images/spatial-audio/create-render-texture.png)

<span data-ttu-id="07770-134">在 **呈现纹理** 的 "**检查器**" 窗格中，将 " **Size** " 属性设置为与视频的 "1280x720 的本机分辨率" 匹配。</span><span class="sxs-lookup"><span data-stu-id="07770-134">On the **Inspector** pane of the **Render Texture**, set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="07770-135">然后，若要确保在 HoloLens 2 上呈现良好的性能，请将 **深度缓冲区** 属性设置为 **至少16位深度**。</span><span class="sxs-lookup"><span data-stu-id="07770-135">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span> <span data-ttu-id="07770-136">这些设置之后，**呈现纹理** 的 "**检查器**" 窗格将如下所示：</span><span class="sxs-lookup"><span data-stu-id="07770-136">After these settings, the **Inspector** pane for the **Render Texture** will look like this:</span></span>

![呈现纹理属性](images/spatial-audio/render-texture-properties.png)

<span data-ttu-id="07770-138">接下来，使用新的 **呈现纹理** 作为 **四** 个的纹理：</span><span class="sxs-lookup"><span data-stu-id="07770-138">Next, use your new **Render Texture** as the texture for the **Quad**:</span></span>
1. <span data-ttu-id="07770-139">将 **呈现纹理** 从 "**项目**" 窗格拖到 **层次结构** 中的 **四** 个</span><span class="sxs-lookup"><span data-stu-id="07770-139">Drag the **Render Texture** from the **Project** pane onto the **Quad** in the **Hierarchy**</span></span>
2. <span data-ttu-id="07770-140">若要在 HoloLens 2 上确保良好的性能，请在 "**四** 个 **检查器**" 窗格中选择 **混合现实工具包标准着色器**。</span><span class="sxs-lookup"><span data-stu-id="07770-140">To ensure good performance on HoloLens 2, on the **Inspector** pane for the **Quad**, select the **Mixed Reality Toolkit Standard Shader**.</span></span>

<span data-ttu-id="07770-141">在这些设置中，**四** 个 "**检查器**" 窗格中的 **纹理** 组件如下所示：</span><span class="sxs-lookup"><span data-stu-id="07770-141">With these settings, the **Texture** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![四纹理属性](images/spatial-audio/quad-texture-properties.png)

<span data-ttu-id="07770-143">若要设置新的 **视频播放器** 并 **渲染纹理** 以播放视频剪辑，请打开 **视频播放器** 的 "**检查器**" 窗格，并执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="07770-143">To set your new **Video Player** and **Render Texture** to play your video clip, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="07770-144">将 **视频剪辑** 属性设置为视频文件</span><span class="sxs-lookup"><span data-stu-id="07770-144">Set the **Video Clip** property to your video file</span></span>
* <span data-ttu-id="07770-145">选中 " **循环** " 复选框</span><span class="sxs-lookup"><span data-stu-id="07770-145">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="07770-146">将 **目标纹理** 设置为新的渲染纹理</span><span class="sxs-lookup"><span data-stu-id="07770-146">Set **Target Texture** to your new render texture</span></span>

<span data-ttu-id="07770-147">**视频播放器** 的 "**检查器**" 窗格现在将如下所示：</span><span class="sxs-lookup"><span data-stu-id="07770-147">The **Inspector** pane for the **Video Player** will now look like this:</span></span>

![视频播放器属性](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="07770-149">Spatialize 视频中的音频</span><span class="sxs-lookup"><span data-stu-id="07770-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="07770-150">在 **四** 个 "**检查器**" 窗格中，创建要将音频从视频路由到的 **音频源**：</span><span class="sxs-lookup"><span data-stu-id="07770-150">In the **Inspector** pane for the **Quad**, create an **Audio Source** to which you'll route the audio from the video:</span></span>
* <span data-ttu-id="07770-151">单击窗格底部的 " **添加组件** "</span><span class="sxs-lookup"><span data-stu-id="07770-151">Click **Add Component** at the bottom of the pane</span></span>
* <span data-ttu-id="07770-152">添加 **音频源**</span><span class="sxs-lookup"><span data-stu-id="07770-152">Add an **Audio Source**</span></span>

<span data-ttu-id="07770-153">然后，在 " **音频源**：</span><span class="sxs-lookup"><span data-stu-id="07770-153">Then, on the **Audio Source**:</span></span>
* <span data-ttu-id="07770-154">将 **输出** 设置为混音器</span><span class="sxs-lookup"><span data-stu-id="07770-154">Set **Output** to your mixer</span></span>
* <span data-ttu-id="07770-155">选中 " **Spatialize** " 框</span><span class="sxs-lookup"><span data-stu-id="07770-155">Check the **Spatialize** box</span></span>
* <span data-ttu-id="07770-156">将 **空间混合** 滑块移动到 1 (3d) </span><span class="sxs-lookup"><span data-stu-id="07770-156">Move the **Spatial Blend** slider to 1 (3D)</span></span>

<span data-ttu-id="07770-157">进行这些更改后，**四** 个 "**检查器**" 窗格中的 "**音频源**" 组件会如下所示：</span><span class="sxs-lookup"><span data-stu-id="07770-157">After these changes, the **Audio Source** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![四核音频源检查器](images/spatial-audio/quad-audio-source-inspector.png)

<span data-ttu-id="07770-159">若要将 **视频播放器** 设置为将音频源路由到 **四** 个视频 **源**，请打开 **视频播放器** 的 **检查器** 窗格，并执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="07770-159">To set the **Video Player** to route its audio to the **Audio Source** on the **Quad**, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="07770-160">将 **音频输出模式** 设置为 "音频源"</span><span class="sxs-lookup"><span data-stu-id="07770-160">Set the **Audio Output Mode** to 'Audio Source'</span></span>
* <span data-ttu-id="07770-161">将 " **音频源** " 属性设置为四</span><span class="sxs-lookup"><span data-stu-id="07770-161">Set the **Audio Source** property to your Quad</span></span>

<span data-ttu-id="07770-162">进行这些更改后，**视频播放器** 的 "**检查器**" 窗格将如下所示：</span><span class="sxs-lookup"><span data-stu-id="07770-162">After these changes, the **Inspector** pane for the **Video Player** will look like this:</span></span>

![视频播放器设置音频源](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a><span data-ttu-id="07770-164">后续步骤</span><span class="sxs-lookup"><span data-stu-id="07770-164">Next steps</span></span>

<span data-ttu-id="07770-165">在 HoloLens 2 上或在 Unity 编辑器中试用你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="07770-165">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="07770-166">你将看到并听到视频，视频中的音频将为 spatialized。</span><span class="sxs-lookup"><span data-stu-id="07770-166">You'll see and hear the video, and the audio from the video will be spatialized.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07770-167">第4章</span><span class="sxs-lookup"><span data-stu-id="07770-167">Chapter 4</span></span>](unity-spatial-audio-ch4.md) 

