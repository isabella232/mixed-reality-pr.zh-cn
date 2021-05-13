---
title: 贡献
description: 如何参与混合现实工具包
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， Bug 报告，
ms.openlocfilehash: 11a62708b4cb1a5acc3d230f933be2e88e0ac87b
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850363"
---
# <a name="contributing"></a><span data-ttu-id="695fc-104">贡献</span><span class="sxs-lookup"><span data-stu-id="695fc-104">Contributing</span></span>

<span data-ttu-id="695fc-105">混合现实工具包 (MRTK) 欢迎来自社区的贡献。</span><span class="sxs-lookup"><span data-stu-id="695fc-105">The Mixed Reality Toolkit (MRTK) welcomes contributions from the community.</span></span> <span data-ttu-id="695fc-106">所有更改（小或大）都需要遵守 [MRTK](coding-guidelines.md)编码标准，因此请确保在开发时熟悉这些更改，以避免在评审更改时出现延迟。</span><span class="sxs-lookup"><span data-stu-id="695fc-106">All changes be they small or large, need to adhere to the [MRTK coding standards](coding-guidelines.md), so please ensure you are familiar with these while developing to avoid delays when the change is being reviewed.</span></span>

<span data-ttu-id="695fc-107">如果有任何疑问，请访问 Slack 上的 [混合现实工具包通道](https://holodevelopers.slack.com/messages/C2H4HT858)。</span><span class="sxs-lookup"><span data-stu-id="695fc-107">If you have any questions, please reach out on the [mixed-reality-toolkit channel on Slack](https://holodevelopers.slack.com/messages/C2H4HT858).</span></span>
<span data-ttu-id="695fc-108">可通过[自动邀请发送程序](https://holodevelopersslack.azurewebsites.net/)加入 Slack 社区。</span><span class="sxs-lookup"><span data-stu-id="695fc-108">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

## <a name="submission-process"></a><span data-ttu-id="695fc-109">提交过程</span><span class="sxs-lookup"><span data-stu-id="695fc-109">Submission process</span></span>

<span data-ttu-id="695fc-110">我们提供了多个路径，使开发人员能够参与混合现实工具包，这一切都从创建新 [问题 开始](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose)。</span><span class="sxs-lookup"><span data-stu-id="695fc-110">We provide several paths to enable developers to contribute to the Mixed Reality Toolkit, all starting with [creating a new Issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose).</span></span>

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

<span data-ttu-id="695fc-111">在此处提交：</span><span class="sxs-lookup"><span data-stu-id="695fc-111">From here you file:</span></span>

- <span data-ttu-id="695fc-112">**Bug 报告** - 混合现实工具包组件之一的功能问题</span><span class="sxs-lookup"><span data-stu-id="695fc-112">**Bug report** - Functionality issue with one of the Mixed Reality Toolkit components</span></span>
- <span data-ttu-id="695fc-113">**文档问题** - 混合现实工具包文档 [的问题](https://microsoft.github.io/MixedRealityToolkit-Unity)</span><span class="sxs-lookup"><span data-stu-id="695fc-113">**Documentation issue** - Issue with the Mixed Reality Toolkit [documentation](https://microsoft.github.io/MixedRealityToolkit-Unity)</span></span>
- <span data-ttu-id="695fc-114">**功能请求** - 新混合现实工具包功能的建议</span><span class="sxs-lookup"><span data-stu-id="695fc-114">**Feature request** - Proposal for a new Mixed Reality Toolkit feature</span></span>

## <a name="proposing-feature-requests"></a><span data-ttu-id="695fc-115">建议的功能请求</span><span class="sxs-lookup"><span data-stu-id="695fc-115">Proposing feature requests</span></span>

<span data-ttu-id="695fc-116">请求新的混合现实工具包功能时，必须记录要解决的客户权益/问题。</span><span class="sxs-lookup"><span data-stu-id="695fc-116">When requesting a new Mixed Reality Toolkit feature, it is important to document the customer benefit / problem to be solved.</span></span> <span data-ttu-id="695fc-117">提交后，将在 GitHub 上查看并讨论功能请求。</span><span class="sxs-lookup"><span data-stu-id="695fc-117">Once submitted, a feature request will be reviewed and discussed on GitHub.</span></span> <span data-ttu-id="695fc-118">我们鼓励对每项功能建议进行公开而积极的讨论，以确保该工作对大量客户有利。</span><span class="sxs-lookup"><span data-stu-id="695fc-118">We encourage open and constructive discussion of each feature proposal to ensure that the work is beneficial to a large segment of customers.</span></span>

<span data-ttu-id="695fc-119">为了避免需要重新修改该功能，通常建议在评审阶段不开始开发该功能。</span><span class="sxs-lookup"><span data-stu-id="695fc-119">To avoid needing to rework the feature, it is generally recommended that development of the feature does not begin during the review phase.</span></span> <span data-ttu-id="695fc-120">在许多情况下，社区评审过程会发现一个或多个问题，这些问题可能需要对建议实现进行重大更改。</span><span class="sxs-lookup"><span data-stu-id="695fc-120">Many times, the community review process uncovers one or more issues that may require significant changes in the proposed implementation.</span></span>

> [!NOTE]
> <span data-ttu-id="695fc-121">如果要处理积压工作上已存在的项，可以将该工作项用作建议。</span><span class="sxs-lookup"><span data-stu-id="695fc-121">If you wish to work on something that already exists on our backlog, you can use that work item as your proposal.</span></span> <span data-ttu-id="695fc-122">请务必对任务进行注释，通知维护人员你正在努力完成它。</span><span class="sxs-lookup"><span data-stu-id="695fc-122">Be sure to also comment on the task notifying maintainers that you're working towards completing it.</span></span>

## <a name="contribution-process"></a><span data-ttu-id="695fc-123">贡献过程</span><span class="sxs-lookup"><span data-stu-id="695fc-123">Contribution process</span></span>

<span data-ttu-id="695fc-124">若要开始，只需执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="695fc-124">To get started, simply follow these steps:</span></span>

1. <span data-ttu-id="695fc-125">创建存储库分支。</span><span class="sxs-lookup"><span data-stu-id="695fc-125">Fork the repository.</span></span> <span data-ttu-id="695fc-126">单击页面右上方的 "分叉" 按钮，并按照流进行操作。</span><span class="sxs-lookup"><span data-stu-id="695fc-126">Click on the "Fork" button on the top right of the page and follow the flow.</span></span>
1. <span data-ttu-id="695fc-127">在分支中创建分支 ([主](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) 分支) ，以便更轻松地隔离任何更改，直到准备好进行提交。</span><span class="sxs-lookup"><span data-stu-id="695fc-127">Create a branch in your fork (off of the [main](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) branch) to make it easier to isolate any changes until ready for submission.</span></span> <span data-ttu-id="695fc-128">对于在发布稳定期间的 bug 修复，请查找最新的 `prerelease/*` 分支。</span><span class="sxs-lookup"><span data-stu-id="695fc-128">For bug fixes during a release stabilization period, look for the latest `prerelease/*` branch.</span></span> <span data-ttu-id="695fc-129">新功能应始终进入 `main` 。</span><span class="sxs-lookup"><span data-stu-id="695fc-129">New features should always go into `main`.</span></span>

<span data-ttu-id="695fc-130">如果你不熟悉 Git 工作流，请 [查看 Github 中的此简介](https://guides.github.com/activities/hello-world/)。</span><span class="sxs-lookup"><span data-stu-id="695fc-130">If you are new to to the Git workflow, [check out this introduction from Github](https://guides.github.com/activities/hello-world/).</span></span>

<span data-ttu-id="695fc-131">添加 bug 修复或功能时，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="695fc-131">When adding a bug fix or feature, follow these steps:</span></span>

1. <span data-ttu-id="695fc-132">实现 bug 修复或功能。</span><span class="sxs-lookup"><span data-stu-id="695fc-132">Implement the bug fix or feature.</span></span> <span data-ttu-id="695fc-133">有关生成和部署 MRTK 的说明，请参阅 [部署到 Hololens 和 WMR 设备](../supported-devices/wmr-mrtk.md)。</span><span class="sxs-lookup"><span data-stu-id="695fc-133">Instructions for building and deploying MRTK are at [Deploying to Hololens and WMR devices](../supported-devices/wmr-mrtk.md).</span></span> <span data-ttu-id="695fc-134">请记住遵循 [编码准则](../contributing/coding-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="695fc-134">Remember to follow the [Coding Guidelines](../contributing/coding-guidelines.md).</span></span>
1. <span data-ttu-id="695fc-135">如果添加功能，还应添加演示该功能的示例场景。</span><span class="sxs-lookup"><span data-stu-id="695fc-135">If adding a feature, also add an example scene that demonstrates the feature.</span></span>
1. <span data-ttu-id="695fc-136">如果添加实验功能，则不需要编写测试和文档。</span><span class="sxs-lookup"><span data-stu-id="695fc-136">If adding an experimental feature, then writing tests and documentation are not necessary.</span></span> <span data-ttu-id="695fc-137">相反，请遵循 [试验性功能准则](../contributing/experimental-features.md)。</span><span class="sxs-lookup"><span data-stu-id="695fc-137">Instead, follow [experimental feature guidelines](../contributing/experimental-features.md).</span></span>
1. <span data-ttu-id="695fc-138">添加用于验证 bug 修复/功能的测试。</span><span class="sxs-lookup"><span data-stu-id="695fc-138">Add tests to verify the bug fix / feature.</span></span> <span data-ttu-id="695fc-139">有关编写和运行测试的说明，请参阅 [run-unittests](../contributing/unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="695fc-139">Instructions for writing and running tests are at [UnitTests](../contributing/unit-tests.md).</span></span>
1. <span data-ttu-id="695fc-140">请确保按照 [文档准则](../contributing/documentation-guide.md)所述说明了代码和功能 (的) 。</span><span class="sxs-lookup"><span data-stu-id="695fc-140">Ensure the code and feature(s) are documented as described in the [Documentation Guidelines](../contributing/documentation-guide.md).</span></span>
1. <span data-ttu-id="695fc-141">确保代码在所有平台上按预期方式工作。</span><span class="sxs-lookup"><span data-stu-id="695fc-141">Ensure the code works as intended on all platforms.</span></span> <span data-ttu-id="695fc-142">有关支持的平台列表，请参阅 [发行说明](../release-notes/mrtk-26-release-notes.md) 。</span><span class="sxs-lookup"><span data-stu-id="695fc-142">Please see [Release notes](../release-notes/mrtk-26-release-notes.md) for the list of supported platforms.</span></span> <span data-ttu-id="695fc-143">对于 Windows UWP 项目，代码必须 [符合 WACK](https://developer.microsoft.com/windows/develop/app-certification-kit)。</span><span class="sxs-lookup"><span data-stu-id="695fc-143">For Windows UWP projects, code must be [WACK compliant](https://developer.microsoft.com/windows/develop/app-certification-kit).</span></span> <span data-ttu-id="695fc-144">为此，请生成 Visual Studio 解决方案，右键单击 "项目";**应用商店**  > **创建应用包**。</span><span class="sxs-lookup"><span data-stu-id="695fc-144">To do this, generate a Visual Studio solution, right click on project; **Store** > **Create App Packages**.</span></span> <span data-ttu-id="695fc-145">按照提示操作并运行 WACK 测试。</span><span class="sxs-lookup"><span data-stu-id="695fc-145">Follow the prompts and run WACK tests.</span></span> <span data-ttu-id="695fc-146">请确保它们全部成功。</span><span class="sxs-lookup"><span data-stu-id="695fc-146">Make sure they all succeed.</span></span>
1. <span data-ttu-id="695fc-147">提出拉取 [请求时，](../contributing/pull-requests.md) 请按照拉取请求中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="695fc-147">Follow the instructions at [Pull Requests](../contributing/pull-requests.md) when making a pull request.</span></span>
