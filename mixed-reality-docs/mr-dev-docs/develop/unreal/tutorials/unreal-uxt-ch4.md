---
title: 4. 使场景具有交互性
description: 教程系列第 4 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款象棋应用
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: 771dd4028adfacb27544e632aa0f355d3bc91c66
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712590"
---
# <a name="4-making-your-scene-interactive"></a><span data-ttu-id="c13b5-104">4.使场景具有交互性</span><span class="sxs-lookup"><span data-stu-id="c13b5-104">4. Making your scene interactive</span></span>

<span data-ttu-id="c13b5-105">在上一个教程中，你添加了 ARSession、Pawn 和游戏模式，以完成针对象棋应用的混合现实设置。</span><span class="sxs-lookup"><span data-stu-id="c13b5-105">In the previous tutorial, you added an ARSession, Pawn, and Game Mode to complete the mixed reality setup for the chess app.</span></span> <span data-ttu-id="c13b5-106">本部分重点介绍如何使用开放源代码的[混合现实工具包 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) 插件，它提供了使场景具有交互性的工具。</span><span class="sxs-lookup"><span data-stu-id="c13b5-106">This section focuses on using the open source [Mixed Reality Toolkit UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) plugin, which provides tools to make the scene interactive.</span></span> <span data-ttu-id="c13b5-107">本部分结束时，棋子将按照用户输入移动。</span><span class="sxs-lookup"><span data-stu-id="c13b5-107">By the end of this section, your chess pieces will be moving by user input.</span></span>

## <a name="objectives"></a><span data-ttu-id="c13b5-108">目标</span><span class="sxs-lookup"><span data-stu-id="c13b5-108">Objectives</span></span>

* <span data-ttu-id="c13b5-109">安装混合现实 UX Tools 插件</span><span class="sxs-lookup"><span data-stu-id="c13b5-109">Installing the Mixed Reality UX Tools plugin</span></span>
* <span data-ttu-id="c13b5-110">将手势交互 Actor 添加到指尖</span><span class="sxs-lookup"><span data-stu-id="c13b5-110">Adding Hand Interaction Actors to your fingertips</span></span>
* <span data-ttu-id="c13b5-111">创建操控器并将其添加到场景中的对象</span><span class="sxs-lookup"><span data-stu-id="c13b5-111">Creating and adding Manipulators to objects in the scene</span></span>
* <span data-ttu-id="c13b5-112">使用输入模拟来验证项目</span><span class="sxs-lookup"><span data-stu-id="c13b5-112">Using input simulation to validate the project</span></span>

## <a name="downloading-the-mixed-reality-ux-tools-plugin"></a><span data-ttu-id="c13b5-113">下载混合现实 UX Tools 插件</span><span class="sxs-lookup"><span data-stu-id="c13b5-113">Downloading the Mixed Reality UX Tools plugin</span></span>
<span data-ttu-id="c13b5-114">在开始使用用户输入之前，需要将混合现实 UX Tools 插件添加到项目。</span><span class="sxs-lookup"><span data-stu-id="c13b5-114">Before you start working with user input, you'll need to add the Mixed Reality UX Tools plugin to the project.</span></span> <span data-ttu-id="c13b5-115">若要了解有关 UX Tools 的详细信息，可以在 [GitHub](https://aka.ms/uxt-unreal) 上查看该项目。</span><span class="sxs-lookup"><span data-stu-id="c13b5-115">To learn more about UX Tools, you can check out the project on [GitHub](https://aka.ms/uxt-unreal).</span></span>

1. <span data-ttu-id="c13b5-116">打开 Epic Games Launcher。</span><span class="sxs-lookup"><span data-stu-id="c13b5-116">Open the Epic Games Launcher.</span></span> <span data-ttu-id="c13b5-117">导航到 Unreal Engine Marketplace 并搜索“[Mixed Reality UX Tools](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools)”。</span><span class="sxs-lookup"><span data-stu-id="c13b5-117">Navigate to Unreal Engine Marketplace and search for "[Mixed Reality UX Tools](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools)".</span></span> <span data-ttu-id="c13b5-118">将插件安装到引擎。</span><span class="sxs-lookup"><span data-stu-id="c13b5-118">Install the plugin to your engine.</span></span>

![Unreal Marketplace](images/unreal-uxt/2-uxt-plugin.PNG)

2. <span data-ttu-id="c13b5-120">返回到 Unreal 编辑器，前往“项目设置” > “插件”，然后搜索“混合现实 UX Tools”。</span><span class="sxs-lookup"><span data-stu-id="c13b5-120">Back in the Unreal editor, go to **Project Settings** > **Plugins** and search for "Mixed Reality UX Tools".</span></span> <span data-ttu-id="c13b5-121">请确保已启用该插件，并在出现提示时重新启动编辑器。</span><span class="sxs-lookup"><span data-stu-id="c13b5-121">Ensure the plugin is enabled and restart the editor if prompted.</span></span>

![启用混合现实 UX Tools 插件](images/unreal-uxt/2-enable-uxt.PNG)

3.  <span data-ttu-id="c13b5-123">UXTools 插件具有一个“内容”文件夹（带有组件子文件夹，包括“按钮”、“XR 模拟”和“指针”），以及一个包含额外代码的“C++ 类”文件夹  。</span><span class="sxs-lookup"><span data-stu-id="c13b5-123">The UXTools plugin has a Content folder with subfolders for components, including **Buttons**, **XR Simulation**, and **Pointers**, and a C++ Classes folder with additional code.</span></span>  

> [!NOTE]
> <span data-ttu-id="c13b5-124">如果在“内容浏览器”中看不到“UXTools 内容”部分，请单击“视图选项”>“显示引擎内容”  。</span><span class="sxs-lookup"><span data-stu-id="c13b5-124">If you don’t see the **UXTools Content** section in the **Content Browser**, click **View Options > Show Engine Content**.</span></span>

![显示引擎内容](images/unreal-uxt/4-showenginecontent.PNG)

<span data-ttu-id="c13b5-126">可以在混合现实 UX Tools GitHub [存储库](https://aka.ms/uxt-unreal)中找到其他插件文档。</span><span class="sxs-lookup"><span data-stu-id="c13b5-126">Additional plugin documentation can be found on the Mixed Reality UX Tools GitHub [repository](https://aka.ms/uxt-unreal).</span></span>

<span data-ttu-id="c13b5-127">安装插件后，便可以开始使用它所提供的工具，从手势交互 Actor 开始。</span><span class="sxs-lookup"><span data-stu-id="c13b5-127">With the plugin installed, you're ready to start using the tools it has to offer, starting with hand interaction actors.</span></span>

## <a name="spawning-hand-interaction-actors"></a><span data-ttu-id="c13b5-128">生成手势交互 Actor</span><span class="sxs-lookup"><span data-stu-id="c13b5-128">Spawning Hand Interaction Actors</span></span>

<span data-ttu-id="c13b5-129">与 UX 元素的手势交互是使用手势交互 Actor 完成的，这些手势交互 Actor 为近距和远距交互创建并驱动指针和视觉对象。</span><span class="sxs-lookup"><span data-stu-id="c13b5-129">Hand interaction with UX elements is done with Hand Interaction Actors, which create and drive the pointers and visuals for near and far interactions.</span></span>
- <span data-ttu-id="c13b5-130">近距交互 - 缩放食指和拇指之间的元素或使用指尖戳元素。</span><span class="sxs-lookup"><span data-stu-id="c13b5-130">*Near interactions* - pinching elements between index finger and thumb or by poking them with a fingertip.</span></span>
- <span data-ttu-id="c13b5-131">远距交互 - 将虚拟手的光线指向元素并同时按住食指和拇指。</span><span class="sxs-lookup"><span data-stu-id="c13b5-131">*Far interactions* - pointing a ray from the virtual hand at an element and pressing index and thumb together.</span></span>

<span data-ttu-id="c13b5-132">在我们的示例中，将手势交互 Actor 添加到 MRPawn 可达到以下目的：</span><span class="sxs-lookup"><span data-stu-id="c13b5-132">In our case, adding a Hand Interaction Actor to **MRPawn** will:</span></span>
- <span data-ttu-id="c13b5-133">将光标添加到 Pawn 的食指指尖。</span><span class="sxs-lookup"><span data-stu-id="c13b5-133">Add a cursor to the tips of the Pawn’s index fingers.</span></span>
- <span data-ttu-id="c13b5-134">提供可通过 Pawn 操纵的精确手势输入事件。</span><span class="sxs-lookup"><span data-stu-id="c13b5-134">Provide articulated hand input events that can be manipulated through the Pawn.</span></span>
- <span data-ttu-id="c13b5-135">通过从虚拟手的手掌延伸出的手部光线允许远距交互输入事件。</span><span class="sxs-lookup"><span data-stu-id="c13b5-135">Allow far interaction input events through hand rays extending from the palms of the virtual hands.</span></span>

<span data-ttu-id="c13b5-136">建议在继续之前通读介绍手动交互的[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html)。</span><span class="sxs-lookup"><span data-stu-id="c13b5-136">We recommend reading through the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) on hand interactions before continuing.</span></span>

<span data-ttu-id="c13b5-137">准备就绪后，打开“MRPawn”蓝图，然后转到“事件图”。</span><span class="sxs-lookup"><span data-stu-id="c13b5-137">Once you're ready, open the **MRPawn** Blueprint and go to the **Event Graph**.</span></span>

1. <span data-ttu-id="c13b5-138">将执行引脚从事件 BeginPlay 拖离然后释放，以放置一个新节点。</span><span class="sxs-lookup"><span data-stu-id="c13b5-138">Drag and release the execution pin from **Event BeginPlay** to place a new node.</span></span>
    * <span data-ttu-id="c13b5-139">选择“从类中生成 Actor”，单击“类”引脚旁边的下拉列表，并搜索“UXT 手势交互 Actor”  。</span><span class="sxs-lookup"><span data-stu-id="c13b5-139">Select **Spawn Actor from Class**, click the dropdown next to the **Class** pin and search for **Uxt Hand Interaction Actor**.</span></span>  

2. <span data-ttu-id="c13b5-140">生成第二个“UXT 手势交互 Actor”，这次会将手势设置为“向右”  。</span><span class="sxs-lookup"><span data-stu-id="c13b5-140">Spawn a second **Uxt Hand Interaction Actor**, this time setting the **Hand** to **Right**.</span></span> <span data-ttu-id="c13b5-141">事件开始时，将会在每只手上生成 UXT 手势交互 Actor。</span><span class="sxs-lookup"><span data-stu-id="c13b5-141">When the event begins, a Uxt Hand Interaction Actor will be spawned on each hand.</span></span>

<span data-ttu-id="c13b5-142">事件图应与以下屏幕截图匹配：</span><span class="sxs-lookup"><span data-stu-id="c13b5-142">Your **Event Graph** should match the following screenshot:</span></span>

![生成 UXT 手势交互 Actor](images/unreal-uxt/4-spawnactor.PNG)

<span data-ttu-id="c13b5-144">两个 UXT 手势交互 Actor 均需要所有者和初始变形位置。</span><span class="sxs-lookup"><span data-stu-id="c13b5-144">Both Uxt Hand Interaction Actors need owners and initial transform locations.</span></span> <span data-ttu-id="c13b5-145">在这种情况下，初始变形并不重要，因为 UX Tools 插件中包含手势交互 Actor，后者可见后便立即跳转到虚拟手。</span><span class="sxs-lookup"><span data-stu-id="c13b5-145">The initial transform doesn’t matter in this case because UX Tools will have the Hand Interaction Actors jump to the virtual hands as soon as they're visible.</span></span> <span data-ttu-id="c13b5-146">但是，`SpawnActor` 函数需要使用变形输入来避免编译器错误，因此你将使用默认值。</span><span class="sxs-lookup"><span data-stu-id="c13b5-146">However, the `SpawnActor` function requires a Transform input to avoid a compiler error, so you'll use the default values.</span></span>

1. <span data-ttu-id="c13b5-147">将该引脚拖离一个“生成变形”引脚，然后释放，即可放置一个新节点。</span><span class="sxs-lookup"><span data-stu-id="c13b5-147">Drag and release the pin off one of the **Spawn Transform** pins to place a new node.</span></span>
    * <span data-ttu-id="c13b5-148">搜索“进行变形”节点，然后将“返回值”拖到另一个手势的“生成变形”，以便连接两个 SpawnActor 节点   。</span><span class="sxs-lookup"><span data-stu-id="c13b5-148">Search for the **Make Transform** node, then drag the **Return Value** to the other hand’s **Spawn Transform** so that both **SpawnActor** nodes are connected.</span></span>

2.  <span data-ttu-id="c13b5-149">选择两个 SpawnActor 节点底部的“向下箭头”，以显示“所有者”引脚  。</span><span class="sxs-lookup"><span data-stu-id="c13b5-149">Select the **down arrow** at the bottom of both **SpawnActor** nodes to reveal the **Owner** pin.</span></span>    
    * <span data-ttu-id="c13b5-150">将该引脚拖离一个“所有者”引脚，然后放开，即可放置一个新节点。</span><span class="sxs-lookup"><span data-stu-id="c13b5-150">Drag the pin off one of the **Owner** pins and release to place a new node.</span></span>
    * <span data-ttu-id="c13b5-151">搜索“self”并选择“Get a reference to self”变量 。</span><span class="sxs-lookup"><span data-stu-id="c13b5-151">Search for **self** and select the **Get a reference to self** variable.</span></span>
    * <span data-ttu-id="c13b5-152">在 Self 对象引用节点和另一个手势交互 Actor 的“所有者”引脚之间创建链接 。</span><span class="sxs-lookup"><span data-stu-id="c13b5-152">Create a link between the **Self** object reference node and the other Hand Interaction Actor’s **Owner** pin.</span></span>
3. <span data-ttu-id="c13b5-153">最后，同时选中两个手势交互 Actor 的“在抓取目标上显示近光标”框。</span><span class="sxs-lookup"><span data-stu-id="c13b5-153">Lastly, check the **Show Near Cursor on Grab Targets** box for both Hand Interaction Actors.</span></span> <span data-ttu-id="c13b5-154">当食指靠近时，光标应出现在抓取目标上，这样就可以看到手指相对于目标的位置。</span><span class="sxs-lookup"><span data-stu-id="c13b5-154">A cursor should appear on the grab target as your index finger gets close, so you can see where your finger is relative to the target.</span></span>
    * <span data-ttu-id="c13b5-155">编译并保存后返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="c13b5-155">**Compile**, **save**, and return to the Main window.</span></span>

<span data-ttu-id="c13b5-156">确保连接与以下屏幕截图匹配，但可随意拖动节点以使蓝图更具可读性。</span><span class="sxs-lookup"><span data-stu-id="c13b5-156">Make sure the connections match the following screenshot, but feel free to drag around nodes to make your Blueprint more readable.</span></span>

![完成 UXT 手势交互 Actor 设置](images/unreal-uxt/4-fingerptrs.PNG)

<span data-ttu-id="c13b5-158">可以在 [UX Tools 文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html)中找到有关手动交互 Actor 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="c13b5-158">You can find more information about Hand Interaction Actors in the [UX Tools documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html).</span></span>

<span data-ttu-id="c13b5-159">现在，项目中的虚拟手可以选择对象，但仍无法对其进行操纵。</span><span class="sxs-lookup"><span data-stu-id="c13b5-159">Now the virtual hands in the project have a way of selecting objects, but they still can't manipulate them.</span></span> <span data-ttu-id="c13b5-160">测试应用之前的最后一个任务是将操控器组件添加到场景中的 Actor。</span><span class="sxs-lookup"><span data-stu-id="c13b5-160">Your last task before testing the app is to add Manipulator components to the actors in the scene.</span></span>

## <a name="attaching-manipulators"></a><span data-ttu-id="c13b5-161">附加操控器</span><span class="sxs-lookup"><span data-stu-id="c13b5-161">Attaching Manipulators</span></span>

<span data-ttu-id="c13b5-162">操控器是一个响应精确手动输入的组件，可进行抓取、旋转和平移。</span><span class="sxs-lookup"><span data-stu-id="c13b5-162">A Manipulator is a component that responds to articulated hand input and can be grabbed, rotated, and translated.</span></span> <span data-ttu-id="c13b5-163">将操控器的变形应用到 Actor 变形可允许进行直接 Actor 操纵。</span><span class="sxs-lookup"><span data-stu-id="c13b5-163">Applying the Manipulator’s transform to an Actors transform allows direct Actor manipulation.</span></span>

1. <span data-ttu-id="c13b5-164">在“组件”面板中，打开“棋盘”蓝图，单击“添加组件”并搜索“UXT 通用操控器”   。</span><span class="sxs-lookup"><span data-stu-id="c13b5-164">Open the **Board** blueprint, click **Add Component** and search for **Uxt Generic Manipulator** in the **Components** panel.</span></span>

![添加通用操控器](images/unreal-uxt/4-addmanip.PNG)

2. <span data-ttu-id="c13b5-166">展开“详细信息”面板中的“通用操控器”部分 。</span><span class="sxs-lookup"><span data-stu-id="c13b5-166">Expand the **Generic Manipulator** section in the **Details** panel.</span></span> <span data-ttu-id="c13b5-167">可以在其中设置单手操纵或双手操纵、旋转模式和平滑模式。</span><span class="sxs-lookup"><span data-stu-id="c13b5-167">You can set one-handed or two-handed manipulation, rotation mode, and smoothing from here.</span></span> <span data-ttu-id="c13b5-168">可以随意选择所需的模式，然后编译和保存棋盘。</span><span class="sxs-lookup"><span data-stu-id="c13b5-168">Feel free to select whichever modes you wish, then **Compile** and **Save** Board.</span></span>

![设置模式](images/unreal-uxt/4-setrotmode.PNG)

3. <span data-ttu-id="c13b5-170">对 WhiteKing Actor 重复以上步骤。</span><span class="sxs-lookup"><span data-stu-id="c13b5-170">Repeat the steps above for the **WhiteKing** Actor.</span></span>

<span data-ttu-id="c13b5-171">可以在[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html)中找到有关混合现实 UX Tools 插件中提供的操控器组件的详细信息。</span><span class="sxs-lookup"><span data-stu-id="c13b5-171">You can find more information about the Manipulator Components provided in the Mixed Reality UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html).</span></span>

## <a name="testing-the-scene"></a><span data-ttu-id="c13b5-172">测试场景</span><span class="sxs-lookup"><span data-stu-id="c13b5-172">Testing the scene</span></span>

<span data-ttu-id="c13b5-173">好消息！</span><span class="sxs-lookup"><span data-stu-id="c13b5-173">Good news everyone!</span></span> <span data-ttu-id="c13b5-174">你已准备好使用其新的虚拟手和用户输入来测试应用。</span><span class="sxs-lookup"><span data-stu-id="c13b5-174">You're ready to test out the app with its new virtual hands and user input.</span></span> <span data-ttu-id="c13b5-175">在主窗口中按“播放”，应该会看到两个网格手，且从每个手掌延伸出手部光线。</span><span class="sxs-lookup"><span data-stu-id="c13b5-175">Press **Play** in the Main Window and you'll see two mesh hands with rays extending from each hand’s palm.</span></span> <span data-ttu-id="c13b5-176">可以按如下所示控制手势及其交互：</span><span class="sxs-lookup"><span data-stu-id="c13b5-176">You can control the hands and their interactions as follows:</span></span>
- <span data-ttu-id="c13b5-177">按住“左 Alt”键以控制左手，按住“左 Shift”键以控制右手   。</span><span class="sxs-lookup"><span data-stu-id="c13b5-177">Hold down the **left Alt** key to control the **left hand** and the **left Shift** key to control the **right hand**.</span></span>
- <span data-ttu-id="c13b5-178">移动鼠标来移动手，并滚动鼠标滚轮，向前或向后移动手  。</span><span class="sxs-lookup"><span data-stu-id="c13b5-178">Move your mouse to move the hand and scroll with your **mouse wheel** to move the hand **forwards** or **backwards**.</span></span>
- <span data-ttu-id="c13b5-179">使用鼠标左键进行缩放，使用鼠标中键执行戳操作。</span><span class="sxs-lookup"><span data-stu-id="c13b5-179">Use the left mouse button to **pinch** and the middle mouse button to **poke**.</span></span>

> [!NOTE]
> <span data-ttu-id="c13b5-180">如果你有多个头戴显示设备插入电脑，则输入模拟可能无法正常工作。</span><span class="sxs-lookup"><span data-stu-id="c13b5-180">Input simulation may not work if you have multiple headsets plugged into your PC.</span></span> <span data-ttu-id="c13b5-181">如果遇到问题，请尝试拔下其他头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="c13b5-181">If you're having issues, try unplugging your other headsets.</span></span>

![视口中的模拟手](images/unreal-uxt/4-handsim.PNG)

<span data-ttu-id="c13b5-183">请尝试使用模拟手来拿起、移动和放下白棋国王并操纵棋盘！</span><span class="sxs-lookup"><span data-stu-id="c13b5-183">Try using the simulated hands to pick up, move, and set down the white chess king and manipulate the board!</span></span> <span data-ttu-id="c13b5-184">试验近距交互和远距交互 - 请注意，当手足够靠近可直接抓住棋盘和国王时，食指指尖上的手指光标会取代手部光线。</span><span class="sxs-lookup"><span data-stu-id="c13b5-184">Experiment with both near and far interaction - notice that when your hands get close enough to grab the board and king directly, a finger cursor at the tip of the index finger replaces the hand ray.</span></span>

<span data-ttu-id="c13b5-185">可以在[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/InputSimulation.html)中找到有关 MRTK UX Tools 插件中提供的模拟手功能的详细信息。</span><span class="sxs-lookup"><span data-stu-id="c13b5-185">You can find more information about the simulated hands feature provided by the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/InputSimulation.html).</span></span>

<span data-ttu-id="c13b5-186">现在，你的虚拟手可以与对象交互，接下来可以继续学习下一个教程，并添加用户界面和事件。</span><span class="sxs-lookup"><span data-stu-id="c13b5-186">Now that your virtual hands can interact with objects, you're ready to move on to the next tutorial and add user interfaces and events.</span></span>

[<span data-ttu-id="c13b5-187">下一节：5.添加按钮并重置棋子位置</span><span class="sxs-lookup"><span data-stu-id="c13b5-187">Next Section: 5. Adding a button & resetting piece locations</span></span>](unreal-uxt-ch5.md)
