---
title: 登月舱
description: 了解如何通过两个右手跟踪和 Xbox 控制器输入来扩展 HoloLens 的基本手势，创建反应对象并实现菜单系统。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，示例应用，设计，MRTK，混合现实工具包，Unity，示例应用，示例应用，开源，Microsoft Store，HoloLens，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: 797e8d5ea4d72d1c19ee167ff655f99ab37da271
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300182"
---
# <a name="lunar-module"></a>登月舱

>[!NOTE]
>本文讨论了我们在 [混合现实设计实验室](https://github.com/Microsoft/MRDesignLabs_Unity)中创建的探索示例，这是我们与混合现实应用开发的知识和建议。 我们设计相关的文章和代码将随着我们的新发现而发展。

[阴历模块](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) 是 Microsoft 混合现实设计实验室的开源示例应用。 了解如何通过两个右手跟踪和 Xbox controller 输入来扩展 HoloLens 的基本手势，创建被动于 surface 贴图和飞机查找并实现简单菜单系统的对象。 所有项目组件都可以在自己的混合现实应用体验中使用。

## <a name="demo-video"></a>演示视频 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IcIP]

使用混合现实捕获记录了 HoloLens 2

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Windows Mixed Reality 的反思经典体验

在氛围中，Apollo 模块的小发货让人想起是的一小小船调查地形。 我们的 fearless 试点是合适的登录区域。 下降是棘手的，但令人欣慰，这一旅程在 .。。

![来自 Atari 的1979农历 Lander 的原始接口](images/640px-atari-lunar-lander.png)<br>
*来自 Atari 的1979农历 Lander 的原始接口*

[农历 Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) 是一种拱廊类经典的，其中播放机尝试将月球 Lander 试点到农历地形的平整点上。 在一段时间内，任何人都在拱廊类，其眼睛粘附到了此向量 plummeting。 当玩家向登陆领域导航时，地形会进行缩放以揭示更详细的信息。 成功意味着在水平和垂直的安全阈值内进行登录。 使用 "登陆" 和 "剩余燃料" 的时间来奖励点，并根据登陆区域的大小进行调整。

除了游戏，游戏的拱廊类时代带来了控制方案的不断创新。 从最简单的四向操纵杆和按钮配置中 (在图标 [Pac-Man](https://en.wikipedia.org/wiki/Pac-Man)) 中发现了在90的后期和 00s (如高尔夫模拟器和铁路 shooters) 中的高度特定、复杂的方案。 农历 Lander 计算机中使用的输入方案为耐人寻味，原因有两个：路缘和浸入式。

![Atari 农历 Lander 的拱廊类控制台](images/atariconsole.png)<br>
*Atari 的农历 Lander 拱廊类控制台*

为什么 Atari 和其他许多游戏公司决定重新思考输入？

一拱廊类的孩子将自然兴趣最新的 flashiest 机。 但农历 Lander 是 novel 输入 mechanic，可从那个的。

农历 Lander 使用两个按钮来旋转向左和向右旋转，并使用 **主旨是杠杆** 来控制发运产生的主旨是量。 此杠杆为用户提供了一个 finesse 的常规游戏杆级别。 这也是新式航空考核中心的常见组成部分。 Atari 希望阴历 Lander 从而深入了解用户，他们认为他们实际上是一个农历模块。 此概念称为 **tactile 浸入式**。

Tactile 浸入式是执行重复操作的传感器反馈。 在这种情况下，调整调节杆和旋转的重复操作（我们的眼睛和我们的产品/服务）可帮助将播放机连接到月球的 "登陆" 的行为。 此概念可以绑定到 "flow" 的心理概念。 用户完全完全吸收在一项任务中，该任务具有挑战和奖励的适当组合，或者更简单地说，他们是 "在区域中"。

在混合现实中，最明显的浸入式类型是空间浸入式。 混合现实的整个点是为了使自己相信这些数字对象存在于现实世界中。 我们正在综合的环境中，在整个环境和体验中空间沉浸。 这并不意味着我们在我们的体验中仍不能使用其他类型的浸入式，正如 Atari 在农历 Lander 中 tactile 浸入式。

## <a name="designing-with-immersion"></a>用浸入式进行设计

如何将 tactile 浸入式应用于已更新的容量耗尽脚步到 Atari 经典？ 在处理输入方案之前，需要对三维空间的游戏构造进行寻址。

![在 HoloLens 中可视化 surface 映射](images/surfacemapping.png)<br>
*在 HoloLens 中可视化空间映射*

通过利用用户的周围环境，我们为农历模块提供了无限地形的选项。 若要使游戏与原始标题最为相似，用户可能会在其环境中操作并将登录控制置于不同的难题。

![飞行农历模块](images/640px-lm-hero.jpg)<br>
*飞行农历模块*

要求用户了解输入方案，控制发运，并向土地提供小目标，这是一个需要考虑的事情。 成功的游戏体验具有挑战和回报的正确组合。 用户可以选择一种难易程度，最简单的模式就是要求用户成功地在由 HoloLens 扫描的图面上的用户定义区域中进行。 一旦用户进入了游戏的挂起状态，他们就可以曲柄，

### <a name="adding-input-for-hand-gestures"></a>添加手势输入

HoloLens 基本输入只包含两个笔势： " [Air" 和 "布隆](../../design/gaze-and-commit.md#composite-gestures)"。 用户无需记住上下文的细微差别，也不需要了解特定手势的详细列表，使平台界面可广泛使用，并且易于学习。 尽管系统可能只公开这两个手势，但作为一种设备，HoloLens 可以同时跟踪两次。 我们的 o) 到农历 Lander 是一个 [沉浸式应用程序，这意味着我们可以扩展基准手势集来利用两个手势，并为农历的 "" 导航添加自己的适合 tactile。

查看原始控制方案， **我们需要解决主旨是和旋转**。 特别要注意的是，在新上下文中的旋转会在技术上添加另一个轴 (，但 Y 轴对于登陆) 不太重要。 这两个不同的发货变动自然会使自身彼此映射：

![点击并拖动手势，旋转所有三个轴上的 lander](images/module-handdrag.gif)<br>
*点击并拖动手势，旋转所有三个轴上的 lander*

**主旨是**

原始拱廊类机上的杠杆映射到一小数值，移动的杠杆越大，就会将更多的主旨是应用于发货。 此处指出的一项重要的细微差别是用户可以如何从控件中进行操作并维护所需的值。 我们可以有效地使用点击和拖动行为来获得相同的结果。 主旨是值从零开始。 用户点击并拖动以增加值。 此时，他们可以继续维护它。 任何点击并拖动笔势值的更改将是原始值的增量。

**旋转**

这有点棘手。 通过使用全息的 "旋转" 按钮，您可以获得更丰富的体验。 没有要利用的物理控件，因此该行为必须从表示 lander 的对象或 lander 本身的操作来处理。 我们使用点击和拖动方法来提供方法，使用户能够有效地 "推送并拉取" 其所需的方向。 用户点击并按住时，启动笔势的空间中的点就成为旋转的原点。 从原点拖动会将手平移的增量转换 (X、Y、Z) ，并将其应用于 lander 旋转值的增量。 更简单的一点是， *向上拖动 <-> 右，向上 <-> 向下，向前 < 中的 > 返回空格，并相应地旋转*。

由于 HoloLens 可以跟踪两次，因此，在主旨是由左侧控制时，可以向右手分配旋转。 Finesse 是在此游戏中取得成功的驱动因素。 这些交互的 *外观* 是绝对最高的优先级。 尤其是在 tactile 浸入式的上下文中。 如果发货反应太快，则很难做出反应，而速度太慢，则会要求用户在 awkwardly 长时间内 "推送并请求"。

### <a name="adding-input-for-game-controllers"></a>添加游戏控制器的输入

尽管 HoloLens 上的手势提供了 novel 的精细控制方法，但仍有特定的 tactile 反馈，那就是你从模拟控件中获得的反馈。 通过连接 Xbox 游戏控制器，我们可以 physicality 这种功能，同时利用控制杆来保持精细的控制。

可以通过多种方式将相对直接的控件方案应用于 Xbox 控制器。 由于我们尝试尽可能接近原始拱廊类设置，因此最好将 **主旨是** 映射到触发器按钮。 这些按钮是模拟控件，这意味着它们的 *开启和关闭* 状态大于简单状态，它们实际上会响应施加的压力。 这为我们提供了类似于 **主旨是杠杆** 的结构。 与原始游戏和手手势不同，此控制会在用户停止对触发器的压力后，就会主旨是。 它仍为用户提供与原始拱廊类游戏相同的 finesse。

![左操纵杆映射到偏航并滚动，将右操纵杆映射到螺距并滚动](images/thumbsticksidebyside.gif)<br>
*左操纵杆映射到偏航并滚动向右操纵杆映射到间距和滚动*

双重 thumbsticks 自然会为控制运输旋转提供控制。 遗憾的是，发货可以旋转三个轴，两个均支持两个轴的 thumbsticks。 这种不匹配意味着一个操纵杆控制一个轴;或 thumbsticks 的轴重叠。 以前的解决方案最终会 "损坏"，因为 thumbsticks 原本会混合其本地 X 和 Y 值。 后一种解决方案需要进行一些测试，以发现哪些冗余轴感觉最自然。 最后一个示例使用 *偏航* 并 *滚动* 使用左侧操纵杆 (Y 和 x 轴) *，并为* 右操纵杆 *)  (Z 和 x* 轴。 这种感觉最自然的 *做法是，* 在 *偏航* 和 *音调* 上，自然会使其不受影响。 作为一条注释，同时使用两个 thumbsticks 进行 *滚动* 还会使旋转值翻倍;让 lander 执行循环非常有趣。

此示例应用演示了如何通过 Windows Mixed Reality 的可扩展输入情态，空间识别和 tactile 浸入式可以显著改变体验。 虽然农历 Lander 可能接近40年，但使用这种小小的小小的概念却会永远不会出现。 在应该构想将来，为什么不会看到过去？

## <a name="technical-details"></a>技术详细信息

可在 [混合现实设计实验室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule)上查找农历模块示例应用的脚本和 prototyping。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>用户体验设计师 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另请参阅

* [MRTK 示例中心](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [表面](sampleapp-surfaces.md) - [（从 HoloLens 2 中的 Microsoft Store 下载）](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [元素周期表 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [星系探索者 2.0](galaxy-explorer-update.md)
