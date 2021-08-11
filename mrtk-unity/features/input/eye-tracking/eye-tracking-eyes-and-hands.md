---
title: 眼睛和手
description: 如何在 MRTK 中结合使用眼部定位作为主指针和手部运动
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， EyeTracking，
ms.openlocfilehash: 37411eb344b4efae03a00bb06a31ce56182cc724d96b2cdcc008f10a66d56011
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224746"
---
# <a name="eyes-and-hands"></a>眼睛和手

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a>如何支持 _眼睛凝_ 视和 (运动&手势) 

本页介绍如何将眼动定位用作主指针与手部运动。
在 [MRTK 眼动跟踪演示](../../example-scenes/eye-tracking-examples-overview.md)中，我们介绍了使用眼睛 + 手的几个示例，例如：

- [选择](eye-tracking-target-selection.md)：查看远程全息按钮，只需执行收缩手势即可快速选择它。
- **定位 (** 文章) ：Fluently 通过简单地查看全息影像，将手指和拇指合在一起抓取它，然后用手四处移动全息影像。
- [导航](eye-tracking-navigation.md)：只需查看要放大的位置，将手指和拇指合在一起，然后拉手进行放大。

请注意，MRTK 目前采用的方式是，在距离上手部射线充当优先焦点指针。
这意味着，检测到手后，头部和眼睛凝视指针将自动抑制，并且会在说"选择"后再次可见。
但是，这可能并不是你想在距离上交互的方式，而是支持简单的"凝视和提交"交互，而与视图中的手无关。

### <a name="how-to-disable-the-hand-ray"></a>如何禁用手部射线

若要禁用手部射线指针，只需删除 Input -> Pointer MRTK _配置设置中的__"DefaultControllerPointer"。_
若要在应用中使用眼睛和手，另请确保满足使用眼 [动跟踪 的所有要求](eye-tracking-basic-setup.md)。

![如何移除手部射线](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

还可以查看如何将眼动跟踪示例包中的输入配置文件 _EyeTrackingDemoPointerProfile_ 设置为参考。

### <a name="how-to-keep-gaze-pointer-always-on"></a>如何使凝视指针始终打开

为了避免在检测到手部后自动抑制头部或眼睛凝视指针，可指定凝视以控制它是打开还是 [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 关闭。

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

请参阅 [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)

---
[返回到"MixedRealityToolkit 中的眼动跟踪"](eye-tracking-main.md)
