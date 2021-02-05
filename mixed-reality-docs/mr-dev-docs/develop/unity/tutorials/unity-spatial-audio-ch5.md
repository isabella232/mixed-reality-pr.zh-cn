---
title: 空间音频教程-5。 使用混响为空间音频添加距离感
description: 添加回音效果，提高对空间音频的距离变体的意义。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality，unity，教程，hololens2，空间音频，MRTK，混合现实工具包，UWP，Windows 10，HRTF，头相关传输函数，回音，Microsoft Spatializer，音频混合器，SFX 回音
ms.openlocfilehash: f7a5270d969f2e462db0244bd6c68b99347ae1a7
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590719"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a>5.使用混响为空间音频添加距离感

## <a name="overview"></a>概述

在上一教程中，你已为声音添加了 spatialization，以使其在本教程中有一个方向，你将添加一个回音效果，以便为声音提供距离。

## <a name="objectives"></a>目标

* 通过添加回音来改善声音源的感知距离。
* 使用侦听器与全息图的距离控制声音的已知距离。

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>添加混音器组和回音效果

在 [Spatializing button 交互声音教程](unity-spatial-audio-ch2.md)中，我们添加了一个混音器。 混音器默认包含一个名为 **Master** 的 **组**。 因为我们只是想要将回音效果应用到一些声音，接下来要为这些声音添加另一个组。 若要添加组，请在 **音频混合器** 中右键单击主组，选择 " **添加子组** " 并为 " _会议室效果_" 提供合适的名称：

![添加子组](images/spatial-audio/spatial-audio-05-section1-step1-1.png)

每个 **组** 都有自己的效果集。 通过在新组中单击 " **添加 ...** " 并选择 " **SFX 回音**"，向新组添加回音效果：

![添加 SFX 回音](images/spatial-audio/spatial-audio-05-section1-step1-2.png)

在音频术语中，原始、unreverberated 的音频称为 _晾干路径_，筛选后的音频被称为 _湿路径_。 这两个路径都发送到音频输出，在此组合中，其相对强度称为 _湿/干燥混合_。 湿/干燥混合会对距离的理解产生很大影响。

**SFX 回音** 包含用于在效果内调整湿/干燥混合的控件。 由于 **Microsoft Spatializer** 插件处理晾干路径，因此，我们只为湿路径使用 **SFX 回音** 。 在 **SFX 回音** 的 "检查器" 窗格上：

* 将 " **晾干级别** " 属性设置为最低 (-10000 mB) 
* 将 " **房间" 属性** 设置为最高 (0 mB) 

![SFX 回音属性](images/spatial-audio/spatial-audio-05-section1-step1-3.png)

其他设置控制模拟房间的感觉。 具体而言， **衰减时间** 与感知到的空间大小相关。

## <a name="enable-reverb-on-the-video-playback"></a>启用视频播放时播放回音

在音频源上启用回音的步骤有两个：

* 将 **音频源** 路由到相应的 **组**
* 设置 **Microsoft Spatializer** 插件以将音频传递到 **组** 进行处理

在以下步骤中，你将调整脚本以控制音频路由，并附加与 **Microsoft Spatializer** 插件一起提供的控制脚本，将数据送入回音。

在层次结构中选择的 **四** 个步骤中，单击 "检查器" 窗口上的 "**添加组件**"，并将 "**房间效果" 发送级别 (脚本)**

![添加发送级别脚本](images/spatial-audio/spatial-audio-05-section2-step1-1.png)

> [!NOTE]
> 除非你启用 **Microsoft Spatializer** 插件的 **会议室效果发送级别** 功能，否则它不会将任何音频发送回 Unity 音频引擎以进行有效处理。

" **房间效果发送级别** " 组件包括一个图形控件，该控件设置发送到 Unity 音频引擎以进行回音处理的音频级别。 若要打开图形控件，请单击 **房间效果发送级别**。  单击并向下拖动绿色曲线，将级别设置为30dB：

![调整回音曲线](images/spatial-audio/spatial-audio-05-section2-step1-2.png)

接下来，取消注释 **SpatializeOnOff** 脚本中的4个注释行。 该脚本现在将如下所示：

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

取消注释这些行后，它会将两个属性添加到 **SpatializeOnOff 脚本** 的检查器中。 在 **四** 个 **SpatializeOnOff** 组件的检查器窗口上分配它们。

在层次结构中，如果仍在层次结构中选择了 Quad 对象，请在检查器窗口中找到 **SpatializeOnOff 脚本** 组件，并：

* 将 " **房间效果组** " 属性设置为新的 "房间效果" 混音器组
* 将 " **主组** " 属性设置为 "主混音器" 组

![Spatialize 扩展](images/spatial-audio/spatial-audio-05-section2-step1-3.png)

## <a name="congratulations"></a>祝贺

已完成适用于 Unity 的 HoloLens 2 空间音频教程。 试用 HoloLens 2 或 Unity 上的应用。 单击应用中的按钮以激活 spatialization 时，该脚本会将视频的音频路由到房间效果组以添加回音。 切换到立体声时，它会将音频路由到主组，并避免添加回音。

> [!TIP]
> 要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。
