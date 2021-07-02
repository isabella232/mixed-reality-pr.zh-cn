---
title: 手动菜单
description: MRTK 中的手形菜单示例场景
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，HandMenu，
ms.openlocfilehash: 9bb0276c048912b4f463dd93d3303c9a3af8fe29
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177527"
---
# <a name="hand-menu"></a>手动菜单

![手动菜单 UX 示例](../images/solver/MRTK_UX_HandMenu.png)

手动菜单允许用户快速为常用函数获取手动连接的 UI。 若要防止在与其他对象交互时出现错误激活，则可以使用 "上" 菜单提供 "需要平头" 和 "使用注视激活" 等选项。 建议使用这些选项以防止不必要的激活。

## <a name="hand-menu-examples"></a>手动菜单示例

**HandMenuExamples** 场景位于 ``MRTK/Examples/Demos/HandTracking/Scenes`` 文件夹下。 当它运行时，场景将仅激活当前选定的菜单类型。
<br/><img src="../images/hand-menu/MRTK_HandMenu_ExampleScene.png" width="600px" alt="HandMenu_ExampleScene">

可以在 "文件夹" 下找到 prototyping ``MRTK/Examples/Demos/HandTracking/Prefabs`` 。

### <a name="handmenu_small_hideonhanddrop-and-handmenu_medium_hideonhanddrop"></a>HandMenu_Small_HideOnHandDrop 和 HandMenu_Medium_HideOnHandDrop

这两个示例只是激活和停用 MenuContent 对象，以便显示和隐藏 **OnFirstHandDetected ()** 和 **OnLastHandLost ()** 事件上的菜单。
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example1.png" width="600" alt="HandMenu_ExampleScene 1">
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example2.png" width="600" alt="HandMenu_ExampleScene 2">

### <a name="handmenu_large_worldlock_on_grabandpull"></a>HandMenu_Large_WorldLock_On_GrabAndPull

对于需要较长时间交互时间的更复杂菜单，建议使用全局锁定菜单。 在此示例中，除了激活和停用 **OnFirstHandDetected ()** 和 **OnLastHandLost ()** 事件外，用户还可以获取并拉取到全局锁定菜单。
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example3.png" width="600" alt="HandMenu_ExampleScene 3">

Backplate `ManipulationHandler` 使其 grabbable 并可移动。 **在操作已启动时** ， **SolverHandler UpdateSolvers** 被停用，使其成为全局锁定菜单。 此外，它还会显示 " **关闭" 按钮** ，以允许用户在任务完成时关闭菜单。 **处理结束事件时** ，它会调用 **HandConstraintPalmUp** ，以允许用户通过引发和查看 palm 来返回菜单。
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example4.png" width="600" alt="HandMenu_ExampleScene 4">

"**关闭**" 按钮会重新激活 **SolverHandler UpdateSolvers** 并隐藏 **MenuContent**。
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example5.png" alt="HandMenu_ExampleScene 5">

### <a name="handmenu_large_autoworldlock_on_handdrop"></a>HandMenu_Large_AutoWorldLock_On_HandDrop

此示例类似于 HandMenu_Large_WorldLock_On_GrabAndPull。 唯一的区别是，菜单将自动放置时自动锁定。 只需隐藏 **OnLastHandLost ()** 事件上的 MenuContent 即可完成此操作。 抓取 & 拉取行为与 HandMenu_Large_WorldLock_On_GrabAndPull 示例相同。

## <a name="scripts"></a>脚本

此 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 行为提供了一个求解器，用于将跟踪的对象约束为适用于手写 (的区域，如手写用户 UI、菜单等) 。 保险箱区域被视为不与手相交的区域。 还包含一个名为的派生类， [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) 以演示当 palm 面向用户时激活规划求解跟踪对象的常见行为。

有关其他文档，请参阅可用于每个属性的工具提示 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 。 下面更详细地定义了几个属性。

<img src="../images/solver/MRTK_Solver_HandConstraintPalmUp.png" width="450" alt="HandMenu_ExampleScene Palm up">

* **保险箱区域**：安全区域指定对内容进行约束的位置。 建议将内容放在 Ulnar 端，以避免与手和改善交互质量重叠。 保险箱区域的计算方法是：将双手方向投影到与相机的视图相对应的平面中，并 raycasting。 保险箱区域定义为使用， [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) 但也适用于其他控制器类型。 建议你了解每个安全区域在不同控制器类型上代表的内容。

* **朝** 上的照相机在这种情况下，求解器将按照手型旋转，直至菜单与看起来充分对齐，此时它会给照相机旋转。 这可以通过将 HandConstraintSolver 中的 SolverRotationBehavior （从 LookAtTrackedObject 更改为 LookAtMainCamera）与 GazeAlignment 的角变化来实现。

<img src="../images/solver/MRTK_Solver_HandConstraintSafeZones.png" width="450" alt="HandMenu Safe Zones">

* **激活事件**：目前 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 触发了四个激活事件。 可以在许多不同的组合中使用这些事件来创建独特 [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) 的行为， `MRTK/Examples/Demos/HandTracking/Scenes/` 有关这些行为的示例，请参阅下的 HandBasedMenuExample 场景。

  * *OnHandActivate*：当手满足 IsHandActive 方法时触发。
  * *OnHandDeactivate*： IsHandActive 方法不再满足时触发触发器。
  * *OnFirstHandDetected*：手动跟踪状态从无干预视图更改为视图中的第一批时发生。
  * *OnLastHandLost*：在从视图中的至少一个手更改手动跟踪状态时发生。

* **规划求解激活/停用逻辑**：当前用于激活和停用逻辑的建议 [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) 是通过使用 SolverHandler 的 UpdateSolver 值来实现，而不是通过禁用/启用对象来实现。 在示例场景中，可以通过在附加菜单的 ManipulationHandler "OnManipulationStarted/结束" 事件后触发的基于编辑器的挂钩来查看。

  * *正在停止手动约束逻辑*：尝试将手动约束的对象设置为 "停止" (并且不运行激活/停用逻辑) 时，请将 UpdateSolver 设置为 False，而不是禁用 HandConstraintPalmUp。
    * 如果你想要启用基于注视的 (甚至不是基于注视的) 重新附加逻辑，则随后将调用 StartWorldLockReattachCheckCoroutine () 函数。 这会触发一个协同程序，它会继续检查是否满足 "IsValidController" 条件，并将 UpdateSolver 设置为 True (或禁用对象) 
  * *启动手动约束逻辑*：尝试将手动约束的对象设置为根据其是否满足激活) 条件 (再次开始后，请将 SolverHandler 的 UpdateSolver 设置为 true。

* 重新 **附加逻辑**：目前， [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) 无论 SolverHandler 的 UpdateSolver 是否为 True，都可以自动将目标对象重新附加到跟踪的点。 这是通过调用 HandConstraintPalmUp 的 StartWorldLockReattachCheckCoroutine () 函数来实现的，在这种情况下， (它会将 SolverHandler 的 UpdateSolver 有效地设置为 False) 。

## <a name="see-also"></a>另请参阅

* [Button](button.md)
* [邻近菜单](near-menu.md)
