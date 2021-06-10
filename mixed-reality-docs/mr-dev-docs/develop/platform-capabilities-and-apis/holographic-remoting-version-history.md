---
title: 全息远程处理版本历史记录
description: 随时了解适用于 HoloLens 2 的全息远程处理功能的版本历史记录。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 06/10/2021
ms.topic: article
keywords: HoloLens， 远程处理， 全息远程处理， 版本历史记录， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
ms.openlocfilehash: dae7bc0dac792cbe1a8472415d5e9fa34532e918
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908220"
---
# <a name="holographic-remoting-version-history"></a>全息远程处理版本历史记录

> [!IMPORTANT]
> 本指南特定于全息远程处理HoloLens 2。

## <a name="version-260-june-10-2021"></a>版本 2.6.0 (2021 年 6 月 10 日) <a name="v2.6.0"></a>
* 使用 OpenXR API 的全息远程处理现在支持：
  * 新的 XR_MSFT_holographic_remoting_speech 扩展，允许应用程序侦听各种语言的自定义语音命令。
  * XR_MSFT_scene_understanding扩展，为应用程序提供用户环境中平面、网格和对象的结构化高级表示形式，从而可以开发空间感知应用程序。 但是，请注意，XR_SCENE_COMPUTE_CONSISTENCY_OCCLUSION_OPTIMIZED_MSFT xrComputeNewSceneMSFT 支持的唯一一致性。
  * 此XR_MSFT_spatial_graph_bridge扩展，允许应用程序创建 XrSpace 句柄，以跟踪设备平台库或 API Windows Mixed Reality空间图节点。 但是，请注意，XR_SPATIAL_GRAPH_NODE_TYPE_STATIC_MSFT xrCreateSpatialGraphNodeSpaceMSFT 支持的唯一节点类型。 
* 使用混合现实 API 的全息远程处理现在支持：
  * SpatialGraphInteropPreview.CreateCoordinateSystemForNode 重载，使应用程序能够跟踪静态空间图形节点，以便用户可以推理其环境中的位置和事物。
* 使用 OpenXR 和混合现实 API 的全息远程处理现在支持：
  * Microsoft.MixedReality.SceneUnder一 SDK，它允许应用程序计算用户 (周围的场景的说明，如墙、楼层和表面) 提供四边形、网格和内容放置提示。
  * Microsoft.MixedReality.QR SDK，它允许应用程序跟踪检测到的 QR 码的位置、大小和内容。
* OpenXR 远程示例已更新为包括： 
  * 使用扩展插件XR_MSFT_holographic_remoting_speech示例。
* 混合现实远程示例已更新为包括：  
  * 使用 Microsoft.MixedReality.SceneUnder一 SDK 的示例。
  * 使用 Microsoft.MixedReality.QR SDK (替换了以前的 QR 代码检测机制的) 。
* 在建立连接时，全息远程处理播放器现在会显示加载动画。
* 修复了 OpenXR API 运行时和混合现实 API 示例中 RenderDoc 兼容性的问题。
* 各种 bug 修复和稳定性改进。

## <a name="version-250-february-12-2021"></a>版本 2.5.0 (2021 年 2 月 12 日) <a name="v2.5.0"></a>
* 使用 [OpenXR API](../native/openxr.md) 的全息远程处理现在支持：
  * XR_MSFT_spatial_anchor扩展。 此扩展允许应用程序创建空间定位点，这些定位点是用户物理环境中由运行时跟踪的任意自由空间点。
  * XR_MSFT_controller_model扩展。 此扩展提供了一种机制，用于加载控制器的 GLTF 模型。
  * 自定义数据通道作为扩展插件的一XR_MSFT_holographic_remoting部分。 OpenXR 远程示例 [中显示的 示例](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)。
* 改进了播放器和远程端之间的同步。 这允许动态更改姿势和帧缓冲，确保远程渲染的内容以预期的目标帧速率顺利到达显示器。
* 改进了通过远程处理设备提供的全息远程处理Microsoft Store。 在HoloLens 2播放器现在以每秒 60 帧的速度稳定运行。
* 空间图面网格的优化传输，远程应用可通过 [SpatialSurfaceObserver](/uwp/api/windows.perception.spatial.surfaces.spatialsurfaceobserver) 查询这些网格。
* 修复了调用 SpatialAnchorManager 方法或释放定位点导致断开连接时出现异常的问题。
* 修复了关闭 PlayerContext 或 RemoteContext 实例时导致崩溃的线程问题。
* 桌面上的全息远程处理播放器：在未安装Windows Mixed Reality时显示错误消息，而不是以无提示方式关闭。
* 其他许多 bug 修复和稳定性改进。

## <a name="version-241-january-22-2021"></a>版本 2.4.1 (2021 年 1 月 22 日) <a name="v2.4.1"></a>

* 修复了在连接时调用 SpatialAnchorManager：：RequestStoreAsync 时无法可靠地工作的问题。
* 修复了在定位点不可定位时 SpatialAnchorManager：：TrySave 无法正确保存定位点的问题。

## <a name="version-240-december-1-2020"></a>版本 2.4.0 (2020 年 12 月 1 日) <a name="v2.4.0"></a>

* 全息远程处理现在支持使用 [OpenXR API 编写远程应用](../native/openxr.md)。 若要开始，请查看使用 [OpenXR](holographic-remoting-create-remote-openxr.md) API 编写全息远程处理远程应用。
* Bug 修复和稳定性改进。

## <a name="version-231-october-10-2020"></a>版本 2.3.1 (2020 年 10 月 10 日) <a name="v2.3.1"></a>

* 修复了远程姿势预测的回归，该预测导致视觉抖动。
* 实现了 PerceptionDeviceSetCreateFactoryOverride，PerceptionDevice.dll全息远程处理附带的版本不会干扰 Windows 10。

## <a name="version-230-october-2-2020"></a>版本 2.3.0 (2020 年 10 月 2 日) <a name="v2.3.0"></a>

* 修复了在全息远程处理播放器挂起时可能发生的崩溃。
* 稳定性改进。

## <a name="version-223-august-28-2020"></a>版本 2.2.3 (2020 年 8 月 28 日) <a name="v2.2.3"></a>

* Bug 修复和稳定性改进。

## <a name="version-222-july-10-2020"></a>版本 2.2.2 (2020 年 7 月 10 日) <a name="v2.2.2"></a>

* 修复了从头戴显示设备流式传输时 [HolographicCamera.LeftViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) 和 [HolographicCamera.RightViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) 不返回任何隐藏区域网格顶点Windows Mixed Reality的问题。
* 修复了网络连接不佳时可能发生的故障。

## <a name="version-221-july-6-2020"></a>版本 2.2.1 (2020 年 7 月 6 日) <a name="v2.2.1"></a>

> [!IMPORTANT]
> [Windows 应用认证工具包](https://developer.microsoft.com/windows/downloads/app-certification-kit/) 版本 [2.2.0 的验证](holographic-remoting-version-history.md#v2.2.0) 将失败。 如果你使用版本 [2.2.0，](holographic-remoting-version-history.md#v2.2.0) 并且想要将应用程序提交到更新到至少版本 2.2.1 的 Microsoft store p 租约。
* 修复 [Windows 应用认证工具包](https://developer.microsoft.com/windows/downloads/app-certification-kit/) 合规性问题。

## <a name="version-220-july-1-2020"></a>版本 2.2.0 (2020 年 7 月 1 日) <a name="v2.2.0"></a>

* 全息远程处理播放器现在可以安装在运行 Windows Mixed Reality 的 PC 上[](../../discover/navigating-the-windows-mixed-reality-home.md)，从而可以流式传输到沉浸式头戴显示设备。
* [全息](../../design/motion-controllers.md) 远程处理现在支持运动控制器，控制器特定的数据可以通过 [SpatialInteractionSource.Controller 检索](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)。
* [现在支持 SpatialStageFrameOfReference，](/uwp/api/windows.perception.spatial.spatialstageframeofreference) 可通过 [SpatialStageFrameOfReference.Current 检索当前阶段](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)。 此外，可以通过 [SpatialStageFrameOfReference.RequestNewStageAsync 请求新阶段](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)。
* 在早期版本中，全息远程处理播放器在播放器端处理了姿势预测。 从版本 2.2.0 开始，全息远程处理具有时间同步，预测由远程应用程序完全完成。 用户还应期望在困难网络情况下提高全息影像稳定性。

## <a name="version-213-may-25-2020"></a>版本 2.1.3 (2020 年 5 月 25 日) <a name="v2.1.3"></a>

* 更改了 [HolographicSpace.CameraAdded 事件](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) 的行为。 在早期版本中，不保证添加的[HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera)在通过[HolographicSpace.CreateNextFrame](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe)创建下一帧时也具有有效的[HolographicCameraPose。](/uwp/api/windows.graphics.holographic.holographiccamerapose) 从版本 2.1.3 开始 [，HolographicSpace.CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) 与来自全息远程播放器的姿势数据同步。 用户可以期望在添加相机时，下一帧中也会有一个有效的 [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) 可用于该相机。
* 向DepthBufferStreamResolution 添加了"已禁用"，可用于通过 ureDepthVideoStream RemoteContext.Config深度缓冲区流。 请注意，如果使用 [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer，E_ILLEGAL_METHOD_CALL。](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)
* 全息远程处理播放器的启动屏幕已重新设计，现在不会阻止用户视图。
* 稳定性改进和 bug 修复。

## <a name="version-212-april-5-2020"></a>版本 2.1.2 (2020 年 4 月 5 日) <a name="v2.1.2"></a>

* 修复了最新的全息远程处理播放器与使用低于 2.1.0 版本的远程应用之间的音频向后兼容性问题。
* 修复了空间定位点问题，该问题意外关闭了全息远程处理播放器。 此问题还会影响自定义播放器。

## <a name="version-211-march-20-2020"></a>版本 2.1.1 (2020 年 3 月 20 日) <a name="v2.1.1"></a>

* 修复了使用 AMD GPU 时远程应用的视频编码问题。
* 全息远程处理播放器性能改进。

## <a name="version-210-march-11-2020"></a>版本 2.1.0 (2020 年 3 月 11 日) <a name="v2.1.0"></a>

* 切换网络传输以通过 [UDP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) 使用 RTP。 安全连接现在[使用 SRTP。](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) 请注意， [全息远程处理播放器](holographic-remoting-player.md) 仍与所有以前发布的全息远程处理版本兼容。 为了同时受益于新的网络传输，全息远程处理播放器和远程应用必须使用版本 2.1.0。
* 添加了对 [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer 的支持](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)。 

## <a name="version-2020-february-2-2020"></a>版本 2.0.20 (2020 年 2 月 2 日) <a name="v2.0.20"></a>

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

* 修复了使用 VR 控制器的触发器按钮时崩溃的问题。 全息远程处理不完全支持控制器，只有触发器按钮和 Windows 按钮与 HoloLens 2。

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