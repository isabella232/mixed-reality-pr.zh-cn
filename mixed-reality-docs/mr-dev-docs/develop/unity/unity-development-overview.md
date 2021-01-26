---
title: 针对 HoloLens 的 Unity 开发
description: 通过我们精选的检查点旅程开始在 Unity 和 HoloLens 中构建混合现实应用。
author: hferrone
ms.author: kurtie
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合现实, 开发, 入门, 新项目, 移植, 功能, 相机, 模拟, 仿真, 文档, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 什么是虚拟现实, 什么是增强现实, MRTK, 混合现实工具包, 空间映射, 语音输入, 可定位相机, 仿真器, Azure, 教程
ms.openlocfilehash: fc444f4d40d8bc013253869fe77ddd563e889d85
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583008"
---
# <a name="unity-development-for-hololens"></a>针对 HoloLens 的 Unity 开发

![Unity 横幅徽标](../images/unity_logo_banner.png)

在 [Unity](https://unity.com) 中生成 HoloLens [混合现实应用](../../design/app-views.md)的最快途径是使用混合现实工具包。 如果你尚不熟悉 Unity，我们建议你先在 Unity Learn 平台上浏览初学者级别[教程](https://unity3d.com/learn/tutorials)，然后再继续操作。 访问综合性的 [Asset Store](https://www.assetstore.unity3d.com/) 和 [Unity 混合现实论坛](https://forum.unity3d.com/forums/hololens.102/)，与在线社区一起生成混合现实应用程序也是一个好主意。 你永远都不知道你可能会在未知领域发现什么样的绝佳资产或解决方案。 准备好开始使用 MRTK 时，请前往下面的开发检查点！

> [!IMPORTANT]
> 如果你有一个想要引入到 HoloLens 2 的现有 Unity 项目，请查看 **[移植指南](../porting-apps/porting-overview.md)** 。 我们有指南针对正在使用 HTK、MRTK v1 或 SteamVR 的项目。

## <a name="development-checkpoints"></a>开发检查点

使用以下检查点，将 Unity 游戏和应用程序带入混合现实的世界。 如果你尚未浏览[设计全息影像示例应用程序](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)，我们建议下载并使用它来熟悉混合现实 UX 的基本知识。

### <a name="1-getting-started"></a>1.入门

若要在 Unity 中进行开发，最简单的方法是使用混合现实工具包。 MRTK 将帮助你自动为混合现实设置项目，并提供一组功能以加速开发过程。 本部分结束时，你将对混合现实工具包有一个基本的了解、对混合现实应用有一个正确配置的开发环境以及一个你自己构建的、可在 Unity 中正常工作的 MRTK 项目。

|  Checkpoint  |  业务成效  |
| --- | --- |
| [什么是 MRTK？](mrtk-getting-started.md) | 通过熟悉混合现实工具包及其所提供的功能开始历程 |
| [安装最新工具](../install-the-tools.md) | 下载并安装最新 Unity 包，并为混合现实设置你的项目 |
| [HoloLens 2 教程系列](tutorials/mr-learning-base-01.md) | 深入研究 HoloLens 2 硬件的初学者级别 MRTK 教程 |

> [!IMPORTANT]
> 若要在不导入混合现实工具包的情况下创建新的 Unity 项目，需针对 Windows Mixed Reality 手动更改一小组 Unity 设置。 这些设置分为两个类别：按项目设置和按场景设置。 有关分步过程，请参阅我们的[配置指南](configure-unity-project.md)。

> [!NOTE]
> 在项目中设置 MRTK V2，标准的 Unity 游戏对象（例如相机）就会立即启动，为你带来坐定式体验。 可在[坐标系统](coordinate-systems-in-unity.md)页面上找到有关更改应用程序的体验范围的说明。

### <a name="2-core-building-blocks"></a>2.核心构建基块

混合现实应用程序的所有核心构建基块的公开方式与其他 Unity API 一致。 这些构建基块可以作为独立功能提供，也可以通过混合现实工具包提供。 你可能不需要一次全部使用它们，但建议你尽早进行使用。 深入了解下面列出的核心构建基块后，你将拥有一个工具箱，其中包含了各种你可以集成到混合现实项目中的功能（通过这些功能本身或通过 MRTK 实现）。

[!INCLUDE[](../includes/unity-building-blocks.md)]

### <a name="3-advanced-features"></a>3.高级功能

在混合现实应用程序中起作用的其他关键功能可通过 Unity API 获得，而无需任何额外的包或设置。 可以在安装或未安装 MRTK 的情况下将这些功能添加到 Unity 项目中。 深入了解 Unity 提供的更高级功能后，你将能够生成更深层、更复杂的混合现实应用。

|  功能  |  功能  |
| --- | --- |
| [共享体验](shared-experiences-in-unity.md) | 使用空间定位点共享，在空间中的固定点共同观看同一全息影像并与之交互 |
| [可定位相机](locatable-camera-in-unity.md) | 在混合现实应用程序中捕获照片和视频内容 |
| [焦点](focus-point-in-unity.md) | 向 HoloLens 提供有关如何最好地对当前显示的全息影像执行稳定化的提示 |
| [失跟](tracking-loss-in-unity.md) | 处理设备无法在应用程序世界空间中定位自己的情况 |
| [键盘输入](keyboard-input-in-unity.md) | 在应用中获取来自现实世界和混合现实键盘的输入 |

### <a name="4-deploying-to-a-device-or-emulator"></a>4.部署到设备或仿真器

准备好对全息 Unity 项目进行测试以后，下一步是导出和构建 Unity Visual Studio 解决方案。 有了该 VS 解决方案以后，即可使用下述三种方法之一在真实的或模拟的设备运行应用程序。 本部分结束后，你将能够在适合你的开发需求的任何设备或仿真器上部署应用程序。

* [HoloLens 或 Windows Mixed Reality 沉浸式头戴显示设备](../platform-capabilities-and-apis/using-visual-studio.md)
* [HoloLens 仿真器](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [Windows Mixed Reality 沉浸式头戴显示设备模拟器](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="5-adding-services"></a>5.添加服务

在开发历程中的这个阶段，你可能希望添加服务或寻求商业部署方面的帮助。 将 [Azure 云服务](../mixed-reality-cloud-services.md) 与 Dynamics 365 功能集成可以在很大程度上提高项目的水平。 我们已编译了几个入门点，用于探索和扩展你的混合现实知识。

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

我们还提供了一个[针对其他 Azure 服务的支持文档的完整列表](../mixed-reality-cloud-services.md#standalone-unity-services)，你可以自行将这些服务添加到 Unity 项目中。

## <a name="whats-next"></a>下一步操作

开发人员的工作一直在更新，特别是在学习新工具或 SDK 时。 以下部分将带你进入你已完成的初学者级别资料之外的其他领域，并在你遇到问题时提供有用的资源。 请注意，这些主题和资源不按任何顺序排列，因此请随意查看并探索！

### <a name="porting"></a>移植

如果你当前有想要移植的应用，那么接下来请查看以下文章：

* [HoloToolkit/MRTK 到 MRTK v2](../porting-apps/porting-hl1-hl2.md)
* [沉浸式应用移植指南](../porting-apps/porting-guides.md)
* [输入移植指南](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a>教程

如果你希望将特定的混合现实功能添加到应用程序，我们提供了一些精选的教程，可以指导你从头到尾完成整个过程。 下面列出了最受欢迎的 HoloLens 2 和 HoloLens（第一代）内容，但你可以通过访问教程概述查找整个集合。

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a>其他资源

在你自己进入混合现实世界之前，我们建议你先阅读下面列出的与 MRTK 相关的文档。 这些文章详细介绍了 MRTK 是如何工作的，是非常好的起始点，它们将使你深入了解如何使应用更高效。

|  主题  |  说明  |
| --- | --- |
| [MRTK 体系结构概述](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/Overview.html) | 更深入地了解 MRTK SDK 在项目中的工作方式 |
| [设置和性能](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) | 分析你的应用、更新 Unity 设置并实现最佳的全息影像稳定性能 |
| [MRTK + XR 入门](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html) | 转到 Unity 提供的替代 XR 管道 |

### <a name="unity-resources"></a>Unity 资源

除了 docs.microsoft.com 上提供的此文档，Unity 还配置了适用于 Windows Mixed Reality 功能和 Unity 编辑器的文档。 Unity 提供的文档包括两个单独的部分。

|  资源  |  说明  |
| --- | --- |
| [脚本引用](https://docs.unity3d.com/ScriptReference/) | 本文档的此部分包含 Unity 提供的脚本编写 API 的详细信息，并可在 Unity 编辑器中通过单击“帮助”>“脚本编写参考”在线进行访问 |
| [手动](https://docs.unity3d.com/Manual/index.html) | 本手册旨在帮助你了解如何使用 Unity（从基本方法到高级方法），并可在 Unity 编辑器中通过单击“帮助”>“手册”在线进行访问 |

> [!div class="nextstepaction"]
> [探索 MRTK](mrtk-getting-started.md)

## <a name="have-feedback"></a>想提供反馈？

你可在 [Unity 论坛](https://aka.ms/unityforums)上找到我们，标记 Microsoft 和下列标记的组合来帮助我们了解你要就哪种插件提供反馈：

* HoloLens 2 
* Windows Mixed Reality
* OpenXR
* XRSDK
* 旧版 XR 

## <a name="see-also"></a>另请参阅

* [混合现实工具包 v2](mrtk-getting-started.md)
* [MR 基础知识 100：Unity 入门](tutorials/holograms-100.md)
* [建议用于 Unity 的设置](recommended-settings-for-unity.md)
* [针对 Unity 的性能建议](performance-recommendations-for-unity.md)
* [导出和构建 Unity Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [将 Windows 命名空间与 Unity 应用配合用于 HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [使用 Unity 和 Visual Studio 的最佳做法](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity 播放模式](unity-play-mode.md)
* [移植指南](../porting-apps/porting-guides.md)