---
title: Unreal 中的编辑器扩展
description: 了解如何使用自定义脚本、脚本操作和实用程序小组件扩展 Unreal 引擎编辑器。
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, 编辑器扩展, Unreal 编辑器, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 文档, 指南, 功能, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 移植, 升级
ms.openlocfilehash: ee0ba5d1d60b83dc334204e12283c76a877b4ec8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "98584734"
---
# <a name="editor-extensions-in-unreal"></a><span data-ttu-id="41ede-104">Unreal 中的编辑器扩展</span><span class="sxs-lookup"><span data-stu-id="41ede-104">Editor extensions in Unreal</span></span>

<span data-ttu-id="41ede-105">Unreal 提供了一组广泛的功能，可让你根据需要自定义引擎。</span><span class="sxs-lookup"><span data-stu-id="41ede-105">Unreal provides an extensive set of features that allow you to customize the engine to your needs.</span></span> <span data-ttu-id="41ede-106">这些功能涵盖从简单但受限的功能到非常强大但复杂的功能的各种功能。</span><span class="sxs-lookup"><span data-stu-id="41ede-106">The features range from simple but limited, to very powerful but complex.</span></span> <span data-ttu-id="41ede-107">以下步骤按复杂性递增顺序列出。</span><span class="sxs-lookup"><span data-stu-id="41ede-107">The following steps are listed in order of increasing complexity.</span></span> <span data-ttu-id="41ede-108">通常在解决问题时，应先寻找较简单的解决方案，在尝试完所有简单方法后，才转而寻求较复杂的方法。</span><span class="sxs-lookup"><span data-stu-id="41ede-108">In general, you should reach for simpler solutions to your problem, and exhausting its options, before moving to a more complex option.</span></span> <span data-ttu-id="41ede-109">例如，我们发现很多时候可以使用基本的构造脚本代替插件。</span><span class="sxs-lookup"><span data-stu-id="41ede-109">As an example, we have found that the basic Construction Script can be used in lieu of plugins most of the time.</span></span> 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a><span data-ttu-id="41ede-110">构造脚本</span><span class="sxs-lookup"><span data-stu-id="41ede-110">Construction scripts</span></span>

<span data-ttu-id="41ede-111">可以使用构造脚本执行初始化操作，这些脚本会在创建蓝图实例时运行。</span><span class="sxs-lookup"><span data-stu-id="41ede-111">You can use construction scripts to perform initialization actions, which run when Blueprint instance are created.</span></span>

* [<span data-ttu-id="41ede-112">用户构造脚本</span><span class="sxs-lookup"><span data-stu-id="41ede-112">User Constructions script</span></span>](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [<span data-ttu-id="41ede-113">蓝图示例</span><span class="sxs-lookup"><span data-stu-id="41ede-113">Blueprint example</span></span>](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [<span data-ttu-id="41ede-114">视频教程</span><span class="sxs-lookup"><span data-stu-id="41ede-114">Video tutorial</span></span>](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a><span data-ttu-id="41ede-115">已编写脚本的操作</span><span class="sxs-lookup"><span data-stu-id="41ede-115">Scripted actions</span></span>

<span data-ttu-id="41ede-116">已编写脚本的操作是编辑器实用工具蓝图。</span><span class="sxs-lookup"><span data-stu-id="41ede-116">Scripted Actions are Editor Utility Blueprints.</span></span> <span data-ttu-id="41ede-117">可以通过以下操作在 Unreal 编辑器中启动它们：</span><span class="sxs-lookup"><span data-stu-id="41ede-117">You can launch them in the Unreal Editor by:</span></span>
* <span data-ttu-id="41ede-118">右键单击内容浏览器中的“资产”</span><span class="sxs-lookup"><span data-stu-id="41ede-118">Right-clicking **Assets** in the Content Browser</span></span>
* <span data-ttu-id="41ede-119">或右键单击“关卡视口”或“世界大纲视图”中的“角色”</span><span class="sxs-lookup"><span data-stu-id="41ede-119">Or by right-clicking **Actors** either in the Level Viewport or in the World Outliner</span></span>

<span data-ttu-id="41ede-120">已编写脚本的操作非常适合以下情况：需要“蓝图”逻辑来根据上下文了解“资产”或“角色”集。</span><span class="sxs-lookup"><span data-stu-id="41ede-120">Scripted Actions are uniquely suited for times when you need your Blueprint logic to have contextual awareness about sets of Assets or Actors.</span></span> <span data-ttu-id="41ede-121">通常，已编写脚本的操作会获得执行操作时选择的“资产”或“角色”的列表，然后修改这些对象或在其图形中考虑使用它们。</span><span class="sxs-lookup"><span data-stu-id="41ede-121">Typically, a Scripted Action gets a list of Assets or Actors that you've selected when the action is executed, then modifies those objects or considers them in its graph.</span></span>

* [<span data-ttu-id="41ede-122">已编写脚本的操作</span><span class="sxs-lookup"><span data-stu-id="41ede-122">Scripted Actions</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [<span data-ttu-id="41ede-123">在项目启动时运行已编写脚本的操作</span><span class="sxs-lookup"><span data-stu-id="41ede-123">Running scripted actions on project startup</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a><span data-ttu-id="41ede-124">编辑器实用工具小组件</span><span class="sxs-lookup"><span data-stu-id="41ede-124">Editor utility widgets</span></span>

<span data-ttu-id="41ede-125">如果想添加新的 UI 元素来修改 Unreal 编辑器的用户界面 (UI)，可以使用[编辑器实用工具小组件](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html)。</span><span class="sxs-lookup"><span data-stu-id="41ede-125">You can use [Editor Utility Widgets](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) anytime you want to add new UI elements to modify the User Interface (UI) of the Unreal Editor.</span></span> <span data-ttu-id="41ede-126">编辑器实用程序小组件基于 Unreal Motion Graphics (UMG)，因此可以在蓝图中像对其他任何 UMG 小组件蓝图一样设置小组件。</span><span class="sxs-lookup"><span data-stu-id="41ede-126">Editor Utility Widgets are based on Unreal Motion Graphics (UMG), so you can set up Widgets in a Blueprint like you would for any other UMG Widget Blueprint.</span></span>

<span data-ttu-id="41ede-127">这些小组件专用于编辑器 UI，你可以使用它们创建自定义编辑器选项卡。</span><span class="sxs-lookup"><span data-stu-id="41ede-127">These Widgets are specifically for the Editor UI, and you can use them to create custom Editor tabs.</span></span> <span data-ttu-id="41ede-128">然后，可以像选择现有的编辑器选项卡一样从 Windows 菜单中选择这些自定义选项卡。</span><span class="sxs-lookup"><span data-stu-id="41ede-128">You can then select these custom tabs from the Windows menu, like you would select existing Editor tabs.</span></span>

## <a name="plugins"></a><span data-ttu-id="41ede-129">插件</span><span class="sxs-lookup"><span data-stu-id="41ede-129">Plugins</span></span>

<span data-ttu-id="41ede-130">通过 Unreal 可以开发和管理自己的自定义[插件](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html)，以与 UE4 工具和运行时搭配使用。</span><span class="sxs-lookup"><span data-stu-id="41ede-130">Unreal lets you develop and manage your own custom [plugins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) for use with UE4 tools and runtime.</span></span> <span data-ttu-id="41ede-131">可以随时在 Unreal 编辑器中启用或禁用插件。</span><span class="sxs-lookup"><span data-stu-id="41ede-131">You can enable or disable your plugins at any time in the Unreal Editor.</span></span> <span data-ttu-id="41ede-132">插件可以添加运行时游戏功能、修改内置引擎功能、新建文件类型以及扩展编辑器的功能。</span><span class="sxs-lookup"><span data-stu-id="41ede-132">Plugins can add runtime gameplay functionality, modify built-in Engine features, create new file types, and extend the capabilities of the Editor.</span></span>

<!-- ## Engine modifications -->

