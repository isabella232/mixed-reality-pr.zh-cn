---
title: 眼动跟踪导航
description: 如何在 MRTK 中使用目视定位定位导航
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，EyeTracking，
ms.openlocfilehash: d966bbe1d3a256e55c62532e8101c1f2846e1136
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145271"
---
# <a name="eye-supported-navigation-in-mrtk"></a>MRTK 中支持的目视导航

![MRTK](../../images/eye-tracking/mrtk_et_navigation.png)

假设你要在平板上阅读信息，当你到达显示的文本的末尾时，文本会自动向上滚动以显示更多内容。 或者，你可以在查看的位置流畅地缩放。 此地图还会自动调整内容，以在视图字段中保留感兴趣的内容。 另一个有趣的应用程序是通过自动将您正在查看的全息图部分自动引入到前面，可以无需人工地观察3D 全息。 下面是在支持目视导航的上下文中在此页上描述的一些示例。

以下说明假定你已熟悉如何 [在 MRTK 场景中设置目视跟踪](eye-tracking-basic-setup.md) ，以及在 MRTK Unity 中 [访问眼睛跟踪数据](eye-tracking-target-selection.md) 的基础知识。
下面讨论的示例包括 `EyeTrackingDemo-03-Navigation` (资产/MRTK/示例/演示程序/EyeTracking/场景/EyeTrackingDemo-03) -03-03-03-

**摘要：** 自动滚动文本、目视浏览支持的虚拟地图的平移和缩放、无人参与的直接定向3D 旋转。

## <a name="auto-scroll"></a>自动滚动

自动滚动使得用户无需抬起手指即可滚动查看文本。
只需继续阅读，文本就会自动向上或向下滚动，具体取决于用户的查找位置。
可以从 `EyeTrackingDemo-03-Navigation` (资产/MRTK/示例/演示/EyeTracking/场景) 中提供的示例开始。
此示例使用 [TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) 组件，以灵活地加载新文本并设置其格式。
若要启用自动滚动，只需将以下两个脚本添加到文本框的碰撞器组件：

### <a name="scrollrecttransf"></a>ScrollRectTransf

若要在 [TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) 或更常见的 [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) 组件中滚动浏览，你可以使用 [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) 脚本。
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
UseS并Proofing | 如果启用此功能，则可防止在快速查找时突然滚动移动。 但这可能会使滚动感觉不太响应。 它可以用 *SkimProofUpdateSpeed* 值进行优化。
SkimProofUpdateSpeed | 该值越低，滚动速度越慢，滚动支撑后的速度就越快。 建议值：5。

![Unity 中支持的目视滚动设置](../../images/eye-tracking/mrtk_et_nav_scroll.jpg)

### <a name="eyetrackingtarget"></a>EyeTrackingTarget

附加 _EyeTrackingTarget_ 组件可灵活地处理目视相关的事件。
滚动示例说明滚动文本，该文本 *在用户查看* 面板时开始，并在用户 *离开* 时停止。
![Unity 中支持的目视滚动设置： EyeTrackingTarget](../../images/eye-tracking/mrtk_et_nav_scroll_ettarget.jpg)

## <a name="gaze-supported-pan-and-zoom"></a>注视支持的平移和缩放

谁在搜索其家里或浏览全新位置之前尚未使用过虚拟映射？ 通过目视跟踪，你可以直接深入了解你感兴趣的部分，一旦放大，你就可以平稳地按照街道的过程来浏览你的邻居！
这不仅适用于浏览地理地图，还用于查看照片、数据可视化甚至实时传输的医疗图像中的详细信息。 在应用程序中使用此功能非常简单！ 对于呈现给 [纹理]( https://docs.unity3d.com/ScriptReference/Texture.html) 的内容 (例如，) 的照片流数据，只需添加 [PanZoomTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomTexture) 脚本。
对于 [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) ，请使用 [PanZoomRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomRectTransf)。 通过扩展 [自动滚动](#auto-scroll) 功能，我们实质上是启用同时垂直和水平滚动并放大用户的当前焦点。

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
Pan_Speed_x | 如果设置为与零不相等的值，则将启用水平滚动。 负值表示滚动方向的变化：从左到右与从右到左。
Pan_Speed_y | 如果设置为与零不相等的值，则将启用垂直滚动。 负值表示滚动方向发生变化：向上、向下和向下移动。
Pan_MinDistFromCenter | 从目标的命中框中心开始，x 和 y 中的最小距离， (0，0) 滚动。 因此，值必须介于 0 (始终滚动) ，0.5 (没有滚动) 。
UseSkimProofing | 如果启用此功能，则可防止在快速查找时突然滚动移动。 但这可能会使滚动感觉不太响应。 它可以用 *SkimProofUpdateSpeed* 值进行优化。
SkimProofUpdateSpeed | 该值越低，滚动速度越慢，滚动支撑后的速度就越快。 建议值：5。

![Unity 支持的目视平移和缩放设置](../../images/eye-tracking/mrtk_et_nav_panzoom.jpg)

## <a name="attention-based-3d-rotation"></a>基于关注的3D 旋转

想象一下，查看三维对象和您想要看到的内容更加神奇，就好像系统会阅读您的想法，并知道您会将物品转向您！
这是一种基于关注的3D 旋转的理念，使您能够调查出全息影像的所有面，而不会抬起手指。
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
MinRotY | 最小垂直旋转角度，用于限制围绕 x 轴的旋转。
MaxRotY | 用于限制绕 y 轴旋转的最大垂直旋转角度。

![Unity 中支持的目视3D 旋转设置](../../images/eye-tracking/mrtk_et_nav_rotate.jpg)

总而言之，以上脚本使你可以开始使用目视查看各种输入导航任务，例如滚动文本、缩放和平移纹理以及旋转3D 全息影像。

### <a name="see-also"></a>另请参阅

- [基本 MRTK 安装程序使用目视跟踪](eye-tracking-basic-setup.md)
- [目视支持的目标选择](eye-tracking-target-selection.md)

---
[返回 "MixedRealityToolkit" 中的眼睛跟踪](eye-tracking-main.md)
