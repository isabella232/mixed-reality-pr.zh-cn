---
title: 凝视
description: MRTK 中 Docummentation 的类型
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，注视，
ms.openlocfilehash: a9d97ef73a7014a46001cbd42281c5ab28f6cf425dfd7605ce5b3c8c7fc45198
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208426"
---
# <a name="gaze"></a>凝视

"[注视](/windows/mixed-reality/gaze)" 是一种输入，它基于用户的查找位置与世界交互。 注视两种不同的风格

## <a name="head-gaze"></a>头部凝视

这种看起来取决于头/相机正在查看的方向。 在不支持眼睛的系统上，或在硬件可能支持目视，但没有执行正确的 [权限集和设置](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) 的情况下，眼睛处于活动状态。

打印头通常与 HoloLens 1 样式交互相关，这种交互涉及到对象，方法是将其放在全息帧的中心，然后执行 "air" 手势。

## <a name="eye-gaze"></a>眼睛凝视

这种注视基于用户的眼睛所在的位置。 眼睛仅出现在支持目视跟踪的系统上。 有关如何使用眼睛的详细信息，请参阅 [目视跟踪文档](eye-tracking/eye-tracking-main.md) 。

## <a name="gazeprovider"></a>GazeProvider

) 眼睛良好的功能 (由 [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider)提供。 可在输入系统配置文件的 " *指针* " 部分中配置此提供程序：

![注视配置入口点](../images/input/GazeConfigurationEntrypoint.png)

与其他输入源一样，注视提供程序通过使用指针与场景中的对象进行交互 [ (参见此文档，了解有关指针) 的信息 ](../../architecture/controllers-pointers-and-focus.md)。
对于注视提供程序，其指针是通过实现的， `InternalGazePointer` 并且不是通过配置文件配置的。

可以通过将 " *注视" 提供程序类型* 更改为引用实现 [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) 和 [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider)的不同类，将 "股票 GazeProvider" 替换为备用实现。
通常情况下，建议使用 stock GazeProvider (并在查找) bug 时在中归档问题，因为重新实现 GazeProvider 是不重要的。

### <a name="alternative-platform-provided-gaze-poses"></a>替代平台提供的注视

默认情况下，MRTK GazeProvider 使用摄像机帧的中心作为注视原点。 某些平台（如 HoloLens 2 上的 Windows Mixed Reality）提供了另一种定义的注视姿势。 这是通过 "注视" 设置中的设置来管理的 `Use Head Gaze Override` 。 启用后，将使用备用的注视替代。 禁用后，将使用默认的框架中心原点。 具体而言，对于 HoloLens 2，将会产生几度的外观，以使用户在使用其目标头时感到舒适。

## <a name="usage"></a>使用情况

### <a name="how-get-the-current-gaze-target"></a>如何获取当前注视目标

此示例演示如何获取用户注视的目标当前游戏对象。

```c#
void LogCurrentGazeTarget()
{
    if (CoreServices.InputSystem.GazeProvider.GazeTarget)
    {
        Debug.Log("User gaze is currently over game object: "
            + CoreServices.InputSystem.GazeProvider.GazeTarget)
    }
}
```

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a>如何获取当前注视方向和原点

此示例演示如何获取 System.numerics.vector2，以表示用户注视的方向，并 (方向) 方向。

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
