---
title: 参与说明
description: 了解有关参与 Windows Mixed Reality 爱好者指南的基本步骤和指导原则。 我们非常感谢你的反馈、编辑、添加和帮助。
author: mattwojo
ms.author: mattwoj
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality，Mixed reality，虚拟现实，VR，先生，反馈，反馈中心，bug
appliesto:
- Windows 10
ms.openlocfilehash: fd47e806a1ac14d85f503d7d4f799b232cbd3e102c3d4494d5704082bf0e08ea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188102"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a>对混合现实发烧指南进行贡献

感谢您对爱好者指南的兴趣。 我们非常感谢你的反馈、编辑、添加和改进文档的帮助。此页介绍了用于参与的基本步骤和指导原则。

> [!IMPORTANT]
> 发布到 docs.microsoft.com 的所有存储库均遵循 [Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。 有关详细信息，请参阅[行为准则常见问题](https://opensource.microsoft.com/codeofconduct/faq/)；若有任何问题或意见，请联系 [opencode@microsoft.com](mailto:opencode@microsoft.com)。<br>
>
> [docs.microsoft.com 使用条款](/legal/termsofuse)适用于对公共存储库中文档和代码示例所做的小修订和澄清。 如果你不是 Microsoft 的员工，那么新更改或重大更改会在拉取请求中发送一条注释，要求提交一份在线供稿许可协议 (CLA)。 在我们接受提取请求之前，需要你填写这份在线表单。

## <a name="before-you-start"></a>开始之前

如果还没有帐户，则需要[创建一个 GitHub 帐户](https://github.com/join)。

>[!NOTE]
>如果你是 microsoft 员工，请将你的 GitHub 帐户链接到[microsoft 开源门户](https://repos.opensource.microsoft.com/)上的 microsoft 别名。 加入 **"Microsoft"** 和 **"MicrosoftDocs"** 组织。

设置 GitHub 帐户时，我们还建议采用以下安全预防措施：
- [为 Github 帐户创建强密码](https://github.com/settings/admin)。
- 启用 [双因素身份验证](https://github.com/settings/two_factor_authentication/configure)。
- 将 [恢复代码](https://github.com/settings/auth/recovery-codes) 保存在安全的位置。
- 更新 [公用配置文件设置](https://github.com/settings/profile)。
   - 设置你的名称，并考虑将你的 *公用电子邮件* 设置为 *不显示我的电子邮件地址*。
   - 建议你上载个人资料图片，因为你所涉及的文档页面上会显示缩略图。
- 如果计划使用命令行，请考虑[为 Windows 设置 Git 凭据管理器](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)。 这样，每次发布时都无需输入密码。

发布系统与 GitHub 相关联，因此这些步骤非常重要。 您将使用您的 GitHub 别名作为每个项目的作者或参与者列出。

## <a name="how-to-make-a-change"></a>如何进行更改

| 若要建议更改文档，请按以下步骤操作： | 屏幕截图 |
| :------------------- | :--------: |
| 1. 如果正在查看 Docs.microsoft.com 页面，请单击页面右上角的 " **编辑** " 按钮。  我们会将你重定向到 [GitHub 存储库](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide)中的相应 Markdown 源文件。 | ![编辑按钮](images/edit_button.jpg) |
| 2. 如果你还没有 GitHub 帐户，请单击右上角的 "**注册**"，并创建一个新帐户。 | ![注册按钮](images/signup-for-github-button.png)|
| 3. 在打开的相应 GitHub 页面上，单击 "编辑" (铅笔图标) "。 | ![铅笔按钮](images/pencil_button.jpg)|
| 4. 在 "编辑文件" 窗格中， [更新文件的元数据](#updating-metadata) ，并使用 Markdown 语言更改内容。  ([如何编写 markdown。](https://help.github.com/articles/basic-writing-and-formatting-syntax/)) | ![编辑文件](images/edit-in-github.png)|
| 5. 单击 "预览更改" 验证格式设置是否符合预期。 | ![预览更改](images/edit-in-github.png)|
| 6. 完成后，滚动到页面底部，然后单击 "建议文件更改"，会显示 "比较更改" 页，使您能够验证所做的更改。 然后单击 "创建拉取请求" 按钮提交所做的更改。 至此，已完成提交！ | ![建议更改](images/propose.jpg)|

 (通过拉取请求提交更改后) ，文档团队成员将对这些更改进行检查。 如果接受了你的请求，则会将更新发布到 [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](/windows/mixed-reality/enthusiast-guide) 。

* 仅限内部检查，你可以在中看到你所做的更改 [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) 。

### <a name="updating-metadata"></a>更新元数据

更新每个项目顶部的元数据：
   * **标题**：查看项目时浏览器选项卡中显示的页面标题。 页面标题用于 SEO 和编制索引，因此，除非必要，否则请不要更改标题，因为这在文档公开) 之前不太重要 (。
   * **说明**：编写文章内容的简短描述，这会提高 SEO 和发现。
   * **作者**：如果你是页面的主所有者，请在此处添加你的 GitHub 别名。
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
- `redirect_document_id` 指示是否要保留以前文件中的文档 ID。 默认为 `false`。 `true`如果要保留 `ms.documentid` 重定向的项目中的属性值，请使用。 如果保留文档 ID，数据（如页面视图和分级）将传输到目标文章。 如果重定向主要用于重命名，而不是指向仅涵盖一些相同内容的不同项目，则执行此操作。

如果添加重定向，请确保同时删除旧文件。

### <a name="creating-a-new-article"></a>创建新项目

使用以下工作流，通过 web 浏览器中的 GitHub 在文档存储库中 *创建新项目*：

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

[混合现实发烧 GitHub 存储库](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide)利用了两个主要的父分支： [Master](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master)，可以在[过渡站点](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)上查看此内容，[也可以在实时](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live)[站点](/windows/mixed-reality/enthusiast-guide)上查看内容。

进行发布时，请将拉取请求提交 (PR) 到 **主** 分支。 此分支可以在暂存站点上查看，应该只包含即将实时发布的稿件。 你还可以使用自己的唯一分支名称创建并提交分支，此分支名称可在暂存站点中选择和查看。  (仅允许内容管理员使用 **实时** 分支。 ) 

## <a name="markdown-basics"></a>Markdown 基础知识

以下资源将帮助你了解如何使用 Markdown 语言编辑文档：

- [Markdown 基本信息](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Markdown-a-a-glance 参考海报](images/MarkdownPoster.pdf)
- [用于编写 Markdown for docs.microsoft.com](/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>添加表

由于样式表 docs.microsoft.com，即使尝试内联 CSS，它们也不会具有边框或自定义样式。 它看起来会在短时间内正常工作，但最终平台会从表中去除样式。 因此，请提前规划并简化表。 [下面是一个使 Markdown 表变得简单的站点](https://www.tablesgenerator.com/markdown_tables)。

如果使用文档，Visual Studio Code的[Docs Markdown](/teamblog/docs-extension)扩展还使表生成变得Visual Studio Code ([请参阅](#using-visual-studio-code)) 编辑文档。

### <a name="adding-images"></a>添加图像

需要将图像上传到存储库的"mixed-reality-docs/images"文件夹，然后在文章中适当地引用它们。 图像将自动以全尺寸显示，这意味着大型图像将填满文章的整个宽度。 建议在上传图像之前预先调整图像大小。 建议的宽度介于 600 和 700 像素之间，但如果是密集屏幕截图或屏幕截图的一小部分，则应该放大或缩小。

>[!IMPORTANT]
>在合并之前，只能将图像上传到分支存储库。 因此，如果计划将图像添加到文章，则需要先使用[Visual Studio Code](#using-visual-studio-code)将图像添加到分叉的"images"文件夹，或者确保已完成 Web 浏览器中的以下操作：
>
>1. 为 MicrosoftDocs/混合现实存储库分叉。
>2. 编辑了分叉中的文章。
>3. 将文章中引用的图像上传到分叉中的"mixed-reality-docs/images"文件夹。
>4. 创建了一 **个拉取** 请求，用于将分支合并到 MicrosoftDocs/混合现实"master"分支中。
>
>若要了解如何设置自己的分叉存储库，请按照创建新 [文章 的说明操作](#creating-a-new-article)。

## <a name="previewing-your-work"></a>预览工作

通过 Web 浏览器GitHub预览时，可以选择页面顶部附近的"预览"选项卡，在提交之前预览工作。 

>[!NOTE]
>预览更改review.docs.microsoft.com 仅适用于 Microsoft 员工

Microsoft 员工：将贡献内容合并到"主"分支后，可以在 上公开之前查看内容 https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide?branch=master 。 使用左侧列中的目录查找文章。

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>在浏览器中编辑与使用桌面客户端进行编辑

在浏览器中编辑是进行快速更改的最简单方法，但存在一些缺点：

- 不会进行拼写检查。
- 如果必须手动键入文章的文件名， (无法智能链接到其他) 。
- 上传和引用图像可能很麻烦。

如果愿意不解决这些问题，请使用桌面客户端（如[Visual Studio Code在参与](https://code.visualstudio.com/)时[提供一些](#useful-extensions)有用的扩展。

## <a name="using-visual-studio-code"></a>使用 Visual Studio Code

出于 [上述原因，](#editing-in-the-browser-vs-editing-with-a-desktop-client)你可能更喜欢使用桌面客户端来编辑文档，而不是 Web 浏览器。 建议使用[ Visual Studio Code](https://code.visualstudio.com/)。

### <a name="setup"></a>设置

按照以下步骤配置Visual Studio Code存储库：

1. 在 Web 浏览器中：
    1. 为[电脑安装 Git。](https://git-scm.com/downloads)
    2. 安装 [Visual Studio Code](https://code.visualstudio.com/)。
    3. [为 MicrosoftDocs/mixed-reality](#creating-a-new-article) 创建分叉（如果尚未创建）。
    4. 在分叉中，选择" **克隆或下载** 并复制 URL"。
2. 在 Visual Studio Code 中创建分叉的本地Visual Studio Code：
    1. 在"视图 **"菜单中**，选择"**命令面板"。**
    2. 键入"Git： Clone"。
    3. 粘贴复制的 URL。
    4. 选择在电脑上保存克隆的地方。
    5. 在 **弹出窗口中选择** "打开存储库"。

### <a name="editing-documentation"></a>编辑文档

使用以下工作流对文档进行更改，并Visual Studio Code：

>[!NOTE]
>上述有关[编辑和创建](#how-to-make-a-change)文章的所有[](#creating-a-new-article)指南以及编辑[Markdown](#markdown-basics)的基础知识也适用于使用 Visual Studio Code。

1. 使用官方存储库确保克隆的分叉是最新的。
   1. 在 Web 浏览器中，创建拉取请求，将 MicrosoftDocs/混合现实"master"中其他参与者的最新更改同步到分叉 (确保箭头指向正确的) 。
      
      ![将更改从 MicrosoftDocs/mixed-reality 同步到分叉](images/sync_repos.PNG)
   2. 在Visual Studio Code"中，选择"同步"按钮，将新更新的分叉同步到本地克隆。
      
      ![单击同步按钮图像](images/sync_clone.png)
2. 使用 Visual Studio Code 在克隆的存储库创建或编辑Visual Studio Code。
   1. 根据需要编辑一个或多个 (图像添加到"images"文件夹) 。
   2. **在** 资源管理器 中 **保存更改**。
      
      ![在资源管理器中选择"全部保存"](images/explorer_save.png)
   3. **在源代码管理** 中 **提交所有 (** 在系统提示时写入提交) 。
      
      ![在源代码管理中选择"全部提交"](images/source_control_commit.png)
   4. 选择同步 **按钮**，将更改同步回源 (上的分叉GitHub) 。
      
      ![单击同步按钮](images/sync_back.png)
3. 在 Web 浏览器中，创建拉取请求，将分叉中的新更改同步回 MicrosoftDocs/混合现实"master" (确保箭头指向正确的) 。

   ![创建从分叉到 MicrosoftDocs/mixed-reality 的拉取请求](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>有用的扩展

编辑Visual Studio Code时，以下扩展非常有用：

- [Docs Markdown 扩展Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - 使用 **Alt+M** 打开文档创作选项的菜单，例如：
   - 搜索和引用已上传的图像。
   - 添加格式设置，如列表、表和文档特定的调用（如 `>[!NOTE]` ）。
   - 搜索和引用内部链接和书签 (链接到页面中特定部分) 。
   - 格式设置错误突出显示 (将鼠标悬停在错误上方，了解) 。
- [代码拼写检查器](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - 拼写错误的单词将带有下划线;右键单击拼写错误的单词以将其更改或保存到字典中。

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a>使用问题提供有关Windows Mixed Reality指南的反馈

若要提供反馈或指出问题，而不是直接修改实际的文档页，请创建问题，[](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues)内容所有者将尽力及时解决问题。

如果要创建与特定页面有关的问题，请务必包含主题标题和 URL。

感谢你支持此内容！