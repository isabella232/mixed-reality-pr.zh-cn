---
title: 边界系统概述
description: MRTK 中边界系统的登陆页面
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，边界系统，
ms.openlocfilehash: 134c92d8b3019ea8114f5bf50b7c4e3a19b0061f59a8266f6218a25f73c76449
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115194401"
---
# <a name="boundary-system-overview"></a>边界系统概述

边界系统为在混合现实应用程序中可视化虚拟现实边界组件提供支持。 边界定义用户在戴上一个 VR 耳机时可以安全地四处移动的区域。 边界是混合现实体验的重要组成部分，可帮助用户在戴上一个 VR 耳机时避免出现不可见的障碍。

许多虚拟现实平台提供了自动显示，例如，当用户或其控制器接近边界时，虚拟世界上叠加的白色轮廓。 混合现实 Toolkit 的边界系统扩展了此功能，以允许显示所跟踪区域的轮廓、楼层面和可用于向用户提供附加信息的其他功能。

## <a name="getting-started"></a>入门

添加对边界的支持需要混合现实 Toolkit 的两个关键组件：边界系统和配置有边界的虚拟现实平台。

1. [启用](#enable-boundary-system) 边界系统
2. [配置](#configure-boundary-visualization) 边界可视化
3. 使用配置的边界[构建并部署](#build-and-deploy)到 VR 平台

## <a name="enable-boundary-system"></a>启用边界系统

边界系统 (或另一个 [服务注册](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 器组件) 管理。

以下步骤假定使用 MixedRealityToolkit 对象。 其他服务注册机构所需的步骤可能不同。

1. 选择场景层次结构中的 MixedRealityToolkit 对象。

    ![MRTK 配置场景层次结构](../images/MRTK_ConfiguredHierarchy.png)

1. 将检查器面板导航到边界系统部分，并选中 "启用"

    ![启用边界系统](../images/boundary/MRTKConfig_Boundary.png)

1. 选择边界系统实现。 MRTK 提供的默认类实现是 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

    ![选择边界系统实现](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> 所有边界系统实现都必须扩展 [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)

## <a name="configure-boundary-visualization"></a>配置边界可视化

[边界系统使用配置文件](configuring-boundary-visualization.md)来指定要显示的边界组件并配置其外观。

![边界可视化选项](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> 默认配置文件 `DefaultMixedRealityBoundaryVisualizationProfile` (资产/MRTK/SDK/配置文件) 的用户会将边界系统预配置为显示楼面平面、播放区域和跟踪区域。

## <a name="build-and-deploy"></a>生成并部署

为边界系统配置所需的可视化选项后，可以将项目部署到目标平台。

> [!NOTE]
> Unity 播放模式启用配置边界的编辑器内可视化。 此功能可实现快速开发和测试，而无需执行生成和部署步骤。 请确保使用在目标硬件和平台上运行的应用程序的构建和部署版本执行最终的验收测试。

## <a name="accessing-boundary-system-via-code"></a>通过代码访问边界系统

如果启用并配置，则可以通过 CoreServices 静态帮助程序类访问边界系统。 然后，可以使用该引用动态更改边界参数，并访问由系统管理的相关 Gameobject。

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a>另请参阅

- [边界 API 文档](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [配置边界可视化](configuring-boundary-visualization.md)
