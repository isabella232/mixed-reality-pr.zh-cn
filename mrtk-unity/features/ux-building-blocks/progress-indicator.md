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
# <a name="progress-indicator"></a><span data-ttu-id="922d6-104">进度指示器</span><span class="sxs-lookup"><span data-stu-id="922d6-104">Progress indicator</span></span>

![进度指示器](../images/progress-indicator/MRTK_ProgressIndicator_Main.png)

## <a name="example-scene"></a><span data-ttu-id="922d6-106">示例场景</span><span class="sxs-lookup"><span data-stu-id="922d6-106">Example scene</span></span>

<span data-ttu-id="922d6-107">可以在场景中找到如何使用进度指示器 `ProgressIndicatorExamples` 的示例。</span><span class="sxs-lookup"><span data-stu-id="922d6-107">Examples of how to use progress indicators can be found in the `ProgressIndicatorExamples` scene.</span></span> <span data-ttu-id="922d6-108">此场景演示 SDK 中包含的每个进度指示器预制项。</span><span class="sxs-lookup"><span data-stu-id="922d6-108">This scene demonstrates each of the progress indicator prefabs included in the SDK.</span></span> <span data-ttu-id="922d6-109">它还演示如何将进度指示器与一些常见的异步任务（如场景加载）结合使用。</span><span class="sxs-lookup"><span data-stu-id="922d6-109">It also demonstrates how to use progress indicators in conjunction with some common asynchronous tasks like scene loading.</span></span>

<img src="../images/progress-indicator/MRTK_ProgressIndicator_Examples.png" alt="Progress Indicator Examples 1">

## <a name="example-open-update--close-a-progress-indicator"></a><span data-ttu-id="922d6-110">示例：打开、&关闭进度指示器</span><span class="sxs-lookup"><span data-stu-id="922d6-110">Example: Open, update & close a progress indicator</span></span>

<span data-ttu-id="922d6-111">进度指示器实现 [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) 接口。</span><span class="sxs-lookup"><span data-stu-id="922d6-111">Progress indicators implement the [`IProgressIndicator`](xref:Microsoft.MixedReality.Toolkit.UI.IProgressIndicator) interface.</span></span> <span data-ttu-id="922d6-112">可以使用 从 GameObject 检索此接口 `GetComponent` 。</span><span class="sxs-lookup"><span data-stu-id="922d6-112">This interface can be retrieved from a GameObject using `GetComponent`.</span></span>

```c#
[SerializedField]
private GameObject indicatorObject;
private IProgressIndicator indicator;

private void Start()
{
    indicator = indicatorObject.GetComponent<IProgressIndicator>();
}
```

<span data-ttu-id="922d6-113">和 `IProgressIndicator.OpenAsync()` `IProgressIndicator.CloseAsync()` 方法返回 [任务](xref:System.Threading.Tasks.Task)。</span><span class="sxs-lookup"><span data-stu-id="922d6-113">The `IProgressIndicator.OpenAsync()` and `IProgressIndicator.CloseAsync()` methods return [Tasks](xref:System.Threading.Tasks.Task).</span></span> <span data-ttu-id="922d6-114">建议以异步方法等待这些任务。</span><span class="sxs-lookup"><span data-stu-id="922d6-114">We recommend awaiting these Tasks in an async method.</span></span>

<span data-ttu-id="922d6-115">将 MRTK 的默认进度指示器预制项置于场景中时，应处于非活动状态。</span><span class="sxs-lookup"><span data-stu-id="922d6-115">The MRTK's default progress indicator prefabs should be inactive when placed in a scene.</span></span> <span data-ttu-id="922d6-116">调用 `IProgressIndicator.OpenAsync()` 其方法时，进度指示器将自动激活和停用其 gameobject。</span><span class="sxs-lookup"><span data-stu-id="922d6-116">When their `IProgressIndicator.OpenAsync()` methods are called the progress indicators will activate and deactivate their gameobjects automatically.</span></span> <span data-ttu-id="922d6-117"> (此模式不是 IProgressIndicator interface.) </span><span class="sxs-lookup"><span data-stu-id="922d6-117">(This pattern is not a requirement of the IProgressIndicator interface.)</span></span>

<span data-ttu-id="922d6-118">将指示器的 属性 `Progress` 设置为 0-1 的值，以更新其显示的进度。</span><span class="sxs-lookup"><span data-stu-id="922d6-118">Set the indicator's `Progress` property to a value from 0-1 to update its displayed progress.</span></span> <span data-ttu-id="922d6-119">设置其 `Message` 属性以更新其显示的消息。</span><span class="sxs-lookup"><span data-stu-id="922d6-119">Set its `Message` property to update its displayed message.</span></span> <span data-ttu-id="922d6-120">不同的实现可能会以不同方式显示此内容。</span><span class="sxs-lookup"><span data-stu-id="922d6-120">Different implementations may display this content in different ways.</span></span>

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

## <a name="indicator-states"></a><span data-ttu-id="922d6-121">指示器状态</span><span class="sxs-lookup"><span data-stu-id="922d6-121">Indicator states</span></span>

<span data-ttu-id="922d6-122">指示器的 `State` 属性确定哪些操作有效。</span><span class="sxs-lookup"><span data-stu-id="922d6-122">An indicator's `State` property determines which operations are valid.</span></span> <span data-ttu-id="922d6-123">调用无效的方法通常会导致指示器报告错误，并且不采取措施。</span><span class="sxs-lookup"><span data-stu-id="922d6-123">Calling an invalid method will typically cause the indicator to report an error and take no action.</span></span>

<span data-ttu-id="922d6-124">状态</span><span class="sxs-lookup"><span data-stu-id="922d6-124">State</span></span> | <span data-ttu-id="922d6-125">有效操作</span><span class="sxs-lookup"><span data-stu-id="922d6-125">Valid Operations</span></span>
--- | ---
`ProgressIndicatorState.Opening` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Open` | `CloseAsync()`
`ProgressIndicatorState.Closing` | `AwaitTransitionAsync()`
`ProgressIndicatorState.Closed` | `OpenAsync()`

<span data-ttu-id="922d6-126">`AwaitTransitionAsync()` 可用于确保指示器在使用前已完全打开或关闭。</span><span class="sxs-lookup"><span data-stu-id="922d6-126">`AwaitTransitionAsync()` can be used to be sure an indicator is fully opened or closed before using it.</span></span>

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
