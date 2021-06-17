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
# <a name="progress-indicators"></a><span data-ttu-id="7541d-104">进度指示器</span><span class="sxs-lookup"><span data-stu-id="7541d-104">Progress Indicators</span></span>

![进度指示器](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="7541d-106">示例场景</span><span class="sxs-lookup"><span data-stu-id="7541d-106">Example scene</span></span>

<span data-ttu-id="7541d-107">在场景中可以找到有关如何使用进度指示器的示例 `ProgressIndicatorExamples` 。</span><span class="sxs-lookup"><span data-stu-id="7541d-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="7541d-108">此场景演示 SDK 中包含的每个进度指示器 prototyping。</span><span class="sxs-lookup"><span data-stu-id="7541d-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span> <span data-ttu-id="7541d-109">它还演示了如何将进度指示器与一些常见的异步任务（如场景加载）结合使用。</span><span class="sxs-lookup"><span data-stu-id="7541d-109">It also demonstrates how to use progress indicators in conjunction with some common asynchronous tasks like scene loading.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="7541d-110">示例：打开、更新 & 关闭进度指示器</span><span class="sxs-lookup"><span data-stu-id="7541d-110">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="7541d-111">进度指示器实现 [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) 接口。</span><span class="sxs-lookup"><span data-stu-id="7541d-111">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="7541d-112">此接口可以使用从 GameObject 中检索 `GetComponent` 。</span><span class="sxs-lookup"><span data-stu-id="7541d-112">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="7541d-113">`IProgressIndicator.OpenAsync()`和 `IProgressIndicator.CloseAsync()` 方法返回[任务](xref:System.Threading.Tasks.Task)。</span><span class="sxs-lookup"><span data-stu-id="7541d-113">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="7541d-114">建议在异步方法中等待这些任务。</span><span class="sxs-lookup"><span data-stu-id="7541d-114">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="7541d-115">置于场景中时，MRTK 的默认进度指示器 prototyping 应为非活动状态。</span><span class="sxs-lookup"><span data-stu-id="7541d-115">The MRTK's default progress indicator prefabs should be inactive when placed in a scene.</span></span> <span data-ttu-id="7541d-116">当 `IProgressIndicator.OpenAsync()` 调用其方法时，进度指示器将自动激活和停用它们的 gameobject。</span><span class="sxs-lookup"><span data-stu-id="7541d-116">When their `IProgressIndicator.OpenAsync()` methods are called the progress indicators will activate and deactivate their gameobjects automatically.</span></span> <span data-ttu-id="7541d-117"> (此模式不是 IProgressIndicator 接口所必需的。 ) </span><span class="sxs-lookup"><span data-stu-id="7541d-117">(This pattern is not a requirement of the IProgressIndicator interface.)</span></span>

<span data-ttu-id="7541d-118">将指示器的 `Progress` 属性设置为一个介于0-1 之间的值，以更新其显示进度。</span><span class="sxs-lookup"><span data-stu-id="7541d-118">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="7541d-119">设置其 `Message` 属性以更新其显示的消息。</span><span class="sxs-lookup"><span data-stu-id="7541d-119">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="7541d-120">不同的实现可以以不同的方式显示此内容。</span><span class="sxs-lookup"><span data-stu-id="7541d-120">Different implementations may display this content in different ways.</span></span>

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

## <a name="indicator-states"></a><span data-ttu-id="7541d-121">指示器状态</span><span class="sxs-lookup"><span data-stu-id="7541d-121">Indicator states</span></span>

<span data-ttu-id="7541d-122">指示器的 `State` 属性确定哪些操作有效。</span><span class="sxs-lookup"><span data-stu-id="7541d-122">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="7541d-123">调用无效方法通常会导致指示器报告错误，而不执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="7541d-123">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="7541d-124">状态</span><span class="sxs-lookup"><span data-stu-id="7541d-124">State</span></span> | <span data-ttu-id="7541d-125">有效操作</span><span class="sxs-lookup"><span data-stu-id="7541d-125">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="7541d-126">`AwaitTransitionAsync()` 可用于在使用指示器之前确保其完全打开或关闭。</span><span class="sxs-lookup"><span data-stu-id="7541d-126">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

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
