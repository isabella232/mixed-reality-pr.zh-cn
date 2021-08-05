---
title: 参与 MRTK 工作
description: 如何参与混合现实Toolkit
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， Bug 报告，
ms.openlocfilehash: e24ef1c568f9d6fa84fdd49dac17581f71dfc466018929e045de43d58549c09b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210744"
---
# <a name="contributing-to-mrtk"></a>参与 MRTK 工作

混合现实Toolkit (MRTK) 欢迎来自社区的贡献。 所有更改（小或大）都需要遵守 [MRTK](coding-guidelines.md)编码标准，因此请确保在开发时熟悉这些更改，以避免在评审更改时出现延迟。

如果有任何疑问，请访问 Slack 上的 [混合现实工具包通道](https://holodevelopers.slack.com/messages/C2H4HT858)。
可通过[自动邀请发送程序](https://holodevelopersslack.azurewebsites.net/)加入 Slack 社区。

## <a name="submission-process"></a>提交过程

我们提供了多个路径，使开发人员能够参与混合现实Toolkit，这一切都从创建新问题[开始](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose)。

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

在此处提交：

- **Bug 报告**- 混合现实组件之一Toolkit问题
- **文档问题**- 混合现实Toolkit [问题](https://microsoft.github.io/MixedRealityToolkit-Unity)
- **功能请求**- 新的混合现实Toolkit建议

## <a name="proposing-feature-requests"></a>建议的功能请求

请求新的混合现实Toolkit功能时，必须记录要解决的客户权益/问题。 提交后，将在提交时查看并讨论GitHub。 我们鼓励对每项功能建议进行公开而积极的讨论，以确保该工作对大量客户有利。

为了避免需要重新修改该功能，通常建议在评审阶段不开始开发该功能。 在许多情况下，社区评审过程会发现一个或多个问题，这些问题可能需要对建议实现进行重大更改。

> [!NOTE]
> 如果要处理积压工作上已存在的项，可以将该工作项用作建议。 请务必对任务进行注释，通知维护人员你正在努力完成它。

## <a name="contribution-process"></a>贡献过程

若要开始，只需执行以下步骤：

1. 创建存储库分支。 单击页面右上方的"分叉"按钮，然后按照流操作。
1. 在分支中从主分支 (分支创建) ，以便更轻松地[](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main)隔离任何更改，直到准备好提交。 有关版本稳定期间的错误修复，请查找最新的 `prerelease/*` 分支。 新功能应始终进入 `main` 。

如果对 Git 工作流还很了解， [请查看 Github 中的此简介](https://guides.github.com/activities/hello-world/)。

添加 bug 修复或功能时，请执行以下步骤：

1. 实现 bug 修复或功能。 有关生成和部署 MRTK 的说明，请参阅 [部署到 Hololens 和 WMR 设备](../supported-devices/wmr-mrtk.md)。 请记得遵循 [编码准则](../contributing/coding-guidelines.md)。
1. 如果添加功能，则还要添加演示该功能的示例场景。
1. 如果添加实验性功能，则不需要编写测试和文档。 相反，请 [遵循实验性功能准则](../contributing/experimental-features.md)。
1. 添加测试以验证 bug 修复/功能。 有关编写和运行测试的说明位于 [UnitTests](../contributing/unit-tests.md)。
1. 确保根据文档 (中所述) 代码[和特性。](../contributing/documentation-guide.md)
1. 确保代码在所有平台上都正常工作。 有关 [支持的平台列表](../release-notes/mrtk-26-release-notes.md) ，请参阅发行说明。 对于Windows UWP 项目，代码必须符合[WACK。](https://developer.microsoft.com/windows/develop/app-certification-kit) 为此，请生成一个Visual Studio解决方案，右键单击项目;**Store**  > **创建应用包**。 按照提示运行 WACK 测试。 请确保它们全部成功。
1. 提出拉取 [请求时，](../contributing/pull-requests.md) 请按照拉取请求中的说明进行操作。
