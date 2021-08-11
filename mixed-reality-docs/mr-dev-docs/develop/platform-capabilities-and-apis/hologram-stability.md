---
title: 全息影像稳定性
description: HoloLens 自动使全息影像稳定，但开发人员可以进一步改善全息影像稳定性。
author: thetuvix
ms.author: alexturn
ms.date: 07/08/2020
ms.topic: article
keywords: 全息影像，稳定性，hololens，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，帧速率，渲染，reprojection，颜色分离
appliesto:
- HoloLens
ms.openlocfilehash: a9a260208764db86d3a2d945cb6a1a611e66848889dfc228d9341f10b8e054ef
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198806"
---
# <a name="hologram-stability"></a>全息影像稳定性

若要实现稳定的全息影像，HoloLens 具有内置的图像稳定性管道。 稳定管道在后台自动运行，因此不需要执行任何额外的步骤来启用它。 但是，您应运用改善全息影像稳定性的技术，避免降低稳定性的方案。

## <a name="hologram-quality-terminology"></a>全息影像质量术语

全息影像的质量是良好的环境和良好的应用程序开发。 在 HoloLens 可以跟踪周围的环境中，每秒在常量60帧上运行的应用可确保全息影像和匹配坐标系处于同步状态。从用户的角度来看，要保持静止的全息影像不会相对于环境移动。

以下术语可帮助你确定环境问题、不一致的呈现速率或任何其他内容。
* **准确性.** 在全局锁定全息图并将其放置在现实世界中后，它应保留相对于周围环境的位置，并独立于用户运动或小型和稀疏环境更改。 如果在意外的位置出现全息图，则这是一个 *准确性* 问题。 如果两个不同的房间看起来相同，则可能会发生这种情况。
* **抖动.** 用户将抖动视为全息图的高频握手，这在跟踪环境时可能会发生这种情况。 对于用户，解决方案正在运行 [传感器调整](/hololens/hololens-updates)。
* **Judder.** 低渲染频率会导致动画的不均匀运动和双图像。 Judder 在动态影像中尤其明显。 开发人员需要维护 [常量 60 FPS](hologram-stability.md#frame-rate)。
* **光标.** 用户在出现全息图后会看到偏移，使其远离其最初放置位置。 当你从 [空间锚](../../design/spatial-anchors.md)，而不是在环境的未映射部分中时，会发生偏移。 创建与空间锚接近的全息影像会降低偏移的可能性。
* **Jumpiness.** 如果不是，则不会偶尔从其位置 "弹出" 或 "跳转"。 当跟踪调整全息影像以匹配更新的环境时，会发生 Jumpiness。
* **泳道.** 当 sway 与用户的头运动相对应时，会出现一个全息图。 当应用程序未完全实现[reprojection](hologram-stability.md#reprojection)，并且没有为当前用户[校准](/hololens/hololens-calibration)HoloLens 时，会发生泳道。 用户可以重新运行 [校准](/hololens/hololens-calibration) 应用程序以解决此问题。 开发人员可以更新稳定平面，以进一步增强稳定性。
* **颜色分离。** HoloLens 中显示的是颜色顺序显示，它以 60 hz 为 hz (各个颜色字段以 hz 的颜色通道显示在 240 hz) 。 无论用户何时使用其眼睛跟踪移动的全息图，都将在其构成颜色中分离出全息图的前导和尾随边缘，从而产生彩虹效果。 分离程度取决于全息图的速度。 在某些罕见情况下，在查看固定全息图的同时迅速移动打印头也会导致彩虹效果，这称为 *[颜色分离](hologram-stability.md#color-separation)*。

## <a name="frame-rate"></a>帧速率

帧速率是全息图稳定性的第一个支柱。 要使全息影像在世界中显得稳定，提供给用户的每个图像都必须在正确的位置中绘制出全息影像。 显示 HoloLens 每秒刷新240次，为每个新呈现的图像显示四个单独的颜色字段，从而导致用户体验 60 FPS (帧/秒) 。 若要提供最佳体验，应用程序开发人员必须维护 60 FPS，这将转换为每16毫秒向操作系统持续提供一次新映像。

**60 FPS** 若要绘出全息影像，使其看起来像是真实世界，HoloLens 需要从用户的位置呈现图像。 由于图像渲染需要时间，HoloLens 预测在显示器中显示图像的位置。 但是，此预测算法是近似值。 HoloLens 有一些硬件，用于调整呈现的图像，以考虑预测的头位置与实际头位置之间的差异。 调整会使用户看到的图像看起来就像是从正确位置呈现的一样，而全息影像却是稳定的。 映像更新最适合进行少量更改，它无法完全修复呈现的图像（如视差）中的某些项。

通过在 60 FPS 的情况下呈现，你将执行以下三项操作来帮助实现稳定的全息影像：
1. 最大程度地降低渲染图像和用户查看图像之间的总体延迟。 在具有游戏的引擎和在一脉相承中运行的渲染线程中，在30FPS 上运行可能会增加 33.3 ms 的额外延迟。 减少延迟可减少预测错误并增加全息影像稳定性。
2. 这样，每个图像都能达到用户的眼睛，并具有一致的延迟时间。 如果以 30 fps 的速度呈现，则显示的图像仍为 60 FPS，这意味着相同的图像会在一行中显示两次。 第二个16.6 帧比第一帧的延迟时间更长，并将不得不更正更明显的错误量。 这种错误的不一致会导致不需要的 60 Hz judder。
3. 减轻视觉上的抖动，其特征是运动不均衡和重影。 全息影像运动速度越快且渲染速率越低，抖动就越明显。 努力始终维护 60 FPS，将有助于避免给定移动全息图的 judder。

**帧速率一致性** 帧速率一致性与高帧/秒一样重要。 对于任何内容丰富的应用程序，偶尔删除的帧都是不可避免的，HoloLens 实现一些复杂的算法来从偶然的故障中恢复。 但是，对于用户而言，持续波动的帧比以较低的帧速率持续运行要多得多。 例如，在这5帧的持续时间内，呈现为五帧 (60 FPS) 的应用程序，然后删除接下来的10帧的每个其他帧 (30 FPS，在这10帧的持续时间内，) 会显得比一致呈现的应用程序的不稳定。

在相关说明中，当 [混合现实捕获](/hololens/holographic-photos-and-videos) 正在运行时，操作系统将应用程序限制为 30 FPS。

**性能分析** 可以使用不同种类的工具来基准应用程序帧速率，例如：
* GPUView
* Visual Studio 图形调试器
* 内置于三维引擎（如 Unity）的探查器

## <a name="hologram-render-distances"></a>全息图呈现距离

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

当 fixates 和专注于某个对象时，该视觉对象系统会集成多个距离相关的信号。
* [便利设施](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) -单个眼睛的重点。
* [收敛](https://en.wikipedia.org/wiki/Convergence_(eye)) -两个眼睛向内或向外移动到对象的中心。
* [望远镜视觉](https://en.wikipedia.org/wiki/Stereopsis) 对象-在与固定点远离某个对象距离的左侧和右侧图像之间发达国家。
* 着色、相对角度大小和其他 monocular (单眼睛) 提示。

会合和便利的独特之处在于，它们的视网膜提示与眼睛如何变化以不同的距离感知对象相关。 在自然查看中，聚合和便利设施均已链接。 例如，当眼睛接近 (例如，鼻子) ，眼睛交叉并适应近点。 当眼睛查看无穷时，眼睛会成为平行的，眼睛可容纳无限大。 

戴 HoloLens 的用户将始终适应 2.0 m 以维护一个清晰的图像，因为 HoloLens 显示的固定距离离用户约2.0 米。 应用开发人员通过在不同的深度放置内容和全息影像来控制用户的眼睛汇聚。 当用户容纳并聚合到不同的距离时，两个提示之间的自然链接会断开，这可能会导致 visual discomfort 或疲劳，特别是当冲突量大时。 

Discomfort 可以通过将混合内容保持在最接近 2.0 m 的位置来避免或最大程度 (地降低 vergence，这就是在具有很多深度的场景中，尽可能多地将感2.0 兴趣的区域) 。 当内容不能放在 2.0 m 附近时，当用户在不同距离之间来回注视时，discomfort 会出现 vergence 冲突。 换言之，观看 50 厘米远的静态全息影像，比观看 50 厘米远的前后不断移动的全息影像要舒适得多。

将内容放置在 2.0 m 也是有益的，因为这两个显示器的设计目的是完全重叠。 对于放置在此平面之外的图像，当它们移出全息帧的一侧时，它们将显示在一个显示器上，同时仍然可见。 此望远镜 rivalry 可能会对全息图的深度认知造成中断。

**全息影像与用户之间的最佳距离**

![全息影像与用户之间的最佳距离](images/distanceguiderendering-750px.png)

**剪辑平面** 为了最大限度地获取舒适，我们建议在85厘米剪辑渲染距离，从 1 m 开始的内容淡化。 在全息影像和用户均为静止的应用程序中，可以轻松地查看全息影像，如50厘米。在这种情况下，应用程序应将不超过30厘米的剪辑平面置于离剪裁平面至少10厘米的位置。 只要内容比85厘米更近，就必须确保用户不会频繁地从全息影像中移近或远离用户，否则，在这些情况下，这种情况很可能会导致 discomfort 的 vergence 冲突。 内容的设计目的是为了最大程度地减少从用户交互到 85 cm 的需要，但当内容必须比85厘米更近时，适用于开发人员的很好的经验法则是设计这样的方案：用户和/或全息影像不会在超过25% 的时间内移动。

**最佳做法** 如果无法将全息影像置于 2 m 个位置，并且无法避免聚合和便利设施之间发生冲突，则全息图位置的最佳区域为 1.25 m 和 5 m。 在每种情况下，设计器都应该构建内容来鼓励用户与 (进行交互，例如调整内容大小和默认位置参数) 。

## <a name="reprojection"></a>Reprojection
HoloLens 提供了一种复杂的硬件辅助的全息稳定技术（称为 reprojection）。 Reprojection 在场景进行动画处理时，会考虑运动和变化的观点 (CameraPose) ，并使用户移动其头。  应用程序需要执行特定操作，以充分利用重新保护。


有四种主要类型的重新保护
* **深度重现：**  以最少的工作量从应用程序生成最佳结果。  渲染场景的所有部分都根据它们与用户的距离独立稳定。  某些呈现项目在深度有明显变化时可能可见。  此选项仅适用于沉浸式HoloLens 2头戴显示设备。
* **Planar Reprojection：**  允许应用程序精确控制稳定性。  平面由应用程序设置，该平面上的所有内容将是场景中最稳定的部分。  全息影像离平面较远，其稳定性就较低。  此选项在所有 MR 平台上Windows可用。
* **自动平面重新项目：**  系统使用深度缓冲区中的信息设置稳定平面。  此选项适用于第 1 代HoloLens第 1 代HoloLens 2。
* **无：** 如果应用程序不执行任何操作，则 Planar Reprojection 与固定在用户头部凝视方向 2 米处的稳定平面一起使用，通常生成不标准的结果。

应用程序需要执行特定操作才能启用不同类型的重新保护
* **深度重现：** 应用程序将每个呈现帧的深度缓冲区提交到系统。  在 Unity 上，使用"XR 插件管理"下"Windows Mixed Reality 设置"共享深度 **缓冲区**"选项 **完成深度重新保护**。  DirectX 应用调用 CommitDirect3D11DepthBuffer。  应用程序不应调用 SetFocusPoint。
* **Planar Reprojection：** 每个帧上，应用程序都会告知系统要稳定平面的位置。  Unity 应用程序调用 SetFocusPointForFrame，应禁用 **共享深度** 缓冲区。  DirectX 应用调用 SetFocusPoint，不应调用 CommitDirect3D11DepthBuffer。
* **自动平面重新项目：** 若要启用，应用程序需要像提交深度重新保护一样，将深度缓冲区提交到系统。 使用混合现实 Toolkit (MRTK) 可以将相机设置提供程序配置为使用 AutoPlanar 重新保护。 [](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings#hololens-2-reprojection-method) 本机应用应在 `DepthReprojectionMode` [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters) 中将 设置为 `AutoPlanar` 每个帧。 对于HoloLens第 1 代，应用程序不应调用 SetFocusPoint。

### <a name="choosing-reprojection-technique"></a>选择重新保护技术

稳定类型 |    沉浸式头戴显示设备 |    HoloLens第 1 代 | HoloLens 2
--- | --- | --- | ---
深度重现 |    建议 |   不适用 |   建议<br/><br/>Unity 应用程序必须使用 Unity 2018.4.12+、Unity 2019.3+ 或 Unity 2020.3+。 否则，请使用自动平面重新项目。
自动平面重新项目 | 不适用 |   建议的默认 |   如果深度重现未提供最佳结果，建议<br/><br/>建议使用 Unity 2018.4.12+、Unity 2019.3+ 或 Unity 2020.3+ 的 Unity 应用程序。  以前的 Unity 版本将处理略微降级的重新保护结果。
Planar Reprojection |   不建议使用 |   如果自动平面未提供最佳结果，建议 | 如果两个深度选项都未提供所需的结果，请使用    

### <a name="verifying-depth-is-set-correctly"></a>验证深度是否已正确设置
            
当重新保护方法使用深度缓冲区时，必须验证深度缓冲区的内容是否代表应用程序呈现的场景。  许多因素都可能导致问题。 例如，如果有第二个相机用于呈现用户界面覆盖，则可能会覆盖实际视图中的所有深度信息。  透明对象通常不设置深度。  默认情况下，某些文本呈现不会设置深度。  当深度与呈现的全息影像不匹配时，呈现中将存在明显的问题。
            
HoloLens 2可视化工具，用于显示深度是和未设置的深度，可以从设备门户。  在"**视图**  >  **全息影像稳定性"** 选项卡上，选中"**在头戴显示设备中显示深度可视化效果"** 复选框。  深度设置正确的区域将为蓝色。  未设置深度的呈现项标记为红色，需要修复。  

> [!NOTE]
> 深度的可视化效果不会显示在混合现实捕获。  它仅通过设备可见。
            
某些 GPU 查看工具将允许可视化深度缓冲区。  应用程序开发人员可以使用这些工具确保正确设置深度。  请参阅应用程序工具的文档。

### <a name="using-planar-reprojection"></a>使用 Planar Reprojection
> [!NOTE]
> 对于桌面沉浸式头戴显示设备，设置稳定平面通常具有反效率，因为它提供的视觉质量比向系统提供应用的深度缓冲区要低，以启用基于像素深度的重新项目。 除非在 HoloLens上运行，否则通常应避免设置稳定平面。

![3D 对象的稳定平面](images/stab-plane-500px.jpg)

设备将自动尝试选择此平面，但应用程序应该通过选择场景中的焦点来提供帮助。 在应用上运行的 Unity HoloLens应基于场景选择最佳焦点，并传递到[SetFocusPoint () 。 ](../unity/focus-point-in-unity.md) 默认旋转多维数据集模板中包含在 DirectX 中设置焦点的示例。

Unity 将深度缓冲区提交到 Windows，以在连接到桌面电脑的沉浸式头戴显示设备中运行应用时启用每像素重新保护，无需应用显式工作，即可提供更好的图像质量。 只有在应用在应用上运行时，才应提供HoloLens，否则将重写每个像素的重新保护。


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

焦点的位置主要取决于全息影像正在查看的内容。 应用具有用于引用的凝视向量，应用设计器知道他们希望用户观察的内容。

开发人员在稳定全息影像时可以执行的最主要操作是以 60 FPS 渲染。 无论稳定平面优化如何，低于 60 FPS 都会显著降低全息影像稳定性。

**最佳做法** 没有通用方法可以设置稳定平面，并且它是特定于应用的。 我们的主要建议是试验并查看最适合你的方案的情况。 但是，请尝试使稳定平面与尽可能多的内容对齐，因为此平面上的所有内容都完全稳定。

例如：
* 如果只有平面内容 (，则视频播放应用) ，请使稳定平面与包含内容的平面对齐。
* 如果有三个小球体被世界锁定，请通过当前用户视图中所有球体的中心将稳定平面"剪切"。
* 如果场景的内容深度明显不同，则倾向于使用更多对象。
* 请确保调整每个帧的稳定点，使其与用户正在查看的全息影像保持一致

**要避免的一些操作** 稳定平面是实现稳定全息影像的一种很好的工具，但如果误用，可能会导致严重的图像不稳定。
* 请勿"发后不放"。 你最终可以使用用户后面的稳定平面或附加到不再位于用户视图中的对象。 确保将稳定平面法线设置为与相机 (相反，例如 -camera.forward) 
* 不要在极端之间来回快速更改稳定平面
* 不要将稳定平面设置为固定距离/方向
* 不要让稳定平面通过用户
* 在台式电脑（而不是计算机）上运行时，不要设置HoloLens，而是依赖于基于像素深度的重新保护。

## <a name="color-separation"></a>颜色分离 

由于图像显示HoloLens，有时可以感知名为"颜色分离"的项目。 它表现为图像分离成单独的基本颜色 -红色、绿色和蓝色。 显示白色对象时，项目可能特别明显，因为它们具有大量的红色、绿色和蓝色。 当用户以可视方式跟踪正在高速跨全息帧移动的全息影像时，这一点最明显。 项目可以清单的另一种方式是对象的翻转/缩小。 如果对象具有高对比度和/或纯色（如红色、绿色、蓝色），则颜色分离被视为对象不同部分的翻转。

**用户将头部旋转到一侧时，锁定头部的白色圆形光标的颜色分离示例：**

![用户将头部旋转到一侧时，锁定头部的白色圆形光标的颜色分离示例。](images/colorseparationofroundwhitecursor-300px.png)

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