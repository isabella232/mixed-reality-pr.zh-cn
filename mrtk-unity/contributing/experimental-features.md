---
title: 实验性功能
description: 与 MRTK 中的实验性功能相关的文档。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 341ba0ee3e5900cc52f1ef715232f49064102309
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121375"
---
# <a name="experimental-features"></a><span data-ttu-id="c15e2-104">实验性功能</span><span class="sxs-lookup"><span data-stu-id="c15e2-104">Experimental features</span></span>

<span data-ttu-id="c15e2-105">MRTK 团队工作的一些功能似乎具有大量初始价值，即使我们尚未全面了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="c15e2-105">Some features the MRTK team works on appear to have a lot of initial value even if we haven’t fully fleshed out the details.</span></span> <span data-ttu-id="c15e2-106">对于这些类型的功能，我们希望社区有机会尽早看到它们。</span><span class="sxs-lookup"><span data-stu-id="c15e2-106">For these types of features, we want the community to get a chance to see them early.</span></span> <span data-ttu-id="c15e2-107">由于它们处于周期早期，因此我们将它们标记为实验性，以指示它们仍在不断发展，并且可能会随着时间的推移而发生变化。</span><span class="sxs-lookup"><span data-stu-id="c15e2-107">Because they are early in the cycle, we label them as experimental to indicate that they are still evolving, and subject to change over time.</span></span>

## <a name="what-to-expect-from-an-experimental-feature"></a><span data-ttu-id="c15e2-108">试验性功能预期的结果</span><span class="sxs-lookup"><span data-stu-id="c15e2-108">What to expect from an experimental feature</span></span>

<span data-ttu-id="c15e2-109">如果组件标记为实验性组件，可以预期以下各项：</span><span class="sxs-lookup"><span data-stu-id="c15e2-109">If a component is marked experimental you can expect the following:</span></span>

- <span data-ttu-id="c15e2-110">演示用法的示例场景，位于 `MRTK/Examples/Experimental` 子文件夹下</span><span class="sxs-lookup"><span data-stu-id="c15e2-110">An example scene demonstrating usage, located under `MRTK/Examples/Experimental` sub-folder</span></span>
- <span data-ttu-id="c15e2-111">实验性功能可能没有文档。</span><span class="sxs-lookup"><span data-stu-id="c15e2-111">Experimental features may not have docs.</span></span>
- <span data-ttu-id="c15e2-112">它们可能没有测试。</span><span class="sxs-lookup"><span data-stu-id="c15e2-112">They probably don't have tests.</span></span>
- <span data-ttu-id="c15e2-113">实验性功能可能会更改。</span><span class="sxs-lookup"><span data-stu-id="c15e2-113">Experimental features are subject to change.</span></span>

## <a name="experimental-feature-guidelines"></a><span data-ttu-id="c15e2-114">实验性功能指南</span><span class="sxs-lookup"><span data-stu-id="c15e2-114">Experimental feature guidelines</span></span>

### <a name="experimental-code-should-live-in-a-separate-folder"></a><span data-ttu-id="c15e2-115">实验性代码应包含于单独的文件夹中</span><span class="sxs-lookup"><span data-stu-id="c15e2-115">Experimental code should live in a separate folder</span></span>

<span data-ttu-id="c15e2-116">实验性代码应进入顶级实验文件夹，后跟实验性功能名称。</span><span class="sxs-lookup"><span data-stu-id="c15e2-116">Experimental code should go into a top-level experimental folder followed by the experimental feature name.</span></span> <span data-ttu-id="c15e2-117">例如，如果尝试提供新功能 FooBar，请放入以下代码：</span><span class="sxs-lookup"><span data-stu-id="c15e2-117">For example, if trying to contribute a new feature FooBar, put code in the following:</span></span>

- <span data-ttu-id="c15e2-118">脚本进入的示例场景 `MRTK/Examples/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="c15e2-118">Example scenes, scripts go into `MRTK/Examples/Experimental/FooBar/`</span></span>
- <span data-ttu-id="c15e2-119">组件脚本，预制件进入 `MRTK/SDK/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="c15e2-119">Component scripts, prefabs go into `MRTK/SDK/Experimental/FooBar/`</span></span>
- <span data-ttu-id="c15e2-120">组件检查器进入 `MRTK/SDK/Inspectors/Experimental/FooBar`</span><span class="sxs-lookup"><span data-stu-id="c15e2-120">Component inspectors go into `MRTK/SDK/Inspectors/Experimental/FooBar`</span></span>

<span data-ttu-id="c15e2-121">在实验性功能名称下使用子文件夹时，请尝试镜像 MRTK 的相同文件夹结构。</span><span class="sxs-lookup"><span data-stu-id="c15e2-121">When using sub-folders under the experimental feature name, try to mirror the same folder structure of MRTK.</span></span>

<span data-ttu-id="c15e2-122">例如，求解器将 `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span><span class="sxs-lookup"><span data-stu-id="c15e2-122">For example, solvers would go under `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span></span>

<span data-ttu-id="c15e2-123">将场景放在靠近顶部的场景文件夹中： `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span><span class="sxs-lookup"><span data-stu-id="c15e2-123">Keep scenes in a scene folder near the top: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span></span>

> [!NOTE]
> <span data-ttu-id="c15e2-124">我们考虑没有单个实验性根文件夹，而是将"实验性"放在 下面 `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` 。</span><span class="sxs-lookup"><span data-stu-id="c15e2-124">We considered not having a single Experimental root folder and instead putting Experimental under say `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity`.</span></span> <span data-ttu-id="c15e2-125">我们决定在基础位置使用文件夹，使实验性功能更易于发现。</span><span class="sxs-lookup"><span data-stu-id="c15e2-125">We decided to go with folders at the base to make the experimental features easier to discover.</span></span>

### <a name="experimental-code-should-be-in-a-special-namespace"></a><span data-ttu-id="c15e2-126">实验性代码应包含特殊命名空间</span><span class="sxs-lookup"><span data-stu-id="c15e2-126">Experimental code should be in a special namespace</span></span>

<span data-ttu-id="c15e2-127">确保实验性代码位于与非实验性位置匹配的实验命名空间中。</span><span class="sxs-lookup"><span data-stu-id="c15e2-127">Ensure that the experimental code lives in an experimental namespace that matches the non-experimental location.</span></span> <span data-ttu-id="c15e2-128">例如，如果组件是 中的求解器的一部分， `Microsoft.MixedReality.Toolkit.Utilities.Solvers` 则其命名空间应为 `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` 。</span><span class="sxs-lookup"><span data-stu-id="c15e2-128">For example, if your component is part of solvers at `Microsoft.MixedReality.Toolkit.Utilities.Solvers`, its namespace should be `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers`.</span></span>

<span data-ttu-id="c15e2-129">有关 [示例，](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) 请参阅此 PR。</span><span class="sxs-lookup"><span data-stu-id="c15e2-129">See [this PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) for an example.</span></span>

### <a name="experimental-features-should-have-an-experimental-attribute"></a><span data-ttu-id="c15e2-130">实验性功能应具有 [实验性] 属性</span><span class="sxs-lookup"><span data-stu-id="c15e2-130">Experimental features should have an [Experimental] attribute</span></span>

<span data-ttu-id="c15e2-131">将属性添加到其中一个字段上方，使组件编辑器中出现一个小对话框，其中提到你的功能是实验性的， `[Experimental]` 并且可能会进行重大更改。</span><span class="sxs-lookup"><span data-stu-id="c15e2-131">Add an `[Experimental]` attribute above one of your fields to have a small dialog appear in the component editor that mentions your feature is experimental and subject to significant changes.</span></span>

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a><span data-ttu-id="c15e2-132">实验性功能的菜单应转到"实验性"子菜单下</span><span class="sxs-lookup"><span data-stu-id="c15e2-132">Menus for experimental features should go under "Experimental" sub-menu</span></span>

<span data-ttu-id="c15e2-133">将命令添加到编辑器中的菜单时，请确保实验性功能在"实验性"子菜单下。</span><span class="sxs-lookup"><span data-stu-id="c15e2-133">Ensure that experimental features are under "experimental" sub-menus when adding commands to menus in the editor.</span></span> <span data-ttu-id="c15e2-134">以下是一些示例：</span><span class="sxs-lookup"><span data-stu-id="c15e2-134">Here are a few examples:</span></span>

<span data-ttu-id="c15e2-135">添加顶级菜单命令：</span><span class="sxs-lookup"><span data-stu-id="c15e2-135">Adding a top-level menu command:</span></span>

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

<span data-ttu-id="c15e2-136">添加组件菜单：</span><span class="sxs-lookup"><span data-stu-id="c15e2-136">Adding a component menu:</span></span>

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a><span data-ttu-id="c15e2-137">文档</span><span class="sxs-lookup"><span data-stu-id="c15e2-137">Documentation</span></span>

<span data-ttu-id="c15e2-138">按照以下步骤为实验性功能添加文档：</span><span class="sxs-lookup"><span data-stu-id="c15e2-138">Follow these steps to add documentation for your experimental feature:</span></span>

1. <span data-ttu-id="c15e2-139">实验性功能的任何文档都应在实验 `readme.md` 性文件夹中的文件中。</span><span class="sxs-lookup"><span data-stu-id="c15e2-139">Any documentation for an experimental feature should go in a `readme.md` file in the experimental folder.</span></span> <span data-ttu-id="c15e2-140">例如，MRTK/SDK/Experimental/PulseShader/readme.md。</span><span class="sxs-lookup"><span data-stu-id="c15e2-140">For example, MRTK/SDK/Experimental/PulseShader/readme.md.</span></span>

1. <span data-ttu-id="c15e2-141">在 *"功能概述"* 下，在 的实验 *部分添加* 链接 [`Documentation/toc.yml`](../toc.yml) 。</span><span class="sxs-lookup"><span data-stu-id="c15e2-141">Under *Feature Overviews* Add a link in the *Experimental* section at [`Documentation/toc.yml`](../toc.yml).</span></span>

### <a name="minimize-impact-to-mrtk-code"></a><span data-ttu-id="c15e2-142">尽量减少对 MRTK 代码的影响</span><span class="sxs-lookup"><span data-stu-id="c15e2-142">Minimize impact to MRTK code</span></span>

<span data-ttu-id="c15e2-143">虽然 MRTK 更改可能会使试验正常工作，但它可能会以你期望的方式影响其他人。</span><span class="sxs-lookup"><span data-stu-id="c15e2-143">While your MRTK change might get your experiment to work, it could impact other people in ways you do not expect.</span></span>
<span data-ttu-id="c15e2-144">对 MRTK 核心代码进行的任何回归都会导致拉取请求恢复。</span><span class="sxs-lookup"><span data-stu-id="c15e2-144">Any regressions you make to the MRTK core code would result in your pull request getting reverted.</span></span>

<span data-ttu-id="c15e2-145">旨在对除实验性文件夹外的文件夹进行零更改。</span><span class="sxs-lookup"><span data-stu-id="c15e2-145">Aim to have zero changes in folders other than experimental folders.</span></span> <span data-ttu-id="c15e2-146">下面是可进行试验性更改的文件夹列表：</span><span class="sxs-lookup"><span data-stu-id="c15e2-146">Here is a list of folders that can have experimental changes:</span></span>

- <span data-ttu-id="c15e2-147">MRTK/SDK/实验性</span><span class="sxs-lookup"><span data-stu-id="c15e2-147">MRTK/SDK/Experimental</span></span>
- <span data-ttu-id="c15e2-148">MRTK/SDK/Inspectors/Experimental</span><span class="sxs-lookup"><span data-stu-id="c15e2-148">MRTK/SDK/Inspectors/Experimental</span></span>
- <span data-ttu-id="c15e2-149">MRTK/Examples/Experimental</span><span class="sxs-lookup"><span data-stu-id="c15e2-149">MRTK/Examples/Experimental</span></span>

<span data-ttu-id="c15e2-150">应谨慎处理这些文件夹之外的更改。</span><span class="sxs-lookup"><span data-stu-id="c15e2-150">Changes outside of these folders should be treated very carefully.</span></span> <span data-ttu-id="c15e2-151">如果实验性功能必须包括对 MRTK 核心代码的更改，请考虑将 MRTK 更改拆分为包含测试和文档的单独拉取请求。</span><span class="sxs-lookup"><span data-stu-id="c15e2-151">If your experimental feature must include changes to MRTK core code, consider splitting out MRTK changes into a separate pull request that includes tests and documentation.</span></span>

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a><span data-ttu-id="c15e2-152">使用实验性功能不应影响人们使用核心控件的能力</span><span class="sxs-lookup"><span data-stu-id="c15e2-152">Using your experimental feature should not impact people's ability to use core controls</span></span>

<span data-ttu-id="c15e2-153">大多数人非常频繁地使用核心 UX 组件，如按钮、ManipulationHandler 和 Interactable。</span><span class="sxs-lookup"><span data-stu-id="c15e2-153">Most people use core UX components like the button, ManipulationHandler and Interactable very frequently.</span></span> <span data-ttu-id="c15e2-154">如果阻止他们使用按钮，他们很可能不会使用实验性功能。</span><span class="sxs-lookup"><span data-stu-id="c15e2-154">They will likely not use your experimental feature if it prevents them from using buttons.</span></span>

<span data-ttu-id="c15e2-155">使用组件不应中断按钮、ManipulationHandler、BoundingBox 或可交互。</span><span class="sxs-lookup"><span data-stu-id="c15e2-155">Using your component should not break buttons, ManipulationHandler, BoundingBox, or interactable.</span></span>

<span data-ttu-id="c15e2-156">例如，在此 [ScrollableObjectCollection PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001)中，添加 ScrollableObjectCollection 导致用户无法使用 HoloLens 按钮预制。</span><span class="sxs-lookup"><span data-stu-id="c15e2-156">For example, in [this ScrollableObjectCollection PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), adding a ScrollableObjectCollection caused people to not be able to use the HoloLens button prefabs.</span></span> <span data-ttu-id="c15e2-157">尽管这不是由 PR 代码中的 bug 引起的 (而是公开了现有的 bug) ，但它阻止了 PR 签入。</span><span class="sxs-lookup"><span data-stu-id="c15e2-157">Even though this was not caused by a bug in the PR (but rather exposed an existing bug), it prevented the PR from getting checked in.</span></span>

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a><span data-ttu-id="c15e2-158">提供演示如何使用该功能的示例场景</span><span class="sxs-lookup"><span data-stu-id="c15e2-158">Provide an example scene that demonstrates how to use the feature</span></span>

<span data-ttu-id="c15e2-159">人们需要了解如何使用你的功能以及如何测试它。</span><span class="sxs-lookup"><span data-stu-id="c15e2-159">People need to see how to use your feature, and how to test it.</span></span>

<span data-ttu-id="c15e2-160">在 MRTK/Examples/Experimental/YOUR_FEATURE</span><span class="sxs-lookup"><span data-stu-id="c15e2-160">Provide an example under MRTK/Examples/Experimental/YOUR_FEATURE</span></span>

### <a name="minimize-user-visible-flaws-in-experimental-features"></a><span data-ttu-id="c15e2-161">最大程度地减少实验性功能中的用户可见缺陷</span><span class="sxs-lookup"><span data-stu-id="c15e2-161">Minimize user visible flaws in experimental features</span></span>

<span data-ttu-id="c15e2-162">其他人不会使用实验性功能（如果它不起作用，它将不会成为一项功能）。</span><span class="sxs-lookup"><span data-stu-id="c15e2-162">Others will not use the experimental feature if it does not work, it will not graduate to a feature.</span></span>

<span data-ttu-id="c15e2-163">在目标平台上测试示例场景，确保它正常工作。</span><span class="sxs-lookup"><span data-stu-id="c15e2-163">Test your example scene on your target platform, make sure it works as expected.</span></span> <span data-ttu-id="c15e2-164">确保功能在编辑器中也正常工作，以便即使用户没有目标平台，也可以快速进行访问和查看功能。</span><span class="sxs-lookup"><span data-stu-id="c15e2-164">Make sure your feature also works in editor, so people can rapidly iterate and see your feature even if they don’t have the target platform.</span></span>

## <a name="graduating-experimental-code-into-mrtk-code"></a><span data-ttu-id="c15e2-165">将实验性代码转换为 MRTK 代码</span><span class="sxs-lookup"><span data-stu-id="c15e2-165">Graduating experimental code into MRTK code</span></span>

<span data-ttu-id="c15e2-166">如果某个功能最终发现大量使用，则应该将该功能分为核心 MRTK 代码。</span><span class="sxs-lookup"><span data-stu-id="c15e2-166">If a feature ends up seeing quite a lot of use, then we should graduate it into core MRTK code.</span></span> <span data-ttu-id="c15e2-167">为此，该功能应具有测试、文档和示例场景。</span><span class="sxs-lookup"><span data-stu-id="c15e2-167">To do this, the feature should have tests, documentation, and an example scene.</span></span>

<span data-ttu-id="c15e2-168">准备好对 MRTK 功能进行分期时，请创建一个问题以签入 PR。</span><span class="sxs-lookup"><span data-stu-id="c15e2-168">When you are ready to graduate the feature MRTK, create an issue to check in your PR against.</span></span> <span data-ttu-id="c15e2-169">PR 应包括使此功能成为核心功能所需的全部内容：测试、文档和显示使用情况的示例场景。</span><span class="sxs-lookup"><span data-stu-id="c15e2-169">The PR should include all the things needed to make this a core feature: tests, documentation, and an example scene showing usage.</span></span>

<span data-ttu-id="c15e2-170">此外，不要忘记更新命名空间以删除"实验性"子空间。</span><span class="sxs-lookup"><span data-stu-id="c15e2-170">Also, don’t forget to update the namespaces to remove the “Experimental” subspace.</span></span>
