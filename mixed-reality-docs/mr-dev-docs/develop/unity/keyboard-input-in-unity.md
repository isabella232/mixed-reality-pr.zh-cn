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
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="0f4af-104">Unity 中的键盘输入</span><span class="sxs-lookup"><span data-stu-id="0f4af-104">Keyboard input in Unity</span></span>

<span data-ttu-id="0f4af-105">**命名空间：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="0f4af-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="0f4af-106">**类型**： *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="0f4af-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="0f4af-107">虽然 HoloLens 支持多种形式的输入，包括蓝牙键盘，但大多数应用程序都无法假定所有用户都有可用的物理键盘。</span><span class="sxs-lookup"><span data-stu-id="0f4af-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications can't assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="0f4af-108">如果你的应用程序需要文本输入，则应该提供某种形式的屏幕键盘。</span><span class="sxs-lookup"><span data-stu-id="0f4af-108">If your application requires text input, some form of on-screen keyboard should be provided.</span></span>

<span data-ttu-id="0f4af-109">Unity 提供了 *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 类，可用于在没有可用物理键盘时接受键盘输入。</span><span class="sxs-lookup"><span data-stu-id="0f4af-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there's no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="0f4af-110">Unity 中的 HoloLens 系统键盘行为</span><span class="sxs-lookup"><span data-stu-id="0f4af-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="0f4af-111">在 HoloLens 上， *TouchScreenKeyboard* 利用系统的屏幕键盘，并直接覆盖 MR 应用程序的容量耗尽视图。</span><span class="sxs-lookup"><span data-stu-id="0f4af-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on-screen keyboard and directly overlays on top of the volumetric view of your MR application.</span></span> <span data-ttu-id="0f4af-112">经验类似于在 HoloLens 内置应用程序中使用键盘。</span><span class="sxs-lookup"><span data-stu-id="0f4af-112">The experience is similar to using keyboard in the built-in apps of HoloLens.</span></span> <span data-ttu-id="0f4af-113">请注意，系统键盘的行为取决于目标平台的功能，例如，HoloLens 2 上的键盘支持直接交互，而 HoloLens 上的键盘 (第一代) 将支持 GGV (注视、手势和语音) 。</span><span class="sxs-lookup"><span data-stu-id="0f4af-113">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice).</span></span> <span data-ttu-id="0f4af-114">此外，在从编辑器向 HoloLens 执行 Unity 远程处理时，系统键盘不会显示。</span><span class="sxs-lookup"><span data-stu-id="0f4af-114">Additionally, the system keyboard will not show up when performing Unity Remoting from the editor to a HoloLens.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="0f4af-115">在 Unity 应用中使用系统键盘</span><span class="sxs-lookup"><span data-stu-id="0f4af-115">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="0f4af-116">声明键盘</span><span class="sxs-lookup"><span data-stu-id="0f4af-116">Declare the keyboard</span></span>

<span data-ttu-id="0f4af-117">在类中，声明一个用于存储 *TouchScreenKeyboard* 的变量，并声明一个用于保存键盘返回的字符串的变量。</span><span class="sxs-lookup"><span data-stu-id="0f4af-117">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="0f4af-118">调用键盘</span><span class="sxs-lookup"><span data-stu-id="0f4af-118">Invoke the keyboard</span></span>

<span data-ttu-id="0f4af-119">当请求键盘输入的事件发生时，使用以下项显示键盘。</span><span class="sxs-lookup"><span data-stu-id="0f4af-119">When an event occurs requesting keyboard input, use the following to show the keyboard.</span></span>

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

<span data-ttu-id="0f4af-120">您可以使用传递到函数的其他参数 `TouchScreenKeyboard.Open` 来控制键盘的行为 (例如，设置占位符文本或支持自动更正) 。</span><span class="sxs-lookup"><span data-stu-id="0f4af-120">You can use additional parameters passed into the `TouchScreenKeyboard.Open` function to control the behavior of the keyboard (e.g. setting placeholder text or supporting autocorrection).</span></span> <span data-ttu-id="0f4af-121">有关参数的完整列表，请参阅 [Unity 的文档](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html)。</span><span class="sxs-lookup"><span data-stu-id="0f4af-121">For the full list of parameters please refer to [Unity's documentation](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).</span></span>

### <a name="retrieve-typed-contents"></a><span data-ttu-id="0f4af-122">检索类型化内容</span><span class="sxs-lookup"><span data-stu-id="0f4af-122">Retrieve typed contents</span></span>

<span data-ttu-id="0f4af-123">只需调用即可检索内容 `keyboard.text` 。</span><span class="sxs-lookup"><span data-stu-id="0f4af-123">The content can simply be retrieved by calling `keyboard.text`.</span></span> <span data-ttu-id="0f4af-124">您可能想要每帧检索内容，或仅在键盘关闭时检索内容。</span><span class="sxs-lookup"><span data-stu-id="0f4af-124">You may want to retrieve the content per frame or only when the keyboard is closed.</span></span>

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="0f4af-125">备用键盘选项</span><span class="sxs-lookup"><span data-stu-id="0f4af-125">Alternative keyboard options</span></span>

<span data-ttu-id="0f4af-126">除了直接使用 *TouchScreenKeyboard* 类之外，还可以使用 Unity 的 *UI 输入字段* 或 *TextMeshPro 输入字段* 获取用户输入。</span><span class="sxs-lookup"><span data-stu-id="0f4af-126">Besides using the *TouchScreenKeyboard* class directly, you can also get user input by using Unity's *UI Input Field* or *TextMeshPro Input Field*.</span></span> <span data-ttu-id="0f4af-127">此外，在 [MRTK](/windows/mixed-reality/mrtk-unity)的 [HandInteractionExamples 场景](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)中有一个基于 *TouchScreenKeyboard* 的实现 () 左侧有一个键盘交互示例。</span><span class="sxs-lookup"><span data-stu-id="0f4af-127">Additionally, there is an implementation based on *TouchScreenKeyboard* in the [HandInteractionExamples scene](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) of [MRTK](/windows/mixed-reality/mrtk-unity) (there is a keyboard interaction sample on the left hand side).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="0f4af-128">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="0f4af-128">Next Development Checkpoint</span></span>

<span data-ttu-id="0f4af-129">如果遵循我们所说的 Unity 开发旅程，就是探索混合现实平台功能和 Api。</span><span class="sxs-lookup"><span data-stu-id="0f4af-129">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="0f4af-130">在这里，你可以继续阅读任何 [主题](unity-development-overview.md#3-advanced-features) ，也可以直接跳转到在设备或模拟器上部署你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0f4af-130">From here, you can continue to any [topic](unity-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0f4af-131">部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳机</span><span class="sxs-lookup"><span data-stu-id="0f4af-131">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
