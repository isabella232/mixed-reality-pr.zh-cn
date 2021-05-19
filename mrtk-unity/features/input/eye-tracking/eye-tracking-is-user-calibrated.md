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
   - 在此场景中，我们已经有了一个示例，用于检测是否在 *_EyeCalibrationChecker_ 游戏对象* 下校准了当前用户。
它只是父级几个文本网格，还有一些附加触发器，用于将通知混合入和移出。这包括缓慢增加其大小和激活时的不透明度。
一旦通知被消除，它会慢慢地降低其大小并淡出。

   - 附加到 *_EyeCalibrationChecker_ 游戏对象* 是公开两个 Unity 事件的 [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker)脚本：
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - 仅当校准状态发生更改时，才会触发这些事件。 因此，如果用户选择取消通知，则通知将不再显示，直到
      - 应用重新启动
      - 已检测到有效的用户，然后一个新的 uncalibrated 用户已将该设备置于

   - 为测试是否正确触发了动画和事件，EyeCalibrationChecker 脚本拥有一个 `bool editorTestUserIsCalibrated` 标志。 例如，在 Unity 编辑器中运行时，可以测试：
      1. 校准状态从 true 变为 false 后是否自动弹出通知
      1. 当状态从 false 更改为 true 时，是否再次自动消除通知。

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

- [MRTK 目视跟踪概述](eye-tracking-main.md)
- [MRTK 目视跟踪设置](eye-tracking-basic-setup.md)
- [通过代码 MRTK 目视跟踪](eye-tracking-eye-gaze-provider.md)
- [HoloLens 2 目视跟踪文档](/windows/mixed-reality/eye-tracking)