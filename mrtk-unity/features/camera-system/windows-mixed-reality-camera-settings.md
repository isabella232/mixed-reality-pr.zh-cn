---
title: Windows Mixed Reality相机设置
description: 在 MRTK Windows Mixed Reality相机设置的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 相机，
ms.openlocfilehash: 49b178b7ebd1fbcdaab9648baeaa6abfa9e885ea
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121635"
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

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>从照片/视频相机渲染混合现实捕获

使用此设置HoloLens 2，可以在混合现实捕获中启用全息影像对齐。 如果启用，该平台将在拍摄混合现实捕获照片或视频时向应用提供额外的 HolographicCamera。 此 HolographicCamera 提供与照片/视频相机位置对应的视图矩阵，并且它使用照片/视频相机视场提供投影矩阵。 这将确保全息影像（如手部网格）在视频输出中保持可见对齐。

### <a name="hololens-2-reprojection-method"></a>HoloLens 2重现方法

设置用于重新HoloLens 2的初始方法。 默认建议是使用深度重新项目，因为场景的所有部分都将根据它们与用户的距离独立稳定。 如果全息影像看起来仍不稳定，请尝试确保所有对象已正确将深度提交到深度缓冲区。 这有时是着色器设置。 如果深度似乎已正确提交，并且不稳定仍然存在，请尝试自动平面稳定，它使用深度缓冲区来计算稳定平面。 如果应用无法提交足够的深度数据供其中任一选项使用，则平面重新保护作为回退提供。 此方法将基于应用通过 [SetFocusPointForFrame 提供的焦点数据](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)。

若要在运行时更新 reprojection 方法，请如下所示 `WindowsMixedRealityReprojectionUpdater` 访问 ：

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

只需更新一次，该值将重新用于所有后续帧。 如果方法将频繁更新，则建议缓存 的结果， `EnsureComponent` 而不是经常调用它。

## <a name="see-also"></a>另请参阅

- [照相机系统概述](camera-system-overview.md)
- [创建相机设置提供程序](create-settings-provider.md)
- [从 PV 混合现实捕获渲染图像](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [全息重新投影](/windows/mixed-reality/hologram-stability#reprojection)