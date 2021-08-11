---
title: Unreal 中的凝视输入
description: 了解如何在 Unreal 中为应用设置并使用视线输入和眼动HoloLens方向。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality、全息影像、HoloLens 2、眼动跟踪、凝视输入、头部装入显示器、Unreal 引擎、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备
ms.openlocfilehash: e423086e293629e3dfadb49b52a376c0b93f5e465328b93f47c2f1e3e0790b63
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200662"
---
# <a name="gaze-input"></a>凝视输入

混合现实应用中的凝视输入与了解用户正在查看的内容有关。 当设备上眼动跟踪相机与 Unreal 世界空间中的射线匹配时，用户的视线数据将变为可用。 凝视可以在蓝图和 C++ 中使用，是对象交互、方法查找和相机控件等机制的核心功能。

## <a name="enabling-eye-tracking"></a>启用眼动跟踪

- 在 **Project 设置 > HoloLens** 中，启用 **凝视输入** 功能：

![项目设置HoloLens屏幕截图，其中突出显示了凝视输入](images/unreal-gaze-img-01.png)

- 创建新的执行组件并将其添加到场景中

> [!NOTE]
> HoloLens Unreal 中的眼动跟踪只有一条眼睛凝视射线。 不支持需要两条射线的立体声跟踪。

## <a name="using-eye-tracking"></a>使用眼动跟踪

首先，检查设备是否支持使用 **IsEyeTrackerConnected 函数进行眼** 动跟踪。  如果函数返回 true，请调用 **GetGazeData** 以查找用户眼睛在当前帧中正在查看的地方：

![Is Eye Tracking Connected 函数的蓝图](images/unreal-gaze-img-02.png)

> [!NOTE]
> 固定点和置信度值在 HoloLens。

在行跟踪中，使用凝视原点和方向来精确确定用户正在查找的内容。  凝视值为矢量，从凝视原点开始，在原点处结束，凝视方向乘以直线跟踪距离：

![获取凝视数据函数的蓝图](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>获取头部方向

还可使用 HMD (HMD) 头的旋转来表示用户头部的方向。 可以在不启用凝视输入功能的情况下获取用户头部方向，但无法获取任何眼动跟踪信息。  添加对蓝图的引用作为世界上下文，获取正确的输出数据：

> [!NOTE]
> 获取 HMD 数据仅在 Unreal 4.26 及之后提供。

![Get HMDData 函数的蓝图](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>使用 C++

- 在游戏的 **build.cs** 文件中，将 **EyeTracker** 添加到 **PublicDependencyModuleNames** 列表：

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "EyeTracker"
});
```

- 在 **"文件/新建 C++ 类"** 中，创建名为 **EyeTracker 的新** C++ 执行组件
    - 一Visual Studio解决方案将打开新的 EyeTracker 类。 生成并运行 ，以使用新的 EyeTracker 执行组件打开 Unreal 游戏。  在"放置执行组件"窗口中搜索"EyeTracker"，并将该类拖放到游戏窗口中以将其添加到项目： 

![角色的屏幕截图，其中位置执行组件窗口已打开](images/unreal-gaze-img-06.png)

- 在 **EyeTracker.cpp** 中，为 **EyeTrackerFunctionLibrary** 和 **DrawDebugHelpers 添加包含 ：**

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

在尝试获取任何凝视数据之前，请检查设备是否支持使用 **UEyeTrackerFunctionLibrary：：IsEyeTrackerConnected** 进行眼动跟踪。  如果支持眼动跟踪，请从 **UEyeTrackerFunctionLibrary：：GetGazeData** 查找线条跟踪的射线起点和终点。 可以在那里构造凝视向量，将其内容传递给 **LineTraceSingleByChannel** 以调试任何光线命中结果：

```cpp
void AEyeTracker::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    if(UEyeTrackerFunctionLibrary::IsEyeTrackerConnected())
    {
        FEyeTrackerGazeData GazeData;
        if(UEyeTrackerFunctionLibrary::GetGazeData(GazeData))
        {
            FVector Start = GazeData.GazeOrigin;
            FVector End = GazeData.GazeOrigin + GazeData.GazeDirection * 100;

            FHitResult Hit Result;
            if (GWorld->LineTraceSingleByChannel(HitResult, Start, End, ECollisionChannel::ECC_Visiblity))
            {
                DrawDebugCoordinateSystem(GWorld, HitResult.Location, FQuat::Identity.Rotator(), 10);
            }
        }
    }
}
```

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们规划的 Unreal 开发历程，则你处于探索 MRTK 核心基础知识的过程之中。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [手部跟踪](unreal-hand-tracking.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [HoloLens 摄像头](unreal-hololens-camera.md)

你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅
* [校准](/hololens/hololens-calibration)
* [舒适](../../design/comfort.md)
* [凝视和提交](../../design/gaze-and-commit.md)
* [语音输入](../../out-of-scope/voice-design.md)