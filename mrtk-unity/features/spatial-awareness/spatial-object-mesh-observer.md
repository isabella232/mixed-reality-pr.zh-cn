---
title: 空间对象网格观察器
description: 有关 MRTK 中空间网格观察程序的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: db0b2f14d0a5d65140223d3fa3f4f5324ef2ba76
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176691"
---
# <a name="spatial-object-mesh-observer"></a>空间对象网格观察器

在 Unity 编辑器中提供环境网格数据的便捷方法就是使用 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 类。 空间 *对象网格观察* 程序是空间感知系统的仅编辑器数据访问接口，[](spatial-awareness-getting-started.md)允许导入三维模型数据来表示空间网格。 空间对象网格观察者的一个常见用途是通过 Microsoft HoloLens 导入扫描的数据，以测试体验如何适应 Unity 中的不同环境。

## <a name="getting-started"></a>入门

本指南将演练设置空间对象 *网格观察器*。 启用此功能有三个关键步骤。

1. 将空间 *对象网格观察器* 添加到空间感知系统配置文件
1. 设置环境网格数据对象
1. [配置网格观察器配置文件属性的其余部分](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a>设置空间 *对象网格观察器* 配置文件

1. 选择所需的 *混合现实Toolkit* 配置文件，或选择场景中 *的混合现实Toolkit* 对象
1. 打开或展开" *空间感知系统"* 选项卡
1. 单击" *添加空间观察器"* 按钮

    ![添加空间观察器](../images/spatial-awareness/AddObserver.png)

1. 选择 *SpatialObjectMeshObserver* 类型

    ![选择空间对象网格观察器](../images/spatial-awareness/SelectObjectObserver.png)

1. 选择所需的 *空间网格对象*。 默认情况下，使用示例模型配置观察程序。 此模型是使用 Microsoft HoloLens创建的，但可以[创建新的扫描网格对象](#acquiring-environment-scans)。
1. [配置网格观察器配置文件属性的其余部分](configuring-spatial-awareness-mesh-observer.md)

    ![选择网格对象](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a>空间对象网格观察器配置文件说明

由于 *空间对象网格观察程序* 从 3D 模型加载数据，因此它不支持下面概述的一些标准网格观察程序设置。

**更新间隔**

加载  *模型时* ，空间对象网格观察程序会向应用程序发送所有网格。 它不会模拟更新之间的时间增量。 应用程序可以通过调用 和 来重新接收网格 [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) 事件 [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) 。

**是固定观察者**

空间 *对象网格观察器* 将所有 3D 网格对象都考虑为静态，并忽略原点。

**观察者形状和区**

空间  *对象网格观察程序* 将整个 3D 网格发送到应用程序。 不考虑观察者形状和区。

**详细信息和三角形级别/三角形/三角形**

将网格发送到应用程序时，观察程序不会尝试查找 3D 模型 LOD。

## <a name="acquiring-environment-scans"></a>获取环境扫描

本部分概述了用于创建和收集空间网格 *对象* 文件以用于空间对象网格观察 *程序 的其他信息*。

### <a name="windows-device-portal"></a>Windows 设备门户

该[Windows 设备门户](/windows/mixed-reality/using-the-windows-device-portal)可用于从设备下载空间网格（作为 .obj Microsoft HoloLens文件）。

1. 只需通过快速浏览和查看所需环境即可HoloLens
1. 连接HoloLens Windows 设备门户
1. 导航到 *"三维视图"* 页
1. 单击"空间 *映射"**部分下的"更新"* 按钮
1. 单击" *空间映射* " *部分下的* "保存"按钮，将 obj 文件保存到电脑

> [!NOTE]
> **HoloToolkit .room 文件**
>
> 许多开发人员以前会使用 HoloToolkit 扫描环境并创建 .room 文件。 混合现实Toolkit现在支持在 Unity 中将这些文件导入为 GameObjects，并使用它们作为观察 *程序* 中的空间网格对象。

## <a name="see-also"></a>另请参阅

- [Profiles](../profiles/profiles.md)
- [混合现实Toolkit配置文件配置指南](../../configuration/mixed-reality-configuration-guide.md)
- [空间感知入门](spatial-awareness-getting-started.md)
- [在设备上配置网格观察程序](configuring-spatial-awareness-mesh-observer.md)
- [通过代码配置网格观察程序](usage-guide.md)
- [使用 Windows 设备门户](/windows/mixed-reality/using-the-windows-device-portal)
