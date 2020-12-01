---
title: Unreal 中的 UMG 和键盘
description: 了解如何使用 Unrealm 动画图形从小组件创建 UI 系统。
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality，全息影像，HoloLens 2，眼睛跟踪，眼睛输入，head 装显示，Unreal 引擎，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，小组件，UI，UMG，Unreal 运动图形，Unreal 引擎，UE，UE4
ms.openlocfilehash: 9f22a5f7a13732727b6b122d385aad7e708a1343
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355286"
---
# <a name="umg-and-keyboard-in-unreal"></a>Unreal 中的 UMG 和键盘

Unreal 运动图形 (UMG) 是 Unreal 引擎的内置 UI 系统，用于创建菜单和文本框等接口。 用 UMG 生成的用户界面由小组件组成。 本指南将演示如何创建新的小组件，如何将其添加到世界空间，以及如何使用系统键盘作为示例在混合现实中实现与该小组件的交互。 可以在官方 Unreal 引擎 [文档](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)中了解有关 UMG 的详细信息。 

## <a name="create-a-new-widget"></a>创建新小组件

- 创建小组件蓝图来布置游戏的 UI：

![从 "Unreal" 菜单添加小组件蓝图的屏幕截图](images/unreal-umg-img-01.png)

- 打开新蓝图，并将组件从调色板添加到画布。  在这种情况下，我们已从 "Input" 节中添加了两个文本框组件：

![突出显示并展开文本小组件组件的层次结构窗口的屏幕截图](images/unreal-umg-img-02.png)

- 在 "层次结构" 或 "设计器" 窗口中选择一个小组件，并在详细信息面板中修改参数。  在这种情况下，我们添加了一些默认的 "提示文本" 和淡色颜色，当光标悬停在文本框上方，以提供小组件已准备好进行交互的反馈时。  当与以下内容交互时，文本框将在 HoloLens 上弹出虚拟键盘：

!["层次结构" 窗口中已修改参数的屏幕截图](images/unreal-umg-img-03.png)

- 还可以在 "详细信息" 面板中订阅事件：

![详细信息面板中事件的屏幕截图](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a>向世界空间添加小组件

- 创建新的执行组件，添加小组件组件，并将执行组件添加到场景：

![附加了小组件的参与者的屏幕截图](images/unreal-umg-img-05.png)

- 在小组件的详细信息面板中，将 " **小组件" 类** 设置为先前创建的小组件蓝图：

![带有小组件类集的蓝图详细信息面板的屏幕截图](images/unreal-umg-img-06.png)

- 对于文本小组件，请确保未选中 " **接收硬件输入** "，因此我们仅从虚拟键盘更新其文本：

![未选中带有接收硬件输入的交互部分的屏幕截图](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a>小组件交互

UMG 小组件通常从鼠标接收输入。  在 HoloLens 或 VR 上，我们需要模拟带有小组件交互组件的鼠标以获取相同的事件。

- 创建新的执行组件，添加 **小组件交互** 组件，并将执行组件添加到场景：

![突出显示小组件交互组件的新执行组件的屏幕截图](images/unreal-umg-img-08.png)

- 在小组件交互组件的 "详细信息" 面板中，将 "交互距离" 设置为所需距离，将 " **交互源** " 设置为 " **自定义**"，并将 " **显示调试** " 设置为 " **true**"：

![小组件交互和调试组件属性的屏幕截图](images/unreal-umg-img-09.png)

交互源的默认值是 "World"，它应基于小组件交互组件的世界位置发送 raycasts，但在 AR 和 VR 中，这似乎不是这样。  在开发过程中启用 "显示调试" 并向小组件添加悬停淡色非常重要，请检查小组件交互组件是否正在执行所需的操作。  解决方法是使用自定义源，并在右侧的事件图中设置 raycast。  

这里，我们从事件滴答中调用此内容：

![事件滴答的蓝图](images/unreal-umg-img-10.png)

然后，将虚拟鼠标指针事件添加到对 HoloLens 输入做出反应的小组件交互组件。  在这种情况下，请在 grasped 时发送鼠标左键按下事件，并在 not grasped 时发送鼠标左键释放事件：

![添加了虚拟鼠标指针事件的蓝图](images/unreal-umg-img-13.png)

现在，当你将应用程序部署到 HoloLens 2 时，你将看到右手的手写。 如果将其定向到一个可编辑的文本框，然后单击一下，系统键盘将显示在您的前面，并允许您输入文本。 
 
> [!NOTE]
> HoloLens 系统键盘需要 Unreal 引擎4.26 或更高版本。 此外，仅当应用程序在设备上运行时，才会显示在应用程序从 Unreal 编辑器流式传输到耳机时的键盘。

## <a name="see-also"></a>另请参阅：
* [Unreal 的 UMG 文档](https://docs.unrealengine.com/Engine/UMG/index.html)
* [Unreal 的 UMG 教程](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
