---
title: 检测 MRTK 中的控制器
description: 有关将各种控制器与 MRTK 一起使用的文档
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 控制器， HP Reverb， Oculus， CPU Vive， 手
ms.openlocfilehash: 04afcf75fc11c1c3b4c6fb9f244172c0960e8943bd469bc6424465b376ceaf53
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226400"
---
# <a name="detecting-controllers-in-mrtk"></a>检测 MRTK 中的控制器

MRTK 支持许多不同的控制器。 在兼容的设备上启动使用 MRTK 构建的应用程序后，许多控制器（例如，"完成"操作）将本机工作，例如"适用于 KNP Vive Knuckles"和"适用于 WINDOWS Vive Wands"的应用程序。 其他控制器（如 Oculus Quest 和 HP Reverb G2 控制器上的手部）需要其他包，然后 MRTK 才能识别它们。

本文档介绍需要安装额外包的常见方案。 有关如何部署到设备的说明，请参阅 [**Hololens/WMR**](./wmr-mrtk.md) 或 [**Oculus Quest**](/windows/mixed-reality/mrtk-unity/supported-devices/oclus-quest-mrtk) 部署页。 有关控制器的其他信息，请访问 [**功能页**](../features/input/controllers.md)。 若要调试控制器问题，请参阅 [**控制器映射工具**](../features/tools/controller-mapping-tool.md)

## <a name="hp-reverb-g2-controllers"></a>HP Reverb G2 控制器

若要在使用 MRTK 时检测并显示 HP Reverb G2 控制器，请按照以下步骤安装 [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) 包。 安装此包后，无需对默认配置文件进行任何其他更改，使控制器显示在 HP Reverb 上。 

若要在编辑器中显示控制器，需要确保使用 [**OpenXR 插件**](/windows/mixed-reality/develop/unity/openxr-getting-started)。

## <a name="oculus-controllers"></a>Oculus 控制器 

若要可视化 Oculus 控制器模型，请按照 Oculus Quest 部署说明进行操作。 如果要在使用控制器时显示虚拟手，请确保在 XR SDK  Oculus 控件下选中"呈现头像手而不是控制器"设备管理器。 否则，请取消选中此选项。

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
