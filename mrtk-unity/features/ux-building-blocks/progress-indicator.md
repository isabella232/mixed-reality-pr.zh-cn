---
title: 进度指示器
description: MRTK 中进度指示器的概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 268d13d00bc0bcf1d522eaa6809dab9892624e11
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176571"
---
# <a name="progress-indicator"></a>进度指示器

![进度指示器](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a>示例场景

可以在场景中找到如何使用进度指示器 `ProgressIndicatorExamples` 的示例。 此场景演示 SDK 中包含的每个进度指示器预制项。 它还演示如何将进度指示器与一些常见的异步任务（如场景加载）结合使用。

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a>示例：打开、&关闭进度指示器

进度指示器实现 [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) 接口。 可以使用 从 GameObject 检索此接口 `GetComponent` 。

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

和 `IProgressIndicator.OpenAsync()` `IProgressIndicator.CloseAsync()` 方法返回 [任务](xref:System.Threading.Tasks.Task)。 建议以异步方法等待这些任务。

将 MRTK 的默认进度指示器预制项置于场景中时，应处于非活动状态。 调用 `IProgressIndicator.OpenAsync()` 其方法时，进度指示器将自动激活和停用其 gameobject。  (此模式不是 IProgressIndicator interface.) 

将指示器的 属性 `Progress` 设置为 0-1 的值，以更新其显示的进度。 设置其 `Message` 属性以更新其显示的消息。 不同的实现可能会以不同方式显示此内容。

```c#
private async void OpenProgressIndicator()
{
    await indicator.OpenAsync();

    float progress = 0;
    while (progress < 1)
    {
        progress += Time.deltaTime;
        indicator.Message = "Loading...";
        indicator.Progress = progress;
        await Task.Yield();
    }

    await indicator.CloseAsync();
}
```

## <a name="indicator-states"></a>指示器状态

指示器的 `State` 属性确定哪些操作有效。 调用无效的方法通常会导致指示器报告错误，并且不采取措施。

状态 | 有效操作
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

`AwaitTransitionAsync()` 可用于确保指示器在使用前已完全打开或关闭。

```c#
private async void ToggleIndicator(IProgressIndicator indicator)
{
    await indicator.AwaitTransitionAsync();

    switch (indicator.State)
    {
        case ProgressIndicatorState.Closed:
            await indicator.OpenAsync();
            break;

        case ProgressIndicatorState.Open:
            await indicator.CloseAsync();
            break;
        }
    }
```
