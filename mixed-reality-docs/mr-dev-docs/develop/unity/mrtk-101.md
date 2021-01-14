---
title: MRTK 101 - 使用通用空间交互
description: 对于 HoloLens 2、HoloLens、Windows Mixed Reality 和 Open VR，如何使用混合现实工具包 Unity 进行基本的交互。
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, 混合现实工具包, Windows Mixed Reality, 设计, 示例应用, 控件, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.localizationpriority: high
ms.openlocfilehash: ff3c6e055bca66fc5ad12548966140af8197235c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008937"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a>MRTK 101：如何使用混合现实工具包 Unity 进行常见的空间交互

![MRTK](images/MRTK101/MRTK101Cover.png)

了解如何使用 MRTK 在混合现实中实现最常用的交互模式。

- 如何在 Unity 编辑器中模拟输入交互？
- 如何抓取和移动对象？
- 如何调整对象的大小？
- 如何精确移动或旋转对象？
- 如何使对象响应输入事件？
- 如何添加视觉反馈？
- 如何添加音频反馈？
- 如何使用 HoloLens 2 样式按钮预制件？
- 如何使对象跟随你？
- 如何使对象朝向你？

> [!NOTE]
> 本文已经过更新，反映了 [MRTK v2.5.1 版本](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)中的更改

本页中的所有内容都可在 Unity 中使用 MRTK 的输入模拟进行测试。 如果你还没有，可按照 [MRTK 安装指南 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) 安装最新版本的 MRTK。

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a>如何在 Unity 编辑器中模拟输入交互？

MRTK 支持编辑器中的输入模拟。 单击 Unity 的播放按钮以运行场景，然后使用以下按键来模拟输入：
- 按 W、A、S、D 键可移动相机。
- 在按住鼠标右键的同时移动鼠标可以四处浏览。
- 按空格键（右手）或左 Shift 键（左手）以显示模拟双手
- 按 T 或 Y 键以将模拟双手保持在视野中
- 按 Q 或 E（水平）/R 或 F（垂直）来旋转模拟双手

可以在 [MRTK 文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)中详细了解输入模拟。

## <a name="how-to-grab-and-move-an-object"></a>如何抓取和移动对象？

附加 ObjectManipulator.cs 和 NearInteractionGrabbable.cs 脚本，使对象可抓取 。 ObjectManipulator 支持近距离和远距离交互。 可以使用 HoloLens 2 的精确手动跟踪输入（近距）、手部射线（远距）、运动控制器光束（远距）、HoloLens 凝视光标和隔空敲击（远距）来抓取和移动对象。

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a>如何调整对象的大小？
ObjectManipulator.cs 支持双手缩放/旋转。 此脚本适用于各种输入类型，例如 HoloLens 2 的精确手动输入、HoloLens 1 的凝视 + 手势输入，以及 Windows Mixed Reality 沉浸式头戴显示设备的运动控制器输入。

- [在 MRTK 文档中详细了解对象处理程序](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>如何精确移动或旋转对象？
将 BoundsControl.cs 分配到某个对象以使用边界框（用于缩放和旋转对象的界面）。 默认情况下，该脚本会显示 HoloLens 1 样式的蓝色控点和线条。 若要使用基于 HoloLens 2 样式邻近性的动画控点，需要分配预制件和材料。 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [在 MRTK 文档中详细了解边界控制](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a>如何使对象响应输入事件？
将 PointerHandler.cs 分配到某个对象。 在检查器中，可使用事件 OnPointerDown()、OnPointerUp()、OnPointerClicked() 和 OnPointerDragged()。若要在脚本中使用这些事件，请实现 IMixedRealityPointerHandler。

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [在 MRTK 文档中详细了解输入系统](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>如何添加视觉反馈？
将 Interactable.cs 分配到某个对象。 在检查器中，添加目标对象并创建新主题。 使用 Interactable 的主题配置文件可以轻松将视觉反馈添加到所有可用的输入交互状态。

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Interactable 提供各种类型的主题，包括着色器主题，该主题可用于控制每种交互状态的着色器的属性。

- [在 MRTK 文档中详细了解 Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

视觉反馈的另一个重要构建基块是 MRTK 标准着色器。 使用 MRTK 标准着色器可以轻松添加视觉反馈效果，例如悬停光线和邻近光线。 由于 MRTK 标准着色器占用的计算资源要比 Unity 标准着色器少，因此你可以创建高性能的体验。

创建新材料，然后选择着色器的“混合现实工具包”>“标准”。 或者，可以选择某个使用 MRTK 标准着色器的现有材料。

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [在 MRTK 文档中详细了解 MRTK 标准着色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>如何添加音频反馈？
将 AudioSource 添加到某个对象。 然后，在公开输入事件的脚本（例如 Interactable.cs 或 PointerHandler.cs）中，将带有 AudioSource 的对象分配到该事件，并选择 AudioSource.PlayOneShot()。 可以使用自己的音频剪辑，或从 MRTK 的音频资产中进行选择。

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a>如何使用 HoloLens 2 样式按钮预制件？
MRTK 提供了各种类型的 HoloLens 2 shell (OS) 样式按钮，包括邻近感应光、压缩框和按钮表面的波纹效果等视觉反馈，可增强用户的信心。

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

将某个 HoloLens 2 样式的可按按钮预制件拖放到场景中即可。 该预制件将使用前面介绍的 Interactable.cs。 可以使用 Interactable 中公开的事件（例如 OnClick()）来触发操作。

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [在 MRTK 文档中详细了解按钮预制件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a>如何使对象跟随你？
将 RadialView.cs 或 Follow.cs 脚本分配到某个对象 。 此脚本是解算器脚本系列的一部分，可用于在 3D 空间中实现各种类型的对象定位。 将自动添加 SolverHandler.cs。
下面是 RadialView 配置的一个示例，它可以实现“惰性跟踪”追随行为，就如同使用 HoloLens shell 中的“开始”菜单一样。 可以指定最小/最大距离和最小/最大视图角度。 以下示例演示如何在 0.4 到 0.8 米范围内以 15° 的视图角度定位对象。 调整“线性插值时间”值，以加快或减慢定位更新的速度。

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [在 MRTK 文档中详细了解解算器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a>如何使对象朝向你？
将 Billboard.cs 脚本分配到某个对象。 不管你处于哪个位置，该对象都会朝向你。 可以指定枢轴选项。

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


准备好创建令人惊叹的混合现实体验了吗？ 请访问以下页面来详细了解 MRTK 和混合现实。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>用户体验设计师 @Microsoft</td>
</tr>
</table>

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们规划的 Unity 的开发检查点旅程，则你在探索 MRTK 核心构建基块的过程中。 从这里，你可以继续了解下一部分基础知识： 

> [!div class="nextstepaction"]
> [摄像头](camera-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅
* [MRTK 安装指南 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [混合现实工具包 - Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [MRTK 文档门户 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [HoloToolkit 到 MRTK 的移植指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
