---
title: 手部指导
description: 手部教练的说明和示例。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: f6042fce7c95c106de9c72adc854e2b7112da63c
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177152"
---
# <a name="hand-coach"></a><span data-ttu-id="af450-104">手部指导</span><span class="sxs-lookup"><span data-stu-id="af450-104">Hand coach</span></span>

![手部指导菜单](../images/hand-coach/MRTK_UX_HandCoach_Main.jpg)

<span data-ttu-id="af450-106">手部训练是 3D 建模手，当系统未检测到用户的手时，会触发手部训练。</span><span class="sxs-lookup"><span data-stu-id="af450-106">Hand coach is 3D modeled hand which is triggered when the system does not detect the user’s hands.</span></span> <span data-ttu-id="af450-107">这是作为"教学"组件实现的，可帮助在未教授手势时指导用户。</span><span class="sxs-lookup"><span data-stu-id="af450-107">This is implemented as a “teaching” component that helps guide the user when the gesture has not been taught.</span></span> <span data-ttu-id="af450-108">如果用户有一段时间没有完成指定的手势，手将循环并出现延迟。</span><span class="sxs-lookup"><span data-stu-id="af450-108">If users have not done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="af450-109">手部指导可用于表示按下按钮或选取全息影像。</span><span class="sxs-lookup"><span data-stu-id="af450-109">Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>

<span data-ttu-id="af450-110">当前交互模型表示各种手势控件，例如滚动、远点选择和近点击。</span><span class="sxs-lookup"><span data-stu-id="af450-110">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="af450-111">下面是现有手部教练示例的完整列表：</span><span class="sxs-lookup"><span data-stu-id="af450-111">Below is a full list of existing Hand coach examples:</span></span>

- <span data-ttu-id="af450-112">近点击 – 用于按钮或关闭可交互对象</span><span class="sxs-lookup"><span data-stu-id="af450-112">Near tap – Used for buttons or close interactable objects</span></span>
- <span data-ttu-id="af450-113">远选 – 用于远离的对象</span><span class="sxs-lookup"><span data-stu-id="af450-113">Far select – Used for objects that are far away</span></span>
- <span data-ttu-id="af450-114">移动 – 用于在空间中移动全息影像</span><span class="sxs-lookup"><span data-stu-id="af450-114">Move – Used to move a hologram in space</span></span>
- <span data-ttu-id="af450-115">旋转 – 用于显示如何旋转全息影像或对象</span><span class="sxs-lookup"><span data-stu-id="af450-115">Rotate – Used to show how to rotate holograms or objects</span></span>
- <span data-ttu-id="af450-116">缩放 - 用于显示如何操作放大或缩小全息影像</span><span class="sxs-lookup"><span data-stu-id="af450-116">Scale – Used to show how to manipulate holograms to be bigger or smaller</span></span>
- <span data-ttu-id="af450-117">手部翻转 - 用于打开 UI 启动面板或手部菜单</span><span class="sxs-lookup"><span data-stu-id="af450-117">Hand flip – Used for bringing up a UI start panel or Hand Menus</span></span>
- <span data-ttu-id="af450-118">"开箱即用"– 用于在开箱即用体验中实现鸟鸟时刻。</span><span class="sxs-lookup"><span data-stu-id="af450-118">Palm up – Used for hummingbird moment in out of the box experience.</span></span> <span data-ttu-id="af450-119">另一个建议可能是启动 UI 启动面板</span><span class="sxs-lookup"><span data-stu-id="af450-119">Another suggestion could be to bring up a UI start panel</span></span>
- <span data-ttu-id="af450-120">滚动 – 用于滚动列表或长文档</span><span class="sxs-lookup"><span data-stu-id="af450-120">Scroll – Used for scrolling a list or a long document</span></span>

## <a name="example-scene"></a><span data-ttu-id="af450-121">示例场景</span><span class="sxs-lookup"><span data-stu-id="af450-121">Example scene</span></span>

<span data-ttu-id="af450-122">可以在 **HandCoachExample** 场景下找到示例 [：MixedRealityToolkit.Examples/Experimental/HandCoach/Scene](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach/Scenes)</span><span class="sxs-lookup"><span data-stu-id="af450-122">You can find examples in the **HandCoachExample** scene under: [MixedRealityToolkit.Examples/Experimental/HandCoach/Scenes](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach/Scenes)</span></span>

## <a name="hand-3d-assets"></a><span data-ttu-id="af450-123">手部 3D 资产</span><span class="sxs-lookup"><span data-stu-id="af450-123">Hand 3D Assets</span></span>

<span data-ttu-id="af450-124">可以在以下项下找到资产 [：MixedRealityToolkit.SDK/Experimental/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach)</span><span class="sxs-lookup"><span data-stu-id="af450-124">You can find the assets under: [MixedRealityToolkit.SDK/Experimental/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach)</span></span>

## <a name="quality"></a><span data-ttu-id="af450-125">质量</span><span class="sxs-lookup"><span data-stu-id="af450-125">Quality</span></span>

<span data-ttu-id="af450-126">如果注意到外观网格上的扭曲，则需要确保项目使用适当数量的连接。</span><span class="sxs-lookup"><span data-stu-id="af450-126">If you notice distortions on the skinned mesh, you need to make sure your project is using the proper amount of joints.</span></span>
<span data-ttu-id="af450-127">转到 Unity 的编辑> Project 设置 >质量>其他>混合权重。</span><span class="sxs-lookup"><span data-stu-id="af450-127">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="af450-128">确保已选择"4 个关节"，以查看平滑联合。</span><span class="sxs-lookup"><span data-stu-id="af450-128">Make sure "4 bones" are selected to see Smooth Joints.</span></span>
<span data-ttu-id="af450-129">![Project设置](../images/hand-coach/MRTK_ProjectSettings.png)</span><span class="sxs-lookup"><span data-stu-id="af450-129">![Project Setting](../images/hand-coach/MRTK_ProjectSettings.png)</span></span>

## <a name="scripts"></a><span data-ttu-id="af450-130">脚本</span><span class="sxs-lookup"><span data-stu-id="af450-130">Scripts</span></span>

### <a name="interaction-hint"></a><span data-ttu-id="af450-131">交互提示</span><span class="sxs-lookup"><span data-stu-id="af450-131">Interaction hint</span></span>

<span data-ttu-id="af450-132">该 `InteractionHint.cs` 脚本提供包装器功能，用于触发手部工具的动画和淡入淡出。</span><span class="sxs-lookup"><span data-stu-id="af450-132">The `InteractionHint.cs` script provides wrapper functionality for triggering animations and fades for the hand rig.</span></span>

#### <a name="how-to-set-up-an-interaction-hint"></a><span data-ttu-id="af450-133">如何设置交互提示</span><span class="sxs-lookup"><span data-stu-id="af450-133">How to set up an interaction hint</span></span>

<span data-ttu-id="af450-134">若要设置交互提示，建议使用提供的预制项"StaticHandCoachRoot_L.prefab"和"StaticHandCoachRoot_R.prefab"。</span><span class="sxs-lookup"><span data-stu-id="af450-134">To set up an interaction hint, it is recommended to use the provided prefabs “StaticHandCoachRoot_L.prefab” and “StaticHandCoachRoot_R.prefab”.</span></span> <span data-ttu-id="af450-135">此预制项包含 InteractionHint 脚本和手部工具以及适当的层次结构，以确保提供的提示动画符合预期。</span><span class="sxs-lookup"><span data-stu-id="af450-135">This prefab contains the InteractionHint script and hand rig as well as the proper hierarchy to ensure that the provided hint animations work as intended.</span></span>
<span data-ttu-id="af450-136">否则，需要将脚本放在 gameObject 上，使用动画器从手部工具向上放置一个父级别。</span><span class="sxs-lookup"><span data-stu-id="af450-136">Otherwise, you'll need to place the script on a gameObject one parent level up from your hand rig with animator.</span></span>

#### <a name="inspector-properties"></a><span data-ttu-id="af450-137">检查器属性</span><span class="sxs-lookup"><span data-stu-id="af450-137">Inspector properties</span></span>

- <span data-ttu-id="af450-138">**HideIfHandTracked** 此布尔值指定在跟踪用户的手时，是否应当使用手部跟踪状态来隐藏视觉对象。</span><span class="sxs-lookup"><span data-stu-id="af450-138">**HideIfHandTracked** This boolean specifies whether hand tracking state should be used to hide visuals when a user’s hands are being tracked.</span></span> <span data-ttu-id="af450-139">如果设置为 false，则仅脚本属性"customShouldHideVisuals"用于确定是否隐藏提示。</span><span class="sxs-lookup"><span data-stu-id="af450-139">If this is set to false, only the scripting property “customShouldHideVisuals” will be used to determine whether to hide the hint.</span></span>

- <span data-ttu-id="af450-140">**MinDelay** 此属性指定显示视觉对象的最小延迟。</span><span class="sxs-lookup"><span data-stu-id="af450-140">**MinDelay** This property specifies the minimum delay for showing the visuals.</span></span> <span data-ttu-id="af450-141">默认情况下，如果未跟踪用户的手，则手部视觉对象将在此秒后显示。</span><span class="sxs-lookup"><span data-stu-id="af450-141">By default, the visuals for the hand will appear after this many seconds if the user’s hands are not being tracked.</span></span>

- <span data-ttu-id="af450-142">**MaxDelay** 此属性指定显示视觉对象的最大延迟。</span><span class="sxs-lookup"><span data-stu-id="af450-142">**MaxDelay** This property specifies the maximum delay for showing the visuals.</span></span> <span data-ttu-id="af450-143">默认情况下，即使跟踪用户的手，手部视觉对象也会在此秒后显示。</span><span class="sxs-lookup"><span data-stu-id="af450-143">By default, the visuals for the hand will appear after this many seconds even if the user’s hands are being tracked.</span></span>

- <span data-ttu-id="af450-144">**UseMaxTimer** 如果此布尔值设置为 false，它将禁用最大计时器，并且仅允许用户在手部无法查看或自定义条件返回 false 时显示手部提示。</span><span class="sxs-lookup"><span data-stu-id="af450-144">**UseMaxTimer** If this boolean is set to false, it disables the max timer and only allows the hand hint to be shown when the user’s hands are out of view, or the custom condition returns false.</span></span>

- <span data-ttu-id="af450-145">**重复** 此属性控制在最小或最大计时器通过时提示动画播放次数。</span><span class="sxs-lookup"><span data-stu-id="af450-145">**Repeats** This property controls how many times the hint animation plays when the min or max timer has passed.</span></span> <span data-ttu-id="af450-146">然后，提示将隐藏并再次等待延迟。</span><span class="sxs-lookup"><span data-stu-id="af450-146">The hint then hides and waits for the delay again.</span></span>

- <span data-ttu-id="af450-147">**AutoActivate** 当此布尔值设置为 true 时，当脚本的 GameObject 在层次结构中处于活动状态并启用脚本时，提示将自动通过计时器逻辑运行。</span><span class="sxs-lookup"><span data-stu-id="af450-147">**AutoActivate** When this boolean is set to true, the hint will automatically run through the timer logic when the GameObject of the script is active in the hierarchy and the script is enabled.</span></span> <span data-ttu-id="af450-148">只有打算通过代码手动控制提示外观和消失时，才应设置为 false。</span><span class="sxs-lookup"><span data-stu-id="af450-148">This should only be set to false if you intend to manually control the hint appearance and disappearance via code.</span></span>

- <span data-ttu-id="af450-149">**AnimationState** 提示处于活动状态时应播放的动画状态的名称。</span><span class="sxs-lookup"><span data-stu-id="af450-149">**AnimationState** The name of the animation state that should play when the hint is active.</span></span> <span data-ttu-id="af450-150">如果在 OnEnable 期间选中了 AutoActivate， () StartHintLoop (调用 StartHintLoop 函数之前，必须设置) 。</span><span class="sxs-lookup"><span data-stu-id="af450-150">This must be set before the StartHintLoop() function is called (during OnEnable if AutoActivate is checked).</span></span>

#### <a name="controlling-interactionhint-via-script"></a><span data-ttu-id="af450-151">通过脚本控制 InteractionHint</span><span class="sxs-lookup"><span data-stu-id="af450-151">Controlling InteractionHint via script</span></span>

- <span data-ttu-id="af450-152">**StartHintLoop** 如果 AutoActivate 标志设置为 true，此函数将启动显示/隐藏循环，否则启动 OnEnable。</span><span class="sxs-lookup"><span data-stu-id="af450-152">**StartHintLoop** This function starts the show/hide loop that otherwise starts OnEnable if the AutoActivate flag is set to true.</span></span>
- <span data-ttu-id="af450-153">**StopHintLoop** 如果当前未播放，此函数将调用淡出动画状态，然后停用显示/隐藏循环，并设置层次结构中的手部不活动。</span><span class="sxs-lookup"><span data-stu-id="af450-153">**StopHintLoop** This function calls the fade out animation state if it is not currently playing, then will deactivate the show/hide loop and set the hand rig inactive in the hierarchy.</span></span>
- <span data-ttu-id="af450-154">**AnimationState** 此字符串确定在循环期间播放的动画状态。</span><span class="sxs-lookup"><span data-stu-id="af450-154">**AnimationState** This string determines which animation state is played during the loop.</span></span> <span data-ttu-id="af450-155">可以更改此字符串以更改播放的状态，但在调用 StopHintLoop 后必须这样做，并且必须在更改状态后再次调用 StartHintLoop。</span><span class="sxs-lookup"><span data-stu-id="af450-155">You may change this string to change which state plays, but you must do so after calling StopHintLoop, and you must call StartHintLoop again after you have changed the state.</span></span>
- <span data-ttu-id="af450-156">**CustomShouldHideVisuals** 可以使用自己的函数对此进行设置，当想要隐藏手部视觉对象时，应返回 true (请记住 MinMaxTimer，特别是 max 参数) </span><span class="sxs-lookup"><span data-stu-id="af450-156">**CustomShouldHideVisuals** You can set this with your own function, which should return true when you want to hide the hand visuals (keep in mind the MinMaxTimer, specifically the max parameter)</span></span>

#### <a name="custom-animation-considerations"></a><span data-ttu-id="af450-157">自定义动画注意事项</span><span class="sxs-lookup"><span data-stu-id="af450-157">Custom animation considerations</span></span>

<span data-ttu-id="af450-158">淡入淡入淡出默认为 0.5 秒，因此，为与钻台一起创建的任何自定义动画应至少为 1.5 秒，以便传达任何有意义的信息</span><span class="sxs-lookup"><span data-stu-id="af450-158">Fades are defaulted to 0.5 seconds, so any custom animations created for use with the rig should be 1.5 seconds minimum for any meaningful information to be conveyed</span></span>

<span data-ttu-id="af450-159">提供的默认淡入和淡出状态Fade_In，Fade_Out通过更改第二个关键帧的时间戳来设置淡入淡出长度来调整其淡入和淡出状态。</span><span class="sxs-lookup"><span data-stu-id="af450-159">The provided default fade in and fade out states, Fade_In and Fade_Out may be adjusted by changing the timestamp of the second keyframe to set the fade length.</span></span>

<span data-ttu-id="af450-160">动画器和脚本的设置方式应使设置尽可能简单。</span><span class="sxs-lookup"><span data-stu-id="af450-160">The animator and script were set up in a way that should make setup as simple as possible.</span></span> <span data-ttu-id="af450-161">若要添加新动画状态，只需导入 fbx，确保动画名称设置有一个不同的名称，然后将该动画拖动到动画器中。</span><span class="sxs-lookup"><span data-stu-id="af450-161">To add new animation states, simply import your fbx, ensure the animation name is set with a distinct name, and drag that animation into the animator.</span></span>

### <a name="movetotarget"></a><span data-ttu-id="af450-162">MoveToTarget</span><span class="sxs-lookup"><span data-stu-id="af450-162">MoveToTarget</span></span>

<span data-ttu-id="af450-163">MoveToTarget.cs 脚本提供了一些功能，可随着时间的推移将手部提示从跟踪位置移动到目标位置。</span><span class="sxs-lookup"><span data-stu-id="af450-163">The MoveToTarget.cs script provides functionality to move the hand hint from a tracking position to a target position over time.</span></span>

#### <a name="how-to-set-up-movetotarget"></a><span data-ttu-id="af450-164">如何设置 MoveToTarget</span><span class="sxs-lookup"><span data-stu-id="af450-164">How to set up MoveToTarget</span></span>

<span data-ttu-id="af450-165">提供的预制项"MovingHandCoachRoot_L.prefab"和"MovingHandCoachRoot_R.prefab"在层次结构中包含 MoveToTarget。</span><span class="sxs-lookup"><span data-stu-id="af450-165">The provided prefabs “MovingHandCoachRoot_L.prefab” and “MovingHandCoachRoot_R.prefab” contain a MoveToTarget in their hierarchies.</span></span> <span data-ttu-id="af450-166">如果要在你自己的设置中使用此脚本，则需要将脚本放在根 gameobject 上，其中包含用于你的钻器的动画器。</span><span class="sxs-lookup"><span data-stu-id="af450-166">If you want to use this script on your own setup, you need to place it on the root gameobject containing the Animator for your rig.</span></span>

#### <a name="inspector-properties"></a><span data-ttu-id="af450-167">检查器属性</span><span class="sxs-lookup"><span data-stu-id="af450-167">Inspector properties</span></span>

- <span data-ttu-id="af450-168">**TrackingObject** 在设备开始其运动之前，将此选项设置为希望其遵循的对象。</span><span class="sxs-lookup"><span data-stu-id="af450-168">**TrackingObject** Set this with the object you want the rig to follow before it starts its motion.</span></span> <span data-ttu-id="af450-169">建议创建一个空 GameObject，并移动到特定位置，以帮助你查明跟踪。</span><span class="sxs-lookup"><span data-stu-id="af450-169">It is recommended to create an empty GameObject and move it to a specific position to help you pinpoint the tracking.</span></span>
- <span data-ttu-id="af450-170">**TargetObject** 将此选项设置为要在其运动过程中将钻设备移动到的对象。</span><span class="sxs-lookup"><span data-stu-id="af450-170">**TargetObject** Set this with the object you want the rig to move to during its motion.</span></span> <span data-ttu-id="af450-171">建议创建一个空 GameObject，并移动到特定位置，以帮助你查明跟踪。</span><span class="sxs-lookup"><span data-stu-id="af450-171">It is recommended to create an empty GameObject and move it to a specific position to help you pinpoint the tracking.</span></span>
- <span data-ttu-id="af450-172">**RootObject** 将此选项设置为跟踪对象和目标对象之间的共享父级，以便可以正确计算相对位置。</span><span class="sxs-lookup"><span data-stu-id="af450-172">**RootObject** Set this to a shared parent between tracking and target object so that the relative positions can be calculated correctly.</span></span> <span data-ttu-id="af450-173">包含的预制件在其层次结构中同时具有跟踪对象和目标对象，但可以将目标对象设置为预制件外部的 gameObject，将根对象更改为共享父级。</span><span class="sxs-lookup"><span data-stu-id="af450-173">The included prefab has both tracking and target objects in its hierarchy, but you can set the target object as a gameObject outside of the prefab and change the root object to a shared parent.</span></span>
- <span data-ttu-id="af450-174">**持续时间** 从 TrackingObject (TargetObject) 秒的时间。</span><span class="sxs-lookup"><span data-stu-id="af450-174">**Duration** The amount of time it should take (in seconds) to move from TrackingObject to TargetObject in seconds.</span></span>
- <span data-ttu-id="af450-175">**TargetOffset** 可调整的偏移量，使 GameObject 到达正确的目标位置。</span><span class="sxs-lookup"><span data-stu-id="af450-175">**TargetOffset** A tunable offset to get the GameObject to arrive at the right target position.</span></span> <span data-ttu-id="af450-176">如果动画在动画期间包含位置偏移量，则这很有用。</span><span class="sxs-lookup"><span data-stu-id="af450-176">This is useful if your animation includes a position offset during the animation.</span></span>
- <span data-ttu-id="af450-177">**AnimationCurve** 这默认为线性曲线，但可以更改曲线，在启动和停止运动路径时提供缓动。</span><span class="sxs-lookup"><span data-stu-id="af450-177">**AnimationCurve** This is defaulted to a linear curve, but you can alter the curve to provide easing in/out when starting and stopping the motion path.</span></span>

#### <a name="controlling-movetotarget-via-script"></a><span data-ttu-id="af450-178">通过脚本控制 MoveToTarget</span><span class="sxs-lookup"><span data-stu-id="af450-178">Controlling MoveToTarget via script</span></span>

<span data-ttu-id="af450-179">在自定义脚本中，在希望手部工具跟随 TrackingObject 时调用"跟踪 () "，然后在希望手部工具开始向 TargetObject 移动时调用 MoveToTargetPosition () 。</span><span class="sxs-lookup"><span data-stu-id="af450-179">In your custom script, make a call to Follow() while you want the hand rig to be following the TrackingObject, then make a call to MoveToTargetPosition() when you want the hand rig to begin its motion to the TargetObject.</span></span>

#### <a name="controlling-movetotarget-via-animations"></a><span data-ttu-id="af450-180">通过动画控制 MoveToTarget</span><span class="sxs-lookup"><span data-stu-id="af450-180">Controlling MoveToTarget via animations</span></span>

<span data-ttu-id="af450-181">在需要移动的动画中，设置两个事件：一个事件调用 Follow () ，另一个事件调用 MoveToTargetPosition () 。</span><span class="sxs-lookup"><span data-stu-id="af450-181">In the animation that needs to move, set two events: one with a call to Follow() and one with a call to MoveToTargetPosition().</span></span> <span data-ttu-id="af450-182">应在第一个关键帧上设置"关注"，因为它会导致手部工具跟随 TrackingObject。</span><span class="sxs-lookup"><span data-stu-id="af450-182">Follow should be set on the first keyframe, since it causes the hand rig to follow your TrackingObject.</span></span> <span data-ttu-id="af450-183">应在希望设备开始移动到目标的关键帧上设置 MoveToTargetPosition。</span><span class="sxs-lookup"><span data-stu-id="af450-183">MoveToTargetPosition should be set on the keyframe where you want the rig to begin moving to the target.</span></span> <span data-ttu-id="af450-184">这是脚本功能在提供的预制组件中的使用方式。</span><span class="sxs-lookup"><span data-stu-id="af450-184">This is how the script functionality is used in the provided prefabs.</span></span>

### <a name="rotatearoundpoint"></a><span data-ttu-id="af450-185">Rotate按UndPoint</span><span class="sxs-lookup"><span data-stu-id="af450-185">RotateAroundPoint</span></span>

<span data-ttu-id="af450-186">RotateAroundPoint.cs 脚本提供了在一段时间围绕透视点旋转手提示的功能。</span><span class="sxs-lookup"><span data-stu-id="af450-186">The RotateAroundPoint.cs script provides functionality to rotate the hand hint around a pivot point over time.</span></span>

#### <a name="how-to-set-up-rotatearoundpoint"></a><span data-ttu-id="af450-187">如何设置 RotateAroundPoint</span><span class="sxs-lookup"><span data-stu-id="af450-187">How to set up RotateAroundPoint</span></span>

<span data-ttu-id="af450-188">提供的预制件"RotatingHandCoachRoot_L.prefab"和"RotatingHandCoachRoot_R.prefab"在层次结构中包含 Rotate且undPoint。</span><span class="sxs-lookup"><span data-stu-id="af450-188">The provided prefabs “RotatingHandCoachRoot_L.prefab” and “RotatingHandCoachRoot_R.prefab” contain a RotateAroundPoint in their hierarchies.</span></span> <span data-ttu-id="af450-189">如果要在你自己的设置中使用此脚本，则需要将脚本放在根 gameobject 上，其中包含用于你的钻器的动画器。</span><span class="sxs-lookup"><span data-stu-id="af450-189">If you want to use this script on your own setup, you need to place it on the root gameobject containing the Animator for your rig.</span></span>

#### <a name="inspector-properties"></a><span data-ttu-id="af450-190">检查器属性</span><span class="sxs-lookup"><span data-stu-id="af450-190">Inspector properties</span></span>

- <span data-ttu-id="af450-191">**CenteredParent** 将此选项设置为希望设备四处透视的父对象。</span><span class="sxs-lookup"><span data-stu-id="af450-191">**CenteredParent** Set this with the parent object you want the rig to pivot around.</span></span>
- <span data-ttu-id="af450-192">**InverseParent** 将此选项与父级一起设置为"反向旋转"到"居中""参数"，以保持手部方向不变。</span><span class="sxs-lookup"><span data-stu-id="af450-192">**InverseParent** Set this with the parent to rotate inverse to centeredParent in order to keep the hand orientation the same.</span></span> <span data-ttu-id="af450-193">一般情况下，这将是其上具有 InteractionHint 脚本的父对象。</span><span class="sxs-lookup"><span data-stu-id="af450-193">In general, this will be the parent object with the InteractionHint script on it.</span></span>
- <span data-ttu-id="af450-194">**PivotPosition** 将此选项设置为希望提示开始移动的点。</span><span class="sxs-lookup"><span data-stu-id="af450-194">**PivotPosition** Set this to a point where you want the hint to start movement at.</span></span>
- <span data-ttu-id="af450-195">**持续时间** 围绕 CenteredParent 旋转 (需要) 秒。</span><span class="sxs-lookup"><span data-stu-id="af450-195">**Duration** The amount of time it should take (in seconds) to rotate around the CenteredParent.</span></span>
- <span data-ttu-id="af450-196">**AnimationCurve** 这默认为线性曲线，但可以更改曲线，在启动和停止运动路径时提供缓动。</span><span class="sxs-lookup"><span data-stu-id="af450-196">**AnimationCurve** This is defaulted to a linear curve, but you can alter the curve to provide easing in/out when starting and stopping the motion path.</span></span>
- <span data-ttu-id="af450-197">**RotationVector** 沿每个轴旋转的度数。</span><span class="sxs-lookup"><span data-stu-id="af450-197">**RotationVector** How many degrees to rotate along each axis.</span></span>

#### <a name="controlling-rotatearoundpoint-via-script"></a><span data-ttu-id="af450-198">通过脚本控制 RotateAroundPoint</span><span class="sxs-lookup"><span data-stu-id="af450-198">Controlling RotateAroundPoint via script</span></span>

<span data-ttu-id="af450-199">在自定义脚本中，在希望手部 () 在 CenteredParent 周围开始旋转时，调用 RotateToTarget 参数。</span><span class="sxs-lookup"><span data-stu-id="af450-199">In your custom script, make a call to RotateToTarget() when you want the hand rig to begin its rotation around the CenteredParent.</span></span> <span data-ttu-id="af450-200">若要将位置重置为原始 PivotPosition，请调用 ResetAndDeterminePivot () 。</span><span class="sxs-lookup"><span data-stu-id="af450-200">When you want the position to reset to the original PivotPosition, make a call to ResetAndDeterminePivot().</span></span>

#### <a name="controlling-rotatearoundpoint-via-animations"></a><span data-ttu-id="af450-201">通过动画控制 RotateAroundPoint</span><span class="sxs-lookup"><span data-stu-id="af450-201">Controlling RotateAroundPoint via animations</span></span>

<span data-ttu-id="af450-202">在需要移动的动画中，设置两个事件：一个事件调用 ResetAndDeterminePivot () ，另一个事件调用 RotateToTarget () 。</span><span class="sxs-lookup"><span data-stu-id="af450-202">In the animation that needs to move, set two events: one with a call to ResetAndDeterminePivot() and one with a call to RotateToTarget().</span></span> <span data-ttu-id="af450-203">应在第一个关键帧上设置 ResetAndDeterminePivot，因为它会导致手型装置重置为 PivotPosition。</span><span class="sxs-lookup"><span data-stu-id="af450-203">ResetAndDeterminePivot should be set on the first keyframe, since it causes the hand rig to reset to the PivotPosition.</span></span> <span data-ttu-id="af450-204">应在你希望远程测试机组在 CenteredParent 上开始旋转的关键帧上设置 RotateToTarget。</span><span class="sxs-lookup"><span data-stu-id="af450-204">RotateToTarget should be set on the keyframe where you want the rig to begin rotating around the CenteredParent.</span></span> <span data-ttu-id="af450-205">这就是在提供的 prototyping 中使用脚本功能的方式。</span><span class="sxs-lookup"><span data-stu-id="af450-205">This is how the script functionality is used in the provided prefabs.</span></span>
