---
title: 全息远程处理故障排除和限制
description: 在远程设备上查找全息远程处理功能HoloLens 2说明。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality、全息影像、全息远程处理、远程渲染、网络渲染、HoloLens、远程全息影像、故障排除、帮助、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备
ms.openlocfilehash: d49f73f4cbe205e71cb2f76ab02769ddad5f3ed2
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184608"
---
# <a name="holographic-remoting-troubleshooting"></a>全息远程处理故障排除

> [!IMPORTANT]
> 本指南特定于全息远程处理HoloLens 2。

## <a name="spectre-mitigated-libraries-not-found"></a>找不到 Spectre 缓解库。

全息远程处理示例应用在发布配置中 (/Qspectre) Spectre 缓解功能。

如果收到 *vccorlib.lib* 无法打开的致命错误，请确保Visual Studio工作负荷包含 [Spectre 缓解库](/cpp/build/reference/qspectre)

## <a name="speech"></a>语音

全息远程处理播放器支持诊断覆盖，可以通过说 来启用诊断覆盖，通过说 来 ```Enable Diagnostics``` 禁用 ```Disable Diagnostics``` 它。 如果使用这些语音命令时遇到问题，还可使用 作为 URL 通过 Web 浏览器启动全息 ```ms-holographic-remoting:?stats``` 远程处理播放器。

## <a name="h265-video-codec-not-available"></a>H265 视频编解码器不可用

在远程[HEVC 视频扩展](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7)H265 视频编解码器时安装该编码器。 如果遇到安装编解码器但无法使用的问题，请查看 [故障排除](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) 指南。

## <a name="limitations"></a>限制

使用全息远程处理进行远程处理时，当前不支持以下 API HoloLens 2除非另有说明，否则将 ```ERROR_NOT_SUPPORTED``` 引发错误：

[Windows.Graphics.Holographic](/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - 从版本 [2.0.18 开始支持](holographic-remoting-version-history.md#v2.0.18)
  - 在早期版本上，始终引发错误。
* [HolographicCamera.IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - 从版本 [2.2.0 开始支持](holographic-remoting-version-history.md#v2.2.0)
  - 在以前的版本中不会失败，但呈现器目标大小不会更改。
* [HolographicCameraPose.OverrideProjectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose.OverrideViewport](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose.OverrideViewTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - 从版本 [2.2.0 开始支持](holographic-remoting-version-history.md#v2.2.0)
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - 能源部。
  - 从版本 [2.1.0 开始支持](holographic-remoting-version-history.md#v2.1.0)
* [HolographicDisplay.TryGetViewConfiguration](/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - 查询 HolographicViewConfigurationKind.PhotoVideoCamera 将始终返回 ```nullptr``` 。
  - 从版本 [2.0.18 开始支持](holographic-remoting-version-history.md#v2.0.18)
  - 在早期版本上，始终引发错误。
* [HolographicSpace.CreateFramePresentationMonitor](/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay.GetDefault](/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - 如果在建立连接之前调用 ，将报告错误。


[Windows.Perception.Spatial](/uwp/api/windows.perception.spatial)

* [SpatialLocation.AbsoluteAngularAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation.AbsoluteAngularVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation.AbsoluteLinearAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation.AbsoluteLinearVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference.Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - 从版本 [2.2.0 开始支持](holographic-remoting-version-history.md#v2.2.0)
  - 在以前的版本中，始终返回 ```nullptr``` 。
* [SpatialStageFrameOfReference.RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - 从版本 [2.2.0 开始支持](holographic-remoting-version-history.md#v2.2.0)
* [SpatialAnchor.RemovedByUser](/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - 从版本 [2.0.9 开始受支持](holographic-remoting-version-history.md#v2.0.9)。 
  - 在以前的版本中，始终返回 ```nullptr``` 。 
* [SpatialAnchorExporter.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - 从版本 [2.0.9 开始受支持](holographic-remoting-version-history.md#v2.0.9)。 
  - 在早期版本上，异步操作始终使用 完成 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。
* [SpatialAnchorTransferManager.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - 异步操作始终使用 完成 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - 异步操作始终使用 完成 ```false``` 。
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - 异步操作始终使用 完成 ```nullptr``` 。

[Windows.UI.Input.Spatial](/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [SpatialInteractionSource.Controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - 从版本 [2.2.0 开始支持](holographic-remoting-version-history.md#v2.2.0)

[Windows.Perception.Spatial.Preview](/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>另请参阅
* [全息远程处理概述](holographic-remoting-overview.md)
* [全息远程处理版本历史记录](holographic-remoting-version-history.md)
* [使用远程 API 编写全息远程Windows Mixed Reality应用](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR API 编写全息远程处理远程应用](holographic-remoting-create-remote-openxr.md)
* [编写自定义全息远程处理播放器应用](holographic-remoting-create-player.md)
* [全息远程处理软件许可条款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)