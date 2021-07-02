---
title: 手型接点 chaser
description: MRTK 中的 chaser
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 0beac2dae5aa12cf07f193dab9a6db7bc7ddf2e5
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175366"
---
# <a name="hand-joint-chaser"></a><span data-ttu-id="ef95b-104">手型接点 chaser</span><span class="sxs-lookup"><span data-stu-id="ef95b-104">Hand joint chaser</span></span>

<span data-ttu-id="ef95b-105">![手型接点 chasers ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) 此示例场景演示了如何使用规划求解将对象附加到手。</span><span class="sxs-lookup"><span data-stu-id="ef95b-105">![Hand joint chasers](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="ef95b-106">示例场景</span><span class="sxs-lookup"><span data-stu-id="ef95b-106">Example scene</span></span>

<span data-ttu-id="ef95b-107">可以在下的文件夹中查找示例场景 **HandJointChaserExample** 场景 `Assets/MRTK/Examples` `Demos/Input/Scenes/` 。</span><span class="sxs-lookup"><span data-stu-id="ef95b-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="ef95b-108">规划求解处理程序</span><span class="sxs-lookup"><span data-stu-id="ef95b-108">Solver handler</span></span>

<span data-ttu-id="ef95b-109">单击 " **跟踪对象以引用** "，然后选择 " **右侧接点** " 或 " **右向右**"。</span><span class="sxs-lookup"><span data-stu-id="ef95b-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="ef95b-110">你将能够看到 **跟踪** 的 "向下移动" 下拉。</span><span class="sxs-lookup"><span data-stu-id="ef95b-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="ef95b-111">从下拉列表中，可以选择要跟踪的特定联合。此示例场景使用径向视图规划求解来使对象跟随目标对象。</span><span class="sxs-lookup"><span data-stu-id="ef95b-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="ef95b-112">有关更多详细信息，请参阅 " [规划求解](../ux-building-blocks/solvers/solver.md) " 页。</span><span class="sxs-lookup"><span data-stu-id="ef95b-112">See [Solver](../ux-building-blocks/solvers/solver.md) page for more details.</span></span>

![手动组合求解器](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
