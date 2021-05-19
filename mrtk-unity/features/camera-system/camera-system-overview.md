---
title: 照相机系统概述
description: MRTK 中相机系统的登陆页
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 相机，
ms.openlocfilehash: 1dc5328f2a6390246918063b6564837f150d28d8
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144473"
---
# <a name="camera-system"></a>相机系统

借助相机系统，Microsoft Mixed Reality Toolkit 可以配置和优化应用程序的相机，以用于混合现实应用程序。 使用相机系统，可以编写应用程序来支持不透明的 (例如：虚拟现实) 和透明 (，例如 Microsoft HoloLens) 设备，无需编写代码来区分和适应每种类型的显示器。

## <a name="enabling-the-camera-system"></a>启用相机系统

相机系统由 MixedRealityToolkit 对象 (或其他服务注册器组件) 。

以下步骤将预先使用 MixedRealityToolkit 对象。 其他服务注册机构所需的步骤可能有所不同。

1. 选择场景层次结构中的 MixedRealityToolkit 对象。

    ![MRTK 配置的场景层次结构](../images/MRTK_ConfiguredHierarchy.png)

2. 将检查器面板导航到相机系统部分，并确保选中" **启用相机系统** "。

    ![启用相机系统](../images/camera-system/EnableCameraSystem.png)

3. 选择相机系统实现。 MRTK 提供的默认类实现是 `MixedRealityCameraSystem` 。

    ![选择相机系统实现](../images/camera-system/SelectCameraSystemType.png)

4. 选择所需的配置文件

    ![选择相机系统配置文件](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a>配置相机系统

### <a name="settings-providers"></a>设置提供程序

![照相机设置提供程序](../images/camera-system/CameraSettingsProviders.png)

照相机设置提供程序启用相机的平台特定配置。 这些设置可能包括自定义配置步骤和/或组件。

可以通过单击 " **添加照相机设置提供程序** " 按钮添加提供程序。 可以通过单击 **-** 提供程序名称右侧的按钮来删除它们。

> [!Note]
> 并非所有平台都需要照相机设置提供程序。 如果没有与运行应用程序的平台兼容的提供程序，则 Microsoft Mixed Reality 工具包将应用基本默认值。

### <a name="display-settings"></a>显示设置

![相机显示设置](../images/camera-system/CameraDisplaySettings.png)

显示设置是为不透明 (（例如：虚拟现实) 和透明 (，例如： Microsoft HoloLens) 显示）指定的。 照相机是在运行时使用这些设置配置的。

**附近的剪辑**

近剪裁平面是指虚拟对象可以指向相机并仍呈现的最近的距离（以米为单位）。 为了使用户舒适，建议将此值设为大于零。 上图包含的值在各种设备上都非常熟悉。

**远剪辑**

最远的剪辑平面是一个虚拟对象可以到相机并仍呈现的最大距离（以米为单位）。 对于透明设备，建议此值相对接近于现实世界空间，并打破应用程序的沉浸式质量。

**清除标志**

清除标志值指示在绘制时如何清除显示。 对于虚拟现实体验，此值最常设置为 Skybox。 对于透明显示，建议将此设置为彩色。

**背景色**

如果 clear 标志未设置为 Skybox，则将显示 "背景颜色" 属性。

**质量设置**

质量设置值指示 Unity 在呈现场景时应使用的图形质量。 质量级别为项目级别设置，不特定于任何一个相机。 有关详细信息，请参阅 Unity 文档中的 [优质](https://docs.unity3d.com/Manual/class-QualitySettings.html) 文章。

## <a name="see-also"></a>另请参阅

- [照相机系统 API 文档](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [创建照相机设置提供程序](create-settings-provider.md)
