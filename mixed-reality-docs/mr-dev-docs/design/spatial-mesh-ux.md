---
title: 空间网格可视化
description: 了解 MRTK 中空间网格可视化的设计准则和物理环境理解。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 混合现实， HoloLens， UI 控件， 交互， ui， ux， UX 设计， 空间 UI， 空间交互， 3D UI， 3D UX， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， HoloLens， MRTK， 混合现实工具包
ms.openlocfilehash: 5bdcba60f38ac67bbf0f394337735f4a2d4ec423
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600626"
---
# <a name="spatial-mesh"></a>空间网格

![空间网格](images/MRTK_PulseShader_SpatialMesh.gif)

用户通过空间网格可视化了解设备如何感知和理解物理环境。 适当的空间网格可视化效果可以在提供空间上下文的同时创建一种有趣而有趣的体验。  

## <a name="design-guideline"></a>设计准则

必须允许用户专注于内容并与之交互。 在后台连续可视化空间网格可能会分散注意力。 建议尽量少地可视化环境，只需在初始发射时显示一次，或者当用户清楚地显示他们希望通过定目标空间和空敲击空间来查看环境网格时。 可以在以下方法中观察此混合现实门户。
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>MRTK 中的空间网格 (Unity 混合现实工具包) 可视化效果

MRTK 为空间网格可视化提供了多种材料。

- **MRTK_Wireframe.mat、MRTK_Wireframe.mat：** 默认静态空间网格材料，用于显示无动画的网格轮廓。 此材料可用于调试，因为它显示了整个空间网格几何。 但是，不建议用于生产。
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction.mat：** 此材料在空间网格上提供动画脉冲效果。 可以使用此材料来可视化特定时刻的环境或用户的空敲击输入。 有关 **示例，请参阅 PulseShaderExamples.unity** 场景。
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">

* 有关详细信息，请参阅 [MRTK - 空间感知](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) 和 [MRTK - 脉冲着色器](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader)。

<br>

---

## <a name="see-also"></a>另请参阅

* [光标](cursors.md)
* [手部射线](point-and-commit.md)
* [Button](button.md)
* [可交互对象](interactable-object.md)
* [边界框和应用栏](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [手动菜单](hand-menu.md)
* [追踪菜单](near-menu.md)
* [对象集合](object-collection.md)
* [语音命令](voice-input.md)
* [键盘](keyboard.md)
* [工具提示](tooltip.md)
* [平板](slate.md)
* [滑块](slider.md)
* [着色器](shader.md)
* [公告和尾随](billboarding-and-tag-along.md)
* [显示进度](progress.md)
* [表面磁吸](surface-magnetism.md)