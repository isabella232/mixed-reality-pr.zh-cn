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
# <a name="dependency-window"></a><span data-ttu-id="c31f7-104">依赖项窗口</span><span class="sxs-lookup"><span data-stu-id="c31f7-104">Dependency window</span></span>

<span data-ttu-id="c31f7-105">在 Unity 中，通常很难 gleam 正在使用哪些资产，以及引用它们的资产。</span><span class="sxs-lookup"><span data-stu-id="c31f7-105">In Unity, it is often difficult to gleam which assets are being used, and what is referencing them.</span></span> <span data-ttu-id="c31f7-106">如果你只关心当前场景，但你的整个 Unity 项目如何，则 "在场景中查找引用" 选项非常有用？</span><span class="sxs-lookup"><span data-stu-id="c31f7-106">The "Find References in Scene" option works great when you are only concerned with the current scene, but what about your entire Unity project?</span></span> <span data-ttu-id="c31f7-107">在这种情况下， **依赖关系窗口** (资产/MRTK/Tools/DependencyWindow) 会很有用。</span><span class="sxs-lookup"><span data-stu-id="c31f7-107">This is where the **Dependency Window** (Assets/MRTK/Tools/DependencyWindow) can be useful.</span></span>

<span data-ttu-id="c31f7-108">"依赖关系" 窗口显示资产引用方式，并依赖于其他资产。</span><span class="sxs-lookup"><span data-stu-id="c31f7-108">The Dependency Window displays how assets reference and depend on each other.</span></span> <span data-ttu-id="c31f7-109">依赖关系是通过分析项目 YAML 文件中的 guid 来计算 (注意，脚本到脚本的依赖项不会被视为) 。</span><span class="sxs-lookup"><span data-stu-id="c31f7-109">Dependencies are calculated by parsing guids within project YAML files (note, script to script dependencies are not considered).</span></span>

## <a name="usage"></a><span data-ttu-id="c31f7-110">使用情况</span><span class="sxs-lookup"><span data-stu-id="c31f7-110">Usage</span></span>

<span data-ttu-id="c31f7-111">若要打开该窗口，请选择 "**混合现实**  >  **Toolkit**  >  **实用工具**  >  **依赖关系窗口**，该窗口将打开窗口并自动开始生成项目的依赖项关系图。</span><span class="sxs-lookup"><span data-stu-id="c31f7-111">To open the window, select **Mixed Reality** > **Toolkit** > **Utilities** > **Dependency Window** which will open the window and automatically begin building your project's dependency graph.</span></span> <span data-ttu-id="c31f7-112">生成依赖项关系图后，可以在 "项目" 选项卡中选择 "资产" 来检查其依赖项。</span><span class="sxs-lookup"><span data-stu-id="c31f7-112">Once the dependency graph is built, you can select assets in the project tab to inspect their dependencies.</span></span>

![依赖项窗口](../images/dependency-window/MRTK_Dependency_Window.png)

<span data-ttu-id="c31f7-114">此窗口将显示当前所选资产依赖的资产的列表，以及依赖于它的资产的层次结构列表。</span><span class="sxs-lookup"><span data-stu-id="c31f7-114">The window displays a list of assets that the currently selected asset depends on, and a hierarchical list of assets that depend on it.</span></span> <span data-ttu-id="c31f7-115">如果没有任何内容依赖于当前所选的资产，则可以考虑将其从项目中删除 (请注意，某些资产是通过诸如着色器之类的 Api 以编程方式加载的。查找 () ，而不会被依赖关系跟踪器) 捕获。</span><span class="sxs-lookup"><span data-stu-id="c31f7-115">If nothing depends on the currently selected asset, you can consider deleting it from your project (note that some assets are loaded programmatically via APIs like Shader.Find() and may not be caught by the dependency tracker).</span></span>

<span data-ttu-id="c31f7-116">该窗口还可以只显示所有其他资产未引用的资产的列表，并且可以将其视为删除：</span><span class="sxs-lookup"><span data-stu-id="c31f7-116">The window can also display just a list of all assets which are not referenced by any other assets and could be considered for deletion:</span></span>

![显示未引用资产的依赖项窗口](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> <span data-ttu-id="c31f7-118">如果在依赖项窗口正在使用时修改、添加或删除了资产，则建议刷新依赖项关系图，了解最新的结果。</span><span class="sxs-lookup"><span data-stu-id="c31f7-118">If assets are modified, added, or removed while the dependency window is in use, it is advised to refresh the dependency graph for the most "up to date" results.</span></span>
