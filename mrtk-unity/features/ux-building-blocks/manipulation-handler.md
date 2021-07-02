---
title: 操作处理程序
description: 有关 MRTK 中的操作处理程序的文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 操作，
ms.openlocfilehash: 179ef40ba054b0fda3b13e9d578905eb064a58ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176631"
---
# <a name="manipulation-handler"></a><span data-ttu-id="e9b83-104">操作处理程序</span><span class="sxs-lookup"><span data-stu-id="e9b83-104">Manipulation handler</span></span>

![操作处理程序](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="e9b83-106">*ManipulationHandler* 脚本允许使用一只或两只手使对象可移动、可缩放且可旋转。</span><span class="sxs-lookup"><span data-stu-id="e9b83-106">The *ManipulationHandler* script allows for an object to be made movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="e9b83-107">可以限制操作，以便仅允许某些类型的转换。</span><span class="sxs-lookup"><span data-stu-id="e9b83-107">Manipulation can be restricted so that it only allows certain kinds of transformation.</span></span> <span data-ttu-id="e9b83-108">该脚本适用于各种类型的输入，包括HoloLens 2手部输入、手部射线、HoloLens (第一代) 手势输入和沉浸式头戴显示设备运动控制器输入。</span><span class="sxs-lookup"><span data-stu-id="e9b83-108">The script works with various types of inputs including HoloLens 2 articulated hand input, hand-rays, HoloLens (1st gen) gesture input, and immersive headset motion controller input.</span></span>

## <a name="how-to-use-the-manipulation-handler"></a><span data-ttu-id="e9b83-109">如何使用操作处理程序</span><span class="sxs-lookup"><span data-stu-id="e9b83-109">How to use the manipulation handler</span></span>

<span data-ttu-id="e9b83-110">将 `ManipulationHandler` 脚本组件添加到 GameObject。</span><span class="sxs-lookup"><span data-stu-id="e9b83-110">Add the `ManipulationHandler` script component to a GameObject.</span></span> <span data-ttu-id="e9b83-111">请确保还将碰撞体添加到对象，使其与可抓取边界匹配。</span><span class="sxs-lookup"><span data-stu-id="e9b83-111">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="e9b83-112">若要使对象响应接近表达的手动输入，请 `NearInteractionGrabbable` 添加脚本。</span><span class="sxs-lookup"><span data-stu-id="e9b83-112">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

![在 unity 编辑器中使用操作处理程序](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a><span data-ttu-id="e9b83-114">检查器属性</span><span class="sxs-lookup"><span data-stu-id="e9b83-114">Inspector properties</span></span>

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

<span data-ttu-id="e9b83-115">**主机转换** 将拖动的转换。</span><span class="sxs-lookup"><span data-stu-id="e9b83-115">**Host Transform** Transform that will be dragged.</span></span> <span data-ttu-id="e9b83-116">默认为组件的 对象。</span><span class="sxs-lookup"><span data-stu-id="e9b83-116">Defaults to the object of the component.</span></span>

<span data-ttu-id="e9b83-117">**操作类型** 指定是否可以使用一只手、两只手或两手操作对象。</span><span class="sxs-lookup"><span data-stu-id="e9b83-117">**Manipulation Type** Specifies whether the object can be manipulated using one hand, two hands, or both.</span></span>

* <span data-ttu-id="e9b83-118">*仅一手*</span><span class="sxs-lookup"><span data-stu-id="e9b83-118">*One handed only*</span></span>
* <span data-ttu-id="e9b83-119">*仅两手*</span><span class="sxs-lookup"><span data-stu-id="e9b83-119">*Two handed only*</span></span>
* <span data-ttu-id="e9b83-120">*一手和两手*</span><span class="sxs-lookup"><span data-stu-id="e9b83-120">*One and Two handed*</span></span>

<span data-ttu-id="e9b83-121">**两手操作类型**</span><span class="sxs-lookup"><span data-stu-id="e9b83-121">**Two Handed Manipulation Type**</span></span>

* <span data-ttu-id="e9b83-122">*缩放*：仅允许缩放。</span><span class="sxs-lookup"><span data-stu-id="e9b83-122">*Scale*: Only scaling is allowed.</span></span>
* <span data-ttu-id="e9b83-123">*旋转*：仅允许旋转。</span><span class="sxs-lookup"><span data-stu-id="e9b83-123">*Rotate*: Only rotation is allowed.</span></span>
* <span data-ttu-id="e9b83-124">*移动缩放*：允许移动和缩放。</span><span class="sxs-lookup"><span data-stu-id="e9b83-124">*Move Scale*: Moving and scaling is allowed.</span></span>
* <span data-ttu-id="e9b83-125">*移动旋转*：允许移动和旋转。</span><span class="sxs-lookup"><span data-stu-id="e9b83-125">*Move Rotate*: Moving and rotating is allowed.</span></span>
* <span data-ttu-id="e9b83-126">*旋转缩放*：允许旋转和缩放。</span><span class="sxs-lookup"><span data-stu-id="e9b83-126">*Rotate Scale*: Rotating and scaling is allowed.</span></span>
* <span data-ttu-id="e9b83-127">*移动旋转刻度*：允许移动、旋转和缩放。</span><span class="sxs-lookup"><span data-stu-id="e9b83-127">*Move Rotate Scale*: Moving, rotating and scaling is allowed.</span></span>

![操作处理程序](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

<span data-ttu-id="e9b83-129">**允许远操作** 指定是否可以使用与指针的远部交互完成操作。</span><span class="sxs-lookup"><span data-stu-id="e9b83-129">**Allow Far Manipulation** Specifies whether manipulation can be done using far interaction with pointers.</span></span>

<span data-ttu-id="e9b83-130">**单手旋转模式附近** 指定在靠近一个手/控制器抓取对象时对象的行为方式。</span><span class="sxs-lookup"><span data-stu-id="e9b83-130">**One Hand Rotation Mode Near** Specifies how the object will behave when it is being grabbed with one hand / controller near.</span></span>

<span data-ttu-id="e9b83-131">**单手旋转模式远** 指定在距离上用一只手/控制器抓取对象时对象的行为方式。</span><span class="sxs-lookup"><span data-stu-id="e9b83-131">**One Hand Rotation Mode Far** Specifies how the object will behave when it is being grabbed with one hand / controller at distance.</span></span>

<span data-ttu-id="e9b83-132">**单手旋转模式选项** 指定用一手抓取对象时对象的旋转方向。</span><span class="sxs-lookup"><span data-stu-id="e9b83-132">**One Hand Rotation Mode Options** Specifies how the object will rotate when it is being grabbed with one hand.</span></span>

* <span data-ttu-id="e9b83-133">*维护原始旋转*：在移动对象时不旋转对象</span><span class="sxs-lookup"><span data-stu-id="e9b83-133">*Maintain original rotation*: Does not rotate object as it is being moved</span></span>
* <span data-ttu-id="e9b83-134">*向用户维护旋转*：为用户维护 X/Y 轴的对象原始旋转</span><span class="sxs-lookup"><span data-stu-id="e9b83-134">*Maintain rotation to user*: Maintains the object's original rotation for X/Y axis to the user</span></span>
* <span data-ttu-id="e9b83-135">*垂直对齐使旋转保持旋转到用户*：将对象的原始旋转维护给用户，但使对象垂直旋转。</span><span class="sxs-lookup"><span data-stu-id="e9b83-135">*Gravity aligned maintain rotation to user*: Maintains object's original rotation to user, but makes the object vertical.</span></span> <span data-ttu-id="e9b83-136">对于具有边界控件的对象很有用。</span><span class="sxs-lookup"><span data-stu-id="e9b83-136">Useful for objects with a bounds control.</span></span>
* <span data-ttu-id="e9b83-137">*人脸用户*：确保对象始终面向用户。</span><span class="sxs-lookup"><span data-stu-id="e9b83-137">*Face user*: Ensures object always faces the user.</span></span> <span data-ttu-id="e9b83-138">适用于平板电脑/面板。</span><span class="sxs-lookup"><span data-stu-id="e9b83-138">Useful for slates/panels.</span></span>
* <span data-ttu-id="e9b83-139">*人脸离开用户*：确保对象始终面向用户。</span><span class="sxs-lookup"><span data-stu-id="e9b83-139">*Face away from user*: Ensures object always faces away from user.</span></span> <span data-ttu-id="e9b83-140">适用于向后配置的板/面板。</span><span class="sxs-lookup"><span data-stu-id="e9b83-140">Useful for slates/panels that are configured backwards.</span></span>
* <span data-ttu-id="e9b83-141">*围绕对象中心旋转*：仅适用于铰接式手/控制器。</span><span class="sxs-lookup"><span data-stu-id="e9b83-141">*Rotate about object center*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="e9b83-142">使用手/控制器的旋转旋转对象，但围绕对象中心点旋转对象。</span><span class="sxs-lookup"><span data-stu-id="e9b83-142">Rotate object using rotation of the hand/controller, but about the object center point.</span></span> <span data-ttu-id="e9b83-143">可用于在距离上检查。</span><span class="sxs-lookup"><span data-stu-id="e9b83-143">Useful for inspecting at a distance.</span></span>
* <span data-ttu-id="e9b83-144">*围绕抓取点旋转*：仅适用于铰接式手/控制器。</span><span class="sxs-lookup"><span data-stu-id="e9b83-144">*Rotate about grab point*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="e9b83-145">旋转对象，就像由手/控制器持有一样。</span><span class="sxs-lookup"><span data-stu-id="e9b83-145">Rotate object as if it was being held by hand/controller.</span></span> <span data-ttu-id="e9b83-146">用于检查。</span><span class="sxs-lookup"><span data-stu-id="e9b83-146">Useful for inspection.</span></span>

<span data-ttu-id="e9b83-147">**发布行为** 释放对象时，指定其物理移动行为。</span><span class="sxs-lookup"><span data-stu-id="e9b83-147">**Release Behavior** When an object is released, specify its physical movement behavior.</span></span> <span data-ttu-id="e9b83-148">要求一个刚体组件位于该对象上。</span><span class="sxs-lookup"><span data-stu-id="e9b83-148">Requires a rigidbody component to be on that object.</span></span>

* <span data-ttu-id="e9b83-149">*无*</span><span class="sxs-lookup"><span data-stu-id="e9b83-149">*Nothing*</span></span>
* <span data-ttu-id="e9b83-150">*全部内容*</span><span class="sxs-lookup"><span data-stu-id="e9b83-150">*Everything*</span></span>
* <span data-ttu-id="e9b83-151">*保持速度*</span><span class="sxs-lookup"><span data-stu-id="e9b83-151">*Keep Velocity*</span></span>
* <span data-ttu-id="e9b83-152">*保持Angular速度*</span><span class="sxs-lookup"><span data-stu-id="e9b83-152">*Keep Angular Velocity*</span></span>

<span data-ttu-id="e9b83-153">**旋转约束** 指定对象在交互时将在哪个轴上旋转。</span><span class="sxs-lookup"><span data-stu-id="e9b83-153">**Constraints on Rotation** Specifies on which axis the object will rotate when interacted with.</span></span>

* <span data-ttu-id="e9b83-154">*无*</span><span class="sxs-lookup"><span data-stu-id="e9b83-154">*None*</span></span>
* <span data-ttu-id="e9b83-155">*仅 X 轴*</span><span class="sxs-lookup"><span data-stu-id="e9b83-155">*X-Axis Only*</span></span>
* <span data-ttu-id="e9b83-156">*仅 Y 轴*</span><span class="sxs-lookup"><span data-stu-id="e9b83-156">*Y-Axis Only*</span></span>
* <span data-ttu-id="e9b83-157">*仅 Z 轴*</span><span class="sxs-lookup"><span data-stu-id="e9b83-157">*Z-Axis Only*</span></span>

<span data-ttu-id="e9b83-158">**将本地空间用于约束** 一个切换开关，用于在应用世界空间轴或本地空间轴的约束之间进行切换。</span><span class="sxs-lookup"><span data-stu-id="e9b83-158">**Use Local Space For Constraint** A toggle to switch between applying constraints in respect to world-space axis, or local space axis.</span></span>

<span data-ttu-id="e9b83-159">**移动约束**</span><span class="sxs-lookup"><span data-stu-id="e9b83-159">**Constraints on Movement**</span></span>

* <span data-ttu-id="e9b83-160">*无*</span><span class="sxs-lookup"><span data-stu-id="e9b83-160">*None*</span></span>
* <span data-ttu-id="e9b83-161">*修复与头部的距离*</span><span class="sxs-lookup"><span data-stu-id="e9b83-161">*Fix distance from head*</span></span>

<span data-ttu-id="e9b83-162">**平滑处理活动** 指定平滑是否处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="e9b83-162">**Smoothing Active** Specifies whether smoothing is active.</span></span>

<span data-ttu-id="e9b83-163">**一手平滑量** 要应用于移动、缩放、旋转的平滑量。</span><span class="sxs-lookup"><span data-stu-id="e9b83-163">**Smoothing Amount One Hand** Amount of smoothing to apply to the movement, scale, rotation.</span></span> <span data-ttu-id="e9b83-164">平滑为 0 表示无平滑。</span><span class="sxs-lookup"><span data-stu-id="e9b83-164">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="e9b83-165">最大值表示不更改值。</span><span class="sxs-lookup"><span data-stu-id="e9b83-165">Max value means no change to value.</span></span>

## <a name="events"></a><span data-ttu-id="e9b83-166">事件</span><span class="sxs-lookup"><span data-stu-id="e9b83-166">Events</span></span>

<span data-ttu-id="e9b83-167">操作处理程序提供以下事件：</span><span class="sxs-lookup"><span data-stu-id="e9b83-167">Manipulation handler provides the following events:</span></span>

* <span data-ttu-id="e9b83-168">*OnManipulationStarted：* 在操作开始时触发。</span><span class="sxs-lookup"><span data-stu-id="e9b83-168">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
* <span data-ttu-id="e9b83-169">*OnManipulationEnded：* 操作结束时触发。</span><span class="sxs-lookup"><span data-stu-id="e9b83-169">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
* <span data-ttu-id="e9b83-170">*OnHoverStarted：* 当手/控制器将可操作对象悬停在近或远时触发。</span><span class="sxs-lookup"><span data-stu-id="e9b83-170">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
* <span data-ttu-id="e9b83-171">*OnHoverEnded：* 当手/控制器取消悬停可操作对象（近或远）时触发。</span><span class="sxs-lookup"><span data-stu-id="e9b83-171">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>
