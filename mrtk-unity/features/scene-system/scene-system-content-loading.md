---
title: 场景系统内容加载
description: 使用 MRTK 加载场景系统的文档
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: c6bc6474afd50fe265853e53c0f29009d816cf51
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177585"
---
# <a name="scene-system-content-loading"></a><span data-ttu-id="241ec-104">场景系统内容加载</span><span class="sxs-lookup"><span data-stu-id="241ec-104">Scene system content loading</span></span>

<span data-ttu-id="241ec-105">所有内容加载操作都是异步的，默认情况下，所有内容加载都是累加的。</span><span class="sxs-lookup"><span data-stu-id="241ec-105">All content load operations are asynchronous, and by default all content loading is additive.</span></span> <span data-ttu-id="241ec-106">管理器和照明场景永远不会受内容加载操作的影响。</span><span class="sxs-lookup"><span data-stu-id="241ec-106">Manager and lighting scenes are never affected by content loading operations.</span></span> <span data-ttu-id="241ec-107">有关监视加载进度和场景激活的信息，请参阅 [监视内容加载](scene-system-load-progress.md)。</span><span class="sxs-lookup"><span data-stu-id="241ec-107">For information about monitoring load progress and scene activation, see [Monitoring Content Loading](scene-system-load-progress.md).</span></span>

## <a name="loading-content"></a><span data-ttu-id="241ec-108">加载内容</span><span class="sxs-lookup"><span data-stu-id="241ec-108">Loading content</span></span>

<span data-ttu-id="241ec-109">若要加载内容场景，请使用 `LoadContent` 方法：</span><span class="sxs-lookup"><span data-stu-id="241ec-109">To load content scenes use the `LoadContent` method:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a><span data-ttu-id="241ec-110">单个场景加载</span><span class="sxs-lookup"><span data-stu-id="241ec-110">Single scene loading</span></span>

<span data-ttu-id="241ec-111">可以通过可选参数实现单个场景负载的 `mode` 等效项。</span><span class="sxs-lookup"><span data-stu-id="241ec-111">The equivalent of a single scene load can be achieved via the optional `mode` argument.</span></span> <span data-ttu-id="241ec-112">`LoadSceneMode.Single` 将先卸载所有已加载的内容场景，然后再继续加载。</span><span class="sxs-lookup"><span data-stu-id="241ec-112">`LoadSceneMode.Single` will first unload all loaded content scenes before proceeding with the load.</span></span>

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

## <a name="next--previous-scene-loading"></a><span data-ttu-id="241ec-113">下一个/上一个场景加载</span><span class="sxs-lookup"><span data-stu-id="241ec-113">Next / previous scene loading</span></span>

<span data-ttu-id="241ec-114">可以按生成索引的顺序单一加载内容。</span><span class="sxs-lookup"><span data-stu-id="241ec-114">Content can be singly loaded in order of build index.</span></span> <span data-ttu-id="241ec-115">这适用于展示可让用户一一完成一组演示场景的应用程序。</span><span class="sxs-lookup"><span data-stu-id="241ec-115">This is useful for showcase applications that take users through a set of demonstration scenes one-by-one.</span></span>

![播放器设置中的生成中的当前场景](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

<span data-ttu-id="241ec-117">请注意，下一个 /prev 内容加载默认使用 LoadSceneMode.Single 来确保卸载以前的内容。</span><span class="sxs-lookup"><span data-stu-id="241ec-117">Note that next / prev content loading uses LoadSceneMode.Single by default to ensure that the previous content is unloaded.</span></span>

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

<span data-ttu-id="241ec-118">`PrevContentExists` 如果至少有一个内容场景的生成索引低于当前加载的最低生成索引，则 将返回 true。</span><span class="sxs-lookup"><span data-stu-id="241ec-118">`PrevContentExists` will return true if there is at least one content scene that has a lower build index than the lowest build index currently loaded.</span></span> <span data-ttu-id="241ec-119">`NextContentExists` 如果至少有一个内容场景的生成索引高于当前加载的最高生成索引，则 将返回 true。</span><span class="sxs-lookup"><span data-stu-id="241ec-119">`NextContentExists` will return true if there is at least one content scene that has a higher build index than the highest build index currently loaded.</span></span>

<span data-ttu-id="241ec-120">如果参数 `wrap` 为 true，则内容将循环回第一个/最后一个生成索引。</span><span class="sxs-lookup"><span data-stu-id="241ec-120">If the `wrap` argument is true, content will loop back to the first / last build index.</span></span> <span data-ttu-id="241ec-121">这无需检查下一个/以前的内容：</span><span class="sxs-lookup"><span data-stu-id="241ec-121">This removes the need to check for next / previous content:</span></span>

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

## <a name="loading-by-tag"></a><span data-ttu-id="241ec-122">按标记加载</span><span class="sxs-lookup"><span data-stu-id="241ec-122">Loading by tag</span></span>

![按标记加载内容场景](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

<span data-ttu-id="241ec-124">有时需要以组加载内容场景。</span><span class="sxs-lookup"><span data-stu-id="241ec-124">It's sometimes desirable to load content scenes in groups.</span></span> <span data-ttu-id="241ec-125">例如，体验的一个阶段可能由多个场景组成，所有这些场景必须同时加载，以正常运行。</span><span class="sxs-lookup"><span data-stu-id="241ec-125">Eg, a stage of an experience may be composed of multiple scenes, all of which must be loaded simultaneously to function.</span></span> <span data-ttu-id="241ec-126">为方便此操作，可以标记场景，然后加载或卸载这些场景以及该标记。</span><span class="sxs-lookup"><span data-stu-id="241ec-126">To facilitate this, you can tag your scenes and then load them or unload them with that tag.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

<span data-ttu-id="241ec-127">如果艺术家希望合并/删除体验中的元素而无需修改脚本，则按标记加载也很有用。</span><span class="sxs-lookup"><span data-stu-id="241ec-127">Loading by tag can also be useful if artists want to incorporate / remove elements from an experience without having to modify scripts.</span></span> <span data-ttu-id="241ec-128">例如，运行包含以下两组标记的此脚本会产生不同的结果：</span><span class="sxs-lookup"><span data-stu-id="241ec-128">For instance, running this script with the following two sets of tags produces different results:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a><span data-ttu-id="241ec-129">测试内容</span><span class="sxs-lookup"><span data-stu-id="241ec-129">Testing content</span></span>

<span data-ttu-id="241ec-130">场景名称</span><span class="sxs-lookup"><span data-stu-id="241ec-130">Scene Name</span></span> | <span data-ttu-id="241ec-131">场景标记</span><span class="sxs-lookup"><span data-stu-id="241ec-131">Scene Tag</span></span> | <span data-ttu-id="241ec-132">由脚本加载</span><span class="sxs-lookup"><span data-stu-id="241ec-132">Loaded by script</span></span>
---|---|---
<span data-ttu-id="241ec-133">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="241ec-133">DebugTerrainPhysics</span></span> | <span data-ttu-id="241ec-134">地形</span><span class="sxs-lookup"><span data-stu-id="241ec-134">Terrain</span></span> | <span data-ttu-id="241ec-135">•</span><span class="sxs-lookup"><span data-stu-id="241ec-135">•</span></span>
<span data-ttu-id="241ec-136">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="241ec-136">StructureTesting</span></span> | <span data-ttu-id="241ec-137">結構</span><span class="sxs-lookup"><span data-stu-id="241ec-137">Structures</span></span> | <span data-ttu-id="241ec-138">•</span><span class="sxs-lookup"><span data-stu-id="241ec-138">•</span></span>
<span data-ttu-id="241ec-139">使用"设备"工具</span><span class="sxs-lookup"><span data-stu-id="241ec-139">VegetationTools</span></span> | <span data-ttu-id="241ec-140">植被</span><span class="sxs-lookup"><span data-stu-id="241ec-140">Vegetation</span></span> | <span data-ttu-id="241ec-141">•</span><span class="sxs-lookup"><span data-stu-id="241ec-141">•</span></span>
<span data-ttu-id="241ec-142">Mountain</span><span class="sxs-lookup"><span data-stu-id="241ec-142">Mountain</span></span> | <span data-ttu-id="241ec-143">地形</span><span class="sxs-lookup"><span data-stu-id="241ec-143">Terrain</span></span> | <span data-ttu-id="241ec-144">•</span><span class="sxs-lookup"><span data-stu-id="241ec-144">•</span></span>
<span data-ttu-id="241ec-145">Cabin</span><span class="sxs-lookup"><span data-stu-id="241ec-145">Cabin</span></span> | <span data-ttu-id="241ec-146">結構</span><span class="sxs-lookup"><span data-stu-id="241ec-146">Structures</span></span> | <span data-ttu-id="241ec-147">•</span><span class="sxs-lookup"><span data-stu-id="241ec-147">•</span></span>
<span data-ttu-id="241ec-148">Trees</span><span class="sxs-lookup"><span data-stu-id="241ec-148">Trees</span></span> | <span data-ttu-id="241ec-149">植被</span><span class="sxs-lookup"><span data-stu-id="241ec-149">Vegetation</span></span> | <span data-ttu-id="241ec-150">•</span><span class="sxs-lookup"><span data-stu-id="241ec-150">•</span></span>

### <a name="final-content"></a><span data-ttu-id="241ec-151">最终内容</span><span class="sxs-lookup"><span data-stu-id="241ec-151">Final content</span></span>

<span data-ttu-id="241ec-152">场景名称</span><span class="sxs-lookup"><span data-stu-id="241ec-152">Scene Name</span></span> | <span data-ttu-id="241ec-153">场景标记</span><span class="sxs-lookup"><span data-stu-id="241ec-153">Scene Tag</span></span> | <span data-ttu-id="241ec-154">由脚本加载</span><span class="sxs-lookup"><span data-stu-id="241ec-154">Loaded by script</span></span>
---|---|---
<span data-ttu-id="241ec-155">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="241ec-155">DebugTerrainPhysics</span></span> | <span data-ttu-id="241ec-156">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="241ec-156">DoNotInclude</span></span> |
<span data-ttu-id="241ec-157">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="241ec-157">StructureTesting</span></span> | <span data-ttu-id="241ec-158">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="241ec-158">DoNotInclude</span></span> |
<span data-ttu-id="241ec-159">使用"设备"工具</span><span class="sxs-lookup"><span data-stu-id="241ec-159">VegetationTools</span></span> | <span data-ttu-id="241ec-160">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="241ec-160">DoNotInclude</span></span> |
<span data-ttu-id="241ec-161">Mountain</span><span class="sxs-lookup"><span data-stu-id="241ec-161">Mountain</span></span> | <span data-ttu-id="241ec-162">地形</span><span class="sxs-lookup"><span data-stu-id="241ec-162">Terrain</span></span> | <span data-ttu-id="241ec-163">•</span><span class="sxs-lookup"><span data-stu-id="241ec-163">•</span></span>
<span data-ttu-id="241ec-164">Cabin</span><span class="sxs-lookup"><span data-stu-id="241ec-164">Cabin</span></span> | <span data-ttu-id="241ec-165">結構</span><span class="sxs-lookup"><span data-stu-id="241ec-165">Structures</span></span> | <span data-ttu-id="241ec-166">•</span><span class="sxs-lookup"><span data-stu-id="241ec-166">•</span></span>
<span data-ttu-id="241ec-167">Trees</span><span class="sxs-lookup"><span data-stu-id="241ec-167">Trees</span></span> | <span data-ttu-id="241ec-168">植被</span><span class="sxs-lookup"><span data-stu-id="241ec-168">Vegetation</span></span> | <span data-ttu-id="241ec-169">•</span><span class="sxs-lookup"><span data-stu-id="241ec-169">•</span></span>

---

## <a name="editor-behavior"></a><span data-ttu-id="241ec-170">编辑器行为</span><span class="sxs-lookup"><span data-stu-id="241ec-170">Editor behavior</span></span>

<span data-ttu-id="241ec-171">可以使用场景系统的服务检查器在编辑器和播放模式下执行 [所有这些操作。](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span><span class="sxs-lookup"><span data-stu-id="241ec-171">You can perform all these operations in editor and in play mode by using the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="241ec-172">在编辑模式下，场景加载是即时的，而在播放模式下，你可以观察加载进度并使用 [激活令牌。](scene-system-load-progress.md)</span><span class="sxs-lookup"><span data-stu-id="241ec-172">In edit mode scene loads will be instantaneous, while in play mode you can observe loading progress and use [activation tokens.](scene-system-load-progress.md)</span></span>

![检查器中的场景系统，突出显示了内容加载](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
