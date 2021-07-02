---
title: 输入操作
description: 在 MRTK 中创建输入操作的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， InputActions，
ms.openlocfilehash: cf6ce2af304ee1cd706d0111d66a97018113fb09
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176812"
---
# <a name="input-actions"></a>输入操作

[**输入操作**](input-actions.md) 是原始输入的抽象，有助于将应用程序逻辑与生成输入的特定输入源隔离。 例如，定义"选择"操作，将其映射到鼠标左键、游戏板中的按钮和 6 DOF 控制器中的触发器等可能很有用。 然后，你可以让应用程序逻辑侦听"选择输入操作"事件，而不必了解可生成它的所有不同输入。

## <a name="creating-an-input-action"></a>创建输入操作

输入操作在"输入操作配置文件"中配置，在混合现实 Toolkit 组件的"输入系统配置文件"内，指定操作的名称和输入类型 (轴 *约束) 可* 映射到：

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

转到"输入 **系统配置文件"下的**"控制器 *输入映射配置文件"。* 可在这里找到所有受支持控制器的列表：

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

选择要配置的对话框，将显示一个对话框窗口，其中显示所有控制器输入，允许为其中每个输入设置操作：

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a>语音输入

在 **"语音命令配置文件"** 的" *输入系统* 配置文件"下，可以找到当前定义的语音命令的列表。 若要将其中一个映射到操作，只需在"操作"下拉列表 *中选择* 它。

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a>笔势输入

" **笔势配置文件"** 在 *"输入系统配置文件"下* 包含所有定义的笔势。 可以在"操作"下拉列表中选择每个操作， *将其映射到操作* 。

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a>处理输入操作

> [!WARNING]
> 目前，只能使用本节中所述的方法处理数字类型的输入操作。 对于其他操作类型，必须改为直接处理相应输入的事件。 例如，若要处理映射到控制器输入的 6 DOF 操作，必须使用 T = [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) 。

处理输入操作的最简单方法是使用 [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) 脚本。 这允许你定义想要侦听的操作，以及使用 Unity 事件对已启动和已结束事件的操作做出反应。

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

如果想进行更多控制，可以直接 [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) 在脚本中实现 接口。 有关通过 [**处理程序**](input-events.md) 接口处理事件的详细信息，请参阅输入事件部分。

## <a name="examples"></a>示例

请参阅示例场景，了解如何创建操作、将操作映射到控制器、语音和手势输入，并使用它在命令上 `MRTK/Examples/Demos/Input/Scenes/InputActions` 旋转对象。

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
