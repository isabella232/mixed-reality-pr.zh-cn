---
title: 靠接
description: 停靠控件的说明。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 4446dbe3199aab63d7ee85474d3696a45cf4401f1d8100a8d99885a7265c7fe2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226569"
---
# <a name="dock"></a>靠接

![靠接](../images/dock/MRTK_UX_Dock_Main.png)

此控件允许将对象移进和移出预先确定的位置，以创建调色板、架子和导航栏。

## <a name="features"></a>功能

- 支持任意数目的停靠位置和布局 ([`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 非常适用于) 
- 停靠的对象会自动离开，以为新对象提供空间
- 对象缩放以适合停靠的空间，然后在拖动时调整到其原始位置。

## <a name="getting-started-with-dock"></a>Dock 入门

- 使用 Dock 组件创建 GameObject，并添加一些子 GameObject。
- 将 DockPosition 组件添加到每个子项。
- 将可停靠组件添加到场景中任意数目的对象，以允许它们停靠。 它们还必须 [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) 具有组件和碰撞体。
- *可选* ：使用 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 到 Dock 的 自动布局 DockPositions。

### <a name="prerequisites"></a>先决条件

- 每个可停靠对象必须具有具有 或 的 [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) 碰撞体 [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) 。
- 如果希望对象在场景加载时启动 Docked，请将其分配给 DockPosition 的任何停靠对象属性。

## <a name="how-it-works"></a>工作原理

可停靠组件基于操作事件而构建，以允许拖动的对象停靠和移除特定位置。 放置由与拖动对象最近的重叠触发的 DockPosition 确定，因此两个对象都需要有碰撞体才能激活触发器。
