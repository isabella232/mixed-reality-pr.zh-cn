---
title: 控制器映射工具
description: 有关 MRTK 中的控制器映射工具的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: f00dc01555ef158dab21334761bd23ef6a70dba4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144082"
---
# <a name="controller-mapping-tool"></a>控制器映射工具

控制器映射工具是 (或编辑器) 工具中的运行时映射，使开发人员能够快速确定硬件控制器的 Unity 输入轴和按钮映射 (例如：运动控制器) 。

开发对新硬件控制器的支持时，此工具非常有用。 它还可以帮助确认现有控制器的支持类中存在可疑的控制映射问题。

![控制器映射工具](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a>使用控制器映射工具

若要开始使用控制器映射工具，请导航到 **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** 并打开 **ControllerMappingTool** 场景。 加载场景后，可以使用播放模式在编辑器中运行项目，或在设备上生成和运行项目。

检查 Unity 的控制器映射：

- 连接控制器
- 按每个按钮并移动每个轴
- 请注意显示中的映射
- 更新控制器的输入系统数据提供程序中的控制映射

> [!NOTE]
> 控制器映射工具不使用 Microsoft Mixed Reality Toolkit 组件。 它直接与 Unity 通信以确定和显示控件映射。

### <a name="all-controls-display"></a>显示所有控件

大型显示面板报告所有定义的 Unity 输入轴和按钮的状态，例如 (轴 10，按钮 3) 。 此面板提供控制器状态的完整视图。

![显示所有控件](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a>活动控件显示

较小的窄显示面板显示处于活动状态的 Unity 输入 axed 和按钮 (例如：按下按钮) 。 活动控件显示提供了一个易于阅读的控制器状态的摘要视图。

![活动控件显示](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a>另请参阅

- [创建输入系统数据提供程序](../input/create-data-provider.md)
- [InputFeatureUsage 工具](input-feature-usage-tool.md)
