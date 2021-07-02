---
title: 眼部校准
description: 如何在 MRTK 中设置用户眼校准
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， EyeTracking， 校准，
ms.openlocfilehash: a2023a2d7f6a0254e8fef32f4faf09def956e94f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177199"
---
# <a name="eye-calibration"></a><span data-ttu-id="0f80b-104">眼部校准</span><span class="sxs-lookup"><span data-stu-id="0f80b-104">Eye calibration</span></span>

![眼部校准通知的屏幕截图](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a><span data-ttu-id="0f80b-106">概述</span><span class="sxs-lookup"><span data-stu-id="0f80b-106">Overview</span></span>

<span data-ttu-id="0f80b-107">如果眼动跟踪是应用体验的基本部分，你可能希望确保用户的眼部校准有效。</span><span class="sxs-lookup"><span data-stu-id="0f80b-107">If eye tracking is a fundamental part of your app experience, one may wish to ensure that the user's eye calibration is valid.</span></span>
<span data-ttu-id="0f80b-108">它无效的主要原因是用户在放置设备时选择了跳过眼动跟踪校准。</span><span class="sxs-lookup"><span data-stu-id="0f80b-108">The main reason for it to be invalid is that the user has chosen to skip the eye tracking calibration when putting on the device.</span></span>

<span data-ttu-id="0f80b-109">本页涵盖以下内容：</span><span class="sxs-lookup"><span data-stu-id="0f80b-109">This page covers the following:</span></span>

- <span data-ttu-id="0f80b-110">描述如何检测用户是否进行了眼部校准</span><span class="sxs-lookup"><span data-stu-id="0f80b-110">Describes how to detect that a user is eye calibrated</span></span>
- <span data-ttu-id="0f80b-111">提供一个示例，了解如何触发用户通知以指示用户进行眼部校准</span><span class="sxs-lookup"><span data-stu-id="0f80b-111">Provides a sample for how to trigger a user notification to instruct the user to go through the eye calibration</span></span>
  - <span data-ttu-id="0f80b-112">如果眼部校准生效，则自动消除通知</span><span class="sxs-lookup"><span data-stu-id="0f80b-112">Automatically dismiss notification if eye calibration becomes valid</span></span>
  - <span data-ttu-id="0f80b-113">如果用户选择在不校准的情况下继续，则手动关闭通知</span><span class="sxs-lookup"><span data-stu-id="0f80b-113">Manually dismiss notification if user chooses to continue without calibration</span></span>

### <a name="how-to-detect-the-eye-calibration-state"></a><span data-ttu-id="0f80b-114">如何检测眼部校准状态</span><span class="sxs-lookup"><span data-stu-id="0f80b-114">How to detect the eye calibration state</span></span>

<span data-ttu-id="0f80b-115">MRTK 中的眼动跟踪配置是通过 接口 [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) 配置的。</span><span class="sxs-lookup"><span data-stu-id="0f80b-115">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span>

<span data-ttu-id="0f80b-116">使用 [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) 提供在运行时在工具包中注册的默认凝视提供程序实现。</span><span class="sxs-lookup"><span data-stu-id="0f80b-116">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span> <span data-ttu-id="0f80b-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` 如果 `bool?` 眼动跟踪器中尚没有可用信息，则 返回一个为 null 的 。</span><span class="sxs-lookup"><span data-stu-id="0f80b-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` returns a `bool?` which is null if no information from the eye tracker is available yet.</span></span>
<span data-ttu-id="0f80b-118">收到数据后，它将返回 true 或 false，以指示用户的眼动跟踪校准有效或无效。</span><span class="sxs-lookup"><span data-stu-id="0f80b-118">Once data has been received, it will either return true or false to indicate that the user's eye tracking calibration is valid or invalid.</span></span>

### <a name="sample-eye-calibration-notification---step-by-step"></a><span data-ttu-id="0f80b-119">样本眼校准通知 - 分步</span><span class="sxs-lookup"><span data-stu-id="0f80b-119">Sample eye calibration notification - step-by-step</span></span>

1. <span data-ttu-id="0f80b-120">打开 MRTK 眼动跟踪示例包 (Assets/MRTK/Examples/Demos/EyeTracking) </span><span class="sxs-lookup"><span data-stu-id="0f80b-120">Open the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking)</span></span>

2. <span data-ttu-id="0f80b-121">加载 _EyeTrackingDemo-00-RootScene.unity_ 场景</span><span class="sxs-lookup"><span data-stu-id="0f80b-121">Load _EyeTrackingDemo-00-RootScene.unity_ scene</span></span>

3. <span data-ttu-id="0f80b-122">查看 _EyeCalibrationChecker：_</span><span class="sxs-lookup"><span data-stu-id="0f80b-122">Check out _EyeCalibrationChecker_:</span></span>
   - <span data-ttu-id="0f80b-123">在此场景中，我们已有一个检测当前用户是否在 *_EyeCalibrationChecker_* 游戏对象 下校准的示例。</span><span class="sxs-lookup"><span data-stu-id="0f80b-123">In this scene, we have already a sample for detecting whether the current user is calibrated under the *_EyeCalibrationChecker_ game object*.</span></span>
<span data-ttu-id="0f80b-124">它仅作为一些文本网格的父对象，并且具有一些用于将通知混合在一起的其他触发器。这包括在激活时逐渐增加其大小和不透明度。</span><span class="sxs-lookup"><span data-stu-id="0f80b-124">It simply parents a few text meshes and has some additional triggers for blending the notification in and out. This includes slowly increasing its size and opacity on activation.</span></span>
<span data-ttu-id="0f80b-125">关闭通知后，它会逐渐减小其大小并淡出。</span><span class="sxs-lookup"><span data-stu-id="0f80b-125">Once the notification is dismissed, it will slowly decrease its size and fade out.</span></span>

   - <span data-ttu-id="0f80b-126">附加到 *_EyeCalibrationChecker_ 游戏对象的* 是 [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) 脚本，该脚本公开两个 Unity 事件：</span><span class="sxs-lookup"><span data-stu-id="0f80b-126">Attached to the *_EyeCalibrationChecker_ game object* is the [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) script which exposes two Unity Events:</span></span>
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - <span data-ttu-id="0f80b-127">这些事件仅在校准状态更改时触发。</span><span class="sxs-lookup"><span data-stu-id="0f80b-127">These events will only trigger if the calibration status changes.</span></span> <span data-ttu-id="0f80b-128">因此，如果用户选择关闭通知，则通知不会再次显示，直到</span><span class="sxs-lookup"><span data-stu-id="0f80b-128">Hence, if a user chooses to dismiss the notification, the notification will not show up again until</span></span>
      - <span data-ttu-id="0f80b-129">重启应用</span><span class="sxs-lookup"><span data-stu-id="0f80b-129">The app gets restarted</span></span>
      - <span data-ttu-id="0f80b-130">检测到有效的用户，然后新的未校准用户将设备置于</span><span class="sxs-lookup"><span data-stu-id="0f80b-130">A valid user has been detected and then a new uncalibrated user has put the device on</span></span>

   - <span data-ttu-id="0f80b-131">为了测试动画和事件是否已正确触发，EyeCalibrationChecker 脚本拥有 `bool editorTestUserIsCalibrated` 标志。</span><span class="sxs-lookup"><span data-stu-id="0f80b-131">For testing whether the animations and events are triggered correctly, the EyeCalibrationChecker script possesses a `bool editorTestUserIsCalibrated` flag.</span></span> <span data-ttu-id="0f80b-132">例如，在 Unity 编辑器中运行时，可以测试：</span><span class="sxs-lookup"><span data-stu-id="0f80b-132">For example, when running in the Unity Editor, one can test:</span></span>
      1. <span data-ttu-id="0f80b-133">校准状态从 true 更改为 false 后，通知是否自动弹出</span><span class="sxs-lookup"><span data-stu-id="0f80b-133">Whether the notification automatically pops up once the calibration status changes from true to false</span></span>
      1. <span data-ttu-id="0f80b-134">在状态从 false 更改为 true 后，是否自动再次关闭通知。</span><span class="sxs-lookup"><span data-stu-id="0f80b-134">Whether it automatically dismisses the notification again once the status changes from false to true.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0f80b-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f80b-135">See also</span></span>

- [<span data-ttu-id="0f80b-136">MRTK 眼动跟踪概述</span><span class="sxs-lookup"><span data-stu-id="0f80b-136">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="0f80b-137">MRTK 眼动跟踪设置</span><span class="sxs-lookup"><span data-stu-id="0f80b-137">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="0f80b-138">通过代码进行 MRTK 眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="0f80b-138">MRTK Eye Tracking via Code</span></span>](eye-tracking-eye-gaze-provider.md)
- [<span data-ttu-id="0f80b-139">HoloLens 2眼动跟踪文档</span><span class="sxs-lookup"><span data-stu-id="0f80b-139">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)
