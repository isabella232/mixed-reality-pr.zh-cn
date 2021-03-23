---
title: 设置 Photon Unity Networking
description: 完成本课程可以了解如何在 HoloLens 2 混合现实应用程序中实现 Photon Unity Network。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 多用户功能, Photon, MRTK, 混合现实工具包, UWP, Azure 空间定位点, PUN
ms.localizationpriority: high
ms.openlocfilehash: 372cb7c9516a994cb7c3da1efb6cade792e862d1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590309"
---
# <a name="2-setting-up-photon-unity-networking"></a><span data-ttu-id="2b106-104">2.设置 Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="2b106-104">2. Setting up Photon Unity Networking</span></span>

<span data-ttu-id="2b106-105">在本教程中，你将准备好使用 Photon Unity Networking (PUN) 来创建共享体验。</span><span class="sxs-lookup"><span data-stu-id="2b106-105">In this tutorial, you will prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="2b106-106">你将学习如何创建 PUN 应用，如何将 PUN 资产导入到 Unity 项目，以及如何将 Unity 项目连接到 PUN 应用。</span><span class="sxs-lookup"><span data-stu-id="2b106-106">You will learn how to create a PUN app, import PUN assets into your Unity project, and connect your Unity project to the PUN app.</span></span>

## <a name="objectives"></a><span data-ttu-id="2b106-107">目标</span><span class="sxs-lookup"><span data-stu-id="2b106-107">Objectives</span></span>

* <span data-ttu-id="2b106-108">了解如何创建 PUN 应用</span><span class="sxs-lookup"><span data-stu-id="2b106-108">Learn how to create a PUN app</span></span>
* <span data-ttu-id="2b106-109">了解如何查找和导入 PUN 资产</span><span class="sxs-lookup"><span data-stu-id="2b106-109">Learn how to find and import the PUN assets</span></span>
* <span data-ttu-id="2b106-110">了解如何将 Unity 项目连接到 PUN 应用</span><span class="sxs-lookup"><span data-stu-id="2b106-110">Learn how to connect your Unity project to the PUN app</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="2b106-111">创建和准备 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="2b106-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="2b106-112">在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。</span><span class="sxs-lookup"><span data-stu-id="2b106-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="2b106-113">首先，请按照[初始化项目和部署第一个应用程序](mr-learning-base-02.md)进行操作，但请忽略[在设备上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)说明；其中操作包括以下步骤：</span><span class="sxs-lookup"><span data-stu-id="2b106-113">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="2b106-114">[创建 Unity 项目](mr-learning-base-02.md#creating-the-unity-project)并为其指定适当的名称，例如“MRTK 教程”</span><span class="sxs-lookup"><span data-stu-id="2b106-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="2b106-115">切换生成平台</span><span class="sxs-lookup"><span data-stu-id="2b106-115">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="2b106-116">导入 TextMeshPro 基本资源</span><span class="sxs-lookup"><span data-stu-id="2b106-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="2b106-117">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="2b106-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="2b106-118">配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="2b106-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="2b106-119">[创建和配置场景](mr-learning-base-02.md#creating-and-configuring-the-scene)，并为场景提供适当的名称，例如 MultiUserCapabilities</span><span class="sxs-lookup"><span data-stu-id="2b106-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="2b106-120">然后，按照[更改空间感知显示选项](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)中的说明执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2b106-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="2b106-121">将 MRTK 配置配置文件更改为 DefaultHoloLens2ConfigurationProfile </span><span class="sxs-lookup"><span data-stu-id="2b106-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="2b106-122">将空间感知网格显示选项更改为“遮挡” 。</span><span class="sxs-lookup"><span data-stu-id="2b106-122">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="enabling-additional-capabilities"></a><span data-ttu-id="2b106-123">启用附加功能</span><span class="sxs-lookup"><span data-stu-id="2b106-123">Enabling additional capabilities</span></span>

<span data-ttu-id="2b106-124">在 Unity 菜单中，选择“编辑” > “项目设置...”打开“播放器设置”窗口，然后找到“播放器” >  “发布设置”部分：   </span><span class="sxs-lookup"><span data-stu-id="2b106-124">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![Unity 播放器设置](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

<span data-ttu-id="2b106-126">在“发布设置”中，向下滚动到“功能”部分，仔细检查你在上面的[配置 Unity 项目](mr-learning-base-02.md#configuring-the-unity-project)步骤中启用的“InternetClient”、“Microphone”、“SpatialPerception”和“GazeInput”都已启用     。</span><span class="sxs-lookup"><span data-stu-id="2b106-126">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, **SpatialPerception**, and **GazeInput** capabilities, which you enabled during the [Configuring the Unity project](mr-learning-base-02.md#configuring-the-unity-project) step above, are enabled.</span></span>

<span data-ttu-id="2b106-127">然后，启用以下附加功能：</span><span class="sxs-lookup"><span data-stu-id="2b106-127">Then enable the following additional capabilities:</span></span>

* <span data-ttu-id="2b106-128">“InternetClientServer”功能</span><span class="sxs-lookup"><span data-stu-id="2b106-128">**InternetClientServer** capability</span></span>
* <span data-ttu-id="2b106-129">“PrivateNetworkClientServer”功能</span><span class="sxs-lookup"><span data-stu-id="2b106-129">**PrivateNetworkClientServer** capability</span></span>

![Unity 功能设置](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="2b106-131">安装内置 Unity 包</span><span class="sxs-lookup"><span data-stu-id="2b106-131">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="2b106-132">在 Unity 菜单中，选择“窗口” > “包管理器”打开“包管理器”窗口，然后选择“AR Foundation”并单击“安装”按钮以安装包   ：</span><span class="sxs-lookup"><span data-stu-id="2b106-132">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![选中了“AR Foundation”的 Unity 包管理器](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="2b106-134">你要安装 AR Foundation 包，因为将在下一部分中导入 Azure Spatial Anchors SDK 必须使用它。</span><span class="sxs-lookup"><span data-stu-id="2b106-134">You are installing the AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="2b106-135">导入教程资产</span><span class="sxs-lookup"><span data-stu-id="2b106-135">Importing the tutorial assets</span></span>

<span data-ttu-id="2b106-136">将 AzurespatialAnchors SDK V2.7.1 添加到 unity 项目，若要添加包，请遵循此[教程](https://docs.microsoft.com/en-us/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span><span class="sxs-lookup"><span data-stu-id="2b106-136">Add AzurespatialAnchors SDK V2.7.1 into your unity project, to add the packages please follow this [tutorial](https://docs.microsoft.com/en-us/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>


<span data-ttu-id="2b106-137">下载以下 Unity 自定义包，并 **按其列出顺序** 将其 **导入**：</span><span class="sxs-lookup"><span data-stu-id="2b106-137">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>
 
* [<span data-ttu-id="2b106-138">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="2b106-138">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="2b106-139">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="2b106-139">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)
* [<span data-ttu-id="2b106-140">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="2b106-140">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)

<span data-ttu-id="2b106-141">导入教程资产后，“项目”窗口应如下所示：</span><span class="sxs-lookup"><span data-stu-id="2b106-141">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![导入教程资产后的 Unity“层次结构”、“场景”和“项目”窗口](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="2b106-143">有关如何导入 Unity 自定义包的提示，可参阅[导入教程资产](mr-learning-base-04.md#importing-the-tutorial-assets)说明。</span><span class="sxs-lookup"><span data-stu-id="2b106-143">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="2b106-144">导入 MultiUserCapabilities 教程资产包后，会在控制台窗口中看到几个 [CS0246](/dotnet/csharp/language-reference/compiler-messages/cs0246) 错误，指出缺少类型或命名空间。</span><span class="sxs-lookup"><span data-stu-id="2b106-144">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="2b106-145">这符合预期，并且会在下一部分中（当你导入 PUN 资产时）解决。</span><span class="sxs-lookup"><span data-stu-id="2b106-145">This is expected and will be resolved in the next section when you import the PUN assets.</span></span>

## <a name="importing-the-pun-assets"></a><span data-ttu-id="2b106-146">导入 PUN 资产</span><span class="sxs-lookup"><span data-stu-id="2b106-146">Importing the PUN assets</span></span>

<span data-ttu-id="2b106-147">在 Unity 菜单中，选择“窗口” > “资产存储”来打开“资产存储”窗口，搜索并选择来自 Exit Games 的“PUN 2 - FREE”，然后单击“下载”按钮，将资产包下载到 Unity 帐户   。</span><span class="sxs-lookup"><span data-stu-id="2b106-147">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, click the **Download** button to download the asset package to your Unity account.</span></span>

<span data-ttu-id="2b106-148">下载完成后，单击“导入”按钮以打开“导入 Unity 包”窗口：</span><span class="sxs-lookup"><span data-stu-id="2b106-148">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![具有“PUN 2 - 免费”的 Unity 资产存储](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

<span data-ttu-id="2b106-150">在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：</span><span class="sxs-lookup"><span data-stu-id="2b106-150">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![具有 PUN 2 导入窗口的 Unity](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

<span data-ttu-id="2b106-152">当 Unity 完成导入过程后，将显示“PUN 向导”窗口，其中加载了“PUN 设置”菜单，此时你可以忽略或关闭此窗口：</span><span class="sxs-lookup"><span data-stu-id="2b106-152">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![具有 PUN 设置窗口的 Unity](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a><span data-ttu-id="2b106-154">创建 PUN 应用程序</span><span class="sxs-lookup"><span data-stu-id="2b106-154">Creating the PUN application</span></span>

<span data-ttu-id="2b106-155">在本部分中，你将创建一个 Photon 帐户（如果还没有），并创建新的 PUN 应用。</span><span class="sxs-lookup"><span data-stu-id="2b106-155">In this section, you will create a Photon account, if you don't already have one, and create a new PUN app.</span></span>

<span data-ttu-id="2b106-156">导航到 Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">仪表板</a>，如果你已有想要使用的帐户，请登录；否则，请单击“创建一个”链接并按照说明注册新帐户：</span><span class="sxs-lookup"><span data-stu-id="2b106-156">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![Photon 登录页](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

<span data-ttu-id="2b106-158">登录后，单击“创建新应用”按钮：</span><span class="sxs-lookup"><span data-stu-id="2b106-158">Once signed in, click the **Create a New App** button:</span></span>

![Photon 仪表板欢迎页](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

<span data-ttu-id="2b106-160">在“创建新应用程序”页上，输入以下值：</span><span class="sxs-lookup"><span data-stu-id="2b106-160">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="2b106-161">对于 Photon 类型，请选择“PUN”</span><span class="sxs-lookup"><span data-stu-id="2b106-161">For Photon Type, select PUN</span></span>
* <span data-ttu-id="2b106-162">对于“名称”，请输入合适的名称，例如“MRTK 教程”</span><span class="sxs-lookup"><span data-stu-id="2b106-162">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="2b106-163">对于“说明”，请选择性地输入适当的说明</span><span class="sxs-lookup"><span data-stu-id="2b106-163">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="2b106-164">对于“Url”，请将字段留空</span><span class="sxs-lookup"><span data-stu-id="2b106-164">For Url, leave the field empty</span></span>

<span data-ttu-id="2b106-165">然后，单击“创建”按钮来创建新的应用：</span><span class="sxs-lookup"><span data-stu-id="2b106-165">Then click the **Create** button to create the new app:</span></span>

![Photon 创建应用程序页](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

<span data-ttu-id="2b106-167">Photon 完成创建过程后，仪表板上将显示新的 PUN 应用：</span><span class="sxs-lookup"><span data-stu-id="2b106-167">Once Photon has finished the creation process, the new PUN app will appear on your dashboard:</span></span>

![Photon 应用程序页](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="2b106-169">将 Unity 项目连接到 PUN 应用程序</span><span class="sxs-lookup"><span data-stu-id="2b106-169">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="2b106-170">在本部分中，你要将 Unity 项目连接到在上一部分中创建的 PUN 应用。</span><span class="sxs-lookup"><span data-stu-id="2b106-170">In this section, you will connect your Unity project to the PUN app you created in the previous section.</span></span>

<span data-ttu-id="2b106-171">在 Photon 仪表板上，单击“应用 ID”字段以显示应用 ID，然后将其复制到剪贴板：</span><span class="sxs-lookup"><span data-stu-id="2b106-171">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![选中了应用 ID 的 Photon 应用程序页](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

<span data-ttu-id="2b106-173">在 Unity 菜单中，选择“窗口” > “Photon Unity Networking” > “PUN 向导”以打开 PUN 向导窗口，然后单击“设置项目”按钮以打开“PUN 设置”菜单，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="2b106-173">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="2b106-174">在“应用 ID 或电子邮件”字段中，粘贴在上一步中复制的 PUN 应用 ID</span><span class="sxs-lookup"><span data-stu-id="2b106-174">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="2b106-175">然后单击“设置项目”按钮，以应用该应用 ID：</span><span class="sxs-lookup"><span data-stu-id="2b106-175">Then click the **Setup Project** button to apply the app ID:</span></span>

![填写了应用 ID 的 Unity PUN 设置窗口](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

<span data-ttu-id="2b106-177">当 Unity 完成 PUN 设置过程后，“PUN 设置”菜单将显示消息“已完成!”</span><span class="sxs-lookup"><span data-stu-id="2b106-177">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="2b106-178">并在“项目”窗口中自动选择“PhotonServerSettings”资产，使其属性显示在检查器窗口中：</span><span class="sxs-lookup"><span data-stu-id="2b106-178">and automatically select the **PhotonServerSettings** asset in the Project window, so its properties are displayed in the Inspector window:</span></span>

![应用了“设置项目”的 Unity PUN 设置窗口](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="2b106-180">祝贺</span><span class="sxs-lookup"><span data-stu-id="2b106-180">Congratulations</span></span>

<span data-ttu-id="2b106-181">你已成功创建 PUN 应用并将它连接到了 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="2b106-181">You have successfully created a PUN app and connected it to your Unity project.</span></span> <span data-ttu-id="2b106-182">下一步是允许与其他用户建立连接，从而使多个用户可以看到彼此。</span><span class="sxs-lookup"><span data-stu-id="2b106-182">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2b106-183">下一教程：3.连接多个用户</span><span class="sxs-lookup"><span data-stu-id="2b106-183">Next Tutorial: 3. Connecting multiple users</span></span>](mr-learning-sharing-03.md)