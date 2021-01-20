---
title: 缩放
description: 如果要显示看起来十分逼真的全息形式的内容，其关键是尽可能真实地模拟现实世界的视觉统计数据。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，样式，设计，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens，规模，全息影像
ms.openlocfilehash: 12b1c96146f76274831c9bc3427cef93bb326f70
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583318"
---
# <a name="scale"></a><span data-ttu-id="3c5db-104">缩放</span><span class="sxs-lookup"><span data-stu-id="3c5db-104">Scale</span></span>

<span data-ttu-id="3c5db-105">显示真实的全息内容的关键是，模拟真实世界的视觉统计信息。</span><span class="sxs-lookup"><span data-stu-id="3c5db-105">The key to displaying realistic holographic content is mimicking the visual statistics of the real world as closely as possible.</span></span> <span data-ttu-id="3c5db-106">合并了可视化提示，以帮助现实世界用户了解对象的位置、其大小以及所做的操作。</span><span class="sxs-lookup"><span data-stu-id="3c5db-106">Incorporate visual cues to help real-world users understand where objects are, how big they are, and what they’re made of.</span></span> <span data-ttu-id="3c5db-107">对象的小数位数是最重要的视觉提示之一，因为它为查看器提供了对象大小并提示其位置。</span><span class="sxs-lookup"><span data-stu-id="3c5db-107">The scale of an object is one of the most important visual cues because it gives viewer a sense of the objects size and cues to its location.</span></span> <span data-ttu-id="3c5db-108">此外，查看真实规模的对象是一般的混合现实的关键经验因素之一–在以前的基于屏幕的查看中不可能出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="3c5db-108">Further, viewing objects at real scale is one of the key experience differentiators for mixed reality in general – something that hasn’t been possible on previous screen-based viewing.</span></span>

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a><span data-ttu-id="3c5db-109">如何建议对象和环境的规模</span><span class="sxs-lookup"><span data-stu-id="3c5db-109">How to suggest the scale of objects and environments</span></span>

<span data-ttu-id="3c5db-110">有多种方法可建议对象的规模，其中一些方法可能会对其他可感知因素产生影响。</span><span class="sxs-lookup"><span data-stu-id="3c5db-110">There are many ways to suggest the scale of an object, some of which have possible effects on other perceptual factors.</span></span> <span data-ttu-id="3c5db-111">第一项是以 "真实" 大小显示对象，并在用户移动时保持真实大小。</span><span class="sxs-lookup"><span data-stu-id="3c5db-111">The key one is to display objects at a ‘real’ size, and maintain that realistic size as users move.</span></span> <span data-ttu-id="3c5db-112">全息网会占用用户的用户视觉角度，因为这些用户的视觉对象比实际对象更近或更远。</span><span class="sxs-lookup"><span data-stu-id="3c5db-112">Holograms will take up a different amount of a user’s visual angle of a user as they come closer or further away, the same way that real objects do.</span></span>

### <a name="use-the-distance-of-objects-as-theyre-presented-to-the-user"></a><span data-ttu-id="3c5db-113">使用对象向用户显示的距离</span><span class="sxs-lookup"><span data-stu-id="3c5db-113">Use the distance of objects as they're presented to the user</span></span>

<span data-ttu-id="3c5db-114">一种常见方法是使用对象的距离，就像向用户显示一样。</span><span class="sxs-lookup"><span data-stu-id="3c5db-114">One common method is to use the distance of objects as they're presented to the user.</span></span> <span data-ttu-id="3c5db-115">例如，请考虑在用户的正面直观呈现大型家族汽车。</span><span class="sxs-lookup"><span data-stu-id="3c5db-115">For example, consider visualizing a large family car in front of the user.</span></span> <span data-ttu-id="3c5db-116">如果轿车在 arm 的长度内直接位于其前面，则它会太大，无法容纳在用户的视图中。</span><span class="sxs-lookup"><span data-stu-id="3c5db-116">If the car was directly in front of them within arm’s length, it would be too large to fit in the user’s field of view.</span></span> <span data-ttu-id="3c5db-117">关闭对象要求用户移动其头和正文，以了解对象的整体。</span><span class="sxs-lookup"><span data-stu-id="3c5db-117">Close objects require the user to move their head and body to understand the entirety of the object.</span></span> <span data-ttu-id="3c5db-118">如果将汽车置于房间外 () ，则用户可以通过在其视图字段中查看整个对象来确定规模。</span><span class="sxs-lookup"><span data-stu-id="3c5db-118">If the car is placed further away (across the room), the user can establish a sense of scale by seeing the entire object in their field of view.</span></span> <span data-ttu-id="3c5db-119">然后，用户可以更接近对象，以便进行更详细的检查。</span><span class="sxs-lookup"><span data-stu-id="3c5db-119">Users could then move themselves closer to the object for a more detailed inspection.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3c5db-120">**[Volvo 使用此方法为新汽车创建了 showroom](https://www.youtube.com/watch?v=DilzwF90vec)** 体验，使用全息汽车的规模，以一种对用户来说切实可行且直观的方式。</span><span class="sxs-lookup"><span data-stu-id="3c5db-120">**[Volvo used this technique to create a showroom](https://www.youtube.com/watch?v=DilzwF90vec)** experience for a new car, using the scale of the holographic car in a way that felt realistic and intuitive to the user.</span></span> <span data-ttu-id="3c5db-121">此体验始于物理表中的汽车全息图，使用户能够了解模型的总大小和形状。</span><span class="sxs-lookup"><span data-stu-id="3c5db-121">The experience begins with the car hologram on a physical table, allowing the user to understand the total size and shape of the model.</span></span> <span data-ttu-id="3c5db-122">以后在此体验中，汽车扩展到的规模超出了设备的视图字段大小。</span><span class="sxs-lookup"><span data-stu-id="3c5db-122">Later in the experience, the car expands to a scale beyond the size of the device's field of view.</span></span> <span data-ttu-id="3c5db-123">由于用户已从较小的模型获取了引用帧，因此可以充分地浏览汽车的功能。</span><span class="sxs-lookup"><span data-stu-id="3c5db-123">Since the user already acquired a frame of reference from the smaller model, they can adequately navigate around features of the car.</span></span><br>
        <br>
        <span data-ttu-id="3c5db-124">*图像： Volvo 汽车的 HoloLens 体验*</span><span class="sxs-lookup"><span data-stu-id="3c5db-124">*Image: Volvo Cars experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens 的 Volvo 汽车体验](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a><span data-ttu-id="3c5db-126">使用全息影像修改用户的真实空间</span><span class="sxs-lookup"><span data-stu-id="3c5db-126">Use holograms to modify the user's real space</span></span>

<span data-ttu-id="3c5db-127">另一种方法是使用全息影像来修改用户的实际空间，将现有的墙壁或上限替换为环境，或者追加 "洞" 或 "windows"。</span><span class="sxs-lookup"><span data-stu-id="3c5db-127">Another method is to use holograms to modify the user's real space, replacing the existing walls or ceilings with environments or appending ‘holes’ or ‘windows’.</span></span> <span data-ttu-id="3c5db-128">这允许大小过度的对象看似 "突破" 物理空间。</span><span class="sxs-lookup"><span data-stu-id="3c5db-128">This allows over-sized objects to seemingly 'break-through' the physical space.</span></span> <span data-ttu-id="3c5db-129">例如，大型树可能不适合大多数用户的生活空间，但通过将虚拟天空置于天花板上，物理空间将扩展到虚拟。</span><span class="sxs-lookup"><span data-stu-id="3c5db-129">For example, a large tree might not fit in most users’ living rooms, but by putting a virtual sky on their ceiling, the physical space expands into the virtual.</span></span> <span data-ttu-id="3c5db-130">这样，用户就可以浏览虚拟树的基础，并收集规模和现实世界的意义。</span><span class="sxs-lookup"><span data-stu-id="3c5db-130">This allows the user to walk around the base of the virtual tree and gather a sense of scale and real-world appearance.</span></span> <span data-ttu-id="3c5db-131">然后，用户可以查看它是否超出空间的物理空间。</span><span class="sxs-lookup"><span data-stu-id="3c5db-131">Users can then look up to see it extend far beyond the physical space of the room.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3c5db-132">**[Minecraft 开发了](https://minecraft.net/)** 使用类似技术的概念。</span><span class="sxs-lookup"><span data-stu-id="3c5db-132">**[Minecraft developed a concept experiences](https://minecraft.net/)** using a similar technique.</span></span> <span data-ttu-id="3c5db-133">通过将虚拟窗口添加到物理图面上，房间中的现有对象会置于更大的环境中，超出了房间的物理规模限制。</span><span class="sxs-lookup"><span data-stu-id="3c5db-133">By adding a virtual window to a physical surface, the existing objects in the room are placed in the context of a vastly larger environment, beyond the physical scale limitations of the room.</span></span><br>
        <br>
        <span data-ttu-id="3c5db-134">*Image： HoloLens 的 Minecraft 概念体验*</span><span class="sxs-lookup"><span data-stu-id="3c5db-134">*Image: Minecraft concept experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens 的 Minecraft 概念体验](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a><span data-ttu-id="3c5db-136">进行大规模试验</span><span class="sxs-lookup"><span data-stu-id="3c5db-136">Experimenting with scale</span></span>

<span data-ttu-id="3c5db-137">设计人员通过更改对象的显示的 "真实" 大小，vspackage 了修改规模。</span><span class="sxs-lookup"><span data-stu-id="3c5db-137">Designers have experimented with modifying the scale by changing the displayed ‘real’ size of the object.</span></span> <span data-ttu-id="3c5db-138">同时，它们维护单个对象位置，以使对象接近查看器而不进行任何实际移动。</span><span class="sxs-lookup"><span data-stu-id="3c5db-138">At the same time, they maintain a single object position to approximate an object moving towards the viewer without any actual movement.</span></span> <span data-ttu-id="3c5db-139">在某些情况下，在某些情况下会对此进行测试，这是一种模拟多个项的方式，同时仍然遵从查看虚拟内容的可能舒适的限制，而不会建议使用。</span><span class="sxs-lookup"><span data-stu-id="3c5db-139">This was tested in some cases as a way to simulate up-close viewing of items while still respecting potential comfort limitations of viewing virtual content closer than the “zone of comfort” would suggest.</span></span>

<span data-ttu-id="3c5db-140">但这可能会在经验中创建几个可能的项目：</span><span class="sxs-lookup"><span data-stu-id="3c5db-140">This can create a few possible artifacts in the experience however:</span></span>
* <span data-ttu-id="3c5db-141">对于以 "已知" 大小显示在查看器中的某个对象的虚拟对象，在不更改位置的情况下更改缩放将导致视觉提示冲突。眼睛可能仍会在一定程度上看到对象，因为存在 vergence 提示。有关详细信息，请参阅 [舒适](comfort.md) 文章。</span><span class="sxs-lookup"><span data-stu-id="3c5db-141">For virtual objects that represent some object with a ‘known’ size to the viewer, changing the scale without changing the position leads to conflicting visual cues. The eyes may still ‘see’ the object at some depth because of vergence cues. For more information, see the [Comfort](comfort.md) article.</span></span> <span data-ttu-id="3c5db-142">大小是 monocular 的，提示对象可能会更接近。</span><span class="sxs-lookup"><span data-stu-id="3c5db-142">The size acts as a monocular cue that the object might be getting closer.</span></span> <span data-ttu-id="3c5db-143">这些冲突的提示会导致混淆，查看器通常会将对象视为就地 (，因为有恒定的深度提示) 但快速增长。</span><span class="sxs-lookup"><span data-stu-id="3c5db-143">These conflicting cues lead to confused perceptions – viewers often see the object as staying in place (because of the constant depth cue) but growing rapidly.</span></span>
* <span data-ttu-id="3c5db-144">在某些情况下，更改规模会被视为 "临近" 提示，在该对象中，可能会或不会看到对象通过查看器进行缩放，但看起来像是在查看者的眼睛 (，这可能是成名的) 。</span><span class="sxs-lookup"><span data-stu-id="3c5db-144">In some cases, change of scale is seen as a ‘looming’ cue instead, where the object may or may not be seen to change scale by a viewer, but does appear to be moving directly toward the viewer’s eyes (which can be an uncomfortable sensation).</span></span>
* <span data-ttu-id="3c5db-145">在现实世界中的比较面上，此类缩放更改有时会被视为在多个轴上改变位置-在某些情况) 下，对象看起来降低，而不是更接近 (类似于三维移动的2D 投影。</span><span class="sxs-lookup"><span data-stu-id="3c5db-145">With comparison surfaces in the real world, such scaling changes are sometimes seen as changing position along multiple axes – objects appear to drop lower instead of moving closer (similar in a 2D projection of 3D movement in some cases).</span></span>
* <span data-ttu-id="3c5db-146">最后，对于没有已知 "现实世界" 大小的对象 (例如，具有任意大小的任意形状、UI 元素等) ，更改的缩放可能会以某种方式进行操作，以模拟距离的变化。</span><span class="sxs-lookup"><span data-stu-id="3c5db-146">Finally, for objects without a known ‘real world’ size (for example, arbitrary shapes with arbitrary sizes, UI elements, and so on), changing scale may act functionally as a way to mimic changes in distance.</span></span> <span data-ttu-id="3c5db-147">查看器的预先存在的自顶向下提示不能了解对象的真实大小或位置，因此可以将该刻度作为更重要的提示进行处理。</span><span class="sxs-lookup"><span data-stu-id="3c5db-147">Viewers don't have as many pre-existing top-down cues to understand the object’s true size or location, so the scale can be processed as a more important cue.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="3c5db-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c5db-148">See also</span></span>
* [<span data-ttu-id="3c5db-149">颜色、光线和材料</span><span class="sxs-lookup"><span data-stu-id="3c5db-149">Color, light, and materials</span></span>](./color-light-and-materials.md)
* [<span data-ttu-id="3c5db-150">版式</span><span class="sxs-lookup"><span data-stu-id="3c5db-150">Typography</span></span>](typography.md)
* [<span data-ttu-id="3c5db-151">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="3c5db-151">Spatial sound design</span></span>](spatial-sound-design.md)