---
title: 空间音频教程-4。 在运行时启用和禁用空间音频
description: 使用按钮来启用和禁用运行时音频的 spatialization。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality，unity，教程，hololens2，空间音频，MRTK，混合现实工具包，UWP，Windows 10，HRTF，head 相关传输函数，回音，Microsoft Spatializer
ms.openlocfilehash: 9239c45efa5196b94fe2e05f85a2e83df6c7789f
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578300"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="ddfc4-105">4. 在运行时启用和禁用 spatialization</span><span class="sxs-lookup"><span data-stu-id="ddfc4-105">4. Enabling and disabling spatialization at run time</span></span>

## <a name="overview"></a><span data-ttu-id="ddfc4-106">概述</span><span class="sxs-lookup"><span data-stu-id="ddfc4-106">Overview</span></span>

<span data-ttu-id="ddfc4-107">在本教程中，您将学习如何在运行时启用和禁用 spatialization，并在 unity 编辑器和 HoloLens 2 中对此进行测试。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-107">In this tutorial, you will learn how to Enable and disable spatialization at run time and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="ddfc4-108">目标</span><span class="sxs-lookup"><span data-stu-id="ddfc4-108">Objectives</span></span>

* <span data-ttu-id="ddfc4-109">添加新脚本以控制游戏对象上的 spatialization</span><span class="sxs-lookup"><span data-stu-id="ddfc4-109">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="ddfc4-110">从按钮操作驱动 spatialization 控件脚本</span><span class="sxs-lookup"><span data-stu-id="ddfc4-110">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="ddfc4-111">添加 spatialization 控件脚本</span><span class="sxs-lookup"><span data-stu-id="ddfc4-111">Add spatialization control script</span></span>

 <span data-ttu-id="ddfc4-112">在项目窗口中右键单击，然后选择 "**创建**  >  **c # 脚本**" 以创建新的 c # 脚本，为脚本输入合适的名称，例如， _SpatializeOnOff_：</span><span class="sxs-lookup"><span data-stu-id="ddfc4-112">Right-click in the Project window and choose **Create** > **C# Script** to create a new C# script, enter a suitable name for the script, for example, _SpatializeOnOff_:</span></span>

![创建脚本](images/spatial-audio/spatial-audio-04-section1-step1-1.png)

<span data-ttu-id="ddfc4-114">双击 "项目" 窗口中的脚本，在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-114">Double-click the script in the Project window to open it in Visual Studio.</span></span> <span data-ttu-id="ddfc4-115">将默认脚本内容替换为以下内容：</span><span class="sxs-lookup"><span data-stu-id="ddfc4-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="ddfc4-116">脚本的几行被注释掉。以下各行将在 [下一章中取消注释：使用回音向空间音频添加距离](unity-spatial-audio-ch5.md)。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-116">Several lines of the script are commented out. These lines will be uncommented in [Next Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md).</span></span>

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

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
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> <span data-ttu-id="ddfc4-117">若要启用或禁用 spatialization，此脚本只会调整 **spatialBlend** 属性，使 **spatialization** 属性保持启用状态。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-117">To enable or disable the spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="ddfc4-118">在此模式下，Unity 仍会应用 **卷** 曲线。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="ddfc4-119">否则，如果用户在远距离源时禁用了 spatialization，则会听到音量突然增加。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span>
> <span data-ttu-id="ddfc4-120">如果希望完全禁用 spatialization，请修改脚本，同时调整 **SourceObject** 变量的 **spatialization** 布尔值属性。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="ddfc4-121">附加脚本，然后从按钮中进行驱动器</span><span class="sxs-lookup"><span data-stu-id="ddfc4-121">Attach your script and drive it from the button</span></span>

<span data-ttu-id="ddfc4-122">选择层次结构中的 **四** 个，并在 "检查器" 窗口中，使用 "添加组件" 按钮添加 **SpatializeOnOff (脚本)**</span><span class="sxs-lookup"><span data-stu-id="ddfc4-122">Select **Quad** in the Hierarchy and in the Inspector window, use the Add Component button to add **SpatializeOnOff(Script)**</span></span>

![将脚本添加到四个](images/spatial-audio/spatial-audio-04-section2-step1-1.png)

<span data-ttu-id="ddfc4-124">在层次结构中找到 **PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-124">In the Hierarchy locate **PressableButtonHoloLens2** > **IconAndText** > **TextMeshPro**.</span></span>

<span data-ttu-id="ddfc4-125">如果仍在层次结构中选择了 **Quad** 对象，则在 "检查器" 窗口中，找到 " **Spatialize On Off" (Script)** Component 并拖放 PressableButtonHoloLens2 的 **TextMeshPro** 组件。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-125">With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.</span></span>

![在层次结构中查找 PressableButtonHoloLens2 对象](images/spatial-audio/spatial-audio-04-section2-step1-2.png)

<span data-ttu-id="ddfc4-127">若要将按钮设置为在释放按钮时调用 **SpatializeOnOff** 脚本，需要配置种不可交互脚本。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-127">To set the button to call the **SpatializeOnOff** script when the button is released You need to configure interactable script.</span></span>

<span data-ttu-id="ddfc4-128">在 "层次结构" 窗口中，选择 " **PressableButtonHoloLens2**"。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-128">In the Hierarchy window, select the **PressableButtonHoloLens2**.</span></span> <span data-ttu-id="ddfc4-129">在 "检查器" 窗口中，找到 **种不可交互 (Script)** 组件，并单击 OnClick ( # A3 事件下的 + 图标。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-129">In the Inspector window, locate the **Interactable (Script)** component and click on + icon under OnClick () event.</span></span>

* <span data-ttu-id="ddfc4-130">如果仍在 "层次结构" 窗口中选择 "PressableButtonHoloLens2" 对象，请在 "层次结构" 窗口中单击 "  "，并将 **该对象从**"层次结构" 窗口中拖到 "空 **None (") 对象** 中，然后将 ButtonParent 对象侦听此按钮中的按钮单击事件：</span><span class="sxs-lookup"><span data-stu-id="ddfc4-130">With the **PressableButtonHoloLens2** object still selected in the Hierarchy window, click-and-drag the **Quad** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

* <span data-ttu-id="ddfc4-131">单击同一事件的“无函数”下拉列表。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-131">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="ddfc4-132">然后选择 **SpatializeOnOff**  >  **SwapSpatialization ( # B1** 以打开和关闭空间音频</span><span class="sxs-lookup"><span data-stu-id="ddfc4-132">Then select **SpatializeOnOff** > **SwapSpatialization ()** to turn on and off the Spatial audio</span></span>

![按钮操作设置](images/spatial-audio/spatial-audio-04-section2-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="ddfc4-134">祝贺</span><span class="sxs-lookup"><span data-stu-id="ddfc4-134">Congratulations</span></span>

<span data-ttu-id="ddfc4-135">在本教程中，已学习了如何在运行时启用和禁用 spatialization、在 HoloLens 2 上或在 Unity 编辑器中测试应用程序。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-135">In this tutorial, you have learned how to enable and disable spatialization at run time, test out the app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="ddfc4-136">在应用程序中，你现在可以单击该按钮以激活和停用 spatialization 的音频。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-136">In the app, you can now click the button to activate and deactivate spatialization of the audio.</span></span>

<span data-ttu-id="ddfc4-137">在下一教程中，你将添加一个回音效果，以便为声音指定距离。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-137">In the next tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

> [!TIP]
> <span data-ttu-id="ddfc4-138">要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。</span><span class="sxs-lookup"><span data-stu-id="ddfc4-138">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ddfc4-139">下一教程： 5. 使用回音向空间音频添加距离</span><span class="sxs-lookup"><span data-stu-id="ddfc4-139">Next Tutorial: 5. Using reverb to add distance to spatial audio</span></span>](unity-spatial-audio-ch5.md)
