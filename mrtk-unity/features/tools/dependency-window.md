---
title: 依赖关系窗口
description: 有关 MRTK 中依赖项窗口使用情况的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 22ecbb09ebf759e15f1f21085a7b7696cb24bc6e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144447"
---
# <a name="dependency-window"></a>"依赖项"窗口

在 Unity 中，通常很难发现哪些资产被使用，以及引用哪些资产。 "在场景中查找引用"选项非常适用于仅关注当前场景，但整个 Unity 项目呢？ 在这种情况下，依赖关系 **窗口 (** Assets/MRTK/Tools/DependencyWindow) 非常有用。

"依赖关系窗口"显示资产如何相互引用和依赖。 依赖项是通过分析项目 YAML 文件内的 guid (，请注意，脚本依赖项脚本不被视为) 。

## <a name="usage"></a>使用情况

若要打开该窗口，请选择" *混合现实工具包>Utilities->依赖项窗口* "，这将打开该窗口并自动开始生成项目的依赖项关系图。 生成依赖项关系图后，可以在项目选项卡中选择资产以检查其依赖项。

!["依赖项"窗口](../images/dependency-window/MRTK_Dependency_Window.png)

该窗口显示当前所选资产所依赖的资产列表，以及依赖它的资产的层次结构列表。 如果没有任何内容依赖于当前选择的资产，可以考虑从项目中删除它 (请注意，某些资产通过着色器.Find () 等 API 以编程方式加载，并且可能无法由依赖项跟踪器) 捕获。

该窗口还可以仅显示未由任何其他资产引用且可考虑删除的所有资产的列表：

![显示未引用资产的依赖项窗口](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> 如果在依赖关系窗口使用期间修改、添加或删除资产，建议刷新依赖项关系图，以获得最佳"最新"结果。
