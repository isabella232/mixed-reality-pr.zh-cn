---
title: ProgressIndicator
description: MRTK 中的进度指示器概述
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 9170a376812901cb063038a5513d4fbf79ad0a28
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110126"
---
# <a name="progress-indicators"></a>进度指示器

![进度指示器](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a>示例场景

在场景中可以找到有关如何使用进度指示器的示例 `ProgressIndicatorExamples` 。 此场景演示 SDK 中包含的每个进度指示器 prototyping。 它还演示了如何将进度指示器与一些常见的异步任务（如场景加载）结合使用。

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a>示例：打开、更新 & 关闭进度指示器

进度指示器实现 [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) 接口。 此接口可以使用从 GameObject 中检索 `GetComponent` 。

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

`IProgressIndicator.OpenAsync()`和 `IProgressIndicator.CloseAsync()` 方法返回[任务](xref:System.Threading.Tasks.Task)。 建议在异步方法中等待这些任务。

置于场景中时，MRTK 的默认进度指示器 prototyping 应为非活动状态。 当 `IProgressIndicator.OpenAsync()` 调用其方法时，进度指示器将自动激活和停用它们的 gameobject。  (此模式不是 IProgressIndicator 接口所必需的。 ) 

将指示器的 `Progress` 属性设置为一个介于0-1 之间的值，以更新其显示进度。 设置其 `Message` 属性以更新其显示的消息。 不同的实现可以以不同的方式显示此内容。

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

指示器的 `State` 属性确定哪些操作有效。 调用无效方法通常会导致指示器报告错误，而不执行任何操作。

状态 | 有效操作
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

`AwaitTransitionAsync()` 可用于在使用指示器之前确保其完全打开或关闭。

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
