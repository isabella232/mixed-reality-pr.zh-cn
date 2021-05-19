---
title: 空间对象网格观察程序
description: 有关 MRTK 中的空间网格观察程序的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 51963fca4fa76340089b84e400f2882763977f72
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144457"
---
# <a name="configuring-mesh-observers-for-the-editor"></a><span data-ttu-id="6bfb1-104">为编辑器配置网格观察器</span><span class="sxs-lookup"><span data-stu-id="6bfb1-104">Configuring mesh observers for the editor</span></span>

<span data-ttu-id="6bfb1-105">在 Unity 编辑器中提供环境网格数据的一种简便方法是使用 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 类。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-105">A convenient way to provide environment mesh data in the Unity editor is to use the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class.</span></span> <span data-ttu-id="6bfb1-106">*空间对象网格观察* 程序是用于 [空间感知系统](spatial-awareness-getting-started.md)的仅限编辑器的数据访问接口，它允许导入三维模型数据以表示空间网格。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-106">The *Spatial Object Mesh Observer* is an editor-only data provider for the [Spatial Awareness system](spatial-awareness-getting-started.md) that enables importing 3D model data to represent a spatial mesh.</span></span> <span data-ttu-id="6bfb1-107">*空间对象网格观察* 程序的一种常见用途是导入通过 Microsoft HoloLens 扫描的数据，测试体验如何适应 Unity 内的不同环境。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-107">One common use of the *Spatial Object Mesh Observer* is to import data scanned via a Microsoft HoloLens to test how an experience adapts to different environments from within Unity.</span></span>

## <a name="getting-started"></a><span data-ttu-id="6bfb1-108">入门</span><span class="sxs-lookup"><span data-stu-id="6bfb1-108">Getting started</span></span>

<span data-ttu-id="6bfb1-109">本指南将指导完成设置 *空间对象网格观察* 程序。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-109">This guide will walk through setting up a *Spatial Object Mesh Observer*.</span></span> <span data-ttu-id="6bfb1-110">启用此功能有三个关键步骤。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-110">There are three key steps to enable this feature.</span></span>

1. <span data-ttu-id="6bfb1-111">向空间感知系统配置文件添加 *空间对象网格观察* 程序</span><span class="sxs-lookup"><span data-stu-id="6bfb1-111">Add a *Spatial Object Mesh Observer* to the Spatial Awareness system profile</span></span>
1. <span data-ttu-id="6bfb1-112">设置环境网格数据对象</span><span class="sxs-lookup"><span data-stu-id="6bfb1-112">Set the Environment Mesh Data object</span></span>
1. [<span data-ttu-id="6bfb1-113">配置其他网格观察程序配置文件属性</span><span class="sxs-lookup"><span data-stu-id="6bfb1-113">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a><span data-ttu-id="6bfb1-114">设置 *空间对象网格观察* 程序配置文件</span><span class="sxs-lookup"><span data-stu-id="6bfb1-114">Set up a *spatial object mesh observer* profile</span></span>

1. <span data-ttu-id="6bfb1-115">选择所需的 *混合现实工具包* 配置文件，或者在场景中选择 *混合现实工具包* 对象</span><span class="sxs-lookup"><span data-stu-id="6bfb1-115">Select the desired *Mixed Reality Toolkit* configuration profile or select the *Mixed Reality Toolkit* object in scene</span></span>
1. <span data-ttu-id="6bfb1-116">打开或展开 " *空间感知系统* " 选项卡</span><span class="sxs-lookup"><span data-stu-id="6bfb1-116">Open or expand the *Spatial Awareness System* tab</span></span>
1. <span data-ttu-id="6bfb1-117">单击 *"添加空间观察器"* 按钮</span><span class="sxs-lookup"><span data-stu-id="6bfb1-117">Click on *"Add Spatial Observer"* button</span></span>

    ![添加空间观察程序](../images/spatial-awareness/AddObserver.png)

1. <span data-ttu-id="6bfb1-119">选择 *SpatialObjectMeshObserver* 类型</span><span class="sxs-lookup"><span data-stu-id="6bfb1-119">Select the *SpatialObjectMeshObserver* type</span></span>

    ![选择空间对象网格观察程序](../images/spatial-awareness/SelectObjectObserver.png)

1. <span data-ttu-id="6bfb1-121">选择所需的 *空间网格对象*。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-121">Select the desired *Spatial Mesh Object*.</span></span> <span data-ttu-id="6bfb1-122">默认情况下，使用示例模型配置观察程序。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-122">By default, the observer is configured with an example model.</span></span> <span data-ttu-id="6bfb1-123">此模型是使用 Microsoft HoloLens 创建的，但也可以 [创建新的 scan 网格对象](#acquiring-environment-scans)。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-123">This model was created using a Microsoft HoloLens but it is possible to [create a new scan mesh object](#acquiring-environment-scans).</span></span>
1. [<span data-ttu-id="6bfb1-124">配置网格观察器配置文件属性的其余部分</span><span class="sxs-lookup"><span data-stu-id="6bfb1-124">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

    ![选择网格对象](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a><span data-ttu-id="6bfb1-126">空间对象网格观察器配置文件说明</span><span class="sxs-lookup"><span data-stu-id="6bfb1-126">Spatial object mesh observer profile notes</span></span>

<span data-ttu-id="6bfb1-127">由于 *空间对象网格观察程序* 从 3D 模型加载数据，因此它不支持下面概述的一些标准网格观察程序设置。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-127">Since the *Spatial Object Mesh Observer* loads data from a 3D model, it does not honor some of the standard mesh observer settings which are outlined below.</span></span>

<span data-ttu-id="6bfb1-128">**更新间隔**</span><span class="sxs-lookup"><span data-stu-id="6bfb1-128">**Update Interval**</span></span>

<span data-ttu-id="6bfb1-129">加载  *模型时* ，空间对象网格观察程序会向应用程序发送所有网格。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-129">The  *Spatial Object Mesh Observer* sends all meshes to an application when the model is loaded.</span></span> <span data-ttu-id="6bfb1-130">它不会模拟更新之间的时间增量。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-130">It does not simulate time deltas between updates.</span></span> <span data-ttu-id="6bfb1-131">应用程序可以通过调用 和 来重新接收网格 [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) 事件 [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) 。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-131">An application can re-receive the mesh events by calling [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) and [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume).</span></span>

<span data-ttu-id="6bfb1-132">**是固定观察者**</span><span class="sxs-lookup"><span data-stu-id="6bfb1-132">**Is Stationary Observer**</span></span>

<span data-ttu-id="6bfb1-133">空间 *对象网格观察器* 将所有 3D 网格对象都考虑为静态，并忽略原点。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-133">The *Spatial Object Mesh Observer* considers all 3D mesh objects to be stationary and disregards origin.</span></span>

<span data-ttu-id="6bfb1-134">**观察者形状和区**</span><span class="sxs-lookup"><span data-stu-id="6bfb1-134">**Observer Shape and Extents**</span></span>

<span data-ttu-id="6bfb1-135">空间  *对象网格观察程序* 将整个 3D 网格发送到应用程序。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-135">The  *Spatial Object Mesh Observer* sends the entire 3D mesh to the application.</span></span> <span data-ttu-id="6bfb1-136">不考虑观察者形状和区。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-136">Observer shape and extents are not considered.</span></span>

<span data-ttu-id="6bfb1-137">**详细信息和三角形级别/三角形/三角形**</span><span class="sxs-lookup"><span data-stu-id="6bfb1-137">**Level of Detail and Triangles / Cubic Meter**</span></span>

<span data-ttu-id="6bfb1-138">将网格发送到应用程序时，观察程序不会尝试查找 3D 模型 LOD。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-138">The Observer does not attempt to find 3D model LODs when sending the meshes to the application.</span></span>

## <a name="acquiring-environment-scans"></a><span data-ttu-id="6bfb1-139">获取环境扫描</span><span class="sxs-lookup"><span data-stu-id="6bfb1-139">Acquiring environment scans</span></span>

<span data-ttu-id="6bfb1-140">本部分概述了用于创建和收集空间网格 *对象* 文件以用于空间对象网格观察 *程序 的其他信息*。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-140">This section outlines additional information to create and gather *Spatial Mesh Object* files for use with the *Spatial Object Mesh Observer*.</span></span>

### <a name="windows-device-portal"></a><span data-ttu-id="6bfb1-141">Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="6bfb1-141">Windows Device Portal</span></span>

<span data-ttu-id="6bfb1-142">该 [Windows 设备门户](/windows/mixed-reality/using-the-windows-device-portal) 可用于从设备下载空间网格（作为 .obj Microsoft HoloLens文件）。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-142">The [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) can be used to download the spatial mesh, as a .obj file, from a Microsoft HoloLens device.</span></span>

1. <span data-ttu-id="6bfb1-143">只需使用 HoloLens 浏览和查看所需环境即可进行扫描</span><span class="sxs-lookup"><span data-stu-id="6bfb1-143">Scan by simply walking and viewing the desired environment with a HoloLens</span></span>
1. <span data-ttu-id="6bfb1-144">使用客户端连接到 HoloLens Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="6bfb1-144">Connect to the HoloLens using the Windows Device Portal</span></span>
1. <span data-ttu-id="6bfb1-145">导航到 *三维视图* 页面</span><span class="sxs-lookup"><span data-stu-id="6bfb1-145">Navigate to the *3D View* page</span></span>
1. <span data-ttu-id="6bfb1-146">单击 "*空间映射*" 部分下的 "*更新*" 按钮</span><span class="sxs-lookup"><span data-stu-id="6bfb1-146">Click the *Update* button under *Spatial Mapping* section</span></span>
1. <span data-ttu-id="6bfb1-147">单击 "*空间映射*" 部分下的 "*保存*" 按钮，将 OBJ 文件保存到 PC</span><span class="sxs-lookup"><span data-stu-id="6bfb1-147">Click the *Save* button under *Spatial Mapping* section to save the obj file to PC</span></span>

> [!NOTE]
> <span data-ttu-id="6bfb1-148">**HoloToolkit 文件**</span><span class="sxs-lookup"><span data-stu-id="6bfb1-148">**HoloToolkit .room files**</span></span>
>
> <span data-ttu-id="6bfb1-149">许多开发人员以前使用 HoloToolkit 来扫描环境并创建文件室文件。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-149">Many developers will have previously used HoloToolkit to scan environments and create .room files.</span></span> <span data-ttu-id="6bfb1-150">混合现实工具包现在支持将这些文件导入到 Unity 中的 Gameobject，并将其用作观察程序中的 *空间网格对象* 。</span><span class="sxs-lookup"><span data-stu-id="6bfb1-150">The Mixed Reality Toolkit now supports importing these files as GameObjects in Unity and use them as *Spatial Mesh Objects* in the observer.</span></span>

## <a name="see-also"></a><span data-ttu-id="6bfb1-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6bfb1-151">See also</span></span>

- [<span data-ttu-id="6bfb1-152">Profiles</span><span class="sxs-lookup"><span data-stu-id="6bfb1-152">Profiles</span></span>](../profiles/profiles.md)
- [<span data-ttu-id="6bfb1-153">混合现实工具包配置文件配置指南</span><span class="sxs-lookup"><span data-stu-id="6bfb1-153">Mixed Reality Toolkit Profile configuration guide</span></span>](../../configuration/mixed-reality-configuration-guide.md)
- [<span data-ttu-id="6bfb1-154">空间感知入门</span><span class="sxs-lookup"><span data-stu-id="6bfb1-154">Spatial Awareness Getting started</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="6bfb1-155">在设备上配置网格观察器</span><span class="sxs-lookup"><span data-stu-id="6bfb1-155">Configuring Mesh Observers on Device</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="6bfb1-156">通过代码配置网格观察器</span><span class="sxs-lookup"><span data-stu-id="6bfb1-156">Configuring Mesh Observers via code</span></span>](usage-guide.md)
- [<span data-ttu-id="6bfb1-157">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="6bfb1-157">Using the Windows Device Portal</span></span>](/windows/mixed-reality/using-the-windows-device-portal)