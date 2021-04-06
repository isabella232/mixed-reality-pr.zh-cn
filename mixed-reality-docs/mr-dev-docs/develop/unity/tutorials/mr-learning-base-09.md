---
title: 使用语音命令
description: 本课程介绍如何使用混合现实工具包 (MRTK) 在混合现实应用中设置、创建和使用语音命令。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 语音命令, 语音输入
ms.localizationpriority: high
ms.openlocfilehash: 3aea23d5a259e555f47ca9ea41d77f345c977aeb
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982923"
---
# <a name="9-using-speech-commands"></a>9.使用语音命令

本教程将介绍如何创建语音命令，以及如何在全局范围内对其进行控制。 还将介绍如何控制需要用户查看控制语音命令的对象的本地语音命令。

## <a name="objectives"></a>目标

* 了解如何创建语音命令
* 了解如何在全局和本地控制语音命令

[!INCLUDE[](includes/ensuring-microphone-capabality.md)]

## <a name="creating-speech-commands"></a>创建语音命令

在“层次结构”窗口中选择“MixedRealityToolkit”对象，然后在“检查器”窗口中选择“MixedRealityToolkit”>“输入”选项卡，并执行以下步骤 ：

* 展开“语音”部分
* 克隆 DefaultMixedRealitySpeechCommandsProfile 并为其指定一个适当的名称，例如 GettingStarted_MixedRealitySpeechCommandsProfile
* 验证“启动行为”是否设置为“自动启动” 

![创建语音命令](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> 有关如何克隆 MRTK 配置文件的提示，可参阅[配置 MRTK 配置文件](mr-learning-base-03.md)中的说明。

在“语音”>“语音命令”部分，单击“+ 添加新的语音命令”按钮四次，以在现有语音命令列表种添加四个新的语音命令，然后在“关键字”字段中输入以下短语  ：

* 启用指示器
* 启用点击放置
* 启用边界控制
* 禁用边界控制

![添加新语音命令](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> 如果计算机没有麦克风，可向语音命令分配一个 KeyCode，以便在按下相应的键时触发它们。

## <a name="controlling-speech-commands"></a>控制语音命令

在“项目”窗口中，导航到“包” > “混合现实工具包基础” > “SDK” > “功能” > “UX” > “预制件” > “工具提示”文件夹，以查找工具提示预制件      ：

![打开工具提示文件夹](images/mr-learning-base/base-09-section3-step1-1.png)

在“层次结构”窗口中，右键单击空白区域，然后选择“创建空白项”，将空对象添加到场景中。

将对象命名为 SpeechInputHandler_Global，然后在“检查器”窗口中，使用“添加组件”按钮添加 SpeechInputHandler 组件，并按如下所示对其进行配置  ：

* 取消选中“需要焦点”复选框，使用户无需查看带有 SpeechInputHandler 组件的对象即可触发语音命令 
* 从“项目”窗口中，将“SpeechConfirmation Tooltip”预制件分配到“语音确认工具提示预制件”字段，以便在识别语音命令时显示此预制件 

![配置语音输入处理程序组件](images/mr-learning-base/base-09-section3-step1-2.png)

在 SpeechInputHandler 组件上，单击小 + 图标三次，添加三个关键字元素：

![向语音输入处理程序添加关键字元素](images/mr-learning-base/base-09-section3-step1-3.png)

展开“元素 0”并按如下所示对其进行配置：

* 在“关键字”字段中，输入“启用指示器”，以引用在上一部分中创建的“启用指示器”语音命令 
* 单击 + 图标以添加事件
* 从“层次结构”窗口中，向“无(对象)”字段分配 Indicator 对象 
* 从“无函数”下拉列表中，选择“GameObject” > “SetActive (bool)”将此函数设置为触发事件时要执行的操作  
* 选中参数复选框，让其处于选中状态

![配置关键字元素 0](images/mr-learning-base/base-09-section3-step1-4.png)

展开“元素 1”并按如下所示对其进行配置：

* 在“关键字”字段中，输入“启用边界控制”，以引用在上一部分中创建的“启用边界控制”命令 
* 单击 + 图标以添加事件
* 从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 
* 在“无函数”下拉列表中选择“BoundsControl” > “启用布尔”，以便在触发事件时更新此属性  
* 选中参数复选框，让其处于选中状态
* 单击小 + 图标以添加另一个事件
* 从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 
* 在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  
* 选中参数复选框，让其处于选中状态

![配置关键字元素 1](images/mr-learning-base/base-09-section3-step1-5.png)

展开“元素 2”并按如下所示对其进行配置：

* 在“关键字”字段中，输入“禁用边界控制”，以引用在上一部分中创建的“禁用边界控制”命令 
* 单击 + 图标以添加事件
* 从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 
* 在“无函数”下拉列表中选择“BoundsControl” > “启用布尔”，以便在触发事件时更新此属性  
* 验证是否已取消选中参数复选框
* 单击小 + 图标以添加另一个事件
* 从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 
* 在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  
* 验证是否已取消选中参数复选框

![配置关键字元素 2](images/mr-learning-base/base-09-section3-step1-6.png)

在“层次结构”窗口中依次选择“RoverExplorer”>“RoverAssembly”对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“SpeechInputHandler”组件，并按如下所述配置该组件：  

* 验证是否已选中“需要焦点”复选框，使用户需要查看带有 SpeechInputHandler 组件的对象才可触发语音命令 
* 从“项目”窗口中，将“SpeechConfirmation Tooltip”预制件分配到“语音确认工具提示预制件”字段，以便在识别语音命令时显示此预制件 

![将语音输入处理程序添加到 Rover Assembly](images/mr-learning-base/base-09-section3-step1-7.png)

在 SpeechInputHandler 组件上，单击小 + 图标以添加关键字元素，展开新创建的元素，然后按如下所示对其进行配置：

* 在“关键字”字段中，输入“启用点击放置”，以引用在上一部分中创建的“启用点击放置”命令 
* 单击 + 图标以添加事件
* 从“层次结构”窗口中，将对象本身（即 RoverAssembly 对象）分配给“无(对象)”字段 
* 在“无函数”下拉列表中选择“TapToPlace” > “启用布尔”，以便在触发事件时更新此属性  
* 选中参数复选框，让其处于选中状态

![配置 Rover Assembly 上的语音输入处理程序](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a>祝贺

在本教程中，你学习了如何创建语音命令，以及如何在全局范围内对其进行控制。 还了解了如何控制需要用户查看控制语音命令的对象的本地语音命令。

[入门教程](mr-learning-base-01.md)系列到此也就结束了。 通过这些教程，你成功使用 MRTK 从头构建了一个完整的混合现实体验。

接下来的 [Azure 空间定位点](mr-learning-asa-01.md)和[多用户功能教程](mr-learning-sharing-01.md)这两个教程系列将首先介绍如何将 Azure 空间定位点集成到你的项目中，以定位在现实世界中创建的漫游者探测器体验。 然后，将介绍如何将多用户功能添加到你的项目，以实时共享用户和对象的移动情况。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们规划的 Unity 开发检查点历程，你的下一项任务就是熟悉混合现实应用的核心构建基块。

> [!div class="nextstepaction"]
> [基本交互](../../../out-of-scope/mrtk-101.md)

你可以随时返回到 [Unity 开发检查点](../unity-development-overview.md#1-getting-started)。