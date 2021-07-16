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
# <a name="contributing-to-mrtk"></a>参与 MRTK

混合现实 Toolkit (MRTK) 欢迎社区的内容。 所有更改都是小或大，需要遵守 [MRTK 编码标准](coding-guidelines.md)，因此请确保在开发过程中熟悉这些更改，以避免在查看更改时出现延迟。

如果你有任何疑问，请在可松弛性上了解 [混合现实工具包通道](https://holodevelopers.slack.com/messages/C2H4HT858)。
可通过[自动邀请发送程序](https://holodevelopersslack.azurewebsites.net/)加入 Slack 社区。

## <a name="submission-process"></a>提交过程

我们提供了多个路径，使开发人员能够参与到混合现实 Toolkit，这一切都[是在创建新问题](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose)时开始的。

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

从此处获取文件：

- **Bug 报告**-与混合现实 Toolkit 组件之一有关的功能问题
- **文档问题**-混合现实 Toolkit [文档](https://microsoft.github.io/MixedRealityToolkit-Unity)的问题
- **功能请求**-针对新的 Mixed Reality Toolkit 功能的建议

## <a name="proposing-feature-requests"></a>建议功能请求

请求新的 Mixed Reality Toolkit 功能时，请务必记录要解决的客户权益/问题。 提交后，将查看并讨论 GitHub 上的功能请求。 我们鼓励对每个功能提议的公开和建设性讨论，以确保工作对于大型客户群非常有利。

为了避免需要重新修改功能，通常建议开发功能，而不是在评审阶段开始。 很多时候，社区审核流程发现一个或多个可能需要在建议的实现中进行重大更改的问题。

> [!NOTE]
> 如果要处理积压工作（backlog）中已存在的内容，可以使用该工作项作为建议。 另外，请确保对任务进行注释，通知维护人员您正在完成该任务。

## <a name="contribution-process"></a>贡献过程

若要开始，只需执行以下步骤：

1. 创建存储库分支。 单击页面右上方的 "分叉" 按钮，并按照流进行操作。
1. 在分支中创建分支 ([主](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) 分支) ，以便更轻松地隔离任何更改，直到准备好进行提交。 对于在发布稳定期间的 bug 修复，请查找最新的 `prerelease/*` 分支。 新功能应始终进入 `main` 。

如果你不熟悉 Git 工作流，请 [查看 Github 中的此简介](https://guides.github.com/activities/hello-world/)。

添加 bug 修复或功能时，请执行以下步骤：

1. 实现 bug 修复或功能。 有关生成和部署 MRTK 的说明，请参阅 [部署到 Hololens 和 WMR 设备](../supported-devices/wmr-mrtk.md)。 请记住遵循 [编码准则](../contributing/coding-guidelines.md)。
1. 如果添加功能，还应添加演示该功能的示例场景。
1. 如果添加实验功能，则不需要编写测试和文档。 相反，请遵循 [试验性功能准则](../contributing/experimental-features.md)。
1. 添加用于验证 bug 修复/功能的测试。 有关编写和运行测试的说明，请参阅 [run-unittests](../contributing/unit-tests.md)。
1. 请确保按照 [文档准则](../contributing/documentation-guide.md)所述说明了代码和功能 (的) 。
1. 确保代码在所有平台上按预期方式工作。 有关支持的平台列表，请参阅 [发行说明](../release-notes/mrtk-26-release-notes.md) 。 对于 Windows UWP 项目，代码必须[符合 WACK](https://developer.microsoft.com/windows/develop/app-certification-kit)。 为此，请生成一个 Visual Studio 解决方案，右键单击 "项目";**应用商店**  > **创建应用包**。 按照提示操作并运行 WACK 测试。 确保它们都成功。
1. 发出拉取请求时，请按照 [拉取请求](../contributing/pull-requests.md) 中的说明进行操作。
