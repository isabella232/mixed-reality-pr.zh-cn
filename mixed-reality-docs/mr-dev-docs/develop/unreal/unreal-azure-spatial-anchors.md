---
title: Unreal 中的 Azure 空间定位点
description: 概要讲解如何在 Unreal 引擎中创建 Azure 空间定位点。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, azure 开发, 空间定位点, 混合现实, 开发, 功能, 新项目, 仿真器, 文档, 指南, 全息影像, 游戏开发, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: 18ec9db03341ad4fc6a5c10ea6f8fdd38c61c537
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2020
ms.locfileid: "96926024"
---
# <a name="azure-spatial-anchors-in-unreal"></a><span data-ttu-id="cc86a-104">Unreal 中的 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="cc86a-104">Azure Spatial Anchors in Unreal</span></span>

<span data-ttu-id="cc86a-105">Azure 空间定位点是一项 Microsoft Mixed Reality 服务，增强现实设备可用它来发现、共享和保存现实世界中的定位点。</span><span class="sxs-lookup"><span data-stu-id="cc86a-105">Azure Spatial Anchors is a Microsoft Mixed Reality service, allowing augmented reality devices to discover, share, and persist anchor points in the physical world.</span></span> <span data-ttu-id="cc86a-106">下列文档介绍了如何将 Azure 空间定位点服务集成到 Unreal 项目中。</span><span class="sxs-lookup"><span data-stu-id="cc86a-106">Documentation below provides instructions for integrating the Azure Spatial Anchors service into an Unreal project.</span></span> <span data-ttu-id="cc86a-107">若要了解详细信息，请查看 [Azure 空间定位点服务](https://azure.microsoft.com/services/spatial-anchors/)。</span><span class="sxs-lookup"><span data-stu-id="cc86a-107">If you're looking for more information, check out the [Azure Spatial Anchors service](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

> [!NOTE]
> <span data-ttu-id="cc86a-108">Unreal Engine 4.26 现具有适合 ARKit 和 ARCore 支持的插件，供你在面向 iOS 或 Android 时使用。</span><span class="sxs-lookup"><span data-stu-id="cc86a-108">Unreal Engine 4.26 now has plugins for ARKit and ARCore support if you're targeting iOS or Android.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cc86a-109">本地定位点存储在设备上，而 Azure 空间定位点存储在云中。</span><span class="sxs-lookup"><span data-stu-id="cc86a-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="cc86a-110">如果你想要在设备上本地存储定位点，我们有一个[本地空间定位点](unreal-spatial-anchors.md)文档可指导你完成整个过程。</span><span class="sxs-lookup"><span data-stu-id="cc86a-110">If you're looking to store your anchors locally on a device, we have a [Local Spatial Anchors](unreal-spatial-anchors.md) document that can walk you through the process.</span></span> <span data-ttu-id="cc86a-111">请注意，你可在同一项目中使用本地定位点和 Azure 定位点，不会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="cc86a-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cc86a-112">必备条件</span><span class="sxs-lookup"><span data-stu-id="cc86a-112">Prerequisites</span></span>

<span data-ttu-id="cc86a-113">要完成本指南，请确保：</span><span class="sxs-lookup"><span data-stu-id="cc86a-113">To complete this guide, make sure you have:</span></span>

- <span data-ttu-id="cc86a-114">已安装 [Unreal 4.25](https://www.unrealengine.com/get-now) 或更高版本</span><span class="sxs-lookup"><span data-stu-id="cc86a-114">Installed [Unreal version 4.25](https://www.unrealengine.com/get-now) or later</span></span>
- <span data-ttu-id="cc86a-115">已在 Unreal 中设置 [HoloLens 2 项目](tutorials/unreal-uxt-ch1.md)</span><span class="sxs-lookup"><span data-stu-id="cc86a-115">A [HoloLens 2 project](tutorials/unreal-uxt-ch1.md) setup in Unreal</span></span> 
- <span data-ttu-id="cc86a-116">已仔细阅读 [Azure 空间定位点概述](https://docs.microsoft.com/azure/spatial-anchors/overview)</span><span class="sxs-lookup"><span data-stu-id="cc86a-116">Read through the [Azure Spatial Anchors overview](https://docs.microsoft.com/azure/spatial-anchors/overview)</span></span>
- <span data-ttu-id="cc86a-117">具备 C++ 和 Unreal 的基础知识</span><span class="sxs-lookup"><span data-stu-id="cc86a-117">Basic knowledge on C++ and Unreal</span></span>

## <a name="getting-azure-spatial-anchors-account-info"></a><span data-ttu-id="cc86a-118">获取 Azure 空间定位点帐户信息</span><span class="sxs-lookup"><span data-stu-id="cc86a-118">Getting Azure Spatial Anchors account info</span></span>

<span data-ttu-id="cc86a-119">在项目中使用 Azure 空间定位点之前，你需要：</span><span class="sxs-lookup"><span data-stu-id="cc86a-119">Before using Azure Spatial Anchors in your project, you need to:</span></span>
* <span data-ttu-id="cc86a-120">[创建空间定位点资源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource)并复制下面列出的帐户字段。</span><span class="sxs-lookup"><span data-stu-id="cc86a-120">[Create a spatial anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) and copy the account fields listed below.</span></span> <span data-ttu-id="cc86a-121">这些值用于向你的应用程序的帐户验证用户的身份：</span><span class="sxs-lookup"><span data-stu-id="cc86a-121">These values are used to authenticate users with your application's account:</span></span>
    * <span data-ttu-id="cc86a-122">**帐户 ID**</span><span class="sxs-lookup"><span data-stu-id="cc86a-122">**Account ID**</span></span>
    * <span data-ttu-id="cc86a-123">**帐户密钥**</span><span class="sxs-lookup"><span data-stu-id="cc86a-123">**Account Key**</span></span>

<span data-ttu-id="cc86a-124">有关详细信息，请查看 [Azure 空间定位点身份验证](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp)文档。</span><span class="sxs-lookup"><span data-stu-id="cc86a-124">Check out the [Azure Spatial Anchors authentication](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) docs for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="cc86a-125">Unreal 4.25 中的 Azure 空间定位点不支持 Azure AD 身份验证令牌，但今后的版本中将提供对该功能的支持。</span><span class="sxs-lookup"><span data-stu-id="cc86a-125">Azure Spatial Anchors in Unreal 4.25 does not support Azure AD authentication tokens, but support for this functionality will be coming in a later release.</span></span>

## <a name="adding-azure-spatial-anchors-plugins"></a><span data-ttu-id="cc86a-126">添加 Azure 空间定位点插件</span><span class="sxs-lookup"><span data-stu-id="cc86a-126">Adding Azure Spatial Anchors plugins</span></span>

<span data-ttu-id="cc86a-127">通过以下方法在 Unreal 编辑器中启用 Azure 空间定位点插件：</span><span class="sxs-lookup"><span data-stu-id="cc86a-127">Enable the Azure Spatial Anchors plugins in the Unreal editor by:</span></span>
1. <span data-ttu-id="cc86a-128">单击“编辑”>“插件”，然后搜索“AzureSpatialAnchors”和“AzureSpatialAnchorsForWMR”  。</span><span class="sxs-lookup"><span data-stu-id="cc86a-128">Clicking **Edit > Plugins** and searching for **AzureSpatialAnchors** and **AzureSpatialAnchorsForWMR**.</span></span>
2. <span data-ttu-id="cc86a-129">选中这两个插件中的“启用”复选框，允许访问你的应用程序中的 Azure 空间定位点蓝图库。</span><span class="sxs-lookup"><span data-stu-id="cc86a-129">Select the **Enabled** checkbox in both plugins to allow access to the Azure Spatial Anchors blueprint libraries in your application.</span></span>

![Unreal 编辑器中空间定位点插件的屏幕截图](images/asa-unreal/unreal-spatial-anchors-img-01.png)

<span data-ttu-id="cc86a-131">完成后，重启 Unreal 编辑器，使插件更改生效。</span><span class="sxs-lookup"><span data-stu-id="cc86a-131">Once that's done, restart the Unreal Editor for the plugin changes to take effect.</span></span> <span data-ttu-id="cc86a-132">该项目现就可使用 Azure 空间定位点了。</span><span class="sxs-lookup"><span data-stu-id="cc86a-132">The project is now ready to use Azure Spatial Anchors.</span></span>

## <a name="starting-a-spatial-anchors-session"></a><span data-ttu-id="cc86a-133">启动空间定位点会话</span><span class="sxs-lookup"><span data-stu-id="cc86a-133">Starting a Spatial Anchors session</span></span>

<span data-ttu-id="cc86a-134">通过 Azure 空间定位点会话，客户端应用程序可与 Azure 空间定位点服务通信。</span><span class="sxs-lookup"><span data-stu-id="cc86a-134">An Azure Spatial Anchors session allows client applications to communicate with the Azure Spatial Anchors service.</span></span> <span data-ttu-id="cc86a-135">你需要创建并启动 Azure 空间定位点会话才能创建、保存和共享 Azure 空间定位点：</span><span class="sxs-lookup"><span data-stu-id="cc86a-135">You'll need to create and start an Azure Spatial Anchors session to create, persist, and share Azure Spatial Anchors:</span></span>

1. <span data-ttu-id="cc86a-136">打开你在应用程序中使用的 Pawn 的蓝图。</span><span class="sxs-lookup"><span data-stu-id="cc86a-136">Open the blueprint for the Pawn you're using in the application.</span></span>
2. <span data-ttu-id="cc86a-137">添加两个字符串变量分别用于帐户 ID 和帐户密钥，然后从 Azure 空间定位点帐户分配相应的值，对会话进行身份验证 。</span><span class="sxs-lookup"><span data-stu-id="cc86a-137">Add two string variables for the **Account ID** and **Account Key**, then assign the corresponding values from your Azure Spatial Anchors account to authenticate the session.</span></span>

![详细信息面板的屏幕截图，其中突出显示了 Azure 空间定位点帐户 ID、密钥和变量类型](images/asa-unreal/unreal-spatial-anchors-img-02.png)

<span data-ttu-id="cc86a-139">通过以下方式启动 Azure 空间定位点会话：</span><span class="sxs-lookup"><span data-stu-id="cc86a-139">Start an Azure Spatial Anchors session by:</span></span>
1. <span data-ttu-id="cc86a-140">检查 AR 会话是否正在 HoloLens 应用程序中运行，因为在 AR 会话运行之后，才能启动 Azure 空间定位点会话。</span><span class="sxs-lookup"><span data-stu-id="cc86a-140">Checking that an **AR Session** is running in the HoloLens application, as the Azure Spatial Anchors session can't start until an AR Session is running.</span></span> <span data-ttu-id="cc86a-141">如果未设置，请[创建 AR 会话资产](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)。</span><span class="sxs-lookup"><span data-stu-id="cc86a-141">If you don't have one setup, [create an AR Session asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>
2. <span data-ttu-id="cc86a-142">添加名为“启动 Azure 空间定位点会话”的自定义事件并对其进行配置，如下面的屏幕截图所示。</span><span class="sxs-lookup"><span data-stu-id="cc86a-142">Adding the **Start Azure Spatial Anchors Session** custom event and configure it as shown in the screenshot below.</span></span>
    * <span data-ttu-id="cc86a-143">默认情况下，创建会话不会启动会话，这使得你可配置会话来向 Azure 空间定位点服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="cc86a-143">Creating a session doesn't start the session by default, which allows you to configure the session for authentication with the Azure Spatial Anchors service.</span></span>

![启动 Azure 空间定位点会话自定义事件的蓝图](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. <span data-ttu-id="cc86a-145">配置 Azure 空间定位点会话，以提供帐户 ID 和帐户密钥 。</span><span class="sxs-lookup"><span data-stu-id="cc86a-145">Configure the Azure Spatial Anchors session to provide the **Account ID** and **Account Key**.</span></span>

![添加了帐户 ID 和密钥的 config session 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. <span data-ttu-id="cc86a-147">启动 Azure 空间定位点会话，让应用程序能够创建和查找 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="cc86a-147">Start the Azure Spatial Anchors session, allowing the application to create and locate Azure Spatial Anchors.</span></span>

![Azure 空间定位点 session start 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-05.png)

<span data-ttu-id="cc86a-149">不再使用该服务时，最好清理 Event Graph 蓝图中的 Azure 空间定位点资源：</span><span class="sxs-lookup"><span data-stu-id="cc86a-149">It's good practice to clean up Azure Spatial Anchors resources in your Event Graph blueprint when you're no longer using the service:</span></span>

1. <span data-ttu-id="cc86a-150">停止 Azure 空间定位点会话。</span><span class="sxs-lookup"><span data-stu-id="cc86a-150">Stop the Azure Spatial Anchors session.</span></span> <span data-ttu-id="cc86a-151">该会话将不再运行，但它关联的资源仍将保留在 Azure 空间定位点插件中。</span><span class="sxs-lookup"><span data-stu-id="cc86a-151">The session will no longer be running, but its associated resources will still exist in the Azure Spatial Anchors plugin.</span></span>

![stop azure spatial anchors sessions custom event and stop session 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. <span data-ttu-id="cc86a-153">销毁 Azure 空间定位点会话，来清理 Azure 空间定位点插件仍然知晓的所有 Azure 空间定位点会话资源。</span><span class="sxs-lookup"><span data-stu-id="cc86a-153">Destroy the Azure Spatial Anchors session to clean up any Azure Spatial Anchors session resources still known to the Azure Spatial Anchors plugin.</span></span>

![destroy session 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-07.png)

<span data-ttu-id="cc86a-155">你的 Event Graph 蓝图应该会与以下屏幕截图类似：</span><span class="sxs-lookup"><span data-stu-id="cc86a-155">Your Event Graph blueprint should look like the screenshot below:</span></span>

![Azure 空间定位点会话设置的完整事件图的蓝图](images/asa-unreal/unreal-spatial-anchors-img-08.png)

## <a name="creating-an-anchor"></a><span data-ttu-id="cc86a-157">创建定位点</span><span class="sxs-lookup"><span data-stu-id="cc86a-157">Creating an anchor</span></span>

<span data-ttu-id="cc86a-158">Azure 空间定位点是现实世界中的姿势在增强现实应用空间中的表示形式，它将增强现实内容与物理位置挂钩。</span><span class="sxs-lookup"><span data-stu-id="cc86a-158">An Azure Spatial Anchor represents a physical world pose in the augmented reality application space, which locks augmented reality content to physical locations.</span></span> <span data-ttu-id="cc86a-159">Azure 空间定位点也可在不同的用户之间共享。</span><span class="sxs-lookup"><span data-stu-id="cc86a-159">Azure Spatial Anchors can also be shared among different users.</span></span> <span data-ttu-id="cc86a-160">通过这种共享，在不同设备上绘制的增强现实内容可放置到现实世界中的同一个位置。</span><span class="sxs-lookup"><span data-stu-id="cc86a-160">This sharing allows augmented reality content drawn on different devices to be positioned in the same location in the physical world.</span></span> 

<span data-ttu-id="cc86a-161">若要创建新的 Azure 空间定位点：</span><span class="sxs-lookup"><span data-stu-id="cc86a-161">To create a new Azure Spatial Anchor:</span></span>
1. <span data-ttu-id="cc86a-162">检查 Azure 空间定位点会话是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="cc86a-162">Check that an Azure Spatial Anchors session is running.</span></span> <span data-ttu-id="cc86a-163">如果 Azure 空间定位点会话都未运行，则应用程序无法创建或保留 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="cc86a-163">The application can't create or persist an Azure Spatial Anchor when no Azure Spatial Anchors session is running.</span></span>

![创建 Azure 空间定位点自定义事件的蓝图](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. <span data-ttu-id="cc86a-165">创建或获取 Unreal [场景组件](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)（该组件应保留其所在位置）。</span><span class="sxs-lookup"><span data-stu-id="cc86a-165">Create or obtain an Unreal **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** that should have its location persisted.</span></span> 
    * <span data-ttu-id="cc86a-166">在下图中，“场景组件需要定位点”组件用作变量。</span><span class="sxs-lookup"><span data-stu-id="cc86a-166">In the below image, the **Scene Component Needing Anchor** component is used as a variable.</span></span> <span data-ttu-id="cc86a-167">要为 [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) 和 Azure 空间定位点建立应用世界坐标变换，需要使用 Unreal 场景组件。</span><span class="sxs-lookup"><span data-stu-id="cc86a-167">An Unreal Scene Component is needed to establish an application world transform for an [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) and Azure Spatial Anchor.</span></span>

![使用场景组件创建 Azure 空间定位点自定义事件的蓝图](images/asa-unreal/unreal-spatial-anchors-img-10.png)

<span data-ttu-id="cc86a-169">若要为 Unreal 场景组件构造并保存 Azure 空间定位点：</span><span class="sxs-lookup"><span data-stu-id="cc86a-169">To construct and save an Azure Spatial Anchor for an Unreal Scene Component:</span></span>
1. <span data-ttu-id="cc86a-170">为 Unreal 场景组件调用 [Pin 组件](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html)，并将场景组件的世界坐标变换指定为用于 AR Pin 的世界坐标变换。</span><span class="sxs-lookup"><span data-stu-id="cc86a-170">Call the [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) for the Unreal Scene Component and specify the Scene Component's **World Transform** as the World Transform used for the AR Pin.</span></span>
    * <span data-ttu-id="cc86a-171">Unreal 使用 AR Pin 来跟踪应用空间中的 AR 点，AR Pin 用于创建 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="cc86a-171">Unreal tracks AR points in the application space using AR Pins, which are used to create an Azure Spatial Anchor.</span></span> <span data-ttu-id="cc86a-172">在 Unreal 中，AR Pin 与 HoloLens 上的 SpatialAnchor 类似。</span><span class="sxs-lookup"><span data-stu-id="cc86a-172">In Unreal, an AR Pin is analogous to a SpatialAnchor on HoloLens.</span></span>

![连接到 pin component 函数的场景组件的蓝图](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. <span data-ttu-id="cc86a-174">使用新创建的 AR Pin 调用“创建云定位点”。</span><span class="sxs-lookup"><span data-stu-id="cc86a-174">Call **Create Cloud Anchor** using the newly created AR Pin.</span></span>
    * <span data-ttu-id="cc86a-175">“创建云定位点”会在本地创建 Azure 空间定位点，但不在 Azure 空间定位点服务中进行创建。</span><span class="sxs-lookup"><span data-stu-id="cc86a-175">Create Cloud Anchor creates an Azure Spatial Anchor locally but not in the Azure Spatial Anchor service.</span></span> <span data-ttu-id="cc86a-176">在使用服务创建 Azure 空间定位点之前，可设置 Azure 空间定位点的参数（例如到期日期）。</span><span class="sxs-lookup"><span data-stu-id="cc86a-176">Parameters for the Azure Spatial Anchor, such as an expiration date, can be set before creating the Azure Spatial Anchor with the service.</span></span>

![连接到返回 ARPin 的 create cloud anchor 函数的 pin component 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. <span data-ttu-id="cc86a-178">设置 Azure 空间定位点的到期日期。</span><span class="sxs-lookup"><span data-stu-id="cc86a-178">Set the Azure Spatial Anchor expiration.</span></span> <span data-ttu-id="cc86a-179">通过此函数的生存期参数，开发人员可以秒为单位指定服务应维护定位点多长时间。</span><span class="sxs-lookup"><span data-stu-id="cc86a-179">This function's Lifetime parameter allows the developer to specify in seconds how long the anchor should be maintained by the service.</span></span>
    * <span data-ttu-id="cc86a-180">例如，一周有效期的值的计算方式为：60 秒 x 60 分钟 x 24 小时 x 7 天 = 604,800 秒。</span><span class="sxs-lookup"><span data-stu-id="cc86a-180">For example, a week long expiration would take a value of 60 seconds x 60 minutes x 24 hours x seven days = 604,800 seconds.</span></span>

![连接到 set expiration 函数（其生存期值设置为 604,800 秒）的云定位点的蓝图](images/asa-unreal/unreal-spatial-anchors-img-13.png)

<span data-ttu-id="cc86a-182">设置定位点参数后，将定位点声明为已可供保存。</span><span class="sxs-lookup"><span data-stu-id="cc86a-182">After setting anchor parameters, declare the anchor as ready to save.</span></span> <span data-ttu-id="cc86a-183">在下例中，新创建的 Azure 空间定位点会被添加到一组需要保存的 Azure 空间定位点中。</span><span class="sxs-lookup"><span data-stu-id="cc86a-183">In the example below, the newly created Azure Spatial Anchor is added to a set of Azure Spatial Anchors needing saving.</span></span> <span data-ttu-id="cc86a-184">这组定位点被声明为 Pawn 蓝图的变量。</span><span class="sxs-lookup"><span data-stu-id="cc86a-184">This set is declared as a variable for the Pawn blueprint.</span></span>

![准备保存在 set 变量中的定位点蓝图](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a><span data-ttu-id="cc86a-186">保存定位点</span><span class="sxs-lookup"><span data-stu-id="cc86a-186">Saving an Anchor</span></span>

<span data-ttu-id="cc86a-187">在用参数配置 Azure 空间定位点之后，调用“保存云定位点”。</span><span class="sxs-lookup"><span data-stu-id="cc86a-187">After configuring the Azure Spatial Anchor with your parameters, call **Save Cloud Anchor**.</span></span> <span data-ttu-id="cc86a-188">“保存云定位点”会将定位点声明指向 Azure 空间定位点服务。</span><span class="sxs-lookup"><span data-stu-id="cc86a-188">Save Cloud Anchor declares the anchor to the Azure Spatial Anchors service.</span></span> <span data-ttu-id="cc86a-189">“保存云定位点”调用成功后，Azure 空间定位点可供 Azure 空间定位点服务的其他用户使用。</span><span class="sxs-lookup"><span data-stu-id="cc86a-189">When the call to Save Cloud Anchor succeeds, the Azure Spatial Anchor is available to other users of the Azure Spatial Anchor service.</span></span>  

![正在调用的 save cloud anchor 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> <span data-ttu-id="cc86a-191">“保存云定位点”是一个异步函数，只能在游戏线程事件（例如 EventTick）上调用。</span><span class="sxs-lookup"><span data-stu-id="cc86a-191">Save Cloud Anchor is an asynchronous function and can only be called on a game thread event such as **EventTick**.</span></span> <span data-ttu-id="cc86a-192">在自定义蓝图函数中，“保存云定位点”可能不会显示为可用的蓝图函数。</span><span class="sxs-lookup"><span data-stu-id="cc86a-192">Save Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="cc86a-193">但是，应该能在 Pawn Event Graph 蓝图编辑器中使用它。</span><span class="sxs-lookup"><span data-stu-id="cc86a-193">However, it should be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="cc86a-194">在下例中，Azure 空间定位点在输入事件回调期间存储在一个集合中。</span><span class="sxs-lookup"><span data-stu-id="cc86a-194">In the example below, the Azure Spatial Anchor is stored in a set during an input event callback.</span></span> <span data-ttu-id="cc86a-195">随后，在出现 EventTick 时保存定位点。</span><span class="sxs-lookup"><span data-stu-id="cc86a-195">The anchor is then saved on the EventTick.</span></span> <span data-ttu-id="cc86a-196">保存 Azure 空间定位点可能需要多次尝试，具体取决于 Azure 空间定位点会话创建的空间数据量。</span><span class="sxs-lookup"><span data-stu-id="cc86a-196">Saving an Azure Spatial Anchor may take multiple attempts depending on the amount of spatial data that your Azure Spatial Anchors session has created.</span></span> <span data-ttu-id="cc86a-197">这就是检查保存调用是否成功的原因。</span><span class="sxs-lookup"><span data-stu-id="cc86a-197">That's why it's a good idea to check whether the save call succeeded.</span></span>

<span data-ttu-id="cc86a-198">如果定位点没有保存，请重新将它添加到仍然需要保存的定位点集中。</span><span class="sxs-lookup"><span data-stu-id="cc86a-198">If the anchor doesn't save, readd it to the set of anchors still needing to be saved.</span></span> <span data-ttu-id="cc86a-199">之后的 EventTick 将继续尝试保存定位点，直到它成功存储。</span><span class="sxs-lookup"><span data-stu-id="cc86a-199">Future EventTicks will keep trying to save the anchor until it's successfully stored.</span></span>

![在 set 变量中再次保存未保存定位点的蓝图](images/asa-unreal/unreal-spatial-anchors-img-16.png)

<span data-ttu-id="cc86a-201">保存定位点后，AR Pin 的变换用作将内容置于应用中的引用坐标变换。</span><span class="sxs-lookup"><span data-stu-id="cc86a-201">Once the anchor saves, the AR Pins' transform acts as a reference transform for placing content in your app.</span></span> <span data-ttu-id="cc86a-202">其他用户可检测此定位点，请针对现实世界中的不同设备将 AR 内容对齐。</span><span class="sxs-lookup"><span data-stu-id="cc86a-202">Other users can detect this anchor and align AR content for different devices in the physical world.</span></span>

## <a name="deleting-an-anchor"></a><span data-ttu-id="cc86a-203">删除定位点</span><span class="sxs-lookup"><span data-stu-id="cc86a-203">Deleting an Anchor</span></span>

<span data-ttu-id="cc86a-204">可通过调用“删除云定位点”，从 Azure 空间定位点服务中删除定位点。</span><span class="sxs-lookup"><span data-stu-id="cc86a-204">You can delete anchors from the Azure Spatial Anchor service by calling **Delete Cloud Anchor**.</span></span>

![正在调用的 delete cloud anchor 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> <span data-ttu-id="cc86a-206">“删除云定位点”是一个潜在函数，只能在游戏线程事件（例如 EventTick）上调用。</span><span class="sxs-lookup"><span data-stu-id="cc86a-206">Delete Cloud Anchor is a latent function and can only be called on a game thread event, such as EventTick.</span></span> <span data-ttu-id="cc86a-207">在自定义蓝图函数中，“删除云定位点”可能不会显示为可用的蓝图函数。</span><span class="sxs-lookup"><span data-stu-id="cc86a-207">Delete Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="cc86a-208">但是，应该能够在 Pawn Event Graph 蓝图编辑器中使用它。</span><span class="sxs-lookup"><span data-stu-id="cc86a-208">It should however be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="cc86a-209">在下例中，定位点被标记为要在发生自定义输入事件时删除。</span><span class="sxs-lookup"><span data-stu-id="cc86a-209">In the example below, the anchor is flagged for deletion on a custom input event.</span></span> <span data-ttu-id="cc86a-210">系统随后在发生 EventTick 时尝试删除。</span><span class="sxs-lookup"><span data-stu-id="cc86a-210">The deletion is then attempted on the EventTick.</span></span> <span data-ttu-id="cc86a-211">如果定位点删除失败，请将 Azure 空间定位点添加到已标记为要删除且将在发生后续 EventTick 时重试的定位点集中。</span><span class="sxs-lookup"><span data-stu-id="cc86a-211">If the anchor deletion fails, add the Azure Spatial Anchor to the set of anchors flagged for deletion and tries again on later EventTicks.</span></span>

<span data-ttu-id="cc86a-212">你的 Event Graph 蓝图现在应该会与以下屏幕截图类似：</span><span class="sxs-lookup"><span data-stu-id="cc86a-212">Your Event Graph blueprint should now look like the screenshot below:</span></span>

![用于处理云定位点的完整事件图的蓝图](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a><span data-ttu-id="cc86a-214">查找预先存在的定位点</span><span class="sxs-lookup"><span data-stu-id="cc86a-214">Locating pre-existing anchors</span></span>

<span data-ttu-id="cc86a-215">对等方可以使用 Azure 空间定位点服务创建现有定位点：</span><span class="sxs-lookup"><span data-stu-id="cc86a-215">Existing anchors can be created by peers with the Azure Spatial Anchors service:</span></span>

1. <span data-ttu-id="cc86a-216">获取要检测的定位点的 Azure 空间定位点标识符。</span><span class="sxs-lookup"><span data-stu-id="cc86a-216">Obtain an Azure Spatial Anchor identifier for the anchor that you would like to detect.</span></span>
    * <span data-ttu-id="cc86a-217">可为在之前的 Azure 空间定位点会话中由同一设备创建的定位点获取定位点标识符。</span><span class="sxs-lookup"><span data-stu-id="cc86a-217">An anchor identifier can be obtained for an anchor created by the same device in a previous Azure Spatial Anchors session.</span></span> <span data-ttu-id="cc86a-218">它还可由与 Azure 空间定位点服务交互的对等设备进行创建和共享。</span><span class="sxs-lookup"><span data-stu-id="cc86a-218">It can also be created and shared by peer devices interacting with the Azure Spatial Anchors service.</span></span>

![使用 get azure cloud identifier 函数的存储 Azure 空间定位点标识符自定义事件的蓝图](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. <span data-ttu-id="cc86a-220">将 AzureSpatialAnchorsEvent 组件添加到 Pawn 蓝图中。</span><span class="sxs-lookup"><span data-stu-id="cc86a-220">Add an **AzureSpatialAnchorsEvent** component to your Pawn blueprint.</span></span>
    * <span data-ttu-id="cc86a-221">通过此组件可订阅各种 Azure 空间定位点事件，例如在查找 Azure 空间定位点时调用的事件。</span><span class="sxs-lookup"><span data-stu-id="cc86a-221">This component allows you to subscribe to various Azure Spatial Anchors events, such as events called when Azure Spatial Anchors are located.</span></span>

![屏幕截图显示了蓝图编辑器中打开的 BP_Pawn，其中打开了组件和详细信息面板](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. <span data-ttu-id="cc86a-223">订阅 AzureSpatialAnchorsEvent 组件的“ASAAnchor 已找到委托” 。</span><span class="sxs-lookup"><span data-stu-id="cc86a-223">Subscribe to the **ASAAnchor Located Delegate** for the **AzureSpatialAnchorsEvent** component.</span></span>
    * <span data-ttu-id="cc86a-224">通过委托，应用程序可知道已找到与 Azure 空间定位点帐户关联的新的定位点。</span><span class="sxs-lookup"><span data-stu-id="cc86a-224">The delegate lets the application know when new anchors associated with the Azure Spatial Anchors account have been located.</span></span>
    * <span data-ttu-id="cc86a-225">默认情况下，通过事件回调，由使用 Azure 空间定位点会话的对等方创建的 Azure 空间定位点不会创建 AR Pin。</span><span class="sxs-lookup"><span data-stu-id="cc86a-225">With the event callback, Azure Spatial Anchors created by peers using the Azure Spatial Anchors session won't have AR Pins created by default.</span></span> <span data-ttu-id="cc86a-226">要为检测到的 Azure 空间定位点创建 AR Pin，开发人员可调用“围绕 Azure 云空间定位点创建 ARPin”。</span><span class="sxs-lookup"><span data-stu-id="cc86a-226">To create an AR Pin for the detected Azure Spatial Anchor, developers can call **Create ARPin Around Azure Cloud Spatial Anchor**.</span></span>

![连接到 ASAAnchor 所找到委托的开始播放事件的蓝图](images/asa-unreal/unreal-spatial-anchors-img-20.png)

<span data-ttu-id="cc86a-228">若要查找由使用 Azure 空间定位点服务的 Peer 创建的 Azure 空间定位点，应用程序必须创建“Azure 空间定位点观察程序”：</span><span class="sxs-lookup"><span data-stu-id="cc86a-228">To locate Azure Spatial Anchors created by peers using the Azure Spatial Anchor service, the application will have to create an **Azure Spatial Anchors Watcher**:</span></span>
1. <span data-ttu-id="cc86a-229">检查 Azure 空间定位点会话是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="cc86a-229">Check that an Azure Spatial Anchors session is running.</span></span>
2. <span data-ttu-id="cc86a-230">创建 AzureSpatialAnchorsLocateCriteria。</span><span class="sxs-lookup"><span data-stu-id="cc86a-230">Create an **AzureSpatialAnchorsLocateCriteria**.</span></span>
    * <span data-ttu-id="cc86a-231">可指定不同的位置参数，例如与用户的距离或与另一定位点的距离。</span><span class="sxs-lookup"><span data-stu-id="cc86a-231">You can specify various location parameters like distance from the user or distance from another anchor.</span></span>
3. <span data-ttu-id="cc86a-232">在 AzureSpatialAnchorsLocateCritieria 中声明所需的 Azure 空间定位点标识符。</span><span class="sxs-lookup"><span data-stu-id="cc86a-232">Declare the Azure Spatial Anchor identifier you're looking for in the **AzureSpatialAnchorsLocateCritieria**.</span></span>
4. <span data-ttu-id="cc86a-233">调用“创建观察程序”。</span><span class="sxs-lookup"><span data-stu-id="cc86a-233">Call **Create Watcher**.</span></span>

![启动 Azure 空间定位点观察程序自定义事件的蓝图](images/asa-unreal/unreal-spatial-anchors-img-21.png)

<span data-ttu-id="cc86a-235">应用程序现开始查找 Azure 空间定位点服务已知的 Azure 空间定位点，这意味着用户可找到由其对等方创建的 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="cc86a-235">The application now begins looking for Azure Spatial Anchors known to the Azure Spatial Anchors service, meaning that users can locate Azure Spatial Anchors created by their peers.</span></span>

<span data-ttu-id="cc86a-236">找到 Azure 空间定位点后，调用“停止观察程序”来停止 Azure 空间定位点观察程序，并清理观察程序资源。</span><span class="sxs-lookup"><span data-stu-id="cc86a-236">After locating the Azure Spatial Anchor, call **Stop Watcher** to stop the Azure Spatial Anchors Watcher and clean up watcher resources.</span></span>

![正在调用的 stop watcher 函数的蓝图](images/asa-unreal/unreal-spatial-anchors-img-22.png)

<span data-ttu-id="cc86a-238">最终的 Event Graph 蓝图现在应该会与以下屏幕截图类似：</span><span class="sxs-lookup"><span data-stu-id="cc86a-238">Your final Event Graph blueprint should now look like the screenshot below:</span></span>

![用于处理定位点委托事件的完整事件图的蓝图](images/asa-unreal/unreal-spatial-anchors-img-23.png)

## <a name="next-development-checkpoint"></a><span data-ttu-id="cc86a-240">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="cc86a-240">Next Development Checkpoint</span></span>

<span data-ttu-id="cc86a-241">如果你遵循我们规划的 Unreal 开发历程，则你处于探索 MRTK 核心基础知识的过程之中。</span><span class="sxs-lookup"><span data-stu-id="cc86a-241">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="cc86a-242">从这里，你可以继续了解下一部分基础知识：</span><span class="sxs-lookup"><span data-stu-id="cc86a-242">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="cc86a-243">空间映射</span><span class="sxs-lookup"><span data-stu-id="cc86a-243">Spatial mapping</span></span>](unreal-spatial-mapping.md)

<span data-ttu-id="cc86a-244">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="cc86a-244">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cc86a-245">HoloLens 摄像头</span><span class="sxs-lookup"><span data-stu-id="cc86a-245">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="cc86a-246">你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="cc86a-246">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="next-steps"></a><span data-ttu-id="cc86a-247">后续步骤</span><span class="sxs-lookup"><span data-stu-id="cc86a-247">Next steps</span></span>
* [<span data-ttu-id="cc86a-248">本地空间定位点</span><span class="sxs-lookup"><span data-stu-id="cc86a-248">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="cc86a-249">空间定位点文档</span><span class="sxs-lookup"><span data-stu-id="cc86a-249">Spatial Anchors documentation</span></span>](https://docs.microsoft.com/azure/spatial-anchors/)
* [<span data-ttu-id="cc86a-250">空间定位点功能</span><span class="sxs-lookup"><span data-stu-id="cc86a-250">Spatial Anchor features</span></span>](https://azure.microsoft.com/services/spatial-anchors/#features)
* [<span data-ttu-id="cc86a-251">有效定位点体验准则</span><span class="sxs-lookup"><span data-stu-id="cc86a-251">Effective anchor experience guidelines</span></span>](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)