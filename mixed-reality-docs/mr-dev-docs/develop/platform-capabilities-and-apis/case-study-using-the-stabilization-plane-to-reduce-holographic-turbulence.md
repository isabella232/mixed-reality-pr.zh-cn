---
title: 案例研究-使用稳定面
description: 探索我们的开发团队如何使用稳定平面来减少混合现实应用程序中的全息 turbulence。
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，全息影像，稳定性，案例研究，混合现实耳机，Windows Mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 4227be39c18e43ad712a14dd61217994a8fc761f41f9416b95b511be5396712a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202348"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>案例研究-使用稳定面减少全息 turbulence

使用全息影像通常比较棘手。 四处移动空间，从所有不同角度查看全息影像，可提供一种在普通计算机屏幕上不可用的浸入式级别。 将这些全息影像置于适当位置并真实地设计是由 Microsoft HoloLens 硬件和全息智能设计来实现的技术特征。

## <a name="the-tech"></a>技术人员

为了使全息影像看起来像是实际与你共享空间，它们应该正确呈现，无需颜色分离。 这是通过内置于 HoloLens 硬件的技术来实现的，该技术使全息影像定位在我们调用了一个稳定的[平面](hologram-stability.md#reprojection)上。

平面由点和法线定义。 由于我们始终希望飞机面对相机，因此，我们要考虑设置飞机的点。 我们可以告诉 HoloLens 要将其处理集中于哪个点，以使所有内容保持锚定和稳定。 但是，设置此焦点点是特定于应用的，并且可以根据内容创建或中断应用。

如果正确应用了稳定平面，则全息影像最有效，但实际的含义取决于要创建的应用程序的类型。 让我们看看当前提供的一些应用程序 HoloLens 如何解决此问题。

## <a name="behind-the-scenes"></a>幕后

在开发以下应用程序时，我们注意到，当我们没有使用飞机时，对象会在我们的打印头移动时使用 sway。 此外，还可以看到彩色隔离与打印头或全息图的移动。 我们结束了试用和错误如何最好地使用稳定平面，并围绕无法修复的问题设计应用程序。

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy 资源管理器：静止内容，三维交互

在此场景中， [Galaxy 资源管理器](../unity/galaxy-explorer.md)具有两个主要元素：天体内容的主视图和看看注视的小 UI 工具栏。 对于稳定性逻辑，我们将查看当前看上去向量与每个帧中的相交情况，以确定它是否达到了指定冲突层上的任何内容。 在这种情况下，我们感兴趣的层是行星，因此，如果注视落在地球上，则会将稳定平面放置在该处。 如果未命中目标冲突层中的任何对象，则应用将使用辅助 "计划 B" 层。 如果未在 gazed 任何内容，则稳定面将保持与 gazing 内容时的距离相同。 UI 工具将作为平面目标，正如我们发现，在接近到远处，降低了整体场景的稳定性。

Galaxy 资源管理器的设计适合于使其保持稳定并降低颜色分离的效果。 鼓励用户浏览内容，而不是从一边移动内容，而是轨道缓慢，以致颜色分离并不明显。 此外，还保留了恒定的 60 FPS，这在防止颜色分离发生的情况下是一种很长的方式。

若要亲自查看此问题，请在[GitHub 上的 Galaxy 资源管理器代码](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities)中查找名为 LSRPlaneModifier 的文件。

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio：带有 UI 焦点的固定内容

在 HoloStudio 中，大多数时候都在查看正在使用的同一模型。 如果你选择一个新工具或要浏览 UI，你的注视不会有很大的影响，因此，我们可以将平面设置逻辑保持简单。 查看 UI 时，平面将设置为您的 "注视" 对齐的任何 UI 元素。 查看模型时，平面是一组距离，与您与模型之间的默认距离相对应。

![在用户 gazes "主页" 按钮上进行可视化处理的稳定平面 HoloStudio](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour 和3D 查看器：包含动画和电影的静止内容

在 HoloTour 和3D 查看器中，您正在查看孤立动画对象或电影，其中添加了三维效果。 这些应用中的稳定设置为当前正在查看的内容。

HoloTour 还可以让你与你的虚拟世界 straying 得太远，而不是在固定位置继续。 这可以确保你不会从其他影像中获得足够的空间，以便在中进行爬出。

![在此示例中，HoloTour 为 Hadrian 的 Pantheon 的此电影。](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid：动态内容和环境交互

尽管应用程序需要突然移动，但在 RoboRaid 中设置稳定平面非常简单。 该平面靠近墙壁或周围的对象，并且在离您的距离足够远时，将在您前面固定距离。

RoboRaid 设计为在设计时考虑到了稳定性。 Reticle，它将最大程度地移动，因为它已被锁定，只使用红色和蓝色，这会最大程度地减少任何颜色。 它还包含各部分之间的一小部分深度，最大程度地减少了通过使用已预期的视差效果屏蔽的颜色出血。 机器人不会迅速移动，而且会按固定的时间间隔快速移动。 它们的正面往往围绕2米，在默认情况下，会设置稳定。

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>片段和年轻人 Conker：包含环境交互的动态内容

用 c + + 中的 Asobo Studio 编写，片段和年轻人 Conker 采用不同的方法来设置 "稳定" 平面。 POI) 的兴趣点 (在代码中定义，并按优先级排序。 Poi 是游戏中的内容，例如年轻人 Conker、菜单、目标 reticle 和徽标中的 Conker 模型。 Poi 与用户的 "注视" 相交，"平面" 设置为具有最高优先级的对象的中心。 如果未发生交集，则将平面设置为默认距离。

如果移动到之前已作为播放空间进行了扫描的内容，则片段和年轻人 Conker 还会通过暂停应用程序来设计离全息 straying 太远的位置。 因此，它们使你能够在提供最稳定的体验的边界内实现。

## <a name="do-it-yourself"></a>自制

如果你有 HoloLens 并且想要了解本文中的概念，你可以下载一个测试场景来尝试以下练习。 测试场景使用 Unity 的内置别出心裁 API 来帮助你直观显示你的平面的设置位置。 在此示例中，代码还用于捕获屏幕截图。
1. 同步最新版本的 [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)。
2. 打开 [HoloToolkit-Examples/公用事业/场景/StabilizationPlaneSetting](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity) 场景。
3. 生成并配置生成的项目。
4. 在设备上运行。

### <a name="exercise-1"></a>练习 1

你将看到不同方向的几个白点。 在您之前，您将在不同的深度看到三个点。 点击以更改平面设置为的点。 对于本练习，在这两个过程中，在 gazing 点时移动空间。 向左、向右、向上、向下旋转。 从点更接近或更远地移动。 查看稳定性平面设置为不同目标时，如何做出反应。

### <a name="exercise-2"></a>练习 2

现在，转到右侧，直到看到两个移动点、水平路径上的一个振荡和一个垂直路径上的一个。 同样，单击即可更改该平面设置为的点。 请注意颜色分离如何减少并显示在连接到平面的点上。 再次点击以在 "平面" 设置函数中使用点的速度。 此参数可提供有关对象的预期运动 HoloLens 提示。 了解何时使用这一点非常重要，因为当在一个圆点上使用了速度时，另一个移动点将显示更大的颜色分隔。 在设计应用程序时请牢记这一点，这会使对象的运动产生内聚性，从而有助于防止出现项目。

### <a name="exercise-3"></a>练习3

再次转到右侧，直到看到新的点配置。 在这种情况下，距离有一个点，其中有一个圆点在其前面加上一个点。 点击以更改平面设置为的点，在背面的点与运动中的点之间交替。 请注意，将平面位置与螺旋式点的速度设置为会使项目显示在任何位置。

**提示**
* 使平面设置逻辑简单。 如您所见，您不需要使用复杂的平面设置算法来实现沉浸式体验。 稳定平面只是一片谜。
* 在任何可能的情况下，始终在目标之间平稳移动平面。 即时切换到远处目标可能会以可视方式中断场景。
* 请考虑在飞机中设置一个选项，将逻辑锁定到特定目标。 这样一来，就可以根据需要在对象（如徽标或标题屏幕）上锁定平面。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>软件工程师 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另请参阅
* [MR 基础知识 100：Unity 入门](../unity/tutorials/holograms-100.md)
* [Unity 中的焦点](../unity/focus-point-in-unity.md)
* [全息影像稳定性](hologram-stability.md)
