---
title: 手部和运动控制器
description: 了解免提和运动控制器交互模型，这些模型可删除虚拟与物理之间的边界。
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: 混合现实，动手，运动控制器，交互，设计，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，HoloLens，MRTK，混合现实工具包
ms.openlocfilehash: 1dffdd5f3471993dfdb5e504e4c5b87ec0bfef7d
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847325"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="68cd7-104">手部和运动控制器</span><span class="sxs-lookup"><span data-stu-id="68cd7-104">Hands and motion controllers</span></span>

## <a name="scenarios"></a><span data-ttu-id="68cd7-105">方案</span><span class="sxs-lookup"><span data-stu-id="68cd7-105">Scenarios</span></span>

<span data-ttu-id="68cd7-106">阅读 [交互概述](interaction-fundamentals.md)后，选择 "手形和运动控制器交互模型"。</span><span class="sxs-lookup"><span data-stu-id="68cd7-106">After reading the [interaction overview](interaction-fundamentals.md), you choose the hand and motion controller interaction model.</span></span> <span data-ttu-id="68cd7-107">这意味着你要开发的应用程序要求用户使用两次手与全息世界交互。</span><span class="sxs-lookup"><span data-stu-id="68cd7-107">This means you're developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="68cd7-108">您的应用程序将实现删除虚拟与物理之间边界的目标。</span><span class="sxs-lookup"><span data-stu-id="68cd7-108">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="68cd7-109">某些特定情况可能如下：</span><span class="sxs-lookup"><span data-stu-id="68cd7-109">Some specific scenarios might be:</span></span>
* <span data-ttu-id="68cd7-110">为信息工作者提供包含 UI 的 2D 虚拟屏幕来显示和控制内容</span><span class="sxs-lookup"><span data-stu-id="68cd7-110">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="68cd7-111">为工厂程序集线提供第一行工作人员教程和指南</span><span class="sxs-lookup"><span data-stu-id="68cd7-111">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="68cd7-112">开发用于协助和教育医疗专业人员的专业工具</span><span class="sxs-lookup"><span data-stu-id="68cd7-112">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="68cd7-113">使用 3D 虚拟对象来装饰现实世界，或创建第二世界</span><span class="sxs-lookup"><span data-stu-id="68cd7-113">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="68cd7-114">以现实世界为背景创建基于位置的服务和游戏</span><span class="sxs-lookup"><span data-stu-id="68cd7-114">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="68cd7-115">双手和运动控制器情态</span><span class="sxs-lookup"><span data-stu-id="68cd7-115">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="68cd7-116">[![用手直接操作](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="68cd7-116">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="68cd7-117">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="68cd7-117">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="68cd7-118">模态应用程序的功能，用户可以使用它来触摸和操作全息影像。</span><span class="sxs-lookup"><span data-stu-id="68cd7-118">Modality applying the power of hands that users can use to touch and manipulate holograms.</span></span> <span data-ttu-id="68cd7-119">通过使用每日生活经验并提供适当的视觉实用，用户可以使用与虚拟对象进行交互的相同方式进行交互。</span><span class="sxs-lookup"><span data-stu-id="68cd7-119">By using daily life experiences and providing proper visual affordances, users can use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="68cd7-120">[![用手指向并提交](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="68cd7-120">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="68cd7-121">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="68cd7-121">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="68cd7-122">这种模态使用户能够在远处与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="68cd7-122">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="68cd7-123">它使用户能够充分利用环境。</span><span class="sxs-lookup"><span data-stu-id="68cd7-123">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="68cd7-124">用户可以在任何位置放置全息影像，同时仍然可以从任意距离访问。</span><span class="sxs-lookup"><span data-stu-id="68cd7-124">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="68cd7-125">用于控制和操作2D 和3D 全息影像的心理模型和手势与直接操作的情况有关。</span><span class="sxs-lookup"><span data-stu-id="68cd7-125">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="68cd7-126">[![运动控制器](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="68cd7-126">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="68cd7-127">运动控制器</span><span class="sxs-lookup"><span data-stu-id="68cd7-127">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="68cd7-128">当使用一种或两种方式时，运动控制器会将用户的物理功能扩展到跨一定距离的精确交互。</span><span class="sxs-lookup"><span data-stu-id="68cd7-128">Motion controllers extend the user's physical capabilities with precise interactions across a range of distances while using one or both hands.</span></span> <span data-ttu-id="68cd7-129">这些硬件附件提供了许多常用交互的快捷方式，并为各种操作提供了 footed、tactile 的反馈。</span><span class="sxs-lookup"><span data-stu-id="68cd7-129">These hardware accessories provide shortcuts to many commonly used interactions and provide sure-footed, tactile feedback for various actions.</span></span> <span data-ttu-id="68cd7-130">目前，运动控制器仅适用于 Windows Mixed Reality (WMR) 方案。</span><span class="sxs-lookup"><span data-stu-id="68cd7-130">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="68cd7-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68cd7-131">See also</span></span>
* [<span data-ttu-id="68cd7-132">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="68cd7-132">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="68cd7-133">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="68cd7-133">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="68cd7-134">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="68cd7-134">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="68cd7-135">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="68cd7-135">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="68cd7-136">免动手操作</span><span class="sxs-lookup"><span data-stu-id="68cd7-136">Hands-free</span></span>](hands-free.md)
