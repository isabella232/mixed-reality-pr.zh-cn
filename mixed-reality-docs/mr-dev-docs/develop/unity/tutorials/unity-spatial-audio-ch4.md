---
title: 空间音频教程 - 4. 在运行时启用和禁用空间音频
description: 使用按钮可启用和禁用音频运行时的空间化。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实， unity， 教程， hololens2， 空间音频， MRTK， 混合现实工具包， UWP， Windows 10， HRTF， 头部相关的传输函数， 混响， Microsoft 空间化程序
ms.openlocfilehash: 2599e2f360afa4518102ab9535608e9d378264ae87f84a36823d460f934d6a05
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213209"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4.运行时启用和禁用空间化

## <a name="overview"></a>概述

在本教程中，你将了解如何运行时启用和禁用空间化，以及如何在 unity 编辑器和 HoloLens 2。

## <a name="objectives"></a>目标

* 添加新脚本以控制游戏对象上的空间化
* 通过按钮操作驱动空间化控制脚本

## <a name="add-spatialization-control-script"></a>添加空间化控制脚本

 右键单击"Project"，然后选择"创建C# 脚本"以创建新的 C# 脚本，输入脚本的合适名称，例如  >  _SpatializeOnOff_：

![创建脚本](images/spatial-audio/spatial-audio-04-section1-step1-1.PNG)

双击"脚本"窗口中的Project，以在Visual Studio。 将默认脚本内容替换为以下内容：

> [!NOTE]
> 脚本的几个行被注释掉。下一章：使用混响添加空间音频 的距离中 [将取消注释这些行](unity-spatial-audio-ch5.md)。

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
> 若要启用或禁用空间化，脚本仅调整 **spatialBlend** 属性，使 **空间化属性** 保留为启用状态。 在此模式下，Unity 仍应用"卷 **"** 曲线。 否则，如果用户在远离源时禁用空间化，他们将听到卷突然增加。
> 如果希望完全禁用空间化，请修改脚本以同时调整 **SourceObject** 变量的空间化布尔属性。 

## <a name="attach-your-script-and-drive-it-from-the-button"></a>附加脚本，然后从按钮驱动它

在 **"** 层次结构"中选择"四边形"，在"检查器"窗口中，使用"添加组件"按钮添加 **SpatializeOnOff (脚本)**

![将脚本添加到四边形](images/spatial-audio/spatial-audio-04-section2-step1-1.PNG)

在"层次结构"中，找到 **PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**。

在" **层次结构** "中仍选中 Quad 对象时，在"检查器"窗口中，找到 **"Spatialize On (Script) "** 组件，然后拖放 PressableButtonHoloLens2 的 **TextMeshPro** 组件。

![在层次结构中查找 PressableButtonHoloLens2 对象](images/spatial-audio/spatial-audio-04-section2-step1-2.PNG)

若要设置按钮以在按钮释放时调用 **SpatializeOnOff** 脚本，需要配置可交互脚本。

在"层次结构"窗口中，选择 **"PressableButtonHoloLens2"。** 在"检查器"窗口中，找到"可 **交互** (脚本) 组件，然后单击 OnClick () 事件下的"+"图标。

* 在"层次结构"窗口中仍选中 **PressableButtonHoloLens2** 对象时，单击"四边形"对象并将其从"层次结构"窗口拖动到刚添加事件的空"无 (对象 **) "** 字段中，使 ButtonParent 对象侦听此按钮中的按钮单击事件：

* 单击同一事件的“无函数”下拉列表。 然后选择 **"SpatializeOnOff**  >  **SwapSpatialization () "** 以打开和关闭空间音频

![按钮操作设置](images/spatial-audio/spatial-audio-04-section2-step1-3.PNG)

## <a name="congratulations"></a>祝贺

本教程介绍了如何启用和禁用运行时空间化，以及如何在 HoloLens 2 Unity 编辑器中测试应用。 在应用中，现在可以单击按钮来激活和停用音频的空间化。

下一教程将添加混响效果，使声音具有距离感。

> [!TIP]
> 要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。

> [!div class="nextstepaction"]
> [下一教程：5.使用混响添加与空间音频的距离](unity-spatial-audio-ch5.md)
