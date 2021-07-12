---
title: 电脑全息远程处理入门
description: 完成本课程可以了解如何将混合现实应用程序从电脑远程地流式传输到 HoloLens 2。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 电脑全息远程处理, 工具提示, 眼动跟踪
ms.localizationpriority: high
ms.openlocfilehash: 05831ff19a998bd5e99ab5d20c3fb045a09c55e9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175429"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a><span data-ttu-id="30ce7-104">1.电脑全息远程处理入门</span><span class="sxs-lookup"><span data-stu-id="30ce7-104">1. Getting started with PC Holographic Remoting</span></span>

<span data-ttu-id="30ce7-105">欢迎学习 HoloLens 2 教程。</span><span class="sxs-lookup"><span data-stu-id="30ce7-105">Welcome to the HoloLens 2 tutorials.</span></span> <span data-ttu-id="30ce7-106">该系列由两部分组成，其中你将学习如何创建混合现实体验演示，并了解如何创建用于全息远程处理的电脑应用。</span><span class="sxs-lookup"><span data-stu-id="30ce7-106">In this two-part tutorial series, you will learn how to create a mixed reality experience demonstration and how to create a PC app for Holographic Remoting.</span></span>

<span data-ttu-id="30ce7-107">本教程介绍如何创建混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="30ce7-107">In this tutorial, you'll learn how to create a mixed reality experience.</span></span> <span data-ttu-id="30ce7-108">它将演示 UI 元素、3D 模型操作、模型剪辑和眼动跟踪功能。</span><span class="sxs-lookup"><span data-stu-id="30ce7-108">It will demonstrate UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span>

<span data-ttu-id="30ce7-109">在[创建全息远程处理应用程序](mr-learning-pc-holographic-remoting-02.md)（第二篇教程）中，你将学习如何创建用于全息远程处理的电脑应用。</span><span class="sxs-lookup"><span data-stu-id="30ce7-109">In the second tutorial, [Create a Holographic Remoting application](mr-learning-pc-holographic-remoting-02.md), you will learn how to create a PC app for Holographic Remoting.</span></span> <span data-ttu-id="30ce7-110">你还可随时连接到 HoloLens 2，从而在混合现实中直观呈现 3D 内容。</span><span class="sxs-lookup"><span data-stu-id="30ce7-110">And connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="30ce7-111">目标</span><span class="sxs-lookup"><span data-stu-id="30ce7-111">Objectives</span></span>

* <span data-ttu-id="30ce7-112">导入资产并设置场景</span><span class="sxs-lookup"><span data-stu-id="30ce7-112">Import assets and set up the scene</span></span>
* <span data-ttu-id="30ce7-113">使用 UI 元素和按钮来与全息影像交互</span><span class="sxs-lookup"><span data-stu-id="30ce7-113">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="30ce7-114">为剪辑功能配置3D 对象</span><span class="sxs-lookup"><span data-stu-id="30ce7-114">Configure 3D objects for the clipping feature</span></span>
* <span data-ttu-id="30ce7-115">了解如何通过眼动跟踪激活工具提示</span><span class="sxs-lookup"><span data-stu-id="30ce7-115">Learn about activating tooltips with eye-tracking</span></span>

## <a name="prerequisites"></a><span data-ttu-id="30ce7-116">必备条件</span><span class="sxs-lookup"><span data-stu-id="30ce7-116">Prerequisites</span></span>

* <span data-ttu-id="30ce7-117">一台 Windows 10 电脑，其中已[安装](../../install-the-tools.md)并配置正确的工具</span><span class="sxs-lookup"><span data-stu-id="30ce7-117">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="30ce7-118">基本 C# 编程知识</span><span class="sxs-lookup"><span data-stu-id="30ce7-118">Basic c# programming knowledge</span></span>
* <span data-ttu-id="30ce7-119">一个[针对开发配置](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="30ce7-119">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="30ce7-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已装载 Unity 2020/2019 LTS 且已添加通用 Windows 平台生成支持模块</span><span class="sxs-lookup"><span data-stu-id="30ce7-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="30ce7-121">继续学习之前，强烈建议完成[入门](mr-learning-base-01.md)教程系列，或者具备一些使用 Unity 和 MRTK 的基本经验。</span><span class="sxs-lookup"><span data-stu-id="30ce7-121">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="30ce7-122">本教程系列支持 Unity 2020 LTS（当前版本 2020.3.x）（如果您使用 Open XR）和 Unity 2019 LTS（当前版本 2019.4.x）（如果您使用旧版 WSA）。这会取代上文必备条件链接中所述的任何 Unity 版本要求。</span><span class="sxs-lookup"><span data-stu-id="30ce7-122">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR and Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="30ce7-123">创建和准备 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="30ce7-123">Creating and preparing the Unity project</span></span>

<span data-ttu-id="30ce7-124">在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。</span><span class="sxs-lookup"><span data-stu-id="30ce7-124">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="30ce7-125">为此，请先执行[初始化项目和第一个应用程序](mr-learning-base-02.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的说明：</span><span class="sxs-lookup"><span data-stu-id="30ce7-125">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="30ce7-126">[创建 Unity 项目](mr-learning-base-02.md#creating-the-unity-project)并为其指定适当的名称，例如“MRTK 教程”</span><span class="sxs-lookup"><span data-stu-id="30ce7-126">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="30ce7-127">切换生成平台</span><span class="sxs-lookup"><span data-stu-id="30ce7-127">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="30ce7-128">导入 TextMeshPro 基本资源</span><span class="sxs-lookup"><span data-stu-id="30ce7-128">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="30ce7-129">导入混合现实工具包和配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="30ce7-129">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="30ce7-130">[创建和设置场景](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)，并为场景提供一个合适的名称，例如“电脑全息远程处理”</span><span class="sxs-lookup"><span data-stu-id="30ce7-130">[Creating and setting the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, **PC Holographic Remoting**</span></span>

<span data-ttu-id="30ce7-131">然后，按照[更改空间感知显示选项](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)的说明，将场景的 MRTK 配置配置文件更改为“DefaultHoloLens2ConfigurationProfile”。</span><span class="sxs-lookup"><span data-stu-id="30ce7-131">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile**.</span></span> <span data-ttu-id="30ce7-132">将空间感知网格的显示选项更改为“遮挡”。</span><span class="sxs-lookup"><span data-stu-id="30ce7-132">Change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="30ce7-133">导入教程资产</span><span class="sxs-lookup"><span data-stu-id="30ce7-133">Importing the tutorial assets</span></span>

[!INCLUDE[](includes/importing-tutorial-assets-pc-holographic-remoting.md)]

## <a name="configuring-and-preparing-the-scene"></a><span data-ttu-id="30ce7-134">配置和准备场景</span><span class="sxs-lookup"><span data-stu-id="30ce7-134">Configuring and preparing the scene</span></span>

<span data-ttu-id="30ce7-135">在本部分，你将通过添加一些教程预制件来准备场景。</span><span class="sxs-lookup"><span data-stu-id="30ce7-135">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="30ce7-136">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.PCHolograhicRemoting” > “预制件”文件夹  。</span><span class="sxs-lookup"><span data-stu-id="30ce7-136">In the Project window, navigate to **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder.</span></span> <span data-ttu-id="30ce7-137">在按住 Ctrl 按钮时单击下面 6 个预制件。</span><span class="sxs-lookup"><span data-stu-id="30ce7-137">While holding down the CTRL button, click on the below six prefabs.</span></span>

* <span data-ttu-id="30ce7-138">ButtonParent</span><span class="sxs-lookup"><span data-stu-id="30ce7-138">ButtonParent</span></span>
* <span data-ttu-id="30ce7-139">ClippingObjects</span><span class="sxs-lookup"><span data-stu-id="30ce7-139">ClippingObjects</span></span>
* <span data-ttu-id="30ce7-140">HandSpatialMapButton</span><span class="sxs-lookup"><span data-stu-id="30ce7-140">HandSpatialMapButton</span></span>
* <span data-ttu-id="30ce7-141">说明</span><span class="sxs-lookup"><span data-stu-id="30ce7-141">Instructions</span></span>
* <span data-ttu-id="30ce7-142">ModelParent</span><span class="sxs-lookup"><span data-stu-id="30ce7-142">ModelParent</span></span>
* <span data-ttu-id="30ce7-143">平台</span><span class="sxs-lookup"><span data-stu-id="30ce7-143">Platform</span></span>

![显示了要添加到所选场景的预制件的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

<span data-ttu-id="30ce7-145">将这些模型从预制件文件夹拖放到“层次结构”窗口。</span><span class="sxs-lookup"><span data-stu-id="30ce7-145">Drag-and-drop these models from the prefabs folder into the **Hierarchy window**.</span></span>

![新增的预制件仍处于选中状态的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

<span data-ttu-id="30ce7-147">若要将焦点置于场景中的对象上，可双击 ModelParent 对象，然后再次放大一些：</span><span class="sxs-lookup"><span data-stu-id="30ce7-147">To focus in on the objects in the scene, you can double-click on the **ModelParent** object, and then zoom slightly in again:</span></span>

![ModelParent 对象处于对焦状态的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> <span data-ttu-id="30ce7-149">如果在场景中看到大图标（例如带边框的“T”图标会分散注意力），可<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">将调节器 (Gizmos) 切换</a>到关闭位置来隐藏这些图标。</span><span class="sxs-lookup"><span data-stu-id="30ce7-149">If you find the large icons in your scene, such as, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="30ce7-150">配置按钮以操作场景</span><span class="sxs-lookup"><span data-stu-id="30ce7-150">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="30ce7-151">在本部分，你将向场景中添加脚本来创建按钮事件，从而演示模型切换和剪辑功能的基本原理。</span><span class="sxs-lookup"><span data-stu-id="30ce7-151">In this section, you will add scripts into the scene to create button events demonstrating the fundamentals of model switching and clipping functionality.</span></span>

### <a name="1-configuring-the-interactable-script-component"></a><span data-ttu-id="30ce7-152">1.配置“可交互(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="30ce7-152">1. Configuring the Interactable (Script) component</span></span>

<span data-ttu-id="30ce7-153">在“层次结构”窗口中，展开 ButtonParent 对象并选择“NextButton” 。</span><span class="sxs-lookup"><span data-stu-id="30ce7-153">In the Hierarchy window, expand the **ButtonParent** object and select the **NextButton**.</span></span> <span data-ttu-id="30ce7-154">在检查器窗口中，找到“可交互(脚本)”组件，然后单击 OnClick () 事件下的 + 图标  。</span><span class="sxs-lookup"><span data-stu-id="30ce7-154">In the Inspector window, locate the **Interactable (Script)** component and click on **+** icon under **OnClick ()** event.</span></span>

![添加了 Nextbutton OnClick 事件的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

<span data-ttu-id="30ce7-156">在“层次结构”窗口中仍选中 NextButton 对象的情况下，单击“层次结构”窗口中的 ButtonParent 对象并将其拖放到刚刚添加的事件的空“无(对象)”字段中，使 ButtonParent 对象侦听此按钮的按钮单击事件  ：</span><span class="sxs-lookup"><span data-stu-id="30ce7-156">With the **NextButton** object still selected in the Hierarchy window, click-and-drag the **ButtonParent** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

![配置了 NextButton OnClick 事件侦听器的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

<span data-ttu-id="30ce7-158">单击同一事件的“无函数”下拉列表。</span><span class="sxs-lookup"><span data-stu-id="30ce7-158">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="30ce7-159">然后选择“ViewButtonControl” >  NextModel ()，将 NextModel () 函数设置为从该按钮触发按钮按下事件时触发的操作  ：</span><span class="sxs-lookup"><span data-stu-id="30ce7-159">Then select **ViewButtonControl** > **NextModel ()** to set the **NextModel ()** function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![具有 NextButton OnClick 事件操作选择路径的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a><span data-ttu-id="30ce7-161">2.配置其余的按钮</span><span class="sxs-lookup"><span data-stu-id="30ce7-161">2. Configuring the remaining buttons</span></span>

<span data-ttu-id="30ce7-162">对于剩余的每个按钮，请完成上述的过程，将函数分配给“OnClick ()”事件：</span><span class="sxs-lookup"><span data-stu-id="30ce7-162">For each of the remaining buttons, complete the process outlined above to assign functions to the **OnClick ()** events:</span></span>

* <span data-ttu-id="30ce7-163">对于 PreviousButton 对象，请分配“ViewButtonControl”>“PreviousModel ()”函数 。</span><span class="sxs-lookup"><span data-stu-id="30ce7-163">For PreviousButton object, assign the **ViewButtonContro** l > **PreviousModel ()** function.</span></span>

* <span data-ttu-id="30ce7-164">对于 ClippingButton，请选择“ToggleButton” > “ToggleClipping ()”函数 。</span><span class="sxs-lookup"><span data-stu-id="30ce7-164">For ClippingButton select **ToggleButton** > **ToggleClipping ()** function.</span></span>

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a><span data-ttu-id="30ce7-165">3.配置“视图按钮控件(脚本)”和“切换按钮(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="30ce7-165">3. Configuring the View Button Control (Script)  and Toggle Button (Script) components</span></span>

<span data-ttu-id="30ce7-166">现在根据配置，你的按钮会演示模型切换和剪辑功能。</span><span class="sxs-lookup"><span data-stu-id="30ce7-166">Now your buttons are configured to demonstrate the model switching and clipping functionality.</span></span> <span data-ttu-id="30ce7-167">现可向脚本中添加 3D 模型和剪辑对象。</span><span class="sxs-lookup"><span data-stu-id="30ce7-167">It is time to add 3D models and the clipping objects to the script.</span></span>

<span data-ttu-id="30ce7-168">我们提供了 6 种不同的 3D 模型用于演示，展开 ModelParentobject 可公开这些 3D 模型。</span><span class="sxs-lookup"><span data-stu-id="30ce7-168">We have provided six different 3D models for demonstration, expand the ***ModelParentobject*** to expose these 3D models.</span></span>

<span data-ttu-id="30ce7-169">在“层次结构”窗口中仍选中 ButtonParent 对象的情况下，在检查器窗口中找到“视图按钮控件(脚本)”组件并展开“模型”变量 。</span><span class="sxs-lookup"><span data-stu-id="30ce7-169">With the ButtonParent object still selected in the Hierarchy window, in the Inspector window, locate the **View Button Control (Script)** component and expand the **Models** variable.</span></span>

<span data-ttu-id="30ce7-170">在“大小”字段中，输入要在场景中拥有的 3D 模型的数量。</span><span class="sxs-lookup"><span data-stu-id="30ce7-170">In the **Size** field, enter the number of 3D models you would like to have in your scene.</span></span> <span data-ttu-id="30ce7-171">在本例中，为 6 个模型。</span><span class="sxs-lookup"><span data-stu-id="30ce7-171">In this case, it would be six.</span></span> <span data-ttu-id="30ce7-172">它将创建用于添加新 3D 模型的字段。</span><span class="sxs-lookup"><span data-stu-id="30ce7-172">It will create fields for adding new 3D models.</span></span>

![具有 ViewButtonControl 脚本组件字段的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

<span data-ttu-id="30ce7-174">将 ModelParent 对象的每个子对象拖放到这些字段中。</span><span class="sxs-lookup"><span data-stu-id="30ce7-174">Drag and drop each child object of ModelParent Object into these fields.</span></span>

![配置了 ViewButtonControl 脚本组件字段的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

<span data-ttu-id="30ce7-176">将 ClippingObjects 对象从“层次结构”窗口拖放到“切换按钮(脚本)”组件的“剪辑对象”字段  。</span><span class="sxs-lookup"><span data-stu-id="30ce7-176">Drag and drop the  **ClippingObjects** object from the Hierarchy window to the  **Toggle Button (Script)** component **Clipping Object** field.</span></span>
>[!NOTE]
><span data-ttu-id="30ce7-177">仅保留按钮父对象。</span><span class="sxs-lookup"><span data-stu-id="30ce7-177">Stay in button parent object only.</span></span>

![配置了 ToggleButton 脚本组件字段的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

<span data-ttu-id="30ce7-179">在“层次结构”窗口中，选择 ClippingObjects 预制件，并在检查器窗口中启用它来打开剪辑对象。</span><span class="sxs-lookup"><span data-stu-id="30ce7-179">In the Hierarchy window, select the **ClippingObjects** prefab and enable it in the Inspector window to turn on the Clipping objects.</span></span>

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a><span data-ttu-id="30ce7-180">配置剪辑对象以启用剪辑功能</span><span class="sxs-lookup"><span data-stu-id="30ce7-180">Configuring the clipping objects to enable clipping feature</span></span>

<span data-ttu-id="30ce7-181">在本部分中，你将向单个剪辑对象添加 MarsCuriosityRover 对象的子对象渲染器，演示对 MarsCuriosityRover 模型的剪辑。</span><span class="sxs-lookup"><span data-stu-id="30ce7-181">In this section, you will add MarsCuriosityRover object's child objects renderer into an individual clipping object to demonstrate the clipping of the MarsCuriosityRover model.</span></span>

<span data-ttu-id="30ce7-182">在“层次结构”窗口中，展开 ClippingObjects 对象，显示你将在此项目中使用的 3 个不同的剪辑对象。</span><span class="sxs-lookup"><span data-stu-id="30ce7-182">In the Hierarchy window, expand the **ClippingObjects** object to expose the three different clipping objects that you will be using in this project.</span></span>

<span data-ttu-id="30ce7-183">若要配置 ClippingSphere 对象，请单击它，然后在检查器窗口中找到“剪辑球体(脚本)”组件 。</span><span class="sxs-lookup"><span data-stu-id="30ce7-183">To configure the **ClippingSphere** object, click on it, and in the Inspector window, locate the **Clipping Sphere (Script)** component.</span></span> <span data-ttu-id="30ce7-184">在“大小”字段中输入需要为 3D 模型添加的渲染器数量。</span><span class="sxs-lookup"><span data-stu-id="30ce7-184">Enter the number of renderers in the size field that you need to add for your 3D model.</span></span> <span data-ttu-id="30ce7-185">在本例中，为 MarsCuriosityRover 子对象添加 10 个渲染器。</span><span class="sxs-lookup"><span data-stu-id="30ce7-185">In this case, add 10 for MarsCuriosityRover child objects.</span></span> <span data-ttu-id="30ce7-186">它将创建用于添加渲染器的字段，并将 MarsCuriosityRover 对象的子模型对象拖放到这些字段中。</span><span class="sxs-lookup"><span data-stu-id="30ce7-186">It will create fields for adding renderers, drag and drop MarsCuriosityRover Object's child model objects into these fields.</span></span>

![配置了 ClippingSphere 脚本组件字段的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

<span data-ttu-id="30ce7-188">按照相同的过程，将 MarsCuriosityRover 的子对象渲染器添加到 ClippingBox 和 ClippingPlane 对象 。</span><span class="sxs-lookup"><span data-stu-id="30ce7-188">Follow the same process and add MarsCuriosityRover's child objects renderers to the **ClippingBox** and **ClippingPlane** objects.</span></span>

<span data-ttu-id="30ce7-189">在本教程中，只有 MarsCuriosityRover 模型将用于演示剪辑功能。</span><span class="sxs-lookup"><span data-stu-id="30ce7-189">In this tutorial, only the MarsCuriosityRover model will be used for demonstrating the clipping feature.</span></span> <span data-ttu-id="30ce7-190">它们向更多的模型添加剪辑功能，从而增加了渲染器的大小，并添加了其各自的网格渲染器。</span><span class="sxs-lookup"><span data-stu-id="30ce7-190">They were adding clipping features to more models, increasing the size of the renderer, and adding their individual mesh renderers.</span></span>

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a><span data-ttu-id="30ce7-191">配置眼动跟踪以突出显示工具提示</span><span class="sxs-lookup"><span data-stu-id="30ce7-191">Configuring eye-tracking to highlight tooltips</span></span>

<span data-ttu-id="30ce7-192">本部分探讨如何在项目中启用眼动跟踪。</span><span class="sxs-lookup"><span data-stu-id="30ce7-192">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="30ce7-193">例如，你将实现这样的功能，即在查看 MarsCuriosityRover 各部分时突出显示附加到它们的工具提示，在不看这些部分时隐藏这些提示。</span><span class="sxs-lookup"><span data-stu-id="30ce7-193">For example, you will implement the functionality to highlight tooltips attached to MarsCuriosityRover's parts while looking at them and hiding them, while you are looking away from them.</span></span>

### <a name="1-identify-target-objects-and-associated-tooltips"></a><span data-ttu-id="30ce7-194">1.确定目标对象及关联的工具提示</span><span class="sxs-lookup"><span data-stu-id="30ce7-194">1. Identify target objects and associated tooltips</span></span>

<span data-ttu-id="30ce7-195">在“层次结构”窗口中，选择 ModelParent 对象。</span><span class="sxs-lookup"><span data-stu-id="30ce7-195">In the Hierarchy window, select the ModelParent object.</span></span> <span data-ttu-id="30ce7-196">展开“MarsCuriosity”->“探测器”，找到 MarsCuriosityRover 的五个主要部分：POI-Camera、POI-Wheels、POI-Antena、POI-Spectrometer、POI-RUHF Antenna    。</span><span class="sxs-lookup"><span data-stu-id="30ce7-196">Expand the ***MarsCuriosity -> Rover** _ to find five main parts of the MarsCuriosityRover: _*POI-Camera\*\*, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.</span></span>

* <span data-ttu-id="30ce7-197">在“层次结构”窗口中观察与 MarsCuriosityRover 各部分关联的 5 个对应的工具提示对象。</span><span class="sxs-lookup"><span data-stu-id="30ce7-197">Observe five corresponding tooltip objects associated with MarsCuriosityRover parts in the Hierarchy window.</span></span>
* <span data-ttu-id="30ce7-198">你将配置这些对象，以便在查看 MarsCuriosityRover 各部分时突出显示体验。</span><span class="sxs-lookup"><span data-stu-id="30ce7-198">You will be configuring these objects to highlight the experience when you look at the MarsCuriosityRover parts.</span></span>

![选中并展开了“探测器”对象的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a><span data-ttu-id="30ce7-200">2.实现 While Looking At Target () 和 On Look Away () 事件</span><span class="sxs-lookup"><span data-stu-id="30ce7-200">2. Implement While Looking At Target ()  &  On Look Away () events</span></span>

<span data-ttu-id="30ce7-201">在“层次结构”窗口中，选择 POI-Camera 对象。</span><span class="sxs-lookup"><span data-stu-id="30ce7-201">In the Hierarchy window, select the \***POI-Camera** _ object.</span></span> <span data-ttu-id="30ce7-202">在检查器窗口中，找到“眼动跟踪目标(脚本)”组件，并配置“While Looking At Target ()” & “On Look Away ()”事件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="30ce7-202">In the Inspector window, locate the _ *Eye Tracking Target (Script)*\* component and configure the **While Looking At Target ()** & **On Look Away ()** events as follows:</span></span>

* <span data-ttu-id="30ce7-203">对于“无(对象)”字段，指定“POI Camera 工具提示”对象 </span><span class="sxs-lookup"><span data-stu-id="30ce7-203">To **None (Object)** field, assign the **POI-Camera ToolTip** object</span></span>
* <span data-ttu-id="30ce7-204">从“While Looking At Target ()”事件的“无函数”下拉列表中，选择“GameObject” > “SetActive (bool)”   。</span><span class="sxs-lookup"><span data-stu-id="30ce7-204">From **No Function** dropdown of **While Looking At Target ()** event, select **GameObject** > **SetActive (bool).**</span></span> <span data-ttu-id="30ce7-205">选中它下面的“复选框”，将突出显示工具提示作为在查看目标对象时触发的操作。</span><span class="sxs-lookup"><span data-stu-id="30ce7-205">Select the **Checkbox** under it to highlight the tooltip as the action that is triggered when you look at the target object.</span></span>

![Unity 正在配置 EyeTrackingTarget WhileLookingAtTarget 事件](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* <span data-ttu-id="30ce7-207">按照相同的过程，单击“On Look Away ()”事件侦听器上的“无函数”下拉列表 。</span><span class="sxs-lookup"><span data-stu-id="30ce7-207">Follow the same process and click on the **No Function** dropdown of the **On Look Away ()** event listener.</span></span> <span data-ttu-id="30ce7-208">然后选择“GameObject” > “SetActive (bool)”，并将复选框留空，将隐藏工具提示作为在不看目标对象时触发的操作  。</span><span class="sxs-lookup"><span data-stu-id="30ce7-208">Then select **GameObject** > **SetActive (bool**) and leave the **Checkbox** empty to hide the tooltip as the action that is triggered when you look away from the target object.</span></span>

![配置了 EyeTrackingTarget OnLookAway 事件的 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

<span data-ttu-id="30ce7-210">按照相同的过程，将各自的工具提示对象分配给对应的 MarsCuriosityRover 部分的“While Looking At Target ()”和“On Look Away ()”事件  。</span><span class="sxs-lookup"><span data-stu-id="30ce7-210">Follow the same process and assign respective tooltip objects to their same **MarsCuriosityRover** parts **While Looking At Target ()** & **On Look Away ()** events.</span></span>

<span data-ttu-id="30ce7-211">若要启用眼动跟踪，请遵循这些[准则](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations)。</span><span class="sxs-lookup"><span data-stu-id="30ce7-211">To enable eye tracking, please follow these [guidelines](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span></span>

## <a name="congratulations"></a><span data-ttu-id="30ce7-212">祝贺</span><span class="sxs-lookup"><span data-stu-id="30ce7-212">Congratulations</span></span>

<span data-ttu-id="30ce7-213">在本教程中，你学习了如何构建混合现实体验来演示 UI 元素、3D 模型操作、模型剪辑和眼动跟踪功能。</span><span class="sxs-lookup"><span data-stu-id="30ce7-213">In this tutorial, you learned to build a mixed reality experience demonstrating UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span> <span data-ttu-id="30ce7-214">本教程提供了 NextButton 和 PreviousButton，便于你探索 3D 模型查看器的体验。</span><span class="sxs-lookup"><span data-stu-id="30ce7-214">The tutorial provided you with NextButton and PreviousButton that let you explore the 3D model viewer experience.</span></span> <span data-ttu-id="30ce7-215">通过 ClippingObjectButton，你打开了剪辑对象，还体验了剪辑功能。</span><span class="sxs-lookup"><span data-stu-id="30ce7-215">The ClippingObjectButton made you turn on clipping objects and experience clipping feature.</span></span> <span data-ttu-id="30ce7-216">本教程还为你提供了眼动跟踪元素，以便在体验中突出显示工具提示。</span><span class="sxs-lookup"><span data-stu-id="30ce7-216">The tutorial also provided you with an eye-tracking element to enable highlighting the tooltips in the experience.</span></span>

<span data-ttu-id="30ce7-217">在下堂课中，你将学习如何为电脑创建全息远程处理应用程序来随时连接 HoloLens 2，从而可在混合现实中直观呈现 3D 内容。</span><span class="sxs-lookup"><span data-stu-id="30ce7-217">In the next lesson, you will learn how to create a Holographic Remoting application for PC to connect HoloLens 2 at any point, providing a way to Visualize 3D content in mixed reality.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="30ce7-218">下一课：2.创建全息远程处理应用程序</span><span class="sxs-lookup"><span data-stu-id="30ce7-218">Next Lesson: 2. Create Holographic Remoting application</span></span>](mr-learning-pc-holographic-remoting-02.md)