---
title: 术语
description: MRTK 中的不同输入系统术语。
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 输入，
ms.openlocfilehash: 33f423fba286e9e85e6d0bedac82bff0b7aae81f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121455"
---
# <a name="input-system"></a>输入系统

输入系统是 MRTK 提供的所有功能中最大的系统之一。
工具包中基于它构建的许多内容 (指针、焦点、预制件) 。 输入系统内的代码允许自然交互，例如跨平台抓取和旋转。

输入系统有一些值得定义的术语：

- **数据提供程序**

    输入配置文件中的输入设置具有对称为数据访问提供程序的实体的引用 - 另一个描述这些实体的单词是设备管理器。 这些组件的工作是通过使用特定的基础系统进行连接来扩展 MRTK 输入系统。 提供程序的一个示例是 Windows Mixed Reality 提供程序，其作业是与基础 Windows Mixed Reality API 对话，然后将这些 API 的数据转换为下面特定于 MRTK 的输入概念。 另一个示例是 OpenVR 提供程序 (，其作业是与 Unity 抽象版本的 OpenVR API 对话，然后将该数据转换为 MRTK 输入概念) 。

- **控制器**

    物理控制器的表示形式 (无论它是 6 度自由控制器、具有手势支持的 HoloLens 1 样式手、完全表达的手势、闰运动控制器等) 。 控制器由设备管理器生成 (，即 WMR 设备管理器将生成一个控制器，并管理其生存期，当它看到一个明确手) 。

- **指针**

    控制器使用指针与游戏对象交互。 例如，近交互指针负责检测手部（ (控制器）何时) 将自身播发为支持"近交互"的对象。 指针的其他示例包括远程传送或远距指针 (即 shell 手部射线指针) ，它使用远距光线广播来与用户发送的长于手部长度的内容交互。

    指针由设备管理器创建，然后附加到输入源。 若要获取控制器的所有指针，请执行以下操作： `controller.InputSource.Pointers`

    请注意，控制器可以同时与许多不同的指针关联。 为了确保这不会进入混沌状态，有一个指针转换器控制允许哪些指针处于活动状态 (例如，当检测到近交互时，该) 。

- **重点**

    指针事件将发送到焦点 **中的对象**。 焦点选择因指针类型而异;手部射线指针将使用光线广播，而手部指针将使用球体广播。 对象必须实现 IMixedRealityFocusHandler 以接收焦点。 可以全局注册对象以接收未筛选的指针事件，但不建议此方法。

    更新焦点对象的组件是 [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)

- **游标**

    与指针关联的实体，该指针围绕指针交互提供其他视觉提示。 例如，FingerCursor 将围绕手指呈现一个环，并且当手指接近"近可交互"对象时，可能会旋转该环。 指针可以一次与单个游标相关联。

- **交互和操作**

    可以使用交互或操作脚本标记对象。 这可以通过 或 [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) 类似 [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) / [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) 。

    例如，NearInteractionGrabbable 和 NearInteractionTouchable 允许某些指针 (尤其是近) 交互指针，以知道可以聚焦哪些对象。

    可交互和 ManipulationHandler 是侦听指针事件以修改 UI 视觉对象或移动/缩放/旋转游戏对象的组件示例。

下图从 MRTK 输入堆栈 (从下到) 捕获高级生成：

![输入系统关系图](../features/images/input/MRTK_InputSystem.png)
