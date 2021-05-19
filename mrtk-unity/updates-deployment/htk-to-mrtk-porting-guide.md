---
title: HTK 到 MRTK 移植指南
description: 从 HoloLens Toolkit (HTK) 迁移到混合现实工具包 (MRTK) 。
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， HTK，
ms.openlocfilehash: fbcb2863c894a4e4c1529e19112b33712f69e99f
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143767"
---
# <a name="porting-guide"></a>移植指南

帮助你从 HoloLens Toolkit (HTK) 迁移到混合现实工具包 (MRTK) 。

## <a name="controller-and-hand-input"></a>控制器和手动输入

### <a name="setup-and-configuration"></a>安装和配置

|         方法                  | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 类型                      | 按钮的特定事件，相关时具有输入类型信息。 | 基于操作/手势的输入，通过事件传递。 |
| 设置                     | 将 InputManager 放在场景中。 | 在配置文件中启用输入 [系统，](../configuration/mixed-reality-configuration-guide.md) 并指定具体的输入系统类型。 |
| 配置             | 在检查器中针对场景中的每个脚本配置。 | 通过混合现实输入系统配置文件及其相关配置文件进行配置，如下所示。 |

相关配置文件：

* 混合现实控制器映射配置文件
* 混合现实控制器可视化配置文件
* 混合现实手势配置文件
* 混合现实输入操作配置文件
* 混合现实输入操作规则配置文件
* 混合现实指针配置文件

在场景中的主相机对象上修改了 "[注视提供程序](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider)" 设置。

平台支持组件 (例如，必须将 Windows Mixed Reality Device Manager) 添加到相应服务的数据访问接口。

### <a name="interface-and-event-mappings"></a>接口和事件映射

有些事件不再具有唯一事件，并且现在包含 [MixedRealityInputAction](../features/input/input-actions.md)。 这些操作在输入操作配置文件中指定，并映射到控制器映射配置文件中的特定控制器和平台。 这样 `OnInputDown` 的事件现在应检查 MixedRealityInputAction 类型。

相关输入系统：

* [输入概述](../features/input/overview.md)
* [输入事件数](../features/input/input-events.md)
* [输入指针](../features/input/pointers.md)

| HTK 2017 |  MRTK v2  | 操作映射 |
|----------|-----------|----------------|
| `IControllerInputHandler` | [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 映射到触摸板或操纵杆 |
| `IControllerTouchpadHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | 映射到触摸板 |
| `IFocusable` | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) | |
| `IGamePadHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IHoldHandler` | [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | 映射到笔势配置文件中的保留 |
| `IInputClickHandler` | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) |
| `IInputHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | 映射到控制器的按钮或点击 |
| `IManipulationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | 映射到笔势配置文件中的操作 |
| `INavigationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | 映射到笔势配置文件中的导航 |
| `IPointerSpecificFocusable` | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) | |
| `ISelectHandler` | [`IMixedRealityInputHandler<float>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 映射到触发器位置 |
| `ISourcePositionHandler` | [`IMixedRealityInputHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) 或 [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 映射到指针位置或手柄位置 |
| `ISourceRotationHandler` | [`IMixedRealityInputHandler<Quaternion>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) 或 [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 映射到指针位置或手柄位置 |
| `ISourceStateHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IXboxControllerHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) 和 [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | 映射到各种控制器按钮和 thumbsticks |

## <a name="camera"></a>照相机

|        方法                    | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 设置                     | 删除 MainCamera，将 MixedRealityCameraParent/MixedRealityCamera/HoloLensCamera prefab 添加到场景， **或** 使用混合现实工具包 > 配置 > 应用混合现实场景设置菜单项。 | 通过混合现实工具包在 MixedRealityPlayspace 下 MainCamera 父级 > 添加到场景并配置 .。。 |
| 配置             | 照相机设置配置在 prefab 实例上执行。 | [混合现实照相机配置文件](xref:Microsoft.MixedReality.Toolkit.MixedRealityCameraProfile)中配置的照相机设置。 |

## <a name="speech"></a>语音

### <a name="keyword-recognition"></a>关键字识别

|         方法                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 设置                     | 将 SpeechInputSource 添加到场景中。 | 关键字服务 (例如，必须将 Windows Speech 输入管理器) 添加到输入系统的数据访问接口。 |
| 配置             | 可识别的关键字在 SpeechInputSource 的检查器中配置。 | 关键字在 [混合现实语音命令配置文件](../features/input/speech.md)中进行配置。 |
| 事件处理程序            | `ISpeechHandler` | [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

### <a name="dictation"></a>听写

|         方法                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 设置                     | 将 DictationInputManager 添加到场景中。 | 听写支持需要服务 (例如，将 Windows 听写输入管理器) 添加到输入系统的数据访问接口。 |
| 事件处理程序            | `IDictationHandler` | `IMixedRealityDictationHandler`[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

## <a name="spatial-awareness--mapping"></a>空间感知/映射

### <a name="mesh"></a>网格

|         方法                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 设置                     | 将 SpatialMapping 预制添加到场景中。 | 在配置文件中启用空间感知系统，并添加空间观察 (，例如Windows Mixed Reality网格观察) 空间感知系统的数据提供程序。 |
| 配置             | 在检查器中配置场景实例。 | 配置每个空间观察器配置文件上的设置。 |

### <a name="planes"></a>飞机

|         方法                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 设置                     | 使用 `SurfaceMeshesToPlanes` 脚本。 | 尚未实现。 |

### <a name="spatial-understanding"></a>空间理解

|       方法                      | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 设置                     | 将 SpatialUnderunder 预制添加到场景中。 | 尚未实现。 |
| 配置             | 在检查器中配置场景实例。 | 尚未实现。 |

## <a name="boundary"></a>边界

|         方法                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 设置                     | 将 `BoundaryManager` 脚本添加到场景中。 | 在配置文件中启用边界系统。 |
| 配置             | 在检查器中配置场景实例。 | 配置边界可视化配置文件中的设置。 |

## <a name="sharing"></a>共享

|             方法               | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| 设置                     | 共享服务：将共享 prefab 添加到场景中。 UNet：使用 SharingWithUNET 示例。 | 正在进行 |
| 配置             | 在检查器中配置场景实例。 | 正在进行 |

## <a name="ux"></a>HP-UX

|         方法                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Button                     | [种不可交互对象](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Button](../features/ux-building-blocks/Button.md) |
| 可交互                     | [种不可交互对象](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [可交互](../features/ux-building-blocks/Interactable.md) |
| 边界框             | [边界框](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [边界框](../features/ux-building-blocks/bounding-box.md) |
| 应用栏             | [应用栏](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [应用栏](../features/ux-building-blocks/app-bar.md) |
| 一次操作 (Grb 并移动)    | [HandDraggable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/HandDraggable.cs) | [操作处理程序](../features/ux-building-blocks/manipulation-handler.md) |
| 两次操作 (获取/移动/旋转/缩放)              | [TwoHandManipulatable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/TwoHandManipulatable.cs) | [操作处理程序](../features/ux-building-blocks/manipulation-handler.md) |
| 键盘             | [键盘 prefab]() | [系统键盘](../features/ux-building-blocks/system-keyboard.md) |
| 工具提示             | [工具提示](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_TooltipExample.md) | [工具提示](../features/ux-building-blocks/tooltip.md) |
| 对象集合             | [对象集合](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md) | [对象集合](../features/ux-building-blocks/object-collection.md) |
| 解算器             | [解算器](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Readme/README_SolverSystem.md) | [解算器](../features/ux-building-blocks/solvers/solver.md) |

## <a name="utilities"></a>实用程序

某些实用工具已与求解器系统协调为重复项。 如果缺少所需的任何脚本，请提交问题。

| HTK 2017 |  MRTK v2  |
|----------|-----------|
| 广告 牌 | [`Billboard`](xref:Microsoft.MixedReality.Toolkit.UI.Billboard) |
| Tagalong | [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) 或 [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) [求解器](../features/ux-building-blocks/solvers/Solver.md) |
| FixedAngularSize | [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize)[求解器](../features/ux-building-blocks/solvers/solver.md) |
| FpsDisplay | [Configuration Profile (](../features/diagnostics/diagnostics-system-getting-started.md) 中的诊断系统)  |
| NearFade | 内置于混合 [现实工具包标准着色器](../features/rendering/mrtk-standard-shader.md) |
