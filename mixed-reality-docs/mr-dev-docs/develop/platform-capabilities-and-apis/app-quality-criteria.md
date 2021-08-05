---
title: 应用质量标准
description: 本文档介绍影响混合现实应用质量的主要因素。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 应用质量标准，混合现实，混合现实应用，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 858b0782c4e6754ee6753d463d5fe498e3a893f6c21b3f1c86ac14f8c0e6c8cf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189377"
---
# <a name="app-quality-criteria"></a>应用质量标准

本文档介绍影响混合现实应用质量的主要因素。 对于每个因素，提供以下信息
* 概述-质量因素及其重要原因的简短说明。
* 设备影响-影响哪种类型的窗口混合现实设备。
* 质量标准–如何评估质量因素。
* 如何衡量方法，以衡量问题 (或经验) 。
* 推荐–提供更好的用户体验的方法摘要。
* 资源-相关的开发人员和设计资源有助于创建更好的应用程序体验。

## <a name="frame-rate"></a>帧速率

帧速率是全息图稳定性和用户舒适的第一个支柱。 低于建议目标的帧速率可能导致全息影像出现抖动，对体验的 believability 产生负面影响，并可能导致目视疲劳。 Windows Mixed Reality 沉浸式耳机上的体验的目标帧速率为 60 hz 或 90 hz，具体取决于你支持的 Windows Mixed Reality 兼容 pc。 对于 HoloLens，目标帧速率为 60 Hz。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  最佳  |  适合 |  失败 |
--- | --- | ---
| 应用一致地满足了目标设备的每秒帧数 (FPS) 目标，HoloLens 为 60 fps;超计算机上的 90 fps;和 60 fps。 | 应用程序有间歇性的帧不会阻碍核心体验，或者 FPS 的速度一直低于所需的目标，但不会妨碍应用程序的体验。 | 应用在每10秒或更短时间内每隔10秒或更短时间内遇到一次帧速率下降。 |

### <a name="how-to-measure"></a>如何度量

* 在 "系统性能" 下，通过[Windows 设备门户](using-the-windows-device-portal.md#system-performance)提供实时的帧速率图。
* 对于开发调试，请将帧速率诊断计数器添加到应用中。 查看示例计数器的资源。
* 当应用程序运行时，可以在设备中体验到帧速率下降。 如果全息图显示意外的抖动运动，则帧速率较低或稳定性平面可能是原因。

### <a name="recommendations"></a>建议

* 在开发工作开始时添加帧速率计数器。
* 应评估出现帧速率下降的更改，并适当地将其解析为性能 bug。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [了解混合现实的性能](understanding-performance-for-mixed-reality.md)
* [全息图稳定性和帧速率](hologram-stability.md#frame-rate)
* [资产性能预算](../../design/asset-creation-process.md)
* [针对 Unity 的性能建议](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [混合现实 Toolkit，FPS 计数器显示](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [混合现实 Toolkit，着色器](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>外部引用

* [Unity，优化移动应用程序](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>全息影像稳定性

稳定的全息影像会提高应用程序的可用性和 believability，并为用户创建更舒适的查看体验。 全息图稳定性的质量是良好的应用开发和设备了解 (磁道) 其环境的能力。 尽管帧速率是稳定性的第一支柱，但其他因素可能会影响稳定性，其中包括：

* 使用 "稳定" 平面
* 与空间锚的距离
* 跟踪

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  最佳  |  适合 |  失败 |
--- | --- | ---
|  全息影像一致地显示稳定。 | 辅助内容显示意外移动;或意外移动不会妨碍总体应用程序体验。 | 帧中的主要内容显示意外移动。 |

### <a name="how-to-measure"></a>如何度量

戴设备并观看体验：

* 从一侧到另一侧移动您的头。 如果全息影像显示意外移动，而稳定平面与焦距平面之间的不正确对齐，则可能的原因。
* 四处移动影像和环境，查找泳道和 jumpiness 等行为。 此类动作可能由设备不跟踪环境或到空间锚点的距离引起。
* 如果帧中有大的或多个全息影像，请在不同的深度观察全息影像行为，同时从一侧到另一侧，如果出现抖动，这可能是由稳定平面导致的。

### <a name="recommendations"></a>建议

* 在开发工作开始时添加帧速率计数器。
* 使用 "稳定" 平面。
* 始终在其定位点的3米以内呈现定位的全息影像。
* 请确保您的环境已设置正确跟踪。
* 设计你的体验，以避免帧内处于不同焦点级别的全息影像。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [全息图稳定性和帧速率](hologram-stability.md#frame-rate)
* [使用 "稳定" 平面进行案例研究](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [了解混合现实的性能](understanding-performance-for-mixed-reality.md)
* [针对 Unity 的性能建议](../unity/performance-recommendations-for-unity.md)
* [空间定位点](../../design/spatial-anchors.md)
* [处理跟踪错误](../../design/coordinate-systems.md#handling-tracking-errors)
* [固定的引用框架](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>工具和教程

* [MR 配套包，Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>实面上的全息影像位置

使用物理 (对象的 Misalignments 的，如果要将其与另一个相对应) ，则可以清楚地指示全息影像和真实世界的非联合。 位置的准确性应与方案的需求相关;例如，常规表面布局可以使用空间图，但更准确的放置需要使用标记和校准。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  最佳  |  会见 |  失败 |
--- | --- | ---
| 全息影像通常以厘米到英寸范围与表面对齐。 如果需要更高的准确性，应用应提供在应用规范内进行协作的高效方法。 | NA | 全息影像通过破坏表面平面或似乎浮出表面来与物理目标对象无对齐。 如果需要准确性，全息影像应符合方案的邻近性规范。 | 

### <a name="how-to-measure"></a>如何度量

* 全息影像放置在空间地图上的图面不应明显浮点在图面上方或下方。
* 全息影像位置正确的设备应具有某种形式的标记和校准系统，这些标记和校准系统应符合方案要求。

### <a name="recommendations"></a>建议

* 当不需要精度时，空间地图可用于将对象放置在图面上。
* 为获得最佳精度，请使用标记或海报来设置全息影像和 Xbox 控制器 (或某些手动对齐机制) 最终校准。
* 请考虑将超大型全息影像分解为逻辑部分，并对齐每个部分到图面。
* IPD 图像中未正确设置 (距离) 也会影响全息影像对齐。 始终HoloLens用户的 IPD。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [空间映射位置](../../design/spatial-mapping.md#placement)
* [房间扫描过程](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [空间定位点最佳做法](../../design/spatial-anchors.md#best-practices)
* [处理跟踪错误](../../design/coordinate-systems.md#handling-tracking-errors)
* [Unity 中的空间映射](../unity/spatial-mapping-in-unity.md)
* [Vuforia 开发概述](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [MR Toolkit，空间映射库](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [MR 助理工具包，海报校准示例](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [MR 助理工具包，Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>外部引用

* [低值案例研究，精度对齐](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>查看舒适区域

应用开发人员通过将内容和全息影像放置在各种深度来控制用户眼睛的聚合位置。 使用 HoloLens 的用户将始终适应 2.0 米以保持清晰的图像，因为 HoloLens 显示器固定在距离用户约 2.0 米的光学距离上。 内容深度不当可能会导致视觉障碍或感同感。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

<table>
<tr>
<td> 最佳 </td><td><ul>
<li>将内容放在 2 米处。</li><li>如果全息影像不能放置在 2 米，并且无法避免收敛和收敛之间的冲突，则全息影像放置的最佳区域介于 1.25 米到 5 米之间。</li><li>在每种情况下，设计者都应构建内容，以鼓励用户在 1 米 (交互，例如调整内容大小和默认放置) 。</li><li>除非方案不需要，否则应实现剪辑平面，从 1 米开始淡出。</li><li>如果需要更密切地观察无运动全息影像，则内容不应接近 50 cm。</li>
</ul></td>
</tr><tr>
<td> 会见</td><td> 内容位于查看和运动指南中，但不当使用或不使用剪辑平面。</td>
</tr><tr>
<td> 失败 </td><td> 对于需要更密切观察 (固定全息影像，内容显示得过于 (通常为 &lt; 1.25 米 &lt; 或 50 cm。) </td>
</tr>
</table>

### <a name="how-to-measure"></a>如何度量

* 内容通常应距离 2 米，但不超过 1.25 或不超过 5 米。
* 除了少数例外情况，HoloLens剪辑呈现距离应设置为 85CM，从 1 米开始淡出内容。 接近内容并记下剪辑平面效果。
* 固定内容不应接近 50 cm。

### <a name="recommendations"></a>建议

* 设计内容以实现 2 米的最佳观看距离。
* 将剪辑呈现距离设置为 85 cm，从 1 米开始淡出内容。
* 对于需要更仔细查看的固定全息影像，剪辑平面应不超过 30 cm，淡出应从剪辑平面开始至少 10 cm。

### <a name="resources"></a>资源

* [呈现距离](hologram-stability.md#hologram-render-distances)
* [Unity 中的焦点](../unity/focus-point-in-unity.md)
* [试验缩放](../../design/scale.md#experimenting-with-scale)
* [文本，建议的字体大小](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a>深度切换

无论查看舒适问题的区域如何，用户对在近距和远距焦点对象（包括全息影像和真实内容 () ）之间频繁或快速切换的需求都可能导致视光障碍和一般症状。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  最佳  |  会见 |  失败 |
--- | --- | ---
|  有限或自然的深度切换，不会导致用户非自然地重新聚焦。 | "突然的深度切换"是核心，旨在融入应用体验，或由意外的真实内容引起的突然深度切换。 | 应用体验不需要或核心的一致深度切换或突然的深度切换。 | 

### <a name="how-to-measure"></a>如何度量

* 如果应用要求用户持续和/或突然更改深度焦点，则存在深度切换问题。

### <a name="recommendations"></a>建议

* 将主要内容保持在一致的焦点平面，并确保稳定平面与焦点平面匹配。 这将减轻微积分器疾病和意外全息影像移动。

### <a name="resources"></a>资源

* [呈现距离](hologram-stability.md#hologram-render-distances)
* [Unity 中的焦点](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>空间声音的使用

在Windows Mixed Reality中，音频引擎通过使用方向、距离和环境模拟来模拟 3D 声音，提供混合现实体验的音频组件。 在应用程序中使用空间声音可让开发人员将声音合理放置于三维空间中， () 用户周围的球体。 然后，这些声音看起来就像来自真实物理对象或用户周围的混合现实全息影像一样。 空间音效是一款功能强大的工具，适用于混合现实应用程序中的沉浸式、辅助功能和 UX 设计。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  最佳  |  会见 |  失败 |
--- | --- | ---
|  声音在逻辑上是空间化的，UX 会适当地使用声音来帮助发现对象和用户反馈。 声音自然且与对象相关，并在整个方案中规范化。 | 空间音频用于适当实现可读性，但缺少作为帮助用户反馈和可发现性的方式。 | 声音未根据预期进行空间化，并且/或缺少声音来帮助 UX 中的用户。 或者，在设计方案时，不会考虑或使用空间音频。 | 

### <a name="how-to-measure"></a>如何度量

* 一般情况下，相关声音应从目标全息影像发出 (例如来自全息狗.) 
* 在整个 UX 中，应该使用声音提示来帮助用户反馈或感知全息帧外的操作。

### <a name="recommendations"></a>建议

* 使用空间音频协助对象发现和用户界面。
* 真实声音比合成或不自然声音效果更好。
* 大多数声音都应进行空间化。
* 避免不可见的眼部。
* 避免空间掩码。
* 规范化所有声音。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [空间音效](../../design/spatial-sound.md)
* [空间音效设计](../../design/spatial-sound-design.md)
* [Unity 中的空间音效](../unity/spatial-sound-in-unity.md)
* [HoloTour 的空间音效案例研究](../../design/case-study-spatial-sound-design-for-holotour.md)
* [案例研究：在 RoboRaid 中使用空间声音](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [混合现实Toolkit - 空间音频](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>专注于 FOV 边界 (帧) 帧

设计良好的用户体验可以创建和维护围绕用户扩展的虚拟环境的有用上下文。 缓解 FOV 边界的影响涉及精心设计内容规模和上下文、使用空间音频、指导系统和用户位置。 如果操作正确，用户在拥有舒适应用体验的同时，将不太受 FOV 边界的阻碍。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  最佳  |  会见 |  失败 |
--- | --- | ---
|  用户永远不会失去上下文，并且查看很舒适。 为大型对象提供上下文协助。 为框架外部的对象提供了可发现性和查看指南。 一般情况下，全息影像的动作设计和缩放适合舒适观看体验。 | 用户永远不会失去上下文，但在有限的情况下可能需要额外的头部运动。 在有限的情况下，缩放会导致全息影像中断垂直或水平帧，从而导致某些头部运动查看全息影像。 | 用户可能需要失去上下文和/或一致的运动才能查看全息影像。 没有适用于大型全息对象的上下文指南、移动对象很容易在帧外丢失且没有可发现性指导，或者高全息影像需要定期的头部运动来查看。 | 

### <a name="how-to-measure"></a>如何度量

* 由于在边界 (，) 大型全息影像的上下文丢失或无法理解。
* 由于缺乏注意或内容快速移进和离开全息帧，因此很难找到全息影像的位置。
* 方案需要定期和重复的向上和向下头部运动，以完全看到导致眼睛感到感的全息影像。

### <a name="recommendations"></a>建议

* 使用适合 FOV 的小对象开始体验，然后使用视觉提示转换为更大的版本。
* 使用空间音频和注意控制器来帮助用户查找 FOV 外部的内容。
* 请尽可能避免垂直剪裁 FOV 的全息影像。
* 为用户提供应用内指南，以获得最佳查看位置。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [全息帧](../../design/holographic-frame.md)
* [案例研究、HoloStudio UI 和交互设计学习](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [对象和环境的规模](../../design/scale.md)
* [光标、视觉提示](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a>外部引用

* [有关 FOV 的很多工作](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>内容对用户位置做出反应

全息影像应该以与"实际"对象大致相同的方式响应用户位置。 一个值得注意的设计注意事项是 UI 元素，这些元素不一定假定用户的位置是固定的，并且适应用户的动作。 设计可正确适应用户位置的应用将创建一种更易于理解的体验，使其更易于使用。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

<table>
<tr>
<td> 最佳 </td><td> 内容和 UI 适应用户位置，允许用户与预期用户移动范围内的内容自然交互。</td>
</tr><tr>
<td> 会见 </td><td> UI 适应用户位置，但可能会妨碍关键内容视图，要求用户调整其位置。</td>
</tr><tr>
<td> 失败 </td><td><ol>
<li>UI 元素在移动过程中丢失或锁定，导致用户不自然地返回到 (或) 控件。</li><li>UI 元素限制主内容的视图。</li><li>UI 移动未针对查看距离和动量进行优化，尤其是使用 <a href="../../design/billboarding-and-tag-along.md">沿</a> 标记的 UI 元素。</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>如何度量

* 所有度量都应在方案的合理范围内完成。 尽管用户移动会有所不同，但不要尝试通过极端的用户移动来欺骗应用。
* 对于 UI 元素，无论用户移动如何，都应提供相关控件。 例如，如果用户正在查看并浏览带缩放效果的 3D 地图，则无论用户位于什么位置，缩放控件都应随时可供用户使用。

### <a name="recommendations"></a>建议

* 用户是照相机，他们控制移动。 让他们进行驱动。
* 考虑为文本和菜单系统设置广告，如果用户四处移动，这些系统将被世界锁定或遮盖。
* 对需要跟随用户的内容使用标记，同时仍允许用户查看其前面的内容。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [交互设计](../../discover/hologram.md)
* [颜色、光线和材料](../../design/color-light-and-materials.md)
* [公告和尾随](../../design/billboarding-and-tag-along.md)
* [本能交互](../../design/interaction-fundamentals.md)
* [自我运动和用户位移](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a>输入交互清晰度

输入交互清晰度对于应用的可用性至关重要，包括输入一致性、可接近性和交互方法的可发现性。 用户可以使用平台范围的常见交互，而无需重新学习。 如果应用具有自定义输入，应清楚地传达和演示它。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  最佳  |  会见 |  失败 |
--- | --- | ---
|  输入交互方法与提供的Windows Mixed Reality一[致](../../design/interaction-fundamentals.md)。 任何自定义输入不应是标准输入的冗余输入 (而是使用标准交互) 并且必须清楚地传达给用户并展示给用户。 | 与 best 类似，但自定义输入与标准输入方法是冗余的。 用户仍可在应用体验中实现目标和进度。 | 难以理解输入法或按钮映射。 输入是高度自定义的，不支持标准输入、无指令，或可能导致舒适和舒适问题。 | 

### <a name="how-to-measure"></a>如何度量

* 应用使用一致的 [标准输入方法。](../../design/interaction-fundamentals.md)
* 如果应用具有自定义输入，则可以通过以下方式清楚地传达：
* 首次运行体验
* 介绍性屏幕
* 工具提示
* 手部指导
* 帮助部分
* 语音朗读

### <a name="recommendations"></a>建议

* 尽可能使用标准输入方法。
* 提供非标准输入方法的演示、教程和工具提示。
* 在整个应用中使用一致的交互模型。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [本能交互](../../design/interaction-fundamentals.md)
* [可交互对象](../../design/interactable-object.md)
* [头部凝视和停留](../../design/gaze-and-dwell.md)
* [游标](../../design/cursors.md)
* [舒适和凝视](../../design/comfort.md#gaze-direction)
* [语音输入](../../design/voice-input.md)
* [运动控制器](../../design/motion-controllers.md)
* [Unity 的输入移植指南](../porting-apps/input-porting-guide-for-unity.md)
* [Unity 中的键盘输入](../unity/keyboard-input-in-unity.md)
* [Unity 中的凝视](../unity/gaze-in-unity.md)
* [Unity 中的运动控制器](../unity/motion-controllers-in-unity.md)
* [Unity 中的笔势](../unity/gestures-in-unity.md)
* [Unity 中的语音输入](../unity/voice-input-in-unity.md)
* [DirectX 中的键盘、鼠标和控制器输入](./keyboard-mouse-and-controller-input-in-directx.md)
* [DirectX 中的头部和眼部凝视](../native/gaze-in-directx.md)
* [DirectX 中的手和运动控制器](../native/hands-and-motion-controllers-in-directx.md)
* [DirectX 中的语音输入](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [案例研究：更多个人计算的优势](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [强制转换HoloStudio UI 和交互设计学习](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [示例应用：元素的周期表](../unity/periodic-table-of-the-elements.md)
* [示例应用：登月舱](../unity/lunar-module.md)

## <a name="interactable-objects"></a>可交互对象

按钮一直是在 2D 抽象世界触发事件的一种暗念。 在三维混合现实世界，我们不必再局限于这个抽象世界。 任何内容都可以是触发事件的可交互对象。 可交互对象可以表示为任何内容，从表上的咖啡杯到浮动在空气的气球。 无论窗体如何，用户可通过视觉和音频提示清楚地识别可交互对象。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  最佳  |  会见 |  失败 |
--- | --- | ---
|  无论窗体如何，均可通过视觉和音频提示识别可交互对象，这三种状态包括空闲、定向和选定。 在整个体验中，"查看它，说它"清晰且一致地使用。 缩放和分发对象，以允许无错误目标。 | 用户可以通过音频或视觉反馈将对象识别为可交互，并可以定位和激活该对象。 | 如果没有视觉或音频提示，用户无法识别可交互的对象。 由于对象规模或对象之间的距离，交互容易出错。 | 

### <a name="how-to-measure"></a>如何度量

* 可交互对象可识别为"可交互";包括按钮、菜单和特定于应用的内容。 根据经验法则，在以可交互对象为目标时，应存在视觉和音频提示。

### <a name="recommendations"></a>建议

* 使用视觉对象和音频反馈进行交互。
* 应针对每个输入状态区分视觉反馈， (空闲、定向、所选) 
* 应缩放和放置可交互对象，以便无错误定位。
* 分组的可交互对象 (如菜单栏或列表) 应具有适当的目标间距。
* 支持语音命令的按钮和菜单应为命令关键字提供文本标签 ("查看它，说) 

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [可交互对象](../../design/interactable-object.md)
* [Unity 中的文本](../unity/text-in-unity.md)
* [边界框和应用栏](../../design/app-bar-and-bounding-box.md)
* [语音输入](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [混合现实Toolkit - UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>房间扫描

需要空间映射数据的应用依赖于设备在用户浏览其环境且设备处于活动状态时，在一段时间和不同会话中自动收集此数据。 此数据的完整性和质量取决于许多因素，包括用户已完成的探索量、自探索以来经过的时间，以及设备扫描该区域后是否移动了设备和门等对象。 许多应用将在体验开始时分析空间映射数据，以判断用户是否应该执行其他步骤来提高空间地图的完整性和质量。 如果用户需要扫描环境，应在扫描体验期间提供明确的指导。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  最佳  |  会见 |  失败 |
--- | --- | ---
|  空间网格的可视化效果告知用户扫描正在进行。 用户清楚地知道要执行什么操作，以及扫描何时开始和停止。 | 提供了空间网格的可视化效果，但用户可能无法清楚地知道要执行哪些操作，并且未提供进度信息。 | 无网格可视化效果。 未向用户提供有关查找位置或扫描开始/停止时间的指导信息。 |

### <a name="how-to-measure"></a>如何度量

* 在所需的房间扫描期间，会提供视觉和音频指南，指示查找位置以及何时开始和停止扫描。

### <a name="recommendations"></a>建议

* 指示用户附近的总容量需要属于体验的一部分。
* 扫描开始和停止时通信，例如进度指示器。
* 在扫描期间使用网格的可视化效果。
* 提供视觉和音频提示，鼓励用户查看并移动房间。
* 告知用户要在何处改进数据。 在许多情况下，最好告诉用户他们需要执行哪些操作 (例如，查看上限、在) 后面查看，以获得必要的扫描质量。

### <a name="resources"></a>资源

#### <a name="documentation"></a>文档

* [房间扫描可视化](../../design/room-scan-visualization.md)
* [案例研究：扩展应用程序的空间映射HoloLens](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [案例研究：HoloTour 的空间音效设计](../../design/case-study-spatial-sound-design-for-holotour.md)
* [案例研究：在片段中创建沉浸式体验](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>工具和教程

* [混合现实Toolkit - UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>方向指示器

在混合现实应用中，内容可能位于视场之外，或被实际对象遮挡。 设计良好的应用可让用户更轻松地查找不可见的内容。 方向指示器提醒用户注意重要内容，并提供有关用户位置的内容的指导。 非可见内容的指南可能以声音提示、方向箭头或直接视觉提示的形式提供。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  最佳  |  会见 |  失败 |
--- | --- | ---
|  视觉和音频提示直接引导用户查看视场外的相关内容。 | 一个箭头或一些指示符，用于将用户指向内容的一般方向。 | 相关内容位于视场之外，并且向用户提供了差或无位置指南。 | 

### <a name="how-to-measure"></a>如何度量

* 可以通过视觉和/或音频提示发现用户视场之外的相关内容。

### <a name="recommendations"></a>建议

* 当相关内容位于用户视场之外时，请使用方向指示器和音频提示来指导用户查看内容。 在许多情况下，直接视觉指南比方向箭头更可取。
* 方向指示器不应内置于光标中。

### <a name="resources"></a>资源

* [全息帧](../../design/holographic-frame.md)

## <a name="data-loading"></a>数据加载

进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。 这可能意味着，当进度指示器可见时，用户无法与应用交互，并且还可以指示等待时间可能有多长。

### <a name="device-impact"></a>设备影响

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>质量标准

|  最佳  |  会见 |  失败 |
--- | --- | ---
|  动态视觉指示器，以进度栏或环的形式显示任何数据加载或处理过程中的进度。 可视指示器提供有关等待时间的指导。 | 用户被通知正在加载数据，但无法指示等待时间。 | 任务的数据加载或处理指示器不会超过 5 秒。 |

### <a name="how-to-measure"></a>如何度量

* 在数据加载过程中，验证在 5 秒以上没有空白状态。

### <a name="recommendations"></a>建议

* 提供一个数据加载动画器，用于显示用户可能认为此应用已停止或崩溃的任何情况下的进度。 合理的经验法则是任何"加载"活动，可能需要超过 5 秒。

### <a name="resources"></a>资源

* [显示进度](../../design/progress.md)