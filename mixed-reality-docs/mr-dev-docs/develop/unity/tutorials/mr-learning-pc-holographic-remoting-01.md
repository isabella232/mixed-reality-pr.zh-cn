---
title: 电脑全息远程处理入门
description: 完成本课程可以了解如何将混合现实应用程序从电脑远程地流式传输到 HoloLens 2。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 电脑全息远程处理, 工具提示, 眼动跟踪
ms.localizationpriority: high
ms.openlocfilehash: 05831ff19a998bd5e99ab5d20c3fb045a09c55e9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175429"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a>1.电脑全息远程处理入门

欢迎学习 HoloLens 2 教程。 该系列由两部分组成，其中你将学习如何创建混合现实体验演示，并了解如何创建用于全息远程处理的电脑应用。

本教程介绍如何创建混合现实体验。 它将演示 UI 元素、3D 模型操作、模型剪辑和眼动跟踪功能。

在[创建全息远程处理应用程序](mr-learning-pc-holographic-remoting-02.md)（第二篇教程）中，你将学习如何创建用于全息远程处理的电脑应用。 你还可随时连接到 HoloLens 2，从而在混合现实中直观呈现 3D 内容。

## <a name="objectives"></a>目标

* 导入资产并设置场景
* 使用 UI 元素和按钮来与全息影像交互
* 为剪辑功能配置3D 对象
* 了解如何通过眼动跟踪激活工具提示

## <a name="prerequisites"></a>必备条件

* 一台 Windows 10 电脑，其中已[安装](../../install-the-tools.md)并配置正确的工具
* 基本 C# 编程知识
* 一个[针对开发配置](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已装载 Unity 2020/2019 LTS 且已添加通用 Windows 平台生成支持模块

继续学习之前，强烈建议完成[入门](mr-learning-base-01.md)教程系列，或者具备一些使用 Unity 和 MRTK 的基本经验。

> [!IMPORTANT]
> * 本教程系列支持 Unity 2020 LTS（当前版本 2020.3.x）（如果您使用 Open XR）和 Unity 2019 LTS（当前版本 2019.4.x）（如果您使用旧版 WSA）。这会取代上文必备条件链接中所述的任何 Unity 版本要求。

## <a name="creating-and-preparing-the-unity-project"></a>创建和准备 Unity 项目

在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。

为此，请先执行[初始化项目和第一个应用程序](mr-learning-base-02.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的说明：

1. [创建 Unity 项目](mr-learning-base-02.md#creating-the-unity-project)并为其指定适当的名称，例如“MRTK 教程”
2. [切换生成平台](mr-learning-base-02.md#switching-the-build-platform)
3. [导入 TextMeshPro 基本资源](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [导入混合现实工具包和配置 Unity 项目](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [创建和设置场景](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)，并为场景提供一个合适的名称，例如“电脑全息远程处理”

然后，按照[更改空间感知显示选项](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)的说明，将场景的 MRTK 配置配置文件更改为“DefaultHoloLens2ConfigurationProfile”。 将空间感知网格的显示选项更改为“遮挡”。

## <a name="importing-the-tutorial-assets"></a>导入教程资产

[!INCLUDE[](includes/importing-tutorial-assets-pc-holographic-remoting.md)]

## <a name="configuring-and-preparing-the-scene"></a>配置和准备场景

在本部分，你将通过添加一些教程预制件来准备场景。

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.PCHolograhicRemoting” > “预制件”文件夹  。 在按住 Ctrl 按钮时单击下面 6 个预制件。

* ButtonParent
* ClippingObjects
* HandSpatialMapButton
* 说明
* ModelParent
* 平台

![显示了要添加到所选场景的预制件的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

将这些模型从预制件文件夹拖放到“层次结构”窗口。

![新增的预制件仍处于选中状态的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

若要将焦点置于场景中的对象上，可双击 ModelParent 对象，然后再次放大一些：

![ModelParent 对象处于对焦状态的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> 如果在场景中看到大图标（例如带边框的“T”图标会分散注意力），可<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">将调节器 (Gizmos) 切换</a>到关闭位置来隐藏这些图标。

## <a name="configuring-the-buttons-to-operate-the-scene"></a>配置按钮以操作场景

在本部分，你将向场景中添加脚本来创建按钮事件，从而演示模型切换和剪辑功能的基本原理。

### <a name="1-configuring-the-interactable-script-component"></a>1.配置“可交互(脚本)”组件

在“层次结构”窗口中，展开 ButtonParent 对象并选择“NextButton” 。 在检查器窗口中，找到“可交互(脚本)”组件，然后单击 OnClick () 事件下的 + 图标  。

![添加了 Nextbutton OnClick 事件的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

在“层次结构”窗口中仍选中 NextButton 对象的情况下，单击“层次结构”窗口中的 ButtonParent 对象并将其拖放到刚刚添加的事件的空“无(对象)”字段中，使 ButtonParent 对象侦听此按钮的按钮单击事件  ：

![配置了 NextButton OnClick 事件侦听器的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

单击同一事件的“无函数”下拉列表。 然后选择“ViewButtonControl” >  NextModel ()，将 NextModel () 函数设置为从该按钮触发按钮按下事件时触发的操作  ：

![具有 NextButton OnClick 事件操作选择路径的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a>2.配置其余的按钮

对于剩余的每个按钮，请完成上述的过程，将函数分配给“OnClick ()”事件：

* 对于 PreviousButton 对象，请分配“ViewButtonControl”>“PreviousModel ()”函数 。

* 对于 ClippingButton，请选择“ToggleButton” > “ToggleClipping ()”函数 。

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a>3.配置“视图按钮控件(脚本)”和“切换按钮(脚本)”组件

现在根据配置，你的按钮会演示模型切换和剪辑功能。 现可向脚本中添加 3D 模型和剪辑对象。

我们提供了 6 种不同的 3D 模型用于演示，展开 ModelParentobject 可公开这些 3D 模型。

在“层次结构”窗口中仍选中 ButtonParent 对象的情况下，在检查器窗口中找到“视图按钮控件(脚本)”组件并展开“模型”变量 。

在“大小”字段中，输入要在场景中拥有的 3D 模型的数量。 在本例中，为 6 个模型。 它将创建用于添加新 3D 模型的字段。

![具有 ViewButtonControl 脚本组件字段的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

将 ModelParent 对象的每个子对象拖放到这些字段中。

![配置了 ViewButtonControl 脚本组件字段的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

将 ClippingObjects 对象从“层次结构”窗口拖放到“切换按钮(脚本)”组件的“剪辑对象”字段  。
>[!NOTE]
>仅保留按钮父对象。

![配置了 ToggleButton 脚本组件字段的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

在“层次结构”窗口中，选择 ClippingObjects 预制件，并在检查器窗口中启用它来打开剪辑对象。

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a>配置剪辑对象以启用剪辑功能

在本部分中，你将向单个剪辑对象添加 MarsCuriosityRover 对象的子对象渲染器，演示对 MarsCuriosityRover 模型的剪辑。

在“层次结构”窗口中，展开 ClippingObjects 对象，显示你将在此项目中使用的 3 个不同的剪辑对象。

若要配置 ClippingSphere 对象，请单击它，然后在检查器窗口中找到“剪辑球体(脚本)”组件 。 在“大小”字段中输入需要为 3D 模型添加的渲染器数量。 在本例中，为 MarsCuriosityRover 子对象添加 10 个渲染器。 它将创建用于添加渲染器的字段，并将 MarsCuriosityRover 对象的子模型对象拖放到这些字段中。

![配置了 ClippingSphere 脚本组件字段的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

按照相同的过程，将 MarsCuriosityRover 的子对象渲染器添加到 ClippingBox 和 ClippingPlane 对象 。

在本教程中，只有 MarsCuriosityRover 模型将用于演示剪辑功能。 它们向更多的模型添加剪辑功能，从而增加了渲染器的大小，并添加了其各自的网格渲染器。

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a>配置眼动跟踪以突出显示工具提示

本部分探讨如何在项目中启用眼动跟踪。 例如，你将实现这样的功能，即在查看 MarsCuriosityRover 各部分时突出显示附加到它们的工具提示，在不看这些部分时隐藏这些提示。

### <a name="1-identify-target-objects-and-associated-tooltips"></a>1.确定目标对象及关联的工具提示

在“层次结构”窗口中，选择 ModelParent 对象。 展开“MarsCuriosity”->“探测器”，找到 MarsCuriosityRover 的五个主要部分：POI-Camera、POI-Wheels、POI-Antena、POI-Spectrometer、POI-RUHF Antenna    。

* 在“层次结构”窗口中观察与 MarsCuriosityRover 各部分关联的 5 个对应的工具提示对象。
* 你将配置这些对象，以便在查看 MarsCuriosityRover 各部分时突出显示体验。

![选中并展开了“探测器”对象的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a>2.实现 While Looking At Target () 和 On Look Away () 事件

在“层次结构”窗口中，选择 POI-Camera 对象。 在检查器窗口中，找到“眼动跟踪目标(脚本)”组件，并配置“While Looking At Target ()” & “On Look Away ()”事件，如下所示 ：

* 对于“无(对象)”字段，指定“POI Camera 工具提示”对象 
* 从“While Looking At Target ()”事件的“无函数”下拉列表中，选择“GameObject” > “SetActive (bool)”   。 选中它下面的“复选框”，将突出显示工具提示作为在查看目标对象时触发的操作。

![Unity 正在配置 EyeTrackingTarget WhileLookingAtTarget 事件](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* 按照相同的过程，单击“On Look Away ()”事件侦听器上的“无函数”下拉列表 。 然后选择“GameObject” > “SetActive (bool)”，并将复选框留空，将隐藏工具提示作为在不看目标对象时触发的操作  。

![配置了 EyeTrackingTarget OnLookAway 事件的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

按照相同的过程，将各自的工具提示对象分配给对应的 MarsCuriosityRover 部分的“While Looking At Target ()”和“On Look Away ()”事件  。

若要启用眼动跟踪，请遵循这些[准则](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations)。

## <a name="congratulations"></a>祝贺

在本教程中，你学习了如何构建混合现实体验来演示 UI 元素、3D 模型操作、模型剪辑和眼动跟踪功能。 本教程提供了 NextButton 和 PreviousButton，便于你探索 3D 模型查看器的体验。 通过 ClippingObjectButton，你打开了剪辑对象，还体验了剪辑功能。 本教程还为你提供了眼动跟踪元素，以便在体验中突出显示工具提示。

在下堂课中，你将学习如何为电脑创建全息远程处理应用程序来随时连接 HoloLens 2，从而可在混合现实中直观呈现 3D 内容。

> [!div class="nextstepaction"]
> [下一课：2.创建全息远程处理应用程序](mr-learning-pc-holographic-remoting-02.md)