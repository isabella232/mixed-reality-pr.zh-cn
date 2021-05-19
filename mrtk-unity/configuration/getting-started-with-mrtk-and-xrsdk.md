---
title: 与 MRTK 和 XRSDK 入门
description: XRSDK 的 MRTK 的登陆页
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，XRSDK，
ms.openlocfilehash: ef6d8c9205a9d801e8cb0ec2690d77b74c72b5fb
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143523"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="82943-104">MRTK 和 XR SDK 入门</span><span class="sxs-lookup"><span data-stu-id="82943-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="82943-105">XR SDK 是 unity [2019.3 和更高版本中的 unity 新 XR 管道](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)。</span><span class="sxs-lookup"><span data-stu-id="82943-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="82943-106">在 Unity 2019 中，它可替代现有的 XR 管道。</span><span class="sxs-lookup"><span data-stu-id="82943-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="82943-107">在 Unity 2020 中，它将成为 Unity 中唯一的 XR 管道。</span><span class="sxs-lookup"><span data-stu-id="82943-107">In Unity 2020, it will become the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="82943-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="82943-108">Prerequisites</span></span>

<span data-ttu-id="82943-109">若要开始使用混合现实工具包，请按照 [提供的步骤](../install-the-tools.md#importing-the-mixed-reality-toolkit) 将 MRTK 添加到项目。</span><span class="sxs-lookup"><span data-stu-id="82943-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="82943-110">为 XR SDK 管道配置 Unity</span><span class="sxs-lookup"><span data-stu-id="82943-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="82943-111">XR SDK 管道当前支持3个平台： Windows Mixed Reality、Oculus 和 OpenXR。</span><span class="sxs-lookup"><span data-stu-id="82943-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="82943-112">以下各节将介绍为每个平台配置 XR SDK 所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="82943-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="82943-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="82943-113">Windows Mixed Reality</span></span>

<span data-ttu-id="82943-114">进入 **Unity 的包管理器** 并安装 Windows XR 插件包，其中添加了对 XR SDK 上 Windows Mixed Reality 的支持。</span><span class="sxs-lookup"><span data-stu-id="82943-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="82943-115">这也会提取一些依赖项包。</span><span class="sxs-lookup"><span data-stu-id="82943-115">This will pull down a few dependency packages as well.</span></span> 

1. <span data-ttu-id="82943-116">确保已成功安装以下所有内容：</span><span class="sxs-lookup"><span data-stu-id="82943-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="82943-117">XR 插件管理</span><span class="sxs-lookup"><span data-stu-id="82943-117">XR Plugin Management</span></span>
   * <span data-ttu-id="82943-118">Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="82943-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="82943-119">XR 旧版输入帮助程序</span><span class="sxs-lookup"><span data-stu-id="82943-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="82943-120">转到“编辑”>“项目设置”。</span><span class="sxs-lookup"><span data-stu-id="82943-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="82943-121">单击 "项目设置" 窗口中的 XR 插件管理选项卡。</span><span class="sxs-lookup"><span data-stu-id="82943-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="82943-122">请访问 "通用 Windows 平台设置"，并确保在 "插件提供程序" 下选中 "Windows Mixed Reality"。</span><span class="sxs-lookup"><span data-stu-id="82943-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="82943-123">请确保已选中 "在启动时初始化 XR"。</span><span class="sxs-lookup"><span data-stu-id="82943-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="82943-124"> (**_编辑器中的 HoloLens 远程_** 处理是必需的，否则为可选) 转到"独立"设置，并确保Windows Mixed Reality插件提供程序下选中了"设置"。</span><span class="sxs-lookup"><span data-stu-id="82943-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="82943-125">另请确保选中"启动时初始化 XR"。</span><span class="sxs-lookup"><span data-stu-id="82943-125">Also ensure that Initialize XR on Startup is checked.</span></span>

![选中"独立"选项卡的 XR 插件管理](images/xr-management-img-02.png)

7. <span data-ttu-id="82943-127"> (**_可选_**) 单击"XR 插件管理"下的"Windows Mixed Reality"选项卡，并创建自定义设置配置文件以更改默认值。</span><span class="sxs-lookup"><span data-stu-id="82943-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="82943-128">如果设置列表已存在，则无需创建配置文件。</span><span class="sxs-lookup"><span data-stu-id="82943-128">If the list of settings are already there, no profile needs to be created.</span></span>

![选中 Windows 选项卡的 XR 插件管理](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="82943-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="82943-130">Oculus</span></span>

1. <span data-ttu-id="82943-131">按照 [如何使用 XR SDK 管道在 MRTK](../supported-devices/oculus-quest-mrtk.md) 中配置 Oculus Quest 指南操作到最后。</span><span class="sxs-lookup"><span data-stu-id="82943-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="82943-132">本指南概述了将 Unity 和 MRTK 配置为使用 Oculus Quest 的 XR SDK 管道所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="82943-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="82943-133">OpenXR (预览) </span><span class="sxs-lookup"><span data-stu-id="82943-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="82943-134">Unity 中的 OpenXR 仅在 Unity 2020.2 及更高版本上受支持。</span><span class="sxs-lookup"><span data-stu-id="82943-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
>
> <span data-ttu-id="82943-135">目前，它还仅支持 x64 和 ARM64 生成。</span><span class="sxs-lookup"><span data-stu-id="82943-135">Currently, it also only supports x64 and ARM64 builds.</span></span>

1. <span data-ttu-id="82943-136">按照 [使用适用于 Unity 的混合现实 OpenXR 插件](/windows/mixed-reality/develop/unity/openxr-getting-started) 指南操作，包括配置 XR 插件管理和优化的步骤，将 OpenXR 插件安装到项目中。</span><span class="sxs-lookup"><span data-stu-id="82943-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="82943-137">确保已成功安装以下内容：</span><span class="sxs-lookup"><span data-stu-id="82943-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="82943-138">XR 插件管理</span><span class="sxs-lookup"><span data-stu-id="82943-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="82943-139">OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="82943-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="82943-140">混合现实 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="82943-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="82943-141">转到"编辑>项目设置"。</span><span class="sxs-lookup"><span data-stu-id="82943-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="82943-142">单击"项目设置"窗口中的"XR 插件管理"选项卡。</span><span class="sxs-lookup"><span data-stu-id="82943-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="82943-143">确保选中"启动时初始化 XR"。</span><span class="sxs-lookup"><span data-stu-id="82943-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="82943-144"> (**_可选_**) 如果面向 HoloLens 2，请确保位于 UWP 平台上，并选择 "Microsoft HoloLens 功能集"</span><span class="sxs-lookup"><span data-stu-id="82943-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![插件管理打开 XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="82943-146">如果预先存在的项目正在使用 MRTK 与 UPM，请确保以下行位于 MixedRealityToolkit 文件夹中的 **link.xml** 文件中。</span><span class="sxs-lookup"><span data-stu-id="82943-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="82943-147">对于 MRTK 和 OpenXR 的初始版本，仅支持 HoloLens 2 表述的手势和 Windows Mixed Reality 运动控制器。</span><span class="sxs-lookup"><span data-stu-id="82943-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="82943-148">未来版本中将添加对其他硬件的支持。</span><span class="sxs-lookup"><span data-stu-id="82943-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="82943-149">为 XR SDK 管道配置 MRTK</span><span class="sxs-lookup"><span data-stu-id="82943-149">Configuring MRTK for the XR SDK pipeline</span></span>

<span data-ttu-id="82943-150">如果使用的是 OpenXR，请选择 "DefaultOpenXRConfigurationProfile" 作为活动配置文件，或将其克隆以便进行自定义。</span><span class="sxs-lookup"><span data-stu-id="82943-150">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="82943-151">如果在 XR 插件管理配置（如 Windows Mixed Reality 或 Oculus）中使用其他 XR 运行时，请选择 "DefaultXRSDKConfigurationProfile" 作为活动配置文件，或将其克隆以便进行自定义。</span><span class="sxs-lookup"><span data-stu-id="82943-151">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="82943-152">这些配置文件在需要时设置为正确的系统和提供程序。</span><span class="sxs-lookup"><span data-stu-id="82943-152">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="82943-153">请参阅 [配置文件文档](../features/profiles/profiles.md#xr-sdk) ，以了解有关 XR SDK 的配置文件和示例支持的详细信息。</span><span class="sxs-lookup"><span data-stu-id="82943-153">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>

<span data-ttu-id="82943-154">若要将现有配置文件迁移到 XR SDK，应更新以下服务和数据提供程序：</span><span class="sxs-lookup"><span data-stu-id="82943-154">To migrate an existing profile to XR SDK, the following services and data providers should be updated:</span></span>

### <a name="camera"></a><span data-ttu-id="82943-155">照相机</span><span class="sxs-lookup"><span data-stu-id="82943-155">Camera</span></span>

<span data-ttu-id="82943-156">从 [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="82943-156">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![旧照相机设置](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="82943-158">to</span><span class="sxs-lookup"><span data-stu-id="82943-158">to</span></span>

| <span data-ttu-id="82943-159">OpenXR</span><span class="sxs-lookup"><span data-stu-id="82943-159">OpenXR</span></span> | <span data-ttu-id="82943-160">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="82943-160">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | <span data-ttu-id="82943-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**和**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="82943-161">[`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) **and** [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings)</span></span> |

![XR SDK 照相机设置](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="82943-163">输入</span><span class="sxs-lookup"><span data-stu-id="82943-163">Input</span></span>

<span data-ttu-id="82943-164">从 [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="82943-164">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![旧输入设置](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="82943-166">to</span><span class="sxs-lookup"><span data-stu-id="82943-166">to</span></span>

| <span data-ttu-id="82943-167">OpenXR</span><span class="sxs-lookup"><span data-stu-id="82943-167">OpenXR</span></span> | <span data-ttu-id="82943-168">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="82943-168">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="82943-169">__OpenXR__：</span><span class="sxs-lookup"><span data-stu-id="82943-169">__OpenXR__:</span></span>

![OpenXR 输入设置](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="82943-171">__Windows Mixed Reality__：</span><span class="sxs-lookup"><span data-stu-id="82943-171">__Windows Mixed Reality__:</span></span>

![XR SDK 输入设置](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="82943-173">边界</span><span class="sxs-lookup"><span data-stu-id="82943-173">Boundary</span></span>

<span data-ttu-id="82943-174">从 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="82943-174">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![旧边界设置](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="82943-176">to</span><span class="sxs-lookup"><span data-stu-id="82943-176">to</span></span>

| <span data-ttu-id="82943-177">OpenXR</span><span class="sxs-lookup"><span data-stu-id="82943-177">OpenXR</span></span> | <span data-ttu-id="82943-178">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="82943-178">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK 边界设置](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="82943-180">空间感知</span><span class="sxs-lookup"><span data-stu-id="82943-180">Spatial awareness</span></span>

<span data-ttu-id="82943-181">从 [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="82943-181">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![旧版空间感知设置](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="82943-183">to</span><span class="sxs-lookup"><span data-stu-id="82943-183">to</span></span>

| <span data-ttu-id="82943-184">OpenXR</span><span class="sxs-lookup"><span data-stu-id="82943-184">OpenXR</span></span> | <span data-ttu-id="82943-185">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="82943-185">Windows Mixed Reality</span></span> |
|--------|-----------------------|
| <span data-ttu-id="82943-186">正在学习</span><span class="sxs-lookup"><span data-stu-id="82943-186">In progress</span></span> | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![XR SDK 空间感知设置](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="82943-188">控制器映射</span><span class="sxs-lookup"><span data-stu-id="82943-188">Controller mappings</span></span>

<span data-ttu-id="82943-189">如果使用自定义控制器映射配置文件，请打开其中一个配置文件并运行混合现实工具包 -> 实用工具 -> Update -> 控制器映射配置文件菜单项，以确保定义新的 XR SDK 控制器类型。</span><span class="sxs-lookup"><span data-stu-id="82943-189">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="82943-190">另请参阅</span><span class="sxs-lookup"><span data-stu-id="82943-190">See also</span></span>

* [<span data-ttu-id="82943-191">Unity 中的 AR 开发入门</span><span class="sxs-lookup"><span data-stu-id="82943-191">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="82943-192">Unity 中的 VR 开发入门</span><span class="sxs-lookup"><span data-stu-id="82943-192">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)