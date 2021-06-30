---
title: 部署到 HoloLens 和 WMR 头戴显示设备
description: 介绍生成应用并将其部署到各种设备中的文档。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、混合现实、开发、MRTK、Visual Studio
ms.openlocfilehash: 12384c3d3c0c2208d86a9a946580d0311f8a8955
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042298"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a><span data-ttu-id="2dc13-104">部署到 HoloLens 和 WMR 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="2dc13-104">Deploying to HoloLens and WMR headsets</span></span>

<span data-ttu-id="2dc13-105">有两种方法将使用 MRTK 构建的应用程序部署到 Windows 设备：Univeral Windows Platform (UWP) 和独立平台。</span><span class="sxs-lookup"><span data-stu-id="2dc13-105">There are two ways to deploy applications built with MRTK to your windows device, the Univeral Windows Platform (UWP) and the Standalone Platform.</span></span> <span data-ttu-id="2dc13-106">为 HoloLens 1 或 HoloLens 2的应用程序必须面向 UWP，而为 WMR 头戴显示设备构建的应用程序可能面向 UWP 或独立设备。</span><span class="sxs-lookup"><span data-stu-id="2dc13-106">Applications built for HoloLens 1 or HoloLens 2 must target UWP, while applications built for WMR headsets may target either UWP or Standalone.</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="2dc13-107">构建 MRTK 并部署到 HoloLens 1、HoloLens 2和 WMR 头戴显示设备 (UWP) </span><span class="sxs-lookup"><span data-stu-id="2dc13-107">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="2dc13-108">有关如何为 **HoloLens 1** 和 HoloLens 2  (UWP) 的说明，请参阅生成应用程序 [到设备](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device)。</span><span class="sxs-lookup"><span data-stu-id="2dc13-108">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="2dc13-109">这些步骤还允许部署到 **WMR 头戴显示设备**。</span><span class="sxs-lookup"><span data-stu-id="2dc13-109">These steps also allow you to deploy to **WMR headsets**.</span></span>

> [!NOTE]
> <span data-ttu-id="2dc13-110">在 Visual Studio 中将应用程序部署到设备时，Visual Studio配置方式略有不同，具体取决于设备。</span><span class="sxs-lookup"><span data-stu-id="2dc13-110">When deploying your application to your device in Visual Studio, you need to configure Visual Studio slightly differently depending on the device.</span></span> <span data-ttu-id="2dc13-111">配置如下</span><span class="sxs-lookup"><span data-stu-id="2dc13-111">The configurations are as follows</span></span>
>
>| <span data-ttu-id="2dc13-112">平台</span><span class="sxs-lookup"><span data-stu-id="2dc13-112">Platform</span></span> | <span data-ttu-id="2dc13-113">配置</span><span class="sxs-lookup"><span data-stu-id="2dc13-113">Configuration</span></span> | <span data-ttu-id="2dc13-114">体系结构</span><span class="sxs-lookup"><span data-stu-id="2dc13-114">Architecture</span></span> | <span data-ttu-id="2dc13-115">目标</span><span class="sxs-lookup"><span data-stu-id="2dc13-115">Target</span></span> |
|---|---|---|---|
| <span data-ttu-id="2dc13-116">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2dc13-116">HoloLens 2</span></span> | <span data-ttu-id="2dc13-117">Release 或 Master</span><span class="sxs-lookup"><span data-stu-id="2dc13-117">Release or Master</span></span> | <span data-ttu-id="2dc13-118">ARM64</span><span class="sxs-lookup"><span data-stu-id="2dc13-118">ARM64</span></span> | <span data-ttu-id="2dc13-119">设备</span><span class="sxs-lookup"><span data-stu-id="2dc13-119">Device</span></span> |
| <span data-ttu-id="2dc13-120">HoloLens 1</span><span class="sxs-lookup"><span data-stu-id="2dc13-120">HoloLens 1</span></span> | <span data-ttu-id="2dc13-121">Release 或 Master</span><span class="sxs-lookup"><span data-stu-id="2dc13-121">Release or Master</span></span> | <span data-ttu-id="2dc13-122">x86</span><span class="sxs-lookup"><span data-stu-id="2dc13-122">x86</span></span> | <span data-ttu-id="2dc13-123">设备</span><span class="sxs-lookup"><span data-stu-id="2dc13-123">Device</span></span> |
| <span data-ttu-id="2dc13-124">WMR 头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="2dc13-124">WMR Headsets</span></span> | <span data-ttu-id="2dc13-125">Release 或 Master</span><span class="sxs-lookup"><span data-stu-id="2dc13-125">Release or Master</span></span> | <span data-ttu-id="2dc13-126">X64</span><span class="sxs-lookup"><span data-stu-id="2dc13-126">x64</span></span> | <span data-ttu-id="2dc13-127">本地计算机</span><span class="sxs-lookup"><span data-stu-id="2dc13-127">Local Machine</span></span> |

<span data-ttu-id="2dc13-128">**提示：** 为 HoloLens 1、HoloLens 2 或 WMR 进行生成时，建议将生成设置"目标 SDK 版本"和"最低平台版本"设置为如下图所示：</span><span class="sxs-lookup"><span data-stu-id="2dc13-128">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![“生成”窗口](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="2dc13-130">其他设置可以不同（例如，随时都能在 Visual Studio 解决方案中更改生成配置/体系结构/生成类型和其他信息）。</span><span class="sxs-lookup"><span data-stu-id="2dc13-130">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="2dc13-131">确保“目标 SDK 版本”下拉列表包含“10.0.18362.0”选项 - 如果没有此选项，则需要安装[最新版的 Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。</span><span class="sxs-lookup"><span data-stu-id="2dc13-131">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20192020-and-hololens"></a><span data-ttu-id="2dc13-132">Unity 2019/2020 和 HoloLens</span><span class="sxs-lookup"><span data-stu-id="2dc13-132">Unity 2019/2020 and HoloLens</span></span>

<span data-ttu-id="2dc13-133">如果 HoloLens 应用在设备上显示为 2D 面板，请确保在部署 UWP 应用之前，已在 Unity 中配置以下设置：</span><span class="sxs-lookup"><span data-stu-id="2dc13-133">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity before deploying your UWP app:</span></span>

<span data-ttu-id="2dc13-134">如果使用旧版内置 XR 支持， (Unity 2019) ：</span><span class="sxs-lookup"><span data-stu-id="2dc13-134">If using the legacy built-in XR support (Unity 2019 only):</span></span>

1. <span data-ttu-id="2dc13-135">导航到“编辑”>“项目设置，播放器”</span><span class="sxs-lookup"><span data-stu-id="2dc13-135">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="2dc13-136">在 UWP 选项卡的“XR 设置”下，确保已启用“支持的虚拟现实”且已在 SDK 中添加 Windows Mixed Reality SDK  。</span><span class="sxs-lookup"><span data-stu-id="2dc13-136">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="2dc13-137">在 Visual Studio 中生成和部署</span><span class="sxs-lookup"><span data-stu-id="2dc13-137">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="2dc13-138">如果使用 OpenXR 或 Windows XR 插件：</span><span class="sxs-lookup"><span data-stu-id="2dc13-138">If using the OpenXR or Windows XR plugins:</span></span>

1. <span data-ttu-id="2dc13-139">按照在 [XRSDK 入门](../configuration/getting-started-with-mrtk-and-xrsdk.md)中找到的步骤操作</span><span class="sxs-lookup"><span data-stu-id="2dc13-139">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="2dc13-140">确保配置文件是 DefaultXRSDKConfigurationProfile</span><span class="sxs-lookup"><span data-stu-id="2dc13-140">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="2dc13-141">导航到“编辑”>“项目设置，XR 插件管理”，确保已启用 Windows Mixed Reality 。</span><span class="sxs-lookup"><span data-stu-id="2dc13-141">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="2dc13-142">在 Visual Studio 中生成和部署</span><span class="sxs-lookup"><span data-stu-id="2dc13-142">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="2dc13-143">如果使用的是 Unity 2019.3.x，请在 Visual Studio 中选择 ARM64（而不是 ARM）作为生成体系结构 。</span><span class="sxs-lookup"><span data-stu-id="2dc13-143">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="2dc13-144">使用 Unity 2019.3.x 中的默认 Unity 设置时，如果由于 Unity bug 而选择了 ARM，则 Unity 应用将不会部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="2dc13-144">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span>
>
> <span data-ttu-id="2dc13-145">如果需要使用 ARM 体系结构，请导航到“编辑”>“项目设置，播放器”，然后在“其他设置”菜单下，禁用“图形作业”  。</span><span class="sxs-lookup"><span data-stu-id="2dc13-145">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="2dc13-146">如果禁用“图形作业”，那么应用将能够对 Unity 2019.3.x 使用 ARM 生成体系结构进行部署，但建议使用 ARM64。</span><span class="sxs-lookup"><span data-stu-id="2dc13-146">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>
>
> <span data-ttu-id="2dc13-147">此问题在 Unity 2019.4 和 Unity 2020.3 中已修复。</span><span class="sxs-lookup"><span data-stu-id="2dc13-147">This issue was fixed in Unity 2019.4 and Unity 2020.3.</span></span>

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a><span data-ttu-id="2dc13-148">构建 MRTK 并部署到 WMR 头戴显示设备 (独立) </span><span class="sxs-lookup"><span data-stu-id="2dc13-148">Building and deploying MRTK to WMR Headsets (Standalone)</span></span>

<span data-ttu-id="2dc13-149">MRTK 的独立版本可用于 WMR 头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="2dc13-149">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="2dc13-150">对于适合 WMR 头戴显示设备的独立版本，需额外执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="2dc13-150">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="2dc13-151">Unity 的 XR SDK 也支持独立版本中的原生 WMR，但它不需要 SteamVR 或 WMR 插件。</span><span class="sxs-lookup"><span data-stu-id="2dc13-151">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="2dc13-152">需要对 Unity 的旧版 XR 执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="2dc13-152">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="2dc13-153">安装 [Steam](https://store.steampowered.com/about/)</span><span class="sxs-lookup"><span data-stu-id="2dc13-153">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="2dc13-154">安装 [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="2dc13-154">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="2dc13-155">安装 [WMR 插件](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span><span class="sxs-lookup"><span data-stu-id="2dc13-155">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="2dc13-156">如何使用 WMR 插件</span><span class="sxs-lookup"><span data-stu-id="2dc13-156">How to use WMR plugin</span></span>

1. <span data-ttu-id="2dc13-157">打开 Steam 并搜索 Windows Mixed Reality 插件</span><span class="sxs-lookup"><span data-stu-id="2dc13-157">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="2dc13-158">在启动 WMR 插件之前，请确保 SteamVR 已关闭。</span><span class="sxs-lookup"><span data-stu-id="2dc13-158">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="2dc13-159">启动 WMR 插件时会一并启动 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="2dc13-159">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="2dc13-160">确保 WMR 头戴显示设备已接通电源。</span><span class="sxs-lookup"><span data-stu-id="2dc13-160">Make sure the WMR headset is plugged in.</span></span>

    ![WMR 插件搜索](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="2dc13-162">为 SteamVR 的 Windows Mixed Reality 插件选择“启动”。</span><span class="sxs-lookup"><span data-stu-id="2dc13-162">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![WMR 插件](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="2dc13-164">这会启动 SteamVR 和 WMR 插件，并对 WMR 头戴显示设备显示新的跟踪状态窗口。</span><span class="sxs-lookup"><span data-stu-id="2dc13-164">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="2dc13-165">有关详细信息，请访问 [Windows Mixed Reality Steam 文档](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span><span class="sxs-lookup"><span data-stu-id="2dc13-165">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![WMR 启动外观](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="2dc13-167">在 Unity 中，在 MRTK 屏幕打开的情况下导航到“文件”>“生成设置”</span><span class="sxs-lookup"><span data-stu-id="2dc13-167">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="2dc13-168">生成场景</span><span class="sxs-lookup"><span data-stu-id="2dc13-168">Build the scene</span></span>
    - <span data-ttu-id="2dc13-169">选择“添加开放式场景”</span><span class="sxs-lookup"><span data-stu-id="2dc13-169">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="2dc13-170">确保该平台是独立平台</span><span class="sxs-lookup"><span data-stu-id="2dc13-170">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="2dc13-171">选择“生成”</span><span class="sxs-lookup"><span data-stu-id="2dc13-171">Select **Build**</span></span>
    - <span data-ttu-id="2dc13-172">在文件资源管理器中为新的生成项选择位置</span><span class="sxs-lookup"><span data-stu-id="2dc13-172">Choose the location for the new build in File Explorer</span></span>

    ![适合独立版本的生成设置](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="2dc13-174">这将创建一个新的 Unity 可执行文件。若要启用应用，请在文件资源管理器中选择该 Unity 可执行文件。</span><span class="sxs-lookup"><span data-stu-id="2dc13-174">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![文件资源管理器 Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="2dc13-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2dc13-176">See also</span></span>

- [<span data-ttu-id="2dc13-177">Android 和 iOS 支持</span><span class="sxs-lookup"><span data-stu-id="2dc13-177">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="2dc13-178">Leap Motion 支持</span><span class="sxs-lookup"><span data-stu-id="2dc13-178">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="2dc13-179">检测平台功能</span><span class="sxs-lookup"><span data-stu-id="2dc13-179">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)