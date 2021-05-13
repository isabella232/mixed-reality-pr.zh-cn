---
title: 部署到 Hololens 和 WMR 设备
description: 介绍生成应用并将其部署到各种设备中的文档。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，Visual Studio
ms.openlocfilehash: ec66c6ccb8cf1c702fed804230f5cf3ca0526139
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852338"
---
# <a name="building-and-deploying-mrtk-uwp"></a><span data-ttu-id="0861d-104">生成并部署 MRTK (UWP) </span><span class="sxs-lookup"><span data-stu-id="0861d-104">Building and deploying MRTK (UWP)</span></span>

<span data-ttu-id="0861d-105">若要在设备上将某应用作为独立应用来运行（对于 HoloLens,、Android、iOS 等），需要在 Unity 项目中执行生成和部署步骤。</span><span class="sxs-lookup"><span data-stu-id="0861d-105">To run an app on device as a standalone app (for HoloLens, Android, iOS, etc.), the build and deploy step needs to be executed in the unity project.</span></span> <span data-ttu-id="0861d-106">生成和部署使用 MRTK 的应用就像生成和部署任何其他 Unity 应用一样。</span><span class="sxs-lookup"><span data-stu-id="0861d-106">Building and deploying an app that uses MRTK is just like building and deploying any other Unity app.</span></span> <span data-ttu-id="0861d-107">不存在 MRTK 特定的说明。</span><span class="sxs-lookup"><span data-stu-id="0861d-107">There are no MRTK-specific instructions.</span></span> <span data-ttu-id="0861d-108">请在下面查看详细步骤，了解如何生成和部署适合 HoloLens 的 Unity 应用。</span><span class="sxs-lookup"><span data-stu-id="0861d-108">Read below for detailed steps on how to build and deploy a Unity app for HoloLens.</span></span> <span data-ttu-id="0861d-109">在[发布版本](https://docs.unity3d.com/Manual/PublishingBuilds.html)中详细了解如何针对其他平台进行生成。</span><span class="sxs-lookup"><span data-stu-id="0861d-109">Learn more about building for other platforms at [Publishing Builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="0861d-110">生成 MRTK 并将其部署到 HoloLens 1、HoloLens 2 和 WMR 耳机 (UWP) </span><span class="sxs-lookup"><span data-stu-id="0861d-110">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="0861d-111">有关如何为 **hololens 1** 和 **HOLOLENS 2** (UWP) 进行生成和部署的说明，请参阅在 [设备上生成应用程序](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device)。</span><span class="sxs-lookup"><span data-stu-id="0861d-111">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="0861d-112">这些步骤还允许你部署到 **WMR 耳机**。</span><span class="sxs-lookup"><span data-stu-id="0861d-112">These steps also allow you to deploy to **WMR headsets**.</span></span>

<span data-ttu-id="0861d-113">**提示：** 为 HoloLens 1、HoloLens 2 或 WMR 进行生成时，建议生成设置 "目标 SDK 版本" 和 "最低平台版本" 与下图中所示类似：</span><span class="sxs-lookup"><span data-stu-id="0861d-113">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![“生成”窗口](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="0861d-115">其他设置可以不同（例如，随时都能在 Visual Studio 解决方案中更改生成配置/体系结构/生成类型和其他信息）。</span><span class="sxs-lookup"><span data-stu-id="0861d-115">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="0861d-116">确保“目标 SDK 版本”下拉列表包含“10.0.18362.0”选项 - 如果没有此选项，则需要安装[最新版的 Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。</span><span class="sxs-lookup"><span data-stu-id="0861d-116">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="0861d-117">Unity 2019.3 和 HoloLens</span><span class="sxs-lookup"><span data-stu-id="0861d-117">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="0861d-118">如果某个 HoloLens 应用在设备上显示为 2D 面板，请确保在部署 UWP 应用之前，已在 Unity 2019.3.x 中配置以下设置：</span><span class="sxs-lookup"><span data-stu-id="0861d-118">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="0861d-119">如果使用的是旧版 XR：</span><span class="sxs-lookup"><span data-stu-id="0861d-119">If using the legacy XR:</span></span>

1. <span data-ttu-id="0861d-120">导航到“编辑”>“项目设置，播放器”</span><span class="sxs-lookup"><span data-stu-id="0861d-120">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="0861d-121">在 UWP 选项卡的“XR 设置”下，确保已启用“支持的虚拟现实”且已在 SDK 中添加 Windows Mixed Reality SDK  。</span><span class="sxs-lookup"><span data-stu-id="0861d-121">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="0861d-122">在 Visual Studio 中生成和部署</span><span class="sxs-lookup"><span data-stu-id="0861d-122">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="0861d-123">如果使用的是 XR 插件：</span><span class="sxs-lookup"><span data-stu-id="0861d-123">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="0861d-124">按照在 [XRSDK 入门](../configuration/getting-started-with-mrtk-and-xrsdk.md)中找到的步骤操作</span><span class="sxs-lookup"><span data-stu-id="0861d-124">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="0861d-125">确保配置文件是 DefaultXRSDKConfigurationProfile</span><span class="sxs-lookup"><span data-stu-id="0861d-125">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="0861d-126">导航到“编辑”>“项目设置，XR 插件管理”，确保已启用 Windows Mixed Reality 。</span><span class="sxs-lookup"><span data-stu-id="0861d-126">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="0861d-127">在 Visual Studio 中生成和部署</span><span class="sxs-lookup"><span data-stu-id="0861d-127">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="0861d-128">如果使用的是 Unity 2019.3.x，请在 Visual Studio 中选择 ARM64（而不是 ARM）作为生成体系结构 。</span><span class="sxs-lookup"><span data-stu-id="0861d-128">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="0861d-129">使用 Unity 2019.3.x 中的默认 Unity 设置时，如果由于 Unity bug 而选择了 ARM，则 Unity 应用将不会部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0861d-129">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="0861d-130">可在 [Unity 的问题跟踪器](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)上跟踪此问题。</span><span class="sxs-lookup"><span data-stu-id="0861d-130">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="0861d-131">如果需要使用 ARM 体系结构，请导航到“编辑”>“项目设置，播放器”，然后在“其他设置”菜单下，禁用“图形作业”  。</span><span class="sxs-lookup"><span data-stu-id="0861d-131">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="0861d-132">如果禁用“图形作业”，那么应用将能够对 Unity 2019.3.x 使用 ARM 生成体系结构进行部署，但建议使用 ARM64。</span><span class="sxs-lookup"><span data-stu-id="0861d-132">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-standalone"></a><span data-ttu-id="0861d-133">构建和部署 MRTK (独立) </span><span class="sxs-lookup"><span data-stu-id="0861d-133">Building and deploying MRTK (Standalone)</span></span>

<span data-ttu-id="0861d-134">可在 WMR 耳机上使用独立的 MRTK 版本。</span><span class="sxs-lookup"><span data-stu-id="0861d-134">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="0861d-135">对于适合 WMR 头戴显示设备的独立版本，需额外执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="0861d-135">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="0861d-136">Unity 的 XR SDK 也支持独立版本中的原生 WMR，但它不需要 SteamVR 或 WMR 插件。</span><span class="sxs-lookup"><span data-stu-id="0861d-136">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="0861d-137">需要对 Unity 的旧版 XR 执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="0861d-137">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="0861d-138">安装 [Steam](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="0861d-138">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="0861d-139">安装 [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="0861d-139">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="0861d-140">安装 [WMR 插件](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="0861d-140">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="0861d-141">如何使用 WMR 插件</span><span class="sxs-lookup"><span data-stu-id="0861d-141">How to use WMR plugin</span></span>

1. <span data-ttu-id="0861d-142">打开 Steam 并搜索 Windows Mixed Reality 插件</span><span class="sxs-lookup"><span data-stu-id="0861d-142">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="0861d-143">在启动 WMR 插件之前，请确保 SteamVR 已关闭。</span><span class="sxs-lookup"><span data-stu-id="0861d-143">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="0861d-144">启动 WMR 插件时会一并启动 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="0861d-144">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="0861d-145">确保 WMR 头戴显示设备已接通电源。</span><span class="sxs-lookup"><span data-stu-id="0861d-145">Make sure the WMR headset is plugged in.</span></span>

    ![WMR 插件搜索](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="0861d-147">为 SteamVR 的 Windows Mixed Reality 插件选择“启动”。</span><span class="sxs-lookup"><span data-stu-id="0861d-147">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![WMR 插件](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="0861d-149">这会启动 SteamVR 和 WMR 插件，并对 WMR 头戴显示设备显示新的跟踪状态窗口。</span><span class="sxs-lookup"><span data-stu-id="0861d-149">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="0861d-150">有关详细信息，请访问 [Windows Mixed Reality Steam 文档](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span><span class="sxs-lookup"><span data-stu-id="0861d-150">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![WMR 启动外观](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="0861d-152">在 Unity 中，在 MRTK 屏幕打开的情况下导航到“文件”>“生成设置”</span><span class="sxs-lookup"><span data-stu-id="0861d-152">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="0861d-153">生成场景</span><span class="sxs-lookup"><span data-stu-id="0861d-153">Build the scene</span></span>
    - <span data-ttu-id="0861d-154">选择“添加开放式场景”</span><span class="sxs-lookup"><span data-stu-id="0861d-154">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="0861d-155">确保该平台是独立平台</span><span class="sxs-lookup"><span data-stu-id="0861d-155">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="0861d-156">选择“生成”</span><span class="sxs-lookup"><span data-stu-id="0861d-156">Select **Build**</span></span>
    - <span data-ttu-id="0861d-157">在文件资源管理器中为新的生成项选择位置</span><span class="sxs-lookup"><span data-stu-id="0861d-157">Choose the location for the new build in File Explorer</span></span>

    ![适合独立版本的生成设置](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="0861d-159">这将创建一个新的 Unity 可执行文件。若要启用应用，请在文件资源管理器中选择该 Unity 可执行文件。</span><span class="sxs-lookup"><span data-stu-id="0861d-159">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![文件资源管理器 Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="0861d-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0861d-161">See also</span></span>

- [<span data-ttu-id="0861d-162">Android 和 iOS 支持</span><span class="sxs-lookup"><span data-stu-id="0861d-162">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="0861d-163">Leap Motion 支持</span><span class="sxs-lookup"><span data-stu-id="0861d-163">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="0861d-164">检测平台功能</span><span class="sxs-lookup"><span data-stu-id="0861d-164">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)