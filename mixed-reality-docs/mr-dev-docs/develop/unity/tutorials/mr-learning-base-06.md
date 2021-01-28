---
title: 创建用户界面
description: 本课程介绍如何使用混合现实工具包 (MRTK) 创建静态和动态用户界面。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 预制件, 全息影像, 工具提示
ms.localizationpriority: high
ms.openlocfilehash: 4fe4b016be36e04abffeb415f690cc0c01a6f767
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635551"
---
# <a name="6-creating-user-interfaces"></a>6.创建用户界面

本教程介绍如何使用 MRTK 的按钮和菜单预制件以及 Unity 的 TextMeshPro 组件来创建简单的用户界面。 还介绍如何配置这些按钮以触发事件，并添加动态工具提示 UI 元素以向用户提供其他信息。

## <a name="objectives"></a>目标

* 了解如何组织集合中的按钮
* 了解如何使用 MRTK 的菜单预制件
* 了解如何使用 UI 菜单和按钮来与全息影像交互
* 了解如何添加文本元素
* 了解如何在对象上动态生成工具提示

## <a name="creating-a-static-panel-of-buttons"></a>创建按钮的静态面板

在“层次结构”窗口中，右键单击“RoverExplorer”对象，然后选择“创建空白项”添加一个空对象作为 RoverExplorer 的子对象，将该对象命名为“Buttons”，并按如下所述配置“转换”组件   ：

* **位置**：X = -0.6，Y = 0.036，Z = -0.5
* **旋转**：X = 90, Y = 0, Z = 0
* **缩放**：X = 1，Y = 1，Z = 1

![选中并定位了新创建的 Buttons 对象的 Unity](images/mr-learning-base/base-06-section1-step1-1.png)

在“项目”窗口中，导航至“资产” > “MRTK.Tutorials.GettingStarted” > “预制件”文件夹，然后单击“PressableRoundButton”预制件并将其拖动到 Buttons 对象上，然后右键单击“PressableRoundButton”并选择“重复”以创建副本，重复此操作，直到共有三个 PressableRoundButton 对象     ：

![新添加了 PressableRoundButton 预制件的 Unity](images/mr-learning-base/base-06-section1-step1-2.png)

在“层次结构”窗口中选择“Buttons”对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“GridObjectCollection”组件，并按如下所述配置该组件  ：

* **排序类型**：子顺序
* **布局**：水平
* **单元格宽度**：0.2
* **定位点**：中部左对齐

然后单击“更新集合”按钮以更新 Buttons 对象的子对象的位置：

![添加、配置并应用了 GridObjectCollection 组件的 Unity“按钮”对象](images/mr-learning-base/base-06-section1-step1-3.png)

在“层次结构”窗口中，将按钮命名为“提示”、“分解”和“重置”  。

为每个按钮选择“SeeItaysLabel” > “TextMeshPro”子对象，然后在“检查器”窗口中，更改相应的“TextMeshPro - Text”组件文本以匹配按钮名称  ：

![配置了按钮文本标签的 Unity](images/mr-learning-base/base-06-section1-step1-4.png)

完成后，折叠按钮对象的子对象。

在“层次结构”窗口中，选择“提示”按钮对象，然后在“检查器”窗口中配置 Interactable.OnClick () 事件，如下所示 ：

* 向“无(对象)”字段分配“RoverAssembly”对象 
* 从“无函数”下拉列表中，选择“PlacementHintsController” > “TogglePlacementHints ()”将此函数设置为触发事件时要执行的操作  

![配置了“提示”按钮对象 OnClick 事件的 Unity](images/mr-learning-base/base-06-section1-step1-5.png)

> [!TIP]
> 可交互组件是一体式的容器，它使所有对象都能轻松交互并响应输入。 “可交互”用作各种类型的输入的一个笼统术语，包括触摸、手射线和语音等等，它将这些交互传送到事件和视觉主题响应中。 若要了解如何为不同的输入类型配置它，以及如何自定义它的视觉主题，可参阅 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[可交互](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)指南。

在“层次结构”窗口中，选择“分解”按钮对象，然后在“检查器”窗口中配置 Interactable.OnClick () 事件，如下所示 ：

* 向“无(对象)”字段分配“RoverAssembly”对象 
* 从“无函数”下拉列表中，选择“ExplodedViewController” > “ToggleExplodedView ()”将此函数设置为触发事件时要执行的操作  

![配置了“分解”按钮对象 OnClick 事件的 Unity](images/mr-learning-base/base-06-section1-step1-6.png)

按“播放”按钮进入游戏模式，然后按住空格键以激活操作手，然后使用鼠标按“提示”按钮来切换放置提示对象的可见性：

![显示正在按下“提示”按钮的 Unity“播放”模式分屏视图](images/mr-learning-base/base-06-section1-step1-7.png)

然后按“分解”按钮以启用或关闭“分解”视图：

![显示正在按下“拆分”按钮的 Unity“播放”模式分屏视图](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a>创建跟随用户的动态菜单

在“项目”窗口中，导航到“资产” > “MRTK” > “SDK” > “功能” > “UX” > “预制件” > “菜单”文件夹，单击“NearMenu4x1”预制件并将其拖动到“层次结构”窗口中，然后将其“转换”位置设置为 X = 0、Y = -0.4、Z = 0 并按如下所述进行配置        ：

* 验证 SolverHandler 组件的“跟踪的目标类型”是否设置为“头部”  
* 选中“RadialView”解算器旁的复选框，使其默认为启用

![选中了新增的 near menu 预制件的 Unity](images/mr-learning-base/base-06-section2-step1-1.png)

在“层次结构”窗口中，将对象重命名为“Menu”，然后展开其 ButtonCollection 子对象以显示四个按钮 ：

![选中了“菜单”对象并展开了 ButtonCollection 对象的 Unity](images/mr-learning-base/base-06-section2-step1-2.png)

将 ButtonCollection 中的第一个按钮重命名为“指示器”，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件，如下所示：

* 更改主标签文本以匹配按钮的名称
* 向“无(对象)”字段分配 V 形外观的“指示器”对象
* 从“无函数”下拉列表中，选择“GameObject” > “SetActive (bool)”将此函数设置为触发事件时要执行的操作  
* 验证是否已选中参数复选框
* 将图标更改为“搜索”图标

![配置了“指示器”按钮对象“按钮配置帮助程序”的 Unity](images/mr-learning-base/base-06-section2-step1-3.png)

若要禁用 V 形“指示器”对象，请在“层次结构”窗口中选择 V 形外观的“指示器”对象，然后在“检查器”窗口中：

* 取消选中其名称旁的复选框，以使其在默认情况下处于非活动状态
* 使用“添加组件”按钮添加“方向指示器控制器(脚本)”组件 

![选中并禁用了“指示器”对象、添加了 DirectionalIndicatorController 组件的 Unity](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> 现在，当应用程序启动时，会默认禁用 V 形指示器，并且可以通过按“指标器”按钮来启用。

将第二个按钮重命名为“TapToPlace”，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件，如下所示 ：

* 更改主标签文本以匹配按钮的名称
* 向“无(对象)”字段分配“RoverExplorer”>“RoverAssembly”对象 
* 在“无函数”下拉列表中选择“TapToPlace” > “启用布尔”，以便在触发事件时更新此属性  
* 验证是否已选中参数复选框
* 将图标更改为“带有射线的手”图标

![配置了 TapToPlace 按钮对象“按钮配置帮助程序”的 Unity](images/mr-learning-base/base-06-section2-step1-5.png)

在“层次结构”窗口中选择“RoverAssembly”对象，然后在“检查器”窗口中配置“点击放置(脚本)”组件，如下所示 ：

* 取消选中其名称旁的复选框，以使其在默认情况下处于非活动状态
* 在“On Placing Stopped ()”事件部分中，单击 + 图标以添加新事件 ：
* 向“无(对象)”字段分配“RoverExplorer”>“RoverAssembly”对象 
* 在“无函数”下拉列表中选择“TapToPlace” > “启用布尔”，以便在触发事件时更新此属性  
* 验证是否已取消选中参数复选框

![重新配置了 TapToPlace 组件的 Unity](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> 现在，当应用程序启动时，默认情况下会禁用“点击放置”功能，并且可以通过按“点击放置”按钮来启用。 此外，当“点击放置”完成时，它会自动禁用。

## <a name="adding-text-to-the-scene"></a>向场景添加文本

在“层次结构”窗口中，右键单击“Table”对象，然后选择“3D 对象” > “Text - TextMeshPro”添加一个文本对象作为 Table 的子对象，然后在“检查器”窗口中按如下所述配置“矩形转换”组件   ：

* 将“位置 Y”更改为 1
* 将“宽度”更改为 1
* 将“高度”更改为 1
* 将“旋转 X”更改为 90

![选中了新创建的 TextMeshPro 对象的 Unity](images/mr-learning-base/base-06-section3-step1-1.png)

然后按如下所述配置“TextMeshPro - Text”组件：

* 将“文本”更改为漫游者探测器
* 将“字形”更改为粗体
* 将“字体大小”更改为 1
* 将“额外设置”>“边距”更改为 0.03

![配置了 TextMeshPro 组件的 Unity](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a>添加工具提示

在“项目”窗口中，导航到“资产” > “MRTK” > “SDK” > “功能” > “UX” > “预制件” > “工具提示”文件夹，以查找工具提示预制件      ：

![选中了 ToolTips 文件夹的 Unity 项目窗口](images/mr-learning-base/base-06-section4-step1-1.png)

在“层次结构”窗口中展开“RoverExplorer”>“RoverParts”对象并选择其所有子探测器部件对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“ToolTipSpawner”组件并按如下所述配置  ：

* 确保选中“启用焦点”复选框，以要求用户查看部件以显示工具提示
* 从“项目”窗口中将“简单行工具提示”预制件分配给“预制件”字段 
* 将“工具提示替代设置”>“设置模式”更改为“替代” 
* 将“工具提示替代设置”>“手动透视本地位置 Y”更改为 1.5 

![选中了所有探测器部件对象、添加和配置了 ToolTipSpawner 组件的 Unity](images/mr-learning-base/base-06-section4-step1-2.png)

在“层次结构”窗口中选择第一个探测器部件，“RoverParts”>“Camera_Part”，并按如下所述配置“ToolTipSpawner”组件 ：

* 更改“工具提示文本”以反映部件的名称，即“照相机” 

![配置了 Camera ToolTipText 的 Unity](images/mr-learning-base/base-06-section4-step1-3.png)

对每个探测器部件对象重复此步骤以配置“ToolTipSpawner”组件，如下所示 ：

* 对于 Generator_Part，请将“工具提示文本”更改为“生成器”  
* 对于 Lights_Part，请将“工具提示文本”更改为“灯光”  
* 对于 UHFAntenna_Part，请将“工具提示文本”更改为“UHF 天线”字段  
* 对于 Spectrometer_Part，请将“工具提示文本”更改为“分光仪”  

按下“播放”按钮进入“游戏”模式，然后在按住鼠标右键的同时移动鼠标，直到视线瞄准部件之一，并将显示该部件的工具提示：

![显示通过视线触发的工具提示的 Unity“播放”模式分屏视图](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a>祝贺

在本教程中，你了解了如何使用 MRTK 提供的按钮和菜单预制件以及 Unity 的 TextMeshPro 组件来创建简单的用户界面，以及如何配置按钮以在按下按钮时触发事件。 还了解了如何添加动态工具提示 UI 元素以向用户提供其他信息。

> [!div class="nextstepaction"]
>[下一教程：7.与 3D 对象交互](mr-learning-base-07.md)
