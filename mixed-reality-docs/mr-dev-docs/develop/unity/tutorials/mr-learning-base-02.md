---
title: 初始化项目并部署第一个应用程序
description: 本课程介绍如何配置 Unity 项目以使用混合现实工具包 (MRTK) 以及如何将其部署到 HoloLens 2。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, TextMeshPro
ms.localizationpriority: high
ms.openlocfilehash: 7124650a59271b48b763719063411765b5457768
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176022"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="b2113-104">2.初始化项目并部署第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="b2113-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="b2113-105">在本教程中，你将了解如何创建新的 Unity 项目、如何配置该项目以进行混合现实工具包 (MRTK) 开发，以及如何导入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="b2113-105">In this tutorial, you'll learn how to create a new Unity project, configure it for Mixed Reality Toolkit (MRTK) development, and import MRTK.</span></span> <span data-ttu-id="b2113-106">你还将演练如何配置和生成基本 Unity 场景，并将其从 Visual Studio 部署到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="b2113-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="b2113-107">将其部署到 HoloLens 2 后，应该会看到空间映射网格覆盖了 HoloLens 感知到的所有表面。</span><span class="sxs-lookup"><span data-stu-id="b2113-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="b2113-108">此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="b2113-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="b2113-109">目标</span><span class="sxs-lookup"><span data-stu-id="b2113-109">Objectives</span></span>

* <span data-ttu-id="b2113-110">了解如何配置用于 HoloLens 开发的 Unity</span><span class="sxs-lookup"><span data-stu-id="b2113-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="b2113-111">了解如何生成应用并将其部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="b2113-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="b2113-112">在 HoloLens 2 设备上体验空间映射网格、手部网格和帧率计数器</span><span class="sxs-lookup"><span data-stu-id="b2113-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

### <a name="steps-overview"></a><span data-ttu-id="b2113-113">步骤概述</span><span class="sxs-lookup"><span data-stu-id="b2113-113">Steps overview</span></span>
:::row:::
    :::column:::
       <span data-ttu-id="b2113-114">![概述步骤 1](images/mr-learning-base/base-02-overview-step1.png) **1. 创建新的 Unity 项目**</span><span class="sxs-lookup"><span data-stu-id="b2113-114">![Overview Step 1](images/mr-learning-base/base-02-overview-step1.png) **1. Create a new Unity project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="b2113-115">![概述步骤 2](images/mr-learning-base/base-02-overview-step2.png) **2. 将 MRTK 导入到项目中**</span><span class="sxs-lookup"><span data-stu-id="b2113-115">![Overview Step 2](images/mr-learning-base/base-02-overview-step2.png) **2. Import MRTK into the project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="b2113-116">![概述步骤 3](images/mr-learning-base/base-02-overview-step3.png) **3. 使用 MRTK 配置新场景**</span><span class="sxs-lookup"><span data-stu-id="b2113-116">![Overview Step 3](images/mr-learning-base/base-02-overview-step3.png) **3. Configure a new scene with MRTK**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       <span data-ttu-id="b2113-117">![概述步骤 4](images/mr-learning-base/base-02-overview-step4.png) **4. 构建 Unity 项目**</span><span class="sxs-lookup"><span data-stu-id="b2113-117">![Overview Step 4](images/mr-learning-base/base-02-overview-step4.png) **4. Build Unity Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="b2113-118">![概述步骤 5](images/mr-learning-base/base-02-overview-step5.png) **5. 构建 UWP 项目**</span><span class="sxs-lookup"><span data-stu-id="b2113-118">![Overview Step 5](images/mr-learning-base/base-02-overview-step5.png) **5. Build UWP Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="b2113-119">![概述步骤 6](images/mr-learning-base/base-02-overview-step6.png) **6. 在设备上运行项目**</span><span class="sxs-lookup"><span data-stu-id="b2113-119">![Overview Step 6](images/mr-learning-base/base-02-overview-step6.png) **6. Run Project on the Device**</span></span>
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a><span data-ttu-id="b2113-120">创建 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="b2113-120">Creating the Unity project</span></span>

<span data-ttu-id="b2113-121">启动“Unity 中心”，选择“项目”选项卡，然后单击“新建”按钮旁边的 **向下箭头**：</span><span class="sxs-lookup"><span data-stu-id="b2113-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

<span data-ttu-id="b2113-122">在下拉列表中，选择[先决条件](mr-learning-base-01.md#prerequisites)中指定的 Unity 版本：</span><span class="sxs-lookup"><span data-stu-id="b2113-122">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> <span data-ttu-id="b2113-123">如果 Unity Hub 没有特定的 Unity 版本，可以从 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下载存档</a>启动安装。</span><span class="sxs-lookup"><span data-stu-id="b2113-123">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="b2113-124">在“创建新项目”窗口中执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b2113-124">In the Create a new project window:</span></span>

* <span data-ttu-id="b2113-125">确保将“模板”设置为“3D” </span><span class="sxs-lookup"><span data-stu-id="b2113-125">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="b2113-126">输入合适的“项目名称”，例如“MRTK 教程”</span><span class="sxs-lookup"><span data-stu-id="b2113-126">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="b2113-127">选择合适的“位置”来存储项目，例如“D:\MixedRealityLearning”</span><span class="sxs-lookup"><span data-stu-id="b2113-127">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="b2113-128">单击“创建”按钮，创建并启动新的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="b2113-128">Click the **Create** button to create and launch your new Unity project</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> <span data-ttu-id="b2113-129">在 Windows 上工作时，有 255 个字符的 MAX_PATH 限制。</span><span class="sxs-lookup"><span data-stu-id="b2113-129">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="b2113-130">因此，应将 Unity 项目保存到驱动器的根目录附近。</span><span class="sxs-lookup"><span data-stu-id="b2113-130">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="b2113-131">等待 Unity 创建项目：</span><span class="sxs-lookup"><span data-stu-id="b2113-131">Wait for Unity to create the project:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a><span data-ttu-id="b2113-132">切换生成平台</span><span class="sxs-lookup"><span data-stu-id="b2113-132">Switching the build platform</span></span>

<span data-ttu-id="b2113-133">在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口： </span><span class="sxs-lookup"><span data-stu-id="b2113-133">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity“生成设置...”菜单路径](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="b2113-135">在“生成设置”窗口中选择“通用 Windows 平台”，然后：</span><span class="sxs-lookup"><span data-stu-id="b2113-135">In the Build Settings window, select **Universal Windows Platform** and:</span></span>

1. <span data-ttu-id="b2113-136">将“目标设备”设置为“HoloLens” </span><span class="sxs-lookup"><span data-stu-id="b2113-136">Set **Target device** to **HoloLens**</span></span>
2. <span data-ttu-id="b2113-137">将“体系结构”设置为“ARM 64” </span><span class="sxs-lookup"><span data-stu-id="b2113-137">Set **Architecture** to **ARM 64**</span></span> 
3. <span data-ttu-id="b2113-138">将“生成类型”设置为“D3D 项目”</span><span class="sxs-lookup"><span data-stu-id="b2113-138">Set **Build Type** to **D3D Project**</span></span>
4. <span data-ttu-id="b2113-139">将“目标 SDK 版本”设置为“最新安装项” </span><span class="sxs-lookup"><span data-stu-id="b2113-139">Set **Target SDK Version** to **Latest Installed**</span></span>
5. <span data-ttu-id="b2113-140">将“最低平台版本”设置为 10.0.1024.0 </span><span class="sxs-lookup"><span data-stu-id="b2113-140">Set **Minimum Platform Version** to **10.0.1024.0**</span></span>
6. <span data-ttu-id="b2113-141">将“Visual Studio 版本”设置为“最新安装项” </span><span class="sxs-lookup"><span data-stu-id="b2113-141">Set **Visual Studio Version** to **Latest installed**</span></span>
7. <span data-ttu-id="b2113-142">将“生成和运行位置”设置为“USB 设备” </span><span class="sxs-lookup"><span data-stu-id="b2113-142">Set **Build and Run on** to **USB Device**</span></span>
8. <span data-ttu-id="b2113-143">将“生成配置”设置为“发布”，因为调试存在已知的性能问题 </span><span class="sxs-lookup"><span data-stu-id="b2113-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9. <span data-ttu-id="b2113-144">单击“切换平台”按钮</span><span class="sxs-lookup"><span data-stu-id="b2113-144">Click the Switch Platform button</span></span>

![设置了通用 Windows 平台设置的 Unity 生成设置](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="b2113-146">等待 Unity 完成平台切换操作：</span><span class="sxs-lookup"><span data-stu-id="b2113-146">Wait for Unity to finish switching the platform:</span></span>

![Unity 正在切换平台](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

<span data-ttu-id="b2113-148">当 Unity 完成平台切换后，单击 x 图标，关闭“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="b2113-148">When Unity has finished switching the platform, click the  **x** icon to close the Build Settings window.</span></span>

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a><span data-ttu-id="b2113-149">导入混合现实工具包和配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="b2113-149">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>

<span data-ttu-id="b2113-150">若要将“混合现实工具包”导入 Unity 项目中，需要使用[混合现实功能工具](../welcome-to-mr-feature-tool.md)，开发人员使用该工具能够发现、更新混合现实功能包并将其添加到 Unity 项目中。</span><span class="sxs-lookup"><span data-stu-id="b2113-150">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="b2113-151">你可以按名称或类别搜索包，查看其依赖项，甚至在导入之前查看项目清单文件的建议更改。</span><span class="sxs-lookup"><span data-stu-id="b2113-151">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="b2113-152">从 [Microsoft 下载中心](https://aka.ms/MRFeatureTool)下载最新版本的混合现实功能工具，下载完成后，解压缩文件并将其保存到桌面。</span><span class="sxs-lookup"><span data-stu-id="b2113-152">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="b2113-153">需先安装 [.NET 5.0 运行时](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)，才能运行混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="b2113-153">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)</span></span>

<span data-ttu-id="b2113-154">从下载的文件夹中打开可执行文件“MixedRealityFeatureTool”，以启动混合现实功能工具。</span><span class="sxs-lookup"><span data-stu-id="b2113-154">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="b2113-155">创建场景并配置 MRTK</span><span class="sxs-lookup"><span data-stu-id="b2113-155">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="b2113-156">在 Unity 菜单中，选择“文件” > “新建场景”：</span><span class="sxs-lookup"><span data-stu-id="b2113-156">In the Unity menu, select **File** > **New Scene**:</span></span>

![Unity“新建场景”菜单路径](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="b2113-158">在“新建场景”窗口中，选择“基本（内置）”并单击“创建”以创建新场景：</span><span class="sxs-lookup"><span data-stu-id="b2113-158">In the **New Scene** window select **Basic (Built-in)** and click on **create** to create a new scene:</span></span>

![Unity“新建场景”窗口](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> <span data-ttu-id="b2113-160">上面的屏幕截图来自 Unity 版本 2020，如果您使用的是 Unity 2019，那么单击“创建”时，将创建一个新的空白场景。</span><span class="sxs-lookup"><span data-stu-id="b2113-160">Above screenshot is from Unity Version 2020, if you are using Unity 2019 when you click on **create** a new empty scene will be created.</span></span>

<span data-ttu-id="b2113-161">在 Unity 菜单中，选择“混合现实” > “工具包” > “添加到场景并配置…”，将 MRTK 添加到当前场景  ：</span><span class="sxs-lookup"><span data-stu-id="b2113-161">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity“添加到场景并配置...”菜单路径](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="b2113-163">仍在“层次结构”窗口中选中 MixedRealityToolkit 对象，在“检查器”窗口中验证 MixedRealityToolkit 配置文件是否已设置为 DefaultMixedRealityToolkitConfigurationProfile  ：</span><span class="sxs-lookup"><span data-stu-id="b2113-163">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![选中了 DefaultMixedRealityTookitConfigurationProfile 的 Unity MixedRealityToolkit 组件](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="b2113-165">在 Unity 菜单中选择“文件” > “另存为...”，打开“保存场景”窗口： </span><span class="sxs-lookup"><span data-stu-id="b2113-165">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity“另存为...”菜单路径](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="b2113-167">在“资产” > “场景”下，将场景保存在项目中。</span><span class="sxs-lookup"><span data-stu-id="b2113-167">Save the scene in you project under **Asset** > **Scenes**.</span></span>

![Unity 保存场景“保存”提示窗口](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a><span data-ttu-id="b2113-169">向项目添加手交互</span><span class="sxs-lookup"><span data-stu-id="b2113-169">Adding hand interaction to an object</span></span>

<span data-ttu-id="b2113-170">在 Unity 菜单中，选择“GameObject” > “3D 对象” > “立方体”，将立方体对象添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="b2113-170">In the Unity menu, select **GameObject** > **3D Object** > **Cube** to add a cube object to the scene.</span></span>

![将立方体添加到场景中](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="b2113-172">单击“层次结构”窗口中的“立方体”对象，然后在检查器窗口中按如下所示配置其“转换”组件</span><span class="sxs-lookup"><span data-stu-id="b2113-172">Click the **Cube** object in the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="b2113-173">**位置**：X = 0, Y = -0.1, Z = 0.5</span><span class="sxs-lookup"><span data-stu-id="b2113-173">**Position**: X = 0, Y = -0.1, Z = 0.5</span></span>
* <span data-ttu-id="b2113-174">**旋转**：X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="b2113-174">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="b2113-175">**缩放**：X = 0.1, Y = 0.1, Z = 0.1</span><span class="sxs-lookup"><span data-stu-id="b2113-175">**Scale**: X = 0.1, Y = 0.1, Z = 0.1</span></span>

<span data-ttu-id="b2113-176">1 个 Unity 单位等于 1 米。</span><span class="sxs-lookup"><span data-stu-id="b2113-176">1 Unity unit is 1 meter.</span></span> <span data-ttu-id="b2113-177">我们已将立方体的大小更新到 10x10x10 cm，位于头戴式耳机位置 (0,0,0) 的 50cm 处。</span><span class="sxs-lookup"><span data-stu-id="b2113-177">We have updated cube's size to 10x10x10 cm, placed at 50cm from the headset position (0,0,0).</span></span> <span data-ttu-id="b2113-178">位于眼睛下方 10cm 处，给用户提供舒适的交互体验。</span><span class="sxs-lookup"><span data-stu-id="b2113-178">10cm below the eye level for comfortable interaction.</span></span> 

<span data-ttu-id="b2113-179">如果使用默认缩放 (1,1,1)，则立方体将会太大。</span><span class="sxs-lookup"><span data-stu-id="b2113-179">If you use the default scale (1,1,1), the cube will be too big.</span></span> <span data-ttu-id="b2113-180">如果使用默认位置 (0,0,0)，则该立方体将放在与耳机相同的位置上，你只能在向后移动之后才能看到它。</span><span class="sxs-lookup"><span data-stu-id="b2113-180">If you use the default position (0,0,0), the cube will be placed at the same position as your headset and you won't be able to see it until you move backward.</span></span>

![调整转换信息](images/mr-learning-base/base-02-section8-step1-1b.png)

<span data-ttu-id="b2113-182">若要将焦点置于场景中的对象上，可双击“立方体”对象，然后再次放大一些。</span><span class="sxs-lookup"><span data-stu-id="b2113-182">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again.</span></span> <span data-ttu-id="b2113-183">也可以使用 F 键进行缩放并将焦点置于对象上。</span><span class="sxs-lookup"><span data-stu-id="b2113-183">Or you can use F key to zoom and focus on the object.</span></span>

<span data-ttu-id="b2113-184">要使用跟踪的手进行交互并抓取对象，对象必须具有：</span><span class="sxs-lookup"><span data-stu-id="b2113-184">To interact and grab an object with tracked hands, the object must have:</span></span>
 * <span data-ttu-id="b2113-185">碰撞器组件，如“盒碰撞器”（Unity 的立方体默认已有一个盒碰撞器）</span><span class="sxs-lookup"><span data-stu-id="b2113-185">Collider component such as **Box Collider** (Unity's cube already has a Box Collider by default)</span></span>
 * <span data-ttu-id="b2113-186">“对象操控器(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="b2113-186">**Object Manipulator (Script)** component</span></span>
 * <span data-ttu-id="b2113-187">NearInteractionGrabbable（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="b2113-187">**NearInteractionGrabbable(Script)** component</span></span>

<span data-ttu-id="b2113-188">MRTK 的 ObjectManipulator 脚本能够让对象变得可移动、可缩放和可旋转，这些操作可通过一只或两只手来实现。</span><span class="sxs-lookup"><span data-stu-id="b2113-188">MRTK's **ObjectManipulator** script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="b2113-189">此脚本支持直接操作输入模型，因为此脚本让用户能够直接用手接触全息影像。</span><span class="sxs-lookup"><span data-stu-id="b2113-189">This script supports the direct manipulation input model as the script enables the user to touch holograms directly with their hands.</span></span>

<span data-ttu-id="b2113-190">在“层次结构”窗口中保持选中“立方体”，在“检查器”窗口中单击“添加组件”按钮，然后搜索并选择“对象操控器”脚本，将对象操控器脚本添加到立方体对象。  </span><span class="sxs-lookup"><span data-stu-id="b2113-190">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![向立方体添加对象操控器](images/mr-learning-base/base-02-section8-step1-2.PNG)

<span data-ttu-id="b2113-192">重复相同的操作，以向立方体添加 Near Interaction Grabbable 脚本</span><span class="sxs-lookup"><span data-stu-id="b2113-192">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![向立方体添加 Near Interaction Grabbable](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="b2113-194">在这种情况下，添加对象操控器（脚本）时，将自动添加约束管理器（脚本），因为对象操控器（脚本）依赖于约束管理器。</span><span class="sxs-lookup"><span data-stu-id="b2113-194">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a><span data-ttu-id="b2113-195">通过 MRTK 输入模拟在 Unity 编辑器中测试应用程序</span><span class="sxs-lookup"><span data-stu-id="b2113-195">Testing your application in Unity editor with MRTK input simulation</span></span>

<span data-ttu-id="b2113-196">借助 MRTK 的输入模拟，你可以在 Unity 编辑器中测试各种类型的交互，而无需生成并部署到设备。</span><span class="sxs-lookup"><span data-stu-id="b2113-196">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="b2113-197">这使你可以在设计和开发过程中快速迭代你的想法。</span><span class="sxs-lookup"><span data-stu-id="b2113-197">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="b2113-198">使用键盘和鼠标组合来控制模拟输入。</span><span class="sxs-lookup"><span data-stu-id="b2113-198">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="b2113-199">单击播放按钮，然后进入播放模式。</span><span class="sxs-lookup"><span data-stu-id="b2113-199">Click the play button and enter the play mode.</span></span> <span data-ttu-id="b2113-200">按住左 Shift 或空格键来调出控制器（模拟的双手），鼠标移动将移动控制器，还可以使用鼠标滚轮来远离或靠近摄像头。</span><span class="sxs-lookup"><span data-stu-id="b2113-200">Hold the **Left Shift** or **Space** key to bring up the controller (simulated hands), Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="b2113-201">当指针在立方体上时，按住鼠标左键可抓握立方体对象。</span><span class="sxs-lookup"><span data-stu-id="b2113-201">Once the pointer is on the Cube press and hold **Left Mouse Button** to grab the Cube object.</span></span>

* <span data-ttu-id="b2113-202">按 W、A、S、D、Q、E 键可移动摄像头。</span><span class="sxs-lookup"><span data-stu-id="b2113-202">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="b2113-203">在按住鼠标右键的同时移动鼠标可以四处浏览。</span><span class="sxs-lookup"><span data-stu-id="b2113-203">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="b2113-204">按空格键（右手）或左 Shift 键（左手）以显示模拟的双手 </span><span class="sxs-lookup"><span data-stu-id="b2113-204">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="b2113-205">按 T 或 Y 键以将模拟的双手保持在视野中 </span><span class="sxs-lookup"><span data-stu-id="b2113-205">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="b2113-206">若要旋转模拟的手部，请按住 Ctrl 键并移动鼠标</span><span class="sxs-lookup"><span data-stu-id="b2113-206">To rotate simulated hands, press and hold **Ctrl** key and move mouse</span></span>

![游戏模式](images/mr-learning-base/base-02-section8-step1-4.gif)


## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="b2113-208">将应用程序构建到 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b2113-208">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="b2113-209">1.生成 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="b2113-209">1. Build the Unity project</span></span>

<span data-ttu-id="b2113-210">在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口。 </span><span class="sxs-lookup"><span data-stu-id="b2113-210">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="b2113-211">在“生成设置”窗口中单击“添加打开的场景”按钮，将当前场景添加到“生成中的场景”列表，然后单击“生成”按钮以打开“生成通用 Windows 平台”窗口：</span><span class="sxs-lookup"><span data-stu-id="b2113-211">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![选中了 UWP 的 Unity“生成设置”窗口](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="b2113-213">在“生成通用 Windows 平台”窗口中，选择用于存储生成的适当位置（例如 _D:\MixedRealityLearning\Builds_），创建一个新文件夹并为其指定适当的名称（例如 _GettingStarted_），然后单击“选择文件夹”按钮，启动生成过程：</span><span class="sxs-lookup"><span data-stu-id="b2113-213">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![具有“选择文件夹”提示窗口的 Unity“生成设置”窗口](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="b2113-215">等待 Unity 完成生成过程：</span><span class="sxs-lookup"><span data-stu-id="b2113-215">Wait for Unity to finish the build process:</span></span>

![Unity 正在生成进程](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="b2113-217">2.生成并部署应用程序</span><span class="sxs-lookup"><span data-stu-id="b2113-217">2. Build and deploy the application</span></span>

<span data-ttu-id="b2113-218">生成过程完成后，Unity 会提示 Windows 文件资源管理器打开你存储生成的位置。</span><span class="sxs-lookup"><span data-stu-id="b2113-218">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="b2113-219">在文件夹内导航，然后双击解决方案文件，在 Visual Studio 中其打开：</span><span class="sxs-lookup"><span data-stu-id="b2113-219">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![选中了“新建的 Visual Studio 解决方案”的 Windows 资源管理器](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="b2113-221">如果 Visual Studio 要求安装新组件，请花一点时间确保拥有[安装工具](../../install-the-tools.md)文档中的所有必备组件。</span><span class="sxs-lookup"><span data-stu-id="b2113-221">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="b2113-222">通过选择“Master”配置或“发布”配置、ARM64 体系结构和“设备”作为目标，配置 Visual Studio for HoloLens   ：</span><span class="sxs-lookup"><span data-stu-id="b2113-222">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![配置为部署到 HoloLens 2 的 Visual Studio](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="b2113-224">如果要部署到 HoloLens（第一代），请选择 x86 体系结构。</span><span class="sxs-lookup"><span data-stu-id="b2113-224">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="b2113-225">对于 HoloLens，通常是针对 ARM 体系结构进行生成。</span><span class="sxs-lookup"><span data-stu-id="b2113-225">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="b2113-226">但是，在 Unity 2019.3 中有一个 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知问题</strong></a>，即在 Visual Studio 中选择 ARM 作为生成体系结构时会导致错误。</span><span class="sxs-lookup"><span data-stu-id="b2113-226">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="b2113-227">建议的解决方法是针对 ARM64 进行生成。</span><span class="sxs-lookup"><span data-stu-id="b2113-227">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="b2113-228">如果该方法不可行，请前往“编辑”>“项目设置”>“播放器”>“其他设置”并禁用“图形作业” 。</span><span class="sxs-lookup"><span data-stu-id="b2113-228">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="b2113-229">如果目标选项中没有“设备”，则可能需要将 Visual Studio 解决方案的启动项目从 IL2CPP 项目更改为 UWP 项目。</span><span class="sxs-lookup"><span data-stu-id="b2113-229">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="b2113-230">在“解决方案资源管理器”中，右键单击“YourProjectName (通用 Windows)”并选择“设为启动项目”。</span><span class="sxs-lookup"><span data-stu-id="b2113-230">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="b2113-231">将 HoloLens 连接到计算机，然后选择“调试” > “启动但不调试”，以生成并部署到你的设备 ：</span><span class="sxs-lookup"><span data-stu-id="b2113-231">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio“启动(不调试)”菜单路径](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="b2113-233">在生成到设备之前，设备必须处于开发人员模式并与开发计算机配对。</span><span class="sxs-lookup"><span data-stu-id="b2113-233">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="b2113-234">这两个步骤都可以按照[这些说明](../../platform-capabilities-and-apis/using-visual-studio.md)来完成。</span><span class="sxs-lookup"><span data-stu-id="b2113-234">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="b2113-235">你还可以部署到 [HoloLens 模拟器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)或创建[应用包](/windows/uwp/packaging/packaging-uwp-apps)用于旁加载。</span><span class="sxs-lookup"><span data-stu-id="b2113-235">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="b2113-236">使用“启动但不调试”会自动启动设备上的应用，而不会连接 Visual Studio 调试器。</span><span class="sxs-lookup"><span data-stu-id="b2113-236">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="b2113-237">选择“生成”>“部署解决方案”，在不自动启动应用的情况下将内容部署到设备。</span><span class="sxs-lookup"><span data-stu-id="b2113-237">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="b2113-238">在应用中，你可能会注意到诊断探查器，可以使用语音命令“切换诊断”来切换其可见性。</span><span class="sxs-lookup"><span data-stu-id="b2113-238">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **"Toggle Diagnostics"**.</span></span> <span data-ttu-id="b2113-239">我们建议你在开发过程中使探查器在大部分时间都可见，以便了解何时更改应用可能会影响性能。</span><span class="sxs-lookup"><span data-stu-id="b2113-239">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="b2113-240">例如，HoloLens 应用应以 [60 Fps 连续运行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="b2113-240">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="b2113-241">祝贺</span><span class="sxs-lookup"><span data-stu-id="b2113-241">Congratulations</span></span>

<span data-ttu-id="b2113-242">现在，你已经部署了第一个 HoloLens 2 应用。</span><span class="sxs-lookup"><span data-stu-id="b2113-242">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="b2113-243">打开应用后，你面前应该会出现一个立方体对象，你应该能够通过移动该对象来与其进行交互；并且当你四处走动时，应该会看到一个空间映射网格，它覆盖了 HoloLens 识别出的表面。</span><span class="sxs-lookup"><span data-stu-id="b2113-243">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="b2113-244">此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="b2113-244">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="b2113-245">这些只是 MRTK 附带的几个基础功能。</span><span class="sxs-lookup"><span data-stu-id="b2113-245">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="b2113-246">在接下来的教程中，我们将向场景添加内容，以探索 HoloLens 和 MRTK 的各种功能。</span><span class="sxs-lookup"><span data-stu-id="b2113-246">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2113-247">下一教程：3.配置 MRTK 配置文件</span><span class="sxs-lookup"><span data-stu-id="b2113-247">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
