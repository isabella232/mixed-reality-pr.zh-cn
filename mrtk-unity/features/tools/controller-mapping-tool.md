---
title: 控制器映射工具
description: MRTK 中的控制器映射工具的相关文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: a5ebf85e3f45e622aaa05311d78066bf8b762108af81cff5292772b92cce0900
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200208"
---
# <a name="controller-mapping-tool"></a>控制器映射工具

控制器映射工具是设备上或编辑器) 工具中的运行时 (，它使开发人员能够快速确定硬件控制器的 Unity 输入轴和按钮映射 (例如：运动控制器) 。

当开发对新硬件控制器的支持时，此工具非常有用。 它还可以帮助确认现有控制器的支持类中存在可疑的控件映射问题。

![控制器映射工具](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a>使用控制器映射工具

若要开始利用控制器映射工具，请导航到 **MRTK/tools/RuntimeTools/tools/ControllerMappingTool** 并打开 **ControllerMappingTool** 场景。 加载场景后，可以使用播放模式在编辑器中运行项目，也可以在设备上生成并运行该项目。

检查控制器的 Unity 映射：

- 连接控制器
- 按每个按钮并移动每个轴
- 请注意，显示中的映射
- 更新控制器的输入系统数据提供程序中的控件映射

> [!NOTE]
> 控制器映射工具不会将 Microsoft Mixed Reality Toolkit 组件使用。 它直接与 Unity 通信，以确定和显示控件映射。

### <a name="all-controls-display"></a>所有控件显示

大的 "显示面板" 报告所有定义的 Unity 输入轴和按钮的状态， (例如：轴10、按钮 3) 。 此面板提供控制器状态的完整视图。

![所有控件显示](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a>活动控件显示

较小的窄显示面板显示处于活动状态的 Unity 输入 axed 和按钮 (例如：按下按钮) 。 活动控件显示提供了一个易于阅读的控制器状态的摘要视图。

![活动控件显示](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a>另请参阅

- [创建输入系统数据提供程序](../input/create-data-provider.md)
- [InputFeatureUsage 工具](input-feature-usage-tool.md)
