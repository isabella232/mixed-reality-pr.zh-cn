---
ms.openlocfilehash: 9fdcbdfe115fa859081c28b768f9c213ac241d13
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002648"
---
# <a name="425"></a>[<span data-ttu-id="2464a-101">4.25</span><span class="sxs-lookup"><span data-stu-id="2464a-101">4.25</span></span>](#tab/425)

<span data-ttu-id="2464a-102">`EWMRHandKeypoint`枚举描述手形的骨骼层次结构。</span><span class="sxs-lookup"><span data-stu-id="2464a-102">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="2464a-103">可以在蓝图中找到每个 keypoint：</span><span class="sxs-lookup"><span data-stu-id="2464a-103">You can find each hand keypoint listed in your Blueprints:</span></span>

![手动 Keypoint 最佳实践](../images/hand-keypoint-bp.png)

<span data-ttu-id="2464a-105">完整的 c + + 枚举如下所示：</span><span class="sxs-lookup"><span data-stu-id="2464a-105">The full C++ enum is listed below:</span></span>
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

<span data-ttu-id="2464a-106">您可以在 [HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) 表中找到每个枚举用例的数值。</span><span class="sxs-lookup"><span data-stu-id="2464a-106">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span>

### <a name="supporting-hand-tracking"></a><span data-ttu-id="2464a-107">支持手动跟踪</span><span class="sxs-lookup"><span data-stu-id="2464a-107">Supporting Hand Tracking</span></span>

<span data-ttu-id="2464a-108">可以通过在 **Windows Mixed Reality > 手动** 跟踪中添加 **支持手动** 跟踪，在蓝图中使用手动跟踪：</span><span class="sxs-lookup"><span data-stu-id="2464a-108">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![手动跟踪最佳实践](../images/unreal/hand-tracking-bp.png)

<span data-ttu-id="2464a-110">`true`如果设备上是否支持手动跟踪，则此函数返回， `false` 如果手动跟踪不可用，则返回。</span><span class="sxs-lookup"><span data-stu-id="2464a-110">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking isn't available.</span></span>

![支持手动跟踪最佳实践](../images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="2464a-112">C++：</span><span class="sxs-lookup"><span data-stu-id="2464a-112">C++:</span></span>

<span data-ttu-id="2464a-113">添加 `WindowsMixedRealityHandTrackingFunctionLibrary.h`。</span><span class="sxs-lookup"><span data-stu-id="2464a-113">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="2464a-114">正在获取手动跟踪</span><span class="sxs-lookup"><span data-stu-id="2464a-114">Getting Hand Tracking</span></span>

<span data-ttu-id="2464a-115">您可以使用 **GetHandJointTransform** 从手返回空间数据。</span><span class="sxs-lookup"><span data-stu-id="2464a-115">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="2464a-116">数据将每帧更新一次，但如果在框架中，则会缓存返回值。</span><span class="sxs-lookup"><span data-stu-id="2464a-116">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="2464a-117">出于性能方面的考虑，不建议在此函数中使用繁重的逻辑。</span><span class="sxs-lookup"><span data-stu-id="2464a-117">It's not recommended to have heavy logic in this function for performance reasons.</span></span>

![获取手动联合转换](../images/unreal/get-hand-joint-transform.png)

<span data-ttu-id="2464a-119">C++：</span><span class="sxs-lookup"><span data-stu-id="2464a-119">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="2464a-120">下面是 GetHandJointTransform 函数参数的细目：</span><span class="sxs-lookup"><span data-stu-id="2464a-120">Here's a breakdown of GetHandJointTransform's function parameters:</span></span>

* <span data-ttu-id="2464a-121">**手型** –用户可以是向左或向右。</span><span class="sxs-lookup"><span data-stu-id="2464a-121">**Hand** – can be the users left or right hand.</span></span>
* <span data-ttu-id="2464a-122">**Keypoint** –手型的骨骼。</span><span class="sxs-lookup"><span data-stu-id="2464a-122">**Keypoint** – the bone of the hand.</span></span>
* <span data-ttu-id="2464a-123">**转换** –骨骼基的坐标和方向。</span><span class="sxs-lookup"><span data-stu-id="2464a-123">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="2464a-124">你可以请求下一个骨骼的基，以获取骨骼末尾的转换数据。</span><span class="sxs-lookup"><span data-stu-id="2464a-124">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="2464a-125">特殊的 Tip 骨骼提供 distal 的结尾。</span><span class="sxs-lookup"><span data-stu-id="2464a-125">A special Tip bone gives end of distal.</span></span>
* <span data-ttu-id="2464a-126">\* \* 半径-骨骼基的半径。</span><span class="sxs-lookup"><span data-stu-id="2464a-126">\*\*Radius—radius of the base of the bone.</span></span>
* <span data-ttu-id="2464a-127">\* \* 返回值-如果该骨骼跟踪此帧，则为 true; 如果未跟踪该骨骼，则为 false。</span><span class="sxs-lookup"><span data-stu-id="2464a-127">\*\*Return Value—true if the bone is tracked this frame, false if the bone isn't tracked.</span></span>


# <a name="426"></a>[<span data-ttu-id="2464a-128">4.26</span><span class="sxs-lookup"><span data-stu-id="2464a-128">4.26</span></span>](#tab/426)

<span data-ttu-id="2464a-129">该层次结构由 `EHandKeypoint` enum 描述：</span><span class="sxs-lookup"><span data-stu-id="2464a-129">The hierarchy is described by `EHandKeypoint` enum:</span></span>

![Keypoint 蓝图选项的图像](../images/hand-keypoint-bp.png)

<span data-ttu-id="2464a-131">您可以使用 **获取运动控制器数据** 函数从用户的手获取所有这些数据。</span><span class="sxs-lookup"><span data-stu-id="2464a-131">You can get all this data from a user’s hands using the **Get Motion Controller Data** function.</span></span> <span data-ttu-id="2464a-132">该函数返回 **XRMotionControllerData** 结构。</span><span class="sxs-lookup"><span data-stu-id="2464a-132">That function returns an **XRMotionControllerData** structure.</span></span> <span data-ttu-id="2464a-133">下面是一个示例蓝图脚本，它分析 XRMotionControllerData 结构以获取现有的接点位置，并在每个接合位置绘制一个调试坐标系。</span><span class="sxs-lookup"><span data-stu-id="2464a-133">Below is a sample Blueprint script that parses the XRMotionControllerData structure to get hand joint locations and draws a debug coordinate system at each joint’s location.</span></span>

![通过信道函数连接到行跟踪的 "获取注视" 数据函数蓝图](../images/unreal-hand-tracking-img-03.png)

<span data-ttu-id="2464a-135">务必要检查该结构是否有效以及它是否为手形。</span><span class="sxs-lookup"><span data-stu-id="2464a-135">It's important to check if the structure is valid and that it's a hand.</span></span> <span data-ttu-id="2464a-136">否则，在访问位置、旋转和半径数组时，可能会获得未定义的行为。</span><span class="sxs-lookup"><span data-stu-id="2464a-136">Otherwise, you may get undefined behavior in access to positions, rotations, and radii arrays.</span></span>
