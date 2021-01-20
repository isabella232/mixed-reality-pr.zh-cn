---
ms.openlocfilehash: 21c29b2c8d540378259200cc834f7a36065f8ab3
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581099"
---
# <a name="426"></a>[<span data-ttu-id="e5992-101">4.26</span><span class="sxs-lookup"><span data-stu-id="e5992-101">4.26</span></span>](#tab/426)

<span data-ttu-id="e5992-102">该层次结构由 `EHandKeypoint` enum 描述：</span><span class="sxs-lookup"><span data-stu-id="e5992-102">The hierarchy is described by `EHandKeypoint` enum:</span></span>

![Keypoint 蓝图选项的图像](../images/hand-keypoint-bp.png)

<span data-ttu-id="e5992-104">您可以使用 **获取运动控制器数据** 函数从用户的手获取所有这些数据。</span><span class="sxs-lookup"><span data-stu-id="e5992-104">You can get all this data from a user’s hands using the **Get Motion Controller Data** function.</span></span> <span data-ttu-id="e5992-105">该函数返回 **XRMotionControllerData** 结构。</span><span class="sxs-lookup"><span data-stu-id="e5992-105">That function returns an **XRMotionControllerData** structure.</span></span> <span data-ttu-id="e5992-106">下面是一个示例蓝图脚本，它分析 XRMotionControllerData 结构以获取现有的接点位置，并在每个接合位置绘制一个调试坐标系。</span><span class="sxs-lookup"><span data-stu-id="e5992-106">Below is a sample Blueprint script that parses the XRMotionControllerData structure to get hand joint locations and draws a debug coordinate system at each joint’s location.</span></span>

![通过信道函数连接到行跟踪的 "获取注视" 数据函数蓝图](../images/unreal-hand-tracking-img-03.png)

<span data-ttu-id="e5992-108">务必要检查该结构是否有效以及它是否为手形。</span><span class="sxs-lookup"><span data-stu-id="e5992-108">It's important to check if the structure is valid and that it's a hand.</span></span> <span data-ttu-id="e5992-109">否则，在访问位置、旋转和半径数组时，可能会获得未定义的行为。</span><span class="sxs-lookup"><span data-stu-id="e5992-109">Otherwise, you may get undefined behavior in access to positions, rotations, and radii arrays.</span></span>

# <a name="425"></a>[<span data-ttu-id="e5992-110">4.25</span><span class="sxs-lookup"><span data-stu-id="e5992-110">4.25</span></span>](#tab/425)

<span data-ttu-id="e5992-111">`EWMRHandKeypoint`枚举描述手形的骨骼层次结构。</span><span class="sxs-lookup"><span data-stu-id="e5992-111">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="e5992-112">可以在蓝图中找到每个 keypoint：</span><span class="sxs-lookup"><span data-stu-id="e5992-112">You can find each hand keypoint listed in your Blueprints:</span></span>

![手动 Keypoint 最佳实践](../images/hand-keypoint-bp.png)

<span data-ttu-id="e5992-114">完整的 c + + 枚举如下所示：</span><span class="sxs-lookup"><span data-stu-id="e5992-114">The full C++ enum is listed below:</span></span>
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

<span data-ttu-id="e5992-115">您可以在 [HandJointKind](/uwp/api/windows.perception.people.handjointkind) 表中找到每个枚举用例的数值。</span><span class="sxs-lookup"><span data-stu-id="e5992-115">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](/uwp/api/windows.perception.people.handjointkind) table.</span></span>

### <a name="supporting-hand-tracking"></a><span data-ttu-id="e5992-116">支持手动跟踪</span><span class="sxs-lookup"><span data-stu-id="e5992-116">Supporting Hand Tracking</span></span>

<span data-ttu-id="e5992-117">可以通过在 **Windows Mixed Reality > 手动** 跟踪中添加 **支持手动** 跟踪，在蓝图中使用手动跟踪：</span><span class="sxs-lookup"><span data-stu-id="e5992-117">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![手动跟踪最佳实践](../images/unreal/hand-tracking-bp.png)

<span data-ttu-id="e5992-119">`true`如果设备上是否支持手动跟踪，则此函数返回， `false` 如果手动跟踪不可用，则返回。</span><span class="sxs-lookup"><span data-stu-id="e5992-119">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking isn't available.</span></span>

![支持手动跟踪最佳实践](../images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="e5992-121">C++：</span><span class="sxs-lookup"><span data-stu-id="e5992-121">C++:</span></span>

<span data-ttu-id="e5992-122">添加 `WindowsMixedRealityHandTrackingFunctionLibrary.h`。</span><span class="sxs-lookup"><span data-stu-id="e5992-122">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="e5992-123">正在获取手动跟踪</span><span class="sxs-lookup"><span data-stu-id="e5992-123">Getting Hand Tracking</span></span>

<span data-ttu-id="e5992-124">您可以使用 **GetHandJointTransform** 从手返回空间数据。</span><span class="sxs-lookup"><span data-stu-id="e5992-124">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="e5992-125">数据将每帧更新一次，但如果在框架中，则会缓存返回值。</span><span class="sxs-lookup"><span data-stu-id="e5992-125">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="e5992-126">出于性能方面的考虑，不建议在此函数中使用繁重的逻辑。</span><span class="sxs-lookup"><span data-stu-id="e5992-126">It's not recommended to have heavy logic in this function for performance reasons.</span></span>

![获取手动联合转换](../images/unreal/get-hand-joint-transform.png)

<span data-ttu-id="e5992-128">C++：</span><span class="sxs-lookup"><span data-stu-id="e5992-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="e5992-129">下面是 GetHandJointTransform 函数参数的细目：</span><span class="sxs-lookup"><span data-stu-id="e5992-129">Here's a breakdown of GetHandJointTransform's function parameters:</span></span>

* <span data-ttu-id="e5992-130">**手型** –用户可以是向左或向右。</span><span class="sxs-lookup"><span data-stu-id="e5992-130">**Hand** – can be the users left or right hand.</span></span>
* <span data-ttu-id="e5992-131">**Keypoint** –手型的骨骼。</span><span class="sxs-lookup"><span data-stu-id="e5992-131">**Keypoint** – the bone of the hand.</span></span>
* <span data-ttu-id="e5992-132">**转换** –骨骼基的坐标和方向。</span><span class="sxs-lookup"><span data-stu-id="e5992-132">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="e5992-133">你可以请求下一个骨骼的基，以获取骨骼末尾的转换数据。</span><span class="sxs-lookup"><span data-stu-id="e5992-133">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="e5992-134">特殊的 Tip 骨骼提供 distal 的结尾。</span><span class="sxs-lookup"><span data-stu-id="e5992-134">A special Tip bone gives end of distal.</span></span>
* <span data-ttu-id="e5992-135">\* \* 半径-骨骼基的半径。</span><span class="sxs-lookup"><span data-stu-id="e5992-135">\*\*Radius—radius of the base of the bone.</span></span>
* <span data-ttu-id="e5992-136">\* \* 返回值-如果该骨骼跟踪此帧，则为 true; 如果未跟踪该骨骼，则为 false。</span><span class="sxs-lookup"><span data-stu-id="e5992-136">\*\*Return Value—true if the bone is tracked this frame, false if the bone isn't tracked.</span></span>