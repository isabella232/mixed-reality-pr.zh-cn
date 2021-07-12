---
title: 2. 初始化你的项目和第一个应用程序
description: 教程系列第 2 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款象棋应用
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: f7cf43e8f1c040660b6a2688e234a271bc071b00
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712638"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="684bb-104">2.初始化你的项目和第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="684bb-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="684bb-105">在第一个教程中，你将开始从一个新 Unreal 项目着手，需启用 HoloLens 插件、创建和点亮关卡，以及添加棋子。</span><span class="sxs-lookup"><span data-stu-id="684bb-105">In the first tutorial, you'll start out with a new Unreal project and enable the HoloLens plugin, create and light a level, and add chess pieces.</span></span> <span data-ttu-id="684bb-106">你可将我们预制的资产用于所有 3D 对象和材质，因此不必担心需自行建模的问题。</span><span class="sxs-lookup"><span data-stu-id="684bb-106">You'll be using our pre-made assets for all 3D objects and materials, so don't worry about modeling anything yourself.</span></span> <span data-ttu-id="684bb-107">本教程结束时，你会有一个可用于混合现实的空白画布。</span><span class="sxs-lookup"><span data-stu-id="684bb-107">By the end of this tutorial, you'll have a blank canvas that's ready for mixed reality.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="684bb-108">请确保满足[入门](/windows/mixed-reality/unreal-uxt-ch1)页面中的所有先决条件。</span><span class="sxs-lookup"><span data-stu-id="684bb-108">Make sure you have all the prerequisites from the [Getting Started](/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="684bb-109">目标</span><span class="sxs-lookup"><span data-stu-id="684bb-109">Objectives</span></span>

* <span data-ttu-id="684bb-110">为 HoloLens 开发配置 Unreal 项目</span><span class="sxs-lookup"><span data-stu-id="684bb-110">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="684bb-111">导入资产和设置场景</span><span class="sxs-lookup"><span data-stu-id="684bb-111">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="684bb-112">使用蓝图创建 Actor 和脚本级别事件</span><span class="sxs-lookup"><span data-stu-id="684bb-112">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="684bb-113">创建新的 Unreal 项目</span><span class="sxs-lookup"><span data-stu-id="684bb-113">Creating a new Unreal project</span></span>

<span data-ttu-id="684bb-114">首先需要一个待处理的项目。</span><span class="sxs-lookup"><span data-stu-id="684bb-114">The first thing you need is a project to work with.</span></span> <span data-ttu-id="684bb-115">如果你是刚接触的 Unreal 开发人员，则需要从 Epic Launcher [下载支持文件](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="684bb-115">If you're a first-time Unreal developer, you'll need to [download supporting files](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="684bb-116">启动 Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="684bb-116">Launch Unreal Engine</span></span>

2. <span data-ttu-id="684bb-117">在“新项目类别”中选择“游戏”，然后单击“下一步”  。</span><span class="sxs-lookup"><span data-stu-id="684bb-117">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![选择游戏项目模板](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="684bb-119">选择“空白”模板，然后单击“下一步” 。</span><span class="sxs-lookup"><span data-stu-id="684bb-119">Select the **Blank** Template and click **Next**.</span></span> 

![选择“空白”模板](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="684bb-121">在项目设置中选择“C++”、“可缩放的 3D 或 2D”、“移动/平板电脑”和“非初学者内容”，然后选择保存位置并单击“创建项目”    。</span><span class="sxs-lookup"><span data-stu-id="684bb-121">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**, then choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="684bb-122">为了生成 UX Tools 插件，必须选择 C++ 项目而不是 Blueprint 项目，你稍后将在第 4 节中对此进行设置。</span><span class="sxs-lookup"><span data-stu-id="684bb-122">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![初始项目设置](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="684bb-124">项目应在 Unreal 编辑器中自动打开，这意味着你已准备好进入下一部分。</span><span class="sxs-lookup"><span data-stu-id="684bb-124">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="684bb-125">启用所需插件</span><span class="sxs-lookup"><span data-stu-id="684bb-125">Enabling required plugins</span></span>

<span data-ttu-id="684bb-126">为了使用通过 Microsoft 混合现实平台提供的功能，你首先需要安装并启用 Microsoft OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="684bb-126">In order to use the features available via Microsoft's mixed reality platform, you'll first need to install and enable the Microsoft OpenXR plugin.</span></span> <span data-ttu-id="684bb-127">若要了解有关插件的详细信息，可以在 [GitHub](https://github.com/microsoft/Microsoft-OpenXR-Unreal) 上查看该项目。</span><span class="sxs-lookup"><span data-stu-id="684bb-127">To learn more about the plugin, you can check out the project on [GitHub](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

1. <span data-ttu-id="684bb-128">打开 Epic Games Launcher。</span><span class="sxs-lookup"><span data-stu-id="684bb-128">Open the Epic Games Launcher.</span></span> <span data-ttu-id="684bb-129">导航到 Unreal Engine Marketplace 并搜索“[Microsoft OpenXR](https://www.unrealengine.com/marketplace/product/ef8930ca860148c498b46887da196239)”。</span><span class="sxs-lookup"><span data-stu-id="684bb-129">Navigate to Unreal Engine Marketplace and search for "[Microsoft OpenXR](https://www.unrealengine.com/marketplace/product/ef8930ca860148c498b46887da196239)".</span></span> <span data-ttu-id="684bb-130">将插件安装到引擎。</span><span class="sxs-lookup"><span data-stu-id="684bb-130">Install the plugin to your engine.</span></span>

![Unreal Marketplace](images/unreal-uxt/2-openxr-plugin.PNG)

2. <span data-ttu-id="684bb-132">返回到 Unreal 编辑器，前往“项目设置” > “插件”，然后搜索“Microsoft OpenXR”。</span><span class="sxs-lookup"><span data-stu-id="684bb-132">Back in the Unreal editor, go to **Project Settings** > **Plugins** and search for "Microsoft OpenXR".</span></span> <span data-ttu-id="684bb-133">如果出现提示，请确保已启用该插件，并重新启动编辑器。</span><span class="sxs-lookup"><span data-stu-id="684bb-133">Ensure the plugin is enabled and restart the editor if prompted.</span></span>

![启用 Microsoft OpenXR 插件](images/unreal-uxt/2-enable-plugin.PNG)

<span data-ttu-id="684bb-135">启用 Microsoft OpenXR 插件将自动启用混合现实开发所需的所有其他插件。</span><span class="sxs-lookup"><span data-stu-id="684bb-135">Enabling the Microsoft OpenXR plugin will automatically enable all the other plugins required for mixed reality development.</span></span> <span data-ttu-id="684bb-136">请注意，必须禁用“Microsoft Windows Mixed Reality”插件才能使用 OpenXR。</span><span class="sxs-lookup"><span data-stu-id="684bb-136">Note that the "Microsoft Windows Mixed Reality" plugin must be disabled in order to use OpenXR.</span></span> 

## <a name="creating-a-level"></a><span data-ttu-id="684bb-137">创建关卡</span><span class="sxs-lookup"><span data-stu-id="684bb-137">Creating a level</span></span>
<span data-ttu-id="684bb-138">下一个任务是创建具有可供参考和缩放的起点和立方体的玩家设置。</span><span class="sxs-lookup"><span data-stu-id="684bb-138">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="684bb-139">选择“文件”>“新关卡”>“空关卡”。</span><span class="sxs-lookup"><span data-stu-id="684bb-139">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="684bb-140">视口中的默认场景现在应为空。</span><span class="sxs-lookup"><span data-stu-id="684bb-140">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="684bb-141">从“模式”选项卡中选择“基本”，并将“PlayerStart”拖到场景中  。</span><span class="sxs-lookup"><span data-stu-id="684bb-141">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="684bb-142">在“详细信息”选项卡中，将“位置”设置为“X = 0”、“Y = 0”和“Z = 0”，以便在应用启动时将用户设置到场景的中心    。</span><span class="sxs-lookup"><span data-stu-id="684bb-142">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab to set the user at the center of the scene when the app starts up.</span></span>

![具有 PlayerStart 的视口](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="684bb-144">将“立方体”从“基本”选项卡拖到场景中 。</span><span class="sxs-lookup"><span data-stu-id="684bb-144">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="684bb-145">将“位置”设置为“X = 50”、“Y = 0”和“Z = 0”   。</span><span class="sxs-lookup"><span data-stu-id="684bb-145">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="684bb-146">在启动时将立方体放在距离玩家 50 厘米的位置。</span><span class="sxs-lookup"><span data-stu-id="684bb-146">to position the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="684bb-147">将“比例”更改为“X = 0.2”、“Y = 0.2”和“Z = 0.2”以缩小立方体   。</span><span class="sxs-lookup"><span data-stu-id="684bb-147">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="684bb-148">除非向场景添加光源（这是测试场景前的最后一个任务），否则看不到立方体。</span><span class="sxs-lookup"><span data-stu-id="684bb-148">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="684bb-149">切换到“模式”面板上的“光源”选项卡，然后将“定向光源”拖到场景中  。</span><span class="sxs-lookup"><span data-stu-id="684bb-149">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="684bb-150">将光源置于“PlayerStart”上方，以便可以看到该光源。</span><span class="sxs-lookup"><span data-stu-id="684bb-150">Position the light above **PlayerStart** so you can see it.</span></span>

![添加了光源的视口](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="684bb-152">转到“文件”>“保存当前”，将关卡命名为“主”，然后选择“保存”  。</span><span class="sxs-lookup"><span data-stu-id="684bb-152">Go to **File > Save Current**, name your level **Main**, and select **Save**.</span></span> 

<span data-ttu-id="684bb-153">设置场景后，按工具栏中的“开始”，以查看正在运行的立方体！</span><span class="sxs-lookup"><span data-stu-id="684bb-153">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="684bb-154">完成工作后，按 Esc 停止应用程序。</span><span class="sxs-lookup"><span data-stu-id="684bb-154">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![视口中的立方体](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="684bb-156">设置场景后，便可以开始在棋盘和棋子中进行添加以构成应用程序环境。</span><span class="sxs-lookup"><span data-stu-id="684bb-156">Now that the scene is set up, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="684bb-157">导入资产</span><span class="sxs-lookup"><span data-stu-id="684bb-157">Importing assets</span></span>
<span data-ttu-id="684bb-158">场景目前看起来非常空，但通过将现成的资产导入到项目中，将解决此问题。</span><span class="sxs-lookup"><span data-stu-id="684bb-158">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="684bb-159">使用 [7-zip](https://www.7-zip.org/) 下载并解压缩 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) 资产文件夹。</span><span class="sxs-lookup"><span data-stu-id="684bb-159">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder using [7-zip](https://www.7-zip.org/).</span></span>

2. <span data-ttu-id="684bb-160">从“内容浏览器”中选择“新增”>“新建文件夹”，然后将其命名为“ChessAssets”  。</span><span class="sxs-lookup"><span data-stu-id="684bb-160">Select **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="684bb-161">双击新文件夹，这是导入 3D 资产的位置。</span><span class="sxs-lookup"><span data-stu-id="684bb-161">Double-click the new folder where you'll import the 3D assets.</span></span>

![显示或隐藏源面板](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="684bb-163">从“内容浏览器”中选择“导入”，选择解压缩的资产文件夹中的所有项目，然后单击“打开”  。</span><span class="sxs-lookup"><span data-stu-id="684bb-163">Select **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="684bb-164">资产包括棋盘和棋子的 3D 对象网格（采用 FBX 格式）和用于材质的纹理映射（采用 TGA 格式）。</span><span class="sxs-lookup"><span data-stu-id="684bb-164">Assets include the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="684bb-165">弹出“FBX 导入选项”窗口后，展开“材质”部分，并将“材质导入方法”更改为“不创建材质”  。</span><span class="sxs-lookup"><span data-stu-id="684bb-165">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="684bb-166">选择“全部导入”。</span><span class="sxs-lookup"><span data-stu-id="684bb-166">Select **Import All**.</span></span>

![导入 FBX 选项](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="684bb-168">资产只需执行这些操作。</span><span class="sxs-lookup"><span data-stu-id="684bb-168">That's all you need to do for the assets.</span></span> <span data-ttu-id="684bb-169">接下来的一组任务是使用蓝图创建应用程序的构建基块。</span><span class="sxs-lookup"><span data-stu-id="684bb-169">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="684bb-170">添加蓝图</span><span class="sxs-lookup"><span data-stu-id="684bb-170">Adding blueprints</span></span>

1. <span data-ttu-id="684bb-171">在“内容浏览器”中选择“新增”>“新建文件夹”，然后将其命名为“蓝图”  。</span><span class="sxs-lookup"><span data-stu-id="684bb-171">Select **Add New > New Folder** in the **Content Browser** and name it **Blueprints**.</span></span> 

> [!NOTE]
> <span data-ttu-id="684bb-172">如果你不熟悉[蓝图](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html)，这些蓝图为特殊资产，它们提供基于节点的接口来创建新类型的 Actor 和脚本级别事件。</span><span class="sxs-lookup"><span data-stu-id="684bb-172">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="684bb-173">双击“蓝图”文件夹，然后右键单击并选择“蓝图类”。</span><span class="sxs-lookup"><span data-stu-id="684bb-173">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="684bb-174">选择“Actor”并将蓝图命名为“棋盘”。</span><span class="sxs-lookup"><span data-stu-id="684bb-174">Select **Actor** and name the blueprint **Board**.</span></span> 

![选择蓝图的父类](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="684bb-176">新的棋盘蓝图现在显示在“蓝图”文件夹中，如以下屏幕截图中所示 。</span><span class="sxs-lookup"><span data-stu-id="684bb-176">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![新棋盘蓝图](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="684bb-178">你已经准备好开始向创建的对象添加材质。</span><span class="sxs-lookup"><span data-stu-id="684bb-178">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="684bb-179">使用材质</span><span class="sxs-lookup"><span data-stu-id="684bb-179">Working with materials</span></span>
<span data-ttu-id="684bb-180">你创建的对象默认为灰色，这看上去太过普通。</span><span class="sxs-lookup"><span data-stu-id="684bb-180">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="684bb-181">向对象添加材质和网格是本教程中的最后一组任务。</span><span class="sxs-lookup"><span data-stu-id="684bb-181">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="684bb-182">双击“棋盘”以打开蓝图编辑器。</span><span class="sxs-lookup"><span data-stu-id="684bb-182">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="684bb-183">从“组件”面板中选择“添加组件”>“场景”，并将其命名为“Root”  。</span><span class="sxs-lookup"><span data-stu-id="684bb-183">Select **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="684bb-184">请注意，“Root”在下面的屏幕截图中显示为 DefaultSceneRoot 的子项 ：</span><span class="sxs-lookup"><span data-stu-id="684bb-184">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![替换蓝图中的 root](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="684bb-186">单击“Root”并将其拖到 DefaultSceneRoot 中，以替换它并在视口中消除球面 。</span><span class="sxs-lookup"><span data-stu-id="684bb-186">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![替换 Root](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="684bb-188">从“组件”面板中选择“添加组件”>“静态网格”，并将其命名为“SM_Board”  。</span><span class="sxs-lookup"><span data-stu-id="684bb-188">Select **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="684bb-189">它将在“Root”下显示为子对象。</span><span class="sxs-lookup"><span data-stu-id="684bb-189">It will appear as a child object under **Root**.</span></span>

![添加静态网格](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="684bb-191">选择“SM_Board”，向下滚动到“详细信息”面板的“静态网格”部分，并从下拉列表中选择“棋盘”   。</span><span class="sxs-lookup"><span data-stu-id="684bb-191">Select **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![视口中的棋盘网格](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="684bb-193">继续在“详细信息”面板中，展开“材质”部分，然后从下拉列表中选择“新建资产”>“材质”  。</span><span class="sxs-lookup"><span data-stu-id="684bb-193">Still in the **Details** panel, expand the **Materials** section and select **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="684bb-194">将材质命名为“M_ChessBoard”，并将其保存到“ChessAssets”文件夹中。</span><span class="sxs-lookup"><span data-stu-id="684bb-194">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![创建新材质](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="684bb-196">双击“M_ChessBoard”材质映像以打开材质编辑器。</span><span class="sxs-lookup"><span data-stu-id="684bb-196">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![打开材质编辑器](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="684bb-198">在材质编辑器中，单击右键并搜索“纹理示例”。</span><span class="sxs-lookup"><span data-stu-id="684bb-198">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="684bb-199">在“详细信息”面板中展开“材质表现纹理库”部分，然后将“纹理”设置为“ChessBoard_Albedo”   。</span><span class="sxs-lookup"><span data-stu-id="684bb-199">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="684bb-200">将“RGB”输出引脚拖至“M_ChessBoard”的“基准颜色”引脚上。</span><span class="sxs-lookup"><span data-stu-id="684bb-200">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![设置基准颜色](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="684bb-202">再重复上述步骤 4 次以再创建四个具有以下设置的“纹理示例”节点：</span><span class="sxs-lookup"><span data-stu-id="684bb-202">Repeat the previous step 4 more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="684bb-203">将“纹理”设置为“ChessBoard_AO”，将“RGB”链接到“环境遮蔽”引脚   。</span><span class="sxs-lookup"><span data-stu-id="684bb-203">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="684bb-204">将“纹理”设置为“ChessBoard_Metal”，将“RGB”链接到“金属”引脚   。</span><span class="sxs-lookup"><span data-stu-id="684bb-204">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="684bb-205">将“纹理”设置为“ChessBoard_Normal”，将“RGB”链接到“正常”引脚   。</span><span class="sxs-lookup"><span data-stu-id="684bb-205">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="684bb-206">将“纹理”设置为“ChessBoard_Rough”，将“RGB”链接到“粗糙度”引脚   。</span><span class="sxs-lookup"><span data-stu-id="684bb-206">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="684bb-207">单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="684bb-207">Click **Save**.</span></span> 

![连接剩余纹理](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="684bb-209">在继续之前，请确保材质设置看起来类似于以上屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="684bb-209">Make sure your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="684bb-210">填充场景</span><span class="sxs-lookup"><span data-stu-id="684bb-210">Populating the scene</span></span>
<span data-ttu-id="684bb-211">如果返回到“棋盘”蓝图，将会看到已应用刚创建的材质。</span><span class="sxs-lookup"><span data-stu-id="684bb-211">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="684bb-212">只需设置场景即可！</span><span class="sxs-lookup"><span data-stu-id="684bb-212">All that's left is setting up the scene!</span></span> <span data-ttu-id="684bb-213">首先，更改以下属性，以确保在场景中放置棋盘时，它的大小和角度正确：</span><span class="sxs-lookup"><span data-stu-id="684bb-213">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="684bb-214">将“比例”设置为“(0.05, 0.05, 0.05)”并将“Z 旋转”设置为“90”   。</span><span class="sxs-lookup"><span data-stu-id="684bb-214">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="684bb-215">单击顶部工具栏中的“编译”，然后单击“保存”并返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="684bb-215">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![已应用材质的棋盘](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="684bb-217">右键单击“立方体”>“编辑”>“删除”并将“棋盘”从“内容浏览器”拖至视口中  。</span><span class="sxs-lookup"><span data-stu-id="684bb-217">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="684bb-218">将“位置”设置为“X = 80”、“Y = 0”和“Z = -20”   。</span><span class="sxs-lookup"><span data-stu-id="684bb-218">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="684bb-219">选择“开始”按钮，查看你所处关卡中的新棋盘。</span><span class="sxs-lookup"><span data-stu-id="684bb-219">Select the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="684bb-220">按 Esc 返回到编辑器。</span><span class="sxs-lookup"><span data-stu-id="684bb-220">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="684bb-221">现在，你将按照与棋盘相同的步骤创建棋子：</span><span class="sxs-lookup"><span data-stu-id="684bb-221">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="684bb-222">转到“蓝图”文件夹，右键单击并选择“蓝图类”，然后选择“Actor”  。</span><span class="sxs-lookup"><span data-stu-id="684bb-222">Go to the **Blueprints** folder, right-click, and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="684bb-223">将 Actor 命名为“WhiteKing”。</span><span class="sxs-lookup"><span data-stu-id="684bb-223">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="684bb-224">双击“WhiteKing”以在蓝图编辑器中将其打开，选择“添加组件”>“场景”，并将其命名为“Root”  。</span><span class="sxs-lookup"><span data-stu-id="684bb-224">Double-click **WhiteKing** to open it in the Blueprint Editor, select **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="684bb-225">将“Root”拖放到 DefaultSceneRoot 中来替换它 。</span><span class="sxs-lookup"><span data-stu-id="684bb-225">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="684bb-226">单击“添加组件”>“静态网格”，并将其命名为“SM_King” 。</span><span class="sxs-lookup"><span data-stu-id="684bb-226">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="684bb-227">在“详细信息”面板中，将“静态网格”设置为“Chess_King”，并将“材质”设置为名为“M_ChessWhite”的新材质。</span><span class="sxs-lookup"><span data-stu-id="684bb-227">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="684bb-228">在材质编辑器中打开“M_ChessWhite”，并将以下“纹理示例”节点连接到以下各项：</span><span class="sxs-lookup"><span data-stu-id="684bb-228">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
   * <span data-ttu-id="684bb-229">将“纹理”设置为“ChessWhite_Albedo”并将“RGB”链接到“基本颜色”引脚   。</span><span class="sxs-lookup"><span data-stu-id="684bb-229">Set **Texture** to **ChessWhite_Albedo** and link the **RGB** to the **Base Color** pin.</span></span>
    * <span data-ttu-id="684bb-230">将“纹理”设置为“ChessWhite_AO”，将“RGB”链接到“环境遮蔽”引脚   。</span><span class="sxs-lookup"><span data-stu-id="684bb-230">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="684bb-231">将“纹理”设置为“ChessWhite_Metal”，将“RGB”链接到“金属”引脚   。</span><span class="sxs-lookup"><span data-stu-id="684bb-231">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="684bb-232">将“纹理”设置为“ChessWhite_Normal”，将“RGB”链接到“正常”引脚   。</span><span class="sxs-lookup"><span data-stu-id="684bb-232">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="684bb-233">将“纹理”设置为“ChessWhite_Rough”，将“RGB”链接到“粗糙度”引脚   。</span><span class="sxs-lookup"><span data-stu-id="684bb-233">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="684bb-234">单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="684bb-234">Click **Save**.</span></span> 

<span data-ttu-id="684bb-235">在继续之前，“M_ChessKing”材质应与下图类似。</span><span class="sxs-lookup"><span data-stu-id="684bb-235">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![为国王（棋子）创建材质](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="684bb-237">即将完成，只需将新棋子添加到场景中即可：</span><span class="sxs-lookup"><span data-stu-id="684bb-237">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="684bb-238">打开“WhiteKing”蓝图，并将“比例”更改为“(0.05, 0.05, 0.05)”，将“Z 旋转”更改为“90”。</span><span class="sxs-lookup"><span data-stu-id="684bb-238">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="684bb-239">编译并保存蓝图，然后返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="684bb-239">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="684bb-240">将“WhiteKing”拖到视口中，切换到“世界大纲视图”面板，将“WhiteKing”拖到“棋盘”上，使其成为子对象。</span><span class="sxs-lookup"><span data-stu-id="684bb-240">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![世界大纲视图](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="684bb-242">在“详细信息”面板中的“变形”下，将 WhiteKing 的“位置”设置为“X = -26”、“Y = 4”、“Z = 0”      。</span><span class="sxs-lookup"><span data-stu-id="684bb-242">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="684bb-243">完成！</span><span class="sxs-lookup"><span data-stu-id="684bb-243">That's a wrap!</span></span> <span data-ttu-id="684bb-244">选择“开始”以查看正在运行中的已填充关卡，并在准备好退出时按 Esc。</span><span class="sxs-lookup"><span data-stu-id="684bb-244">Select **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="684bb-245">只是创建一个简单项目就涉及了很多内容，你现在可以进入本系列的下一部分：设置混合现实。</span><span class="sxs-lookup"><span data-stu-id="684bb-245">You covered a lot of ground just creating a simple project, but now you're ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="684bb-246">下一节：3.设置混合现实项目</span><span class="sxs-lookup"><span data-stu-id="684bb-246">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)