---
title: Unity 中的明确表述和眼睛跟踪
description: 了解在你在 Unity、手型手势和运动控制器中进行操作的两个关键方法。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 手势，运动控制器，unity，注视，输入，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，MRTK，混合现实工具包
ms.openlocfilehash: 8c1ab88358f4218fadce9b7a2a0dbd179b680eab
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759753"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Unity 中的明确表述和眼睛跟踪

HoloLens 2 引入了一些新的令人兴奋的功能，如经过表述的手势和眼睛跟踪。

利用 Unity 中新功能的最简单方法是使用 MRTK。 此外，还提供了一些帮助您入门的示例场景。

* [MRTK 中的明确表述入门](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/hand-tracking.md)
* [MRTK 中的目视跟踪入门](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-main.md)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>在 MRTK 中支持免提和其他的构建基块 

MRTK v2 提供一组 UI 控件和构建基块，有助于加快开发速度。

|  [ ![ 按钮](images/MRTK_Button_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md)[按钮](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md) | [ ![ 边界框](images/MRTK_BoundingBox_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/bounding-box.md)[边界框](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/bounding-box.md) | [ ![ 操作处理程序](images/MRTK_Manipulation_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/manipulation-handler.md)[操作处理程序](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/manipulation-handler.md) |
|:--- | :--- | :--- |
| "Button" 控件，支持各种输入方法，包括 HoloLens2's 的有向的手写 | 用于在三维空间中操作对象的标准 UI | 用一或两次手操作对象的脚本 |
|  [ ![ 石板](images/MRTK_Slate_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/slate.md)[石板](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/slate.md) | [ ![ 系统键盘](images/MRTK_SystemKeyboard_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/system-keyboard.md)[系统键盘](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/system-keyboard.md) | [ ![ 种不可交互](images/InteractableExamples.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/interactable.md)[种不可交互](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/interactable.md) |
| 2D 样式平面，它支持通过可表述的手写输入进行滚动 | 在 Unity 中使用系统键盘的示例脚本  | 用于使对象种不可交互可视状态和主题支持的脚本 |
|  [ ![ 规划](images/MRTK_Solver_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/solvers/solver.md)求解[求解](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/solvers/solver.md) | [ ![ 对象集合](images/MRTK_ObjectCollection_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-collection.md)[对象集合](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/object-collection.md) | [ ![ 工具](images/MRTK_Tooltip_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/tooltip.md)提示[工具提示](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/tooltip.md) |
| 各种对象定位行为，如标记、正文锁定、常量视图大小和 surface 磁性 | 用于在三维形状中布局对象数组的脚本 | 具有灵活的定位点/透视系统的批注 UI，可用于标记运动控制器和对象。 |
|  [ ![ 应用栏](images/MRTK_AppBar_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/app-bar.md)[应用栏](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/app-bar.md) | [ ![ 指针](images/MRTK_Pointer_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md)[指针](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md) | [ ![ 手指可视化](images/MRTK_FingertipVisualization_Main.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/fingertip-visualization.md)[手指可视化](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/fingertip-visualization.md) |
| 边界框手动激活的 UI | 了解各种类型的指针 | 手指上的视觉对象 affordance，提高了直接交互的置信度 |
|  [ ![ 目视跟踪：目标选择](images/mrtk_et_targetselect.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-target-selection.md)[目视跟踪：目标选择](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-target-selection.md) | [ ![ 目视跟踪：导航](images/mrtk_et_navigation.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-navigation.md)[目视跟踪：导航](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/eye-tracking/eye-tracking-navigation.md) | [ ![ 目视跟踪：热度地图](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html)[眼睛跟踪：热度地图](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| 将眼睛、语音和手输入组合在不同场景中快速轻松地选择全息影像 | 了解如何根据要查看的内容自动滚动文本或缩放到聚焦内容| 记录、加载和可视化用户在应用中查看的内容的示例 |

## <a name="example-scenes"></a>示例场景

在 [此示例场景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)中，探索 MRTK 的各种交互类型和 UI 控件。

可以在 "**资产/MixedRealityToolkit**" 下的 [混合现实工具包 GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)中找到其他示例场景。

[![示例场景](images/MRTK_Examples.png)](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/example-scenes/hand-interaction-examples.md)

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所说的 Unity 开发旅程，就是在浏览 MRTK 核心构建基块。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [空间映射](spatial-mapping-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅

* [基于眼睛的交互](../../design/eye-gaze-interaction.md)
* [HoloLens 2 中的眼动跟踪](../../design/eye-tracking.md)
* [凝视和提交](../../design/gaze-and-commit.md)
* [手 - 直接操作](../../design/direct-manipulation.md)
* [手 - 手势](../../design/gaze-and-commit.md#composite-gestures)
* [手 - 指向并提交](../../design/point-and-commit.md)
* [本能交互](../../design/interaction-fundamentals.md)
* [运动控制器](../../design/motion-controllers.md)
* [UnityEngine. XR](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
