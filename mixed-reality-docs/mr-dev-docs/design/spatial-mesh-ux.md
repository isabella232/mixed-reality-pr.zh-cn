---
title: 空间网格可视化
description: 了解 MRTK 中空间网格可视化的设计准则和物理环境理解。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 混合现实， HoloLens， UI 控件， 交互， ui， ux， UX 设计， 空间 UI， 空间交互， 3D UI， 3D UX， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， HoloLens， MRTK， 混合现实工具包
ms.openlocfilehash: 5bdcba60f38ac67bbf0f394337735f4a2d4ec423
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600626"
---
# <a name="spatial-mesh"></a><span data-ttu-id="9a604-104">空间网格</span><span class="sxs-lookup"><span data-stu-id="9a604-104">Spatial mesh</span></span>

![空间网格](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="9a604-106">用户通过空间网格可视化了解设备如何感知和理解物理环境。</span><span class="sxs-lookup"><span data-stu-id="9a604-106">Users learn how a device perceives and understands the physical environment through spatial mesh visualization.</span></span> <span data-ttu-id="9a604-107">适当的空间网格可视化效果可以在提供空间上下文的同时创建一种有趣而有趣的体验。</span><span class="sxs-lookup"><span data-stu-id="9a604-107">Proper spatial mesh visualization can create a delightful and magical experience while providing spatial context.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="9a604-108">设计准则</span><span class="sxs-lookup"><span data-stu-id="9a604-108">Design guideline</span></span>

<span data-ttu-id="9a604-109">必须允许用户专注于内容并与之交互。</span><span class="sxs-lookup"><span data-stu-id="9a604-109">It's important to allow the user to focus and interact with content.</span></span> <span data-ttu-id="9a604-110">在后台连续可视化空间网格可能会分散注意力。</span><span class="sxs-lookup"><span data-stu-id="9a604-110">Continuous visualization of the spatial mesh in the background can be distracting.</span></span> <span data-ttu-id="9a604-111">建议尽量少地可视化环境，只需在初始发射时显示一次，或者当用户清楚地显示他们希望通过定目标空间和空敲击空间来查看环境网格时。</span><span class="sxs-lookup"><span data-stu-id="9a604-111">We recommend visualizing the environment sparingly, either only once in the initial launch or when the user clearly shows they want to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="9a604-112">可以在以下方法中观察此混合现实门户。</span><span class="sxs-lookup"><span data-stu-id="9a604-112">You can observe this behavior in the Mixed Reality Portal.</span></span>
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="9a604-113">MRTK 中的空间网格 (Unity 混合现实工具包) 可视化效果</span><span class="sxs-lookup"><span data-stu-id="9a604-113">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="9a604-114">MRTK 为空间网格可视化提供了多种材料。</span><span class="sxs-lookup"><span data-stu-id="9a604-114">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="9a604-115">**MRTK_Wireframe.mat、MRTK_Wireframe.mat：** 默认静态空间网格材料，用于显示无动画的网格轮廓。</span><span class="sxs-lookup"><span data-stu-id="9a604-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material, which shows the mesh outlines without animation.</span></span> <span data-ttu-id="9a604-116">此材料可用于调试，因为它显示了整个空间网格几何。</span><span class="sxs-lookup"><span data-stu-id="9a604-116">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="9a604-117">但是，不建议用于生产。</span><span class="sxs-lookup"><span data-stu-id="9a604-117">However, it isn't recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="9a604-118">**MRTK_SurfaceReconstruction.mat：** 此材料在空间网格上提供动画脉冲效果。</span><span class="sxs-lookup"><span data-stu-id="9a604-118">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="9a604-119">可以使用此材料来可视化特定时刻的环境或用户的空敲击输入。</span><span class="sxs-lookup"><span data-stu-id="9a604-119">You can use this material to visualize the environment at a specific moment or on the user's air-tap input.</span></span> <span data-ttu-id="9a604-120">有关 **示例，请参阅 PulseShaderExamples.unity** 场景。</span><span class="sxs-lookup"><span data-stu-id="9a604-120">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">

* <span data-ttu-id="9a604-121">有关详细信息，请参阅 [MRTK - 空间感知](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) 和 [MRTK - 脉冲着色器](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader)。</span><span class="sxs-lookup"><span data-stu-id="9a604-121">For more information, see [MRTK - Spatial Awareness](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) and [MRTK - Pulse Shader](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="9a604-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a604-122">See also</span></span>

* [<span data-ttu-id="9a604-123">光标</span><span class="sxs-lookup"><span data-stu-id="9a604-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="9a604-124">手部射线</span><span class="sxs-lookup"><span data-stu-id="9a604-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="9a604-125">Button</span><span class="sxs-lookup"><span data-stu-id="9a604-125">Button</span></span>](button.md)
* [<span data-ttu-id="9a604-126">可交互对象</span><span class="sxs-lookup"><span data-stu-id="9a604-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="9a604-127">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="9a604-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="9a604-128">操作</span><span class="sxs-lookup"><span data-stu-id="9a604-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9a604-129">手动菜单</span><span class="sxs-lookup"><span data-stu-id="9a604-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="9a604-130">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="9a604-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="9a604-131">对象集合</span><span class="sxs-lookup"><span data-stu-id="9a604-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="9a604-132">语音命令</span><span class="sxs-lookup"><span data-stu-id="9a604-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="9a604-133">键盘</span><span class="sxs-lookup"><span data-stu-id="9a604-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="9a604-134">工具提示</span><span class="sxs-lookup"><span data-stu-id="9a604-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="9a604-135">平板</span><span class="sxs-lookup"><span data-stu-id="9a604-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="9a604-136">滑块</span><span class="sxs-lookup"><span data-stu-id="9a604-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="9a604-137">着色器</span><span class="sxs-lookup"><span data-stu-id="9a604-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="9a604-138">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="9a604-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="9a604-139">显示进度</span><span class="sxs-lookup"><span data-stu-id="9a604-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="9a604-140">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="9a604-140">Surface magnetism</span></span>](surface-magnetism.md)