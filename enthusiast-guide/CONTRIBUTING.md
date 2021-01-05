---
title: 参与说明
description: 了解适用于 Windows Mixed Reality 爱好者 Guide 的基本步骤和指导原则。 我们非常感谢你的反馈、编辑、添加和帮助。
author: mattwojo
ms.author: mattwoj
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，反馈，反馈中心，bug
appliesto:
- Windows 10
ms.openlocfilehash: afb559937c2bde06d3c74c1c572aefec50502884
ms.sourcegitcommit: 9a93c9e9b3b088da942ac4386813ecf263c2e324
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865432"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a>对混合现实发烧指南进行贡献

感谢您对爱好者指南的兴趣。 我们非常感谢你的反馈、编辑、添加和改进文档的帮助。此页介绍了用于参与的基本步骤和指导原则。

> [!IMPORTANT]
> 发布到 docs.microsoft.com 的所有存储库均遵循 [Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。 有关详细信息，请参阅[行为准则常见问题](https://opensource.microsoft.com/codeofconduct/faq/)；若有任何问题或意见，请联系 [opencode@microsoft.com](mailto:opencode@microsoft.com)。<br>
>
> [docs.microsoft.com 使用条款](https://docs.microsoft.com/legal/termsofuse)适用于对公共存储库中文档和代码示例所做的小修订和澄清。 如果你不是 Microsoft 的员工，那么新更改或重大更改会在拉取请求中发送一条注释，要求提交一份在线供稿许可协议 (CLA)。 在我们接受提取请求之前，需要你填写这份在线表单。

## <a name="before-you-start"></a>准备工作

如果还没有，则需要 [创建一个 GitHub 帐户](https://github.com/join)。

>[!NOTE]
>如果你是 Microsoft 员工，请将你的 GitHub 帐户链接到 [Microsoft 开源门户](https://repos.opensource.microsoft.com/)上的 microsoft 别名。 加入 **"Microsoft"** 和 **"MicrosoftDocs"** 组织。

设置 GitHub 帐户时，我们还建议采用以下安全预防措施：
- [为 Github 帐户创建强密码](https://github.com/settings/admin)。
- 启用 [双因素身份验证](https://github.com/settings/two_factor_authentication/configure)。
- 将 [恢复代码](https://github.com/settings/auth/recovery-codes) 保存在安全的位置。
- 更新 [公用配置文件设置](https://github.com/settings/profile)。
   - 设置你的名称，并考虑将你的 *公用电子邮件* 设置为 *不显示我的电子邮件地址*。
   - 建议你上载个人资料图片，因为你所涉及的文档页面上会显示缩略图。
- 如果计划使用命令行，请考虑设置 [适用于 Windows 的 Git 凭据管理器](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)。 这样，每次发布时都无需输入密码。

发布系统与 GitHub 相关联，因此这些步骤非常重要。 将使用 GitHub 别名作为每个项目的作者或参与者列出。

## <a name="how-to-make-a-change"></a>如何进行更改

| 若要建议更改文档，请按以下步骤操作： | 屏幕截图 |
| :------------------- | :--------: |
| 1. 如果正在查看 Docs.microsoft.com 页面，请单击页面右上角的 " **编辑** " 按钮。  我们会将你重定向到 [GitHub 存储库](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide)中的相应 Markdown 源文件。 | ![编辑按钮](images/edit_button.jpg) |
| 2. 如果你还没有 GitHub 帐户，请单击右上角的 " **注册** "，并创建一个新帐户。 | ![注册按钮](images/signup-for-github-button.png)|
| 3. 在打开的对应 GitHub 页上，单击 "编辑" (铅笔图标) 。 | ![铅笔按钮](images/pencil_button.jpg)|
| 4. 在 "编辑文件" 窗格中， [更新文件的元数据](#updating-metadata) ，并使用 Markdown 语言更改内容。  ([如何编写 markdown。](https://help.github.com/articles/basic-writing-and-formatting-syntax/)) | ![编辑文件](images/edit-in-github.png)|
| 5. 单击 "预览更改" 验证格式设置是否符合预期。 | ![预览更改](images/edit-in-github.png)|
| 6. 完成后，滚动到页面底部，然后单击 "建议文件更改"，会显示 "比较更改" 页，使您能够验证所做的更改。 然后单击 "创建拉取请求" 按钮提交所做的更改。 至此，已完成提交！ | ![建议更改](images/propose.jpg)|

 (通过拉取请求提交更改后) ，文档团队成员将对这些更改进行检查。 如果接受了你的请求，则会将更新发布到 [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide) 。

* 仅限内部检查，你可以在中看到你所做的更改 [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) 。

### <a name="updating-metadata"></a>更新元数据

更新每个项目顶部的元数据：
   * **标题**：查看项目时浏览器选项卡中显示的页面标题。 页面标题用于 SEO 和编制索引，因此，除非必要，否则请不要更改标题，因为这在文档公开) 之前不太重要 (。
   * **说明**：编写文章内容的简短描述，这会提高 SEO 和发现。
   * **作者**：如果你是页面的主要所有者，请在此处添加你的 GitHub 别名。
   * **女士**：如果你是页面的主要所有者，请在此处添加你的 Microsoft 别名 (你不需要 @microsoft.com ，只是别名) 。
   * " **ms**"：如果向页面中添加主要内容，则更新日期，但不将其用于修补，如说明、格式、语法或拼写。
   * **关键字**： SEO 中的关键字帮助 (搜索引擎优化) 。 添加特定于您的项目的关键字，并用逗号和空格分隔，但列表中最后一个关键字之后没有标点。 无需添加适用于所有项目的全局关键字，因为在其他位置托管这些项目。 

### <a name="renaming-or-deleting-an-existing-article"></a>重命名或删除现有项目

如果更改将重命名或删除现有项目，请确保添加一个重定向。 这样一来，具有现有文章的链接的任何人仍将在正确的位置结束。 重定向由存储库根目录中的文件 .openpublishing.redirection.js管理。

若要将重定向添加到中的 .openpublishing.redirection.js，请将条目添加到 `redirections` 数组中：

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/enthusiast-guide/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- `source_path`是要删除的旧项目的相对存储库路径。 请确保路径以开头 `mixed-reality-docs/enthusiast-guide` ，并以结尾 `.md` 。
- `redirect_url`是从旧文章到新文章的相对公共 URL。 请确保此 URL **不** 包含 `mixed-reality-docs/enthusiast-guide` 或 `.md` ，因为它引用的是公共 URL，而不是存储库路径。 允许使用链接到新项目中的部分 `#section` 。 如果需要，还可以在此处使用其他站点的绝对路径。
- `redirect_document_id` 指示是否要保留以前文件中的文档 ID。 默认值为 `false`。 `true`如果要保留 `ms.documentid` 重定向的项目中的属性值，请使用。 如果保留文档 ID，数据（如页面视图和分级）将传输到目标文章。 如果重定向主要用于重命名，而不是指向仅涵盖一些相同内容的不同项目的指针，则执行此操作。

如果添加重定向，请确保同时删除旧文件。

### <a name="creating-a-new-article"></a>创建新项目

使用以下工作流在 web 浏览器中通过 GitHub 在文档存储库中 *创建新项目* ：

1. 使用右上方) 中的 " **分叉** " 按钮，创建 MicrosoftDocs/mixed reality/tree/文档/发烧指南 "master" 分支 (的分叉。

   ![将主分支分叉。](images/forkbranch.png)
2. 在 "mixed reality/发烧指南" 文件夹中，选择右上方的 " **新建文件** "。
3. 为项目创建页面名称， (使用连字符而不是空格，并且不要使用标点或撇号) 并追加 "md"

   ![命名新页。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >请确保在 "混合现实文档/发烧友" 文件夹中创建新项目。 可以通过在 "新文件名" 行中检查 "/mixed-reality-docs/enthusiast-guide" 来确认这一点。

4. 在新页的顶部，添加以下元数据块：

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. 按照 [以上部分](#updating-metadata)中的说明填写相关的元数据字段。
6. 使用 [Markdown 基础知识](#markdown-basics)编写文章内容。
7. 在 `## See also` 文章底部添加一个部分，其中包含指向其他相关文章的链接。
8. 完成后，选择 " **提交新文件**"。
9. 选择 " **新建拉取请求** "，并将分支的 "master" 分支合并到 MicrosoftDocs/mixed reality/发烧指南 "master" (确保箭头指向) 正确的方式。

   ![创建从分叉到 MicrosoftDocs/混合现实/发烧](images/pr_to_master.PNG)

## <a name="working-with-branches"></a>使用分支

[混合现实发烧友 GitHub 存储库](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide)利用了两个主要的父分支： [Master](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master)，可在[暂存站点](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)上查看此内容[，并在实时](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live)[站点](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide)上查看内容。

进行发布时，请将拉取请求提交 (PR) 到 **主** 分支。 此分支可以在暂存站点上查看，应该只包含即将实时发布的稿件。 你还可以使用自己的唯一分支名称创建并提交分支，此分支名称可在暂存站点中选择和查看。  (仅允许内容管理员使用 **实时** 分支。 ) 

## <a name="markdown-basics"></a>Markdown 基础知识

以下资源将帮助你了解如何使用 Markdown 语言编辑文档：

- [Markdown 基本信息](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [一览式参考海报 Markdown](images/MarkdownPoster.pdf)
- [用于编写 docs.microsoft.com 的 Markdown 的其他资源](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>添加表

由于 docs.microsoft.com 样式表的方式，它们没有边框或自定义样式，即使您尝试使用内联 CSS 也是如此。 它看起来可以正常工作，但最终平台会去除表的样式。 因此请提前规划并使表保持简单。 [下面是使 Markdown 表变得简单的站点](https://www.tablesgenerator.com/markdown_tables)。

如果你使用[Visual Studio Code (请参阅) 下面](#using-visual-studio-code)的 "Markdown" 文档中的 "[文档" Visual Studio Code 扩展](https://docs.microsoft.com/teamblog/docs-extension)，以编辑该文档。

### <a name="adding-images"></a>添加图像

需要将映像上传到存储库中的 "混合现实文档/映像" 文件夹，并在文章中对它们进行相应的引用。 图像将自动以全尺寸显示，这意味着大型图像将填充整个文章的宽度。 建议在上传映像之前对其进行预先调整大小。 建议宽度介于600到700像素之间，不过，如果它是密集屏幕截图或屏幕截图的小部分，则应调整大小。

>[!IMPORTANT]
>在合并前，只能将图像上传到分叉存储库。 因此，如果你计划将图像添加到项目中，则需要先 [使用 Visual Studio Code](#using-visual-studio-code) 将图像添加到分叉的 "images" 文件夹，或者确保已在 web 浏览器中完成以下操作：
>
>1. 分叉 MicrosoftDocs/mixed reality 存储库。
>2. 已编辑分叉中的项目。
>3. 将你在项目中引用的映像上传到你的分支中的 "混合现实文档/映像" 文件夹。
>4. 创建了用于将分叉合并到 MicrosoftDocs/mixed reality "master" 分支的 **拉取请求** 。
>
>若要了解如何设置自己的分叉存储库，请按照 [创建新文章](#creating-a-new-article)的说明进行操作。

## <a name="previewing-your-work"></a>预览工作

通过 web 浏览器在 GitHub 中进行编辑时，可以选择页面顶部附近的 " **预览** " 选项卡来预览你的工作，然后再提交。 

>[!NOTE]
>review.docs.microsoft.com 上预览所做的更改仅适用于 Microsoft 员工

Microsoft 员工：将你的贡献合并到 "master" 分支后，你可以在内容公开之前查看内容 https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide?branch=master 。 使用左栏中的目录查找文章。

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>在浏览器中编辑与使用桌面客户端进行编辑

在浏览器中进行编辑是进行快速更改的最简单方法，但有几个缺点：

- 不会进行拼写检查。
- 您不会获得任何智能链接到其他文章 (您必须手动键入文章的文件名) 。
- 这可能是上传和引用图像的麻烦。

如果你不想处理这些问题，请使用类似于 [Visual Studio Code](https://code.visualstudio.com/) 的桌面客户端，并在参与时使用几个 [有用的扩展](#useful-extensions) 。

## <a name="using-visual-studio-code"></a>使用 Visual Studio Code

出于 [上面](#editing-in-the-browser-vs-editing-with-a-desktop-client)列出的原因，您可能更倾向于使用桌面客户端编辑文档而不是 web 浏览器。 建议使用 [Visual Studio Code](https://code.visualstudio.com/)。

### <a name="setup"></a>设置

请按照以下步骤配置 Visual Studio Code 以使用此存储库：

1. 在 web 浏览器中：
    1. 安装 [适用于你的电脑的 Git](https://git-scm.com/downloads)。
    2. 安装 [Visual Studio Code](https://code.visualstudio.com/)。
    3. [分叉 MicrosoftDocs/混合现实（](#creating-a-new-article) 如果尚未这样做）。
    4. 在分支中，选择 " **克隆" 或 "下载** 并复制 URL"。
2. 在 Visual Studio Code 中创建分叉的本地复本：
    1. 从 " **视图** " 菜单中选择 " **命令面板**"。
    2. 键入 "Git： Clone"。
    3. 粘贴复制的 URL。
    4. 选择要在电脑上保存克隆的位置。
    5. 在弹出窗口中选择 " **打开** 存储库"。

### <a name="editing-documentation"></a>编辑文档

使用以下工作流，通过 Visual Studio Code 对文档进行更改：

>[!NOTE]
>在使用 Visual Studio Code 时，所有有关 [编辑](#how-to-make-a-change) 和 [创建](#creating-a-new-article) 文章的指南以及 [编辑 Markdown 的基础知识](#markdown-basics)也适用。

1. 请确保你的克隆分叉与官方存储库保持最新。
   1. 在 web 浏览器中，创建一个拉取请求，将 MicrosoftDocs/mixed reality "master" 中其他参与者的最近更改同步到分叉 (确保箭头指向) 正确的方式。
      
      ![将更改从 MicrosoftDocs/混合事实同步到你的分支](images/sync_repos.PNG)
   2. 在 Visual Studio Code 中，选择 "同步" 按钮，将最新更新的分支同步到本地克隆。
      
      ![单击 "同步" 按钮图像](images/sync_clone.png)
2. 使用 Visual Studio Code 在克隆的存储库中创建或编辑项目。
   1. 编辑一个或多个项目 (如有必要，将图像添加到 "images" 文件夹) 。
   2. 在 **资源管理器** 中 **保存** 更改。
      
      ![在资源管理器中选择 "全部保存"](images/explorer_save.png)
   3. ) 提示时，提交 **源代码管理** 中的 **所有** 更改 (写入提交消息。
      
      ![在源代码管理中选择 "全部提交"](images/source_control_commit.png)
   4. 选择 " **同步** " 按钮，将所做的更改同步回 GitHub 上的源 (分叉) 上。
      
      ![单击 "同步" 按钮](images/sync_back.png)
3. 在 web 浏览器中，创建一个拉取请求，将分支中的新更改同步回 MicrosoftDocs/mixed reality "master" (确保箭头指向) 正确的方式。

   ![创建从分叉到 MicrosoftDocs/混合现实的拉取请求](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>有用的扩展

编辑文档时，以下 Visual Studio Code 扩展很有用：

- [用于 Visual Studio Code 的文档 Markdown 扩展](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -使用 **Alt + M** 显示文档创作选项的菜单，如下所示：
   - 搜索和引用已上传的映像。
   - 添加格式（如列表、表和文档） `>[!NOTE]` 。
   - 搜索和引用内部链接和书签 (指向) 页面内特定部分的链接。
   - 突出显示格式错误 (将鼠标悬停在错误上以了解详细) 。
- [代码拼写检查器](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -将为拼写错误的单词加下划线。右键单击拼写错误的单词以对其进行更改或将其保存到字典中。

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a>使用问题提供有关 Windows Mixed Reality 爱好者 Guide 的反馈

若要提供反馈或指出问题，而不是直接修改实际的文档页，请 [创建一个问题](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) ，内容所有者将尽力及时解决该问题。

如果要创建与特定页面有关的问题，请确保包含主题标题和 URL。

感谢你支持此内容！
