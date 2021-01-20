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
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="19d85-104">全息远程处理疑难解答</span><span class="sxs-lookup"><span data-stu-id="19d85-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="19d85-105">本指南特定于 HoloLens 2 上的全息远程处理。</span><span class="sxs-lookup"><span data-stu-id="19d85-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="19d85-106">找不到 Spectre 缓解的库。</span><span class="sxs-lookup"><span data-stu-id="19d85-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="19d85-107">全息远程处理示例应用在发布配置中启用了 Spectre 缓解 (/Qspectre) 。</span><span class="sxs-lookup"><span data-stu-id="19d85-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="19d85-108">如果你的 *vccorlib.h 无法打开* 错误，请确保你的 Visual Studio 工作负荷包含 [Spectre 缓解的库](/cpp/build/reference/qspectre)</span><span class="sxs-lookup"><span data-stu-id="19d85-108">If you get the *vccorlib.lib cannot be opened* fatal error, make sure that your Visual Studio Workload includes the [Spectre mitigated libraries](/cpp/build/reference/qspectre)</span></span>

## <a name="speech"></a><span data-ttu-id="19d85-109">语音</span><span class="sxs-lookup"><span data-stu-id="19d85-109">Speech</span></span>

<span data-ttu-id="19d85-110">全息远程处理播放机支持诊断覆盖，可以通过口述 ```Enable Diagnostics``` 和禁用来启用 ```Disable Diagnostics``` 。</span><span class="sxs-lookup"><span data-stu-id="19d85-110">The Holographic Remoting Player supports a diagnostics overlay, which can be enabled by saying ```Enable Diagnostics``` and disabled by saying ```Disable Diagnostics```.</span></span> <span data-ttu-id="19d85-111">如果使用这些声音命令时遇到问题，也可以通过 web 浏览器使用作为 URL 来启动全息远程处理播放器 ```ms-holographic-remoting:?stats``` 。</span><span class="sxs-lookup"><span data-stu-id="19d85-111">If you have trouble with these voice commands, you can also launch the Holographic Remoting player via a web browser using ```ms-holographic-remoting:?stats``` as a URL.</span></span>

## <a name="h265-video-codec-not-available"></a><span data-ttu-id="19d85-112">H265 视频编解码器不可用</span><span class="sxs-lookup"><span data-stu-id="19d85-112">H265 video codec not available</span></span>

<span data-ttu-id="19d85-113">在远程应用中使用 H265 视频编解码器时，安装 [HEVC 视频扩展](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) 。</span><span class="sxs-lookup"><span data-stu-id="19d85-113">Install the [HEVC Video Extensions](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) when using H265 video codec in your remote app.</span></span> <span data-ttu-id="19d85-114">如果遇到安装了编解码器但无法使用的问题，请查看 [故障排除](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) 指南。</span><span class="sxs-lookup"><span data-stu-id="19d85-114">If you run into issues where the codec is installed but can't be used, check out [troubleshooting](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) guide.</span></span>

## <a name="limitations"></a><span data-ttu-id="19d85-115">限制</span><span class="sxs-lookup"><span data-stu-id="19d85-115">Limitations</span></span>

<span data-ttu-id="19d85-116">使用 HoloLens 2 的全息远程处理时，当前 **不** 支持以下 api，除非另有说明，否则将引发 ```ERROR_NOT_SUPPORTED``` 错误：</span><span class="sxs-lookup"><span data-stu-id="19d85-116">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raise an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="19d85-117">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="19d85-117">Windows.Graphics.Holographic</span></span>](/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="19d85-118">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="19d85-118">HolographicCamera.ViewConfiguration</span></span>](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="19d85-119">支持从版本[2.0.18](holographic-remoting-version-history.md#v2.0.18)开始</span><span class="sxs-lookup"><span data-stu-id="19d85-119">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="19d85-120">在以前的版本中，始终会引发错误。</span><span class="sxs-lookup"><span data-stu-id="19d85-120">On previous versions always raise an error.</span></span>
* [<span data-ttu-id="19d85-121">HolographicCamera.IsHardwareContentProtectionEnabled</span><span class="sxs-lookup"><span data-stu-id="19d85-121">HolographicCamera.IsHardwareContentProtectionEnabled</span></span>](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [<span data-ttu-id="19d85-122">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="19d85-122">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="19d85-123">支持从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始</span><span class="sxs-lookup"><span data-stu-id="19d85-123">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="19d85-124">在以前的版本中不会失败，但不会更改呈现目标大小。</span><span class="sxs-lookup"><span data-stu-id="19d85-124">On previous versions don't fail, but the render target size won't be changed.</span></span>
* [<span data-ttu-id="19d85-125">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="19d85-125">HolographicCameraPose.OverrideProjectionTransform</span></span>](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="19d85-126">HolographicCameraPose.OverrideViewport</span><span class="sxs-lookup"><span data-stu-id="19d85-126">HolographicCameraPose.OverrideViewport</span></span>](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="19d85-127">HolographicCameraPose.OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="19d85-127">HolographicCameraPose.OverrideViewTransform</span></span>](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - <span data-ttu-id="19d85-128">支持从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始</span><span class="sxs-lookup"><span data-stu-id="19d85-128">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="19d85-129">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="19d85-129">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="19d85-130">Doe.</span><span class="sxs-lookup"><span data-stu-id="19d85-130">Doe.</span></span>
  - <span data-ttu-id="19d85-131">支持从版本[2.1.0](holographic-remoting-version-history.md#v2.1.0)开始</span><span class="sxs-lookup"><span data-stu-id="19d85-131">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="19d85-132">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="19d85-132">HolographicDisplay.TryGetViewConfiguration</span></span>](/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="19d85-133">查询 HolographicViewConfigurationKind PhotoVideoCamera 将始终返回 ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="19d85-133">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="19d85-134">支持从版本[2.0.18](holographic-remoting-version-history.md#v2.0.18)开始</span><span class="sxs-lookup"><span data-stu-id="19d85-134">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="19d85-135">在以前的版本中，始终会引发错误。</span><span class="sxs-lookup"><span data-stu-id="19d85-135">On previous versions always raise an error.</span></span>
* [<span data-ttu-id="19d85-136">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="19d85-136">HolographicSpace.CreateFramePresentationMonitor</span></span>](/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="19d85-137">HolographicDisplay. Adaptivesourcemanager.getdefault</span><span class="sxs-lookup"><span data-stu-id="19d85-137">HolographicDisplay.GetDefault</span></span>](/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="19d85-138">如果在建立连接之前调用，将报告错误。</span><span class="sxs-lookup"><span data-stu-id="19d85-138">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="19d85-139">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="19d85-139">Windows.Perception.Spatial</span></span>](/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="19d85-140">SpatialLocation. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="19d85-140">SpatialLocation.AbsoluteAngularAcceleration</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="19d85-141">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="19d85-141">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="19d85-142">SpatialLocation. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="19d85-142">SpatialLocation.AbsoluteAngularVelocity</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="19d85-143">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="19d85-143">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="19d85-144">SpatialLocation. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="19d85-144">SpatialLocation.AbsoluteLinearAcceleration</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="19d85-145">SpatialLocation. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="19d85-145">SpatialLocation.AbsoluteLinearVelocity</span></span>](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="19d85-146">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="19d85-146">SpatialStageFrameOfReference.Current</span></span>](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="19d85-147">支持从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始</span><span class="sxs-lookup"><span data-stu-id="19d85-147">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="19d85-148">在以前的版本中 ```nullptr``` ，始终返回。</span><span class="sxs-lookup"><span data-stu-id="19d85-148">On previous versions always return ```nullptr```.</span></span>
* [<span data-ttu-id="19d85-149">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="19d85-149">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - <span data-ttu-id="19d85-150">支持从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始</span><span class="sxs-lookup"><span data-stu-id="19d85-150">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="19d85-151">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="19d85-151">SpatialAnchor.RemovedByUser</span></span>](/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="19d85-152">SpatialAnchorExporter.GetDefault</span><span class="sxs-lookup"><span data-stu-id="19d85-152">SpatialAnchorExporter.GetDefault</span></span>](/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="19d85-153">从版本 [2.0.9](holographic-remoting-version-history.md#v2.0.9)开始支持。</span><span class="sxs-lookup"><span data-stu-id="19d85-153">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="19d85-154">在以前的版本中 ```nullptr``` ，始终返回。</span><span class="sxs-lookup"><span data-stu-id="19d85-154">On previous versions always return ```nullptr```.</span></span> 
* [<span data-ttu-id="19d85-155">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="19d85-155">SpatialAnchorExporter.RequestAccessAsync</span></span>](/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="19d85-156">从版本 [2.0.9](holographic-remoting-version-history.md#v2.0.9)开始支持。</span><span class="sxs-lookup"><span data-stu-id="19d85-156">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="19d85-157">在以前的版本中，异步操作始终以完成 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。</span><span class="sxs-lookup"><span data-stu-id="19d85-157">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="19d85-158">SpatialAnchorTransferManager.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="19d85-158">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="19d85-159">异步操作始终以结束 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。</span><span class="sxs-lookup"><span data-stu-id="19d85-159">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="19d85-160">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="19d85-160">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="19d85-161">异步操作始终以结束 ```false``` 。</span><span class="sxs-lookup"><span data-stu-id="19d85-161">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="19d85-162">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="19d85-162">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="19d85-163">异步操作始终以结束 ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="19d85-163">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="19d85-164">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="19d85-164">Windows.UI.Input.Spatial</span></span>](/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="19d85-165">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="19d85-165">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="19d85-166">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="19d85-166">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [<span data-ttu-id="19d85-167">SpatialInteractionSource</span><span class="sxs-lookup"><span data-stu-id="19d85-167">SpatialInteractionSource.Controller</span></span>](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - <span data-ttu-id="19d85-168">支持从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始</span><span class="sxs-lookup"><span data-stu-id="19d85-168">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>

[<span data-ttu-id="19d85-169">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="19d85-169">Windows.Perception.Spatial.Preview</span></span>](/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="19d85-170">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="19d85-170">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="19d85-171">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="19d85-171">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a><span data-ttu-id="19d85-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19d85-172">See Also</span></span>
* [<span data-ttu-id="19d85-173">全息远程处理版本历史记录</span><span class="sxs-lookup"><span data-stu-id="19d85-173">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="19d85-174">使用 Windows Mixed Reality Api 编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="19d85-174">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="19d85-175">使用 OpenXR Api 编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="19d85-175">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="19d85-176">编写自定义全息远程处理播放器应用</span><span class="sxs-lookup"><span data-stu-id="19d85-176">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="19d85-177">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="19d85-177">Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="19d85-178">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="19d85-178">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)