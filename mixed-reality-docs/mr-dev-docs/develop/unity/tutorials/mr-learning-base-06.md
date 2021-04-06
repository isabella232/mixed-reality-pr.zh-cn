---
title: 创建用户界面
description: 本课程介绍如何使用混合现实工具包 (MRTK) 创建静态和动态用户界面。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 预制件, 全息影像, 工具提示
ms.localizationpriority: high
ms.openlocfilehash: 4400ce669863b719b409e11076ceb5689e21893e
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982970"
---
# <a name="6-creating-user-interfaces"></a><span data-ttu-id="b65bd-104">6.创建用户界面</span><span class="sxs-lookup"><span data-stu-id="b65bd-104">6. Creating user interfaces</span></span>

<span data-ttu-id="b65bd-105">本教程介绍如何使用 MRTK 的按钮和菜单预制件以及 Unity 的 TextMeshPro 组件来创建简单的用户界面。</span><span class="sxs-lookup"><span data-stu-id="b65bd-105">In this tutorial, you will learn how to create a simple user interface using MRTK's button and menu prefabs alongside Unity's TextMeshPro component.</span></span> <span data-ttu-id="b65bd-106">还介绍如何配置这些按钮以触发事件，并添加动态工具提示 UI 元素以向用户提供其他信息。</span><span class="sxs-lookup"><span data-stu-id="b65bd-106">You will also learn how to configure the buttons to trigger events and add dynamic tooltip UI elements to provide the user with additional information.</span></span>

## <a name="objectives"></a><span data-ttu-id="b65bd-107">目标</span><span class="sxs-lookup"><span data-stu-id="b65bd-107">Objectives</span></span>

* <span data-ttu-id="b65bd-108">了解如何组织集合中的按钮</span><span class="sxs-lookup"><span data-stu-id="b65bd-108">Learn how to organize buttons in a collection</span></span>
* <span data-ttu-id="b65bd-109">了解如何使用 MRTK 的菜单预制件</span><span class="sxs-lookup"><span data-stu-id="b65bd-109">Learn how to use MRTK's menu prefabs</span></span>
* <span data-ttu-id="b65bd-110">了解如何使用 UI 菜单和按钮来与全息影像交互</span><span class="sxs-lookup"><span data-stu-id="b65bd-110">Learn how to interact with holograms using UI menus and buttons</span></span>
* <span data-ttu-id="b65bd-111">了解如何添加文本元素</span><span class="sxs-lookup"><span data-stu-id="b65bd-111">Learn how to add text elements</span></span>
* <span data-ttu-id="b65bd-112">了解如何在对象上动态生成工具提示</span><span class="sxs-lookup"><span data-stu-id="b65bd-112">Learn how to spawn tooltips on objects dynamically</span></span>

## <a name="creating-a-static-panel-of-buttons"></a><span data-ttu-id="b65bd-113">创建按钮的静态面板</span><span class="sxs-lookup"><span data-stu-id="b65bd-113">Creating a static panel of buttons</span></span>

<span data-ttu-id="b65bd-114">在“层次结构”窗口中，右键单击“RoverExplorer”对象，然后选择“创建空白项”添加一个空对象作为 RoverExplorer 的子对象，将该对象命名为“Buttons”，并按如下所述配置“转换”组件   ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-114">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **Buttons**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="b65bd-115">**位置**：X = -0.6，Y = 0.036，Z = -0.5</span><span class="sxs-lookup"><span data-stu-id="b65bd-115">**Position**: X = -0.6, Y = 0.036, Z = -0.5</span></span>
* <span data-ttu-id="b65bd-116">**旋转**：X = 90, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="b65bd-116">**Rotation**: X = 90, Y = 0, Z = 0</span></span>
* <span data-ttu-id="b65bd-117">**缩放**：X = 1，Y = 1，Z = 1</span><span class="sxs-lookup"><span data-stu-id="b65bd-117">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![选中并定位了新创建的 Buttons 对象的 Unity](images/mr-learning-base/base-06-section1-step1-1.png)

<span data-ttu-id="b65bd-119">在“项目”窗口中，导航至“资产” > “MRTK.Tutorials.GettingStarted” > “预制件”文件夹，然后单击“PressableRoundButton”预制件并将其拖动到 Buttons 对象上，然后右键单击“PressableRoundButton”并选择“重复”以创建副本，重复此操作，直到共有三个 PressableRoundButton 对象     ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-119">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **PressableRoundButton** prefab on to the **Buttons** object, then right-click on the PressableRoundButton and select **Duplicate** to create a copy, repeat until you have a total of three PressableRoundButton objects:</span></span>

![新添加了 PressableRoundButton 预制件的 Unity](images/mr-learning-base/base-06-section1-step1-2.png)

<span data-ttu-id="b65bd-121">在“层次结构”窗口中选择“Buttons”对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“GridObjectCollection”组件，并按如下所述配置该组件  ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-121">In the Hierarchy window, select the **Buttons** object, then in the Inspector window, use the **Add Component** button to add the **GridObjectCollection** component and configure it as follows:</span></span>

* <span data-ttu-id="b65bd-122">**排序类型**：子顺序</span><span class="sxs-lookup"><span data-stu-id="b65bd-122">**Sort Type**: Child Order</span></span>
* <span data-ttu-id="b65bd-123">**布局**：水平</span><span class="sxs-lookup"><span data-stu-id="b65bd-123">**Layout**: Horizontal</span></span>
* <span data-ttu-id="b65bd-124">**单元格宽度**：0.2</span><span class="sxs-lookup"><span data-stu-id="b65bd-124">**Cell Width**: 0.2</span></span>
* <span data-ttu-id="b65bd-125">**定位点**：中部左对齐</span><span class="sxs-lookup"><span data-stu-id="b65bd-125">**Anchor**: Middle Left</span></span>

<span data-ttu-id="b65bd-126">然后单击“更新集合”按钮以更新 Buttons 对象的子对象的位置：</span><span class="sxs-lookup"><span data-stu-id="b65bd-126">Then click the **Update Collection** button to update the position of the Buttons object's child objects:</span></span>

![添加、配置并应用了 GridObjectCollection 组件的 Unity“按钮”对象](images/mr-learning-base/base-06-section1-step1-3.png)

<span data-ttu-id="b65bd-128">在“层次结构”窗口中，将按钮命名为“提示”、“分解”和“重置”  。</span><span class="sxs-lookup"><span data-stu-id="b65bd-128">In the Hierarchy window, name the buttons **Hints**, **Explode**, and **Reset**.</span></span>

<span data-ttu-id="b65bd-129">为每个按钮选择“SeeItaysLabel” > “TextMeshPro”子对象，然后在“检查器”窗口中，更改相应的“TextMeshPro - Text”组件文本以匹配按钮名称  ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-129">For each button, select the **SeeItSayItLabel** > **TextMeshPro** child object, then in the Inspector window, change the respective **TextMeshPro - Text** component text to match the button names:</span></span>

![配置了按钮文本标签的 Unity](images/mr-learning-base/base-06-section1-step1-4.png)

<span data-ttu-id="b65bd-131">完成后，折叠按钮对象的子对象。</span><span class="sxs-lookup"><span data-stu-id="b65bd-131">Once done, collapse the Buttons object's child objects.</span></span>

<span data-ttu-id="b65bd-132">在“层次结构”窗口中，选择“提示”按钮对象，然后在“检查器”窗口中配置 Interactable.OnClick () 事件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-132">In the Hierarchy window, select the **Hints** button object, then in the Inspector window, configure the **Interactable.OnClick ()** event as follows:</span></span>

* <span data-ttu-id="b65bd-133">向“无(对象)”字段分配“RoverAssembly”对象 </span><span class="sxs-lookup"><span data-stu-id="b65bd-133">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b65bd-134">从“无函数”下拉列表中，选择“PlacementHintsController” > “TogglePlacementHints ()”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="b65bd-134">From the **No Function** dropdown, select **PlacementHintsController** > **TogglePlacementHints ()** to set this function as the action to be executed when the event is triggered</span></span>

![配置了“提示”按钮对象 OnClick 事件的 Unity](images/mr-learning-base/base-06-section1-step1-5.png)

> [!TIP]
> <span data-ttu-id="b65bd-136">可交互组件是一体式的容器，它使所有对象都能轻松交互并响应输入。</span><span class="sxs-lookup"><span data-stu-id="b65bd-136">The Interactable component is an all-in-one container to make any object easily interactable and responsive to input.</span></span> <span data-ttu-id="b65bd-137">“可交互”用作各种类型的输入的一个笼统术语，包括触摸、手射线和语音等等，它将这些交互传送到事件和视觉主题响应中。</span><span class="sxs-lookup"><span data-stu-id="b65bd-137">Interactable acts as a catch-all for all types of input including touch, hand rays, speech, etc. and funnels these interactions into events and visual theme responses.</span></span> <span data-ttu-id="b65bd-138">若要了解如何为不同的输入类型配置它，以及如何自定义它的视觉主题，可参阅 [MRTK 文档门户](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/)中的[可交互](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)指南。</span><span class="sxs-lookup"><span data-stu-id="b65bd-138">To learn how to configure it for different input types and customize it's visual theme, you can refer to the [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/).</span></span>

<span data-ttu-id="b65bd-139">在“层次结构”窗口中，选择“分解”按钮对象，然后在“检查器”窗口中配置 Interactable.OnClick () 事件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-139">In the Hierarchy window, select the **Explode** button object, then in the Inspector window, configure the **Interactable.OnClick ()** event as follows:</span></span>

* <span data-ttu-id="b65bd-140">向“无(对象)”字段分配“RoverAssembly”对象 </span><span class="sxs-lookup"><span data-stu-id="b65bd-140">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b65bd-141">从“无函数”下拉列表中，选择“ExplodedViewController” > “ToggleExplodedView ()”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="b65bd-141">From the **No Function** dropdown, select **ExplodedViewController** > **ToggleExplodedView ()** to set this function as the action to be executed when the event is triggered</span></span>

![配置了“分解”按钮对象 OnClick 事件的 Unity](images/mr-learning-base/base-06-section1-step1-6.png)

<span data-ttu-id="b65bd-143">按“播放”按钮进入游戏模式，然后按住空格键以激活操作手，然后使用鼠标按“提示”按钮来切换放置提示对象的可见性：</span><span class="sxs-lookup"><span data-stu-id="b65bd-143">Press the Play button to enter Game mode, then press-and-hold the space bar button to activate the hand and use the mouse to press the **Hints** button to toggle the visibility of the placement hint objects:</span></span>

![显示正在按下“提示”按钮的 Unity“播放”模式分屏视图](images/mr-learning-base/base-06-section1-step1-7.png)

<span data-ttu-id="b65bd-145">然后按“分解”按钮以启用或关闭“分解”视图：</span><span class="sxs-lookup"><span data-stu-id="b65bd-145">and the **Explode** button to toggle the exploded view on and off:</span></span>

![显示正在按下“拆分”按钮的 Unity“播放”模式分屏视图](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a><span data-ttu-id="b65bd-147">创建跟随用户的动态菜单</span><span class="sxs-lookup"><span data-stu-id="b65bd-147">Creating a dynamic menu that follows the user</span></span>

<span data-ttu-id="b65bd-148">在“项目”窗口中，导航到“包” > “混合现实工具包基础” > “SDK” > “功能” > “UX” > “预制件” > “菜单”文件夹，单击“NearMenu4x1”预制件并将其拖动到“层次结构”窗口中，然后将其“转换”位置设置为 X = 0、Y = -0.4、Z = 0 并按如下所述进行配置        ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-148">In the Project window, navigate to the **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **Menus** folder, click-and-drag the **NearMenu4x1** prefab into the Hierarchy window, set its Transform **Position** to X = 0, Y = -0.4, Z = 0 and configure it as follows:</span></span>

* <span data-ttu-id="b65bd-149">验证 SolverHandler 组件的“跟踪的目标类型”是否设置为“头部”  </span><span class="sxs-lookup"><span data-stu-id="b65bd-149">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="b65bd-150">选中“RadialView”解算器旁的复选框，使其默认为启用</span><span class="sxs-lookup"><span data-stu-id="b65bd-150">Check the checkbox next to the **RadialView** Solver component so it is enabled by default</span></span>

![选中了新增的 near menu 预制件的 Unity](images/mr-learning-base/base-06-section2-step1-1.png)

<span data-ttu-id="b65bd-152">在“层次结构”窗口中，将对象重命名为“Menu”，然后展开其 ButtonCollection 子对象以显示四个按钮 ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-152">In the Hierarchy window, rename the object to **Menu**, then expand its **ButtonCollection** child object to reveal the four buttons:</span></span>

![选中了“菜单”对象并展开了 ButtonCollection 对象的 Unity](images/mr-learning-base/base-06-section2-step1-2.png)

<span data-ttu-id="b65bd-154">将 ButtonCollection 中的第一个按钮重命名为“指示器”，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b65bd-154">Rename the first button in the ButtonCollection to Indicator, then in the Inspector window, configure the Button Config Helper (Script) component as follows:</span></span>

* <span data-ttu-id="b65bd-155">更改主标签文本以匹配按钮的名称</span><span class="sxs-lookup"><span data-stu-id="b65bd-155">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="b65bd-156">向“无(对象)”字段分配 V 形外观的“指示器”对象</span><span class="sxs-lookup"><span data-stu-id="b65bd-156">Assign the Indicator object that looks like a chevron, to the None (Object) field</span></span>
* <span data-ttu-id="b65bd-157">从“无函数”下拉列表中，选择“GameObject” > “SetActive (bool)”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="b65bd-157">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="b65bd-158">验证是否已选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="b65bd-158">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="b65bd-159">将图标更改为“搜索”图标</span><span class="sxs-lookup"><span data-stu-id="b65bd-159">Change the **Icon** to the 'search' icon</span></span>

![配置了“指示器”按钮对象“按钮配置帮助程序”的 Unity](images/mr-learning-base/base-06-section2-step1-3.png)

<span data-ttu-id="b65bd-161">若要禁用 V 形“指示器”对象，请在“层次结构”窗口中选择 V 形外观的“指示器”对象，然后在“检查器”窗口中：</span><span class="sxs-lookup"><span data-stu-id="b65bd-161">To disable the chevron Indicator object, in the Hierarchy window, select the Indicator object that looks like chevron, then in the Inspector window:</span></span>

* <span data-ttu-id="b65bd-162">取消选中其名称旁的复选框，以使其在默认情况下处于非活动状态</span><span class="sxs-lookup"><span data-stu-id="b65bd-162">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="b65bd-163">使用“添加组件”按钮添加“方向指示器控制器(脚本)”组件 </span><span class="sxs-lookup"><span data-stu-id="b65bd-163">Use the **Add Component** button to add the **Directional Indicator Controller (Script)** component</span></span>

![选中并禁用了“指示器”对象、添加了 DirectionalIndicatorController 组件的 Unity](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="b65bd-165">现在，当应用程序启动时，会默认禁用 V 形指示器，并且可以通过按“指标器”按钮来启用。</span><span class="sxs-lookup"><span data-stu-id="b65bd-165">Now, when the app starts, the chevron Indicator is disabled by default and can be enabled by pressing the Indicator button.</span></span>

<span data-ttu-id="b65bd-166">将第二个按钮重命名为“TapToPlace”，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-166">Rename the second button to **TapToPlace**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="b65bd-167">更改主标签文本以匹配按钮的名称</span><span class="sxs-lookup"><span data-stu-id="b65bd-167">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="b65bd-168">向“无(对象)”字段分配“RoverExplorer”>“RoverAssembly”对象 </span><span class="sxs-lookup"><span data-stu-id="b65bd-168">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b65bd-169">在“无函数”下拉列表中选择“TapToPlace” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="b65bd-169">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b65bd-170">验证是否已选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="b65bd-170">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="b65bd-171">将图标更改为“带有射线的手”图标</span><span class="sxs-lookup"><span data-stu-id="b65bd-171">Change the **Icon** to the 'hand with ray' icon</span></span>

![配置了 TapToPlace 按钮对象“按钮配置帮助程序”的 Unity](images/mr-learning-base/base-06-section2-step1-5.png)

<span data-ttu-id="b65bd-173">在“层次结构”窗口中选择“RoverAssembly”对象，然后在“检查器”窗口中配置“点击放置(脚本)”组件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-173">In the Hierarchy window, select the **RoverAssembly** object, then in the Inspector window, configure the **Tap To Place (Script)** component as follows:</span></span>

* <span data-ttu-id="b65bd-174">取消选中其名称旁的复选框，以使其在默认情况下处于非活动状态</span><span class="sxs-lookup"><span data-stu-id="b65bd-174">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="b65bd-175">在“On Placing Stopped ()”事件部分中，单击 + 图标以添加新事件 ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-175">In the **On Placing Stopped ()** event section, click the **+** icon to add a new event:</span></span>
* <span data-ttu-id="b65bd-176">向“无(对象)”字段分配“RoverExplorer”>“RoverAssembly”对象 </span><span class="sxs-lookup"><span data-stu-id="b65bd-176">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b65bd-177">在“无函数”下拉列表中选择“TapToPlace” > “启用布尔”，以便在触发事件时更新此属性  </span><span class="sxs-lookup"><span data-stu-id="b65bd-177">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b65bd-178">验证是否已取消选中参数复选框</span><span class="sxs-lookup"><span data-stu-id="b65bd-178">Verify that the argument checkbox is **unchecked**</span></span>

![重新配置了 TapToPlace 组件的 Unity](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> <span data-ttu-id="b65bd-180">现在，当应用程序启动时，默认情况下会禁用“点击放置”功能，并且可以通过按“点击放置”按钮来启用。</span><span class="sxs-lookup"><span data-stu-id="b65bd-180">Now, when the app starts, the Tap to Place functionality is disabled by default and can be enabled by pressing the Tap to Place button.</span></span> <span data-ttu-id="b65bd-181">此外，当“点击放置”完成时，它会自动禁用。</span><span class="sxs-lookup"><span data-stu-id="b65bd-181">Additionally, when the tap to place is completed, it will disable itself.</span></span>

## <a name="adding-text-to-the-scene"></a><span data-ttu-id="b65bd-182">向场景添加文本</span><span class="sxs-lookup"><span data-stu-id="b65bd-182">Adding text to the scene</span></span>

<span data-ttu-id="b65bd-183">在“层次结构”窗口中，右键单击“Table”对象，然后选择“3D 对象” > “Text - TextMeshPro”添加一个文本对象作为 Table 的子对象，然后在“检查器”窗口中按如下所述配置“矩形转换”组件   ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-183">In the Hierarchy window, right-click on the **Table** object and select **3D Object** > **Text - TextMeshPro** to add a text object as a child of the Table object, then in the Inspector window, configure the **Rect Transform** component as follows:</span></span>

* <span data-ttu-id="b65bd-184">将“位置 Y”更改为 1</span><span class="sxs-lookup"><span data-stu-id="b65bd-184">Change **Pos Y** to 1</span></span>
* <span data-ttu-id="b65bd-185">将“宽度”更改为 1</span><span class="sxs-lookup"><span data-stu-id="b65bd-185">Change **Width** to 1</span></span>
* <span data-ttu-id="b65bd-186">将“高度”更改为 1</span><span class="sxs-lookup"><span data-stu-id="b65bd-186">Change **Height** to 1</span></span>
* <span data-ttu-id="b65bd-187">将“旋转 X”更改为 90</span><span class="sxs-lookup"><span data-stu-id="b65bd-187">Change **Rotation X** to 90</span></span>

![选中了新创建的 TextMeshPro 对象的 Unity](images/mr-learning-base/base-06-section3-step1-1.png)

<span data-ttu-id="b65bd-189">然后按如下所述配置“TextMeshPro - Text”组件：</span><span class="sxs-lookup"><span data-stu-id="b65bd-189">Then configure the **TextMeshPro - Text** component as follows::</span></span>

* <span data-ttu-id="b65bd-190">将“文本”更改为漫游者探测器</span><span class="sxs-lookup"><span data-stu-id="b65bd-190">Change **Text** to Rover Explorer</span></span>
* <span data-ttu-id="b65bd-191">将“字形”更改为粗体</span><span class="sxs-lookup"><span data-stu-id="b65bd-191">Change **Font Style** to Bold</span></span>
* <span data-ttu-id="b65bd-192">将“字体大小”更改为 1</span><span class="sxs-lookup"><span data-stu-id="b65bd-192">Change **Font Size** to 1</span></span>
* <span data-ttu-id="b65bd-193">将“额外设置”>“边距”更改为 0.03</span><span class="sxs-lookup"><span data-stu-id="b65bd-193">Change Extra Settings > **Margins** to 0.03</span></span>

![配置了 TextMeshPro 组件的 Unity](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a><span data-ttu-id="b65bd-195">添加工具提示</span><span class="sxs-lookup"><span data-stu-id="b65bd-195">Adding tooltips</span></span>

<span data-ttu-id="b65bd-196">在“项目”窗口中，导航到“包” > “混合现实工具包基础” > “SDK” > “功能” > “UX” > “预制件” > “工具提示”文件夹，以查找工具提示预制件      ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-196">In the Project window, navigate to the **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![选中了 ToolTips 文件夹的 Unity 项目窗口](images/mr-learning-base/base-06-section4-step1-1.png)

<span data-ttu-id="b65bd-198">在“层次结构”窗口中展开“RoverExplorer”>“RoverParts”对象并选择其所有子探测器部件对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“ToolTipSpawner”组件并按如下所述配置  ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-198">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects, then in the Inspector window, use the **Add Component** button to add the **ToolTipSpawner** component and configure it as follows:</span></span>

* <span data-ttu-id="b65bd-199">确保选中“启用焦点”复选框，以要求用户查看部件以显示工具提示</span><span class="sxs-lookup"><span data-stu-id="b65bd-199">Ensure the **Focus Enabled** checkbox is checked to require the user to look at the part for the tooltip to appear</span></span>
* <span data-ttu-id="b65bd-200">从“项目”窗口中将“简单行工具提示”预制件分配给“预制件”字段 </span><span class="sxs-lookup"><span data-stu-id="b65bd-200">Assign the **Simple Line ToolTip** prefab from the Project window to the **Prefab** field</span></span>
* <span data-ttu-id="b65bd-201">将“工具提示替代设置”>“设置模式”更改为“替代” </span><span class="sxs-lookup"><span data-stu-id="b65bd-201">Change the ToolTip Override Settings > **Settings Mode** to **Override**</span></span>
* <span data-ttu-id="b65bd-202">将“工具提示替代设置”>“手动透视本地位置 Y”更改为 1.5 </span><span class="sxs-lookup"><span data-stu-id="b65bd-202">Change the ToolTip Override Settings > **Manual Pivot Local Position Y** to **1.5**</span></span>

![选中了所有探测器部件对象、添加和配置了 ToolTipSpawner 组件的 Unity](images/mr-learning-base/base-06-section4-step1-2.png)

<span data-ttu-id="b65bd-204">在“层次结构”窗口中选择第一个探测器部件，“RoverParts”>“Camera_Part”，并按如下所述配置“ToolTipSpawner”组件 ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-204">In the Hierarchy window, select the first rover part, RoverParts > **Camera_Part**, and configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="b65bd-205">更改“工具提示文本”以反映部件的名称，即“照相机” </span><span class="sxs-lookup"><span data-stu-id="b65bd-205">Change **Tool Tip Text** to reflect the name of the part, i.e., **Camera**</span></span>

![配置了 Camera ToolTipText 的 Unity](images/mr-learning-base/base-06-section4-step1-3.png)

<span data-ttu-id="b65bd-207">对每个探测器部件对象重复此步骤以配置“ToolTipSpawner”组件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="b65bd-207">**Repeat** this step for each of the rover part objects to configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="b65bd-208">对于 Generator_Part，请将“工具提示文本”更改为“生成器”  </span><span class="sxs-lookup"><span data-stu-id="b65bd-208">For the **Generator_Part**, change the **Tool Tip Text** to **Generator**</span></span>
* <span data-ttu-id="b65bd-209">对于 Lights_Part，请将“工具提示文本”更改为“灯光”  </span><span class="sxs-lookup"><span data-stu-id="b65bd-209">For the **Lights_Part**, change the **Tool Tip Text** to **Lights**</span></span>
* <span data-ttu-id="b65bd-210">对于 UHFAntenna_Part，请将“工具提示文本”更改为“UHF 天线”字段  </span><span class="sxs-lookup"><span data-stu-id="b65bd-210">For the **UHFAntenna_Part**, change the **Tool Tip Text** to **UHF Antenna** field</span></span>
* <span data-ttu-id="b65bd-211">对于 Spectrometer_Part，请将“工具提示文本”更改为“分光仪”  </span><span class="sxs-lookup"><span data-stu-id="b65bd-211">For the **Spectrometer_Part**, change the **Tool Tip Text** to **Spectrometer**</span></span>

<span data-ttu-id="b65bd-212">按下“播放”按钮进入“游戏”模式，然后在按住鼠标右键的同时移动鼠标，直到视线瞄准部件之一，并将显示该部件的工具提示：</span><span class="sxs-lookup"><span data-stu-id="b65bd-212">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the parts and the tooltip for that part will be displayed:</span></span>

![显示通过视线触发的工具提示的 Unity“播放”模式分屏视图](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="b65bd-214">祝贺</span><span class="sxs-lookup"><span data-stu-id="b65bd-214">Congratulations</span></span>

<span data-ttu-id="b65bd-215">在本教程中，你了解了如何使用 MRTK 提供的按钮和菜单预制件以及 Unity 的 TextMeshPro 组件来创建简单的用户界面，以及如何配置按钮以在按下按钮时触发事件。</span><span class="sxs-lookup"><span data-stu-id="b65bd-215">In this tutorial, you learned how to create a simple user interface using MRTK's provided button and menu prefabs alongside Unity's TextMeshPro component and how to configure the buttons to trigger events when they are pressed.</span></span> <span data-ttu-id="b65bd-216">还了解了如何添加动态工具提示 UI 元素以向用户提供其他信息。</span><span class="sxs-lookup"><span data-stu-id="b65bd-216">You also learned how to add dynamic tooltip UI elements to provide the user with additional information.</span></span>

> [!div class="nextstepaction"]
>[<span data-ttu-id="b65bd-217">下一教程：7.与 3D 对象交互</span><span class="sxs-lookup"><span data-stu-id="b65bd-217">Next Tutorial: 7. Interacting with 3D objects</span></span>](mr-learning-base-07.md)
