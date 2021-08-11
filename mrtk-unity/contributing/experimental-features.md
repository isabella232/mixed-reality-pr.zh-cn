---
title: 实验性功能
description: 与 MRTK 中的实验性功能相关的文档。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 9b7ef7564e0e4f84ba70c034b1bcc33a29498432620a002c8509de518dde479c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228379"
---
# <a name="experimental-features"></a>实验性功能

MRTK 团队工作的一些功能似乎具有大量初始价值，即使我们尚未全面了解详细信息。 对于这些类型的功能，我们希望社区有机会尽早看到它们。 由于它们处于周期早期，因此我们将它们标记为实验性，以指示它们仍在不断发展，并且可能会随着时间的推移而发生变化。

## <a name="what-to-expect-from-an-experimental-feature"></a>试验性功能预期的结果

如果组件标记为实验性组件，可以预期以下各项：

- 演示用法的示例场景，位于 `MRTK/Examples/Experimental` 子文件夹下
- 实验性功能可能没有文档。
- 它们可能没有测试。
- 实验性功能可能会更改。

## <a name="experimental-feature-guidelines"></a>实验性功能指南

### <a name="experimental-code-should-live-in-a-separate-folder"></a>实验性代码应包含于单独的文件夹中

实验性代码应进入顶级实验文件夹，后跟实验性功能名称。 例如，如果尝试提供新功能 FooBar，请放入以下代码：

- 脚本进入的示例场景 `MRTK/Examples/Experimental/FooBar/`
- 组件脚本，预制件进入 `MRTK/SDK/Experimental/FooBar/`
- 组件检查器进入 `MRTK/SDK/Inspectors/Experimental/FooBar`

在实验性功能名称下使用子文件夹时，请尝试镜像 MRTK 的相同文件夹结构。

例如，求解器将 `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`

将场景放在靠近顶部的场景文件夹中： `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`

> [!NOTE]
> 我们考虑没有单个实验性根文件夹，而是将"实验性"放在 下面 `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` 。 我们决定在基础位置使用文件夹，使实验性功能更易于发现。

### <a name="experimental-code-should-be-in-a-special-namespace"></a>实验性代码应包含特殊命名空间

确保实验性代码位于与非实验性位置匹配的实验命名空间中。 例如，如果组件是 中的求解器的一部分， `Microsoft.MixedReality.Toolkit.Utilities.Solvers` 则其命名空间应为 `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` 。

有关 [示例，](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) 请参阅此 PR。

### <a name="experimental-features-should-have-an-experimental-attribute"></a>实验性功能应具有 [实验性] 属性

将属性添加到其中一个字段上方，使组件编辑器中出现一个小对话框，其中提到你的功能是实验性的， `[Experimental]` 并且可能会进行重大更改。

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a>实验性功能的菜单应转到"实验性"子菜单下

将命令添加到编辑器中的菜单时，请确保实验性功能在"实验性"子菜单下。 以下是一些示例：

添加顶级菜单命令：

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

添加组件菜单：

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a>文档

按照以下步骤为实验性功能添加文档：

1. 实验性功能的任何文档都应在实验 `readme.md` 性文件夹中的文件中。 例如，MRTK/SDK/Experimental/PulseShader/readme.md。

1. 在 *"功能概述"* 下，在 的实验 *部分添加* 链接 [`Documentation/toc.yml`](../toc.yml) 。

### <a name="minimize-impact-to-mrtk-code"></a>尽量减少对 MRTK 代码的影响

虽然 MRTK 更改可能会使试验正常工作，但它可能会以你期望的方式影响其他人。
对 MRTK 核心代码进行的任何回归都会导致拉取请求恢复。

旨在对除实验性文件夹外的文件夹进行零更改。 下面是可进行试验性更改的文件夹列表：

- MRTK/SDK/实验性
- MRTK/SDK/Inspectors/Experimental
- MRTK/Examples/Experimental

应谨慎处理这些文件夹之外的更改。 如果实验性功能必须包括对 MRTK 核心代码的更改，请考虑将 MRTK 更改拆分为包含测试和文档的单独拉取请求。

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a>使用实验性功能不应影响人们使用核心控件的能力

大多数人非常频繁地使用核心 UX 组件，如按钮、ManipulationHandler 和 Interactable。 如果阻止他们使用按钮，他们很可能不会使用实验性功能。

使用组件不应中断按钮、ManipulationHandler、BoundingBox 或可交互。

例如，在此[ScrollableObjectCollection PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001)中，添加 ScrollableObjectCollection 导致用户HoloLens按钮预制。 尽管这不是由 PR 代码中的 bug 引起的 (而是公开了现有的 bug) ，但它阻止了 PR 签入。

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a>提供演示如何使用该功能的示例场景

人们需要了解如何使用你的功能以及如何测试它。

在 MRTK/Examples/Experimental/YOUR_FEATURE

### <a name="minimize-user-visible-flaws-in-experimental-features"></a>最大程度地减少实验性功能中的用户可见缺陷

其他人不会使用实验性功能（如果它不起作用，它将不会成为一项功能）。

在目标平台上测试示例场景，确保它正常工作。 确保功能在编辑器中也正常工作，以便即使用户没有目标平台，也可以快速进行访问和查看功能。

## <a name="graduating-experimental-code-into-mrtk-code"></a>将实验性代码转换为 MRTK 代码

如果某个功能最终发现大量使用，则应该将该功能分为核心 MRTK 代码。 为此，该功能应具有测试、文档和示例场景。

准备好对 MRTK 功能进行分期时，请创建一个问题以签入 PR。 PR 应包括使此功能成为核心功能所需的全部内容：测试、文档和显示使用情况的示例场景。

此外，不要忘记更新命名空间以删除"实验性"子空间。
