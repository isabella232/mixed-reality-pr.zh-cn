---
title: 配置空间感知网格观察程序
description: 如何在 MRTK 中配置现用空间网格观察器
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 0d71a32d76624698e78b8123f427ddefc08f3d0b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144968"
---
# <a name="configuring-mesh-observers-for-device"></a><span data-ttu-id="0c5a4-104">为设备配置网格观察程序</span><span class="sxs-lookup"><span data-stu-id="0c5a4-104">Configuring mesh observers for device</span></span>

<span data-ttu-id="0c5a4-105">本指南将演练在 MRTK 中配置现成空间网格观察程序，该观察程序支持Windows Mixed Reality平台 (即</span><span class="sxs-lookup"><span data-stu-id="0c5a4-105">This guide will walk through configuring the out-of-box Spatial Mesh Observer in MRTK which supports the Windows Mixed Reality platform (i.e</span></span> <span data-ttu-id="0c5a4-106">HoloLens) 。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-106">HoloLens).</span></span> <span data-ttu-id="0c5a4-107">混合现实工具包提供的默认实现是 [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 类。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-107">The default implementation provided by the Mixed Reality Toolkit is the [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span> <span data-ttu-id="0c5a4-108">不过，本文中的许多属性适用于其他 [自定义观察者实现](create-data-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-108">Many of the properties in this article though apply for other [custom Observer implementations](create-data-provider.md).</span></span>

## <a name="profile-settings"></a><span data-ttu-id="0c5a4-109">配置文件设置</span><span class="sxs-lookup"><span data-stu-id="0c5a4-109">Profile settings</span></span>

<span data-ttu-id="0c5a4-110">为空间感知系统 配置空间网格观察程序配置文件时，必须先定义以下两 [项](spatial-awareness-getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-110">The following two items must be defined first when configuring a Spatial Mesh Observer profile for the [Spatial Awareness system](spatial-awareness-getting-started.md).</span></span>

1. <span data-ttu-id="0c5a4-111">具体观察者类型实现</span><span class="sxs-lookup"><span data-stu-id="0c5a4-111">The concrete observer type implementation</span></span>
1. <span data-ttu-id="0c5a4-112">用于运行此 () 支持的平台列表</span><span class="sxs-lookup"><span data-stu-id="0c5a4-112">list of supported platform(s) to run this observer</span></span>

> [!NOTE]
> <span data-ttu-id="0c5a4-113">所有观察程序都必须扩展 [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 接口。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-113">All observers must extend the [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![网格观察器常规设置平台类型](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a><span data-ttu-id="0c5a4-115">常规设置</span><span class="sxs-lookup"><span data-stu-id="0c5a4-115">General settings</span></span>

![网格观察器常规设置常规设置](../images/spatial-awareness/MeshObserverGeneralSettings.png)

<span data-ttu-id="0c5a4-117">**启动行为**</span><span class="sxs-lookup"><span data-stu-id="0c5a4-117">**Startup Behavior**</span></span>

<span data-ttu-id="0c5a4-118">启动行为指定观察程序在首次实例化时是否开始运行。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-118">The startup behavior specifies whether the observer will begin running when first instantiated.</span></span> <span data-ttu-id="0c5a4-119">这两个选项如下：</span><span class="sxs-lookup"><span data-stu-id="0c5a4-119">The two options are:</span></span>

* <span data-ttu-id="0c5a4-120">*自动启动* - 默认值，在此默认值中，观察者将在初始化后开始操作</span><span class="sxs-lookup"><span data-stu-id="0c5a4-120">*Auto Start* - The default value whereby the observer will begin operation after initialization</span></span>
* <span data-ttu-id="0c5a4-121">*手动启动* - 观察程序将等待定向到启动</span><span class="sxs-lookup"><span data-stu-id="0c5a4-121">*Manual Start* - The Observer will wait to be directed to start</span></span>

<span data-ttu-id="0c5a4-122">如果使用手动 *启动*，则必须 [在运行时通过代码 恢复和挂起它们](usage-guide.md#starting-and-stopping-mesh-observation)。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-122">If using *Manual Start*, one must [resume and suspend them at runtime via code](usage-guide.md#starting-and-stopping-mesh-observation).</span></span>

<span data-ttu-id="0c5a4-123">**更新间隔**</span><span class="sxs-lookup"><span data-stu-id="0c5a4-123">**Update Interval**</span></span>

<span data-ttu-id="0c5a4-124">请求平台更新空间网格数据之间的时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-124">The time, in seconds, between requests to the platform to update spatial mesh data.</span></span> <span data-ttu-id="0c5a4-125">典型值的范围为 0.1 和 5.0 秒。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-125">Typical values fall in the range of 0.1 and 5.0 seconds.</span></span>

<span data-ttu-id="0c5a4-126">**为静止观察程序**</span><span class="sxs-lookup"><span data-stu-id="0c5a4-126">**Is Stationary Observer**</span></span>

<span data-ttu-id="0c5a4-127">指示观察者是保持静止还是与用户一起移动和更新。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-127">Indicates whether or not the observer is to remain stationary or to move and update with the user.</span></span> <span data-ttu-id="0c5a4-128">如果为 true，则在启动时，具有由 *观察范围* 定义的卷的 *观察者形状* 将保持为源。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-128">If true, the *Observer Shape* with volume defined by *Observation Extents* will remain at the origin on startup.</span></span> <span data-ttu-id="0c5a4-129">如果为 false，则观察者空间将跟随用户的头作为形状的原点。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-129">If false, the Observer space will follow the user's head as the shape's origin.</span></span>

<span data-ttu-id="0c5a4-130">将不会为这些属性所定义的观察者空间之外的任何物理区域计算网格数据： *是静止观察程序*、\* 观察器形状 \* \* 和 *观察区*。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-130">There will be no mesh data calculated for any physical area outside of the Observer space as defined by these properties: *Is Stationary Observer*, \*Observer Shape\*\*, and *Observation Extents*.</span></span>

<span data-ttu-id="0c5a4-131">**观察者形状**</span><span class="sxs-lookup"><span data-stu-id="0c5a4-131">**Observer Shape**</span></span>

<span data-ttu-id="0c5a4-132">"观察者" 形状定义网格观察器在观察网格时将使用的卷的类型。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-132">The observer shape defines the type of volume that the mesh observer will use when observing meshes.</span></span> <span data-ttu-id="0c5a4-133">支持的选项包括：</span><span class="sxs-lookup"><span data-stu-id="0c5a4-133">The supported options are:</span></span>

* <span data-ttu-id="0c5a4-134">*轴对齐的多维数据集* -与世界坐标系统的轴对齐的矩形形状，在应用程序启动时确定。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-134">*Axis Aligned Cube* - Rectangular shape that stays aligned with the axes of the world coordinate system, as determined at application startup.</span></span>
* <span data-ttu-id="0c5a4-135">*用户对齐的多维数据集* -旋转以与用户本地坐标系统对齐的矩形形状。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-135">*User Aligned Cube* - Rectangular shape that rotates to align with the users local coordinate system.</span></span>
* <span data-ttu-id="0c5a4-136">*球* -带有世界空间原点中心的球面体积。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-136">*Sphere* - A spherical volume with a center at the world space origin.</span></span> <span data-ttu-id="0c5a4-137">" *观察范围* " 属性的 X 值将用作球的半径。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-137">The X value of the *Observation Extents* property will be used as the radius of the sphere.</span></span>

<span data-ttu-id="0c5a4-138">**观察范围**</span><span class="sxs-lookup"><span data-stu-id="0c5a4-138">**Observation Extents**</span></span>

<span data-ttu-id="0c5a4-139">"观察范围" 定义观察到的网格的距离。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-139">The observation extents define the distance from the observation point that meshes will be observed.</span></span>

### <a name="physics-settings"></a><span data-ttu-id="0c5a4-140">物理设置</span><span class="sxs-lookup"><span data-stu-id="0c5a4-140">Physics settings</span></span>

![网格观察器物理设置](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

<span data-ttu-id="0c5a4-142">**物理层**</span><span class="sxs-lookup"><span data-stu-id="0c5a4-142">**Physics Layer**</span></span>

<span data-ttu-id="0c5a4-143">将在其中放置空间网格对象以便与 Unity 物理学和 RayCast 系统交互的物理层。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-143">The physics layer on which spatial mesh objects will be placed in order to interact with the Unity Physics and RayCast systems.</span></span>

> [!NOTE]
> <span data-ttu-id="0c5a4-144">默认情况下，混合现实工具包保留 *第31层* 供空间感知观察程序使用。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-144">The Mixed Reality Toolkit reserves *layer 31* by default for use by Spatial Awareness observers.</span></span>

<span data-ttu-id="0c5a4-145">**重新计算法线**</span><span class="sxs-lookup"><span data-stu-id="0c5a4-145">**Recalculate Normals**</span></span>

<span data-ttu-id="0c5a4-146">指定网格观察器是否将在观察后重新计算网格的法线。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-146">Specifies whether or not the mesh observer will recalculate the normals of the mesh following observation.</span></span> <span data-ttu-id="0c5a4-147">此设置可用于确保应用程序在不使用网格返回它们的平台上接收包含有效的法线数据的网格。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-147">This setting is available to ensure applications receive meshes that contain valid normals data on platforms that do not return them with meshes.</span></span>

### <a name="level-of-detail-settings"></a><span data-ttu-id="0c5a4-148">详细信息设置级别</span><span class="sxs-lookup"><span data-stu-id="0c5a4-148">Level of detail settings</span></span>

![网格观察程序级别的详细信息设置](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

<span data-ttu-id="0c5a4-150">**详细信息级别**</span><span class="sxs-lookup"><span data-stu-id="0c5a4-150">**Level of Detail**</span></span>

<span data-ttu-id="0c5a4-151">指定空间网格数据 (LOD) 的详细级别。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-151">Specifies the level of detail (LOD) of the spatial mesh data.</span></span> <span data-ttu-id="0c5a4-152">当前定义的值是粗、精细和自定义的。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-152">Currently defined values are Coarse, Fine and Custom.</span></span>

* <span data-ttu-id="0c5a4-153">*粗* -对应用程序性能的影响较小，并且是导航/平面查找的最佳选择。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-153">*Coarse* - Places a smaller impact on application performance and is an excellent choice for navigation/plane finding.</span></span>

* <span data-ttu-id="0c5a4-154">"*中等* 平衡" 设置通常适用于对大型功能、地面和墙壁以及封闭详细信息持续扫描环境的体验。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-154">*Medium* - Balanced setting often useful for experiences that continually scan the environment for both large features, floors and walls, as well as occlusion details.</span></span>

* <span data-ttu-id="0c5a4-155">*正常* 情况下，exacts 对应用程序性能的影响较高，对于封闭网格非常有用。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-155">*Fine* - Generally exacts a higher impact on application performance and is a great option for occlusion meshes.</span></span>

* <span data-ttu-id="0c5a4-156">*自定义* -要求应用程序指定 *三角形/立方米计量* 属性，并使应用程序能够优化性能和对空间网格观察程序性能的影响。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-156">*Custom* - Requires the application to specify the *Triangles / Cubic Meter* property and allows applications to tune the accuracy vs. performance impact of the spatial mesh observer.</span></span>

> [!NOTE]
> <span data-ttu-id="0c5a4-157">不能保证所有的 *三角形/立方计量* 值都由所有平台所接受。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-157">It is not guaranteed that all *Triangles/Cubic Meter* values are honored by all platforms.</span></span> <span data-ttu-id="0c5a4-158">使用自定义 LOD 时，强烈建议使用试验和分析。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-158">Experimentation and profiling is highly recommended when using a custom LOD.</span></span>

<span data-ttu-id="0c5a4-159">**每个立方计量的三角形**</span><span class="sxs-lookup"><span data-stu-id="0c5a4-159">**Triangles per Cubic Meter**</span></span>

<span data-ttu-id="0c5a4-160">使用 "**详细信息级别**" 属性的 "*自定义*" 设置并为空间网格指定三角形密度时有效。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-160">Valid when using the *Custom* setting for the **Level of Detail** property and specifies the triangle density for the spatial mesh.</span></span>

### <a name="display-settings"></a><span data-ttu-id="0c5a4-161">显示设置</span><span class="sxs-lookup"><span data-stu-id="0c5a4-161">Display settings</span></span>

![网格观察程序显示设置](../images/spatial-awareness/MeshObserverDisplaySettings.png)

<span data-ttu-id="0c5a4-163">**显示选项**</span><span class="sxs-lookup"><span data-stu-id="0c5a4-163">**Display Option**</span></span>

<span data-ttu-id="0c5a4-164">指定观察者如何显示空间网格。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-164">Specifies how spatial meshes are to be displayed by the observer.</span></span> <span data-ttu-id="0c5a4-165">支持的值是：</span><span class="sxs-lookup"><span data-stu-id="0c5a4-165">Supported values are:</span></span>

* <span data-ttu-id="0c5a4-166">*无* -观察程序将不呈现网格</span><span class="sxs-lookup"><span data-stu-id="0c5a4-166">*None* - Observer will not render the mesh</span></span>
* <span data-ttu-id="0c5a4-167">*可见的数据* 将使用 *可见材料* 显示</span><span class="sxs-lookup"><span data-stu-id="0c5a4-167">*Visible* - Mesh data will be visible using the *Visible Material*</span></span>
* <span data-ttu-id="0c5a4-168">*遮挡* - 网格数据将是场景中使用遮挡材料的 *遮挡项*</span><span class="sxs-lookup"><span data-stu-id="0c5a4-168">*Occlusion* - Mesh data will be occlude items in scene using the *Occlusion Material*</span></span>

![选择空间感知系统实现](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

<span data-ttu-id="0c5a4-170">可以通过代码在运行时 [恢复/挂起空间观察程序。](usage-guide.md#starting-and-stopping-mesh-observation)</span><span class="sxs-lookup"><span data-stu-id="0c5a4-170">Spatial Observers can be [resumed/suspended at runtime via code.](usage-guide.md#starting-and-stopping-mesh-observation)</span></span>

> [!WARNING]
> <span data-ttu-id="0c5a4-171">将 *"显示选项\*\*"设置为"无\*\*\*"不会阻止*\* 观察程序运行。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-171">Setting *Display Option* to *None* does **NOT** stop the observer from running.</span></span> <span data-ttu-id="0c5a4-172">如果要停止所有观察程序，应用程序将需要通过 暂停所有观察程序 [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span><span class="sxs-lookup"><span data-stu-id="0c5a4-172">If you wish to stop all observers, applications will need to suspend all observers via [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span></span>

<span data-ttu-id="0c5a4-173">**可见材料**</span><span class="sxs-lookup"><span data-stu-id="0c5a4-173">**Visible Material**</span></span>

<span data-ttu-id="0c5a4-174">指示可视化空间网格时所使用的材料。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-174">Indicates the material to be used when visualizing the spatial mesh.</span></span>

<span data-ttu-id="0c5a4-175">**遮挡材料**</span><span class="sxs-lookup"><span data-stu-id="0c5a4-175">**Occlusion Material**</span></span>

<span data-ttu-id="0c5a4-176">指示用于使空间网格遮挡全息影像的材料。</span><span class="sxs-lookup"><span data-stu-id="0c5a4-176">Indicates the material to be used to cause the spatial mesh to occlude holograms.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c5a4-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0c5a4-177">See also</span></span>

* [<span data-ttu-id="0c5a4-178">空间感知系统</span><span class="sxs-lookup"><span data-stu-id="0c5a4-178">Spatial Awareness System</span></span>](spatial-awareness-getting-started.md)
* [<span data-ttu-id="0c5a4-179">通过代码配置空间感知系统</span><span class="sxs-lookup"><span data-stu-id="0c5a4-179">Configuring Spatial Awareness system via Code</span></span>](usage-guide.md)
* [<span data-ttu-id="0c5a4-180">IMixedRealitySpatialAwarenessObserver API 文档</span><span class="sxs-lookup"><span data-stu-id="0c5a4-180">IMixedRealitySpatialAwarenessObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [<span data-ttu-id="0c5a4-181">IMixedRealitySpatialAwarenessMeshObserver API 文档</span><span class="sxs-lookup"><span data-stu-id="0c5a4-181">IMixedRealitySpatialAwarenessMeshObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [<span data-ttu-id="0c5a4-182">BaseSpatialObserver API 文档</span><span class="sxs-lookup"><span data-stu-id="0c5a4-182">BaseSpatialObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
