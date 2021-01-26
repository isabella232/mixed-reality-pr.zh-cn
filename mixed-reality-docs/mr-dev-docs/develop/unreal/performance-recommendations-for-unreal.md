---
title: 针对 Unreal 的性能建议
description: 了解如何使用我们推荐的 Unreal 项目设置在混合现实应用中获得最佳性能。
author: hferrone
ms.author: safarooq
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 性能, 优化, 设置, 文档
ms.openlocfilehash: e956f12d27c826cff35e0b65957060953073a28b
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583066"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="a9826-104">针对 Unreal 的性能建议</span><span class="sxs-lookup"><span data-stu-id="a9826-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="a9826-105">Unreal Engine 具有多项可提高应用性能的功能，所有这些功能均基于[混合现实性能建议](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)概述的讨论内容。</span><span class="sxs-lookup"><span data-stu-id="a9826-105">Unreal Engine has several features that can increase an apps performance, all based on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span> <span data-ttu-id="a9826-106">建议在继续操作之前，先了解应用程序瓶颈和一般性能修复，以及有关分析和剖析混合现实应用的信息。</span><span class="sxs-lookup"><span data-stu-id="a9826-106">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="a9826-107">建议的 Unreal 项目设置</span><span class="sxs-lookup"><span data-stu-id="a9826-107">Recommended Unreal project settings</span></span>

<span data-ttu-id="a9826-108">可以在“编辑”>“项目设置”中找到以下每个设置。</span><span class="sxs-lookup"><span data-stu-id="a9826-108">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="a9826-109">使用移动 VR 呈现器：</span><span class="sxs-lookup"><span data-stu-id="a9826-109">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="a9826-110">滚动到“项目”部分，选择“目标硬件”，并将目标平台设置为“移动/平板电脑”</span><span class="sxs-lookup"><span data-stu-id="a9826-110">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![移动目标设置](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="a9826-112">使用前向呈现器：</span><span class="sxs-lookup"><span data-stu-id="a9826-112">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="a9826-113">由于前向呈现器具有众多可单独关闭的功能，因此比默认的延迟渲染管道更适用于混合现实。</span><span class="sxs-lookup"><span data-stu-id="a9826-113">Forward Renderer is much better for Mixed Reality than the default Deferred rendering pipeline because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="a9826-114">可以在 [Unreal 文档](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html)中找到详细信息。</span><span class="sxs-lookup"><span data-stu-id="a9826-114">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![前向呈现](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="a9826-116">使用移动多视图：</span><span class="sxs-lookup"><span data-stu-id="a9826-116">Using mobile multi-view:</span></span>
    * <span data-ttu-id="a9826-117">滚动到“引擎”部分，选择“呈现”，展开“VR”部分，同时启用“实例立体声”和“移动多视图”。</span><span class="sxs-lookup"><span data-stu-id="a9826-117">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="a9826-118">应取消选中移动端 HDR。</span><span class="sxs-lookup"><span data-stu-id="a9826-118">Mobile HDR should be unchecked.</span></span>

![VR 渲染设置](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="a9826-120">[仅 OpenXR] 请确保为“默认 RHI”选择了“默认值”或“D3D12”   。</span><span class="sxs-lookup"><span data-stu-id="a9826-120">**[OpenXR only]** Ensure **Default** or **D3D12** is the selected **Default RHI**:</span></span>
    * <span data-ttu-id="a9826-121">由于平台执行额外的渲染通道，因此选择 D3D11 将对性能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="a9826-121">Selecting **D3D11** will have a negative performance impact due to the platform performing an additional render pass.</span></span> <span data-ttu-id="a9826-122">D3D12 会改进渲染性能，同时避免额外的渲染通道。</span><span class="sxs-lookup"><span data-stu-id="a9826-122">**D3D12** should provide rendering performance improvements besides avoiding the additional render pass.</span></span>

![默认 RHI](images/unreal/performance-recommendations-img-09.png)

5. <span data-ttu-id="a9826-124">禁用顶点雾化：</span><span class="sxs-lookup"><span data-stu-id="a9826-124">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="a9826-125">顶点雾化在多边形中的每个顶点上应用雾化计算，然后将结果插入到多边形的整个面上。</span><span class="sxs-lookup"><span data-stu-id="a9826-125">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="a9826-126">如果游戏不使用雾化，建议禁用“顶点雾化”以提高着色性能。</span><span class="sxs-lookup"><span data-stu-id="a9826-126">If your game does not use fog, we recommend disabling Vertex Fogging to increase shading performance.</span></span>

![顶点雾化选项​​](images/unreal/performance-recommendations-img-05.png)

6. <span data-ttu-id="a9826-128">禁用遮挡剔除：</span><span class="sxs-lookup"><span data-stu-id="a9826-128">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="a9826-129">滚动到“引擎”部分，选择“呈现”，展开“剔除”部分，取消选中“遮挡剔除”。</span><span class="sxs-lookup"><span data-stu-id="a9826-129">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="a9826-130">如果需要对呈现的详细场景进行遮挡剔除，建议在“引擎”>“呈现”中启用“支持软件遮挡剔除” 。</span><span class="sxs-lookup"><span data-stu-id="a9826-130">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="a9826-131">Unreal 将在 CPU 上执行此操作，并避免 GPU 遮挡查询，后者在 HoloLens 2 上的执行效果不佳。</span><span class="sxs-lookup"><span data-stu-id="a9826-131">Unreal will do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="a9826-132">移动设备上 GPU 上的遮挡剔除速度缓慢。</span><span class="sxs-lookup"><span data-stu-id="a9826-132">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="a9826-133">通常，你希望 GPU 主要关注呈现。</span><span class="sxs-lookup"><span data-stu-id="a9826-133">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="a9826-134">如果你认为遮挡将有助于提高性能，请尝试改为启用软件遮挡。</span><span class="sxs-lookup"><span data-stu-id="a9826-134">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> 

> [!NOTE]
> <span data-ttu-id="a9826-135">如果你已受到大量绘图调用的 CPU 限制，则启用软件遮挡可能会使性能更差。</span><span class="sxs-lookup"><span data-stu-id="a9826-135">Enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![禁用遮挡剔除](images/unreal/performance-recommendations-img-02.png)

7. <span data-ttu-id="a9826-137">禁用自定义深度模具通道：</span><span class="sxs-lookup"><span data-stu-id="a9826-137">Disabling Custom Depth-Stencil Pass:</span></span>
    * <span data-ttu-id="a9826-138">禁用自定义深度模具需要额外的通道，这意味着其速度缓慢。</span><span class="sxs-lookup"><span data-stu-id="a9826-138">Disabling Custom Depth-Stencil requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="a9826-139">在 Unreal 上，半透明度功能也很慢。</span><span class="sxs-lookup"><span data-stu-id="a9826-139">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="a9826-140">可以在 [Unreal 文档](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html)中找到详细信息。</span><span class="sxs-lookup"><span data-stu-id="a9826-140">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![深度模板](images/unreal/performance-recommendations-img-06.png)

8. <span data-ttu-id="a9826-142">减少级联阴影映射：</span><span class="sxs-lookup"><span data-stu-id="a9826-142">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="a9826-143">减少阴影映射的数量将提高性能。</span><span class="sxs-lookup"><span data-stu-id="a9826-143">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="a9826-144">通常，应将属性设置为 1，除非存在明显质量不佳的情况。</span><span class="sxs-lookup"><span data-stu-id="a9826-144">Generally, you should set the property to 1 unless there's a visible quality loss.</span></span> 

![级联阴影映射](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="a9826-146">可选设置</span><span class="sxs-lookup"><span data-stu-id="a9826-146">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="a9826-147">以下设置可能会提高性能，但会以禁用某些功能为代价。</span><span class="sxs-lookup"><span data-stu-id="a9826-147">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="a9826-148">仅当你确定不需要使用这些功能时才使用这些设置。</span><span class="sxs-lookup"><span data-stu-id="a9826-148">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="a9826-149">移动着色器置换减少</span><span class="sxs-lookup"><span data-stu-id="a9826-149">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="a9826-150">如果光源不独立于相机移动，则可以安全地将属性设置为 0。</span><span class="sxs-lookup"><span data-stu-id="a9826-150">If your lights don't move independently of the camera, then you can safely set the property value to 0.</span></span> <span data-ttu-id="a9826-151">主要优点是它将允许 Unreal 剔除多个着色器置换，从而加快着色器的编译速度。</span><span class="sxs-lookup"><span data-stu-id="a9826-151">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![移动着色器置换减少](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="a9826-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="a9826-153">See also</span></span>

* [<span data-ttu-id="a9826-154">Unreal 引擎移动性能准则</span><span class="sxs-lookup"><span data-stu-id="a9826-154">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)