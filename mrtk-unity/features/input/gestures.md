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
# <a name="gestures"></a><span data-ttu-id="24f0a-104">笔势</span><span class="sxs-lookup"><span data-stu-id="24f0a-104">Gestures</span></span>

<span data-ttu-id="24f0a-105">手势是基于人类手的输入事件。</span><span class="sxs-lookup"><span data-stu-id="24f0a-105">Gestures are input events based on human hands.</span></span> <span data-ttu-id="24f0a-106">有两种类型的设备在 MRTK 中引发手势输入事件：</span><span class="sxs-lookup"><span data-stu-id="24f0a-106">There are two types of devices that raise gesture input events in MRTK:</span></span>

- <span data-ttu-id="24f0a-107">Windows Mixed Reality设备，例如HoloLens。</span><span class="sxs-lookup"><span data-stu-id="24f0a-107">Windows Mixed Reality devices such as HoloLens.</span></span> <span data-ttu-id="24f0a-108">本文介绍" (") 和按住手势的收缩运动。</span><span class="sxs-lookup"><span data-stu-id="24f0a-108">This describes pinching motions ("Air Tap") and tap-and-hold gestures.</span></span>

  <span data-ttu-id="24f0a-109">有关手势HoloLens，请参阅Windows Mixed Reality[手势文档](/windows/mixed-reality/gestures)。</span><span class="sxs-lookup"><span data-stu-id="24f0a-109">For more information on HoloLens gestures see the [Windows Mixed Reality Gestures documentation](/windows/mixed-reality/gestures).</span></span>

  <span data-ttu-id="24f0a-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)包装[Unity XR。Wsa。Input.GestureRecognizer，](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html)用于从设备HoloLens Unity 的手势事件。</span><span class="sxs-lookup"><span data-stu-id="24f0a-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) wraps the [Unity XR.WSA.Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) to consume Unity's gesture events from HoloLens devices.</span></span>

- <span data-ttu-id="24f0a-111">触摸屏设备。</span><span class="sxs-lookup"><span data-stu-id="24f0a-111">Touch screen devices.</span></span>

  <span data-ttu-id="24f0a-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) 包装支持 [物理触摸屏的 Unity Touch](https://docs.unity3d.com/ScriptReference/Touch.html) 类。</span><span class="sxs-lookup"><span data-stu-id="24f0a-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) wraps the [Unity Touch class](https://docs.unity3d.com/ScriptReference/Touch.html) that supports physical touch screens.</span></span>

<span data-ttu-id="24f0a-113">这两个输入源都使用 _手势设置_ 配置文件将 Unity 的 Touch 和 Gesture 事件分别转换为 MRTK 的 [输入操作](input-actions.md)。</span><span class="sxs-lookup"><span data-stu-id="24f0a-113">Both of these input sources use the _Gesture Settings_ profile to translate Unity's Touch and Gesture events respectively into MRTK's [Input Actions](input-actions.md).</span></span> <span data-ttu-id="24f0a-114">此配置文件可以在"输入系统 _"设置下_ 找到。</span><span class="sxs-lookup"><span data-stu-id="24f0a-114">This profile can be found under the _Input System Settings_ profile.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a><span data-ttu-id="24f0a-115">手势事件</span><span class="sxs-lookup"><span data-stu-id="24f0a-115">Gesture events</span></span>

<span data-ttu-id="24f0a-116">通过实现其中一个笔势处理程序接口接收笔势事件：或 ([`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) 事件处理程序表 [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1)) 。 [](input-events.md)</span><span class="sxs-lookup"><span data-stu-id="24f0a-116">Gesture events are received by implementing one of the gesture handler interfaces: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) or [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (see table of [event handlers](input-events.md)).</span></span>

<span data-ttu-id="24f0a-117">有关 [笔势](#example-scene) 事件处理程序的示例实现，请参阅示例场景。</span><span class="sxs-lookup"><span data-stu-id="24f0a-117">See [Example Scene](#example-scene) for an example implementation of a gesture event handler.</span></span>

<span data-ttu-id="24f0a-118">实现泛型版本时 *，OnGestureCompleted* 和 *OnGestureUpdated* 事件可以接收以下类型的类型化数据：</span><span class="sxs-lookup"><span data-stu-id="24f0a-118">When implementing the generic version, the *OnGestureCompleted* and *OnGestureUpdated* events can receive typed data of the following types:</span></span>

- <span data-ttu-id="24f0a-119">`Vector2` - 2D 位置手势。</span><span class="sxs-lookup"><span data-stu-id="24f0a-119">`Vector2` - 2D position gesture.</span></span> <span data-ttu-id="24f0a-120">由触摸屏生成以通知其 [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) 。</span><span class="sxs-lookup"><span data-stu-id="24f0a-120">Produced by touch screens to inform of their [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html).</span></span>
- <span data-ttu-id="24f0a-121">`Vector3` - 3D 位置手势。</span><span class="sxs-lookup"><span data-stu-id="24f0a-121">`Vector3` - 3D position gesture.</span></span> <span data-ttu-id="24f0a-122">由 HoloLens生成，以通知：</span><span class="sxs-lookup"><span data-stu-id="24f0a-122">Produced by HoloLens to inform of:</span></span>
  - <span data-ttu-id="24f0a-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) 操作事件的</span><span class="sxs-lookup"><span data-stu-id="24f0a-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) of a manipulation event</span></span>
  - <span data-ttu-id="24f0a-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) 导航事件的</span><span class="sxs-lookup"><span data-stu-id="24f0a-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) of a navigation event</span></span>
- <span data-ttu-id="24f0a-125">`Quaternion` - 3D 旋转手势。</span><span class="sxs-lookup"><span data-stu-id="24f0a-125">`Quaternion` - 3D rotation gesture.</span></span> <span data-ttu-id="24f0a-126">可用于自定义输入源，但目前不由任何现有输入源生成。</span><span class="sxs-lookup"><span data-stu-id="24f0a-126">Available to custom input sources but not currently produced by any of the existing ones.</span></span>
- <span data-ttu-id="24f0a-127">`MixedRealityPose` - 组合的 3D 位置/旋转手势。</span><span class="sxs-lookup"><span data-stu-id="24f0a-127">`MixedRealityPose` - Combined 3D position/rotation gesture.</span></span> <span data-ttu-id="24f0a-128">可用于自定义输入源，但目前不由任何现有输入源生成。</span><span class="sxs-lookup"><span data-stu-id="24f0a-128">Available to custom input sources but not currently produced by any of the existing ones.</span></span>

## <a name="order-of-events"></a><span data-ttu-id="24f0a-129">事件顺序</span><span class="sxs-lookup"><span data-stu-id="24f0a-129">Order of events</span></span>

<span data-ttu-id="24f0a-130">事件有两个主体链，具体取决于用户输入：</span><span class="sxs-lookup"><span data-stu-id="24f0a-130">There are two principal chains of events, depending on user input:</span></span>

- <span data-ttu-id="24f0a-131">"保留"：</span><span class="sxs-lookup"><span data-stu-id="24f0a-131">"Hold":</span></span>
    1. <span data-ttu-id="24f0a-132">按住点击：</span><span class="sxs-lookup"><span data-stu-id="24f0a-132">Hold tap:</span></span>
        - <span data-ttu-id="24f0a-133">启动 _操作_</span><span class="sxs-lookup"><span data-stu-id="24f0a-133">start _Manipulation_</span></span>
    1. <span data-ttu-id="24f0a-134">按住点击超出[HoldStartDuration：](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)</span><span class="sxs-lookup"><span data-stu-id="24f0a-134">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="24f0a-135">start _Hold_</span><span class="sxs-lookup"><span data-stu-id="24f0a-135">start _Hold_</span></span>
    1. <span data-ttu-id="24f0a-136">发布点击：</span><span class="sxs-lookup"><span data-stu-id="24f0a-136">Release tap:</span></span>
        - <span data-ttu-id="24f0a-137">完成 _保留_</span><span class="sxs-lookup"><span data-stu-id="24f0a-137">complete _Hold_</span></span>
        - <span data-ttu-id="24f0a-138">完成 _操作_</span><span class="sxs-lookup"><span data-stu-id="24f0a-138">complete _Manipulation_</span></span>

- <span data-ttu-id="24f0a-139">"移动"：</span><span class="sxs-lookup"><span data-stu-id="24f0a-139">"Move":</span></span>
    1. <span data-ttu-id="24f0a-140">按住点击：</span><span class="sxs-lookup"><span data-stu-id="24f0a-140">Hold tap:</span></span>
        - <span data-ttu-id="24f0a-141">启动 _操作_</span><span class="sxs-lookup"><span data-stu-id="24f0a-141">start _Manipulation_</span></span>
    1. <span data-ttu-id="24f0a-142">按住点击超出[HoldStartDuration：](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)</span><span class="sxs-lookup"><span data-stu-id="24f0a-142">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="24f0a-143">start _Hold_</span><span class="sxs-lookup"><span data-stu-id="24f0a-143">start _Hold_</span></span>
    1. <span data-ttu-id="24f0a-144">将手移到 [NavigationStartThreshold 之外](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold)：</span><span class="sxs-lookup"><span data-stu-id="24f0a-144">Move hand beyond [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span></span>
        - <span data-ttu-id="24f0a-145">取消 _保留_</span><span class="sxs-lookup"><span data-stu-id="24f0a-145">cancel _Hold_</span></span>
        - <span data-ttu-id="24f0a-146">启动 _导航_</span><span class="sxs-lookup"><span data-stu-id="24f0a-146">start _Navigation_</span></span>
    1. <span data-ttu-id="24f0a-147">发布点击：</span><span class="sxs-lookup"><span data-stu-id="24f0a-147">Release tap:</span></span>
        - <span data-ttu-id="24f0a-148">完成 _操作_</span><span class="sxs-lookup"><span data-stu-id="24f0a-148">complete _Manipulation_</span></span>
        - <span data-ttu-id="24f0a-149">完成 _导航_</span><span class="sxs-lookup"><span data-stu-id="24f0a-149">complete _Navigation_</span></span>

## <a name="example-scene"></a><span data-ttu-id="24f0a-150">示例场景</span><span class="sxs-lookup"><span data-stu-id="24f0a-150">Example scene</span></span>

<span data-ttu-id="24f0a-151">**HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scene) 场景演示如何使用指针 Result 在命中位置生成对象。</span><span class="sxs-lookup"><span data-stu-id="24f0a-151">The **HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) scene shows how to use the pointer Result to spawn an object at the hit location.</span></span>

<span data-ttu-id="24f0a-152"> (`GestureTester` Assets/MRTK/Examples/Demos/HandTracking/Script) 脚本是一个示例实现，用于通过 GameObjects 可视化手势事件。</span><span class="sxs-lookup"><span data-stu-id="24f0a-152">The `GestureTester` (Assets/MRTK/Examples/Demos/HandTracking/Script) script is an example implementation to visualize gesture events via GameObjects.</span></span> <span data-ttu-id="24f0a-153">处理程序函数更改指示器对象的颜色，并显示场景中文本对象中最后记录的事件。</span><span class="sxs-lookup"><span data-stu-id="24f0a-153">The handler functions change the color of indicator objects and display the last recorded event in text objects in the scene.</span></span>
