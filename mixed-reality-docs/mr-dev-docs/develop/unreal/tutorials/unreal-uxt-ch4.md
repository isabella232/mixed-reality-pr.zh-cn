---
title: 4. 使场景具有交互性
description: 教程系列第 4 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款象棋应用
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: 74d4fb7ebab2f5ba2df477cc29d8787367c1f105cc7a65d87460ac1e033b0fbb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203767"
---
# <a name="4-making-your-scene-interactive"></a>4.使场景具有交互性

在上一个教程中，你添加了 ARSession、Pawn 和游戏模式，以完成针对象棋应用的混合现实设置。 本部分重点介绍如何使用开放源代码的[混合现实工具包 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) 插件，它提供了使场景具有交互性的工具。 本部分结束时，棋子将按照用户输入移动。

## <a name="objectives"></a>目标

* 安装混合现实 UX Tools 插件
* 将手势交互 Actor 添加到指尖
* 创建操控器并将其添加到场景中的对象
* 使用输入模拟来验证项目

## <a name="downloading-the-mixed-reality-ux-tools-plugin"></a>下载混合现实 UX Tools 插件
在开始使用用户输入之前，需要将混合现实 UX Tools 插件添加到项目。 若要了解有关 UX Tools 的详细信息，可以在 [GitHub](https://aka.ms/uxt-unreal) 上查看该项目。

1. 打开 Epic Games Launcher。 导航到 Unreal Engine Marketplace 并搜索“[Mixed Reality UX Tools](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools)”。 将插件安装到引擎。

![Unreal Marketplace](images/unreal-uxt/2-uxt-plugin.PNG)

2. 返回到 Unreal 编辑器，前往“项目设置” > “插件”，然后搜索“混合现实 UX Tools”。 请确保已启用该插件，并在出现提示时重新启动编辑器。

![启用混合现实 UX Tools 插件](images/unreal-uxt/2-enable-uxt.PNG)

3.  UXTools 插件具有一个“内容”文件夹（带有组件子文件夹，包括“按钮”、“XR 模拟”和“指针”），以及一个包含额外代码的“C++ 类”文件夹  。  

> [!NOTE]
> 如果在“内容浏览器”中看不到“UXTools 内容”部分，请单击“视图选项”>“显示引擎内容”  。

![显示引擎内容](images/unreal-uxt/4-showenginecontent.PNG)

可以在混合现实 UX Tools GitHub [存储库](https://aka.ms/uxt-unreal)中找到其他插件文档。

安装插件后，便可以开始使用它所提供的工具，从手势交互 Actor 开始。

## <a name="spawning-hand-interaction-actors"></a>生成手势交互 Actor

与 UX 元素的手势交互是使用手势交互 Actor 完成的，这些手势交互 Actor 为近距和远距交互创建并驱动指针和视觉对象。
- 近距交互 - 缩放食指和拇指之间的元素或使用指尖戳元素。
- 远距交互 - 将虚拟手的光线指向元素并同时按住食指和拇指。

在我们的示例中，将手势交互 Actor 添加到 MRPawn 可达到以下目的：
- 将光标添加到 Pawn 的食指指尖。
- 提供可通过 Pawn 操纵的精确手势输入事件。
- 通过从虚拟手的手掌延伸出的手部光线允许远距交互输入事件。

建议在继续之前通读介绍手动交互的[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html)。

准备就绪后，打开“MRPawn”蓝图，然后转到“事件图”。

1. 将执行引脚从事件 BeginPlay 拖离然后释放，以放置一个新节点。
    * 选择“从类中生成 Actor”，单击“类”引脚旁边的下拉列表，并搜索“UXT 手势交互 Actor”  。  

2. 生成第二个“UXT 手势交互 Actor”，这次会将手势设置为“向右”  。 事件开始时，将会在每只手上生成 UXT 手势交互 Actor。

事件图应与以下屏幕截图匹配：

![生成 UXT 手势交互 Actor](images/unreal-uxt/4-spawnactor.PNG)

两个 UXT 手势交互 Actor 均需要所有者和初始变形位置。 在这种情况下，初始变形并不重要，因为 UX Tools 插件中包含手势交互 Actor，后者可见后便立即跳转到虚拟手。 但是，`SpawnActor` 函数需要使用变形输入来避免编译器错误，因此你将使用默认值。

1. 将该引脚拖离一个“生成变形”引脚，然后释放，即可放置一个新节点。
    * 搜索“进行变形”节点，然后将“返回值”拖到另一个手势的“生成变形”，以便连接两个 SpawnActor 节点   。

2.  选择两个 SpawnActor 节点底部的“向下箭头”，以显示“所有者”引脚  。    
    * 将该引脚拖离一个“所有者”引脚，然后放开，即可放置一个新节点。
    * 搜索“self”并选择“Get a reference to self”变量 。
    * 在 Self 对象引用节点和另一个手势交互 Actor 的“所有者”引脚之间创建链接 。
3. 最后，同时选中两个手势交互 Actor 的“在抓取目标上显示近光标”框。 当食指靠近时，光标应出现在抓取目标上，这样就可以看到手指相对于目标的位置。
    * 编译并保存后返回到主窗口。

确保连接与以下屏幕截图匹配，但可随意拖动节点以使蓝图更具可读性。

![完成 UXT 手势交互 Actor 设置](images/unreal-uxt/4-fingerptrs.PNG)

可以在 [UX Tools 文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html)中找到有关手动交互 Actor 的详细信息。

现在，项目中的虚拟手可以选择对象，但仍无法对其进行操纵。 测试应用之前的最后一个任务是将操控器组件添加到场景中的 Actor。

## <a name="attaching-manipulators"></a>附加操控器

操控器是一个响应精确手动输入的组件，可进行抓取、旋转和平移。 将操控器的变形应用到 Actor 变形可允许进行直接 Actor 操纵。

1. 在“组件”面板中，打开“棋盘”蓝图，单击“添加组件”并搜索“UXT 通用操控器”   。

![添加通用操控器](images/unreal-uxt/4-addmanip.PNG)

2. 展开“详细信息”面板中的“通用操控器”部分 。 可以在其中设置单手操纵或双手操纵、旋转模式和平滑模式。 可以随意选择所需的模式，然后编译和保存棋盘。

![设置模式](images/unreal-uxt/4-setrotmode.PNG)

3. 对 WhiteKing Actor 重复以上步骤。

可以在[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html)中找到有关混合现实 UX Tools 插件中提供的操控器组件的详细信息。

## <a name="testing-the-scene"></a>测试场景

好消息！ 你已准备好使用其新的虚拟手和用户输入来测试应用。 在主窗口中按“播放”，应该会看到两个网格手，且从每个手掌延伸出手部光线。 可以按如下所示控制手势及其交互：
- 按住“左 Alt”键以控制左手，按住“左 Shift”键以控制右手   。
- 移动鼠标来移动手，并滚动鼠标滚轮，向前或向后移动手  。
- 使用鼠标左键进行缩放，使用鼠标中键执行戳操作。

> [!NOTE]
> 如果你有多个头戴显示设备插入电脑，则输入模拟可能无法正常工作。 如果遇到问题，请尝试拔下其他头戴显示设备。

![视口中的模拟手](images/unreal-uxt/4-handsim.PNG)

请尝试使用模拟手来拿起、移动和放下白棋国王并操纵棋盘！ 试验近距交互和远距交互 - 请注意，当手足够靠近可直接抓住棋盘和国王时，食指指尖上的手指光标会取代手部光线。

可以在[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/InputSimulation.html)中找到有关 MRTK UX Tools 插件中提供的模拟手功能的详细信息。

现在，你的虚拟手可以与对象交互，接下来可以继续学习下一个教程，并添加用户界面和事件。

[下一节：5.添加按钮并重置棋子位置](unreal-uxt-ch5.md)
