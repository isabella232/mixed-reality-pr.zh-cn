---
title: 文档指南
description: MRTK 的文档准则和标准。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: aa583876d4ca9e115d4ea4507638eebab838207230693cb7c24b781d8f0b020b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210714"
---
# <a name="documentation-guidelines"></a>文档指南

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

本文档概述了混合现实 Toolkit (MRTK) 的文档准则和标准。 这介绍了文档编写和生成的技术方面，重点介绍了常见的缺陷，并描述了建议的写作风格。

页面本身应作为示例，因此它使用文档的预期样式和最常见的标记功能。

- [Source](#source-documentation)
- [操作指南](#how-to-documentation)
- [设计](#design-documentation)
- [性能说明](#performance-notes)
- [重大更改](#breaking-changes)

---

## <a name="functionality-and-markup"></a>功能和标记

本节介绍经常需要的功能。 若要查看其工作原理，请查看页面的源代码。

1. 编号列表
   1. 带有至少三个前导空格的嵌套编号列表
   1. 代码中的实际数量是不相关的;分析将负责设置正确的项目编号。

- 项目符号列表
  - 嵌套的项目符号点列表
- 带 \* \* 双星号的粗体文本\*\*
-  带有 \_ 下划线 \_ 或 \* 单星号的斜体文本\*
- `highlighted as code`使用 backquotes 的句子内的文本 \`\`
- 文档链接到文档页面 [MRTK 文档指南](documentation-guide.md)
- 链接到 [页中的定位点](#style);通过用短划线替换空格并将其转换为小写来形成定位点

对于代码示例，我们将块用于三个反撇号 \` \` \` ，并指定 *csharp* 作为语法突出显示的语言：

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

当涉及句子中的代码时 `use a single backtick` 。

### <a name="todos"></a>Todo

避免在文档中使用 Todo，因为随着时间的推移，这些 Todo (如代码 Todo) 往往会积累，有关应如何更新以及为何会丢失。

如果绝对需要添加 TODO，请遵循以下步骤：

1. 在 Github 上指出 TODO 后面的上下文的新问题，并提供足够的背景，使另一参与者能够理解并解决 TODO 问题。
2. 参考文档中 todo 的问题 URL。

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a>突出显示部分

若要突出显示读取器的特定点，请使用 *> [!NOTE]* 、 *> [!WARNING]* 和 *> [!IMPORTANT]* 生成以下样式。 建议仅将说明用于特殊的相关事例，并针对一般点和警告/要点使用备注。

> [!NOTE]
> 注释示例

> [!WARNING]
> 警告示例

> [!IMPORTANT]
> 重要注释示例

## <a name="page-layout"></a>页面布局

### <a name="introduction"></a>简介

本章标题后面的部分应作为本章内容的简短介绍。 不要将其设置得太长，而应添加子标题。 它们允许链接到部分，并可以保存为书签。

### <a name="main-body"></a>主体

使用两级和三级标题来构造其余内容。

**迷你部分**

为应突出显示的块使用粗体文本。在某个时候，我们可能会将此替换为四个级别的标题。

### <a name="see-also-section"></a>"另请参阅" 部分

大多数页面都应以 *一个名为的章节* 结束。 本章只是指向与本主题相关的页面的链接的列表。 这些链接也可能出现在页面文本中相应的位置，但这不是必需的。 同样，页文本可能包含指向与主主题不相关的页面的链接，这些链接不应包含在 " *另请参阅* " 列表中。 有关链接选择的示例，请参阅 [此页的 "" 另请参阅 "" 一章](#see-also) 。

## <a name="table-of-contents-toc"></a>目录 (TOC) 

Toc 文件用于在 MRTK github.io 文档中生成导航栏。
添加新的文档文件时，请确保文档文件夹的一个 docker-compose.override.yml 文件中存在该文件的条目。 只有 toc 文件中列出的项目才会显示在开发人员文档的导航中。文档文件夹中的每个子文件夹都可以有一个 toc 文件，该文件可链接到任何现有的 toc 文件，以将其作为子节添加到导航的相应部分。

## <a name="style"></a>Style

### <a name="writing-style"></a>写入样式

一般经验法则：尝试 **听专业人员**。 这通常意味着避免出现 "对话音"。 还要尝试避免 hyperbole 和 sensationalism。

1. 不要尝试) 有趣的 (。
2. 从不写入 "I"
3. 避免出现 "我们"。 这通常可以使用 "MRTK" 轻松只。 示例： "我们支持此功能"-> "MRTK 支持此功能" 或 "支持以下功能 ..."。
4. 同样，尝试避免 "你"。 示例： "此简单更改将变为可配置的！" -> "着色器可以在很少的工作中进行配置。"
5. 不要使用 "草率短语"。
6. 避免太兴奋，我们不需要进行任何销售。
7. 同样，避免过于巨大。 很少需要感叹号。

### <a name="capitalization"></a>大写

- 将 **句子事例用于标题**。 即 首字母和名称的首字母大写，但没有其他内容。
- 对于其他所有内容，请使用常规英语。 这意味着 **不会将任意字词大写**，即使它们在该上下文中具有特殊含义。 首选 *斜体文本* 以突出显示某些字词， [请参阅下文](#emphasis-and-highlighting)。
- 如果某个句子嵌入了某个句子 (这是首选方法) ，则标准章节名称始终使用大写字母，因此不会在文本内产生任意大小写规则。 因此，请使用自定义链接名称来修复此大写。 例如，下面是指向 [边界控件](../features/ux-building-blocks/bounds-control.md) 文档的链接。
- 将名称大写，例如 *Unity*。
- 编写 *Unity 编辑器* 时，不要将 "editor" 改为大写。

### <a name="emphasis-and-highlighting"></a>强调和突出显示

可以通过两种方式强调或突出显示单词，使它们变为粗体或使其倾斜。 粗体文本的效果是 **粗体文本显示出来** ，因此在支撑文本片段或甚至只是滚动页面时，可以很容易地注意到。 粗体突出显示了人们应记住的短语。 但是， **很少使用粗体文本**，因为这通常会分散注意力。

通常，一种方法是希望 "组合" 在逻辑上属于同一项，或突出显示特定的项，因为它具有特殊意义。 这类情况不需要整体文本。 使用斜体文本作为 *轻量方法* 可突出显示某些内容。

同样，如果在文本中提到了文件名、路径或菜单项，则更喜欢将其设置为斜体以便对其进行逻辑分组，而不会分散注意力。

通常，请尽量 **避免不必要的文本突出显示**。 特殊术语可以突出显示一次以使读者知道，不要在整个文本中重复此类突出显示，而在这种情况下，它将不再延误。

### <a name="mentioning-menu-entries"></a>提及菜单项

提及用户应该单击的菜单项时，当前约定为： *Project > 文件 > 创建 > 叶*

### <a name="links"></a>链接

向其他页面插入尽可能多的有用链接，但每个链接只插入一次。 假设读者单击页面的每一个链接，并考虑如果同一页打开 20 次，它会有多令人麻烦。

首选嵌入在句子中的链接：

- 错误：指南很有用。 有关详细信息 [，请参阅](../contributing/documentation-guide.md) 本章。
- 好： [指南](documentation-guide.md) 很有用。

避免外部链接，它们可能会过时或包含受版权保护的内容。

添加链接时，请考虑是否还应在"另请参阅" [部分中列出](#see-also) 该链接。 同样，检查是否应当将指向新页面的链接添加到链接页。

### <a name="images--screenshots"></a>图像/屏幕截图

**请谨慎使用屏幕截图。** 维护文档中的图像是一项大量工作，较小的 UI 更改会使大量屏幕截图过时。 以下规则将减少维护工作量：

1. 请勿对文本中描述的内容使用屏幕截图。 特别是 **，切勿为显示属性** 名称和值的唯一目的对属性网格进行屏幕截图。
2. 请勿在屏幕截图中包括与显示内容无关的内容。 例如，当显示呈现效果时，请创建视区屏幕截图，但排除其周围的任何 UI。 显示某些 UI 时，请尝试移动窗口，使图像中只有该重要部分。
3. 包括屏幕截图 UI 时，只显示重要部分。 例如，在工具栏中讨论按钮时，请制作一个小图像，显示重要的工具栏按钮，但排除其周围的所有按钮。
4. 仅使用易于重现的图像。 这意味着不要将标记或突出显示绘制到屏幕截图中。 首先，没有一致的规则来说明这些规则的外观。 其次，重现此类屏幕截图需要额外的工作量。 请改为描述文本中的重要部分。 此规则存在例外情况，但它们很少见。
5. 显然，重新创建动画 GIF 的工作要多得多。 希望负责在一段时间结束之前重新创建它，或者希望人们放弃它（如果他们不想花费该时间）。
6. 将文章中的图像数保持在较低水平。 通常，一个好方法是制作一个工具的整体屏幕截图，其中显示了所有内容，然后以文本描述其余内容。 这样，必要时可以轻松替换屏幕截图。

其他一些方面：

- 屏幕截图的编辑器 UI 应使用浅灰色主题编辑器，因为并非所有用户都有权访问深色主题，我们希望尽可能保持一致。
- 默认图像宽度为 500 像素，因为在大多数监视器上显示效果良好。 尽量不要偏离太多。 最大宽度应为 800 像素。
- 对 UI 的屏幕截图使用 PNG。
- 将 PNG 或 JPG 用于 3D 视区屏幕截图。 首选质量，而首选压缩率。

### <a name="list-of-component-properties"></a>组件属性列表

记录属性列表时，请使用粗体文本突出显示属性名称，然后使用换行符和常规文本来描述它们。 请勿使用子章节或项目符号点列表。

此外，不要忘记用句点完成所有句子。

## <a name="page-completion-checklist"></a>页面完成清单

1. 确保遵循本文档的准则。
1. 浏览文档结构，看新文档能否在其他页面的 ["另请参阅](#see-also) "部分下提及。
1. 如果可用，请让了解主题证明的人阅读页面，了解技术正确性。
1. 让某人对页面进行样式和格式设置进行证明。 这可以是不熟悉该主题的人，这也是获取有关文档可理解性的反馈的一个好办法。

## <a name="source-documentation"></a>源文档

API 文档会从 MRTK 源文件自动生成。 为此，源文件需要包含以下内容：

- [类、结构、枚举摘要块](#class-struct-enum-summary-blocks)
- [属性、方法、事件摘要块](#property-method-event-summary-blocks)
- [功能简介版本和依赖项](#feature-introduction-version-and-dependencies)
- [序列化字段](#serialized-fields)
- [枚举值](#enumeration-values)

除了上述代码，还应对代码进行良好的注释，以便进行维护、bug 修复和轻松自定义。

### <a name="class-struct-enum-summary-blocks"></a>类、结构、枚举摘要块

如果将类、结构或枚举添加到 MRTK，则必须描述其用途。 这是以 类上方的摘要块的形式。

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

如果存在任何类级依赖项，应在摘要正下方的备注块中记录它们。

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

在未提供类、结构或枚举摘要的情况下提交的拉取请求不会获得批准。

### <a name="property-method-event-summary-blocks"></a>属性、方法、事件摘要块

无论代码可见性 (公共、专用、受保护和内部) ，都将使用摘要块记录 PMES (属性、方法和) 事件。 文档生成工具负责筛选和发布公共和受保护的功能。

注意：Unity 方法不需要摘要 **块** ， (唤醒、启动、更新) 。

批准拉 **取** 请求需要 PME 文档。

作为 PME 摘要块的一部分，参数和返回的数据的含义和用途是必需的。

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a>功能简介版本和依赖项

作为 API 摘要文档的一部分，有关引入该功能的 MRTK 版本以及任何依赖项的信息都应记录在备注块中。

依赖项应包括扩展和/或平台依赖项。

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a>序列化字段

最佳做法是使用 Unity 的工具提示属性为检查器中的脚本字段提供运行时文档。

为了在 API 文档中包含配置选项，脚本至少需要包含摘要块中的工具提示内容。

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a>枚举值

定义和枚举时，代码还必须使用摘要块记录枚举值的含义。 备注块可以选择用于提供更多详细信息以增强理解。

```c#
/// <summary>
/// Full range of human hearing.
/// </summary>
/// <remarks>
/// The frequency range used is a bit wider than that of human
/// hearing. It closely resembles the range used for audio CDs.
/// </remarks>
```

## <a name="how-to-documentation"></a>操作说明文档

混合现实Toolkit用户可能不需要使用 API 文档。 这些用户将利用我们预先构建的可重用预制组件和脚本来创建其体验。

每个功能区域将包含一个或多个 markdown (.md) 文件，这些文件在相当高级别描述提供的内容。 根据给定功能区域的大小和/或复杂性，可能需要其他文件，每个功能最多需要一个文件。

在将功能添加到 (或更改使用情况) ，必须提供概述文档。

作为本文档的一部分，应提供相关说明部分（包括插图）来帮助新了解功能或概念的客户入门。

## <a name="design-documentation"></a>设计文档

混合现实提供了一个创建新世界的机会。 其中一部分可能涉及创建用于 MRTK 的自定义资产。 为了尽可能使客户无冲突，组件应提供设计文档，描述任何格式设置或其他对艺术资产的要求。

设计文档可能有所帮助的一些示例：

- 游标模型
- 空间映射可视化效果
- 音效文件

强烈建议使用此类 **文档**，并可以在拉取请求评审中请求此类文档。

这可能与 MS 开发人员站点上的设计建议不同，也可能 [没有区别](/windows/mixed-reality/design)

## <a name="performance-notes"></a>性能说明

一些重要功能会花费性能成本。 通常，此代码将非常依赖于其配置方式。

例如：

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

建议对 CPU 和/或 GPU 繁重的组件使用性能说明，并且可能会作为拉取请求评审的一部分进行请求。 任何适用的性能注释都包含在 API **和** 概述文档中。

## <a name="breaking-changes"></a>中断性变更

重大更改文档是由顶级文件组成，该 [文件](../contributing/breaking-changes.md) 链接到每个功能区的单个 breaking-changes.md。

功能区 breaking-changes.md 文件包含给定版本的所有已知的重大更改的列表 **，** 以及来自过去版本的重大更改的历史记录。

例如：

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

功能级别 breaking-changes.md 文件中包含的信息将聚合到每个新 MRTK 版本的发行说明中。

任何属于更改的重大更改都 **必须** 记录为拉取请求的一部分。

## <a name="tools-for-editing-markdown"></a>用于编辑 MarkDown 的工具

[Visual Studio Code](https://code.visualstudio.com/)是一种很好的工具，用于编辑 MRTK 文档中的 markdown 文件。

编写文档时，还强烈建议安装以下两个扩展：

- 用于 Visual Studio Code 的文档 Markdown 扩展-使用 Alt + M 打开文档创作选项的菜单。

- 代码拼写检查器-将为拼写错误的单词加下划线。右键单击拼写错误的单词以对其进行更改或将其保存到字典中。

这两个包都打包在 Microsoft 发布的文档创作包中。

## <a name="see-also"></a>另请参阅

- [文档的示例 "另请参阅" 链接](https://www.microsoft.com)
