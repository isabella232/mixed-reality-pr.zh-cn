---
title: 元素周期表
description: 了解如何将对象集合与元素周期表示例应用一起，在具有各种图面类型的 3D 空间中布局对象数组。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality， 设计， 示例应用， 控件， MRTK， 混合现实工具包， Unity， 示例应用， 示例应用， 开源， Microsoft Store， HoloLens， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
ms.openlocfilehash: ed8c35fc6467322c25b92924b134f176fa4a9b47
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743412"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="73d0c-104">元素周期表</span><span class="sxs-lookup"><span data-stu-id="73d0c-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="73d0c-105">本文讨论我们在混合现实设计实验室中创建的探索示例，我们在该实验室[](https://github.com/Microsoft/MRDesignLabs_Unity)中分享有关混合现实应用开发的学习和建议。</span><span class="sxs-lookup"><span data-stu-id="73d0c-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="73d0c-106">随着我们进行新的发现，与设计相关的文章和代码将不断发展。</span><span class="sxs-lookup"><span data-stu-id="73d0c-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="73d0c-107">[元素周期表是](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) Microsoft 混合现实设计实验室提供的开源示例应用。</span><span class="sxs-lookup"><span data-stu-id="73d0c-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="73d0c-108">了解如何使用对象集合 在具有各种图面类型的 3D 空间中布局 **[对象的数组](../../design/object-collection.md)**。</span><span class="sxs-lookup"><span data-stu-id="73d0c-108">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="73d0c-109">另请了解如何创建可交互对象，以响应 HoloLens 中的标准输入。</span><span class="sxs-lookup"><span data-stu-id="73d0c-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="73d0c-110">可以使用此项目的组件创建自己的混合现实应用体验。</span><span class="sxs-lookup"><span data-stu-id="73d0c-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Elements 应用的周期表](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="73d0c-112">演示视频</span><span class="sxs-lookup"><span data-stu-id="73d0c-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="73d0c-113">使用 HoloLens 2 记录混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="73d0c-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="73d0c-114">关于应用</span><span class="sxs-lookup"><span data-stu-id="73d0c-114">About the app</span></span>

<span data-ttu-id="73d0c-115">元素周期表将三维空间中化学元素及其每个属性可视化。</span><span class="sxs-lookup"><span data-stu-id="73d0c-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="73d0c-116">它结合了 HoloLens 的基本交互，例如凝视和敲击。</span><span class="sxs-lookup"><span data-stu-id="73d0c-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="73d0c-117">用户可以了解具有动画 3D 模型的元素。</span><span class="sxs-lookup"><span data-stu-id="73d0c-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="73d0c-118">它们可以直观地了解元素的电子外壳及其由质子和中子组成。</span><span class="sxs-lookup"><span data-stu-id="73d0c-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="73d0c-119">背景</span><span class="sxs-lookup"><span data-stu-id="73d0c-119">Background</span></span>

<span data-ttu-id="73d0c-120">我第一次体验 HoloLens 后，知道我想在混合现实中试验定期表应用。</span><span class="sxs-lookup"><span data-stu-id="73d0c-120">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="73d0c-121">由于每个元素都有许多以文本显示的数据点，因此我认为在 3D 空间中浏览版式撰写是一个很好的主题。</span><span class="sxs-lookup"><span data-stu-id="73d0c-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="73d0c-122">为用户提供可视化元素电子模型的机会是此项目的另一个有趣部分。</span><span class="sxs-lookup"><span data-stu-id="73d0c-122">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="73d0c-123">设计</span><span class="sxs-lookup"><span data-stu-id="73d0c-123">Design</span></span>

<span data-ttu-id="73d0c-124">对于周期表的默认视图，我假设三维框将包含每个元素的电子模型。</span><span class="sxs-lookup"><span data-stu-id="73d0c-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="73d0c-125">每个框的图面是半透明的，以便用户可以大致了解元素的音量。</span><span class="sxs-lookup"><span data-stu-id="73d0c-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="73d0c-126">通过凝视和敲击，用户可以打开每个元素的详细视图。</span><span class="sxs-lookup"><span data-stu-id="73d0c-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="73d0c-127">为了在表视图和详细信息视图之间顺利且自然地转换，我使其类似于实际打开的框的物理交互。</span><span class="sxs-lookup"><span data-stu-id="73d0c-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="73d0c-128">![设计草图](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="73d0c-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="73d0c-129">*设计草图*</span><span class="sxs-lookup"><span data-stu-id="73d0c-129">*Design sketches*</span></span>

<span data-ttu-id="73d0c-130">在详细信息视图中，我想要使用 3D 空间中美观呈现的文本可视化每个元素的信息。</span><span class="sxs-lookup"><span data-stu-id="73d0c-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="73d0c-131">动画 3D 电子模型显示在中心区域，可以从不同角度查看。</span><span class="sxs-lookup"><span data-stu-id="73d0c-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![交互](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="73d0c-133">![原型](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="73d0c-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="73d0c-134">*交互原型*</span><span class="sxs-lookup"><span data-stu-id="73d0c-134">*Interaction prototypes*</span></span>

<span data-ttu-id="73d0c-135">用户可以通过通过按表底部的按钮来更改表面类型 - 它们可以在平面、柱面、球体和散点图之间切换。</span><span class="sxs-lookup"><span data-stu-id="73d0c-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="73d0c-136">此应用中使用的常见控件和模式</span><span class="sxs-lookup"><span data-stu-id="73d0c-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="73d0c-137">可交互对象 (按钮) </span><span class="sxs-lookup"><span data-stu-id="73d0c-137">Interactable object (button)</span></span>

<span data-ttu-id="73d0c-138">[可交互](../../design/interactable-object.md) 对象是一个对象，可以响应基本的 HoloLens 输入。</span><span class="sxs-lookup"><span data-stu-id="73d0c-138">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="73d0c-139">它作为预制/脚本提供，可轻松应用于任何对象。</span><span class="sxs-lookup"><span data-stu-id="73d0c-139">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="73d0c-140">例如，可以使场景中的咖啡杯交互，并响应凝视、敲击、导航和操作手势等输入。</span><span class="sxs-lookup"><span data-stu-id="73d0c-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="73d0c-141">了解详细信息</span><span class="sxs-lookup"><span data-stu-id="73d0c-141">Learn more</span></span>](../../design/interactable-object.md)

![nteractable 对象](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="73d0c-143">对象集合</span><span class="sxs-lookup"><span data-stu-id="73d0c-143">Object collection</span></span>

<span data-ttu-id="73d0c-144">[对象](../../design/object-collection.md) 集合是一个对象，可帮助你以各种形状布局多个对象。</span><span class="sxs-lookup"><span data-stu-id="73d0c-144">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="73d0c-145">它支持平面、柱面、球体和散点图。</span><span class="sxs-lookup"><span data-stu-id="73d0c-145">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="73d0c-146">可以配置其他属性，例如半径、行数和间距。</span><span class="sxs-lookup"><span data-stu-id="73d0c-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="73d0c-147">了解详细信息</span><span class="sxs-lookup"><span data-stu-id="73d0c-147">Learn more</span></span>](../../design/object-collection.md)

![对象集合](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="73d0c-149">技术详细信息</span><span class="sxs-lookup"><span data-stu-id="73d0c-149">Technical details</span></span>

<span data-ttu-id="73d0c-150">可以在混合现实设计实验室 GitHub 上找到 Elements 应用的周期表的脚本和 [预制件](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)。</span><span class="sxs-lookup"><span data-stu-id="73d0c-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="73d0c-151">移植适用于 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="73d0c-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="73d0c-152">阅读有关如何使用元素应用周期表更新HoloLens 2性交互的信息。</span><span class="sxs-lookup"><span data-stu-id="73d0c-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="73d0c-153">元素周期表 2.0</span><span class="sxs-lookup"><span data-stu-id="73d0c-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="73d0c-154">关于作者</span><span class="sxs-lookup"><span data-stu-id="73d0c-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="73d0c-155"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="73d0c-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="73d0c-156">用户体验设计师 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="73d0c-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="73d0c-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73d0c-157">See also</span></span>

* <span data-ttu-id="73d0c-158">[MRTK 示例中心](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="73d0c-158">[MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="73d0c-159">[表面](sampleapp-surfaces.md) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="73d0c-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="73d0c-160">元素周期表 2.0</span><span class="sxs-lookup"><span data-stu-id="73d0c-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="73d0c-161">星系探索者 2.0</span><span class="sxs-lookup"><span data-stu-id="73d0c-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)