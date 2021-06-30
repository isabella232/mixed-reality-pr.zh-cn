---
title: 全息影像稳定性
description: HoloLens 自动稳定全息影像，但开发人员可以执行一些步骤来进一步提高全息影像的稳定性。
author: thetuvix
ms.author: alexturn
ms.date: 07/08/2020
ms.topic: article
keywords: 全息影像、稳定性、全息影像、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、帧速率、渲染、重现、颜色分离
appliesto:
- HoloLens
ms.openlocfilehash: a4a22221d3238bb7dfed711e6ee1f11edc70238e
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042288"
---
# <a name="hologram-stability"></a>全息影像稳定性

为了实现稳定的全息影像，HoloLens 具有内置的图像稳定管道。 稳定管道在后台自动工作，因此无需执行任何额外的步骤来启用它。 但是，应练习提高全息影像稳定性和避免降低稳定性的方案的技术。

## <a name="hologram-quality-terminology"></a>全息影像质量术语

全息影像的质量是良好的环境和良好的应用开发的结果。 在 HoloLens 可以跟踪周围的环境中以恒定每秒 60 帧运行的应用可确保全息影像和匹配的坐标系保持同步。从用户的角度来看，旨在固定全息影像不会相对于环境移动。

在识别环境问题、呈现速率不一致或低或其他任何内容时，以下术语可以帮助你。
* **精度。** 全息影像被世界锁定并放置在现实世界中后，它应保持相对于周围环境的放置位置，而不受用户运动或小型稀疏环境更改的影响。 如果全息影像稍后出现在意外位置，则 *这是准确性问题* 。 如果两个不同的房间看起来相同，可能会发生此类情况。
* **抖动。** 用户观察到抖动是全息影像的高频率抖动，当环境的跟踪降级时，可能会发生这种情况。 对于用户，解决方案正在运行 [传感器优化](/hololens/hololens-updates)。
* **Judder。** 低渲染频率会导致全息影像的不均匀运动和双倍图像。 在具有动作的全息影像中，Judder 尤其明显。 开发人员需要保持恒定 [的 60 FPS](hologram-stability.md#frame-rate)。
* **漂移。** 用户看到偏移，因为全息影像似乎从最初放置的位置移开。 将全息影像放在远离空间定位点的位置时，[](../../design/spatial-anchors.md)会发生偏移，尤其是在环境的未映射部分。 创建靠近空间定位点的全息影像可以降低偏移的可能性。
* **跳转。** 当全息影像偶尔"弹出"或"跳转"离开其位置时。 当跟踪调整全息影像以匹配对环境的更新理解时，可能会出现跳转。
* **游泳。** 当全息影像看起来与用户头部运动相对应时。 如果应用程序尚未完全实现重新保护，并且 HoloLens 未为当前用户校准，则会发生流。 [](hologram-stability.md#reprojection) [](/hololens/hololens-calibration) 用户可以重新运行校准 [应用程序](/hololens/hololens-calibration) 来解决此问题。 开发人员可以更新稳定平面以进一步增强稳定性。
* **颜色分离。** HoloLens 中的显示是颜色顺序显示，60 Hz 的红色-绿色-蓝-绿的闪烁颜色通道 (单个颜色字段以 240 Hz) 。 每当用户用眼睛跟踪移动的全息影像时，该全息影像的前导和尾随边缘会以其构成颜色分开，从而产生一种闪烁效果。 分离程度取决于全息影像的速度。 在某些极少数情况下，在查看固定全息影像时快速移动全息影像也会导致一种光栅效果，这称为 *["颜色分离"。](hologram-stability.md#color-separation)*

## <a name="frame-rate"></a>帧速率

帧速率是全息影像稳定性的第一大支柱。 若要让全息影像在世界上稳定显示，向用户呈现的每个图像都必须在正确的位置绘制全息影像。 HoloLens 上的显示每秒刷新 240 次，显示每个新渲染的图像的四个单独的颜色字段，从而获得每秒 60 FPS (帧的用户体验) 。 为了尽可能提供最佳体验，应用程序开发人员必须维护 60 FPS，这转换为每 16 毫秒向操作系统提供一次新映像。

**60 FPS** 若要绘制全息影像，使其看起来像在现实世界中，HoloLens 需要从用户的位置渲染图像。 由于图像呈现需要时间，因此 HoloLens 预测当图像显示在显示器中时，用户的头部位置。 但是，此预测算法是近似值。 HoloLens 的硬件可调整呈现的图像，以考虑预测的头位置与实际头部位置之间的差异。 调整会使用户看到的图像看起来就像从正确的位置呈现一样，并且全息影像感觉稳定。 图像更新最适合进行少量更改，并且无法完全修复呈现的图像中的某些内容，如运动视差。

通过以 60 FPS 呈现，你将执行三项操作来帮助制作稳定的全息影像：
1. 最大程度地降低呈现图像与用户看到的图像之间的总体延迟。 在具有游戏且呈现线程在锁步中运行的引擎中，以 30FPS 运行可能会增加 33.3 毫秒的额外延迟。 降低延迟可减少预测错误，提高全息影像稳定性。
2. 这样，到达用户眼睛的每张图像都有一致的延迟量。 如果以 30 fps 呈现，则显示器仍以 60 FPS 显示图像，这意味着同一图像将在一行中显示两次。 第二帧的延迟比第一帧多 16.6 毫秒，并且必须更正更明显的错误量。 错误量级中的这种不一致可能会导致不需要的 60 Hz 放大器。
3. 减轻视觉上的抖动，其特征是运动不均衡和重影。 全息影像运动速度越快且渲染速率越低，抖动就越明显。 如果始终保持 60 FPS，将有助于避免给定移动全息影像的灰度。

**帧速率一致性** 帧速率一致性与每秒高帧数一样重要。 对于内容丰富的应用程序，偶尔丢弃的帧都无可避免，HoloLens 实现了一些复杂的算法，以从偶尔的故障中恢复。 但是，不断波动的帧速率比以较低的帧速率持续运行更明显。 例如，如果应用程序在这五个帧) 的持续时间内平滑呈现五帧 (60 FPS，然后在这 1) 0 帧 (30 FPS 内每隔一帧删除 30 FPS，则该应用程序看起来比以 30 FPS 一致呈现的应用程序更加不稳定。

在相关说明中，当混合现实捕获运行时，操作系统将应用程序限制为 30 FPS。 [](/hololens/holographic-photos-and-videos)

**性能分析** 有不同类型的工具可用于对应用程序帧速率进行基准测试，例如：
* GPUView
* Visual Studio 图形调试器
* 内置于 3D 引擎（如 Unity）的探查器

## <a name="hologram-render-distances"></a>全息影像呈现距离

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

人类视觉系统在固定并专注于对象时集成多个与距离相关的信号。
* [调整](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) - 单个眼睛的焦点。
* [收](https://en.wikipedia.org/wiki/Convergence_(eye)) 敛 - 两只眼睛在对象上向内或向外移动。
* [双眼视觉](https://en.wikipedia.org/wiki/Stereopsis) - 依赖于对象与固定点的距离的左眼和右眼图像的差异。
* 着色、相对角大小和其他单眼 (视觉) 提示。

收敛和调整是唯一的，因为它们的额外视素提示与眼睛如何改变以不同距离感知对象有关。 在自然观看中，收敛和调整是链接的。 例如，当眼睛看到 (，你的眼睛) ，眼睛交叉并适应近点。 当眼睛在无穷大看到某些内容时，眼睛变为并行，眼睛适应无穷大。 

使用 HoloLens 的用户将始终适应 2.0 米以保持清晰的图像，因为 HoloLens 显示器固定在距离用户约 2.0 米的光学距离上。 应用开发人员通过将内容和全息影像放置在各种深度来控制用户眼睛的聚合位置。 当用户适应并聚合到不同的距离时，这两个提示之间的自然链接会断开，这可能会导致视觉障碍，尤其是在冲突量很大时。 

通过尽可能将聚合内容保持为接近 2.0 米（即，在具有大量深度的场景中）将兴趣区域放在约 2. (0 米的位置（如果可能) ）可以避免或最小化来自自我调整-适应冲突的风险。 当无法将内容放在 2.0 米附近时，当用户在不同距离之间来回凝视时，来自自我适应冲突的症状最大。 换言之，观看 50 厘米远的静态全息影像，比观看 50 厘米远的前后不断移动的全息影像要舒适得多。

将内容放在 2.0 米位置也有利，因为两个显示器设计为在此距离完全重叠。 对于放置在此平面上的图像，当图像从全息帧的一侧移开时，它们会显示在一个显示器上，而在其他显示器上仍可见。 这种二眼性功能可能会干扰全息影像的深度感知。

**全息影像与用户之间的最佳距离**

![全息影像与用户之间的最佳距离](images/distanceguiderendering-750px.png)

**剪贴平面** 为获得最大舒适感，我们建议将渲染距离剪裁为 85 cm，从 1 米开始淡出内容。 在全息影像和用户都处于固定状态的应用程序中，可以非常轻松地查看接近 50 cm 的全息影像。在这种情况下，应用程序应放置不超过 30 cm 的剪贴平面，淡出应从剪辑平面开始至少 10 cm。 每当内容接近 85 cm 时，必须确保用户不经常离全息影像更近或更远，或者全息影像不会频繁靠近或远离用户，因为这些情况最有可能导致与行为-适应冲突产生不便。 内容应设计为最大程度地减少与用户距离不超过 85 cm 的交互需求，但当内容必须呈现接近 85 cm 时，开发人员的一个良好经验法则是设计用户和/或全息影像在 25% 以上的时间深度移动的方案。

**最佳做法** 如果全息影像不能放置在 2 米，并且无法避免收敛和调整之间的冲突，则全息影像放置的最佳区域介于 1.25 米到 5 米之间。 在每种情况下，设计者都应构建内容，以鼓励用户在 1 米 (交互，例如，调整内容大小和默认放置) 。

## <a name="reprojection"></a>重新保护
HoloLens 具有一种复杂的硬件辅助全息稳定技术，称为重新投影。 当场景进行动画处理和用户移动其头部时，重新 (会考虑 CameraPose) 运动和视点更改。  应用程序需要执行特定操作才能充分利用 reprojection。


有四种主要类型的 reprojection
* **深度 Reprojection：**  从应用程序生成最少工作量的最佳结果。  呈现的场景的所有部分都基于用户与用户之间的距离进行了单独的稳定。  某些呈现项目在深度变化时可能会可见。  此选项仅在 HoloLens 2 和沉浸式耳机上可用。
* **平面 Reprojection：**  允许应用程序精确控制稳定。  平面由应用程序设置，该平面上的所有内容将是场景中最稳定的部分。  全息图离飞机的更好，就是不太稳定。  此选项在所有 Windows MR 平台上可用。
* **自动平面 Reprojection：**  系统使用深度缓冲区中的信息设置稳定平面。  此选项在 HoloLens 第1代和 HoloLens 2 上可用。
* **无：** 如果应用程序不执行任何操作，则会在用户的打印头注视方向上，将平面 Reprojection 与以2米固定的稳定平面一起使用，通常会生成未达标准的结果。

应用程序需要执行特定操作才能启用不同类型的 reprojection
* **深度 Reprojection：** 应用程序将每个呈现的帧的深度缓冲区提交给系统。  在 Unity 上，在 " **XR 插件管理**" 下的 " **Windows Mixed Reality 设置**" 窗格中，通过 "**共享深度缓冲区**" 选项完成深度 Reprojection。  DirectX 应用调用 CommitDirect3D11DepthBuffer。  应用程序不应调用 SetFocusPoint。
* **平面 Reprojection：** 在每个帧上，应用程序会告诉系统要稳定的平面位置。  Unity 应用程序调用 SetFocusPointForFrame，并应禁用 **共享深度缓冲** 。  DirectX 应用调用 SetFocusPoint，不应调用 CommitDirect3D11DepthBuffer。
* **自动平面 Reprojection：** 若要启用，应用程序需要将其深度缓冲区提交给系统，因为它们的深度 Reprojection。 使用混合现实工具包 (MRTK) 的应用可以将 [照相机设置提供程序](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings#hololens-2-reprojection-method) 配置为使用 AutoPlanar Reprojection。 本机应用应将 `DepthReprojectionMode` [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters) 中的设置为 `AutoPlanar` 每个框架。 对于 HoloLens 第1代，应用程序不应调用 SetFocusPoint。

### <a name="choosing-reprojection-technique"></a>选择 Reprojection 技术

稳定类型 |    沉浸式头戴显示设备 |    HoloLens 第1代 | HoloLens 2
--- | --- | --- | ---
深度 Reprojection |    建议 |   空值 |   建议<br/><br/>Unity 应用程序必须使用 Unity 2018.4.12 +、Unity 2019.3 + 或 Unity 2020.3 +。 否则，请使用自动平面 Reprojection。
自动平面 Reprojection | 空值 |   建议默认值 |   如果深度 Reprojection 未提供最佳结果，建议使用<br/><br/>建议 unity 应用程序使用 Unity 2018.4.12 +、Unity 2019.3 + 或 Unity 2020.3 +。  以前的 Unity 版本将使用略微降级的 reprojection 结果。
平面 Reprojection |   不建议使用 |   如果自动平面未提供最佳结果，建议使用 | 如果两个深度选项都不能获得所需的结果，请使用    

### <a name="verifying-depth-is-set-correctly"></a>验证深度设置正确
            
当 reprojection 方法使用深度缓冲区时，验证深度缓冲区的内容是否表示应用程序的呈现场景很重要。  许多因素可能导致问题。 例如，如果有另一个相机用于渲染用户界面覆盖，则可能会覆盖实际视图中的所有深度信息。  透明对象通常不会设置深度。  某些文本呈现默认情况下不设置深度。  当深度与呈现的全息影像不匹配时，呈现会出现明显的问题。
            
HoloLens 2 有一个可视化工具，用于显示深度的位置和未设置，可从设备门户启用。  在 "**查看**  >  **全息图稳定性**" 选项卡上，选择 "**在耳机中显示深度可视化**" 复选框。  深度设置正确的区域将为蓝色。  没有深度集的呈现项将标记为红色，需要修复。  

> [!NOTE]
> 视觉对象的视觉对象将不会在混合现实捕获中显示。  它仅在设备上可见。
            
某些 GPU 查看工具将允许可视化深度缓冲区。  应用程序开发人员可以使用这些工具来确保正确设置深度。  请参阅应用程序工具的文档。

### <a name="using-planar-reprojection"></a>使用平面 Reprojection
> [!NOTE]
> 对于桌面沉浸式耳机，设置稳定面通常会提高效率，因为它提供的视觉质量不如向系统提供应用的深度缓冲区来启用基于深度的 reprojection。 除非在 HoloLens 上运行，否则通常应避免设置稳定平面。

![三维对象的稳定平面](images/stab-plane-500px.jpg)

设备将自动尝试选择此平面，但应用程序应通过选择场景中的焦点来提供帮助。 在 HoloLens 上运行的 Unity 应用应根据场景选择最佳关注点，并将其传递到 [SetFocusPoint () ](../unity/focus-point-in-unity.md)。 默认的旋转多维数据集模板中包含了在 DirectX 中设置焦点的示例。

当你在连接到台式计算机的沉浸式耳机上运行应用时，Unity 将向 Windows 提交深度缓冲区以启用每像素 reprojection，这可提供更好的图像质量，无需应用显式工作。 仅当应用程序在 HoloLens 上运行时，才应提供焦点，否则会重写每像素 reprojection。


```cs
// SetFocusPoint informs the system about a specific point in your scene to
// prioritize for image stabilization. The focus point is set independently
// for each holographic camera.
// You should set the focus point near the content that the user is looking at.
// In this example, we put the focus point at the center of the sample hologram,
// since that is the only hologram available for the user to focus on.
// You can also set the relative velocity and facing of that content; the sample
// hologram is at a fixed point so we only need to indicate its position.
renderingParameters.SetFocusPoint(
    currentCoordinateSystem,
    spinningCubeRenderer.Position
    );
```

焦点的位置很大程度上取决于全息图所查看的内容。 应用具有用于引用的 "注视" 向量，应用设计器知道他们希望用户看到哪些内容。

开发人员可对稳定全息影像执行的最重要的一项操作是以 60 FPS 的帧呈现。 如果低于 60 FPS，将大大减少全息图稳定性，无论是什么稳定性平面优化。

**最佳做法** 没有通用的方法来设置稳定平面，它是特定于应用的。 我们的主要建议是试验并了解哪种方法最适合你的方案。 但是，请尽量将稳定平面与尽可能多的内容对齐，因为此平面上的所有内容都是完美稳定的。

例如：
* 如果只有平面内容 (读取应用程序、视频播放应用) ，请将稳定平面与包含内容的平面对齐。
* 如果有三个小球体处于世界锁定状态，则会使 "稳定" 平面成为当前用户视图中所有球的中心。
* 如果场景的内容在深度上非常不同，则更倾向于获取更多对象。
* 确保调整每个帧的稳定点，使其与用户正在查看的全息图一致

**要避免的问题** 稳定面是实现稳定的全息影像的极佳工具，但如果误用它，可能会导致严重的映像不稳定。
* 别忘了。 最终，用户可以使用稳定平面，或将其附加到不再位于用户视图中的对象。 确保稳定平面正常设置为相对于照相机前进 (例如，-摄像) 
* 不要在两个极端之间来回更改稳定平面
* 不要将稳定平面设置为固定距离/方向
* 不要让稳定面贯穿用户
* 在台式计算机上运行时，请勿设置焦点，而不是使用基于像素的深度 reprojection。

## <a name="color-separation"></a>颜色分离 

由于 HoloLens 显示的性质，有时会出现名为 "颜色分离" 的项目。 它将以图像形式表现为单独的基本颜色（红色、绿色和蓝色）。 当显示白色对象时，项目尤其可见，因为它们有大量的红色、绿色和蓝色。 当用户以较快的速度在全息帧上移动时，最明显的是用户。 项目的另一种方式是对象的扭曲/变形。 如果对象具有高对比度和/或纯色，如红色、绿色、蓝色，则会将颜色分隔视为对象的不同部分的弯曲。

**打印头锁定空心轮光标的颜色分离的示例可能类似于用户将其头旋转到侧面：**

![打印头锁定空心轮光标的颜色分离的示例可能类似于用户将其头旋转到一边。](images/colorseparationofroundwhitecursor-300px.png)

尽管很难完全避免颜色分离，但有几种方法可用于缓解这种情况。

**可以在以下项上查看颜色分隔：**
* 正在快速移动的对象，包括 head 锁定对象，如 [光标](../../design/cursors.md)。
* 远离 [稳定平面](hologram-stability.md#reprojection)的对象。

**衰减颜色分离的效果：**
* 使对象滞后用户。 它应显示为具有某种惯性，并附加到注视 "on 弹簧"。 此方法降低了光标 (降低分离距离) 并将其放在用户可能的注视点后面。 只要用户停止改变其看起来就会很自然。
* 如果你确实想要移动一张全息图，如果你希望用户跟随其眼睛，请尝试将其移动速度保持在5度/秒以下。
* 使用 *光* 而不是 *几何图形* 作为光标。 附加到注视的虚拟照明源会被视为交互式指针，但不会导致颜色分离。
* 调整 "稳定" 平面，使其与用户正在 gazing 的全息影像匹配。
* 使对象变为红色、绿色或蓝色。
* 切换到内容的模糊版本。 例如，可以将一个圆形白色光标更改为在运动方向上稍微模糊的线条。

与之前一样，在 60 FPS 和设置 "稳定" 平面的情况下，最重要的技术是全息图稳定性。 如果有明显的颜色分离，请首先确保帧速率符合预期。

## <a name="see-also"></a>另请参阅
* [了解混合现实的性能](understanding-performance-for-mixed-reality.md)
* [颜色、光线和材料](../../design/color-light-and-materials.md)
* [本能交互](../../design/interaction-fundamentals.md)
* [MRTK 全息影像稳定性](/windows/mixed-reality/mrtk-unity/performance/hologram-stabilization)