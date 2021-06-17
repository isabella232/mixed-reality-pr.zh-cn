---
title: 边界框和应用栏
description: 应用栏是一个对象级菜单，其中包含一系列按钮，这些按钮显示在全息影像边界的底部边缘。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality、应用栏、边界框、混合现实头戴显示设备、Windows 混合现实头戴显示设备、虚拟现实头戴显示设备、HoloLens、MRTK、混合现实工具包
ms.openlocfilehash: 5c437b303ec5462179a1ddf43687aa1653419b08
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110098"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="df09f-104">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="df09f-104">Bounding box and App bar</span></span>
<span data-ttu-id="df09f-105">![边界是混合现实中对象操作的标准接口。](images/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="df09f-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="df09f-106">什么是边界框？</span><span class="sxs-lookup"><span data-stu-id="df09f-106">What is the Bounding box?</span></span>

<span data-ttu-id="df09f-107">边界是混合现实中对象操作的标准接口。</span><span class="sxs-lookup"><span data-stu-id="df09f-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="df09f-108">此功能为用户提供一个视觉提示，指示对象当前可调整。</span><span class="sxs-lookup"><span data-stu-id="df09f-108">This feature provides the user with a visual cue that the object is currently adjustable.</span></span> <span data-ttu-id="df09f-109">在HoloLens 2，边界框适用于直接手动操作，并响应用户手指的邻近性。</span><span class="sxs-lookup"><span data-stu-id="df09f-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="df09f-110">它显示视觉反馈，帮助用户感知与对象的距离。</span><span class="sxs-lookup"><span data-stu-id="df09f-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="df09f-111">缩放对象</span><span class="sxs-lookup"><span data-stu-id="df09f-111">Scaling an object</span></span><br>
        <span data-ttu-id="df09f-112">边界框的角告知用户对象可以缩放。</span><span class="sxs-lookup"><span data-stu-id="df09f-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="df09f-113">句柄遵循广泛理解的调整缩放模式。</span><span class="sxs-lookup"><span data-stu-id="df09f-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="df09f-114">此视觉提示向用户显示对象的总区域 ， 即使它在调整模式之外不可见。</span><span class="sxs-lookup"><span data-stu-id="df09f-114">This visual cue shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="df09f-115">如果没有此功能，与另一个对象或图面对齐的对象的行为可能看起来就像周围存在不应存在的空间一样。</span><span class="sxs-lookup"><span data-stu-id="df09f-115">Without this feature, an object snapped to another object or surface may appear to behave like there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="df09f-116">*视频循环：通过边界框缩放对象*</span><span class="sxs-lookup"><span data-stu-id="df09f-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="df09f-117">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="df09f-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="df09f-118">![通过边界框缩放对象的 HoloLens 视图](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="df09f-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="df09f-119">旋转对象</span><span class="sxs-lookup"><span data-stu-id="df09f-119">Rotating an object</span></span><br>
        <span data-ttu-id="df09f-120">边界框边缘上的垂直矩形设计是旋转指示器。</span><span class="sxs-lookup"><span data-stu-id="df09f-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="df09f-121">这样，用户可以更精细地调整其放置的全息影像。</span><span class="sxs-lookup"><span data-stu-id="df09f-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="df09f-122">它们不仅可以调整和缩放，现在还可以旋转。</span><span class="sxs-lookup"><span data-stu-id="df09f-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="df09f-123">*视频循环：通过边界框旋转对象*</span><span class="sxs-lookup"><span data-stu-id="df09f-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="df09f-124">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="df09f-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="df09f-125">![通过边界框旋转对象的 HoloLens 视图](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="df09f-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="df09f-126">有关手动邻近感应的视觉HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="df09f-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="df09f-127">在HoloLens 2，有一个额外的视觉提示，可帮助用户感知深度。</span><span class="sxs-lookup"><span data-stu-id="df09f-127">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="df09f-128">当手指靠近对象时，可显示一个靠近其手指的环并缩小。</span><span class="sxs-lookup"><span data-stu-id="df09f-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="df09f-129">当达到按下状态时，环最终会聚合为点。</span><span class="sxs-lookup"><span data-stu-id="df09f-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="df09f-130">此视觉视觉视觉元素可帮助用户了解它们与对象距离有多远。</span><span class="sxs-lookup"><span data-stu-id="df09f-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="df09f-131">*视频循环：基于边界框邻近性进行视觉反馈的示例*</span><span class="sxs-lookup"><span data-stu-id="df09f-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="df09f-132">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="df09f-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="df09f-133">![有关手部邻近感应的视觉反馈](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="df09f-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="df09f-134">**有关 Unity 应用开发，请参阅混合现实 [工具包 Unity 中的边界框。](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**</span><span class="sxs-lookup"><span data-stu-id="df09f-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="df09f-135">什么是应用栏？</span><span class="sxs-lookup"><span data-stu-id="df09f-135">What is the App bar?</span></span>

<span data-ttu-id="df09f-136">应用栏是一个对象级菜单，其中包含一系列显示在全息影像边界下边缘的按钮。</span><span class="sxs-lookup"><span data-stu-id="df09f-136">The App bar is an object-level menu, which contains a series of buttons displayed on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="df09f-137">此模式通常用于让用户删除和调整全息影像。</span><span class="sxs-lookup"><span data-stu-id="df09f-137">This pattern is commonly used to let users remove and adjust holograms.</span></span> <span data-ttu-id="df09f-138">应用栏主要用于管理用户环境中放置的对象。</span><span class="sxs-lookup"><span data-stu-id="df09f-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="df09f-139">与边界框一起，用户可以完全控制混合现实中对象的面向位置和方向。</span><span class="sxs-lookup"><span data-stu-id="df09f-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="df09f-140">应用栏跟随用户</span><span class="sxs-lookup"><span data-stu-id="df09f-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="df09f-141">由于此模式与被世界锁定的对象一起使用，因此，在用户围绕对象移动时，应用栏将始终显示在离用户最近的对象端。</span><span class="sxs-lookup"><span data-stu-id="df09f-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="df09f-142">虽然从技术上来说不是广告，但此功能实际上实现了相同的结果。</span><span class="sxs-lookup"><span data-stu-id="df09f-142">While not technically billboarding, this feature effectively achieves the same result.</span></span> <span data-ttu-id="df09f-143">防止用户的位置遮挡或阻止功能，否则可从其环境中的不同位置获得这些功能。</span><span class="sxs-lookup"><span data-stu-id="df09f-143">Preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="df09f-144">*视频循环：遍历全息影像，应用栏如下所示*</span><span class="sxs-lookup"><span data-stu-id="df09f-144">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="df09f-145">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="df09f-145">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="df09f-146">![在全息影像周围移动。</span><span class="sxs-lookup"><span data-stu-id="df09f-146">![Walking around a hologram.</span></span> <span data-ttu-id="df09f-147">应用栏如下所示。](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="df09f-147">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="df09f-148">适用于 Unity 的混合现实工具包 (MRTK) 边界框</span><span class="sxs-lookup"><span data-stu-id="df09f-148">Bounding box in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="df09f-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 为边界框和应用栏提供脚本和预制。</span><span class="sxs-lookup"><span data-stu-id="df09f-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="df09f-150">可以通过将 BoundingBox.cs 脚本分配给任何对象来添加边界框。</span><span class="sxs-lookup"><span data-stu-id="df09f-150">You can add a Bounding box by assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="df09f-151">MRTK - 边界框</span><span class="sxs-lookup"><span data-stu-id="df09f-151">MRTK - Bounding Box</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


<br>

---


## <a name="see-also"></a><span data-ttu-id="df09f-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df09f-152">See also</span></span>

* [<span data-ttu-id="df09f-153">光标</span><span class="sxs-lookup"><span data-stu-id="df09f-153">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="df09f-154">手部射线</span><span class="sxs-lookup"><span data-stu-id="df09f-154">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="df09f-155">Button</span><span class="sxs-lookup"><span data-stu-id="df09f-155">Button</span></span>](button.md)
* [<span data-ttu-id="df09f-156">可交互对象</span><span class="sxs-lookup"><span data-stu-id="df09f-156">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="df09f-157">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="df09f-157">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="df09f-158">操作</span><span class="sxs-lookup"><span data-stu-id="df09f-158">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="df09f-159">手动菜单</span><span class="sxs-lookup"><span data-stu-id="df09f-159">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="df09f-160">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="df09f-160">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="df09f-161">对象集合</span><span class="sxs-lookup"><span data-stu-id="df09f-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="df09f-162">语音命令</span><span class="sxs-lookup"><span data-stu-id="df09f-162">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="df09f-163">键盘</span><span class="sxs-lookup"><span data-stu-id="df09f-163">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="df09f-164">工具提示</span><span class="sxs-lookup"><span data-stu-id="df09f-164">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="df09f-165">平板</span><span class="sxs-lookup"><span data-stu-id="df09f-165">Slate</span></span>](slate.md)
* [<span data-ttu-id="df09f-166">滑块</span><span class="sxs-lookup"><span data-stu-id="df09f-166">Slider</span></span>](slider.md)
* [<span data-ttu-id="df09f-167">着色器</span><span class="sxs-lookup"><span data-stu-id="df09f-167">Shader</span></span>](shader.md)
* [<span data-ttu-id="df09f-168">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="df09f-168">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="df09f-169">显示进度</span><span class="sxs-lookup"><span data-stu-id="df09f-169">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="df09f-170">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="df09f-170">Surface magnetism</span></span>](surface-magnetism.md)