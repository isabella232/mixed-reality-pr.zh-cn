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
# <a name="object-collection"></a><span data-ttu-id="7606a-104">对象集合</span><span class="sxs-lookup"><span data-stu-id="7606a-104">Object collection</span></span>

![对象集合](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

<span data-ttu-id="7606a-106">对象集合是一个脚本，用于帮助布局预定义三维形状中的对象数组。</span><span class="sxs-lookup"><span data-stu-id="7606a-106">Object collection is a script to help lay out an array of objects in predefined three-dimensional shapes.</span></span> <span data-ttu-id="7606a-107">它支持各种表面样式，包括平面、圆柱、球面和放射状。</span><span class="sxs-lookup"><span data-stu-id="7606a-107">It supports various surface styles including plane, cylinder, sphere, and radial.</span></span> <span data-ttu-id="7606a-108">由于它支持 Unity 中的任何对象，因此它可用于布局二维和三维对象。</span><span class="sxs-lookup"><span data-stu-id="7606a-108">Since it supports any object in Unity, it can be used to layout both 2D and 3D objects.</span></span>

## <a name="object-collection-scripts"></a><span data-ttu-id="7606a-109">对象集合脚本</span><span class="sxs-lookup"><span data-stu-id="7606a-109">Object collection scripts</span></span>

- <span data-ttu-id="7606a-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 支持圆柱体、平面、球、径向曲面类型</span><span class="sxs-lookup"><span data-stu-id="7606a-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) supports Cylinder, Plane, Sphere, Radial surface types</span></span>
- <span data-ttu-id="7606a-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) 支持分散样式集合</span><span class="sxs-lookup"><span data-stu-id="7606a-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) supports scattered style collection</span></span>  
- <span data-ttu-id="7606a-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) 向 GridObjectCollection 提供了一些其他选项。</span><span class="sxs-lookup"><span data-stu-id="7606a-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) provides some additional options to GridObjectCollection.</span></span> <span data-ttu-id="7606a-113">**注意：** TileGridObjectCollection 未扩展 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) ，并且有多个 bug (参阅 [问题 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)) 。</span><span class="sxs-lookup"><span data-stu-id="7606a-113">**Note:** TileGridObjectCollection does not extend [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection), and has several bugs (see [issue 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)).</span></span> <span data-ttu-id="7606a-114">因此，建议使用 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 。</span><span class="sxs-lookup"><span data-stu-id="7606a-114">Therefore, it is recommended to use [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection).</span></span>

|![网格对象集合-圆柱形](../images/object-collection/MRTK_ObjectCollectionCylinder.png) <span data-ttu-id="7606a-116">网格对象集合-圆柱形</span><span class="sxs-lookup"><span data-stu-id="7606a-116">Grid Object Collection - Cylinder</span></span> | ![网格对象集合-球体](../images/object-collection/MRTK_ObjectCollectionSphere.png) <span data-ttu-id="7606a-118">网格对象集合-球体</span><span class="sxs-lookup"><span data-stu-id="7606a-118">Grid Object Collection - Sphere</span></span> |
|:--- | :--- |
|![网格对象集合-放射形](../images/object-collection/MRTK_ObjectCollectionRadial.png) <span data-ttu-id="7606a-120">网格对象集合-放射形</span><span class="sxs-lookup"><span data-stu-id="7606a-120">Grid Object Collection - Radial</span></span> | ![网格对象集合-平面](../images/object-collection/MRTK_ObjectCollectionPlane.png) <span data-ttu-id="7606a-122">网格对象集合-平面</span><span class="sxs-lookup"><span data-stu-id="7606a-122">Grid Object Collection - Plane</span></span> |
|![分散的对象集合](../images/object-collection/MRTK_ObjectCollectionScattered.png) <span data-ttu-id="7606a-124">分散的对象集合</span><span class="sxs-lookup"><span data-stu-id="7606a-124">Scattered Object Collection</span></span> | ![磁贴网格对象集合](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) <span data-ttu-id="7606a-126">磁贴网格对象集合</span><span class="sxs-lookup"><span data-stu-id="7606a-126">Tile Grid Object Collection</span></span> |

## <a name="how-to-use-an-object-collection"></a><span data-ttu-id="7606a-127">如何使用对象集合</span><span class="sxs-lookup"><span data-stu-id="7606a-127">How to use an object collection</span></span>

<span data-ttu-id="7606a-128">若要创建集合，请创建一个空的 GameObject 并为其分配一个对象集合脚本。</span><span class="sxs-lookup"><span data-stu-id="7606a-128">To create a collection, create an empty GameObject and assign one of the Object Collection scripts to it.</span></span> <span data-ttu-id="7606a-129">任何 () 的对象都可以添加为 GameObject 的子级。</span><span class="sxs-lookup"><span data-stu-id="7606a-129">Any object(s) can be added as a child of the GameObject.</span></span> <span data-ttu-id="7606a-130">添加完子对象后，单击 "检查器" 面板中的 " *更新集合* " 按钮以生成对象集合。</span><span class="sxs-lookup"><span data-stu-id="7606a-130">Once finished adding child objects, click the *Update Collection* button in the inspector panel to generate the object collection.</span></span> <span data-ttu-id="7606a-131">对象将根据集合参数在场景中进行布局。</span><span class="sxs-lookup"><span data-stu-id="7606a-131">The objects will be laid out in the scene according to the collection parameters.</span></span> <span data-ttu-id="7606a-132">还可以通过代码访问更新集合。</span><span class="sxs-lookup"><span data-stu-id="7606a-132">Update Collection can be accessed through the code too.</span></span>

![对象集合脚本](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a><span data-ttu-id="7606a-134">`GridObjectCollection` 内容对齐</span><span class="sxs-lookup"><span data-stu-id="7606a-134">`GridObjectCollection` content alignment</span></span>

<span data-ttu-id="7606a-135">可以对齐 GridObjectCollection 中的内容，以便将父对象锚定到集合的顶部/中间/下和左/中。</span><span class="sxs-lookup"><span data-stu-id="7606a-135">The content in a GridObjectCollection can be aligned so that the parent object is anchored to the top/middle/bottom and left/center/right of the collection.</span></span> <span data-ttu-id="7606a-136">使用 " **定位点** " 属性可以指定内容对齐方式。</span><span class="sxs-lookup"><span data-stu-id="7606a-136">Use the **anchor** property to specify content alignment.</span></span>

## <a name="gridobjectcollection-layout-order"></a><span data-ttu-id="7606a-137">`GridObjectCollection` 布局顺序</span><span class="sxs-lookup"><span data-stu-id="7606a-137">`GridObjectCollection` layout order</span></span>

<span data-ttu-id="7606a-138">使用 " **布局** " 字段可以指定子项布局的行/列顺序：</span><span class="sxs-lookup"><span data-stu-id="7606a-138">Use the **Layout** field to specify the row / column order that children are laid out:</span></span>

<span data-ttu-id="7606a-139">首先，第一列的第一 **列** 是布局，第一列按) 水平 (，然后按行) 垂直 (。</span><span class="sxs-lookup"><span data-stu-id="7606a-139">**Column Then Row** - Children are first laid out by horizontally (by column), then vertically (by row).</span></span> <span data-ttu-id="7606a-140">使用 "代码) 中 (或" 列 "属性中的" **数字列** "可以指定网格中的列数。</span><span class="sxs-lookup"><span data-stu-id="7606a-140">Use **Num Columns** (or Columns property in code) to specify the number of columns in the grid.</span></span>

![列 then 行布局](../images/object-collection/MRTK_ColumnThenRow.png)

<span data-ttu-id="7606a-142">**行 Then 列** -子级首先按行) 垂直布局 (，然后水平 (按列) 。</span><span class="sxs-lookup"><span data-stu-id="7606a-142">**Row Then Column** - Children are first laid out vertically (by row), then horizontally (by columns).</span></span> <span data-ttu-id="7606a-143">在代码) 中 (或 Rows 属性使用 **Num rows** 来指定网格中的行数。</span><span class="sxs-lookup"><span data-stu-id="7606a-143">Use **Num Rows** (or Rows property in code) to specify the number of rows in the grid.</span></span>

![行 then 列布局](../images/object-collection/MRTK_RowThenColumn.png)

<span data-ttu-id="7606a-145">**水平** -子级仅使用列在单个行中布局</span><span class="sxs-lookup"><span data-stu-id="7606a-145">**Horizontal** - Children are laid out in a single row using columns only</span></span>

<span data-ttu-id="7606a-146">**垂直** -子级仅使用行在单个列中进行布局。</span><span class="sxs-lookup"><span data-stu-id="7606a-146">**Vertical** - Children are laid out in a single column using rows only.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="7606a-147">对象集合示例</span><span class="sxs-lookup"><span data-stu-id="7606a-147">Object collection examples</span></span>

<span data-ttu-id="7606a-148">`ObjectCollectionExamples` (资产/MRTK/示例/演示/UX/集合/场景/ObjectCollectionExamples) 示例场景包含对象集合类型的各种示例。</span><span class="sxs-lookup"><span data-stu-id="7606a-148">The `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) example scene contains various examples of object collection types.</span></span>

<span data-ttu-id="7606a-149">[定期表元素](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) 是一个示例应用，演示对象集合的工作方式。</span><span class="sxs-lookup"><span data-stu-id="7606a-149">[Periodic table of the elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an example app that demonstrates how object collections work.</span></span> <span data-ttu-id="7606a-150">它使用对象集合来布局不同形状中的三维元素框。</span><span class="sxs-lookup"><span data-stu-id="7606a-150">It uses object collection to layout the 3D element boxes in different shapes.</span></span>

## <a name="object-collection-types"></a><span data-ttu-id="7606a-151">对象集合类型</span><span class="sxs-lookup"><span data-stu-id="7606a-151">Object collection types</span></span>

<span data-ttu-id="7606a-152">**三维对象**</span><span class="sxs-lookup"><span data-stu-id="7606a-152">**3D objects**</span></span>

<span data-ttu-id="7606a-153">对象集合可用于对导入的3D 对象进行布局。</span><span class="sxs-lookup"><span data-stu-id="7606a-153">An object collection can be used to layout imported 3D objects.</span></span> <span data-ttu-id="7606a-154">下面的示例使用集合显示三维椅子模型对象的平面和圆柱形布局。</span><span class="sxs-lookup"><span data-stu-id="7606a-154">The example below shows the plane and cylindrical layouts of 3D chair model objects using a collection.</span></span>

![对象集合三维](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

<span data-ttu-id="7606a-156">**2D 对象**</span><span class="sxs-lookup"><span data-stu-id="7606a-156">**2D Objects**</span></span>

<span data-ttu-id="7606a-157">还可以从2D 图像创建对象集合。</span><span class="sxs-lookup"><span data-stu-id="7606a-157">An object collection can also be crated from 2D images.</span></span> <span data-ttu-id="7606a-158">例如，可以在网格样式中放置多个图像。</span><span class="sxs-lookup"><span data-stu-id="7606a-158">For example, multiple images can be placed in a grid style.</span></span>

![对象集合2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
