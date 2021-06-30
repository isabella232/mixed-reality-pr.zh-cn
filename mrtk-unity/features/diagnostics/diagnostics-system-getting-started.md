---
title: 诊断系统概述
description: 在 MRTK 中启用和禁用诊断的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 0de7b904a48453d6021cf7aed5835412c19b7884
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121775"
---
# <a name="diagnostic-system"></a>诊断系统

混合现实工具包诊断系统提供在应用程序中运行的诊断工具，用于分析应用程序问题。

诊断系统的第一个版本包含 [Visual Profiler，](using-visual-profiler.md) 用于分析使用应用程序时的性能问题。

## <a name="getting-started"></a>入门

> [!IMPORTANT]
> 强烈建议 **_在整个_** 产品开发周期中启用诊断系统，并禁用诊断系统作为生成和发布最终版本之前的最后一个更改。

开始使用诊断系统有两个关键步骤。

1. [启用](#enable-diagnostics) 诊断系统
2. [配置](#configure-diagnostic-options) 诊断选项

### <a name="enable-diagnostics"></a>启用诊断

诊断系统由 MixedRealityToolkit 对象管理 (或其他 [服务注册](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 器组件) 。

以下步骤将预先使用 MixedRealityToolkit 对象。 其他服务注册机构所需的步骤可能有所不同。

1. 选择场景层次结构中的 MixedRealityToolkit 对象。

    ![MRTK 配置的场景层次结构](../images/MRTK_ConfiguredHierarchy.png)

1. 将"检查器"面板导航到"诊断系统"部分，并选中"启用"
1. 选择诊断系统实现

    ![选择诊断系统实现](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> 默认配置文件（ (`DefaultMixedRealityToolkitConfigurationProfile` Assets/MRTK/SDK/Profiles) ）的用户将预配置诊断系统以使用 [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) 对象。

### <a name="configure-diagnostic-options"></a>配置诊断选项

诊断系统使用配置文件来指定要显示的组件并配置其设置。 有关 [可用组件设置详细信息，](configuring-diagnostics.md) 请参阅配置诊断系统。

> [!IMPORTANT]
> 虽然可以在开发应用程序时使用 Unity 的播放模式，而无需生成和部署步骤，但使用在目标硬件和平台上运行的已编译应用程序评估诊断系统结果非常重要。
>
> 从编辑器中运行时，性能诊断（如 [Visual Profiler）](using-visual-profiler.md)可能无法准确反映实际的应用程序性能。

## <a name="see-also"></a>另请参阅

- [诊断 API 文档](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [配置诊断系统](configuring-diagnostics.md)
- [使用 Visual Profiler](using-visual-profiler.md)
