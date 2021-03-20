---
title: HoloLens (第一代) 和 Azure 311-Microsoft Graph
description: 完成本课程，了解如何利用 Microsoft Graph，并在混合现实应用程序中连接到用于驱动工作效率的数据。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合现实，学院，unity，教程，api，microsoft graph，hololens，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: 6afa1e8c5d2baa2d46652901558b2917c5c43d70
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730244"
---
# <a name="hololens-1st-gen-and-azure-311---microsoft-graph"></a><span data-ttu-id="d8b85-104">HoloLens (第一代) 和 Azure 311-Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="d8b85-104">HoloLens (1st gen) and Azure 311 - Microsoft Graph</span></span>

>[!NOTE]
><span data-ttu-id="d8b85-105">混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="d8b85-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="d8b85-106">因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。</span><span class="sxs-lookup"><span data-stu-id="d8b85-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="d8b85-107">我们 **不会** 在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。</span><span class="sxs-lookup"><span data-stu-id="d8b85-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="d8b85-108">我们将维护这些教程，使之持续适用于支持的设备。</span><span class="sxs-lookup"><span data-stu-id="d8b85-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="d8b85-109">将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="d8b85-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="d8b85-110">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="d8b85-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<span data-ttu-id="d8b85-111">在本课程中，你将了解如何使用 *Microsoft Graph* 在混合现实应用程序中使用安全身份验证登录到 Microsoft 帐户。</span><span class="sxs-lookup"><span data-stu-id="d8b85-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="d8b85-112">然后，你将在应用程序界面中检索并显示你的计划会议。</span><span class="sxs-lookup"><span data-stu-id="d8b85-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="d8b85-113">*Microsoft Graph* 是一组 api，旨在实现对许多 Microsoft 服务的访问。</span><span class="sxs-lookup"><span data-stu-id="d8b85-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="d8b85-114">Microsoft 将 Microsoft Graph 描述为一系列按关系连接的资源，这意味着，应用程序可以访问所有种类的已连接用户数据。</span><span class="sxs-lookup"><span data-stu-id="d8b85-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="d8b85-115">有关详细信息，请访问 [Microsoft Graph 页](https://developer.microsoft.com/graph)。</span><span class="sxs-lookup"><span data-stu-id="d8b85-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="d8b85-116">开发过程中，将会创建一个应用程序，在该应用程序中，用户将会被指示到，然后点击一个球，这将提示用户安全登录到 Microsoft 帐户。</span><span class="sxs-lookup"><span data-stu-id="d8b85-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="d8b85-117">登录到帐户后，用户将能够看到一天计划的会议列表。</span><span class="sxs-lookup"><span data-stu-id="d8b85-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="d8b85-118">完成本课程后，你将拥有一个混合现实 HoloLens 应用程序，该应用程序将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d8b85-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="d8b85-119">使用点击 "笔势"，点击某个对象，这将提示用户登录到 Microsoft 帐户 (移出该应用程序以登录，然后再次) 返回到应用程序。</span><span class="sxs-lookup"><span data-stu-id="d8b85-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="d8b85-120">查看当天计划的会议列表。</span><span class="sxs-lookup"><span data-stu-id="d8b85-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="d8b85-121">在您的应用程序中，您将由您来决定如何将结果与您的设计相集成。</span><span class="sxs-lookup"><span data-stu-id="d8b85-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="d8b85-122">本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。</span><span class="sxs-lookup"><span data-stu-id="d8b85-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="d8b85-123">您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。</span><span class="sxs-lookup"><span data-stu-id="d8b85-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="d8b85-124">设备支持</span><span class="sxs-lookup"><span data-stu-id="d8b85-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d8b85-125">课程</span><span class="sxs-lookup"><span data-stu-id="d8b85-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="d8b85-126"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d8b85-126"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d8b85-127"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="d8b85-127"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="d8b85-128">MR 和 Azure 311：Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="d8b85-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="d8b85-129">✔️</span><span class="sxs-lookup"><span data-stu-id="d8b85-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="d8b85-130">必备条件</span><span class="sxs-lookup"><span data-stu-id="d8b85-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="d8b85-131">本教程专为具有 Unity 和 c # 基本经验的开发人员设计。</span><span class="sxs-lookup"><span data-stu-id="d8b85-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="d8b85-132">请注意，本文档中的先决条件和书面说明表示在) 2018 年7月 (撰写本文时已测试和验证的内容。</span><span class="sxs-lookup"><span data-stu-id="d8b85-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="d8b85-133">你可以随意使用最新的软件（如 [安装工具](../../install-the-tools.md) 一文中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="d8b85-133">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="d8b85-134">本课程建议采用以下硬件和软件：</span><span class="sxs-lookup"><span data-stu-id="d8b85-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="d8b85-135">开发 PC</span><span class="sxs-lookup"><span data-stu-id="d8b85-135">A development PC</span></span>
- [<span data-ttu-id="d8b85-136">Windows 10 秋季创意者更新 (或更高版本启用了开发人员模式) </span><span class="sxs-lookup"><span data-stu-id="d8b85-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d8b85-137">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="d8b85-137">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d8b85-138">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="d8b85-138">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d8b85-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d8b85-139">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="d8b85-140">已启用开发人员模式的[Microsoft HoloLens](/hololens/hololens1-hardware)</span><span class="sxs-lookup"><span data-stu-id="d8b85-140">A [Microsoft HoloLens](/hololens/hololens1-hardware) with Developer mode enabled</span></span>
- <span data-ttu-id="d8b85-141">Azure 安装和 Microsoft Graph 数据检索的 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="d8b85-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="d8b85-142"> (个人或工作/学校) 有效的 **Microsoft 帐户**</span><span class="sxs-lookup"><span data-stu-id="d8b85-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="d8b85-143">使用同一个 Microsoft 帐户安排当天计划的几个会议</span><span class="sxs-lookup"><span data-stu-id="d8b85-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="d8b85-144">开始之前</span><span class="sxs-lookup"><span data-stu-id="d8b85-144">Before you start</span></span>

1.  <span data-ttu-id="d8b85-145">若要避免在生成此项目时遇到问题，强烈建议你在根或近乎根文件夹中创建本教程中所述的项目 (长文件夹路径在生成时) 会导致问题。</span><span class="sxs-lookup"><span data-stu-id="d8b85-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="d8b85-146">设置并测试你的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d8b85-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="d8b85-147">如果需要支持设置 HoloLens，请 [确保访问 hololens 设置一文](/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="d8b85-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="d8b85-148">在开始开发新的 HoloLens 应用程序时，最好执行校准和传感器调整 (有时，它可以帮助为每个用户) 执行这些任务。</span><span class="sxs-lookup"><span data-stu-id="d8b85-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="d8b85-149">有关校准的帮助信息，请单击此链接，了解 [到 HoloLens 校准文章](/hololens/hololens-calibration#hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="d8b85-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](/hololens/hololens-calibration#hololens-2).</span></span>

<span data-ttu-id="d8b85-150">有关传感器优化的帮助，请单击 ["HoloLens 传感器优化" 一文](/hololens/hololens-updates)。</span><span class="sxs-lookup"><span data-stu-id="d8b85-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](/hololens/hololens-updates).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="d8b85-151">第1章-在应用程序注册门户中创建应用</span><span class="sxs-lookup"><span data-stu-id="d8b85-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="d8b85-152">首先，需要在 **应用程序注册门户** 中创建并注册应用程序。</span><span class="sxs-lookup"><span data-stu-id="d8b85-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="d8b85-153">在本章中，你还将找到服务密钥，你可以通过它调用 *Microsoft Graph* 来访问你的帐户内容。</span><span class="sxs-lookup"><span data-stu-id="d8b85-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="d8b85-154">导航到 [Microsoft 应用程序注册门户](https://apps.dev.microsoft.com) 并登录到你的 microsoft 帐户。</span><span class="sxs-lookup"><span data-stu-id="d8b85-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="d8b85-155">登录后，将重定向到 **应用程序注册门户**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="d8b85-156">在 " **我的应用程序** " 部分中，单击 " **添加应用**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="d8b85-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="d8b85-157">**应用程序注册门户** 的外观可能会不同，具体取决于你之前是否使用过 *Microsoft Graph*。</span><span class="sxs-lookup"><span data-stu-id="d8b85-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="d8b85-158">下面的屏幕截图显示这些不同版本。</span><span class="sxs-lookup"><span data-stu-id="d8b85-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="d8b85-159">添加应用程序的名称，然后单击 " **创建**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="d8b85-160">创建应用程序后，将重定向到应用程序主页。</span><span class="sxs-lookup"><span data-stu-id="d8b85-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="d8b85-161">复制 " **应用程序 Id** "，并确保在 "安全" 的位置记录此值，并在代码中立即使用。</span><span class="sxs-lookup"><span data-stu-id="d8b85-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="d8b85-162">在 " **平台** " 部分中，确保显示 " **本机应用程序** "。</span><span class="sxs-lookup"><span data-stu-id="d8b85-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="d8b85-163">如果 *未* 单击 " **添加平台** "，请选择 " **本机应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="d8b85-164">在同一页中向下滚动，并在 " **Microsoft Graph 权限** " 部分中向下滚动，你将需要为应用程序添加其他权限。</span><span class="sxs-lookup"><span data-stu-id="d8b85-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="d8b85-165">单击 "**委派权限**" 旁的 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="d8b85-166">由于你希望你的应用程序访问用户的日历，因此 **选中名为** Calendar 的框，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="d8b85-167">滚动到底部，然后单击 " **保存** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="d8b85-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="d8b85-168">你的保存将会得到确认，你可以从 **应用程序注册门户** 注销。</span><span class="sxs-lookup"><span data-stu-id="d8b85-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="d8b85-169">第2章-设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="d8b85-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="d8b85-170">下面是用于使用混合现实进行开发的典型设置，因此，这是其他项目的一个不错的模板。</span><span class="sxs-lookup"><span data-stu-id="d8b85-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="d8b85-171">打开 *Unity* ，并单击 " **新建**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="d8b85-172">需要提供 Unity 项目名称。</span><span class="sxs-lookup"><span data-stu-id="d8b85-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="d8b85-173">插入 **MSGraphMR**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="d8b85-174">请确保将项目模板设置为 **3d**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="d8b85-175">将位置设置为合适的 **位置** (记住，更接近根目录) 。</span><span class="sxs-lookup"><span data-stu-id="d8b85-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="d8b85-176">然后单击 " **创建项目**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="d8b85-177">当 Unity 处于打开状态时，有必要选中 "默认 **脚本编辑器** " 设置为 " **Visual Studio**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="d8b85-178">转到 "**编辑**  >  **首选项**"，然后在新窗口中导航到 "**外部工具**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-178">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="d8b85-179">将 **外部脚本编辑器** 更改为 **Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="d8b85-180">关闭 " **首选项** " 窗口。</span><span class="sxs-lookup"><span data-stu-id="d8b85-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="d8b85-181">转到 "**文件**  >  **生成设置**" 并选择 "**通用 Windows 平台**"，然后单击 "**切换平台**" 按钮以应用所选内容。</span><span class="sxs-lookup"><span data-stu-id="d8b85-181">Go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="d8b85-182">仍在 **文件**  >  **生成设置** 中时，请确保：</span><span class="sxs-lookup"><span data-stu-id="d8b85-182">While still in **File** > **Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="d8b85-183">**目标设备** 设置为 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="d8b85-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="d8b85-184">**生成类型** 设置为 **D3D**</span><span class="sxs-lookup"><span data-stu-id="d8b85-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="d8b85-185">**SDK** 设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="d8b85-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="d8b85-186">**Visual Studio 版本** 设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="d8b85-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="d8b85-187">"**生成并运行**" 设置为 "**本地计算机**"</span><span class="sxs-lookup"><span data-stu-id="d8b85-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="d8b85-188">保存场景并将其添加到生成中。</span><span class="sxs-lookup"><span data-stu-id="d8b85-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="d8b85-189">通过选择 " **添加打开的场景**" 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="d8b85-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="d8b85-190">将显示 "保存" 窗口。</span><span class="sxs-lookup"><span data-stu-id="d8b85-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="d8b85-191">为此以及任何将来的场景创建新文件夹。</span><span class="sxs-lookup"><span data-stu-id="d8b85-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="d8b85-192">选择 " **新建文件夹** " 按钮，创建一个新文件夹，将其命名为 **场景**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="d8b85-193">打开新创建的 **场景** 文件夹，然后 *在 "文件名：文本" 字段* 中，键入 **MR_ComputerVisionScene**，并单击 " **保存**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="d8b85-194">请注意，必须将 Unity 场景保存在 " *资产* " 文件夹中，因为它们必须与 Unity 项目相关联。</span><span class="sxs-lookup"><span data-stu-id="d8b85-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="d8b85-195">创建场景文件夹 (和其他类似文件夹) 是构建 Unity 项目的典型方式。</span><span class="sxs-lookup"><span data-stu-id="d8b85-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="d8b85-196">现在，" *生成设置*" 中的其余设置应保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="d8b85-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="d8b85-197">在 " *生成设置* " 窗口中，单击 " **播放机设置** " 按钮，这会在 *检查器* 所在的空间中打开相关面板。</span><span class="sxs-lookup"><span data-stu-id="d8b85-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="d8b85-198">在此面板中，需要验证几项设置：</span><span class="sxs-lookup"><span data-stu-id="d8b85-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="d8b85-199">在 " **其他设置** " 选项卡中：</span><span class="sxs-lookup"><span data-stu-id="d8b85-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="d8b85-200">**脚本\*\*\*\*运行时版本** 应 ( .Net 4.6 等效) **试验**，这会触发重新启动编辑器的需要。</span><span class="sxs-lookup"><span data-stu-id="d8b85-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="d8b85-201">**脚本编写后端** 应为 **.net**</span><span class="sxs-lookup"><span data-stu-id="d8b85-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="d8b85-202">**API 兼容级别** 应为 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="d8b85-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="d8b85-203">在 " **发布设置** " 选项卡的 " **功能**" 下，检查：</span><span class="sxs-lookup"><span data-stu-id="d8b85-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="d8b85-204">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="d8b85-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="d8b85-205">在面板中，在 "**发布设置**") 下面 (找到 " **XR 设置**" 中，选中 "**支持的虚拟现实**"，确保已添加 **Windows Mixed reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="d8b85-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="d8b85-206">返回 *生成设置*， *Unity c # 项目* 不再灰显;选中此旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="d8b85-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="d8b85-207">关闭“生成设置”窗口  。</span><span class="sxs-lookup"><span data-stu-id="d8b85-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="d8b85-208">保存场景和项目 (**文件**  >  **保存场景/文件**  >  **保存项目**) 。</span><span class="sxs-lookup"><span data-stu-id="d8b85-208">Save your scene and project (**FILE** > **SAVE SCENES / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="d8b85-209">第3章-在 Unity 中导入库</span><span class="sxs-lookup"><span data-stu-id="d8b85-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8b85-210">如果要跳过本课程的 *Unity 设置* 组件，并继续直接进入代码，请随时下载此 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)，将其作为 [**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目，然后从 [第5章](#chapter-5---create-meetingsui-class)继续。</span><span class="sxs-lookup"><span data-stu-id="d8b85-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="d8b85-211">若要在 Unity 内使用 *Microsoft Graph* ，需要 **使用 "**</span><span class="sxs-lookup"><span data-stu-id="d8b85-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="d8b85-212">不过，可以使用 Microsoft Graph SDK，因为在生成 Unity 项目后，它将需要添加 NuGet 包 (这意味着编辑项目后期生成) 。</span><span class="sxs-lookup"><span data-stu-id="d8b85-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="d8b85-213">将所需的 Dll 直接导入到 Unity 中是更简单的方法。</span><span class="sxs-lookup"><span data-stu-id="d8b85-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="d8b85-214">当前 Unity 中存在一个已知问题，需要在导入后重新配置插件。</span><span class="sxs-lookup"><span data-stu-id="d8b85-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="d8b85-215">此部分中 (4-7 的这些步骤) 解决 bug 后不再需要这些步骤。</span><span class="sxs-lookup"><span data-stu-id="d8b85-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="d8b85-216">若要将 *Microsoft Graph* 导入到自己的项目中，请 [下载 MSGraph_LabPlugins.zip 文件](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="d8b85-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="d8b85-217">已使用经过测试的库版本创建此包。</span><span class="sxs-lookup"><span data-stu-id="d8b85-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="d8b85-218">如果希望了解有关如何将自定义 Dll 添加到 Unity 项目的详细信息，请 [访问此链接](https://docs.unity3d.com/Manual/UsingDLL.html)。</span><span class="sxs-lookup"><span data-stu-id="d8b85-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="d8b85-219">导入包：</span><span class="sxs-lookup"><span data-stu-id="d8b85-219">To import the package:</span></span>

1.  <span data-ttu-id="d8b85-220">使用 "**资产**  >  **导入包**  >  **自定义包**" 菜单选项将 unity 包添加到 unity。</span><span class="sxs-lookup"><span data-stu-id="d8b85-220">Add the Unity Package to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span> <span data-ttu-id="d8b85-221">选择刚刚下载的包。</span><span class="sxs-lookup"><span data-stu-id="d8b85-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="d8b85-222">在弹出的 " **导入 Unity 包** " 框中，确保选择 (下的所有内容，包括) 的 **插件** 。</span><span class="sxs-lookup"><span data-stu-id="d8b85-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="d8b85-223">单击 " **导入** " 按钮，将项添加到项目。</span><span class="sxs-lookup"><span data-stu-id="d8b85-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="d8b85-224">在 "*项目" 面板* 中的 "**插件**" 下，单击 " **MSGraph** " 文件夹，然后选择名为 "" 的 **插件。**</span><span class="sxs-lookup"><span data-stu-id="d8b85-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="d8b85-225">选择该 *插件* 后，请确保未选中 **任何平台** ，然后确保 **WSAPlayer** 未被选中，然后单击 " **应用**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="d8b85-226">这只是为了确认已正确配置文件。</span><span class="sxs-lookup"><span data-stu-id="d8b85-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="d8b85-227">标记这些插件会将它们配置为仅在 Unity 编辑器中使用。</span><span class="sxs-lookup"><span data-stu-id="d8b85-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="d8b85-228">在将项目从 Unity 导出为通用 Windows 应用程序之后，WSA 文件夹中将使用不同的 Dll 集。</span><span class="sxs-lookup"><span data-stu-id="d8b85-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="d8b85-229">接下来，需要在 **MSGraph** 文件夹中打开 **WSA** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="d8b85-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="d8b85-230">你将看到刚才配置的同一文件的副本。</span><span class="sxs-lookup"><span data-stu-id="d8b85-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="d8b85-231">选择该文件，然后在检查器中：</span><span class="sxs-lookup"><span data-stu-id="d8b85-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="d8b85-232">请确保 **未选中\*\*\*\*任何平台**，并且 **仅\*\*\*\*选中** **WSAPlayer** 。</span><span class="sxs-lookup"><span data-stu-id="d8b85-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="d8b85-233">确保将 **SDK** 设置为 **UWP**，并将 "**脚本后端**" 设置为 "**点网络**"</span><span class="sxs-lookup"><span data-stu-id="d8b85-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="d8b85-234">确保 **选中**"**不处理**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="d8b85-235">单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="d8b85-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="d8b85-236">第4章-照相机设置</span><span class="sxs-lookup"><span data-stu-id="d8b85-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="d8b85-237">在本章中，你将设置场景的主照相机：</span><span class="sxs-lookup"><span data-stu-id="d8b85-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="d8b85-238">在 " *层次结构" 面板* 中，选择 " **摄像机**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="d8b85-239">选择后，你将能够在 "*检查器*" 面板中看到 **主相机** 的所有组件。</span><span class="sxs-lookup"><span data-stu-id="d8b85-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="d8b85-240">**照相机对象** 必须命名为 "**主相机**" (记下拼写！ ) </span><span class="sxs-lookup"><span data-stu-id="d8b85-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="d8b85-241">必须将主相机 **标记** 设置为 " **MainCamera** "， (记下拼写！ ) </span><span class="sxs-lookup"><span data-stu-id="d8b85-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="d8b85-242">请确保将 **转换位置** 设置为 **0，0，0**</span><span class="sxs-lookup"><span data-stu-id="d8b85-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="d8b85-243">将 **清除标志** 设置为 **纯色**</span><span class="sxs-lookup"><span data-stu-id="d8b85-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="d8b85-244">将相机组件的 **背景色** 设置为 **黑色、Alpha 0** **(十六进制代码： #00000000)**</span><span class="sxs-lookup"><span data-stu-id="d8b85-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="d8b85-245">" *层次结构" 面板* 中的最后一个对象结构应类似于下图所示：</span><span class="sxs-lookup"><span data-stu-id="d8b85-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="d8b85-246">第5章-创建 MeetingsUI 类</span><span class="sxs-lookup"><span data-stu-id="d8b85-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="d8b85-247">需要创建的第一个脚本是 **MeetingsUI**，它负责承载和填充应用程序的 UI (欢迎消息、说明和会议详细信息) 。</span><span class="sxs-lookup"><span data-stu-id="d8b85-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="d8b85-248">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="d8b85-248">To create this class:</span></span>

1.  <span data-ttu-id="d8b85-249">右键单击 "*项目" 面板* 中的 "**资产**" 文件夹，然后选择 "**创建**  >  **文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-249">Right-click on the **Assets** folder in the *Project Panel*, then select **Create** > **Folder**.</span></span> <span data-ttu-id="d8b85-250">命名文件夹 **脚本**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="d8b85-251">打开 "**脚本**" 文件夹，然后在该文件夹中右键单击 "**创建**  >  **c # 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-251">Open the **Scripts** folder then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="d8b85-252">将脚本命名为 **MeetingsUI。**</span><span class="sxs-lookup"><span data-stu-id="d8b85-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="d8b85-253">双击新的 **MeetingsUI** 脚本以通过 *Visual Studio* 打开它。</span><span class="sxs-lookup"><span data-stu-id="d8b85-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="d8b85-254">插入以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="d8b85-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="d8b85-255">在类中插入以下变量：</span><span class="sxs-lookup"><span data-stu-id="d8b85-255">Inside the class insert the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  <span data-ttu-id="d8b85-256">然后替换 **Start ()** 方法，并添加一个 **唤醒的 ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="d8b85-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="d8b85-257">当类初始化时，将调用以下内容：</span><span class="sxs-lookup"><span data-stu-id="d8b85-257">These will be called when the class initializes:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  <span data-ttu-id="d8b85-258">添加负责创建 *会议 UI* 的方法，并在请求时向其填充当前会议：</span><span class="sxs-lookup"><span data-stu-id="d8b85-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. <span data-ttu-id="d8b85-259">**删除** () 方法的 **更新** ，并在 Visual Studio 返回到 Unity 之前 **保存更改** 。</span><span class="sxs-lookup"><span data-stu-id="d8b85-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="d8b85-260">第6章-创建图形类</span><span class="sxs-lookup"><span data-stu-id="d8b85-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="d8b85-261">要创建的下一个脚本是 **图形** 脚本。</span><span class="sxs-lookup"><span data-stu-id="d8b85-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="d8b85-262">此脚本负责进行调用以对用户进行身份验证，并从用户日历中检索当天的计划会议。</span><span class="sxs-lookup"><span data-stu-id="d8b85-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="d8b85-263">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="d8b85-263">To create this class:</span></span>

1.  <span data-ttu-id="d8b85-264">双击 " **脚本** " 文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="d8b85-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="d8b85-265">右键单击 "**脚本**" 文件夹中，单击 "**创建**  >  **c # 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="d8b85-266">将脚本命名为 **Graph**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="d8b85-267">双击脚本以通过 Visual Studio 打开它。</span><span class="sxs-lookup"><span data-stu-id="d8b85-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="d8b85-268">插入以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="d8b85-268">Insert the following namespaces:</span></span>

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="d8b85-269">你将注意到，此脚本中的部分代码围绕 [预编译指令](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)环绕，这是为了避免生成 Visual Studio 解决方案时库出现问题。</span><span class="sxs-lookup"><span data-stu-id="d8b85-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="d8b85-270">删除 **开始 ()** 并 **更新 ()** 方法，因为它们不会被使用。</span><span class="sxs-lookup"><span data-stu-id="d8b85-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="d8b85-271">在 **图形** 类外部，插入以下对象，这些对象是反序列化表示每日计划会议的 JSON 对象所必需的：</span><span class="sxs-lookup"><span data-stu-id="d8b85-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  <span data-ttu-id="d8b85-272">在 **图形** 类中，添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="d8b85-272">Inside the **Graph** class, add the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > <span data-ttu-id="d8b85-273">将 **appId** 值更改为你在 **第 [1 章](#chapter-1---create-your-app-in-the-application-registration-portal)步骤 4** 中记下的 **应用 Id** 。</span><span class="sxs-lookup"><span data-stu-id="d8b85-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="d8b85-274">此值应与应用程序注册页面中显示的应用程序注册 **门户** 中的值相同。</span><span class="sxs-lookup"><span data-stu-id="d8b85-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="d8b85-275">在 **Graph** 类中，添加方法 **SignInAsync ()** 和 **AquireTokenAsync ()**，这将提示用户插入登录凭据。</span><span class="sxs-lookup"><span data-stu-id="d8b85-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successful, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  <span data-ttu-id="d8b85-276">添加以下两个方法：</span><span class="sxs-lookup"><span data-stu-id="d8b85-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="d8b85-277">**BuildTodayCalendarEndpoint ()**，用于生成指定在其中检索计划会议的日期和时间范围的 URI。</span><span class="sxs-lookup"><span data-stu-id="d8b85-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="d8b85-278">**ListMeetingsAsync ()**，它从 *Microsoft Graph* 请求计划会议。</span><span class="sxs-lookup"><span data-stu-id="d8b85-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. <span data-ttu-id="d8b85-279">你现在已经完成了 **图形** 脚本。</span><span class="sxs-lookup"><span data-stu-id="d8b85-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="d8b85-280">在返回到 Unity 之前，在 Visual Studio 中 **保存更改**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="d8b85-281">第7章-创建 GazeInput 脚本</span><span class="sxs-lookup"><span data-stu-id="d8b85-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="d8b85-282">现在会创建 **GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="d8b85-283">此类处理并跟踪用户的注视，并使用 **Raycast** 来自 **主摄像机** 的 "向前投影"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="d8b85-284">创建脚本：</span><span class="sxs-lookup"><span data-stu-id="d8b85-284">To create the script:</span></span>

1.  <span data-ttu-id="d8b85-285">双击 " **脚本** " 文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="d8b85-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="d8b85-286">右键单击 "**脚本**" 文件夹中，单击 "**创建**  >  **c # 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="d8b85-287">将脚本命名为 **GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="d8b85-288">双击脚本以通过 Visual Studio 打开它。</span><span class="sxs-lookup"><span data-stu-id="d8b85-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="d8b85-289">更改命名空间代码以匹配下面的代码，并 **\[ \] 将 "GazeInput" 标记** 添加到你的类的上方，以便能够对其进行序列化：</span><span class="sxs-lookup"><span data-stu-id="d8b85-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="d8b85-290">在 **GazeInput** 类中，添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="d8b85-290">Inside the **GazeInput** class, add the following variables:</span></span>

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  <span data-ttu-id="d8b85-291">将 **CreateCursor ()** 方法添加到场景中，并从 **Start ()** 方法调用方法：</span><span class="sxs-lookup"><span data-stu-id="d8b85-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  <span data-ttu-id="d8b85-292">下面的方法可启用注视 Raycast 并跟踪聚焦对象。</span><span class="sxs-lookup"><span data-stu-id="d8b85-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
                HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;
                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="d8b85-293">在返回到 Unity 之前，在 Visual Studio 中 **保存更改**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="d8b85-294">第8章-创建交互类</span><span class="sxs-lookup"><span data-stu-id="d8b85-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="d8b85-295">你现在需要创建 **交互** 脚本，该脚本负责：</span><span class="sxs-lookup"><span data-stu-id="d8b85-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="d8b85-296">处理 **点击** 交互和 **照相机注视**，使用户能够与场景中的 "button" 中的日志交互。</span><span class="sxs-lookup"><span data-stu-id="d8b85-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="d8b85-297">在场景中的 "button" 对象中创建用于用户交互的日志。</span><span class="sxs-lookup"><span data-stu-id="d8b85-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="d8b85-298">创建脚本：</span><span class="sxs-lookup"><span data-stu-id="d8b85-298">To create the script:</span></span>

1.  <span data-ttu-id="d8b85-299">双击 " **脚本** " 文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="d8b85-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="d8b85-300">右键单击 "**脚本**" 文件夹中，单击 "**创建**  >  **c # 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="d8b85-301">命名脚本 **交互**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="d8b85-302">双击脚本以通过 Visual Studio 打开它。</span><span class="sxs-lookup"><span data-stu-id="d8b85-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="d8b85-303">插入以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="d8b85-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="d8b85-304">将 **交互** 类的继承从 *MonoBehaviour* 更改为 **GazeInput**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="d8b85-305">~~公共类交互： MonoBehaviour~~</span><span class="sxs-lookup"><span data-stu-id="d8b85-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="d8b85-306">在 **交互** 类中插入以下变量：</span><span class="sxs-lookup"><span data-stu-id="d8b85-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="d8b85-307">替换 **Start** 方法;请注意，它是一个重写方法，它调用 "基" 注视类方法。</span><span class="sxs-lookup"><span data-stu-id="d8b85-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="d8b85-308">在类初始化、注册输入识别并在场景中创建 "登录"*按钮* 时，将调用 **Start ()** ：</span><span class="sxs-lookup"><span data-stu-id="d8b85-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  <span data-ttu-id="d8b85-309">添加 **CreateSignInButton ()** 方法，该方法将实例化场景中的 "登录" *按钮* 并设置其属性：</span><span class="sxs-lookup"><span data-stu-id="d8b85-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  <span data-ttu-id="d8b85-310">添加 **GestureRecognizer_Tapped ()** 方法，该方法将响应 *点击* 用户事件。</span><span class="sxs-lookup"><span data-stu-id="d8b85-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. <span data-ttu-id="d8b85-311">**删除** () 方法的 **更新** ，然后在 Visual Studio 返回到 Unity 之前 **保存更改** 。</span><span class="sxs-lookup"><span data-stu-id="d8b85-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="d8b85-312">第9章-设置脚本引用</span><span class="sxs-lookup"><span data-stu-id="d8b85-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="d8b85-313">在本章中，需要将 **交互** 脚本放到 **主摄像机** 上。</span><span class="sxs-lookup"><span data-stu-id="d8b85-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="d8b85-314">然后，该脚本会处理需要的其他脚本。</span><span class="sxs-lookup"><span data-stu-id="d8b85-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="d8b85-315">从 "*项目" 面板* 的 "**脚本**" 文件夹中，将脚本 **交互** 拖动到 "**相机**" 对象，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d8b85-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="d8b85-316">第10章-设置标记</span><span class="sxs-lookup"><span data-stu-id="d8b85-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="d8b85-317">处理注视的代码将使用标记 **SignInButton** 来标识用户将与之交互的对象，以便登录 *Microsoft Graph*。</span><span class="sxs-lookup"><span data-stu-id="d8b85-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="d8b85-318">若要创建标记：</span><span class="sxs-lookup"><span data-stu-id="d8b85-318">To create the Tag:</span></span>

1.  <span data-ttu-id="d8b85-319">在 Unity 编辑器中，单击 "*层次结构" 面板* 中的 **主相机**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="d8b85-320">在 *检查器面板* 中，单击 " **MainCamera** " *标记* 以打开下拉列表。</span><span class="sxs-lookup"><span data-stu-id="d8b85-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="d8b85-321">单击 "**添加标记 ...** "</span><span class="sxs-lookup"><span data-stu-id="d8b85-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="d8b85-322">单击该 **+** 按钮。</span><span class="sxs-lookup"><span data-stu-id="d8b85-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="d8b85-323">将标记名称写入为 **SignInButton** ，然后单击 "保存"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="d8b85-324">第11章-将 Unity 项目生成到 UWP</span><span class="sxs-lookup"><span data-stu-id="d8b85-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="d8b85-325">此项目的 Unity 部分所需的所有内容现在均已完成，因此可以从 Unity 构建它。</span><span class="sxs-lookup"><span data-stu-id="d8b85-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="d8b85-326">导航到 " *生成设置* " ( "*文件* > \* 生成设置 \* \* ) "。</span><span class="sxs-lookup"><span data-stu-id="d8b85-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="d8b85-327">如果尚未这样做，请勾选 **Unity C \# 项目**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="d8b85-328">单击“生成”。</span><span class="sxs-lookup"><span data-stu-id="d8b85-328">Click **Build**.</span></span> <span data-ttu-id="d8b85-329">Unity 将启动 **文件资源管理器** 窗口，在该窗口中，需要创建一个文件夹，然后选择要在其中生成应用的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d8b85-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="d8b85-330">立即创建该文件夹并将其命名为 **应用**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="d8b85-331">选择 **应用** 文件夹后，单击 " **选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="d8b85-332">Unity 将开始向 **应用** 文件夹生成项目。</span><span class="sxs-lookup"><span data-stu-id="d8b85-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="d8b85-333">Unity 完成生成后 (可能需要一些时间) ，它将在你的生成的位置上打开 " **文件资源管理器** " 窗口 (检查任务栏，因为它可能不会始终出现在 windows 上，但会通知你添加了新的窗口) 。</span><span class="sxs-lookup"><span data-stu-id="d8b85-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="d8b85-334">第12章-部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="d8b85-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="d8b85-335">在 HoloLens 上部署：</span><span class="sxs-lookup"><span data-stu-id="d8b85-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="d8b85-336">需要为远程部署) 提供 HoloLens (的 IP 地址，并确保 HoloLens 处于 **开发人员模式。**</span><span class="sxs-lookup"><span data-stu-id="d8b85-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="d8b85-337">要执行此操作：</span><span class="sxs-lookup"><span data-stu-id="d8b85-337">To do this:</span></span>

    1.  <span data-ttu-id="d8b85-338">在戴上 HoloLens 的同时，请打开 **设置**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="d8b85-339">中转到 **网络 & Internet**  >  **wi-fi**  >  **高级选项**</span><span class="sxs-lookup"><span data-stu-id="d8b85-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="d8b85-340">记下 **IPv4** 地址。</span><span class="sxs-lookup"><span data-stu-id="d8b85-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="d8b85-341">接下来，导航回 "**设置**"，然后为  >  **开发人员** 更新 & 安全性</span><span class="sxs-lookup"><span data-stu-id="d8b85-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="d8b85-342">设置 **开发人员模式**。</span><span class="sxs-lookup"><span data-stu-id="d8b85-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="d8b85-343">导航到新的 Unity 生成 (**应用** 文件夹) 并通过 **Visual Studio** 打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="d8b85-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="d8b85-344">在 **解决方案配置** 中，选择 " **调试**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="d8b85-345">在 **解决方案平台** 中，选择 " **X86，远程计算机**"。</span><span class="sxs-lookup"><span data-stu-id="d8b85-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="d8b85-346">系统将提示你插入远程设备的 **IP 地址** (HoloLens，在本例中，你记) 。</span><span class="sxs-lookup"><span data-stu-id="d8b85-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="d8b85-347">中转到 " **生成** " 菜单，然后单击 " **部署解决方案** "，将应用程序旁加载到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="d8b85-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="d8b85-348">应用现在应显示在你的 HoloLens 上已安装的应用列表中，可以启动了！</span><span class="sxs-lookup"><span data-stu-id="d8b85-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="d8b85-349">Microsoft Graph HoloLens 应用程序</span><span class="sxs-lookup"><span data-stu-id="d8b85-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="d8b85-350">恭喜，你构建了一个利用 Microsoft Graph 的混合现实应用来读取和显示用户日历数据。</span><span class="sxs-lookup"><span data-stu-id="d8b85-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="d8b85-351">额外练习</span><span class="sxs-lookup"><span data-stu-id="d8b85-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="d8b85-352">练习 1</span><span class="sxs-lookup"><span data-stu-id="d8b85-352">Exercise 1</span></span>

<span data-ttu-id="d8b85-353">使用 Microsoft Graph 显示有关用户的其他信息</span><span class="sxs-lookup"><span data-stu-id="d8b85-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="d8b85-354">用户电子邮件/电话号码/个人资料图片</span><span class="sxs-lookup"><span data-stu-id="d8b85-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="d8b85-355">练习 1</span><span class="sxs-lookup"><span data-stu-id="d8b85-355">Exercise 1</span></span>

<span data-ttu-id="d8b85-356">实现语音控制以导航 Microsoft Graph UI。</span><span class="sxs-lookup"><span data-stu-id="d8b85-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>