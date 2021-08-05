---
title: Unreal 中的 UMG 和键盘
description: 了解如何使用 Unrealm 运动图形创建小组件中的 UI 系统。
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality、全息影像、HoloLens 2、眼动跟踪、凝视输入、头部装载显示器、Unreal 引擎、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、小组件、UI、UMG、Unreal Motion Graphics、Unreal Engine、UE、UE4
ms.openlocfilehash: 8cb1c804757332ce7b78f0cb92cf895b873c1835208962b20d5bbbfae4684785
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212794"
---
# <a name="umg-and-keyboard-in-unreal"></a>Unreal 中的 UMG 和键盘

Unreal Motion Graphics (UMG) 是 Unreal Engine 的内置 UI 系统，用于创建菜单和文本框等界面。 使用 UMG 构建的用户界面由小组件组成。 我们将指导你创建新小组件、将小组件添加到世界空间，以及以使用系统键盘进行交互为例。 有关 UMG 的信息，请参阅官方 Unreal Engine [文档](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)。 

## <a name="create-a-new-widget"></a>创建新小组件

- 创建小组件蓝图来布局游戏的 UI：

![从 Unreal 菜单添加小组件蓝图的屏幕截图](images/unreal-umg-img-01.png)

- 打开新蓝图，将组件从调色板添加到画布。  在这种情况下，我们已从"输入"部分添加了两个文本框组件：

![层次结构窗口的屏幕截图，其中突出显示并展开了文本小组件组件](images/unreal-umg-img-02.png)

- 在"层次结构"或"设计器"窗口中选择一个小组件，并修改详细信息面板中的参数。  在这种情况下，我们添加了一些默认的"提示文本"和将鼠标悬停在文本框上时出现的浅色。  与虚拟键盘交互时，文本框HoloLens虚拟键盘：

![层次结构窗口中已修改参数的屏幕截图](images/unreal-umg-img-03.png)

- 还可以在详细信息面板中订阅事件：

![详细信息面板中事件的屏幕截图](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a>向世界空间添加小组件

- 创建新的 Actor、添加小组件组件，以及将执行组件添加到场景中：

![附加了小组件执行组件屏幕截图](images/unreal-umg-img-05.png)

- 在小组件的详细信息面板中，将 **小组件类设置为** 之前创建的小组件蓝图：

![设置了小组件类的蓝图详细信息面板的屏幕截图](images/unreal-umg-img-06.png)

- 对于文本小组件，请确保未选中" **接收硬件** 输入"，以便我们仅从虚拟键盘更新其文本：

![未选中包含接收硬件输入的交互部分屏幕截图](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a>小组件交互

UMG 小组件通常从鼠标接收输入。  在 HoloLens 或 VR 上，我们需要使用小组件交互组件模拟鼠标，以获得相同的事件。

- 创建新的 Actor、添加小 **组件交互** 组件，以及将执行组件添加到场景中：

![新执行组件的屏幕截图，其中突出显示了小组件交互组件](images/unreal-umg-img-08.png)

- 在小组件交互组件的详细信息面板中：
    - 将交互距离设置为需要的距离值
    - 将 **交互源设置为****自定义**
    - 对于开发，将 **"显示调试"** 设置为 **true：**

![小组件交互和调试组件属性的屏幕截图](images/unreal-umg-img-09.png)

交互源的默认值为"World"，它应基于小组件交互组件的世界位置发送光线广播。 在 AR 和 VR 中，情况并非如此。  启用"显示调试"和向小组件添加悬停色调对于检查小组件交互组件是否执行预期操作非常重要。  解决方法是使用自定义源，并设置来自手部射线的事件图中的光线广播。  

此处，我们将从事件时钟周期调用此代码：

![事件刻度的蓝图](images/unreal-umg-img-10.png)

然后将虚拟鼠标指针事件添加到小组件交互组件，以响应HoloLens输入。  在这种情况下，在抓取手时发送鼠标左键按下事件，在未抓取时发送鼠标左键释放事件：

![添加了虚拟鼠标指针事件的蓝图](images/unreal-umg-img-13.png)

现在，将应用部署到 HoloLens 2，你将看到从右侧延伸的手部射线。 如果直接在可编辑的文本框之一和 air tap 上，系统键盘将出现在你前面，并允许你输入文本。 
 
> [!NOTE]
> 系统HoloLens需要 Unreal Engine 4.26 或更高版本。 此外，当应用从 Unreal 编辑器流式传输到头戴显示设备时，只有在设备上运行应用时，键盘才显示。

## <a name="see-also"></a>另请参阅：
* [Unreal 的 UMG 文档](https://docs.unrealengine.com/Engine/UMG/index.html)
* [Unreal 的 UMG 教程](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
