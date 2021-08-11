---
title: 对象集合
description: MRTK 中的对象集合概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 对象集合，
ms.openlocfilehash: 6705bd7093dbcd81912153872e4fd07c703fc5c0b9c081e0287589a7c8e959ac
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197509"
---
# <a name="object-collection"></a>对象集合

![对象集合](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

对象集合是一个脚本，可帮助以预定义的三维形状布局对象的数组。 它支持各种表面样式，包括平面、柱面、球体和径向。 由于它支持 Unity 中的任意对象，因此可用于对 2D 和 3D 对象进行布局。

## <a name="object-collection-scripts"></a>对象集合脚本

- [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 支持柱面、平面、球体、径向表面类型
- [`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) 支持散点样式集合  
- [`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) 为 GridObjectCollection 提供了一些附加选项。 **注意：** TileGridObjectCollection 不会扩展 ，并且有几个 bug (请参阅问题 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) [6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)) 。 因此，建议使用 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 。

|![网格对象集合 - 柱面](../images/object-collection/MRTK_ObjectCollectionCylinder.png) 网格对象集合 - 柱面 | ![网格对象集合 - Sphere](../images/object-collection/MRTK_ObjectCollectionSphere.png) 网格对象集合 - Sphere |
|:--- | :--- |
|![网格对象集合 - 径向](../images/object-collection/MRTK_ObjectCollectionRadial.png) 网格对象集合 - 径向 | ![网格对象集合 - 平面](../images/object-collection/MRTK_ObjectCollectionPlane.png) 网格对象集合 - 平面 |
|![散点对象集合](../images/object-collection/MRTK_ObjectCollectionScattered.png) 散点对象集合 | ![磁贴网格对象集合](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) 磁贴网格对象集合 |

## <a name="how-to-use-an-object-collection"></a>如何使用对象集合

若要创建集合，请创建一个空 GameObject，并为其分配一个对象集合脚本。 任何 (对象) 添加为 GameObject 的子级。 添加完子对象后，单击检查 *器面板* 中的"更新集合"按钮以生成对象集合。 这些对象根据集合参数在场景中布局。 也可通过代码访问更新集合。

![对象集合脚本](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a>`GridObjectCollection` 内容对齐方式

GridObjectCollection 中的内容可以对齐，以便父对象定位到集合的顶部/中间/底部和左侧/中心/右侧。 使用 **定位点** 属性指定内容对齐方式。

## <a name="gridobjectcollection-layout-order"></a>`GridObjectCollection` 布局顺序

使用 **"布局** "字段指定子元素布局的行/列顺序：

**列后行** - 子级首先按列 (水平布局) ，然后 (按行) 。 在 **代码中** 使用 (列数或列) 指定网格中的列数。

![列，然后行布局](../images/object-collection/MRTK_ColumnThenRow.png)

**Row Then Column** - 子级首先按行 (垂直布局) ，然后按 (列) 。 在 **代码中** (行数或行) 指定网格中的行数。

![行，然后是列布局](../images/object-collection/MRTK_RowThenColumn.png)

**水平** - 子级仅在使用列的单个行中布局

**垂直** - 子级仅在使用行的单个列中布局。

## <a name="object-collection-examples"></a>对象集合示例

 (`ObjectCollectionExamples` Assets/MRTK/Examples/Demos/UX/Collections/Scene/ObjectCollectionExamples.unity) 示例场景包含对象集合类型的各种示例。

[元素的周期表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) 是一个示例应用，演示对象集合如何工作。 它使用对象集合以不同形状布局 3D 元素框。

## <a name="object-collection-types"></a>对象集合类型

**3D 对象**

对象集合可用于对导入的 3D 对象进行布局。 以下示例显示了使用 集合的 3D 长板模型对象的平面和圆条布局。

![对象集合 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

**2D 对象**

也可以从 2D 图像对对象集合进行计算。 例如，可以将多个图像置于网格样式中。

![对象集合 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
