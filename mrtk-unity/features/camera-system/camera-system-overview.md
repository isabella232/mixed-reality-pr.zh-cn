---
title: 照相机系统概述
description: MRTK 中相机系统的登陆页
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 相机，
ms.openlocfilehash: 3c9bdbc96688c4df6ee2f39be2c8bb2023817f9081b5366308ba8b4c2590568d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211445"
---
# <a name="camera-system-overview"></a>照相机系统概述

借助相机系统，Microsoft Mixed Reality Toolkit配置和优化应用程序的相机，以用于混合现实应用程序。 使用相机系统，可以编写应用程序来支持不透明的 (例如：虚拟现实) 和透明 (，例如 Microsoft HoloLens) 设备，无需编写代码来区分和适应每种类型的显示器。

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

![相机设置提供程序](../images/camera-system/CameraSettingsProviders.png)

相机设置提供程序启用相机的平台特定配置。 这些设置可能包括自定义配置步骤和/或组件。

可以通过单击"添加相机"设置 **提供程序"按钮添加** 提供程序。 可以通过单击提供程序名称右边的按钮 **-** 来删除它们。

> [!Note]
> 并非所有平台都需要相机设置提供程序。 如果没有与运行应用程序的平台兼容的提供程序，Microsoft Mixed Reality Toolkit将应用基本默认值。

### <a name="display-settings"></a>显示设置

![相机显示设置](../images/camera-system/CameraDisplaySettings.png)

为不透明对象指定显示设置 (例如：虚拟现实) 和 (显示Microsoft HoloLens) 设置。 相机是使用这些设置运行时配置的。

**近剪辑**

近剪贴平面最接近虚拟对象与相机的距离（以米为单位）并且仍可呈现。 为获得最大的用户舒适感，建议将此值大于零。 上图包含各种设备上已发现的舒适值。

**Far Clip**

最远的剪辑平面是虚拟对象可以到达相机且仍可呈现的最远（以米为单位）。 对于透明设备，建议此值相对接近，因为不要过度超过现实世界空间，并破坏应用程序的沉浸式质量。

**清除标志**

清除标志值指示绘制显示器时如何清除显示。 对于虚拟现实体验，此值通常设置为 Skybox。 对于透明显示，建议将此选项设置为"颜色"。

**背景色**

如果未将清除标志设置为 Skybox，将显示背景色属性。

**质量设置**

质量设置值指示 Unity 在呈现场景时应该使用的图形质量。 质量级别是项目级别设置，并不特定于任何一个相机。 有关详细信息，请参阅 Unity [文档中的质量](https://docs.unity3d.com/Manual/class-QualitySettings.html) 文章。

## <a name="see-also"></a>另请参阅

- [相机系统 API 文档](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [创建相机设置提供程序](create-settings-provider.md)
