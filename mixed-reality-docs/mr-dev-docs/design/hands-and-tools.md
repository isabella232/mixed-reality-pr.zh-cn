---
title: 手部和运动控制器
description: 了解免提和运动控制器交互模型，这些模型可删除虚拟与物理之间的边界。
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: 混合现实、动手、运动控制器、交互、设计
ms.openlocfilehash: 8b2ed6127708204d0c4a537c56b2225ff26e0d0f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677853"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="ba91a-104">手部和运动控制器</span><span class="sxs-lookup"><span data-stu-id="ba91a-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="ba91a-105">方案</span><span class="sxs-lookup"><span data-stu-id="ba91a-105">Scenarios</span></span>
<span data-ttu-id="ba91a-106">如果在阅读 [交互概述](interaction-fundamentals.md)后选择采用此交互模型，这意味着您正在开发一个应用程序，要求用户使用两次手与全息世界交互。</span><span class="sxs-lookup"><span data-stu-id="ba91a-106">If you choose to adopt this interaction model after reading the [interaction overview](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="ba91a-107">您的应用程序将实现删除虚拟与物理之间边界的目标。</span><span class="sxs-lookup"><span data-stu-id="ba91a-107">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="ba91a-108">某些特定情况可能如下：</span><span class="sxs-lookup"><span data-stu-id="ba91a-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="ba91a-109">为信息工作者提供包含 UI 的 2D 虚拟屏幕来显示和控制内容</span><span class="sxs-lookup"><span data-stu-id="ba91a-109">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="ba91a-110">为工厂程序集线提供第一行工作人员教程和指南</span><span class="sxs-lookup"><span data-stu-id="ba91a-110">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="ba91a-111">开发用于协助和教育医疗专业人员的专业工具</span><span class="sxs-lookup"><span data-stu-id="ba91a-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="ba91a-112">使用 3D 虚拟对象来装饰现实世界，或创建第二世界</span><span class="sxs-lookup"><span data-stu-id="ba91a-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="ba91a-113">以现实世界为背景创建基于位置的服务和游戏</span><span class="sxs-lookup"><span data-stu-id="ba91a-113">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="ba91a-114">双手和运动控制器情态</span><span class="sxs-lookup"><span data-stu-id="ba91a-114">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="ba91a-115">[![用手直接操作](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="ba91a-115">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="ba91a-116">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="ba91a-116">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="ba91a-117">这是一种使用手的强大功能的模态，用户可以直接接触和操作全息影像。</span><span class="sxs-lookup"><span data-stu-id="ba91a-117">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="ba91a-118">通过利用日常经验并提供适当的视觉实用，用户可以使用相同的方法来操作现实世界对象，以便与虚拟对象进行交互。</span><span class="sxs-lookup"><span data-stu-id="ba91a-118">By leveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ba91a-119">[![用手指向并提交](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="ba91a-119">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="ba91a-120">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="ba91a-120">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="ba91a-121">这种模态使用户能够在远处与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="ba91a-121">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="ba91a-122">它使用户能够充分利用环境。</span><span class="sxs-lookup"><span data-stu-id="ba91a-122">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="ba91a-123">用户可以在任何位置放置全息影像，同时仍然可以从任意距离访问。</span><span class="sxs-lookup"><span data-stu-id="ba91a-123">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="ba91a-124">用于控制和操作2D 和3D 全息影像的心理模型和手势与直接操作的情况有关。</span><span class="sxs-lookup"><span data-stu-id="ba91a-124">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ba91a-125">[![运动控制器](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="ba91a-125">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="ba91a-126">运动控制器</span><span class="sxs-lookup"><span data-stu-id="ba91a-126">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="ba91a-127">运动控制器是通过在使用一种或两种手时跨大量距离提供精确交互来扩展用户的物理功能的工具。</span><span class="sxs-lookup"><span data-stu-id="ba91a-127">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="ba91a-128">这些硬件附件提供了许多常用交互的快捷方式，并为各种操作提供了 surefooted、tactile 的反馈。</span><span class="sxs-lookup"><span data-stu-id="ba91a-128">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="ba91a-129">目前，运动控制器仅适用于 Windows Mixed Reality (WMR) 方案。</span><span class="sxs-lookup"><span data-stu-id="ba91a-129">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="ba91a-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba91a-130">See also</span></span>
* [<span data-ttu-id="ba91a-131">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="ba91a-131">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="ba91a-132">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="ba91a-132">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="ba91a-133">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="ba91a-133">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ba91a-134">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="ba91a-134">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="ba91a-135">免动手操作</span><span class="sxs-lookup"><span data-stu-id="ba91a-135">Hands-free</span></span>](hands-free.md)
