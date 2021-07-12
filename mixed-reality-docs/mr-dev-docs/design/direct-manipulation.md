---
title: 用手直接操作
description: 了解直接操作，一种输入模型，用户可在此输入模型中用手直接接触全息影像。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, 凝视, 设定凝视目标, 交互, 设计, 手动近距, HoloLens, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, MRTK, 混合现实工具包, 按钮, 碰撞体, 边界框, 2D, 本能手势
ms.openlocfilehash: 7a689f887bfd358b0d6e0826d41ef409bf887042
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600466"
---
# <a name="direct-manipulation-with-hands"></a>用手直接操作

![Button](images/UX_Hero_Manipulation.jpg)

直接操作是一个输入模型，涉及到用手直接触摸全息影像。 此概念后面的理念是使对象的行为如同在现实世界中一样自然。 只需按下按钮就能将其激活，抓取对象可以拾取对象，2D 内容的行为与在虚拟触摸屏上类似。 直接操作基于视觉元素，因此具备用户友好性。 没有任何符号手势可以向用户传授操作方法。 所有交互都是围绕一个可以触摸或抓取的可视元素构建的。 它被视为一种“近距”输入模型，这意味着，它最好用于与手臂可触及范围内的内容进行交互。

## <a name="device-support"></a>设备支持

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>输入模型</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></td>
     <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
     <td><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>沉浸式头戴显示设备</strong></a></td>
</tr>
<tr>
     <td>用手直接操作</td>
     <td>❌ 不支持</td>
     <td>✔️ 推荐</td>
     <td>➕ 支持。  对于 UI，我们建议改为<a href="point-and-commit.md">使用手指向和提交</a>。</td>
    
</tr>
</table>


直接操作是 HoloLens 2 中的主要输入模型，使用最新的语音式手动跟踪系统。 还可以通过运动控制器在沉浸式头戴显示设备中使用该输入模型，但不建议将它用作对象操作以外的主要交互方式。 直接操作在 HoloLens（第 1 代）中不可用。

<br>

---

## <a name="basic-hand-tracking-and-instinctual-interactions-demo"></a>基本手部跟踪和本能交互演示

若要了解头部和眼动跟踪设计概念的运行情况，请查看下面的“设计全息影像 - 头部跟踪和眼动跟踪”视频演示。 完成后，请继续详细了解特定主题。

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

此视频来自于“设计全息影像”HoloLens 2 应用。在[此处](https://aka.ms/dhapp)下载并享受完整体验。

## <a name="collidable-fingertip"></a>可碰撞指尖

在 HoloLens 2 上，用户的手部将被识别并解释为左右手骨架模型。 为了实现直接用手触摸全息影像的思路，理想情况下，可将 5 个碰撞体附加到每个手部骨架模型的 5 个指尖。 但是，由于缺少触觉反馈，使用 10 个可碰撞指尖可能会导致全息影像中发生意外且不可预测的碰撞。 

建议只在每个食指上放置一个碰撞体。 可碰撞的食指指尖仍可充当涉及其他手指的各种触摸手势的触摸点。 触摸手势包括一指按压、一指点击、两指按压、五指按压，如下所示：

:::row:::
    :::column:::
       ![可碰撞指尖](images/Collidable-Fingertip.jpg)<br>
       **可碰撞指尖**<br>
    :::column-end:::
    :::column:::
       ![单指按下](images/Collidable-Fingertip-1-finger-press.jpg)<br>
        **单指按下**<br>
    :::column-end:::
    :::column:::
       ![单指点击](images/Collidable-Fingertip-1-finger-tap.jpg)<br>
       **单指点击**<br>
    :::column-end:::
    :::column:::
       ![五指按下](images/Collidable-Fingertip-5-finger-press.jpg)<br>
       **五指按下**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a>球体碰撞体

如果不使用随机的一般形状，我们建议使用球体碰撞体。 然后即可以可视方式渲染它，以便为近距定位提供更好的线索。 该球体的直径应与食指的粗细相匹配，以提高触摸准确度。 可以通过调用手部 API 来更轻松地检索手指粗细的变量。

### <a name="fingertip-cursor"></a>指尖光标

除了在食指指尖上渲染可碰撞球体以外，我们还创建了一个高级指尖光标来实现更好的近距定位体验。 它是附在食指上的一个圆环形光标。 根据邻近性，它会对目标的方向和大小做出动态反应，下面提供了详述：

* 将食指移向全息影像时，该光标始终与全息影像的表面平行，在移动过程中会逐渐缩小其大小。
* 一旦手指接触到表面，该光标就会缩小为一个点，并发出触摸事件。

借助交互式反馈，用户可以实现高精度的近距定位任务，例如，触发超链接，或按下某个按钮，如下所示。 

:::row:::
    :::column:::
       ![指尖光标远](images/Fingertip-cursor-far.jpg)<br>
       **指尖光标远**<br>
    :::column-end:::
    :::column:::
       ![指尖光标近](images/Fingertip-cursor-near.jpg)<br>
        **指尖光标近**<br>
    :::column-end:::
    :::column:::
       ![指尖光标接触](images/Fingertip-cursor-contact.jpg)<br>
       **指尖光标接触**<br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a>带有邻近着色器的边界框

全息影像本身还需要能够提供视频和音频反馈，以补偿触觉反馈的缺失。 为此，我们提出了带有邻近着色器的边界框的概念。 边界框是包含一个 3D 对象的紧凑立体区域。 边界框提供名为“邻近着色器”的交互式渲染机制。 邻近着色器的行为：

:::row:::
    :::column:::
       ![通过视觉反馈进行悬停（远）](images/bounding-box-with-proximity-shader-hover-far.jpg)<br>
       **悬停（远）**<br>
       当食指处于某个范围内时，指尖光点会投射到边界框的表面。
    :::column-end:::
    :::column:::
       ![通过视觉反馈进行悬停（近）](images/bounding-box-with-proximity-shader-hover-near.jpg)<br>
        **悬停（近）**<br>
        当指尖更靠近表面时，光点会收缩。
    :::column-end:::
    :::column:::
       ![接触开始](images/bounding-box-with-proximity-shader-begin-contact.jpg)<br>
       **接触开始**<br>
       一旦指尖接触到表面，整个边界框就会改变颜色，或生成视觉效果来反映触摸状态。
    :::column-end:::
    :::column:::
       ![接触结束](images/bounding-box-with-proximity-shader-end-contact.jpg)<br>
       **接触结束**<br>
       还可以激活某种音效来增强视觉触摸反馈。
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a>可按按钮

现在，用户可以使用可碰撞指尖来与一个基本的全息图 UI 组件（例如，可按按钮）进行交互。 可按按钮是专门用手指直接按下的全息图按钮。 同样，由于缺少触觉反馈，可按按钮配备了两个机制来解决触觉反馈相关的问题。

* 第一个机制是上一部分已详述的带有邻近着色器的边界框。 该机制可以在用户接近和接触到某个按钮时提供更好的邻近感。
* 第二个机制是沉降。 在指尖接触到按钮后，沉降可产生一种按入感。 此机制确保按钮在深度轴上如影随形地与指尖一起移动。 当指尖达到选定的深度（按下按钮），或者在移过按钮后脱离该深度（松开按钮）时，可以触发按钮。
* 触发按钮时，应该添加音效来增强反馈。

:::row:::
    :::column:::
       ![可按按钮远](images/pressable-button-far.jpg)<br>
       **手指远离**<br>
    :::column-end:::
    :::column:::
       ![可按按钮近](images/pressable-button-approach.jpg)<br>
        **手指接近**<br>
    :::column-end:::
    :::column:::
       ![可按按钮接触开始](images/pressable-button-contact.jpg)<br>
       **接触开始**<br>
    :::column-end:::
    :::column:::
       ![可按按钮按下](images/pressable-button-press.jpg)<br>
       **按下**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>2D 盖板交互

2D [盖板](slate.md)是用于承载 Web 浏览器等 2D 应用内容的全息容器。 通过直接操作来与 2D 盖板交互的设计概念和与物理触摸屏交互时一样。

### <a name="to-interact-with-the-slate-contact"></a>若要与盖板触点交互

:::row:::
    :::column:::
       ![触控](images/2d-slate-interaction-touch.jpg)<br>
       **触控**<br>
       使用食指按下某个超链接或按钮。
    :::column-end:::
    :::column:::
       ![滚动](images/2d-slate-interaction-scroll2.jpg)<br>
        **滚动**<br>
        使用食指上下滚动盖板内容。
    :::column-end:::
    :::column:::
       ![缩放](images/2d-slate-interaction-zoom2.jpg)<br>
       **缩放**<br>
       用户使用两根食指根据手指的相对运动来放大和缩小盖板内容。
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a>操作 2D 平板电脑本身

:::row:::
    :::column:::
       ![显示抓取和拖动功能的图形](images/manipulate-2d-slate-move.jpg)<br>
       **移动**<br>
       将手移近边角和边缘，显示最靠近的可视操作元素。 抓取 2D 盖板顶层的全息条，以移动整个盖板。
    :::column-end:::
    :::column:::
       ![显示缩放功能的图形](images/manipulate-2d-slate-scale.jpg)<br>
        **缩放**<br>
        抓取操作视觉元素，通过边角视觉元素执行统一的缩放。
    :::column-end:::
    :::column:::
       ![重新排列](images/manipulate-2d-slate-reflow.jpg)<br>
       **重新排列**<br>
       抓取操作视觉元素，通过编译视觉元素进行重排。
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a>3D 对象操作

HoloLens 2 可让用户将边界框应用到每个 3D 对象，以便用手引导和操作 3D 全息图对象。 边界框通过其邻近着色器提供更好的深度感。 使用边界框可以通过两种设计方法来操作 3D 对象。

### <a name="affordance-based-manipulation"></a>基于可视操作元素的操作

使用基于视觉元素的操作可以通过边界框及其周围的操作视觉元素来操作 3D 对象。 

:::row:::
    :::column:::
       ![显示对象边界框和移动功能的图形](images/3d-object-manipulation-move.jpg)<br>
       **移动**<br>
       一旦用户的手靠近某个 3D 对象，就会显示边界框和最靠近的视觉元素。 用户可以抓取边界框来移动整个对象。
    :::column-end:::
    :::column:::
       ![显示用户抓取对象边缘进行旋转的图形](images/3d-object-manipulation-rotate.jpg)<br>
        **旋转**<br>
        用户可以抓取边缘视觉元素执行旋转操作。
    :::column-end:::
    :::column:::
       ![显示用户抓取对象边角进行缩放的图形](images/3d-object-manipulation-scale.jpg)<br>
       **缩放**<br>
       用户可以抓取边角视觉元素进行统一缩放。
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a>不基于视觉元素的操作

非基于视觉元素的操作不会将任何视觉元素附加到边界框。 用户只能显示边界框，然后直接与它交互。 如果用一只手抓取边界框，则对象的平移和旋转将与手的动作和方向相关联。 用两只手抓取对象时，用户可以根据两只手的相对运动来平移、缩放和旋转该对象。

具体的操作需要精确。 我们建议使用 **基于视觉元素的操作**，因为它提供较高的粒度级。 若要灵活操作，我们建议使用 **非基于视觉元素的操作**，因为它可以实现充满乐趣的即时体验。

<br>

---


## <a name="instinctual-gestures"></a>本能手势

在 HoloLens（第 1 代）中，我们已向用户传授了几种预定义的手势，例如“开花”和“隔空敲击”。 对于 HoloLens 2，我们不要求用户记住任何符号手势。 用户与全息影像和内容交互所要使用的全部手势都是本能的。 实现本能手势的方法是通过 UI 视觉元素的设计帮助用户执行手势。

例如，如果我们建议用户使用夹紧的两根手指来抓取某个对象或控制点，该对象或控制点应该很小。 如果我们希望用户执行五指抓取，则该对象或控制点应该相对较大。 与按钮类似，按钮微小会导致用户使用单个手指将其按下的手势受限。 大按钮使用户更有可能用手掌将其按下。


:::row:::
    :::column:::
       ![显示用户抓取小型对象并移动的图形](images/instinctual-gestures-smallobject.jpg)<br>
       **小型对象**<br>
    :::column-end:::
    :::column:::
       ![显示用户抓取中等大小对象并移动的图形](images/instinctual-gestures-mediumobject.jpg)<br>
        **中型对象**<br>
    :::column-end:::
    :::column:::
       ![显示用户抓取大型对象并移动的图形](images/instinctual-gestures-largeobject.jpg)<br>
       **大型对象**<br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>手部与 6 DoF 控制器之间的对称设计

你可能已经注意到，我们可以在 AR 中的手部与 VR 中的运动控制器之间引入类似的交互方式。 使用这两种输入可在其各自的环境中触发直接操作。 在 HoloLens 2 中，用手近距抓取和拖放非常类似于在 WMR 运动控制器中抓取按钮。 因此，用户会熟悉这两个平台中的交互方式。如果你决定在平台之间移植应用程序，这种类似性会很有帮助。

<br>

---

## <a name="optimize-with-eye-tracking"></a>使用眼动跟踪进行优化

如果直接操作按预期方式运行，则用户可能会觉得它充满魔力。 但是，如果只能在无意触发全息影像的情况下才能四处移动手部，则直接操作可能会带来困扰。 眼动追踪可能有助于更好地识别用户的意图。

* **何时**：减少无意中触发操作响应的情况。 眼动追踪可以更好地识别用户当前正在与哪个对象互动。
例如，假设你在伸手抓取一个现实的工具时正在阅读某段全息图（说明）文本。

此外，你的手会意外地移过某些以前未曾注意到的交互式全息图按钮。 例如，也许这些按钮在用户的视场 (FoV) 以外。

如果用户有一段时间未注视某张全息影像，但检测到了该全息图的触摸或抓取事件，则有可能交互行为是意外发生的。

* **哪一个**：除了解决误报激活以外，另一个示例反映了眼动跟踪可以更好地识别要抓取或点击的全息影像，因为从你的立场来看，精确的交点可能并不明确，尤其是多个全息影像相互靠近时。

  尽管 HoloLens 2 上的眼动跟踪在如何准确确定视线方面存在限制，但对于近距交互，它仍可以提供帮助，因为使用手动输入交互时，存在深度差异。 举例而言，这意味着有时难以确定手是全息影像的前面还是后面，因此无法精确抓取某个操作小组件。

* **何处**：使用有关用户正在使用快速投射手势观看的内容的信息。 抓取一幅全息影像，然后大致将它投射到预期目标。  

    尽管有时可以正常进行此操作，但快速执行手势可能会导致目标极不准确。 但是，眼动跟踪可以提高手势的准确度。

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 的 MRTK（混合现实工具包）中的操作
有了 [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)，便可使用脚本 ObjectManipulator 轻松实现常见的操作行为 。 借助 ObjectManipulator，可以直接使用手或手部射线抓取和移动对象。 它还支持使用双手操作来缩放和旋转对象。

* [MRTK - 操作](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator)

---

## <a name="see-also"></a>另请参阅

* [头部凝视并提交](gaze-and-commit.md)
* [使用手指向和提交](point-and-commit.md)
* [本能交互](interaction-fundamentals.md)