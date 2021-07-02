---
title: 滑块
description: 滑杆 MRTK 概述
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，滑杆，
ms.openlocfilehash: c8a2b6c377762918bfff79008ab34d3dfe4e20bb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177500"
---
# <a name="sliders"></a>滑块

![滑块示例](../images/slider/MRTK_UX_Slider_Main.jpg)

滑块是用户界面组件，使您可以通过将滑块移动到轨道上来持续更改值。目前，可以通过直接或距离方向直接抓取滑块来移动挤压滑块。 滑块在 AR 和 VR 上工作，使用运动控制器、手或手势 + 语音。

## <a name="example-scene"></a>示例场景

可以在中的 **SliderExample** 场景中找到示例 `MRTK/Examples/Demos/UX/Slider/Scenes/` 。

## <a name="how-to-use-sliders"></a>如何使用滑块

将 **PinchSlider** prefab 拖放到场景层次结构中。 如果要修改或创建自己的滑块，请记住执行以下操作：

- 请确保拇指对象上有一个碰撞器。 在 PinchSlider prefab 中，碰撞器位于 `SliderThumb/Button_AnimationContainer/Slider_Button`
- 如果你希望能够抓住附近的滑块，请确保包含碰撞器的对象在其上还有近乎交互的 Grabbable 组件。

我们还建议使用以下层次结构

- PinchSlider-包含 sliderComponent
  - TouchCollider-包含滑块的整个可选择区域的碰撞器。 启用 "对齐位置" 行为。
  - SliderThumb-包含可移动的拇指
  - TrackVisuals-包含轨迹和任何其他视觉对象
  - OtherVisuals-包含任何其他视觉对象

## <a name="slider-events"></a>滑块事件

滑块公开了以下事件：

- OnValueUpdated-每当滑块值改变时调用
- OnInteractionStarted-用户获取滑块时调用
- OnInteractionEnded-用户释放滑块时调用
- OnHoverEntered-当用户的手动/控制器使用近距离或远交互方式悬停在滑块上时调用。
- OnHoverExited-当用户的手/控制器不再位于滑块附近时调用。

## <a name="configuring-slider-bound-and-axis"></a>配置滑块绑定和轴

您可以通过移动场景中的句柄直接移动滑块的起点和终点：

![滑杆配置](../images/sliders/MRTK_Sliders_Setup.png)

还可以通过 " _滑块轴_ " 字段在滑块的本地空间) 指定轴 (

如果您无法使用该句柄，则可以改为通过 " _滑块起始距离_ " 和 " _滑块结束距离_ " 字段指定滑块的起点和终点。 它们将滑块的开始/结束位置指定为以局部坐标形式从滑块中心的距离。 这意味着，一旦您所需的滑块开始和结束距离，您可以将滑块缩放到更小或更大，而无需更新开始和结束距离。

## <a name="inspector-properties"></a>检查器属性

**拇指根** 包含滑块的 gameobject。

**对齐位置** 此滑块是否与滑块上指定的位置对齐

**为可触摸** 此滑块是否可通过触摸事件控制

**拇指碰撞** 器控制滑块的碰撞器

**可触摸碰撞** 器对齐位置为 true 时，可接触或选中的滑块区域。

**滑块值** 滑块的值。

**使用滑块步骤划分** 控制是在步骤中还是连续递增此滑块。

**滑块步骤划分** 启用滑块步骤划分后，滑块拆分到的细分数。

**跟踪视觉对象** 包含沿滑块方向的所需跟踪视觉对象的 gameobject。

**刻度线** Gameobject，其中包含沿滑块方向的所需刻度线。

**Thumb 视觉对象** 包含沿滑块方向的所需 thumb 视觉对象的 gameobject。

**滑块轴** 滑块沿其移动的轴。

**滑块开始距离** 滑块轨道的起始位置，与中心沿滑块轴的距离（以本地空间单位为单位）。

**滑块结束距离** 滑块轨迹结束的位置，与中心沿滑块轴的距离（以本地空间单位为单位）。

当用户在编辑器中更新滑块轴值时，如果指定了 "跟踪视觉对象" 或 "滴答视觉对象"，则会更新其转换。
具体而言，将重置其本地位置，并将其本地旋转设置为与滑块轴方向匹配。
未修改其缩放比例。
如果刻度线具有网格对象集合组件，则会相应地更新 Layout 和 CellWidth 或 CellHeight 以匹配滑块轴。

## <a name="example-slider-configurations"></a>示例滑块配置

靠齐到位置连续滑块的连续滑块 ![](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)

带有对齐位置的步骤滑块

![步骤滑块](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

触摸滑块

![触摸滑块](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)
