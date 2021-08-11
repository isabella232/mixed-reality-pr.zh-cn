---
title: 混合现实键盘
description: 如何使用混合现实键盘的说明
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 068d88483eff8db5466c6b5ff0d2ca8bbc0b5dddee549bb3d87c82fa740bc8fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197007"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a>混合现实和 HoloLens 键盘帮助程序类

MRTK 提供了多个试验性帮助程序组件，以帮助从 [系统键盘](../ux-building-blocks/system-keyboard.md)启动和读取文本。

请注意，系统键盘的行为取决于目标平台的功能，例如 HoloLens 2 上的键盘支持直接交互，而 HoloLens (第一代) 将支持 GGV<sup>[1](/windows/mixed-reality/gaze)</sup>。 此外，在从编辑器执行[Unity 远程处理](../tools/holographic-remoting.md)到 HoloLens 时，系统键盘不会显示。

## <a name="mixedrealitykeyboard"></a>MixedRealityKeyboard

[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) 是一个组件，它提供用于启动和关闭系统键盘以及与键盘输入的文本交互的方法。  

### <a name="how-to-use"></a>使用方法

1. 将 [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) 组件附加到任何对象。
2. 调用 `ShowKeyboard(string text = "", bool multiLine = false)` `HideKeyboard()` 以显示和隐藏键盘，并处理 `OnShowKeyboard` 、 `OnHideKeyboard` 和 `OnCommitText` 事件以处理在显示、隐藏键盘以及按下 enter 键时要处理的事件。

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a>输入字段 TMP_KeyboardInputField 和 UI_KeyboardInputField

[`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField)和 [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 类是可以添加到文本输入字段的组件，可在单击时自动调用系统键盘，并在用户输入文本时更新文本输入字段内容。

### <a name="how-to-use"></a>如何使用

1. 为 UnityUI 或 TextMeshPro 创建输入字段。
2. 将相应的 [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) 或 [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 组件添加到输入字段游戏对象。

UnityUI 输入字段和 TextMeshPro (TMPro) 输入字段的 prototyping 在 "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs" 中提供

如何使用 TMP_KeyboardInputField 和 UI_KeyboardInputField 的示例位于 "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"