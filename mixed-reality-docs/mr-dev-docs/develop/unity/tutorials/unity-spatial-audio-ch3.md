---
title: 空间音频教程-3。 将视频中的音频空间化
description: 将视频资产导入到 Unity 项目，并 spatialize 视频中的音频。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality，unity，教程，hololens2，空间音频，MRTK，混合现实工具包，UWP，Windows 10，HRTF，头相关传输函数，回音，Microsoft Spatializer，视频导入，视频播放器
ms.openlocfilehash: 6474da522e650d23349a21c3deeac00222b8ce93
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578557"
---
# <a name="3-spatializing-audio-from-a-video"></a>3.将视频中的音频空间化

## <a name="overview"></a>概述

在本教程中，您将学习如何从视频源 spatialize 音频并在 unity 编辑器和 HoloLens 2 中对此进行测试。

## <a name="objectives"></a>目标

* 导入视频并添加视频播放器
* 播放视频到 quadrangle
* 将音频从视频路由到 quadrangle，并 spatialize 音频

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a>导入视频并将视频播放器添加到场景

在本教程中，你可以从空间音频示例项目使用 [此视频](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) 。

将视频导入 unity 项目。 在 Unity 菜单中，选择 "**资产**  >  **导入新资产** 
 ![ 导入资产"](images/spatial-audio/spatial-audio-03-section1-step1-1.png)

在 " **导入新资产 ...** " 窗口中，选择已下载的 **Microsoft HoloLens 空间 PTPvx7mDon4** 文件，并单击 " **打开** " 按钮将资产导入到项目中：

![选择资产](images/spatial-audio/spatial-audio-03-section1-step1-2.png)

调整视频剪辑的质量设置可以确保在 HoloLens 2 上顺畅地播放。 在 " **项目** " 窗口中选择视频文件，并在视频文件的 "检查器" 窗口中， **覆盖** **Windows 应用商店应用** 的设置，并执行以下操作：

* 启用 **转码**
* 将 **编解码器** 设置为 H264
* 将 **比特率模式** 设置为低
* 将 **空间质量** 设置为中等空间质量

完成这些调整后，单击 "应用" 以更改视频剪辑的质量设置。

![视频属性更改](images/spatial-audio/spatial-audio-03-section1-step1-3.png)

右键单击层次结构，选择 "**视频**  >  **视频播放器**" 添加视频播放器组件。

![添加视频播放器](images/spatial-audio/spatial-audio-03-section1-step1-4.png)

## <a name="play-video-onto-a-quadrangle"></a>播放视频到 quadrangle

**视频播放器** 对象需要纹理的游戏对象来渲染视频。

右键单击层次结构，选择 " **3d 对象**  >  **四** 个"，创建一个四核，并按如下所示配置 **转换** 组件：

* **Position**： X = 0、Y = 0、Z = 2
* **旋转**：X = 0, Y = 0, Z = 0
* **Scale**： X = 1.28，Y = 0.72，Z = 1

![添加四](images/spatial-audio/spatial-audio-03-section2-step1-1.png)

现在，需要使用视频对 **四核** 进行着色，在 "**项目**" 窗口中，右键单击并选择 "**创建**  >  **渲染纹理**" 以创建渲染纹理组件，为渲染纹理输入合适的名称（例如，_空间音频纹理_）：

![创建着色纹理](images/spatial-audio/spatial-audio-03-section2-step1-2.png)

选择 " **渲染纹理** "，然后在 "检查器" 窗口中，设置 " **Size** " 属性以匹配视频的 "1280x720 的本机分辨率"。 然后，若要确保在 HoloLens 2 上呈现良好的性能，请将 **深度缓冲区** 属性设置为 **至少16位深度**。

![呈现纹理属性](images/spatial-audio/spatial-audio-03-section2-step1-3.png)

接下来，使用创建的呈现纹理 **空间音频纹理** 作为 **四** 个的纹理：

1. 将 **空间音频纹理** 从 " **项目** " 窗口拖到层次结构中的 " **四** 个"，将渲染纹理添加到 "四核"
2. 若要在 HoloLens 2 上确保良好的性能，请在层次结构中选择四个四个，并在着色器的检查器窗口中选择 **混合现实工具包**  >  **标准** 着色器。

![四纹理属性](images/spatial-audio/spatial-audio-03-section2-step1-4.png)

若要设置 **视频播放机** 和 **渲染纹理** 以播放视频剪辑，请在 **层次结构** 中选择 **视频播放器**，然后在 "**检查器**" 窗口中选择

* 将 **视频剪辑** 属性设置为下载的视频文件 "Microsoft PTPvx7mDon4"
* 选中 " **循环** " 复选框
* 将 **目标纹理** 设置为新的呈现纹理 **空间音频纹理**

![视频播放器属性](images/spatial-audio/spatial-audio-03-section2-step1-5.png)

## <a name="spatialize-the-audio-from-the-video"></a>Spatialize 视频中的音频

在 "层次结构" 窗口中，选择 " **四** 个对象"，然后在 "检查器" 窗口中，使用 " **添加组件** " 按钮添加 **音频源** ，从视频将音频源路由到该视频源。

在 **音频源** 中：

* 将 **输出** 设置为 **空间音频混合器**
* 选中 " **Spatialize** " 框
* 将 **空间混合** 滑块移动到 1 (3d) 

![四核音频源检查器](images/spatial-audio/spatial-audio-03-section3-step1-1.png)

若要将视频播放机设置为将音频源路由到 **音频源**，请在 "层次结构" 窗口中选择 **视频播放器** ，然后在 "检查器" 中的 "视频播放器" 对象中执行以下更改。

* 将 **音频输出模式** 设置为 **音频源**
* 将 " **音频源** " 属性设置为 **四**

![视频播放器设置音频源](images/spatial-audio/spatial-audio-03-section3-step1-2.png)

> [!TIP]
> 要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。

## <a name="congratulations"></a>祝贺

在本教程中，你已学习如何从视频源 spatialize 音频，尝试在 HoloLens 2 上或在 Unity 编辑器中运行你的应用。 你会看到并听到视频，视频中的音频是 spatialized 的。

在下一教程中，你将了解如何在运行时启用和禁用 spatialization

> [!div class="nextstepaction"]
> [下一教程： 4. 在运行时启用和禁用 spatialization](unity-spatial-audio-ch4.md)
