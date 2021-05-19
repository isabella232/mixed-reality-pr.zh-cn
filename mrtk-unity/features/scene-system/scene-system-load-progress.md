---
title: 场景系统加载进度
description: 有关 MRTK 中的场景内容加载的文档
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 51b5d4d00d65491a0476068bbdc256ffce67412b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144402"
---
# <a name="monitoring-content-loading"></a>监视内容加载

## <a name="scene-operation-progress"></a>场景操作进度

加载或卸载内容时， `SceneOperationInProgress` 属性将返回 true。 可以通过属性监视此操作的进度 `SceneOperationProgress` 。

`SceneOperationProgress`值是所有当前异步场景操作的平均数。 内容加载开始时， `SceneOperationProgress` 将为零。 完全完成后， `SceneOperationProgress` 将设置为1，并且在下一操作发生之前将保持为1。 请注意，只有内容场景操作会影响这些属性。

这些属性反映了从开始到完成的 *整个操作* 的状态，即使该操作包括多个步骤：

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// First do an additive scene load
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
await sceneSystem.LoadContent("ContentScene1");

// Now do a single scene load
// This will result in two actions back-to-back
// First "ContentScene1" will be unloaded
// Then "ContentScene2" will be loaded
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
sceneSystem.LoadContent("ContentScene2", LoadSceneMode.Single)
```

### <a name="progress-examples"></a>进度示例

`SceneOperationInProgress` 如果在加载内容时应挂起活动，则会很有用：

```c#
public class FooManager : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        // Don't update foos while a scene operation is in progress
        if (sceneSystem.SceneOperationInProgress)
        {
            return;
        }

        // Update foos
        ...
    }
    ...
}
```

`SceneOperationProgress` 可用于显示进度对话框：

```c#
public class ProgressDialog : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        if (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
        }
        else
        {
            HideProgressIndicator();
        }
    }
    ...
}
```

---

## <a name="monitoring-with-actions"></a>监视操作

场景系统提供了若干操作，可让你在加载或卸载场景时了解这些操作。 每个操作都将对受影响场景的名称进行中继。

如果加载或卸载操作涉及多个场景，则会针对每个受影响的场景调用相关操作一次。 加载或卸载操作 *完全完成* 后，也会同时调用它们。 出于此原因，建议你使用 *OnWillUnload* 操作来检测 *将* 销毁的内容，而不是使用 *OnUnloaded* 操作在事实下检测已销毁的内容。

反向，因为仅当激活并完全加载所有场景时才会调用 *OnLoaded* 操作，而使用 *OnLoaded* 操作来检测和使用新内容是安全的。

操作 | 调用时 | 内容场景 | 照明场景 | 管理器场景
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | 在加载内容场景之前 | • | |  
`OnContentLoaded` | 加载操作中所有内容场景完全加载并激活后 | • | |
`OnWillUnloadContent` | 在内容场景卸载操作之前 | • | |
`OnContentUnloaded` | 卸载操作中所有内容场景完全卸载后 | • | |
`OnWillLoadLighting` | 在照明场景加载之前 | | • |
`OnLightingLoaded` | 完全加载并激活照明场景后| | • |
`OnWillUnloadLighting` | 在照明场景卸载之前 | | • |
`OnLightingUnloaded` | 完全卸载照明场景后 | | • |
`OnWillLoadScene` | 在场景加载之前 | • | • | •
`OnSceneLoaded` | 操作中所有场景完全加载并激活后 | • | • | •
`OnWillUnloadScene` | 在卸载场景之前 | • | • | •
`OnSceneUnloaded` | 完全卸载场景后 |  • | • | •

### <a name="action-examples"></a>操作示例

使用操作和协同例程而不是更新的另一个进度对话框示例：

```c#
public class ProgressDialog : MonoBehaviour
{
    private bool displayingProgress = false;

    private void Start()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
        sceneSystem.OnWillLoadContent += HandleSceneOperation;
        sceneSystem.OnWillUnloadContent += HandleSceneOperation;
    }

    private void HandleSceneOperation (string sceneName)
    {
        // This may be invoked multiple times per frame - once per scene being loaded or unloaded.
        // So filter the events appropriately.
        if (displayingProgress)
        {
            return;
        }

        displayingProgress = true;
        StartCoroutine(DisplayProgress());
    }

    private IEnumerator DisplayProgress()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        while (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
            yield return null;
        }

        HideProgressIndicator();
        displayingProgress = false;
    }

    ...
}
```

---

## <a name="controlling-scene-activation"></a>控制场景激活

默认情况下，内容场景设置为在加载时激活。 如果要手动控制场景激活，则可以 `SceneActivationToken` 将传递到任何内容加载方法。 如果一个操作正在加载多个内容场景，此激活令牌将应用于所有场景。

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

SceneActivationToken activationToken = new SceneActivationToken();

// Load the content and pass the activation token
sceneSystem.LoadContent(new string[] { "ContentScene1", "ContentScene2", "ContentScene3" }, LoadSceneMode.Additive, activationToken);

// Wait until all users have joined the experience
while (!AllUsersHaveJoinedExperience())
{
    await Task.Yield();
}

// Let scene system know we're ready to activate all scenes
activationToken.AllowSceneActivation = true;

// Wait for all scenes to be fully loaded and activated
while (sceneSystem.SceneOperationInProgress)
{
    await Task.Yield();
}

// Proceed with experience
```

---

## <a name="checking-which-content-is-loaded"></a>检查加载的内容

`ContentSceneNames`属性按生成索引的顺序提供可用内容场景的数组。 可以通过检查是否已加载这些场景 `IsContentLoaded(string contentName)` 。

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
