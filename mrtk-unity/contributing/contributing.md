---
title: 参与 MRTK
description: 如何参与混合现实 Toolkit
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，Bug 报告，
ms.openlocfilehash: b79f69cbb6dea1201c88d9fd1a354967ce40735e
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282044"
---
# <a name="contributing-to-mrtk"></a><span data-ttu-id="20f14-104">参与 MRTK</span><span class="sxs-lookup"><span data-stu-id="20f14-104">Contributing to MRTK</span></span>

<span data-ttu-id="20f14-105">混合现实 Toolkit (MRTK) 欢迎社区的内容。</span><span class="sxs-lookup"><span data-stu-id="20f14-105">The Mixed Reality Toolkit (MRTK) welcomes contributions from the community.</span></span> <span data-ttu-id="20f14-106">所有更改都是小或大，需要遵守 [MRTK 编码标准](coding-guidelines.md)，因此请确保在开发过程中熟悉这些更改，以避免在查看更改时出现延迟。</span><span class="sxs-lookup"><span data-stu-id="20f14-106">All changes be they small or large, need to adhere to the [MRTK coding standards](coding-guidelines.md), so please ensure you are familiar with these while developing to avoid delays when the change is being reviewed.</span></span>

<span data-ttu-id="20f14-107">如果你有任何疑问，请在可松弛性上了解 [混合现实工具包通道](https://holodevelopers.slack.com/messages/C2H4HT858)。</span><span class="sxs-lookup"><span data-stu-id="20f14-107">If you have any questions, please reach out on the [mixed-reality-toolkit channel on Slack](https://holodevelopers.slack.com/messages/C2H4HT858).</span></span>
<span data-ttu-id="20f14-108">可通过[自动邀请发送程序](https://holodevelopersslack.azurewebsites.net/)加入 Slack 社区。</span><span class="sxs-lookup"><span data-stu-id="20f14-108">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

## <a name="submission-process"></a><span data-ttu-id="20f14-109">提交过程</span><span class="sxs-lookup"><span data-stu-id="20f14-109">Submission process</span></span>

<span data-ttu-id="20f14-110">我们提供了多个路径，使开发人员能够参与到混合现实 Toolkit，这一切都[是在创建新问题](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose)时开始的。</span><span class="sxs-lookup"><span data-stu-id="20f14-110">We provide several paths to enable developers to contribute to the Mixed Reality Toolkit, all starting with [creating a new Issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose).</span></span>

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

<span data-ttu-id="20f14-111">从此处获取文件：</span><span class="sxs-lookup"><span data-stu-id="20f14-111">From here you file:</span></span>

- <span data-ttu-id="20f14-112">**Bug 报告**-与混合现实 Toolkit 组件之一有关的功能问题</span><span class="sxs-lookup"><span data-stu-id="20f14-112">**Bug report** - Functionality issue with one of the Mixed Reality Toolkit components</span></span>
- <span data-ttu-id="20f14-113">**文档问题**-混合现实 Toolkit [文档](https://microsoft.github.io/MixedRealityToolkit-Unity)的问题</span><span class="sxs-lookup"><span data-stu-id="20f14-113">**Documentation issue** - Issue with the Mixed Reality Toolkit [documentation](https://microsoft.github.io/MixedRealityToolkit-Unity)</span></span>
- <span data-ttu-id="20f14-114">**功能请求**-针对新的 Mixed Reality Toolkit 功能的建议</span><span class="sxs-lookup"><span data-stu-id="20f14-114">**Feature request** - Proposal for a new Mixed Reality Toolkit feature</span></span>

## <a name="proposing-feature-requests"></a><span data-ttu-id="20f14-115">建议功能请求</span><span class="sxs-lookup"><span data-stu-id="20f14-115">Proposing feature requests</span></span>

<span data-ttu-id="20f14-116">请求新的 Mixed Reality Toolkit 功能时，请务必记录要解决的客户权益/问题。</span><span class="sxs-lookup"><span data-stu-id="20f14-116">When requesting a new Mixed Reality Toolkit feature, it is important to document the customer benefit / problem to be solved.</span></span> <span data-ttu-id="20f14-117">提交后，将查看并讨论 GitHub 上的功能请求。</span><span class="sxs-lookup"><span data-stu-id="20f14-117">Once submitted, a feature request will be reviewed and discussed on GitHub.</span></span> <span data-ttu-id="20f14-118">我们鼓励对每个功能提议的公开和建设性讨论，以确保工作对于大型客户群非常有利。</span><span class="sxs-lookup"><span data-stu-id="20f14-118">We encourage open and constructive discussion of each feature proposal to ensure that the work is beneficial to a large segment of customers.</span></span>

<span data-ttu-id="20f14-119">为了避免需要重新修改功能，通常建议开发功能，而不是在评审阶段开始。</span><span class="sxs-lookup"><span data-stu-id="20f14-119">To avoid needing to rework the feature, it is generally recommended that development of the feature does not begin during the review phase.</span></span> <span data-ttu-id="20f14-120">很多时候，社区审核流程发现一个或多个可能需要在建议的实现中进行重大更改的问题。</span><span class="sxs-lookup"><span data-stu-id="20f14-120">Many times, the community review process uncovers one or more issues that may require significant changes in the proposed implementation.</span></span>

> [!NOTE]
> <span data-ttu-id="20f14-121">如果要处理积压工作（backlog）中已存在的内容，可以使用该工作项作为建议。</span><span class="sxs-lookup"><span data-stu-id="20f14-121">If you wish to work on something that already exists on our backlog, you can use that work item as your proposal.</span></span> <span data-ttu-id="20f14-122">另外，请确保对任务进行注释，通知维护人员您正在完成该任务。</span><span class="sxs-lookup"><span data-stu-id="20f14-122">Be sure to also comment on the task notifying maintainers that you're working towards completing it.</span></span>

## <a name="contribution-process"></a><span data-ttu-id="20f14-123">贡献过程</span><span class="sxs-lookup"><span data-stu-id="20f14-123">Contribution process</span></span>

<span data-ttu-id="20f14-124">若要开始，只需执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="20f14-124">To get started, simply follow these steps:</span></span>

1. <span data-ttu-id="20f14-125">创建存储库分支。</span><span class="sxs-lookup"><span data-stu-id="20f14-125">Fork the repository.</span></span> <span data-ttu-id="20f14-126">单击页面右上方的 "分叉" 按钮，并按照流进行操作。</span><span class="sxs-lookup"><span data-stu-id="20f14-126">Click on the "Fork" button on the top right of the page and follow the flow.</span></span>
1. <span data-ttu-id="20f14-127">在分支中创建分支 ([主](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) 分支) ，以便更轻松地隔离任何更改，直到准备好进行提交。</span><span class="sxs-lookup"><span data-stu-id="20f14-127">Create a branch in your fork (off of the [main](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) branch) to make it easier to isolate any changes until ready for submission.</span></span> <span data-ttu-id="20f14-128">对于在发布稳定期间的 bug 修复，请查找最新的 `prerelease/*` 分支。</span><span class="sxs-lookup"><span data-stu-id="20f14-128">For bug fixes during a release stabilization period, look for the latest `prerelease/*` branch.</span></span> <span data-ttu-id="20f14-129">新功能应始终进入 `main` 。</span><span class="sxs-lookup"><span data-stu-id="20f14-129">New features should always go into `main`.</span></span>

<span data-ttu-id="20f14-130">如果你不熟悉 Git 工作流，请 [查看 Github 中的此简介](https://guides.github.com/activities/hello-world/)。</span><span class="sxs-lookup"><span data-stu-id="20f14-130">If you are new to to the Git workflow, [check out this introduction from Github](https://guides.github.com/activities/hello-world/).</span></span>

<span data-ttu-id="20f14-131">添加 bug 修复或功能时，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="20f14-131">When adding a bug fix or feature, follow these steps:</span></span>

1. <span data-ttu-id="20f14-132">实现 bug 修复或功能。</span><span class="sxs-lookup"><span data-stu-id="20f14-132">Implement the bug fix or feature.</span></span> <span data-ttu-id="20f14-133">有关生成和部署 MRTK 的说明，请参阅 [部署到 Hololens 和 WMR 设备](../supported-devices/wmr-mrtk.md)。</span><span class="sxs-lookup"><span data-stu-id="20f14-133">Instructions for building and deploying MRTK are at [Deploying to Hololens and WMR devices](../supported-devices/wmr-mrtk.md).</span></span> <span data-ttu-id="20f14-134">请记住遵循 [编码准则](../contributing/coding-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="20f14-134">Remember to follow the [Coding Guidelines](../contributing/coding-guidelines.md).</span></span>
1. <span data-ttu-id="20f14-135">如果添加功能，还应添加演示该功能的示例场景。</span><span class="sxs-lookup"><span data-stu-id="20f14-135">If adding a feature, also add an example scene that demonstrates the feature.</span></span>
1. <span data-ttu-id="20f14-136">如果添加实验功能，则不需要编写测试和文档。</span><span class="sxs-lookup"><span data-stu-id="20f14-136">If adding an experimental feature, then writing tests and documentation are not necessary.</span></span> <span data-ttu-id="20f14-137">相反，请遵循 [试验性功能准则](../contributing/experimental-features.md)。</span><span class="sxs-lookup"><span data-stu-id="20f14-137">Instead, follow [experimental feature guidelines](../contributing/experimental-features.md).</span></span>
1. <span data-ttu-id="20f14-138">添加用于验证 bug 修复/功能的测试。</span><span class="sxs-lookup"><span data-stu-id="20f14-138">Add tests to verify the bug fix / feature.</span></span> <span data-ttu-id="20f14-139">有关编写和运行测试的说明，请参阅 [run-unittests](../contributing/unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="20f14-139">Instructions for writing and running tests are at [UnitTests](../contributing/unit-tests.md).</span></span>
1. <span data-ttu-id="20f14-140">请确保按照 [文档准则](../contributing/documentation-guide.md)所述说明了代码和功能 (的) 。</span><span class="sxs-lookup"><span data-stu-id="20f14-140">Ensure the code and feature(s) are documented as described in the [Documentation Guidelines](../contributing/documentation-guide.md).</span></span>
1. <span data-ttu-id="20f14-141">确保代码在所有平台上按预期方式工作。</span><span class="sxs-lookup"><span data-stu-id="20f14-141">Ensure the code works as intended on all platforms.</span></span> <span data-ttu-id="20f14-142">有关支持的平台列表，请参阅 [发行说明](../release-notes/mrtk-26-release-notes.md) 。</span><span class="sxs-lookup"><span data-stu-id="20f14-142">Please see [Release notes](../release-notes/mrtk-26-release-notes.md) for the list of supported platforms.</span></span> <span data-ttu-id="20f14-143">对于 Windows UWP 项目，代码必须[符合 WACK](https://developer.microsoft.com/windows/develop/app-certification-kit)。</span><span class="sxs-lookup"><span data-stu-id="20f14-143">For Windows UWP projects, code must be [WACK compliant](https://developer.microsoft.com/windows/develop/app-certification-kit).</span></span> <span data-ttu-id="20f14-144">为此，请生成一个 Visual Studio 解决方案，右键单击 "项目";**应用商店**  > **创建应用包**。</span><span class="sxs-lookup"><span data-stu-id="20f14-144">To do this, generate a Visual Studio solution, right click on project; **Store** > **Create App Packages**.</span></span> <span data-ttu-id="20f14-145">按照提示操作并运行 WACK 测试。</span><span class="sxs-lookup"><span data-stu-id="20f14-145">Follow the prompts and run WACK tests.</span></span> <span data-ttu-id="20f14-146">确保它们都成功。</span><span class="sxs-lookup"><span data-stu-id="20f14-146">Make sure they all succeed.</span></span>
1. <span data-ttu-id="20f14-147">发出拉取请求时，请按照 [拉取请求](../contributing/pull-requests.md) 中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="20f14-147">Follow the instructions at [Pull Requests](../contributing/pull-requests.md) when making a pull request.</span></span>
