---
title: Unity 中的语音输入
description: 了解 Unity 如何公开向 Windows Mixed Reality 应用程序添加语音输入、语音识别和听写的三种方法。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 语音输入，KeywordRecognizer，GrammarRecognizer，麦克风，听写，语音，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，MRTK，混合现实工具包
ms.openlocfilehash: 7268a4df9c7fce03029937c72540ed274574067d
ms.sourcegitcommit: 8c3af63fb49494f75c8ab46236fc3dd8533c1e9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2021
ms.locfileid: "99606112"
---
# <a name="voice-input-in-unity"></a>Unity 中的语音输入

> [!CAUTION]
> 在开始之前，请考虑使用认知语音服务 SDK 的 Unity 插件。 此插件提供更好的语音准确性结果，并可轻松访问语音到文本解码，以及高级语音功能，如对话框、基于意向的交互、翻译、文本到语音合成和自然语言语音识别。 若要开始，请查看 [示例和文档](https://docs.microsoft.com/azure/cognitive-services/speech-service/quickstart-csharp-unity)。

Unity 公开了三种向 Unity 应用程序添加 [语音输入](../../design/voice-input.md) 的方法，这两种方法是 PhraseRecognizer 类型：
* `KeywordRecognizer`向你的应用程序提供一个要侦听的字符串命令数组
* 为 `GrammarRecognizer` 应用程序提供一个 SRGS 文件，用于定义要侦听的特定语法
* `DictationRecognizer`允许你的应用程序侦听任何字词，并向用户提供其语音的注释或其他显示方式

> [!NOTE]
> 不能同时处理听写和短语识别。 如果 GrammarRecognizer 或 KeywordRecognizer 处于活动状态，则 DictationRecognizer 不能处于活动状态，反之亦然。

## <a name="enabling-the-capability-for-voice"></a>启用语音功能

必须为应用声明 **麦克风** 功能才能使用语音输入。
1. 在 Unity 编辑器中，导航到 "编辑" " **> 项目设置" > Player**
2. 选择 " **Windows 应用商店** " 选项卡
3. 在 " **发布设置 > 功能** " 部分中，检查 **麦克风** 功能
4. 在你的 HoloLens 设备上向应用程序授予麦克风访问权限
    * 系统会要求你在设备启动时执行此操作，但如果意外单击了 "否"，则可以在设备设置中更改权限

## <a name="phrase-recognition"></a>短语识别

若要使你的应用能够侦听用户所说的特定短语，请采取一些操作，你需要执行以下操作：
1. 使用或指定要侦听的短语 `KeywordRecognizer``GrammarRecognizer`
2. 处理 `OnPhraseRecognized` 事件，并采取相应的操作来识别已识别的短语

### <a name="keywordrecognizer"></a>KeywordRecognizer

**命名空间：** *UnityEngine*<br>
**类型：** *KeywordRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*

我们需要使用几个语句来保存一些击键：

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

接下来，让我们将一些字段添加到类，以存储识别器和关键字 >操作字典：

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

现在，将关键字添加到字典中，例如，在方法中添加关键字 `Start()` 。 在此示例中，我们要添加 "activate" 关键字：

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

创建关键字识别器并告诉它我们要识别的内容：

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

现在注册 `OnPhraseRecognized` 事件

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

示例处理程序是：

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

最后，开始识别！

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**命名空间：** *UnityEngine*<br>
**类型**： *GrammarRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*

如果要使用 SRGS 指定识别语法，则使用 GrammarRecognizer。 如果你的应用程序包含多个关键字（如果你想要识别更复杂的短语），或者如果你想要轻松打开和关闭命令集，这会很有用。 请参阅： [使用 SRGS XML 创建语法](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) 以获取文件格式信息。

获得 SRGS 语法后，在项目中的 [StreamingAssets 文件夹](https://docs.unity3d.com/Manual/StreamingAssets.html)中：

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

创建 `GrammarRecognizer` 并向其传递 SRGS 文件的路径：

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

现在注册 `OnPhraseRecognized` 事件

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

你将获得一个回调，其中包含你可以进行相应处理的 SRGS 语法中指定的信息。 数组中将提供大部分重要信息 `semanticMeanings` 。

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

最后，开始识别！

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>听写

**命名空间：** *UnityEngine*<br>
**类型**： *DictationRecognizer*、 *SpeechError*、 *SpeechSystemStatus*

使用将 `DictationRecognizer` 用户的语音转换为文本。 DictationRecognizer 公开 [听写](../../design/voice-input.md#dictation) 功能，并支持注册和侦听假设和短语完成的事件，因此，你可以在用户讲话和之后向用户提供反馈。 `Start()` 和 `Stop()` 方法分别启用和禁用听写识别。 完成识别器后，应使用将其释放， `Dispose()` 以释放它所使用的资源。 如果未在此之前释放这些资源，它将在垃圾回收期间自动释放这些资源。

开始使用听写只需几个步骤：
1. 创建新的 `DictationRecognizer`
2. 处理听写事件
3. 启动 DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>启用听写功能

必须为应用声明 **Internet 客户端** 和 **麦克风** 功能才能使用听写：
1. 在 Unity 编辑器中，参阅 **编辑 > 项目设置 > Player**
2. 选择 " **Windows 应用商店** " 选项卡
3. 在 " **发布设置 > 功能** " 部分中，查看 **InternetClient** 功能
    * 如果还没有启用麦克风，可以选择选中 **麦克风** 功能
4. 向应用程序授予对你的 HoloLens 设备上麦克风的访问权限（如果尚未这样做）
    * 系统会要求你在设备启动时执行此操作，但如果意外单击了 "否"，则可以在设备设置中更改权限

### <a name="dictationrecognizer"></a>DictationRecognizer

创建 DictationRecognizer，如下所示：

```
dictationRecognizer = new DictationRecognizer();
```

可以订阅和处理四个听写事件，以实现听写行为。
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

**DictationResult**

此事件在用户暂停之后（通常是在句子结束时）触发。 此处返回了已识别的完整字符串。

首先，订阅该 `DictationResult` 事件：

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

然后处理 DictationResult 回调：

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

当用户正在对话时，将连续触发此事件。 当识别器倾听时，它提供了到目前为止所听说内容的文本。

首先，订阅该 `DictationHypothesis` 事件：

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

然后处理 DictationHypothesis 回调：

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

当识别器停止时，无论是从停止 ( # A1，还是发生超时或其他错误，都将激发此事件。

首先，订阅该 `DictationComplete` 事件：

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

然后处理 DictationComplete 回调：

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

当发生错误时，将激发此事件。

首先，订阅该 `DictationError` 事件：

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

然后处理 DictationError 回调：

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

一旦你订阅并处理了所关注的听写事件，开始听写识别器即可开始接收事件。

```
dictationRecognizer.Start();
```

如果不再想要保留 DictationRecognizer，则需要取消订阅事件并释放 DictationRecognizer。

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**提示**
* `Start()` 和 `Stop()` 方法分别启用和禁用听写识别。
* 完成识别器后，必须使用将其释放， `Dispose()` 以释放它所使用的资源。 如果未在此之前释放这些资源，它将在垃圾回收期间自动释放这些资源。
* 超时发生在设定的时间段之后。 您可以在事件中检查这些超时 `DictationComplete` 。 需要注意两个超时：
   1. 如果识别器在前五秒内开始播放并且不听到任何音频，则会超时。
   2. 如果识别器给出了结果，但随后听到了20秒，则会超时。

## <a name="using-both-phrase-recognition-and-dictation"></a>使用短语识别和听写

如果你想要在应用中同时使用短语识别和听写，则需要完全关闭一项，然后才能启动另一个。 如果有多个 KeywordRecognizers 正在运行，则可以使用以下操作一次性关闭它们：

```
PhraseRecognitionSystem.Shutdown();
```

在 `Restart()` DictationRecognizer 停止后，可以调用将所有识别器还原到其以前的状态：

```
PhraseRecognitionSystem.Restart();
```

还可以只启动 KeywordRecognizer，这也会重新启动 PhraseRecognitionSystem。

## <a name="voice-input-in-mixed-reality-toolkit"></a>混合现实工具包中的语音输入

在以下演示场景中，可以找到语音输入的 MRTK 示例：
* [听写](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [语音](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所说的 Unity 开发检查点旅程，则下一项任务是探索混合现实平台功能和 Api：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。