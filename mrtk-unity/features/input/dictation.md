---
title: 听写
description: Docummentation 如何录制音频剪辑和获取 MRTK 中的脚本
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 14061197031282dcc9dd20a141101b65ee92ca2376bdc009fa8790076681a970
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219992"
---
# <a name="dictation"></a>听写

听写允许用户录制音频剪辑和获取脚本。 若要使用它，请确保在 *输入系统配置文件* 中注册了口述系统。 **Windows 听写输入提供程序** 是现成提供的听写系统，但可以创建实现的替代听写系统 [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) 。

## <a name="requirements"></a>要求

听写系统使用 Unity 的[DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) ，它本身使用基础 Windows 语音 api 来处理听写。 请注意，这意味着此功能只存在于基于 Windows 的平台上。

使用听写系统时， [PlayerSettings 部分](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities)需要 "Internet 客户端" 和 "麦克风" 应用程序功能。
有关 Unity 中语音输入的更多详细信息，请参阅[Windows Mixed Reality 文档](/windows/mixed-reality/voice-input-in-unity#dictation)。

## <a name="configuration"></a>配置

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

设置听写服务后，可以使用该 [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) 脚本来启动和停止记录会话，并通过 UnityEvents 获取脚本结果。

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- **听写假设** 是在用户熟悉转录的最早捕获音频的情况下引发的。
- **听写结果** 在每个句子的末尾引发 (例如，当用户暂停) 时，最后就是在迄今为止捕获的音频。
- 在录音会话结束时，将会出现 **听写完成**，并提供完整的最终脚本。
- 听写服务中出现错误时，将引发 **听写错误**。 在此示例中，脚本包含错误说明。

## <a name="example-scene"></a>示例场景

中的 **听写** 场景 `MRTK/Examples/Demos/Input/Scenes/Dictation` 显示了 `DictationHandler` 正在使用的脚本。 如果需要更多控制，可以扩展此脚本或创建自己的实现 [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) 来直接接收听写事件。

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
