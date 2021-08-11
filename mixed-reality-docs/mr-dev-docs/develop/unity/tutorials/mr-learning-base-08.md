---
title: 使用眼动跟踪
description: 本课程介绍如何将混合现实应用中的眼动跟踪与混合现实工具包 (MRTK) 结合使用。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 眼动跟踪
ms.localizationpriority: high
ms.openlocfilehash: 8a12bf37547466a07cd47e34d7fbc41e88ca87d345e2ef4fcd73b749bdfd0322
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227451"
---
# <a name="8-using-eye-tracking"></a>8.使用眼动跟踪

在本教程中，你将了解如何为 HoloLens 2 启用眼动跟踪，以及在用户查看对象时如何将眼动跟踪添加到对象以触发操作。

> [!NOTE]
> 如果你也要将此项目部署到 HoloLens（第一代），请注意，只有 HoloLens 2 支持眼动跟踪。

## <a name="objectives"></a>目标

* 了解如何为 HoleLens 2 启用眼动跟踪
* 了解如何使用眼动跟踪触发操作

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>确保启用了“眼睛凝视输入”功能

在 Unity 菜单中，选择“混合现实”>“工具包”>“实用工具”>“配置 MRTK 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用眼睛凝视输入功能”是否灰显   ：

![Unity“MRTK 项目配置器”窗口](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> 当你在本系列教程开头配置 Unity 项目时，[应用 MRTK 项目配置器设置](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)指令期间应该已经启用了眼睛凝视输入功能。 但如果未启用此功能，请确保立即启用。

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>在凝视提供者中启用基于眼睛的凝视

在“层次结构”窗口中选择“MixedRealityToolkit”对象，然后在“检查器”窗口中选择“MixedRealityToolkit”>“输入”选项卡，并执行以下步骤 ：

* 克隆 DefaultHoloLens2InputSystemProfile 并为其指定合适的名称，例如 GettingStarted_HoloLens2InputSystemProfile
* 展开“指针”部分
* 克隆 DefaultMixedRealityPointerProfile 并为其指定合适的名称，例如 GettingStarted_MixedRealityPointerProfile
* 找到“凝视设置”部分，并选中“是否启用了眼动跟踪”复选框 

![应用了新创建的配置文件并启用了眼动跟踪的 Unity MixedRealityToolkit 组件](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> 有关如何克隆 MRTK 配置文件的提示，可参阅[配置 MRTK 配置文件](mr-learning-base-03.md)中的说明。

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a>为 Unity 编辑器启用模拟的眼动跟踪

在“层次结构”窗口中，选择“MixedRealityToolkit”对象，然后在“检查器”窗口中，导航到“输入”选项卡，然后执行以下操作 ：

* 展开“输入数据提供者” > “输入模拟服务”部分 
* 克隆 DefaultMixedRealityInputSimulationProfile 并为其指定合适的名称，例如 GettingStarted_MixedRealityInputSimulationProfile
* 找到“眼睛凝视模拟”，并将“默认眼睛凝视模拟模式”设置为“摄像头前轴”  

![选中了 TextMeshPro 对象的 Unity](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a>将眼动跟踪添加到对象

在“层次结构”窗口中，展开“RoverExplorer” > “Buttons”，然后选择全部三个子按钮对象：

![已选中 Button 对象的 Unity](images/mr-learning-base/base-08-section4-step1-1.png)

在三个 Button 对象仍处于选中状态时，在“检查器”窗口中使用“添加组件”按钮将 EyeTrackingTarget 组件添加到所有选定对象 ：

![选中了 TextMeshPro 对象并添加了组件的 Unity](images/mr-learning-base/base-08-section4-step1-2.png)

在“层次结构”窗口中，展开“RoverExplorer” > “Buttons” > “Hints” > “SeeItSayItLabel” > “TextMeshPro”

在“层次结构”窗口中，选择“Hints”按钮对象，然后按以下方式配置“EyeTrackingTarget”组件： 

* 在“On Look At Start ()”事件部分
  * 单击小 + 图标以添加另一个事件
  * 将“Hints”按钮中的“TextMeshPro”对象分配给“None (Object)”字段  
  * 在“无函数”下拉列表中选择“TextMeshPro” > “float fontSize”，以便在触发事件时更新此属性  
  * 将参数设置为 0.06，以将 0.04 的当前字号增加 50%
* 在“On Look Away ()”事件部分
  * 单击小 + 图标以添加另一个事件
  * 将“Hints”按钮中的“TextMeshPro”对象分配给“None (Object)”字段  
  * 在“无函数”下拉列表中选择“TextMeshPro” > “float fontSize”，以便在触发事件时更新此属性  
  * 将参数设置为 0.04 以将字号重置为 0.04

![选中了“提示 TextMeshPro 对象”并配置了 EyeTrackingTarget 组件的 Unity](images/mr-learning-base/base-08-section4-step1-3.png)

对“Explode”和“Reset”按钮对象重复此步骤，为剩余按钮配置眼动跟踪。  

如果你现在进入游戏模式，然后按住鼠标右键，同时移动鼠标，直到凝视命中的某个按钮出现，你将看到文本字号增加了 50%，而鼠标移走时字号将重置回其原始大小：

![视线对准眼动跟踪目标“分解”按钮标签的 Unity“播放”模式分屏视图](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a>祝贺

在本教程中，你了解了如何为 HoloLens 2 启用眼动跟踪，以及在用户查看对象时如何将眼动跟踪添加到对象以触发操作。

> [!div class="nextstepaction"]
> [下一教程：9.使用语音命令](mr-learning-base-09.md)
