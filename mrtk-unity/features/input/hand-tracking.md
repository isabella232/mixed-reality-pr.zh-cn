---
title: 手部跟踪
description: 有关如何在 MRTK 中使用 HandTracking 的文档
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity，HoloLens，HoloLens 2，混合现实，开发，MRTK，手动跟踪
ms.openlocfilehash: 68e936cb4121027008f37aae72496fe59445b636
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176892"
---
# <a name="hand-tracking"></a><span data-ttu-id="8ffe4-104">手部跟踪</span><span class="sxs-lookup"><span data-stu-id="8ffe4-104">Hand tracking</span></span>

## <a name="hand-tracking-profile"></a><span data-ttu-id="8ffe4-105">手动跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="8ffe4-105">Hand tracking profile</span></span>

<span data-ttu-id="8ffe4-106">_手动跟踪配置文件_ 位于 _输入系统配置文件_ 下。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-106">The _Hand Tracking profile_ is found under the _Input System profile_.</span></span> <span data-ttu-id="8ffe4-107">它包含用于自定义手动表示形式的设置。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-107">It contains settings for customizing hand representation.</span></span>

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a><span data-ttu-id="8ffe4-108">联合 prototyping</span><span class="sxs-lookup"><span data-stu-id="8ffe4-108">Joint prefabs</span></span>

<span data-ttu-id="8ffe4-109">联合 prototyping 使用简单的 prototyping 进行可视化。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-109">Joint prefabs are visualized using simple prefabs.</span></span> <span data-ttu-id="8ffe4-110">_掌_ 形和 _食指_ 是特别重要的，拥有自己的 prefab，而所有其他接头共享同一 prefab。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-110">The _Palm_ and _Index Finger_ joints are of special importance and have their own prefab, while all other joints share the same prefab.</span></span>

<span data-ttu-id="8ffe4-111">默认情况下，手型 prototyping 是简单的几何基元。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-111">By default the hand joint prefabs are simple geometric primitives.</span></span> <span data-ttu-id="8ffe4-112">如果需要，可以将其替换。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-112">These can be replaced if desired.</span></span> <span data-ttu-id="8ffe4-113">如果根本没有指定 prefab，则改为创建空 [gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) 。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-113">If no prefab is specified at all, empty [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) are created instead.</span></span>

> [!WARNING]
> <span data-ttu-id="8ffe4-114">避免在联合 prototyping 中使用复杂的脚本或消耗大量的资源，因为联合对象会在每个帧上转换，并且可能会产生极高的性能开销！</span><span class="sxs-lookup"><span data-stu-id="8ffe4-114">Avoid using complex scripts or expensive rendering in joint prefabs, since joint objects are transformed on every frame and can have significant performance cost!</span></span>

<span data-ttu-id="8ffe4-115">默认手动接点表示</span><span class="sxs-lookup"><span data-stu-id="8ffe4-115">Default Hand Joint Representation</span></span> |  <span data-ttu-id="8ffe4-116">接点标签</span><span class="sxs-lookup"><span data-stu-id="8ffe4-116">Joint Labels</span></span>
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a><span data-ttu-id="8ffe4-117">手动网格 prefab</span><span class="sxs-lookup"><span data-stu-id="8ffe4-117">Hand mesh prefab</span></span>

<span data-ttu-id="8ffe4-118">如果手动跟踪设备提供了完全定义的网格数据，则使用手写网格。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-118">The hand mesh is used if fully defined mesh data is provided by the hand tracking device.</span></span> <span data-ttu-id="8ffe4-119">Prefab 中的网格呈现被设备中的数据替换，因此虚拟网格（如多维数据集）就足够了。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-119">The mesh renderable in the prefab is replaced by data from the device, so a dummy mesh such as a cube is sufficient.</span></span> <span data-ttu-id="8ffe4-120">Prefab 的材料用于手写网格。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-120">The material of the prefab is used for the hand mesh.</span></span>

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

<span data-ttu-id="8ffe4-121">手动网格显示可能会对性能产生显著影响，因此，可通过取消选中 " **启用手写显示可视化效果** " 选项来完全禁用它。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-121">Hand mesh display can have a noticeable performance impact, for this reason it can be disabled entirely by unchecking **Enable Hand Mesh Visualization** option.</span></span>

## <a name="hand-visualization-settings"></a><span data-ttu-id="8ffe4-122">手动可视化设置</span><span class="sxs-lookup"><span data-stu-id="8ffe4-122">Hand visualization settings</span></span>

<span data-ttu-id="8ffe4-123">可以通过 " *手工网格可视化模式* " 设置和 "手动转换" *可视化模式* 来关闭或打开手写网格和手动接点。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-123">The hand mesh and hand joint visualizations can be turned off or on via the *Hand Mesh Visualization Modes* setting and *Hand Joint Visualization Modes* respectively.</span></span> <span data-ttu-id="8ffe4-124">这些设置是特定于应用程序模式的，这意味着可以在编辑器中打开某些功能 (以查看与编辑器内模拟的联接，例如) ，同时在播放) 机中部署到设备 (时禁用相同的功能。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-124">These settings are application-mode specific, meaning it is possible to turn on some features while in editor (to see joints with in-editor simulation, for example) while having the same features turned off when deployed to device (in player builds).</span></span>

<span data-ttu-id="8ffe4-125">请注意，我们通常建议在编辑器中打开手动联合可视化 (，以便编辑器内模拟将显示) 的位置，并在播放机 (中同时关闭手联合可视化和手写图形可视化效果，因为它们会导致) 性能下降。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-125">Note that it's generally recommended to have hand joint visualization turned on in editor (so that in-editor simulation will show where the hand joints are), and to have both hand joint visualization and hand mesh visualization turned off in player (because they incur a performance hit).</span></span>

## <a name="scripting"></a><span data-ttu-id="8ffe4-126">脚本编写</span><span class="sxs-lookup"><span data-stu-id="8ffe4-126">Scripting</span></span>

<span data-ttu-id="8ffe4-127">可以从输入系统中为每个单独的局请求定位和旋转 [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) 。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-127">Position and rotation can be requested from the input system for each individual hand joint as a [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="8ffe4-128">此外，系统还允许访问跟随 [gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) 的访问。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-128">Alternatively the system allows access to [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) that follow the joints.</span></span> <span data-ttu-id="8ffe4-129">如果另一个 GameObject 应连续跟踪接头，这会很有用。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-129">This can be useful if another GameObject should track a joint continuously.</span></span>

<span data-ttu-id="8ffe4-130">可用接头在枚举中列出 [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) 。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-130">Available joints are listed in the [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) enum.</span></span>

> [!NOTE]
> <span data-ttu-id="8ffe4-131">当手动跟踪丢失时，接点对象会被销毁！</span><span class="sxs-lookup"><span data-stu-id="8ffe4-131">Joint object are destroyed when hand tracking is lost!</span></span> <span data-ttu-id="8ffe4-132">请确保任何使用该接点对象的脚本都 `null` 可以适当地处理这种情况，以免出现错误！</span><span class="sxs-lookup"><span data-stu-id="8ffe4-132">Make sure that any scripts using the joint object handle the `null` case gracefully to avoid errors!</span></span>

### <a name="accessing-a-given-hand-controller"></a><span data-ttu-id="8ffe4-133">访问给定的手形控制器</span><span class="sxs-lookup"><span data-stu-id="8ffe4-133">Accessing a given hand controller</span></span>

<span data-ttu-id="8ffe4-134">在处理输入事件时，可以使用特定的手动控制器。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-134">A specific hand controller is often available, e.g. when handling input events.</span></span> <span data-ttu-id="8ffe4-135">在这种情况下，可以使用接口直接从设备请求联合数据 [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) 。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-135">In this case the joint data can be requested directly from the device, using the [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interface.</span></span>

#### <a name="polling-joint-pose-from-controller"></a><span data-ttu-id="8ffe4-136">轮询控制器的接点姿势</span><span class="sxs-lookup"><span data-stu-id="8ffe4-136">Polling joint pose from controller</span></span>

<span data-ttu-id="8ffe4-137">[`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) `false` 如果由于某种原因而导致请求的联合不可用，则该函数将返回。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-137">The [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) function returns `false` if the requested joint is not available for some reason.</span></span> <span data-ttu-id="8ffe4-138">在这种情况下，生成的姿势将为 [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) 。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-138">In that case the resulting pose will be [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity).</span></span>

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var hand = eventData.Controller as IMixedRealityHand;
  if (hand != null)
  {
    if (hand.TryGetJoint(TrackedHandJoint.IndexTip, out MixedRealityPose jointPose)
    {
      // ...
    }
  }
}
```

#### <a name="joint-transform-from-hand-visualizer"></a><span data-ttu-id="8ffe4-139">手动可视化工具的联合转换</span><span class="sxs-lookup"><span data-stu-id="8ffe4-139">Joint transform from hand visualizer</span></span>

<span data-ttu-id="8ffe4-140">可以从 [控制器可视化工具](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer)请求联合对象。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-140">Joint objects can be requested from the [controller visualizer](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).</span></span>

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var handVisualizer = eventData.Controller.Visualizer as IMixedRealityHandVisualizer;
  if (handVisualizer != null)
  {
    if (handVisualizer.TryGetJointTransform(TrackedHandJoint.IndexTip, out Transform jointTransform)
    {
      // ...
    }
  }
}
```

### <a name="simplified-joint-data-access"></a><span data-ttu-id="8ffe4-141">简化的联合数据访问</span><span class="sxs-lookup"><span data-stu-id="8ffe4-141">Simplified joint data access</span></span>

<span data-ttu-id="8ffe4-142">如果未提供任何特定控制器，则提供实用工具类以方便访问手动联合数据。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-142">If no specific controller is given then utility classes are provided for convenient access to hand joint data.</span></span> <span data-ttu-id="8ffe4-143">这些函数请求当前跟踪的第一个可用设备的联合数据。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-143">These functions request joint data from the first available hand device currently tracked.</span></span>

#### <a name="polling-joint-pose-from-handjointutils"></a><span data-ttu-id="8ffe4-144">轮询来自 HandJointUtils 的接头姿势</span><span class="sxs-lookup"><span data-stu-id="8ffe4-144">Polling joint pose from HandJointUtils</span></span>

<span data-ttu-id="8ffe4-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) 是一个静态类，用于查询第一个活动的设备。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) is a static class that queries the first active hand device.</span></span>

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a><span data-ttu-id="8ffe4-146">从手联合服务的联合转换</span><span class="sxs-lookup"><span data-stu-id="8ffe4-146">Joint transform from hand joint service</span></span>

<span data-ttu-id="8ffe4-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) 为跟踪接头保留一组持久的 [gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) 。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) keeps a persistent set of [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) for tracking joints.</span></span>

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a><span data-ttu-id="8ffe4-148">手动跟踪事件</span><span class="sxs-lookup"><span data-stu-id="8ffe4-148">Hand tracking events</span></span>

<span data-ttu-id="8ffe4-149">如果不需要直接从控制器轮询数据，则输入系统还会提供事件。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-149">The input system provides events as well, if polling data from controllers directly is not desirable.</span></span>

#### <a name="joint-events"></a><span data-ttu-id="8ffe4-150">联合事件</span><span class="sxs-lookup"><span data-stu-id="8ffe4-150">Joint events</span></span>

<span data-ttu-id="8ffe4-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) 处理接点位置的更新。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) handles updates of joint positions.</span></span>

```c#
public class MyHandJointEventHandler : IMixedRealityHandJointHandler
{
    public Handedness myHandedness;

    void IMixedRealityHandJointHandler.OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            if (eventData.InputData.TryGetValue(TrackedHandJoint.IndexTip, out MixedRealityPose pose))
            {
                // ...
            }
        }
    }
}
```

#### <a name="mesh-events"></a><span data-ttu-id="8ffe4-152">网格事件</span><span class="sxs-lookup"><span data-stu-id="8ffe4-152">Mesh events</span></span>

<span data-ttu-id="8ffe4-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) 处理所表述的手写网格的更改。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) handles changes of the articulated hand mesh.</span></span>

<span data-ttu-id="8ffe4-154">请注意，默认情况下不启用手头网格。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-154">Note that hand meshes are not enabled by default.</span></span>

```c#
public class MyHandMeshEventHandler : IMixedRealityHandMeshHandler
{
    public Handedness myHandedness;
    public Mesh myMesh;

    public void OnHandMeshUpdated(InputEventData<HandMeshInfo> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            myMesh.vertices = eventData.InputData.vertices;
            myMesh.normals = eventData.InputData.normals;
            myMesh.triangles = eventData.InputData.triangles;

            if (eventData.InputData.uvs != null && eventData.InputData.uvs.Length > 0)
            {
                myMesh.uv = eventData.InputData.uvs;
            }

            // ...
        }
    }
}
```

## <a name="known-issues"></a><span data-ttu-id="8ffe4-155">已知问题</span><span class="sxs-lookup"><span data-stu-id="8ffe4-155">Known issues</span></span>

### <a name="net-native"></a><span data-ttu-id="8ffe4-156">.NET Native</span><span class="sxs-lookup"><span data-stu-id="8ffe4-156">.NET Native</span></span>

<span data-ttu-id="8ffe4-157">使用 .NET 后端时，主版本目前有一个已知问题。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-157">There is currently a known issue with Master builds using the .NET backend.</span></span> <span data-ttu-id="8ffe4-158">在 .NET Native 中， `IInspectable` 无法使用将指针从本机封送到托管代码 `Marshal.GetObjectForIUnknown` 。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-158">In .NET Native, `IInspectable` pointers cannot be marshaled from native to managed code using `Marshal.GetObjectForIUnknown`.</span></span> <span data-ttu-id="8ffe4-159">MRTK 使用此来获取，以便 `SpatialCoordinateSystem` 从平台接收手写数据。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-159">The MRTK uses this to obtain the `SpatialCoordinateSystem` in order to receive hand and eye data from the platform.</span></span>

<span data-ttu-id="8ffe4-160">在[本机混合现实 Toolkit](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround)存储库中，我们提供了 DLL 源作为此问题的解决方法。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-160">We've provided DLL source as a workaround for this issue, in [the native Mixed Reality Toolkit repo](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround).</span></span> <span data-ttu-id="8ffe4-161">请按照自述文件中的说明进行操作，并将生成的二进制文件复制到 Unity 资产的插件文件夹中。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-161">Please follow the instructions in the README there and copy the resulting binaries into a Plugins folder in your Unity assets.</span></span> <span data-ttu-id="8ffe4-162">之后，MRTK 中提供的 WindowsMixedRealityUtilities 脚本将解决此问题。</span><span class="sxs-lookup"><span data-stu-id="8ffe4-162">After that, the WindowsMixedRealityUtilities script provided in the MRTK will resolve the workaround for you.</span></span>

<span data-ttu-id="8ffe4-163">如果要创建自己的 DLL 或在现有 DLL 中包含此解决方法，解决方法的核心是：</span><span class="sxs-lookup"><span data-stu-id="8ffe4-163">If you want to create your own DLL or include this workaround in an existing one, the core of the workaround is:</span></span>

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

<span data-ttu-id="8ffe4-164">在 c # Unity 代码中使用它：</span><span class="sxs-lookup"><span data-stu-id="8ffe4-164">And its use in your C# Unity code:</span></span>

```c#
[DllImport("DotNetNativeWorkaround.dll", EntryPoint = "MarshalIInspectable")]
private static extern void GetSpatialCoordinateSystem(IntPtr nativePtr, out SpatialCoordinateSystem coordinateSystem);

private static SpatialCoordinateSystem GetSpatialCoordinateSystem(IntPtr nativePtr)
{
    try
    {
        GetSpatialCoordinateSystem(nativePtr, out SpatialCoordinateSystem coordinateSystem);
        return coordinateSystem;
    }
    catch
    {
        UnityEngine.Debug.LogError("Call to the DotNetNativeWorkaround plug-in failed. The plug-in is required for correct behavior when using .NET Native compilation");
        return Marshal.GetObjectForIUnknown(nativePtr) as SpatialCoordinateSystem;
    }
}
```
