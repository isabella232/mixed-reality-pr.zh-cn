---
title: Unity AR 照相机设置
description: 使用 MRTK 中的 AR 相机的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、混合现实、开发、MRTK、AR 相机、
ms.openlocfilehash: e1c032805bc4b733cfcc51e1ceac5096c73715cf
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121195"
---
# <a name="unity-ar-camera-settings-provider"></a>Unity AR 照相机设置提供程序

Unity AR 照相机设置提供程序是一个试验性的 MRTK 组件，使混合现实应用程序能够在 Android 和 iOS 设备上运行。

## <a name="unity-ar-camera-settings-provider-options"></a>Unity AR 照相机设置提供程序选项

![Unity AR 照相机设置配置](../images/camera-system/UnityArSettingsConfiguration.png)

有关如何将提供程序添加到场景中的指南： [如何为 iOS 和 Android 配置 MRTK](../../supported-devices/using-ar-foundation.md)

### <a name="tracking-settings"></a>跟踪设置

Unity AR 照相机设置提供程序允许配置有关如何执行跟踪的选项。 这些设置特定于 Unity AR 相机设置提供程序实现。

**姿势源**

姿势源定义增加的现实跟踪姿势的可用类型。 通常，这些值映射到正在运行应用程序的设备的组件。

下表介绍了可用的选项。

| 选项 | 说明 |
| --- | --- |
| Center | 头设备的中心眼。 |
| 彩色照相机 | 移动设备的彩色相机。 |
| 头 | 打印头上架的设备，通常略微大于中心眼。 |
| 左眼 | 打印头装入设备的左侧。 |
| 左姿势 | 左侧控制器的构成。 |
| 右眼 | 头设备的正确使用。 |
| 右姿势 | 右手控制器会带来。 |

"姿势 source" 的默认值为 " **彩色相机**"，用于在移动设备（如电话或平板电脑）上启用透明显示。

**跟踪类型**

跟踪类型定义将用于跟踪的姿势 () 部分。

下表介绍了可用的选项。

| 选项 | 说明 |
| --- | --- |
| 位置 | 设备的位置。 |
| 旋转 | 设备的旋转。 |
| 旋转和位置 | 设备的位置和旋转。 |

跟踪类型的默认值为 " **旋转" 和 "位置**"，以启用最丰富的跟踪体验。

**更新类型**

更新类型定义在帧处理过程中，将对姿势数据进行采样。

下表介绍了可用的选项。

| 选项 | 说明 |
| --- | --- |
| 呈现之前 | 在呈现之前。 |
| 更新 | 在框架的更新阶段。 |
| 在呈现之前更新 | 在更新阶段和渲染之前。 |

跟踪类型的默认值为 **Update 和 Render 之前**，以启用最小跟踪延迟。

## <a name="see-also"></a>另请参阅

- [照相机系统概述](camera-system-overview.md)
- [创建照相机设置提供程序](create-settings-provider.md)
