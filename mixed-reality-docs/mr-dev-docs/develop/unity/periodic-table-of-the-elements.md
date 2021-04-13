---
title: 元素周期表
description: 了解如何使用不同的图面类型在三维空间布局对象的数组，使用带有元素示例应用的定期表的对象集合。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计，示例应用，控件，MRTK，混合现实工具包，Unity，示例应用，示例应用，开源，Microsoft Store，HoloLens，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: 36491d230f9d236db77f34b9540f19609c7619ef
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300172"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="e12b3-104">元素周期表</span><span class="sxs-lookup"><span data-stu-id="e12b3-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="e12b3-105">本文讨论了我们在 [混合现实设计实验室](https://github.com/Microsoft/MRDesignLabs_Unity)中创建的探索示例，这是我们与混合现实应用开发的知识和建议。</span><span class="sxs-lookup"><span data-stu-id="e12b3-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="e12b3-106">我们设计相关的文章和代码将随着我们的新发现而发展。</span><span class="sxs-lookup"><span data-stu-id="e12b3-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="e12b3-107">[定期表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) 是 Microsoft 混合现实设计实验室的开源示例应用。</span><span class="sxs-lookup"><span data-stu-id="e12b3-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="e12b3-108">了解如何使用 **[对象集合](../../design/object-collection.md)** 在三维空间中布局对象的数组。</span><span class="sxs-lookup"><span data-stu-id="e12b3-108">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="e12b3-109">还将了解如何创建响应 HoloLens 标准输入的种不可交互对象。</span><span class="sxs-lookup"><span data-stu-id="e12b3-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="e12b3-110">您可以使用此项目的组件来创建自己的混合现实应用程序体验。</span><span class="sxs-lookup"><span data-stu-id="e12b3-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![元素应用的 Period 表](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="e12b3-112">演示视频</span><span class="sxs-lookup"><span data-stu-id="e12b3-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="e12b3-113">使用混合现实捕获记录了 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e12b3-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="e12b3-114">关于应用</span><span class="sxs-lookup"><span data-stu-id="e12b3-114">About the app</span></span>

<span data-ttu-id="e12b3-115">元素的周期性表在三维空间中直观显示化学元素及其每个属性。</span><span class="sxs-lookup"><span data-stu-id="e12b3-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="e12b3-116">它结合了 HoloLens 的基本交互，如注视和分流。</span><span class="sxs-lookup"><span data-stu-id="e12b3-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="e12b3-117">用户可以了解带有动画3D 模型的元素。</span><span class="sxs-lookup"><span data-stu-id="e12b3-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="e12b3-118">它们可以直观地了解元素的 electron shell 及其核心，这是由 protons 和 neutrons 组成的。</span><span class="sxs-lookup"><span data-stu-id="e12b3-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="e12b3-119">背景</span><span class="sxs-lookup"><span data-stu-id="e12b3-119">Background</span></span>

<span data-ttu-id="e12b3-120">在我首次体验 HoloLens 后，我知道我想在混合现实中试用定期表应用程序。</span><span class="sxs-lookup"><span data-stu-id="e12b3-120">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="e12b3-121">由于每个元素都有多个与文本一起显示的数据点，因此，我认为这对于浏览三维空间中的排版组合非常重要。</span><span class="sxs-lookup"><span data-stu-id="e12b3-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="e12b3-122">使用户有机会直观显示元素的 electron 模型是此项目的另一个有趣的部分。</span><span class="sxs-lookup"><span data-stu-id="e12b3-122">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="e12b3-123">设计</span><span class="sxs-lookup"><span data-stu-id="e12b3-123">Design</span></span>

<span data-ttu-id="e12b3-124">对于周期性表的默认视图，我想要将包含每个元素的 electron 模型的三维方框。</span><span class="sxs-lookup"><span data-stu-id="e12b3-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="e12b3-125">每个框的表面都是透明的，这样用户就可以大致了解元素的音量。</span><span class="sxs-lookup"><span data-stu-id="e12b3-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="e12b3-126">使用注视和空中点击，用户可以打开每个元素的详细视图。</span><span class="sxs-lookup"><span data-stu-id="e12b3-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="e12b3-127">为了使表视图和详细信息视图之间的过渡平滑和自然，我使其类似于实际生活中打开的方框的物理交互。</span><span class="sxs-lookup"><span data-stu-id="e12b3-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="e12b3-128">![设计草图](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="e12b3-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="e12b3-129">*设计草图*</span><span class="sxs-lookup"><span data-stu-id="e12b3-129">*Design sketches*</span></span>

<span data-ttu-id="e12b3-130">在详细信息视图中，我想要将每个元素的信息可视化到三维空间中完美呈现的文本。</span><span class="sxs-lookup"><span data-stu-id="e12b3-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="e12b3-131">动画 3D electron 模型将显示在中心区域，并且可以从不同角度查看。</span><span class="sxs-lookup"><span data-stu-id="e12b3-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![交互](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="e12b3-133">![原型](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="e12b3-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="e12b3-134">*交互原型*</span><span class="sxs-lookup"><span data-stu-id="e12b3-134">*Interaction prototypes*</span></span>

<span data-ttu-id="e12b3-135">用户可以通过点击表格底部的按钮来更改曲面类型，它们可以在平面、圆柱、球和散点之间切换。</span><span class="sxs-lookup"><span data-stu-id="e12b3-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="e12b3-136">此应用中使用的公共控件和模式</span><span class="sxs-lookup"><span data-stu-id="e12b3-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="e12b3-137">种不可交互对象 (按钮) </span><span class="sxs-lookup"><span data-stu-id="e12b3-137">Interactable object (button)</span></span>

<span data-ttu-id="e12b3-138">[种不可交互对象](../../design/interactable-object.md) 是一个对象，它可以响应基本的 HoloLens 输入。</span><span class="sxs-lookup"><span data-stu-id="e12b3-138">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="e12b3-139">它作为 prefab/script 提供，你可以轻松地将其应用于任何对象。</span><span class="sxs-lookup"><span data-stu-id="e12b3-139">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="e12b3-140">例如，你可以在场景种不可交互中发出咖啡杯，并对输入（如注视、分流、导航和操作手势）做出响应。</span><span class="sxs-lookup"><span data-stu-id="e12b3-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="e12b3-141">了解详细信息</span><span class="sxs-lookup"><span data-stu-id="e12b3-141">Learn more</span></span>](../../design/interactable-object.md)

![nteractable 对象](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="e12b3-143">对象集合</span><span class="sxs-lookup"><span data-stu-id="e12b3-143">Object collection</span></span>

<span data-ttu-id="e12b3-144">[对象集合](../../design/object-collection.md) 是一个对象，可帮助您在不同的形状中布局多个对象。</span><span class="sxs-lookup"><span data-stu-id="e12b3-144">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="e12b3-145">它支持平面、圆柱、球面和散点图。</span><span class="sxs-lookup"><span data-stu-id="e12b3-145">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="e12b3-146">可以配置其他属性，如 radius、行数和间距。</span><span class="sxs-lookup"><span data-stu-id="e12b3-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="e12b3-147">了解详细信息</span><span class="sxs-lookup"><span data-stu-id="e12b3-147">Learn more</span></span>](../../design/object-collection.md)

![对象集合](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="e12b3-149">技术详细信息</span><span class="sxs-lookup"><span data-stu-id="e12b3-149">Technical details</span></span>

<span data-ttu-id="e12b3-150">可在 [混合现实设计实验室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)上查找元素应用的定期表的脚本和 prototyping。</span><span class="sxs-lookup"><span data-stu-id="e12b3-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="e12b3-151">针对 HoloLens 2 的移植故事</span><span class="sxs-lookup"><span data-stu-id="e12b3-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="e12b3-152">阅读有关如何用 HoloLens 2 的 instinctual 交互更新元素应用的定期表的文章。</span><span class="sxs-lookup"><span data-stu-id="e12b3-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="e12b3-153">元素周期表 2.0</span><span class="sxs-lookup"><span data-stu-id="e12b3-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="e12b3-154">关于作者</span><span class="sxs-lookup"><span data-stu-id="e12b3-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="e12b3-155"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="e12b3-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="e12b3-156">用户体验设计师 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="e12b3-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="e12b3-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e12b3-157">See also</span></span>

* <span data-ttu-id="e12b3-158">[MRTK 示例中心](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="e12b3-158">[MRTK Examples Hub](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="e12b3-159">[表面](sampleapp-surfaces.md) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="e12b3-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="e12b3-160">元素周期表 2.0</span><span class="sxs-lookup"><span data-stu-id="e12b3-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="e12b3-161">星系探索者 2.0</span><span class="sxs-lookup"><span data-stu-id="e12b3-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)