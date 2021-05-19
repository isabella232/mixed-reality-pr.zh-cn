---
title: Windows Mixed Reality 照相机设置
description: 在 MRTK Windows Mixed Reality相机的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 相机，
ms.openlocfilehash: 94e00f47dc565af0824ef6acf5c08a9e99d4529f
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145167"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a>Windows Mixed Reality相机设置提供程序

Windows Mixed Reality相机设置提供程序确定运行应用程序的设备类型，并基于显示器的透明或不透明 (应用相应的) 。

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a>启用Windows Mixed Reality设置提供程序

以下步骤将预先使用 MixedRealityToolkit 对象。 其他服务注册机构所需的步骤可能有所不同。

1. 选择场景层次结构中的 MixedRealityToolkit 对象。

    ![MRTK 配置的场景层次结构](../images/MRTK_ConfiguredHierarchy.png)

2. 将"检查器"面板导航到"相机系统"部分，然后展开" **相机设置提供程序"** 部分。

    ![展开设置提供程序](../images/camera-system/ExpandProviders.png)

3. 单击 **"添加相机设置提供程序"，** 然后展开新 **添加的"新建相机设置"** 条目。

    ![展开新设置提供程序](../images/camera-system/ExpandNewProvider.png)

4. 选择Windows Mixed Reality设置提供程序

    ![选择Windows Mixed Reality设置提供程序](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> 使用 Microsoft Mixed Reality Toolkit 默认配置文件时，Windows Mixed Reality相机设置提供程序已启用并配置。

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>配置Windows Mixed Reality设置提供程序

Windows Mixed Reality相机设置还支持配置文件。 此配置文件提供以下选项：

![Windows Mixed Reality相机设置配置](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>从照片/视频摄像机呈现混合现实捕获

在 HoloLens 2 上使用此设置，你可以在混合现实捕获中启用全息图对齐。 如果已启用，则在采用混合现实捕获照片或视频时，平台将为应用提供附加的 HolographicCamera。 此 HolographicCamera 提供与照片/视频摄像机位置对应的视图矩阵，并使用视图的 "照片/视频相机" 字段提供投影矩阵。 这将确保全息影像（如手写网格）在视频输出中保持明显对齐。

### <a name="hololens-2-reprojection-method"></a>HoloLens 2 reprojection 方法

为 HoloLens 2 reprojection 设置初始方法。 默认的建议是使用深度 reprojection，因为场景的所有部分都将基于用户与用户之间的距离进行单独的稳定。 如果全息影像仍显示不稳定，请尝试确保所有对象已正确地将其深度提交到深度缓冲区。 这有时是着色器设置。 如果深度看上去正确并仍存在不稳定，请尝试 autoplanar 稳定性，它使用深度缓冲区来计算稳定平面。 如果某个应用无法为这些选项中的任何一个提供足够的深度数据可供使用，则将平面 reprojection 作为回退提供。 此方法将基于通过 [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)提供的应用提供的焦点数据。

若要在运行时更新 reprojection 方法，请访问， `WindowsMixedRealityReprojectionUpdater` 如下所示：

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

这只需更新一次，并为所有后续帧重复使用该值。 如果此方法将会频繁更新，则建议缓存的结果， `EnsureComponent` 而不是经常调用它。

## <a name="see-also"></a>另请参阅

- [照相机系统概述](camera-system-overview.md)
- [创建照相机设置提供程序](create-settings-provider.md)
- [通过 PV 相机呈现混合现实捕获](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [全息 reprojection](/windows/mixed-reality/hologram-stability#reprojection)