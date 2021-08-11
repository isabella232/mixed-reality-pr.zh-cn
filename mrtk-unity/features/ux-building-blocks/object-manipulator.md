---
title: 对象操控器
description: 如何在 MRTK 中使用对象操控器
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，对象操作，
ms.openlocfilehash: 4c43a35e164d3e66e662afc927d28f84463e1586250e9847a2d88c219ba27f23
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191598"
---
# <a name="object-manipulator"></a>对象操控器

![对象操控器](../images/manipulation-handler/MRTK_Manipulation_Main.png)

*ObjectManipulator* 是之前在 *ManipulationHandler* 中找到的操作行为的新组件。 对象操控器进行了大量改进和简化。 此组件是操作处理程序的替代，将不推荐使用。

使用 *ObjectManipulator* 脚本，可以使用一种或两种指针来可移动、缩放和 rotatable 对象。 对象操控器可以配置为控制对象对各种输入的响应方式。 该脚本应该适用于大多数形式的交互操作，例如 HoloLens 2 清晰的手、HoloLens 2 的手片、HoloLens 1 注视和手势和沉浸式耳机运动控制器输入。

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a>如何使用对象操控器

若要使用对象操控器，请先将 `ObjectManipulator` 脚本组件添加到 GameObject。 请确保还将碰撞器添加到对象中，并将其 grabbable 边界匹配。

若要使对象响应接近的有表述的手写输入，请 `NearInteractionGrabbable` 同时添加脚本。

可以通过将刚体组件添加到对象来为对象操控器启用物理学行为。 [*物理和冲突*](#physics-and-collisions)中更详细地讨论了通过添加此组件启用的物理学行为。

同样，可以通过向对象添加 [操作约束组件](constraint-manager.md#transform-constraints) 来对操作进行约束。 这些是使用操作的特殊组件，并以某种方式更改操作行为。

![在 Unity 编辑器中使用操作处理程序](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a>检查器属性和字段

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a>常规属性

#### <a name="host-transform"></a>主机转换

将操作的对象转换。 默认为组件的对象。

#### <a name="manipulation-type"></a>操作类型

指定是否可以使用一个或两个手操作对象。 因为此属性是一个标志，所以这两个选项都可以选择。

- *One 右手*：如果选中，则启用一种操作。
- *两个右手* 操作：如果选中，则启用两个被处理的操作。

#### <a name="allow-far-manipulation"></a>允许远操作

指定是否可以使用远与指针交互来完成操作。

### <a name="one-handed-manipulation-properties"></a>一个右手操作属性

#### <a name="one-hand-rotation-mode-near"></a>一种手型旋转模式接近

指定在用一只手对对象进行处理时，对象的行为方式。 这些选项仅适用于明确表述的操作。

- *围绕对象中心旋转*：对象使用旋转旋转，但关于对象中心点旋转。 对象在旋转时看起来更少，但在这种情况下，手与对象之间可能会有很大的连接。 更适用于远距离交互。
- *旋转 "吸引点*"：围绕拇指和食指之间的抓住点旋转对象。 它应该感觉到该对象正由手来控制。

#### <a name="one-hand-rotation-mode-far"></a>目前有一种手型旋转模式

指定在通过一只手对对象进行抓取时，对象的行为方式。 这些选项仅适用于明确表述的操作。

- *围绕对象中心旋转*：使用手型旋转旋转对象，但关于对象中心点。 用于在不使用对象中心作为对象旋转时进行检查的距离。
- *旋转 "吸引点*"：使用手型旋转旋转对象，但关于指针射线点击点。 对于检查很有用。

### <a name="two-handed-manipulation-properties"></a>两个右手操作属性

#### <a name="two-handed-manipulation-type"></a>双向操作类型

指定两次操作如何转换对象。 因为此属性是一个标志，所以可以选择任意数量的选项。

- *移动*：如果选中，则允许移动。
- *缩放*：如果选中，则允许缩放。
- *旋转*：如果选中，则允许旋转。

![操作处理程序](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a>约束

#### <a name="enable-constraints"></a>启用约束

此设置将启用链接 [约束管理器](constraint-manager.md)。 转换更改将由注册到选定 [约束管理器](constraint-manager.md)的约束处理。

#### <a name="constraint-manager"></a>约束管理器

下拉列表允许选择任何附加的 [约束管理器](constraint-manager.md)。 对象操控器确保在任何时候都附加了 [约束管理器](constraint-manager.md) 。
请注意，同一类型的多个组件将在 unity 中显示为同一名称。 为了更容易区分同一个对象的多个约束管理器，可用选项将显示有关所选约束管理器的配置的提示 (手动或自动约束选择) 。

#### <a name="go-to-component"></a>中转到组件

约束管理器选项附带了 " *转到组件* " 按钮。 此按钮将使检查器滚动到所选组件，以便可以对其进行配置。

### <a name="physics"></a>物理

仅当对象具有刚体组件时，才会显示此部分中的设置。

#### <a name="release-behavior"></a>版本行为

指定操作对象在发布时应保留的物理属性。 因为此属性是一个标志，所以这两个选项都可以选择。

- *保持速度*：释放对象时，如果选择此选项，它将保持其线性速度。
- *保持 Angular 速度*：释放对象时，如果选择此选项，它将保持其角度速度。

#### <a name="use-forces-for-near-manipulation"></a>使用强制执行接近操作

当执行接近操作时是否使用物理学强制移动对象。 如果将此选项设置为 *false* ，则对象将感到更加直接连接到用户。 将此值设置为 *true* 将服从对象的质量和惯性，但可能感觉对象通过弹簧进行连接。 默认值为 false。

### <a name="smoothing"></a>平滑处理

#### <a name="smoothing-far"></a>向上平滑

对远交互是否启用帧速率独立平滑处理。 默认情况下，将启用迄今为止的平滑处理。

#### <a name="smoothing-near"></a>近乎平滑

是否为近交互启用帧速率独立平滑处理。 默认情况下禁用近乎平滑处理，因为这种效果可能会被视为 "断开连接"。

#### <a name="smoothing-active"></a>平滑活动

已过时，并将在将来的版本中删除。 应用程序应使用 SmoothingFar、SmoothingNear 或二者的组合。

#### <a name="move-lerp-time"></a>移动 lerp 时间

要应用于移动的平滑量。 平滑0表示无平滑处理。 Max 值表示没有更改为值。

#### <a name="rotate-lerp-time"></a>旋转 lerp 时间

要应用于旋转的平滑量。 平滑0表示无平滑处理。 Max 值表示没有更改为值。

#### <a name="scale-lerp-time"></a>缩放 lerp 时间

要应用于刻度的平滑量。 平滑为 0 表示无平滑。 最大值表示不更改值。

### <a name="manipulation-events"></a>操作事件

操作处理程序提供以下事件：

- *OnManipulationStarted：* 在操作开始时触发。
- *OnManipulationEnded：* 操作结束时触发。
- *OnHoverStarted：* 当手/控制器将可操作对象悬停在近或远时触发。
- *OnHoverEnded：* 当手/控制器取消悬停可操作对象（近或远）时触发。

操作的事件发后顺序为：

*OnHoverStarted*  -> *OnManipulationStarted*  -> *OnManipulationEnded*  -> *OnHoverEnded*

如果没有操作，你仍将获得具有以下起火顺序的悬停事件：

*OnHoverStarted*  -> *OnHoverEnded*

## <a name="physics-and-collisions"></a>物理和碰撞

通过将刚体组件添加到对象操控器相同的对象中，可以启用物理行为。 这不仅支持上述 [发布行为的配置](#release-behavior) ，还支持冲突。 如果没有刚体组件，则操作期间冲突的行为不正确：

- 受操作对象与静态碰撞体之间的冲突 (即具有碰撞体但没有刚体的对象) 不起作用，被操作的对象将直接通过静态碰撞体而不受影响。
- 被操控对象与刚体与刚体 (冲突，即 具有碰撞体和刚体对象的对象) 使刚体具有碰撞响应，但响应是跳转的且不自然。 操作对象上也没有冲突响应。

添加刚体时，冲突应正常工作。

### <a name="without-rigidbody"></a>无刚体

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a>使用刚体

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a>弹性 (实验) 

通过对象操控器操作对象时，可以使用弹性。 请注意， [弹性系统](../experimental/elastic-system.md) 仍处于试验状态。 若要启用弹性，请链接现有弹性管理器组件，或通过 按钮创建并链接新的弹性 `Add Elastics Manager` 管理器。

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a>另请参阅

- [边界控制](bounds-control.md)
- [约束管理器](constraint-manager.md)
- [迁移时限](../tools/migration-window.md)
- [弹性系统 (实验) ](../experimental/elastic-system.md)
