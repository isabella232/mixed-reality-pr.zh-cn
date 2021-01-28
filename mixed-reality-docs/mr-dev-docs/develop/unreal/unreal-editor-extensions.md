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
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584734"
---
# <a name="editor-extensions-in-unreal"></a>Unreal 中的编辑器扩展

Unreal 提供了一组广泛的功能，可让你根据需要自定义引擎。 这些功能涵盖从简单但受限的功能到非常强大但复杂的功能的各种功能。 以下步骤按复杂性递增顺序列出。 通常在解决问题时，应先寻找较简单的解决方案，在尝试完所有简单方法后，才转而寻求较复杂的方法。 例如，我们发现很多时候可以使用基本的构造脚本代替插件。 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a>构造脚本

可以使用构造脚本执行初始化操作，这些脚本会在创建蓝图实例时运行。

* [用户构造脚本](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [蓝图示例](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [视频教程](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a>已编写脚本的操作

已编写脚本的操作是编辑器实用工具蓝图。 可以通过以下操作在 Unreal 编辑器中启动它们：
* 右键单击内容浏览器中的“资产”
* 或右键单击“关卡视口”或“世界大纲视图”中的“角色”

已编写脚本的操作非常适合以下情况：需要“蓝图”逻辑来根据上下文了解“资产”或“角色”集。 通常，已编写脚本的操作会获得执行操作时选择的“资产”或“角色”的列表，然后修改这些对象或在其图形中考虑使用它们。

* [已编写脚本的操作](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [在项目启动时运行已编写脚本的操作](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a>编辑器实用工具小组件

如果想添加新的 UI 元素来修改 Unreal 编辑器的用户界面 (UI)，可以使用[编辑器实用工具小组件](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html)。 编辑器实用程序小组件基于 Unreal Motion Graphics (UMG)，因此可以在蓝图中像对其他任何 UMG 小组件蓝图一样设置小组件。

这些小组件专用于编辑器 UI，你可以使用它们创建自定义编辑器选项卡。 然后，可以像选择现有的编辑器选项卡一样从 Windows 菜单中选择这些自定义选项卡。

## <a name="plugins"></a>插件

通过 Unreal 可以开发和管理自己的自定义[插件](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html)，以与 UE4 工具和运行时搭配使用。 可以随时在 Unreal 编辑器中启用或禁用插件。 插件可以添加运行时游戏功能、修改内置引擎功能、新建文件类型以及扩展编辑器的功能。

<!-- ## Engine modifications -->

