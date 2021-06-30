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
# <a name="controllers-pointers-and-focus"></a><span data-ttu-id="f2705-104">控制器、指针和焦点</span><span class="sxs-lookup"><span data-stu-id="f2705-104">Controllers, pointers, and focus</span></span>

<span data-ttu-id="f2705-105">控制器、指针和焦点是更高级别的概念，基于核心输入系统建立的基础。</span><span class="sxs-lookup"><span data-stu-id="f2705-105">Controllers, pointers, and focus are higher-level concepts that build upon the foundation established by the core input system.</span></span> <span data-ttu-id="f2705-106">它们共同提供了与场景中的对象进行交互的很大一部分机制。</span><span class="sxs-lookup"><span data-stu-id="f2705-106">Together, they provide a large portion of the mechanism for interacting with objects in the scene.</span></span>

## <a name="controllers"></a><span data-ttu-id="f2705-107">Controllers</span><span class="sxs-lookup"><span data-stu-id="f2705-107">Controllers</span></span>

<span data-ttu-id="f2705-108">控制器是物理控制器的表示形式 (6 度自由、手部表达等) 。</span><span class="sxs-lookup"><span data-stu-id="f2705-108">Controllers are representations of a physical controller (6-degrees of freedom, articulated hand, etc).</span></span> <span data-ttu-id="f2705-109">它们由设备管理器创建，负责与相应的基础系统通信，并将该数据转换为 MRTK 形状的数据和事件。a</span><span class="sxs-lookup"><span data-stu-id="f2705-109">They are created by device managers and are responsible for communicating with the corresponding underlying system and translating that data into MRTK-shaped data and events.a</span></span>

<span data-ttu-id="f2705-110">例如，在 Windows Mixed Reality 平台上， 是一个控制器，负责与基础 Windows 手部跟踪 API 交互，以获取有关手部、姿势和其他属性 [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) 的信息[](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)。</span><span class="sxs-lookup"><span data-stu-id="f2705-110">For example, on the Windows Mixed Reality platform, the [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) is a controller that is responsible for interfacing with the underlying Windows [hand tracking APIs](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) to get information about the joints, pose, and other properties of the hand.</span></span> <span data-ttu-id="f2705-111">它负责将这些数据转换为相关的 MRTK 事件 (例如，通过调用 RaisePoseInputChanged 或 RaiseHandJointsUpdated) 并更新其自己的内部状态，以便对 的查询返回正确的数据。 [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A)</span><span class="sxs-lookup"><span data-stu-id="f2705-111">It is responsible for turning this data into relevant MRTK events (for example, by calling RaisePoseInputChanged or RaiseHandJointsUpdated) and by updating its own internal state so that queries for [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) will return correct data.</span></span>

<span data-ttu-id="f2705-112">通常，控制器的生命周期将涉及：</span><span class="sxs-lookup"><span data-stu-id="f2705-112">Generally, a controller's lifecycle will involve:</span></span>

1. <span data-ttu-id="f2705-113">设备管理器在检测到新源时创建控制器 (例如，设备管理器检测并开始跟踪手部) 。</span><span class="sxs-lookup"><span data-stu-id="f2705-113">A controller gets created by a device manager upon detection of a new source (for example, the device manager detects and starts tracking a hand).</span></span>

2. <span data-ttu-id="f2705-114">在控制器的 Update () 循环中，它会调用其基础 API 系统。</span><span class="sxs-lookup"><span data-stu-id="f2705-114">In the controller's Update() loop, it calls into its underlying API system.</span></span>

3. <span data-ttu-id="f2705-115">在同一更新循环中，它通过直接调用核心输入系统本身来引发输入事件更改 (例如，引发 HandMeshUpdated 或 HandJointsUpdated) 。</span><span class="sxs-lookup"><span data-stu-id="f2705-115">In the same update loop, it raises input event changes by calling directly into the core input system itself (for example, raising HandMeshUpdated, or HandJointsUpdated).</span></span>

## <a name="pointers-and-focus"></a><span data-ttu-id="f2705-116">指针和焦点</span><span class="sxs-lookup"><span data-stu-id="f2705-116">Pointers and focus</span></span>

<span data-ttu-id="f2705-117">指针用于与游戏对象交互。</span><span class="sxs-lookup"><span data-stu-id="f2705-117">Pointers are used to interact with game objects.</span></span> <span data-ttu-id="f2705-118">本部分介绍如何创建指针、如何更新指针，以及如何确定 (焦点) 对象。</span><span class="sxs-lookup"><span data-stu-id="f2705-118">This section describes how pointers are created, how they get updated, and how they determine the object(s) that are in focus.</span></span> <span data-ttu-id="f2705-119">它还将介绍存在的不同类型的指针及其处于活动状态的方案。</span><span class="sxs-lookup"><span data-stu-id="f2705-119">It will also cover the different types of pointers that exist and the scenarios in which they are active.</span></span>

### <a name="pointer-categories"></a><span data-ttu-id="f2705-120">指针类别</span><span class="sxs-lookup"><span data-stu-id="f2705-120">Pointer categories</span></span>

<span data-ttu-id="f2705-121">指针通常分为以下类别之一：</span><span class="sxs-lookup"><span data-stu-id="f2705-121">Pointers generally fall into one of the following categories:</span></span>

- <span data-ttu-id="f2705-122">**远指针**</span><span class="sxs-lookup"><span data-stu-id="f2705-122">**Far pointers**</span></span>

  <span data-ttu-id="f2705-123">这些类型的指针用于与远离用户的对象交互 (被定义为"不靠近") 。</span><span class="sxs-lookup"><span data-stu-id="f2705-123">These types of pointers are used to interact with objects that are far away from the user (far away is defined as simply “not near”).</span></span> <span data-ttu-id="f2705-124">这些类型的指针通常可强制转换行，这些线条可以深入到世界，并允许用户与它们不紧接的对象进行交互和操作。</span><span class="sxs-lookup"><span data-stu-id="f2705-124">These types of pointers generally cast lines that can go far into the world and allow the user to interact with and manipulate objects that are not immediately next to them.</span></span>

- <span data-ttu-id="f2705-125">**近指针**</span><span class="sxs-lookup"><span data-stu-id="f2705-125">**Near pointers**</span></span>

  <span data-ttu-id="f2705-126">这些类型的指针用于与距离用户足够近的对象进行交互，以便进行抓取、触摸和操作。</span><span class="sxs-lookup"><span data-stu-id="f2705-126">These types of pointers are used to interact with objects that are close enough to the user to grab, touch, and manipulate.</span></span> <span data-ttu-id="f2705-127">通常，这些类型的指针通过查找附近邻近区域 (中的对象来与对象交互：在短距离处进行光线投射、执行球状强制转换以查找邻近对象，或枚举被视为可抓取/可触摸对象) 。</span><span class="sxs-lookup"><span data-stu-id="f2705-127">Generally, these types of pointers interact with objects by looking for objects in the nearby vicinity (either by doing raycasting at small distances, doing spherical casting looking for objects in the vicinity, or enumerating lists of objects that are considered grabbable/touchable).</span></span>

- <span data-ttu-id="f2705-128">**Teleport 指针**</span><span class="sxs-lookup"><span data-stu-id="f2705-128">**Teleport pointers**</span></span>

  <span data-ttu-id="f2705-129">这些类型的指针会插入远程传送系统，以处理将用户移动到指针所针对的位置。</span><span class="sxs-lookup"><span data-stu-id="f2705-129">These types of pointers plug into the teleportation system to handle moving the user to the location targeted by the pointer.</span></span>

## <a name="pointer-mediation"></a><span data-ttu-id="f2705-130">指针中介</span><span class="sxs-lookup"><span data-stu-id="f2705-130">Pointer mediation</span></span>

<span data-ttu-id="f2705-131">例如，由于单个控制器可以有多个指针 (，因此可同时具有近部和远部交互指针) 因此存在一个组件，负责对哪个指针应处于活动状态进行媒体处理。</span><span class="sxs-lookup"><span data-stu-id="f2705-131">Because a single controller can have multiple pointers (for example, the articulated hand can have both near and far interaction pointers), there exists a component that is responsible for mediating which pointer should be active.</span></span>

<span data-ttu-id="f2705-132">例如，当用户手接近可按下按钮时， [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) 应停止显示，并且 [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) 应参与。</span><span class="sxs-lookup"><span data-stu-id="f2705-132">For example, as the user’s hand approaches a pressable button, the [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) should stop showing, and the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) should be engaged.</span></span>

<span data-ttu-id="f2705-133">这由 处理，它负责根据所有指针的状态确定哪些指针 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) 处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="f2705-133">This is handled by the [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator), which is responsible for determining which pointers are active, based on the state of all pointers.</span></span> <span data-ttu-id="f2705-134">此操作的主要功能之一是，当近指针接近对象时禁用远指针 (请参阅 [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator)) 。</span><span class="sxs-lookup"><span data-stu-id="f2705-134">One of the key things this does is disable far pointers when a near pointer is close to an object (please see [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator)).</span></span>

<span data-ttu-id="f2705-135">通过更改指针配置文件上的 属性，可以提供指针中介 [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) 的备用实现。</span><span class="sxs-lookup"><span data-stu-id="f2705-135">It's possible to provide an alternate implementation of the pointer mediator by changing the [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) property on the pointer profile.</span></span>

### <a name="how-to-disable-pointers"></a><span data-ttu-id="f2705-136">如何禁用指针</span><span class="sxs-lookup"><span data-stu-id="f2705-136">How to disable pointers</span></span>

<span data-ttu-id="f2705-137">由于指针转换器运行每个帧，因此它最终控制所有指针的活动/非活动状态。</span><span class="sxs-lookup"><span data-stu-id="f2705-137">Because the pointer mediator runs every frame, it ends up controlling the active / inactive state of all pointers.</span></span> <span data-ttu-id="f2705-138">因此，如果在代码中设置指针的 IsInteractionEnabled 属性，它将被每个帧的指针转换器覆盖。</span><span class="sxs-lookup"><span data-stu-id="f2705-138">Therefore, if you set a pointer's IsInteractionEnabled property in code, it will get overwritten by the pointer mediator every frame.</span></span> <span data-ttu-id="f2705-139">相反，可以指定 来控制 [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 指针是应打开还是关闭。</span><span class="sxs-lookup"><span data-stu-id="f2705-139">Instead, you can specify the [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) to control whether pointers should be on or off yourself.</span></span> <span data-ttu-id="f2705-140">请注意，只有在 MRTK 中使用的是默认 和 时 [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ，这才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="f2705-140">Note that this will only work if you are using the default [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) and [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK.</span></span>

#### <a name="example-disable-hand-rays-in-mrtk"></a><span data-ttu-id="f2705-141">示例：禁用 MRTK 中的手部射线</span><span class="sxs-lookup"><span data-stu-id="f2705-141">Example: Disable hand rays in MRTK</span></span>

<span data-ttu-id="f2705-142">以下代码将关闭 MRTK 中的手部射线：</span><span class="sxs-lookup"><span data-stu-id="f2705-142">The following code will turn off the hand rays in MRTK:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

<span data-ttu-id="f2705-143">以下代码将手部射线返回到 MRTK 中的默认行为：</span><span class="sxs-lookup"><span data-stu-id="f2705-143">The following code will return hand rays to their default behavior in MRTK:</span></span>

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

<span data-ttu-id="f2705-144">以下代码将强制手部射线打开，而不考虑是否靠近可抓取项：</span><span class="sxs-lookup"><span data-stu-id="f2705-144">The following code will force hand rays to be on, regardless if near a grabbable:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="f2705-145">有关 [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) 更多 [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) 示例，请参阅 和 。</span><span class="sxs-lookup"><span data-stu-id="f2705-145">See [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) and [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) for more examples.</span></span>

### <a name="focusprovider"></a><span data-ttu-id="f2705-146">FocusProvider</span><span class="sxs-lookup"><span data-stu-id="f2705-146">FocusProvider</span></span>

<span data-ttu-id="f2705-147">是一个工作队列，负责访问所有指针的列表，并找出每个指针的聚焦 [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) 对象。</span><span class="sxs-lookup"><span data-stu-id="f2705-147">The [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) is the workhorse that is responsible for iterating over the list of all pointers and figuring out what the focused object is for each pointer.</span></span>

<span data-ttu-id="f2705-148">在每个 `Update()` 调用中，这将：</span><span class="sxs-lookup"><span data-stu-id="f2705-148">In each `Update()` call, this will:</span></span>

1. <span data-ttu-id="f2705-149">通过光线广播和按指针本身配置执行命中检测来更新所有指针 (例如，球体指针可以指定 SphereOverlap raycastMode，因此 FocusProvider 将执行基于球体的碰撞) </span><span class="sxs-lookup"><span data-stu-id="f2705-149">Update all of the pointers, by raycasting and doing hit detection as-configured by the pointer itself (for example, the sphere pointer could specify the SphereOverlap raycastMode, so FocusProvider will do a sphere-based collision)</span></span>

2. <span data-ttu-id="f2705-150">根据每个指针更新焦点对象 (即，如果对象获得焦点，它还将触发指向这些对象的事件，如果对象失去焦点，则触发焦点丢失等) 。</span><span class="sxs-lookup"><span data-stu-id="f2705-150">Update the focused object on a per-pointer basis (i.e. if an object gained focus, it would also trigger events to those object, if an object lost focus, it would trigger focus lost, etc).</span></span>

### <a name="pointer-configuration-and-lifecycle"></a><span data-ttu-id="f2705-151">指针配置和生命周期</span><span class="sxs-lookup"><span data-stu-id="f2705-151">Pointer configuration and lifecycle</span></span>

<span data-ttu-id="f2705-152">[可以在输入系统配置文件的](../features/input/pointers.md)*指针* 部分配置指针。</span><span class="sxs-lookup"><span data-stu-id="f2705-152">[Pointers can be configured](../features/input/pointers.md) in the *Pointers* section of the input system profile.</span></span>

<span data-ttu-id="f2705-153">指针的生存期通常如下所示：</span><span class="sxs-lookup"><span data-stu-id="f2705-153">The lifetime of a pointer is generally the following:</span></span>

1. <span data-ttu-id="f2705-154">设备管理器将检测控制器是否存在。</span><span class="sxs-lookup"><span data-stu-id="f2705-154">A device manager will detect the presence of a controller.</span></span> <span data-ttu-id="f2705-155">然后，此设备管理器会通过调用 创建与控制器关联的指针集 [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) 。</span><span class="sxs-lookup"><span data-stu-id="f2705-155">This device manager will then create the set of pointers associated with the controller via a call to [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager).</span></span>

2. <span data-ttu-id="f2705-156">FocusProvider 在其 Update () 循环中，将循环遍历所有有效的指针，并执行关联的光线广播或命中检测逻辑。</span><span class="sxs-lookup"><span data-stu-id="f2705-156">The FocusProvider, in its Update() loop, will iterate over all of the valid pointers and do the associated raycast or hit detection logic.</span></span> <span data-ttu-id="f2705-157">这用于确定由每个特定指针聚焦的对象。</span><span class="sxs-lookup"><span data-stu-id="f2705-157">This is used to determine the object that is focused by each particular pointer.</span></span>

    - <span data-ttu-id="f2705-158">由于可以同时具有多个活动的输入源 (例如，两只手处于活动状态) ，因此还可以同时具有多个具有焦点的对象。</span><span class="sxs-lookup"><span data-stu-id="f2705-158">Because it's possible to have multiple sources of input active at the same time (for example, two hands active present), it's also possible to have multiple objects that have focus at the same time.</span></span>

3. <span data-ttu-id="f2705-159">设备管理器发现控制器源丢失后，会关闭与丢失的控制器关联的指针。</span><span class="sxs-lookup"><span data-stu-id="f2705-159">The device manager, upon discovering that a controller source was lost, will tear down the pointers associated with the lost controller.</span></span>