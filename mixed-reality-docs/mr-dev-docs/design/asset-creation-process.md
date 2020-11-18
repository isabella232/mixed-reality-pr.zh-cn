---
title: 资产创建过程
description: 有关为混合现实体验创建资产的指导。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: 资产，创建，处理，预算，多边形，纹理，着色器，性能，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包，资产
ms.openlocfilehash: 0c6f592dd813c06613801510ad8c8a936ad0de65
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702873"
---
# <a name="asset-creation-process"></a><span data-ttu-id="6a149-104">资产创建过程</span><span class="sxs-lookup"><span data-stu-id="6a149-104">Asset creation process</span></span>

<span data-ttu-id="6a149-105">Windows Mixed Reality 构建于 Microsoft 投入了 DirectX 的数十年中。</span><span class="sxs-lookup"><span data-stu-id="6a149-105">Windows Mixed Reality builds on the decades of investment Microsoft has made into DirectX.</span></span> <span data-ttu-id="6a149-106">这意味着，开发人员构建3D 图形的所有经验和技能都将继续对 HoloLens 有用。</span><span class="sxs-lookup"><span data-stu-id="6a149-106">This means that all of the experience and skills developers have with building 3D graphics continues to be valuable with HoloLens.</span></span>

<span data-ttu-id="6a149-107">你为项目创建的资产分为多个形状和窗体。</span><span class="sxs-lookup"><span data-stu-id="6a149-107">The assets you create for a project come in many shapes and forms.</span></span> <span data-ttu-id="6a149-108">它们可以包含一系列纹理/图像、音频、视频、3D 模型和动画。</span><span class="sxs-lookup"><span data-stu-id="6a149-108">They can be comprised of a series of textures/images, audio, video, 3D models and animations.</span></span> <span data-ttu-id="6a149-109">我们无法开始涵盖可用于创建项目中使用的不同类型资产的所有工具。</span><span class="sxs-lookup"><span data-stu-id="6a149-109">We can't begin to cover all the tools that are available to create the different types of assets used in a project.</span></span> <span data-ttu-id="6a149-110">对于本文，我们将重点介绍3D 资产创建方法。</span><span class="sxs-lookup"><span data-stu-id="6a149-110">For this article we will focus on 3D asset creation methods.</span></span>

<span data-ttu-id="6a149-111">![概念、创建、集成和迭代流](images/concept-creation-integration-iteration-flow-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="6a149-111">![Concept, creation, integration and iteration flow](images/concept-creation-integration-iteration-flow-640px.jpg)</span></span><br>
<span data-ttu-id="6a149-112">*概念、创建、集成和迭代流*</span><span class="sxs-lookup"><span data-stu-id="6a149-112">*Concept, creation, integration and iteration flow*</span></span>

## <a name="things-to-consider"></a><span data-ttu-id="6a149-113">注意事项</span><span class="sxs-lookup"><span data-stu-id="6a149-113">Things to consider</span></span>

<span data-ttu-id="6a149-114">在观看您的体验时，您要尝试创建它作为 **预算** ，以尝试创建最佳体验。</span><span class="sxs-lookup"><span data-stu-id="6a149-114">When looking at the experience you're trying to create think of it as a **budget** that you can spend to try to create the best experience.</span></span> <span data-ttu-id="6a149-115">不一定会对资产中的 **多边形** 数量或 **材料类型** 的数量有硬性限制，但会有一组预算的折衷。</span><span class="sxs-lookup"><span data-stu-id="6a149-115">There is not necessarily hard limits on the number of **polygons** or **types of materials** use in your assets but more a budgeted set of tradeoffs.</span></span>

<span data-ttu-id="6a149-116">下面是你的体验的示例预算。</span><span class="sxs-lookup"><span data-stu-id="6a149-116">Below is an example budget for your experience.</span></span> <span data-ttu-id="6a149-117">性能通常不是单一故障点，而是每 se 一千次切削死亡。</span><span class="sxs-lookup"><span data-stu-id="6a149-117">Performance is usually not a single point of failure but death by a thousand cuts per-se.</span></span>
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><span data-ttu-id="6a149-118"><b>资产</b></span><span class="sxs-lookup"><span data-stu-id="6a149-118"><b>Assets</b></span></span></th><th style="text-align:right;"> <span data-ttu-id="6a149-119">CPU</span><span class="sxs-lookup"><span data-stu-id="6a149-119">CPU</span></span></th><th> <span data-ttu-id="6a149-120">GPU</span><span class="sxs-lookup"><span data-stu-id="6a149-120">GPU</span></span></th><th> <span data-ttu-id="6a149-121">内存</span><span class="sxs-lookup"><span data-stu-id="6a149-121">Memory</span></span></th>
</tr><tr>
<td> <span data-ttu-id="6a149-122">Polygon（多边形）</span><span class="sxs-lookup"><span data-stu-id="6a149-122">Polygons</span></span></td><td> <span data-ttu-id="6a149-123">0%</span><span class="sxs-lookup"><span data-stu-id="6a149-123">0%</span></span></td><td> <span data-ttu-id="6a149-124">5%</span><span class="sxs-lookup"><span data-stu-id="6a149-124">5%</span></span></td><td> <span data-ttu-id="6a149-125">10%</span><span class="sxs-lookup"><span data-stu-id="6a149-125">10%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6a149-126">纹理</span><span class="sxs-lookup"><span data-stu-id="6a149-126">Textures</span></span></td><td> <span data-ttu-id="6a149-127">5%</span><span class="sxs-lookup"><span data-stu-id="6a149-127">5%</span></span></td><td> <span data-ttu-id="6a149-128">15%</span><span class="sxs-lookup"><span data-stu-id="6a149-128">15%</span></span></td><td><span data-ttu-id="6a149-129">25%</span><span class="sxs-lookup"><span data-stu-id="6a149-129">25%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6a149-130">着色器</span><span class="sxs-lookup"><span data-stu-id="6a149-130">Shaders</span></span></td><td> <span data-ttu-id="6a149-131">15%</span><span class="sxs-lookup"><span data-stu-id="6a149-131">15%</span></span></td><td> <span data-ttu-id="6a149-132">35%</span><span class="sxs-lookup"><span data-stu-id="6a149-132">35%</span></span></td><td> <span data-ttu-id="6a149-133">0%</span><span class="sxs-lookup"><span data-stu-id="6a149-133">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6a149-134"><b>Dynamics</b></span><span class="sxs-lookup"><span data-stu-id="6a149-134"><b>Dynamics</b></span></span></td><td></td><td></td><td></td>
</tr><tr>
<td> <span data-ttu-id="6a149-135">物理</span><span class="sxs-lookup"><span data-stu-id="6a149-135">Physics</span></span></td><td> <span data-ttu-id="6a149-136">5%</span><span class="sxs-lookup"><span data-stu-id="6a149-136">5%</span></span></td><td> <span data-ttu-id="6a149-137">15%</span><span class="sxs-lookup"><span data-stu-id="6a149-137">15%</span></span></td><td> <span data-ttu-id="6a149-138">0%</span><span class="sxs-lookup"><span data-stu-id="6a149-138">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6a149-139">实时照明</span><span class="sxs-lookup"><span data-stu-id="6a149-139">Realtime lighting</span></span></td><td> <span data-ttu-id="6a149-140">10%</span><span class="sxs-lookup"><span data-stu-id="6a149-140">10%</span></span></td><td> <span data-ttu-id="6a149-141">0%</span><span class="sxs-lookup"><span data-stu-id="6a149-141">0%</span></span></td><td> <span data-ttu-id="6a149-142">0%</span><span class="sxs-lookup"><span data-stu-id="6a149-142">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6a149-143">Media (音频/视频) </span><span class="sxs-lookup"><span data-stu-id="6a149-143">Media (audio/video)</span></span></td><td> -</td><td> <span data-ttu-id="6a149-144">15%</span><span class="sxs-lookup"><span data-stu-id="6a149-144">15%</span></span></td><td> <span data-ttu-id="6a149-145">25%</span><span class="sxs-lookup"><span data-stu-id="6a149-145">25%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6a149-146">脚本/逻辑</span><span class="sxs-lookup"><span data-stu-id="6a149-146">Script/logic</span></span></td><td> <span data-ttu-id="6a149-147">25%</span><span class="sxs-lookup"><span data-stu-id="6a149-147">25%</span></span></td><td> <span data-ttu-id="6a149-148">0%</span><span class="sxs-lookup"><span data-stu-id="6a149-148">0%</span></span></td><td> <span data-ttu-id="6a149-149">5%</span><span class="sxs-lookup"><span data-stu-id="6a149-149">5%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6a149-150">一般开销</span><span class="sxs-lookup"><span data-stu-id="6a149-150">General overhead</span></span></td><td> <span data-ttu-id="6a149-151">5%</span><span class="sxs-lookup"><span data-stu-id="6a149-151">5%</span></span></td><td> <span data-ttu-id="6a149-152">5%</span><span class="sxs-lookup"><span data-stu-id="6a149-152">5%</span></span></td><td> <span data-ttu-id="6a149-153">5%</span><span class="sxs-lookup"><span data-stu-id="6a149-153">5%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6a149-154"><b>总计</b></span><span class="sxs-lookup"><span data-stu-id="6a149-154"><b>Total</b></span></span></td><td> <span data-ttu-id="6a149-155"><b>65%</b></span><span class="sxs-lookup"><span data-stu-id="6a149-155"><b>65%</b></span></span></td><td> <span data-ttu-id="6a149-156"><b>90%</b></span><span class="sxs-lookup"><span data-stu-id="6a149-156"><b>90%</b></span></span></td><td> <span data-ttu-id="6a149-157"><b>70%</b></span><span class="sxs-lookup"><span data-stu-id="6a149-157"><b>70%</b></span></span></td>
</tr>
</table>

<span data-ttu-id="6a149-158">**资产总数**</span><span class="sxs-lookup"><span data-stu-id="6a149-158">**Total number of assets**</span></span>
* <span data-ttu-id="6a149-159">场景中有多少资产处于活动状态？</span><span class="sxs-lookup"><span data-stu-id="6a149-159">How many assets are active in the scene?</span></span>

<span data-ttu-id="6a149-160">**资产复杂性**</span><span class="sxs-lookup"><span data-stu-id="6a149-160">**Complexity of assets**</span></span>
* <span data-ttu-id="6a149-161">三角形/多边形有多少？</span><span class="sxs-lookup"><span data-stu-id="6a149-161">How many triangles / polygons?</span></span>
* <span data-ttu-id="6a149-162">着色器的复杂程度如何？</span><span class="sxs-lookup"><span data-stu-id="6a149-162">How complex is the shader?</span></span> <span data-ttu-id="6a149-163">使用混合现实工具包时，建议使用 [混合现实工具包标准着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) 来降低着色器的复杂性。</span><span class="sxs-lookup"><span data-stu-id="6a149-163">When using the Mixed Reality Toolkit, it is recommended to use the [Mixed Reality Toolkit Standard shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) to reduce shader complexity.</span></span>

<span data-ttu-id="6a149-164">开发人员和艺术家都必须考虑设备和图形引擎的功能。</span><span class="sxs-lookup"><span data-stu-id="6a149-164">Both the developers and artists have to consider the capabilities of the device and the graphics engine.</span></span> <span data-ttu-id="6a149-165">Microsoft HoloLens 包含内置于设备中的所有计算和图形。</span><span class="sxs-lookup"><span data-stu-id="6a149-165">Microsoft HoloLens has all of the computational and graphics built into the device.</span></span> <span data-ttu-id="6a149-166">它共享开发人员在移动平台上所能找到的功能。</span><span class="sxs-lookup"><span data-stu-id="6a149-166">It shares the capabilities developers would find on a mobile platform.</span></span>

<span data-ttu-id="6a149-167">无论您的目标是 [全息设备还是沉浸式设备](../discover/mixed-reality.md#the-mixed-reality-spectrum)的体验，资产的创建过程都是相同的。</span><span class="sxs-lookup"><span data-stu-id="6a149-167">The creation process for assets is the same regardless of whether you're targeting an experience for a [holographic device or an immersive device](../discover/mixed-reality.md#the-mixed-reality-spectrum).</span></span> <span data-ttu-id="6a149-168">需要注意的主要事项是上述设备功能以及规模，因为你可以在混合现实中看到真实世界，你需要根据经验维护适当的规模。</span><span class="sxs-lookup"><span data-stu-id="6a149-168">The primary thing to note is the device capability as mentioned above as well as scale since you can see the real world in mixed reality you will want to maintain the correct scale based on the experience.</span></span>

## <a name="authoring-assets"></a><span data-ttu-id="6a149-169">创作资产</span><span class="sxs-lookup"><span data-stu-id="6a149-169">Authoring assets</span></span>

<span data-ttu-id="6a149-170">首先，我们将介绍如何获取项目的资产：</span><span class="sxs-lookup"><span data-stu-id="6a149-170">We'll start with the ways to get assets for your project:</span></span>
1. <span data-ttu-id="6a149-171">创建资产 (创作工具和对象捕获) </span><span class="sxs-lookup"><span data-stu-id="6a149-171">Creating Assets (Authoring tools and object capture)</span></span>
2. <span data-ttu-id="6a149-172">采购资产 (在线购买资产) </span><span class="sxs-lookup"><span data-stu-id="6a149-172">Purchasing Assets (Buying assets online)</span></span>
3. <span data-ttu-id="6a149-173">迁移资产 (获取现有资产) </span><span class="sxs-lookup"><span data-stu-id="6a149-173">Porting Assets (Taking existing assets)</span></span>
4. <span data-ttu-id="6a149-174">外包资产 (从第三方导入资产) </span><span class="sxs-lookup"><span data-stu-id="6a149-174">Outsourcing Assets (Importing assets from 3rd parties)</span></span>

### <a name="creating-assets"></a><span data-ttu-id="6a149-175">创建资产</span><span class="sxs-lookup"><span data-stu-id="6a149-175">Creating assets</span></span>

<span data-ttu-id="6a149-176">**创作工具**</span><span class="sxs-lookup"><span data-stu-id="6a149-176">**Authoring tools**</span></span><br>
<span data-ttu-id="6a149-177">首先，您可以使用多种不同的方法创建自己的资产。</span><span class="sxs-lookup"><span data-stu-id="6a149-177">First you can create your own assets in a number of different ways.</span></span> <span data-ttu-id="6a149-178">三维音乐家使用多种应用程序和工具来创建由 **网格**、 **纹理** 和 **材料** 组成的模型。</span><span class="sxs-lookup"><span data-stu-id="6a149-178">3D artists use a number of applications and tools to create models which consist of **meshes**, **textures**, and **materials**.</span></span> <span data-ttu-id="6a149-179">然后以文件格式保存该文件，应用程序使用的图形引擎可以导入或使用该格式，如 **。FBX** 或 **。OBJ**。</span><span class="sxs-lookup"><span data-stu-id="6a149-179">This is then saved in a file format that can be imported or used by the graphics engine used by the app, such as **.FBX** or **.OBJ**.</span></span> <span data-ttu-id="6a149-180">生成所选图形引擎支持的模型的任何工具将在 **HoloLens** 上运行。</span><span class="sxs-lookup"><span data-stu-id="6a149-180">Any tool that generates a model that your chosen graphics engine supports will work on **HoloLens**.</span></span> <span data-ttu-id="6a149-181">在三维音乐家之间，很多选择使用 [Autodesk 的 Maya，它本身能够使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) 来转换资产的创建方式。</span><span class="sxs-lookup"><span data-stu-id="6a149-181">Among 3D artists, many choose to use [Autodesk’s Maya which itself is able to use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="6a149-182">如果你想要快速获取内容，还可以使用随 Windows 一起导出的 [3D 生成器](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) 。要在应用程序中使用的 OBJ。</span><span class="sxs-lookup"><span data-stu-id="6a149-182">If you want to get something in quick you can also use [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) that comes with Windows to export .OBJ for use in your application.</span></span>

<span data-ttu-id="6a149-183">**对象捕获**</span><span class="sxs-lookup"><span data-stu-id="6a149-183">**Object capture**</span></span><br>
<span data-ttu-id="6a149-184">还可以选择在三维中捕获对象。</span><span class="sxs-lookup"><span data-stu-id="6a149-184">There is also the option to capture objects in 3D.</span></span> <span data-ttu-id="6a149-185">在三维中捕获 inanimate 对象并通过数字内容创建软件对其进行编辑时，三维打印增加了。</span><span class="sxs-lookup"><span data-stu-id="6a149-185">Capturing inanimate objects in 3D and editing them with digital content creation software is increasingly popular with the rise of 3D printing.</span></span> <span data-ttu-id="6a149-186">使用 **Kinect 2** 传感器和 [3d 生成器](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) ，可以使用捕获功能从真实世界对象创建资产。</span><span class="sxs-lookup"><span data-stu-id="6a149-186">Using the **Kinect 2** sensor and [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) you can use the capture feature to create assets from real world objects.</span></span> <span data-ttu-id="6a149-187">这也是一 [套工具](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) ，用于通过处理多个要装订在一起以及网格和纹理的图像来对 **photogrammetry** 执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="6a149-187">This is also a [suite of tools](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) to do the same with **photogrammetry** by processing a number of images to stitch together and mesh and textures.</span></span>

### <a name="purchasing-assets"></a><span data-ttu-id="6a149-188">采购资产</span><span class="sxs-lookup"><span data-stu-id="6a149-188">Purchasing assets</span></span>

<span data-ttu-id="6a149-189">另一种极佳的选择是购买资产以获得经验。</span><span class="sxs-lookup"><span data-stu-id="6a149-189">Another excellent option is to purchase assets for your experience.</span></span> <span data-ttu-id="6a149-190">有大量的资产可通过 [Unity 资产存储区](https://www.assetstore.unity3d.com/) 或 [TurboSquid](https://www.turbosquid.com/) 等服务获得。</span><span class="sxs-lookup"><span data-stu-id="6a149-190">There are a ton of assets available through services such as the [Unity Asset Store](https://www.assetstore.unity3d.com/) or [TurboSquid](https://www.turbosquid.com/) among others.</span></span>

<span data-ttu-id="6a149-191">从第三方购买资产时，始终需要检查以下各项：</span><span class="sxs-lookup"><span data-stu-id="6a149-191">When you purchase assets from a 3rd party you always want to check the following:</span></span>
* <span data-ttu-id="6a149-192">**什么是 poly 计数？**</span><span class="sxs-lookup"><span data-stu-id="6a149-192">**What's the poly count?**</span></span>
  * <span data-ttu-id="6a149-193">它是否适用于预算内？</span><span class="sxs-lookup"><span data-stu-id="6a149-193">Does it fit within your budget?</span></span>
* <span data-ttu-id="6a149-194">**模型是否有 (LODs) 的详细信息级别？**</span><span class="sxs-lookup"><span data-stu-id="6a149-194">**Are there levels of detail (LODs) for the model?**</span></span>
  * <span data-ttu-id="6a149-195">利用模型的详细信息级别，可以缩放模型的详细信息以提高性能。</span><span class="sxs-lookup"><span data-stu-id="6a149-195">Level of detail of a model allow you to scale the detail of a model for performance.</span></span>
* <span data-ttu-id="6a149-196">**源文件可用吗？**</span><span class="sxs-lookup"><span data-stu-id="6a149-196">**Is the source file available?**</span></span>
  * <span data-ttu-id="6a149-197">通常不包含在 [Unity 资产存储区](https://www.assetstore.unity3d.com/) 中，但始终包含在 [TurboSquid](https://www.turbosquid.com/)等服务中。</span><span class="sxs-lookup"><span data-stu-id="6a149-197">Usually not included with [Unity Asset Store](https://www.assetstore.unity3d.com/) but always included with services like [TurboSquid](https://www.turbosquid.com/).</span></span>
  * <span data-ttu-id="6a149-198">如果没有源文件，将无法修改资产。</span><span class="sxs-lookup"><span data-stu-id="6a149-198">Without the source file you won't be able to modify the asset.</span></span>
  * <span data-ttu-id="6a149-199">请确保3D 工具可以导入提供的源文件。</span><span class="sxs-lookup"><span data-stu-id="6a149-199">Make sure the source file provided can be imported by your 3D tools.</span></span>
* <span data-ttu-id="6a149-200">**了解所获得的内容**</span><span class="sxs-lookup"><span data-stu-id="6a149-200">**Know what you're getting**</span></span>
  * <span data-ttu-id="6a149-201">动画是否提供？</span><span class="sxs-lookup"><span data-stu-id="6a149-201">Are animations provided?</span></span>
  * <span data-ttu-id="6a149-202">请确保检查要购买的资产的 "内容" 列表。</span><span class="sxs-lookup"><span data-stu-id="6a149-202">Make sure to check the contents list of the asset you're purchasing.</span></span>

### <a name="porting-assets"></a><span data-ttu-id="6a149-203">移植资产</span><span class="sxs-lookup"><span data-stu-id="6a149-203">Porting assets</span></span>

<span data-ttu-id="6a149-204">在某些情况下，你将获得最初为其他设备和不同应用生成的现有资产。</span><span class="sxs-lookup"><span data-stu-id="6a149-204">In some cases you'll be handed existing assets that were originally built for other devices and different apps.</span></span> <span data-ttu-id="6a149-205">在大多数情况下，可以将这些资产转换为与应用正在使用的图形引擎兼容的格式。</span><span class="sxs-lookup"><span data-stu-id="6a149-205">In most cases these assets can be converted to formats compatible with the graphics engine their app is using.</span></span>

<span data-ttu-id="6a149-206">在将资产移植到 HoloLens 应用程序中使用时，需要询问以下内容：</span><span class="sxs-lookup"><span data-stu-id="6a149-206">When porting assets to use in your HoloLens application you will want to ask the following:</span></span>
* <span data-ttu-id="6a149-207">**能否直接导入或是否需要将其转换为另一种格式？**</span><span class="sxs-lookup"><span data-stu-id="6a149-207">**Can you import directly or does need to be converted to another format?**</span></span> <span data-ttu-id="6a149-208">使用正在使用的图形引擎检查要导入的格式。</span><span class="sxs-lookup"><span data-stu-id="6a149-208">Check the format you're importing with the graphics engine you're using.</span></span>
* <span data-ttu-id="6a149-209">**如果转换为兼容的格式，会丢失任何内容吗？**</span><span class="sxs-lookup"><span data-stu-id="6a149-209">**If converting to a compatible format is anything lost?**</span></span> <span data-ttu-id="6a149-210">有时，详细信息可能会丢失，或者导入可能会导致需要在三维创作工具中清除的项目。</span><span class="sxs-lookup"><span data-stu-id="6a149-210">Sometimes details can be lost or importing can cause artifacts that need to be cleaned up in a 3D authoring tool.</span></span>
* <span data-ttu-id="6a149-211">**资产的三角形/多边形数是多少？**</span><span class="sxs-lookup"><span data-stu-id="6a149-211">**What is the triangles / polygons count for the asset?**</span></span> <span data-ttu-id="6a149-212">根据你的应用程序的预算，你可以使用 [Simplygon](https://www.simplygon.com/) 或类似的工具来 decimate (过程，或手动缩减 poly 计数) 原始资产，使其适合应用程序预算。</span><span class="sxs-lookup"><span data-stu-id="6a149-212">Based on the budget for you application you can use [Simplygon](https://www.simplygon.com/) or similar tools to decimate (procedurally or manually reduce poly count) the original asset to fit within your applications budget.</span></span>

### <a name="outsourcing-assets"></a><span data-ttu-id="6a149-213">外包资产</span><span class="sxs-lookup"><span data-stu-id="6a149-213">Outsourcing assets</span></span>

<span data-ttu-id="6a149-214">对于需要更多资产而不是团队创建的大型项目，另一个选项是将资产创建外包。</span><span class="sxs-lookup"><span data-stu-id="6a149-214">Another option for larger projects that require more assets than your team is equipped to create is to outsource asset creation.</span></span> <span data-ttu-id="6a149-215">外包过程涉及到寻找适用于外包资产的正确工作室或机构。</span><span class="sxs-lookup"><span data-stu-id="6a149-215">The process of outsourcing involves finding the right studio or agency that specializes in outsourcing assets.</span></span> <span data-ttu-id="6a149-216">这可能是成本最高的选项，但也是最灵活的选项。</span><span class="sxs-lookup"><span data-stu-id="6a149-216">This can be the most expensive option but also be the most flexible in what you get.</span></span>
* <span data-ttu-id="6a149-217">**明确定义你请求的内容**</span><span class="sxs-lookup"><span data-stu-id="6a149-217">**Clearly define what you're requesting**</span></span>
  * <span data-ttu-id="6a149-218">提供尽可能多的详细信息</span><span class="sxs-lookup"><span data-stu-id="6a149-218">Provide as much detail as possible</span></span>
  * <span data-ttu-id="6a149-219">正面、反面和背面概念图像</span><span class="sxs-lookup"><span data-stu-id="6a149-219">Front, side and back concept images</span></span>
  * <span data-ttu-id="6a149-220">显示上下文中资产的参考资料</span><span class="sxs-lookup"><span data-stu-id="6a149-220">Reference art showing asset in context</span></span>
  * <span data-ttu-id="6a149-221">通常按厘米指定 (对象的规模) </span><span class="sxs-lookup"><span data-stu-id="6a149-221">Scale of object (Usually specified in centimeters)</span></span>
* <span data-ttu-id="6a149-222">**提供预算**</span><span class="sxs-lookup"><span data-stu-id="6a149-222">**Provide a Budget**</span></span>
  * <span data-ttu-id="6a149-223">Poly 计数范围</span><span class="sxs-lookup"><span data-stu-id="6a149-223">Poly count range</span></span>
  * <span data-ttu-id="6a149-224">纹理数量</span><span class="sxs-lookup"><span data-stu-id="6a149-224">Number of textures</span></span>
  * <span data-ttu-id="6a149-225">适用于 Unity 和 HoloLens 的着色器 (类型应始终默认为移动着色器) </span><span class="sxs-lookup"><span data-stu-id="6a149-225">Type of shader (For Unity and HoloLens you should always default to mobile shaders first)</span></span>
* <span data-ttu-id="6a149-226">**了解成本**</span><span class="sxs-lookup"><span data-stu-id="6a149-226">**Understand the costs**</span></span>
  * <span data-ttu-id="6a149-227">更改请求的外包策略是什么？</span><span class="sxs-lookup"><span data-stu-id="6a149-227">What's the outsourcing policy for change requests?</span></span>

<span data-ttu-id="6a149-228">外包可以很好地根据项目时间线工作，但需要更多的监督来保证你首次获得所需的正确资产。</span><span class="sxs-lookup"><span data-stu-id="6a149-228">Outsourcing can work extremely well based on your projects timeline but requires more oversight to guarantee that you get the right assets you need the first time.</span></span>
