---
title: 空间音频教程 - 1. 向项目添加空间音频
description: 将 Microsoft Spatializer 插件添加到 Unity 项目，以HoloLens 2 HRTF 硬件卸载。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实， unity， 教程， hololens2， 空间音频， MRTK， 混合现实工具包， UWP， Windows 10， HRTF， 头部相关的传输函数， 混响， Microsoft 空间化程序
ms.openlocfilehash: a61e709f24c2162bc6e6e1248de658128674d49e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175372"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1.将空间音频添加到 Unity 项目

## <a name="overview"></a>概述

欢迎使用 HoloLens2 上的 Unity 空间音频教程。 通过本教程系列，你将了解如何使用与头相关的传输函数 (HRTF) 卸载 HoloLens 2 和使用 HRTF 卸载时如何启用混响。

[Microsoft Spatializer GitHub](https://github.com/microsoft/spatialaudio-unity)存储库具有本教程序列中已完成的 Unity 项目。

若要了解使用基于 HRTF 的空间化技术对声音进行空间化的含义，以及有关何时有用的建议，请参阅 [空间声音设计](/windows/mixed-reality/spatial-sound-design)。

## <a name="what-is-hrtf-offload"></a>什么是 HRTF 卸载？

使用基于 HRTF 的算法处理音频需要大量专用计算。 HoloLens 2包括专用硬件，可以利用这些硬件来避免给应用程序处理器造成负担，从而"卸载"基于 HRTF 的算法的处理。  Microsoft 空间化程序插件为应用程序提供了一种简单的方式来利用专用 HRTF 硬件，以便应用程序可以使用更多应用程序处理器执行空间音频外的操作。

## <a name="objectives"></a>目标

* 导入和启用 Microsoft 空间化程序插件
* 在开发人员工作站上启用空间音频

## <a name="prerequisites"></a>必备条件

* 一台 Windows 10 电脑，其中已[安装](../../install-the-tools.md)并配置正确的工具
* 基本 C# 编程知识
* 一个[针对开发配置](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">已装载</a>Unity 2020/2019 LTS 且添加了通用 Windows 平台生成支持模块的 Unity Hub

**强烈建议先完成** 入门教程系列，[](mr-learning-base-01.md)或在继续操作之前具有一些基本的 Unity 和 MRTK 经验。

> [!Important]
> 如果使用的是 Open XR 或 Windows XR 插件，则本教程系列支持 Unity 2020 LTS (当前为 2020.3.x) ;如果使用旧版 WSA 或 Windows XR 插件，则支持 Unity 2019 LTS (当前为 2019.4.x) 。 这将取代上述链接的先决条件中所述的任何 Unity 版本要求。

## <a name="creating-and-preparing-the-unity-project"></a>创建和准备 Unity 项目

在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。

为此，请先执行[初始化项目和第一个应用程序](mr-learning-base-02.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的说明：

1. [创建 Unity 项目](mr-learning-base-02.md#creating-the-unity-project)并为其指定适当的名称，例如“MRTK 教程”
2. [切换生成平台](mr-learning-base-02.md#configuring-the-unity-project)
3. [导入 TextMeshPro 基本资源](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [导入混合现实Toolkit配置 Unity 项目](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [创建和配置场景，](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) 为场景指定合适的名称，例如 *SpatialAudio*

然后按照 [更改](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)空间感知显示选项说明操作，确保场景的 MRTK 配置文件为 **DefaultHoloLens2ConfigurationProfile，** 然后将空间感知网格的显示选项更改为"遮挡 **"。**

## <a name="adding-microsoft-spatializer-to-the-project"></a>将 Microsoft Spatializer 添加到Project

下载并导入 Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a>

>[!TIP]
> 有关如何导入 Unity 自定义包的提示，可参阅[导入教程资产](mr-learning-base-04.md#importing-the-tutorial-assets)说明。

## <a name="enable-the-microsoft-spatializer-plugin"></a>启用 Microsoft Spatializer 插件

将 Microsoft Spatializer 导入 Unity 项目后，**将显示 MRTK Project Configurator** 窗口，使用"音频空间化程序"下拉列表选择 **Microsoft Spatializer，** 然后单击"应用"按钮应用设置：

![MRTK Project配置器](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

还可以手动启用 Microsoft 空间化程序：打开"编辑 **"-> Project 设置 -> 音频，将"空间化程序插件"****更改为"Microsoft** Spatializer"。

![Project 设置显示空间化程序插件](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a>在工作站上启用空间音频

在桌面版本的 Windows，空间音频默认处于禁用状态。 通过右键单击任务栏中的卷图标来启用它。 若要以最佳方式表示在音频中听到HoloLens 2，请选择"空间声音 **-> 用于耳机的 Windows Sonic"。**

![桌面空间音频设置](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> 只有在计划在 Unity 编辑器中测试项目时，才需要此设置。

## <a name="congratulations"></a>祝贺

本教程介绍了如何导入和启用 Microsoft Spatializer 插件，以及如何在工作站上启用空间音频。
下一教程介绍如何在 unity 项目中添加空间音频。

> [!div class="nextstepaction"]
> [下一教程：2.将按钮交互声音空间化](unity-spatial-audio-ch2.md)
