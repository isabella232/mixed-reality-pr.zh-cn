---
title: 控制器、指针和焦点
description: 与控制器、指针和焦点交互。
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 指针， 控制器
ms.openlocfilehash: b3e4438c1318abbc60606bcbca42854edae28167
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121615"
---
# <a name="controllers-pointers-and-focus"></a>控制器、指针和焦点

控制器、指针和焦点是更高级别的概念，基于核心输入系统建立的基础。 它们共同提供了与场景中的对象进行交互的很大一部分机制。

## <a name="controllers"></a>Controllers

控制器是物理控制器的表示形式 (6 度自由、手部表达等) 。 它们由设备管理器创建，负责与相应的基础系统通信，并将该数据转换为 MRTK 形状的数据和事件。a

例如，在 Windows Mixed Reality 平台上， 是一个控制器，负责与基础 Windows 手部跟踪 API 交互，以获取有关手部、姿势和其他属性 [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) 的信息[](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)。 它负责将这些数据转换为相关的 MRTK 事件 (例如，通过调用 RaisePoseInputChanged 或 RaiseHandJointsUpdated) 并更新其自己的内部状态，以便对 的查询返回正确的数据。 [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A)

通常，控制器的生命周期将涉及：

1. 设备管理器在检测到新源时创建控制器 (例如，设备管理器检测并开始跟踪手部) 。

2. 在控制器的 Update () 循环中，它会调用其基础 API 系统。

3. 在同一更新循环中，它通过直接调用核心输入系统本身来引发输入事件更改 (例如，引发 HandMeshUpdated 或 HandJointsUpdated) 。

## <a name="pointers-and-focus"></a>指针和焦点

指针用于与游戏对象交互。 本部分介绍如何创建指针、如何更新指针，以及如何确定 (焦点) 对象。 它还将介绍存在的不同类型的指针及其处于活动状态的方案。

### <a name="pointer-categories"></a>指针类别

指针通常分为以下类别之一：

- **远指针**

  这些类型的指针用于与远离用户的对象交互 (被定义为"不靠近") 。 这些类型的指针通常可强制转换行，这些线条可以深入到世界，并允许用户与它们不紧接的对象进行交互和操作。

- **近指针**

  这些类型的指针用于与距离用户足够近的对象进行交互，以便进行抓取、触摸和操作。 通常，这些类型的指针通过查找附近邻近区域 (中的对象来与对象交互：在短距离处进行光线投射、执行球状强制转换以查找邻近对象，或枚举被视为可抓取/可触摸对象) 。

- **Teleport 指针**

  这些类型的指针会插入远程传送系统，以处理将用户移动到指针所针对的位置。

## <a name="pointer-mediation"></a>指针中介

例如，由于单个控制器可以有多个指针 (，因此可同时具有近部和远部交互指针) 因此存在一个组件，负责对哪个指针应处于活动状态进行媒体处理。

例如，当用户手接近可按下按钮时， [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 应停止显示，并且 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) 应参与。

这由 处理，它负责根据所有指针的状态确定哪些指针 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) 处于活动状态。 此操作的主要功能之一是，当近指针接近对象时禁用远指针 (请参阅 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator)) 。

通过更改指针配置文件上的 属性，可以提供指针中介 [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) 的备用实现。

### <a name="how-to-disable-pointers"></a>如何禁用指针

由于指针转换器运行每个帧，因此它最终控制所有指针的活动/非活动状态。 因此，如果在代码中设置指针的 IsInteractionEnabled 属性，它将被每个帧的指针转换器覆盖。 相反，可以指定 来控制 [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 指针是应打开还是关闭。 请注意，只有在 MRTK 中使用的是默认 和 时 [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ，这才能正常工作。

#### <a name="example-disable-hand-rays-in-mrtk"></a>示例：禁用 MRTK 中的手部射线

以下代码将关闭 MRTK 中的手部射线：

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

以下代码将手部射线返回到 MRTK 中的默认行为：

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

以下代码将强制手部射线打开，而不考虑是否靠近可抓取项：

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

有关 [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) 更多 [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) 示例，请参阅 和 。

### <a name="focusprovider"></a>FocusProvider

是一个工作队列，负责访问所有指针的列表，并找出每个指针的聚焦 [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) 对象。

在每个 `Update()` 调用中，这将：

1. 通过光线广播和按指针本身配置执行命中检测来更新所有指针 (例如，球体指针可以指定 SphereOverlap raycastMode，因此 FocusProvider 将执行基于球体的碰撞) 

2. 根据每个指针更新焦点对象 (即，如果对象获得焦点，它还将触发指向这些对象的事件，如果对象失去焦点，则触发焦点丢失等) 。

### <a name="pointer-configuration-and-lifecycle"></a>指针配置和生命周期

[可以在输入系统配置文件的](../features/input/pointers.md)*指针* 部分配置指针。

指针的生存期通常如下所示：

1. 设备管理器将检测控制器是否存在。 然后，此设备管理器会通过调用 创建与控制器关联的指针集 [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) 。

2. FocusProvider 在其 Update () 循环中，将循环遍历所有有效的指针，并执行关联的光线广播或命中检测逻辑。 这用于确定由每个特定指针聚焦的对象。

    - 由于可以同时具有多个活动的输入源 (例如，两只手处于活动状态) ，因此还可以同时具有多个具有焦点的对象。

3. 设备管理器发现控制器源丢失后，会关闭与丢失的控制器关联的指针。