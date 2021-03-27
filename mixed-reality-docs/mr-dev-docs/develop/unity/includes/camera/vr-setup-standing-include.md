---
ms.openlocfilehash: 5f990569ae4052377cba717b5526bb8ba51b8016
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636267"
---
# <a name="mrtk"></a>[<span data-ttu-id="f6c91-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="f6c91-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="f6c91-102">使用 MRTK for Unity 中的 [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace)类，并将 **目标规模** 设置为 "空间 **" 或 "** 目标"：</span><span class="sxs-lookup"><span data-stu-id="f6c91-102">Use the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to either **Room** or **Standing**:</span></span>

![MRTK 设置窗口](../../images/mrtk-target-scale.png)

<span data-ttu-id="f6c91-104">MRTK 应自动处理 playspace 和相机的位置，但最好仔细检查：</span><span class="sxs-lookup"><span data-stu-id="f6c91-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="f6c91-106">从 " **层次结构** " 面板中，展开 " **MixedRealityPlayspace** " GameObject 并查找 " **照相机** " 子对象</span><span class="sxs-lookup"><span data-stu-id="f6c91-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="f6c91-107">在 **检查器** 面板中，找到 **转换** 组件，并将 **位置** 更改为 **(X：0，Y：0，Z： 0)**</span><span class="sxs-lookup"><span data-stu-id="f6c91-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="f6c91-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="f6c91-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="f6c91-109">在 [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)上设置跟踪源模式。</span><span class="sxs-lookup"><span data-stu-id="f6c91-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="f6c91-110">获取子系统后，调用 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)：</span><span class="sxs-lookup"><span data-stu-id="f6c91-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

<span data-ttu-id="f6c91-111">和使用 Unity 的 [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)。</span><span class="sxs-lookup"><span data-stu-id="f6c91-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![层次结构中的 XR 远程测试机组](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="f6c91-113">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="f6c91-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="f6c91-114">请参阅 **Windows 应用商店播放机设置** 中的 "**其他设置**" 部分</span><span class="sxs-lookup"><span data-stu-id="f6c91-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="f6c91-115">选择 **Windows Mixed Reality** 作为设备，在较旧版本的 Unity 中，它可能作为 **Windows 全息** 列出</span><span class="sxs-lookup"><span data-stu-id="f6c91-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="f6c91-116">选择 **支持的虚拟现实**</span><span class="sxs-lookup"><span data-stu-id="f6c91-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="f6c91-117">由于主相机对象会自动标记为相机，因此 Unity 会支持移动和平移。</span><span class="sxs-lookup"><span data-stu-id="f6c91-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="f6c91-118">需要在应用的每个场景中将这些设置应用到相机。</span><span class="sxs-lookup"><span data-stu-id="f6c91-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="f6c91-119">默认情况下，当你在 Unity 中创建新场景时，它将包含层次结构中的一个主相机 GameObject，其中包括相机组件，但未正确应用下面的设置。</span><span class="sxs-lookup"><span data-stu-id="f6c91-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="f6c91-120">**命名空间：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="f6c91-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="f6c91-121">**类型：** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="f6c91-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="f6c91-122">对于 **大规模** 或 **房间规模的体验**，需要相对于楼层放置内容。</span><span class="sxs-lookup"><span data-stu-id="f6c91-122">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="f6c91-123">使用 **[空间阶段](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**（表示用户在首次运行期间设置的已定义的层级来源和可选房间边界）的原因。</span><span class="sxs-lookup"><span data-stu-id="f6c91-123">You reason about the user's floor using the **[spatial stage](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="f6c91-124">若要确保 Unity 在地面级别使用其世界坐标系统进行操作，可以设置和测试 Unity 是否正在使用 RoomScale 跟踪空间类型：</span><span class="sxs-lookup"><span data-stu-id="f6c91-124">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

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

* <span data-ttu-id="f6c91-125">如果 SetTrackingSpaceType 返回 true，则 Unity 已成功切换其世界坐标系统以跟踪 [引用的阶段框架](../../../../design/coordinate-systems.md#spatial-coordinate-systems)。</span><span class="sxs-lookup"><span data-stu-id="f6c91-125">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="f6c91-126">如果 SetTrackingSpaceType 返回 false，则 Unity 无法切换到引用的阶段框架，原因可能是用户尚未在其环境中设置楼层。</span><span class="sxs-lookup"><span data-stu-id="f6c91-126">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="f6c91-127">虽然错误的返回值不常见，但如果在不同的空间中设置了阶段，并且在用户未设置新阶段的情况下将设备移动到当前房间，则会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="f6c91-127">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="f6c91-128">应用成功设置 RoomScale 跟踪空间类型后，放置在 y = 0 平面上的内容将显示在地面上。</span><span class="sxs-lookup"><span data-stu-id="f6c91-128">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="f6c91-129">位于0，0，0的原点将是用户在房间设置期间考验的特定位置，并以-Z 表示在安装过程中的正向方向。</span><span class="sxs-lookup"><span data-stu-id="f6c91-129">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>