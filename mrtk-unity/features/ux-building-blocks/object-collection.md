---
title: 对象集合
description: MRTK 中的对象集合概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，对象集合，
ms.openlocfilehash: 8390e9c4a7bd419f99a5c8c4af7e7a2eca1d8f3f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177056"
---
# <a name="object-collection"></a>对象集合

![对象集合](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

对象集合是一个脚本，用于帮助布局预定义三维形状中的对象数组。 它支持各种表面样式，包括平面、圆柱、球面和放射状。 由于它支持 Unity 中的任何对象，因此它可用于布局二维和三维对象。

## <a name="object-collection-scripts"></a>对象集合脚本

- [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 支持圆柱体、平面、球、径向曲面类型
- [`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) 支持分散样式集合  
- [`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) 向 GridObjectCollection 提供了一些其他选项。 **注意：** TileGridObjectCollection 未扩展 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) ，并且有多个 bug (参阅 [问题 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)) 。 因此，建议使用 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 。

|![网格对象集合-圆柱形](../images/object-collection/MRTK_ObjectCollectionCylinder.png) 网格对象集合-圆柱形 | ![网格对象集合-球体](../images/object-collection/MRTK_ObjectCollectionSphere.png) 网格对象集合-球体 |
|:--- | :--- |
|![网格对象集合-放射形](../images/object-collection/MRTK_ObjectCollectionRadial.png) 网格对象集合-放射形 | ![网格对象集合-平面](../images/object-collection/MRTK_ObjectCollectionPlane.png) 网格对象集合-平面 |
|![分散的对象集合](../images/object-collection/MRTK_ObjectCollectionScattered.png) 分散的对象集合 | ![磁贴网格对象集合](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) 磁贴网格对象集合 |

## <a name="how-to-use-an-object-collection"></a>如何使用对象集合

若要创建集合，请创建一个空的 GameObject 并为其分配一个对象集合脚本。 任何 () 的对象都可以添加为 GameObject 的子级。 添加完子对象后，单击 "检查器" 面板中的 " *更新集合* " 按钮以生成对象集合。 对象将根据集合参数在场景中进行布局。 还可以通过代码访问更新集合。

![对象集合脚本](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a>`GridObjectCollection` 内容对齐

可以对齐 GridObjectCollection 中的内容，以便将父对象锚定到集合的顶部/中间/下和左/中。 使用 " **定位点** " 属性可以指定内容对齐方式。

## <a name="gridobjectcollection-layout-order"></a>`GridObjectCollection` 布局顺序

使用 " **布局** " 字段可以指定子项布局的行/列顺序：

首先，第一列的第一 **列** 是布局，第一列按) 水平 (，然后按行) 垂直 (。 使用 "代码) 中 (或" 列 "属性中的" **数字列** "可以指定网格中的列数。

![列 then 行布局](../images/object-collection/MRTK_ColumnThenRow.png)

**行 Then 列** -子级首先按行) 垂直布局 (，然后水平 (按列) 。 在代码) 中 (或 Rows 属性使用 **Num rows** 来指定网格中的行数。

![行 then 列布局](../images/object-collection/MRTK_RowThenColumn.png)

**水平** -子级仅使用列在单个行中布局

**垂直** -子级仅使用行在单个列中进行布局。

## <a name="object-collection-examples"></a>对象集合示例

`ObjectCollectionExamples` (资产/MRTK/示例/演示/UX/集合/场景/ObjectCollectionExamples) 示例场景包含对象集合类型的各种示例。

[定期表元素](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) 是一个示例应用，演示对象集合的工作方式。 它使用对象集合来布局不同形状中的三维元素框。

## <a name="object-collection-types"></a>对象集合类型

**三维对象**

对象集合可用于对导入的3D 对象进行布局。 下面的示例使用集合显示三维椅子模型对象的平面和圆柱形布局。

![对象集合三维](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

**2D 对象**

还可以从2D 图像创建对象集合。 例如，可以在网格样式中放置多个图像。

![对象集合2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
