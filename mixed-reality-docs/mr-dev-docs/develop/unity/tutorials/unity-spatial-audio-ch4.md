---
title: 空间音频教程 - 4. 在运行时启用和禁用空间音频
description: 使用按钮可启用和禁用音频运行时的空间化。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实， unity， 教程， hololens2， 空间音频， MRTK， 混合现实工具包， UWP， Windows 10， HRTF， 与头部相关的传输函数， 混响， Microsoft 空间化程序
ms.openlocfilehash: 9d0fa432f2e653cdd6820cb6c779cc1acc5c4b15
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712740"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="d5b24-105">4.运行时启用和禁用空间化</span><span class="sxs-lookup"><span data-stu-id="d5b24-105">4. Enabling and disabling spatialization at run time</span></span>

## <a name="overview"></a><span data-ttu-id="d5b24-106">概述</span><span class="sxs-lookup"><span data-stu-id="d5b24-106">Overview</span></span>

<span data-ttu-id="d5b24-107">本教程介绍如何运行时启用和禁用空间化，以及如何在 unity 编辑器和HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="d5b24-107">In this tutorial, you will learn how to Enable and disable spatialization at run time and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="d5b24-108">目标</span><span class="sxs-lookup"><span data-stu-id="d5b24-108">Objectives</span></span>

* <span data-ttu-id="d5b24-109">添加新脚本以控制游戏对象上的空间化</span><span class="sxs-lookup"><span data-stu-id="d5b24-109">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="d5b24-110">通过按钮操作驱动空间化控制脚本</span><span class="sxs-lookup"><span data-stu-id="d5b24-110">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="d5b24-111">添加空间化控制脚本</span><span class="sxs-lookup"><span data-stu-id="d5b24-111">Add spatialization control script</span></span>

 <span data-ttu-id="d5b24-112">在"项目"窗口中右键单击，然后选择"创建 C# 脚本"以创建新的 C# 脚本，输入脚本的合适名称，  >  例如 _SpatializeOnOff_：</span><span class="sxs-lookup"><span data-stu-id="d5b24-112">Right-click in the Project window and choose **Create** > **C# Script** to create a new C# script, enter a suitable name for the script, for example, _SpatializeOnOff_:</span></span>

![创建脚本](images/spatial-audio/spatial-audio-04-section1-step1-1.PNG)

<span data-ttu-id="d5b24-114">双击"项目"窗口中的脚本，在"项目"窗口中Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d5b24-114">Double-click the script in the Project window to open it in Visual Studio.</span></span> <span data-ttu-id="d5b24-115">将默认脚本内容替换为以下内容：</span><span class="sxs-lookup"><span data-stu-id="d5b24-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="d5b24-116">脚本的几个行被注释掉。下一章：使用混响添加空间音频 的距离中 [将取消注释这些行](unity-spatial-audio-ch5.md)。</span><span class="sxs-lookup"><span data-stu-id="d5b24-116">Several lines of the script are commented out. These lines will be uncommented in [Next Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md).</span></span>

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
> <span data-ttu-id="d5b24-117">若要启用或禁用空间化，脚本仅调整 **spatialBlend** 属性，使 **空间化属性** 保留为启用状态。</span><span class="sxs-lookup"><span data-stu-id="d5b24-117">To enable or disable the spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="d5b24-118">在此模式下，Unity 仍应用"卷 **"** 曲线。</span><span class="sxs-lookup"><span data-stu-id="d5b24-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="d5b24-119">否则，如果用户在远离源时禁用空间化，他们将听到卷突然增加。</span><span class="sxs-lookup"><span data-stu-id="d5b24-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span>
> <span data-ttu-id="d5b24-120">如果希望完全禁用空间化，请修改脚本以同时调整 **SourceObject** 变量的空间化布尔属性。 </span><span class="sxs-lookup"><span data-stu-id="d5b24-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="d5b24-121">附加脚本，然后从按钮驱动它</span><span class="sxs-lookup"><span data-stu-id="d5b24-121">Attach your script and drive it from the button</span></span>

<span data-ttu-id="d5b24-122">在 **"** 层次结构"中选择"四边形"，在"检查器"窗口中，使用"添加组件"按钮添加 **SpatializeOnOff (脚本)**</span><span class="sxs-lookup"><span data-stu-id="d5b24-122">Select **Quad** in the Hierarchy and in the Inspector window, use the Add Component button to add **SpatializeOnOff(Script)**</span></span>

![将脚本添加到四边形](images/spatial-audio/spatial-audio-04-section2-step1-1.PNG)

<span data-ttu-id="d5b24-124">在"层次结构"中，找到 **PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**。</span><span class="sxs-lookup"><span data-stu-id="d5b24-124">In the Hierarchy locate **PressableButtonHoloLens2** > **IconAndText** > **TextMeshPro**.</span></span>

<span data-ttu-id="d5b24-125">在" **层次结构** "中仍选中 Quad 对象时，在"检查器"窗口中，找到 **"Spatialize On (Script) "** 组件，然后拖放 PressableButtonHoloLens2 的 **TextMeshPro** 组件。</span><span class="sxs-lookup"><span data-stu-id="d5b24-125">With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.</span></span>

![在层次结构中查找 PressableButtonHoloLens2 对象](images/spatial-audio/spatial-audio-04-section2-step1-2.PNG)

<span data-ttu-id="d5b24-127">若要设置按钮以在按钮释放时调用 **SpatializeOnOff** 脚本，需要配置可交互脚本。</span><span class="sxs-lookup"><span data-stu-id="d5b24-127">To set the button to call the **SpatializeOnOff** script when the button is released You need to configure interactable script.</span></span>

<span data-ttu-id="d5b24-128">在"层次结构"窗口中，选择 **"PressableButtonHoloLens2"。**</span><span class="sxs-lookup"><span data-stu-id="d5b24-128">In the Hierarchy window, select the **PressableButtonHoloLens2**.</span></span> <span data-ttu-id="d5b24-129">在"检查器"窗口中，找到"可 **交互** (脚本) 组件，然后单击 OnClick () 事件下的"+"图标。</span><span class="sxs-lookup"><span data-stu-id="d5b24-129">In the Inspector window, locate the **Interactable (Script)** component and click on + icon under OnClick () event.</span></span>

* <span data-ttu-id="d5b24-130">在"层次结构"窗口中仍选中 **PressableButtonHoloLens2** 对象时，单击"四边形"对象并将其从"层次结构"窗口拖动到刚添加事件的空"无 (对象 **) "** 字段中，使 ButtonParent 对象侦听此按钮中的按钮单击事件：</span><span class="sxs-lookup"><span data-stu-id="d5b24-130">With the **PressableButtonHoloLens2** object still selected in the Hierarchy window, click-and-drag the **Quad** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

* <span data-ttu-id="d5b24-131">单击同一事件的“无函数”下拉列表。</span><span class="sxs-lookup"><span data-stu-id="d5b24-131">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="d5b24-132">然后选择 **"SpatializeOnOff**  >  **SwapSpatialization () "** 以打开和关闭空间音频</span><span class="sxs-lookup"><span data-stu-id="d5b24-132">Then select **SpatializeOnOff** > **SwapSpatialization ()** to turn on and off the Spatial audio</span></span>

![按钮操作设置](images/spatial-audio/spatial-audio-04-section2-step1-3.PNG)

## <a name="congratulations"></a><span data-ttu-id="d5b24-134">祝贺</span><span class="sxs-lookup"><span data-stu-id="d5b24-134">Congratulations</span></span>

<span data-ttu-id="d5b24-135">在本教程中，你已了解如何在运行时启用和禁用空间化，以及如何在应用HoloLens 2 Unity 编辑器中测试应用。</span><span class="sxs-lookup"><span data-stu-id="d5b24-135">In this tutorial, you have learned how to enable and disable spatialization at run time, test out the app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="d5b24-136">在应用中，现在可以单击按钮来激活和停用音频的空间化。</span><span class="sxs-lookup"><span data-stu-id="d5b24-136">In the app, you can now click the button to activate and deactivate spatialization of the audio.</span></span>

<span data-ttu-id="d5b24-137">下一教程将添加混响效果，使声音具有距离感。</span><span class="sxs-lookup"><span data-stu-id="d5b24-137">In the next tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

> [!TIP]
> <span data-ttu-id="d5b24-138">要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。</span><span class="sxs-lookup"><span data-stu-id="d5b24-138">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d5b24-139">下一教程：5.使用混响添加与空间音频的距离</span><span class="sxs-lookup"><span data-stu-id="d5b24-139">Next Tutorial: 5. Using reverb to add distance to spatial audio</span></span>](unity-spatial-audio-ch5.md)
