---
title: MRTK 和 XR SDK 入门
description: MRTK with XR SDK 的登录页
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，XRSDK，XR SDK
ms.openlocfilehash: 01aca42ab4e883d26a814a1572d39eda7576ab57
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908382"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a><span data-ttu-id="c52f9-104">MRTK 和 XR SDK 入门</span><span class="sxs-lookup"><span data-stu-id="c52f9-104">Getting started with MRTK and XR SDK</span></span>

<span data-ttu-id="c52f9-105">XR SDK 是 unity [2019.3 和更高版本中的 unity 新 XR 管道](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)。</span><span class="sxs-lookup"><span data-stu-id="c52f9-105">XR SDK is Unity's [new XR pipeline in Unity 2019.3 and beyond](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/).</span></span> <span data-ttu-id="c52f9-106">在 Unity 2019 中，它可替代现有的 XR 管道。</span><span class="sxs-lookup"><span data-stu-id="c52f9-106">In Unity 2019, it provides an alternative to the existing XR pipeline.</span></span> <span data-ttu-id="c52f9-107">在 Unity 2020 中，它是 Unity 中唯一的 XR 管道。</span><span class="sxs-lookup"><span data-stu-id="c52f9-107">In Unity 2020, it is the only XR pipeline in Unity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c52f9-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="c52f9-108">Prerequisites</span></span>

<span data-ttu-id="c52f9-109">若要开始使用混合现实工具包，请按照 [提供的步骤](../install-the-tools.md#importing-the-mixed-reality-toolkit) 将 MRTK 添加到项目。</span><span class="sxs-lookup"><span data-stu-id="c52f9-109">To get started with the Mixed Reality Toolkit, follow [the provided steps](../install-the-tools.md#importing-the-mixed-reality-toolkit) to add MRTK to a project.</span></span>

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a><span data-ttu-id="c52f9-110">为 XR SDK 管道配置 Unity</span><span class="sxs-lookup"><span data-stu-id="c52f9-110">Configuring Unity for the XR SDK pipeline</span></span>

<span data-ttu-id="c52f9-111">XR SDK 管道当前支持3个平台： Windows Mixed Reality、Oculus 和 OpenXR。</span><span class="sxs-lookup"><span data-stu-id="c52f9-111">The XR SDK pipeline currently supports 3 platforms: Windows Mixed Reality, Oculus, and OpenXR.</span></span> <span data-ttu-id="c52f9-112">以下各节将介绍为每个平台配置 XR SDK 所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="c52f9-112">The sections below will cover the steps needed to configure XR SDK for each platform.</span></span>

### <a name="windows-mixed-reality"></a><span data-ttu-id="c52f9-113">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c52f9-113">Windows Mixed Reality</span></span>

<span data-ttu-id="c52f9-114">进入 **Unity 的包管理器** 并安装 Windows XR 插件包，其中添加了对 XR SDK 上 Windows Mixed Reality 的支持。</span><span class="sxs-lookup"><span data-stu-id="c52f9-114">Go into **Unity's Package Manager** and install the Windows XR Plugin package, which adds support for Windows Mixed Reality on XR SDK.</span></span> <span data-ttu-id="c52f9-115">这也会提取一些依赖项包。</span><span class="sxs-lookup"><span data-stu-id="c52f9-115">This will pull down a few dependency packages as well.</span></span>

1. <span data-ttu-id="c52f9-116">确保已成功安装以下所有内容：</span><span class="sxs-lookup"><span data-stu-id="c52f9-116">Ensure that the following all successfully installed:</span></span>
   * <span data-ttu-id="c52f9-117">XR 插件管理</span><span class="sxs-lookup"><span data-stu-id="c52f9-117">XR Plugin Management</span></span>
   * <span data-ttu-id="c52f9-118">Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="c52f9-118">Windows XR Plugin</span></span>
   * <span data-ttu-id="c52f9-119">XR 旧版输入帮助程序</span><span class="sxs-lookup"><span data-stu-id="c52f9-119">XR Legacy Input Helpers</span></span>

2. <span data-ttu-id="c52f9-120">转到“编辑”>“项目设置”。</span><span class="sxs-lookup"><span data-stu-id="c52f9-120">Go to **Edit > Project Settings**.</span></span>
3. <span data-ttu-id="c52f9-121">单击 "项目设置" 窗口中的 XR 插件管理选项卡。</span><span class="sxs-lookup"><span data-stu-id="c52f9-121">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
4. <span data-ttu-id="c52f9-122">请访问 "通用 Windows 平台设置"，并确保在 "插件提供程序" 下选中 "Windows Mixed Reality"。</span><span class="sxs-lookup"><span data-stu-id="c52f9-122">Go to the Universal Windows Platform settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span>
5. <span data-ttu-id="c52f9-123">请确保已选中 "在启动时初始化 XR"。</span><span class="sxs-lookup"><span data-stu-id="c52f9-123">Ensure that Initialize XR on Startup is checked.</span></span>
6. <span data-ttu-id="c52f9-124"> (**_编辑器内的 HoloLens 远程处理需要此项，否则) 选择_** "切换到独立设置，并确保在插件提供程序下检查 Windows Mixed Reality"。</span><span class="sxs-lookup"><span data-stu-id="c52f9-124">(**_Required for in-editor HoloLens Remoting, otherwise optional_**) Go to the Standalone settings and ensure Windows Mixed Reality is checked under Plug-in Providers.</span></span> <span data-ttu-id="c52f9-125">还要确保已选中 "在启动时初始化 XR"。</span><span class="sxs-lookup"><span data-stu-id="c52f9-125">Also ensure that Initialize XR on Startup is checked.</span></span>

    ![已选择 "独立" 选项卡的 XR 插件管理](images/xr-management-img-02.png)

7. <span data-ttu-id="c52f9-127"> (**_可选_**) 单击 "XR 插件管理" 下的 "Windows Mixed Reality" 选项卡，并创建自定义设置配置文件以更改默认值。</span><span class="sxs-lookup"><span data-stu-id="c52f9-127">(**_Optional_**) Click on the Windows Mixed Reality tab under XR Plug-in Management and create a custom settings profile to change the defaults.</span></span> <span data-ttu-id="c52f9-128">如果已存在设置列表，则无需创建配置文件。</span><span class="sxs-lookup"><span data-stu-id="c52f9-128">If the list of settings are already there, no profile needs to be created.</span></span>

    ![选择了 "Windows" 选项卡的 XR 插件管理](images/xr-management-img-01.png)

### <a name="oculus"></a><span data-ttu-id="c52f9-130">Oculus</span><span class="sxs-lookup"><span data-stu-id="c52f9-130">Oculus</span></span>

1. <span data-ttu-id="c52f9-131">按照 [如何使用 XR SDK 管道指南在 MRTK 中配置 Oculus 的](../supported-devices/oculus-quest-mrtk.md) 操作。</span><span class="sxs-lookup"><span data-stu-id="c52f9-131">Follow the [How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end.</span></span> <span data-ttu-id="c52f9-132">本指南概述了将 Unity 和 MRTK 配置为使用 XR SDK 管道进行 Oculus 寻找所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="c52f9-132">The guide outlines the steps needed to configure both Unity and MRTK to use the XR SDK pipeline for the Oculus Quest.</span></span>

### <a name="openxr-preview"></a><span data-ttu-id="c52f9-133">OpenXR (预览) </span><span class="sxs-lookup"><span data-stu-id="c52f9-133">OpenXR (Preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c52f9-134">Unity 中的 OpenXR 仅在 Unity 2020.2 和更高版本上受支持。</span><span class="sxs-lookup"><span data-stu-id="c52f9-134">OpenXR in Unity is only supported on Unity 2020.2 and higher.</span></span>
> <span data-ttu-id="c52f9-135">它还仅支持 x64、ARM 和 ARM64 生成。</span><span class="sxs-lookup"><span data-stu-id="c52f9-135">It also only supports x64, ARM, and ARM64 builds.</span></span>

1. <span data-ttu-id="c52f9-136">遵循 [使用 Mixed Reality OpenXR 插件了解 Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) 指南，其中包括配置 XR 插件管理和优化以将 OpenXR 插件安装到项目的步骤。</span><span class="sxs-lookup"><span data-stu-id="c52f9-136">Follow the [Using the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) guide, including the steps for configuring XR Plugin Management and Optimization to install the OpenXR plug-in to your project.</span></span> <span data-ttu-id="c52f9-137">确保已成功安装以下各项：</span><span class="sxs-lookup"><span data-stu-id="c52f9-137">Ensure that the following have successfully installed:</span></span>
   1. <span data-ttu-id="c52f9-138">XR 插件管理</span><span class="sxs-lookup"><span data-stu-id="c52f9-138">XR Plugin Management</span></span>
   1. <span data-ttu-id="c52f9-139">OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="c52f9-139">OpenXR Plugin</span></span>
   1. <span data-ttu-id="c52f9-140">混合现实 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="c52f9-140">Mixed Reality OpenXR Plugin</span></span>
1. <span data-ttu-id="c52f9-141">请参阅编辑 > 项目设置。</span><span class="sxs-lookup"><span data-stu-id="c52f9-141">Go to Edit > Project Settings.</span></span>
1. <span data-ttu-id="c52f9-142">单击 "项目设置" 窗口中的 XR 插件管理选项卡。</span><span class="sxs-lookup"><span data-stu-id="c52f9-142">Click on the XR Plug-in Management tab in the Project Settings window.</span></span>
1. <span data-ttu-id="c52f9-143">请确保已选中 "在启动时初始化 XR"。</span><span class="sxs-lookup"><span data-stu-id="c52f9-143">Ensure that Initialize XR on Startup is checked.</span></span>
1. <span data-ttu-id="c52f9-144"> (**_可选_**) 如果面向 HoloLens 2，请确保位于 UWP 平台上，并选择 "Microsoft HoloLens 功能集"</span><span class="sxs-lookup"><span data-stu-id="c52f9-144">(**_Optional_**) If targeting HoloLens 2, make sure you're on the UWP platform and select Microsoft HoloLens Feature Set</span></span>

![插件管理 OpenXR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> <span data-ttu-id="c52f9-146">如果预先存在的项目正在使用 MRTK 与 UPM，请确保以下行位于 MixedRealityToolkit 文件夹中的 **link.xml** 文件中。</span><span class="sxs-lookup"><span data-stu-id="c52f9-146">If you have a pre-existing project that is using MRTK from UPM, make sure that the following line is in the **link.xml** file located in the MixedRealityToolkit.Generated folder.</span></span>

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> <span data-ttu-id="c52f9-147">对于 MRTK 和 OpenXR 的初始版本，仅支持 HoloLens 2 表述的手势和 Windows Mixed Reality 运动控制器。</span><span class="sxs-lookup"><span data-stu-id="c52f9-147">For the initial release of MRTK and OpenXR, only the HoloLens 2 articulated hands and Windows Mixed Reality motion controllers are natively supported.</span></span> <span data-ttu-id="c52f9-148">未来版本中将添加对其他硬件的支持。</span><span class="sxs-lookup"><span data-stu-id="c52f9-148">Support for additional hardware will be added in upcoming releases.</span></span>

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a><span data-ttu-id="c52f9-149">为 XR SDK 管道配置 MRTK</span><span class="sxs-lookup"><span data-stu-id="c52f9-149">Configuring MRTK for the XR SDK pipeline</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="c52f9-150">使用所有默认的 MRTK 配置文件，这些配置文件都是跨 Unity 的 XR 管道配置的。</span><span class="sxs-lookup"><span data-stu-id="c52f9-150">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="c52f9-151">以前的 "DefaultOpenXRConfigurationProfile" 和 "DefaultXRSDKConfigurationProfile" 现在标记为已过时。</span><span class="sxs-lookup"><span data-stu-id="c52f9-151">The previous "DefaultOpenXRConfigurationProfile" and "DefaultXRSDKConfigurationProfile" are now labeled obsolete.</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="c52f9-152">如果使用的是 OpenXR，请选择 "DefaultOpenXRConfigurationProfile" 作为活动配置文件，或将其克隆以便进行自定义。</span><span class="sxs-lookup"><span data-stu-id="c52f9-152">If using OpenXR, choose "DefaultOpenXRConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="c52f9-153">如果在 XR 插件管理配置（如 Windows Mixed Reality 或 Oculus）中使用其他 XR 运行时，请选择 "DefaultXRSDKConfigurationProfile" 作为活动配置文件，或将其克隆以便进行自定义。</span><span class="sxs-lookup"><span data-stu-id="c52f9-153">If using other XR runtimes in the XR Plug-in Management configuration, like Windows Mixed Reality or Oculus, choose "DefaultXRSDKConfigurationProfile" as the active profile or clone it to make customizations.</span></span>

<span data-ttu-id="c52f9-154">这些配置文件在需要时设置为正确的系统和提供程序。</span><span class="sxs-lookup"><span data-stu-id="c52f9-154">These profiles are set up with the correct systems and providers, where needed.</span></span> <span data-ttu-id="c52f9-155">请参阅 [配置文件文档](../features/profiles/profiles.md#xr-sdk) ，以了解有关 XR SDK 的配置文件和示例支持的详细信息。</span><span class="sxs-lookup"><span data-stu-id="c52f9-155">See [the profiles docs](../features/profiles/profiles.md#xr-sdk) for more information on profile and sample support with XR SDK.</span></span>
::: moniker-end

<span data-ttu-id="c52f9-156">若要将现有配置文件迁移到 XR SDK，应更新以下服务和数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="c52f9-156">To migrate an existing profile to XR SDK, the following services and data providers should be updated.</span></span>
::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="c52f9-157">你将能够在 Unity 2019 中的 XR SDK 选项卡下，或在 Unity 2020 + 的主/仅视图中看到新的数据提供程序，其中旧 XR 不存在。</span><span class="sxs-lookup"><span data-stu-id="c52f9-157">You will be able to see the new data providers under the XR SDK tab in Unity 2019, or in the main/only view in Unity 2020+, where legacy XR doesn't exist.</span></span>

![XR SDK 选项卡](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a><span data-ttu-id="c52f9-159">照相机</span><span class="sxs-lookup"><span data-stu-id="c52f9-159">Camera</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="c52f9-160">添加以下数据访问接口</span><span class="sxs-lookup"><span data-stu-id="c52f9-160">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="c52f9-161">从 [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span><span class="sxs-lookup"><span data-stu-id="c52f9-161">From [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)</span></span>

![旧照相机设置](../features/images/xrsdk/CameraSystemLegacy.png)

<span data-ttu-id="c52f9-163">to</span><span class="sxs-lookup"><span data-stu-id="c52f9-163">to</span></span>
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| <span data-ttu-id="c52f9-164">OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="c52f9-164">OpenXR Plugin</span></span> | <span data-ttu-id="c52f9-165">Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="c52f9-165">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| <span data-ttu-id="c52f9-166">OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="c52f9-166">OpenXR Plugin</span></span> | <span data-ttu-id="c52f9-167">Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="c52f9-167">Windows XR Plugin</span></span> |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![XR SDK 照相机设置](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a><span data-ttu-id="c52f9-169">输入</span><span class="sxs-lookup"><span data-stu-id="c52f9-169">Input</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="c52f9-170">添加以下数据访问接口</span><span class="sxs-lookup"><span data-stu-id="c52f9-170">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="c52f9-171">从 [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span><span class="sxs-lookup"><span data-stu-id="c52f9-171">From [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)</span></span>

![旧输入设置](../features/images/xrsdk/InputSystemWMRLegacy.png)

<span data-ttu-id="c52f9-173">to</span><span class="sxs-lookup"><span data-stu-id="c52f9-173">to</span></span>
::: moniker-end

| <span data-ttu-id="c52f9-174">OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="c52f9-174">OpenXR Plugin</span></span> | <span data-ttu-id="c52f9-175">Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="c52f9-175">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

<span data-ttu-id="c52f9-176">__OpenXR__：</span><span class="sxs-lookup"><span data-stu-id="c52f9-176">__OpenXR__:</span></span>

![OpenXR 输入设置](../features/images/xrsdk/InputSystemOpenXR.png)

<span data-ttu-id="c52f9-178">__Windows Mixed Reality__：</span><span class="sxs-lookup"><span data-stu-id="c52f9-178">__Windows Mixed Reality__:</span></span>

![XR SDK 输入设置](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a><span data-ttu-id="c52f9-180">边界</span><span class="sxs-lookup"><span data-stu-id="c52f9-180">Boundary</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="c52f9-181">添加以下数据访问接口</span><span class="sxs-lookup"><span data-stu-id="c52f9-181">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="c52f9-182">从 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="c52f9-182">From [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

![旧边界设置](../features/images/xrsdk/BoundarySystemLegacy.png)

<span data-ttu-id="c52f9-184">to</span><span class="sxs-lookup"><span data-stu-id="c52f9-184">to</span></span>
::: moniker-end

| <span data-ttu-id="c52f9-185">OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="c52f9-185">OpenXR Plugin</span></span> | <span data-ttu-id="c52f9-186">Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="c52f9-186">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK 边界设置](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a><span data-ttu-id="c52f9-188">空间感知</span><span class="sxs-lookup"><span data-stu-id="c52f9-188">Spatial awareness</span></span>

::: moniker range=">= mrtkunity-2021-05"
<span data-ttu-id="c52f9-189">添加以下数据访问接口</span><span class="sxs-lookup"><span data-stu-id="c52f9-189">Add the following data providers</span></span>
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
<span data-ttu-id="c52f9-190">从 [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="c52f9-190">From [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span></span>

![旧空间感知设置](../features/images/xrsdk/SpatialAwarenessLegacy.png)

<span data-ttu-id="c52f9-192">to</span><span class="sxs-lookup"><span data-stu-id="c52f9-192">to</span></span>
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| <span data-ttu-id="c52f9-193">OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="c52f9-193">OpenXR Plugin</span></span> | <span data-ttu-id="c52f9-194">Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="c52f9-194">Windows XR Plugin</span></span> |
|---------------|-------------------|
| <span data-ttu-id="c52f9-195">[`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) UWP) 的 (</span><span class="sxs-lookup"><span data-stu-id="c52f9-195">[`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (for UWP)</span></span> | <span data-ttu-id="c52f9-196">[`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) UWP) 的 (</span><span class="sxs-lookup"><span data-stu-id="c52f9-196">[`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (for UWP)</span></span> |
| <span data-ttu-id="c52f9-197">[`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) 非 UWP) 的 (</span><span class="sxs-lookup"><span data-stu-id="c52f9-197">[`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (for non-UWP)</span></span> | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| <span data-ttu-id="c52f9-198">OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="c52f9-198">OpenXR Plugin</span></span> | <span data-ttu-id="c52f9-199">Windows XR 插件</span><span class="sxs-lookup"><span data-stu-id="c52f9-199">Windows XR Plugin</span></span> |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![XR SDK 空间感知设置](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a><span data-ttu-id="c52f9-201">控制器映射</span><span class="sxs-lookup"><span data-stu-id="c52f9-201">Controller mappings</span></span>

<span data-ttu-id="c52f9-202">如果使用自定义控制器映射配置文件，请打开其中一个配置文件并运行混合现实工具包 -> 实用工具 -> Update -> 控制器映射配置文件菜单项，以确保定义新的 XR SDK 控制器类型。</span><span class="sxs-lookup"><span data-stu-id="c52f9-202">If using custom controller mapping profiles, open one of them and run the Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles menu item to ensure the new XR SDK controller types are defined.</span></span>

## <a name="see-also"></a><span data-ttu-id="c52f9-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c52f9-203">See also</span></span>

* [<span data-ttu-id="c52f9-204">Unity 中的 AR 开发入门</span><span class="sxs-lookup"><span data-stu-id="c52f9-204">Getting started with AR development in Unity</span></span>](https://docs.unity3d.com/Manual/AROverview.html)
* [<span data-ttu-id="c52f9-205">Unity 中的 VR 开发入门</span><span class="sxs-lookup"><span data-stu-id="c52f9-205">Getting started with VR development in Unity</span></span>](https://docs.unity3d.com/Manual/VROverview.html)
