---
title: 眼动跟踪注视提供者
description: MRTK 中的眼睛查看器文档
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，EyeTracking，EyeGaze，
ms.openlocfilehash: ef50a55d52a5dad9f424c8af8139565e02542b6c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144024"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a><span data-ttu-id="d7319-104">在 Unity 脚本中访问目视跟踪数据</span><span class="sxs-lookup"><span data-stu-id="d7319-104">Accessing eye tracking data in your Unity script</span></span>

<span data-ttu-id="d7319-105">本文假设已了解如何在 MRTK 场景中设置目视跟踪 (参阅 [基本 MRTK 安装程序以使用目视跟踪](eye-tracking-basic-setup.md)) 。</span><span class="sxs-lookup"><span data-stu-id="d7319-105">This article assumes one has understanding for setting up eye tracking in an MRTK scene (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)).</span></span>
<span data-ttu-id="d7319-106">在 MonoBehaviour 脚本中访问眼睛跟踪数据非常简单！</span><span class="sxs-lookup"><span data-stu-id="d7319-106">Accessing eye tracking data in a MonoBehaviour script is easy!</span></span> <span data-ttu-id="d7319-107">只需使用 *CoreServices. InputSystem. EyeGazeProvider*。</span><span class="sxs-lookup"><span data-stu-id="d7319-107">Simply use *CoreServices.InputSystem.EyeGazeProvider*.</span></span>

## <a name="imixedrealityeyegazeprovider"></a><span data-ttu-id="d7319-108">IMixedRealityEyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="d7319-108">IMixedRealityEyeGazeProvider</span></span>

<span data-ttu-id="d7319-109">MRTK 中的目视跟踪配置通过接口进行配置 [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) 。</span><span class="sxs-lookup"><span data-stu-id="d7319-109">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span> <span data-ttu-id="d7319-110">使用 [CoreServices](eye-tracking-eye-gaze-provider.md) 可在运行时在工具包中注册默认的注视提供程序实现。</span><span class="sxs-lookup"><span data-stu-id="d7319-110">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span>
<span data-ttu-id="d7319-111">的有用属性 `EyeGazeProvider` 如下所述。</span><span class="sxs-lookup"><span data-stu-id="d7319-111">Useful properties of the `EyeGazeProvider` is outlined below.</span></span>

- <span data-ttu-id="d7319-112">**IsEyeTrackingEnabled**：如果用户已选择使用目视跟踪进行注视，则为 True。</span><span class="sxs-lookup"><span data-stu-id="d7319-112">**IsEyeTrackingEnabled**: True if user has selected to use eye tracking for gaze.</span></span>

- <span data-ttu-id="d7319-113">**IsEyeCalibrationValid**：指示用户的目视跟踪校准是否有效。</span><span class="sxs-lookup"><span data-stu-id="d7319-113">**IsEyeCalibrationValid**: Indicates whether the user's eye tracking calibration is valid or not.</span></span>
<span data-ttu-id="d7319-114">如果值尚未从目视跟踪系统收到数据，则返回 "null"。</span><span class="sxs-lookup"><span data-stu-id="d7319-114">It returns 'null', if the value has not yet received data from the eye tracking system.</span></span>
<span data-ttu-id="d7319-115">它可能无效，因为用户跳过了眼睛跟踪校准。</span><span class="sxs-lookup"><span data-stu-id="d7319-115">It may be invalid, because the user skipped the eye tracking calibration.</span></span>

- <span data-ttu-id="d7319-116">**IsEyeTrackingEnabledAndValid**：指示当前目视跟踪数据当前是否用于注视。</span><span class="sxs-lookup"><span data-stu-id="d7319-116">**IsEyeTrackingEnabledAndValid**: Indicates whether the current eye tracking data is currently been used for gaze.</span></span>

- <span data-ttu-id="d7319-117">**IsEyeTrackingDataValid**：如果目视跟踪数据可用，则为 True。</span><span class="sxs-lookup"><span data-stu-id="d7319-117">**IsEyeTrackingDataValid**: True if eye tracking data is available.</span></span>
<span data-ttu-id="d7319-118">由于超时 (应该会使用户处于稳定状态，但) 或缺少跟踪硬件或权限时，此功能可能会变得不可用。</span><span class="sxs-lookup"><span data-stu-id="d7319-118">It may be unavailable due to exceeded timeout (should be robust to the user blinking though) or lack of tracking hardware or permissions.</span></span>
<span data-ttu-id="d7319-119">查看缺少的 [眼睛校准通知示例](eye-tracking-is-user-calibrated.md) ，该示例说明如何检测用户是否引人注目，并显示相应的通知。</span><span class="sxs-lookup"><span data-stu-id="d7319-119">Check out our [Missing eye calibration notification sample](eye-tracking-is-user-calibrated.md) that explains how to detect whether a user is eye calibrated and to show an appropriate notification.</span></span>

- <span data-ttu-id="d7319-120">**GazeOrigin**： "注视" 射线的原点。</span><span class="sxs-lookup"><span data-stu-id="d7319-120">**GazeOrigin**: Origin of the gaze ray.</span></span>
<span data-ttu-id="d7319-121">请注意，如果 "IsEyeGazeValid" 为 false，则将返回 *打印头* 注视原点。</span><span class="sxs-lookup"><span data-stu-id="d7319-121">Please note that this will return the *head* gaze origin if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="d7319-122">**GazeDirection：** 凝视射线的方向。</span><span class="sxs-lookup"><span data-stu-id="d7319-122">**GazeDirection**: Direction of the gaze ray.</span></span>
<span data-ttu-id="d7319-123">如果"IsEyeGazeValid"为 false，这将返回头部凝视方向。 </span><span class="sxs-lookup"><span data-stu-id="d7319-123">This will return the *head* gaze direction if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="d7319-124">HitInfo、HitPosition、HitNormal 等：有关当前目标的信息。  </span><span class="sxs-lookup"><span data-stu-id="d7319-124">**HitInfo**, **HitPosition**, **HitNormal**, etc.: Information about the currently gazed at target.</span></span>
<span data-ttu-id="d7319-125">同样， `IsEyeGazeValid` 如果 为 false，则这基于用户的 *头部凝* 视。</span><span class="sxs-lookup"><span data-stu-id="d7319-125">Again, if `IsEyeGazeValid` is false, this will be based on the user's *head* gaze.</span></span>

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a><span data-ttu-id="d7319-126">使用 CoreServices.InputSystem.EyeGazeProvider 的示例</span><span class="sxs-lookup"><span data-stu-id="d7319-126">Examples for using CoreServices.InputSystem.EyeGazeProvider</span></span>

<span data-ttu-id="d7319-127">下面是 [FollowEyeGaze.cs 的示例](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze)：</span><span class="sxs-lookup"><span data-stu-id="d7319-127">Here is an example from the [FollowEyeGaze.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):</span></span>

- <span data-ttu-id="d7319-128">获取用户正在查看的全息影像点：</span><span class="sxs-lookup"><span data-stu-id="d7319-128">Get the point of a hologram that the user is looking at:</span></span>

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- <span data-ttu-id="d7319-129">显示与用户当前正在查找的可视资产保持固定距离：</span><span class="sxs-lookup"><span data-stu-id="d7319-129">Showing a visual asset at a fixed distance from where the user is currently looking:</span></span>

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a><span data-ttu-id="d7319-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d7319-130">See also</span></span>

- [<span data-ttu-id="d7319-131">MRTK 眼动跟踪概述</span><span class="sxs-lookup"><span data-stu-id="d7319-131">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="d7319-132">MRTK 眼动跟踪设置</span><span class="sxs-lookup"><span data-stu-id="d7319-132">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="d7319-133">MRTK 眼动跟踪校准</span><span class="sxs-lookup"><span data-stu-id="d7319-133">MRTK Eye Tracking Calibration</span></span>](eye-tracking-is-user-calibrated.md)
- [<span data-ttu-id="d7319-134">HoloLens 2眼动跟踪文档</span><span class="sxs-lookup"><span data-stu-id="d7319-134">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)