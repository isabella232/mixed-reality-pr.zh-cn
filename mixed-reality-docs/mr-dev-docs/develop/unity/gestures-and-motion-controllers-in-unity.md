---
title: Unity 中的手势和运动控制器
description: 了解如何使用手型手势和运动控制器在 Unity 上执行操作。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 手势，运动控制器，unity，注视，输入，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，MRTK，混合现实工具包
ms.openlocfilehash: 8941fa05af21a7b2c7302f4a76f27cf38e1d5a65
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010318"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="0b9ef-104">Unity 中的手势和运动控制器</span><span class="sxs-lookup"><span data-stu-id="0b9ef-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="0b9ef-105">您可以通过两种主要方式在您的 [HMD 中进行](gaze-in-unity.md)操作，在 HoloLens 和沉浸式的中的 [手势](../../design/gaze-and-commit.md#composite-gestures) 和 [运动控制器](../../design/motion-controllers.md) 。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="0b9ef-106">可以通过 Unity 中的相同 Api 访问空间输入的两个源的数据。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="0b9ef-107">Unity 提供了两种主要方法来访问 Windows Mixed Reality 的空间输入数据。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="0b9ef-108">常见的 *GetButton/GetAxis* api 跨多个 Unity XR sdk 工作，而特定于 Windows Mixed Reality 的 *InteractionManager/GestureRecognizer* api 会公开一组完整的空间输入数据。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="0b9ef-109">Unity XR 输入 Api</span><span class="sxs-lookup"><span data-stu-id="0b9ef-109">Unity XR input APIs</span></span>

<span data-ttu-id="0b9ef-110">对于新项目，建议从头开始使用新的 XR 输入 Api。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-110">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="0b9ef-111">可在此处找到有关 [XR api](https://docs.unity3d.com/Manual/xr_input.html)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-111">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="0b9ef-112">Unity 按钮/轴映射表</span><span class="sxs-lookup"><span data-stu-id="0b9ef-112">Unity button/axis mapping table</span></span>

<span data-ttu-id="0b9ef-113">适用于 Windows Mixed Reality 运动控制器的 Unity 输入管理器支持通过 *GetButton/GetAxis* api 在下面列出的按钮和轴 id。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-113">Unity's Input Manager for Windows Mixed Reality motion controllers supports the button and axis IDs listed below through the *Input.GetButton/GetAxis* APIs.</span></span> <span data-ttu-id="0b9ef-114">"Windows MR 特定" 列是指 *InteractionSourceState* 类型可用的属性。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-114">The "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="0b9ef-115">以下各节将详细介绍其中的每个 Api。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-115">Each of these APIs is described in detail in the sections below.</span></span>

<span data-ttu-id="0b9ef-116">Windows Mixed Reality 的按钮/轴 ID 映射通常与 Oculus 按钮/轴 Id 匹配。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-116">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="0b9ef-117">Windows Mixed Reality 的按钮/轴 ID 映射在以下两个方面不同于 OpenVR 的映射：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-117">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="0b9ef-118">该映射使用不同于操纵杆的触摸板 Id，以支持同时具有 thumbsticks 和触摸板的控制器。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-118">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="0b9ef-119">映射避免了对菜单按钮的 A 和 X 按钮 Id 进行重载，以使它们可用于物理 ABXY 按钮。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-119">The mapping avoids overloading the A and X button IDs for the Menu buttons to leave them available for the physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="0b9ef-120">输入</span><span class="sxs-lookup"><span data-stu-id="0b9ef-120">Input</span></span> </th><th colspan="2"><span data-ttu-id="0b9ef-121"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">通用 Unity API</a></span><span class="sxs-lookup"><span data-stu-id="0b9ef-121"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="0b9ef-122"> (GetButton/GetAxis) </span><span class="sxs-lookup"><span data-stu-id="0b9ef-122">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="0b9ef-123"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR 专用输入 API</a></span><span class="sxs-lookup"><span data-stu-id="0b9ef-123"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="0b9ef-124"> (XR。WSA.输入) </span><span class="sxs-lookup"><span data-stu-id="0b9ef-124">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="0b9ef-125">左手</span><span class="sxs-lookup"><span data-stu-id="0b9ef-125">Left hand</span></span> </th><th> <span data-ttu-id="0b9ef-126">右手</span><span class="sxs-lookup"><span data-stu-id="0b9ef-126">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="0b9ef-127">选择触发按下</span><span class="sxs-lookup"><span data-stu-id="0b9ef-127">Select trigger pressed</span></span> </td><td> <span data-ttu-id="0b9ef-128">轴 9 = 1。0</span><span class="sxs-lookup"><span data-stu-id="0b9ef-128">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="0b9ef-129">轴 10 = 1。0</span><span class="sxs-lookup"><span data-stu-id="0b9ef-129">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="0b9ef-130">selectPressed</span><span class="sxs-lookup"><span data-stu-id="0b9ef-130">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-131">选择触发器模拟值</span><span class="sxs-lookup"><span data-stu-id="0b9ef-131">Select trigger analog value</span></span> </td><td> <span data-ttu-id="0b9ef-132">轴9</span><span class="sxs-lookup"><span data-stu-id="0b9ef-132">Axis 9</span></span> </td><td> <span data-ttu-id="0b9ef-133">轴10</span><span class="sxs-lookup"><span data-stu-id="0b9ef-133">Axis 10</span></span> </td><td> <span data-ttu-id="0b9ef-134">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="0b9ef-134">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-135">选择触发器部分按下</span><span class="sxs-lookup"><span data-stu-id="0b9ef-135">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="0b9ef-136">按钮 14 <i> (游戏板兼容) </i> </span><span class="sxs-lookup"><span data-stu-id="0b9ef-136">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="0b9ef-137">按钮 15 <i> (游戏板兼容) </i> </span><span class="sxs-lookup"><span data-stu-id="0b9ef-137">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="0b9ef-138">selectPressedAmount &gt; 0。0</span><span class="sxs-lookup"><span data-stu-id="0b9ef-138">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-139">按下菜单按钮</span><span class="sxs-lookup"><span data-stu-id="0b9ef-139">Menu button pressed</span></span> </td><td> <span data-ttu-id="0b9ef-140">按钮 6 \*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-140">Button 6\*</span></span> </td><td> <span data-ttu-id="0b9ef-141">按钮 7 \*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-141">Button 7\*</span></span> </td><td> <span data-ttu-id="0b9ef-142">menuPressed</span><span class="sxs-lookup"><span data-stu-id="0b9ef-142">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-143">按下手柄按钮</span><span class="sxs-lookup"><span data-stu-id="0b9ef-143">Grip button pressed</span></span> </td><td> <span data-ttu-id="0b9ef-144">Axis 11 = 1.0 (没有模拟值) </span><span class="sxs-lookup"><span data-stu-id="0b9ef-144">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="0b9ef-145">按钮 4 <i> (游戏板兼容) </i> </span><span class="sxs-lookup"><span data-stu-id="0b9ef-145">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="0b9ef-146">轴 12 = 1.0 (没有模拟值) </span><span class="sxs-lookup"><span data-stu-id="0b9ef-146">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="0b9ef-147">按钮 5 <i> (游戏板兼容) </i> </span><span class="sxs-lookup"><span data-stu-id="0b9ef-147">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="0b9ef-148">grasped</span><span class="sxs-lookup"><span data-stu-id="0b9ef-148">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-149">操纵杆 X <i> (左：-1.0，right： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="0b9ef-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="0b9ef-150">轴1</span><span class="sxs-lookup"><span data-stu-id="0b9ef-150">Axis 1</span></span> </td><td> <span data-ttu-id="0b9ef-151">轴4</span><span class="sxs-lookup"><span data-stu-id="0b9ef-151">Axis 4</span></span> </td><td> <span data-ttu-id="0b9ef-152">thumbstickPosition</span><span class="sxs-lookup"><span data-stu-id="0b9ef-152">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-153">操纵杆 Y <i> (顶部：-1.0、底部： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="0b9ef-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="0b9ef-154">轴2</span><span class="sxs-lookup"><span data-stu-id="0b9ef-154">Axis 2</span></span> </td><td> <span data-ttu-id="0b9ef-155">轴5</span><span class="sxs-lookup"><span data-stu-id="0b9ef-155">Axis 5</span></span> </td><td> <span data-ttu-id="0b9ef-156">thumbstickPosition</span><span class="sxs-lookup"><span data-stu-id="0b9ef-156">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-157">已按下操纵杆</span><span class="sxs-lookup"><span data-stu-id="0b9ef-157">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="0b9ef-158">按钮8</span><span class="sxs-lookup"><span data-stu-id="0b9ef-158">Button 8</span></span> </td><td> <span data-ttu-id="0b9ef-159">按钮9</span><span class="sxs-lookup"><span data-stu-id="0b9ef-159">Button 9</span></span> </td><td> <span data-ttu-id="0b9ef-160">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="0b9ef-160">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-161">触摸板 X <i> (左：-1.0，右： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="0b9ef-161">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="0b9ef-162">轴 17 \*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-162">Axis 17\*</span></span> </td><td> <span data-ttu-id="0b9ef-163">轴 19 \*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-163">Axis 19\*</span></span> </td><td> <span data-ttu-id="0b9ef-164">touchpadPosition</span><span class="sxs-lookup"><span data-stu-id="0b9ef-164">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-165">触摸板 Y <i> (顶部：-1.0、底部： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="0b9ef-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="0b9ef-166">Axis 18 \*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-166">Axis 18\*</span></span> </td><td> <span data-ttu-id="0b9ef-167">轴 20 \*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-167">Axis 20\*</span></span> </td><td> <span data-ttu-id="0b9ef-168">touchpadPosition</span><span class="sxs-lookup"><span data-stu-id="0b9ef-168">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-169">接触触摸板</span><span class="sxs-lookup"><span data-stu-id="0b9ef-169">Touchpad touched</span></span> </td><td> <span data-ttu-id="0b9ef-170">按钮 18 \*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-170">Button 18\*</span></span> </td><td> <span data-ttu-id="0b9ef-171">按钮 19 \*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-171">Button 19\*</span></span> </td><td> <span data-ttu-id="0b9ef-172">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="0b9ef-172">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-173">已按触摸板</span><span class="sxs-lookup"><span data-stu-id="0b9ef-173">Touchpad pressed</span></span> </td><td> <span data-ttu-id="0b9ef-174">按钮 16 \*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-174">Button 16\*</span></span> </td><td> <span data-ttu-id="0b9ef-175">按钮 17 \*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-175">Button 17\*</span></span> </td><td> <span data-ttu-id="0b9ef-176">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="0b9ef-176">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-177">6DoF 手柄姿势或指针姿势</span><span class="sxs-lookup"><span data-stu-id="0b9ef-177">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="0b9ef-178">仅限<i>抓握</i>： <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR。InputTracking. GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="0b9ef-178"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="0b9ef-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="0b9ef-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="0b9ef-180">Pass <i>手柄</i> 或 <i>指针</i> 作为参数： SourceState. sourcePose. TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="0b9ef-180">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="0b9ef-181">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="0b9ef-181">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-182">跟踪状态</span><span class="sxs-lookup"><span data-stu-id="0b9ef-182">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="0b9ef-183"><i>位置准确性和源丢失风险仅通过 MR 专用 API 提供</i> </span><span class="sxs-lookup"><span data-stu-id="0b9ef-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="0b9ef-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="0b9ef-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="0b9ef-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="0b9ef-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="0b9ef-186">这些按钮/轴 Id 不同于 Unity 用于 OpenVR 的 Id，因为 gamepads、Oculus 触控和 OpenVR 所使用的映射中出现冲突。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-186">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="0b9ef-187">手柄姿势与指针姿势</span><span class="sxs-lookup"><span data-stu-id="0b9ef-187">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="0b9ef-188">Windows Mixed Reality 支持各种外形规格的运动控制器。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-188">Windows Mixed Reality supports motion controllers in a variety of form factors.</span></span> <span data-ttu-id="0b9ef-189">每个控制器的设计不同于用户的位置与应用在呈现控制器时使用的自然 "转发" 方向之间的关系。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-189">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="0b9ef-190">为了更好地表示这些控制器，可以针对每个交互源来调查两种类型的姿势， **手柄姿势** 和 **指针姿势**。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-190">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="0b9ef-191">手柄姿势和指针姿势坐标都由全局 Unity 世界坐标中的所有 Unity Api 表示。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-191">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="0b9ef-192">抓握姿势</span><span class="sxs-lookup"><span data-stu-id="0b9ef-192">Grip pose</span></span>

<span data-ttu-id="0b9ef-193">**抓握姿势** 表示用户掌的位置，由 HoloLens 检测到或持有运动控制器。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-193">The **grip pose** represents the location of the users palm, either detected by a HoloLens or holding a motion controller.</span></span>

<span data-ttu-id="0b9ef-194">在沉浸式耳机上，手柄姿势最适合用于呈现 **用户的手** 或 **持有用户的对象**。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-194">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**.</span></span> <span data-ttu-id="0b9ef-195">可视化运动控制器时也使用手柄姿势。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-195">The grip pose is also used when visualizing a motion controller.</span></span> <span data-ttu-id="0b9ef-196">用于运动控制器的 Windows 提供的 **呈现模型** 使用手柄姿势作为原点和旋转中心。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-196">The **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="0b9ef-197">手柄姿势的定义具体如下：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-197">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="0b9ef-198">**手柄位置**：在固定控制器时，掌上质心，向左或向右调整以使其在手柄内居中。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-198">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="0b9ef-199">在 Windows Mixed Reality 运动控制器上，此位置通常与 "抓住" 按钮对齐。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-199">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="0b9ef-200">**手柄方向的右轴**：当你完全打开手形成一个平面的5指形姿势时，与你的掌上的光线 (从右手掌向后) </span><span class="sxs-lookup"><span data-stu-id="0b9ef-200">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="0b9ef-201">**手柄方向的正向轴**：当您关闭手中的部分 (时，就如同按住控制器) 一样，通过您的非拇指形来表示 "转发" 的射线。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-201">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="0b9ef-202">**手柄方向的上轴**：向右和向后定义隐含的上轴。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-202">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="0b9ef-203">可以通过 Unity 的跨供应商输入 API (XR 来访问抓握姿势 *[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/旋转*) 或通过 WINDOWS MR (*sourcePose*，请求) 请求为 **抓握** 节点提供数据。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-203">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="0b9ef-204">指针姿势</span><span class="sxs-lookup"><span data-stu-id="0b9ef-204">Pointer pose</span></span>

<span data-ttu-id="0b9ef-205">**指针姿势** 代表着控制器的末端。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-205">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="0b9ef-206">系统提供的指针姿势最适合用于在 **呈现控制器模型本身** 时进行 raycast。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-206">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="0b9ef-207">如果要渲染某个其他虚拟对象来替代控制器（如虚拟压力），则应指出该虚拟对象的最自然的射线，如沿应用定义的机枪模型的桶向下移动的射线。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-207">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that's most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="0b9ef-208">由于用户可以看到虚拟对象，而不是物理控制器，因此，使用虚拟对象指向虚拟对象可能会更自然地使用应用。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-208">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="0b9ef-209">目前，指针姿势仅通过 Windows MR 专用 API TryGetPosition/轮换提供，并传入 InteractionSourceNode 作为参数传递 。 *sourceState/sourcePose。*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-209">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="0b9ef-210">控制器跟踪状态</span><span class="sxs-lookup"><span data-stu-id="0b9ef-210">Controller tracking state</span></span>

<span data-ttu-id="0b9ef-211">与耳机一样，Windows Mixed Reality 运动控制器不需要外部跟踪传感器的设置。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-211">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="0b9ef-212">相反，控制器由耳机本身中的传感器跟踪。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-212">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="0b9ef-213">如果用户将控制器移出耳机的视图，则在大多数情况下，Windows 将继续推断控制器位置。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-213">If the user moves the controllers out of the headset's field of view, Windows continues to infer controller positions in most cases.</span></span> <span data-ttu-id="0b9ef-214">如果控制器丢失了足够长时间的视觉跟踪，控制器的位置将降到近似准确性位置。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-214">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="0b9ef-215">此时，系统会将控制器正文锁定到用户，在移动用户时跟踪用户的位置，同时仍然使用其内部方向传感器公开控制器的真正方向。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-215">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="0b9ef-216">许多使用控制器指向和激活 UI 元素的应用程序可以正常运行，而无需用户注意。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-216">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="0b9ef-217">为此，最好的方法是亲自尝试一下。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-217">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="0b9ef-218">查看此视频，其中包含可在各种跟踪状态下使用运动控制器的沉浸式内容的示例：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-218">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="0b9ef-219">显式跟踪状态的推理</span><span class="sxs-lookup"><span data-stu-id="0b9ef-219">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="0b9ef-220">希望根据跟踪状态以不同方式对位置进行处理的应用可能会进一步检查控制器状态的属性，如 *SourceLossRisk* 和 *PositionAccuracy*：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-220">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="0b9ef-221">跟踪状态</span><span class="sxs-lookup"><span data-stu-id="0b9ef-221">Tracking state</span></span> </th><th> <span data-ttu-id="0b9ef-222">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="0b9ef-222">SourceLossRisk</span></span> </th><th> <span data-ttu-id="0b9ef-223">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="0b9ef-223">PositionAccuracy</span></span> </th><th> <span data-ttu-id="0b9ef-224">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="0b9ef-224">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="0b9ef-225"><b>高准确度</b> </span><span class="sxs-lookup"><span data-stu-id="0b9ef-225"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="0b9ef-226">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="0b9ef-226">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="0b9ef-227">高</span><span class="sxs-lookup"><span data-stu-id="0b9ef-227">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="0b9ef-228">true</span><span class="sxs-lookup"><span data-stu-id="0b9ef-228">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-229"><b>高准确度 (丢失) 的风险 </b> </span><span class="sxs-lookup"><span data-stu-id="0b9ef-229"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="0b9ef-230">= = 1。0</span><span class="sxs-lookup"><span data-stu-id="0b9ef-230">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="0b9ef-231">高</span><span class="sxs-lookup"><span data-stu-id="0b9ef-231">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="0b9ef-232">true</span><span class="sxs-lookup"><span data-stu-id="0b9ef-232">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-233"><b>近似准确度</b> </span><span class="sxs-lookup"><span data-stu-id="0b9ef-233"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="0b9ef-234">= = 1。0</span><span class="sxs-lookup"><span data-stu-id="0b9ef-234">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="0b9ef-235">近似</span><span class="sxs-lookup"><span data-stu-id="0b9ef-235">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="0b9ef-236">true</span><span class="sxs-lookup"><span data-stu-id="0b9ef-236">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0b9ef-237"><b>无位置</b> </span><span class="sxs-lookup"><span data-stu-id="0b9ef-237"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="0b9ef-238">= = 1。0</span><span class="sxs-lookup"><span data-stu-id="0b9ef-238">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="0b9ef-239">近似</span><span class="sxs-lookup"><span data-stu-id="0b9ef-239">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="0b9ef-240">false</span><span class="sxs-lookup"><span data-stu-id="0b9ef-240">false</span></span></td>
</tr>
</table>

<span data-ttu-id="0b9ef-241">这些运动控制器跟踪状态的定义如下：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-241">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="0b9ef-242">**高准确度：** 尽管运动控制器位于耳机的视图中，但它通常会根据视觉对象跟踪提供高准确性位置。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-242">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="0b9ef-243">一种移动控制器，该控制器暂时离开了 "查看" 字段或暂时不能从耳机传感器中遮盖 (例如，根据用户的另一种情况，) 将继续根据控制器本身的惯性跟踪来返回高准确度姿势。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-243">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="0b9ef-244">**高准确度 (丢失) 的风险：** 当用户将运动控制器移出耳机的视图边缘后，耳机不久就无法直观地跟踪控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-244">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="0b9ef-245">此应用通过查看 **SourceLossRisk** 到1.0，来了解控制器何时到达此 FOV 边界。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-245">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="0b9ef-246">此时，应用程序可以选择暂停需要稳定的高质量姿势流的控制器手势。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-246">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="0b9ef-247">**近似准确性：** 如果控制器丢失了足够长时间的视觉跟踪，控制器的位置将降到近似准确性位置。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-247">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="0b9ef-248">此时，系统会将控制器正文锁定到用户，在移动用户时跟踪用户的位置，同时仍然使用其内部方向传感器公开控制器的真正方向。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-248">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="0b9ef-249">许多使用控制器指向和激活 UI 元素的应用程序可以正常运行，而无需用户注意。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-249">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="0b9ef-250">对于输入要求较高的应用，可以通过检查 **PositionAccuracy** 属性，从 **高** 准确度到 **接近** 准确性，从而为用户提供更多的 hitbox。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-250">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="0b9ef-251">**无位置：** 尽管控制器可以在很长时间内正常运行，但有时系统也知道，甚至在当前情况下，该位置都没有意义。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-251">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="0b9ef-252">例如，已打开的控制器可能从未被可视化地观察到，或者用户可能会关闭控制器，然后由其他人选取。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-252">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="0b9ef-253">在这种情况下，系统不会提供应用程序的任何位置，并且 *TryGetPosition* 将返回 false。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-253">At those times, the system won't provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="0b9ef-254">常见 Unity Api (GetButton/GetAxis) </span><span class="sxs-lookup"><span data-stu-id="0b9ef-254">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="0b9ef-255">**命名空间：** *UnityEngine*、 *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-255">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="0b9ef-256">**类型**： *输入*， *XR。InputTracking*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-256">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="0b9ef-257">Unity 目前使用其常规 *输入. GetButton/GetAxis* Api 公开 [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)、 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) 和 Windows Mixed Reality 的输入，包括双手和运动控制器。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-257">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="0b9ef-258">如果你的应用程序使用这些 Api 进行输入，则它可以在多个 XR Sdk （包括 Windows Mixed Reality）中轻松支持运动控制器。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-258">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="0b9ef-259">获取逻辑按钮的按下状态</span><span class="sxs-lookup"><span data-stu-id="0b9ef-259">Getting a logical button's pressed state</span></span>

<span data-ttu-id="0b9ef-260">若要使用一般 Unity 输入 Api，通常先将按钮和轴向上滑到 [Unity 输入管理器](https://docs.unity3d.com/Manual/ConventionalGameInput.html)中的逻辑名称，然后将按钮或轴 id 绑定到每个名称。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-260">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="0b9ef-261">然后，你可以编写引用该逻辑按钮/轴名称的代码。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-261">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="0b9ef-262">例如，若要将左运动控制器的触发器按钮映射到 "提交" 操作，请在 Unity 内执行 " **编辑 > 项目设置" > 输入** ，然后展开 "轴" 下 "提交" 部分的属性。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-262">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="0b9ef-263">更改 " **正按钮** " 或 " **Alt 正** 向按钮" 属性以阅读 **游戏杆按钮 14**，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-263">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="0b9ef-264">![Unity 的 InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="0b9ef-264">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="0b9ef-265">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-265">*Unity InputManager*</span></span>

<span data-ttu-id="0b9ef-266">然后，你的脚本可以使用 *GetButton* 检查提交操作：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-266">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="0b9ef-267">可以通过在 "**轴**" 下更改 " **Size** " 属性来添加更多逻辑按钮。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-267">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="0b9ef-268">直接获取物理按钮的按下状态</span><span class="sxs-lookup"><span data-stu-id="0b9ef-268">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="0b9ef-269">还可以使用 *GetKey*，通过其完全限定的名称手动访问按钮：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-269">You can also access buttons manually by their fully qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="0b9ef-270">获取手或运动控制器的姿势</span><span class="sxs-lookup"><span data-stu-id="0b9ef-270">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="0b9ef-271">可以使用 XR 访问控制器的位置和旋转 *。InputTracking*：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-271">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> <span data-ttu-id="0b9ef-272">上面的代码代表控制器的手柄姿势 (其中，用户在其中保存控制器) ，这对于渲染用户的剑或压力或控制器本身的模型非常有用。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-272">The above code represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>
> 
> <span data-ttu-id="0b9ef-273">这种控制手柄的关系导致，指针 (在控制器的笔尖指向) 在控制器之间可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-273">The relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="0b9ef-274">目前，仅通过 MR 专用输入 API （在以下各节中介绍）才能访问控制器的指针姿势。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-274">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="0b9ef-275"> (XR 的特定于 Windows 的 Api。WSA.输入) </span><span class="sxs-lookup"><span data-stu-id="0b9ef-275">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="0b9ef-276">如果你的项目使用的是任何 XR。WSA Api 在未来的 Unity 版本中，这些 Api 将在 XR SDK 的后面逐步推出。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-276">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="0b9ef-277">对于新项目，建议从头开始使用 XR SDK。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-277">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="0b9ef-278">可在此处找到有关 [XR 输入系统和 api](https://docs.unity3d.com/Manual/xr_input.html)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-278">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="0b9ef-279">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-279">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="0b9ef-280">**类型**： *InteractionManager*、 *InteractionSourceState*、 *InteractionSource*、 *InteractionSourceProperties*、 *InteractionSourceKind*、 *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-280">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="0b9ef-281">若要获取有关 HoloLens) 和运动控制器的 Windows Mixed Reality 手型输入 (的更多详细信息，可以选择在 *XR* 命名空间下使用特定于 windows 的空间输入 api。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-281">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="0b9ef-282">这样，你就可以访问其他信息，例如位置准确性或源种类，使你可以区分手和控制器。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-282">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="0b9ef-283">对双手和运动控制器的状态进行轮询</span><span class="sxs-lookup"><span data-stu-id="0b9ef-283">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="0b9ef-284">使用 *GetCurrentReading* 方法，可以轮询每个交互源 (手型或运动控制器) 的此帧状态。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-284">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="0b9ef-285">返回的每个 *InteractionSourceState* 表示当前时刻的交互源。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-285">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="0b9ef-286">*InteractionSourceState* 显示如下信息：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-286">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="0b9ef-287"> (选择/菜单/抓住/触摸板/操纵杆) 出现哪些[类型的按下](../../design/motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="0b9ef-287">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="0b9ef-288">其他特定于运动控制器的数据，例如触摸板和/或操纵杆的 XY 坐标和接触状态</span><span class="sxs-lookup"><span data-stu-id="0b9ef-288">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="0b9ef-289">要了解源是手型还是运动控制器的 InteractionSourceKind</span><span class="sxs-lookup"><span data-stu-id="0b9ef-289">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="0b9ef-290">轮询前向预测呈现姿势</span><span class="sxs-lookup"><span data-stu-id="0b9ef-290">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="0b9ef-291">当轮询来自双手和控制器的交互源数据时，您获得的是向前预测的，这是框架的 photons 将达到用户的眼睛。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-291">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="0b9ef-292">向前预测的姿势最适合用于 **呈现** 控制器或每个帧的持有对象。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-292">Forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="0b9ef-293">如果使用的是针对控制器的给定按下或发布，则在使用下面所述的历史事件 Api 时，这将是最准确的。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-293">If you're targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="0b9ef-294">你还可以获取此当前帧的前推预测 head。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-294">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="0b9ef-295">与源姿势一样，这对于 **呈现** 游标非常有用，但如果你使用下面所述的历史事件 api，则以给定的按下或释放为目标是最准确的。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-295">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="0b9ef-296">处理交互源事件</span><span class="sxs-lookup"><span data-stu-id="0b9ef-296">Handling interaction source events</span></span>

<span data-ttu-id="0b9ef-297">若要在输入事件的准确历史记录数据发生时处理输入事件，可处理交互源事件，而不是轮询。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-297">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="0b9ef-298">处理交互源事件：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-298">To handle interaction source events:</span></span>
* <span data-ttu-id="0b9ef-299">注册 *InteractionManager* 输入事件。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-299">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="0b9ef-300">对于你感兴趣的每种类型的交互事件，你需要订阅该事件。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-300">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="0b9ef-301">处理事件。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-301">Handle the event.</span></span> <span data-ttu-id="0b9ef-302">订阅交互事件后，会在适当的时候获取回调。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-302">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="0b9ef-303">在 *SourcePressed* 示例中，这会在检测到源后、发布或丢失之前。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-303">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="0b9ef-304">如何停止处理事件</span><span class="sxs-lookup"><span data-stu-id="0b9ef-304">How to stop handling an event</span></span>

<span data-ttu-id="0b9ef-305">如果不再对事件感兴趣或正在销毁已订阅事件的对象，则需要停止处理事件。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-305">You need to stop handling an event when you're no longer interested in the event or you're destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="0b9ef-306">若要停止处理事件，请取消订阅该事件。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-306">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="0b9ef-307">交互源事件的列表</span><span class="sxs-lookup"><span data-stu-id="0b9ef-307">List of interaction source events</span></span>

<span data-ttu-id="0b9ef-308">可用的交互源事件包括：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-308">The available interaction source events are:</span></span>
* <span data-ttu-id="0b9ef-309">*InteractionSourceDetected* (源成为活动) </span><span class="sxs-lookup"><span data-stu-id="0b9ef-309">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="0b9ef-310">*InteractionSourceLost* (变为非活动状态) </span><span class="sxs-lookup"><span data-stu-id="0b9ef-310">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="0b9ef-311">*InteractionSourcePressed* (点击，按下按钮或 "选择" 失措) </span><span class="sxs-lookup"><span data-stu-id="0b9ef-311">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="0b9ef-312">*InteractionSourceReleased* (点击、按钮已释放或结束 "Select" 失措) </span><span class="sxs-lookup"><span data-stu-id="0b9ef-312">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="0b9ef-313">*InteractionSourceUpdated* (移动或以其他方式更改某种状态) </span><span class="sxs-lookup"><span data-stu-id="0b9ef-313">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="0b9ef-314">最准确地匹配新闻或发布的历史目标姿势的事件</span><span class="sxs-lookup"><span data-stu-id="0b9ef-314">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="0b9ef-315">前面所述的轮询 Api 为应用程序带来了前推预测的姿势。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-315">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="0b9ef-316">尽管这些预测的姿势最适用于渲染控制器或虚拟手持对象，但出于以下两个重要原因，未来的姿势并不是最佳目标：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-316">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses aren't optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="0b9ef-317">当用户按下控制器上的某个按钮时，系统收到该按键之前，蓝牙上可能会出现大约 20 ms 的无线延迟。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-317">When the user presses a button on a controller, there can be about 20 ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="0b9ef-318">然后，如果您使用的是前推预测型，则会有另一个 10-20 ms 应用于当前帧的 photons 将达到用户眼睛的时间。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-318">Then, if you're using a forward-predicted pose, there would be another 10-20 ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="0b9ef-319">这意味着，轮询会为你提供源姿势或 head 型，即从用户的头和用户在按下或释放发生时实际返回的位置为30-40 毫秒。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-319">This means that polling gives you a source pose or head pose that is 30-40 ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="0b9ef-320">对于 HoloLens 手写输入，在没有无线传输延迟的情况下，可以使用类似的处理延迟来检测按键。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-320">For HoloLens hand input, while there's no wireless transmission delay, there's a similar processing delay to detect the press.</span></span>

<span data-ttu-id="0b9ef-321">若要精确地根据用户的原始意图或按下控制器，应使用来自该 *InteractionSourcePressed* 或 *InteractionSourceReleased* 输入事件的历史源姿势或 head 姿势。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-321">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="0b9ef-322">你可以从用户的头或其控制器使用历史姿势数据作为新闻或发布的目标：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-322">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="0b9ef-323">当该笔势或控制器按下时，头姿势会出现， **可用于确定** 用户的 [gazing](../../design/gaze-and-commit.md) ：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-323">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="0b9ef-324">当运动控制器按下时，源会出现，这可用于确定用户在何处定位控制器的 **目标** 。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-324">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="0b9ef-325">这将是遇到按下的控制器的状态。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-325">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="0b9ef-326">如果要渲染控制器本身，则可以请求指针（而不是手柄姿势），以从用户将考虑呈现的控制器的自然提示的那种情况下生成目标射线：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-326">If you're rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="0b9ef-327">事件处理程序示例</span><span class="sxs-lookup"><span data-stu-id="0b9ef-327">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="0b9ef-328">高级别复合手势 Api (GestureRecognizer) </span><span class="sxs-lookup"><span data-stu-id="0b9ef-328">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="0b9ef-329">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-329">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="0b9ef-330">**类型**： *GestureRecognizer*、 *GestureSettings*、 *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-330">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="0b9ef-331">您的应用程序还可以识别空间输入源、点击、保持、操作和导航笔势的更高级复合手势。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-331">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation, and Navigation gestures.</span></span> <span data-ttu-id="0b9ef-332">您可以使用 GestureRecognizer 在 [手](../../design/gaze-and-commit.md#composite-gestures) 和 [运动控制器](../../design/motion-controllers.md) 中识别这些组合手势。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-332">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="0b9ef-333">GestureRecognizer 上的每个手势事件都提供输入的 SourceKind，以及事件发生时的目标 head 射线。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-333">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="0b9ef-334">某些事件提供其他特定于上下文的信息。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-334">Some events provide additional context-specific information.</span></span>

<span data-ttu-id="0b9ef-335">使用手势识别器捕获手势只需几个步骤：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-335">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="0b9ef-336">创建新的手势识别器</span><span class="sxs-lookup"><span data-stu-id="0b9ef-336">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="0b9ef-337">指定要监视的手势</span><span class="sxs-lookup"><span data-stu-id="0b9ef-337">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="0b9ef-338">订阅这些手势的事件</span><span class="sxs-lookup"><span data-stu-id="0b9ef-338">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="0b9ef-339">开始捕获手势</span><span class="sxs-lookup"><span data-stu-id="0b9ef-339">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="0b9ef-340">创建新的手势识别器</span><span class="sxs-lookup"><span data-stu-id="0b9ef-340">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="0b9ef-341">若要使用 *GestureRecognizer*，必须创建 *GestureRecognizer*：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-341">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="0b9ef-342">指定要监视的手势</span><span class="sxs-lookup"><span data-stu-id="0b9ef-342">Specify which gestures to watch for</span></span>

<span data-ttu-id="0b9ef-343">通过 SetRecognizableGestures 指定你对其感兴趣的手势 *( # B1*：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-343">Specify which gestures you're interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="0b9ef-344">订阅这些手势的事件</span><span class="sxs-lookup"><span data-stu-id="0b9ef-344">Subscribe to events for those gestures</span></span>

<span data-ttu-id="0b9ef-345">订阅你感兴趣的手势的事件。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-345">Subscribe to events for the gestures you're interested in.</span></span>

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
><span data-ttu-id="0b9ef-346">导航和操作手势在 *GestureRecognizer* 的实例上互相排斥。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-346">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="0b9ef-347">开始捕获手势</span><span class="sxs-lookup"><span data-stu-id="0b9ef-347">Start capturing gestures</span></span>

<span data-ttu-id="0b9ef-348">默认情况下，在调用 *StartCapturingGestures ( # B1* 之前， *GestureRecognizer* 不监视输入。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-348">By default, a *GestureRecognizer* doesn't monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="0b9ef-349">如果在处理 *StopCapturingGestures ( # B3* 的帧之前执行了输入，则可能会在 *StopCapturingGestures ( # B1* 之后生成笔势事件。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-349">It's possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="0b9ef-350">*GestureRecognizer* 将记得在上一帧实际发生的情况下，它是处于打开还是关闭状态，因此，根据此帧的注视目标启动和停止手势监视是可靠的。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-350">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it's reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="0b9ef-351">停止捕获手势</span><span class="sxs-lookup"><span data-stu-id="0b9ef-351">Stop capturing gestures</span></span>

<span data-ttu-id="0b9ef-352">停止手势识别：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-352">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="0b9ef-353">删除手势识别器</span><span class="sxs-lookup"><span data-stu-id="0b9ef-353">Removing a gesture recognizer</span></span>

<span data-ttu-id="0b9ef-354">请记住，在销毁 *GestureRecognizer* 对象之前，取消订阅已订阅的事件。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-354">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="0b9ef-355">在 Unity 中呈现运动控制器模型</span><span class="sxs-lookup"><span data-stu-id="0b9ef-355">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="0b9ef-356">![运动控制器模型和 teleportation](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="0b9ef-356">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="0b9ef-357">*运动控制器模型和 teleportation*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-357">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="0b9ef-358">若要在应用中渲染与用户所持有的物理控制器相匹配的运动控制器，并在按下各种按钮时进行解释，可以在 [混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity/)中使用 **MotionController prefab** 。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-358">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="0b9ef-359">此 prefab 从系统的已安装运动控制器驱动程序在运行时动态加载正确的 glTF 模型。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-359">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="0b9ef-360">必须动态加载这些模型，而不是在编辑器中手动导入它们，以便您的应用程序能够显示您的用户可能拥有的任何当前和未来控制器的物理上准确的3D 模型。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-360">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="0b9ef-361">按照 [入门](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) 说明下载混合现实工具包，并将其添加到 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-361">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="0b9ef-362">如果在入门步骤中将相机替换为 *MixedRealityCameraParent* prefab，则准备就绪！</span><span class="sxs-lookup"><span data-stu-id="0b9ef-362">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="0b9ef-363">该 prefab 包括运动控制器呈现。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-363">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="0b9ef-364">否则，请从 "项目" 窗格中将 *资产/HoloToolkit/Input/prototyping/MotionControllers* 添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-364">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="0b9ef-365">你需要将该 prefab 添加为你用来移动相机的任何父对象的子对象，以使该用户在场景中 teleports 时，使控制器与用户一起工作。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-365">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="0b9ef-366">如果应用不涉及 teleporting，只需在场景的根目录中添加 prefab。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-366">If your app doesn't involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="0b9ef-367">引发对象</span><span class="sxs-lookup"><span data-stu-id="0b9ef-367">Throwing objects</span></span>

<span data-ttu-id="0b9ef-368">在虚拟现实中引发对象比最初可能更难。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-368">Throwing objects in virtual reality is a harder problem than it may at first seem.</span></span> <span data-ttu-id="0b9ef-369">与大多数基于物理的交互一样，当游戏中的抛出意外时，它会立即出现，并打破浸入式。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-369">As with most physically based interactions, when throwing in game acts in an unexpected way, it's immediately obvious and breaks immersion.</span></span> <span data-ttu-id="0b9ef-370">我们花了一些时间来了解如何表示物理上正确的引发行为，并通过我们的平台的更新启用了一些准则，我们想要与你共享。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-370">We've spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="0b9ef-371">可在 [此处](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)找到如何实现引发的示例。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-371">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="0b9ef-372">此示例遵循以下四个准则：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-372">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="0b9ef-373">**使用控制器的 *速度* （而不是位置**）。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-373">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="0b9ef-374">在11月的 Windows 更新中，我们引入了 ["近似" 位置跟踪状态](../../design/motion-controllers.md#controller-tracking-state)下的行为更改。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-374">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="0b9ef-375">处于此状态时，将继续报告有关控制器的速率信息，前提是我们相信它的高准确性，这通常比位置长。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-375">When in this state, velocity information about the controller will continue to be reported for as long as we believe its high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="0b9ef-376">\*\*合并控制器的 \*角度速度\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-376">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="0b9ef-377">此逻辑全部包含在 `throwing.cs` 文件中的静态方法中，该文件位于 `GetThrownObjectVelAngVel` 以上链接的包中：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-377">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="0b9ef-378">在角度速度 conserved 时，引发的对象必须保持与抛出时相同的角度速度： `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="0b9ef-378">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="0b9ef-379">由于引发的对象很大范围可能不会成为手柄姿势的源，因此它的速度可能比用户引用框架中控制器的速度不同。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-379">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity than that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="0b9ef-380">以这种方式提供的对象速度的部分是围绕控制器原点的已抛出对象的质量的瞬间相切速度。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-380">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="0b9ef-381">此相切速度是控制器角度速度的叉积，向量表示控制器原点与所引发对象的质量中心之间的距离。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-381">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="0b9ef-382">引发的对象的总速度是控制器的速度与此相切速度的总和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="0b9ef-382">The total velocity of the thrown object is the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="0b9ef-383">密切 \*\*关注我们应用速度的 \*时间\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-383">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="0b9ef-384">按下按钮时，该事件最多可能需要 20 ms 才能通过蓝牙向上向上冒泡到操作系统。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-384">When a button is pressed, it can take up to 20 ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="0b9ef-385">这意味着，如果你将控制器状态更改从按下状态更改为未按下或其他方式，则控制器会提供你获取的信息。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-385">This means that if you poll for a controller state change from pressed to not pressed or the other way around, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="0b9ef-386">接下来，轮询 API 所提供的控制器可能是向前预测的，它会在帧显示时反映可能的情况，这可能会在未来超过 20 ms。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-386">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more than 20 ms in the future.</span></span> <span data-ttu-id="0b9ef-387">这适用于 *呈现* 已保存的对象，但会在计算用户释放引发的时间轨迹时，为 *目标* 对象提供时间问题。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-387">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released the throw.</span></span> <span data-ttu-id="0b9ef-388">幸运的是，在11月更新中，当发送 Unity 事件（如 *InteractionSourcePressed* 或 *InteractionSourceReleased* ）时，当按下或释放该按钮时，该状态包含来自后端的历史记录数据。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-388">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was pressed or released.</span></span>  <span data-ttu-id="0b9ef-389">若要在引发期间获得最准确的控制器呈现和控制器目标，则必须根据需要正确使用轮询和事件：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-389">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="0b9ef-390">对于每个帧的 **控制器呈现** ，你的应用程序应将控制器的 *GameObject* 放在前预测的控制器上，为当前帧的 photon 时间提供。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-390">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="0b9ef-391">可以从 XR 等 Unity 轮询 Api 获取此数据 *[。InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或 *[XR。WSA.InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-391">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="0b9ef-392">对于 **控制器** 针对按下或释放的目标，应用程序应基于该按下或释放事件的历史控制器提出的 raycast 和计算轨迹。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-392">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="0b9ef-393">可以从 Unity 事件 Api 获取此数据，如 *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-393">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="0b9ef-394">**使用手柄姿势**。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-394">**Use the grip pose**.</span></span> <span data-ttu-id="0b9ef-395">相对于手柄姿势报告角度速度和速度，而不是指针姿势。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-395">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="0b9ef-396">在将来的 Windows 更新中，引发将继续改进，你可以在此处找到详细信息。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-396">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a><span data-ttu-id="0b9ef-397">MRTK v2 中的手势和运动控制器</span><span class="sxs-lookup"><span data-stu-id="0b9ef-397">Gesture and Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="0b9ef-398">可以从输入管理器访问笔势和运动控制器。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-398">You can access gesture and motion controller from the input Manager.</span></span>
* [<span data-ttu-id="0b9ef-399">MRTK v2 中的手势</span><span class="sxs-lookup"><span data-stu-id="0b9ef-399">Gesture in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [<span data-ttu-id="0b9ef-400">MRTK v2 中的运动控制器</span><span class="sxs-lookup"><span data-stu-id="0b9ef-400">Motion Controller in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a><span data-ttu-id="0b9ef-401">按照教程进行操作</span><span class="sxs-lookup"><span data-stu-id="0b9ef-401">Follow along with tutorials</span></span>

<span data-ttu-id="0b9ef-402">混合现实学院中提供了更详细的自定义示例的分步教程：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-402">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="0b9ef-403">MR 输入 211：手势</span><span class="sxs-lookup"><span data-stu-id="0b9ef-403">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="0b9ef-404">MR 输入 213：运动控制器</span><span class="sxs-lookup"><span data-stu-id="0b9ef-404">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="0b9ef-405">[![MR 输入 213-运动控制器](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="0b9ef-405">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="0b9ef-406">*MR 输入 213-运动控制器*</span><span class="sxs-lookup"><span data-stu-id="0b9ef-406">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="0b9ef-407">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="0b9ef-407">Next Development Checkpoint</span></span>

<span data-ttu-id="0b9ef-408">如果遵循我们所说的 Unity 开发旅程，就是在浏览 MRTK 核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-408">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="0b9ef-409">从这里，你可以继续执行下一个构建基块：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-409">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0b9ef-410">手部和眼部跟踪</span><span class="sxs-lookup"><span data-stu-id="0b9ef-410">Hand and eye tracking</span></span>](hand-eye-in-unit.md)

<span data-ttu-id="0b9ef-411">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="0b9ef-411">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0b9ef-412">共享体验</span><span class="sxs-lookup"><span data-stu-id="0b9ef-412">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="0b9ef-413">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="0b9ef-413">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b9ef-414">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b9ef-414">See also</span></span>

* [<span data-ttu-id="0b9ef-415">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="0b9ef-415">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="0b9ef-416">运动控制器</span><span class="sxs-lookup"><span data-stu-id="0b9ef-416">Motion controllers</span></span>](../../design/motion-controllers.md)
