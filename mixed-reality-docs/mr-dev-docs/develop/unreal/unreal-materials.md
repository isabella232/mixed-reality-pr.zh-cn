---
title: Unreal 中的材料建议
description: Unreal 引擎中的资料概述。
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal，Unreal 引擎4，UE4，HoloLens，HoloLens 2，开发，材料，文档，指南，功能，全息影像，游戏开发，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: d57689e9427ab5877e3afb49b0d19f35df6c47d2
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678936"
---
# <a name="material-recommendations-in-unreal"></a><span data-ttu-id="965f7-104">Unreal 中的材料建议</span><span class="sxs-lookup"><span data-stu-id="965f7-104">Material recommendations in Unreal</span></span>

<span data-ttu-id="965f7-105">材料可能会在 Unreal 引擎中产生或中断性能。</span><span class="sxs-lookup"><span data-stu-id="965f7-105">Materials can make or break performance in Unreal Engine.</span></span> <span data-ttu-id="965f7-106">此页将作为你应使用的基本设置的快速入门，以便获得最佳性能。</span><span class="sxs-lookup"><span data-stu-id="965f7-106">This page acts as a quick-start on the basic settings you should be using in order to get the best performance.</span></span>

## <a name="using-customizeduvs"></a><span data-ttu-id="965f7-107">使用 CustomizedUVs</span><span class="sxs-lookup"><span data-stu-id="965f7-107">Using CustomizedUVs</span></span>

<span data-ttu-id="965f7-108">如果需要对材料提供 Uv-11 的平铺，则应使用 CustomizedUVs，而不是直接修改纹理节点的 UV。</span><span class="sxs-lookup"><span data-stu-id="965f7-108">If you need to provide tiling of UVs on your material, you should use CustomizedUVs rather than modifying the UV of the texture node directly.</span></span> <span data-ttu-id="965f7-109">CustomizedUVs 允许在顶点着色器而不是像素着色器中发生 UV 操作。</span><span class="sxs-lookup"><span data-stu-id="965f7-109">CustomizedUVs allow UV manipulation to happen in the Vertex shaders rather than Pixel shader.</span></span> 

![Unreal 中的材料设置](images/unreal-materials-img-01c.png)

<span data-ttu-id="965f7-111">有关详细信息，请参阅 [Unreal 引擎文档](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) 和以下屏幕截图中的最佳方案示例：</span><span class="sxs-lookup"><span data-stu-id="965f7-111">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) and best practice examples in the screenshots below:</span></span>

<span data-ttu-id="965f7-112">建议[ ![ 在 Unreal ](images/unreal-materials-img-01.png) 中设置的材料设置](images/unreal-materials-img-01.png#lightbox) 
 *Recommended material setup*</span><span class="sxs-lookup"><span data-stu-id="965f7-112">[ ![Recommended material settings in Unreal](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox)
*Recommended material setup*</span></span>

<span data-ttu-id="965f7-113">不建议[ ![ 的材料设置 Unreal ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox) 
 *不推荐的材料* 设置</span><span class="sxs-lookup"><span data-stu-id="965f7-113">[ ![Non recommended material settings in Unreal](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)
*Non-recommended material setup*</span></span>

## <a name="changing-blend-mode"></a><span data-ttu-id="965f7-114">更改混合模式</span><span class="sxs-lookup"><span data-stu-id="965f7-114">Changing Blend Mode</span></span>

<span data-ttu-id="965f7-115">除非有很强的理由，否则应将 blend 模式设置为不透明。</span><span class="sxs-lookup"><span data-stu-id="965f7-115">You should set blend mode to opaque unless there is a strong reason to do otherwise.</span></span> <span data-ttu-id="965f7-116">屏蔽和半透明的材料速度缓慢。</span><span class="sxs-lookup"><span data-stu-id="965f7-116">Masked and Translucent materials are slow.</span></span> <span data-ttu-id="965f7-117">有关详细信息，请 [参阅 Unreal 引擎文档](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)。</span><span class="sxs-lookup"><span data-stu-id="965f7-117">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![更改混合模式](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a><span data-ttu-id="965f7-119">更新移动的照明</span><span class="sxs-lookup"><span data-stu-id="965f7-119">Updating lighting for mobile</span></span>

<span data-ttu-id="965f7-120">应关闭完全精度。</span><span class="sxs-lookup"><span data-stu-id="965f7-120">Full precision should be turned off.</span></span> <span data-ttu-id="965f7-121">可以通过翻方向信息来拔下 Lightmap 照明。</span><span class="sxs-lookup"><span data-stu-id="965f7-121">Lightmap lighting can be dialed down by turning of directional information.</span></span> <span data-ttu-id="965f7-122">禁用后，lightmaps 中的照明将是平面但更便宜。</span><span class="sxs-lookup"><span data-stu-id="965f7-122">When disabled, lighting from lightmaps will be flat but cheaper.</span></span>

![Unreal 中的移动材料设置](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a><span data-ttu-id="965f7-124">调整前向底纹</span><span class="sxs-lookup"><span data-stu-id="965f7-124">Adjusting Forward Shading</span></span>

<span data-ttu-id="965f7-125">这些选项以性能为代价提高视觉保真。</span><span class="sxs-lookup"><span data-stu-id="965f7-125">These options improve visual fidelity at the cost of performance.</span></span> <span data-ttu-id="965f7-126">为了获得最佳性能，应关闭它们。</span><span class="sxs-lookup"><span data-stu-id="965f7-126">They should be turned off for maximum performance.</span></span>

![Unreal 中的前向底纹材料设置](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a><span data-ttu-id="965f7-128">设置材料半透明度</span><span class="sxs-lookup"><span data-stu-id="965f7-128">Setting material translucency</span></span>

<span data-ttu-id="965f7-129">指示半透明材料应不受布隆或 DOF 影响。</span><span class="sxs-lookup"><span data-stu-id="965f7-129">Indicates that the translucent material should not be affected by bloom or DOF.</span></span> <span data-ttu-id="965f7-130">由于这两种影响都非常罕见，因此默认情况下此设置应处于启用状态。</span><span class="sxs-lookup"><span data-stu-id="965f7-130">Since both those effects are rare in MR, this setting should be on by default.</span></span>

![Unreal 中的移动单独半透明度设置](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a><span data-ttu-id="965f7-132">可选设置</span><span class="sxs-lookup"><span data-stu-id="965f7-132">Optional settings</span></span>

<span data-ttu-id="965f7-133">以下设置可能会提高性能，但请注意，它们会禁用某些功能。</span><span class="sxs-lookup"><span data-stu-id="965f7-133">The following settings may improve performance, but note that they disable certain features.</span></span> <span data-ttu-id="965f7-134">仅在您确定不需要相关功能时才使用这些设置。</span><span class="sxs-lookup"><span data-stu-id="965f7-134">Only use these settings if you are sure you don't need the features in question.</span></span>

![Unreal 中的可选材料设置](images/unreal-materials-img-06.jpg)

<span data-ttu-id="965f7-136">如果材料不需要反射或闪光，则设置此选项可显著提高性能。</span><span class="sxs-lookup"><span data-stu-id="965f7-136">If your material doesn't require reflections or shine, then setting this option can provide a tremendous performance boost.</span></span> <span data-ttu-id="965f7-137">在内部测试中，它的速度与 "unlit" 的速度一样快，同时提供照明信息。</span><span class="sxs-lookup"><span data-stu-id="965f7-137">In internal testing, it is as fast as "unlit" while providing lighting information.</span></span>

## <a name="best-practices"></a><span data-ttu-id="965f7-138">最佳实践</span><span class="sxs-lookup"><span data-stu-id="965f7-138">Best practices</span></span>

<span data-ttu-id="965f7-139">以下内容不是 "设置"，它们是与材料相关的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="965f7-139">The following are not "settings" as much as they are best practices related to Materials.</span></span>

<span data-ttu-id="965f7-140">创建参数时，最好尽可能使用 "静态参数"。</span><span class="sxs-lookup"><span data-stu-id="965f7-140">When creating parameters, prefer to use "Static Parameters" wherever possible.</span></span> <span data-ttu-id="965f7-141">静态开关可用于删除内容的整个分支，而不会产生运行时开销。</span><span class="sxs-lookup"><span data-stu-id="965f7-141">Static Switches can be used to remove an entire branch of a material with no runtime cost.</span></span> <span data-ttu-id="965f7-142">实例可以具有不同的值，从而使模板化着色器设置成为可能，而不会造成性能损失。</span><span class="sxs-lookup"><span data-stu-id="965f7-142">Instances can have different values, making it possible to have a templated shader setup with no performance loss.</span></span> <span data-ttu-id="965f7-143">不过，缺点在于，这会产生许多重新编译着色器的情况。</span><span class="sxs-lookup"><span data-stu-id="965f7-143">The downside, however, is that this creates many permutations that will cause a lot of shader recompilation.</span></span> <span data-ttu-id="965f7-144">尝试最大程度地减少材料中的静态参数数目，以及实际使用的这些静态参数的排列数。</span><span class="sxs-lookup"><span data-stu-id="965f7-144">Try to minimize the number of static parameters in the material and the number of permutations of those static parameters that are actually used.</span></span> <span data-ttu-id="965f7-145">在 [Unreal 引擎文档](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter)中，可以找到有关呈现材料参数的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="965f7-145">You can find more details on rendering material parameters in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span></span>

![材料设置最佳方案](images/unreal-materials-img-07.jpg)

<span data-ttu-id="965f7-147">创建材料实例时，应将首选项指定为在 "材料实例动态" 上的 " **材料实例常量** "。</span><span class="sxs-lookup"><span data-stu-id="965f7-147">When creating Material Instances, preference should be given to **Material Instance Constant** over Material Instance Dynamic.</span></span> <span data-ttu-id="965f7-148">"**材料实例常量**" 是一种在运行时之前只计算一次的实例材料。</span><span class="sxs-lookup"><span data-stu-id="965f7-148">**Material Instance Constant** is an instanced Material that calculates only once, prior to runtime.</span></span>

<span data-ttu-id="965f7-149">通过 "内容浏览器" 创建的材料实例 (**右键单击 > 创建材料实例** ，) 是一个材料实例常量。</span><span class="sxs-lookup"><span data-stu-id="965f7-149">The material instance created via the Content Browser (**right-click > Create Material Instance**) is a Material Instance Constant.</span></span> <span data-ttu-id="965f7-150">通过代码创建 "材料实例动态"。</span><span class="sxs-lookup"><span data-stu-id="965f7-150">Material Instance Dynamic are created via code.</span></span> <span data-ttu-id="965f7-151">有关详细信息，请 [参阅 Unreal 引擎文档](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)。</span><span class="sxs-lookup"><span data-stu-id="965f7-151">You can find more details on material instances in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span></span>

![在 Unreal 中创建材料实例](images/unreal-materials-img-08.png)

<span data-ttu-id="965f7-153">密切关注材料/着色器的复杂性。</span><span class="sxs-lookup"><span data-stu-id="965f7-153">Keep an eye on the complexity of your materials/shaders.</span></span> <span data-ttu-id="965f7-154">可以通过单击 "平台统计信息" 图标来查看各种平台上的材料成本。</span><span class="sxs-lookup"><span data-stu-id="965f7-154">You can view the cost of your Material on various platforms by clicking on the Platform Stats icon.</span></span> <span data-ttu-id="965f7-155">你还可以在 [Unreal 引擎文档](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)中找到有关材料的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="965f7-155">You can also find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![在 Unreal 中创建材料实例动态设置](images/unreal-materials-img-09.png)

<span data-ttu-id="965f7-157">您可以通过着色器复杂性 [视图模式](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)来快速了解着色器的相对复杂性。</span><span class="sxs-lookup"><span data-stu-id="965f7-157">You can get a quick idea of the relative complexity of your shader via the Shader Complexity [View mode](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).</span></span>

* <span data-ttu-id="965f7-158">查看模式热键： Alt + 8</span><span class="sxs-lookup"><span data-stu-id="965f7-158">View Mode Hotkey: Alt + 8</span></span>
* <span data-ttu-id="965f7-159">控制台命令： viewmode shadercomplexity</span><span class="sxs-lookup"><span data-stu-id="965f7-159">Console command: viewmode shadercomplexity</span></span>

![Unreal 中的材料复杂性](images/unreal-materials-img-10.png)

## <a name="see-also"></a><span data-ttu-id="965f7-161">请参阅</span><span class="sxs-lookup"><span data-stu-id="965f7-161">See also</span></span>
* [<span data-ttu-id="965f7-162">移动材料</span><span class="sxs-lookup"><span data-stu-id="965f7-162">Mobile materials</span></span>](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [<span data-ttu-id="965f7-163">查看模式</span><span class="sxs-lookup"><span data-stu-id="965f7-163">View modes</span></span>](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [<span data-ttu-id="965f7-164">材料实例</span><span class="sxs-lookup"><span data-stu-id="965f7-164">Material instances</span></span>](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
