---
title: Unreal 中的手部跟踪
description: 说明如何在 Unreal 中使用手动跟踪
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality，手动跟踪，Unreal，Unreal 引擎4，UE4，HoloLens，HoloLens 2，混合现实，开发，功能，文档，指南，全息影像，游戏开发
ms.openlocfilehash: 5bc120f802c2160282befd1ce6cb8025be21cbaa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675877"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="4a1a6-104">Unreal 中的手部跟踪</span><span class="sxs-lookup"><span data-stu-id="4a1a6-104">Hand tracking in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="4a1a6-105">概述</span><span class="sxs-lookup"><span data-stu-id="4a1a6-105">Overview</span></span>

<span data-ttu-id="4a1a6-106">手写跟踪系统使用用户的不要和手指作为输入。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-106">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="4a1a6-107">您可以获取每个手指的位置和旋转、整个手掌甚至是在代码中使用的手势。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-107">You can get the position and rotation of every finger, the entire palm, and even hand gestures to use in your code.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="4a1a6-108">举手</span><span class="sxs-lookup"><span data-stu-id="4a1a6-108">Hand Pose</span></span>

<span data-ttu-id="4a1a6-109">使用举手功能，你可以跟踪活动用户的手和手指，并将其用作输入，你可以通过蓝图和 c + + 进行访问。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-109">Hand pose lets you track the hands and fingers of the active user and use it as input, which you can access through Blueprints and C++.</span></span> <span data-ttu-id="4a1a6-110">可以在 Unreal 的 [HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) API 中找到更多技术详细信息。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-110">You can find more technical details in Unreal's [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) API.</span></span> <span data-ttu-id="4a1a6-111">Unreal API 以坐标系统的形式发送数据，并使用 Unreal 引擎同步刻度。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

### <a name="understanding-the-bone-hierarchy"></a><span data-ttu-id="4a1a6-112">了解骨骼层次结构</span><span class="sxs-lookup"><span data-stu-id="4a1a6-112">Understanding the bone hierarchy</span></span>

<span data-ttu-id="4a1a6-113">`EWMRHandKeypoint`枚举描述手形的骨骼层次结构。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-113">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="4a1a6-114">可以在蓝图中找到每个 keypoint：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-114">You can find each hand keypoint listed in your Blueprints:</span></span>

![手动 Keypoint 最佳实践](images/hand-keypoint-bp.png)

<span data-ttu-id="4a1a6-116">完整的 c + + 枚举如下所示：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-116">The full C++ enum is listed below:</span></span>
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

<span data-ttu-id="4a1a6-117">您可以在 [HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) 表中找到每个枚举用例的数值。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-117">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span> <span data-ttu-id="4a1a6-118">下图显示了具有匹配枚举事例的整个手型布局：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-118">The entire hand pose layout with matching enum cases is shown in the image below:</span></span>

![手写框架](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a><span data-ttu-id="4a1a6-120">支持手动跟踪</span><span class="sxs-lookup"><span data-stu-id="4a1a6-120">Supporting Hand Tracking</span></span>

<span data-ttu-id="4a1a6-121">可以通过在 **Windows Mixed Reality > 手动** 跟踪中添加 **支持手动** 跟踪，在蓝图中使用手动跟踪：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-121">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality** :</span></span>

![手动跟踪最佳实践](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="4a1a6-123">`true`如果设备上是否支持手动跟踪，则此函数返回， `false` 如果未提供手动跟踪，则返回。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-123">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking is not available.</span></span>

![支持手动跟踪最佳实践](images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="4a1a6-125">C++：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-125">C++:</span></span> 

<span data-ttu-id="4a1a6-126">添加 `WindowsMixedRealityHandTrackingFunctionLibrary.h`。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-126">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="4a1a6-127">正在获取手动跟踪</span><span class="sxs-lookup"><span data-stu-id="4a1a6-127">Getting Hand Tracking</span></span>
<span data-ttu-id="4a1a6-128">您可以使用 **GetHandJointTransform** 从手返回空间数据。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-128">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="4a1a6-129">数据将每帧更新一次，但如果在框架中，则会缓存返回值。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-129">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="4a1a6-130">出于性能方面的考虑，不建议在此函数中使用繁重的逻辑。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-130">It's not recommended to have heavy logic in this function for performance reasons.</span></span> 

![获取手动联合转换](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="4a1a6-132">C++：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-132">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="4a1a6-133">函数参数细目：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-133">Function parameter breakdown:</span></span>

* <span data-ttu-id="4a1a6-134">**手型** –是用户的左侧或右侧</span><span class="sxs-lookup"><span data-stu-id="4a1a6-134">**Hand** – an be the left or right hand of the user</span></span>
* <span data-ttu-id="4a1a6-135">**Keypoint** –手型的骨骼。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-135">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="4a1a6-136">**转换** –骨骼基的坐标和方向。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-136">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="4a1a6-137">你可以请求下一个骨骼的基，以获取骨骼末尾的转换数据。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-137">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="4a1a6-138">特殊的 Tip 骨骼提供 distal 的结尾。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-138">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="4a1a6-139">**半径** -骨骼基的半径。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-139">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="4a1a6-140">**返回值** -如果在此帧中跟踪了骨骼，则为 true; 如果未跟踪骨骼，则为 false。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-140">**Return Value** — true if the bone is tracked this frame, false if the bone is not tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="4a1a6-141">手动实时链接动画</span><span class="sxs-lookup"><span data-stu-id="4a1a6-141">Hand Live Link Animation</span></span>
<span data-ttu-id="4a1a6-142">使用 [实时链接插件](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)向动画显示手姿势。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-142">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="4a1a6-143">如果启用了 Windows Mixed Reality 和 Live Link 插件：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-143">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span> 
1. <span data-ttu-id="4a1a6-144">选择 " **窗口 >" 实时链接** "，打开" 实时链接编辑器 "窗口。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-144">Select **Window > Live Link** to open the Live Link editor window.</span></span> 
2. <span data-ttu-id="4a1a6-145">单击 " **源** " 并启用 **Windows Mixed Reality 手动跟踪源**</span><span class="sxs-lookup"><span data-stu-id="4a1a6-145">Click **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![实时链接源](images/unreal/live-link-source.png)
 
<span data-ttu-id="4a1a6-147">启用源并打开动画资产后，展开 " **预览场景** " 选项卡中的 " **动画** " 部分会显示其他选项 (详细信息显示在 Unreal 的实时链接文档中-由于插件已在 beta 中，因此该过程稍后可能会更改) 。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-147">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options (the details are in Unreal’s Live Link documentation - as the plugin is in beta, the process may change later).</span></span>

![实时链接动画](images/unreal/live-link-animation.png)
 
<span data-ttu-id="4a1a6-149">手型动画层次结构与在中相同 `EWMRHandKeypoint` 。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-149">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="4a1a6-150">动画可以使用 **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** 重定向：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-150">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** :</span></span>

![实时链接动画2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="4a1a6-152">还可以在编辑器中将它作为子类：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-152">It can also be subclassed in the editor:</span></span>

![实时链接重新映射](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a><span data-ttu-id="4a1a6-154">访问手写网格数据</span><span class="sxs-lookup"><span data-stu-id="4a1a6-154">Accessing Hand Mesh Data</span></span>

![手写网格](images/unreal/hand-mesh.png)

<span data-ttu-id="4a1a6-156">在可以访问手写网格数据之前，你需要：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-156">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="4a1a6-157">选择 **ARSessionConfig** 资产，展开 " **AR 设置->** " "世界" 映射设置，然后选中 " **根据跟踪的几何生成网格数据** "。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-157">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry** .</span></span> 

<span data-ttu-id="4a1a6-158">下面是默认的网格参数：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-158">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="4a1a6-159">将网格数据用于封闭</span><span class="sxs-lookup"><span data-stu-id="4a1a6-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="4a1a6-160">为网格数据生成冲突</span><span class="sxs-lookup"><span data-stu-id="4a1a6-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="4a1a6-161">为网格数据生成导航网格</span><span class="sxs-lookup"><span data-stu-id="4a1a6-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="4a1a6-162">以线框–用于显示生成的网格的 debug 参数呈现网格数据</span><span class="sxs-lookup"><span data-stu-id="4a1a6-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="4a1a6-163">这些参数值用作空间映射网格和手写网格默认值。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-163">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="4a1a6-164">你可以在任何网格的蓝图或代码中随时对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-164">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="4a1a6-165">C + + API 参考</span><span class="sxs-lookup"><span data-stu-id="4a1a6-165">C++ API Reference</span></span> 
<span data-ttu-id="4a1a6-166">用于 `EEARObjectClassification` 查找所有以可跟踪对象中的手写网格值。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-166">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

<span data-ttu-id="4a1a6-167">当系统检测到任何以可跟踪对象（包括手写网格）时，将调用以下委托。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-167">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

<span data-ttu-id="4a1a6-168">请确保委托处理程序遵循下面的函数签名：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-168">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="4a1a6-169">可以通过以下操作访问网格数据  `UARTrackedGeometry::GetUnderlyingMesh` ：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-169">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a><span data-ttu-id="4a1a6-170">蓝图 API 参考</span><span class="sxs-lookup"><span data-stu-id="4a1a6-170">Blueprint API Reference</span></span>

<span data-ttu-id="4a1a6-171">若要在蓝图中使用手写网格：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-171">In order to work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="4a1a6-172">将 **ARTrackableNotify** 组件添加到蓝图参与者</span><span class="sxs-lookup"><span data-stu-id="4a1a6-172">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)
 
2. <span data-ttu-id="4a1a6-174">请参阅 " **详细信息** " 面板，展开 " **事件** " 部分。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-174">Go to the **Details** panel and expand the **Events** section.</span></span> 

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)
 
3. <span data-ttu-id="4a1a6-176">添加/更新/删除跟踪的几何图形时覆盖事件图中的以下节点：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-176">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![在 ARTrackable 通知上](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="4a1a6-178">手写光线</span><span class="sxs-lookup"><span data-stu-id="4a1a6-178">Hand Rays</span></span>

<span data-ttu-id="4a1a6-179">您可以在 c + + 和蓝图中使用一种手写作为指针设备，这会公开 [SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-179">You can use a hand ray as a pointing device in both C++ and Blueprints, which exposes the [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API.</span></span>

<span data-ttu-id="4a1a6-180">必须指出的是，由于所有函数的结果都更改每个帧，因此它们都是可调用的。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-180">It’s important to mention that since the results of all the functions change every frame, they're all made callable.</span></span> <span data-ttu-id="4a1a6-181">有关纯函数和非纯函数或可调用函数的详细信息，请参阅蓝图用户 guid on [函数](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span><span class="sxs-lookup"><span data-stu-id="4a1a6-181">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span></span>

<span data-ttu-id="4a1a6-182">若要在蓝图中使用现货，请在 **Windows Mixed REALITY HMD** 下搜索任何操作：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-182">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD** :</span></span>

![手动射线最佳实践](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="4a1a6-184">若要在 c + + 中访问它们，请将添加 `WindowsMixedRealityFunctionLibrary.h` 到调用代码文件的顶部。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-184">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="4a1a6-185">枚举</span><span class="sxs-lookup"><span data-stu-id="4a1a6-185">Enum</span></span>
<span data-ttu-id="4a1a6-186">你还可以访问 **EHMDInputControllerButtons** 下的输入事例，它们可在蓝图中使用：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-186">You also have access to input cases under **EHMDInputControllerButtons** , which can be used in Blueprints:</span></span>

![输入控制器按钮](images/unreal/input-controller-buttons.png)

<span data-ttu-id="4a1a6-188">若要在 c + + 中访问，请使用 `EHMDInputControllerButtons` enum 类：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-188">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="4a1a6-189">下面是两个适用的枚举事例的细目：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-189">Below is a breakdown of the two applicable enum cases:</span></span>
* <span data-ttu-id="4a1a6-190">**选择** -用户触发的 Select 事件。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-190">**Select** - User triggered Select event.</span></span> 
    * <span data-ttu-id="4a1a6-191">通过使用 "选择" 并启用 [语音输入](unreal-voice-input.md) ，可以在 HoloLens 2 中触发事件。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-191">The event can be triggered in HoloLens 2 by air-tap, gaze and commit, or by saying “Select” with [voice input](unreal-voice-input.md) enabled.</span></span> 
* <span data-ttu-id="4a1a6-192">**抓住** 用户触发的抓住事件。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-192">**Grasp** - User triggered Grasp event.</span></span> 
    * <span data-ttu-id="4a1a6-193">可以通过将用户的手指置于全息图上，在 HoloLens 2 中触发此事件。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-193">This event can be triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 

<span data-ttu-id="4a1a6-194">可以通过下面所示的枚举来访问 c + + 中手写网格的跟踪状态 `EHMDTrackingStatus` ：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-194">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="4a1a6-195">下面是两个适用的枚举事例的细目：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-195">Below is a breakdown of the two applicable enum cases:</span></span>
* <span data-ttu-id="4a1a6-196">**NotTracked** –手写不可见</span><span class="sxs-lookup"><span data-stu-id="4a1a6-196">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="4a1a6-197">**跟踪** –完全跟踪</span><span class="sxs-lookup"><span data-stu-id="4a1a6-197">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="4a1a6-198">结构</span><span class="sxs-lookup"><span data-stu-id="4a1a6-198">Struct</span></span>
<span data-ttu-id="4a1a6-199">PointerPoseInfo 结构可为你带来以下手数据信息：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-199">The PointerPoseInfo struct can give you information on the following hand data:</span></span>
* <span data-ttu-id="4a1a6-200">**源** –现有的原点</span><span class="sxs-lookup"><span data-stu-id="4a1a6-200">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="4a1a6-201">**方向** –手型方向</span><span class="sxs-lookup"><span data-stu-id="4a1a6-201">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="4a1a6-202">**向上** –向上向量</span><span class="sxs-lookup"><span data-stu-id="4a1a6-202">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="4a1a6-203">**方向** -方向四元数</span><span class="sxs-lookup"><span data-stu-id="4a1a6-203">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="4a1a6-204">**跟踪状态** -当前跟踪状态</span><span class="sxs-lookup"><span data-stu-id="4a1a6-204">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="4a1a6-205">可以通过蓝图访问此内容，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-205">You can access this through Blueprints, as shown below:</span></span>

![指针姿势信息最佳实践](images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="4a1a6-207">或带有 c + +：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-207">Or with C++:</span></span>

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

### <a name="functions"></a><span data-ttu-id="4a1a6-208">函数</span><span class="sxs-lookup"><span data-stu-id="4a1a6-208">Functions</span></span>

<span data-ttu-id="4a1a6-209">可以在每个帧上调用下面列出的所有函数，这允许持续监视。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-209">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span> 

1. <span data-ttu-id="4a1a6-210">**获取指针姿势信息** 返回有关当前帧中的现货方向的完整信息。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-210">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span> 

<span data-ttu-id="4a1a6-211">建立</span><span class="sxs-lookup"><span data-stu-id="4a1a6-211">Blueprint:</span></span>

![获取指针姿势信息](images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="4a1a6-213">C++：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-213">C++:</span></span> 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="4a1a6-214">如果指针在当前帧中 Grasped， **则为 Grasped** 返回 true。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-214">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="4a1a6-215">建立</span><span class="sxs-lookup"><span data-stu-id="4a1a6-215">Blueprint:</span></span>

![是 Grasped 的最佳实践](images/unreal/is-grasped-bp.png)

<span data-ttu-id="4a1a6-217">C++：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-217">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. <span data-ttu-id="4a1a6-218">如果用户在当前帧中触发了 Select， **则选择 "按下" 将** 返回 true。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-218">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="4a1a6-219">建立</span><span class="sxs-lookup"><span data-stu-id="4a1a6-219">Blueprint:</span></span>

![选择按下的 BP](images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="4a1a6-221">C++：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-221">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="4a1a6-222">如果在当前帧中触发事件或按钮， **则单击 "是" 按钮** 返回 true。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-222">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="4a1a6-223">建立</span><span class="sxs-lookup"><span data-stu-id="4a1a6-223">Blueprint:</span></span>

![按钮是否已单击 BP](images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="4a1a6-225">C++：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-225">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="4a1a6-226">**获取控制器跟踪状态** 返回当前帧中的跟踪状态。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-226">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="4a1a6-227">建立</span><span class="sxs-lookup"><span data-stu-id="4a1a6-227">Blueprint:</span></span>

![获取控制器跟踪状态 BP](images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="4a1a6-229">C++：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-229">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a><span data-ttu-id="4a1a6-230">笔势</span><span class="sxs-lookup"><span data-stu-id="4a1a6-230">Gestures</span></span>

<span data-ttu-id="4a1a6-231">Hololens 2 可以跟踪空间手势，这意味着您可以将这些手势捕获为输入。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-231">The Hololens 2 can track spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="4a1a6-232">可以在 [HoloLens 2 基本使用](https://docs.microsoft.com/hololens/hololens2-basic-usage) 文档中找到有关手势的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-232">You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

<span data-ttu-id="4a1a6-233">您可以在 " **Windows Mixed Reality 空间输入** " 下查找蓝图函数，并通过 `WindowsMixedRealitySpatialInputFunctionLibrary.h` 在调用代码文件中添加来查找 c + + 函数。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-233">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input** , and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![捕获手势](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="4a1a6-235">枚举</span><span class="sxs-lookup"><span data-stu-id="4a1a6-235">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="4a1a6-236">建立</span><span class="sxs-lookup"><span data-stu-id="4a1a6-236">Blueprint:</span></span> 

![手势类型](images/unreal/gesture-type.png)

<span data-ttu-id="4a1a6-238">C++：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-238">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="4a1a6-239">函数</span><span class="sxs-lookup"><span data-stu-id="4a1a6-239">Function</span></span>
<span data-ttu-id="4a1a6-240">您可以使用函数启用和禁用手势捕获 `CaptureGestures` 。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-240">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="4a1a6-241">当启用的笔势激发输入事件时， `true` 如果手势捕获成功，则函数返回 `false` ; 如果出现错误，则返回。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-241">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="4a1a6-242">建立</span><span class="sxs-lookup"><span data-stu-id="4a1a6-242">Blueprint:</span></span>

![捕获手势最佳实践](images/unreal/capture-gestures-bp.png)

<span data-ttu-id="4a1a6-244">C++：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-244">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

<span data-ttu-id="4a1a6-245">下面是关键事件，可在蓝图和 c + +： ![ 键事件中找到](images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="4a1a6-245">The following are key events, which you can find in Blueprints and C++: ![Key Events](images/unreal/key-events.png)</span></span>

![关键事件2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

## <a name="next-development-checkpoint"></a><span data-ttu-id="4a1a6-247">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="4a1a6-247">Next Development Checkpoint</span></span>

<span data-ttu-id="4a1a6-248">如果遵循我们所 Unreal 的开发检查点旅程，就是在探索 MRTK 核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-248">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="4a1a6-249">在这里，你可以继续执行下一个构建基块：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-249">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="4a1a6-250">本地空间定位点</span><span class="sxs-lookup"><span data-stu-id="4a1a6-250">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="4a1a6-251">或跳转到混合现实平台功能和 Api：</span><span class="sxs-lookup"><span data-stu-id="4a1a6-251">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4a1a6-252">HoloLens 摄像头</span><span class="sxs-lookup"><span data-stu-id="4a1a6-252">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="4a1a6-253">随时可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks) 。</span><span class="sxs-lookup"><span data-stu-id="4a1a6-253">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>