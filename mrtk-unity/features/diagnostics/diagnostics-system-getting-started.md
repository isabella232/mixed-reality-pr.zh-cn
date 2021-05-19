---
title: 诊断系统入门
description: 用于在 MRTK 中启用和禁用诊断的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 66d68902dd9ffa36a5b30c1130a8640d154ac5e1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144723"
---
# <a name="diagnostic-system"></a>诊断系统

混合现实工具包诊断系统提供在应用程序中运行的诊断工具，以启用对应用程序问题的分析。

诊断系统的第一个版本包含 [视觉探查器](using-visual-profiler.md) ，以允许在使用应用程序时分析性能问题。

## <a name="getting-started"></a>入门

> [!IMPORTANT]
> **_强烈_** 建议在整个产品开发周期中启用诊断系统，并在生成和发布最终版本之前禁用该系统。

开始使用诊断系统需要执行两个重要步骤。

1. [启用](#enable-diagnostics) 诊断系统
2. [配置](#configure-diagnostic-options) 诊断选项

### <a name="enable-diagnostics"></a>启用诊断

诊断系统由 MixedRealityToolkit 对象管理 (或另一个 [服务注册](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 器组件) 管理。

以下步骤假定使用 MixedRealityToolkit 对象。 其他服务注册机构所需的步骤可能不同。

1. 选择场景层次结构中的 MixedRealityToolkit 对象。

    ![MRTK 配置场景层次结构](../images/MRTK_ConfiguredHierarchy.png)

1. 将检查器面板导航到 "诊断系统" 部分，并选中 "启用"
1. 选择诊断系统实现

    ![选择诊断系统实现](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> 默认配置文件 `DefaultMixedRealityToolkitConfigurationProfile` (资产/MRTK/SDK/配置文件) 的用户会将该诊断系统预配置为使用该 [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) 对象。

### <a name="configure-diagnostic-options"></a>配置诊断选项

诊断系统使用配置文件来指定要显示的组件并配置其设置。 有关可用组件设置的详细信息，请参阅 [配置诊断系统](configuring-diagnostics.md) 。

> [!IMPORTANT]
> 虽然可以在开发应用程序时使用 Unity 的播放模式，而无需生成和部署步骤，但使用在目标硬件和平台上运行的已编译应用程序评估诊断系统结果非常重要。
>
> 从编辑器中运行时，性能诊断（如 [Visual Profiler）](using-visual-profiler.md)可能无法准确反映实际的应用程序性能。

## <a name="see-also"></a>另请参阅

- [诊断 API 文档](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [配置诊断系统](configuring-diagnostics.md)
- [使用 Visual Profiler](using-visual-profiler.md)
