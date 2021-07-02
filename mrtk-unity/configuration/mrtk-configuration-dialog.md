---
title: MRTK 配置对话框
description: 在 Unity Project 中配置 MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，Unity
ms.openlocfilehash: 50a0f40723c05e96f79eefab933942044afb22f1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177335"
---
# <a name="mrtk-configuration-dialog"></a><span data-ttu-id="a565a-104">MRTK 配置对话框</span><span class="sxs-lookup"><span data-stu-id="a565a-104">MRTK configuration dialog</span></span>

<span data-ttu-id="a565a-105">当 Unity 加载项目并且确定一个或多个配置选项需要开发人员关注时，将显示 "MRTK 配置" 对话框。</span><span class="sxs-lookup"><span data-stu-id="a565a-105">The MRTK configuration dialog is displayed when Unity loads a project and it is determined that one or more configuration options needs the attention of the developer.</span></span>

![稍后应用](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

<span data-ttu-id="a565a-107">若要应用更改，请单击 " **应用** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="a565a-107">To apply the changes, click the **Apply** button.</span></span> <span data-ttu-id="a565a-108">**稍后** 按钮将延迟更改，直到在将来重新加载项目。</span><span class="sxs-lookup"><span data-stu-id="a565a-108">The **Later** button will defer the changes until the project is reloaded at a future time.</span></span>

> [!NOTE]
> <span data-ttu-id="a565a-109">如果未选中一个或多个建议的设置，则配置对话框将重新出现。</span><span class="sxs-lookup"><span data-stu-id="a565a-109">The configuration dialog will reappear if one or more of the recommended settings is left unchecked.</span></span> <span data-ttu-id="a565a-110">若要防止此情况发生，请应用所需的选项，然后通过 **混合现实** 重新启动对话框 Toolkit  >  **实用程序**  >  **配置 Unity Project** 并单击 "**忽略**"。</span><span class="sxs-lookup"><span data-stu-id="a565a-110">To prevent this from occurring, apply the desired options, then relaunch the dialog via  **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click **Ignore**.</span></span> <span data-ttu-id="a565a-111">这会阻止配置对话框自动再次出现。</span><span class="sxs-lookup"><span data-stu-id="a565a-111">This will prevent the configuration dialog from reappearing automatically.</span></span>

## <a name="common-settings"></a><span data-ttu-id="a565a-112">通用设置</span><span class="sxs-lookup"><span data-stu-id="a565a-112">Common settings</span></span>

<span data-ttu-id="a565a-113">所有生成目标共享公用选项的集合。</span><span class="sxs-lookup"><span data-stu-id="a565a-113">All build targets share a collection of common options.</span></span>

![通用设置](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a><span data-ttu-id="a565a-115">强制文本资产序列化和启用可见元文件</span><span class="sxs-lookup"><span data-stu-id="a565a-115">Force text asset serialization and Enable visible meta files</span></span>

<span data-ttu-id="a565a-116">这些设置有助于简化使用 Unity 项目和源代码管理系统 (例如： Git) 。</span><span class="sxs-lookup"><span data-stu-id="a565a-116">These settings help simplify working with Unity projects and source control systems (ex: Git).</span></span>

### <a name="enable-vr-supported"></a><span data-ttu-id="a565a-117">支持启用 VR</span><span class="sxs-lookup"><span data-stu-id="a565a-117">Enable VR supported</span></span>

<span data-ttu-id="a565a-118">**Unity 2018**</span><span class="sxs-lookup"><span data-stu-id="a565a-118">**Unity 2018**</span></span>

<span data-ttu-id="a565a-119">在 **播放机** 中配置虚拟现实支持的虚拟机和虚拟现实 SDK 选项设置  >  **XR 设置**。</span><span class="sxs-lookup"><span data-stu-id="a565a-119">Configures the Virtual Reality Supported and Virtual Reality SDK options in **Player Settings** > **XR Settings**.</span></span>

### <a name="set-single-pass-instanced-rendering-path"></a><span data-ttu-id="a565a-120">设置单一传递实例呈现路径</span><span class="sxs-lookup"><span data-stu-id="a565a-120">Set Single Pass Instanced rendering path</span></span>

<span data-ttu-id="a565a-121">将 **播放机设置**  >  **XR 设置**  >  **立体声渲染模式** 配置为 **单步实例**。</span><span class="sxs-lookup"><span data-stu-id="a565a-121">Configures the **Player Settings** > **XR Settings** > **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>

### <a name="set-default-spatial-awareness-layer"></a><span data-ttu-id="a565a-122">设置默认空间感知层</span><span class="sxs-lookup"><span data-stu-id="a565a-122">Set default Spatial Awareness layer</span></span>

<span data-ttu-id="a565a-123">将空间感知注册为第31层，以实现 raycast 和物理学选项的简单一致的配置。</span><span class="sxs-lookup"><span data-stu-id="a565a-123">Registers Spatial Awareness as layer 31 to enable easy and consistent configuration of raycast and physics options.</span></span>

### <a name="audio-spatializer"></a><span data-ttu-id="a565a-124">音频 spatializer</span><span class="sxs-lookup"><span data-stu-id="a565a-124">Audio spatializer</span></span>

<span data-ttu-id="a565a-125">音频 spatializers 是用于解锁空间声音和位置音频功能的组件，使混合现实体验真正成为沉浸式体验。</span><span class="sxs-lookup"><span data-stu-id="a565a-125">Audio spatializers are the components that unlock the power of Spatial Sound and positional audio to make mixed reality experiences truly immersive.</span></span>

> [!NOTE]
> <span data-ttu-id="a565a-126">将音频 spatializer 设置为 "无" 将禁用位置音频特征。</span><span class="sxs-lookup"><span data-stu-id="a565a-126">Setting the audio spatializer to None will disable positional audio features.</span></span>

#### <a name="common-spatializers"></a><span data-ttu-id="a565a-127">常见 spatializers</span><span class="sxs-lookup"><span data-stu-id="a565a-127">Common spatializers</span></span>

- <span data-ttu-id="a565a-128">Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="a565a-128">Microsoft Spatializer</span></span>

<span data-ttu-id="a565a-129">Microsoft 提供的 spatializer 支持 HoloLens 2 上的硬件加速。</span><span class="sxs-lookup"><span data-stu-id="a565a-129">Microsoft provided spatializer that supports utilization of hardware acceleration on HoloLens 2.</span></span>

<span data-ttu-id="a565a-130">此 spatializer 通过[NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/)和[GitHub](https://github.com/microsoft/spatialaudio-unity)提供。</span><span class="sxs-lookup"><span data-stu-id="a565a-130">This spatializer is available via [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) and [GitHub](https://github.com/microsoft/spatialaudio-unity).</span></span>

<span data-ttu-id="a565a-131">有关 Microsoft Spatializer 的更多详细信息，请参阅 [空间音效文档](/windows/mixed-reality/spatial-sound-in-unity)。</span><span class="sxs-lookup"><span data-stu-id="a565a-131">More details on Microsoft Spatializer can be found in the [Spatial Sound documentation](/windows/mixed-reality/spatial-sound-in-unity).</span></span>

- <span data-ttu-id="a565a-132">MS HRTF Spatializer</span><span class="sxs-lookup"><span data-stu-id="a565a-132">MS HRTF Spatializer</span></span>

<span data-ttu-id="a565a-133">Microsoft Windows spatializer，由 Unity 作为 Windows Mixed Reality 和 Windows XR 平台包的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="a565a-133">Microsoft Windows spatializer that is provided by Unity as part of the Windows Mixed Reality and Windows XR Platform packages.</span></span>

- <span data-ttu-id="a565a-134">Resonance 音频</span><span class="sxs-lookup"><span data-stu-id="a565a-134">Resonance Audio</span></span>

<span data-ttu-id="a565a-135">由 Unity 提供的来自 Google 的跨平台 spatializer。</span><span class="sxs-lookup"><span data-stu-id="a565a-135">A cross platform spatializer from Google that is provided by Unity.</span></span>

<span data-ttu-id="a565a-136">有关详细信息，请参阅 [Resonance 音频文档](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) 网站。</span><span class="sxs-lookup"><span data-stu-id="a565a-136">More information can be found on the [Resonance Audio documentation](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) site.</span></span>

## <a name="universal-windows-platform-settings"></a><span data-ttu-id="a565a-137">通用 Windows 平台设置</span><span class="sxs-lookup"><span data-stu-id="a565a-137">Universal Windows Platform settings</span></span>

![UWP 设置](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a><span data-ttu-id="a565a-139">UWP 功能</span><span class="sxs-lookup"><span data-stu-id="a565a-139">UWP Capabilities</span></span>

<span data-ttu-id="a565a-140">为通用 Windows 平台应用程序启用特定应用程序功能。</span><span class="sxs-lookup"><span data-stu-id="a565a-140">Enables specific application capabilities for Universal Windows Platform application.</span></span> <span data-ttu-id="a565a-141">这些功能使平台能够通知并请求启用特定功能的权限。</span><span class="sxs-lookup"><span data-stu-id="a565a-141">These capabilities enable the platform to inform and request permission to enable specific functionality.</span></span>

- <span data-ttu-id="a565a-142">麦克风</span><span class="sxs-lookup"><span data-stu-id="a565a-142">Microphone</span></span>

  <span data-ttu-id="a565a-143">通过麦克风启用捕获声音。</span><span class="sxs-lookup"><span data-stu-id="a565a-143">Enables capturing sound via the microphone.</span></span>

- <span data-ttu-id="a565a-144">Internet 客户端</span><span class="sxs-lookup"><span data-stu-id="a565a-144">Internet Client</span></span>

  <span data-ttu-id="a565a-145">支持访问 internet 上的资源。</span><span class="sxs-lookup"><span data-stu-id="a565a-145">Enables support for accessing resources on the internet.</span></span>

- <span data-ttu-id="a565a-146">空间感知</span><span class="sxs-lookup"><span data-stu-id="a565a-146">Spatial Perception</span></span>

  <span data-ttu-id="a565a-147">启用对使用实际环境的支持。</span><span class="sxs-lookup"><span data-stu-id="a565a-147">Enables support for using the real-world environment.</span></span>

- <span data-ttu-id="a565a-148">眼睛</span><span class="sxs-lookup"><span data-stu-id="a565a-148">Eye Gaze</span></span>

  <span data-ttu-id="a565a-149">**Unity 2019.3 和更高版本**</span><span class="sxs-lookup"><span data-stu-id="a565a-149">**Unity 2019.3 and newer**</span></span>

  <span data-ttu-id="a565a-150">启用对跟踪用户眼睛的支持。</span><span class="sxs-lookup"><span data-stu-id="a565a-150">Enables support for tracking the user's eye gaze.</span></span>

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a><span data-ttu-id="a565a-151">避免 Unity "PlayerSettings. graphicsJob" 崩溃</span><span class="sxs-lookup"><span data-stu-id="a565a-151">Avoid Unity 'PlayerSettings.graphicsJob' crash</span></span>

<span data-ttu-id="a565a-152">**Unity 2019.3 和更高版本**</span><span class="sxs-lookup"><span data-stu-id="a565a-152">**Unity 2019.3 and newer**</span></span>

<span data-ttu-id="a565a-153">在最新版本的 Unity 2019 中，当启用 "图形作业" 时，应用将在部署到 HoloLens 2 时崩溃。</span><span class="sxs-lookup"><span data-stu-id="a565a-153">In the latest version of Unity 2019, when "Graphics Jobs" is enabled, the app will crash when deployed to a HoloLens 2.</span></span>
<span data-ttu-id="a565a-154">默认情况下，在 Unity 中启用此设置-尽管存在此 bug (请参阅[Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)) ，配置器将默认设置为 "false" 的图形作业 (因此，可以允许部署到 HoloLens 2 不会崩溃) 的应用。</span><span class="sxs-lookup"><span data-stu-id="a565a-154">This setting is enabled by default in Unity - while this bug exists (see [Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), the configurator will default to setting Graphics Jobs to 'false' (thus allowing apps deployed to HoloLens 2 not to crash).</span></span>

## <a name="android-settings"></a><span data-ttu-id="a565a-155">Android 设置</span><span class="sxs-lookup"><span data-stu-id="a565a-155">Android settings</span></span>

<span data-ttu-id="a565a-156">支持 Android 设备上的 AR 应用程序的配置设置。</span><span class="sxs-lookup"><span data-stu-id="a565a-156">Configuration settings to support AR applications on Android powered devices.</span></span>

![Android 设置](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a><span data-ttu-id="a565a-158">禁用多线程呈现</span><span class="sxs-lookup"><span data-stu-id="a565a-158">Disable Multi-Threaded Rendering</span></span>

<span data-ttu-id="a565a-159">禁用 **播放器设置**  >  **其他设置**  >  **多线程呈现**，如 Android 的 AR 支持的要求。</span><span class="sxs-lookup"><span data-stu-id="a565a-159">Disables **Player Settings** > **Other Settings** > **Multithreaded Rendering** as required by Android's AR support.</span></span>

### <a name="set-minimum-api-level"></a><span data-ttu-id="a565a-160">设置最低 API 级别</span><span class="sxs-lookup"><span data-stu-id="a565a-160">Set Minimum API Level</span></span>

<span data-ttu-id="a565a-161">将 Player 的值设置 **设置**  >  **其他设置**  >  **最低 API 级别**，以强制执行 AR 应用程序的操作系统要求。</span><span class="sxs-lookup"><span data-stu-id="a565a-161">Sets the value of **Player Settings** > **Other Settings** > **Minimum API Level** to enforce operating system requirements for AR applications.</span></span>

## <a name="ios-settings"></a><span data-ttu-id="a565a-162">iOS 设置</span><span class="sxs-lookup"><span data-stu-id="a565a-162">iOS settings</span></span>

<span data-ttu-id="a565a-163">支持 iOS 设备上的 AR 应用程序的配置设置。</span><span class="sxs-lookup"><span data-stu-id="a565a-163">Configuration settings to support AR applications on iOS powered devices.</span></span>

![iOS 设置](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a><span data-ttu-id="a565a-165">设置所需的 OS 版本</span><span class="sxs-lookup"><span data-stu-id="a565a-165">Set Required OS Version</span></span>

<span data-ttu-id="a565a-166">设置 **设置**  >  **其他设置**  >  **目标最低 iOS 版本** 的播放机的值，以强制执行 AR 应用程序的操作系统要求。</span><span class="sxs-lookup"><span data-stu-id="a565a-166">Sets the value of **Player Settings** > **Other Settings** > **Target minimum iOS Version** to enforce operating system requirements for AR applications.</span></span>

### <a name="set-required-architecture"></a><span data-ttu-id="a565a-167">设置所需的体系结构</span><span class="sxs-lookup"><span data-stu-id="a565a-167">Set Required Architecture</span></span>

<span data-ttu-id="a565a-168">设置 **设置**  >  **其他设置** 体系结构的播放机的值  >   ，以强制执行 AR 应用程序的平台要求。</span><span class="sxs-lookup"><span data-stu-id="a565a-168">Sets the value of **Player Settings** > **Other Settings** > **Architecture** to enforce platform requirements for AR applications.</span></span>

### <a name="set-camera-usage-descriptions"></a><span data-ttu-id="a565a-169">设置相机使用说明</span><span class="sxs-lookup"><span data-stu-id="a565a-169">Set Camera Usage Descriptions</span></span>

<span data-ttu-id="a565a-170">设置 **播放机的值设置**  >  **其他设置**  >  **相机使用情况说明**，用于请求使用设备相机的权限。</span><span class="sxs-lookup"><span data-stu-id="a565a-170">Sets the value of **Player Settings** > **Other Settings** > **Camera Usage Description** used to request permission to use the device's camera.</span></span>
