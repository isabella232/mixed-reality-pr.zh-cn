---
title: MRTK 2.7 发行说明
description: MRTK 版本 2.7 发行说明
author: RogPodge
ms.author: roliu
ms.date: 05/27/2021
ms.localizationpriority: medium
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， XRSDK， 旧版 XR， Leap Motion， Ultraleap
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 92c8705c70a2a6c1e25f1ed6b1f87eac1e5726e0
ms.sourcegitcommit: 11d5d7c3fdd59c1ebcfca34dbb6d84c05b481e5f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2021
ms.locfileid: "111897400"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a><span data-ttu-id="80e95-104">Microsoft Mixed Reality Toolkit 2.7 发行说明</span><span class="sxs-lookup"><span data-stu-id="80e95-104">Microsoft Mixed Reality Toolkit 2.7 Release Notes</span></span>

## <a name="whats-new-in-270"></a><span data-ttu-id="80e95-105">2.7.0 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="80e95-105">What's new in 2.7.0</span></span>

### <a name="openxr-is-now-officially-supported-in-mrtk"></a><span data-ttu-id="80e95-106">MRTK 中现已正式支持 OpenXR</span><span class="sxs-lookup"><span data-stu-id="80e95-106">OpenXR is now officially supported in MRTK</span></span>

<span data-ttu-id="80e95-107">随着新的 OpenXR 插件变得越来越成熟，MRTK 现在正式支持 OpenXR。</span><span class="sxs-lookup"><span data-stu-id="80e95-107">As the new OpenXR plugins are becoming more and more mature MRTK now officially supports OpenXR.</span></span> <span data-ttu-id="80e95-108">与以前的版本相比，我们使用 OpenXR 向项目添加了以下功能：</span><span class="sxs-lookup"><span data-stu-id="80e95-108">Compared to previous releases we added the following capabilities to projects using OpenXR:</span></span>

- [<span data-ttu-id="80e95-109">支持系统提供的动作控制器模型</span><span class="sxs-lookup"><span data-stu-id="80e95-109">Support for the system-provided motion controller model</span></span>](#support-for-the-system-provided-motion-controller-model-on-openxr)
- <span data-ttu-id="80e95-110">支持 WinMR 手势 (选择、按住、[操作和导航](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)) #9843</span><span class="sxs-lookup"><span data-stu-id="80e95-110">Support for WinMR gestures (select, hold, manipulation and navigation) [#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)</span></span>
- [<span data-ttu-id="80e95-111">支持控制器触点</span><span class="sxs-lookup"><span data-stu-id="80e95-111">Support for controller haptics</span></span>](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [<span data-ttu-id="80e95-112">支持在手动网格上进行HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="80e95-112">Support for articulated hand mesh on HoloLens 2</span></span>](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- <span data-ttu-id="80e95-113">支持在 HoloLens 2 #9567[上#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567) [](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)</span><span class="sxs-lookup"><span data-stu-id="80e95-113">Support for Spatial Mapping on HoloLens 2 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567), [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)</span></span>
- <span data-ttu-id="80e95-114">支持对场景进行场景 [HoloLens 2#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)</span><span class="sxs-lookup"><span data-stu-id="80e95-114">Support for Scene Understanding on HoloLens 2 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)</span></span>

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a><span data-ttu-id="80e95-115">旧式 XR 和 XR SDK 数据提供程序现在可以在同一配置文件中使用</span><span class="sxs-lookup"><span data-stu-id="80e95-115">Legacy XR and XR SDK Data Providers can now be used within the same profile</span></span>

<span data-ttu-id="80e95-116">现在，只有在选择了适当的管道时，才加载数据提供程序，从而允许旧式 XR 和 XR SDK 数据提供程序共存于同一配置文件中。</span><span class="sxs-lookup"><span data-stu-id="80e95-116">Data providers will now also only be loaded when the appropriate pipeline is selected, allowing both Legacy XR and XR SDK data providers to co-exist within the same profile.</span></span> <span data-ttu-id="80e95-117">为了适应这种情况，旧版 XR 和 XR SDK 数据提供程序现在组织在配置文件视图中的不同选项卡下，帮助用户确定其目标 XR 管道是否具有正确的配置文件。</span><span class="sxs-lookup"><span data-stu-id="80e95-117">To accommodate this, Legacy XR and XR SDK Data Providers are now organized under different tabs within the profile view, helping users determine whether they have the correct profile for their targeted XR pipeline.</span></span>

![旧式和 XR SDK 数据提供程序现在可以在单个配置文件下统一](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

<span data-ttu-id="80e95-119">为了适应这种情况，现在不再加载 null 数据提供程序并显示在配置文件检查器中。</span><span class="sxs-lookup"><span data-stu-id="80e95-119">To accommodate this, null data providers will now no longer be loaded and displayed in the profile inspector.</span></span> <span data-ttu-id="80e95-120">用户可以在" `Show null data providers in the profile inspector` 编辑 **"->"项目设置"->混合现实工具包** "下切换，以调试缺少数据提供程序的意外行为。</span><span class="sxs-lookup"><span data-stu-id="80e95-120">Users can toggle `Show null data providers in the profile inspector` under **Edit -> Project Settings -> Mixed Reality Toolkit** to debug unexpected behaviors with missing data providers.</span></span>

<span data-ttu-id="80e95-121">![现在默认隐藏 Null 数据提供程序 在配置文件检查器中 ](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
 ![ 切换显示 null 数据提供程序](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)</span><span class="sxs-lookup"><span data-stu-id="80e95-121">![Null data providers are now hidden by default](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
![Toggle show null data providers in the profile inspector](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)</span></span>

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a><span data-ttu-id="80e95-122">添加了体验设置和关联的混合现实场景内容行为</span><span class="sxs-lookup"><span data-stu-id="80e95-122">Added Experience Settings and an associated Mixed Reality Scene Content behavior</span></span>

<span data-ttu-id="80e95-123">用户现在可以配置["体验设置"，](../features/experience-settings/experience-settings.md)这将允许 MRTK[](../features/experience-settings/scene-content.md)根据目标体验适当地显示混合现实场景内容。</span><span class="sxs-lookup"><span data-stu-id="80e95-123">Users can now configure [Experience Settings](../features/experience-settings/experience-settings.md), which will allow MRTK to display [Mixed Reality Scene Content](../features/experience-settings/scene-content.md) appropriately based on the targeted experience.</span></span>

<span data-ttu-id="80e95-124">如果用户以前的体验缩放设置与新的体验设置配置文件不匹配，系统会在检查器中提示他们更正它</span><span class="sxs-lookup"><span data-stu-id="80e95-124">If user's previous Experience Scale settings do not match the new Experience Settings Profile, they will be prompted to correct it in the inspector</span></span>

![体验缩放迁移](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a><span data-ttu-id="80e95-126">重新设计的配置器现在引导用户完成安装过程</span><span class="sxs-lookup"><span data-stu-id="80e95-126">The Redesigned Configurator now guides the user through the setup process</span></span>

<span data-ttu-id="80e95-127">新的 MRTK 配置器为用户提供分步指南，以正确配置项目以用于 XR 开发并用于 MRTK。</span><span class="sxs-lookup"><span data-stu-id="80e95-127">The new MRTK configurator provides users step-by-step guidance to properly configure the project for XR development and use with MRTK.</span></span> <span data-ttu-id="80e95-128">其中介绍了 XR 管道的选择、获取特定于平台的插件、导入 TextMeshPro、显示使用 UPM) 时的示例 (以及以前为项目提供的其他建议设置。</span><span class="sxs-lookup"><span data-stu-id="80e95-128">It covers the selection of XR pipeline, getting the platform specific plugins, importing TextMeshPro, displaying the examples (when using UPM) and other previously included recommended settings for the project.</span></span>

![显示管道列表的 Configurator](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a><span data-ttu-id="80e95-130">已伸缩的 Teleport 热点</span><span class="sxs-lookup"><span data-stu-id="80e95-130">Graduated Teleport Hotspot</span></span>

<span data-ttu-id="80e95-131">新的 [远程端口热点组件](../features/teleport-system/teleport-hotspot.md) 已经过专业。</span><span class="sxs-lookup"><span data-stu-id="80e95-131">A new [teleport hotspot component](../features/teleport-system/teleport-hotspot.md) has been graduated.</span></span> <span data-ttu-id="80e95-132">可以将远程端口热点添加到 GameObject，以确保用户在远程传送到该位置时处于特定位置和方向。</span><span class="sxs-lookup"><span data-stu-id="80e95-132">You can add a teleport hotspot to your GameObject to ensure that the user is in a certain position and orientation when they teleport to that location.</span></span>

![Teleport 热点示例](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a><span data-ttu-id="80e95-134">已分居</span><span class="sxs-lookup"><span data-stu-id="80e95-134">Graduated Dwell</span></span>

<span data-ttu-id="80e95-135">停留特征和示例现已从实验阶段开始。</span><span class="sxs-lookup"><span data-stu-id="80e95-135">The dwell feature and example is now graduated from experimental.</span></span> <span data-ttu-id="80e95-136">示例场景中包含HoloLens 2样式按钮的新示例。</span><span class="sxs-lookup"><span data-stu-id="80e95-136">New examples of volumetric HoloLens 2 style buttons are included in the sample scene.</span></span>

![停留英雄](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a><span data-ttu-id="80e95-138">添加了对 Leap Motion Unity 模块版本 4.6.0、4.7.0、4.7.1 和 4.8.0 的支持</span><span class="sxs-lookup"><span data-stu-id="80e95-138">Added support for Leap Motion Unity Modules version 4.6.0, 4.7.0, 4.7.1 and 4.8.0</span></span>

<span data-ttu-id="80e95-139">对最新版本的 Leap Motion [Unity 模块](https://developer.leapmotion.com/unity) 的支持现在与 MRTK 2.7.0 兼容。</span><span class="sxs-lookup"><span data-stu-id="80e95-139">Support for the latest versions of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) is now compatible with MRTK 2.7.0.</span></span>  <span data-ttu-id="80e95-140">有关详细信息[，请参阅如何为 Leap Motion 配置 MRTK。](../supported-devices/leap-motion-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="80e95-140">See [How to Configure MRTK for Leap Motion](../supported-devices/leap-motion-mrtk.md) for more information.</span></span>

<span data-ttu-id="80e95-141">感谢贡献 @jackyangzzh 新的 LeapMotionOrientationExample 场景！</span><span class="sxs-lookup"><span data-stu-id="80e95-141">Big thanks to @jackyangzzh for contributing the new LeapMotionOrientationExample scene!</span></span>

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a><span data-ttu-id="80e95-142">引发的目标语音事件不再局限于凝视指针</span><span class="sxs-lookup"><span data-stu-id="80e95-142">Targeted speech events raised no longer restricted to gaze pointers</span></span>

<span data-ttu-id="80e95-143">以前，只能在使用凝视指针聚焦的对象上引发目标语音事件。</span><span class="sxs-lookup"><span data-stu-id="80e95-143">Previously, targeted speech events could only be raised on objects which were focused on with the gaze pointer.</span></span> <span data-ttu-id="80e95-144">现在，如果对象通过任何指针聚焦，则它们可以接收语音事件。</span><span class="sxs-lookup"><span data-stu-id="80e95-144">Now, objects can receive speech events if they are focused by any pointer.</span></span>

![具有远点指针的语音事件](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a><span data-ttu-id="80e95-146">从 HTK 移植到 MRTK 的 TextToSpeech</span><span class="sxs-lookup"><span data-stu-id="80e95-146">Ported TextToSpeech from HTK to MRTK</span></span>

<span data-ttu-id="80e95-147">现在，MRTK 中最终提供了一个纯文本 TextToSpeech 脚本，可帮助你使用 从 UWP 平台上的文本生成语音 [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer) 。</span><span class="sxs-lookup"><span data-stu-id="80e95-147">The beloved TextToSpeech script is now finally available in MRTK to help you generate speech from text on the UWP platform using [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer).</span></span> <span data-ttu-id="80e95-148">还添加了一个示例场景来演示该功能。</span><span class="sxs-lookup"><span data-stu-id="80e95-148">Also added a sample scene to demonstrate the feature.</span></span>

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a><span data-ttu-id="80e95-149">在 OpenXR 上支持系统提供的动作控制器模型</span><span class="sxs-lookup"><span data-stu-id="80e95-149">Support for the system-provided motion controller model on OpenXR</span></span>

<span data-ttu-id="80e95-150">添加了对 OpenXR 上系统提供的动作控制器模型的支持（在编辑器中和运行时）。</span><span class="sxs-lookup"><span data-stu-id="80e95-150">Added support, both in-editor and at runtime, for the system-provided motion controller model on OpenXR.</span></span>

![显示两个运动控制器模型的编辑器窗口](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a><span data-ttu-id="80e95-152">支持在 OpenXR HoloLens 2手部网格</span><span class="sxs-lookup"><span data-stu-id="80e95-152">Support for HoloLens 2 articulated hand mesh on OpenXR</span></span>

![MRTK 示例场景中在设备上运行手动网格](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a><span data-ttu-id="80e95-154">支持跨旧版 WMR、Windows XR 插件和 OpenXR 的控制器触角</span><span class="sxs-lookup"><span data-stu-id="80e95-154">Support for controller haptics across legacy WMR, Windows XR Plugin, and OpenXR</span></span>

<span data-ttu-id="80e95-155">添加了对跨旧版 WMR、Windows XR 插件和 OpenXR 的控制器触角的支持。</span><span class="sxs-lookup"><span data-stu-id="80e95-155">Added support for controller haptics across legacy WMR, Windows XR Plugin, and OpenXR.</span></span> [<span data-ttu-id="80e95-156">#9735</span><span class="sxs-lookup"><span data-stu-id="80e95-156">#9735</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a><span data-ttu-id="80e95-157">支持在 Windows XR 插件上进行眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="80e95-157">Support for eye tracking on Windows XR Plugin</span></span>

<span data-ttu-id="80e95-158">添加了在使用 Windows XR 插件最低版本 2.7.0 (Unity 2019) 、4.4.2 (Unity 2020) 和 5.2.2 (Unity 2021) 时对眼睛凝视的支持。</span><span class="sxs-lookup"><span data-stu-id="80e95-158">Added support for eye gaze when using Windows XR Plugin minimum versions of 2.7.0 (Unity 2019), 4.4.2 (Unity 2020), and 5.2.2 (Unity 2021).</span></span> [<span data-ttu-id="80e95-159">#9609</span><span class="sxs-lookup"><span data-stu-id="80e95-159">#9609</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a><span data-ttu-id="80e95-160">值得注意的 Bug 修复和更改</span><span class="sxs-lookup"><span data-stu-id="80e95-160">Notable Bugfixes and Changes</span></span>

- <span data-ttu-id="80e95-161">收缩检测更流畅。</span><span class="sxs-lookup"><span data-stu-id="80e95-161">Pinch detection made smoother.</span></span> <span data-ttu-id="80e95-162">现在更难意外删除收缩手势。</span><span class="sxs-lookup"><span data-stu-id="80e95-162">It is now harder to accidentally drop the pinch gesture.</span></span> [<span data-ttu-id="80e95-163">#9576</span><span class="sxs-lookup"><span data-stu-id="80e95-163">#9576</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- <span data-ttu-id="80e95-164">设置 标志时，具有对象操控器组件的对象现在一致地保持发布速度。</span><span class="sxs-lookup"><span data-stu-id="80e95-164">Objects with the Object Manipulator component now consistently maintain velocity on release when the flag is set.</span></span> [<span data-ttu-id="80e95-165">#9733</span><span class="sxs-lookup"><span data-stu-id="80e95-165">#9733</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- <span data-ttu-id="80e95-166">Back-strafing 现在会检查楼层，帮助防止相机卡入环境或用户将鼠标悬停在空白区域的情况。[#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)</span><span class="sxs-lookup"><span data-stu-id="80e95-166">Back-strafing now checks for a floor, helping prevent situations where the camera can clip into the environment or where the user is left hovering over empty space.[#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)</span></span>
- <span data-ttu-id="80e95-167">IsNearObject 现在是一个虚拟属性，在扩展球体或圆球指针时允许更灵活。</span><span class="sxs-lookup"><span data-stu-id="80e95-167">IsNearObject is now a virtual property, allowing more flexibility when extending the sphere or poke pointer.</span></span> [<span data-ttu-id="80e95-168">#9803</span><span class="sxs-lookup"><span data-stu-id="80e95-168">#9803</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- <span data-ttu-id="80e95-169">现在，当显示可用的语音命令时，按钮会显示正确的关键字。</span><span class="sxs-lookup"><span data-stu-id="80e95-169">Buttons now display the proper keyword when showing the available speech command.</span></span> [<span data-ttu-id="80e95-170">#9824</span><span class="sxs-lookup"><span data-stu-id="80e95-170">#9824</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- <span data-ttu-id="80e95-171">Oculus 控制器现在使用自己的独立可视化工具，防止 MRTK 可视化效果与 Oculus 集成包的可视化效果冲突。</span><span class="sxs-lookup"><span data-stu-id="80e95-171">Oculus Controllers now uses it's own standalone visualizer, preventing the MRTK visualization from clashing with the Oculus Integration Package's visualization.</span></span> [<span data-ttu-id="80e95-172">#9589</span><span class="sxs-lookup"><span data-stu-id="80e95-172">#9589</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- <span data-ttu-id="80e95-173">与键盘相关的脚本已更改，以与最新 Unity 版本 (2019.4.25+ & 2020.3.2+) 中的行为保持一致。</span><span class="sxs-lookup"><span data-stu-id="80e95-173">Keyboard related scripts have been changed to align with the behavior in latest Unity versions (2019.4.25+ & 2020.3.2+).</span></span> <span data-ttu-id="80e95-174">自发布起，仍有一个自动完成 bug 和 TMP 输入字段 bug (在 MRTK 外部) 影响 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="80e95-174">As of the release there is still an auto-completion bug and a TMP Input Field bug (both are external to MRTK) impacting HoloLens.</span></span> <span data-ttu-id="80e95-175">有关详细信息，请参阅[#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056)和[#9724。](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724)</span><span class="sxs-lookup"><span data-stu-id="80e95-175">For more information please see [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) and [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724).</span></span>
- <span data-ttu-id="80e95-176">改进了滚动对象集合的性能。</span><span class="sxs-lookup"><span data-stu-id="80e95-176">Improved the performance of Scrolling Object Collection.</span></span> <span data-ttu-id="80e95-177">还修复了在复制时导致集合中的 GameObject 丢失材料的问题。</span><span class="sxs-lookup"><span data-stu-id="80e95-177">Also fixed an issue causing GameObject within the collection to lose material when duplicated.</span></span> <span data-ttu-id="80e95-178">[#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813) [、#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)</span><span class="sxs-lookup"><span data-stu-id="80e95-178">[#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)</span></span>
- <span data-ttu-id="80e95-179">在"场景理解"演示脚本中，添加了 `GetSceneObjectsOfType` 用于检索所有观察到的某种类型的场景对象的 函数。</span><span class="sxs-lookup"><span data-stu-id="80e95-179">In the Scene Understanding demo script, added the `GetSceneObjectsOfType` function to retrieve all observed scene object of a certain kind.</span></span> <span data-ttu-id="80e95-180">[#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524) [、#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)</span><span class="sxs-lookup"><span data-stu-id="80e95-180">[#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)</span></span>
- <span data-ttu-id="80e95-181">在命令行生成工具中，只有 或 标志指定的场景 (存在任何标志时) 将 `sceneList` `sceneListFile` 包含在生成中。</span><span class="sxs-lookup"><span data-stu-id="80e95-181">In command line build tool, only scenes specified by the `sceneList` or `sceneListFile` flags (when any flag is present) will be included in the build.</span></span> [<span data-ttu-id="80e95-182">#9695</span><span class="sxs-lookup"><span data-stu-id="80e95-182">#9695</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- <span data-ttu-id="80e95-183">在生成工具中，有一个新选项指定的路径，并使用它来执行包还原，而不是使用 (`nuget.exe` `msbuild` 默认) 。</span><span class="sxs-lookup"><span data-stu-id="80e95-183">In build tool, there is a new option to specify a path to `nuget.exe` and use that to perform package restore instead of using `msbuild` (the default option).</span></span> [<span data-ttu-id="80e95-184">#9556</span><span class="sxs-lookup"><span data-stu-id="80e95-184">#9556</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- <span data-ttu-id="80e95-185">修复了使用 Windows XR 插件可能会导致手部连接过时和手部网格双倍的问题。</span><span class="sxs-lookup"><span data-stu-id="80e95-185">Fixed issue where using Windows XR Plugin could result in stale hand joints and doubled hand meshes.</span></span> [<span data-ttu-id="80e95-186">#9890</span><span class="sxs-lookup"><span data-stu-id="80e95-186">#9890</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- <span data-ttu-id="80e95-187">修复了使用 Windows XR 插件的自动远程处理功能导致缺少输入和交互的问题。</span><span class="sxs-lookup"><span data-stu-id="80e95-187">Fixed issue where using Windows XR Plugin's automatic remoting feature led to missing input and interactions.</span></span> [<span data-ttu-id="80e95-188">#9868</span><span class="sxs-lookup"><span data-stu-id="80e95-188">#9868</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- <span data-ttu-id="80e95-189">修复了 BuildDeployWindow 尝试查询路径的无效 reg 键Windows SDK的问题。</span><span class="sxs-lookup"><span data-stu-id="80e95-189">Fixed issue where the BuildDeployWindow would try to query an invalid reg key for the Windows SDK path.</span></span> [<span data-ttu-id="80e95-190">#9664</span><span class="sxs-lookup"><span data-stu-id="80e95-190">#9664</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- <span data-ttu-id="80e95-191">MRTK 的 glTF 导入程序现在是可选的。</span><span class="sxs-lookup"><span data-stu-id="80e95-191">MRTK's glTF importers are now optional.</span></span> <span data-ttu-id="80e95-192">如果存在多个 glTF 导入程序，则可以通过将 添加到自定义脚本定义符号来禁用 `MRTK_GLTF_IMPORTER_OFF` MRTK。</span><span class="sxs-lookup"><span data-stu-id="80e95-192">If multiple glTF importers are present, MRTK's can be disabled by adding `MRTK_GLTF_IMPORTER_OFF` to the custom scripting define symbols.</span></span> [<span data-ttu-id="80e95-193">#9658</span><span class="sxs-lookup"><span data-stu-id="80e95-193">#9658</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- <span data-ttu-id="80e95-194">修复了未正确检测到 OpenVR 上的 Knuckles 控制器的问题。</span><span class="sxs-lookup"><span data-stu-id="80e95-194">Fixed issue where the Knuckles controllers on OpenVR weren't being detected properly.</span></span> [<span data-ttu-id="80e95-195">#9881</span><span class="sxs-lookup"><span data-stu-id="80e95-195">#9881</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- <span data-ttu-id="80e95-196">在可视化手部网格网格时减少每帧分配 [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)</span><span class="sxs-lookup"><span data-stu-id="80e95-196">Reduce the number of per-frame allocations when visualizing the hand mesh [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)</span></span>
- <span data-ttu-id="80e95-197">添加了一个菜单项以在 Unity (中启动 MRTK 示例包程序包管理器) 以便更轻松地将示例导入 [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)</span><span class="sxs-lookup"><span data-stu-id="80e95-197">Added a menu item to launch the MRTK Examples package (in Unity Package Manager) to make it easier to import samples [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)</span></span>
- <span data-ttu-id="80e95-198">减少了使用 Unity 2020.3 时出现加载时警告的数量。</span><span class="sxs-lookup"><span data-stu-id="80e95-198">Reduced the number of load-time warnings when using Unity 2020.3.</span></span>
- <span data-ttu-id="80e95-199">添加了生成窗口功能文档 [：请访问页面](/windows/mixed-reality/mrtk-unity/features/tools/build-window)</span><span class="sxs-lookup"><span data-stu-id="80e95-199">Added Build Window feature documentation: [Visit the page](/windows/mixed-reality/mrtk-unity/features/tools/build-window)</span></span>

## <a name="known-issues"></a><span data-ttu-id="80e95-200">已知问题</span><span class="sxs-lookup"><span data-stu-id="80e95-200">Known Issues</span></span>

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a><span data-ttu-id="80e95-201">音频演示缺少 (UPM 包的 asmdef 文件) </span><span class="sxs-lookup"><span data-stu-id="80e95-201">Audio demos are missing an asmdef file (UPM package)</span></span>

<span data-ttu-id="80e95-202">通过混合现实功能工具导入 MRTK 时，示例和演示将使用 Unity 包管理器 UI 添加到项目。</span><span class="sxs-lookup"><span data-stu-id="80e95-202">When importing MRTK via the Mixed Reality Feature Tool, samples and demos are added to the project using the Unity Package Manager UI.</span></span> <span data-ttu-id="80e95-203">导入音频演示后， `WindowsMicrophoneStreamDemo.unity` 场景将无法正常运行。</span><span class="sxs-lookup"><span data-stu-id="80e95-203">After importing the Audio demos, the `WindowsMicrophoneStreamDemo.unity` scene will not behave properly.</span></span> <span data-ttu-id="80e95-204">这是示例缺少 asmdef 文件的结果。</span><span class="sxs-lookup"><span data-stu-id="80e95-204">This is a result of a missing .asmdef file for the sample.</span></span>

<span data-ttu-id="80e95-205">若要解决此 [问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908)，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="80e95-205">To work around this [issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908), please perform the following steps:</span></span>

- <span data-ttu-id="80e95-206">Copy Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@ [...]/MRTK.示例 asmdef 到 "资产/示例/混合现实工具包示例" 文件夹</span><span class="sxs-lookup"><span data-stu-id="80e95-206">Copy Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@[...]/MRTK.Examples.asmdef into your "Assets/Samples/Mixed Reality Toolkit Examples" folder</span></span>
- <span data-ttu-id="80e95-207">将复制的文件重命名为示例</span><span class="sxs-lookup"><span data-stu-id="80e95-207">Rename the copied file to Examples</span></span>
- <span data-ttu-id="80e95-208">打开示例文件</span><span class="sxs-lookup"><span data-stu-id="80e95-208">Open the Examples file</span></span>
- <span data-ttu-id="80e95-209">在 "名称" 框中，将内容替换为示例</span><span class="sxs-lookup"><span data-stu-id="80e95-209">In the Name box, replace the contents with Examples</span></span>
- <span data-ttu-id="80e95-210">单击“应用”</span><span class="sxs-lookup"><span data-stu-id="80e95-210">Click Apply</span></span>
- <span data-ttu-id="80e95-211">生成并部署</span><span class="sxs-lookup"><span data-stu-id="80e95-211">Build and deploy</span></span>

<span data-ttu-id="80e95-212">此问题将在即将发布的 MRTK 版本中解决。</span><span class="sxs-lookup"><span data-stu-id="80e95-212">This issue will be fixed in an upcoming MRTK release.</span></span>

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a><span data-ttu-id="80e95-213">MRTK 生成窗口触发 Unity 2020.3 中的 "导入资产" 对话框</span><span class="sxs-lookup"><span data-stu-id="80e95-213">MRTK build window triggers indefinite "Importing assets" dialog in Unity 2020.3</span></span>

<span data-ttu-id="80e95-214">Unity 2020.3 上的 MRTK 生成窗口存在一个已知 [问题](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) ，在成功执行 UWP 生成后，"导入资产" 对话框不会完成。</span><span class="sxs-lookup"><span data-stu-id="80e95-214">There is a known [issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) with the MRTK build window on Unity 2020.3 where after successfully performing a UWP build, the "Importing assets" dialog does not complete.</span></span> <span data-ttu-id="80e95-215">与 Unity 的合作调查中正在调查此问题。</span><span class="sxs-lookup"><span data-stu-id="80e95-215">This issue is being investigated in partnership with Unity.</span></span>

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a><span data-ttu-id="80e95-216">Unity 2020 中的文本网格 Pro 画布呈现器警告</span><span class="sxs-lookup"><span data-stu-id="80e95-216">Text Mesh Pro Canvas Renderer warnings in Unity 2020</span></span>

<span data-ttu-id="80e95-217">使用 Unity 2020 时，大多数 MRTK 示例场景中都记录了以下警告：</span><span class="sxs-lookup"><span data-stu-id="80e95-217">The following warning is logged in most MRTK example scenes while using Unity 2020:</span></span>

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

<span data-ttu-id="80e95-218">[TextMeshPro 版本 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3)中添加了画布呈现器警告。</span><span class="sxs-lookup"><span data-stu-id="80e95-218">The Canvas Renderer warning was added in [TextMeshPro version 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3).</span></span>  <span data-ttu-id="80e95-219">这些警告不会影响 MRTK 的示例场景，可以从控制台中清除。</span><span class="sxs-lookup"><span data-stu-id="80e95-219">These warning do not have an impact on MRTK's example scenes and can be cleared from the console.</span></span> <span data-ttu-id="80e95-220">有关更多详细信息，请参阅 [问题 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811) 。</span><span class="sxs-lookup"><span data-stu-id="80e95-220">See [Issue 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811) for more details.</span></span>
