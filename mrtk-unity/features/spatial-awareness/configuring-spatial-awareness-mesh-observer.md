---
title: 为设备配置网格观察程序
description: 如何在 MRTK 中配置现用空间网格观察器
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: aba49e88d4fc555a88fe42e4b09858f1d2453ddc
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281938"
---
# <a name="configuring-mesh-observers-for-device"></a><span data-ttu-id="05459-104">为设备配置网格观察程序</span><span class="sxs-lookup"><span data-stu-id="05459-104">Configuring mesh observers for device</span></span>

<span data-ttu-id="05459-105">本指南将演练在 MRTK 中配置现成空间网格观察程序，该观察程序支持Windows Mixed Reality平台 (，即</span><span class="sxs-lookup"><span data-stu-id="05459-105">This guide will walk through configuring the out-of-box Spatial Mesh Observer in MRTK which supports the Windows Mixed Reality platform (i.e</span></span> <span data-ttu-id="05459-106">HoloLens) 。</span><span class="sxs-lookup"><span data-stu-id="05459-106">HoloLens).</span></span> <span data-ttu-id="05459-107">混合现实应用程序提供的默认实现Toolkit [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)类。</span><span class="sxs-lookup"><span data-stu-id="05459-107">The default implementation provided by the Mixed Reality Toolkit is the [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span> <span data-ttu-id="05459-108">不过，本文中的许多属性适用于其他 [自定义观察者实现](create-data-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="05459-108">Many of the properties in this article though apply for other [custom Observer implementations](create-data-provider.md).</span></span>

## <a name="profile-settings"></a><span data-ttu-id="05459-109">配置文件设置</span><span class="sxs-lookup"><span data-stu-id="05459-109">Profile settings</span></span>

<span data-ttu-id="05459-110">为空间感知系统 配置空间网格观察程序配置文件时，必须先定义以下两 [项](spatial-awareness-getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="05459-110">The following two items must be defined first when configuring a Spatial Mesh Observer profile for the [Spatial Awareness system](spatial-awareness-getting-started.md).</span></span>

1. <span data-ttu-id="05459-111">具体观察者类型实现</span><span class="sxs-lookup"><span data-stu-id="05459-111">The concrete observer type implementation</span></span>
1. <span data-ttu-id="05459-112">用于运行此 () 支持的平台列表</span><span class="sxs-lookup"><span data-stu-id="05459-112">list of supported platform(s) to run this observer</span></span>

> [!NOTE]
> <span data-ttu-id="05459-113">所有观察程序都必须扩展 [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 接口。</span><span class="sxs-lookup"><span data-stu-id="05459-113">All observers must extend the [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![网格观察器常规设置平台类型](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a><span data-ttu-id="05459-115">常规设置</span><span class="sxs-lookup"><span data-stu-id="05459-115">General settings</span></span>

![网格观察器常规设置常规设置](../images/spatial-awareness/MeshObserverGeneralSettings.png)

<span data-ttu-id="05459-117">**启动行为**</span><span class="sxs-lookup"><span data-stu-id="05459-117">**Startup Behavior**</span></span>

<span data-ttu-id="05459-118">启动行为指定观察程序在首次实例化时是否开始运行。</span><span class="sxs-lookup"><span data-stu-id="05459-118">The startup behavior specifies whether the observer will begin running when first instantiated.</span></span> <span data-ttu-id="05459-119">这两个选项如下：</span><span class="sxs-lookup"><span data-stu-id="05459-119">The two options are:</span></span>

* <span data-ttu-id="05459-120">*自动启动* - 默认值，在此默认值中，观察者将在初始化后开始操作</span><span class="sxs-lookup"><span data-stu-id="05459-120">*Auto Start* - The default value whereby the observer will begin operation after initialization</span></span>
* <span data-ttu-id="05459-121">*手动启动* - 观察程序将等待定向到启动</span><span class="sxs-lookup"><span data-stu-id="05459-121">*Manual Start* - The Observer will wait to be directed to start</span></span>

<span data-ttu-id="05459-122">如果使用手动 *启动*，则必须 [在运行时通过代码 恢复和挂起它们](usage-guide.md#starting-and-stopping-mesh-observation)。</span><span class="sxs-lookup"><span data-stu-id="05459-122">If using *Manual Start*, one must [resume and suspend them at runtime via code](usage-guide.md#starting-and-stopping-mesh-observation).</span></span>

<span data-ttu-id="05459-123">**更新间隔**</span><span class="sxs-lookup"><span data-stu-id="05459-123">**Update Interval**</span></span>

<span data-ttu-id="05459-124">请求平台更新空间网格数据之间的时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="05459-124">The time, in seconds, between requests to the platform to update spatial mesh data.</span></span> <span data-ttu-id="05459-125">典型值的范围为 0.1 和 5.0 秒。</span><span class="sxs-lookup"><span data-stu-id="05459-125">Typical values fall in the range of 0.1 and 5.0 seconds.</span></span>

<span data-ttu-id="05459-126">**是固定观察者**</span><span class="sxs-lookup"><span data-stu-id="05459-126">**Is Stationary Observer**</span></span>

<span data-ttu-id="05459-127">指示观察程序是保持静止状态，还是与用户一起移动和更新。</span><span class="sxs-lookup"><span data-stu-id="05459-127">Indicates whether or not the observer is to remain stationary or to move and update with the user.</span></span> <span data-ttu-id="05459-128">如果为 *true，则* 具有由观察区定义的卷的观察程序 *形状在启动时* 将保留在原点。</span><span class="sxs-lookup"><span data-stu-id="05459-128">If true, the *Observer Shape* with volume defined by *Observation Extents* will remain at the origin on startup.</span></span> <span data-ttu-id="05459-129">如果为 false，则观察者空间将跟随用户的头部作为形状的原点。</span><span class="sxs-lookup"><span data-stu-id="05459-129">If false, the Observer space will follow the user's head as the shape's origin.</span></span>

<span data-ttu-id="05459-130">对于观察器空间之外的任何物理区域，不会根据以下属性的定义计算网格数据：是固定观察者、\*观察者形状\*\*和观察 *区*。 </span><span class="sxs-lookup"><span data-stu-id="05459-130">There will be no mesh data calculated for any physical area outside of the Observer space as defined by these properties: *Is Stationary Observer*, \*Observer Shape\*\*, and *Observation Extents*.</span></span>

<span data-ttu-id="05459-131">**观察者形状**</span><span class="sxs-lookup"><span data-stu-id="05459-131">**Observer Shape**</span></span>

<span data-ttu-id="05459-132">观察者形状定义网格观察器在观察网格时将使用的卷的类型。</span><span class="sxs-lookup"><span data-stu-id="05459-132">The observer shape defines the type of volume that the mesh observer will use when observing meshes.</span></span> <span data-ttu-id="05459-133">支持的选项包括：</span><span class="sxs-lookup"><span data-stu-id="05459-133">The supported options are:</span></span>

* <span data-ttu-id="05459-134">*轴对齐多维数据集* - 与世界坐标系统的轴保持一致的矩形形状，如应用程序启动时确定。</span><span class="sxs-lookup"><span data-stu-id="05459-134">*Axis Aligned Cube* - Rectangular shape that stays aligned with the axes of the world coordinate system, as determined at application startup.</span></span>
* <span data-ttu-id="05459-135">*用户对齐的多维数据集* - 旋转以与用户本地坐标系对齐的矩形形状。</span><span class="sxs-lookup"><span data-stu-id="05459-135">*User Aligned Cube* - Rectangular shape that rotates to align with the users local coordinate system.</span></span>
* <span data-ttu-id="05459-136">*球体* - 球状体，其中心位于世界空间原点。</span><span class="sxs-lookup"><span data-stu-id="05459-136">*Sphere* - A spherical volume with a center at the world space origin.</span></span> <span data-ttu-id="05459-137">"观察区 *"* 属性的 X 值将用作球体的半径。</span><span class="sxs-lookup"><span data-stu-id="05459-137">The X value of the *Observation Extents* property will be used as the radius of the sphere.</span></span>

<span data-ttu-id="05459-138">**观察区**</span><span class="sxs-lookup"><span data-stu-id="05459-138">**Observation Extents**</span></span>

<span data-ttu-id="05459-139">观察区定义将观测网格的观察点的距离。</span><span class="sxs-lookup"><span data-stu-id="05459-139">The observation extents define the distance from the observation point that meshes will be observed.</span></span>

### <a name="physics-settings"></a><span data-ttu-id="05459-140">物理设置</span><span class="sxs-lookup"><span data-stu-id="05459-140">Physics settings</span></span>

![网格观察器物理设置](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

<span data-ttu-id="05459-142">**物理层**</span><span class="sxs-lookup"><span data-stu-id="05459-142">**Physics Layer**</span></span>

<span data-ttu-id="05459-143">要与 Unity 物理和 RayCast 系统交互而放置空间网格对象的物理层。</span><span class="sxs-lookup"><span data-stu-id="05459-143">The physics layer on which spatial mesh objects will be placed in order to interact with the Unity Physics and RayCast systems.</span></span>

> [!NOTE]
> <span data-ttu-id="05459-144">混合现实Toolkit默认保留 *第 31* 层供空间感知观察者使用。</span><span class="sxs-lookup"><span data-stu-id="05459-144">The Mixed Reality Toolkit reserves *layer 31* by default for use by Spatial Awareness observers.</span></span>

<span data-ttu-id="05459-145">**重新计算法线**</span><span class="sxs-lookup"><span data-stu-id="05459-145">**Recalculate Normals**</span></span>

<span data-ttu-id="05459-146">指定网格观察器是否会在观察后重新计算网格的法线。</span><span class="sxs-lookup"><span data-stu-id="05459-146">Specifies whether or not the mesh observer will recalculate the normals of the mesh following observation.</span></span> <span data-ttu-id="05459-147">此设置可用于确保应用程序在未通过网格返回这些网格的平台上接收包含有效法线数据的网格。</span><span class="sxs-lookup"><span data-stu-id="05459-147">This setting is available to ensure applications receive meshes that contain valid normals data on platforms that do not return them with meshes.</span></span>

### <a name="level-of-detail-settings"></a><span data-ttu-id="05459-148">详细信息设置级别</span><span class="sxs-lookup"><span data-stu-id="05459-148">Level of detail settings</span></span>

![网格观察器详细级别设置](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

<span data-ttu-id="05459-150">**详细信息级别**</span><span class="sxs-lookup"><span data-stu-id="05459-150">**Level of Detail**</span></span>

<span data-ttu-id="05459-151">指定空间网格 (LOD) 的详细级别。</span><span class="sxs-lookup"><span data-stu-id="05459-151">Specifies the level of detail (LOD) of the spatial mesh data.</span></span> <span data-ttu-id="05459-152">当前定义的值为"粗略"、"精细"和"自定义"。</span><span class="sxs-lookup"><span data-stu-id="05459-152">Currently defined values are Coarse, Fine and Custom.</span></span>

* <span data-ttu-id="05459-153">*粗略* - 对应用程序性能的影响较小，是导航/平面查找的极佳选择。</span><span class="sxs-lookup"><span data-stu-id="05459-153">*Coarse* - Places a smaller impact on application performance and is an excellent choice for navigation/plane finding.</span></span>

* <span data-ttu-id="05459-154">*中等* - 均衡设置通常适用于持续扫描环境以寻找大型特征、楼层和墙面以及遮挡细节的体验。</span><span class="sxs-lookup"><span data-stu-id="05459-154">*Medium* - Balanced setting often useful for experiences that continually scan the environment for both large features, floors and walls, as well as occlusion details.</span></span>

* <span data-ttu-id="05459-155">*精细* - 通常对应用程序性能的影响更大，是遮挡网格的一个很好的选择。</span><span class="sxs-lookup"><span data-stu-id="05459-155">*Fine* - Generally exacts a higher impact on application performance and is a great option for occlusion meshes.</span></span>

* <span data-ttu-id="05459-156">*自定义* - 要求应用程序指定 *"三角形/* 三角形"属性，并允许应用程序优化空间网格观察程序的准确性和性能影响。</span><span class="sxs-lookup"><span data-stu-id="05459-156">*Custom* - Requires the application to specify the *Triangles / Cubic Meter* property and allows applications to tune the accuracy vs. performance impact of the spatial mesh observer.</span></span>

> [!NOTE]
> <span data-ttu-id="05459-157">不保证所有平台都遵守所有 *三角形/* 三角形计量值。</span><span class="sxs-lookup"><span data-stu-id="05459-157">It is not guaranteed that all *Triangles/Cubic Meter* values are honored by all platforms.</span></span> <span data-ttu-id="05459-158">使用自定义 LOD 时，强烈建议进行试验和分析。</span><span class="sxs-lookup"><span data-stu-id="05459-158">Experimentation and profiling is highly recommended when using a custom LOD.</span></span>

<span data-ttu-id="05459-159">**每个三角形（每三米）**</span><span class="sxs-lookup"><span data-stu-id="05459-159">**Triangles per Cubic Meter**</span></span>

<span data-ttu-id="05459-160">对"详细信息 *级别"* 属性使用"自定义"设置 **时** 有效，并指定空间网格的三角形密度。</span><span class="sxs-lookup"><span data-stu-id="05459-160">Valid when using the *Custom* setting for the **Level of Detail** property and specifies the triangle density for the spatial mesh.</span></span>

### <a name="display-settings"></a><span data-ttu-id="05459-161">显示设置</span><span class="sxs-lookup"><span data-stu-id="05459-161">Display settings</span></span>

![网格观察器显示设置](../images/spatial-awareness/MeshObserverDisplaySettings.png)

<span data-ttu-id="05459-163">**显示选项**</span><span class="sxs-lookup"><span data-stu-id="05459-163">**Display Option**</span></span>

<span data-ttu-id="05459-164">指定观察器如何显示空间网格。</span><span class="sxs-lookup"><span data-stu-id="05459-164">Specifies how spatial meshes are to be displayed by the observer.</span></span> <span data-ttu-id="05459-165">支持的值是：</span><span class="sxs-lookup"><span data-stu-id="05459-165">Supported values are:</span></span>

* <span data-ttu-id="05459-166">*无* - 观察者不会呈现网格</span><span class="sxs-lookup"><span data-stu-id="05459-166">*None* - Observer will not render the mesh</span></span>
* <span data-ttu-id="05459-167">*可见* - 网格数据将通过使用可见 *材料可见*</span><span class="sxs-lookup"><span data-stu-id="05459-167">*Visible* - Mesh data will be visible using the *Visible Material*</span></span>
* <span data-ttu-id="05459-168">*遮挡* - 网格数据将是场景中使用遮挡材料的 *遮挡项*</span><span class="sxs-lookup"><span data-stu-id="05459-168">*Occlusion* - Mesh data will be occlude items in scene using the *Occlusion Material*</span></span>

![选择空间感知系统实现](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

<span data-ttu-id="05459-170">可以通过代码在运行时 [恢复/挂起空间观察程序。](usage-guide.md#starting-and-stopping-mesh-observation)</span><span class="sxs-lookup"><span data-stu-id="05459-170">Spatial Observers can be [resumed/suspended at runtime via code.](usage-guide.md#starting-and-stopping-mesh-observation)</span></span>

> [!WARNING]
> <span data-ttu-id="05459-171">将 *"显示选项\*\*"设置为"无\*\*\*"不会阻止*\* 观察程序运行。</span><span class="sxs-lookup"><span data-stu-id="05459-171">Setting *Display Option* to *None* does **NOT** stop the observer from running.</span></span> <span data-ttu-id="05459-172">如果要停止所有观察程序，应用程序将需要通过 暂停所有观察程序 [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span><span class="sxs-lookup"><span data-stu-id="05459-172">If you wish to stop all observers, applications will need to suspend all observers via [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span></span>

<span data-ttu-id="05459-173">**可见材料**</span><span class="sxs-lookup"><span data-stu-id="05459-173">**Visible Material**</span></span>

<span data-ttu-id="05459-174">指示可视化空间网格时所使用的材料。</span><span class="sxs-lookup"><span data-stu-id="05459-174">Indicates the material to be used when visualizing the spatial mesh.</span></span>

<span data-ttu-id="05459-175">**遮挡材料**</span><span class="sxs-lookup"><span data-stu-id="05459-175">**Occlusion Material**</span></span>

<span data-ttu-id="05459-176">指示用于使空间网格遮挡全息影像的材料。</span><span class="sxs-lookup"><span data-stu-id="05459-176">Indicates the material to be used to cause the spatial mesh to occlude holograms.</span></span>

## <a name="see-also"></a><span data-ttu-id="05459-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05459-177">See also</span></span>

* [<span data-ttu-id="05459-178">空间感知系统</span><span class="sxs-lookup"><span data-stu-id="05459-178">Spatial Awareness System</span></span>](spatial-awareness-getting-started.md)
* [<span data-ttu-id="05459-179">通过代码配置空间感知系统</span><span class="sxs-lookup"><span data-stu-id="05459-179">Configuring Spatial Awareness system via Code</span></span>](usage-guide.md)
* [<span data-ttu-id="05459-180">IMixedRealitySpatialAwarenessObserver API 文档</span><span class="sxs-lookup"><span data-stu-id="05459-180">IMixedRealitySpatialAwarenessObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [<span data-ttu-id="05459-181">IMixedRealitySpatialAwarenessMeshObserver API 文档</span><span class="sxs-lookup"><span data-stu-id="05459-181">IMixedRealitySpatialAwarenessMeshObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [<span data-ttu-id="05459-182">BaseSpatialObserver API 文档</span><span class="sxs-lookup"><span data-stu-id="05459-182">BaseSpatialObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
