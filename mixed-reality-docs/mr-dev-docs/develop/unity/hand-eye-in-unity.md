---
title: Unity 中的手部和眼动跟踪
description: 了解在 Unity 中对凝视采取措施的两种关键方法：手势和运动控制器。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 手势， 运动控制器， unity， 凝视， 输入， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， MRTK， 混合现实工具包
ms.openlocfilehash: ff4c4b064e11e0cad45f4b0c1aaa90c61eda51d7
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600656"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Unity 中的手部和眼动跟踪

HoloLens 2引入了一些令人兴奋的新功能，例如"手部和眼部跟踪"。

在 Unity 中利用新功能的最简单方法是通过 MRTK。 还有一些示例场景可帮助你入门。

* [MRTK 中的表达手入门](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
* [MRTK 中的眼动跟踪入门](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>在 MRTK 中支持手部、眼睛和其他的构建基块

MRTK v2 提供了一组 UI 控件和构建基块，可帮助你加速开发。

|  [![按钮](images/MRTK_Button_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) [按钮](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) | [ ![ 边界框](images/MRTK_BoundingBox_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)[边界框](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) | [ ![ 操作处理程序](images/MRTK_Manipulation_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler)[操作处理程序](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) |
|:--- | :--- | :--- |
| 按钮控件，支持各种输入方法，包括 HoloLens2 的铰接手 | 用于模拟 3D 空间中的对象的标准 UI | 用于通过单手或双手操控对象的脚本 |
|  [![场记板](images/MRTK_Slate_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) [场记板](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) | [![系统键盘](images/MRTK_SystemKeyboard_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) [系统键盘](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) | [![可交互](images/InteractableExamples.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) [可交互](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) |
| 2D 样式平面，支持使用明确手部输入进行滚动 | 用于在 Unity 中使用系统键盘的示例脚本  | 用于使对象可与可视状态和主题支持进行交互的脚本 |
|  [![求解器](images/MRTK_Solver_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) [求解器](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) | [![对象集合](images/MRTK_ObjectCollection_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) [对象集合](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) | [![工具提示](images/MRTK_Tooltip_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) [工具提示](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) |
| 各种对象定位行为，例如标记沿、人体锁定、恒定视图大小和表面磁力 | 用于以三维形状布局对象数组的脚本 | 具有灵活定位点/透视系统的批注 UI，可用于标记运动控制器和对象。 |
|  [![应用栏](images/MRTK_AppBar_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) [应用栏](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) | [![指针](images/MRTK_Pointer_Main.png)](/windows/mixed-reality/mrtk-unity/features/input/pointers) [指针](/windows/mixed-reality/mrtk-unity/features/input/pointers) | [![指尖可视化](images/MRTK_FingertipVisualization_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) [指尖可视化](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) |
| 用于边界框手动激活的 UI | 了解各种类型的指针 | 视觉视觉视觉元素，可提高直接交互的置信度 |
|  [![眼动跟踪：目标选择](images/mrtk_et_targetselect.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) [眼动跟踪：目标选择](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) | [![眼动跟踪：导航](images/mrtk_et_navigation.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) [眼动跟踪：导航](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) | [![眼动跟踪：热图](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) [眼动跟踪：热图](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| 组合眼睛、语音和手部输入，快速轻松地选择场景中的全息影像 | 了解如何根据正在查看的内容自动滚动文本或放大焦点内容| 记录、加载和可视化用户在应用中看到的内容的示例 |

## <a name="example-scenes"></a>示例场景

在 [此示例场景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)中，了解 MRTK 各种类型的交互和 UI 控件。

可以在混合现实工具包 [GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity) 中的 **Assets/MixedRealityToolkit.Examples/Demos** 文件夹下找到其他示例场景。

[![示例场景](images/MRTK_Examples.png)](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们布局的 Unity 开发旅程，则你正在探索 MRTK 核心构建基块。 从这里，你可以继续了解下一部分基础知识：

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
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)