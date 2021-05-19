---
title: 场景转换服务概述
description: MRTK 中的场景转换文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， SceneTransition，
ms.openlocfilehash: 5ea76b572b3cddc097e8266d3c31f152b63a13aa
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144288"
---
# <a name="scene-transition-service"></a><span data-ttu-id="a90e1-104">场景转换服务</span><span class="sxs-lookup"><span data-stu-id="a90e1-104">Scene transition service</span></span>

<span data-ttu-id="a90e1-105">此扩展简化了以下业务：淡出场景、显示进度指示器、加载场景，然后淡入。</span><span class="sxs-lookup"><span data-stu-id="a90e1-105">This extension simplifies the business of fading out a scene, displaying a progress indicator, loading a scene, then fading back in.</span></span>

<span data-ttu-id="a90e1-106">场景操作由 SceneSystem 服务驱动，但任何基于任务的操作都可用于驱动转换。</span><span class="sxs-lookup"><span data-stu-id="a90e1-106">Scene operations are driven by the SceneSystem service, but any Task-based operation can be used to drive a transition.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="a90e1-107">启用扩展</span><span class="sxs-lookup"><span data-stu-id="a90e1-107">Enabling the extension</span></span>

<span data-ttu-id="a90e1-108">若要启用扩展，请打开 RegisteredServiceProvider 配置文件。</span><span class="sxs-lookup"><span data-stu-id="a90e1-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="a90e1-109">单击"注册新服务提供程序"以添加新配置。</span><span class="sxs-lookup"><span data-stu-id="a90e1-109">Click Register a new Service Provider to add a new configuration.</span></span> <span data-ttu-id="a90e1-110">在"组件类型"字段中，选择"SceneTransitionService"。</span><span class="sxs-lookup"><span data-stu-id="a90e1-110">In the Component Type field, select SceneTransitionService.</span></span> <span data-ttu-id="a90e1-111">在"配置文件"字段中，选择扩展中包含的默认场景转换配置文件。</span><span class="sxs-lookup"><span data-stu-id="a90e1-111">In the Configuration Profile field, select the default scene transition profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="a90e1-112">配置文件选项</span><span class="sxs-lookup"><span data-stu-id="a90e1-112">Profile options</span></span>

### <a name="use-default-progress-indicator"></a><span data-ttu-id="a90e1-113">使用默认进度指示器</span><span class="sxs-lookup"><span data-stu-id="a90e1-113">Use default progress indicator</span></span>

<span data-ttu-id="a90e1-114">如果选中此选项，则当调用 "如果提供了进度指示器对象" 时未提供进度指示器对象时，将使用默认进度指示器 `DoSceneTransition.` 预制项，默认进度指示器将被忽略。</span><span class="sxs-lookup"><span data-stu-id="a90e1-114">If checked, the default progress indicator prefab will be used when no progress indicator object is provided when calling `DoSceneTransition.` If a progress indicator object is provided, the default will be ignored.</span></span>

### <a name="use-fade-color"></a><span data-ttu-id="a90e1-115">使用淡入淡出颜色</span><span class="sxs-lookup"><span data-stu-id="a90e1-115">Use fade color</span></span>

<span data-ttu-id="a90e1-116">如果选中，转换服务将在转换过程中应用淡入淡出。</span><span class="sxs-lookup"><span data-stu-id="a90e1-116">If checked, the transition service will apply a fade during your transition.</span></span> <span data-ttu-id="a90e1-117">可以通过服务的 属性在运行时更改 `UseFadeColor` 此设置。</span><span class="sxs-lookup"><span data-stu-id="a90e1-117">This setting can be changed at runtime via the service's `UseFadeColor` property.</span></span>

### <a name="fade-color"></a><span data-ttu-id="a90e1-118">淡入淡出颜色</span><span class="sxs-lookup"><span data-stu-id="a90e1-118">Fade color</span></span>

<span data-ttu-id="a90e1-119">控制淡入淡出效果的颜色。</span><span class="sxs-lookup"><span data-stu-id="a90e1-119">Controls the color of the fade effect.</span></span> <span data-ttu-id="a90e1-120">将忽略阿尔法。</span><span class="sxs-lookup"><span data-stu-id="a90e1-120">Alpha is ignored.</span></span> <span data-ttu-id="a90e1-121">在通过服务的 属性转换之前，可以在运行时更改 `FadeColor` 此设置。</span><span class="sxs-lookup"><span data-stu-id="a90e1-121">This setting can be changed at runtime prior to a transition via the service's `FadeColor` property.</span></span>

### <a name="fade-targets"></a><span data-ttu-id="a90e1-122">淡化目标</span><span class="sxs-lookup"><span data-stu-id="a90e1-122">Fade targets</span></span>

<span data-ttu-id="a90e1-123">控制将对其应用淡化效果的相机。</span><span class="sxs-lookup"><span data-stu-id="a90e1-123">Controls which cameras will have a fade effect applied to them.</span></span> <span data-ttu-id="a90e1-124">可以通过服务的属性在运行时更改此设置 `FadeTargets` 。</span><span class="sxs-lookup"><span data-stu-id="a90e1-124">This setting can be changed at runtime via the service's `FadeTargets` property.</span></span>

<span data-ttu-id="a90e1-125">设置</span><span class="sxs-lookup"><span data-stu-id="a90e1-125">Setting</span></span> | <span data-ttu-id="a90e1-126">目标照相机</span><span class="sxs-lookup"><span data-stu-id="a90e1-126">Targeted Cameras</span></span>
--- | --- | ---
<span data-ttu-id="a90e1-127">主要</span><span class="sxs-lookup"><span data-stu-id="a90e1-127">Main</span></span> | <span data-ttu-id="a90e1-128">将淡化效果应用于主摄像机。</span><span class="sxs-lookup"><span data-stu-id="a90e1-128">Applies fade effect to the main camera.</span></span>
<span data-ttu-id="a90e1-129">UI</span><span class="sxs-lookup"><span data-stu-id="a90e1-129">UI</span></span> | <span data-ttu-id="a90e1-130">对 UI 层上的照相机应用淡化效果。</span><span class="sxs-lookup"><span data-stu-id="a90e1-130">Applies fade effect to cameras on the UI layer.</span></span> <span data-ttu-id="a90e1-131"> (不会影响覆盖用户界面) </span><span class="sxs-lookup"><span data-stu-id="a90e1-131">(Does not affect overlay UI)</span></span>
<span data-ttu-id="a90e1-132">全部</span><span class="sxs-lookup"><span data-stu-id="a90e1-132">All</span></span> | <span data-ttu-id="a90e1-133">适用于主相机和 UI 照相机。</span><span class="sxs-lookup"><span data-stu-id="a90e1-133">Applies to both main and UI cameras.</span></span>
<span data-ttu-id="a90e1-134">自定义</span><span class="sxs-lookup"><span data-stu-id="a90e1-134">Custom</span></span> | <span data-ttu-id="a90e1-135">适用于通过提供的一组自定义相机 `SetCustomFadeTargetCameras`</span><span class="sxs-lookup"><span data-stu-id="a90e1-135">Applies to a custom set of cameras provided via `SetCustomFadeTargetCameras`</span></span>

### <a name="fade-out-time--fade-in-time"></a><span data-ttu-id="a90e1-136">淡出时间/淡化时间</span><span class="sxs-lookup"><span data-stu-id="a90e1-136">Fade out time / fade in time</span></span>

<span data-ttu-id="a90e1-137">在进入/退出转换的持续时间内的默认设置。</span><span class="sxs-lookup"><span data-stu-id="a90e1-137">Default settings for the duration of a fade on entering / exiting a transition.</span></span> <span data-ttu-id="a90e1-138">可以通过服务的和属性在运行时更改这些 `FadeOutTime` 设置 `FadeInTime` 。</span><span class="sxs-lookup"><span data-stu-id="a90e1-138">These settings can be changed at runtime via the service's `FadeOutTime` and `FadeInTime` properties.</span></span>

### <a name="camera-fader-type"></a><span data-ttu-id="a90e1-139">照相机 fader 类型</span><span class="sxs-lookup"><span data-stu-id="a90e1-139">Camera fader type</span></span>

<span data-ttu-id="a90e1-140">要 `ICameraFader` 使用哪个类向照相机应用淡化效果。</span><span class="sxs-lookup"><span data-stu-id="a90e1-140">Which `ICameraFader` class to use for applying a fade effect to cameras.</span></span> <span data-ttu-id="a90e1-141">默认 `CameraFaderQuad` 类在目标相机靠近剪辑平面的情况下实例化四个具有透明材料的四个。</span><span class="sxs-lookup"><span data-stu-id="a90e1-141">The default `CameraFaderQuad` class instantiates a quad with a transparent material in front of the target camera close to the clip plane.</span></span> <span data-ttu-id="a90e1-142">另一种方法可能是使用 post 效果系统。</span><span class="sxs-lookup"><span data-stu-id="a90e1-142">Another approach might be to use a post effects system.</span></span>

## <a name="using-the-extension"></a><span data-ttu-id="a90e1-143">使用扩展</span><span class="sxs-lookup"><span data-stu-id="a90e1-143">Using the extension</span></span>

<span data-ttu-id="a90e1-144">通过在摄像机淡出时传递运行的任务来使用转换服务。</span><span class="sxs-lookup"><span data-stu-id="a90e1-144">You use the transition service by passing Tasks that are run while the camera is faded out.</span></span>

### <a name="using-scene-system-tasks"></a><span data-ttu-id="a90e1-145">使用场景系统任务</span><span class="sxs-lookup"><span data-stu-id="a90e1-145">Using scene system tasks</span></span>

<span data-ttu-id="a90e1-146">在大多数情况下，你将使用 SceneSystem 服务提供的任务：</span><span class="sxs-lookup"><span data-stu-id="a90e1-146">In most cases you will be using Tasks supplied by the SceneSystem service:</span></span>

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Runs LoadContent task
    // Fades back in
    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}
```

### <a name="using-custom-tasks"></a><span data-ttu-id="a90e1-147">使用自定义任务</span><span class="sxs-lookup"><span data-stu-id="a90e1-147">Using custom tasks</span></span>

<span data-ttu-id="a90e1-148">在其他情况下，你可能想要在不实际加载场景的情况下执行转换：</span><span class="sxs-lookup"><span data-stu-id="a90e1-148">In other cases you may want to perform a transition without actually loading a scene:</span></span>

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Resets scene
    // Fades back in
    await transition.DoSceneTransition(
            () => ResetScene()
        );
}

private async Task ResetScene()
{
    // Go through all enemies in the current scene and move them back to starting positions
}
```

<span data-ttu-id="a90e1-149">或者，你可能想要在不使用 SceneSystem 服务的情况下加载场景：</span><span class="sxs-lookup"><span data-stu-id="a90e1-149">Or you may want to load a scene without using the SceneSystem service:</span></span>

```c#
private async void TransitionToScene()
{
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Loads scene using Unity's scene manager
    // Fades back in
    await transition.DoSceneTransition(
            () => LoadScene("TestScene1")
        );
}

private async Task LoadScene(string sceneName)
{
    AsyncOperation asyncOp = SceneManager.LoadSceneAsync(sceneName, LoadSceneMode.Additive);
    while (!asyncOp.isDone)
    {
        await Task.Yield();
    }
}
```

### <a name="using-multiple-tasks"></a><span data-ttu-id="a90e1-150">使用多个任务</span><span class="sxs-lookup"><span data-stu-id="a90e1-150">Using multiple tasks</span></span>

<span data-ttu-id="a90e1-151">还可以提供多个任务，这些任务将按以下顺序执行：</span><span class="sxs-lookup"><span data-stu-id="a90e1-151">You can also supply multiple tasks, which will be executed in order:</span></span>

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    // Fades out
    // Sets time scale to 0
    // Fades out audio to 0
    // Loads TestScene1
    // Fades in audio to 1
    // Sets time scale to 1
    // Fades back in
    await transition.DoSceneTransition(
            () => SetTimescale(0f),
            () => FadeAudio(0f, 1f),
            () => sceneSystem.LoadContent("TestScene1"),
            () => FadeAudio(1f, 1f),
            () => SetTimescale(1f)
        );
}

private async Task SetTimescale(float targetTime)
{
    Time.timeScale = targetTime;
    await Task.Yield();
}

private async Task FadeAudio(float targetVolume, float duration)
{
    float startTime = Time.realtimeSinceStartup;
    float startVolume = AudioListener.volume;
    while (Time.realtimeSinceStartup < startTime + duration)
    {
        AudioListener.volume = Mathf.Lerp(startVolume, targetVolume, Time.realtimeSinceStartup - startTime / duration);
        await Task.Yield();
       }
       AudioListener.volume = targetVolume;
}
```

## <a name="using-the-progress-indicator"></a><span data-ttu-id="a90e1-152">使用进度指示器</span><span class="sxs-lookup"><span data-stu-id="a90e1-152">Using the progress indicator</span></span>

<span data-ttu-id="a90e1-153">进度指示器是实现 接口 `IProgressIndicator` 的一切内容。</span><span class="sxs-lookup"><span data-stu-id="a90e1-153">A progress indicator is anything that implements the `IProgressIndicator` interface.</span></span> <span data-ttu-id="a90e1-154">这可以是初始屏幕、3D 标记加载指示器或提供有关转换进度反馈的任何其他内容。</span><span class="sxs-lookup"><span data-stu-id="a90e1-154">This can take the form of a splash screen, a 3D tagalong loading indicator, or anything else that provides feedback about transition progress.</span></span>

<span data-ttu-id="a90e1-155">如果在 SceneTransitionService 配置文件中选中 ，则转换开始时将实例 `UseDefaultProgressIndicator` 化进度指示器。</span><span class="sxs-lookup"><span data-stu-id="a90e1-155">If `UseDefaultProgressIndicator` is checked in the SceneTransitionService profile, a progress indicator will be instantiated when a transition begins.</span></span> <span data-ttu-id="a90e1-156">在转换期间，可以通过该服务的 和 方法访问此指示器 `Progress` `Message` 的 和 `SetProgressValue` `SetProgressMessage` 属性。</span><span class="sxs-lookup"><span data-stu-id="a90e1-156">For the duration of the transition this indicator's `Progress` and `Message` properties can be accessed via that service's `SetProgressValue` and `SetProgressMessage` methods.</span></span>

```c#
private async void TransitionToScene()
{
    IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
    ISceneTransitionService transition = MixedRealityToolkit.Instance.GetService<ISceneTransitionService>();

    ListenToSceneTransition(sceneSystem, transition);

    await transition.DoSceneTransition(
            () => sceneSystem.LoadContent("TestScene1")
        );
}

private async void ListenToSceneTransition(IMixedRealitySceneSystem sceneSystem, ISceneTransitionService transition)
{
    transition.SetProgressMessage("Starting transition...");

    while (transition.TransitionInProgress)
    {
        if (sceneSystem.SceneOperationInProgress)
        {
            transition.SetProgressMessage("Loading scene...");
            transition.SetProgressValue(sceneSystem.SceneOperationProgress);
        }
        else
        {
            transition.SetProgressMessage("Finished loading scene...");
            transition.SetProgressValue(1);
        }

        await Task.Yield();
    }
}
```

<span data-ttu-id="a90e1-157">或者，在调用 `DoSceneTransition` 时，可以通过可选参数提供自己的进度 `progressIndicator` 指示器。</span><span class="sxs-lookup"><span data-stu-id="a90e1-157">Alternatively, when calling `DoSceneTransition` you can supply your own progress indicator via the optional `progressIndicator` argument.</span></span> <span data-ttu-id="a90e1-158">这将替代默认进度指示器。</span><span class="sxs-lookup"><span data-stu-id="a90e1-158">This will override the default progress indicator.</span></span>
