---
title: 目视跟踪目标选择
description: 如何访问眼睛数据和目视注视特定事件，以在 MRTK 中选择目标
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，EyeTracking，
ms.openlocfilehash: 229903e01c597aefbb3fc29de8a49d79cbbd42d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144194"
---
# <a name="eye-supported-target-selection"></a><span data-ttu-id="558ba-104">目视支持的目标选择</span><span class="sxs-lookup"><span data-stu-id="558ba-104">Eye-supported target selection</span></span>

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="558ba-106">本页讨论用于访问眼睛数据的不同选项，以及用于在 MRTK 中选择目标的目视特定事件。</span><span class="sxs-lookup"><span data-stu-id="558ba-106">This page discusses different options for accessing eye gaze data and eye gaze specific events to select targets in MRTK.</span></span> <span data-ttu-id="558ba-107">使用目视跟踪，可以通过与用户正在查看的信息以及有关 _手动跟踪_ 和 _语音命令_ 等其他输入的信息组合来进行快速轻松的目标选择：</span><span class="sxs-lookup"><span data-stu-id="558ba-107">Eye tracking allows for fast and effortless target selections using a combination of information about what a user is looking at with additional inputs such as _hand tracking_ and _voice commands_:</span></span>

- <span data-ttu-id="558ba-108">查找 & 说 _"选择"_ (默认的语音命令) </span><span class="sxs-lookup"><span data-stu-id="558ba-108">Look & Say _"Select"_ (default voice command)</span></span>
- <span data-ttu-id="558ba-109">查找 (自定义语音命令 & 说 _"分解"_ 或 _"Pop"_) </span><span class="sxs-lookup"><span data-stu-id="558ba-109">Look & Say _"Explode"_ or _"Pop"_ (custom voice commands)</span></span>
- <span data-ttu-id="558ba-110">"查看 & 蓝牙" 按钮</span><span class="sxs-lookup"><span data-stu-id="558ba-110">Look & Bluetooth button</span></span>
- <span data-ttu-id="558ba-111">看看 & 挤压 (例如，在你的前方，将拇指和食指置于一起) </span><span class="sxs-lookup"><span data-stu-id="558ba-111">Look & Pinch (i.e., hold up your hand in front of you and bring your thumb and index finger together)</span></span>
  - <span data-ttu-id="558ba-112">请注意，要使其正常工作， [需要禁用手写片](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span><span class="sxs-lookup"><span data-stu-id="558ba-112">Please note that for this to work, the [hand rays need to be disabled](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span></span>

<span data-ttu-id="558ba-113">若要使用眼睛来选择全息内容，有几个选项可供选择：</span><span class="sxs-lookup"><span data-stu-id="558ba-113">To select holographic content using eye gaze, there are several options:</span></span>

[<span data-ttu-id="558ba-114">**1. 使用主要焦点指针：**</span><span class="sxs-lookup"><span data-stu-id="558ba-114">**1. Use the primary focus pointer:**</span></span>](#1-use-generic-focus-and-pointer-handlers)

<span data-ttu-id="558ba-115">这可以理解为优先顺序的游标。</span><span class="sxs-lookup"><span data-stu-id="558ba-115">This can be understood as your prioritized cursor.</span></span>
<span data-ttu-id="558ba-116">默认情况下，如果手处于视图状态，则这将是手动光线。</span><span class="sxs-lookup"><span data-stu-id="558ba-116">By default, if the hands are in view, then this would be hand rays.</span></span>
<span data-ttu-id="558ba-117">如果没有任何指针在视图中，则优先顺序的指针将为 head 或眼睛。</span><span class="sxs-lookup"><span data-stu-id="558ba-117">If no hands are in view, then the prioritized pointer would be head or eye gaze.</span></span>
<span data-ttu-id="558ba-118">因此，请注意，如果使用的是手写光线，则会将基于当前设计头或眼睛的眼睛禁止为光标输入。</span><span class="sxs-lookup"><span data-stu-id="558ba-118">Thus, please note that based on the current design head or eye gaze is suppressed as a cursor input if hand rays are used.</span></span>

<span data-ttu-id="558ba-119">例如：</span><span class="sxs-lookup"><span data-stu-id="558ba-119">For example:</span></span>

<span data-ttu-id="558ba-120">用户需要选择一个 "远处" 的全息按钮。</span><span class="sxs-lookup"><span data-stu-id="558ba-120">A user wants to select a distant holographic button.</span></span>
<span data-ttu-id="558ba-121">作为开发人员，您希望提供一个灵活的解决方案，使用户能够在各种情况下实现此任务：</span><span class="sxs-lookup"><span data-stu-id="558ba-121">As a developer, you want to provide a flexible solution that allows the user to achieve this tasks in various conditions:</span></span>

- <span data-ttu-id="558ba-122">转到按钮并浏览</span><span class="sxs-lookup"><span data-stu-id="558ba-122">Walk up to the button and poke it</span></span>
- <span data-ttu-id="558ba-123">从一个距离中查看它，说"选择"</span><span class="sxs-lookup"><span data-stu-id="558ba-123">Look at it from a distance and say "select"</span></span>
- <span data-ttu-id="558ba-124">使用手部射线并执行收缩将按钮作为目标。在这种情况下，最灵活的解决方案是使用主焦点处理程序，因为每当当前优先处理的主焦点指针触发事件时，它会通知你。</span><span class="sxs-lookup"><span data-stu-id="558ba-124">Target the button using a hand ray and performing a pinch In this case, the most flexible solution is to use the primary focus handler as it will notify you whenever the currently prioritized primary focus pointer triggers an event.</span></span> <span data-ttu-id="558ba-125">请注意，如果启用了手部射线，当手进入视场时，头部或眼睛凝视焦点指针就会被禁用。</span><span class="sxs-lookup"><span data-stu-id="558ba-125">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="558ba-126">请注意，如果启用了手部射线，当手进入视场时，头部或眼睛凝视焦点指针就会被禁用。</span><span class="sxs-lookup"><span data-stu-id="558ba-126">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span> <span data-ttu-id="558ba-127">如果要支持"外观和收缩"[交互，则需要禁用手部射线](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)。</span><span class="sxs-lookup"><span data-stu-id="558ba-127">If you want to support a [_'look and pinch'_ interaction, you need to disable the hand ray](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray).</span></span> <span data-ttu-id="558ba-128">在眼动跟踪示例场景中，我们禁用了手部射线，以允许使用眼睛 + 手部运动展示更丰富的交互 - 请参阅支持眼 [部定位的示例](eye-tracking-eyes-and-hands.md)。</span><span class="sxs-lookup"><span data-stu-id="558ba-128">In our eye tracking sample scenes, we have disabled the hand ray to allow for showcasing richer interactions using eyes + hand motions - see for example [Eye-Supported Positioning](eye-tracking-eyes-and-hands.md).</span></span>

[<span data-ttu-id="558ba-129">**2.同时使用眼睛焦点和手部射线：**</span><span class="sxs-lookup"><span data-stu-id="558ba-129">**2. Use both eye focus and hand rays at the same time:**</span></span>](#2-independent-eye-gaze-specific-eyetrackingtarget)

<span data-ttu-id="558ba-130">在某些情况下，你可能希望更具体地了解哪些焦点指针类型可以触发特定事件并允许同时使用多个远场交互技术。</span><span class="sxs-lookup"><span data-stu-id="558ba-130">There might be instances where you want to be more specific which type of focus pointers can trigger certain events and allow for simultaneously using multiple far interaction techniques.</span></span>

<span data-ttu-id="558ba-131">例如：在应用中，用户可以使用远手射线来操作一些全息机械设置，例如，抓取并按住一些远程全息引擎部件并就地保存它们。</span><span class="sxs-lookup"><span data-stu-id="558ba-131">For example: In your app, a user can use far hand rays to manipulate some holographic mechanical setup - e.g., grab and hold some distant holographic engine parts and hold them in place.</span></span> <span data-ttu-id="558ba-132">执行此操作时，用户必须浏览多个说明，并通过标记一些复选框来记录其进度。</span><span class="sxs-lookup"><span data-stu-id="558ba-132">While doing so, the user has to go through a number of instructions and record her/his progress by marking off some check boxes.</span></span> <span data-ttu-id="558ba-133">如果用户手不忙，那么只需触摸复选框，或者使用手部射线选择它，就会很自然。</span><span class="sxs-lookup"><span data-stu-id="558ba-133">If the user has her/his hands _not busy_, it would be instinctual to simply touch the check box or select it using a hand ray.</span></span> <span data-ttu-id="558ba-134">但是，如果用户手忙，就像我们的情况中，将一些全息引擎部件放在一起时，你想要让用户使用眼睛凝视无缝滚动说明，并直接查看复选框并说"检查！"。</span><span class="sxs-lookup"><span data-stu-id="558ba-134">However, if the user has her/his hands busy, as in our case holding some holographic engine parts in place, you want to enable the user to seamlessly scroll through the instructions using their eye gaze and to simply look at a check box and say "check it!".</span></span>

<span data-ttu-id="558ba-135">若要启用此功能，需要使用与核心 MRTK FocusHandlers 无关的特定于眼睛的 EyeTrackingTarget 脚本，并在下面进一步讨论。</span><span class="sxs-lookup"><span data-stu-id="558ba-135">To enable this, you need to use eye-specific EyeTrackingTarget script that is independent from the core MRTK FocusHandlers and will be discussed further below.</span></span>

## <a name="1-use-generic-focus-and-pointer-handlers"></a><span data-ttu-id="558ba-136">1.使用通用焦点和指针处理程序</span><span class="sxs-lookup"><span data-stu-id="558ba-136">1. Use generic focus and pointer handlers</span></span>

<span data-ttu-id="558ba-137">如果正确设置了目视跟踪 (参阅 [基本 MRTK 安装程序以使用目视跟踪](eye-tracking-basic-setup.md)) ，使用户可以使用眼睛来选择全息影像，这与任何其他焦点输入 (例如，打印头或手 ray) 相同。这使你可以通过在 MRTK 输入指针配置文件中定义主焦点类型（这取决于用户的需求）来灵活地与全息影像交互，同时使代码保持不变。</span><span class="sxs-lookup"><span data-stu-id="558ba-137">If eye tracking is set up correctly (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)), enabling users to select holograms using their eyes is the same as for any other focus input (e.g., head gaze or hand ray).This provides the great advantage of a flexible way to interact with your holograms by defining the main focus type in your MRTK Input Pointer Profile depending on your user's needs, while leaving your code untouched.</span></span> <span data-ttu-id="558ba-138">这允许在打印头或眼睛眼睛之间切换，而无需更改代码行或将手形光线替换为远交互的目视目标。</span><span class="sxs-lookup"><span data-stu-id="558ba-138">This allows for switching between head or eye gaze without changing a line of code or replace hand rays with eye targeting for far interactions.</span></span>

### <a name="focusing-on-a-hologram"></a><span data-ttu-id="558ba-139">专注于全息图</span><span class="sxs-lookup"><span data-stu-id="558ba-139">Focusing on a hologram</span></span>

<span data-ttu-id="558ba-140">若要检测全息影像的聚焦情况，请使用 _"IMixedRealityFocusHandler"_ 接口，该接口提供两个接口成员： _OnFocusEnter_ 和 _OnFocusExit_。</span><span class="sxs-lookup"><span data-stu-id="558ba-140">To detect when a hologram is focused, use the _'IMixedRealityFocusHandler'_ interface that provides you with two interface members: _OnFocusEnter_ and _OnFocusExit_.</span></span>

<span data-ttu-id="558ba-141">下面是 [ColorTap](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) 中的一个简单示例，用于在查看时更改全息图的颜色。</span><span class="sxs-lookup"><span data-stu-id="558ba-141">Here is a simple example from [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) to change a hologram's color when being looked at.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler
{
    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }
    ...
}
```

### <a name="selecting-a-focused-hologram"></a><span data-ttu-id="558ba-142">选择重点全息图</span><span class="sxs-lookup"><span data-stu-id="558ba-142">Selecting a focused hologram</span></span>

<span data-ttu-id="558ba-143">若要选择具有焦点的全息图，请使用 _PointerHandler_ 侦听输入事件以确认所做的选择。</span><span class="sxs-lookup"><span data-stu-id="558ba-143">To select a focused hologram, use _PointerHandler_ to listen for input events to confirm a selection.</span></span>
<span data-ttu-id="558ba-144">例如，添加 _IMixedRealityPointerHandler_ 会使它们对简单指针输入做出反应。</span><span class="sxs-lookup"><span data-stu-id="558ba-144">For example, adding the _IMixedRealityPointerHandler_ will make them react to simple pointer input.</span></span>
<span data-ttu-id="558ba-145">_IMixedRealityPointerHandler_ 接口需要实现以下三个接口成员： _OnPointerUp_、 _OnPointerDown_ 和 _OnPointerClicked_。</span><span class="sxs-lookup"><span data-stu-id="558ba-145">The _IMixedRealityPointerHandler_ interface requires implementing the following three interface members: _OnPointerUp_, _OnPointerDown_, and _OnPointerClicked_.</span></span>

<span data-ttu-id="558ba-146">在下面的示例中，我们通过查看并收缩或说 "select" 来更改全息图的颜色。</span><span class="sxs-lookup"><span data-stu-id="558ba-146">In the example below, we change the color of a hologram by looking at it and pinching or saying "select".</span></span>
<span data-ttu-id="558ba-147">触发事件所需的操作的定义是， `eventData.MixedRealityInputAction == selectAction` 我们可以 `selectAction` 在 Unity 编辑器中设置的类型-默认情况下，它是 "选择" 操作。</span><span class="sxs-lookup"><span data-stu-id="558ba-147">The required action to trigger the event is defined by `eventData.MixedRealityInputAction == selectAction` whereby we can set the type of `selectAction` in the Unity Editor - by default it's the "Select" action.</span></span> <span data-ttu-id="558ba-148">可以通过 [](../input-actions.md) _MRTK 配置文件_  ->  _输入_  ->  _输入操作_ 在 MRTK 配置文件中配置可用 MixedRealityInputActions 的类型。</span><span class="sxs-lookup"><span data-stu-id="558ba-148">The types of available [MixedRealityInputActions](../input-actions.md) can be configured in the MRTK Profile via _MRTK Configuration Profile_ -> _Input_ -> _Input Actions_.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    // Allow for editing the type of select action in the Unity Editor.
    [SerializeField]
    private MixedRealityInputAction selectAction = MixedRealityInputAction.None;
    ...

    void IMixedRealityPointerHandler.OnPointerUp(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnHover;
        }
    }

    void IMixedRealityPointerHandler.OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnSelect;
        }
    }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData) { }
}
```

### <a name="eye-gaze-specific-baseeyefocushandler"></a><span data-ttu-id="558ba-149">眼睛特定的 BaseEyeFocusHandler</span><span class="sxs-lookup"><span data-stu-id="558ba-149">Eye-gaze-specific BaseEyeFocusHandler</span></span>

<span data-ttu-id="558ba-150">鉴于眼睛凝视与其他指针输入可能非常不同，你可能希望确保仅在焦点输入为眼睛凝视且当前为主输入指针时做出反应。 </span><span class="sxs-lookup"><span data-stu-id="558ba-150">Given that eye gaze can be very different to other pointer inputs, you may want to make sure to only react to the focus input if it is _eye gaze_ and it is currently the primary input pointer.</span></span>
<span data-ttu-id="558ba-151">为此，将使用特定于眼动跟踪的 以及 [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) 派生自 的 [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) 。</span><span class="sxs-lookup"><span data-stu-id="558ba-151">For this purpose, you would use the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) which is specific to eye tracking and which derives from the [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler).</span></span>
<span data-ttu-id="558ba-152">如前所述，只有当眼睛凝视目标当前是主要指针输入（即没有手部射线处于活动状态 (时，它才触发) 。</span><span class="sxs-lookup"><span data-stu-id="558ba-152">As mentioned before, it will only trigger if eye gaze targeting is currently the primary pointer input (i.e., no hand ray is active).</span></span> <span data-ttu-id="558ba-153">有关详细信息，请参阅 [如何支持眼睛凝视 + 手势](eye-tracking-eyes-and-hands.md)。</span><span class="sxs-lookup"><span data-stu-id="558ba-153">For more information, see [How to support eye gaze + hand gestures](eye-tracking-eyes-and-hands.md).</span></span>

<span data-ttu-id="558ba-154">下面是来自 (`EyeTrackingDemo-03-Navigation` Assets/MRTK/Examples/Demos/EyeTracking/Scenes) 。</span><span class="sxs-lookup"><span data-stu-id="558ba-154">Here is an example from `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).</span></span>
<span data-ttu-id="558ba-155">在此演示中，有两个 3D 全息影像将打开，具体取决于查看对象的哪个部分：如果用户查看全息影像的左侧，则该部分将缓慢地向面向用户的正面移动。</span><span class="sxs-lookup"><span data-stu-id="558ba-155">In this demo, there are two 3D holograms that will turn depending on which part of the object is looked at: If the user looks at the left side of the hologram, then that part will slowly move towards the front facing the user.</span></span>
<span data-ttu-id="558ba-156">如果查看右侧，则该部分将缓慢移动到前面。</span><span class="sxs-lookup"><span data-stu-id="558ba-156">If the right side is looked at, then that part will slowly move to the front.</span></span>
<span data-ttu-id="558ba-157">这是一种可能不希望一直处于活动状态的行为，也是不希望由手部射线或头部凝视意外触发的行为。</span><span class="sxs-lookup"><span data-stu-id="558ba-157">This is a behavior that you may not want to have active at all times and also something that you may not want to accidentally trigger by a hand ray or head gaze.</span></span>
<span data-ttu-id="558ba-158">附加 [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) 后，查看 GameObject 时将旋转。</span><span class="sxs-lookup"><span data-stu-id="558ba-158">Having the [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) attached, a GameObject will rotate while being looked at.</span></span>

```c#
public class OnLookAtRotateByEyeGaze : BaseEyeFocusHandler
{
    ...

    protected override void OnEyeFocusStay()
    {
        // Update target rotation
        RotateHitTarget();
    }

    ...

    ///
    /// This function computes the rotation of the target to move the currently
    /// looked at aspect slowly to the front.
    ///
    private void RotateHitTarget()
    {
        // Example for querying the hit position of the eye gaze ray using EyeGazeProvider
        Vector3 TargetToHit = (this.gameObject.transform.position - InputSystem.EyeGazeProvider.HitPosition).normalized;

        ...
    }
}
```

<span data-ttu-id="558ba-159">有关 的可用事件的完整列表，请查看 API 文档 [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) ：</span><span class="sxs-lookup"><span data-stu-id="558ba-159">Check the API documentation for a complete list of available events of the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler):</span></span>

- <span data-ttu-id="558ba-160">**OnEyeFocusStart：** 当眼睛凝视射线 *开始与* 此目标的碰撞体相交时触发。</span><span class="sxs-lookup"><span data-stu-id="558ba-160">**OnEyeFocusStart:** Triggered once the eye gaze ray *starts* intersecting with this target's collider.</span></span>
- <span data-ttu-id="558ba-161">**OnEyeFocusStay：** 当 *眼睛* 凝视射线与此目标的碰撞体相交时触发。</span><span class="sxs-lookup"><span data-stu-id="558ba-161">**OnEyeFocusStay:** Triggered *while* the eye gaze ray is intersecting with this target's collider.</span></span>
- <span data-ttu-id="558ba-162">**OnEyeFocusStop：** 当眼睛凝视射线 *停止与* 此目标的碰撞体相交时触发。</span><span class="sxs-lookup"><span data-stu-id="558ba-162">**OnEyeFocusStop:** Triggered once the eye gaze ray *stops* intersecting with this target's collider.</span></span>
- <span data-ttu-id="558ba-163">**OnEyeFocusDwell：** 在眼睛凝视射线与此目标的碰撞体相交一定时间后触发。</span><span class="sxs-lookup"><span data-stu-id="558ba-163">**OnEyeFocusDwell:** Triggered once the eye gaze ray has intersected with this target's collider for a specified amount of time.</span></span>

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a><span data-ttu-id="558ba-164">2.独立眼睛凝视特定的 EyeTrackingTarget</span><span class="sxs-lookup"><span data-stu-id="558ba-164">2. Independent eye-gaze-specific EyeTrackingTarget</span></span>

<span data-ttu-id="558ba-165">最后，我们提供了一个解决方案，让你通过脚本完全独立于其他焦点指针处理基于眼睛的 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 输入。</span><span class="sxs-lookup"><span data-stu-id="558ba-165">Finally, we provide you with a solution that let's you treat eye-based input completely independent from other focus pointers via the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.</span></span>

<span data-ttu-id="558ba-166">这有三 _个优点_：</span><span class="sxs-lookup"><span data-stu-id="558ba-166">This has three _advantages_:</span></span>

- <span data-ttu-id="558ba-167">可以确保只对用户的眼睛进行反应。</span><span class="sxs-lookup"><span data-stu-id="558ba-167">You can make sure that the hologram is only reacting to the user's eye gaze.</span></span>
- <span data-ttu-id="558ba-168">这与当前活动的主输入无关。</span><span class="sxs-lookup"><span data-stu-id="558ba-168">This is independent from the currently active primary input.</span></span> <span data-ttu-id="558ba-169">因此，可以一次处理多个输入，例如，将快速目视定位与手势结合起来。</span><span class="sxs-lookup"><span data-stu-id="558ba-169">Hence, you can process multiple inputs at once - for example, combining fast eye targeting with hand gestures.</span></span>
- <span data-ttu-id="558ba-170">已经设置了几个 Unity 事件，使您能够快速轻松地处理和重用 Unity 编辑器内或通过代码中的现有行为。</span><span class="sxs-lookup"><span data-stu-id="558ba-170">Several Unity events have already been set up to make it fast and convenient to handle and reuse existing behaviors from within the Unity Editor or via code.</span></span>

<span data-ttu-id="558ba-171">还有一些 _缺点：_</span><span class="sxs-lookup"><span data-stu-id="558ba-171">There are also some _disadvantages:_</span></span>

- <span data-ttu-id="558ba-172">分别处理单独的输入的工作量。</span><span class="sxs-lookup"><span data-stu-id="558ba-172">More effort to handle separate inputs individually.</span></span>
- <span data-ttu-id="558ba-173">不优雅地降低：它仅支持目视目标。</span><span class="sxs-lookup"><span data-stu-id="558ba-173">No elegant degradation: It only supports eye targeting.</span></span> <span data-ttu-id="558ba-174">如果目视跟踪不起作用，则需要额外的回退。</span><span class="sxs-lookup"><span data-stu-id="558ba-174">If eye tracking is not working, you require some additional fallback.</span></span>

<span data-ttu-id="558ba-175">与 _BaseFocusHandler_ 类似， _EyeTrackingTarget_ 已准备好几个眼睛特定的 unity 事件，你可以通过 Unity 编辑器轻松地侦听这些事件 (参见下面的示例) 或通过在代码中使用 _AddListener ()_ ：</span><span class="sxs-lookup"><span data-stu-id="558ba-175">Similar to the _BaseFocusHandler_, the _EyeTrackingTarget_ comes ready with several eye-gaze-specific Unity events that you can conveniently listen to either via the Unity Editor (see example below) or by using _AddListener()_ in code:</span></span>

- <span data-ttu-id="558ba-176">OnLookAtStart () </span><span class="sxs-lookup"><span data-stu-id="558ba-176">OnLookAtStart()</span></span>
- <span data-ttu-id="558ba-177">WhileLookingAtTarget () </span><span class="sxs-lookup"><span data-stu-id="558ba-177">WhileLookingAtTarget()</span></span>
- <span data-ttu-id="558ba-178">OnLookAway () </span><span class="sxs-lookup"><span data-stu-id="558ba-178">OnLookAway()</span></span>
- <span data-ttu-id="558ba-179">OnDwell () </span><span class="sxs-lookup"><span data-stu-id="558ba-179">OnDwell()</span></span>
- <span data-ttu-id="558ba-180">OnSelected () </span><span class="sxs-lookup"><span data-stu-id="558ba-180">OnSelected()</span></span>

<span data-ttu-id="558ba-181">在下面的示例中，我们将逐步介绍如何使用 _EyeTrackingTarget_。</span><span class="sxs-lookup"><span data-stu-id="558ba-181">In the following, we walk you through a few examples for how to use _EyeTrackingTarget_.</span></span>

### <a name="example-1-eye-supported-smart-notifications"></a><span data-ttu-id="558ba-182">示例 #1：目视支持的智能通知</span><span class="sxs-lookup"><span data-stu-id="558ba-182">Example #1: Eye-supported smart notifications</span></span>

<span data-ttu-id="558ba-183">在 `EyeTrackingDemo-02-TargetSelection` (资产/MRTK/示例/演示/EyeTracking/场景) 中，可以找到反应眼睛的 _"智能留心通知"_ 的示例。</span><span class="sxs-lookup"><span data-stu-id="558ba-183">In `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes), you can find an example for _'smart attentive notifications'_ that react to your eye gaze.</span></span>
<span data-ttu-id="558ba-184">这些是可放置在场景中的3D 文本框，当查看这些文本框以便于辨认时，它们会平稳地放大并向用户翻。</span><span class="sxs-lookup"><span data-stu-id="558ba-184">These are 3D text boxes that can be placed in the scene and that will smoothly enlarge and turn toward the user when being looked at to ease legibility.</span></span> <span data-ttu-id="558ba-185">当用户阅读通知时，信息始终显示清晰清晰。</span><span class="sxs-lookup"><span data-stu-id="558ba-185">While the user is reading the notification, the information keeps getting displayed crisp and clear.</span></span> <span data-ttu-id="558ba-186">阅读并查看通知后，将自动消除通知并将其淡出。为实现所有这一切，有几个根本不特定于目视跟踪的通用行为脚本，例如：</span><span class="sxs-lookup"><span data-stu-id="558ba-186">After reading it and looking away from the notification, the notification will automatically be dismissed and fades out. To achieve all this, there are a few generic behavior scripts that are not specific to eye tracking at all, such as:</span></span>

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

<span data-ttu-id="558ba-187">此方法的优点是，各种事件可以重复使用相同的脚本。</span><span class="sxs-lookup"><span data-stu-id="558ba-187">The advantage of this approach is that the same scripts can be reused by various events.</span></span> <span data-ttu-id="558ba-188">例如，全息影像可能会基于语音命令或按下虚拟按钮后开始面向用户。</span><span class="sxs-lookup"><span data-stu-id="558ba-188">For example, a hologram may start facing the user based on a voice commands or after pressing a virtual button.</span></span> <span data-ttu-id="558ba-189">若要触发这些事件，只需引用应在附加到 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) GameObject 的脚本中执行的方法。</span><span class="sxs-lookup"><span data-stu-id="558ba-189">To trigger these events, you can simply reference the methods that should be executed in the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script that is attached to your GameObject.</span></span>

<span data-ttu-id="558ba-190">对于"智能智能手机通知 _"_ 的示例，会发生以下情况：</span><span class="sxs-lookup"><span data-stu-id="558ba-190">For the example of the _'smart attentive notifications'_, the following happens:</span></span>

- <span data-ttu-id="558ba-191">**OnLookAtStart () ：** 通知开始...</span><span class="sxs-lookup"><span data-stu-id="558ba-191">**OnLookAtStart()**: The notification starts to...</span></span>
  - <span data-ttu-id="558ba-192">*FaceUser.Engage：...* 向用户打开 。</span><span class="sxs-lookup"><span data-stu-id="558ba-192">*FaceUser.Engage:* ... turn toward the user.</span></span>
  - <span data-ttu-id="558ba-193">*ChangeSize.Engage：...* 大小增加 _(到指定的最大缩放) 。_</span><span class="sxs-lookup"><span data-stu-id="558ba-193">*ChangeSize.Engage:* ... increase in size _(up to a specified maximum scale)_.</span></span>
  - <span data-ttu-id="558ba-194">*BlendOut.Engage：...* 在 处于更 (_空闲状态后，_ 开始混合使用) 。</span><span class="sxs-lookup"><span data-stu-id="558ba-194">*BlendOut.Engage:* ... starts to blend in more _(after being at a more subtle idle state)_.</span></span>  

- <span data-ttu-id="558ba-195">**OnDwell () ：** 通知 _BlendOut_ 脚本通知通知已充分查看。</span><span class="sxs-lookup"><span data-stu-id="558ba-195">**OnDwell()**: Informs the _BlendOut_ script that the notification has been looked at sufficiently.</span></span>

- <span data-ttu-id="558ba-196">**OnLookAway () ：** 通知开始...</span><span class="sxs-lookup"><span data-stu-id="558ba-196">**OnLookAway()**: The notification starts to...</span></span>
  - <span data-ttu-id="558ba-197">*FaceUser.Disengage：...* 将 返回到其原始方向。</span><span class="sxs-lookup"><span data-stu-id="558ba-197">*FaceUser.Disengage:* ... turn back to its original orientation.</span></span>
  - <span data-ttu-id="558ba-198">*ChangeSize.Disengage：...* 减小回其原始大小。</span><span class="sxs-lookup"><span data-stu-id="558ba-198">*ChangeSize.Disengage:* ... decrease back to its original size.</span></span>
  - <span data-ttu-id="558ba-199">*BlendOut.Disengage：...* 开始混合 - _如果 OnDwell ()_ 触发，则完全混合并销毁，否则返回其空闲状态。</span><span class="sxs-lookup"><span data-stu-id="558ba-199">*BlendOut.Disengage:* ... starts to blend out - If _OnDwell()_ was triggered, blend out completely and destroy, otherwise back to its idle state.</span></span>

<span data-ttu-id="558ba-200">**设计注意事项：** 在这里，获得舒适体验的关键是仔细调整任何这些行为的速度，以避免由于一直对用户眼睛凝视反应过快而引起眼睛凝视。</span><span class="sxs-lookup"><span data-stu-id="558ba-200">**Design consideration:** The key to an enjoyable experience here is to carefully tune the speed of any of these behaviors to avoid causing discomfort by reacting to the user’s eye gaze too quickly all the time.</span></span>
<span data-ttu-id="558ba-201">否则，这很快就会让人感到难以承受。</span><span class="sxs-lookup"><span data-stu-id="558ba-201">Otherwise this can quickly feel extremely overwhelming.</span></span>

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a><span data-ttu-id="558ba-202">示例#2：全息 gem 在查看时缓慢旋转</span><span class="sxs-lookup"><span data-stu-id="558ba-202">Example #2: Holographic gem rotates slowly when looking at it</span></span>

<span data-ttu-id="558ba-203">与示例 #1 类似，我们可以轻松地为 (Assets/MRTK/Examples/Demos/EyeTracking/Scene) 场景中的全息 gem 创建悬停反馈，该场景在查看时以恒定方向和恒定速度 (缓慢旋转 (与上面) 中的旋转示例相反。 `EyeTrackingDemo-02-TargetSelection`</span><span class="sxs-lookup"><span data-stu-id="558ba-203">Similar to Example #1, we can easily create a hover feedback for our holographic gems in `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) scene that will slowly rotate in a constant direction and at a constant speed (in contrast to the rotation example from above) when being looked at.</span></span> <span data-ttu-id="558ba-204">只需从 _EyeTrackingTarget_ 的 _WhileLookingAtTarget ()_ 事件触发全息 gem 的旋转。</span><span class="sxs-lookup"><span data-stu-id="558ba-204">All you need is to trigger the rotation of the holographic gem from the _EyeTrackingTarget_'s _WhileLookingAtTarget()_ event.</span></span> <span data-ttu-id="558ba-205">以下是更多详细信息：</span><span class="sxs-lookup"><span data-stu-id="558ba-205">Here are a few more details:</span></span>

1. <span data-ttu-id="558ba-206">创建一个泛型脚本，其中包含一个用于旋转其附加到的 GameObject 的公共函数。</span><span class="sxs-lookup"><span data-stu-id="558ba-206">Create a generic script that includes a public function to rotate the GameObject it is attached to.</span></span> <span data-ttu-id="558ba-207">下面是 _RotateWithConstSpeedDir_ 中的一个示例，可在其中通过 Unity 编辑器调整旋转方向和速度。</span><span class="sxs-lookup"><span data-stu-id="558ba-207">Below is an example from _RotateWithConstSpeedDir.cs_ where we can tweak the rotation direction and speed from the Unity Editor.</span></span>

    ```c#
    using UnityEngine;

    namespace Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking
    {
        /// <summary>
        /// The associated GameObject will rotate when RotateTarget() is called based on a given direction and speed.
        /// </summary>
        public class RotateWithConstSpeedDir : MonoBehaviour
        {
            [Tooltip("Euler angles by which the object should be rotated by.")]
            [SerializeField]
            private Vector3 RotateByEulerAngles = Vector3.zero;

            [Tooltip("Rotation speed factor.")]
            [SerializeField]
            private float speed = 1f;

            /// <summary>
            /// Rotate game object based on specified rotation speed and Euler angles.
            /// </summary>
            public void RotateTarget()
            {
                transform.eulerAngles = transform.eulerAngles + RotateByEulerAngles * speed;
            }
        }
    }
    ```

1. <span data-ttu-id="558ba-208">将 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 脚本添加到目标 GameObject，并在 UnityEvent 触发器中引用 _RotateTarget ()_ 函数，如以下屏幕截图所示：</span><span class="sxs-lookup"><span data-stu-id="558ba-208">Add the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to your target GameObject and reference the _RotateTarget()_ function in the UnityEvent trigger as shown the screenshot below:</span></span>

    ![EyeTrackingTarget 示例](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a><span data-ttu-id="558ba-210">示例 #3： Pop 这些 gem 又 _又称_</span><span class="sxs-lookup"><span data-stu-id="558ba-210">Example #3: Pop those gems aka _multi-modal eye-gaze-supported target selection_</span></span>

<span data-ttu-id="558ba-211">在上面的示例中，我们已展示了如何轻松地检测是否查看目标以及如何触发对该目标的反应。</span><span class="sxs-lookup"><span data-stu-id="558ba-211">In the previous example, we have shown how easy it is to detect whether a target is looked at and how to trigger a reaction to that.</span></span> <span data-ttu-id="558ba-212">接下来，让我们使用中的 _OnSelected ()_ 事件分解 gem [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 。</span><span class="sxs-lookup"><span data-stu-id="558ba-212">Next, let's make the gems explode using the _OnSelected()_ event from the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget).</span></span> <span data-ttu-id="558ba-213">有趣的部分是 *如何* 触发选择。</span><span class="sxs-lookup"><span data-stu-id="558ba-213">The interesting part is *how* the selection is triggered.</span></span> <span data-ttu-id="558ba-214">[`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget)允许快速分配不同的方法来调用选择：</span><span class="sxs-lookup"><span data-stu-id="558ba-214">The [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) allows for quickly assigning different ways to invoke a selection:</span></span>

- <span data-ttu-id="558ba-215">_挤压手势_：将 "选择操作" 设置为 "select" 将使用默认的手动笔势来触发选择。</span><span class="sxs-lookup"><span data-stu-id="558ba-215">_Pinch gesture_: Setting the 'Select Action' to 'Select' uses the default hand gesture to trigger the selection.</span></span>
<span data-ttu-id="558ba-216">这意味着用户只需抬起手并将其拇指和食指合并在一起以确认所做的选择。</span><span class="sxs-lookup"><span data-stu-id="558ba-216">This means that the user can simply raise their hand and pinch their thumb and index finger together to confirm the selection.</span></span>

- <span data-ttu-id="558ba-217">说 _"选择"_：使用默认的语音命令 _"选择"_ 来选择全息影像。</span><span class="sxs-lookup"><span data-stu-id="558ba-217">Say _"Select"_: Use the default voice command _"Select"_ for selecting a hologram.</span></span>

- <span data-ttu-id="558ba-218">说 _"分解"_ 或 _"Pop"_：若要使用自定义语音命令，需要执行两个步骤：</span><span class="sxs-lookup"><span data-stu-id="558ba-218">Say _"Explode"_ or _"Pop"_: To use custom voice commands, you need to follow two steps:</span></span>
    1. <span data-ttu-id="558ba-219">设置自定义操作，如 _"DestroyTarget"_</span><span class="sxs-lookup"><span data-stu-id="558ba-219">Set up a custom action such as _"DestroyTarget"_</span></span>
        - <span data-ttu-id="558ba-220">导航到 _MRTK-> 输入-> 输入操作_</span><span class="sxs-lookup"><span data-stu-id="558ba-220">Navigate to _MRTK -> Input -> Input Actions_</span></span>
        - <span data-ttu-id="558ba-221">单击 "添加新操作"</span><span class="sxs-lookup"><span data-stu-id="558ba-221">Click "Add a new action"</span></span>

    2. <span data-ttu-id="558ba-222">设置触发此操作的语音命令，如 _"分解"_ 或 _"Pop"_</span><span class="sxs-lookup"><span data-stu-id="558ba-222">Set up the voice commands that trigger this action such as _"Explode"_ or _"Pop"_</span></span>
        - <span data-ttu-id="558ba-223">导航到 _MRTK-> 输入-> 语音_</span><span class="sxs-lookup"><span data-stu-id="558ba-223">Navigate to _MRTK -> Input -> Speech_</span></span>
        - <span data-ttu-id="558ba-224">单击"添加新的语音命令"</span><span class="sxs-lookup"><span data-stu-id="558ba-224">Click "Add a new speech command"</span></span>
            - <span data-ttu-id="558ba-225">关联刚刚创建的操作</span><span class="sxs-lookup"><span data-stu-id="558ba-225">Associate the action you just created</span></span>
            - <span data-ttu-id="558ba-226">分配 _KeyCode_ 以允许通过按下按钮触发操作</span><span class="sxs-lookup"><span data-stu-id="558ba-226">Assign a _KeyCode_ to allow for triggering the action via a button press</span></span>

![语音命令 EyeTrackingTarget 示例](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

<span data-ttu-id="558ba-228">选择 gem 后，它会分解，发出声音并消失。</span><span class="sxs-lookup"><span data-stu-id="558ba-228">When a gem is selected it will explode, making a sound and disappear.</span></span> <span data-ttu-id="558ba-229">这由脚本 [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) 处理。</span><span class="sxs-lookup"><span data-stu-id="558ba-229">This is handled by the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script.</span></span> <span data-ttu-id="558ba-230">可以使用两个选项：</span><span class="sxs-lookup"><span data-stu-id="558ba-230">You have two options:</span></span>

- <span data-ttu-id="558ba-231">**在 Unity 编辑器中：** 只需将附加到每个 gem 模板的脚本链接到 Unity 编辑器中的 OnSelected () Unity 事件。</span><span class="sxs-lookup"><span data-stu-id="558ba-231">**In the Unity Editor:** You could simply link the script that is attached to each of our gem templates to the OnSelected() Unity event in the Unity Editor.</span></span>
- <span data-ttu-id="558ba-232">**在代码中：** 如果不想四处拖放 GameObject，还可以直接将事件侦听器添加到脚本。</span><span class="sxs-lookup"><span data-stu-id="558ba-232">**In code:** If you don't want to drag and drop GameObjects around, you can also simply add a event listener directly to your script.</span></span>  
<span data-ttu-id="558ba-233">下面是我们在脚本中执行它 [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) 的示例：</span><span class="sxs-lookup"><span data-stu-id="558ba-233">Here's an example from how we did it in the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:</span></span>

```c#
/// <summary>
/// Destroys the game object when selected and optionally plays a sound or animation when destroyed.
/// </summary>
[RequireComponent(typeof(EyeTrackingTarget))] // This helps to ensure that the EyeTrackingTarget is attached
public class HitBehaviorDestroyOnSelect : MonoBehaviour
{
    ...
    private EyeTrackingTarget myEyeTrackingTarget = null;

    private void Start()
    {
        myEyeTrackingTarget = this.GetComponent<EyeTrackingTarget>();

        if (myEyeTrackingTarget != null)
        {
            myEyeTrackingTarget.OnSelected.AddListener(TargetSelected);
        }
    }

    ...

    ///
    /// This is called once the EyeTrackingTarget detected a selection.
    ///
    public void TargetSelected()
    {
        // Play some animation
        // Play some audio effect
        // Handle destroying the target appropriately
    }
}
```

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a><span data-ttu-id="558ba-234">示例#4：将手部射线和眼睛凝视输入一起使用</span><span class="sxs-lookup"><span data-stu-id="558ba-234">Example #4: Use hand rays and eye gaze input together</span></span>

<span data-ttu-id="558ba-235">手部射线优先于头部和眼睛凝视目标。</span><span class="sxs-lookup"><span data-stu-id="558ba-235">Hand rays take priority over head and eye gaze targeting.</span></span> <span data-ttu-id="558ba-236">这意味着，如果启用手部射线，当手进入视图时，手部射线将充当主指针。</span><span class="sxs-lookup"><span data-stu-id="558ba-236">This means, if hand rays are enabled, the moment the hands come into view, the hand ray will act as the primary pointer.</span></span>
<span data-ttu-id="558ba-237">但是，在某些情况下，你可能想要在仍然检测用户是否正在查看某个全息影像的同时使用手部射线。</span><span class="sxs-lookup"><span data-stu-id="558ba-237">However, there might be situations in which you want to use hand rays while still detecting whether a user is looking at a certain hologram.</span></span> <span data-ttu-id="558ba-238">简单！</span><span class="sxs-lookup"><span data-stu-id="558ba-238">Easy!</span></span> <span data-ttu-id="558ba-239">实质上，需要执行两个步骤：</span><span class="sxs-lookup"><span data-stu-id="558ba-239">Essentially you require two steps:</span></span>

<span data-ttu-id="558ba-240">**1.启用手部射线：** 若要启用手部射线，请转到混合现实 _工具包 ->输入 ->指针_。</span><span class="sxs-lookup"><span data-stu-id="558ba-240">**1. Enable the hand ray:** To enable the hand ray, go to _Mixed Reality Toolkit -> Input -> Pointers_.</span></span>
<span data-ttu-id="558ba-241">在所有眼动跟踪演示场景配置混合现实工具包一次的 _EyeTrackingDemo-00-RootScene_ 中，应会看到 _EyeTrackingDemoPointerProfile_。</span><span class="sxs-lookup"><span data-stu-id="558ba-241">In the _EyeTrackingDemo-00-RootScene_ where the Mixed Reality Toolkit is configured once for all of the eye tracking demo scenes, you should see the _EyeTrackingDemoPointerProfile_.</span></span>
<span data-ttu-id="558ba-242">可以从头开始 _创建新的输入配置文件_ ，也可以调整当前眼动跟踪配置文件：</span><span class="sxs-lookup"><span data-stu-id="558ba-242">You can either create a new _Input Profile_ from scratch or adapt the current eye tracking one:</span></span>

- <span data-ttu-id="558ba-243">**从头开始：** 在"_指针"_ 选项卡中，从上下文菜单中选择 _DefaultMixedRealityInputPointerProfile。_</span><span class="sxs-lookup"><span data-stu-id="558ba-243">**From scratch:** In the _Pointers_ tab, select the _DefaultMixedRealityInputPointerProfile_ from the context menu.</span></span>
<span data-ttu-id="558ba-244">这是已启用手部射线的默认指针配置文件！</span><span class="sxs-lookup"><span data-stu-id="558ba-244">This is the default pointer profile that already has the hand ray enabled!</span></span>
<span data-ttu-id="558ba-245">若要更改默认光标 (不透明的白色) ，只需克隆配置文件并创建自己的自定义指针配置文件。</span><span class="sxs-lookup"><span data-stu-id="558ba-245">To change the default cursor (an opaque white dot), simply clone the profile and create your own custom pointer profile.</span></span>
<span data-ttu-id="558ba-246">然后将 _DefaultCursor_ 替换为 "_注视 Cursor Prefab_" 下的 " _EyeGazeCursor_ "。</span><span class="sxs-lookup"><span data-stu-id="558ba-246">Then replace _DefaultCursor_ with _EyeGazeCursor_ under _Gaze Cursor Prefab_.</span></span>  
- <span data-ttu-id="558ba-247">**基于现有的 _EyeTrackingDemoPointerProfile_：** 双击 _EyeTrackingDemoPointerProfile_ 并在 " _指针选项_" 下面添加以下项：</span><span class="sxs-lookup"><span data-stu-id="558ba-247">**Based on the existing _EyeTrackingDemoPointerProfile_:** Double-click the _EyeTrackingDemoPointerProfile_ and add the following entry under _Pointer Options_:</span></span>
  - <span data-ttu-id="558ba-248">**控制器类型：** "有向右" 的 "Windows Mixed Reality"</span><span class="sxs-lookup"><span data-stu-id="558ba-248">**Controller Type:** 'Articulated Hand', 'Windows Mixed Reality'</span></span>
  - <span data-ttu-id="558ba-249">**左右手使用习惯：** 随时</span><span class="sxs-lookup"><span data-stu-id="558ba-249">**Handedness:** Any</span></span>
  - <span data-ttu-id="558ba-250">**指针 Prefab：** DefaultControllerPointer</span><span class="sxs-lookup"><span data-stu-id="558ba-250">**Pointer Prefab:** DefaultControllerPointer</span></span>

<span data-ttu-id="558ba-251">**2. 检测是否会查看全息图：** 使用 [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) 脚本来检测是否查看了全息图，如上所述。</span><span class="sxs-lookup"><span data-stu-id="558ba-251">**2. Detect that a hologram is looked at:** Use the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to enable detecting that a hologram is looked at as described above.</span></span> <span data-ttu-id="558ba-252">你还可以查看 `FollowEyeGaze` 有关灵感的示例脚本，因为这会在眼睛下显示一个全息图， (例如，光标) 是否已启用手写光线。</span><span class="sxs-lookup"><span data-stu-id="558ba-252">You can also take a look at the `FollowEyeGaze` sample script for inspiration as this is showing a hologram following your eye gaze (e.g., a cursor) whether hand rays are enabled or not.</span></span>

<span data-ttu-id="558ba-253">现在，当您开始眼睛跟踪演示场景时，您应该会看到一条来自手的射线。</span><span class="sxs-lookup"><span data-stu-id="558ba-253">Now, when you start the eye tracking demo scenes, you should see a ray coming from your hands.</span></span>
<span data-ttu-id="558ba-254">例如，在 "目视跟踪目标选择" 演示中，半透明圆圈仍位于眼睛眼睛的位置，并且 gem 将响应其是否处于查找状态，而顶部场景菜单按钮则使用主输入指针 (你) 改为使用。</span><span class="sxs-lookup"><span data-stu-id="558ba-254">For example, in the eye tracking target selection demo, the semi-transparent circle is still following your eye gaze and the gems respond to whether they are looked at or not, while the top scene menu buttons use the primary input pointer (your hands) instead.</span></span>

---
[<span data-ttu-id="558ba-255">返回 "MixedRealityToolkit" 中的眼睛跟踪</span><span class="sxs-lookup"><span data-stu-id="558ba-255">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
