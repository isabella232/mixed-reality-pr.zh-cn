---
title: Unreal 开发概述
description: 通过我们特选的检查点历程，使用 Unreal Engine 4 开始针对 HoloLens 和 VR 的混合现实开发。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 流式处理, 远程处理, 混合现实, 开发, 入门, 功能, 新项目, 仿真器, 文档, 指南, 功能, 全息影像, 游戏开发, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, OpenXR
ms.openlocfilehash: eb9ec39d663dec2b5bf4c9177524449f31aaf554
ms.sourcegitcommit: e24715fffa815c24ca411fa93eed9576ae729337
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2021
ms.locfileid: "98247730"
---
# <a name="unreal-development-overview"></a>Unreal 开发概述

![Unreal 横幅徽标](../images/unreal_logo_banner.png)

开始使用<a href="https://docs.microsoft.com/windows/mixed-reality" target="_blank" title="混合现实文档">混合现实应用程序</a>是一个重大任务。 新概念、平台和前沿硬件看似都障碍重重。 但是，如果你是 Unreal 的开发人员，那么你很幸运。 Unreal Engine 4 具有对 <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title="Windows Mixed Reality 文档">Windows Mixed Reality</a> (VR) 和 <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="HoloLens 2 文档">HoloLens 2</a> (AR) 设备的完全支持。

[!INCLUDE[](includes/tabs-unreal-features.md)]

如果你不熟悉 Unreal 开发，请勿直接跳转。 浏览 Unreal <a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">教程系列</a>，并在 Unreal <a href="https://www.unrealengine.com/marketplace/store" target="_blank">市场</a>中查看资产。 还可以在混合现实<a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">论坛</a>中找到支持。 这些资源是指向当今的混合现实市场中的构建者和问题解决者的社区的链接。

> [!IMPORTANT]
> 如果你有一个现成的 Unreal 项目想要引入到沉浸式头戴显示设备（例如 Reverb G2）中，请查看我们的[移植指南](unreal-reverb-g2-controllers.md)。

## <a name="development-checkpoints"></a>开发检查点

使用以下检查点，将 Unreal 游戏和应用程序带入混合现实的世界。 如果你尚未浏览[设计全息影像示例应用程序](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)，建议下载它来熟悉混合现实 UX 的基本知识。

### <a name="1-getting-started"></a>1.入门

首先，需要安装用于 HoloLens 2 开发的工具。 接下来，阅读我们的教程系列，基本了解混合现实工具包、为混合现实应用正确配置的开发环境以及在 Unreal 中运行的 MRTK 项目。 从 Unreal 4.26 开始，还可以选择为 HoloLens 2 开发 OpenXR 应用。

|  Checkpoint  |  业务成效  |
| --- | --- |
| [安装最新工具](../install-the-tools.md) | 下载并安装最新版 Unreal Engine，并为你的项目设置混合现实 |
| [HoloLens 2 教程系列](tutorials/unreal-uxt-ch1.md) | 在 Unreal 中设置混合现实开发，使用 MRTK 构建首款应用，然后将该应用部署到 HoloLens 2 |
| （可选）在 Unreal 中开始使用 [OpenXR](../native/openxr.md) | 如果要在 Unreal 中构建 OpenXR 应用，则应禁用以下引擎插件：<ul><li>Windows Mixed Reality</li></ul><br>从 GitHub 下载以下插件并在项目中启用它们：<ul><li> [Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal)</li></ul><br>[下面](#supported-features)是 OpenXR 当前支持的功能的完整列表。|

### <a name="2-core-building-blocks"></a>2.核心构建基块

许多主要混合现实功能在教程系列中未涉及。 这些构建基块可以作为独立功能提供，也可以通过混合现实工具包提供。 你可能不需要一次全部使用它们，但建议你尽早进行使用。 深入了解下面列出的核心构建基块后，你将拥有一个工具箱，其中包含了各种你可以集成到混合现实项目中的功能。

[适用于 Unreal 的混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unreal)是一组设计用于在 Unreal 中加快开发速度的插件。 每个插件都包含用于设置沉浸式体验的组件、示例和文档。

* [适用于 Unreal 的 UX Tools](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools) 是第一个要发布的插件，目前仅在 HoloLens 2 上受支持。 此插件包括 C++ 代码、蓝图，以及用于输入模拟、手部交互、表面磁性等的常见 UX 功能的示例资产。

[!INCLUDE[](../includes/unreal-building-blocks.md)]

> [!NOTE]
> 有关更多详细信息，可以深入了解[适用于 Unreal 的 UX Tools GitHub](https://github.com/microsoft/MixedReality-UXTools-Unreal) 存储库。

### <a name="3-advanced-features"></a>3.高级功能

在混合现实应用程序中起作用的其他关键功能可用，无需任何额外的包或设置。 可以在安装或未安装 MRTK 的情况下将这些功能添加到 Unreal 项目中。 深入了解这些更高级功能后，你将可以生成更复杂的混合现实应用。

|  功能  |  功能  |
| --- | --- |
| [HoloLens 摄像头](unreal-hololens-camera.md) | 从在 HoloLens 设备上运行的应用捕获混合现实视觉内容和真实世界视觉内容 |
| [QR 码](unreal-qr-codes.md) | 使用坐标系统在每个 QR 码的真实世界位置将 QR 码呈现为全息影像 |
| [WinRT](unreal-winrt.md) | 使用可由 Unreal 的生成系统使用的 WinRT 代码创建一个单独的二进制文件 |

### <a name="4-streaming-and-deploying-to-a-device"></a>4.流式传输并部署到设备

如果你想要在 HoloLens 设备上测试仍处于开发阶段的应用程序，则可以使用 Unreal 编辑器或打包的 Windows 可执行文件[从电脑直接流式传输该应用程序](unreal-streaming.md)。

如果这是你第一次将 Unreal 应用部署到 HoloLens 2，则需要从 Epic Launcher [下载支持文件](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)。 安装这些文件后，即可从 [Unreal 编辑器](unreal-deploying.md)或[设备门户](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)进行部署。

### <a name="5-adding-services"></a>5.添加服务

在开发历程中的这个阶段，你可能希望添加服务或寻求商业部署方面的帮助。 将 [Azure 云服务](../mixed-reality-cloud-services.md) 与 Dynamics 365 功能集成可以在很大程度上提高项目的水平。 我们已编译了几个入门点，用于探索和扩展你的混合现实知识。

[!INCLUDE[](../includes/unreal-cloud-services-d365.md)]

## <a name="whats-next"></a>下一步操作

开发人员的工作一直在更新，特别是在学习新工具或 SDK 时。 以下部分将带你进入你已完成的初学者级别资料之外的其他领域，并在你遇到问题时提供有用的资源。 请注意，这些主题和资源不按任何顺序排列，因此请随意查看并探索！

### <a name="debugging"></a>调试

如果希望使用 Visual Studio 对在设备上运行的应用程序进行调试，请按照以下[说明](https://docs.microsoft.com/visualstudio/debugger/debug-installed-app-package#remote)操作。

### <a name="performance"></a>性能

混合现实开发附带依赖于平台的性能检查点。 HoloLens 2 应用必须以每秒 60 帧的速度运行，才能使全息影像稳定显示且快速响应。 幸运的是，我们提供了有关在 Unreal 应用程序中升级性能的[性能建议](performance-recommendations-for-unreal.md)。

## <a name="supported-features"></a>支持的功能

| HoloLens 2 功能 | 最早支持的 Unreal Engine 版本 | 在 OpenXR 中受支持 (4.26) |
| ----------- | ----------- | ----------- |
| ARM64 支持 | 4.23 | ✔️ |
| 从电脑进行流式传输 | 4.23 | ✔️ |
| 空间映射 | 4.23 | ✔️ |
| 手动和联合跟踪 | 4.23 | ✔️ |
| 眼动跟踪 | 4.23 | ✔️ |
| 语音输入 | 4.23 | ✔️ |
| 空间定位点 | 4.23 | ✔️ |
| 摄像头访问 | 4.23 |
| QR 码 | 4.23 | ✔️ |
| 空间音频 | 4.23 | ✔️ |
| Spectator Screen 支持流式传输 | 4.24 |
| 通过流式传输的平面 LSR | 4.24 |
| [示例应用](unreal-samples.md) | 4.24 | ✔️ |
| 移动多视图：性能达到 60 fps | 4.25 | ✔️ |
| 第三人称摄像机渲染 | 4.25 |
| 从打包的桌面应用进行流式传输 | 4.25.1 | ✔️ |
| 面向 HoloLens 2 的 Azure 空间定位点 (beta) | 4.25 |
| 混合现实 UX Tools 支持 | 4.25 | ✔️ |
| 开发人员文档和教程 | 4.25 | ✔️ |
| 系统键盘 | 4.26 | ✔️ |
| HoloLens Media Player 插件 | 4.26 | ✔️ |
| 适用于 iOS 和 Android 的 Azure 空间定位点（beta 版） | 4.26 |
| 具有 Microsoft 供应商特定 OpenXR 扩展的 Microsoft OpenXR 插件 | 4.26 | ✔️ |
| 从 Azure 流式传输到 HoloLens 2 | 4.26 | ✔️ |
| 适用于打包应用的 Windows 应用认证工具包合规性 | 4.26 | ✔️ |
| HP Reverb G2 手柄支持 | 4.26 | ✔️ |

> [!div class="nextstepaction"]
> [安装工具](../install-the-tools.md)

## <a name="see-also"></a>另请参阅
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">关于流式传输、部署到仿真器和设备的 Unreal 文档</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">移动设备的 Unreal 性能指南</a>
