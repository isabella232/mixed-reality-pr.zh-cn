---
title: 手动菜单
description: MRTK 中的手动菜单示例场景
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， HandMenu，
ms.openlocfilehash: ecf05b687c52dab68302b9b66b3890aca31b5635b803084abd6845f31de974e0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226457"
---
# <a name="hand-menu"></a>手动菜单

![手部菜单 UX 示例](../images/solver/MRTK_UX_HandMenu.png)

手部菜单允许用户为常用函数快速启动手动附加的 UI。 为了防止与其他对象交互时出现误报，手部菜单提供了"需要平手"和"使用凝视激活"等选项。 建议使用这些选项来防止不需要的激活。

## <a name="hand-menu-examples"></a>手部菜单示例

**HandMenuExamples.unity** 场景位于 ``MRTK/Examples/Demos/HandTracking/Scenes`` 文件夹下。 当场景运行时，场景将仅激活当前选定的菜单类型。
<br/><img src="../images/hand-menu/MRTK_HandMenu_ExampleScene.png" width="600px" alt="HandMenu_ExampleScene">

可以在文件夹下找到这些手部菜单 ``MRTK/Examples/Demos/HandTracking/Prefabs`` 预制项。

### <a name="handmenu_small_hideonhanddrop-and-handmenu_medium_hideonhanddrop"></a>HandMenu_Small_HideOnHandDrop 和 HandMenu_Medium_HideOnHandDrop

这两个示例只需激活和停用 MenuContent 对象即可在 **OnFirstHandDetected** () **和 OnLastHandLost () 事件上显示和隐藏** 菜单。
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example1.png" width="600" alt="HandMenu_ExampleScene 1">
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example2.png" width="600" alt="HandMenu_ExampleScene 2">

### <a name="handmenu_large_worldlock_on_grabandpull"></a>HandMenu_Large_WorldLock_On_GrabAndPull

对于需要较长交互时间的复杂菜单，建议对菜单进行世界锁定。 此示例中，除了激活和停用 **OnFirstHandDetected ()** 和 **OnLastHandLost** () 事件上的 MenuContent 外，用户还可以抓取并拉取到世界锁定菜单。
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example3.png" width="600" alt="HandMenu_ExampleScene 3">

反板使其 `ManipulationHandler` 可抓取且可移动。 **在操作启动** 事件上 **，将停用 SolverHandler.UpdateSolvers** 以对菜单进行世界锁定。 此外，它还显示 **"关闭** "按钮，允许用户在任务完成后关闭菜单。 **在"操作** 结束"事件上，它调用 **HandConstraintPalmUp.StartWorldLockReattachCheckCoroutine，** 允许用户通过引发并查看手部使菜单恢复为手。
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example4.png" width="600" alt="HandMenu_ExampleScene 4">

**"关闭** "按钮重新激活 **SolverHandler.UpdateSolvers** 并隐藏 **MenuContent**。
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example5.png" alt="HandMenu_ExampleScene 5">

### <a name="handmenu_large_autoworldlock_on_handdrop"></a>HandMenu_Large_AutoWorldLock_On_HandDrop

此示例类似于 HandMenu_Large_WorldLock_On_GrabAndPull。 唯一的区别是菜单将自动进行手动锁定。 完成此操作时，只需不隐藏 **OnLastHandLost** 上的 MenuContent () 事件。 抓取&行为与示例HandMenu_Large_WorldLock_On_GrabAndPull相同。

## <a name="scripts"></a>脚本

[`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 行为提供了一个求解器，该求解器将跟踪对象约束在确保可显示手部约束内容（如手部 UI、菜单等）的区域内。 安全区域是指不会与手部相交的区域。 还包含了一个名为 [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) 的 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 派生类，用于演示手掌朝向用户时激活求解器的常见行为。

有关其他文档，请参阅每个 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 属性可用的工具提示。 下面更详细地定义了几个属性。

<img src="../images/solver/MRTK_Solver_HandConstraintPalmUp.png" width="450" alt="HandMenu_ExampleScene Palm up">

* **保险箱区域**：安全区域指定要约束内容的手动位置。 建议将内容放置在 Ulnar 端，以避免与手重叠并提高交互质量。 保险箱区域的计算方式为：将手部方向与相机视图正交到平面中，并针对手周围的边界框进行光线广播。 保险箱区域定义为使用 ， [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) 但也适用于其他控制器类型。 建议浏览每个安全区域在不同控制器类型上表示什么。

* **跟随手部直到面向摄像头** 在此活动状态下，求解器将跟随手部旋转，直到菜单与凝视完全对齐，此时它面向照相机。 此操作的工作原理是，将 HandConstraintSolver 中的 SolverRotationBehavior 从 LookAtTrackedObject 更改为 LookAtMainCamera，因为求解器的 GazeAlignment 角度会有所不同。

<img src="../images/solver/MRTK_Solver_HandConstraintSafeZones.png" width="450" alt="HandMenu Safe Zones">

* **激活事件**：当前 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 触发四个激活事件。 这些事件可用于许多不同的组合来创建唯一行为，有关这些行为的示例，请参阅 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 下的 HandBasedMenuExample `MRTK/Examples/Demos/HandTracking/Scenes/` 场景。

  * *OnHandActivate：* 当手满足 IsHandActive 方法时触发。
  * *OnHandDeactivate：* 当不再满足 IsHandActive 方法时触发。
  * *OnFirstHandDetected*：当手部跟踪状态从"没有手部"视图更改到"第一手"视图时发生。
  * *OnLastHandLost：* 当手部跟踪状态从视图中的至少一只手更改到没有手部时发生。

* **求解** 器激活/停用逻辑：目前，激活和停用逻辑的建议是通过使用 SolverHandler 的 UpdateSolver 值（而不是通过禁用/启用对象）来这样做。 [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) 可通过附加菜单的 ManipulationHandler"OnManipulationStarted/Ended"事件后触发的基于编辑器的挂钩在示例场景中看到此情况。

  * 停止手部约束逻辑：尝试将手部约束对象设置为停止 (以及不运行激活/停用逻辑) 时，将 UpdateSolver 设置为 False，而不是禁用 HandConstraintPalmUp。
    * 如果要启用基于凝视的 (甚至非基于凝视的) 重新附加逻辑，则随后调用 HandConstraintPalmUp.StartWorldLockReattachCheckCoroutine () 函数。 这将触发协同例程，然后继续检查是否满足"IsValidController"条件，并且将在 UpdateSolver 设置为 True 后 (或对象被禁用) 
  * 启动手部约束逻辑：尝试将手部约束对象设置为根据 (是否满足激活条件) 再次开始跟踪手部约束对象时，将 SolverHandler 的 UpdateSolver 设置为 true。

* **重新附加逻辑**：目前， 能够自动将目标对象重新附加到跟踪点，无论 [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) SolverHandler 的 UpdateSolver 是否为 True。 这是通过调用 HandConstraintPalmUp 的 StartWorldLockReattachCheckCoroutine () 函数（在此例中为 (实际上将 SolverHandler 的 UpdateSolver 设置为 False) ）完成此操作。

## <a name="see-also"></a>另请参阅

* [Button](button.md)
* [近菜单](near-menu.md)
