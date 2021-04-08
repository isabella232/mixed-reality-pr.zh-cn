---
title: MRTK 教程 - 4. 定位场景中的对象
description: 本课程介绍如何定位场景中的对象，以及如何使用混合现实工具包 (MRTK) 来组织网格中的对象。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 求解器, 网格对象集合
ms.localizationpriority: high
ms.openlocfilehash: 28cebe871e1046e8668a079affabf6167632cfa4
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2021
ms.locfileid: "105983004"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="1ae3b-105">4.定位场景中的对象</span><span class="sxs-lookup"><span data-stu-id="1ae3b-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="1ae3b-106">概述</span><span class="sxs-lookup"><span data-stu-id="1ae3b-106">Overview</span></span>

<span data-ttu-id="1ae3b-107">在本教程中，你将在场景中定位由教程资产提供的对象。</span><span class="sxs-lookup"><span data-stu-id="1ae3b-107">In this tutorial, you will position the provided objects from the tutorial assets in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="1ae3b-108">目标</span><span class="sxs-lookup"><span data-stu-id="1ae3b-108">Objectives</span></span>

* <span data-ttu-id="1ae3b-109">了解如何定位场景中的对象</span><span class="sxs-lookup"><span data-stu-id="1ae3b-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="1ae3b-110">了解如何使用 MRTK 的网格对象集合功能</span><span class="sxs-lookup"><span data-stu-id="1ae3b-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="creating-the-parent-object"></a><span data-ttu-id="1ae3b-111">创建父对象</span><span class="sxs-lookup"><span data-stu-id="1ae3b-111">Creating the parent object</span></span>

<span data-ttu-id="1ae3b-112">在“层次结构”窗口中，右键单击空白区域，然后选择“创建空白项”将空对象添加到场景中：</span><span class="sxs-lookup"><span data-stu-id="1ae3b-112">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![Unity“创建空上下文弹出菜单”](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="1ae3b-114">若要按上图所示并排显示“场景”和“游戏”窗口，请将“游戏”窗口拖放到“场景”窗口的右侧。</span><span class="sxs-lookup"><span data-stu-id="1ae3b-114">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="1ae3b-115">若要详细了解如何自定义工作区，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">自定义工作区</a>文档。</span><span class="sxs-lookup"><span data-stu-id="1ae3b-115">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="1ae3b-116">右键单击新创建的对象，选择“重命名”，然后将名称更改为“RoverExplorer” ：</span><span class="sxs-lookup"><span data-stu-id="1ae3b-116">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![Unity“重命名上下文弹出菜单”](images/mr-learning-base/base-04-section1-step1-2.png)

<span data-ttu-id="1ae3b-118">在仍选中 RoverExplorer 对象的情况下，在“检查器”窗口中，按如下所示配置“转换”组件：</span><span class="sxs-lookup"><span data-stu-id="1ae3b-118">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="1ae3b-119">**位置**：X = 0, Y = -0.6, Z = 2</span><span class="sxs-lookup"><span data-stu-id="1ae3b-119">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="1ae3b-120">**旋转**：X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="1ae3b-120">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="1ae3b-121">**缩放**：X = 1，Y = 1，Z = 1</span><span class="sxs-lookup"><span data-stu-id="1ae3b-121">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![选中并定位了 RoverExplorer 对象的 Unity](images/mr-learning-base/base-04-section1-step1-3.png)

> [!NOTE]
> <span data-ttu-id="1ae3b-123">摄像头表示用户头部，位于原点，即 X = 0，Y = 0，Z = 0。</span><span class="sxs-lookup"><span data-stu-id="1ae3b-123">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="1ae3b-124">一般情况下，Unity 中的 1 个单位大致对应现实生活中的 1 米。</span><span class="sxs-lookup"><span data-stu-id="1ae3b-124">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="1ae3b-125">但也存在例外情况，例如，当对象是缩放对象的子级时。</span><span class="sxs-lookup"><span data-stu-id="1ae3b-125">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="1ae3b-126">在上述场景中，RoverExplorer 位于用户头部前方 2 米、下方 0.6 米处。</span><span class="sxs-lookup"><span data-stu-id="1ae3b-126">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="1ae3b-127">添加教程预制件</span><span class="sxs-lookup"><span data-stu-id="1ae3b-127">Adding the tutorial prefabs</span></span>

<span data-ttu-id="1ae3b-128">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件”文件夹  ：</span><span class="sxs-lookup"><span data-stu-id="1ae3b-128">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![选中了预制件文件夹的 Unity 项目窗口](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="1ae3b-130"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">预制件</a>是作为 Unity 资产存储的预配置 GameObject，可在整个项目中重复使用。</span><span class="sxs-lookup"><span data-stu-id="1ae3b-130">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="1ae3b-131">在“项目”窗口中，单击“Table”预制件并将其拖动到 RoverExplorer 对象上，使其成为 RoverExplorer 对象的子对象，然后在“检查器”窗口中，按如下所示配置“转换”组件  ：</span><span class="sxs-lookup"><span data-stu-id="1ae3b-131">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="1ae3b-132">**位置**：X = 0, Y = -0.005, Z = 0</span><span class="sxs-lookup"><span data-stu-id="1ae3b-132">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="1ae3b-133">**旋转**：X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="1ae3b-133">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="1ae3b-134">**缩放**：X = 1.2，Y = 0.01，Z = 1.2</span><span class="sxs-lookup"><span data-stu-id="1ae3b-134">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![选中并定位了新增的“表”预制件的 Unity](images/mr-learning-base/base-04-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="1ae3b-136">若要按下图所示显示场景，请使用“场景”窗口右上角的<a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">场景 Gizmo</a>，将视角调整为沿正向 Z 轴，双击 MixedRealityPlayspace 对象以将焦点对准摄像头，然后根据需要放大。</span><span class="sxs-lookup"><span data-stu-id="1ae3b-136">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="1ae3b-137">在“项目”窗口中，单击“RoverAssembly”预制件并将其拖动到 RoverExplorer 对象上，使其成为 RoverExplorer 对象的子对象，然后在“检查器”窗口中，按如下所示配置“转换”组件  ：</span><span class="sxs-lookup"><span data-stu-id="1ae3b-137">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="1ae3b-138">**位置**：X = -0.1, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="1ae3b-138">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="1ae3b-139">**旋转**：X = 0, Y = -135, Z = 0</span><span class="sxs-lookup"><span data-stu-id="1ae3b-139">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="1ae3b-140">**缩放**：X = 1，Y = 1，Z = 1</span><span class="sxs-lookup"><span data-stu-id="1ae3b-140">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![选中并定位了新增的 RoverAssembly 预制件的 Unity](images/mr-learning-base/base-04-section2-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="1ae3b-142">组织集合中的对象</span><span class="sxs-lookup"><span data-stu-id="1ae3b-142">Organizing objects in a collection</span></span>

<span data-ttu-id="1ae3b-143">在“层次结构”窗口中，右键单击“RoverExplorer”对象，然后选择“创建空白项”添加一个空对象作为 RoverExplorer 的子对象，将该对象命名为“RoverParts”，并按如下所示配置“转换”组件   ：</span><span class="sxs-lookup"><span data-stu-id="1ae3b-143">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="1ae3b-144">**位置**：X = 0, Y = 0.06, Z = 0</span><span class="sxs-lookup"><span data-stu-id="1ae3b-144">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="1ae3b-145">**旋转**：X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="1ae3b-145">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="1ae3b-146">**缩放**：X = 1，Y = 1，Z = 1</span><span class="sxs-lookup"><span data-stu-id="1ae3b-146">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![选中并定位了新创建的 RoverParts 对象的 Unity](images/mr-learning-base/base-04-section3-step1-1.png)

<span data-ttu-id="1ae3b-148">在“层次结构”窗口中，选择所有“RoverExplorer”>“RoverAssembly”>“RoverModel”>“Parts”子对象，右键单击它们，然后选择“复制”，创建每个部件的副本 ：</span><span class="sxs-lookup"><span data-stu-id="1ae3b-148">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![选中了所有部件且具有“复制上下文弹出菜单”的 Unity](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="1ae3b-150">若要选择多个相邻的对象，请按住 SHIFT 键，并同时使用鼠标选择第一个和最后一个对象。</span><span class="sxs-lookup"><span data-stu-id="1ae3b-150">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="1ae3b-151">在仍选中新复制的 Parts 子对象的情况下，单击它们并将其拖动到 RoverParts 对象上，使其成为 RoverParts 对象的子对象：</span><span class="sxs-lookup"><span data-stu-id="1ae3b-151">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![将新复制的部件作为 RoverParts 对象的子类的 Unity](images/mr-learning-base/base-04-section3-step1-3.png)

<span data-ttu-id="1ae3b-153">为了更轻松地在场景中操作，请在“层次结构”窗口中，单击“RoverAssembly”对象左侧的眼睛图标，将此对象的“场景可见性”切换为关闭  。</span><span class="sxs-lookup"><span data-stu-id="1ae3b-153">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverAssembly** object off.</span></span> <span data-ttu-id="1ae3b-154">这会在“场景”窗口中隐藏该对象，但在游戏中不会改变其可见性：</span><span class="sxs-lookup"><span data-stu-id="1ae3b-154">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![RoverAssembly 场景可见性为关闭的 Unity](images/mr-learning-base/base-04-section3-step1-4.png)

> [!TIP]
> <span data-ttu-id="1ae3b-156">若要详细了解“场景可见性”控件以及如何使用它们来优化场景视图和工作流，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">场景可见性</a>文档。</span><span class="sxs-lookup"><span data-stu-id="1ae3b-156">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="1ae3b-157">在“层次结构”窗口中，将后缀“(1)”替换为“_Part”以整理 RoverParts 子对象的名称 ：</span><span class="sxs-lookup"><span data-stu-id="1ae3b-157">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![清除了复制的部件名称的 Unity](images/mr-learning-base/base-04-section3-step1-5.png)

<span data-ttu-id="1ae3b-159">在“层次结构”窗口中，选择“RoverParts”对象，然后在“检查器”窗口中单击“添加组件”按钮，搜索并选择“GridObjectCollection”，以将“GridObjectCollection”组件添加到“RoverParts”对象  ：</span><span class="sxs-lookup"><span data-stu-id="1ae3b-159">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![正在“添加组件网格对象集合”的 Unity RoverParts 对象](images/mr-learning-base/base-04-section3-step1-6.png)

<span data-ttu-id="1ae3b-161">按如下所示配置“GridObjectCollection”组件值：</span><span class="sxs-lookup"><span data-stu-id="1ae3b-161">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="1ae3b-162">**排序类型**：按字母顺序</span><span class="sxs-lookup"><span data-stu-id="1ae3b-162">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="1ae3b-163">**布局**：水平</span><span class="sxs-lookup"><span data-stu-id="1ae3b-163">**Layout**: Horizontal</span></span>
* <span data-ttu-id="1ae3b-164">**单元格宽度**：0.25</span><span class="sxs-lookup"><span data-stu-id="1ae3b-164">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="1ae3b-165">**到父项的距离**：0.38</span><span class="sxs-lookup"><span data-stu-id="1ae3b-165">**Distance from parent**: 0.38</span></span>

![配置了 GridObjectCollection 组件的 Unity](images/mr-learning-base/base-04-section3-step1-7.png)

<span data-ttu-id="1ae3b-167">然后单击“更新集合”按钮以更新 RoverParts 子对象的位置：</span><span class="sxs-lookup"><span data-stu-id="1ae3b-167">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![应用了 GridObjectCollection 组件的 Unity](images/mr-learning-base/base-04-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="1ae3b-169">祝贺</span><span class="sxs-lookup"><span data-stu-id="1ae3b-169">Congratulations</span></span>

<span data-ttu-id="1ae3b-170">本教程介绍了如何在场景中相对于用户定位对象，以及如何使用 MRTK 的网格对象集合功能来组织集合中的对象。</span><span class="sxs-lookup"><span data-stu-id="1ae3b-170">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

> [!div class="nextstepaction"]
>[<span data-ttu-id="1ae3b-171">下一教程：5.使用求解器创建动态内容</span><span class="sxs-lookup"><span data-stu-id="1ae3b-171">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
