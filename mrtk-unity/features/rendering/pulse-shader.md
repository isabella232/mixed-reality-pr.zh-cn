---
title: 脉冲着色器
description: MRTK 中的脉冲着色器的说明。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: add3aaa2a98ca2ddc1f60b0307a3defed3236d9a2c09aa70ea2d12b2d9638eba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228378"
---
# <a name="pulse-shader"></a>脉冲着色器

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

使用脉冲着色器对表面重建、有向右网格或任何其他网格的视觉脉冲效果进行动画处理。

## <a name="shader-and-material"></a>着色器和材料

以下材料使用 **SR_Triangles** 着色器。 可以配置各种选项，如填充颜色、线条颜色和脉冲颜色。

- **MRTK_Pulse_SpatialMeshBlue** 
- **MRTK_Pulse_SpatialMeshPurple** 
- **MRTK_Pulse_ArticulatedHandMeshBlue** 
- **MRTK_Pulse_ArticulatedHandMeshPurple** 

## <a name="prerequisites"></a>先决条件

对于空间网格示例，请确保在 MixedRealityToolkit 对象（> 空间感知配置文件设置 >）下分配 MRTK_Pulse_SpatialMeshBlue 的 MRTK_Pulse_SpatialMeshPurple。

对于手写网格示例，请确保在 ArticulatedHandMesh 中分配 MRTK_Pulse_ArticulatedHandMeshBlue MRTK_Pulse_ArticulatedHandMeshPurple。 prefab，这本身应在 MRTK 设置-> 输入-> 手动跟踪-> 手写网格 Prefab 中分配。

## <a name="how-it-works"></a>工作原理

手写着色器使用 Uv-11 来沿手写网格地图脉冲，并使手腕淡出。 Surface 重构着色器使用顶点位置来映射脉冲。

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>空间网格示例-PulseShaderSpatialMeshExample

与 HoloLens 2 shell 体验类似，你可以通过使用手型来指向并使用手型来在空间网格上生成影响效果。 示例场景包含 ExampleSpatialMesh 对象，该对象是适用于 Unity 游戏模式的测试空间网格数据。 此对象将在设备上被禁用和隐藏。

如果为 true，则 **PulseShaderSpatialMeshHandler** 脚本将在点位置对空间网格生成脉冲效果 `PulseOnSelect` 。 `Auto Pulse`对于重复动画，属性也可在材料本身中设置为 true。  在示例场景中，此脚本附加到 PulseShaderSpatialMeshParent prefab。  通过运行时空间网格 Prefab 属性在空间感知配置文件下引用此 prefab。 在运行时，PulseShaderSpatialMeshParent prefab 和将实例化并添加到空间网格层次结构中 (仅在设备上，不能在编辑器) 中观察到此行为。

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>手写网格示例-PulseShaderHandMeshExample

此示例场景演示了使用脉冲着色器的手写网格可视化。 HoloLens 设备检测到手时，将触发一次脉冲动画。 此视觉反馈可提高用户的交互置信度。 

**PulseShaderHandMeshHandler** 脚本会对分配的材料生成脉冲效果。 默认情况下，选中 "检测到手动脉冲"。
