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
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a><span data-ttu-id="fac6d-104">混合现实和 HoloLens 键盘帮助程序类</span><span class="sxs-lookup"><span data-stu-id="fac6d-104">Mixed Reality and HoloLens Keyboard Helper Classes</span></span>

<span data-ttu-id="fac6d-105">MRTK 提供了几个实验性帮助程序组件，以帮助从系统键盘 启动和 [读取文本](../ux-building-blocks/system-keyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="fac6d-105">MRTK provides several experimental helper components to assist with launching and reading text from the [System Keyboard](../ux-building-blocks/system-keyboard.md).</span></span>

<span data-ttu-id="fac6d-106">请注意，系统键盘的行为取决于目标平台的功能，例如 HoloLens 2 上的键盘支持直接手部交互，而 HoloLens (第一代) 上的键盘支持 GGV<sup>[1。](/windows/mixed-reality/gaze)</sup></span><span class="sxs-lookup"><span data-stu-id="fac6d-106">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="fac6d-107">此外，执行从编辑器到 HoloLens 的 [Unity 远程](../tools/holographic-remoting.md) 处理时，系统键盘不会显示。</span><span class="sxs-lookup"><span data-stu-id="fac6d-107">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="mixedrealitykeyboard"></a><span data-ttu-id="fac6d-108">MixedRealityKeyboard</span><span class="sxs-lookup"><span data-stu-id="fac6d-108">MixedRealityKeyboard</span></span>

<span data-ttu-id="fac6d-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) 是一个 组件，它提供启动和关闭系统键盘以及与键盘输入的文本进行交互的方法。</span><span class="sxs-lookup"><span data-stu-id="fac6d-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) is a component that provides methods for launching and closing a system keyboard, as well as interacting with text entered by the keyboard.</span></span>  

### <a name="how-to-use"></a><span data-ttu-id="fac6d-110">使用方法</span><span class="sxs-lookup"><span data-stu-id="fac6d-110">How to Use</span></span>

1. <span data-ttu-id="fac6d-111">将 [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) 组件附加到任何对象。</span><span class="sxs-lookup"><span data-stu-id="fac6d-111">Attach the [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) component to any object.</span></span>
2. <span data-ttu-id="fac6d-112">调用 `Show()` `Hide()` 以显示和隐藏键盘，并处理在显示、隐藏键盘和按 Enter 键时要处理的 `OnShowKeyboard` `OnHideKeyboard` 和 `OnCommitText` 事件。</span><span class="sxs-lookup"><span data-stu-id="fac6d-112">Call `Show()` `Hide()` to show and hide the keyboard, and handle the `OnShowKeyboard`, `OnHideKeyboard` and `OnCommitText` events to handle when the keyboard is shown, hidden, and when the enter key is pressed.</span></span>

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a><span data-ttu-id="fac6d-113">输入字段TMP_KeyboardInputField和UI_KeyboardInputField</span><span class="sxs-lookup"><span data-stu-id="fac6d-113">Input fields TMP_KeyboardInputField, and UI_KeyboardInputField</span></span>

<span data-ttu-id="fac6d-114">和 类是可添加到文本输入字段的组件，可在单击时自动调用系统键盘，在用户输入文本时 [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 更新文本输入字段内容。</span><span class="sxs-lookup"><span data-stu-id="fac6d-114">The [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) and [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classes are components that can be added to text input fields to automatically invoke the system keyboard when clicked and update the text input field contents as the user enters text.</span></span>

### <a name="how-to-use"></a><span data-ttu-id="fac6d-115">如何使用</span><span class="sxs-lookup"><span data-stu-id="fac6d-115">How to use</span></span>

1. <span data-ttu-id="fac6d-116">为 UnityUI 或 TextMeshPro 创建输入字段。</span><span class="sxs-lookup"><span data-stu-id="fac6d-116">Create an input field for either UnityUI or TextMeshPro.</span></span>
2. <span data-ttu-id="fac6d-117">将相应的 [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) 或 [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) 组件添加到输入字段游戏对象。</span><span class="sxs-lookup"><span data-stu-id="fac6d-117">Add the corresponding [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) or [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) component to the input field game object.</span></span>

<span data-ttu-id="fac6d-118">UnityUI 输入字段和 TextMeshPro (TMPro) 输入字段的预制项位于"Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span><span class="sxs-lookup"><span data-stu-id="fac6d-118">Prefabs for both UnityUI input fields and TextMeshPro (TMPro) input fields are available at "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span></span>

<span data-ttu-id="fac6d-119">在"Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"中TMP_KeyboardInputField UI_KeyboardInputField示例演示了如何使用 和</span><span class="sxs-lookup"><span data-stu-id="fac6d-119">An example of how the to use TMP_KeyboardInputField and UI_KeyboardInputField is at "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span></span>