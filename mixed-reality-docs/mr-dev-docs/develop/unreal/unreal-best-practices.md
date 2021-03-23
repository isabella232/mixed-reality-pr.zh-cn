---
title: 一般最佳实践
description: 了解有关在 Unreal 引擎中开发混合现实应用程序的所有推荐最佳做法的最新信息。
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, 编辑器扩展, Unreal 编辑器, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 文档, 指南, 功能, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 移植, 升级
ms.openlocfilehash: 478ae3137fc73d1ef516087618ab0247f2164c02
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2021
ms.locfileid: "98584731"
---
# <a name="general-best-practices"></a>一般最佳实践

以下是一些通用的最佳做法，建议所有开发人员在为混合现实创建 Unreal Engine 项目时遵循。

## <a name="constructors"></a>构造函数

如果需要在蓝图中使用“构造函数”的等效项，请使用 Unreal 的[构造脚本](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)。 相较于使用“BeginPlay”事件，使用该构造脚本的主要优势是构造脚本也在“编辑器”中运行。 大多数情况下，可以在启动时甚至编译时缓存值。

> [!NOTE]
> 可以在[编辑器扩展概述](unreal-editor-extensions.md#construction-scripts)中找到有关构建脚本的更多支持信息。

## <a name="3d-buttons-and-textures"></a>3D 按钮和纹理

在混合现实应用程序中进行创建或计划使用 3D 按钮时，自然要考虑性能。 但并非所有内容都必须由网格制成才能被视为 3D。 可以选择使用 Paper2D 并精心制作纹理来实现 3D 外观。 这非常适用于“看似”3D 但实则是四边形上经 photoshop 处理过的图片的按钮。 它们的一个精美版本称为 [sprite](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html)。

## <a name="variants"></a>变量

在运行时创建具有多个对象配置的场景时，请使用 [Unreal 变体](https://docs.unrealengine.com/Basics/Levels/Variants/index.html)。 变体可以包括不断变化的材料或网格。 

## <a name="animation"></a>动画

如果要创建大量“可交互的动画”，请使用 [Spline 组件](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html)（而不是 Spline“网格”组件）和[时间线节点](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html)。 

<!-- You can find a comprehensive [video tutorial here](https://www.youtube.com/watch?v=bWXI91FdMtk&ab_channel=DoubleCrossGames). -->

## <a name="communications"></a>通信

如果在动态查找对象时或使用过多带宽在多个角色和蓝图之间进行通信时遇到麻烦，请使用[关卡蓝图](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html)。 请记住，Unreal Engine 4 与 Unity 不同，并非所有内容都必须位于组件内部。 关卡蓝图是简化多个角色之间通信的非常有效的推荐方法。 在关卡蓝图的 OnBeginPlay 中，甚至可以在启动时“缓存”对象引用。

## <a name="global-state"></a>全局状态

通常需要存储特定于关卡的状态，例如分数、关卡数据、特定于玩家的信息或不完全属于特定对象的任何其他内容。 请勿忽略 [GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html)。 大多数人都忘记了它的存在，但是 GameMode 可以在每个关卡创建，并包含特定于每个关卡的数据。

## <a name="optimizing-blueprints"></a>优化蓝图

如果发现自己的蓝图太慢，请在用 c++ 重写代码前，先让 Unreal 将蓝图“本地化”。 创建自己的自定义解决方案前，请先尝试使用自动[本地化](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html)。

![蓝图设置，其中突出显示了蓝图本地化方法](images/unreal-general-practices-img-01.jpg)
