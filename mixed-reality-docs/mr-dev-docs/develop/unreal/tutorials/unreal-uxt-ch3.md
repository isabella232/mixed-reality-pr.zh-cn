---
title: 3. 设置混合现实项目
description: 教程系列第 3 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款象棋应用
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: 26bb874578e56b21d319741b8b1c1ff6decebe4b
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "96609698"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="0ed07-104">3.设置混合现实项目</span><span class="sxs-lookup"><span data-stu-id="0ed07-104">3. Setting up your project for mixed reality</span></span>

<span data-ttu-id="0ed07-105">在上一个教程中设置了象棋应用项目。</span><span class="sxs-lookup"><span data-stu-id="0ed07-105">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="0ed07-106">本部分将逐步介绍如何设置此应用，来进行混合现实开发，这意味着要添加 AR 会话。</span><span class="sxs-lookup"><span data-stu-id="0ed07-106">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="0ed07-107">此任务将使用 ARSessionConfig 数据资产，其中包含有用的 AR 设置，如空间映射和遮挡。</span><span class="sxs-lookup"><span data-stu-id="0ed07-107">You'll be using an ARSessionConfig data asset for this task, which has useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="0ed07-108">可以在 Unreal 的文档中找到有关 [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) 资产和 [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) 类的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="0ed07-108">You can find more details about the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class in Unreal's documentation.</span></span>

## <a name="objectives"></a><span data-ttu-id="0ed07-109">目标</span><span class="sxs-lookup"><span data-stu-id="0ed07-109">Objectives</span></span>

* <span data-ttu-id="0ed07-110">使用 Unreal Engine 的 AR 设置</span><span class="sxs-lookup"><span data-stu-id="0ed07-110">Working with Unreal Engine's AR settings</span></span>
* <span data-ttu-id="0ed07-111">使用 ARSessionConfig 数据资产</span><span class="sxs-lookup"><span data-stu-id="0ed07-111">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="0ed07-112">设置 Pawn 和游戏模式</span><span class="sxs-lookup"><span data-stu-id="0ed07-112">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="0ed07-113">添加会话资产</span><span class="sxs-lookup"><span data-stu-id="0ed07-113">Adding the session asset</span></span>

<span data-ttu-id="0ed07-114">Unreal 中的 AR 会话无法自行发生。</span><span class="sxs-lookup"><span data-stu-id="0ed07-114">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="0ed07-115">要使用会话，需要借助 ARSessionConfig 数据资产，这就是接下来的任务：</span><span class="sxs-lookup"><span data-stu-id="0ed07-115">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="0ed07-116">单击“内容浏览器”中的“添加新项 > 杂项 > 数据资产”。 </span><span class="sxs-lookup"><span data-stu-id="0ed07-116">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="0ed07-117">请确保自己处于根 Content 文件夹级别。</span><span class="sxs-lookup"><span data-stu-id="0ed07-117">Make sure you're at the root **Content** folder level.</span></span>
    * <span data-ttu-id="0ed07-118">选择“ARSessionConfig”，单击“选择”，然后将资产命名为“ARSessionConfig”。  </span><span class="sxs-lookup"><span data-stu-id="0ed07-118">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![创建数据资产](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="0ed07-120">双击“ARSessionConfig”将其打开，保留所有默认设置，点击“保存”。 </span><span class="sxs-lookup"><span data-stu-id="0ed07-120">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="0ed07-121">返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="0ed07-121">Return to the Main window.</span></span>

![AR 会话配置](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="0ed07-123">完成此操作后，下一步是确保在关卡加载时 AR 会话会启动，而在关卡结束时 AR 会话会停止。</span><span class="sxs-lookup"><span data-stu-id="0ed07-123">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="0ed07-124">幸运的是，Unreal 具有叫做“关卡蓝图”的特殊蓝图，它用作关卡范围的全局事件图。</span><span class="sxs-lookup"><span data-stu-id="0ed07-124">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="0ed07-125">在关卡蓝图中连接 ARSessionConfig 资产，可确保游戏开始时 AR 会话将立即触发。</span><span class="sxs-lookup"><span data-stu-id="0ed07-125">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="0ed07-126">从编辑器工具栏中单击“蓝图 > 打开关卡蓝图”：</span><span class="sxs-lookup"><span data-stu-id="0ed07-126">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span>

![打开关卡蓝图](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="0ed07-128">将执行节点（向左箭头图标）拖离“事件 BeginPlay”，随后放开，然后搜索“启动 AR 会话”节点并按 Enter 。</span><span class="sxs-lookup"><span data-stu-id="0ed07-128">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release, then search for the **Start AR Session** node and hit enter.</span></span>  
    * <span data-ttu-id="0ed07-129">单击“会话配置”下的“选择资产”下拉列表，然后选择“ARSessionConfig”资产。  </span><span class="sxs-lookup"><span data-stu-id="0ed07-129">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span>

![启动 AR 会话](images/unreal-uxt/3-start-ar-session.PNG)

6. <span data-ttu-id="0ed07-131">右键单击 EventGraph 中的任意位置，然后创建一个新的 Event EndPlay 节点。</span><span class="sxs-lookup"><span data-stu-id="0ed07-131">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> <span data-ttu-id="0ed07-132">拖动执行脚本，随后放开，然后搜索“停止 AR 会话”节点并按 Enter。</span><span class="sxs-lookup"><span data-stu-id="0ed07-132">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter.</span></span> <span data-ttu-id="0ed07-133">如果在关卡结束时 AR 会话仍在运行，那么在流式传输到头戴显示设备时，如果你重启应用，某些功能可能会停止工作。</span><span class="sxs-lookup"><span data-stu-id="0ed07-133">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>
    * <span data-ttu-id="0ed07-134">点击“编译”和保存”，然后返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="0ed07-134">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![停止 AR 会话](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="0ed07-136">创建 Pawn</span><span class="sxs-lookup"><span data-stu-id="0ed07-136">Create a Pawn</span></span>

<span data-ttu-id="0ed07-137">此时，项目仍需要一个玩家对象。</span><span class="sxs-lookup"><span data-stu-id="0ed07-137">At this point, the project still needs a player object.</span></span> <span data-ttu-id="0ed07-138">在 Unreal 中，Pawn 表示游戏中的用户，但在本例中它将代表 HoloLens 2 体验。</span><span class="sxs-lookup"><span data-stu-id="0ed07-138">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="0ed07-139">在 Content 文件夹中单击“添加新项 > 蓝图类”，展开底部的“所有类”部分。  </span><span class="sxs-lookup"><span data-stu-id="0ed07-139">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span>
    * <span data-ttu-id="0ed07-140">搜索“DefaultPawn”，单击“选择”，将其命名为“MRPawn”，然后双击资产打开它  。</span><span class="sxs-lookup"><span data-stu-id="0ed07-140">Search for **DefaultPawn**, click **Select**, name it **MRPawn**, and double-click the asset to open.</span></span>

![创建从 DefaultPawn 继承的新 Pawn](images/unreal-uxt/3-defaultpawn.PNG)

2. <span data-ttu-id="0ed07-142">从“组件”面板中单击“添加组件”>“相机”，然后将其命名为“相机”  。</span><span class="sxs-lookup"><span data-stu-id="0ed07-142">Click **Add Component > Camera** from the **Components** panel and name it **Camera**.</span></span> <span data-ttu-id="0ed07-143">确保“相机”组件是根 (CollisionComponent) 的直接子级 。</span><span class="sxs-lookup"><span data-stu-id="0ed07-143">Make sure that the **Camera** component is a direct child of the root (**CollisionComponent**).</span></span> <span data-ttu-id="0ed07-144">这样，玩家相机就能随 HoloLens 2 设备一起移动。</span><span class="sxs-lookup"><span data-stu-id="0ed07-144">This allows the player camera to move with the HoloLens 2 device.</span></span>

> [!NOTE]
> <span data-ttu-id="0ed07-145">默认情况下，Pawn 具有网格和碰撞组件。</span><span class="sxs-lookup"><span data-stu-id="0ed07-145">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="0ed07-146">在大多数 Unreal 项目中，Pawn 都是可与其他组件碰撞的固体。</span><span class="sxs-lookup"><span data-stu-id="0ed07-146">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="0ed07-147">在混合现实中 Pawn 与用户相同，因此需要能够在不发生碰撞的情况下传递全息影像。</span><span class="sxs-lookup"><span data-stu-id="0ed07-147">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span>

3. <span data-ttu-id="0ed07-148">从“组件”面板中选择“CollisionComponent”，向下滚动到“详细信息”面板的“碰撞”部分。   </span><span class="sxs-lookup"><span data-stu-id="0ed07-148">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span>
    * <span data-ttu-id="0ed07-149">单击“碰撞预设”下拉列表，将值更改为“NoCollision”。 </span><span class="sxs-lookup"><span data-stu-id="0ed07-149">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span>
    * <span data-ttu-id="0ed07-150">对“MeshComponent”执行同样的操作</span><span class="sxs-lookup"><span data-stu-id="0ed07-150">Do the same for the **MeshComponent**</span></span>

![调整 Pawn 的碰撞预设](images/unreal-uxt/3-nocollision.PNG)

4. <span data-ttu-id="0ed07-152">编译并保存蓝图 。</span><span class="sxs-lookup"><span data-stu-id="0ed07-152">**Compile** and **Save** the Blueprint.</span></span>

<span data-ttu-id="0ed07-153">从此处完成操作后，返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="0ed07-153">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="0ed07-154">创建游戏模式</span><span class="sxs-lookup"><span data-stu-id="0ed07-154">Create a Game Mode</span></span>

<span data-ttu-id="0ed07-155">混合现实设置的最后一个部分是游戏模式。</span><span class="sxs-lookup"><span data-stu-id="0ed07-155">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="0ed07-156">游戏模式决定着游戏或体验的诸多设置，其中包括要使用的默认 Pawn。</span><span class="sxs-lookup"><span data-stu-id="0ed07-156">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="0ed07-157">在“内容”文件夹中单击“添加新项”>“蓝图类”，然后选择“游戏模式基类”作为父类  。</span><span class="sxs-lookup"><span data-stu-id="0ed07-157">Click **Add New > Blueprint Class** in the **Content** folder and select **Game Mode Base** as the parent class.</span></span> <span data-ttu-id="0ed07-158">将其命名为“MRGameMode”并双击以打开。</span><span class="sxs-lookup"><span data-stu-id="0ed07-158">Name it **MRGameMode** and double-click to open.</span></span>

![内容浏览器中的 MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="0ed07-160">转到“详细信息”面板中的“类”部分，将“默认 Pawn 类”更改为“MRPawn”。   。</span><span class="sxs-lookup"><span data-stu-id="0ed07-160">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span>
    * <span data-ttu-id="0ed07-161">点击“编译”和保存”，然后返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="0ed07-161">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![设置默认 Pawn 类](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="0ed07-163">选择“编辑 > 项目设置”，然后从左侧列表单击“地图和模式”。 </span><span class="sxs-lookup"><span data-stu-id="0ed07-163">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span>
    * <span data-ttu-id="0ed07-164">展开“默认模式”，将“默认游戏模式”更改为“MRGameMode”。  </span><span class="sxs-lookup"><span data-stu-id="0ed07-164">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span>
    * <span data-ttu-id="0ed07-165">展开“默认地图”，将“EditorStartupMap”和“GameDefaultMap”都设置为“主”。   </span><span class="sxs-lookup"><span data-stu-id="0ed07-165">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="0ed07-166">当你关闭并重新打开编辑器或玩游戏时，现在将默认选择主地图。</span><span class="sxs-lookup"><span data-stu-id="0ed07-166">When you close and reopen the editor or play the game, the Main map will now be selected by default.</span></span>

![项目设置 - 映射和模式](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="0ed07-168">针对混合现实全面设置此项目后，你可以继续学习下一个教程，开始将用户输入添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="0ed07-168">With the project fully set up for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span>

[<span data-ttu-id="0ed07-169">下一节：4.使场景具有交互性</span><span class="sxs-lookup"><span data-stu-id="0ed07-169">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)
