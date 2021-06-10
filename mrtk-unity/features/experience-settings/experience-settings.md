---
title: ExperienceSettings
description: 有关 MRTK 的不同体验设置的文档
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 1c93e2ee703eb5dad43bb51236b9991d17e1d58d
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647761"
---
# <a name="experience-settings"></a><span data-ttu-id="991c5-104">体验设置</span><span class="sxs-lookup"><span data-stu-id="991c5-104">Experience Settings</span></span>

<span data-ttu-id="991c5-105">为混合现实创建 UI 的其中一个难题是跨不同体验保持一致。</span><span class="sxs-lookup"><span data-stu-id="991c5-105">One of the challenges of creating UI for Mixed Reality is aligning across different experiences.</span></span> <span data-ttu-id="991c5-106">使用 MRTK，你可以为场景设置 和 ，将以下内容配置为适合 `Target Experience Scale` `Content Offset` 目标规模的行为。</span><span class="sxs-lookup"><span data-stu-id="991c5-106">With MRTK, you can set the `Target Experience Scale` and the `Content Offset` for your scene, will configue the following to behave appropriately for the target scale.</span></span>

- <span data-ttu-id="991c5-107">混合现实场景内容</span><span class="sxs-lookup"><span data-stu-id="991c5-107">Mixed Reality Scene Content</span></span>
- <span data-ttu-id="991c5-108">边界系统</span><span class="sxs-lookup"><span data-stu-id="991c5-108">Boundary System</span></span>

  ![MRTK 配置文件中的体验设置](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a><span data-ttu-id="991c5-110">目标体验缩放</span><span class="sxs-lookup"><span data-stu-id="991c5-110">Target Experience Scale</span></span>

<span data-ttu-id="991c5-111">" **目标体验** 规模"指定设计体验的环境。</span><span class="sxs-lookup"><span data-stu-id="991c5-111">The **Target Experience Scale** specifies the environment for which the experience is designed.</span></span> <span data-ttu-id="991c5-112">它可以接受以下值。</span><span class="sxs-lookup"><span data-stu-id="991c5-112">It can take on the following values.</span></span>

* <span data-ttu-id="991c5-113">*OrientationOnly* - 一种仅利用头戴显示设备方向且与力对齐的体验。</span><span class="sxs-lookup"><span data-stu-id="991c5-113">*OrientationOnly* - An experience which utilizes only the headset orientation and is gravity aligned.</span></span> <span data-ttu-id="991c5-114">坐标系统原点位于头级别。</span><span class="sxs-lookup"><span data-stu-id="991c5-114">The coordinate system origin is at head level.</span></span>
* <span data-ttu-id="991c5-115">*下* 级 - 专为自己使用而设计的体验。</span><span class="sxs-lookup"><span data-stu-id="991c5-115">*Seated* - An experience designed for seated use.</span></span> <span data-ttu-id="991c5-116">坐标系原点在楼层级别。</span><span class="sxs-lookup"><span data-stu-id="991c5-116">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="991c5-117">*站* 式 - 专为固定固定使用而设计的体验。</span><span class="sxs-lookup"><span data-stu-id="991c5-117">*Standing* - An experience designed for stationary standing use.</span></span> <span data-ttu-id="991c5-118">坐标系原点在楼层级别。</span><span class="sxs-lookup"><span data-stu-id="991c5-118">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="991c5-119">*房间* - 旨在支持整个房间移动的体验。</span><span class="sxs-lookup"><span data-stu-id="991c5-119">*Room* - An experience designed to support movement throughout a room.</span></span> <span data-ttu-id="991c5-120">坐标系原点在楼层级别。</span><span class="sxs-lookup"><span data-stu-id="991c5-120">The coordinate system origin is at floor level.</span></span>
* <span data-ttu-id="991c5-121">*世界* - 旨在利用和移动物理世界的体验。</span><span class="sxs-lookup"><span data-stu-id="991c5-121">*World* - An experience designed to utilize and move through the physical world.</span></span> <span data-ttu-id="991c5-122">坐标系统原点位于头级别。</span><span class="sxs-lookup"><span data-stu-id="991c5-122">The coordinate system origin is at head level.</span></span>

## <a name="content-offset"></a><span data-ttu-id="991c5-123">内容偏移量</span><span class="sxs-lookup"><span data-stu-id="991c5-123">Content Offset</span></span>

<span data-ttu-id="991c5-124">当对齐类型设置为"与体验刻度对齐"时 [](scene-content.md)，此参数指定楼层上方的高度以偏移混合现实 **场景内容**</span><span class="sxs-lookup"><span data-stu-id="991c5-124">This parameter specifies the height above the floor to offset [Mixed Reality Scene Content](scene-content.md) when **Alignment Type** is set to **Align with Experience Scale**</span></span>