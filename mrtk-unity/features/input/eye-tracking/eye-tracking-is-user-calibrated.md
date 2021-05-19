---
title: 目视校准
description: 如何在 MRTK 中设置用户眼校准
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， EyeTracking， 校准，
ms.openlocfilehash: d7ae9885b77798b44b3d63bb7f92283658e05411
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143999"
---
# <a name="eye-calibration"></a><span data-ttu-id="a14eb-104">眼部校准</span><span class="sxs-lookup"><span data-stu-id="a14eb-104">Eye calibration</span></span>

![眼部校准通知的屏幕截图](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a><span data-ttu-id="a14eb-106">概述</span><span class="sxs-lookup"><span data-stu-id="a14eb-106">Overview</span></span>

<span data-ttu-id="a14eb-107">如果眼动跟踪是应用体验的基本部分，你可能希望确保用户的眼部校准有效。</span><span class="sxs-lookup"><span data-stu-id="a14eb-107">If eye tracking is a fundamental part of your app experience, one may wish to ensure that the user's eye calibration is valid.</span></span>
<span data-ttu-id="a14eb-108">它无效的主要原因是用户在放置设备时选择了跳过眼动跟踪校准。</span><span class="sxs-lookup"><span data-stu-id="a14eb-108">The main reason for it to be invalid is that the user has chosen to skip the eye tracking calibration when putting on the device.</span></span>

<span data-ttu-id="a14eb-109">本页涵盖以下内容：</span><span class="sxs-lookup"><span data-stu-id="a14eb-109">This page covers the following:</span></span>

- <span data-ttu-id="a14eb-110">描述如何检测用户是否进行了眼部校准</span><span class="sxs-lookup"><span data-stu-id="a14eb-110">Describes how to detect that a user is eye calibrated</span></span>
- <span data-ttu-id="a14eb-111">提供一个示例，了解如何触发用户通知以指示用户进行眼部校准</span><span class="sxs-lookup"><span data-stu-id="a14eb-111">Provides a sample for how to trigger a user notification to instruct the user to go through the eye calibration</span></span>
  - <span data-ttu-id="a14eb-112">如果眼部校准生效，则自动消除通知</span><span class="sxs-lookup"><span data-stu-id="a14eb-112">Automatically dismiss notification if eye calibration becomes valid</span></span>
  - <span data-ttu-id="a14eb-113">如果用户选择在不校准的情况下继续，则手动关闭通知</span><span class="sxs-lookup"><span data-stu-id="a14eb-113">Manually dismiss notification if user chooses to continue without calibration</span></span>

### <a name="how-to-detect-the-eye-calibration-state"></a><span data-ttu-id="a14eb-114">如何检测眼部校准状态</span><span class="sxs-lookup"><span data-stu-id="a14eb-114">How to detect the eye calibration state</span></span>

<span data-ttu-id="a14eb-115">MRTK 中的眼动跟踪配置是通过 接口 [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) 配置的。</span><span class="sxs-lookup"><span data-stu-id="a14eb-115">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span>

<span data-ttu-id="a14eb-116">使用 [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) 提供在运行时在工具包中注册的默认凝视提供程序实现。</span><span class="sxs-lookup"><span data-stu-id="a14eb-116">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span> <span data-ttu-id="a14eb-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` 如果 `bool?` 眼动跟踪器中尚没有可用信息，则 返回一个为 null 的 。</span><span class="sxs-lookup"><span data-stu-id="a14eb-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` returns a `bool?` which is null if no information from the eye tracker is available yet.</span></span>
<span data-ttu-id="a14eb-118">收到数据后，它将返回 true 或 false，以指示用户的眼动跟踪校准有效或无效。</span><span class="sxs-lookup"><span data-stu-id="a14eb-118">Once data has been received, it will either return true or false to indicate that the user's eye tracking calibration is valid or invalid.</span></span>

### <a name="sample-eye-calibration-notification---step-by-step"></a><span data-ttu-id="a14eb-119">样本眼校准通知 - 分步</span><span class="sxs-lookup"><span data-stu-id="a14eb-119">Sample eye calibration notification - step-by-step</span></span>

1. <span data-ttu-id="a14eb-120">打开 MRTK 眼动跟踪示例包 (Assets/MRTK/Examples/Demos/EyeTracking) </span><span class="sxs-lookup"><span data-stu-id="a14eb-120">Open the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking)</span></span>

2. <span data-ttu-id="a14eb-121">加载 _EyeTrackingDemo-00-RootScene.unity_ 场景</span><span class="sxs-lookup"><span data-stu-id="a14eb-121">Load _EyeTrackingDemo-00-RootScene.unity_ scene</span></span>

3. <span data-ttu-id="a14eb-122">查看 _EyeCalibrationChecker：_</span><span class="sxs-lookup"><span data-stu-id="a14eb-122">Check out _EyeCalibrationChecker_:</span></span>
   - <span data-ttu-id="a14eb-123">在此场景中，我们已经有了一个示例，用于检测是否在 *_EyeCalibrationChecker_ 游戏对象* 下校准了当前用户。</span><span class="sxs-lookup"><span data-stu-id="a14eb-123">In this scene, we have already a sample for detecting whether the current user is calibrated under the *_EyeCalibrationChecker_ game object*.</span></span>
<span data-ttu-id="a14eb-124">它只是父级几个文本网格，还有一些附加触发器，用于将通知混合入和移出。这包括缓慢增加其大小和激活时的不透明度。</span><span class="sxs-lookup"><span data-stu-id="a14eb-124">It simply parents a few text meshes and has some additional triggers for blending the notification in and out. This includes slowly increasing its size and opacity on activation.</span></span>
<span data-ttu-id="a14eb-125">一旦通知被消除，它会慢慢地降低其大小并淡出。</span><span class="sxs-lookup"><span data-stu-id="a14eb-125">Once the notification is dismissed, it will slowly decrease its size and fade out.</span></span>

   - <span data-ttu-id="a14eb-126">附加到 *_EyeCalibrationChecker_ 游戏对象* 是公开两个 Unity 事件的 [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker)脚本：</span><span class="sxs-lookup"><span data-stu-id="a14eb-126">Attached to the *_EyeCalibrationChecker_ game object* is the [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) script which exposes two Unity Events:</span></span>
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - <span data-ttu-id="a14eb-127">仅当校准状态发生更改时，才会触发这些事件。</span><span class="sxs-lookup"><span data-stu-id="a14eb-127">These events will only trigger if the calibration status changes.</span></span> <span data-ttu-id="a14eb-128">因此，如果用户选择取消通知，则通知将不再显示，直到</span><span class="sxs-lookup"><span data-stu-id="a14eb-128">Hence, if a user chooses to dismiss the notification, the notification will not show up again until</span></span>
      - <span data-ttu-id="a14eb-129">应用重新启动</span><span class="sxs-lookup"><span data-stu-id="a14eb-129">The app gets restarted</span></span>
      - <span data-ttu-id="a14eb-130">已检测到有效的用户，然后一个新的 uncalibrated 用户已将该设备置于</span><span class="sxs-lookup"><span data-stu-id="a14eb-130">A valid user has been detected and then a new uncalibrated user has put the device on</span></span>

   - <span data-ttu-id="a14eb-131">为测试是否正确触发了动画和事件，EyeCalibrationChecker 脚本拥有一个 `bool editorTestUserIsCalibrated` 标志。</span><span class="sxs-lookup"><span data-stu-id="a14eb-131">For testing whether the animations and events are triggered correctly, the EyeCalibrationChecker script possesses a `bool editorTestUserIsCalibrated` flag.</span></span> <span data-ttu-id="a14eb-132">例如，在 Unity 编辑器中运行时，可以测试：</span><span class="sxs-lookup"><span data-stu-id="a14eb-132">For example, when running in the Unity Editor, one can test:</span></span>
      1. <span data-ttu-id="a14eb-133">校准状态从 true 变为 false 后是否自动弹出通知</span><span class="sxs-lookup"><span data-stu-id="a14eb-133">Whether the notification automatically pops up once the calibration status changes from true to false</span></span>
      1. <span data-ttu-id="a14eb-134">当状态从 false 更改为 true 时，是否再次自动消除通知。</span><span class="sxs-lookup"><span data-stu-id="a14eb-134">Whether it automatically dismisses the notification again once the status changes from false to true.</span></span>

```c#
    private bool? prevCalibrationStatus = null;
    ...

   void Update()
   {
      // Get the latest calibration state from the EyeGazeProvider
      bool? calibrationStatus = CoreServices.InputSystem?.EyeGazeProvider?.IsEyeCalibrationValid;

      ...

      if (calibrationStatus != null)
      {
         if (prevCalibrationStatus != calibrationStatus)
         {
            if (calibrationStatus == false)
            {
               OnNoEyeCalibrationDetected.Invoke();
            }
         else
         {
            OnEyeCalibrationDetected.Invoke();
         }

         prevCalibrationStatus = calibrationStatus;
      }
   }
```

## <a name="see-also"></a><span data-ttu-id="a14eb-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a14eb-135">See also</span></span>

- [<span data-ttu-id="a14eb-136">MRTK 目视跟踪概述</span><span class="sxs-lookup"><span data-stu-id="a14eb-136">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="a14eb-137">MRTK 目视跟踪设置</span><span class="sxs-lookup"><span data-stu-id="a14eb-137">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="a14eb-138">通过代码 MRTK 目视跟踪</span><span class="sxs-lookup"><span data-stu-id="a14eb-138">MRTK Eye Tracking via Code</span></span>](eye-tracking-eye-gaze-provider.md)
- [<span data-ttu-id="a14eb-139">HoloLens 2 目视跟踪文档</span><span class="sxs-lookup"><span data-stu-id="a14eb-139">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)