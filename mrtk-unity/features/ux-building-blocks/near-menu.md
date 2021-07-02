---
title: 追踪菜单
description: MRTK 中靠近菜单类型的概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 附近菜单，
ms.openlocfilehash: 15f53ad4e67a0b281750fd1df7f894c49f546531
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175650"
---
# <a name="near-menu"></a><span data-ttu-id="2cdf9-104">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="2cdf9-104">Near menu</span></span>

![追踪菜单](../images/near-menu/MRTK_UX_NearMenu.png)

<span data-ttu-id="2cdf9-106">"近菜单"是一个 UX 控件，它提供按钮或其他 UI 组件的集合。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-106">Near Menu is a UX control which provides a collection of buttons or other UI components.</span></span> <span data-ttu-id="2cdf9-107">它围绕用户正文浮动，随时易于访问。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-107">It is floating around the user's body and easily accessible anytime.</span></span> <span data-ttu-id="2cdf9-108">由于它与用户松散耦合，因此不会妨碍用户与目标内容的交互。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-108">Since it is loosely coupled with the user, it does not disturb the user's interaction with the target content.</span></span> <span data-ttu-id="2cdf9-109">用户可以使用"固定"按钮来锁定/解锁菜单。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-109">The user can use the 'Pin' button to world-lock/unlock the menu.</span></span> <span data-ttu-id="2cdf9-110">可以抓取菜单，并放置在特定位置。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-110">The menu can be grabbed and placed at a specific position.</span></span>

## <a name="interaction-behavior"></a><span data-ttu-id="2cdf9-111">交互行为</span><span class="sxs-lookup"><span data-stu-id="2cdf9-111">Interaction behavior</span></span>

- <span data-ttu-id="2cdf9-112">**标记：** 菜单将跟随你，并保持在 30-60cm 范围内，与用户进行近场交互。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-112">**Tag-along**: The menu follows you and stays within 30-60cm range from the user for the near interactions.</span></span>
- <span data-ttu-id="2cdf9-113">**固定**：使用"固定"按钮，菜单可以全球锁定并释放。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-113">**Pin**: Using the 'Pin' button, the menu can be world-locked and released.</span></span>
- <span data-ttu-id="2cdf9-114">**抓取和移动**：菜单始终可抓取且可移动。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-114">**Grab and move**: The menu is always grabbable and movable.</span></span> <span data-ttu-id="2cdf9-115">无论之前的状态如何，在抓取和释放 (菜单) 锁定菜单。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-115">Regardless of the previous state, the menu will be pinned(world-locked) when grabbed and released.</span></span> <span data-ttu-id="2cdf9-116">可抓取区域有视觉提示。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-116">There are visual cues for the grabbable area.</span></span> <span data-ttu-id="2cdf9-117">它们公开在手部邻近性。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-117">They are revealed on hand proximity.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a><span data-ttu-id="2cdf9-118">预制</span><span class="sxs-lookup"><span data-stu-id="2cdf9-118">Prefabs</span></span>

<span data-ttu-id="2cdf9-119">"近菜单"预制件旨在演示如何使用 MRTK 的各种组件生成用于近交互的菜单。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-119">Near Menu prefabs are designed to demonstrate how to use MRTK's various components to build menus for near interactions.</span></span>

- <span data-ttu-id="2cdf9-120">**NearMenu2x4.prefab**</span><span class="sxs-lookup"><span data-stu-id="2cdf9-120">**NearMenu2x4.prefab**</span></span>
- <span data-ttu-id="2cdf9-121">**NearMenu3x1.prefab**</span><span class="sxs-lookup"><span data-stu-id="2cdf9-121">**NearMenu3x1.prefab**</span></span>
- <span data-ttu-id="2cdf9-122">**NearMenu3x2.prefab**</span><span class="sxs-lookup"><span data-stu-id="2cdf9-122">**NearMenu3x2.prefab**</span></span>
- <span data-ttu-id="2cdf9-123">**NearMenu3x3.prefab**</span><span class="sxs-lookup"><span data-stu-id="2cdf9-123">**NearMenu3x3.prefab**</span></span>
- <span data-ttu-id="2cdf9-124">**NearMenu4x1.prefab**</span><span class="sxs-lookup"><span data-stu-id="2cdf9-124">**NearMenu4x1.prefab**</span></span>
- <span data-ttu-id="2cdf9-125">**NearMenu4x2.prefab**</span><span class="sxs-lookup"><span data-stu-id="2cdf9-125">**NearMenu4x2.prefab**</span></span>

## <a name="example-scene"></a><span data-ttu-id="2cdf9-126">示例场景</span><span class="sxs-lookup"><span data-stu-id="2cdf9-126">Example scene</span></span>

<span data-ttu-id="2cdf9-127">可以在场景中找到"近菜单"预制项 `NearMenuExamples` 的示例。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-127">You can find examples of Near Menu prefabs in the `NearMenuExamples` scene.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a><span data-ttu-id="2cdf9-128">结构</span><span class="sxs-lookup"><span data-stu-id="2cdf9-128">Structure</span></span>

<span data-ttu-id="2cdf9-129">近菜单预制件由以下 MRTK 组件构成。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-129">Near Menu prefabs are made with following MRTK components.</span></span>

- <span data-ttu-id="2cdf9-130">[**PressableButtonHoloLens2**](button.md) 预制</span><span class="sxs-lookup"><span data-stu-id="2cdf9-130">[**PressableButtonHoloLens2**](button.md) prefab</span></span>
- <span data-ttu-id="2cdf9-131">[**网格对象集合**](object-collection.md)：网格中的多个按钮布局</span><span class="sxs-lookup"><span data-stu-id="2cdf9-131">[**Grid Object Collection**](object-collection.md): Multiple button layout in grid</span></span>
- <span data-ttu-id="2cdf9-132">[**操作处理程序**](manipulation-handler.md)：抓取并移动菜单</span><span class="sxs-lookup"><span data-stu-id="2cdf9-132">[**Manipulation Handler**](manipulation-handler.md): Grab and move the menu</span></span>
- <span data-ttu-id="2cdf9-133">[**RadialView 求解器**](solvers/solver.md)：跟踪 (跟踪标记) 行为</span><span class="sxs-lookup"><span data-stu-id="2cdf9-133">[**RadialView Solver**](solvers/solver.md): Follow Me(tag-along) behavior</span></span>

![近菜单预制](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a><span data-ttu-id="2cdf9-135">如何自定义</span><span class="sxs-lookup"><span data-stu-id="2cdf9-135">How to customize</span></span>

<span data-ttu-id="2cdf9-136">**1.添加/删除按钮**</span><span class="sxs-lookup"><span data-stu-id="2cdf9-136">**1. Add/Remove Buttons**</span></span>

<span data-ttu-id="2cdf9-137">在 `ButtonCollection` "对象"下，添加或删除按钮。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-137">Under `ButtonCollection` object, add or remove buttons.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

<span data-ttu-id="2cdf9-138">**2.更新网格对象集合**</span><span class="sxs-lookup"><span data-stu-id="2cdf9-138">**2. Update the Grid Object Collection**</span></span>

<span data-ttu-id="2cdf9-139">单击 `Update Collection` 对象的检查器中的 `ButtonCollection` 按钮。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-139">Click `Update Collection` button in the Inspector of the `ButtonCollection` object.</span></span> <span data-ttu-id="2cdf9-140">它将更新网格布局。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-140">It will update the grid layout.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

<span data-ttu-id="2cdf9-141">可以使用 Grid 对象集合的 属性 `Rows` 配置行数。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-141">You can configure the number of rows using `Rows` property of the Grid Object Collection.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

<span data-ttu-id="2cdf9-142">**3.调整反板大小**</span><span class="sxs-lookup"><span data-stu-id="2cdf9-142">**3. Adjust the backplate size**</span></span>

<span data-ttu-id="2cdf9-143">调整 下 对象 `Quad` `Backplate` 的大小。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-143">Adjust the size of the `Quad` under `Backplate` object.</span></span> <span data-ttu-id="2cdf9-144">底板的宽度和高度应为 `0.032 * [Number of the buttons + 1]` 。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-144">The width and height of the backplate should be `0.032 * [Number of the buttons + 1]`.</span></span> <span data-ttu-id="2cdf9-145">例如，如果有 3 x 2 个按钮，则底板的宽度为 `0.032 * 4` ，高度为 `0.032 * 3` 。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-145">For example, if you have 3 x 2 buttons, the width of the backplate is `0.032 * 4` and the height is `0.032 * 3`.</span></span> <span data-ttu-id="2cdf9-146">可以直接将此表达式放入 Unity 的 字段中。</span><span class="sxs-lookup"><span data-stu-id="2cdf9-146">You can directly put this expression into the Unity's field.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- <span data-ttu-id="2cdf9-147">按钮的默认大小HoloLens 2为 3.2x3.2 cm (0.032m) </span><span class="sxs-lookup"><span data-stu-id="2cdf9-147">Default size of the HoloLens 2 button is 3.2x3.2 cm (0.032m)</span></span>

## <a name="see-also"></a><span data-ttu-id="2cdf9-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2cdf9-148">See also</span></span>

- [<span data-ttu-id="2cdf9-149">**按钮**</span><span class="sxs-lookup"><span data-stu-id="2cdf9-149">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="2cdf9-150">**边界控制**</span><span class="sxs-lookup"><span data-stu-id="2cdf9-150">**Bounds Control**</span></span>](bounds-control.md)
- [<span data-ttu-id="2cdf9-151">**滑块**</span><span class="sxs-lookup"><span data-stu-id="2cdf9-151">**Slider**</span></span>](sliders.md)
- [<span data-ttu-id="2cdf9-152">**网格对象集合**</span><span class="sxs-lookup"><span data-stu-id="2cdf9-152">**Grid Object Collection**</span></span>](object-collection.md)
- [<span data-ttu-id="2cdf9-153">**操作处理程序**</span><span class="sxs-lookup"><span data-stu-id="2cdf9-153">**Manipulation Handler**</span></span>](manipulation-handler.md)
- [<span data-ttu-id="2cdf9-154">**RadialView 求解器**</span><span class="sxs-lookup"><span data-stu-id="2cdf9-154">**RadialView Solver**</span></span>](solvers/solver.md)
