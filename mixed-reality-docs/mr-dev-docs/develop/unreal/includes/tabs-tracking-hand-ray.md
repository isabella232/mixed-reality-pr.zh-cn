---
ms.openlocfilehash: 23bba22801f61f6b4814991c8b3bde68d2c5f6b7
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002653"
---
# <a name="425"></a>[<span data-ttu-id="b8343-101">4.25</span><span class="sxs-lookup"><span data-stu-id="b8343-101">4.25</span></span>](#tab/425)

<span data-ttu-id="b8343-102">若要在蓝图中使用现货，请在 **Windows Mixed REALITY HMD** 下搜索任何操作：</span><span class="sxs-lookup"><span data-stu-id="b8343-102">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![手动射线最佳实践](../images/unreal/hand-rays-bp.png)

<span data-ttu-id="b8343-104">若要在 c + + 中访问它们，请将添加 `WindowsMixedRealityFunctionLibrary.h` 到调用代码文件的顶部。</span><span class="sxs-lookup"><span data-stu-id="b8343-104">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="b8343-105">枚举</span><span class="sxs-lookup"><span data-stu-id="b8343-105">Enum</span></span>

<span data-ttu-id="b8343-106">你还可以访问 **EHMDInputControllerButtons** 下的输入事例，它们可在蓝图中使用：</span><span class="sxs-lookup"><span data-stu-id="b8343-106">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![输入控制器按钮](../images/unreal/input-controller-buttons.png)

<span data-ttu-id="b8343-108">若要在 c + + 中访问，请使用 `EHMDInputControllerButtons` enum 类：</span><span class="sxs-lookup"><span data-stu-id="b8343-108">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="b8343-109">下面是两个适用的枚举事例的细目：</span><span class="sxs-lookup"><span data-stu-id="b8343-109">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="b8343-110">**选择** -用户触发的 Select 事件。</span><span class="sxs-lookup"><span data-stu-id="b8343-110">**Select** - User triggered Select event.</span></span>
    * <span data-ttu-id="b8343-111">通过使用 "选择" （启用 [语音输入](../unreal-voice-input.md) ）在 HoloLens 2 中触发。</span><span class="sxs-lookup"><span data-stu-id="b8343-111">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](../unreal-voice-input.md) enabled.</span></span>
* <span data-ttu-id="b8343-112">**抓住** 用户触发的抓住事件。</span><span class="sxs-lookup"><span data-stu-id="b8343-112">**Grasp** - User triggered Grasp event.</span></span>
    * <span data-ttu-id="b8343-113">在 HoloLens 2 中通过将用户的手指关闭到全息图上触发。</span><span class="sxs-lookup"><span data-stu-id="b8343-113">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span>

<span data-ttu-id="b8343-114">可以通过下面所示的枚举来访问 c + + 中手写网格的跟踪状态 `EHMDTrackingStatus` ：</span><span class="sxs-lookup"><span data-stu-id="b8343-114">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="b8343-115">下面是两个适用的枚举事例的细目：</span><span class="sxs-lookup"><span data-stu-id="b8343-115">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="b8343-116">**NotTracked** –手写不可见</span><span class="sxs-lookup"><span data-stu-id="b8343-116">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="b8343-117">**跟踪** –完全跟踪</span><span class="sxs-lookup"><span data-stu-id="b8343-117">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="b8343-118">结构</span><span class="sxs-lookup"><span data-stu-id="b8343-118">Struct</span></span>

<span data-ttu-id="b8343-119">PointerPoseInfo 结构可为你带来以下手数据信息：</span><span class="sxs-lookup"><span data-stu-id="b8343-119">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="b8343-120">**源** –现有的原点</span><span class="sxs-lookup"><span data-stu-id="b8343-120">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="b8343-121">**方向** –手型方向</span><span class="sxs-lookup"><span data-stu-id="b8343-121">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="b8343-122">**向上** –向上向量</span><span class="sxs-lookup"><span data-stu-id="b8343-122">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="b8343-123">**方向** -方向四元数</span><span class="sxs-lookup"><span data-stu-id="b8343-123">**Orientation** – orientation quaternion</span></span>
* <span data-ttu-id="b8343-124">**跟踪状态** -当前跟踪状态</span><span class="sxs-lookup"><span data-stu-id="b8343-124">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="b8343-125">可以通过蓝图访问 PointerPoseInfo 结构，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b8343-125">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![指针姿势信息最佳实践](../images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="b8343-127">或带有 c + +：</span><span class="sxs-lookup"><span data-stu-id="b8343-127">Or with C++:</span></span>

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a><span data-ttu-id="b8343-128">函数</span><span class="sxs-lookup"><span data-stu-id="b8343-128">Functions</span></span>

<span data-ttu-id="b8343-129">可以在每个帧上调用下面列出的所有函数，这允许持续监视。</span><span class="sxs-lookup"><span data-stu-id="b8343-129">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span>

1. <span data-ttu-id="b8343-130">**获取指针姿势信息** 返回有关当前帧中的现货方向的完整信息。</span><span class="sxs-lookup"><span data-stu-id="b8343-130">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span>

<span data-ttu-id="b8343-131">建立</span><span class="sxs-lookup"><span data-stu-id="b8343-131">Blueprint:</span></span>

![获取指针姿势信息](../images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="b8343-133">C++：</span><span class="sxs-lookup"><span data-stu-id="b8343-133">C++:</span></span>
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="b8343-134">如果指针在当前帧中 Grasped，**则为 Grasped** 返回 true。</span><span class="sxs-lookup"><span data-stu-id="b8343-134">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="b8343-135">建立</span><span class="sxs-lookup"><span data-stu-id="b8343-135">Blueprint:</span></span>

![是 Grasped 的最佳实践](../images/unreal/is-grasped-bp.png)

<span data-ttu-id="b8343-137">C++：</span><span class="sxs-lookup"><span data-stu-id="b8343-137">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. <span data-ttu-id="b8343-138">如果用户在当前帧中触发了 Select，**则选择 "按下" 将** 返回 true。</span><span class="sxs-lookup"><span data-stu-id="b8343-138">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="b8343-139">建立</span><span class="sxs-lookup"><span data-stu-id="b8343-139">Blueprint:</span></span>

![选择按下的 BP](../images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="b8343-141">C++：</span><span class="sxs-lookup"><span data-stu-id="b8343-141">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="b8343-142">如果在当前帧中触发事件或按钮，**则单击 "是" 按钮** 返回 true。</span><span class="sxs-lookup"><span data-stu-id="b8343-142">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="b8343-143">建立</span><span class="sxs-lookup"><span data-stu-id="b8343-143">Blueprint:</span></span>

![按钮是否已单击 BP](../images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="b8343-145">C++：</span><span class="sxs-lookup"><span data-stu-id="b8343-145">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="b8343-146">**获取控制器跟踪状态** 返回当前帧中的跟踪状态。</span><span class="sxs-lookup"><span data-stu-id="b8343-146">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="b8343-147">建立</span><span class="sxs-lookup"><span data-stu-id="b8343-147">Blueprint:</span></span>

![获取控制器跟踪状态 BP](../images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="b8343-149">C++：</span><span class="sxs-lookup"><span data-stu-id="b8343-149">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
# <a name="426"></a>[<span data-ttu-id="b8343-150">4.26</span><span class="sxs-lookup"><span data-stu-id="b8343-150">4.26</span></span>](#tab/426)

<span data-ttu-id="b8343-151">若要获取手写片的数据，应使用上一节中的 Get 运动控制器数据函数。</span><span class="sxs-lookup"><span data-stu-id="b8343-151">To get the data for the hand rays, you should use the Get Motion Controller Data function from the previous section.</span></span> <span data-ttu-id="b8343-152">返回的结构包含两个参数，您可以使用这些参数创建一个手型， **瞄准位置** 和 **aim 旋转**。</span><span class="sxs-lookup"><span data-stu-id="b8343-152">The returned structure contains two parameters you can use to create a hand ray – **Aim Position** and **Aim Rotation**.</span></span> <span data-ttu-id="b8343-153">这些参数构成弯头线。</span><span class="sxs-lookup"><span data-stu-id="b8343-153">These parameters form a ray directed by your elbow.</span></span> <span data-ttu-id="b8343-154">您应该获取它们并查找指向的全息影像。</span><span class="sxs-lookup"><span data-stu-id="b8343-154">You should take them and find a hologram being pointed by.</span></span>

<span data-ttu-id="b8343-155">下面是一个示例，该示例确定手 ray 是否击中小组件并设置自定义命中结果：</span><span class="sxs-lookup"><span data-stu-id="b8343-155">Below is an example of determining whether a hand ray hits a Widget and setting a custom hit result:</span></span>

![获取运动控制器数据函数的蓝图](../images/unreal-hand-tracking-img-04.png) 