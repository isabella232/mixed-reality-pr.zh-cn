---
title: Unity AR 照相机设置
description: 使用 MRTK 中的 AR 相机的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity、HoloLens、HoloLens 2、混合现实、开发、MRTK、AR 相机、
ms.openlocfilehash: e1c032805bc4b733cfcc51e1ceac5096c73715cf
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121195"
---
# <a name="unity-ar-camera-settings-provider"></a><span data-ttu-id="fb5f9-104">Unity AR 照相机设置提供程序</span><span class="sxs-lookup"><span data-stu-id="fb5f9-104">Unity AR camera settings provider</span></span>

<span data-ttu-id="fb5f9-105">Unity AR 照相机设置提供程序是一个试验性的 MRTK 组件，使混合现实应用程序能够在 Android 和 iOS 设备上运行。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-105">The Unity AR camera settings provider is an experimental MRTK component that enables mixed reality applications to run on Android and iOS devices.</span></span>

## <a name="unity-ar-camera-settings-provider-options"></a><span data-ttu-id="fb5f9-106">Unity AR 照相机设置提供程序选项</span><span class="sxs-lookup"><span data-stu-id="fb5f9-106">Unity AR camera settings provider options</span></span>

![Unity AR 照相机设置配置](../images/camera-system/UnityArSettingsConfiguration.png)

<span data-ttu-id="fb5f9-108">有关如何将提供程序添加到场景中的指南： [如何为 iOS 和 Android 配置 MRTK](../../supported-devices/using-ar-foundation.md)</span><span class="sxs-lookup"><span data-stu-id="fb5f9-108">For a guide on how to add the provider to your scene: [How to configure MRTK for iOS and Android](../../supported-devices/using-ar-foundation.md)</span></span>

### <a name="tracking-settings"></a><span data-ttu-id="fb5f9-109">跟踪设置</span><span class="sxs-lookup"><span data-stu-id="fb5f9-109">Tracking settings</span></span>

<span data-ttu-id="fb5f9-110">Unity AR 照相机设置提供程序允许配置有关如何执行跟踪的选项。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-110">The Unity AR camera settings provider allows configuration options for how tracking is performed.</span></span> <span data-ttu-id="fb5f9-111">这些设置特定于 Unity AR 相机设置提供程序实现。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-111">These settings are specific to the Unity AR camera settings provider implementation.</span></span>

<span data-ttu-id="fb5f9-112">**姿势源**</span><span class="sxs-lookup"><span data-stu-id="fb5f9-112">**Pose Source**</span></span>

<span data-ttu-id="fb5f9-113">姿势源定义增加的现实跟踪姿势的可用类型。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-113">The pose source defines the available types of augmented reality tracking poses.</span></span> <span data-ttu-id="fb5f9-114">通常，这些值映射到正在运行应用程序的设备的组件。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-114">In general, these values map to a component of the device on which the application is running.</span></span>

<span data-ttu-id="fb5f9-115">下表介绍了可用的选项。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-115">The available options are described in the following table.</span></span>

| <span data-ttu-id="fb5f9-116">选项</span><span class="sxs-lookup"><span data-stu-id="fb5f9-116">Option</span></span> | <span data-ttu-id="fb5f9-117">说明</span><span class="sxs-lookup"><span data-stu-id="fb5f9-117">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fb5f9-118">Center</span><span class="sxs-lookup"><span data-stu-id="fb5f9-118">Center</span></span> | <span data-ttu-id="fb5f9-119">头设备的中心眼。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-119">The center eye of a head mounted device.</span></span> |
| <span data-ttu-id="fb5f9-120">彩色照相机</span><span class="sxs-lookup"><span data-stu-id="fb5f9-120">Color Camera</span></span> | <span data-ttu-id="fb5f9-121">移动设备的彩色相机。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-121">The color camera of a mobile device.</span></span> |
| <span data-ttu-id="fb5f9-122">头</span><span class="sxs-lookup"><span data-stu-id="fb5f9-122">Head</span></span> | <span data-ttu-id="fb5f9-123">打印头上架的设备，通常略微大于中心眼。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-123">The head eye of a head mounted device, often slightly above the center eye.</span></span> |
| <span data-ttu-id="fb5f9-124">左眼</span><span class="sxs-lookup"><span data-stu-id="fb5f9-124">Left Eye</span></span> | <span data-ttu-id="fb5f9-125">打印头装入设备的左侧。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-125">The left eye of a head mounted device.</span></span> |
| <span data-ttu-id="fb5f9-126">左姿势</span><span class="sxs-lookup"><span data-stu-id="fb5f9-126">Left Pose</span></span> | <span data-ttu-id="fb5f9-127">左侧控制器的构成。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-127">The left hand controller pose.</span></span> |
| <span data-ttu-id="fb5f9-128">右眼</span><span class="sxs-lookup"><span data-stu-id="fb5f9-128">Right Eye</span></span> | <span data-ttu-id="fb5f9-129">头设备的正确使用。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-129">The right eye of a head mounted device.</span></span> |
| <span data-ttu-id="fb5f9-130">右姿势</span><span class="sxs-lookup"><span data-stu-id="fb5f9-130">Right Pose</span></span> | <span data-ttu-id="fb5f9-131">右手控制器会带来。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-131">The right hand controller pose.</span></span> |

<span data-ttu-id="fb5f9-132">"姿势 source" 的默认值为 " **彩色相机**"，用于在移动设备（如电话或平板电脑）上启用透明显示。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-132">The default value for pose source is **Color Camera**, to enable a transparent display on mobile devices, such as a phone or tablet.</span></span>

<span data-ttu-id="fb5f9-133">**跟踪类型**</span><span class="sxs-lookup"><span data-stu-id="fb5f9-133">**Tracking Type**</span></span>

<span data-ttu-id="fb5f9-134">跟踪类型定义将用于跟踪的姿势 () 部分。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-134">The tracking type defines the portion(s) of the pose that will be used for tracking.</span></span>

<span data-ttu-id="fb5f9-135">下表介绍了可用的选项。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-135">The available options are described in the following table.</span></span>

| <span data-ttu-id="fb5f9-136">选项</span><span class="sxs-lookup"><span data-stu-id="fb5f9-136">Option</span></span> | <span data-ttu-id="fb5f9-137">说明</span><span class="sxs-lookup"><span data-stu-id="fb5f9-137">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fb5f9-138">位置</span><span class="sxs-lookup"><span data-stu-id="fb5f9-138">Position</span></span> | <span data-ttu-id="fb5f9-139">设备的位置。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-139">The position of the device.</span></span> |
| <span data-ttu-id="fb5f9-140">旋转</span><span class="sxs-lookup"><span data-stu-id="fb5f9-140">Rotation</span></span> | <span data-ttu-id="fb5f9-141">设备的旋转。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-141">The rotation of the device.</span></span> |
| <span data-ttu-id="fb5f9-142">旋转和位置</span><span class="sxs-lookup"><span data-stu-id="fb5f9-142">Rotation And Position</span></span> | <span data-ttu-id="fb5f9-143">设备的位置和旋转。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-143">The position and rotation of the device.</span></span> |

<span data-ttu-id="fb5f9-144">跟踪类型的默认值为 " **旋转" 和 "位置**"，以启用最丰富的跟踪体验。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-144">The default value for tracking type is **Rotation And Position**, to enable the richest tracking experience.</span></span>

<span data-ttu-id="fb5f9-145">**更新类型**</span><span class="sxs-lookup"><span data-stu-id="fb5f9-145">**Update Type**</span></span>

<span data-ttu-id="fb5f9-146">更新类型定义在帧处理过程中，将对姿势数据进行采样。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-146">The update type defines at what points, during frame processing, the pose data will be sampled.</span></span>

<span data-ttu-id="fb5f9-147">下表介绍了可用的选项。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-147">The available options are described in the following table.</span></span>

| <span data-ttu-id="fb5f9-148">选项</span><span class="sxs-lookup"><span data-stu-id="fb5f9-148">Option</span></span> | <span data-ttu-id="fb5f9-149">说明</span><span class="sxs-lookup"><span data-stu-id="fb5f9-149">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fb5f9-150">呈现之前</span><span class="sxs-lookup"><span data-stu-id="fb5f9-150">Before Render</span></span> | <span data-ttu-id="fb5f9-151">在呈现之前。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-151">Just before rendering.</span></span> |
| <span data-ttu-id="fb5f9-152">更新</span><span class="sxs-lookup"><span data-stu-id="fb5f9-152">Update</span></span> | <span data-ttu-id="fb5f9-153">在框架的更新阶段。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-153">During the update phase of the frame.</span></span> |
| <span data-ttu-id="fb5f9-154">在呈现之前更新</span><span class="sxs-lookup"><span data-stu-id="fb5f9-154">Update And Before Render</span></span> | <span data-ttu-id="fb5f9-155">在更新阶段和渲染之前。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-155">During the update phase and just before rendering.</span></span> |

<span data-ttu-id="fb5f9-156">跟踪类型的默认值为 **Update 和 Render 之前**，以启用最小跟踪延迟。</span><span class="sxs-lookup"><span data-stu-id="fb5f9-156">The default value for tracking type is **Update And Before Render**, to enable the lowest tracking latency.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb5f9-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fb5f9-157">See also</span></span>

- [<span data-ttu-id="fb5f9-158">照相机系统概述</span><span class="sxs-lookup"><span data-stu-id="fb5f9-158">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="fb5f9-159">创建照相机设置提供程序</span><span class="sxs-lookup"><span data-stu-id="fb5f9-159">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
