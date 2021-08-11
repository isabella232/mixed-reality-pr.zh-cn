---
title: 眼动跟踪导航
description: 如何在 MRTK 中将眼睛定位用于导航
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， EyeTracking，
ms.openlocfilehash: e1ca34054a019e26bebf14282cd351467e5c65e2c2c3fa4f35647dd5aba680ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197102"
---
# <a name="eye-supported-navigation-in-mrtk"></a>MRTK 中支持眼睛的导航

![MRTK](../../images/eye-tracking/mrtk_et_navigation.png)

Imagine在平板电脑上阅读信息，并且到达显示文本的末尾时，文本会自动向上滚动以显示更多内容。 或者，可以流畅地放大正在查看的内容。 地图还会自动调整内容，以将感兴趣的内容保留在你的视场中。 另一个有趣的应用程序是自动将你正在查看的全息影像部分引入到前面，以免手观察 3D 全息影像。 以下是此页上在支持眼睛的导航上下文中介绍的一些示例。

以下说明假定你已熟悉如何在[MRTK](eye-tracking-basic-setup.md)场景中设置眼动跟踪，并熟悉在 MRTK Unity[](eye-tracking-target-selection.md)中访问眼动跟踪数据的基础知识。
下面讨论的示例都是 (`EyeTrackingDemo-03-Navigation` Assets/MRTK/Examples/Demos/EyeTracking/Scene/EyeTrackingDemo-03-Navigation) 场景的一部分。

**摘要：** 自动滚动文本、支持眼睛凝视的平移和缩放虚拟地图、无手凝视定向 3D 旋转。

## <a name="auto-scroll"></a>自动滚动

自动滚动使用户能够在文本中滚动，而无需提升手指。
只需继续阅读，文本就会根据用户正在查找的内容自动向上或向下滚动。
可以从资产 `EyeTrackingDemo-03-Navigation` /MRTK/Examples/Demos/EyeTracking/Scenes (中提供的示例) 。
此示例使用 [TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) 组件，以便灵活地加载新文本并设置其格式。
若要启用自动滚动，只需将以下两个脚本添加到文本框的碰撞体组件：

### <a name="scrollrecttransf"></a>ScrollRectTransf

若要滚动 [TextMesh 或](https://docs.unity3d.com/ScriptReference/TextMesh.html) 更一般而言的 [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) 组件，可以使用 [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) 脚本。
如果要滚动纹理而不是 [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html)，请使用 [ScrollTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollTexture) 而不是 [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf)。
下面更详细地介绍了 Unity 编辑器中提供的 [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) 参数：

参数 | 说明
:---- | :----
LimitPanning | 如果启用， 将在其边界停止可滚动内容。
RectTransfToNavigate | 引用要[滚动到的 RectTransform。](https://docs.unity3d.com/ScriptReference/RectTransform.html)
RefToViewport | 对可滚动内容的 [父 RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) 的引用，以确定正确的偏移量和边界。
AutoGazeScrollIsActive | 如果启用，则如果用户查看活动区域（例如 (滚动面板的顶部和底部，则文本将自动滚动（如果垂直滚动速度不为零) ）。
ScrollSpeed_x | 如果设置为不等于零的值，将启用水平滚动。 负值表示滚动方向发生变化：从左到右，从右到左。
ScrollSpeed_y | 如果设置为不等于零的值，将启用垂直滚动。 负值表示滚动方向的变化：从上到下到上。
MinDistFromCenterForAutoScroll | 以 x 和 y 表示的与目标命中框中心之间的最小距离规范化 (0，0) 滚动。 因此，值必须介于 0 之间 (始终滚动) 0.5 (滚动) 。
UseS并Proofing | 如果启用，它可以防止在快速四处查找时突然滚动移动。 不过，这可能会导致滚动速度降低。 它可以使用 *S并ProofUpdateSpeed 值进行优化* 。
S并ProofUpdateSpeed | 值越低，滚动速度在轻扫后的速度就越低。 建议的值：5。

![Unity 中支持眼睛的滚动设置](../../images/eye-tracking/mrtk_et_nav_scroll.jpg)

### <a name="eyetrackingtarget"></a>EyeTrackingTarget

附加 _EyeTrackingTarget_ 组件可灵活处理与眼睛凝视相关的事件。
滚动示例演示滚动文本，该文本在用户查看面板时开始，当用户离开面板时停止。 
![Unity 中支持眼睛的滚动设置：EyeTrackingTarget](../../images/eye-tracking/mrtk_et_nav_scroll_ettarget.jpg)

## <a name="gaze-supported-pan-and-zoom"></a>支持凝视的平移和缩放

Who之前从未使用过虚拟地图来搜索其主页或探索全新的位置？ 眼动跟踪可让你直接深入了解你感兴趣的部分，放大后，可以顺利遵循街道过程来探索邻域！
这不仅可用于浏览地理地图，还可用于查看照片、数据可视化效果甚至实时流式医疗图像中的详细信息。 在应用中使用此功能非常简单！ 对于呈现到 [纹理]( https://docs.unity3d.com/ScriptReference/Texture.html) (例如照片、流式处理的数据) ，只需添加 [PanZoomTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomTexture) 脚本。
对于 [RectTransform，](https://docs.unity3d.com/ScriptReference/RectTransform.html) 请使用 [PanZoomRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomRectTransf)。 扩展 [自动滚动](#auto-scroll) 功能后，我们实质上能够同时垂直和水平滚动，并放大用户当前焦点周围的内容。

参数 | 说明
:---- | :----
LimitPanning | 如果启用， 将在其边界停止可滚动内容。
HandZoomEnabledOnStartup | 指示是否自动启用手势来执行缩放手势。 你可能希望首先禁用它，以避免意外触发缩放操作。
RendererOfTextureToBeNavigated | 要导航的纹理的引用呈现器。
Zoom_Acceleration | 缩放加速定义逻辑速度函数映射的倾斜度。
Zoom_SpeedMax | 最大缩放速度。
Zoom_MinScale | 用于放大的最小纹理比例 - 例如，0.5f (原始大小的一) 。
Zoom_MaxScale | 缩小纹理的最大比例 - 例如，1f (原始大小) 或 2.0f (原始大小) 。
Zoom_TimeInSecToZoom | 时间缩放：触发后，将在给定的时间（以秒数）内执行放大/缩小。
Zoom_Gesture | 用于放大/缩小的手势类型。
--- | ---
Pan_AutoScrollIsActive | 如果启用，则如果用户查看活动区域（例如 (滚动面板的顶部和底部，则文本将自动滚动（如果垂直滚动速度不为零) ）。
Pan_Speed_x | 如果设置为不等于零的值，将启用水平滚动。 负值表示滚动方向发生变化：从左到右，从右到左。
Pan_Speed_y | 如果设置为不等于零的值，将启用垂直滚动。 负值表示滚动方向的变化：从上到下到上。
Pan_MinDistFromCenter | 以 x 和 y 表示的与目标命中框中心之间的最小距离规范化 (0，0) 滚动。 因此，值必须介于 0 之间 (始终滚动) 0.5 (滚动) 。
UseS并Proofing | 如果启用，它可以防止在快速四处查找时突然滚动移动。 不过，这可能会导致滚动速度降低。 它可以使用 *S并ProofUpdateSpeed 值进行优化* 。
S并ProofUpdateSpeed | 值越低，滚动速度在轻扫后的速度就越低。 建议的值：5。

![Unity 中支持眼睛的平移和缩放设置](../../images/eye-tracking/mrtk_et_nav_panzoom.jpg)

## <a name="attention-based-3d-rotation"></a>基于注意的 3D 旋转

Imagine一个 3D 对象，以及想要更密切地看到的各个部分，就如系统会读读你的想法，并知道将项打开给你！
这是基于注意力的 3D 旋转理念，使你可以调查全息影像的所有端，而无需举手。
若要启用此行为，只需使用碰撞体组件将 [OnLookAtRotateByEyeGaze](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) 脚本添加到 GameObject [的](https://docs.unity3d.com/ScriptReference/Collider.html) 一部分。
可以调整下面列出的几个参数，以限制全息影像旋转的速度和方向。

如你想象的那样，让此行为在一直处于活动状态时，可能很快就会在人满为观的场景中变得相当分散注意力。
因此，你可能希望首先禁用此行为，然后使用语音命令快速启用它。
或者，我们在 `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) 中添加了一个示例，以使用 [TargetMoveToCamera，](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.TargetMoveToCamera)你可针对该目标选择一个焦点目标，并且它会在你前面流动 -只需说"*向我看"。*

进入近模式后，将自动启用自动旋转模式。
在这种情况下，你可以从四面观察它，只需向后看、四处移动，或者手一起抓取和旋转它。 当关闭目标 (时&说"发回") ，它将返回到其原始位置，并停止从远地响应。

参数 | 说明
:---- | :----
SpeedX | 水平旋转速度。
迅速 | 垂直旋转速度。
InverseX | 反转水平旋转方向。
反向 | 反转垂直旋转方向。
RotationThreshInDegrees | 如果"凝视目标"和"相机到目标"之间的角度小于此值，则不执行任何操作。 这是为了防止小型抖动旋转。。
MinRotX | 最小水平旋转角度。 这是为了限制不同方向的旋转。
MaxRotX | 最大水平旋转角度。 这是为了限制不同方向的旋转。
MinRoty | 最小垂直旋转角度，以限制围绕 x 轴的旋转。
MaxRoty | 最大垂直旋转角度，限制围绕 y 轴的旋转。

![Unity 中支持眼睛的 3D 旋转设置](../../images/eye-tracking/mrtk_et_nav_rotate.jpg)

总之，上述脚本应使你可以开始对各种输入导航任务（例如滚动文本、缩放和平移纹理以及旋转调查 3D 全息影像）使用眼睛凝视。

### <a name="see-also"></a>另请参阅

- [使用眼动跟踪的基本 MRTK 设置](eye-tracking-basic-setup.md)
- [眼睛支持的目标选择](eye-tracking-target-selection.md)

---
[返回到"MixedRealityToolkit 中的眼动跟踪"](eye-tracking-main.md)
