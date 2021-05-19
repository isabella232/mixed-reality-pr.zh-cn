---
title: 配置边界可视化
description: 在 MRTK 中配置边界系统的详细信息
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 边界系统，
ms.openlocfilehash: 36717493107b129a7200dd3f912bcbdc3337b9a1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144491"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="65620-104">配置边界可视化效果</span><span class="sxs-lookup"><span data-stu-id="65620-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="65620-105">边界 *可视化配置文件* 提供用于为边界系统配置视觉外观和其他相关参数的选项。</span><span class="sxs-lookup"><span data-stu-id="65620-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="65620-106">边界可视化效果附加到场景中的混合现实 Playspace 对象，并随用户进行远程传送。</span><span class="sxs-lookup"><span data-stu-id="65620-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="65620-107">常规设置</span><span class="sxs-lookup"><span data-stu-id="65620-107">General settings</span></span>

![边界可视化常规设置](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="65620-109">边界高度</span><span class="sxs-lookup"><span data-stu-id="65620-109">Boundary height</span></span>

<span data-ttu-id="65620-110">边界高度指示应在平面上方呈现边界上限的距离。</span><span class="sxs-lookup"><span data-stu-id="65620-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="65620-111">默认值为 3 米。</span><span class="sxs-lookup"><span data-stu-id="65620-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="65620-112">楼层设置</span><span class="sxs-lookup"><span data-stu-id="65620-112">Floor settings</span></span>

![边界可视化楼层设置](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="65620-114">**显示**</span><span class="sxs-lookup"><span data-stu-id="65620-114">**Show**</span></span>

<span data-ttu-id="65620-115">指示是否创建地平面并添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="65620-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="65620-116">默认值为 true。</span><span class="sxs-lookup"><span data-stu-id="65620-116">The default value is true.</span></span>

<span data-ttu-id="65620-117">**材料**</span><span class="sxs-lookup"><span data-stu-id="65620-117">**Material**</span></span>

<span data-ttu-id="65620-118">指示应在创建地平面时使用的材料。</span><span class="sxs-lookup"><span data-stu-id="65620-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="65620-119">**缩放**</span><span class="sxs-lookup"><span data-stu-id="65620-119">**Scale**</span></span>

<span data-ttu-id="65620-120">指示要创建的地平面的大小（以米为单位）。</span><span class="sxs-lookup"><span data-stu-id="65620-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="65620-121">默认比例为 3 米 x 3 米正方形。</span><span class="sxs-lookup"><span data-stu-id="65620-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="65620-122">**物理层**</span><span class="sxs-lookup"><span data-stu-id="65620-122">**Physics Layer**</span></span>

<span data-ttu-id="65620-123">应在其上设置地平面的层。</span><span class="sxs-lookup"><span data-stu-id="65620-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="65620-124">默认值 *为默认层* 。</span><span class="sxs-lookup"><span data-stu-id="65620-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="65620-125">播放区域设置</span><span class="sxs-lookup"><span data-stu-id="65620-125">Play area settings</span></span>

![边界可视化效果播放区域设置](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="65620-127">**显示**</span><span class="sxs-lookup"><span data-stu-id="65620-127">**Show**</span></span>

<span data-ttu-id="65620-128">指示是否创建播放区域矩形并将其添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="65620-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="65620-129">默认值为 true。</span><span class="sxs-lookup"><span data-stu-id="65620-129">The default value is true.</span></span>

<span data-ttu-id="65620-130">**材料**</span><span class="sxs-lookup"><span data-stu-id="65620-130">**Material**</span></span>

<span data-ttu-id="65620-131">指示创建播放区域对象时应使用的材料。</span><span class="sxs-lookup"><span data-stu-id="65620-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="65620-132">**物理层**</span><span class="sxs-lookup"><span data-stu-id="65620-132">**Physics Layer**</span></span>

<span data-ttu-id="65620-133">应在其上设置播放区域的层。</span><span class="sxs-lookup"><span data-stu-id="65620-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="65620-134">默认值为 *Ignore Raycast* 层。</span><span class="sxs-lookup"><span data-stu-id="65620-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="65620-135">跟踪区域设置</span><span class="sxs-lookup"><span data-stu-id="65620-135">Tracked area settings</span></span>

![边界可视化跟踪区域设置](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="65620-137">**显示**</span><span class="sxs-lookup"><span data-stu-id="65620-137">**Show**</span></span>

<span data-ttu-id="65620-138">指示是否创建跟踪区域的轮廓并将其添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="65620-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="65620-139">默认值为 true。</span><span class="sxs-lookup"><span data-stu-id="65620-139">The default value is true.</span></span>

<span data-ttu-id="65620-140">**材料**</span><span class="sxs-lookup"><span data-stu-id="65620-140">**Material**</span></span>

<span data-ttu-id="65620-141">指示创建跟踪区域轮廓时应使用的材料。</span><span class="sxs-lookup"><span data-stu-id="65620-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="65620-142">**物理层**</span><span class="sxs-lookup"><span data-stu-id="65620-142">**Physics Layer**</span></span>

<span data-ttu-id="65620-143">应在其上设置跟踪区域的层。</span><span class="sxs-lookup"><span data-stu-id="65620-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="65620-144">默认值为 *Ignore Raycast* 层。</span><span class="sxs-lookup"><span data-stu-id="65620-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="65620-145">边界墙壁设置</span><span class="sxs-lookup"><span data-stu-id="65620-145">Boundary wall settings</span></span>

![边界可视化边界墙壁设置](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="65620-147">**显示**</span><span class="sxs-lookup"><span data-stu-id="65620-147">**Show**</span></span>

<span data-ttu-id="65620-148">指示是否要创建边界墙壁，并将其添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="65620-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="65620-149">默认值为 false。</span><span class="sxs-lookup"><span data-stu-id="65620-149">The default value is false.</span></span>

<span data-ttu-id="65620-150">**材料**</span><span class="sxs-lookup"><span data-stu-id="65620-150">**Material**</span></span>

<span data-ttu-id="65620-151">指示在创建边界墙壁时应使用的材料。</span><span class="sxs-lookup"><span data-stu-id="65620-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="65620-152">**物理层**</span><span class="sxs-lookup"><span data-stu-id="65620-152">**Physics Layer**</span></span>

<span data-ttu-id="65620-153">应在其上设置边界壁的层。</span><span class="sxs-lookup"><span data-stu-id="65620-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="65620-154">默认值为 *Ignore Raycast* 层。</span><span class="sxs-lookup"><span data-stu-id="65620-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="65620-155">将边界墙壁组件设置为除 *Ignore Raycast* 以外的物理层可能会阻止用户与场景中的对象进行交互。</span><span class="sxs-lookup"><span data-stu-id="65620-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="65620-156">边界上限设置</span><span class="sxs-lookup"><span data-stu-id="65620-156">Boundary ceiling settings</span></span>

![边界可视化边界上限设置](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="65620-158">**显示**</span><span class="sxs-lookup"><span data-stu-id="65620-158">**Show**</span></span>

<span data-ttu-id="65620-159">指示是否创建边界上限平面并添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="65620-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="65620-160">默认值为 false。</span><span class="sxs-lookup"><span data-stu-id="65620-160">The default value is false.</span></span>

<span data-ttu-id="65620-161">**材料**</span><span class="sxs-lookup"><span data-stu-id="65620-161">**Material**</span></span>

<span data-ttu-id="65620-162">指示在创建边界上限平面时应该使用的材料。</span><span class="sxs-lookup"><span data-stu-id="65620-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="65620-163">**物理层**</span><span class="sxs-lookup"><span data-stu-id="65620-163">**Physics Layer**</span></span>

<span data-ttu-id="65620-164">应设置边界墙的层。</span><span class="sxs-lookup"><span data-stu-id="65620-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="65620-165">默认值为 Ignore *Raycast* 层。</span><span class="sxs-lookup"><span data-stu-id="65620-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="65620-166">将边界上限组件设置为"忽略 *光线* 广播"之外的物理层可能会阻止用户与场景中的对象交互。</span><span class="sxs-lookup"><span data-stu-id="65620-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="65620-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65620-167">See also</span></span>

- [<span data-ttu-id="65620-168">边界 API 文档</span><span class="sxs-lookup"><span data-stu-id="65620-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="65620-169">边界系统</span><span class="sxs-lookup"><span data-stu-id="65620-169">Boundary System</span></span>](boundary-system-getting-started.md)
