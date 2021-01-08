---
title: 将按钮交互声音空间化
description: 了解如何在混合现实应用程序中添加按钮并 spatialize 按钮交互声音。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality，unity，教程，hololens2，空间音频，MRTK，混合现实工具包，UWP，Windows 10，HRTF，头相关传输函数，回音，Microsoft Spatializer，prototyping，音量曲线
ms.openlocfilehash: 1f54ba8cab55ba375a6b1499796761ae02b03a02
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007357"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="74821-104">将按钮交互声音空间化</span><span class="sxs-lookup"><span data-stu-id="74821-104">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="74821-105">目标</span><span class="sxs-lookup"><span data-stu-id="74821-105">Objectives</span></span>

<span data-ttu-id="74821-106">在 HoloLens 2 教程的 "空间音频" 模块的第二章中，你将：</span><span class="sxs-lookup"><span data-stu-id="74821-106">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="74821-107">添加按钮</span><span class="sxs-lookup"><span data-stu-id="74821-107">Add a button</span></span>
* <span data-ttu-id="74821-108">Spatialize 按钮单击声音</span><span class="sxs-lookup"><span data-stu-id="74821-108">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="74821-109">添加按钮</span><span class="sxs-lookup"><span data-stu-id="74821-109">Add a button</span></span>

<span data-ttu-id="74821-110">在 " **项目** " 窗格中，选择 " **资产** "，并在搜索栏中键入 "PressableButtonHoloLens2"：</span><span class="sxs-lookup"><span data-stu-id="74821-110">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![资产中的 prefab 按钮](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="74821-112">按钮 prefab 是由蓝色图标表示的项，而不是白色图标。</span><span class="sxs-lookup"><span data-stu-id="74821-112">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="74821-113">将名为 **PressableButtonHoloLens2** 的 prefab 拖到 " **层次结构** " 窗格中。</span><span class="sxs-lookup"><span data-stu-id="74821-113">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="74821-114">在 "新建" 按钮的 " **检查器** " 窗格中，将 " **位置** " 属性设置为 (0，-0.4，2) ，以便在应用程序启动时，它将显示在用户之前。</span><span class="sxs-lookup"><span data-stu-id="74821-114">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="74821-115">此按钮的 **转换** 组件如下所示：</span><span class="sxs-lookup"><span data-stu-id="74821-115">The **Transform** component of the button will look like this:</span></span>

![按钮转换](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="74821-117">Spatialize 按钮反馈</span><span class="sxs-lookup"><span data-stu-id="74821-117">Spatialize button feedback</span></span>

<span data-ttu-id="74821-118">在此步骤中，你将 spatialize 按钮的音频反馈。</span><span class="sxs-lookup"><span data-stu-id="74821-118">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="74821-119">有关相关设计的建议，请参阅 [空间音效设计](../../../design/spatial-sound-design.md)。</span><span class="sxs-lookup"><span data-stu-id="74821-119">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span> 

<span data-ttu-id="74821-120">"**音频混音** 器" 窗格用于定义从 **音频源** 组件播放音频的目标（称为 **混音器组**）。</span><span class="sxs-lookup"><span data-stu-id="74821-120">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="74821-121">使用 **> 音频 > 音频混合器** 从菜单栏打开 "**音频混音** 器" 窗格</span><span class="sxs-lookup"><span data-stu-id="74821-121">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="74821-122">通过单击 **Mixers** 旁边的 "+" 来创建 **混音** 器。</span><span class="sxs-lookup"><span data-stu-id="74821-122">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="74821-123">新混音器将包含一个名为 **Master** 的默认 **组**。</span><span class="sxs-lookup"><span data-stu-id="74821-123">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="74821-124">**混音** 器窗格现在如下所示：</span><span class="sxs-lookup"><span data-stu-id="74821-124">Your **Mixer** pane will now look like this:</span></span>

![带有第一个混音器的混音器面板](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="74821-126">在 [第5章](unity-spatial-audio-ch5.md)中启用回响后，混音器的音量指示器不会显示通过 Microsoft Spatializer 播放的声音的活动</span><span class="sxs-lookup"><span data-stu-id="74821-126">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="74821-127">单击 "**层次结构**" 窗格中的 **PressableButtonHoloLens2** 。</span><span class="sxs-lookup"><span data-stu-id="74821-127">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="74821-128">在 " **检查器** " 窗格中：</span><span class="sxs-lookup"><span data-stu-id="74821-128">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="74821-129">查找 **音频源** 组件</span><span class="sxs-lookup"><span data-stu-id="74821-129">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="74821-130">对于 " **输出** " 属性，单击选择器并选择混音器</span><span class="sxs-lookup"><span data-stu-id="74821-130">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="74821-131">选中 " **Spatialize** " 复选框</span><span class="sxs-lookup"><span data-stu-id="74821-131">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="74821-132">将 **空间 Blend** 滑块移动到 3d (1) 。</span><span class="sxs-lookup"><span data-stu-id="74821-132">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="74821-133">在2019之前的 Unity 版本中，"Spatialize" 复选框位于 **音频源** 的 **检查器** 窗格的底部。</span><span class="sxs-lookup"><span data-stu-id="74821-133">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="74821-134">进行这些更改后， **PressableButtonHoloLens2** 的 **音频源** 组件将如下所示：</span><span class="sxs-lookup"><span data-stu-id="74821-134">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![按钮音频源](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="74821-136">如果将 **空间混合** 移动到 1 (3d) 而不选中 **Spatialize** 复选框，则 Unity 将使用其平移 spatializer，而不是 **Microsoft spatializer** with HRTFs。</span><span class="sxs-lookup"><span data-stu-id="74821-136">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="74821-137">调整音量曲线</span><span class="sxs-lookup"><span data-stu-id="74821-137">Adjust the Volume curve</span></span>

<span data-ttu-id="74821-138">默认情况下，在从侦听器获得更远的距离时，Unity 将衰减 spatialized 声音。</span><span class="sxs-lookup"><span data-stu-id="74821-138">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="74821-139">如果此衰减应用于交互反馈声音，则接口可能会变得更难以使用。</span><span class="sxs-lookup"><span data-stu-id="74821-139">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="74821-140">若要禁用此衰减，请调整 **音量** 曲线。</span><span class="sxs-lookup"><span data-stu-id="74821-140">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="74821-141">在 **PressableButtonHoloLens2** 的 "**检查器**" 窗格的 "**音频源**" 组件中，有一个名为 "**三维声音设置**" 的部分。</span><span class="sxs-lookup"><span data-stu-id="74821-141">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="74821-142">在该部分中：</span><span class="sxs-lookup"><span data-stu-id="74821-142">In that section:</span></span>
1. <span data-ttu-id="74821-143">将 **Volume Rolloff** 属性设置为线性</span><span class="sxs-lookup"><span data-stu-id="74821-143">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="74821-144">将 **卷** 曲线上的终结点从 y 轴上的 "0")  (红色曲线上，直到 "1"</span><span class="sxs-lookup"><span data-stu-id="74821-144">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="74821-145">若要将 **音量** 曲线的形状调整为平面，请拖动 "白色曲线" 形状控件，使其平行于 X 轴</span><span class="sxs-lookup"><span data-stu-id="74821-145">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="74821-146">进行这些更改后， **PressableButtonHoloLens2** 的 "**音频源**" 属性的 " **3d 声音设置**" 部分将如下所示：</span><span class="sxs-lookup"><span data-stu-id="74821-146">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![按钮三维声音设置](images/spatial-audio/button-3d-sound-settings.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="74821-148">测试 spatialize 音频</span><span class="sxs-lookup"><span data-stu-id="74821-148">Testing the spatialize audio</span></span>

<span data-ttu-id="74821-149">可随意测试新的 spatialized 按钮交互声音：</span><span class="sxs-lookup"><span data-stu-id="74821-149">Feel free to test out the new spatialized button interaction sounds:</span></span>

* <span data-ttu-id="74821-150">在 Unity 编辑器中进入游戏模式，理想情况下，使用场景中的循环音频示例</span><span class="sxs-lookup"><span data-stu-id="74821-150">Enter game mode in the Unity editor, ideally with a looped audio sample in the scene</span></span>
* <span data-ttu-id="74821-151">将对象从左到右移动到音频源，并与未启用空间音频的和进行比较。</span><span class="sxs-lookup"><span data-stu-id="74821-151">Move the object with the audio source from left to right and compare with and without spatial audio enabled.</span></span> <span data-ttu-id="74821-152">可以通过以下方式更改用于测试的音频源设置：</span><span class="sxs-lookup"><span data-stu-id="74821-152">You can change the Audio Source settings for testing by:</span></span>
    * <span data-ttu-id="74821-153">将空间 Blend 属性移动到 0-1 (2D 非 spatialized 和 3D spatialized 声音) </span><span class="sxs-lookup"><span data-stu-id="74821-153">Moving the Spatial Blend property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
    * <span data-ttu-id="74821-154">选中和取消选中 Spatialize 属性</span><span class="sxs-lookup"><span data-stu-id="74821-154">Checking and unchecking the Spatialize property</span></span>

## <a name="next-steps"></a><span data-ttu-id="74821-155">后续步骤</span><span class="sxs-lookup"><span data-stu-id="74821-155">Next steps</span></span>

<span data-ttu-id="74821-156">在 HoloLens 2 上或在 Unity 编辑器中试用你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="74821-156">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="74821-157">在应用程序中，可以触摸按钮并听到 spatialized 按钮交互声音。</span><span class="sxs-lookup"><span data-stu-id="74821-157">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="74821-158">在 Unity 编辑器中测试时，按空格键并滚动鼠标滚轮以激活手动模拟。</span><span class="sxs-lookup"><span data-stu-id="74821-158">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="74821-159">有关详细信息，请参阅 [MRTK 文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)。</span><span class="sxs-lookup"><span data-stu-id="74821-159">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="74821-160">第3章</span><span class="sxs-lookup"><span data-stu-id="74821-160">Chapter 3</span></span>](unity-spatial-audio-ch3.md)

