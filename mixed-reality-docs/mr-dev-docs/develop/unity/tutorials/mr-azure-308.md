---
title: HoloLens (第一代) 和 Azure 308-跨设备通知
description: 完成本课程，了解如何在混合现实应用程序中实现 Azure 通知中心、Azure Functions 以及 Azure 存储和表。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合现实，学院，unity，教程，api，通知，函数，表，通知中心，hololens，沉浸，vr，Windows 10，Visual Studio
ms.openlocfilehash: 8fef7fe2da76e228264037ca51daa57662fbc554
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730584"
---
# <a name="hololens-1st-gen-and-azure-308-cross-device-notifications"></a><span data-ttu-id="26eec-104">HoloLens (第一代) 和 Azure 308：跨设备通知</span><span class="sxs-lookup"><span data-stu-id="26eec-104">HoloLens (1st gen) and Azure 308: Cross-device notifications</span></span>

<br>

>[!NOTE]
><span data-ttu-id="26eec-105">混合现实学院教程在制作时考虑到了 HoloLens（第一代）和混合现实沉浸式头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="26eec-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="26eec-106">因此，对于仍在寻求这些设备的开发指导的开发人员而言，我们觉得很有必要保留这些教程。</span><span class="sxs-lookup"><span data-stu-id="26eec-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="26eec-107">我们 **不会** 在这些教程中更新 HoloLens 2 所用的最新工具集或集成相关的内容。</span><span class="sxs-lookup"><span data-stu-id="26eec-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="26eec-108">我们将维护这些教程，使之持续适用于支持的设备。</span><span class="sxs-lookup"><span data-stu-id="26eec-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="26eec-109">将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="26eec-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="26eec-110">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="26eec-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

![最终产品-启动](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="26eec-112">在本课程中，你将学习如何使用 Azure 通知中心、Azure 表和 Azure Functions 向混合现实应用程序添加通知中心功能。</span><span class="sxs-lookup"><span data-stu-id="26eec-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="26eec-113">**Azure 通知中心** 是一种 Microsoft 服务，它允许开发人员将有针对性的个性化推送通知发送到所有平台，并将其放入云中。</span><span class="sxs-lookup"><span data-stu-id="26eec-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="26eec-114">这可以有效地允许开发人员与最终用户通信，甚至可以在各种应用程序之间进行通信，具体取决于方案。</span><span class="sxs-lookup"><span data-stu-id="26eec-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="26eec-115">有关详细信息，请访问 **Azure 通知中心**[页](/azure/notification-hubs/notification-hubs-push-notification-overview)。</span><span class="sxs-lookup"><span data-stu-id="26eec-115">For more information, visit the **Azure Notification Hubs** [page](/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="26eec-116">**Azure Functions** 是一项 Microsoft 服务，它允许开发人员在 Azure 中运行少量的代码 "函数"。</span><span class="sxs-lookup"><span data-stu-id="26eec-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="26eec-117">这提供了一种方法，可将工作委托给云，而不是本地应用程序，这可能有很多好处。</span><span class="sxs-lookup"><span data-stu-id="26eec-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="26eec-118">**Azure Functions** 支持多种开发语言，包括 C \# 、F \# 、Node.js、Java 和 PHP。</span><span class="sxs-lookup"><span data-stu-id="26eec-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="26eec-119">有关详细信息，请访问 **Azure Functions** [页](/azure/azure-functions/functions-overview)。</span><span class="sxs-lookup"><span data-stu-id="26eec-119">For more information, visit the **Azure Functions** [page](/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="26eec-120">**Azure 表** 是一种 Microsoft 云服务，可让开发人员在云中存储结构化非 SQL 数据，使其在任何地方都可以轻松访问。</span><span class="sxs-lookup"><span data-stu-id="26eec-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="26eec-121">该服务的设计无架构，可根据需要进行表的发展，因此非常灵活。</span><span class="sxs-lookup"><span data-stu-id="26eec-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="26eec-122">有关详细信息，请访问 **Azure 表**[页](/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="26eec-122">For more information, visit the **Azure Tables** [page](/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="26eec-123">完成本课程后，你将拥有一个混合现实沉浸式头戴式耳机应用程序和一个台式 PC 应用程序，该应用程序将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="26eec-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="26eec-124">桌面电脑应用将允许用户使用鼠标将对象移动到 (X 和 Y) 的2D 空间。</span><span class="sxs-lookup"><span data-stu-id="26eec-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="26eec-125">将使用 JSON 将对象移动到云中，其格式为字符串，其中包含一个对象 ID、类型和转换信息 (X 和 Y 坐标) 。</span><span class="sxs-lookup"><span data-stu-id="26eec-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="26eec-126">对于桌面应用程序具有相同场景的混合现实应用，会收到有关对象移动的通知，从通知中心服务 (，该应用刚刚由桌面 PC 应用) 更新。</span><span class="sxs-lookup"><span data-stu-id="26eec-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="26eec-127">收到包含对象 ID、类型和转换信息的通知后，混合现实应用会将接收到的信息应用到其自身的场景。</span><span class="sxs-lookup"><span data-stu-id="26eec-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="26eec-128">在您的应用程序中，您将由您来决定如何将结果与您的设计相集成。</span><span class="sxs-lookup"><span data-stu-id="26eec-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="26eec-129">本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。</span><span class="sxs-lookup"><span data-stu-id="26eec-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="26eec-130">您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。</span><span class="sxs-lookup"><span data-stu-id="26eec-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="26eec-131">本课程是一个自包含教程，并不直接涉及任何其他混合现实实验室。</span><span class="sxs-lookup"><span data-stu-id="26eec-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="26eec-132">设备支持</span><span class="sxs-lookup"><span data-stu-id="26eec-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="26eec-133">课程</span><span class="sxs-lookup"><span data-stu-id="26eec-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="26eec-134"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="26eec-134"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="26eec-135"><a href="../../../discover/immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="26eec-135"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="26eec-136">MR 和 Azure 308：跨设备通知</span><span class="sxs-lookup"><span data-stu-id="26eec-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="26eec-137">✔️</span><span class="sxs-lookup"><span data-stu-id="26eec-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="26eec-138">✔️</span><span class="sxs-lookup"><span data-stu-id="26eec-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="26eec-139">尽管本课程主要侧重于 Windows Mixed Reality 沉浸式 (VR) 耳机，但你也可以将本课程中学习的内容应用于 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="26eec-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="26eec-140">在本课程中，你将看到有关支持 HoloLens 时可能需要执行的任何更改的说明。</span><span class="sxs-lookup"><span data-stu-id="26eec-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="26eec-141">使用 HoloLens 时，可能会在语音捕获过程中注意到某些回声。</span><span class="sxs-lookup"><span data-stu-id="26eec-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="26eec-142">必备条件</span><span class="sxs-lookup"><span data-stu-id="26eec-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="26eec-143">本教程专为具有 Unity 和 c # 基本经验的开发人员设计。</span><span class="sxs-lookup"><span data-stu-id="26eec-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="26eec-144">请注意，本文档中的先决条件和书面说明表明了编写 (2018) 时测试和验证的内容。</span><span class="sxs-lookup"><span data-stu-id="26eec-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="26eec-145">您可以随意使用最新的软件（如 [安装工具](../../install-the-tools.md) 一文中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="26eec-145">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="26eec-146">本课程建议采用以下硬件和软件：</span><span class="sxs-lookup"><span data-stu-id="26eec-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="26eec-147">[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC，适用于沉浸式 (VR) 耳机开发</span><span class="sxs-lookup"><span data-stu-id="26eec-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="26eec-148">Windows 10 秋季创意者更新 (或更高版本启用了开发人员模式) </span><span class="sxs-lookup"><span data-stu-id="26eec-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="26eec-149">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="26eec-149">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="26eec-150">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="26eec-150">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="26eec-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="26eec-151">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="26eec-152">[Windows Mixed Reality 沉浸式 (VR) 耳机](../../../discover/immersive-headset-hardware-details.md)或[Microsoft HoloLens](/hololens/hololens1-hardware) ，启用了开发人员模式</span><span class="sxs-lookup"><span data-stu-id="26eec-152">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](/hololens/hololens1-hardware) with Developer mode enabled</span></span>
- <span data-ttu-id="26eec-153">Azure 安装和访问通知中心的 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="26eec-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="26eec-154">开始之前</span><span class="sxs-lookup"><span data-stu-id="26eec-154">Before you start</span></span>

- <span data-ttu-id="26eec-155">若要避免在生成此项目时遇到问题，强烈建议你在根或近乎根文件夹中创建本教程中所述的项目 (长文件夹路径在生成时) 会导致问题。</span><span class="sxs-lookup"><span data-stu-id="26eec-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="26eec-156">你必须是 Microsoft 开发人员门户和应用程序注册门户的所有者，否则你将不具有访问 [第2章](#chapter-2---retrieve-your-new-apps-credentials)中的应用的权限。</span><span class="sxs-lookup"><span data-stu-id="26eec-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="26eec-157">第1章-在 Microsoft 开发人员门户中创建应用程序</span><span class="sxs-lookup"><span data-stu-id="26eec-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="26eec-158">若要使用 **Azure 通知中心** 服务，你将需要在 Microsoft 开发人员门户中创建一个应用程序，因为你的应用程序将需要注册，以便它能够发送和接收通知。</span><span class="sxs-lookup"><span data-stu-id="26eec-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="26eec-159">登录到 [Microsoft 开发人员门户](https://developer.microsoft.com/dashboard)。</span><span class="sxs-lookup"><span data-stu-id="26eec-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="26eec-160">你将需要登录到你的 Microsoft 帐户。</span><span class="sxs-lookup"><span data-stu-id="26eec-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="26eec-161">在仪表板中，单击 " **创建新应用**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-161">From the Dashboard, click **Create a new app**.</span></span>

    ![创建应用](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="26eec-163">将显示一个弹出窗口，需要为新应用保留一个名称。</span><span class="sxs-lookup"><span data-stu-id="26eec-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="26eec-164">在文本框中，插入一个适当的名称;如果所选名称可用，则勾选标记将显示在文本框的右侧。</span><span class="sxs-lookup"><span data-stu-id="26eec-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="26eec-165">插入可用名称后，单击弹出窗口左下角的 " **保留产品名称** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="26eec-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![反转名称](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="26eec-167">创建应用后，你可以转到下一章节。</span><span class="sxs-lookup"><span data-stu-id="26eec-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="26eec-168">第2章-检索新的应用凭据</span><span class="sxs-lookup"><span data-stu-id="26eec-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="26eec-169">登录到应用程序注册门户，其中将列出新应用程序，并检索将用于在 **Azure 门户** 中设置 **通知中心服务** 的凭据。</span><span class="sxs-lookup"><span data-stu-id="26eec-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="26eec-170">导航到 [应用程序注册门户](https://apps.dev.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="26eec-170">Navigate to the [Application Registration Portal](https://apps.dev.microsoft.com).</span></span>

    ![应用程序注册门户](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="26eec-172">你将需要使用 Microsoft 帐户进行登录。</span><span class="sxs-lookup"><span data-stu-id="26eec-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="26eec-173">这 **必须** 是上一 [章](#chapter-1---create-an-application-on-the-microsoft-developer-portal)使用 Windows 应用商店开发人员门户时使用的 Microsoft 帐户。</span><span class="sxs-lookup"><span data-stu-id="26eec-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="26eec-174">你将在 " **我的应用程序** " 部分下找到你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="26eec-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="26eec-175">找到后，单击它，随即会转到新页面，其中包含应用名称和 **注册**。</span><span class="sxs-lookup"><span data-stu-id="26eec-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![新注册的应用](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="26eec-177">向下滚动注册页面，找到 **应用程序的机密** 部分和 **包 SID** 。</span><span class="sxs-lookup"><span data-stu-id="26eec-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="26eec-178">复制这两个用于在下一章中设置 **Azure 通知中心服务** 。</span><span class="sxs-lookup"><span data-stu-id="26eec-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![应用程序机密](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="26eec-180">第3章-设置 Azure 门户：创建通知中心服务</span><span class="sxs-lookup"><span data-stu-id="26eec-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="26eec-181">检索应用凭据后，你将需要在 Azure 门户中创建 Azure 通知中心服务。</span><span class="sxs-lookup"><span data-stu-id="26eec-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="26eec-182">登录到 [Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="26eec-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="26eec-183">如果还没有 Azure 帐户，则需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="26eec-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="26eec-184">如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。</span><span class="sxs-lookup"><span data-stu-id="26eec-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="26eec-185">登录后，单击左上角的 " **新建** "，搜索 " **通知中心**"，然后单击 " **_输入_**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click **_Enter_**.</span></span>

    ![搜索通知中心](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="26eec-187">在较新的门户中，可以使用 _ \* Create a 资源 \* \* 来替换 word \***New** _。</span><span class="sxs-lookup"><span data-stu-id="26eec-187">The word ***New** _ may have been replaced with _*Create a resource\*\*, in newer portals.</span></span>

3.  <span data-ttu-id="26eec-188">新页将提供 *通知中心* 服务的说明。</span><span class="sxs-lookup"><span data-stu-id="26eec-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="26eec-189">在此提示符下，选择 " **创建** " 按钮以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="26eec-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![创建通知中心实例](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="26eec-191">单击 " ***创建***" 后：</span><span class="sxs-lookup"><span data-stu-id="26eec-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="26eec-192">为此服务实例插入所需的名称。</span><span class="sxs-lookup"><span data-stu-id="26eec-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="26eec-193">提供可与此应用关联的 **命名空间** 。</span><span class="sxs-lookup"><span data-stu-id="26eec-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="26eec-194">选择一个 **位置。**</span><span class="sxs-lookup"><span data-stu-id="26eec-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="26eec-195">选择一个 **资源组** ，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="26eec-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="26eec-196">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="26eec-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="26eec-197">建议保留与单个项目关联的所有 Azure 服务 (例如，这些实验室) 在常见资源组) 下。</span><span class="sxs-lookup"><span data-stu-id="26eec-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="26eec-198">如果希望了解有关 Azure 资源组的详细信息，请参阅此 [链接，了解如何管理资源组](/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="26eec-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="26eec-199">选择相应的 **订阅**。</span><span class="sxs-lookup"><span data-stu-id="26eec-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="26eec-200">还需要确认是否已了解应用于此服务的条款和条件。</span><span class="sxs-lookup"><span data-stu-id="26eec-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="26eec-201">选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="26eec-201">Select **Create**.</span></span>

        ![填写服务详细信息](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="26eec-203">单击 " **创建**" 后，需要等待创建服务，这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="26eec-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="26eec-204">创建服务实例后，门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="26eec-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![通知](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="26eec-206">单击通知中的 " **中转到资源** " 按钮以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="26eec-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="26eec-207">你将转到新的 **通知中心** 服务实例。</span><span class="sxs-lookup"><span data-stu-id="26eec-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![中转到资源](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="26eec-209">从 "概述" 页中，单击 " **Windows (WNS") 。**</span><span class="sxs-lookup"><span data-stu-id="26eec-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="26eec-210">右侧面板将更改为显示两个文本字段，它们需要你之前设置的应用中的 **包 SID** 和 **安全密钥**。</span><span class="sxs-lookup"><span data-stu-id="26eec-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![新创建的集线器服务](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="26eec-212">将详细信息复制到正确的字段后，请单击 " **保存**"，在成功更新通知中心后，将收到通知。</span><span class="sxs-lookup"><span data-stu-id="26eec-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![复制安全详细信息](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="26eec-214">第4章-设置 Azure 门户：创建表服务</span><span class="sxs-lookup"><span data-stu-id="26eec-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="26eec-215">创建通知中心服务实例后，请导航回 Azure 门户，以便通过创建存储资源来创建 Azure 表服务。</span><span class="sxs-lookup"><span data-stu-id="26eec-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="26eec-216">如果尚未登录，请登录到 [Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="26eec-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="26eec-217">登录后，单击左上角的 " **新建** "，然后搜索 " **存储帐户**"，然后单击 " **Enter**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="26eec-218">在较新的门户中，可以使用 _ \* Create a 资源 \* \* 来替换 word \***New** _。</span><span class="sxs-lookup"><span data-stu-id="26eec-218">The word ***New** _ may have been replaced with _*Create a resource\*\*, in newer portals.</span></span>

3.  <span data-ttu-id="26eec-219">从列表中选择 " **存储帐户-blob、文件、表、队列** "。</span><span class="sxs-lookup"><span data-stu-id="26eec-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![搜索存储帐户](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="26eec-221">新页将提供 **存储帐户** 服务的说明。</span><span class="sxs-lookup"><span data-stu-id="26eec-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="26eec-222">在此提示符下，选择 " **创建** " 按钮，创建此服务的实例。</span><span class="sxs-lookup"><span data-stu-id="26eec-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![创建存储实例](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="26eec-224">单击 " **创建**" 后，将显示一个面板：</span><span class="sxs-lookup"><span data-stu-id="26eec-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="26eec-225">为此服务实例插入所需的 **名称** ， (必须全部为小写) 。</span><span class="sxs-lookup"><span data-stu-id="26eec-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="26eec-226">对于 **部署模型**，单击 " **资源管理器**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="26eec-227">对于 " **帐户类型**"，请使用下拉菜单，选择 " **存储 (常规用途 v1)**。</span><span class="sxs-lookup"><span data-stu-id="26eec-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="26eec-228">选择适当的 **位置**。</span><span class="sxs-lookup"><span data-stu-id="26eec-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="26eec-229">对于 " **复制** " 下拉菜单，选择 " **读取-访问-异地冗余存储 (GRS)**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="26eec-230">对于 " **性能**"，请单击 " **标准**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="26eec-231">在 " **需要安全传输** " 部分中，选择 " **禁用**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="26eec-232">从 " **订阅** " 下拉菜单中，选择相应的订阅。</span><span class="sxs-lookup"><span data-stu-id="26eec-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="26eec-233">选择一个 **资源组** ，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="26eec-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="26eec-234">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="26eec-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="26eec-235">建议保留与单个项目关联的所有 Azure 服务 (例如，这些实验室) 在常见资源组) 下。</span><span class="sxs-lookup"><span data-stu-id="26eec-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="26eec-236">如果希望了解有关 Azure 资源组的详细信息，请参阅此 [链接，了解如何管理资源组](/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="26eec-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="26eec-237">如果这是一个选项，请将 **虚拟网络** 保持为 **禁用状态** 。</span><span class="sxs-lookup"><span data-stu-id="26eec-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="26eec-238">单击 **“创建”** 。</span><span class="sxs-lookup"><span data-stu-id="26eec-238">Click **Create**.</span></span>

        ![填写存储详细信息](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="26eec-240">单击 " **创建**" 后，需要等待创建服务，这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="26eec-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="26eec-241">创建服务实例后，门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="26eec-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="26eec-242">单击通知以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="26eec-242">Click on the notifications to explore your new Service instance.</span></span>

    ![新存储通知](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="26eec-244">单击通知中的 " **中转到资源** " 按钮以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="26eec-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="26eec-245">你将转到新的存储服务实例概述页。</span><span class="sxs-lookup"><span data-stu-id="26eec-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![中转到资源](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="26eec-247">在 "概述" 页中，单击右侧的 " **表**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="26eec-248">右侧面板将更改为显示 **表服务** 信息，你需要添加一个新表。</span><span class="sxs-lookup"><span data-stu-id="26eec-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="26eec-249">单击左上角的 "表" 按钮即可执行此操作 **+**  。</span><span class="sxs-lookup"><span data-stu-id="26eec-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![打开表](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="26eec-251">将显示一个新页，需要在其中输入 **表名称**。</span><span class="sxs-lookup"><span data-stu-id="26eec-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="26eec-252">这是将在后面章节中用于引用应用程序中的数据的名称。</span><span class="sxs-lookup"><span data-stu-id="26eec-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="26eec-253">插入适当的名称，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="26eec-253">Insert an appropriate name and click **OK**.</span></span>

    ![创建新表](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="26eec-255">创建新表后，可在 " **表服务** " 页的底部)  (查看它。</span><span class="sxs-lookup"><span data-stu-id="26eec-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![已创建新表](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="26eec-257">第5章-完成 Visual Studio 中的 Azure 表</span><span class="sxs-lookup"><span data-stu-id="26eec-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="26eec-258">由于已设置了 **表服务** 存储帐户，因此可以向其添加数据，这将用于存储和检索信息。</span><span class="sxs-lookup"><span data-stu-id="26eec-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="26eec-259">可以通过 **Visual Studio** 来编辑表。</span><span class="sxs-lookup"><span data-stu-id="26eec-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="26eec-260">打开 **Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="26eec-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="26eec-261">从菜单中，单击 "**查看**  >  **Cloud Explorer**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-261">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![打开 cloud explorer](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="26eec-263">**Cloud Explorer** 将作为停靠项打开 (患者，因为加载可能需要一些时间) 。</span><span class="sxs-lookup"><span data-stu-id="26eec-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="26eec-264">如果用于创建 *存储帐户* 的订阅不可见，请确保：</span><span class="sxs-lookup"><span data-stu-id="26eec-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="26eec-265">已登录到与 Azure 门户一起使用的帐户。</span><span class="sxs-lookup"><span data-stu-id="26eec-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="26eec-266">从 "帐户管理" 页中选择了你的订阅 (你可能需要从帐户设置) 应用筛选器：</span><span class="sxs-lookup"><span data-stu-id="26eec-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![查找订阅](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="26eec-268">将显示你的 Azure 云服务。</span><span class="sxs-lookup"><span data-stu-id="26eec-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="26eec-269">查找 **存储帐户** ，并单击其左侧的箭头以展开你的帐户。</span><span class="sxs-lookup"><span data-stu-id="26eec-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![打开存储帐户](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="26eec-271">展开后，新创建的 **存储帐户** 应该可用。</span><span class="sxs-lookup"><span data-stu-id="26eec-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="26eec-272">单击存储左侧的箭头，然后在展开后，查找 " **表** " 并单击该按钮旁边的箭头，以显示在上一章中创建的 **表** 。</span><span class="sxs-lookup"><span data-stu-id="26eec-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="26eec-273">双击 **表**。</span><span class="sxs-lookup"><span data-stu-id="26eec-273">Double click your **Table**.</span></span>

    ![打开场景对象表](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="26eec-275">您的表将在您的 Visual Studio 窗口的中心打开。</span><span class="sxs-lookup"><span data-stu-id="26eec-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="26eec-276">单击带有 **+** (加) 的表图标。</span><span class="sxs-lookup"><span data-stu-id="26eec-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![添加新表](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="26eec-278">将显示一个窗口，提示你 *添加实体*。</span><span class="sxs-lookup"><span data-stu-id="26eec-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="26eec-279">您将创建三个实体，每个实体都有多个属性。</span><span class="sxs-lookup"><span data-stu-id="26eec-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="26eec-280">你会注意到已提供了 *PartitionKey* 和 *RowKey* ，因为表使用这些方法来查找数据。</span><span class="sxs-lookup"><span data-stu-id="26eec-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![分区和行键](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="26eec-282">按如下所示更新 **PartitionKey** 和 **RowKey** 的 *值* (记得为你添加的每个行属性执行此操作，但每次) 递增 RowKey：</span><span class="sxs-lookup"><span data-stu-id="26eec-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![添加正确的值](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="26eec-284">单击 " **添加属性** " 以添加额外的数据行。</span><span class="sxs-lookup"><span data-stu-id="26eec-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="26eec-285">使第一个空表与下表匹配。</span><span class="sxs-lookup"><span data-stu-id="26eec-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="26eec-286">完成后，单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="26eec-286">Click **OK** when you are finished.</span></span>

    ![完成后单击 "确定"](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="26eec-288">确保将 **X**、 **Y** 和 **Z** 条目的 **类型** 更改为 **Double**。</span><span class="sxs-lookup"><span data-stu-id="26eec-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="26eec-289">你会注意到，你的表现在具有一行数据。</span><span class="sxs-lookup"><span data-stu-id="26eec-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="26eec-290">再次单击 **+** (加号) 图标以添加另一个实体。</span><span class="sxs-lookup"><span data-stu-id="26eec-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![第一行](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="26eec-292">创建其他属性，然后将新实体的值设置为与下面显示的值相匹配。</span><span class="sxs-lookup"><span data-stu-id="26eec-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![添加多维数据集](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="26eec-294">重复上一步以添加另一个实体。</span><span class="sxs-lookup"><span data-stu-id="26eec-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="26eec-295">将此实体的值设置为下面显示的值。</span><span class="sxs-lookup"><span data-stu-id="26eec-295">Set the values for this entity to those shown below.</span></span>

    ![添加圆柱体](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="26eec-297">现在，你的表应如下所示。</span><span class="sxs-lookup"><span data-stu-id="26eec-297">Your table should now look like the one below.</span></span>

    ![表完成](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="26eec-299">你已完成本章节。</span><span class="sxs-lookup"><span data-stu-id="26eec-299">You have completed this Chapter.</span></span> <span data-ttu-id="26eec-300">请确保保存。</span><span class="sxs-lookup"><span data-stu-id="26eec-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="26eec-301">第6章-创建 Azure Function App</span><span class="sxs-lookup"><span data-stu-id="26eec-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="26eec-302">创建一个 Azure Function App，桌面应用程序将调用该来更新 **表** 服务，并通过 **通知中心** 发送通知。</span><span class="sxs-lookup"><span data-stu-id="26eec-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="26eec-303">首先，需要创建一个文件，该文件允许 Azure 函数加载所需的库。</span><span class="sxs-lookup"><span data-stu-id="26eec-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="26eec-304">打开 **记事本** (按 Windows 键，然后键入 Notepad) 。</span><span class="sxs-lookup"><span data-stu-id="26eec-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![打开记事本](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="26eec-306">打开记事本后，将下面的 JSON 结构插入其中。</span><span class="sxs-lookup"><span data-stu-id="26eec-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="26eec-307">完成此操作后，将其保存在桌面上，就 **project.js**。</span><span class="sxs-lookup"><span data-stu-id="26eec-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="26eec-308">命名正确，这一点很重要：确保它没有 **.txt** 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="26eec-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="26eec-309">此文件定义你的函数将使用的库，如果你使用了 NuGet，则该文件将非常熟悉。</span><span class="sxs-lookup"><span data-stu-id="26eec-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="26eec-310">登录到 [Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="26eec-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="26eec-311">登录后，单击左上角的 " **新建** "，然后搜索 " **Function App**"，按 **enter**。</span><span class="sxs-lookup"><span data-stu-id="26eec-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![搜索函数应用](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="26eec-313">在较新的门户中，可能已将 " **新建** " 一词替换为 " **创建资源**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="26eec-314">新页将提供 **Function App** 服务的说明。</span><span class="sxs-lookup"><span data-stu-id="26eec-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="26eec-315">在此提示符下，选择 " **创建** " 按钮以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="26eec-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![function app 实例](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="26eec-317">单击 " **创建**" 后，请填写以下内容：</span><span class="sxs-lookup"><span data-stu-id="26eec-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="26eec-318">对于 " **应用名称**"，请为此服务实例插入所需的名称。</span><span class="sxs-lookup"><span data-stu-id="26eec-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="26eec-319">选择一个“订阅”  。</span><span class="sxs-lookup"><span data-stu-id="26eec-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="26eec-320">选择适合你的定价层，如果这是第一次创建 **Function App 服务**，则应提供免费层。</span><span class="sxs-lookup"><span data-stu-id="26eec-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="26eec-321">选择一个 **资源组** ，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="26eec-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="26eec-322">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="26eec-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="26eec-323">建议保留与单个项目关联的所有 Azure 服务 (例如，这些实验室) 在常见资源组) 下。</span><span class="sxs-lookup"><span data-stu-id="26eec-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="26eec-324">如果希望了解有关 Azure 资源组的详细信息，请参阅此 [链接，了解如何管理资源组](/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="26eec-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="26eec-325">对于 **操作系统**，请单击 "Windows"，因为这是预期的平台。</span><span class="sxs-lookup"><span data-stu-id="26eec-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="26eec-326">选择一种 **托管计划** (本教程将使用 **消耗计划**。</span><span class="sxs-lookup"><span data-stu-id="26eec-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="26eec-327">选择一个 **位置** **(选择与在上一步骤中生成的存储相同的位置)**</span><span class="sxs-lookup"><span data-stu-id="26eec-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="26eec-328">对于 " **存储** " 部分， **你必须选择在上一步中创建的存储服务**。</span><span class="sxs-lookup"><span data-stu-id="26eec-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="26eec-329">在此应用中不需要 *Application Insights* ，因此可随意将其 **关闭**。</span><span class="sxs-lookup"><span data-stu-id="26eec-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="26eec-330">单击 **“创建”** 。</span><span class="sxs-lookup"><span data-stu-id="26eec-330">Click **Create**.</span></span>

        ![创建新实例](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="26eec-332">单击 " **创建** " 后，将需要等待服务创建完成，这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="26eec-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="26eec-333">创建服务实例后，门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="26eec-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![新建通知](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="26eec-335">单击通知以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="26eec-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="26eec-336">单击通知中的 " **中转到资源** " 按钮以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="26eec-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![中转到资源](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="26eec-338">单击 " **+** *函数*" 旁边的 (加) 图标，以 *创建新* 的。</span><span class="sxs-lookup"><span data-stu-id="26eec-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![添加新函数](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="26eec-340">在中央面板中，将显示 " **函数** 创建" 窗口。</span><span class="sxs-lookup"><span data-stu-id="26eec-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="26eec-341">忽略面板上半部分中的信息，然后单击 " **自定义函数**" （位于蓝色区底部 (附近），如下所示) 。</span><span class="sxs-lookup"><span data-stu-id="26eec-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![自定义函数](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="26eec-343">窗口中的新页面将显示各种函数类型。</span><span class="sxs-lookup"><span data-stu-id="26eec-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="26eec-344">向下滚动以查看紫色类型，然后单击 " **HTTP PUT** 元素"。</span><span class="sxs-lookup"><span data-stu-id="26eec-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![http put 链接](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="26eec-346">你可能必须在页面下向下滚动 (并且此图像可能看起来不完全相同，如果已发生 Azure 门户更新) 但你正在寻找名为 " *HTTP PUT*" 的元素。</span><span class="sxs-lookup"><span data-stu-id="26eec-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="26eec-347">此时将显示 " **HTTP PUT** " 窗口，需要在此配置函数 (参阅下面的图像) 。</span><span class="sxs-lookup"><span data-stu-id="26eec-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="26eec-348">对于 " **语言"，** 使用下拉菜单选择 "C" \# 。</span><span class="sxs-lookup"><span data-stu-id="26eec-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="26eec-349">对于 **"名称"，请** 输入适当的名称。</span><span class="sxs-lookup"><span data-stu-id="26eec-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="26eec-350">在 " **身份验证级别** " 下拉菜单中，选择 " **函数**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="26eec-351">对于 " **表名** " 部分，需要使用以前用于创建 **表** 服务的名称， (包括相同的字母大小写) 。</span><span class="sxs-lookup"><span data-stu-id="26eec-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="26eec-352">在 " **存储帐户连接** " 部分中，使用下拉菜单，并从该处选择存储帐户。</span><span class="sxs-lookup"><span data-stu-id="26eec-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="26eec-353">如果没有，请单击部分标题旁边的 **新** 超链接，以显示另一个面板，应在其中列出你的存储帐户。</span><span class="sxs-lookup"><span data-stu-id="26eec-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![新存储](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="26eec-355">单击 " **创建** "，你将收到通知，告知你的设置已成功更新。</span><span class="sxs-lookup"><span data-stu-id="26eec-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![create 函数](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="26eec-357">单击 " **创建**" 后，将重定向到函数编辑器。</span><span class="sxs-lookup"><span data-stu-id="26eec-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![更新函数代码](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="26eec-359">将以下代码插入函数编辑器中 (替换函数) 中的代码：</span><span class="sxs-lookup"><span data-stu-id="26eec-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="26eec-360">该函数使用所包含的库，接收在 Unity 场景中移动的对象的名称和位置， (称为 **UnityGameObject**) 的 c # 对象。</span><span class="sxs-lookup"><span data-stu-id="26eec-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="26eec-361">然后，此对象用于更新创建的表中的对象参数。</span><span class="sxs-lookup"><span data-stu-id="26eec-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="26eec-362">遵循此功能后，该函数将调用你创建的通知中心服务，这会通知所有已订阅的应用程序。</span><span class="sxs-lookup"><span data-stu-id="26eec-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="26eec-363">在代码准备就绪后，单击 " **保存**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="26eec-364">接下来，单击 **\<** 页面右侧) 图标 (箭头。</span><span class="sxs-lookup"><span data-stu-id="26eec-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![打开上传面板](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="26eec-366">面板会从右侧滑入。</span><span class="sxs-lookup"><span data-stu-id="26eec-366">A panel will slide in from the right.</span></span> <span data-ttu-id="26eec-367">在该面板中，单击 " **上载**"，将显示文件浏览器。</span><span class="sxs-lookup"><span data-stu-id="26eec-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="26eec-368">导航到，然后单击 " **project.js** 文件，该文件是您之前在 **记事本** 中创建的，然后单击" **打开** "按钮。</span><span class="sxs-lookup"><span data-stu-id="26eec-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="26eec-369">此文件定义函数将使用的库。</span><span class="sxs-lookup"><span data-stu-id="26eec-369">This file defines the libraries that your function will use.</span></span>

    ![上传 json](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="26eec-371">文件上传后，它将显示在右侧的面板中。</span><span class="sxs-lookup"><span data-stu-id="26eec-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="26eec-372">单击它会在 **函数** 编辑器中打开它。</span><span class="sxs-lookup"><span data-stu-id="26eec-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="26eec-373">它必须与下一个映像 (在步骤 23) 下 **完全** 相同。</span><span class="sxs-lookup"><span data-stu-id="26eec-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="26eec-374">然后，在左侧面板的 " **函数**" 下，单击 " **集成** " 链接。</span><span class="sxs-lookup"><span data-stu-id="26eec-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![集成函数](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="26eec-376">在下一页上的右上角，单击 " **高级编辑器** (") "。</span><span class="sxs-lookup"><span data-stu-id="26eec-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![打开高级编辑器](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="26eec-378">将在中心面板中打开文件的 **function.js** ，需要将其替换为以下代码片段。</span><span class="sxs-lookup"><span data-stu-id="26eec-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="26eec-379">这会定义正在生成的函数和传递到函数的参数。</span><span class="sxs-lookup"><span data-stu-id="26eec-379">This defines the function you are building and the parameters passed into the function.</span></span>

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. <span data-ttu-id="26eec-380">编辑器现在应如下图所示：</span><span class="sxs-lookup"><span data-stu-id="26eec-380">Your editor should now look like the image below:</span></span>

    ![返回到标准编辑器](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="26eec-382">你可能会注意到，你刚插入的输入参数可能与你的表和存储详细信息不匹配，因此将需要使用你的信息更新。</span><span class="sxs-lookup"><span data-stu-id="26eec-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="26eec-383">请不要 **在此处执行此操作**，如下所述。</span><span class="sxs-lookup"><span data-stu-id="26eec-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="26eec-384">只需单击页面右上角的 " **标准编辑器** " 链接，返回即可。</span><span class="sxs-lookup"><span data-stu-id="26eec-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="26eec-385">返回到 **标准编辑器**，在 "**输入**" 下单击 " **Azure 表存储 (表)**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![表输入](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="26eec-387">请确保以下各项的匹配项，因为它们可能不同 (下面的步骤) ：</span><span class="sxs-lookup"><span data-stu-id="26eec-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="26eec-388">**表名**：在 Azure 存储中创建的表的名称，表服务。</span><span class="sxs-lookup"><span data-stu-id="26eec-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="26eec-389">**存储帐户连接：** 单击 " **新建**" （显示在下拉菜单旁），此时会在窗口的右侧显示一个面板。</span><span class="sxs-lookup"><span data-stu-id="26eec-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![新存储](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="26eec-391">选择之前创建的 **存储帐户** 以托管 **函数应用。**</span><span class="sxs-lookup"><span data-stu-id="26eec-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="26eec-392">你会注意到已创建 **存储帐户** 连接值。</span><span class="sxs-lookup"><span data-stu-id="26eec-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="26eec-393">完成后，请务必按 " **保存** "。</span><span class="sxs-lookup"><span data-stu-id="26eec-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="26eec-394">" **输入** " 页现在应与下面的内容匹配，并显示 **你的** 信息。</span><span class="sxs-lookup"><span data-stu-id="26eec-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![输入完成](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="26eec-396">接下来，在 "**输出**" 下单击 " **Azure 通知中心 (通知)** 。</span><span class="sxs-lookup"><span data-stu-id="26eec-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="26eec-397">请确保以下各项与 **你** 的信息匹配，因为它们可能不同 (以下步骤) ：</span><span class="sxs-lookup"><span data-stu-id="26eec-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="26eec-398">**通知中心名称**：这是你之前创建的 **通知中心** 服务实例的名称。</span><span class="sxs-lookup"><span data-stu-id="26eec-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="26eec-399">**通知中心命名空间连接**：单击 " **新建**"，随即出现下拉菜单。</span><span class="sxs-lookup"><span data-stu-id="26eec-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![检查输出](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="26eec-401">此时将显示 **连接** 弹出窗口 (参阅下图) ，你需要选择之前设置的 **通知中心** 的 **命名空间**。</span><span class="sxs-lookup"><span data-stu-id="26eec-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="26eec-402">从中间的下拉菜单中选择 **通知中心** 名称。</span><span class="sxs-lookup"><span data-stu-id="26eec-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="26eec-403">将 **策略** 下拉菜单设置为 **DefaultFullSharedAccessSignature**。</span><span class="sxs-lookup"><span data-stu-id="26eec-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="26eec-404">单击 " **选择** " 按钮返回。</span><span class="sxs-lookup"><span data-stu-id="26eec-404">Click the **Select** button to go back.</span></span>

        ![输出更新](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="26eec-406">" **输出** " 页现在应与下面的内容匹配，但会改为替换为 **您** 的信息。</span><span class="sxs-lookup"><span data-stu-id="26eec-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="26eec-407">请确保按 " **保存**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="26eec-408">请不要 *直接编辑通知中心名称* (应使用 **高级编辑器** 完成此操作，前提是你遵循了前面的步骤。</span><span class="sxs-lookup"><span data-stu-id="26eec-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![输出完成](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="26eec-410">此时，应测试函数，以确保其正常运行。</span><span class="sxs-lookup"><span data-stu-id="26eec-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="26eec-411">要执行此操作：</span><span class="sxs-lookup"><span data-stu-id="26eec-411">To do this:</span></span> 

    1. <span data-ttu-id="26eec-412">再次导航到函数页：</span><span class="sxs-lookup"><span data-stu-id="26eec-412">Navigate to the function page once more:</span></span>

        ![输出完成](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="26eec-414">返回到 "函数" 页，单击页最右侧的 " **测试** " 选项卡以打开 " *测试* " 边栏选项卡：</span><span class="sxs-lookup"><span data-stu-id="26eec-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![输出完成](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="26eec-416">在边栏选项卡的 " **请求正文** " 文本框中，粘贴以下代码：</span><span class="sxs-lookup"><span data-stu-id="26eec-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. <span data-ttu-id="26eec-417">测试代码准备就绪后，单击右下角的 " **运行** " 按钮，将运行测试。</span><span class="sxs-lookup"><span data-stu-id="26eec-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="26eec-418">测试的输出日志将显示在功能代码下方的控制台区域中。</span><span class="sxs-lookup"><span data-stu-id="26eec-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![输出完成](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="26eec-420">如果上述测试失败，则需要仔细检查是否已按照上述步骤执行操作，尤其是 **集成面板** 中的设置。</span><span class="sxs-lookup"><span data-stu-id="26eec-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="26eec-421">第7章-设置桌面 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="26eec-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26eec-422">你现在正在创建的桌面应用程序 **将不** 能在 Unity 编辑器中运行。</span><span class="sxs-lookup"><span data-stu-id="26eec-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="26eec-423">需要在生成应用程序后，使用 Visual Studio (或已部署的应用程序) 在编辑器外运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="26eec-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="26eec-424">下面是用于使用 Unity 和混合现实进行开发的典型设置，因此，这是其他项目的一个不错的模板。</span><span class="sxs-lookup"><span data-stu-id="26eec-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="26eec-425">设置并测试混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="26eec-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="26eec-426">本课程 **不** 需要移动控制器。</span><span class="sxs-lookup"><span data-stu-id="26eec-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="26eec-427">如果需要支持设置沉浸式耳机，请参阅此链接， [了解如何设置 Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="26eec-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="26eec-428">打开 **Unity** ，并单击 " **新建**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-428">Open **Unity** and click **New**.</span></span>

    ![新建 unity 项目](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="26eec-430">需要提供 Unity 项目名称，插入 **UnityDesktopNotifHub**。</span><span class="sxs-lookup"><span data-stu-id="26eec-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="26eec-431">请确保 "项目类型" 设置为 " **3d**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="26eec-432">将位置设置为合适的 **位置** (记住，更接近根目录) 。</span><span class="sxs-lookup"><span data-stu-id="26eec-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="26eec-433">然后单击 " **创建项目**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-433">Then, click **Create project**.</span></span>

    ![创建项目](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="26eec-435">当 Unity 处于打开状态时，有必要选中 "默认 **脚本编辑器** " 设置为 " **Visual Studio**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="26eec-436">转到 "**编辑**  >  **首选项**"，然后在新窗口中导航到 "**外部工具**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-436">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="26eec-437">将 **外部脚本编辑器** 更改为 **Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="26eec-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="26eec-438">关闭 " **首选项** " 窗口。</span><span class="sxs-lookup"><span data-stu-id="26eec-438">Close the **Preferences** window.</span></span>

    ![设置外部 VS 工具](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="26eec-440">接下来，转到 "**文件**  >  " "**生成设置**" 并选择 "**通用 Windows 平台**"，然后单击 "**切换平台**" 按钮以应用你的选择。</span><span class="sxs-lookup"><span data-stu-id="26eec-440">Next, go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![交换机平台](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="26eec-442">仍在 **文件**  >  **生成设置** 中时，请确保：</span><span class="sxs-lookup"><span data-stu-id="26eec-442">While still in **File** > **Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="26eec-443">**目标设备** 设置为 **任何设备**</span><span class="sxs-lookup"><span data-stu-id="26eec-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="26eec-444">此应用程序将用于桌面，因此必须是 **任何设备**</span><span class="sxs-lookup"><span data-stu-id="26eec-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="26eec-445">**生成类型** 设置为 **D3D**</span><span class="sxs-lookup"><span data-stu-id="26eec-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="26eec-446">**SDK** 设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="26eec-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="26eec-447">**Visual Studio 版本** 设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="26eec-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="26eec-448">"**生成并运行**" 设置为 "**本地计算机**"</span><span class="sxs-lookup"><span data-stu-id="26eec-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="26eec-449">在此过程中，需要保存场景，并将其添加到生成中。</span><span class="sxs-lookup"><span data-stu-id="26eec-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="26eec-450">通过选择 " **添加打开的场景**" 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="26eec-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="26eec-451">将显示 "保存" 窗口。</span><span class="sxs-lookup"><span data-stu-id="26eec-451">A save window will appear.</span></span>

            ![添加打开的场景](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="26eec-453">为此创建新文件夹，并为将来的任何场景创建一个新文件夹，然后选择 " **新建文件夹** " 按钮以创建新文件夹，将其命名为 **场景**。</span><span class="sxs-lookup"><span data-stu-id="26eec-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![新的场景文件夹](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="26eec-455">打开新创建的 **场景** 文件夹，然后在 "文件名 **：** 文本" 字段中，键入 " **NH \_ Desktop \_ 场景**"，并按 " **保存**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![新 NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="26eec-457">现在，" **生成设置**" 中的其余设置应保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="26eec-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="26eec-458">在同一窗口中，单击 " **播放机设置** " 按钮，这会在 **检查器** 所在的空间中打开相关的面板。</span><span class="sxs-lookup"><span data-stu-id="26eec-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="26eec-459">在此面板中，需要验证几项设置：</span><span class="sxs-lookup"><span data-stu-id="26eec-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="26eec-460">在 " **其他设置** " 选项卡中：</span><span class="sxs-lookup"><span data-stu-id="26eec-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="26eec-461">**脚本运行时版本** 应为 **试验 ( .net 4.6 等效)**</span><span class="sxs-lookup"><span data-stu-id="26eec-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="26eec-462">**脚本编写后端** 应为 **.net**</span><span class="sxs-lookup"><span data-stu-id="26eec-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="26eec-463">**API 兼容级别** 应为 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="26eec-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![4.6 net 版本](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="26eec-465">在 " **发布设置** " 选项卡的 " **功能**" 下，检查：</span><span class="sxs-lookup"><span data-stu-id="26eec-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="26eec-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="26eec-466">**InternetClient**</span></span>

            ![刻度 internet 客户端](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="26eec-468">返回 **生成设置** *Unity C \# 项目* 不再灰显; 勾选此的旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="26eec-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="26eec-469">关闭“生成设置”窗口  。</span><span class="sxs-lookup"><span data-stu-id="26eec-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="26eec-470">保存场景和项目 **文件**  >  **保存场景/文件**  >  **保存项目**。</span><span class="sxs-lookup"><span data-stu-id="26eec-470">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="26eec-471">如果要跳过此项目 (桌面应用的 *Unity 设置* 组件) ，并直接转到代码，请随时 [下载 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage)，将其作为 [**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目，然后从第 [9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)继续。</span><span class="sxs-lookup"><span data-stu-id="26eec-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="26eec-472">你仍需添加脚本组件。</span><span class="sxs-lookup"><span data-stu-id="26eec-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="26eec-473">第8章-在 Unity 中导入 Dll</span><span class="sxs-lookup"><span data-stu-id="26eec-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="26eec-474">你将使用适用于 Unity (的 Azure 存储，该存储本身利用 .Net SDK for Azure) 。</span><span class="sxs-lookup"><span data-stu-id="26eec-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="26eec-475">有关详细信息，请 [参阅此链接，了解有关适用于 Unity 的 Azure 存储](/sandbox/gamedev/unity/azure-storage-unity)。</span><span class="sxs-lookup"><span data-stu-id="26eec-475">For more information follow this [link about Azure Storage for Unity](/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="26eec-476">当前 Unity 中存在一个已知问题，需要在导入后重新配置插件。</span><span class="sxs-lookup"><span data-stu-id="26eec-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="26eec-477">此部分中 (4-7 的这些步骤) 解决 bug 后不再需要这些步骤。</span><span class="sxs-lookup"><span data-stu-id="26eec-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="26eec-478">若要将 SDK 导入到自己的项目中，请确保已从 GitHub 下载最新的 [**unitypackage**](https://aka.ms/azstorage-unitysdk) 。</span><span class="sxs-lookup"><span data-stu-id="26eec-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="26eec-479">然后执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="26eec-479">Then, do the following:</span></span>

1.  <span data-ttu-id="26eec-480">使用 "**资产 \> 导入包 \> 自定义包**" 菜单选项将 **unitypackage** 添加到 Unity。</span><span class="sxs-lookup"><span data-stu-id="26eec-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="26eec-481">在弹出的 " **导入 Unity 包** " 框中，可以选择 "_插件_\* 存储" 下的所有内容 \* \* \* \> 。</span><span class="sxs-lookup"><span data-stu-id="26eec-481">In the **Import Unity Package** box that pops up, you can select everything under \*\*_Plugin_ \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="26eec-482">取消选中所有其他内容，因为本课程不需要这样做。</span><span class="sxs-lookup"><span data-stu-id="26eec-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![导入到包](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="26eec-484">单击 " ***导入*** " 按钮，将项添加到项目。</span><span class="sxs-lookup"><span data-stu-id="26eec-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="26eec-485">在项目视图中，在 "**插件**" 下，选择 "**存储**" 文件夹，并 *仅* 选择以下插件：</span><span class="sxs-lookup"><span data-stu-id="26eec-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="26eec-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="26eec-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="26eec-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="26eec-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="26eec-488">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="26eec-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="26eec-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="26eec-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="26eec-490">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="26eec-490">System.Spatial</span></span>

![取消选中任何平台](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="26eec-492">选择 *这些特定插件* 后，**取消选中\*\*\*\*任何平台** 并 **取消选中**" **WSAPlayer** "，然后单击 "**应用**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![应用平台 dll](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="26eec-494">我们正在将这些特定插件标记为仅在 Unity 编辑器中使用。</span><span class="sxs-lookup"><span data-stu-id="26eec-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="26eec-495">这是因为在从 Unity 导出项目后，将使用 WSA 文件夹中的相同插件的不同版本。</span><span class="sxs-lookup"><span data-stu-id="26eec-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="26eec-496">在 **存储** 插件文件夹中，只选择：</span><span class="sxs-lookup"><span data-stu-id="26eec-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="26eec-497">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="26eec-497">Microsoft.Data.Services.Client</span></span>

        ![为 dll 设置不处理](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="26eec-499">选中 "**平台设置**" 下的 "**不处理**" 框，并单击 "**_应用_**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-499">Check the **Don't Process** box under **Platform Settings** and click **_Apply_**.</span></span>

    ![不应用处理](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="26eec-501">我们正在将此插件标记为 "不处理"，因为 Unity 程序集 patcher 在处理此插件时遇到困难。</span><span class="sxs-lookup"><span data-stu-id="26eec-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="26eec-502">即使未处理插件，该插件仍可正常工作。</span><span class="sxs-lookup"><span data-stu-id="26eec-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="26eec-503">第9章-创建桌面 Unity 项目中的 TableToScene 类</span><span class="sxs-lookup"><span data-stu-id="26eec-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="26eec-504">现在，需要创建包含代码的脚本来运行此应用程序。</span><span class="sxs-lookup"><span data-stu-id="26eec-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="26eec-505">需要创建的第一个脚本是 **TableToScene**，它负责：</span><span class="sxs-lookup"><span data-stu-id="26eec-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="26eec-506">读取 Azure 表中的实体。</span><span class="sxs-lookup"><span data-stu-id="26eec-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="26eec-507">使用表数据确定要生成的对象，以及在哪个位置生成的对象。</span><span class="sxs-lookup"><span data-stu-id="26eec-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="26eec-508">需要创建的第二个脚本是 **CloudScene**，它负责：</span><span class="sxs-lookup"><span data-stu-id="26eec-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="26eec-509">注册左键单击事件，使用户能够在场景周围拖动对象。</span><span class="sxs-lookup"><span data-stu-id="26eec-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="26eec-510">将此 Unity 场景中的对象数据序列化，并将其发送到 Azure Function App。</span><span class="sxs-lookup"><span data-stu-id="26eec-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="26eec-511">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="26eec-511">To create this class:</span></span>

1.  <span data-ttu-id="26eec-512">右键单击位于 "项目" 面板中的 "**资产**" 文件夹，然后单击 "**创建**  >  **文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-512">Right-click in the **Asset** Folder located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="26eec-513">命名文件夹 **脚本**。</span><span class="sxs-lookup"><span data-stu-id="26eec-513">Name the folder **Scripts**.</span></span>

    ![创建脚本文件夹](images/AzureLabs-Lab8-66.png)

    ![创建脚本文件夹2](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="26eec-516">双击刚创建的文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="26eec-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="26eec-517">右键单击 "**脚本**" 文件夹中，单击 "**创建**  >  **c # 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-517">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="26eec-518">将脚本命名为 **TableToScene**。</span><span class="sxs-lookup"><span data-stu-id="26eec-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="26eec-519">![新的 c # 脚本 ](images/AzureLabs-Lab8-68.png)
     ![ TableToScene 重命名](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="26eec-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="26eec-520">双击脚本，在 Visual Studio 2017 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="26eec-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="26eec-521">添加以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="26eec-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="26eec-522">在类中，插入以下变量：</span><span class="sxs-lookup"><span data-stu-id="26eec-522">Within the class, insert the following variables:</span></span>

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > <span data-ttu-id="26eec-523">将 **accountName** 值替换为 Azure 存储服务名称，将 **accountKey** 值替换为 azure 存储服务中的密钥值，在 Azure 门户中 (参阅下图) 。</span><span class="sxs-lookup"><span data-stu-id="26eec-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![提取帐户密钥](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="26eec-525">现在，添加 **开始 ()** 和 **唤醒 ()** 方法来初始化类。</span><span class="sxs-lookup"><span data-stu-id="26eec-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  <span data-ttu-id="26eec-526">在 **TableToScene** 类中，添加方法，该方法将检索 Azure 表中的值，并使用这些值在场景中生成相应的基元。</span><span class="sxs-lookup"><span data-stu-id="26eec-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  <span data-ttu-id="26eec-527">在 **TableToScene** 类之外，需要定义应用程序用于序列化和反序列化 **表实体** 的类。</span><span class="sxs-lookup"><span data-stu-id="26eec-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. <span data-ttu-id="26eec-528">请确保在返回到 Unity 编辑器之前 **保存** 。</span><span class="sxs-lookup"><span data-stu-id="26eec-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="26eec-529">单击 "**层次结构**" 面板中的 **主摄像机**，使其属性显示在 **检查器** 中。</span><span class="sxs-lookup"><span data-stu-id="26eec-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="26eec-530">在 " **脚本** " 文件夹打开的情况下，选择脚本 **TableToScene 文件** ，然后将其拖到 **主摄像机**。</span><span class="sxs-lookup"><span data-stu-id="26eec-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="26eec-531">结果应如下所示：</span><span class="sxs-lookup"><span data-stu-id="26eec-531">The result should be as below:</span></span>

    ![向主相机添加脚本](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="26eec-533">第10章-创建桌面 Unity 项目中的 CloudScene 类</span><span class="sxs-lookup"><span data-stu-id="26eec-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="26eec-534">需要创建的第二个脚本是 **CloudScene**，它负责：</span><span class="sxs-lookup"><span data-stu-id="26eec-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="26eec-535">注册左键单击事件，使用户能够在场景周围拖动对象。</span><span class="sxs-lookup"><span data-stu-id="26eec-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="26eec-536">将此 Unity 场景中的对象数据序列化，并将其发送到 Azure Function App。</span><span class="sxs-lookup"><span data-stu-id="26eec-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="26eec-537">创建第二个脚本：</span><span class="sxs-lookup"><span data-stu-id="26eec-537">To create the second script:</span></span>

1.  <span data-ttu-id="26eec-538">右键单击 " **脚本** " 文件夹中，单击 " **创建**， **C \# 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="26eec-539">将脚本命名为 **CloudScene**</span><span class="sxs-lookup"><span data-stu-id="26eec-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="26eec-540">![新的 c # 脚本 ](images/AzureLabs-Lab8-72.png)
     ![ 重命名 CloudScene](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="26eec-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="26eec-541">添加以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="26eec-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="26eec-542">插入以下变量：</span><span class="sxs-lookup"><span data-stu-id="26eec-542">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  <span data-ttu-id="26eec-543">将 **azureFunctionEndpoint** 值替换为 azure 门户中 Azure Function App 服务中找到的 AZURE Function App URL，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="26eec-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![获取函数 URL](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="26eec-545">现在，添加 **开始 ()** 和 **唤醒 ()** 方法来初始化类。</span><span class="sxs-lookup"><span data-stu-id="26eec-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  <span data-ttu-id="26eec-546">在 **Update ()** 方法中，添加下面的代码，用于检测鼠标输入并拖动，这反过来会移动场景中的 gameobject。</span><span class="sxs-lookup"><span data-stu-id="26eec-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="26eec-547">如果用户已拖放了一个对象，它会将该对象的名称和坐标传递给 **UpdateCloudScene ()** 方法，该方法将调用 azure Function App 服务，该服务将更新 azure 表并触发通知。</span><span class="sxs-lookup"><span data-stu-id="26eec-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  <span data-ttu-id="26eec-548">现在，按如下所示添加 **UpdateCloudScene ()** 方法：</span><span class="sxs-lookup"><span data-stu-id="26eec-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  <span data-ttu-id="26eec-549">保存代码并返回到 Unity</span><span class="sxs-lookup"><span data-stu-id="26eec-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="26eec-550">将 **CloudScene** 脚本拖到 **主照相机** 上。</span><span class="sxs-lookup"><span data-stu-id="26eec-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="26eec-551">单击 "**层次结构**" 面板中的 **主摄像机**，使其属性显示在 **检查器** 中。</span><span class="sxs-lookup"><span data-stu-id="26eec-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="26eec-552">在 " **脚本** " 文件夹打开的情况下，选择 **CloudScene** 脚本，并将其拖动到 **主相机** 上。</span><span class="sxs-lookup"><span data-stu-id="26eec-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="26eec-553">结果应如下所示：</span><span class="sxs-lookup"><span data-stu-id="26eec-553">The result should be as below:</span></span>

        > ![将云脚本拖到主相机上](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="26eec-555">第11章-将桌面项目构建到 UWP</span><span class="sxs-lookup"><span data-stu-id="26eec-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="26eec-556">此项目的 Unity 部分所需的所有内容现在都已完成。</span><span class="sxs-lookup"><span data-stu-id="26eec-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="26eec-557">导航到 "**生成设置**" (**文件**  >  **生成设置**") 。</span><span class="sxs-lookup"><span data-stu-id="26eec-557">Navigate to **Build Settings** (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="26eec-558">在 **生成设置** 窗口中，单击 " **生成**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-558">From the **Build Settings** window, click **Build**.</span></span>

    ![生成项目](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="26eec-560">将弹出一个 **文件资源管理器** 窗口，提示你提供要生成的位置。</span><span class="sxs-lookup"><span data-stu-id="26eec-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="26eec-561">单击左上角的 " **新建文件夹** ") 创建新文件夹 (，并将其命名为 " **生成**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![用于生成的新文件夹](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="26eec-563">打开 "新建 **生成** " 文件夹，并使用 " **新建文件夹** " 创建另一个文件夹 (再次) ，并将其命名为 " **NH \_ 桌面 \_ 应用**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![文件夹名称 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="26eec-565">选中 " **NH \_ 桌面" \_ 应用** 。</span><span class="sxs-lookup"><span data-stu-id="26eec-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="26eec-566">单击 " **选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-566">click **Select Folder**.</span></span> <span data-ttu-id="26eec-567">项目将需要一分钟或更长时间才能生成。</span><span class="sxs-lookup"><span data-stu-id="26eec-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="26eec-568">以下生成将显示 **文件资源管理器** ，显示新项目的位置。</span><span class="sxs-lookup"><span data-stu-id="26eec-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="26eec-569">无需打开它，因为在接下来的几章中，你需要先创建另一个 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="26eec-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="26eec-570">第12章-设置混合现实 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="26eec-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="26eec-571">下面是使用混合现实进行开发的典型设置，因此，这是其他项目的一个不错的模板。</span><span class="sxs-lookup"><span data-stu-id="26eec-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="26eec-572">打开 **Unity** ，并单击 " **新建**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-572">Open **Unity** and click **New**.</span></span>

    ![新建 unity 项目](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="26eec-574">你现在需要提供 Unity 项目名称，请插入 **UnityMRNotifHub**。</span><span class="sxs-lookup"><span data-stu-id="26eec-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="26eec-575">请确保 "项目类型" 设置为 " **3d**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="26eec-576">将位置设置为合适的 **位置** (记住，更接近根目录) 。</span><span class="sxs-lookup"><span data-stu-id="26eec-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="26eec-577">然后单击 " **创建项目**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-577">Then, click **Create project**.</span></span>

    ![名称 UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="26eec-579">当 Unity 处于打开状态时，有必要选中 "默认 **脚本编辑器** " 设置为 " **Visual Studio**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="26eec-580">转到 "**编辑**  >  **首选项**"，然后在新窗口中导航到 "**外部工具**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-580">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="26eec-581">将 **外部脚本编辑器** 更改为 **Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="26eec-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="26eec-582">关闭 " **首选项** " 窗口。</span><span class="sxs-lookup"><span data-stu-id="26eec-582">Close the **Preferences** window.</span></span>

    ![将外部编辑器设置为 VS](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="26eec-584">接下来，转到 "**文件**  >  **生成设置**"，并通过单击 "**切换平台**" 按钮将平台切换到 **通用 Windows 平台**。</span><span class="sxs-lookup"><span data-stu-id="26eec-584">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![将平台切换到 UWP](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="26eec-586">中转到 "**文件**" "  >  **生成设置**"，并确保：</span><span class="sxs-lookup"><span data-stu-id="26eec-586">Go to **File** > **Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="26eec-587">**目标设备** 设置为 **任何设备**</span><span class="sxs-lookup"><span data-stu-id="26eec-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="26eec-588">对于 Microsoft HoloLens，将 " **目标设备** " 设置为 " *hololens*"。</span><span class="sxs-lookup"><span data-stu-id="26eec-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="26eec-589">**生成类型** 设置为 **D3D**</span><span class="sxs-lookup"><span data-stu-id="26eec-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="26eec-590">**SDK** 设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="26eec-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="26eec-591">**Visual Studio 版本** 设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="26eec-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="26eec-592">"**生成并运行**" 设置为 "**本地计算机**"</span><span class="sxs-lookup"><span data-stu-id="26eec-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="26eec-593">在此过程中，需要保存场景，并将其添加到生成中。</span><span class="sxs-lookup"><span data-stu-id="26eec-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="26eec-594">通过选择 " **添加打开的场景**" 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="26eec-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="26eec-595">将显示 "保存" 窗口。</span><span class="sxs-lookup"><span data-stu-id="26eec-595">A save window will appear.</span></span>

            ![添加打开的场景](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="26eec-597">为此创建新文件夹，并为将来的任何场景创建一个新文件夹，然后选择 " **新建文件夹** " 按钮以创建新文件夹，将其命名为 **场景**。</span><span class="sxs-lookup"><span data-stu-id="26eec-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![新的场景文件夹](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="26eec-599">打开新创建的 **场景** 文件夹，然后在 "文件名 **：** 文本" 字段中，键入 **NH \_ MR \_ 场景**，并按 " **保存**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![新场景-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="26eec-601">现在，" **生成设置**" 中的其余设置应保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="26eec-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="26eec-602">在同一窗口中，单击 " **播放机设置** " 按钮，这会在 **检查器** 所在的空间中打开相关的面板。</span><span class="sxs-lookup"><span data-stu-id="26eec-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![打开播放机设置](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="26eec-604">在此面板中，需要验证几项设置：</span><span class="sxs-lookup"><span data-stu-id="26eec-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="26eec-605">在 " **其他设置** " 选项卡中：</span><span class="sxs-lookup"><span data-stu-id="26eec-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="26eec-606">**脚本运行时版本** 应为 **试验** ( .net 4.6 等效) </span><span class="sxs-lookup"><span data-stu-id="26eec-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="26eec-607">**脚本编写后端** 应为 **_.net_**</span><span class="sxs-lookup"><span data-stu-id="26eec-607">**Scripting Backend** should be **_.NET_**</span></span>
        3.  <span data-ttu-id="26eec-608">**API 兼容级别** 应为 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="26eec-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![api 兼容性](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="26eec-610">在面板中，在 " **XR 设置**" (的 "发布设置") 下面的 "**发布设置**" 下，请确保已添加 Windows Mixed reality SDK，确保已添加 **Windows Mixed reality SDK** </span><span class="sxs-lookup"><span data-stu-id="26eec-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![更新 xr 设置](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="26eec-612">在 " **发布设置** " 选项卡中，在 " **功能**" 下面：</span><span class="sxs-lookup"><span data-stu-id="26eec-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="26eec-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="26eec-613">**InternetClient**</span></span>           

            ![刻度 internet 客户端](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="26eec-615">返回 **生成设置**， **Unity c # 项目** 不再灰显：勾选此旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="26eec-615">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="26eec-616">完成这些更改后，关闭 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="26eec-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="26eec-617">保存场景和项目 **文件**  >  **保存场景/文件**  >  **保存项目**。</span><span class="sxs-lookup"><span data-stu-id="26eec-617">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="26eec-618">如果要跳过此项目的 *Unity 设置* 组件 (混合现实应用) ，并继续直接进入代码，请随意 [下载 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage)，将其作为 [**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目，然后从第 [14 章](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project)继续。</span><span class="sxs-lookup"><span data-stu-id="26eec-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="26eec-619">你仍需添加脚本组件。</span><span class="sxs-lookup"><span data-stu-id="26eec-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="26eec-620">第13章-导入混合现实 Unity 项目中的 Dll</span><span class="sxs-lookup"><span data-stu-id="26eec-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="26eec-621">将使用适用于 Azure) 的 .Net SDK (用于 Unity 库的 Azure 存储。</span><span class="sxs-lookup"><span data-stu-id="26eec-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="26eec-622">请单击以下 [链接，了解如何通过 Unity 使用 Azure 存储](/sandbox/gamedev/unity/azure-storage-unity)。</span><span class="sxs-lookup"><span data-stu-id="26eec-622">Please follow this [link on how to use Azure Storage with Unity](/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="26eec-623">当前 Unity 中存在一个已知问题，需要在导入后重新配置插件。</span><span class="sxs-lookup"><span data-stu-id="26eec-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="26eec-624">此部分中 (4-7 的这些步骤) 解决 bug 后不再需要这些步骤。</span><span class="sxs-lookup"><span data-stu-id="26eec-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="26eec-625">若要将 SDK 导入到自己的项目中，请确保已下载最新的 [unitypackage](https://aka.ms/azstorage-unitysdk)。</span><span class="sxs-lookup"><span data-stu-id="26eec-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="26eec-626">然后执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="26eec-626">Then, do the following:</span></span>

1.  <span data-ttu-id="26eec-627">使用 "**资产**  >  **导入包**  >  **自定义包**" 菜单选项将从上 unitypackage 下载的文件添加到 Unity。</span><span class="sxs-lookup"><span data-stu-id="26eec-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="26eec-628">在弹出的 "**导入 Unity 包**" 框中，可以选择 "**插件**" "存储" 下的所有内容  >  。</span><span class="sxs-lookup"><span data-stu-id="26eec-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span>

    ![导入包](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="26eec-630">单击 " **导入** " 按钮，将项添加到项目。</span><span class="sxs-lookup"><span data-stu-id="26eec-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="26eec-631">在项目视图中，在 "**插件**" 下，选择 "**存储**" 文件夹，并 *仅* 选择以下插件：</span><span class="sxs-lookup"><span data-stu-id="26eec-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="26eec-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="26eec-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="26eec-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="26eec-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="26eec-634">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="26eec-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="26eec-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="26eec-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="26eec-636">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="26eec-636">System.Spatial</span></span>

    ![选择插件](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="26eec-638">选择 *这些特定插件* 后，**取消选中\*\*\*\*任何平台** 并 **取消选中**" **WSAPlayer** "，然后单击 "**应用**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![应用平台更改](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="26eec-640">你要将这些特定插件标记为仅在 Unity 编辑器中使用。</span><span class="sxs-lookup"><span data-stu-id="26eec-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="26eec-641">这是因为在从 Unity 导出项目后，将使用 WSA 文件夹中的相同插件的不同版本。</span><span class="sxs-lookup"><span data-stu-id="26eec-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="26eec-642">在 **存储** 插件文件夹中，只选择：</span><span class="sxs-lookup"><span data-stu-id="26eec-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="26eec-643">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="26eec-643">Microsoft.Data.Services.Client</span></span>

        ![选择数据服务客户端](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="26eec-645">选中 "**平台设置**" 下的 "**不处理**" 框，并单击 "**应用**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![不处理](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="26eec-647">你正在将此插件标记为 "不处理"，因为 Unity 程序集 patcher 在处理此插件时遇到困难。</span><span class="sxs-lookup"><span data-stu-id="26eec-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="26eec-648">即使未处理插件，该插件仍可正常工作。</span><span class="sxs-lookup"><span data-stu-id="26eec-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="26eec-649">第14章-在混合现实 Unity 项目中创建 TableToScene 类</span><span class="sxs-lookup"><span data-stu-id="26eec-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="26eec-650">**TableToScene** 类与第 [9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)中所述的类完全相同。</span><span class="sxs-lookup"><span data-stu-id="26eec-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="26eec-651">按照第 [9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)所述的相同过程，在混合现实 Unity 项目中创建相同的类。</span><span class="sxs-lookup"><span data-stu-id="26eec-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="26eec-652">完成本章后，这两个 **Unity 项目** 将在主摄像机上设置此类。</span><span class="sxs-lookup"><span data-stu-id="26eec-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="26eec-653">第15章-在混合现实 Unity 项目中创建 NotificationReceiver 类</span><span class="sxs-lookup"><span data-stu-id="26eec-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="26eec-654">需要创建的第二个脚本是 **NotificationReceiver**，它负责：</span><span class="sxs-lookup"><span data-stu-id="26eec-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="26eec-655">在初始化时向通知中心注册应用。</span><span class="sxs-lookup"><span data-stu-id="26eec-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="26eec-656">正在侦听来自通知中心的通知。</span><span class="sxs-lookup"><span data-stu-id="26eec-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="26eec-657">从收到的通知反序列化对象数据。</span><span class="sxs-lookup"><span data-stu-id="26eec-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="26eec-658">基于反序列化的数据移动场景中的 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="26eec-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="26eec-659">创建 **NotificationReceiver** 脚本：</span><span class="sxs-lookup"><span data-stu-id="26eec-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="26eec-660">右键单击 " **脚本** " 文件夹中，单击 " **创建**， **C \# 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="26eec-661">将脚本命名为 **NotificationReceiver**。</span><span class="sxs-lookup"><span data-stu-id="26eec-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="26eec-662">![创建新的 c # 脚本 ](images/AzureLabs-Lab8-95.png)
     ![ 名称 NotificationReceiver](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="26eec-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="26eec-663">双击脚本将其打开。</span><span class="sxs-lookup"><span data-stu-id="26eec-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="26eec-664">添加以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="26eec-664">Add the following namespaces:</span></span>

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  <span data-ttu-id="26eec-665">插入以下变量：</span><span class="sxs-lookup"><span data-stu-id="26eec-665">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  <span data-ttu-id="26eec-666">将 **hubName** 值替换为你的通知中心服务名称，将 **hubListenEndpoint** 值替换为在 "访问策略" 选项卡中找到的终结点值，在 azure 门户中 (参阅下图) 。</span><span class="sxs-lookup"><span data-stu-id="26eec-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![插入通知中心策略终结点](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="26eec-668">现在，添加 **开始 ()** 和 **唤醒 ()** 方法来初始化类。</span><span class="sxs-lookup"><span data-stu-id="26eec-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  <span data-ttu-id="26eec-669">添加 **WaitForNotification** 方法，以允许该应用从通知中心库接收通知，而无需冲突主线程：</span><span class="sxs-lookup"><span data-stu-id="26eec-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  <span data-ttu-id="26eec-670">以下方法 **InitNotificationAsync ()** 将在初始化时向通知中心服务注册应用程序。</span><span class="sxs-lookup"><span data-stu-id="26eec-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="26eec-671">代码已注释掉，因为 Unity 将不能生成项目。</span><span class="sxs-lookup"><span data-stu-id="26eec-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="26eec-672">在 Visual Studio 中导入 Azure 消息传递 Nuget 包时，将删除注释。</span><span class="sxs-lookup"><span data-stu-id="26eec-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  <span data-ttu-id="26eec-673">每次收到通知时，将触发以下处理程序 **\_ PushNotificationReceived ()**。</span><span class="sxs-lookup"><span data-stu-id="26eec-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="26eec-674">它将反序列化通知，该通知将是已移动到桌面应用程序中的 Azure 表实体，然后将 MR 场景中的相应 GameObject 移到相同的位置。</span><span class="sxs-lookup"><span data-stu-id="26eec-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="26eec-675">代码已被注释掉，因为代码引用 Azure 消息库，你将在 Visual Studio 中使用 Nuget 包管理器生成 Unity 项目后添加该消息库。</span><span class="sxs-lookup"><span data-stu-id="26eec-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="26eec-676">因此，除非已注释掉，否则 Unity 项目将无法生成。请注意，如果你生成项目，然后希望返回到 Unity，你将需要 **重新注释** 该代码。</span><span class="sxs-lookup"><span data-stu-id="26eec-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. <span data-ttu-id="26eec-677">请记住在返回到 Unity 编辑器之前保存更改。</span><span class="sxs-lookup"><span data-stu-id="26eec-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="26eec-678">单击 "**层次结构**" 面板中的 **主摄像机**，使其属性显示在 **检查器** 中。</span><span class="sxs-lookup"><span data-stu-id="26eec-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="26eec-679">在 " **脚本** " 文件夹打开的情况下，选择 **NotificationReceiver** 脚本，并将其拖动到 **主相机** 上。</span><span class="sxs-lookup"><span data-stu-id="26eec-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="26eec-680">结果应如下所示：</span><span class="sxs-lookup"><span data-stu-id="26eec-680">The result should be as below:</span></span>

    ![将通知接收方脚本拖到照相机](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="26eec-682">如果你要为 Microsoft HoloLens 开发此内容，则需要更新 **摄像机** 的 *相机* 组件，以便：</span><span class="sxs-lookup"><span data-stu-id="26eec-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="26eec-683">清除标志：纯色</span><span class="sxs-lookup"><span data-stu-id="26eec-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="26eec-684">背景色：黑色</span><span class="sxs-lookup"><span data-stu-id="26eec-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="26eec-685">第16章-将混合现实项目构建到 UWP</span><span class="sxs-lookup"><span data-stu-id="26eec-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="26eec-686">本章与上一个项目的生成过程完全相同。</span><span class="sxs-lookup"><span data-stu-id="26eec-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="26eec-687">此项目的 Unity 部分所需的所有内容现在均已完成，因此可以从 Unity 构建它。</span><span class="sxs-lookup"><span data-stu-id="26eec-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="26eec-688">导航到 "**生成设置**" (**文件**  >  **生成设置**") 。</span><span class="sxs-lookup"><span data-stu-id="26eec-688">Navigate to **Build Settings** ( **File** > **Build Settings** ).</span></span>

2.  <span data-ttu-id="26eec-689">从 " **生成设置** " 菜单中，确保 **Unity c # 项目**\* 是勾选 (这将允许您在生成) 之后编辑此项目中的脚本。</span><span class="sxs-lookup"><span data-stu-id="26eec-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="26eec-690">完成此操作后，单击 " **生成**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-690">After this is done, click **Build**.</span></span>

    ![生成项目](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="26eec-692">将弹出一个 **文件资源管理器** 窗口，提示你提供要生成的位置。</span><span class="sxs-lookup"><span data-stu-id="26eec-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="26eec-693">单击左上角的 " **新建文件夹** ") 创建新文件夹 (，并将其命名为 " **生成**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![创建生成文件夹](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="26eec-695">打开 "新建 **生成** " 文件夹，并使用 " **新建文件夹** " 创建另一个文件夹 (再次) ，并将其命名为 **NH \_ MR \_ 应用**。</span><span class="sxs-lookup"><span data-stu-id="26eec-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![创建 NH_MR_Apps 文件夹](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="26eec-697">已选择 **NH \_ MR \_ 应用** 。</span><span class="sxs-lookup"><span data-stu-id="26eec-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="26eec-698">单击 " **选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-698">click **Select Folder**.</span></span> <span data-ttu-id="26eec-699">项目将需要一分钟或更长时间才能生成。</span><span class="sxs-lookup"><span data-stu-id="26eec-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="26eec-700">生成后，将在新项目的位置打开 **文件资源管理器** 窗口。</span><span class="sxs-lookup"><span data-stu-id="26eec-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="26eec-701">第17章-将 NuGet 包添加到 UnityMRNotifHub 解决方案</span><span class="sxs-lookup"><span data-stu-id="26eec-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="26eec-702">请记住，一旦你添加了以下 NuGet 包 (并取消注释下一 [章](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class) 中的代码) ，在 Unity 项目中重新打开时代码将显示错误。</span><span class="sxs-lookup"><span data-stu-id="26eec-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="26eec-703">如果希望返回并继续在 Unity 编辑器中进行编辑，则需要 errosome 代码的注释，稍后在 Visual Studio 中重新注释。</span><span class="sxs-lookup"><span data-stu-id="26eec-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="26eec-704">混合现实生成完成后，请导航到你生成的混合现实项目，并双击该文件夹中的解决方案 ( .sln) 文件，以通过 Visual Studio 2017 打开解决方案。</span><span class="sxs-lookup"><span data-stu-id="26eec-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="26eec-705">你现在需要添加 **Windowsazure.storage** NuGet 包;这是一个用于从通知中心接收通知的库。</span><span class="sxs-lookup"><span data-stu-id="26eec-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="26eec-706">导入 NuGet 包：</span><span class="sxs-lookup"><span data-stu-id="26eec-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="26eec-707">在 **解决方案资源管理器** 中，右键单击你的解决方案</span><span class="sxs-lookup"><span data-stu-id="26eec-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="26eec-708">单击 " **管理 NuGet 包**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-708">Click on **Manage NuGet Packages**.</span></span>

    ![打开 nuget 管理器](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="26eec-710">选择 "**浏览**" 选项卡并搜索 _ \* windowsazure.storage \* \*。</span><span class="sxs-lookup"><span data-stu-id="26eec-710">Select the ***Browse** _ tab and search for _*WindowsAzure.Messaging.managed\*\*.</span></span>

    ![查找 windows azure 消息包](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="26eec-712">选择结果 (如下所示) ，然后在右侧的窗口中，选中 " **项目**" 旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="26eec-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="26eec-713">这会在 " **项目**" 旁边的复选框中放置一个勾选标记，并在 " **Assembly-CSharp** " 和 " **UnityMRNotifHub** " 项目旁边放置一个复选框。</span><span class="sxs-lookup"><span data-stu-id="26eec-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![勾选所有项目](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="26eec-715">最初提供的版本 **可能** 与此项目不兼容。</span><span class="sxs-lookup"><span data-stu-id="26eec-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="26eec-716">因此，请单击 " **版本**" 旁边的下拉菜单，单击 " **版本 0.1.7.9**"，然后单击 " **安装**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="26eec-717">你现在已经完成了 NuGet 包的安装。</span><span class="sxs-lookup"><span data-stu-id="26eec-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="26eec-718">查找在 **NotificationReceiver** 类中输入的注释代码，并删除注释。</span><span class="sxs-lookup"><span data-stu-id="26eec-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="26eec-719">第18章-编辑 UnityMRNotifHub 应用程序，NotificationReceiver 类</span><span class="sxs-lookup"><span data-stu-id="26eec-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="26eec-720">添加 **NuGet 包** 后，需要 *取消注释* **NotificationReceiver** 类中的某些代码。</span><span class="sxs-lookup"><span data-stu-id="26eec-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="26eec-721">这包括：</span><span class="sxs-lookup"><span data-stu-id="26eec-721">This includes:</span></span>

1. <span data-ttu-id="26eec-722">位于顶部的命名空间：</span><span class="sxs-lookup"><span data-stu-id="26eec-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="26eec-723">**InitNotificationsAsync ()** 方法中的所有代码：</span><span class="sxs-lookup"><span data-stu-id="26eec-723">All the code within the **InitNotificationsAsync()** method:</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> <span data-ttu-id="26eec-724">上面的代码中包含注释：确保你未意外 *取消注释* 该注释 (因为如果你有！ ) ，代码将不会编译。</span><span class="sxs-lookup"><span data-stu-id="26eec-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="26eec-725">最后， **Channel_PushNotificationReceived** 事件：</span><span class="sxs-lookup"><span data-stu-id="26eec-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

<span data-ttu-id="26eec-726">在这些取消注释中，请确保保存，然后转到下一章节。</span><span class="sxs-lookup"><span data-stu-id="26eec-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="26eec-727">第19章-将混合现实项目关联到应用商店应用</span><span class="sxs-lookup"><span data-stu-id="26eec-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="26eec-728">现在需要将 **混合现实** 项目关联到在实验室开始时创建的应用商店应用。</span><span class="sxs-lookup"><span data-stu-id="26eec-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="26eec-729">打开解决方案。</span><span class="sxs-lookup"><span data-stu-id="26eec-729">Open the solution.</span></span>

2.  <span data-ttu-id="26eec-730">右键单击 "解决方案资源管理器面板" 中的 UWP 应用项目，单击 "前往应用 **商店**"，并 **将应用与应用商店关联 ...**。</span><span class="sxs-lookup"><span data-stu-id="26eec-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![打开存储关联](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="26eec-732">将显示一个新窗口 **，称为 "将应用与 Windows 应用商店关联"**。</span><span class="sxs-lookup"><span data-stu-id="26eec-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="26eec-733">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="26eec-733">Click **Next**.</span></span>

    ![切换到下一个屏幕](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="26eec-735">它将加载与已登录的帐户相关联的所有应用程序。</span><span class="sxs-lookup"><span data-stu-id="26eec-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="26eec-736">如果你未登录到你的帐户，则可以在此页上 **登录** 。</span><span class="sxs-lookup"><span data-stu-id="26eec-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="26eec-737">查找你在本教程开始时创建的 **应用商店应用名称** ，然后选择它。</span><span class="sxs-lookup"><span data-stu-id="26eec-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="26eec-738">然后单击“下一步”  。</span><span class="sxs-lookup"><span data-stu-id="26eec-738">Then click **Next**.</span></span>

    ![查找并选择你的商店名称](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="26eec-740">单击 " **关联**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-740">Click **Associate**.</span></span>

    ![关联应用](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="26eec-742">应用现已与应用商店应用 **相关联** 。</span><span class="sxs-lookup"><span data-stu-id="26eec-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="26eec-743">这是启用通知所必需的。</span><span class="sxs-lookup"><span data-stu-id="26eec-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="26eec-744">第20章-部署 UnityMRNotifHub 和 UnityDesktopNotifHub 应用程序</span><span class="sxs-lookup"><span data-stu-id="26eec-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="26eec-745">这一章可能更便于两人，因为这样做会包括运行的应用程序、在计算机桌面上运行的应用程序，以及沉浸式耳机中的其他应用程序。</span><span class="sxs-lookup"><span data-stu-id="26eec-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="26eec-746">沉浸式耳机应用正在等待接收对场景的更改 (位置更改本地 Gameobject) ，桌面应用将更改其本地场景 (位置更改) ，这些更改将与 MR 应用共享。</span><span class="sxs-lookup"><span data-stu-id="26eec-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="26eec-747">首先部署 MR 应用，然后部署桌面应用，以便接收方可以开始侦听。</span><span class="sxs-lookup"><span data-stu-id="26eec-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="26eec-748">若要在本地计算机上部署 **UnityMRNotifHub** 应用，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="26eec-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="26eec-749">在 **Visual Studio 2017** 中打开 **UnityMRNotifHub** 应用程序的解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="26eec-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="26eec-750">在 **解决方案平台** 中，选择 " **X86，本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="26eec-751">在 **解决方案配置** 中，选择 " **调试**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![设置项目配置](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="26eec-753">中转到 " **生成" 菜单** ，然后单击 " **部署解决方案** "，将应用程序旁加载到计算机上。</span><span class="sxs-lookup"><span data-stu-id="26eec-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="26eec-754">应用现在应显示在已安装的应用列表中，可以启动。</span><span class="sxs-lookup"><span data-stu-id="26eec-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="26eec-755">在本地计算机上部署 **UnityDesktopNotifHub** 应用程序：</span><span class="sxs-lookup"><span data-stu-id="26eec-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="26eec-756">在 **Visual Studio 2017** 中打开 **UnityDesktopNotifHub** 应用程序的解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="26eec-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="26eec-757">在 **解决方案平台** 中，选择 " **X86，本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="26eec-758">在 **解决方案配置** 中，选择 " **调试**"。</span><span class="sxs-lookup"><span data-stu-id="26eec-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![设置项目配置](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="26eec-760">中转到 " **生成" 菜单** ，然后单击 " **部署解决方案** "，将应用程序旁加载到计算机上。</span><span class="sxs-lookup"><span data-stu-id="26eec-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="26eec-761">应用现在应显示在已安装的应用列表中，可以启动。</span><span class="sxs-lookup"><span data-stu-id="26eec-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="26eec-762">启动混合现实应用程序，后跟桌面应用程序。</span><span class="sxs-lookup"><span data-stu-id="26eec-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="26eec-763">在两个应用程序都运行的情况下，使用鼠标左键)  (移动桌面场景中的对象。</span><span class="sxs-lookup"><span data-stu-id="26eec-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="26eec-764">这些位置更改将在本地进行、序列化并发送到 Function App 服务。</span><span class="sxs-lookup"><span data-stu-id="26eec-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="26eec-765">然后，Function App 服务将与通知中心一起更新表。</span><span class="sxs-lookup"><span data-stu-id="26eec-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="26eec-766">收到更新后，通知中心会将更新的数据直接发送到所有已注册的应用程序 (在这种情况下，沉浸式头戴式耳机应用程序) ，它将反序列化传入的数据，并将新位置数据应用于本地对象，并将其移入场景。</span><span class="sxs-lookup"><span data-stu-id="26eec-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="26eec-767">已完成 Azure 通知中心应用程序</span><span class="sxs-lookup"><span data-stu-id="26eec-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="26eec-768">恭喜，你构建了一个利用 Azure 通知中心服务的混合现实应用，并允许在应用之间进行通信。</span><span class="sxs-lookup"><span data-stu-id="26eec-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![最终产品-结束](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="26eec-770">额外练习</span><span class="sxs-lookup"><span data-stu-id="26eec-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="26eec-771">练习 1</span><span class="sxs-lookup"><span data-stu-id="26eec-771">Exercise 1</span></span>

<span data-ttu-id="26eec-772">能否使用如何更改 Gameobject 的颜色并将该通知发送到其他应用程序查看场景？</span><span class="sxs-lookup"><span data-stu-id="26eec-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="26eec-773">练习 2</span><span class="sxs-lookup"><span data-stu-id="26eec-773">Exercise 2</span></span>

<span data-ttu-id="26eec-774">能否将 Gameobject 移动到 MR 应用并在桌面应用中看到更新的场景？</span><span class="sxs-lookup"><span data-stu-id="26eec-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>