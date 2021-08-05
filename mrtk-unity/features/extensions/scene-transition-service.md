---
title: 场景转换服务
description: MRTK 中的场景转换文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，SceneTransition，
ms.openlocfilehash: a66922f1c9d58018ee856c3054aa71f5213ec690c5f4780b32fd735eb59f2ac7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189229"
---
# <a name="scene-transition-service"></a>场景转换服务

此扩展简化了场景的业务，其中显示了进度指示器、加载场景，然后淡入。

场景操作由 SceneSystem 服务驱动，但任何基于任务的操作都可用于驱动转换。

## <a name="enabling-the-extension"></a>启用扩展

若要启用此扩展，请打开 RegisteredServiceProvider 配置文件。 单击 "注册新的服务提供商" 以添加新配置。 在 "组件类型" 字段中，选择 "SceneTransitionService"。 在 "配置文件" 字段中，选择包含在扩展中的默认场景转换配置文件。

## <a name="profile-options"></a>配置文件选项

### <a name="use-default-progress-indicator"></a>使用默认进度指示器

如果选中，则在提供进度指示器对象时，如果不提供进度指示器对象，则将使用默认的进度指示器 prefab `DoSceneTransition.` ，将忽略默认值。

### <a name="use-fade-color"></a>使用淡化颜色

如果选中，转换服务将在转换过程中应用淡化。 可以通过服务的属性在运行时更改此设置 `UseFadeColor` 。

### <a name="fade-color"></a>淡化颜色

控制淡化效果的颜色。 将忽略阿尔法。 在通过服务的属性转换之前，可以在运行时更改此设置 `FadeColor` 。

### <a name="fade-targets"></a>淡化目标

控制将对其应用淡化效果的相机。 可以通过服务的属性在运行时更改此设置 `FadeTargets` 。

设置 | 目标照相机
--- | --- | ---
Main | 将淡化效果应用于主摄像机。
UI | 对 UI 层上的照相机应用淡化效果。  (不会影响覆盖用户界面) 
All | 适用于主相机和 UI 照相机。
自定义 | 适用于通过提供的一组自定义相机 `SetCustomFadeTargetCameras`

### <a name="fade-out-time--fade-in-time"></a>淡出时间/淡化时间

在进入/退出转换的持续时间内的默认设置。 可以通过服务的和属性在运行时更改这些 `FadeOutTime` 设置 `FadeInTime` 。

### <a name="camera-fader-type"></a>照相机 fader 类型

要 `ICameraFader` 使用哪个类向照相机应用淡化效果。 默认 `CameraFaderQuad` 类在目标相机靠近剪辑平面的情况下实例化四个具有透明材料的四个。 另一种方法可能是使用 post 效果系统。

## <a name="using-the-extension"></a>使用扩展

通过在摄像机淡出时传递运行的任务来使用转换服务。

### <a name="using-scene-system-tasks"></a>使用场景系统任务

在大多数情况下，你将使用 SceneSystem 服务提供的任务：

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

### <a name="using-custom-tasks"></a>使用自定义任务

在其他情况下，你可能需要执行转换，而无需实际加载场景：

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

或者，可能需要在不使用 SceneSystem 服务的情况下加载场景：

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

### <a name="using-multiple-tasks"></a>使用多个任务

你还可以提供多个任务，这些任务将按顺序执行：

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

## <a name="using-the-progress-indicator"></a>使用进度指示器

进度指示器是实现接口的任何内容 `IProgressIndicator` 。 这可以采用初始屏幕、三维 tagalong 加载指示器的形式，或者提供有关转换进度的反馈的任何其他内容。

如果 `UseDefaultProgressIndicator` 在 SceneTransitionService 配置文件中选中了，则在转换开始时，将实例化进度指示器。 在转换期间， `Progress` `Message` 可以通过该服务的和方法访问此指示器的和属性 `SetProgressValue` `SetProgressMessage` 。

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

或者，在调用时， `DoSceneTransition` 可以通过可选参数提供自己的进度指示器 `progressIndicator` 。 这将覆盖默认的进度指示器。
