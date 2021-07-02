---
title: MRTK 2.7 发行说明
description: MRTK 版本 2.7 发行说明
author: RogPodge
ms.author: roliu
ms.date: 06/16/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK, XRSDK, 旧版 XR, Leap Motion, Ultraleap, OpenXR
ms.localizationpriority: high
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 8f6c68c067df735761dd9c162c71fd85f1f3e132
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906973"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a><span data-ttu-id="a88a6-104">Microsoft 混合现实工具包 2.7 发行说明</span><span class="sxs-lookup"><span data-stu-id="a88a6-104">Microsoft Mixed Reality Toolkit 2.7 Release Notes</span></span>

## <a name="whats-new-in-272"></a><span data-ttu-id="a88a6-105">2\.7.2 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="a88a6-105">What's new in 2.7.2</span></span>

### <a name="fixed-a-upm-package-dependency-issue"></a><span data-ttu-id="a88a6-106">修复了一个 UPM 包依赖关系问题</span><span class="sxs-lookup"><span data-stu-id="a88a6-106">Fixed a UPM package dependency issue</span></span>

<span data-ttu-id="a88a6-107">MRTK 2.7.1 UPM 包中存在一个未正确设置依赖关系的问题。</span><span class="sxs-lookup"><span data-stu-id="a88a6-107">There is an issue with MRTK 2.7.1 UPM packages where the dependencies were not set up correctly.</span></span> <span data-ttu-id="a88a6-108">该问题会导致混合现实功能工具无法正确导入 MRTK 2.7.1 包。</span><span class="sxs-lookup"><span data-stu-id="a88a6-108">The issue caused the Mixed Reality Feature Tool to fail to import MRTK 2.7.1 packages properly.</span></span> <span data-ttu-id="a88a6-109">该问题现已在 2.7.2 中得到解决。</span><span class="sxs-lookup"><span data-stu-id="a88a6-109">The issue is now resolved in 2.7.2.</span></span> <span data-ttu-id="a88a6-110">与 2.7.1 相比，此版本中的代码未有更改。</span><span class="sxs-lookup"><span data-stu-id="a88a6-110">There is no code change in this version compared to 2.7.1.</span></span>


## <a name="whats-new-in-271"></a><span data-ttu-id="a88a6-111">2\.7.1 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="a88a6-111">What's new in 2.7.1</span></span>

### <a name="show-version"></a><span data-ttu-id="a88a6-112">显示版本</span><span class="sxs-lookup"><span data-stu-id="a88a6-112">Show version</span></span>

<span data-ttu-id="a88a6-113">`Mixed Reality` > `Toolkit` 菜单现在包含一个 `Show version...` 项，该项可用于检查混合现实工具包基础包，以确定项目所使用的 MRTK 版本。</span><span class="sxs-lookup"><span data-stu-id="a88a6-113">The `Mixed Reality` > `Toolkit` menu now contains a `Show version...` entry that examines the Mixed Reality Toolkit Foundation package to determine the version of MRTK that is being used by the project.</span></span>

![显示版本菜单](images/ShowVersionMenu.png)

![MRTK 版本对话框](images/VersionDialog.png)

> [!NOTE]
> <span data-ttu-id="a88a6-116">如果 MRTK 是从 [GitHub 存储库](https://aka.ms/mrtk)克隆的，则不会设置版本信息。</span><span class="sxs-lookup"><span data-stu-id="a88a6-116">If MRTK was cloned from the [GitHub repository](https://aka.ms/mrtk), the version information will not have been set.</span></span>
>
> ![无法确定版本](images/CannotDetermineVersion.png)

### <a name="authors-list"></a><span data-ttu-id="a88a6-118">作者列表</span><span class="sxs-lookup"><span data-stu-id="a88a6-118">Authors list</span></span>

<span data-ttu-id="a88a6-119">从 MRTK 2.7.1 开始，混合现实工具包基础包中包含了作者列表文件。</span><span class="sxs-lookup"><span data-stu-id="a88a6-119">Starting with MRTK 2.7.1, the authors list file is included in the Mixed Reality Toolkit Foundation package.</span></span>

### <a name="integrated-openxr-project-setup-into-the-configurator-setup-flow"></a><span data-ttu-id="a88a6-120">在配置器设置流中集成了 OpenXR 项目设置</span><span class="sxs-lookup"><span data-stu-id="a88a6-120">Integrated OpenXR project setup into the Configurator setup flow</span></span>

<span data-ttu-id="a88a6-121">从 MRTK 2.7.1 开始，混合现实 OpenXR 插件的用户将收到有关如何通过 MRTK 设置该插件的说明。</span><span class="sxs-lookup"><span data-stu-id="a88a6-121">Starting with MRTK 2.7.1, users of the Mixed Reality OpenXR plugin will receive instructions on how to set up that plugin with MRTK.</span></span> <span data-ttu-id="a88a6-122">有一个选项可供以 HoloLens 2 为目标的用户自动应用建议的设置。</span><span class="sxs-lookup"><span data-stu-id="a88a6-122">There is an option for users targeting HoloLens 2 to apply recommended settings automatically.</span></span>

![包含 OpenXR 设置说明的配置器窗口](images/configuratorMROpenXR.png)

### <a name="notable-bugfixes-and-changes"></a><span data-ttu-id="a88a6-124">值得注意的 Bug 修复和更改</span><span class="sxs-lookup"><span data-stu-id="a88a6-124">Notable Bugfixes and Changes</span></span>

- <span data-ttu-id="a88a6-125">已将 Unity Joystick Manager 标记为在 XR SDK 管道上受支持 [#9954](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9954)、[#9994](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9994)</span><span class="sxs-lookup"><span data-stu-id="a88a6-125">Marked Unity Joystick Manager as supported on XR SDK pipeline [#9954](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9954), [#9994](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9994)</span></span>
- <span data-ttu-id="a88a6-126">添加了对可交互检查器代码的检查，以防止出现 null 错误 [#9943](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9943)</span><span class="sxs-lookup"><span data-stu-id="a88a6-126">Added checks to interactable inspector code to prevent null errors [#9943](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9943)</span></span>
- <span data-ttu-id="a88a6-127">在脉冲着色器示例场景中添加了 OpenXR 网格提供程序 [#9902](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9902)</span><span class="sxs-lookup"><span data-stu-id="a88a6-127">Add OpenXR mesh provider to pulse shader example scene [#9902](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9902)</span></span>
- <span data-ttu-id="a88a6-128">在示例场景中还原了手部物理特性配置文件 [#9915](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9915)</span><span class="sxs-lookup"><span data-stu-id="a88a6-128">Restore hand physics profile to example scene [#9915](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9915)</span></span>
- <span data-ttu-id="a88a6-129">对 HandConstraint\* 脚本做了一些清理 [#9935](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9935)</span><span class="sxs-lookup"><span data-stu-id="a88a6-129">Some cleanup to the HandConstraint\* scripts [#9935](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9935)</span></span>
- <span data-ttu-id="a88a6-130">修复了一些会影响创建和克隆配置文件的 bug [#9982](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9982)</span><span class="sxs-lookup"><span data-stu-id="a88a6-130">Fixed some bugs affecting creating and cloning profiles [#9982](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9982)</span></span>


## <a name="whats-new-in-270"></a><span data-ttu-id="a88a6-131">2\.7.0 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="a88a6-131">What's new in 2.7.0</span></span>

### <a name="openxr-is-now-officially-supported-in-mrtk"></a><span data-ttu-id="a88a6-132">OpenXR 现已在 MRTK 中正式受支持</span><span class="sxs-lookup"><span data-stu-id="a88a6-132">OpenXR is now officially supported in MRTK</span></span>

<span data-ttu-id="a88a6-133">随着新的 OpenXR 插件变得越来越成熟，MRTK 现已正式支持 OpenXR。</span><span class="sxs-lookup"><span data-stu-id="a88a6-133">As the new OpenXR plugins are becoming more and more mature MRTK now officially supports OpenXR.</span></span> <span data-ttu-id="a88a6-134">与以前的版本相比，我们在使用 OpenXR 的项目中添加了以下功能：</span><span class="sxs-lookup"><span data-stu-id="a88a6-134">Compared to previous releases we added the following capabilities to projects using OpenXR:</span></span>

- [<span data-ttu-id="a88a6-135">支持系统提供的运动控制器模型</span><span class="sxs-lookup"><span data-stu-id="a88a6-135">Support for the system-provided motion controller model</span></span>](#support-for-the-system-provided-motion-controller-model-on-openxr)
- <span data-ttu-id="a88a6-136">支持 WinMR 手势（选择、保持、操控和导航）[#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)</span><span class="sxs-lookup"><span data-stu-id="a88a6-136">Support for WinMR gestures (select, hold, manipulation and navigation) [#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)</span></span>
- [<span data-ttu-id="a88a6-137">支持控制器触觉</span><span class="sxs-lookup"><span data-stu-id="a88a6-137">Support for controller haptics</span></span>](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [<span data-ttu-id="a88a6-138">支持 HoloLens 2 上的铰接式手部网格</span><span class="sxs-lookup"><span data-stu-id="a88a6-138">Support for articulated hand mesh on HoloLens 2</span></span>](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- <span data-ttu-id="a88a6-139">支持 HoloLens 2 上的空间映射 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567)、[#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)</span><span class="sxs-lookup"><span data-stu-id="a88a6-139">Support for Spatial Mapping on HoloLens 2 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567), [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)</span></span>
- <span data-ttu-id="a88a6-140">支持 HoloLens 2 上的场景理解 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)</span><span class="sxs-lookup"><span data-stu-id="a88a6-140">Support for Scene Understanding on HoloLens 2 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)</span></span>

<span data-ttu-id="a88a6-141">如果你通过 OpenXR 将 HoloLens 2 或 Windows Mixed Reality 头戴显示设备用作目标，请确保通过[混合现实功能工具](https://aka.ms/MRFeatureTool)安装/更新到混合现实 OpenXR 插件版本 0.9.5 或更高版本，否则你可能会错过上述某些改进。</span><span class="sxs-lookup"><span data-stu-id="a88a6-141">If you are targeting HoloLens 2 or Windows Mixed Reality headsets via OpenXR please make sure to install/update to **Mixed Reality OpenXR plugin version 0.9.5 or later** via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool), otherwise you might miss some of the improvements above.</span></span>

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a><span data-ttu-id="a88a6-142">现在可以在同一配置文件中使用旧版 XR 和 XR SDK 数据提供程序</span><span class="sxs-lookup"><span data-stu-id="a88a6-142">Legacy XR and XR SDK Data Providers can now be used within the same profile</span></span>

<span data-ttu-id="a88a6-143">现在，仅当选择了相应的管道时，才会加载数据提供程序，使得旧版 XR 和 XR SDK 数据提供程序可共存于同一个配置文件中。</span><span class="sxs-lookup"><span data-stu-id="a88a6-143">Data providers will now also only be loaded when the appropriate pipeline is selected, allowing both Legacy XR and XR SDK data providers to co-exist within the same profile.</span></span> <span data-ttu-id="a88a6-144">为了适应这种变化，旧版 XR 和 XR SDK 数据提供程序现已组织在配置文件视图中的不同选项卡下，帮助用户确定他们是否对其目标 XR 管道使用了正确的配置文件。</span><span class="sxs-lookup"><span data-stu-id="a88a6-144">To accommodate this, Legacy XR and XR SDK Data Providers are now organized under different tabs within the profile view, helping users determine whether they have the correct profile for their targeted XR pipeline.</span></span>

![旧版数据提供程序和 XR SDK 数据提供程序现在可在单个配置文件下统一](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

<span data-ttu-id="a88a6-146">为了适应这种变化，null 数据提供程序现在不再会加载并显示在配置文件检查器中。</span><span class="sxs-lookup"><span data-stu-id="a88a6-146">To accommodate this, null data providers will now no longer be loaded and displayed in the profile inspector.</span></span> <span data-ttu-id="a88a6-147">用户可以在“编辑”->“项目设置”->“混合现实工具包”下切换 `Show null data providers in the profile inspector`，以调试在缺少数据提供程序时发生的意外行为。</span><span class="sxs-lookup"><span data-stu-id="a88a6-147">Users can toggle `Show null data providers in the profile inspector` under **Edit -> Project Settings -> Mixed Reality Toolkit** to debug unexpected behaviors with missing data providers.</span></span>

<span data-ttu-id="a88a6-148">![Null 数据提供程序现在默认已隐藏](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
![切换“在配置文件检查器中显示 null 数据提供程序”设置](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)</span><span class="sxs-lookup"><span data-stu-id="a88a6-148">![Null data providers are now hidden by default](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
![Toggle show null data providers in the profile inspector](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)</span></span>

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a><span data-ttu-id="a88a6-149">添加了体验设置和一个关联的混合现实场景内容行为</span><span class="sxs-lookup"><span data-stu-id="a88a6-149">Added Experience Settings and an associated Mixed Reality Scene Content behavior</span></span>

<span data-ttu-id="a88a6-150">用户现在可以配置[体验设置](../features/experience-settings/experience-settings.md)，使得 MRTK 能够根据目标体验适当显示[混合现实场景内容](../features/experience-settings/scene-content.md)。</span><span class="sxs-lookup"><span data-stu-id="a88a6-150">Users can now configure [Experience Settings](../features/experience-settings/experience-settings.md), which will allow MRTK to display [Mixed Reality Scene Content](../features/experience-settings/scene-content.md) appropriately based on the targeted experience.</span></span>

<span data-ttu-id="a88a6-151">如果用户以前的“体验规模”设置与新的体验设置配置文件不匹配，系统会提示他们在检查器中进行更正</span><span class="sxs-lookup"><span data-stu-id="a88a6-151">If user's previous Experience Scale settings do not match the new Experience Settings Profile, they will be prompted to correct it in the inspector</span></span>

![体验规模迁移](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a><span data-ttu-id="a88a6-153">重新设计的配置器现在会指导用户完成设置过程</span><span class="sxs-lookup"><span data-stu-id="a88a6-153">The Redesigned Configurator now guides the user through the setup process</span></span>

<span data-ttu-id="a88a6-154">新的 MRTK 配置器为用户提供分步指导，使他们能够正确配置项目以进行 XR 开发，并将其与 MRTK 配合使用。</span><span class="sxs-lookup"><span data-stu-id="a88a6-154">The new MRTK configurator provides users step-by-step guidance to properly configure the project for XR development and use with MRTK.</span></span> <span data-ttu-id="a88a6-155">在该配置器中可以选择 XR 管道、获取特定于平台的插件、导入 TextMeshPro，并显示示例（在使用 UPM 时）以及以前包含的为项目建议的设置。</span><span class="sxs-lookup"><span data-stu-id="a88a6-155">It covers the selection of XR pipeline, getting the platform specific plugins, importing TextMeshPro, displaying the examples (when using UPM) and other previously included recommended settings for the project.</span></span>

![显示管道列表的配置器](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a><span data-ttu-id="a88a6-157">正式推出了传送热点</span><span class="sxs-lookup"><span data-stu-id="a88a6-157">Graduated Teleport Hotspot</span></span>

<span data-ttu-id="a88a6-158">已正式推出一个新的[传送热点组件](../features/teleport-system/teleport-hotspot.md)。</span><span class="sxs-lookup"><span data-stu-id="a88a6-158">A new [teleport hotspot component](../features/teleport-system/teleport-hotspot.md) has been graduated.</span></span> <span data-ttu-id="a88a6-159">你可以将传送热点添加到 GameObject，以确保用户在传送到特定位置时处于该特定位置和方位。</span><span class="sxs-lookup"><span data-stu-id="a88a6-159">You can add a teleport hotspot to your GameObject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

![传送热点示例](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a><span data-ttu-id="a88a6-161">正式推出了停留功能</span><span class="sxs-lookup"><span data-stu-id="a88a6-161">Graduated Dwell</span></span>

<span data-ttu-id="a88a6-162">在经过试验后，停留功能和示例现已正式推出。</span><span class="sxs-lookup"><span data-stu-id="a88a6-162">The dwell feature and example is now graduated from experimental.</span></span> <span data-ttu-id="a88a6-163">示例场景中包含容积型 HoloLens 2 样式按钮的新示例。</span><span class="sxs-lookup"><span data-stu-id="a88a6-163">New examples of volumetric HoloLens 2 style buttons are included in the sample scene.</span></span>

![停留功能主图](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a><span data-ttu-id="a88a6-165">添加了对 Leap Motion Unity 模块版本 4.6.0、4.7.0、4.7.1 和 4.8.0 的支持</span><span class="sxs-lookup"><span data-stu-id="a88a6-165">Added support for Leap Motion Unity Modules version 4.6.0, 4.7.0, 4.7.1 and 4.8.0</span></span>

<span data-ttu-id="a88a6-166">对最新版 [Leap Motion Unity 模块](https://developer.leapmotion.com/unity)的支持现在与 MRTK 2.7.0 兼容。</span><span class="sxs-lookup"><span data-stu-id="a88a6-166">Support for the latest versions of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) is now compatible with MRTK 2.7.0.</span></span> <span data-ttu-id="a88a6-167">有关详细信息，请参阅[如何为 Leap Motion 配置 MRTK](../supported-devices/leap-motion-mrtk.md)。</span><span class="sxs-lookup"><span data-stu-id="a88a6-167">See [How to Configure MRTK for Leap Motion](../supported-devices/leap-motion-mrtk.md) for more information.</span></span>

<span data-ttu-id="a88a6-168">非常感谢 @jackyangzzh 为新的 LeapMotionOrientationExample 场景所做的贡献！</span><span class="sxs-lookup"><span data-stu-id="a88a6-168">Big thanks to @jackyangzzh for contributing the new LeapMotionOrientationExample scene!</span></span>

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a><span data-ttu-id="a88a6-169">引发的目标语音事件不再局限于凝视指针</span><span class="sxs-lookup"><span data-stu-id="a88a6-169">Targeted speech events raised no longer restricted to gaze pointers</span></span>

<span data-ttu-id="a88a6-170">以前，只能对通过凝视指针聚焦的对象引发目标语音事件。</span><span class="sxs-lookup"><span data-stu-id="a88a6-170">Previously, targeted speech events could only be raised on objects which were focused on with the gaze pointer.</span></span> <span data-ttu-id="a88a6-171">现在，通过任何指针聚焦的对象都可以接收语音事件。</span><span class="sxs-lookup"><span data-stu-id="a88a6-171">Now, objects can receive speech events if they are focused by any pointer.</span></span>

![通过远端指针引发的语音事件](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a><span data-ttu-id="a88a6-173">已将 TextToSpeech 从 HTK 移植到 MRTK</span><span class="sxs-lookup"><span data-stu-id="a88a6-173">Ported TextToSpeech from HTK to MRTK</span></span>

<span data-ttu-id="a88a6-174">广受欢迎的 TextToSpeech 脚本现在终于可在 MRTK 中使用，以便帮助你在 UWP 平台上使用 [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer) 从文本生成语音。</span><span class="sxs-lookup"><span data-stu-id="a88a6-174">The beloved TextToSpeech script is now finally available in MRTK to help you generate speech from text on the UWP platform using [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer).</span></span> <span data-ttu-id="a88a6-175">此外还添加了一个示例场景来演示该功能。</span><span class="sxs-lookup"><span data-stu-id="a88a6-175">Also added a sample scene to demonstrate the feature.</span></span>

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a><span data-ttu-id="a88a6-176">OpenXR 上支持系统提供的运动控制器模型</span><span class="sxs-lookup"><span data-stu-id="a88a6-176">Support for the system-provided motion controller model on OpenXR</span></span>

<span data-ttu-id="a88a6-177">在 OpenXR 上添加了对系统提供的运动控制器模型的支持（在编辑器中以及在运行时）。</span><span class="sxs-lookup"><span data-stu-id="a88a6-177">Added support, both in-editor and at runtime, for the system-provided motion controller model on OpenXR.</span></span>

![显示两个运动控制器模型的编辑器窗口](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a><span data-ttu-id="a88a6-179">OpenXR 上支持 HoloLens 2 铰接式手部网格</span><span class="sxs-lookup"><span data-stu-id="a88a6-179">Support for HoloLens 2 articulated hand mesh on OpenXR</span></span>

![MRTK 示例场景中在设备上运行的手部网格](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a><span data-ttu-id="a88a6-181">旧版 WMR、Windows XR 插件和 OpenXR 均支持控制器触觉</span><span class="sxs-lookup"><span data-stu-id="a88a6-181">Support for controller haptics across legacy WMR, Windows XR Plugin, and OpenXR</span></span>

<span data-ttu-id="a88a6-182">添加了旧版 WMR、Windows XR 插件和 OpenXR 对控制器触觉的支持。</span><span class="sxs-lookup"><span data-stu-id="a88a6-182">Added support for controller haptics across legacy WMR, Windows XR Plugin, and OpenXR.</span></span> [<span data-ttu-id="a88a6-183">#9735</span><span class="sxs-lookup"><span data-stu-id="a88a6-183">#9735</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a><span data-ttu-id="a88a6-184">Windows XR 插件支持眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="a88a6-184">Support for eye tracking on Windows XR Plugin</span></span>

<span data-ttu-id="a88a6-185">添加了在使用 Windows XR 插件最低版本 2.7.0 (Unity 2019)、4.4.2 (Unity 2020) 和 5.2.2 (Unity 2021) 时的眼睛凝视支持。</span><span class="sxs-lookup"><span data-stu-id="a88a6-185">Added support for eye gaze when using Windows XR Plugin minimum versions of 2.7.0 (Unity 2019), 4.4.2 (Unity 2020), and 5.2.2 (Unity 2021).</span></span> [<span data-ttu-id="a88a6-186">#9609</span><span class="sxs-lookup"><span data-stu-id="a88a6-186">#9609</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a><span data-ttu-id="a88a6-187">值得注意的 Bug 修复和更改</span><span class="sxs-lookup"><span data-stu-id="a88a6-187">Notable Bugfixes and Changes</span></span>

- <span data-ttu-id="a88a6-188">捏合检测变得更顺利。</span><span class="sxs-lookup"><span data-stu-id="a88a6-188">Pinch detection made smoother.</span></span> <span data-ttu-id="a88a6-189">现在更不容易出现意外中断捏合手势的情况。</span><span class="sxs-lookup"><span data-stu-id="a88a6-189">It is now harder to accidentally drop the pinch gesture.</span></span> [<span data-ttu-id="a88a6-190">#9576</span><span class="sxs-lookup"><span data-stu-id="a88a6-190">#9576</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- <span data-ttu-id="a88a6-191">现在，在设置标志后，具有对象操控器组件的对象在释放时会持续保持速度。</span><span class="sxs-lookup"><span data-stu-id="a88a6-191">Objects with the Object Manipulator component now consistently maintain velocity on release when the flag is set.</span></span> [<span data-ttu-id="a88a6-192">#9733</span><span class="sxs-lookup"><span data-stu-id="a88a6-192">#9733</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- <span data-ttu-id="a88a6-193">向后扫射现在会查找地面，帮助防止摄像头固定到环境中或用户将光标悬停在空白空间上的情况。[#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)</span><span class="sxs-lookup"><span data-stu-id="a88a6-193">Back-strafing now checks for a floor, helping prevent situations where the camera can clip into the environment or where the user is left hovering over empty space.[#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)</span></span>
- <span data-ttu-id="a88a6-194">IsNearObject 现在是一个虚拟属性，可让用户更灵活地展开球体或戳击指针。</span><span class="sxs-lookup"><span data-stu-id="a88a6-194">IsNearObject is now a virtual property, allowing more flexibility when extending the sphere or poke pointer.</span></span> [<span data-ttu-id="a88a6-195">#9803</span><span class="sxs-lookup"><span data-stu-id="a88a6-195">#9803</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- <span data-ttu-id="a88a6-196">在显示可用的语音命令时，按钮现在会显示正确的关键字。</span><span class="sxs-lookup"><span data-stu-id="a88a6-196">Buttons now display the proper keyword when showing the available speech command.</span></span> [<span data-ttu-id="a88a6-197">#9824</span><span class="sxs-lookup"><span data-stu-id="a88a6-197">#9824</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- <span data-ttu-id="a88a6-198">Oculus 控制器现在使用自身的独立可视化工具，防止 MRTK 可视化效果与 Oculus 集成包的可视化效果相冲突。</span><span class="sxs-lookup"><span data-stu-id="a88a6-198">Oculus Controllers now uses it's own standalone visualizer, preventing the MRTK visualization from clashing with the Oculus Integration Package's visualization.</span></span> [<span data-ttu-id="a88a6-199">#9589</span><span class="sxs-lookup"><span data-stu-id="a88a6-199">#9589</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- <span data-ttu-id="a88a6-200">与键盘相关的脚本已更改，以便与最新 Unity 版本（2019.4.25+ 和 2020.3.2+）的行为相一致。</span><span class="sxs-lookup"><span data-stu-id="a88a6-200">Keyboard related scripts have been changed to align with the behavior in latest Unity versions (2019.4.25+ & 2020.3.2+).</span></span> <span data-ttu-id="a88a6-201">在该版本中，仍然存在会影响 HoloLens 的自动完成 bug 和 TMP 输入字段 bug（这两个 bug 都出现在 MRTK 的外部）。</span><span class="sxs-lookup"><span data-stu-id="a88a6-201">As of the release there is still an auto-completion bug and a TMP Input Field bug (both are external to MRTK) impacting HoloLens.</span></span> <span data-ttu-id="a88a6-202">有关详细信息，请参阅 [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) 和 [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724)。</span><span class="sxs-lookup"><span data-stu-id="a88a6-202">For more information please see [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) and [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724).</span></span>
- <span data-ttu-id="a88a6-203">改进了滚动对象集合的性能。</span><span class="sxs-lookup"><span data-stu-id="a88a6-203">Improved the performance of Scrolling Object Collection.</span></span> <span data-ttu-id="a88a6-204">此外，还修复了一个导致集合中的 GameObject 在复制后丢失材料的问题。</span><span class="sxs-lookup"><span data-stu-id="a88a6-204">Also fixed an issue causing GameObject within the collection to lose material when duplicated.</span></span> <span data-ttu-id="a88a6-205">[#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813)、[#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)</span><span class="sxs-lookup"><span data-stu-id="a88a6-205">[#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)</span></span>
- <span data-ttu-id="a88a6-206">在场景理解演示脚本中，添加了 `GetSceneObjectsOfType` 函数以检索特定种类的所有已观测到的场景对象。</span><span class="sxs-lookup"><span data-stu-id="a88a6-206">In the Scene Understanding demo script, added the `GetSceneObjectsOfType` function to retrieve all observed scene object of a certain kind.</span></span> <span data-ttu-id="a88a6-207">[#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524)、[#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)</span><span class="sxs-lookup"><span data-stu-id="a88a6-207">[#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)</span></span>
- <span data-ttu-id="a88a6-208">在命令行生成工具中，只会将 `sceneList` 或 `sceneListFile` 标志（如果存在任一标志）指定的场景包含在生成中。</span><span class="sxs-lookup"><span data-stu-id="a88a6-208">In command line build tool, only scenes specified by the `sceneList` or `sceneListFile` flags (when any flag is present) will be included in the build.</span></span> [<span data-ttu-id="a88a6-209">#9695</span><span class="sxs-lookup"><span data-stu-id="a88a6-209">#9695</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- <span data-ttu-id="a88a6-210">在生成工具中，有一个新选项可用于指定 `nuget.exe` 的路径，并使用该路径执行包还原，而无需使用 `msbuild`（默认选项）。</span><span class="sxs-lookup"><span data-stu-id="a88a6-210">In build tool, there is a new option to specify a path to `nuget.exe` and use that to perform package restore instead of using `msbuild` (the default option).</span></span> [<span data-ttu-id="a88a6-211">#9556</span><span class="sxs-lookup"><span data-stu-id="a88a6-211">#9556</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- <span data-ttu-id="a88a6-212">修复了使用 Windows XR 插件可能会导致手关节僵硬和手部网格数翻倍的问题。</span><span class="sxs-lookup"><span data-stu-id="a88a6-212">Fixed issue where using Windows XR Plugin could result in stale hand joints and doubled hand meshes.</span></span> [<span data-ttu-id="a88a6-213">#9890</span><span class="sxs-lookup"><span data-stu-id="a88a6-213">#9890</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- <span data-ttu-id="a88a6-214">修复了使用 Windows XR 插件的自动远程控制功能导致丢失输入和交互的问题。</span><span class="sxs-lookup"><span data-stu-id="a88a6-214">Fixed issue where using Windows XR Plugin's automatic remoting feature led to missing input and interactions.</span></span> [<span data-ttu-id="a88a6-215">#9868</span><span class="sxs-lookup"><span data-stu-id="a88a6-215">#9868</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- <span data-ttu-id="a88a6-216">修复了 BuildDeployWindow 尝试在无效注册表项中查询 Windows SDK 路径的问题。</span><span class="sxs-lookup"><span data-stu-id="a88a6-216">Fixed issue where the BuildDeployWindow would try to query an invalid reg key for the Windows SDK path.</span></span> [<span data-ttu-id="a88a6-217">#9664</span><span class="sxs-lookup"><span data-stu-id="a88a6-217">#9664</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- <span data-ttu-id="a88a6-218">MRTK 的 glTF 导入器现在是可选的。</span><span class="sxs-lookup"><span data-stu-id="a88a6-218">MRTK's glTF importers are now optional.</span></span> <span data-ttu-id="a88a6-219">如果存在多个 glTF 导入器，可以通过将 `MRTK_GLTF_IMPORTER_OFF` 添加到自定义脚本定义符号来禁用 MRTK 的导入器。</span><span class="sxs-lookup"><span data-stu-id="a88a6-219">If multiple glTF importers are present, MRTK's can be disabled by adding `MRTK_GLTF_IMPORTER_OFF` to the custom scripting define symbols.</span></span> [<span data-ttu-id="a88a6-220">#9658</span><span class="sxs-lookup"><span data-stu-id="a88a6-220">#9658</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- <span data-ttu-id="a88a6-221">修复了无法正常检测 OpenVR 上的指节控制器的问题。</span><span class="sxs-lookup"><span data-stu-id="a88a6-221">Fixed issue where the Knuckles controllers on OpenVR weren't being detected properly.</span></span> [<span data-ttu-id="a88a6-222">#9881</span><span class="sxs-lookup"><span data-stu-id="a88a6-222">#9881</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- <span data-ttu-id="a88a6-223">减少了可视化手部网格时的每帧分配数 [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)</span><span class="sxs-lookup"><span data-stu-id="a88a6-223">Reduce the number of per-frame allocations when visualizing the hand mesh [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)</span></span>
- <span data-ttu-id="a88a6-224">添加了一个菜单项用于启动 MRTK 示例包（在 Unity 包管理器中），以便更轻松地导入示例 [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)</span><span class="sxs-lookup"><span data-stu-id="a88a6-224">Added a menu item to launch the MRTK Examples package (in Unity Package Manager) to make it easier to import samples [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)</span></span>
- <span data-ttu-id="a88a6-225">减少了使用 Unity 2020.3 时显示的加载时间警告数。</span><span class="sxs-lookup"><span data-stu-id="a88a6-225">Reduced the number of load-time warnings when using Unity 2020.3.</span></span>
- <span data-ttu-id="a88a6-226">添加了生成窗口功能文档：[访问页面](../features/tools/build-window.md)</span><span class="sxs-lookup"><span data-stu-id="a88a6-226">Added Build Window feature documentation: [Visit the page](../features/tools/build-window.md)</span></span>

## <a name="known-issues"></a><span data-ttu-id="a88a6-227">已知问题</span><span class="sxs-lookup"><span data-stu-id="a88a6-227">Known Issues</span></span>

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a><span data-ttu-id="a88a6-228">音频演示缺少 asmdef 文件（UPM 包）</span><span class="sxs-lookup"><span data-stu-id="a88a6-228">Audio demos are missing an asmdef file (UPM package)</span></span>

<span data-ttu-id="a88a6-229">通过混合现实功能工具导入 MRTK 时，会使用 Unity 包管理器 UI 将示例和演示添加到项目。</span><span class="sxs-lookup"><span data-stu-id="a88a6-229">When importing MRTK via the Mixed Reality Feature Tool, samples and demos are added to the project using the Unity Package Manager UI.</span></span> <span data-ttu-id="a88a6-230">导入音频演示后，`WindowsMicrophoneStreamDemo.unity` 场景的行为将不正常。</span><span class="sxs-lookup"><span data-stu-id="a88a6-230">After importing the Audio demos, the `WindowsMicrophoneStreamDemo.unity` scene will not behave properly.</span></span> <span data-ttu-id="a88a6-231">这是由于示例缺少 .asmdef 文件所致。</span><span class="sxs-lookup"><span data-stu-id="a88a6-231">This is a result of a missing .asmdef file for the sample.</span></span>

<span data-ttu-id="a88a6-232">若要解决此[问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908)，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="a88a6-232">To work around this [issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908), please perform the following steps:</span></span>

- <span data-ttu-id="a88a6-233">将 Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@[...]/MRTK.Examples.asmdef 复制到“Assets/Samples/Mixed Reality Toolkit Examples”文件夹中</span><span class="sxs-lookup"><span data-stu-id="a88a6-233">Copy Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@[...]/MRTK.Examples.asmdef into your "Assets/Samples/Mixed Reality Toolkit Examples" folder</span></span>
- <span data-ttu-id="a88a6-234">将复制的文件重命名为 Examples</span><span class="sxs-lookup"><span data-stu-id="a88a6-234">Rename the copied file to Examples</span></span>
- <span data-ttu-id="a88a6-235">打开 Examples 文件</span><span class="sxs-lookup"><span data-stu-id="a88a6-235">Open the Examples file</span></span>
- <span data-ttu-id="a88a6-236">在“名称”框中，将内容替换为 Examples</span><span class="sxs-lookup"><span data-stu-id="a88a6-236">In the Name box, replace the contents with Examples</span></span>
- <span data-ttu-id="a88a6-237">单击“应用”</span><span class="sxs-lookup"><span data-stu-id="a88a6-237">Click Apply</span></span>
- <span data-ttu-id="a88a6-238">生成并部署</span><span class="sxs-lookup"><span data-stu-id="a88a6-238">Build and deploy</span></span>

<span data-ttu-id="a88a6-239">将来的 MRTK 版本将修复此问题。</span><span class="sxs-lookup"><span data-stu-id="a88a6-239">This issue will be fixed in an upcoming MRTK release.</span></span>

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a><span data-ttu-id="a88a6-240">MRTK 生成窗口在 Unity 2020.3 中不停地触发“正在导入资产”对话框</span><span class="sxs-lookup"><span data-stu-id="a88a6-240">MRTK build window triggers indefinite "Importing assets" dialog in Unity 2020.3</span></span>

<span data-ttu-id="a88a6-241">Unity 2020.3 上的 MRTK 生成窗口存在一个已知[问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723)：在成功执行 UWP 生成后，“正在导入资产”对话框不会完成。</span><span class="sxs-lookup"><span data-stu-id="a88a6-241">There is a known [issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) with the MRTK build window on Unity 2020.3 where after successfully performing a UWP build, the "Importing assets" dialog does not complete.</span></span> <span data-ttu-id="a88a6-242">我们正在配合 Unity 调查此问题。</span><span class="sxs-lookup"><span data-stu-id="a88a6-242">This issue is being investigated in partnership with Unity.</span></span>

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a><span data-ttu-id="a88a6-243">Unity 2020 中出现 Text Mesh Pro 画布渲染器警告</span><span class="sxs-lookup"><span data-stu-id="a88a6-243">Text Mesh Pro Canvas Renderer warnings in Unity 2020</span></span>

<span data-ttu-id="a88a6-244">使用 Unity 2020 时，大部分 MRTK 示例场景中都会记录以下警告：</span><span class="sxs-lookup"><span data-stu-id="a88a6-244">The following warning is logged in most MRTK example scenes while using Unity 2020:</span></span>

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

<span data-ttu-id="a88a6-245">[TextMeshPro 版本 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3) 中添加了画布渲染器警告。</span><span class="sxs-lookup"><span data-stu-id="a88a6-245">The Canvas Renderer warning was added in [TextMeshPro version 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3).</span></span> <span data-ttu-id="a88a6-246">这些警告不会影响 MRTK 的示例场景，可以从控制台中清除。</span><span class="sxs-lookup"><span data-stu-id="a88a6-246">These warning do not have an impact on MRTK's example scenes and can be cleared from the console.</span></span> <span data-ttu-id="a88a6-247">有关更多详细信息，请参阅[问题 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811)。</span><span class="sxs-lookup"><span data-stu-id="a88a6-247">See [Issue 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811) for more details.</span></span>