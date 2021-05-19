---
title: 手部物理扩展服务
description: description 手部物理扩展服务。
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 401a9d31ed3fbbe0c3e02cb95ffebb024f882fd9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143429"
---
# <a name="hand-physics-extension-services"></a><span data-ttu-id="515f1-104">手部物理扩展服务</span><span class="sxs-lookup"><span data-stu-id="515f1-104">Hand physics extension services</span></span>

<span data-ttu-id="515f1-105">手部物理服务支持严格的人体碰撞事件，以及与手部表达的交互。</span><span class="sxs-lookup"><span data-stu-id="515f1-105">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="getting-started-with-hand-physics-extension-service"></a><span data-ttu-id="515f1-106">手部物理扩展服务入门</span><span class="sxs-lookup"><span data-stu-id="515f1-106">Getting started with hand physics extension service</span></span>

<span data-ttu-id="515f1-107">将手部物理服务添加到扩展服务列表中，并使用默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="515f1-107">Add the hand physics service to the list of extension services and use the default profile.</span></span>

<span data-ttu-id="515f1-108">启用后，使用任何碰撞体的 IsTrigger 属性接收来自所有 10 位数字（如果 (）的碰撞) 。</span><span class="sxs-lookup"><span data-stu-id="515f1-108">Once enabled, use any collider's IsTrigger property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>

### <a name="prerequisites"></a><span data-ttu-id="515f1-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="515f1-109">Prerequisites</span></span>

- <span data-ttu-id="515f1-110">已启用扩展服务</span><span class="sxs-lookup"><span data-stu-id="515f1-110">Enabled the extension service</span></span>
- <span data-ttu-id="515f1-111">将适当的预制名分配到手指/手部。</span><span class="sxs-lookup"><span data-stu-id="515f1-111">Assign an appropriate prefab to the finger/palm joint.</span></span>

## <a name="recommendations"></a><span data-ttu-id="515f1-112">建议</span><span class="sxs-lookup"><span data-stu-id="515f1-112">Recommendations</span></span>

<span data-ttu-id="515f1-113">虽然服务默认为"默认"层，但建议为 HandPhysics 对象使用单独的层。</span><span class="sxs-lookup"><span data-stu-id="515f1-113">While the service defaults to the "default" layer, it is recommended to use a separate layer for HandPhysics objects.</span></span> <span data-ttu-id="515f1-114">否则，可能有不需要的碰撞和/或不准确的光线广播。</span><span class="sxs-lookup"><span data-stu-id="515f1-114">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>
