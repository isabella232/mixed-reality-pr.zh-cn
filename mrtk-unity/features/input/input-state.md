---
title: 输入状态
description: MRTK 中的输入状态文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，Mixed Reality，开发，MRTK，InputState，
ms.openlocfilehash: 7d5e008ae3e43d227b90a563dd74e65a89527bd7ddf1720e26577042ce0d545f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228357"
---
# <a name="accessing-input-state-in-mrtk"></a>访问 MRTK 中的输入状态

通过循环访问附加到输入源的控制器，可以直接在 MRTK 中查询所有输入的状态。 MRTK 还提供了一种便捷方法，用于访问眼睛、双手、头和运动控制器的位置和旋转。

请参阅 InputDataExample 场景，了解通过遍历控制器和使用类查询输入的示例 [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) 。

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a>示例： Access 位置、头 MRTK 的旋转、双手、眼睛

MRTK 的 [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) 类提供用于访问手型、打印头、眼睛眼睛和运动控制器光线的便利方法。

```c#
// Get the head ray
var headRay = InputRayUtils.GetHeadGazeRay();

// Get the right hand ray
Ray rightHandRay;
if(InputRayUtils.TryGetHandRay(Handedness.right, rightHandRay))
{
    // Right hand ray is available
}
else
{
    // Right hand ray is not available
}
```

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a>示例：访问位置，场景中处于活动状态的所有6DOF 控制器的旋转

```c#
foreach(var controller in CoreServices.InputSystem.DetectedControllers)
{
    // Interactions for a controller is the list of inputs that this controller exposes
    foreach(MixedRealityInteractionMapping inputMapping in controller.Interactions)
    {
        // 6DOF controllers support the "SpatialPointer" type (pointing direction)
        // or "GripPointer" type (direction of the 6DOF controller)
        if (inputMapping.InputType == DeviceInputType.SpatialPointer)
        {
            Debug.Log("spatial pointer PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial pointer RotationData: " + inputMapping.RotationData);
        }

        if (inputMapping.InputType == DeviceInputType.SpatialGrip)
        {
            Debug.Log("spatial grip PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial grip RotationData: " + inputMapping.RotationData);
        }
    }
}
```

## <a name="see-also"></a>另请参阅

- [InputEvents](input-events.md)
- [指针](pointers.md)
- [HandTracking](hand-tracking.md)
