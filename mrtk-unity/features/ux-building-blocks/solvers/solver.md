---
title: 求解器概述
description: MRTK 中的求解器概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity,HoloLens, HoloLens 2, 混合现实, 开发, MRTK, 求解器,
ms.openlocfilehash: bf9bbfe578ace576fca8870f038f145037a6838d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176453"
---
# <a name="solver-overview"></a>求解器概述

![求解器主要内容](../../images/solver/MRTK_Solver_Main.png)

求解器是有助于根据预定义算法计算对象位置和方向的组件。 例如，将对象放置在用户当前注视视线直达的表面上。

此外，求解器系统确定性地定义这些转换计算的运算顺序，因为没有可靠的方法向 Unity 指定组件的更新顺序。

求解器提供一系列行为，以将对象附加到其他对象或系统。 另一个示例是一个尾随对象，该对象悬停在用户前面（基于摄像机）。 求解器还可以附加到控制器和对象，使对象尾随控制器。 所有求解器都可以安全地堆叠，例如尾随行为 + 表面磁性 + 动量。

## <a name="how-to-use-a-solver"></a>如何使用求解器

求解器系统由三类脚本组成：

* [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver)：基本抽象类，用于派生所有求解器。 它提供状态跟踪、平滑参数和实现、自动求解器系统集成和更新顺序。
* [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler)：设置跟踪所参照的对象（例如：主摄像头转换、手部射线等），处理求解器组件收集以及按正确顺序执行更新。

第三个类别是求解器本身。 以下求解器提供基本行为的构建基块：

* [`Orbital`](#orbital)：锁定到指定位置并偏离参照对象。
* [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize)：缩放以保持相对于参照对象视图不变的大小。
* [`RadialView`](#radialview)：使对象保持在参照对象的视锥投射范围内。
* [`Follow`](#follow)：使对象保持在参照对象的一组用户定义边界内。
* [`InBetween`](#inbetween)：使对象保持在两个跟踪对象之间。
* [`SurfaceMagnetism`](#surfacemagnetism)：将射线投射到世界中的表面上，并使对象对齐到该表面。
* [`DirectionalIndicator`](#directionalindicator)：确定作为方向指示器的对象的位置和方向。 从 SolverHandler 跟踪目标的参照点来看，此指示器将面向提供的 DirectionalTarget。
* [`Momentum`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Momentum)：应用加速/速度/摩擦来模拟由其他求解器/组件移动的对象的动量和弹性。
* [`HandConstraint`](#hand-menu-with-handconstraint-and-handconstraintpalmup)：约束对象，使其在 GameObject 不会与手部交叉的区域跟随手部。 对手部约束的交互式内容很有用，如菜单等。此求解器旨在与 [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) 一起使用，但也可以与 [IMixedRealityController](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController) 一起使用。
* [`HandConstraintPalmUp`](#hand-menu-with-handconstraint-and-handconstraintpalmup)：派生自 HandConstraint，但包含用于测试手部在激活前是否手掌面向用户的逻辑。 此求解器只能与 [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) 控制器一起使用，如果与其他控制器类型一起使用，此求解器的行为类似于基类。

要使用求解器系统，只需将上面所列任一组件添加到 GameObject 即可。 由于所有求解器都需要 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler)，因此 Unity 会自动创建一个。

> [!NOTE]
> SolverExamples.scene 文件中介绍了如何使用求解器系统的示例。

## <a name="how-to-change-tracking-reference"></a>如何更改跟踪参照

[`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) 组件的“跟踪目标类型”属性定义所有求解器将用来计算其算法的参照点。 例如，具有简单 [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) 组件的 [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) 值类型将产生从头部开始，沿着用户凝视方向发射出去的射线，用于求解射线到达的表面。 `TrackedTargetType` 属性的可能值包括：

* *Hea*：参照点是主摄像头的转换
* *ControllerRay*：参照点是控制器上的 [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer) 转换（即 运动控制器或手部控制器上的指针原点），指向直线射线方向
  * 使用 `TrackedHandedness` 属性选择惯用手偏好（即 左、右、均可）
* *HandJoint*：参照点是特定手部关节的转换
  * 使用 `TrackedHandedness` 属性选择惯用手偏好（即 左、右、均可）
  * 使用 `TrackedHandJoint` 属性确定要利用的关节转换
* *CustomOverride*：参照点来自于已分配的 `TransformOverride`

> [!NOTE]
> 对于 ControllerRay 和 HandJoint 类型，求解器处理程序将先尝试提供左侧控制器/手部转换，然后在前者不可用时提供右侧转换，或者除非 `TrackedHandedness` 属性另有指定。

![求解器跟踪的对象](../../images/solver/TrackedObjectType-Example.gif) 
与每个 TrackedTargetType 关联的各种属性的示例

> [!IMPORTANT]
> 大多数求解器使用 `SolverHandler` 提供的跟踪转换目标的前向向量。 使用“手部关节”跟踪目标类型时，手掌关节的前向向量可能会穿过手指，而非手掌。 这取决于提供手部关节数据的平台。 对于输入模拟和 Windows Mixed Reality，穿过手掌指向上方的是“向上向量”（即 绿色向量向上，蓝色向量向前）。
>
> ![前向向上向量](../../images/solver/HandJoint_ForwardUpVectors.png)
>
> 若要克服这个问题，可以将 `SolverHandler` 上的“其他旋转”属性更新为 <90, 0, 0>。 这将确保提供给求解器的前向向量穿过手掌，从手部向外指出去。
>
> ![其他旋转](../../images/solver/SolverHandler_AdditionalRotation.png)
>
> 或者，使用“控制器射线”跟踪目标类型获取与手部指向相似的行为。

## <a name="how-to-chain-solvers"></a>如何链接求解器

您可以将多个 `Solver` 组件添加到同一 GameObject 来链接算法。 `SolverHandler` 组件负责更新同一 GameObject 上的所有求解器。 默认情况下，`SolverHandler` 会在 Start 上调用 `GetComponents<Solver>()`，从而按求解器在检查器中显示的顺序返回求解器。

此外，将"更新的链接转换"属性设置为 true，会指示 `Solver` 将其计算的位置、方向和缩放保存到所有求解器都可以访问的中间变量（即 `GoalPosition`). 如果为 false，`Solver` 将直接更新 GameObject 的转换。 通过将转换属性保存至中间位置，其他求解器能够从中间变量开始执行其计算。 这是因为 Unity 不允许对 gameObject.transform 的更新在同一帧中堆叠。

> [!NOTE]
> 开发人员可以通过直接设置 `SolverHandler.Solvers` 属性来修改求解器的执行顺序。

## <a name="how-to-create-a-new-solver"></a>如何创建新的求解器

所有求解器都必须继承自抽象基类 [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver)。 求解器扩展的主要要求涉及重写 `SolverUpdate` 方法。 在此方法中，开发人员应将继承的 `GoalPosition`、`GoalRotation` 和 `GoalScale` 属性更新为所需值。 此外，将 `SolverHandler.TransformTarget` 用作使用者所需的参照帧通常十分有益。

下面提供的代码提供了名为 `InFront` 的新求解器组件的示例，该组件将附加对象放在 `SolverHandler.TransformTarget` 前面 2 米处。 如果使用者将 `SolverHandler.TrackedTargetType` 设置为 [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head)，则 `SolverHandler.TransformTarget` 将是相机转换，因此该求解器会在每一帧将附加的 GameObject 放在用户凝视的前面的 2 米处。

```c#
/// <summary>
/// InFront solver positions an object 2m in front of the tracked transform target
/// </summary>
public class InFront : Solver
{
    ...

    public override void SolverUpdate()
    {
        if (SolverHandler != null && SolverHandler.TransformTarget != null)
        {
            var target = SolverHandler.TransformTarget;
            GoalPosition = target.position + target.forward * 2.0f;
        }
    }
}
```

## <a name="solver-implementation-guides"></a>求解器实现指南

### <a name="common-solver-properties"></a>常见求解器属性

每个求解器组件都有一组核心属性，这些属性是相同的，用于控制求解器行为。

如果启用了“平滑处理”，则求解器将随着时间的推移，将 GameObject 的转换逐渐更新为计算值。 此更改的速度取决于每个转换组件的“LerpTime”属性。 例如，MoveLerpTime 值越高，帧之间的移动增量就会越慢。

如果启用了 MaintainScale，求解器将利用 GameObject 的默认本地缩放。

![核心求解器属性](../../images/solver/GeneralSolverProperties.png)  
*所有求解器组件都会继承的常见属性*

### <a name="orbital"></a>Orbital

[`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) 类是一个尾随组件，其行为类似于太阳系中的行星。 此求解器将确保附加的 GameObject 围绕着跟踪转换旋转。 因此，如果 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) 的“跟踪目标类型”设置为 [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head)，则 GameObject 将按照所应用的固定偏移量，围绕用户的头部旋转。

开发人员可以修改此固定偏移量，以使菜单或其他场景组件保持在眼睛或腰部的高度，围绕在用户周围。 这可以通过修改“本地偏移量”和“全局偏移量”属性完成。 “方向类型”属性确定应用于对象的旋转，例如，对象应始终保持原始旋转，或者总是面向摄像头，或者面向驱动其位置的转换，等等。

![Orbital 示例](../../images/solver/OrbitalExample.png)  
*Orbital 示例*

### <a name="radialview"></a>RadialView

[`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) 是另一个尾随组件，用于使 GameObject 的特定部分保持在用户视野的圆锥体内。

“最小和最大视场角度”属性决定了 GameObject 必须始终在视线范围内的部分的面积。

“最小和最大距离”属性决定了 GameObject 应该与用户保持多远距离。 例如，如果“最小距离”为 1 米，走向 GameObject 会将 GameObject 推开，以确保它永远不会距离用户短于 1 米。

通常，[`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) 会与设置为 [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) 的“跟踪目标类型”一起使用，这样组件就会跟随用户凝视。 但是，此组件可以发挥作用，以保持在任何跟踪目标类型的“视线”范围内。 

![RadialView 示例](../../images/solver/RadialViewExample.png)  
*RadialView 示例*

### <a name="follow"></a>关注

[`Follow`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Follow) 类将元素定位在跟踪目标的前面，相对于其局部前向轴。 该元素可以是松散约束型（又称 尾随），这样只有在跟踪目标移动到用户定义边界之外时才会跟随目标。

它的工作方式类似于 RadialView 求解器，但具有更多控制，可以管理“最大水平和垂直视场角度”，此外还有用于更改对象“方向”的机制。 

![Follow 属性](../../images/solver/FollowExample.png)  
*Follow 属性*

![Follow 示例场景](../../images/solver/FollowExampleScene.gif)  
*Follow 示例场景 (Assets/MRTK/Examples/Demos/Solvers/Scenes/FollowSolverExample.unity)*

### <a name="inbetween"></a>InBetween

[`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) 类使附加的 GameObject 保持在两个转换之间。 这两个转换终结点由 GameObject 自己的 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler)"跟踪目标类型"和 [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) 组件的“第二个跟踪目标类型”属性定义。  通常，这两个类型都将设置为 [`CustomOverride`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.CustomOverride)，产生的 `SolverHandler.TransformOverride` 和 `InBetween.SecondTransformOverride` 值将设置为两个跟踪的终结点。

在运行时，[`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) 组件将基于“第二个跟踪目标类型”和“第二个转换覆盖”属性再创建一个 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) 组件。 

`PartwayOffset` 定义应在直线上两个转换之间的哪个位置放置对象，0.5 表示中间，1.0 表示第一个转换，0.0 表示第二个转换。

![InBetween 示例](../../images/solver/InBetweenExample.png)  
*使用 InBetween 求解器使对象保持在两个转换之间的示例*

### <a name="surfacemagnetism"></a>SurfaceMagnetism

[`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) 的工作方式是对一组表面的 LayerMask 执行光线投射，并将 GameObject 放置在接触点。

“表面垂直偏移”按照设定好的距离表面的距离（米），沿着表面上击中点处的法线方向放置 GameObject。

相反，“表面射线偏移”按照设定好的距离表面的距离（米），沿着所执行光线投射的相反方向放置 GameObject。 因此，如果光线投射是用户凝视的方向，则 GameObject 将沿直线从表面上的击中点向摄像头靠近。

“方向模式”确定相对于表面上的法线应用的旋转类型。

* 无 - 不应用旋转
* 跟踪目标 - 对象将面向驱动光线投射的跟踪转换
* 表面法线 - 对象将基于表面上的击中点对齐
* 混合 - 对象将基于表面上的击中点对齐，并且面向跟踪转换。

要强制关联的 GameObject 在除“无”以外的任何模式下都保持垂直，请启用“使方向保持垂直”。

> [!NOTE]
> 当“方向模式”设置为“混合”时，使用“方向混合”属性控制旋转因子之间的平衡。   如果值为 0.0，则方向完全由“跟踪目标”模式驱动，值为 1.0 时，方向完全由“表面法线”驱动。 

![SurfaceMagnetism 示例](../../images/solver/SurfaceMagExample.png)

#### <a name="determining-what-surfaces-can-be-hit"></a>确定可以击中的表面

将 [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) 组件添加到 GameObject 时，必须考虑 GameObject 及其子代的层（如果任何子代有碰撞器）。 该组件的工作方式是执行各种类型的光线投射，以确定哪些表面可以“吸附”光线。 如果求解器 GameObject 在 `SurfaceMagnetism` 的 `MagneticSurfaces` 属性所列的其中一个层上有碰撞器，那么光线投射很可能会击中自己，导致 GameObject 附加到其自己的碰撞器点。 这种异常行为是可以避免的，方法是将主 GameObject 和所有子代设置为“忽略光线投射”层或相应地修改 `MagneticSurfaces` LayerMask 数组。

相反，[`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) GameObject 不会与 `MagneticSurfaces` 属性中未列出的层上的表面发生碰撞。 通常建议将所有所需表面放在专用层上（即 “表面”），并将 `MagneticSurfaces` 属性仅设置为这个层。  使用“默认”或“全部”可能会导致 UI 组件或光标影响求解器。 

最后，`SurfaceMagnetism` 光线投射将忽略 `MaxRaycastDistance` 属性设置，而不是表面。

### <a name="directionalindicator"></a>DirectionalIndicator

[`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator) 类是一个尾随组件，它可以根据空间中指定点的方向调整自身方向。

最常用于 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) 的“跟踪目标类型”设置为 [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) 的情况。 这样，具有 [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator) 求解器的 UX 组件将指引用户看空间中的指定点。

空间中的指定点通过“方向目标”属性确定。

如果用户可以查看方向目标，或在 [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) 中设置了任何参照帧，则该求解器将禁用它下面的所有 [`Renderer`](https://docs.unity3d.com/ScriptReference/Renderer.html) 组件。 如果不可查看，则该指示器上将启用所有内容。

随着用户逐渐靠近以在他们的 FOV 中捕捉“方向目标”，指示器的大小将缩小。

* 最小指示器比例 - 指示器对象的最小比例
* 最大指示器比例 - 指示器对象的最大比例

* 可见性比例因子 - 用于增加或减少 FOV 的乘数，用于确定“方向目标”点是否可见
* 视线偏移 - 从参照帧的视角（即， 很有可能是摄像头），此属性定义对象在指示器方向距离视角中心多远的位置处。

![DirectionalIndicator 属性](../../images/solver/DirectionalIndicatorExample.png)  
*DirectionalIndicator 属性*

![DirectionalIndicator 示例场景](../../images/solver/DirectionalIndicatorExampleScene.gif)  
*DirectionalIndicator 示例场景 (Assets/MRTK/Examples/Demos/Solvers/Scenes/DirectionalIndicatorSolverExample.unity)*

### <a name="hand-menu-with-handconstraint-and-handconstraintpalmup"></a>带有 HandConstraint 和 HandConstraintPalmUp 的手部菜单

![手部菜单 UX 示例](../../images/solver/MRTK_UX_HandMenu.png)

[`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 行为提供了一个求解器，该求解器将跟踪对象约束在确保可显示手部约束内容（如手部 UI、菜单等）的区域内。 安全区域是指不会与手部相交的区域。 还包含了一个名为 [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) 的 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 派生类，用于演示手掌朝向用户时激活求解器的常见行为。

[另请参阅“手部菜单”页面](../hand-menu.md)，了解使用手部约束求解器创建手部菜单的示例。

## <a name="see-also"></a>另请参阅

* [手部跟踪](../../input/hand-tracking.md)
* [凝视](../../input/gaze.md)
