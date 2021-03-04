---
title: Unity 中的凝视
description: 了解如何使用 "注视输入" 作为主要方式，使用户能够面向混合现实中的应用创建的全息影像。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 眼睛，眼睛，头盔，unity，全息影像，混合现实，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，MRTK，混合现实工具包
ms.openlocfilehash: 7602eb27da19dc77e4eab1c1a428dc9a1cf8b252
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759683"
---
# <a name="head-gaze-in-unity"></a>头-注视 Unity

[注视](../../design/gaze-and-commit.md)是用户在[混合现实](../../discover/mixed-reality.md)中以[影像](../../discover/hologram.md)为目标的主要方式。

## <a name="implementing-head-gaze"></a>实现机头

从概念上讲，您通过从用户的耳机中向前投影一条射线 [来确定其](../../design/gaze-and-commit.md) 点击情况。 在 Unity 中，用户的头位置和方向通过 [相机](camera-in-unity.md)公开，特别是 [UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform](https://docs.unity3d.com/ScriptReference/Transform-forward.html) 和 [UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[转换。位置](https://docs.unity3d.com/ScriptReference/Transform-position.html)。

调用 [RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 可提供一个 [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) ，其中包含有关冲突的信息，其中包括3d 冲突点，以及打印头看点的另一 GameObject。

### <a name="example-implement-head-gaze"></a>示例：实现机头

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

### <a name="best-practices"></a>最佳做法

尽管上面的示例从更新循环中触发了单个 raycast 以查找用户头所在的目标，但我们建议使用单个对象来管理所有的头节点。 将您的头看起来的逻辑结合起来可节省您的应用程序的宝贵处理能力，并将 raycasting 限制为每帧一次。

## <a name="visualizing-head-gaze"></a>形象注视

就像在计算机上使用鼠标指针一样，你应该实现表示用户头看的 [光标](../../design/cursors.md) 。 了解用户的目标内容会对要与之交互的内容增加信心。

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>打印头-注视混合现实工具包 
可以通过 MRTK 中的 [输入管理器](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md) 访问 head。

## <a name="next-development-checkpoint"></a>下一个开发检查点

如果遵循我们所说的 Unity 开发旅程，就是在浏览 MRTK 核心构建基块。 从这里，你可以继续了解下一部分基础知识：

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
