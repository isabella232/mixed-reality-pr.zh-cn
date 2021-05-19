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
# <a name="scene-transition-service"></a>场景转换服务

此扩展简化了以下业务：淡出场景、显示进度指示器、加载场景，然后淡入。

场景操作由 SceneSystem 服务驱动，但任何基于任务的操作都可用于驱动转换。

## <a name="enabling-the-extension"></a>启用扩展

若要启用扩展，请打开 RegisteredServiceProvider 配置文件。 单击"注册新服务提供程序"以添加新配置。 在"组件类型"字段中，选择"SceneTransitionService"。 在"配置文件"字段中，选择扩展中包含的默认场景转换配置文件。

## <a name="profile-options"></a>配置文件选项

### <a name="use-default-progress-indicator"></a>使用默认进度指示器

如果选中此选项，则当调用 "如果提供了进度指示器对象" 时未提供进度指示器对象时，将使用默认进度指示器 `DoSceneTransition.` 预制项，默认进度指示器将被忽略。

### <a name="use-fade-color"></a>使用淡入淡出颜色

如果选中，转换服务将在转换过程中应用淡入淡出。 可以通过服务的 属性在运行时更改 `UseFadeColor` 此设置。

### <a name="fade-color"></a>淡入淡出颜色

控制淡入淡出效果的颜色。 将忽略阿尔法。 在通过服务的 属性转换之前，可以在运行时更改 `FadeColor` 此设置。

### <a name="fade-targets"></a>淡化目标

控制将对其应用淡化效果的相机。 可以通过服务的属性在运行时更改此设置 `FadeTargets` 。

设置 | 目标照相机
--- | --- | ---
主要 | 将淡化效果应用于主摄像机。
UI | 对 UI 层上的照相机应用淡化效果。  (不会影响覆盖用户界面) 
全部 | 适用于主相机和 UI 照相机。
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

在其他情况下，你可能想要在不实际加载场景的情况下执行转换：

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

或者，你可能想要在不使用 SceneSystem 服务的情况下加载场景：

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

还可以提供多个任务，这些任务将按以下顺序执行：

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

进度指示器是实现 接口 `IProgressIndicator` 的一切内容。 这可以是初始屏幕、3D 标记加载指示器或提供有关转换进度反馈的任何其他内容。

如果在 SceneTransitionService 配置文件中选中 ，则转换开始时将实例 `UseDefaultProgressIndicator` 化进度指示器。 在转换期间，可以通过该服务的 和 方法访问此指示器 `Progress` `Message` 的 和 `SetProgressValue` `SetProgressMessage` 属性。

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

或者，在调用 `DoSceneTransition` 时，可以通过可选参数提供自己的进度 `progressIndicator` 指示器。 这将替代默认进度指示器。
