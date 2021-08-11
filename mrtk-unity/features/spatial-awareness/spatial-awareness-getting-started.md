---
title: 空间感知入门
description: 介绍 MRTK 中的空间感知
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: bbe5b923ea7da965424e7fac98adca180c6f91d0c9b4c4ca7a0477e301c362f9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204314"
---
# <a name="spatial-awareness-getting-started"></a>空间感知入门

![空间感知](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

空间感知系统在混合现实应用程序中提供真实的环境意识。 在 Microsoft HoloLens 上引入时，空间感知提供了一组网格，表示环境的几何图形，这允许全息影像与现实世界之间的引人注目的交互。

> [!NOTE]
> 目前，混合现实Toolkit与最初打包在 HoloToolkit 中的空间理解算法一起提供。 空间理解通常涉及转换空间网格数据，以创建简化的和/或分组的网格数据，例如平面、墙、楼层、上限等。

## <a name="getting-started"></a>入门

添加对空间感知的支持需要混合现实平台的两个关键Toolkit：空间感知系统和受支持的平台提供程序。

1. [启用](#enable-the-spatial-awareness-system) 空间感知系统
2. [注册](#register-observers) 并 [配置](configuring-spatial-awareness-mesh-observer.md) 一个或多个空间观察器以提供网格数据
3. [生成并](#build-and-deploy) 部署到支持空间感知的平台

### <a name="enable-the-spatial-awareness-system"></a>启用空间感知系统

空间感知系统由 MixedRealityToolkit 对象管理 (或其他 [服务](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 注册器组件) 。 按照以下步骤在 *MixedRealityToolkit* *配置文件* 中启用或禁用空间感知系统。

混合现实Toolkit预配置的一些默认配置文件。 其中一些默认已启用或禁用空间感知系统。 此预配置（尤其是禁用时）的目的是避免计算和呈现网格的视觉开销。

| 配置文件 | 系统默认启用 |
| --- | --- |
| `DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)  | False |
| `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)  | False |
| `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)  | True |

1. 选择场景层次结构中的 MixedRealityToolkit 对象，以在检查器面板中打开。

    ![MRTK 配置的场景层次结构](../images/MRTK_ConfiguredHierarchy.png)

1. 导航到" *空间感知系统"* 部分，并选中" *启用空间感知系统"*

    ![启用空间感知](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. 选择所需的空间感知系统实现类型。 [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem)是提供的默认值。

    ![选择空间感知系统实现](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a>注册观察者

混合现实服务Toolkit数据提供程序服务，通过平台特定的[](../../architecture/systems-extensions-providers.md)数据和实现控制来补充主要服务。 例如，混合现实输入系统具有多个数据访问接口，用于[](../input/input-providers.md)从各种特定于平台的 API 获取控制器和其他相关输入信息。

空间感知系统类似，数据提供程序为系统提供有关现实世界的网格数据。 空间感知配置文件必须至少注册一个空间观察器。 空间观察器通常是平台特定的组件，充当提供程序，用于从特定于平台的终结点（即） (网格数据 HoloLens) 。

1. 打开或展开 *空间感知系统配置文件*

    ![空间感知系统配置文件](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. 单击" *添加空间观察器"* 按钮
1. 选择所需的 *空间观察器实现类型*

    ![选择空间观察器实现](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. [根据需要修改观察器上的](configuring-spatial-awareness-mesh-observer.md) 配置属性

> [!NOTE]
>  (`DefaultMixedRealityToolkitConfigurationProfile` Assets/MRTK/SDK/Profiles) 的用户将为使用 类的 Windows Mixed Reality 平台预配置空间感知 [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 系统。

### <a name="build-and-deploy"></a>生成并部署

使用所需的观察程序配置空间感知系统 () ，可以生成项目并部署到目标平台。

> [!IMPORTANT]
> 如果面向 Windows Mixed Reality平台 (例如：HoloLens) ，请确保启用空间感知功能，以便使用设备上的空间感知系统。 [](/windows/mixed-reality/spatial-mapping-in-unity)

> [!WARNING]
> 某些平台（包括 Microsoft HoloLens）为 Unity 中的远程执行提供支持。 此功能可实现快速开发和测试，而无需生成和部署步骤。 请确保使用在目标硬件和平台上运行的生成和部署的应用程序版本执行最终验收测试。

## <a name="next-steps"></a>后续步骤

按照上述过程启用空间感知系统后，可以更详细地配置和控制系统。

有关在检查器中配置观察程序的信息：

- [为设备使用情况配置观察程序](configuring-spatial-awareness-mesh-observer.md)
- [为编辑器内使用情况配置观察程序](spatial-object-mesh-observer.md)

有关通过代码控制和扩展观察程序的信息：

- [通过代码配置观察程序](usage-guide.md)
- [创建自定义观察者](create-data-provider.md)

## <a name="see-also"></a>另请参阅

- [空间感知 API 文档](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [空间映射概述 WMR](/windows/mixed-reality/spatial-mapping)
- [Unity WMR 中的空间映射](/windows/mixed-reality/spatial-mapping-in-unity)
