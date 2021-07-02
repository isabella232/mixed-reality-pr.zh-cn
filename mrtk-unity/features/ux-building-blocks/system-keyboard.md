---
title: 系统键盘
description: MRTK 中的系统密钥板概述
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，系统键盘，
ms.openlocfilehash: 9b1db512a1a4e27a2c41e8e8b5752200c461ee6e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176490"
---
# <a name="system-keyboard"></a><span data-ttu-id="74acc-104">系统键盘</span><span class="sxs-lookup"><span data-stu-id="74acc-104">System keyboard</span></span>

![系统键盘](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

<span data-ttu-id="74acc-106">Unity 应用程序可以随时调用系统键盘。</span><span class="sxs-lookup"><span data-stu-id="74acc-106">A Unity application can invoke the system keyboard at any time.</span></span> <span data-ttu-id="74acc-107">请注意，系统键盘的行为取决于目标平台的功能，例如 HoloLens 2 上的键盘支持直接交互，而 HoloLens (第一代) 将支持 GGV (注视、手势和语音) <sup>[1](/windows/mixed-reality/gaze)</sup>。</span><span class="sxs-lookup"><span data-stu-id="74acc-107">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice)<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="74acc-108">此外，在从编辑器执行[Unity 远程处理](../tools/holographic-remoting.md)到 HoloLens 时，系统键盘不会显示。</span><span class="sxs-lookup"><span data-stu-id="74acc-108">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="how-to-invoke-the-system-keyboard"></a><span data-ttu-id="74acc-109">如何调用系统键盘</span><span class="sxs-lookup"><span data-stu-id="74acc-109">How to invoke the system keyboard</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a><span data-ttu-id="74acc-110">如何读取输入</span><span class="sxs-lookup"><span data-stu-id="74acc-110">How to read the input</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

private void Update()
{
    if (keyboard != null)
    {
        keyboardText = keyboard.text;
        // Do stuff with keyboardText
    }
}
```

## <a name="system-keyboard-example"></a><span data-ttu-id="74acc-111">系统键盘示例</span><span class="sxs-lookup"><span data-stu-id="74acc-111">System keyboard example</span></span>

<span data-ttu-id="74acc-112">你可以看到一个简单的示例，演示如何在 `MixedRealityKeyboard.cs` (资产/MRTK/SDK/实验性/功能/UX/MixedRealityKeyboard 中引入系统键盘) </span><span class="sxs-lookup"><span data-stu-id="74acc-112">You can see a simple example of how to bring up system keyboard in `MixedRealityKeyboard.cs` (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)</span></span>

## <a name="see-also"></a><span data-ttu-id="74acc-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74acc-113">See Also</span></span>

- [<span data-ttu-id="74acc-114">混合现实键盘帮助程序类</span><span class="sxs-lookup"><span data-stu-id="74acc-114">Mixed Reality Keyboard Helper Classes</span></span>](../experimental/mixed-reality-keyboard.md)
