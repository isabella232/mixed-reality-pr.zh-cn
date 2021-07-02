---
title: 凝视
description: MRTK 中 Docummentation 的类型
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，注视，
ms.openlocfilehash: 95dad85ca8154d35f73906b53019d3a52ced546f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176912"
---
# <a name="gaze"></a><span data-ttu-id="9c022-104">凝视</span><span class="sxs-lookup"><span data-stu-id="9c022-104">Gaze</span></span>

<span data-ttu-id="9c022-105">"[注视](/windows/mixed-reality/gaze)" 是一种输入，它基于用户的查找位置与世界交互。</span><span class="sxs-lookup"><span data-stu-id="9c022-105">[Gaze](/windows/mixed-reality/gaze) is a form of input that interacts with the world based on where the user is looking.</span></span> <span data-ttu-id="9c022-106">注视两种不同的风格</span><span class="sxs-lookup"><span data-stu-id="9c022-106">Gaze exists in two different flavors</span></span>

## <a name="head-gaze"></a><span data-ttu-id="9c022-107">头部凝视</span><span class="sxs-lookup"><span data-stu-id="9c022-107">Head gaze</span></span>

<span data-ttu-id="9c022-108">这种看起来取决于头/相机正在查看的方向。</span><span class="sxs-lookup"><span data-stu-id="9c022-108">This type of gaze is based on the direction that the head/camera is looking at.</span></span> <span data-ttu-id="9c022-109">在不支持眼睛的系统上，或在硬件可能支持目视，但没有执行正确的 [权限集和设置](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) 的情况下，眼睛处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="9c022-109">Head gaze is active on systems that don't support eye gaze, or in cases where the hardware may support eye gaze, but the right set of [permissions and setup](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) has not been performed.</span></span>

<span data-ttu-id="9c022-110">打印头通常与 HoloLens 1 样式交互相关，这种交互涉及到对象，方法是将其放在全息帧的中心，然后执行 "air" 手势。</span><span class="sxs-lookup"><span data-stu-id="9c022-110">Head gaze is usually associated with HoloLens 1 style interactions involving looking at object by placing it in the center of the Holographic Frame and then performing the air tap gesture.</span></span>

## <a name="eye-gaze"></a><span data-ttu-id="9c022-111">眼睛凝视</span><span class="sxs-lookup"><span data-stu-id="9c022-111">Eye gaze</span></span>

<span data-ttu-id="9c022-112">这种注视基于用户的眼睛所在的位置。</span><span class="sxs-lookup"><span data-stu-id="9c022-112">This type of gaze is based on where the user's eyes are looking.</span></span> <span data-ttu-id="9c022-113">眼睛仅出现在支持目视跟踪的系统上。</span><span class="sxs-lookup"><span data-stu-id="9c022-113">Eye gaze is only present on systems that support eye tracking.</span></span> <span data-ttu-id="9c022-114">有关如何使用眼睛的详细信息，请参阅 [目视跟踪文档](eye-tracking/eye-tracking-main.md) 。</span><span class="sxs-lookup"><span data-stu-id="9c022-114">See the [eye tracking documentation](eye-tracking/eye-tracking-main.md) for more details on how to use eye gaze.</span></span>

## <a name="gazeprovider"></a><span data-ttu-id="9c022-115">GazeProvider</span><span class="sxs-lookup"><span data-stu-id="9c022-115">GazeProvider</span></span>

<span data-ttu-id="9c022-116">) 眼睛良好的功能 (由 [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider)提供。</span><span class="sxs-lookup"><span data-stu-id="9c022-116">Gaze functionality (both head and eye) is provided by the [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider).</span></span> <span data-ttu-id="9c022-117">可在输入系统配置文件的 " *指针* " 部分中配置此提供程序：</span><span class="sxs-lookup"><span data-stu-id="9c022-117">This provider can be configured in the *Pointer* section of the input system profile:</span></span>

![注视配置入口点](../images/input/GazeConfigurationEntrypoint.png)

<span data-ttu-id="9c022-119">与其他输入源一样，注视提供程序通过使用指针与场景中的对象进行交互 [ (参见此文档，了解有关指针) 的信息 ](../../architecture/controllers-pointers-and-focus.md)。</span><span class="sxs-lookup"><span data-stu-id="9c022-119">Like other sources of input, the gaze provider interacts with objects in the scene through use of a pointer [(see this document for information on pointers)](../../architecture/controllers-pointers-and-focus.md).</span></span>
<span data-ttu-id="9c022-120">对于注视提供程序，其指针是通过实现的， `InternalGazePointer` 并且不是通过配置文件配置的。</span><span class="sxs-lookup"><span data-stu-id="9c022-120">In the case of the gaze provider, its pointer is implemented via `InternalGazePointer` and is not configured through a profile.</span></span>

<span data-ttu-id="9c022-121">可以通过将 " *注视" 提供程序类型* 更改为引用实现 [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) 和 [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider)的不同类，将 "股票 GazeProvider" 替换为备用实现。</span><span class="sxs-lookup"><span data-stu-id="9c022-121">It is possible to replace the stock GazeProvider with an alternate implementation by changing *Gaze Provider Type* to reference a different class that implements [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) and [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).</span></span>
<span data-ttu-id="9c022-122">通常情况下，建议使用 stock GazeProvider (并在查找) bug 时在中归档问题，因为重新实现 GazeProvider 是不重要的。</span><span class="sxs-lookup"><span data-stu-id="9c022-122">It's generally recommended to use the stock GazeProvider (and filing issues in when finding bugs) as re-implementing the GazeProvider is non-trivial.</span></span>

### <a name="alternative-platform-provided-gaze-poses"></a><span data-ttu-id="9c022-123">替代平台提供的注视</span><span class="sxs-lookup"><span data-stu-id="9c022-123">Alternative platform-provided gaze poses</span></span>

<span data-ttu-id="9c022-124">默认情况下，MRTK GazeProvider 使用摄像机帧的中心作为注视原点。</span><span class="sxs-lookup"><span data-stu-id="9c022-124">By default, the MRTK GazeProvider uses the center of the camera's frame as the gaze origin.</span></span> <span data-ttu-id="9c022-125">某些平台（如 HoloLens 2 上的 Windows Mixed Reality）提供了另一种定义的注视姿势。</span><span class="sxs-lookup"><span data-stu-id="9c022-125">Some platforms, like Windows Mixed Reality on HoloLens 2, provide an alternatively defined gaze pose.</span></span> <span data-ttu-id="9c022-126">这是通过 "注视" 设置中的设置来管理的 `Use Head Gaze Override` 。</span><span class="sxs-lookup"><span data-stu-id="9c022-126">This is managed via the `Use Head Gaze Override` setting in the gaze settings.</span></span> <span data-ttu-id="9c022-127">启用后，将使用备用的注视替代。</span><span class="sxs-lookup"><span data-stu-id="9c022-127">When enabled, the alternative gaze override will be used.</span></span> <span data-ttu-id="9c022-128">禁用后，将使用默认的框架中心原点。</span><span class="sxs-lookup"><span data-stu-id="9c022-128">When disabled, the default frame center origin will be used.</span></span> <span data-ttu-id="9c022-129">具体而言，对于 HoloLens 2，将会产生几度的外观，以使用户在使用其目标头时感到舒适。</span><span class="sxs-lookup"><span data-stu-id="9c022-129">Specifically, for HoloLens 2, the gaze angle will be raised several degrees to account for user comfort in using their head for targeting.</span></span>

## <a name="usage"></a><span data-ttu-id="9c022-130">使用情况</span><span class="sxs-lookup"><span data-stu-id="9c022-130">Usage</span></span>

### <a name="how-get-the-current-gaze-target"></a><span data-ttu-id="9c022-131">如何获取当前注视目标</span><span class="sxs-lookup"><span data-stu-id="9c022-131">How get the current gaze target</span></span>

<span data-ttu-id="9c022-132">此示例演示如何获取用户注视的目标当前游戏对象。</span><span class="sxs-lookup"><span data-stu-id="9c022-132">This sample shows how to get the current game object that is targeted by the user gaze.</span></span>

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

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a><span data-ttu-id="9c022-133">如何获取当前注视方向和原点</span><span class="sxs-lookup"><span data-stu-id="9c022-133">How to get the current gaze direction and origin</span></span>

<span data-ttu-id="9c022-134">此示例演示如何获取 System.numerics.vector2，以表示用户注视的方向，并 (方向) 方向。</span><span class="sxs-lookup"><span data-stu-id="9c022-134">This sample shows how to get the Vector3 representing the direction of the user gaze and the origin (the point from which the direction is going).</span></span>

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
