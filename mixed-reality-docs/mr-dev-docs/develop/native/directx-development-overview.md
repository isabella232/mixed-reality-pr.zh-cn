---
title: 原生开发概述
description: 了解如何直接使用基于 DirectX 的混合现实Windows Mixed Reality引擎。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX， 全息渲染， 本机， 本机应用， WinRT， WinRT 应用， 平台 API， 自定义引擎， 中间件， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
ms.openlocfilehash: 056cb0c07002cb319e8acadf66e7f59650f5e00413440d6ad0103aa8ee936400
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200147"
---
# <a name="native-development-overview"></a>原生开发概述

![本机横幅徽标](../images/native_logo_banner.png)

Unity 或[Unreal](../unreal/unreal-development-overview.md)等 3D 引擎并不是唯一可打开的混合现实开发路径。 [](../unity/unity-development-overview.md) 还可使用 DirectX 11 或 DirectX 12 Windows Mixed Reality API 创建混合现实应用。 通过进入平台源，实质上是构建自己的中间件或框架。 

> [!IMPORTANT]
> 如果已有要维护的现有 WinRT 项目，请前往我们的主要 [WinRT 文档](creating-a-holographic-directx-project.md)。 

## <a name="development-checkpoints"></a>开发检查点

使用以下检查点，将 Unity 游戏和应用程序带入混合现实的世界。

### <a name="1-getting-started"></a>1.入门

Windows Mixed Reality支持[两种类型的应用](../../design/app-views.md)：
* UWP 或 Win32 **混合现实** 应用程序，这些应用程序使用 [HolographicSpace API](getting-a-holographicspace.md)或 [](../../design/app-views.md) [OpenXR API](openxr.md)呈现填充头戴显示设备显示的沉浸式视图
* **2D** (UWP) ，这些 UWP 应用使用 DirectX、XAML 或其他框架在主Windows Mixed Reality上呈现 [2D](../../design/app-views.md#2d-views)视图

[2D](../../design/app-views.md)视图和沉浸式视图的 DirectX 开发之间的差异主要涉及全息渲染和空间输入。 UWP 应用程序的 [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) 或 Win32 应用程序的 HWND 是必需的，并且大致保持不变。 适用于应用的 WinRT API 也是如此。 但是，必须使用这些 API 的不同子集来利用全息功能。 例如，全息应用程序的系统管理交换链和帧，以启用姿势预测帧循环。

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2.核心构建基块

Windows Mixed Reality应用程序使用以下 API 为设备和其他沉浸式[](../../discover/mixed-reality.md)头戴显示设备HoloLens混合现实体验：

|  特性  |  功能  |
| --- | --- |
| [凝视](../../design/gaze-and-commit.md) | 让用户通过查看全息影像来定位它们 |
| [手势](../../design/gaze-and-commit.md#composite-gestures) | 向应用添加空间操作 |
| [全息渲染](../platform-capabilities-and-apis/rendering.md) | 在用户周围的世界精确位置绘制全息影像 |
| [运动控制器](../../design/motion-controllers.md) | 让用户在混合现实环境中采取措施 |
| [空间映射](../../design/spatial-mapping.md) | 使用虚拟网格覆盖映射物理空间以标记环境边界 |
| [语音](../../design/voice-input.md) | 捕获用户的口语关键字、短语和听写 |
 
> [!NOTE]
> 可以在 OpenXR 路线图文档中找到即将推出的和开发 [中的核心](openxr.md#roadmap) 功能。

### <a name="3-deploying-and-testing"></a>3.部署和测试

可以在桌面上使用 OpenXR 在桌面或沉浸式头戴显示HoloLens 2 Windows Mixed Reality进行开发。  如果无法访问头戴显示设备，可以改为使用 HoloLens 2 Emulator[或](../platform-capabilities-and-apis/using-the-hololens-emulator.md)[Windows Mixed Reality 模拟器](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)。

## <a name="whats-next"></a>下一步操作

开发人员的工作一直在更新，特别是在学习新工具或 SDK 时。 以下部分将介绍你已完成的入门级材料以外的领域。 这些主题和资源不按任何顺序排序，因此可随意跳转和探索！

### <a name="additional-resources"></a>其他资源

如果希望提高 OpenXR 游戏的级别，请查看以下链接：

* [OpenXR 最佳做法](openxr-best-practices.md)
* [OpenXR 性能](openxr-performance.md)
* [OpenXR 故障排除](openxr-troubleshooting.md)

## <a name="see-also"></a>另请参阅
* [应用模型](../../design/app-model.md)
* [应用视图](../../design/app-views.md)