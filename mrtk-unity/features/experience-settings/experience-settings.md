---
title: 体验设置
description: 有关 MRTK 的不同体验设置的文档
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: ab3a449b064d4a1c8f2bf76154f7a25c688693e1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177356"
---
# <a name="experience-settings"></a><span data-ttu-id="2fd50-104">体验设置</span><span class="sxs-lookup"><span data-stu-id="2fd50-104">Experience settings</span></span>

<span data-ttu-id="2fd50-105">为混合现实创建 UI 的难题之一是跨不同体验。</span><span class="sxs-lookup"><span data-stu-id="2fd50-105">One of the challenges of creating UI for Mixed Reality is aligning across different experiences.</span></span> <span data-ttu-id="2fd50-106">通过 MRTK，你可以 `Target Experience Scale` 为场景设置和， `Content Offset` 将配置以下各项，以适合目标规模。</span><span class="sxs-lookup"><span data-stu-id="2fd50-106">With MRTK, you can set the `Target Experience Scale` and the `Content Offset` for your scene, will configue the following to behave appropriately for the target scale.</span></span>

- <span data-ttu-id="2fd50-107">混合现实场景内容</span><span class="sxs-lookup"><span data-stu-id="2fd50-107">Mixed Reality Scene Content</span></span>
- <span data-ttu-id="2fd50-108">边界系统</span><span class="sxs-lookup"><span data-stu-id="2fd50-108">Boundary System</span></span>

  ![MRTK 配置文件中的体验设置](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a><span data-ttu-id="2fd50-110">目标体验规模</span><span class="sxs-lookup"><span data-stu-id="2fd50-110">Target Experience Scale</span></span>

<span data-ttu-id="2fd50-111">**目标体验规模** 指定了经验的设计环境。</span><span class="sxs-lookup"><span data-stu-id="2fd50-111">The **Target Experience Scale** specifies the environment for which the experience is designed.</span></span> <span data-ttu-id="2fd50-112">它可以采用以下值。</span><span class="sxs-lookup"><span data-stu-id="2fd50-112">It can take on the following values.</span></span>

* <span data-ttu-id="2fd50-113">*OrientationOnly* -一种只利用耳机方向且重心对齐的体验。</span><span class="sxs-lookup"><span data-stu-id="2fd50-113">*OrientationOnly* - An experience which utilizes only the headset orientation and is gravity aligned.</span></span> <span data-ttu-id="2fd50-114">坐标系统原点位于 head 级别。</span><span class="sxs-lookup"><span data-stu-id="2fd50-114">The coordinate system origin is at head level.</span></span>
* <span data-ttu-id="2fd50-115">已 *就位设计，旨在* 实现现有用途。</span><span class="sxs-lookup"><span data-stu-id="2fd50-115">*Seated* - An experience designed for seated use.</span></span> <span data-ttu-id="2fd50-116">坐标系统原点在楼层级。</span><span class="sxs-lookup"><span data-stu-id="2fd50-116">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="2fd50-117">持续-为静止使用而 *设计的体验*。</span><span class="sxs-lookup"><span data-stu-id="2fd50-117">*Standing* - An experience designed for stationary standing use.</span></span> <span data-ttu-id="2fd50-118">坐标系统原点在楼层级。</span><span class="sxs-lookup"><span data-stu-id="2fd50-118">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="2fd50-119">*房间* -一种体验，旨在支持在房间内移动。</span><span class="sxs-lookup"><span data-stu-id="2fd50-119">*Room* - An experience designed to support movement throughout a room.</span></span> <span data-ttu-id="2fd50-120">坐标系统原点在楼层级。</span><span class="sxs-lookup"><span data-stu-id="2fd50-120">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="2fd50-121">*世界* -一种经验，旨在利用和迁移到现实世界。</span><span class="sxs-lookup"><span data-stu-id="2fd50-121">*World* - An experience designed to utilize and move through the physical world.</span></span> <span data-ttu-id="2fd50-122">坐标系统原点位于 head 级别。</span><span class="sxs-lookup"><span data-stu-id="2fd50-122">The coordinate system origin is at head level.</span></span>

## <a name="content-offset"></a><span data-ttu-id="2fd50-123">内容偏移</span><span class="sxs-lookup"><span data-stu-id="2fd50-123">Content Offset</span></span>

<span data-ttu-id="2fd50-124">此参数指定当 **对齐类型** 设置为 **与体验规模一致** 时，将 [混合现实场景内容](scene-content.md)偏移的地面的高度</span><span class="sxs-lookup"><span data-stu-id="2fd50-124">This parameter specifies the height above the floor to offset [Mixed Reality Scene Content](scene-content.md) when **Alignment Type** is set to **Align with Experience Scale**</span></span>
