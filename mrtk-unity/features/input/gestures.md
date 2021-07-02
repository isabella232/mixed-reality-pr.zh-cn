---
title: 笔势
description: MRTK 中笔势及其事件的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 笔势，
ms.openlocfilehash: 7bbc97ab5e23a69356d523c463aa37c013d70337
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176881"
---
# <a name="gestures"></a>笔势

手势是基于人类手的输入事件。 有两种类型的设备在 MRTK 中引发手势输入事件：

- Windows Mixed Reality设备，例如HoloLens。 本文介绍" (") 和按住手势的收缩运动。

  有关手势HoloLens，请参阅Windows Mixed Reality[手势文档](/windows/mixed-reality/gestures)。

  [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)包装[Unity XR。Wsa。Input.GestureRecognizer，](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html)用于从设备HoloLens Unity 的手势事件。

- 触摸屏设备。

  [`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) 包装支持 [物理触摸屏的 Unity Touch](https://docs.unity3d.com/ScriptReference/Touch.html) 类。

这两个输入源都使用 _手势设置_ 配置文件将 Unity 的 Touch 和 Gesture 事件分别转换为 MRTK 的 [输入操作](input-actions.md)。 此配置文件可以在"输入系统 _"设置下_ 找到。

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a>手势事件

通过实现其中一个笔势处理程序接口接收笔势事件：或 ([`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) 事件处理程序表 [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1)) 。 [](input-events.md)

有关 [笔势](#example-scene) 事件处理程序的示例实现，请参阅示例场景。

实现泛型版本时 *，OnGestureCompleted* 和 *OnGestureUpdated* 事件可以接收以下类型的类型化数据：

- `Vector2` - 2D 位置手势。 由触摸屏生成以通知其 [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) 。
- `Vector3` - 3D 位置手势。 由 HoloLens生成，以通知：
  - [`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) 操作事件的
  - [`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) 导航事件的
- `Quaternion` - 3D 旋转手势。 可用于自定义输入源，但目前不由任何现有输入源生成。
- `MixedRealityPose` - 组合的 3D 位置/旋转手势。 可用于自定义输入源，但目前不由任何现有输入源生成。

## <a name="order-of-events"></a>事件顺序

事件有两个主体链，具体取决于用户输入：

- "保留"：
    1. 按住点击：
        - 启动 _操作_
    1. 按住点击超出[HoldStartDuration：](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)
        - start _Hold_
    1. 发布点击：
        - 完成 _保留_
        - 完成 _操作_

- "移动"：
    1. 按住点击：
        - 启动 _操作_
    1. 按住点击超出[HoldStartDuration：](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)
        - start _Hold_
    1. 将手移到 [NavigationStartThreshold 之外](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold)：
        - 取消 _保留_
        - 启动 _导航_
    1. 发布点击：
        - 完成 _操作_
        - 完成 _导航_

## <a name="example-scene"></a>示例场景

**HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scene) 场景演示如何使用指针 Result 在命中位置生成对象。

 (`GestureTester` Assets/MRTK/Examples/Demos/HandTracking/Script) 脚本是一个示例实现，用于通过 GameObjects 可视化手势事件。 处理程序函数更改指示器对象的颜色，并显示场景中文本对象中最后记录的事件。
