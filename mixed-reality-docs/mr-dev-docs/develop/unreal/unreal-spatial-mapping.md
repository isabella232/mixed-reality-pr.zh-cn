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
# <a name="spatial-mapping-in-unreal"></a>Unreal 中的空间映射

利用空间映射，你可以将对象放置在现实世界的物理表面上。 对 HoloLens 周围的世界进行映射时，全息影像看起来会让用户感觉更加真实。 空间映射还利用深度提示，在用户的世界中为对象定位，这有助于说服用户这些全息影像实际位于其空间中。 在空间中浮动或随用户移动的全息影像并不会让人感觉真实，因此建议尽可能始终放置一些项目，让人保持舒适感。

可以在[空间映射](../../design/spatial-mapping.md)文档中找到有关空间映射质量、位置、封闭、呈现等内容的详细信息。

## <a name="enabling-spatial-mapping"></a>启用空间映射

若要在 HoloLens 上启用空间映射，请执行以下操作：
- 打开“编辑”>“项目设置”，并向下滚动到“平台”部分。    
    + 选择“HoloLens”并检查“空间感知”。

![HoloLens 项目设置功能的屏幕截图，其中突出显示了空间感知](images/unreal-spatial-mapping-img-01.png)

若要选择在 HoloLens 游戏中使用空间映射并调试“MRMesh”，请执行以下操作：
1. 打开“ARSessionConfig”并展开“ARSettings”>“世界映射”部分。 

2. 选中“从跟踪几何生成网格数据”，可指示 HoloLens 插件开始异步获取空间映射数据，并通过 MRMesh 将其呈现给 Unreal。 
3. 选中“在线框中呈现网格数据”，以显示 MRMesh 中每个三角形的白色线框轮廓。 

![空间定位点存储准备就绪](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a>运行时的空间映射
可以修改以下参数以更新空间映射运行时行为：

- 打开“编辑”>“项目设置”，向下滚动到“平台”部分，并选择“HoloLens”>“空间映射”  ： 

![空间定位点项目设置](images/unreal-spatialmapping-projectsettings.PNG)

- “每立方米最大三角形”将更新空间映射网格中三角形的密度。  
- “空间网格体积大小”是在玩家周围渲染和更新空间映射数据的立方体的大小。  
    + 如果预期的应用程序运行时环境很大，那么这个值可能需要很大才能匹配实际空间。 如果应用程序只需要将全息影像直接放置在用户周围的表面上，那么这个值可能会较小。 当用户在世界内走动时，空间映射卷将随之移动。 

## <a name="working-with-mrmesh"></a>使用 MRMesh

首先，你需要启动“空间映射”：

![ToggleARCapture 函数的蓝图，其中突出显示了空间映射捕获类型](images/unreal-spatial-mapping-img-02.png)

为空间捕获空间映射后，建议关闭空间映射。  可在一定时间后完成空间映射，也可当各方向的光线投射均对 MRMesh 返回碰撞时完成。

若要在运行时访问 MRMesh，请执行以下操作：
1. 将“ARTrackableNotify”组件添加到蓝图 Actor。 

![空间定位点 AR 可跟踪通知](images/unreal-spatialmapping-artrackablenotify.PNG)

2. 选择“ARTrackableNotify”组件，然后在“详细信息”面板中展开“事件”部分  。 
    - 在要监视的事件上，选择 + 按钮。 

![空间定位点事件](images/unreal-spatialmapping-events.PNG)

在这种情况下，会监视“添加时跟踪几何”事件，这将查找与空间映射数据匹配的有效世界网格。 可以在 [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 组件 API 中找到事件的完整列表。 

可以在蓝图事件图或 C++ 中更改网格的材料。 下面的屏幕截图显示蓝图路由： 

![空间定位点示例](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a>使用 C++ 的空间映射

在游戏的 build.cs 文件中，向 PublicDependencyModuleNames 列表添加 AugmentedReality 和 MRMesh ：

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

若要访问 MRMesh，请订阅 OnTrackableAdded 委托：

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
> 对于已更新和已删除的事件，存在类似的委托，分别为 AddOnTrackableUpdatedDelegate_Handle 和 AddOnTrackableRemovedDelegate_Handle 。
>
> 可以在 [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API 中找到事件的完整列表。

## <a name="see-also"></a>另请参阅
* [空间映射](../../design/spatial-mapping.md)
