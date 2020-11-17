---
title: 在 Unreal 中注视输入
description: 针对 HoloLens 和 Unreal 引擎设置注视输入的教程
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality，全息影像，HoloLens 2，眼睛跟踪，眼睛输入，head 装显示，Unreal 引擎，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: 2ea55e3c53275f6150ca7f2def10d71634119e2e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679046"
---
# <a name="gaze-input"></a>注视输入

## <a name="overview"></a>概述

[Windows Mixed Reality 插件](https://docs.unrealengine.com/Platforms/VR/WMR/index.html)不提供任何用于目视输入的内置函数，但 HoloLens 2 支持目视跟踪。 实际的跟踪功能由 Unreal 的 **Head 挂载显示** 和 **目视跟踪** api 提供，包括：

- 设备信息
- 跟踪传感器
- 方向和位置
- 剪辑窗格
- 注视数据和跟踪信息

可以在 Unreal 的 [安装的显示](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) 和 [目视跟踪](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) 文档中找到功能的完整列表。

除了 Unreal Api 外，还可以查看有关 HoloLens 2 的 [基于目视](../../design/eye-gaze-interaction.md) 观看的交互的文档，并了解如何 [在 hololens 2 上运行目视跟踪](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) 。

> [!IMPORTANT]
> 仅在 HoloLens 2 上支持目视跟踪。

## <a name="enabling-eye-tracking"></a>启用目视跟踪
需要在 HoloLens 项目设置中启用 "注视输入"，然后才能使用任何 Unreal Api。 当应用程序启动时，你将看到下面的屏幕截图中显示的同意提示。

- 选择 **"是"** 以设置权限并获取对注视输入的访问权限。 如果需要随时更改此设置，可在 " **设置** " 应用中找到它。

![目视输入权限](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> Unreal 中的 HoloLens 眼睛跟踪只对这两种眼睛都有一个注视，而不是 stereoscopic 跟踪所需的两个射线，这不受支持。

这就是在 Unreal 中开始向 HoloLens 2 应用添加注视输入所需的全部设置。 有关 "注视输入" 以及它如何影响混合现实中的用户的详细信息，请参阅以下链接。 在构建交互式体验时，请务必考虑这种情况。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们规划的 Unreal 开发检查点历程，则你处于探索 MRTK 核心构建基块的过程之中。 从这里，你可以进入下一个构建基块： 

> [!div class="nextstepaction"]
> [手部跟踪](unreal-hand-tracking.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [HoloLens 摄像头](unreal-hololens-camera.md)

你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅
* [校准](../../calibration.md)
* [舒适](../../design/comfort.md)
* [凝视和提交](../../design/gaze-and-commit.md)
* [语音输入](../../out-of-scope/voice-design.md)
