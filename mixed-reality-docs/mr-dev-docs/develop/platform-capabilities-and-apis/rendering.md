---
title: 渲染
description: 了解全息着色如何使您的应用程序能够在世界各地的用户的精确位置绘制一个全息影像。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 呈现，全息影像
ms.openlocfilehash: d01a5911ad8b479197bd38e8ed7825feef1f69dc51d2c2dc2f8e500e93880955
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193663"
---
# <a name="rendering"></a>渲染

全息渲染使你的应用程序可以在世界各地的确切位置绘制一个全息影像，无论是精确地放入到物理领域还是在创建的虚拟领域内。 [全息影像](../../discover/hologram.md)是发出声音和光的对象。 呈现使应用程序能够添加光。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>第一代 (HoloLens) </strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>渲染</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>全息渲染

用于全息呈现的关键是了解所使用的设备类型。 具有 "**查看**" 的设备显示（如 [HoloLens](/hololens/hololens1-hardware)）可向世界添加光源。 黑色像素是完全透明的，而较亮的像素则越来越不透明。 由于显示器中的光线被添加到现实世界的灯光，因此白色像素是半透明的。

尽管 stereoscopic 呈现为你的全息影像提供了一个深度提示，但增加了 [接地效果](../../design/interaction-fundamentals.md) 可帮助用户更轻松地了解到全息图附近的图面。 一种接地方法是围绕附近图面上的全息图添加发光，然后针对此发光呈现阴影。 这样一来，您的阴影就会显得比环境少一些。 [空间音效](../../design/spatial-sound.md) 是另一个重要的深度提示，可让用户了解全息图的距离和相对位置。

显示不 **透明** 的设备，如 [Windows Mixed Reality 沉浸式耳机](../../discover/immersive-headset-hardware-details.md)，会将世界区向外。 黑色像素为纯色，而任何其他颜色则作为该颜色显示给用户。 应用程序负责呈现用户看到的所有内容。 这使得更重要的是保持持续的刷新率，使用户有舒适的体验。

## <a name="predicted-rendering-parameters"></a>预测呈现参数

混合现实耳机 (HoloLens 和沉浸式耳机) 持续跟踪用户相对于其周围的位置和方向。 当您的应用程序开始准备下一帧时，系统将预测用户在显示器上的未来的哪一段时间。 根据此预测，系统将计算用于该帧的视图和投影转换。 应用程序 **必须使用这些转换才能生成正确的结果**。 如果未使用系统提供的转换，则生成的图像不会与真实环境保持一致，从而导致用户 discomfort。

> [!NOTE]
> 为了准确预测新帧何时会到达显示器，系统会不断地测量应用程序渲染管道的端到端延迟。 当系统调整到您的渲染管道的长度时，您可以通过使该管道尽可能简短来改善全息影像的稳定性。

使用高级技术来增强系统预测的应用程序可能会覆盖系统视图和投影转换。 这些应用程序仍然必须使用系统提供的转换，以使其自定义转换产生有意义的结果。

## <a name="other-rendering-parameters"></a>其他呈现参数

呈现帧时，系统将指定应用程序应在其中进行绘制的后台缓冲区视区。 此视区通常小于帧缓冲区的完整大小。 无论什么是视区大小，应用程序呈现一帧后，系统都将 upscales 图像以填充整个显示器。

对于自行找不到的应用程序，无法按所需的刷新速率进行呈现， [系统呈现参数可以配置](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) 为减少内存压力，并以增加像素别名的成本呈现成本。 还可以更改后台缓冲区格式，对于某些应用，这可以帮助提高内存带宽和像素吞吐量。

呈现拆分器、分辨率和应用程序在其中呈现的帧速率可能也会随帧之间的变化而变化，并且可能会在左右眼睛之间有所不同。 例如，当 [混合现实捕获](/hololens/holographic-photos-and-videos) (MRC) 处于活动状态，并且未选择 " [照片/视频相机" 视图配置](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) 时，可能会使用较大的 FOV 或分辨率来呈现一种眼睛。

对于任何给定的帧，应用 *必须* 使用系统提供的视图转换、投影转换和视区分辨率进行呈现。 此外，应用程序决不能假设任何呈现或视图参数都保持从帧到帧的固定。 类似于 Unity 的引擎会在其自己的相机对象中处理所有这些转换，以便始终遵循用户的物理移动和系统的状态。 如果你的应用程序允许用户通过世界来虚拟移动 (例如，在游戏板上使用操纵杆) ，你可以在移动它的相机上方添加一个父远程测试机组对象。 这将导致照相机反映用户的虚拟动作和物理动作。 如果你的应用程序修改系统提供的视图转换、投影转换或视区维度，则它必须通过调用相应的 [重写 API](/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)来通知系统。

若要提高全息呈现的稳定性，应用应提供 Windows 每个帧用于呈现的深度缓冲区。 如果你的应用程序提供了深度缓冲区，则它应具有连贯的深度值，并以米为单位从相机中表示深度。 这使系统可以使用每像素深度数据来更好地实现稳定的内容，前提是用户的头与预测的位置有略微的偏移量。 如果无法提供深度缓冲区，则可以提供焦点，并定义一个用于剪切大部分内容的平面。 如果深度缓冲区和焦点平面都提供，则系统可能会同时使用这两者。 特别是，提供深度缓冲区和焦点（当应用程序显示动态影像时包含速度矢量）会很有帮助。

有关本主题的详细信息，请参阅 [DirectX 文章中的呈现](../native/rendering-in-directx.md) 。

## <a name="holographic-cameras"></a>全息相机

Windows Mixed Reality 引入了 **全息相机** 的概念。 全息相机类似于3D 图形文本中的传统相机;它们同时定义外部 (位置和方向) 和内部照相机属性。  (例如，视图字段用于查看虚拟三维场景。 ) 不同于传统的3D 相机，应用程序不控制相机的位置、方向和内部属性。 而是通过用户的移动隐式控制全息相机的位置和方向。 用户的移动通过视图转换逐帧地中继到应用程序。 同样，照相机的内部属性由设备的校准光学，并通过投影转换按帧中继。

通常，应用程序将针对单个立体声相机进行呈现。 可靠的呈现循环将支持多个照相机，同时支持 mono 和立体声相机。 例如，当用户激活 [混合现实捕获](/hololens/holographic-photos-and-videos) (MRC) 等功能时，系统可能会要求你的应用程序从备用角度进行呈现，具体取决于头戴式耳机形状。 可以支持多个照相机的应用 [程序通过选择](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) 他们可以支持的相机 [类型](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) 来获取它们。

## <a name="volume-rendering"></a>立体渲染

在三维中呈现医学面向 mri 或工程量时，通常使用 [卷渲染](volume-rendering.md) 技术。 这些技术在混合现实中非常有趣，用户可以自然地从不同的角度观看此类卷，只需移动其头。

## <a name="supported-resolutions-on-hololens-first-gen"></a> (第一代 HoloLens 上支持的分辨率) 

* 最大视区大小是 [HolographicDisplay](/uwp/api/windows.graphics.holographic.holographicdisplay)的属性。 默认情况下，HoloLens 设置为最大的视区大小，即 720p (1268x720) 。
* 可以通过在 HolographicCamera 上设置 ViewportScaleFactor 来更改视区大小。 此比例因子在0到1的范围内。
*  (第一代) HoloLens 上支持的最小视区大小为720p 的50%，即 360p (634x360) 。 这是0.5 的 ViewportScaleFactor。
* 由于视觉对象降级，不建议使用小于540p 的任何内容，但可用于识别像素填充率的瓶颈。

## <a name="supported-resolutions-on-hololens-2"></a>HoloLens 2 支持的解决方法

* 支持的当前和最大呈现器目标大小是 [视图配置](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)的属性。 默认情况下，HoloLens 2 设置为1440x936 的最大呈现目标大小。
* 应用可以通过调用 RequestRenderTargetSize 方法来更改呈现器目标缓冲区的大小，以请求新的呈现目标大小。 将选择一个新的呈现目标大小，该大小满足或超过请求的呈现目标大小。 此 API 更改呈现器目标缓冲区的大小，这需要在 GPU 上重新分配内存。 这包括：呈现目标大小可缩小以减少 GPU 上的内存压力，不应以高频率调用此方法。
* 应用仍可更改视区大小，其方式与 HoloLens 1 相同。 不会在 GPU 上增加内存重新分配，因此它可以以较高的频率进行更改，但不能用于减少 GPU 上的内存压力。
* HoloLens 2 上支持的最小视区大小为634x412，当使用默认呈现器目标大小时，ViewportScaleFactor 约为0.44。
* 如果提供的呈现目标大小小于受支持的最小视区大小，则会忽略视区缩放系数。
* 由于视觉对象降级，不建议使用小于540p 的任何内容，但可用于识别像素填充率的瓶颈。



## <a name="see-also"></a>另请参阅
* [全息影像稳定性](hologram-stability.md)
* [在 DirectX 中渲染](../native/rendering-in-directx.md)