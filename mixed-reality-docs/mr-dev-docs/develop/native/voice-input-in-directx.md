---
title: DirectX 中的语音输入
description: 说明如何在 DirectX 应用中实现语音命令和小短语和句子识别，Windows Mixed Reality。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: 演练， 语音命令， 短语， 识别， 语音， directx， 平台， cortana， windows 混合现实
ms.openlocfilehash: e30d5c2101bed4b613111b6131a3e94d654c3ff5b1e913f4d8e275ffc1a2776a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221837"
---
# <a name="voice-input-in-directx"></a>DirectX 中的语音输入

> [!NOTE]
> 本文与旧版 WinRT 本机 API 相关。  对于新的本机应用项目，建议使用 **[OpenXR API](openxr-getting-started.md)**。

本文介绍如何在 DirectX 应用中实现[语音命令](../../design/voice-input.md)以及小短语和句子识别，Windows Mixed Reality。

>[!NOTE]
>本文中的代码片段使用 C++/CX，而不是 C++17 兼容的 C++/WinRT，C++ 全息项目模板 [中使用的代码片段](creating-a-holographic-directx-project.md)。  这些概念等效于 C++/WinRT 项目，但你需要转换代码。

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a>使用 SpeechRecognizer 进行连续语音识别

本部分介绍如何使用连续语音识别在应用中启用语音命令。 本演练使用 [HolographicVoiceInput 示例中的代码](https://go.microsoft.com/fwlink/p/?LinkId=844964) 。 运行示例时，请说出其中一个已注册颜色命令的名称，以更改旋转立方体的颜色。

首先，创建一个新的 *Windows：：Media：：SpeechRecognition：：SpeechRecognizer* 实例。

从 *HolographicVoiceInputSampleMain：：CreateSpeechConstraintsForCurrentState*：

```
m_speechRecognizer = ref new SpeechRecognizer();
```

为识别器创建要侦听的语音命令列表。 在这里，我们将构造一组命令来更改全息影像的颜色。 为方便起见，我们还创建稍后用于命令的数据。

```
m_speechCommandList = ref new Platform::Collections::Vector<String^>();
   m_speechCommandData.clear();
   m_speechCommandList->Append(StringReference(L"white"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"grey"));
   m_speechCommandData.push_back(float4(0.5f, 0.5f, 0.5f, 1.f));
   m_speechCommandList->Append(StringReference(L"green"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"black"));
   m_speechCommandData.push_back(float4(0.1f, 0.1f, 0.1f, 1.f));
   m_speechCommandList->Append(StringReference(L"red"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"yellow"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"aquamarine"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"blue"));
   m_speechCommandData.push_back(float4(0.f, 0.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"purple"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 1.f, 1.f));
```

可以使用字典中可能未包含的语音词来指定命令。

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

若要将命令列表加载到语音识别器的约束列表中，请使用 [SpeechRecognitionListConstraint](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionListConstraint) 对象。

```
SpeechRecognitionListConstraint^ spConstraint = ref new SpeechRecognitionListConstraint(m_speechCommandList);
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(spConstraint);
   create_task(m_speechRecognizer->CompileConstraintsAsync()).then([this](SpeechRecognitionCompilationResult^ compilationResult)
   {
       if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
       {
           m_speechRecognizer->ContinuousRecognitionSession->StartAsync();
       }
       else
       {
           // Handle errors here.
       }
   });
```

订阅语音识别器[SpeechContinuousRecognitionSession](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession)上的[ResultGenerated](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession)事件。 当识别了其中一个命令时，此事件会通知应用。

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

*OnResultGenerated* 事件处理程序在 [SpeechContinuousRecognitionResultGeneratedEventArgs](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionResultGeneratedEventArgs)实例中接收事件数据。 如果置信度大于定义的阈值，应用应会注意到事件发生。 保存事件数据，以便可以在以后的更新循环中使用它。

从 *HolographicVoiceInputSampleMain.cpp*：

```
// Change the cube color, if we get a valid result.
   void HolographicVoiceInputSampleMain::OnResultGenerated(SpeechContinuousRecognitionSession ^sender, SpeechContinuousRecognitionResultGeneratedEventArgs ^args)
   {
       if (args->Result->RawConfidence > 0.5f)
       {
           m_lastCommand = args->Result->Text;
       }
   }
```

在示例代码中，我们根据用户的 命令更改旋转全息影像立方体的颜色。

从 *HolographicVoiceInputSampleMain：：Update*：

```
// Check for new speech input since the last frame.
   if (m_lastCommand != nullptr)
   {
       auto command = m_lastCommand;
       m_lastCommand = nullptr;

       int i = 0;
       for each (auto& iter in m_speechCommandList)
       {
           if (iter == command)
           {
               m_spinningCubeRenderer->SetColor(m_speechCommandData[i]);
               break;
           }

           ++i;
       }
   }
```

## <a name="use-one-shot-recognition"></a>使用"一次"识别

可以将语音识别器配置为侦听用户说话的短语或句子。 在这种情况下，我们将应用 *SpeechRecognitionTopicConstraint，* 告知语音识别器预期输入类型。 下面是此方案的应用工作流：
1. 应用创建 SpeechRecognizer，提供 UI 提示，并开始侦听语音命令。
2. 用户说短语或句子。
3. 识别用户的语音，结果将返回到应用。 此时，应用应提供 UI 提示以指示已发生识别。
4. 根据要响应的置信度以及语音识别结果的置信度，应用可以处理结果并根据需要做出响应。

本部分介绍如何创建 SpeechRecognizer、编译约束和侦听语音输入。

以下代码编译主题约束，该约束在此例中针对 Web 搜索进行了优化。

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

如果编译成功，我们可以继续进行语音识别。

```
try
       {
           SpeechRecognitionCompilationResult^ compilationResult = previousTask.get();

           // Check to make sure that the constraints were in a proper format and the recognizer was able to compile it.
           if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
           {
               // If the compilation succeeded, we can start listening for the user's spoken phrase or sentence.
               create_task(m_speechRecognizer->RecognizeAsync()).then([this](task<SpeechRecognitionResult^>& previousTask)
               {
```

然后，结果将返回到应用。 如果我们对结果有足够的信心，我们可以处理 命令。 此代码示例至少以中等置信度处理结果。

```
try
                   {
                       auto result = previousTask.get();

                       if (result->Status != SpeechRecognitionResultStatus::Success)
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech recognition was not successful: ") +
                               result->Status.ToString()->Data() +
                               L"\n"
                               );
                       }

                       // In this example, we look for at least medium confidence in the speech result.
                       if ((result->Confidence == SpeechRecognitionConfidence::High) ||
                           (result->Confidence == SpeechRecognitionConfidence::Medium))
                       {
                           // If the user said a color name anywhere in their phrase, it will be recognized in the
                           // Update loop; then, the cube will change color.
                           m_lastCommand = result->Text;

                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech phrase was: ") +
                               m_lastCommand->Data() +
                               L"\n"
                               );
                       }
                       else
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Recognition confidence not high enough: ") +
                               result->Confidence.ToString()->Data() +
                               L"\n"
                               );
                       }
                   }
```

每当使用语音识别时，请留意可能指示用户已关闭系统隐私设置中的麦克风的异常。 在初始化或识别期间可能会发生这种情况。

```
catch (Exception^ exception)
                   {
                       // Note that if you get an "Access is denied" exception, you might need to enable the microphone
                       // privacy setting on the device and/or add the microphone capability to your app manifest.

                       PrintWstringToDebugConsole(
                           std::wstring(L"Speech recognizer error: ") +
                           exception->ToString()->Data() +
                           L"\n"
                           );
                   }
               });

               return true;
           }
           else
           {
               OutputDebugStringW(L"Could not initialize predefined grammar speech engine!\n");

               // Handle errors here.
               return false;
           }
       }
       catch (Exception^ exception)
       {
           // Note that if you get an "Access is denied" exception, you might need to enable the microphone
           // privacy setting on the device and/or add the microphone capability to your app manifest.

           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to initialize predefined grammar speech engine:") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
           return false;
       }
   });
```

> [!NOTE]
> 有几个预定义的 [SpeechRecognitionScenario 可用于](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionScenario) 优化语音识别。

* 若要优化听写，请使用听写方案。<br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* 对于语音 Web 搜索，请使用以下特定于 Web 的方案约束。

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* 使用窗体约束填充窗体。 在这种情况下，最好应用自己的已针对填写表单进行优化的语法。

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* 可以使用 SRGS 格式提供自己的语法。

## <a name="use-continuous-recognition"></a>使用连续识别

有关连续听写方案，请参阅 Windows 10 [UWP 语音代码示例](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)。

## <a name="handle-quality-degradation"></a>处理质量下降

环境条件有时会干扰语音识别。 例如，房间可能太杂乱，或者用户说话声音过大。 语音识别 API 会尽可能提供有关导致质量下降的条件的信息。 此信息通过 WinRT 事件推送到应用。 以下示例演示如何订阅此事件。

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

在代码示例中，我们将条件信息写入调试控制台。 应用可能需要通过 UI、语音合成和其他方法为用户提供反馈。 或者，当语音因临时质量降低而中断时，它的行为可能有所不同。

```
void HolographicSpeechPromptSampleMain::OnSpeechQualityDegraded(SpeechRecognizer^ recognizer, SpeechRecognitionQualityDegradingEventArgs^ args)
   {
       switch (args->Problem)
       {
       case SpeechRecognitionAudioProblem::TooFast:
           OutputDebugStringW(L"The user spoke too quickly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooSlow:
           OutputDebugStringW(L"The user spoke too slowly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooQuiet:
           OutputDebugStringW(L"The user spoke too softly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooLoud:
           OutputDebugStringW(L"The user spoke too loudly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooNoisy:
           OutputDebugStringW(L"There is too much noise in the signal.\n");
           break;

       case SpeechRecognitionAudioProblem::NoSignal:
           OutputDebugStringW(L"There is no signal.\n");
           break;

       case SpeechRecognitionAudioProblem::None:
       default:
           OutputDebugStringW(L"An error was reported with no information.\n");
           break;
       }
   }
```

如果不使用 ref 类来创建 DirectX 应用，则必须在发布或重新创建语音识别器之前取消订阅事件。 HolographicSpeechPromptSample 有一个例程，用于停止识别和取消订阅事件。

```
Concurrency::task<void> HolographicSpeechPromptSampleMain::StopCurrentRecognizerIfExists()
   {
       return create_task([this]()
       {
           if (m_speechRecognizer != nullptr)
           {
               return create_task(m_speechRecognizer->StopRecognitionAsync()).then([this]()
               {
                   m_speechRecognizer->RecognitionQualityDegrading -= m_speechRecognitionQualityDegradedToken;

                   if (m_speechRecognizer->ContinuousRecognitionSession != nullptr)
                   {
                       m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated -= m_speechRecognizerResultEventToken;
                   }
               });
           }
           else
           {
               return create_task([this]() { m_speechRecognizer = nullptr; });
           }
       });
   }
```

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a>使用语音合成提供语音提示

全息语音示例使用语音合成为用户提供有声说明。 本部分演示如何创建合成语音示例，然后通过 HRTF 音频 API 播放它。

建议在请求短语输入时提供自己的语音提示。 提示还有助于指示何时可以针对连续识别方案说出语音命令。 下面的示例演示如何使用语音合成器来这样做。 还可以使用预录制的语音剪辑、可视化 UI 或其他要表达内容的指标，例如，在提示不动态的情况下。

首先，创建 SpeechSynthesizer 对象。

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

还需要包含要合成的文本的字符串。

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

语音通过 SynthesizeTextToStreamAsync 异步合成。 在这里，我们将启动一个异步任务来合成语音。

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

语音合成作为字节流发送。 我们可以使用该字节流来初始化 XAudio2 语音。 对于全息代码示例，我们将它播放为 HRTF 音频效果。

```
Windows::Media::SpeechSynthesis::SpeechSynthesisStream^ stream = synthesisStreamTask.get();

           auto hr = m_speechSynthesisSound.Initialize(stream, 0);
           if (SUCCEEDED(hr))
           {
               m_speechSynthesisSound.SetEnvironment(HrtfEnvironment::Small);
               m_speechSynthesisSound.Start();

               // Amount of time to pause after the audio prompt is complete, before listening
               // for speech input.
               static const float bufferTime = 0.15f;

               // Wait until the prompt is done before listening.
               m_secondsUntilSoundIsComplete = m_speechSynthesisSound.GetDuration() + bufferTime;
               m_waitingForSpeechPrompt = true;
           }
       }
```

与语音识别一样，如果出现问题，语音合成会引发异常。

```
catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to synthesize speech: ") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
       }
   });
```

## <a name="see-also"></a>另请参阅
* [语音应用设计](/windows/uwp/design/input/speech-interactions)
* [SpeechRecognitionAndSynthesis 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)