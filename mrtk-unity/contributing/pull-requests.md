---
title: 拉取请求
description: 与拉取请求相关的详细信息。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, 混合现实, 开发, MRTK, PR,
ms.openlocfilehash: 7fb0dea4616acbf91b0459397f4a05f05a167947
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144747"
---
# <a name="pull-requests"></a>拉取请求

## <a name="prerequisites"></a>先决条件

如果你之前未向 Microsoft 项目贡献过内容，系统可能会要求你签署[贡献许可协议](https://cla.microsoft.com/)。
如果你贡献过内容，拉取请求 (PR) 中的注释将显示此信息。

> [!IMPORTANT]
> 如果你是 Microsoft 员工，且不属于 [GitHub 上的 Microsoft 组织](https://github.com/Microsoft)，那么在发起拉取请求之前，请访问 [Microsoft 中的开放源代码](https://opensource.microsoft.com/)，在 corpnet 上关联你的 Microsoft 和 GitHub 帐户。 你需要提前执行一些操作。

## <a name="creating-a-pull-request"></a>创建拉取请求

准备好提交拉取请求时， [请创建面向](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/main...main?expand=1) 主分支的 [拉取](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) 请求。 有关版本稳定期间的错误修复，请查找最新的 `prerelease/*` 分支。 新功能应始终进入 `main` 。

请阅读指南，确保你的拉取请求遵循这些指南。

* 务必提及与 PR 相关的所有问题/功能请求或任务。
* 检查拉取请求是否仅包含与 PR 相关的文件/更改。
* 检查文档是否是最新的且是否被包含在内。 检查所有公共字段是否都有注释。
* 若要添加新功能，请检查是否包含了测试来验证该功能（参见 [UnitTests](../contributing/unit-tests.md)）。
* 若要修复 bug，请编写测试来验证 bug 修补程序。

项目维护人员将评审你所作的更改。 我们打算在 3 个工作日内评审所有更改。 请处理所有评审注释、将其推送到你的主题分支，并发布注释，让我们知道是否有新内容需要评审。

> [!NOTE]
> 我们会根据 [MRTK 编码标准指南](../contributing/coding-guidelines.md)对提交至项目的所有 PR 进行审查，因此在提交 PR 之前，请对其进行评审以确保顺利处理。

## <a name="pull-request-guidelines"></a>拉取请求指南

这些指南是根据 [Google 的工程实践](https://google.github.io/eng-practices/review/developer/small-cls.html)编写的。

### <a name="keep-pull-requests-small"></a>减少拉取请求的数量

PR 数量越少，越能更快、更全面地进行审查，也越不可能引入 bug，越容易回滚，且越容易合并。

拉取请求的数量应足够的少，以便一名工程师可在 30 分钟内完成审查。 请尝试尽量少做更改，只处理一个问题。 如果必须创建一个较大的 PR，请将其拆分为几个 PR，要么加入你的本地分支，要么加入 MRTK 的功能分支。 不要添加新的资产（例如 fbx、obj 文件），而是要重复使用现有的资产。

### <a name="tests-should-be-added-in-the-same-pr-as-your-fix--feature-except-for-emergencies"></a>应将测试添加到包含你的修补程序/功能的 PR 中（紧急情况除外）

测试是确保更改不会导致现有代码性能下降的最佳方式，但在提交拉取请求时，也很容易忘记添加测试。 要求在 PR 中包含测试是确保编写测试的绝佳方式。

每项功能和 bug 修补程序都应具有关联的测试。 如果你没有编写测试的专业知识，或者没时间编写，请创建一个问题来编写测试，并使用“考虑用于当前迭代”标签标记这些测试。

### <a name="documentation-should-be-added-in-the-same-pull-request-as-a-fix--feature"></a>应将文档添加到包含你的修补程序/功能的拉取请求中

在了解如何使用某项功能时，开发人员首先看的不是代码，而是文档。 确保文档是最新的可使人们更加容易地使用和依赖 MRTK。  文档应始终与相关拉取捆绑在一起，确保项目保持最新且一致。

确保每个公共字段、方法和属性都有[三斜杠式摘要注释](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html)，以便我们的 docfx 站点能为字段/方法生成相关说明。 如有需要，请更新“文档”文件夹中的 markdown 文件。

### <a name="pull-request-descriptions-should-clearly-and-completely-describe-changes"></a>拉取请求说明应清晰、完整地描述所作更改

清晰完整的拉取请求说明可确保审阅者理解他们正在评审的内容。

若要添加包含 UX 的功能，请就你要更改的功能添加图片/gif。 [这是一个很好的例子](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532)。 另一种建议是在前后添加 gif，[例如在此拉取请求中](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896)。 我们建议使用 [ScreenToGif](https://www.screentogif.com/) 工具来从屏幕捕获中生成 gif。
