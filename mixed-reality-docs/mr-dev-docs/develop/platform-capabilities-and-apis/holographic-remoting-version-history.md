---
title: 全息远程处理版本历史记录
description: 随时了解 HoloLens 2 的全息远程处理功能的版本历史记录。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 07/20/2021
ms.topic: article
keywords: HoloLens，远程处理，全息远程处理，版本历史记录，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 21ba89e477872f5dfa41468f1a7f2d7507affd681556d79843c195d7d5839e7b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223548"
---
# <a name="holographic-remoting-version-history"></a>全息远程处理版本历史记录

> [!IMPORTANT]
> 本指南特定于 HoloLens 2 上的全息远程处理。

## <a name="version-261-july-20-2021"></a>版本 2.6.1 (7 月20日 2021) <a name="v2.6.1"></a>
* XR_MSFT_holographic_remoting_speech 扩展现在允许在运行会话期间使用新参数重新初始化语音识别器。
* 修复了语音识别可靠性在多个连接上减少的问题。
* 各种 bug 修复和稳定性改进。

## <a name="version-260-june-10-2021"></a>版本 2.6.0 (6 月10日 2021) <a name="v2.6.0"></a>
* 使用 OpenXR API 的全息远程处理现在支持：
  * 新的 XR_MSFT_holographic_remoting_speech 扩展，它允许应用程序以各种语言侦听自定义语音命令。
  * XR_MSFT_scene_understanding 扩展，它为应用程序提供用户环境中平面、网格和对象的结构化、高级别表示形式，从而实现空间感知应用程序的开发。 不过，请注意，XR_SCENE_COMPUTE_CONSISTENCY_OCCLUSION_OPTIMIZED_MSFT 是 xrComputeNewSceneMSFT 支持的唯一一致性。
  * XR_MSFT_spatial_graph_bridge 扩展，它允许应用程序创建 XrSpace 句柄来跟踪其他 Windows Mixed Reality 设备平台库或 api 的空间 Graph 节点。 不过，请注意，XR_SPATIAL_GRAPH_NODE_TYPE_STATIC_MSFT 是 xrCreateSpatialGraphNodeSpaceMSFT 支持的唯一节点类型。 
* 使用混合现实 API 的全息远程处理现在支持：
  * SpatialGraphInteropPreview CreateCoordinateSystemForNode 重载，它允许应用程序跟踪 Graph 节点的静态空间，使用户能够在其环境中实现位置和操作。
* 使用 OpenXR 和混合现实 Api 的全息远程处理现在支持：
  * MixedReality. SceneUnderstanding SDK，它允许应用程序计算围绕用户的场景的说明 (如墙壁、地面和表面) 提供四边形、网格和内容放置提示。
  * MixedReality SDK，它允许应用程序跟踪检测到的 QR 码的位置、大小和内容。
* OpenXR 远程示例已更新为包含： 
  * 使用 XR_MSFT_holographic_remoting_speech 扩展的示例。
* 混合现实远程示例已更新为包括：  
  * 使用 MixedReality. SceneUnderstanding SDK 的示例。
  * 使用 MixedReality SDK (的一个示例，它将替换以前的 QR 码检测机制) 。
* 在建立连接时，全息远程处理播放机将显示加载动画。
* 修复了 OpenXR API 运行时和混合现实 API 示例中的 RenderDoc 兼容性问题。
* 各种 bug 修复和稳定性改进。

## <a name="version-250-february-12-2021"></a>版本 2.5.0 (2021 年2月12日) <a name="v2.5.0"></a>
* 使用 [OPENXR API](../native/openxr.md) 的全息远程处理现在支持：
  * XR_MSFT_spatial_anchor 扩展。 此扩展允许应用程序创建空间锚点，这是用户的物理环境中的任意可用空间点，将由运行时跟踪。
  * XR_MSFT_controller_model 扩展。 此扩展提供了一种机制，用于加载控制器的 GLTF 模型。
  * 作为 XR_MSFT_holographic_remoting 扩展的一部分的自定义数据通道。 [OpenXR 远程示例](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)中显示了一个示例。
* 改善了播放器与远程端之间的同步。 这允许动态变化的姿势和帧缓冲，确保远程呈现的内容平稳地达到预期的目标帧速率。
* 通过 Microsoft Store 提高的全息远程处理播放机的性能。 在 HoloLens 2 播放机现在在每秒60帧上运行。
* 优化了可通过 [SpatialSurfaceObserver](/uwp/api/windows.perception.spatial.surfaces.spatialsurfaceobserver) 通过远程应用查询的空间 surface 网格传输。
* 修复了在断开连接时调用 SpatialAnchorManager 方法或释放定位点的问题。
* 固定线程问题导致关闭 PlayerContext 或 RemoteContext 实例时出现故障。
* 桌面上的全息远程处理播放机：未安装 Windows Mixed Reality，而不是以无提示方式关闭时显示错误消息。
* 许多其他 bug 修复和稳定性改进。

## <a name="version-241-january-22-2021"></a>版本 2.4.1 (2021 年1月22日) <a name="v2.4.1"></a>

* 修复了在连接时调用时 SpatialAnchorManager：： RequestStoreAsync 无法可靠工作的问题。
* 修复了 SpatialAnchorManager：： TrySave 无法正确保存定位点的问题。

## <a name="version-240-december-1-2020"></a>版本 2.4.0 (2020 年12月1日) <a name="v2.4.0"></a>

* 全息远程处理现在支持使用 [OPENXR API](../native/openxr.md)写入远程应用。 请参阅 [使用 OpenXR Api 编写全息远程处理远程应用](holographic-remoting-create-remote-openxr.md) ，开始使用。
* Bug 修复和稳定性改进。

## <a name="version-231-october-10-2020"></a>版本 2.3.1 (2020 年10月10日) <a name="v2.3.1"></a>

* 通过远程姿势预测固定回归，导致视觉抖动。
* 实现了 PerceptionDeviceSetCreateFactoryOverride，这确保了全息远程处理随附的 PerceptionDevice.dll 不会干扰 Windows 10 附带的版本。

## <a name="version-230-october-2-2020"></a>版本 2.3.0 (10 月2日 2020) <a name="v2.3.0"></a>

* 修复了在全息远程处理播放机挂起时可能发生的崩溃。
* 稳定性改进。

## <a name="version-223-august-28-2020"></a>版本 2.2.3 (2020 年8月28日) <a name="v2.2.3"></a>

* Bug 修复和稳定性改进。

## <a name="version-222-july-10-2020"></a>版本 2.2.2 (2020 年7月10日) <a name="v2.2.2"></a>

* 解决了在 Windows Mixed Reality 耳机进行流式处理时， [LeftViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters)和[HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters)的问题。
* 修复了故障，这种情况可能会导致网络连接不佳。

## <a name="version-221-july-6-2020"></a>版本 2.2.1 (7 月6日 2020) <a name="v2.2.1"></a>

> [!IMPORTANT]
> 版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)的[Windows 应用认证包](https://developer.microsoft.com/windows/downloads/app-certification-kit/)验证将失败。 如果你在版本 [2.2.0](holographic-remoting-version-history.md#v2.2.0) 上，并且想要将你的应用程序提交到 Microsoft store p 租约更新为至少版本2.2.1。
* 修复了[Windows 应用认证包](https://developer.microsoft.com/windows/downloads/app-certification-kit/)相容性问题。

## <a name="version-220-july-1-2020"></a>版本 2.2.0 (2020 年7月1日) <a name="v2.2.0"></a>

* 全息远程处理播放器现在可以安装在运行[Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md)的 pc 上，使其可以流式传输到沉浸式耳机。
* [运动控制器](../../design/motion-controllers.md) 现在支持全息远程处理，并且可以通过 [SpatialInteractionSource](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)检索控制器特定的数据。
* 现在支持[SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference) ，并且可以通过[SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)检索当前阶段。 此外，还可以通过 SpatialStageFrameOfReference 请求新阶段 [。 RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)。
* 在以前的版本中，通过全息远程处理播放机在播放机上处理 "提出预测"。 从版本2.2.0 开始，全息远程处理具有时间同步，并由远程应用程序完全完成预测。 在出现困难的网络情况下，用户还应预计提高的全息影像稳定性。

## <a name="version-213-may-25-2020"></a>版本 2.1.3 (5 月25日 2020) <a name="v2.1.3"></a>

* 已更改 [HolographicSpace](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) 事件的行为。 在以前的版本中，**无法** 保证添加的 [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera)在通过 [HolographicSpace](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe)创建下一帧时还具有有效的 [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) 。 从版本2.1.3 开始， [HolographicSpace](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) 与来自全息远程处理播放机的姿势数据同步。 当添加照相机时，用户可能会发现，在下一帧上还可以使用该相机的有效 [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) 。
* 已将 **禁用** 添加到 DepthBufferStreamResolution，这可用于通过 RemoteContext.ConfigureDepthVideoStream 禁用深度缓冲区流式处理。 请注意，如果使用的 [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) 将失败，并 *E_ILLEGAL_METHOD_CALL*。
* 全息远程处理播放机的启动屏幕经过重新设计，现在不会阻止 "用户" 视图。
* 稳定性改进和 bug 修复。

## <a name="version-212-april-5-2020"></a>版本 2.1.2 (2020 年4月5日) <a name="v2.1.2"></a>

* 修复了最新的全息远程处理播放器与使用小于2.1.0 的版本的远程应用之间的音频向后兼容性问题。
* 固定空间锚定问题，意外地关闭了全息远程处理播放器。 此问题还会影响自定义播放机。

## <a name="version-211-march-20-2020"></a>版本 2.1.1 (2020 年3月20日) <a name="v2.1.1"></a>

* 修复了使用 AMD Gpu 时远程应用的视频编码问题。
* 全息远程处理播放器性能改进。

## <a name="version-210-march-11-2020"></a>版本 2.1.0 (2020 年3月11日) <a name="v2.1.0"></a>

* 已将网络传输切换为使用 [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP。 安全连接现在使用 [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) 。 请注意， [全息远程处理播放器](holographic-remoting-player.md) 仍与所有以前版本的全息远程处理版本兼容。 若要从新的网络传输中获益，全息远程处理播放器和有问题的远程应用必须使用版本2.1.0。
* 添加了对 [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)的支持。 

## <a name="version-2020-february-2-2020"></a>版本 2.0.20 (2020 年2月2日) <a name="v2.0.20"></a>

* 修复了导致崩溃的各种 bug。

## <a name="version-2018-december-17-2019"></a>版本 2.0.18 (2019 年 12 月 17 日) <a name="v2.0.18"></a>

* 添加了对 [HolographicViewConfiguration 的支持](/uwp/api/windows.graphics.holographic.holographicviewconfiguration)
* 修复了导致崩溃的各种 bug。
* 修复了以下 bug：HolographicCamera 需要 HolographicSpace.CameraAdded 回调才能被接受，并作为已添加的相机显示在 HolographicFrame 中。

## <a name="version-2016-november-11-2019"></a>版本 2.0.16 (2019 年 11 月 11 日) <a name="2.0.16"></a>

* 修复了 QR 代码跟踪中的死锁。
* 修复了由于主线程中的阻塞等待而未处理异常。

## <a name="version-2014-october-26-2019"></a>版本 2.0.14 (2019 年 10 月 26 日) <a name="v2.0.14"></a>

* 支持新的 PerceptionDevice API (Windows 10 2019 年 11 月更新) 。
* 修复了阻止 SpatialGestureRecognizer 触发手势事件的问题。
* 修复了使用 SpatialSurfaceObserver.SetBoundingVolume 时出现线程问题。

## <a name="version-2012-october-18-2019"></a>版本 2.0.12 (2019 年 10 月 18 日) <a name="v2.0.12"></a>

* 修复了使用 NavigationRail x/Y/Z (时 SpatialGestureRecognizer 中的) 。

## <a name="version-2010-october-10-2019"></a>版本 2.0.10 (2019 年 10 月 10 日) <a name="v2.0.10"></a>

* 修复了使用 VR 控制器的触发器按钮时崩溃的问题。 全息远程处理不完全支持控制器，如果与 Windows HoloLens 2 按钮配对，则只有触发器按钮和 Windows。

## <a name="version-209-september-19-2019"></a>版本 2.0.9 (2019 年 9 月 19 日) <a name="v2.0.9"></a>

* 添加了对 [SpatialAnchorExporter 的支持](/uwp/api/windows.perception.spatial.spatialanchorexporter)
* 添加了由 (```IPlayerContext2``` 实现的新 ```PlayerContext```) 提供以下成员：
  - [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  属性。
* 向 ```Failed_RemoteFrameTooOld``` 添加了值 ```BlitResult```
* 稳定性和可靠性改进

## <a name="version-208-august-20-2019"></a>版本 2.0.8 (2019 年 8 月 20 日) <a name="v2.0.8"></a>

* 修复了使用[IDXGISurface2](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2)作为参数调用[HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)时出现崩溃的问题。
* 稳定性和可靠性改进

## <a name="version-207-july-26-2019"></a>版本 2.0.7 (2019 年 7 月 26 日) <a name="v2.0.7"></a>

* 适用于 HoloLens 2 的全息远程处理的第一个公共HoloLens 2。

## <a name="see-also"></a>另请参阅

* [使用远程 API 编写全息远程Windows Mixed Reality应用](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR API 编写全息远程处理远程应用](holographic-remoting-create-remote-openxr.md)
* [编写自定义全息远程处理播放器应用](holographic-remoting-create-player.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)