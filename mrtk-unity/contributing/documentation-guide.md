---
title: 文档指南
description: 文档指南和 MRTK 标准。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 95af19b71a9fe06dabad058e75f78d951262ba4a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175349"
---
# <a name="documentation-guidelines"></a>文档指南

<img src="../features/images/MRTK_Logo_Rev.png" alt="MRTK">

本文档概述了混合现实和 MRTK Toolkit (的文档) 。 本文介绍文档编写和生成的技术方面，以突出显示常见缺陷，并描述建议的编写风格。

页面本身应用作示例，因此它使用文档的目标样式和最常见的标记功能。

- [Source](#source-documentation)
- [如何](#how-to-documentation)
- [设计](#design-documentation)
- [性能说明](#performance-notes)
- [重大更改](#breaking-changes)

---

## <a name="functionality-and-markup"></a>功能和标记

本部分介绍经常需要的功能。 若要了解它们如何工作，请参阅页面的源代码。

1. 编号列表
   1. 包含至少 3 个前导空格的嵌套编号列表
   1. 代码中的实际数字不相关;分析将负责设置正确的项号。

- 项目符号点列表
  - 嵌套项目符号点列表
- 带双 **星号** \* \* 的粗体文本\*\*
- _带下划线或_ 单个星号 \_ \_ 的 \* italic 文本\*
- 使用 `highlighted as code` 反引用 \` 的句子中的文本\`
- 文档页 [MRTK 文档指南的链接](documentation-guide.md)
- 指向 [页面中定位点的链接](#style);定位点通过用短划线替换空格并转换为小写来形成

对于代码示例，我们使用带三个反号的块，并 \` \` \` 指定 *csharp* 作为语法突出显示的语言：

```c#
int SampleFunction(int i)
{
   return i + 42;
}
```

在句子 中提及代码时 `use a single backtick` 。

### <a name="todos"></a>TODOS

避免在文档内使用 TODOS，因为随着时间的推移，这些 TODOS (如代码 TODOS) 往往累积并提供有关它们应如何更新以及丢失原因的信息。

如果绝对有必要添加 TODO，请执行以下步骤：

1. 在 Github 上提出一个新问题，描述 TODO 背后的上下文，并提供足够的背景信息供其他参与者理解并解决 TODO。
2. 在文档 todo 中引用问题 URL。

\<\!-- TODO[https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/ISSUE_NUMBER_HERE): A brief blurb on the issue --\>

### <a name="highlighted-sections"></a>突出显示的部分

若要突出显示读取器的特定点，请使用 *> [!NOTE]* 、 *> [!WARNING]* 和 *> [!IMPORTANT]* 生成以下样式。 建议仅对特殊相关情况使用常规点和警告/重要点的注释。

> [!NOTE]
> 备注示例

> [!WARNING]
> 警告示例

> [!IMPORTANT]
> 重要注释的示例

## <a name="page-layout"></a>页面布局

### <a name="introduction"></a>简介

主章节标题之后的部分应用作该章节的简短介绍。 不要使此标题太长，请改为添加子标题。 这些允许链接到部分，并可以另存为书签。

### <a name="main-body"></a>正文

使用两级和三级标题来构建其余部分。

**微型部分**

对应突出显示的块使用粗体文本行。我们在某些时候可能会将其替换为四级标题。

### <a name="see-also-section"></a>"另请参阅"部分

大多数页面应以名为"另请参阅"的 *章节结尾*。 本章只是指向与本主题相关的页面的链接的项目符号列表。 在适当时，这些链接也可能显示在页面文本中，但这不是必需的。 同样，页面文本可能包含指向与主主题不相关的页面的链接，这些链接不应包含在"另 *请参阅"* 列表中。 [有关选择链接的示例](#see-also)，请参阅此页的"另请参阅"一章。

## <a name="table-of-contents-toc"></a>目录 (TOC) 

Toc 文件用于生成 MRTK 文档文档中的 github.io 栏。
每当添加新的文档文件时，请确保文档文件夹的 toc.yml 文件之一中具有该文件的条目。 只有 toc 文件中列出的文章会显示在开发人员文档导航中。文档文件夹中每个子文件夹都可以有一个 toc 文件，该文件可链接到任何现有的 toc 文件，以将其作为子节添加到导航的相应部分。

## <a name="style"></a>Style

### <a name="writing-style"></a>写入样式

一般经验法则：尝试 **听起来专业**。 这通常意味着避免"对话语气"。 另请尝试避免双曲和唯一性。

1. 不要尝试过度 (或) 。
2. 从不编写"I"
3. 避免使用"we"。 通常可以使用"MRTK"轻松重新短语。 示例："我们支持此功能"->"MRTK 支持此功能"或"支持以下功能..."。
4. 同样，请尝试避免"你"。 示例："通过这个简单的更改，着色器变为可配置！" ->"着色器几乎可以配置。"
5. 请勿使用'sloppy phrases'。
6. 避免声音过于积极，我们不需要销售任何内容。
7. 同样，避免过于明显。 很少需要感叹号。

### <a name="capitalization"></a>大写

- 使用 **标题的句子大小写**。 即 将第一个字母和名称大写，但无其他内容。
- 对于其他所有内容，请使用常规英语。 这意味着 **不将任意字词大写**，即使它们具有该上下文中的特殊含义。 首选 *用于突出显示某些字词的 italic* 文本 [，请参阅下面的](#emphasis-and-highlighting)。
- 当链接嵌入句子中 (这是首选) ，标准章节名称始终使用大写字母，从而破坏文本中无任意大写的规则。 因此，使用自定义链接名称修复大写。 例如，下面是边界 [控件文档](../features/ux-building-blocks/bounds-control.md) 的链接。
- 将名称大写，例如 *Unity*。
- 编写 Unity 编辑器 时，请勿将 *"editor"大写*。

### <a name="emphasis-and-highlighting"></a>重点和突出显示

有两种方法可以强调或突出显示字词，即将其加粗或使其为 italic。 粗体文本的效果是，粗体文本会卡住，因此，在浏览一段文本时，甚至只是滚动一页，都很容易被注意到。 粗体可以突出显示人们应该记住的短语。 但是， **很少使用粗体文本**，因为它通常分散注意力。

通常，用户希望"分组"逻辑上属于一部分或突出显示特定术语，因为它具有特殊含义。 此类内容无需突出整体文本。 使用 italic 文本作为 *轻量级方法来* 突出显示某些内容。

同样，在文本中提及文件名、路径或菜单项时，最好使其在逻辑上进行分组，而不会分散注意力。

通常，请尝试 **避免不必要的文本突出显示**。 特殊术语可以突出显示一次，使读者知道，当它不再具有任何用途且只会分散注意力时，请不要在整个文本中重复此类突出显示。

### <a name="mentioning-menu-entries"></a>提及菜单条目

提及用户应单击的菜单项时，当前约定为：Project > *Files > Create > Leaf*

### <a name="links"></a>链接

尽可能多地插入其他页面的有用链接，但每个链接只需一次。 假设读者在页面上的每个链接上单击，并想要在同一页面打开20次的情况下，将其视为多么恼人。

首选句子中嵌入的链接：

- 糟糕：准则很有用。 有关详细信息，请参阅 [此章节](../contributing/documentation-guide.md) 。
- 好： [准则](documentation-guide.md) 很有用。

避免外部链接，它们可能会过时或包含版权内容。

添加链接时，请考虑是否还应该在 " [另请参阅](#see-also) " 部分中列出。 同样，请检查是否应将指向新页的链接添加到链接到页中。

### <a name="images--screenshots"></a>图像/屏幕截图

**请慎用屏幕截图。** 维护文档中的图像是很多工作，小型 UI 更改会使大量屏幕截图过时。 以下规则将减少维护工作量：

1. 不要将屏幕截图用于文本中描述的内容。 尤其是， **绝不会显示属性网格** ，只是为了显示属性名称和值。
2. 不要在屏幕截图中包括与显示内容无关的内容。 例如，显示呈现效果时，会显示视区的屏幕截图，但排除围绕它的任何 UI。 显示某些 UI，尝试移动窗口，使其绕过该重要部分。
3. 包括屏幕截图 UI 时，仅显示重要部分。 例如，在讨论工具栏中的按钮时，请创建一个显示重要工具栏按钮的小图像，但是排除它周围的所有内容。
4. 仅使用容易再现的映像。 这意味着不会在屏幕截图中绘制标记或突出显示内容。 首先，没有一致的规则，这些规则的外观始终是如此。 其次，重现此类屏幕截图是额外的工作。 相反，请在文本中描述重要部分。 此规则有例外，但很少发生。
5. 很明显，重新创建动画 GIF 要多得多。 希望在结束时间结束后再重新创建该程序，如果他们不想花时间，则应将其放弃。
6. 使项目中的图像数量保持较低。 通常，一种很好的方法是使一个工具的整个屏幕截图，其中显示所有内容，然后在文本中描述其余内容。 这样就可以在需要时轻松替换屏幕截图。

其他一些方面：

- 用于屏幕截图的编辑器 UI 应使用浅灰色主题编辑器，因为并非所有用户都有权访问深色主题，因此，我们希望尽可能使其保持一致。
- 默认图像宽度为500像素，因为这很适合大多数监视器。 不要与它有太大的不同。 800像素宽度应为最大值。
- 使用 Png 为 UI 的屏幕截图。
- 将 Png 或 JPGs 用于3D 视区屏幕截图。 优于压缩比。

### <a name="list-of-component-properties"></a>组件属性列表

记录属性列表时，请使用粗体文本突出显示属性名称，然后使用换行符和常规文本对其进行描述。 不要使用子章节或项目符号列表。

此外，请不要忘记以句点结束所有句子。

## <a name="page-completion-checklist"></a>页面完成清单

1. 确保遵循本文档的指导原则。
1. 浏览文档结构，并查看是否可以在其他页面的 " [另请参阅](#see-also) " 部分下提及新文档。
1. 如果可用，请对主题进行校对-阅读有关技术正确性的页面。
1. 让别人对样式和格式的页面进行校对。 这可能是与主题不熟悉的人，这也是获得文档理解方式的反馈的一个好主意。

## <a name="source-documentation"></a>源文档

将从 MRTK 源文件中自动生成 API 文档。 为了便于实现此操作，源文件需要包含以下内容：

- [类、结构、枚举摘要块](#class-struct-enum-summary-blocks)
- [属性、方法、事件摘要块](#property-method-event-summary-blocks)
- [功能简介版本和依赖关系](#feature-introduction-version-and-dependencies)
- [序列化的字段](#serialized-fields)
- [枚举值](#enumeration-values)

除了上述代码外，还应对代码进行很好的注释，以便进行维护、bug 修复和简化自定义。

### <a name="class-struct-enum-summary-blocks"></a>类、结构、枚举摘要块

如果要将类、结构或枚举添加到 MRTK 中，则必须对其目的进行说明。 这将采用类之上的摘要块的形式。

```c#
/// <summary>
/// AudioOccluder implements IAudioInfluencer to provide an occlusion effect.
/// </summary>
```

如果有任何类级别的依赖项，它们应该记录在注释块中，紧靠在摘要的下方。

```c#
/// <remarks>
/// Ensure that all sound emitting objects have an attached AudioInfluencerController.
/// Failing to do so will result in the desired effect not being applied to the sound.
/// </remarks>
```

不会批准在类、结构或枚举没有汇总的情况下提交的拉取请求。

### <a name="property-method-event-summary-blocks"></a>属性、方法、事件摘要块

属性、方法和事件 (PMEs) 以及字段将与摘要块一起记录，而不考虑 (公共、私有、受保护和内部) 的代码可见性。 文档生成工具负责仅筛选和发布公共和受保护的功能。

注意： Unity 方法 **不** 需要摘要块 (例如：唤醒、启动、更新) 。

**需要** 使用 PME 文档才能获得批准请求。

作为 PME 摘要块的一部分，需要使用参数的含义和用途和返回的数据。

```c#
/// <summary>
/// Sets the cached native cutoff frequency of the attached low pass filter.
/// </summary>
/// <param name="frequency">The new low pass filter cutoff frequency.</param>
/// <returns>The new cutoff frequency value.</returns>
```

### <a name="feature-introduction-version-and-dependencies"></a>功能简介版本和依赖关系

作为 API 摘要文档的一部分，有关引入此功能的 MRTK 版本的信息以及所有依赖项都应记录在备注块中。

依赖关系应包括扩展和/或平台依赖项。

```c#
/// <remarks>
/// Introduced in MRTK version: 2018.06.0
/// Minimum Unity version: 2018.0.0f1
/// Minimum Operating System: Windows 10.0.11111.0
/// Requires installation of: ImaginarySDK v2.1
/// </remarks>
```

### <a name="serialized-fields"></a>序列化的字段

最好在检查器中使用 Unity 的 tooltip 特性来提供脚本字段的运行时文档。

为了使配置选项包含在 API 文档中，脚本需要 *至少* 在摘要块中包含工具提示内容。

```c#
/// <summary>
/// The quality level of the simulated audio source (ex: AM radio).
/// </summary>
[Tooltip("The quality level of the simulated audio source.")]
```

### <a name="enumeration-values"></a>枚举值

在定义和枚举时，代码还必须使用 summary 块记录枚举值的含义。 可以选择使用备注块来提供更多详细信息以增强理解。

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

许多混合现实 Toolkit 的用户可能不需要使用 API 文档。 这些用户将利用我们提供的可重复使用的 prototyping 和脚本来创建自己的体验。

每个功能区域都包含一个或多个 markdown ( md) 文件，这些文件在相当高的级别描述，提供了什么。 根据给定功能区域的大小和/或复杂性，可能需要其他文件，每个功能最多有一个。

添加功能后 (或更改用法) ，必须提供概述文档。

在本文档中，应提供 "操作说明" 部分（包括说明），以帮助客户在入门中熟悉某个功能或概念。

## <a name="design-documentation"></a>设计文档

混合现实为创建全新的世界提供了机会。 部分原因可能涉及创建自定义资产，以便与 MRTK 一起使用。 为了使客户能够免费实现此要求，组件应提供描述任何格式或其他对作品资产的要求的设计文档。

设计文档可能有帮助的一些示例：

- 游标模型
- 空间映射可视化效果
- 声音效果文件

**强烈** 建议使用这种类型的文档，并且 **可能** 会在拉取请求评审过程中请求此类文档。

这不一定与[MS 开发人员网站](/windows/mixed-reality/design)上的设计建议有所不同

## <a name="performance-notes"></a>性能说明

一些重要的功能以性能为代价。 通常，此代码的配置取决于其配置方式。

例如：

```md
When using the spatial mapping component, the performance impact will increase with the level of detail requested.  
It is recommended to use the least detail possible for the desired experience.
```

建议将性能说明用于 CPU 和/或 GPU 繁重的组件 **，并在** 拉取请求检查过程中请求。 API 和概述文档中将包含任何 **适用的性能** 说明。

## <a name="breaking-changes"></a>中断性变更

中断性变更文档包含一个 [顶级文件，](../contributing/breaking-changes.md) 该文件链接到每个功能区的单个 breaking-changes.md。

文件 breaking-changes.md 区域是包含给定版本的所有已知中断性变更的列表，以及过去版本中中断性变更的历史记录。

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

功能级别中包含的信息 breaking-changes.md 文件将聚合到每个新 MRTK 发布的发行说明中。

任何属于更改的中断性变更 **都必须** 记录为拉取请求的一部分。

## <a name="tools-for-editing-markdown"></a>用于编辑 MarkDown 的工具

[Visual Studio Code](https://code.visualstudio.com/)是一个很好的工具，用于编辑属于 MRTK 文档的 Markdown 文件。

编写文档时，强烈建议安装以下两个扩展：

- Docs Markdown 扩展Visual Studio Code - 使用 Alt+M 打开文档创作选项菜单。

- 代码拼写检查器 - 拼写错误的单词将带有下划线;右键单击拼写错误的单词以将其更改或保存到字典中。

这两者都打包在 Microsoft 发布的 Docs 创作包中。

## <a name="see-also"></a>另请参阅

- [文档的示例"另请参阅"链接](https://www.microsoft.com)
