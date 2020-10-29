---
title: 空间音频教程-3。 将视频中的音频空间化
description: 将视频资产导入到 Unity 项目，并 spatialize 视频中的音频。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 混合现实、unity、教程、hololens2、空间音频
ms.openlocfilehash: cd684944bdd618dcf435ef91566d6d4f18aa87a3
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91678577"
---
# <a name="spatializing-audio-from-a-video"></a><span data-ttu-id="a9c99-105">将视频中的音频空间化</span><span class="sxs-lookup"><span data-stu-id="a9c99-105">Spatializing audio from a video</span></span>
<span data-ttu-id="a9c99-106">在 HoloLens 2 Unity 教程的 "空间音频" 模块的第三章中，你将：</span><span class="sxs-lookup"><span data-stu-id="a9c99-106">In this 3rd chapter of the spatial audio module of the HoloLens 2 Unity tutorials, you'll:</span></span>
* <span data-ttu-id="a9c99-107">导入视频并添加视频播放器</span><span class="sxs-lookup"><span data-stu-id="a9c99-107">Import a video and add a Video Player</span></span>
* <span data-ttu-id="a9c99-108">播放视频到 quadrangle</span><span class="sxs-lookup"><span data-stu-id="a9c99-108">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="a9c99-109">将音频从视频路由到 quadrangle，并 spatialize 音频</span><span class="sxs-lookup"><span data-stu-id="a9c99-109">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player"></a><span data-ttu-id="a9c99-110">导入视频并添加视频播放器</span><span class="sxs-lookup"><span data-stu-id="a9c99-110">Import a video and add a Video Player</span></span>

<span data-ttu-id="a9c99-111">将视频文件拖到 Unity 项目的 " **项目** " 窗格中。</span><span class="sxs-lookup"><span data-stu-id="a9c99-111">Drag a video file into the **Project** pane in your Unity project.</span></span> <span data-ttu-id="a9c99-112">可以从空间音频示例项目使用 [此视频](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) 。</span><span class="sxs-lookup"><span data-stu-id="a9c99-112">You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

![包含视频的资产文件夹](images/spatial-audio/assets-folder-with-video.png)

<span data-ttu-id="a9c99-114">调整视频剪辑的质量设置可以确保在 HoloLens 2 上顺畅地播放。</span><span class="sxs-lookup"><span data-stu-id="a9c99-114">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="a9c99-115">单击 " **项目** " 窗格中的视频文件。</span><span class="sxs-lookup"><span data-stu-id="a9c99-115">Click on the video file in the **Project** pane.</span></span> <span data-ttu-id="a9c99-116">然后在视频文件的 " **检查器** " 窗格中，覆盖 Windows 应用商店应用的设置，并执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a9c99-116">Then in the **Inspector** pane for the video file, override the settings for Windows Store Apps, and:</span></span>
* <span data-ttu-id="a9c99-117">启用 **转码**</span><span class="sxs-lookup"><span data-stu-id="a9c99-117">Enable **Transcode**</span></span>
* <span data-ttu-id="a9c99-118">将 **编解码器** 设置为 H264</span><span class="sxs-lookup"><span data-stu-id="a9c99-118">Set **Codec** to H264</span></span>
* <span data-ttu-id="a9c99-119">将 **比特率模式** 设置为低</span><span class="sxs-lookup"><span data-stu-id="a9c99-119">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="a9c99-120">将 **空间质量** 设置为中等空间质量</span><span class="sxs-lookup"><span data-stu-id="a9c99-120">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="a9c99-121">完成这些调整后，视频文件的 " **检查器** " 窗格将如下所示：</span><span class="sxs-lookup"><span data-stu-id="a9c99-121">After these adjustments, the **Inspector** pane for the video file will look like this:</span></span>

![视频属性窗格](images/spatial-audio/video-property-pane.png)

<span data-ttu-id="a9c99-123">接下来 **，通过右键单击 "** **层次结构** " 窗格并选择 " **视频 > 视频播放器** ： **Video Player**</span><span class="sxs-lookup"><span data-stu-id="a9c99-123">Next, add a **Video Player** object to the **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **Video -> Video Player** :</span></span>

![层次结构中的视频播放器](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="a9c99-125">播放视频到 quadrangle</span><span class="sxs-lookup"><span data-stu-id="a9c99-125">Play video onto a quadrangle</span></span>
<span data-ttu-id="a9c99-126">**视频播放器** 对象需要一个纹理游戏对象用于呈现视频。</span><span class="sxs-lookup"><span data-stu-id="a9c99-126">The **Video Player** object needs a textured game object on which to render the video.</span></span> <span data-ttu-id="a9c99-127">首先 **，通过** 右键 **Quad** 单击 " **层次结构** " 窗格并选择 " **3d 对象-> 四个** ：</span><span class="sxs-lookup"><span data-stu-id="a9c99-127">First, add a **Quad** to your **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **3D Object -> Quad** :</span></span>

![向层次结构添加四个](images/spatial-audio/add-quad-to-hierarchy.png)

<span data-ttu-id="a9c99-129">若要确保在应用程序启动时 **四个四** 个显示在用户前面，请将 **4** 的 " **位置** " 属性设置为 (0，0，2) ，并将 " **小数位数** " 属性设置为 (1.28，0.72，1) 。</span><span class="sxs-lookup"><span data-stu-id="a9c99-129">To ensure the **Quad** appears in front of the user when the application starts, set the **Position** property of the **Quad** to (0, 0, 2), and the **Scale** property to (1.28, 0.72, 1).</span></span> <span data-ttu-id="a9c99-130">进行这些更改后， **四** 个 " **检查器** " 窗格中的 " **转换** " 组件将如下所示：</span><span class="sxs-lookup"><span data-stu-id="a9c99-130">After these changes, the **Transform** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![四向转换](images/spatial-audio/quad-transform.png)

<span data-ttu-id="a9c99-132">若要为 **四** 个视频着色，请创建新的 **渲染纹理** 。</span><span class="sxs-lookup"><span data-stu-id="a9c99-132">To texture the **Quad** with video, create a new **Render Texture** .</span></span> <span data-ttu-id="a9c99-133">在 " **项目** " 窗格中，右键单击并选择 " **创建-> 渲染纹理** "：</span><span class="sxs-lookup"><span data-stu-id="a9c99-133">In the **Project** pane, right-click and choose **Create -> Render Texture** :</span></span>

![创建着色纹理](images/spatial-audio/create-render-texture.png)

<span data-ttu-id="a9c99-135">在 **呈现纹理** 的 " **检查器** " 窗格中，将 " **Size** " 属性设置为与视频的 "1280x720 的本机分辨率" 匹配。</span><span class="sxs-lookup"><span data-stu-id="a9c99-135">On the **Inspector** pane of the **Render Texture** , set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="a9c99-136">然后，若要确保在 HoloLens 2 上呈现良好的性能，请将 **深度缓冲区** 属性设置为 **至少16位深度** 。</span><span class="sxs-lookup"><span data-stu-id="a9c99-136">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth** .</span></span> <span data-ttu-id="a9c99-137">这些设置之后， **呈现纹理** 的 " **检查器** " 窗格将如下所示：</span><span class="sxs-lookup"><span data-stu-id="a9c99-137">After these settings, the **Inspector** pane for the **Render Texture** will look like this:</span></span>

![呈现纹理属性](images/spatial-audio/render-texture-properties.png)

<span data-ttu-id="a9c99-139">接下来，使用新的 **呈现纹理** 作为 **四** 个的纹理：</span><span class="sxs-lookup"><span data-stu-id="a9c99-139">Next, use your new **Render Texture** as the texture for the **Quad** :</span></span>
1. <span data-ttu-id="a9c99-140">将 **呈现纹理** 从 " **项目** " 窗格拖到 **层次结构** 中的 **四** 个</span><span class="sxs-lookup"><span data-stu-id="a9c99-140">Drag the **Render Texture** from the **Project** pane onto the **Quad** in the **Hierarchy**</span></span>
2. <span data-ttu-id="a9c99-141">若要在 HoloLens 2 上确保良好的性能，请在 " **四** 个 **检查器** " 窗格中选择 **混合现实工具包标准着色器** 。</span><span class="sxs-lookup"><span data-stu-id="a9c99-141">To ensure good performance on HoloLens 2, on the **Inspector** pane for the **Quad** , select the **Mixed Reality Toolkit Standard Shader** .</span></span>

<span data-ttu-id="a9c99-142">在这些设置中， **四** 个 " **检查器** " 窗格中的 **纹理** 组件如下所示：</span><span class="sxs-lookup"><span data-stu-id="a9c99-142">With these settings, the **Texture** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![四纹理属性](images/spatial-audio/quad-texture-properties.png)

<span data-ttu-id="a9c99-144">若要设置新的 **视频播放器** 并 **渲染纹理** 以播放视频剪辑，请打开 **视频播放器** 的 " **检查器** " 窗格，并执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a9c99-144">To set your new **Video Player** and **Render Texture** to play your video clip, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="a9c99-145">将 **视频剪辑** 属性设置为视频文件</span><span class="sxs-lookup"><span data-stu-id="a9c99-145">Set the **Video Clip** property to your video file</span></span>
* <span data-ttu-id="a9c99-146">选中 " **循环** " 复选框</span><span class="sxs-lookup"><span data-stu-id="a9c99-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="a9c99-147">将 **目标纹理** 设置为新的渲染纹理</span><span class="sxs-lookup"><span data-stu-id="a9c99-147">Set **Target Texture** to your new render texture</span></span>

<span data-ttu-id="a9c99-148">**视频播放器** 的 " **检查器** " 窗格现在将如下所示：</span><span class="sxs-lookup"><span data-stu-id="a9c99-148">The **Inspector** pane for the **Video Player** will now look like this:</span></span>

![视频播放器属性](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="a9c99-150">Spatialize 视频中的音频</span><span class="sxs-lookup"><span data-stu-id="a9c99-150">Spatialize the audio from the video</span></span>
<span data-ttu-id="a9c99-151">在 **四** 个 " **检查器** " 窗格中，创建要将音频从视频路由到的 **音频源** ：</span><span class="sxs-lookup"><span data-stu-id="a9c99-151">In the **Inspector** pane for the **Quad** , create an **Audio Source** to which you'll route the audio from the video:</span></span>
* <span data-ttu-id="a9c99-152">单击窗格底部的 " **添加组件** "</span><span class="sxs-lookup"><span data-stu-id="a9c99-152">Click **Add Component** at the bottom of the pane</span></span>
* <span data-ttu-id="a9c99-153">添加 **音频源**</span><span class="sxs-lookup"><span data-stu-id="a9c99-153">Add an **Audio Source**</span></span>

<span data-ttu-id="a9c99-154">然后，在 " **音频源** ：</span><span class="sxs-lookup"><span data-stu-id="a9c99-154">Then, on the **Audio Source** :</span></span>
* <span data-ttu-id="a9c99-155">将 **输出** 设置为混音器</span><span class="sxs-lookup"><span data-stu-id="a9c99-155">Set **Output** to your mixer</span></span>
* <span data-ttu-id="a9c99-156">选中 " **Spatialize** " 框</span><span class="sxs-lookup"><span data-stu-id="a9c99-156">Check the **Spatialize** box</span></span>
* <span data-ttu-id="a9c99-157">将 **空间混合** 滑块移动到 1 (3d) </span><span class="sxs-lookup"><span data-stu-id="a9c99-157">Move the **Spatial Blend** slider to 1 (3D)</span></span>

<span data-ttu-id="a9c99-158">进行这些更改后， **四** 个 " **检查器** " 窗格中的 " **音频源** " 组件会如下所示：</span><span class="sxs-lookup"><span data-stu-id="a9c99-158">After these changes, the **Audio Source** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![四核音频源检查器](images/spatial-audio/quad-audio-source-inspector.png)

<span data-ttu-id="a9c99-160">若要将 **视频播放器** 设置为将音频源路由到 **四** 个视频 **源** ，请打开 **视频播放器** 的 **检查器** 窗格，并执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a9c99-160">To set the **Video Player** to route its audio to the **Audio Source** on the **Quad** , open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="a9c99-161">将 **音频输出模式** 设置为 "音频源"</span><span class="sxs-lookup"><span data-stu-id="a9c99-161">Set the **Audio Output Mode** to 'Audio Source'</span></span>
* <span data-ttu-id="a9c99-162">将 " **音频源** " 属性设置为四</span><span class="sxs-lookup"><span data-stu-id="a9c99-162">Set the **Audio Source** property to your Quad</span></span>

<span data-ttu-id="a9c99-163">进行这些更改后， **视频播放器** 的 " **检查器** " 窗格将如下所示：</span><span class="sxs-lookup"><span data-stu-id="a9c99-163">After these changes, the **Inspector** pane for the **Video Player** will look like this:</span></span>

![视频播放器设置音频源](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a><span data-ttu-id="a9c99-165">后续步骤</span><span class="sxs-lookup"><span data-stu-id="a9c99-165">Next steps</span></span>
<span data-ttu-id="a9c99-166">在 HoloLens 2 上或在 Unity 编辑器中试用你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="a9c99-166">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="a9c99-167">你将看到并听到视频，视频中的音频将为 spatialized。</span><span class="sxs-lookup"><span data-stu-id="a9c99-167">You'll see and hear the video, and the audio from the video will be spatialized.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a9c99-168">第4章</span><span class="sxs-lookup"><span data-stu-id="a9c99-168">Chapter 4</span></span>](unity-spatial-audio-ch4.md) 

