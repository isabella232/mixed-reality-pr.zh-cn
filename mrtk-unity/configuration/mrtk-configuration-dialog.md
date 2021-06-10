---
title: MRTK 配置对话框
description: 在 Unity 项目中配置 MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，Unity
ms.openlocfilehash: fd05f7f3b579522a1225e11b0411b255a43e1e3f
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345090"
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

### <a name="audio-spatializer"></a>音频 spatializer

音频 spatializers 是用于解锁空间声音和位置音频功能的组件，使混合现实体验真正成为沉浸式体验。

> [!NOTE]
> 将音频 spatializer 设置为 "无" 将禁用位置音频特征。

#### <a name="common-spatializers"></a>常见 spatializers

- Microsoft Spatializer

Microsoft 提供的 spatializer 支持在 HoloLens 2 上利用硬件加速。

此 spatializer 通过 [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) 和 [GitHub](https://github.com/microsoft/spatialaudio-unity)提供。

有关 Microsoft Spatializer 的更多详细信息，请参阅 [空间音效文档](/windows/mixed-reality/spatial-sound-in-unity)。

- MS HRTF Spatializer

由 Unity 作为 Windows Mixed Reality 和 Windows XR Platform 包的一部分提供的 Microsoft Windows spatializer。

- Resonance 音频

由 Unity 提供的来自 Google 的跨平台 spatializer。

有关详细信息，请参阅 [Resonance 音频文档](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) 网站。

## <a name="universal-windows-platform-settings"></a>通用 Windows 平台设置

![UWP 设置](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a>UWP 功能

为通用 Windows 平台应用程序启用特定应用程序功能。 这些功能使平台能够通知并请求启用特定功能的权限。

- 麦克风

  通过麦克风启用捕获声音。

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

设置 "**播放机设置**"  >  **其他设置**  >  **结构** 的值，以强制执行 AR 应用程序的平台要求。

### <a name="set-camera-usage-descriptions"></a>设置相机使用说明

设置 **播放机设置** 的值  >  **其他设置**  >  **相机使用说明**，用于请求使用设备相机的权限。