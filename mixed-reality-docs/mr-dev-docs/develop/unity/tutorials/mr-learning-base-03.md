---
title: 入门教程 - 3. 配置 MRTK 配置文件
description: 本教程介绍如何配置混合现实工具包 (MRTK) 配置文件。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, MRTK, 混合现实工具包, UWP, 空间感知
ms.localizationpriority: high
ms.openlocfilehash: 3b44ba6c4eac3cf7b42d15c8fb19d42676b10a4a
ms.sourcegitcommit: 5017f309827c1d20df4ce656d105a1a49ba7942c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/31/2021
ms.locfileid: "106011136"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="52966-105">3.配置 MRTK 配置文件</span><span class="sxs-lookup"><span data-stu-id="52966-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="52966-106">概述</span><span class="sxs-lookup"><span data-stu-id="52966-106">Overview</span></span>

<span data-ttu-id="52966-107">在本教程中，你将学习如何自定义和配置 MRTK 配置文件。</span><span class="sxs-lookup"><span data-stu-id="52966-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="52966-108"><a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles.md" target="_blank">MRTK 配置文件</a>是一个嵌套配置文件树，它们构成了应如何初始化 MRTK 系统和功能的配置信息。</span><span class="sxs-lookup"><span data-stu-id="52966-108">The <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles.md" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="52966-109">顶级配置文件（即“配置”配置文件）包含每个主要核心系统的嵌套配置文件。</span><span class="sxs-lookup"><span data-stu-id="52966-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="52966-110">每个嵌套的配置文件都设计为配置其对应系统的行为。</span><span class="sxs-lookup"><span data-stu-id="52966-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="52966-111">此特定示例将演示如何通过更改空间网格观察程序的设置来隐藏空间感知网格。</span><span class="sxs-lookup"><span data-stu-id="52966-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="52966-112">但是，可以按照相同的原则来自定义 MRTK 配置文件中的任何设置或值。</span><span class="sxs-lookup"><span data-stu-id="52966-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="52966-113">正如你在[上一教程](mr-learning-base-02.md#congratulations)期间将项目部署到 HoloLens 2 时遇到的一样，<a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">空间感知</a>网格是一系列表示环境几何图形的网格。</span><span class="sxs-lookup"><span data-stu-id="52966-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="52966-114">这是一种有用的可视化效果，一开始就能看到，但通常也可将它关闭，以避免用它后产生视觉干扰和额外的性能影响。</span><span class="sxs-lookup"><span data-stu-id="52966-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="52966-115">目标</span><span class="sxs-lookup"><span data-stu-id="52966-115">Objectives</span></span>

* <span data-ttu-id="52966-116">了解如何自定义和配置 MRTK 配置文件</span><span class="sxs-lookup"><span data-stu-id="52966-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="52966-117">隐藏空间感知网格</span><span class="sxs-lookup"><span data-stu-id="52966-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="52966-118">更改空间感知显示选项</span><span class="sxs-lookup"><span data-stu-id="52966-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="52966-119">隐藏空间感知网格所要执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="52966-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="52966-120">克隆默认的配置配置文件</span><span class="sxs-lookup"><span data-stu-id="52966-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="52966-121">启用空间感知系统</span><span class="sxs-lookup"><span data-stu-id="52966-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="52966-122">克隆默认的空间感知系统配置文件</span><span class="sxs-lookup"><span data-stu-id="52966-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="52966-123">克隆默认的空间感知网格观察程序配置文件</span><span class="sxs-lookup"><span data-stu-id="52966-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="52966-124">更改空间感知网格的可见性</span><span class="sxs-lookup"><span data-stu-id="52966-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="52966-125">默认情况下，MRTK 配置文件不可编辑。</span><span class="sxs-lookup"><span data-stu-id="52966-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="52966-126">这是一些默认的配置文件模板，必须先克隆它们，然后才能对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="52966-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="52966-127">配置文件有多个嵌套层。</span><span class="sxs-lookup"><span data-stu-id="52966-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="52966-128">因此，在配置一个或多个设置时，常见的做法是克隆然后编辑多个配置文件。</span><span class="sxs-lookup"><span data-stu-id="52966-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a><span data-ttu-id="52966-129">祝贺</span><span class="sxs-lookup"><span data-stu-id="52966-129">Congratulations</span></span>

<span data-ttu-id="52966-130">在本教程中，你学习了如何克隆、自定义和配置 MRTK 配置文件和设置。</span><span class="sxs-lookup"><span data-stu-id="52966-130">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="52966-131">下一教程：4.定位场景中的对象</span><span class="sxs-lookup"><span data-stu-id="52966-131">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)