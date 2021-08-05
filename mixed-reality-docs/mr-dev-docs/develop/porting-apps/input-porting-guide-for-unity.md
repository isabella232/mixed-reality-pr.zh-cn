---
title: Unity 的输入移植指南
description: 了解如何在 Unity 中处理Windows Mixed Reality输入。
author: thetuvix
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: 输入， unity， 移植
ms.openlocfilehash: b2c328152d681a4c8753e29babf0f3ece6bdc0d3f21f9df6dd8de150c3fb47f0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212075"
---
# <a name="input-porting-guide-for-unity"></a>Unity 的输入移植指南

可以使用两种方法之一将输入Windows Mixed Reality逻辑移植到一起。 第一种是使用跨多个平台的 Unity 常规 Input.GetButton/GetAxis API。 第二个Windows XR。Wsa。输入 API，为运动控制器和手部提供更丰富的HoloLens数据。

## <a name="general-inputgetbuttongetaxis-apis"></a>常规 Input.GetButton/GetAxis API

Unity 当前使用常规 Input.GetButton/Input.GetAxis API 公开 [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) 和 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)的输入。 如果应用已在使用这些 API 进行输入，则 Input.GetButton/Input.GetAxis API 是支持 Windows Mixed Reality 中运动控制器的最简单路径。 只需在输入管理器中重新映射按钮和轴。

有关详细信息，请参阅 Unity [按钮/轴映射表](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 和常见 [Unity API 的概述](../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)。

## <a name="windows-specific-xrwsainput-apis"></a>Windows XR。Wsa。输入 API

如果应用已针对每个平台生成自定义输入逻辑，Windows **UnityEngine.XR.WSA.Input** 命名空间中特定于 Windows 空间输入 API。 从该位置访问其他信息（例如位置准确性或源类型）后，可以告知手部和控制器HoloLens。

有关详细信息，请参阅 [UnityEngine.XR.WSA.Input API 概述](../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)。

## <a name="grip-pose-vs-pointing-pose"></a>手柄姿势与指向姿势

Windows Mixed Reality支持不同外形系数的动作控制器。 每个控制器的设计在用户手部位置与应用在呈现控制器时应该用于指向的自然"向前"方向之间的关系有所不同。

为了更好地表示这些控制器，可以针对每个交互源调查两种类型的姿势：

* 手柄 **姿势**，表示手部检测到的手的HoloLens或持有运动控制器的手部的位置。
    * 在沉浸式头戴显示设备中，此姿势最适用于呈现用户手部或用户手部中持有的对象，如手部或手机。
    * 手柄 **位置**：自然按住控制器时，通过向左或向右调整以将手柄中的位置居中时，手心中心。
    * 手柄 **方向的** 右轴：完全打开手形成平面 5 指姿势时，与手部正常的射线从左 (向前，从右手心向后) 
    * 手柄 **方向的向前** 轴：当你部分关闭手部时，就像按住控制器一样，指向"向前"的射线通过由非滚动手指组成的管道。
    * 手柄 **方向的上轴**：右侧和向前定义隐含的向上轴。
    * 可以通过 Unity 的跨供应商输入 API 或 XR 访问手柄 (**[姿势。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation**) 或特定于 Windows 的 API (**sourceState.sourcePose.TryGetPosition/Rotation，** 请求手柄姿势) 。
* 指针 **指向**，表示指向的控制器的提示。
    * 在呈现控制器模型本身时，此姿势最适合在指向 **UI** 时进行光线广播。
    * 目前，指针姿势仅通过特定于 Windows API (**sourceState.sourcePose.TryGetPosition/Rotation** 提供，请求指针) 。

这些姿势坐标全部以 Unity 世界坐标表示。

## <a name="see-also"></a>另请参阅
* [运动控制器]()。。/../design/motion-controllers.md) 
* [Unity 中的运动控制器](../unity/motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [移植指南](porting-guides.md)
