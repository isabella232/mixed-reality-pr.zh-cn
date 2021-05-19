---
title: 混合现实键盘
description: 有关如何使用混合现实键盘的说明
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 9fa81db9a71f1d0ce32bdd80a123eb072fc26fc5
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143396"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a>混合现实和 HoloLens 键盘帮助程序类

MRTK 提供了几个实验性帮助程序组件，以帮助从系统键盘 启动和 [读取文本](../ux-building-blocks/system-keyboard.md)。

请注意，系统键盘的行为取决于目标平台的功能，例如 HoloLens 2 上的键盘支持直接手部交互，而 HoloLens (第一代) 上的键盘支持 GGV<sup>[1。](/windows/mixed-reality/gaze)</sup> 此外，执行从编辑器到 HoloLens 的 [Unity 远程](../tools/holographic-remoting.md) 处理时，系统键盘不会显示。

## <a name="mixedrealitykeyboard"></a>MixedRealityKeyboard

[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) 是一个 组件，它提供启动和关闭系统键盘以及与键盘输入的文本进行交互的方法。  

### <a name="how-to-use"></a>使用方法

1. 将 [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) 组件附加到任何对象。
2. 调用 `Show()` `Hide()` 以显示和隐藏键盘，并处理在显示、隐藏键盘和按 Enter 键时要处理的 `OnShowKeyboard` `OnHideKeyboard` 和 `OnCommitText` 事件。

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a>输入字段TMP_KeyboardInputField和UI_KeyboardInputField

和 类是可添加到文本输入字段的组件，可在单击时自动调用系统键盘，在用户输入文本时 [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 更新文本输入字段内容。

### <a name="how-to-use"></a>如何使用

1. 为 UnityUI 或 TextMeshPro 创建输入字段。
2. 将相应的 [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) 或 [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 组件添加到输入字段游戏对象。

UnityUI 输入字段和 TextMeshPro (TMPro) 输入字段的预制项位于"Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"

在"Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"中TMP_KeyboardInputField UI_KeyboardInputField示例演示了如何使用 和