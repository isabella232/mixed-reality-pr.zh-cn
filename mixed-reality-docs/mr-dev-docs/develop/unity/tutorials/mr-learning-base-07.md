---
title: 与 3D 对象交互
description: 本课程介绍如何使用混合现实工具包 (MRTK) 来操作混合现实应用中的 3D 对象并与之交互。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 对象交互, 边界控件
ms.localizationpriority: high
ms.openlocfilehash: f92eca294e2114207a5e28ebe80aa480b9029b66
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590423"
---
# <a name="7-interacting-with-3d-objects"></a>7.与 3D 对象交互

本教程介绍如何启用 3D 对象的远近操作以及如何限制允许的操作类型。 你还将了解如何在 3D 对象周围添加边界控件，以便更轻松地控制对象操作。

## <a name="objectives"></a>目标

* 了解如何配置 3D 对象，以便可以与它们进行交互
* 了解如何将边界控件添加到 3D 对象

## <a name="manipulating-3d-objects"></a>操作 3D 对象

在本部分中，你将添加相应功能，用于操作在教程[定位场景中的对象](mr-learning-base-04.md)期间在表格中包含的所有探测器部件。

若要实现此目的，请执行以下主要步骤：

1. 将“对象操控器(脚本)”组件添加到所有部件对象
2. 将“NearInteractionGrabbable”组件添加到所有部件对象
3. 配置“对象操控器(脚本)”组件

> [!NOTE]
> 若要 **操作某个对象**，该对象必须具有以下组件：
>
> * “碰撞体”组件，例如盒碰撞体
> * “对象操控器(脚本)”组件
>
> 若要使用跟踪手 **操作** 和 **抓取某个对象**，该对象必须具有以下组件：
>
> * “碰撞体”组件，例如盒碰撞体
> * “对象操控器(脚本)”组件
> * “NearInteractionGrabbable”组件

此外，你将配置漫游者探测器，以便能够将探测器部件放置到探测器上，使其成为完整的探测器。

在“层次结构”窗口中展开“RoverExplorer”>“RoverParts”对象并选择其所有子探测器部件对象和“RoverAssembly”对象，然后在“检查器”窗口中，使用“添加组件”按钮将以下组件添加到所有选定对象  ：

* “对象操控器(脚本)”组件
* “NearInteractionGrabbable”组件
* “部件程序集控制器(脚本)”组件

![选中了 RoverAssembly 和所有探测器部件对象并添加了组件的 Unity](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> 若要选择不相邻的多个对象，请在按住 CTRL 键的同时使用鼠标选择任何对象。

> [!NOTE]
> 在这种情况下，添加对象操控器（脚本）时，将自动添加约束管理器（脚本），因为对象操控器（脚本）依赖于约束管理器。

> [!NOTE]
> 在本教程中，碰撞体已添加到探测器部件中。 若要详细了解碰撞体，可访问 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞体</a>文档。

> [!NOTE]
> “部件程序集控制器(脚本)”并不是 MRTK 的一部分，而是属于本教程的资源。

在所有探测器部件对象和 RoverAssembly 对象仍处于选中状态的情况下，在“检查器”窗口中，配置“对象操控器(脚本)”组件，如下所示：

* 从“双手操作类型”下拉列表中取消选中“缩放”，以便仅启用“移动”和“旋转”  

![配置了“双手操作类型”的 Unity](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> 至此，已为所有探测器部件对象和 RoverAssembly 对象启用了对象操作。

在“项目”窗口中，导航到“包” > “混合现实工具包标准资产” > “音频”文件夹，查找音频剪辑：

![选中了音频文件夹的 Unity 项目窗口](images/mr-learning-base/base-07-section1-step1-3.png)

在“层次结构”窗口中重新选择所有探测器部件对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“音频资源”组件，并按如下所述配置该组件  ：

* 将“MRTK_Scale_Start”音频剪辑分配到“AudioClip”字段 
* 取消选中“唤醒时播放”复选框
* 将“空间混合”更改为 1

![选中了所有探测器部件并添加和配置了“音频源”组件的 Unity](images/mr-learning-base/base-07-section1-step1-4.png)

在“层次结构”窗口中，展开“RoverAssembly”>“RoverModel_PlacementHints_XRay”>“Parts_PlacementHints”对象以显示所有放置提示对象，然后选择第一个探测器部件，“RoverParts”>“Camera_Part”，并配置“部件程序集控制器(脚本)”组件，如下所示  ：

* 将“Camera_PlacementHint”对象分配到“定位位置”字段 

![配置了 Camera_Part PartAssemblyController 组件的 Unity](images/mr-learning-base/base-07-section1-step1-5.png)

对其余的每个探测器部件对象重复该步骤，以配置“部件程序集控制器(脚本)”组件，如下所示 ：

* 对于“Generator_Part”，请将“Generator_PlacementHint”对象分配到“定位位置”字段  
* 对于“Lights_Part”，请将“Lights_PlacementHint”对象分配到“定位位置”字段  
* 对于“UHFAntenna_Part”，请将“UHFAntenna_PlacementHint”对象分配到“定位位置”字段  
* 对于“Spectrometer_Part”，请将“Spectrometer_PlacementHint”对象分配到“定位位置”字段  
* 对于“RoverAssembly”，将对象本身（即同一 RoverAssembly 对象）分配到“定位位置”字段  

在“层次结构”窗口中，选择“RoverExplorer”>“按钮”>“重置”按钮对象，然后在“检查器”窗口中配置可交互的“OnClick ()”事件，如下所示 ：

* 向“无(对象)”字段分配“RoverAssembly”对象 
* 从“无函数”下拉列表中，选择“PartAssemblyController” > “ResetPlacement ()”将此函数设置为触发事件时要执行的操作  

![配置了“重置”按钮对象 OnClick 事件的 Unity](images/mr-learning-base/base-07-section1-step1-6.png)

如果现在进入“游戏”模式，就可以使用近距或远距交互将探测器部件放置到探测器上。 一旦部件靠近相应的放置提示，它将贴靠到位并成为探测器的一部分。 若要重置放置，可以按“重置”按钮：

![显示正在按下“重置”按钮的 Unity“播放”模式分屏视图](images/mr-learning-base/base-07-section1-step1-7.png)

若要详细了解“对象操控器”组件及其相关属性，可参阅 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[对象操控器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)指南。

## <a name="adding-bounds-control"></a>添加边界控件

边界控件提供用于缩放和旋转的控点，在近距和远距交互时，使用边界控件可以更轻松、更直观地单手操作对象。

在此示例中，将向 RoverExplorer 对象添加一个边界控件，以便可以轻松实现整体移动、旋转和缩放。 此外，还将配置菜单，以便可以打开和关闭边界控件。

在“层次结构”窗口中选择“RoverExplorer”对象，然后在“检查器”窗口中，使用“添加组件”按钮添加以下组件 ：

* BoundsControl 组件
* “对象操控器(脚本)”组件

然后取消选中所有组件旁边的复选框，以使其默认为“禁用” ：

![选中 RoverExplorer 对象并添加和禁用了组件的 Unity](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> 边界控件可视化效果是在运行时创建的，因此在进入“游戏”模式之前不可见。

> [!NOTE]
>BoundsControl 组件将在运行时自动添加 NearInteractionGrabbable 组件。 因此，无需添加此组件即可使用跟踪的双手抓取包含的对象。

> [!NOTE]
>对象操控器（脚本）自动添加约束管理器（脚本）

在“层次结构”窗口中展开“菜单”>“ButtonCollection”对象以显示第四个按钮，并将第三个按钮重命名为“BoundsControl_Enable”，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”，如下所示  ：

* 将“主标签文本”更改为“启用” 
* 向“无(对象)”字段分配“RoverExplorer”对象 
* 在“无函数”下拉列表中选择“BoundsControl” > “启用布尔”，以便在触发事件时更新此属性  
* 验证是否已选中参数复选框
* 单击小 + 图标以添加另一个事件
* 向“无(对象)”字段分配“RoverExplorer”对象 
* 在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  
* 验证是否已选中参数复选框
* 将图标保留为“带有边界控件的多维数据集”图标

![选中了 BoundsControl_Enable 按钮对象并配置了“按钮配置帮助程序”组件的 Unity](images/mr-learning-base/base-07-section2-step1-2.png)

将第四个和最后一个按钮重命名为“BoundsControl_Disable”，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件，如下所示 ：

* 将“主标签文本”更改为“禁用” 
* 向“无(对象)”字段分配“RoverExplorer”对象 
* 在“无函数”下拉列表中选择“BoundsControl” > “启用布尔”，以便在触发事件时更新此属性  
* 验证是否已取消选中参数复选框
* 单击小 + 图标以添加另一个事件
* 向“无(对象)”字段分配“RoverExplorer”对象 
* 在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  
* 验证是否已取消选中参数复选框
* 将图标更改为“带有边界控件的多维数据集”图标

![选中了 BoundsControl_Disable 按钮对象并配置了“按钮配置帮助程序”组件的 Unity](images/mr-learning-base/base-07-section2-step1-3.png)

如果现在进入“游戏”模式并通过单击“启用”按钮启用边界控件，则可以使用近距或远距交互来移动、旋转和缩放边界控件，然后使用“禁用”按钮再次禁用边界控件：

![显示正在操作边界控件的 Unity“播放”模式分屏视图](images/mr-learning-base/base-07-section2-step1-4.png)

若要详细了解“边界控件”组件及其相关属性，可以访问 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[边界控件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)指南。

## <a name="congratulations"></a>祝贺

在本教程中，你了解了如何为 3D 对象启用近距和远距操作，以及如何限制允许的操作类型。 你还了解了如何在 3D 对象周围添加边界控件，以便更轻松地控制对象操作。

> [!div class="nextstepaction"]
> [下一教程：8.使用眼动跟踪](mr-learning-base-08.md)
