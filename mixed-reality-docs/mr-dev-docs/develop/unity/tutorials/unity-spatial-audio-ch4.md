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
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. 在运行时启用和禁用 spatialization

## <a name="overview"></a>概述

在本教程中，您将学习如何在运行时启用和禁用 spatialization，并在 unity 编辑器和 HoloLens 2 中对此进行测试。

## <a name="objectives"></a>目标

* 添加新脚本以控制游戏对象上的 spatialization
* 从按钮操作驱动 spatialization 控件脚本

## <a name="add-spatialization-control-script"></a>添加 spatialization 控件脚本

 在项目窗口中右键单击，然后选择 "**创建**  >  **c # 脚本**" 以创建新的 c # 脚本，为脚本输入合适的名称，例如， _SpatializeOnOff_：

![创建脚本](images/spatial-audio/spatial-audio-04-section1-step1-1.png)

双击 "项目" 窗口中的脚本，在 Visual Studio 中将其打开。 将默认脚本内容替换为以下内容：

> [!NOTE]
> 脚本的几行被注释掉。以下各行将在 [下一章中取消注释：使用回音向空间音频添加距离](unity-spatial-audio-ch5.md)。

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
> 若要启用或禁用 spatialization，此脚本只会调整 **spatialBlend** 属性，使 **spatialization** 属性保持启用状态。 在此模式下，Unity 仍会应用 **卷** 曲线。 否则，如果用户在远距离源时禁用了 spatialization，则会听到音量突然增加。
> 如果希望完全禁用 spatialization，请修改脚本，同时调整 **SourceObject** 变量的 **spatialization** 布尔值属性。

## <a name="attach-your-script-and-drive-it-from-the-button"></a>附加脚本，然后从按钮中进行驱动器

选择层次结构中的 **四** 个，并在 "检查器" 窗口中，使用 "添加组件" 按钮添加 **SpatializeOnOff (脚本)**

![将脚本添加到四个](images/spatial-audio/spatial-audio-04-section2-step1-1.png)

在层次结构中找到 **PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**。

如果仍在层次结构中选择了 **Quad** 对象，则在 "检查器" 窗口中，找到 " **Spatialize On Off" (Script)** Component 并拖放 PressableButtonHoloLens2 的 **TextMeshPro** 组件。

![在层次结构中查找 PressableButtonHoloLens2 对象](images/spatial-audio/spatial-audio-04-section2-step1-2.png)

若要将按钮设置为在释放按钮时调用 **SpatializeOnOff** 脚本，需要配置种不可交互脚本。

在 "层次结构" 窗口中，选择 " **PressableButtonHoloLens2**"。 在 "检查器" 窗口中，找到 **种不可交互 (Script)** 组件，并单击 OnClick ( # A3 事件下的 + 图标。

* 如果仍在 "层次结构" 窗口中选择 "PressableButtonHoloLens2" 对象，请在 "层次结构" 窗口中单击 "  "，并将 **该对象从**"层次结构" 窗口中拖到 "空 **None (") 对象** 中，然后将 ButtonParent 对象侦听此按钮中的按钮单击事件：

* 单击同一事件的“无函数”下拉列表。 然后选择 **SpatializeOnOff**  >  **SwapSpatialization ( # B1** 以打开和关闭空间音频

![按钮操作设置](images/spatial-audio/spatial-audio-04-section2-step1-3.png)

## <a name="congratulations"></a>祝贺

在本教程中，已学习了如何在运行时启用和禁用 spatialization、在 HoloLens 2 上或在 Unity 编辑器中测试应用程序。 在应用程序中，你现在可以单击该按钮以激活和停用 spatialization 的音频。

在下一教程中，你将添加一个回音效果，以便为声音指定距离。

> [!TIP]
> 要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。

> [!div class="nextstepaction"]
> [下一教程： 5. 使用回音向空间音频添加距离](unity-spatial-audio-ch5.md)
