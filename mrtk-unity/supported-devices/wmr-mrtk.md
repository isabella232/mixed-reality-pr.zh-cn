---
title: 部署到 HoloLens 和 WMR 头戴显示设备
description: 介绍生成应用并将其部署到各种设备中的文档。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，Visual Studio
ms.openlocfilehash: 622c7ca4b9c527630b5677fe377d1d3108bdfe08c9dc616bfd4d3256b83b9ab0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209463"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a>部署到 HoloLens 和 WMR 头戴显示设备

可以通过两种方式将用 MRTK 构建的应用程序部署到 windows 设备、通用 Windows 平台 (UWP) 和独立平台。 为 HoloLens 1 或 HoloLens 2 生成的应用程序必须以 uwp 为目标，而为 WMR 耳机构建的应用程序可能面向 uwp 或独立。

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a>构建 MRTK 并将其部署到 HoloLens 1、HoloLens 2 和 WMR 耳机 (UWP) 

有关如何生成和部署 **HoloLens 1** 和 **HoloLens 2** (UWP) 的说明，请参阅在 [设备上生成应用程序](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device)。 这些步骤还允许你部署到 **WMR 耳机**。

> [!NOTE]
> 在 Visual Studio 中将应用程序部署到设备时，需要根据设备配置 Visual Studio 略有不同。 配置如下所示
>
>| 平台 | 配置 | 体系结构 | 目标 |
|---|---|---|---|
| HoloLens 2 | Release 或 Master | ARM64 | 设备 |
| HoloLens 1 | Release 或 Master | x86 | 设备 |
| WMR 耳机 | Release 或 Master | X64 | 本地计算机 |

**提示：** 为 HoloLens 1、HoloLens 2 或 WMR 进行生成时，建议生成设置 "目标 SDK 版本" 和 "最低平台版本" 与下图中所示类似：

![“生成”窗口](../features/images/getting-started/BuildWindow.png)

其他设置可以不同（例如，随时都能在 Visual Studio 解决方案中更改生成配置/体系结构/生成类型和其他信息）。

确保“目标 SDK 版本”下拉列表包含“10.0.18362.0”选项 - 如果没有此选项，则需要安装[最新版的 Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。

### <a name="unity-20192020-and-hololens"></a>Unity 2019/2020 和 HoloLens

如果 HoloLens 应用在设备上显示为2d 面板，请确保在部署 UWP 应用之前已在 Unity 中配置以下设置：

如果使用旧的内置 XR 支持 (仅) Unity 2019：

1. 导航到“编辑”>“项目设置，播放器”
1. 在 UWP 选项卡的“XR 设置”下，确保已启用“支持的虚拟现实”且已在 SDK 中添加 Windows Mixed Reality SDK  。
1. 在 Visual Studio 中生成和部署

如果使用的是 OpenXR 或 Windows XR 插件：

1. 按照在 [XRSDK 入门](../configuration/getting-started-with-mrtk-and-xrsdk.md)中找到的步骤操作
1. 确保配置文件是 DefaultXRSDKConfigurationProfile
1. 导航到“编辑”>“项目设置，XR 插件管理”，确保已启用 Windows Mixed Reality 。
1. 在 Visual Studio 中生成和部署

>[!IMPORTANT]
> 如果使用的是 Unity 2019.3.x，请在 Visual Studio 中选择 ARM64（而不是 ARM）作为生成体系结构 。 使用 Unity 2019.3.x 中的默认 Unity 设置时，如果由于 Unity bug 而选择了 ARM，则 Unity 应用将不会部署到 HoloLens。
>
> 如果需要使用 ARM 体系结构，请导航到“编辑”>“项目设置，播放器”，然后在“其他设置”菜单下，禁用“图形作业”  。 如果禁用“图形作业”，那么应用将能够对 Unity 2019.3.x 使用 ARM 生成体系结构进行部署，但建议使用 ARM64。
>
> 此问题已在 Unity 2019.4 和 Unity 2020.3 中解决。

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a>构建 MRTK 并将其部署到 WMR 耳机 (独立) 

可在 WMR 耳机上使用独立的 MRTK 版本。 对于适合 WMR 头戴显示设备的独立版本，需额外执行下列步骤：

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

- [Android 和 iOS 支持](using-ar-foundation.md)
- [Leap Motion 支持](leap-motion-mrtk.md)
- [检测平台功能](detecting-platform-capabilities.md)
