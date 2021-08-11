---
title: 5. 添加按钮并重置棋子位置
description: 教程系列第 5 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款象棋应用
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: 5f37599e43147a79c8bdd9f0c28e0b23f163c39fa833d3835650c28deb4f0898
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226708"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5.添加按钮并重置棋子位置

在上一个教程中，向棋盘的 Pawn 和操控器组件添加了手势交互 Actor，使它们具有交互性。 在本部分中，你将继续使用混合现实工具包 UX Tools 插件，使用蓝图中的新函数和 Actor 引用构建象棋应用。 本部分结束时，你就可以打包混合现实应用，并将其部署到设备或仿真器中。

## <a name="objectives"></a>目标

* 添加交互式按钮
* 创建用于重置棋子位置的函数
* 连接按钮，以在按下时触发此函数

## <a name="creating-a-reset-function"></a>创建重置函数

第一个任务是创建一个函数蓝图，来将象棋棋子重置到场景中的原始位置。

1.  打开“WhiteKing”，选择“我的蓝图”中“函数”部分旁的“+”图标，将其命名为“重置位置”。    

2.  从蓝图网格拖动并释放“重置位置”的执行，以创建“SetActorRelativeTransform”节点。 
    * 此函数可设置 Actor 相对于其父级的变形（位置、旋转和缩放）。 将使用此函数来重置棋盘上国王的位置，即使棋盘已从其原始位置移动也无妨。

3. 在事件图表中右击，选择“进行变形”，然后将其“位置”更改为“X = -26”、“Y = 4”和“Z = 0”。    
    * 将其“返回值”连接到“SetActorRelativeTransform”中的“新相对变形”引脚。  

![Reset Location 函数](images/unreal-uxt/5-function.PNG)

编译并保存项目，然后返回到主窗口。 


## <a name="adding-a-button"></a>添加按钮

正确设置此函数后，接下来的任务是创建一个按钮，以在按它时触发函数。

1.  单击“添加新项”>“蓝图类”，展开“所有类”部分，然后搜索“UxtPressableButtonActor”  。
    * 将其命名为“ResetButton”，然后双击以打开蓝图

![从 HoloLens 2 样式按钮为新蓝图建立子类](images/unreal-uxt/5-subclass.PNG)

2. 确保在“组件”面板中选择了“ResetButton(自身)” 。 在“详细信息”面板中，导航到“按钮”部分 。 将默认“按钮标签”更改为“重置”，展开“按钮图标画笔”部分，然后按“打开图标画笔编辑器”按钮  。

![设置按钮上的标签和图标](images/unreal-uxt/5-buttonconfig.PNG)

图标画笔编辑器随即打开，你可以使用该编辑器为按钮选择新图标。

![为按钮选择图标](images/unreal-uxt/5-iconbrusheditor.PNG)

为配置按钮，还有很多其他的设置可以进行调整。 若要了解有关 UXT 可按按钮组件的详细信息，请参阅[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html)。

3. 单击“组件”面板中的“ButtonComponent (继承)”，将“详细信息”面板向下滚动到“事件”部分   。
    * 单击“按钮按下时”旁的绿色 + 按钮，向事件图表添加事件，按下按钮时将调用该事件。

此时，需要调用“WhiteKing”的“重置位置”函数，这需要在关卡中引用“WhiteKing”Actor。  

4.  在“我的蓝图”面板中，导航到“变量”部分，然后单击 + 按钮，将变量命名为“WhiteKing”   。
    * 在“详细信息”面板中，选择“变量类型”旁的下拉列表，搜索“WhiteKing”，然后选择“对象引用”   。
    * 选中“实例可编辑”旁的框，这使得可从主关卡设置变量。

![创建变量](images/unreal-uxt/5-var.PNG)

5.  将 WhiteKing 变量从“我的蓝图 > 变量”拖放到“‘重置’按钮事件图表”中，然后选择“获取 WhiteKing”。

## <a name="firing-the-function"></a>触发函数

剩下的就是，在按下按钮时，正式触发重置函数。

1.  拖动“WhiteKing”输出引脚并释放以放置新节点。 选择“Reset Location”函数。 最后，将传出执行引脚从“按钮按下时”拖放到“重置位置”上的传入执行引脚。 编译和保存 ResetButton 蓝图，然后返回到主窗口。

![从“按下按钮时”调用“Reset Location”函数](images/unreal-uxt/5-callresetloc.PNG)

2.  将“ResetButton”拖到视口中，并将其位置设置为“X = 50”、“Y = -25”和“Z = 10”。   将其旋转设置为“Z = 180”。 在“默认值”下，将 WhiteKing 变量的值设置为“WhiteKing”。  

![设置变量](images/unreal-uxt/5-buttonlevel.PNG)

运行应用，将象棋棋子移动到新位置，然后按 HoloLens 2 样式按钮来查看重置逻辑正在运行！

现在，你有了一个混合现实应用，其中包含可交互的棋子和棋盘，以及一个功能齐全的按钮，该按钮可重置棋子的位置。 可以在 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) 存储库中找到目前完成的该应用程序。 请随意阅读本教程以外的内容并设置其余的棋子，以便按下“重置”按钮时重置整个棋盘。

![在视口中结束场景](images/unreal-uxt/5-endscene.PNG)

你可以继续学习本教程的最后一部分，你将了解如何将应用打包并部署到设备或仿真器。

> [!IMPORTANT]
> 此时，在将应用程序部署到设备或仿真器之前，应使用建议的 [Unreal 性能设置](../performance-recommendations-for-unreal.md)来更新项目。

[下一节：6.打包并部署到设备或仿真器](unreal-uxt-ch6.md)
