---
title: 创建 HoloLens 项目
description: 了解如何为 HoloLens 混合现实开发正确配置具有场景对象和输入交互的 Unreal 项目。
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, Unreal 编辑器, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 文档, 指南, 功能, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 移植, 升级
ms.openlocfilehash: 3b2b88ac897a8791fec1ca2942d0db34efcee598
ms.sourcegitcommit: be33fcda10d1cb98df90b428a923289933d42c77
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2021
ms.locfileid: "98672734"
---
# <a name="creating-a-hololens-project"></a><span data-ttu-id="d4f25-104">创建 HoloLens 项目</span><span class="sxs-lookup"><span data-stu-id="d4f25-104">Creating a HoloLens project</span></span>

<span data-ttu-id="d4f25-105">首先需要一个待处理的项目。</span><span class="sxs-lookup"><span data-stu-id="d4f25-105">The first thing you need is a project to work with.</span></span> <span data-ttu-id="d4f25-106">如果你是刚接触的 Unreal 开发人员，则需要从 Epic Launcher [下载支持文件](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)。</span><span class="sxs-lookup"><span data-stu-id="d4f25-106">If you're a first-time Unreal developer, you'll need to [download supporting files](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="d4f25-107">启动 Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="d4f25-107">Launch Unreal Engine</span></span>
2. <span data-ttu-id="d4f25-108">在“新建项目类别”中，选择“游戏”，然后单击“下一步”  ：</span><span class="sxs-lookup"><span data-stu-id="d4f25-108">In the **New Project Categories**, select **Games** and click **Next**:</span></span>

![“最近使用的项目”窗口打开，并突出显示了“游戏”](images/unreal-quickstart-img-01.png)

3. <span data-ttu-id="d4f25-110">选择“空白”模板，然后单击“下一步” ：</span><span class="sxs-lookup"><span data-stu-id="d4f25-110">Select the **Blank** template and click **Next**:</span></span>

![Unreal 项目浏览器窗口，突出显示了“空白”模板](images/unreal-quickstart-img-02.png)

4. <span data-ttu-id="d4f25-112">在“项目设置”中，设置“C++、可缩放的 3D 或 2D、移动/平板电脑”和“非初学者内容”，然后选择保存位置并单击“创建项目”   </span><span class="sxs-lookup"><span data-stu-id="d4f25-112">In the **Project Settings**, set **C++, Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content**, then choose a save location and click **Create Project**</span></span>

> [!NOTE] <span data-ttu-id="d4f25-113">使用 C++ 而不是 Blueprint 项目，以便后续可以使用 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="d4f25-113">You're using a C++ rather than a Blueprint project in order to be ready to use the OpenXR plugin later.</span></span> <span data-ttu-id="d4f25-114">本快速入门使用 Unreal Engine 随附的默认 OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="d4f25-114">This QuickStart uses the default OpenXR plugin that comes with Unreal Engine.</span></span> <span data-ttu-id="d4f25-115">但建议下载和使用官方的 Microsoft OpenXR 插件。</span><span class="sxs-lookup"><span data-stu-id="d4f25-115">However, downloading and using the official Microsoft OpenXR plugin is recommended.</span></span> <span data-ttu-id="d4f25-116">这要求项目是 C++ 项目。</span><span class="sxs-lookup"><span data-stu-id="d4f25-116">That requires the project to be a C++ project.</span></span>

![“项目设置”窗口，突出显示了项目、性能、目标平台和初学者内容选项](images/unreal-quickstart-img-03.png)

<span data-ttu-id="d4f25-118">新项目应在 Unreal 编辑器中自动打开，这意味着你已准备好进入下一部分。</span><span class="sxs-lookup"><span data-stu-id="d4f25-118">Your new project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="d4f25-119">启用所需插件</span><span class="sxs-lookup"><span data-stu-id="d4f25-119">Enabling required plugins</span></span>

<span data-ttu-id="d4f25-120">你需要启用两个插件，然后才能开始向场景添加对象。</span><span class="sxs-lookup"><span data-stu-id="d4f25-120">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="d4f25-121">打开“编辑”>“插件”，并从内置选项列表中选择“增强现实”。</span><span class="sxs-lookup"><span data-stu-id="d4f25-121">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span>
* <span data-ttu-id="d4f25-122">向下滚动到“HoloLens”并选中“已启用” </span><span class="sxs-lookup"><span data-stu-id="d4f25-122">Scroll down to **HoloLens** and check **Enabled**</span></span>

![“插件”窗口，打开了“增强现实”部分并突出显示了 HoloLens](images/unreal-quickstart-img-04.png)

2. <span data-ttu-id="d4f25-124">在右上角的搜索框中键入 OpenXR，然后启用 OpenXR 和 OpenXRMsftHandInteraction 插件  ：</span><span class="sxs-lookup"><span data-stu-id="d4f25-124">Type **OpenXR** in the search box at the top right and enable the **OpenXR** and **OpenXRMsftHandInteraction** plugins:</span></span>

![“插件”窗口，其中启用了 OpenXR](images/unreal-quickstart-img-05.jpg)

![“插件”窗口，其中启用了 OpenXR Msft Hand Interaction](images/unreal-quickstart-img-06.jpg)

3. <span data-ttu-id="d4f25-127">重启编辑器</span><span class="sxs-lookup"><span data-stu-id="d4f25-127">Restart your editor</span></span>

> [!NOTE]
> <span data-ttu-id="d4f25-128">本教程使用 OpenXR，但上文中安装的两个插件目前尚不提供适用于 HoloLens 开发的完整功能集。</span><span class="sxs-lookup"><span data-stu-id="d4f25-128">This tutorial uses OpenXR, but the two plugins you've installed above don't currently provide the full feature set for HoloLens development.</span></span> <span data-ttu-id="d4f25-129">HandInteraction 插件可满足后续将使用的“收缩”手势的要求，但如果还想实现基础要求以外的要求，则需要[下载 OpenXR 插件](https://github.com/microsoft/Microsoft-OpenXR-Unreal)。</span><span class="sxs-lookup"><span data-stu-id="d4f25-129">The HandInteraction plugin will suffice for the "Pinch" gesture you'll use later, but if you want to go beyond the basics you'll need to [download the OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

<span data-ttu-id="d4f25-130">启用插件后，可专注于为其填充内容。</span><span class="sxs-lookup"><span data-stu-id="d4f25-130">With the plugins enabled, you can focus on filling it with content.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="d4f25-131">创建关卡</span><span class="sxs-lookup"><span data-stu-id="d4f25-131">Creating a level</span></span>

<span data-ttu-id="d4f25-132">下一个任务是创建具有可供参考和缩放的起点和立方体的玩家设置。</span><span class="sxs-lookup"><span data-stu-id="d4f25-132">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="d4f25-133">选择“文件”>“新关卡”>“空关卡”。</span><span class="sxs-lookup"><span data-stu-id="d4f25-133">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="d4f25-134">视口中的默认场景现在应为空</span><span class="sxs-lookup"><span data-stu-id="d4f25-134">The default scene in the viewport should now be empty</span></span>
2. <span data-ttu-id="d4f25-135">从“模式”选项卡中选择“基本”，并将“PlayerStart”拖到场景中  </span><span class="sxs-lookup"><span data-stu-id="d4f25-135">From the **Modes** tab, select **Basic** and drag **PlayerStart** into the scene</span></span>
* <span data-ttu-id="d4f25-136">在“详细信息”选项卡中，将“位置”设置为“X = 0, Y = 0”和“Z = 0”，以便在应用启动时将用户放置到场景的中心   </span><span class="sxs-lookup"><span data-stu-id="d4f25-136">In the **Details** tab, set **Location** to **X = 0, Y = 0,** and **Z = 0** to place the user at the center of the scene when the app starts</span></span>

![Unreal 编辑器场景，其中添加了位置和 PlayerStart](images/unreal-quickstart-img-07.png)

3. <span data-ttu-id="d4f25-138">在“基本”选项卡中，将“立方体”拖到场景中 </span><span class="sxs-lookup"><span data-stu-id="d4f25-138">From the **Basic** tab, drag a **Cube** into the scene</span></span>
* <span data-ttu-id="d4f25-139">将立方体的“位置”设置为“X = 50, Y = 0”和“Z = 0”，以便在启动时将立方体放置于距播放器 50 厘米处的位置  </span><span class="sxs-lookup"><span data-stu-id="d4f25-139">Set the cube's **Location** to **X = 50, Y = 0**, and **Z = 0** to position the cube 50 cm away from the player at start</span></span>
* <span data-ttu-id="d4f25-140">将立方体的“缩放”更改为“X = 0.2, Y = 0.2”和“Z = 0.2”  </span><span class="sxs-lookup"><span data-stu-id="d4f25-140">Change  the cube's **Scale** to **X = 0.2, Y = 0.2**, and **Z = 0.2**</span></span> 

<span data-ttu-id="d4f25-141">除非向场景添加光源（这是测试场景前的最后一个任务），否则看不到立方体。</span><span class="sxs-lookup"><span data-stu-id="d4f25-141">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="d4f25-142">在“模式”面板上，切换到“光”选项卡，然后将“定向光”拖到场景中  </span><span class="sxs-lookup"><span data-stu-id="d4f25-142">In the **Modes** panel, switch to the **Lights** tab and drag a **Directional Light** into the scene</span></span>
* <span data-ttu-id="d4f25-143">将光置于“PlayerStart”上方，以便可以看到它</span><span class="sxs-lookup"><span data-stu-id="d4f25-143">Position the light above **PlayerStart** so you can see it</span></span>

![Unreal 编辑器场景，其中添加了立方体和定向光](images/unreal-quickstart-img-08.png)

5. <span data-ttu-id="d4f25-145">转到“文件”>“保存当前”，将关卡命名为“主”，然后选择“保存”  </span><span class="sxs-lookup"><span data-stu-id="d4f25-145">Go to **File > Save Current**, name your level **Main**, and select **Save**</span></span>

<span data-ttu-id="d4f25-146">设置场景后，按工具栏中的“开始”，以查看正在运行的立方体！</span><span class="sxs-lookup"><span data-stu-id="d4f25-146">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="d4f25-147">完成工作后，按 Esc 停止应用程序。</span><span class="sxs-lookup"><span data-stu-id="d4f25-147">When you're finished admiring your work, press Esc to stop the application.</span></span>

![播放模式下的场景，其中立方体位于屏幕中间](images/unreal-quickstart-img-09.png)

<span data-ttu-id="d4f25-149">设置好场景后，准备在 AR 中进行一些基本交互。</span><span class="sxs-lookup"><span data-stu-id="d4f25-149">Now that the scene is set up, lets get it ready for some basic interactions in AR.</span></span> <span data-ttu-id="d4f25-150">首先，需创建 AR 会话，然后可以添加蓝图以启用手动交互。</span><span class="sxs-lookup"><span data-stu-id="d4f25-150">First, you need to create an AR Session and can add blueprints to enable hand interaction.</span></span>

## <a name="adding-a-session-asset"></a><span data-ttu-id="d4f25-151">添加会话资产</span><span class="sxs-lookup"><span data-stu-id="d4f25-151">Adding a session asset</span></span>

<span data-ttu-id="d4f25-152">Unreal 中的 AR 会话无法自行发生。</span><span class="sxs-lookup"><span data-stu-id="d4f25-152">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="d4f25-153">要使用会话，需要借助 ARSessionConfig 数据资产，这就是接下来的任务：</span><span class="sxs-lookup"><span data-stu-id="d4f25-153">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="d4f25-154">在“内容浏览器”中，选择“添加新项”>“其他”>“数据资产”，并确保位于根“内容”文件夹级别 </span><span class="sxs-lookup"><span data-stu-id="d4f25-154">In the **Content Browser**, select **Add New > Miscellaneous > Data Asset** and make sure you're at the root Content folder level</span></span>
2. <span data-ttu-id="d4f25-155">选择“ARSessionConfig”，单击“选择”，然后将资产命名为“ARSessionConfig”  ：</span><span class="sxs-lookup"><span data-stu-id="d4f25-155">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**:</span></span>

![“选择数据资产类”窗口打开，其中突出显示了 AR 会话配置资产](images/unreal-quickstart-img-10.png)

2. <span data-ttu-id="d4f25-157">双击“ARSessionConfig”将其打开，保存所有默认设置，然后返回到主窗口 ：</span><span class="sxs-lookup"><span data-stu-id="d4f25-157">Double-click **ARSessionConfig** to open it, **Save** with all default settings, and return to the Main window:</span></span>

![“AR 会话配置资产详细信息”窗口](images/unreal-quickstart-img-11.png)

<span data-ttu-id="d4f25-159">完成此操作后，下一步是确保在关卡加载时 AR 会话会启动，而在关卡结束时 AR 会话会停止。</span><span class="sxs-lookup"><span data-stu-id="d4f25-159">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="d4f25-160">幸运的是，Unreal 具有叫做“关卡蓝图”的特殊蓝图，它用作关卡范围的全局事件图。</span><span class="sxs-lookup"><span data-stu-id="d4f25-160">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="d4f25-161">在关卡蓝图中连接 ARSessionConfig 资产，可确保游戏开始时 AR 会话将立即触发。</span><span class="sxs-lookup"><span data-stu-id="d4f25-161">Connecting the ARSessionConfig asset in the Level Blueprint guarantees the AR session will fire right when the game starts playing.</span></span>

3. <span data-ttu-id="d4f25-162">从编辑器工具栏中，选择“蓝图”>“打开关卡蓝图”：</span><span class="sxs-lookup"><span data-stu-id="d4f25-162">From the editor toolbar, select **Blueprints > Open Level Blueprint**:</span></span>

![“蓝图”菜单打开，其中突出显示了“打开关卡蓝图”选项](images/unreal-quickstart-img-12.png)

4. <span data-ttu-id="d4f25-164">将执行节点（左指箭头图标）拖离 Event BeginPlay 并释放</span><span class="sxs-lookup"><span data-stu-id="d4f25-164">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release</span></span>
* <span data-ttu-id="d4f25-165">搜索“启动 AR 会话”节点，然后按 Enter 键</span><span class="sxs-lookup"><span data-stu-id="d4f25-165">Search for the **Start AR Session node** and hit enter</span></span>
* <span data-ttu-id="d4f25-166">单击“会话配置”下的“选择资产”下拉列表，然后选择“ARSessionConfig”资产  </span><span class="sxs-lookup"><span data-stu-id="d4f25-166">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset</span></span>

![“蓝图”图，其中“event begin play”连接到了“start ar session”函数](images/unreal-quickstart-img-13.png)

5. <span data-ttu-id="d4f25-168">右键单击 EventGraph 中的任意位置，然后创建一个新的 Event EndPlay 节点。</span><span class="sxs-lookup"><span data-stu-id="d4f25-168">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> 
* <span data-ttu-id="d4f25-169">拖动执行脚本，随后放开，然后搜索“停止 AR 会话”节点并按 Enter</span><span class="sxs-lookup"><span data-stu-id="d4f25-169">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter</span></span> 
* <span data-ttu-id="d4f25-170">点击“编译”和保存”，然后返回到主窗口 </span><span class="sxs-lookup"><span data-stu-id="d4f25-170">Hit **Compile**, then **Save** and return to the Main window</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4f25-171">如果在关卡结束时 AR 会话仍在运行，那么在流式传输到头戴显示设备时，如果你重启应用，某些功能可能会停止工作。</span><span class="sxs-lookup"><span data-stu-id="d4f25-171">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>

![附加到“stop ar session”函数的“event end play”节点](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a><span data-ttu-id="d4f25-173">设置输入</span><span class="sxs-lookup"><span data-stu-id="d4f25-173">Setting up inputs</span></span>

1. <span data-ttu-id="d4f25-174">选择“编辑”>“项目设置”，然后转到“引擎”>“输入” </span><span class="sxs-lookup"><span data-stu-id="d4f25-174">Select **Edit > Project Settings** and go to the **Engine > Input**</span></span>
2. <span data-ttu-id="d4f25-175">选择“操作映射”旁的 + 图标，然后创建 RightPinch 和 LeftPinch 操作   ：</span><span class="sxs-lookup"><span data-stu-id="d4f25-175">Select the **+** icon next to **Action Mappings** and create **RightPinch** and **LeftPinch** actions:</span></span>

![“绑定输入”设置，其中突出显示了右收缩和左收缩操作映射](images/unreal-quickstart-img-15.jpg)

3. <span data-ttu-id="d4f25-177">将 RightPinch 和 LeftPinch 操作映射到相应的 OpenXR Msft Hand Interaction 操作  ：</span><span class="sxs-lookup"><span data-stu-id="d4f25-177">Map the **RightPinch** and **LeftPinch** actions the to the respective **OpenXR Msft Hand Interaction** actions:</span></span>

![操作映射，其中突出显示了 Open XR Msft Hand Interaction 选项](images/unreal-quickstart-img-16.jpg)

4. <span data-ttu-id="d4f25-179">打开“关卡蓝图”，然后添加 InputAction RightPinch 和 InputAction LeftPinch  </span><span class="sxs-lookup"><span data-stu-id="d4f25-179">Open the **Level Blueprint** and add an **InputAction RightPinch** and **InputAction LeftPinch**</span></span>
* <span data-ttu-id="d4f25-180">将右收缩事件连接到 AddActorLocalRotation，并将立方体作为目标，将“Delta 旋转”设置为“X = 0, Y = 0”和“Z = 20”    。</span><span class="sxs-lookup"><span data-stu-id="d4f25-180">Connect the right pinch event to an **AddActorLocalRotation** with your **Cube** as the target and **Delta Rotation** set to **X = 0, Y = 0**, and **Z = 20**.</span></span> <span data-ttu-id="d4f25-181">现在每次收缩时，立方体将旋转 20 度</span><span class="sxs-lookup"><span data-stu-id="d4f25-181">The cube will now rotate by 20 degrees every time you pinch</span></span>
* <span data-ttu-id="d4f25-182">将左收缩事件连接到“退出游戏”</span><span class="sxs-lookup"><span data-stu-id="d4f25-182">Connect the left pinch event to **Quit Game**</span></span>

![关卡蓝图打开，其中有针对右收缩和左收缩事件的输入操作](images/unreal-quickstart-img-17.jpg)

5. <span data-ttu-id="d4f25-184">在立方体的“转换”设置中，将“移动性”设置为“可移动”，使其可动态移动  ：</span><span class="sxs-lookup"><span data-stu-id="d4f25-184">In the cube's **Transform** settings, set **Mobility** to **Movable** so it can move dynamically:</span></span>

![“转换”设置，其中突出显示了“移动性”属性](images/unreal-quickstart-img-18.jpg)

<span data-ttu-id="d4f25-186">现在即可部署和测试应用程序！</span><span class="sxs-lookup"><span data-stu-id="d4f25-186">At this point, you're ready to deply and test the application!</span></span>