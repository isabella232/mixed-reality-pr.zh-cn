---
title: MRTK 中的控制器
description: 有关将各种控制器与 MRTK 一起使用的文档
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，控制器，HP 回音，Oculus，HTC Naopak，动手
ms.openlocfilehash: 953b1cd56dbf7d7a548a3aba8da07ce5875fec74
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145458"
---
# <a name="controllers-in-mrtk"></a>MRTK 中的控制器

MRTK 支持许多不同的控制器。 当使用 MRTK 构建的应用程序在兼容的设备上启动时，许多控制器（例如 HTC Naopak Knuckles 和 HTC Naopak Wands）都将在本机工作。 其他控制器（如 Oculus 请求和 HP 回音 G2 控制器上的明确说明）在 MRTK 识别它们之前需要额外的包。

本文档将介绍需要安装额外包的常见方案。 有关控制器的其他信息，请访问 [**功能页**](../features/input/controllers.md)。 若要调试控制器的问题，请参阅 [**控制器映射工具**](../features/tools/controller-mapping-tool.md)

## <a name="hp-reverb-g2-controllers"></a>HP 回音 G2 控制器

若要在使用 MRTK 时检测并显示 HP 回音 G2 控制器，请按照以下步骤安装 [**MixedReality**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) 包。 安装此包后，需要对默认配置文件进行其他更改，使控制器显示在 HP 回音上。 

若要在编辑器中显示控制器，需要确保使用的是 [**OpenXR 插件**](/windows/mixed-reality/develop/unity/openxr-getting-started)。

## <a name="oculus-controllers"></a>Oculus 控制器 

若要可视化 Oculus 控制器模型，请按照 Oculus 寻找部署说明进行操作。 如果要在使用控制器时显示虚拟指针，请确保在 XR SDK Oculus Device Manager 下选中 " **呈现头像" 而非 "控制器** "。 否则，请取消选中此选项。

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
