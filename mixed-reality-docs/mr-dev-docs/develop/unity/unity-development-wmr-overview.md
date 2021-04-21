---
title: 针对 VR 的 Unity 开发
description: 开始在适合 VR 和 Windows Mixed Reality 沉浸式头戴显示设备的 Unity 中构建混合现实应用。
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合现实, 开发, 入门, 新项目, 移植, 功能, 相机, 模拟, 仿真, 文档, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 什么是虚拟现实, 什么是增强现实, MRTK, 混合现实工具包, 语音输入, 可定位相机, 仿真器, Azure, 教程
ms.openlocfilehash: 50300ff08dd06c5fc250bc93979d537e10b38044
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528712"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a>针对 VR 和 Windows Mixed Reality 的 Unity 开发

![Unity 横幅徽标](../images/unity_logo_banner.png)

如果你尚不熟悉 Unity，我们建议你先在 Unity Learn 平台上浏览初学者级别[教程](https://unity3d.com/learn/tutorials)，然后再继续操作。 还有一个好主意是访问 [Unity 混合现实论坛](https://forum.unity3d.com/forums/hololens.102/)，与在线社区一起构建混合现实应用。 你永远都不知道你可能会在未知领域发现什么样的绝佳资产或解决方案。 准备好开始使用 MRTK 时，请前往下面的开发检查点！

> [!IMPORTANT]
> 如果你当前有一个想要引入到 Windows Mixed Reality 沉浸式头戴显示设备的 Unity 项目，请查看[移植指南](../porting-apps/porting-overview.md)。 

## <a name="development-checkpoints"></a>开发检查点

使用以下检查点，将 Unity 游戏和应用程序带入混合现实的世界。 

### <a name="1-getting-started"></a>1.入门

对于 Windows Mixed Reality 和 VR 开发，有少量的 Unity 设置需要你手动进行更改。 这些设置分为两个类别：按项目设置和按场景设置。 本部分结束时，你将获得工具和项目设置来开始创建自己的应用！

|  Checkpoint  |  业务成效  |
| --- | --- |
| [安装最新工具](../install-the-tools.md) | 下载并安装最新 Unity 包，并为混合现实设置你的项目 |
| [针对 WMR 配置项目](windows-xr-plugin.md) | 了解如何构建在全息和 VR 显示设备上呈现数字内容的应用程序 |

> [!IMPORTANT]
> 若要详细了解如何设置项目，请查看我们的 Unity 项目[配置指南](choosing-unity-version.md)。

### <a name="2-core-building-blocks"></a>2.核心构建基块

启动新的沉浸式项目后，你需要一些基本的构建基块来开发沉浸式应用。 混合现实应用程序的所有核心构建基块的公开方式与其他 Unity API 一致。 你可能不需要一次全部使用它们，但建议你尽早进行使用。 深入了解下面列出的核心构建基块后，你将拥有一个工具箱，其中包含了你可集成到 VR 项目中的各种功能。

|  功能  |  功能  |
| --- | --- |
| [摄像头](../unity/camera-in-unity.md) | 全面优化混合现实应用中的视觉质量和全息影像稳定性 |
| [世界锁定和空间定位点](spatial-anchors-in-unity.md) | 解决稳定性问题、相机调整并集成稳定的坐标系解决方案 || [运动控制器](../unity/motion-controllers-in-unity.md) | 向混合现实应用添加空间操作 |
| [笔势](../unity/gestures-in-unity.md) | 在混合现实体验中将手势作为输入内容 |
| [空间音效](../unity/spatial-sound-in-unity.md) | 使用沉浸式 3D 音频增强应用 |
| [Text](../unity/text-in-unity.md) | 获得清晰的高质量文本，其具有可管理的大小和质量渲染 |
| [语音输入](../unity/voice-input-in-unity.md) | 捕获用户的口语关键字、短语和听写|

### <a name="3-advanced-features"></a>3.高级功能

在沉浸式应用程序中起作用的其他关键功能可通过 Unity API 获得，无需任何额外的包或设置。 深入了解 Unity 提供的更高级功能后，你将能够生成更深层、更复杂的 VR 应用。

|  功能  |  功能  |
| --- | --- |
| [失跟](tracking-loss-in-unity.md) | 处理设备无法在应用程序世界空间中定位自己的情况 |
| [键盘输入](keyboard-input-in-unity.md) | 在应用中获取来自现实世界和混合现实键盘的输入 |

### <a name="4-deploying-to-a-device-or-emulator"></a>4.部署到设备或仿真器

准备好对全息 Unity 项目进行测试以后，下一步是导出和构建 Unity Visual Studio 解决方案。 有了该 VS 解决方案后，即可在真实的或模拟的设备运行应用程序。 本部分结束后，你将能够在适合你的开发需求的设备或仿真器上部署应用程序。

* [Windows Mixed Reality 沉浸式头戴显示设备](../platform-capabilities-and-apis/using-visual-studio.md)
* [Windows Mixed Reality 沉浸式头戴显示设备模拟器](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a>下一步操作

开发人员的工作一直在更新，特别是在学习新工具或 SDK 时。 以下部分将带你进入你已完成的初学者级别资料之外的其他领域，并在你遇到问题时提供有用的资源。 请注意，这些主题和资源不按任何顺序排列，因此请随意查看并探索！

### <a name="porting"></a>移植

如果你当前有想要移植的应用，那么接下来请查看以下文章：

* [将 VR 应用移植到 Windows Mixed Reality](../porting-apps/porting-guides.md?tabs=project)
* [更新适用于 Windows Mixed Reality 的 SteamVR 应用](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="additional-resources"></a>其他资源

在你自己进入混合现实世界之前，建议先阅读下面的额外文档。 

* [VR 发烧友指南](/windows/mixed-reality/enthusiast-guide/vr-journey)
* [Unity Asset Store](https://assetstore.unity.com)

## <a name="see-also"></a>请参阅 

* [建议用于 Unity 的设置](recommended-settings-for-unity.md)
* [针对 Unity 的性能建议](performance-recommendations-for-unity.md)
* [导出和构建 Unity Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [使用 Unity 和 Visual Studio 的最佳做法](best-practices-for-working-with-unity-and-visual-studio.md)