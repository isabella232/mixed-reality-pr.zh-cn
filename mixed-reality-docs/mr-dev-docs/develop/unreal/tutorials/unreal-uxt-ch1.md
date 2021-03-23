---
title: 1. 入门
description: 教程系列第 1 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款象棋应用
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: a46b9fef96f75f3d80b9ebbd5cbd724730374b41
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "98580567"
---
# <a name="1-getting-started"></a>1.入门

无论你是混合现实新手还是经验丰富的专业人员，都可以使用 [HoloLens 2](../../../index.yml) 和 [Unreal Engine](https://www.unrealengine.com/en-US/) 开始你的体验之旅。 本系列教程将为你提供有关如何使用 [UX Tools 插件](https://github.com/microsoft/MixedReality-UXTools-Unreal)构建交互式象棋应用的分步指南，该插件是 [Unreal 混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unreal)的一部分。 该插件将帮助你通过代码、蓝图和示例将常见的 UX 功能添加到项目中。 

![在视口中结束场景](images/unreal-uxt/5-endscene.PNG)

在本系列文章结束时，你将拥有以下方面的经验：
* 开始新项目
* 设置混合现实
* 使用用户输入
* 添加按钮
* 在模拟器或设备上播放

## <a name="prerequisites"></a>必备知识

在开始之前，请确保已安装以下项：
* Windows 10 1809 或更高版本
* Windows 10 SDK 10.0.18362.0 或更高版本
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 或更高版本
* [针对开发配置](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)的 Microsoft HoloLens 2 设备，或[仿真器](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)
* 具有以下工作负载的 Visual Studio 2019

### <a name="installing-visual-studio-2019"></a>安装 Visual Studio 2019

首先，确保使用所有必需的 Visual Studio 包进行设置：
1. 安装最新版本的 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)
1. 安装以下[工作负载](/visualstudio/install/modify-visual-studio#modify-workloads)：
    * 使用 C++ 的桌面开发
    * .NET 桌面开发
    * 通用 Windows 平台开发
1. 展开“通用 Windows 平台开发”并选择： 
    * USB 设备连接性
    * C++ (v142) 通用 Windows 平台工具

1. 安装以下[组件](/visualstudio/install/modify-visual-studio#modify-individual-components)：
    * 编译器、生成工具和运行时 > MSVC v142 - VS 2019 C++ ARM64 生成工具（最新版本）

可使用以下图片确认安装

![VS 安装程序中的重要时钟周期](images/unreal-uxt/1-install-the-tools.png)

就这么简单！ 一切准备就绪，现在可以开始象棋项目了。

[下一节：2.初始化你的项目和第一个应用程序](unreal-uxt-ch2.md)