---
title: 为设备配置网格观察程序
description: 如何在 MRTK 中配置现用空间网格观察器
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: aba49e88d4fc555a88fe42e4b09858f1d2453ddc
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281938"
---
# <a name="configuring-mesh-observers-for-device"></a>为设备配置网格观察程序

本指南将演练在 MRTK 中配置现成空间网格观察程序，该观察程序支持Windows Mixed Reality平台 (，即 HoloLens) 。 混合现实应用程序提供的默认实现Toolkit [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)类。 不过，本文中的许多属性适用于其他 [自定义观察者实现](create-data-provider.md)。

## <a name="profile-settings"></a>配置文件设置

为空间感知系统 配置空间网格观察程序配置文件时，必须先定义以下两 [项](spatial-awareness-getting-started.md)。

1. 具体观察者类型实现
1. 用于运行此 () 支持的平台列表

> [!NOTE]
> 所有观察程序都必须扩展 [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 接口。

![网格观察器常规设置平台类型](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a>常规设置

![网格观察器常规设置常规设置](../images/spatial-awareness/MeshObserverGeneralSettings.png)

**启动行为**

启动行为指定观察程序在首次实例化时是否开始运行。 这两个选项如下：

* *自动启动* - 默认值，在此默认值中，观察者将在初始化后开始操作
* *手动启动* - 观察程序将等待定向到启动

如果使用手动 *启动*，则必须 [在运行时通过代码 恢复和挂起它们](usage-guide.md#starting-and-stopping-mesh-observation)。

**更新间隔**

请求平台更新空间网格数据之间的时间（秒）。 典型值的范围为 0.1 和 5.0 秒。

**是固定观察者**

指示观察程序是保持静止状态，还是与用户一起移动和更新。 如果为 *true，则* 具有由观察区定义的卷的观察程序 *形状在启动时* 将保留在原点。 如果为 false，则观察者空间将跟随用户的头部作为形状的原点。

对于观察器空间之外的任何物理区域，不会根据以下属性的定义计算网格数据：是固定观察者、*观察者形状**和观察 *区*。 

**观察者形状**

观察者形状定义网格观察器在观察网格时将使用的卷的类型。 支持的选项包括：

* *轴对齐多维数据集* - 与世界坐标系统的轴保持一致的矩形形状，如应用程序启动时确定。
* *用户对齐的多维数据集* - 旋转以与用户本地坐标系对齐的矩形形状。
* *球体* - 球状体，其中心位于世界空间原点。 "观察区 *"* 属性的 X 值将用作球体的半径。

**观察区**

观察区定义将观测网格的观察点的距离。

### <a name="physics-settings"></a>物理设置

![网格观察器物理设置](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

**物理层**

要与 Unity 物理和 RayCast 系统交互而放置空间网格对象的物理层。

> [!NOTE]
> 混合现实Toolkit默认保留 *第 31* 层供空间感知观察者使用。

**重新计算法线**

指定网格观察器是否会在观察后重新计算网格的法线。 此设置可用于确保应用程序在未通过网格返回这些网格的平台上接收包含有效法线数据的网格。

### <a name="level-of-detail-settings"></a>详细信息设置级别

![网格观察器详细级别设置](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

**详细信息级别**

指定空间网格 (LOD) 的详细级别。 当前定义的值为"粗略"、"精细"和"自定义"。

* *粗略* - 对应用程序性能的影响较小，是导航/平面查找的极佳选择。

* *中等* - 均衡设置通常适用于持续扫描环境以寻找大型特征、楼层和墙面以及遮挡细节的体验。

* *精细* - 通常对应用程序性能的影响更大，是遮挡网格的一个很好的选择。

* *自定义* - 要求应用程序指定 *"三角形/* 三角形"属性，并允许应用程序优化空间网格观察程序的准确性和性能影响。

> [!NOTE]
> 不保证所有平台都遵守所有 *三角形/* 三角形计量值。 使用自定义 LOD 时，强烈建议进行试验和分析。

**每个三角形（每三米）**

对"详细信息 *级别"* 属性使用"自定义"设置 **时** 有效，并指定空间网格的三角形密度。

### <a name="display-settings"></a>显示设置

![网格观察器显示设置](../images/spatial-awareness/MeshObserverDisplaySettings.png)

**显示选项**

指定观察器如何显示空间网格。 支持的值是：

* *无* - 观察者不会呈现网格
* *可见* - 网格数据将通过使用可见 *材料可见*
* *遮挡* - 网格数据将是场景中使用遮挡材料的 *遮挡项*

![选择空间感知系统实现](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

可以通过代码在运行时 [恢复/挂起空间观察程序。](usage-guide.md#starting-and-stopping-mesh-observation)

> [!WARNING]
> 将 *"显示选项**"设置为"无***"不会阻止** 观察程序运行。 如果要停止所有观察程序，应用程序将需要通过 暂停所有观察程序 [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)

**可见材料**

指示可视化空间网格时所使用的材料。

**遮挡材料**

指示用于使空间网格遮挡全息影像的材料。

## <a name="see-also"></a>另请参阅

* [空间感知系统](spatial-awareness-getting-started.md)
* [通过代码配置空间感知系统](usage-guide.md)
* [IMixedRealitySpatialAwarenessObserver API 文档](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [IMixedRealitySpatialAwarenessMeshObserver API 文档](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [BaseSpatialObserver API 文档](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
