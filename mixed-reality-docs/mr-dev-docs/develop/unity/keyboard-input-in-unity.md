---
title: Unity 中的键盘输入
description: Unity 提供了 TouchScreenKeyboard 类，可用于在没有可用物理键盘时接受键盘输入。
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: 键盘，输入，unity，touchscreenkeyboard，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，HoloLens 2
ms.openlocfilehash: 398a7c57dc701fc848fe9091949b45b2c1796987
ms.sourcegitcommit: e5bd72d8b92976a6590e0f59706a88e66374934c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/31/2021
ms.locfileid: "106098269"
---
# <a name="keyboard-input-in-unity"></a>Unity 中的键盘输入

**命名空间：** *UnityEngine*<br>
 **类型**： *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

虽然 HoloLens 支持多种形式的输入，包括蓝牙键盘，但大多数应用程序都无法假定所有用户都有可用的物理键盘。 如果你的应用程序需要文本输入，则应该提供某种形式的屏幕键盘。

Unity 提供了 *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 类，可用于在没有可用物理键盘时接受键盘输入。

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Unity 中的 HoloLens 系统键盘行为

在 HoloLens 上， *TouchScreenKeyboard* 利用系统的屏幕键盘，并直接覆盖 MR 应用程序的容量耗尽视图。 经验类似于在 HoloLens 内置应用程序中使用键盘。 请注意，系统键盘的行为取决于目标平台的功能，例如，HoloLens 2 上的键盘支持直接交互，而 HoloLens 上的键盘 (第一代) 将支持 GGV (注视、手势和语音) 。 此外，在从编辑器向 HoloLens 执行 Unity 远程处理时，系统键盘不会显示。

## <a name="using-the-system-keyboard-in-your-unity-app"></a>在 Unity 应用中使用系统键盘

### <a name="declare-the-keyboard"></a>声明键盘

在类中，声明一个用于存储 *TouchScreenKeyboard* 的变量，并声明一个用于保存键盘返回的字符串的变量。

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>调用键盘

当请求键盘输入的事件发生时，使用以下项显示键盘。

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

您可以使用传递到函数的其他参数 `TouchScreenKeyboard.Open` 来控制键盘的行为 (例如，设置占位符文本或支持自动更正) 。 有关参数的完整列表，请参阅 [Unity 的文档](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html)。

### <a name="retrieve-typed-contents"></a>检索类型化内容

只需调用即可检索内容 `keyboard.text` 。 您可能想要每帧检索内容，或仅在键盘关闭时检索内容。

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a>备用键盘选项

除了直接使用 *TouchScreenKeyboard* 类之外，还可以使用 Unity 的 *UI 输入字段* 或 *TextMeshPro 输入字段* 获取用户输入。 此外，在 [MRTK](/windows/mixed-reality/mrtk-unity)的 [HandInteractionExamples 场景](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)中有一个基于 *TouchScreenKeyboard* 的实现 () 左侧有一个键盘交互示例。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所说的 Unity 开发旅程，就是探索混合现实平台功能和 Api。 在这里，你可以继续阅读任何 [主题](unity-development-overview.md#3-advanced-features) ，也可以直接跳转到在设备或模拟器上部署你的应用程序。

> [!div class="nextstepaction"]
> [部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳机](../platform-capabilities-and-apis/using-visual-studio.md)
