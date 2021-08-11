---
title: 输入概述
description: MRTK 中的输入系统概述
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: b175b16e2004fb00cef430335751c3aabc8c59fdd4ae78a2fc78c959a92240fb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219752"
---
# <a name="input-overview"></a>输入概述

通过 MRTK 中的输入系统，可以执行以下操作：

- 使用来自各种输入源的输入，例如6个 DOF 控制器，通过输入事件进行有表述的双手或语音。
- 定义抽象操作，如 *Select* 或 *Menu*，并将它们关联到不同的输入。
- 通过焦点和指针事件附加到控制器的设置指针，以驱动 UI 组件。

<img src="../images/input/MRTK_InputSystem.png" alt="Input System" style="display:block;margin-left:auto;margin-right:auto;">
<sup>MRTK 输入系统概述</sup>

[**输入由输入数据提供程序生成， (Device Manager)**](input-providers.md)。 每个提供程序对应于输入的特定源： Open VR、Windows Mixed Reality (WMR) 、Unity 操纵杆、Windows 语音等。通过 *混合现实 Toolkit* 组件中的 **已注册服务提供程序配置文件** 将提供程序添加到项目中，并将在相应的输入源可用时自动生成 [**输入事件**](input-events.md) (例如，检测到 WMR 控制器或连接) 的游戏板。

[**输入操作**](input-actions.md) 是针对原始输入的抽象，旨在帮助将应用程序逻辑与产生输入的特定输入源隔离开来。 例如，可以定义 " *选择* " 操作并将其映射到鼠标左键、游戏板中的按钮和 6 DOF 控制器中的触发器，这一点非常有用。 然后，你可以让应用程序逻辑侦听 *选择* 输入操作事件，而无需知道可以生成的所有不同输入。 输入操作在 **输入操作配置文件** 中定义，该配置文件位于 *混合现实 Toolkit* 组件中的 *输入系统配置文件* 中。

当检测到输入设备丢失或断开连接时，*输入提供程序* 会创建 [**控制器**](controllers.md)并销毁它们。 例如，WMR 输入提供程序将为 6 DOF 设备创建 *WMR 控制器* ，并为明确表述的手写设备创建 *WMR* 。 在 *输入系统配置文件* 中，可以通过 **控制器映射配置文件** 将控制器输入映射到输入操作。 由控制器引发的输入事件将包括关联的输入操作（如果有）。

控制器可以附加到它们的指针，这些 [**指针**](pointers.md) 用于查询场景来确定具有焦点的游戏对象并在其上引发 [**指针事件**](pointers.md#pointer-event-interfaces) 。 例如， *行指针* 使用控制器姿势对场景执行 raycast，以计算光线的原点和方向。 为每个控制器创建的指针是在 "*输入系统配置文件*" 下的 **指针配置文件** 中设置的。

<img src="../images/input/MRTK_Input_EventFlow.png" width="200px" alt="Event Flow" style="display:block;margin-left:auto;margin-right:auto;">
<sup>事件流。</sup>

尽管可以 [直接在 UI 组件中处理输入事件](input-events.md)，但建议使用 [指针事件](pointers.md#pointer-event-interfaces) ，使实现与设备无关。

MRTK 还提供了几种便捷方法来直接以与设备无关的方式查询输入状态。 有关更多详细信息，请参阅 [访问 MRTK 中的输入状态](input-state.md) 。
