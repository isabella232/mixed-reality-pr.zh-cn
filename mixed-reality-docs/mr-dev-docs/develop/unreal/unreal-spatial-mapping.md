---
title: Unreal 中的空间映射
description: Unreal 中空间映射使用指南
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, 空间映射, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: 878eae5f5fd0b7a1630511faa23c1477455ed988
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354367"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="58e78-104">Unreal 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="58e78-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="58e78-105">使用空间映射可以通过向全球展示 HoloLens 来将对象放置在现实生活中的表面上，这使全息影像看起来更真实。</span><span class="sxs-lookup"><span data-stu-id="58e78-105">Spatial mapping makes it possible to place objects on surfaces in the physical world by showing the world around the HoloLens, which makes holograms seem more real to the user.</span></span> <span data-ttu-id="58e78-106">空间映射还可以利用真实的深度提示，在用户世界定位对象。这有助于说服用户这些全息影像实际位于其空间中；在空间中浮动或随用户移动的全息影像并不真实。</span><span class="sxs-lookup"><span data-stu-id="58e78-106">Spatial mapping also anchors objects in the user's world by taking advantage of real world depth cues. This helps convince the user that these holograms are actually in their space; holograms floating in space or moving with the user will not feel as real.</span></span> <span data-ttu-id="58e78-107">你希望尽可能轻松地放置各个项。</span><span class="sxs-lookup"><span data-stu-id="58e78-107">You want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="58e78-108">可以在[空间映射](../../design/spatial-mapping.md)文档中找到有关空间映射质量、位置、封闭、呈现等内容的详细信息。</span><span class="sxs-lookup"><span data-stu-id="58e78-108">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](../../design/spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="58e78-109">启用空间映射</span><span class="sxs-lookup"><span data-stu-id="58e78-109">Enabling Spatial Mapping</span></span>

<span data-ttu-id="58e78-110">若要在 HoloLens 上启用空间映射，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="58e78-110">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="58e78-111">打开“编辑”>“项目设置”，并向下滚动到“平台”部分。</span><span class="sxs-lookup"><span data-stu-id="58e78-111">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="58e78-112">选择“HoloLens”并检查“空间感知”。</span><span class="sxs-lookup"><span data-stu-id="58e78-112">Select **HoloLens** and check **Spatial Perception**.</span></span>

![HoloLens 项目设置功能的屏幕截图，其中突出显示了空间感知](images/unreal-spatial-mapping-img-01.png)

<span data-ttu-id="58e78-114">若要选择在 HoloLens 游戏中使用空间映射并调试“MRMesh”，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="58e78-114">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="58e78-115">打开“ARSessionConfig”并展开“ARSettings”>“世界映射”部分。</span><span class="sxs-lookup"><span data-stu-id="58e78-115">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="58e78-116">选中“从跟踪几何生成网格数据”，可指示 HoloLens 插件开始异步获取空间映射数据，并通过 MRMesh 将其呈现给 Unreal。</span><span class="sxs-lookup"><span data-stu-id="58e78-116">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="58e78-117">选中“在线框中呈现网格数据”，以显示 MRMesh 中每个三角形的白色线框轮廓。</span><span class="sxs-lookup"><span data-stu-id="58e78-117">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![空间定位点存储准备就绪](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="58e78-119">运行时的空间映射</span><span class="sxs-lookup"><span data-stu-id="58e78-119">Spatial Mapping at runtime</span></span>
<span data-ttu-id="58e78-120">可以修改以下参数以更新空间映射运行时行为：</span><span class="sxs-lookup"><span data-stu-id="58e78-120">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="58e78-121">打开“编辑”>“项目设置”，向下滚动到“平台”部分，并选择“HoloLens”>“空间映射”  ：</span><span class="sxs-lookup"><span data-stu-id="58e78-121">Open **Edit > Project Settings**, scroll down to the **Platforms** section and select **HoloLens > Spatial Mapping**:</span></span> 

![空间定位点项目设置](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="58e78-123">“每立方米最大三角形”将更新空间映射网格中三角形的密度。</span><span class="sxs-lookup"><span data-stu-id="58e78-123">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="58e78-124">“空间网格体积大小”是在玩家周围渲染和更新空间映射数据的立方体的大小。</span><span class="sxs-lookup"><span data-stu-id="58e78-124">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="58e78-125">如果预期的应用程序运行时环境很大，那么这个值可能需要很大才能匹配实际空间。</span><span class="sxs-lookup"><span data-stu-id="58e78-125">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span>  <span data-ttu-id="58e78-126">另一方面，如果应用程序只需要将全息影像直接放置在用户周围的表面上，那么这个值可能会较小。</span><span class="sxs-lookup"><span data-stu-id="58e78-126">On the other hand, this value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="58e78-127">当用户在世界内走动时，空间映射卷将随之移动。</span><span class="sxs-lookup"><span data-stu-id="58e78-127">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="58e78-128">使用 MRMesh</span><span class="sxs-lookup"><span data-stu-id="58e78-128">Working with MRMesh</span></span>

<span data-ttu-id="58e78-129">首先，你需要启动“空间映射”：</span><span class="sxs-lookup"><span data-stu-id="58e78-129">First, you need to start Spatial Mapping:</span></span>

![ToggleARCapture 函数的蓝图，其中突出显示了空间映射捕获类型](images/unreal-spatial-mapping-img-02.png)

<span data-ttu-id="58e78-131">为空间捕获空间映射后，建议关闭空间映射。</span><span class="sxs-lookup"><span data-stu-id="58e78-131">Once spatial mapping has been captured for the space, we recommend toggling spatial mapping off.</span></span>  <span data-ttu-id="58e78-132">可在一定时间后完成空间映射，也可当各方向的光线投射均对 MRMesh 返回碰撞时完成。</span><span class="sxs-lookup"><span data-stu-id="58e78-132">The spatial mapping may be completed either after a certain amount of time, or when raycasts in each direction return collisions against the MRMesh.</span></span>

<span data-ttu-id="58e78-133">若要在运行时访问 MRMesh，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="58e78-133">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="58e78-134">将“ARTrackableNotify”组件添加到蓝图 Actor。</span><span class="sxs-lookup"><span data-stu-id="58e78-134">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![空间定位点 AR 可跟踪通知](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="58e78-136">选择“ARTrackableNotify”组件，然后在“详细信息”面板中展开“事件”部分  。</span><span class="sxs-lookup"><span data-stu-id="58e78-136">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="58e78-137">在要监视的事件上，单击 + 按钮。</span><span class="sxs-lookup"><span data-stu-id="58e78-137">Click the **+** button on the events you want to monitor.</span></span> 

![空间定位点事件](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="58e78-139">在这种情况下，会监视“添加时跟踪几何”事件，这将查找与空间映射数据匹配的有效世界网格。</span><span class="sxs-lookup"><span data-stu-id="58e78-139">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="58e78-140">可以在 [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 组件 API 中找到事件的完整列表。</span><span class="sxs-lookup"><span data-stu-id="58e78-140">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="58e78-141">可以在蓝图事件图或 C++ 中更改网格的材料。</span><span class="sxs-lookup"><span data-stu-id="58e78-141">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="58e78-142">下面的屏幕截图显示蓝图路由：</span><span class="sxs-lookup"><span data-stu-id="58e78-142">The screenshot below shows the Blueprint route:</span></span> 

![空间定位点示例](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a><span data-ttu-id="58e78-144">使用 C++ 的空间映射</span><span class="sxs-lookup"><span data-stu-id="58e78-144">Spatial Mapping in C++</span></span>

<span data-ttu-id="58e78-145">在游戏的 build.cs 文件中，向 PublicDependencyModuleNames 列表添加 AugmentedReality 和 MRMesh ：</span><span class="sxs-lookup"><span data-stu-id="58e78-145">In your game's build.cs file, add **AugmentedReality** and **MRMesh** to the PublicDependencyModuleNames list:</span></span>

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

<span data-ttu-id="58e78-146">若要访问 MRMesh，请订阅 OnTrackableAdded 委托：</span><span class="sxs-lookup"><span data-stu-id="58e78-146">To access the MRMesh, subscribe to the **OnTrackableAdded** delegates:</span></span>

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
> <span data-ttu-id="58e78-147">对于已更新和已删除的事件，存在类似的委托，分别为 AddOnTrackableUpdatedDelegate_Handle 和 AddOnTrackableRemovedDelegate_Handle 。</span><span class="sxs-lookup"><span data-stu-id="58e78-147">There are similar delegates for updated and removed events, **AddOnTrackableUpdatedDelegate_Handle** and **AddOnTrackableRemovedDelegate_Handle** respectively.</span></span>
>
> <span data-ttu-id="58e78-148">可以在 [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API 中找到事件的完整列表。</span><span class="sxs-lookup"><span data-stu-id="58e78-148">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="58e78-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58e78-149">See also</span></span>
* [<span data-ttu-id="58e78-150">空间映射</span><span class="sxs-lookup"><span data-stu-id="58e78-150">Spatial mapping</span></span>](../../design/spatial-mapping.md)
