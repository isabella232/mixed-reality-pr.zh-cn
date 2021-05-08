---
title: 对话框
description: 对话框控件的说明。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 729c3f6a6b9bc63a498c5d76205a0730f52c678a
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489187"
---
# <a name="dialog"></a>对话框

![对话框](../images/dialog/MRTK_UX_Dialog_Main.png)

对话框控件是提供上下文应用信息的 UI 覆盖。 它们通常会请求用户进行某种类型的操作。 使用对话框通知用户重要信息或在可以完成某个操作之前请求确认或其他信息。

## <a name="example-scene"></a>示例场景

可以在 **DialogExample** 场景下找到示例 [：MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)

## <a name="how-to-use-dialog-control"></a>如何使用对话框控件

MRTK 提供三个对话框预制：

- DialogSmall_192x96.prefab
- DialogMedium_192x128.prefab
- DialogLarge_192x192.prefab

使用 Dialog.Open () 打开一个新对话框。 指定对话框预制、按钮数、标题文本、消息文本、放置距离 (或) 位置、其他) 。 对话框提供"确认 (按钮) "和"选择 (按钮) "对话框选项。

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a>使用单个"确定"按钮打开大型对话的示例，该按钮放置在远交互范围内 (凝视、手部射线、运动控制器) 

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a>打开包含用户选择消息的"小"对话框的示例，放置在接近交互范围 (直接手动交互) 

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

有关详细信息，请参阅 `DialogExampleController.cs` DialogExample.unity 场景中的 。
