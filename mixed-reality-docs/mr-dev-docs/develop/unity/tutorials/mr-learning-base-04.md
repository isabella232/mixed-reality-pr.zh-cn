---
title: MRTK 教程 - 4. 定位场景中的对象
description: 本课程介绍如何定位场景中的对象，以及如何使用混合现实工具包 (MRTK) 来组织网格中的对象。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 求解器, 网格对象集合
ms.localizationpriority: high
ms.openlocfilehash: d5d10893ba8274139c6e09b8cd426d58a0b3a0cb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175468"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="f4d08-105">4.定位场景中的对象</span><span class="sxs-lookup"><span data-stu-id="f4d08-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="f4d08-106">概述</span><span class="sxs-lookup"><span data-stu-id="f4d08-106">Overview</span></span>

<span data-ttu-id="f4d08-107">在本教程中，你将在场景中定位由教程资产提供的对象。</span><span class="sxs-lookup"><span data-stu-id="f4d08-107">In this tutorial, you will position the provided objects from the tutorial assets in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="f4d08-108">目标</span><span class="sxs-lookup"><span data-stu-id="f4d08-108">Objectives</span></span>

* <span data-ttu-id="f4d08-109">了解如何定位场景中的对象</span><span class="sxs-lookup"><span data-stu-id="f4d08-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="f4d08-110">了解如何使用 MRTK 的网格对象集合功能</span><span class="sxs-lookup"><span data-stu-id="f4d08-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="f4d08-111">导入 TextMeshPro 基本资源</span><span class="sxs-lookup"><span data-stu-id="f4d08-111">Importing the TextMeshPro Essential Resources</span></span>
<span data-ttu-id="f4d08-112">MRTK 的 UI 元素需要 TextMeshPro 基本资源。</span><span class="sxs-lookup"><span data-stu-id="f4d08-112">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="f4d08-113">在 Unity 菜单中，选择“窗口” > “TextMeshPro” > “导入 TMP 基本资源”以打开“导入 Unity 包”窗口  ：</span><span class="sxs-lookup"><span data-stu-id="f4d08-113">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Unity 导入 TMP 基本资源菜单路径](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="f4d08-115">在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：</span><span class="sxs-lookup"><span data-stu-id="f4d08-115">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity TMP 基本资源导入窗口](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="f4d08-117">导入教程资产</span><span class="sxs-lookup"><span data-stu-id="f4d08-117">Importing the tutorial assets</span></span>

<span data-ttu-id="f4d08-118">下载以下 Unity 自定义包。</span><span class="sxs-lookup"><span data-stu-id="f4d08-118">Download the following Unity custom package.</span></span> <span data-ttu-id="f4d08-119">此包中含有我们将在本教程中使用的 3D 资产，例如 Mars Rover。</span><span class="sxs-lookup"><span data-stu-id="f4d08-119">This package includes 3D assets such as Mars Rover that we are going to use in this tutorial.</span></span>

* [<span data-ttu-id="f4d08-120">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="f4d08-120">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

<span data-ttu-id="f4d08-121">若要导入 Unity 自定义包，在 Unity 菜单中选择“资产” > “导入包” > “自定义包...”，打开“导入包...”窗口：  </span><span class="sxs-lookup"><span data-stu-id="f4d08-121">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![导入自定义包](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="f4d08-123">在“导入包…”窗口中，选择下载的 MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage，然后单击“打开”按钮：</span><span class="sxs-lookup"><span data-stu-id="f4d08-123">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** you downloaded and click the Open button:</span></span>

![选择资产包](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="f4d08-125">在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：</span><span class="sxs-lookup"><span data-stu-id="f4d08-125">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![选择要导入的所有资产](images/mr-learning-base/base-02-section7-step1-3.png)

<span data-ttu-id="f4d08-127">导入教程资产后，“项目”窗口应如下所示：</span><span class="sxs-lookup"><span data-stu-id="f4d08-127">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![导入资产后的 Unity 项目窗口](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="creating-the-parent-object"></a><span data-ttu-id="f4d08-129">创建父对象</span><span class="sxs-lookup"><span data-stu-id="f4d08-129">Creating the parent object</span></span>

<span data-ttu-id="f4d08-130">在“层次结构”窗口中，右键单击空白区域，然后选择“创建空白项”将空对象添加到场景中：</span><span class="sxs-lookup"><span data-stu-id="f4d08-130">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![Unity“创建空上下文弹出菜单”](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="f4d08-132">若要按上图所示并排显示“场景”和“游戏”窗口，请将“游戏”窗口拖放到“场景”窗口的右侧。</span><span class="sxs-lookup"><span data-stu-id="f4d08-132">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="f4d08-133">若要详细了解如何自定义工作区，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">自定义工作区</a>文档。</span><span class="sxs-lookup"><span data-stu-id="f4d08-133">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="f4d08-134">右键单击新创建的对象，选择“重命名”，然后将名称更改为“RoverExplorer” ：</span><span class="sxs-lookup"><span data-stu-id="f4d08-134">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![Unity“重命名上下文弹出菜单”](images/mr-learning-base/base-04-section1-step1-2.png)

<span data-ttu-id="f4d08-136">在仍选中 RoverExplorer 对象的情况下，在“检查器”窗口中，按如下所示配置“转换”组件：</span><span class="sxs-lookup"><span data-stu-id="f4d08-136">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="f4d08-137">**位置**：X = 0, Y = -0.6, Z = 2</span><span class="sxs-lookup"><span data-stu-id="f4d08-137">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="f4d08-138">**旋转**：X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="f4d08-138">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="f4d08-139">**缩放**：X = 1，Y = 1，Z = 1</span><span class="sxs-lookup"><span data-stu-id="f4d08-139">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![选中并定位了 RoverExplorer 对象的 Unity](images/mr-learning-base/base-04-section1-step1-3.png)

> [!NOTE]
> <span data-ttu-id="f4d08-141">摄像头表示用户头部，位于原点，即 X = 0，Y = 0，Z = 0。</span><span class="sxs-lookup"><span data-stu-id="f4d08-141">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="f4d08-142">一般情况下，Unity 中的 1 个单位大致对应现实生活中的 1 米。</span><span class="sxs-lookup"><span data-stu-id="f4d08-142">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="f4d08-143">但也存在例外情况，例如，当对象是缩放对象的子级时。</span><span class="sxs-lookup"><span data-stu-id="f4d08-143">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="f4d08-144">在上述场景中，RoverExplorer 位于用户头部前方 2 米、下方 0.6 米处。</span><span class="sxs-lookup"><span data-stu-id="f4d08-144">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="f4d08-145">添加教程预制件</span><span class="sxs-lookup"><span data-stu-id="f4d08-145">Adding the tutorial prefabs</span></span>

<span data-ttu-id="f4d08-146">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件”文件夹  ：</span><span class="sxs-lookup"><span data-stu-id="f4d08-146">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![选中了预制件文件夹的 Unity 项目窗口](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="f4d08-148"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">预制件</a>是作为 Unity 资产存储的预配置 GameObject，可在整个项目中重复使用。</span><span class="sxs-lookup"><span data-stu-id="f4d08-148">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="f4d08-149">在“项目”窗口中，单击“Table”预制件并将其拖动到 RoverExplorer 对象上，使其成为 RoverExplorer 对象的子对象，然后在“检查器”窗口中，按如下所示配置“转换”组件  ：</span><span class="sxs-lookup"><span data-stu-id="f4d08-149">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="f4d08-150">**位置**：X = 0, Y = -0.005, Z = 0</span><span class="sxs-lookup"><span data-stu-id="f4d08-150">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="f4d08-151">**旋转**：X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="f4d08-151">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="f4d08-152">**缩放**：X = 1.2，Y = 0.01，Z = 1.2</span><span class="sxs-lookup"><span data-stu-id="f4d08-152">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![选中并定位了新增的“表”预制件的 Unity](images/mr-learning-base/base-04-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="f4d08-154">若要按下图所示显示场景，请使用“场景”窗口右上角的<a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">场景 Gizmo</a>，将视角调整为沿正向 Z 轴，双击 MixedRealityPlayspace 对象以将焦点对准摄像头，然后根据需要放大。</span><span class="sxs-lookup"><span data-stu-id="f4d08-154">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="f4d08-155">在“项目”窗口中，单击“RoverAssembly”预制件并将其拖动到 RoverExplorer 对象上，使其成为 RoverExplorer 对象的子对象，然后在“检查器”窗口中，按如下所示配置“转换”组件  ：</span><span class="sxs-lookup"><span data-stu-id="f4d08-155">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="f4d08-156">**位置**：X = -0.1, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="f4d08-156">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="f4d08-157">**旋转**：X = 0, Y = -135, Z = 0</span><span class="sxs-lookup"><span data-stu-id="f4d08-157">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="f4d08-158">**缩放**：X = 1，Y = 1，Z = 1</span><span class="sxs-lookup"><span data-stu-id="f4d08-158">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![选中并定位了新增的 RoverAssembly 预制件的 Unity](images/mr-learning-base/base-04-section2-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="f4d08-160">组织集合中的对象</span><span class="sxs-lookup"><span data-stu-id="f4d08-160">Organizing objects in a collection</span></span>

<span data-ttu-id="f4d08-161">在“层次结构”窗口中，右键单击“RoverExplorer”对象，然后选择“创建空白项”添加一个空对象作为 RoverExplorer 的子对象，将该对象命名为“RoverParts”，并按如下所示配置“转换”组件   ：</span><span class="sxs-lookup"><span data-stu-id="f4d08-161">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="f4d08-162">**位置**：X = 0, Y = 0.06, Z = 0</span><span class="sxs-lookup"><span data-stu-id="f4d08-162">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="f4d08-163">**旋转**：X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="f4d08-163">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="f4d08-164">**缩放**：X = 1，Y = 1，Z = 1</span><span class="sxs-lookup"><span data-stu-id="f4d08-164">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![选中并定位了新创建的 RoverParts 对象的 Unity](images/mr-learning-base/base-04-section3-step1-1.png)

<span data-ttu-id="f4d08-166">在“层次结构”窗口中，选择所有“RoverExplorer”>“RoverAssembly”>“RoverModel”>“Parts”子对象，右键单击它们，然后选择“复制”，创建每个部件的副本 ：</span><span class="sxs-lookup"><span data-stu-id="f4d08-166">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![选中了所有部件且具有“复制上下文弹出菜单”的 Unity](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="f4d08-168">若要选择多个相邻的对象，请按住 SHIFT 键，并同时使用鼠标选择第一个和最后一个对象。</span><span class="sxs-lookup"><span data-stu-id="f4d08-168">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="f4d08-169">在仍选中新复制的 Parts 子对象的情况下，单击它们并将其拖动到 RoverParts 对象上，使其成为 RoverParts 对象的子对象：</span><span class="sxs-lookup"><span data-stu-id="f4d08-169">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![将新复制的部件作为 RoverParts 对象的子类的 Unity](images/mr-learning-base/base-04-section3-step1-3.png)

<span data-ttu-id="f4d08-171">为了更轻松地在场景中操作，请在“层次结构”窗口中，单击“RoverAssembly”对象左侧的眼睛图标，将此对象的“场景可见性”切换为关闭  。</span><span class="sxs-lookup"><span data-stu-id="f4d08-171">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverAssembly** object off.</span></span> <span data-ttu-id="f4d08-172">这会在“场景”窗口中隐藏该对象，但在游戏中不会改变其可见性：</span><span class="sxs-lookup"><span data-stu-id="f4d08-172">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![RoverAssembly 场景可见性为关闭的 Unity](images/mr-learning-base/base-04-section3-step1-4.png)

> [!TIP]
> <span data-ttu-id="f4d08-174">若要详细了解“场景可见性”控件以及如何使用它们来优化场景视图和工作流，可参阅 Unity 的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">场景可见性</a>文档。</span><span class="sxs-lookup"><span data-stu-id="f4d08-174">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="f4d08-175">在“层次结构”窗口中，将后缀“(1)”替换为“_Part”以整理 RoverParts 子对象的名称 ：</span><span class="sxs-lookup"><span data-stu-id="f4d08-175">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![清除了复制的部件名称的 Unity](images/mr-learning-base/base-04-section3-step1-5.png)

<span data-ttu-id="f4d08-177">在“层次结构”窗口中，选择“RoverParts”对象，然后在“检查器”窗口中单击“添加组件”按钮，搜索并选择“GridObjectCollection”，以将“GridObjectCollection”组件添加到“RoverParts”对象  ：</span><span class="sxs-lookup"><span data-stu-id="f4d08-177">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![正在“添加组件网格对象集合”的 Unity RoverParts 对象](images/mr-learning-base/base-04-section3-step1-6.png)

<span data-ttu-id="f4d08-179">按如下所示配置“GridObjectCollection”组件值：</span><span class="sxs-lookup"><span data-stu-id="f4d08-179">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="f4d08-180">**排序类型**：按字母顺序</span><span class="sxs-lookup"><span data-stu-id="f4d08-180">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="f4d08-181">**布局**：水平</span><span class="sxs-lookup"><span data-stu-id="f4d08-181">**Layout**: Horizontal</span></span>
* <span data-ttu-id="f4d08-182">**单元格宽度**：0.25</span><span class="sxs-lookup"><span data-stu-id="f4d08-182">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="f4d08-183">**到父项的距离**：0.38</span><span class="sxs-lookup"><span data-stu-id="f4d08-183">**Distance from parent**: 0.38</span></span>

![配置了 GridObjectCollection 组件的 Unity](images/mr-learning-base/base-04-section3-step1-7.png)

<span data-ttu-id="f4d08-185">然后单击“更新集合”按钮以更新 RoverParts 子对象的位置：</span><span class="sxs-lookup"><span data-stu-id="f4d08-185">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![应用了 GridObjectCollection 组件的 Unity](images/mr-learning-base/base-04-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="f4d08-187">祝贺</span><span class="sxs-lookup"><span data-stu-id="f4d08-187">Congratulations</span></span>

<span data-ttu-id="f4d08-188">本教程介绍了如何在场景中相对于用户定位对象，以及如何使用 MRTK 的网格对象集合功能来组织集合中的对象。</span><span class="sxs-lookup"><span data-stu-id="f4d08-188">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

> [!div class="nextstepaction"]
>[<span data-ttu-id="f4d08-189">下一教程：5.使用求解器创建动态内容</span><span class="sxs-lookup"><span data-stu-id="f4d08-189">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
