---
title: 输入状态
description: 有关 MRTK 中的输入状态的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， InputState，
ms.openlocfilehash: 4c1bd115c63e25decf73c082546e75b0f276a7ef
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145254"
---
# <a name="accessing-input-state-in-mrtk"></a><span data-ttu-id="3c20c-104">访问 MRTK 中的输入状态</span><span class="sxs-lookup"><span data-stu-id="3c20c-104">Accessing input state in MRTK</span></span>

<span data-ttu-id="3c20c-105">通过访问附加到输入源的控制器，可以直接查询 MRTK 中所有输入的状态。</span><span class="sxs-lookup"><span data-stu-id="3c20c-105">It's possible to directly query the state of all inputs in MRTK by iterating over the controllers attached to the input sources.</span></span> <span data-ttu-id="3c20c-106">MRTK 还提供了访问眼睛、手、头部和运动控制器的位置和旋转的便捷方法。</span><span class="sxs-lookup"><span data-stu-id="3c20c-106">MRTK also provides convenience methods for accessing the position and rotation of the eyes, hands, head, and motion controller.</span></span>

<span data-ttu-id="3c20c-107">有关通过访问控制器和使用 类查询输入的示例，请参阅 InputDataExample [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) 场景。</span><span class="sxs-lookup"><span data-stu-id="3c20c-107">See the InputDataExample scene for an example of querying input both via iterating over controllers, and by using the [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) class.</span></span>

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a><span data-ttu-id="3c20c-108">示例：MRTK 中的访问位置、头部、手、眼睛的旋转</span><span class="sxs-lookup"><span data-stu-id="3c20c-108">Example: Access position, rotation of head, hands, eyes in MRTK</span></span>

<span data-ttu-id="3c20c-109">MRTK 的 类提供了访问手部射线、头部射线、眼睛凝视射线和运动控制器射线 [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) 的便捷方法。</span><span class="sxs-lookup"><span data-stu-id="3c20c-109">MRTK's [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) class provides convenience methods for accessing the hand ray, head ray, eye gaze ray, and motion controller rays.</span></span>

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

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a><span data-ttu-id="3c20c-110">示例：访问位置，场景中所有活动 6DOF 控制器的旋转</span><span class="sxs-lookup"><span data-stu-id="3c20c-110">Example: Access position, rotation of all 6DOF controllers active in scene</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3c20c-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c20c-111">See also</span></span>

- [<span data-ttu-id="3c20c-112">InputEvents</span><span class="sxs-lookup"><span data-stu-id="3c20c-112">InputEvents</span></span>](input-events.md)
- [<span data-ttu-id="3c20c-113">指针</span><span class="sxs-lookup"><span data-stu-id="3c20c-113">Pointers</span></span>](pointers.md)
- [<span data-ttu-id="3c20c-114">HandTracking</span><span class="sxs-lookup"><span data-stu-id="3c20c-114">HandTracking</span></span>](hand-tracking.md)
