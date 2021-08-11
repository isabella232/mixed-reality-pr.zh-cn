---
title: 案例研究 - 看透现实中的洞
description: 此案例研究解释了在 HoloLens 上的"幻窗口"效果实现，允许用户在墙后、楼层下和虚拟门面中查看。
author: ericrehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、magic 窗口、视差
ms.openlocfilehash: 0769d8a7bd2b5bdf1ef1fe50f1bbcd2f284b8503bf66b8fdb09b2206b716ea65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228167"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>案例研究 - 看透现实中的洞

当人们考虑混合现实以及他们可以使用Microsoft HoloLens时，他们通常会坚持"我可以将哪些对象添加到房间？" 或"我可以在空间顶层分层什么？" 我想重点介绍另一个可考虑的方面（实质上是一个万能技巧）使用同一技术来查看或浏览你周围的实际物理对象。

## <a name="the-tech"></a>技术

如果你在它们从 **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** 中穿过墙时进行了努力，在 **[Fragments](case-study-creating-an-immersive-experience-in-fragments.md)** 中解锁了一个墙安全，或者对在 **[2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)** 年 E3 的 Halo 5 体验中看到了 UNSC Infinity hangar 感到十分幸运的是，那么你已了解我所说的。 根据你的想象，此视觉技巧可用于在干墙中放入临时孔，或将世界隐藏在松散的地板下。

![RoboRaid 在墙后面添加三维管道和其他结构，这些结构仅通过当比特器穿过时创建的孔可见。](../develop/unity/images/roboraid-640px.png)

RoboRaid 在墙后面添加三维管道和其他结构，这些结构仅通过当比特器穿过时创建的孔可见。

在 HoloLens 上使用这些独特的全息影像之一，应用可以像通过实际窗口呈现自身一样，在墙后面或楼层中提供内容的假象。 向左移动，可以看到右侧的任何信息。 更近一点，可以看到更多内容。 主要区别在于，实际孔允许通过，而楼层则不允许你进入到这个令人动听的全息内容。  (向 backlog.) 

## <a name="behind-the-scenes"></a>幕后

此技巧是两种效果的组合。 首先，全息内容使用"空间定位点"固定到世界。 使用定位点使该内容"被锁定"意味着你正在查看的内容不会在视觉上偏离它附近的物理对象，即使你移动或基础空间映射系统更新其房间的 3D 模型。

其次，全息内容在视觉上仅限于一个非常具体的空间，因此只能通过现实中的孔来查看。 这种遮挡是必需的，需要查看逻辑孔、窗口或门道，从而销售技巧。 如果不阻止大部分视图，机密 Jurassic 维度的空间破解可能只是看起来像一只放置不佳的恐龙。

![这不是实际的屏幕截图，而是 MR Basics 101 中机密下部在HoloLens。 黑色机箱未显示，但可以通过虚拟孔查看内容。  (查看实际设备时，楼层似乎会消失更多，因为你的视线会聚焦在更远的距离，就像它甚至不存在一样。) ](images/origamiholecomposited-640px.png)

这不是实际屏幕截图，而是[MR Basics 101](../develop/unity/tutorials/holograms-101.md)中机密下的显示HoloLens。 黑色机箱未显示，但可以通过虚拟孔查看内容。  (查看实际设备时，楼层似乎会消失更多，因为你的视线会聚焦在更远的距离，就像它甚至不存在一样。) 

### <a name="world-locking-holographic-content"></a>世界锁定全息内容

在 Unity 中，使全息内容保持世界锁定与添加 WorldAnchor 组件一样简单：

```
myObject.AddComponent<WorldAnchor>();
```

WorldAnchor 组件将不断调整 GameObject (的位置和旋转，从而调整层次结构中该对象下) 以相对于附近的物理对象保持稳定。 创作内容时，请创建内容，使对象的根透视以此虚拟孔为中心。  (如果对象的透视深度在墙中，则其位置和旋转的细微调整将更加明显，并且孔看起来可能不太稳定。) 

### <a name="occluding-everything-but-the-virtual-hole"></a>遮挡除了虚拟孔外的所有内容

有多种方法可以选择性地阻止视图中隐藏在墙中。 最简单的方法利用这样一个事实：HoloLens加性显示，这意味着完全黑色对象看起来不可见。 可以在 Unity 中执行此操作，而无需执行任何特殊的着色器或材料技巧 - 只需创建黑色材料并将其分配给内容中框的对象即可。 如果不想进行 3D 建模，只需使用几个默认的四边形对象，并稍微重叠一下。 此方法存在许多缺点，但这是使某些内容正常工作的最快方法，并且即使怀疑稍后可能需要重构概念证明，获取低保真度的概念证明也很好。

上述"黑盒"方法的一个主要缺点是，它无法很好地拍摄。 虽然效果可能通过显示HoloLens完美，但任何屏幕截图都会显示一个大型黑色对象，而不是墙或楼层的保留内容。 这是因为物理硬件和屏幕截图以不同方式复合全息影像和现实。 让我们暂时看看一些假数学...

*假数学警报！这些数字和公式旨在说明一个点，而不是任何一种准确的指标！*

通过查看HoloLens：

```
( Reality * darkening_amount ) + Holograms
```

在屏幕截图和视频中看到：

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

英语：通过英语HoloLens你所看到的是一种简单的混合现实 (例如通过) 以及应用想要显示的任何全息影像。 但是，当你拍摄屏幕截图时，相机的图像根据每像素透明度值与应用的全息影像混合。

要解决此问题，一个方法就是将"黑盒"材料更改为仅写入深度缓冲区，然后使用所有其他不透明材料进行排序。 有关这种情况的示例，请查看 上[MixedRealityToolkit 中的 WindowOcclusion.shader GitHub。](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader) 此处复制了相关行：

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

 (请注意，"偏移量 50， 100"行用于处理不相关的问题，因此，最好不要) 

实现这样的不可见遮挡材料，使应用能够绘制一个在显示器和混合现实屏幕截图中看起来正确的框。 对于奖励点，可以通过执行更智能操作来绘制更少的不可见像素，以进一步提高该框的性能，但这确实可以进入无线，通常不需要。

![下面是 MR Basics 101 中的机密，Unity 绘制它时，遮挡框的外部部分除外。 请注意，下层的透视位于框的中心，这有助于使孔相对于实际楼层尽可能稳定。](images/underworld-occluded-640px.png)

下面是 MR [Basics 101](../develop/unity/tutorials/holograms-101.md) 中的机密，Unity 绘制它时，遮挡框的外部部分除外。 请注意，下层的透视位于框的中心，这有助于使孔相对于实际楼层尽可能稳定。

## <a name="do-it-yourself"></a>自制

有HoloLens并想要自己试用效果？ 无需编码 (最简单的) 是安装免费的 3D 查看器 应用，然后加载在 GitHub 上提供的下载[.fbx](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow)文件，以便查看房间中的花店模型。 在HoloLens加载它，可以看到工作上的假象。 当你位于模型前面时，只能看到小孔中，其他所有内容都是不可见的。 从任何其他端查看模型，它完全消失。 使用虚拟孔的移动、旋转和3D 查看器控件将虚拟孔定位到任何可想生成创意的垂直表面！

![在 Unity 编辑器中查看此模型将在花体周围显示一个大型黑盒。 在HoloLens，框会消失，从而产生一种幻窗口效果。](images/magicwindowflowerpotineditor.png)

在 Unity 编辑器中查看此模型将在花体周围显示一个大型黑盒。 在HoloLens，框会消失，从而产生一种幻窗口效果。

若要生成使用此技术的应用，请查看混合现实教程 中的 MR [基础知识 101](../develop/unity/tutorials/holograms-101.md) [教程](../develop/unity/tutorials.md)。 第 7 章以楼层中的一次爆炸结束，它显示了一个隐藏的 (，如上图) 。 Who教程必须让人感到不自在？

下面是一些有关接下来可采取此想法的思路：
* 考虑使虚拟孔内的内容交互的方法。 让用户在墙之外产生一些影响，可以真正提高这种技巧可以提供的怀疑感。
* 考虑将对象查看回已知区域的方法。 例如，如何将全息孔放在咖啡表中，并在其下方看到楼层？

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>高级软件工程师 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另请参阅
* [MR 基础知识 101：使用设备完成项目](../develop/unity/tutorials/holograms-101.md)
* [坐标系统](../design/coordinate-systems.md)
* [空间定位点](../design/spatial-anchors.md)
* [空间映射](../design/spatial-mapping.md)
