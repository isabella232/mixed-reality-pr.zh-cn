---
title: Unreal 中的语音输入
description: 了解如何设置和使用适用于 HoloLens 2 设备的 Unreal mixed reality 应用中的语音输入、语音映射和识别。
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality，Unreal，Unreal 引擎4，UE4，HoloLens 2，语音，语音输入，语音识别，混合现实，开发，功能，文档，指南，全息影像，游戏开发，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: c7ac523258dc44aa261470aea8cdf21f32c915b2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010067"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="e24d8-104">Unreal 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="e24d8-104">Voice Input in Unreal</span></span>

<span data-ttu-id="e24d8-105">使用 Unreal 中的语音输入，无需使用手手势即可与全息图进行交互，并且仅支持 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="e24d8-105">Voice input in Unreal allows you to interact with a hologram without having to use hand gestures and is only supported HoloLens 2.</span></span> <span data-ttu-id="e24d8-106">HoloLens 2 上的语音输入由支持所有其他通用 Windows 应用中的语音的同一引擎提供支持，但 Unreal 使用更有限的引擎来处理语音输入。</span><span class="sxs-lookup"><span data-stu-id="e24d8-106">Voice input on HoloLens 2 is powered by the same engine that supports speech in all other Universal Windows Apps, but Unreal uses a more limited engine to process voice input.</span></span> <span data-ttu-id="e24d8-107">这会将 Unreal 中的语音输入功能限制为预定义的语音映射，如以下各节中所述。</span><span class="sxs-lookup"><span data-stu-id="e24d8-107">This limits voice input features in Unreal to predefined speech mappings, which are covered in the following sections.</span></span> 

## <a name="enabling-speech-recognition"></a><span data-ttu-id="e24d8-108">启用语音识别</span><span class="sxs-lookup"><span data-stu-id="e24d8-108">Enabling Speech Recognition</span></span>

<span data-ttu-id="e24d8-109">在 HoloLens 上启用语音识别：</span><span class="sxs-lookup"><span data-stu-id="e24d8-109">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="e24d8-110">选择 " **项目设置" > 平台 > HoloLens > 功能** 并启用 **麦克风**。</span><span class="sxs-lookup"><span data-stu-id="e24d8-110">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="e24d8-111">已在 " **设置" > 隐私 > 语音** "中启用语音识别，然后选择" **英语**"。</span><span class="sxs-lookup"><span data-stu-id="e24d8-111">Enabled speech recognition in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="e24d8-112">语音识别始终在 " **设置** " 应用程序中配置的 Windows 显示语言中工作。</span><span class="sxs-lookup"><span data-stu-id="e24d8-112">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="e24d8-113">建议你同时启用 **在线语音识别** ，以获得最佳的服务质量。</span><span class="sxs-lookup"><span data-stu-id="e24d8-113">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Windows 语音识别设置](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="e24d8-115">当应用程序首次启动时，将显示一个对话框，询问你是否要启用麦克风。</span><span class="sxs-lookup"><span data-stu-id="e24d8-115">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="e24d8-116">选择 **"是"** 将在应用中启动语音输入。</span><span class="sxs-lookup"><span data-stu-id="e24d8-116">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="e24d8-117">语音输入不需要任何特殊的 Windows Mixed Reality Api;它基于现有的 Unreal Engine 4 [输入](https://docs.unrealengine.com/Gameplay/Input/index.html) 映射 API 构建。</span><span class="sxs-lookup"><span data-stu-id="e24d8-117">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="e24d8-118">添加语音映射</span><span class="sxs-lookup"><span data-stu-id="e24d8-118">Adding Speech Mappings</span></span>

<span data-ttu-id="e24d8-119">使用语音输入时，将语音连接到操作非常重要。</span><span class="sxs-lookup"><span data-stu-id="e24d8-119">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="e24d8-120">这些映射会监视用户可能会说出的语音关键字应用，然后发出链接的操作。</span><span class="sxs-lookup"><span data-stu-id="e24d8-120">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="e24d8-121">可以通过以下方式找到语音映射：</span><span class="sxs-lookup"><span data-stu-id="e24d8-121">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="e24d8-122">选择 " **编辑 > 项目设置**"，滚动到 " **引擎** " 部分，然后单击 " **输入**"。</span><span class="sxs-lookup"><span data-stu-id="e24d8-122">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="e24d8-123">添加跳转命令的新语音映射：</span><span class="sxs-lookup"><span data-stu-id="e24d8-123">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="e24d8-124">选择 " **+** **数组元素** " 旁边的图标，然后填写以下值：</span><span class="sxs-lookup"><span data-stu-id="e24d8-124">Select the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="e24d8-125">**操作名称** 的 **jumpWord**</span><span class="sxs-lookup"><span data-stu-id="e24d8-125">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="e24d8-126">**跳转\*\*\*\*语音关键字**</span><span class="sxs-lookup"><span data-stu-id="e24d8-126">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="e24d8-127"> () 的任何英语单词 () 或短句子都可以用作关键字。</span><span class="sxs-lookup"><span data-stu-id="e24d8-127">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![UE4 引擎输入设置](images/unreal/engine-input.png)

<span data-ttu-id="e24d8-129">语音映射可用作操作或轴映射等输入组件或事件图中的蓝图节点。</span><span class="sxs-lookup"><span data-stu-id="e24d8-129">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="e24d8-130">例如，可以链接 "跳转" 命令，根据字词的讲述时间打印出两个不同的日志：</span><span class="sxs-lookup"><span data-stu-id="e24d8-130">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="e24d8-131">双击蓝图以在 **事件图** 中打开它。</span><span class="sxs-lookup"><span data-stu-id="e24d8-131">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="e24d8-132">**右键单击** 并搜索语音映射的 **操作名称** (在本例中为 **JumpWord**) ，然后按 **Enter** 将 " **输入操作** " 节点添加到关系图中。</span><span class="sxs-lookup"><span data-stu-id="e24d8-132">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter** to add an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="e24d8-133">将 **按下** 的 pin 拖放到 " **打印字符串** " 节点，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="e24d8-133">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="e24d8-134">你可以保留已 **释放** 的 pin，而不会对语音映射执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="e24d8-134">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![简单的语音操作](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="e24d8-136">播放应用程序，口述 " **跳转**"，并观看控制台来打印日志！</span><span class="sxs-lookup"><span data-stu-id="e24d8-136">Play the app, say the word **jump**, and watch the console print out the logs!</span></span>

<span data-ttu-id="e24d8-137">这就是在 Unreal 中开始向 HoloLens 应用添加语音输入所需的全部设置。</span><span class="sxs-lookup"><span data-stu-id="e24d8-137">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="e24d8-138">你可以在下面的链接中找到有关语音和交互性的详细信息，并确保考虑你为用户创建的体验。</span><span class="sxs-lookup"><span data-stu-id="e24d8-138">You can find more information on speech and interactivity at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="e24d8-139">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="e24d8-139">Next Development Checkpoint</span></span>

<span data-ttu-id="e24d8-140">如果遵循我们所说的 Unreal 开发旅程，下一项任务就是探索混合现实平台功能和 Api：</span><span class="sxs-lookup"><span data-stu-id="e24d8-140">If you're following the Unreal development journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="e24d8-141">HoloLens 摄像头</span><span class="sxs-lookup"><span data-stu-id="e24d8-141">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="e24d8-142">你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="e24d8-142">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="e24d8-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e24d8-143">See also</span></span>
* [<span data-ttu-id="e24d8-144">语音输入</span><span class="sxs-lookup"><span data-stu-id="e24d8-144">Voice Input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="e24d8-145">凝视和提交</span><span class="sxs-lookup"><span data-stu-id="e24d8-145">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="e24d8-146">本能交互</span><span class="sxs-lookup"><span data-stu-id="e24d8-146">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)

