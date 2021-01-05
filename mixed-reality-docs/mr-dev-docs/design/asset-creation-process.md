---
title: 资产创建过程
description: 有关为混合现实体验创建资产的指导。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: 资产，创建，处理，预算，多边形，纹理，着色器，性能，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，资产
ms.openlocfilehash: 2089ac7a870d9b4b13d314774d6d6124b78bb15c
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847547"
---
# <a name="asset-creation-process"></a><span data-ttu-id="2816b-104">资产创建过程</span><span class="sxs-lookup"><span data-stu-id="2816b-104">Asset creation process</span></span>

<span data-ttu-id="2816b-105">Windows Mixed Reality 构建于 Microsoft 投入了 DirectX 的数十年中。</span><span class="sxs-lookup"><span data-stu-id="2816b-105">Windows Mixed Reality builds on the decades of investment Microsoft has made into DirectX.</span></span> <span data-ttu-id="2816b-106">开发人员构建三维图形的所有经验和技能都将继续对 HoloLens 有价值。</span><span class="sxs-lookup"><span data-stu-id="2816b-106">All of the experience and skills developers have with building 3D graphics continues to be valuable with HoloLens.</span></span>

<span data-ttu-id="2816b-107">你为项目创建的资产分为多个形状和窗体。</span><span class="sxs-lookup"><span data-stu-id="2816b-107">The assets you create for a project come in many shapes and forms.</span></span> <span data-ttu-id="2816b-108">它们可由一系列纹理/图像、音频、视频、3D 模型和动画组成。</span><span class="sxs-lookup"><span data-stu-id="2816b-108">They can be composed of a series of textures/images, audio, video, 3D models, and animations.</span></span> <span data-ttu-id="2816b-109">我们无法开始涵盖可用于创建项目中使用的不同类型资产的所有工具。</span><span class="sxs-lookup"><span data-stu-id="2816b-109">We can't begin to cover all the tools that are available to create the different types of assets used in a project.</span></span> <span data-ttu-id="2816b-110">对于本文，我们将重点介绍3D 资产创建方法。</span><span class="sxs-lookup"><span data-stu-id="2816b-110">For this article, we'll focus on 3D asset creation methods.</span></span>

<span data-ttu-id="2816b-111">![概念、创建、集成和迭代流](images/concept-creation-integration-iteration-flow-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="2816b-111">![Concept, creation, integration and iteration flow](images/concept-creation-integration-iteration-flow-640px.jpg)</span></span><br>
<span data-ttu-id="2816b-112">*概念、创建、集成和迭代流*</span><span class="sxs-lookup"><span data-stu-id="2816b-112">*Concept, creation, integration, and iteration flow*</span></span>

## <a name="things-to-consider"></a><span data-ttu-id="2816b-113">注意事项</span><span class="sxs-lookup"><span data-stu-id="2816b-113">Things to consider</span></span>

<span data-ttu-id="2816b-114">在观看经验时，您要尝试创建，将其视为可用于尝试创建最佳体验的 **预算** 。</span><span class="sxs-lookup"><span data-stu-id="2816b-114">When looking at the experience, you're trying to create,  think of it as a **budget** that you can spend to try to create the best experience.</span></span> <span data-ttu-id="2816b-115">对于可以在资产中使用的 **多边形** 数量或 **材料类型** ，不一定有任何硬性限制。</span><span class="sxs-lookup"><span data-stu-id="2816b-115">There aren't necessarily any hard limits on the number of **polygons** or **material types** you can use in your assets.</span></span> <span data-ttu-id="2816b-116">将其视为一组预算的折衷。</span><span class="sxs-lookup"><span data-stu-id="2816b-116">Think of it more as a budgeted set of tradeoffs.</span></span>

<span data-ttu-id="2816b-117">下面是你的体验的示例预算。</span><span class="sxs-lookup"><span data-stu-id="2816b-117">Below is an example budget for your experience.</span></span> <span data-ttu-id="2816b-118">性能不是单一故障点，而是通过几千次切削停止。</span><span class="sxs-lookup"><span data-stu-id="2816b-118">Performance isn't a single point of failure, but death by a thousand cuts.</span></span>
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><span data-ttu-id="2816b-119"><b>资产</b></span><span class="sxs-lookup"><span data-stu-id="2816b-119"><b>Assets</b></span></span></th><th style="text-align:right;"> <span data-ttu-id="2816b-120">CPU</span><span class="sxs-lookup"><span data-stu-id="2816b-120">CPU</span></span></th><th> <span data-ttu-id="2816b-121">GPU</span><span class="sxs-lookup"><span data-stu-id="2816b-121">GPU</span></span></th><th> <span data-ttu-id="2816b-122">内存</span><span class="sxs-lookup"><span data-stu-id="2816b-122">Memory</span></span></th>
</tr><tr>
<td> <span data-ttu-id="2816b-123">Polygon（多边形）</span><span class="sxs-lookup"><span data-stu-id="2816b-123">Polygons</span></span></td><td> <span data-ttu-id="2816b-124">0%</span><span class="sxs-lookup"><span data-stu-id="2816b-124">0%</span></span></td><td> <span data-ttu-id="2816b-125">5%</span><span class="sxs-lookup"><span data-stu-id="2816b-125">5%</span></span></td><td> <span data-ttu-id="2816b-126">10%</span><span class="sxs-lookup"><span data-stu-id="2816b-126">10%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2816b-127">纹理</span><span class="sxs-lookup"><span data-stu-id="2816b-127">Textures</span></span></td><td> <span data-ttu-id="2816b-128">5%</span><span class="sxs-lookup"><span data-stu-id="2816b-128">5%</span></span></td><td> <span data-ttu-id="2816b-129">15%</span><span class="sxs-lookup"><span data-stu-id="2816b-129">15%</span></span></td><td><span data-ttu-id="2816b-130">25%</span><span class="sxs-lookup"><span data-stu-id="2816b-130">25%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2816b-131">着色器</span><span class="sxs-lookup"><span data-stu-id="2816b-131">Shaders</span></span></td><td> <span data-ttu-id="2816b-132">15%</span><span class="sxs-lookup"><span data-stu-id="2816b-132">15%</span></span></td><td> <span data-ttu-id="2816b-133">35%</span><span class="sxs-lookup"><span data-stu-id="2816b-133">35%</span></span></td><td> <span data-ttu-id="2816b-134">0%</span><span class="sxs-lookup"><span data-stu-id="2816b-134">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2816b-135"><b>Dynamics</b></span><span class="sxs-lookup"><span data-stu-id="2816b-135"><b>Dynamics</b></span></span></td><td></td><td></td><td></td>
</tr><tr>
<td> <span data-ttu-id="2816b-136">物理</span><span class="sxs-lookup"><span data-stu-id="2816b-136">Physics</span></span></td><td> <span data-ttu-id="2816b-137">5%</span><span class="sxs-lookup"><span data-stu-id="2816b-137">5%</span></span></td><td> <span data-ttu-id="2816b-138">15%</span><span class="sxs-lookup"><span data-stu-id="2816b-138">15%</span></span></td><td> <span data-ttu-id="2816b-139">0%</span><span class="sxs-lookup"><span data-stu-id="2816b-139">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2816b-140">实时照明</span><span class="sxs-lookup"><span data-stu-id="2816b-140">Real-time lighting</span></span></td><td> <span data-ttu-id="2816b-141">10%</span><span class="sxs-lookup"><span data-stu-id="2816b-141">10%</span></span></td><td> <span data-ttu-id="2816b-142">0%</span><span class="sxs-lookup"><span data-stu-id="2816b-142">0%</span></span></td><td> <span data-ttu-id="2816b-143">0%</span><span class="sxs-lookup"><span data-stu-id="2816b-143">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2816b-144">Media (音频/视频) </span><span class="sxs-lookup"><span data-stu-id="2816b-144">Media (audio/video)</span></span></td><td> -</td><td> <span data-ttu-id="2816b-145">15%</span><span class="sxs-lookup"><span data-stu-id="2816b-145">15%</span></span></td><td> <span data-ttu-id="2816b-146">25%</span><span class="sxs-lookup"><span data-stu-id="2816b-146">25%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2816b-147">脚本/逻辑</span><span class="sxs-lookup"><span data-stu-id="2816b-147">Script/logic</span></span></td><td> <span data-ttu-id="2816b-148">25%</span><span class="sxs-lookup"><span data-stu-id="2816b-148">25%</span></span></td><td> <span data-ttu-id="2816b-149">0%</span><span class="sxs-lookup"><span data-stu-id="2816b-149">0%</span></span></td><td> <span data-ttu-id="2816b-150">5%</span><span class="sxs-lookup"><span data-stu-id="2816b-150">5%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2816b-151">一般开销</span><span class="sxs-lookup"><span data-stu-id="2816b-151">General overhead</span></span></td><td> <span data-ttu-id="2816b-152">5%</span><span class="sxs-lookup"><span data-stu-id="2816b-152">5%</span></span></td><td> <span data-ttu-id="2816b-153">5%</span><span class="sxs-lookup"><span data-stu-id="2816b-153">5%</span></span></td><td> <span data-ttu-id="2816b-154">5%</span><span class="sxs-lookup"><span data-stu-id="2816b-154">5%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2816b-155"><b>总计</b></span><span class="sxs-lookup"><span data-stu-id="2816b-155"><b>Total</b></span></span></td><td> <span data-ttu-id="2816b-156"><b>65%</b></span><span class="sxs-lookup"><span data-stu-id="2816b-156"><b>65%</b></span></span></td><td> <span data-ttu-id="2816b-157"><b>90%</b></span><span class="sxs-lookup"><span data-stu-id="2816b-157"><b>90%</b></span></span></td><td> <span data-ttu-id="2816b-158"><b>70%</b></span><span class="sxs-lookup"><span data-stu-id="2816b-158"><b>70%</b></span></span></td>
</tr>
</table>

<span data-ttu-id="2816b-159">**资产总数**</span><span class="sxs-lookup"><span data-stu-id="2816b-159">**Total number of assets**</span></span>
* <span data-ttu-id="2816b-160">场景中有多少资产处于活动状态？</span><span class="sxs-lookup"><span data-stu-id="2816b-160">How many assets are active in the scene?</span></span>

<span data-ttu-id="2816b-161">**资产复杂性**</span><span class="sxs-lookup"><span data-stu-id="2816b-161">**Complexity of assets**</span></span>
* <span data-ttu-id="2816b-162">三角形/多边形有多少？</span><span class="sxs-lookup"><span data-stu-id="2816b-162">How many triangles / polygons?</span></span>
* <span data-ttu-id="2816b-163">着色器的复杂程度如何？</span><span class="sxs-lookup"><span data-stu-id="2816b-163">How complex is the shader?</span></span> <span data-ttu-id="2816b-164">使用混合现实工具包时，建议使用 [混合现实工具包标准着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) 来降低着色器的复杂性。</span><span class="sxs-lookup"><span data-stu-id="2816b-164">When using the Mixed Reality Toolkit, it's recommended to use the [Mixed Reality Toolkit Standard shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) to reduce shader complexity.</span></span>

<span data-ttu-id="2816b-165">开发人员和艺术家都必须考虑设备和图形引擎的功能。</span><span class="sxs-lookup"><span data-stu-id="2816b-165">Both the developers and artists have to consider the capabilities of the device and the graphics engine.</span></span> <span data-ttu-id="2816b-166">Microsoft HoloLens 包含内置于设备中的所有计算和图形。</span><span class="sxs-lookup"><span data-stu-id="2816b-166">Microsoft HoloLens has all of the computational and graphics built into the device.</span></span> <span data-ttu-id="2816b-167">它共享开发人员在移动平台上所能找到的功能。</span><span class="sxs-lookup"><span data-stu-id="2816b-167">It shares the capabilities developers would find on a mobile platform.</span></span>

<span data-ttu-id="2816b-168">无论你的体验面向的是 [全息设备还是沉浸式设备](../discover/mixed-reality.md#the-mixed-reality-spectrum)，资产创建过程都是相同的。</span><span class="sxs-lookup"><span data-stu-id="2816b-168">The asset creation process is the same whether your experience targets a [holographic device or an immersive device](../discover/mixed-reality.md#the-mixed-reality-spectrum).</span></span> <span data-ttu-id="2816b-169">需要注意的主要事项是设备功能和规模。</span><span class="sxs-lookup"><span data-stu-id="2816b-169">The primary thing to note is the device capability and scale.</span></span> <span data-ttu-id="2816b-170">您可以在混合现实中看到现实世界，因此您需要根据经验来维护正确的规模。</span><span class="sxs-lookup"><span data-stu-id="2816b-170">You can see the real world in mixed reality, so you'll want to maintain the correct scale based on the experience.</span></span>

## <a name="authoring-assets"></a><span data-ttu-id="2816b-171">创作资产</span><span class="sxs-lookup"><span data-stu-id="2816b-171">Authoring assets</span></span>

<span data-ttu-id="2816b-172">首先，我们将介绍如何获取项目的资产：</span><span class="sxs-lookup"><span data-stu-id="2816b-172">We'll start with the ways to get assets for your project:</span></span>
1. <span data-ttu-id="2816b-173">创建资产 (创作工具和对象捕获) </span><span class="sxs-lookup"><span data-stu-id="2816b-173">Creating Assets (Authoring tools and object capture)</span></span>
2. <span data-ttu-id="2816b-174">采购资产 (在线购买资产) </span><span class="sxs-lookup"><span data-stu-id="2816b-174">Purchasing Assets (Buying assets online)</span></span>
3. <span data-ttu-id="2816b-175">迁移资产 (获取现有资产) </span><span class="sxs-lookup"><span data-stu-id="2816b-175">Porting Assets (Taking existing assets)</span></span>
4. <span data-ttu-id="2816b-176">外包资产 (从第三方导入资产) </span><span class="sxs-lookup"><span data-stu-id="2816b-176">Outsourcing Assets (Importing assets from third parties)</span></span>

### <a name="creating-assets"></a><span data-ttu-id="2816b-177">创建资产</span><span class="sxs-lookup"><span data-stu-id="2816b-177">Creating assets</span></span>

<span data-ttu-id="2816b-178">**创作工具**</span><span class="sxs-lookup"><span data-stu-id="2816b-178">**Authoring tools**</span></span><br>
<span data-ttu-id="2816b-179">首先，你可以通过几种不同的方式创建自己的资产。</span><span class="sxs-lookup"><span data-stu-id="2816b-179">First you can create your own assets in several different ways.</span></span> <span data-ttu-id="2816b-180">3D 艺术家使用各种应用程序和工具来创建模型，其中包括 **网格**、 **纹理** 和 **材料**。</span><span class="sxs-lookup"><span data-stu-id="2816b-180">3D artists use various applications and tools to create models, which consist of **meshes**, **textures**, and **materials**.</span></span> <span data-ttu-id="2816b-181">然后以文件格式保存该文件，应用程序使用的图形引擎可以导入或使用该格式，如 **。FBX** 或 **。OBJ**。</span><span class="sxs-lookup"><span data-stu-id="2816b-181">This is then saved in a file format that can be imported or used by the graphics engine used by the app, such as **.FBX** or **.OBJ**.</span></span> <span data-ttu-id="2816b-182">生成所选图形引擎支持的模型的任何工具将在 **HoloLens** 上运行。</span><span class="sxs-lookup"><span data-stu-id="2816b-182">Any tool that generates a model that your chosen graphics engine supports will work on **HoloLens**.</span></span> <span data-ttu-id="2816b-183">在三维音乐家之间，很多选择使用 [Autodesk 的 Maya，因为它可以使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) 来转换资产的创建方式。</span><span class="sxs-lookup"><span data-stu-id="2816b-183">Among 3D artists, many choose to use [Autodesk’s Maya because it can use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="2816b-184">如果你想要快速获得一些内容，也可以使用 Windows 附带的 [3D 生成器](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) 进行导出。要在应用程序中使用的 OBJ。</span><span class="sxs-lookup"><span data-stu-id="2816b-184">If you want to get something in quick, you can also use [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) that comes with Windows to export .OBJ for use in your application.</span></span>

<span data-ttu-id="2816b-185">**对象捕获**</span><span class="sxs-lookup"><span data-stu-id="2816b-185">**Object capture**</span></span><br>
<span data-ttu-id="2816b-186">还可以选择以三维方式捕获对象。</span><span class="sxs-lookup"><span data-stu-id="2816b-186">There's also the option to capture objects in 3D.</span></span> <span data-ttu-id="2816b-187">在三维中捕获 inanimate 对象并通过数字内容创建软件对其进行编辑时，三维打印增加了。</span><span class="sxs-lookup"><span data-stu-id="2816b-187">Capturing inanimate objects in 3D and editing them with digital content creation software is increasingly popular with the rise of 3D printing.</span></span> <span data-ttu-id="2816b-188">使用 **Kinect 2** 传感器和 [3d 生成器](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) ，可以使用捕获功能从真实世界对象创建资产。</span><span class="sxs-lookup"><span data-stu-id="2816b-188">Using the **Kinect 2** sensor and [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) you can use the capture feature to create assets from real world objects.</span></span> <span data-ttu-id="2816b-189">这也是一 [套工具](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) ，用于通过处理多个要装订在一起和网格和纹理的图像来对 **photogrammetry** 执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="2816b-189">This is also a [suite of tools](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) to do the same with **photogrammetry** by processing several images to stitch together and mesh and textures.</span></span>

### <a name="purchasing-assets"></a><span data-ttu-id="2816b-190">采购资产</span><span class="sxs-lookup"><span data-stu-id="2816b-190">Purchasing assets</span></span>

<span data-ttu-id="2816b-191">另一种极佳的选择是购买资产以获得经验。</span><span class="sxs-lookup"><span data-stu-id="2816b-191">Another excellent option is to purchase assets for your experience.</span></span> <span data-ttu-id="2816b-192">有大量的资产可通过 [Unity 资产存储区](https://www.assetstore.unity3d.com/) 或 [TurboSquid](https://www.turbosquid.com/) 等服务获得。</span><span class="sxs-lookup"><span data-stu-id="2816b-192">There are a ton of assets available through services such as the [Unity Asset Store](https://www.assetstore.unity3d.com/) or [TurboSquid](https://www.turbosquid.com/) among others.</span></span>

<span data-ttu-id="2816b-193">从第三方购买资产时，始终需要检查以下属性：</span><span class="sxs-lookup"><span data-stu-id="2816b-193">When you purchase assets from a third party, you always want to check the following properties:</span></span>
* <span data-ttu-id="2816b-194">**什么是 poly 计数？**</span><span class="sxs-lookup"><span data-stu-id="2816b-194">**What's the poly count?**</span></span>
  * <span data-ttu-id="2816b-195">它是否适用于预算内？</span><span class="sxs-lookup"><span data-stu-id="2816b-195">Does it fit within your budget?</span></span>
* <span data-ttu-id="2816b-196">**模型是否有 (LODs) 的详细信息级别？**</span><span class="sxs-lookup"><span data-stu-id="2816b-196">**Are there levels of detail (LODs) for the model?**</span></span>
  * <span data-ttu-id="2816b-197">利用模型级别的详细信息，您可以缩放模型的详细信息以提高性能。</span><span class="sxs-lookup"><span data-stu-id="2816b-197">A models level of detail lets you scale the detail of a model for performance.</span></span>
* <span data-ttu-id="2816b-198">**源文件可用吗？**</span><span class="sxs-lookup"><span data-stu-id="2816b-198">**Is the source file available?**</span></span>
  * <span data-ttu-id="2816b-199">不包含在 [Unity 资产存储区](https://www.assetstore.unity3d.com/) 中，但始终包含在 [TurboSquid](https://www.turbosquid.com/)等服务中。</span><span class="sxs-lookup"><span data-stu-id="2816b-199">Not included with [Unity Asset Store](https://www.assetstore.unity3d.com/) but always included with services like [TurboSquid](https://www.turbosquid.com/).</span></span>
  * <span data-ttu-id="2816b-200">如果没有源文件，则无法修改资产。</span><span class="sxs-lookup"><span data-stu-id="2816b-200">Without the source file, you can't modify the asset.</span></span>
  * <span data-ttu-id="2816b-201">请确保3D 工具可以导入提供的源文件。</span><span class="sxs-lookup"><span data-stu-id="2816b-201">Make sure the source file provided can be imported by your 3D tools.</span></span>
* <span data-ttu-id="2816b-202">**了解所获得的内容**</span><span class="sxs-lookup"><span data-stu-id="2816b-202">**Know what you're getting**</span></span>
  * <span data-ttu-id="2816b-203">动画是否提供？</span><span class="sxs-lookup"><span data-stu-id="2816b-203">Are animations provided?</span></span>
  * <span data-ttu-id="2816b-204">请确保检查要购买的资产的 "内容" 列表。</span><span class="sxs-lookup"><span data-stu-id="2816b-204">Make sure to check the contents list of the asset you're purchasing.</span></span>

### <a name="porting-assets"></a><span data-ttu-id="2816b-205">移植资产</span><span class="sxs-lookup"><span data-stu-id="2816b-205">Porting assets</span></span>

<span data-ttu-id="2816b-206">在某些情况下，你将获得最初为其他设备和不同应用生成的现有资产。</span><span class="sxs-lookup"><span data-stu-id="2816b-206">In some cases you'll be handed existing assets that were originally built for other devices and different apps.</span></span> <span data-ttu-id="2816b-207">在大多数情况下，可以将这些资产转换为与应用使用的图形引擎兼容的格式。</span><span class="sxs-lookup"><span data-stu-id="2816b-207">In most cases, these assets can be converted to formats compatible with the graphics engine their app is using.</span></span>

<span data-ttu-id="2816b-208">在将资产移植到 HoloLens 应用程序中使用时，需要询问以下问题：</span><span class="sxs-lookup"><span data-stu-id="2816b-208">When porting assets to use in your HoloLens application, you'll want to ask the following questions:</span></span>
* <span data-ttu-id="2816b-209">**能否直接导入或是否需要将其转换为另一种格式？**</span><span class="sxs-lookup"><span data-stu-id="2816b-209">**Can you import directly or does need to be converted to another format?**</span></span> <span data-ttu-id="2816b-210">使用正在使用的图形引擎检查要导入的格式。</span><span class="sxs-lookup"><span data-stu-id="2816b-210">Check the format you're importing with the graphics engine you're using.</span></span>
* <span data-ttu-id="2816b-211">**如果转换为兼容的格式，会丢失任何内容吗？**</span><span class="sxs-lookup"><span data-stu-id="2816b-211">**If converting to a compatible format is anything lost?**</span></span> <span data-ttu-id="2816b-212">有时，详细信息可能会丢失，或者导入可能会导致需要在三维创作工具中清除的项目。</span><span class="sxs-lookup"><span data-stu-id="2816b-212">Sometimes details can be lost or importing can cause artifacts that need to be cleaned up in a 3D authoring tool.</span></span>
* <span data-ttu-id="2816b-213">**资产的三角形/多边形数是多少？**</span><span class="sxs-lookup"><span data-stu-id="2816b-213">**What is the triangle / polygon count for the asset?**</span></span> <span data-ttu-id="2816b-214">根据你的应用程序的预算，你可以使用 [Simplygon](https://www.simplygon.com/) 或类似的工具来 decimate (过程，或手动缩减 poly 计数) 原始资产，使其适合应用程序预算。</span><span class="sxs-lookup"><span data-stu-id="2816b-214">Based on the budget for your application you can use [Simplygon](https://www.simplygon.com/) or similar tools to decimate (procedurally or manually reduce poly count) the original asset to fit within your applications budget.</span></span>

### <a name="outsourcing-assets"></a><span data-ttu-id="2816b-215">外包资产</span><span class="sxs-lookup"><span data-stu-id="2816b-215">Outsourcing assets</span></span>

<span data-ttu-id="2816b-216">对于需要更多资产而不是团队创建的大型项目，另一个选项是将资产创建外包。</span><span class="sxs-lookup"><span data-stu-id="2816b-216">Another option for larger projects that require more assets than your team is equipped to create is to outsource asset creation.</span></span> <span data-ttu-id="2816b-217">外包过程涉及到寻找适用于外包资产的正确工作室或机构。</span><span class="sxs-lookup"><span data-stu-id="2816b-217">The process of outsourcing involves finding the right studio or agency that specializes in outsourcing assets.</span></span> <span data-ttu-id="2816b-218">这可能是成本最高的选项，但也是最灵活的选项。</span><span class="sxs-lookup"><span data-stu-id="2816b-218">This can be the most expensive option but also be the most flexible in what you get.</span></span>
* <span data-ttu-id="2816b-219">**明确定义你请求的内容**</span><span class="sxs-lookup"><span data-stu-id="2816b-219">**Clearly define what you're requesting**</span></span>
  * <span data-ttu-id="2816b-220">提供尽可能多的详细信息</span><span class="sxs-lookup"><span data-stu-id="2816b-220">Provide as much detail as possible</span></span>
  * <span data-ttu-id="2816b-221">正面、背面和背面概念图像</span><span class="sxs-lookup"><span data-stu-id="2816b-221">Front, side, and back concept images</span></span>
  * <span data-ttu-id="2816b-222">显示上下文中资产的参考资料</span><span class="sxs-lookup"><span data-stu-id="2816b-222">Reference art showing asset in context</span></span>
  * <span data-ttu-id="2816b-223">通常按厘米指定 (对象的规模) </span><span class="sxs-lookup"><span data-stu-id="2816b-223">Scale of object (Usually specified in centimeters)</span></span>
* <span data-ttu-id="2816b-224">**提供预算**</span><span class="sxs-lookup"><span data-stu-id="2816b-224">**Provide a Budget**</span></span>
  * <span data-ttu-id="2816b-225">Poly 计数范围</span><span class="sxs-lookup"><span data-stu-id="2816b-225">Poly count range</span></span>
  * <span data-ttu-id="2816b-226">纹理数量</span><span class="sxs-lookup"><span data-stu-id="2816b-226">Number of textures</span></span>
  * <span data-ttu-id="2816b-227">适用于 Unity 和 HoloLens 的着色器 (类型应始终默认为移动着色器) </span><span class="sxs-lookup"><span data-stu-id="2816b-227">Type of shader (For Unity and HoloLens you should always default to mobile shaders first)</span></span>
* <span data-ttu-id="2816b-228">**了解成本**</span><span class="sxs-lookup"><span data-stu-id="2816b-228">**Understand the costs**</span></span>
  * <span data-ttu-id="2816b-229">更改请求的外包策略是什么？</span><span class="sxs-lookup"><span data-stu-id="2816b-229">What's the outsourcing policy for change requests?</span></span>

<span data-ttu-id="2816b-230">外包可以很好地根据你的项目时间线运行，但需要更多监督才能保证你首次获得所需的正确资产。</span><span class="sxs-lookup"><span data-stu-id="2816b-230">Outsourcing can work well based on your projects timeline but requires more oversight to guarantee that you get the right assets you need the first time.</span></span>
