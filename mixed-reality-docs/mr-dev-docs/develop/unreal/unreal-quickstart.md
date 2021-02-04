---
title: 创建第一个 HoloLens Unreal 应用程序
description: 了解如何为 HoloLens 混合现实开发正确配置具有场景对象和输入交互的 Unreal 项目。
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, Unreal 编辑器, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 文档, 指南, 功能, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 移植, 升级
ms.openlocfilehash: 467987f69b50c0ec635c99899d6bcecab5a62af0
ms.sourcegitcommit: 1304f8f0a838290c1ae3db34670b67c75ea9bdaa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/02/2021
ms.locfileid: "99421426"
---
# <a name="creating-your-first-hololens-unreal-application"></a><span data-ttu-id="cea62-104">创建第一个 HoloLens Unreal 应用程序</span><span class="sxs-lookup"><span data-stu-id="cea62-104">Creating your first HoloLens Unreal application</span></span>

<span data-ttu-id="cea62-105">本指南将指导你创建在 Unreal 引擎中的 HoloLens 上运行的第一个混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="cea62-105">This guide will walk you through getting your first Mixed Reality app running on the HoloLens in Unreal Engine.</span></span> <span data-ttu-id="cea62-106">在“Hello World”的传统程序中，你将创建一个在屏幕上显示多维数据集的简单应用程序。</span><span class="sxs-lookup"><span data-stu-id="cea62-106">In the tradition of "Hello World", you'll create a simple app that displays a cube on the screen.</span></span> <span data-ttu-id="cea62-107">为了使应用程序更有用，还会创建第一个手势来旋转多维数据集并退出应用程序。</span><span class="sxs-lookup"><span data-stu-id="cea62-107">To make it more useful, you'll also create your first gesture to rotate the cube and quit the application.</span></span> 

## <a name="objectives"></a><span data-ttu-id="cea62-108">目标</span><span class="sxs-lookup"><span data-stu-id="cea62-108">Objectives</span></span>

* <span data-ttu-id="cea62-109">启动 HoloLens 项目</span><span class="sxs-lookup"><span data-stu-id="cea62-109">Start a HoloLens Project</span></span>
* <span data-ttu-id="cea62-110">启用正确的插件</span><span class="sxs-lookup"><span data-stu-id="cea62-110">Enable the correct plugins</span></span>
* <span data-ttu-id="cea62-111">创建 ARSessionConfig 数据资产</span><span class="sxs-lookup"><span data-stu-id="cea62-111">Create an ARSessionConfig Data Asset</span></span>
* <span data-ttu-id="cea62-112">设置手势输入</span><span class="sxs-lookup"><span data-stu-id="cea62-112">Set up gesture inputs</span></span>
* <span data-ttu-id="cea62-113">构建初级内容</span><span class="sxs-lookup"><span data-stu-id="cea62-113">Build a basic level</span></span>
* <span data-ttu-id="cea62-114">实现收缩手势</span><span class="sxs-lookup"><span data-stu-id="cea62-114">Implement a pinch gesture</span></span>

## <a name="creating-a-new-project"></a><span data-ttu-id="cea62-115">创建新项目</span><span class="sxs-lookup"><span data-stu-id="cea62-115">Creating a new project</span></span>

<span data-ttu-id="cea62-116">首先需要一个待处理的项目。</span><span class="sxs-lookup"><span data-stu-id="cea62-116">The first thing you need is a project to work with.</span></span> <span data-ttu-id="cea62-117">如果你是刚接触的 Unreal 开发人员，则需要从 Epic Launcher [下载支持文件](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="cea62-117">If you're a first-time Unreal developer, you'll need to [download supporting files](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="cea62-118">启动 Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="cea62-118">Launch Unreal Engine</span></span>
2. <span data-ttu-id="cea62-119">在“新建项目类别”中，选择“游戏”，然后单击“下一步”  ：</span><span class="sxs-lookup"><span data-stu-id="cea62-119">In the **New Project Categories**, select **Games** and click **Next**:</span></span>

![“最近使用的项目”窗口打开，并突出显示了“游戏”](images/unreal-quickstart-img-01.png)

3. <span data-ttu-id="cea62-121">选择“空白”模板，然后单击“下一步” ：</span><span class="sxs-lookup"><span data-stu-id="cea62-121">Select the **Blank** template and click **Next**:</span></span>

![Unreal 项目浏览器窗口，突出显示了“空白”模板](images/unreal-quickstart-img-02.png)

4. <span data-ttu-id="cea62-123">在“项目设置”中，设置“C++、可缩放的 3D 或 2D、移动/平板电脑”和“非初学者内容”，然后选择保存位置并单击“创建项目”   </span><span class="sxs-lookup"><span data-stu-id="cea62-123">In the **Project Settings**, set **C++, Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content**, then choose a save location and click **Create Project**</span></span>

> [!NOTE] 
> <span data-ttu-id="cea62-124">使用 C++ 而不是 Blueprint 项目，以便后续可以使用 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="cea62-124">You're using a C++ rather than a Blueprint project in order to be ready to use the OpenXR plugin later.</span></span> <span data-ttu-id="cea62-125">本快速入门使用 Unreal Engine 随附的默认 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="cea62-125">This QuickStart uses the default OpenXR plugin that comes with Unreal Engine.</span></span> <span data-ttu-id="cea62-126">但建议下载和使用官方的 Microsoft OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="cea62-126">However, downloading and using the official Microsoft OpenXR plugin is recommended.</span></span> <span data-ttu-id="cea62-127">这要求项目是 C++ 项目。</span><span class="sxs-lookup"><span data-stu-id="cea62-127">That requires the project to be a C++ project.</span></span>

![“项目设置”窗口，突出显示了项目、性能、目标平台和初学者内容选项](images/unreal-quickstart-img-03.png)

<span data-ttu-id="cea62-129">新项目应在 Unreal 编辑器中自动打开，这意味着你已准备好进入下一部分。</span><span class="sxs-lookup"><span data-stu-id="cea62-129">Your new project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="cea62-130">启用所需插件</span><span class="sxs-lookup"><span data-stu-id="cea62-130">Enabling required plugins</span></span>

<span data-ttu-id="cea62-131">你需要启用两个插件，然后才能开始向场景添加对象。</span><span class="sxs-lookup"><span data-stu-id="cea62-131">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="cea62-132">打开“编辑”>“插件”，并从内置选项列表中选择“增强现实”。</span><span class="sxs-lookup"><span data-stu-id="cea62-132">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span>
* <span data-ttu-id="cea62-133">向下滚动到“HoloLens”并选中“已启用” </span><span class="sxs-lookup"><span data-stu-id="cea62-133">Scroll down to **HoloLens** and check **Enabled**</span></span>

![“插件”窗口，打开了“增强现实”部分并突出显示了 HoloLens](images/unreal-quickstart-img-04.png)

2. <span data-ttu-id="cea62-135">在右上角的搜索框中键入 OpenXR，然后启用 OpenXR 和 OpenXRMsftHandInteraction 插件  ：</span><span class="sxs-lookup"><span data-stu-id="cea62-135">Type **OpenXR** in the search box at the top right and enable the **OpenXR** and **OpenXRMsftHandInteraction** plugins:</span></span>

![“插件”窗口，其中启用了 OpenXR](images/unreal-quickstart-img-05.jpg)

![“插件”窗口，其中启用了 OpenXR Msft Hand Interaction](images/unreal-quickstart-img-06.jpg)

3. <span data-ttu-id="cea62-138">重启编辑器</span><span class="sxs-lookup"><span data-stu-id="cea62-138">Restart your editor</span></span>

> [!NOTE]
> <span data-ttu-id="cea62-139">本教程使用 OpenXR，但上文中安装的两个插件目前尚不提供适用于 HoloLens 开发的完整功能集。</span><span class="sxs-lookup"><span data-stu-id="cea62-139">This tutorial uses OpenXR, but the two plugins you've installed above don't currently provide the full feature set for HoloLens development.</span></span> <span data-ttu-id="cea62-140">HandInteraction 插件可满足后续将使用的“收缩”手势的要求，但如果还想实现基础要求以外的要求，则需要[下载 OpenXR 插件](https://github.com/microsoft/Microsoft-OpenXR-Unreal)。</span><span class="sxs-lookup"><span data-stu-id="cea62-140">The HandInteraction plugin will suffice for the "Pinch" gesture you'll use later, but if you want to go beyond the basics you'll need to [download the OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

<span data-ttu-id="cea62-141">启用插件后，可专注于为其填充内容。</span><span class="sxs-lookup"><span data-stu-id="cea62-141">With the plugins enabled, you can focus on filling it with content.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="cea62-142">创建关卡</span><span class="sxs-lookup"><span data-stu-id="cea62-142">Creating a level</span></span>

<span data-ttu-id="cea62-143">下一个任务是创建具有可供参考和缩放的起点和立方体的玩家设置。</span><span class="sxs-lookup"><span data-stu-id="cea62-143">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="cea62-144">选择“文件”>“新关卡”>“空关卡”。</span><span class="sxs-lookup"><span data-stu-id="cea62-144">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="cea62-145">视口中的默认场景现在应为空</span><span class="sxs-lookup"><span data-stu-id="cea62-145">The default scene in the viewport should now be empty</span></span>
2. <span data-ttu-id="cea62-146">从“模式”选项卡中选择“基本”，并将“PlayerStart”拖到场景中  </span><span class="sxs-lookup"><span data-stu-id="cea62-146">From the **Modes** tab, select **Basic** and drag **PlayerStart** into the scene</span></span>
* <span data-ttu-id="cea62-147">在“详细信息”选项卡中，将“位置”设置为“X = 0, Y = 0”和“Z = 0”，以便在应用启动时将用户放置到场景的中心   </span><span class="sxs-lookup"><span data-stu-id="cea62-147">In the **Details** tab, set **Location** to **X = 0, Y = 0,** and **Z = 0** to place the user at the center of the scene when the app starts</span></span>

![Unreal 编辑器场景，其中添加了位置和 PlayerStart](images/unreal-quickstart-img-07.png)

3. <span data-ttu-id="cea62-149">在“基本”选项卡中，将“立方体”拖到场景中 </span><span class="sxs-lookup"><span data-stu-id="cea62-149">From the **Basic** tab, drag a **Cube** into the scene</span></span>
* <span data-ttu-id="cea62-150">将立方体的“位置”设置为“X = 50, Y = 0”和“Z = 0”，以便在启动时将立方体放置于距播放器 50 厘米处的位置  </span><span class="sxs-lookup"><span data-stu-id="cea62-150">Set the cube's **Location** to **X = 50, Y = 0**, and **Z = 0** to position the cube 50 cm away from the player at start</span></span>
* <span data-ttu-id="cea62-151">将立方体的“缩放”更改为“X = 0.2, Y = 0.2”和“Z = 0.2”  </span><span class="sxs-lookup"><span data-stu-id="cea62-151">Change  the cube's **Scale** to **X = 0.2, Y = 0.2**, and **Z = 0.2**</span></span> 

<span data-ttu-id="cea62-152">除非向场景添加光源（这是测试场景前的最后一个任务），否则看不到立方体。</span><span class="sxs-lookup"><span data-stu-id="cea62-152">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="cea62-153">在“模式”面板上，切换到“光”选项卡，然后将“定向光”拖到场景中  </span><span class="sxs-lookup"><span data-stu-id="cea62-153">In the **Modes** panel, switch to the **Lights** tab and drag a **Directional Light** into the scene</span></span>
* <span data-ttu-id="cea62-154">将光置于“PlayerStart”上方，以便可以看到它</span><span class="sxs-lookup"><span data-stu-id="cea62-154">Position the light above **PlayerStart** so you can see it</span></span>

![Unreal 编辑器场景，其中添加了立方体和定向光](images/unreal-quickstart-img-08.png)

5. <span data-ttu-id="cea62-156">转到“文件”>“保存当前”，将关卡命名为“主”，然后选择“保存”  </span><span class="sxs-lookup"><span data-stu-id="cea62-156">Go to **File > Save Current**, name your level **Main**, and select **Save**</span></span>

<span data-ttu-id="cea62-157">设置场景后，按工具栏中的“开始”，以查看正在运行的立方体！</span><span class="sxs-lookup"><span data-stu-id="cea62-157">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="cea62-158">完成工作后，按 Esc 停止应用程序。</span><span class="sxs-lookup"><span data-stu-id="cea62-158">When you're finished admiring your work, press Esc to stop the application.</span></span>

![播放模式下的场景，其中立方体位于屏幕中间](images/unreal-quickstart-img-09.png)

<span data-ttu-id="cea62-160">设置好场景后，准备在 AR 中进行一些基本交互。</span><span class="sxs-lookup"><span data-stu-id="cea62-160">Now that the scene is set up, lets get it ready for some basic interactions in AR.</span></span> <span data-ttu-id="cea62-161">首先，需创建 AR 会话，然后可以添加蓝图以启用手动交互。</span><span class="sxs-lookup"><span data-stu-id="cea62-161">First, you need to create an AR Session and can add blueprints to enable hand interaction.</span></span>

## <a name="adding-a-session-asset"></a><span data-ttu-id="cea62-162">添加会话资产</span><span class="sxs-lookup"><span data-stu-id="cea62-162">Adding a session asset</span></span>

<span data-ttu-id="cea62-163">Unreal 中的 AR 会话无法自行发生。</span><span class="sxs-lookup"><span data-stu-id="cea62-163">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="cea62-164">要使用会话，需要借助 ARSessionConfig 数据资产，这就是接下来的任务：</span><span class="sxs-lookup"><span data-stu-id="cea62-164">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="cea62-165">在“内容浏览器”中，选择“添加新项”>“其他”>“数据资产”，并确保位于根“内容”文件夹级别 </span><span class="sxs-lookup"><span data-stu-id="cea62-165">In the **Content Browser**, select **Add New > Miscellaneous > Data Asset** and make sure you're at the root Content folder level</span></span>
2. <span data-ttu-id="cea62-166">选择“ARSessionConfig”，单击“选择”，然后将资产命名为“ARSessionConfig”  ：</span><span class="sxs-lookup"><span data-stu-id="cea62-166">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**:</span></span>

![“选择数据资产类”窗口打开，其中突出显示了 AR 会话配置资产](images/unreal-quickstart-img-10.png)

2. <span data-ttu-id="cea62-168">双击“ARSessionConfig”将其打开，保存所有默认设置，然后返回到主窗口 ：</span><span class="sxs-lookup"><span data-stu-id="cea62-168">Double-click **ARSessionConfig** to open it, **Save** with all default settings, and return to the Main window:</span></span>

![“AR 会话配置资产详细信息”窗口](images/unreal-quickstart-img-11.png)

<span data-ttu-id="cea62-170">完成此操作后，下一步是确保在关卡加载时 AR 会话会启动，而在关卡结束时 AR 会话会停止。</span><span class="sxs-lookup"><span data-stu-id="cea62-170">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="cea62-171">幸运的是，Unreal 具有叫做“关卡蓝图”的特殊蓝图，它用作关卡范围的全局事件图。</span><span class="sxs-lookup"><span data-stu-id="cea62-171">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="cea62-172">在关卡蓝图中连接 ARSessionConfig 资产，可确保游戏开始时 AR 会话将立即触发。</span><span class="sxs-lookup"><span data-stu-id="cea62-172">Connecting the ARSessionConfig asset in the Level Blueprint guarantees the AR session will fire right when the game starts playing.</span></span>

3. <span data-ttu-id="cea62-173">从编辑器工具栏中，选择“蓝图”>“打开关卡蓝图”：</span><span class="sxs-lookup"><span data-stu-id="cea62-173">From the editor toolbar, select **Blueprints > Open Level Blueprint**:</span></span>

![“蓝图”菜单打开，其中突出显示了“打开关卡蓝图”选项](images/unreal-quickstart-img-12.png)

4. <span data-ttu-id="cea62-175">将执行节点（左指箭头图标）拖离 Event BeginPlay 并释放</span><span class="sxs-lookup"><span data-stu-id="cea62-175">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release</span></span>
* <span data-ttu-id="cea62-176">搜索“启动 AR 会话”节点，然后按 Enter 键</span><span class="sxs-lookup"><span data-stu-id="cea62-176">Search for the **Start AR Session node** and hit enter</span></span>
* <span data-ttu-id="cea62-177">单击“会话配置”下的“选择资产”下拉列表，然后选择“ARSessionConfig”资产  </span><span class="sxs-lookup"><span data-stu-id="cea62-177">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset</span></span>

![“蓝图”图，其中“event begin play”连接到了“start ar session”函数](images/unreal-quickstart-img-13.png)

5. <span data-ttu-id="cea62-179">右键单击 EventGraph 中的任意位置，然后创建一个新的 Event EndPlay 节点。</span><span class="sxs-lookup"><span data-stu-id="cea62-179">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> 
* <span data-ttu-id="cea62-180">拖动执行脚本，随后放开，然后搜索“停止 AR 会话”节点并按 Enter</span><span class="sxs-lookup"><span data-stu-id="cea62-180">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter</span></span> 
* <span data-ttu-id="cea62-181">点击“编译”和保存”，然后返回到主窗口 </span><span class="sxs-lookup"><span data-stu-id="cea62-181">Hit **Compile**, then **Save** and return to the Main window</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cea62-182">如果在关卡结束时 AR 会话仍在运行，那么在流式传输到头戴显示设备时，如果你重启应用，某些功能可能会停止工作。</span><span class="sxs-lookup"><span data-stu-id="cea62-182">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>

![附加到“stop ar session”函数的“event end play”节点](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a><span data-ttu-id="cea62-184">设置输入</span><span class="sxs-lookup"><span data-stu-id="cea62-184">Setting up inputs</span></span>

1. <span data-ttu-id="cea62-185">选择“编辑”>“项目设置”，然后转到“引擎”>“输入” </span><span class="sxs-lookup"><span data-stu-id="cea62-185">Select **Edit > Project Settings** and go to the **Engine > Input**</span></span>
2. <span data-ttu-id="cea62-186">选择“操作映射”旁的 + 图标，然后创建 RightPinch 和 LeftPinch 操作   ：</span><span class="sxs-lookup"><span data-stu-id="cea62-186">Select the **+** icon next to **Action Mappings** and create **RightPinch** and **LeftPinch** actions:</span></span>

![“绑定输入”设置，其中突出显示了右收缩和左收缩操作映射](images/unreal-quickstart-img-15.jpg)

3. <span data-ttu-id="cea62-188">将 RightPinch 和 LeftPinch 操作映射到相应的 OpenXR Msft Hand Interaction 操作  ：</span><span class="sxs-lookup"><span data-stu-id="cea62-188">Map the **RightPinch** and **LeftPinch** actions the to the respective **OpenXR Msft Hand Interaction** actions:</span></span>

![操作映射，其中突出显示了 Open XR Msft Hand Interaction 选项](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a><span data-ttu-id="cea62-190">设置手势</span><span class="sxs-lookup"><span data-stu-id="cea62-190">Setting up gestures</span></span>

<span data-ttu-id="cea62-191">现在我们已设置了输入，接下来我们将进入有趣的部分：添加手势！</span><span class="sxs-lookup"><span data-stu-id="cea62-191">Now that we have setup the inputs, we can get to the exciting part: Adding gestures!</span></span> <span data-ttu-id="cea62-192">右收缩时旋转立方体，左收缩时退出应用程序。</span><span class="sxs-lookup"><span data-stu-id="cea62-192">Lets rotate the cube on the right pinch and quit the application on left pinch.</span></span>

1. <span data-ttu-id="cea62-193">打开“关卡蓝图”，然后添加 InputAction RightPinch 和 InputAction LeftPinch  </span><span class="sxs-lookup"><span data-stu-id="cea62-193">Open the **Level Blueprint** and add an **InputAction RightPinch** and **InputAction LeftPinch**</span></span>
* <span data-ttu-id="cea62-194">将右收缩事件连接到 AddActorLocalRotation，并将立方体作为目标，将“Delta 旋转”设置为“X = 0, Y = 0”和“Z = 20”    。</span><span class="sxs-lookup"><span data-stu-id="cea62-194">Connect the right pinch event to an **AddActorLocalRotation** with your **Cube** as the target and **Delta Rotation** set to **X = 0, Y = 0**, and **Z = 20**.</span></span> <span data-ttu-id="cea62-195">现在每次收缩时，立方体将旋转 20 度</span><span class="sxs-lookup"><span data-stu-id="cea62-195">The cube will now rotate by 20 degrees every time you pinch</span></span>
* <span data-ttu-id="cea62-196">将左收缩事件连接到“退出游戏”</span><span class="sxs-lookup"><span data-stu-id="cea62-196">Connect the left pinch event to **Quit Game**</span></span>

![关卡蓝图打开，其中有针对右收缩和左收缩事件的输入操作](images/unreal-quickstart-img-17.jpg)

2. <span data-ttu-id="cea62-198">在立方体的“转换”设置中，将“移动性”设置为“可移动”，使其可动态移动  ：</span><span class="sxs-lookup"><span data-stu-id="cea62-198">In the cube's **Transform** settings, set **Mobility** to **Movable** so it can move dynamically:</span></span>

![“转换”设置，其中突出显示了“移动性”属性](images/unreal-quickstart-img-18.jpg)

<span data-ttu-id="cea62-200">现在即可部署和测试应用程序！</span><span class="sxs-lookup"><span data-stu-id="cea62-200">At this point, you're ready to deploy and test the application!</span></span>