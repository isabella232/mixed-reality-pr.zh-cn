---
title: 开发人员的混合现实捕获
description: 了解为开发人员启用、使用和呈现混合现实捕获的最佳实践。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc， 照片， 视频， 捕获， 相机
ms.openlocfilehash: af585cd212ba8f2ddc3ea812c1fff2a5da8603bff0e77d8fc2ad794486821685
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192088"
---
# <a name="mixed-reality-capture-for-developers"></a>开发人员的混合现实捕获

> [!NOTE]
> 有关[新 MRC](#render-from-the-pv-camera-opt-in)功能的指导，请参阅下面的 PV 相机渲染HoloLens 2。

你 [随时都可以在](/hololens/holographic-photos-and-videos) MRC (或视频) 混合现实捕获，但在开发应用程序时，需要记住一些内容。 这包括有关 MRC 视觉质量以及捕获 MRC 时响应系统更改的最佳实践。

开发人员还可以无缝地将混合现实捕获和插入集成到其应用中。

HoloLens (第一代) 上的 MRC 支持高达 720p 的视频和照片，而 HoloLens 2 上的 MRC 支持高达 1080p 的视频和高达 4K 分辨率的照片。

## <a name="the-importance-of-quality-mrc"></a>质量 MRC 的重要性

无论是用户页面上的混合现实屏幕截图Microsoft Store还是其他用户共享社交网络上的捕获内容，混合现实捕获媒体通常是用户首次向应用公开。 可以使用 MRC 演示应用、培训用户、鼓励用户共享其混合世界交互，以及进行用户研究并解决问题。

## <a name="how-mrc-impacts-your-app"></a>MRC 如何影响应用

### <a name="enabling-mrc-in-your-app"></a>在应用中启用 MRC

默认情况下，应用不必执行任何操作来使用户能够进行混合现实捕获。

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>为应用中的 MRC 启用改进的对齐方式

默认情况下，混合现实捕获将右眼的全息输出与照片/视频 (PV) 相机。 这两个源使用当前正在运行的沉浸式应用设置的焦点进行组合。

这意味着，由于 PV 相机和右侧显示器之间的物理距离，焦点平面外部的全息影像不会对齐。

#### <a name="set-the-focus-point"></a>设置焦点

沉浸 (应用程序HoloLens) 应设置其稳定平面的聚焦点。 [](../unity/focus-point-in-unity.md) 这可确保在头戴显示设备以及混合现实捕获中实现最佳对齐方式。

如果未设置焦点，则稳定平面默认为 2 米。

#### <a name="render-from-the-pv-camera-opt-in"></a>从 PV 相机渲染 (选择加入) 

HoloLens 2使沉浸式应用能够在混合现实捕获运行时从 **PV** 相机渲染。 若要确保应用正确支持其他呈现，应用必须选择加入此功能。

从 PV 相机渲染比默认的 MRC 体验提供以下改进：
* 全息影像与物理环境和手部之间的近距交互应准确无误。 避免在除焦点外的距离有偏移量，如在默认 MRC 中可能看到。
* 头戴显示设备中的右眼不会受到影响，因为它不会用于呈现 MRC 输出的全息影像。

启用 PV 相机渲染有三个步骤：
1. 启用 PhotoVideoCamera HolographicViewConfiguration
2. 处理其他 HolographicCamera 渲染器
3. 验证着色器以及代码是否从此额外的 HolographicCamera 正确呈现

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a>在 DirectX 中启用 PhotoVideoCamera HolographicViewConfiguration

若要选择从 PV 相机进行渲染，应用只需启用 PhotoVideoCamera 的[HolographicViewConfiguration：](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>在 DirectX 中处理其他 HolographicCamera 渲染

当应用选择从 PV 相机渲染时，混合现实捕获将开始：
1. 将发射 HolographicSpace 的 CameraAdded 事件。 如果应用目前无法处理相机，可以延迟此事件。
2. 完成事件后，没有未完成的延迟，HolographicCamera 将显示在下一个全息帧的 AddedCameras 列表中。

当混合现实捕获停止 (或者当混合现实捕获正在运行) 时，如果应用禁用了视图配置：HolographicCamera 将显示在下一个全息帧的 RemovedCameras 列表中，并且将启动 HolographicSpace 的 CameraRemoved 事件。

[ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)属性已添加到 HolographicCamera，以帮助识别相机所属的配置。

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a>在 Unity 中启用 PhotoVideoCamera HolographicViewConfiguration

> [!NOTE]
> 如果使用的是 Unity 2018，则需要 **Unity 2018.4.13f1** 或更高版本。 如果使用的是 Unity 2019，则需要 **Unity 2019.4** 或更高版本。

若要在使用混合现实相机时选择从 PV 相机 [Toolkit，](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)请启用 Windows Mixed Reality Camera [设置](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings)提供程序，并选中"从 PV 相机 **渲染"。**

如果不使用混合现实Toolkit，可以使用 组件手动选择加入，如上述 DirectX 所述[](#enable-the-photovideocamera-holographicviewconfiguration-in-directx)。

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>在 Unity 中处理其他 HolographicCamera 呈现

Unity 会自动完成此操作。

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a>在 Unreal 中启用 PhotoVideoCamera HolographicViewConfiguration

> [!NOTE]
> 这需要 Unreal Engine 4.25 或更高版本。

若要选择从 PV 摄像头进行渲染：

1. 调用 SetEnabledMixedRealityCamera 和 ResizeMixedRealityCamera 
    * 使用“尺寸 X”和“尺寸 Y”值设置视频尺寸。 

![第三人称摄像头](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a>在 Unreal 中处理其他 HolographicCamera 渲染

Unreal 会自动完成此操作。

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>验证着色器与代码是否支持其他相机

运行混合现实捕获并检查异常对齐、缺少内容或性能问题。 根据情况更新着色器和代码。

如果某些场景不支持渲染到其他相机，可以禁用 PhotoVideoCamera 的 HolographicViewConfiguration。

### <a name="disabling-mrc-in-your-app"></a>在应用中禁用 MRC

#### <a name="2d-app"></a>2D 应用

运行混合现实捕获时，2D 应用可以选择让视觉内容模糊化：
* 具有 DXGI_PRESENT_RESTRICT_TO_OUTPUT[标志](/windows/desktop/direct3ddxgi/dxgi-present)
* 使用 DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED 标志 [创建应用的交换](/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) 链
* 使用 Windows 10 2019 年 5 月更新，设置 ApplicationView 的[IsScreenCaptureEnabled](/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)

#### <a name="immersive-app"></a>沉浸式应用

沉浸式应用可以选择通过以下方式将其视觉内容从混合现实捕获中排除：
* 将 HolographicCameraRenderingParameter 的 [IsContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) 设置为禁用其关联帧的混合现实捕获
* 设置 HolographicCamera 的 [IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) 以禁用其关联的全息相机的混合现实捕获

#### <a name="password-keyboard"></a>密码键盘

使用Windows 10 2019 年 5 月更新，当密码或固定键盘可见时，视觉对象内容会自动从混合现实捕获中排除。

### <a name="knowing-when-mrc-is-active"></a>了解 MRC 何时处于活动状态

[应用可以使用 AppCapture](/uwp/api/Windows.Media.Capture.AppCapture)类来了解系统混合现实捕获何时 (音频或视频捕获) 。

>[!NOTE]
>如果设备上没有混合现实捕获，AppCapture 的 [GetForCurrentView](/uwp/api/windows.media.capture.appcapture.getforcurrentview) API 可能会返回 null。 在应用挂起时取消注册 CapturingChanged 事件也很重要，否则 MRC 可能会进入阻止状态。

### <a name="best-practices-hololens-specific"></a>特定于 (HoloLens的) 

MRC 预期无需额外的开发工作即可工作，但在提供最佳混合现实捕获体验时，需要注意一些内容。

**MRC 使用全息影像的 alpha 通道与相机 [图像](locatable-camera.md) 混合**

最重要的步骤是确保应用清除为透明黑色，而不是清除为不透明黑色。 在 Unity 中，默认情况下使用 MixedRealityToolkit 完成此操作。 如果要在非 Unity 中开发，可能需要进行单行更改。

如果应用未清除为透明黑色，你可能会在 MRC 中看到以下项目：

**示例失败**：内容周围的黑色边缘 (无法清除到透明黑色) 

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failure to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**示例失败**：全息影像的整个背景场景显示为黑色。 设置 1 的背景 alpha 值会导致黑色背景

![将背景 alpha 值设置为 1 会导致黑色背景](images/clearopaqueblack-300px.png)

**预期结果**：全息影像清除为透明黑色图像时， (与实际结果正确混合) 

![清除为透明黑色时的预期结果](images/cleartransparentblack-300px.png)

**解决方案**；
* 将显示为不透明黑色的任何内容更改为 alpha 值为 0。
* 确保应用清除为透明黑色。
* Unity 默认使用 MixedRealityToolkit 自动清除，但如果它是非 Unity 应用，应修改 ID3D11DeiceContext：：ClearRenderTargetView () 。 你想要确保清除透明黑色 (0，0，0，0) ，而不是不透明的黑色 (0，0，0，1) 。

现在，如果需要，可以优化资产的 alpha 值，但通常不需要。 大多数情况下，MRC 看起来开箱即用。 MRC 假定预乘 alpha。 alpha 值仅影响 MRC 捕获。

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>当在 HoloLens 上启用了 MRC 时应发生的情况

以下各项适用于 HoloLens (第一代) 和 HoloLens 2，除非另有说明：

* 系统会将应用程序限制为 30-Hz。 这会为 MRC 创建一些空间，使应用无需保留固定预算预留，同时还可匹配 30 fps 的 MRC 视频记录的帧速率
* 录制/流式处理 MRC 时，全息图内容在设备上显示为 "火花"：文本可能会变得更难以阅读，如果 (选择第三个照相机呈现 **HoloLens 2** ，则可能会出现更多的 jaggy) 
* 当应用程序启用了应用程序时，MRC 照片和视频将遵循应用程序的 [重点点](../unity/focus-point-in-unity.md) ，这将有助于确保全息影像精确定位。 对于视频，重点是平滑的，因此，如果焦点深度发生变化，全息影像可能会慢慢地发生缓慢偏移。 与焦点位于不同深度的全息影像可能会显示与现实世界 (的偏移量，请参阅下面的示例，其中焦点设置为2米，而全息图位于1米) 。

![以2计量速率显示的全息影像将完全注册到全球。 近距离或远距离的全息影像可能会略微偏移。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>在应用中集成 MRC 功能

混合现实应用可以从应用内启动 MRC 照片或视频捕获，而捕获的内容将在应用中提供，而不会存储到设备的 "照相机"。 您可以创建自定义的 MRC 记录器或利用内置的相机捕获 UI。 

### <a name="mrc-with-built-in-camera-ui"></a>带有内置照相机 UI 的 MRC

开发人员只需编写几行代码，即可使用 *[相机捕获 UI API](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 获取用户捕获的混合现实照片或视频。

此 API 启动内置的 MRC 相机 UI，用户可以在其中拍摄照片或视频，并将生成的捕获结果返回到应用。 如果需要添加自己的相机 UI 或较低级别的访问权限来捕获流，则可以创建自定义混合现实捕获记录器。

### <a name="creating-a-custom-mrc-recorder"></a>创建自定义 MRC 记录器

尽管用户始终可以使用系统 MRC 捕获服务来触发照片或视频，但应用程序可能需要构建自定义相机应用程序，该应用程序在相机流中包含全息影像，就像在 "MRC" 中一样。 这样，应用程序便可以从用户输入、生成自定义录制 UI，或自定义 MRC 设置以命名几个示例。

**HoloStudio 使用 MRC 效果添加自定义 MRC 相机**

![HoloStudio 使用 MRC 效果添加自定义 MRC 相机](images/cameraiconholostudio-300px.jpg)

Unity 应用程序应看到属性 [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) ，以启用全息影像。

其他应用程序可以通过使用[Windows 媒体捕获 api](/uwp/api/Windows.Media.Capture.MediaCapture)来控制相机并添加 MRC 视频和音频效果，以将虚拟全息影像和应用程序音频包含在静止图像和视频中。

应用程序有两个选项可添加效果：
* 旧的 API： [Windows。MediaCapture. AddEffectAsync () ](/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* 新的 Microsoft 推荐 API (返回对象，从而能够) ： Windows 操作动态属性[。MediaCapture. AddVideoEffectAsync () ](/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [Windows。MediaCapture. AddAudioEffectAsync () ](/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync)要求应用创建自己的[IVideoEffectDefinition](/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)和[IAudioEffectDefinition](/uwp/api/windows.media.effects.iaudioeffectdefinition)的实现。 有关示例，请参阅 [MRC 示例应用](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture) 。

>[!NOTE]
> Windows。Visual Studio 无法识别 MixedRealityCapture 命名空间，但字符串仍然有效。

MRC 视频效果 (**Windows。MixedRealityCapture. MixedRealityCaptureVideoEffect**) 

|  属性名称  |  类型  |  默认值  |  说明 |
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([mediastreamtype.video](/uwp/api/Windows.Media.Capture.MediaStreamType))   |  1 (VideoRecord)   |  描述此影响所使用的捕获流。 音频不可用。 |
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  用于在视频捕获中启用或禁用全息影像的标志。 |
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  用于在全息影像捕获期间启用或禁用录制指示器的标志。 |
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  用于启用或禁用由 HoloLens 跟踪器支持的视频稳定性的标志。 |
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  设置视频抖动使用的历史帧数。 从电源和性能的角度来看，0从0到延迟，几乎是 "免费"。 15对于最高质量 (建议使用15帧延迟和内存) 。 |
|  GlobalOpacityCoefficient  |  float  |  0.9 (HoloLens) 1.0 (沉浸式耳机)   |  将范围从 0.0 (完全透明) 到 (1.0 的全局不透明度系数设置为完全不透明) 。 |
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  用于启用或禁用在有显示受保护内容的 2d UWP 应用时返回空帧的标志。 如果此标志为 false，并且二维 UWP 应用显示受保护的内容，则在耳机和混合现实捕获中，二维 UWP 应用将替换为受保护的内容纹理。 |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  用于启用或禁用显示全息相机隐藏区域网格和相邻内容的标志。 |
| OutputSize | 大小 | 0, 0 | 在裁剪视频稳定性后设置所需的输出大小。 如果指定了0或指定了无效的输出大小，则选择默认裁剪大小。 |
| PreferredHologramPerspective | UINT32 | Windows 设备门户中的 "**从相机渲染**" 设置 | 用于指示应捕获的全息相机视图配置的枚举： 0 (显示) 意味着不会要求应用从照片/视频相机进行渲染，1 (PhotoVideoCamera) 会要求应用从照片/视频摄像机， (应用程序支持它) 。 仅 HoloLens 2 上支持 |

>[!NOTE]
> 可以通过转到 [混合现实捕获页面](using-the-windows-device-portal.md#mixed-reality-capture)并取消选中 "**从相机** 中进行渲染"，在 Windows 设备门户中更改 **PreferredHologramPerspective** 的默认值。 设置默认为 **1 (PhotoVideoCamera)**，但可以取消选中以将其设置为 **0 (显示)**。
>
> **PreferredHologramPerspective** 的默认值为 0 (在2020年6月 (Windows 全息版、版本2004生成19041.1106 和 Windows 全息版本1903生成 18362.1064) **显示)** 。

MRC 音频效果 (**Windows。MixedRealityCapture. MixedRealityCaptureAudioEffect**) 

| 属性名称 | 类型 | 默认值 | 说明 |
|----------|----------|----------|----------|
| MixerMode | UINT32 | 2 (麦克风和系统音频)  | 用于指示应使用的音频源的枚举： 0 (Mic 音频) ，1 (系统音频仅) ，2 (Mic 和系统音频)  |
| LoopbackGain | float | Windows 设备门户中的 **应用音频增益** 设置 | 适用于系统音频音量的增益。 范围为0.0 到5.0。 仅 HoloLens 2 上支持 |
| MicrophoneGain | float | Windows 设备门户中的 **Mic 音频增益** 设置 | 适用于麦克风音量的增益。 范围为0.0 到5.0。 仅 HoloLens 2 上支持 |

>[!NOTE]
> 可以通过转到 [混合现实捕获页面](using-the-windows-device-portal.md#mixed-reality-capture)并调整其各自设置旁的滑块来更改 Windows 设备门户中 **LoopbackGain** 或 **MicrophoneGain** 的默认值。 这两个设置默认为 **1.0**，但可以设置为 **0.0** 和 **5.0** 之间的任何值。
>
> 在2020年6月的更新中，使用 Windows 设备门户配置默认增益 (Windows 全息版2004内部版本19041.1106 和 Windows 全息版 1903 build 18362.1064) 。

### <a name="simultaneous-mrc-limitations"></a>同时 MRC 限制

如果多个应用同时访问了 MRC，则需要了解某些限制。

#### <a name="photovideo-camera-access"></a>照片/视频相机访问

在 HoloLens 1 上，当进程录制视频或拍摄照片时，MRC 将无法捕获照片或捕获视频。 反之亦然：如果 MRC 正在运行，则应用程序将无法访问相机。 

使用 HoloLens 2，可以共享对相机的访问。 如果不需要直接控制分辨率或帧速率，则可以使用 [SharedMode 属性](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) 和 SharedReadOnly 初始化 MediaCapture。  

##### <a name="built-in-mrc-photovideo-camera-access"></a>内置的 MRC 照片/视频相机访问

通过 Cortana、开始菜单、硬件快捷方式、Miracast、Windows 设备门户 (内置于 Windows 10 的 MRC 功能：

* 默认情况下，将使用 ExclusiveControl 运行

但是，已将支持添加到 MRC 子系统以在共享模式下运行： 

* 如果应用请求 ExclusiveControl 访问照片/视频摄像机，内置的 MRC 会自动停止使用照片/视频相机，因此应用的请求将会成功。 
* 如果在应用具有 ExclusiveControl 的情况下启动了内置的 MRC，内置的 MRC 将在 SharedReadOnly 模式下运行 

此共享模式功能有一些限制：

* 照片通过 Cortana、硬件快捷方式或 "开始" 菜单：需要 Windows 10 2018 年4月更新 (或更高版本) 
* 视频 via Cortana、硬件快捷方式或 "开始" 菜单： Windows 10 需要2018年4月更新 (或更高版本) 
* Miracast 上的流式处理 MRC：需要 Windows 10 2018 年10月更新 (或更高版本) 
* Windows 设备门户上或通过 HoloLens 配套应用来流式传输 MRC：需要 HoloLens 2

>[!NOTE]
> 当另一个应用正在使用 photo/视频摄像机时，内置 MRC 相机 UI 的分辨率和帧速率可能会从其正常值中减少。

#### <a name="mrc-access-for-developers"></a>开发人员的 MRC 访问

建议你始终在使用 MRC 时请求对相机进行独占控制。 这将确保你的应用程序可以完全控制照相机的设置，前提是你知道上面列出的限制。 

* 使用[初始化设置](/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041)创建媒体捕获对象
* 将 [SharingMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode) 属性设置为 **exclusive**

> [!CAUTION]
> 继续操作之前，请务必仔细阅读 [SharingMode 备注](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks) 。

* 按所需方式设置照相机
* 启动应用，使用启动 API 捕获视频帧，然后启用 MRC

> [!CAUTION]
> 如果在启动应用之前启动了 MRC，我们无法保证功能将按预期工作。

你可以在 [全息面跟踪示例](/samples/microsoft/windows-universal-samples/holographicfacetracking)中找到上述过程的完整示例。

> [!NOTE]
> 在 Windows 10 2018 年4月更新之前，应用程序的自定义 MRC 记录器与系统 MRC 互斥 (从 Windows 设备门户) 捕获照片、捕获视频或流式处理。

## <a name="see-also"></a>请参阅

* [混合现实捕获](/hololens/holographic-photos-and-videos)
* [旁观视图](spectator-view.md)
* [Unity 开发概述](../unity/unity-development-overview.md)
* [Unreal 开发概述](../unreal/unreal-development-overview.md)
