---
title: Unreal 中的手部跟踪
description: 说明如何在 Unreal 中使用手动跟踪
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality，手动跟踪，Unreal，Unreal 引擎4，UE4，HoloLens，HoloLens 2，混合现实，开发，功能，文档，指南，全息影像，游戏开发，混合现实耳机，windows Mixed Reality 耳机，虚拟现实耳机
ms.openlocfilehash: 66ae1994f2bbee3ba4786a7c4eeebfe1cd57ca37
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002644"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="f7b41-104">Unreal 中的手部跟踪</span><span class="sxs-lookup"><span data-stu-id="f7b41-104">Hand tracking in Unreal</span></span>

<span data-ttu-id="f7b41-105">手写跟踪系统使用用户的不要和手指作为输入。</span><span class="sxs-lookup"><span data-stu-id="f7b41-105">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="f7b41-106">每个手指的位置和旋转数据都可用。</span><span class="sxs-lookup"><span data-stu-id="f7b41-106">Data on position and rotation of every finger, the entire palm, and hand gestures is available.</span></span> <span data-ttu-id="f7b41-107">从 Unreal 4.26 开始，手动跟踪基于 Unreal HeadMountedDisplay 插件，并在所有 XR 平台和设备上使用公共 API。</span><span class="sxs-lookup"><span data-stu-id="f7b41-107">Starting in Unreal 4.26, hand tracking is based on the Unreal HeadMountedDisplay plugin and uses a common API across all XR platforms and devices.</span></span> <span data-ttu-id="f7b41-108">对于 Windows Mixed Reality 和 OpenXR 系统，功能是相同的。</span><span class="sxs-lookup"><span data-stu-id="f7b41-108">Functionality is the same for both Windows Mixed Reality and OpenXR systems.</span></span>

## <a name="hand-pose"></a><span data-ttu-id="f7b41-109">举手</span><span class="sxs-lookup"><span data-stu-id="f7b41-109">Hand pose</span></span>

<span data-ttu-id="f7b41-110">使用举手功能，您可以跟踪和使用用户的手和手指作为输入，可在蓝图和 c + + 中访问。</span><span class="sxs-lookup"><span data-stu-id="f7b41-110">Hand pose lets you track and use the hands and fingers of your users as input, which can be accessed in both Blueprints and C++.</span></span> <span data-ttu-id="f7b41-111">Unreal API 以坐标系统的形式发送数据，并使用 Unreal 引擎同步刻度。</span><span class="sxs-lookup"><span data-stu-id="f7b41-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

![手写框架](../native/images/hand-skeleton.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a><span data-ttu-id="f7b41-113">手动实时链接动画</span><span class="sxs-lookup"><span data-stu-id="f7b41-113">Hand Live Link Animation</span></span>

<span data-ttu-id="f7b41-114">使用 [实时链接插件](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)向动画显示手姿势。</span><span class="sxs-lookup"><span data-stu-id="f7b41-114">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="f7b41-115">如果启用了 Windows Mixed Reality 和 Live Link 插件：</span><span class="sxs-lookup"><span data-stu-id="f7b41-115">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span>
1. <span data-ttu-id="f7b41-116">选择 " **窗口 >" 实时链接** "，打开" 实时链接编辑器 "窗口。</span><span class="sxs-lookup"><span data-stu-id="f7b41-116">Select **Window > Live Link** to open the Live Link editor window.</span></span>
2. <span data-ttu-id="f7b41-117">选择 **源** 并启用 **Windows Mixed Reality 手动跟踪源**</span><span class="sxs-lookup"><span data-stu-id="f7b41-117">Select **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![实时链接源](images/unreal/live-link-source.png)

<span data-ttu-id="f7b41-119">启用源并打开动画资产后，展开 "**预览场景**" 选项卡中的 "**动画**" 部分也会显示其他选项。</span><span class="sxs-lookup"><span data-stu-id="f7b41-119">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options.</span></span>

![实时链接动画](images/unreal/live-link-animation.png)

<span data-ttu-id="f7b41-121">手型动画层次结构与在中相同 `EWMRHandKeypoint` 。</span><span class="sxs-lookup"><span data-stu-id="f7b41-121">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="f7b41-122">动画可以使用 **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** 重定向：</span><span class="sxs-lookup"><span data-stu-id="f7b41-122">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![实时链接动画2](images/unreal/live-link-animation2.png)

<span data-ttu-id="f7b41-124">还可以在编辑器中将它作为子类：</span><span class="sxs-lookup"><span data-stu-id="f7b41-124">It can also be subclassed in the editor:</span></span>

![实时链接重新映射](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a><span data-ttu-id="f7b41-126">手写网格</span><span class="sxs-lookup"><span data-stu-id="f7b41-126">Hand Mesh</span></span>

### <a name="hand-mesh-as-a-tracked-geometry"></a><span data-ttu-id="f7b41-127">手动网格作为跟踪的几何图形</span><span class="sxs-lookup"><span data-stu-id="f7b41-127">Hand Mesh as a Tracked Geometry</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f7b41-128">若要在 OpenXR 中将手写网格作为跟踪的几何获取，则需要调用 **已启用跟踪几何** 的 "**使用手网格**"。</span><span class="sxs-lookup"><span data-stu-id="f7b41-128">Getting hand meshes as a tracked geometry in OpenXR requires you to call **Set Use Hand Mesh** with **Enabled Tracking Geometry**.</span></span>

<span data-ttu-id="f7b41-129">若要启用该模式，应调用 **已启用跟踪几何** 的 "**使用手网格**"：</span><span class="sxs-lookup"><span data-stu-id="f7b41-129">To enable that mode you should call **Set Use Hand Mesh** with **Enabled Tracking Geometry**:</span></span>

![事件开始播放的蓝图连接到已启用跟踪几何模式的 "使用手写" 功能](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> <span data-ttu-id="f7b41-131">不可能同时启用这两种模式。</span><span class="sxs-lookup"><span data-stu-id="f7b41-131">It’s not possible for both modes to be enabled at the same time.</span></span> <span data-ttu-id="f7b41-132">如果启用，则会自动禁用另一个。</span><span class="sxs-lookup"><span data-stu-id="f7b41-132">If you enable one, the other is automatically disabled.</span></span>

### <a name="accessing-hand-mesh-data"></a><span data-ttu-id="f7b41-133">访问手写网格数据</span><span class="sxs-lookup"><span data-stu-id="f7b41-133">Accessing Hand Mesh Data</span></span>

![手写网格](images/unreal/hand-mesh.png)

<span data-ttu-id="f7b41-135">在可以访问手写网格数据之前，你需要：</span><span class="sxs-lookup"><span data-stu-id="f7b41-135">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="f7b41-136">选择 **ARSessionConfig** 资产，展开 " **AR 设置->** " "世界" 映射设置，然后选中 " **根据跟踪的几何生成网格数据**"。</span><span class="sxs-lookup"><span data-stu-id="f7b41-136">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span>

<span data-ttu-id="f7b41-137">下面是默认的网格参数：</span><span class="sxs-lookup"><span data-stu-id="f7b41-137">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="f7b41-138">将网格数据用于封闭</span><span class="sxs-lookup"><span data-stu-id="f7b41-138">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="f7b41-139">为网格数据生成冲突</span><span class="sxs-lookup"><span data-stu-id="f7b41-139">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="f7b41-140">为网格数据生成导航网格</span><span class="sxs-lookup"><span data-stu-id="f7b41-140">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="f7b41-141">以线框–用于显示生成的网格的 debug 参数呈现网格数据</span><span class="sxs-lookup"><span data-stu-id="f7b41-141">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="f7b41-142">这些参数值用作空间映射网格和手写网格默认值。</span><span class="sxs-lookup"><span data-stu-id="f7b41-142">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="f7b41-143">你可以在任何网格的蓝图或代码中随时对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="f7b41-143">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="f7b41-144">C + + API 参考</span><span class="sxs-lookup"><span data-stu-id="f7b41-144">C++ API Reference</span></span>
<span data-ttu-id="f7b41-145">用于 `EEARObjectClassification` 查找所有以可跟踪对象中的手写网格值。</span><span class="sxs-lookup"><span data-stu-id="f7b41-145">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

<span data-ttu-id="f7b41-146">当系统检测到任何以可跟踪对象（包括手写网格）时，将调用以下委托。</span><span class="sxs-lookup"><span data-stu-id="f7b41-146">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span>

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

<span data-ttu-id="f7b41-147">请确保委托处理程序遵循下面的函数签名：</span><span class="sxs-lookup"><span data-stu-id="f7b41-147">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="f7b41-148">可以通过以下操作访问网格数据  `UARTrackedGeometry::GetUnderlyingMesh` ：</span><span class="sxs-lookup"><span data-stu-id="f7b41-148">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a><span data-ttu-id="f7b41-149">蓝图 API 参考</span><span class="sxs-lookup"><span data-stu-id="f7b41-149">Blueprint API Reference</span></span>

<span data-ttu-id="f7b41-150">若要在蓝图中使用手写网格：</span><span class="sxs-lookup"><span data-stu-id="f7b41-150">To work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="f7b41-151">将 **ARTrackableNotify** 组件添加到蓝图参与者</span><span class="sxs-lookup"><span data-stu-id="f7b41-151">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)

2. <span data-ttu-id="f7b41-153">请参阅 " **详细信息** " 面板，展开 " **事件** " 部分。</span><span class="sxs-lookup"><span data-stu-id="f7b41-153">Go to the **Details** panel and expand the **Events** section.</span></span>

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)

3. <span data-ttu-id="f7b41-155">添加/更新/删除跟踪的几何图形时覆盖事件图中的以下节点：</span><span class="sxs-lookup"><span data-stu-id="f7b41-155">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![在 ARTrackable 通知上](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a><span data-ttu-id="f7b41-157">OpenXR 中的手写图形可视化效果</span><span class="sxs-lookup"><span data-stu-id="f7b41-157">Hand Mesh visualization in OpenXR</span></span>

<span data-ttu-id="f7b41-158">可视化手写网格的建议方法是将长篇故事的 XRVisualization 插件与 [Microsoft OpenXR 插件](https://github.com/microsoft/Microsoft-OpenXR-Unreal)结合使用。</span><span class="sxs-lookup"><span data-stu-id="f7b41-158">The recommended way to visualize hand mesh is to use Epic’s XRVisualization plugin together with the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span> 

<span data-ttu-id="f7b41-159">然后，在蓝图编辑器中，应使用 **启用了 XRVisualization** 的 [Microsoft OpenXR 插件](https://github.com/microsoft/Microsoft-OpenXR-Unreal)中的 "**使用手网格**" 功能作为参数：</span><span class="sxs-lookup"><span data-stu-id="f7b41-159">Then in the blueprint editor, you should use **Set Use Hand Mesh** function from the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) with **Enabled XRVisualization** as a parameter:</span></span>

![事件开始播放的蓝图已连接到已启用 xrvisualization 模式的 "使用手动网格" 功能](images/unreal-hand-tracking-img-05.png)

<span data-ttu-id="f7b41-161">若要管理呈现过程，应使用 XRVisualization 中的 **Render 运动控制器** ：</span><span class="sxs-lookup"><span data-stu-id="f7b41-161">To manage the rendering process, you should use **Render Motion Controller** from XRVisualization:</span></span>

![连接到呈现运动控制器函数的 get 运动控制器数据函数蓝图](images/unreal-hand-tracking-img-06.png)

<span data-ttu-id="f7b41-163">结果：</span><span class="sxs-lookup"><span data-stu-id="f7b41-163">The result:</span></span>

![重叠的数字手图像](images/unreal-hand-tracking-img-07.png) 

<span data-ttu-id="f7b41-165">如果需要更复杂的内容，如使用自定义着色器绘制手写网格，则需要将网格作为跟踪的几何获取。</span><span class="sxs-lookup"><span data-stu-id="f7b41-165">If you need anything more complicated, such as drawing a hand mesh with a custom shader, you need to get the meshes as a tracked geometry.</span></span> 

## <a name="hand-rays"></a><span data-ttu-id="f7b41-166">手部射线</span><span class="sxs-lookup"><span data-stu-id="f7b41-166">Hand rays</span></span>

<span data-ttu-id="f7b41-167">手动姿势用于接近对象或按下按钮等关闭交互。</span><span class="sxs-lookup"><span data-stu-id="f7b41-167">Getting hand pose works for close interactions like grabbing objects or pressing buttons.</span></span> <span data-ttu-id="f7b41-168">但是，有时您需要使用离用户更远的全息影像。</span><span class="sxs-lookup"><span data-stu-id="f7b41-168">However, sometimes you need to work with holograms that are far away from your users.</span></span> <span data-ttu-id="f7b41-169">这可以使用手动光线完成，可在 c + + 和蓝图中用作指针设备。</span><span class="sxs-lookup"><span data-stu-id="f7b41-169">This can be accomplished with hand rays, which can be used as pointing devices in both C++ and Blueprints.</span></span> <span data-ttu-id="f7b41-170">您可以从手中将一条射线绘制到远处，并在 Unreal ray 跟踪的情况下，选择一种在其他情况下不会到达的全息图。</span><span class="sxs-lookup"><span data-stu-id="f7b41-170">You can draw a ray from your hand to a far point and, with some help from Unreal ray tracing, select a hologram that would otherwise be out of reach.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="f7b41-171">由于所有函数结果都会更改每个帧，因此它们都是可调用的。</span><span class="sxs-lookup"><span data-stu-id="f7b41-171">Since all function results change every frame, they're all made callable.</span></span> <span data-ttu-id="f7b41-172">有关纯函数和非纯函数或可调用函数的详细信息，请参阅蓝图用户 guid on [函数](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)。</span><span class="sxs-lookup"><span data-stu-id="f7b41-172">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span></span>

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a><span data-ttu-id="f7b41-173">笔势</span><span class="sxs-lookup"><span data-stu-id="f7b41-173">Gestures</span></span>

<span data-ttu-id="f7b41-174">HoloLens 2 跟踪空间手势，这意味着您可以将这些手势捕获为输入。</span><span class="sxs-lookup"><span data-stu-id="f7b41-174">The HoloLens 2 tracks spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="f7b41-175">手势跟踪基于订阅模型。</span><span class="sxs-lookup"><span data-stu-id="f7b41-175">Gesture tracking is based on a subscription model.</span></span> <span data-ttu-id="f7b41-176">应使用 "配置手势" 功能告诉设备要跟踪的手势。 可以在 [HoloLens 2 基本使用](https://docs.microsoft.com/hololens/hololens2-basic-usage) 文档中找到有关手势的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="f7b41-176">You should use the “Configure Gestures” function to tell the device which gestures you want to track.  You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="f7b41-177">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="f7b41-177">Next Development Checkpoint</span></span>

<span data-ttu-id="f7b41-178">如果遵循我们的 Unreal 开发旅程，就是在探索 MRTK 核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="f7b41-178">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="f7b41-179">从这里，你可以继续执行下一个构建基块：</span><span class="sxs-lookup"><span data-stu-id="f7b41-179">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f7b41-180">本地空间定位点</span><span class="sxs-lookup"><span data-stu-id="f7b41-180">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="f7b41-181">或跳转到混合现实平台功能和 API：</span><span class="sxs-lookup"><span data-stu-id="f7b41-181">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f7b41-182">HoloLens 摄像头</span><span class="sxs-lookup"><span data-stu-id="f7b41-182">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="f7b41-183">你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks)。</span><span class="sxs-lookup"><span data-stu-id="f7b41-183">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
