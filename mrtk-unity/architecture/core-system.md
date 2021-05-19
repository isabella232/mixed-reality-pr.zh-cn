---
title: 核心系统
description: MRTK 中的输入系统、设备管理器和数据提供程序
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 事件
ms.openlocfilehash: 12719a6c749a03648d4f75e9e6461b85cc9ab275
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144298"
---
# <a name="core-system"></a><span data-ttu-id="a9945-104">核心系统</span><span class="sxs-lookup"><span data-stu-id="a9945-104">Core system</span></span>

<span data-ttu-id="a9945-105">输入系统的核心是 [InputSystem，](../features/input/overview.md)这是一项服务，负责初始化和操作与 MRTK 关联的所有输入相关功能。</span><span class="sxs-lookup"><span data-stu-id="a9945-105">At the heart of the input system is the [InputSystem](../features/input/overview.md), which is a service that is responsible for initializing and operating all of the input related functionality associated with the MRTK.</span></span>

> [!NOTE]
> <span data-ttu-id="a9945-106">假定读者已阅读并基本了解 [术语部分](terminology.md) 。</span><span class="sxs-lookup"><span data-stu-id="a9945-106">It is assumed that readers have already read and have a basic understanding of the [terminology](terminology.md) section.</span></span>

<span data-ttu-id="a9945-107">此服务负责：</span><span class="sxs-lookup"><span data-stu-id="a9945-107">This service is responsible for:</span></span>

- <span data-ttu-id="a9945-108">读取 [输入系统配置文件](../configuration/mixed-reality-configuration-guide.md#input-system-settings)</span><span class="sxs-lookup"><span data-stu-id="a9945-108">Reading the [input system profile](../configuration/mixed-reality-configuration-guide.md#input-system-settings)</span></span>
- <span data-ttu-id="a9945-109">启动已配置 [的数据提供程序 (](../features/input/input-providers.md) 例如 `Windows Mixed Reality Device Manager` `OpenVR Device Manager` ，) 。</span><span class="sxs-lookup"><span data-stu-id="a9945-109">Starting the configured [data providers](../features/input/input-providers.md) (for example, `Windows Mixed Reality Device Manager` and `OpenVR Device Manager`).</span></span>
- <span data-ttu-id="a9945-110">[GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider)实例化，该组件负责提供 HoloLens (第一代) 样式头部凝视信息以及 HoloLens 2 样式眼睛凝视信息。</span><span class="sxs-lookup"><span data-stu-id="a9945-110">Instantiation of the [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider), which is a component that is responsible for providing HoloLens (1st generation) style head gaze information in addition to HoloLens 2 style eye gaze information.</span></span>
- <span data-ttu-id="a9945-111">[FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider)实例化，这是一个组件，负责确定具有焦点的对象。</span><span class="sxs-lookup"><span data-stu-id="a9945-111">Instantiation of the [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider), which is a component that is responsible for determining objects that have focus.</span></span> <span data-ttu-id="a9945-112">本文档的指针 [和焦点部分](controllers-pointers-and-focus.md#pointers-and-focus) 对此进行了更深入的介绍。</span><span class="sxs-lookup"><span data-stu-id="a9945-112">This is described in more depth in the [pointers and focus](controllers-pointers-and-focus.md#pointers-and-focus) section of the documentation.</span></span>
- <span data-ttu-id="a9945-113">提供所有输入事件的注册点 (全局[侦听器) 。](#global-listeners)</span><span class="sxs-lookup"><span data-stu-id="a9945-113">Providing registration points for all input events (as [global listeners](#global-listeners)).</span></span>
- <span data-ttu-id="a9945-114">为这些输入事件提供事件调度功能。</span><span class="sxs-lookup"><span data-stu-id="a9945-114">Providing event dispatch capabilities for those input events.</span></span>

## <a name="input-events"></a><span data-ttu-id="a9945-115">输入事件</span><span class="sxs-lookup"><span data-stu-id="a9945-115">Input events</span></span>

<span data-ttu-id="a9945-116">输入事件通常在两个不同的通道上触发：</span><span class="sxs-lookup"><span data-stu-id="a9945-116">Input events are generally fired on two different channels:</span></span>

### <a name="objects-in-focus"></a><span data-ttu-id="a9945-117">焦点对象</span><span class="sxs-lookup"><span data-stu-id="a9945-117">Objects in focus</span></span>

<span data-ttu-id="a9945-118">可以直接将事件发送到具有焦点的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="a9945-118">Events can be sent directly to a GameObject that has focus.</span></span> <span data-ttu-id="a9945-119">例如，对象可能有实现 的脚本 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 。</span><span class="sxs-lookup"><span data-stu-id="a9945-119">For example, an object might have a script that implements [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler).</span></span>
<span data-ttu-id="a9945-120">当焦点位于它附近的手上时，此对象将获取触摸事件。</span><span class="sxs-lookup"><span data-stu-id="a9945-120">This object would get touch events when focused by a hand that is near it.</span></span> <span data-ttu-id="a9945-121">这些类型的事件会"向上"进入 GameObject 层次结构，直到找到能够处理事件的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="a9945-121">These types of events go "up" the GameObject hierarchy until it finds a GameObject that is capable of handling the event.</span></span>

<span data-ttu-id="a9945-122">这是通过使用默认输入系统实现中的 [ExecuteHierarchy](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) 完成。</span><span class="sxs-lookup"><span data-stu-id="a9945-122">This is done by using [ExecuteHierarchy](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) from within the default input system implementation.</span></span>

### <a name="global-listeners"></a><span data-ttu-id="a9945-123">全局侦听器</span><span class="sxs-lookup"><span data-stu-id="a9945-123">Global listeners</span></span>

<span data-ttu-id="a9945-124">可以向全局侦听器发送事件。</span><span class="sxs-lookup"><span data-stu-id="a9945-124">Events can be sent to global listeners.</span></span> <span data-ttu-id="a9945-125">可以通过使用输入系统的接口注册所有输入事件 [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) 。</span><span class="sxs-lookup"><span data-stu-id="a9945-125">It's possible to register for all input events by using the input system's [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) interface.</span></span> <span data-ttu-id="a9945-126">建议使用 [r](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler%2A) 方法来注册全局事件-不推荐使用的 `Register` 函数将导致侦听器收到所有输入事件的通知，而不是仅通知特定类型的输入事件 (其中类型由事件接口) 定义。</span><span class="sxs-lookup"><span data-stu-id="a9945-126">It's recommended to use the [RegisterHandler](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler%2A) method for registering for global events - the deprecated `Register` function will cause listeners to get notified of ALL input events, rather than just input events of a particular type (where type is defined by the event interface).</span></span>

<span data-ttu-id="a9945-127">请注意， [后备侦听器](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler%2A) 是另一种类型的全局侦听器，这也是不鼓励的，因为它们将接收每个未在场景中的其他位置处理的单个输入事件。</span><span class="sxs-lookup"><span data-stu-id="a9945-127">Note that [fallback listeners](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler%2A) are another type of global listeners which are also discouraged because they will receive every single input event that hasn't been handled elsewhere in the scene.</span></span>

### <a name="order-of-event-dispatch"></a><span data-ttu-id="a9945-128">事件调度的顺序</span><span class="sxs-lookup"><span data-stu-id="a9945-128">Order of event dispatch</span></span>

<span data-ttu-id="a9945-129">通常情况下，事件按以下方式发送到侦听器。</span><span class="sxs-lookup"><span data-stu-id="a9945-129">Generally, events are sent to listeners in the following way.</span></span> <span data-ttu-id="a9945-130">请注意，如果以下任一步骤将事件标记为已 [处理](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html)，则事件调度进程将停止。</span><span class="sxs-lookup"><span data-stu-id="a9945-130">Note that if any of the steps below mark the event as [handled](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html), the event dispatch process stops.</span></span>

1. <span data-ttu-id="a9945-131">事件将发送到全局侦听器。</span><span class="sxs-lookup"><span data-stu-id="a9945-131">Event is sent to global listeners.</span></span>
2. <span data-ttu-id="a9945-132">事件将发送到聚焦对象的模式对话框。</span><span class="sxs-lookup"><span data-stu-id="a9945-132">Event is sent to modal dialogs of the focused object.</span></span>
3. <span data-ttu-id="a9945-133">事件发送到聚焦对象。</span><span class="sxs-lookup"><span data-stu-id="a9945-133">Event is sent to the focused object.</span></span>
4. <span data-ttu-id="a9945-134">事件将发送到回退侦听器。</span><span class="sxs-lookup"><span data-stu-id="a9945-134">Event is sent to fallback listeners.</span></span>

## <a name="device-managers-and-data-providers"></a><span data-ttu-id="a9945-135">设备管理器和数据访问接口</span><span class="sxs-lookup"><span data-stu-id="a9945-135">Device managers and data providers</span></span>

<span data-ttu-id="a9945-136">这些实体负责与较低级别 Api (例如 Windows Mixed Reality Api 或 OpenVR Api) ，并将这些系统中的数据转换为适合 MRTK 的更高级别输入抽象化的数据。</span><span class="sxs-lookup"><span data-stu-id="a9945-136">These entities are responsible for interfacing with lower-level APIs (such as Windows Mixed Reality APIs, or OpenVR APIs) and translating data from those systems into ones that fit the MRTK's higher level input abstractions.</span></span> <span data-ttu-id="a9945-137">它们负责检测、创建和管理 [控制器](controllers-pointers-and-focus.md#controllers)的生存期。</span><span class="sxs-lookup"><span data-stu-id="a9945-137">They are responsible for detecting, creating, and managing the lifetime of [controllers](controllers-pointers-and-focus.md#controllers).</span></span>

<span data-ttu-id="a9945-138">设备管理器的基本流程涉及：</span><span class="sxs-lookup"><span data-stu-id="a9945-138">The basic flow of a device manager involves:</span></span>

1. <span data-ttu-id="a9945-139">设备管理器由输入系统服务实例化。</span><span class="sxs-lookup"><span data-stu-id="a9945-139">The device manager is instantiated by the input system service.</span></span>
2. <span data-ttu-id="a9945-140">设备管理器将向其基础系统注册 (例如，Windows Mixed Reality 设备管理器将注册 [输入](../features/input/input-events.md) 和 [手势](../features/input/gestures.md#gesture-events) 事件。</span><span class="sxs-lookup"><span data-stu-id="a9945-140">The device manager registers with its underlying system (for example, the Windows Mixed Reality device manager will register for [input](../features/input/input-events.md) and [gesture](../features/input/gestures.md#gesture-events) events.</span></span>
3. <span data-ttu-id="a9945-141">它会创建它从基础系统发现的控制器 (例如，提供程序可以检测到有表述的手的状态) </span><span class="sxs-lookup"><span data-stu-id="a9945-141">It creates controllers that it discovers from the underlying system (for example the provider could detect the presence of articulated hands)</span></span>
4. <span data-ttu-id="a9945-142">在其更新 () 循环中调用 UpdateController () ，以轮询基础系统的新状态并更新其控制器表示形式。</span><span class="sxs-lookup"><span data-stu-id="a9945-142">In its Update() loop, call UpdateController() to poll for the new state of the underlying system and update its controller representation.</span></span>
