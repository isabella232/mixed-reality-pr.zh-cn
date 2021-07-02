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
# <a name="dictation"></a>听写

听写允许用户录制音频剪辑并获取听录。 若要使用它，请确保在输入系统配置文件 中注册 *听写系统*。 **Windows听写输入提供程序** 是开箱即用提供的听写系统，但可以通过实现 创建替代听写系统 [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) 。

## <a name="requirements"></a>要求

听写系统使用 Unity 的[听写Recognizer，](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html)它本身使用基础Windows API 来处理听写。 请注意，这意味着此功能仅在基于 Windows平台上提供。

使用听写系统需要 [PlayerSettings - Capabilities](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities)节中的"Internet 客户端"和"麦克风"应用程序功能。
有关[Unity 中语音输入的](/windows/mixed-reality/voice-input-in-unity#dictation)更多详细信息，请参阅 Windows Mixed Reality 文档。

## <a name="configuration"></a>配置

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

设置听写服务后，可以使用脚本启动和停止录制会话，然后通过 [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) UnityEvents 获取听录结果。

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- **听写假设是** 随着用户使用到目前为止捕获的音频的早期粗略听录而提出的。
- **听写结果** 在每个句子末尾引发 (即用户暂停) 到目前为止捕获的音频的最终听录时。
- **听写完成** 在录制会话结束时引发，并包含音频的完整最终听录。
- **引发听** 写错误以通知听写服务中的错误。 本例中的听录包含错误说明。

## <a name="example-scene"></a>示例场景

**中的听** 写 `MRTK/Examples/Demos/Input/Scenes/Dictation` 场景显示 `DictationHandler` 使用的脚本。 如果需要更多控制，可以扩展此脚本或创建自己的实现来 [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) 直接接收听写事件。

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
