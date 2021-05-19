---
title: 场景系统内容加载
description: 文档加载场景系统与 MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: f310b3687a6773404c7a998a3764163daf159857
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145140"
---
# <a name="content-scene-loading"></a><span data-ttu-id="ccc20-104">内容场景加载</span><span class="sxs-lookup"><span data-stu-id="ccc20-104">Content scene loading</span></span>

<span data-ttu-id="ccc20-105">所有内容加载操作都是异步的，默认情况下，所有内容加载都是累加的。</span><span class="sxs-lookup"><span data-stu-id="ccc20-105">All content load operations are asynchronous, and by default all content loading is additive.</span></span> <span data-ttu-id="ccc20-106">管理器和照明场景从不受内容加载操作影响。</span><span class="sxs-lookup"><span data-stu-id="ccc20-106">Manager and lighting scenes are never affected by content loading operations.</span></span> <span data-ttu-id="ccc20-107">有关监视加载进度和场景激活的信息，请参阅 [监视内容加载](scene-system-load-progress.md)。</span><span class="sxs-lookup"><span data-stu-id="ccc20-107">For information about monitoring load progress and scene activation, see [Monitoring Content Loading](scene-system-load-progress.md).</span></span>

## <a name="loading-content"></a><span data-ttu-id="ccc20-108">正在加载内容</span><span class="sxs-lookup"><span data-stu-id="ccc20-108">Loading content</span></span>

<span data-ttu-id="ccc20-109">若要加载内容场景，请使用 `LoadContent` 方法：</span><span class="sxs-lookup"><span data-stu-id="ccc20-109">To load content scenes use the `LoadContent` method:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a><span data-ttu-id="ccc20-110">单场景加载</span><span class="sxs-lookup"><span data-stu-id="ccc20-110">Single scene loading</span></span>

<span data-ttu-id="ccc20-111">可以通过可选的参数来实现单个场景加载的等效项 `mode` 。</span><span class="sxs-lookup"><span data-stu-id="ccc20-111">The equivalent of a single scene load can be achieved via the optional `mode` argument.</span></span> <span data-ttu-id="ccc20-112">`LoadSceneMode.Single` 将首先卸载所有加载的内容场景，然后再继续进行加载。</span><span class="sxs-lookup"><span data-stu-id="ccc20-112">`LoadSceneMode.Single` will first unload all loaded content scenes before proceeding with the load.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// ContentScene1, ContentScene2 and ContentScene3 will be loaded additively
await sceneSystem.LoadContent("ContentScene1");
await sceneSystem.LoadContent("ContentScene2");
await sceneSystem.LoadContent("ContentScene3");

// ContentScene1, ContentScene2 and ContentScene3 will be unloaded
// SingleContentScene will be loaded additively
await sceneSystem.LoadContent("SingleContentScene", LoadSceneMode.Single);
```

## <a name="next--previous-scene-loading"></a><span data-ttu-id="ccc20-113">下一个/上一个场景加载</span><span class="sxs-lookup"><span data-stu-id="ccc20-113">Next / previous scene loading</span></span>

<span data-ttu-id="ccc20-114">可以按生成索引的顺序单独加载内容。</span><span class="sxs-lookup"><span data-stu-id="ccc20-114">Content can be singly loaded in order of build index.</span></span> <span data-ttu-id="ccc20-115">这对于展示每个使用用户一组演示场景的应用程序很有用。</span><span class="sxs-lookup"><span data-stu-id="ccc20-115">This is useful for showcase applications that take users through a set of demonstration scenes one-by-one.</span></span>

!["在播放机中生成" 设置中的当前场景](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

<span data-ttu-id="ccc20-117">请注意，在默认情况下，下一项/前一项内容将使用 LoadSceneMode 来确保卸载以前的内容。</span><span class="sxs-lookup"><span data-stu-id="ccc20-117">Note that next / prev content loading uses LoadSceneMode.Single by default to ensure that the previous content is unloaded.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested && sceneSystem.NextContentExists)
{
    await sceneSystem.LoadNextContent();
}

if (prevSceneRequested && sceneSystem.PrevContentExists)
{
    await sceneSystem.LoadPrevContent();
}
```

<span data-ttu-id="ccc20-118">`PrevContentExists` 如果至少有一个内容场景的生成索引低于当前加载的最低生成索引，将返回 true。</span><span class="sxs-lookup"><span data-stu-id="ccc20-118">`PrevContentExists` will return true if there is at least one content scene that has a lower build index than the lowest build index currently loaded.</span></span> <span data-ttu-id="ccc20-119">`NextContentExists` 如果至少有一个内容场景具有比当前加载的最高生成索引更高的生成索引，将返回 true。</span><span class="sxs-lookup"><span data-stu-id="ccc20-119">`NextContentExists` will return true if there is at least one content scene that has a higher build index than the highest build index currently loaded.</span></span>

<span data-ttu-id="ccc20-120">如果 `wrap` 参数为 true，则内容将循环回到第一个/最后一个生成索引。</span><span class="sxs-lookup"><span data-stu-id="ccc20-120">If the `wrap` argument is true, content will loop back to the first / last build index.</span></span> <span data-ttu-id="ccc20-121">这无需检查下一个/以前的内容：</span><span class="sxs-lookup"><span data-stu-id="ccc20-121">This removes the need to check for next / previous content:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested)
{
    await sceneSystem.LoadNextContent(true);
}

if (prevSceneRequested)
{
    await sceneSystem.LoadPrevContent(true);
}
```

## <a name="loading-by-tag"></a><span data-ttu-id="ccc20-122">按标记加载</span><span class="sxs-lookup"><span data-stu-id="ccc20-122">Loading by tag</span></span>

![按标记加载内容场景](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

<span data-ttu-id="ccc20-124">有时需要将内容场景加载到组中。</span><span class="sxs-lookup"><span data-stu-id="ccc20-124">It's sometimes desirable to load content scenes in groups.</span></span> <span data-ttu-id="ccc20-125">例如，经历的阶段可能由多个场景组成，它们必须同时加载，才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="ccc20-125">Eg, a stage of an experience may be composed of multiple scenes, all of which must be loaded simultaneously to function.</span></span> <span data-ttu-id="ccc20-126">为此，可以标记场景，然后加载并加载它们，或将其卸载到该标记。</span><span class="sxs-lookup"><span data-stu-id="ccc20-126">To facilitate this, you can tag your scenes and then load them or unload them with that tag.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

<span data-ttu-id="ccc20-127">如果艺术家希望在不修改脚本的情况下合并/删除元素，则 "按标记加载" 也很有用。</span><span class="sxs-lookup"><span data-stu-id="ccc20-127">Loading by tag can also be useful if artists want to incorporate / remove elements from an experience without having to modify scripts.</span></span> <span data-ttu-id="ccc20-128">例如，通过以下两组标记运行此脚本会产生不同的结果：</span><span class="sxs-lookup"><span data-stu-id="ccc20-128">For instance, running this script with the following two sets of tags produces different results:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a><span data-ttu-id="ccc20-129">测试内容</span><span class="sxs-lookup"><span data-stu-id="ccc20-129">Testing content</span></span>

<span data-ttu-id="ccc20-130">场景名称</span><span class="sxs-lookup"><span data-stu-id="ccc20-130">Scene Name</span></span> | <span data-ttu-id="ccc20-131">场景标记</span><span class="sxs-lookup"><span data-stu-id="ccc20-131">Scene Tag</span></span> | <span data-ttu-id="ccc20-132">由脚本加载</span><span class="sxs-lookup"><span data-stu-id="ccc20-132">Loaded by script</span></span>
---|---|---
<span data-ttu-id="ccc20-133">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="ccc20-133">DebugTerrainPhysics</span></span> | <span data-ttu-id="ccc20-134">地形</span><span class="sxs-lookup"><span data-stu-id="ccc20-134">Terrain</span></span> | <span data-ttu-id="ccc20-135">•</span><span class="sxs-lookup"><span data-stu-id="ccc20-135">•</span></span>
<span data-ttu-id="ccc20-136">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="ccc20-136">StructureTesting</span></span> | <span data-ttu-id="ccc20-137">結構</span><span class="sxs-lookup"><span data-stu-id="ccc20-137">Structures</span></span> | <span data-ttu-id="ccc20-138">•</span><span class="sxs-lookup"><span data-stu-id="ccc20-138">•</span></span>
<span data-ttu-id="ccc20-139">VegetationTools</span><span class="sxs-lookup"><span data-stu-id="ccc20-139">VegetationTools</span></span> | <span data-ttu-id="ccc20-140">Vegetation</span><span class="sxs-lookup"><span data-stu-id="ccc20-140">Vegetation</span></span> | <span data-ttu-id="ccc20-141">•</span><span class="sxs-lookup"><span data-stu-id="ccc20-141">•</span></span>
<span data-ttu-id="ccc20-142">Mountain</span><span class="sxs-lookup"><span data-stu-id="ccc20-142">Mountain</span></span> | <span data-ttu-id="ccc20-143">地形</span><span class="sxs-lookup"><span data-stu-id="ccc20-143">Terrain</span></span> | <span data-ttu-id="ccc20-144">•</span><span class="sxs-lookup"><span data-stu-id="ccc20-144">•</span></span>
<span data-ttu-id="ccc20-145">Cabin</span><span class="sxs-lookup"><span data-stu-id="ccc20-145">Cabin</span></span> | <span data-ttu-id="ccc20-146">結構</span><span class="sxs-lookup"><span data-stu-id="ccc20-146">Structures</span></span> | <span data-ttu-id="ccc20-147">•</span><span class="sxs-lookup"><span data-stu-id="ccc20-147">•</span></span>
<span data-ttu-id="ccc20-148">Trees</span><span class="sxs-lookup"><span data-stu-id="ccc20-148">Trees</span></span> | <span data-ttu-id="ccc20-149">Vegetation</span><span class="sxs-lookup"><span data-stu-id="ccc20-149">Vegetation</span></span> | <span data-ttu-id="ccc20-150">•</span><span class="sxs-lookup"><span data-stu-id="ccc20-150">•</span></span>

### <a name="final-content"></a><span data-ttu-id="ccc20-151">最终内容</span><span class="sxs-lookup"><span data-stu-id="ccc20-151">Final content</span></span>

<span data-ttu-id="ccc20-152">场景名称</span><span class="sxs-lookup"><span data-stu-id="ccc20-152">Scene Name</span></span> | <span data-ttu-id="ccc20-153">场景标记</span><span class="sxs-lookup"><span data-stu-id="ccc20-153">Scene Tag</span></span> | <span data-ttu-id="ccc20-154">由脚本加载</span><span class="sxs-lookup"><span data-stu-id="ccc20-154">Loaded by script</span></span>
---|---|---
<span data-ttu-id="ccc20-155">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="ccc20-155">DebugTerrainPhysics</span></span> | <span data-ttu-id="ccc20-156">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="ccc20-156">DoNotInclude</span></span> |
<span data-ttu-id="ccc20-157">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="ccc20-157">StructureTesting</span></span> | <span data-ttu-id="ccc20-158">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="ccc20-158">DoNotInclude</span></span> |
<span data-ttu-id="ccc20-159">使用"设备"工具</span><span class="sxs-lookup"><span data-stu-id="ccc20-159">VegetationTools</span></span> | <span data-ttu-id="ccc20-160">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="ccc20-160">DoNotInclude</span></span> |
<span data-ttu-id="ccc20-161">Mountain</span><span class="sxs-lookup"><span data-stu-id="ccc20-161">Mountain</span></span> | <span data-ttu-id="ccc20-162">地形</span><span class="sxs-lookup"><span data-stu-id="ccc20-162">Terrain</span></span> | <span data-ttu-id="ccc20-163">•</span><span class="sxs-lookup"><span data-stu-id="ccc20-163">•</span></span>
<span data-ttu-id="ccc20-164">Cabin</span><span class="sxs-lookup"><span data-stu-id="ccc20-164">Cabin</span></span> | <span data-ttu-id="ccc20-165">結構</span><span class="sxs-lookup"><span data-stu-id="ccc20-165">Structures</span></span> | <span data-ttu-id="ccc20-166">•</span><span class="sxs-lookup"><span data-stu-id="ccc20-166">•</span></span>
<span data-ttu-id="ccc20-167">Trees</span><span class="sxs-lookup"><span data-stu-id="ccc20-167">Trees</span></span> | <span data-ttu-id="ccc20-168">植被</span><span class="sxs-lookup"><span data-stu-id="ccc20-168">Vegetation</span></span> | <span data-ttu-id="ccc20-169">•</span><span class="sxs-lookup"><span data-stu-id="ccc20-169">•</span></span>

---

## <a name="editor-behavior"></a><span data-ttu-id="ccc20-170">编辑器行为</span><span class="sxs-lookup"><span data-stu-id="ccc20-170">Editor behavior</span></span>

<span data-ttu-id="ccc20-171">可以使用场景系统的服务检查器在编辑器和播放模式下执行 [所有这些操作。](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span><span class="sxs-lookup"><span data-stu-id="ccc20-171">You can perform all these operations in editor and in play mode by using the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="ccc20-172">在编辑模式下，场景加载是即时的，而在播放模式下，你可以观察加载进度并使用 [激活令牌。](scene-system-load-progress.md)</span><span class="sxs-lookup"><span data-stu-id="ccc20-172">In edit mode scene loads will be instantaneous, while in play mode you can observe loading progress and use [activation tokens.](scene-system-load-progress.md)</span></span>

![检查器中的场景系统，突出显示了内容加载](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
