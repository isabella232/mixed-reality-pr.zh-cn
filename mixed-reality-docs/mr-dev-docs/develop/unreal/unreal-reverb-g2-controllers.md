---
title: Unreal 中的 HP 回音 G2 控制器
description: 了解如何使用 OpenXR 和 SteamVR 中的新 HP 回音 G2 控制器来 Unreal 混合现实应用程序。
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal，Unreal Engine 4，UE4，回音，回音 G2，HP 回音 G2，mixed reality，开发，运动控制器，用户输入，功能，新项目，模拟器，文档，指南，功能，全息影像，游戏开发，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 83ff19c0527ee2d10a4f00ccd84539ca16d05517
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009987"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>Unreal 中的 HP 回音 G2 控制器 

## <a name="getting-started"></a>入门

> [!IMPORTANT]
> 需要使用 Unreal 引擎4.26 和 OpenXR 或 SteamVR 来访问 HP 运动控制器插件，你需要使用 HP 回音 G2 控制器。

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>移植现有的 OpenXR 应用 

如果 HP 混合现实控制器的游戏中不存在控制器绑定，OpenXR 运行时将尝试将现有绑定重新映射到活动控制器。  在这种情况下，游戏具有 Oculus Touch 绑定，没有 HP 混合现实控制器绑定。

![在不存在控制器绑定时重新映射现有绑定](images/reverb-g2-img-04.png)

事件仍将触发，但是如果游戏需要使用控制器特定的绑定（如右菜单按钮），则必须使用 HP 混合现实交互配置文件。  可以为每个操作指定多个控制器绑定，以便更好地支持不同的设备。
   
![使用多控制器绑定](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a>添加输入操作映射 

定义新操作并映射到 "HP Mixed Reality 控制器" 部分中的某个按键。

![定义新操作和映射](images/reverb-g2-img-02.png)

HP 回音 G2 控制器还具有模拟手柄，可在使用 "挤压轴" 绑定的轴映射中使用。  有一个单独的压缩绑定，该绑定应在完全按下手柄按钮时用于操作映射。 

![使用挤轴绑定](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a>添加输入事件

右键单击蓝图，并搜索输入系统的新操作名称，为这些操作添加事件。  这里，蓝图使用输出当前按钮和轴状态的打印字符串来响应事件。

![蓝图响应事件并输出当前按钮和轴状态](images/reverb-g2-img-06.png)

### <a name="using-input"></a>使用输入 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a>另请参阅
* [SteamVR 输入](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [将 SteamVR 与 Windows Mixed Reality 一起使用](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Unreal Player 相机](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)