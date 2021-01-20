---
title: 全息远程处理故障排除和限制
description: 在 HoloLens 2 设备上查找全息远程处理功能的疑难解答资源和说明。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality，全息影像，全息远程处理，远程渲染，网络渲染，HoloLens，远程影像，故障排除，帮助，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: 429ca7364d82e1713af059aa3c6da01852283120
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583836"
---
# <a name="holographic-remoting-troubleshooting"></a>全息远程处理疑难解答

> [!IMPORTANT]
> 本指南特定于 HoloLens 2 上的全息远程处理。

## <a name="spectre-mitigated-libraries-not-found"></a>找不到 Spectre 缓解的库。

全息远程处理示例应用在发布配置中启用了 Spectre 缓解 (/Qspectre) 。

如果你的 *vccorlib.h 无法打开* 错误，请确保你的 Visual Studio 工作负荷包含 [Spectre 缓解的库](/cpp/build/reference/qspectre)

## <a name="speech"></a>语音

全息远程处理播放机支持诊断覆盖，可以通过口述 ```Enable Diagnostics``` 和禁用来启用 ```Disable Diagnostics``` 。 如果使用这些声音命令时遇到问题，也可以通过 web 浏览器使用作为 URL 来启动全息远程处理播放器 ```ms-holographic-remoting:?stats``` 。

## <a name="h265-video-codec-not-available"></a>H265 视频编解码器不可用

在远程应用中使用 H265 视频编解码器时，安装 [HEVC 视频扩展](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) 。 如果遇到安装了编解码器但无法使用的问题，请查看 [故障排除](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) 指南。

## <a name="limitations"></a>限制

使用 HoloLens 2 的全息远程处理时，当前 **不** 支持以下 api，除非另有说明，否则将引发 ```ERROR_NOT_SUPPORTED``` 错误：

[Windows.Graphics.Holographic](/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - 支持从版本[2.0.18](holographic-remoting-version-history.md#v2.0.18)开始
  - 在以前的版本中，始终会引发错误。
* [HolographicCamera.IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - 支持从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始
  - 在以前的版本中不会失败，但不会更改呈现目标大小。
* [HolographicCameraPose.OverrideProjectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose.OverrideViewport](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose.OverrideViewTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - 支持从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - Doe.
  - 支持从版本[2.1.0](holographic-remoting-version-history.md#v2.1.0)开始
* [HolographicDisplay.TryGetViewConfiguration](/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - 查询 HolographicViewConfigurationKind PhotoVideoCamera 将始终返回 ```nullptr``` 。
  - 支持从版本[2.0.18](holographic-remoting-version-history.md#v2.0.18)开始
  - 在以前的版本中，始终会引发错误。
* [HolographicSpace.CreateFramePresentationMonitor](/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay. Adaptivesourcemanager.getdefault](/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - 如果在建立连接之前调用，将报告错误。


[Windows.Perception.Spatial](/uwp/api/windows.perception.spatial)

* [SpatialLocation. AbsoluteAngularAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. AbsoluteAngularVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. AbsoluteLinearAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. AbsoluteLinearVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - 支持从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始
  - 在以前的版本中 ```nullptr``` ，始终返回。
* [SpatialStageFrameOfReference.RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - 支持从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始
* [SpatialAnchor.RemovedByUser](/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - 从版本 [2.0.9](holographic-remoting-version-history.md#v2.0.9)开始支持。 
  - 在以前的版本中 ```nullptr``` ，始终返回。 
* [SpatialAnchorExporter.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - 从版本 [2.0.9](holographic-remoting-version-history.md#v2.0.9)开始支持。 
  - 在以前的版本中，异步操作始终以完成 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。
* [SpatialAnchorTransferManager.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - 异步操作始终以结束 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - 异步操作始终以结束 ```false``` 。
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - 异步操作始终以结束 ```nullptr``` 。

[Windows.UI.Input.Spatial](/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [SpatialInteractionSource](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - 支持从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始

[Windows.Perception.Spatial.Preview](/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>另请参阅
* [全息远程处理版本历史记录](holographic-remoting-version-history.md)
* [使用 Windows Mixed Reality Api 编写全息远程处理远程应用](holographic-remoting-create-remote-wmr.md)
* [使用 OpenXR Api 编写全息远程处理远程应用](holographic-remoting-create-remote-openxr.md)
* [编写自定义全息远程处理播放器应用](holographic-remoting-create-player.md)
* [全息远程处理软件许可条款](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)