---
title: Unity 中的焦点
description: 了解如何通过设置 HoloLens 和 Windows Mixed Reality 沉浸式耳机，手动优化 Unity 中的全息影像稳定性。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，焦点，焦点平面，稳定平面，稳定点，reprojection，LSR，深度缓冲区，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: 16f359e1742b86c5f12c0c5965ac9e818ea76aee
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636219"
---
# <a name="focus-point-in-unity"></a>Unity 中的焦点

**命名空间：** *UnityEngine. XR*<br>
**类型**： *HolographicSettings*

使用 [焦点](../platform-capabilities-and-apis/hologram-stability.md#reprojection) 向 HoloLens 提供有关如何最好地使当前正在显示的全息影像稳定的提示。

如果要在 Unity 中设置焦点，则需要使用 *HolographicSettings. SetFocusPointForFrame ()* 设置每个框架。 如果未为帧设置焦点，则使用默认的稳定平面。

> [!NOTE]
> 默认情况下，新的 Unity 项目设置了 "启用深度缓冲共享" 选项。  使用此选项时，在沉浸式桌面耳机上运行的 Unity 应用或运行 Windows 10 4 月2018更新 (RS4) 或更高版本的应用程序将向 Windows 提交深度缓冲区以自动优化全息影像稳定性，无需应用指定焦点：
> * 在沉浸式桌面耳机上，这将启用基于像素深度的 reprojection。
> * 在运行 Windows 10 4 月2018更新或更高版本的 HoloLens 上，这将分析深度缓冲区以自动选择最佳的稳定平面。
>
> 这两种方法都应该提供更好的图像质量，而无需由您的应用程序显式工作，从而为每个帧选择焦点。  请注意，如果你确实手动提供了焦点，这将替代上述自动行为，并且通常会降低全息图的稳定性。  通常，仅当你的应用在尚未更新到 Windows 10 4 2018 月版更新的 HoloLens 上运行时，才应指定手动焦点点。

### <a name="example"></a>示例

有多种方法可设置焦点，如 *SetFocusPointForFrame* 静态函数上的可用重载所建议的那样。 下面提供了一个简单的示例，可将焦点平面设置为每个帧的提供的对象：

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to
    // the normal of the plane and ensure the user does not pass through the
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

> [!NOTE]
> 如果焦点对象最终出现在用户后面，则上述简单代码可以减少全息图的稳定性。 我们通常建议设置 " **[启用深度缓冲区共享"，](camera-in-unity.md#sharing-depth-buffers)** 而不是手动指定焦点。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所说的 Unity 开发旅程，就是探索混合现实平台功能和 Api。 从这里，你可以继续了解下一个主题：

> [!div class="nextstepaction"]
> [失跟](tracking-loss-in-unity.md)

或直接跳到在设备或模拟器上部署应用：

> [!div class="nextstepaction"]
> [部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳机](../platform-capabilities-and-apis/using-visual-studio.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#3-advanced-features)。

### <a name="see-also"></a>另请参阅

* [稳定平面](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
