---
title: 混合现实配置指南
description: 用于将 MRTK 配置为 Unity 的文档。
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，
ms.openlocfilehash: a8aca05b4a4bc154061d6f7594e5128ab91d5f0e
ms.sourcegitcommit: c08997a75acfe4ac1d044c0fb9112e6817eb3d45
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2021
ms.locfileid: "112588867"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a><span data-ttu-id="1b7e6-104">混合现实工具包配置文件配置指南</span><span class="sxs-lookup"><span data-stu-id="1b7e6-104">Mixed Reality Toolkit profile configuration guide</span></span>

<span data-ttu-id="1b7e6-105">混合现实工具包将尽可能多的配置用于管理工具包， (除了真正的运行时 "内容" ) 。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-105">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="1b7e6-106">本指南是一个简单的演练，适用于当前适用于该工具包的每个配置文件屏蔽。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-106">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="1b7e6-107">主要混合现实工具包配置文件</span><span class="sxs-lookup"><span data-stu-id="1b7e6-107">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="1b7e6-108">主配置文件（附加到场景中的 *MixedRealityToolkit* GameObject）提供项目中工具包的主入口点。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-108">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="1b7e6-109">混合现实工具包 "锁定" 默认配置屏幕以确保你始终具有项目的一个公共起点，并且建议在项目演变后开始定义自己的设置。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-109">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="1b7e6-110">在播放模式下，不能编辑 MRTK 配置。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-110">The MRTK configuration is not editable during play-mode.</span></span>

![MRTK 配置文件](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="1b7e6-112">混合现实工具包的所有 "默认" 配置文件均可在 SDK 项目中的文件夹 "资产/MRTK/SDK/配置文件" 中找到。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-112">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b7e6-113">DefaultHoloLens2ConfigurationProfile 针对 HoloLens 2 进行了优化。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-113">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="1b7e6-114">有关详细信息，请参阅 [配置文件](../features/profiles/profiles.md) 。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-114">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="1b7e6-115">打开主混合现实工具包配置文件时，检查器中会显示以下屏幕：</span><span class="sxs-lookup"><span data-stu-id="1b7e6-115">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="1b7e6-116">如果在场景中选择不包含 MixedRealityToolkit 的 MixedRealityToolkitConfigurationProfile 资产，则会询问你是否希望 MRTK 自动为你安装场景。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-116">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="1b7e6-117">这是可选的，但是，场景中必须有一个活动的 MixedRealityToolkit 对象才能访问所有配置屏幕。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-117">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="1b7e6-118">这会承载项目的当前活动运行时配置。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-118">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="1b7e6-119">从这里，你可以导航到 MRTK 的所有配置文件，包括：</span><span class="sxs-lookup"><span data-stu-id="1b7e6-119">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="1b7e6-120">混合现实工具包配置文件配置指南</span><span class="sxs-lookup"><span data-stu-id="1b7e6-120">Mixed Reality Toolkit profile configuration guide</span></span>](#mixed-reality-toolkit-profile-configuration-guide)
  - [<span data-ttu-id="1b7e6-121">主要混合现实工具包配置文件</span><span class="sxs-lookup"><span data-stu-id="1b7e6-121">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="1b7e6-122">体验设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-122">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="1b7e6-123">相机设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-123">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="1b7e6-124">输入系统设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-124">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="1b7e6-125">边界可视化设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-125">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="1b7e6-126">Teleportation 系统选择</span><span class="sxs-lookup"><span data-stu-id="1b7e6-126">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="1b7e6-127">空间感知设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-127">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="1b7e6-128">诊断设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-128">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="1b7e6-129">场景系统设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-129">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="1b7e6-130">其他服务设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-130">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="1b7e6-131">输入操作设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-131">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="1b7e6-132">输入操作规则</span><span class="sxs-lookup"><span data-stu-id="1b7e6-132">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="1b7e6-133">指针配置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-133">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="1b7e6-134">手势配置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-134">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="1b7e6-135">语音命令</span><span class="sxs-lookup"><span data-stu-id="1b7e6-135">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="1b7e6-136">控制器映射配置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-136">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="1b7e6-137">控制器可视化设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-137">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="1b7e6-138">编辑器实用工具</span><span class="sxs-lookup"><span data-stu-id="1b7e6-138">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="1b7e6-139">服务检查器</span><span class="sxs-lookup"><span data-stu-id="1b7e6-139">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="1b7e6-140">深度缓冲区呈现器</span><span class="sxs-lookup"><span data-stu-id="1b7e6-140">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="1b7e6-141">在运行时更改配置文件</span><span class="sxs-lookup"><span data-stu-id="1b7e6-141">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="1b7e6-142">预 MRTK 初始化配置文件开关</span><span class="sxs-lookup"><span data-stu-id="1b7e6-142">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="1b7e6-143">活动配置文件开关</span><span class="sxs-lookup"><span data-stu-id="1b7e6-143">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="1b7e6-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b7e6-144">See also</span></span>](#see-also)

<span data-ttu-id="1b7e6-145">下面详细介绍了这些配置文件：</span><span class="sxs-lookup"><span data-stu-id="1b7e6-145">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="1b7e6-146">体验设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-146">Experience settings</span></span>

<span data-ttu-id="1b7e6-147">位于 "主混合现实工具包配置" 页上，此设置定义项目的 [混合现实环境规模](/windows/mixed-reality/coordinate-systems-in-unity) 的默认操作。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-147">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="1b7e6-148">相机设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-148">Camera settings</span></span>

<span data-ttu-id="1b7e6-149">相机设置定义如何为混合现实项目设置照相机，定义一般剪辑、质量和透明度设置。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-149">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="1b7e6-150">输入系统设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-150">Input system settings</span></span>

<span data-ttu-id="1b7e6-151">混合现实项目提供了一个功能强大的经过训练的输入系统，用于路由默认情况下选择的项目的所有输入事件。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-151">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="1b7e6-152">MRTK 提供的输入系统后面是多个其他系统，它们有助于推动和管理复杂的 weavings，以抽象出多平台/混合现实框架的复杂性。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-152">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="1b7e6-153">下面详细介绍了每个配置文件：</span><span class="sxs-lookup"><span data-stu-id="1b7e6-153">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="1b7e6-154">焦点设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-154">Focus Settings</span></span>
- [<span data-ttu-id="1b7e6-155">输入操作设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-155">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="1b7e6-156">输入操作规则</span><span class="sxs-lookup"><span data-stu-id="1b7e6-156">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="1b7e6-157">指针配置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-157">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="1b7e6-158">手势配置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-158">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="1b7e6-159">语音命令</span><span class="sxs-lookup"><span data-stu-id="1b7e6-159">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="1b7e6-160">控制器映射配置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-160">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="1b7e6-161">控制器可视化设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-161">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="1b7e6-162">边界可视化设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-162">Boundary visualization settings</span></span>

<span data-ttu-id="1b7e6-163">边界系统会转换由基础平台边界/监护人系统报告的感知边界。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-163">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="1b7e6-164">边界可视化工具配置使你能够根据用户的位置自动显示场景中记录的边界。边界还会根据用户在场景中 teleports 的位置做出反应/更新。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-164">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="1b7e6-165">Teleportation 系统选择</span><span class="sxs-lookup"><span data-stu-id="1b7e6-165">Teleportation system selection</span></span>

<span data-ttu-id="1b7e6-166">混合现实项目提供了一个功能完备的 Teleportation 系统，用于管理项目中的 Teleportation 事件，默认情况下处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-166">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="1b7e6-167">空间感知设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-167">Spatial awareness settings</span></span>

<span data-ttu-id="1b7e6-168">混合现实项目提供重建的空间感知系统，用于在默认情况下选择的项目中使用空间扫描系统。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-168">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="1b7e6-169">混合现实工具包的空间感知配置使你能够定制系统的启动方式，无论应用程序是在应用程序启动时自动启动还是在以后以编程方式设置，还可以为视图字段设置范围。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-169">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="1b7e6-170">它还允许您配置网格和图面设置，进一步自定义您的项目如何理解您的环境。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-170">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="1b7e6-171">这仅适用于可提供扫描环境的设备。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-171">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="1b7e6-172">诊断设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-172">Diagnostics settings</span></span>

<span data-ttu-id="1b7e6-173">MRTK 的可选但非常有用的功能是插件诊断功能。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-173">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="1b7e6-174">诊断配置文件提供了几个简单的系统，可以在项目运行时进行监视，包括便捷的 On/Off 开关，用于在场景中启用/禁用显示面板。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-174">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="1b7e6-175">场景系统设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-175">Scene system settings</span></span>

<span data-ttu-id="1b7e6-176">MRTK 提供了此可选的服务，可帮助管理复杂的加法场景加载/卸载。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-176">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="1b7e6-177">若要确定场景系统是否适合你的项目，请阅读 [场景系统入门指南。](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="1b7e6-177">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="1b7e6-178">其他服务设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-178">Additional services settings</span></span>

<span data-ttu-id="1b7e6-179">混合现实工具包的更高级的领域之一是其 [服务定位器模式](https://en.wikipedia.org/wiki/Service_locator_pattern) 实现，该实现允许向框架注册任何 "服务"。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-179">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="1b7e6-180">这样，就可以轻松地使用新功能/系统扩展框架，还可以利用这些功能来注册自己的运行时组件。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-180">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="1b7e6-181">任何注册的服务仍能充分利用所有 Unity 事件，而无需执行 MonoBehaviour 或笨单一实例模式的开销和成本。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-181">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="1b7e6-182">这就允许在运行前台和后台进程（例如，生成系统、运行时游戏逻辑或几乎任何其他操作）时不具有场景开销的纯 c # 组件。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-182">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="1b7e6-183">输入操作设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-183">Input actions settings</span></span>

<span data-ttu-id="1b7e6-184">输入操作提供了一种方法，用于从运行时项目抽象任何物理交互和输入。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-184">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="1b7e6-185">所有物理输入 (从控制器/手/鼠标/等) 转换为逻辑输入操作，以便在运行时项目中使用。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-185">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="1b7e6-186">这可确保无论输入来自何处，项目只是在幕后将这些操作作为 "要执行的操作" 或 "交互" 来实现。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-186">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="1b7e6-187">若要创建新的输入操作，只需单击 "添加新操作" 按钮并为其表示的内容输入友好文本名称即可。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-187">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="1b7e6-188">然后，只需选择一个轴 (操作要传达的数据类型) ，或在物理控制器的情况下，它可以附加到的物理输入类型，例如：</span><span class="sxs-lookup"><span data-stu-id="1b7e6-188">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="1b7e6-189">轴约束</span><span class="sxs-lookup"><span data-stu-id="1b7e6-189">Axis Constraint</span></span> | <span data-ttu-id="1b7e6-190">数据类型</span><span class="sxs-lookup"><span data-stu-id="1b7e6-190">Data Type</span></span> | <span data-ttu-id="1b7e6-191">描述</span><span class="sxs-lookup"><span data-stu-id="1b7e6-191">Description</span></span> | <span data-ttu-id="1b7e6-192">用法示例</span><span class="sxs-lookup"><span data-stu-id="1b7e6-192">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="1b7e6-193">无</span><span class="sxs-lookup"><span data-stu-id="1b7e6-193">None</span></span> | <span data-ttu-id="1b7e6-194">无数据</span><span class="sxs-lookup"><span data-stu-id="1b7e6-194">No data</span></span> | <span data-ttu-id="1b7e6-195">用于空操作或事件</span><span class="sxs-lookup"><span data-stu-id="1b7e6-195">Used for an empty action or event</span></span> | <span data-ttu-id="1b7e6-196">事件触发器</span><span class="sxs-lookup"><span data-stu-id="1b7e6-196">Event Trigger</span></span> |
| <span data-ttu-id="1b7e6-197">原始 (保留) </span><span class="sxs-lookup"><span data-stu-id="1b7e6-197">Raw (reserved)</span></span> | <span data-ttu-id="1b7e6-198">object</span><span class="sxs-lookup"><span data-stu-id="1b7e6-198">object</span></span> | <span data-ttu-id="1b7e6-199">保留以供将来使用</span><span class="sxs-lookup"><span data-stu-id="1b7e6-199">Reserved for future use</span></span> | <span data-ttu-id="1b7e6-200">空值</span><span class="sxs-lookup"><span data-stu-id="1b7e6-200">N/A</span></span> |
| <span data-ttu-id="1b7e6-201">数码</span><span class="sxs-lookup"><span data-stu-id="1b7e6-201">Digital</span></span> | <span data-ttu-id="1b7e6-202">bool</span><span class="sxs-lookup"><span data-stu-id="1b7e6-202">bool</span></span> | <span data-ttu-id="1b7e6-203">打开或关闭类型数据的布尔值</span><span class="sxs-lookup"><span data-stu-id="1b7e6-203">A boolean on or off type data</span></span> | <span data-ttu-id="1b7e6-204">控制器按钮</span><span class="sxs-lookup"><span data-stu-id="1b7e6-204">A controller button</span></span> |
| <span data-ttu-id="1b7e6-205">单轴</span><span class="sxs-lookup"><span data-stu-id="1b7e6-205">Single Axis</span></span> | <span data-ttu-id="1b7e6-206">FLOAT</span><span class="sxs-lookup"><span data-stu-id="1b7e6-206">float</span></span> | <span data-ttu-id="1b7e6-207">单个精度数据值</span><span class="sxs-lookup"><span data-stu-id="1b7e6-207">A single precision data value</span></span> | <span data-ttu-id="1b7e6-208">范围输入，例如触发器</span><span class="sxs-lookup"><span data-stu-id="1b7e6-208">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="1b7e6-209">双轴</span><span class="sxs-lookup"><span data-stu-id="1b7e6-209">Dual Axis</span></span> | <span data-ttu-id="1b7e6-210">Vector2</span><span class="sxs-lookup"><span data-stu-id="1b7e6-210">Vector2</span></span> | <span data-ttu-id="1b7e6-211">多个轴的双浮点类型日期</span><span class="sxs-lookup"><span data-stu-id="1b7e6-211">A dual float type date for multiple axis</span></span> | <span data-ttu-id="1b7e6-212">Dpad 或 Thumbstick</span><span class="sxs-lookup"><span data-stu-id="1b7e6-212">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="1b7e6-213">三个 Dof 位置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-213">Three Dof Position</span></span> | <span data-ttu-id="1b7e6-214">Vector3</span><span class="sxs-lookup"><span data-stu-id="1b7e6-214">Vector3</span></span> | <span data-ttu-id="1b7e6-215">具有 3 个浮点轴的 中的位置类型数据</span><span class="sxs-lookup"><span data-stu-id="1b7e6-215">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="1b7e6-216">仅 3D 位置样式控制器</span><span class="sxs-lookup"><span data-stu-id="1b7e6-216">3D position style only controller</span></span> |
| <span data-ttu-id="1b7e6-217">三个 Dof 旋转</span><span class="sxs-lookup"><span data-stu-id="1b7e6-217">Three Dof Rotation</span></span> | <span data-ttu-id="1b7e6-218">四元</span><span class="sxs-lookup"><span data-stu-id="1b7e6-218">Quaternion</span></span> | <span data-ttu-id="1b7e6-219">具有 4 个浮点轴的仅旋转输入</span><span class="sxs-lookup"><span data-stu-id="1b7e6-219">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="1b7e6-220">三度样式控制器，例如 Oculus Go 控制器</span><span class="sxs-lookup"><span data-stu-id="1b7e6-220">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="1b7e6-221">六个 Dof</span><span class="sxs-lookup"><span data-stu-id="1b7e6-221">Six Dof</span></span> | <span data-ttu-id="1b7e6-222">混合现实姿势 (Vector3、四元数) </span><span class="sxs-lookup"><span data-stu-id="1b7e6-222">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="1b7e6-223">包含 Vector3 和四元数组件的位置和旋转样式输入</span><span class="sxs-lookup"><span data-stu-id="1b7e6-223">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="1b7e6-224">运动控制器或指针</span><span class="sxs-lookup"><span data-stu-id="1b7e6-224">A motion controller or Pointer</span></span> |

<span data-ttu-id="1b7e6-225">利用输入操作的事件不限于物理控制器，仍可在项目中使用，使运行时效果生成新操作。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-225">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="1b7e6-226">输入操作是在运行时无法编辑的少数组件之一，它们只是设计时配置。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-226">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="1b7e6-227">在项目运行时，不应交换此配置文件，因为框架 (并且项目) 每个操作生成的 ID 的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-227">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="1b7e6-228">输入操作规则</span><span class="sxs-lookup"><span data-stu-id="1b7e6-228">Input actions rules</span></span>

<span data-ttu-id="1b7e6-229">输入操作规则提供了一种自动将中针对一个输入操作引发的事件转换为基于其数据值的不同操作的方法。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-229">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="1b7e6-230">这些在框架中无缝管理，不会产生任何性能成本。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-230">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="1b7e6-231">例如，将单个双轴输入事件从 中的 DPad 转换为 4 个对应的"Dpad Up"/"DPad 向下"/"Dpad 左侧"/"Dpad 右侧"操作 (如下图) 所示。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-231">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="1b7e6-232">这也可在你自己的代码中完成。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-232">This could also be done in your own code.</span></span> <span data-ttu-id="1b7e6-233">但是，由于这是一种非常常见的模式，框架提供了一种机制来"开箱使用"</span><span class="sxs-lookup"><span data-stu-id="1b7e6-233">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="1b7e6-234">可以针对任何可用的输入轴配置输入操作规则。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-234">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="1b7e6-235">但是，一个轴类型的输入操作可以转换为同一轴类型的另一个输入操作。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-235">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="1b7e6-236">可以将双轴操作映射到另一个双轴操作，但不能映射到数字或无操作。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-236">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![输入操作规则配置文件](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="1b7e6-238">指针配置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-238">Pointer configuration</span></span>

<span data-ttu-id="1b7e6-239">指针用于驱动来自任何输入设备的场景中的交互性，从而对场景中的任何对象提供方向和命中测试 (该对象附加了碰撞体或是 UI 组件) 。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-239">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="1b7e6-240">默认情况下，会自动为控制器、头戴显示设备配置 (/焦点) 和鼠标/触摸输入。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-240">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="1b7e6-241">此外，还可使用混合现实工具包提供的众多行组件之一在活动场景中可视化指针，如果它们实现 MRTK IMixedRealityPointer 接口，也可以可视化自己的任何一个。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-241">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="1b7e6-242">指向范围：确定所有指针（包括凝视）的全局指向范围。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-242">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="1b7e6-243">指向光线广播层掩码：确定指针将针对哪些层进行光线广播。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-243">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="1b7e6-244">调试绘制指向射线：用于可视化用于光线广播的射线的调试帮助程序。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-244">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="1b7e6-245">调试绘制指向射线颜色：用于可视化的一组颜色。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-245">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="1b7e6-246">凝视光标预制件：可轻松指定任何场景的全局凝视光标。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-246">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="1b7e6-247">有一个附加的帮助器按钮，可根据需要快速跳转到凝视提供程序，以替代凝视的一些特定值。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-247">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="1b7e6-248">笔势配置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-248">Gestures configuration</span></span>

<span data-ttu-id="1b7e6-249">手势是一种特定于系统的实现，允许将输入操作分配给各种 SDK 提供的各种"笔势"输入 (例如 HoloLens) 。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-249">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="1b7e6-250">当前的笔势实现仅适用于 HoloLens，并且将针对其他系统进行增强，因为将来这些系统将添加到工具包 (尚未) 。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-250">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="1b7e6-251">语音命令</span><span class="sxs-lookup"><span data-stu-id="1b7e6-251">Speech commands</span></span>

<span data-ttu-id="1b7e6-252">与笔势一样，某些运行时平台语音转文本智能"命令"功能，能够生成 Unity 项目可以接收的命令。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-252">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="1b7e6-253">此配置文件允许配置以下各项：</span><span class="sxs-lookup"><span data-stu-id="1b7e6-253">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="1b7e6-254">常规设置 - 设置为"自动启动"或"手动启动"的"启动行为"确定是初始化输入系统启动时的 KeywordRecognizer，还是让项目决定何时初始化 KeywordRecognizer。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-254">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="1b7e6-255">"识别置信度"用于初始化 Unity 的 [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span><span class="sxs-lookup"><span data-stu-id="1b7e6-255">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="1b7e6-256">语音命令 - 注册"单词"，并将其转换为项目可以接收的输入操作。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-256">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="1b7e6-257">如果需要，还可以将键盘操作附加到键盘操作。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-257">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b7e6-258">系统目前仅在 Windows 10 平台（例如 HoloLens 和 Windows 10 桌面）上运行时支持语音，并且将针对其他系统进行增强，因为将来会添加到 MRTK 中 (尚未) 。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-258">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="1b7e6-259">控制器映射配置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-259">Controller mapping configuration</span></span>

<span data-ttu-id="1b7e6-260">混合现实工具包的核心配置屏幕之一是能够配置和映射项目可以使用的各种类型的控制器。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-260">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="1b7e6-261">下面的配置屏幕允许配置工具包当前识别的任何控制器。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-261">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="1b7e6-262">MRTK 为以下控制器/系统提供默认配置：</span><span class="sxs-lookup"><span data-stu-id="1b7e6-262">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="1b7e6-263">鼠标 (包括三维空间鼠标支持) </span><span class="sxs-lookup"><span data-stu-id="1b7e6-263">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="1b7e6-264">触摸屏手机</span><span class="sxs-lookup"><span data-stu-id="1b7e6-264">Touch Screen</span></span>
- <span data-ttu-id="1b7e6-265">Xbox 控制器</span><span class="sxs-lookup"><span data-stu-id="1b7e6-265">Xbox controllers</span></span>
- <span data-ttu-id="1b7e6-266">Windows Mixed Reality控制器</span><span class="sxs-lookup"><span data-stu-id="1b7e6-266">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="1b7e6-267">HoloLens 笔势</span><span class="sxs-lookup"><span data-stu-id="1b7e6-267">HoloLens Gestures</span></span>
- <span data-ttu-id="1b7e6-268">用于 WANVive Wand 控制器的</span><span class="sxs-lookup"><span data-stu-id="1b7e6-268">HTC Vive wand controllers</span></span>
- <span data-ttu-id="1b7e6-269">Oculus Touch 控制器</span><span class="sxs-lookup"><span data-stu-id="1b7e6-269">Oculus Touch controllers</span></span>
- <span data-ttu-id="1b7e6-270">Oculus 远程控制器</span><span class="sxs-lookup"><span data-stu-id="1b7e6-270">Oculus Remote controller</span></span>
- <span data-ttu-id="1b7e6-271">通用 OpenVR 设备 (高级用户) </span><span class="sxs-lookup"><span data-stu-id="1b7e6-271">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="1b7e6-272">单击任何预建控制器系统的"映像"，可以针对其所有相应输入配置单个输入操作，例如，请参阅下面的 Oculus Touch 控制器配置屏幕：</span><span class="sxs-lookup"><span data-stu-id="1b7e6-272">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="1b7e6-273">还有一个高级屏幕，用于配置上面未标识的其他 OpenVR 或 Unity 输入控制器。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-273">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="1b7e6-274">控制器可视化设置</span><span class="sxs-lookup"><span data-stu-id="1b7e6-274">Controller visualization settings</span></span>

<span data-ttu-id="1b7e6-275">除了控制器映射，还提供了单独的配置文件来自定义控制器在场景中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-275">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="1b7e6-276">可以在控制器的所有实例的"全局" (配置此配置，) 或特定于单个控制器类型/手部。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-276">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="1b7e6-277">MRTK 还支持适用于 Windows Mixed Reality OpenVR 的本机 SDK 控制器模型。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-277">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="1b7e6-278">这些对象作为 GameObjects 加载到场景中，使用平台的控制器跟踪进行定位。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-278">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="1b7e6-279">如果场景中的控制器表示形式需要与物理控制器位置偏移，则只需针对控制器模型的预制项设置该偏移量 (例如，使用偏移位置) 设置控制器预制的转换位置。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-279">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="1b7e6-280">编辑器实用工具</span><span class="sxs-lookup"><span data-stu-id="1b7e6-280">Editor utilities</span></span>

<span data-ttu-id="1b7e6-281">以下实用工具仅在编辑器中工作，可用于提高开发效率。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-281">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![MRTK 编辑器配置实用工具](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="1b7e6-283">服务检查器</span><span class="sxs-lookup"><span data-stu-id="1b7e6-283">Service inspectors</span></span>

<span data-ttu-id="1b7e6-284">服务检查器是一项仅编辑器功能，可生成表示活动服务的场景中对象。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-284">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="1b7e6-285">选择这些对象将显示检查器，这些检查器提供文档链接、控制编辑器可视化效果和深入了解服务状态。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-285">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="1b7e6-286">可以通过在配置文件的"编辑器设置"下选中"使用服务 *检查* 器" *来* 启用服务检查器。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-286">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="1b7e6-287">深度缓冲区呈现器</span><span class="sxs-lookup"><span data-stu-id="1b7e6-287">Depth buffer renderer</span></span>

<span data-ttu-id="1b7e6-288">与一些混合现实平台共享深度缓冲区可以提高 [全息影像稳定性](../performance/hologram-stabilization.md)。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-288">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="1b7e6-289">例如，Windows Mixed Reality平台可以修改每个像素呈现的场景，以考虑呈现帧所花时间的细微头部运动。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-289">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="1b7e6-290">但是，这些技术需要使用具有准确数据的深度缓冲区来了解几何图形与用户的位置和距离。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-290">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="1b7e6-291">为了确保场景将所有必要的数据呈现到深度缓冲区，开发人员可以在配置文件中的"编辑器设置"下切换"呈现深度缓冲区"功能。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-291">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="1b7e6-292">这会采用当前深度缓冲区，通过向主相机应用后处理效果，以颜色呈现给 [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) 场景视图。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-292">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="1b7e6-293">![渲染深度缓冲区实用工具 ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>场景中的蓝色柱形具有 ZWrite 关闭的材料，因此不会写入深度数据</sup></span><span class="sxs-lookup"><span data-stu-id="1b7e6-293">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="1b7e6-294">在运行时更改配置文件</span><span class="sxs-lookup"><span data-stu-id="1b7e6-294">Changing profiles at runtime</span></span>

<span data-ttu-id="1b7e6-295">可以在运行时更新配置文件，通常有两种不同的方案和时间，这很有帮助：</span><span class="sxs-lookup"><span data-stu-id="1b7e6-295">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="1b7e6-296">**MRTK** 初始化配置文件开关：在启动时，在 MRTK 初始化和配置文件变为活动状态之前，替换尚未使用的配置文件，以基于设备功能启用/禁用不同的功能。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-296">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="1b7e6-297">例如，如果体验在没有空间映射硬件的 VR 中运行，则启用空间映射组件可能没有意义。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-297">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="1b7e6-298">**活动配置文件切换**：启动后，在 MRTK 初始化且配置文件变为活动状态后，交换当前使用的配置文件以更改某些功能的行为方式。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-298">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="1b7e6-299">例如，应用程序中可能有特定的子体验需要完全删除远手指针。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-299">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="1b7e6-300">PRE MRTK 初始化配置文件开关</span><span class="sxs-lookup"><span data-stu-id="1b7e6-300">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="1b7e6-301">为此，可将下面的 MonoBehaviour (示例附加到 MRTK 初始化之前运行的) ， (即唤醒 () ) 。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-301">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="1b7e6-302">请注意，脚本 (例如，对 `SetProfileBeforeInitialization`) 的调用必须早于脚本执行 `MixedRealityToolkit` ，这可以通过设置 [脚本执行顺序设置](https://docs.unity3d.com/Manual/class-MonoManager.html)来实现。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-302">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

<span data-ttu-id="1b7e6-303"> (例如，一组适用于特定平台的任意配置文件，而不是 "profileToUse"，例如，一个用于 VR，一个用于 VR 2，等等) 。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-303">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="1b7e6-304">可以使用各种其他指标 (例如 https://docs.unity3d.com/ScriptReference/SystemInfo.html ，或照相机是否为不透明/透明) ，以确定要加载的配置文件。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-304">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="1b7e6-305">活动配置文件开关</span><span class="sxs-lookup"><span data-stu-id="1b7e6-305">Active profile switch</span></span>

<span data-ttu-id="1b7e6-306">可以通过将 `MixedRealityToolkit.Instance.ActiveProfile` 属性设置为替换活动配置文件的新配置文件来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-306">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="1b7e6-307">注意当在 `ActiveProfile` 运行时进行设置时，当前正在运行的服务将在所有服务的最后一个 behaviour () 之后发生，并且与新配置文件关联的服务的实例化和初始化将发生在所有服务的第一次更新 () 之前。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-307">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="1b7e6-308">在此过程中可能会出现明显的应用程序毫不迟疑。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-308">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="1b7e6-309">此外，任何优先级高于脚本的脚本 `MixedRealityToolkit` 都可以在正确设置新的配置文件之前输入其更新。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-309">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="1b7e6-310">有关脚本优先级的详细信息，请参阅 [脚本执行顺序设置](https://docs.unity3d.com/Manual/class-MonoManager.html) 。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-310">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="1b7e6-311">在配置文件切换过程中，现有的 UI 照相机会保持不变，确保在开关后需要画布的 Unity UI 组件仍可正常工作。</span><span class="sxs-lookup"><span data-stu-id="1b7e6-311">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b7e6-312">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b7e6-312">See also</span></span>

- [<span data-ttu-id="1b7e6-313">全息影像稳定化</span><span class="sxs-lookup"><span data-stu-id="1b7e6-313">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)