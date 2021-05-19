---
title: 手部关节追踪器
description: MRTK 中的手部联合追踪器
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: f9db1c4a2ca1959a35c541e87c9a4a01bc41637e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144619"
---
# <a name="hand-joint-chaser-example"></a>手部联合追踪器示例

![手部联合追踪器 此示例场景演示如何 ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) 使用求解器将对象附加到手部。

## <a name="example-scene"></a>示例场景

可以在 下的 文件夹中找到 **示例场景 HandJointChaserExample** `Assets/MRTK/Examples` 场景 `Demos/Input/Scenes/` 。

## <a name="solver-handler"></a>求解器处理程序

单击 **"要引用的跟踪对象"，** 然后选择"左 **手联合"** 或"**右手联合"。** 你将能够看到" **跟踪的手部联合"** 下拉列表。 从下拉列表中，可以选择要跟踪的特定联合。此示例场景使用径向视图求解器使对象跟随目标对象。 有关详细信息 [，请参阅求解](../ux-building-blocks/solvers/solver.md) 器页。

![手部联合求解器](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
