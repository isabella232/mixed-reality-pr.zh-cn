---
title: Unity 中的凝视
description: 了解如何使用 "注视输入" 作为主要方式，使用户能够面向混合现实中的应用创建的全息影像。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 眼睛，眼睛，头盔，unity，全息影像，混合现实，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机，MRTK，混合现实工具包
ms.openlocfilehash: 98eb4445d04b236dea74917d9c51108b66d6df3b
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300362"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="376d8-104">头-注视 Unity</span><span class="sxs-lookup"><span data-stu-id="376d8-104">Head-gaze in Unity</span></span>

<span data-ttu-id="376d8-105">[注视](../../design/gaze-and-commit.md)是用户在[混合现实](../../discover/mixed-reality.md)中以[影像](../../discover/hologram.md)为目标的主要方式。</span><span class="sxs-lookup"><span data-stu-id="376d8-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="376d8-106">实现机头</span><span class="sxs-lookup"><span data-stu-id="376d8-106">Implementing head-gaze</span></span>

<span data-ttu-id="376d8-107">从概念上讲，您通过从用户的耳机中向前投影一条射线 [来确定其](../../design/gaze-and-commit.md) 点击情况。</span><span class="sxs-lookup"><span data-stu-id="376d8-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="376d8-108">在 Unity 中，用户的头位置和方向通过 [相机](camera-in-unity.md)公开，特别是 [UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform](https://docs.unity3d.com/ScriptReference/Transform-forward.html) 和 [UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[转换。位置](https://docs.unity3d.com/ScriptReference/Transform-position.html)。</span><span class="sxs-lookup"><span data-stu-id="376d8-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="376d8-109">调用 [RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 可提供一个 [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) ，其中包含有关冲突的信息，其中包括3d 冲突点，以及打印头看点的另一 GameObject。</span><span class="sxs-lookup"><span data-stu-id="376d8-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="376d8-110">示例：实现机头</span><span class="sxs-lookup"><span data-stu-id="376d8-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="376d8-111">最佳做法</span><span class="sxs-lookup"><span data-stu-id="376d8-111">Best practices</span></span>

<span data-ttu-id="376d8-112">尽管上面的示例从更新循环中触发了单个 raycast 以查找用户头所在的目标，但我们建议使用单个对象来管理所有的头节点。</span><span class="sxs-lookup"><span data-stu-id="376d8-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="376d8-113">将您的头看起来的逻辑结合起来可节省您的应用程序的宝贵处理能力，并将 raycasting 限制为每帧一次。</span><span class="sxs-lookup"><span data-stu-id="376d8-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="376d8-114">形象注视</span><span class="sxs-lookup"><span data-stu-id="376d8-114">Visualizing head-gaze</span></span>

<span data-ttu-id="376d8-115">就像在计算机上使用鼠标指针一样，你应该实现表示用户头看的 [光标](../../design/cursors.md) 。</span><span class="sxs-lookup"><span data-stu-id="376d8-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="376d8-116">了解用户的目标内容会对要与之交互的内容增加信心。</span><span class="sxs-lookup"><span data-stu-id="376d8-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="376d8-117">打印头-注视混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="376d8-117">Head-gaze in the Mixed Reality Toolkit</span></span>

<span data-ttu-id="376d8-118">可以通过 MRTK 中的 [输入管理器](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/overview) 访问 head。</span><span class="sxs-lookup"><span data-stu-id="376d8-118">You can access head-gaze from the [Input Manager](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/overview) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="376d8-119">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="376d8-119">Next Development Checkpoint</span></span>

<span data-ttu-id="376d8-120">如果遵循我们所说的 Unity 开发旅程，就是在浏览 MRTK 核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="376d8-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="376d8-121">从这里，你可以继续了解下一部分基础知识：</span><span class="sxs-lookup"><span data-stu-id="376d8-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="376d8-122">运动控制器</span><span class="sxs-lookup"><span data-stu-id="376d8-122">Motion controllers</span></span>](motion-controllers-in-unity.md)

<span data-ttu-id="376d8-123">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="376d8-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="376d8-124">共享体验</span><span class="sxs-lookup"><span data-stu-id="376d8-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="376d8-125">你可以随时返回到 [Unity 开发检查点](unity-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="376d8-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="376d8-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="376d8-126">See also</span></span>
* [<span data-ttu-id="376d8-127">摄像头</span><span class="sxs-lookup"><span data-stu-id="376d8-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="376d8-128">游标</span><span class="sxs-lookup"><span data-stu-id="376d8-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="376d8-129">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="376d8-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
