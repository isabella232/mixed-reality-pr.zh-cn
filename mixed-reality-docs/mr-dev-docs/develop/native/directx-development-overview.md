---
title: 原生开发概述
description: 直接使用 Windows Mixed Reality Api 构建基于 DirectX 的混合现实引擎。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX，全息呈现，本机，本机应用，WinRT，WinRT 应用，平台 Api，自定义引擎，中间件
ms.openlocfilehash: fb51dfe15de26b80db255f0daca69e913f9ad35c
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903120"
---
# <a name="native-development-overview"></a>原生开发概述

![本机横幅徽标](../images/native_logo_banner.png)

3D 引擎（如 [Unity](../unity/unity-development-overview.md) 或 [Unreal](../unreal/unreal-development-overview.md) ）并不是唯一的混合现实开发途径。 还可以通过使用 DirectX 11 或 DirectX 12 的 Windows 混合现实 Api 直接编写代码来创建混合现实应用。 通过直接利用该平台，你实质上是构建自己的中间件或框架。 

> [!IMPORTANT]
> 如果你有想要维护的现有 WinRT 项目，请转到我们的主 [winrt 文档](creating-a-holographic-directx-project.md)。 

## <a name="development-checkpoints"></a>开发检查点

使用以下检查点，将 Unity 游戏和应用程序带入混合现实的世界。

### <a name="1-getting-started"></a>1.入门

Windows Mixed Reality 支持 [两种类型的应用](../../design/app-views.md)：
* **混合现实应用程序** (UWP 或 Win32) ，这些应用程序使用 [HolographicSpace API](getting-a-holographicspace.md) 或 [OpenXR api](openxr.md) 将 [沉浸式视图](../../design/app-views.md) 呈现给填充耳机显示的用户
*  (UWP) 的 **2d 应用** ，使用 DIRECTX、XAML 或其他框架在 Windows Mixed Reality 主页上呈现清单的 [2d 视图](../../design/app-views.md#2d-views)

[2d 视图和沉浸式视图](../../design/app-views.md)的 DirectX 开发之间的差异主要涉及全息呈现和空间输入。 UWP 应用程序的 [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) 或 Win32 应用程序的 HWND 是必需的，并且保持基本相同。 适用于应用程序的 WinRT Api 也是如此。 但您必须使用这些 Api 的不同子集才能利用全息功能。 例如，存在和帧的存在由系统为全息应用程序管理，以便启用姿势预测帧循环。

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2.核心构建基块

Windows Mixed Reality 应用程序使用以下 Api 为 HoloLens 和其他沉浸式耳机构建 [混合现实](../../discover/mixed-reality.md) 体验：

|  特性  |  功能  |
| --- | --- |
| [凝视](../../design/gaze-and-commit.md) | 让用户通过查看全息影像来定位它们 |
| [手势](../../design/gaze-and-commit.md#composite-gestures) | 向你的应用添加空间操作 |
| [全息渲染](../platform-capabilities-and-apis/rendering.md) | 在世界各地的用户的精确位置绘制一个全息图 |
| [运动控制器](../../design/motion-controllers.md) | 让用户在混合现实环境中采取措施 |
| [空间映射](../../design/spatial-mapping.md) | 使用虚拟网格覆盖映射物理空间以标记环境边界 |
| [语音](../../design/voice-input.md) | 捕获用户的口语关键字、短语和听写 |
 
> [!NOTE]
> 可以在 OpenXR [路线图](openxr.md#roadmap) 文档中找到即将推出的和开发中的核心功能。

### <a name="3-deploying-and-testing"></a>3. 部署和测试

你可在桌面上的 HoloLens 2 或 Windows Mixed Reality 沉浸式头戴显示设备上使用 OpenXR 进行开发。  如果你无权访问耳机，则可以改用 [HoloLens 2 模拟器](../platform-capabilities-and-apis/using-the-hololens-emulator.md) 或 [Windows Mixed Reality 模拟器](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 。

## <a name="whats-next"></a>下一步操作

开发人员的工作一直在更新，特别是在学习新工具或 SDK 时。 以下部分将带你进入你已完成的初学者级别资料之外的其他领域，并在你遇到问题时提供有用的资源。 请注意，这些主题和资源不按任何顺序排列，因此请随意查看并探索！

### <a name="additional-resources"></a>其他资源

如果想要对 OpenXR 游戏进行调配，请查看以下链接：

* [OpenXR 最佳做法](openxr-best-practices.md)
* [OpenXR 性能](openxr-performance.md)
* [OpenXR 故障排除](openxr-troubleshooting.md)

## <a name="see-also"></a>另请参阅
* [应用模型](../../design/app-model.md)
* [应用视图](../../design/app-views.md)
