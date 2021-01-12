---
title: 将 Azure 空间定位点集成到共享体验中
description: 完成本课程可以了解如何使用 Azure 空间定位点来锚定共享的多用户 HoloLens 2 应用程序中的对象。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 多用户功能, Photon, MRTK, 混合现实工具包, UWP, Azure 空间定位点
ms.localizationpriority: high
ms.openlocfilehash: 665979d860a2507fbf6cc9b962f5449c7d7d12f2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010127"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="d1260-104">5.将 Azure 空间定位点集成到共享体验中</span><span class="sxs-lookup"><span data-stu-id="d1260-104">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="d1260-105">本教程介绍如何将 Azure 空间定位点 (ASA) 集成到共享体验中。</span><span class="sxs-lookup"><span data-stu-id="d1260-105">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="d1260-106">ASA 允许多台设备具有一个对物理环境的共同引用，从而使用户能够在其实际物理位置看到彼此，并看到同一位置中的共享体验。</span><span class="sxs-lookup"><span data-stu-id="d1260-106">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="d1260-107">目标</span><span class="sxs-lookup"><span data-stu-id="d1260-107">Objectives</span></span>

* <span data-ttu-id="d1260-108">将 ASA 集成到共享体验，以实现多设备空间配准</span><span class="sxs-lookup"><span data-stu-id="d1260-108">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="d1260-109">了解 ASA 在本地共享体验上下文中的基本工作原理</span><span class="sxs-lookup"><span data-stu-id="d1260-109">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="d1260-110">准备场景</span><span class="sxs-lookup"><span data-stu-id="d1260-110">Preparing the scene</span></span>

<span data-ttu-id="d1260-111">在“层次结构”窗口中，展开“SharedPlayground”对象，然后展开“TableAnchor”对象以公开其子对象：</span><span class="sxs-lookup"><span data-stu-id="d1260-111">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![展开了 SharedPlayground 和 TableAnchor 对象的 Unity](images/mr-learning-sharing/sharing-05-section1-step1-1.png)

<span data-ttu-id="d1260-113">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “预制件”文件夹，然后将“Buttons”预制件拖动到“TableAnchor”子对象上，以将其作为 TableAnchor 对象的子项添加到场景    ：</span><span class="sxs-lookup"><span data-stu-id="d1260-113">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab onto the **TableAnchor** child object to add it to your scene as a child of the TableAnchor object:</span></span>

![选中了新增的 Buttons 预制件的 Unity](images/mr-learning-sharing/sharing-05-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="d1260-115">配置按钮以操作场景</span><span class="sxs-lookup"><span data-stu-id="d1260-115">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="d1260-116">在本部分，你将配置一系列按钮事件，用于演示如何使用 Azure 空间定位点实现共享体验中的空间配准。</span><span class="sxs-lookup"><span data-stu-id="d1260-116">In this section, you will configure a series of button events demonstrating the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="d1260-117">在“层次结构”窗口中展开“Button”对象，然后选择名为“StartAzureSession”的第一个子按钮对象： </span><span class="sxs-lookup"><span data-stu-id="d1260-117">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:</span></span>

![选中了 StartAzureSession 按钮对象的 Unity](images/mr-learning-sharing/sharing-05-section2-step1-1.png)

<span data-ttu-id="d1260-119">在“检查器”窗口中，找到“可交互(脚本)”组件，并按如下所示配置 OnClick () 事件：</span><span class="sxs-lookup"><span data-stu-id="d1260-119">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="d1260-120">向“无(对象)”字段中分配“TableAnchor”对象 </span><span class="sxs-lookup"><span data-stu-id="d1260-120">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="d1260-121">从“无函数”下拉列表中，选择“AnchorModuleScript” > “StartAzureSession ()”函数  </span><span class="sxs-lookup"><span data-stu-id="d1260-121">From the **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![配置了 StartAzureSession 按钮 OnClick 事件的 Unity](images/mr-learning-sharing/sharing-05-section2-step1-2.png)

<span data-ttu-id="d1260-123">在“层次结构”窗口中，选择名为“CreateAzureAnchor”的第二个子按钮对象，然后在“检查器”窗口中，找到“可交互(脚本)”组件，并按如下所示配置 OnClick () 事件：</span><span class="sxs-lookup"><span data-stu-id="d1260-123">In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="d1260-124">向“无(对象)”字段中分配“TableAnchor”对象 </span><span class="sxs-lookup"><span data-stu-id="d1260-124">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="d1260-125">从“无函数”下拉列表中，选择“AnchorModuleScript” > “CreateAzureAnchor ()”函数  </span><span class="sxs-lookup"><span data-stu-id="d1260-125">From the **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="d1260-126">向出现的新“无(游戏对象)”字段中分配“TableAnchor”对象</span><span class="sxs-lookup"><span data-stu-id="d1260-126">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![配置了 CreateAzureAnchor 按钮 OnClick 事件的 Unity](images/mr-learning-sharing/sharing-05-section2-step1-3.png)

<span data-ttu-id="d1260-128">在“层次结构”窗口中，选择名为“ShareAzureAnchor”的第三个子按钮对象，然后在“检查器”窗口中，找到“可交互(脚本)”组件，并按如下所示配置 OnClick () 事件：</span><span class="sxs-lookup"><span data-stu-id="d1260-128">In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="d1260-129">向“无(对象)”字段中分配“TableAnchor”对象 </span><span class="sxs-lookup"><span data-stu-id="d1260-129">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="d1260-130">从“无函数”下拉列表中，选择“SharingModuleScript” > “ShareAzureAnchor ()”函数  </span><span class="sxs-lookup"><span data-stu-id="d1260-130">From the **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![配置了 ShareAzureAnchor 按钮 OnClick 事件的 Unity](images/mr-learning-sharing/sharing-05-section2-step1-4.png)

<span data-ttu-id="d1260-132">在“层次结构”窗口中，选择名为“GetAzureAnchor”的第四个子按钮对象，然后在“检查器”窗口中，找到“可交互(脚本)”组件，并按如下所示配置 OnClick () 事件  ：</span><span class="sxs-lookup"><span data-stu-id="d1260-132">In the Hierarchy window, select the fourth child button object named **GetAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="d1260-133">向“无(对象)”字段中分配“TableAnchor”对象 </span><span class="sxs-lookup"><span data-stu-id="d1260-133">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="d1260-134">从“无函数”下拉列表中，选择“SharingModuleScript” > “GetAzureAnchor ()”函数  </span><span class="sxs-lookup"><span data-stu-id="d1260-134">From the **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![配置了 GetAzureAnchor 按钮 OnClick 事件的 Unity](images/mr-learning-sharing/sharing-05-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="d1260-136">将场景连接到 Azure 资源</span><span class="sxs-lookup"><span data-stu-id="d1260-136">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="d1260-137">在“层次结构”窗口中，展开“SharedPlayground”对象，然后选择“TableAnchor”对象。</span><span class="sxs-lookup"><span data-stu-id="d1260-137">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span>

<span data-ttu-id="d1260-138">在“检查器”窗口中，找到“空间定位点管理器(脚本)”组件，并使用来自 Azure 空间定位点帐户（该帐户作为本教程系列[先决条件](mr-learning-sharing-01.md#prerequisites)一部分创建）的凭据配置“凭据”部分：</span><span class="sxs-lookup"><span data-stu-id="d1260-138">In the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-sharing-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="d1260-139">在“空间定位点帐户 ID”字段中，粘贴来自你的 Azure 空间定位点帐户的“帐户 ID”</span><span class="sxs-lookup"><span data-stu-id="d1260-139">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="d1260-140">在“空间定位点帐户密钥”字段中，粘贴来自你的 Azure 空间定位点帐户的主“访问密钥”或辅助“访问密钥”</span><span class="sxs-lookup"><span data-stu-id="d1260-140">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![配置了空间定位点管理器的 Unity](images/mr-learning-sharing/sharing-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="d1260-142">不要在场景中设置空间定位点帐户 ID 和密钥，而是针对整个项目设置它，这在有多个使用 ASA 的场景时会非常有利。</span><span class="sxs-lookup"><span data-stu-id="d1260-142">Instead of setting the Spatial Anchors Account ID and Key in the scene, you can set it for your entire project, this can be advantageous if you have multiple scenes using ASA.</span></span> <span data-ttu-id="d1260-143">为此，请在“项目”窗口中导航到“资产”>“AzureSpatialAnchors.SDK”>“资源”>“SpatialAnchorConfig”资产，然后在“检查器”窗口中设置这些值。</span><span class="sxs-lookup"><span data-stu-id="d1260-143">To do this, in the Project window, navigate to the Assets > AzureSpatialAnchors.SDK > Resources > **SpatialAnchorConfig** asset, then set the values in the Inspector window.</span></span>

<span data-ttu-id="d1260-144">在“层次结构”窗口中选择“TableAnchor”对象，然后在“检查器”窗口中，找到“定位点模块(脚本)”组件，并按如下所示进行配置 ：</span><span class="sxs-lookup"><span data-stu-id="d1260-144">In the Hierarchy window, select the **TableAnchor** object, then in the Inspector window, locate the **Anchor Module (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="d1260-145">在“公共共享 Pin”字段中，更改几个数字，使 Pin 成为项目的唯一 Pin</span><span class="sxs-lookup"><span data-stu-id="d1260-145">In the **Public Sharing Pin** field, change a few digits, so the pin becomes unique to your project</span></span>

![配置了定位点模块脚本的 Unity](images/mr-learning-sharing/sharing-05-section3-step1-2.png)

<span data-ttu-id="d1260-147">在仍选中“TableAnchor”对象的情况下，在“检查器”窗口中，确保已启用所有脚本组件 ：</span><span class="sxs-lookup"><span data-stu-id="d1260-147">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are **enabled**:</span></span>

* <span data-ttu-id="d1260-148">选中“空间定位点管理器(脚本)”组件旁边的复选框以启用该组件</span><span class="sxs-lookup"><span data-stu-id="d1260-148">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="d1260-149">选中“空间模块脚本(脚本)”组件旁边的复选框以启用该组件</span><span class="sxs-lookup"><span data-stu-id="d1260-149">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="d1260-150">选中“共享模块脚本(脚本)”组件旁边的复选框以启用该组件</span><span class="sxs-lookup"><span data-stu-id="d1260-150">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![启用了所有 TableAnchor 脚本组件的 Unity](images/mr-learning-sharing/sharing-05-section3-step1-3.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="d1260-152">尝试带有空间配准的体验</span><span class="sxs-lookup"><span data-stu-id="d1260-152">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="d1260-153">Azure 空间定位点不能在 Unity 中运行。</span><span class="sxs-lookup"><span data-stu-id="d1260-153">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="d1260-154">因此，若要测试 Azure 空间定位点功能，需将项目部署到至少两个设备。</span><span class="sxs-lookup"><span data-stu-id="d1260-154">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two devices.</span></span>

<span data-ttu-id="d1260-155">如果现在生成 Unity 项目并将其部署到两个设备，则可以通过共享 Azure 定位点 ID 在设备之间实现空间配准。</span><span class="sxs-lookup"><span data-stu-id="d1260-155">If you now build and deploy the Unity project to two devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="d1260-156">若要进行测试，可执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="d1260-156">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="d1260-157">在设备 1 上：启动应用（探测车浏览器已实例化并置于台面上）</span><span class="sxs-lookup"><span data-stu-id="d1260-157">On device 1: **Start the app** (the Rover Explorer is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="d1260-158">在设备 2 上：启动应用（这两个用户都看到带有探测车浏览器的台面，但是，该台面未出现在同一位置，用户头像未出现在用户所在的位置）</span><span class="sxs-lookup"><span data-stu-id="d1260-158">On device 2: **Start the app** (both users see the table with the Rover Explorer, but the table does not appear in the same place, and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="d1260-159">在设备 1 上：按“启动 Azure 会话”按钮</span><span class="sxs-lookup"><span data-stu-id="d1260-159">On device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="d1260-160">在设备 1 上：按“创建 Azure 定位点”按钮（在 TableAnchor 对象的位置创建定位点，并将定位点信息存储在 Azure 资源中）。</span><span class="sxs-lookup"><span data-stu-id="d1260-160">On device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="d1260-161">在设备 1 上：按“共享 Azure 定位点”按钮（与其他用户实时共享定位点 ID）</span><span class="sxs-lookup"><span data-stu-id="d1260-161">On device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="d1260-162">在设备 2 上：按“启动 Azure 会话”按钮</span><span class="sxs-lookup"><span data-stu-id="d1260-162">On device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="d1260-163">在设备 2 上：按“获取 Azure 定位点”按钮（连接到 Azure 资源以检索共享定位点 ID 的定位点信息，然后将 TableAnchor 对象移到通过设备 1 创建定位点的位置）</span><span class="sxs-lookup"><span data-stu-id="d1260-163">On device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the device 1)</span></span>

> [!TIP]
> <span data-ttu-id="d1260-164">如果你无权访问两个 HoloLens 设备，则可以按照[为移动设备生成 Azure 空间定位点](mr-learning-asa-05.md)操作，将项目部署到移动设备。</span><span class="sxs-lookup"><span data-stu-id="d1260-164">If you don't have access to two HoloLens devices, you may follow the [Building Azure Spatial Anchors for mobile devices](mr-learning-asa-05.md) to deploy the project to your mobile device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d1260-165">祝贺</span><span class="sxs-lookup"><span data-stu-id="d1260-165">Congratulations</span></span>

<span data-ttu-id="d1260-166">在本教程中，你已了解如何集成 Azure 中强大的空间定位点功能，以在共享体验中为设备实现空间配准。</span><span class="sxs-lookup"><span data-stu-id="d1260-166">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span>

<span data-ttu-id="d1260-167">这也是此教程系列的总结。在此教程系列中，你已学会了如何设置 Photon 帐户、创建 PUN 应用、将 PUN 集成到 Unity 项目中、配置用户头像和共享的对象，并最终使用 Azure 空间定位点来为多个参与者实现空间配准。</span><span class="sxs-lookup"><span data-stu-id="d1260-167">This also concludes this tutorial series where you learned how to set up a Photon account, create a PUN app, integrate PUN into the Unity project, configure user avatars and shared objects, and finally align multiple participants using Azure Spatial Anchors.</span></span>
