---
title: BuildAndDeploy
description: 介绍生成应用并将其部署到各种设备中的文档。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity,HoloLens, HoloLens 2, 混合现实, 开发, MRTK, Visual Studio, Android, IOS
ms.openlocfilehash: f86e70fb80e854111c62391d706a8d33fcd67c90
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101765219"
---
# <a name="building-and-deploying-mrtk"></a><span data-ttu-id="3ef4d-104">生成和部署 MRTK</span><span class="sxs-lookup"><span data-stu-id="3ef4d-104">Building and deploying MRTK</span></span>

<span data-ttu-id="3ef4d-105">若要在设备上将某应用作为独立应用来运行（对于 HoloLens,、Android、iOS 等），需要在 Unity 项目中执行生成和部署步骤。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-105">To run an app on device as a standalone app (for HoloLens, Android, iOS, etc.), the build and deploy step needs to be executed in the unity project.</span></span> <span data-ttu-id="3ef4d-106">生成和部署使用 MRTK 的应用就像生成和部署任何其他 Unity 应用一样。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-106">Building and deploying an app that uses MRTK is just like building and deploying any other Unity app.</span></span> <span data-ttu-id="3ef4d-107">不存在 MRTK 特定的说明。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-107">There are no MRTK-specific instructions.</span></span> <span data-ttu-id="3ef4d-108">请在下面查看详细步骤，了解如何生成和部署适合 HoloLens 的 Unity 应用。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-108">Read below for detailed steps on how to build and deploy a Unity app for HoloLens.</span></span>  <span data-ttu-id="3ef4d-109">在[发布版本](https://docs.unity3d.com/Manual/PublishingBuilds.html)中详细了解如何针对其他平台进行生成。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-109">Learn more about building for other platforms at [Publishing Builds](https://docs.unity3d.com/Manual/PublishingBuilds.html).</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-and-hololens-2-uwp"></a><span data-ttu-id="3ef4d-110">生成 MRTK 并将其部署到 HoloLens 1 和 HoloLens 2 (UWP)</span><span class="sxs-lookup"><span data-stu-id="3ef4d-110">Building and deploying MRTK to HoloLens 1 and HoloLens 2 (UWP)</span></span>

<span data-ttu-id="3ef4d-111">有关如何为 HoloLens 1 和 HoloLens 2 (UWP) 进行生成和部署的说明，可查看[生成应用程序并将其部署到设备上](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device)。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-111">Instructions on how to build and deploy for HoloLens 1 and HoloLens 2 (UWP) can be found at [building your application to device](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span>

<span data-ttu-id="3ef4d-112">**提示：** 针对 WMR、HoloLens 1 或 HoloLens 2 进行生成时，建议生成设置“目标 SDK 版本”和“最低平台版本”设为如下图所示：</span><span class="sxs-lookup"><span data-stu-id="3ef4d-112">**Tip:** When building for WMR, HoloLens 1, or HoloLens 2, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![“生成”窗口](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="3ef4d-114">其他设置可以不同（例如，随时都能在 Visual Studio 解决方案中更改生成配置/体系结构/生成类型和其他信息）。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-114">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="3ef4d-115">确保“目标 SDK 版本”下拉列表包含“10.0.18362.0”选项 - 如果没有此选项，则需要安装[最新版的 Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-115">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="3ef4d-116">Unity 2019.3 和 HoloLens</span><span class="sxs-lookup"><span data-stu-id="3ef4d-116">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="3ef4d-117">如果某个 HoloLens 应用在设备上显示为 2D 面板，请确保在部署 UWP 应用之前，已在 Unity 2019.3.x 中配置以下设置：</span><span class="sxs-lookup"><span data-stu-id="3ef4d-117">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="3ef4d-118">如果使用的是旧版 XR：</span><span class="sxs-lookup"><span data-stu-id="3ef4d-118">If using the legacy XR:</span></span>

1. <span data-ttu-id="3ef4d-119">导航到“编辑”>“项目设置，播放器”</span><span class="sxs-lookup"><span data-stu-id="3ef4d-119">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="3ef4d-120">在 UWP 选项卡的“XR 设置”下，确保已启用“支持的虚拟现实”且已在 SDK 中添加 Windows Mixed Reality SDK  。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-120">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="3ef4d-121">在 Visual Studio 中生成和部署</span><span class="sxs-lookup"><span data-stu-id="3ef4d-121">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="3ef4d-122">如果使用的是 XR 插件：</span><span class="sxs-lookup"><span data-stu-id="3ef4d-122">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="3ef4d-123">按照在 [XRSDK 入门](../configuration/getting-started-with-mrtk-and-xrsdk.md)中找到的步骤操作</span><span class="sxs-lookup"><span data-stu-id="3ef4d-123">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="3ef4d-124">确保配置文件是 DefaultXRSDKConfigurationProfile</span><span class="sxs-lookup"><span data-stu-id="3ef4d-124">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="3ef4d-125">导航到“编辑”>“项目设置，XR 插件管理”，确保已启用 Windows Mixed Reality 。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-125">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="3ef4d-126">在 Visual Studio 中生成和部署</span><span class="sxs-lookup"><span data-stu-id="3ef4d-126">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="3ef4d-127">如果使用的是 Unity 2019.3.x，请在 Visual Studio 中选择 ARM64（而不是 ARM）作为生成体系结构 。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-127">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="3ef4d-128">使用 Unity 2019.3.x 中的默认 Unity 设置时，如果由于 Unity bug 而选择了 ARM，则 Unity 应用将不会部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-128">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="3ef4d-129">可在 [Unity 的问题跟踪器](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)上跟踪此问题。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-129">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="3ef4d-130">如果需要使用 ARM 体系结构，请导航到“编辑”>“项目设置，播放器”，然后在“其他设置”菜单下，禁用“图形作业”  。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-130">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="3ef4d-131">如果禁用“图形作业”，那么应用将能够对 Unity 2019.3.x 使用 ARM 生成体系结构进行部署，但建议使用 ARM64。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-131">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-to-a-windows-mixed-reality-headset"></a><span data-ttu-id="3ef4d-132">生成 MRTK 并将其部署到 Windows Mixed Reality 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="3ef4d-132">Building and deploying MRTK to a Windows Mixed Reality Headset</span></span>

<span data-ttu-id="3ef4d-133">Windows Mixed Reality (WMR) 头戴显示设备可用于通用 Windows 平台 (UWP) 和独立版本。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-133">The Windows Mixed Reality (WMR) headset can be used for Universal Windows Platform (UWP) and Standalone builds.</span></span>  <span data-ttu-id="3ef4d-134">对于适合 WMR 头戴显示设备的独立版本，需额外执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="3ef4d-134">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="3ef4d-135">Unity 的 XR SDK 也支持独立版本中的原生 WMR，但它不需要 SteamVR 或 WMR 插件。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-135">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="3ef4d-136">需要对 Unity 的旧版 XR 执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-136">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="3ef4d-137">安装 [Steam](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="3ef4d-137">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="3ef4d-138">安装 [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="3ef4d-138">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="3ef4d-139">安装 [WMR 插件](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="3ef4d-139">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="3ef4d-140">如何使用 WMR 插件</span><span class="sxs-lookup"><span data-stu-id="3ef4d-140">How to use WMR plugin</span></span>

1. <span data-ttu-id="3ef4d-141">打开 Steam 并搜索 Windows Mixed Reality 插件</span><span class="sxs-lookup"><span data-stu-id="3ef4d-141">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="3ef4d-142">在启动 WMR 插件之前，请确保 SteamVR 已关闭。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-142">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="3ef4d-143">启动 WMR 插件时会一并启动 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-143">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="3ef4d-144">确保 WMR 头戴显示设备已接通电源。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-144">Make sure the WMR headset is plugged in.</span></span>

    ![WMR 插件搜索](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="3ef4d-146">为 SteamVR 的 Windows Mixed Reality 插件选择“启动”。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-146">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![WMR 插件](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="3ef4d-148">这会启动 SteamVR 和 WMR 插件，并对 WMR 头戴显示设备显示新的跟踪状态窗口。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-148">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="3ef4d-149">有关详细信息，请访问 [Windows Mixed Reality Steam 文档](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span><span class="sxs-lookup"><span data-stu-id="3ef4d-149">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![WMR 启动外观](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="3ef4d-151">在 Unity 中，在 MRTK 屏幕打开的情况下导航到“文件”>“生成设置”</span><span class="sxs-lookup"><span data-stu-id="3ef4d-151">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="3ef4d-152">生成场景</span><span class="sxs-lookup"><span data-stu-id="3ef4d-152">Build the scene</span></span>
    - <span data-ttu-id="3ef4d-153">选择“添加开放式场景”</span><span class="sxs-lookup"><span data-stu-id="3ef4d-153">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="3ef4d-154">确保该平台是独立平台</span><span class="sxs-lookup"><span data-stu-id="3ef4d-154">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="3ef4d-155">选择“生成”</span><span class="sxs-lookup"><span data-stu-id="3ef4d-155">Select **Build**</span></span>
    - <span data-ttu-id="3ef4d-156">在文件资源管理器中为新的生成项选择位置</span><span class="sxs-lookup"><span data-stu-id="3ef4d-156">Choose the location for the new build in File Explorer</span></span>

    ![适合独立版本的生成设置](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="3ef4d-158">这将创建一个新的 Unity 可执行文件。若要启用应用，请在文件资源管理器中选择该 Unity 可执行文件。</span><span class="sxs-lookup"><span data-stu-id="3ef4d-158">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![文件资源管理器 Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="3ef4d-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ef4d-160">See also</span></span>

- [<span data-ttu-id="3ef4d-161">Android 和 iOS 支持</span><span class="sxs-lookup"><span data-stu-id="3ef4d-161">Android and iOS Support</span></span>](../features/cross-platform/using-ar-foundation.md)
- [<span data-ttu-id="3ef4d-162">Leap Motion 支持</span><span class="sxs-lookup"><span data-stu-id="3ef4d-162">Leap Motion Support</span></span>](../features/cross-platform/leap-motion-mrtk.md)
- [<span data-ttu-id="3ef4d-163">检测平台功能</span><span class="sxs-lookup"><span data-stu-id="3ef4d-163">Detecting Platform Capabilities</span></span>](../features/cross-platform/detecting-platform-capabilities.md)
