---
title: 空间网格可视化
description: 了解设备如何使用空间网格了解物理环境。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 混合现实，HoloLens，UI 控制，交互，UI，ux，UX 设计，空间 UI，空间交互，三维 UI，三维 UX，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包
ms.openlocfilehash: ffa13da6762b803ba2a3f370308ac2af65164ecf
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848194"
---
# <a name="spatial-mesh"></a>空间网格

![空间网格](images/MRTK_PulseShader_SpatialMesh.gif)

用户了解设备如何通过空间网格可视化了解并了解物理环境。 适当的空间网格可视化可以在提供空间上下文的同时创建不知和神奇体验。  

## <a name="design-guideline"></a>设计准则

允许用户集中关注内容并与之交互，这一点很重要。 背景中的空间网格的连续可视化可能会分散注意力。 建议在初始启动时，或在用户清楚地显示要查看环境网格的情况下，在初始启动时将环境可视化，或在用户清楚地显示环境网格。 可在混合现实门户中查看此行为。
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>MRTK 中的空间网格可视化 (适用于 Unity 的混合现实工具包) 

MRTK 提供了多个材料来实现空间网格可视化。

- **MRTK_Wireframe，MRTK_Wireframe** 的：默认静态空间网格材料，其中显示不带动画的网格轮廓。 此材料可用于调试目的，因为它显示了整个空间网格几何。 不过，不建议在生产环境中使用。
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction** 材料：此材料在空间网格上提供动画脉冲效果。 您可以使用此材料在特定时刻或用户的点击输入中直观显示环境。 有关示例，请参阅 **PulseShaderExamples** 场景。
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* 有关详细信息，请参阅 [MRTK-空间感知](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) 和 [MRTK 着色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html)。

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
