---
title: Unity 中的笔势
description: 了解如何使用 XR 和常用按钮和轴 API 通过手势输入在 Unity 中对凝视采取措施。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 手势， unity， 凝视， 输入， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， MRTK， 混合现实工具包
ms.openlocfilehash: 87666c120686547b1a07f6da41519219d4a47720
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600636"
---
# <a name="gestures-in-unity"></a><span data-ttu-id="f8961-104">Unity 中的笔势</span><span class="sxs-lookup"><span data-stu-id="f8961-104">Gestures in Unity</span></span>

<span data-ttu-id="f8961-105">在 Unity 中，有两种对凝视采取措施的关键[](../../design/gaze-and-commit.md#composite-gestures)方法[：HoloLens](gaze-in-unity.md)和沉浸式 HMD 中的手势和运动控制器。 [](../../design/motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="f8961-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="f8961-106">可以通过 Unity 中的相同 API 访问两个空间输入源的数据。</span><span class="sxs-lookup"><span data-stu-id="f8961-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="f8961-107">Unity 提供两种主要方法来访问空间输入数据Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="f8961-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="f8961-108">常见的 *Input.GetButton/Input.GetAxis* API 可跨多个 Unity XR SDK 工作，而特定于 Windows Mixed Reality 的 *InteractionManager/GestureRecognizer* API 则公开一组完整的空间输入数据。</span><span class="sxs-lookup"><span data-stu-id="f8961-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="f8961-109">高级复合手势 API (GestureRecognizer) </span><span class="sxs-lookup"><span data-stu-id="f8961-109">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="f8961-110">\**命名空间\*\*\*：UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="f8961-110">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="f8961-111">**类型**：GestureRecognizer、GestureSettings、InteractionSourceKind   </span><span class="sxs-lookup"><span data-stu-id="f8961-111">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="f8961-112">应用还可以识别空间输入源、点击、按住、操作和导航手势的更高级别复合手势。</span><span class="sxs-lookup"><span data-stu-id="f8961-112">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation, and Navigation gestures.</span></span> <span data-ttu-id="f8961-113">可以使用 GestureRecognizer 在手[](../../design/gaze-and-commit.md#composite-gestures)部和运动[控制器](../../design/motion-controllers.md)上识别这些复合手势。</span><span class="sxs-lookup"><span data-stu-id="f8961-113">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="f8961-114">GestureRecognizer 上的每个笔势事件都提供输入的 SourceKind，以及事件发生时的目标头射线。</span><span class="sxs-lookup"><span data-stu-id="f8961-114">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="f8961-115">某些事件提供其他上下文特定信息。</span><span class="sxs-lookup"><span data-stu-id="f8961-115">Some events provide additional context-specific information.</span></span>

<span data-ttu-id="f8961-116">使用手势识别器捕获手势只需几个步骤：</span><span class="sxs-lookup"><span data-stu-id="f8961-116">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="f8961-117">创建新的手势识别器</span><span class="sxs-lookup"><span data-stu-id="f8961-117">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="f8961-118">指定要监视的手势</span><span class="sxs-lookup"><span data-stu-id="f8961-118">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="f8961-119">订阅这些手势的事件</span><span class="sxs-lookup"><span data-stu-id="f8961-119">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="f8961-120">开始捕获手势</span><span class="sxs-lookup"><span data-stu-id="f8961-120">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="f8961-121">创建新的手势识别器</span><span class="sxs-lookup"><span data-stu-id="f8961-121">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="f8961-122">若要使用 *GestureRecognizer，* 必须已创建 *GestureRecognizer*：</span><span class="sxs-lookup"><span data-stu-id="f8961-122">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="f8961-123">指定要监视的手势</span><span class="sxs-lookup"><span data-stu-id="f8961-123">Specify which gestures to watch for</span></span>

<span data-ttu-id="f8961-124">通过 *SetRecognizableGestures* () ：</span><span class="sxs-lookup"><span data-stu-id="f8961-124">Specify which gestures you're interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="f8961-125">订阅这些手势的事件</span><span class="sxs-lookup"><span data-stu-id="f8961-125">Subscribe to events for those gestures</span></span>

<span data-ttu-id="f8961-126">订阅事件，了解你感兴趣的手势。</span><span class="sxs-lookup"><span data-stu-id="f8961-126">Subscribe to events for the gestures you're interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="f8961-127">导航和操作手势在 *GestureRecognizer* 的实例上互斥。</span><span class="sxs-lookup"><span data-stu-id="f8961-127">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="f8961-128">开始捕获手势</span><span class="sxs-lookup"><span data-stu-id="f8961-128">Start capturing gestures</span></span>

<span data-ttu-id="f8961-129">默认情况下，在调用 *StartCapturingGestures* 之前 *，GestureRecognizer* () 监视输入。</span><span class="sxs-lookup"><span data-stu-id="f8961-129">By default, a *GestureRecognizer* doesn't monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="f8961-130">如果在 *处理 StopCapturingGestures* 的帧之前执行了输入，则调用 *StopCapturingGestures ()* 后，可能会生成笔势 () 事件。</span><span class="sxs-lookup"><span data-stu-id="f8961-130">It's possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="f8961-131">*GestureRecognizer* 将记住它在上一帧中是打开还是关闭，而该帧实际发生手势，因此，根据此帧的凝视目标启动和停止手势监视是可靠的。</span><span class="sxs-lookup"><span data-stu-id="f8961-131">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it's reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="f8961-132">停止捕获手势</span><span class="sxs-lookup"><span data-stu-id="f8961-132">Stop capturing gestures</span></span>

<span data-ttu-id="f8961-133">停止手势识别：</span><span class="sxs-lookup"><span data-stu-id="f8961-133">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="f8961-134">删除手势识别器</span><span class="sxs-lookup"><span data-stu-id="f8961-134">Removing a gesture recognizer</span></span>

<span data-ttu-id="f8961-135">在销毁 GestureRecognizer 对象之前，请 *记得取消订阅已订阅* 的事件。</span><span class="sxs-lookup"><span data-stu-id="f8961-135">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="f8961-136">在 Unity 中呈现运动控制器模型</span><span class="sxs-lookup"><span data-stu-id="f8961-136">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="f8961-137">![运动控制器模型和远程传送](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="f8961-137">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="f8961-138">*运动控制器模型和远程传送*</span><span class="sxs-lookup"><span data-stu-id="f8961-138">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="f8961-139">若要在应用中呈现与用户持有的物理控制器匹配的运动控制器，并按各种按钮时进行阐明，可以使用混合现实工具包 中的 **MotionController** [预制项](https://github.com/Microsoft/MixedRealityToolkit-Unity/)。</span><span class="sxs-lookup"><span data-stu-id="f8961-139">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="f8961-140">此预制件在运行时从系统安装的动态控制器驱动程序动态加载正确的 glTF 模型。</span><span class="sxs-lookup"><span data-stu-id="f8961-140">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="f8961-141">必须动态加载这些模型，而不是在编辑器中手动导入这些模型，这样应用就会为用户可能拥有的任何当前和未来控制器显示物理上准确的 3D 模型。</span><span class="sxs-lookup"><span data-stu-id="f8961-141">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="f8961-142">按照 [入门](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) 说明下载混合现实工具包，并将其添加到 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="f8961-142">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="f8961-143">如果在安装步骤中将相机替换为 *MixedRealityCameraParent* 预制件入门，则你可以继续操作！</span><span class="sxs-lookup"><span data-stu-id="f8961-143">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="f8961-144">该预制包括运动控制器呈现。</span><span class="sxs-lookup"><span data-stu-id="f8961-144">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="f8961-145">否则，请从" *项目"窗格将 Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* 添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="f8961-145">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="f8961-146">需要添加该预制组件作为任何父对象的子级，当用户在场景中进行远程传送时，你使用它来移动照相机，以便控制器与用户一起移动。</span><span class="sxs-lookup"><span data-stu-id="f8961-146">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="f8961-147">如果应用不涉及远程传送，只需在场景的根目录下添加预制。</span><span class="sxs-lookup"><span data-stu-id="f8961-147">If your app doesn't involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="f8961-148">引发对象</span><span class="sxs-lookup"><span data-stu-id="f8961-148">Throwing objects</span></span>

<span data-ttu-id="f8961-149">在虚拟现实中引发对象比最初看起来更困难。</span><span class="sxs-lookup"><span data-stu-id="f8961-149">Throwing objects in virtual reality is a harder problem than it may at first seem.</span></span> <span data-ttu-id="f8961-150">与大多数基于物理的交互一样，在游戏中以意外方式引发时，它将立即明显并中断沉浸式。</span><span class="sxs-lookup"><span data-stu-id="f8961-150">As with most physically based interactions, when throwing in game acts in an unexpected way, it's immediately obvious and breaks immersion.</span></span> <span data-ttu-id="f8961-151">我们花费了一些时间来深入思考如何表示物理上正确的引发行为，并制定了一些指南，通过更新我们的平台来启用，我们希望与大家分享。</span><span class="sxs-lookup"><span data-stu-id="f8961-151">We've spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="f8961-152">可在此处找到建议实现 引发 [的示例](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="f8961-152">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="f8961-153">此示例遵循以下四个准则：</span><span class="sxs-lookup"><span data-stu-id="f8961-153">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="f8961-154">**使用控制器的速度 *，而不是* 位置**。</span><span class="sxs-lookup"><span data-stu-id="f8961-154">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="f8961-155">在 Windows 的 11 月更新中，我们引入了在处于"近似"位置跟踪状态 [时的行为更改](../../design/motion-controllers.md#controller-tracking-state)。</span><span class="sxs-lookup"><span data-stu-id="f8961-155">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="f8961-156">处于此状态时，只要我们认为控制器的准确度较高（通常比位置长）保持高精度，就会继续报告有关控制器的速度信息。</span><span class="sxs-lookup"><span data-stu-id="f8961-156">When in this state, velocity information about the controller will continue to be reported for as long as we believe its high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="f8961-157">**合并 *控制器 的* 角速度**。</span><span class="sxs-lookup"><span data-stu-id="f8961-157">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="f8961-158">此逻辑全部包含在静态 方法的 文件中， `throwing.cs` `GetThrownObjectVelAngVel` 位于上面链接的包中：</span><span class="sxs-lookup"><span data-stu-id="f8961-158">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="f8961-159">由于角速度被放大，所引发的对象必须保持与引发时相同的角速度： `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="f8961-159">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="f8961-160">由于所引发对象的质量中心可能不在手柄姿势的原点，因此在用户参考框架中，其速度可能不同于控制器的速度。</span><span class="sxs-lookup"><span data-stu-id="f8961-160">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity than that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="f8961-161">通过此方式提供的对象速度部分是控制器原点周围所引发对象质量中心的即时正切速度。</span><span class="sxs-lookup"><span data-stu-id="f8961-161">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="f8961-162">此正切速度是控制器角度速度的交叉乘积，向量表示控制器原点与所引发对象的质量中心之间的距离。</span><span class="sxs-lookup"><span data-stu-id="f8961-162">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="f8961-163">所引发对象的总速度是控制器的速度和此正切速度之和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="f8961-163">The total velocity of the thrown object is the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="f8961-164">**请密切注意 *应用* 速度 的时间**。</span><span class="sxs-lookup"><span data-stu-id="f8961-164">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="f8961-165">按下按钮时，该事件可能需要 20 毫秒才能通过蓝牙向上冒泡到操作系统。</span><span class="sxs-lookup"><span data-stu-id="f8961-165">When a button is pressed, it can take up to 20 ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="f8961-166">这意味着，如果轮询控制器状态是否从按下状态更改为未按下状态，则控制器会提供你通过它获得的信息，实际上会提前进行此状态更改。</span><span class="sxs-lookup"><span data-stu-id="f8961-166">This means that if you poll for a controller state change from pressed to not pressed or the other way around, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="f8961-167">此外，轮询 API 呈现的控制器姿势会向前预测，以反映显示帧时可能超过 20 毫秒的姿势。</span><span class="sxs-lookup"><span data-stu-id="f8961-167">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more than 20 ms in the future.</span></span> <span data-ttu-id="f8961-168">这适用于 *呈现* 持有的对象，但在我们计算用户释放引发的时间时，会进一步解决以对象为目标的时间问题。</span><span class="sxs-lookup"><span data-stu-id="f8961-168">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released the throw.</span></span> <span data-ttu-id="f8961-169">幸运的是，在 11 月更新中，当发送 *InteractionSourcePressed* 或 *InteractionSourceReleased* 等 Unity 事件时，状态包括按下或释放按钮时从返回的历史姿势数据。</span><span class="sxs-lookup"><span data-stu-id="f8961-169">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was pressed or released.</span></span>  <span data-ttu-id="f8961-170">若要在引发期间获取最准确的控制器呈现和控制器目标，必须正确使用轮询和事件处理（如果适用）：</span><span class="sxs-lookup"><span data-stu-id="f8961-170">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="f8961-171">对于 **呈现每个** 帧的控制器，应用应在当前帧的光子时间将控制器 *的 GameObject* 定位到向前预测的控制器姿势。</span><span class="sxs-lookup"><span data-stu-id="f8961-171">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="f8961-172">从 Unity 轮询 API（如 *[XR）获取此数据。InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或 *[XR。Wsa。Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*。</span><span class="sxs-lookup"><span data-stu-id="f8961-172">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="f8961-173">对于 **面向按下或** 释放的控制器，应用应基于该按下或释放事件的历史控制器姿势进行光线广播和计算轨迹。</span><span class="sxs-lookup"><span data-stu-id="f8961-173">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="f8961-174">从 Unity 事件 API（如 *[InteractionManager.InteractionSourcePressed）获取此数据](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*。</span><span class="sxs-lookup"><span data-stu-id="f8961-174">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="f8961-175">**使用手柄姿势**。</span><span class="sxs-lookup"><span data-stu-id="f8961-175">**Use the grip pose**.</span></span> <span data-ttu-id="f8961-176">相对于手柄姿势（而不是指针姿势）报告角速度和速度。</span><span class="sxs-lookup"><span data-stu-id="f8961-176">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="f8961-177">引发将继续随将来的 Windows 更新而改进，你可以在此处找到有关它的信息。</span><span class="sxs-lookup"><span data-stu-id="f8961-177">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk"></a><span data-ttu-id="f8961-178">MRTK 中的手势和运动控制器</span><span class="sxs-lookup"><span data-stu-id="f8961-178">Gesture and Motion Controllers in MRTK</span></span>

<span data-ttu-id="f8961-179">可以从输入管理器访问手势和运动控制器。</span><span class="sxs-lookup"><span data-stu-id="f8961-179">You can access gesture and motion controller from the input Manager.</span></span>

* [<span data-ttu-id="f8961-180">MRTK 中的笔势</span><span class="sxs-lookup"><span data-stu-id="f8961-180">Gesture in MRTK</span></span>](/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [<span data-ttu-id="f8961-181">MRTK 中的运动控制器</span><span class="sxs-lookup"><span data-stu-id="f8961-181">Motion Controller in MRTK</span></span>](/windows/mixed-reality/mrtk-unity/features/input/controllers)

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="f8961-182">按照教程进行操作</span><span class="sxs-lookup"><span data-stu-id="f8961-182">Follow along with tutorials</span></span>

<span data-ttu-id="f8961-183">混合现实学院中提供了分步教程和更详细的自定义示例：</span><span class="sxs-lookup"><span data-stu-id="f8961-183">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="f8961-184">MR 输入 211：手势</span><span class="sxs-lookup"><span data-stu-id="f8961-184">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="f8961-185">MR 输入 213：运动控制器</span><span class="sxs-lookup"><span data-stu-id="f8961-185">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="f8961-186">[![MR 输入 213 - 运动控制器](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="f8961-186">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="f8961-187">*MR 输入 213 - 运动控制器*</span><span class="sxs-lookup"><span data-stu-id="f8961-187">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="f8961-188">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="f8961-188">Next Development Checkpoint</span></span>

<span data-ttu-id="f8961-189">如果你遵循我们布局的 Unity 开发旅程，则你正在探索 MRTK 核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="f8961-189">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="f8961-190">从这里，你可以继续了解下一部分基础知识：</span><span class="sxs-lookup"><span data-stu-id="f8961-190">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f8961-191">手部和眼部跟踪</span><span class="sxs-lookup"><span data-stu-id="f8961-191">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="f8961-192">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="f8961-192">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f8961-193">共享体验</span><span class="sxs-lookup"><span data-stu-id="f8961-193">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="f8961-194">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="f8961-194">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8961-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8961-195">See also</span></span>

* [<span data-ttu-id="f8961-196">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="f8961-196">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="f8961-197">运动控制器</span><span class="sxs-lookup"><span data-stu-id="f8961-197">Motion controllers</span></span>](../../design/motion-controllers.md)