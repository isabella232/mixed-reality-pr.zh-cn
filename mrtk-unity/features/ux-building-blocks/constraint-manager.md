---
title: 约束管理器
description: MRTK 中的约束管理器概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 7036bb552952a0e45a8ba465d769a8952e48bc36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177555"
---
# <a name="constraint-manager"></a>约束管理器

约束管理器允许将一组约束组件应用于转换。 可以 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) 考虑附加到游戏对象的类型的组件。
默认情况下，约束管理器将自动 [收集附加到游戏](#transform-constraints) 对象的所有约束组件，并应用于已处理的转换。
但是，用户可以选择手动配置应用的约束列表，只允许应用附加约束的子集。

目前，以下 MRTK UX 元素支持约束管理器：

- [边界控件](bounds-control.md)
- [对象操控器](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a>检查器属性和字段

约束管理器可以在两种模式下运行：

- 自动约束选择
- 手动约束选择

### <a name="auto-constraint-selection"></a>自动约束选择

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

约束管理器的默认模式（自动约束选择）将提供所有附加约束组件的列表，以及转到按钮和添加[约束按钮](#add-constraint-to-game-object)。 [](#go-to-component)

#### <a name="add-constraint-to-game-object"></a>向游戏对象添加约束

此按钮允许直接从约束管理器检查器添加约束组件。 项目的所有约束类型应在此处可见。 有关详细信息 [，请参阅](#transform-constraints) 转换约束。

#### <a name="go-to-component"></a>转到组件

此处列出了在对象上找到的所有约束，并包含" *转到组件"* 按钮。 此按钮将导致检查器滚动到所选约束组件，以便可以配置该组件。

### <a name="manual-constraint-selection"></a>手动约束选择

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

如果约束管理器设置为手动模式，则仅处理约束列表中链接的约束并应用于转换。 显示的列表将只显示用户选择的约束，以及转到用于删除或[](#go-to-component)添加条目的按钮或选项。
首次启用手动模式时，约束管理器将填充列表，所有可用组件都将作为选择附加约束组件的起点。

### <a name="remove-entry"></a>删除条目

这会从手动选择的列表中删除该条目。 请注意，此选项不会从游戏对象中删除约束组件。 始终需要手动删除约束组件，以确保不会意外中断引用此组件的其他组件。

### <a name="add-entry"></a>添加条目

"添加项"将打开一个下拉列表，其中显示尚未在手动列表中的所有可用约束组件。 通过单击组件将添加到手动约束选择的任何条目。

### <a name="add-new-constraint"></a>添加新约束

此选项将所选类型的组件添加到游戏对象，并且将新创建的约束组件添加到手动约束列表中。

## <a name="transform-constraints"></a>转换约束

约束可用于以某种方式限制操作。 例如，某些应用程序可能需要旋转，但也要求对象保持垂直。 在这种情况下，可以将 添加到 对象，并用于将旋转限制为 `RotationAxisConstraint` y 轴旋转。 MRTK 提供了许多约束，所有这些约束如下所述。

还可以定义新约束，并使用它们创建某些应用程序可能需要的唯一操作行为。 为此，请创建一个继承自 的脚本 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) ，并实现抽象 `ConstraintType` 属性和抽象 `ApplyConstraint` 方法。 向 对象添加新约束后，它应按定义的方式约束操作。 此新约束还应显示在约束管理器自动[选择中，](#auto-constraint-selection)[或在手动](#add-entry)模式下添加条目下拉列表。

MRTK 提供的所有约束共享以下属性：

#### <a name="hand-type"></a>手类型

指定约束是用于一手、两手还是两种操作。 由于此属性是一个标志，因此可以选中这两个选项。

- *一手*：如果选中，将在一手操作期间使用约束。
- *两手*：如果选中，将在两次手部操作期间使用约束。

#### <a name="proximity-type"></a>邻近类型

指定约束是用于近、远或两种操作。 由于此属性是一个标志，因此可以选中这两个选项。

- *Near*：如果选中，将在近操作期间使用约束。
- *远*：如果选中，将在远操作期间使用约束。

### <a name="faceuserconstraint"></a>FaceUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

当此约束附加到对象时，旋转将受到限制，以便对象始终面向用户。 这适用于板或面板。 的属性 `FaceUserConstraint` 如下所示：

#### <a name="face-away"></a>人脸离开

如果为 true，则对象与用户远离。

### <a name="fixeddistanceconstraint"></a>FixedDistanceConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

此约束修复了操作开始时被操作的对象与另一个对象转换之间的距离。 这适用于诸如修复从操作对象到头部转换的距离等行为。 的属性 `FixedDistanceConstraint` 如下所示：

#### <a name="constraint-transform"></a>约束转换

这是被操作的对象将具有固定距离的另一个转换。 默认为相机转换。

### <a name="fixedrotationtouserconstraint"></a>FixedRotationToUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

此约束修复了操作用户和被操作对象之间的相对旋转。 这适用于板或面板，因为它可确保操作对象始终向用户显示与操作开始时相同的人脸。 `FixedRotationToUserConstraint`没有任何唯一属性。

### <a name="fixedrotationtoworldconstraint"></a>FixedRotationToWorldConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

此约束修复了被操作对象的全局旋转。 当不应通过操作来设置旋转时，这非常有用。 `FixedRotationToWorldConstraint`没有任何唯一属性：

### <a name="maintainapparentsizeconstraint"></a>MaintainApparentSizeConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

当此约束附加到对象时，无论对象与用户有多远，它都将保持与用户相同的明显大小 (即，它将占用户视场的相同比例) 。 这可用于确保平板电脑或文本面板在操作时保持可读。 `MaintainApparentSizeConstraint`没有任何唯一属性：

### <a name="moveaxisconstraint"></a>MoveAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

此约束可用于修复可沿其移动被操作对象的轴。 这可用于在平面图面上或沿直线操作对象。 的属性 `MoveAxisConstraint` 如下所示：

#### <a name="constraint-on-movement"></a>移动约束

指定要阻止移动的轴。 默认情况下，这些轴是全局轴，而不是本地轴，但可以在下方进行更改。 由于此属性是标志，因此可以选择任意数目的选项。

- *X 轴*：如果选中，则沿 x 轴的移动受到限制。
- *Y 轴*：如果选中，则沿 y 轴的移动受到限制。
- *Z 轴*：如果选中，则沿 z 轴的移动受到限制。

#### <a name="use-local-space-for-constraint"></a>使用本地空间进行约束

如果为 true，则约束被操作对象的局部转换轴的相对约束。 默认值为 False。

### <a name="rotationaxisconstraint"></a>RotationAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

此约束可用于修复可旋转操作对象的轴。 这可用于保持操控对象垂直，但仍允许 y 轴旋转，例如。 的属性 `RotationAxisConstraint` 如下所示：

#### <a name="constraint-on-rotation"></a>旋转约束

指定阻止旋转的轴。 默认情况下，这些轴是全局性的，而不是本地的，但可以在下面更改。 因为此属性是一个标志，所以可以选择任意数量的选项。

- *Y 轴*：如果选中，则会约束围绕 Y 轴的旋转。
- *Z 轴*：如果选中，则对 Z 轴进行旋转。
- *X 轴*：如果选中，则会约束围绕 X 轴的旋转。

#### <a name="use-local-space-for-constraint"></a>使用本地空间作为约束

如果为 true，则将限制操作对象的本地转换轴。 默认值为 False。

### <a name="minmaxscaleconstraint"></a>MinMaxScaleConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

此约束允许为操作对象的小数位数设置最小值和最大值。 这对于防止用户缩放对象太小或太大非常有用。 的属性如下所示 `MinMaxScaleConstraint` ：

#### <a name="scale-minimum"></a>最小缩放

操作过程中的最小刻度值。

#### <a name="scale-maximum"></a>最大缩放

操作过程中的最大刻度值。

#### <a name="relative-to-initial-state"></a>相对于初始状态

如果为 true，则上述值将被解释为相对于对象初始刻度。 否则，它们将被解释为绝对缩放值。
