---
title: 为本地语音到文本翻译添加脱机模式
description: 完成本课程可以了解如何在混合现实应用程序中为本地语音到文本翻译添加脱机模式。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, Azure 空间定位点, 语音识别, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 2e7a48dc4bb64eb177e6fa290f4918345c3d642f
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590149"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="d5479-104">2.为本地语音到文本翻译添加脱机模式</span><span class="sxs-lookup"><span data-stu-id="d5479-104">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="d5479-105">在本教程中，你将添加使用 Azure 语音识别执行命令的功能，以便可以根据定义的单词或短语执行一些操作。</span><span class="sxs-lookup"><span data-stu-id="d5479-105">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="d5479-106">目标</span><span class="sxs-lookup"><span data-stu-id="d5479-106">Objectives</span></span>

* <span data-ttu-id="d5479-107">了解如何使用 Azure 语音识别执行命令</span><span class="sxs-lookup"><span data-stu-id="d5479-107">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="d5479-108">说明</span><span class="sxs-lookup"><span data-stu-id="d5479-108">Instructions</span></span>

<span data-ttu-id="d5479-109">在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中，使用“添加组件”按钮将“Lunarcom 唤醒字词识别器(脚本)”组件添加到 Lunarcom 对象，并按如下所述配置该组件：  </span><span class="sxs-lookup"><span data-stu-id="d5479-109">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="d5479-110">在“唤醒字词”字段中输入适当的短语，例如“激活终端”。</span><span class="sxs-lookup"><span data-stu-id="d5479-110">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="d5479-111">在“解除字词”字段中输入适当的短语，例如“解除终端”。</span><span class="sxs-lookup"><span data-stu-id="d5479-111">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![Unity 编辑器，其中 Lunarcom 唤醒字词识别器脚本组件突出显示](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="d5479-113">MRTK 中未包含“Lunarcom 唤醒字词识别器(脚本)”组件。</span><span class="sxs-lookup"><span data-stu-id="d5479-113">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="d5479-114">本教程的资产中随附了该组件。</span><span class="sxs-lookup"><span data-stu-id="d5479-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="d5479-115">如果现在进入“游戏”模式，与在上一篇教程中一样，默认已启用终端面板，但你现在可以通过讲出解除字词“解除终端”来禁用它：</span><span class="sxs-lookup"><span data-stu-id="d5479-115">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![播放模式中的 Unity 编辑器，其中语音识别器功能正在使用](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="d5479-117">讲出唤醒字词“激活终端”以再次启用终端面板：</span><span class="sxs-lookup"><span data-stu-id="d5479-117">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![播放模式中的 Unity 编辑器，带有活动终端](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="d5479-119">应用程序需要连接到 Azure，因此请确保计算机/设备已连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="d5479-119">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="d5479-120">如果你预计经常无法连接到 Azure，还可以按照[使用语音命令](mr-learning-base-09.md)说明，使用 MRTK 实现语音命令。</span><span class="sxs-lookup"><span data-stu-id="d5479-120">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Using speech commands](mr-learning-base-09.md) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d5479-121">祝贺</span><span class="sxs-lookup"><span data-stu-id="d5479-121">Congratulations</span></span>

<span data-ttu-id="d5479-122">现已实现了由 Azure 提供支持的语音命令。</span><span class="sxs-lookup"><span data-stu-id="d5479-122">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="d5479-123">请在设备上运行该应用程序，以确保功能正常。</span><span class="sxs-lookup"><span data-stu-id="d5479-123">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="d5479-124">下一篇教程将介绍如何使用 Azure 语音翻译来翻译语音。</span><span class="sxs-lookup"><span data-stu-id="d5479-124">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d5479-125">下一教程：3.添加 Azure 认知服务语音翻译组件</span><span class="sxs-lookup"><span data-stu-id="d5479-125">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
