---
title: 手部关节追踪器
description: MRTK 中的 chaser
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 376dcd0e1ff01d6e9020aedf35ed2bb2b7b39fa8a119d125aa8c3a96bf0024fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189553"
---
# <a name="hand-joint-chaser"></a>手部关节追踪器

![手型接点 chasers ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) 此示例场景演示了如何使用规划求解将对象附加到手。

## <a name="example-scene"></a>示例场景

可以在下的文件夹中查找示例场景 **HandJointChaserExample** 场景 `Assets/MRTK/Examples` `Demos/Input/Scenes/` 。

## <a name="solver-handler"></a>规划求解处理程序

单击 " **跟踪对象以引用** "，然后选择 " **右侧接点** " 或 " **右向右**"。 你将能够看到 **跟踪** 的 "向下移动" 下拉。 从下拉列表中，可以选择要跟踪的特定联合。此示例场景使用径向视图规划求解来使对象跟随目标对象。 有关更多详细信息，请参阅 " [规划求解](../ux-building-blocks/solvers/solver.md) " 页。

![手动组合求解器](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
