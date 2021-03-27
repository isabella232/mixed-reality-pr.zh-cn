---
ms.openlocfilehash: 7470690a96380184ead7319d4461005042c6db82
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636256"
---
# <a name="mrtk"></a>[<span data-ttu-id="ab794-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="ab794-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="ab794-102">按照此 [分步教程](../../tutorials/mr-learning-base-01.md) 在 Unity 项目中添加和自动配置混合现实工具包。</span><span class="sxs-lookup"><span data-stu-id="ab794-102">Follow this [step-by-step tutorial](../../tutorials/mr-learning-base-01.md) to add and automatically configure Mixed Reality Toolkit in your Unity project.</span></span> <span data-ttu-id="ab794-103">还可以直接使用 MRTK for Unity 中的 [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) 类，并将 **目标规模** 设置为 **World**：</span><span class="sxs-lookup"><span data-stu-id="ab794-103">It's also possible to work directly with the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **World**:</span></span>

![MRTK 设置窗口](../../images/mrtk-target-scale.png)

<span data-ttu-id="ab794-105">MRTK 应自动处理 playspace 和相机的位置，但最好仔细检查：</span><span class="sxs-lookup"><span data-stu-id="ab794-105">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="ab794-107">从 " **层次结构** " 面板中，展开 " **MixedRealityPlayspace** " GameObject 并查找 " **照相机** " 子对象</span><span class="sxs-lookup"><span data-stu-id="ab794-107">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="ab794-108">在 **检查器** 面板中，找到 **转换** 组件，并将 **位置** 更改为 **(X：0，Y：0，Z： 0)**</span><span class="sxs-lookup"><span data-stu-id="ab794-108">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="ab794-109">XR SDK</span><span class="sxs-lookup"><span data-stu-id="ab794-109">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="ab794-110">在 [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)上设置跟踪源模式。</span><span class="sxs-lookup"><span data-stu-id="ab794-110">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="ab794-111">获取子系统后，调用 [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)：</span><span class="sxs-lookup"><span data-stu-id="ab794-111">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

<span data-ttu-id="ab794-112">可以将 [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) 用于 HoloLens 应用程序，该应用程序可以更好地使用定位点和 ARKit/ARCore。</span><span class="sxs-lookup"><span data-stu-id="ab794-112">You can use [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) for HoloLens applications, which works better with anchors and ARKit/ARCore.</span></span>

![层次结构中的 AR 会话](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> <span data-ttu-id="ab794-114">AR 会话和相关功能需要安装 AR Foundation。</span><span class="sxs-lookup"><span data-stu-id="ab794-114">AR Session and related features need AR Foundation installed.</span></span>

<span data-ttu-id="ab794-115">在不使用 ARSession 的情况下，也可以手动应用相机变化：</span><span class="sxs-lookup"><span data-stu-id="ab794-115">It's also possible to apply the camera changes manually without using ARSession:</span></span>

1. <span data-ttu-id="ab794-116">选择 "**层次结构**" 面板中的 "**主相机**"</span><span class="sxs-lookup"><span data-stu-id="ab794-116">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="ab794-117">在 **检查器** 面板中，找到 **转换** 组件，并将 **位置** 更改为 **(X：0，Y：0，Z： 0)**</span><span class="sxs-lookup"><span data-stu-id="ab794-117">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="ab794-118">![Unity 中的 "检查器" 窗格中的照相机](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="ab794-118">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="ab794-119">*Unity 中的 "检查器" 窗格中的照相机*</span><span class="sxs-lookup"><span data-stu-id="ab794-119">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="ab794-120">将 **TrackedPoseDriver** 添加到 **主摄像机**</span><span class="sxs-lookup"><span data-stu-id="ab794-120">Add a **TrackedPoseDriver** to the **Main Camera**</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="ab794-121">旧 WSA</span><span class="sxs-lookup"><span data-stu-id="ab794-121">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="ab794-122">选择 "**层次结构**" 面板中的 "**主相机**"</span><span class="sxs-lookup"><span data-stu-id="ab794-122">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="ab794-123">在 **检查器** 面板中，找到 **转换** 组件，并将 **位置** 更改为 **(X：0，Y：0，Z： 0)**</span><span class="sxs-lookup"><span data-stu-id="ab794-123">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="ab794-124">![Unity 中的 "检查器" 窗格中的照相机](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="ab794-124">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="ab794-125">*Unity 中的 "检查器" 窗格中的照相机*</span><span class="sxs-lookup"><span data-stu-id="ab794-125">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="ab794-126">请参阅 **Windows 应用商店播放机设置** 中的 "**其他设置**" 部分</span><span class="sxs-lookup"><span data-stu-id="ab794-126">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
1. <span data-ttu-id="ab794-127">选择 **Windows Mixed Reality** 作为设备，在较旧版本的 Unity 中，它可能作为 **Windows 全息** 列出</span><span class="sxs-lookup"><span data-stu-id="ab794-127">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
1. <span data-ttu-id="ab794-128">选择 **支持的虚拟现实**</span><span class="sxs-lookup"><span data-stu-id="ab794-128">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="ab794-129">由于主相机对象会自动标记为相机，因此 Unity 会支持移动和平移。</span><span class="sxs-lookup"><span data-stu-id="ab794-129">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="ab794-130">需要在应用的每个场景中将这些设置应用到相机。</span><span class="sxs-lookup"><span data-stu-id="ab794-130">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="ab794-131">默认情况下，当你在 Unity 中创建新场景时，它将包含层次结构中的一个主相机 GameObject，其中包括相机组件，但可能未正确应用这些设置。</span><span class="sxs-lookup"><span data-stu-id="ab794-131">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but may not have the settings properly applied.</span></span>