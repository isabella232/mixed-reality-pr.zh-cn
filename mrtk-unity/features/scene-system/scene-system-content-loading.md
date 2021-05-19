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
# <a name="content-scene-loading"></a>内容场景加载

所有内容加载操作都是异步的，默认情况下，所有内容加载都是累加的。 管理器和照明场景从不受内容加载操作影响。 有关监视加载进度和场景激活的信息，请参阅 [监视内容加载](scene-system-load-progress.md)。

## <a name="loading-content"></a>正在加载内容

若要加载内容场景，请使用 `LoadContent` 方法：

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a>单场景加载

可以通过可选的参数来实现单个场景加载的等效项 `mode` 。 `LoadSceneMode.Single` 将首先卸载所有加载的内容场景，然后再继续进行加载。

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

## <a name="next--previous-scene-loading"></a>下一个/上一个场景加载

可以按生成索引的顺序单独加载内容。 这对于展示每个使用用户一组演示场景的应用程序很有用。

!["在播放机中生成" 设置中的当前场景](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

请注意，在默认情况下，下一项/前一项内容将使用 LoadSceneMode 来确保卸载以前的内容。

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

`PrevContentExists` 如果至少有一个内容场景的生成索引低于当前加载的最低生成索引，将返回 true。 `NextContentExists` 如果至少有一个内容场景具有比当前加载的最高生成索引更高的生成索引，将返回 true。

如果 `wrap` 参数为 true，则内容将循环回到第一个/最后一个生成索引。 这无需检查下一个/以前的内容：

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

## <a name="loading-by-tag"></a>按标记加载

![按标记加载内容场景](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

有时需要将内容场景加载到组中。 例如，经历的阶段可能由多个场景组成，它们必须同时加载，才能正常工作。 为此，可以标记场景，然后加载并加载它们，或将其卸载到该标记。

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

如果艺术家希望在不修改脚本的情况下合并/删除元素，则 "按标记加载" 也很有用。 例如，通过以下两组标记运行此脚本会产生不同的结果：

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a>测试内容

场景名称 | 场景标记 | 由脚本加载
---|---|---
DebugTerrainPhysics | 地形 | •
StructureTesting | 結構 | •
VegetationTools | Vegetation | •
Mountain | 地形 | •
Cabin | 結構 | •
Trees | Vegetation | •

### <a name="final-content"></a>最终内容

场景名称 | 场景标记 | 由脚本加载
---|---|---
DebugTerrainPhysics | DoNotInclude |
StructureTesting | DoNotInclude |
使用"设备"工具 | DoNotInclude |
Mountain | 地形 | •
Cabin | 結構 | •
Trees | 植被 | •

---

## <a name="editor-behavior"></a>编辑器行为

可以使用场景系统的服务检查器在编辑器和播放模式下执行 [所有这些操作。](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) 在编辑模式下，场景加载是即时的，而在播放模式下，你可以观察加载进度并使用 [激活令牌。](scene-system-load-progress.md)

![检查器中的场景系统，突出显示了内容加载](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)
