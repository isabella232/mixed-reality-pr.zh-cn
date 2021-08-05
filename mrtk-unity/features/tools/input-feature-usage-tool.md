---
title: 输入功能使用情况工具
description: MRTK 中的文档 InputFeatureUsage 工具
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 9d5e80ee5f31086b12ec2b82ab2368361fb738e03ea7fe5cf02ba0b4bd22c0b8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189428"
---
# <a name="input-feature-usage-tool"></a>输入功能使用情况工具

InputFeatureUsage 工具是设备上的运行时 (，或在编辑器) 工具中，它使开发人员能够快速确定检测到的输入源的可用 Unity InputFeatureUsages， (例如，运动控制器或有向清楚表述的) 手写内容。

> [!NOTE]
> 此场景仅适用于 Unity 2019.3 或更高版本。

当开发对新硬件控制器的支持时，此工具非常有用。 它还可以帮助确认现有控制器的支持类中存在可疑的控件映射问题。

![InputFeatureUsage 工具](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>使用 InputFeatureUsage 工具

若要开始学习 InputFeatureUsage 工具，请导航到 **MRTK/tools/RuntimeTools/tools/InputFeatureUsageTool** 并打开 **InputFeatureUsageTool** 场景。 加载场景后，可以使用播放模式在编辑器中运行项目，也可以在设备上生成并运行该项目。

检查控制器的 Unity 映射：

- 连接控制器
- 按每个按钮并移动每个轴
- 请注意，显示的功能用法
- 更新控制器的输入系统数据提供程序中的控件映射

> [!NOTE]
> InputFeatureUsage 工具不会将 Microsoft Mixed Reality Toolkit 组件使用。 它直接与 Unity 通信，以确定和显示功能使用情况。

### <a name="panels"></a>面板

面板显示所有检测到的 Unity 输入源上所有报告的 InputFeatureUsages 的当前状态。

顶部的小面板会列出所有检测到的源的名称。

## <a name="see-also"></a>另请参阅

- [创建输入系统数据提供程序](../input/create-data-provider.md)
- [控制器映射工具](controller-mapping-tool.md)
