---
title: 空间音频教程-1。 向项目添加空间音频
description: 将 Microsoft Spatializer 插件添加到 Unity 项目以访问 HoloLens 2 HRTF 硬件卸载。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality，unity，教程，hololens2，空间音频，MRTK，混合现实工具包，UWP，Windows 10，HRTF，head 相关传输函数，回音，Microsoft Spatializer
ms.openlocfilehash: 7d4702a21fccbb18c7c4b07675953c37785ae6db
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580223"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. 将空间音频添加到 Unity 项目

## <a name="overview"></a>概述

欢迎使用 HoloLens2 上 Unity 的空间音频教程。 在本系列教程中，你将了解如何在 HoloLens 2 上使用与头相关的传输功能 (HRTF) 卸载，以及如何在使用 HRTF 卸载时启用回响。

[Microsoft Spatializer GitHub 存储库](https://github.com/microsoft/spatialaudio-unity)包含此教程序列的已完成 Unity 项目。

若要了解如何使用基于 HRTF 的 spatialization 技术来 spatialize 声音，并提供有关其有用时间的建议，请参阅 [空间音效设计](/windows/mixed-reality/spatial-sound-design)。

## <a name="what-is-hrtf-offload"></a>什么是 HRTF 卸载？

使用基于 HRTF 的算法处理音频需要大量的专用计算。 HoloLens 2 包括专用硬件，可以利用这些硬件来避免应用程序处理器的负担，从而将处理基于 HRTF 的算法。  Microsoft spatializer 插件为应用程序提供了一种简单的方法，使应用程序能够利用专用的 HRTF 硬件，使应用程序可以将更多应用程序处理器用于除了空间音频以外的其他操作。

## <a name="objectives"></a>目标

* 导入和启用 Microsoft spatializer 插件
* 启用开发人员工作站上的空间音频

## <a name="prerequisites"></a>必备条件

* 一台 Windows 10 电脑，其中已[安装](../../install-the-tools.md)并配置正确的工具
* 基本 C# 编程知识
* 一个[针对开发配置](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已装载 Unity 2019 LTS 且已添加通用 Windows 平台生成支持模块

我们 **强烈建议** 先完成 [入门](mr-learning-base-01.md) 教程系列，或先熟悉 Unity 和 MRTK，然后再继续。

> [!IMPORTANT]
>
> * 建议对本系列教程使用 Unity 2019 LTS。 这将取代上述链接的先决条件中所述的所有 Unity 版本要求或建议。

## <a name="creating-and-preparing-the-unity-project"></a>创建和准备 Unity 项目

在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。

为此，请先执行[初始化项目和第一个应用程序](mr-learning-base-02.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的说明：

1. [创建 Unity 项目](mr-learning-base-02.md#creating-the-unity-project)并为其指定适当的名称，例如“MRTK 教程”

1. [切换生成平台](mr-learning-base-02.md#configuring-the-unity-project)

1. [导入 TextMeshPro 基本资源](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [导入混合现实工具包](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [配置 Unity 项目](mr-learning-base-02.md#configuring-the-unity-project)

1. [创建和设置场景](mr-learning-base-02.md#creating-and-configuring-the-scene) 并为场景提供一个合适的名称，例如 *SpatialAudio*

然后，按照 [更改空间感知显示选项](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 说明进行操作，以确保场景的 MRTK 配置文件为 **DefaultXRSDKConfigurationProfile** ，并将空间感知网格的显示选项改为 " **封闭**"。

## <a name="adding-microsoft-spatializer-to-the-project"></a>向项目添加 Microsoft Spatializer

下载并导入 Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">SpatialAudio. unitypackage </a>

>[!TIP]
> 有关如何导入 Unity 自定义包的提示，可参阅[导入混合现实工具包](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)中的说明。

## <a name="enable-the-microsoft-spatializer-plugin"></a>启用 Microsoft Spatializer 插件

导入 **Microsoft Spatializer** 后，需要启用它。 打开 **> 项目设置-> 音频**"，然后将 **Spatializer 插件** 更改为" Microsoft Spatializer "。

![显示 spatializer 插件的项目设置](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>启用工作站上的空间音频

在桌面版本的 Windows 上，默认情况下禁用空间音频。 右键单击任务栏中的音量图标即可启用此项。 若要获得有关在 HoloLens 2 上收到的内容的最佳表示，请选择 " **空间音效-> Windows Sonic 用于耳机**"。

![桌面空间音频设置](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> 仅当计划在 Unity 编辑器中测试项目时，才需要此设置。

## <a name="congratulations"></a>祝贺

在本教程中，你将了解如何导入和启用 Microsoft Spatializer 插件，还可以在工作站上启用空间音频了解到。
在下一教程中，你将了解如何在 unity 项目中添加空间音频。

> [!div class="nextstepaction"]
> [下一教程： Spatializing 按钮交互声音](unity-spatial-audio-ch2.md)
