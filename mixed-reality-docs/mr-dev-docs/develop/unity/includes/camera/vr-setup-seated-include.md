---
ms.openlocfilehash: 3bffb5db8f4a36d04c2b408c939cbd2010a7def7
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748466"
---
# <a name="mrtk"></a>[<span data-ttu-id="1ed5b-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="1ed5b-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="1ed5b-102">使用 MRTK for Unity 中的 [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace)类，将"目标 **刻度"设置为\*\*\*\*"固定"：**</span><span class="sxs-lookup"><span data-stu-id="1ed5b-102">Use the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **Seated**:</span></span>

![MRTK 设置窗口](../../images/mrtk-target-scale.png)

<span data-ttu-id="1ed5b-104">MRTK 应自动处理播放空间和相机的位置，但请仔细检查：</span><span class="sxs-lookup"><span data-stu-id="1ed5b-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="1ed5b-106">在" **层次结构"面板** 中，展开 **"MixedRealityPlayspace** GameObject"并找到 **"主相机"** 子对象</span><span class="sxs-lookup"><span data-stu-id="1ed5b-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="1ed5b-107">在"**检查器**"面板中，找到 **"转换**"组件，将"位置"更改为 (**X： 0， Y： 0， Z： 0)**</span><span class="sxs-lookup"><span data-stu-id="1ed5b-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="1ed5b-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="1ed5b-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="1ed5b-109">在 [XRInputSubsystem 上设置跟踪源模式](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)。</span><span class="sxs-lookup"><span data-stu-id="1ed5b-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="1ed5b-110">获取子系统后，调用 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)：</span><span class="sxs-lookup"><span data-stu-id="1ed5b-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

<span data-ttu-id="1ed5b-111">使用 Unity 的 [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)。</span><span class="sxs-lookup"><span data-stu-id="1ed5b-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![层次结构中的 XR 演练](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="1ed5b-113">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="1ed5b-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="1ed5b-114">转到 Windows **应用商店播放器** 设置 **的其他设置部分**</span><span class="sxs-lookup"><span data-stu-id="1ed5b-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="1ed5b-115">选择 **Windows Mixed Reality** 作为设备，在旧版 Unity 中可能会列为 **Windows Holographic**</span><span class="sxs-lookup"><span data-stu-id="1ed5b-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="1ed5b-116">选择 **"支持的虚拟现实"**</span><span class="sxs-lookup"><span data-stu-id="1ed5b-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="1ed5b-117">由于主相机对象自动标记为照相机，Unity 支持所有移动和转换。</span><span class="sxs-lookup"><span data-stu-id="1ed5b-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="1ed5b-118">需要在应用的每个场景中将这些设置应用于相机。</span><span class="sxs-lookup"><span data-stu-id="1ed5b-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="1ed5b-119">默认情况下，在 Unity 中创建新场景时，它将在层次结构中包含主相机 GameObject，其中包括相机组件，但没有正确应用以下设置。</span><span class="sxs-lookup"><span data-stu-id="1ed5b-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="1ed5b-120">\**命名空间\*\*\*：UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="1ed5b-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="1ed5b-121">\**类型\*\*\*：XRDevice*</span><span class="sxs-lookup"><span data-stu-id="1ed5b-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="1ed5b-122">若要构建 **仅方向或\*\*\*\*方向缩放** 体验，需要将 Unity 设置为"固定跟踪空间"类型。</span><span class="sxs-lookup"><span data-stu-id="1ed5b-122">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="1ed5b-123">固定跟踪空间设置 Unity 世界坐标系以跟踪 [固定参考框架](../../../../design/coordinate-systems.md#spatial-coordinate-systems)。</span><span class="sxs-lookup"><span data-stu-id="1ed5b-123">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="1ed5b-124">在"固定跟踪"模式下，当应用启动时，编辑器中位于相机默认位置前面的内容 (向前是 -Z) 会显示在用户的前面。</span><span class="sxs-lookup"><span data-stu-id="1ed5b-124">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="1ed5b-125">\**命名空间\*\*\*：UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="1ed5b-125">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="1ed5b-126">\**类型\*\*\*：InputTracking*</span><span class="sxs-lookup"><span data-stu-id="1ed5b-126">**Type:** *InputTracking*</span></span>

<span data-ttu-id="1ed5b-127">对于纯方向体验（如 360 度视频查看器 (位置头部更新会破坏假象) ，可以设置[XR。InputTracking.disablePositionalTracking 为](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html)true：</span><span class="sxs-lookup"><span data-stu-id="1ed5b-127">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="1ed5b-128">若要 **获得固定缩放体验**，若要让用户稍后更晚地获得源，可以调用 [XR。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 方法：</span><span class="sxs-lookup"><span data-stu-id="1ed5b-128">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

<span data-ttu-id="1ed5b-129">如果要构建一种 [步进缩放](../../../../design/coordinate-systems.md)体验，可以通过调用 XR，在用户的当前头部位置使用最新的 Unity 世界 **[原点。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法。</span><span class="sxs-lookup"><span data-stu-id="1ed5b-129">If you're building a [seated-scale experience](../../../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>