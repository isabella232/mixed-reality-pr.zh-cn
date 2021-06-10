---
title: Unity 中的凝视
description: 了解如何将凝视输入用作用户以混合现实中应用创建的全息影像为目标的主要方式。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 眼睛凝视， 头部凝视， unity， 全息影像， 混合现实， 混合现实头戴显示设备， Windows 混合现实头戴显示设备， 虚拟现实头戴显示设备， MRTK， 混合现实工具包
ms.openlocfilehash: f10079d36f737e5d8a2ee74a88ca0f8b2b3d791c
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600146"
---
# <a name="head-gaze-in-unity"></a>Unity 中的头部凝视

[凝](../../design/gaze-and-commit.md)视是用户定位应用在混合现实[](../../discover/hologram.md)中创建的全息[影像的主要方式](../../discover/mixed-reality.md)。

## <a name="implementing-head-gaze"></a>实现头部凝视

从概念上讲 [，通过](../../design/gaze-and-commit.md) 从用户的头戴显示设备向前预测射线来查看其命中次数来确定头部凝视。 在 Unity 中，用户的头部位置和方向通过 [相机](camera-in-unity.md)（特别是 [UnityEngine.Camera.main）公开](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) 和 [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html)。

调用 [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 可为你提供一个 [RaycastHit，](https://docs.unity3d.com/ScriptReference/RaycastHit.html) 其中包含有关碰撞的信息，包括 3D 碰撞点和其他 GameObject 头部凝视射线命中。

### <a name="example-implement-head-gaze"></a>示例：实现头部凝视

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a>最佳实践

虽然上面的示例从更新循环触发单个光线广播来查找用户头部的目标，但建议使用单个对象来管理所有头部凝视过程。 组合头部凝视逻辑可节省应用宝贵的处理能力，将光线广播限制为每个帧一个。

## <a name="visualizing-head-gaze"></a>可视化头部凝视

就像在计算机上使用鼠标指针一样，应 [实现表示用户](../../design/cursors.md) 头部凝视的光标。 了解用户所面向的内容可增强用户对要与之交互的内容的置信度。

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>混合现实工具包中的头部凝视

可以从 MRTK 中的 [输入管理器访问](/windows/mixed-reality/mrtk-unity/features/input/overview) 头部凝视。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果你遵循我们布局的 Unity 开发旅程，则你正在探索 MRTK 核心构建基块。 从这里，你可以继续了解下一部分基础知识：

> [!div class="nextstepaction"]
> [运动控制器](motion-controllers-in-unity.md)

或跳转到混合现实平台功能和 API：

> [!div class="nextstepaction"]
> [共享体验](shared-experiences-in-unity.md)

你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。

## <a name="see-also"></a>另请参阅
* [摄像头](camera-in-unity.md)
* [游标](../../design/cursors.md)
* [头部凝视并提交](../../design/gaze-and-commit.md)