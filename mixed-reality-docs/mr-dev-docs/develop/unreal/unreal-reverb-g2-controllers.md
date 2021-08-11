---
title: Unreal 中的 HP Reverb G2 手柄
description: 了解如何在 OpenXR 和 SteamVR 中将新的 HP Reverb G2 控制器用于 Unreal 混合现实应用程序。
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal， Unreal Engine 4， UE4， Reverb， Reverb G2， HP Reverb G2， 混合现实， 开发， 运动控制器， 用户输入， 功能， 新项目， 仿真器， 文档， 指南， 功能， 全息影像， 游戏开发， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备
ms.openlocfilehash: b287a5c7de1ea086b76228d9109cc07a4e1569f5f926cb42dc3e37cc2a3bb916
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204163"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>Unreal 中的 HP Reverb G2 手柄 

## <a name="getting-started"></a>入门

> [!IMPORTANT]
> 需要 Unreal Engine 4.26 和 OpenXR 或 SteamVR 才能访问 HP 运动控制器插件，你需要使用 HP Reverb G2 控制器。

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>移植现有 OpenXR 应用 

如果 HP Mixed Reality Controller 的游戏中不存在控制器绑定，OpenXR 运行时将尝试将现有绑定重新映射至活动控制器。  在这种情况下，游戏具有 Oculus Touch 绑定，并且没有 HP Mixed Reality Controller 绑定。

![在不存在控制器绑定时重新映射现有绑定](images/reverb-g2-img-04.png)

事件仍将启动，但如果游戏需要使用控制器特定的绑定（如右菜单按钮），则必须使用 HP Mixed Reality 交互配置文件。  每个操作可指定多个控制器绑定，以更好地支持不同的设备。
   
![使用多个控制器绑定](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a>添加输入操作映射 

定义一个新操作，并映射到 HP Mixed Reality Controller 部分中的一个按键。

![定义新操作和映射](images/reverb-g2-img-02.png)

HP Reverb G2 控制器还有一个模拟手柄，该手柄可用于具有"轴轴"绑定的轴映射。  有一个单独的"压缩"绑定，应在完全按下手柄按钮时用于操作映射。 

![使用"倾斜"轴绑定](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a>添加输入事件

右键单击蓝图，然后从输入系统搜索新的操作名称，为这些操作添加事件。  此处，蓝图使用输出当前按钮和轴状态打印字符串来响应事件。

![响应事件并输出当前按钮和轴状态蓝图](images/reverb-g2-img-06.png)

### <a name="using-input"></a>使用输入 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a>另请参阅
* [SteamVR 输入](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [将 SteamVR 与 Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Unreal Player 相机](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)