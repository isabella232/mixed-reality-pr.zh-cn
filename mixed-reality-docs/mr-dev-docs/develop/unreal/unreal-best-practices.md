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
# <a name="general-best-practices"></a><span data-ttu-id="46ee3-104">一般最佳实践</span><span class="sxs-lookup"><span data-stu-id="46ee3-104">General best practices</span></span>

<span data-ttu-id="46ee3-105">以下是一些通用的最佳做法，建议所有开发人员在为混合现实创建 Unreal Engine 项目时遵循。</span><span class="sxs-lookup"><span data-stu-id="46ee3-105">The following are some general best practices we recommend all developers follow when creating an Unreal Engine project for Mixed Reality.</span></span>

## <a name="constructors"></a><span data-ttu-id="46ee3-106">构造函数</span><span class="sxs-lookup"><span data-stu-id="46ee3-106">Constructors</span></span>

<span data-ttu-id="46ee3-107">如果需要在蓝图中使用“构造函数”的等效项，请使用 Unreal 的[构造脚本](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)。</span><span class="sxs-lookup"><span data-stu-id="46ee3-107">If you need the equivalent of a "constructor" in blueprints, use Unreals' [construction script](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html).</span></span> <span data-ttu-id="46ee3-108">相较于使用“BeginPlay”事件，使用该构造脚本的主要优势是构造脚本也在“编辑器”中运行。</span><span class="sxs-lookup"><span data-stu-id="46ee3-108">The primary advantage over using "BeginPlay" events is the constructor script runs in the "editor" as well.</span></span> <span data-ttu-id="46ee3-109">大多数情况下，可以在启动时甚至编译时缓存值。</span><span class="sxs-lookup"><span data-stu-id="46ee3-109">Most of the time the values can be cached right at the start or even at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="46ee3-110">可以在[编辑器扩展概述](unreal-editor-extensions.md#construction-scripts)中找到有关构建脚本的更多支持信息。</span><span class="sxs-lookup"><span data-stu-id="46ee3-110">You can find more supporting information for Construction scripts in our [editor extensions overview](unreal-editor-extensions.md#construction-scripts).</span></span>

## <a name="3d-buttons-and-textures"></a><span data-ttu-id="46ee3-111">3D 按钮和纹理</span><span class="sxs-lookup"><span data-stu-id="46ee3-111">3D buttons and textures</span></span>

<span data-ttu-id="46ee3-112">在混合现实应用程序中进行创建或计划使用 3D 按钮时，自然要考虑性能。</span><span class="sxs-lookup"><span data-stu-id="46ee3-112">It's natural to think about performance when creating or planning to use 3D buttons in mixed reality applications.</span></span> <span data-ttu-id="46ee3-113">但并非所有内容都必须由网格制成才能被视为 3D。</span><span class="sxs-lookup"><span data-stu-id="46ee3-113">However, not everything has to be made from meshes to be perceived as 3D.</span></span> <span data-ttu-id="46ee3-114">可以选择使用 Paper2D 并精心制作纹理来实现 3D 外观。</span><span class="sxs-lookup"><span data-stu-id="46ee3-114">You have the option of using Paper2D with carefully crafted textures to get that 3D look.</span></span> <span data-ttu-id="46ee3-115">这非常适用于“看似”3D 但实则是四边形上经 photoshop 处理过的图片的按钮。</span><span class="sxs-lookup"><span data-stu-id="46ee3-115">This works really well for buttons that "seem" 3D, but are just photoshopped images on a quad.</span></span> <span data-ttu-id="46ee3-116">它们的一个精美版本称为 [sprite](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html)。</span><span class="sxs-lookup"><span data-stu-id="46ee3-116">A fancy version of these is called a [sprite](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html).</span></span>

## <a name="variants"></a><span data-ttu-id="46ee3-117">变量</span><span class="sxs-lookup"><span data-stu-id="46ee3-117">Variants</span></span>

<span data-ttu-id="46ee3-118">在运行时创建具有多个对象配置的场景时，请使用 [Unreal 变体](https://docs.unrealengine.com/Basics/Levels/Variants/index.html)。</span><span class="sxs-lookup"><span data-stu-id="46ee3-118">Use [Unreal Variants](https://docs.unrealengine.com/Basics/Levels/Variants/index.html) in scenarios where you're creating a scene with multiple object configurations at runtime.</span></span> <span data-ttu-id="46ee3-119">变体可以包括不断变化的材料或网格。</span><span class="sxs-lookup"><span data-stu-id="46ee3-119">Variations can include changing materials or meshes.</span></span> 

## <a name="animation"></a><span data-ttu-id="46ee3-120">动画</span><span class="sxs-lookup"><span data-stu-id="46ee3-120">Animation</span></span>

<span data-ttu-id="46ee3-121">如果要创建大量“可交互的动画”，请使用 [Spline 组件](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html)（而不是 Spline“网格”组件）和[时间线节点](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html)。</span><span class="sxs-lookup"><span data-stu-id="46ee3-121">Take advantage of the [Spline component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html) (not the Spline "Mesh" Component) and [Timeline nodes](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html) if you're creating lots of "interactable animations".</span></span> 

<!-- You can find a comprehensive [video tutorial here](https://www.youtube.com/watch?v=bWXI91FdMtk&ab_channel=DoubleCrossGames). -->

## <a name="communications"></a><span data-ttu-id="46ee3-122">通信</span><span class="sxs-lookup"><span data-stu-id="46ee3-122">Communications</span></span>

<span data-ttu-id="46ee3-123">如果在动态查找对象时或使用过多带宽在多个角色和蓝图之间进行通信时遇到麻烦，请使用[关卡蓝图](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html)。</span><span class="sxs-lookup"><span data-stu-id="46ee3-123">Use a [Level Blueprint](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html) if you're having trouble dynamically finding objects or using too much bandwidth to communicate between multiple actors and blueprints.</span></span> <span data-ttu-id="46ee3-124">请记住，Unreal Engine 4 与 Unity 不同，并非所有内容都必须位于组件内部。</span><span class="sxs-lookup"><span data-stu-id="46ee3-124">Remember, Unreal Engine 4 isn't like Unity, not everything has to be inside a component.</span></span> <span data-ttu-id="46ee3-125">关卡蓝图是简化多个角色之间通信的非常有效的推荐方法。</span><span class="sxs-lookup"><span data-stu-id="46ee3-125">Level Blueprints are a perfectly valid and recommended way of simplifying the communication between multiple actors.</span></span> <span data-ttu-id="46ee3-126">在关卡蓝图的 OnBeginPlay 中，甚至可以在启动时“缓存”对象引用。</span><span class="sxs-lookup"><span data-stu-id="46ee3-126">Object references can even be "cached" at startup in the Level Blueprint's OnBeginPlay.</span></span>

## <a name="global-state"></a><span data-ttu-id="46ee3-127">全局状态</span><span class="sxs-lookup"><span data-stu-id="46ee3-127">Global state</span></span>

<span data-ttu-id="46ee3-128">通常需要存储特定于关卡的状态，例如分数、关卡数据、特定于玩家的信息或不完全属于特定对象的任何其他内容。</span><span class="sxs-lookup"><span data-stu-id="46ee3-128">You'll often need to store level-specific state like score, level data, player-specific information, or anything else that doesn't quite belong to a particular object.</span></span> <span data-ttu-id="46ee3-129">请勿忽略 [GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html)。</span><span class="sxs-lookup"><span data-stu-id="46ee3-129">Don't overlook the [GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html).</span></span> <span data-ttu-id="46ee3-130">大多数人都忘记了它的存在，但是 GameMode 可以在每个关卡创建，并包含特定于每个关卡的数据。</span><span class="sxs-lookup"><span data-stu-id="46ee3-130">Most people forget that it exists, but the GameMode can be created per level, and contain data specific to each level.</span></span>

## <a name="optimizing-blueprints"></a><span data-ttu-id="46ee3-131">优化蓝图</span><span class="sxs-lookup"><span data-stu-id="46ee3-131">Optimizing Blueprints</span></span>

<span data-ttu-id="46ee3-132">如果发现自己的蓝图太慢，请在用 c++ 重写代码前，先让 Unreal 将蓝图“本地化”。</span><span class="sxs-lookup"><span data-stu-id="46ee3-132">If you're finding your blueprints to be too slow, let Unreal "nativize" your blueprints before resorting to rewriting the code in c++.</span></span> <span data-ttu-id="46ee3-133">创建自己的自定义解决方案前，请先尝试使用自动[本地化](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html)。</span><span class="sxs-lookup"><span data-stu-id="46ee3-133">Try using the automatic [nativization](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html) before creating your own custom solution.</span></span>

![蓝图设置，其中突出显示了蓝图本地化方法](images/unreal-general-practices-img-01.jpg)
