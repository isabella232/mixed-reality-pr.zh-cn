---
title: 登月舱
description: 了解如何使用HoloLens跟踪和 Xbox 控制器输入扩展基本手势、创建反应对象以及实现菜单系统。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality， 示例应用， 设计， MRTK， 混合现实 Toolkit， Unity， 示例应用， 示例应用， 开源， Microsoft Store， HoloLens， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
ms.openlocfilehash: 50ca50acd2960ac7bfbd3a3595d7a3dfa4e69f06848919afe7c8f430c41aeaaf
ms.sourcegitcommit: 5977109661a1db4ee2be8ed532479342093303d5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2021
ms.locfileid: "116862604"
---
# <a name="lunar-module"></a>登月舱
![登月舱](../images/MRDL_LunarModule.jpg)

>[!NOTE]
>本文讨论我们在混合现实设计实验室中创建的探索示例，我们在该实验室[](https://github.com/Microsoft/MRDesignLabs_Unity)中分享有关混合现实应用开发的学习和建议。 随着我们进行新的发现，与设计相关的文章和代码将不断发展。

>[!NOTE]
>此示例应用专为第一代HoloLens设计。

[登月](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) 舱是 Microsoft 混合现实设计实验室提供的开源示例应用。 了解如何使用HoloLens跟踪和 Xbox 控制器输入扩展基本手势、创建对表面映射和平面查找反应的对象，以及实现简单的菜单系统。 项目的所有组件都可用于你自己的混合现实应用体验。

## <a name="demo-video"></a>演示视频 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IcIP]

使用 HoloLens 2 记录混合现实捕获

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>重新思考经典体验Windows Mixed Reality

在太空中，一条小型飞船从太空舱起，有条不从地调查下方的锯齿地形。 我们无限的试点发现一个合适的登陆区域。 这一下降是一种意外，但幸运的是，此旅程之前已经进行了多次...

![Atari 1979 年登月登陆者的原始接口](images/640px-atari-lunar-lander.png)<br>
*Atari 1979 年登月登陆者的原始接口*

[登月器](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) 是一种经典经典，玩家尝试将月球登陆器试飞到月球地形的平面位置。 20 世纪 70 年代出生的人很可能在一只飞地中花费数小时，眼睛粘在从天而降的这个向量飞船上。 当玩家在飞船上导航到登陆区域时，地形会缩放，以逐渐显示更多详细信息。 成功意味着在水平和垂直速度的安全阈值内登陆。 对于登陆时间以及剩余燃料，将授予点数，并基于登陆区域的大小进行乘数。

除了游戏之外，游戏的发明纪元还带来了控制方案不断的创新。 从最简单的四向步子和按钮配置 (在节奏人类 [) ](https://en.wikipedia.org/wiki/Pac-Man) 中，到 90 世纪 90 年代后期和 00 年代出现的高度特定且复杂的方案 (如在飞行模拟器和导轨) 。 登月机中使用的输入方案有两个原因：沉浸式和沉浸式。

![Atari 的登月登陆器控制台](images/atariconsole.png)<br>
*Atari 的登月登陆器控制台*

为什么 Atari 和其他许多游戏公司决定重新思考输入？

一个穿过一个子的儿童自然会被最新、最繁忙的计算机所动。 但登月者具有一种从人们中出来的新奇输入设备。

登月者使用两个按钮向左和向右旋转飞船，使用一个水动手柄来控制飞船产生的推力量。 此手柄为用户提供了常规手柄无法提供的一定级别的精细。 它也恰好是新式飞行中心通用的组件。 Atari 希望登月者能够让用户沉浸于他们实际上正在发射登月舱这一感觉中。 此概念称为 **"触感沉浸式"。**

触感沉浸式是执行重复操作时获得传感器反馈的体验。 在这种情况下，调整节流门和旋转的重复操作（我们眼睛看到和听到的响声）有助于将玩家连接到登月飞船的行为。 此概念可以与"流"这一科学概念关联。 如果用户完全专注于具有正确挑战和奖励组合的任务，或者更简单地说，他们"位于区域中"。

也许，混合现实中最突出的沉浸类型是空间沉浸。 混合现实的全部要点是欺骗自己，使这些数字对象存在于现实世界中。 我们正在合成我们周围的全息影像，在空间上沉浸于整个环境和体验中。 这并不意味着我们仍无法像 Atari 在登月登陆器中处理触感沉浸一样，在体验中采用其他类型的沉浸式。

## <a name="designing-with-immersion"></a>使用沉浸式进行设计

如何将触感沉浸式应用于 Atari 经典更新的 volumetric sequel？ 在处理输入方案之前，需要解决三维空间的游戏构造。

![在图像中可视化HoloLens](images/surfacemapping.png)<br>
*可视化图像中的空间HoloLens*

通过利用用户周围的环境，我们实际上有无限地形选项用于登陆登月舱。 若要使游戏最像原始标题，用户可能会操作并放置其环境中存在各种难题的登陆板。

要求用户学习输入方案、控制飞船以及登陆目标非常多。 成功的游戏体验具有挑战和奖励的合适组合。 用户可以选择一定的难度级别，最简单的模式只是要求用户成功登陆到用户定义区域上由用户扫描的HoloLens。 一旦用户获得游戏的挂起，他们就可以在认为合适的时候增加难度。

### <a name="adding-input-for-hand-gestures"></a>添加手势输入

HoloLens基本输入只有两个手势 - Air [Tap 和 Bloom](../../design/gaze-and-commit.md#composite-gestures)。 用户无需记住上下文细微差别或特定手势的丰富列表，使平台的界面既通用又易于学习。 虽然系统只能公开这两个手势，HoloLens设备一次可以跟踪两只手。 登月登陆器节点是一款[沉浸式应用，这意味着我们可以扩展基本手势集，以利用两只手，并添加自己的适合登月舱导航的触摸方式。

回顾原始控制方案， **我们需要解决旋转和旋转** 问题。 需要注意的是，新上下文中的旋转从技术角度 (两个轴，但 Y 轴对于登陆和) 。 两种不同的飞船移动自然适合映射到每只手：

![点击并拖动手势，在所有三个轴上旋转登陆器](images/module-handdrag.gif)<br>
*点击并拖动手势，在所有三个轴上旋转登陆器*

**推力**

映射到值刻度的原始机上的手柄移动得越高，对飞船应用的推力就越高。 此处要指出的一个重要细微差别是，用户如何从控件中下手并保持所需的值。 我们可以有效地使用点击和拖动行为来实现相同的结果。 开值从零开始。 用户点击并拖动以增大值。 此时，他们可以开始维护它。 任何点击和拖动手势值更改都会是原始值中的增量。

**旋转**

这有点棘手。 使用全息"旋转"按钮点击即可获得一种令人感到难受的体验。 没有可以利用的物理控件，因此该行为必须来自对表示登陆者的对象或登陆者本身的操作。 我们使用了一种使用点击和拖动的方法，该方法使用户能够按用户想要的方向有效地"推送和拉取"它。 每当用户点击并按住时，启动手势的空间点就会成为旋转的原点。 从原点拖动可转换手部平移的增量 (X、Y、Z) 并将其应用于登陆者旋转值的增量。 或者更简单地，向左<向右>向上拖动 *<->，* 在空格中向前<->可相应地旋转飞船。

由于HoloLens可以跟踪两只手，因此旋转可以分配给右侧，而运动由左侧控制。 Finesse 是在此游戏中取得成功的推动因素。 这些 *交互* 感觉是绝对最高优先级。 尤其是在触感沉浸式上下文中。 反应过快的飞船很难上手，而速度过慢的货轮需要用户在飞船上"推送和拉取"的时间非常长。

### <a name="adding-input-for-game-controllers"></a>添加游戏控制器的输入

虽然手势在HoloLens提供了一种全新的精细控制方法，但从模拟控件获取的"真实"触摸反馈仍然存在一定缺失。 通过连接 Xbox 游戏控制器，我们可恢复这种物理性，同时利用控制条保持精细控制。

有多种方法将相对直接的控制方案应用于 Xbox 控制器。 由于我们尝试尽可能靠近原始设置中的， **因此，"地图** "最好映射到触发器按钮。 这些按钮是模拟控件，这意味着它们具有多个简单的打开和关闭状态，它们实际上会响应对它们施加的压力程度。 这为我们提供了一个类似于"锁定" **的构造**。 与原始游戏和手势不同，一旦用户停止对触发器施加压力，此控件就会剪切飞船的手部。 它仍然为用户提供了与原始游戏相同的精细度。

![左滚动块映射到 Yaw 和 Roll，右 thumbstick 映射到"间距"和"滚动"](images/thumbsticksidebyside.gif)<br>
*左 thumbstick 映射到 yaw 和 roll;右滚动块映射到间距和滚动*

双指纹自然有助于控制飞船旋转。 遗憾的是，有三个轴可以旋转，两个滚动条都支持两个轴。 这种不匹配意味着一个操纵杆控制一个轴;或 thumbsticks 的轴重叠。 以前的解决方案最终会 "损坏"，因为 thumbsticks 原本会混合其本地 X 和 Y 值。 后一种解决方案需要进行一些测试，以发现哪些冗余轴感觉最自然。 最后一个示例使用 *偏航* 并 *滚动* 使用左侧操纵杆 (Y 和 x 轴) *，并为* 右操纵杆 *)  (Z 和 x* 轴。 这种感觉最自然的 *做法是，* 在 *偏航* 和 *音调* 上，自然会使其不受影响。 作为一条注释，同时使用两个 thumbsticks 进行 *滚动* 还会使旋转值翻倍;让 lander 执行循环非常有趣。

此示例应用演示了如何通过 Windows Mixed Reality 的可扩展输入情态，空间识别和 tactile 浸入式会显著改变体验。 虽然农历 Lander 可能接近40年，但使用这种小小的小小的概念却会永远不会出现。 在应该构想将来，为什么不会看到过去？

## <a name="technical-details"></a>技术详细信息

可在[混合现实设计实验室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule)中找到农历模块示例应用的脚本和 prototyping。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>用户体验设计师 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>请参阅

* [MRTK 示例中心](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [表面](sampleapp-surfaces.md) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [元素周期表 2.0](periodic-table-of-the-elements-2.md)
* [星系探索者 2.0](galaxy-explorer-update.md)