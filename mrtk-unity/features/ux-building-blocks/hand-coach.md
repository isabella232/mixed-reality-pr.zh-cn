---
title: 手部指导
description: 手动指导的说明和示例。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 3e5a56f7498288e79963acea6fca223421fee2607004a9a2bae639f81441e0d9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209018"
---
# <a name="hand-coach"></a>手部指导

![手动指导菜单](../images/hand-coach/MRTK_UX_HandCoach_Main.jpg)

手动指导是在系统未检测到用户的手时触发的3D 建模手。 这是作为 "教学" 组件实现的，该组件可帮助引导用户在未教授手势时进行引导。 如果用户未在某个时间段内完成指定的手势，则会循环一段时间。 手动指导可用于表示按下某个按钮或选择一个全息影像。

当前交互模型表示各种手势控件，例如滚动、远选和点击显示。 下面是现有手动指导示例的完整列表：

- 点击点击–用于按钮或关闭种不可交互对象
- 选择–用于远离远处的对象
- 移动–用于在空间中移动全息图
- 旋转–用于演示如何旋转全息影像或对象
- 规模-用于显示如何操作更大或更小的全息影像
- 手动翻转–用于引入 UI 的 "开始" 面板或手菜单
- 掌上–在全新体验中用于 hummingbird。 另一个建议是打开 UI 开始面板
- 滚动-用于滚动列表或长文档

## <a name="example-scene"></a>示例场景

可在以下主题中找到 **HandCoachExample** 场景中的示例： [MixedRealityToolkit/实验/HandCoach/场景](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach/Scenes)

## <a name="hand-3d-assets"></a>手动三维资产

可以在以下资源中找到资产： [MixedRealityToolkit/实验/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach)

## <a name="quality"></a>质量

如果注意到 skinned 网格上的扭曲，需要确保项目使用的是正确的联接量。
中转到 Unity 的编辑 > Project 设置 > 质量 > 其他 > 混合权重。 请确保选择 "4 骨骼" 以查看平滑联接。
![Project将](../images/hand-coach/MRTK_ProjectSettings.png)

## <a name="scripts"></a>脚本

### <a name="interaction-hint"></a>交互提示

该 `InteractionHint.cs` 脚本提供了用于触发动画的包装功能，并为手型工作机组淡化。

#### <a name="how-to-set-up-an-interaction-hint"></a>如何设置交互提示

若要设置交互提示，建议使用提供的 prototyping StaticHandCoachRoot_L "prefab" 和 StaticHandCoachRoot_R "prefab"。 此 prefab 包含 InteractionHint 脚本和手写工作装置以及适当的层次结构，以确保所提供的提示动画按预期方式工作。
否则，你将需要使用 animator 将该脚本放在 gameObject 的父级别上。

#### <a name="inspector-properties"></a>检查器属性

- **HideIfHandTracked** 此布尔值指定在跟踪用户的手时是否应使用手动跟踪状态隐藏视觉对象。 如果将此属性设置为 false，则只使用脚本属性 "customShouldHideVisuals" 来确定是否隐藏提示。

- **MinDelay** 此属性指定显示视觉对象的最小延迟。 默认情况下，如果未跟踪用户的手，则手形的视觉对象将显示在这几秒钟后。

- **MaxDelay** 此属性指定显示视觉对象的最大延迟。 默认情况下，即使正在跟踪用户的手，该手形的视觉对象也会在数秒后出现。

- **UseMaxTimer** 如果将此布尔值设置为 "false"，则它将禁用最大计时器，并只允许在用户退出查看时显示手形提示，或自定义条件返回 false。

- **重复** 此属性控制在达到最小或最大计时器时，提示动画的播放次数。 然后，提示将隐藏并再次等待延迟。

- **AutoActivate** 如果将此布尔值设置为 true，则当脚本的 GameObject 在层次结构中处于活动状态且该脚本已启用时，提示将自动通过计时器逻辑运行。 如果要通过代码手动控制提示外观和消失，则此值应设置为 false。

- **AnimationState** 提示处于活动状态时应播放的动画状态的名称。 如果) 检查 AutoActivate，则必须在 OnEnable 期间 (调用 StartHintLoop () 函数之前设置此设置。

#### <a name="controlling-interactionhint-via-script"></a>通过脚本控制 InteractionHint

- **StartHintLoop** 如果 AutoActivate 标志设置为 true，则此函数将启动 "显示/隐藏" 循环，否则会启动 OnEnable。
- **StopHintLoop** 如果当前未播放，此函数将调用淡出动画状态，然后停用显示/隐藏循环，并在层次结构中设置不活动的手动装置。
- **AnimationState** 此字符串确定循环中播放的动画状态。 你可以更改此字符串来更改播放的状态，但必须在调用 StopHintLoop 之后执行此操作，并且必须在更改状态后再次调用 StartHintLoop。
- **CustomShouldHideVisuals** 你可以将此设置为你自己的函数，当你想要隐藏手视觉对象时，它应返回 true， (记住 MinMaxTimer，尤其是最大参数) 

#### <a name="custom-animation-considerations"></a>自定义动画注意事项

淡化的默认值为0.5 秒，因此，为与 rig 一起使用而创建的任何自定义动画应最少1.5 秒，以便传达任何有意义的信息

提供的默认淡入和淡出状态、Fade_In 和 Fade_Out 可以通过更改第二个关键帧的时间戳来进行调整，以设置淡化长度。

Animator 和脚本的设置方式使安装尽可能简单。 若要添加新的动画状态，只需导入 fbx，确保使用不同的名称设置动画名称，然后将动画拖到 animator 中。

### <a name="movetotarget"></a>MoveToTarget

MoveToTarget 脚本提供将手形提示从跟踪位置移动到目标位置的功能。

#### <a name="how-to-set-up-movetotarget"></a>如何设置 MoveToTarget

提供的 prototyping MovingHandCoachRoot_L "prefab" 和 MovingHandCoachRoot_R "prefab" 在其层次结构中包含 MoveToTarget。 如果要在自己的设置中使用此脚本，则需要将其放在包含远程测试机组 Animator 的根 gameobject 上。

#### <a name="inspector-properties"></a>检查器属性

- **TrackingObject** 将此设置为你希望远程测试在开始运动之前应遵循的对象。 建议创建一个空的 GameObject，并将其移至特定位置以帮助你确定跟踪。
- **TargetObject** 将此设置为你希望远程测试在其运动期间移动到的对象。 建议创建一个空的 GameObject，并将其移至特定位置以帮助你确定跟踪。
- **RootObject** 将此项设置为跟踪和目标对象之间的共享父级，以便可以正确计算相对位置。 包含的 prefab 在其层次结构中同时具有跟踪和目标对象，但你可以将目标对象设置为 prefab 外的 gameObject，并将根对象更改为共享父级。
- **持续时间** 在几秒内从 TrackingObject 移动到 TargetObject 所需的时间量 () 。
- **TargetOffset** 用于获取 GameObject 到达适当目标位置的可调偏移量。 如果动画中的动画包含位置偏移量，则此方法非常有用。
- **AnimationCurve** 这是默认情况下的线性曲线，但您可以在启动和停止运动路径时更改曲线以提供缓动。

#### <a name="controlling-movetotarget-via-script"></a>通过脚本控制 MoveToTarget

在自定义脚本中，调用以下 () ，同时想要在 TrackingObject 时使用该手型装置，然后调用 MoveToTargetPosition () ，以使其开始将其移动到 TargetObject。

#### <a name="controlling-movetotarget-via-animations"></a>通过动画控制 MoveToTarget

在需要移动的动画中，设置两个事件：一个事件调用追随 () ，另一个事件调用 MoveToTargetPosition () 。 应在第一个关键帧上设置 "跟随"，因为它会导致手型装置按照 TrackingObject。 应在希望远程测试机组开始移动到目标的关键帧上设置 MoveToTargetPosition。 这就是在提供的 prototyping 中使用脚本功能的方式。

### <a name="rotatearoundpoint"></a>RotateAroundPoint

RotateAroundPoint 脚本可提供一段时间来围绕一个数据透视点旋转手形提示。

#### <a name="how-to-set-up-rotatearoundpoint"></a>如何设置 RotateAroundPoint

提供的 prototyping RotatingHandCoachRoot_L "prefab" 和 RotatingHandCoachRoot_R "prefab" 在其层次结构中包含 RotateAroundPoint。 如果要在自己的设置中使用此脚本，则需要将其放在包含远程测试机组 Animator 的根 gameobject 上。

#### <a name="inspector-properties"></a>检查器属性

- **CenteredParent** 将此项设置为你希望远程测试机组绕过的父对象。
- **InverseParent** 将此项设置为父项，以将其反向旋转到 centeredParent，以使手写方向相同。 通常，这是包含 InteractionHint 脚本的父对象。
- **PivotPosition** 将此设置为想要在其中开始移动的点。
- **持续时间**) 绕 CenteredParent 旋转所需的时间量 (，以秒为单位。
- **AnimationCurve** 这是默认情况下的线性曲线，但您可以在启动和停止运动路径时更改曲线以提供缓动。
- **RotationVector** 沿每个轴旋转的度数。

#### <a name="controlling-rotatearoundpoint-via-script"></a>通过脚本控制 RotateAroundPoint

在自定义脚本中，当你希望在 CenteredParent 上开始旋转时，请调用 RotateToTarget () 。 如果希望将位置重置为原始 PivotPosition，请调用 ResetAndDeterminePivot () 。

#### <a name="controlling-rotatearoundpoint-via-animations"></a>通过动画控制 RotateAroundPoint

在需要移动的动画中，设置两个事件：一个事件调用 ResetAndDeterminePivot () ，另一个事件调用 RotateToTarget () 。 应在第一个关键帧上设置 ResetAndDeterminePivot，因为它会导致手型装置重置为 PivotPosition。 应在你希望远程测试机组在 CenteredParent 上开始旋转的关键帧上设置 RotateToTarget。 这就是在提供的 prototyping 中使用脚本功能的方式。
