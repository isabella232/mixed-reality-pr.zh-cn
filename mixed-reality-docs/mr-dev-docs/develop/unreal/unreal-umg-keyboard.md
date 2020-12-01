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
# <a name="umg-and-keyboard-in-unreal"></a><span data-ttu-id="7aeae-104">Unreal 中的 UMG 和键盘</span><span class="sxs-lookup"><span data-stu-id="7aeae-104">UMG and keyboard in Unreal</span></span>

<span data-ttu-id="7aeae-105">Unreal 运动图形 (UMG) 是 Unreal 引擎的内置 UI 系统，用于创建菜单和文本框等接口。</span><span class="sxs-lookup"><span data-stu-id="7aeae-105">Unreal Motion Graphics (UMG) is Unreal Engine’s built-in UI system, used to create interfaces such as menus and text boxes.</span></span> <span data-ttu-id="7aeae-106">用 UMG 生成的用户界面由小组件组成。</span><span class="sxs-lookup"><span data-stu-id="7aeae-106">User interfaces built with UMG consist of widgets.</span></span> <span data-ttu-id="7aeae-107">本指南将演示如何创建新的小组件，如何将其添加到世界空间，以及如何使用系统键盘作为示例在混合现实中实现与该小组件的交互。</span><span class="sxs-lookup"><span data-stu-id="7aeae-107">This guide will show you how to create a new widget, add it to world space, and enable interaction with that widget in mixed reality, using the system keyboard as an example.</span></span> <span data-ttu-id="7aeae-108">可以在官方 Unreal 引擎 [文档](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)中了解有关 UMG 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="7aeae-108">You can learn more about UMG in the official Unreal Engine [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html).</span></span> 

## <a name="create-a-new-widget"></a><span data-ttu-id="7aeae-109">创建新小组件</span><span class="sxs-lookup"><span data-stu-id="7aeae-109">Create a new widget</span></span>

- <span data-ttu-id="7aeae-110">创建小组件蓝图来布置游戏的 UI：</span><span class="sxs-lookup"><span data-stu-id="7aeae-110">Create a Widget Blueprint to lay out the game’s UI:</span></span>

![从 "Unreal" 菜单添加小组件蓝图的屏幕截图](images/unreal-umg-img-01.png)

- <span data-ttu-id="7aeae-112">打开新蓝图，并将组件从调色板添加到画布。</span><span class="sxs-lookup"><span data-stu-id="7aeae-112">Open the new blueprint and add components from the Palette to the canvas.</span></span>  <span data-ttu-id="7aeae-113">在这种情况下，我们已从 "Input" 节中添加了两个文本框组件：</span><span class="sxs-lookup"><span data-stu-id="7aeae-113">In this case we have added two Text Box components from the “Input” section:</span></span>

![突出显示并展开文本小组件组件的层次结构窗口的屏幕截图](images/unreal-umg-img-02.png)

- <span data-ttu-id="7aeae-115">在 "层次结构" 或 "设计器" 窗口中选择一个小组件，并在详细信息面板中修改参数。</span><span class="sxs-lookup"><span data-stu-id="7aeae-115">Select a widget in the Hierarchy or Designer window and modify parameters in the details panel.</span></span>  <span data-ttu-id="7aeae-116">在这种情况下，我们添加了一些默认的 "提示文本" 和淡色颜色，当光标悬停在文本框上方，以提供小组件已准备好进行交互的反馈时。</span><span class="sxs-lookup"><span data-stu-id="7aeae-116">In this case, we’ve added some default “Hint Text” and a tint color when the cursor is hovering over the text box to give feedback that the widget is ready to be interacted with.</span></span>  <span data-ttu-id="7aeae-117">当与以下内容交互时，文本框将在 HoloLens 上弹出虚拟键盘：</span><span class="sxs-lookup"><span data-stu-id="7aeae-117">A text box will pop up a virtual keyboard on HoloLens when it is interacted with:</span></span>

!["层次结构" 窗口中已修改参数的屏幕截图](images/unreal-umg-img-03.png)

- <span data-ttu-id="7aeae-119">还可以在 "详细信息" 面板中订阅事件：</span><span class="sxs-lookup"><span data-stu-id="7aeae-119">Events can also be subscribed to in the details panel:</span></span>

![详细信息面板中事件的屏幕截图](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a><span data-ttu-id="7aeae-121">向世界空间添加小组件</span><span class="sxs-lookup"><span data-stu-id="7aeae-121">Add a Widget to World Space</span></span>

- <span data-ttu-id="7aeae-122">创建新的执行组件，添加小组件组件，并将执行组件添加到场景：</span><span class="sxs-lookup"><span data-stu-id="7aeae-122">Create a new Actor, add a Widget component, and add the actor to the scene:</span></span>

![附加了小组件的参与者的屏幕截图](images/unreal-umg-img-05.png)

- <span data-ttu-id="7aeae-124">在小组件的详细信息面板中，将 " **小组件" 类** 设置为先前创建的小组件蓝图：</span><span class="sxs-lookup"><span data-stu-id="7aeae-124">In the details panel for the Widget, set the **Widget Class** to the Widget Blueprint created earlier:</span></span>

![带有小组件类集的蓝图详细信息面板的屏幕截图](images/unreal-umg-img-06.png)

- <span data-ttu-id="7aeae-126">对于文本小组件，请确保未选中 " **接收硬件输入** "，因此我们仅从虚拟键盘更新其文本：</span><span class="sxs-lookup"><span data-stu-id="7aeae-126">For a text Widget, ensure **Receive Hardware Input** is unchecked so we only update its text from the virtual keyboard:</span></span>

![未选中带有接收硬件输入的交互部分的屏幕截图](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a><span data-ttu-id="7aeae-128">小组件交互</span><span class="sxs-lookup"><span data-stu-id="7aeae-128">Widget Interaction</span></span>

<span data-ttu-id="7aeae-129">UMG 小组件通常从鼠标接收输入。</span><span class="sxs-lookup"><span data-stu-id="7aeae-129">UMG Widgets typically receive input from a mouse.</span></span>  <span data-ttu-id="7aeae-130">在 HoloLens 或 VR 上，我们需要模拟带有小组件交互组件的鼠标以获取相同的事件。</span><span class="sxs-lookup"><span data-stu-id="7aeae-130">On HoloLens or VR, we need to simulate a mouse with a Widget Interaction component to get the same events.</span></span>

- <span data-ttu-id="7aeae-131">创建新的执行组件，添加 **小组件交互** 组件，并将执行组件添加到场景：</span><span class="sxs-lookup"><span data-stu-id="7aeae-131">Create a new Actor, add a **Widget Interaction** component, and add the actor to your scene:</span></span>

![突出显示小组件交互组件的新执行组件的屏幕截图](images/unreal-umg-img-08.png)

- <span data-ttu-id="7aeae-133">在小组件交互组件的 "详细信息" 面板中，将 "交互距离" 设置为所需距离，将 " **交互源** " 设置为 " **自定义**"，并将 " **显示调试** " 设置为 " **true**"：</span><span class="sxs-lookup"><span data-stu-id="7aeae-133">In the details panel for the Widget Interaction component, set the interaction distance to the desired distance, set the **Interaction Source** to **custom**, and for development, set **Show Debug** to **true**:</span></span>

![小组件交互和调试组件属性的屏幕截图](images/unreal-umg-img-09.png)

<span data-ttu-id="7aeae-135">交互源的默认值是 "World"，它应基于小组件交互组件的世界位置发送 raycasts，但在 AR 和 VR 中，这似乎不是这样。</span><span class="sxs-lookup"><span data-stu-id="7aeae-135">The default for Interaction Source is “World”, which should send raycasts based on the world position of the Widget Interaction component, but in AR and VR this does not appear to be the case.</span></span>  <span data-ttu-id="7aeae-136">在开发过程中启用 "显示调试" 并向小组件添加悬停淡色非常重要，请检查小组件交互组件是否正在执行所需的操作。</span><span class="sxs-lookup"><span data-stu-id="7aeae-136">Enabling “Show Debug” and adding a hover tint to widgets while developing is important to sanity check the widget interaction component is doing what you expect.</span></span>  <span data-ttu-id="7aeae-137">解决方法是使用自定义源，并在右侧的事件图中设置 raycast。</span><span class="sxs-lookup"><span data-stu-id="7aeae-137">The workaround is to use a custom source and set the raycast in the event graph from the hand ray.</span></span>  

<span data-ttu-id="7aeae-138">这里，我们从事件滴答中调用此内容：</span><span class="sxs-lookup"><span data-stu-id="7aeae-138">Here we are calling this from Event Tick:</span></span>

![事件滴答的蓝图](images/unreal-umg-img-10.png)

<span data-ttu-id="7aeae-140">然后，将虚拟鼠标指针事件添加到对 HoloLens 输入做出反应的小组件交互组件。</span><span class="sxs-lookup"><span data-stu-id="7aeae-140">Then add virtual mouse pointer events to the widget interaction component reacting to HoloLens input.</span></span>  <span data-ttu-id="7aeae-141">在这种情况下，请在 grasped 时发送鼠标左键按下事件，并在 not grasped 时发送鼠标左键释放事件：</span><span class="sxs-lookup"><span data-stu-id="7aeae-141">In this case, send a Left Mouse press event when the hand is grasped, and a Left Mouse release event when not grasped:</span></span>

![添加了虚拟鼠标指针事件的蓝图](images/unreal-umg-img-13.png)

<span data-ttu-id="7aeae-143">现在，当你将应用程序部署到 HoloLens 2 时，你将看到右手的手写。</span><span class="sxs-lookup"><span data-stu-id="7aeae-143">Now, when you deploy the app to the HoloLens 2, you’ll see a hand ray extending from your right hand.</span></span> <span data-ttu-id="7aeae-144">如果将其定向到一个可编辑的文本框，然后单击一下，系统键盘将显示在您的前面，并允许您输入文本。</span><span class="sxs-lookup"><span data-stu-id="7aeae-144">If you direct it at one of the editable text boxes and air tap, the system keyboard will appear in front of you and allow you to enter text.</span></span> 
 
> [!NOTE]
> <span data-ttu-id="7aeae-145">HoloLens 系统键盘需要 Unreal 引擎4.26 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7aeae-145">The HoloLens system keyboard requires Unreal Engine 4.26 or later.</span></span> <span data-ttu-id="7aeae-146">此外，仅当应用程序在设备上运行时，才会显示在应用程序从 Unreal 编辑器流式传输到耳机时的键盘。</span><span class="sxs-lookup"><span data-stu-id="7aeae-146">Additionally, the keyboard will not appear when your app is being streamed from the Unreal editor to the headset, only when the app is running on device.</span></span>

## <a name="see-also"></a><span data-ttu-id="7aeae-147">另请参阅：</span><span class="sxs-lookup"><span data-stu-id="7aeae-147">See Also:</span></span>
* [<span data-ttu-id="7aeae-148">Unreal 的 UMG 文档</span><span class="sxs-lookup"><span data-stu-id="7aeae-148">Unreal's UMG documentation</span></span>](https://docs.unrealengine.com/Engine/UMG/index.html)
* [<span data-ttu-id="7aeae-149">Unreal 的 UMG 教程</span><span class="sxs-lookup"><span data-stu-id="7aeae-149">Unreal's UMG tutorials</span></span>](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
