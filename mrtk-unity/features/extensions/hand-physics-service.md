---
title: 手部物理服务
description: 文档：在 MRTK 中使用手部物理扩展服务
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: af7ea753d52b5e478c54ca19d6d8e391401eea6d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176257"
---
# <a name="hand-physics-service"></a><span data-ttu-id="05abe-104">手部物理服务</span><span class="sxs-lookup"><span data-stu-id="05abe-104">Hand physics service</span></span>

![手部物理扩展服务](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="05abe-106">手部物理服务支持严格的人体碰撞事件，以及与手部表达的交互。</span><span class="sxs-lookup"><span data-stu-id="05abe-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="05abe-107">启用扩展</span><span class="sxs-lookup"><span data-stu-id="05abe-107">Enabling the extension</span></span>

<span data-ttu-id="05abe-108">若要启用扩展，请打开 RegisteredServiceProvider 配置文件。</span><span class="sxs-lookup"><span data-stu-id="05abe-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="05abe-109">单击 `Register a new Service Provider` 以添加新配置。</span><span class="sxs-lookup"><span data-stu-id="05abe-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="05abe-110">在组件类型字段中，选择"HandPhysicsService"。</span><span class="sxs-lookup"><span data-stu-id="05abe-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="05abe-111">在"配置文件"字段中，选择扩展中包含的默认手部物理配置文件。</span><span class="sxs-lookup"><span data-stu-id="05abe-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="05abe-112">配置文件选项</span><span class="sxs-lookup"><span data-stu-id="05abe-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="05abe-113">手部物理层</span><span class="sxs-lookup"><span data-stu-id="05abe-113">Hand physics layer</span></span>

<span data-ttu-id="05abe-114">控制实例化手部将转到的层。</span><span class="sxs-lookup"><span data-stu-id="05abe-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="05abe-115">虽然服务默认为"默认"层 (0) ，但建议为手部物理对象使用单独的层。</span><span class="sxs-lookup"><span data-stu-id="05abe-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="05abe-116">否则，可能有不需要的碰撞和/或不准确的光线广播。</span><span class="sxs-lookup"><span data-stu-id="05abe-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="05abe-117">手指尖运动性人体预制</span><span class="sxs-lookup"><span data-stu-id="05abe-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="05abe-118">控制在触手可及时实例化预制项。</span><span class="sxs-lookup"><span data-stu-id="05abe-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="05abe-119">为了使服务按预期工作，预制项需要：</span><span class="sxs-lookup"><span data-stu-id="05abe-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="05abe-120">已启用 isKinematic 的刚体组件</span><span class="sxs-lookup"><span data-stu-id="05abe-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="05abe-121">碰撞体</span><span class="sxs-lookup"><span data-stu-id="05abe-121">A collider</span></span>
- <span data-ttu-id="05abe-122">`JointKinematicBody` 组件</span><span class="sxs-lookup"><span data-stu-id="05abe-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="05abe-123">使用手部运动体</span><span class="sxs-lookup"><span data-stu-id="05abe-123">Use palm kinematic body</span></span>

<span data-ttu-id="05abe-124">控制服务是否尝试实例化手部上的预制。</span><span class="sxs-lookup"><span data-stu-id="05abe-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="05abe-125">手部运动人体预制</span><span class="sxs-lookup"><span data-stu-id="05abe-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="05abe-126">启用 `UsePalmKinematicBody` 后，这是它将实例化的预制。</span><span class="sxs-lookup"><span data-stu-id="05abe-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="05abe-127">与 `FingerTipKinematicBodyPrefab` 一样，此预制需要：</span><span class="sxs-lookup"><span data-stu-id="05abe-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="05abe-128">已启用 isKinematic 的刚体组件</span><span class="sxs-lookup"><span data-stu-id="05abe-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="05abe-129">碰撞体</span><span class="sxs-lookup"><span data-stu-id="05abe-129">A collider</span></span>
- <span data-ttu-id="05abe-130">`JointKinematicBody` 组件</span><span class="sxs-lookup"><span data-stu-id="05abe-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="05abe-131">如何使用服务</span><span class="sxs-lookup"><span data-stu-id="05abe-131">How to use the service</span></span>

<span data-ttu-id="05abe-132">启用后，使用碰撞体的任何 属性接收来自所有 10 位数字的碰撞事件 (（如果它们已启用 `IsTrigger`) ）。</span><span class="sxs-lookup"><span data-stu-id="05abe-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>
