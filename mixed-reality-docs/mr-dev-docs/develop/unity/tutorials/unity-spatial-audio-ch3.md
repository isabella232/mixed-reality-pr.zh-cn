---
title: 空间音频教程 - 3. 将视频中的音频空间化
description: 将视频资产导入 Unity 项目，并空间化视频中的音频。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实， unity， 教程， hololens2， 空间音频， MRTK， 混合现实工具包， UWP， Windows 10， HRTF， 与头部相关的传输函数， 混响， Microsoft Spatializer， 视频导入， 视频播放器
ms.openlocfilehash: 2926301aac9db67d3e72b0511600720c24e5965f52a23faa1230c381a47c9b90
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202886"
---
# <a name="3-spatializing-audio-from-a-video"></a>3.将视频中的音频空间化

## <a name="overview"></a>概述

在本教程中，你将了解如何从视频源对音频进行空间化，以及如何在 unity 编辑器和HoloLens 2。

## <a name="objectives"></a>目标

* 导入视频并添加视频播放器
* 在四边形图上播放视频
* 将音频从视频路由到四边形，并空间化音频

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a>导入视频，将视频播放器添加到场景中

对于本教程，请使用空间 [音频示例](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) 项目中的此视频。

将视频导入 unity 项目。 在 Unity 菜单中，选择 **"资产**  >  **导入""新建资产** 
 ![ ""导入资产"](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)

在"**导入新资产..."** 窗口中，选择Microsoft HoloLens **空间声音 - PTPvx7mDon4** 文件，然后单击"打开"按钮将资产导入项目：

![选择资产](images/spatial-audio/spatial-audio-03-section1-step1-2.PNG)

调整视频剪辑上的质量设置可确保在视频剪辑上HoloLens 2。 在"应用"窗口中选择Project文件，在视频文件的"检查器"窗口中，Windows **应用商店应用的设置**，然后： 

* 启用 **转码**
* 将 **编解码器设置为** H264
* 将 **比特率模式设置为** 低
* 将 **空间质量设置为** 中等空间质量

完成这些调整后，单击"应用"以更改视频剪辑的质量设置。

![视频属性更改](images/spatial-audio/spatial-audio-03-section1-step1-3.PNG)

右键单击"层次结构"，选择 **"**  >  **视频播放器**"以添加视频播放器组件。

![添加视频播放器](images/spatial-audio/spatial-audio-03-section1-step1-4.PNG)

## <a name="play-video-onto-a-quadrangle"></a>在四边形图上播放视频

Video **Player** 对象需要纹理游戏对象来呈现视频。

右键单击"层次结构"，选择 **"三维对象** 四边形"以创建四边形  >  并配置 **其转换** 组件，如下所示：

* **位置**：X = 0，Y = 0，Z = 2
* **旋转**：X = 0, Y = 0, Z = 0
* **小数** 位：X = 1.28，Y = 0.72，Z = 1

![添加四边形](images/spatial-audio/spatial-audio-03-section2-step1-1.PNG)

现在，你需要使用视频对四边形进行纹理处理，在 **Project** 窗口中，右键单击并选择"创建渲染纹理"以创建呈现纹理组件，为"呈现纹理"输入适当的名称，例如"空间音频  >  _纹理"：_

![创建呈现纹理](images/spatial-audio/spatial-audio-03-section2-step1-2.PNG)

选择" **呈现纹理"，** 在"检查器"窗口中设置 **"大小** "属性，以匹配视频的本机分辨率 1280x720。 然后，为了确保在上获得良好的呈现HoloLens 2，**将"深度** 缓冲区"属性设置为 **至少 16 位深度**。

![呈现纹理属性](images/spatial-audio/spatial-audio-03-section2-step1-3.PNG)

接下来，使用创建的渲染纹理 **空间音频纹理** 作为四边形 **的纹理**：

1. 将 **空间音频纹理****从Project** 窗口拖到层次结构中的四边形上，以将渲染纹理添加到四边形
2. 若要确保着色器的性能HoloLens 2，请在"层次结构"中选择"四边形"，在着色器"检查器"窗口中选择"混合现实  >  **"Toolkit"标准** 着色器"。

![四边形纹理属性](images/spatial-audio/spatial-audio-03-section2-step1-4.PNG)

若要设置 **"视频播放器****"** 和"渲染纹理"以播放视频剪辑，请在"层次结构"和"检查器"窗口中选择 **"视频播放器**"，

* 将"**视频剪辑"** 属性设置为下载的视频文件"Microsoft HoloLens - 空间声音 PTPvx7mDon4"
* 选中" **循环"** 复选框
* 将 **"目标纹理** "设置为新的渲染纹理 **空间音频纹理**

![视频播放器属性](images/spatial-audio/spatial-audio-03-section2-step1-5.PNG)

## <a name="spatialize-the-audio-from-the-video"></a>将视频中的音频空间化

在"层次结构"窗口中，选择"**四** 边形对象"，然后在"检查器"窗口中，使用"添加组件"按钮添加音频源，将音频从视频路由到其中。

在 **音频源中**：

* 将 **"输出**"**设置为"空间音频Mixer**
* 选中" **空间化"** 框
* 将" **空间混合"** 滑块移动到 1 (3D) 

![四边形音频源检查器](images/spatial-audio/spatial-audio-03-section3-step1-1.PNG)

若要将视频播放器设置为将其音频路由到音频源，请在"层次结构"窗口中选择"视频播放器"，在检查器中的"视频播放器"对象中执行以下更改。

* 将"**音频输出模式"设置为****"音频源"**
* 将 **"音频源"** 属性设置为四 **边形**

![视频播放器集音频源](images/spatial-audio/spatial-audio-03-section3-step1-2.PNG)

> [!TIP]
> 要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。

## <a name="congratulations"></a>祝贺

在本教程中，你已了解如何从视频源对音频进行空间化尝试在 HoloLens 2 Unity 编辑器中试用应用。 你将观看并听到视频，视频中的音频已空间化。

下一教程将介绍如何启用和禁用运行时空间化

> [!div class="nextstepaction"]
> [下一教程：4.启用和禁用运行时空间化](unity-spatial-audio-ch4.md)
