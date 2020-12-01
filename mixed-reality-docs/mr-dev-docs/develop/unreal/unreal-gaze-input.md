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
# <a name="gaze-input"></a><span data-ttu-id="79acc-104">注视输入</span><span class="sxs-lookup"><span data-stu-id="79acc-104">Gaze Input</span></span>

<span data-ttu-id="79acc-105">注视用于指示用户正在查看的内容。</span><span class="sxs-lookup"><span data-stu-id="79acc-105">Gaze is used to indicate what the user is looking at.</span></span>  <span data-ttu-id="79acc-106">这会使用设备上的眼睛跟踪相机在 Unreal world 空间中查找与用户当前正在查看的内容相匹配的射线。</span><span class="sxs-lookup"><span data-stu-id="79acc-106">This uses the eye tracking cameras on the device to find a ray in Unreal world space matching what the user is currently looking at.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="79acc-107">启用目视跟踪</span><span class="sxs-lookup"><span data-stu-id="79acc-107">Enabling eye tracking</span></span>

- <span data-ttu-id="79acc-108">在 " **项目设置" > HoloLens** 中，启用 " **注视输入** " 功能：</span><span class="sxs-lookup"><span data-stu-id="79acc-108">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![已突出显示 "注视" 输入的 HoloLens 项目设置功能的屏幕截图](images/unreal-gaze-img-01.png)

- <span data-ttu-id="79acc-110">创建新的执行组件，并将其添加到场景</span><span class="sxs-lookup"><span data-stu-id="79acc-110">Create a new actor and add it to your scene</span></span>

> [!NOTE] 
> <span data-ttu-id="79acc-111">Unreal 中的 HoloLens 眼睛跟踪只对这两种眼睛都有一个注视，而不是 stereoscopic 跟踪所需的两个射线，这不受支持。</span><span class="sxs-lookup"><span data-stu-id="79acc-111">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="79acc-112">使用眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="79acc-112">Using eye tracking</span></span>

<span data-ttu-id="79acc-113">首先检查设备是否支持通过 IsEyeTrackerConnected 函数进行目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="79acc-113">First check that the device supports eye tracking with the IsEyeTrackerConnected function.</span></span>  <span data-ttu-id="79acc-114">如果此返回 true，请调用 GetGazeData 以查找用户眼睛在当前帧中的外观：</span><span class="sxs-lookup"><span data-stu-id="79acc-114">If this returns true, call GetGazeData to find where the user’s eyes are looking at during the current frame:</span></span>

![的蓝图为目视跟踪连接函数](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="79acc-116">HoloLens 上不提供固定点和置信度值。</span><span class="sxs-lookup"><span data-stu-id="79acc-116">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="79acc-117">若要查找用户正在查看的内容，请在行轨迹中使用 "注视原点" 和 "方向"。</span><span class="sxs-lookup"><span data-stu-id="79acc-117">To find what the user is looking at, use the gaze origin and direction in a line trace.</span></span>  <span data-ttu-id="79acc-118">此向量的起始位置为 "注视原点"，终点为原点加上 "注视" 方向乘以所需距离：</span><span class="sxs-lookup"><span data-stu-id="79acc-118">The start of this vector is the gaze origin and the end is the origin plus the gaze direction multiplied by the desired distance:</span></span>

![获取注视数据函数的蓝图](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="79acc-120">获取打印头方向</span><span class="sxs-lookup"><span data-stu-id="79acc-120">Getting head orientation</span></span>

<span data-ttu-id="79acc-121">或者，可以使用 HMD 旋转来表示用户的头的方向。</span><span class="sxs-lookup"><span data-stu-id="79acc-121">Alternatively, the HMD rotation can be used to represent the direction of the user’s head.</span></span>  <span data-ttu-id="79acc-122">这不需要注视输入功能，但不会为您显示任何眼睛跟踪信息。</span><span class="sxs-lookup"><span data-stu-id="79acc-122">This does not require the Gaze Input capability but won't give you any eye tracking information.</span></span>  <span data-ttu-id="79acc-123">必须将对蓝图的引用添加为世界上下文才能获得正确的输出数据：</span><span class="sxs-lookup"><span data-stu-id="79acc-123">A reference to the blueprint must be added as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="79acc-124">获取 HMD 数据仅在 Unreal 4.26 和更高版本中可用。</span><span class="sxs-lookup"><span data-stu-id="79acc-124">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Get HMDData 函数的蓝图](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="79acc-126">使用 C++</span><span class="sxs-lookup"><span data-stu-id="79acc-126">Using C++</span></span> 

- <span data-ttu-id="79acc-127">在游戏的 build.cs 文件中，将 "EyeTracker" 添加到 PublicDependencyModuleNames 列表：</span><span class="sxs-lookup"><span data-stu-id="79acc-127">In your game’s build.cs file, add “EyeTracker” to the PublicDependencyModuleNames list:</span></span>

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

- <span data-ttu-id="79acc-128">在 "文件/新 c + + 类" 中，创建一个名为 "EyeTracker" 的新 c + + 参与者</span><span class="sxs-lookup"><span data-stu-id="79acc-128">In “File/ New C++ Class”, Create a new C++ actor called “EyeTracker”</span></span>
    - <span data-ttu-id="79acc-129">Visual Studio 解决方案将打开新的 EyeTracker 类。</span><span class="sxs-lookup"><span data-stu-id="79acc-129">A Visual Studio solution will open to the new EyeTracker class.</span></span> <span data-ttu-id="79acc-130">生成并运行，以通过新的 EyeTracker 参与者打开 Unreal 游戏。</span><span class="sxs-lookup"><span data-stu-id="79acc-130">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="79acc-131">在 "放置参与者" 窗口中搜索 "EyeTracker"。</span><span class="sxs-lookup"><span data-stu-id="79acc-131">Search for “EyeTracker” in the “Place Actors” window.</span></span>  <span data-ttu-id="79acc-132">将此类拖放到游戏窗口，将其添加到项目中：</span><span class="sxs-lookup"><span data-stu-id="79acc-132">Drag and drop this class into the game window to add it to the project:</span></span>

![参与者窗口打开的参与者的屏幕截图](images/unreal-gaze-img-06.png)

- <span data-ttu-id="79acc-134">在 EyeTracker 中，添加 EyeTrackerFunctionLibrary 和 DrawDebugHelpers 的包含：</span><span class="sxs-lookup"><span data-stu-id="79acc-134">In EyeTracker.cpp, add includes for EyeTrackerFunctionLibrary, and DrawDebugHelpers:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="79acc-135">在勾选标记中，检查设备是否支持通过 UEyeTrackerFunctionLibrary：： IsEyeTrackerConnected 进行目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="79acc-135">In Tick, check that the device supports eye tracking with UEyeTrackerFunctionLibrary::IsEyeTrackerConnected.</span></span>  <span data-ttu-id="79acc-136">然后从 UEyeTrackerFunctionLibrary：： GetGazeData 中查找线条轨迹的射线的起点和终点：</span><span class="sxs-lookup"><span data-stu-id="79acc-136">Then find the start and end of a ray for a line trace from UEyeTrackerFunctionLibrary::GetGazeData:</span></span>

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

## <a name="next-development-checkpoint"></a><span data-ttu-id="79acc-137">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="79acc-137">Next Development Checkpoint</span></span>

<span data-ttu-id="79acc-138">如果你遵循我们规划的 Unreal 开发检查点历程，则你处于探索 MRTK 核心构建基块的过程之中。</span><span class="sxs-lookup"><span data-stu-id="79acc-138">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="79acc-139">从这里，你可以进入下一个构建基块：</span><span class="sxs-lookup"><span data-stu-id="79acc-139">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="79acc-140">手部跟踪</span><span class="sxs-lookup"><span data-stu-id="79acc-140">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="79acc-141">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="79acc-141">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="79acc-142">HoloLens 摄像头</span><span class="sxs-lookup"><span data-stu-id="79acc-142">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="79acc-143">你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="79acc-143">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="79acc-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="79acc-144">See also</span></span>
* [<span data-ttu-id="79acc-145">校准</span><span class="sxs-lookup"><span data-stu-id="79acc-145">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="79acc-146">舒适</span><span class="sxs-lookup"><span data-stu-id="79acc-146">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="79acc-147">凝视和提交</span><span class="sxs-lookup"><span data-stu-id="79acc-147">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="79acc-148">语音输入</span><span class="sxs-lookup"><span data-stu-id="79acc-148">Voice input</span></span>](../../out-of-scope/voice-design.md)
