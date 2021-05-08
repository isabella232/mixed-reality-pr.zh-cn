---
title: Unity 中的语音输入
description: 了解 Unity 如何公开向 Windows Mixed Reality 应用程序添加语音输入、语音识别和听写的三种方法。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 语音输入，KeywordRecognizer，GrammarRecognizer，麦克风，听写，语音，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，MRTK，混合现实工具包
ms.openlocfilehash: 6b040443606e05843f85b2f74f5ea812daafba31
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489197"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="1c407-104">Unity 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="1c407-104">Voice input in Unity</span></span>

> [!CAUTION]
> <span data-ttu-id="1c407-105">在开始之前，请考虑使用认知语音服务 SDK 的 Unity 插件。</span><span class="sxs-lookup"><span data-stu-id="1c407-105">Before starting, consider using the Unity plug-in for the Cognitive Speech Services SDK.</span></span> <span data-ttu-id="1c407-106">此插件提供更好的语音准确性结果，并可轻松访问语音到文本解码，以及高级语音功能，如对话框、基于意向的交互、翻译、文本到语音合成和自然语言语音识别。</span><span class="sxs-lookup"><span data-stu-id="1c407-106">The plugin has better Speech Accuracy results and easy access to speech-to-text decode, as well as advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis, and natural language speech recognition.</span></span> <span data-ttu-id="1c407-107">若要开始，请查看 [示例和文档](/azure/cognitive-services/speech-service/quickstart-csharp-unity)。</span><span class="sxs-lookup"><span data-stu-id="1c407-107">To get started, check out the [sample and documentation](/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span></span>

<span data-ttu-id="1c407-108">Unity 公开了三种向 Unity 应用程序添加 [语音输入](../../design/voice-input.md) 的方法，这两种方法是 PhraseRecognizer 类型：</span><span class="sxs-lookup"><span data-stu-id="1c407-108">Unity exposes three ways to add [Voice input](../../design/voice-input.md) to your Unity application, the first two of which are types of PhraseRecognizer:</span></span>
* <span data-ttu-id="1c407-109">`KeywordRecognizer`向你的应用程序提供一个要侦听的字符串命令数组</span><span class="sxs-lookup"><span data-stu-id="1c407-109">The `KeywordRecognizer` supplies your app with an array of string commands to listen for</span></span>
* <span data-ttu-id="1c407-110">为 `GrammarRecognizer` 应用程序提供一个 SRGS 文件，用于定义要侦听的特定语法</span><span class="sxs-lookup"><span data-stu-id="1c407-110">The `GrammarRecognizer` gives your app an SRGS file defining a specific grammar to listen for</span></span>
* <span data-ttu-id="1c407-111">`DictationRecognizer`允许你的应用程序侦听任何字词，并向用户提供其语音的注释或其他显示方式</span><span class="sxs-lookup"><span data-stu-id="1c407-111">The `DictationRecognizer` lets your app listen for any word and provide the user with a note or other display of their speech</span></span>

> [!NOTE]
> <span data-ttu-id="1c407-112">不能同时处理听写和短语识别。</span><span class="sxs-lookup"><span data-stu-id="1c407-112">Dictation and phrase recognition can't be handled at the same time.</span></span> <span data-ttu-id="1c407-113">如果 GrammarRecognizer 或 KeywordRecognizer 处于活动状态，则 DictationRecognizer 不能处于活动状态，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="1c407-113">If a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can't be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="1c407-114">启用语音功能</span><span class="sxs-lookup"><span data-stu-id="1c407-114">Enabling the capability for Voice</span></span>

<span data-ttu-id="1c407-115">必须为应用声明 **麦克风** 功能才能使用语音输入。</span><span class="sxs-lookup"><span data-stu-id="1c407-115">The **Microphone** capability must be declared for an app to use Voice input.</span></span>
1. <span data-ttu-id="1c407-116">在 Unity 编辑器中，导航到 "编辑" " **> 项目设置" > Player**</span><span class="sxs-lookup"><span data-stu-id="1c407-116">In the Unity Editor, navigate to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="1c407-117">选择 " **Windows 应用商店** " 选项卡</span><span class="sxs-lookup"><span data-stu-id="1c407-117">Select the **Windows Store** tab</span></span>
3. <span data-ttu-id="1c407-118">在 " **发布设置 > 功能** " 部分中，检查 **麦克风** 功能</span><span class="sxs-lookup"><span data-stu-id="1c407-118">In the **Publishing Settings > Capabilities** section, check the **Microphone** capability</span></span>
4. <span data-ttu-id="1c407-119">在你的 HoloLens 设备上向应用程序授予麦克风访问权限</span><span class="sxs-lookup"><span data-stu-id="1c407-119">Grant permissions to the app for microphone access on your HoloLens device</span></span>
    * <span data-ttu-id="1c407-120">系统会要求你在设备启动时执行此操作，但如果意外单击了 "否"，则可以在设备设置中更改权限</span><span class="sxs-lookup"><span data-stu-id="1c407-120">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="1c407-121">短语识别</span><span class="sxs-lookup"><span data-stu-id="1c407-121">Phrase Recognition</span></span>

<span data-ttu-id="1c407-122">若要使你的应用能够侦听用户所说的特定短语，请采取一些操作，你需要执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="1c407-122">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="1c407-123">使用 或 指定要侦听的 `KeywordRecognizer` 短语 `GrammarRecognizer`</span><span class="sxs-lookup"><span data-stu-id="1c407-123">Specify which phrases to listen for using a `KeywordRecognizer` or `GrammarRecognizer`</span></span>
2. <span data-ttu-id="1c407-124">处理 `OnPhraseRecognized` 事件并采取措施，以与识别的短语相对应</span><span class="sxs-lookup"><span data-stu-id="1c407-124">Handle the `OnPhraseRecognized` event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="1c407-125">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="1c407-125">KeywordRecognizer</span></span>

<span data-ttu-id="1c407-126">\**命名空间\*\*\*：UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="1c407-126">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="1c407-127">**类型**：KeywordRecognizer、PhraseRecognizedEventArgs、SpeechError、SpeechSystemStatus    </span><span class="sxs-lookup"><span data-stu-id="1c407-127">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="1c407-128">我们需要一些 using 语句来保存一些击键：</span><span class="sxs-lookup"><span data-stu-id="1c407-128">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="1c407-129">然后，让我们向类添加几个字段，以存储识别器以及关键字>字典：</span><span class="sxs-lookup"><span data-stu-id="1c407-129">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="1c407-130">现在，向字典添加关键字，例如在 方法 `Start()` 的 中。</span><span class="sxs-lookup"><span data-stu-id="1c407-130">Now add a keyword to the dictionary, for example in of a `Start()` method.</span></span> <span data-ttu-id="1c407-131">本示例中添加了"activate"关键字：</span><span class="sxs-lookup"><span data-stu-id="1c407-131">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="1c407-132">创建关键字识别器，并告知我们想要识别哪些内容：</span><span class="sxs-lookup"><span data-stu-id="1c407-132">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="1c407-133">现在注册 `OnPhraseRecognized` 事件</span><span class="sxs-lookup"><span data-stu-id="1c407-133">Now register for the `OnPhraseRecognized` event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="1c407-134">示例处理程序是：</span><span class="sxs-lookup"><span data-stu-id="1c407-134">An example handler is:</span></span>

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

<span data-ttu-id="1c407-135">最后，开始识别！</span><span class="sxs-lookup"><span data-stu-id="1c407-135">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="1c407-136">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="1c407-136">GrammarRecognizer</span></span>

<span data-ttu-id="1c407-137">\**命名空间\*\*\*：UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="1c407-137">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="1c407-138">**类型**：GrammarRecognizer、PhraseRecognizedEventArgs、SpeechError、SpeechSystemStatus    </span><span class="sxs-lookup"><span data-stu-id="1c407-138">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="1c407-139">如果使用 SRGS 指定识别语法，则使用 GrammarRecognizer。</span><span class="sxs-lookup"><span data-stu-id="1c407-139">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="1c407-140">如果应用不仅仅是几个关键字，或者想要识别更复杂的短语，或者想要轻松打开和关闭命令集，则这非常有用。</span><span class="sxs-lookup"><span data-stu-id="1c407-140">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="1c407-141">有关文件格式 [信息，请参阅：使用 SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) 创建语法。</span><span class="sxs-lookup"><span data-stu-id="1c407-141">See: [Create Grammars Using SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) for file format information.</span></span>

<span data-ttu-id="1c407-142">获得 SRGS 语法后，该语法位于项目的 [StreamingAssets 文件夹中](https://docs.unity3d.com/Manual/StreamingAssets.html)：</span><span class="sxs-lookup"><span data-stu-id="1c407-142">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="1c407-143">创建 `GrammarRecognizer` 并向其传递 SRGS 文件的路径：</span><span class="sxs-lookup"><span data-stu-id="1c407-143">Create a `GrammarRecognizer` and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="1c407-144">现在注册 `OnPhraseRecognized` 事件</span><span class="sxs-lookup"><span data-stu-id="1c407-144">Now register for the `OnPhraseRecognized` event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="1c407-145">你将获得一个回调，其中包含你可以进行相应处理的 SRGS 语法中指定的信息。</span><span class="sxs-lookup"><span data-stu-id="1c407-145">You'll get a callback containing information specified in your SRGS grammar, which you can handle appropriately.</span></span> <span data-ttu-id="1c407-146">数组中将提供大部分重要信息 `semanticMeanings` 。</span><span class="sxs-lookup"><span data-stu-id="1c407-146">Most of the important information will be provided in the `semanticMeanings` array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="1c407-147">最后，开始识别！</span><span class="sxs-lookup"><span data-stu-id="1c407-147">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="1c407-148">听写</span><span class="sxs-lookup"><span data-stu-id="1c407-148">Dictation</span></span>

<span data-ttu-id="1c407-149">**命名空间：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="1c407-149">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="1c407-150">**类型**： *DictationRecognizer*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="1c407-150">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="1c407-151">使用将 `DictationRecognizer` 用户的语音转换为文本。</span><span class="sxs-lookup"><span data-stu-id="1c407-151">Use the `DictationRecognizer` to convert the user's speech to text.</span></span> <span data-ttu-id="1c407-152">DictationRecognizer 公开 [听写](../../design/voice-input.md#dictation) 功能，并支持注册和侦听假设和短语完成的事件，因此，你可以在用户讲话和之后向用户提供反馈。</span><span class="sxs-lookup"><span data-stu-id="1c407-152">The DictationRecognizer exposes [dictation](../../design/voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="1c407-153">`Start()` 和 `Stop()` 方法分别启用和禁用听写识别。</span><span class="sxs-lookup"><span data-stu-id="1c407-153">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="1c407-154">完成识别器后，应使用将其释放， `Dispose()` 以释放它所使用的资源。</span><span class="sxs-lookup"><span data-stu-id="1c407-154">Once done with the recognizer, it should be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="1c407-155">如果未在此之前释放这些资源，它将在垃圾回收期间自动释放这些资源。</span><span class="sxs-lookup"><span data-stu-id="1c407-155">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>

<span data-ttu-id="1c407-156">开始使用听写只需几个步骤：</span><span class="sxs-lookup"><span data-stu-id="1c407-156">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="1c407-157">创建新的 `DictationRecognizer`</span><span class="sxs-lookup"><span data-stu-id="1c407-157">Create a new `DictationRecognizer`</span></span>
2. <span data-ttu-id="1c407-158">处理听写事件</span><span class="sxs-lookup"><span data-stu-id="1c407-158">Handle Dictation events</span></span>
3. <span data-ttu-id="1c407-159">启动 DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="1c407-159">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="1c407-160">启用听写功能</span><span class="sxs-lookup"><span data-stu-id="1c407-160">Enabling the capability for dictation</span></span>

<span data-ttu-id="1c407-161">必须为应用声明 **Internet 客户端** 和 **麦克风** 功能才能使用听写：</span><span class="sxs-lookup"><span data-stu-id="1c407-161">The **Internet Client** and **Microphone** capabilities must be declared for an app to use dictation:</span></span>
1. <span data-ttu-id="1c407-162">在 Unity 编辑器中，参阅 **编辑 > 项目设置 > Player**</span><span class="sxs-lookup"><span data-stu-id="1c407-162">In the Unity Editor, go to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="1c407-163">选择 " **Windows 应用商店** " 选项卡</span><span class="sxs-lookup"><span data-stu-id="1c407-163">Select on the **Windows Store** tab</span></span>
3. <span data-ttu-id="1c407-164">在" **发布设置>功能"部分中** ，检查 **InternetClient** 功能</span><span class="sxs-lookup"><span data-stu-id="1c407-164">In the **Publishing Settings > Capabilities** section, check the **InternetClient** capability</span></span>
    * <span data-ttu-id="1c407-165">（可选）如果还没有启用麦克风，请检查 **麦克风** 功能</span><span class="sxs-lookup"><span data-stu-id="1c407-165">Optionally, if you didn't already enable the microphone, check the **Microphone** capability</span></span>
4. <span data-ttu-id="1c407-166">向应用授予对 HoloLens 设备上麦克风访问权限的权限（如果尚未授予）</span><span class="sxs-lookup"><span data-stu-id="1c407-166">Grant permissions to the app for microphone access on your HoloLens device if you haven't already</span></span>
    * <span data-ttu-id="1c407-167">设备启动时会要求你执行此操作，但如果意外单击了"否"，可以在设备设置中更改权限</span><span class="sxs-lookup"><span data-stu-id="1c407-167">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="1c407-168">听写Recognizer</span><span class="sxs-lookup"><span data-stu-id="1c407-168">DictationRecognizer</span></span>

<span data-ttu-id="1c407-169">创建听写Recognizer，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1c407-169">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="1c407-170">有四个听写事件可以订阅并进行处理来实现听写行为。</span><span class="sxs-lookup"><span data-stu-id="1c407-170">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

<span data-ttu-id="1c407-171">**听写Result**</span><span class="sxs-lookup"><span data-stu-id="1c407-171">**DictationResult**</span></span>

<span data-ttu-id="1c407-172">此事件在用户暂停后触发，通常位于句子末尾。</span><span class="sxs-lookup"><span data-stu-id="1c407-172">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="1c407-173">此处返回完整识别的字符串。</span><span class="sxs-lookup"><span data-stu-id="1c407-173">The full recognized string is returned here.</span></span>

<span data-ttu-id="1c407-174">首先，订阅 `DictationResult` 事件：</span><span class="sxs-lookup"><span data-stu-id="1c407-174">First, subscribe to the `DictationResult` event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="1c407-175">然后处理听写Result 回调：</span><span class="sxs-lookup"><span data-stu-id="1c407-175">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="1c407-176">**听写Hypothesis**</span><span class="sxs-lookup"><span data-stu-id="1c407-176">**DictationHypothesis**</span></span>

<span data-ttu-id="1c407-177">此事件在用户说话时持续触发。</span><span class="sxs-lookup"><span data-stu-id="1c407-177">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="1c407-178">当识别器侦听时，它会提供到目前为止听到的内容的文本。</span><span class="sxs-lookup"><span data-stu-id="1c407-178">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="1c407-179">首先，订阅 `DictationHypothesis` 事件：</span><span class="sxs-lookup"><span data-stu-id="1c407-179">First, subscribe to the `DictationHypothesis` event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="1c407-180">然后处理听写Hypothesis 回调：</span><span class="sxs-lookup"><span data-stu-id="1c407-180">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="1c407-181">**听写完成**</span><span class="sxs-lookup"><span data-stu-id="1c407-181">**DictationComplete**</span></span>

<span data-ttu-id="1c407-182">当识别器停止时，将触发此事件，无论是从"停止 () 调用、发生超时还是出现其他错误。</span><span class="sxs-lookup"><span data-stu-id="1c407-182">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="1c407-183">首先，订阅 `DictationComplete` 事件：</span><span class="sxs-lookup"><span data-stu-id="1c407-183">First, subscribe to the `DictationComplete` event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="1c407-184">然后处理 DictationComplete 回调：</span><span class="sxs-lookup"><span data-stu-id="1c407-184">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="1c407-185">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="1c407-185">**DictationError**</span></span>

<span data-ttu-id="1c407-186">当发生错误时，将激发此事件。</span><span class="sxs-lookup"><span data-stu-id="1c407-186">This event is fired when an error occurs.</span></span>

<span data-ttu-id="1c407-187">首先，订阅该 `DictationError` 事件：</span><span class="sxs-lookup"><span data-stu-id="1c407-187">First, subscribe to the `DictationError` event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="1c407-188">然后处理 DictationError 回调：</span><span class="sxs-lookup"><span data-stu-id="1c407-188">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="1c407-189">一旦你订阅并处理了所关注的听写事件，开始听写识别器即可开始接收事件。</span><span class="sxs-lookup"><span data-stu-id="1c407-189">Once you've subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="1c407-190">如果不再想要保留 DictationRecognizer，则需要取消订阅事件并释放 DictationRecognizer。</span><span class="sxs-lookup"><span data-stu-id="1c407-190">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="1c407-191">**提示**</span><span class="sxs-lookup"><span data-stu-id="1c407-191">**Tips**</span></span>
* <span data-ttu-id="1c407-192">`Start()` 和 `Stop()` 方法分别启用和禁用听写识别。</span><span class="sxs-lookup"><span data-stu-id="1c407-192">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="1c407-193">完成识别器后，必须使用将其释放， `Dispose()` 以释放它所使用的资源。</span><span class="sxs-lookup"><span data-stu-id="1c407-193">Once done with the recognizer, it must be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="1c407-194">如果未在此之前释放这些资源，它将在垃圾回收期间自动释放这些资源。</span><span class="sxs-lookup"><span data-stu-id="1c407-194">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>
* <span data-ttu-id="1c407-195">超时发生在设定的时间段之后。</span><span class="sxs-lookup"><span data-stu-id="1c407-195">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="1c407-196">您可以在事件中检查这些超时 `DictationComplete` 。</span><span class="sxs-lookup"><span data-stu-id="1c407-196">You can check for these timeouts in the `DictationComplete` event.</span></span> <span data-ttu-id="1c407-197">需要注意两个超时：</span><span class="sxs-lookup"><span data-stu-id="1c407-197">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="1c407-198">如果识别器在前五秒内开始播放并且不听到任何音频，则会超时。</span><span class="sxs-lookup"><span data-stu-id="1c407-198">If the recognizer starts and doesn't hear any audio for the first five seconds, it will time out.</span></span>
   2. <span data-ttu-id="1c407-199">如果识别器给出了结果，但随后听到了20秒，则会超时。</span><span class="sxs-lookup"><span data-stu-id="1c407-199">If the recognizer has given a result, but then hears silence for 20 seconds, it will time out.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="1c407-200">使用短语识别和听写</span><span class="sxs-lookup"><span data-stu-id="1c407-200">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="1c407-201">如果你想要在应用中同时使用短语识别和听写，则需要完全关闭一项，然后才能启动另一个。</span><span class="sxs-lookup"><span data-stu-id="1c407-201">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="1c407-202">如果有多个 KeywordRecognizers 正在运行，则可以使用以下操作一次性关闭它们：</span><span class="sxs-lookup"><span data-stu-id="1c407-202">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="1c407-203">在 `Restart()` DictationRecognizer 停止后，可以调用将所有识别器还原到其以前的状态：</span><span class="sxs-lookup"><span data-stu-id="1c407-203">You can call `Restart()` to restore all recognizers to their previous state after the DictationRecognizer has stopped:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="1c407-204">还可以只启动 KeywordRecognizer，这也会重新启动 PhraseRecognitionSystem。</span><span class="sxs-lookup"><span data-stu-id="1c407-204">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="1c407-205">混合现实工具包中的语音输入</span><span class="sxs-lookup"><span data-stu-id="1c407-205">Voice input in Mixed Reality Toolkit</span></span>

<span data-ttu-id="1c407-206">可以在以下演示场景中找到语音输入的 MRTK 示例：</span><span class="sxs-lookup"><span data-stu-id="1c407-206">You can find MRTK examples for voice input in the following demo scenes:</span></span>
* [<span data-ttu-id="1c407-207">听写</span><span class="sxs-lookup"><span data-stu-id="1c407-207">Dictation</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [<span data-ttu-id="1c407-208">语音</span><span class="sxs-lookup"><span data-stu-id="1c407-208">Speech</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a><span data-ttu-id="1c407-209">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="1c407-209">Next Development Checkpoint</span></span>

<span data-ttu-id="1c407-210">如果你遵循我们布局的 Unity 开发检查点旅程，下一个任务是探索混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="1c407-210">If you're following the Unity development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1c407-211">共享体验</span><span class="sxs-lookup"><span data-stu-id="1c407-211">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="1c407-212">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="1c407-212">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>