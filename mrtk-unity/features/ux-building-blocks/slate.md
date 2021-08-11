---
title: 平板
description: 有关 MRTK 中的 Slate 的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， Slate，
ms.openlocfilehash: 6bc1f18c71367ce05aadae0ff3f8aa51fd17d10c943022525fc5043d8d7989a2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224010"
---
# <a name="slate"></a>平板

![平板](../images/slate/MRTK_Slate_Main.png)

Slate 预制件提供用于显示 2D 内容的精简窗口样式控件，例如纯文本或包含媒体的文章。 它提供了可抓取的标题栏以及" *关注我"* 和" *关闭"* 功能。 可以通过手部输入滚动内容窗口。

## <a name="how-to-use-a-slate-control"></a>如何使用平板电脑控件

板板控件由以下元素组成：

* **TitleBar：** 平板电脑顶部的整个标题栏。
* **标题**：标题栏左侧的标题区域。
* **按钮**：标题栏右侧按钮区域。
* **BackPlate：** 板的背面。
* **ContentQuad：** 内容分配为材料。 该示例使用示例材料"PanContent"。

<img src="../images/slate/MRTK_SlateStructure.jpg" width="650" alt="Slate Structure in the Unity editor">

## <a name="bounds-control"></a>边界控制

平板电脑控件包含用于缩放和旋转的边界控制脚本。 有关边界控件详细信息，请参阅 [边界控件](bounds-control.md) 页。

<img src="../images/slate/MRTK_Slate_BB.jpg" width="650" alt="Slate BB">

## <a name="buttons"></a>按钮

标准版板在标题栏的右上方提供两个默认按钮：

* **跟随我**：切换轨道求解器组件，使板对象跟随用户。
* **关闭**：禁用板对象。

<img src="../images/slate/MRTK_Slate_Buttons.jpg" width="650" alt="Slate Button">

## <a name="scripts"></a>脚本

一般情况下，脚本必须附加到任何旨在接收 来自 `NearInteractionTouchable.cs` 的触摸事件的对象 `IMixedRealityTouchHandler` 。

<img src="../images/slate/MRTK_Slate_Scripts.png" alt="Slate Structure">

* `HandInteractionPan.cs` 此脚本处理用于触摸和移动平板电脑 *ContentQuad* 上的内容的表达式手动输入。

* `HandInteractionPanZoom.cs`：除了平移交互，此脚本还支持两手缩放。

<img src="../images/slate/MRTK_Slate_PanZoom.png" width="500" alt="Slate Pan Zooming">
