---
title: 混合现实配置指南
description: 将 MRTK 配置为 unity 的文档。
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: fc97a2d7c6182b4836d644d91be237e2aef01feb
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143574"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a><span data-ttu-id="29812-104">混合现实工具包配置文件配置指南</span><span class="sxs-lookup"><span data-stu-id="29812-104">Mixed Reality Toolkit profile configuration guide</span></span>

![MRTK 徽标](../features/images/MRTK_Logo_Rev.png)

<span data-ttu-id="29812-106&quot;>混合现实工具包集中了管理工具包所需的尽可能多的配置， (真正的运行时&quot;操作") 。</span><span class="sxs-lookup"><span data-stu-id="29812-106">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="29812-107">本指南是当前可用于工具包的每个配置文件屏幕的简单演练。</span><span class="sxs-lookup"><span data-stu-id="29812-107">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="29812-108">主要混合现实工具包配置文件</span><span class="sxs-lookup"><span data-stu-id="29812-108">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="29812-109">附加到场景中 *MixedRealityToolkit* GameObject 的主配置文件为项目中的工具包提供了主入口点。</span><span class="sxs-lookup"><span data-stu-id="29812-109">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="29812-110">混合现实工具包"锁定"默认配置屏幕，以确保始终有项目的共同起点，建议随着项目的发展开始定义自己的设置。</span><span class="sxs-lookup"><span data-stu-id="29812-110">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="29812-111">在播放模式下，MRTK 配置不可编辑。</span><span class="sxs-lookup"><span data-stu-id="29812-111">The MRTK configuration is not editable during play-mode.</span></span>

![MRTK 配置文件](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="29812-113">混合现实工具包的所有"默认"配置文件都可以在 SDK 项目的 Assets/MRTK/SDK/Profiles 文件夹中找到。</span><span class="sxs-lookup"><span data-stu-id="29812-113">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29812-114">DefaultHoloLens2ConfigurationProfile 针对 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="29812-114">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="29812-115">有关详细信息 [，](../features/profiles/profiles.md) 请参阅配置文件。</span><span class="sxs-lookup"><span data-stu-id="29812-115">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="29812-116">打开主混合现实工具包配置文件时，检查器中将看到以下屏幕：</span><span class="sxs-lookup"><span data-stu-id="29812-116">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="29812-117">如果在场景中选择没有 MixedRealityToolkitConfigurationProfile 资产的 MixedRealityToolkit，它会询问是否希望 MRTK 自动设置场景。</span><span class="sxs-lookup"><span data-stu-id="29812-117">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="29812-118">这是可选的，但是，场景中必须有一个活动的 MixedRealityToolkit 对象来访问所有配置屏幕。</span><span class="sxs-lookup"><span data-stu-id="29812-118">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="29812-119">这保存项目的当前活动运行时配置。</span><span class="sxs-lookup"><span data-stu-id="29812-119">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="29812-120">可在此处导航到 MRTK 的所有配置文件，包括：</span><span class="sxs-lookup"><span data-stu-id="29812-120">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="29812-121">混合现实工具包配置文件配置指南</span><span class="sxs-lookup"><span data-stu-id="29812-121">Mixed Reality Toolkit profile configuration guide</span></span>](#mixed-reality-toolkit-profile-configuration-guide)
  - [<span data-ttu-id="29812-122">主要混合现实工具包配置文件</span><span class="sxs-lookup"><span data-stu-id="29812-122">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="29812-123">体验设置</span><span class="sxs-lookup"><span data-stu-id="29812-123">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="29812-124">相机设置</span><span class="sxs-lookup"><span data-stu-id="29812-124">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="29812-125">输入系统设置</span><span class="sxs-lookup"><span data-stu-id="29812-125">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="29812-126">边界可视化设置</span><span class="sxs-lookup"><span data-stu-id="29812-126">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="29812-127">Teleportation 系统选择</span><span class="sxs-lookup"><span data-stu-id="29812-127">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="29812-128">空间感知设置</span><span class="sxs-lookup"><span data-stu-id="29812-128">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="29812-129">诊断设置</span><span class="sxs-lookup"><span data-stu-id="29812-129">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="29812-130">场景系统设置</span><span class="sxs-lookup"><span data-stu-id="29812-130">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="29812-131">其他服务设置</span><span class="sxs-lookup"><span data-stu-id="29812-131">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="29812-132">输入操作设置</span><span class="sxs-lookup"><span data-stu-id="29812-132">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="29812-133">输入操作规则</span><span class="sxs-lookup"><span data-stu-id="29812-133">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="29812-134">指针配置</span><span class="sxs-lookup"><span data-stu-id="29812-134">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="29812-135">手势配置</span><span class="sxs-lookup"><span data-stu-id="29812-135">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="29812-136">语音命令</span><span class="sxs-lookup"><span data-stu-id="29812-136">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="29812-137">控制器映射配置</span><span class="sxs-lookup"><span data-stu-id="29812-137">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="29812-138">控制器可视化设置</span><span class="sxs-lookup"><span data-stu-id="29812-138">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="29812-139">编辑器实用工具</span><span class="sxs-lookup"><span data-stu-id="29812-139">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="29812-140">服务检查器</span><span class="sxs-lookup"><span data-stu-id="29812-140">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="29812-141">深度缓冲区呈现器</span><span class="sxs-lookup"><span data-stu-id="29812-141">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="29812-142">在运行时更改配置文件</span><span class="sxs-lookup"><span data-stu-id="29812-142">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="29812-143">预 MRTK 初始化配置文件开关</span><span class="sxs-lookup"><span data-stu-id="29812-143">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="29812-144">活动配置文件开关</span><span class="sxs-lookup"><span data-stu-id="29812-144">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="29812-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29812-145">See also</span></span>](#see-also)

<span data-ttu-id="29812-146">下面详细介绍了这些配置文件：</span><span class="sxs-lookup"><span data-stu-id="29812-146">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="29812-147">体验设置</span><span class="sxs-lookup"><span data-stu-id="29812-147">Experience settings</span></span>

<span data-ttu-id="29812-148">此设置位于混合现实工具包的主要配置页上，定义项目的 [混合现实环境规模](/windows/mixed-reality/coordinate-systems-in-unity) 的默认操作。</span><span class="sxs-lookup"><span data-stu-id="29812-148">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="29812-149">相机设置</span><span class="sxs-lookup"><span data-stu-id="29812-149">Camera settings</span></span>

<span data-ttu-id="29812-150">相机设置定义如何为混合现实项目设置相机，并定义通用剪辑、质量和透明度设置。</span><span class="sxs-lookup"><span data-stu-id="29812-150">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="29812-151">输入系统设置</span><span class="sxs-lookup"><span data-stu-id="29812-151">Input system settings</span></span>

<span data-ttu-id="29812-152">混合现实项目提供了一个可靠且经过良好训练的输入系统，用于路由默认情况下选中的项目周围的所有输入事件。</span><span class="sxs-lookup"><span data-stu-id="29812-152">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="29812-153">MRTK 提供的输入系统后面是其他几个系统，这些系统有助于推动和管理抽象出多平台/混合现实框架的复杂性所需的复杂互操作。</span><span class="sxs-lookup"><span data-stu-id="29812-153">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="29812-154">下面详细介绍了每个配置文件：</span><span class="sxs-lookup"><span data-stu-id="29812-154">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="29812-155">焦点设置</span><span class="sxs-lookup"><span data-stu-id="29812-155">Focus Settings</span></span>
- [<span data-ttu-id="29812-156">输入操作设置</span><span class="sxs-lookup"><span data-stu-id="29812-156">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="29812-157">输入操作规则</span><span class="sxs-lookup"><span data-stu-id="29812-157">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="29812-158">指针配置</span><span class="sxs-lookup"><span data-stu-id="29812-158">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="29812-159">笔势配置</span><span class="sxs-lookup"><span data-stu-id="29812-159">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="29812-160">语音命令</span><span class="sxs-lookup"><span data-stu-id="29812-160">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="29812-161">控制器映射配置</span><span class="sxs-lookup"><span data-stu-id="29812-161">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="29812-162">控制器可视化设置</span><span class="sxs-lookup"><span data-stu-id="29812-162">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="29812-163">边界可视化设置</span><span class="sxs-lookup"><span data-stu-id="29812-163">Boundary visualization settings</span></span>

<span data-ttu-id="29812-164">边界系统转换基础平台边界/保护者系统报告的感知边界。</span><span class="sxs-lookup"><span data-stu-id="29812-164">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="29812-165">边界可视化工具配置使你可以自动显示场景中相对于用户位置的记录边界。边界还会根据用户在场景中的远程端口位置做出反应/更新。</span><span class="sxs-lookup"><span data-stu-id="29812-165">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="29812-166">远程传送系统选择</span><span class="sxs-lookup"><span data-stu-id="29812-166">Teleportation system selection</span></span>

<span data-ttu-id="29812-167">混合现实项目提供了一个功能齐全的远程传送系统，用于管理项目中默认选择的远程传送事件。</span><span class="sxs-lookup"><span data-stu-id="29812-167">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="29812-168">空间感知设置</span><span class="sxs-lookup"><span data-stu-id="29812-168">Spatial awareness settings</span></span>

<span data-ttu-id="29812-169">混合现实项目提供重建的空间感知系统，用于在默认情况下选择的项目中使用空间扫描系统。</span><span class="sxs-lookup"><span data-stu-id="29812-169">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="29812-170">混合现实工具包的空间感知配置使你能够定制系统的启动方式，无论应用程序是在应用程序启动时自动启动还是在以后以编程方式设置，还可以为视图字段设置范围。</span><span class="sxs-lookup"><span data-stu-id="29812-170">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="29812-171">它还允许您配置网格和图面设置，进一步自定义您的项目如何理解您的环境。</span><span class="sxs-lookup"><span data-stu-id="29812-171">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="29812-172">这仅适用于可提供扫描环境的设备。</span><span class="sxs-lookup"><span data-stu-id="29812-172">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="29812-173">诊断设置</span><span class="sxs-lookup"><span data-stu-id="29812-173">Diagnostics settings</span></span>

<span data-ttu-id="29812-174">MRTK 的可选但非常有用的功能是插件诊断功能。</span><span class="sxs-lookup"><span data-stu-id="29812-174">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="29812-175">诊断配置文件提供了几个简单的系统，可以在项目运行时进行监视，包括便捷的 On/Off 开关，用于在场景中启用/禁用显示面板。</span><span class="sxs-lookup"><span data-stu-id="29812-175">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="29812-176">场景系统设置</span><span class="sxs-lookup"><span data-stu-id="29812-176">Scene system settings</span></span>

<span data-ttu-id="29812-177">MRTK 提供了此可选的服务，可帮助管理复杂的加法场景加载/卸载。</span><span class="sxs-lookup"><span data-stu-id="29812-177">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="29812-178">若要确定场景系统是否适合你的项目，请阅读 [场景系统入门指南。](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="29812-178">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="29812-179">其他服务设置</span><span class="sxs-lookup"><span data-stu-id="29812-179">Additional services settings</span></span>

<span data-ttu-id="29812-180">混合现实工具包的更高级的领域之一是其 [服务定位器模式](https://en.wikipedia.org/wiki/Service_locator_pattern) 实现，该实现允许向框架注册任何 "服务"。</span><span class="sxs-lookup"><span data-stu-id="29812-180">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="29812-181">这样，就可以轻松地使用新功能/系统扩展框架，还可以利用这些功能来注册自己的运行时组件。</span><span class="sxs-lookup"><span data-stu-id="29812-181">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="29812-182">任何注册的服务仍能充分利用所有 Unity 事件，而无需执行 MonoBehaviour 或笨单一实例模式的开销和成本。</span><span class="sxs-lookup"><span data-stu-id="29812-182">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="29812-183">这就允许在运行前台和后台进程（例如，生成系统、运行时游戏逻辑或几乎任何其他操作）时不具有场景开销的纯 c # 组件。</span><span class="sxs-lookup"><span data-stu-id="29812-183">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="29812-184">输入操作设置</span><span class="sxs-lookup"><span data-stu-id="29812-184">Input actions settings</span></span>

<span data-ttu-id="29812-185">输入操作提供了一种从运行时项目中抽象任何物理交互和输入的方法。</span><span class="sxs-lookup"><span data-stu-id="29812-185">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="29812-186">控制器/ (/鼠标/等) 输入的所有物理输入将转换为逻辑输入操作，以用于运行时项目。</span><span class="sxs-lookup"><span data-stu-id="29812-186">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="29812-187">这可确保无论输入来自何处，项目都只是在后台将这些操作实现为"要执行的操作"或"交互"。</span><span class="sxs-lookup"><span data-stu-id="29812-187">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="29812-188">若要创建新的输入操作，只需单击"添加新操作"按钮，并输入其表示的友好文本名称。</span><span class="sxs-lookup"><span data-stu-id="29812-188">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="29812-189">然后，只需选择 (数据类型的轴) 用于传达操作，或者对于物理控制器，它可附加到的物理输入类型，例如：</span><span class="sxs-lookup"><span data-stu-id="29812-189">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="29812-190">轴约束</span><span class="sxs-lookup"><span data-stu-id="29812-190">Axis Constraint</span></span> | <span data-ttu-id="29812-191">数据类型</span><span class="sxs-lookup"><span data-stu-id="29812-191">Data Type</span></span> | <span data-ttu-id="29812-192">说明</span><span class="sxs-lookup"><span data-stu-id="29812-192">Description</span></span> | <span data-ttu-id="29812-193">用法示例</span><span class="sxs-lookup"><span data-stu-id="29812-193">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="29812-194">无</span><span class="sxs-lookup"><span data-stu-id="29812-194">None</span></span> | <span data-ttu-id="29812-195">无数据</span><span class="sxs-lookup"><span data-stu-id="29812-195">No data</span></span> | <span data-ttu-id="29812-196">用于空操作或事件</span><span class="sxs-lookup"><span data-stu-id="29812-196">Used for an empty action or event</span></span> | <span data-ttu-id="29812-197">事件触发器</span><span class="sxs-lookup"><span data-stu-id="29812-197">Event Trigger</span></span> |
| <span data-ttu-id="29812-198">原始 (预留) </span><span class="sxs-lookup"><span data-stu-id="29812-198">Raw (reserved)</span></span> | <span data-ttu-id="29812-199">object</span><span class="sxs-lookup"><span data-stu-id="29812-199">object</span></span> | <span data-ttu-id="29812-200">保留以供将来使用</span><span class="sxs-lookup"><span data-stu-id="29812-200">Reserved for future use</span></span> | <span data-ttu-id="29812-201">不适用</span><span class="sxs-lookup"><span data-stu-id="29812-201">N/A</span></span> |
| <span data-ttu-id="29812-202">数码</span><span class="sxs-lookup"><span data-stu-id="29812-202">Digital</span></span> | <span data-ttu-id="29812-203">bool</span><span class="sxs-lookup"><span data-stu-id="29812-203">bool</span></span> | <span data-ttu-id="29812-204">打开或关闭类型数据的布尔值</span><span class="sxs-lookup"><span data-stu-id="29812-204">A boolean on or off type data</span></span> | <span data-ttu-id="29812-205">控制器按钮</span><span class="sxs-lookup"><span data-stu-id="29812-205">A controller button</span></span> |
| <span data-ttu-id="29812-206">单轴</span><span class="sxs-lookup"><span data-stu-id="29812-206">Single Axis</span></span> | <span data-ttu-id="29812-207">FLOAT</span><span class="sxs-lookup"><span data-stu-id="29812-207">float</span></span> | <span data-ttu-id="29812-208">单个精度数据值</span><span class="sxs-lookup"><span data-stu-id="29812-208">A single precision data value</span></span> | <span data-ttu-id="29812-209">范围输入，例如触发器</span><span class="sxs-lookup"><span data-stu-id="29812-209">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="29812-210">双轴</span><span class="sxs-lookup"><span data-stu-id="29812-210">Dual Axis</span></span> | <span data-ttu-id="29812-211">Vector2</span><span class="sxs-lookup"><span data-stu-id="29812-211">Vector2</span></span> | <span data-ttu-id="29812-212">多个轴的双浮点类型日期</span><span class="sxs-lookup"><span data-stu-id="29812-212">A dual float type date for multiple axis</span></span> | <span data-ttu-id="29812-213">Dpad 或 Thumbstick</span><span class="sxs-lookup"><span data-stu-id="29812-213">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="29812-214">三个 Dof 位置</span><span class="sxs-lookup"><span data-stu-id="29812-214">Three Dof Position</span></span> | <span data-ttu-id="29812-215">Vector3</span><span class="sxs-lookup"><span data-stu-id="29812-215">Vector3</span></span> | <span data-ttu-id="29812-216">具有 3 个浮点轴的 中的位置类型数据</span><span class="sxs-lookup"><span data-stu-id="29812-216">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="29812-217">仅 3D 位置样式控制器</span><span class="sxs-lookup"><span data-stu-id="29812-217">3D position style only controller</span></span> |
| <span data-ttu-id="29812-218">三个 Dof 旋转</span><span class="sxs-lookup"><span data-stu-id="29812-218">Three Dof Rotation</span></span> | <span data-ttu-id="29812-219">四元</span><span class="sxs-lookup"><span data-stu-id="29812-219">Quaternion</span></span> | <span data-ttu-id="29812-220">仅旋转4浮点轴的输入</span><span class="sxs-lookup"><span data-stu-id="29812-220">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="29812-221">三度样式的控制器，例如 Oculus 控制器</span><span class="sxs-lookup"><span data-stu-id="29812-221">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="29812-222">6 Dof</span><span class="sxs-lookup"><span data-stu-id="29812-222">Six Dof</span></span> | <span data-ttu-id="29812-223">混合现实姿势 (System.numerics.vector2，四元数) </span><span class="sxs-lookup"><span data-stu-id="29812-223">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="29812-224">使用 System.numerics.vector2 和四元数分量的位置和旋转样式输入</span><span class="sxs-lookup"><span data-stu-id="29812-224">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="29812-225">运动控制器或指针</span><span class="sxs-lookup"><span data-stu-id="29812-225">A motion controller or Pointer</span></span> |

<span data-ttu-id="29812-226">使用输入操作的事件并不限于物理控制器，仍可在项目中使用，以使运行时效果生成新的操作。</span><span class="sxs-lookup"><span data-stu-id="29812-226">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="29812-227">输入操作是无法在运行时编辑的几个组件之一，它们只是设计时配置。</span><span class="sxs-lookup"><span data-stu-id="29812-227">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="29812-228">由于框架 (，不应将此配置文件换出，且项目) 依赖于为每个操作生成的 ID。</span><span class="sxs-lookup"><span data-stu-id="29812-228">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="29812-229">输入操作规则</span><span class="sxs-lookup"><span data-stu-id="29812-229">Input actions rules</span></span>

<span data-ttu-id="29812-230">输入操作规则提供了一种方法，用于根据其数据值将对中的一个输入操作引发的事件自动转换为不同的操作。</span><span class="sxs-lookup"><span data-stu-id="29812-230">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="29812-231">它们在框架内无缝管理，不会产生任何性能开销。</span><span class="sxs-lookup"><span data-stu-id="29812-231">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="29812-232">例如，将单个双轴输入事件从中的 DPad 转换为4对应的 "Dpad Up"/"DPad 向下"/"Dpad 左"/"Dpad Right" 操作 (如下图所示) 。</span><span class="sxs-lookup"><span data-stu-id="29812-232">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="29812-233">也可以在自己的代码中完成此操作。</span><span class="sxs-lookup"><span data-stu-id="29812-233">This could also be done in your own code.</span></span> <span data-ttu-id="29812-234">不过，由于这是一种非常常见的模式，因此框架提供了一种机制来实现这种 "现成"</span><span class="sxs-lookup"><span data-stu-id="29812-234">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="29812-235">可以为任何可用输入轴配置输入操作规则。</span><span class="sxs-lookup"><span data-stu-id="29812-235">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="29812-236">但是，可以将一个轴类型的输入操作转换为同一轴类型的另一个输入操作。</span><span class="sxs-lookup"><span data-stu-id="29812-236">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="29812-237">可以将双轴操作映射到另一个双轴操作，但不能映射到数字或无操作。</span><span class="sxs-lookup"><span data-stu-id="29812-237">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![输入操作规则配置文件](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="29812-239">指针配置</span><span class="sxs-lookup"><span data-stu-id="29812-239">Pointer configuration</span></span>

<span data-ttu-id="29812-240">指针用于驱动来自任何输入设备的场景中的交互性，从而对场景中的任何对象提供方向和命中测试 (该对象附加了碰撞体或是 UI 组件) 。</span><span class="sxs-lookup"><span data-stu-id="29812-240">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="29812-241">默认情况下，会自动为控制器、头戴显示设备配置 (/焦点) 和鼠标/触摸输入。</span><span class="sxs-lookup"><span data-stu-id="29812-241">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="29812-242">此外，还可使用混合现实工具包提供的众多行组件之一在活动场景中可视化指针，如果它们实现 MRTK IMixedRealityPointer 接口，也可以可视化自己的任何一个。</span><span class="sxs-lookup"><span data-stu-id="29812-242">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="29812-243">指向范围：确定所有指针（包括凝视）的全局指向范围。</span><span class="sxs-lookup"><span data-stu-id="29812-243">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="29812-244">指向光线广播层掩码：确定指针将针对哪些层进行光线广播。</span><span class="sxs-lookup"><span data-stu-id="29812-244">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="29812-245">调试绘制指向射线：用于可视化用于光线广播的射线的调试帮助程序。</span><span class="sxs-lookup"><span data-stu-id="29812-245">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="29812-246">调试绘制指向射线颜色：用于可视化的一组颜色。</span><span class="sxs-lookup"><span data-stu-id="29812-246">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="29812-247">凝视光标预制件：可轻松指定任何场景的全局凝视光标。</span><span class="sxs-lookup"><span data-stu-id="29812-247">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="29812-248">有一个附加的帮助器按钮，可根据需要快速跳转到凝视提供程序，以替代凝视的一些特定值。</span><span class="sxs-lookup"><span data-stu-id="29812-248">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="29812-249">笔势配置</span><span class="sxs-lookup"><span data-stu-id="29812-249">Gestures configuration</span></span>

<span data-ttu-id="29812-250">手势是一种特定于系统的实现，允许将输入操作分配给各种 SDK 提供的各种"笔势"输入 (例如 HoloLens) 。</span><span class="sxs-lookup"><span data-stu-id="29812-250">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="29812-251">当前的笔势实现仅适用于 HoloLens，并且将针对其他系统进行增强，因为将来这些系统将添加到工具包 (尚未) 。</span><span class="sxs-lookup"><span data-stu-id="29812-251">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="29812-252">语音命令</span><span class="sxs-lookup"><span data-stu-id="29812-252">Speech commands</span></span>

<span data-ttu-id="29812-253">与笔势一样，某些运行时平台语音转文本智能"命令"功能，能够生成 Unity 项目可以接收的命令。</span><span class="sxs-lookup"><span data-stu-id="29812-253">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="29812-254">此配置文件允许配置以下各项：</span><span class="sxs-lookup"><span data-stu-id="29812-254">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="29812-255">常规设置 - 设置为"自动启动"或"手动启动"的"启动行为"确定是初始化输入系统启动时的 KeywordRecognizer，还是让项目决定何时初始化 KeywordRecognizer。</span><span class="sxs-lookup"><span data-stu-id="29812-255">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="29812-256">"识别置信度"用于初始化 Unity 的 [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span><span class="sxs-lookup"><span data-stu-id="29812-256">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="29812-257">语音命令 - 注册"单词"，并将其转换为项目可以接收的输入操作。</span><span class="sxs-lookup"><span data-stu-id="29812-257">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="29812-258">如果需要，还可以将键盘操作附加到键盘操作。</span><span class="sxs-lookup"><span data-stu-id="29812-258">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29812-259">系统目前仅在 Windows 10 平台（例如 HoloLens 和 Windows 10 桌面）上运行时支持语音，并且将针对其他系统进行增强，因为将来会添加到 MRTK 中 (尚未) 。</span><span class="sxs-lookup"><span data-stu-id="29812-259">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="29812-260">控制器映射配置</span><span class="sxs-lookup"><span data-stu-id="29812-260">Controller mapping configuration</span></span>

<span data-ttu-id="29812-261">混合现实工具包的核心配置屏幕之一是能够配置和映射项目可以使用的各种类型的控制器。</span><span class="sxs-lookup"><span data-stu-id="29812-261">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="29812-262">下面的配置屏幕允许配置工具包当前识别的任何控制器。</span><span class="sxs-lookup"><span data-stu-id="29812-262">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="29812-263">MRTK 为以下控制器/系统提供默认配置：</span><span class="sxs-lookup"><span data-stu-id="29812-263">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="29812-264">鼠标 (包括三维空间鼠标支持) </span><span class="sxs-lookup"><span data-stu-id="29812-264">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="29812-265">触摸屏手机</span><span class="sxs-lookup"><span data-stu-id="29812-265">Touch Screen</span></span>
- <span data-ttu-id="29812-266">Xbox 控制器</span><span class="sxs-lookup"><span data-stu-id="29812-266">Xbox controllers</span></span>
- <span data-ttu-id="29812-267">Windows Mixed Reality控制器</span><span class="sxs-lookup"><span data-stu-id="29812-267">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="29812-268">HoloLens 笔势</span><span class="sxs-lookup"><span data-stu-id="29812-268">HoloLens Gestures</span></span>
- <span data-ttu-id="29812-269">用于 WANVive Wand 控制器的</span><span class="sxs-lookup"><span data-stu-id="29812-269">HTC Vive wand controllers</span></span>
- <span data-ttu-id="29812-270">Oculus Touch 控制器</span><span class="sxs-lookup"><span data-stu-id="29812-270">Oculus Touch controllers</span></span>
- <span data-ttu-id="29812-271">Oculus 远程控制器</span><span class="sxs-lookup"><span data-stu-id="29812-271">Oculus Remote controller</span></span>
- <span data-ttu-id="29812-272">通用 OpenVR 设备 (高级用户) </span><span class="sxs-lookup"><span data-stu-id="29812-272">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="29812-273">单击任何预建控制器系统的"映像"，可以针对其所有相应输入配置单个输入操作，例如，请参阅下面的 Oculus Touch 控制器配置屏幕：</span><span class="sxs-lookup"><span data-stu-id="29812-273">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="29812-274">还有一个高级屏幕，用于配置上面未标识的其他 OpenVR 或 Unity 输入控制器。</span><span class="sxs-lookup"><span data-stu-id="29812-274">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="29812-275">控制器可视化设置</span><span class="sxs-lookup"><span data-stu-id="29812-275">Controller visualization settings</span></span>

<span data-ttu-id="29812-276">除了控制器映射，还提供了单独的配置文件来自定义控制器在场景中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="29812-276">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="29812-277">可以在控制器的所有实例的"全局" (配置此配置，) 或特定于单个控制器类型/手部。</span><span class="sxs-lookup"><span data-stu-id="29812-277">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="29812-278">MRTK 还支持适用于 Windows Mixed Reality OpenVR 的本机 SDK 控制器模型。</span><span class="sxs-lookup"><span data-stu-id="29812-278">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="29812-279">这些对象作为 GameObjects 加载到场景中，使用平台的控制器跟踪进行定位。</span><span class="sxs-lookup"><span data-stu-id="29812-279">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="29812-280">如果场景中的控制器表示形式需要与物理控制器位置偏移，则只需针对控制器模型的预制项设置该偏移量 (例如，使用偏移位置) 设置控制器预制的转换位置。</span><span class="sxs-lookup"><span data-stu-id="29812-280">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="29812-281">编辑器实用工具</span><span class="sxs-lookup"><span data-stu-id="29812-281">Editor utilities</span></span>

<span data-ttu-id="29812-282">以下实用工具仅在编辑器中工作，可用于提高开发效率。</span><span class="sxs-lookup"><span data-stu-id="29812-282">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![MRTK 编辑器配置实用工具](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="29812-284">服务检查器</span><span class="sxs-lookup"><span data-stu-id="29812-284">Service inspectors</span></span>

<span data-ttu-id="29812-285">服务检查器是一项仅编辑器功能，可生成表示活动服务的场景中对象。</span><span class="sxs-lookup"><span data-stu-id="29812-285">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="29812-286">选择这些对象将显示检查器，这些检查器提供文档链接、控制编辑器可视化效果和深入了解服务状态。</span><span class="sxs-lookup"><span data-stu-id="29812-286">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="29812-287">可以通过在配置文件的"编辑器设置"下选中"使用服务 *检查* 器" *来* 启用服务检查器。</span><span class="sxs-lookup"><span data-stu-id="29812-287">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="29812-288">深度缓冲区呈现器</span><span class="sxs-lookup"><span data-stu-id="29812-288">Depth buffer renderer</span></span>

<span data-ttu-id="29812-289">与一些混合现实平台共享深度缓冲区可以提高 [全息影像稳定性](../performance/hologram-stabilization.md)。</span><span class="sxs-lookup"><span data-stu-id="29812-289">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="29812-290">例如，Windows Mixed Reality平台可以修改每个像素呈现的场景，以考虑呈现帧所花时间的细微头部运动。</span><span class="sxs-lookup"><span data-stu-id="29812-290">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="29812-291">但是，这些技术需要使用具有准确数据的深度缓冲区来了解几何图形与用户的位置和距离。</span><span class="sxs-lookup"><span data-stu-id="29812-291">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="29812-292">为了确保场景将所有必要的数据呈现到深度缓冲区，开发人员可以在配置文件中的"编辑器设置"下切换"呈现深度缓冲区"功能。</span><span class="sxs-lookup"><span data-stu-id="29812-292">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="29812-293">这会采用当前深度缓冲区，通过向主相机应用后处理效果，以颜色呈现给 [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) 场景视图。</span><span class="sxs-lookup"><span data-stu-id="29812-293">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="29812-294">![呈现深度缓冲区实用程序 ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>场景中的蓝色圆柱体的材料具有 ZWrite off，因此不会写入深度数据</sup></span><span class="sxs-lookup"><span data-stu-id="29812-294">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="29812-295">在运行时更改配置文件</span><span class="sxs-lookup"><span data-stu-id="29812-295">Changing profiles at runtime</span></span>

<span data-ttu-id="29812-296">在运行时可以更新配置文件，但在这种情况下，通常有两种不同的方案和时间：</span><span class="sxs-lookup"><span data-stu-id="29812-296">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="29812-297">**预 MRTK 初始化配置文件开关**：在启动时，在初始化 MRTK 之前，并将配置文件变为活动状态，替换不使用的配置文件，根据设备功能启用/禁用不同的功能。</span><span class="sxs-lookup"><span data-stu-id="29812-297">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="29812-298">例如，如果在不具有空间映射硬件的 VR 中运行体验，则启用空间映射组件可能没有意义。</span><span class="sxs-lookup"><span data-stu-id="29812-298">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="29812-299">**活动配置文件切换**：启动后，在初始化 MRTK 并激活配置文件后，交换当前正在使用的配置文件，以更改特定功能的行为方式。</span><span class="sxs-lookup"><span data-stu-id="29812-299">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="29812-300">例如，应用程序中可能有特定的子体验，需要完全删除最多的指针。</span><span class="sxs-lookup"><span data-stu-id="29812-300">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="29812-301">预 MRTK 初始化配置文件开关</span><span class="sxs-lookup"><span data-stu-id="29812-301">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="29812-302">为此，可将下面的 MonoBehaviour (示例附加到 MRTK 初始化之前运行的) ， (即唤醒 () ) 。</span><span class="sxs-lookup"><span data-stu-id="29812-302">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="29812-303">请注意，脚本 (例如，对 `SetProfileBeforeInitialization`) 的调用必须早于脚本执行 `MixedRealityToolkit` ，这可以通过设置 [脚本执行顺序设置](https://docs.unity3d.com/Manual/class-MonoManager.html)来实现。</span><span class="sxs-lookup"><span data-stu-id="29812-303">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

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

<span data-ttu-id="29812-304"> (例如，一组适用于特定平台的任意配置文件，而不是 "profileToUse"，例如，一个用于 VR，一个用于 VR 2，等等) 。</span><span class="sxs-lookup"><span data-stu-id="29812-304">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="29812-305">可以使用各种其他指标 (例如 https://docs.unity3d.com/ScriptReference/SystemInfo.html ，或照相机是否为不透明/透明) ，以确定要加载的配置文件。</span><span class="sxs-lookup"><span data-stu-id="29812-305">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="29812-306">活动配置文件开关</span><span class="sxs-lookup"><span data-stu-id="29812-306">Active profile switch</span></span>

<span data-ttu-id="29812-307">可以通过将 `MixedRealityToolkit.Instance.ActiveProfile` 属性设置为替换活动配置文件的新配置文件来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="29812-307">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="29812-308">注意当在 `ActiveProfile` 运行时进行设置时，当前正在运行的服务将在所有服务的最后一个 behaviour () 之后发生，并且与新配置文件关联的服务的实例化和初始化将发生在所有服务的第一次更新 () 之前。</span><span class="sxs-lookup"><span data-stu-id="29812-308">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="29812-309">在此过程中可能会出现明显的应用程序毫不迟疑。</span><span class="sxs-lookup"><span data-stu-id="29812-309">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="29812-310">此外，任何优先级高于脚本的脚本 `MixedRealityToolkit` 都可以在正确设置新的配置文件之前输入其更新。</span><span class="sxs-lookup"><span data-stu-id="29812-310">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="29812-311">有关脚本优先级的详细信息，请参阅 [脚本执行顺序设置](https://docs.unity3d.com/Manual/class-MonoManager.html) 。</span><span class="sxs-lookup"><span data-stu-id="29812-311">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="29812-312">在配置文件切换过程中，现有的 UI 照相机会保持不变，确保在开关后需要画布的 Unity UI 组件仍可正常工作。</span><span class="sxs-lookup"><span data-stu-id="29812-312">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="29812-313">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29812-313">See also</span></span>

- [<span data-ttu-id="29812-314">全息影像稳定化</span><span class="sxs-lookup"><span data-stu-id="29812-314">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)