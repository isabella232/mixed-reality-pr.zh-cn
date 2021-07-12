---
title: 设置 XR 配置
description: 了解有关 HoloLens 应用程序开发的最新 Unity XR 配置建议。
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit，mixedrealitytoolkit，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，unity
ms.openlocfilehash: d2904b9ea4771286b7091a8d5b7c599fcbd1244a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603703"
---
# <a name="setting-up-your-xr-configuration"></a>设置 XR 配置

[选择 Unity 版本](choosing-unity-version.md)后，下一步是选择用于构建混合现实应用的 XR 配置：

## <a name="choosing-an-xr-configuration"></a>选择 XR 配置

启动新的 Unity 项目时，可以选择多个 XR 配置：**混合现实 OpenXR 插件**、 **Windows XR 插件** 和 **旧内置 XR**。

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>用 MRTK 设置项目

为混合现实设置 Unity 项目的最简单方法是将混合现实 Toolkit (MRTK) 。  MRTK for Unity 是一个开源的跨平台开发工具包，旨在简化混合现实应用程序的构建。

![MRTK](../../design/images/MRTK_UX_Hero.png)

MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。  在 MRTK 版本2中，你可以加快应用程序开发 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 耳机以及许多其他的 VR/AR 设备。 该项目旨在减少进入障碍，使每个人都可以构建混合现实应用程序，并在我们的所有增长时向社区提供反馈。

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

若要了解有关混合现实 Toolkit 的详细信息，请参阅[MRTK 文档](/windows/mixed-reality/mrtk-unity)。

## <a name="manual-setup-without-mrtk"></a>无 MRTK 的手动设置

尽管 Microsoft 和社区创建了开源工具，例如[混合现实 Toolkit (MRTK) ](/windows/mixed-reality/mrtk-unity)自动为混合现实设置你的环境，但某些开发人员可能希望从头开始构建自己的体验。

[!INCLUDE[](includes/xr/manual-setup.md)]