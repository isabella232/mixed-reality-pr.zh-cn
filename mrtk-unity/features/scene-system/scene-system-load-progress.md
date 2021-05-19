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
# <a name="monitoring-content-loading"></a><span data-ttu-id="07efc-104">监视内容加载</span><span class="sxs-lookup"><span data-stu-id="07efc-104">Monitoring content loading</span></span>

## <a name="scene-operation-progress"></a><span data-ttu-id="07efc-105">场景操作进度</span><span class="sxs-lookup"><span data-stu-id="07efc-105">Scene operation progress</span></span>

<span data-ttu-id="07efc-106">加载或卸载内容时， `SceneOperationInProgress` 属性将返回 true。</span><span class="sxs-lookup"><span data-stu-id="07efc-106">When content is being loaded or unloaded, the `SceneOperationInProgress` property will return true.</span></span> <span data-ttu-id="07efc-107">可以通过属性监视此操作的进度 `SceneOperationProgress` 。</span><span class="sxs-lookup"><span data-stu-id="07efc-107">You can monitor the progress of this operation via the `SceneOperationProgress` property.</span></span>

<span data-ttu-id="07efc-108">`SceneOperationProgress`值是所有当前异步场景操作的平均数。</span><span class="sxs-lookup"><span data-stu-id="07efc-108">The `SceneOperationProgress` value is the average of all current async scene operations.</span></span> <span data-ttu-id="07efc-109">内容加载开始时， `SceneOperationProgress` 将为零。</span><span class="sxs-lookup"><span data-stu-id="07efc-109">At the start of a content load, `SceneOperationProgress` will be zero.</span></span> <span data-ttu-id="07efc-110">完全完成后， `SceneOperationProgress` 将设置为1，并且在下一操作发生之前将保持为1。</span><span class="sxs-lookup"><span data-stu-id="07efc-110">Once fully completed, `SceneOperationProgress` will be set to 1 and will remain at 1 until the next operation takes place.</span></span> <span data-ttu-id="07efc-111">请注意，只有内容场景操作会影响这些属性。</span><span class="sxs-lookup"><span data-stu-id="07efc-111">Note that only content scene operations affect these properties.</span></span>

<span data-ttu-id="07efc-112">这些属性反映了从开始到完成的 *整个操作* 的状态，即使该操作包括多个步骤：</span><span class="sxs-lookup"><span data-stu-id="07efc-112">These properties reflect the state of an *entire operation* from start to finish, even if that operation includes multiple steps:</span></span>

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

### <a name="progress-examples"></a><span data-ttu-id="07efc-113">进度示例</span><span class="sxs-lookup"><span data-stu-id="07efc-113">Progress examples</span></span>

<span data-ttu-id="07efc-114">`SceneOperationInProgress` 如果在加载内容时应挂起活动，则会很有用：</span><span class="sxs-lookup"><span data-stu-id="07efc-114">`SceneOperationInProgress` can be useful if activity should be suspended while content is being loaded:</span></span>

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

<span data-ttu-id="07efc-115">`SceneOperationProgress` 可用于显示进度对话框：</span><span class="sxs-lookup"><span data-stu-id="07efc-115">`SceneOperationProgress` can be used to display progress dialogs:</span></span>

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

## <a name="monitoring-with-actions"></a><span data-ttu-id="07efc-116">监视操作</span><span class="sxs-lookup"><span data-stu-id="07efc-116">Monitoring with actions</span></span>

<span data-ttu-id="07efc-117">场景系统提供了若干操作，可让你在加载或卸载场景时了解这些操作。</span><span class="sxs-lookup"><span data-stu-id="07efc-117">The Scene System provides several actions to let you know when scenes are being loaded or unloaded.</span></span> <span data-ttu-id="07efc-118">每个操作都将对受影响场景的名称进行中继。</span><span class="sxs-lookup"><span data-stu-id="07efc-118">Each action relays the name of the affected scene.</span></span>

<span data-ttu-id="07efc-119">如果加载或卸载操作涉及多个场景，则会针对每个受影响的场景调用相关操作一次。</span><span class="sxs-lookup"><span data-stu-id="07efc-119">If a load or unload operation involves multiple scenes, the relevant actions will be invoked once per affected scene.</span></span> <span data-ttu-id="07efc-120">加载或卸载操作 *完全完成* 后，也会同时调用它们。</span><span class="sxs-lookup"><span data-stu-id="07efc-120">They are also invoked all at once when the load or unload operation is *fully completed.*</span></span> <span data-ttu-id="07efc-121">出于此原因，建议你使用 *OnWillUnload* 操作来检测 *将* 销毁的内容，而不是使用 *OnUnloaded* 操作在事实下检测已销毁的内容。</span><span class="sxs-lookup"><span data-stu-id="07efc-121">For this reason it's recommended that you use *OnWillUnload* actions to detect content that *will* be destroyed, as opposed to using *OnUnloaded* actions to detect destroyed content after the fact.</span></span>

<span data-ttu-id="07efc-122">反向，因为仅当激活并完全加载所有场景时才会调用 *OnLoaded* 操作，而使用 *OnLoaded* 操作来检测和使用新内容是安全的。</span><span class="sxs-lookup"><span data-stu-id="07efc-122">On the flip side, because *OnLoaded* actions are only invoked when all scenes are activated and fully loaded, using *OnLoaded* actions to detect and use new content is guaranteed to be safe.</span></span>

<span data-ttu-id="07efc-123">操作</span><span class="sxs-lookup"><span data-stu-id="07efc-123">Action</span></span> | <span data-ttu-id="07efc-124">调用时</span><span class="sxs-lookup"><span data-stu-id="07efc-124">When it's invoked</span></span> | <span data-ttu-id="07efc-125">内容场景</span><span class="sxs-lookup"><span data-stu-id="07efc-125">Content Scenes</span></span> | <span data-ttu-id="07efc-126">照明场景</span><span class="sxs-lookup"><span data-stu-id="07efc-126">Lighting Scenes</span></span> | <span data-ttu-id="07efc-127">管理器场景</span><span class="sxs-lookup"><span data-stu-id="07efc-127">Manager Scenes</span></span>
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | <span data-ttu-id="07efc-128">在加载内容场景之前</span><span class="sxs-lookup"><span data-stu-id="07efc-128">Just prior to a content scene load</span></span> | <span data-ttu-id="07efc-129">•</span><span class="sxs-lookup"><span data-stu-id="07efc-129">•</span></span> | |  
`OnContentLoaded` | <span data-ttu-id="07efc-130">加载操作中所有内容场景完全加载并激活后</span><span class="sxs-lookup"><span data-stu-id="07efc-130">After all content scenes in a load operation have been fully loaded and activated</span></span> | <span data-ttu-id="07efc-131">•</span><span class="sxs-lookup"><span data-stu-id="07efc-131">•</span></span> | |
`OnWillUnloadContent` | <span data-ttu-id="07efc-132">在内容场景卸载操作之前</span><span class="sxs-lookup"><span data-stu-id="07efc-132">Just prior to a content scene unload operation</span></span> | <span data-ttu-id="07efc-133">•</span><span class="sxs-lookup"><span data-stu-id="07efc-133">•</span></span> | |
`OnContentUnloaded` | <span data-ttu-id="07efc-134">卸载操作中所有内容场景完全卸载后</span><span class="sxs-lookup"><span data-stu-id="07efc-134">After all content scenes in an unload operation have been fully unloaded</span></span> | <span data-ttu-id="07efc-135">•</span><span class="sxs-lookup"><span data-stu-id="07efc-135">•</span></span> | |
`OnWillLoadLighting` | <span data-ttu-id="07efc-136">在照明场景加载之前</span><span class="sxs-lookup"><span data-stu-id="07efc-136">Just prior to a lighting scene load</span></span> | | <span data-ttu-id="07efc-137">•</span><span class="sxs-lookup"><span data-stu-id="07efc-137">•</span></span> |
`OnLightingLoaded` | <span data-ttu-id="07efc-138">完全加载并激活照明场景后</span><span class="sxs-lookup"><span data-stu-id="07efc-138">After a lighting scene has been fully loaded and activated</span></span>| | <span data-ttu-id="07efc-139">•</span><span class="sxs-lookup"><span data-stu-id="07efc-139">•</span></span> |
`OnWillUnloadLighting` | <span data-ttu-id="07efc-140">在照明场景卸载之前</span><span class="sxs-lookup"><span data-stu-id="07efc-140">Just prior to a lighting scene unload</span></span> | | <span data-ttu-id="07efc-141">•</span><span class="sxs-lookup"><span data-stu-id="07efc-141">•</span></span> |
`OnLightingUnloaded` | <span data-ttu-id="07efc-142">完全卸载照明场景后</span><span class="sxs-lookup"><span data-stu-id="07efc-142">After a lighting scene has been fully unloaded</span></span> | | <span data-ttu-id="07efc-143">•</span><span class="sxs-lookup"><span data-stu-id="07efc-143">•</span></span> |
`OnWillLoadScene` | <span data-ttu-id="07efc-144">在场景加载之前</span><span class="sxs-lookup"><span data-stu-id="07efc-144">Just prior to a scene load</span></span> | <span data-ttu-id="07efc-145">•</span><span class="sxs-lookup"><span data-stu-id="07efc-145">•</span></span> | <span data-ttu-id="07efc-146">•</span><span class="sxs-lookup"><span data-stu-id="07efc-146">•</span></span> | <span data-ttu-id="07efc-147">•</span><span class="sxs-lookup"><span data-stu-id="07efc-147">•</span></span>
`OnSceneLoaded` | <span data-ttu-id="07efc-148">操作中所有场景完全加载并激活后</span><span class="sxs-lookup"><span data-stu-id="07efc-148">After all scenes in an operation are fully loaded and activated</span></span> | <span data-ttu-id="07efc-149">•</span><span class="sxs-lookup"><span data-stu-id="07efc-149">•</span></span> | <span data-ttu-id="07efc-150">•</span><span class="sxs-lookup"><span data-stu-id="07efc-150">•</span></span> | <span data-ttu-id="07efc-151">•</span><span class="sxs-lookup"><span data-stu-id="07efc-151">•</span></span>
`OnWillUnloadScene` | <span data-ttu-id="07efc-152">在卸载场景之前</span><span class="sxs-lookup"><span data-stu-id="07efc-152">Just prior to a scene unload</span></span> | <span data-ttu-id="07efc-153">•</span><span class="sxs-lookup"><span data-stu-id="07efc-153">•</span></span> | <span data-ttu-id="07efc-154">•</span><span class="sxs-lookup"><span data-stu-id="07efc-154">•</span></span> | <span data-ttu-id="07efc-155">•</span><span class="sxs-lookup"><span data-stu-id="07efc-155">•</span></span>
`OnSceneUnloaded` | <span data-ttu-id="07efc-156">完全卸载场景后</span><span class="sxs-lookup"><span data-stu-id="07efc-156">After a scene is fully unloaded</span></span> |  <span data-ttu-id="07efc-157">•</span><span class="sxs-lookup"><span data-stu-id="07efc-157">•</span></span> | <span data-ttu-id="07efc-158">•</span><span class="sxs-lookup"><span data-stu-id="07efc-158">•</span></span> | <span data-ttu-id="07efc-159">•</span><span class="sxs-lookup"><span data-stu-id="07efc-159">•</span></span>

### <a name="action-examples"></a><span data-ttu-id="07efc-160">操作示例</span><span class="sxs-lookup"><span data-stu-id="07efc-160">Action examples</span></span>

<span data-ttu-id="07efc-161">使用操作和协同例程而不是更新的另一个进度对话框示例：</span><span class="sxs-lookup"><span data-stu-id="07efc-161">Another progress dialog example using actions and a coroutine instead of Update:</span></span>

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

## <a name="controlling-scene-activation"></a><span data-ttu-id="07efc-162">控制场景激活</span><span class="sxs-lookup"><span data-stu-id="07efc-162">Controlling scene activation</span></span>

<span data-ttu-id="07efc-163">默认情况下，内容场景设置为在加载时激活。</span><span class="sxs-lookup"><span data-stu-id="07efc-163">By default content scenes are set to activate when loaded.</span></span> <span data-ttu-id="07efc-164">如果要手动控制场景激活，则可以 `SceneActivationToken` 将传递到任何内容加载方法。</span><span class="sxs-lookup"><span data-stu-id="07efc-164">If you want to control scene activation manually, you can pass a `SceneActivationToken` to any content load method.</span></span> <span data-ttu-id="07efc-165">如果一个操作正在加载多个内容场景，此激活令牌将应用于所有场景。</span><span class="sxs-lookup"><span data-stu-id="07efc-165">If multiple content scenes are being loaded by a single operation, this activation token will apply to all scenes.</span></span>

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

## <a name="checking-which-content-is-loaded"></a><span data-ttu-id="07efc-166">检查加载的内容</span><span class="sxs-lookup"><span data-stu-id="07efc-166">Checking which content is loaded</span></span>

<span data-ttu-id="07efc-167">`ContentSceneNames`属性按生成索引的顺序提供可用内容场景的数组。</span><span class="sxs-lookup"><span data-stu-id="07efc-167">The `ContentSceneNames` property provides an array of available content scenes in order of build index.</span></span> <span data-ttu-id="07efc-168">可以通过检查是否已加载这些场景 `IsContentLoaded(string contentName)` 。</span><span class="sxs-lookup"><span data-stu-id="07efc-168">You can check whether these scenes are loaded via `IsContentLoaded(string contentName)`.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```
