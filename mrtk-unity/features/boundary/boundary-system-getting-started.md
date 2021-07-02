---
title: 边界系统概述
description: MRTK 中边界系统的登陆页
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 边界系统，
ms.openlocfilehash: fd70479e5183e9a7557de5c5a532cc87161be017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177085"
---
# <a name="boundary-system-overview"></a>边界系统概述

边界系统支持在混合现实应用程序中可视化虚拟现实边界组件。 边界定义一个区域，用户可以在运动 VR 头戴显示设备时安全地四处移动。 边界是混合现实体验的一个重要组成部分，可帮助用户在接触 VR 头戴显示设备时避免意外的障碍。

许多虚拟现实平台都提供自动显示，例如，当用户或控制器接近边界时，虚拟世界上叠加了白色轮廓。 混合现实Toolkit边界系统扩展了此功能，以便显示跟踪区域、地平面和其他可用于为用户提供附加信息的功能的轮廓。

## <a name="getting-started"></a>入门

添加对边界的支持需要混合现实平台的两个关键Toolkit：边界系统和配置了边界的虚拟现实平台。

1. [启用](#enable-boundary-system) 边界系统
2. [配置](#configure-boundary-visualization) 边界可视化效果
3. [生成并](#build-and-deploy) 部署到具有已配置边界的 VR 平台

## <a name="enable-boundary-system"></a>启用边界系统

边界系统由 MixedRealityToolkit 对象对象 (或其他 [服务](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 注册器组件) 。

以下步骤将预先使用 MixedRealityToolkit 对象。 其他服务注册机构所需的步骤可能有所不同。

1. 选择场景层次结构中的 MixedRealityToolkit 对象。

    ![MRTK 配置的场景层次结构](../images/MRTK_ConfiguredHierarchy.png)

1. 将"检查器"面板导航到"边界系统"部分，并选中"启用"

    ![启用边界系统](../images/boundary/MRTKConfig_Boundary.png)

1. 选择边界系统实现。 MRTK 提供的默认类实现是 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

    ![选择边界系统实现](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> 所有边界系统实现都必须扩展 [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)

## <a name="configure-boundary-visualization"></a>配置边界可视化

[边界系统使用配置文件来](configuring-boundary-visualization.md)指定要显示的边界组件并配置其外观。

![边界可视化选项](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> 默认配置文件 `DefaultMixedRealityBoundaryVisualizationProfile` （ (Assets/MRTK/SDK/Profiles) ）的用户将预先配置边界系统以显示楼层平面、播放区域以及跟踪区域。

## <a name="build-and-deploy"></a>生成并部署

使用所需的可视化选项配置边界系统后，可以将项目部署到目标平台。

> [!NOTE]
> Unity 播放模式启用已配置边界的编辑器内可视化。 此功能可实现快速开发和测试，而无需生成和部署步骤。 请确保使用在目标硬件和平台上运行的生成和部署的应用程序版本执行最终验收测试。

## <a name="accessing-boundary-system-via-code"></a>通过代码访问边界系统

如果启用并配置了边界系统，则可以通过 CoreServices 静态帮助程序类访问边界系统。 然后，可以使用引用动态更改边界参数，并访问由系统管理的相关 GameObject。

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a>另请参阅

- [边界 API 文档](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [配置边界可视化效果](configuring-boundary-visualization.md)
