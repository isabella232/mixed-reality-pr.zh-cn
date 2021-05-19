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
# <a name="dependency-window"></a><span data-ttu-id="e56aa-104">"依赖项"窗口</span><span class="sxs-lookup"><span data-stu-id="e56aa-104">Dependency window</span></span>

<span data-ttu-id="e56aa-105">在 Unity 中，通常很难发现哪些资产被使用，以及引用哪些资产。</span><span class="sxs-lookup"><span data-stu-id="e56aa-105">In Unity, it is often difficult to gleam which assets are being used, and what is referencing them.</span></span> <span data-ttu-id="e56aa-106">"在场景中查找引用"选项非常适用于仅关注当前场景，但整个 Unity 项目呢？</span><span class="sxs-lookup"><span data-stu-id="e56aa-106">The "Find References in Scene" option works great when you are only concerned with the current scene, but what about your entire Unity project?</span></span> <span data-ttu-id="e56aa-107">在这种情况下，依赖关系 **窗口 (** Assets/MRTK/Tools/DependencyWindow) 非常有用。</span><span class="sxs-lookup"><span data-stu-id="e56aa-107">This is where the **Dependency Window** (Assets/MRTK/Tools/DependencyWindow) can be useful.</span></span>

<span data-ttu-id="e56aa-108">"依赖关系窗口"显示资产如何相互引用和依赖。</span><span class="sxs-lookup"><span data-stu-id="e56aa-108">The Dependency Window displays how assets reference and depend on each other.</span></span> <span data-ttu-id="e56aa-109">依赖项是通过分析项目 YAML 文件内的 guid (，请注意，脚本依赖项脚本不被视为) 。</span><span class="sxs-lookup"><span data-stu-id="e56aa-109">Dependencies are calculated by parsing guids within project YAML files (note, script to script dependencies are not considered).</span></span>

## <a name="usage"></a><span data-ttu-id="e56aa-110">使用情况</span><span class="sxs-lookup"><span data-stu-id="e56aa-110">Usage</span></span>

<span data-ttu-id="e56aa-111">若要打开该窗口，请选择" *混合现实工具包>Utilities->依赖项窗口* "，这将打开该窗口并自动开始生成项目的依赖项关系图。</span><span class="sxs-lookup"><span data-stu-id="e56aa-111">To open the window, select *Mixed Reality Toolkit->Utilities->Dependency Window* which will open the window and automatically begin building your project's dependency graph.</span></span> <span data-ttu-id="e56aa-112">生成依赖项关系图后，可以在项目选项卡中选择资产以检查其依赖项。</span><span class="sxs-lookup"><span data-stu-id="e56aa-112">Once the dependency graph is built, you can select assets in the project tab to inspect their dependencies.</span></span>

!["依赖项"窗口](../images/dependency-window/MRTK_Dependency_Window.png)

<span data-ttu-id="e56aa-114">该窗口显示当前所选资产所依赖的资产列表，以及依赖它的资产的层次结构列表。</span><span class="sxs-lookup"><span data-stu-id="e56aa-114">The window displays a list of assets that the currently selected asset depends on, and a hierarchical list of assets that depend on it.</span></span> <span data-ttu-id="e56aa-115">如果没有任何内容依赖于当前选择的资产，可以考虑从项目中删除它 (请注意，某些资产通过着色器.Find () 等 API 以编程方式加载，并且可能无法由依赖项跟踪器) 捕获。</span><span class="sxs-lookup"><span data-stu-id="e56aa-115">If nothing depends on the currently selected asset, you can consider deleting it from your project (note that some assets are loaded programmatically via APIs like Shader.Find() and may not be caught by the dependency tracker).</span></span>

<span data-ttu-id="e56aa-116">该窗口还可以仅显示未由任何其他资产引用且可考虑删除的所有资产的列表：</span><span class="sxs-lookup"><span data-stu-id="e56aa-116">The window can also display just a list of all assets which are not referenced by any other assets and could be considered for deletion:</span></span>

![显示未引用资产的依赖项窗口](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> <span data-ttu-id="e56aa-118">如果在依赖关系窗口使用期间修改、添加或删除资产，建议刷新依赖项关系图，以获得最佳"最新"结果。</span><span class="sxs-lookup"><span data-stu-id="e56aa-118">If assets are modified, added, or removed while the dependency window is in use, it is advised to refresh the dependency graph for the most "up to date" results.</span></span>
