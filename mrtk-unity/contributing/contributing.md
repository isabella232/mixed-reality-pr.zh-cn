---
title: 贡献
description: 如何参与混合现实工具包
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，Bug 报告，
ms.openlocfilehash: 525e704ae2f09580c8c19ca7e8a25dad4aed2647
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489257"
---
# <a name="contributing"></a>供稿

混合现实工具包 (MRTK) 欢迎社区的内容。 所有更改都是小或大，需要遵守 [MRTK 编码标准](coding-guidelines.md)，因此请确保在开发过程中熟悉这些更改，以避免在查看更改时出现延迟。

如果你有任何疑问，请在可松弛性上了解 [混合现实工具包通道](https://holodevelopers.slack.com/messages/C2H4HT858)。
可通过[自动邀请发送程序](https://holodevelopersslack.azurewebsites.net/)加入 Slack 社区。

## <a name="submission-process"></a>提交过程

我们提供了多个路径，使开发人员能够参与混合现实工具包，这一切都 [是在创建新问题](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose)时开始的。

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

从此处获取文件：

- 与一个混合现实工具包组件有关的 **Bug 报告** 功能问题
- **文档问题**-混合现实工具包 [文档](https://microsoft.github.io/MixedRealityToolkit-Unity)的问题
- 针对新的混合现实工具包功能的 **功能请求**-建议

## <a name="proposing-feature-requests"></a>建议功能请求

在请求新的混合现实工具包功能时，请务必记录要解决的客户权益/问题。 提交后，将查看并讨论 GitHub 上的功能请求。 我们鼓励对每个功能提议的公开和建设性讨论，以确保工作对于大型客户群非常有利。

为了避免需要重新修改功能，通常建议开发功能，而不是在评审阶段开始。 很多时候，社区审核流程发现一个或多个可能需要在建议的实现中进行重大更改的问题。

> [!NOTE]
> 如果要处理积压工作（backlog）中已存在的内容，可以使用该工作项作为建议。 另外，请确保对任务进行注释，通知维护人员您正在完成该任务。

## <a name="contribution-process"></a>贡献过程

若要开始，只需执行以下步骤：

1. 创建存储库分支。 单击页面右上方的"分叉"按钮，然后按照流操作。
1. 在分支中从主分支 (分支创建) ，以便更轻松地[](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main)隔离任何更改，直到准备好提交。 有关版本稳定期间的错误修复，请查找最新的 `prerelease/*` 分支。 新功能应始终进入 `main` 。

如果对 Git 工作流还很了解， [请查看 Github 中的此简介](https://guides.github.com/activities/hello-world/)。

添加 bug 修复或功能时，请执行以下步骤：

1. 实现 bug 修复或功能。 有关生成和部署 MRTK 的说明，请参阅 [BuildAndDeploy](../updates-deployment/build-and-deploy.md)。 请记得遵循 [编码准则](../contributing/coding-guidelines.md)。
1. 如果添加功能，则还要添加演示该功能的示例场景。
1. 如果添加实验性功能，则不需要编写测试和文档。 相反，请 [遵循实验性功能准则](../contributing/experimental-features.md)。
1. 添加测试以验证 bug 修复/功能。 有关编写和运行测试的说明位于 [UnitTests](../contributing/unit-tests.md)。
1. 确保根据文档 (中所述) 代码[和特性。](../contributing/documentation-guide.md)
1. 确保代码在所有平台上都正常工作。 有关 [支持的平台列表](../release-notes/mrtk-26-release-notes.md) ，请参阅发行说明。 对于 Windows UWP 项目，代码必须符合[WACK。](https://developer.microsoft.com/windows/develop/app-certification-kit) 为此，请生成一个Visual Studio解决方案，右键单击项目;**Store**  > **创建应用包**。 按照提示运行 WACK 测试。 确保它们都成功。
1. 发出拉取请求时，请按照 [拉取请求](../contributing/pull-requests.md) 中的说明进行操作。
