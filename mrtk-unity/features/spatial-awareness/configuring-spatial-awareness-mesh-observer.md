---
title: 为设备配置网格观察程序
description: 如何在 MRTK 中配置现成的空间网格观察程序
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 00a3b9afe1970239f52b1ead4f87f930c5826ba75522b99a52cf368249c9fd83
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228443"
---
# <a name="configuring-mesh-observers-for-device"></a>为设备配置网格观察程序

本指南将指导你在 MRTK 中配置现成的空间网格观察程序，该程序支持 Windows Mixed Reality 平台 (例如 HoloLens) 。 混合现实 Toolkit 提供的默认实现是[WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)类。 本文中的许多属性都适用于其他 [自定义观察程序实现](create-data-provider.md)。

## <a name="profile-settings"></a>配置文件设置

为 [空间感知系统](spatial-awareness-getting-started.md)配置空间网格观察程序配置文件时，必须先定义以下两项。

1. 具体观察者类型实现
1. 运行此观察程序) 受支持平台 (的列表

> [!NOTE]
> 所有观察器都必须扩展 [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 接口。

![网格观察程序常规设置平台类型](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a>常规设置

![网格观察程序常规设置 Genral 设置](../images/spatial-awareness/MeshObserverGeneralSettings.png)

**启动行为**

启动行为指定观察程序在第一次实例化时是否将开始运行。 这两个选项如下：

* *自动启动* -默认值，由此观察程序在初始化后将开始操作
* *手动启动* -观察者将等待定向到开始

如果使用 *手动启动*，则必须 [在运行时通过代码恢复并挂起它们](usage-guide.md#starting-and-stopping-mesh-observation)。

**更新间隔**

向平台发送更新空间网格数据所用的时间（以秒为单位）。 典型值介于0.1 和5.0 秒之间。

**为静止观察程序**

指示观察者是保持静止还是与用户一起移动和更新。 如果为 true，则在启动时，具有由 *观察范围* 定义的卷的 *观察者形状* 将保持为源。 如果为 false，则观察者空间将跟随用户的头作为形状的原点。

将不会为这些属性所定义的观察者空间之外的任何物理区域计算网格数据： *是静止观察程序*、* 观察器形状 * * 和 *观察区*。

**观察者形状**

"观察者" 形状定义网格观察器在观察网格时将使用的卷的类型。 支持的选项包括：

* *轴对齐的多维数据集* -与世界坐标系统的轴对齐的矩形形状，在应用程序启动时确定。
* *用户对齐的多维数据集* -旋转以与用户本地坐标系统对齐的矩形形状。
* *球* -带有世界空间原点中心的球面体积。 " *观察范围* " 属性的 X 值将用作球的半径。

**观察范围**

"观察范围" 定义观察到的网格的距离。

### <a name="physics-settings"></a>物理设置

![网格观察器物理学设置](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

**物理层**

将在其中放置空间网格对象以便与 Unity 物理学和 RayCast 系统交互的物理层。

> [!NOTE]
> 默认情况下，混合现实 Toolkit 保留 *第31层* 以供空间感知观察程序使用。

**重新计算法线**

指定网格观察器是否将在观察后重新计算网格的法线。 此设置可用于确保应用程序在不使用网格返回它们的平台上接收包含有效的法线数据的网格。

### <a name="level-of-detail-settings"></a>详细信息设置级别

![网格观察程序级别详细信息设置](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

**详细信息级别**

指定空间网格数据 (LOD) 的详细级别。 当前定义的值是粗、精细和自定义的。

* *粗* -对应用程序性能的影响较小，并且是导航/平面查找的最佳选择。

* "*中等* 平衡" 设置通常适用于对大型功能、地面和墙壁以及封闭详细信息持续扫描环境的体验。

* *正常* 情况下，exacts 对应用程序性能的影响较高，对于封闭网格非常有用。

* *自定义* -要求应用程序指定 *三角形/立方米计量* 属性，并使应用程序能够优化性能和对空间网格观察程序性能的影响。

> [!NOTE]
> 不能保证所有的 *三角形/立方计量* 值都由所有平台所接受。 使用自定义 LOD 时，强烈建议使用试验和分析。

**每个立方计量的三角形**

使用 "**详细信息级别**" 属性的 "*自定义*" 设置并为空间网格指定三角形密度时有效。

### <a name="display-settings"></a>显示设置

![网格观察程序显示设置](../images/spatial-awareness/MeshObserverDisplaySettings.png)

**显示选项**

指定观察者如何显示空间网格。 支持的值是：

* *无* -观察程序将不呈现网格
* *可见的数据* 将使用 *可见材料* 显示
* *封闭* 数据将使用 *封闭材料* 在场景中遮蔽项

![选择空间感知系统实现](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

空间观察器可 [在运行时通过代码恢复/挂起。](usage-guide.md#starting-and-stopping-mesh-observation)

> [!WARNING]
> 将 *显示选项* 设置为 " *无* **" 不会停止运行** 观察程序。 如果要停止所有观察程序，应用程序将需要通过 [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)

**可见材料**

指示可视化空间网格时要使用的材料。

**封闭材料**

指示用于使空间网格遮蔽全息影像的材料。

## <a name="see-also"></a>另请参阅

* [空间感知系统](spatial-awareness-getting-started.md)
* [通过代码配置空间感知系统](usage-guide.md)
* [IMixedRealitySpatialAwarenessObserver API 文档](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [IMixedRealitySpatialAwarenessMeshObserver API 文档](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [BaseSpatialObserver API 文档](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
