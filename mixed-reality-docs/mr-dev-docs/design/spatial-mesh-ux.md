---
title: 空间网格可视化
description: 了解设备如何使用空间网格了解物理环境。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 混合现实，HoloLens，UI 控制，交互，UI，ux，UX 设计，空间 UI，空间交互，三维 UI，三维 UX，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包
ms.openlocfilehash: ffa13da6762b803ba2a3f370308ac2af65164ecf
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848194"
---
# <a name="spatial-mesh"></a><span data-ttu-id="fafc8-104">空间网格</span><span class="sxs-lookup"><span data-stu-id="fafc8-104">Spatial mesh</span></span>

![空间网格](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="fafc8-106">用户了解设备如何通过空间网格可视化了解并了解物理环境。</span><span class="sxs-lookup"><span data-stu-id="fafc8-106">Users learn how a device perceives and understands the physical environment through spatial mesh visualization.</span></span> <span data-ttu-id="fafc8-107">适当的空间网格可视化可以在提供空间上下文的同时创建不知和神奇体验。</span><span class="sxs-lookup"><span data-stu-id="fafc8-107">Proper spatial mesh visualization can create a delightful and magical experience while providing spatial context.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="fafc8-108">设计准则</span><span class="sxs-lookup"><span data-stu-id="fafc8-108">Design guideline</span></span>

<span data-ttu-id="fafc8-109">允许用户集中关注内容并与之交互，这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="fafc8-109">It's important to allow the user to focus and interact with content.</span></span> <span data-ttu-id="fafc8-110">背景中的空间网格的连续可视化可能会分散注意力。</span><span class="sxs-lookup"><span data-stu-id="fafc8-110">Continuous visualization of the spatial mesh in the background can be distracting.</span></span> <span data-ttu-id="fafc8-111">建议在初始启动时，或在用户清楚地显示要查看环境网格的情况下，在初始启动时将环境可视化，或在用户清楚地显示环境网格。</span><span class="sxs-lookup"><span data-stu-id="fafc8-111">We recommend visualizing the environment sparingly, either only once in the initial launch or when the user clearly shows they want to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="fafc8-112">可在混合现实门户中查看此行为。</span><span class="sxs-lookup"><span data-stu-id="fafc8-112">You can observe this behavior in the Mixed Reality Portal.</span></span>
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="fafc8-113">MRTK 中的空间网格可视化 (适用于 Unity 的混合现实工具包) </span><span class="sxs-lookup"><span data-stu-id="fafc8-113">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="fafc8-114">MRTK 提供了多个材料来实现空间网格可视化。</span><span class="sxs-lookup"><span data-stu-id="fafc8-114">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="fafc8-115">**MRTK_Wireframe，MRTK_Wireframe** 的：默认静态空间网格材料，其中显示不带动画的网格轮廓。</span><span class="sxs-lookup"><span data-stu-id="fafc8-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material, which shows the mesh outlines without animation.</span></span> <span data-ttu-id="fafc8-116">此材料可用于调试目的，因为它显示了整个空间网格几何。</span><span class="sxs-lookup"><span data-stu-id="fafc8-116">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="fafc8-117">不过，不建议在生产环境中使用。</span><span class="sxs-lookup"><span data-stu-id="fafc8-117">However, it isn't recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="fafc8-118">**MRTK_SurfaceReconstruction** 材料：此材料在空间网格上提供动画脉冲效果。</span><span class="sxs-lookup"><span data-stu-id="fafc8-118">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="fafc8-119">您可以使用此材料在特定时刻或用户的点击输入中直观显示环境。</span><span class="sxs-lookup"><span data-stu-id="fafc8-119">You can use this material to visualize the environment at a specific moment or on the user's air-tap input.</span></span> <span data-ttu-id="fafc8-120">有关示例，请参阅 **PulseShaderExamples** 场景。</span><span class="sxs-lookup"><span data-stu-id="fafc8-120">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="fafc8-121">有关详细信息，请参阅 [MRTK-空间感知](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) 和 [MRTK 着色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html)。</span><span class="sxs-lookup"><span data-stu-id="fafc8-121">For more information, see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="fafc8-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fafc8-122">See also</span></span>

* [<span data-ttu-id="fafc8-123">光标</span><span class="sxs-lookup"><span data-stu-id="fafc8-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="fafc8-124">手部射线</span><span class="sxs-lookup"><span data-stu-id="fafc8-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="fafc8-125">Button</span><span class="sxs-lookup"><span data-stu-id="fafc8-125">Button</span></span>](button.md)
* [<span data-ttu-id="fafc8-126">可交互对象</span><span class="sxs-lookup"><span data-stu-id="fafc8-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="fafc8-127">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="fafc8-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="fafc8-128">操作</span><span class="sxs-lookup"><span data-stu-id="fafc8-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="fafc8-129">手动菜单</span><span class="sxs-lookup"><span data-stu-id="fafc8-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="fafc8-130">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="fafc8-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="fafc8-131">对象集合</span><span class="sxs-lookup"><span data-stu-id="fafc8-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="fafc8-132">语音命令</span><span class="sxs-lookup"><span data-stu-id="fafc8-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="fafc8-133">键盘</span><span class="sxs-lookup"><span data-stu-id="fafc8-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="fafc8-134">工具提示</span><span class="sxs-lookup"><span data-stu-id="fafc8-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="fafc8-135">平板</span><span class="sxs-lookup"><span data-stu-id="fafc8-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="fafc8-136">滑块</span><span class="sxs-lookup"><span data-stu-id="fafc8-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="fafc8-137">着色器</span><span class="sxs-lookup"><span data-stu-id="fafc8-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="fafc8-138">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="fafc8-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="fafc8-139">显示进度</span><span class="sxs-lookup"><span data-stu-id="fafc8-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="fafc8-140">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="fafc8-140">Surface magnetism</span></span>](surface-magnetism.md)
