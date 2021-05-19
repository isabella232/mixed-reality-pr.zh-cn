---
title: 场景理解
description: 了解如何使用 HoloLens 的场景理解进行开发，包括 SDK、功能和常见使用方案。
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 场景理解、空间映射、Windows Mixed Reality、Unity、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、HoloLens、遮挡、SDK
ms.openlocfilehash: 06a4fdb6f3ad777c47151950acbd4ccdec9935ca
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143597"
---
# <a name="scene-understanding"></a><span data-ttu-id="6465c-104">场景理解</span><span class="sxs-lookup"><span data-stu-id="6465c-104">Scene understanding</span></span>

<span data-ttu-id="6465c-105">场景理解为混合现实开发人员提供了结构化的高级别环境表示形式，旨在直观地为环境感知型应用程序进行开发。</span><span class="sxs-lookup"><span data-stu-id="6465c-105">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="6465c-106">场景理解通过组合现有混合现实运行时（如高度准确但结构不太结构化的空间映射和新的 AI[](spatial-mapping.md)驱动运行时）的能力来实现此点。</span><span class="sxs-lookup"><span data-stu-id="6465c-106">Scene understanding does this by combining the power of existing mixed reality runtimes, like the highly accurate but less structured [spatial mapping](spatial-mapping.md) and new AI driven runtimes.</span></span> <span data-ttu-id="6465c-107">通过组合这些技术，场景理解可生成类似于 Unity 或 ARKit/ARCore 等框架中使用的三维环境的表示形式。</span><span class="sxs-lookup"><span data-stu-id="6465c-107">By combining these technologies, Scene understanding generates representations of 3D environments that are similar to those you may have used in frameworks such as Unity or ARKit/ARCore.</span></span> <span data-ttu-id="6465c-108">场景理解入口点从场景观察程序开始，应用程序调用它来计算新场景。</span><span class="sxs-lookup"><span data-stu-id="6465c-108">The Scene understanding entry point begins with a Scene Observer, which is called by your application to compute a new scene.</span></span> <span data-ttu-id="6465c-109">目前，该技术可以生成 3 个不同但相关的对象类别：</span><span class="sxs-lookup"><span data-stu-id="6465c-109">Today, the technology can generate 3 distinct but related object categories:</span></span>

* <span data-ttu-id="6465c-110">简化的 watertight 环境网格，可推断平面房间结构，且无杂乱</span><span class="sxs-lookup"><span data-stu-id="6465c-110">Simplified watertight environment meshes that infer the planar room structure without clutter</span></span>
* <span data-ttu-id="6465c-111">用于放置的平面区域，我们称之为四边形</span><span class="sxs-lookup"><span data-stu-id="6465c-111">Plane regions for placement that we call Quads</span></span>
* <span data-ttu-id="6465c-112">与 [所显示](spatial-mapping.md) Quads/Watertight 数据对齐的空间映射网格的快照</span><span class="sxs-lookup"><span data-stu-id="6465c-112">A snapshot of the [spatial mapping](spatial-mapping.md) mesh that aligns with the Quads/Watertight data that we surface</span></span>

![空间映射网格、带标签的平面图面、watertight 网格](images/SUScenarios.png)

<span data-ttu-id="6465c-114">本文档旨在提供方案概述，并阐明场景理解和空间映射共享的关系。</span><span class="sxs-lookup"><span data-stu-id="6465c-114">This document is intended to provide a scenario overview and to clarify the relationship that Scene understanding and Spatial mapping share.</span></span> <span data-ttu-id="6465c-115">若要了解场景理解的运行情况，请查看下面的设计 [全息影像 - 空间]() 感知视频演示：</span><span class="sxs-lookup"><span data-stu-id="6465c-115">If you'd like to see Scene Understanding in action, check out our [Designing Holograms - Spatial Awareness]() video demo below:</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="6465c-116">使用场景理解进行开发</span><span class="sxs-lookup"><span data-stu-id="6465c-116">Developing with Scene Understanding</span></span>

<span data-ttu-id="6465c-117">本文仅介绍场景理解运行时和概念。</span><span class="sxs-lookup"><span data-stu-id="6465c-117">This article only serves to introduce the Scene Understanding runtime and concepts.</span></span> <span data-ttu-id="6465c-118">如果你正在寻找有关如何使用场景理解进行开发的文档，你可能对以下文章感兴趣：</span><span class="sxs-lookup"><span data-stu-id="6465c-118">If you're looking for documentation on how to develop with Scene Understanding, you may be interested in the following articles:</span></span>

[<span data-ttu-id="6465c-119">场景理解 SDK 概述</span><span class="sxs-lookup"><span data-stu-id="6465c-119">Scene Understanding SDK overview</span></span>](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

<span data-ttu-id="6465c-120">可以从示例 GitHub 站点下载场景理解示例应用：</span><span class="sxs-lookup"><span data-stu-id="6465c-120">You can download the Scene Understanding Sample app from the sample GitHub site:</span></span>

[<span data-ttu-id="6465c-121">场景理解示例</span><span class="sxs-lookup"><span data-stu-id="6465c-121">Scene Understanding Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

<span data-ttu-id="6465c-122">如果你没有设备，并且想要访问示例场景来尝试了解场景，示例资产文件夹中有一些场景：</span><span class="sxs-lookup"><span data-stu-id="6465c-122">If you don't have a device and wish to access sample scenes to try Scene Understanding out, there are scenes in the sample asset folder:</span></span>

[<span data-ttu-id="6465c-123">场景了解示例场景</span><span class="sxs-lookup"><span data-stu-id="6465c-123">Scene Understanding Sample Scenes</span></span>](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a><span data-ttu-id="6465c-124">SDK 中 IsInRole 中的声明</span><span class="sxs-lookup"><span data-stu-id="6465c-124">SDK</span></span>

<span data-ttu-id="6465c-125">如果正在寻找有关通过场景理解进行开发的特定详细信息，请参阅 [场景了解 SDK 概述](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) 文档。</span><span class="sxs-lookup"><span data-stu-id="6465c-125">If you're looking for specific details on developing with Scene Understanding, see the [Scene Understanding SDK overview](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) documentation.</span></span>

### <a name="sample"></a><span data-ttu-id="6465c-126">示例</span><span class="sxs-lookup"><span data-stu-id="6465c-126">Sample</span></span>

## <a name="device-support"></a><span data-ttu-id="6465c-127">设备支持</span><span class="sxs-lookup"><span data-stu-id="6465c-127">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="6465c-128"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="6465c-128"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="6465c-129"><a href="/hololens/hololens1-hardware"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="6465c-129"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="6465c-130"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="6465c-130"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="6465c-131"><a href="../discover/immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="6465c-131"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6465c-132">场景理解</span><span class="sxs-lookup"><span data-stu-id="6465c-132">Scene understanding</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="6465c-133">✔️</span><span class="sxs-lookup"><span data-stu-id="6465c-133">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a><span data-ttu-id="6465c-134">常见使用方案</span><span class="sxs-lookup"><span data-stu-id="6465c-134">Common usage scenarios</span></span>

<span data-ttu-id="6465c-135">![常见空间映射使用方案的插图：放置、封闭、物理学和导航](images/sm-concepts-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6465c-135">![Illustrations of common Spatial mapping usage scenarios: Placement, Occlusion, Physics and Navigation](images/sm-concepts-1000px.png)</span></span><br>
<span data-ttu-id="6465c-136">*常见的空间映射使用方案：放置、封闭、物理学和导航。*</span><span class="sxs-lookup"><span data-stu-id="6465c-136">*Common spatial mapping usage scenarios: placement, occlusion, physics, and navigation.*</span></span>

<br>

<span data-ttu-id="6465c-137">环境感知应用程序的许多核心方案可通过空间映射和场景理解进行寻址。</span><span class="sxs-lookup"><span data-stu-id="6465c-137">Many of the core scenarios for environmentally aware applications can be addressed by both Spatial mapping and Scene understanding.</span></span> <span data-ttu-id="6465c-138">这些核心方案包括放置、封闭、物理学等。</span><span class="sxs-lookup"><span data-stu-id="6465c-138">These core scenarios include placement, occlusion, physics, and so on.</span></span> <span data-ttu-id="6465c-139">场景理解和空间映射之间的核心差异是对结构和简易性的最大准确性和延迟的折衷。</span><span class="sxs-lookup"><span data-stu-id="6465c-139">A core difference between Scene understanding and Spatial mapping is a tradeoff of maximal accuracy and latency to structure and simplicity.</span></span> <span data-ttu-id="6465c-140">如果你的应用程序需要可能的最低延迟时间和只需要访问的网格三角形，请直接使用空间映射。</span><span class="sxs-lookup"><span data-stu-id="6465c-140">If your application requires the lowest-latency possible and mesh triangles that only you'll want to access, use Spatial Mapping directly.</span></span> <span data-ttu-id="6465c-141">如果要执行更高级的处理，则可以考虑切换到场景理解模型，因为它应提供功能的超集。</span><span class="sxs-lookup"><span data-stu-id="6465c-141">If you're doing higher-level processing, you may consider switching to the Scene understanding model as it should provide you with a superset of functionality.</span></span> <span data-ttu-id="6465c-142">您始终可以访问最完整且准确的空间映射数据，因为场景理解会提供空间映射网格的快照作为其表示形式的一部分。</span><span class="sxs-lookup"><span data-stu-id="6465c-142">You'll always have access to the most complete and accurate spatial mapping data possible because Scene understanding provides a snapshot of the spatial mapping mesh as part of its representation.</span></span>

<span data-ttu-id="6465c-143">以下部分将在新的场景理解 SDK 的上下文中重新访问核心空间映射方案。</span><span class="sxs-lookup"><span data-stu-id="6465c-143">The following sections revisit the core spatial mapping scenarios in the context of the new Scene understanding SDK.</span></span>

### <a name="placement"></a><span data-ttu-id="6465c-144">放置</span><span class="sxs-lookup"><span data-stu-id="6465c-144">Placement</span></span>

<span data-ttu-id="6465c-145">场景理解提供旨在简化放置方案的新构造。</span><span class="sxs-lookup"><span data-stu-id="6465c-145">Scene understanding provides new constructs designed to simplify placement scenarios.</span></span> <span data-ttu-id="6465c-146">场景可以计算称为 SceneQuads 的基元，它们描述了可放置全息影像的平面面。</span><span class="sxs-lookup"><span data-stu-id="6465c-146">A scene can compute primitives called SceneQuads, which describe flat surfaces on which holograms can be placed.</span></span> <span data-ttu-id="6465c-147">SceneQuads 围绕放置而设计，描述了二维图面，并提供了一个用于放置在该表面上的 API。</span><span class="sxs-lookup"><span data-stu-id="6465c-147">SceneQuads have been designed around placement and describe a 2D surface and provide an API for placement on that surface.</span></span> <span data-ttu-id="6465c-148">以前，当使用三角形网格进行放置时，必须扫描四个部分的所有区域，执行孔填充/后处理来识别对象放置的好位置。</span><span class="sxs-lookup"><span data-stu-id="6465c-148">Previously, when using the triangle mesh to do placement, one had to scan all areas of the quad and do hole filling/post-processing to identify good locations for object placement.</span></span> <span data-ttu-id="6465c-149">对于四边形，这并不总是必需的，因为场景了解运行时可推断哪些故障区域未扫描，并使不属于图面的区域无效。</span><span class="sxs-lookup"><span data-stu-id="6465c-149">This isn't always necessary with Quads, as the Scene understanding runtime infers which quad areas weren't scanned, and invalidate areas that aren't part of the surface.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="6465c-150">![已禁用推理，并捕获扫描区域的放置区域 SceneQuads。](images/SUQuads.png)</span><span class="sxs-lookup"><span data-stu-id="6465c-150">![SceneQuads with inference disabled, capturing placement areas for scanned regions.](images/SUQuads.png)</span></span><br>
       <span data-ttu-id="6465c-151">已禁用 SceneQuads 的 **图像 #1** ，并捕获扫描区域的放置区。</span><span class="sxs-lookup"><span data-stu-id="6465c-151">**Image #1** - SceneQuads with inference disabled, capturing placement areas for scanned regions.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="6465c-152">![四边形启用了推理后，放置不再局限于扫描区域。](images/SUWatertight.png)</span><span class="sxs-lookup"><span data-stu-id="6465c-152">![Quads with inference enabled, placement is no longer limited to scanned areas.](images/SUWatertight.png)</span></span><br>
        <span data-ttu-id="6465c-153">**图像 #2** -启用了推理的四边形，放置不再局限于扫描区域。</span><span class="sxs-lookup"><span data-stu-id="6465c-153">**Image #2** - Quads with inference enabled, placement is no longer limited to scanned areas.</span></span>
    :::column-end:::
:::row-end:::

<br>


<span data-ttu-id="6465c-154">如果你的应用程序想要将二维或3D 全息图放置在环境的严格结构上，最好是从 [空间映射](spatial-mapping.md) 网格计算此信息。</span><span class="sxs-lookup"><span data-stu-id="6465c-154">If your application intends to place 2D or 3D holograms on rigid structures of your environment, the simplicity and convenience of SceneQuads for placement is preferable to computing this information from the [spatial mapping](spatial-mapping.md) mesh.</span></span> <span data-ttu-id="6465c-155">有关此主题的详细信息，请参阅 [场景了解 SDK 参考](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)</span><span class="sxs-lookup"><span data-stu-id="6465c-155">For more information on this topic, see the [Scene understanding SDK reference](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)</span></span>

<span data-ttu-id="6465c-156">**注意** 对于依赖于空间映射网格的传统放置代码，可以通过设置 EnableWorldMesh 设置与 SceneQuads 一起计算空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="6465c-156">**Note** For legacy placement code that depends on the spatial mapping mesh, the spatial mapping mesh can be computed along with SceneQuads by setting EnableWorldMesh setting.</span></span> <span data-ttu-id="6465c-157">如果场景理解 API 不满足应用程序的延迟要求，我们建议继续使用 [空间映射 API](spatial-mapping.md#placement)。</span><span class="sxs-lookup"><span data-stu-id="6465c-157">If Scene understanding API doesn't satisfy your application's latency requirements, we recommend you continue to use the [Spatial mapping API](spatial-mapping.md#placement).</span></span>

### <a name="occlusion"></a><span data-ttu-id="6465c-158">封闭</span><span class="sxs-lookup"><span data-stu-id="6465c-158">Occlusion</span></span>

<span data-ttu-id="6465c-159">[空间映射封闭](spatial-mapping.md#occlusion) 仍是捕获环境的实时状态的最小延迟方式。</span><span class="sxs-lookup"><span data-stu-id="6465c-159">[Spatial mapping occlusion](spatial-mapping.md#occlusion) remains the least latent way to capture the real-time state of the environment.</span></span> <span data-ttu-id="6465c-160">虽然这对于在高度动态的场景中提供封闭可能很有用，但出于多种原因，你可能希望考虑到封闭的场景理解。</span><span class="sxs-lookup"><span data-stu-id="6465c-160">Though this may be useful to provide occlusion in highly dynamic scenes, you may wish to consider Scene understanding for occlusion for several reasons.</span></span> <span data-ttu-id="6465c-161">如果使用通过场景理解生成的空间映射网格，则可以从空间映射请求数据，这些数据不会存储在本地缓存中，也不能从感知 Api 获得。</span><span class="sxs-lookup"><span data-stu-id="6465c-161">If you use the spatial mapping mesh generated by Scene Understanding, you can request data from spatial mapping that wouldn't be stored in the local cache and isn't available from the perception APIs.</span></span> <span data-ttu-id="6465c-162">使用封闭和 watertight 网格的空间映射将提供额外的价值，特别是完成了未扫描的空间结构。</span><span class="sxs-lookup"><span data-stu-id="6465c-162">Using Spatial Mapping for occlusion alongside watertight meshes will provide extra value, specifically completion of unscanned room structure.</span></span>

<span data-ttu-id="6465c-163">如果你的要求可以容忍场景理解的延迟增加，应用程序开发人员应考虑使用场景理解 watertight 网格，以及与平面表示形式一致的空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="6465c-163">If your requirements can tolerate the increased latency of Scene understanding, application developers should consider using the Scene understanding watertight mesh, and the spatial mapping mesh in unison with planar representations.</span></span> <span data-ttu-id="6465c-164">这将提供"两全其美"方案，其中简化的 watertight 遮挡通过更精细的非平面几何图形进行渗透，从而尽可能提供最真实的遮挡贴图。</span><span class="sxs-lookup"><span data-stu-id="6465c-164">This would provide a "best of both worlds" scenario where simplified watertight occlusion is married with finer nonplanar geometry providing the most realistic occlusion maps possible.</span></span>

### <a name="physics"></a><span data-ttu-id="6465c-165">物理</span><span class="sxs-lookup"><span data-stu-id="6465c-165">Physics</span></span>

<span data-ttu-id="6465c-166">场景理解会生成使用语义分解空间的 watertight 网格，专门用于解决空间映射网格施加的许多物理限制。</span><span class="sxs-lookup"><span data-stu-id="6465c-166">Scene understanding generates watertight meshes that decompose space with semantics, specifically to address many limitations to physics that spatial mapping meshes impose.</span></span> <span data-ttu-id="6465c-167">Watertight 结构可确保始终命中物理光线投射，语义分解允许更简单地生成用于室内导航的导航网格。</span><span class="sxs-lookup"><span data-stu-id="6465c-167">Watertight structures ensure physics ray casts always hit, and semantic decomposition allows for simpler generation of nav meshes for indoor navigation.</span></span> <span data-ttu-id="6465c-168">如有关遮挡 [的部分](#occlusion)中所述，使用 EnableSceneObjectMeshes 和 EnableWorldMesh 创建场景将生成尽可能完整的物理网格。</span><span class="sxs-lookup"><span data-stu-id="6465c-168">As described in the section on [occlusion](#occlusion), creating a scene with EnableSceneObjectMeshes and EnableWorldMesh will produce the most physically complete mesh possible.</span></span> <span data-ttu-id="6465c-169">环境网格的 watertight 属性可防止命中测试无法命中表面。</span><span class="sxs-lookup"><span data-stu-id="6465c-169">The watertight property of the environment mesh prevents hit tests from failing to hit surfaces.</span></span> <span data-ttu-id="6465c-170">网格数据将确保物理与场景中的所有对象交互，而不只是房间结构。</span><span class="sxs-lookup"><span data-stu-id="6465c-170">The mesh data will ensure physics are interacting with all objects in the scene and not just the room structure.</span></span>

### <a name="navigation"></a><span data-ttu-id="6465c-171">导航</span><span class="sxs-lookup"><span data-stu-id="6465c-171">Navigation</span></span>

<span data-ttu-id="6465c-172">由语义类分解的平面网格是导航和路径规划的理想构造，可缓解空间映射导航概述 [中所述的许多](spatial-mapping.md#navigation) 问题。</span><span class="sxs-lookup"><span data-stu-id="6465c-172">Planar meshes decomposed by semantic class are ideal constructs for navigation and path planning, easing many of the issues described in the [Spatial mapping navigation](spatial-mapping.md#navigation) overview.</span></span> <span data-ttu-id="6465c-173">场景中计算的 SceneMesh 对象由表面类型取消组合，确保导航网格生成仅限于可进行演练的图面。</span><span class="sxs-lookup"><span data-stu-id="6465c-173">The SceneMesh objects computed in the scene are de-composed by surface type ensuring that nav-mesh generation is limited to surfaces that can be walked on.</span></span> <span data-ttu-id="6465c-174">由于地面结构的简单性，3D 引擎（如 Unity）中的动态导航网格生成取决于实时要求。</span><span class="sxs-lookup"><span data-stu-id="6465c-174">Because of the floor structures' simplicity, dynamic nav-mesh generation in 3d engines such as Unity are attainable depending on real-time requirements.</span></span>

<span data-ttu-id="6465c-175">生成准确的导航网格目前仍然需要后期处理，即应用程序仍必须将遮挡器项目到楼层，以确保导航不会通过混乱/表等。</span><span class="sxs-lookup"><span data-stu-id="6465c-175">Generating accurate nav-meshes currently still requires post-processing, namely applications must still project occluders on to the floor to ensure that navigation doesn't pass through clutter/tables and so on.</span></span> <span data-ttu-id="6465c-176">实现此目的的最准确方法就是预测世界网格数据，如果场景是使用 EnableWorldMesh 标志计算的，则提供该数据。</span><span class="sxs-lookup"><span data-stu-id="6465c-176">The most accurate way to accomplish this is to project the world mesh data, which is provided if the scene is computed with the EnableWorldMesh flag.</span></span>

### <a name="visualization"></a><span data-ttu-id="6465c-177">可视化效果</span><span class="sxs-lookup"><span data-stu-id="6465c-177">Visualization</span></span>

<span data-ttu-id="6465c-178">虽然 [空间](spatial-mapping.md#visualization) 映射可视化可用于环境实时反馈，但在许多情况下，平面对象和 watertight 对象的简单性提供了更多的性能或视觉质量。</span><span class="sxs-lookup"><span data-stu-id="6465c-178">While [spatial mapping visualization](spatial-mapping.md#visualization) can be used for real-time feedback of the environment, there are many scenarios where the simplicity of planar and watertight objects provides more performance or visual quality.</span></span> <span data-ttu-id="6465c-179">如果投影在四边形网格或平面水台网格提供的平面图面上，则使用空间映射描述的阴影投影和地面技术可能更美观。</span><span class="sxs-lookup"><span data-stu-id="6465c-179">Shadow projection and grounding techniques that are described using spatial mapping may be more pleasing if projected on the planar surfaces provided by Quads or the planar watertight mesh.</span></span> <span data-ttu-id="6465c-180">对于环境/方案尤其如此，因为场景将推断出全面预扫描，而完整的环境和平面假设将最大程度地减少项目。</span><span class="sxs-lookup"><span data-stu-id="6465c-180">This is especially true for environments/scenarios where thorough pre-scanning isn't optimal because the scene will infer, and complete environments and planar assumptions will minimize artifacts.</span></span>

<span data-ttu-id="6465c-181">此外，空间映射返回的图面总数受内部空间缓存限制，而场景理解的空间映射网格版本可以访问未缓存的空间映射数据。</span><span class="sxs-lookup"><span data-stu-id="6465c-181">Additionally, the total number of surfaces returned by Spatial Mapping is limited by the internal spatial cache, while Scene understanding's version of the Spatial Mapping mesh can access spatial mapping data that isn't cached.</span></span> <span data-ttu-id="6465c-182">因此，场景理解更适用于捕获较大空间的网格表示形式 (例如，大于单个房间) 可视化或进一步网格处理。</span><span class="sxs-lookup"><span data-stu-id="6465c-182">Because of this, Scene understanding is more suited to capturing mesh representations for larger spaces (for example, larger than a single room) for visualization or further mesh processing.</span></span> <span data-ttu-id="6465c-183">使用 EnableWorldMesh 返回世界网格将始终具有一致的详细级别，如果呈现为线框，则可能会生成更美观的可视化效果。</span><span class="sxs-lookup"><span data-stu-id="6465c-183">The world mesh returned with EnableWorldMesh will have a consistent level of detail throughout, which may yield a more pleasing visualization if rendered as wireframe.</span></span>

### <a name="see-also"></a><span data-ttu-id="6465c-184">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6465c-184">See Also</span></span>

* [<span data-ttu-id="6465c-185">场景理解 SDK</span><span class="sxs-lookup"><span data-stu-id="6465c-185">Scene understanding SDK</span></span>](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [<span data-ttu-id="6465c-186">空间映射</span><span class="sxs-lookup"><span data-stu-id="6465c-186">Spatial mapping</span></span>](spatial-mapping.md)