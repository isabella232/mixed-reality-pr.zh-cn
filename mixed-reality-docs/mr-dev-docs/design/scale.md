---
title: 缩放
description: 如果要显示看起来十分逼真的全息形式的内容，其关键是尽可能真实地模拟现实世界的视觉统计数据。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，样式，设计，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens，规模，全息影像
ms.openlocfilehash: e82211b0bee2214df7542d3129f95ea207f4b0e3
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703373"
---
# <a name="scale"></a>缩放

如果要显示看起来十分逼真的全息形式的内容，其关键是尽可能真实地模拟现实世界的视觉统计数据。 这意味着将尽可能多的、可以帮助我们（在现实世界中）了解对象的位置、大小及其组成部分的视觉提示整合在一起。 对象的小数位数是这些视觉对象提示中最重要的一种，为查看器提供对象的大小并提示其位置 (尤其是对于具有已知大小) 的对象。 此外，查看真实规模的对象已被视为一般的混合现实中的一个关键体验优势，即以前不能在屏幕上查看的内容。

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>如何建议对象和环境的规模

有多种方法可建议对象的规模，其中一些方法可能会对其他可感知因素产生影响。 第一项是只显示 "真实" 大小的对象，并在用户移动时保持真实大小。 这意味着，全息影像会占用用户的用户视觉角度，因为这些用户的视觉对象比实际对象更近或更远。

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a>利用对象在向用户显示时的距离

一种常见方法是利用对象在向用户显示时的距离。 例如，请考虑在用户的正面直观呈现大型家族汽车。 如果轿车直接位于其前面，则在 arm 的长度内，可能会太大而无法容纳在用户的视图中。 这将要求用户移动其头和正文以了解对象的整体。 如果将汽车置于房间外 () ，则用户可以通过在其视图字段中查看全部对象来建立一种规模，然后将其移动到更靠近它的位置来更详细地检查区域。

:::row:::
    :::column:::
        **[Volvo 使用此方法为新汽车创造了 showroom](https://www.youtube.com/watch?v=DilzwF90vec)** 的体验，利用全息汽车的规模，以一种对用户来说切实可行、直观的方式。 此体验始于一个物理表中的汽车全息图，使用户能够了解模型的总大小和形状。 在此体验中，汽车扩展到的 (超出了设备的视图) 大小，但由于用户已从较小的模型获取了引用帧，因此可以充分地浏览汽车的功能。<br>
        <br>
        *图像： Volvo 汽车的 HoloLens 体验*
    :::column-end:::
        :::column:::
       ![HoloLens 的 Volvo 汽车体验](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a>使用全息影像修改用户的真实空间

另一种方法是使用全息影像来修改用户的实际空间，将现有的墙壁或上限替换为环境，或者追加 "洞" 或 "windows"，允许大小过度的对象看似 "突破" 物理空间。 例如，大型树可能不适合大多数用户的生活空间，但通过将虚拟天空置于天花板上，物理空间将扩展到虚拟。 这样，用户就可以在虚拟树的基础上进行探讨，并收集它在现实生活中的显示方式，并查看它是否超出了房间的物理空间。

:::row:::
    :::column:::
        **[Minecraft 开发了](https://minecraft.net/)** 使用类似技术的概念。 通过将虚拟窗口添加到房间中的物理表面上，房间中的现有对象会置于更大的环境中，而不会超出空间的物理规模限制。<br>
        <br>
        *Image： HoloLens 的 Minecraft 概念体验*
    :::column-end:::
        :::column:::
       ![HoloLens 的 Minecraft 概念体验](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a>进行大规模试验

在某些情况下，设计人员 vspackage 通过更改对象的显示 "真正" 大小来修改缩放 () 同时保持对象的单个位置，以使对象接近或更接近查看器而不进行任何实际移动。 在某些情况下，在某些情况下会对此进行测试，这是一种模拟多个项的方式，同时仍然遵从查看虚拟内容的可能舒适的限制，而不会建议使用。

但这可能会在经验中创建几个可能的项目：
* 对于表示查看器大小为 "已知" 的对象的虚拟对象，在不更改位置的情况下更改缩放将导致出现冲突的视觉提示，该眼睛仍可能会因为 vergence (提示而在某种程度) 上看到对象[Comfort](comfort.md) ，但大小是 monocular 的，提示对象可能会更接近。 这些冲突的提示会导致混乱的认知，查看器通常会将对象视为就地 (由于恒定的深度提示) 但会迅速增长。
* 在某些情况下，更改规模会被视为 "临近" 提示，在该对象中，可能会或不会看到对象通过查看器进行缩放，但看起来像是在查看者的眼睛 (，这可能是成名的) 。
* 在现实世界中的比较面上，此类缩放更改有时会被视为随着多个轴的变化位置，在某些情况) 下，对象可能看起来降低，而不是以更近的方向 (类似于三维移动的2D 投影。
* 最后，对于没有已知 "实际大小" 的对象 (例如任意大小、UI 元素 ) 等的任意形状），更改规模可能会以某种方式进行操作，以模拟距离变化–查看器不具有与对象的真实大小或位置有关的任何预先存在的自顶向下提示，因此可将该刻度作为更重要的提示进行处理。

<br>

---

## <a name="see-also"></a>另请参阅
* [颜色、光线和材料](../color,-light-and-materials.md)
* [版式](typography.md)
* [空间音效设计](spatial-sound-design.md)
