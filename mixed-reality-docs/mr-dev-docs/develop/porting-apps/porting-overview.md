---
title: 移植概述
description: 概述使现有应用程序成为混合现实的各种移植选项。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: 移植，unity，中间件，引擎，UWP，Win32
ms.openlocfilehash: 1ec03610dd26e9f75162795cbdded77a8e0189ce
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925832"
---
# <a name="porting-overview"></a>移植概述

当涉及到迁移或升级现有项目以满足混合现实的需要时，可以根据应用是使用 Unity 还是 Unreal 引擎、HoloLens (第一代) 还是 HoloLens 2 或 SteamVR 来进行。 此概述页面包含我们针对每个平台和设备的当前建议-请务必检查，因为这些过程始终会更改。

首先，根据我们的 [Unity](#unity) 和 [Unreal](#unreal) 建议设置项目目标，然后执行一个或多个移植方案：

- [HoloLens (第一代) 到 HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Windows Mixed Reality 头戴显示设备](#windows-mixed-reality-headsets)
- [SteamVR 应用](#steamvr-applications)
- [2D UWP 应用](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>推荐的项目目标

无论你是否将应用程序移植到另一台目标设备，都要使你的项目保持最新状态，这一点很重要。 有关我们当前的建议，请参阅下面列出的基于引擎的资源。

### <a name="unity"></a>Unity

我们当前对混合现实的 Unity 开发建议是 **使用旧 XR 包的 unity 2019 LTS**。 如果你的项目使用混合现实工具包，请仔细检查是否正在使用最新版本，即当前为 **MRTK 2.5**。

> [!CAUTION]
> 尽管此版本的 Unity 提供了 XR SDK，但 Azure 空间锚不与此安装程序兼容。 将使用适用于 Unity 的 Azure 空间定位包的未来版本更新此建议。 
> 
> * 如果不需要 Azure 空间锚，可以 [配置适用于 XR 的 Unity 项目](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) 并 [开始 MRTK 和 XR SDK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html)。
> 
> * 如果你当前使用的是项目中的 XR SDK，并且想要使用 Azure 空间锚，请卸载 XR SDK，并重新安装旧版 XR 包以恢复你的项目设置。


### <a name="unreal"></a>Unreal 

我们当前对混合现实的 Unreal 开发建议是 **Unreal 引擎 4.26**。 如果你的项目使用混合现实工具包 UX 工具，请确保使用最新版本，该版本目前为 **UXT 0.10**。

## <a name="porting-scenarios"></a>移植方案

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>HoloLens (第一代) Unity 应用到 HoloLens 2

如果你有一个现有的 HoloLens (第一代) Unity 应用程序，你想要将其移植到 HoloLens 2，请按照 [HoloLens 移植一文](../unity/mrtk-porting-guide.md)中的说明进行操作。

### <a name="windows-mixed-reality-headsets"></a>Windows Mixed Reality 头戴显示设备

如果为其他设备（如 Oculus Rift 或 HP 回音 G2）生成了内容，则需要重新定位特定于供应商的 VR Sdk 和可能的输入映射 Api。 可以在我们的 [沉浸式应用移植指南](porting-guides.md)中查找 Unity 和 Unreal 移植方案的相关信息。

### <a name="steamvr-applications"></a>SteamVR 应用程序

对于要为 Windows Mixed Reality 耳机更新的任何 SteamVR 体验，请参阅我们的 [SteamVR 更新指南](updating-your-steamvr-application-for-windows-mixed-reality.md)。

### <a name="2d-universal-windows-applications"></a>2D 通用 Windows 应用程序

如果你想要将现有的 2D UWP 应用程序移植到 Windows Mixed Reality 沉浸式耳机或 HoloLens，请遵循我们的 [移植 2D uwp apps For Windows Mixed reality](building-2d-apps.md) 一文中的说明。

