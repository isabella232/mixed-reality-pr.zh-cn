---
title: 脉冲着色器
description: MRTK 中脉冲着色器的说明。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: e03c021689b6701b86ae25ba9fa253ece1368428
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144947"
---
# <a name="pulse-shader"></a>脉冲着色器

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

使用脉冲着色器对表面重建、表达手部网格或任何其他网格上的视觉脉冲效果进行动画处理。

## <a name="shader-and-material"></a>着色器与材料

以下材料使用 **SR_Triangles** 器。 可以配置各种选项，例如填充颜色、线条颜色和脉冲颜色。

- **MRTK_Pulse_SpatialMeshBlue.mat** 
- **MRTK_Pulse_SpatialMeshPurple.mat** 
- **MRTK_Pulse_ArticulatedHandMeshBlue.mat** 
- **MRTK_Pulse_ArticulatedHandMeshPurple.mat** 

## <a name="prerequisites"></a>先决条件

对于空间网格示例，请确保在 MRTK 设置 -> 空间感知 -> 显示设置 ->可见材料下分配 MRTK_Pulse_ArticulatedHandMeshBlue.mat 或 MRTK_Pulse_ArticulatedHandMeshPurple.mat。

对于手部网格示例，请确保在"HandMesh.prefab"中分配 MRTK_Pulse_SpatialMeshBlue.mat 或 MRTK_Pulse_SpatialMeshPurple.mat，它本身应分配给 MRTK 设置 -> 输入 -> 手部跟踪 -> 手部网格预制。

## <a name="how-it-works"></a>工作原理

手部网格着色器使用 UV 沿手部网格映射脉冲，并淡出阴影。 表面重建着色器使用顶点位置来映射脉冲。

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>空间网格示例 - PulseShaderSpatialMeshExample.unity

与HoloLens 2的 shell 体验类似，可以使用手部射线进行指向和敲击，以在空间网格上产生脉冲效果。 示例场景包含 ExampleSpatialMesh 对象，该对象是 Unity 游戏模式的测试空间网格数据。 此对象将在设备上禁用和隐藏。

**如果 为 true，PulseShaderSpatialMeshHandler.cs** 脚本在命中点位置的空间网格上生成 `PulseOnSelect` 脉冲效果。 `Auto Pulse`对于重复动画，属性也可在材料本身中设置为 true。  在示例场景中，此脚本附加到 PulseShaderSpatialMeshParent prefab。  通过运行时空间网格 Prefab 属性在空间感知配置文件下引用此 prefab。 在运行时，PulseShaderSpatialMeshParent prefab 和将实例化并添加到空间网格层次结构中 (仅在设备上，不能在编辑器) 中观察到此行为。

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>手写网格示例-PulseShaderHandMeshExample

此示例场景演示了使用脉冲着色器的手写网格可视化。 当 HoloLens 设备检测到手时，将触发一次脉冲动画。 此视觉反馈可提高用户的交互置信度。 

**PulseShaderHandMeshHandler** 脚本会对分配的材料生成脉冲效果。 默认情况下，选中 "检测到手动脉冲"。
