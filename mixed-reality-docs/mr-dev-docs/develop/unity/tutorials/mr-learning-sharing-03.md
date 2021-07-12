---
title: 连接多个用户
description: 完成本课程可以了解如何在 HoloLens 2 混合现实应用程序中连接多名用户。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, 多用户功能, Photon, MRTK, 混合现实工具包, UWP, Azure 空间定位点
ms.localizationpriority: high
ms.openlocfilehash: 976593fd2f107d456da4f04da19621dd253f2ae1
ms.sourcegitcommit: 943489923c69c3a28bc152f1cb516dcdcea2880a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2021
ms.locfileid: "111772420"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="ae38e-104">3.连接多个用户</span><span class="sxs-lookup"><span data-stu-id="ae38e-104">3. Connecting multiple users</span></span>

<span data-ttu-id="ae38e-105">本教程介绍如何将多个用户连接为实时共享体验的一部分。</span><span class="sxs-lookup"><span data-stu-id="ae38e-105">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="ae38e-106">在本教程结束时，你将能够在多台设备上运行应用，并让每位用户都能实时看到其他用户的头像移动。</span><span class="sxs-lookup"><span data-stu-id="ae38e-106">By the end of the tutorial, you will be able to run the app on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="ae38e-107">目标</span><span class="sxs-lookup"><span data-stu-id="ae38e-107">Objectives</span></span>

* <span data-ttu-id="ae38e-108">了解如何在共享体验中连接多个用户</span><span class="sxs-lookup"><span data-stu-id="ae38e-108">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="ae38e-109">准备场景</span><span class="sxs-lookup"><span data-stu-id="ae38e-109">Preparing the scene</span></span>

<span data-ttu-id="ae38e-110">在本部分，你将通过添加一些教程预制件来准备场景。</span><span class="sxs-lookup"><span data-stu-id="ae38e-110">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="ae38e-111">在“项目”窗口中导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “预制件”文件夹，然后单击以下预制件并将其拖动到“层次结构”窗口中，从而将其添加到场景中  ：</span><span class="sxs-lookup"><span data-stu-id="ae38e-111">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="ae38e-112">NetworkLobby 预制件</span><span class="sxs-lookup"><span data-stu-id="ae38e-112">**NetworkLobby** prefab</span></span>
* <span data-ttu-id="ae38e-113">SharedPlayground 预制件</span><span class="sxs-lookup"><span data-stu-id="ae38e-113">**SharedPlayground** prefab</span></span>

![选中了新增的 NetworkLobby 和 SharedPlayground 预制件的 Unity](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

<span data-ttu-id="ae38e-115">在“项目”窗口中导航到“资产” > “MRTK.Tutorials.AzureSpatialAnchors” > “预制件”文件夹，然后单击以下预制件并将其拖动到“层次结构”窗口中，从而将其添加到场景中  ：</span><span class="sxs-lookup"><span data-stu-id="ae38e-115">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefab into the Hierarchy window to add it to your scene:</span></span>

* <span data-ttu-id="ae38e-116">DebugWindow 预制件</span><span class="sxs-lookup"><span data-stu-id="ae38e-116">**DebugWindow** prefab</span></span>

![选中了新增的 DebugWindow 预制件的 Unity](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="ae38e-118">创建用户预制件</span><span class="sxs-lookup"><span data-stu-id="ae38e-118">Creating the user prefab</span></span>

<span data-ttu-id="ae38e-119">在本部分中，你将创建一个预制件，用于表示共享体验中的用户。</span><span class="sxs-lookup"><span data-stu-id="ae38e-119">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="ae38e-120">1.创建和配置用户</span><span class="sxs-lookup"><span data-stu-id="ae38e-120">1. Create and configure the user</span></span>

<span data-ttu-id="ae38e-121">在“层次结构”窗口中，右键单击空白区域，然后选择“创建空白项”将空对象添加到场景中，将该对象命名为“PhotonUser”，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="ae38e-121">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="ae38e-122">请确保将变换位置设置为 X = 0，Y = 0，Z = 0：</span><span class="sxs-lookup"><span data-stu-id="ae38e-122">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![选中了新创建的 PhotonUser 对象的 Unity](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

<span data-ttu-id="ae38e-124">在“层次结构”窗口中，选择“PhotonUser”对象，然后在检查器窗口中，使用“添加组件”按钮将“Photon 用户(脚本)”组件添加到 PhotonUser 对象：  </span><span class="sxs-lookup"><span data-stu-id="ae38e-124">In the Hierarchy window, select the **PhotonUser** object, then in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![添加了 PhotonUser 组件的 Unity](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

<span data-ttu-id="ae38e-126">在检查器窗口中，使用“添加组件”按钮将“通用网络同步(脚本)”组件添加到 PhotonUser 对象，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="ae38e-126">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="ae38e-127">选中“是用户”复选框</span><span class="sxs-lookup"><span data-stu-id="ae38e-127">Check the **Is User** checkbox</span></span>

![添加并配置了“通用网络同步”组件的 Unity](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

<span data-ttu-id="ae38e-129">在检查器窗口中，使用“添加组件”按钮将“Photon 视图(脚本)”组件添加到 PhotonUser 对象，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="ae38e-129">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="ae38e-130">确保“观察到的组件”字段分配有“通用网络同步(脚本)”组件 </span><span class="sxs-lookup"><span data-stu-id="ae38e-130">Ensure that the **Observed Components** field is assigned with the **Generic Net Sync (Script)** component</span></span>

![添加并配置了 Photon 视图组件的 Unity](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="ae38e-132">2.创建头像</span><span class="sxs-lookup"><span data-stu-id="ae38e-132">2. Create the avatar</span></span>

<span data-ttu-id="ae38e-133">在“项目”窗口中，导航到“包” > “混合现实工具包标准资产” > “材料”文件夹以找到 MRTK 材料。</span><span class="sxs-lookup"><span data-stu-id="ae38e-133">In the Project window, navigate to the **Packages** > **Mixed Reality Toolkit Standard Assets** > **Materials** folder to locate the MRTK materials.</span></span>

<span data-ttu-id="ae38e-134">然后，在“层次结构”窗口中，右键单击 PhotonUser 对象，然后选择“3D 对象” > “球体”来创建一个球体对象作为 PhotonUser 对象的子项，并按如下所示对它进行配置  ：</span><span class="sxs-lookup"><span data-stu-id="ae38e-134">Then, in the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="ae38e-135">请确保将变换位置设置为 X = 0，Y = 0，Z = 0</span><span class="sxs-lookup"><span data-stu-id="ae38e-135">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="ae38e-136">将变换标度更改为适当的大小，例如 X = 0.15，Y = 0.15，Z = 0.15</span><span class="sxs-lookup"><span data-stu-id="ae38e-136">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>
* <span data-ttu-id="ae38e-137">在“MeshRenderer”>“材料”>“元素 0”字段中，指定 MRTK_Standard_White 材料 </span><span class="sxs-lookup"><span data-stu-id="ae38e-137">To the MeshRenderer > Materials > **Element 0** field, assign the **MRTK_Standard_White** material</span></span>

![具有新创建和新配置的头像球体的 Unity](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="ae38e-139">3.创建预制件</span><span class="sxs-lookup"><span data-stu-id="ae38e-139">3. Create the prefab</span></span>

<span data-ttu-id="ae38e-140">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “资源”文件夹：  </span><span class="sxs-lookup"><span data-stu-id="ae38e-140">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![选中了“资源”文件夹的 Unity 项目窗口](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

<span data-ttu-id="ae38e-142">在“资源”文件夹仍处于选定状态的情况下，单击“层次结构”窗口中的“PhotonUser”对象并将其拖动到“资源”文件夹，以使 PhotonUser 对象成为预制件：  </span><span class="sxs-lookup"><span data-stu-id="ae38e-142">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![选中了新创建的 PhotonUser 预制件的 Unity](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

<span data-ttu-id="ae38e-144">在“层次结构”窗口中，右键单击“PhotonUser”对象，然后选择“删除”将其从场景中删除：</span><span class="sxs-lookup"><span data-stu-id="ae38e-144">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![从场景中删除了新创建的 PhotonUser 预制件的 Unity](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="ae38e-146">配置 PUN 以将用户预制件实例化</span><span class="sxs-lookup"><span data-stu-id="ae38e-146">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="ae38e-147">在本部分中，你将配置项目以使用在上一部分中创建的 PhotonUser 预制件。</span><span class="sxs-lookup"><span data-stu-id="ae38e-147">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="ae38e-148">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “资源”文件夹。  </span><span class="sxs-lookup"><span data-stu-id="ae38e-148">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="ae38e-149">在“层次结构”窗口中，展开“NetworkLobby”对象并选择“NetworkRoom”子对象，然后在检查器窗口中，找到“Photon 房间(脚本)”组件，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="ae38e-149">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="ae38e-150">向“Photon 用户预制件”字段中分配来自“资源”文件夹的“PhotonUser”预制件</span><span class="sxs-lookup"><span data-stu-id="ae38e-150">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![配置了部分 Photon 房间组件的 Unity](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="ae38e-152">尝试包含多个用户的体验</span><span class="sxs-lookup"><span data-stu-id="ae38e-152">Trying the experience with multiple users</span></span>

<span data-ttu-id="ae38e-153">如果现在生成 Unity 项目并将其部署到 HoloLens，然后回到 Unity，并在应用运行于 HoloLens 上时进入“游戏”模式，那么当你来回晃动头部 (HoloLens) 时，你将看到 HoloLens 用户头像移动：</span><span class="sxs-lookup"><span data-stu-id="ae38e-153">If you now build and deploy the Unity project to your HoloLens, then, back in Unity, enter Game mode while the app is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![动画显示了具有联网用户的 Unity](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="ae38e-155">要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。</span><span class="sxs-lookup"><span data-stu-id="ae38e-155">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="ae38e-156">应用需要连接到 Photon，因此请确保计算机/设备已连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="ae38e-156">The app needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ae38e-157">祝贺</span><span class="sxs-lookup"><span data-stu-id="ae38e-157">Congratulations</span></span>

<span data-ttu-id="ae38e-158">你已成功将项目配置为允许多个用户连接到相同体验并可看到彼此的移动。</span><span class="sxs-lookup"><span data-stu-id="ae38e-158">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="ae38e-159">在下一教程中，你将实现功能，以使对象的移动也可以在多个设备之间共享。</span><span class="sxs-lookup"><span data-stu-id="ae38e-159">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae38e-160">下一教程：4.与多个用户共享对象移动</span><span class="sxs-lookup"><span data-stu-id="ae38e-160">Next Tutorial: 4. Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
