---
title: MRTK 配置对话框
description: 在 Unity 项目中配置 MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，Unity
ms.openlocfilehash: ef326a4e4c9e34479cebacf3f3f575cd902ff24e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144837"
---
# <a name="mrtk-project-configuration-dialog"></a>MRTK 项目配置对话框

当 Unity 加载项目并且确定一个或多个配置选项需要开发人员关注时，将显示 "MRTK 配置" 对话框。

![稍后应用](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

若要应用更改，请单击 " **应用** " 按钮。 **稍后** 按钮将延迟更改，直到在将来重新加载项目。

> [!NOTE]
> 如果未选中一个或多个建议的设置，则配置对话框将重新出现。 若要防止此情况发生，请应用所需的选项，然后通过 **混合现实工具包**  >  **实用工具**  >  **配置 Unity 项目** 并单击 "**忽略**" 来重新启动对话框。 这会阻止配置对话框自动再次出现。

## <a name="common-settings"></a>通用设置

所有生成目标共享公用选项的集合。

![通用设置](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a>强制文本资产序列化和启用可见元文件

这些设置有助于简化使用 Unity 项目和源代码管理系统 (例如： Git) 。

### <a name="enable-vr-supported"></a>支持启用 VR

**Unity 2018**

在 **播放机设置**  >  **XR 设置** 中配置支持的虚拟现实和虚拟现实 SDK 选项。

### <a name="set-single-pass-instanced-rendering-path"></a>设置单一传递实例呈现路径

将 **播放机设置**  >  **XR 设置**  >  **立体声渲染模式** 配置为 **单一传递实例**。

### <a name="set-default-spatial-awareness-layer"></a>设置默认空间感知层

将空间感知注册为第31层，以实现 raycast 和物理学选项的简单一致的配置。

### <a name="audio-spatializer"></a>音频空间化程序

音频空间化程序是解锁空间音效和位置音频功能的组件，使混合现实体验真正沉浸式。

> [!NOTE]
> 将音频空间化程序设置为"无"将禁用位置音频功能。

#### <a name="common-spatializers"></a>常见空间化程序

- Microsoft Spatializer

Microsoft 提供了空间化程序，支持对硬件加速进行HoloLens 2。

此空间化程序通过 [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) 和 [GitHub 提供](https://github.com/microsoft/spatialaudio-unity)。

有关 Microsoft 空间化程序的详细信息，请参阅 [空间音效文档](/windows/mixed-reality/spatial-sound-in-unity)。

- MS HRTF 空间化程序

Microsoft Windows 空间化程序，由 Unity 作为 Windows Mixed Reality 和 Windows XR 平台包的一部分提供。

- 音频

来自 Google 的由 Unity 提供的跨平台空间化程序。

有关详细信息，请参阅 [Audio 文档](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) 站点。

## <a name="universal-windows-platform-settings"></a>通用 Windows 平台设置

![UWP 设置](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a>UWP 功能

为应用程序启用通用 Windows 平台功能。 这些功能使平台能够通知和请求启用特定功能的权限。

- 麦克风

  允许通过麦克风捕获声音。

- Internet 客户端

  支持访问 internet 上的资源。

- 空间感知

  启用对使用实际环境的支持。

- 眼睛

  **Unity 2019.3 和更高版本**

  启用对跟踪用户眼睛的支持。

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a>避免 Unity "PlayerSettings. graphicsJob" 崩溃

**Unity 2019.3 和更高版本**

在最新版本的 Unity 2019 中，当启用 "图形作业" 时，应用将在部署到 HoloLens 2 时崩溃。
默认情况下，在 Unity 中启用此设置-尽管存在此 bug (请参阅 [Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)) ，配置器将默认设置为 "false" 的图形作业 (因此允许部署到 HoloLens 2 的应用不会崩溃) 。

## <a name="android-settings"></a>Android 设置

支持 Android 设备上的 AR 应用程序的配置设置。

![Android 设置](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a>禁用多线程呈现

禁用 **播放机设置**  >  **其他设置**  >  Android 的 AR 支持所需的 **多线程呈现**。

### <a name="set-minimum-api-level"></a>设置最低 API 级别

设置 "**播放机设置**" "  >  **其他设置**" "  >  **最小 API 级别**" 的值，以强制执行 AR 应用程序的操作系统要求。

## <a name="ios-settings"></a>iOS 设置

支持 iOS 设备上的 AR 应用程序的配置设置。

![iOS 设置](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a>设置所需的 OS 版本

设置 "**播放机设置**" 的值 "  >  **其他设置**"  >  **定位最低 iOS 版本** 以强制执行 AR 应用程序的操作系统要求。

### <a name="set-required-architecture"></a>设置所需的体系结构

设置"播放器 **设置**  >  **""其他设置**  >  **体系结构"** 的值，以强制实施 AR 应用程序的平台要求。

### <a name="set-camera-usage-descriptions"></a>设置相机使用情况说明

设置"播放器 **设置**  >  **"的值"其他设置** 相机使用情况说明"，该值用于请求使用  >  设备摄像头的权限。