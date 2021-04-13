---
title: Unity 中的手势
description: 了解如何使用 XR 和通用按钮和轴 Api 在 Unity 中使用手动手势输入来执行操作。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 手势，unity，注视，输入，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，MRTK，混合现实工具包
ms.openlocfilehash: 523f05f9b3dd05a140bb40168b654a2dc0b00bb5
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299712"
---
# <a name="gestures-in-unity"></a><span data-ttu-id="b96bc-104">Unity 中的手势</span><span class="sxs-lookup"><span data-stu-id="b96bc-104">Gestures in Unity</span></span>

<span data-ttu-id="b96bc-105">您可以通过两种主要方式在您的 [HMD 中进行](gaze-in-unity.md)操作，在 HoloLens 和沉浸式的中的 [手势](../../design/gaze-and-commit.md#composite-gestures) 和 [运动控制器](../../design/motion-controllers.md) 。</span><span class="sxs-lookup"><span data-stu-id="b96bc-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="b96bc-106">可以通过 Unity 中的相同 Api 访问空间输入的两个源的数据。</span><span class="sxs-lookup"><span data-stu-id="b96bc-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="b96bc-107">Unity 提供了两种主要方法来访问 Windows Mixed Reality 的空间输入数据。</span><span class="sxs-lookup"><span data-stu-id="b96bc-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="b96bc-108">常见的 *GetButton/GetAxis* api 跨多个 Unity XR sdk 工作，而特定于 Windows Mixed Reality 的 *InteractionManager/GestureRecognizer* api 会公开一组完整的空间输入数据。</span><span class="sxs-lookup"><span data-stu-id="b96bc-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="b96bc-109">高级别复合手势 Api (GestureRecognizer) </span><span class="sxs-lookup"><span data-stu-id="b96bc-109">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="b96bc-110">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="b96bc-110">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="b96bc-111">**类型**： *GestureRecognizer*、 *GestureSettings*、 *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="b96bc-111">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="b96bc-112">您的应用程序还可以识别空间输入源、点击、保持、操作和导航笔势的更高级复合手势。</span><span class="sxs-lookup"><span data-stu-id="b96bc-112">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation, and Navigation gestures.</span></span> <span data-ttu-id="b96bc-113">您可以使用 GestureRecognizer 在 [手](../../design/gaze-and-commit.md#composite-gestures) 和 [运动控制器](../../design/motion-controllers.md) 中识别这些组合手势。</span><span class="sxs-lookup"><span data-stu-id="b96bc-113">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="b96bc-114">GestureRecognizer 上的每个手势事件都提供输入的 SourceKind，以及事件发生时的目标 head 射线。</span><span class="sxs-lookup"><span data-stu-id="b96bc-114">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="b96bc-115">某些事件提供其他特定于上下文的信息。</span><span class="sxs-lookup"><span data-stu-id="b96bc-115">Some events provide additional context-specific information.</span></span>

<span data-ttu-id="b96bc-116">使用手势识别器捕获手势只需几个步骤：</span><span class="sxs-lookup"><span data-stu-id="b96bc-116">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="b96bc-117">创建新的手势识别器</span><span class="sxs-lookup"><span data-stu-id="b96bc-117">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="b96bc-118">指定要监视的手势</span><span class="sxs-lookup"><span data-stu-id="b96bc-118">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="b96bc-119">订阅这些手势的事件</span><span class="sxs-lookup"><span data-stu-id="b96bc-119">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="b96bc-120">开始捕获手势</span><span class="sxs-lookup"><span data-stu-id="b96bc-120">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="b96bc-121">创建新的手势识别器</span><span class="sxs-lookup"><span data-stu-id="b96bc-121">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="b96bc-122">若要使用 *GestureRecognizer*，必须创建 *GestureRecognizer*：</span><span class="sxs-lookup"><span data-stu-id="b96bc-122">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="b96bc-123">指定要监视的手势</span><span class="sxs-lookup"><span data-stu-id="b96bc-123">Specify which gestures to watch for</span></span>

<span data-ttu-id="b96bc-124">通过 *SetRecognizableGestures ()* 指定你感兴趣的手势：</span><span class="sxs-lookup"><span data-stu-id="b96bc-124">Specify which gestures you're interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="b96bc-125">订阅这些手势的事件</span><span class="sxs-lookup"><span data-stu-id="b96bc-125">Subscribe to events for those gestures</span></span>

<span data-ttu-id="b96bc-126">订阅你感兴趣的手势的事件。</span><span class="sxs-lookup"><span data-stu-id="b96bc-126">Subscribe to events for the gestures you're interested in.</span></span>

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
><span data-ttu-id="b96bc-127">导航和操作手势在 *GestureRecognizer* 的实例上互相排斥。</span><span class="sxs-lookup"><span data-stu-id="b96bc-127">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="b96bc-128">开始捕获手势</span><span class="sxs-lookup"><span data-stu-id="b96bc-128">Start capturing gestures</span></span>

<span data-ttu-id="b96bc-129">默认情况下， *GestureRecognizer* 不会监视输入，直到调用 *StartCapturingGestures ()* 。</span><span class="sxs-lookup"><span data-stu-id="b96bc-129">By default, a *GestureRecognizer* doesn't monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="b96bc-130">如果在处理 *StopCapturingGestures ()* 的帧之前执行了输入，则在调用 *StopCapturingGestures ()* 之后可能会生成该笔势事件。</span><span class="sxs-lookup"><span data-stu-id="b96bc-130">It's possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="b96bc-131">*GestureRecognizer* 将记得在上一帧实际发生的情况下，它是处于打开还是关闭状态，因此，根据此帧的注视目标启动和停止手势监视是可靠的。</span><span class="sxs-lookup"><span data-stu-id="b96bc-131">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it's reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="b96bc-132">停止捕获手势</span><span class="sxs-lookup"><span data-stu-id="b96bc-132">Stop capturing gestures</span></span>

<span data-ttu-id="b96bc-133">停止手势识别：</span><span class="sxs-lookup"><span data-stu-id="b96bc-133">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="b96bc-134">删除手势识别器</span><span class="sxs-lookup"><span data-stu-id="b96bc-134">Removing a gesture recognizer</span></span>

<span data-ttu-id="b96bc-135">请记住，在销毁 *GestureRecognizer* 对象之前，取消订阅已订阅的事件。</span><span class="sxs-lookup"><span data-stu-id="b96bc-135">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="b96bc-136">在 Unity 中呈现运动控制器模型</span><span class="sxs-lookup"><span data-stu-id="b96bc-136">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="b96bc-137">![运动控制器模型和 teleportation](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="b96bc-137">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="b96bc-138">*运动控制器模型和 teleportation*</span><span class="sxs-lookup"><span data-stu-id="b96bc-138">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="b96bc-139">若要在应用中渲染与用户所持有的物理控制器相匹配的运动控制器，并在按下各种按钮时进行解释，可以在 [混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity/)中使用 **MotionController prefab** 。</span><span class="sxs-lookup"><span data-stu-id="b96bc-139">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="b96bc-140">此 prefab 从系统的已安装运动控制器驱动程序在运行时动态加载正确的 glTF 模型。</span><span class="sxs-lookup"><span data-stu-id="b96bc-140">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="b96bc-141">必须动态加载这些模型，而不是在编辑器中手动导入它们，以便您的应用程序能够显示您的用户可能拥有的任何当前和未来控制器的物理上准确的3D 模型。</span><span class="sxs-lookup"><span data-stu-id="b96bc-141">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="b96bc-142">按照 [入门](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) 说明下载混合现实工具包，并将其添加到 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="b96bc-142">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="b96bc-143">如果在入门步骤中将相机替换为 *MixedRealityCameraParent* prefab，则准备就绪！</span><span class="sxs-lookup"><span data-stu-id="b96bc-143">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="b96bc-144">该 prefab 包括运动控制器呈现。</span><span class="sxs-lookup"><span data-stu-id="b96bc-144">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="b96bc-145">否则，请从 "项目" 窗格中将 *资产/HoloToolkit/Input/prototyping/MotionControllers* 添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="b96bc-145">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="b96bc-146">你需要将该 prefab 添加为你用来移动相机的任何父对象的子对象，以使该用户在场景中 teleports 时，使控制器与用户一起工作。</span><span class="sxs-lookup"><span data-stu-id="b96bc-146">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="b96bc-147">如果应用不涉及 teleporting，只需在场景的根目录中添加 prefab。</span><span class="sxs-lookup"><span data-stu-id="b96bc-147">If your app doesn't involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="b96bc-148">引发对象</span><span class="sxs-lookup"><span data-stu-id="b96bc-148">Throwing objects</span></span>

<span data-ttu-id="b96bc-149">在虚拟现实中引发对象比最初可能更难。</span><span class="sxs-lookup"><span data-stu-id="b96bc-149">Throwing objects in virtual reality is a harder problem than it may at first seem.</span></span> <span data-ttu-id="b96bc-150">与大多数基于物理的交互一样，当游戏中的抛出意外时，它会立即出现，并打破浸入式。</span><span class="sxs-lookup"><span data-stu-id="b96bc-150">As with most physically based interactions, when throwing in game acts in an unexpected way, it's immediately obvious and breaks immersion.</span></span> <span data-ttu-id="b96bc-151">我们花了一些时间来了解如何表示物理上正确的引发行为，并通过我们的平台的更新启用了一些准则，我们想要与你共享。</span><span class="sxs-lookup"><span data-stu-id="b96bc-151">We've spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="b96bc-152">可在 [此处](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)找到如何实现引发的示例。</span><span class="sxs-lookup"><span data-stu-id="b96bc-152">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="b96bc-153">此示例遵循以下四个准则：</span><span class="sxs-lookup"><span data-stu-id="b96bc-153">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="b96bc-154">**使用控制器的 *速度* （而不是位置**）。</span><span class="sxs-lookup"><span data-stu-id="b96bc-154">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="b96bc-155">在11月的 Windows 更新中，我们引入了 ["近似" 位置跟踪状态](../../design/motion-controllers.md#controller-tracking-state)下的行为更改。</span><span class="sxs-lookup"><span data-stu-id="b96bc-155">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="b96bc-156">处于此状态时，将继续报告有关控制器的速率信息，前提是我们相信它的高准确性，这通常比位置长。</span><span class="sxs-lookup"><span data-stu-id="b96bc-156">When in this state, velocity information about the controller will continue to be reported for as long as we believe its high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="b96bc-157">\*\*合并控制器的 \*角度速度\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b96bc-157">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="b96bc-158">此逻辑全部包含在 `throwing.cs` 文件中的静态方法中，该文件位于 `GetThrownObjectVelAngVel` 以上链接的包中：</span><span class="sxs-lookup"><span data-stu-id="b96bc-158">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="b96bc-159">在角度速度 conserved 时，引发的对象必须保持与抛出时相同的角度速度： `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="b96bc-159">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="b96bc-160">由于引发的对象很大范围可能不会成为手柄姿势的源，因此它的速度可能比用户引用框架中控制器的速度不同。</span><span class="sxs-lookup"><span data-stu-id="b96bc-160">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity than that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="b96bc-161">以这种方式提供的对象速度的部分是围绕控制器原点的已抛出对象的质量的瞬间相切速度。</span><span class="sxs-lookup"><span data-stu-id="b96bc-161">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="b96bc-162">此相切速度是控制器角度速度的叉积，向量表示控制器原点与所引发对象的质量中心之间的距离。</span><span class="sxs-lookup"><span data-stu-id="b96bc-162">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="b96bc-163">引发的对象的总速度是控制器的速度与此相切速度的总和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="b96bc-163">The total velocity of the thrown object is the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="b96bc-164">密切 \*\*关注我们应用速度的 \*时间\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b96bc-164">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="b96bc-165">按下按钮时，该事件最多可能需要 20 ms 才能通过蓝牙向上向上冒泡到操作系统。</span><span class="sxs-lookup"><span data-stu-id="b96bc-165">When a button is pressed, it can take up to 20 ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="b96bc-166">这意味着，如果你将控制器状态更改从按下状态更改为未按下或其他方式，则控制器会提供你获取的信息。</span><span class="sxs-lookup"><span data-stu-id="b96bc-166">This means that if you poll for a controller state change from pressed to not pressed or the other way around, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="b96bc-167">接下来，轮询 API 所提供的控制器可能是向前预测的，它会在帧显示时反映可能的情况，这可能会在未来超过 20 ms。</span><span class="sxs-lookup"><span data-stu-id="b96bc-167">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more than 20 ms in the future.</span></span> <span data-ttu-id="b96bc-168">这适用于 *呈现* 已保存的对象，但会在计算用户释放引发的时间轨迹时，为 *目标* 对象提供时间问题。</span><span class="sxs-lookup"><span data-stu-id="b96bc-168">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released the throw.</span></span> <span data-ttu-id="b96bc-169">幸运的是，在11月更新中，当发送 Unity 事件（如 *InteractionSourcePressed* 或 *InteractionSourceReleased* ）时，当按下或释放该按钮时，该状态包含来自后端的历史记录数据。</span><span class="sxs-lookup"><span data-stu-id="b96bc-169">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was pressed or released.</span></span>  <span data-ttu-id="b96bc-170">若要在引发期间获得最准确的控制器呈现和控制器目标，则必须根据需要正确使用轮询和事件：</span><span class="sxs-lookup"><span data-stu-id="b96bc-170">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="b96bc-171">对于每个帧的 **控制器呈现** ，你的应用程序应将控制器的 *GameObject* 放在前预测的控制器上，为当前帧的 photon 时间提供。</span><span class="sxs-lookup"><span data-stu-id="b96bc-171">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="b96bc-172">可以从 XR 等 Unity 轮询 Api 获取此数据 *[。InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或 *[XR。WSA.InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*。</span><span class="sxs-lookup"><span data-stu-id="b96bc-172">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="b96bc-173">对于 **控制器** 针对按下或释放的目标，应用程序应基于该按下或释放事件的历史控制器提出的 raycast 和计算轨迹。</span><span class="sxs-lookup"><span data-stu-id="b96bc-173">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="b96bc-174">可以从 Unity 事件 Api 获取此数据，如 *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*。</span><span class="sxs-lookup"><span data-stu-id="b96bc-174">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="b96bc-175">**使用手柄姿势**。</span><span class="sxs-lookup"><span data-stu-id="b96bc-175">**Use the grip pose**.</span></span> <span data-ttu-id="b96bc-176">相对于手柄姿势报告角度速度和速度，而不是指针姿势。</span><span class="sxs-lookup"><span data-stu-id="b96bc-176">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="b96bc-177">在将来的 Windows 更新中，引发将继续改进，你可以在此处找到详细信息。</span><span class="sxs-lookup"><span data-stu-id="b96bc-177">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk"></a><span data-ttu-id="b96bc-178">MRTK 中的手势和运动控制器</span><span class="sxs-lookup"><span data-stu-id="b96bc-178">Gesture and Motion Controllers in MRTK</span></span>

<span data-ttu-id="b96bc-179">可以从输入管理器访问笔势和运动控制器。</span><span class="sxs-lookup"><span data-stu-id="b96bc-179">You can access gesture and motion controller from the input Manager.</span></span>

* [<span data-ttu-id="b96bc-180">MRTK 中的手势</span><span class="sxs-lookup"><span data-stu-id="b96bc-180">Gesture in MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [<span data-ttu-id="b96bc-181">MRTK 中的运动控制器</span><span class="sxs-lookup"><span data-stu-id="b96bc-181">Motion Controller in MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/controllers)

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="b96bc-182">按照教程进行操作</span><span class="sxs-lookup"><span data-stu-id="b96bc-182">Follow along with tutorials</span></span>

<span data-ttu-id="b96bc-183">混合现实学院中提供了更详细的自定义示例的分步教程：</span><span class="sxs-lookup"><span data-stu-id="b96bc-183">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="b96bc-184">MR 输入 211：手势</span><span class="sxs-lookup"><span data-stu-id="b96bc-184">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="b96bc-185">MR 输入 213：运动控制器</span><span class="sxs-lookup"><span data-stu-id="b96bc-185">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="b96bc-186">[![MR 输入 213-运动控制器](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="b96bc-186">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="b96bc-187">*MR 输入 213-运动控制器*</span><span class="sxs-lookup"><span data-stu-id="b96bc-187">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b96bc-188">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="b96bc-188">Next Development Checkpoint</span></span>

<span data-ttu-id="b96bc-189">如果遵循我们所说的 Unity 开发旅程，就是在浏览 MRTK 核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="b96bc-189">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="b96bc-190">从这里，你可以继续了解下一部分基础知识：</span><span class="sxs-lookup"><span data-stu-id="b96bc-190">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b96bc-191">手部和眼部跟踪</span><span class="sxs-lookup"><span data-stu-id="b96bc-191">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="b96bc-192">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="b96bc-192">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b96bc-193">共享体验</span><span class="sxs-lookup"><span data-stu-id="b96bc-193">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="b96bc-194">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="b96bc-194">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b96bc-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b96bc-195">See also</span></span>

* [<span data-ttu-id="b96bc-196">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="b96bc-196">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="b96bc-197">运动控制器</span><span class="sxs-lookup"><span data-stu-id="b96bc-197">Motion controllers</span></span>](../../design/motion-controllers.md)