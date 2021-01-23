---
title: 全息远程处理版本历史记录
description: 随时了解 HoloLens 2 的全息远程处理功能的版本历史记录。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens，远程处理，全息远程处理，版本历史记录，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: e1f80d0d2cbd02b78ed07e3ec60825ffe1059309
ms.sourcegitcommit: 3dad2adfdb5bdb8100d8d864f7845e34a3ef912d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699006"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="7c64c-104">全息远程处理版本历史记录</span><span class="sxs-lookup"><span data-stu-id="7c64c-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7c64c-105">本指南特定于 HoloLens 2 上的全息远程处理。</span><span class="sxs-lookup"><span data-stu-id="7c64c-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="version-241-january-22-2021"></a><span data-ttu-id="7c64c-106">版本 2.4.1 (2021 年1月22日) <a name="v2.4.1"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-106">Version 2.4.1 (January 22, 2021) <a name="v2.4.1"></a></span></span>

* <span data-ttu-id="7c64c-107">修复了在连接时调用时 SpatialAnchorManager：： RequestStoreAsync 无法可靠工作的问题。</span><span class="sxs-lookup"><span data-stu-id="7c64c-107">Fixed issue with SpatialAnchorManager::RequestStoreAsync not working reliably when called while connecting.</span></span>
* <span data-ttu-id="7c64c-108">修复了 SpatialAnchorManager：： TrySave 无法正确保存定位点的问题。</span><span class="sxs-lookup"><span data-stu-id="7c64c-108">Fixed issue with SpatialAnchorManager::TrySave not correctly saving an anchor if anchor in question is not locatable.</span></span>

## <a name="version-240-december-1-2020"></a><span data-ttu-id="7c64c-109">版本 2.4.0 (2020 年12月1日) <a name="v2.4.0"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-109">Version 2.4.0 (December 1, 2020) <a name="v2.4.0"></a></span></span>

* <span data-ttu-id="7c64c-110">全息远程处理现在支持使用 [OPENXR API](../native/openxr.md)写入远程应用。</span><span class="sxs-lookup"><span data-stu-id="7c64c-110">Holographic Remoting now support writing remote apps using the [OpenXR API](../native/openxr.md).</span></span> <span data-ttu-id="7c64c-111">请参阅 [使用 OpenXR Api 编写全息远程处理远程应用](holographic-remoting-create-remote-openxr.md) ，开始使用。</span><span class="sxs-lookup"><span data-stu-id="7c64c-111">Check out [Writing a Holographic Remoting remote app using OpenXR APIs](holographic-remoting-create-remote-openxr.md) to get started.</span></span>
* <span data-ttu-id="7c64c-112">Bug 修复和稳定性改进。</span><span class="sxs-lookup"><span data-stu-id="7c64c-112">Bug fixes and stability improvements.</span></span>

## <a name="version-231-october-10-2020"></a><span data-ttu-id="7c64c-113">版本 2.3.1 (2020 年10月10日) <a name="v2.3.1"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-113">Version 2.3.1 (October 10, 2020) <a name="v2.3.1"></a></span></span>

* <span data-ttu-id="7c64c-114">通过远程姿势预测固定回归，导致视觉抖动。</span><span class="sxs-lookup"><span data-stu-id="7c64c-114">Fixed regression with remote pose prediction, which caused visual jitter.</span></span>
* <span data-ttu-id="7c64c-115">实现了 PerceptionDeviceSetCreateFactoryOverride，这确保了全息远程处理随附的 PerceptionDevice.dll 不会干扰 Windows 10 附带的版本。</span><span class="sxs-lookup"><span data-stu-id="7c64c-115">Implemented PerceptionDeviceSetCreateFactoryOverride, which ensures that PerceptionDevice.dll shipped with Holographic Remoting doesn't interfere with the version shipped with Windows 10.</span></span>

## <a name="version-230-october-2-2020"></a><span data-ttu-id="7c64c-116">版本 2.3.0 (10 月2日 2020) <a name="v2.3.0"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-116">Version 2.3.0 (October 2, 2020) <a name="v2.3.0"></a></span></span>

* <span data-ttu-id="7c64c-117">修复了在全息远程处理播放机挂起时可能发生的崩溃。</span><span class="sxs-lookup"><span data-stu-id="7c64c-117">Fixed crashes, which can happen when Holographic Remoting Player is suspended.</span></span>
* <span data-ttu-id="7c64c-118">稳定性改进。</span><span class="sxs-lookup"><span data-stu-id="7c64c-118">Stability improvements.</span></span>

## <a name="version-223-august-28-2020"></a><span data-ttu-id="7c64c-119">版本 2.2.3 (2020 年8月28日) <a name="v2.2.3"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-119">Version 2.2.3 (August 28, 2020) <a name="v2.2.3"></a></span></span>

* <span data-ttu-id="7c64c-120">Bug 修复和稳定性改进。</span><span class="sxs-lookup"><span data-stu-id="7c64c-120">Bug fixes and stability improvements.</span></span>

## <a name="version-222-july-10-2020"></a><span data-ttu-id="7c64c-121">版本 2.2.2 (2020 年7月10日) <a name="v2.2.2"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-121">Version 2.2.2 (July 10, 2020) <a name="v2.2.2"></a></span></span>

* <span data-ttu-id="7c64c-122">修复了从 Windows Mixed Reality 耳机流式传输时， [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) 和 [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) 的问题。</span><span class="sxs-lookup"><span data-stu-id="7c64c-122">Fixed issue with [HolographicCamera.LeftViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) and [HolographicCamera.RightViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) not returning any hidden area mesh vertices when streaming from a Windows Mixed Reality headset.</span></span>
* <span data-ttu-id="7c64c-123">修复了故障，这种情况可能会导致网络连接不佳。</span><span class="sxs-lookup"><span data-stu-id="7c64c-123">Fixed crash, which can happen with poor network connection.</span></span>

## <a name="version-221-july-6-2020"></a><span data-ttu-id="7c64c-124">版本 2.2.1 (7 月6日 2020) <a name="v2.2.1"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-124">Version 2.2.1 (July 6, 2020) <a name="v2.2.1"></a></span></span>

> [!IMPORTANT]
> <span data-ttu-id="7c64c-125">版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)的[Windows 应用程序认证包](https://developer.microsoft.com/windows/downloads/app-certification-kit/)验证将失败。</span><span class="sxs-lookup"><span data-stu-id="7c64c-125">[Windows App Certification Kit](https://developer.microsoft.com/windows/downloads/app-certification-kit/) validation with version [2.2.0](holographic-remoting-version-history.md#v2.2.0) will fail.</span></span> <span data-ttu-id="7c64c-126">如果你在版本 [2.2.0](holographic-remoting-version-history.md#v2.2.0) 上，并且想要将你的应用程序提交到 Microsoft store p 租约更新为至少版本2.2.1。</span><span class="sxs-lookup"><span data-stu-id="7c64c-126">In case you're on version [2.2.0](holographic-remoting-version-history.md#v2.2.0) and want to submit your application to the Microsoft store p lease updated to at least version 2.2.1.</span></span>
* <span data-ttu-id="7c64c-127">修复了 [Windows 应用程序认证包](https://developer.microsoft.com/windows/downloads/app-certification-kit/) 的相容性问题。</span><span class="sxs-lookup"><span data-stu-id="7c64c-127">Fixed [Windows App Certification Kit](https://developer.microsoft.com/windows/downloads/app-certification-kit/) compliance issues.</span></span>

## <a name="version-220-july-1-2020"></a><span data-ttu-id="7c64c-128">版本 2.2.0 (2020 年7月1日) <a name="v2.2.0"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-128">Version 2.2.0 (July 1, 2020) <a name="v2.2.0"></a></span></span>

* <span data-ttu-id="7c64c-129">全息远程处理播放器现在可以安装在运行 [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md)的 pc 上，使其可以流式传输到沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="7c64c-129">The Holographic Remoting player can now be installed on PCs running [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md), making it possible to stream to immersive headsets.</span></span>
* <span data-ttu-id="7c64c-130">[运动控制器](../../design/motion-controllers.md) 现在支持全息远程处理，并且可以通过 [SpatialInteractionSource](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)检索控制器特定的数据。</span><span class="sxs-lookup"><span data-stu-id="7c64c-130">[Motion controllers](../../design/motion-controllers.md) are now supported by Holographic Remoting and controller-specific data can be retrieved via [SpatialInteractionSource.Controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller).</span></span>
* <span data-ttu-id="7c64c-131">现在支持[SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference) ，并且可以通过[SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)检索当前阶段。</span><span class="sxs-lookup"><span data-stu-id="7c64c-131">[SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference) is now supported and the current stage can be retrieved via [SpatialStageFrameOfReference.Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current).</span></span> <span data-ttu-id="7c64c-132">此外，还可以通过 SpatialStageFrameOfReference 请求新阶段 [。 RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)。</span><span class="sxs-lookup"><span data-stu-id="7c64c-132">Also, a new stage can be requested via [SpatialStageFrameOfReference.RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync).</span></span>
* <span data-ttu-id="7c64c-133">在以前的版本中，通过全息远程处理播放机在播放机上处理 "提出预测"。</span><span class="sxs-lookup"><span data-stu-id="7c64c-133">In previous versions, pose prediction was handled on the player side by the Holographic Remoting player.</span></span> <span data-ttu-id="7c64c-134">从版本2.2.0 开始，全息远程处理具有时间同步，并由远程应用程序完全完成预测。</span><span class="sxs-lookup"><span data-stu-id="7c64c-134">Starting with version 2.2.0, Holographic Remoting has time synchronization, and prediction is fully done by the remote application.</span></span> <span data-ttu-id="7c64c-135">在出现困难的网络情况下，用户还应预计提高的全息影像稳定性。</span><span class="sxs-lookup"><span data-stu-id="7c64c-135">Users should also expect improved hologram stability under difficult network situations.</span></span>

## <a name="version-213-may-25-2020"></a><span data-ttu-id="7c64c-136">版本 2.1.3 (5 月25日 2020) <a name="v2.1.3"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-136">Version 2.1.3 (May 25, 2020) <a name="v2.1.3"></a></span></span>

* <span data-ttu-id="7c64c-137">已更改 [HolographicSpace](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) 事件的行为。</span><span class="sxs-lookup"><span data-stu-id="7c64c-137">Changed behavior of [HolographicSpace.CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) event.</span></span> <span data-ttu-id="7c64c-138">在以前的版本中，**无法** 保证添加的 [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera)在通过 [HolographicSpace](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe)创建下一帧时还具有有效的 [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) 。</span><span class="sxs-lookup"><span data-stu-id="7c64c-138">In previous versions, it was **not** guaranteed that an added [HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera) also has a valid [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) when creating the next frame via [HolographicSpace.CreateNextFrame](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe).</span></span> <span data-ttu-id="7c64c-139">从版本2.1.3 开始， [HolographicSpace](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) 与来自全息远程处理播放机的姿势数据同步。</span><span class="sxs-lookup"><span data-stu-id="7c64c-139">Starting with version 2.1.3, [HolographicSpace.CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) is synchronized with pose data coming from the Holographic Remoting Player.</span></span> <span data-ttu-id="7c64c-140">当添加照相机时，用户可能会发现，在下一帧上还可以使用该相机的有效 [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) 。</span><span class="sxs-lookup"><span data-stu-id="7c64c-140">Users can expect that when a camera is added there is also a valid [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) available for that camera on the next frame.</span></span>
* <span data-ttu-id="7c64c-141">已将 **禁用** 添加到 DepthBufferStreamResolution，这可用于通过 RemoteContext.ConfigureDepthVideoStream 禁用深度缓冲区流式处理。</span><span class="sxs-lookup"><span data-stu-id="7c64c-141">Added **Disabled** to DepthBufferStreamResolution, which can be used to disable depth buffer streaming via RemoteContext.ConfigureDepthVideoStream.</span></span> <span data-ttu-id="7c64c-142">请注意，如果使用的 [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) 将失败，并 *E_ILLEGAL_METHOD_CALL*。</span><span class="sxs-lookup"><span data-stu-id="7c64c-142">Note, if used [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) will fail with *E_ILLEGAL_METHOD_CALL*.</span></span>
* <span data-ttu-id="7c64c-143">全息远程处理播放机的启动屏幕经过重新设计，现在不会阻止 "用户" 视图。</span><span class="sxs-lookup"><span data-stu-id="7c64c-143">The Holographic Remoting Player's startup screen has been redesigned and now doesn't block the users view.</span></span>
* <span data-ttu-id="7c64c-144">稳定性改进和 bug 修复。</span><span class="sxs-lookup"><span data-stu-id="7c64c-144">Stability improvements and bug fixes.</span></span>

## <a name="version-212-april-5-2020"></a><span data-ttu-id="7c64c-145">版本 2.1.2 (2020 年4月5日) <a name="v2.1.2"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-145">Version 2.1.2 (April 5, 2020) <a name="v2.1.2"></a></span></span>

* <span data-ttu-id="7c64c-146">修复了最新的全息远程处理播放器与使用小于2.1.0 的版本的远程应用之间的音频向后兼容性问题。</span><span class="sxs-lookup"><span data-stu-id="7c64c-146">Fixed audio backwards compatibility issue between latest Holographic Remoting player and remote apps using version smaller than 2.1.0.</span></span>
* <span data-ttu-id="7c64c-147">固定空间锚定问题，意外地关闭了全息远程处理播放器。</span><span class="sxs-lookup"><span data-stu-id="7c64c-147">Fixed spatial anchor issue, which unexpectedly closed the Holographic Remoting player.</span></span> <span data-ttu-id="7c64c-148">此问题还会影响自定义播放机。</span><span class="sxs-lookup"><span data-stu-id="7c64c-148">This issue also affects custom players.</span></span>

## <a name="version-211-march-20-2020"></a><span data-ttu-id="7c64c-149">版本 2.1.1 (2020 年3月20日) <a name="v2.1.1"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-149">Version 2.1.1 (March 20, 2020) <a name="v2.1.1"></a></span></span>

* <span data-ttu-id="7c64c-150">修复了使用 AMD Gpu 时远程应用的视频编码问题。</span><span class="sxs-lookup"><span data-stu-id="7c64c-150">Fixed video encoding issue with remote apps when using AMD GPUs.</span></span>
* <span data-ttu-id="7c64c-151">全息远程处理播放器性能改进。</span><span class="sxs-lookup"><span data-stu-id="7c64c-151">Holographic Remoting Player performance improvements.</span></span>

## <a name="version-210-march-11-2020"></a><span data-ttu-id="7c64c-152">版本 2.1.0 (2020 年3月11日) <a name="v2.1.0"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-152">Version 2.1.0 (March 11, 2020) <a name="v2.1.0"></a></span></span>

* <span data-ttu-id="7c64c-153">已将网络传输切换为使用 [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP。</span><span class="sxs-lookup"><span data-stu-id="7c64c-153">Switched network transport to use [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP.</span></span> <span data-ttu-id="7c64c-154">安全连接现在使用 [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) 。</span><span class="sxs-lookup"><span data-stu-id="7c64c-154">Secure connections use [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) now.</span></span> <span data-ttu-id="7c64c-155">请注意， [全息远程处理播放器](holographic-remoting-player.md) 仍与所有以前版本的全息远程处理版本兼容。</span><span class="sxs-lookup"><span data-stu-id="7c64c-155">Note, the [Holographic Remoting Player](holographic-remoting-player.md) is still compatible with all previously release Holographic Remoting versions.</span></span> <span data-ttu-id="7c64c-156">若要从新的网络传输中获益，全息远程处理播放器和有问题的远程应用必须使用版本2.1.0。</span><span class="sxs-lookup"><span data-stu-id="7c64c-156">To benefit from the new network transport both, the Holographic Remoting Player and the remote app in question, have to use version 2.1.0.</span></span>
* <span data-ttu-id="7c64c-157">添加了对 [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)的支持。</span><span class="sxs-lookup"><span data-stu-id="7c64c-157">Added support for [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span> 

## <a name="version-2020-february-2-2020"></a><span data-ttu-id="7c64c-158">版本 2.0.20 (2020 年2月2日) <a name="v2.0.20"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-158">Version 2.0.20 (February 2, 2020) <a name="v2.0.20"></a></span></span>

* <span data-ttu-id="7c64c-159">修复了导致崩溃的各种 bug。</span><span class="sxs-lookup"><span data-stu-id="7c64c-159">Fixed various bugs that lead to crashes.</span></span>

## <a name="version-2018-december-17-2019"></a><span data-ttu-id="7c64c-160">版本 2.0.18 (2019 年12月17日) <a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-160">Version 2.0.18 (December 17, 2019) <a name="v2.0.18"></a></span></span>

* <span data-ttu-id="7c64c-161">添加了对[HolographicViewConfiguration](/uwp/api/windows.graphics.holographic.holographicviewconfiguration)的支持</span><span class="sxs-lookup"><span data-stu-id="7c64c-161">Added support for [HolographicViewConfiguration](/uwp/api/windows.graphics.holographic.holographicviewconfiguration)</span></span>
* <span data-ttu-id="7c64c-162">修复了导致崩溃的各种 bug。</span><span class="sxs-lookup"><span data-stu-id="7c64c-162">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="7c64c-163">修复了一个 bug，HolographicCamera 需要 HolographicSpace CameraAdded 回调才能接受，并将其显示为 HolographicFrame 中的已添加照相机。</span><span class="sxs-lookup"><span data-stu-id="7c64c-163">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HolographicFrame.</span></span>

## <a name="version-2016-november-11-2019"></a><span data-ttu-id="7c64c-164">版本 2.0.16 (2019 年11月11日) <a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-164">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>

* <span data-ttu-id="7c64c-165">修复了 QR 代码跟踪中的死锁。</span><span class="sxs-lookup"><span data-stu-id="7c64c-165">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="7c64c-166">修复了 unhandeled 异常，因为在主线程中有一个阻塞等待。</span><span class="sxs-lookup"><span data-stu-id="7c64c-166">Fixed unhandeled exception because of a blocking wait in main thread.</span></span>

## <a name="version-2014-october-26-2019"></a><span data-ttu-id="7c64c-167">版本 2.0.14 (2019 年10月26日) <a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-167">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>

* <span data-ttu-id="7c64c-168">支持新的 PerceptionDevice Api (Windows 10 11 月2019更新) 。</span><span class="sxs-lookup"><span data-stu-id="7c64c-168">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="7c64c-169">修复了此问题，这会阻止 SpatialGestureRecognizer 触发暂停手势事件。</span><span class="sxs-lookup"><span data-stu-id="7c64c-169">Fixed issue, which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="7c64c-170">修复了使用 SpatialSurfaceObserver 时的线程处理问题。</span><span class="sxs-lookup"><span data-stu-id="7c64c-170">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <a name="version-2012-october-18-2019"></a><span data-ttu-id="7c64c-171">版本 2.0.12 (10 月18日 2019) <a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-171">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>

* <span data-ttu-id="7c64c-172">修复了使用 NavigationRail (X/Y/Z) 时 SpatialGestureRecognizer 中的崩溃。</span><span class="sxs-lookup"><span data-stu-id="7c64c-172">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <a name="version-2010-october-10-2019"></a><span data-ttu-id="7c64c-173">版本 v2.0.10 (2019 年10月10日) <a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-173">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>

* <span data-ttu-id="7c64c-174">修复了使用 VR 控制器的触发器按钮时出现故障。</span><span class="sxs-lookup"><span data-stu-id="7c64c-174">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="7c64c-175">全息远程处理并不完全支持控制器，如果与 HoloLens 2 配对，则仅触发器按钮和 Windows 按钮正常工作。</span><span class="sxs-lookup"><span data-stu-id="7c64c-175">Holographic Remoting doesn't fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <a name="version-209-september-19-2019"></a><span data-ttu-id="7c64c-176">版本 2.0.9 (2019 年9月19日) <a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-176">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>

* <span data-ttu-id="7c64c-177">添加了对[SpatialAnchorExporter](/uwp/api/windows.perception.spatial.spatialanchorexporter)的支持</span><span class="sxs-lookup"><span data-stu-id="7c64c-177">Added support for [SpatialAnchorExporter](/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="7c64c-178">添加了 ```IPlayerContext2``` 通过 ```PlayerContext```) 提供以下成员 (实现的新接口：</span><span class="sxs-lookup"><span data-stu-id="7c64c-178">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="7c64c-179">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  属性。</span><span class="sxs-lookup"><span data-stu-id="7c64c-179">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="7c64c-180">```Failed_RemoteFrameTooOld```向添加值```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="7c64c-180">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="7c64c-181">稳定性和可靠性改进</span><span class="sxs-lookup"><span data-stu-id="7c64c-181">Stability and reliability improvements</span></span>

## <a name="version-208-august-20-2019"></a><span data-ttu-id="7c64c-182">版本 2.0.8 (8 月20日 2019) <a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-182">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="7c64c-183">修复了使用[IDXGISurface2](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2)作为参数调用[HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)时的崩溃。</span><span class="sxs-lookup"><span data-stu-id="7c64c-183">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="7c64c-184">稳定性和可靠性改进</span><span class="sxs-lookup"><span data-stu-id="7c64c-184">Stability and reliability improvements</span></span>

## <a name="version-207-july-26-2019"></a><span data-ttu-id="7c64c-185">版本 2.0.7 (2019) 年7月26日 <a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="7c64c-185">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="7c64c-186">适用于 HoloLens 2 的全息远程处理的第一个公共版本。</span><span class="sxs-lookup"><span data-stu-id="7c64c-186">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c64c-187">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7c64c-187">See Also</span></span>

* [<span data-ttu-id="7c64c-188">使用 Windows Mixed Reality Api 编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="7c64c-188">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="7c64c-189">使用 OpenXR Api 编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="7c64c-189">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="7c64c-190">编写自定义全息远程处理播放器应用</span><span class="sxs-lookup"><span data-stu-id="7c64c-190">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="7c64c-191">全息远程处理故障排除和限制</span><span class="sxs-lookup"><span data-stu-id="7c64c-191">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="7c64c-192">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="7c64c-192">Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="7c64c-193">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="7c64c-193">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)