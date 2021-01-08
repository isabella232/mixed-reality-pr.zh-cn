---
title: 在 Unreal 中注视输入
description: 了解如何在 Unreal 中设置和使用适用于 HoloLens 的目视跟踪和打印头方向的目视输入。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality，全息影像，HoloLens 2，眼睛跟踪，眼睛输入，head 装显示，Unreal 引擎，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: e546867fe02acd5e72ee76b4108a369ec25fd32f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010137"
---
# <a name="gaze-input"></a>注视输入

Mixed reality 应用中的 "注视输入" 就是找出用户正在寻找的内容。 当设备上的眼睛跟踪相机与 Unreal 世界空间中的光线匹配时，用户的视觉数据将变为可用。 看起来可以在蓝图和 c + + 中使用，它是对象交互、查找和照相机控件等机制的核心功能。

## <a name="enabling-eye-tracking"></a>启用目视跟踪

- 在 " **项目设置" > HoloLens** 中，启用 " **注视输入** " 功能：

![已突出显示 "注视" 输入的 HoloLens 项目设置功能的屏幕截图](images/unreal-gaze-img-01.png)

- 创建新的执行组件，并将其添加到场景

> [!NOTE]
> Unreal 中的 HoloLens 眼睛跟踪仅有两个眼睛的一眼。 不支持 Stereoscopic 跟踪，这需要两个射线。

## <a name="using-eye-tracking"></a>使用眼动跟踪

首先，检查设备是否支持通过 **IsEyeTrackerConnected** 函数进行目视跟踪。  如果该函数返回 true，则调用 **GetGazeData** 以查找用户眼睛在当前帧中的位置：

![的蓝图为目视跟踪连接函数](images/unreal-gaze-img-02.png)

> [!NOTE]
> HoloLens 上不提供固定点和置信度值。

在线条轨迹中使用 "注视原点" 和 "方向" 来找出用户正在寻找的内容。  "注视" 值为向量，从注视原点开始，沿原点结束，并沿线条轨迹的距离结束：

![获取注视数据函数的蓝图](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>获取打印头方向

你还可以使用 Head 已装入显示 (HMD) 的旋转来表示用户的头的方向。 你可以在不启用 "注视输入" 功能的情况下获取用户头，但不会获得任何目视跟踪信息。  添加对蓝图的引用作为世界上下文，以获取正确的输出数据：

> [!NOTE]
> 获取 HMD 数据仅在 Unreal 4.26 和更高版本中可用。

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

- 在 "**文件/新 c + + 类**" 中，创建名为 **EyeTracker** 的新 c + + 参与者
    - Visual Studio 解决方案将打开新的 EyeTracker 类。 生成并运行，以通过新的 EyeTracker 参与者打开 Unreal 游戏。  在 " **放置参与者** " 窗口中搜索 "EyeTracker"，并将类拖放到游戏窗口，以将其添加到项目中：

![参与者窗口打开的参与者的屏幕截图](images/unreal-gaze-img-06.png)

- 在 **EyeTracker** 中，添加 **EyeTrackerFunctionLibrary** 和 **DrawDebugHelpers** 的包含：

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

尝试获取任何目视的数据之前，请检查你的设备是否支持 **UEyeTrackerFunctionLibrary：： IsEyeTrackerConnected** 的目视跟踪。  如果支持目视跟踪，请从 **UEyeTrackerFunctionLibrary：： GetGazeData** 中查找线条跟踪的射线的起点和终点。 在该处，可以构造一个注视向量，并将其内容传递到 **LineTraceSingleByChannel** 以调试任何射线命中结果：

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
* [校准](../../calibration.md)
* [舒适](../../design/comfort.md)
* [凝视和提交](../../design/gaze-and-commit.md)
* [语音输入](../../out-of-scope/voice-design.md)
