---
title: 空间音频教程-3。 将视频中的音频空间化
description: 将视频资产导入到 Unity 项目，并 spatialize 视频中的音频。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality，unity，教程，hololens2，空间音频，MRTK，混合现实工具包，UWP，Windows 10，HRTF，头相关传输函数，回音，Microsoft Spatializer，视频导入，视频播放器
ms.openlocfilehash: 876918c3e886fae6cd2066d84c55a6e158e4c773
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590049"
---
# <a name="3-spatializing-audio-from-a-video"></a><span data-ttu-id="42d73-105">3.将视频中的音频空间化</span><span class="sxs-lookup"><span data-stu-id="42d73-105">3. Spatializing audio from a video</span></span>

## <a name="overview"></a><span data-ttu-id="42d73-106">概述</span><span class="sxs-lookup"><span data-stu-id="42d73-106">Overview</span></span>

<span data-ttu-id="42d73-107">在本教程中，您将学习如何从视频源 spatialize 音频并在 unity 编辑器和 HoloLens 2 中对此进行测试。</span><span class="sxs-lookup"><span data-stu-id="42d73-107">In this tutorial, you will learn how to spatialize audio from an video source and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="42d73-108">目标</span><span class="sxs-lookup"><span data-stu-id="42d73-108">Objectives</span></span>

* <span data-ttu-id="42d73-109">导入视频并添加视频播放器</span><span class="sxs-lookup"><span data-stu-id="42d73-109">Import a video and add a Video Player</span></span>
* <span data-ttu-id="42d73-110">播放视频到 quadrangle</span><span class="sxs-lookup"><span data-stu-id="42d73-110">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="42d73-111">将音频从视频路由到 quadrangle，并 spatialize 音频</span><span class="sxs-lookup"><span data-stu-id="42d73-111">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a><span data-ttu-id="42d73-112">导入视频并将视频播放器添加到场景</span><span class="sxs-lookup"><span data-stu-id="42d73-112">Import a video and add a Video Player to the Scene</span></span>

<span data-ttu-id="42d73-113">在本教程中，你可以从空间音频示例项目使用 [此视频](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) 。</span><span class="sxs-lookup"><span data-stu-id="42d73-113">For this tutorial use You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

<span data-ttu-id="42d73-114">将视频导入 unity 项目。</span><span class="sxs-lookup"><span data-stu-id="42d73-114">To import Video into the unity project.</span></span> <span data-ttu-id="42d73-115">在 Unity 菜单中，选择 "**资产**  >  **导入新资产** 
 ![ 导入资产"](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="42d73-115">in the Unity menu select **Asset** > **Import New Asset**
![Importing Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span></span>

<span data-ttu-id="42d73-116">在 " **导入新资产 ...** " 窗口中，选择已下载的 **Microsoft HoloLens 空间 PTPvx7mDon4** 文件，并单击 " **打开** " 按钮将资产导入到项目中：</span><span class="sxs-lookup"><span data-stu-id="42d73-116">In the **Import New Asset...** window, select the **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** file you downloaded and click the **Open** button to import the asset into the project:</span></span>

![选择资产](images/spatial-audio/spatial-audio-03-section1-step1-2.png)

<span data-ttu-id="42d73-118">调整视频剪辑的质量设置可以确保在 HoloLens 2 上顺畅地播放。</span><span class="sxs-lookup"><span data-stu-id="42d73-118">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="42d73-119">在 " **项目** " 窗口中选择视频文件，并在视频文件的 "检查器" 窗口中， **覆盖** **Windows 应用商店应用** 的设置，并执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="42d73-119">Select the video file in the **Project** window and in the Inspector window of the video file, **override** the settings for **Windows Store Apps**, and:</span></span>

* <span data-ttu-id="42d73-120">启用 **转码**</span><span class="sxs-lookup"><span data-stu-id="42d73-120">Enable **Transcode**</span></span>
* <span data-ttu-id="42d73-121">将 **编解码器** 设置为 H264</span><span class="sxs-lookup"><span data-stu-id="42d73-121">Set **Codec** to H264</span></span>
* <span data-ttu-id="42d73-122">将 **比特率模式** 设置为低</span><span class="sxs-lookup"><span data-stu-id="42d73-122">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="42d73-123">将 **空间质量** 设置为中等空间质量</span><span class="sxs-lookup"><span data-stu-id="42d73-123">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="42d73-124">完成这些调整后，单击 "应用" 以更改视频剪辑的质量设置。</span><span class="sxs-lookup"><span data-stu-id="42d73-124">After these adjustments, click on Apply to change the quality setting on the video clip.</span></span>

![视频属性更改](images/spatial-audio/spatial-audio-03-section1-step1-3.png)

<span data-ttu-id="42d73-126">右键单击层次结构，选择 "**视频**  >  **视频播放器**" 添加视频播放器组件。</span><span class="sxs-lookup"><span data-stu-id="42d73-126">Right click on the Hierarchy, Select **Video** > **Video Player** to add Video player component.</span></span>

![添加视频播放器](images/spatial-audio/spatial-audio-03-section1-step1-4.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="42d73-128">播放视频到 quadrangle</span><span class="sxs-lookup"><span data-stu-id="42d73-128">Play video onto a quadrangle</span></span>

<span data-ttu-id="42d73-129">**视频播放器** 对象需要纹理的游戏对象来渲染视频。</span><span class="sxs-lookup"><span data-stu-id="42d73-129">The **Video Player** object needs a textured game object to render the video.</span></span>

<span data-ttu-id="42d73-130">右键单击层次结构，选择 " **3d 对象**  >  **四** 个"，创建一个四核，并按如下所示配置 **转换** 组件：</span><span class="sxs-lookup"><span data-stu-id="42d73-130">Right click the Hierarchy , Select **3D Object** > **Quad** to create a quad and configure its **Transform** component as follows:</span></span>

* <span data-ttu-id="42d73-131">**Position**： X = 0、Y = 0、Z = 2</span><span class="sxs-lookup"><span data-stu-id="42d73-131">**Position**: X = 0, Y = 0, Z = 2</span></span>
* <span data-ttu-id="42d73-132">**旋转**：X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="42d73-132">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="42d73-133">**Scale**： X = 1.28，Y = 0.72，Z = 1</span><span class="sxs-lookup"><span data-stu-id="42d73-133">**Scale**: X = 1.28, Y = 0.72, Z = 1</span></span>

![添加四](images/spatial-audio/spatial-audio-03-section2-step1-1.png)

<span data-ttu-id="42d73-135">现在，需要使用视频对 **四核** 进行着色，在 "**项目**" 窗口中，右键单击并选择 "**创建**  >  **渲染纹理**" 以创建渲染纹理组件，为渲染纹理输入合适的名称（例如，_空间音频纹理_）：</span><span class="sxs-lookup"><span data-stu-id="42d73-135">Now you need to texture the **Quad** with the video, In the **Project** window, right-click and choose **Create** > **Render Texture** to create a Render Texture component, enter a suitable name to the Render Texture for example, _Spatial Audio Texture_:</span></span>

![创建着色纹理](images/spatial-audio/spatial-audio-03-section2-step1-2.png)

<span data-ttu-id="42d73-137">选择 " **渲染纹理** "，然后在 "检查器" 窗口中，设置 " **Size** " 属性以匹配视频的 "1280x720 的本机分辨率"。</span><span class="sxs-lookup"><span data-stu-id="42d73-137">Select the **Render Texture** and in the Inspector window set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="42d73-138">然后，若要确保在 HoloLens 2 上呈现良好的性能，请将 **深度缓冲区** 属性设置为 **至少16位深度**。</span><span class="sxs-lookup"><span data-stu-id="42d73-138">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span>

![呈现纹理属性](images/spatial-audio/spatial-audio-03-section2-step1-3.png)

<span data-ttu-id="42d73-140">接下来，使用创建的呈现纹理 **空间音频纹理** 作为 **四** 个的纹理：</span><span class="sxs-lookup"><span data-stu-id="42d73-140">Next, use the created Render Texture **Spatial Audio Texture** as the texture for the **Quad**:</span></span>

1. <span data-ttu-id="42d73-141">将 **空间音频纹理** 从 " **项目** " 窗口拖到层次结构中的 " **四** 个"，将渲染纹理添加到 "四核"</span><span class="sxs-lookup"><span data-stu-id="42d73-141">Drag the **Spatial Audio Texture** from the **Project** window onto the **Quad** in the Hierarchy to add the Render Texture to the Quad</span></span>
2. <span data-ttu-id="42d73-142">若要在 HoloLens 2 上确保良好的性能，请在层次结构中选择四个四个，并在着色器的检查器窗口中选择 **混合现实工具包**  >  **标准** 着色器。</span><span class="sxs-lookup"><span data-stu-id="42d73-142">To ensure good performance on HoloLens 2, select Quad in the Hierarchy and in the Inspector window for shader select the **Mixed Reality Toolkit** > **Standard** Shader.</span></span>

![四纹理属性](images/spatial-audio/spatial-audio-03-section2-step1-4.png)

<span data-ttu-id="42d73-144">若要设置 **视频播放机** 和 **渲染纹理** 以播放视频剪辑，请在 **层次结构** 中选择 **视频播放器**，然后在 "**检查器**" 窗口中选择</span><span class="sxs-lookup"><span data-stu-id="42d73-144">To set **Video Player** and **Render Texture** to play the video clip, select the **Video Player** in the **Hierarchy** and in the **Inspector** window,</span></span>

* <span data-ttu-id="42d73-145">将 **视频剪辑** 属性设置为下载的视频文件 "Microsoft PTPvx7mDon4"</span><span class="sxs-lookup"><span data-stu-id="42d73-145">Set the **Video Clip** property to the downloaded video file 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'</span></span>
* <span data-ttu-id="42d73-146">选中 " **循环** " 复选框</span><span class="sxs-lookup"><span data-stu-id="42d73-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="42d73-147">将 **目标纹理** 设置为新的呈现纹理 **空间音频纹理**</span><span class="sxs-lookup"><span data-stu-id="42d73-147">Set **Target Texture** to your new render texture **Spatial Audio Texture**</span></span>

![视频播放器属性](images/spatial-audio/spatial-audio-03-section2-step1-5.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="42d73-149">Spatialize 视频中的音频</span><span class="sxs-lookup"><span data-stu-id="42d73-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="42d73-150">在 "层次结构" 窗口中，选择 " **四** 个对象"，然后在 "检查器" 窗口中，使用 " **添加组件** " 按钮添加 **音频源** ，从视频将音频源路由到该视频源。</span><span class="sxs-lookup"><span data-stu-id="42d73-150">In the Hierarchy window, select **Quad** object, then in the Inspector window, use the **Add Component** button to add **Audio Source** to which you'll route the audio from the video.</span></span>

<span data-ttu-id="42d73-151">在 **音频源** 中：</span><span class="sxs-lookup"><span data-stu-id="42d73-151">In the **Audio Source**:</span></span>

* <span data-ttu-id="42d73-152">将 **输出** 设置为 **空间音频混合器**</span><span class="sxs-lookup"><span data-stu-id="42d73-152">Set **Output** to the **Spatial Audio Mixer**</span></span>
* <span data-ttu-id="42d73-153">选中 " **Spatialize** " 框</span><span class="sxs-lookup"><span data-stu-id="42d73-153">Check the **Spatialize** box</span></span>
* <span data-ttu-id="42d73-154">将 **空间混合** 滑块移动到 1 (3d) </span><span class="sxs-lookup"><span data-stu-id="42d73-154">Move the **Spatial Blend** slider to 1 (3D)</span></span>

![四核音频源检查器](images/spatial-audio/spatial-audio-03-section3-step1-1.png)

<span data-ttu-id="42d73-156">若要将视频播放机设置为将音频源路由到 **音频源**，请在 "层次结构" 窗口中选择 **视频播放器** ，然后在 "检查器" 中的 "视频播放器" 对象中执行以下更改。</span><span class="sxs-lookup"><span data-stu-id="42d73-156">To set the Video Player to route its audio to the **Audio Source**, select the **Video Player** In the Hierarchy window, and in Video Player object in the Inspector do the following changes.</span></span>

* <span data-ttu-id="42d73-157">将 **音频输出模式** 设置为 **音频源**</span><span class="sxs-lookup"><span data-stu-id="42d73-157">Set the **Audio Output Mode** to **Audio Source**</span></span>
* <span data-ttu-id="42d73-158">将 " **音频源** " 属性设置为 **四**</span><span class="sxs-lookup"><span data-stu-id="42d73-158">Set the **Audio Source** property to the **Quad**</span></span>

![视频播放器设置音频源](images/spatial-audio/spatial-audio-03-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="42d73-160">要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。</span><span class="sxs-lookup"><span data-stu-id="42d73-160">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="42d73-161">祝贺</span><span class="sxs-lookup"><span data-stu-id="42d73-161">Congratulations</span></span>

<span data-ttu-id="42d73-162">在本教程中，你已学习如何从视频源 spatialize 音频，尝试在 HoloLens 2 上或在 Unity 编辑器中运行你的应用。</span><span class="sxs-lookup"><span data-stu-id="42d73-162">In this tutorial, you have learned how to spatialize audio from an video source Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="42d73-163">你会看到并听到视频，视频中的音频是 spatialized 的。</span><span class="sxs-lookup"><span data-stu-id="42d73-163">You'll see and hear the video, and the audio from the video is spatialized.</span></span>

<span data-ttu-id="42d73-164">在下一教程中，你将了解如何在运行时启用和禁用 spatialization</span><span class="sxs-lookup"><span data-stu-id="42d73-164">In the next tutorial you will learn how to Enable and disable spatialization at run time</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="42d73-165">下一教程： 4. 在运行时启用和禁用 spatialization</span><span class="sxs-lookup"><span data-stu-id="42d73-165">Next Tutorial: 4. Enabling and disabling spatialization at run time</span></span>](unity-spatial-audio-ch4.md)
