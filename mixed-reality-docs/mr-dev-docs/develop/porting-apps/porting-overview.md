---
title: 移植概述
description: 概述用于将现有应用程序引入混合现实（适用于 HoloLens VR）的各种移植选项。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: 移植， unity， 中间件， 引擎， UWP， Win32
ms.openlocfilehash: 519dae088e689e0a6e617bf5e2b34f81cc2e265256c4844df7dd34e99172d536
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189417"
---
# <a name="porting-overview"></a>移植概述

在移植或升级混合现实的现有项目时，移植过程取决于应用是使用 Unity 还是 Unreal Engine 构建的，并且面向 HoloLens (第一代) 或 HoloLens 2 或 SteamVR。 此概述页包含我们针对每个平台和设备的当前建议 - 请务必返回查看，因为这些流程始终在变化。

首先，根据 [Unity](#unity) 和 [Unreal](#unreal) 建议设置项目目标，然后遵循一个或多个移植方案：

- [HoloLens (第一代) HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [沉浸式 VR 头戴显示设备](#immersive-vr-headsets)
- [2D UWP 应用](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>建议的项目目标

无论将应用移植到另一个目标设备，都保持项目最新状态非常重要。 请参阅下面列出的基于引擎的资源，了解我们当前的建议。

### <a name="unity"></a>Unity

有关 [建议的 Unity 和](../unity/choosing-unity-version.md) MRTK 版本最新指南，请参阅选择 Unity 版本页。

### <a name="unreal"></a>Unreal

有关 [建议的 Unreal](../unreal/unreal-project-setup.md) 和 MRTK 版本最新指南，请参阅设置 Unreal 项目页。

## <a name="porting-scenarios"></a>移植方案

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>HoloLens (第一代) Unity 应用HoloLens 2

如果已有要HoloLens (移植到 HoloLens 2 的) 第一代) Unity 应用程序，请按照我们的 HoloLens[移植一](./porting-hl1-hl2.md)文的说明进行操作。

### <a name="immersive-vr-headsets"></a>沉浸式 VR 头戴显示设备

如果为其他 VR 设备生成了内容，则需要重定任何供应商特定的 VR SDK 和可能的输入映射 API。 可以在沉浸式应用移植指南 中查找 Unity 和 Unreal 移植 [方案的信息](porting-guides.md)。

有关要针对头戴显示设备更新的 SteamVR Windows Mixed Reality，请参阅[我们的 SteamVR 更新指南](updating-your-steamvr-application-for-windows-mixed-reality.md)。

### <a name="2d-universal-windows-applications"></a>2D 通用Windows应用程序

如果要移植到 Windows Mixed Reality 沉浸式头戴显示设备或 HoloLens 的现有 2D UWP 应用，请按照移植[2D UWP](building-2d-apps.md)应用了解 Windows Mixed Reality 说明。