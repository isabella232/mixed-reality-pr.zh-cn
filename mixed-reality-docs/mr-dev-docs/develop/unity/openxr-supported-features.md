---
title: OpenXR 插件支持 Unity 中的功能
description: 发现 OpenXR 支持 Unity 中混合现实开发的功能。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，扩充现实，虚拟现实，混合现实耳机，学习，教程，入门
ms.openlocfilehash: e622cd617ccf67c0877b9064efe791743e4c34b6
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333369"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="73a68-104">混合现实 OpenXR 支持 Unity 中的功能</span><span class="sxs-lookup"><span data-stu-id="73a68-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="73a68-105">**Mixed Reality OpenXR 插件** 包是 Unity 的 **OpenXR 插件** 的扩展，支持用于 HoloLens 2 和 Windows Mixed Reality 耳机的一套功能。</span><span class="sxs-lookup"><span data-stu-id="73a68-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="73a68-106">在继续之前，请确保已 [为 OpenXR 配置](openxr-getting-started.md)了 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="73a68-106">Before continuing, make sure your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="73a68-107">支持的操作</span><span class="sxs-lookup"><span data-stu-id="73a68-107">What's supported</span></span>

<span data-ttu-id="73a68-108">目前支持以下功能：</span><span class="sxs-lookup"><span data-stu-id="73a68-108">The following features are currently supported:</span></span>

* <span data-ttu-id="73a68-109">支持 HoloLens 2 的 UWP 应用程序，并针对 HoloLens 2 应用程序模型进行优化。</span><span class="sxs-lookup"><span data-stu-id="73a68-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="73a68-110">支持适用于 Windows Mixed Reality 耳机的 Win32 VR 应用程序，包含最新控制器配置文件和全息应用远程处理。</span><span class="sxs-lookup"><span data-stu-id="73a68-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="73a68-111">使用定位点和无限空间进行世界规模跟踪。</span><span class="sxs-lookup"><span data-stu-id="73a68-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="73a68-112">[用于将定位点保存](spatial-anchors-in-unity.md) 到 HoloLens 2 本地存储的定位存储 API。</span><span class="sxs-lookup"><span data-stu-id="73a68-112">[Anchor storage API to persist anchors](spatial-anchors-in-unity.md) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="73a68-113">[运动控制器和手动交互](#motion-controller-and-hand-interactions)，包括新的 HP 回音 G2 控制器。</span><span class="sxs-lookup"><span data-stu-id="73a68-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="73a68-114">使用26个接合和接点输入的有向右跟踪。</span><span class="sxs-lookup"><span data-stu-id="73a68-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="73a68-115">HoloLens 2 上的目视注视交互。</span><span class="sxs-lookup"><span data-stu-id="73a68-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="73a68-116">在 HoloLens 2 上查找 (PV) 相机的照片/视频。</span><span class="sxs-lookup"><span data-stu-id="73a68-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="73a68-117">混合现实通过 PV 相机使用第三种目视渲染来捕获。</span><span class="sxs-lookup"><span data-stu-id="73a68-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="73a68-118">支持 [通过全息远程处理应用 "播放" 到 HoloLens 2](unity-play-mode.md#holographic-remoting-in-unity-editor-play-mode)，使开发人员无需生成并部署到设备即可调试脚本。</span><span class="sxs-lookup"><span data-stu-id="73a68-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](unity-play-mode.md#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="73a68-119">与 MRTK Unity 2.5.3 和更高版本通过 [MRTK OpenXR 提供程序支持](openxr-getting-started.md#using-mrtk-with-openxr-support)兼容。</span><span class="sxs-lookup"><span data-stu-id="73a68-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="73a68-120">与 Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 或更高版本兼容。</span><span class="sxs-lookup"><span data-stu-id="73a68-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="73a68-121"> (在 0.1.3) 中添加的功能支持从生成和部署的 Windows 独立应用进行 [桌面应用全息远程处理](holographic-remoting-desktop.md) 。</span><span class="sxs-lookup"><span data-stu-id="73a68-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](holographic-remoting-desktop.md) from a built and deployed Windows Standalone app.</span></span>
* <span data-ttu-id="73a68-122"> (0.1.4) 支持通过 SpatialGraphNode 在 HoloLens2 上跟踪 [QR](#qr-codes) 码</span><span class="sxs-lookup"><span data-stu-id="73a68-122">(Added in 0.1.4) Supports [QR code tracking](#qr-codes) on HoloLens2 through SpatialGraphNode</span></span>
* <span data-ttu-id="73a68-123"> (0.2.0 中添加) 支持 **全息** 远程处理中的定位点</span><span class="sxs-lookup"><span data-stu-id="73a68-123">(Added in 0.2.0) Supports **Anchor** in Holographic Remoting</span></span>
* <span data-ttu-id="73a68-124"> (0.2.0) 支持手部和 **手部网格跟踪**</span><span class="sxs-lookup"><span data-stu-id="73a68-124">(Added in 0.2.0) Supports both **hand joints and hand mesh tracking**</span></span>
* <span data-ttu-id="73a68-125"> (0.2.0) 支持使用 ARRaycastManager 进行平面检测和放置全息影像的 **ARPlaneSubsystems。** </span><span class="sxs-lookup"><span data-stu-id="73a68-125">(Added in 0.2.0) Supports **ARPlaneSubsystems** for plane detection and place hologram using **ARRaycastManager**.</span></span>
* <span data-ttu-id="73a68-126"> (0.9.0) 支持 **XRMeshSubsystem** 和 **ARMeshManager** 进行空间映射。</span><span class="sxs-lookup"><span data-stu-id="73a68-126">(0.9.0) Supports **XRMeshSubsystem** and **ARMeshManager** for spatial mapping.</span></span>
* <span data-ttu-id="73a68-127"> (0.9.0 中) 支持适用于 Windows 的 Azure 空间定位点 SDK 插件。</span><span class="sxs-lookup"><span data-stu-id="73a68-127">(Added in 0.9.0) Supports the Azure Spatial Anchors SDK for Windows plugin.</span></span> <span data-ttu-id="73a68-128">有关详细信息，请参阅 [GitHub 上的混合现实 + OpenXR Azure 空间定位点示例项目](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample)。</span><span class="sxs-lookup"><span data-stu-id="73a68-128">For more information, see the [Mixed Reality + OpenXR Azure Spatial Anchors sample project on GitHub](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample).</span></span>
* <span data-ttu-id="73a68-129"> (0.9.1) 支持从生成和部署的 Windows UWP 应用进行桌面应用全息远程处理。</span><span class="sxs-lookup"><span data-stu-id="73a68-129">(Added in 0.9.1) Supports desktop app Holographic Remoting from a built and deployed Windows UWP app.</span></span>
* <span data-ttu-id="73a68-130"> (0.9.4 版中添加) 支持 ARM 平台以及 ARM64 for HoloLens 2 应用程序。</span><span class="sxs-lookup"><span data-stu-id="73a68-130">(Added in 0.9.4) Supports ARM platform in addition to ARM64 for HoloLens 2 application.</span></span>

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="73a68-131">运动控制器和手部交互</span><span class="sxs-lookup"><span data-stu-id="73a68-131">Motion controller and hand interactions</span></span>

<span data-ttu-id="73a68-132">若要了解有关 Unity 中混合现实交互的基础知识，请访问 [Unity XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)输入的 Unity 手册。</span><span class="sxs-lookup"><span data-stu-id="73a68-132">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="73a68-133">此 Unity 文档介绍了从控制器特定的输入到更通用 **InputFeatureUsage** 的映射、如何标识和分类可用的 XR 输入、如何从这些输入读取数据，等等。</span><span class="sxs-lookup"><span data-stu-id="73a68-133">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="73a68-134">混合现实 OpenXR 插件提供映射到标准 **InputFeatureUsage** 的其他输入交互配置文件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="73a68-134">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="73a68-135">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="73a68-135">InputFeatureUsage</span></span> | <span data-ttu-id="73a68-136">HP Reverb G2 控制器 (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="73a68-136">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="73a68-137">HoloLens Hand (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="73a68-137">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="73a68-138">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="73a68-138">primary2DAxis</span></span> | <span data-ttu-id="73a68-139">操纵 杆</span><span class="sxs-lookup"><span data-stu-id="73a68-139">Joystick</span></span> | |
| <span data-ttu-id="73a68-140">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="73a68-140">primary2DAxisClick</span></span> | <span data-ttu-id="73a68-141">下一步 - 单击</span><span class="sxs-lookup"><span data-stu-id="73a68-141">Joystick - Click</span></span> | |
| <span data-ttu-id="73a68-142">触发器</span><span class="sxs-lookup"><span data-stu-id="73a68-142">trigger</span></span> | <span data-ttu-id="73a68-143">触发器</span><span class="sxs-lookup"><span data-stu-id="73a68-143">Trigger</span></span>  | |
| <span data-ttu-id="73a68-144">调整</span><span class="sxs-lookup"><span data-stu-id="73a68-144">grip</span></span> | <span data-ttu-id="73a68-145">调整</span><span class="sxs-lookup"><span data-stu-id="73a68-145">Grip</span></span> | <span data-ttu-id="73a68-146">空中分流或挤压</span><span class="sxs-lookup"><span data-stu-id="73a68-146">Air tap or squeeze</span></span> |
| <span data-ttu-id="73a68-147">primaryButton</span><span class="sxs-lookup"><span data-stu-id="73a68-147">primaryButton</span></span> | <span data-ttu-id="73a68-148">[X/A]-按</span><span class="sxs-lookup"><span data-stu-id="73a68-148">[X/A] - Press</span></span> | <span data-ttu-id="73a68-149">隔空敲击</span><span class="sxs-lookup"><span data-stu-id="73a68-149">Air tap</span></span> |
| <span data-ttu-id="73a68-150">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="73a68-150">secondaryButton</span></span> | <span data-ttu-id="73a68-151">[Y/B]-按</span><span class="sxs-lookup"><span data-stu-id="73a68-151">[Y/B] - Press</span></span> | |
| <span data-ttu-id="73a68-152">gripButton</span><span class="sxs-lookup"><span data-stu-id="73a68-152">gripButton</span></span> | <span data-ttu-id="73a68-153">手柄-按</span><span class="sxs-lookup"><span data-stu-id="73a68-153">Grip - Press</span></span> | |
| <span data-ttu-id="73a68-154">triggerButton</span><span class="sxs-lookup"><span data-stu-id="73a68-154">triggerButton</span></span> | <span data-ttu-id="73a68-155">触发器-按</span><span class="sxs-lookup"><span data-stu-id="73a68-155">Trigger - Press</span></span> | |
| <span data-ttu-id="73a68-156">menuButton</span><span class="sxs-lookup"><span data-stu-id="73a68-156">menuButton</span></span> | <span data-ttu-id="73a68-157">菜单</span><span class="sxs-lookup"><span data-stu-id="73a68-157">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="73a68-158">瞄准并抓住姿势</span><span class="sxs-lookup"><span data-stu-id="73a68-158">Aim and Grip Poses</span></span>

<span data-ttu-id="73a68-159">通过 OpenXR 输入交互可以访问两组姿势：</span><span class="sxs-lookup"><span data-stu-id="73a68-159">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="73a68-160">用于呈现对象的手柄姿势</span><span class="sxs-lookup"><span data-stu-id="73a68-160">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="73a68-161">目标是指进入世界。</span><span class="sxs-lookup"><span data-stu-id="73a68-161">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="73a68-162">有关此设计的详细信息以及这两个姿势之间的差异，请参阅 [OpenXR 规范输入子路径](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)。</span><span class="sxs-lookup"><span data-stu-id="73a68-162">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="73a68-163">InputFeatureUsages **DevicePosition**、 **DeviceRotation**、 **DeviceVelocity** 和 **DeviceAngularVelocity** 提供的姿势都代表了 OpenXR **手柄** 的姿势。</span><span class="sxs-lookup"><span data-stu-id="73a68-163">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="73a68-164">与手柄姿势相关的 InputFeatureUsages 在 Unity 的 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)中定义。</span><span class="sxs-lookup"><span data-stu-id="73a68-164">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="73a68-165">InputFeatureUsages **PointerPosition**、 **PointerRotation**、 **PointerVelocity** 和 **PointerAngularVelocity** 提供的姿势均代表 OpenXR **aim** 姿势。</span><span class="sxs-lookup"><span data-stu-id="73a68-165">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="73a68-166">这些 InputFeatureUsages 未在任何包含的 C# 文件中定义，因此需要定义自己的 InputFeatureUsages，如下所示：</span><span class="sxs-lookup"><span data-stu-id="73a68-166">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="73a68-167">Haptics</span><span class="sxs-lookup"><span data-stu-id="73a68-167">Haptics</span></span>

<span data-ttu-id="73a68-168">有关在 Unity 的 XR 输入系统中使用 haptics 的信息，请参阅 Unity Manual [for Unity XR Input - Haptics （Unity XR 输入 - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)的 Unity 手册）。</span><span class="sxs-lookup"><span data-stu-id="73a68-168">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="qr-codes"></a><span data-ttu-id="73a68-169">QR 码</span><span class="sxs-lookup"><span data-stu-id="73a68-169">QR codes</span></span>

<span data-ttu-id="73a68-170">HoloLens 2 可以检测头戴显示设备周围环境中的 QR 码，从而在每个代码的真实位置建立坐标系统。</span><span class="sxs-lookup"><span data-stu-id="73a68-170">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="73a68-171">可以在 QR 代码跟踪 [文档中找到更多详细信息](../platform-capabilities-and-apis/qr-code-tracking.md) 。</span><span class="sxs-lookup"><span data-stu-id="73a68-171">You can find more details in our [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) documentation.</span></span>  <span data-ttu-id="73a68-172">使用 OpenXR 插件时，从[ `SpatialGraphNodeId` QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference)获取 ，并使用 `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API 查找 QR 代码。</span><span class="sxs-lookup"><span data-stu-id="73a68-172">When using the OpenXR plugin, grab the [`SpatialGraphNodeId` from the QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) and use the `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API to locate the QR code.</span></span>

<span data-ttu-id="73a68-173">有关参考，我们在 GitHub 上提供了一个[QR](https://github.com/yl-msft/QRTracking)跟踪示例项目，并详细介绍[ `SpatialGraphNode` 了 API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)的用法说明。</span><span class="sxs-lookup"><span data-stu-id="73a68-173">For reference, we have a [QR tracking sample project on GitHub](https://github.com/yl-msft/QRTracking) with more a detailed usage explanation for the [`SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="73a68-174">疑难解答</span><span class="sxs-lookup"><span data-stu-id="73a68-174">Troubleshooting</span></span>

<span data-ttu-id="73a68-175">当在 HoloLens 2 上挂起和恢复 Unity 应用时，该应用无法正确恢复，这会导致 HoloLens 视图中出现 4 个旋转点。</span><span class="sxs-lookup"><span data-stu-id="73a68-175">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="73a68-176">将 **OpenXR** **项目设置中的** "深度提交模式"设置为"无"作为解决方法</span><span class="sxs-lookup"><span data-stu-id="73a68-176">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
