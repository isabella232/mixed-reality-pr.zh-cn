---
title: 添加 Azure 认知服务语音翻译组件
description: 在本课程中，你将学习如何在混合现实应用程序中添加 Azure 认知服务语音翻译。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, Azure 空间定位点, 语音识别, Windows 10, 语音翻译
ms.localizationpriority: high
ms.openlocfilehash: bcc966b63f4c3e5bb9e6d6a38dc7f0312b288402
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590139"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="2713a-104">3.添加 Azure 认知服务语音翻译组件</span><span class="sxs-lookup"><span data-stu-id="2713a-104">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="2713a-105">在本教程中，你将在项目中添加语音翻译，以便可以将语音翻译和听录成三种不同的语言。</span><span class="sxs-lookup"><span data-stu-id="2713a-105">In this tutorial, you will add speech translation to your project which will allow you to translate and transcribed your speech into three different languages.</span></span>

## <a name="objectives"></a><span data-ttu-id="2713a-106">目标</span><span class="sxs-lookup"><span data-stu-id="2713a-106">Objectives</span></span>

* <span data-ttu-id="2713a-107">了解如何集成 Azure 语音翻译</span><span class="sxs-lookup"><span data-stu-id="2713a-107">Learn how to integrate Azure speech translation</span></span>

## <a name="instructions"></a><span data-ttu-id="2713a-108">说明</span><span class="sxs-lookup"><span data-stu-id="2713a-108">Instructions</span></span>

<span data-ttu-id="2713a-109">在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中，使用“添加组件”按钮将“Lunarcom 翻译识别器(脚本)”组件添加到 Lunarcom 对象，并按如下所述配置该组件：   </span><span class="sxs-lookup"><span data-stu-id="2713a-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Translation Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="2713a-110">将“目标语言”更改为所选语言，例如“德语”  </span><span class="sxs-lookup"><span data-stu-id="2713a-110">Change the **Target Language** to a language of your choosing, for example, _German_</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="2713a-112">MRTK 中未包含“Lunarcom 翻译识别器(脚本)”组件。</span><span class="sxs-lookup"><span data-stu-id="2713a-112">The Lunarcom Translation Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="2713a-113">本教程的资产中随附了该组件。</span><span class="sxs-lookup"><span data-stu-id="2713a-113">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="2713a-114">如果现在进入“游戏”模式，可以先按卫星按钮来测试语音翻译。</span><span class="sxs-lookup"><span data-stu-id="2713a-114">If you now enter Game mode, you can test the speech translation by first pressing the satellite button.</span></span> <span data-ttu-id="2713a-115">假设计算机上配备了麦克风，当你讲话时，你的语音将翻译成所选语言，并在终端面板上听录：</span><span class="sxs-lookup"><span data-stu-id="2713a-115">Then, assuming your computer has a microphone, when you say something, your speech will be translated into the chosen language and transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="2713a-117">应用程序需要连接到 Azure，因此请确保计算机/设备已连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="2713a-117">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="2713a-118">祝贺</span><span class="sxs-lookup"><span data-stu-id="2713a-118">Congratulations</span></span>

<span data-ttu-id="2713a-119">项目现在可以成功地将你讲出的词语翻译成多种不同的语言。</span><span class="sxs-lookup"><span data-stu-id="2713a-119">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="2713a-120">请在设备上运行该应用程序，以确保功能正常。</span><span class="sxs-lookup"><span data-stu-id="2713a-120">Run the application on your device to ensure the feature is working properly.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2713a-121">下一教程：4.设置意向和自然语言理解</span><span class="sxs-lookup"><span data-stu-id="2713a-121">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
