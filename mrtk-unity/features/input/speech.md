---
title: 语音
description: 在 MRTK 中配置语音输入
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 语音，
ms.openlocfilehash: 00de7854bcb68703fbfd5566b7d502f08ac34efc1ac9434a2c86274f07b6342d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228400"
---
# <a name="speech"></a>语音

![追踪菜单](../images/input/MRTK_Input_Speech.png)

语音输入提供程序（Windows *输入*）不会创建任何控制器，而是允许你定义关键字，这些关键字在识别时将引发语音输入事件。 输入 **系统配置文件** 中的语音命令 *配置文件* 用于配置要识别的关键字。 对于每个命令，还可以：

- 选择要 **映射到的** 输入操作。 例如，可以通过将两者映射到同一操作，使用关键字 *Select* 获得与鼠标左键单击相同的效果。
- 指定 **一个键** 代码，该代码将在按下时生成相同的语音事件。
- 添加 **将在** UWP 应用中使用的本地化密钥，以从应用资源获取本地化关键字。

<img src="../images/input/SpeechCommandsProfile.png" width="450px" alt="Speech Commands profile">

## <a name="handling-speech-input"></a>处理语音输入

该 [**`Speech Input Handler`**](xref:Microsoft.MixedReality.Toolkit.Input.SpeechInputHandler) 脚本可以添加到 GameObject，以使用 [**UnityEvents 处理语音命令**](https://docs.unity3d.com/Manual/UnityEvents.html)。 它会自动显示语音命令配置文件 中定义的 **关键字列表**。

<img src="../images/input/SpeechCommands_SpeechInputHandler1.png" width="450px" alt="Speech Input handler">

分配可选的 **SpeechConfirmationTooltip.prefab，** 以在识别时显示动画确认工具提示标签。

<img src="../images/input/SpeechCommands_SpeechInputHandler2.png" alt="Sppech input handler 2">

或者，开发人员可以在自定义脚本组件中实现 接口 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) [来处理语音输入事件](input-events.md#input-event-interface-example)。

## <a name="example-scene"></a>示例场景

中的 **SpeechInputExample** `MRTK/Examples/Demos/Input/Scenes/Speech` 场景演示如何使用语音。 还可以直接在你自己的脚本中侦听语音命令事件， ([`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 事件[处理程序表) 。](input-events.md)

<img src="../images/input/SpeechExampleScene.png" width="750px" alt="Speech Example scene">
