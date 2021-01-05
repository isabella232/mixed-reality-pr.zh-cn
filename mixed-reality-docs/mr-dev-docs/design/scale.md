---
title: 缩放
description: 如果要显示看起来十分逼真的全息形式的内容，其关键是尽可能真实地模拟现实世界的视觉统计数据。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，样式，设计，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机，HoloLens，规模，全息影像
ms.openlocfilehash: 6711a58fb4dde2aa28272c3003e642c4f4d3e236
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848274"
---
# <a name="scale"></a>缩放

显示真实的全息内容的关键是，模拟真实世界的视觉统计信息。 合并了可视化提示，以帮助现实世界用户了解对象的位置、其大小以及所做的操作。 对象的小数位数是最重要的视觉提示之一，因为它为查看器提供了对象大小并提示其位置。 此外，查看真实规模的对象是一般的混合现实的关键经验因素之一–在以前的基于屏幕的查看中不可能出现这种情况。

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>如何建议对象和环境的规模

有多种方法可建议对象的规模，其中一些方法可能会对其他可感知因素产生影响。 第一项是以 "真实" 大小显示对象，并在用户移动时保持真实大小。 全息网会占用用户的用户视觉角度，因为这些用户的视觉对象比实际对象更近或更远。

### <a name="use-the-distance-of-objects-as-theyre-presented-to-the-user"></a>使用对象向用户显示的距离

一种常见方法是使用对象的距离，就像向用户显示一样。 例如，请考虑在用户的正面直观呈现大型家族汽车。 如果轿车在 arm 的长度内直接位于其前面，则它会太大，无法容纳在用户的视图中。 关闭对象要求用户移动其头和正文，以了解对象的整体。 如果将汽车置于房间外 () ，则用户可以通过在其视图字段中查看整个对象来确定规模。 然后，用户可以更接近对象，以便进行更详细的检查。

:::row:::
    :::column:::
        **[Volvo 使用此方法为新汽车创建了 showroom](https://www.youtube.com/watch?v=DilzwF90vec)** 体验，使用全息汽车的规模，以一种对用户来说切实可行且直观的方式。 此体验始于物理表中的汽车全息图，使用户能够了解模型的总大小和形状。 以后在此体验中，汽车扩展到的规模超出了设备的视图字段大小。 由于用户已从较小的模型获取了引用帧，因此可以充分地浏览汽车的功能。<br>
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

另一种方法是使用全息影像来修改用户的实际空间，将现有的墙壁或上限替换为环境，或者追加 "洞" 或 "windows"。 这允许大小过度的对象看似 "突破" 物理空间。 例如，大型树可能不适合大多数用户的生活空间，但通过将虚拟天空置于天花板上，物理空间将扩展到虚拟。 这样，用户就可以浏览虚拟树的基础，并收集规模和现实世界的意义。 然后，用户可以查看它是否超出空间的物理空间。

:::row:::
    :::column:::
        **[Minecraft 开发了](https://minecraft.net/)** 使用类似技术的概念。 通过将虚拟窗口添加到物理图面上，房间中的现有对象会置于更大的环境中，超出了房间的物理规模限制。<br>
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

设计人员通过更改对象的显示的 "真实" 大小，vspackage 了修改规模。 同时，它们维护单个对象位置，以使对象接近查看器而不进行任何实际移动。 在某些情况下，在某些情况下会对此进行测试，这是一种模拟多个项的方式，同时仍然遵从查看虚拟内容的可能舒适的限制，而不会建议使用。

但这可能会在经验中创建几个可能的项目：
* 对于以 "已知" 大小显示在查看器中的某个对象的虚拟对象，在不更改位置的情况下更改缩放将导致视觉提示冲突。眼睛可能仍会在一定程度上看到对象，因为存在 vergence 提示。有关详细信息，请参阅 [舒适](comfort.md) 文章。 大小是 monocular 的，提示对象可能会更接近。 这些冲突的提示会导致混淆，查看器通常会将对象视为就地 (，因为有恒定的深度提示) 但快速增长。
* 在某些情况下，更改规模会被视为 "临近" 提示，在该对象中，可能会或不会看到对象通过查看器进行缩放，但看起来像是在查看者的眼睛 (，这可能是成名的) 。
* 在现实世界中的比较面上，此类缩放更改有时会被视为在多个轴上改变位置-在某些情况) 下，对象看起来降低，而不是更接近 (类似于三维移动的2D 投影。
* 最后，对于没有已知 "现实世界" 大小的对象 (例如，具有任意大小的任意形状、UI 元素等) ，更改的缩放可能会以某种方式进行操作，以模拟距离的变化。 查看器的预先存在的自顶向下提示不能了解对象的真实大小或位置，因此可以将该刻度作为更重要的提示进行处理。

<br>

---

## <a name="see-also"></a>另请参阅
* [颜色、光线和材料](../color,-light-and-materials.md)
* [版式](typography.md)
* [空间音效设计](spatial-sound-design.md)
