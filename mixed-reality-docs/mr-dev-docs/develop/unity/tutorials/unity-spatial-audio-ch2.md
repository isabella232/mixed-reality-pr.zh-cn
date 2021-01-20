---
title: 空间音频教程-2。 将按钮交互声音空间化
description: 向项目添加一个按钮，并 spatialize 按钮交互声音。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality，unity，教程，hololens2，空间音频，MRTK，混合现实工具包，UWP，Windows 10，HRTF，头相关传输函数，回音，Microsoft Spatializer，prototyping，音量曲线
ms.openlocfilehash: e4b2ed99f56fea82b1c72e4fce5205c14e1d3533
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578472"
---
# <a name="2-spatializing-button-interaction-sounds"></a><span data-ttu-id="e7f1c-105">2.将按钮交互声音空间化</span><span class="sxs-lookup"><span data-stu-id="e7f1c-105">2. Spatializing button interaction sounds</span></span>

## <a name="overview"></a><span data-ttu-id="e7f1c-106">概述</span><span class="sxs-lookup"><span data-stu-id="e7f1c-106">Overview</span></span>

<span data-ttu-id="e7f1c-107">在本教程中，你将学习如何 spatialize 按钮交互声音，还可以了解如何使用音频剪辑测试 spatialized 按钮交互。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-107">In this tutorial, you will learn how to spatialize the button interaction sounds and also learn how to use an audio clip to test spatialized button interaction.</span></span>  

## <a name="objectives"></a><span data-ttu-id="e7f1c-108">目标</span><span class="sxs-lookup"><span data-stu-id="e7f1c-108">Objectives</span></span>

* <span data-ttu-id="e7f1c-109">添加并 Spatialize 按钮单击声音</span><span class="sxs-lookup"><span data-stu-id="e7f1c-109">Add and Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="e7f1c-110">添加按钮</span><span class="sxs-lookup"><span data-stu-id="e7f1c-110">Add a button</span></span>

<span data-ttu-id="e7f1c-111">若要添加按钮 prefab，请在 " **项目** " 窗口中选择 " **资产** "，并在搜索栏中键入 "PressableButtonHoloLens2"。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-111">To add the Button prefab, in the **Project** window, select **Assets** and type "PressableButtonHoloLens2" in the search bar.</span></span>

![资产中的 prefab 按钮](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

<span data-ttu-id="e7f1c-113">按钮 prefab 是由蓝色图标表示的条目。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-113">The button prefab is the entry represented by a blue icon.</span></span> <span data-ttu-id="e7f1c-114">单击并将 **PressableButtonHoloLens2** prefab 拖到层次结构中。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-114">Click and drag the **PressableButtonHoloLens2** prefab into the Hierarchy.</span></span> <span data-ttu-id="e7f1c-115">在 **PressableButtonHoloLens2** 对象仍处于选中状态的情况下，在 "检查器" 窗口中，按如下所示配置 **转换** 组件：</span><span class="sxs-lookup"><span data-stu-id="e7f1c-115">With the **PressableButtonHoloLens2** object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="e7f1c-116">**Position**： X = 0，Y =-0.4，Z = 2</span><span class="sxs-lookup"><span data-stu-id="e7f1c-116">**Position**: X = 0, Y = -0.4, Z = 2</span></span>
* <span data-ttu-id="e7f1c-117">**旋转**：X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="e7f1c-117">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="e7f1c-118">**缩放**：X = 1，Y = 1，Z = 1</span><span class="sxs-lookup"><span data-stu-id="e7f1c-118">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![按钮转换](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

<span data-ttu-id="e7f1c-120">若要重点关注场景中的对象，可以双击 **PressableButtonHoloLens2** 对象，然后再次缩小：</span><span class="sxs-lookup"><span data-stu-id="e7f1c-120">To focus in on the objects in the scene, you can double-click on the **PressableButtonHoloLens2** object, and then zoom slightly in again:</span></span>

## <a name="spatialize-button-feedback"></a><span data-ttu-id="e7f1c-121">Spatialize 按钮反馈</span><span class="sxs-lookup"><span data-stu-id="e7f1c-121">Spatialize button feedback</span></span>

<span data-ttu-id="e7f1c-122">在此步骤中，你将 spatialize 按钮的音频反馈。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-122">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="e7f1c-123">有关相关设计的建议，请参阅 [空间音效设计](../../../design/spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-123">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span>

<span data-ttu-id="e7f1c-124">在 " **音频混音** 器" 窗口中，你将定义名为 " **混音器组**" 的目标，以便从 **音频源** 组件播放音频。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-124">In the **Audio Mixer** window you will define destinations called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span>

<span data-ttu-id="e7f1c-125">若要打开 "**音频混音** 器" 窗口，请在 Unity 菜单中选择 "**窗口**  >  **音频**  >  **混音** 器： ![ 打开音频混音器" 窗口](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="e7f1c-125">To open the **Audio Mixer** window, In the Unity menu, select **Window** > **Audio** > **Audio Mixer**: ![Open Audio Mixer Window](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span></span>

 <span data-ttu-id="e7f1c-126">单击 " **Mixers** " 旁边的 "+" 并向混音器输入合适的名称（例如，_空间音频混合器_），创建 **混音** 器。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-126">Create a **Mixer** by clicking the '+' next to **Mixers** and enter a suitable name to the Mixer for example, _Spatial Audio Mixer_.</span></span> <span data-ttu-id="e7f1c-127">新混音器将包含一个名为 **Master** 的默认 **组**。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-127">The new mixer will include a default **Group** called **Master**.</span></span>

![带有第一个混音器的混音器面板](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="e7f1c-129">在5章节中启用回响后 [：使用回音向空间音频添加距离](unity-spatial-audio-ch5.md)，混音器的音量指示器不显示通过 Microsoft Spatializer 播放的声音的活动</span><span class="sxs-lookup"><span data-stu-id="e7f1c-129">Until reverb is enabled in [5th Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="e7f1c-130">在 "层次结构" 窗口中，选择 " **PressableButtonHoloLens2** "，然后在 "检查器" 窗口中找到 " **音频源** " 组件，并按如下所示配置音频源组件：</span><span class="sxs-lookup"><span data-stu-id="e7f1c-130">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window find the **Audio Source** component and Configure the Audio Source component as follows:</span></span>

1. <span data-ttu-id="e7f1c-131">对于 " **输出** " 属性，单击选择器并选择已创建的 **混音** 器。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-131">For the **Output** property, click the selector and choose the **Mixer** that you created.</span></span>
2. <span data-ttu-id="e7f1c-132">选中 " **Spatialize** " 复选框。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-132">Check the **Spatialize** checkbox.</span></span>
3. <span data-ttu-id="e7f1c-133">将 **空间 Blend** 滑块移动到 3d (1) 。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

![按钮音频源](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="e7f1c-135">如果将 **空间混合** 移动到 1 (3d) 而不选中 **Spatialize** 复选框，则 Unity 将使用其平移 spatializer，而不是 **Microsoft spatializer** with HRTFs。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-135">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="e7f1c-136">调整音量曲线</span><span class="sxs-lookup"><span data-stu-id="e7f1c-136">Adjust the Volume curve</span></span>

<span data-ttu-id="e7f1c-137">默认情况下，在从侦听器获得更远的距离时，Unity 将衰减 spatialized 声音。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-137">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="e7f1c-138">如果此衰减应用于交互反馈声音，则接口可能会变得更难以使用。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-138">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="e7f1c-139">若要禁用此衰减，需调整 **音频源** 组件中的 **音量** 曲线。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-139">To disable this attenuation, you need to adjust the **Volume** curve In the **Audio Source** component.</span></span>

<span data-ttu-id="e7f1c-140">在 "层次结构" 窗口中，选择 " **PressableButtonHoloLens2** "，然后在 "检查器" 窗口中，导航到 "**音频源**  >  **3d 声音设置**"，并按如下</span><span class="sxs-lookup"><span data-stu-id="e7f1c-140">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window navigate to  **Audio Source** > **3D Sound Settings** and Configure as follows:</span></span>

1. <span data-ttu-id="e7f1c-141">将 **Volume Rolloff** 属性设置为线性 Rolloff</span><span class="sxs-lookup"><span data-stu-id="e7f1c-141">Set the **Volume Rolloff** property to Linear Rolloff</span></span>
2. <span data-ttu-id="e7f1c-142">将 **卷** 曲线上的终结点从 y 轴上的 "0")  (红色曲线上，直到 "1"</span><span class="sxs-lookup"><span data-stu-id="e7f1c-142">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="e7f1c-143">若要将 **音量** 曲线的形状调整为平面，请拖动 "白色曲线" 形状控件，使其平行于 X 轴</span><span class="sxs-lookup"><span data-stu-id="e7f1c-143">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

![按钮三维声音设置](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="e7f1c-145">测试 spatialize 音频</span><span class="sxs-lookup"><span data-stu-id="e7f1c-145">Testing the spatialize audio</span></span>

<span data-ttu-id="e7f1c-146">若要在 unity 编辑器中测试 spatialize 音频，必须在 **PressableButtonHoloLens2** 对象上 **的 "已签入"** "**循环**" 选项中添加音频剪辑。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-146">To test the spatialize audio in the unity editor you have to add an audio clip in the **Audio Source** component with **Loop** option checked in on **PressableButtonHoloLens2** object.</span></span>

<span data-ttu-id="e7f1c-147">在播放模式下，将 **PressableButtonHoloLens2** 对象从左到右移动，并在工作站上比较和不启用空间音频。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-147">In the play mode move the **PressableButtonHoloLens2** object from left to right and compare with and without spatial audio enabled on your workstation.</span></span> <span data-ttu-id="e7f1c-148">还可以通过以下方式更改用于测试的音频源设置：</span><span class="sxs-lookup"><span data-stu-id="e7f1c-148">You can also change the Audio Source settings for testing by:</span></span>

* <span data-ttu-id="e7f1c-149">将 **空间 Blend** 属性移动到 0-1 (2d 非 Spatialized 和 3d spatialized 声音) </span><span class="sxs-lookup"><span data-stu-id="e7f1c-149">Moving the **Spatial Blend** property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
* <span data-ttu-id="e7f1c-150">选中和取消选中 **Spatialize** 属性</span><span class="sxs-lookup"><span data-stu-id="e7f1c-150">Checking and unchecking the **Spatialize** property</span></span>

<span data-ttu-id="e7f1c-151">试用 HoloLens 2 上的应用。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-151">Try out the app on HoloLens 2.</span></span> <span data-ttu-id="e7f1c-152">在应用程序中，可以单击按钮并听到 spatialized 按钮交互声音。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-152">In the app, you can click the button and hear the spatialized button interaction sounds.</span></span>

> [!TIP]
> <span data-ttu-id="e7f1c-153">要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-153">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="e7f1c-154">祝贺</span><span class="sxs-lookup"><span data-stu-id="e7f1c-154">Congratulations</span></span>

<span data-ttu-id="e7f1c-155">在本教程中，你已了解到 spatialize 按钮交互声音，并使用音频剪辑测试 spatialized 按钮交互。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-155">In this tutorial you have learnt to spatialize the button interaction sounds and to use an audio clip to test spatialized button interaction.</span></span> <span data-ttu-id="e7f1c-156">在下一教程中，你将学习如何从视频源 spatialize 音频。</span><span class="sxs-lookup"><span data-stu-id="e7f1c-156">In the next tutorial you will learn how to spatialize audio from an video source.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e7f1c-157">下一教程： Spatializing 音频视频</span><span class="sxs-lookup"><span data-stu-id="e7f1c-157">Next Tutorial: 3. Spatializing audio from a video</span></span>](unity-spatial-audio-ch3.md)
