---
title: 输入操作
description: 用于在 MRTK 中创建输入操作的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，InputActions，
ms.openlocfilehash: ffa8f201097c8d85b1ea19613b608487529412f3686ddf077f1acc1c34e93c1f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211210"
---
# <a name="input-actions"></a>输入操作

[**输入操作**](input-actions.md) 是针对原始输入的抽象，旨在帮助将应用程序逻辑与产生输入的特定输入源隔离开来。 例如，可以定义 " *选择* " 操作并将其映射到鼠标左键、游戏板中的按钮和 6 DOF 控制器中的触发器，这一点非常有用。 然后，你可以让应用程序逻辑侦听 *选择* 输入操作事件，而无需知道可以生成的所有不同输入。

## <a name="creating-an-input-action"></a>创建输入操作

输入操作在 **输入操作配置文件** 中的 "混合现实 Toolkit" 组件内的 *输入系统配置文件* 中进行配置，指定操作的名称和输入 (*轴约束* 的类型) 可将其映射到：

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

这些是最常使用的 **轴约束** 值：

轴约束 | 说明
--- | ---
数码 | 开启/关闭输入，例如游戏板或鼠标中的二元按钮。
单轴 | 单轴模拟游戏中的输入，例如模拟触发器。
双轴 | 双轴模拟输入，例如操纵杆。
6 Dof | 3D 姿势，其中包含由6个 DOF 控制器生成的平移和旋转。

可以在中找到完整列表 [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) 。

## <a name="mapping-input-to-actions"></a>将输入映射到操作

将输入映射到和操作的方式取决于输入源的类型：

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
