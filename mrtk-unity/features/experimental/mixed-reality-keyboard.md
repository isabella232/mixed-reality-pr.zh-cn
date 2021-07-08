---
title: 混合现实键盘
description: 如何使用混合现实键盘的说明
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 6a33ed5b021e90cba56344f32a9c9a33e8fcc476
ms.sourcegitcommit: c260aed8a37855faf9575d968e615959a56a13fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2021
ms.locfileid: "113466227"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a><span data-ttu-id="7c033-104">混合现实和 HoloLens 键盘帮助程序类</span><span class="sxs-lookup"><span data-stu-id="7c033-104">Mixed Reality and HoloLens Keyboard Helper Classes</span></span>

<span data-ttu-id="7c033-105">MRTK 提供了多个试验性帮助程序组件，以帮助从 [系统键盘](../ux-building-blocks/system-keyboard.md)启动和读取文本。</span><span class="sxs-lookup"><span data-stu-id="7c033-105">MRTK provides several experimental helper components to assist with launching and reading text from the [System Keyboard](../ux-building-blocks/system-keyboard.md).</span></span>

<span data-ttu-id="7c033-106">请注意，系统键盘的行为取决于目标平台的功能，例如 HoloLens 2 上的键盘支持直接交互，而 HoloLens (第一代) 将支持 GGV<sup>[1](/windows/mixed-reality/gaze)</sup>。</span><span class="sxs-lookup"><span data-stu-id="7c033-106">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="7c033-107">此外，在从编辑器执行[Unity 远程处理](../tools/holographic-remoting.md)到 HoloLens 时，系统键盘不会显示。</span><span class="sxs-lookup"><span data-stu-id="7c033-107">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="mixedrealitykeyboard"></a><span data-ttu-id="7c033-108">MixedRealityKeyboard</span><span class="sxs-lookup"><span data-stu-id="7c033-108">MixedRealityKeyboard</span></span>

<span data-ttu-id="7c033-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) 是一个组件，它提供用于启动和关闭系统键盘以及与键盘输入的文本交互的方法。</span><span class="sxs-lookup"><span data-stu-id="7c033-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) is a component that provides methods for launching and closing a system keyboard, as well as interacting with text entered by the keyboard.</span></span>  

### <a name="how-to-use"></a><span data-ttu-id="7c033-110">使用方法</span><span class="sxs-lookup"><span data-stu-id="7c033-110">How to Use</span></span>

1. <span data-ttu-id="7c033-111">将 [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) 组件附加到任何对象。</span><span class="sxs-lookup"><span data-stu-id="7c033-111">Attach the [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) component to any object.</span></span>
2. <span data-ttu-id="7c033-112">调用 `ShowKeyboard(string text = "", bool multiLine = false)` `HideKeyboard()` 以显示和隐藏键盘，并处理 `OnShowKeyboard` 、 `OnHideKeyboard` 和 `OnCommitText` 事件以处理在显示、隐藏键盘以及按下 enter 键时要处理的事件。</span><span class="sxs-lookup"><span data-stu-id="7c033-112">Call `ShowKeyboard(string text = "", bool multiLine = false)` `HideKeyboard()` to show and hide the keyboard, and handle the `OnShowKeyboard`, `OnHideKeyboard` and `OnCommitText` events to handle when the keyboard is shown, hidden, and when the enter key is pressed.</span></span>

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a><span data-ttu-id="7c033-113">输入字段 TMP_KeyboardInputField 和 UI_KeyboardInputField</span><span class="sxs-lookup"><span data-stu-id="7c033-113">Input fields TMP_KeyboardInputField, and UI_KeyboardInputField</span></span>

<span data-ttu-id="7c033-114">[`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField)和 [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 类是可以添加到文本输入字段的组件，可在单击时自动调用系统键盘，并在用户输入文本时更新文本输入字段内容。</span><span class="sxs-lookup"><span data-stu-id="7c033-114">The [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) and [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classes are components that can be added to text input fields to automatically invoke the system keyboard when clicked and update the text input field contents as the user enters text.</span></span>

### <a name="how-to-use"></a><span data-ttu-id="7c033-115">如何使用</span><span class="sxs-lookup"><span data-stu-id="7c033-115">How to use</span></span>

1. <span data-ttu-id="7c033-116">为 UnityUI 或 TextMeshPro 创建输入字段。</span><span class="sxs-lookup"><span data-stu-id="7c033-116">Create an input field for either UnityUI or TextMeshPro.</span></span>
2. <span data-ttu-id="7c033-117">将相应的 [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) 或 [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 组件添加到输入字段游戏对象。</span><span class="sxs-lookup"><span data-stu-id="7c033-117">Add the corresponding [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) or [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) component to the input field game object.</span></span>

<span data-ttu-id="7c033-118">UnityUI 输入字段和 TextMeshPro (TMPro) 输入字段的 prototyping 在 "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs" 中提供</span><span class="sxs-lookup"><span data-stu-id="7c033-118">Prefabs for both UnityUI input fields and TextMeshPro (TMPro) input fields are available at "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span></span>

<span data-ttu-id="7c033-119">如何使用 TMP_KeyboardInputField 和 UI_KeyboardInputField 的示例位于 "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span><span class="sxs-lookup"><span data-stu-id="7c033-119">An example of how the to use TMP_KeyboardInputField and UI_KeyboardInputField is at "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span></span>