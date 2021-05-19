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
# <a name="core-system"></a>核心系统

输入系统的核心是 [InputSystem，](../features/input/overview.md)这是一项服务，负责初始化和操作与 MRTK 关联的所有输入相关功能。

> [!NOTE]
> 假定读者已阅读并基本了解 [术语部分](terminology.md) 。

此服务负责：

- 读取 [输入系统配置文件](../configuration/mixed-reality-configuration-guide.md#input-system-settings)
- 启动已配置 [的数据提供程序 (](../features/input/input-providers.md) 例如 `Windows Mixed Reality Device Manager` `OpenVR Device Manager` ，) 。
- [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider)实例化，该组件负责提供 HoloLens (第一代) 样式头部凝视信息以及 HoloLens 2 样式眼睛凝视信息。
- [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider)实例化，这是一个组件，负责确定具有焦点的对象。 本文档的指针 [和焦点部分](controllers-pointers-and-focus.md#pointers-and-focus) 对此进行了更深入的介绍。
- 提供所有输入事件的注册点 (全局[侦听器) 。](#global-listeners)
- 为这些输入事件提供事件调度功能。

## <a name="input-events"></a>输入事件

输入事件通常在两个不同的通道上触发：

### <a name="objects-in-focus"></a>焦点对象

可以直接将事件发送到具有焦点的 GameObject。 例如，对象可能有实现 的脚本 [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) 。
当焦点位于它附近的手上时，此对象将获取触摸事件。 这些类型的事件会"向上"进入 GameObject 层次结构，直到找到能够处理事件的 GameObject。

这是通过使用默认输入系统实现中的 [ExecuteHierarchy](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) 完成。

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
