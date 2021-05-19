---
title: 输入操作
description: 在 MRTK 中创建输入操作的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， InputActions，
ms.openlocfilehash: 071d4bc8bb4193a3d60cb53852c192ae975d79df
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144158"
---
# <a name="input-actions"></a>输入操作

[**输入操作**](input-actions.md) 是原始输入的抽象，有助于将应用程序逻辑与生成输入的特定输入源隔离。 例如，定义"选择"操作，将其映射到鼠标左键、游戏板中的按钮和 6 DOF 控制器中的触发器等可能很有用。 然后，你可以让应用程序逻辑侦听"选择输入操作"事件，而不必了解可生成它的所有不同输入。

## <a name="creating-an-input-action"></a>创建输入操作

输入操作在"输入操作配置文件"中配置，在混合现实工具包组件的"输入系统配置文件"内，指定操作的名称和输入类型 (轴约束) 可映射到： 

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

这些是轴约束最常使用 **的值**：

轴约束 | 说明
--- | ---
数码 | 打开/关闭输入，如游戏板或鼠标中的二进制按钮。
单轴 | 单轴倾斜输入，如游戏板中的模拟触发器。
双轴 | 双轴倾斜输入，如滚动块。
六个 Dof | 具有平移和旋转的 3D 姿势，如 6 个 DOF 控制器生成的 3D 姿势。

可以在 中查找完整列表 [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) 。

## <a name="mapping-input-to-actions"></a>将输入映射到操作

将输入映射到 和 操作的方式取决于输入源的类型：

### <a name="controller-input"></a>控制器输入

在 *输入系统配置文件* 下，中转到 **控制器输入映射配置文件**。 可在其中找到所有受支持的控制器的列表：

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

选择要配置的配置，将出现一个对话框窗口，其中包含所有控制器输入，使你可以为每个输入设置操作：

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a>语音输入

在 **语音命令配置文件** 中的 *输入系统配置文件* 下，你会看到当前定义的语音命令的列表。 若要将其中一项映射到操作，只需在 " *操作* " 下拉列表中选择它即可。

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a>手势输入

**笔势配置文件** 位于 *输入系统配置文件* 下，包含所有定义的手势。 可以通过在 " *操作* " 下拉列表中选择每个操作，将它们映射到某个操作。

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a>处理输入操作

> [!WARNING]
> 目前只能使用本节中所述的方法来处理 *数字* 类型的输入操作。 对于其他操作类型，您必须直接处理相应输入的事件。 例如，若要处理映射到控制器输入的 6 DOF 操作，则必须 [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) 与 T = 一起使用 [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) 。

处理输入操作的最简单方法是使用 [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) 脚本。 这允许您定义要侦听的操作，并使用 Unity 事件对操作开始和结束事件做出反应。

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

如果需要更多控制，可以 [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) 直接在脚本中实现接口。 有关通过处理程序接口的事件处理的更多详细信息，请参阅 [**输入事件**](input-events.md) 部分。

## <a name="examples"></a>示例

`MRTK/Examples/Demos/Input/Scenes/InputActions`有关演示如何创建操作的示例场景，请参阅将其映射到控制器、语音和手势输入，并使用它来旋转命令上的对象。

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
