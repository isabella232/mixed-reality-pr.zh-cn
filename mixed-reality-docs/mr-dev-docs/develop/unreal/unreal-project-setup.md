---
title: 设置 Unreal 项目
description: 了解如何使用最新版 Unreal Engine 和混合现实功能工具设置项目。
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, 混合现实, 开发, 功能, 新项目, 仿真器, 文档, 指南, 全息影像, 游戏开发, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: 8201e97ed35d11404928c1dfe94ad9b7e626e51b
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394611"
---
# <a name="setting-up-your-unreal-project"></a>设置 Unreal 项目

建议安装 [Unreal Engine 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 或更高版本，以充分利用内置的 HoloLens 支持。

转到 Epic Games Launcher 的“库”选项卡，选择“启动”旁的下拉箭头，然后单击“选项”。   在“目标平台”下，选择“HoloLens 2”，然后单击“应用”。
![Unreal 安装选项 HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>导入 Unreal 的混合现实工具包

![MRTK](../../design/images/MRTK_UX_Hero.png)

混合现实工具包 (MRTK) 是一个用于混合现实应用程序的开放源代码跨平台开发工具包。 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。 该工具包旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。

对于安装，我们建议完成策划的 [Unreal 开发历程](unreal-development-overview.md)的[入门部分](unreal-development-overview.md#1-getting-started)。 如果你已遵循 Unreal 开发历程，请完成下面列出的其余设置步骤，并继续学习 [HoloLens 2 入门教程](tutorials/unreal-uxt-ch1.md)。

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 徽标图像](../images/MRTK-Unreal-Banner.png)<br>**混合现实工具包 - Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> 如果你不想使用 Unreal 的 MRTK，则需要自行编写所有交互和行为的脚本。