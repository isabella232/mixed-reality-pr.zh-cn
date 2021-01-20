---
title: DirectX 中的语音输入
description: 介绍如何在适用于 Windows Mixed Reality 的 DirectX 应用程序中实现语音命令和短语识别。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: 演练，语音命令，短语，识别，语音，directx，平台，cortana，windows mixed reality
ms.openlocfilehash: 5f7ed587b474d147c0b13e4896a89f655f8dc30b
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583744"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="62722-104">DirectX 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="62722-104">Voice input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="62722-105">本文与旧版 WinRT 本机 Api 相关。</span><span class="sxs-lookup"><span data-stu-id="62722-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="62722-106">对于新的本机应用项目，建议使用 **[OPENXR API](openxr-getting-started.md)**。</span><span class="sxs-lookup"><span data-stu-id="62722-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="62722-107">本文介绍如何在适用于 Windows Mixed Reality 的 DirectX 应用程序中实现 [语音命令](../../design/voice-input.md) 和短语识别。</span><span class="sxs-lookup"><span data-stu-id="62722-107">This article explains how to implement [voice commands](../../design/voice-input.md) plus small-phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="62722-108">本文中的代码片段使用 c + +/CX，而不是 C + + 17 兼容 c + +/WinRT，它用于 [c + + 全息项目模板](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="62722-108">The code snippets in this article use C++/CX rather than C++17-compliant C++/WinRT, which is used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="62722-109">概念与 c + +/WinRT 项目等效，但你需要转换代码。</span><span class="sxs-lookup"><span data-stu-id="62722-109">The concepts are equivalent for a C++/WinRT project, but you need to translate the code.</span></span>

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a><span data-ttu-id="62722-110">使用 SpeechRecognizer 进行连续语音识别</span><span class="sxs-lookup"><span data-stu-id="62722-110">Use SpeechRecognizer for continuous speech recognition</span></span>

<span data-ttu-id="62722-111">本部分介绍如何使用连续语音识别在应用中启用语音命令。</span><span class="sxs-lookup"><span data-stu-id="62722-111">This section describes how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="62722-112">本演练使用 [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) 示例中的代码。</span><span class="sxs-lookup"><span data-stu-id="62722-112">This walk-through uses code from the [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) sample.</span></span> <span data-ttu-id="62722-113">当示例运行时，请用一个已注册颜色命令的名称来更改旋转立方体的颜色。</span><span class="sxs-lookup"><span data-stu-id="62722-113">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="62722-114">首先，创建一个新的 *Windows：： Media：： SpeechRecognition：： SpeechRecognizer* 实例。</span><span class="sxs-lookup"><span data-stu-id="62722-114">First, create a new *Windows::Media::SpeechRecognition::SpeechRecognizer* instance.</span></span>

<span data-ttu-id="62722-115">From *HolographicVoiceInputSampleMain：： CreateSpeechConstraintsForCurrentState*：</span><span class="sxs-lookup"><span data-stu-id="62722-115">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="62722-116">创建要侦听的识别器的语音命令的列表。</span><span class="sxs-lookup"><span data-stu-id="62722-116">Create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="62722-117">在这里，我们将构造一组命令来更改全息图的颜色。</span><span class="sxs-lookup"><span data-stu-id="62722-117">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="62722-118">为方便起见，我们还创建了以后用于命令的数据。</span><span class="sxs-lookup"><span data-stu-id="62722-118">For convenience, we also create the data that we'll use for the commands later.</span></span>

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

<span data-ttu-id="62722-119">你可以使用不在字典中的拼音词来指定命令。</span><span class="sxs-lookup"><span data-stu-id="62722-119">You can use phonetic words that might not be in a dictionary to specify commands.</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="62722-120">若要将命令列表加载到语音识别器的约束列表中，请使用 [SpeechRecognitionListConstraint](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionListConstraint) 对象。</span><span class="sxs-lookup"><span data-stu-id="62722-120">To load the commands list into the list of constraints for the speech recognizer, use a [SpeechRecognitionListConstraint](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionListConstraint) object.</span></span>

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

<span data-ttu-id="62722-121">订阅语音识别器的[SpeechContinuousRecognitionSession](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession)上的[ResultGenerated](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession)事件。</span><span class="sxs-lookup"><span data-stu-id="62722-121">Subscribe to the [ResultGenerated](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession) event on the speech recognizer's [SpeechContinuousRecognitionSession](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession).</span></span> <span data-ttu-id="62722-122">此事件将在你已识别到你的某个命令时通知你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="62722-122">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="62722-123">*OnResultGenerated* 事件处理程序接收 [SpeechContinuousRecognitionResultGeneratedEventArgs](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionResultGeneratedEventArgs)实例中的事件数据。</span><span class="sxs-lookup"><span data-stu-id="62722-123">Your *OnResultGenerated* event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionResultGeneratedEventArgs) instance.</span></span> <span data-ttu-id="62722-124">如果置信度大于你定义的阈值，应用应注意到事件发生。</span><span class="sxs-lookup"><span data-stu-id="62722-124">If the confidence is greater than the threshold you defined, your app should note that the event happened.</span></span> <span data-ttu-id="62722-125">保存事件数据，以便您可以在以后的更新循环中使用它。</span><span class="sxs-lookup"><span data-stu-id="62722-125">Save the event data so that you can use it in a later update loop.</span></span>

<span data-ttu-id="62722-126">从 *HolographicVoiceInputSampleMain*：</span><span class="sxs-lookup"><span data-stu-id="62722-126">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="62722-127">在我们的示例代码中，我们将根据用户的命令更改旋转全息图多维数据集的颜色。</span><span class="sxs-lookup"><span data-stu-id="62722-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="62722-128">From *HolographicVoiceInputSampleMain：： Update*：</span><span class="sxs-lookup"><span data-stu-id="62722-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-one-shot-recognition"></a><span data-ttu-id="62722-129">使用 "一次拍摄" 识别</span><span class="sxs-lookup"><span data-stu-id="62722-129">Use "one-shot" recognition</span></span>

<span data-ttu-id="62722-130">你可以配置语音识别器来侦听用户讲述的短语或句子。</span><span class="sxs-lookup"><span data-stu-id="62722-130">You can configure a speech recognizer to listen for phrases or sentences that the user speaks.</span></span> <span data-ttu-id="62722-131">在这种情况下，我们将应用 *SpeechRecognitionTopicConstraint* ，告知语音识别器所需的输入类型。</span><span class="sxs-lookup"><span data-stu-id="62722-131">In this case, we apply a *SpeechRecognitionTopicConstraint* that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="62722-132">下面是此方案的应用工作流：</span><span class="sxs-lookup"><span data-stu-id="62722-132">Here's an app workflow for this scenario:</span></span>
1. <span data-ttu-id="62722-133">你的应用程序将创建 SpeechRecognizer，提供 UI 提示，并开始侦听讲述命令。</span><span class="sxs-lookup"><span data-stu-id="62722-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a spoken command.</span></span>
2. <span data-ttu-id="62722-134">用户讲述一个短语或句子。</span><span class="sxs-lookup"><span data-stu-id="62722-134">The user speaks a phrase or sentence.</span></span>
3. <span data-ttu-id="62722-135">用户的语音识别发生，并将结果返回到应用。</span><span class="sxs-lookup"><span data-stu-id="62722-135">Recognition of the user's speech occurs, and a result is returned to the app.</span></span> <span data-ttu-id="62722-136">此时，你的应用程序应提供 UI 提示以指示已发生识别。</span><span class="sxs-lookup"><span data-stu-id="62722-136">At this point, your app should provide a UI prompt to indicate that recognition has occurred.</span></span>
4. <span data-ttu-id="62722-137">根据你想要响应的置信度和语音识别结果的置信度，你的应用程序可以处理结果并相应地做出响应。</span><span class="sxs-lookup"><span data-stu-id="62722-137">Depending on the confidence level that you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="62722-138">本部分介绍如何创建 SpeechRecognizer、编译约束和侦听语音输入。</span><span class="sxs-lookup"><span data-stu-id="62722-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="62722-139">下面的代码编译主题约束，这种情况下，它针对 web 搜索进行了优化。</span><span class="sxs-lookup"><span data-stu-id="62722-139">The following code compiles the topic constraint, which in this case is optimized for web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="62722-140">如果编译成功，则可以继续语音识别。</span><span class="sxs-lookup"><span data-stu-id="62722-140">If compilation succeeds, we can continue with speech recognition.</span></span>

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

<span data-ttu-id="62722-141">然后，将结果返回到应用程序。</span><span class="sxs-lookup"><span data-stu-id="62722-141">The result is then returned to the app.</span></span> <span data-ttu-id="62722-142">如果我们完全相信，我们可以处理该命令。</span><span class="sxs-lookup"><span data-stu-id="62722-142">If we're confident enough in the result, we can process the command.</span></span> <span data-ttu-id="62722-143">此代码示例处理至少具有中等置信度的结果。</span><span class="sxs-lookup"><span data-stu-id="62722-143">This code example processes results with at least medium confidence.</span></span>

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

<span data-ttu-id="62722-144">使用语音识别时，请注意可能表明用户已在系统隐私设置中关闭麦克风的例外情况。</span><span class="sxs-lookup"><span data-stu-id="62722-144">Whenever you use speech recognition, watch for exceptions that could indicate that the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="62722-145">这可能发生在初始化或识别期间。</span><span class="sxs-lookup"><span data-stu-id="62722-145">This can happen during initialization or recognition.</span></span>

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
> <span data-ttu-id="62722-146">可使用多个预定义的 [SpeechRecognitionScenarios](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionScenario) 来优化语音识别。</span><span class="sxs-lookup"><span data-stu-id="62722-146">There are several predefined [SpeechRecognitionScenarios](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionScenario) that you can use to optimize speech recognition.</span></span>

* <span data-ttu-id="62722-147">若要优化听写，请使用听写方案。</span><span class="sxs-lookup"><span data-stu-id="62722-147">To optimize for dictation, use the dictation scenario.</span></span><br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* <span data-ttu-id="62722-148">对于语音 web 搜索，请使用以下特定于 web 的方案约束。</span><span class="sxs-lookup"><span data-stu-id="62722-148">For speech web searches, use the following web-specific scenario constraint.</span></span>

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* <span data-ttu-id="62722-149">使用窗体约束填写表单。</span><span class="sxs-lookup"><span data-stu-id="62722-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="62722-150">在这种情况下，最好应用自己的语法，用于填写表单。</span><span class="sxs-lookup"><span data-stu-id="62722-150">In this case, it's best to apply your own grammar that's optimized for filling out the form.</span></span>

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* <span data-ttu-id="62722-151">您可以以 SRGS 格式提供自己的语法。</span><span class="sxs-lookup"><span data-stu-id="62722-151">You can provide your own grammar in the SRGS format.</span></span>

## <a name="use-continuous-recognition"></a><span data-ttu-id="62722-152">使用连续识别</span><span class="sxs-lookup"><span data-stu-id="62722-152">Use continuous recognition</span></span>

<span data-ttu-id="62722-153">有关连续听写方案，请参阅 [Windows 10 UWP 语音代码示例](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)。</span><span class="sxs-lookup"><span data-stu-id="62722-153">For the continuous-dictation scenario, see the [Windows 10 UWP speech code sample](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span></span>

## <a name="handle-quality-degradation"></a><span data-ttu-id="62722-154">处理质量降级</span><span class="sxs-lookup"><span data-stu-id="62722-154">Handle quality degradation</span></span>

<span data-ttu-id="62722-155">环境条件有时会干扰语音识别。</span><span class="sxs-lookup"><span data-stu-id="62722-155">Environmental conditions sometimes interfere with speech recognition.</span></span> <span data-ttu-id="62722-156">例如，房间可能太干扰，或者用户可能会说声音太大。</span><span class="sxs-lookup"><span data-stu-id="62722-156">For example, the room might be too noisy, or the user might speak too loudly.</span></span> <span data-ttu-id="62722-157">只要有可能，语音识别 API 就会提供导致质量降低的条件的相关信息。</span><span class="sxs-lookup"><span data-stu-id="62722-157">Whenever possible, the speech recognition API provides information about the conditions that caused the quality degradation.</span></span> <span data-ttu-id="62722-158">此信息通过 WinRT 事件推送到应用。</span><span class="sxs-lookup"><span data-stu-id="62722-158">This information is pushed to your app through a WinRT event.</span></span> <span data-ttu-id="62722-159">下面的示例演示如何订阅此事件。</span><span class="sxs-lookup"><span data-stu-id="62722-159">The following example shows  how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="62722-160">在我们的代码示例中，我们将条件信息写入调试控制台。</span><span class="sxs-lookup"><span data-stu-id="62722-160">In our code sample, we write the conditions information to the debug console.</span></span> <span data-ttu-id="62722-161">应用可能需要通过 UI、语音合成和另一种方法向用户提供反馈。</span><span class="sxs-lookup"><span data-stu-id="62722-161">An app might want to provide feedback to the user through the UI, speech synthesis, and another method.</span></span> <span data-ttu-id="62722-162">或者，当语音被暂时降低质量的中断时，可能需要以不同的方式运行。</span><span class="sxs-lookup"><span data-stu-id="62722-162">Or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="62722-163">如果未使用 ref 类创建 DirectX 应用，则必须先取消订阅该事件，然后才能释放或重新创建语音识别器。</span><span class="sxs-lookup"><span data-stu-id="62722-163">If you're not using ref classes to create your DirectX app, you must unsubscribe from the event before you release or recreate your speech recognizer.</span></span> <span data-ttu-id="62722-164">HolographicSpeechPromptSample 有一个例程，用于停止识别和取消订阅事件。</span><span class="sxs-lookup"><span data-stu-id="62722-164">The HolographicSpeechPromptSample has a routine to stop recognition and unsubscribe from events.</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a><span data-ttu-id="62722-165">使用语音合成提供可听见的提示</span><span class="sxs-lookup"><span data-stu-id="62722-165">Use speech synthesis to provide audible prompts</span></span>

<span data-ttu-id="62722-166">全息语音示例使用语音合成向用户提供可听见的指令。</span><span class="sxs-lookup"><span data-stu-id="62722-166">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="62722-167">本部分介绍如何创建合成语音样本，并通过 HRTF 音频 Api 将其播放回来。</span><span class="sxs-lookup"><span data-stu-id="62722-167">This section shows how to create a synthesized voice sample  and then play it back through the HRTF audio APIs.</span></span>

<span data-ttu-id="62722-168">建议在请求短语输入时提供自己的语音提示。</span><span class="sxs-lookup"><span data-stu-id="62722-168">We recommend providing your own speech prompts when you request phrase input.</span></span> <span data-ttu-id="62722-169">提示还可以帮助指示何时可以为连续识别方案口述语音命令。</span><span class="sxs-lookup"><span data-stu-id="62722-169">Prompts can also help indicate when speech commands can be spoken for a continuous-recognition scenario.</span></span> <span data-ttu-id="62722-170">下面的示例演示如何使用语音合成器执行此操作。</span><span class="sxs-lookup"><span data-stu-id="62722-170">The following example demonstrates how to use a speech synthesizer to do this.</span></span> <span data-ttu-id="62722-171">你还可以使用预先录制的语音剪辑、视觉对象 UI 或另一个指示符，例如在提示不是动态的情况下。</span><span class="sxs-lookup"><span data-stu-id="62722-171">You could also use a pre-recorded voice clip, a visual UI, or another indicator of what to say, for example in scenarios where the prompt isn't dynamic.</span></span>

<span data-ttu-id="62722-172">首先，创建 SpeechSynthesizer 对象。</span><span class="sxs-lookup"><span data-stu-id="62722-172">First, create the SpeechSynthesizer object.</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="62722-173">还需要包含要合成的文本的字符串。</span><span class="sxs-lookup"><span data-stu-id="62722-173">You also need a string that includes the text to  synthesize.</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="62722-174">通过 SynthesizeTextToStreamAsync 以异步方式合成语音。</span><span class="sxs-lookup"><span data-stu-id="62722-174">Speech is synthesized asynchronously through SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="62722-175">在这里，我们启动了一个异步任务来合成语音。</span><span class="sxs-lookup"><span data-stu-id="62722-175">Here, we start an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="62722-176">语音合成作为字节流发送。</span><span class="sxs-lookup"><span data-stu-id="62722-176">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="62722-177">我们可以使用该字节流来初始化 XAudio2 的声音。</span><span class="sxs-lookup"><span data-stu-id="62722-177">We can use that byte stream to initialize an XAudio2 voice.</span></span> <span data-ttu-id="62722-178">对于我们的全息代码示例，我们将它作为 HRTF 音频效果播放。</span><span class="sxs-lookup"><span data-stu-id="62722-178">For our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="62722-179">与语音识别一样，如果出现问题，语音合成就会引发异常。</span><span class="sxs-lookup"><span data-stu-id="62722-179">As with speech recognition, speech synthesis throws an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="62722-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62722-180">See also</span></span>
* [<span data-ttu-id="62722-181">语音应用设计</span><span class="sxs-lookup"><span data-stu-id="62722-181">Speech app design</span></span>](/windows/uwp/design/input/speech-interactions)
* [<span data-ttu-id="62722-182">SpeechRecognitionAndSynthesis 示例</span><span class="sxs-lookup"><span data-stu-id="62722-182">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)