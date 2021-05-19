---
title: 边界系统入门
description: MRTK 中边界系统的登陆页
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 边界系统，
ms.openlocfilehash: 2858b770fb49a44d1e2d704e8d3a81affe74d272
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144731"
---
# <a name="boundary-system"></a>边界系统

边界系统支持在混合现实应用程序中可视化虚拟现实边界组件。 边界定义一个区域，用户可以在运动 VR 头戴显示设备时安全地四处移动。 边界是混合现实体验的一个重要组成部分，可帮助用户在接触 VR 头戴显示设备时避免意外的障碍。

许多虚拟现实平台都提供自动显示，例如，当用户或控制器接近边界时，虚拟世界上叠加了白色轮廓。 混合现实工具包的边界系统扩展了此功能，以便显示跟踪区域、楼层平面和其他可用于为用户提供附加信息的功能的轮廓。

## <a name="getting-started"></a>入门

添加对边界的支持需要混合现实工具包的两个关键组件：边界系统和配置有边界的虚拟现实平台。

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
