---
title: 设置意向和自然语言理解
description: 完成本课程可以了解如何在混合现实应用程序中设置意向和自然语言理解。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, Azure 空间定位点, 语音识别, Windows 10, LUIS, LUIS 门户, 意图, 实体, 言语, 自然语言理解
ms.localizationpriority: high
ms.openlocfilehash: 49e2b44000add22e924d9552f60b63ac1ac30288
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590359"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="e1543-104">4.设置意向和自然语言理解</span><span class="sxs-lookup"><span data-stu-id="e1543-104">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="e1543-105">本教程探讨 Azure 语音服务的意向识别。</span><span class="sxs-lookup"><span data-stu-id="e1543-105">In this tutorial, you will explore the Azure Speech Service's intent recognition.</span></span> <span data-ttu-id="e1543-106">使用意向识别可以在我们的应用程序中配备 AI 驱动的语音命令，在其中，即使用户讲出非特定的语音命令，系统也仍能识别其意向。</span><span class="sxs-lookup"><span data-stu-id="e1543-106">The intent recognition allows you to equip our application with AI-powered speech commands, where users can say non-specific speech commands and still have their intent understood by the system.</span></span>

## <a name="objectives"></a><span data-ttu-id="e1543-107">目标</span><span class="sxs-lookup"><span data-stu-id="e1543-107">Objectives</span></span>

* <span data-ttu-id="e1543-108">了解如何在 LUIS 门户中设置意向、实体和言语</span><span class="sxs-lookup"><span data-stu-id="e1543-108">Learn how to set up intent, entities, and utterances in the LUIS portal</span></span>
* <span data-ttu-id="e1543-109">了解如何在应用程序中实现意向和自然语言理解</span><span class="sxs-lookup"><span data-stu-id="e1543-109">Learn how to implement intent and natural language understanding in our application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="e1543-110">准备场景</span><span class="sxs-lookup"><span data-stu-id="e1543-110">Preparing the scene</span></span>

<span data-ttu-id="e1543-111">在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中，使用“添加组件”按钮将“Lunarcom 意向识别器(脚本)”组件添加到 Lunarcom 对象中：   </span><span class="sxs-lookup"><span data-stu-id="e1543-111">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Intent Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

<span data-ttu-id="e1543-113">在“项目”窗口中导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件” > “RocketLauncher”文件夹，将“RocketLauncher_Complete”预制件拖放到“层次结构”窗口中，并将其放在相机前面的适当位置，例如：     </span><span class="sxs-lookup"><span data-stu-id="e1543-113">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher_Complete** prefab into your Hierarchy window, and place it at a suitable location in front of the camera, for example:</span></span>

* <span data-ttu-id="e1543-114">变换 **位置** X = 0，Y = -0.4，Z = 1</span><span class="sxs-lookup"><span data-stu-id="e1543-114">Transform **Position** X = 0, Y = -0.4, Z = 1</span></span>
* <span data-ttu-id="e1543-115">变换 **位置** X = 0，Y = 90，Z = 0</span><span class="sxs-lookup"><span data-stu-id="e1543-115">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

<span data-ttu-id="e1543-117">在“层次结构”窗口中再次选择“Lunarcom”对象，展开“RocketLauncher_Complete” > “Button”对象，并将“Button”对象的每个子对象分配到相应的“Lunar Launcher 按钮”字段中：     </span><span class="sxs-lookup"><span data-stu-id="e1543-117">In the Hierarchy window, select the **Lunarcom** object again, then expand the **RocketLauncher_Complete** > **Button** object and assign each of the **Buttons** object's child objects to the corresponding **Lunar Launcher Buttons** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a><span data-ttu-id="e1543-119">创建 Azure 语言理解资源</span><span class="sxs-lookup"><span data-stu-id="e1543-119">Creating the Azure Language Understanding resource</span></span>

<span data-ttu-id="e1543-120">在本部分，你将为要在下一部分创建的语言理解智能服务 (LUIS) 应用创建 Azure 预测资源。</span><span class="sxs-lookup"><span data-stu-id="e1543-120">In this section, you will create an Azure prediction resource for the Language Understanding Intelligent Service (LUIS) app you will create in the next section.</span></span>

<span data-ttu-id="e1543-121">登录到 <a href="https://portal.azure.com" target="_blank">Azure</a> 并单击“创建资源”。 </span><span class="sxs-lookup"><span data-stu-id="e1543-121">Sign in to <a href="https://portal.azure.com" target="_blank">Azure</a> and click **Create a resource**.</span></span> <span data-ttu-id="e1543-122">然后搜索并选择“语言理解”： </span><span class="sxs-lookup"><span data-stu-id="e1543-122">Then search for and select **Language Understanding**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

<span data-ttu-id="e1543-124">单击“创建”按钮创建此服务的实例： </span><span class="sxs-lookup"><span data-stu-id="e1543-124">Click the **Create** button to create an instance of this service:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

<span data-ttu-id="e1543-126">在“创建”页上，单击“预测”选项并输入以下值： </span><span class="sxs-lookup"><span data-stu-id="e1543-126">On the Create page, click the **Prediction** option and enter the following values:</span></span>

* <span data-ttu-id="e1543-127">对于“订阅”，如果你有试用版订阅，请选择“免费试用”，否则请选择其他订阅之一  </span><span class="sxs-lookup"><span data-stu-id="e1543-127">For **Subscription**, select **Free Trail** if you have a trial subscription, otherwise, select one of your other subscriptions</span></span>
* <span data-ttu-id="e1543-128">对于“资源组”，请单击“新建”链接，输入适当的名称（例如 MRKT-Tutorials），然后单击“确定” </span><span class="sxs-lookup"><span data-stu-id="e1543-128">For the **Resource group**, click the **Create new** link, enter a suitable name, for example, *MRKT-Tutorials*, and then click on **OK**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="e1543-130">截至编写本文时，无需创建创作资源，因为在下一部分创建语言理解智能服务 (LUIS) 时，系统会在 LUIS 中自动生成一个创作试用密钥。</span><span class="sxs-lookup"><span data-stu-id="e1543-130">As of the time of this writing, you do not need to create an authoring resource because an authoring trial key will automatically be generated within LUIS when you create the Language Understanding Intelligent Service (LUIS) in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="e1543-131">如果 Azure 帐户中已有另一个适当的资源组（例如，如果已完成 [Azure 空间定位点](mr-learning-asa-01.md)教程），则可以使用此资源组，而无需创建新资源组。</span><span class="sxs-lookup"><span data-stu-id="e1543-131">If you already have another suitable resource group in your Azure account, for example, if you completed the [Azure Spatial Anchors](mr-learning-asa-01.md) tutorial, you may use this resource group instead of creating a new one.</span></span>

<span data-ttu-id="e1543-132">仍在“创建”页上，输入以下值：</span><span class="sxs-lookup"><span data-stu-id="e1543-132">While still on the Create page, enter the following values:</span></span>

* <span data-ttu-id="e1543-133">对于“名称”，请输入服务的适当名称，例如 *MRTK-Tutorials-AzureSpeechServices* </span><span class="sxs-lookup"><span data-stu-id="e1543-133">For **Name**, enter a suitable name for the service, for example, *MRTK-Tutorials-AzureSpeechServices*</span></span>
* <span data-ttu-id="e1543-134">对于“预测位置”，请选择与应用用户的实际位置靠近的位置，例如“(美国)美国西部”  </span><span class="sxs-lookup"><span data-stu-id="e1543-134">For **Prediction location**, choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="e1543-135">对于“预测定价层”，根据本教程的目的，请选择“F0 (每秒 5 次调用，每月 1 万次调用)”  </span><span class="sxs-lookup"><span data-stu-id="e1543-135">For **Prediction pricing tier**, for the purpose of this tutorial, select **F0 (5 Calls per second, 10K Calls per month)**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

<span data-ttu-id="e1543-137">接下来，单击“查看 + 创建”选项卡，复查详细信息，然后单击页面底部的“创建”按钮，以创建资源和新资源组（如果配置为创建资源组） ：</span><span class="sxs-lookup"><span data-stu-id="e1543-137">Next, click on **Review + create** tab, review the details, and then click the **Create** button, located at the bottom of the page, to create the resource, as well as, the new resource group if you configured one to be created:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> <span data-ttu-id="e1543-139">单击“创建”按钮后，必须等待服务创建完成，这可能需要几分钟时间。</span><span class="sxs-lookup"><span data-stu-id="e1543-139">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

<span data-ttu-id="e1543-140">资源创建过程完成后，将看到消息“部署完成”： </span><span class="sxs-lookup"><span data-stu-id="e1543-140">Once the resource creation process is completed, you will see the message **Your deployment is complete**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a><span data-ttu-id="e1543-142">创建语言理解智能服务 (LUIS)</span><span class="sxs-lookup"><span data-stu-id="e1543-142">Creating the Language Understanding Intelligent Service (LUIS)</span></span>

<span data-ttu-id="e1543-143">在本部分，你将创建一个 LUIS 应用，配置并训练其预测模型，然后将其连接到在上一步骤中创建的 Azure 预测资源。</span><span class="sxs-lookup"><span data-stu-id="e1543-143">In this section, you will create a LUIS app, configure and train its prediction model, and connect it to the Azure prediction resource you created in the previous step.</span></span>

<span data-ttu-id="e1543-144">具体而言，你将创建以下意向：如果用户讲出要执行某项操作，该应用将对场景中的三个红色按钮之一（具体取决于用户引用的按钮）触发 Interactable.OnClick() 事件。</span><span class="sxs-lookup"><span data-stu-id="e1543-144">Specifically, you will create an intent that if the user says an action should be taken, the app will trigger the Interactable.OnClick() event on one of the three red buttons in the scene, depending on which button the user references.</span></span>

<span data-ttu-id="e1543-145">例如，如果用户讲出“继续发射火箭”，则该应用将预测出“继续”表示应执行某项“操作”，而“目标”Interactable.OnClick() 事件发生在“发射”按钮上。     </span><span class="sxs-lookup"><span data-stu-id="e1543-145">For example, if the user says **go ahead and launch the rocket**, the app will predict that **go ahead** means some **action** should be taken, and that the Interactable.OnClick() event to **target** is on the **launch** button.</span></span>

<span data-ttu-id="e1543-146">若要实现此目的，请执行以下主要步骤：</span><span class="sxs-lookup"><span data-stu-id="e1543-146">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="e1543-147">创建 LUIS 应用</span><span class="sxs-lookup"><span data-stu-id="e1543-147">Create a LUIS app</span></span>
2. <span data-ttu-id="e1543-148">创建意向</span><span class="sxs-lookup"><span data-stu-id="e1543-148">Create intents</span></span>
3. <span data-ttu-id="e1543-149">创建示例言语</span><span class="sxs-lookup"><span data-stu-id="e1543-149">Create example utterances</span></span>
4. <span data-ttu-id="e1543-150">创建实体</span><span class="sxs-lookup"><span data-stu-id="e1543-150">Create entities</span></span>
5. <span data-ttu-id="e1543-151">将实体分配到示例言语</span><span class="sxs-lookup"><span data-stu-id="e1543-151">Assign entities to the example utterances</span></span>
6. <span data-ttu-id="e1543-152">训练、测试并发布应用</span><span class="sxs-lookup"><span data-stu-id="e1543-152">Train, test, and publish the app</span></span>
7. <span data-ttu-id="e1543-153">将 Azure 预测资源分配到应用</span><span class="sxs-lookup"><span data-stu-id="e1543-153">Assign an Azure prediction resource to the app</span></span>

### <a name="1-create-a-luis-app"></a><span data-ttu-id="e1543-154">1.创建 LUIS 应用</span><span class="sxs-lookup"><span data-stu-id="e1543-154">1. Create a LUIS app</span></span>

<span data-ttu-id="e1543-155">使用在上一部分创建 Azure 资源时所用的同一用户帐户登录到 <a href="https://www.luis.ai" target="_blank">LUIS</a>，选择所在的国家/地区，然后同意使用条款。</span><span class="sxs-lookup"><span data-stu-id="e1543-155">Using the same user account you used when creating the Azure resource in the previous section, sign in to <a href="https://www.luis.ai" target="_blank">LUIS</a>, select your country, and agree to the terms of use.</span></span> <span data-ttu-id="e1543-156">在下一步骤中看到“链接 Azure 帐户”的提示时，请选择“继续使用试用密钥”，以改用 Azure 创作资源。  </span><span class="sxs-lookup"><span data-stu-id="e1543-156">In the next step, when asked to **Link your Azure account**, choose **Continue using your trial key**, to use an Azure authoring resource instead.</span></span>

> [!NOTE]
> <span data-ttu-id="e1543-157">如果你已注册 LUIS 但创作试用密钥已过期，可以参阅[迁移到 Azure 资源创作密钥](/azure/cognitive-services/luis/luis-migration-authoring)文档，将 LUIS 创作资源切换到 Azure。</span><span class="sxs-lookup"><span data-stu-id="e1543-157">If you have already signed up for LUIS and your authoring trial key has expired, you can refer to the [Migrate to an Azure resource authoring key](/azure/cognitive-services/luis/luis-migration-authoring) documentation to switch your LUIS authoring resource to Azure.</span></span>

<span data-ttu-id="e1543-158">登录后，单击“新建应用”并在“创建新应用”弹出窗口中输入以下值 ：</span><span class="sxs-lookup"><span data-stu-id="e1543-158">Once signed in, click **New app** and enter the following values in the **Create new app** popup window:</span></span>

* <span data-ttu-id="e1543-159">对于“名称”，请输入适当的名称，例如 *MRTK Tutorials - AzureSpeechServices* </span><span class="sxs-lookup"><span data-stu-id="e1543-159">For **Name**, enter a suitable name, for example, *MRTK Tutorials - AzureSpeechServices*</span></span>
* <span data-ttu-id="e1543-160">对于“区域性”，请选择“英语”  </span><span class="sxs-lookup"><span data-stu-id="e1543-160">For **Culture**, select **English**</span></span>
* <span data-ttu-id="e1543-161">对于“说明”，请选择性地输入适当的说明 </span><span class="sxs-lookup"><span data-stu-id="e1543-161">For **Description**, optionally enter a suitable description</span></span>
* <span data-ttu-id="e1543-162">对于“预测资源”，根据下拉列表选择已在 Azure 门户中创建的预测资源。</span><span class="sxs-lookup"><span data-stu-id="e1543-162">For **Prediction resource**, select the prediction resource by dropdown list that had been created azure portal.</span></span>

<span data-ttu-id="e1543-163">然后单击“完成”按钮创建新应用： </span><span class="sxs-lookup"><span data-stu-id="e1543-163">Then click the **Done** button to create the new app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

<span data-ttu-id="e1543-165">创建新应用后，你将转到该应用的“仪表板”页： </span><span class="sxs-lookup"><span data-stu-id="e1543-165">When the new app has been created, you will be taken to that app's **Dashboard** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a><span data-ttu-id="e1543-167">2.创建意向</span><span class="sxs-lookup"><span data-stu-id="e1543-167">2. Create intents</span></span>

<span data-ttu-id="e1543-168">在“仪表板”页上，导航到“生成”>“应用资产”>“意向”页，然后单击“创建”，并在“创建新意向”弹出窗口中输入以下值  ：</span><span class="sxs-lookup"><span data-stu-id="e1543-168">From the Dashboard page, navigate to the Build > App Assets > **Intents** page, then click **Create** and enter the following value in the **Create new intent** popup window:</span></span>

* <span data-ttu-id="e1543-169">对于“意向名称”，请输入 **PressButton** </span><span class="sxs-lookup"><span data-stu-id="e1543-169">For **Intent name**, enter **PressButton**</span></span>

<span data-ttu-id="e1543-170">然后单击“完成”按钮创建新意向： </span><span class="sxs-lookup"><span data-stu-id="e1543-170">Then click the **Done** button to create the new intent:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> <span data-ttu-id="e1543-172">在本教程中，Unity 项目将按名称（即“PressButton”）引用此意向。</span><span class="sxs-lookup"><span data-stu-id="e1543-172">For the purpose of this tutorial, your Unity project will reference this intent by its name, i.e. 'PressButton'.</span></span> <span data-ttu-id="e1543-173">因此，为意向指定完全相同的名称极其重要。</span><span class="sxs-lookup"><span data-stu-id="e1543-173">Consequently, it is extremely important that you name your intent exactly the same.</span></span>

<span data-ttu-id="e1543-174">创建新意向后，你将转到该意向的页面：</span><span class="sxs-lookup"><span data-stu-id="e1543-174">When the new intent has been created, you will be taken to that intent's page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a><span data-ttu-id="e1543-176">3.创建示例言语</span><span class="sxs-lookup"><span data-stu-id="e1543-176">3. Create example utterances</span></span>

<span data-ttu-id="e1543-177">将以下示例言语添加到 **PressButton** 意向的“示例言语”列表中： </span><span class="sxs-lookup"><span data-stu-id="e1543-177">To the **PressButton** intent's **Example utterance** list, add the following example utterances:</span></span>

* <span data-ttu-id="e1543-178">激活发射顺序</span><span class="sxs-lookup"><span data-stu-id="e1543-178">activate launch sequence</span></span>
* <span data-ttu-id="e1543-179">显示位置提示</span><span class="sxs-lookup"><span data-stu-id="e1543-179">show me a placement hint</span></span>
* <span data-ttu-id="e1543-180">启动发射顺序</span><span class="sxs-lookup"><span data-stu-id="e1543-180">initiate the launch sequence</span></span>
* <span data-ttu-id="e1543-181">按下位置提示按钮</span><span class="sxs-lookup"><span data-stu-id="e1543-181">press placement hints button</span></span>
* <span data-ttu-id="e1543-182">给予提示</span><span class="sxs-lookup"><span data-stu-id="e1543-182">give me a hint</span></span>
* <span data-ttu-id="e1543-183">按下发射按钮</span><span class="sxs-lookup"><span data-stu-id="e1543-183">push the launch button</span></span>
* <span data-ttu-id="e1543-184">我需要提示</span><span class="sxs-lookup"><span data-stu-id="e1543-184">i need a hint</span></span>
* <span data-ttu-id="e1543-185">按下重置按钮</span><span class="sxs-lookup"><span data-stu-id="e1543-185">press the reset button</span></span>
* <span data-ttu-id="e1543-186">重置体验的时间</span><span class="sxs-lookup"><span data-stu-id="e1543-186">time to reset the experience</span></span>
* <span data-ttu-id="e1543-187">继续发射火箭</span><span class="sxs-lookup"><span data-stu-id="e1543-187">go ahead and launch the rocket</span></span>

<span data-ttu-id="e1543-188">添加所有示例言语后，PressButton 意向页应如下所示：</span><span class="sxs-lookup"><span data-stu-id="e1543-188">When all the example utterances have been added, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> <span data-ttu-id="e1543-190">在本教程中，Unity 项目将引用词语“提示”、“重置”和“发射”。</span><span class="sxs-lookup"><span data-stu-id="e1543-190">For the purpose of this tutorial, your Unity project will reference the words 'hint', 'hints', 'reset', and 'launch'.</span></span> <span data-ttu-id="e1543-191">因此，以完全相同的方式拼写这些词语极其重要。</span><span class="sxs-lookup"><span data-stu-id="e1543-191">Consequently, it is extremely important that you spell these words in the exact same way.</span></span>

### <a name="4-create-entities"></a><span data-ttu-id="e1543-192">4.创建实体</span><span class="sxs-lookup"><span data-stu-id="e1543-192">4. Create entities</span></span>

<span data-ttu-id="e1543-193">从 PressButton 意向页导航到“生成”>“应用资产”>“实体”页，然后单击“创建”，并在“创建新实体”弹出窗口中输入以下值  ：</span><span class="sxs-lookup"><span data-stu-id="e1543-193">From the PressButton intent page, navigate to the Build > App Assets > **Entities** page, then click **Create** and enter the following values in the **Create new entity** popup window:</span></span>

* <span data-ttu-id="e1543-194">对于“实体名称”，请输入 **Action** </span><span class="sxs-lookup"><span data-stu-id="e1543-194">For **Entity name**, enter **Action**</span></span>
* <span data-ttu-id="e1543-195">对于“实体类型”，选择“机器学习” </span><span class="sxs-lookup"><span data-stu-id="e1543-195">For **Entity type**, select **Machine learned**</span></span>

<span data-ttu-id="e1543-196">然后，单击“创建”按钮来创建新的实体：</span><span class="sxs-lookup"><span data-stu-id="e1543-196">Then click the **Create** button to create the new entity:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

<span data-ttu-id="e1543-198">**重复** 上述步骤创建名为 **Target** 的另一个实体，因此现在有名为 Action 和 Target 的两个实体：</span><span class="sxs-lookup"><span data-stu-id="e1543-198">**Repeat** the previous step to create another entity named **Target**, so you have two entities named Action and Target:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> <span data-ttu-id="e1543-200">在本教程中，Unity 项目将按名称（即“Action”和“Target”）引用这些实体。</span><span class="sxs-lookup"><span data-stu-id="e1543-200">For the purpose of this tutorial, your Unity project will reference these entities by their names, i.e. 'Action' and 'Target'.</span></span> <span data-ttu-id="e1543-201">因此，为实体指定完全相同的名称极其重要。</span><span class="sxs-lookup"><span data-stu-id="e1543-201">Consequently, it is extremely important that you name your entities exactly the same.</span></span>

### <a name="5-assign-entities-to-the-example-utterances"></a><span data-ttu-id="e1543-202">5.将实体分配到示例言语</span><span class="sxs-lookup"><span data-stu-id="e1543-202">5. Assign entities to the example utterances</span></span>

<span data-ttu-id="e1543-203">从“实体”页导航回到 **PressButton** 意向页。</span><span class="sxs-lookup"><span data-stu-id="e1543-203">From the Entities page, navigate back to the **PressButton** intent page.</span></span>

<span data-ttu-id="e1543-204">返回到 PressButton 意向页后，依次单击单词“继”和“续”，然后从上下文弹出菜单中选择“Action (简单)”，将“继续”标记为 **Action** 实体值：    </span><span class="sxs-lookup"><span data-stu-id="e1543-204">Once back on the the PressButton intent page, click on the word **go** and then on the word **ahead**, and then select **Action (Simple)** from the contextual popup menu to label **go ahead** as an **Action** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

<span data-ttu-id="e1543-206">短语“继续”现在定义为 **Action** 实体值。 </span><span class="sxs-lookup"><span data-stu-id="e1543-206">The **go ahead** phrase is now defined as an **Action** entity value.</span></span> <span data-ttu-id="e1543-207">现在，你可以看到“继续”一词下方的操作实体值：</span><span class="sxs-lookup"><span data-stu-id="e1543-207">Now you can notice the action entity value under the word go ahead:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> <span data-ttu-id="e1543-209">上图中标签下方的红线表示尚未预测实体值，在下一部分训练模型时将解决此问题。</span><span class="sxs-lookup"><span data-stu-id="e1543-209">The red line you see under the label in the image above indicates that the entity value has not been predicted, this will be resolved when you train the model in the next section.</span></span>

<span data-ttu-id="e1543-210">接下来单击词语“发射”，然后从上下文弹出菜单中选择“Target (简单)”，将“发射”标记为 **Target** 实体值：   </span><span class="sxs-lookup"><span data-stu-id="e1543-210">Next, click on the word **launch**, and then select **Target (Simple)** from the contextual popup menu to label **launch** as a **Target** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

<span data-ttu-id="e1543-212">现将“启动”一词定义为目标实体值。你可以看到“启动”一词下方的目标实体值 ：</span><span class="sxs-lookup"><span data-stu-id="e1543-212">The **launch** word is now defined as a **Target** entity value.Now you can notice the Target entity value under the word launch :</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

<span data-ttu-id="e1543-214">PressButton 意向示例言语“继续发射火箭”现已配置为按如下所示进行预测：</span><span class="sxs-lookup"><span data-stu-id="e1543-214">The PressButton intent example utterance 'go ahead and launch the rocket' is now configured to be predicted as follows:</span></span>

* <span data-ttu-id="e1543-215">意向：PressButton</span><span class="sxs-lookup"><span data-stu-id="e1543-215">Intent: PressButton</span></span>
* <span data-ttu-id="e1543-216">Action 实体：继续</span><span class="sxs-lookup"><span data-stu-id="e1543-216">Action entity: go ahead</span></span>
* <span data-ttu-id="e1543-217">Target 实体：发射</span><span class="sxs-lookup"><span data-stu-id="e1543-217">Target entity: launch</span></span>

<span data-ttu-id="e1543-218">**重复** 上述两步过程，将 Action 和 Target 实体标签分配到每个示例言语，请记住，应将以下词语标记为 **Target** 实体：</span><span class="sxs-lookup"><span data-stu-id="e1543-218">**Repeat** the previous two-step process to assign an Action and a Target entity label to each of the example utterances, keeping in mind that the following words should be labeled as **Target** entities:</span></span>

* <span data-ttu-id="e1543-219">**提示**（针对 Unity 项目中的 HintsButton）</span><span class="sxs-lookup"><span data-stu-id="e1543-219">**hint** (targets the HintsButton in the Unity project)</span></span>
* <span data-ttu-id="e1543-220">**提示**（针对 Unity 项目中的 HintsButton）</span><span class="sxs-lookup"><span data-stu-id="e1543-220">**hints** (targets HintsButton in the Unity project)</span></span>
* <span data-ttu-id="e1543-221">**重置**（针对 Unity 项目中的 ResetButton）</span><span class="sxs-lookup"><span data-stu-id="e1543-221">**reset** (targets the ResetButton in the Unity project)</span></span>
* <span data-ttu-id="e1543-222">**发射**（针对 Unity 项目中的 LaunchButton）</span><span class="sxs-lookup"><span data-stu-id="e1543-222">**launch** (targets the LaunchButton in the Unity project)</span></span>

<span data-ttu-id="e1543-223">标记所有示例言语后，PressButton 意向页应如下所示：</span><span class="sxs-lookup"><span data-stu-id="e1543-223">When all the example utterances have been labeled, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

### <a name="6-train-test-and-publish-the-app"></a><span data-ttu-id="e1543-225">6.训练、测试并发布应用</span><span class="sxs-lookup"><span data-stu-id="e1543-225">6. Train, test, and publish the app</span></span>

<span data-ttu-id="e1543-226">若要训练应用，请单击“训练”按钮并等待训练过程完成： </span><span class="sxs-lookup"><span data-stu-id="e1543-226">To train the app, click the **Train** button and wait for the training process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> <span data-ttu-id="e1543-228">在上图中可以发现，所有标签下面的红线都已删除，这表示已预测所有实体值。</span><span class="sxs-lookup"><span data-stu-id="e1543-228">As you can see in the image above, the red lines under all the labels have been removed, indicating that all the entity values have been predicted.</span></span> <span data-ttu-id="e1543-229">另外可以看到，“训练”按钮左侧的状态图标颜色已从红色变为绿色。</span><span class="sxs-lookup"><span data-stu-id="e1543-229">Also notice that the status icon to the left of the Train button has changed color from red to green.</span></span>

<span data-ttu-id="e1543-230">处理完训练后，单击“测试”按钮，然后键入“继续发射火箭”并按 Enter 键：  </span><span class="sxs-lookup"><span data-stu-id="e1543-230">When the training is finished processing, click the **Test** button, then type in **go ahead and launch the rocket** and press the Enter key:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

<span data-ttu-id="e1543-232">处理测试言语后，单击“检查”以查看测试结果： </span><span class="sxs-lookup"><span data-stu-id="e1543-232">When the test utterance has been processed, click **Inspect** to see the test result:</span></span>

* <span data-ttu-id="e1543-233">意向：PressButton（98.5% 确定性）</span><span class="sxs-lookup"><span data-stu-id="e1543-233">Intent: PressButton (with a 98.5% certainty)</span></span>
* <span data-ttu-id="e1543-234">Action 实体：继续</span><span class="sxs-lookup"><span data-stu-id="e1543-234">Action entity: go ahead</span></span>
* <span data-ttu-id="e1543-235">Target 实体：发射</span><span class="sxs-lookup"><span data-stu-id="e1543-235">Target entity: launch</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

<span data-ttu-id="e1543-237">若要发布应用，请单击右上方的“发布”按钮，然后在“选择发布槽和设置”弹出窗口中，选择“生产”并单击“完成”按钮   ：</span><span class="sxs-lookup"><span data-stu-id="e1543-237">To publish the app, click the **Publish** button in the top right, then in the **Choose your publishing slot and settings** popup window, select **Production** and click the **Done** button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

<span data-ttu-id="e1543-239">等待发布过程完成：</span><span class="sxs-lookup"><span data-stu-id="e1543-239">Wait for the publishing process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

<span data-ttu-id="e1543-241">导航到“管理”>“应用程序设置”>“Azure 资源”页，“Azure 资源”页应如下所示：</span><span class="sxs-lookup"><span data-stu-id="e1543-241">Navigate to the Manage > Application Settings > **Azure Resources** page, your Azure Resources page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-6.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a><span data-ttu-id="e1543-243">将 Unity 项目连接到 LUIS 应用</span><span class="sxs-lookup"><span data-stu-id="e1543-243">Connecting the Unity project to the LUIS app</span></span>

<span data-ttu-id="e1543-244">在“管理”>“应用程序设置”>“Azure 资源”页上，单击“复制”图标复制“示例查询”：   </span><span class="sxs-lookup"><span data-stu-id="e1543-244">On the Manage > Application Settings > **Azure Resources** page, click the **copy** icon to copy the **Example Query**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

<span data-ttu-id="e1543-246">返回到 Unity 项目，在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中，找到“Lunarcom 意向识别器(脚本)”组件，并按如下所述对其进行配置：  </span><span class="sxs-lookup"><span data-stu-id="e1543-246">Back in your Unity project, in the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Intent Recognizer (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="e1543-247">在“LUIS 终结点”字段中，粘贴在上一步骤中复制的“示例查询”：  </span><span class="sxs-lookup"><span data-stu-id="e1543-247">In the **LUIS Endpoint** field, past the **Example Query** you copied in the previous step:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a><span data-ttu-id="e1543-249">测试和改善意向识别</span><span class="sxs-lookup"><span data-stu-id="e1543-249">Testing and improving the intent recognition</span></span>

<span data-ttu-id="e1543-250">若要在 Unity 编辑器中直接使用意向识别，必须允许开发计算机使用听写。</span><span class="sxs-lookup"><span data-stu-id="e1543-250">To use intent recognition directly in the Unity editor, you must allow your development computer to use dictation.</span></span> <span data-ttu-id="e1543-251">若要验证此设置，请打开 Windows 的“设置”，然后选择“隐私” > “语音”，并确保启用“在线语音识别”：    </span><span class="sxs-lookup"><span data-stu-id="e1543-251">To verify this setting, open Windows **Settings** then choose **Privacy** > **Speech** and ensure **Online speech recognition** is turned on:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

<span data-ttu-id="e1543-253">如果现在进入“游戏”模式，可以先按火箭按钮来测试意向识别。</span><span class="sxs-lookup"><span data-stu-id="e1543-253">If you now enter Game mode, you can test the intent recognition by first pressing the rocket button.</span></span> <span data-ttu-id="e1543-254">假设计算机上配备了麦克风，当你讲出第一个示例言语“继续发射火箭”时，将会看到 LunarModule 发射到了太空： </span><span class="sxs-lookup"><span data-stu-id="e1543-254">Then, assuming your computer has a microphone, when you say the first example utterance, **go ahead and launch the rocket**, you will see the LunarModule launch into space:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

<span data-ttu-id="e1543-256">尝试所有 **示例言语**，然后尝试 **示例言语的一些变体**，以及一些 **随机言语**。</span><span class="sxs-lookup"><span data-stu-id="e1543-256">Try all the **example utterances**, then some **variation of the example utterances**, as well as, a few **random utterances**.</span></span>

<span data-ttu-id="e1543-257">接下来，返回到 <a href="https://www.luis.ai" target="_blank">LUIS</a> 并导航到“生成”>“改善应用性能”>“查看终结点言语”页，使用 **切换** 按钮从默认的“实体视图”切换到“标记视图”，然后查看言语：  </span><span class="sxs-lookup"><span data-stu-id="e1543-257">Next, return to <a href="https://www.luis.ai" target="_blank">LUIS</a> and navigate to Build > Improve app performance > **Review endpoint utterances** page, use the **toggle** button to switch from the default Entities View to **Tokens View**, and then review the utterances:</span></span>

* <span data-ttu-id="e1543-258">在“言语”列中，根据需要更改和删除分配的标签，使之与意向相符 </span><span class="sxs-lookup"><span data-stu-id="e1543-258">In the **Utterance** column, change and remove the assigned labels as needed so they align with your intent</span></span>
* <span data-ttu-id="e1543-259">在“对齐的意向”列中，检查意向是否正确 </span><span class="sxs-lookup"><span data-stu-id="e1543-259">In the **Aligned intent** column, verify that the intent is correct</span></span>
* <span data-ttu-id="e1543-260">在“添加/删除”列中，单击绿色的勾选按钮添加言语，或单击红色的 X 按钮删除言语 </span><span class="sxs-lookup"><span data-stu-id="e1543-260">In the **Add/Delete** column, click the green check mark button to add the utterance or the red x button to delete it</span></span>

<span data-ttu-id="e1543-261">检查所需数目的言语后，单击“训练”按钮以重新训练模型，然后单击“发布”按钮重新发布更新的应用：  </span><span class="sxs-lookup"><span data-stu-id="e1543-261">When you have reviewed as many utterances as you like, click the **Train** button to retrain the model, then the **Publish** button to republish the updated app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> <span data-ttu-id="e1543-263">如果某个终结点言语与 PressButton 意向不一致，但你希望模型知道该言语不包含意向，可将“对齐的意向”更改为“无”。</span><span class="sxs-lookup"><span data-stu-id="e1543-263">If an endpoint utterance does not align with the PressButton intent, but you would like your model to know that the utterance has no intent, you can change the Aligned intent to None.</span></span>

<span data-ttu-id="e1543-264">**重复** 此过程任意次，以改善应用模型。</span><span class="sxs-lookup"><span data-stu-id="e1543-264">**Repeat** this process as many times as you like to improve your app model.</span></span>

## <a name="congratulations"></a><span data-ttu-id="e1543-265">祝贺</span><span class="sxs-lookup"><span data-stu-id="e1543-265">Congratulations</span></span>

<span data-ttu-id="e1543-266">现已在项目中包含了 AI 驱动的语音命令，即使用户没有讲出准确的命令，应用程序也能识别用户的意向。</span><span class="sxs-lookup"><span data-stu-id="e1543-266">Your project now have AI-powered speech commands, allowing your application to recognize the users' intent even if they do not utter precise commands.</span></span> <span data-ttu-id="e1543-267">请在设备上运行该应用程序，以确保功能正常。</span><span class="sxs-lookup"><span data-stu-id="e1543-267">Run the application on your device to ensure the feature is working properly.</span></span>