---
title: PullRequests
description: 与拉取请求相关的详细信息。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, 混合现实, 开发, MRTK, PR,
ms.openlocfilehash: 31db19154adbf7016aec609e7baca8c4fa3eda48
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687537"
---
# <a name="pull-requests"></a><span data-ttu-id="96283-104">拉取请求</span><span class="sxs-lookup"><span data-stu-id="96283-104">Pull requests</span></span>

## <a name="prerequisites"></a><span data-ttu-id="96283-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="96283-105">Prerequisites</span></span>

<span data-ttu-id="96283-106">如果你之前未向 Microsoft 项目贡献过内容，系统可能会要求你签署[贡献许可协议](https://cla.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="96283-106">If you haven't contributed to a Microsoft project before, you may be asked to sign a [contribution license agreement](https://cla.microsoft.com/).</span></span>
<span data-ttu-id="96283-107">如果你贡献过内容，拉取请求 (PR) 中的注释将显示此信息。</span><span class="sxs-lookup"><span data-stu-id="96283-107">A comment in the PR will let you know if you do.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96283-108">如果你是 Microsoft 员工，且不属于 [GitHub 上的 Microsoft 组织](https://github.com/Microsoft)，那么在发起拉取请求之前，请访问 [Microsoft 中的开放源代码](https://opensource.microsoft.com/)，在 corpnet 上关联你的 Microsoft 和 GitHub 帐户。</span><span class="sxs-lookup"><span data-stu-id="96283-108">If you are a Microsoft employee and are not a member of the [Microsoft organization on GitHub](https://github.com/Microsoft), please link your Microsoft and GitHub accounts on corpnet by visiting [Open Source at Microsoft](https://opensource.microsoft.com/) before you start your pull request.</span></span> <span data-ttu-id="96283-109">你需要提前执行一些操作。</span><span class="sxs-lookup"><span data-stu-id="96283-109">There's some process stuff you'll need to do ahead of time.</span></span>

## <a name="creating-a-pull-request"></a><span data-ttu-id="96283-110">创建拉取请求</span><span class="sxs-lookup"><span data-stu-id="96283-110">Creating a pull request</span></span>

<span data-ttu-id="96283-111">在准备好提交拉取请求时，请[创建](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/mrtk_development...mrtk_development?expand=1)一个针对 [mrtk_development](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/mrtk_development) 分支的拉取请求。</span><span class="sxs-lookup"><span data-stu-id="96283-111">When you are ready to submit a pull request, [create a pull request](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/mrtk_development...mrtk_development?expand=1) targeting the [mrtk_development](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/mrtk_development) branch.</span></span>

<span data-ttu-id="96283-112">请阅读指南，确保你的拉取请求遵循这些指南。</span><span class="sxs-lookup"><span data-stu-id="96283-112">Read the guidelines and ensure your pull request meets the guidelines.</span></span>

* <span data-ttu-id="96283-113">务必提及与 PR 相关的所有问题/功能请求或任务。</span><span class="sxs-lookup"><span data-stu-id="96283-113">Make sure to reference any Issue / Feature Request or Task the PR relates to.</span></span>
* <span data-ttu-id="96283-114">检查拉取请求是否仅包含与 PR 相关的文件/更改。</span><span class="sxs-lookup"><span data-stu-id="96283-114">Check the pull request contains only files / changes related to the PR.</span></span>
* <span data-ttu-id="96283-115">检查文档是否是最新的且是否被包含在内。</span><span class="sxs-lookup"><span data-stu-id="96283-115">Check documentation is up to date and included.</span></span> <span data-ttu-id="96283-116">检查所有公共字段是否都有注释。</span><span class="sxs-lookup"><span data-stu-id="96283-116">Check all public fields have comments.</span></span>
* <span data-ttu-id="96283-117">若要添加新功能，请检查是否包含了测试来验证该功能（参见 [UnitTests](UnitTests.md)）。</span><span class="sxs-lookup"><span data-stu-id="96283-117">If adding a new feature, check that tests are included to validate the feature (see [UnitTests](UnitTests.md)).</span></span>
* <span data-ttu-id="96283-118">若要修复 bug，请编写测试来验证 bug 修补程序。</span><span class="sxs-lookup"><span data-stu-id="96283-118">If fixing a bug, write a test to verify the bug fix.</span></span>

<span data-ttu-id="96283-119">项目维护人员将评审你所作的更改。</span><span class="sxs-lookup"><span data-stu-id="96283-119">The project maintainers will review your changes.</span></span> <span data-ttu-id="96283-120">我们打算在 3 个工作日内评审所有更改。</span><span class="sxs-lookup"><span data-stu-id="96283-120">We aim to review all changes within three business days.</span></span> <span data-ttu-id="96283-121">请处理所有评审注释、将其推送到你的主题分支，并发布注释，让我们知道是否有新内容需要评审。</span><span class="sxs-lookup"><span data-stu-id="96283-121">Please address any review comments, push to your topic branch, and post a comment letting us know that there's new stuff to review.</span></span>

> [!NOTE]
> <span data-ttu-id="96283-122">我们会根据 [MRTK 编码标准指南](CodingGuidelines.md)对提交至项目的所有 PR 进行审查，因此在提交 PR 之前，请对其进行评审以确保顺利处理。</span><span class="sxs-lookup"><span data-stu-id="96283-122">All PR's submitted to the project will also be vetted according to the [MRTK coding standards guide](CodingGuidelines.md), so please review these before submitting your PR to ensure a smooth process.</span></span>

## <a name="pull-request-guidelines"></a><span data-ttu-id="96283-123">拉取请求指南</span><span class="sxs-lookup"><span data-stu-id="96283-123">Pull request guidelines</span></span>

<span data-ttu-id="96283-124">这些指南是根据 [Google 的工程实践](https://google.github.io/eng-practices/review/developer/small-cls.html)编写的。</span><span class="sxs-lookup"><span data-stu-id="96283-124">These guidelines are based off of the [Google's engineering practices](https://google.github.io/eng-practices/review/developer/small-cls.html).</span></span>

### <a name="keep-pull-requests-small"></a><span data-ttu-id="96283-125">减少拉取请求的数量</span><span class="sxs-lookup"><span data-stu-id="96283-125">Keep pull requests small</span></span>

<span data-ttu-id="96283-126">PR 数量越少，越能更快、更全面地进行审查，也越不可能引入 bug，越容易回滚，且越容易合并。</span><span class="sxs-lookup"><span data-stu-id="96283-126">Smaller PRs are reviewed more quickly and thoroughly, are less likely to introduce bugs, easier to roll back, and easier to merge.</span></span>

<span data-ttu-id="96283-127">拉取请求的数量应足够的少，以便一名工程师可在 30 分钟内完成审查。</span><span class="sxs-lookup"><span data-stu-id="96283-127">Pull requests should be small enough that an engineer could review it in under 30 minutes.</span></span> <span data-ttu-id="96283-128">请尝试尽量少做更改，只处理一个问题。</span><span class="sxs-lookup"><span data-stu-id="96283-128">Try to make a minimal change that addresses just one thing.</span></span> <span data-ttu-id="96283-129">如果必须创建一个较大的 PR，请将其拆分为几个 PR，要么加入你的本地分支，要么加入 MRTK 的功能分支。</span><span class="sxs-lookup"><span data-stu-id="96283-129">If you must create a large PR, split it into several PRs that go into either your local branch, or a feature branch of MRTK.</span></span> <span data-ttu-id="96283-130">不要添加新的资产（例如 fbx、obj 文件），而是要重复使用现有的资产。</span><span class="sxs-lookup"><span data-stu-id="96283-130">Avoid adding new assets (e.g. fbx, obj files) and instead aim to re-use existing assets.</span></span>

### <a name="tests-should-be-added-in-the-same-pr-as-your-fix--feature-except-for-emergencies"></a><span data-ttu-id="96283-131">应将测试添加到包含你的修补程序/功能的 PR 中（紧急情况除外）</span><span class="sxs-lookup"><span data-stu-id="96283-131">Tests should be added in the same PR as your fix / feature, except for emergencies</span></span>

<span data-ttu-id="96283-132">测试是确保更改不会导致现有代码性能下降的最佳方式，但在提交拉取请求时，也很容易忘记添加测试。</span><span class="sxs-lookup"><span data-stu-id="96283-132">Tests are the best way to ensure changes do not regress existing code, but it is also easy to forget about tests when submitting pull requests.</span></span> <span data-ttu-id="96283-133">要求在 PR 中包含测试是确保编写测试的绝佳方式。</span><span class="sxs-lookup"><span data-stu-id="96283-133">Requiring that they go in with your PR are a great way to ensure that tests get written.</span></span>

<span data-ttu-id="96283-134">每项功能和 bug 修补程序都应具有关联的测试。</span><span class="sxs-lookup"><span data-stu-id="96283-134">Every feature and bug fix should have tests associated with it.</span></span> <span data-ttu-id="96283-135">如果你没有编写测试的专业知识，或者没时间编写，请创建一个问题来编写测试，并使用“考虑用于当前迭代”标签标记这些测试。</span><span class="sxs-lookup"><span data-stu-id="96283-135">If you do not have the expertise or time to write a test, create an issue to write the tests, and mark them with label **Consider for Current Iteration**.</span></span>

### <a name="documentation-should-be-added-in-the-same-pull-request-as-a-fix--feature"></a><span data-ttu-id="96283-136">应将文档添加到包含你的修补程序/功能的拉取请求中</span><span class="sxs-lookup"><span data-stu-id="96283-136">Documentation should be added in the same pull request as a fix / feature</span></span>

<span data-ttu-id="96283-137">在了解如何使用某项功能时，开发人员首先看的不是代码，而是文档。</span><span class="sxs-lookup"><span data-stu-id="96283-137">Most developers look first at documentation, not code, when understanding how to use a feature.</span></span> <span data-ttu-id="96283-138">确保文档是最新的可使人们更加容易地使用和依赖 MRTK。</span><span class="sxs-lookup"><span data-stu-id="96283-138">Ensuring documentation is up to date makes it much easier for people to consume and rely MRTK.</span></span>  <span data-ttu-id="96283-139">文档应始终与相关拉取捆绑在一起，确保项目保持最新且一致。</span><span class="sxs-lookup"><span data-stu-id="96283-139">Documentation should always be bundled with the related pull to ensure items remain up-to-date and consistent.</span></span>

<span data-ttu-id="96283-140">确保每个公共字段、方法和属性都有[三斜杠式摘要注释](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html)，以便我们的 docfx 站点能为字段/方法生成相关说明。</span><span class="sxs-lookup"><span data-stu-id="96283-140">Ensure every public field, method, property has [triple slash summary comments](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html) so our docfx site can generate descriptions for fields / methods.</span></span> <span data-ttu-id="96283-141">如有需要，请更新“文档”文件夹中的 markdown 文件。</span><span class="sxs-lookup"><span data-stu-id="96283-141">If needed, update markdown files in Documentation folder.</span></span>

### <a name="pull-request-descriptions-should-clearly-and-completely-describe-changes"></a><span data-ttu-id="96283-142">拉取请求说明应清晰、完整地描述所作更改</span><span class="sxs-lookup"><span data-stu-id="96283-142">Pull request descriptions should clearly and completely describe changes</span></span>

<span data-ttu-id="96283-143">清晰完整的拉取请求说明可确保审阅者理解他们正在评审的内容。</span><span class="sxs-lookup"><span data-stu-id="96283-143">Clear and complete descriptions of pull requests ensure reviewers understand what they are reviewing.</span></span>

<span data-ttu-id="96283-144">若要添加包含 UX 的功能，请就你要更改的功能添加图片/gif。</span><span class="sxs-lookup"><span data-stu-id="96283-144">If adding features that contain UX, add an image / gif of the feature you are changing.</span></span> <span data-ttu-id="96283-145">[这是一个很好的例子](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532)。</span><span class="sxs-lookup"><span data-stu-id="96283-145">[Here is a good example](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532).</span></span> <span data-ttu-id="96283-146">另一种建议是在前后添加 gif，[例如在此拉取请求中](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896)。</span><span class="sxs-lookup"><span data-stu-id="96283-146">Another suggestion is to have a gif of Before and After, [for example in this pull request](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896).</span></span> <span data-ttu-id="96283-147">我们建议使用 [ScreenToGif](https://www.screentogif.com/) 工具来从屏幕捕获中生成 gif。</span><span class="sxs-lookup"><span data-stu-id="96283-147">A tool we recommend for generating gifs from screen captures is [ScreenToGif](https://www.screentogif.com/).</span></span>
