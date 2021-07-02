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
# <a name="eye-calibration"></a>眼部校准

![眼部校准通知的屏幕截图](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a>概述

如果眼动跟踪是应用体验的基本部分，你可能希望确保用户的眼部校准有效。
它无效的主要原因是用户在放置设备时选择了跳过眼动跟踪校准。

本页涵盖以下内容：

- 描述如何检测用户是否进行了眼部校准
- 提供一个示例，了解如何触发用户通知以指示用户进行眼部校准
  - 如果眼部校准生效，则自动消除通知
  - 如果用户选择在不校准的情况下继续，则手动关闭通知

### <a name="how-to-detect-the-eye-calibration-state"></a>如何检测眼部校准状态

MRTK 中的眼动跟踪配置是通过 接口 [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) 配置的。

使用 [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) 提供在运行时在工具包中注册的默认凝视提供程序实现。 `IMixedRealityEyeGazeProvider.IsEyeGazeValid` 如果 `bool?` 眼动跟踪器中尚没有可用信息，则 返回一个为 null 的 。
收到数据后，它将返回 true 或 false，以指示用户的眼动跟踪校准有效或无效。

### <a name="sample-eye-calibration-notification---step-by-step"></a>样本眼校准通知 - 分步

1. 打开 MRTK 眼动跟踪示例包 (Assets/MRTK/Examples/Demos/EyeTracking) 

2. 加载 _EyeTrackingDemo-00-RootScene.unity_ 场景

3. 查看 _EyeCalibrationChecker：_
   - 在此场景中，我们已有一个检测当前用户是否在 *_EyeCalibrationChecker_* 游戏对象 下校准的示例。
它仅作为一些文本网格的父对象，并且具有一些用于将通知混合在一起的其他触发器。这包括在激活时逐渐增加其大小和不透明度。
关闭通知后，它会逐渐减小其大小并淡出。

   - 附加到 *_EyeCalibrationChecker_ 游戏对象的* 是 [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) 脚本，该脚本公开两个 Unity 事件：
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - 这些事件仅在校准状态更改时触发。 因此，如果用户选择关闭通知，则通知不会再次显示，直到
      - 重启应用
      - 检测到有效的用户，然后新的未校准用户将设备置于

   - 为了测试动画和事件是否已正确触发，EyeCalibrationChecker 脚本拥有 `bool editorTestUserIsCalibrated` 标志。 例如，在 Unity 编辑器中运行时，可以测试：
      1. 校准状态从 true 更改为 false 后，通知是否自动弹出
      1. 在状态从 false 更改为 true 后，是否自动再次关闭通知。

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

## <a name="see-also"></a>另请参阅

- [MRTK 眼动跟踪概述](eye-tracking-main.md)
- [MRTK 眼动跟踪设置](eye-tracking-basic-setup.md)
- [通过代码进行 MRTK 眼动跟踪](eye-tracking-eye-gaze-provider.md)
- [HoloLens 2眼动跟踪文档](/windows/mixed-reality/eye-tracking)
