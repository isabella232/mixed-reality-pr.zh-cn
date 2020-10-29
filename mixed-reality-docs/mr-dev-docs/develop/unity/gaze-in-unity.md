---
title: Unity 中的凝视
description: 注视是用户在混合现实中以应用程序创建的方式为目标的主要方式。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 眼睛、头盔、unity、全息图、混合现实
ms.openlocfilehash: 8c1a6cb0847cd0e6e776c6d4e1f7c1efdc126279
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677307"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="0134e-104">头-注视 Unity</span><span class="sxs-lookup"><span data-stu-id="0134e-104">Head-gaze in Unity</span></span>

<span data-ttu-id="0134e-105">[注视](../../design/gaze-and-commit.md)是用户在[混合现实](../../discover/mixed-reality.md)中以应用程序[创建的方式](../../discover/hologram.md)为目标的主要方式。</span><span class="sxs-lookup"><span data-stu-id="0134e-105">[Gaze](../../design/gaze-and-commit.md) is a primary way for users to target the [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="0134e-106">实现机头</span><span class="sxs-lookup"><span data-stu-id="0134e-106">Implementing head-gaze</span></span>

<span data-ttu-id="0134e-107">从概念上讲， [打印头](../../design/gaze-and-commit.md) 的实现方式是从用户的头投影一条射线，其中的耳机是正面朝上，并确定与该射线发生冲突的内容。</span><span class="sxs-lookup"><span data-stu-id="0134e-107">Conceptually, [head-gaze](../../design/gaze-and-commit.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span>
<span data-ttu-id="0134e-108">在 Unity 中，用户的头位置和方向通过 Unity 主 [摄像机](camera-in-unity.md)公开，特别是 [UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform](https://docs.unity3d.com/ScriptReference/Transform-forward.html) 和 [UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[转换。位置](https://docs.unity3d.com/ScriptReference/Transform-position.html)。</span><span class="sxs-lookup"><span data-stu-id="0134e-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="0134e-109">如果调用 [RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) ，则会生成一个 [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) 结构，其中包含有关冲突的信息，其中包括发生冲突的三维点，以及使用的另一 GameObject。</span><span class="sxs-lookup"><span data-stu-id="0134e-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="0134e-110">示例：实现机头</span><span class="sxs-lookup"><span data-stu-id="0134e-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="0134e-111">最佳实践</span><span class="sxs-lookup"><span data-stu-id="0134e-111">Best practices</span></span>

<span data-ttu-id="0134e-112">尽管上面的示例演示了如何在更新循环中执行单个 raycast 来查找用户头所在的目标，但建议在管理打印头的单个对象中执行此操作，而不是在可能对要 gazed 的对象感兴趣的任何对象中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="0134e-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="0134e-113">这样，你的应用程序就可以通过只对每个帧执行一个 raycast 的操作来保存处理。</span><span class="sxs-lookup"><span data-stu-id="0134e-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="0134e-114">形象注视</span><span class="sxs-lookup"><span data-stu-id="0134e-114">Visualizing head-gaze</span></span>

<span data-ttu-id="0134e-115">就像在使用鼠标指针来定位内容并与内容交互的桌面上，你应该实现表示用户头看的 [光标](../../design/cursors.md) 。</span><span class="sxs-lookup"><span data-stu-id="0134e-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="0134e-116">这为用户提供了与交互相关的置信度。</span><span class="sxs-lookup"><span data-stu-id="0134e-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="0134e-117">标题-注视混合现实工具包 v2</span><span class="sxs-lookup"><span data-stu-id="0134e-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="0134e-118">可以从 MRTK v2 中的 [输入管理器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) 访问 head。</span><span class="sxs-lookup"><span data-stu-id="0134e-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="0134e-119">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="0134e-119">Next Development Checkpoint</span></span>

<span data-ttu-id="0134e-120">如果遵循我们所说的 Unity 开发检查点旅程，就是在浏览 MRTK 核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="0134e-120">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="0134e-121">在这里，你可以继续执行下一个构建基块：</span><span class="sxs-lookup"><span data-stu-id="0134e-121">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0134e-122">手势和运动控制器</span><span class="sxs-lookup"><span data-stu-id="0134e-122">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)

<span data-ttu-id="0134e-123">或跳转到混合现实平台功能和 Api：</span><span class="sxs-lookup"><span data-stu-id="0134e-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0134e-124">共享体验</span><span class="sxs-lookup"><span data-stu-id="0134e-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="0134e-125">随时可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks) 。</span><span class="sxs-lookup"><span data-stu-id="0134e-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="0134e-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="0134e-126">See also</span></span>
* [<span data-ttu-id="0134e-127">摄像头</span><span class="sxs-lookup"><span data-stu-id="0134e-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="0134e-128">游标</span><span class="sxs-lookup"><span data-stu-id="0134e-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="0134e-129">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="0134e-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
