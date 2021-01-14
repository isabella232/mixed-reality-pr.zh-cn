---
title: Unreal 中的空间映射
description: 了解如何在适合 HoloLens 设备的 Unreal 混合现实应用程序中使用空间映射和网格。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, 空间映射, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: 3f07acc5bb4ad85084f6eb178fd1c33d94224408
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009957"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="59610-104">Unreal 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="59610-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="59610-105">利用空间映射，你可以将对象放置在现实世界的物理表面上。</span><span class="sxs-lookup"><span data-stu-id="59610-105">Spatial mapping lets you place objects on physical surfaces in the real-world.</span></span> <span data-ttu-id="59610-106">对 HoloLens 周围的世界进行映射时，全息影像看起来会让用户感觉更加真实。</span><span class="sxs-lookup"><span data-stu-id="59610-106">When the world around the HoloLens is mapped, holograms seem more real to the user.</span></span> <span data-ttu-id="59610-107">空间映射还利用深度提示，在用户的世界中为对象定位，这有助于说服用户这些全息影像实际位于其空间中。</span><span class="sxs-lookup"><span data-stu-id="59610-107">Spatial mapping also anchors objects in the user's world by taking advantage of depth cues, helping convince them that these holograms are actually in their space.</span></span> <span data-ttu-id="59610-108">在空间中浮动或随用户移动的全息影像并不会让人感觉真实，因此建议尽可能始终放置一些项目，让人保持舒适感。</span><span class="sxs-lookup"><span data-stu-id="59610-108">Holograms floating in space or moving with the user won't feel as real, so you always want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="59610-109">可以在[空间映射](../../design/spatial-mapping.md)文档中找到有关空间映射质量、位置、封闭、呈现等内容的详细信息。</span><span class="sxs-lookup"><span data-stu-id="59610-109">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](../../design/spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="59610-110">启用空间映射</span><span class="sxs-lookup"><span data-stu-id="59610-110">Enabling Spatial Mapping</span></span>

<span data-ttu-id="59610-111">若要在 HoloLens 上启用空间映射，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="59610-111">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="59610-112">打开“编辑”>“项目设置”，并向下滚动到“平台”部分。</span><span class="sxs-lookup"><span data-stu-id="59610-112">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="59610-113">选择“HoloLens”并检查“空间感知”。</span><span class="sxs-lookup"><span data-stu-id="59610-113">Select **HoloLens** and check **Spatial Perception**.</span></span>

![HoloLens 项目设置功能的屏幕截图，其中突出显示了空间感知](images/unreal-spatial-mapping-img-01.png)

<span data-ttu-id="59610-115">若要选择在 HoloLens 游戏中使用空间映射并调试“MRMesh”，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="59610-115">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="59610-116">打开“ARSessionConfig”并展开“ARSettings”>“世界映射”部分。</span><span class="sxs-lookup"><span data-stu-id="59610-116">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="59610-117">选中“从跟踪几何生成网格数据”，可指示 HoloLens 插件开始异步获取空间映射数据，并通过 MRMesh 将其呈现给 Unreal。</span><span class="sxs-lookup"><span data-stu-id="59610-117">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="59610-118">选中“在线框中呈现网格数据”，以显示 MRMesh 中每个三角形的白色线框轮廓。</span><span class="sxs-lookup"><span data-stu-id="59610-118">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![空间定位点存储准备就绪](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="59610-120">运行时的空间映射</span><span class="sxs-lookup"><span data-stu-id="59610-120">Spatial Mapping at runtime</span></span>
<span data-ttu-id="59610-121">可以修改以下参数以更新空间映射运行时行为：</span><span class="sxs-lookup"><span data-stu-id="59610-121">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="59610-122">打开“编辑”>“项目设置”，向下滚动到“平台”部分，并选择“HoloLens”>“空间映射”  ：</span><span class="sxs-lookup"><span data-stu-id="59610-122">Open **Edit > Project Settings**, scroll down to the **Platforms** section, and select **HoloLens > Spatial Mapping**:</span></span> 

![空间定位点项目设置](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="59610-124">“每立方米最大三角形”将更新空间映射网格中三角形的密度。</span><span class="sxs-lookup"><span data-stu-id="59610-124">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="59610-125">“空间网格体积大小”是在玩家周围渲染和更新空间映射数据的立方体的大小。</span><span class="sxs-lookup"><span data-stu-id="59610-125">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="59610-126">如果预期的应用程序运行时环境很大，那么这个值可能需要很大才能匹配实际空间。</span><span class="sxs-lookup"><span data-stu-id="59610-126">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span> <span data-ttu-id="59610-127">如果应用程序只需要将全息影像直接放置在用户周围的表面上，那么这个值可能会较小。</span><span class="sxs-lookup"><span data-stu-id="59610-127">The value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="59610-128">当用户在世界内走动时，空间映射卷将随之移动。</span><span class="sxs-lookup"><span data-stu-id="59610-128">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="59610-129">使用 MRMesh</span><span class="sxs-lookup"><span data-stu-id="59610-129">Working with MRMesh</span></span>

<span data-ttu-id="59610-130">首先，你需要启动“空间映射”：</span><span class="sxs-lookup"><span data-stu-id="59610-130">First, you need to start Spatial Mapping:</span></span>

![ToggleARCapture 函数的蓝图，其中突出显示了空间映射捕获类型](images/unreal-spatial-mapping-img-02.png)

<span data-ttu-id="59610-132">为空间捕获空间映射后，建议关闭空间映射。</span><span class="sxs-lookup"><span data-stu-id="59610-132">Once spatial mapping has been captured for the space, we recommend toggling off spatial mapping.</span></span>  <span data-ttu-id="59610-133">可在一定时间后完成空间映射，也可当各方向的光线投射均对 MRMesh 返回碰撞时完成。</span><span class="sxs-lookup"><span data-stu-id="59610-133">The spatial mapping may be completed either after a certain amount of time, or when raycasts in each direction return collisions against the MRMesh.</span></span>

<span data-ttu-id="59610-134">若要在运行时访问 MRMesh，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="59610-134">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="59610-135">将“ARTrackableNotify”组件添加到蓝图 Actor。</span><span class="sxs-lookup"><span data-stu-id="59610-135">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![空间定位点 AR 可跟踪通知](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="59610-137">选择“ARTrackableNotify”组件，然后在“详细信息”面板中展开“事件”部分  。</span><span class="sxs-lookup"><span data-stu-id="59610-137">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="59610-138">在要监视的事件上，选择 + 按钮。</span><span class="sxs-lookup"><span data-stu-id="59610-138">Select the **+** button on the events you want to monitor.</span></span> 

![空间定位点事件](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="59610-140">在这种情况下，会监视“添加时跟踪几何”事件，这将查找与空间映射数据匹配的有效世界网格。</span><span class="sxs-lookup"><span data-stu-id="59610-140">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="59610-141">可以在 [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 组件 API 中找到事件的完整列表。</span><span class="sxs-lookup"><span data-stu-id="59610-141">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="59610-142">可以在蓝图事件图或 C++ 中更改网格的材料。</span><span class="sxs-lookup"><span data-stu-id="59610-142">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="59610-143">下面的屏幕截图显示蓝图路由：</span><span class="sxs-lookup"><span data-stu-id="59610-143">The screenshot below shows the Blueprint route:</span></span> 

![空间定位点示例](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a><span data-ttu-id="59610-145">使用 C++ 的空间映射</span><span class="sxs-lookup"><span data-stu-id="59610-145">Spatial Mapping in C++</span></span>

<span data-ttu-id="59610-146">在游戏的 build.cs 文件中，向 PublicDependencyModuleNames 列表添加 AugmentedReality 和 MRMesh ：</span><span class="sxs-lookup"><span data-stu-id="59610-146">In your game's build.cs file, add **AugmentedReality** and **MRMesh** to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",    
        "EyeTracker",
        "AugmentedReality",
        "MRMesh"
});
```

<span data-ttu-id="59610-147">若要访问 MRMesh，请订阅 OnTrackableAdded 委托：</span><span class="sxs-lookup"><span data-stu-id="59610-147">To access the MRMesh, subscribe to the **OnTrackableAdded** delegates:</span></span>

```cpp
#include "ARBlueprintLibrary.h"
#include "MRMeshComponent.h"

void AARTrackableMonitor::BeginPlay()
{
    Super::BeginPlay();

    // Subscribe to Tracked Geometry delegates
    UARBlueprintLibrary::AddOnTrackableAddedDelegate_Handle(
        FOnTrackableAddedDelegate::CreateUObject(this, &AARTrackableMonitor::OnTrackableAdded)
    );
}

void AARTrackableMonitor::OnTrackableAdded(UARTrackedGeometry* Added)
{
    // When tracked geometry is received, check that it's from spatial mapping
    if(Added->GetObjectClassification() == EARObjectClassification::World)
    {
        UMRMeshComponent* MRMesh = Added->GetUnderlyingMesh();
    }
}
```

> [!NOTE]
> <span data-ttu-id="59610-148">对于已更新和已删除的事件，存在类似的委托，分别为 AddOnTrackableUpdatedDelegate_Handle 和 AddOnTrackableRemovedDelegate_Handle 。</span><span class="sxs-lookup"><span data-stu-id="59610-148">There are similar delegates for updated and removed events, **AddOnTrackableUpdatedDelegate_Handle** and **AddOnTrackableRemovedDelegate_Handle** respectively.</span></span>
>
> <span data-ttu-id="59610-149">可以在 [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API 中找到事件的完整列表。</span><span class="sxs-lookup"><span data-stu-id="59610-149">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="59610-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="59610-150">See also</span></span>
* [<span data-ttu-id="59610-151">空间映射</span><span class="sxs-lookup"><span data-stu-id="59610-151">Spatial mapping</span></span>](../../design/spatial-mapping.md)
