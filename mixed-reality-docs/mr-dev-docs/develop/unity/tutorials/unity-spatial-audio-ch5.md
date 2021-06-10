---
title: 空间音频教程-5。 使用混响为空间音频添加距离感
description: 添加回音效果，提高对空间音频的距离变体的意义。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality，unity，教程，hololens2，空间音频，MRTK，混合现实工具包，UWP，Windows 10，HRTF，头相关传输函数，回音，Microsoft Spatializer，音频混合器，SFX 回音
ms.openlocfilehash: 6f41fe904c21591915e0ef13b61dc6bff04527fe
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712672"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="1829e-105">5.使用混响为空间音频添加距离感</span><span class="sxs-lookup"><span data-stu-id="1829e-105">5. Using reverb to add distance to spatial audio</span></span>

## <a name="overview"></a><span data-ttu-id="1829e-106">概述</span><span class="sxs-lookup"><span data-stu-id="1829e-106">Overview</span></span>

<span data-ttu-id="1829e-107">在上一教程中，你已为声音添加了 spatialization，以使其在本教程中有一个方向，你将添加一个回音效果，以便为声音提供距离。</span><span class="sxs-lookup"><span data-stu-id="1829e-107">In previous tutorial, you have added spatialization for the sounds to give them a sense of direction in this tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

## <a name="objectives"></a><span data-ttu-id="1829e-108">目标</span><span class="sxs-lookup"><span data-stu-id="1829e-108">Objectives</span></span>

* <span data-ttu-id="1829e-109">通过添加回音来改善声音源的感知距离。</span><span class="sxs-lookup"><span data-stu-id="1829e-109">Improve perceived distance of sound sources by adding reverb.</span></span>
* <span data-ttu-id="1829e-110">使用侦听器与全息图的距离控制声音的已知距离。</span><span class="sxs-lookup"><span data-stu-id="1829e-110">Control perceived distance of the sound using the listener's distance to the hologram.</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="1829e-111">添加混音器组和回音效果</span><span class="sxs-lookup"><span data-stu-id="1829e-111">Add a mixer group and a reverb effect</span></span>

<span data-ttu-id="1829e-112">在 [Spatializing button 交互声音教程](unity-spatial-audio-ch2.md)中，我们添加了一个混音器。</span><span class="sxs-lookup"><span data-stu-id="1829e-112">In [Spatializing button interaction sounds Tutorial](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="1829e-113">混音器默认包含一个名为 **Master** 的 **组**。</span><span class="sxs-lookup"><span data-stu-id="1829e-113">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="1829e-114">因为我们只是想要将回音效果应用到一些声音，接下来要为这些声音添加另一个组。</span><span class="sxs-lookup"><span data-stu-id="1829e-114">Because we'll only want to apply a reverb effect to some sounds, let's add a second Group for those sounds.</span></span> <span data-ttu-id="1829e-115">若要添加组，请在 **音频混合器** 中右键单击主组，选择 " **添加子组** " 并为 " _会议室效果_" 提供合适的名称：</span><span class="sxs-lookup"><span data-stu-id="1829e-115">To add a Group, right click on the Master group in the **Audio Mixer** choose **Add child group** and give suitable name for example _Room Effect_:</span></span>

![添加子组](images/spatial-audio/spatial-audio-05-section1-step1-1.PNG)

<span data-ttu-id="1829e-117">每个 **组** 都有自己的效果集。</span><span class="sxs-lookup"><span data-stu-id="1829e-117">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="1829e-118">通过在新组中单击 " **添加 ...** " 并选择 " **SFX 回音**"，向新组添加回音效果：</span><span class="sxs-lookup"><span data-stu-id="1829e-118">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![添加 SFX 回音](images/spatial-audio/spatial-audio-05-section1-step1-2.PNG)

<span data-ttu-id="1829e-120">在音频术语中，原始、unreverberated 的音频称为 _晾干路径_，筛选后的音频被称为 _湿路径_。</span><span class="sxs-lookup"><span data-stu-id="1829e-120">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="1829e-121">这两个路径都发送到音频输出，在此组合中，其相对强度称为 _湿/干燥混合_。</span><span class="sxs-lookup"><span data-stu-id="1829e-121">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="1829e-122">湿/干燥混合会对距离的理解产生很大影响。</span><span class="sxs-lookup"><span data-stu-id="1829e-122">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="1829e-123">**SFX 回音** 包含用于在效果内调整湿/干燥混合的控件。</span><span class="sxs-lookup"><span data-stu-id="1829e-123">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="1829e-124">由于 **Microsoft Spatializer** 插件处理晾干路径，因此，我们只为湿路径使用 **SFX 回音** 。</span><span class="sxs-lookup"><span data-stu-id="1829e-124">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="1829e-125">在 **SFX 回音** 的 "检查器" 窗格上：</span><span class="sxs-lookup"><span data-stu-id="1829e-125">On the Inspector pane of your **SFX Reverb**:</span></span>

* <span data-ttu-id="1829e-126">将 " **晾干级别** " 属性设置为最低 (-10000 mB) </span><span class="sxs-lookup"><span data-stu-id="1829e-126">Set the **Dry Level** property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="1829e-127">将 " **房间" 属性** 设置为最高 (0 mB) </span><span class="sxs-lookup"><span data-stu-id="1829e-127">Set the **Room property** to the highest setting (0 mB)</span></span>

![SFX 回音属性](images/spatial-audio/spatial-audio-05-section1-step1-3.PNG)

<span data-ttu-id="1829e-129">其他设置控制模拟房间的感觉。</span><span class="sxs-lookup"><span data-stu-id="1829e-129">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="1829e-130">具体而言， **衰减时间** 与感知到的空间大小相关。</span><span class="sxs-lookup"><span data-stu-id="1829e-130">In particular, **Decay Time** is related to perceived room size.</span></span>

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="1829e-131">启用视频播放时播放回音</span><span class="sxs-lookup"><span data-stu-id="1829e-131">Enable reverb on the video playback</span></span>

<span data-ttu-id="1829e-132">在音频源上启用回音的步骤有两个：</span><span class="sxs-lookup"><span data-stu-id="1829e-132">There are two steps to enable reverb on an audio source:</span></span>

* <span data-ttu-id="1829e-133">将 **音频源** 路由到相应的 **组**</span><span class="sxs-lookup"><span data-stu-id="1829e-133">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="1829e-134">设置 **Microsoft Spatializer** 插件以将音频传递到 **组** 进行处理</span><span class="sxs-lookup"><span data-stu-id="1829e-134">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="1829e-135">在以下步骤中，你将调整脚本以控制音频路由，并附加与 **Microsoft Spatializer** 插件一起提供的控制脚本，将数据送入回音。</span><span class="sxs-lookup"><span data-stu-id="1829e-135">In the following steps, you will adjust the script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="1829e-136">在层次结构中选择的 **四** 个步骤中，单击 "检查器" 窗口上的 "**添加组件**"，并将 "**房间效果" 发送级别 (脚本)**</span><span class="sxs-lookup"><span data-stu-id="1829e-136">With the **Quad** selected in the Hierarchy click **Add Component** On the Inspector window and add the **Room Effect Send Level(Script)**:</span></span>

![添加发送级别脚本](images/spatial-audio/spatial-audio-05-section2-step1-1.PNG)

> [!NOTE]
> <span data-ttu-id="1829e-138">除非你启用 **Microsoft Spatializer** 插件的 **会议室效果发送级别** 功能，否则它不会将任何音频发送回 Unity 音频引擎以进行有效处理。</span><span class="sxs-lookup"><span data-stu-id="1829e-138">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="1829e-139">" **房间效果发送级别** " 组件包括一个图形控件，该控件设置发送到 Unity 音频引擎以进行回音处理的音频级别。</span><span class="sxs-lookup"><span data-stu-id="1829e-139">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="1829e-140">若要打开图形控件，请单击 **房间效果发送级别**。</span><span class="sxs-lookup"><span data-stu-id="1829e-140">To open the graph control, click on the **Room Effect Send Level**.</span></span>  <span data-ttu-id="1829e-141">单击并向下拖动绿色曲线，将级别设置为30dB：</span><span class="sxs-lookup"><span data-stu-id="1829e-141">Click and drag the green curve downwards to set the level to about -30dB:</span></span>

![调整回音曲线](images/spatial-audio/spatial-audio-05-section2-step1-2.PNG)

<span data-ttu-id="1829e-143">接下来，取消注释 **SpatializeOnOff** 脚本中的4个注释行。</span><span class="sxs-lookup"><span data-stu-id="1829e-143">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="1829e-144">该脚本现在将如下所示：</span><span class="sxs-lookup"><span data-stu-id="1829e-144">The script will now look like this:</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

<span data-ttu-id="1829e-145">取消注释这些行后，它会将两个属性添加到 **SpatializeOnOff 脚本** 的检查器中。</span><span class="sxs-lookup"><span data-stu-id="1829e-145">Once these lines are Uncommented  it adds two properties to the Inspector of the **SpatializeOnOff script**.</span></span> <span data-ttu-id="1829e-146">在 **四** 个 **SpatializeOnOff** 组件的检查器窗口上分配它们。</span><span class="sxs-lookup"><span data-stu-id="1829e-146">assign these on the Inspector window of **SpatializeOnOff** component of the **Quad**.</span></span>

<span data-ttu-id="1829e-147">在层次结构中，如果仍在层次结构中选择了 Quad 对象，请在检查器窗口中找到 **SpatializeOnOff 脚本** 组件，并：</span><span class="sxs-lookup"><span data-stu-id="1829e-147">With the Quad object still selected in the Hierarchy , in the Inspector window locate the **SpatializeOnOff Script** component and :</span></span>

* <span data-ttu-id="1829e-148">将 " **房间效果组** " 属性设置为新的 "房间效果" 混音器组</span><span class="sxs-lookup"><span data-stu-id="1829e-148">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="1829e-149">将 " **主组** " 属性设置为 "主混音器" 组</span><span class="sxs-lookup"><span data-stu-id="1829e-149">Set the **Master Group** property to the Master mixer group</span></span>

![Spatialize 扩展](images/spatial-audio/spatial-audio-05-section2-step1-3.PNG)

## <a name="congratulations"></a><span data-ttu-id="1829e-151">祝贺</span><span class="sxs-lookup"><span data-stu-id="1829e-151">Congratulations</span></span>

<span data-ttu-id="1829e-152">已完成适用于 Unity 的 HoloLens 2 空间音频教程。</span><span class="sxs-lookup"><span data-stu-id="1829e-152">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="1829e-153">试用 HoloLens 2 或 Unity 上的应用。</span><span class="sxs-lookup"><span data-stu-id="1829e-153">Try out the app on a HoloLens 2 or Unity.</span></span> <span data-ttu-id="1829e-154">单击应用中的按钮以激活 spatialization 时，该脚本会将视频的音频路由到房间效果组以添加回音。</span><span class="sxs-lookup"><span data-stu-id="1829e-154">When you click the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="1829e-155">切换到立体声时，它会将音频路由到主组，并避免添加回音。</span><span class="sxs-lookup"><span data-stu-id="1829e-155">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

> [!TIP]
> <span data-ttu-id="1829e-156">要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。</span><span class="sxs-lookup"><span data-stu-id="1829e-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>
