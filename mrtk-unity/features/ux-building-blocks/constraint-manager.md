---
title: 约束管理器
description: MRTK 中的约束管理器概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: f32f7321ec30f337e03d006f47fa92639796a74156483917331304811ea86a45
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198468"
---
# <a name="constraint-manager"></a>约束管理器

约束管理器允许将一组约束组件应用于转换。 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint)可以考虑附加到游戏对象的类型的组件。
约束管理器将自动收集附加到游戏对象的所有 [约束组件](#transform-constraints) ，并将其应用于处理的转换。
但是，用户可以选择手动配置应用的约束列表，只允许应用一部分附加约束。

目前，以下 MRTK UX 元素支持约束管理器：

- [边界控制](bounds-control.md)
- [对象操控器](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a>检查器属性和字段

约束管理器可在两种模式下操作：

- 自动约束选择
- 手动约束选择

### <a name="auto-constraint-selection"></a>自动约束选择

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

"约束管理器"、"自动约束选择" 的默认模式将提供所有附加的约束组件的列表，以及 " [切换到](#go-to-component) " 按钮和 " [添加约束" 按钮](#add-constraint-to-game-object)。

#### <a name="add-constraint-to-game-object"></a>将约束添加到游戏对象

使用此按钮可以从约束管理器检查器直接添加约束组件。 项目中的所有约束类型都应在此处可见。 有关详细信息，请参阅 [转换约束](#transform-constraints) 。

#### <a name="go-to-component"></a>中转到组件

在此对象上找到的所有约束都将在此处列出，并带有 " *中转到组件* " 按钮。 此按钮将使检查器滚动到选定的约束组件，以便可以对其进行配置。

### <a name="manual-constraint-selection"></a>手动约束选择

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

如果 "约束管理器" 设置为 "手动" 模式，则仅处理约束列表中链接的约束并将其应用于转换。 显示的列表将仅显示用户选择的约束以及 " [切换到" 按钮](#go-to-component) 或用于删除或添加条目的选项。
当首次启用手动模式时，约束管理器将填充列表，所有可用组件都作为选择附加约束组件的起点。

### <a name="remove-entry"></a>删除项

这会删除手动选定列表中的条目。 请注意，此选项不会从游戏对象中删除约束组件。 始终需要手动删除约束组件，以确保不会意外中断引用此组件的任何其他组件。

### <a name="add-entry"></a>添加条目

添加项将打开一个下拉列表，其中显示了不在手动列表中的所有可用约束组件。 单击该组件将添加到手动约束选择的任何条目。

### <a name="add-new-constraint"></a>添加新约束

此选项会将所选类型的组件添加到游戏对象，并将新创建的约束组件添加到 "手动约束" 列表中。

## <a name="transform-constraints"></a>转换约束

约束可用于以某种方式限制操作。 例如，某些应用程序可能需要旋转，但也要求对象保持直立。 在这种情况下， `RotationAxisConstraint` 可将添加到对象并用于限制旋转到 y 轴旋转。 MRTK 提供了许多约束，如下所述。

还可以定义新约束，并使用它们来创建某些应用程序可能需要的唯一操作行为。 为此，请创建一个继承自的脚本 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) 并实现抽象 `ConstraintType` 属性和抽象 `ApplyConstraint` 方法。 向对象添加新约束时，它应以定义的方式对操作进行约束。 此新约束还应显示在 "约束管理器 [自动选择](#auto-constraint-selection) " 或 "手动" 模式下的 " [添加项](#add-entry) " 下拉列表中。

MRTK 提供的所有约束都共享以下属性：

#### <a name="hand-type"></a>手写类型

指定是使用一种方法，还是使用两种类型的操作。 因为此属性是一个标志，所以这两个选项都可以选择。

- *One 右手*：如果选中，则在一种处理过程中将使用约束。
- 如果选中，则使用 *两个右手* 操作：约束。

#### <a name="proximity-type"></a>邻近性类型

指定约束是用于近、远还是两种类型的操作。 因为此属性是一个标志，所以这两个选项都可以选择。

- *Near*：如果选中，则在接近操作期间使用约束。
- *远*：如果选中，则将在远处操作期间使用约束。

### <a name="faceuserconstraint"></a>FaceUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

如果将此约束附加到对象，则旋转将受到限制，因此对象将始终面向用户。 这适用于清单或面板。 的属性如下所示 `FaceUserConstraint` ：

#### <a name="face-away"></a>离开

对象面对用户，如果为 true。

### <a name="fixeddistanceconstraint"></a>FixedDistanceConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

此约束修复操作对象与操作开始时的另一个对象转换之间的距离。 这对于修复从操作对象到 head 变换的距离等行为很有用。 的属性如下所示 `FixedDistanceConstraint` ：

#### <a name="constraint-transform"></a>约束转换

这是操作对象与之固定的距离的另一转换。 默认为相机转换。

### <a name="fixedrotationtouserconstraint"></a>FixedRotationToUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

此约束修复了用户与操作对象之间的相对旋转。 这对于清单或面板非常有用，因为它可确保操作的对象始终向用户显示与操作开始时相同的人脸。 没有 `FixedRotationToUserConstraint` 任何唯一属性。

### <a name="fixedrotationtoworldconstraint"></a>FixedRotationToWorldConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

此约束可修复操作对象在操作时的全局旋转。 如果操作不应有关旋转，这会很有用。 没有 `FixedRotationToWorldConstraint` 任何唯一的属性：

### <a name="maintainapparentsizeconstraint"></a>MaintainApparentSizeConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

如果将此约束附加到对象，无论该对象与用户的距离如何，它都会与用户保持相同的外观大小 (也就是说，它将占用用户的视图) 比例。 这可用于确保在操作时可以使用石板或文本面板。 没有 `MaintainApparentSizeConstraint` 任何唯一的属性：

### <a name="moveaxisconstraint"></a>MoveAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

此约束可用于修复可以移动操作对象的轴。 这对于在平面表面上操作对象或沿线条操作非常有用。 的属性如下所示 `MoveAxisConstraint` ：

#### <a name="constraint-on-movement"></a>移动约束

指定要阻止移动的轴。 默认情况下，这些轴是全局性的，而不是本地的，但可以在下面更改。 因为此属性是一个标志，所以可以选择任意数量的选项。

- *X 轴*：如果选中，则沿 X 轴移动。
- *Y 轴*：如果选中，则会约束沿 Y 轴移动。
- *Z 轴*：如果选中，则沿 z 轴移动。

#### <a name="use-local-space-for-constraint"></a>使用本地空间作为约束

如果为 true，则将限制操作对象的本地转换轴。 默认值为 False。

### <a name="rotationaxisconstraint"></a>RotationAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

此约束可用于解决操作对象可以旋转的轴。 这对于保持操作对象为直立，但仍允许 y 轴旋转很有用。 的属性如下所示 `RotationAxisConstraint` ：

#### <a name="constraint-on-rotation"></a>旋转约束

指定要防止旋转的轴。 默认情况下，这些轴是全局轴，而不是本地轴，但可以在下方进行更改。 由于此属性是标志，因此可以选择任意数目的选项。

- *Y 轴*：如果选中，则约束 y 轴的旋转。
- *Z 轴*：如果选中，则约束 z 轴的旋转。
- *X 轴*：如果选中，则约束 x 轴的旋转。

#### <a name="use-local-space-for-constraint"></a>使用本地空间进行约束

如果为 true，则约束被操作对象的局部转换轴的相对约束。 默认值为 False。

### <a name="minmaxscaleconstraint"></a>MinMaxScaleConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

此约束允许为操作对象的规模设置最小值和最大值。 这有助于防止用户缩放对象过小或太大。 的属性 `MinMaxScaleConstraint` 如下所示：

#### <a name="scale-minimum"></a>最小缩放

操作期间的最小缩放值。

#### <a name="scale-maximum"></a>缩放最大值

操作期间的最大缩放值。

#### <a name="relative-to-initial-state"></a>相对于初始状态

如果为 true，则上述值将解释为相对于对象初始刻度。 否则，它们将被解释为绝对小数位值。
