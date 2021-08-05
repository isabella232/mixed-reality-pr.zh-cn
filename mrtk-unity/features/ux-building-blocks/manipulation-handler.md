---
title: 操作处理程序
description: MRTK 中的操作处理程序文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，操作，
ms.openlocfilehash: 24034c43bf8ce1f1ef463e894e9ca5293c2b0d2a146284535b161f8b4277dfa9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190195"
---
# <a name="manipulation-handler"></a>操作处理程序

![操作处理程序](../images/manipulation-handler/MRTK_Manipulation_Main.png)

使用 *ManipulationHandler* 脚本，可以通过一次或两次手使对象成为可移动的、可缩放的和 rotatable 的。 可以限制操作，使其仅允许某些类型的转换。 此脚本可用于各种类型的输入，包括 HoloLens 2 个明确表述的手写输入、手光、HoloLens (第一代) 手势输入和沉浸式耳机运动控制器输入。

## <a name="how-to-use-the-manipulation-handler"></a>如何使用操作处理程序

向 `ManipulationHandler` GameObject 添加脚本组件。 请确保还将碰撞器添加到对象中，并将其 grabbable 边界匹配。

若要使对象响应接近的有表述的手写输入，请 `NearInteractionGrabbable` 同时添加脚本。

![在 unity 编辑器中使用操作处理程序](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a>检查器属性

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

**主机转换** 要拖动的转换。 默认为组件的对象。

**操作类型** 指定是否可以使用一只手和/或双手操作该对象。

* *仅一个*
* *仅限两个*
* *一个和两个传递*

**双向操作类型**

* *Scale*：仅允许缩放。
* *旋转*：仅允许旋转。
* *移动刻度*：允许移动和缩放。
* *移动旋转*：允许移动和旋转。
* *旋转比例*：允许旋转和缩放。
* *移动旋转比例*：允许移动、旋转和缩放。

![操作处理程序](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

**允许远操作** 指定是否可以使用远与指针交互来完成操作。

**一种手型旋转模式接近** 指定对象在与附近的一台手型控制器一起被抓取时的行为方式。

**目前有一种手型旋转模式** 指定对象在与一个手/控制器距离的距离内进行操作时的行为方式。

**一只手旋转模式选项** 指定在用一只手抓取对象时，对象将如何旋转。

* *保持原始旋转*：在移动对象时不旋转对象
* *维护对用户的旋转*：维持对象对用户的 X/Y 轴的原始旋转
* *重心对齐维护对用户的旋转*：维持对象的原始旋转到用户，但使对象垂直。 适用于具有界限控件的对象。
* *面部用户*：确保对象始终面向用户。 适用于清单/面板。
* *远离用户*：确保始终远离用户的对象。 对向后配置的清单/面板非常有用。
* *围绕对象中心旋转*：仅适用于已表述的动手/控制器。 使用手型旋转旋转对象，但关于对象中心点。 对于距离检查很有用。
* *旋转 "吸引点*"：仅适用于已表述的动手/控制器。 旋转对象，就像它是由手动/控制器保持一样。 对于检查很有用。

**版本行为** 释放对象时，指定其物理移动行为。 要求刚体组件位于该对象上。

* *无*
* *全部内容*
* *保持速度*
* *保持 Angular 速度*

**旋转约束** 指定与进行交互时对象将旋转的轴。

* *无*
* *仅限 X 轴*
* *仅 Y 轴*
* *仅 Z 轴*

**使用本地空间作为约束** 切换在应用约束与世界空间轴（或本地空间轴）之间切换。

**有关移动的约束**

* *无*
* *修复与 head 的距离*

**平滑活动** 指定平滑处理是否处于活动状态。

**平滑量一次** 要应用于移动、缩放和旋转的平滑量。 平滑0表示无平滑处理。 Max 值表示没有更改为值。

## <a name="events"></a>事件

操作处理程序提供了以下事件：

* *OnManipulationStarted*：在操作开始时激发。
* *OnManipulationEnded*：操作结束时激发。
* *OnHoverStarted*：当右/控制器悬停可操作时，将会激发。
* *OnHoverEnded*：当手动/控制器取消悬停可操作时，将触发此操作。
