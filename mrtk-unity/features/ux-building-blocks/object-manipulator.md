---
title: 对象操控器
description: 如何在 MRTK 中使用对象操控器
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 对象操作，
ms.openlocfilehash: f9b644c1447d6776389e227bfe49c27f82a3cf31
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176656"
---
# <a name="object-manipulator"></a><span data-ttu-id="322d2-104">对象操控器</span><span class="sxs-lookup"><span data-stu-id="322d2-104">Object manipulator</span></span>

![对象操控器](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="322d2-106">*ObjectManipulator* 是操作行为的新组件，以前在 *ManipulationHandler 中发现*。</span><span class="sxs-lookup"><span data-stu-id="322d2-106">The *ObjectManipulator* is the new component for manipulation behaviour, previously found in *ManipulationHandler*.</span></span> <span data-ttu-id="322d2-107">对象操控器进行了许多改进和简化。</span><span class="sxs-lookup"><span data-stu-id="322d2-107">The object manipulator makes a number of improvements and simplifications.</span></span> <span data-ttu-id="322d2-108">此组件将替换将弃用的操作处理程序。</span><span class="sxs-lookup"><span data-stu-id="322d2-108">This component is a replacement for the manipulation handler, which will be deprecated.</span></span>

<span data-ttu-id="322d2-109">*ObjectManipulator* 脚本使对象可移动、可缩放，并且使用一只或两只手可旋转。</span><span class="sxs-lookup"><span data-stu-id="322d2-109">The *ObjectManipulator* script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="322d2-110">可以将对象操控器配置为控制对象如何响应各种输入。</span><span class="sxs-lookup"><span data-stu-id="322d2-110">The object manipulator can be configured to control how the object will respond to various inputs.</span></span> <span data-ttu-id="322d2-111">该脚本应处理大多数形式的交互，例如HoloLens 2手部、HoloLens 2射线、HoloLens 1 凝视和手势以及沉浸式头戴显示设备运动控制器输入。</span><span class="sxs-lookup"><span data-stu-id="322d2-111">The script should work with most forms of interaction, such as HoloLens 2 articulated hand, HoloLens 2 hand rays, HoloLens 1 gaze and gestures and immersive headset motion controller input.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a><span data-ttu-id="322d2-112">如何使用对象操控器</span><span class="sxs-lookup"><span data-stu-id="322d2-112">How to use the object manipulator</span></span>

<span data-ttu-id="322d2-113">若要使用对象操控器，请首先将 `ObjectManipulator` 脚本组件添加到 GameObject。</span><span class="sxs-lookup"><span data-stu-id="322d2-113">To use the object manipulator, first add the `ObjectManipulator` script component to a GameObject.</span></span> <span data-ttu-id="322d2-114">请确保还将碰撞体添加到对象，使其与可抓取边界匹配。</span><span class="sxs-lookup"><span data-stu-id="322d2-114">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="322d2-115">若要使对象响应接近表达的手动输入，请 `NearInteractionGrabbable` 添加脚本。</span><span class="sxs-lookup"><span data-stu-id="322d2-115">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

<span data-ttu-id="322d2-116">通过将刚体组件添加到对象，为对象操控器启用物理行为。</span><span class="sxs-lookup"><span data-stu-id="322d2-116">Physics behaviour can be enabled for the object manipulator by adding a rigidbody component to the object.</span></span> <span data-ttu-id="322d2-117">在物理和碰撞中更详细地讨论了通过添加此组件 [*启用的物理行为*](#physics-and-collisions)。</span><span class="sxs-lookup"><span data-stu-id="322d2-117">Physics behaviour enabled by adding this component is discussed in greater detail in [*Physics and collisions*](#physics-and-collisions).</span></span>

<span data-ttu-id="322d2-118">此外，可以通过向 对象添加操作约束组件 [来限制](constraint-manager.md#transform-constraints) 操作。</span><span class="sxs-lookup"><span data-stu-id="322d2-118">As well as this, manipulation can be constrained by adding [manipulation constraint components](constraint-manager.md#transform-constraints) to the object.</span></span> <span data-ttu-id="322d2-119">这些是处理操作和以某种方式更改操作行为的特殊组件。</span><span class="sxs-lookup"><span data-stu-id="322d2-119">These are special components that work with manipulation and change the manipulation behaviour in some way.</span></span>

![在 Unity 编辑器中使用操作处理程序](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="322d2-121">检查器属性和字段</span><span class="sxs-lookup"><span data-stu-id="322d2-121">Inspector properties and fields</span></span>

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a><span data-ttu-id="322d2-122">常规属性</span><span class="sxs-lookup"><span data-stu-id="322d2-122">General properties</span></span>

#### <a name="host-transform"></a><span data-ttu-id="322d2-123">主机转换</span><span class="sxs-lookup"><span data-stu-id="322d2-123">Host transform</span></span>

<span data-ttu-id="322d2-124">要操作的对象转换。</span><span class="sxs-lookup"><span data-stu-id="322d2-124">The object transform that will be manipulated.</span></span> <span data-ttu-id="322d2-125">默认为组件的 对象。</span><span class="sxs-lookup"><span data-stu-id="322d2-125">Defaults to the object of the component.</span></span>

#### <a name="manipulation-type"></a><span data-ttu-id="322d2-126">操作类型</span><span class="sxs-lookup"><span data-stu-id="322d2-126">Manipulation type</span></span>

<span data-ttu-id="322d2-127">指定是否可以使用一只手或两只手操作对象。</span><span class="sxs-lookup"><span data-stu-id="322d2-127">Specifies whether the object can be manipulated using one hand or two hands.</span></span> <span data-ttu-id="322d2-128">由于此属性是一个标志，因此可以选中这两个选项。</span><span class="sxs-lookup"><span data-stu-id="322d2-128">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="322d2-129">*一手*：选中后启用一手操作。</span><span class="sxs-lookup"><span data-stu-id="322d2-129">*One handed*: Enables one handed manipulation if selected.</span></span>
- <span data-ttu-id="322d2-130">*两手*：如果选中，则启用两个手部操作。</span><span class="sxs-lookup"><span data-stu-id="322d2-130">*Two handed*: Enables two handed manipulation if selected.</span></span>

#### <a name="allow-far-manipulation"></a><span data-ttu-id="322d2-131">允许远操作</span><span class="sxs-lookup"><span data-stu-id="322d2-131">Allow far manipulation</span></span>

<span data-ttu-id="322d2-132">指定是否可以使用与指针的远部交互完成操作。</span><span class="sxs-lookup"><span data-stu-id="322d2-132">Specifies whether manipulation can be done using far interaction with pointers.</span></span>

### <a name="one-handed-manipulation-properties"></a><span data-ttu-id="322d2-133">单手操作属性</span><span class="sxs-lookup"><span data-stu-id="322d2-133">One handed manipulation properties</span></span>

#### <a name="one-hand-rotation-mode-near"></a><span data-ttu-id="322d2-134">附近的单手旋转模式</span><span class="sxs-lookup"><span data-stu-id="322d2-134">One hand rotation mode near</span></span>

<span data-ttu-id="322d2-135">指定在靠近一手抓取对象时对象的行为方式。</span><span class="sxs-lookup"><span data-stu-id="322d2-135">Specifies how the object will behave when it is being grabbed with one hand near.</span></span> <span data-ttu-id="322d2-136">这些选项仅适用于铰接式手。</span><span class="sxs-lookup"><span data-stu-id="322d2-136">These options only work for articulated hands.</span></span>

- <span data-ttu-id="322d2-137">*围绕对象中心旋转*：对象使用手部旋转，但围绕对象中心点旋转。</span><span class="sxs-lookup"><span data-stu-id="322d2-137">*Rotate about object center*: Object rotates using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="322d2-138">对象在旋转时似乎移动较少，但手和对象之间可能有断开连接感。</span><span class="sxs-lookup"><span data-stu-id="322d2-138">The object will appear to move less as it rotates, but there may be a feeling of disconnection between the hand and the object.</span></span> <span data-ttu-id="322d2-139">更适用于远地交互。</span><span class="sxs-lookup"><span data-stu-id="322d2-139">More useful for far interaction.</span></span>
- <span data-ttu-id="322d2-140">*围绕抓取点旋转*：用手围绕滚动块和手指之间的抓取点旋转对象。</span><span class="sxs-lookup"><span data-stu-id="322d2-140">*Rotate about grab point*: Rotate object with the hand about the grab point between the thumb and index finger.</span></span> <span data-ttu-id="322d2-141">它应感觉就像对象被手持有一样。</span><span class="sxs-lookup"><span data-stu-id="322d2-141">It should feel as if the object is being held by the hand.</span></span>

#### <a name="one-hand-rotation-mode-far"></a><span data-ttu-id="322d2-142">单手旋转模式远</span><span class="sxs-lookup"><span data-stu-id="322d2-142">One hand rotation mode far</span></span>

<span data-ttu-id="322d2-143">指定在距离上用一只手抓取对象时对象的行为方式。</span><span class="sxs-lookup"><span data-stu-id="322d2-143">Specifies how the object will behave when it is being grabbed with one hand at distance.</span></span> <span data-ttu-id="322d2-144">这些选项仅适用于铰接式手。</span><span class="sxs-lookup"><span data-stu-id="322d2-144">These options only work for articulated hands.</span></span>

- <span data-ttu-id="322d2-145">*围绕对象中心旋转*：使用手部旋转旋转对象，但围绕对象中心点旋转。</span><span class="sxs-lookup"><span data-stu-id="322d2-145">*Rotate about object center*: Rotate object using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="322d2-146">可用于在对象旋转时不移动对象中心的距离进行检查。</span><span class="sxs-lookup"><span data-stu-id="322d2-146">Useful for inspecting at a distance without the object center moving as the object rotates.</span></span>
- <span data-ttu-id="322d2-147">*旋转抓取点：* 使用手部旋转旋转对象，但围绕指针射线命中点旋转对象。</span><span class="sxs-lookup"><span data-stu-id="322d2-147">*Rotate about grab point*: Rotate object using rotation of the hand, but about the pointer ray hit point.</span></span> <span data-ttu-id="322d2-148">用于检查。</span><span class="sxs-lookup"><span data-stu-id="322d2-148">Useful for inspection.</span></span>

### <a name="two-handed-manipulation-properties"></a><span data-ttu-id="322d2-149">两手操作属性</span><span class="sxs-lookup"><span data-stu-id="322d2-149">Two handed manipulation properties</span></span>

#### <a name="two-handed-manipulation-type"></a><span data-ttu-id="322d2-150">两手操作类型</span><span class="sxs-lookup"><span data-stu-id="322d2-150">Two handed manipulation type</span></span>

<span data-ttu-id="322d2-151">指定两个手动操作如何转换对象。</span><span class="sxs-lookup"><span data-stu-id="322d2-151">Specifies how two hand manipulation can transform an object.</span></span> <span data-ttu-id="322d2-152">由于此属性是标志，因此可以选择任意数目的选项。</span><span class="sxs-lookup"><span data-stu-id="322d2-152">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="322d2-153">*移动*：如果选中，则允许移动。</span><span class="sxs-lookup"><span data-stu-id="322d2-153">*Move*: Moving is allowed if selected.</span></span>
- <span data-ttu-id="322d2-154">*缩放*：如果选中，则允许缩放。</span><span class="sxs-lookup"><span data-stu-id="322d2-154">*Scale*: Scaling is allowed if selected.</span></span>
- <span data-ttu-id="322d2-155">*旋转*：如果选中，则允许旋转。</span><span class="sxs-lookup"><span data-stu-id="322d2-155">*Rotate*: Rotation is allowed if selected.</span></span>

![操作处理程序](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a><span data-ttu-id="322d2-157">约束</span><span class="sxs-lookup"><span data-stu-id="322d2-157">Constraints</span></span>

#### <a name="enable-constraints"></a><span data-ttu-id="322d2-158">启用约束</span><span class="sxs-lookup"><span data-stu-id="322d2-158">Enable constraints</span></span>

<span data-ttu-id="322d2-159">此设置将启用链接的约束 [管理器](constraint-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="322d2-159">This setting will enable the linked [constraint manager](constraint-manager.md).</span></span> <span data-ttu-id="322d2-160">转换更改由注册到所选约束管理器 [的约束处理](constraint-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="322d2-160">Transform changes will be processed by constraints registered to the selected [constraint manager](constraint-manager.md).</span></span>

#### <a name="constraint-manager"></a><span data-ttu-id="322d2-161">约束管理器</span><span class="sxs-lookup"><span data-stu-id="322d2-161">Constraint manager</span></span>

<span data-ttu-id="322d2-162">下拉列表允许选择任何附加的约束 [管理器](constraint-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="322d2-162">The dropdown allows to select any of the attached [constraint managers](constraint-manager.md).</span></span> <span data-ttu-id="322d2-163">对象操控器可确保始终 [附加约束](constraint-manager.md) 管理器。</span><span class="sxs-lookup"><span data-stu-id="322d2-163">Object manipulator ensures there's a [constraint manager](constraint-manager.md) attached at all times.</span></span>
<span data-ttu-id="322d2-164">请注意，同一类型的多个组件将在 unity 中以同一名称显示。</span><span class="sxs-lookup"><span data-stu-id="322d2-164">Note that multiple components of the same type will show up under the same name in unity.</span></span> <span data-ttu-id="322d2-165">为了更轻松地区分同一对象上的多个约束管理器，可用选项将显示有关所选约束管理器配置的提示 (手动或自动选择约束) 。</span><span class="sxs-lookup"><span data-stu-id="322d2-165">To make it easier to distinguish between multiple constraint managers on the same object, the available options will show a hint on the configuration of the selected constraint manager (manual or auto constraint selection).</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="322d2-166">转到组件</span><span class="sxs-lookup"><span data-stu-id="322d2-166">Go to component</span></span>

<span data-ttu-id="322d2-167">约束管理器选择附带"转到 *组件"* 按钮。</span><span class="sxs-lookup"><span data-stu-id="322d2-167">The constraint manager selection comes with a *Go to component* button.</span></span> <span data-ttu-id="322d2-168">此按钮将导致检查器滚动到所选组件，以便可以配置该组件。</span><span class="sxs-lookup"><span data-stu-id="322d2-168">This button will cause the inspector to scroll to the selected component so that it can be configured.</span></span>

### <a name="physics"></a><span data-ttu-id="322d2-169">物理</span><span class="sxs-lookup"><span data-stu-id="322d2-169">Physics</span></span>

<span data-ttu-id="322d2-170">设置对象具有一个 RigidBody 组件时，才显示本部分中的属性。</span><span class="sxs-lookup"><span data-stu-id="322d2-170">Settings in this section appear only when the object has a RigidBody component.</span></span>

#### <a name="release-behavior"></a><span data-ttu-id="322d2-171">发布行为</span><span class="sxs-lookup"><span data-stu-id="322d2-171">Release behavior</span></span>

<span data-ttu-id="322d2-172">指定操作对象在释放时应保留的物理属性。</span><span class="sxs-lookup"><span data-stu-id="322d2-172">Specify which physical properties a manipulated object should keep upon release.</span></span> <span data-ttu-id="322d2-173">由于此属性是一个标志，因此可以选中这两个选项。</span><span class="sxs-lookup"><span data-stu-id="322d2-173">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="322d2-174">*保持速度*：释放对象时，如果选择此选项，它将保持其线性速度。</span><span class="sxs-lookup"><span data-stu-id="322d2-174">*Keep Velocity*: When the object is released, if this option is selected it will keep its linear velocity.</span></span>
- <span data-ttu-id="322d2-175">*保持Angular* 速度：释放对象时，如果选择此选项，它将保持其角速度。</span><span class="sxs-lookup"><span data-stu-id="322d2-175">*Keep Angular Velocity*: When the object is released, if this option is selected it will keep its angular velocity.</span></span>

#### <a name="use-forces-for-near-manipulation"></a><span data-ttu-id="322d2-176">使用强制进行近操作</span><span class="sxs-lookup"><span data-stu-id="322d2-176">Use forces for near manipulation</span></span>

<span data-ttu-id="322d2-177">执行近操作时，是否使用物理力来移动对象。</span><span class="sxs-lookup"><span data-stu-id="322d2-177">Whether physics forces are used to move the object when performing near manipulations.</span></span> <span data-ttu-id="322d2-178">将此选项 *设置为 false* 会使对象感觉更直接地连接到用户手。</span><span class="sxs-lookup"><span data-stu-id="322d2-178">Setting this to *false* will make the object feel more directly connected to the users hand.</span></span> <span data-ttu-id="322d2-179">将此设置 *设置为 true* 将遵守对象的质和惯性，但可能感觉对象通过一个 spring 连接。</span><span class="sxs-lookup"><span data-stu-id="322d2-179">Setting this to *true* will honor the mass and inertia of the object, but may feel as though the object is connected through a spring.</span></span> <span data-ttu-id="322d2-180">默认值为 false。</span><span class="sxs-lookup"><span data-stu-id="322d2-180">The default is *false*.</span></span>

### <a name="smoothing"></a><span data-ttu-id="322d2-181">平滑处理</span><span class="sxs-lookup"><span data-stu-id="322d2-181">Smoothing</span></span>

#### <a name="smoothing-far"></a><span data-ttu-id="322d2-182">远平滑</span><span class="sxs-lookup"><span data-stu-id="322d2-182">Smoothing far</span></span>

<span data-ttu-id="322d2-183">是否为远部交互启用与帧速率无关的平滑处理。</span><span class="sxs-lookup"><span data-stu-id="322d2-183">Whether frame-rate independent smoothing is enabled for far interactions.</span></span> <span data-ttu-id="322d2-184">默认情况下启用远平滑。</span><span class="sxs-lookup"><span data-stu-id="322d2-184">Far smoothing is enabled by default.</span></span>

#### <a name="smoothing-near"></a><span data-ttu-id="322d2-185">平滑处理接近</span><span class="sxs-lookup"><span data-stu-id="322d2-185">Smoothing near</span></span>

<span data-ttu-id="322d2-186">是否为近交互启用了帧速率无关的平滑处理。</span><span class="sxs-lookup"><span data-stu-id="322d2-186">Whether frame-rate independent smoothing is enabled for near interactions.</span></span> <span data-ttu-id="322d2-187">默认情况下禁用近平滑，因为效果可能被视为与手"断开连接"。</span><span class="sxs-lookup"><span data-stu-id="322d2-187">Near smoothing is disabled by default because the effect may be perceived as being 'disconnected' from the hand.</span></span>

#### <a name="smoothing-active"></a><span data-ttu-id="322d2-188">平滑处理活动</span><span class="sxs-lookup"><span data-stu-id="322d2-188">Smoothing active</span></span>

<span data-ttu-id="322d2-189">已过时，将在未来版本中删除。</span><span class="sxs-lookup"><span data-stu-id="322d2-189">Obsolete and will be removed in a future version.</span></span> <span data-ttu-id="322d2-190">应用程序应该使用 SmoothingFar、SmoothingNear 或这两者的组合。</span><span class="sxs-lookup"><span data-stu-id="322d2-190">Applications should use SmoothingFar, SmoothingNear or a combination of the two.</span></span>

#### <a name="move-lerp-time"></a><span data-ttu-id="322d2-191">移动 lerp 时间</span><span class="sxs-lookup"><span data-stu-id="322d2-191">Move lerp time</span></span>

<span data-ttu-id="322d2-192">要应用于移动的平滑量。</span><span class="sxs-lookup"><span data-stu-id="322d2-192">Amount of smoothing to apply to the movement.</span></span> <span data-ttu-id="322d2-193">平滑为 0 表示无平滑。</span><span class="sxs-lookup"><span data-stu-id="322d2-193">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="322d2-194">最大值表示不更改值。</span><span class="sxs-lookup"><span data-stu-id="322d2-194">Max value means no change to value.</span></span>

#### <a name="rotate-lerp-time"></a><span data-ttu-id="322d2-195">旋转 lerp 时间</span><span class="sxs-lookup"><span data-stu-id="322d2-195">Rotate lerp time</span></span>

<span data-ttu-id="322d2-196">要应用于旋转的平滑量。</span><span class="sxs-lookup"><span data-stu-id="322d2-196">Amount of smoothing to apply to the rotation.</span></span> <span data-ttu-id="322d2-197">平滑为 0 表示无平滑。</span><span class="sxs-lookup"><span data-stu-id="322d2-197">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="322d2-198">最大值表示不更改值。</span><span class="sxs-lookup"><span data-stu-id="322d2-198">Max value means no change to value.</span></span>

#### <a name="scale-lerp-time"></a><span data-ttu-id="322d2-199">缩放 lerp 时间</span><span class="sxs-lookup"><span data-stu-id="322d2-199">Scale lerp time</span></span>

<span data-ttu-id="322d2-200">要应用于刻度的平滑量。</span><span class="sxs-lookup"><span data-stu-id="322d2-200">Amount of smoothing to apply to the scale.</span></span> <span data-ttu-id="322d2-201">平滑0表示无平滑处理。</span><span class="sxs-lookup"><span data-stu-id="322d2-201">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="322d2-202">Max 值表示没有更改为值。</span><span class="sxs-lookup"><span data-stu-id="322d2-202">Max value means no change to value.</span></span>

### <a name="manipulation-events"></a><span data-ttu-id="322d2-203">操作事件</span><span class="sxs-lookup"><span data-stu-id="322d2-203">Manipulation events</span></span>

<span data-ttu-id="322d2-204">操作处理程序提供了以下事件：</span><span class="sxs-lookup"><span data-stu-id="322d2-204">Manipulation handler provides the following events:</span></span>

- <span data-ttu-id="322d2-205">*OnManipulationStarted*：在操作开始时激发。</span><span class="sxs-lookup"><span data-stu-id="322d2-205">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
- <span data-ttu-id="322d2-206">*OnManipulationEnded*：操作结束时激发。</span><span class="sxs-lookup"><span data-stu-id="322d2-206">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
- <span data-ttu-id="322d2-207">*OnHoverStarted*：当右/控制器悬停可操作时，将会激发。</span><span class="sxs-lookup"><span data-stu-id="322d2-207">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
- <span data-ttu-id="322d2-208">*OnHoverEnded*：当手动/控制器取消悬停可操作时，将触发此操作。</span><span class="sxs-lookup"><span data-stu-id="322d2-208">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>

<span data-ttu-id="322d2-209">操作的事件激发顺序是：</span><span class="sxs-lookup"><span data-stu-id="322d2-209">The event fire order for manipulation is:</span></span>

<span data-ttu-id="322d2-210">*OnHoverStarted*  -> *OnManipulationStarted*  -> *OnManipulationEnded*  -> *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="322d2-210">*OnHoverStarted* -> *OnManipulationStarted* -> *OnManipulationEnded* -> *OnHoverEnded*</span></span>

<span data-ttu-id="322d2-211">如果没有操作，则仍会获得具有以下触发顺序的悬停事件：</span><span class="sxs-lookup"><span data-stu-id="322d2-211">If there is no manipulation, you will still get hover events with the following fire order:</span></span>

<span data-ttu-id="322d2-212">*OnHoverStarted*  -> *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="322d2-212">*OnHoverStarted* -> *OnHoverEnded*</span></span>

## <a name="physics-and-collisions"></a><span data-ttu-id="322d2-213">物理和冲突</span><span class="sxs-lookup"><span data-stu-id="322d2-213">Physics and collisions</span></span>

<span data-ttu-id="322d2-214">可以通过将刚体组件添加到与对象操控器相同的对象来启用物理学行为。</span><span class="sxs-lookup"><span data-stu-id="322d2-214">Physics behaviour can be enabled by adding a rigidbody component to the same object as an object manipulator.</span></span> <span data-ttu-id="322d2-215">此功能不仅能启用上述 [版本行为](#release-behavior) 配置，还可以启用冲突。</span><span class="sxs-lookup"><span data-stu-id="322d2-215">Not only does this enable configuration of [release behaviour](#release-behavior) above, it also enables collisions.</span></span> <span data-ttu-id="322d2-216">如果没有刚体组件，则在操作过程中冲突不能正常运行：</span><span class="sxs-lookup"><span data-stu-id="322d2-216">Without a rigidbody component, collisions don't behave correctly during manipulation:</span></span>

- <span data-ttu-id="322d2-217">操作对象和静态碰撞器之间的冲突 (即，具有碰撞器但没有刚体的对象) 不起作用，操作对象直接通过静态碰撞器进行不受影响。</span><span class="sxs-lookup"><span data-stu-id="322d2-217">Collisions between a manipulated object and a static collider (i.e. an object with a collider but no rigidbody) do not work, the manipulated object passes straight through the static collider unaffected.</span></span>
- <span data-ttu-id="322d2-218">操作对象与刚体之间的冲突 (例如</span><span class="sxs-lookup"><span data-stu-id="322d2-218">Collisions between a manipulated object and a rigidbody (i.e</span></span> <span data-ttu-id="322d2-219">同时具有碰撞器和刚体) 的对象导致刚体具有冲突响应，但响应为 jumpy 和非自然。</span><span class="sxs-lookup"><span data-stu-id="322d2-219">an object with both a collider and a rigidbody) cause the rigidbody to have a collision response, but the response is jumpy and unnatural.</span></span> <span data-ttu-id="322d2-220">对于操作的对象也不存在任何冲突响应。</span><span class="sxs-lookup"><span data-stu-id="322d2-220">There is also no collision response on the manipulated object.</span></span>

<span data-ttu-id="322d2-221">添加刚体时，冲突应正常工作。</span><span class="sxs-lookup"><span data-stu-id="322d2-221">When a rigidbody is added, collisions should work correctly.</span></span>

### <a name="without-rigidbody"></a><span data-ttu-id="322d2-222">无刚体</span><span class="sxs-lookup"><span data-stu-id="322d2-222">Without rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a><span data-ttu-id="322d2-223">With 刚体</span><span class="sxs-lookup"><span data-stu-id="322d2-223">With rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a><span data-ttu-id="322d2-224">池中弹性 (试验性) </span><span class="sxs-lookup"><span data-stu-id="322d2-224">Elastics (Experimental)</span></span>

<span data-ttu-id="322d2-225">通过对象操控器操作对象时，可以使用池中弹性。</span><span class="sxs-lookup"><span data-stu-id="322d2-225">Elastics can be used when manipulating objects via object manipulator.</span></span> <span data-ttu-id="322d2-226">请注意， [池中弹性系统](../experimental/elastic-system.md) 仍处于试验状态。</span><span class="sxs-lookup"><span data-stu-id="322d2-226">Note that the [elastics system](../experimental/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="322d2-227">若要启用池中弹性，请链接现有的池中弹性 manager 组件或通过按钮创建和链接新的池中弹性管理器 `Add Elastics Manager` 。</span><span class="sxs-lookup"><span data-stu-id="322d2-227">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a><span data-ttu-id="322d2-228">另请参阅</span><span class="sxs-lookup"><span data-stu-id="322d2-228">See also</span></span>

- [<span data-ttu-id="322d2-229">边界控件</span><span class="sxs-lookup"><span data-stu-id="322d2-229">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="322d2-230">约束管理器</span><span class="sxs-lookup"><span data-stu-id="322d2-230">Constraint manager</span></span>](constraint-manager.md)
- [<span data-ttu-id="322d2-231">迁移时限</span><span class="sxs-lookup"><span data-stu-id="322d2-231">Migration window</span></span>](../tools/migration-window.md)
- [<span data-ttu-id="322d2-232">池中弹性系统 (试验性) </span><span class="sxs-lookup"><span data-stu-id="322d2-232">Elastics system (Experimental)</span></span>](../experimental/elastic-system.md)
