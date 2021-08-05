---
title: 空间对象网格观察程序
description: 有关 MRTK 中的空间网格观察程序的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: f28f8dcb320332b8ff8942ae0b442c0817d6d0b790347daa419cfc24dc0d60fc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209109"
---
# <a name="spatial-object-mesh-observer"></a>空间对象网格观察程序

在 Unity 编辑器中提供环境网格数据的一种简便方法是使用 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 类。 *空间对象网格观察* 程序是用于 [空间感知系统](spatial-awareness-getting-started.md)的仅限编辑器的数据访问接口，它允许导入三维模型数据以表示空间网格。 *空间对象网格观察* 程序的一种常见用途是导入通过 Microsoft HoloLens 扫描的数据，测试体验如何适应 Unity 内的不同环境。

## <a name="getting-started"></a>入门

本指南将指导完成设置 *空间对象网格观察* 程序。 启用此功能有三个关键步骤。

1. 向空间感知系统配置文件添加 *空间对象网格观察* 程序
1. 设置环境网格数据对象
1. [配置其他网格观察程序配置文件属性](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a>设置 *空间对象网格观察* 程序配置文件

1. 选择所需的 *混合现实 Toolkit* 配置文件或在场景中选择 *混合现实 Toolkit* 对象
1. 打开或展开 " *空间感知系统* " 选项卡
1. 单击 *"添加空间观察器"* 按钮

    ![添加空间观察程序](../images/spatial-awareness/AddObserver.png)

1. 选择 *SpatialObjectMeshObserver* 类型

    ![选择空间对象网格观察程序](../images/spatial-awareness/SelectObjectObserver.png)

1. 选择所需的 *空间网格对象*。 默认情况下，使用示例模型配置观察程序。 此模型是使用 Microsoft HoloLens 创建的，但也可以[创建新的 scan 网格对象](#acquiring-environment-scans)。
1. [配置其他网格观察程序配置文件属性](configuring-spatial-awareness-mesh-observer.md)

    ![选择网格对象](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a>空间对象网格观察程序配置文件说明

由于 *空间对象网格观察* 程序从三维模型加载数据，因此它不遵循下面所述的一些标准网格观察程序设置。

**更新间隔**

加载模型时，  *空间对象网格观察* 器会将所有网格发送到应用程序。 它不模拟更新之间的时间增量。 应用程序可以通过调用和重新接收网格事件 [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) 。

**为静止观察程序**

*空间对象网格观察* 器会将所有的3d 网格对象视为静止和不是忽略原点。

**观察者形状和区**

*空间对象网格观察* 器将整个3d 网格发送到应用程序。 不考虑观察者形状和区。

**详细级别和三角形/立方米**

在将网格发送到应用程序时，观察程序不会尝试查找 3D model LODs。

## <a name="acquiring-environment-scans"></a>正在获取环境扫描

本部分概述了用于创建和收集 *空间网格对象* 文件的其他信息，以便用于 *空间对象网格观察* 程序。

### <a name="windows-device-portal"></a>Windows 设备门户

[Windows 设备门户](/windows/mixed-reality/using-the-windows-device-portal)可用于从 Microsoft HoloLens 设备以 .obj 文件的形式下载空间网格。

1. 只需使用 HoloLens 浏览和查看所需的环境即可进行扫描
1. 使用 Windows 设备门户连接到 HoloLens
1. 导航到 *三维视图* 页面
1. 单击 "*空间映射*" 部分下的 "*更新*" 按钮
1. 单击 "*空间映射*" 部分下的 "*保存*" 按钮，将 OBJ 文件保存到 PC

> [!NOTE]
> **HoloToolkit 文件**
>
> 许多开发人员以前使用 HoloToolkit 来扫描环境并创建文件室文件。 混合现实 Toolkit 现在支持将这些文件导入到 Unity 中的 gameobject，并将其用作观察程序中的 *空间网格对象*。

## <a name="see-also"></a>另请参阅

- [Profiles](../profiles/profiles.md)
- [混合现实 Toolkit 配置文件配置指南](../../configuration/mixed-reality-configuration-guide.md)
- [空间感知入门](spatial-awareness-getting-started.md)
- [在设备上配置网格观察器](configuring-spatial-awareness-mesh-observer.md)
- [通过代码配置网格观察器](usage-guide.md)
- [使用 Windows 设备门户](/windows/mixed-reality/using-the-windows-device-portal)
