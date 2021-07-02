---
title: 约束管理器
description: MRTK 中的约束管理器概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 7036bb552952a0e45a8ba465d769a8952e48bc36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177555"
---
# <a name="constraint-manager"></a><span data-ttu-id="570d1-104">约束管理器</span><span class="sxs-lookup"><span data-stu-id="570d1-104">Constraint manager</span></span>

<span data-ttu-id="570d1-105">约束管理器允许将一组约束组件应用于转换。</span><span class="sxs-lookup"><span data-stu-id="570d1-105">The constraint manager allows to apply a set of constraint components to a transform.</span></span> <span data-ttu-id="570d1-106">可以 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) 考虑附加到游戏对象的类型的组件。</span><span class="sxs-lookup"><span data-stu-id="570d1-106">Components of type [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) that are attached to the game object can be taken into consideration.</span></span>
<span data-ttu-id="570d1-107">默认情况下，约束管理器将自动 [收集附加到游戏](#transform-constraints) 对象的所有约束组件，并应用于已处理的转换。</span><span class="sxs-lookup"><span data-stu-id="570d1-107">Per default, constraint manager will automatically collect all [constraint components](#transform-constraints) attached to the game object and apply them to processed transforms.</span></span>
<span data-ttu-id="570d1-108">但是，用户可以选择手动配置应用的约束列表，只允许应用附加约束的子集。</span><span class="sxs-lookup"><span data-stu-id="570d1-108">However users can opt for configuring the list of applied constraints manually and allowing only a subset of attached constraints to be applied.</span></span>

<span data-ttu-id="570d1-109">目前，以下 MRTK UX 元素支持约束管理器：</span><span class="sxs-lookup"><span data-stu-id="570d1-109">Currently the following MRTK UX elements are supporting constraint manager:</span></span>

- [<span data-ttu-id="570d1-110">边界控件</span><span class="sxs-lookup"><span data-stu-id="570d1-110">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="570d1-111">对象操控器</span><span class="sxs-lookup"><span data-stu-id="570d1-111">Object manipulator</span></span>](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="570d1-112">检查器属性和字段</span><span class="sxs-lookup"><span data-stu-id="570d1-112">Inspector properties and fields</span></span>

<span data-ttu-id="570d1-113">约束管理器可以在两种模式下运行：</span><span class="sxs-lookup"><span data-stu-id="570d1-113">Constraint manager can be operated in two modes:</span></span>

- <span data-ttu-id="570d1-114">自动约束选择</span><span class="sxs-lookup"><span data-stu-id="570d1-114">Auto constraint selection</span></span>
- <span data-ttu-id="570d1-115">手动约束选择</span><span class="sxs-lookup"><span data-stu-id="570d1-115">Manual constraint selection</span></span>

### <a name="auto-constraint-selection"></a><span data-ttu-id="570d1-116">自动约束选择</span><span class="sxs-lookup"><span data-stu-id="570d1-116">Auto constraint selection</span></span>

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

<span data-ttu-id="570d1-117">约束管理器的默认模式（自动约束选择）将提供所有附加约束组件的列表，以及转到按钮和添加[约束按钮](#add-constraint-to-game-object)。 [](#go-to-component)</span><span class="sxs-lookup"><span data-stu-id="570d1-117">The default mode of constraint manager, auto constraint selection, will provide a list of all attached constraint components as well as [go to buttons](#go-to-component) and an [add constraint button](#add-constraint-to-game-object).</span></span>

#### <a name="add-constraint-to-game-object"></a><span data-ttu-id="570d1-118">向游戏对象添加约束</span><span class="sxs-lookup"><span data-stu-id="570d1-118">Add constraint to game object</span></span>

<span data-ttu-id="570d1-119">此按钮允许直接从约束管理器检查器添加约束组件。</span><span class="sxs-lookup"><span data-stu-id="570d1-119">This button allows a constraint component to be added directly from the constraint manager inspector.</span></span> <span data-ttu-id="570d1-120">项目的所有约束类型应在此处可见。</span><span class="sxs-lookup"><span data-stu-id="570d1-120">All constraint types in a project should be visible here.</span></span> <span data-ttu-id="570d1-121">有关详细信息 [，请参阅](#transform-constraints) 转换约束。</span><span class="sxs-lookup"><span data-stu-id="570d1-121">See [transform constraints](#transform-constraints) for more info.</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="570d1-122">转到组件</span><span class="sxs-lookup"><span data-stu-id="570d1-122">Go to component</span></span>

<span data-ttu-id="570d1-123">此处列出了在对象上找到的所有约束，并包含" *转到组件"* 按钮。</span><span class="sxs-lookup"><span data-stu-id="570d1-123">All constraints found on the object wil be listed here with a *Go to component* button.</span></span> <span data-ttu-id="570d1-124">此按钮将导致检查器滚动到所选约束组件，以便可以配置该组件。</span><span class="sxs-lookup"><span data-stu-id="570d1-124">This button will cause the inspector to scroll to the selected constraint component so that it can be configured.</span></span>

### <a name="manual-constraint-selection"></a><span data-ttu-id="570d1-125">手动约束选择</span><span class="sxs-lookup"><span data-stu-id="570d1-125">Manual constraint selection</span></span>

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

<span data-ttu-id="570d1-126">如果约束管理器设置为手动模式，则仅处理约束列表中链接的约束并应用于转换。</span><span class="sxs-lookup"><span data-stu-id="570d1-126">If constraint manager is set to manual mode, only constraints that are linked in the constraint list are processed and applied to the transform.</span></span> <span data-ttu-id="570d1-127">显示的列表将只显示用户选择的约束，以及转到用于删除或[](#go-to-component)添加条目的按钮或选项。</span><span class="sxs-lookup"><span data-stu-id="570d1-127">The list displayed will only show the user selected constraints as well as [go to buttons](#go-to-component) or options to remove or add entries.</span></span>
<span data-ttu-id="570d1-128">首次启用手动模式时，约束管理器将填充列表，所有可用组件都将作为选择附加约束组件的起点。</span><span class="sxs-lookup"><span data-stu-id="570d1-128">When enabling manual mode for the first time, constraint manager will populate the list will all available components as a starting point for selecting attached constraint components.</span></span>

### <a name="remove-entry"></a><span data-ttu-id="570d1-129">删除条目</span><span class="sxs-lookup"><span data-stu-id="570d1-129">Remove entry</span></span>

<span data-ttu-id="570d1-130">这会从手动选择的列表中删除该条目。</span><span class="sxs-lookup"><span data-stu-id="570d1-130">This removes the entry from the manually selected list.</span></span> <span data-ttu-id="570d1-131">请注意，此选项不会从游戏对象中删除约束组件。</span><span class="sxs-lookup"><span data-stu-id="570d1-131">Note that this option will not remove the constraint component from the game object.</span></span> <span data-ttu-id="570d1-132">始终需要手动删除约束组件，以确保不会意外中断引用此组件的其他组件。</span><span class="sxs-lookup"><span data-stu-id="570d1-132">Constraint components always need to be removed manually to ensure not accidentally breaking any other component referring to this component.</span></span>

### <a name="add-entry"></a><span data-ttu-id="570d1-133">添加条目</span><span class="sxs-lookup"><span data-stu-id="570d1-133">Add entry</span></span>

<span data-ttu-id="570d1-134">"添加项"将打开一个下拉列表，其中显示尚未在手动列表中的所有可用约束组件。</span><span class="sxs-lookup"><span data-stu-id="570d1-134">Add entry will open a dropdown showing all available constraint components that are not in the manual list yet.</span></span> <span data-ttu-id="570d1-135">通过单击组件将添加到手动约束选择的任何条目。</span><span class="sxs-lookup"><span data-stu-id="570d1-135">By clicking on any of the entries that component will be added to the manual constraint selection.</span></span>

### <a name="add-new-constraint"></a><span data-ttu-id="570d1-136">添加新约束</span><span class="sxs-lookup"><span data-stu-id="570d1-136">Add new constraint</span></span>

<span data-ttu-id="570d1-137">此选项将所选类型的组件添加到游戏对象，并且将新创建的约束组件添加到手动约束列表中。</span><span class="sxs-lookup"><span data-stu-id="570d1-137">This option will add a component of the selected type to the game object and add the newly created constraint component to the manual constraint list.</span></span>

## <a name="transform-constraints"></a><span data-ttu-id="570d1-138">转换约束</span><span class="sxs-lookup"><span data-stu-id="570d1-138">Transform constraints</span></span>

<span data-ttu-id="570d1-139">约束可用于以某种方式限制操作。</span><span class="sxs-lookup"><span data-stu-id="570d1-139">Constraints can be used to limit manipulation in some way.</span></span> <span data-ttu-id="570d1-140">例如，某些应用程序可能需要旋转，但也要求对象保持垂直。</span><span class="sxs-lookup"><span data-stu-id="570d1-140">For example, some applications may require rotation, but also require that the object remain upright.</span></span> <span data-ttu-id="570d1-141">在这种情况下，可以将 添加到 对象，并用于将旋转限制为 `RotationAxisConstraint` y 轴旋转。</span><span class="sxs-lookup"><span data-stu-id="570d1-141">In this case, a `RotationAxisConstraint` can be added to the object and used to limit rotation to y-axis rotation.</span></span> <span data-ttu-id="570d1-142">MRTK 提供了许多约束，所有这些约束如下所述。</span><span class="sxs-lookup"><span data-stu-id="570d1-142">MRTK provides a number of constraints, all of which are described below.</span></span>

<span data-ttu-id="570d1-143">还可以定义新约束，并使用它们创建某些应用程序可能需要的唯一操作行为。</span><span class="sxs-lookup"><span data-stu-id="570d1-143">It is also possible to define new constraints and use them to create unique manipulation behaviour that may be needed for some applications.</span></span> <span data-ttu-id="570d1-144">为此，请创建一个继承自 的脚本 [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) ，并实现抽象 `ConstraintType` 属性和抽象 `ApplyConstraint` 方法。</span><span class="sxs-lookup"><span data-stu-id="570d1-144">To do this, create a script that inherits from [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) and implement the abstract `ConstraintType` property and the abstract `ApplyConstraint` method.</span></span> <span data-ttu-id="570d1-145">向 对象添加新约束后，它应按定义的方式约束操作。</span><span class="sxs-lookup"><span data-stu-id="570d1-145">Upon adding a new constraint to the object, it should constrain manipulation in the way that was defined.</span></span> <span data-ttu-id="570d1-146">此新约束还应显示在约束管理器自动[选择中，](#auto-constraint-selection)[或在手动](#add-entry)模式下添加条目下拉列表。</span><span class="sxs-lookup"><span data-stu-id="570d1-146">This new constraint should also show in the constraint manager [auto selection](#auto-constraint-selection) or [add entry](#add-entry) dropdown in manual mode.</span></span>

<span data-ttu-id="570d1-147">MRTK 提供的所有约束共享以下属性：</span><span class="sxs-lookup"><span data-stu-id="570d1-147">All of the constraints provided by MRTK share the following properties:</span></span>

#### <a name="hand-type"></a><span data-ttu-id="570d1-148">手类型</span><span class="sxs-lookup"><span data-stu-id="570d1-148">Hand Type</span></span>

<span data-ttu-id="570d1-149">指定约束是用于一手、两手还是两种操作。</span><span class="sxs-lookup"><span data-stu-id="570d1-149">Specifies whether the constraint is used for one handed, two handed or both kinds of manipulation.</span></span> <span data-ttu-id="570d1-150">由于此属性是一个标志，因此可以选中这两个选项。</span><span class="sxs-lookup"><span data-stu-id="570d1-150">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="570d1-151">*一手*：如果选中，将在一手操作期间使用约束。</span><span class="sxs-lookup"><span data-stu-id="570d1-151">*One handed*: Constraint will be used during one handed manipulation if selected.</span></span>
- <span data-ttu-id="570d1-152">*两手*：如果选中，将在两次手部操作期间使用约束。</span><span class="sxs-lookup"><span data-stu-id="570d1-152">*Two handed*: Constraint will be used during two handed manipulation if selected.</span></span>

#### <a name="proximity-type"></a><span data-ttu-id="570d1-153">邻近类型</span><span class="sxs-lookup"><span data-stu-id="570d1-153">Proximity Type</span></span>

<span data-ttu-id="570d1-154">指定约束是用于近、远或两种操作。</span><span class="sxs-lookup"><span data-stu-id="570d1-154">Specifies whether the constraint is used for near, far or both kinds of manipulation.</span></span> <span data-ttu-id="570d1-155">由于此属性是一个标志，因此可以选中这两个选项。</span><span class="sxs-lookup"><span data-stu-id="570d1-155">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="570d1-156">*Near*：如果选中，将在近操作期间使用约束。</span><span class="sxs-lookup"><span data-stu-id="570d1-156">*Near*: Constraint will be used during near manipulation if selected.</span></span>
- <span data-ttu-id="570d1-157">*远*：如果选中，将在远操作期间使用约束。</span><span class="sxs-lookup"><span data-stu-id="570d1-157">*Far*: Constraint will be used during far manipulation if selected.</span></span>

### <a name="faceuserconstraint"></a><span data-ttu-id="570d1-158">FaceUserConstraint</span><span class="sxs-lookup"><span data-stu-id="570d1-158">FaceUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

<span data-ttu-id="570d1-159">当此约束附加到对象时，旋转将受到限制，以便对象始终面向用户。</span><span class="sxs-lookup"><span data-stu-id="570d1-159">When this constraint is attached to an object, rotation will be limited so that object will always face the user.</span></span> <span data-ttu-id="570d1-160">这适用于板或面板。</span><span class="sxs-lookup"><span data-stu-id="570d1-160">This is useful for slates or panels.</span></span> <span data-ttu-id="570d1-161">的属性 `FaceUserConstraint` 如下所示：</span><span class="sxs-lookup"><span data-stu-id="570d1-161">The properties for `FaceUserConstraint` are as follows:</span></span>

#### <a name="face-away"></a><span data-ttu-id="570d1-162">人脸离开</span><span class="sxs-lookup"><span data-stu-id="570d1-162">Face away</span></span>

<span data-ttu-id="570d1-163">如果为 true，则对象与用户远离。</span><span class="sxs-lookup"><span data-stu-id="570d1-163">Object faces away from the user if true.</span></span>

### <a name="fixeddistanceconstraint"></a><span data-ttu-id="570d1-164">FixedDistanceConstraint</span><span class="sxs-lookup"><span data-stu-id="570d1-164">FixedDistanceConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

<span data-ttu-id="570d1-165">此约束修复了操作开始时被操作的对象与另一个对象转换之间的距离。</span><span class="sxs-lookup"><span data-stu-id="570d1-165">This constraint fixes the distance between the manipulated object and another object transform on manipulation start.</span></span> <span data-ttu-id="570d1-166">这适用于诸如修复从操作对象到头部转换的距离等行为。</span><span class="sxs-lookup"><span data-stu-id="570d1-166">This is useful for behaviour such as fixing the distance from the manipulated object to the head transform.</span></span> <span data-ttu-id="570d1-167">的属性 `FixedDistanceConstraint` 如下所示：</span><span class="sxs-lookup"><span data-stu-id="570d1-167">The properties for `FixedDistanceConstraint` are as follows:</span></span>

#### <a name="constraint-transform"></a><span data-ttu-id="570d1-168">约束转换</span><span class="sxs-lookup"><span data-stu-id="570d1-168">Constraint transform</span></span>

<span data-ttu-id="570d1-169">这是被操作的对象将具有固定距离的另一个转换。</span><span class="sxs-lookup"><span data-stu-id="570d1-169">This is the other transform that the manipulated object will have a fixed distance to.</span></span> <span data-ttu-id="570d1-170">默认为相机转换。</span><span class="sxs-lookup"><span data-stu-id="570d1-170">Defaults to the camera transform.</span></span>

### <a name="fixedrotationtouserconstraint"></a><span data-ttu-id="570d1-171">FixedRotationToUserConstraint</span><span class="sxs-lookup"><span data-stu-id="570d1-171">FixedRotationToUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

<span data-ttu-id="570d1-172">此约束修复了操作用户和被操作对象之间的相对旋转。</span><span class="sxs-lookup"><span data-stu-id="570d1-172">This constraint fixes the relative rotation between the user and the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="570d1-173">这适用于板或面板，因为它可确保操作对象始终向用户显示与操作开始时相同的人脸。</span><span class="sxs-lookup"><span data-stu-id="570d1-173">This is useful for slates or panels as it ensures that the manipulated object always shows the same face to the user as it did at the start of manipulation.</span></span> <span data-ttu-id="570d1-174">`FixedRotationToUserConstraint`没有任何唯一属性。</span><span class="sxs-lookup"><span data-stu-id="570d1-174">The `FixedRotationToUserConstraint` does not have any unique properties.</span></span>

### <a name="fixedrotationtoworldconstraint"></a><span data-ttu-id="570d1-175">FixedRotationToWorldConstraint</span><span class="sxs-lookup"><span data-stu-id="570d1-175">FixedRotationToWorldConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

<span data-ttu-id="570d1-176">此约束修复了被操作对象的全局旋转。</span><span class="sxs-lookup"><span data-stu-id="570d1-176">This constraint fixes the global rotation of the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="570d1-177">当不应通过操作来设置旋转时，这非常有用。</span><span class="sxs-lookup"><span data-stu-id="570d1-177">This can be useful in cases where no rotation should be imparted by manipulation.</span></span> <span data-ttu-id="570d1-178">`FixedRotationToWorldConstraint`没有任何唯一属性：</span><span class="sxs-lookup"><span data-stu-id="570d1-178">The `FixedRotationToWorldConstraint` does not have any unique properties:</span></span>

### <a name="maintainapparentsizeconstraint"></a><span data-ttu-id="570d1-179">MaintainApparentSizeConstraint</span><span class="sxs-lookup"><span data-stu-id="570d1-179">MaintainApparentSizeConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

<span data-ttu-id="570d1-180">当此约束附加到对象时，无论对象与用户有多远，它都将保持与用户相同的明显大小 (即，它将占用户视场的相同比例) 。</span><span class="sxs-lookup"><span data-stu-id="570d1-180">When this constraint is attached to an object, no matter how far the object is from the user, it will maintain the same apparent size to the user (i.e. it will take up the same proportion of the user's field of view).</span></span> <span data-ttu-id="570d1-181">这可用于确保平板电脑或文本面板在操作时保持可读。</span><span class="sxs-lookup"><span data-stu-id="570d1-181">This can be used to ensure that a slate or text panel remains readable while manipulating.</span></span> <span data-ttu-id="570d1-182">`MaintainApparentSizeConstraint`没有任何唯一属性：</span><span class="sxs-lookup"><span data-stu-id="570d1-182">The `MaintainApparentSizeConstraint` does not have any unique properties:</span></span>

### <a name="moveaxisconstraint"></a><span data-ttu-id="570d1-183">MoveAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="570d1-183">MoveAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

<span data-ttu-id="570d1-184">此约束可用于修复可沿其移动被操作对象的轴。</span><span class="sxs-lookup"><span data-stu-id="570d1-184">This constraint can be used to fix along which axes a manipulated object can be moved.</span></span> <span data-ttu-id="570d1-185">这可用于在平面图面上或沿直线操作对象。</span><span class="sxs-lookup"><span data-stu-id="570d1-185">This can be useful for manipulating objects over the surface of a plane, or along a line.</span></span> <span data-ttu-id="570d1-186">的属性 `MoveAxisConstraint` 如下所示：</span><span class="sxs-lookup"><span data-stu-id="570d1-186">The properties for `MoveAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-movement"></a><span data-ttu-id="570d1-187">移动约束</span><span class="sxs-lookup"><span data-stu-id="570d1-187">Constraint on movement</span></span>

<span data-ttu-id="570d1-188">指定要阻止移动的轴。</span><span class="sxs-lookup"><span data-stu-id="570d1-188">Specifies which axes to prevent movement on.</span></span> <span data-ttu-id="570d1-189">默认情况下，这些轴是全局轴，而不是本地轴，但可以在下方进行更改。</span><span class="sxs-lookup"><span data-stu-id="570d1-189">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="570d1-190">由于此属性是标志，因此可以选择任意数目的选项。</span><span class="sxs-lookup"><span data-stu-id="570d1-190">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="570d1-191">*X 轴*：如果选中，则沿 x 轴的移动受到限制。</span><span class="sxs-lookup"><span data-stu-id="570d1-191">*X Axis*: Movement along the x-axis is constrained if selected.</span></span>
- <span data-ttu-id="570d1-192">*Y 轴*：如果选中，则沿 y 轴的移动受到限制。</span><span class="sxs-lookup"><span data-stu-id="570d1-192">*Y Axis*: Movement along the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="570d1-193">*Z 轴*：如果选中，则沿 z 轴的移动受到限制。</span><span class="sxs-lookup"><span data-stu-id="570d1-193">*Z Axis*: Movement along the z-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="570d1-194">使用本地空间进行约束</span><span class="sxs-lookup"><span data-stu-id="570d1-194">Use local space for constraint</span></span>

<span data-ttu-id="570d1-195">如果为 true，则约束被操作对象的局部转换轴的相对约束。</span><span class="sxs-lookup"><span data-stu-id="570d1-195">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="570d1-196">默认值为 False。</span><span class="sxs-lookup"><span data-stu-id="570d1-196">False by default.</span></span>

### <a name="rotationaxisconstraint"></a><span data-ttu-id="570d1-197">RotationAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="570d1-197">RotationAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

<span data-ttu-id="570d1-198">此约束可用于修复可旋转操作对象的轴。</span><span class="sxs-lookup"><span data-stu-id="570d1-198">This constraint can be used to fix about which axes a manipulated object can be rotated.</span></span> <span data-ttu-id="570d1-199">这可用于保持操控对象垂直，但仍允许 y 轴旋转，例如。</span><span class="sxs-lookup"><span data-stu-id="570d1-199">This can be useful for keeping a manipulated object upright, but still allowing y-axis rotations, for example.</span></span> <span data-ttu-id="570d1-200">的属性 `RotationAxisConstraint` 如下所示：</span><span class="sxs-lookup"><span data-stu-id="570d1-200">The properties for `RotationAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-rotation"></a><span data-ttu-id="570d1-201">旋转约束</span><span class="sxs-lookup"><span data-stu-id="570d1-201">Constraint on rotation</span></span>

<span data-ttu-id="570d1-202">指定阻止旋转的轴。</span><span class="sxs-lookup"><span data-stu-id="570d1-202">Specifies which axes to prevent rotation about.</span></span> <span data-ttu-id="570d1-203">默认情况下，这些轴是全局性的，而不是本地的，但可以在下面更改。</span><span class="sxs-lookup"><span data-stu-id="570d1-203">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="570d1-204">因为此属性是一个标志，所以可以选择任意数量的选项。</span><span class="sxs-lookup"><span data-stu-id="570d1-204">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="570d1-205">*Y 轴*：如果选中，则会约束围绕 Y 轴的旋转。</span><span class="sxs-lookup"><span data-stu-id="570d1-205">*Y Axis*: Rotation about the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="570d1-206">*Z 轴*：如果选中，则对 Z 轴进行旋转。</span><span class="sxs-lookup"><span data-stu-id="570d1-206">*Z Axis*: Rotation about the z-axis is constrained if selected.</span></span>
- <span data-ttu-id="570d1-207">*X 轴*：如果选中，则会约束围绕 X 轴的旋转。</span><span class="sxs-lookup"><span data-stu-id="570d1-207">*X Axis*: Rotation about the x-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="570d1-208">使用本地空间作为约束</span><span class="sxs-lookup"><span data-stu-id="570d1-208">Use local space for constraint</span></span>

<span data-ttu-id="570d1-209">如果为 true，则将限制操作对象的本地转换轴。</span><span class="sxs-lookup"><span data-stu-id="570d1-209">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="570d1-210">默认值为 False。</span><span class="sxs-lookup"><span data-stu-id="570d1-210">False by default.</span></span>

### <a name="minmaxscaleconstraint"></a><span data-ttu-id="570d1-211">MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="570d1-211">MinMaxScaleConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

<span data-ttu-id="570d1-212">此约束允许为操作对象的小数位数设置最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="570d1-212">This constraint allows minimum and maximum values to be set for the scale of the manipulated object.</span></span> <span data-ttu-id="570d1-213">这对于防止用户缩放对象太小或太大非常有用。</span><span class="sxs-lookup"><span data-stu-id="570d1-213">This is useful for preventing users from scaling an object too small or too large.</span></span> <span data-ttu-id="570d1-214">的属性如下所示 `MinMaxScaleConstraint` ：</span><span class="sxs-lookup"><span data-stu-id="570d1-214">The properties for `MinMaxScaleConstraint` are as follows:</span></span>

#### <a name="scale-minimum"></a><span data-ttu-id="570d1-215">最小缩放</span><span class="sxs-lookup"><span data-stu-id="570d1-215">Scale minimum</span></span>

<span data-ttu-id="570d1-216">操作过程中的最小刻度值。</span><span class="sxs-lookup"><span data-stu-id="570d1-216">The minimum scale value during manipulation.</span></span>

#### <a name="scale-maximum"></a><span data-ttu-id="570d1-217">最大缩放</span><span class="sxs-lookup"><span data-stu-id="570d1-217">Scale maximum</span></span>

<span data-ttu-id="570d1-218">操作过程中的最大刻度值。</span><span class="sxs-lookup"><span data-stu-id="570d1-218">The maximum scale value during manipulation.</span></span>

#### <a name="relative-to-initial-state"></a><span data-ttu-id="570d1-219">相对于初始状态</span><span class="sxs-lookup"><span data-stu-id="570d1-219">Relative to initial state</span></span>

<span data-ttu-id="570d1-220">如果为 true，则上述值将被解释为相对于对象初始刻度。</span><span class="sxs-lookup"><span data-stu-id="570d1-220">If true, the values above will be interpreted as relative to the objects initial scale.</span></span> <span data-ttu-id="570d1-221">否则，它们将被解释为绝对缩放值。</span><span class="sxs-lookup"><span data-stu-id="570d1-221">Otherwise they will be interpreted as absolute scale values.</span></span>
