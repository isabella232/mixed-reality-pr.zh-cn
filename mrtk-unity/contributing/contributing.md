---
title: 参与 MRTK
description: 如何参与混合现实工具包
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， Bug 报告，
ms.openlocfilehash: 8132c39a2bac7ae0926f125a6362e411100c8406
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144514"
---
# <a name="contributing"></a>供稿

混合现实工具包 (MRTK) 欢迎来自社区的贡献。 所有更改（小或大）都需要遵守 [MRTK](coding-guidelines.md)编码标准，因此请确保在开发时熟悉这些更改，以避免在评审更改时出现延迟。

如果有任何疑问，请访问 Slack 上的 [混合现实工具包通道](https://holodevelopers.slack.com/messages/C2H4HT858)。
可通过[自动邀请发送程序](https://holodevelopersslack.azurewebsites.net/)加入 Slack 社区。

## <a name="submission-process"></a>提交过程

我们提供了多个路径，使开发人员能够参与混合现实工具包，这一切都从创建新 [问题 开始](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose)。

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

在此处提交：

- **Bug 报告** - 混合现实工具包组件之一的功能问题
- **文档问题** - 混合现实工具包文档 [的问题](https://microsoft.github.io/MixedRealityToolkit-Unity)
- **功能请求** - 新混合现实工具包功能的建议

## <a name="proposing-feature-requests"></a>建议的功能请求

请求新的混合现实工具包功能时，必须记录要解决的客户权益/问题。 提交后，将在 GitHub 上查看并讨论功能请求。 我们鼓励对每项功能建议进行公开而积极的讨论，以确保该工作对大量客户有利。

为了避免需要重新修改该功能，通常建议在评审阶段不开始开发该功能。 在许多情况下，社区评审过程会发现一个或多个问题，这些问题可能需要对建议实现进行重大更改。

> [!NOTE]
> 如果要处理积压工作上已存在的项，可以将该工作项用作建议。 请务必对任务进行注释，通知维护人员你正在努力完成它。

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
1. 确保代码在所有平台上按预期方式工作。 有关支持的平台列表，请参阅 [发行说明](../release-notes/mrtk-26-release-notes.md) 。 对于 Windows UWP 项目，代码必须 [符合 WACK](https://developer.microsoft.com/windows/develop/app-certification-kit)。 为此，请生成 Visual Studio 解决方案，右键单击 "项目";**应用商店**  > **创建应用包**。 按照提示操作并运行 WACK 测试。 确保它们都成功。
1. 发出拉取请求时，请按照 [拉取请求](../contributing/pull-requests.md) 中的说明进行操作。
