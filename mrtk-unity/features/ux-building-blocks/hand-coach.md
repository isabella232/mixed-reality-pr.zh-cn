---
title: README_HandCoach
description: 手部教练的说明和示例。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 8b4069f25692c4058c912ccd06ae678d67882fcd
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489267"
---
# <a name="hand-coach"></a>手部指导

![手部指导菜单](../images/hand-coach/MRTK_UX_HandCoach_Main.jpg)

手部训练是 3D 建模手，当系统未检测到用户的手时，会触发手部训练。 这是作为"教学"组件实现的，可帮助在未教授手势时指导用户。 如果用户有一段时间没有完成指定的手势，手将循环并出现延迟。 手部指导可用于表示按下按钮或选取全息影像。

当前交互模型表示各种手势控件，例如滚动、远点选择和近点击。 下面是现有手部教练示例的完整列表：

- 近点击 – 用于按钮或关闭可交互对象
- 远选 – 用于远离的对象
- 移动 – 用于在空间中移动全息影像
- 旋转 – 用于显示如何旋转全息影像或对象
- 缩放 - 用于显示如何操作放大或缩小全息影像
- 手部翻转 - 用于打开 UI 启动面板或手部菜单
- "开箱即用"– 用于在开箱即用体验中实现鸟鸟时刻。 另一个建议可能是启动 UI 启动面板
- 滚动 – 用于滚动列表或长文档

## <a name="example-scene"></a>示例场景

可以在 **HandCoachExample** 场景下找到示例 [：MixedRealityToolkit.Examples/Experimental/HandCoach/Scene](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach/Scenes)

## <a name="hand-3d-assets"></a>手动三维资产

可以在以下资源中找到资产： [MixedRealityToolkit/实验/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach)

## <a name="quality"></a>质量

如果注意到 skinned 网格上的扭曲，需要确保项目使用的是正确的联接量。
请参阅 Unity 的编辑 > 项目设置 > Quality > 其他 > Blend 权重。 请确保选择 "4 骨骼" 以查看平滑联接。
![项目设置](../images/hand-coach/MRTK_ProjectSettings.png)

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

- **重复** 此属性控制在最小或最大计时器通过时提示动画播放次数。 然后，提示将隐藏并再次等待延迟。

- **AutoActivate** 当此布尔值设置为 true 时，当脚本的 GameObject 在层次结构中处于活动状态并启用脚本时，提示将自动通过计时器逻辑运行。 只有打算通过代码手动控制提示外观和消失时，才应设置为 false。

- **AnimationState** 提示处于活动状态时应播放的动画状态的名称。 如果在 OnEnable 期间选中了 AutoActivate， () StartHintLoop (调用 StartHintLoop 函数之前，必须设置) 。

#### <a name="controlling-interactionhint-via-script"></a>通过脚本控制 InteractionHint

- **StartHintLoop** 如果 AutoActivate 标志设置为 true，此函数将启动显示/隐藏循环，否则启动 OnEnable。
- **StopHintLoop** 如果当前未播放，此函数将调用淡出动画状态，然后停用显示/隐藏循环，并设置层次结构中的手部不活动。
- **AnimationState** 此字符串确定在循环期间播放的动画状态。 可以更改此字符串以更改播放的状态，但在调用 StopHintLoop 后必须这样做，并且必须在更改状态后再次调用 StartHintLoop。
- **CustomShouldHideVisuals** 可以使用自己的函数对此进行设置，当想要隐藏手部视觉对象时，应返回 true (请记住 MinMaxTimer，特别是 max 参数) 

#### <a name="custom-animation-considerations"></a>自定义动画注意事项

淡入淡入淡出默认为 0.5 秒，因此，为与钻台一起创建的任何自定义动画应至少为 1.5 秒，以便传达任何有意义的信息

提供的默认淡入和淡出状态Fade_In，Fade_Out通过更改第二个关键帧的时间戳来设置淡入淡出长度来调整其淡入和淡出状态。

动画器和脚本的设置方式应使设置尽可能简单。 若要添加新的动画状态，只需导入 fbx，确保使用不同的名称设置动画名称，然后将动画拖到 animator 中。

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

在自定义脚本中，在希望手部工具跟随 TrackingObject 时调用"跟踪 () "，然后在希望手部工具开始向 TargetObject 移动时调用 MoveToTargetPosition () 。

#### <a name="controlling-movetotarget-via-animations"></a>通过动画控制 MoveToTarget

在需要移动的动画中，设置两个事件：一个事件调用 Follow () ，另一个事件调用 MoveToTargetPosition () 。 应在第一个关键帧上设置"关注"，因为它会导致手部工具跟随 TrackingObject。 应在希望设备开始移动到目标的关键帧上设置 MoveToTargetPosition。 这是脚本功能在提供的预制组件中的使用方式。

### <a name="rotatearoundpoint"></a>Rotate按UndPoint

RotateAroundPoint.cs 脚本提供了在一段时间围绕透视点旋转手提示的功能。

#### <a name="how-to-set-up-rotatearoundpoint"></a>如何设置 RotateAroundPoint

提供的预制件"RotatingHandCoachRoot_L.prefab"和"RotatingHandCoachRoot_R.prefab"在层次结构中包含 Rotate且undPoint。 如果要在你自己的设置中使用此脚本，则需要将脚本放在根 gameobject 上，其中包含用于你的钻器的动画器。

#### <a name="inspector-properties"></a>检查器属性

- **CenteredParent** 将此选项设置为希望设备四处透视的父对象。
- **InverseParent** 将此选项与父级一起设置为"反向旋转"到"居中""参数"，以保持手部方向不变。 一般情况下，这将是其上具有 InteractionHint 脚本的父对象。
- **PivotPosition** 将此选项设置为希望提示开始移动的点。
- **持续时间** 围绕 CenteredParent 旋转 (需要) 秒。
- **AnimationCurve** 这默认为线性曲线，但可以更改曲线，在启动和停止运动路径时提供缓动。
- **RotationVector** 沿每个轴旋转的度数。

#### <a name="controlling-rotatearoundpoint-via-script"></a>通过脚本控制 RotateAroundPoint

在自定义脚本中，当你希望在 CenteredParent 上开始旋转时，请调用 RotateToTarget () 。 如果希望将位置重置为原始 PivotPosition，请调用 ResetAndDeterminePivot () 。

#### <a name="controlling-rotatearoundpoint-via-animations"></a>通过动画控制 RotateAroundPoint

在需要移动的动画中，设置两个事件：一个事件调用 ResetAndDeterminePivot () ，另一个事件调用 RotateToTarget () 。 应在第一个关键帧上设置 ResetAndDeterminePivot，因为它会导致手型装置重置为 PivotPosition。 应在你希望远程测试机组在 CenteredParent 上开始旋转的关键帧上设置 RotateToTarget。 这就是在提供的 prototyping 中使用脚本功能的方式。
