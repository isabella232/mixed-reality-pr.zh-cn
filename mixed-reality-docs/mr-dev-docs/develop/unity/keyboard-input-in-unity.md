---
title: Unity 中的键盘输入
description: Unity 提供 TouchScreenKeyboard 类，用于当没有可用的物理键盘时接受键盘输入。
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: 键盘、输入、unity、触摸屏键盘、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、HoloLens、HoloLens 2
ms.openlocfilehash: a7bd392036ca548fdd1f25581c8fc1910308909253f9c8df763e2039a32d3e9a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203849"
---
# <a name="keyboard-input-in-unity"></a>Unity 中的键盘输入

**命名空间***：UnityEngine*<br>
 **类型***[：TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

尽管HoloLens支持包括键盘蓝牙形式的输入，但大多数应用程序无法假定所有用户都有可用的物理键盘。 如果应用程序需要文本输入，应提供某种形式的屏幕键盘。

Unity 提供 *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 类，用于当没有可用的物理键盘时接受键盘输入。

## <a name="hololens-system-keyboard-behavior-in-unity"></a>HoloLens Unity 中的系统键盘行为

在 *HoloLens，TouchScreenKeyboard* 利用系统的屏幕键盘并直接覆盖 MR 应用程序的音量视图。 此体验类似于在应用的内置应用中使用键盘HoloLens。 请注意，系统键盘的行为取决于目标平台的功能，例如 HoloLens 2 上的键盘支持直接手部交互，而 HoloLens (第一代) 上的键盘支持 GGV (凝视、手势和语音) 。 此外，执行从编辑器到编辑器的 Unity 远程处理时，系统键盘HoloLens。

## <a name="using-the-system-keyboard-in-your-unity-app"></a>在 Unity 应用中使用系统键盘

### <a name="declare-the-keyboard"></a>声明键盘

在 类中，声明用于存储 *TouchScreenKeyboard* 的变量和用于保存键盘返回的字符串的变量。

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>调用键盘

当发生请求键盘输入的事件时，使用以下命令显示键盘。

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

可以使用传递给 函数的其他参数来控制键盘 (例如设置占位符文本或支持自动 `TouchScreenKeyboard.Open` 更正) 。 有关参数的完整列表，请参阅 [Unity 的文档](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html)。

### <a name="retrieve-typed-contents"></a>检索类型内容

只需调用 来检索内容 `keyboard.text` 。 你可能希望检索每帧的内容，或仅在键盘关闭时检索内容。

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a>备用键盘选项

除了直接使用 *TouchScreenKeyboard* 类外，还可使用 Unity 的 *UI* 输入字段或 *TextMeshPro 输入字段 获取用户输入*。 此外 [，MRTK](/windows/mixed-reality/mrtk-unity)的 [HandInteractionExamples](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)场景中有一个基于 *TouchScreenKeyboard* 的实现 (左侧左侧有一个键盘交互) 。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们布局的 Unity 开发旅程，则你正在探索混合现实平台功能和 API。 在这里，可以继续学习任何 [主题](unity-development-overview.md#3-advanced-features) ，也可以直接跳转到在设备或仿真器上部署应用。

> [!div class="nextstepaction"]
> [部署到HoloLens或Windows Mixed Reality沉浸式头戴显示设备](../platform-capabilities-and-apis/using-visual-studio.md)
