---
title: 在 Unreal 中注视输入
description: 针对 HoloLens 和 Unreal 引擎设置注视输入的教程
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality，全息影像，HoloLens 2，眼睛跟踪，眼睛输入，head 装显示，Unreal 引擎，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: f89638cef6b90e004f097c701c3df13edaf74fac
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354310"
---
# <a name="gaze-input"></a>注视输入

注视用于指示用户正在查看的内容。  这会使用设备上的眼睛跟踪相机在 Unreal world 空间中查找与用户当前正在查看的内容相匹配的射线。

## <a name="enabling-eye-tracking"></a>启用目视跟踪

- 在 " **项目设置" > HoloLens** 中，启用 " **注视输入** " 功能：

![已突出显示 "注视" 输入的 HoloLens 项目设置功能的屏幕截图](images/unreal-gaze-img-01.png)

- 创建新的执行组件，并将其添加到场景

> [!NOTE] 
> Unreal 中的 HoloLens 眼睛跟踪只对这两种眼睛都有一个注视，而不是 stereoscopic 跟踪所需的两个射线，这不受支持。

## <a name="using-eye-tracking"></a>使用眼动跟踪

首先检查设备是否支持通过 IsEyeTrackerConnected 函数进行目视跟踪。  如果此返回 true，请调用 GetGazeData 以查找用户眼睛在当前帧中的外观：

![的蓝图为目视跟踪连接函数](images/unreal-gaze-img-02.png)

> [!NOTE]
> HoloLens 上不提供固定点和置信度值。

若要查找用户正在查看的内容，请在行轨迹中使用 "注视原点" 和 "方向"。  此向量的起始位置为 "注视原点"，终点为原点加上 "注视" 方向乘以所需距离：

![获取注视数据函数的蓝图](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>获取打印头方向

或者，可以使用 HMD 旋转来表示用户的头的方向。  这不需要注视输入功能，但不会为您显示任何眼睛跟踪信息。  必须将对蓝图的引用添加为世界上下文才能获得正确的输出数据：

> [!NOTE]
> 获取 HMD 数据仅在 Unreal 4.26 和更高版本中可用。

![Get HMDData 函数的蓝图](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>使用 C++ 

- 在游戏的 build.cs 文件中，将 "EyeTracker" 添加到 PublicDependencyModuleNames 列表：

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

- 在 "文件/新 c + + 类" 中，创建一个名为 "EyeTracker" 的新 c + + 参与者
    - Visual Studio 解决方案将打开新的 EyeTracker 类。 生成并运行，以通过新的 EyeTracker 参与者打开 Unreal 游戏。  在 "放置参与者" 窗口中搜索 "EyeTracker"。  将此类拖放到游戏窗口，将其添加到项目中：

![参与者窗口打开的参与者的屏幕截图](images/unreal-gaze-img-06.png)

- 在 EyeTracker 中，添加 EyeTrackerFunctionLibrary 和 DrawDebugHelpers 的包含：

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

在勾选标记中，检查设备是否支持通过 UEyeTrackerFunctionLibrary：： IsEyeTrackerConnected 进行目视跟踪。  然后从 UEyeTrackerFunctionLibrary：： GetGazeData 中查找线条轨迹的射线的起点和终点：

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

如果你遵循我们规划的 Unreal 开发检查点历程，则你处于探索 MRTK 核心构建基块的过程之中。 从这里，你可以进入下一个构建基块： 

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
