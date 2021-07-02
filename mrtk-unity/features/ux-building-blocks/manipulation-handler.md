---
title: 操作处理程序
description: 有关 MRTK 中的操作处理程序的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 操作，
ms.openlocfilehash: 179ef40ba054b0fda3b13e9d578905eb064a58ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176631"
---
# <a name="manipulation-handler"></a>操作处理程序

![操作处理程序](../images/manipulation-handler/MRTK_Manipulation_Main.png)

*ManipulationHandler* 脚本允许使用一只或两只手使对象可移动、可缩放且可旋转。 可以限制操作，以便仅允许某些类型的转换。 该脚本适用于各种类型的输入，包括HoloLens 2手部输入、手部射线、HoloLens (第一代) 手势输入和沉浸式头戴显示设备运动控制器输入。

## <a name="how-to-use-the-manipulation-handler"></a>如何使用操作处理程序

将 `ManipulationHandler` 脚本组件添加到 GameObject。 请确保还将碰撞体添加到对象，使其与可抓取边界匹配。

若要使对象响应接近表达的手动输入，请 `NearInteractionGrabbable` 添加脚本。

![在 unity 编辑器中使用操作处理程序](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a>检查器属性

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

**主机转换** 将拖动的转换。 默认为组件的 对象。

**操作类型** 指定是否可以使用一只手、两只手或两手操作对象。

* *仅一手*
* *仅两手*
* *一手和两手*

**两手操作类型**

* *缩放*：仅允许缩放。
* *旋转*：仅允许旋转。
* *移动缩放*：允许移动和缩放。
* *移动旋转*：允许移动和旋转。
* *旋转缩放*：允许旋转和缩放。
* *移动旋转刻度*：允许移动、旋转和缩放。

![操作处理程序](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

**允许远操作** 指定是否可以使用与指针的远部交互完成操作。

**单手旋转模式附近** 指定在靠近一个手/控制器抓取对象时对象的行为方式。

**单手旋转模式远** 指定在距离上用一只手/控制器抓取对象时对象的行为方式。

**单手旋转模式选项** 指定用一手抓取对象时对象的旋转方向。

* *维护原始旋转*：在移动对象时不旋转对象
* *向用户维护旋转*：为用户维护 X/Y 轴的对象原始旋转
* *垂直对齐使旋转保持旋转到用户*：将对象的原始旋转维护给用户，但使对象垂直旋转。 对于具有边界控件的对象很有用。
* *人脸用户*：确保对象始终面向用户。 适用于平板电脑/面板。
* *人脸离开用户*：确保对象始终面向用户。 适用于向后配置的板/面板。
* *围绕对象中心旋转*：仅适用于铰接式手/控制器。 使用手/控制器的旋转旋转对象，但围绕对象中心点旋转对象。 可用于在距离上检查。
* *围绕抓取点旋转*：仅适用于铰接式手/控制器。 旋转对象，就像由手/控制器持有一样。 用于检查。

**发布行为** 释放对象时，指定其物理移动行为。 要求一个刚体组件位于该对象上。

* *无*
* *全部内容*
* *保持速度*
* *保持Angular速度*

**旋转约束** 指定对象在交互时将在哪个轴上旋转。

* *无*
* *仅 X 轴*
* *仅 Y 轴*
* *仅 Z 轴*

**将本地空间用于约束** 一个切换开关，用于在应用世界空间轴或本地空间轴的约束之间进行切换。

**移动约束**

* *无*
* *修复与头部的距离*

**平滑处理活动** 指定平滑是否处于活动状态。

**一手平滑量** 要应用于移动、缩放、旋转的平滑量。 平滑为 0 表示无平滑。 最大值表示不更改值。

## <a name="events"></a>事件

操作处理程序提供以下事件：

* *OnManipulationStarted：* 在操作开始时触发。
* *OnManipulationEnded：* 操作结束时触发。
* *OnHoverStarted：* 当手/控制器将可操作对象悬停在近或远时触发。
* *OnHoverEnded：* 当手/控制器取消悬停可操作对象（近或远）时触发。
