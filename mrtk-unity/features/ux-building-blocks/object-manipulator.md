---
title: 对象操控器
description: 如何在 MRTK 中使用对象操控器
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 对象操作，
ms.openlocfilehash: f9b644c1447d6776389e227bfe49c27f82a3cf31
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176656"
---
# <a name="object-manipulator"></a>对象操控器

![对象操控器](../images/manipulation-handler/MRTK_Manipulation_Main.png)

*ObjectManipulator* 是操作行为的新组件，以前在 *ManipulationHandler 中发现*。 对象操控器进行了许多改进和简化。 此组件将替换将弃用的操作处理程序。

*ObjectManipulator* 脚本使对象可移动、可缩放，并且使用一只或两只手可旋转。 可以将对象操控器配置为控制对象如何响应各种输入。 该脚本应处理大多数形式的交互，例如HoloLens 2手部、HoloLens 2射线、HoloLens 1 凝视和手势以及沉浸式头戴显示设备运动控制器输入。

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a>如何使用对象操控器

若要使用对象操控器，请首先将 `ObjectManipulator` 脚本组件添加到 GameObject。 请确保还将碰撞体添加到对象，使其与可抓取边界匹配。

若要使对象响应接近表达的手动输入，请 `NearInteractionGrabbable` 添加脚本。

通过将刚体组件添加到对象，为对象操控器启用物理行为。 在物理和碰撞中更详细地讨论了通过添加此组件 [*启用的物理行为*](#physics-and-collisions)。

此外，可以通过向 对象添加操作约束组件 [来限制](constraint-manager.md#transform-constraints) 操作。 这些是处理操作和以某种方式更改操作行为的特殊组件。

![在 Unity 编辑器中使用操作处理程序](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a>检查器属性和字段

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a>常规属性

#### <a name="host-transform"></a>主机转换

要操作的对象转换。 默认为组件的 对象。

#### <a name="manipulation-type"></a>操作类型

指定是否可以使用一只手或两只手操作对象。 由于此属性是一个标志，因此可以选中这两个选项。

- *一手*：选中后启用一手操作。
- *两手*：如果选中，则启用两个手部操作。

#### <a name="allow-far-manipulation"></a>允许远操作

指定是否可以使用与指针的远部交互完成操作。

### <a name="one-handed-manipulation-properties"></a>单手操作属性

#### <a name="one-hand-rotation-mode-near"></a>附近的单手旋转模式

指定在靠近一手抓取对象时对象的行为方式。 这些选项仅适用于铰接式手。

- *围绕对象中心旋转*：对象使用手部旋转，但围绕对象中心点旋转。 对象在旋转时似乎移动较少，但手和对象之间可能有断开连接感。 更适用于远地交互。
- *围绕抓取点旋转*：用手围绕滚动块和手指之间的抓取点旋转对象。 它应感觉就像对象被手持有一样。

#### <a name="one-hand-rotation-mode-far"></a>单手旋转模式远

指定在距离上用一只手抓取对象时对象的行为方式。 这些选项仅适用于铰接式手。

- *围绕对象中心旋转*：使用手部旋转旋转对象，但围绕对象中心点旋转。 可用于在对象旋转时不移动对象中心的距离进行检查。
- *旋转抓取点：* 使用手部旋转旋转对象，但围绕指针射线命中点旋转对象。 用于检查。

### <a name="two-handed-manipulation-properties"></a>两手操作属性

#### <a name="two-handed-manipulation-type"></a>两手操作类型

指定两个手动操作如何转换对象。 由于此属性是标志，因此可以选择任意数目的选项。

- *移动*：如果选中，则允许移动。
- *缩放*：如果选中，则允许缩放。
- *旋转*：如果选中，则允许旋转。

![操作处理程序](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a>约束

#### <a name="enable-constraints"></a>启用约束

此设置将启用链接的约束 [管理器](constraint-manager.md)。 转换更改由注册到所选约束管理器 [的约束处理](constraint-manager.md)。

#### <a name="constraint-manager"></a>约束管理器

下拉列表允许选择任何附加的约束 [管理器](constraint-manager.md)。 对象操控器可确保始终 [附加约束](constraint-manager.md) 管理器。
请注意，同一类型的多个组件将在 unity 中以同一名称显示。 为了更轻松地区分同一对象上的多个约束管理器，可用选项将显示有关所选约束管理器配置的提示 (手动或自动选择约束) 。

#### <a name="go-to-component"></a>转到组件

约束管理器选择附带"转到 *组件"* 按钮。 此按钮将导致检查器滚动到所选组件，以便可以配置该组件。

### <a name="physics"></a>物理

设置对象具有一个 RigidBody 组件时，才显示本部分中的属性。

#### <a name="release-behavior"></a>发布行为

指定操作对象在释放时应保留的物理属性。 由于此属性是一个标志，因此可以选中这两个选项。

- *保持速度*：释放对象时，如果选择此选项，它将保持其线性速度。
- *保持Angular* 速度：释放对象时，如果选择此选项，它将保持其角速度。

#### <a name="use-forces-for-near-manipulation"></a>使用强制进行近操作

执行近操作时，是否使用物理力来移动对象。 将此选项 *设置为 false* 会使对象感觉更直接地连接到用户手。 将此设置 *设置为 true* 将遵守对象的质和惯性，但可能感觉对象通过一个 spring 连接。 默认值为 false。

### <a name="smoothing"></a>平滑处理

#### <a name="smoothing-far"></a>远平滑

是否为远部交互启用与帧速率无关的平滑处理。 默认情况下启用远平滑。

#### <a name="smoothing-near"></a>平滑处理接近

是否为近交互启用了帧速率无关的平滑处理。 默认情况下禁用近平滑，因为效果可能被视为与手"断开连接"。

#### <a name="smoothing-active"></a>平滑处理活动

已过时，将在未来版本中删除。 应用程序应该使用 SmoothingFar、SmoothingNear 或这两者的组合。

#### <a name="move-lerp-time"></a>移动 lerp 时间

要应用于移动的平滑量。 平滑为 0 表示无平滑。 最大值表示不更改值。

#### <a name="rotate-lerp-time"></a>旋转 lerp 时间

要应用于旋转的平滑量。 平滑为 0 表示无平滑。 最大值表示不更改值。

#### <a name="scale-lerp-time"></a>缩放 lerp 时间

要应用于刻度的平滑量。 平滑0表示无平滑处理。 Max 值表示没有更改为值。

### <a name="manipulation-events"></a>操作事件

操作处理程序提供了以下事件：

- *OnManipulationStarted*：在操作开始时激发。
- *OnManipulationEnded*：操作结束时激发。
- *OnHoverStarted*：当右/控制器悬停可操作时，将会激发。
- *OnHoverEnded*：当手动/控制器取消悬停可操作时，将触发此操作。

操作的事件激发顺序是：

*OnHoverStarted*  -> *OnManipulationStarted*  -> *OnManipulationEnded*  -> *OnHoverEnded*

如果没有操作，则仍会获得具有以下触发顺序的悬停事件：

*OnHoverStarted*  -> *OnHoverEnded*

## <a name="physics-and-collisions"></a>物理和冲突

可以通过将刚体组件添加到与对象操控器相同的对象来启用物理学行为。 此功能不仅能启用上述 [版本行为](#release-behavior) 配置，还可以启用冲突。 如果没有刚体组件，则在操作过程中冲突不能正常运行：

- 操作对象和静态碰撞器之间的冲突 (即，具有碰撞器但没有刚体的对象) 不起作用，操作对象直接通过静态碰撞器进行不受影响。
- 操作对象与刚体之间的冲突 (例如 同时具有碰撞器和刚体) 的对象导致刚体具有冲突响应，但响应为 jumpy 和非自然。 对于操作的对象也不存在任何冲突响应。

添加刚体时，冲突应正常工作。

### <a name="without-rigidbody"></a>无刚体

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a>With 刚体

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a>池中弹性 (试验性) 

通过对象操控器操作对象时，可以使用池中弹性。 请注意， [池中弹性系统](../experimental/elastic-system.md) 仍处于试验状态。 若要启用池中弹性，请链接现有的池中弹性 manager 组件或通过按钮创建和链接新的池中弹性管理器 `Add Elastics Manager` 。

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a>另请参阅

- [边界控件](bounds-control.md)
- [约束管理器](constraint-manager.md)
- [迁移时限](../tools/migration-window.md)
- [池中弹性系统 (试验性) ](../experimental/elastic-system.md)
