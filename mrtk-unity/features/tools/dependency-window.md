---
title: 依赖项窗口
description: 有关 MRTK 中的依赖项窗口用法的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 590476add6904f76081630c4416184bea9f694ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176662"
---
# <a name="dependency-window"></a>依赖项窗口

在 Unity 中，通常很难 gleam 正在使用哪些资产，以及引用它们的资产。 如果你只关心当前场景，但你的整个 Unity 项目如何，则 "在场景中查找引用" 选项非常有用？ 在这种情况下， **依赖关系窗口** (资产/MRTK/Tools/DependencyWindow) 会很有用。

"依赖关系" 窗口显示资产引用方式，并依赖于其他资产。 依赖关系是通过分析项目 YAML 文件中的 guid 来计算 (注意，脚本到脚本的依赖项不会被视为) 。

## <a name="usage"></a>使用情况

若要打开该窗口，请选择 "**混合现实**  >  **Toolkit**  >  **实用工具**  >  **依赖关系窗口**，该窗口将打开窗口并自动开始生成项目的依赖项关系图。 生成依赖项关系图后，可以在 "项目" 选项卡中选择 "资产" 来检查其依赖项。

![依赖项窗口](../images/dependency-window/MRTK_Dependency_Window.png)

此窗口将显示当前所选资产依赖的资产的列表，以及依赖于它的资产的层次结构列表。 如果没有任何内容依赖于当前所选的资产，则可以考虑将其从项目中删除 (请注意，某些资产是通过诸如着色器之类的 Api 以编程方式加载的。查找 () ，而不会被依赖关系跟踪器) 捕获。

该窗口还可以只显示所有其他资产未引用的资产的列表，并且可以将其视为删除：

![显示未引用资产的依赖项窗口](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> 如果在依赖项窗口正在使用时修改、添加或删除了资产，则建议刷新依赖项关系图，了解最新的结果。
