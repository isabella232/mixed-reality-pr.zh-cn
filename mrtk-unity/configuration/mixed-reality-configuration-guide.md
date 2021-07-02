---
title: MRTK 配置文件配置指南
description: 将 MRTK 配置为 Unity 的文档。
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity， HoloLens， HoloLens 2， 混合现实， 开发， MRTK，
ms.openlocfilehash: b7ec8d9ca2213ff998f94a6a2d029900ff886a2f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176409"
---
# <a name="mrtk-profile-configuration-guide"></a><span data-ttu-id="b9de6-104">MRTK 配置文件配置指南</span><span class="sxs-lookup"><span data-stu-id="b9de6-104">MRTK profile configuration guide</span></span>

<span data-ttu-id="b9de6-105">混合现实Toolkit集中管理工具包所需的尽可能多的配置， (真正的运行时"操作") 。</span><span class="sxs-lookup"><span data-stu-id="b9de6-105">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="b9de6-106">本指南是当前可用于工具包的每个配置文件屏幕的简单演练。</span><span class="sxs-lookup"><span data-stu-id="b9de6-106">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="b9de6-107">主要混合现实Toolkit配置文件</span><span class="sxs-lookup"><span data-stu-id="b9de6-107">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="b9de6-108">附加到场景中 *的 MixedRealityToolkit* GameObject 的主配置文件为项目中的 Toolkit提供了主入口点。</span><span class="sxs-lookup"><span data-stu-id="b9de6-108">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="b9de6-109">混合现实Toolkit"锁定"默认配置屏幕，以确保始终有项目的共同起点，建议随着项目的发展开始定义自己的设置。</span><span class="sxs-lookup"><span data-stu-id="b9de6-109">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="b9de6-110">在播放模式下，MRTK 配置不可编辑。</span><span class="sxs-lookup"><span data-stu-id="b9de6-110">The MRTK configuration is not editable during play-mode.</span></span>

![MRTK 配置文件](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="b9de6-112">混合现实应用的所有"默认"配置文件Toolkit资产/MRTK/SDK/Profiles 文件夹中的 SDK 项目中。</span><span class="sxs-lookup"><span data-stu-id="b9de6-112">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9de6-113">DefaultHoloLens2ConfigurationProfile 已针对 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="b9de6-113">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="b9de6-114">有关详细信息 [，](../features/profiles/profiles.md) 请参阅配置文件。</span><span class="sxs-lookup"><span data-stu-id="b9de6-114">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="b9de6-115">打开"混合现实"Toolkit配置文件"时，检查器中将看到以下屏幕：</span><span class="sxs-lookup"><span data-stu-id="b9de6-115">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="b9de6-116">如果在场景中选择没有 MixedRealityToolkitConfigurationProfile 资产的 MixedRealityToolkit，它会询问是否希望 MRTK 自动设置场景。</span><span class="sxs-lookup"><span data-stu-id="b9de6-116">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="b9de6-117">这是可选的，但是，场景中必须有一个活动的 MixedRealityToolkit 对象来访问所有配置屏幕。</span><span class="sxs-lookup"><span data-stu-id="b9de6-117">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="b9de6-118">这保存项目的当前活动运行时配置。</span><span class="sxs-lookup"><span data-stu-id="b9de6-118">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="b9de6-119">可在此处导航到 MRTK 的所有配置文件，包括：</span><span class="sxs-lookup"><span data-stu-id="b9de6-119">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="b9de6-120">混合现实Toolkit配置文件配置指南</span><span class="sxs-lookup"><span data-stu-id="b9de6-120">Mixed Reality Toolkit profile configuration guide</span></span>](#mrtk-profile-configuration-guide)
  - [<span data-ttu-id="b9de6-121">主要混合现实Toolkit配置文件</span><span class="sxs-lookup"><span data-stu-id="b9de6-121">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="b9de6-122">体验设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-122">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="b9de6-123">相机设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-123">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="b9de6-124">输入系统设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-124">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="b9de6-125">边界可视化设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-125">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="b9de6-126">远程传送系统选择</span><span class="sxs-lookup"><span data-stu-id="b9de6-126">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="b9de6-127">空间感知设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-127">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="b9de6-128">诊断设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-128">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="b9de6-129">场景系统设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-129">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="b9de6-130">其他服务设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-130">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="b9de6-131">输入操作设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-131">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="b9de6-132">输入操作规则</span><span class="sxs-lookup"><span data-stu-id="b9de6-132">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="b9de6-133">指针配置</span><span class="sxs-lookup"><span data-stu-id="b9de6-133">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="b9de6-134">笔势配置</span><span class="sxs-lookup"><span data-stu-id="b9de6-134">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="b9de6-135">语音命令</span><span class="sxs-lookup"><span data-stu-id="b9de6-135">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="b9de6-136">控制器映射配置</span><span class="sxs-lookup"><span data-stu-id="b9de6-136">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="b9de6-137">控制器可视化设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-137">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="b9de6-138">编辑器实用工具</span><span class="sxs-lookup"><span data-stu-id="b9de6-138">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="b9de6-139">服务检查器</span><span class="sxs-lookup"><span data-stu-id="b9de6-139">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="b9de6-140">深度缓冲区呈现器</span><span class="sxs-lookup"><span data-stu-id="b9de6-140">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="b9de6-141">在运行时更改配置文件</span><span class="sxs-lookup"><span data-stu-id="b9de6-141">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="b9de6-142">PRE MRTK 初始化配置文件开关</span><span class="sxs-lookup"><span data-stu-id="b9de6-142">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="b9de6-143">活动配置文件开关</span><span class="sxs-lookup"><span data-stu-id="b9de6-143">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="b9de6-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b9de6-144">See also</span></span>](#see-also)

<span data-ttu-id="b9de6-145">以下相关部分详细介绍了这些配置文件：</span><span class="sxs-lookup"><span data-stu-id="b9de6-145">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="b9de6-146">体验设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-146">Experience settings</span></span>

<span data-ttu-id="b9de6-147">此设置位于混合现实Toolkit配置页上，为项目定义[混合现实环境规模](/windows/mixed-reality/coordinate-systems-in-unity)的默认操作。</span><span class="sxs-lookup"><span data-stu-id="b9de6-147">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="b9de6-148">相机设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-148">Camera settings</span></span>

<span data-ttu-id="b9de6-149">相机设置定义如何为混合现实项目设置相机，并定义通用剪辑、质量和透明度设置。</span><span class="sxs-lookup"><span data-stu-id="b9de6-149">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="b9de6-150">输入系统设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-150">Input system settings</span></span>

<span data-ttu-id="b9de6-151">混合现实Project提供了一个可靠且经过良好训练的输入系统，用于路由默认选择的项目周围的所有输入事件。</span><span class="sxs-lookup"><span data-stu-id="b9de6-151">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="b9de6-152">MRTK 提供的输入系统后面是其他几个系统，这些系统有助于推动和管理抽象出多平台/混合现实框架的复杂性所需的复杂互操作。</span><span class="sxs-lookup"><span data-stu-id="b9de6-152">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="b9de6-153">下面详细介绍了每个配置文件：</span><span class="sxs-lookup"><span data-stu-id="b9de6-153">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="b9de6-154">焦点设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-154">Focus Settings</span></span>
- [<span data-ttu-id="b9de6-155">输入操作设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-155">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="b9de6-156">输入操作规则</span><span class="sxs-lookup"><span data-stu-id="b9de6-156">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="b9de6-157">指针配置</span><span class="sxs-lookup"><span data-stu-id="b9de6-157">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="b9de6-158">笔势配置</span><span class="sxs-lookup"><span data-stu-id="b9de6-158">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="b9de6-159">语音命令</span><span class="sxs-lookup"><span data-stu-id="b9de6-159">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="b9de6-160">控制器映射配置</span><span class="sxs-lookup"><span data-stu-id="b9de6-160">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="b9de6-161">控制器可视化设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-161">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="b9de6-162">边界可视化设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-162">Boundary visualization settings</span></span>

<span data-ttu-id="b9de6-163">边界系统转换基础平台边界/保护者系统报告的感知边界。</span><span class="sxs-lookup"><span data-stu-id="b9de6-163">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="b9de6-164">边界可视化工具配置使你可以自动显示场景中相对于用户位置的记录边界。边界还会根据用户在场景中的远程端口位置做出反应/更新。</span><span class="sxs-lookup"><span data-stu-id="b9de6-164">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="b9de6-165">远程传送系统选择</span><span class="sxs-lookup"><span data-stu-id="b9de6-165">Teleportation system selection</span></span>

<span data-ttu-id="b9de6-166">混合现实Project提供了一个功能齐全的远程传送系统，用于管理项目中默认选择的远程传送事件。</span><span class="sxs-lookup"><span data-stu-id="b9de6-166">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="b9de6-167">空间感知设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-167">Spatial awareness settings</span></span>

<span data-ttu-id="b9de6-168">混合现实Project提供了一个重新生成的空间感知系统，用于处理项目中默认选择的空间扫描系统。</span><span class="sxs-lookup"><span data-stu-id="b9de6-168">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="b9de6-169">混合现实Toolkit空间感知配置可让你定制系统的启动方式，无论系统是在应用程序启动时自动启动还是稍后以编程方式启动，以及设置视场的区。</span><span class="sxs-lookup"><span data-stu-id="b9de6-169">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="b9de6-170">它还允许你配置网格和图面设置，进一步自定义项目如何理解你周围的环境。</span><span class="sxs-lookup"><span data-stu-id="b9de6-170">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="b9de6-171">这仅适用于可以提供扫描环境的设备。</span><span class="sxs-lookup"><span data-stu-id="b9de6-171">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="b9de6-172">诊断设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-172">Diagnostics settings</span></span>

<span data-ttu-id="b9de6-173">MRTK 的一个可选但非常有用的功能是插件诊断功能。</span><span class="sxs-lookup"><span data-stu-id="b9de6-173">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="b9de6-174">诊断配置文件提供了多个在项目运行时监视的简单系统，包括一个方便的打开/关闭开关，用于启用/禁用场景中的显示面板。</span><span class="sxs-lookup"><span data-stu-id="b9de6-174">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="b9de6-175">场景系统设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-175">Scene system settings</span></span>

<span data-ttu-id="b9de6-176">MRTK 提供此可选服务，可帮助你管理复杂的附加场景加载/卸载。</span><span class="sxs-lookup"><span data-stu-id="b9de6-176">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="b9de6-177">若要确定场景系统是否适合你的项目，请阅读场景 [系统入门指南。](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="b9de6-177">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="b9de6-178">其他服务设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-178">Additional services settings</span></span>

<span data-ttu-id="b9de6-179">混合现实平台的一个更高级Toolkit是它的服务定位器模式实现[](https://en.wikipedia.org/wiki/Service_locator_pattern)，它允许向框架注册任何"服务"。</span><span class="sxs-lookup"><span data-stu-id="b9de6-179">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="b9de6-180">这样，框架就可以轻松地通过新功能/系统进行扩展，但还允许项目利用这些功能来注册自己的运行时组件。</span><span class="sxs-lookup"><span data-stu-id="b9de6-180">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="b9de6-181">任何已注册的服务仍可充分利用所有 Unity 事件，无需开销和成本即可实现 MonoBehaviour 或 clunky 单一模式。</span><span class="sxs-lookup"><span data-stu-id="b9de6-181">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="b9de6-182">这样，纯 C# 组件就无需场景开销来同时运行前台进程和后台进程，例如生成系统、运行时游戏逻辑，或者几乎不需要任何其他内容。</span><span class="sxs-lookup"><span data-stu-id="b9de6-182">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="b9de6-183">输入操作设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-183">Input actions settings</span></span>

<span data-ttu-id="b9de6-184">输入操作提供了一种从运行时项目中抽象任何物理交互和输入的方法。</span><span class="sxs-lookup"><span data-stu-id="b9de6-184">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="b9de6-185">控制器/ (/鼠标/等) 输入的所有物理输入将转换为逻辑输入操作，以用于运行时项目。</span><span class="sxs-lookup"><span data-stu-id="b9de6-185">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="b9de6-186">这可确保无论输入来自何处，项目都只是在后台将这些操作实现为"要执行的操作"或"交互"。</span><span class="sxs-lookup"><span data-stu-id="b9de6-186">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="b9de6-187">若要创建新的输入操作，只需单击"添加新操作"按钮，并输入其表示的友好文本名称。</span><span class="sxs-lookup"><span data-stu-id="b9de6-187">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="b9de6-188">然后，只需选择 (数据类型的轴) 用于传达操作，或者对于物理控制器，它可附加到的物理输入类型，例如：</span><span class="sxs-lookup"><span data-stu-id="b9de6-188">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="b9de6-189">轴约束</span><span class="sxs-lookup"><span data-stu-id="b9de6-189">Axis Constraint</span></span> | <span data-ttu-id="b9de6-190">数据类型</span><span class="sxs-lookup"><span data-stu-id="b9de6-190">Data Type</span></span> | <span data-ttu-id="b9de6-191">说明</span><span class="sxs-lookup"><span data-stu-id="b9de6-191">Description</span></span> | <span data-ttu-id="b9de6-192">用法示例</span><span class="sxs-lookup"><span data-stu-id="b9de6-192">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="b9de6-193">无</span><span class="sxs-lookup"><span data-stu-id="b9de6-193">None</span></span> | <span data-ttu-id="b9de6-194">无数据</span><span class="sxs-lookup"><span data-stu-id="b9de6-194">No data</span></span> | <span data-ttu-id="b9de6-195">用于空操作或事件</span><span class="sxs-lookup"><span data-stu-id="b9de6-195">Used for an empty action or event</span></span> | <span data-ttu-id="b9de6-196">事件触发器</span><span class="sxs-lookup"><span data-stu-id="b9de6-196">Event Trigger</span></span> |
| <span data-ttu-id="b9de6-197">原始 (预留) </span><span class="sxs-lookup"><span data-stu-id="b9de6-197">Raw (reserved)</span></span> | <span data-ttu-id="b9de6-198">object</span><span class="sxs-lookup"><span data-stu-id="b9de6-198">object</span></span> | <span data-ttu-id="b9de6-199">保留以供将来使用</span><span class="sxs-lookup"><span data-stu-id="b9de6-199">Reserved for future use</span></span> | <span data-ttu-id="b9de6-200">空值</span><span class="sxs-lookup"><span data-stu-id="b9de6-200">N/A</span></span> |
| <span data-ttu-id="b9de6-201">数码</span><span class="sxs-lookup"><span data-stu-id="b9de6-201">Digital</span></span> | <span data-ttu-id="b9de6-202">bool</span><span class="sxs-lookup"><span data-stu-id="b9de6-202">bool</span></span> | <span data-ttu-id="b9de6-203">类型数据上的布尔值</span><span class="sxs-lookup"><span data-stu-id="b9de6-203">A boolean on or off type data</span></span> | <span data-ttu-id="b9de6-204">控制器按钮</span><span class="sxs-lookup"><span data-stu-id="b9de6-204">A controller button</span></span> |
| <span data-ttu-id="b9de6-205">单轴</span><span class="sxs-lookup"><span data-stu-id="b9de6-205">Single Axis</span></span> | <span data-ttu-id="b9de6-206">float</span><span class="sxs-lookup"><span data-stu-id="b9de6-206">float</span></span> | <span data-ttu-id="b9de6-207">单个精度数据值</span><span class="sxs-lookup"><span data-stu-id="b9de6-207">A single precision data value</span></span> | <span data-ttu-id="b9de6-208">范围输入，例如触发器</span><span class="sxs-lookup"><span data-stu-id="b9de6-208">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="b9de6-209">双轴</span><span class="sxs-lookup"><span data-stu-id="b9de6-209">Dual Axis</span></span> | <span data-ttu-id="b9de6-210">Vector2</span><span class="sxs-lookup"><span data-stu-id="b9de6-210">Vector2</span></span> | <span data-ttu-id="b9de6-211">多轴的双浮点类型日期</span><span class="sxs-lookup"><span data-stu-id="b9de6-211">A dual float type date for multiple axis</span></span> | <span data-ttu-id="b9de6-212">Dpad 或操纵杆</span><span class="sxs-lookup"><span data-stu-id="b9de6-212">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="b9de6-213">三个 Dof 位置</span><span class="sxs-lookup"><span data-stu-id="b9de6-213">Three Dof Position</span></span> | <span data-ttu-id="b9de6-214">Vector3</span><span class="sxs-lookup"><span data-stu-id="b9de6-214">Vector3</span></span> | <span data-ttu-id="b9de6-215">具有3个浮点轴的位置类型数据</span><span class="sxs-lookup"><span data-stu-id="b9de6-215">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="b9de6-216">仅限3D 位置样式控制器</span><span class="sxs-lookup"><span data-stu-id="b9de6-216">3D position style only controller</span></span> |
| <span data-ttu-id="b9de6-217">三个 Dof 旋转</span><span class="sxs-lookup"><span data-stu-id="b9de6-217">Three Dof Rotation</span></span> | <span data-ttu-id="b9de6-218">四元</span><span class="sxs-lookup"><span data-stu-id="b9de6-218">Quaternion</span></span> | <span data-ttu-id="b9de6-219">仅旋转4浮点轴的输入</span><span class="sxs-lookup"><span data-stu-id="b9de6-219">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="b9de6-220">三度样式的控制器，例如 Oculus 控制器</span><span class="sxs-lookup"><span data-stu-id="b9de6-220">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="b9de6-221">6 Dof</span><span class="sxs-lookup"><span data-stu-id="b9de6-221">Six Dof</span></span> | <span data-ttu-id="b9de6-222">混合现实姿势 (System.numerics.vector2，四元数) </span><span class="sxs-lookup"><span data-stu-id="b9de6-222">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="b9de6-223">使用 System.numerics.vector2 和四元数分量的位置和旋转样式输入</span><span class="sxs-lookup"><span data-stu-id="b9de6-223">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="b9de6-224">运动控制器或指针</span><span class="sxs-lookup"><span data-stu-id="b9de6-224">A motion controller or Pointer</span></span> |

<span data-ttu-id="b9de6-225">使用输入操作的事件并不限于物理控制器，仍可在项目中使用，以使运行时效果生成新的操作。</span><span class="sxs-lookup"><span data-stu-id="b9de6-225">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="b9de6-226">输入操作是无法在运行时编辑的几个组件之一，它们只是设计时配置。</span><span class="sxs-lookup"><span data-stu-id="b9de6-226">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="b9de6-227">由于框架 (，不应将此配置文件换出，且项目) 依赖于为每个操作生成的 ID。</span><span class="sxs-lookup"><span data-stu-id="b9de6-227">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="b9de6-228">输入操作规则</span><span class="sxs-lookup"><span data-stu-id="b9de6-228">Input actions rules</span></span>

<span data-ttu-id="b9de6-229">输入操作规则提供了一种方法，用于根据其数据值将对中的一个输入操作引发的事件自动转换为不同的操作。</span><span class="sxs-lookup"><span data-stu-id="b9de6-229">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="b9de6-230">它们在框架内无缝管理，不会产生任何性能开销。</span><span class="sxs-lookup"><span data-stu-id="b9de6-230">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="b9de6-231">例如，将单个双轴输入事件从中的 DPad 转换为4对应的 "Dpad Up"/"DPad 向下"/"Dpad 左"/"Dpad Right" 操作 (如下图所示) 。</span><span class="sxs-lookup"><span data-stu-id="b9de6-231">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="b9de6-232">也可以在自己的代码中完成此操作。</span><span class="sxs-lookup"><span data-stu-id="b9de6-232">This could also be done in your own code.</span></span> <span data-ttu-id="b9de6-233">不过，由于这是一种非常常见的模式，因此框架提供了一种机制来实现这种 "现成"</span><span class="sxs-lookup"><span data-stu-id="b9de6-233">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="b9de6-234">可以为任何可用输入轴配置输入操作规则。</span><span class="sxs-lookup"><span data-stu-id="b9de6-234">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="b9de6-235">但是，可以将一个轴类型的输入操作转换为同一轴类型的另一个输入操作。</span><span class="sxs-lookup"><span data-stu-id="b9de6-235">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="b9de6-236">可以将双轴操作映射到另一个双轴操作，但不能映射到数字或无操作。</span><span class="sxs-lookup"><span data-stu-id="b9de6-236">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![输入操作规则配置文件](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="b9de6-238">指针配置</span><span class="sxs-lookup"><span data-stu-id="b9de6-238">Pointer configuration</span></span>

<span data-ttu-id="b9de6-239">指针用于驱动来自任何输入设备的场景中的交互性，同时为场景 (中附加了碰撞器或) 的 UI 组件提供方向和命中测试。</span><span class="sxs-lookup"><span data-stu-id="b9de6-239">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="b9de6-240">默认情况下，指针是自动配置的控制器、耳机 (注视/聚焦) 和鼠标/触控输入。</span><span class="sxs-lookup"><span data-stu-id="b9de6-240">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="b9de6-241">还可以使用混合现实 Toolkit 所提供的众多线条组件中的一个，或在实现 MRTK IMixedRealityPointer 接口时使用的任意行组件来在活动场景中进行可视化。</span><span class="sxs-lookup"><span data-stu-id="b9de6-241">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="b9de6-242">指向区区：确定所有指针的全局指向范围，包括 "注视"。</span><span class="sxs-lookup"><span data-stu-id="b9de6-242">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="b9de6-243">指向 Raycast 层掩码：确定将 Raycast 哪些层指针。</span><span class="sxs-lookup"><span data-stu-id="b9de6-243">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="b9de6-244">调试绘图指向射线：用于可视化用于 raycasting 的光线的调试帮助程序。</span><span class="sxs-lookup"><span data-stu-id="b9de6-244">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="b9de6-245">调试绘图指向射线颜色：用于可视化的一组颜色。</span><span class="sxs-lookup"><span data-stu-id="b9de6-245">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="b9de6-246">注视 cursor prefab：可轻松地为任何场景指定全局注视光标。</span><span class="sxs-lookup"><span data-stu-id="b9de6-246">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="b9de6-247">还有一个附加帮助器按钮，可快速跳转到注视提供商，以便在需要时重写某些特定值。</span><span class="sxs-lookup"><span data-stu-id="b9de6-247">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="b9de6-248">手势配置</span><span class="sxs-lookup"><span data-stu-id="b9de6-248">Gestures configuration</span></span>

<span data-ttu-id="b9de6-249">手势是一种系统特定的实现，可用于将输入操作分配给各种 sdk (（例如 HoloLens) ）提供的各种 "手势" 输入方法。</span><span class="sxs-lookup"><span data-stu-id="b9de6-249">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="b9de6-250">当前的手势实现仅适用于 HoloLens，并将在将来添加到 Toolkit 的其他系统中进行增强， (尚未) 任何日期。</span><span class="sxs-lookup"><span data-stu-id="b9de6-250">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="b9de6-251">语音命令</span><span class="sxs-lookup"><span data-stu-id="b9de6-251">Speech commands</span></span>

<span data-ttu-id="b9de6-252">与手势相似，某些运行时平台还提供智能的 "语音到文本" 功能，能够生成可由 Unity 项目接收的命令。</span><span class="sxs-lookup"><span data-stu-id="b9de6-252">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="b9de6-253">此配置文件允许你配置以下内容：</span><span class="sxs-lookup"><span data-stu-id="b9de6-253">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="b9de6-254">常规设置-"启动行为" 设置为 "自动启动" 或 "手动启动" 确定是在输入系统启动时初始化 KeywordRecognizer，还是让项目决定何时初始化 KeywordRecognizer。</span><span class="sxs-lookup"><span data-stu-id="b9de6-254">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="b9de6-255">"识别置信度" 用于初始化 Unity 的 [KEYWORDRECOGNIZER API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span><span class="sxs-lookup"><span data-stu-id="b9de6-255">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="b9de6-256">语音命令-注册 "单词" 并将其转换为可由您的项目接收的输入操作。</span><span class="sxs-lookup"><span data-stu-id="b9de6-256">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="b9de6-257">如果需要，还可以将它们附加到键盘操作。</span><span class="sxs-lookup"><span data-stu-id="b9de6-257">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9de6-258">在 Windows 10 平台上运行时，系统当前仅支持语音，例如 HoloLens 和 Windows 10 桌面，并将在将来添加到 MRTK 时，对其他系统进行增强， (尚未) 任何日期。</span><span class="sxs-lookup"><span data-stu-id="b9de6-258">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="b9de6-259">控制器映射配置</span><span class="sxs-lookup"><span data-stu-id="b9de6-259">Controller mapping configuration</span></span>

<span data-ttu-id="b9de6-260">混合现实 Toolkit 的核心配置屏幕之一是能够配置和映射项目可使用的各种类型的控制器。</span><span class="sxs-lookup"><span data-stu-id="b9de6-260">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="b9de6-261">使用下面的配置屏幕，可以配置该工具包当前识别的任何控制器。</span><span class="sxs-lookup"><span data-stu-id="b9de6-261">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="b9de6-262">MRTK 为以下控制器/系统提供默认配置：</span><span class="sxs-lookup"><span data-stu-id="b9de6-262">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="b9de6-263">鼠标 (包括3D 空间鼠标支持) </span><span class="sxs-lookup"><span data-stu-id="b9de6-263">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="b9de6-264">触摸屏手机</span><span class="sxs-lookup"><span data-stu-id="b9de6-264">Touch Screen</span></span>
- <span data-ttu-id="b9de6-265">Xbox 控制器</span><span class="sxs-lookup"><span data-stu-id="b9de6-265">Xbox controllers</span></span>
- <span data-ttu-id="b9de6-266">Windows Mixed Reality 控制器</span><span class="sxs-lookup"><span data-stu-id="b9de6-266">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="b9de6-267">HoloLens笔势</span><span class="sxs-lookup"><span data-stu-id="b9de6-267">HoloLens Gestures</span></span>
- <span data-ttu-id="b9de6-268">HTC Naopak 杆控制器</span><span class="sxs-lookup"><span data-stu-id="b9de6-268">HTC Vive wand controllers</span></span>
- <span data-ttu-id="b9de6-269">Oculus 触摸控制器</span><span class="sxs-lookup"><span data-stu-id="b9de6-269">Oculus Touch controllers</span></span>
- <span data-ttu-id="b9de6-270">Oculus 远程控制器</span><span class="sxs-lookup"><span data-stu-id="b9de6-270">Oculus Remote controller</span></span>
- <span data-ttu-id="b9de6-271">一般 OpenVR 设备 (高级用户仅) </span><span class="sxs-lookup"><span data-stu-id="b9de6-271">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="b9de6-272">单击任意预建控制器系统的映像可为其所有相应输入配置单个输入操作，例如，请参阅下面的 Oculus Touch 控制器配置屏幕：</span><span class="sxs-lookup"><span data-stu-id="b9de6-272">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="b9de6-273">还提供了一个高级屏幕，用于配置上面未标识的其他 OpenVR 或 Unity 输入控制器。</span><span class="sxs-lookup"><span data-stu-id="b9de6-273">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="b9de6-274">控制器可视化设置</span><span class="sxs-lookup"><span data-stu-id="b9de6-274">Controller visualization settings</span></span>

<span data-ttu-id="b9de6-275">除了控制器映射外，还提供了一个单独的配置文件，用于自定义控制器在幕后中的呈现方式。</span><span class="sxs-lookup"><span data-stu-id="b9de6-275">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="b9de6-276">此配置可以在 "全局" (某个特定手) 控制器的所有实例，或特定于单个控制器类型/手。</span><span class="sxs-lookup"><span data-stu-id="b9de6-276">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="b9de6-277">MRTK 还支持 Windows Mixed Reality 和 OpenVR 的本机 SDK 控制器型号。</span><span class="sxs-lookup"><span data-stu-id="b9de6-277">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="b9de6-278">这些在场景中作为 Gameobject 加载，并使用平台的控制器跟踪进行定位。</span><span class="sxs-lookup"><span data-stu-id="b9de6-278">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="b9de6-279">如果场景中的控制器表示形式需要与物理控制器位置偏移，只需将该偏移量设置为与控制器模型的 prefab (例如，将控制器 prefab 的转换位置设置为偏移位置) 。</span><span class="sxs-lookup"><span data-stu-id="b9de6-279">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="b9de6-280">编辑器实用工具</span><span class="sxs-lookup"><span data-stu-id="b9de6-280">Editor utilities</span></span>

<span data-ttu-id="b9de6-281">以下实用工具仅适用于编辑器，有助于提高开发工作效率。</span><span class="sxs-lookup"><span data-stu-id="b9de6-281">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![MRTK 编辑器配置实用工具](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="b9de6-283">服务检查器</span><span class="sxs-lookup"><span data-stu-id="b9de6-283">Service inspectors</span></span>

<span data-ttu-id="b9de6-284">服务检查器是一项仅限编辑器的功能，用于生成代表活动服务的场景中对象。</span><span class="sxs-lookup"><span data-stu-id="b9de6-284">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="b9de6-285">选择这些对象将显示检查器，这些检查器提供文档链接、控制编辑器可视化对象和了解服务的状态。</span><span class="sxs-lookup"><span data-stu-id="b9de6-285">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="b9de6-286">可以通过在配置文件中选中 "*编辑器设置* 下的"*使用服务检查* 器 "来启用服务检查器。</span><span class="sxs-lookup"><span data-stu-id="b9de6-286">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="b9de6-287">深度缓冲区呈现器</span><span class="sxs-lookup"><span data-stu-id="b9de6-287">Depth buffer renderer</span></span>

<span data-ttu-id="b9de6-288">与一些混合现实平台共享深度缓冲区可以改善 [全息影像的稳定性](../performance/hologram-stabilization.md)。</span><span class="sxs-lookup"><span data-stu-id="b9de6-288">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="b9de6-289">例如，Windows Mixed Reality 平台可以修改呈现的场景每个像素，以在呈现帧所花的时间内进行微妙的打印头运动。</span><span class="sxs-lookup"><span data-stu-id="b9de6-289">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="b9de6-290">不过，这些技术需要具有准确数据的深度缓冲区来了解几何图形在用户中的位置和距离。</span><span class="sxs-lookup"><span data-stu-id="b9de6-290">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="b9de6-291">若要确保场景将所有所需数据呈现给深度缓冲区，开发人员可以在配置文件中的 *编辑器设置* 下切换 *呈现深度缓冲区* 功能。</span><span class="sxs-lookup"><span data-stu-id="b9de6-291">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="b9de6-292">这将采用当前深度缓冲区，并通过对主相机应用后处理效果，将其呈现为场景视图的颜色 [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) 。</span><span class="sxs-lookup"><span data-stu-id="b9de6-292">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="b9de6-293">![呈现深度缓冲区实用程序 ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>场景中的蓝色圆柱体的材料具有 ZWrite off，因此不会写入深度数据</sup></span><span class="sxs-lookup"><span data-stu-id="b9de6-293">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="b9de6-294">在运行时更改配置文件</span><span class="sxs-lookup"><span data-stu-id="b9de6-294">Changing profiles at runtime</span></span>

<span data-ttu-id="b9de6-295">在运行时可以更新配置文件，但在这种情况下，通常有两种不同的方案和时间：</span><span class="sxs-lookup"><span data-stu-id="b9de6-295">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="b9de6-296">**预 MRTK 初始化配置文件开关**：在启动时，在初始化 MRTK 之前，并将配置文件变为活动状态，替换不使用的配置文件，根据设备功能启用/禁用不同的功能。</span><span class="sxs-lookup"><span data-stu-id="b9de6-296">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="b9de6-297">例如，如果在不具有空间映射硬件的 VR 中运行体验，则启用空间映射组件可能没有意义。</span><span class="sxs-lookup"><span data-stu-id="b9de6-297">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="b9de6-298">**活动配置文件切换**：启动后，在初始化 MRTK 并激活配置文件后，交换当前正在使用的配置文件，以更改特定功能的行为方式。</span><span class="sxs-lookup"><span data-stu-id="b9de6-298">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="b9de6-299">例如，应用程序中可能有特定的子体验，需要完全删除最多的指针。</span><span class="sxs-lookup"><span data-stu-id="b9de6-299">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="b9de6-300">预 MRTK 初始化配置文件开关</span><span class="sxs-lookup"><span data-stu-id="b9de6-300">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="b9de6-301">为此，可以附加下面的 MonoBehaviour (示例) 该示例在 MRTK 初始化之前运行 (即唤醒 () ) 。</span><span class="sxs-lookup"><span data-stu-id="b9de6-301">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="b9de6-302">请注意， (脚本，即，) 的调用必须早于脚本执行，这可以通过设置脚本执行顺序 `SetProfileBeforeInitialization` `MixedRealityToolkit` 设置 [实现](https://docs.unity3d.com/Manual/class-MonoManager.html)。</span><span class="sxs-lookup"><span data-stu-id="b9de6-302">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

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

<span data-ttu-id="b9de6-303">除了"profileToUse"，还有一组适用于特定平台的任意配置文件（例如 (一个适用于 HoloLens 1、一个适用于 VR、一个适用于 HoloLens 2 等) 。</span><span class="sxs-lookup"><span data-stu-id="b9de6-303">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="b9de6-304">可以使用各种其他指示器（例如 (，或者相机是否不透明/透明) ，以确定要加载的 https://docs.unity3d.com/ScriptReference/SystemInfo.html 配置文件。</span><span class="sxs-lookup"><span data-stu-id="b9de6-304">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="b9de6-305">活动配置文件开关</span><span class="sxs-lookup"><span data-stu-id="b9de6-305">Active profile switch</span></span>

<span data-ttu-id="b9de6-306">可以通过将 属性设置为替换活动配置文件 `MixedRealityToolkit.Instance.ActiveProfile` 的新配置文件来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="b9de6-306">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="b9de6-307">请注意，在运行时进行设置时，当前正在运行的服务的销毁将在所有服务的最后一个 LateUpdate () 之后发生，并且与新配置文件关联的服务实例化和初始化将在所有服务的第一个更新 () 之前发生。 `ActiveProfile`</span><span class="sxs-lookup"><span data-stu-id="b9de6-307">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="b9de6-308">此过程期间可能会出现明显的应用程序异常。</span><span class="sxs-lookup"><span data-stu-id="b9de6-308">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="b9de6-309">此外，优先级高于该脚本的任何脚本都可以在正确设置新配置文件之前输入 `MixedRealityToolkit` 其更新。</span><span class="sxs-lookup"><span data-stu-id="b9de6-309">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="b9de6-310">有关 [脚本优先级详细信息，](https://docs.unity3d.com/Manual/class-MonoManager.html) 请参阅脚本执行顺序设置。</span><span class="sxs-lookup"><span data-stu-id="b9de6-310">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="b9de6-311">在配置文件切换过程中，现有 UI 相机将保持不变，确保需要画布的 Unity UI 组件在切换后仍可正常工作。</span><span class="sxs-lookup"><span data-stu-id="b9de6-311">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9de6-312">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b9de6-312">See also</span></span>

- [<span data-ttu-id="b9de6-313">全息影像稳定化</span><span class="sxs-lookup"><span data-stu-id="b9de6-313">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)
