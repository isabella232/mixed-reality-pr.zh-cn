---
title: 将 Azure 机器人服务与 LUIS 集成
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现 Azure 机器人服务和自然语言理解。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, hololens 2, azure 机器人服务, luis, 自然语言, 对话机器人, azure 云服务, azure 自定义视觉, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 109befea299ba2539e3ab8ee616d3321f89660cd30a831a6833e7bbf51029f98
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206482"
---
# <a name="5-integrating-azure-bot-service"></a>5.集成 Azure 机器人服务

在本教程中，你将了解如何在 HoloLens 2 演示应用程序中使用 Azure 机器人服务添加语言理解 (LUIS)，并让机器人在搜索被跟踪对象时为用户提供帮助  。 本教程分为两部分，在第一部分中，使用 [Bot Composer](/composer/introduction) 作为无代码解决方案来创建机器人，并快速浏览为机器人提供所需数据的 Azure Functions。 在第二部分中，在 Unity 项目中使用“BotManager (脚本)”来利用托管的机器人服务。

## <a name="objectives"></a>目标

## <a name="part-1"></a>第 1 部分

* 了解有关 Azure 机器人服务的基础知识
* 了解如何使用 Bot Composer 创建机器人
* 了解如何使用 Azure Functions 从 Azure 存储提供数据

## <a name="part-2"></a>第 2 部分

* 了解如何在此项目中设置场景以使用 Azure 机器人服务
* 了解如何通过与机器人交谈来设置和查找对象

## <a name="understanding-azure-bot-service"></a>了解 Azure 机器人服务

借助 LUIS，Azure 机器人服务让开发人员能够创建与用户进行自然对话的智能机器人 。 对话机器人是扩展用户与应用程序交互的方式的好方法。 机器人可以充当具有 [QnA Maker](/azure/bot-service/bot-builder-howto-qna?preserve-view=true&tabs=cs&view=azure-bot-service-4.0) 的知识库，借助[语言理解智能服务 (LUIS)](/azure/bot-service/bot-builder-howto-v4-luis?preserve-view=true&tabs=csharp&view=azure-bot-service-4.0) 功能进行复杂的对话。

详细了解 [Azure 机器人服务](/azure/bot-service/bot-service-overview-introduction?preserve-view=true&view=azure-bot-service-4.0)。

## <a name="part-1---creating-the-bot"></a>第 1 部分 - 创建机器人

在 Unity 应用程序中使用机器人之前，必须首先开发机器人，为其提供数据并将其托管在 Azure 上。
机器人的目标是能够说出数据库中存储的被跟踪对象数量，通过被跟踪对象的名称进行查找，以及告诉用户关于被跟踪对象的基本信息 。

### <a name="a-quick-look-into-tracked-objects-azure-function"></a>快速了解被跟踪对象 Azure Functions

你即将开始创建机器人，但是要使其变得有用，你需要为其提供资源，以便机器人从中拉取数据。 由于机器人能够计算被跟踪对象的数量、通过名称查找特定的被跟踪对象以及告知详细信息，因此可使用可以访问 Azure 表存储的简单 Azure Functions 。

下载“被跟踪对象 Azure 函数”项目[AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) 并将其提取到硬盘驱动器。

此 Azure Functions 具有两个操作（Count 和 Find），你可以通过基本的 HTTP GET 调用来调用这两个操作  。 可以在 Visual Studio 中检查代码。

详细了解 [Azure Functions](/azure/azure-functions/functions-overview)。

Count 函数从表存储查询表中的所有 TrackedObject，这非常简单  。 另一方面，Find 函数从 GET 请求中获取名称查询参数，并在表存储中查询匹配的 TrackedObject，然后将 DTO 以 JSON 的形式返回  。

若要直接从 Visual Studio 部署此 Azure 函数，请打开下载的 AzureFunction_TrackedObjectsService 文件夹，并通过 Visual Studio 打开现有的 .sln 文件 ![AzureFunction_TrackedObjectsService 文件夹](images/mr-learning-azure/tutorial5-section3-step1-1.png)  

在 Visual Studio 中加载文件后，在解决方案资源管理器中右键单击“跟踪的对象服务”，然后选择“发布”![发布跟踪的对象服务](images/mr-learning-azure/tutorial5-section3-step1-2.png)

随即将显示“发布”弹出窗口，并请求提供目标平台 选择“Azure”，然后单击“下一步”按钮

![选择目标平台](images/mr-learning-azure/tutorial5-section3-step1-3.png)

在具体目标中，选择“Azure 函数应用(Windows)”，然后单击“下一步”按钮 

![选择目标主机](images/mr-learning-azure/tutorial5-section3-step1-4.png)

如果你未登录到 Azure，请通过 Visual Studio 登录，窗口如下所示

![选择或创建 Azure 函数](images/mr-learning-azure/tutorial5-section3-step1-5.png)

单击加号按钮，在 Azure 帐户中创建新的函数应用

![创建新的函数应用](images/mr-learning-azure/tutorial5-section3-step1-6.png)

* 对于“名称”，请输入服务的适当名称，例如 TrackedObjectsService
* 对于“计划类型”，请选择“消耗”
* 对于“位置”，请选择与应用用户的实际位置靠近的位置，例如“(美国)美国西部”
* 对于“资源组”和“存储”，请选择在先前章节中创建的相应 Azure 组和存储帐户 。

创建函数应用之后，单击“完成”按钮。

![完成创建函数应用](images/mr-learning-azure/tutorial5-section3-step1-7.png)

若要更新连接字符串，单击“托管”选项卡上的 3 个点，然后选择“管理 Azure 应用服务设置”  

![打开“应用程序设置”](images/mr-learning-azure/tutorial5-section3-step1-8.png)

这将打开“应用程序设置”窗口，在此处将“本地”和“远程”的 AzureStorageConnectionString 替换为你的 AzureStorageConnectionString  。 替换后，单击“确定”。

![更新连接字符串](images/mr-learning-azure/tutorial5-section3-step1-8a.png)

现在，单击“发布”按钮，发布函数并等待发布。

发布完成后，单击“操作”部分下的“在 Azure 门户中管理”，转到 Azure 门户中的具体函数，再单击“设置”部分下的“配置” 。 在“应用程序设置”上，需要向存储被跟踪对象的 Azure 存储提供连接字符串 。 单击“新应用程序设置”，并使用其名称(AzureStorageConnectionString)，然后提供正确的连接字符串作为值。 接下来，单击“保存”，现在 Azure Functions 已准备就绪，可以为接下来要创建的机器人提供服务 。

若要获取 Count 和 Find 的 URL，请选择“函数”（位于“函数”部分下） 可在此处找到 Count 和 Find 函数，选择顶部的 Count 函数，可以找到“获取函数 URL”按钮。
按照相同的过程获取 Find 函数 URL。

### <a name="creating-a-conversation-bot"></a>创建对话机器人

可以通过多种方式来开发基于 Bot Framework 的对话机器人。 本课程将使用 [Bot Framework Composer](/composer/) 桌面应用程序，该应用程序是非常适合快速开发的可视化设计器。

可以从 [Github 存储库](https://github.com/microsoft/BotFramework-Composer/releases)下载最新版本。 它适用于 Windows、Mac 和 Linux。

安装 Bot Framework Composer 后，启动应用程序，你应该会看到以下界面：

![Bot Framework Composer 主页](images/mr-learning-azure/tutorial5-section4-step1-1.png)

我们准备了一个机器人构建器项目，可提供本教程所需的对话和触发器。 下载 Bot Framework Composer 项目[BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) 并将其提取到硬盘驱动器中。

在顶部栏上，单击“打开”，然后选择你下载的 Bot Framework 项目，该项目名为 TrackedObjectsBot 。 项目完全加载后，你应该会看到项目已准备就绪。

![已打开 TrackedObjectsBot 项目的 Bot Framework Composer](images/mr-learning-azure/tutorial5-section4-step1-2.png)

让我们集中在左侧，你可以在其中看到“对话框面板”。 左侧有一个名为 TrackedObjectsBot 的对话框，你可以在其中看到几个触发器 。

详细了解 [Bot Framework 概念](/composer/concept-dialog)。

这些触发器执行以下操作：

#### <a name="greeting"></a>问候语

这是用户发起对话时聊天机器人的入口 。

![TrackedObjectsBot 项目对话框触发器 - 问候语](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a>AskingForCount

当用户要求计算所有被跟踪对象时，将触发此对话。
下面是触发短语：

>* 全部统计
>* 存储的数量

![TrackedObjectsBot 项目对话框触发器 - AskForCount](images/mr-learning-azure/tutorial5-section4-step1-4.png)

借助 [LUIS](/composer/how-to-use-luis)，用户不必以这种确切的方式询问短语，从而允许用户进行自然对话 。

在此对话中，机器人还将与 Azure Functions 的“Count”对话，稍后再进行详细介绍。

#### <a name="unknown-intent"></a>未知意向

如果来自用户的输入不符合任何其他触发条件，则会触发此对话，并通过再次尝试提问来响应用户。

![TrackedObjectsBot 项目对话框触发器 - 未知意向](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a>FindEntity

最后一个对话为数据创建分支并将其存储在机器人内存中，因此更加复杂。
它要求用户提供被跟踪对象的名称以便了解详细信息、对 Azure Functions 的“Find”执行查询，并使用响应继续进行对话 。

![TrackedObjectsBot 项目对话框触发器 - FindEntity](images/mr-learning-azure/tutorial5-section4-step1-6.png)

如果未找到被跟踪对象，系统将通知用户并结束对话。 找到相关的被跟踪对象后，启动程序将检查可用的属性并报告这些属性。

### <a name="adapting-the-bot"></a>调整机器人

AskingForCount 和 FindEntity 触发器需要与后端通信，这意味着必须添加先前部署的 Azure Functions 的正确 URL  。

在对话框面板上，单击“AskingForCount”，然后找到“发送 HTTP 请求”操作，你可以在此处看到字段“URL”，在此字段中，需要为 Count 函数终结点更改正确的 URL 。

![TrackedObjectsBot 项目 AskingForCount 对话框触发器终结点配置](images/mr-learning-azure/tutorial5-section5-step1-1.png)

最后，查找 FindEntity 触发器并找到“发送 HTTP 请求”操作，在 URL 字段中将 URL 更改为 Find 函数终结点 。

![TrackedObjectsBot 项目 FindEntity 对话框触发器终结点配置](images/mr-learning-azure/tutorial5-section5-step1-2.png)

完成所有设置后，现在即可部署机器人。 由于你已经安装了 Bot Framework Composer，因此可以直接从此处发布机器人。

详细了解[从 Bot Composer 发布机器人](/composer/how-to-publish-bot)。

> [!TIP]
> 通过添加更多触发短语、新响应或对话分支，可以随时与机器人对话。

## <a name="part-2---putting-everything-together-in-unity"></a>第 2 部分 - 将所有内容整合到 Unity 中

### <a name="preparing-the-scene"></a>准备场景

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.AzureCloudServices” > “预制件” > “管理器”文件夹   。

![已选中 ChatBotManager 预制件的 Unity 项目窗口](images/mr-learning-azure/tutorial5-section6-step1-1.png)

从此处将预制件 ChatBotManager 移到场景层次结构中。

将 ChatBotManager 添加到场景后，单击“聊天机器人管理器”组件。
在“检查器”中，你将看到一个空的“Direct Line 密钥”字段，需要填写该字段。

> [!TIP]
> 可以从 Azure 门户中检索密钥，方法是查找在本教程的第一部分中创建的“机器人通道注册”类型的资源。

![仍然选中新增的 ChatBotManager 预制件的 Unity](images/mr-learning-azure/tutorial5-section6-step1-2.png)

现在，将 ChatBotManager 对象与附加到 ChatBotPanel 对象的 ChatBotController 组件连接起来  。 在“层次结构”中，选择“ChatBotPanel”，你将看到一个空的“聊天机器人管理器”字段，从“层次结构”将“ChatBotManager”对象拖动到空的“聊天机器人管理器”字段中   。

![已配置 ChatBotPanel 的 Unity](images/mr-learning-azure/tutorial5-section6-step1-3.png)

接下来，你需要通过一种方法打开 ChatBotPanel，以便用户可以与之进行交互。 在“场景”窗口中，你可能已经注意到，MainMenu 对象上有一个“聊天机器人”侧按钮，可使用该按钮解决此问题。

在“层次结构”中，找到“RootMenu” > “MainMenu” > “SideButtonCollection” > “ButtonChatBot”，然后在“检查器”中找到“ButtonConfigHelper”脚本   。 在那里，你将在 OnClick() 事件回调中看到一个空槽。 将 ChatBotPanel 拖放到事件槽，从下拉列表中导航到 GameObject，然后在子菜单中选择“SetActive (bool)”并启用复选框 。

![已配置 ButtonChatBot 的 Unity](images/mr-learning-azure/tutorial5-section6-step1-4.png)

现在，可以从主菜单启动聊天机器人，并可以使用场景了。

### <a name="putting-the-bot-to-a-test"></a>对机器人进行测试

#### <a name="asking-about-the-quantity-of-tracked-objects"></a>询问被跟踪对象的数量

首先测试如何向机器人询问在数据库中存储的被跟踪对象的数量。

> [!NOTE]
> 这一次必须从 HoloLens 2 运行应用程序，因为你的系统上可能无法使用文本转语音等服务。

在 HoloLens 2 上运行应用程序，然后单击主菜单旁边的“聊天机器人”按钮。
机器人会问候你，现在询问它“我们有多少个对象？”
机器人应会告诉你数量并结束对话。

#### <a name="asking-about-a-tracked-object"></a>询问被跟踪对象

现在再次运行应用程序，这次让机器人“查找被跟踪对象”，机器人将询问你名称，你应回答“汽车”或者数据库中已知的其他被跟踪对象的名称。 机器人将告诉你详细信息，例如描述以及是否分配了空间定位点。

> [!TIP]
> 尝试询问不存在的被跟踪对象，并了解机器人的响应方式。

## <a name="congratulations"></a>祝贺

在本教程中，你了解了如何通过自然语言对话，使用 Azure Bot Framework 与应用程序进行交互。 你了解了如何开发自己的机器人，以及使机器人正常运行的移动组件，

## <a name="conclusion"></a>结论

在整个本系列教程中，你体验了 Azure 云服务如何为应用程序引入令人兴奋的新功能。
现在，你可以使用 Azure 存储将数据和图像存储在云中、使用 Azure 自定义视觉关联图像和训练模型、使用 Azure 空间定位点将对象引入本地上下文，以及实现由 LUIS 提供支持的 Azure Bot Framework，以添加对话式机器人，从而形成新的自然语言交互模式   。