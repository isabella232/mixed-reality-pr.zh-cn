---
title: BuildAndDeploy
description: 介绍生成应用并将其部署到各种设备中的文档。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, 混合现实, 开发, MRTK, Visual Studio, Android, IOS
ms.openlocfilehash: 6f014bbd1ffd5dc0214bc52e1d3d3861409f85f6
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550857"
---
# <a name="building-and-deploying-mrtk"></a>生成和部署 MRTK

若要在设备上将某应用作为独立应用来运行（对于 HoloLens,、Android、iOS 等），需要在 Unity 项目中执行生成和部署步骤。 生成和部署使用 MRTK 的应用就像生成和部署任何其他 Unity 应用一样。 不存在 MRTK 特定的说明。 请在下面查看详细步骤，了解如何生成和部署适合 HoloLens 的 Unity 应用。  在[发布版本](https://docs.unity3d.com/Manual/PublishingBuilds.html)中详细了解如何针对其他平台进行生成。

## <a name="building-and-deploying-mrtk-to-hololens-1-and-hololens-2-uwp"></a>生成 MRTK 并将其部署到 HoloLens 1 和 HoloLens 2 (UWP)

有关如何为 HoloLens 1 和 HoloLens 2 (UWP) 进行生成和部署的说明，可查看[生成应用程序并将其部署到设备上](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device)。

**提示：** 针对 WMR、HoloLens 1 或 HoloLens 2 进行生成时，建议生成设置“目标 SDK 版本”和“最低平台版本”设为如下图所示：

![“生成”窗口](../features/images/getting-started/BuildWindow.png)

其他设置可以不同（例如，随时都能在 Visual Studio 解决方案中更改生成配置/体系结构/生成类型和其他信息）。

确保“目标 SDK 版本”下拉列表包含“10.0.18362.0”选项 - 如果没有此选项，则需要安装[最新版的 Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。

### <a name="unity-20193-and-hololens"></a>Unity 2019.3 和 HoloLens

如果某个 HoloLens 应用在设备上显示为 2D 面板，请确保在部署 UWP 应用之前，已在 Unity 2019.3.x 中配置以下设置：

如果使用的是旧版 XR：

1. 导航到“编辑”>“项目设置，播放器”
1. 在 UWP 选项卡的“XR 设置”下，确保已启用“支持的虚拟现实”且已在 SDK 中添加 Windows Mixed Reality SDK  。
1. 在 Visual Studio 中生成和部署

如果使用的是 XR 插件：

1. 按照在 [XRSDK 入门](../configuration/getting-started-with-mrtk-and-xrsdk.md)中找到的步骤操作
1. 确保配置文件是 DefaultXRSDKConfigurationProfile
1. 导航到“编辑”>“项目设置，XR 插件管理”，确保已启用 Windows Mixed Reality 。
1. 在 Visual Studio 中生成和部署

>[!IMPORTANT]
> 如果使用的是 Unity 2019.3.x，请在 Visual Studio 中选择 ARM64（而不是 ARM）作为生成体系结构 。 使用 Unity 2019.3.x 中的默认 Unity 设置时，如果由于 Unity bug 而选择了 ARM，则 Unity 应用将不会部署到 HoloLens。 可在 [Unity 的问题跟踪器](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)上跟踪此问题。
>
> 如果需要使用 ARM 体系结构，请导航到“编辑”>“项目设置，播放器”，然后在“其他设置”菜单下，禁用“图形作业”  。 如果禁用“图形作业”，那么应用将能够对 Unity 2019.3.x 使用 ARM 生成体系结构进行部署，但建议使用 ARM64。

## <a name="building-and-deploying-mrtk-to-a-windows-mixed-reality-headset"></a>生成 MRTK 并将其部署到 Windows Mixed Reality 头戴显示设备

Windows Mixed Reality (WMR) 头戴显示设备可用于通用 Windows 平台 (UWP) 和独立版本。  对于适合 WMR 头戴显示设备的独立版本，需额外执行下列步骤：

> [!NOTE]
> Unity 的 XR SDK 也支持独立版本中的原生 WMR，但它不需要 SteamVR 或 WMR 插件。 需要对 Unity 的旧版 XR 执行这些步骤。

1. 安装 [Steam](https://store.steampowered.com/about/)
1. 安装 [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)
1. 安装 [WMR 插件](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

### <a name="how-to-use-wmr-plugin"></a>如何使用 WMR 插件

1. 打开 Steam 并搜索 Windows Mixed Reality 插件
    - 在启动 WMR 插件之前，请确保 SteamVR 已关闭。 启动 WMR 插件时会一并启动 SteamVR。
    - 确保 WMR 头戴显示设备已接通电源。

    ![WMR 插件搜索](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. 为 SteamVR 的 Windows Mixed Reality 插件选择“启动”。

    ![WMR 插件](../features/images/build-deploy/WMR/WMRPlugin.png)

    - 这会启动 SteamVR 和 WMR 插件，并对 WMR 头戴显示设备显示新的跟踪状态窗口。
    - 有关详细信息，请访问 [Windows Mixed Reality Steam 文档](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)

        ![WMR 启动外观](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. 在 Unity 中，在 MRTK 屏幕打开的情况下导航到“文件”>“生成设置”

1. 生成场景
    - 选择“添加开放式场景”
    - 确保该平台是独立平台
    - 选择“生成”
    - 在文件资源管理器中为新的生成项选择位置

    ![适合独立版本的生成设置](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. 这将创建一个新的 Unity 可执行文件。若要启用应用，请在文件资源管理器中选择该 Unity 可执行文件。

    ![文件资源管理器 Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a>另请参阅

- [Android 和 iOS 支持](../features/cross-platform/using-ar-foundation.md)
- [Leap Motion 支持](../features/cross-platform/leap-motion-mrtk.md)
- [检测平台功能](../features/cross-platform/detecting-platform-capabilities.md)