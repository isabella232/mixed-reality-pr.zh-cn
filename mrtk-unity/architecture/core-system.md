---
title: 核心系统
description: MRTK 中的输入系统、设备管理器和数据访问接口
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，事件
ms.openlocfilehash: 79ebd3855cd991db168233f00058ab5d42f87d83
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121595"
---
# <a name="core-system"></a>核心系统

输入系统的核心是 [InputSystem](../features/input/overview.md)，这是一个服务，负责初始化和操作与 MRTK 关联的所有与输入相关的功能。

> [!NOTE]
> 假设读者已经阅读并大致了解 [术语](terminology.md) 部分。

此服务负责：

- 读取 [输入系统配置文件](../configuration/mixed-reality-configuration-guide.md#input-system-settings)
- 例如，启动配置的 [数据提供程序](../features/input/input-providers.md) (， `Windows Mixed Reality Device Manager` 并 `OpenVR Device Manager`) 。
- [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider)的实例化，它是一个组件，该组件负责提供 hololens (第一代) 样式的打印头眼睛，还包括 hololens 2 样式眼睛信息。
- [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider)的实例化，它是负责确定具有焦点的对象的组件。 文档的 [指针和焦点](controllers-pointers-and-focus.md#pointers-and-focus) 部分更深入地介绍了这种情况。
- 为所有输入事件提供注册点， (作为 [全局侦听器](#global-listeners)) 。
- 为这些输入事件提供事件调度功能。

## <a name="input-events"></a>输入事件

输入事件通常在两个不同的通道上触发：

### <a name="objects-in-focus"></a>焦点对象

事件可以直接发送到具有焦点的 GameObject。 例如，对象可能具有实现的脚本 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 。
当焦点在其附近时，此对象将获得触控事件。 这些类型的事件将 "向上" GameObject 层次结构，直到找到能够处理事件的 GameObject。

这是通过从默认输入系统实现中使用 [ExecuteHierarchy](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) 来完成的。

### <a name="global-listeners"></a>全局侦听器

可以向全局侦听器发送事件。 可以通过使用输入系统的接口注册所有输入事件 [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) 。 建议使用 [r](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler%2A) 方法来注册全局事件-不推荐使用的 `Register` 函数将导致侦听器收到所有输入事件的通知，而不是仅通知特定类型的输入事件 (其中类型由事件接口) 定义。

请注意， [后备侦听器](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler%2A) 是另一种类型的全局侦听器，这也是不鼓励的，因为它们将接收每个未在场景中的其他位置处理的单个输入事件。

### <a name="order-of-event-dispatch"></a>事件调度的顺序

通常情况下，事件按以下方式发送到侦听器。 请注意，如果以下任一步骤将事件标记为已 [处理](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html)，则事件调度进程将停止。

1. 事件将发送到全局侦听器。
2. 事件将发送到聚焦对象的模式对话框。
3. 事件发送到聚焦对象。
4. 事件将发送到回退侦听器。

## <a name="device-managers-and-data-providers"></a>设备管理器和数据访问接口

这些实体负责与较低级别 Api (例如 Windows Mixed Reality Api 或 OpenVR Api) ，并将这些系统中的数据转换为适合 MRTK 的更高级别输入抽象化的数据。 它们负责检测、创建和管理 [控制器](controllers-pointers-and-focus.md#controllers)的生存期。

设备管理器的基本流程涉及：

1. 设备管理器由输入系统服务实例化。
2. 设备管理器将向其基础系统注册 (例如，Windows Mixed Reality 设备管理器将注册 [输入](../features/input/input-events.md) 和 [手势](../features/input/gestures.md#gesture-events) 事件。
3. 它会创建它从基础系统发现的控制器 (例如，提供程序可以检测到有表述的手的状态) 
4. 在其更新 () 循环中调用 UpdateController () ，以轮询基础系统的新状态并更新其控制器表示形式。
