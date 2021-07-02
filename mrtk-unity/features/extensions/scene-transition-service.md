---
title: 场景转换服务
description: MRTK 中的场景转换文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，SceneTransition，
ms.openlocfilehash: b645012a055f693fdac794b79e24fd20154fdb65
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176213"
---
# <a name="scene-transition-service"></a><span data-ttu-id="79c0b-104">场景转换服务</span><span class="sxs-lookup"><span data-stu-id="79c0b-104">Scene transition service</span></span>

<span data-ttu-id="79c0b-105">此扩展简化了场景的业务，其中显示了进度指示器、加载场景，然后淡入。</span><span class="sxs-lookup"><span data-stu-id="79c0b-105">This extension simplifies the business of fading out a scene, displaying a progress indicator, loading a scene, then fading back in.</span></span>

<span data-ttu-id="79c0b-106">场景操作由 SceneSystem 服务驱动，但任何基于任务的操作都可用于驱动转换。</span><span class="sxs-lookup"><span data-stu-id="79c0b-106">Scene operations are driven by the SceneSystem service, but any Task-based operation can be used to drive a transition.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="79c0b-107">启用扩展</span><span class="sxs-lookup"><span data-stu-id="79c0b-107">Enabling the extension</span></span>

<span data-ttu-id="79c0b-108">若要启用此扩展，请打开 RegisteredServiceProvider 配置文件。</span><span class="sxs-lookup"><span data-stu-id="79c0b-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="79c0b-109">单击 "注册新的服务提供商" 以添加新配置。</span><span class="sxs-lookup"><span data-stu-id="79c0b-109">Click Register a new Service Provider to add a new configuration.</span></span> <span data-ttu-id="79c0b-110">在 "组件类型" 字段中，选择 "SceneTransitionService"。</span><span class="sxs-lookup"><span data-stu-id="79c0b-110">In the Component Type field, select SceneTransitionService.</span></span> <span data-ttu-id="79c0b-111">在 "配置文件" 字段中，选择包含在扩展中的默认场景转换配置文件。</span><span class="sxs-lookup"><span data-stu-id="79c0b-111">In the Configuration Profile field, select the default scene transition profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="79c0b-112">配置文件选项</span><span class="sxs-lookup"><span data-stu-id="79c0b-112">Profile options</span></span>

### <a name="use-default-progress-indicator"></a><span data-ttu-id="79c0b-113">使用默认进度指示器</span><span class="sxs-lookup"><span data-stu-id="79c0b-113">Use default progress indicator</span></span>

<span data-ttu-id="79c0b-114">如果选中，则在提供进度指示器对象时，如果不提供进度指示器对象，则将使用默认的进度指示器 prefab `DoSceneTransition.` ，将忽略默认值。</span><span class="sxs-lookup"><span data-stu-id="79c0b-114">If checked, the default progress indicator prefab will be used when no progress indicator object is provided when calling `DoSceneTransition.` If a progress indicator object is provided, the default will be ignored.</span></span>

### <a name="use-fade-color"></a><span data-ttu-id="79c0b-115">使用淡化颜色</span><span class="sxs-lookup"><span data-stu-id="79c0b-115">Use fade color</span></span>

<span data-ttu-id="79c0b-116">如果选中，转换服务将在转换过程中应用淡化。</span><span class="sxs-lookup"><span data-stu-id="79c0b-116">If checked, the transition service will apply a fade during your transition.</span></span> <span data-ttu-id="79c0b-117">可以通过服务的属性在运行时更改此设置 `UseFadeColor` 。</span><span class="sxs-lookup"><span data-stu-id="79c0b-117">This setting can be changed at runtime via the service's `UseFadeColor` property.</span></span>

### <a name="fade-color"></a><span data-ttu-id="79c0b-118">淡化颜色</span><span class="sxs-lookup"><span data-stu-id="79c0b-118">Fade color</span></span>

<span data-ttu-id="79c0b-119">控制淡化效果的颜色。</span><span class="sxs-lookup"><span data-stu-id="79c0b-119">Controls the color of the fade effect.</span></span> <span data-ttu-id="79c0b-120">将忽略阿尔法。</span><span class="sxs-lookup"><span data-stu-id="79c0b-120">Alpha is ignored.</span></span> <span data-ttu-id="79c0b-121">在通过服务的属性转换之前，可以在运行时更改此设置 `FadeColor` 。</span><span class="sxs-lookup"><span data-stu-id="79c0b-121">This setting can be changed at runtime prior to a transition via the service's `FadeColor` property.</span></span>

### <a name="fade-targets"></a><span data-ttu-id="79c0b-122">淡化目标</span><span class="sxs-lookup"><span data-stu-id="79c0b-122">Fade targets</span></span>

<span data-ttu-id="79c0b-123">控制将对其应用淡化效果的相机。</span><span class="sxs-lookup"><span data-stu-id="79c0b-123">Controls which cameras will have a fade effect applied to them.</span></span> <span data-ttu-id="79c0b-124">可以通过服务的属性在运行时更改此设置 `FadeTargets` 。</span><span class="sxs-lookup"><span data-stu-id="79c0b-124">This setting can be changed at runtime via the service's `FadeTargets` property.</span></span>

<span data-ttu-id="79c0b-125">设置</span><span class="sxs-lookup"><span data-stu-id="79c0b-125">Setting</span></span> | <span data-ttu-id="79c0b-126">目标照相机</span><span class="sxs-lookup"><span data-stu-id="79c0b-126">Targeted Cameras</span></span>
--- | --- | ---
<span data-ttu-id="79c0b-127">主要</span><span class="sxs-lookup"><span data-stu-id="79c0b-127">Main</span></span> | <span data-ttu-id="79c0b-128">将淡化效果应用于主摄像机。</span><span class="sxs-lookup"><span data-stu-id="79c0b-128">Applies fade effect to the main camera.</span></span>
<span data-ttu-id="79c0b-129">UI</span><span class="sxs-lookup"><span data-stu-id="79c0b-129">UI</span></span> | <span data-ttu-id="79c0b-130">对 UI 层上的照相机应用淡化效果。</span><span class="sxs-lookup"><span data-stu-id="79c0b-130">Applies fade effect to cameras on the UI layer.</span></span> <span data-ttu-id="79c0b-131"> (不会影响覆盖用户界面) </span><span class="sxs-lookup"><span data-stu-id="79c0b-131">(Does not affect overlay UI)</span></span>
<span data-ttu-id="79c0b-132">All</span><span class="sxs-lookup"><span data-stu-id="79c0b-132">All</span></span> | <span data-ttu-id="79c0b-133">适用于主相机和 UI 照相机。</span><span class="sxs-lookup"><span data-stu-id="79c0b-133">Applies to both main and UI cameras.</span></span>
<span data-ttu-id="79c0b-134">自定义</span><span class="sxs-lookup"><span data-stu-id="79c0b-134">Custom</span></span> | <span data-ttu-id="79c0b-135">适用于通过提供的一组自定义相机 `SetCustomFadeTargetCameras`</span><span class="sxs-lookup"><span data-stu-id="79c0b-135">Applies to a custom set of cameras provided via `SetCustomFadeTargetCameras`</span></span>

### <a name="fade-out-time--fade-in-time"></a><span data-ttu-id="79c0b-136">淡出时间/淡化时间</span><span class="sxs-lookup"><span data-stu-id="79c0b-136">Fade out time / fade in time</span></span>

<span data-ttu-id="79c0b-137">在进入/退出转换的持续时间内的默认设置。</span><span class="sxs-lookup"><span data-stu-id="79c0b-137">Default settings for the duration of a fade on entering / exiting a transition.</span></span> <span data-ttu-id="79c0b-138">可以通过服务的和属性在运行时更改这些 `FadeOutTime` 设置 `FadeInTime` 。</span><span class="sxs-lookup"><span data-stu-id="79c0b-138">These settings can be changed at runtime via the service's `FadeOutTime` and `FadeInTime` properties.</span></span>

### <a name="camera-fader-type"></a><span data-ttu-id="79c0b-139">照相机 fader 类型</span><span class="sxs-lookup"><span data-stu-id="79c0b-139">Camera fader type</span></span>

<span data-ttu-id="79c0b-140">要 `ICameraFader` 使用哪个类向照相机应用淡化效果。</span><span class="sxs-lookup"><span data-stu-id="79c0b-140">Which `ICameraFader` class to use for applying a fade effect to cameras.</span></span> <span data-ttu-id="79c0b-141">默认 `CameraFaderQuad` 类在目标相机靠近剪辑平面的情况下实例化四个具有透明材料的四个。</span><span class="sxs-lookup"><span data-stu-id="79c0b-141">The default `CameraFaderQuad` class instantiates a quad with a transparent material in front of the target camera close to the clip plane.</span></span> <span data-ttu-id="79c0b-142">另一种方法可能是使用 post 效果系统。</span><span class="sxs-lookup"><span data-stu-id="79c0b-142">Another approach might be to use a post effects system.</span></span>

## <a name="using-the-extension"></a><span data-ttu-id="79c0b-143">使用扩展</span><span class="sxs-lookup"><span data-stu-id="79c0b-143">Using the extension</span></span>

<span data-ttu-id="79c0b-144">通过在摄像机淡出时传递运行的任务来使用转换服务。</span><span class="sxs-lookup"><span data-stu-id="79c0b-144">You use the transition service by passing Tasks that are run while the camera is faded out.</span></span>

### <a name="using-scene-system-tasks"></a><span data-ttu-id="79c0b-145">使用场景系统任务</span><span class="sxs-lookup"><span data-stu-id="79c0b-145">Using scene system tasks</span></span>

<span data-ttu-id="79c0b-146">在大多数情况下，你将使用 SceneSystem 服务提供的任务：</span><span class="sxs-lookup"><span data-stu-id="79c0b-146">In most cases you will be using Tasks supplied by the SceneSystem service:</span></span>

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

### <a name="using-custom-tasks"></a><span data-ttu-id="79c0b-147">使用自定义任务</span><span class="sxs-lookup"><span data-stu-id="79c0b-147">Using custom tasks</span></span>

<span data-ttu-id="79c0b-148">在其他情况下，你可能需要执行转换，而无需实际加载场景：</span><span class="sxs-lookup"><span data-stu-id="79c0b-148">In other cases you may want to perform a transition without actually loading a scene:</span></span>

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

<span data-ttu-id="79c0b-149">或者，可能需要在不使用 SceneSystem 服务的情况下加载场景：</span><span class="sxs-lookup"><span data-stu-id="79c0b-149">Or you may want to load a scene without using the SceneSystem service:</span></span>

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

### <a name="using-multiple-tasks"></a><span data-ttu-id="79c0b-150">使用多个任务</span><span class="sxs-lookup"><span data-stu-id="79c0b-150">Using multiple tasks</span></span>

<span data-ttu-id="79c0b-151">你还可以提供多个任务，这些任务将按顺序执行：</span><span class="sxs-lookup"><span data-stu-id="79c0b-151">You can also supply multiple tasks, which will be executed in order:</span></span>

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

## <a name="using-the-progress-indicator"></a><span data-ttu-id="79c0b-152">使用进度指示器</span><span class="sxs-lookup"><span data-stu-id="79c0b-152">Using the progress indicator</span></span>

<span data-ttu-id="79c0b-153">进度指示器是实现接口的任何内容 `IProgressIndicator` 。</span><span class="sxs-lookup"><span data-stu-id="79c0b-153">A progress indicator is anything that implements the `IProgressIndicator` interface.</span></span> <span data-ttu-id="79c0b-154">这可以采用初始屏幕、三维 tagalong 加载指示器的形式，或者提供有关转换进度的反馈的任何其他内容。</span><span class="sxs-lookup"><span data-stu-id="79c0b-154">This can take the form of a splash screen, a 3D tagalong loading indicator, or anything else that provides feedback about transition progress.</span></span>

<span data-ttu-id="79c0b-155">如果 `UseDefaultProgressIndicator` 在 SceneTransitionService 配置文件中选中了，则在转换开始时，将实例化进度指示器。</span><span class="sxs-lookup"><span data-stu-id="79c0b-155">If `UseDefaultProgressIndicator` is checked in the SceneTransitionService profile, a progress indicator will be instantiated when a transition begins.</span></span> <span data-ttu-id="79c0b-156">在转换期间， `Progress` `Message` 可以通过该服务的和方法访问此指示器的和属性 `SetProgressValue` `SetProgressMessage` 。</span><span class="sxs-lookup"><span data-stu-id="79c0b-156">For the duration of the transition this indicator's `Progress` and `Message` properties can be accessed via that service's `SetProgressValue` and `SetProgressMessage` methods.</span></span>

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

<span data-ttu-id="79c0b-157">或者，在调用时， `DoSceneTransition` 可以通过可选参数提供自己的进度指示器 `progressIndicator` 。</span><span class="sxs-lookup"><span data-stu-id="79c0b-157">Alternatively, when calling `DoSceneTransition` you can supply your own progress indicator via the optional `progressIndicator` argument.</span></span> <span data-ttu-id="79c0b-158">这将覆盖默认的进度指示器。</span><span class="sxs-lookup"><span data-stu-id="79c0b-158">This will override the default progress indicator.</span></span>
