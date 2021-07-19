---
title: Azure 空间定位点入门
description: 请完成本课程，了解如何在混合现实应用程序中使用 Azure 空间定位点来进行数据定位。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, Azure 空间定位点
ms.localizationpriority: high
ms.openlocfilehash: 9c3ae23c39bf4d0b32d8a5d82716f93fee48b6db
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656642"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a>2.Azure 空间定位点入门

本教程将介绍启动和停止 Azure 空间定位点会话，以及在单个设备上创建、上传和下载 Azure 空间定位点所需的各个步骤。

## <a name="objectives"></a>目标

* 了解有关使用适用于 HoloLens 2 的 Azure 空间定位点进行开发的基础知识
* 了解如何创建空间定位点并从 Azure 中获取它们

## <a name="creating-and-preparing-the-unity-project"></a>创建和准备 Unity 项目

在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。

首先，请按照[初始化项目和部署第一个应用程序](mr-learning-base-02.md)进行操作，但请忽略[在设备上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)说明；其中操作包括以下步骤：

1. [创建 Unity 项目](mr-learning-base-02.md#creating-the-unity-project)并为其指定适当的名称，例如“MRTK 教程”
2. [切换生成平台](mr-learning-base-02.md#switching-the-build-platform)
3. [导入 TextMeshPro 基本资源](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [导入混合现实工具包和配置 Unity 项目](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [创建和设置场景](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)，并为场景提供一个合适的名称，例如 AzureSpatialAnchors

然后，根据[更改空间感知显示选项](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)说明，确保场景的 MRTK 配置配置文件为“DefaultHoloLens2ConfigurationProfile”，并将空间感知网格的显示选项更改为“遮挡” 。

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a>安装内置 Unity 包和导入教程资产

[!INCLUDE[](includes/installing-packages-for-asa.md)]

## <a name="preparing-the-scene"></a>准备场景

在本部分，你将通过添加一些教程预制件来准备场景。

在“项目”窗口中导航到“资产” > “MRTK.Tutorials.AzureSpatialAnchors” > “预制件”文件夹，然后单击并将以下预制件拖动到“层次结构”窗口中，以将其添加到场景中  ：

* ButtonParent 预制件
* DebugWindow 预制件
* Instructions 预制件
* ParentAnchor 预制件

![选中新增的预制件的 Unity](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> 如果在场景中看到很大的图标（例如，框住的“T”图标会分散注意力），可以通过<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">将调节器 (Gizmos) 切换</a>到关闭位置来隐藏这些图标，如上图所示。

在“层次结构”窗口中选择“MixedRealityToolkit”对象，使用检查器窗口中的“添加组件”按钮添加以下组件 ：

* AR 空间点管理器(脚本)
* DisableDiagnosticsSystem (脚本)

![添加了 AR 定位点管理器和 DisableDiagnosticsSystem 组件的 Unity MixedRealityToolkit 对象 ](images/mr-learning-asa/asa-02-section4-step1-2.PNG)

> [!WARNING]
> ASA v2.9.0 和 v2.10.0-preview.1 存在一个已知问题，需要在场景中放置两个额外对象。 请使用检查器窗口中的“添加组件”按钮向“MixedRealityToolkit”对象添加“AR 摄像头管理器（脚本）”和“AR 会话（脚本）”。 请务必取消选中检查器窗口中“摄像头”对象旁边的复选框，以禁用在添加“AR 摄像头管理器（脚本）”时自动创建的摄像头。 此问题将在 ASA v 2.10.0 的完整版本中得到解决。
>

> [!NOTE]
> 添加“AR 空间点管理器（脚本）”组件时，会自动添加“AR 会话原点（脚本）”组件，因为它是“AR 空间点管理器（脚本）”所必需的。

## <a name="configuring-the-buttons-to-operate-the-scene"></a>配置按钮以操作场景

在本部分，你要将脚本添加到场景，以创建一系列按钮事件，用于演示本地定位点和 Azure 空间定位点在应用中的行为方式的基本原理。

在“层次结构”窗口中展开“ButtonParent”对象，然后选择名为“StartAzureSession”的第一个子对象，在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示   ：

* 将 ParentAnchor 对象指定为“On Click ()”事件的侦听器，具体方法是将该对象从“层次结构”窗口拖到“无(对象)”字段 
* 从“无函数”下拉列表中，选择“AnchorModuleScript” > “StartAzureSession ()”，将此函数设置为触发事件时要执行的操作  

![配置了 StartAzureSession 按钮 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-1.png)

在“层次结构”窗口中选择名为“StopAzureSession”的下一个按钮，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示  ：

* 将 ParentAnchor 对象指定为“On Click ()”事件的侦听器，具体方法是将该对象从“层次结构”窗口拖到“无(对象)”字段 
* 从“无函数”下拉列表中，选择“AnchorModuleScript” > “StopAzureSession ()”将此函数设置为触发事件时要执行的操作  

![配置了 StopAzureSession 按钮 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-2.png)

在“层次结构”窗口中选择名为“CreateAzureAnchor”的下一个按钮，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示  ：

* 将 ParentAnchor 对象指定为“On Click ()”事件的侦听器，具体方法是将该对象从“层次结构”窗口拖到“无(对象)”字段 
* 从“无函数”下拉列表中，选择“AnchorModuleScript” > “CreateAzureAnchor ()”将此函数设置为触发事件时要执行的操作  
* 将 ParentAnchor 对象分配到空的“无(游戏对象)”字段，使其成为 CreateAzureAnchor () 函数的参数 

![配置了 CreateAzureAnchor 按钮 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-3.png)

在“层次结构”窗口中选择名为“RemoveLocalAnchor”的下一个按钮，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示  ：

* 将 ParentAnchor 对象指定为“On Click ()”事件的侦听器，具体方法是将该对象从“层次结构”窗口拖到“无(对象)”字段 
* 从“无函数”下拉列表中，选择“AnchorModuleScript” > “RemoveLocalAnchor ()”将此函数设置为触发事件时要执行的操作  
* 将 ParentAnchor 对象分配到空的“无(游戏对象)”字段，使其成为 RemoveLocalAnchor () 函数的参数 

![配置了 RemoveLocalAnchor 按钮 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-4.png)

在“层次结构”窗口中选择名为“FindAzureAnchor”的下一个按钮，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示  ：

* 将 ParentAnchor 对象指定为“On Click ()”事件的侦听器，具体方法是将该对象从“层次结构”窗口拖到“无(对象)”字段 
* 从“无函数”下拉列表中，选择“AnchorModuleScript” > “FindAzureAnchor ()”将此函数设置为触发事件时要执行的操作  

![配置了 FindAzureAnchor 按钮 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-5.png)

在“层次结构”窗口中选择名为“DeleteAzureAnchor”的下一个按钮，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示  ：

* 将 ParentAnchor 对象指定为“On Click ()”事件的侦听器，具体方法是将该对象从“层次结构”窗口拖到“无(对象)”字段 
* 从“无函数”下拉列表中，选择“AnchorModuleScript” > “DeleteAzureAnchor ()”将此函数设置为触发事件时要执行的操作  

![配置了 DeleteAzureAnchor 按钮 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>将场景连接到 Azure 资源

在“层次结构”窗口中选择“ParentAnchor”对象，然后在“检查器”窗口中，找到“空间定位点管理器(脚本)”组件。  使用来自 Azure 空间定位点帐户（该帐户作为本教程系列[必备条件](mr-learning-asa-01.md#prerequisites)的一部分创建）的凭据配置“凭据”部分：

* 在“空间定位点帐户 ID”字段中，粘贴来自你的 Azure 空间定位点帐户的“帐户 ID”
* 在“空间定位点帐户密钥”字段中，粘贴来自你的 Azure 空间定位点帐户的主“访问密钥”或辅助“访问密钥”
* 在“空间定位点帐户域”字段中，粘贴来自你的 Azure 空间定位点帐户的“帐户域”

![配置了空间定位点管理器的 Unity](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>尝试 Azure 空间定位点的基本行为

Azure 空间定位点不能在 Unity 中运行，因此，若要测试 Azure 空间定位点功能，需生成项目并将应用部署到设备。

> [!TIP]
> 有关如何生成 Unity 项目并将其部署到 HoloLens 2 的提示，可参阅[在 HoloLens 2 上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。

当应用在设备上运行时，请按照“Azure 空间定位点教程说明”面板上显示的屏幕说明进行操作：

1. 将多维数据集移动至其他位置
2. 启动 Azure 会话
3. 创建 Azure 定位点（在多维数据集的位置创建定位点）。
4. 停止 Azure 会话
5. 删除本地定位点（允许用户移动多维数据集）
6. 将多维数据集移动至其他位置
7. 启动 Azure 会话
8. 查找 Azure 定位点（将多维数据集定位到步骤 3 所述的位置）
9. 删除 Azure 定位点
10. 停止 Azure 会话

![选中 Instructions 对象的 Unity](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> Azure 空间定位点将使用 Internet 来保存和加载定位点数据，因此请确保设备已连接到 Internet。

## <a name="anchoring-an-experience"></a>定位体验

前面的部分已介绍 Azure 空间定位点的基础知识。 我们已使用一个立方体来表示并可视化了附有定位点的父游戏对象。 本部分将介绍如何通过将整个体验定位为 ParentAnchor 对象的子级，来定位该体验。

在“层次结构”窗口中选择“ParentAnchor”对象，然后在“检查器”窗口中配置“转换”组件，如下所示 ：

* 将“比例 X”改为 1.1
* 将“比例 Z”改为 1.1

![已选择、定位和缩放 ParentAnchor 对象的 Unity](images/mr-learning-asa/asa-02-section8-step1-1.png)

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件” > 探测器”文件夹，然后单击并将“RoverExplorer_Complete”预制件拖动到“层次结构”窗口中，以将其添加到场景中    ：

![选中新增的 RoverExplorer_Complete 预制件的 Unity](images/mr-learning-asa/asa-02-section8-step1-2.png)

在“层次结构”窗口中新添加的 RoverModule_Complete 对象仍处于选中状态的情况下，将其拖动到“ParentAnchor”对象上，使其成为 ParentAnchor 对象的子级：

![将 RoverExplorer_Complete 对象设置为 ParentAnchor 的子级的 Unity](images/mr-learning-asa/asa-02-section8-step1-3.png)

如果现在重建项目并将应用部署到设备，可以通过移动已调整大小的多维数据集来重新定位整个漫游者探测器。

> [!TIP]
> 有多种用户体验流可用于重新定位体验，包括使用重新定位对象（例如本教程中使用的立方体）、使用按钮切换体验周围的边界控件、使用定位和旋转调节器，等等。

## <a name="congratulations"></a>祝贺

在本教程中，你已了解 Azure 空间定位点的基础知识。 本教程提供了多个按钮，让你了解启动和停止 Azure 空间定位点会话所需的各个步骤。 以及如何在单个设备上创建、上传和下载 Azure 空间定位点。

下一教程将介绍如何将 Azure 定位点 ID 保存到 HoloLens 2 以供检索（甚至在重启应用后也可供检索），以及如何在多个设备之间转移定位点 ID，以实现空间对齐。

> [!div class="nextstepaction"]
> [下一教程：3.保存、检索和共享 Azure 空间定位点](mr-learning-asa-03.md)
