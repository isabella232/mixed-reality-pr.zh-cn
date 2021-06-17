---
title: 面向开发人员的混合现实捕获
description: 了解为开发人员启用、使用和呈现混合现实捕获的最佳实践。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、照片、视频、捕获、照相机
ms.openlocfilehash: ec1a53d2f623a8047c2ee1973d8d6f20458ade88
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110242"
---
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="189fa-104">面向开发人员的混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="189fa-104">Mixed reality capture for developers</span></span>

> [!NOTE]
> <span data-ttu-id="189fa-105">有关适用于 HoloLens 2 的新 MRC 功能的指南，请参阅下面 [的 PV 相机中的 Render](#render-from-the-pv-camera-opt-in) 。</span><span class="sxs-lookup"><span data-stu-id="189fa-105">See [Render from the PV camera](#render-from-the-pv-camera-opt-in) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="189fa-106">你可以在任何时候采用 [混合现实捕获](/hololens/holographic-photos-and-videos) (MRC) 照片或视频，但在开发应用程序时，需要记住以下几点。</span><span class="sxs-lookup"><span data-stu-id="189fa-106">You can take a [mixed reality capture](/hololens/holographic-photos-and-videos) (MRC) photo or video at any time, but there are few things to keep in mind when developing your application.</span></span> <span data-ttu-id="189fa-107">这包括在捕获 MRCs 时，可用于 MRC 视觉质量并响应系统更改的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="189fa-107">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="189fa-108">开发人员还可以将混合现实捕获和插入无缝集成到其应用中。</span><span class="sxs-lookup"><span data-stu-id="189fa-108">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="189fa-109">HoloLens 上的 MRC (第一代) 支持最多720p 的视频和照片，而在 HoloLens 2 上，</span><span class="sxs-lookup"><span data-stu-id="189fa-109">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="189fa-110">质量 MRC 的重要性</span><span class="sxs-lookup"><span data-stu-id="189fa-110">The importance of quality MRC</span></span>

<span data-ttu-id="189fa-111">无论是在 Microsoft Store 页面还是其他用户共享在社交网络上捕获内容的混合现实屏幕截图，混合现实捕获媒体通常都是用户首次暴露给你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="189fa-111">Whether it's mixed reality screenshots on your Microsoft Store page or other users sharing capture content on social networks, Mixed Reality Capture media is often a users first exposure to your app.</span></span> <span data-ttu-id="189fa-112">您可以使用 MRC 来演示您的应用程序、培训用户、鼓励用户共享其混合世界交互，以及进行用户研究和解决问题。</span><span class="sxs-lookup"><span data-stu-id="189fa-112">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="189fa-113">MRC 如何影响你的应用</span><span class="sxs-lookup"><span data-stu-id="189fa-113">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="189fa-114">在应用程序中启用 MRC</span><span class="sxs-lookup"><span data-stu-id="189fa-114">Enabling MRC in your app</span></span>

<span data-ttu-id="189fa-115">默认情况下，应用程序无需执行任何操作即可使用户接受混合的现实捕获。</span><span class="sxs-lookup"><span data-stu-id="189fa-115">By default, an app doesn't have to do anything to enable users to take mixed reality captures.</span></span>

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a><span data-ttu-id="189fa-116">在应用中为 MRC 启用改进的对齐方式</span><span class="sxs-lookup"><span data-stu-id="189fa-116">Enabling improved alignment for MRC in your app</span></span>

<span data-ttu-id="189fa-117">默认情况下，混合现实捕获会将适当眼睛的全息输出与照片/视频 (PV) 摄像组合在一起。</span><span class="sxs-lookup"><span data-stu-id="189fa-117">By default, mixed reality capture combines the right eye's holographic output with the photo/video (PV) camera.</span></span> <span data-ttu-id="189fa-118">这两个源使用当前运行的沉浸式应用设置的焦点组合在一起。</span><span class="sxs-lookup"><span data-stu-id="189fa-118">These two sources are combined using the focus point set by the currently running immersive app.</span></span>

<span data-ttu-id="189fa-119">这意味着，由于 PV 摄像机与右显示之间的物理距离，因此不会对齐焦点平面外的全息影像。</span><span class="sxs-lookup"><span data-stu-id="189fa-119">This means that holograms outside the focus plane won't align because of the physical distance between the PV camera and the right display.</span></span>

#### <a name="set-the-focus-point"></a><span data-ttu-id="189fa-120">设置焦点</span><span class="sxs-lookup"><span data-stu-id="189fa-120">Set the focus point</span></span>

<span data-ttu-id="189fa-121">在 HoloLens) 上 (沉浸式应用程序时，应将 [焦点](../unity/focus-point-in-unity.md) 设置为要将其稳定平面置于何处。</span><span class="sxs-lookup"><span data-stu-id="189fa-121">Immersive apps (on HoloLens) should set the [focus point](../unity/focus-point-in-unity.md) of where they want their stabilization plane to be.</span></span> <span data-ttu-id="189fa-122">这确保了耳机和混合现实捕获中的最佳对齐。</span><span class="sxs-lookup"><span data-stu-id="189fa-122">This ensures the best alignment in both the headset and in mixed reality capture.</span></span>

<span data-ttu-id="189fa-123">如果未设置焦点，则稳定平面将默认为2米。</span><span class="sxs-lookup"><span data-stu-id="189fa-123">If a focus point isn't set, the stabilization plane will default to 2 meters.</span></span>

#### <a name="render-from-the-pv-camera-opt-in"></a><span data-ttu-id="189fa-124">通过 PV 相机进行渲染 (选择加入) </span><span class="sxs-lookup"><span data-stu-id="189fa-124">Render from the PV camera (opt-in)</span></span>

<span data-ttu-id="189fa-125">HoloLens 2 添加了一种功能，使沉浸式应用能够在混合现实捕获运行时 **从 PV 摄像机进行呈现** 。</span><span class="sxs-lookup"><span data-stu-id="189fa-125">HoloLens 2 adds the ability for an immersive app to **render from the PV camera** while mixed reality capture is running.</span></span> <span data-ttu-id="189fa-126">若要确保应用正确支持其他呈现，应用必须选择启用此功能。</span><span class="sxs-lookup"><span data-stu-id="189fa-126">To ensure the app supports the additional render correctly, the app has to opt in to this functionality.</span></span>

<span data-ttu-id="189fa-127">PV 相机中的呈现功能与默认的 MRC 体验相比具有以下改进：</span><span class="sxs-lookup"><span data-stu-id="189fa-127">Render from the PV camera offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="189fa-128">与您的物理环境之间的全息图对齐方式，并且在任何距离上都精确到了近乎交互。</span><span class="sxs-lookup"><span data-stu-id="189fa-128">Hologram alignment to your physical environment and hands for near interactions should be accurate at all distances.</span></span> <span data-ttu-id="189fa-129">避免在不同于焦点的位置上偏移，因为在默认 MRC 中可能会看到。</span><span class="sxs-lookup"><span data-stu-id="189fa-129">Avoid having an offset at distances other than the focus point as you might see in the default MRC.</span></span>
* <span data-ttu-id="189fa-130">头戴式耳机不会受到影响，因为它不会用于呈现 MRC 输出的全息影像。</span><span class="sxs-lookup"><span data-stu-id="189fa-130">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

<span data-ttu-id="189fa-131">可以通过以下三个步骤，通过 PV 相机实现呈现：</span><span class="sxs-lookup"><span data-stu-id="189fa-131">There are three steps to enable rendering from the PV camera:</span></span>
1. <span data-ttu-id="189fa-132">启用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="189fa-132">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>
2. <span data-ttu-id="189fa-133">处理附加的 HolographicCamera 呈现</span><span class="sxs-lookup"><span data-stu-id="189fa-133">Handle the additional HolographicCamera render</span></span>
3. <span data-ttu-id="189fa-134">通过此附加 HolographicCamera 正确验证着色器和代码呈现</span><span class="sxs-lookup"><span data-stu-id="189fa-134">Verify your shaders and code render correctly from this additional HolographicCamera</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a><span data-ttu-id="189fa-135">在 DirectX 中启用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="189fa-135">Enable the PhotoVideoCamera HolographicViewConfiguration in DirectX</span></span>

<span data-ttu-id="189fa-136">若要选择从 PV 相机进行渲染，应用只需启用 PhotoVideoCamera 的 [HolographicViewConfiguration](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)：</span><span class="sxs-lookup"><span data-stu-id="189fa-136">To opt in to rendering from the PV Camera, an app simply enables the PhotoVideoCamera's [HolographicViewConfiguration](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span></span>
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a><span data-ttu-id="189fa-137">在 DirectX 中处理附加的 HolographicCamera 呈现</span><span class="sxs-lookup"><span data-stu-id="189fa-137">Handle the additional HolographicCamera render in DirectX</span></span>

<span data-ttu-id="189fa-138">当应用程序有选择地从 PV 相机进行呈现且混合现实捕获开始时：</span><span class="sxs-lookup"><span data-stu-id="189fa-138">When the app has opt-in to render from the PV camera and mixed reality capture starts:</span></span>
1. <span data-ttu-id="189fa-139">HolographicSpace 的 CameraAdded 事件将激发。</span><span class="sxs-lookup"><span data-stu-id="189fa-139">HolographicSpace's CameraAdded event will fire.</span></span> <span data-ttu-id="189fa-140">如果此时应用无法处理照相机，此事件可能会延迟。</span><span class="sxs-lookup"><span data-stu-id="189fa-140">This event can be deferred if the app can't handle the camera at this time.</span></span>
2. <span data-ttu-id="189fa-141">事件完成后，如果没有未完成的延迟，则 HolographicCamera 将在下一个 HolographicFrame 的 AddedCameras 列表中显示。</span><span class="sxs-lookup"><span data-stu-id="189fa-141">Once the event has completed with no outstanding deferrals, the HolographicCamera will appear in the next HolographicFrame's AddedCameras list.</span></span>

<span data-ttu-id="189fa-142">当混合现实捕获停止时 (或应用在混合现实捕获正在运行时禁用了视图配置) ： HolographicCamera 将显示在下一个 HolographicFrame 的 RemovedCameras 列表中，并激发 HolographicSpace 的 CameraRemoved 事件。</span><span class="sxs-lookup"><span data-stu-id="189fa-142">When mixed reality capture stops (or if the app disables the view configuration while mixed reality capture is running): the HolographicCamera will appear in the next HolographicFrame's RemovedCameras list and the HolographicSpace's CameraRemoved event will fire.</span></span>

<span data-ttu-id="189fa-143">已将 [ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) 属性添加到 HolographicCamera，以帮助标识相机所属的配置。</span><span class="sxs-lookup"><span data-stu-id="189fa-143">A [ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) property has been added to HolographicCamera to help identify the configuration a camera belongs to.</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a><span data-ttu-id="189fa-144">在 Unity 中启用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="189fa-144">Enable the PhotoVideoCamera HolographicViewConfiguration in Unity</span></span>

> [!NOTE]
> <span data-ttu-id="189fa-145">如果使用的是 Unity 2018，则需要使用 **unity 2018.4.13 f1** 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="189fa-145">If you're using Unity 2018, this requires **Unity 2018.4.13f1** or newer.</span></span> <span data-ttu-id="189fa-146">如果使用的是 Unity 2019，则需要 **unity 2019.4** 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="189fa-146">If you're using Unity 2019, this requires **Unity 2019.4**, or newer.</span></span>

<span data-ttu-id="189fa-147">若要在使用 [混合现实工具包](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)时选择使用 pv 相机进行呈现，请启用 [Windows Mixed reality 相机设置](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings) 提供程序，并 **通过 PV 相机检查 Render**。</span><span class="sxs-lookup"><span data-stu-id="189fa-147">To opt in to rendering from the PV Camera when using the [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html), enable the [Windows Mixed Reality Camera Settings](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings) provider and check **Render from PV Camera**.</span></span>

<span data-ttu-id="189fa-148">如果使用的不是混合现实工具包，则可以使用组件 [手动选择启用](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) DirectX。</span><span class="sxs-lookup"><span data-stu-id="189fa-148">If you're not using the Mixed Reality Toolkit, you can use a component to [manually opt-in](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) as described above for DirectX.</span></span>

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a><span data-ttu-id="189fa-149">处理 Unity 中的其他 HolographicCamera 呈现</span><span class="sxs-lookup"><span data-stu-id="189fa-149">Handle the additional HolographicCamera render in Unity</span></span>

<span data-ttu-id="189fa-150">这是由 Unity 自动完成的。</span><span class="sxs-lookup"><span data-stu-id="189fa-150">This is done for you automatically by Unity.</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a><span data-ttu-id="189fa-151">启用 Unreal 中的 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="189fa-151">Enable the PhotoVideoCamera HolographicViewConfiguration in Unreal</span></span>

> [!NOTE]
> <span data-ttu-id="189fa-152">这需要 Unreal Engine 4.25 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="189fa-152">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="189fa-153">若要选择从 PV 摄像头进行渲染：</span><span class="sxs-lookup"><span data-stu-id="189fa-153">To opt in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="189fa-154">调用 SetEnabledMixedRealityCamera 和 ResizeMixedRealityCamera </span><span class="sxs-lookup"><span data-stu-id="189fa-154">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="189fa-155">使用“尺寸 X”和“尺寸 Y”值设置视频尺寸。 </span><span class="sxs-lookup"><span data-stu-id="189fa-155">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![第三人称摄像头](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a><span data-ttu-id="189fa-157">在 Unreal 中处理附加的 HolographicCamera 呈现</span><span class="sxs-lookup"><span data-stu-id="189fa-157">Handle the additional HolographicCamera render in Unreal</span></span>

<span data-ttu-id="189fa-158">这是由 Unreal 自动完成的。</span><span class="sxs-lookup"><span data-stu-id="189fa-158">This is done for you automatically by Unreal.</span></span>

##### <a name="verify-shaders-and-code-support-additional-cameras"></a><span data-ttu-id="189fa-159">验证着色器和代码支持其他相机</span><span class="sxs-lookup"><span data-stu-id="189fa-159">Verify shaders and code support additional cameras</span></span>

<span data-ttu-id="189fa-160">运行混合现实捕获，并检查是否存在异常对齐、缺少内容或性能问题。</span><span class="sxs-lookup"><span data-stu-id="189fa-160">Run a mixed reality capture and check for unusual alignment, missing content, or performance issues.</span></span> <span data-ttu-id="189fa-161">根据需要更新着色器和代码。</span><span class="sxs-lookup"><span data-stu-id="189fa-161">Update shaders and code as appropriate.</span></span>

<span data-ttu-id="189fa-162">如果某些场景无法支持向其他相机进行渲染，则可以禁用 PhotoVideoCamera 的 HolographicViewConfiguration。</span><span class="sxs-lookup"><span data-stu-id="189fa-162">If there are certain scenes that can't support rendering to an additional camera, you can disable the PhotoVideoCamera's HolographicViewConfiguration.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="189fa-163">在应用中禁用 MRC</span><span class="sxs-lookup"><span data-stu-id="189fa-163">Disabling MRC in your app</span></span>

#### <a name="2d-app"></a><span data-ttu-id="189fa-164">2D 应用</span><span class="sxs-lookup"><span data-stu-id="189fa-164">2D app</span></span>

<span data-ttu-id="189fa-165">当混合现实捕获正在运行时，2D 应用可以选择使其视觉内容遮盖：</span><span class="sxs-lookup"><span data-stu-id="189fa-165">2D apps can choose to have their visual content obscured when mixed reality capture is running by:</span></span>
* <span data-ttu-id="189fa-166">与 [DXGI_PRESENT_RESTRICT_TO_OUTPUT](/windows/desktop/direct3ddxgi/dxgi-present) 标志一起提供</span><span class="sxs-lookup"><span data-stu-id="189fa-166">Present with the [DXGI_PRESENT_RESTRICT_TO_OUTPUT](/windows/desktop/direct3ddxgi/dxgi-present) flag</span></span>
* <span data-ttu-id="189fa-167">用 [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) 标志创建应用的交换链</span><span class="sxs-lookup"><span data-stu-id="189fa-167">Create the app's swap chain with the [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) flag</span></span>
* <span data-ttu-id="189fa-168">对于 Windows 10 2019 更新，设置 w 的 [IsScreenCaptureEnabled](/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span><span class="sxs-lookup"><span data-stu-id="189fa-168">With the Windows 10 May 2019 Update, setting ApplicationView's [IsScreenCaptureEnabled](/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span></span>

#### <a name="immersive-app"></a><span data-ttu-id="189fa-169">沉浸式应用</span><span class="sxs-lookup"><span data-stu-id="189fa-169">Immersive app</span></span>

<span data-ttu-id="189fa-170">沉浸式应用可通过以下方式选择将其视觉内容从混合现实捕获中排除：</span><span class="sxs-lookup"><span data-stu-id="189fa-170">Immersive apps can choose to have their visual content excluded from mixed reality capture by:</span></span>
* <span data-ttu-id="189fa-171">设置 HolographicCameraRenderingParameter 的 [IsContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) 以禁用其关联帧的混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="189fa-171">Setting HolographicCameraRenderingParameter's [IsContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) to disable mixed reality capture for its associated frame</span></span>
* <span data-ttu-id="189fa-172">将 HolographicCamera 的 [IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) 设置为对其关联的全息相机禁用混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="189fa-172">Setting HolographicCamera's [IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) to disable mixed reality capture for its associated holographic camera</span></span>

#### <a name="password-keyboard"></a><span data-ttu-id="189fa-173">密码键盘</span><span class="sxs-lookup"><span data-stu-id="189fa-173">Password Keyboard</span></span>

<span data-ttu-id="189fa-174">使用 Windows 10 的2019更新可能会在密码或 pin 键盘可见时，自动从混合现实捕获中排除可视内容。</span><span class="sxs-lookup"><span data-stu-id="189fa-174">With the Windows 10 May 2019 Update, visual content is automatically excluded from mixed reality capture when a password or pin keyboard is visible.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="189fa-175">了解 MRC 何时处于活动状态</span><span class="sxs-lookup"><span data-stu-id="189fa-175">Knowing when MRC is active</span></span>

<span data-ttu-id="189fa-176">应用程序可以使用 [AppCapture](/uwp/api/Windows.Media.Capture.AppCapture) 类来了解系统混合现实捕获运行的时间 (音频或视频) 。</span><span class="sxs-lookup"><span data-stu-id="189fa-176">The [AppCapture](/uwp/api/Windows.Media.Capture.AppCapture) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="189fa-177">如果混合现实捕获在设备上不可用，则 AppCapture 的 [GetForCurrentView](/uwp/api/windows.media.capture.appcapture.getforcurrentview) API 可以返回 null。</span><span class="sxs-lookup"><span data-stu-id="189fa-177">AppCapture's [GetForCurrentView](/uwp/api/windows.media.capture.appcapture.getforcurrentview) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="189fa-178">在应用暂停时取消注册 CapturingChanged 事件也很重要，否则可能会进入 "已阻止" 状态。</span><span class="sxs-lookup"><span data-stu-id="189fa-178">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="189fa-179"> (HoloLens 特定) 的最佳实践</span><span class="sxs-lookup"><span data-stu-id="189fa-179">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="189fa-180">在不进行其他开发工作的情况下，MRC 应正常工作，但在提供最佳混合现实捕获体验时需要注意一些事项。</span><span class="sxs-lookup"><span data-stu-id="189fa-180">MRC is expected to work without additional development effort, but there are a few things to be aware of when providing the best mixed reality capture experience.</span></span>

<span data-ttu-id="189fa-181">**MRC 使用全息图的 alpha 通道与 [相机](locatable-camera.md) 图像混合**</span><span class="sxs-lookup"><span data-stu-id="189fa-181">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="189fa-182">最重要的步骤是确保您的应用程序清除为透明黑色，而不是清除为不透明的黑色。</span><span class="sxs-lookup"><span data-stu-id="189fa-182">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="189fa-183">在 Unity 中，这是默认情况下通过 MixedRealityToolkit 实现的。</span><span class="sxs-lookup"><span data-stu-id="189fa-183">In Unity, this is done by default with the MixedRealityToolkit.</span></span> <span data-ttu-id="189fa-184">如果是在非 Unity 中进行开发，则可能需要更改一行。</span><span class="sxs-lookup"><span data-stu-id="189fa-184">If you're developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="189fa-185">如果你的应用未清除透明黑色，以下是你可能会在 MRC 中看到的一些项目：</span><span class="sxs-lookup"><span data-stu-id="189fa-185">Here are some of the artifacts you might see in MRC if your app isn't clearing to transparent black:</span></span>

<span data-ttu-id="189fa-186">**示例失败**：内容周围的黑色边缘 (未能清除透明黑色) </span><span class="sxs-lookup"><span data-stu-id="189fa-186">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

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

<span data-ttu-id="189fa-187">**示例失败**：全息图的整个背景场景显示为黑色。</span><span class="sxs-lookup"><span data-stu-id="189fa-187">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="189fa-188">将一个背景 alpha 值设置为黑色背景</span><span class="sxs-lookup"><span data-stu-id="189fa-188">Setting a background alpha value of one results in a black background</span></span>

![将背景 alpha 值设置为1会导致黑色背景](images/clearopaqueblack-300px.png)

<span data-ttu-id="189fa-190">**预期结果**：如果清除为透明黑色，全息影像会与实际的 (预期结果相结合) </span><span class="sxs-lookup"><span data-stu-id="189fa-190">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![清除为透明黑色时的预期结果](images/cleartransparentblack-300px.png)

<span data-ttu-id="189fa-192">**解决方案**；</span><span class="sxs-lookup"><span data-stu-id="189fa-192">**Solution**:</span></span>
* <span data-ttu-id="189fa-193">将显示为不透明黑色的任何内容更改为 alpha 值0。</span><span class="sxs-lookup"><span data-stu-id="189fa-193">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="189fa-194">确保应用清除为透明黑色。</span><span class="sxs-lookup"><span data-stu-id="189fa-194">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="189fa-195">Unity 默认使用 MixedRealityToolkit 自动清除，但如果它是非 Unity 应用，应修改与 ID3D11DeiceContext：： ClearRenderTargetView () 一起使用的颜色。</span><span class="sxs-lookup"><span data-stu-id="189fa-195">Unity defaults to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="189fa-196">您需要确保清除透明的黑色 (0，0，0，0，0) 而不是不透明的黑色 (0，0，0，1) 。</span><span class="sxs-lookup"><span data-stu-id="189fa-196">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="189fa-197">你现在可以根据需要调整资产的 alpha 值，但通常不需要这样做。</span><span class="sxs-lookup"><span data-stu-id="189fa-197">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="189fa-198">大多数情况下，MRCs 将看起来不错。</span><span class="sxs-lookup"><span data-stu-id="189fa-198">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="189fa-199">MRC 假设预乘 alpha。</span><span class="sxs-lookup"><span data-stu-id="189fa-199">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="189fa-200">Alpha 值仅影响 MRC 捕获。</span><span class="sxs-lookup"><span data-stu-id="189fa-200">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="189fa-201">在 HoloLens 上启用了 MRC 时应发生的情况</span><span class="sxs-lookup"><span data-stu-id="189fa-201">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="189fa-202">以下各项适用于 HoloLens (第一代) 和 HoloLens 2，除非另有说明：</span><span class="sxs-lookup"><span data-stu-id="189fa-202">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="189fa-203">系统会将应用程序限制为 30-Hz。</span><span class="sxs-lookup"><span data-stu-id="189fa-203">The system will throttle the application to 30-Hz rendering.</span></span> <span data-ttu-id="189fa-204">这会为 MRC 创建一些空间，使应用无需保留固定预算预留，同时还可匹配 30 fps 的 MRC 视频记录的帧速率</span><span class="sxs-lookup"><span data-stu-id="189fa-204">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30 fps</span></span>
* <span data-ttu-id="189fa-205">录制/流式处理 MRC 时，全息图内容在设备上显示为 "火花"：文本可能会变得更难以阅读， (在 **HoloLens 2** 上选择第三个照相机呈现可以避免这种折衷) </span><span class="sxs-lookup"><span data-stu-id="189fa-205">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting in to third camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="189fa-206">当应用程序启用了应用程序时，MRC 照片和视频将遵循应用程序的 [重点点](../unity/focus-point-in-unity.md) ，这将有助于确保全息影像精确定位。</span><span class="sxs-lookup"><span data-stu-id="189fa-206">MRC photos and videos will respect the application’s [focus point](../unity/focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="189fa-207">对于视频，重点是平滑的，因此，如果焦点深度发生变化，全息影像可能会慢慢地发生缓慢偏移。</span><span class="sxs-lookup"><span data-stu-id="189fa-207">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="189fa-208">处于焦点不同深度的全息影像可能会显示与现实世界不同的偏移 (请参阅下面的示例，其中焦点设置为2米，而全息图位于1米) 。</span><span class="sxs-lookup"><span data-stu-id="189fa-208">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![2米的全息影像会完全注册到世界。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="189fa-211">在应用中集成 MRC 功能</span><span class="sxs-lookup"><span data-stu-id="189fa-211">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="189fa-212">混合现实应用可以从应用内启动 MRC 照片或视频捕获，而捕获的内容将在应用中提供，而不会存储到设备的 "照相机"。</span><span class="sxs-lookup"><span data-stu-id="189fa-212">Your mixed reality app can start MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="189fa-213">您可以创建自定义的 MRC 记录器或利用内置的相机捕获 UI。</span><span class="sxs-lookup"><span data-stu-id="189fa-213">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="189fa-214">带有内置照相机 UI 的 MRC</span><span class="sxs-lookup"><span data-stu-id="189fa-214">MRC with built-in camera UI</span></span>

<span data-ttu-id="189fa-215">开发人员只需编写几行代码，即可使用 *[相机捕获 UI API](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 获取用户捕获的混合现实照片或视频。</span><span class="sxs-lookup"><span data-stu-id="189fa-215">Developers can use the *[Camera Capture UI API](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="189fa-216">此 API 启动内置的 MRC 相机 UI，用户可以在其中拍摄照片或视频，并将生成的捕获结果返回到应用。</span><span class="sxs-lookup"><span data-stu-id="189fa-216">This API launches the built-in MRC camera UI where users can take a photo or video and returns the resulting capture to your app.</span></span> <span data-ttu-id="189fa-217">如果需要添加自己的相机 UI 或较低级别的访问权限来捕获流，则可以创建自定义混合现实捕获记录器。</span><span class="sxs-lookup"><span data-stu-id="189fa-217">You can create a custom Mixed Reality Capture recorder if you need to add your own camera UI or lower-level access to capture streams.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="189fa-218">创建自定义 MRC 记录器</span><span class="sxs-lookup"><span data-stu-id="189fa-218">Creating a custom MRC recorder</span></span>

<span data-ttu-id="189fa-219">尽管用户始终可以使用系统 MRC 捕获服务来触发照片或视频，但应用程序可能需要构建自定义相机应用程序，该应用程序在相机流中包含全息影像，就像在 "MRC" 中一样。</span><span class="sxs-lookup"><span data-stu-id="189fa-219">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app that include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="189fa-220">这样，应用程序便可以从用户输入、生成自定义录制 UI，或自定义 MRC 设置以命名几个示例。</span><span class="sxs-lookup"><span data-stu-id="189fa-220">This allows the application to kick off captures from user input, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="189fa-221">**HoloStudio 使用 MRC 效果添加自定义 MRC 相机**</span><span class="sxs-lookup"><span data-stu-id="189fa-221">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio 使用 MRC 效果添加自定义 MRC 相机](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="189fa-223">Unity 应用程序应看到属性 [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) ，以启用全息影像。</span><span class="sxs-lookup"><span data-stu-id="189fa-223">Unity Applications should see [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="189fa-224">其他应用程序可以通过使用 [Windows 媒体捕获 api](/uwp/api/Windows.Media.Capture.MediaCapture) 控制相机并添加 MRC 视频和音频效果来包括静止图像和视频中的虚拟全息影像和应用程序音频，来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="189fa-224">Other applications can do this by using the [Windows Media Capture APIs](/uwp/api/Windows.Media.Capture.MediaCapture) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="189fa-225">应用程序有两个选项可添加效果：</span><span class="sxs-lookup"><span data-stu-id="189fa-225">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="189fa-226">旧的 API： [MediaCapture. AddEffectAsync () ](/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span><span class="sxs-lookup"><span data-stu-id="189fa-226">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span></span>
* <span data-ttu-id="189fa-227">新的 Microsoft 推荐 API (将返回一个对象，这使你能够操作) ： MediaCapture 的动态属性[ () ](/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)：  /  [ () ](/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) ，这需要应用程序创建自己的[IVideoEffectDefinition](/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)和[IAudioEffectDefinition](/uwp/api/windows.media.effects.iaudioeffectdefinition)实现。</span><span class="sxs-lookup"><span data-stu-id="189fa-227">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) which require the app create its own implementation of [IVideoEffectDefinition](/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) and [IAudioEffectDefinition](/uwp/api/windows.media.effects.iaudioeffectdefinition).</span></span> <span data-ttu-id="189fa-228">有关示例，请参阅 [MRC 示例应用](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture) 。</span><span class="sxs-lookup"><span data-stu-id="189fa-228">See the [MRC sample app](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture) for examples.</span></span>

>[!NOTE]
> <span data-ttu-id="189fa-229">Visual Studio 将无法识别 MixedRealityCapture 命名空间，但字符串仍然有效。</span><span class="sxs-lookup"><span data-stu-id="189fa-229">The Windows.Media.MixedRealityCapture namespace will not be recognized by Visual Studio, but the strings are still valid.</span></span>

<span data-ttu-id="189fa-230">MRC 视频效果 (**MixedRealityCaptureVideoEffect**) </span><span class="sxs-lookup"><span data-stu-id="189fa-230">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="189fa-231">属性名称</span><span class="sxs-lookup"><span data-stu-id="189fa-231">Property Name</span></span>  |  <span data-ttu-id="189fa-232">类型</span><span class="sxs-lookup"><span data-stu-id="189fa-232">Type</span></span>  |  <span data-ttu-id="189fa-233">默认值</span><span class="sxs-lookup"><span data-stu-id="189fa-233">Default Value</span></span>  |  <span data-ttu-id="189fa-234">说明</span><span class="sxs-lookup"><span data-stu-id="189fa-234">Description</span></span> |
|----------|----------|----------|----------|
|  <span data-ttu-id="189fa-235">StreamType</span><span class="sxs-lookup"><span data-stu-id="189fa-235">StreamType</span></span>  |  <span data-ttu-id="189fa-236">UINT32 ([mediastreamtype.video](/uwp/api/Windows.Media.Capture.MediaStreamType)) </span><span class="sxs-lookup"><span data-stu-id="189fa-236">UINT32 ([MediaStreamType](/uwp/api/Windows.Media.Capture.MediaStreamType))</span></span>  |  <span data-ttu-id="189fa-237">1 (VideoRecord) </span><span class="sxs-lookup"><span data-stu-id="189fa-237">1 (VideoRecord)</span></span>  |  <span data-ttu-id="189fa-238">描述此影响所使用的捕获流。</span><span class="sxs-lookup"><span data-stu-id="189fa-238">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="189fa-239">音频不可用。</span><span class="sxs-lookup"><span data-stu-id="189fa-239">Audio isn't available.</span></span> |
|  <span data-ttu-id="189fa-240">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="189fa-240">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="189fa-241">boolean</span><span class="sxs-lookup"><span data-stu-id="189fa-241">boolean</span></span>  |  <span data-ttu-id="189fa-242">TRUE</span><span class="sxs-lookup"><span data-stu-id="189fa-242">TRUE</span></span>  |  <span data-ttu-id="189fa-243">用于在视频捕获中启用或禁用全息影像的标志。</span><span class="sxs-lookup"><span data-stu-id="189fa-243">Flag to enable or disable holograms in video capture.</span></span> |
|  <span data-ttu-id="189fa-244">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="189fa-244">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="189fa-245">boolean</span><span class="sxs-lookup"><span data-stu-id="189fa-245">boolean</span></span>  |  <span data-ttu-id="189fa-246">TRUE</span><span class="sxs-lookup"><span data-stu-id="189fa-246">TRUE</span></span>  |  <span data-ttu-id="189fa-247">用于在全息影像捕获期间启用或禁用录制指示器的标志。</span><span class="sxs-lookup"><span data-stu-id="189fa-247">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> |
|  <span data-ttu-id="189fa-248">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="189fa-248">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="189fa-249">boolean</span><span class="sxs-lookup"><span data-stu-id="189fa-249">boolean</span></span>  |  <span data-ttu-id="189fa-250">FALSE</span><span class="sxs-lookup"><span data-stu-id="189fa-250">FALSE</span></span>  |  <span data-ttu-id="189fa-251">用于启用或禁用由 HoloLens 跟踪器支持的视频稳定的标志。</span><span class="sxs-lookup"><span data-stu-id="189fa-251">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> |
|  <span data-ttu-id="189fa-252">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="189fa-252">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="189fa-253">UINT32</span><span class="sxs-lookup"><span data-stu-id="189fa-253">UINT32</span></span>  |  <span data-ttu-id="189fa-254">0</span><span class="sxs-lookup"><span data-stu-id="189fa-254">0</span></span>  |  <span data-ttu-id="189fa-255">设置视频抖动使用的历史帧数。</span><span class="sxs-lookup"><span data-stu-id="189fa-255">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="189fa-256">从电源和性能的角度来看，0从0到延迟，几乎是 "免费"。</span><span class="sxs-lookup"><span data-stu-id="189fa-256">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="189fa-257">15对于最高质量 (建议使用15帧延迟和内存) 。</span><span class="sxs-lookup"><span data-stu-id="189fa-257">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> |
|  <span data-ttu-id="189fa-258">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="189fa-258">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="189fa-259">FLOAT</span><span class="sxs-lookup"><span data-stu-id="189fa-259">float</span></span>  |  <span data-ttu-id="189fa-260">0.9 (HoloLens) 1.0 (沉浸式耳机) </span><span class="sxs-lookup"><span data-stu-id="189fa-260">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="189fa-261">将范围从 0.0 (完全透明) 到 (1.0 的全局不透明度系数设置为完全不透明) 。</span><span class="sxs-lookup"><span data-stu-id="189fa-261">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> |
|  <span data-ttu-id="189fa-262">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="189fa-262">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="189fa-263">boolean</span><span class="sxs-lookup"><span data-stu-id="189fa-263">boolean</span></span>  |  <span data-ttu-id="189fa-264">FALSE</span><span class="sxs-lookup"><span data-stu-id="189fa-264">FALSE</span></span>  |  <span data-ttu-id="189fa-265">用于启用或禁用在有显示受保护内容的 2d UWP 应用时返回空帧的标志。</span><span class="sxs-lookup"><span data-stu-id="189fa-265">Flag to enable or disable returning an empty frame if there's a 2d UWP app showing protected content.</span></span> <span data-ttu-id="189fa-266">如果此标志为 false，并且二维 UWP 应用显示受保护的内容，则在耳机和混合现实捕获中，二维 UWP 应用将替换为受保护的内容纹理。</span><span class="sxs-lookup"><span data-stu-id="189fa-266">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="189fa-267">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="189fa-267">ShowHiddenMesh</span></span>  |  <span data-ttu-id="189fa-268">boolean</span><span class="sxs-lookup"><span data-stu-id="189fa-268">boolean</span></span>  |  <span data-ttu-id="189fa-269">FALSE</span><span class="sxs-lookup"><span data-stu-id="189fa-269">FALSE</span></span>  |  <span data-ttu-id="189fa-270">用于启用或禁用显示全息相机隐藏区域网格和相邻内容的标志。</span><span class="sxs-lookup"><span data-stu-id="189fa-270">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |
| <span data-ttu-id="189fa-271">OutputSize</span><span class="sxs-lookup"><span data-stu-id="189fa-271">OutputSize</span></span> | <span data-ttu-id="189fa-272">大小</span><span class="sxs-lookup"><span data-stu-id="189fa-272">Size</span></span> | <span data-ttu-id="189fa-273">0, 0</span><span class="sxs-lookup"><span data-stu-id="189fa-273">0, 0</span></span> | <span data-ttu-id="189fa-274">在裁剪视频稳定性后设置所需的输出大小。</span><span class="sxs-lookup"><span data-stu-id="189fa-274">Set the desired output size after cropping for video stabilization.</span></span> <span data-ttu-id="189fa-275">如果指定了0或指定了无效的输出大小，则选择默认裁剪大小。</span><span class="sxs-lookup"><span data-stu-id="189fa-275">A default crop size is chosen if 0 or an invalid output size is specified.</span></span> |
| <span data-ttu-id="189fa-276">PreferredHologramPerspective</span><span class="sxs-lookup"><span data-stu-id="189fa-276">PreferredHologramPerspective</span></span> | <span data-ttu-id="189fa-277">UINT32</span><span class="sxs-lookup"><span data-stu-id="189fa-277">UINT32</span></span> | <span data-ttu-id="189fa-278">Windows 设备门户中的 "**从相机呈现**" 设置</span><span class="sxs-lookup"><span data-stu-id="189fa-278">**Render from Camera** setting in the Windows Device Portal</span></span> | <span data-ttu-id="189fa-279">用于指示应捕获的全息相机视图配置的枚举： 0 (显示) 意味着不会要求应用从照片/视频相机进行渲染，1 (PhotoVideoCamera) 会要求应用从照片/视频摄像机， (应用程序支持它) 。</span><span class="sxs-lookup"><span data-stu-id="189fa-279">Enum used to indicate which holographic camera view configuration should be captured: 0 (Display) means that the app won't be asked to render from the photo/video camera, 1 (PhotoVideoCamera) will ask the app to render from the photo/video camera (if the app supports it).</span></span> <span data-ttu-id="189fa-280">仅在 HoloLens 2 上受支持</span><span class="sxs-lookup"><span data-stu-id="189fa-280">Only supported on HoloLens 2</span></span> |

>[!NOTE]
> <span data-ttu-id="189fa-281">可以通过转到 [混合现实捕获页面](using-the-windows-device-portal.md#mixed-reality-capture)并取消选中 "**从相机** 中进行渲染"，在 Windows 设备门户中更改 **PreferredHologramPerspective** 的默认值。</span><span class="sxs-lookup"><span data-stu-id="189fa-281">You can change the default value of **PreferredHologramPerspective** in the Windows Device Portal by going to the [Mixed Reality Capture page](using-the-windows-device-portal.md#mixed-reality-capture) and unchecking **Render from Camera**.</span></span> <span data-ttu-id="189fa-282">设置默认为 **1 (PhotoVideoCamera)**，但可以取消选中以将其设置为 **0 (显示)**。</span><span class="sxs-lookup"><span data-stu-id="189fa-282">The setting defaults to **1 (PhotoVideoCamera)**, but can be unchecked to set it to **0 (Display)**.</span></span>
>
> <span data-ttu-id="189fa-283">**PreferredHologramPerspective** 的默认值为 **0 (显示** 2020 年6月版 (Windows 全息版、版本2004内部版本19041.1106 和 windows 全息版 1903 build 18362.1064) 之前) 显示。</span><span class="sxs-lookup"><span data-stu-id="189fa-283">The default value of **PreferredHologramPerspective** was **0 (Display)** prior to the June 2020 update (Windows Holographic, version 2004 build 19041.1106 and Windows Holographic, version 1903 build 18362.1064).</span></span>

<span data-ttu-id="189fa-284"> (**MixedRealityCaptureAudioEffect) 的** MRC 音频效果</span><span class="sxs-lookup"><span data-stu-id="189fa-284">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

| <span data-ttu-id="189fa-285">属性名称</span><span class="sxs-lookup"><span data-stu-id="189fa-285">Property Name</span></span> | <span data-ttu-id="189fa-286">类型</span><span class="sxs-lookup"><span data-stu-id="189fa-286">Type</span></span> | <span data-ttu-id="189fa-287">默认值</span><span class="sxs-lookup"><span data-stu-id="189fa-287">Default Value</span></span> | <span data-ttu-id="189fa-288">说明</span><span class="sxs-lookup"><span data-stu-id="189fa-288">Description</span></span> |
|----------|----------|----------|----------|
| <span data-ttu-id="189fa-289">MixerMode</span><span class="sxs-lookup"><span data-stu-id="189fa-289">MixerMode</span></span> | <span data-ttu-id="189fa-290">UINT32</span><span class="sxs-lookup"><span data-stu-id="189fa-290">UINT32</span></span> | <span data-ttu-id="189fa-291">2 (麦克风和系统音频) </span><span class="sxs-lookup"><span data-stu-id="189fa-291">2 (Mic and System audio)</span></span> | <span data-ttu-id="189fa-292">用于指示应使用的音频源的枚举： 0 (Mic 音频) ，1 (系统音频仅) ，2 (Mic 和系统音频) </span><span class="sxs-lookup"><span data-stu-id="189fa-292">Enum used to indicate which audio sources should be used: 0 (Mic audio only), 1 (System audio only), 2 (Mic and System audio)</span></span> |
| <span data-ttu-id="189fa-293">LoopbackGain</span><span class="sxs-lookup"><span data-stu-id="189fa-293">LoopbackGain</span></span> | <span data-ttu-id="189fa-294">FLOAT</span><span class="sxs-lookup"><span data-stu-id="189fa-294">float</span></span> | <span data-ttu-id="189fa-295">Windows 设备门户中的 **应用音频增益** 设置</span><span class="sxs-lookup"><span data-stu-id="189fa-295">**App Audio Gain** setting in the Windows Device Portal</span></span> | <span data-ttu-id="189fa-296">适用于系统音频音量的增益。</span><span class="sxs-lookup"><span data-stu-id="189fa-296">Gain to apply to system audio volume.</span></span> <span data-ttu-id="189fa-297">范围为0.0 到5.0。</span><span class="sxs-lookup"><span data-stu-id="189fa-297">Ranges from 0.0 to 5.0.</span></span> <span data-ttu-id="189fa-298">仅在 HoloLens 2 上受支持</span><span class="sxs-lookup"><span data-stu-id="189fa-298">Only supported on HoloLens 2</span></span> |
| <span data-ttu-id="189fa-299">MicrophoneGain</span><span class="sxs-lookup"><span data-stu-id="189fa-299">MicrophoneGain</span></span> | <span data-ttu-id="189fa-300">FLOAT</span><span class="sxs-lookup"><span data-stu-id="189fa-300">float</span></span> | <span data-ttu-id="189fa-301">Windows 设备门户中的 **Mic 音频增益** 设置</span><span class="sxs-lookup"><span data-stu-id="189fa-301">**Mic Audio Gain** setting in the Windows Device Portal</span></span> | <span data-ttu-id="189fa-302">适用于麦克风音量的增益。</span><span class="sxs-lookup"><span data-stu-id="189fa-302">Gain to apply to mic volume.</span></span> <span data-ttu-id="189fa-303">范围为0.0 到5.0。</span><span class="sxs-lookup"><span data-stu-id="189fa-303">Ranges from 0.0 to 5.0.</span></span> <span data-ttu-id="189fa-304">仅在 HoloLens 2 上受支持</span><span class="sxs-lookup"><span data-stu-id="189fa-304">Only supported on HoloLens 2</span></span> |

>[!NOTE]
> <span data-ttu-id="189fa-305">可以通过转到 [混合现实捕获页面](using-the-windows-device-portal.md#mixed-reality-capture)并调整其各自设置旁的滑块来更改 Windows 设备门户中 **LoopbackGain** 或 **MicrophoneGain** 的默认值。</span><span class="sxs-lookup"><span data-stu-id="189fa-305">You can change the default value of **LoopbackGain** or **MicrophoneGain** in the Windows Device Portal by going to the [Mixed Reality Capture page](using-the-windows-device-portal.md#mixed-reality-capture) and adjusting the slider next to their respective settings.</span></span> <span data-ttu-id="189fa-306">这两个设置默认为 **1.0**，但可以设置为 **0.0** 和 **5.0** 之间的任何值。</span><span class="sxs-lookup"><span data-stu-id="189fa-306">Both settings default to **1.0**, but can be set to any value between **0.0** and **5.0**.</span></span>
>
> <span data-ttu-id="189fa-307">在2020年6月的更新中，使用 Windows 设备门户配置默认增益 (Windows 全息版、版本2004版本19041.1106 和 Windows 全息版 1903 build 18362.1064) 。</span><span class="sxs-lookup"><span data-stu-id="189fa-307">Using Windows Device Portal to configure the default gain values was added with the June 2020 update (Windows Holographic, version 2004 build 19041.1106 and Windows Holographic, version 1903 build 18362.1064).</span></span>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="189fa-308">同时 MRC 限制</span><span class="sxs-lookup"><span data-stu-id="189fa-308">Simultaneous MRC limitations</span></span>

<span data-ttu-id="189fa-309">如果多个应用同时访问了 MRC，则需要了解某些限制。</span><span class="sxs-lookup"><span data-stu-id="189fa-309">You need to be aware of certain limitations when multiple apps are accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="189fa-310">照片/视频相机访问</span><span class="sxs-lookup"><span data-stu-id="189fa-310">Photo/video camera access</span></span>

<span data-ttu-id="189fa-311">在 HoloLens 1 上，在某个进程录制视频或拍摄照片时，MRC 将无法捕获照片或捕获视频。</span><span class="sxs-lookup"><span data-stu-id="189fa-311">On HoloLens 1, MRC will fail to capture a photo or capture video while a process is recording video or taking a photo.</span></span> <span data-ttu-id="189fa-312">反之亦然：如果 MRC 正在运行，则应用程序将无法访问相机。</span><span class="sxs-lookup"><span data-stu-id="189fa-312">The reverse is also true: if MRC is running, the application will fail to get access to the camera.</span></span> 

<span data-ttu-id="189fa-313">使用 HoloLens 2，可以共享对相机的访问。</span><span class="sxs-lookup"><span data-stu-id="189fa-313">With HoloLens 2, it's possible for you to share access to the camera.</span></span> <span data-ttu-id="189fa-314">如果不需要直接控制分辨率或帧速率，则可以使用 [SharedMode 属性](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) 和 SharedReadOnly 初始化 MediaCapture。</span><span class="sxs-lookup"><span data-stu-id="189fa-314">If you don't need direct control of the resolution or frame-rate, you can initialize MediaCapture using the [SharedMode property](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) with SharedReadOnly.</span></span>  

##### <a name="built-in-mrc-photovideo-camera-access"></a><span data-ttu-id="189fa-315">内置的 MRC 照片/视频相机访问</span><span class="sxs-lookup"><span data-stu-id="189fa-315">Built-in MRC photo/video camera access</span></span>

<span data-ttu-id="189fa-316">通过 Cortana、开始菜单、硬件快捷方式、Miracast、Windows 设备门户) 内置于 Windows 10 (的 MRC 功能：</span><span class="sxs-lookup"><span data-stu-id="189fa-316">MRC functionality built into Windows 10 (via Cortana, Start Menu, hardware shortcuts, Miracast, Windows Device Portal):</span></span>

* <span data-ttu-id="189fa-317">默认情况下，将使用 ExclusiveControl 运行</span><span class="sxs-lookup"><span data-stu-id="189fa-317">Will run with ExclusiveControl by default</span></span>

<span data-ttu-id="189fa-318">但是，已将支持添加到 MRC 子系统以在共享模式下运行：</span><span class="sxs-lookup"><span data-stu-id="189fa-318">However, support has been added to MRC subsystem to operate in a shared mode:</span></span> 

* <span data-ttu-id="189fa-319">如果应用请求 ExclusiveControl 访问照片/视频摄像机，内置的 MRC 会自动停止使用照片/视频相机，因此应用的请求将会成功。</span><span class="sxs-lookup"><span data-stu-id="189fa-319">If an app requests ExclusiveControl access to the photo/video camera, built-in MRC will automatically stop using the photo/video camera so the app's request will succeed</span></span> 
* <span data-ttu-id="189fa-320">如果在应用具有 ExclusiveControl 的情况下启动了内置的 MRC，内置的 MRC 将在 SharedReadOnly 模式下运行</span><span class="sxs-lookup"><span data-stu-id="189fa-320">If built in MRC is started while an app has ExclusiveControl, built-in MRC will run in SharedReadOnly mode</span></span> 

<span data-ttu-id="189fa-321">此共享模式功能有一些限制：</span><span class="sxs-lookup"><span data-stu-id="189fa-321">This shared mode functionality has certain restrictions:</span></span>

* <span data-ttu-id="189fa-322">照片通过 Cortana、硬件快捷方式或 "开始" 菜单：需要 Windows 10 2018 年4月更新 (或更高版本) </span><span class="sxs-lookup"><span data-stu-id="189fa-322">Photo via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="189fa-323">视频 via Cortana、硬件快捷方式或 "开始" 菜单：需要 Windows 10 2018 年4月更新 (或更高版本) </span><span class="sxs-lookup"><span data-stu-id="189fa-323">Video via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="189fa-324">通过 Miracast 流式处理 MRC：需要 Windows 10 10 月2018更新 (或更高版本) </span><span class="sxs-lookup"><span data-stu-id="189fa-324">Streaming MRC over Miracast: Requires the Windows 10 October 2018 Update (or later)</span></span>
* <span data-ttu-id="189fa-325">通过 Windows 设备门户或 HoloLens 随附应用的流式处理 MRC：需要 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="189fa-325">Streaming MRC over Windows Device Portal or via the HoloLens companion app: Requires HoloLens 2</span></span>

>[!NOTE]
> <span data-ttu-id="189fa-326">当另一个应用正在使用 photo/视频摄像机时，内置 MRC 相机 UI 的分辨率和帧速率可能会从其正常值中减少。</span><span class="sxs-lookup"><span data-stu-id="189fa-326">The resolution and frame-rate of the built-in MRC camera UI might be reduced from its normal values when another app is using the photo/video camera.</span></span>

#### <a name="mrc-access-for-developers"></a><span data-ttu-id="189fa-327">开发人员的 MRC 访问</span><span class="sxs-lookup"><span data-stu-id="189fa-327">MRC access for developers</span></span>

<span data-ttu-id="189fa-328">建议你始终在使用 MRC 时请求对相机进行独占控制。</span><span class="sxs-lookup"><span data-stu-id="189fa-328">We recommend you always request Exclusive control for the camera when using MRC.</span></span> <span data-ttu-id="189fa-329">这将确保你的应用程序可以完全控制照相机的设置，前提是你知道上面列出的限制。</span><span class="sxs-lookup"><span data-stu-id="189fa-329">This will ensure your application has full control of the settings for the camera as long as you're aware of the limitations listed above.</span></span> 

* <span data-ttu-id="189fa-330">使用[初始化设置](/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041)创建媒体捕获对象</span><span class="sxs-lookup"><span data-stu-id="189fa-330">Create a media capture object using the [initialization settings](/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041)</span></span>
* <span data-ttu-id="189fa-331">将 [SharingMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode) 属性设置为 **exclusive**</span><span class="sxs-lookup"><span data-stu-id="189fa-331">Set the [SharingMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode) property to **exclusive**</span></span>

> [!CAUTION]
> <span data-ttu-id="189fa-332">继续操作之前，请务必仔细阅读 [SharingMode 备注](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks) 。</span><span class="sxs-lookup"><span data-stu-id="189fa-332">Be sure to carefully read the [SharingMode remarks](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks) before continuing.</span></span>

* <span data-ttu-id="189fa-333">按所需方式设置照相机</span><span class="sxs-lookup"><span data-stu-id="189fa-333">Set up your camera the way you want it</span></span>
* <span data-ttu-id="189fa-334">启动应用，使用启动 API 捕获视频帧，然后启用 MRC</span><span class="sxs-lookup"><span data-stu-id="189fa-334">Start the app, capture video frames with the start API, then enable MRC</span></span>

> [!CAUTION]
> <span data-ttu-id="189fa-335">如果在启动应用之前启动了 MRC，我们无法保证功能将按预期工作。</span><span class="sxs-lookup"><span data-stu-id="189fa-335">If you start MRC before you start your app, we can't guarantee the feature will work as expected.</span></span>

<span data-ttu-id="189fa-336">你可以在 [全息面跟踪示例](/samples/microsoft/windows-universal-samples/holographicfacetracking)中找到上述过程的完整示例。</span><span class="sxs-lookup"><span data-stu-id="189fa-336">You can find a full sample of the above process in the [holographic face tracking sample](/samples/microsoft/windows-universal-samples/holographicfacetracking).</span></span>

> [!NOTE]
> <span data-ttu-id="189fa-337">在 Windows 10 2018 年4月更新之前，应用程序的自定义 MRC 记录器与系统 MRC 互斥， (从 Windows 设备门户) 捕获照片、捕获视频或流式处理。</span><span class="sxs-lookup"><span data-stu-id="189fa-337">Before the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="189fa-338">请参阅</span><span class="sxs-lookup"><span data-stu-id="189fa-338">See also</span></span>

* [<span data-ttu-id="189fa-339">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="189fa-339">Mixed reality capture</span></span>](/hololens/holographic-photos-and-videos)
* [<span data-ttu-id="189fa-340">旁观视图</span><span class="sxs-lookup"><span data-stu-id="189fa-340">Spectator view</span></span>](spectator-view.md)
* [<span data-ttu-id="189fa-341">Unity 开发概述</span><span class="sxs-lookup"><span data-stu-id="189fa-341">Unity Development Overview</span></span>](../unity/unity-development-overview.md)
* [<span data-ttu-id="189fa-342">Unreal 开发概述</span><span class="sxs-lookup"><span data-stu-id="189fa-342">Unreal development overview</span></span>](../unreal/unreal-development-overview.md)
