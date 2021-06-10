---
title: 空间音频教程 - 2. 将按钮交互声音空间化
description: 向项目添加一个按钮，并空间化按钮交互声音。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实， unity， 教程， hololens2， 空间音频， MRTK， 混合现实工具包， UWP， Windows 10， HRTF， 与头部相关的传输函数， 混响， Microsoft Spatializer， 预制器， 音量曲线
ms.openlocfilehash: f3f2faf8220eaebcc674bcf02a45d99d58169076
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712792"
---
# <a name="2-spatializing-button-interaction-sounds"></a><span data-ttu-id="124b3-105">2.将按钮交互声音空间化</span><span class="sxs-lookup"><span data-stu-id="124b3-105">2. Spatializing button interaction sounds</span></span>

## <a name="overview"></a><span data-ttu-id="124b3-106">概述</span><span class="sxs-lookup"><span data-stu-id="124b3-106">Overview</span></span>

<span data-ttu-id="124b3-107">本教程介绍如何将按钮交互声音空间化，并了解如何使用音频剪辑来测试空间化按钮交互。</span><span class="sxs-lookup"><span data-stu-id="124b3-107">In this tutorial, you will learn how to spatialize the button interaction sounds and also learn how to use an audio clip to test spatialized button interaction.</span></span>  

## <a name="objectives"></a><span data-ttu-id="124b3-108">目标</span><span class="sxs-lookup"><span data-stu-id="124b3-108">Objectives</span></span>

* <span data-ttu-id="124b3-109">添加按钮单击声音并将其空间化</span><span class="sxs-lookup"><span data-stu-id="124b3-109">Add and Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="124b3-110">添加按钮</span><span class="sxs-lookup"><span data-stu-id="124b3-110">Add a button</span></span>

<span data-ttu-id="124b3-111">若要添加按钮预制件，请在"项目"窗口中选择"包"，在搜索栏中键入"PressableButtonHoloLens2"。</span><span class="sxs-lookup"><span data-stu-id="124b3-111">To add the Button prefab, in the **Project** window, select **Packages** and type "PressableButtonHoloLens2" in the search bar.</span></span>

![资产中的按钮预制](images/spatial-audio/spatial-audio-02-section1-step1-1.PNG)

<span data-ttu-id="124b3-113">按钮预制项是由蓝色图标表示的项。</span><span class="sxs-lookup"><span data-stu-id="124b3-113">The button prefab is the entry represented by a blue icon.</span></span> <span data-ttu-id="124b3-114">单击 **PressableButtonHoloLens2** 预制项并将其拖动到"层次结构"中。</span><span class="sxs-lookup"><span data-stu-id="124b3-114">Click and drag the **PressableButtonHoloLens2** prefab into the Hierarchy.</span></span> <span data-ttu-id="124b3-115">在 **"PressableButtonHoloLens2"** 对象仍处于选中状态后，在"检查器"窗口中配置 **"转换** "组件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="124b3-115">With the **PressableButtonHoloLens2** object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="124b3-116">**位置**：X = 0，Y = -0.4，Z = 2</span><span class="sxs-lookup"><span data-stu-id="124b3-116">**Position**: X = 0, Y = -0.4, Z = 2</span></span>
* <span data-ttu-id="124b3-117">**旋转**：X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="124b3-117">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="124b3-118">**缩放**：X = 1，Y = 1，Z = 1</span><span class="sxs-lookup"><span data-stu-id="124b3-118">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![按钮转换](images/spatial-audio/spatial-audio-02-section1-step1-2.PNG)

<span data-ttu-id="124b3-120">若要专注于场景中的对象，可以双击 **PressableButtonHoloLens2** 对象，然后再次稍微放大：</span><span class="sxs-lookup"><span data-stu-id="124b3-120">To focus in on the objects in the scene, you can double-click on the **PressableButtonHoloLens2** object, and then zoom slightly in again:</span></span>

## <a name="spatialize-button-feedback"></a><span data-ttu-id="124b3-121">空间化按钮反馈</span><span class="sxs-lookup"><span data-stu-id="124b3-121">Spatialize button feedback</span></span>

<span data-ttu-id="124b3-122">在此步骤中，将按钮的音频反馈空间化。</span><span class="sxs-lookup"><span data-stu-id="124b3-122">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="124b3-123">有关相关设计建议，请参阅 [空间音效设计](../../../design/spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="124b3-123">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span>

<span data-ttu-id="124b3-124">在" **音频调音器** "窗口中，你将定义名为 **"调音** 器组"的目标，用于从音频源 **组件播放** 音频。</span><span class="sxs-lookup"><span data-stu-id="124b3-124">In the **Audio Mixer** window you will define destinations called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span>

<span data-ttu-id="124b3-125">若要打开音频 **调音器** 窗口，请在 Unity 菜单中选择"**窗口**  >  **音频**  >  **音频调** 音器： ![ 打开音频调音器窗口"](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)</span><span class="sxs-lookup"><span data-stu-id="124b3-125">To open the **Audio Mixer** window, In the Unity menu, select **Window** > **Audio** > **Audio Mixer**: ![Open Audio Mixer Window](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)</span></span>

 <span data-ttu-id="124b3-126">通过单击 **"调** 音器"旁边的"+"创建一个调音器，然后向"调音器"输入合适的名称，例如空间 _音频调音器_。</span><span class="sxs-lookup"><span data-stu-id="124b3-126">Create a **Mixer** by clicking the '+' next to **Mixers** and enter a suitable name to the Mixer for example, _Spatial Audio Mixer_.</span></span> <span data-ttu-id="124b3-127">新的混合器将包含名为 **Master 的默认\*\*\*\*组**。</span><span class="sxs-lookup"><span data-stu-id="124b3-127">The new mixer will include a default **Group** called **Master**.</span></span>

![具有第一个调音器的调音器面板](images/spatial-audio/spatial-audio-02-section2-step1-2.PNG)

> [!NOTE]
> <span data-ttu-id="124b3-129">直到第 [5](unity-spatial-audio-ch5.md)章：使用混响向空间音频添加距离中启用混响之前，调音器音量计不会显示通过 Microsoft Spatializer 播放的声音的活动</span><span class="sxs-lookup"><span data-stu-id="124b3-129">Until reverb is enabled in [5th Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="124b3-130">在"层次结构"窗口中，选择 **PressableButtonHoloLens2，** 然后在"检查器"窗口中找到"音频源"组件，并按如下所示配置"音频源"组件：</span><span class="sxs-lookup"><span data-stu-id="124b3-130">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window find the **Audio Source** component and Configure the Audio Source component as follows:</span></span>

1. <span data-ttu-id="124b3-131">对于" **输出** "属性，单击选择器并选择 **创建的"调** 音器"。</span><span class="sxs-lookup"><span data-stu-id="124b3-131">For the **Output** property, click the selector and choose the **Mixer** that you created.</span></span>
2. <span data-ttu-id="124b3-132">选中" **空间化"** 复选框。</span><span class="sxs-lookup"><span data-stu-id="124b3-132">Check the **Spatialize** checkbox.</span></span>
3. <span data-ttu-id="124b3-133">将" **空间混合"** 滑块移动到 1 (3D) 。</span><span class="sxs-lookup"><span data-stu-id="124b3-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

![按钮音频源](images/spatial-audio/spatial-audio-02-section2-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="124b3-135">如果将 **空间混合** 移动到 1 (3D) 而不选中"空间化"复选框，Unity 将使用其平移空间化程序，而不是 **将 Microsoft Spatializer** 与 HRTF 一起使用。</span><span class="sxs-lookup"><span data-stu-id="124b3-135">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="124b3-136">调整音量曲线</span><span class="sxs-lookup"><span data-stu-id="124b3-136">Adjust the Volume curve</span></span>

<span data-ttu-id="124b3-137">默认情况下，当空间化声音距离侦听器较远时，Unity 会衰减这些声音。</span><span class="sxs-lookup"><span data-stu-id="124b3-137">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="124b3-138">当此衰减应用于交互反馈声音时，界面可能变得更加难以使用。</span><span class="sxs-lookup"><span data-stu-id="124b3-138">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="124b3-139">若要禁用此衰减，需要在音频源 **组件中调整\*\*\*\*音量曲线。**</span><span class="sxs-lookup"><span data-stu-id="124b3-139">To disable this attenuation, you need to adjust the **Volume** curve In the **Audio Source** component.</span></span>

<span data-ttu-id="124b3-140">在"层次结构"窗口中，选择 **"PressableButtonHoloLens2"，** 然后在"检查器"窗口中导航到"音频 **源**  >  **3D 声音** 设置"，并按如下所示进行配置：</span><span class="sxs-lookup"><span data-stu-id="124b3-140">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window navigate to  **Audio Source** > **3D Sound Settings** and Configure as follows:</span></span>

1. <span data-ttu-id="124b3-141">将" **卷回滚"属性** 设置为"线性回滚"</span><span class="sxs-lookup"><span data-stu-id="124b3-141">Set the **Volume Rolloff** property to Linear Rolloff</span></span>
2. <span data-ttu-id="124b3-142">将"卷"曲线上的终结点 (红色曲线) 从 y 轴上的"0"拖动到"1"</span><span class="sxs-lookup"><span data-stu-id="124b3-142">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="124b3-143">若要将 **音量曲线的形状** 调整为平面，请将白色曲线形状控件拖动到 X 轴</span><span class="sxs-lookup"><span data-stu-id="124b3-143">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

![按钮 3D 声音设置](images/spatial-audio/spatial-audio-02-section3-step1-1.PNG)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="124b3-145">测试空间化音频</span><span class="sxs-lookup"><span data-stu-id="124b3-145">Testing the spatialize audio</span></span>

<span data-ttu-id="124b3-146">若要在 Unity 编辑器中测试空间化音频，你必须在 **PressableButtonHoloLens2** 对象上选中"循环"选项的"音频源"组件中添加音频剪辑。  </span><span class="sxs-lookup"><span data-stu-id="124b3-146">To test the spatialize audio in the unity editor you have to add an audio clip in the **Audio Source** component with **Loop** option checked in on **PressableButtonHoloLens2** object.</span></span>

<span data-ttu-id="124b3-147">在播放模式下，将 **PressableButtonHoloLens2** 对象从左向右移动，并比较工作站上启用的空间音频和未启用空间音频的对象。</span><span class="sxs-lookup"><span data-stu-id="124b3-147">In the play mode move the **PressableButtonHoloLens2** object from left to right and compare with and without spatial audio enabled on your workstation.</span></span> <span data-ttu-id="124b3-148">还可通过以下方法更改用于测试的音频源设置：</span><span class="sxs-lookup"><span data-stu-id="124b3-148">You can also change the Audio Source settings for testing by:</span></span>

* <span data-ttu-id="124b3-149">将 **空间混合属性** 移动到 0 到 1 之间 (2D 非空间化以及 3D 空间化声音) </span><span class="sxs-lookup"><span data-stu-id="124b3-149">Moving the **Spatial Blend** property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
* <span data-ttu-id="124b3-150">检查和取消选中 **Spatialize** 属性</span><span class="sxs-lookup"><span data-stu-id="124b3-150">Checking and unchecking the **Spatialize** property</span></span>

<span data-ttu-id="124b3-151">在应用程序上试用HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="124b3-151">Try out the app on HoloLens 2.</span></span> <span data-ttu-id="124b3-152">在应用中，可以单击按钮并听到空间化按钮交互声音。</span><span class="sxs-lookup"><span data-stu-id="124b3-152">In the app, you can click the button and hear the spatialized button interaction sounds.</span></span>

> [!TIP]
> <span data-ttu-id="124b3-153">要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。</span><span class="sxs-lookup"><span data-stu-id="124b3-153">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="124b3-154">祝贺</span><span class="sxs-lookup"><span data-stu-id="124b3-154">Congratulations</span></span>

<span data-ttu-id="124b3-155">在本教程中，你已了解将按钮交互声音空间化，并使用音频剪辑来测试空间化按钮交互。</span><span class="sxs-lookup"><span data-stu-id="124b3-155">In this tutorial you have learnt to spatialize the button interaction sounds and to use an audio clip to test spatialized button interaction.</span></span> <span data-ttu-id="124b3-156">下一教程将介绍如何从视频源对音频进行空间化。</span><span class="sxs-lookup"><span data-stu-id="124b3-156">In the next tutorial you will learn how to spatialize audio from an video source.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="124b3-157">下一教程：3.对视频中的音频进行空间化</span><span class="sxs-lookup"><span data-stu-id="124b3-157">Next Tutorial: 3. Spatializing audio from a video</span></span>](unity-spatial-audio-ch3.md)
