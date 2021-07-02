---
title: 空间对象网格观察器
description: 有关 MRTK 中空间网格观察程序的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: db0b2f14d0a5d65140223d3fa3f4f5324ef2ba76
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176691"
---
# <a name="spatial-object-mesh-observer"></a><span data-ttu-id="4e90d-104">空间对象网格观察器</span><span class="sxs-lookup"><span data-stu-id="4e90d-104">Spatial object mesh observer</span></span>

<span data-ttu-id="4e90d-105">在 Unity 编辑器中提供环境网格数据的便捷方法就是使用 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 类。</span><span class="sxs-lookup"><span data-stu-id="4e90d-105">A convenient way to provide environment mesh data in the Unity editor is to use the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class.</span></span> <span data-ttu-id="4e90d-106">空间 *对象网格观察* 程序是空间感知系统的仅编辑器数据访问接口，[](spatial-awareness-getting-started.md)允许导入三维模型数据来表示空间网格。</span><span class="sxs-lookup"><span data-stu-id="4e90d-106">The *Spatial Object Mesh Observer* is an editor-only data provider for the [Spatial Awareness system](spatial-awareness-getting-started.md) that enables importing 3D model data to represent a spatial mesh.</span></span> <span data-ttu-id="4e90d-107">空间对象网格观察者的一个常见用途是通过 Microsoft HoloLens 导入扫描的数据，以测试体验如何适应 Unity 中的不同环境。</span><span class="sxs-lookup"><span data-stu-id="4e90d-107">One common use of the *Spatial Object Mesh Observer* is to import data scanned via a Microsoft HoloLens to test how an experience adapts to different environments from within Unity.</span></span>

## <a name="getting-started"></a><span data-ttu-id="4e90d-108">入门</span><span class="sxs-lookup"><span data-stu-id="4e90d-108">Getting started</span></span>

<span data-ttu-id="4e90d-109">本指南将演练设置空间对象 *网格观察器*。</span><span class="sxs-lookup"><span data-stu-id="4e90d-109">This guide will walk through setting up a *Spatial Object Mesh Observer*.</span></span> <span data-ttu-id="4e90d-110">启用此功能有三个关键步骤。</span><span class="sxs-lookup"><span data-stu-id="4e90d-110">There are three key steps to enable this feature.</span></span>

1. <span data-ttu-id="4e90d-111">将空间 *对象网格观察器* 添加到空间感知系统配置文件</span><span class="sxs-lookup"><span data-stu-id="4e90d-111">Add a *Spatial Object Mesh Observer* to the Spatial Awareness system profile</span></span>
1. <span data-ttu-id="4e90d-112">设置环境网格数据对象</span><span class="sxs-lookup"><span data-stu-id="4e90d-112">Set the Environment Mesh Data object</span></span>
1. [<span data-ttu-id="4e90d-113">配置网格观察器配置文件属性的其余部分</span><span class="sxs-lookup"><span data-stu-id="4e90d-113">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a><span data-ttu-id="4e90d-114">设置空间 *对象网格观察器* 配置文件</span><span class="sxs-lookup"><span data-stu-id="4e90d-114">Set up a *spatial object mesh observer* profile</span></span>

1. <span data-ttu-id="4e90d-115">选择所需的 *混合现实Toolkit* 配置文件，或选择场景中 *的混合现实Toolkit* 对象</span><span class="sxs-lookup"><span data-stu-id="4e90d-115">Select the desired *Mixed Reality Toolkit* configuration profile or select the *Mixed Reality Toolkit* object in scene</span></span>
1. <span data-ttu-id="4e90d-116">打开或展开" *空间感知系统"* 选项卡</span><span class="sxs-lookup"><span data-stu-id="4e90d-116">Open or expand the *Spatial Awareness System* tab</span></span>
1. <span data-ttu-id="4e90d-117">单击" *添加空间观察器"* 按钮</span><span class="sxs-lookup"><span data-stu-id="4e90d-117">Click on *"Add Spatial Observer"* button</span></span>

    ![添加空间观察器](../images/spatial-awareness/AddObserver.png)

1. <span data-ttu-id="4e90d-119">选择 *SpatialObjectMeshObserver* 类型</span><span class="sxs-lookup"><span data-stu-id="4e90d-119">Select the *SpatialObjectMeshObserver* type</span></span>

    ![选择空间对象网格观察器](../images/spatial-awareness/SelectObjectObserver.png)

1. <span data-ttu-id="4e90d-121">选择所需的 *空间网格对象*。</span><span class="sxs-lookup"><span data-stu-id="4e90d-121">Select the desired *Spatial Mesh Object*.</span></span> <span data-ttu-id="4e90d-122">默认情况下，使用示例模型配置观察程序。</span><span class="sxs-lookup"><span data-stu-id="4e90d-122">By default, the observer is configured with an example model.</span></span> <span data-ttu-id="4e90d-123">此模型是使用 Microsoft HoloLens创建的，但可以[创建新的扫描网格对象](#acquiring-environment-scans)。</span><span class="sxs-lookup"><span data-stu-id="4e90d-123">This model was created using a Microsoft HoloLens but it is possible to [create a new scan mesh object](#acquiring-environment-scans).</span></span>
1. [<span data-ttu-id="4e90d-124">配置网格观察器配置文件属性的其余部分</span><span class="sxs-lookup"><span data-stu-id="4e90d-124">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

    ![选择网格对象](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a><span data-ttu-id="4e90d-126">空间对象网格观察器配置文件说明</span><span class="sxs-lookup"><span data-stu-id="4e90d-126">Spatial object mesh observer profile notes</span></span>

<span data-ttu-id="4e90d-127">由于 *空间对象网格观察程序* 从 3D 模型加载数据，因此它不支持下面概述的一些标准网格观察程序设置。</span><span class="sxs-lookup"><span data-stu-id="4e90d-127">Since the *Spatial Object Mesh Observer* loads data from a 3D model, it does not honor some of the standard mesh observer settings which are outlined below.</span></span>

<span data-ttu-id="4e90d-128">**更新间隔**</span><span class="sxs-lookup"><span data-stu-id="4e90d-128">**Update Interval**</span></span>

<span data-ttu-id="4e90d-129">加载  *模型时* ，空间对象网格观察程序会向应用程序发送所有网格。</span><span class="sxs-lookup"><span data-stu-id="4e90d-129">The  *Spatial Object Mesh Observer* sends all meshes to an application when the model is loaded.</span></span> <span data-ttu-id="4e90d-130">它不会模拟更新之间的时间增量。</span><span class="sxs-lookup"><span data-stu-id="4e90d-130">It does not simulate time deltas between updates.</span></span> <span data-ttu-id="4e90d-131">应用程序可以通过调用 和 来重新接收网格 [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) 事件 [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) 。</span><span class="sxs-lookup"><span data-stu-id="4e90d-131">An application can re-receive the mesh events by calling [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) and [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume).</span></span>

<span data-ttu-id="4e90d-132">**是固定观察者**</span><span class="sxs-lookup"><span data-stu-id="4e90d-132">**Is Stationary Observer**</span></span>

<span data-ttu-id="4e90d-133">空间 *对象网格观察器* 将所有 3D 网格对象都考虑为静态，并忽略原点。</span><span class="sxs-lookup"><span data-stu-id="4e90d-133">The *Spatial Object Mesh Observer* considers all 3D mesh objects to be stationary and disregards origin.</span></span>

<span data-ttu-id="4e90d-134">**观察者形状和区**</span><span class="sxs-lookup"><span data-stu-id="4e90d-134">**Observer Shape and Extents**</span></span>

<span data-ttu-id="4e90d-135">空间  *对象网格观察程序* 将整个 3D 网格发送到应用程序。</span><span class="sxs-lookup"><span data-stu-id="4e90d-135">The  *Spatial Object Mesh Observer* sends the entire 3D mesh to the application.</span></span> <span data-ttu-id="4e90d-136">不考虑观察者形状和区。</span><span class="sxs-lookup"><span data-stu-id="4e90d-136">Observer shape and extents are not considered.</span></span>

<span data-ttu-id="4e90d-137">**详细信息和三角形级别/三角形/三角形**</span><span class="sxs-lookup"><span data-stu-id="4e90d-137">**Level of Detail and Triangles / Cubic Meter**</span></span>

<span data-ttu-id="4e90d-138">将网格发送到应用程序时，观察程序不会尝试查找 3D 模型 LOD。</span><span class="sxs-lookup"><span data-stu-id="4e90d-138">The Observer does not attempt to find 3D model LODs when sending the meshes to the application.</span></span>

## <a name="acquiring-environment-scans"></a><span data-ttu-id="4e90d-139">获取环境扫描</span><span class="sxs-lookup"><span data-stu-id="4e90d-139">Acquiring environment scans</span></span>

<span data-ttu-id="4e90d-140">本部分概述了用于创建和收集空间网格 *对象* 文件以用于空间对象网格观察 *程序 的其他信息*。</span><span class="sxs-lookup"><span data-stu-id="4e90d-140">This section outlines additional information to create and gather *Spatial Mesh Object* files for use with the *Spatial Object Mesh Observer*.</span></span>

### <a name="windows-device-portal"></a><span data-ttu-id="4e90d-141">Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="4e90d-141">Windows Device Portal</span></span>

<span data-ttu-id="4e90d-142">该[Windows 设备门户](/windows/mixed-reality/using-the-windows-device-portal)可用于从设备下载空间网格（作为 .obj Microsoft HoloLens文件）。</span><span class="sxs-lookup"><span data-stu-id="4e90d-142">The [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) can be used to download the spatial mesh, as a .obj file, from a Microsoft HoloLens device.</span></span>

1. <span data-ttu-id="4e90d-143">只需通过快速浏览和查看所需环境即可HoloLens</span><span class="sxs-lookup"><span data-stu-id="4e90d-143">Scan by simply walking and viewing the desired environment with a HoloLens</span></span>
1. <span data-ttu-id="4e90d-144">连接HoloLens Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="4e90d-144">Connect to the HoloLens using the Windows Device Portal</span></span>
1. <span data-ttu-id="4e90d-145">导航到 *"三维视图"* 页</span><span class="sxs-lookup"><span data-stu-id="4e90d-145">Navigate to the *3D View* page</span></span>
1. <span data-ttu-id="4e90d-146">单击"空间 *映射"\*\*部分下的"更新"* 按钮</span><span class="sxs-lookup"><span data-stu-id="4e90d-146">Click the *Update* button under *Spatial Mapping* section</span></span>
1. <span data-ttu-id="4e90d-147">单击" *空间映射* " *部分下的* "保存"按钮，将 obj 文件保存到电脑</span><span class="sxs-lookup"><span data-stu-id="4e90d-147">Click the *Save* button under *Spatial Mapping* section to save the obj file to PC</span></span>

> [!NOTE]
> <span data-ttu-id="4e90d-148">**HoloToolkit .room 文件**</span><span class="sxs-lookup"><span data-stu-id="4e90d-148">**HoloToolkit .room files**</span></span>
>
> <span data-ttu-id="4e90d-149">许多开发人员以前会使用 HoloToolkit 扫描环境并创建 .room 文件。</span><span class="sxs-lookup"><span data-stu-id="4e90d-149">Many developers will have previously used HoloToolkit to scan environments and create .room files.</span></span> <span data-ttu-id="4e90d-150">混合现实Toolkit现在支持在 Unity 中将这些文件导入为 GameObjects，并使用它们作为观察 *程序* 中的空间网格对象。</span><span class="sxs-lookup"><span data-stu-id="4e90d-150">The Mixed Reality Toolkit now supports importing these files as GameObjects in Unity and use them as *Spatial Mesh Objects* in the observer.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e90d-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4e90d-151">See also</span></span>

- [<span data-ttu-id="4e90d-152">Profiles</span><span class="sxs-lookup"><span data-stu-id="4e90d-152">Profiles</span></span>](../profiles/profiles.md)
- [<span data-ttu-id="4e90d-153">混合现实Toolkit配置文件配置指南</span><span class="sxs-lookup"><span data-stu-id="4e90d-153">Mixed Reality Toolkit Profile configuration guide</span></span>](../../configuration/mixed-reality-configuration-guide.md)
- [<span data-ttu-id="4e90d-154">空间感知入门</span><span class="sxs-lookup"><span data-stu-id="4e90d-154">Spatial Awareness Getting started</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="4e90d-155">在设备上配置网格观察程序</span><span class="sxs-lookup"><span data-stu-id="4e90d-155">Configuring Mesh Observers on Device</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="4e90d-156">通过代码配置网格观察程序</span><span class="sxs-lookup"><span data-stu-id="4e90d-156">Configuring Mesh Observers via code</span></span>](usage-guide.md)
- [<span data-ttu-id="4e90d-157">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="4e90d-157">Using the Windows Device Portal</span></span>](/windows/mixed-reality/using-the-windows-device-portal)
