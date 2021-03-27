---
ms.openlocfilehash: c7e5be36420ef14fe5aaeaafb49c0a990942339f
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636266"
---
# <a name="mrtk"></a>[<span data-ttu-id="87009-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="87009-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="87009-102">使用 MRTK for Unity 中的 [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 类，并将 **目标规模** 设置为 " **固定**"：</span><span class="sxs-lookup"><span data-stu-id="87009-102">Use the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **Seated**:</span></span>

![MRTK 设置窗口](../../images/mrtk-target-scale.png)

<span data-ttu-id="87009-104">MRTK 应自动处理 playspace 和相机的位置，但最好仔细检查：</span><span class="sxs-lookup"><span data-stu-id="87009-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="87009-106">从 " **层次结构** " 面板中，展开 " **MixedRealityPlayspace** " GameObject 并查找 " **照相机** " 子对象</span><span class="sxs-lookup"><span data-stu-id="87009-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="87009-107">在 **检查器** 面板中，找到 **转换** 组件，并将 **位置** 更改为 **(X：0，Y：0，Z： 0)**</span><span class="sxs-lookup"><span data-stu-id="87009-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="87009-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="87009-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="87009-109">在 [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)上设置跟踪源模式。</span><span class="sxs-lookup"><span data-stu-id="87009-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="87009-110">获取子系统后，调用 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)：</span><span class="sxs-lookup"><span data-stu-id="87009-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

<span data-ttu-id="87009-111">和使用 Unity 的 [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)。</span><span class="sxs-lookup"><span data-stu-id="87009-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![层次结构中的 XR 远程测试机组](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="87009-113">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="87009-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="87009-114">请参阅 **Windows 应用商店播放机设置** 中的 "**其他设置**" 部分</span><span class="sxs-lookup"><span data-stu-id="87009-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="87009-115">选择 **Windows Mixed Reality** 作为设备，在较旧版本的 Unity 中，它可能作为 **Windows 全息** 列出</span><span class="sxs-lookup"><span data-stu-id="87009-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="87009-116">选择 **支持的虚拟现实**</span><span class="sxs-lookup"><span data-stu-id="87009-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="87009-117">由于主相机对象会自动标记为相机，因此 Unity 会支持移动和平移。</span><span class="sxs-lookup"><span data-stu-id="87009-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="87009-118">需要在应用的每个场景中将这些设置应用到相机。</span><span class="sxs-lookup"><span data-stu-id="87009-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="87009-119">默认情况下，当你在 Unity 中创建新场景时，它将包含层次结构中的一个主相机 GameObject，其中包括相机组件，但未正确应用下面的设置。</span><span class="sxs-lookup"><span data-stu-id="87009-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="87009-120">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="87009-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="87009-121">**类型：** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="87009-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="87009-122">若要生成 **仅限方向** 或 **固定规模的体验**，需将 Unity 设置为静止跟踪空间类型。</span><span class="sxs-lookup"><span data-stu-id="87009-122">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="87009-123">静止跟踪空间会将 Unity 的世界坐标系统设置为跟踪 [固定的引用框架](../../../../design/coordinate-systems.md#spatial-coordinate-systems)。</span><span class="sxs-lookup"><span data-stu-id="87009-123">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="87009-124">在静止跟踪模式下，显示在面板默认位置之前的编辑器中的内容 (向前) 在应用启动时将显示在用户的前面。</span><span class="sxs-lookup"><span data-stu-id="87009-124">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="87009-125">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="87009-125">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="87009-126">**类型：** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="87009-126">**Type:** *InputTracking*</span></span>

<span data-ttu-id="87009-127">对于纯粹的 **仅限方向的体验** ，例如360度的视频查看器 (其中位置标题更新会破坏错觉) ，可以设置 [XR。InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) 为 true：</span><span class="sxs-lookup"><span data-stu-id="87009-127">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="87009-128">对于 **大规模体验**，若要让用户在以后 recenter 原位置，可以调用 [XR。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 方法：</span><span class="sxs-lookup"><span data-stu-id="87009-128">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

<span data-ttu-id="87009-129">如果要构建大规模的 [体验](../../../../design/coordinate-systems.md)，可以通过调用 XR，在用户的当前头部位置 recenter Unity 的世界原点 **[。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法。</span><span class="sxs-lookup"><span data-stu-id="87009-129">If you're building a [seated-scale experience](../../../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>