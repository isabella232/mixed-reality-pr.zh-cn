---
title: 眼动跟踪眼睛和手
description: 如何在 MRTK 中结合使用眼部定位作为主指针和手部运动
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， EyeTracking，
ms.openlocfilehash: c9d5f23610d821aa1e50a3217a4be736601dc14d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143998"
---
# <a name="eyes--hand-interaction"></a><span data-ttu-id="8047f-104">眼睛 + 手部交互</span><span class="sxs-lookup"><span data-stu-id="8047f-104">Eyes + hand interaction</span></span>

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a><span data-ttu-id="8047f-105">如何支持 _眼睛凝_ 视和 (运动&手势) </span><span class="sxs-lookup"><span data-stu-id="8047f-105">How to support _look + hand motions_ (eye gaze & hand gestures)</span></span>

<span data-ttu-id="8047f-106">本页介绍如何将眼动定位用作主指针与手部运动。</span><span class="sxs-lookup"><span data-stu-id="8047f-106">This page explains how to use eye targeting as a primary pointer in combination with hand motions.</span></span>
<span data-ttu-id="8047f-107">在 [MRTK 眼动跟踪演示](../../example-scenes/eye-tracking-examples-overview.md)中，我们介绍了使用眼睛 + 手的几个示例，例如：</span><span class="sxs-lookup"><span data-stu-id="8047f-107">In our [MRTK eye tracking demos](../../example-scenes/eye-tracking-examples-overview.md), we describe several examples for using eyes + hands, for example:</span></span>

- <span data-ttu-id="8047f-108">[选择](eye-tracking-target-selection.md)：查看远程全息按钮，只需执行收缩手势即可快速选择它。</span><span class="sxs-lookup"><span data-stu-id="8047f-108">[Selection](eye-tracking-target-selection.md): Looking at distant holographic button and simply performing a pinch gesture to quickly select it.</span></span>
- <span data-ttu-id="8047f-109">**定位 (** 文章) ：Fluently 通过简单地查看全息影像，将手指和拇指合在一起抓取它，然后用手四处移动全息影像。</span><span class="sxs-lookup"><span data-stu-id="8047f-109">**Positioning (this article)**: Fluently move a hologram across your scene by simply looking at it, pinching your index finger and thumb together to grab it and then move it around using your hand.</span></span>
- <span data-ttu-id="8047f-110">[导航](eye-tracking-navigation.md)：只需查看要放大的位置，将手指和拇指合在一起，然后拉手进行放大。</span><span class="sxs-lookup"><span data-stu-id="8047f-110">[Navigation](eye-tracking-navigation.md): Simply look at a location you want to zoom in, pinch your index finger and thumb together and _pull_ your hand toward you to zoom in.</span></span>

<span data-ttu-id="8047f-111">请注意，MRTK 目前采用的方式是，在距离上手部射线充当优先焦点指针。</span><span class="sxs-lookup"><span data-stu-id="8047f-111">Please note that MRTK is currently designed in a way that at a distance hand rays act as the prioritized focus pointers.</span></span>
<span data-ttu-id="8047f-112">这意味着，检测到手后，头部和眼睛凝视指针将自动抑制，并且会在说"选择"后再次可见。</span><span class="sxs-lookup"><span data-stu-id="8047f-112">This means that the head and eye gaze pointers will automatically be suppressed once a hand is detected and will become visible again after saying "Select".</span></span>
<span data-ttu-id="8047f-113">但是，这可能并不是你想在距离上交互的方式，而是支持简单的"凝视和提交"交互，而与视图中的手无关。</span><span class="sxs-lookup"><span data-stu-id="8047f-113">However, this may not be the way you would like to interact at a distance and rather favor a simple _'gaze and commit'_ interaction independent of the presence of hands in your view.</span></span>

### <a name="how-to-disable-the-hand-ray"></a><span data-ttu-id="8047f-114">如何禁用手部射线</span><span class="sxs-lookup"><span data-stu-id="8047f-114">How to disable the hand ray</span></span>

<span data-ttu-id="8047f-115">若要禁用手部射线指针，只需删除 Input -> Pointer MRTK _配置设置中的__"DefaultControllerPointer"。_</span><span class="sxs-lookup"><span data-stu-id="8047f-115">To disable the hand ray pointer, simply remove the _'DefaultControllerPointer'_ in your _Input -> Pointer_ MRTK configuration setting.</span></span>
<span data-ttu-id="8047f-116">若要在应用中使用眼睛和手，另请确保满足使用眼 [动跟踪 的所有要求](eye-tracking-basic-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="8047f-116">To use eyes and hands as described above in your app, please also make sure that you meet all of the [requirements for using eye tracking](eye-tracking-basic-setup.md).</span></span>

![如何移除手部射线](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

<span data-ttu-id="8047f-118">还可以查看如何将眼动跟踪示例包中的输入配置文件 _EyeTrackingDemoPointerProfile_ 设置为参考。</span><span class="sxs-lookup"><span data-stu-id="8047f-118">You can also check out, how the input profile _EyeTrackingDemoPointerProfile_ from the eye tracking sample package is set up as a reference.</span></span>

### <a name="how-to-keep-gaze-pointer-always-on"></a><span data-ttu-id="8047f-119">如何使凝视指针始终打开</span><span class="sxs-lookup"><span data-stu-id="8047f-119">How to keep gaze pointer always on</span></span>

<span data-ttu-id="8047f-120">若要避免在检测到手后，会自动抑制 head 或眼睛眼睛指针， [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 可以指定注视来控制其是打开还是关闭。</span><span class="sxs-lookup"><span data-stu-id="8047f-120">To avoid having the head or eye gaze pointers automatically suppressed once a hand is detected, the gaze [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) can be specified to control whether it should be on or off.</span></span>

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="8047f-121">请参阅 [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span><span class="sxs-lookup"><span data-stu-id="8047f-121">See [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span></span>

---
[<span data-ttu-id="8047f-122">返回 "MixedRealityToolkit" 中的眼睛跟踪</span><span class="sxs-lookup"><span data-stu-id="8047f-122">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
