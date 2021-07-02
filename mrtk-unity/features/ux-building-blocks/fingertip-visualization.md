---
title: 手指可视化效果
description: MRTK 中的手指提示可视化概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 指尖
ms.openlocfilehash: af23fdb9b618e276b7442405e54b7dccd141e4ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177529"
---
# <a name="fingertip-visualization"></a><span data-ttu-id="f3b75-104">手指可视化效果</span><span class="sxs-lookup"><span data-stu-id="f3b75-104">Fingertip visualization</span></span>

![手指可视化效果主](../images/fingertip/MRTK_FingertipVisualization_Main.png)

<span data-ttu-id="f3b75-106">触指可让用户识别与目标对象的距离。</span><span class="sxs-lookup"><span data-stu-id="f3b75-106">The fingertip affordance helps the user recognize the distance from the target object.</span></span> <span data-ttu-id="f3b75-107">环形状视觉对象根据从手指到对象的距离调整其大小。</span><span class="sxs-lookup"><span data-stu-id="f3b75-107">The ring shape visual adjusts its size based on the distance from the fingertip to the object.</span></span> <span data-ttu-id="f3b75-108">手指可视化效果主要由 `FingerCursor` (Assets/MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab)  (和脚本) （生成为一个 *CursorePointer* 的光标预制）控制。</span><span class="sxs-lookup"><span data-stu-id="f3b75-108">The fingertip visualization is primarily controlled by the `FingerCursor` (Assets/MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab) (and script) which is spawned as the cursor prefab of the *PokePointer*.</span></span> <span data-ttu-id="f3b75-109">可视化效果的其他组件包括 *ProximityLight* 脚本和 *MixedRealityStandard 着色* 器。</span><span class="sxs-lookup"><span data-stu-id="f3b75-109">Other components of the visualization include the *ProximityLight* script, and *MixedRealityStandard* shader.</span></span>

## <a name="how-to-use-the-fingertip-visualization"></a><span data-ttu-id="f3b75-110">如何使用手指可视化效果</span><span class="sxs-lookup"><span data-stu-id="f3b75-110">How to use the fingertip visualization</span></span>

<span data-ttu-id="f3b75-111">默认情况下，手指可视化效果在配置为生成 FingerCursor 的任何 Unity 场景中都工作。</span><span class="sxs-lookup"><span data-stu-id="f3b75-111">By default the fingertip visualization will work in any Unity scene that is configured to spawn a FingerCursor.</span></span> <span data-ttu-id="f3b75-112">FingerCursor 的生成发生在 *DefaultMixedRealityToolkitConfigurationProfile* 下：</span><span class="sxs-lookup"><span data-stu-id="f3b75-112">Spawning of the FingerCursor occurs in the *DefaultMixedRealityToolkitConfigurationProfile* under:</span></span>

<span data-ttu-id="f3b75-113">*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile >用户 > FingerCursor*</span><span class="sxs-lookup"><span data-stu-id="f3b75-113">*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > PokePointer > FingerCursor*</span></span>

<span data-ttu-id="f3b75-114">从较高层面看，手指可视化效果的工作原理是使用邻近光在接受邻近光的任何附近表面上绘制彩色渐变。</span><span class="sxs-lookup"><span data-stu-id="f3b75-114">At a high level the fingertip visualization works by using a proximity light to project a colored gradient on any nearby surfaces that accept proximity lights.</span></span> <span data-ttu-id="f3b75-115">然后，手指光标会查找任何附近的可交互表面（由父级确定）以在手指向表面移动时将手指环与表面 `IMixedRealityNearPointer(s)` 对齐。</span><span class="sxs-lookup"><span data-stu-id="f3b75-115">The finger cursor then looks for any nearby interactable surfaces, which are determined by parent `IMixedRealityNearPointer(s)`, to align the finger ring with a surface as the finger moves towards a surface.</span></span> <span data-ttu-id="f3b75-116">当手指接近表面时，手指环也使用 MixedRealityStandard 着色器圆角属性进行动态动画处理。</span><span class="sxs-lookup"><span data-stu-id="f3b75-116">As a finger approaches a surface the finger ring is also dynamically animated using the round corner properties of the MixedRealityStandard shader.</span></span>

## <a name="example-scene"></a><span data-ttu-id="f3b75-117">示例场景</span><span class="sxs-lookup"><span data-stu-id="f3b75-117">Example scene</span></span>

<span data-ttu-id="f3b75-118">可以在几乎任何使用手部表达的场景中找到手部可视化示例，但在 [HandInteractionExample 场景中非常突出](../example-scenes/hand-interaction-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="f3b75-118">You can find fingertip visualization examples in almost any scene that works with articulated hands, but is prominent in the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md).</span></span>

![手指可视化状态](../images/fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a><span data-ttu-id="f3b75-120">检查器属性</span><span class="sxs-lookup"><span data-stu-id="f3b75-120">Inspector properties</span></span>

<span data-ttu-id="f3b75-121">**FingerCursor** 许多手指光标属性都继承自基游标类。</span><span class="sxs-lookup"><span data-stu-id="f3b75-121">**FingerCursor** Many of the finger cursor properties are inherited from the base cursor class.</span></span> <span data-ttu-id="f3b75-122">重要属性包括驱动 MixedRealityStandard 着色器中手指环动画的远/近表面边距和宽度。</span><span class="sxs-lookup"><span data-stu-id="f3b75-122">Important properties include the far / near surface margins and widths which drive the finger ring animation in the MixedRealityStandard shader.</span></span> <span data-ttu-id="f3b75-123">对于其他属性，请将鼠标悬停在检查器工具提示上。</span><span class="sxs-lookup"><span data-stu-id="f3b75-123">For other properties please hover over the inspector tool tips.</span></span>

<img src="../images/fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Cursor Inspector">

<span data-ttu-id="f3b75-124">**ProximityLight** 邻近光设置控制光在靠近和远离表面时的外观。</span><span class="sxs-lookup"><span data-stu-id="f3b75-124">**ProximityLight** The proximity light settings control how the light looks when near and far from a surface.</span></span> <span data-ttu-id="f3b75-125">中间、中间和外部颜色控制光的渐变外观，并可根据应用程序的调色板进行自定义定制。</span><span class="sxs-lookup"><span data-stu-id="f3b75-125">The center, middle, and outer colors control the gradient look of the light and can be custom tailored for the color palette of your application.</span></span> <span data-ttu-id="f3b75-126">请注意，颜色是 HDR (高动态范围) ，允许用户将邻近光变亮为高于 1 的值。</span><span class="sxs-lookup"><span data-stu-id="f3b75-126">Note, the colors are HDR (High Dynamic Range) to allow users to brighten the proximity light to values above one.</span></span> <span data-ttu-id="f3b75-127">对于其他属性，请将鼠标悬停在检查器工具提示上。</span><span class="sxs-lookup"><span data-stu-id="f3b75-127">For other properties please hover over the inspector tool tips.</span></span>

<span data-ttu-id="f3b75-128">**MixedRealityStandard 着色器** MixedRealityStandard 着色器用于 MRTK 中的许多效果。</span><span class="sxs-lookup"><span data-stu-id="f3b75-128">**MixedRealityStandard Shader** The MixedRealityStandard shader is used for many effects in the MRTK.</span></span> <span data-ttu-id="f3b75-129">对于手部可视化来说，重要的两个设置是"Near Fade"和"Proximity Light"。</span><span class="sxs-lookup"><span data-stu-id="f3b75-129">The two settings important for fingertip visualization are "Near Fade" and "Proximity Light."</span></span> <span data-ttu-id="f3b75-130">"近淡出"允许对象在照相机或光线靠近时淡入/淡出。</span><span class="sxs-lookup"><span data-stu-id="f3b75-130">Near Fade allows objects to fade in / out as a camera or light nears them.</span></span> <span data-ttu-id="f3b75-131">请确保选中"光"，以允许邻近光驱动淡 (，而不是相机) 。</span><span class="sxs-lookup"><span data-stu-id="f3b75-131">Make sure to check "Light" to allow proximity lights to drive the fade (rather than the camera).</span></span> <span data-ttu-id="f3b75-132">可以反转"Fade Begin"和"Fade Complete"的值来反转淡入淡出。</span><span class="sxs-lookup"><span data-stu-id="f3b75-132">You can reverse the values of "Fade Begin" and "Fade Complete" to reverse a fade.</span></span> <span data-ttu-id="f3b75-133">检查"邻近感应光"，了解希望邻近光变亮的任何表面。</span><span class="sxs-lookup"><span data-stu-id="f3b75-133">Check "Proximity Light" for any surface you would like the proximity light to brighten.</span></span> <span data-ttu-id="f3b75-134">对于其他属性，请将鼠标悬停在检查器工具提示上。</span><span class="sxs-lookup"><span data-stu-id="f3b75-134">For other properties please hover over the inspector tool tips.</span></span>

<img src="../images/fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Shader Inspector">
