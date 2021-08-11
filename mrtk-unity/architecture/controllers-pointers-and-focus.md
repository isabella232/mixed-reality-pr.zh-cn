---
title: 控制器、指针和焦点
description: 与控制器、指针和焦点交互。
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，指针，控制器
ms.openlocfilehash: 00bc0641182c566b045f959dfa361e1311b3cd224fc998f154010ad2996679ae
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196287"
---
# <a name="controllers-pointers-and-focus"></a>控制器、指针和焦点

控制器、指针和焦点是基于核心输入系统所建立的基础构建的高级概念。 它们共同提供了用于与场景中的对象进行交互的一大部分机制。

## <a name="controllers"></a>Controllers

控制器是物理控制器的表示形式， (6 度的自由、明确表述的) 等。 它们由设备管理器创建，负责与相应的基础系统进行通信，并将该数据转换为 MRTK 的数据和事件。

例如，在 Windows Mixed Reality 平台上， [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) 是负责与基础 Windows[手动跟踪 api](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)建立交互的控制器，以获取有关该手型的接头、姿势和其他属性的信息。 它负责将此数据转换为相关的 MRTK 事件 (例如，通过调用 RaisePoseInputChanged 或 RaiseHandJointsUpdated) 并更新其自己的内部状态，以便查询 [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) 将返回正确的数据。

通常，控制器的生命周期将涉及：

1. 当检测到新的源 (时，控制器由设备管理器创建例如，设备管理器检测并开始跟踪) 。

2. 在控制器的 Update () 循环中，它将调入其基础 API 系统。

3. 在同一更新循环中，它通过直接调用核心输入系统本身来引发输入事件更改 (例如，引发 HandMeshUpdated 或 HandJointsUpdated) 。

## <a name="pointers-and-focus"></a>指针和焦点

指针用于与游戏对象进行交互。 本部分介绍如何创建指针，如何更新指针，以及它们如何确定焦点)  (的对象。 它还将介绍存在的不同类型的指针以及它们处于活动状态的方案。

### <a name="pointer-categories"></a>指针类别

指针通常属于以下类别之一：

- **远端指针**

  这些类型的指针用于与远离用户 (远距离的对象进行交互，只需定义为 "不接近" ) 。 通常，这些类型的指针会转换可以进入世界各地的行，并允许用户与之交互和操作不会立即出现在其中的对象。

- **接近指针**

  这些类型的指针用于与足够接近用户以获取、触摸和操作的对象进行交互。 通常，这些类型的指针通过查找附近附近的对象来与对象进行交互 (方法是：在小规模执行 raycasting，在附近执行球面强制转换，或枚举被视为 grabbable/可触摸) 的对象的列表。

- **传送指针**

  这些类型的指针插入 teleportation 系统，以处理将用户移动到指针的目标位置。

## <a name="pointer-mediation"></a>指针采集

由于单个控制器可以有多个指针 (例如，有向的有向右和远的交互指针) 的组件都有一个组件，该组件负责调节哪个指针应处于活动状态。

例如，当用户的 pressable 按钮接近时， [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 应会停止显示，并 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) 应使用。

这由进行处理 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ，后者负责根据所有指针的状态来确定哪些指针处于活动状态。 此功能的关键之一是在接近对象附近时禁用指针， (请参阅 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator)) 。

可以通过更改 [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) 指针配置文件上的属性，提供指针转存进程的备用实现。

### <a name="how-to-disable-pointers"></a>如何禁用指针

因为指针转存进程每帧运行一次，最终会控制所有指针的活动/非活动状态。 因此，如果您在代码中设置指针的 IsInteractionEnabled 属性，它将被每个帧的指针转存进程所覆盖。 相反，你可以指定， [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 以控制指针是应自行打开还是关闭。 请注意，这仅适用于在 MRTK 中使用默认值 [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) 和 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) 。

#### <a name="example-disable-hand-rays-in-mrtk"></a>示例：在 MRTK 中禁用手写光线

以下代码将关闭 MRTK 中的手写射线：

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

以下代码会在 MRTK 中将手形光线返回到其默认行为：

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

以下代码将强制手动光线开启，而不考虑是否接近 grabbable：

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) 有关更多示例，请参阅和。

### <a name="focusprovider"></a>FocusProvider

[`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)是负责遍历所有指针的列表并确定每个指针的聚焦对象的主力。

在每次 `Update()` 调用中，这将：

1. 通过 raycasting 并按指针本身的配置进行命中检测来更新所有指针 (例如，球指针可指定 SphereOverlap raycastMode，因此 FocusProvider 将执行基于球的冲突) 

2. 基于每个指针更新焦点对象 (即，如果对象获得焦点，则它还会触发这些对象的事件，如果对象失去焦点，则会触发焦点丢失，等等) 。

### <a name="pointer-configuration-and-lifecycle"></a>指针配置和生命周期

可在输入系统配置文件的 "*指针*" 部分 [配置指针](../features/input/pointers.md)。

指针的生存期通常如下：

1. 设备管理器将检测控制器是否存在。 然后，此设备管理器将通过调用来创建与控制器关联的指针集 [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) 。

2. FocusProvider 在其更新 () 循环中，会循环访问所有有效指针，并执行关联的 raycast 或命中检测逻辑。 这用于确定由每个特定指针重点关注的对象。

    - 由于可以同时拥有多个输入的源 (例如，两次) 的活动存在，因此也可以有多个同时具有焦点的对象。

3. 在发现控制器源丢失的情况下，设备管理器将会丢弃与丢失的控制器关联的指针。