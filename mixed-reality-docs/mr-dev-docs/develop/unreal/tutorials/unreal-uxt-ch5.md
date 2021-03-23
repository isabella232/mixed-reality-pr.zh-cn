---
title: 5. 添加按钮并重置棋子位置
description: 教程系列第 5 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款象棋应用
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: 8e16865e89c06c37f2932f1828bf8ca5551e6fce
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "96609688"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="53c1a-104">5.添加按钮并重置棋子位置</span><span class="sxs-lookup"><span data-stu-id="53c1a-104">5. Adding a button & resetting piece locations</span></span>

<span data-ttu-id="53c1a-105">在上一个教程中，向棋盘的 Pawn 和操控器组件添加了手势交互 Actor，使它们具有交互性。</span><span class="sxs-lookup"><span data-stu-id="53c1a-105">In the previous tutorial, you added Hand Interaction Actors to the Pawn and Manipulator components to the chess board to make them both interactive.</span></span> <span data-ttu-id="53c1a-106">在本部分中，你将继续使用混合现实工具包 UX Tools 插件，使用蓝图中的新函数和 Actor 引用构建象棋应用。</span><span class="sxs-lookup"><span data-stu-id="53c1a-106">In this section, you'll continue to use the Mixed Reality Toolkit UX Tools plugin to build out your chess app with new functions and Actor references in Blueprints.</span></span> <span data-ttu-id="53c1a-107">本部分结束时，你就可以打包混合现实应用，并将其部署到设备或仿真器中。</span><span class="sxs-lookup"><span data-stu-id="53c1a-107">By the end of this section, you'll be ready to package and deploy the mixed reality app on a device or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="53c1a-108">目标</span><span class="sxs-lookup"><span data-stu-id="53c1a-108">Objectives</span></span>

* <span data-ttu-id="53c1a-109">添加交互式按钮</span><span class="sxs-lookup"><span data-stu-id="53c1a-109">Adding an interactive button</span></span>
* <span data-ttu-id="53c1a-110">创建用于重置棋子位置的函数</span><span class="sxs-lookup"><span data-stu-id="53c1a-110">Creating a function to reset a pieces' location</span></span>
* <span data-ttu-id="53c1a-111">连接按钮，以在按下时触发此函数</span><span class="sxs-lookup"><span data-stu-id="53c1a-111">Hooking the button up to trigger the function when pressed</span></span>

## <a name="creating-a-reset-function"></a><span data-ttu-id="53c1a-112">创建重置函数</span><span class="sxs-lookup"><span data-stu-id="53c1a-112">Creating a reset function</span></span>

<span data-ttu-id="53c1a-113">第一个任务是创建一个函数蓝图，来将象棋棋子重置到场景中的原始位置。</span><span class="sxs-lookup"><span data-stu-id="53c1a-113">Your first task is to create a function blueprint that resets a chess piece to its original position in the scene.</span></span>

1.  <span data-ttu-id="53c1a-114">打开“WhiteKing”，选择“我的蓝图”中“函数”部分旁的“+”图标，将其命名为“重置位置”。    </span><span class="sxs-lookup"><span data-stu-id="53c1a-114">Open **WhiteKing**, select the **+** icon next to the **Functions** section in the **My Blueprint** and name it **Reset Location**.</span></span>

2.  <span data-ttu-id="53c1a-115">从蓝图网格拖动并释放“重置位置”的执行，以创建“SetActorRelativeTransform”节点。 </span><span class="sxs-lookup"><span data-stu-id="53c1a-115">Drag and release the execution from **Reset Location** on the Blueprint grid to create a **SetActorRelativeTransform** node.</span></span>
    * <span data-ttu-id="53c1a-116">此函数可设置 Actor 相对于其父级的变形（位置、旋转和缩放）。</span><span class="sxs-lookup"><span data-stu-id="53c1a-116">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="53c1a-117">将使用此函数来重置棋盘上国王的位置，即使棋盘已从其原始位置移动也无妨。</span><span class="sxs-lookup"><span data-stu-id="53c1a-117">You’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span>

3. <span data-ttu-id="53c1a-118">在事件图表中右击，选择“进行变形”，然后将其“位置”更改为“X = -26”、“Y = 4”和“Z = 0”。    </span><span class="sxs-lookup"><span data-stu-id="53c1a-118">Right-click inside the Event Graph, select **Make Transform**, and change its **Location** to **X = -26**, **Y = 4**, **Z = 0**.</span></span>
    * <span data-ttu-id="53c1a-119">将其“返回值”连接到“SetActorRelativeTransform”中的“新相对变形”引脚。  </span><span class="sxs-lookup"><span data-stu-id="53c1a-119">Connect its **Return Value** to the **New Relative Transform** pin in **SetActorRelativeTransform**.</span></span>

![Reset Location 函数](images/unreal-uxt/5-function.PNG)

<span data-ttu-id="53c1a-121">编译并保存项目，然后返回到主窗口。 </span><span class="sxs-lookup"><span data-stu-id="53c1a-121">**Compile** and **Save** the project before returning to the Main window.</span></span>


## <a name="adding-a-button"></a><span data-ttu-id="53c1a-122">添加按钮</span><span class="sxs-lookup"><span data-stu-id="53c1a-122">Adding a button</span></span>

<span data-ttu-id="53c1a-123">正确设置此函数后，接下来的任务是创建一个按钮，以在按它时触发函数。</span><span class="sxs-lookup"><span data-stu-id="53c1a-123">Now that the function is set up correctly, your next task is to create a button that fires it off when touched.</span></span>

1.  <span data-ttu-id="53c1a-124">单击“添加新项”>“蓝图类”，展开“所有类”部分，然后搜索“UxtPressableButtonActor”  。</span><span class="sxs-lookup"><span data-stu-id="53c1a-124">Click **Add New > Blueprint Class**, expand the **All Classes** section, and search for **UxtPressableButtonActor**.</span></span>
    * <span data-ttu-id="53c1a-125">将其命名为“ResetButton”，然后双击以打开蓝图</span><span class="sxs-lookup"><span data-stu-id="53c1a-125">Name it **ResetButton** and double click to open the Blueprint</span></span>

![从 HoloLens 2 样式按钮为新蓝图建立子类](images/unreal-uxt/5-subclass.PNG)

2. <span data-ttu-id="53c1a-127">确保在“组件”面板中选择了“ResetButton(自身)” 。</span><span class="sxs-lookup"><span data-stu-id="53c1a-127">Ensure **ResetButton(self)** is selected in the **Components** panel.</span></span> <span data-ttu-id="53c1a-128">在“详细信息”面板中，导航到“按钮”部分 。</span><span class="sxs-lookup"><span data-stu-id="53c1a-128">In the **Details** panel, navigate to the **Button** section.</span></span> <span data-ttu-id="53c1a-129">将默认“按钮标签”更改为“重置”，展开“按钮图标画笔”部分，然后按“打开图标画笔编辑器”按钮  。</span><span class="sxs-lookup"><span data-stu-id="53c1a-129">Change the default **Button Label** to "Reset", expand the **Button Icon Brush** section, and press the **Open Icon Brush Editor** button.</span></span>

![设置按钮上的标签和图标](images/unreal-uxt/5-buttonconfig.PNG)

<span data-ttu-id="53c1a-131">图标画笔编辑器随即打开，你可以使用该编辑器为按钮选择新图标。</span><span class="sxs-lookup"><span data-stu-id="53c1a-131">The Icon Brush Editor will open, which you can use to select a new icon for your button.</span></span>

![为按钮选择图标](images/unreal-uxt/5-iconbrusheditor.PNG)

<span data-ttu-id="53c1a-133">为配置按钮，还有很多其他的设置可以进行调整。</span><span class="sxs-lookup"><span data-stu-id="53c1a-133">There are plenty of other settings you can adjust to configure your button.</span></span> <span data-ttu-id="53c1a-134">若要了解有关 UXT 可按按钮组件的详细信息，请参阅[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html)。</span><span class="sxs-lookup"><span data-stu-id="53c1a-134">To learn more about the UXT Pressable Button component, check out the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html).</span></span>

3. <span data-ttu-id="53c1a-135">单击“组件”面板中的“ButtonComponent (继承)”，将“详细信息”面板向下滚动到“事件”部分   。</span><span class="sxs-lookup"><span data-stu-id="53c1a-135">Click **ButtonComponent (Inherited)** in the **Components** panel and scroll down the **Details** panel to the **Events** section.</span></span>
    * <span data-ttu-id="53c1a-136">单击“按钮按下时”旁的绿色 + 按钮，向事件图表添加事件，按下按钮时将调用该事件。</span><span class="sxs-lookup"><span data-stu-id="53c1a-136">Click the green **+** button next to **On Button Pressed** to add an event to the Event Graph, which will be called when the button is pressed.</span></span>

<span data-ttu-id="53c1a-137">此时，需要调用“WhiteKing”的“重置位置”函数，这需要在关卡中引用“WhiteKing”Actor。  </span><span class="sxs-lookup"><span data-stu-id="53c1a-137">From here, you’ll want to call **WhiteKing**’s **Reset Location** function, which needs a reference to the **WhiteKing** Actor in the Level.</span></span>

4.  <span data-ttu-id="53c1a-138">在“我的蓝图”面板中，导航到“变量”部分，然后单击 + 按钮，将变量命名为“WhiteKing”   。</span><span class="sxs-lookup"><span data-stu-id="53c1a-138">In the **My Blueprint** panel, navigate to the **Variables** section, click the **+** button, and name the variable **WhiteKing**.</span></span>
    * <span data-ttu-id="53c1a-139">在“详细信息”面板中，选择“变量类型”旁的下拉列表，搜索“WhiteKing”，然后选择“对象引用”   。</span><span class="sxs-lookup"><span data-stu-id="53c1a-139">In the **Details** panel, select the dropdown next to **Variable Type**, search for **WhiteKing**, and select the **Object Reference**.</span></span>
    * <span data-ttu-id="53c1a-140">选中“实例可编辑”旁的框，这使得可从主关卡设置变量。</span><span class="sxs-lookup"><span data-stu-id="53c1a-140">Check the box next to **Instance Editable**, which allows the variable to be set from the Main Level.</span></span>

![创建变量](images/unreal-uxt/5-var.PNG)

5.  <span data-ttu-id="53c1a-142">将 WhiteKing 变量从“我的蓝图 > 变量”拖放到“‘重置’按钮事件图表”中，然后选择“获取 WhiteKing”。</span><span class="sxs-lookup"><span data-stu-id="53c1a-142">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph and choose **Get WhiteKing**.</span></span>

## <a name="firing-the-function"></a><span data-ttu-id="53c1a-143">触发函数</span><span class="sxs-lookup"><span data-stu-id="53c1a-143">Firing the function</span></span>

<span data-ttu-id="53c1a-144">剩下的就是，在按下按钮时，正式触发重置函数。</span><span class="sxs-lookup"><span data-stu-id="53c1a-144">All that's left is to officially fire off the reset function when the button is pressed.</span></span>

1.  <span data-ttu-id="53c1a-145">拖动“WhiteKing”输出引脚并释放以放置新节点。</span><span class="sxs-lookup"><span data-stu-id="53c1a-145">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="53c1a-146">选择“Reset Location”函数。</span><span class="sxs-lookup"><span data-stu-id="53c1a-146">Select the **Reset Location** function.</span></span> <span data-ttu-id="53c1a-147">最后，将传出执行引脚从“按钮按下时”拖放到“重置位置”上的传入执行引脚。</span><span class="sxs-lookup"><span data-stu-id="53c1a-147">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="53c1a-148">编译和保存 ResetButton 蓝图，然后返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="53c1a-148">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span>

![从“按下按钮时”调用“Reset Location”函数](images/unreal-uxt/5-callresetloc.PNG)

2.  <span data-ttu-id="53c1a-150">将“ResetButton”拖到视口中，并将其位置设置为“X = 50”、“Y = -25”和“Z = 10”。  </span><span class="sxs-lookup"><span data-stu-id="53c1a-150">Drag **ResetButton** into the viewport and set its location to **X = 50**, **Y = -25**, and **Z = 10**.</span></span> <span data-ttu-id="53c1a-151">将其旋转设置为“Z = 180”。</span><span class="sxs-lookup"><span data-stu-id="53c1a-151">Set its rotation to **Z = 180**.</span></span> <span data-ttu-id="53c1a-152">在“默认值”下，将 WhiteKing 变量的值设置为“WhiteKing”。  </span><span class="sxs-lookup"><span data-stu-id="53c1a-152">Under **Default**, set the value of the **WhiteKing** variable to **WhiteKing**.</span></span>

![设置变量](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="53c1a-154">运行应用，将象棋棋子移动到新位置，然后按 HoloLens 2 样式按钮来查看重置逻辑正在运行！</span><span class="sxs-lookup"><span data-stu-id="53c1a-154">Run the app, move the chess piece to a new location, and press your HoloLens 2-style button to see the reset logic in action!</span></span>

<span data-ttu-id="53c1a-155">现在，你有了一个混合现实应用，其中包含可交互的棋子和棋盘，以及一个功能齐全的按钮，该按钮可重置棋子的位置。</span><span class="sxs-lookup"><span data-stu-id="53c1a-155">You now have a mixed reality app with an interactable chess piece and board, and a fully functioning button that resets the piece’s location.</span></span> <span data-ttu-id="53c1a-156">可以在 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) 存储库中找到目前完成的该应用程序。</span><span class="sxs-lookup"><span data-stu-id="53c1a-156">You can find the completed app up to this point in its [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) repo.</span></span> <span data-ttu-id="53c1a-157">请随意阅读本教程以外的内容并设置其余的棋子，以便按下“重置”按钮时重置整个棋盘。</span><span class="sxs-lookup"><span data-stu-id="53c1a-157">Feel free to go beyond this tutorial and set up the rest of the chess pieces so that the entire board is reset when you press the reset button.</span></span>

![在视口中结束场景](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="53c1a-159">你可以继续学习本教程的最后一部分，你将了解如何将应用打包并部署到设备或仿真器。</span><span class="sxs-lookup"><span data-stu-id="53c1a-159">You're ready to move on to the final section of this tutorial where you'll learn how to package and deploy the app to a device or emulator.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53c1a-160">此时，在将应用程序部署到设备或仿真器之前，应使用建议的 [Unreal 性能设置](../performance-recommendations-for-unreal.md)来更新项目。</span><span class="sxs-lookup"><span data-stu-id="53c1a-160">At this point, you should update your project with the recommended **[Unreal performance settings](../performance-recommendations-for-unreal.md)** before deploying your application to a device or emulator.</span></span>

[<span data-ttu-id="53c1a-161">下一节：6.打包并部署到设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="53c1a-161">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)
