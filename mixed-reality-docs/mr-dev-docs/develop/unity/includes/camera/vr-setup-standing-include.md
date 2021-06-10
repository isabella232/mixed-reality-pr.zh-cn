---
ms.openlocfilehash: 61fe8754192c1fbd0634fd9d1e1994327599321b
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748544"
---
# <a name="mrtk"></a>[<span data-ttu-id="8a02b-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="8a02b-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="8a02b-102">使用 MRTK for Unity 中的 [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace)类，将"目标刻度"设置为"房间"**或**"长期 **"：** </span><span class="sxs-lookup"><span data-stu-id="8a02b-102">Use the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to either **Room** or **Standing**:</span></span>

![MRTK 设置窗口](../../images/mrtk-target-scale.png)

<span data-ttu-id="8a02b-104">MRTK 应自动处理播放空间和相机的位置，但请仔细检查：</span><span class="sxs-lookup"><span data-stu-id="8a02b-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="8a02b-106">在" **层次结构"面板** 中，展开 **"MixedRealityPlayspace** GameObject"并找到 **"主相机"** 子对象</span><span class="sxs-lookup"><span data-stu-id="8a02b-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="8a02b-107">在"**检查器**"面板中，找到 **"转换**"组件，将"位置"更改为 (**X： 0， Y： 0， Z： 0)**</span><span class="sxs-lookup"><span data-stu-id="8a02b-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="8a02b-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="8a02b-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="8a02b-109">在 [XRInputSubsystem 上设置跟踪源模式](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)。</span><span class="sxs-lookup"><span data-stu-id="8a02b-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="8a02b-110">获取子系统后，调用 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)：</span><span class="sxs-lookup"><span data-stu-id="8a02b-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

<span data-ttu-id="8a02b-111">使用 Unity 的 [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)。</span><span class="sxs-lookup"><span data-stu-id="8a02b-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![层次结构中的 XR 演练](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="8a02b-113">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="8a02b-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="8a02b-114">转到 Windows **应用商店播放器** 设置 **的其他设置部分**</span><span class="sxs-lookup"><span data-stu-id="8a02b-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="8a02b-115">选择 **Windows Mixed Reality** 作为设备，在旧版 Unity 中可能会列为 **Windows Holographic**</span><span class="sxs-lookup"><span data-stu-id="8a02b-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="8a02b-116">选择 **"支持的虚拟现实"**</span><span class="sxs-lookup"><span data-stu-id="8a02b-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="8a02b-117">由于主相机对象自动标记为照相机，Unity 支持所有移动和转换。</span><span class="sxs-lookup"><span data-stu-id="8a02b-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="8a02b-118">需要在应用的每个场景中将这些设置应用于相机。</span><span class="sxs-lookup"><span data-stu-id="8a02b-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="8a02b-119">默认情况下，在 Unity 中创建新场景时，它将在层次结构中包含主相机 GameObject，其中包括相机组件，但没有正确应用以下设置。</span><span class="sxs-lookup"><span data-stu-id="8a02b-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="8a02b-120">\**命名空间\*\*\*：UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="8a02b-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="8a02b-121">\**类型\*\*\*：XRDevice*</span><span class="sxs-lookup"><span data-stu-id="8a02b-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="8a02b-122">若要 **获得长期缩放\*\*\*\*或房间** 缩放体验，需要相对于楼层放置内容。</span><span class="sxs-lookup"><span data-stu-id="8a02b-122">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="8a02b-123">使用空间阶段 来推理用户楼层，该 **[](../../../../design/coordinate-systems.md#spatial-coordinate-systems)** 空间阶段表示用户在首次运行期间设置的已定义的楼层原点和可选房间边界。</span><span class="sxs-lookup"><span data-stu-id="8a02b-123">You reason about the user's floor using the **[spatial stage](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="8a02b-124">若要确保 Unity 使用其世界坐标系在楼层运行，可以设置并测试 Unity 是否正在使用 RoomScale 跟踪空间类型：</span><span class="sxs-lookup"><span data-stu-id="8a02b-124">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

* <span data-ttu-id="8a02b-125">如果 SetTrackingSpaceType 返回 true，Unity 已成功切换其世界坐标系，以跟踪 [引用 的阶段框架](../../../../design/coordinate-systems.md#spatial-coordinate-systems)。</span><span class="sxs-lookup"><span data-stu-id="8a02b-125">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="8a02b-126">如果 SetTrackingSpaceType 返回 false，Unity 将无法切换到引用的阶段框架，原因可能是用户尚未设置其环境中楼层。</span><span class="sxs-lookup"><span data-stu-id="8a02b-126">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="8a02b-127">虽然 false 返回值并不常见，但如果在不同房间中设置了阶段，并且设备移动到当前房间，而用户未设置新阶段，则可能会发生此情况。</span><span class="sxs-lookup"><span data-stu-id="8a02b-127">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="8a02b-128">应用成功设置 RoomScale 跟踪空间类型后，放置在 y=0 平面上的内容将显示在楼层上。</span><span class="sxs-lookup"><span data-stu-id="8a02b-128">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="8a02b-129">0、0、0 的原点将是用户在房间设置期间在楼层中旋转的特定位置，-Z 表示他们在安装过程中面向的向前方向。</span><span class="sxs-lookup"><span data-stu-id="8a02b-129">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>