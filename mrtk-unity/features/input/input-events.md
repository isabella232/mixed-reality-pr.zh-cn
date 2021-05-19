---
title: 输入事件数
description: MRTK 中的大于文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，事件，
ms.openlocfilehash: 450c6dbbed8fc9bbb1a648b7a22f0de66747cbaf
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145223"
---
# <a name="input-events"></a><span data-ttu-id="da64e-104">输入事件</span><span class="sxs-lookup"><span data-stu-id="da64e-104">Input events</span></span>

<span data-ttu-id="da64e-105">下面的列表概述了要由自定义 MonoBehaviour 组件实现的所有可用输入事件接口。</span><span class="sxs-lookup"><span data-stu-id="da64e-105">The list below outlines all available input event interfaces to be implemented by a custom MonoBehaviour component.</span></span> <span data-ttu-id="da64e-106">这些接口将由 MRTK 输入系统调用，以根据用户输入交互处理自定义应用逻辑。</span><span class="sxs-lookup"><span data-stu-id="da64e-106">These interfaces will be called by the MRTK input system to handle custom app logic based on user input interactions.</span></span> <span data-ttu-id="da64e-107">与以下标准输入事件类型相比，[指针输入事件](pointers.md#pointer-event-interfaces)的处理方式略有不同。</span><span class="sxs-lookup"><span data-stu-id="da64e-107">[Pointer input events](pointers.md#pointer-event-interfaces) are handled slightly differently than the standard input event types below.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="da64e-108">默认情况下，仅当脚本是焦点中某个 GameObject 的指针或父级的 GameObject 时，该脚本才会接收到输入事件。</span><span class="sxs-lookup"><span data-stu-id="da64e-108">By default, a script will receive input events only if it is the GameObject in focus by a pointer or parent of a GameObject in focus.</span></span>

| <span data-ttu-id="da64e-109">Handler</span><span class="sxs-lookup"><span data-stu-id="da64e-109">Handler</span></span> | <span data-ttu-id="da64e-110">事件</span><span class="sxs-lookup"><span data-stu-id="da64e-110">Events</span></span> | <span data-ttu-id="da64e-111">说明</span><span class="sxs-lookup"><span data-stu-id="da64e-111">Description</span></span> |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | <span data-ttu-id="da64e-112">检测到源/丢失源</span><span class="sxs-lookup"><span data-stu-id="da64e-112">Source Detected / Lost</span></span> | <span data-ttu-id="da64e-113">在检测到/丢失输入源时引发，如检测到的已表述手势或丢失跟踪。</span><span class="sxs-lookup"><span data-stu-id="da64e-113">Raised when an input source is detected/lost, like when an articulated hand is detected or lost track of.</span></span> |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | <span data-ttu-id="da64e-114">源姿势已更改</span><span class="sxs-lookup"><span data-stu-id="da64e-114">Source Pose Changed</span></span> | <span data-ttu-id="da64e-115">在源姿势发生更改时引发。</span><span class="sxs-lookup"><span data-stu-id="da64e-115">Raised on source pose changes.</span></span> <span data-ttu-id="da64e-116">源姿势表示输入源的一般姿势。</span><span class="sxs-lookup"><span data-stu-id="da64e-116">The source pose represents the general pose of the input source.</span></span> <span data-ttu-id="da64e-117">可以通过获取在六个 DOF 控制器中的特定姿势，如手柄或指针 `IMixedRealityInputHandler<MixedRealityPose>` 。</span><span class="sxs-lookup"><span data-stu-id="da64e-117">Specific poses, like the grip or pointer pose in a six DOF controller, can be obtained via `IMixedRealityInputHandler<MixedRealityPose>`.</span></span> |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | <span data-ttu-id="da64e-118">输入关闭/向上</span><span class="sxs-lookup"><span data-stu-id="da64e-118">Input Down / Up</span></span> | <span data-ttu-id="da64e-119">对二进制输入（如按钮）的更改引发。</span><span class="sxs-lookup"><span data-stu-id="da64e-119">Raised on changes to binary inputs like buttons.</span></span> |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | <span data-ttu-id="da64e-120">输入已更改</span><span class="sxs-lookup"><span data-stu-id="da64e-120">Input Changed</span></span> | <span data-ttu-id="da64e-121">对给定类型的输入进行更改时引发。</span><span class="sxs-lookup"><span data-stu-id="da64e-121">Raised on changes to inputs of the given type.</span></span> <span data-ttu-id="da64e-122">**T** 可以采用以下值：</span><span class="sxs-lookup"><span data-stu-id="da64e-122">**T** can take the following values:</span></span> <br/> <span data-ttu-id="da64e-123">- *float* (例如返回模拟触发器) </span><span class="sxs-lookup"><span data-stu-id="da64e-123">- *float* (e.g returns analog trigger)</span></span><br/> <span data-ttu-id="da64e-124">- *Vector2.y* (例如，返回游戏杆操纵杆方向) </span><span class="sxs-lookup"><span data-stu-id="da64e-124">- *Vector2* (e.g returns gamepad thumbstick direction)</span></span> <br/> <span data-ttu-id="da64e-125">- *System.numerics.vector2* (例如，返回跟踪设备的位置) </span><span class="sxs-lookup"><span data-stu-id="da64e-125">- *Vector3* (e.g return position of tracked device)</span></span> <br/> <span data-ttu-id="da64e-126">- *四元* (，例如返回所跟踪设备) </span><span class="sxs-lookup"><span data-stu-id="da64e-126">- *Quaternion* (e.g returns orientation of tracked device)</span></span><br/> <span data-ttu-id="da64e-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (例如，返回完全跟踪的设备) </span><span class="sxs-lookup"><span data-stu-id="da64e-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (e.g. returns fully tracked device)</span></span> |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | <span data-ttu-id="da64e-128">已识别语音关键字</span><span class="sxs-lookup"><span data-stu-id="da64e-128">Speech Keyword Recognized</span></span> | <span data-ttu-id="da64e-129">在识别语音命令配置文件 中配置的关键字之 *一时引发*。</span><span class="sxs-lookup"><span data-stu-id="da64e-129">Raised on recognition of one of the keywords configured in the *Speech Commands Profile*.</span></span> |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | <span data-ttu-id="da64e-130">听写</span><span class="sxs-lookup"><span data-stu-id="da64e-130">Dictation</span></span><br/> <span data-ttu-id="da64e-131">假设</span><span class="sxs-lookup"><span data-stu-id="da64e-131">Hypothesis</span></span> <br/> <span data-ttu-id="da64e-132">结果</span><span class="sxs-lookup"><span data-stu-id="da64e-132">Result</span></span> <br/> <span data-ttu-id="da64e-133">完成</span><span class="sxs-lookup"><span data-stu-id="da64e-133">Complete</span></span> <br/> <span data-ttu-id="da64e-134">错误</span><span class="sxs-lookup"><span data-stu-id="da64e-134">Error</span></span> | <span data-ttu-id="da64e-135">由听写系统引发，以报告听写会话的结果。</span><span class="sxs-lookup"><span data-stu-id="da64e-135">Raised by dictation systems to report the results of a dictation session.</span></span> |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | <span data-ttu-id="da64e-136">上的笔势事件：</span><span class="sxs-lookup"><span data-stu-id="da64e-136">Gesture events on:</span></span> <br/> <span data-ttu-id="da64e-137">Started</span><span class="sxs-lookup"><span data-stu-id="da64e-137">Started</span></span> <br/> <span data-ttu-id="da64e-138">已更新</span><span class="sxs-lookup"><span data-stu-id="da64e-138">Updated</span></span> <br/> <span data-ttu-id="da64e-139">已完成</span><span class="sxs-lookup"><span data-stu-id="da64e-139">Completed</span></span> <br/> <span data-ttu-id="da64e-140">已取消</span><span class="sxs-lookup"><span data-stu-id="da64e-140">Canceled</span></span> | <span data-ttu-id="da64e-141">在手势检测时引发。</span><span class="sxs-lookup"><span data-stu-id="da64e-141">Raised on gesture detection.</span></span> |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | <span data-ttu-id="da64e-142">手势已更新/已完成</span><span class="sxs-lookup"><span data-stu-id="da64e-142">Gesture Updated / Completed</span></span> | <span data-ttu-id="da64e-143">在检测包含给定类型的其他数据的笔势时引发。</span><span class="sxs-lookup"><span data-stu-id="da64e-143">Raised on detection of gestures containing additional data of the given type.</span></span> <span data-ttu-id="da64e-144">有关 [**T 的可能**](gestures.md#gesture-events) 值的详细信息，请参阅笔势 **事件**。</span><span class="sxs-lookup"><span data-stu-id="da64e-144">See [**gesture events**](gestures.md#gesture-events) for details on possible values for **T**.</span></span> |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | <span data-ttu-id="da64e-145">已更新手部</span><span class="sxs-lookup"><span data-stu-id="da64e-145">Hand Joints Updated</span></span> | <span data-ttu-id="da64e-146">在更新手部时由铰接式手部控制器引发。</span><span class="sxs-lookup"><span data-stu-id="da64e-146">Raised by articulated hand controllers when hand joints are updated.</span></span> |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | <span data-ttu-id="da64e-147">手动网格已更新</span><span class="sxs-lookup"><span data-stu-id="da64e-147">Hand Mesh Updated</span></span> | <span data-ttu-id="da64e-148">由手部网格更新时由铰接式手部控制器引发。</span><span class="sxs-lookup"><span data-stu-id="da64e-148">Raised by articulated hand controllers when a hand mesh is updated.</span></span> |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | <span data-ttu-id="da64e-149">操作已启动/已结束</span><span class="sxs-lookup"><span data-stu-id="da64e-149">Action Started / Ended</span></span> | <span data-ttu-id="da64e-150">引发 以指示映射到操作的输入的操作开始和结束。</span><span class="sxs-lookup"><span data-stu-id="da64e-150">Raise to indicate action start and end for inputs mapped to actions.</span></span> |

## <a name="input-events-in-action"></a><span data-ttu-id="da64e-151">操作中的输入事件</span><span class="sxs-lookup"><span data-stu-id="da64e-151">Input events in action</span></span>

<span data-ttu-id="da64e-152">在脚本级别，可以通过实现上表中所示的事件处理程序接口之一来使用输入事件。</span><span class="sxs-lookup"><span data-stu-id="da64e-152">At the script level, input events can be consumed by implementing one of the event handler interfaces shown in the table above.</span></span> <span data-ttu-id="da64e-153">通过用户交互触发输入事件时，将发生以下情况：</span><span class="sxs-lookup"><span data-stu-id="da64e-153">When an input event fires via a user interaction, the following takes place:</span></span>

1. <span data-ttu-id="da64e-154">MRTK 输入系统识别已发生输入事件。</span><span class="sxs-lookup"><span data-stu-id="da64e-154">The MRTK input system recognizes that an input event has occurred.</span></span>
1. <span data-ttu-id="da64e-155">MRTK 输入系统向所有[已注册的全局输入处理程序](#register-for-global-input-events)激发输入事件的相关接口函数</span><span class="sxs-lookup"><span data-stu-id="da64e-155">The MRTK input system fires the relevant interface function of the input event to all [registered global input handlers](#register-for-global-input-events)</span></span>
1. <span data-ttu-id="da64e-156">对于注册到输入系统的每个活动指针：</span><span class="sxs-lookup"><span data-stu-id="da64e-156">For every active pointer registered with the input system:</span></span>
    1. <span data-ttu-id="da64e-157">输入系统确定当前指针的焦点是哪个 GameObject。</span><span class="sxs-lookup"><span data-stu-id="da64e-157">The input system determines which GameObject is in focus for the current pointer.</span></span>
    1. <span data-ttu-id="da64e-158">输入系统利用 [Unity 的事件系统](https://docs.unity3d.com/Manual/EventSystem.html) 为重点 GameObject 上的所有匹配组件激发相关的接口函数。</span><span class="sxs-lookup"><span data-stu-id="da64e-158">The input system utilizes [Unity's event system](https://docs.unity3d.com/Manual/EventSystem.html) to fire the relevant interface function for all matching components on the focused GameObject.</span></span>
    1. <span data-ttu-id="da64e-159">如果任何时候输入事件已 [标记为](#how-to-stop-input-events)"已使用"，该进程将结束，并且不会再进一步 gameobject 接收回调。</span><span class="sxs-lookup"><span data-stu-id="da64e-159">If at any point an input event has been [marked as used](#how-to-stop-input-events), the process will end and no further GameObjects will receive callbacks.</span></span>
        - <span data-ttu-id="da64e-160">示例：在 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 识别语音命令时，将搜索实现接口的组件。</span><span class="sxs-lookup"><span data-stu-id="da64e-160">Example: Components implementing the interface [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) will be searched for when a speech command is recognized.</span></span>
        - <span data-ttu-id="da64e-161">注意：如果在当前 GameObject 上找不到与所需接口匹配的组件，则 Unity 事件系统将向上冒泡以搜索父 GameObject。</span><span class="sxs-lookup"><span data-stu-id="da64e-161">Note: The Unity event system will bubble up to search the parent GameObject if no components matching the desired interface are found on the current GameObject.</span></span>
1. <span data-ttu-id="da64e-162">如果未注册任何全局输入处理程序，并且找不到具有匹配的组件/接口的 GameObject，则输入系统将调用每个回退注册的输入处理程序</span><span class="sxs-lookup"><span data-stu-id="da64e-162">If no global input handlers are registered and no GameObject is found with a matching component/interface, then the input system will call each fallback registered input handler</span></span>

> [!NOTE]
> <span data-ttu-id="da64e-163">与上面列出的输入事件接口相比，[指针输入事件](pointers.md#pointer-event-interfaces)的处理方式略有不同。</span><span class="sxs-lookup"><span data-stu-id="da64e-163">[Pointer input events](pointers.md#pointer-event-interfaces) are handled in a slightly different manner than the input event interfaces listed above.</span></span> <span data-ttu-id="da64e-164">特别是，指针输入事件仅由触发输入事件的指针以及任何全局输入处理程序的 GameObject 处理。</span><span class="sxs-lookup"><span data-stu-id="da64e-164">In particular, pointer input events are handled only by the GameObject in focus by the pointer that fired the input event - as well as any global input handlers.</span></span> <span data-ttu-id="da64e-165">对于所有活动指针，常规输入事件由 Gameobject 处理。</span><span class="sxs-lookup"><span data-stu-id="da64e-165">Regular input events are handled by GameObjects in focus for all active pointers.</span></span>

### <a name="input-event-interface-example"></a><span data-ttu-id="da64e-166">输入事件接口示例</span><span class="sxs-lookup"><span data-stu-id="da64e-166">Input event interface example</span></span>

<span data-ttu-id="da64e-167">下面的代码演示如何使用 [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 接口。</span><span class="sxs-lookup"><span data-stu-id="da64e-167">The code below demonstrates use of the [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface.</span></span> <span data-ttu-id="da64e-168">如果用户在使用此类 GameObject 时显示 "更小" 或 "更大" 字样 `ShowHideSpeechHandler` ，则 GameObject 会将其自身缩放一半或两倍。</span><span class="sxs-lookup"><span data-stu-id="da64e-168">When the user says the words "smaller" or "bigger" while focusing on a GameObject with this `ShowHideSpeechHandler` class, the GameObject will scale itself by half or twice as much.</span></span>

```c#
public class ShowHideSpeechHandler : MonoBehaviour, IMixedRealitySpeechHandler
{
    ...

    void IMixedRealitySpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.Command.Keyword == "smaller")
        {
            transform.localScale *= 0.5f;
        }
        else if (eventData.Command.Keyword == "bigger")
        {
            transform.localScale *= 2.0f;
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="da64e-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) 输入事件要求在 [MRTK 语音命令配置文件](speech.md)中预先注册所需的关键字。</span><span class="sxs-lookup"><span data-stu-id="da64e-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) input events require that the desired keywords are pre-registered in the [MRTK Speech Commands Profile](speech.md).</span></span>

## <a name="register-for-global-input-events"></a><span data-ttu-id="da64e-170">注册全局输入事件</span><span class="sxs-lookup"><span data-stu-id="da64e-170">Register for global input events</span></span>

<span data-ttu-id="da64e-171">若要创建侦听全局输入事件的组件，而不考虑可能的 GameObject，组件必须向输入系统自行注册。</span><span class="sxs-lookup"><span data-stu-id="da64e-171">To create a component that listens for global input events, disregarding what GameObject may be in focus, a component must register itself with the Input System.</span></span> <span data-ttu-id="da64e-172">注册后，此 MonoBehaviour 的任何实例都将接收输入事件，以及当前 (焦点和其他全局注册侦听器) GameObject 事件。</span><span class="sxs-lookup"><span data-stu-id="da64e-172">Once registered, any instances of this MonoBehaviour will receive input events along with any GameObject(s) currently in focus and other global registered listeners.</span></span>

<span data-ttu-id="da64e-173">如果输入事件已 [标记为已用](#how-to-stop-input-events)，则全局注册处理程序仍将接收回调。</span><span class="sxs-lookup"><span data-stu-id="da64e-173">If an input event has been [marked as used](#how-to-stop-input-events), global registered handlers will still all receive callbacks.</span></span> <span data-ttu-id="da64e-174">但是，没有焦点 GameObjects 将接收事件。</span><span class="sxs-lookup"><span data-stu-id="da64e-174">However, no focused GameObjects will receive the event.</span></span>

### <a name="global-input-registration-example"></a><span data-ttu-id="da64e-175">全局输入注册示例</span><span class="sxs-lookup"><span data-stu-id="da64e-175">Global input registration example</span></span>

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler, // Handle source detected and lost
    IMixedRealityHandJointHandler // handle joint position updates for hands
{
    private void OnEnable()
    {
        // Instruct Input System that we would like to receive all input events of type
        // IMixedRealitySourceStateHandler and IMixedRealityHandJointHandler
        CoreServices.InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        // This component is being destroyed
        // Instruct the Input System to disregard us for input event handling
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source detected: " + hand.ControllerHandedness);
        }
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source lost: " + hand.ControllerHandedness);
        }
    }

    public void OnHandJointsUpdated(
                InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        MixedRealityPose palmPose;
        if (eventData.InputData.TryGetValue(TrackedHandJoint.Palm, out palmPose))
        {
            Debug.Log("Hand Joint Palm Updated: " + palmPose.Position);
        }
    }
}
```

## <a name="register-for-fallback-input-events"></a><span data-ttu-id="da64e-176">注册回退输入事件</span><span class="sxs-lookup"><span data-stu-id="da64e-176">Register for fallback input events</span></span>

<span data-ttu-id="da64e-177">回退输入处理程序类似于已注册的全局输入处理程序，但被视为处理输入事件的最后手段。</span><span class="sxs-lookup"><span data-stu-id="da64e-177">Fallback input handlers are similar to registered global input handlers but are treated as a last resort for input event handling.</span></span> <span data-ttu-id="da64e-178">只有在未找到全局输入处理程序且没有 GameObject 焦点时，才使用回退输入处理程序。</span><span class="sxs-lookup"><span data-stu-id="da64e-178">Only if no global input handlers were found and no GameObjects are in focus will fallback input handlers be leveraged.</span></span>

### <a name="fallback-input-handler-example"></a><span data-ttu-id="da64e-179">回退输入处理程序示例</span><span class="sxs-lookup"><span data-stu-id="da64e-179">Fallback input handler example</span></span>

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler // Handle source detected and lost
{
    private void OnEnable()
    {
        CoreServices.InputSystem?.PushFallbackInputHandler(this);
    }

    private void OnDisable()
    {
        CoreServices.InputSystem?.PopFallbackInputHandler();
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        ...
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        ...
    }
}
```

## <a name="how-to-stop-input-events"></a><span data-ttu-id="da64e-180">如何停止输入事件</span><span class="sxs-lookup"><span data-stu-id="da64e-180">How to stop input events</span></span>

<span data-ttu-id="da64e-181">每个输入事件接口都提供 [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) 一个数据对象作为接口上每个函数的参数。</span><span class="sxs-lookup"><span data-stu-id="da64e-181">Every input event interface provides a [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) data object as a parameter to each function on the interface.</span></span> <span data-ttu-id="da64e-182">此事件数据对象从 Unity 自己的 扩展 [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) 。</span><span class="sxs-lookup"><span data-stu-id="da64e-182">This event data object extends from Unity's own [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html).</span></span>

<span data-ttu-id="da64e-183">为了阻止输入事件按所述传播其执行，组件可以调用[](#input-events-in-action)以 [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) 将事件标记为已用。</span><span class="sxs-lookup"><span data-stu-id="da64e-183">In order to stop an input event from propagating through its execution [as outlined](#input-events-in-action), a component can call [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) to mark the event as used.</span></span> <span data-ttu-id="da64e-184">这将阻止任何其他 GameObject 接收当前输入事件，全局输入处理程序除外。</span><span class="sxs-lookup"><span data-stu-id="da64e-184">This will stop any other GameObjects from receiving the current input event, with the exception of global input handlers.</span></span>

> [!NOTE]
> <span data-ttu-id="da64e-185">调用 方法的组件 `Use()` 将阻止其他 GameObject 接收它。</span><span class="sxs-lookup"><span data-stu-id="da64e-185">A component that calls the `Use()` method will stop other GameObjects from receiving it.</span></span> <span data-ttu-id="da64e-186">但是，当前 GameObject 上的其他组件仍将接收输入事件并调用任何相关的接口函数。</span><span class="sxs-lookup"><span data-stu-id="da64e-186">However, other components on the current GameObject will still receive the input event and fire any related interface functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="da64e-187">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da64e-187">See also</span></span>

- [<span data-ttu-id="da64e-188">指针</span><span class="sxs-lookup"><span data-stu-id="da64e-188">Pointers</span></span>](pointers.md)
- [<span data-ttu-id="da64e-189">语音</span><span class="sxs-lookup"><span data-stu-id="da64e-189">Speech</span></span>](speech.md)
- [<span data-ttu-id="da64e-190">输入状态</span><span class="sxs-lookup"><span data-stu-id="da64e-190">Input State</span></span>](input-state.md)
