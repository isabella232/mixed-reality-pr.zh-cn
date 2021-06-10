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
# <a name="head-gaze-in-unity"></a><span data-ttu-id="9bb8b-104">Unity 中的头部凝视</span><span class="sxs-lookup"><span data-stu-id="9bb8b-104">Head-gaze in Unity</span></span>

<span data-ttu-id="9bb8b-105">[凝](../../design/gaze-and-commit.md)视是用户定位应用在混合现实[](../../discover/hologram.md)中创建的全息[影像的主要方式](../../discover/mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="9bb8b-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="9bb8b-106">实现头部凝视</span><span class="sxs-lookup"><span data-stu-id="9bb8b-106">Implementing head-gaze</span></span>

<span data-ttu-id="9bb8b-107">从概念上讲 [，通过](../../design/gaze-and-commit.md) 从用户的头戴显示设备向前预测射线来查看其命中次数来确定头部凝视。</span><span class="sxs-lookup"><span data-stu-id="9bb8b-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="9bb8b-108">在 Unity 中，用户的头部位置和方向通过 [相机](camera-in-unity.md)（特别是 [UnityEngine.Camera.main）公开](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) 和 [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html)。</span><span class="sxs-lookup"><span data-stu-id="9bb8b-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="9bb8b-109">调用 [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 可为你提供一个 [RaycastHit，](https://docs.unity3d.com/ScriptReference/RaycastHit.html) 其中包含有关碰撞的信息，包括 3D 碰撞点和其他 GameObject 头部凝视射线命中。</span><span class="sxs-lookup"><span data-stu-id="9bb8b-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="9bb8b-110">示例：实现头部凝视</span><span class="sxs-lookup"><span data-stu-id="9bb8b-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="9bb8b-111">最佳实践</span><span class="sxs-lookup"><span data-stu-id="9bb8b-111">Best practices</span></span>

<span data-ttu-id="9bb8b-112">虽然上面的示例从更新循环触发单个光线广播来查找用户头部的目标，但建议使用单个对象来管理所有头部凝视过程。</span><span class="sxs-lookup"><span data-stu-id="9bb8b-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="9bb8b-113">组合头部凝视逻辑可节省应用宝贵的处理能力，将光线广播限制为每个帧一个。</span><span class="sxs-lookup"><span data-stu-id="9bb8b-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="9bb8b-114">可视化头部凝视</span><span class="sxs-lookup"><span data-stu-id="9bb8b-114">Visualizing head-gaze</span></span>

<span data-ttu-id="9bb8b-115">就像在计算机上使用鼠标指针一样，应 [实现表示用户](../../design/cursors.md) 头部凝视的光标。</span><span class="sxs-lookup"><span data-stu-id="9bb8b-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="9bb8b-116">了解用户所面向的内容可增强用户对要与之交互的内容的置信度。</span><span class="sxs-lookup"><span data-stu-id="9bb8b-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="9bb8b-117">混合现实工具包中的头部凝视</span><span class="sxs-lookup"><span data-stu-id="9bb8b-117">Head-gaze in the Mixed Reality Toolkit</span></span>

<span data-ttu-id="9bb8b-118">可以从 MRTK 中的 [输入管理器访问](/windows/mixed-reality/mrtk-unity/features/input/overview) 头部凝视。</span><span class="sxs-lookup"><span data-stu-id="9bb8b-118">You can access head-gaze from the [Input Manager](/windows/mixed-reality/mrtk-unity/features/input/overview) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="9bb8b-119">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="9bb8b-119">Next Development Checkpoint</span></span>

<span data-ttu-id="9bb8b-120">如果你遵循我们布局的 Unity 开发旅程，则你正在探索 MRTK 核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="9bb8b-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="9bb8b-121">从这里，你可以继续了解下一部分基础知识：</span><span class="sxs-lookup"><span data-stu-id="9bb8b-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9bb8b-122">运动控制器</span><span class="sxs-lookup"><span data-stu-id="9bb8b-122">Motion controllers</span></span>](motion-controllers-in-unity.md)

<span data-ttu-id="9bb8b-123">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="9bb8b-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9bb8b-124">共享体验</span><span class="sxs-lookup"><span data-stu-id="9bb8b-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="9bb8b-125">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="9bb8b-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="9bb8b-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9bb8b-126">See also</span></span>
* [<span data-ttu-id="9bb8b-127">摄像头</span><span class="sxs-lookup"><span data-stu-id="9bb8b-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="9bb8b-128">游标</span><span class="sxs-lookup"><span data-stu-id="9bb8b-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="9bb8b-129">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="9bb8b-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)