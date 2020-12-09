---
title: 在 Unreal 中注视输入
description: 针对 HoloLens 和 Unreal 引擎设置注视输入的教程
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality，全息影像，HoloLens 2，眼睛跟踪，眼睛输入，head 装显示，Unreal 引擎，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: a11573d732e739068dca8c42dd8688c0705fc5bb
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925990"
---
# <a name="gaze-input"></a><span data-ttu-id="9b79a-104">注视输入</span><span class="sxs-lookup"><span data-stu-id="9b79a-104">Gaze Input</span></span>

<span data-ttu-id="9b79a-105">Mixed reality 应用中的 "注视输入" 就是找出用户正在寻找的内容。</span><span class="sxs-lookup"><span data-stu-id="9b79a-105">Gaze input in mixed reality apps is all about finding out what your users are looking at.</span></span> <span data-ttu-id="9b79a-106">当设备上的眼睛跟踪相机与 Unreal 世界空间中的光线匹配时，用户的视觉数据将变为可用。</span><span class="sxs-lookup"><span data-stu-id="9b79a-106">When the eye tracking cameras on your device match up with rays in Unreal's world space, your user's line of sight data becomes available.</span></span> <span data-ttu-id="9b79a-107">看起来可以在蓝图和 c + + 中使用，它是对象交互、查找和照相机控件等机制的核心功能。</span><span class="sxs-lookup"><span data-stu-id="9b79a-107">Gaze can be used in both blueprints and C++, and is a core feature for mechanics like object interaction, way finding, and camera controls.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="9b79a-108">启用目视跟踪</span><span class="sxs-lookup"><span data-stu-id="9b79a-108">Enabling eye tracking</span></span>

- <span data-ttu-id="9b79a-109">在 " **项目设置" > HoloLens** 中，启用 " **注视输入** " 功能：</span><span class="sxs-lookup"><span data-stu-id="9b79a-109">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![已突出显示 "注视" 输入的 HoloLens 项目设置功能的屏幕截图](images/unreal-gaze-img-01.png)

- <span data-ttu-id="9b79a-111">创建新的执行组件，并将其添加到场景</span><span class="sxs-lookup"><span data-stu-id="9b79a-111">Create a new actor and add it to your scene</span></span>

> [!NOTE]
> <span data-ttu-id="9b79a-112">Unreal 中的 HoloLens 眼睛跟踪仅有两个眼睛的一眼。</span><span class="sxs-lookup"><span data-stu-id="9b79a-112">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes.</span></span> <span data-ttu-id="9b79a-113">不支持 Stereoscopic 跟踪，这需要两个射线。</span><span class="sxs-lookup"><span data-stu-id="9b79a-113">Stereoscopic tracking, which requires two rays, isn't supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="9b79a-114">使用眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="9b79a-114">Using eye tracking</span></span>

<span data-ttu-id="9b79a-115">首先，检查设备是否支持通过 **IsEyeTrackerConnected** 函数进行目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="9b79a-115">First, check that your device supports eye tracking with the **IsEyeTrackerConnected** function.</span></span>  <span data-ttu-id="9b79a-116">如果该函数返回 true，则调用 **GetGazeData** 以查找用户眼睛在当前帧中的位置：</span><span class="sxs-lookup"><span data-stu-id="9b79a-116">If the function returns true, call **GetGazeData** to find where the user’s eyes are looking at in the current frame:</span></span>

![的蓝图为目视跟踪连接函数](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="9b79a-118">HoloLens 上不提供固定点和置信度值。</span><span class="sxs-lookup"><span data-stu-id="9b79a-118">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="9b79a-119">在线条轨迹中使用 "注视原点" 和 "方向" 来找出用户正在寻找的内容。</span><span class="sxs-lookup"><span data-stu-id="9b79a-119">Use the gaze origin and direction in a line trace to find out exactly where your users are looking.</span></span>  <span data-ttu-id="9b79a-120">"注视" 值为向量，从注视原点开始，沿原点结束，并沿线条轨迹的距离结束：</span><span class="sxs-lookup"><span data-stu-id="9b79a-120">The gaze value is a vector, starting at the gaze origin and ending at the origin plus the gaze direction multiplied by the line trace distance:</span></span>

![获取注视数据函数的蓝图](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="9b79a-122">获取打印头方向</span><span class="sxs-lookup"><span data-stu-id="9b79a-122">Getting head orientation</span></span>

<span data-ttu-id="9b79a-123">你还可以使用 Head 已装入显示 (HMD) 的旋转来表示用户的头的方向。</span><span class="sxs-lookup"><span data-stu-id="9b79a-123">You can also use the rotation of the Head Mounted Display (HMD) to represent the direction of the user’s head.</span></span> <span data-ttu-id="9b79a-124">你可以在不启用 "注视输入" 功能的情况下获取用户头，但不会获得任何目视跟踪信息。</span><span class="sxs-lookup"><span data-stu-id="9b79a-124">You can get the users head direction without enabling the Gaze Input capability, but you won't get you any eye tracking information.</span></span>  <span data-ttu-id="9b79a-125">添加对蓝图的引用作为世界上下文，以获取正确的输出数据：</span><span class="sxs-lookup"><span data-stu-id="9b79a-125">Add a reference to the blueprint as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="9b79a-126">获取 HMD 数据仅在 Unreal 4.26 和更高版本中可用。</span><span class="sxs-lookup"><span data-stu-id="9b79a-126">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Get HMDData 函数的蓝图](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="9b79a-128">使用 C++</span><span class="sxs-lookup"><span data-stu-id="9b79a-128">Using C++</span></span>

- <span data-ttu-id="9b79a-129">在游戏的 **build.cs** 文件中，将 **EyeTracker** 添加到 **PublicDependencyModuleNames** 列表：</span><span class="sxs-lookup"><span data-stu-id="9b79a-129">In your game’s **build.cs** file, add **EyeTracker** to the **PublicDependencyModuleNames** list:</span></span>

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

- <span data-ttu-id="9b79a-130">在 "**文件/新 c + + 类**" 中，创建名为 **EyeTracker** 的新 c + + 参与者</span><span class="sxs-lookup"><span data-stu-id="9b79a-130">In **File/ New C++ Class**, create a new C++ actor called **EyeTracker**</span></span>
    - <span data-ttu-id="9b79a-131">Visual Studio 解决方案将打开新的 EyeTracker 类。</span><span class="sxs-lookup"><span data-stu-id="9b79a-131">A Visual Studio solution will open up the new EyeTracker class.</span></span> <span data-ttu-id="9b79a-132">生成并运行，以通过新的 EyeTracker 参与者打开 Unreal 游戏。</span><span class="sxs-lookup"><span data-stu-id="9b79a-132">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="9b79a-133">在 " **放置参与者** " 窗口中搜索 "EyeTracker"，并将类拖放到游戏窗口，以将其添加到项目中：</span><span class="sxs-lookup"><span data-stu-id="9b79a-133">Search for “EyeTracker” in the **Place Actors** window and drag and drop the class into the game window to add it to the project:</span></span>

![参与者窗口打开的参与者的屏幕截图](images/unreal-gaze-img-06.png)

- <span data-ttu-id="9b79a-135">在 **EyeTracker** 中，添加 **EyeTrackerFunctionLibrary** 和 **DrawDebugHelpers** 的包含：</span><span class="sxs-lookup"><span data-stu-id="9b79a-135">In **EyeTracker.cpp**, add includes for **EyeTrackerFunctionLibrary**, and **DrawDebugHelpers**:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="9b79a-136">尝试获取任何目视的数据之前，请检查你的设备是否支持 **UEyeTrackerFunctionLibrary：： IsEyeTrackerConnected** 的目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="9b79a-136">Check that your device supports eye tracking with **UEyeTrackerFunctionLibrary::IsEyeTrackerConnected** before trying to get any gaze data.</span></span>  <span data-ttu-id="9b79a-137">如果支持目视跟踪，请从 **UEyeTrackerFunctionLibrary：： GetGazeData** 中查找线条跟踪的射线的起点和终点。</span><span class="sxs-lookup"><span data-stu-id="9b79a-137">If eye tracking is supported, find the start and end of a ray for a line trace from **UEyeTrackerFunctionLibrary::GetGazeData**.</span></span> <span data-ttu-id="9b79a-138">在该处，可以构造一个注视向量，并将其内容传递到 **LineTraceSingleByChannel** 以调试任何射线命中结果：</span><span class="sxs-lookup"><span data-stu-id="9b79a-138">From there, you can construct a gaze vector and pass its contents to **LineTraceSingleByChannel** to debug any ray hit results:</span></span>

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

## <a name="next-development-checkpoint"></a><span data-ttu-id="9b79a-139">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="9b79a-139">Next Development Checkpoint</span></span>

<span data-ttu-id="9b79a-140">如果遵循我们的 Unreal 开发旅程，就是在探索 MRTK 核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="9b79a-140">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="9b79a-141">从这里，你可以继续执行下一个构建基块：</span><span class="sxs-lookup"><span data-stu-id="9b79a-141">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9b79a-142">手部跟踪</span><span class="sxs-lookup"><span data-stu-id="9b79a-142">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="9b79a-143">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="9b79a-143">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9b79a-144">HoloLens 摄像头</span><span class="sxs-lookup"><span data-stu-id="9b79a-144">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="9b79a-145">你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="9b79a-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b79a-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9b79a-146">See also</span></span>
* [<span data-ttu-id="9b79a-147">校准</span><span class="sxs-lookup"><span data-stu-id="9b79a-147">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="9b79a-148">舒适</span><span class="sxs-lookup"><span data-stu-id="9b79a-148">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="9b79a-149">凝视和提交</span><span class="sxs-lookup"><span data-stu-id="9b79a-149">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="9b79a-150">语音输入</span><span class="sxs-lookup"><span data-stu-id="9b79a-150">Voice input</span></span>](../../out-of-scope/voice-design.md)
