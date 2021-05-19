---
title: 手部物理服务概述
description: 文档：在 MRTK 中使用手部物理扩展服务
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 751aec148d3a40da4728d2fdd60a60402b59a4de
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145083"
---
# <a name="hand-physics-extension-service"></a><span data-ttu-id="8c4a3-104">手部物理扩展服务</span><span class="sxs-lookup"><span data-stu-id="8c4a3-104">Hand physics extension service</span></span>

![手部物理扩展服务](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="8c4a3-106">手部物理服务支持严格的人体碰撞事件，以及与手部表达的交互。</span><span class="sxs-lookup"><span data-stu-id="8c4a3-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="8c4a3-107">启用扩展</span><span class="sxs-lookup"><span data-stu-id="8c4a3-107">Enabling the extension</span></span>

<span data-ttu-id="8c4a3-108">若要启用扩展，请打开 RegisteredServiceProvider 配置文件。</span><span class="sxs-lookup"><span data-stu-id="8c4a3-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="8c4a3-109">单击 `Register a new Service Provider` 以添加新配置。</span><span class="sxs-lookup"><span data-stu-id="8c4a3-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="8c4a3-110">在组件类型字段中，选择"HandPhysicsService"。</span><span class="sxs-lookup"><span data-stu-id="8c4a3-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="8c4a3-111">在"配置文件"字段中，选择扩展中包含的默认手部物理配置文件。</span><span class="sxs-lookup"><span data-stu-id="8c4a3-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="8c4a3-112">配置文件选项</span><span class="sxs-lookup"><span data-stu-id="8c4a3-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="8c4a3-113">手部物理层</span><span class="sxs-lookup"><span data-stu-id="8c4a3-113">Hand physics layer</span></span>

<span data-ttu-id="8c4a3-114">控制实例化手部将转到的层。</span><span class="sxs-lookup"><span data-stu-id="8c4a3-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="8c4a3-115">虽然服务默认为"默认"层 (0) ，但建议为手部物理对象使用单独的层。</span><span class="sxs-lookup"><span data-stu-id="8c4a3-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="8c4a3-116">否则，可能有不需要的碰撞和/或不准确的光线广播。</span><span class="sxs-lookup"><span data-stu-id="8c4a3-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="8c4a3-117">手指尖运动性人体预制</span><span class="sxs-lookup"><span data-stu-id="8c4a3-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="8c4a3-118">控制在触手可及时实例化预制项。</span><span class="sxs-lookup"><span data-stu-id="8c4a3-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="8c4a3-119">为了使服务按预期工作，预制项需要：</span><span class="sxs-lookup"><span data-stu-id="8c4a3-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="8c4a3-120">已启用 isKinematic 的刚体组件</span><span class="sxs-lookup"><span data-stu-id="8c4a3-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="8c4a3-121">碰撞体</span><span class="sxs-lookup"><span data-stu-id="8c4a3-121">A collider</span></span>
- <span data-ttu-id="8c4a3-122">`JointKinematicBody` 组件</span><span class="sxs-lookup"><span data-stu-id="8c4a3-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="8c4a3-123">使用掌运动主体</span><span class="sxs-lookup"><span data-stu-id="8c4a3-123">Use palm kinematic body</span></span>

<span data-ttu-id="8c4a3-124">控制服务是否将尝试实例化 palm 接点上的 prefab。</span><span class="sxs-lookup"><span data-stu-id="8c4a3-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="8c4a3-125">掌运动正文 prefab</span><span class="sxs-lookup"><span data-stu-id="8c4a3-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="8c4a3-126">`UsePalmKinematicBody`启用后，这就是它将实例化的 prefab。</span><span class="sxs-lookup"><span data-stu-id="8c4a3-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="8c4a3-127">就像 `FingerTipKinematicBodyPrefab` 这样，此 prefab 需要：</span><span class="sxs-lookup"><span data-stu-id="8c4a3-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="8c4a3-128">启用了 isKinematic 的刚体组件</span><span class="sxs-lookup"><span data-stu-id="8c4a3-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="8c4a3-129">碰撞器</span><span class="sxs-lookup"><span data-stu-id="8c4a3-129">A collider</span></span>
- <span data-ttu-id="8c4a3-130">`JointKinematicBody` 组件</span><span class="sxs-lookup"><span data-stu-id="8c4a3-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="8c4a3-131">如何使用服务</span><span class="sxs-lookup"><span data-stu-id="8c4a3-131">How to use the service</span></span>

<span data-ttu-id="8c4a3-132">启用后，如果启用了) ，请使用任何碰撞器的 `IsTrigger` 属性接收来自所有10位数的冲突事件 (和不要。</span><span class="sxs-lookup"><span data-stu-id="8c4a3-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>
