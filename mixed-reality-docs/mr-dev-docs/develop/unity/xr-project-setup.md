---
title: 设置 XR 配置
description: 随时了解适用于应用程序开发的最新 Unity XR HoloLens建议。
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit， mixedrealitytoolkit-unity， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， unity
ms.openlocfilehash: 72f17ec9fc74143a2ae6cc51e1ffed0c73d13ef04ef5c4004537be70d1daaaca
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202706"
---
# <a name="setting-up-your-xr-configuration"></a>设置 XR 配置

选择 Unity [版本后](choosing-unity-version.md)，下一步是选择用于生成混合现实应用的 XR 配置：

## <a name="choosing-an-xr-configuration"></a>选择 XR 配置

启动新的 Unity 项目时，可以选择各种 XR 配置：混合现实 **OpenXR** 插件 **、Windows XR** 插件和旧版 **内置 XR。**

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>使用 MRTK 设置项目

为混合现实设置 Unity 项目的最简单方法是使用混合现实 Toolkit (MRTK) 。  MRTK for Unity 是一个开源的跨平台开发工具包，旨在轻松生成令人惊叹的混合现实应用程序。

![MRTK](../../design/images/MRTK_UX_Hero.png)

MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。  使用 MRTK 版本 2，可以加快 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备以及许多其他 VR/AR 设备的应用程序开发。 该项目旨在减少进入障碍，使每个人都能够构建混合现实应用程序，并随着我们的发展为社区做出贡献。

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

若要详细了解混合现实Toolkit，请查看[MRTK 文档](/windows/mixed-reality/mrtk-unity)。

## <a name="manual-setup-without-mrtk"></a>不带 MRTK 的手动设置

虽然 Microsoft 和社区已创建开源工具，例如混合现实[Toolkit (MRTK) ，](/windows/mixed-reality/mrtk-unity)这些工具会自动为混合现实设置环境，但某些开发人员可能希望从头构建自己的体验。

[!INCLUDE[](includes/xr/manual-setup.md)]