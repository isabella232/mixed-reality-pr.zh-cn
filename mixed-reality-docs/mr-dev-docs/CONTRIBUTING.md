---
title: 参与说明
description: 了解如何使用 GitHub-风格 Markdown 在 docs.microsoft.com 平台上参与混合现实开发人员文档。
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: dd84ba86af0b86b29510c4c317ad0a14fabc296b
ms.sourcegitcommit: 3762d207d3b5f4a1d932197aae7a4fae4baec960
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/18/2020
ms.locfileid: "97676196"
---
# <a name="contributing-to-mixed-reality-developer-documentation"></a><span data-ttu-id="21d1b-103">对混合现实开发人员文档进行贡献</span><span class="sxs-lookup"><span data-stu-id="21d1b-103">Contributing to Mixed Reality developer documentation</span></span>

<span data-ttu-id="21d1b-104">欢迎使用 [适用于混合现实开发人员文档的公共](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)存储库！</span><span class="sxs-lookup"><span data-stu-id="21d1b-104">Welcome to the [public repo for Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="21d1b-105">在此存储库中创建或编辑的任何项目 **都将对公共可见。**</span><span class="sxs-lookup"><span data-stu-id="21d1b-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="21d1b-106">混合现实文档现在位于 docs.microsoft.com 平台上，后者使用 GitHub 风格 Markdown 和 Markdig 功能。</span><span class="sxs-lookup"><span data-stu-id="21d1b-106">The Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown with Markdig features.</span></span> <span data-ttu-id="21d1b-107">在此存储库中编辑的内容将格式化为显示在中的样式页面 https://docs.microsoft.com/windows/mixed-reality 。</span><span class="sxs-lookup"><span data-stu-id="21d1b-107">The content you edit in this repo gets formatted into stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> <span data-ttu-id="21d1b-108">若要参与 HoloLens 或 VR 发烧文档，请访问其各自的 [hololens](https://github.com/MicrosoftDocs/Hololens) 和 [vr](https://github.com/MicrosoftDocs/mixed-reality/tree/docs/enthusiast-guide) 存储库。</span><span class="sxs-lookup"><span data-stu-id="21d1b-108">If you want to contribute to HoloLens or VR enthusiast documentation, visit their respective [HoloLens](https://github.com/MicrosoftDocs/Hololens) and [VR](https://github.com/MicrosoftDocs/mixed-reality/tree/docs/enthusiast-guide) repositories.</span></span>

<span data-ttu-id="21d1b-109">此页介绍了用于贡献和链接到 Markdown 基础知识的基本步骤和指导原则。</span><span class="sxs-lookup"><span data-stu-id="21d1b-109">This page covers the basic steps and guidelines for contributing and links to Markdown basics.</span></span> <span data-ttu-id="21d1b-110">感谢你的发布内容！</span><span class="sxs-lookup"><span data-stu-id="21d1b-110">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="21d1b-111">准备工作</span><span class="sxs-lookup"><span data-stu-id="21d1b-111">Before you start</span></span>

<span data-ttu-id="21d1b-112">如果还没有，则需要 [创建一个 GitHub 帐户](https://github.com/join)。</span><span class="sxs-lookup"><span data-stu-id="21d1b-112">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="21d1b-113">如果你是 Microsoft 员工，请将你的 GitHub 帐户链接到 [Microsoft 开源门户](https://repos.opensource.microsoft.com/)上的 microsoft 别名。</span><span class="sxs-lookup"><span data-stu-id="21d1b-113">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="21d1b-114">加入 **"Microsoft"** 和 **"MicrosoftDocs"** 组织。</span><span class="sxs-lookup"><span data-stu-id="21d1b-114">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations.</span></span>

<span data-ttu-id="21d1b-115">设置 GitHub 帐户时，我们还建议采用以下安全预防措施：</span><span class="sxs-lookup"><span data-stu-id="21d1b-115">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="21d1b-116">[为 Github 帐户创建强密码](https://github.com/settings/admin)。</span><span class="sxs-lookup"><span data-stu-id="21d1b-116">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="21d1b-117">启用 [双因素身份验证](https://github.com/settings/two_factor_authentication/configure)。</span><span class="sxs-lookup"><span data-stu-id="21d1b-117">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="21d1b-118">将 [恢复代码](https://github.com/settings/auth/recovery-codes) 保存在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="21d1b-118">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="21d1b-119">更新 [公用配置文件设置](https://github.com/settings/profile)。</span><span class="sxs-lookup"><span data-stu-id="21d1b-119">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="21d1b-120">设置你的名称，并考虑将你的 *公用电子邮件* 设置为 *不显示我的电子邮件地址*。</span><span class="sxs-lookup"><span data-stu-id="21d1b-120">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="21d1b-121">建议你上载个人资料图片，因为你所涉及的文档页面上会显示缩略图。</span><span class="sxs-lookup"><span data-stu-id="21d1b-121">We recommend you upload a profile picture because a thumbnail is shown on docs pages you contribute to.</span></span>
- <span data-ttu-id="21d1b-122">如果计划使用命令行，请考虑设置 [适用于 Windows 的 Git 凭据管理器](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest)。</span><span class="sxs-lookup"><span data-stu-id="21d1b-122">If you plan to use the command line, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest).</span></span> <span data-ttu-id="21d1b-123">这样，每次发布时都无需输入密码。</span><span class="sxs-lookup"><span data-stu-id="21d1b-123">That way, you won't have to enter your password every time you make a contribution.</span></span>

<span data-ttu-id="21d1b-124">发布系统与 GitHub 相关联，因此这些步骤非常重要。</span><span class="sxs-lookup"><span data-stu-id="21d1b-124">The publishing system is tied to GitHub, so these steps are important.</span></span> <span data-ttu-id="21d1b-125">将使用 GitHub 别名作为每个项目的作者或参与者列出。</span><span class="sxs-lookup"><span data-stu-id="21d1b-125">You'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="21d1b-126">编辑现有项目</span><span class="sxs-lookup"><span data-stu-id="21d1b-126">Editing an existing article</span></span>

<span data-ttu-id="21d1b-127">使用以下工作流，在 web 浏览器中通过 GitHub 对 *现有文章* 进行更新：</span><span class="sxs-lookup"><span data-stu-id="21d1b-127">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="21d1b-128">导航到要在 "混合现实-文档" 文件夹中编辑的项目。</span><span class="sxs-lookup"><span data-stu-id="21d1b-128">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="21d1b-129">选择右上方的 "编辑" 按钮 (铅笔图标) ，它将自动从 "master" 分支中派生出可释放分支。</span><span class="sxs-lookup"><span data-stu-id="21d1b-129">Select the edit button (pencil icon) in the top right, which will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![编辑项目。](images/editpage.png)
3. <span data-ttu-id="21d1b-131">根据 ["Markdown 基础知识"](#markdown-basics)编辑项目内容。</span><span class="sxs-lookup"><span data-stu-id="21d1b-131">Edit the content of the article according to the ["Markdown basics"](#markdown-basics).</span></span>
4. <span data-ttu-id="21d1b-132">更新每个项目顶部的元数据：</span><span class="sxs-lookup"><span data-stu-id="21d1b-132">Update metadata at the top of each article:</span></span>
   * <span data-ttu-id="21d1b-133">标题：查看项目时浏览器选项卡中显示的页面标题。</span><span class="sxs-lookup"><span data-stu-id="21d1b-133">title: Page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="21d1b-134">页面标题用于 SEO 和编制索引，因此，除非必要，否则请不要更改标题，因为这在文档公开) 之前不太重要 (。</span><span class="sxs-lookup"><span data-stu-id="21d1b-134">Page titles are used for SEO and indexing, so don't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="21d1b-135">说明：编写文章内容的简短描述，这会提高 SEO 和发现。</span><span class="sxs-lookup"><span data-stu-id="21d1b-135">description: Write a brief description of the article's content, which boosts SEO and discovery.</span></span>
   * <span data-ttu-id="21d1b-136">作者：如果你是页面的主要所有者，请在此处添加你的 GitHub 别名。</span><span class="sxs-lookup"><span data-stu-id="21d1b-136">author: If you're the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="21d1b-137">女士：如果你是页面的主要所有者，请在此处添加你的 Microsoft 别名 (你不需要 @microsoft.com ，只是别名) 。</span><span class="sxs-lookup"><span data-stu-id="21d1b-137">ms.author: If you're the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="21d1b-138">"ms"：如果向页面中添加主要内容，则更新日期，但不将其用于修补，如说明、格式、语法或拼写。</span><span class="sxs-lookup"><span data-stu-id="21d1b-138">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="21d1b-139">关键字： SEO 中的关键字帮助 (搜索引擎优化) 。</span><span class="sxs-lookup"><span data-stu-id="21d1b-139">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="21d1b-140">添加特定于您的项目的关键字，并用逗号和空格分隔，但列表中最后一个关键字之后没有标点。</span><span class="sxs-lookup"><span data-stu-id="21d1b-140">Add keywords, separated by a comma and a space, that are specific to your article, but no punctuation after the last keyword in your list.</span></span> <span data-ttu-id="21d1b-141">无需添加适用于所有项目的全局关键字，因为在其他位置托管这些项目。</span><span class="sxs-lookup"><span data-stu-id="21d1b-141">You don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="21d1b-142">完成文章编辑后，向下滚动并选择 " **建议文件更改**"。</span><span class="sxs-lookup"><span data-stu-id="21d1b-142">When you've completed your article edits, scroll down and select **Propose file change**.</span></span>
6. <span data-ttu-id="21d1b-143">在下一页上，选择 " **创建拉取请求** " 将自动创建的分支合并到 "master"。</span><span class="sxs-lookup"><span data-stu-id="21d1b-143">On the next page, select **Create pull request** to merge your automatically created branch into 'master.'</span></span>
7. <span data-ttu-id="21d1b-144">对于要编辑的下一篇文章，请重复上述步骤。</span><span class="sxs-lookup"><span data-stu-id="21d1b-144">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="renaming-or-deleting-an-existing-article"></a><span data-ttu-id="21d1b-145">重命名或删除现有项目</span><span class="sxs-lookup"><span data-stu-id="21d1b-145">Renaming or deleting an existing article</span></span>

<span data-ttu-id="21d1b-146">如果更改将重命名或删除现有项目，请确保添加一个重定向。</span><span class="sxs-lookup"><span data-stu-id="21d1b-146">If your change will rename or delete an existing article, be sure to add a redirect.</span></span> <span data-ttu-id="21d1b-147">这样一来，具有现有文章的链接的任何人仍将在正确的位置结束。</span><span class="sxs-lookup"><span data-stu-id="21d1b-147">That way, anyone with a link to the existing article will still end up in the right place.</span></span> <span data-ttu-id="21d1b-148">重定向由存储库根目录中的文件 .openpublishing.redirection.js管理。</span><span class="sxs-lookup"><span data-stu-id="21d1b-148">Redirects are managed by the .openpublishing.redirection.json file in the root of the repo.</span></span>

<span data-ttu-id="21d1b-149">若要将重定向添加到中的 .openpublishing.redirection.js，请将条目添加到 `redirections` 数组中：</span><span class="sxs-lookup"><span data-stu-id="21d1b-149">To add a redirect to .openpublishing.redirection.json, add an entry to the `redirections` array:</span></span>

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- <span data-ttu-id="21d1b-150">`source_path`是要删除的旧项目的相对存储库路径。</span><span class="sxs-lookup"><span data-stu-id="21d1b-150">The `source_path` is the relative repository path to the old article that you're removing.</span></span> <span data-ttu-id="21d1b-151">请确保路径以开头 `mixed-reality-docs` ，并以结尾 `.md` 。</span><span class="sxs-lookup"><span data-stu-id="21d1b-151">Be sure the path starts with `mixed-reality-docs` and ends with `.md`.</span></span>
- <span data-ttu-id="21d1b-152">`redirect_url`是从旧文章到新文章的相对公共 URL。</span><span class="sxs-lookup"><span data-stu-id="21d1b-152">The `redirect_url` is the relative public URL from the old article to the new article.</span></span> <span data-ttu-id="21d1b-153">请确保此 URL **不** 包含 `mixed-reality-docs` 或 `.md` ，因为它引用的是公共 URL，而不是存储库路径。</span><span class="sxs-lookup"><span data-stu-id="21d1b-153">Be sure that this URL **doesn't** contain `mixed-reality-docs` or `.md`, as it refers to the public URL and not the repository path.</span></span> <span data-ttu-id="21d1b-154">允许使用链接到新项目中的部分 `#section` 。</span><span class="sxs-lookup"><span data-stu-id="21d1b-154">Linking to a section within the new article using `#section` is allowed.</span></span> <span data-ttu-id="21d1b-155">如果需要，还可以在此处使用其他站点的绝对路径。</span><span class="sxs-lookup"><span data-stu-id="21d1b-155">You can also use an absolute path to another site here, if necessary.</span></span>
- <span data-ttu-id="21d1b-156">`redirect_document_id` 指示是否要保留以前文件中的文档 ID。</span><span class="sxs-lookup"><span data-stu-id="21d1b-156">`redirect_document_id` indicates whether you would like to keep the document ID from the previous file.</span></span> <span data-ttu-id="21d1b-157">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="21d1b-157">The default is `false`.</span></span> <span data-ttu-id="21d1b-158">`true`如果要保留 `ms.documentid` 重定向的项目中的属性值，请使用。</span><span class="sxs-lookup"><span data-stu-id="21d1b-158">Use `true` if you want to preserve the `ms.documentid` attribute value from the redirected article.</span></span> <span data-ttu-id="21d1b-159">如果保留文档 ID，数据（如页面视图和分级）将传输到目标文章。</span><span class="sxs-lookup"><span data-stu-id="21d1b-159">If you preserve the document ID, data, such as page views and rankings, will be transferred to the target article.</span></span> <span data-ttu-id="21d1b-160">如果重定向主要用于重命名，而不是指向仅涵盖一些相同内容的不同项目的指针，则执行此操作。</span><span class="sxs-lookup"><span data-stu-id="21d1b-160">Do this if the redirect is primarily a rename, and not a pointer to different article that only covers some of the same content.</span></span>

<span data-ttu-id="21d1b-161">如果添加重定向，请确保同时删除旧文件。</span><span class="sxs-lookup"><span data-stu-id="21d1b-161">If you add a redirect, be sure to delete the old file as well.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="21d1b-162">创建新项目</span><span class="sxs-lookup"><span data-stu-id="21d1b-162">Creating a new article</span></span>

<span data-ttu-id="21d1b-163">使用以下工作流在 web 浏览器中通过 GitHub 在文档存储库中 *创建新项目* ：</span><span class="sxs-lookup"><span data-stu-id="21d1b-163">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="21d1b-164">使用右上方) 中的 " **分叉** " 按钮，创建 MicrosoftDocs/mixed reality "master" 分支 (分叉。</span><span class="sxs-lookup"><span data-stu-id="21d1b-164">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![将主分支分叉。](images/forkbranch.png)
2. <span data-ttu-id="21d1b-166">在 "混合现实文档" 文件夹中，选择右上方的 " **新建文件** "。</span><span class="sxs-lookup"><span data-stu-id="21d1b-166">In the "mixed-reality-docs" folder, select **Create new file** in the top right.</span></span>
3. <span data-ttu-id="21d1b-167">为项目创建页面名称， (使用连字符而不是空格，并且不要使用标点或撇号) 并追加 "md"</span><span class="sxs-lookup"><span data-stu-id="21d1b-167">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![命名新页。](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="21d1b-169">请确保在 "mixed reality-文档" 文件夹中创建新项目。</span><span class="sxs-lookup"><span data-stu-id="21d1b-169">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="21d1b-170">可以通过在 "新文件名" 行中检查 "/mixed-reality-docs/" 来确认这一点。</span><span class="sxs-lookup"><span data-stu-id="21d1b-170">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="21d1b-171">在新页的顶部，添加以下元数据块：</span><span class="sxs-lookup"><span data-stu-id="21d1b-171">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="21d1b-172">按照 [以上部分](#editing-an-existing-article)中的说明填写相关的元数据字段。</span><span class="sxs-lookup"><span data-stu-id="21d1b-172">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="21d1b-173">使用 [Markdown 基础知识](#markdown-basics)编写文章内容。</span><span class="sxs-lookup"><span data-stu-id="21d1b-173">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="21d1b-174">在 `## See also` 文章底部添加一个部分，其中包含指向其他相关文章的链接。</span><span class="sxs-lookup"><span data-stu-id="21d1b-174">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="21d1b-175">完成后，选择 " **提交新文件**"。</span><span class="sxs-lookup"><span data-stu-id="21d1b-175">When finished, select **Commit new file**.</span></span>
9. <span data-ttu-id="21d1b-176">选择 " **新建拉取请求** "，并将分支的 "master" 分支合并到 MicrosoftDocs/mixed reality "master" (确保箭头指向正确的) 方法。</span><span class="sxs-lookup"><span data-stu-id="21d1b-176">Select **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![创建从分叉到 MicrosoftDocs/混合现实的拉取请求](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="21d1b-178">Markdown 基础知识</span><span class="sxs-lookup"><span data-stu-id="21d1b-178">Markdown basics</span></span>

<span data-ttu-id="21d1b-179">以下资源将帮助你了解如何使用 Markdown 语言编辑文档：</span><span class="sxs-lookup"><span data-stu-id="21d1b-179">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="21d1b-180">Markdown 基本信息</span><span class="sxs-lookup"><span data-stu-id="21d1b-180">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="21d1b-181">一览式参考海报 Markdown</span><span class="sxs-lookup"><span data-stu-id="21d1b-181">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="21d1b-182">用于编写 docs.microsoft.com 的 Markdown 的其他资源</span><span class="sxs-lookup"><span data-stu-id="21d1b-182">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="21d1b-183">添加表</span><span class="sxs-lookup"><span data-stu-id="21d1b-183">Adding tables</span></span>

<span data-ttu-id="21d1b-184">由于 docs.microsoft.com 样式表的方式，它们没有边框或自定义样式，即使您尝试使用内联 CSS 也是如此。</span><span class="sxs-lookup"><span data-stu-id="21d1b-184">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="21d1b-185">它看起来可以正常工作，但最终平台会去除表的样式。</span><span class="sxs-lookup"><span data-stu-id="21d1b-185">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="21d1b-186">因此请提前规划并使表保持简单。</span><span class="sxs-lookup"><span data-stu-id="21d1b-186">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="21d1b-187">[下面是使 Markdown 表变得简单的站点](https://www.tablesgenerator.com/markdown_tables)。</span><span class="sxs-lookup"><span data-stu-id="21d1b-187">[Here’s a site that makes Markdown tables easy](https://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="21d1b-188">如果你使用[Visual Studio Code (请参阅) 下面](#using-visual-studio-code)的 "Markdown" 文档中的 "[文档" Visual Studio Code 扩展](https://docs.microsoft.com/teamblog/docs-extension)，以编辑该文档。</span><span class="sxs-lookup"><span data-stu-id="21d1b-188">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="21d1b-189">添加图像</span><span class="sxs-lookup"><span data-stu-id="21d1b-189">Adding images</span></span>

<span data-ttu-id="21d1b-190">需要将映像上传到存储库中的 "混合现实文档/映像" 文件夹，并在文章中对它们进行相应的引用。</span><span class="sxs-lookup"><span data-stu-id="21d1b-190">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="21d1b-191">图像将自动以全尺寸显示，这意味着大型图像将填充整个文章的宽度。</span><span class="sxs-lookup"><span data-stu-id="21d1b-191">Images will automatically show up at full-size, which means large images will fill the entire width of the article.</span></span> <span data-ttu-id="21d1b-192">建议在上传映像之前对其进行预先调整大小。</span><span class="sxs-lookup"><span data-stu-id="21d1b-192">We recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="21d1b-193">建议宽度介于600到700像素之间，不过，如果它是密集屏幕截图或屏幕截图的小部分，则应调整大小。</span><span class="sxs-lookup"><span data-stu-id="21d1b-193">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="21d1b-194">在合并前，只能将图像上传到分叉存储库。</span><span class="sxs-lookup"><span data-stu-id="21d1b-194">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="21d1b-195">因此，如果你计划将图像添加到项目中，则需要先 [使用 Visual Studio Code](#using-visual-studio-code) 将图像添加到分叉的 "images" 文件夹，或者确保已在 web 浏览器中完成以下操作：</span><span class="sxs-lookup"><span data-stu-id="21d1b-195">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="21d1b-196">分叉 MicrosoftDocs/mixed reality 存储库。</span><span class="sxs-lookup"><span data-stu-id="21d1b-196">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="21d1b-197">已编辑分叉中的项目。</span><span class="sxs-lookup"><span data-stu-id="21d1b-197">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="21d1b-198">将你在项目中引用的映像上传到你的分支中的 "混合现实文档/映像" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="21d1b-198">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="21d1b-199">创建了用于将分叉合并到 MicrosoftDocs/mixed reality "master" 分支的 **拉取请求** 。</span><span class="sxs-lookup"><span data-stu-id="21d1b-199">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="21d1b-200">若要了解如何设置自己的分叉存储库，请按照 [创建新文章](#creating-a-new-article)的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="21d1b-200">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="21d1b-201">预览工作</span><span class="sxs-lookup"><span data-stu-id="21d1b-201">Previewing your work</span></span>

<span data-ttu-id="21d1b-202">通过 web 浏览器在 GitHub 中进行编辑时，可以选择页面顶部附近的 " **预览** " 选项卡来预览你的工作，然后再提交。</span><span class="sxs-lookup"><span data-stu-id="21d1b-202">While editing in GitHub via a web browser, you can select the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="21d1b-203">review.docs.microsoft.com 上预览所做的更改仅适用于 Microsoft 员工</span><span class="sxs-lookup"><span data-stu-id="21d1b-203">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="21d1b-204">Microsoft 员工：将你的贡献合并到 "master" 分支后，你可以在内容公开之前查看内容 https://review.docs.microsoft.com/windows/mixed-reality?branch=master 。</span><span class="sxs-lookup"><span data-stu-id="21d1b-204">Microsoft employees: once your contributions have been merged into the 'master' branch, you can review the content before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master.</span></span> <span data-ttu-id="21d1b-205">使用左栏中的目录查找文章。</span><span class="sxs-lookup"><span data-stu-id="21d1b-205">Find your article using the table of contents in the left column.</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="21d1b-206">在浏览器中编辑与使用桌面客户端进行编辑</span><span class="sxs-lookup"><span data-stu-id="21d1b-206">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="21d1b-207">在浏览器中进行编辑是进行快速更改的最简单方法，但有几个缺点：</span><span class="sxs-lookup"><span data-stu-id="21d1b-207">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="21d1b-208">不会进行拼写检查。</span><span class="sxs-lookup"><span data-stu-id="21d1b-208">You don't get spell-check.</span></span>
- <span data-ttu-id="21d1b-209">您不会获得任何智能链接到其他文章 (您必须手动键入文章的文件名) 。</span><span class="sxs-lookup"><span data-stu-id="21d1b-209">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="21d1b-210">这可能是上传和引用图像的麻烦。</span><span class="sxs-lookup"><span data-stu-id="21d1b-210">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="21d1b-211">如果你不想处理这些问题，请使用类似于 [Visual Studio Code](https://code.visualstudio.com/) 的桌面客户端，并在参与时使用几个 [有用的扩展](#useful-extensions) 。</span><span class="sxs-lookup"><span data-stu-id="21d1b-211">If you'd rather not deal with these issues, use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) when contributing.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="21d1b-212">使用 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="21d1b-212">Using Visual Studio Code</span></span>

<span data-ttu-id="21d1b-213">出于 [上面](#editing-in-the-browser-vs-editing-with-a-desktop-client)列出的原因，您可能更倾向于使用桌面客户端编辑文档而不是 web 浏览器。</span><span class="sxs-lookup"><span data-stu-id="21d1b-213">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="21d1b-214">建议使用 [Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="21d1b-214">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="21d1b-215">设置</span><span class="sxs-lookup"><span data-stu-id="21d1b-215">Setup</span></span>

<span data-ttu-id="21d1b-216">请按照以下步骤配置 Visual Studio Code 以使用此存储库：</span><span class="sxs-lookup"><span data-stu-id="21d1b-216">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="21d1b-217">在 web 浏览器中：</span><span class="sxs-lookup"><span data-stu-id="21d1b-217">In a web browser:</span></span>
    1. <span data-ttu-id="21d1b-218">安装 [适用于你的电脑的 Git](https://git-scm.com/downloads)。</span><span class="sxs-lookup"><span data-stu-id="21d1b-218">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="21d1b-219">安装 [Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="21d1b-219">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="21d1b-220">[分叉 MicrosoftDocs/混合现实（](#creating-a-new-article) 如果尚未这样做）。</span><span class="sxs-lookup"><span data-stu-id="21d1b-220">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="21d1b-221">在分支中，选择 " **克隆" 或 "下载** 并复制 URL"。</span><span class="sxs-lookup"><span data-stu-id="21d1b-221">In your fork, select **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="21d1b-222">在 Visual Studio Code 中创建分叉的本地复本：</span><span class="sxs-lookup"><span data-stu-id="21d1b-222">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="21d1b-223">从 " **视图** " 菜单中选择 " **命令面板**"。</span><span class="sxs-lookup"><span data-stu-id="21d1b-223">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="21d1b-224">键入 "Git： Clone"。</span><span class="sxs-lookup"><span data-stu-id="21d1b-224">Type "Git: Clone."</span></span>
    3. <span data-ttu-id="21d1b-225">粘贴复制的 URL。</span><span class="sxs-lookup"><span data-stu-id="21d1b-225">Paste the URL you copied.</span></span>
    4. <span data-ttu-id="21d1b-226">选择要在电脑上保存克隆的位置。</span><span class="sxs-lookup"><span data-stu-id="21d1b-226">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="21d1b-227">在弹出窗口中选择 " **打开** 存储库"。</span><span class="sxs-lookup"><span data-stu-id="21d1b-227">Select **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="21d1b-228">编辑文档</span><span class="sxs-lookup"><span data-stu-id="21d1b-228">Editing documentation</span></span>

<span data-ttu-id="21d1b-229">使用以下工作流，通过 Visual Studio Code 对文档进行更改：</span><span class="sxs-lookup"><span data-stu-id="21d1b-229">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="21d1b-230">在使用 Visual Studio Code 时，所有有关 [编辑](#editing-an-existing-article) 和 [创建](#creating-a-new-article) 文章的指南以及 [编辑 Markdown 的基础知识](#markdown-basics)也适用。</span><span class="sxs-lookup"><span data-stu-id="21d1b-230">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="21d1b-231">请确保你的克隆分叉与官方存储库保持最新。</span><span class="sxs-lookup"><span data-stu-id="21d1b-231">Make sure your cloned fork is up to date with the official repo.</span></span>
   1. <span data-ttu-id="21d1b-232">在 web 浏览器中，创建一个拉取请求，将 MicrosoftDocs/mixed reality "master" 中其他参与者的最近更改同步到分叉 (确保箭头指向) 正确的方式。</span><span class="sxs-lookup"><span data-stu-id="21d1b-232">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![将更改从 MicrosoftDocs/混合事实同步到你的分支](images/sync_repos.PNG)
   2. <span data-ttu-id="21d1b-234">在 Visual Studio Code 中，选择 "同步" 按钮，将最新更新的分支同步到本地克隆。</span><span class="sxs-lookup"><span data-stu-id="21d1b-234">In Visual Studio Code, select the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![单击 "同步" 按钮图像](images/sync_clone.png)
2. <span data-ttu-id="21d1b-236">使用 Visual Studio Code 在克隆的存储库中创建或编辑项目。</span><span class="sxs-lookup"><span data-stu-id="21d1b-236">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="21d1b-237">编辑一个或多个项目 (如有必要，将图像添加到 "images" 文件夹) 。</span><span class="sxs-lookup"><span data-stu-id="21d1b-237">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="21d1b-238">在 **资源管理器** 中 **保存** 更改。</span><span class="sxs-lookup"><span data-stu-id="21d1b-238">**Save** changes in **Explorer**.</span></span>
      
      ![在资源管理器中选择 "全部保存"](images/explorer_save.png)
   3. <span data-ttu-id="21d1b-240">) 提示时，提交 **源代码管理** 中的 **所有** 更改 (写入提交消息。</span><span class="sxs-lookup"><span data-stu-id="21d1b-240">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![在源代码管理中选择 "全部提交"](images/source_control_commit.png)
   4. <span data-ttu-id="21d1b-242">选择 " **同步** " 按钮，将所做的更改同步回 GitHub 上的源 (分叉) 上。</span><span class="sxs-lookup"><span data-stu-id="21d1b-242">Select the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![单击 "同步" 按钮](images/sync_back.png)
3. <span data-ttu-id="21d1b-244">在 web 浏览器中，创建一个拉取请求，将分支中的新更改同步回 MicrosoftDocs/mixed reality "master" (确保箭头指向) 正确的方式。</span><span class="sxs-lookup"><span data-stu-id="21d1b-244">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![创建从分叉到 MicrosoftDocs/混合现实的拉取请求](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="21d1b-246">有用的扩展</span><span class="sxs-lookup"><span data-stu-id="21d1b-246">Useful extensions</span></span>

<span data-ttu-id="21d1b-247">编辑文档时，以下 Visual Studio Code 扩展很有用：</span><span class="sxs-lookup"><span data-stu-id="21d1b-247">The following Visual Studio Code extensions are useful when editing documentation:</span></span>

- <span data-ttu-id="21d1b-248">[用于 Visual Studio Code 的文档 Markdown 扩展](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -使用 **Alt + M** 显示文档创作选项的菜单，如下所示：</span><span class="sxs-lookup"><span data-stu-id="21d1b-248">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="21d1b-249">搜索和引用已上传的映像。</span><span class="sxs-lookup"><span data-stu-id="21d1b-249">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="21d1b-250">添加格式（如列表、表和文档） `>[!NOTE]` 。</span><span class="sxs-lookup"><span data-stu-id="21d1b-250">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="21d1b-251">搜索和引用内部链接和书签 (指向) 页面内特定部分的链接。</span><span class="sxs-lookup"><span data-stu-id="21d1b-251">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="21d1b-252">突出显示格式错误 (将鼠标悬停在错误上以了解详细) 。</span><span class="sxs-lookup"><span data-stu-id="21d1b-252">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="21d1b-253">[代码拼写检查器](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -将为拼写错误的单词加下划线。右键单击拼写错误的单词以对其进行更改或将其保存到字典中。</span><span class="sxs-lookup"><span data-stu-id="21d1b-253">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
