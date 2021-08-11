---
title: 工具提示
description: MRTK 中的工具提示概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 工具提示，
ms.openlocfilehash: af848db0962948b1f2ada73066c4ae90730b09a99dea231ebf468a05441b85ef
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193242"
---
# <a name="tooltip"></a>工具提示

![工具提示主](../images/tooltip/MRTK_Tooltip_Main.png)

工具提示通常用于在进一步检查对象时传达提示或额外信息。 工具提示可用于批注物理环境中的对象。

## <a name="how-to-use-a-tooltip"></a>如何使用工具提示

工具提示可以直接添加到层次结构中，并面向 对象。

若要使用此方法，只需将游戏对象和工具提示预制项之一 (Assets/MRTK/SDK/Features/UX/Prefabs/Tooltips) 添加到场景层次结构。 在预制的检查器面板中，展开 [`ToolTip`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTip) 脚本。 选择提示状态并配置工具提示。  在文本字段中输入工具提示各自的文本。 展开脚本，并将要具有工具提示的对象从层次结构拖动到 [`ToolTipConnector`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipConnector) 标记为"目标 *"的字段中*。 这会将工具提示附加到 对象。
![工具提示连接器](../images/tooltip/MRTK_Tooltip_Connector.png)

此用途假定工具提示始终显示或通过脚本显示/隐藏，通过更改工具提示组件的工具提示状态属性。

## <a name="dynamically-spawning-tooltips"></a>动态生成工具提示

工具提示可在运行时动态添加到对象，并预先设置为在点击或焦点上显示和隐藏。 只需将 [`ToolTipSpawner`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipSpawner) 脚本添加到任何游戏对象。 可以在脚本检查器中设置出现和消失的延迟以及生存期，以便工具提示在设置持续时间后消失。 工具提示还具有生成程序脚本中的背景视觉对象等功能样式属性。 默认情况下，工具提示将锚定到具有生成程序脚本的对象。 这可以通过将 GameObject 分配给定位点字段来进行更改。

## <a name="example-scene"></a>示例场景

在示例场景中 (Assets/MRTK/Examples/Demos/UX/Tooltips/Scenes) ，你将可以找到工具提示的各种示例。

![工具提示示例](../images/tooltip/MRTK_Tooltip_Examples.png)
