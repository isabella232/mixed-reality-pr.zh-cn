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
# <a name="scene-system-content-loading"></a>场景系统内容加载

所有内容加载操作都是异步的，默认情况下，所有内容加载都是累加的。 管理器和照明场景永远不会受内容加载操作的影响。 有关监视加载进度和场景激活的信息，请参阅 [监视内容加载](scene-system-load-progress.md)。

## <a name="loading-content"></a>加载内容

若要加载内容场景，请使用 `LoadContent` 方法：

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a>单个场景加载

可以通过可选参数实现单个场景负载的 `mode` 等效项。 `LoadSceneMode.Single` 将先卸载所有已加载的内容场景，然后再继续加载。

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

可以按生成索引的顺序单一加载内容。 这适用于展示可让用户一一完成一组演示场景的应用程序。

![播放器设置中的生成中的当前场景](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

请注意，下一个 /prev 内容加载默认使用 LoadSceneMode.Single 来确保卸载以前的内容。

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

`PrevContentExists` 如果至少有一个内容场景的生成索引低于当前加载的最低生成索引，则 将返回 true。 `NextContentExists` 如果至少有一个内容场景的生成索引高于当前加载的最高生成索引，则 将返回 true。

如果参数 `wrap` 为 true，则内容将循环回第一个/最后一个生成索引。 这无需检查下一个/以前的内容：

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

有时需要以组加载内容场景。 例如，体验的一个阶段可能由多个场景组成，所有这些场景必须同时加载，以正常运行。 为方便此操作，可以标记场景，然后加载或卸载这些场景以及该标记。

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

如果艺术家希望合并/删除体验中的元素而无需修改脚本，则按标记加载也很有用。 例如，运行包含以下两组标记的此脚本会产生不同的结果：

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
使用"设备"工具 | 植被 | •
Mountain | 地形 | •
Cabin | 結構 | •
Trees | 植被 | •

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
