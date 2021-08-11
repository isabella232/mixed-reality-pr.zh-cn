---
title: 追踪菜单
description: MRTK 中靠近菜单类型的概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 附近菜单，
ms.openlocfilehash: 75e7ee195a5838e88c42b7547e7b75205bfe1ee2fa1c8b1ba0a868b294883347
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190609"
---
# <a name="near-menu"></a>追踪菜单

![追踪菜单](../images/near-menu/MRTK_UX_NearMenu.png)

"近菜单"是一个 UX 控件，它提供按钮或其他 UI 组件的集合。 它围绕用户正文浮动，随时易于访问。 由于它与用户松散耦合，因此不会妨碍用户与目标内容的交互。 用户可以使用"固定"按钮来锁定/解锁菜单。 可以抓取菜单，并放置在特定位置。

## <a name="interaction-behavior"></a>交互行为

- **标记：** 菜单将跟随你，并保持在 30-60cm 范围内，与用户进行近场交互。
- **固定**：使用"固定"按钮，菜单可以全球锁定并释放。
- **抓取和移动**：菜单始终可抓取且可移动。 无论之前的状态如何，在抓取和释放 (菜单) 锁定菜单。 可抓取区域有视觉提示。 它们公开在手部邻近性。

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a>预制

"近菜单"预制件旨在演示如何使用 MRTK 的各种组件生成用于近交互的菜单。

- **NearMenu2x4.prefab**
- **NearMenu3x1.prefab**
- **NearMenu3x2.prefab**
- **NearMenu3x3.prefab**
- **NearMenu4x1.prefab**
- **NearMenu4x2.prefab**

## <a name="example-scene"></a>示例场景

可以在场景中找到"近菜单"预制项 `NearMenuExamples` 的示例。

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a>结构

近菜单预制件由以下 MRTK 组件构成。

- [**PressableButtonHoloLens2**](button.md) 预制
- [**网格对象集合**](object-collection.md)：网格中的多个按钮布局
- [**操作处理程序**](manipulation-handler.md)：抓取并移动菜单
- [**RadialView 求解器**](solvers/solver.md)：跟踪 (跟踪标记) 行为

![近菜单预制](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a>如何自定义

**1.添加/删除按钮**

在 `ButtonCollection` "对象"下，添加或删除按钮。  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

**2.更新网格对象集合**

单击 `Update Collection` 对象的检查器中的 `ButtonCollection` 按钮。 它将更新网格布局。  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

可以使用 Grid 对象集合的 属性 `Rows` 配置行数。  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

**3.调整反板大小**

调整 下 对象 `Quad` `Backplate` 的大小。 底板的宽度和高度应为 `0.032 * [Number of the buttons + 1]` 。 例如，如果有 3 x 2 个按钮，则底板的宽度为 `0.032 * 4` ，高度为 `0.032 * 3` 。 可以直接将此表达式放入 Unity 的 字段中。  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- 按钮的默认大小HoloLens 2为 3.2x3.2 cm (0.032m) 

## <a name="see-also"></a>另请参阅

- [**按钮**](button.md)
- [**边界控件**](bounds-control.md)
- [**滑块**](sliders.md)
- [**网格对象集合**](object-collection.md)
- [**操作处理程序**](manipulation-handler.md)
- [**RadialView 求解器**](solvers/solver.md)
