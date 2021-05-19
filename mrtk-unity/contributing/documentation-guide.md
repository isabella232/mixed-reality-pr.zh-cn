---
title: 文档指南
description: MRTK 的文档准则和标准。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: cc5572e65540fa40cb1b8db56afbdd0986c467b9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144794"
---
# <a name="documentation-guidelines"></a><span data-ttu-id="49408-104">文档指南</span><span class="sxs-lookup"><span data-stu-id="49408-104">Documentation guidelines</span></span>

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

<span data-ttu-id="49408-105">本文档概述了混合现实工具包 (MRTK) 的文档准则和标准。</span><span class="sxs-lookup"><span data-stu-id="49408-105">This document outlines the documentation guidelines and standards for the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="49408-106">这介绍了文档编写和生成的技术方面，重点介绍了常见的缺陷，并描述了建议的写作风格。</span><span class="sxs-lookup"><span data-stu-id="49408-106">This provides an introduction to technical aspects of documentation writing and generation, to highlight common pitfalls, and to describe the recommended writing style.</span></span>

<span data-ttu-id="49408-107">页面本身应作为示例，因此它使用文档的预期样式和最常见的标记功能。</span><span class="sxs-lookup"><span data-stu-id="49408-107">The page itself is supposed to serve as an example, therefore it uses the intended style and the most common markup features of the documentation.</span></span>

- [<span data-ttu-id="49408-108">Source</span><span class="sxs-lookup"><span data-stu-id="49408-108">Source</span></span>](#source-documentation)
- [<span data-ttu-id="49408-109">操作指南</span><span class="sxs-lookup"><span data-stu-id="49408-109">How-to</span></span>](#how-to-documentation)
- [<span data-ttu-id="49408-110">设计</span><span class="sxs-lookup"><span data-stu-id="49408-110">Design</span></span>](#design-documentation)
- [<span data-ttu-id="49408-111">性能说明</span><span class="sxs-lookup"><span data-stu-id="49408-111">Performance notes</span></span>](#performance-notes)
- [<span data-ttu-id="49408-112">重大更改</span><span class="sxs-lookup"><span data-stu-id="49408-112">Breaking changes</span></span>](#breaking-changes)

---

## <a name="functionality-and-markup"></a><span data-ttu-id="49408-113">功能和标记</span><span class="sxs-lookup"><span data-stu-id="49408-113">Functionality and markup</span></span>

<span data-ttu-id="49408-114">本节介绍经常需要的功能。</span><span class="sxs-lookup"><span data-stu-id="49408-114">This section describes frequently needed features.</span></span> <span data-ttu-id="49408-115">若要查看其工作原理，请查看页面的源代码。</span><span class="sxs-lookup"><span data-stu-id="49408-115">To see how they work, look at the source code of the page.</span></span>

1. <span data-ttu-id="49408-116">编号列表</span><span class="sxs-lookup"><span data-stu-id="49408-116">Numbered lists</span></span>
   1. <span data-ttu-id="49408-117">带有至少三个前导空格的嵌套编号列表</span><span class="sxs-lookup"><span data-stu-id="49408-117">Nested numbered lists with at least 3 leading blank spaces</span></span>
   1. <span data-ttu-id="49408-118">代码中的实际数量是不相关的;分析将负责设置正确的项目编号。</span><span class="sxs-lookup"><span data-stu-id="49408-118">The actual number in code is irrelevant; parsing will take care of setting the correct item number.</span></span>

- <span data-ttu-id="49408-119">项目符号列表</span><span class="sxs-lookup"><span data-stu-id="49408-119">Bullet point lists</span></span>
  - <span data-ttu-id="49408-120">嵌套的项目符号点列表</span><span class="sxs-lookup"><span data-stu-id="49408-120">Nested bullet point lists</span></span>
- <span data-ttu-id="49408-121">带 \* \* 双星号的粗体文本\*\*</span><span class="sxs-lookup"><span data-stu-id="49408-121">Text in **bold** with \*\*double asterisk\*\*</span></span>
- <span data-ttu-id="49408-122"> 带有 \_ 下划线 \_ 或 \* 单星号的斜体文本\*</span><span class="sxs-lookup"><span data-stu-id="49408-122">_italic_ *text* with \_underscore\_ or \*single asterisk\*</span></span>
- <span data-ttu-id="49408-123">`highlighted as code`使用 backquotes 的句子内的文本 \`\`</span><span class="sxs-lookup"><span data-stu-id="49408-123">Text `highlighted as code` within a sentence \`using backquotes\`</span></span>
- <span data-ttu-id="49408-124">文档链接到文档页面 [MRTK 文档指南](documentation-guide.md)</span><span class="sxs-lookup"><span data-stu-id="49408-124">Links to docs pages [MRTK documentation guidelines](documentation-guide.md)</span></span>
- <span data-ttu-id="49408-125">链接到 [页中的定位点](#style);通过用短划线替换空格并将其转换为小写来形成定位点</span><span class="sxs-lookup"><span data-stu-id="49408-125">Links to [anchors within a page](#style); anchors are formed by replacing spaces with dashes, and converting to lowercase</span></span>

<span data-ttu-id="49408-126">对于代码示例，我们将块用于三个反撇号 \` \` \` ，并指定 *csharp* 作为语法突出显示的语言：</span><span class="sxs-lookup"><span data-stu-id="49408-126">For code samples we use the blocks with three backticks \`\`\` and specify *csharp* as the language for syntax highlighting:</span></span>

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

<span data-ttu-id="49408-127">在句子 中提及代码时 `use a single backtick` 。</span><span class="sxs-lookup"><span data-stu-id="49408-127">When mentioning code within a sentence `use a single backtick`.</span></span>

### <a name="todos"></a><span data-ttu-id="49408-128">TODOS</span><span class="sxs-lookup"><span data-stu-id="49408-128">TODOs</span></span>

<span data-ttu-id="49408-129">避免在文档内使用 TODOS，因为随着时间的推移，这些 TODOS (如代码 TODOS) 往往累积并提供有关它们应如何更新以及丢失原因的信息。</span><span class="sxs-lookup"><span data-stu-id="49408-129">Avoid using TODOs in docs, as over time these TODOs (like code TODOs) tend to accumulate and information about how they should be updated and why gets lost.</span></span>

<span data-ttu-id="49408-130">如果绝对有必要添加 TODO，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="49408-130">If it is absolutely necessary to add a TODO, follow these steps:</span></span>

1. <span data-ttu-id="49408-131">在 Github 上提出一个新问题，描述 TODO 背后的上下文，并提供足够的背景信息供其他参与者理解并解决 TODO。</span><span class="sxs-lookup"><span data-stu-id="49408-131">File a new issue on Github describing the context behind the TODO, and provide enough background that another contributor would be able to understand and then address the TODO.</span></span>
2. <span data-ttu-id="49408-132">在文档 todo 中引用问题 URL。</span><span class="sxs-lookup"><span data-stu-id="49408-132">Reference the issue URL in the todo in the docs.</span></span>

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a><span data-ttu-id="49408-133">突出显示的部分</span><span class="sxs-lookup"><span data-stu-id="49408-133">Highlighted sections</span></span>

<span data-ttu-id="49408-134">若要突出显示读取器的特定点，请使用 *> [!NOTE]* 、 *> [!WARNING]* 和 *> [!IMPORTANT]* 生成以下样式。</span><span class="sxs-lookup"><span data-stu-id="49408-134">To highlight specific points to the reader, use *> [!NOTE]* , *> [!WARNING]* , and *> [!IMPORTANT]* to produce the following styles.</span></span> <span data-ttu-id="49408-135">建议仅对特殊相关情况使用常规点和警告/重要点的注释。</span><span class="sxs-lookup"><span data-stu-id="49408-135">It is recommended to use notes for general points and warning/important points only for special relevant cases.</span></span>

> [!NOTE]
> <span data-ttu-id="49408-136">备注示例</span><span class="sxs-lookup"><span data-stu-id="49408-136">Example of a note</span></span>

> [!WARNING]
> <span data-ttu-id="49408-137">警告示例</span><span class="sxs-lookup"><span data-stu-id="49408-137">Example of a warning</span></span>

> [!IMPORTANT]
> <span data-ttu-id="49408-138">重要注释的示例</span><span class="sxs-lookup"><span data-stu-id="49408-138">Example of an important comment</span></span>

## <a name="page-layout"></a><span data-ttu-id="49408-139">页面布局</span><span class="sxs-lookup"><span data-stu-id="49408-139">Page layout</span></span>

### <a name="introduction"></a><span data-ttu-id="49408-140">简介</span><span class="sxs-lookup"><span data-stu-id="49408-140">Introduction</span></span>

<span data-ttu-id="49408-141">主章节标题之后的部分应用作该章节的简短介绍。</span><span class="sxs-lookup"><span data-stu-id="49408-141">The part right after the main chapter title should serve as a short introduction what the chapter is about.</span></span> <span data-ttu-id="49408-142">不要使此标题太长，请改为添加子标题。</span><span class="sxs-lookup"><span data-stu-id="49408-142">Do not make this too long, instead add sub headlines.</span></span> <span data-ttu-id="49408-143">这些允许链接到部分，并可以另存为书签。</span><span class="sxs-lookup"><span data-stu-id="49408-143">These allow to link to sections and can be saved as bookmarks.</span></span>

### <a name="main-body"></a><span data-ttu-id="49408-144">正文</span><span class="sxs-lookup"><span data-stu-id="49408-144">Main body</span></span>

<span data-ttu-id="49408-145">使用两级和三级标题来构建其余部分。</span><span class="sxs-lookup"><span data-stu-id="49408-145">Use two-level and three-level headlines to structure the rest.</span></span>

<span data-ttu-id="49408-146">**微型部分**</span><span class="sxs-lookup"><span data-stu-id="49408-146">**Mini Sections**</span></span>

<span data-ttu-id="49408-147">对应突出显示的块使用粗体文本行。我们在某些时候可能会将其替换为四级标题。</span><span class="sxs-lookup"><span data-stu-id="49408-147">Use a bold line of text for blocks that should stand out. We might replace this by four-level headlines at some point.</span></span>

### <a name="see-also-section"></a><span data-ttu-id="49408-148">"另请参阅"部分</span><span class="sxs-lookup"><span data-stu-id="49408-148">'See also' section</span></span>

<span data-ttu-id="49408-149">大多数页面都应以 *一个名为的章节* 结束。</span><span class="sxs-lookup"><span data-stu-id="49408-149">Most pages should end with a chapter called *See also*.</span></span> <span data-ttu-id="49408-150">本章只是指向与本主题相关的页面的链接的列表。</span><span class="sxs-lookup"><span data-stu-id="49408-150">This chapter is simply a bullet pointed list of links to pages related to this topic.</span></span> <span data-ttu-id="49408-151">这些链接也可能出现在页面文本中相应的位置，但这不是必需的。</span><span class="sxs-lookup"><span data-stu-id="49408-151">These links may also appear within the page text where appropriate, but this is not required.</span></span> <span data-ttu-id="49408-152">同样，页文本可能包含指向与主主题不相关的页面的链接，这些链接不应包含在 " *另请参阅* " 列表中。</span><span class="sxs-lookup"><span data-stu-id="49408-152">Similarly, the page text may contain links to pages that are not related to the main topic, these should not be included in the *See also* list.</span></span> <span data-ttu-id="49408-153">有关链接选择的示例，请参阅 [此页的 "" 另请参阅 "" 一章](#see-also) 。</span><span class="sxs-lookup"><span data-stu-id="49408-153">See [this page's ''See also'' chapter](#see-also) as an example for the choice of links.</span></span>

## <a name="table-of-contents-toc"></a><span data-ttu-id="49408-154">目录 (TOC) </span><span class="sxs-lookup"><span data-stu-id="49408-154">Table of Contents (TOC)</span></span>

<span data-ttu-id="49408-155">Toc 文件用于在 MRTK github.io 文档中生成导航栏。</span><span class="sxs-lookup"><span data-stu-id="49408-155">Toc files are used for generating the navigation bars in the MRTK github.io documentation.</span></span>
<span data-ttu-id="49408-156">添加新的文档文件时，请确保文档文件夹的一个 docker-compose.override.yml 文件中存在该文件的条目。</span><span class="sxs-lookup"><span data-stu-id="49408-156">Whenever a new documentation file is added, make sure that there's an entry for that file in one of the toc.yml files of the documentation folder.</span></span> <span data-ttu-id="49408-157">只有 toc 文件中列出的项目才会显示在开发人员文档的导航中。文档文件夹中的每个子文件夹都可以有一个 toc 文件，该文件可链接到任何现有的 toc 文件，以将其作为子节添加到导航的相应部分。</span><span class="sxs-lookup"><span data-stu-id="49408-157">Only articles listed in the toc files will show up in the navigation of the developer docs. There can be a toc file for every subfolder in the documentation folder which can be linked into any existing toc file to add it as a subsection to the corresponding part of the navigation.</span></span>

## <a name="style"></a><span data-ttu-id="49408-158">Style</span><span class="sxs-lookup"><span data-stu-id="49408-158">Style</span></span>

### <a name="writing-style"></a><span data-ttu-id="49408-159">写入样式</span><span class="sxs-lookup"><span data-stu-id="49408-159">Writing style</span></span>

<span data-ttu-id="49408-160">一般经验法则：尝试 **听专业人员**。</span><span class="sxs-lookup"><span data-stu-id="49408-160">General rule of thumb: Try to **sound professional**.</span></span> <span data-ttu-id="49408-161">这通常意味着避免出现 "对话音"。</span><span class="sxs-lookup"><span data-stu-id="49408-161">That usually means to avoid a 'conversational tone'.</span></span> <span data-ttu-id="49408-162">还要尝试避免 hyperbole 和 sensationalism。</span><span class="sxs-lookup"><span data-stu-id="49408-162">Also try to avoid hyperbole and sensationalism.</span></span>

1. <span data-ttu-id="49408-163">不要尝试) 有趣的 (。</span><span class="sxs-lookup"><span data-stu-id="49408-163">Don't try to be (overly) funny.</span></span>
2. <span data-ttu-id="49408-164">从不写入 "I"</span><span class="sxs-lookup"><span data-stu-id="49408-164">Never write 'I'</span></span>
3. <span data-ttu-id="49408-165">避免出现 "我们"。</span><span class="sxs-lookup"><span data-stu-id="49408-165">Avoid 'we'.</span></span> <span data-ttu-id="49408-166">这通常可以使用 "MRTK" 轻松只。</span><span class="sxs-lookup"><span data-stu-id="49408-166">This can usually be rephrased easily, using 'MRTK' instead.</span></span> <span data-ttu-id="49408-167">示例： "我们支持此功能"-> "MRTK 支持此功能" 或 "支持以下功能 ..."。</span><span class="sxs-lookup"><span data-stu-id="49408-167">Example: "we support this feature" -> "MRTK supports this feature" or "the following features are supported ...".</span></span>
4. <span data-ttu-id="49408-168">同样，尝试避免 "你"。</span><span class="sxs-lookup"><span data-stu-id="49408-168">Similarly, try to avoid 'you'.</span></span> <span data-ttu-id="49408-169">示例： "此简单更改将变为可配置的！"</span><span class="sxs-lookup"><span data-stu-id="49408-169">Example: "With this simple change your shader becomes configurable!"</span></span> <span data-ttu-id="49408-170">-> "着色器可以在很少的工作中进行配置。"</span><span class="sxs-lookup"><span data-stu-id="49408-170">-> "Shaders can be made configurable with little effort."</span></span>
5. <span data-ttu-id="49408-171">请勿使用'sloppy phrases'。</span><span class="sxs-lookup"><span data-stu-id="49408-171">Do not use 'sloppy phrases'.</span></span>
6. <span data-ttu-id="49408-172">避免声音过于积极，我们不需要销售任何内容。</span><span class="sxs-lookup"><span data-stu-id="49408-172">Avoid sounding overly excited, we do not need to sell anything.</span></span>
7. <span data-ttu-id="49408-173">同样，避免过于明显。</span><span class="sxs-lookup"><span data-stu-id="49408-173">Similarly, avoid being overly dramatic.</span></span> <span data-ttu-id="49408-174">很少需要感叹号。</span><span class="sxs-lookup"><span data-stu-id="49408-174">Exclamation marks are rarely needed.</span></span>

### <a name="capitalization"></a><span data-ttu-id="49408-175">大写</span><span class="sxs-lookup"><span data-stu-id="49408-175">Capitalization</span></span>

- <span data-ttu-id="49408-176">使用 **标题的句子大小写**。</span><span class="sxs-lookup"><span data-stu-id="49408-176">Use **Sentence case for headlines**.</span></span> <span data-ttu-id="49408-177">即</span><span class="sxs-lookup"><span data-stu-id="49408-177">Ie.</span></span> <span data-ttu-id="49408-178">将第一个字母和名称大写，但无其他内容。</span><span class="sxs-lookup"><span data-stu-id="49408-178">capitalize the first letter and names, but nothing else.</span></span>
- <span data-ttu-id="49408-179">对于其他所有内容，请使用常规英语。</span><span class="sxs-lookup"><span data-stu-id="49408-179">Use regular English for everything else.</span></span> <span data-ttu-id="49408-180">这意味着 **不将任意字词大写**，即使它们具有该上下文中的特殊含义。</span><span class="sxs-lookup"><span data-stu-id="49408-180">That means **do not capitalize arbitrary words**, even if they hold a special meaning in that context.</span></span> <span data-ttu-id="49408-181">首选 *用于突出显示某些字词的 italic* 文本 [，请参阅下面的](#emphasis-and-highlighting)。</span><span class="sxs-lookup"><span data-stu-id="49408-181">Prefer *italic text* for highlighting certain words, [see below](#emphasis-and-highlighting).</span></span>
- <span data-ttu-id="49408-182">当链接嵌入句子中 (这是首选) ，标准章节名称始终使用大写字母，从而破坏文本中无任意大写的规则。</span><span class="sxs-lookup"><span data-stu-id="49408-182">When a link is embedded in a sentence (which is the preferred method), the standard chapter name always uses capital letters, thus breaking the rule of no arbitrary capitalization inside text.</span></span> <span data-ttu-id="49408-183">因此，使用自定义链接名称修复大写。</span><span class="sxs-lookup"><span data-stu-id="49408-183">Therefore use a custom link name to fix the capitalization.</span></span> <span data-ttu-id="49408-184">例如，下面是边界 [控件文档](../features/ux-building-blocks/bounds-control.md) 的链接。</span><span class="sxs-lookup"><span data-stu-id="49408-184">As an example, here is a link to the [bounds control](../features/ux-building-blocks/bounds-control.md) documentation.</span></span>
- <span data-ttu-id="49408-185">将名称大写，例如 *Unity*。</span><span class="sxs-lookup"><span data-stu-id="49408-185">Do capitalize names, such as *Unity*.</span></span>
- <span data-ttu-id="49408-186">编写 Unity 编辑器 时，请勿将 *"editor"大写*。</span><span class="sxs-lookup"><span data-stu-id="49408-186">Do NOT capitalize "editor" when writing *Unity editor*.</span></span>

### <a name="emphasis-and-highlighting"></a><span data-ttu-id="49408-187">重点和突出显示</span><span class="sxs-lookup"><span data-stu-id="49408-187">Emphasis and highlighting</span></span>

<span data-ttu-id="49408-188">有两种方法可以强调或突出显示字词，即将其加粗或使其为 italic。</span><span class="sxs-lookup"><span data-stu-id="49408-188">There are two ways to emphasize or highlight words, making them bold or making them italic.</span></span> <span data-ttu-id="49408-189">粗体文本的效果是，粗体文本会卡住，因此，在浏览一段文本时，甚至只是滚动一页，都很容易被注意到。</span><span class="sxs-lookup"><span data-stu-id="49408-189">The effect of bold text is that **bold text sticks out** and therefore can easily be noticed while skimming a piece of text or even just scrolling over a page.</span></span> <span data-ttu-id="49408-190">粗体可以突出显示人们应该记住的短语。</span><span class="sxs-lookup"><span data-stu-id="49408-190">Bold is great to highlight phrases that people should remember.</span></span> <span data-ttu-id="49408-191">但是， **很少使用粗体文本**，因为它通常分散注意力。</span><span class="sxs-lookup"><span data-stu-id="49408-191">However, **use bold text rarely**, because it is generally distracting.</span></span>

<span data-ttu-id="49408-192">通常，用户希望"分组"逻辑上属于一部分或突出显示特定术语，因为它具有特殊含义。</span><span class="sxs-lookup"><span data-stu-id="49408-192">Often one wants to either 'group' something that belongs logically together or highlight a specific term, because it has a special meaning.</span></span> <span data-ttu-id="49408-193">这类情况不需要整体文本。</span><span class="sxs-lookup"><span data-stu-id="49408-193">Such things do not need to stand out of the overall text.</span></span> <span data-ttu-id="49408-194">使用斜体文本作为 *轻量方法* 可突出显示某些内容。</span><span class="sxs-lookup"><span data-stu-id="49408-194">Use italic text as a *lightweight method* to highlight something.</span></span>

<span data-ttu-id="49408-195">同样，如果在文本中提到了文件名、路径或菜单项，则更喜欢将其设置为斜体以便对其进行逻辑分组，而不会分散注意力。</span><span class="sxs-lookup"><span data-stu-id="49408-195">Similarly, when a filename, a path or a menu-entry is mentioned in text, prefer to make it italic to logically group it, without being distracting.</span></span>

<span data-ttu-id="49408-196">通常，请尽量 **避免不必要的文本突出显示**。</span><span class="sxs-lookup"><span data-stu-id="49408-196">In general, try to **avoid unnecessary text highlighting**.</span></span> <span data-ttu-id="49408-197">特殊术语可以突出显示一次以使读者知道，不要在整个文本中重复此类突出显示，而在这种情况下，它将不再延误。</span><span class="sxs-lookup"><span data-stu-id="49408-197">Special terms can be highlighted once to make the reader aware, do not repeat such highlighting throughout the text, when it serves no purpose anymore and only distracts.</span></span>

### <a name="mentioning-menu-entries"></a><span data-ttu-id="49408-198">提及菜单项</span><span class="sxs-lookup"><span data-stu-id="49408-198">Mentioning menu entries</span></span>

<span data-ttu-id="49408-199">提及用户应该单击的菜单项时，当前约定为： *Project > 文件 > 创建 > 叶*</span><span class="sxs-lookup"><span data-stu-id="49408-199">When mentioning a menu entry that a user should click, the current convention is: *Project > Files > Create > Leaf*</span></span>

### <a name="links"></a><span data-ttu-id="49408-200">链接</span><span class="sxs-lookup"><span data-stu-id="49408-200">Links</span></span>

<span data-ttu-id="49408-201">尽可能多地插入其他页面的有用链接，但每个链接只需一次。</span><span class="sxs-lookup"><span data-stu-id="49408-201">Insert as many useful links to other pages as possible, but each link only once.</span></span> <span data-ttu-id="49408-202">假设读者在页面上的每个链接上单击，并想要在同一页面打开20次的情况下，将其视为多么恼人。</span><span class="sxs-lookup"><span data-stu-id="49408-202">Assume a reader clicks on every link in the page, and think about how annoying it would be, if the same page opens 20 times.</span></span>

<span data-ttu-id="49408-203">首选句子中嵌入的链接：</span><span class="sxs-lookup"><span data-stu-id="49408-203">Prefer links embedded in a sentence:</span></span>

- <span data-ttu-id="49408-204">糟糕：准则很有用。</span><span class="sxs-lookup"><span data-stu-id="49408-204">BAD: Guidelines are useful.</span></span> <span data-ttu-id="49408-205">有关详细信息，请参阅 [此章节](../contributing/documentation-guide.md) 。</span><span class="sxs-lookup"><span data-stu-id="49408-205">See [this chapter](../contributing/documentation-guide.md) for details.</span></span>
- <span data-ttu-id="49408-206">好： [准则](documentation-guide.md) 很有用。</span><span class="sxs-lookup"><span data-stu-id="49408-206">GOOD: [Guidelines](documentation-guide.md) are useful.</span></span>

<span data-ttu-id="49408-207">避免外部链接，它们可能会过时或包含版权内容。</span><span class="sxs-lookup"><span data-stu-id="49408-207">Avoid external links, they can become outdated or contain copyrighted content.</span></span>

<span data-ttu-id="49408-208">添加链接时，请考虑是否还应该在 " [另请参阅](#see-also) " 部分中列出。</span><span class="sxs-lookup"><span data-stu-id="49408-208">When adding a link, consider whether it should also be listed in the [See also](#see-also) section.</span></span> <span data-ttu-id="49408-209">同样，请检查是否应将指向新页的链接添加到链接到页中。</span><span class="sxs-lookup"><span data-stu-id="49408-209">Similarly, check whether a link to the new page should be added to the linked-to page.</span></span>

### <a name="images--screenshots"></a><span data-ttu-id="49408-210">图像/屏幕截图</span><span class="sxs-lookup"><span data-stu-id="49408-210">Images / screenshots</span></span>

<span data-ttu-id="49408-211">**请慎用屏幕截图。**</span><span class="sxs-lookup"><span data-stu-id="49408-211">**Use screenshots sparingly.**</span></span> <span data-ttu-id="49408-212">维护文档中的图像是很多工作，小型 UI 更改会使大量屏幕截图过时。</span><span class="sxs-lookup"><span data-stu-id="49408-212">Maintaining images in documentation is a lot of work, small UI changes can make a lot of screenshots outdated.</span></span> <span data-ttu-id="49408-213">以下规则将减少维护工作量：</span><span class="sxs-lookup"><span data-stu-id="49408-213">The following rules will reduce maintenance effort:</span></span>

1. <span data-ttu-id="49408-214">请勿对文本中描述的内容使用屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="49408-214">Do not use screenshots for things that can be described in text.</span></span> <span data-ttu-id="49408-215">特别是 **，切勿为显示属性** 名称和值的唯一目的对属性网格进行屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="49408-215">Especially, **never screenshot a property grid** for the sole purpose of showing property names and values.</span></span>
2. <span data-ttu-id="49408-216">请勿在屏幕截图中包括与显示内容无关的内容。</span><span class="sxs-lookup"><span data-stu-id="49408-216">Do not include things in a screenshot that are irrelevant to what is shown.</span></span> <span data-ttu-id="49408-217">例如，当显示呈现效果时，请创建视区屏幕截图，但排除其周围的任何 UI。</span><span class="sxs-lookup"><span data-stu-id="49408-217">For instance, when a rendering effect is shown, make a screenshot of the viewport, but exclude any UI around it.</span></span> <span data-ttu-id="49408-218">显示某些 UI 时，请尝试移动窗口，使图像中只有该重要部分。</span><span class="sxs-lookup"><span data-stu-id="49408-218">Showing some UI, try to move windows around such that only that important part is in the image.</span></span>
3. <span data-ttu-id="49408-219">包括屏幕截图 UI 时，只显示重要部分。</span><span class="sxs-lookup"><span data-stu-id="49408-219">When including screenshot UI, only show the important parts.</span></span> <span data-ttu-id="49408-220">例如，在工具栏中讨论按钮时，请制作一个小图像，显示重要的工具栏按钮，但排除其周围的所有按钮。</span><span class="sxs-lookup"><span data-stu-id="49408-220">For example, when talking about buttons in a toolbar, make a small image that shows the important toolbar buttons, but exclude everything around it.</span></span>
4. <span data-ttu-id="49408-221">仅使用易于重现的图像。</span><span class="sxs-lookup"><span data-stu-id="49408-221">Only use images that are easy to reproduce.</span></span> <span data-ttu-id="49408-222">这意味着不要将标记或突出显示绘制到屏幕截图中。</span><span class="sxs-lookup"><span data-stu-id="49408-222">That means do not paint markers or highlights into screenshots.</span></span> <span data-ttu-id="49408-223">首先，没有一致的规则来说明这些规则的外观。</span><span class="sxs-lookup"><span data-stu-id="49408-223">First, there are no consistent rules how these should look, anyway.</span></span> <span data-ttu-id="49408-224">其次，重现此类屏幕截图需要额外的工作量。</span><span class="sxs-lookup"><span data-stu-id="49408-224">Second, reproducing such a screenshot is additional effort.</span></span> <span data-ttu-id="49408-225">请改为描述文本中的重要部分。</span><span class="sxs-lookup"><span data-stu-id="49408-225">Instead, describe the important parts in text.</span></span> <span data-ttu-id="49408-226">此规则存在例外情况，但它们很少见。</span><span class="sxs-lookup"><span data-stu-id="49408-226">There are exceptions to this rule, but they are rare.</span></span>
5. <span data-ttu-id="49408-227">显然，重新创建动画 GIF 的工作要多得多。</span><span class="sxs-lookup"><span data-stu-id="49408-227">Obviously, it is much more effort to recreate an animated GIF.</span></span> <span data-ttu-id="49408-228">希望负责在一段时间结束之前重新创建它，或者希望人们放弃它（如果他们不想花费该时间）。</span><span class="sxs-lookup"><span data-stu-id="49408-228">Expect to be responsible to recreate it until the end of time, or expect people to throw it out, if they don't want to spend that time.</span></span>
6. <span data-ttu-id="49408-229">将文章中的图像数保持在较低水平。</span><span class="sxs-lookup"><span data-stu-id="49408-229">Keep the number of images in an article low.</span></span> <span data-ttu-id="49408-230">通常，一个好方法是制作一个工具的整体屏幕截图，其中显示了所有内容，然后以文本描述其余内容。</span><span class="sxs-lookup"><span data-stu-id="49408-230">Often a good method is to make one overall screenshot of some tool, that shows everything, and then describe the rest in text.</span></span> <span data-ttu-id="49408-231">这样，必要时可以轻松替换屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="49408-231">This makes it easy to replace the screenshot when necessary.</span></span>

<span data-ttu-id="49408-232">其他一些方面：</span><span class="sxs-lookup"><span data-stu-id="49408-232">Some other aspects:</span></span>

- <span data-ttu-id="49408-233">屏幕截图的编辑器 UI 应使用浅灰色主题编辑器，因为并非所有用户都有权访问深色主题，我们希望尽可能保持一致。</span><span class="sxs-lookup"><span data-stu-id="49408-233">The editor UI for screenshots should use light gray theme editor as not all users have access to the dark theme and we'd like to keep things as consistent as possible.</span></span>
- <span data-ttu-id="49408-234">默认图像宽度为500像素，因为这很适合大多数监视器。</span><span class="sxs-lookup"><span data-stu-id="49408-234">Default image width is 500 pixels, as this displays well on most monitors.</span></span> <span data-ttu-id="49408-235">不要与它有太大的不同。</span><span class="sxs-lookup"><span data-stu-id="49408-235">Try not to deviate too much from it.</span></span> <span data-ttu-id="49408-236">800像素宽度应为最大值。</span><span class="sxs-lookup"><span data-stu-id="49408-236">800 pixels width should be the maximum.</span></span>
- <span data-ttu-id="49408-237">使用 Png 为 UI 的屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="49408-237">Use PNGs for screenshots of UI.</span></span>
- <span data-ttu-id="49408-238">将 Png 或 JPGs 用于3D 视区屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="49408-238">Use PNGs or JPGs for 3D viewport screenshots.</span></span> <span data-ttu-id="49408-239">优于压缩比。</span><span class="sxs-lookup"><span data-stu-id="49408-239">Prefer quality over compression ratio.</span></span>

### <a name="list-of-component-properties"></a><span data-ttu-id="49408-240">组件属性列表</span><span class="sxs-lookup"><span data-stu-id="49408-240">List of component properties</span></span>

<span data-ttu-id="49408-241">记录属性列表时，请使用粗体文本突出显示属性名称，然后使用换行符和常规文本对其进行描述。</span><span class="sxs-lookup"><span data-stu-id="49408-241">When documenting a list of properties, use bold text to highlight the property name, then line breaks and regular text to describe them.</span></span> <span data-ttu-id="49408-242">不要使用子章节或项目符号列表。</span><span class="sxs-lookup"><span data-stu-id="49408-242">Do not use sub-chapters or bullet point lists.</span></span>

<span data-ttu-id="49408-243">此外，请不要忘记以句点结束所有句子。</span><span class="sxs-lookup"><span data-stu-id="49408-243">Also, don't forget to finish all sentences with a period.</span></span>

## <a name="page-completion-checklist"></a><span data-ttu-id="49408-244">页面完成清单</span><span class="sxs-lookup"><span data-stu-id="49408-244">Page completion checklist</span></span>

1. <span data-ttu-id="49408-245">确保遵循本文档的指导原则。</span><span class="sxs-lookup"><span data-stu-id="49408-245">Ensure that this document's guidelines were followed.</span></span>
1. <span data-ttu-id="49408-246">浏览文档结构，并查看是否可以在其他页面的 " [另请参阅](#see-also) " 部分下提及新文档。</span><span class="sxs-lookup"><span data-stu-id="49408-246">Browse the document structure and see if the new document could be mentioned under the [See also](#see-also) section of other pages.</span></span>
1. <span data-ttu-id="49408-247">如果可用，请对主题进行校对-阅读有关技术正确性的页面。</span><span class="sxs-lookup"><span data-stu-id="49408-247">If available, have someone with knowledge of the topic proof-read the page for technical correctness.</span></span>
1. <span data-ttu-id="49408-248">让别人对样式和格式的页面进行校对。</span><span class="sxs-lookup"><span data-stu-id="49408-248">Have someone proof-read the page for style and formatting.</span></span> <span data-ttu-id="49408-249">这可能是与主题不熟悉的人，这也是获得文档理解方式的反馈的一个好主意。</span><span class="sxs-lookup"><span data-stu-id="49408-249">This can be someone unfamiliar with the topic, which is also a good idea to get feedback about how understandable the documentation is.</span></span>

## <a name="source-documentation"></a><span data-ttu-id="49408-250">源文档</span><span class="sxs-lookup"><span data-stu-id="49408-250">Source documentation</span></span>

<span data-ttu-id="49408-251">将从 MRTK 源文件中自动生成 API 文档。</span><span class="sxs-lookup"><span data-stu-id="49408-251">API documentation will be generated automatically from the MRTK source files.</span></span> <span data-ttu-id="49408-252">为了便于实现此操作，源文件需要包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="49408-252">To facilitate this, source files are required to contain the following:</span></span>

- [<span data-ttu-id="49408-253">类、结构、枚举摘要块</span><span class="sxs-lookup"><span data-stu-id="49408-253">Class, struct, enum summary blocks</span></span>](#class-struct-enum-summary-blocks)
- [<span data-ttu-id="49408-254">属性、方法、事件摘要块</span><span class="sxs-lookup"><span data-stu-id="49408-254">Property, method, event summary blocks</span></span>](#property-method-event-summary-blocks)
- [<span data-ttu-id="49408-255">功能简介版本和依赖项</span><span class="sxs-lookup"><span data-stu-id="49408-255">Feature introduction version and dependencies</span></span>](#feature-introduction-version-and-dependencies)
- [<span data-ttu-id="49408-256">序列化字段</span><span class="sxs-lookup"><span data-stu-id="49408-256">Serialized fields</span></span>](#serialized-fields)
- [<span data-ttu-id="49408-257">枚举值</span><span class="sxs-lookup"><span data-stu-id="49408-257">Enumeration values</span></span>](#enumeration-values)

<span data-ttu-id="49408-258">除了上述代码，还应对代码进行良好的注释，以便进行维护、bug 修复和轻松自定义。</span><span class="sxs-lookup"><span data-stu-id="49408-258">In addition to the above, the code should be well commented to allow for maintenance, bug fixes and ease of customization.</span></span>

### <a name="class-struct-enum-summary-blocks"></a><span data-ttu-id="49408-259">类、结构、枚举摘要块</span><span class="sxs-lookup"><span data-stu-id="49408-259">Class, struct, enum summary blocks</span></span>

<span data-ttu-id="49408-260">如果将类、结构或枚举添加到 MRTK，则必须描述其用途。</span><span class="sxs-lookup"><span data-stu-id="49408-260">If a class, struct or enum is being added to the MRTK, its purpose must be described.</span></span> <span data-ttu-id="49408-261">这是以 类上方的摘要块的形式。</span><span class="sxs-lookup"><span data-stu-id="49408-261">This is to take the form of a summary block above the class.</span></span>

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

<span data-ttu-id="49408-262">如果存在任何类级依赖项，应在摘要正下方的备注块中记录它们。</span><span class="sxs-lookup"><span data-stu-id="49408-262">If there are any class level dependencies, they should be documented in a remarks block, immediately below the summary.</span></span>

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

<span data-ttu-id="49408-263">在未提供类、结构或枚举摘要的情况下提交的拉取请求不会获得批准。</span><span class="sxs-lookup"><span data-stu-id="49408-263">Pull Requests submitted without summaries for classes, structures or enums will not be approved.</span></span>

### <a name="property-method-event-summary-blocks"></a><span data-ttu-id="49408-264">属性、方法、事件摘要块</span><span class="sxs-lookup"><span data-stu-id="49408-264">Property, method, event summary blocks</span></span>

<span data-ttu-id="49408-265">无论代码可见性 (公共、专用、受保护和内部) ，都将使用摘要块记录 PMES (属性、方法和) 事件。</span><span class="sxs-lookup"><span data-stu-id="49408-265">Properties, methods and events (PMEs) as well as fields are to be documented with summary blocks, regardless of code visibility (public, private, protected and internal).</span></span> <span data-ttu-id="49408-266">文档生成工具负责筛选和发布公共和受保护的功能。</span><span class="sxs-lookup"><span data-stu-id="49408-266">The documentation generation tool is responsible for filtering out and publishing only the public and protected features.</span></span>

<span data-ttu-id="49408-267">注意：Unity 方法不需要摘要 **块** ， (唤醒、启动、更新) 。</span><span class="sxs-lookup"><span data-stu-id="49408-267">NOTE: A summary block is **not** required for Unity methods (ex: Awake, Start, Update).</span></span>

<span data-ttu-id="49408-268">批准拉 **取** 请求需要 PME 文档。</span><span class="sxs-lookup"><span data-stu-id="49408-268">PME documentation is **required** for a pull request to be approved.</span></span>

<span data-ttu-id="49408-269">作为 PME 摘要块的一部分，参数和返回的数据的含义和用途是必需的。</span><span class="sxs-lookup"><span data-stu-id="49408-269">As part of a PME summary block, the meaning and purpose of parameters and returned data is required.</span></span>

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a><span data-ttu-id="49408-270">功能简介版本和依赖项</span><span class="sxs-lookup"><span data-stu-id="49408-270">Feature introduction version and dependencies</span></span>

<span data-ttu-id="49408-271">作为 API 摘要文档的一部分，有关引入该功能的 MRTK 版本以及任何依赖项的信息都应记录在备注块中。</span><span class="sxs-lookup"><span data-stu-id="49408-271">As part of the API summary documentation, information regarding the MRTK version in which the feature was introduced and any dependencies should be documented in a remarks block.</span></span>

<span data-ttu-id="49408-272">依赖项应包括扩展和/或平台依赖项。</span><span class="sxs-lookup"><span data-stu-id="49408-272">Dependencies should include extension and/or platform dependencies.</span></span>

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a><span data-ttu-id="49408-273">序列化字段</span><span class="sxs-lookup"><span data-stu-id="49408-273">Serialized fields</span></span>

<span data-ttu-id="49408-274">最佳做法是使用 Unity 的工具提示属性为检查器中的脚本字段提供运行时文档。</span><span class="sxs-lookup"><span data-stu-id="49408-274">It is a good practice to use Unity's tooltip attribute to provide runtime documentation for a script's fields in the inspector.</span></span>

<span data-ttu-id="49408-275">为了使配置选项包含在 API 文档中，脚本需要 *至少* 在摘要块中包含工具提示内容。</span><span class="sxs-lookup"><span data-stu-id="49408-275">So that configuration options are included in the API documentation, scripts are required to include *at least* the tooltip contents in a summary block.</span></span>

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a><span data-ttu-id="49408-276">枚举值</span><span class="sxs-lookup"><span data-stu-id="49408-276">Enumeration values</span></span>

<span data-ttu-id="49408-277">在定义和枚举时，代码还必须使用 summary 块记录枚举值的含义。</span><span class="sxs-lookup"><span data-stu-id="49408-277">When defining and enumeration, code must also document the meaning of the enum values using a summary block.</span></span> <span data-ttu-id="49408-278">可以选择使用备注块来提供更多详细信息以增强理解。</span><span class="sxs-lookup"><span data-stu-id="49408-278">Remarks blocks can optionally be used to provide additional details to enhance understanding.</span></span>

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a><span data-ttu-id="49408-279">操作说明文档</span><span class="sxs-lookup"><span data-stu-id="49408-279">How-to documentation</span></span>

<span data-ttu-id="49408-280">混合现实工具包的许多用户可能不需要使用 API 文档。</span><span class="sxs-lookup"><span data-stu-id="49408-280">Many users of the Mixed Reality Toolkit may not need to use the API documentation.</span></span> <span data-ttu-id="49408-281">这些用户将利用我们提供的可重复使用的 prototyping 和脚本来创建自己的体验。</span><span class="sxs-lookup"><span data-stu-id="49408-281">These users will take advantage of our pre-made, reusable prefabs and scripts to create their experiences.</span></span>

<span data-ttu-id="49408-282">每个功能区域都包含一个或多个 markdown ( md) 文件，这些文件在相当高的级别描述，提供了什么。</span><span class="sxs-lookup"><span data-stu-id="49408-282">Each feature area will contain one or more markdown (.md) files that describe at a fairly high level, what is provided.</span></span> <span data-ttu-id="49408-283">根据给定功能区域的大小和/或复杂性，可能需要其他文件，每个功能最多有一个。</span><span class="sxs-lookup"><span data-stu-id="49408-283">Depending on the size and/or complexity of a given feature area, there may be a need for additional files, up to one per feature provided.</span></span>

<span data-ttu-id="49408-284">添加功能后 (或更改用法) ，必须提供概述文档。</span><span class="sxs-lookup"><span data-stu-id="49408-284">When a feature is added (or the usage is changed), overview documentation must be provided.</span></span>

<span data-ttu-id="49408-285">在本文档中，应提供 "操作说明" 部分（包括说明），以帮助客户在入门中熟悉某个功能或概念。</span><span class="sxs-lookup"><span data-stu-id="49408-285">As part of this documentation, how-to sections, including illustrations, should be provided to assist customers new to a feature or concept in getting started.</span></span>

## <a name="design-documentation"></a><span data-ttu-id="49408-286">设计文档</span><span class="sxs-lookup"><span data-stu-id="49408-286">Design documentation</span></span>

<span data-ttu-id="49408-287">混合现实为创建全新的世界提供了机会。</span><span class="sxs-lookup"><span data-stu-id="49408-287">Mixed Reality provides an opportunity to create entirely new worlds.</span></span> <span data-ttu-id="49408-288">部分原因可能涉及创建自定义资产，以便与 MRTK 一起使用。</span><span class="sxs-lookup"><span data-stu-id="49408-288">Part of this is likely to involve the creation of custom assets for use with the MRTK.</span></span> <span data-ttu-id="49408-289">为了使客户能够免费实现此要求，组件应提供描述任何格式或其他对作品资产的要求的设计文档。</span><span class="sxs-lookup"><span data-stu-id="49408-289">To make this as friction free as possible for customers, components should provide design documentation describing any formatting or other requirements for art assets.</span></span>

<span data-ttu-id="49408-290">设计文档可能有帮助的一些示例：</span><span class="sxs-lookup"><span data-stu-id="49408-290">Some examples where design documentation can be helpful:</span></span>

- <span data-ttu-id="49408-291">游标模型</span><span class="sxs-lookup"><span data-stu-id="49408-291">Cursor models</span></span>
- <span data-ttu-id="49408-292">空间映射可视化效果</span><span class="sxs-lookup"><span data-stu-id="49408-292">Spatial mapping visualizations</span></span>
- <span data-ttu-id="49408-293">声音效果文件</span><span class="sxs-lookup"><span data-stu-id="49408-293">Sound effect files</span></span>

<span data-ttu-id="49408-294">**强烈** 建议使用这种类型的文档，并且 **可能** 会在拉取请求评审过程中请求此类文档。</span><span class="sxs-lookup"><span data-stu-id="49408-294">This type of documentation is **strongly** recommended, and **may** be requested as part of a pull request review.</span></span>

<span data-ttu-id="49408-295">这不一定与[MS 开发人员网站](/windows/mixed-reality/design)上的设计建议有所不同</span><span class="sxs-lookup"><span data-stu-id="49408-295">This may or may not be different from the design recommendation on the [MS Developer site](/windows/mixed-reality/design)</span></span>

## <a name="performance-notes"></a><span data-ttu-id="49408-296">性能说明</span><span class="sxs-lookup"><span data-stu-id="49408-296">Performance notes</span></span>

<span data-ttu-id="49408-297">一些重要功能会花费性能成本。</span><span class="sxs-lookup"><span data-stu-id="49408-297">Some important features come at a performance cost.</span></span> <span data-ttu-id="49408-298">通常，此代码将非常依赖于其配置方式。</span><span class="sxs-lookup"><span data-stu-id="49408-298">Often this code will very depending how they are configured.</span></span>

<span data-ttu-id="49408-299">例如：</span><span class="sxs-lookup"><span data-stu-id="49408-299">For example:</span></span>

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

<span data-ttu-id="49408-300">建议对 CPU 和/或 GPU 繁重的组件使用性能说明，并且可能会作为拉取请求评审的一部分进行请求。</span><span class="sxs-lookup"><span data-stu-id="49408-300">Performance notes are recommended for CPU and/or GPU heavy components and **may** be requested as part of a pull request review.</span></span> <span data-ttu-id="49408-301">API 和概述文档中将包含任何 **适用的性能** 说明。</span><span class="sxs-lookup"><span data-stu-id="49408-301">Any applicable performance notes are to be included in API **and** overview documentation.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="49408-302">中断性变更</span><span class="sxs-lookup"><span data-stu-id="49408-302">Breaking changes</span></span>

<span data-ttu-id="49408-303">中断性变更文档包含一个 [顶级文件，](../contributing/breaking-changes.md) 该文件链接到每个功能区的单个 breaking-changes.md。</span><span class="sxs-lookup"><span data-stu-id="49408-303">Breaking changes documentation is to consist of a top level [file](../contributing/breaking-changes.md) which links to each feature area's individual breaking-changes.md.</span></span>

<span data-ttu-id="49408-304">文件 breaking-changes.md 区域是包含给定版本的所有已知中断性变更的列表，以及过去版本中中断性变更的历史记录。</span><span class="sxs-lookup"><span data-stu-id="49408-304">The feature area breaking-changes.md files are to contain the list of all known breaking changes for a given release **as well as** the history of breaking changes from past releases.</span></span>

<span data-ttu-id="49408-305">例如：</span><span class="sxs-lookup"><span data-stu-id="49408-305">For example:</span></span>

```md
Spatial sound breaking changes

2018.07.2
* Spatialization of the imaginary effect is now required.
* Management of randomized AudioClip files requires an entropy value in the manager node.

2018.07.1
No known breaking changes

2018.07.0
...
```

<span data-ttu-id="49408-306">功能级别中包含的信息 breaking-changes.md 文件将聚合到每个新 MRTK 发布的发行说明中。</span><span class="sxs-lookup"><span data-stu-id="49408-306">The information contained within the feature level breaking-changes.md files will be aggregated to the release notes for each new MRTK release.</span></span>

<span data-ttu-id="49408-307">任何属于更改的中断性变更 **都必须** 记录为拉取请求的一部分。</span><span class="sxs-lookup"><span data-stu-id="49408-307">Any breaking changes that are part of a change **must** be documented as part of a Pull Request.</span></span>

## <a name="tools-for-editing-markdown"></a><span data-ttu-id="49408-308">用于编辑 MarkDown 的工具</span><span class="sxs-lookup"><span data-stu-id="49408-308">Tools for editing MarkDown</span></span>

<span data-ttu-id="49408-309">[Visual Studio Code](https://code.visualstudio.com/) 是一个很好的工具，用于编辑 MRTK 文档中的 Markdown 文件。</span><span class="sxs-lookup"><span data-stu-id="49408-309">[Visual Studio Code](https://code.visualstudio.com/) is a great tool for editing markdown files that are part of MRTK's documentation.</span></span>

<span data-ttu-id="49408-310">编写文档时，强烈建议安装以下两个扩展：</span><span class="sxs-lookup"><span data-stu-id="49408-310">When writing documentation, installing the following two extensions is also highly recommended:</span></span>

- <span data-ttu-id="49408-311">Docs Markdown 扩展Visual Studio Code - 使用 Alt+M 打开文档创作选项菜单。</span><span class="sxs-lookup"><span data-stu-id="49408-311">Docs Markdown Extension for Visual Studio Code - Use Alt+M to bring up a menu of docs authoring options.</span></span>

- <span data-ttu-id="49408-312">代码拼写检查器 - 拼写错误的单词将带有下划线;右键单击拼写错误的单词以将其更改或保存到字典中。</span><span class="sxs-lookup"><span data-stu-id="49408-312">Code Spell Checker - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>

<span data-ttu-id="49408-313">这两者都打包在 Microsoft 发布的 Docs 创作包中。</span><span class="sxs-lookup"><span data-stu-id="49408-313">Both of these come packaged in the Microsoft published Docs Authoring Pack.</span></span>

## <a name="see-also"></a><span data-ttu-id="49408-314">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49408-314">See also</span></span> 

* [<span data-ttu-id="49408-315">示例链接</span><span class="sxs-lookup"><span data-stu-id="49408-315">Example link</span></span>](https://www.google.com)