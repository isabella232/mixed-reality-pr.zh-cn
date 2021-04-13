---
title: 对象集合
description: 对象集合是一个布局控件，可帮助您在预定义的三维形状中布局对象的数组。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，控制，设计，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens，对象集合，二维，3D，MRTK，混合现实工具包
ms.openlocfilehash: 109dcd59a2b52a8eec82096c5aa88cd1070f5649
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299722"
---
# <a name="object-collection"></a><span data-ttu-id="bdb37-104">对象集合</span><span class="sxs-lookup"><span data-stu-id="bdb37-104">Object collection</span></span>

![在元素应用的定期表中使用的对象集合](images/UX_Hero_ObjectCollection.jpg)<br>

<span data-ttu-id="bdb37-106">对象集合是一个布局控件，可帮助您在预定义的三维形状中布局对象的数组。</span><span class="sxs-lookup"><span data-stu-id="bdb37-106">Object collection is a layout control, which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="bdb37-107">它支持各种表面样式-\* \* 平面、圆柱、球面和 **放射状**。</span><span class="sxs-lookup"><span data-stu-id="bdb37-107">It supports various surface styles - \*\*plane, cylinder, sphere, and **radial**.</span></span> <span data-ttu-id="bdb37-108">您可以调整对象的半径和大小以及它们之间的空间。</span><span class="sxs-lookup"><span data-stu-id="bdb37-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="bdb37-109">对象集合支持从 Unity （二维和三维）的任何对象。</span><span class="sxs-lookup"><span data-stu-id="bdb37-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="bdb37-110">在 **[混合现实工具包](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** 中，我们已创建了 Unity 脚本和示例，可帮助您创建对象集合。</span><span class="sxs-lookup"><span data-stu-id="bdb37-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="bdb37-111">对象集合示例</span><span class="sxs-lookup"><span data-stu-id="bdb37-111">Object collection examples</span></span>

<span data-ttu-id="bdb37-112">[元素的周期性表](../develop/unity/periodic-table-of-the-elements.md) 是一个示例应用程序，演示了对象集合的工作方式。</span><span class="sxs-lookup"><span data-stu-id="bdb37-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="bdb37-113">它使用对象集合来布局不同形状中的3D 化学元素框。</span><span class="sxs-lookup"><span data-stu-id="bdb37-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="bdb37-114">![在元素应用的定期表中显示的对象集合示例](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bdb37-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="bdb37-115">*在元素示例应用的定期表中显示的对象集合示例*</span><span class="sxs-lookup"><span data-stu-id="bdb37-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="bdb37-116">三维对象</span><span class="sxs-lookup"><span data-stu-id="bdb37-116">3D objects</span></span>

<span data-ttu-id="bdb37-117">可以使用对象集合对导入的3D 对象进行布局。</span><span class="sxs-lookup"><span data-stu-id="bdb37-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="bdb37-118">下面的示例显示了一些3D 椅子对象的平面和圆柱布局。</span><span class="sxs-lookup"><span data-stu-id="bdb37-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="bdb37-119">![三维对象的平面和圆柱形布局示例](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bdb37-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="bdb37-120">*三维对象的平面和圆柱形布局示例*</span><span class="sxs-lookup"><span data-stu-id="bdb37-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="bdb37-121">2D 对象</span><span class="sxs-lookup"><span data-stu-id="bdb37-121">2D objects</span></span>

<span data-ttu-id="bdb37-122">您还可以将2D 图像与对象集合一起使用。</span><span class="sxs-lookup"><span data-stu-id="bdb37-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="bdb37-123">下面的示例演示如何在网格中显示2D 图像。</span><span class="sxs-lookup"><span data-stu-id="bdb37-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![使用对象集合的2D 图像示例](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="bdb37-125">![将对象集合与2D 图像一起使用的示例](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="bdb37-125">![Examples of using object collection with 2D images](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="bdb37-126">*将对象集合与2D 图像一起使用的示例*</span><span class="sxs-lookup"><span data-stu-id="bdb37-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="bdb37-127">MRTK 中的对象集合 (适用于 Unity 的混合现实工具包) </span><span class="sxs-lookup"><span data-stu-id="bdb37-127">Object collection in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="bdb37-128">MRTK-对象集合</span><span class="sxs-lookup"><span data-stu-id="bdb37-128">MRTK - Object collection</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection)

<br>

---

## <a name="see-also"></a><span data-ttu-id="bdb37-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bdb37-129">See also</span></span>

* [<span data-ttu-id="bdb37-130">光标</span><span class="sxs-lookup"><span data-stu-id="bdb37-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="bdb37-131">手部射线</span><span class="sxs-lookup"><span data-stu-id="bdb37-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="bdb37-132">Button</span><span class="sxs-lookup"><span data-stu-id="bdb37-132">Button</span></span>](button.md)
* [<span data-ttu-id="bdb37-133">可交互对象</span><span class="sxs-lookup"><span data-stu-id="bdb37-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="bdb37-134">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="bdb37-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="bdb37-135">操作</span><span class="sxs-lookup"><span data-stu-id="bdb37-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="bdb37-136">手动菜单</span><span class="sxs-lookup"><span data-stu-id="bdb37-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="bdb37-137">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="bdb37-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="bdb37-138">对象集合</span><span class="sxs-lookup"><span data-stu-id="bdb37-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="bdb37-139">语音命令</span><span class="sxs-lookup"><span data-stu-id="bdb37-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="bdb37-140">键盘</span><span class="sxs-lookup"><span data-stu-id="bdb37-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="bdb37-141">工具提示</span><span class="sxs-lookup"><span data-stu-id="bdb37-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="bdb37-142">平板</span><span class="sxs-lookup"><span data-stu-id="bdb37-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="bdb37-143">滑块</span><span class="sxs-lookup"><span data-stu-id="bdb37-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="bdb37-144">着色器</span><span class="sxs-lookup"><span data-stu-id="bdb37-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="bdb37-145">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="bdb37-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="bdb37-146">显示进度</span><span class="sxs-lookup"><span data-stu-id="bdb37-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="bdb37-147">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="bdb37-147">Surface magnetism</span></span>](surface-magnetism.md)
