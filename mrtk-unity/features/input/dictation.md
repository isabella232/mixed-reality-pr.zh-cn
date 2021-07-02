---
title: 听写
description: 有关如何在 MRTK 中录制音频剪辑和获取听录的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 520a667cc4b41f5e8f4373a7c901eb2458cd2d17
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176472"
---
# <a name="dictation"></a><span data-ttu-id="46d8f-104">听写</span><span class="sxs-lookup"><span data-stu-id="46d8f-104">Dictation</span></span>

<span data-ttu-id="46d8f-105">听写允许用户录制音频剪辑并获取听录。</span><span class="sxs-lookup"><span data-stu-id="46d8f-105">Dictation allows users to record audio clips and obtain a transcription.</span></span> <span data-ttu-id="46d8f-106">若要使用它，请确保在输入系统配置文件 中注册 *听写系统*。</span><span class="sxs-lookup"><span data-stu-id="46d8f-106">To use it make sure that a dictation system is registered in the *Input System Profile*.</span></span> <span data-ttu-id="46d8f-107">**Windows听写输入提供程序** 是开箱即用提供的听写系统，但可以通过实现 创建替代听写系统 [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) 。</span><span class="sxs-lookup"><span data-stu-id="46d8f-107">**Windows Dictation Input Provider** is the dictation system provided out of the box but alternative dictation systems can be created implementing [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem).</span></span>

## <a name="requirements"></a><span data-ttu-id="46d8f-108">要求</span><span class="sxs-lookup"><span data-stu-id="46d8f-108">Requirements</span></span>

<span data-ttu-id="46d8f-109">听写系统使用 Unity 的[听写Recognizer，](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html)它本身使用基础Windows API 来处理听写。</span><span class="sxs-lookup"><span data-stu-id="46d8f-109">The dictation system uses Unity's [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) which itself uses the underlying Windows speech APIs for handling dictation.</span></span> <span data-ttu-id="46d8f-110">请注意，这意味着此功能仅在基于 Windows平台上提供。</span><span class="sxs-lookup"><span data-stu-id="46d8f-110">Note that this implies that this feature is only present on Windows-based platforms.</span></span>

<span data-ttu-id="46d8f-111">使用听写系统需要 [PlayerSettings - Capabilities](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities)节中的"Internet 客户端"和"麦克风"应用程序功能。</span><span class="sxs-lookup"><span data-stu-id="46d8f-111">Usage of the Dictation system requires both the "Internet Client" and "Microphone" application capabilities in the [PlayerSettings - Capabilities section](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).</span></span>
<span data-ttu-id="46d8f-112">有关[Unity 中语音输入的](/windows/mixed-reality/voice-input-in-unity#dictation)更多详细信息，请参阅 Windows Mixed Reality 文档。</span><span class="sxs-lookup"><span data-stu-id="46d8f-112">See [Windows Mixed Reality Documentation](/windows/mixed-reality/voice-input-in-unity#dictation) for more details on voice input in Unity.</span></span>

## <a name="configuration"></a><span data-ttu-id="46d8f-113">配置</span><span class="sxs-lookup"><span data-stu-id="46d8f-113">Configuration</span></span>

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

<span data-ttu-id="46d8f-114">设置听写服务后，可以使用脚本启动和停止录制会话，然后通过 [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) UnityEvents 获取听录结果。</span><span class="sxs-lookup"><span data-stu-id="46d8f-114">Once you have a dictation service set up, you can use the [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) script to start and stop recording sessions and obtain the transcription results via UnityEvents.</span></span>

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- <span data-ttu-id="46d8f-115">**听写假设是** 随着用户使用到目前为止捕获的音频的早期粗略听录而提出的。</span><span class="sxs-lookup"><span data-stu-id="46d8f-115">**Dictation Hypothesis** is raised as the user speaks with early, rough transcriptions of the audio captured so far.</span></span>
- <span data-ttu-id="46d8f-116">**听写结果** 在每个句子末尾引发 (即用户暂停) 到目前为止捕获的音频的最终听录时。</span><span class="sxs-lookup"><span data-stu-id="46d8f-116">**Dictation Result** is raised at the end of each sentence (i.e. when the user pauses) with the final transcription of the audio captured so far.</span></span>
- <span data-ttu-id="46d8f-117">**听写完成** 在录制会话结束时引发，并包含音频的完整最终听录。</span><span class="sxs-lookup"><span data-stu-id="46d8f-117">**Dictation Complete** is raised at the end of the recording session with the full, final transcription of the audio.</span></span>
- <span data-ttu-id="46d8f-118">**引发听** 写错误以通知听写服务中的错误。</span><span class="sxs-lookup"><span data-stu-id="46d8f-118">**Dictation Error** is raised to inform of errors in the dictation service.</span></span> <span data-ttu-id="46d8f-119">本例中的听录包含错误说明。</span><span class="sxs-lookup"><span data-stu-id="46d8f-119">The transcription in this case contains a description of the error.</span></span>

## <a name="example-scene"></a><span data-ttu-id="46d8f-120">示例场景</span><span class="sxs-lookup"><span data-stu-id="46d8f-120">Example scene</span></span>

<span data-ttu-id="46d8f-121">**中的听** 写 `MRTK/Examples/Demos/Input/Scenes/Dictation` 场景显示 `DictationHandler` 使用的脚本。</span><span class="sxs-lookup"><span data-stu-id="46d8f-121">**Dictation** scene in `MRTK/Examples/Demos/Input/Scenes/Dictation` shows the `DictationHandler` script in use.</span></span> <span data-ttu-id="46d8f-122">如果需要更多控制，可以扩展此脚本或创建自己的实现来 [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) 直接接收听写事件。</span><span class="sxs-lookup"><span data-stu-id="46d8f-122">If you need more control, you can either extend this script or create your own implementing [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) to receive dictation events directly.</span></span>

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
