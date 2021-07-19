---
title: Azure 空间定位点入门
description: 请完成本课程，了解如何在混合现实应用程序中使用 Azure 空间定位点来进行数据定位。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, Azure 空间定位点
ms.localizationpriority: high
ms.openlocfilehash: 9c3ae23c39bf4d0b32d8a5d82716f93fee48b6db
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656642"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="85d0e-104">2.Azure 空间定位点入门</span><span class="sxs-lookup"><span data-stu-id="85d0e-104">2. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="85d0e-105">本教程将介绍启动和停止 Azure 空间定位点会话，以及在单个设备上创建、上传和下载 Azure 空间定位点所需的各个步骤。</span><span class="sxs-lookup"><span data-stu-id="85d0e-105">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="85d0e-106">目标</span><span class="sxs-lookup"><span data-stu-id="85d0e-106">Objectives</span></span>

* <span data-ttu-id="85d0e-107">了解有关使用适用于 HoloLens 2 的 Azure 空间定位点进行开发的基础知识</span><span class="sxs-lookup"><span data-stu-id="85d0e-107">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="85d0e-108">了解如何创建空间定位点并从 Azure 中获取它们</span><span class="sxs-lookup"><span data-stu-id="85d0e-108">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="85d0e-109">创建和准备 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="85d0e-109">Creating and preparing the Unity project</span></span>

<span data-ttu-id="85d0e-110">在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。</span><span class="sxs-lookup"><span data-stu-id="85d0e-110">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="85d0e-111">首先，请按照[初始化项目和部署第一个应用程序](mr-learning-base-02.md)进行操作，但请忽略[在设备上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)说明；其中操作包括以下步骤：</span><span class="sxs-lookup"><span data-stu-id="85d0e-111">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="85d0e-112">[创建 Unity 项目](mr-learning-base-02.md#creating-the-unity-project)并为其指定适当的名称，例如“MRTK 教程”</span><span class="sxs-lookup"><span data-stu-id="85d0e-112">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="85d0e-113">切换生成平台</span><span class="sxs-lookup"><span data-stu-id="85d0e-113">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="85d0e-114">导入 TextMeshPro 基本资源</span><span class="sxs-lookup"><span data-stu-id="85d0e-114">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="85d0e-115">导入混合现实工具包和配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="85d0e-115">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="85d0e-116">[创建和设置场景](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk)，并为场景提供一个合适的名称，例如 AzureSpatialAnchors</span><span class="sxs-lookup"><span data-stu-id="85d0e-116">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="85d0e-117">然后，根据[更改空间感知显示选项](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)说明，确保场景的 MRTK 配置配置文件为“DefaultHoloLens2ConfigurationProfile”，并将空间感知网格的显示选项更改为“遮挡” 。</span><span class="sxs-lookup"><span data-stu-id="85d0e-117">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile**  and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a><span data-ttu-id="85d0e-118">安装内置 Unity 包和导入教程资产</span><span class="sxs-lookup"><span data-stu-id="85d0e-118">Installing inbuilt Unity packages and Importing the tutorial assets</span></span>

[!INCLUDE[](includes/installing-packages-for-asa.md)]

## <a name="preparing-the-scene"></a><span data-ttu-id="85d0e-119">准备场景</span><span class="sxs-lookup"><span data-stu-id="85d0e-119">Preparing the scene</span></span>

<span data-ttu-id="85d0e-120">在本部分，你将通过添加一些教程预制件来准备场景。</span><span class="sxs-lookup"><span data-stu-id="85d0e-120">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="85d0e-121">在“项目”窗口中导航到“资产” > “MRTK.Tutorials.AzureSpatialAnchors” > “预制件”文件夹，然后单击并将以下预制件拖动到“层次结构”窗口中，以将其添加到场景中  ：</span><span class="sxs-lookup"><span data-stu-id="85d0e-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="85d0e-122">ButtonParent 预制件</span><span class="sxs-lookup"><span data-stu-id="85d0e-122">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="85d0e-123">DebugWindow 预制件</span><span class="sxs-lookup"><span data-stu-id="85d0e-123">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="85d0e-124">Instructions 预制件</span><span class="sxs-lookup"><span data-stu-id="85d0e-124">**Instructions** prefabs</span></span>
* <span data-ttu-id="85d0e-125">ParentAnchor 预制件</span><span class="sxs-lookup"><span data-stu-id="85d0e-125">**ParentAnchor** prefabs</span></span>

![选中新增的预制件的 Unity](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="85d0e-127">如果在场景中看到很大的图标（例如，框住的“T”图标会分散注意力），可以通过<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">将调节器 (Gizmos) 切换</a>到关闭位置来隐藏这些图标，如上图所示。</span><span class="sxs-lookup"><span data-stu-id="85d0e-127">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

<span data-ttu-id="85d0e-128">在“层次结构”窗口中选择“MixedRealityToolkit”对象，使用检查器窗口中的“添加组件”按钮添加以下组件 ：</span><span class="sxs-lookup"><span data-stu-id="85d0e-128">Select **MixedRealityToolkit** object in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="85d0e-129">AR 空间点管理器(脚本)</span><span class="sxs-lookup"><span data-stu-id="85d0e-129">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="85d0e-130">DisableDiagnosticsSystem (脚本)</span><span class="sxs-lookup"><span data-stu-id="85d0e-130">DisableDiagnosticsSystem (Script)</span></span>

![<span data-ttu-id="85d0e-131">添加了 AR 定位点管理器和 DisableDiagnosticsSystem 组件的 Unity MixedRealityToolkit 对象</span><span class="sxs-lookup"><span data-stu-id="85d0e-131">Unity MixedRealityToolkit object with AR Anchor Manager and DisableDiagnosticsSystem components added</span></span> ](images/mr-learning-asa/asa-02-section4-step1-2.PNG)

> [!WARNING]
> <span data-ttu-id="85d0e-132">ASA v2.9.0 和 v2.10.0-preview.1 存在一个已知问题，需要在场景中放置两个额外对象。</span><span class="sxs-lookup"><span data-stu-id="85d0e-132">There is a known issue with ASA v2.9.0 and v2.10.0-preview.1 that requires two additional objects to be placed in the scene.</span></span> <span data-ttu-id="85d0e-133">请使用检查器窗口中的“添加组件”按钮向“MixedRealityToolkit”对象添加“AR 摄像头管理器（脚本）”和“AR 会话（脚本）”。</span><span class="sxs-lookup"><span data-stu-id="85d0e-133">Please use the **Add Component** button in the inspector window to add an AR Camera Manager (Script) and an AR Session (Script) to the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="85d0e-134">请务必取消选中检查器窗口中“摄像头”对象旁边的复选框，以禁用在添加“AR 摄像头管理器（脚本）”时自动创建的摄像头。</span><span class="sxs-lookup"><span data-stu-id="85d0e-134">Be sure to disable the Camera that is created automatically while adding the AR Camera Manager (Script) by unchecking the checkbox next to the Camera object in the inspector window.</span></span> <span data-ttu-id="85d0e-135">此问题将在 ASA v 2.10.0 的完整版本中得到解决。</span><span class="sxs-lookup"><span data-stu-id="85d0e-135">This issue will be addressed in the full release of ASA v2.10.0.</span></span>
>

> [!NOTE]
> <span data-ttu-id="85d0e-136">添加“AR 空间点管理器（脚本）”组件时，会自动添加“AR 会话原点（脚本）”组件，因为它是“AR 空间点管理器（脚本）”所必需的。</span><span class="sxs-lookup"><span data-stu-id="85d0e-136">When you add the AR Anchor Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Anchor Manager (Script) component.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="85d0e-137">配置按钮以操作场景</span><span class="sxs-lookup"><span data-stu-id="85d0e-137">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="85d0e-138">在本部分，你要将脚本添加到场景，以创建一系列按钮事件，用于演示本地定位点和 Azure 空间定位点在应用中的行为方式的基本原理。</span><span class="sxs-lookup"><span data-stu-id="85d0e-138">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="85d0e-139">在“层次结构”窗口中展开“ButtonParent”对象，然后选择名为“StartAzureSession”的第一个子对象，在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示   ：</span><span class="sxs-lookup"><span data-stu-id="85d0e-139">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="85d0e-140">将 ParentAnchor 对象指定为“On Click ()”事件的侦听器，具体方法是将该对象从“层次结构”窗口拖到“无(对象)”字段 </span><span class="sxs-lookup"><span data-stu-id="85d0e-140">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="85d0e-141">从“无函数”下拉列表中，选择“AnchorModuleScript” > “StartAzureSession ()”，将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="85d0e-141">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![配置了 StartAzureSession 按钮 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="85d0e-143">在“层次结构”窗口中选择名为“StopAzureSession”的下一个按钮，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示  ：</span><span class="sxs-lookup"><span data-stu-id="85d0e-143">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="85d0e-144">将 ParentAnchor 对象指定为“On Click ()”事件的侦听器，具体方法是将该对象从“层次结构”窗口拖到“无(对象)”字段 </span><span class="sxs-lookup"><span data-stu-id="85d0e-144">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="85d0e-145">从“无函数”下拉列表中，选择“AnchorModuleScript” > “StopAzureSession ()”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="85d0e-145">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![配置了 StopAzureSession 按钮 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="85d0e-147">在“层次结构”窗口中选择名为“CreateAzureAnchor”的下一个按钮，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示  ：</span><span class="sxs-lookup"><span data-stu-id="85d0e-147">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="85d0e-148">将 ParentAnchor 对象指定为“On Click ()”事件的侦听器，具体方法是将该对象从“层次结构”窗口拖到“无(对象)”字段 </span><span class="sxs-lookup"><span data-stu-id="85d0e-148">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="85d0e-149">从“无函数”下拉列表中，选择“AnchorModuleScript” > “CreateAzureAnchor ()”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="85d0e-149">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="85d0e-150">将 ParentAnchor 对象分配到空的“无(游戏对象)”字段，使其成为 CreateAzureAnchor () 函数的参数 </span><span class="sxs-lookup"><span data-stu-id="85d0e-150">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![配置了 CreateAzureAnchor 按钮 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="85d0e-152">在“层次结构”窗口中选择名为“RemoveLocalAnchor”的下一个按钮，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示  ：</span><span class="sxs-lookup"><span data-stu-id="85d0e-152">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="85d0e-153">将 ParentAnchor 对象指定为“On Click ()”事件的侦听器，具体方法是将该对象从“层次结构”窗口拖到“无(对象)”字段 </span><span class="sxs-lookup"><span data-stu-id="85d0e-153">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="85d0e-154">从“无函数”下拉列表中，选择“AnchorModuleScript” > “RemoveLocalAnchor ()”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="85d0e-154">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="85d0e-155">将 ParentAnchor 对象分配到空的“无(游戏对象)”字段，使其成为 RemoveLocalAnchor () 函数的参数 </span><span class="sxs-lookup"><span data-stu-id="85d0e-155">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![配置了 RemoveLocalAnchor 按钮 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="85d0e-157">在“层次结构”窗口中选择名为“FindAzureAnchor”的下一个按钮，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示  ：</span><span class="sxs-lookup"><span data-stu-id="85d0e-157">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="85d0e-158">将 ParentAnchor 对象指定为“On Click ()”事件的侦听器，具体方法是将该对象从“层次结构”窗口拖到“无(对象)”字段 </span><span class="sxs-lookup"><span data-stu-id="85d0e-158">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="85d0e-159">从“无函数”下拉列表中，选择“AnchorModuleScript” > “FindAzureAnchor ()”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="85d0e-159">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![配置了 FindAzureAnchor 按钮 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="85d0e-161">在“层次结构”窗口中选择名为“DeleteAzureAnchor”的下一个按钮，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示  ：</span><span class="sxs-lookup"><span data-stu-id="85d0e-161">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="85d0e-162">将 ParentAnchor 对象指定为“On Click ()”事件的侦听器，具体方法是将该对象从“层次结构”窗口拖到“无(对象)”字段 </span><span class="sxs-lookup"><span data-stu-id="85d0e-162">Assign the **ParentAnchor** object as a listener for the On Click () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="85d0e-163">从“无函数”下拉列表中，选择“AnchorModuleScript” > “DeleteAzureAnchor ()”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="85d0e-163">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![配置了 DeleteAzureAnchor 按钮 OnClick 事件的 Unity](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="85d0e-165">将场景连接到 Azure 资源</span><span class="sxs-lookup"><span data-stu-id="85d0e-165">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="85d0e-166">在“层次结构”窗口中选择“ParentAnchor”对象，然后在“检查器”窗口中，找到“空间定位点管理器(脚本)”组件。 </span><span class="sxs-lookup"><span data-stu-id="85d0e-166">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="85d0e-167">使用来自 Azure 空间定位点帐户（该帐户作为本教程系列[必备条件](mr-learning-asa-01.md#prerequisites)的一部分创建）的凭据配置“凭据”部分：</span><span class="sxs-lookup"><span data-stu-id="85d0e-167">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="85d0e-168">在“空间定位点帐户 ID”字段中，粘贴来自你的 Azure 空间定位点帐户的“帐户 ID”</span><span class="sxs-lookup"><span data-stu-id="85d0e-168">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="85d0e-169">在“空间定位点帐户密钥”字段中，粘贴来自你的 Azure 空间定位点帐户的主“访问密钥”或辅助“访问密钥”</span><span class="sxs-lookup"><span data-stu-id="85d0e-169">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="85d0e-170">在“空间定位点帐户域”字段中，粘贴来自你的 Azure 空间定位点帐户的“帐户域”</span><span class="sxs-lookup"><span data-stu-id="85d0e-170">In the **Spatial Anchors Account Domain** field, paste the **Account Domain** from your Azure Spatial Anchors account</span></span>

![配置了空间定位点管理器的 Unity](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="85d0e-172">尝试 Azure 空间定位点的基本行为</span><span class="sxs-lookup"><span data-stu-id="85d0e-172">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="85d0e-173">Azure 空间定位点不能在 Unity 中运行，因此，若要测试 Azure 空间定位点功能，需生成项目并将应用部署到设备。</span><span class="sxs-lookup"><span data-stu-id="85d0e-173">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="85d0e-174">有关如何生成 Unity 项目并将其部署到 HoloLens 2 的提示，可参阅[在 HoloLens 2 上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。</span><span class="sxs-lookup"><span data-stu-id="85d0e-174">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="85d0e-175">当应用在设备上运行时，请按照“Azure 空间定位点教程说明”面板上显示的屏幕说明进行操作：</span><span class="sxs-lookup"><span data-stu-id="85d0e-175">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="85d0e-176">将多维数据集移动至其他位置</span><span class="sxs-lookup"><span data-stu-id="85d0e-176">Move the cube to a different location</span></span>
2. <span data-ttu-id="85d0e-177">启动 Azure 会话</span><span class="sxs-lookup"><span data-stu-id="85d0e-177">Start Azure Session</span></span>
3. <span data-ttu-id="85d0e-178">创建 Azure 定位点（在多维数据集的位置创建定位点）。</span><span class="sxs-lookup"><span data-stu-id="85d0e-178">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
4. <span data-ttu-id="85d0e-179">停止 Azure 会话</span><span class="sxs-lookup"><span data-stu-id="85d0e-179">Stop Azure Session</span></span>
5. <span data-ttu-id="85d0e-180">删除本地定位点（允许用户移动多维数据集）</span><span class="sxs-lookup"><span data-stu-id="85d0e-180">Remove Local Anchor (allows the user to move the cube)</span></span>
6. <span data-ttu-id="85d0e-181">将多维数据集移动至其他位置</span><span class="sxs-lookup"><span data-stu-id="85d0e-181">Move the cube somewhere else</span></span>
7. <span data-ttu-id="85d0e-182">启动 Azure 会话</span><span class="sxs-lookup"><span data-stu-id="85d0e-182">Start Azure Session</span></span>
8. <span data-ttu-id="85d0e-183">查找 Azure 定位点（将多维数据集定位到步骤 3 所述的位置）</span><span class="sxs-lookup"><span data-stu-id="85d0e-183">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
9. <span data-ttu-id="85d0e-184">删除 Azure 定位点</span><span class="sxs-lookup"><span data-stu-id="85d0e-184">Delete Azure Anchor</span></span>
10. <span data-ttu-id="85d0e-185">停止 Azure 会话</span><span class="sxs-lookup"><span data-stu-id="85d0e-185">Stop Azure session</span></span>

![选中 Instructions 对象的 Unity](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="85d0e-187">Azure 空间定位点将使用 Internet 来保存和加载定位点数据，因此请确保设备已连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="85d0e-187">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="85d0e-188">定位体验</span><span class="sxs-lookup"><span data-stu-id="85d0e-188">Anchoring an experience</span></span>

<span data-ttu-id="85d0e-189">前面的部分已介绍 Azure 空间定位点的基础知识。</span><span class="sxs-lookup"><span data-stu-id="85d0e-189">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="85d0e-190">我们已使用一个立方体来表示并可视化了附有定位点的父游戏对象。</span><span class="sxs-lookup"><span data-stu-id="85d0e-190">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="85d0e-191">本部分将介绍如何通过将整个体验定位为 ParentAnchor 对象的子级，来定位该体验。</span><span class="sxs-lookup"><span data-stu-id="85d0e-191">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="85d0e-192">在“层次结构”窗口中选择“ParentAnchor”对象，然后在“检查器”窗口中配置“转换”组件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="85d0e-192">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="85d0e-193">将“比例 X”改为 1.1</span><span class="sxs-lookup"><span data-stu-id="85d0e-193">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="85d0e-194">将“比例 Z”改为 1.1</span><span class="sxs-lookup"><span data-stu-id="85d0e-194">Change **Scale Z** to 1.1</span></span>

![已选择、定位和缩放 ParentAnchor 对象的 Unity](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="85d0e-196">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件” > 探测器”文件夹，然后单击并将“RoverExplorer_Complete”预制件拖动到“层次结构”窗口中，以将其添加到场景中    ：</span><span class="sxs-lookup"><span data-stu-id="85d0e-196">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![选中新增的 RoverExplorer_Complete 预制件的 Unity](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="85d0e-198">在“层次结构”窗口中新添加的 RoverModule_Complete 对象仍处于选中状态的情况下，将其拖动到“ParentAnchor”对象上，使其成为 ParentAnchor 对象的子级：</span><span class="sxs-lookup"><span data-stu-id="85d0e-198">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![将 RoverExplorer_Complete 对象设置为 ParentAnchor 的子级的 Unity](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="85d0e-200">如果现在重建项目并将应用部署到设备，可以通过移动已调整大小的多维数据集来重新定位整个漫游者探测器。</span><span class="sxs-lookup"><span data-stu-id="85d0e-200">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="85d0e-201">有多种用户体验流可用于重新定位体验，包括使用重新定位对象（例如本教程中使用的立方体）、使用按钮切换体验周围的边界控件、使用定位和旋转调节器，等等。</span><span class="sxs-lookup"><span data-stu-id="85d0e-201">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounds control that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="85d0e-202">祝贺</span><span class="sxs-lookup"><span data-stu-id="85d0e-202">Congratulations</span></span>

<span data-ttu-id="85d0e-203">在本教程中，你已了解 Azure 空间定位点的基础知识。</span><span class="sxs-lookup"><span data-stu-id="85d0e-203">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="85d0e-204">本教程提供了多个按钮，让你了解启动和停止 Azure 空间定位点会话所需的各个步骤。</span><span class="sxs-lookup"><span data-stu-id="85d0e-204">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="85d0e-205">以及如何在单个设备上创建、上传和下载 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="85d0e-205">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="85d0e-206">下一教程将介绍如何将 Azure 定位点 ID 保存到 HoloLens 2 以供检索（甚至在重启应用后也可供检索），以及如何在多个设备之间转移定位点 ID，以实现空间对齐。</span><span class="sxs-lookup"><span data-stu-id="85d0e-206">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="85d0e-207">下一教程：3.保存、检索和共享 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="85d0e-207">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
