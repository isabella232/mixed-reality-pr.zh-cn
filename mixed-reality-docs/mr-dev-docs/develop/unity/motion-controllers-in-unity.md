---
title: Unity 中的运动控制器
description: 了解如何使用 XR 和通用按钮和轴 Api 在 Unity 中通过运动控制器输入采取措施。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 运动控制器，unity，输入，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，MRTK，混合现实工具包
ms.openlocfilehash: d8f9ce292c0ab1cfa89faf58f0e5b90322192b35
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394511"
---
# <a name="motion-controllers-in-unity"></a><span data-ttu-id="b0ff6-104">Unity 中的运动控制器</span><span class="sxs-lookup"><span data-stu-id="b0ff6-104">Motion controllers in Unity</span></span>

<span data-ttu-id="b0ff6-105">您可以通过两种主要方式在您的 [HMD 中进行](gaze-in-unity.md)操作，在 HoloLens 和沉浸式的中的 [手势](../../design/gaze-and-commit.md#composite-gestures) 和 [运动控制器](../../design/motion-controllers.md) 。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="b0ff6-106">可以通过 Unity 中的相同 Api 访问空间输入的两个源的数据。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="b0ff6-107">Unity 提供了两种主要方法来访问 Windows Mixed Reality 的空间输入数据。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="b0ff6-108">常见的 *GetButton/GetAxis* api 跨多个 Unity XR sdk 工作，而特定于 Windows Mixed Reality 的 *InteractionManager/GestureRecognizer* api 会公开一组完整的空间输入数据。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="b0ff6-109">Unity XR 输入 Api</span><span class="sxs-lookup"><span data-stu-id="b0ff6-109">Unity XR input APIs</span></span>

<span data-ttu-id="b0ff6-110">对于新项目，建议从头开始使用新的 XR 输入 Api。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-110">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="b0ff6-111">可在此处找到有关 [XR api](https://docs.unity3d.com/Manual/xr_input.html)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-111">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="b0ff6-112">Unity 按钮/轴映射表</span><span class="sxs-lookup"><span data-stu-id="b0ff6-112">Unity button/axis mapping table</span></span>

<span data-ttu-id="b0ff6-113">适用于 Windows Mixed Reality 运动控制器的 Unity 输入管理器支持通过 *GetButton/GetAxis* api 在下面列出的按钮和轴 id。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-113">Unity's Input Manager for Windows Mixed Reality motion controllers supports the button and axis IDs listed below through the *Input.GetButton/GetAxis* APIs.</span></span> <span data-ttu-id="b0ff6-114">"Windows MR 特定" 列是指 *InteractionSourceState* 类型可用的属性。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-114">The "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="b0ff6-115">以下各节将详细介绍其中的每个 Api。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-115">Each of these APIs is described in detail in the sections below.</span></span>

<span data-ttu-id="b0ff6-116">Windows Mixed Reality 的按钮/轴 ID 映射通常与 Oculus 按钮/轴 Id 匹配。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-116">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="b0ff6-117">Windows Mixed Reality 的按钮/轴 ID 映射在以下两个方面不同于 OpenVR 的映射：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-117">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="b0ff6-118">该映射使用不同于操纵杆的触摸板 Id，以支持同时具有 thumbsticks 和触摸板的控制器。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-118">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="b0ff6-119">映射避免了对菜单按钮的 A 和 X 按钮 Id 进行重载，以使它们可用于物理 ABXY 按钮。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-119">The mapping avoids overloading the A and X button IDs for the Menu buttons to leave them available for the physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="b0ff6-120">输入</span><span class="sxs-lookup"><span data-stu-id="b0ff6-120">Input</span></span> </th><th colspan="2"><span data-ttu-id="b0ff6-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">通用 Unity API</a></span><span class="sxs-lookup"><span data-stu-id="b0ff6-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="b0ff6-122"> (GetButton/GetAxis) </span><span class="sxs-lookup"><span data-stu-id="b0ff6-122">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="b0ff6-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR 专用输入 API</a></span><span class="sxs-lookup"><span data-stu-id="b0ff6-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="b0ff6-124"> (XR。WSA.输入) </span><span class="sxs-lookup"><span data-stu-id="b0ff6-124">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="b0ff6-125">左手</span><span class="sxs-lookup"><span data-stu-id="b0ff6-125">Left hand</span></span> </th><th> <span data-ttu-id="b0ff6-126">右手</span><span class="sxs-lookup"><span data-stu-id="b0ff6-126">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="b0ff6-127">选择触发按下</span><span class="sxs-lookup"><span data-stu-id="b0ff6-127">Select trigger pressed</span></span> </td><td> <span data-ttu-id="b0ff6-128">轴 9 = 1。0</span><span class="sxs-lookup"><span data-stu-id="b0ff6-128">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="b0ff6-129">轴 10 = 1。0</span><span class="sxs-lookup"><span data-stu-id="b0ff6-129">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="b0ff6-130">selectPressed</span><span class="sxs-lookup"><span data-stu-id="b0ff6-130">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-131">选择触发器模拟值</span><span class="sxs-lookup"><span data-stu-id="b0ff6-131">Select trigger analog value</span></span> </td><td> <span data-ttu-id="b0ff6-132">轴9</span><span class="sxs-lookup"><span data-stu-id="b0ff6-132">Axis 9</span></span> </td><td> <span data-ttu-id="b0ff6-133">轴10</span><span class="sxs-lookup"><span data-stu-id="b0ff6-133">Axis 10</span></span> </td><td> <span data-ttu-id="b0ff6-134">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="b0ff6-134">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-135">选择触发器部分按下</span><span class="sxs-lookup"><span data-stu-id="b0ff6-135">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="b0ff6-136">按钮 14 <i> (游戏板兼容) </i> </span><span class="sxs-lookup"><span data-stu-id="b0ff6-136">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="b0ff6-137">按钮 15 <i> (游戏板兼容) </i> </span><span class="sxs-lookup"><span data-stu-id="b0ff6-137">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="b0ff6-138">selectPressedAmount &gt; 0。0</span><span class="sxs-lookup"><span data-stu-id="b0ff6-138">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-139">按下菜单按钮</span><span class="sxs-lookup"><span data-stu-id="b0ff6-139">Menu button pressed</span></span> </td><td> <span data-ttu-id="b0ff6-140">按钮 6 \*</span><span class="sxs-lookup"><span data-stu-id="b0ff6-140">Button 6\*</span></span> </td><td> <span data-ttu-id="b0ff6-141">按钮 7 \*</span><span class="sxs-lookup"><span data-stu-id="b0ff6-141">Button 7\*</span></span> </td><td> <span data-ttu-id="b0ff6-142">menuPressed</span><span class="sxs-lookup"><span data-stu-id="b0ff6-142">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-143">按下手柄按钮</span><span class="sxs-lookup"><span data-stu-id="b0ff6-143">Grip button pressed</span></span> </td><td> <span data-ttu-id="b0ff6-144">Axis 11 = 1.0 (没有模拟值) </span><span class="sxs-lookup"><span data-stu-id="b0ff6-144">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="b0ff6-145">按钮 4 <i> (游戏板兼容) </i> </span><span class="sxs-lookup"><span data-stu-id="b0ff6-145">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="b0ff6-146">轴 12 = 1.0 (没有模拟值) </span><span class="sxs-lookup"><span data-stu-id="b0ff6-146">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="b0ff6-147">按钮 5 <i> (游戏板兼容) </i> </span><span class="sxs-lookup"><span data-stu-id="b0ff6-147">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="b0ff6-148">grasped</span><span class="sxs-lookup"><span data-stu-id="b0ff6-148">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-149">操纵杆 X <i> (左：-1.0，right： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="b0ff6-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="b0ff6-150">轴1</span><span class="sxs-lookup"><span data-stu-id="b0ff6-150">Axis 1</span></span> </td><td> <span data-ttu-id="b0ff6-151">轴4</span><span class="sxs-lookup"><span data-stu-id="b0ff6-151">Axis 4</span></span> </td><td> <span data-ttu-id="b0ff6-152">thumbstickPosition</span><span class="sxs-lookup"><span data-stu-id="b0ff6-152">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-153">操纵杆 Y <i> (顶部：-1.0、底部： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="b0ff6-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="b0ff6-154">轴2</span><span class="sxs-lookup"><span data-stu-id="b0ff6-154">Axis 2</span></span> </td><td> <span data-ttu-id="b0ff6-155">轴5</span><span class="sxs-lookup"><span data-stu-id="b0ff6-155">Axis 5</span></span> </td><td> <span data-ttu-id="b0ff6-156">thumbstickPosition</span><span class="sxs-lookup"><span data-stu-id="b0ff6-156">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-157">已按下操纵杆</span><span class="sxs-lookup"><span data-stu-id="b0ff6-157">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="b0ff6-158">按钮8</span><span class="sxs-lookup"><span data-stu-id="b0ff6-158">Button 8</span></span> </td><td> <span data-ttu-id="b0ff6-159">按钮9</span><span class="sxs-lookup"><span data-stu-id="b0ff6-159">Button 9</span></span> </td><td> <span data-ttu-id="b0ff6-160">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="b0ff6-160">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-161">触摸板 X <i> (左：-1.0，右： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="b0ff6-161">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="b0ff6-162">轴 17 \*</span><span class="sxs-lookup"><span data-stu-id="b0ff6-162">Axis 17\*</span></span> </td><td> <span data-ttu-id="b0ff6-163">轴 19 \*</span><span class="sxs-lookup"><span data-stu-id="b0ff6-163">Axis 19\*</span></span> </td><td> <span data-ttu-id="b0ff6-164">touchpadPosition</span><span class="sxs-lookup"><span data-stu-id="b0ff6-164">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-165">触摸板 Y <i> (顶部：-1.0、底部： 1.0) </i> </span><span class="sxs-lookup"><span data-stu-id="b0ff6-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="b0ff6-166">Axis 18 \*</span><span class="sxs-lookup"><span data-stu-id="b0ff6-166">Axis 18\*</span></span> </td><td> <span data-ttu-id="b0ff6-167">轴 20 \*</span><span class="sxs-lookup"><span data-stu-id="b0ff6-167">Axis 20\*</span></span> </td><td> <span data-ttu-id="b0ff6-168">touchpadPosition</span><span class="sxs-lookup"><span data-stu-id="b0ff6-168">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-169">接触触摸板</span><span class="sxs-lookup"><span data-stu-id="b0ff6-169">Touchpad touched</span></span> </td><td> <span data-ttu-id="b0ff6-170">按钮 18 \*</span><span class="sxs-lookup"><span data-stu-id="b0ff6-170">Button 18\*</span></span> </td><td> <span data-ttu-id="b0ff6-171">按钮 19 \*</span><span class="sxs-lookup"><span data-stu-id="b0ff6-171">Button 19\*</span></span> </td><td> <span data-ttu-id="b0ff6-172">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="b0ff6-172">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-173">已按触摸板</span><span class="sxs-lookup"><span data-stu-id="b0ff6-173">Touchpad pressed</span></span> </td><td> <span data-ttu-id="b0ff6-174">按钮 16 \*</span><span class="sxs-lookup"><span data-stu-id="b0ff6-174">Button 16\*</span></span> </td><td> <span data-ttu-id="b0ff6-175">按钮 17 \*</span><span class="sxs-lookup"><span data-stu-id="b0ff6-175">Button 17\*</span></span> </td><td> <span data-ttu-id="b0ff6-176">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="b0ff6-176">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-177">6DoF 手柄姿势或指针姿势</span><span class="sxs-lookup"><span data-stu-id="b0ff6-177">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="b0ff6-178">仅限<i>抓握</i>： <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR。InputTracking. GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="b0ff6-178"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="b0ff6-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="b0ff6-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="b0ff6-180">Pass <i>手柄</i> 或 <i>指针</i> 作为参数： SourceState. sourcePose. TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="b0ff6-180">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="b0ff6-181">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="b0ff6-181">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-182">跟踪状态</span><span class="sxs-lookup"><span data-stu-id="b0ff6-182">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="b0ff6-183"><i>位置准确性和源丢失风险仅通过 MR 专用 API 提供</i> </span><span class="sxs-lookup"><span data-stu-id="b0ff6-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="b0ff6-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="b0ff6-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="b0ff6-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="b0ff6-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="b0ff6-186">这些按钮/轴 Id 不同于 Unity 用于 OpenVR 的 Id，因为 gamepads、Oculus 触控和 OpenVR 所使用的映射中出现冲突。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-186">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

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

### <a name="openxr"></a><span data-ttu-id="b0ff6-187">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b0ff6-187">OpenXR</span></span>

<span data-ttu-id="b0ff6-188">若要了解有关 Unity 中混合现实交互的基础知识，请访问 unity [手动 For UNITY XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-188">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="b0ff6-189">此 Unity 文档介绍了从特定于控制器的输入到更可归纳的 **InputFeatureUsage** 的映射，如何识别和分类可用的 XR 输入，如何从这些输入中读取数据等。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-189">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="b0ff6-190">Mixed Reality OpenXR 插件提供附加的输入交互配置文件，这些配置文件映射到标准 **InputFeatureUsage**，如下所述：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-190">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="b0ff6-191">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="b0ff6-191">InputFeatureUsage</span></span> | <span data-ttu-id="b0ff6-192">HP 回音 G2 控制器 (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="b0ff6-192">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="b0ff6-193">HoloLens 手型 (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="b0ff6-193">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="b0ff6-194">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="b0ff6-194">primary2DAxis</span></span> | <span data-ttu-id="b0ff6-195">操纵杆</span><span class="sxs-lookup"><span data-stu-id="b0ff6-195">Joystick</span></span> | |
| <span data-ttu-id="b0ff6-196">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="b0ff6-196">primary2DAxisClick</span></span> | <span data-ttu-id="b0ff6-197">游戏杆-单击</span><span class="sxs-lookup"><span data-stu-id="b0ff6-197">Joystick - Click</span></span> | |
| <span data-ttu-id="b0ff6-198">触发器</span><span class="sxs-lookup"><span data-stu-id="b0ff6-198">trigger</span></span> | <span data-ttu-id="b0ff6-199">触发器</span><span class="sxs-lookup"><span data-stu-id="b0ff6-199">Trigger</span></span>  | |
| <span data-ttu-id="b0ff6-200">调整</span><span class="sxs-lookup"><span data-stu-id="b0ff6-200">grip</span></span> | <span data-ttu-id="b0ff6-201">握</span><span class="sxs-lookup"><span data-stu-id="b0ff6-201">Grip</span></span> | <span data-ttu-id="b0ff6-202">敲击或敲击</span><span class="sxs-lookup"><span data-stu-id="b0ff6-202">Air tap or squeeze</span></span> |
| <span data-ttu-id="b0ff6-203">primaryButton</span><span class="sxs-lookup"><span data-stu-id="b0ff6-203">primaryButton</span></span> | <span data-ttu-id="b0ff6-204">[X/A] - 按</span><span class="sxs-lookup"><span data-stu-id="b0ff6-204">[X/A] - Press</span></span> | <span data-ttu-id="b0ff6-205">隔空敲击</span><span class="sxs-lookup"><span data-stu-id="b0ff6-205">Air tap</span></span> |
| <span data-ttu-id="b0ff6-206">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="b0ff6-206">secondaryButton</span></span> | <span data-ttu-id="b0ff6-207">[Y/B] - 按</span><span class="sxs-lookup"><span data-stu-id="b0ff6-207">[Y/B] - Press</span></span> | |
| <span data-ttu-id="b0ff6-208">gripButton</span><span class="sxs-lookup"><span data-stu-id="b0ff6-208">gripButton</span></span> | <span data-ttu-id="b0ff6-209">手柄 - 按</span><span class="sxs-lookup"><span data-stu-id="b0ff6-209">Grip - Press</span></span> | |
| <span data-ttu-id="b0ff6-210">triggerButton</span><span class="sxs-lookup"><span data-stu-id="b0ff6-210">triggerButton</span></span> | <span data-ttu-id="b0ff6-211">触发器 - 按</span><span class="sxs-lookup"><span data-stu-id="b0ff6-211">Trigger - Press</span></span> | |
| <span data-ttu-id="b0ff6-212">menuButton</span><span class="sxs-lookup"><span data-stu-id="b0ff6-212">menuButton</span></span> | <span data-ttu-id="b0ff6-213">菜单</span><span class="sxs-lookup"><span data-stu-id="b0ff6-213">Menu</span></span> | |

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="b0ff6-214">手柄姿势与指向姿势</span><span class="sxs-lookup"><span data-stu-id="b0ff6-214">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="b0ff6-215">Windows Mixed Reality支持各种外形因素中的运动控制器。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-215">Windows Mixed Reality supports motion controllers in a variety of form factors.</span></span> <span data-ttu-id="b0ff6-216">每个控制器的设计在用户手部位置与应用在呈现控制器时应该用于指向的自然"向前"方向之间的关系有所不同。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-216">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="b0ff6-217">为了更好地表示这些控制器，可以针对每个交互源调查两种类型的姿势：手柄 **姿势** 和 **指针姿势**。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-217">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="b0ff6-218">手柄姿势和指针姿势坐标都由全局 Unity 世界坐标的所有 Unity API 表示。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-218">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="b0ff6-219">手柄姿势</span><span class="sxs-lookup"><span data-stu-id="b0ff6-219">Grip pose</span></span>

<span data-ttu-id="b0ff6-220">手柄 **姿势** 表示用户手部的位置，由 HoloLens 检测或持有运动控制器。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-220">The **grip pose** represents the location of the users palm, either detected by a HoloLens or holding a motion controller.</span></span>

<span data-ttu-id="b0ff6-221">在沉浸式头戴显示设备中，手柄姿势最适合用于呈现用户手部或用户手 **部中持有的对象**。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-221">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**.</span></span> <span data-ttu-id="b0ff6-222">在可视化运动控制器时，也使用手柄姿势。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-222">The grip pose is also used when visualizing a motion controller.</span></span> <span data-ttu-id="b0ff6-223">Windows **为运动控制器** 提供的可呈现模型使用手柄姿势作为旋转的原点和中心。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-223">The **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="b0ff6-224">手柄姿势的定义具体如下：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-224">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="b0ff6-225">手柄 **位置**：自然按住控制器时，通过向左或向右调整以将手柄中的位置居中时，手心中心。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-225">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="b0ff6-226">在Windows Mixed Reality控制器上，此位置通常与"抓取"按钮对齐。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-226">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="b0ff6-227">手柄 **方向的** 右轴：完全打开手形成平面 5 指姿势时，与手部正常的射线从左 (向前，从右手心向后) </span><span class="sxs-lookup"><span data-stu-id="b0ff6-227">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="b0ff6-228">手柄方向 **的** 向前轴：当你部分关闭手部 (就像按住控制器) 一样，指向"向前"的射线通过由非滚动手指组成的管道。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-228">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="b0ff6-229">手柄 **方向的上轴**：右侧和向前定义隐含的向上轴。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-229">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="b0ff6-230">可以通过 Unity 的跨供应商输入 API 或 XR 访问手柄 (*[姿势。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation*) 或 Windows MR 特定的 API (*sourceState.sourcePose.TryGetPosition/Rotation，* 请求手柄节点节点的姿势) 。 </span><span class="sxs-lookup"><span data-stu-id="b0ff6-230">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="b0ff6-231">指针姿势</span><span class="sxs-lookup"><span data-stu-id="b0ff6-231">Pointer pose</span></span>

<span data-ttu-id="b0ff6-232">指针 **姿势** 表示指向向前的控制器的提示。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-232">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="b0ff6-233">在呈现控制器模型本身时，系统提供的指针姿势最适合用于 **光线广播**。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-233">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="b0ff6-234">如果要呈现一些其他虚拟对象（例如虚拟照片）来更换控制器，则应该指向该虚拟对象最自然的射线，例如沿应用定义的"手形"模型群移动的射线。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-234">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that's most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="b0ff6-235">由于用户可以看到虚拟对象，而不是物理控制器，因此使用应用的用户可能更自然地指向虚拟对象。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-235">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="b0ff6-236">目前，指针姿势仅在 Unity 中通过特定于 Windows MR 的 API *sourceState.sourcePose.TryGetPosition/Rotation* 提供，并作为参数传递 *InteractionSourceNode.Pointer。*</span><span class="sxs-lookup"><span data-stu-id="b0ff6-236">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

### <a name="openxr"></a><span data-ttu-id="b0ff6-237">OpenXR</span><span class="sxs-lookup"><span data-stu-id="b0ff6-237">OpenXR</span></span> 

<span data-ttu-id="b0ff6-238">可以通过 OpenXR 输入交互访问两组姿势：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-238">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="b0ff6-239">手柄为在手中呈现对象而造成</span><span class="sxs-lookup"><span data-stu-id="b0ff6-239">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="b0ff6-240">目的是指向世界。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-240">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="b0ff6-241">有关此设计以及两种姿势之间的差异，请参阅 [OpenXR 规范 - 输入子路径](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-241">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="b0ff6-242">InputFeatureUsages  DevicePosition、DeviceRotation、DeviceVelocity和 **DeviceAngularVelocity** 提供的姿势均表示 OpenXR 手柄姿势。  </span><span class="sxs-lookup"><span data-stu-id="b0ff6-242">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="b0ff6-243">与手柄姿势相关的 InputFeatureUsages 在 Unity [的 CommonUsages 中定义](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-243">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="b0ff6-244">InputFeatureUsages  PointerPosition、PointerRotation、PointerVelocity和 **PointerAngularVelocity** 提供的姿势均表示 OpenXR 目标姿势。  </span><span class="sxs-lookup"><span data-stu-id="b0ff6-244">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="b0ff6-245">这些 InputFeatureUsages 未在任何包含的 C# 文件中定义，因此需要定义自己的 InputFeatureUsages，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-245">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

## <a name="haptics"></a><span data-ttu-id="b0ff6-246">Haptics</span><span class="sxs-lookup"><span data-stu-id="b0ff6-246">Haptics</span></span>

<span data-ttu-id="b0ff6-247">有关在 Unity 的 XR 输入系统中使用 haptics 的信息，请参阅 Unity Manual [for Unity XR Input - Haptics （Unity XR 输入 - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)的 Unity 手册）。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-247">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="b0ff6-248">控制器跟踪状态</span><span class="sxs-lookup"><span data-stu-id="b0ff6-248">Controller tracking state</span></span>

<span data-ttu-id="b0ff6-249">与头戴显示设备一样，Windows Mixed Reality控制器不需要设置外部跟踪传感器。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-249">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="b0ff6-250">相反，控制器由头戴显示设备本身的传感器进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-250">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="b0ff6-251">如果用户将控制器从头戴显示设备视场中移开，则在大多数情况下，Windows 将继续推断控制器位置。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-251">If the user moves the controllers out of the headset's field of view, Windows continues to infer controller positions in most cases.</span></span> <span data-ttu-id="b0ff6-252">当控制器丢失视觉跟踪的时间足够长时，控制器的位置将下降至近似准确性位置。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-252">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="b0ff6-253">此时，系统会将控制器进行正文锁定，跟踪用户移动时的位置，同时仍使用其内部方向传感器公开控制器的真实方向。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-253">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="b0ff6-254">许多使用控制器指向和激活 UI 元素的应用都可以正常运行，同时大致准确无误，而无需用户通知。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-254">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<!-- The best way to get a feel for this is to try it yourself. Check out this video with examples of immersive content that works with motion controllers across various tracking states:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g] -->

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="b0ff6-255">有关显式跟踪状态的原因</span><span class="sxs-lookup"><span data-stu-id="b0ff6-255">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="b0ff6-256">希望根据跟踪状态以不同方式处理位置的应用可能会进一步检查控制器状态的属性，例如 *SourceLossRisk* 和 *PositionAccuracy*：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-256">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="b0ff6-257">跟踪状态</span><span class="sxs-lookup"><span data-stu-id="b0ff6-257">Tracking state</span></span> </th><th> <span data-ttu-id="b0ff6-258">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="b0ff6-258">SourceLossRisk</span></span> </th><th> <span data-ttu-id="b0ff6-259">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="b0ff6-259">PositionAccuracy</span></span> </th><th> <span data-ttu-id="b0ff6-260">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="b0ff6-260">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="b0ff6-261"><b>准确度高</b> </span><span class="sxs-lookup"><span data-stu-id="b0ff6-261"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="b0ff6-262">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="b0ff6-262">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="b0ff6-263">高</span><span class="sxs-lookup"><span data-stu-id="b0ff6-263">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="b0ff6-264">true</span><span class="sxs-lookup"><span data-stu-id="b0ff6-264">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-265"><b>高准确度 (有丢失数据) </b> </span><span class="sxs-lookup"><span data-stu-id="b0ff6-265"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="b0ff6-266">== 1.0</span><span class="sxs-lookup"><span data-stu-id="b0ff6-266">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="b0ff6-267">高</span><span class="sxs-lookup"><span data-stu-id="b0ff6-267">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="b0ff6-268">true</span><span class="sxs-lookup"><span data-stu-id="b0ff6-268">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-269"><b>近似准确度</b> </span><span class="sxs-lookup"><span data-stu-id="b0ff6-269"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="b0ff6-270">== 1.0</span><span class="sxs-lookup"><span data-stu-id="b0ff6-270">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="b0ff6-271">近似</span><span class="sxs-lookup"><span data-stu-id="b0ff6-271">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="b0ff6-272">true</span><span class="sxs-lookup"><span data-stu-id="b0ff6-272">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b0ff6-273"><b>无位置</b> </span><span class="sxs-lookup"><span data-stu-id="b0ff6-273"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="b0ff6-274">== 1.0</span><span class="sxs-lookup"><span data-stu-id="b0ff6-274">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="b0ff6-275">近似</span><span class="sxs-lookup"><span data-stu-id="b0ff6-275">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="b0ff6-276">false</span><span class="sxs-lookup"><span data-stu-id="b0ff6-276">false</span></span></td>
</tr>
</table>

<span data-ttu-id="b0ff6-277">这些运动控制器跟踪状态的定义如下：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-277">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="b0ff6-278">**高精度：** 虽然运动控制器位于头戴显示设备视场内，但它通常基于视觉跟踪提供高精度位置。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-278">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="b0ff6-279">暂时离开视场或被头戴显示设备传感器短暂遮盖（例如，被用户另一手遮挡）的移动控制器) 将基于控制器本身的惯性跟踪，在短时间内继续返回高精度姿势。 (</span><span class="sxs-lookup"><span data-stu-id="b0ff6-279">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="b0ff6-280">**高准确度 (有丢失数据) ：** 当用户将运动控制器移到头戴显示设备视场的边缘之后，头戴显示设备很快就会无法直观地跟踪控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-280">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="b0ff6-281">应用通过看到 **SourceLossRisk** 达到 1.0，知道控制器何时到达此 FOV 边界。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-281">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="b0ff6-282">此时，应用可以选择暂停需要稳定高质量手势流的控制器手势。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-282">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="b0ff6-283">**近似准确度：** 当控制器丢失视觉跟踪的时间足够长时，控制器的位置将下降至近似准确性位置。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-283">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="b0ff6-284">此时，系统会将控制器进行正文锁定，跟踪用户移动时的位置，同时仍使用其内部方向传感器公开控制器的真实方向。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-284">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="b0ff6-285">许多使用控制器指向和激活 UI 元素的应用可以正常运行，同时大致准确，无需用户通知。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-285">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="b0ff6-286">具有较重输入要求的应用可以选择通过检查 **PositionAccuracy** 属性来检测从"高准确度"到"近似准确度"的下降，例如，在此期间，在屏幕外目标上为用户提供更丰富的命中框。  </span><span class="sxs-lookup"><span data-stu-id="b0ff6-286">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="b0ff6-287">**无位置：** 虽然控制器可以长时间以近似精度运行，但有时系统知道，即使是人体锁定的位置目前也无意义。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-287">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="b0ff6-288">例如，打开的控制器可能从未在视觉上观察到，或者用户可能会关闭随后由其他人选取的控制器。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-288">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="b0ff6-289">此时，系统不会向应用提供任何位置 *，TryGetPosition* 将返回 false。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-289">At those times, the system won't provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="b0ff6-290">Input.GetButton/GetAxis (的常见 Unity API) </span><span class="sxs-lookup"><span data-stu-id="b0ff6-290">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="b0ff6-291">\**命名空间\*\*\*：UnityEngine、UnityEngine.XR* </span><span class="sxs-lookup"><span data-stu-id="b0ff6-291">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="b0ff6-292">**类型**： *输入* *、XR。InputTracking*</span><span class="sxs-lookup"><span data-stu-id="b0ff6-292">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="b0ff6-293">Unity 当前使用常规 *Input.GetButton/Input.GetAxis* API 公开 [Oculus](https://docs.unity3d.com/Manual/OculusControllers.html)SDK、OpenVR [SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) 和 Windows Mixed Reality 的输入，包括手部和运动控制器。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-293">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="b0ff6-294">如果应用使用这些 API 进行输入，则可以轻松地支持跨多个 XR SDK（包括 Windows Mixed Reality）。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-294">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="b0ff6-295">获取逻辑按钮的按下状态</span><span class="sxs-lookup"><span data-stu-id="b0ff6-295">Getting a logical button's pressed state</span></span>

<span data-ttu-id="b0ff6-296">若要使用常规 Unity 输入 API，通常首先将按钮和轴与 [Unity 输入](https://docs.unity3d.com/Manual/ConventionalGameInput.html)管理器中的逻辑名称连接，将按钮或轴 ID 绑定到每个名称。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-296">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="b0ff6-297">然后，可以编写引用该逻辑按钮/轴名称的代码。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-297">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="b0ff6-298">例如，若要将左侧运动控制器的触发器按钮映射到"提交"操作，请转到"编辑 **> 项目设置">** Unity 中的"输入"，然后展开"轴"下的"提交"部分的属性。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-298">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="b0ff6-299">更改" **正按钮"** 或 **"Alt 正按钮** "属性以读取 **按钮 14，** 如下所示：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-299">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="b0ff6-300">![Unity 的 InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="b0ff6-300">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="b0ff6-301&quot;>*Unity InputManager*</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;b0ff6-301&quot;>*Unity InputManager*</span></span>

<span data-ttu-id=&quot;b0ff6-302&quot;>然后，脚本可以使用 *Input.GetButton 检查&quot;提交&quot;操作*：</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;b0ff6-302&quot;>Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton(&quot;Submit"))
{
  // ...
}
```
<span data-ttu-id="b0ff6-303">可以通过更改"轴"下的 **"大小"属性来\*\*\*\*添加更多逻辑按钮**。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-303">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="b0ff6-304">直接获取物理按钮的按下状态</span><span class="sxs-lookup"><span data-stu-id="b0ff6-304">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="b0ff6-305">还可使用 *Input.GetKey* 按其完全限定名称手动访问按钮：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-305">You can also access buttons manually by their fully qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="b0ff6-306">获取手部或运动控制器的姿势</span><span class="sxs-lookup"><span data-stu-id="b0ff6-306">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="b0ff6-307">可以使用 XR 访问控制器的位置和 *旋转。InputTracking*：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-307">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> <span data-ttu-id="b0ff6-308">上面的代码表示控制器的手柄姿势 (其中用户持有控制器) ，这可用于在用户手部或控制器本身的模型中呈现一个手部或手部。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-308">The above code represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>
> 
> <span data-ttu-id="b0ff6-309">此手柄姿势与指针姿势之间的关系 (控制器的指针指向的位置) 控制器之间可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-309">The relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="b0ff6-310">目前，只有通过特定于 MR 的输入 API 才能访问控制器的指针姿势，如以下各节所述。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-310">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="b0ff6-311">XR 中特定于 Windows (API。Wsa。输入) </span><span class="sxs-lookup"><span data-stu-id="b0ff6-311">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="b0ff6-312">如果项目正在使用任何 XR。WSA API 正在逐步淘汰，以在将来的 Unity 版本中支持 XR SDK。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-312">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="b0ff6-313">对于新项目，我们建议从头开始使用 XR SDK。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-313">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="b0ff6-314">可在此处找到有关 [XR 输入系统和 API 详细信息](https://docs.unity3d.com/Manual/xr_input.html)。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-314">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="b0ff6-315">\**命名空间\*\*\*：UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="b0ff6-315">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="b0ff6-316">**类型**：InteractionManager、InteractionSourceState、InteractionSource、InteractionSourceProperties、InteractionSourceKind、InteractionSourceLocation      </span><span class="sxs-lookup"><span data-stu-id="b0ff6-316">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="b0ff6-317">若要获取有关适用于 HoloLens) 和运动控制器的 Windows Mixed Reality 手动输入 (的更多详细信息，可以选择在 *UnityEngine.XR.WSA.Input* 命名空间下使用特定于 Windows 的空间输入 API。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-317">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="b0ff6-318">这使你可以访问其他信息，例如位置准确性或源类型，使你能够将手和控制器分开。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-318">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="b0ff6-319">轮询手部和运动控制器的状态</span><span class="sxs-lookup"><span data-stu-id="b0ff6-319">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="b0ff6-320">可以使用 (*GetCurrentReading* 方法轮询手部或运动控制器) 每个交互源的状态。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-320">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="b0ff6-321">返回 *的每个 InteractionSourceState* 表示当前时刻的交互源。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-321">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="b0ff6-322">*InteractionSourceState* 公开如下信息：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-322">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="b0ff6-323">选择 [/菜单](../../design/motion-controllers.md) / (/触摸板/Thumbstick) </span><span class="sxs-lookup"><span data-stu-id="b0ff6-323">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="b0ff6-324">特定于运动控制器的其他数据，例如触摸板和/或 thumbstick 的 XY 坐标和触摸状态</span><span class="sxs-lookup"><span data-stu-id="b0ff6-324">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="b0ff6-325">InteractionSourceKind，用于了解源是手还是运动控制器</span><span class="sxs-lookup"><span data-stu-id="b0ff6-325">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="b0ff6-326">轮询向前预测的呈现姿势</span><span class="sxs-lookup"><span data-stu-id="b0ff6-326">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="b0ff6-327">轮询来自手和控制器的交互源数据时，你获取的姿势是向前预测的，此时此帧的光子将到达用户眼睛。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-327">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="b0ff6-328">向前预测的姿势最适合用于 **呈现每个** 帧的控制器或持有的对象。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-328">Forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="b0ff6-329">如果以控制器的给定按下或发布为目标，如果使用下面所述的历史事件 API，则最准确。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-329">If you're targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="b0ff6-330">还可以获取此当前帧的向前预测头部姿势。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-330">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="b0ff6-331">与源姿势一样，这可用于呈现光标，不过，如果使用下面所述的历史事件 API，面向给定的按下或发布将最准确。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-331">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="b0ff6-332">处理交互源事件</span><span class="sxs-lookup"><span data-stu-id="b0ff6-332">Handling interaction source events</span></span>

<span data-ttu-id="b0ff6-333">若要处理输入事件及其准确的历史姿势数据，可以处理交互源事件，而不是轮询。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-333">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="b0ff6-334">处理交互源事件：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-334">To handle interaction source events:</span></span>
* <span data-ttu-id="b0ff6-335">注册 *InteractionManager* 输入事件。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-335">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="b0ff6-336">对于你感兴趣的每种类型的交互事件，需要订阅它。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-336">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="b0ff6-337">处理 事件。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-337">Handle the event.</span></span> <span data-ttu-id="b0ff6-338">订阅交互事件后，将在适当时获取回调。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-338">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="b0ff6-339">在 *SourcePressed* 示例中，这将在检测到源之后以及释放或丢失源之前发生。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-339">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="b0ff6-340">如何停止处理事件</span><span class="sxs-lookup"><span data-stu-id="b0ff6-340">How to stop handling an event</span></span>

<span data-ttu-id="b0ff6-341">如果不再对事件感兴趣，或者要销毁已订阅该事件的对象，则需要停止处理事件。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-341">You need to stop handling an event when you're no longer interested in the event or you're destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="b0ff6-342">若要停止处理事件，请取消订阅该事件。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-342">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="b0ff6-343">交互源事件列表</span><span class="sxs-lookup"><span data-stu-id="b0ff6-343">List of interaction source events</span></span>

<span data-ttu-id="b0ff6-344">可用的交互源事件包括：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-344">The available interaction source events are:</span></span>
* <span data-ttu-id="b0ff6-345">*InteractionSourceDetected (* 源变为活动) </span><span class="sxs-lookup"><span data-stu-id="b0ff6-345">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="b0ff6-346">*InteractionSourceLost (* 变为非活动) </span><span class="sxs-lookup"><span data-stu-id="b0ff6-346">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="b0ff6-347">*InteractionSourcePressed* (点击、按下按钮或"选择") </span><span class="sxs-lookup"><span data-stu-id="b0ff6-347">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="b0ff6-348">*InteractionSourceReleased* (点击结束、按钮释放或"选择"话语结束) </span><span class="sxs-lookup"><span data-stu-id="b0ff6-348">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="b0ff6-349">*InteractionSourceUpdated (* 移动或以其他方式更改某些状态) </span><span class="sxs-lookup"><span data-stu-id="b0ff6-349">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="b0ff6-350">历史目标事件造成与按下或发布最准确的匹配</span><span class="sxs-lookup"><span data-stu-id="b0ff6-350">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="b0ff6-351">前面所述的轮询 API 为应用提供前向预测的姿势。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-351">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="b0ff6-352">虽然这些预测的姿势最适合呈现控制器或虚拟桌面对象，但未来姿势并不是目标的最佳，有两个关键原因：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-352">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses aren't optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="b0ff6-353">当用户按下控制器上的按钮时，系统接收按下前，蓝牙上的无线延迟可能约 20 毫秒。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-353">When the user presses a button on a controller, there can be about 20 ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="b0ff6-354">然后，如果使用的是前向预测姿势，则还有 10-20 毫秒的向前预测应用于当前帧的光子到达用户眼睛的时间。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-354">Then, if you're using a forward-predicted pose, there would be another 10-20 ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="b0ff6-355">这意味着轮询会提供源姿势或头部姿势，向前 30-40 毫秒，从用户头部和手在按下或松开时实际返回的 30-40 毫秒。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-355">This means that polling gives you a source pose or head pose that is 30-40 ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="b0ff6-356">对于 HoloLens 手动输入，虽然没有无线传输延迟，但存在类似的处理延迟来检测按下。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-356">For HoloLens hand input, while there's no wireless transmission delay, there's a similar processing delay to detect the press.</span></span>

<span data-ttu-id="b0ff6-357">若要根据用户对手或控制器按下的原始意图准确定位，应使用该 *InteractionSourcePressed* 或 *InteractionSourceReleased* 输入事件的历史源姿势或头部姿势。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-357">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="b0ff6-358">可以使用来自用户头部或控制器的历史姿势数据的按下或释放目标：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-358">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="b0ff6-359">发生手势或控制器按下时头部姿势，可用于确定用户正在[的目标位置：](../../design/gaze-and-commit.md) </span><span class="sxs-lookup"><span data-stu-id="b0ff6-359">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

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

* <span data-ttu-id="b0ff6-360">源在运动控制器按下发生时的姿势，可用于确定用户指向控制器的位置。 </span><span class="sxs-lookup"><span data-stu-id="b0ff6-360">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="b0ff6-361">这将是遇到按下的控制器的状态。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-361">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="b0ff6-362">如果要呈现控制器本身，可以请求指针姿势而不是手柄姿势，以从用户将考虑的呈现控制器的自然提示中发射目标射线：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-362">If you're rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="b0ff6-363">事件处理程序示例</span><span class="sxs-lookup"><span data-stu-id="b0ff6-363">Event handlers example</span></span>

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

## <a name="motion-controllers-in-mrtk"></a><span data-ttu-id="b0ff6-364">MRTK 中的运动控制器</span><span class="sxs-lookup"><span data-stu-id="b0ff6-364">Motion Controllers in MRTK</span></span>

<span data-ttu-id="b0ff6-365">可以从输入 [管理器访问手势](/windows/mixed-reality/mrtk-unity/features/input/controllers) 和运动控制器。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-365">You can access [gesture and motion controller](/windows/mixed-reality/mrtk-unity/features/input/controllers) from the input Manager.</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="b0ff6-366">按照教程进行操作</span><span class="sxs-lookup"><span data-stu-id="b0ff6-366">Follow along with tutorials</span></span>

<span data-ttu-id="b0ff6-367">混合现实学院中提供了分步教程和更详细的自定义示例：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-367">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="b0ff6-368">MR 输入 211：手势</span><span class="sxs-lookup"><span data-stu-id="b0ff6-368">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="b0ff6-369">MR 输入 213：运动控制器</span><span class="sxs-lookup"><span data-stu-id="b0ff6-369">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="b0ff6-370">[![MR 输入 213 - 运动控制器](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="b0ff6-370">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="b0ff6-371">*MR 输入 213 - 运动控制器*</span><span class="sxs-lookup"><span data-stu-id="b0ff6-371">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b0ff6-372">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="b0ff6-372">Next Development Checkpoint</span></span>

<span data-ttu-id="b0ff6-373">如果你遵循我们布局的 Unity 开发旅程，则你正在探索 MRTK 核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-373">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="b0ff6-374">从这里，你可以继续了解下一部分基础知识：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-374">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0ff6-375">手部和眼部跟踪</span><span class="sxs-lookup"><span data-stu-id="b0ff6-375">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="b0ff6-376">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="b0ff6-376">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0ff6-377">共享体验</span><span class="sxs-lookup"><span data-stu-id="b0ff6-377">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="b0ff6-378">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="b0ff6-378">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0ff6-379">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b0ff6-379">See also</span></span>

* [<span data-ttu-id="b0ff6-380">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="b0ff6-380">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="b0ff6-381">运动控制器</span><span class="sxs-lookup"><span data-stu-id="b0ff6-381">Motion controllers</span></span>](../../design/motion-controllers.md)