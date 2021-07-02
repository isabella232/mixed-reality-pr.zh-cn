---
title: 部署到 HoloLens 和 WMR 耳机
description: 介绍生成应用并将其部署到各种设备中的文档。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，Visual Studio
ms.openlocfilehash: 137e1b699e9a0cda1e8a454a6c3219b581fa71b4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176376"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a><span data-ttu-id="704ac-104">部署到 HoloLens 和 WMR 耳机</span><span class="sxs-lookup"><span data-stu-id="704ac-104">Deploying to HoloLens and WMR headsets</span></span>

<span data-ttu-id="704ac-105">可以通过两种方式将用 MRTK 构建的应用程序部署到 windows 设备、通用 Windows 平台 (UWP) 和独立平台。</span><span class="sxs-lookup"><span data-stu-id="704ac-105">There are two ways to deploy applications built with MRTK to your windows device, the Univeral Windows Platform (UWP) and the Standalone Platform.</span></span> <span data-ttu-id="704ac-106">为 HoloLens 1 或 HoloLens 2 生成的应用程序必须以 uwp 为目标，而为 WMR 耳机构建的应用程序可能面向 uwp 或独立。</span><span class="sxs-lookup"><span data-stu-id="704ac-106">Applications built for HoloLens 1 or HoloLens 2 must target UWP, while applications built for WMR headsets may target either UWP or Standalone.</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="704ac-107">构建 MRTK 并将其部署到 HoloLens 1、HoloLens 2 和 WMR 耳机 (UWP) </span><span class="sxs-lookup"><span data-stu-id="704ac-107">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="704ac-108">有关如何生成和部署 **HoloLens 1** 和 **HoloLens 2** (UWP) 的说明，请参阅在 [设备上生成应用程序](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device)。</span><span class="sxs-lookup"><span data-stu-id="704ac-108">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="704ac-109">这些步骤还允许你部署到 **WMR 耳机**。</span><span class="sxs-lookup"><span data-stu-id="704ac-109">These steps also allow you to deploy to **WMR headsets**.</span></span>

> [!NOTE]
> <span data-ttu-id="704ac-110">在 Visual Studio 中将应用程序部署到设备时，需要根据设备配置 Visual Studio 略有不同。</span><span class="sxs-lookup"><span data-stu-id="704ac-110">When deploying your application to your device in Visual Studio, you need to configure Visual Studio slightly differently depending on the device.</span></span> <span data-ttu-id="704ac-111">配置如下所示</span><span class="sxs-lookup"><span data-stu-id="704ac-111">The configurations are as follows</span></span>
>
>| <span data-ttu-id="704ac-112">平台</span><span class="sxs-lookup"><span data-stu-id="704ac-112">Platform</span></span> | <span data-ttu-id="704ac-113">配置</span><span class="sxs-lookup"><span data-stu-id="704ac-113">Configuration</span></span> | <span data-ttu-id="704ac-114">体系结构</span><span class="sxs-lookup"><span data-stu-id="704ac-114">Architecture</span></span> | <span data-ttu-id="704ac-115">目标</span><span class="sxs-lookup"><span data-stu-id="704ac-115">Target</span></span> |
|---|---|---|---|
| <span data-ttu-id="704ac-116">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="704ac-116">HoloLens 2</span></span> | <span data-ttu-id="704ac-117">Release 或 Master</span><span class="sxs-lookup"><span data-stu-id="704ac-117">Release or Master</span></span> | <span data-ttu-id="704ac-118">ARM64</span><span class="sxs-lookup"><span data-stu-id="704ac-118">ARM64</span></span> | <span data-ttu-id="704ac-119">设备</span><span class="sxs-lookup"><span data-stu-id="704ac-119">Device</span></span> |
| <span data-ttu-id="704ac-120">HoloLens 1</span><span class="sxs-lookup"><span data-stu-id="704ac-120">HoloLens 1</span></span> | <span data-ttu-id="704ac-121">Release 或 Master</span><span class="sxs-lookup"><span data-stu-id="704ac-121">Release or Master</span></span> | <span data-ttu-id="704ac-122">x86</span><span class="sxs-lookup"><span data-stu-id="704ac-122">x86</span></span> | <span data-ttu-id="704ac-123">设备</span><span class="sxs-lookup"><span data-stu-id="704ac-123">Device</span></span> |
| <span data-ttu-id="704ac-124">WMR 耳机</span><span class="sxs-lookup"><span data-stu-id="704ac-124">WMR Headsets</span></span> | <span data-ttu-id="704ac-125">Release 或 Master</span><span class="sxs-lookup"><span data-stu-id="704ac-125">Release or Master</span></span> | <span data-ttu-id="704ac-126">X64</span><span class="sxs-lookup"><span data-stu-id="704ac-126">x64</span></span> | <span data-ttu-id="704ac-127">本地计算机</span><span class="sxs-lookup"><span data-stu-id="704ac-127">Local Machine</span></span> |

<span data-ttu-id="704ac-128">**提示：** 为 HoloLens 1、HoloLens 2 或 WMR 进行生成时，建议生成设置 "目标 SDK 版本" 和 "最低平台版本" 与下图中所示类似：</span><span class="sxs-lookup"><span data-stu-id="704ac-128">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![“生成”窗口](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="704ac-130">其他设置可以不同（例如，随时都能在 Visual Studio 解决方案中更改生成配置/体系结构/生成类型和其他信息）。</span><span class="sxs-lookup"><span data-stu-id="704ac-130">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="704ac-131">确保“目标 SDK 版本”下拉列表包含“10.0.18362.0”选项 - 如果没有此选项，则需要安装[最新版的 Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。</span><span class="sxs-lookup"><span data-stu-id="704ac-131">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20192020-and-hololens"></a><span data-ttu-id="704ac-132">Unity 2019/2020 和 HoloLens</span><span class="sxs-lookup"><span data-stu-id="704ac-132">Unity 2019/2020 and HoloLens</span></span>

<span data-ttu-id="704ac-133">如果 HoloLens 应用在设备上显示为2d 面板，请确保在部署 UWP 应用之前已在 Unity 中配置以下设置：</span><span class="sxs-lookup"><span data-stu-id="704ac-133">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity before deploying your UWP app:</span></span>

<span data-ttu-id="704ac-134">如果使用旧的内置 XR 支持 (仅) Unity 2019：</span><span class="sxs-lookup"><span data-stu-id="704ac-134">If using the legacy built-in XR support (Unity 2019 only):</span></span>

1. <span data-ttu-id="704ac-135">导航到“编辑”>“项目设置，播放器”</span><span class="sxs-lookup"><span data-stu-id="704ac-135">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="704ac-136">在 UWP 选项卡的“XR 设置”下，确保已启用“支持的虚拟现实”且已在 SDK 中添加 Windows Mixed Reality SDK  。</span><span class="sxs-lookup"><span data-stu-id="704ac-136">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="704ac-137">在 Visual Studio 中生成和部署</span><span class="sxs-lookup"><span data-stu-id="704ac-137">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="704ac-138">如果使用的是 OpenXR 或 Windows XR 插件：</span><span class="sxs-lookup"><span data-stu-id="704ac-138">If using the OpenXR or Windows XR plugins:</span></span>

1. <span data-ttu-id="704ac-139">按照在 [XRSDK 入门](../configuration/getting-started-with-mrtk-and-xrsdk.md)中找到的步骤操作</span><span class="sxs-lookup"><span data-stu-id="704ac-139">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="704ac-140">确保配置文件是 DefaultXRSDKConfigurationProfile</span><span class="sxs-lookup"><span data-stu-id="704ac-140">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="704ac-141">导航到“编辑”>“项目设置，XR 插件管理”，确保已启用 Windows Mixed Reality 。</span><span class="sxs-lookup"><span data-stu-id="704ac-141">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="704ac-142">在 Visual Studio 中生成和部署</span><span class="sxs-lookup"><span data-stu-id="704ac-142">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="704ac-143">如果使用的是 Unity 2019.3.x，请在 Visual Studio 中选择 ARM64（而不是 ARM）作为生成体系结构 。</span><span class="sxs-lookup"><span data-stu-id="704ac-143">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="704ac-144">使用 Unity 2019.3.x 中的默认 Unity 设置时，如果由于 Unity bug 而选择了 ARM，则 Unity 应用将不会部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="704ac-144">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span>
>
> <span data-ttu-id="704ac-145">如果需要使用 ARM 体系结构，请导航到“编辑”>“项目设置，播放器”，然后在“其他设置”菜单下，禁用“图形作业”  。</span><span class="sxs-lookup"><span data-stu-id="704ac-145">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="704ac-146">如果禁用“图形作业”，那么应用将能够对 Unity 2019.3.x 使用 ARM 生成体系结构进行部署，但建议使用 ARM64。</span><span class="sxs-lookup"><span data-stu-id="704ac-146">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>
>
> <span data-ttu-id="704ac-147">此问题已在 Unity 2019.4 和 Unity 2020.3 中解决。</span><span class="sxs-lookup"><span data-stu-id="704ac-147">This issue was fixed in Unity 2019.4 and Unity 2020.3.</span></span>

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a><span data-ttu-id="704ac-148">构建 MRTK 并将其部署到 WMR 耳机 (独立) </span><span class="sxs-lookup"><span data-stu-id="704ac-148">Building and deploying MRTK to WMR Headsets (Standalone)</span></span>

<span data-ttu-id="704ac-149">可在 WMR 耳机上使用独立的 MRTK 版本。</span><span class="sxs-lookup"><span data-stu-id="704ac-149">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="704ac-150">对于适合 WMR 头戴显示设备的独立版本，需额外执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="704ac-150">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="704ac-151">Unity 的 XR SDK 也支持独立版本中的原生 WMR，但它不需要 SteamVR 或 WMR 插件。</span><span class="sxs-lookup"><span data-stu-id="704ac-151">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="704ac-152">需要对 Unity 的旧版 XR 执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="704ac-152">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="704ac-153">安装 [Steam](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="704ac-153">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="704ac-154">安装 [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="704ac-154">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="704ac-155">安装 [WMR 插件](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="704ac-155">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="704ac-156">如何使用 WMR 插件</span><span class="sxs-lookup"><span data-stu-id="704ac-156">How to use WMR plugin</span></span>

1. <span data-ttu-id="704ac-157">打开 Steam 并搜索 Windows Mixed Reality 插件</span><span class="sxs-lookup"><span data-stu-id="704ac-157">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="704ac-158">在启动 WMR 插件之前，请确保 SteamVR 已关闭。</span><span class="sxs-lookup"><span data-stu-id="704ac-158">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="704ac-159">启动 WMR 插件时会一并启动 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="704ac-159">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="704ac-160">确保 WMR 头戴显示设备已接通电源。</span><span class="sxs-lookup"><span data-stu-id="704ac-160">Make sure the WMR headset is plugged in.</span></span>

    ![WMR 插件搜索](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="704ac-162">为 SteamVR 的 Windows Mixed Reality 插件选择“启动”。</span><span class="sxs-lookup"><span data-stu-id="704ac-162">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![WMR 插件](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="704ac-164">这会启动 SteamVR 和 WMR 插件，并对 WMR 头戴显示设备显示新的跟踪状态窗口。</span><span class="sxs-lookup"><span data-stu-id="704ac-164">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="704ac-165">有关详细信息，请访问 [Windows Mixed Reality Steam 文档](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span><span class="sxs-lookup"><span data-stu-id="704ac-165">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![WMR 启动外观](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="704ac-167">在 Unity 中，在 MRTK 屏幕打开的情况下导航到“文件”>“生成设置”</span><span class="sxs-lookup"><span data-stu-id="704ac-167">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="704ac-168">生成场景</span><span class="sxs-lookup"><span data-stu-id="704ac-168">Build the scene</span></span>
    - <span data-ttu-id="704ac-169">选择“添加开放式场景”</span><span class="sxs-lookup"><span data-stu-id="704ac-169">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="704ac-170">确保该平台是独立平台</span><span class="sxs-lookup"><span data-stu-id="704ac-170">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="704ac-171">选择“生成”</span><span class="sxs-lookup"><span data-stu-id="704ac-171">Select **Build**</span></span>
    - <span data-ttu-id="704ac-172">在文件资源管理器中为新的生成项选择位置</span><span class="sxs-lookup"><span data-stu-id="704ac-172">Choose the location for the new build in File Explorer</span></span>

    ![适合独立版本的生成设置](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="704ac-174">这将创建一个新的 Unity 可执行文件。若要启用应用，请在文件资源管理器中选择该 Unity 可执行文件。</span><span class="sxs-lookup"><span data-stu-id="704ac-174">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![文件资源管理器 Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="704ac-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="704ac-176">See also</span></span>

- [<span data-ttu-id="704ac-177">Android 和 iOS 支持</span><span class="sxs-lookup"><span data-stu-id="704ac-177">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="704ac-178">Leap Motion 支持</span><span class="sxs-lookup"><span data-stu-id="704ac-178">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="704ac-179">检测平台功能</span><span class="sxs-lookup"><span data-stu-id="704ac-179">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)
