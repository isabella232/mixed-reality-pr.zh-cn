---
title: 将 Azure 机器人服务与 LUIS 集成
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现 Azure 机器人服务和自然语言理解。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, hololens 2, azure 机器人服务, luis, 自然语言, 对话机器人, azure 云服务, azure 自定义视觉, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 10386bf75f9f3d0c9669ad37195188220a1dcb75
ms.sourcegitcommit: daa45a19a3a353334380cda78fee7fa149f0e48b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/28/2021
ms.locfileid: "98981748"
---
# <a name="5-integrating-azure-bot-service"></a><span data-ttu-id="5ba9c-104">5.集成 Azure 机器人服务</span><span class="sxs-lookup"><span data-stu-id="5ba9c-104">5. Integrating Azure Bot Service</span></span>

<span data-ttu-id="5ba9c-105">在本教程中，你将了解如何在 HoloLens 2 演示应用程序中使用 Azure 机器人服务添加语言理解 (LUIS)，并让机器人在搜索被跟踪对象时为用户提供帮助  。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-105">In this tutorial, you will learn how to use **Azure Bot Service** in the **HoloLens 2** demo application to add Language Understanding (LUIS) and letting the Bot assist the user when searching for **Tracked Objects**.</span></span> <span data-ttu-id="5ba9c-106">本教程分为两部分，在第一部分中，使用 [Bot Composer](https://docs.microsoft.com/composer/introduction) 作为无代码解决方案来创建机器人，并快速浏览为机器人提供所需数据的 Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-106">This is a two part tutorial where in the first part you create the Bot with the [Bot Composer](https://docs.microsoft.com/composer/introduction) as a code free solution and take a quick look in the Azure Function that feeds the Bot with the needed data.</span></span> <span data-ttu-id="5ba9c-107">在第二部分中，在 Unity 项目中使用“BotManager (脚本)”来利用托管的机器人服务。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-107">In the second part you use the **BotManager (script)** in the Unity project to consume the hosted Bot Service.</span></span>

## <a name="objectives"></a><span data-ttu-id="5ba9c-108">目标</span><span class="sxs-lookup"><span data-stu-id="5ba9c-108">Objectives</span></span>

## <a name="part-1"></a><span data-ttu-id="5ba9c-109">第 1 部分</span><span class="sxs-lookup"><span data-stu-id="5ba9c-109">Part 1</span></span>

* <span data-ttu-id="5ba9c-110">了解有关 Azure 机器人服务的基础知识</span><span class="sxs-lookup"><span data-stu-id="5ba9c-110">Learn the basics about Azure Bot Service</span></span>
* <span data-ttu-id="5ba9c-111">了解如何使用 Bot Composer 创建机器人</span><span class="sxs-lookup"><span data-stu-id="5ba9c-111">Learn how to use the Bot Composer to create a Bot</span></span>
* <span data-ttu-id="5ba9c-112">了解如何使用 Azure Functions 从 Azure 存储提供数据</span><span class="sxs-lookup"><span data-stu-id="5ba9c-112">Learn how to use an Azure Function to provide data from the Azure Storage</span></span>

## <a name="part-2"></a><span data-ttu-id="5ba9c-113">第 2 部分</span><span class="sxs-lookup"><span data-stu-id="5ba9c-113">Part 2</span></span>

* <span data-ttu-id="5ba9c-114">了解如何在此项目中设置场景以使用 Azure 机器人服务</span><span class="sxs-lookup"><span data-stu-id="5ba9c-114">Learn how to setup the scene to use Azure Bot Service in this project</span></span>
* <span data-ttu-id="5ba9c-115">了解如何通过与机器人交谈来设置和查找对象</span><span class="sxs-lookup"><span data-stu-id="5ba9c-115">Learn how to set and find objects via conversing with the Bot</span></span>

## <a name="understanding-azure-bot-service"></a><span data-ttu-id="5ba9c-116">了解 Azure 机器人服务</span><span class="sxs-lookup"><span data-stu-id="5ba9c-116">Understanding Azure Bot Service</span></span>

<span data-ttu-id="5ba9c-117">借助 LUIS，Azure 机器人服务让开发人员能够创建与用户进行自然对话的智能机器人 。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-117">The **Azure Bot Service** empowers developers to create intelligent bots that can maintain natural conversation with users thanks to **LUIS**.</span></span> <span data-ttu-id="5ba9c-118">对话机器人是扩展用户与应用程序交互的方式的好方法。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-118">A conversational Bot is a great way to expand the ways a user can interact with your application.</span></span> <span data-ttu-id="5ba9c-119">机器人可以充当具有 [QnA Maker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) 的知识库，借助[语言理解智能服务 (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) 功能进行复杂的对话。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-119">A Bot can act as a knowledge base with a [QnA Maker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) to maintaining sophisticated conversation with the power of [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span></span>

<span data-ttu-id="5ba9c-120">详细了解 [Azure 机器人服务](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true)。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-120">Learn more about [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="part-1---creating-the-bot"></a><span data-ttu-id="5ba9c-121">第 1 部分 - 创建机器人</span><span class="sxs-lookup"><span data-stu-id="5ba9c-121">Part 1 - Creating the Bot</span></span>

<span data-ttu-id="5ba9c-122">在 Unity 应用程序中使用机器人之前，必须首先开发机器人，为其提供数据并将其托管在 Azure 上。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-122">Before you can use the bot in the Unity application, you need to develope it, provide it with data and host it on **Azure**.</span></span>
<span data-ttu-id="5ba9c-123">机器人的目标是能够说出数据库中存储的被跟踪对象数量，通过被跟踪对象的名称进行查找，以及告诉用户关于被跟踪对象的基本信息 。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-123">The goal of the bot is to have the abilities to tell how many *Tracked Objects* are stored in the database, find a *Tracked Object* by its name, and tell the user some basic information about it.</span></span>

### <a name="a-quick-look-into-tracked-objects-azure-function"></a><span data-ttu-id="5ba9c-124">快速了解被跟踪对象 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="5ba9c-124">A quick look into Tracked Objects Azure Function</span></span>

<span data-ttu-id="5ba9c-125">你即将开始创建机器人，但是要使其变得有用，你需要为其提供资源，以便机器人从中拉取数据。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-125">You are about to start creating the Bot, but to make it useful you need to give it a resource from which it can pull data.</span></span> <span data-ttu-id="5ba9c-126">由于机器人能够计算被跟踪对象的数量、通过名称查找特定的被跟踪对象以及告知详细信息，因此可使用可以访问 Azure 表存储的简单 Azure Functions 。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-126">Since the *Bot* will be able to count the amount of **Tracked Objects**, find specific ones by name and tell details, you will use a simple Azure Function that has access to the **Azure Table storage**.</span></span>

<span data-ttu-id="5ba9c-127">下载“被跟踪对象 Azure 函数”项目[AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) 并将其提取到硬盘驱动器。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-127">Download the Tracked Objects Azure Function project: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="5ba9c-128">此 Azure Functions 具有两个操作（Count 和 Find），你可以通过基本的 HTTP GET 调用来调用这两个操作  。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-128">This Azure Function has two actions, **Count** and **Find** which can be invoked via basic *HTTP* *GET* calls.</span></span> <span data-ttu-id="5ba9c-129">可以在 Visual Studio 中检查代码。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-129">You can inspect the code in **Visual Studio**.</span></span>

<span data-ttu-id="5ba9c-130">详细了解 [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview)。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-130">Learn more about [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="5ba9c-131">Count 函数从表存储查询表中的所有 TrackedObject，这非常简单  。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-131">The **Count** function queries from the **Table storage** all **TrackedObjects** from the table, very simple.</span></span> <span data-ttu-id="5ba9c-132">另一方面，Find 函数从 GET 请求中获取名称查询参数，并在表存储中查询匹配的 TrackedObject，然后将 DTO 以 JSON 的形式返回  。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-132">On the other hand the **Find** function takes a *name* query parameter from the *GET* request and queries the **Table storage** for a matching **TrackedObject** and returns a DTO as JSON.</span></span>

<span data-ttu-id="5ba9c-133">若要直接从 Visual Studio 部署此 Azure Function，请打开下载的 AzureFunction_TrackedObjectsService 文件夹，并通过 Visual Studio 打开现有的 .sln 文件 ![Bot Framework Composer 主页](images/mr-learning-azure/tutorial5-section3-step1-1.png)  </span><span class="sxs-lookup"><span data-stu-id="5ba9c-133">To deploy this **Azure Function** directly from **Visual Studio**, open the downloaded AzureFunction_TrackedObjectsService folder and open the present **.sln** file with visual studio ![Bot Framework Composer Home](images/mr-learning-azure/tutorial5-section3-step1-1.png)</span></span>

<span data-ttu-id="5ba9c-134">在 Visual Studio 中加载文件后，在解决方案资源管理器中右键单击“跟踪的对象项”，然后选择“发布”![Bot Framework Composer 主页](images/mr-learning-azure/tutorial5-section3-step1-2.png)</span><span class="sxs-lookup"><span data-stu-id="5ba9c-134">Once file loaded in visual studio, Right click over **Tracked object sevice** in solution explorer and select publish ![Bot Framework Composer Home](images/mr-learning-azure/tutorial5-section3-step1-2.png)</span></span>

<span data-ttu-id="5ba9c-135">随即将显示“发布”弹出窗口，并请求提供目标平台 选择“Azure”，然后单击“下一步”按钮</span><span class="sxs-lookup"><span data-stu-id="5ba9c-135">The publish pop up will be displayed and ask for target flatform Select azure and click on **Next** button</span></span>

![Bot Framework Composer 主页](images/mr-learning-azure/tutorial5-section3-step1-3.png)

<span data-ttu-id="5ba9c-137">在具体目标中，选择“Azure 函数应用(Windows)”，然后单击“下一步”按钮 </span><span class="sxs-lookup"><span data-stu-id="5ba9c-137">In specific target select **Azure Function App(Windows)** and click on **Next** button</span></span>

![Bot Framework Composer 主页](images/mr-learning-azure/tutorial5-section3-step1-4.png)

<span data-ttu-id="5ba9c-139">如果你未登录到 Azure，请通过 Visual Studio 登录，窗口如下所示</span><span class="sxs-lookup"><span data-stu-id="5ba9c-139">If you are not logged in to azure please login through visual studio and the window look like</span></span>

![Bot Framework Composer 主页](images/mr-learning-azure/tutorial5-section3-step1-5.png)

<span data-ttu-id="5ba9c-141">单击加号按钮，在 Azure 帐户中创建新的函数应用</span><span class="sxs-lookup"><span data-stu-id="5ba9c-141">Click on pulse button to create new Function App in azure account</span></span>

![Bot Framework Composer 主页](images/mr-learning-azure/tutorial5-section3-step1-6.png)

* <span data-ttu-id="5ba9c-143">对于“名称”，请输入服务的适当名称，例如 TrackedObjectsService</span><span class="sxs-lookup"><span data-stu-id="5ba9c-143">For **Name**, enter a suitable name for the service, for example, *TrackedObjectsService*</span></span>
* <span data-ttu-id="5ba9c-144">对于“计划类型”，请选择“消耗”</span><span class="sxs-lookup"><span data-stu-id="5ba9c-144">For **Plan Type**, choose consumption</span></span>
* <span data-ttu-id="5ba9c-145">对于“位置”，请选择与应用用户的实际位置靠近的位置，例如“(美国)美国西部”</span><span class="sxs-lookup"><span data-stu-id="5ba9c-145">For **Location**, choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="5ba9c-146">对于“资源组”和“存储”，请选择在先前章节中创建的相应 Azure 组和存储帐户 。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-146">For **Resource Group** and **Storage**, choose respective azure group and storage account have been created in pervious chapters.</span></span>

<span data-ttu-id="5ba9c-147">创建函数应用之后，单击“完成”按钮</span><span class="sxs-lookup"><span data-stu-id="5ba9c-147">Once Function App created click on **Finish** button</span></span> 

![Bot Framework Composer 主页](images/mr-learning-azure/tutorial5-section3-step1-7.png)

<span data-ttu-id="5ba9c-149">完成后，将打开“发布”弹出窗口，单击“发布”按钮以发布函数并等待发布</span><span class="sxs-lookup"><span data-stu-id="5ba9c-149">A publish pop up will be opened after the finish process, click on **Publish** button to publish the function and wait for publish</span></span>

![Bot Framework Composer 主页](images/mr-learning-azure/tutorial5-section3-step1-8.png)

<span data-ttu-id="5ba9c-151">发布完成后，单击“操作”部分下的“在 Azure 门户中管理”，转到 Azure 门户中的具体函数，再单击“设置”部分下的“配置” 。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-151">Once completion of publish click on **Manage in Azure portal** under Actions section it is take you to specific function in azure portal and click on **Configuration** which is under the *Settings* section.</span></span> <span data-ttu-id="5ba9c-152">在“应用程序设置”上，需要向存储被跟踪对象的 Azure 存储提供连接字符串 。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-152">There on **Application Settings** you need to provide the *Connection string* to the **Azure Storage** where the **Tracked Objects** are stored.</span></span> <span data-ttu-id="5ba9c-153">单击“新应用程序设置”，并使用其名称(AzureStorageConnectionString)，然后提供正确的连接字符串作为值。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-153">Click on **New Application setting** and use for name: **AzureStorageConnectionString** and for value provide the correct *Connection string*.</span></span> <span data-ttu-id="5ba9c-154">接下来，单击“保存”，现在 Azure Functions 已准备就绪，可以为接下来要创建的机器人提供服务 。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-154">After that click on **Save** and the **Azure Function** is ready to server the *Bot* which you will create next.</span></span>

<span data-ttu-id="5ba9c-155">若要获取 Count 和 Find 的 URL，请选择“函数”（位于“函数”部分下）</span><span class="sxs-lookup"><span data-stu-id="5ba9c-155">To get URL of count and Find , select **Functions** which is under the *Functions* section.</span></span> <span data-ttu-id="5ba9c-156">可在此处找到 Count 和 Find 函数，选择顶部的 Count 函数，可以找到“获取函数 URL”按钮。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-156">here you can find both Count and Find function, select Count function on top side you can find the *Get Function Url* button.</span></span> <span data-ttu-id="5ba9c-157">按照相同的过程获取 Find 函数 URL。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-157">Follow the same procedure to get Find function Url.</span></span>

### <a name="creating-a-conversation-bot"></a><span data-ttu-id="5ba9c-158">创建对话机器人</span><span class="sxs-lookup"><span data-stu-id="5ba9c-158">Creating a conversation Bot</span></span>

<span data-ttu-id="5ba9c-159">可以通过多种方式来开发基于 Bot Framework 的对话机器人。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-159">There are several ways to develop a Bot Framework based conversational bot.</span></span> <span data-ttu-id="5ba9c-160">本课程将使用 [Bot Framework Composer](https://docs.microsoft.com/composer/) 桌面应用程序，该应用程序是非常适合快速开发的可视化设计器。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-160">In this lesson you will use the [Bot Framework Composer](https://docs.microsoft.com/composer/) desktop application which is a visual designer that is perfect for rapid development.</span></span>

<span data-ttu-id="5ba9c-161">可以从 [Github 存储库](https://github.com/microsoft/BotFramework-Composer/releases)下载最新版本。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-161">You can download the latest releases from the [Github repository](https://github.com/microsoft/BotFramework-Composer/releases).</span></span> <span data-ttu-id="5ba9c-162">它适用于 Windows、Mac 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-162">It is available for Windows, Mac, and Linux.</span></span>

<span data-ttu-id="5ba9c-163">安装 Bot Framework Composer 后，启动应用程序，你应该会看到以下界面：</span><span class="sxs-lookup"><span data-stu-id="5ba9c-163">Once the **Bot Framework Composer** is installed, start the application and you should see this interface:</span></span>

![Bot Framework Composer 主页](images/mr-learning-azure/tutorial5-section4-step1-1.png)

<span data-ttu-id="5ba9c-165">我们准备了一个机器人构建器项目，可提供本教程所需的对话和触发器。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-165">We have prepared a bot composer project which provides the needed dialogues and triggers for this tutorial.</span></span> <span data-ttu-id="5ba9c-166">下载 Bot Framework Composer 项目[BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) 并将其提取到硬盘驱动器中。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-166">Download the Bot Framework Composer project: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="5ba9c-167">在顶部栏上，单击“打开”，然后选择你下载的 Bot Framework 项目，该项目名为 TrackedObjectsBot 。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-167">On the top bar click on **Open** and select the Bot Framework project you have downloaded which is named **TrackedObjectsBot**.</span></span> <span data-ttu-id="5ba9c-168">项目完全加载后，你应该会看到项目已准备就绪。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-168">After the project is fully loaded, you should see the project ready.</span></span>

![已打开 TrackedObjectsBot 项目的 Bot Framework Composer](images/mr-learning-azure/tutorial5-section4-step1-2.png)

<span data-ttu-id="5ba9c-170">让我们集中在左侧，你可以在其中看到“对话框面板”。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-170">Let's focus on the left side where you can see the **Dialogs Panel**.</span></span> <span data-ttu-id="5ba9c-171">左侧有一个名为 TrackedObjectsBot 的对话框，你可以在其中看到几个触发器 。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-171">There you have one dialog named **TrackedObjectsBot** under which you can see several **Triggers**.</span></span>

<span data-ttu-id="5ba9c-172">详细了解 [Bot Framework 概念](https://docs.microsoft.com/composer/concept-dialog)。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-172">Learn more about [Bot Framework concepts](https://docs.microsoft.com/composer/concept-dialog).</span></span>

<span data-ttu-id="5ba9c-173">这些触发器执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5ba9c-173">These triggers do the following:</span></span>

#### <a name="greeting"></a><span data-ttu-id="5ba9c-174">问候语</span><span class="sxs-lookup"><span data-stu-id="5ba9c-174">Greeting</span></span>

<span data-ttu-id="5ba9c-175">这是用户发起对话时聊天机器人的入口 。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-175">This is the entry point of the chat *bot* when ever a *user* initiates a conversation.</span></span>

![TrackedObjectsBot 项目对话框触发器 - 问候语](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a><span data-ttu-id="5ba9c-177">AskingForCount</span><span class="sxs-lookup"><span data-stu-id="5ba9c-177">AskingForCount</span></span>

<span data-ttu-id="5ba9c-178">当用户要求计算所有被跟踪对象时，将触发此对话。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-178">This dialog is triggered when the *user* asks for counting all **Tracked Objects**.</span></span>
<span data-ttu-id="5ba9c-179">下面是触发短语：</span><span class="sxs-lookup"><span data-stu-id="5ba9c-179">These are the trigger phrases:</span></span>

>* <span data-ttu-id="5ba9c-180">全部统计</span><span class="sxs-lookup"><span data-stu-id="5ba9c-180">count me all</span></span>
>* <span data-ttu-id="5ba9c-181">存储的数量</span><span class="sxs-lookup"><span data-stu-id="5ba9c-181">how many are stored</span></span>

![TrackedObjectsBot 项目对话框触发器 - AskForCount](images/mr-learning-azure/tutorial5-section4-step1-4.png)

<span data-ttu-id="5ba9c-183">借助 [LUIS](https://docs.microsoft.com/composer/how-to-use-luis)，用户不必以这种确切的方式询问短语，从而允许用户进行自然对话 。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-183">Thanks to [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) the *user* does not have to ask the phrases in that exact way which allows a natural conversation for the *user*.</span></span>

<span data-ttu-id="5ba9c-184">在此对话中，机器人还将与 Azure Functions 的“Count”对话，稍后再进行详细介绍。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-184">In this dialog the *bot* will also talk to the **Count** Azure Function, more about that later.</span></span>

#### <a name="unknown-intent"></a><span data-ttu-id="5ba9c-185">未知意向</span><span class="sxs-lookup"><span data-stu-id="5ba9c-185">Unknown Intent</span></span>

<span data-ttu-id="5ba9c-186">如果来自用户的输入不符合任何其他触发条件，则会触发此对话，并通过再次尝试提问来响应用户。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-186">This dialogue is triggered if the input from the *user* does not fit any other trigger condition and responses the user with trying his question again.</span></span>

![TrackedObjectsBot 项目对话框触发器 - 未知意向](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a><span data-ttu-id="5ba9c-188">FindEntity</span><span class="sxs-lookup"><span data-stu-id="5ba9c-188">FindEntity</span></span>

<span data-ttu-id="5ba9c-189">最后一个对话为数据创建分支并将其存储在机器人内存中，因此更加复杂。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-189">The last dialogue is more complex with branching and storing data in the *bots* memory.</span></span>
<span data-ttu-id="5ba9c-190">它要求用户提供被跟踪对象的名称以便了解详细信息、对 Azure Functions 的“Find”执行查询，并使用响应继续进行对话 。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-190">It asks the user for the *name* of the **Tracked Object** it want's to know more information about, performs a query to the **Find** Azure Function, and uses the response to proceed with the conversation.</span></span>

![TrackedObjectsBot 项目对话框触发器 - FindEntity](images/mr-learning-azure/tutorial5-section4-step1-6.png)

<span data-ttu-id="5ba9c-192">如果未找到被跟踪对象，系统将通知用户并结束对话。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-192">If the **Tracked Object** is not found, the user is informed and the conversation ends.</span></span> <span data-ttu-id="5ba9c-193">找到相关的被跟踪对象后，启动程序将检查可用的属性并报告这些属性。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-193">When the **Tracked Object** in question is found, the boot will check what properties are available and report on them.</span></span>

### <a name="adapting-the-bot"></a><span data-ttu-id="5ba9c-194">调整机器人</span><span class="sxs-lookup"><span data-stu-id="5ba9c-194">Adapting the Bot</span></span>

<span data-ttu-id="5ba9c-195">AskingForCount 和 FindEntity 触发器需要与后端通信，这意味着必须添加先前部署的 Azure Functions 的正确 URL  。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-195">The **AskingForCount** and **FindEntity** trigger need to talk to the backend, this means you have to add the correct URL of the **Azure Function** you deployed previously.</span></span>

<span data-ttu-id="5ba9c-196">在对话框面板上，单击“AskingForCount”，然后找到“发送 HTTP 请求”操作，你可以在此处看到字段“URL”，在此字段中，需要为 Count 函数终结点更改正确的 URL 。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-196">On the dialog panel click on **AskingForCount** and locate the *Send an HTTP request* action, here you can see the field **URL** which you need to change the correct URL for the **Count** function endpoint.</span></span>

![TrackedObjectsBot 项目 AskingForCount 对话框触发器终结点配置](images/mr-learning-azure/tutorial5-section5-step1-1.png)

<span data-ttu-id="5ba9c-198">最后，查找 FindEntity 触发器并找到“发送 HTTP 请求”操作，在 URL 字段中将 URL 更改为 Find 函数终结点 。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-198">Finally, look for the **FindEntity** trigger and locate the *Send an HTTP request* action, in the **URL** field change the URL to the **Find** function endpoint.</span></span>

![TrackedObjectsBot 项目 FindEntity 对话框触发器终结点配置](images/mr-learning-azure/tutorial5-section5-step1-2.png)

<span data-ttu-id="5ba9c-200">完成所有设置后，现在即可部署机器人。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-200">With everything set you are now ready to deploy the Bot.</span></span> <span data-ttu-id="5ba9c-201">由于你已经安装了 Bot Framework Composer，因此可以直接从此处发布机器人。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-201">Since you have Bot Framework composer installed, you can publish it directly from there.</span></span>

<span data-ttu-id="5ba9c-202">详细了解[从 Bot Composer 发布机器人](https://docs.microsoft.com/composer/how-to-publish-bot)。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-202">Learn more about [Publish a bot from Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span></span>

> [!TIP]
> <span data-ttu-id="5ba9c-203">通过添加更多触发短语、新响应或对话分支，可以随时与机器人对话。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-203">Feel free playing around with Bot by adding more trigger phrases, new responses or conversation branching.</span></span>

## <a name="part-2---putting-everything-together-in-unity"></a><span data-ttu-id="5ba9c-204">第 2 部分 - 将所有内容整合到 Unity 中</span><span class="sxs-lookup"><span data-stu-id="5ba9c-204">Part 2 - Putting everything together in Unity</span></span>

### <a name="preparing-the-scene"></a><span data-ttu-id="5ba9c-205">准备场景</span><span class="sxs-lookup"><span data-stu-id="5ba9c-205">Preparing the scene</span></span>

<span data-ttu-id="5ba9c-206">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.AzureCloudServices” > “预制件” > “管理器”文件夹   。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-206">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![已选中 ChatBotManager 预制件的 Unity 项目窗口](images/mr-learning-azure/tutorial5-section6-step1-1.png)

<span data-ttu-id="5ba9c-208">从此处将预制件 ChatBotManager 移到场景层次结构中。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-208">From there move the prefab **ChatBotManager** into the scene Hierarchy.</span></span>

<span data-ttu-id="5ba9c-209">将 ChatBotManager 添加到场景后，单击“聊天机器人管理器”组件。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-209">Once you add the ChatBotManager to the scene, click on the **Chat Bot Manager** component.</span></span>
<span data-ttu-id="5ba9c-210">在“检查器”中，你将看到一个空的“Direct Line 密钥”字段，需要填写该字段。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-210">In the Inspector you will see that there is an empty **Direct Line Secret Key** field which you need to fill out.</span></span>

> [!TIP]
> <span data-ttu-id="5ba9c-211">可以从 Azure 门户中检索密钥，方法是查找在本教程的第一部分中创建的“机器人通道注册”类型的资源。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-211">You can retrieve the *secret key* from the Azure portal by looking for the resource of type **Bot Channels Registration** you have created in the first part of this tutorial.</span></span>

![仍然选中新增的 ChatBotManager 预制件的 Unity](images/mr-learning-azure/tutorial5-section6-step1-2.png)

<span data-ttu-id="5ba9c-213">现在，将 ChatBotManager 对象与附加到 ChatBotPanel 对象的 ChatBotController 组件连接起来  。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-213">Now you will connect the **ChatBotManager** object with the **ChatBotController** component that is attached to the **ChatBotPanel** object.</span></span> <span data-ttu-id="5ba9c-214">在“层次结构”中，选择“ChatBotPanel”，你将看到一个空的“聊天机器人管理器”字段，从“层次结构”将“ChatBotManager”对象拖动到空的“聊天机器人管理器”字段中   。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-214">In the Hierarchy select the **ChatBotPanel** and you will see an empty **Chat Bot Manager** field, drag from the Hierarchy the **ChatBotManager** object into the empty **Chat Bot Manager** field.</span></span>

![已配置 ChatBotPanel 的 Unity](images/mr-learning-azure/tutorial5-section6-step1-3.png)

<span data-ttu-id="5ba9c-216">接下来，你需要通过一种方法打开 ChatBotPanel，以便用户可以与之进行交互。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-216">Next you need a way to open the **ChatBotPanel** so that the user can interact with it.</span></span> <span data-ttu-id="5ba9c-217">在“场景”窗口中，你可能已经注意到，MainMenu 对象上有一个“聊天机器人”侧按钮，可使用该按钮解决此问题。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-217">From the Scene window you may have noticed that there is a *Chat Bot* side button on the **MainMenu** object, you will use it to solve this problem.</span></span>

<span data-ttu-id="5ba9c-218">在“层次结构”中，找到“RootMenu” > “MainMenu” > “SideButtonCollection” > “ButtonChatBot”，然后在“检查器”中找到“ButtonConfigHelper”脚本   。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-218">In the Hierarchy locate **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** and locate in the Inspector the *ButtonConfigHelper* script.</span></span> <span data-ttu-id="5ba9c-219">在那里，你将在 OnClick() 事件回调中看到一个空槽。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-219">There you will see an empty slot on the **OnClick()** event callback.</span></span> <span data-ttu-id="5ba9c-220">将 ChatBotPanel 拖放到事件槽，从下拉列表中导航到 GameObject，然后在子菜单中选择“SetActive (bool)”并启用复选框 。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-220">Drag and drop the **ChatBotPanel** to the event slot, from the dropdown list navigate *GameObject*, then select in the sub menu *SetActive (bool)* and enable the checkbox.</span></span>

![已配置 ButtonChatBot 的 Unity](images/mr-learning-azure/tutorial5-section6-step1-4.png)

<span data-ttu-id="5ba9c-222">现在，可以从主菜单启动聊天机器人，并可以使用场景了。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-222">Now the chat bot can be stared from the main menu and with that the scene is ready for use.</span></span>

### <a name="putting-the-bot-to-a-test"></a><span data-ttu-id="5ba9c-223">对机器人进行测试</span><span class="sxs-lookup"><span data-stu-id="5ba9c-223">Putting the bot to a test</span></span>

#### <a name="asking-about-the-quantity-of-tracked-objects"></a><span data-ttu-id="5ba9c-224">询问被跟踪对象的数量</span><span class="sxs-lookup"><span data-stu-id="5ba9c-224">Asking about the quantity of tracked objects</span></span>

<span data-ttu-id="5ba9c-225">首先测试如何向机器人询问在数据库中存储的被跟踪对象的数量。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-225">First you test asking the bot how many **Tracked Objects** are stored in the database.</span></span>

> [!NOTE]
> <span data-ttu-id="5ba9c-226">这一次必须从 HoloLens 2 运行应用程序，因为你的系统上可能无法使用文本转语音等服务。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-226">This time you must run the application from the HoloLens 2 because services like *text-to-speech* may not be available on your system.</span></span>

<span data-ttu-id="5ba9c-227">在 HoloLens 2 上运行应用程序，然后单击主菜单旁边的“聊天机器人”按钮。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-227">Run the application on your HoloLens 2 and click on the *Chat Bot* button next to the main menu.</span></span>
<span data-ttu-id="5ba9c-228">机器人会问候你，现在询问它“我们有多少个对象？”</span><span class="sxs-lookup"><span data-stu-id="5ba9c-228">The bot will be greeting you, now ask **how many objects do we have?**</span></span>
<span data-ttu-id="5ba9c-229">机器人应会告诉你数量并结束对话。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-229">It should tell you the quantity and end the conversation.</span></span>

#### <a name="asking-about-a-tracked-object"></a><span data-ttu-id="5ba9c-230">询问被跟踪对象</span><span class="sxs-lookup"><span data-stu-id="5ba9c-230">Asking about a tracked object</span></span>

<span data-ttu-id="5ba9c-231">现在再次运行应用程序，这次让机器人“查找被跟踪对象”，机器人将询问你名称，你应回答“汽车”或者数据库中已知的其他被跟踪对象的名称。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-231">Now run the application again and this time ask **find me a tracked object**, the bot will be asking you the name to which you should respond with the "car" or the name of an other *Tracked Object* you know exists in the database.</span></span> <span data-ttu-id="5ba9c-232">机器人将告诉你详细信息，例如描述以及是否分配了空间定位点。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-232">The bot will tell you details like description and if it has a spatial anchor assigned.</span></span>

> [!TIP]
> <span data-ttu-id="5ba9c-233">尝试询问不存在的被跟踪对象，并了解机器人的响应方式。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-233">Try out asking for an **Tracked Objects** that does not exist and hear how the bot responds.</span></span>

## <a name="congratulations"></a><span data-ttu-id="5ba9c-234">祝贺</span><span class="sxs-lookup"><span data-stu-id="5ba9c-234">Congratulations</span></span>

<span data-ttu-id="5ba9c-235">在本教程中，你了解了如何通过自然语言对话，使用 Azure Bot Framework 与应用程序进行交互。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-235">In this tutorial you learned how Azure Bot Framework can be used to interact with the application via conversation with natural language.</span></span> <span data-ttu-id="5ba9c-236">你了解了如何开发自己的机器人，以及使机器人正常运行的移动组件，</span><span class="sxs-lookup"><span data-stu-id="5ba9c-236">You learned how to develop your own bot and what all the moving pieces are to get it running,</span></span>

## <a name="conclusion"></a><span data-ttu-id="5ba9c-237">结论</span><span class="sxs-lookup"><span data-stu-id="5ba9c-237">Conclusion</span></span>

<span data-ttu-id="5ba9c-238">在整个本系列教程中，你体验了 Azure 云服务如何为应用程序引入令人兴奋的新功能。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-238">Through the course of this tutorial series you experienced how **Azure Cloud services** brought new and exciting features to your application.</span></span>
<span data-ttu-id="5ba9c-239">现在，你可以使用 Azure 存储将数据和图像存储在云中、使用 Azure 自定义视觉关联图像和训练模型、使用 Azure 空间定位点将对象引入本地上下文，以及实现由 LUIS 提供支持的 Azure Bot Framework，以添加对话式机器人，从而形成新的自然语言交互模式   。</span><span class="sxs-lookup"><span data-stu-id="5ba9c-239">You can now store data and images in the cloud with **Azure Storage**, use **Azure Custom Vision** to associate images and train a model, bring objects to a local context with **Azure Spatial Anchors**, and implement **Azure Bot Framework powered by LUIS** to add a conversational bot for a new and natural interaction pattern.</span></span>
