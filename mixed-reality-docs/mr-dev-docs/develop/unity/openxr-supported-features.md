---
title: OpenXR 插件支持 Unity 中的功能
description: 发现 OpenXR 支持 Unity 中混合现实开发的功能。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，扩充现实，虚拟现实，混合现实耳机，学习，教程，入门
ms.openlocfilehash: 1c9e185c63d3efef66cdc2782d8d8d4e3692c705
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623627"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="6bddb-104">混合现实 OpenXR 支持 Unity 中的功能</span><span class="sxs-lookup"><span data-stu-id="6bddb-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="6bddb-105">**Mixed Reality OpenXR 插件** 包是 Unity 的 **OpenXR 插件** 的扩展，支持用于 HoloLens 2 和 Windows Mixed Reality 耳机的一套功能。</span><span class="sxs-lookup"><span data-stu-id="6bddb-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="6bddb-106">继续之前，请确保已安装 **Unity 2020.2** 或更高版本， **OpenXR 插件版本 0.1.3** 或更高版本，并且 Unity 项目已 [配置为 OpenXR](openxr-getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="6bddb-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.3** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="6bddb-107">支持的操作</span><span class="sxs-lookup"><span data-stu-id="6bddb-107">What's supported</span></span>

<span data-ttu-id="6bddb-108">目前支持以下功能：</span><span class="sxs-lookup"><span data-stu-id="6bddb-108">The following features are currently supported:</span></span>

* <span data-ttu-id="6bddb-109">支持 HoloLens 2 的 UWP 应用程序，并针对 HoloLens 2 应用程序模型进行优化。</span><span class="sxs-lookup"><span data-stu-id="6bddb-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="6bddb-110">支持适用于 Windows Mixed Reality 耳机的 Win32 VR 应用程序，包含最新控制器配置文件和全息应用远程处理。</span><span class="sxs-lookup"><span data-stu-id="6bddb-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="6bddb-111">使用定位点和无限空间进行世界规模跟踪。</span><span class="sxs-lookup"><span data-stu-id="6bddb-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="6bddb-112">[用于将定位点保存](spatial-anchors-in-unity.md) 到 HoloLens 2 本地存储的定位存储 API。</span><span class="sxs-lookup"><span data-stu-id="6bddb-112">[Anchor storage API to persist anchors](spatial-anchors-in-unity.md) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="6bddb-113">[运动控制器和手动交互](#motion-controller-and-hand-interactions)，包括新的 HP 回音 G2 控制器。</span><span class="sxs-lookup"><span data-stu-id="6bddb-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="6bddb-114">使用26个接合和接点输入的有向右跟踪。</span><span class="sxs-lookup"><span data-stu-id="6bddb-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="6bddb-115">HoloLens 2 上的目视注视交互。</span><span class="sxs-lookup"><span data-stu-id="6bddb-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="6bddb-116">在 HoloLens 2 上查找 (PV) 相机的照片/视频。</span><span class="sxs-lookup"><span data-stu-id="6bddb-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="6bddb-117">混合现实通过 PV 相机使用第三种目视渲染来捕获。</span><span class="sxs-lookup"><span data-stu-id="6bddb-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="6bddb-118">支持 [通过全息远程处理应用 "播放" 到 HoloLens 2](#holographic-remoting-in-unity-editor-play-mode)，使开发人员无需生成并部署到设备即可调试脚本。</span><span class="sxs-lookup"><span data-stu-id="6bddb-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="6bddb-119">与 MRTK Unity 2.5.3 和更高版本通过 [MRTK OpenXR 提供程序支持](openxr-getting-started.md#using-mrtk-with-openxr-support)兼容。</span><span class="sxs-lookup"><span data-stu-id="6bddb-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="6bddb-120">与 Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 或更高版本兼容。</span><span class="sxs-lookup"><span data-stu-id="6bddb-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="6bddb-121"> (在 0.1.3) 中添加的功能支持从生成和部署的 Windows 独立应用进行 [桌面应用全息远程处理](holographic-remoting-desktop.md) 。</span><span class="sxs-lookup"><span data-stu-id="6bddb-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](holographic-remoting-desktop.md) from a built and deployed Windows Standalone app.</span></span>
* <span data-ttu-id="6bddb-122">在 0.1.4) 中添加 (支持通过 SpatialGraphNode 在 HoloLens2 上进行[QR 代码跟踪](#qr-codes)</span><span class="sxs-lookup"><span data-stu-id="6bddb-122">(Added in 0.1.4) Supports [QR code tracking](#qr-codes) on HoloLens2 through SpatialGraphNode</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="6bddb-123">全息远程处理安装</span><span class="sxs-lookup"><span data-stu-id="6bddb-123">Holographic Remoting setup</span></span>

1. <span data-ttu-id="6bddb-124">首先，需要从 HoloLens 2 上的 Microsoft Store[安装全息远程处理播放器应用程序](https://www.microsoft.com/store/productId/9NBLGGH4SV40)</span><span class="sxs-lookup"><span data-stu-id="6bddb-124">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="6bddb-125">在 HoloLens 2 上运行全息远程处理播放器应用程序，你将看到要连接到的版本号和 IP 地址</span><span class="sxs-lookup"><span data-stu-id="6bddb-125">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="6bddb-126">你需要使用版本2.4 或更高版本才能使用 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="6bddb-126">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens 中运行的全息远程处理播放机的屏幕截图](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="6bddb-128">Unity 编辑器播放模式下的全息远程处理</span><span class="sxs-lookup"><span data-stu-id="6bddb-128">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="6bddb-129">在 Visual Studio 项目中生成 UWP Unity 项目，然后将其打包并部署到 HoloLens 2 设备可能需要一些时间。</span><span class="sxs-lookup"><span data-stu-id="6bddb-129">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="6bddb-130">一种解决方案是启用全息编辑器远程处理功能，该功能使你能够通过网络将 "播放" 模式直接调试到 HoloLens 2 设备。</span><span class="sxs-lookup"><span data-stu-id="6bddb-130">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="6bddb-131">此方案可避免生成 UWP 包并将其部署到远程设备的系统开销。</span><span class="sxs-lookup"><span data-stu-id="6bddb-131">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="6bddb-132">按照[全息远程处理设置](#holographic-remoting-setup)中的步骤操作</span><span class="sxs-lookup"><span data-stu-id="6bddb-132">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="6bddb-133">打开 " **> 项目**" "设置"，导航到 "XR" " **插件管理**"，然后选中 " **Windows Mixed Reality 功能集** " 框：</span><span class="sxs-lookup"><span data-stu-id="6bddb-133">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-features-img-02.png)

3. <span data-ttu-id="6bddb-135">展开 " **OpenXR** " 下的 "**功能**" 部分，然后选择 "**全部显示**"</span><span class="sxs-lookup"><span data-stu-id="6bddb-135">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="6bddb-136">选中 " **全息编辑器远程处理** " 复选框并输入从全息远程处理应用获取的 IP 地址：</span><span class="sxs-lookup"><span data-stu-id="6bddb-136">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了功能](images/openxr-features-img-03.png)

<span data-ttu-id="6bddb-138">现在，你可以单击 "播放" 按钮，将 Unity 应用播放到 HoloLens 上的全息远程处理应用。</span><span class="sxs-lookup"><span data-stu-id="6bddb-138">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="6bddb-139">还可以 [将 Visual Studio 连接到 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) ，以便在播放模式下调试 c # 脚本。</span><span class="sxs-lookup"><span data-stu-id="6bddb-139">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="6bddb-140">从版本0.1.0 起，全息远程处理运行时不支持定位点，并且 ARAnchorManager 功能将无法通过远程处理。</span><span class="sxs-lookup"><span data-stu-id="6bddb-140">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="6bddb-141">此功能即将推出。</span><span class="sxs-lookup"><span data-stu-id="6bddb-141">This feature is coming in future releases.</span></span>

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="6bddb-142">运动控制器和手动交互</span><span class="sxs-lookup"><span data-stu-id="6bddb-142">Motion controller and hand interactions</span></span>

<span data-ttu-id="6bddb-143">若要了解有关 Unity 中混合现实交互的基础知识，请访问 unity [手动 For UNITY XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)。</span><span class="sxs-lookup"><span data-stu-id="6bddb-143">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="6bddb-144">此 Unity 文档介绍了从特定于控制器的输入到更可归纳的 **InputFeatureUsage** 的映射，如何识别和分类可用的 XR 输入，如何从这些输入中读取数据等。</span><span class="sxs-lookup"><span data-stu-id="6bddb-144">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="6bddb-145">Mixed Reality OpenXR 插件提供附加的输入交互配置文件，这些配置文件映射到标准 **InputFeatureUsage**，如下所述：</span><span class="sxs-lookup"><span data-stu-id="6bddb-145">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="6bddb-146">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="6bddb-146">InputFeatureUsage</span></span> | <span data-ttu-id="6bddb-147">HP 回音 G2 控制器 (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="6bddb-147">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="6bddb-148">HoloLens 手型 (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="6bddb-148">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="6bddb-149">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="6bddb-149">primary2DAxis</span></span> | <span data-ttu-id="6bddb-150">操纵杆</span><span class="sxs-lookup"><span data-stu-id="6bddb-150">Joystick</span></span> | |
| <span data-ttu-id="6bddb-151">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="6bddb-151">primary2DAxisClick</span></span> | <span data-ttu-id="6bddb-152">游戏杆-单击</span><span class="sxs-lookup"><span data-stu-id="6bddb-152">Joystick - Click</span></span> | |
| <span data-ttu-id="6bddb-153">触发器</span><span class="sxs-lookup"><span data-stu-id="6bddb-153">trigger</span></span> | <span data-ttu-id="6bddb-154">触发器</span><span class="sxs-lookup"><span data-stu-id="6bddb-154">Trigger</span></span>  | |
| <span data-ttu-id="6bddb-155">调整</span><span class="sxs-lookup"><span data-stu-id="6bddb-155">grip</span></span> | <span data-ttu-id="6bddb-156">调整</span><span class="sxs-lookup"><span data-stu-id="6bddb-156">Grip</span></span> | <span data-ttu-id="6bddb-157">空中分流或挤压</span><span class="sxs-lookup"><span data-stu-id="6bddb-157">Air tap or squeeze</span></span> |
| <span data-ttu-id="6bddb-158">primaryButton</span><span class="sxs-lookup"><span data-stu-id="6bddb-158">primaryButton</span></span> | <span data-ttu-id="6bddb-159">[X/A]-按</span><span class="sxs-lookup"><span data-stu-id="6bddb-159">[X/A] - Press</span></span> | <span data-ttu-id="6bddb-160">隔空敲击</span><span class="sxs-lookup"><span data-stu-id="6bddb-160">Air tap</span></span> |
| <span data-ttu-id="6bddb-161">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="6bddb-161">secondaryButton</span></span> | <span data-ttu-id="6bddb-162">[Y/B]-按</span><span class="sxs-lookup"><span data-stu-id="6bddb-162">[Y/B] - Press</span></span> | |
| <span data-ttu-id="6bddb-163">gripButton</span><span class="sxs-lookup"><span data-stu-id="6bddb-163">gripButton</span></span> | <span data-ttu-id="6bddb-164">手柄-按</span><span class="sxs-lookup"><span data-stu-id="6bddb-164">Grip - Press</span></span> | |
| <span data-ttu-id="6bddb-165">triggerButton</span><span class="sxs-lookup"><span data-stu-id="6bddb-165">triggerButton</span></span> | <span data-ttu-id="6bddb-166">触发器-按</span><span class="sxs-lookup"><span data-stu-id="6bddb-166">Trigger - Press</span></span> | |
| <span data-ttu-id="6bddb-167">menuButton</span><span class="sxs-lookup"><span data-stu-id="6bddb-167">menuButton</span></span> | <span data-ttu-id="6bddb-168">菜单</span><span class="sxs-lookup"><span data-stu-id="6bddb-168">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="6bddb-169">瞄准并抓住姿势</span><span class="sxs-lookup"><span data-stu-id="6bddb-169">Aim and Grip Poses</span></span>

<span data-ttu-id="6bddb-170">通过 OpenXR 输入交互可以访问两组姿势：</span><span class="sxs-lookup"><span data-stu-id="6bddb-170">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="6bddb-171">用于呈现对象的手柄姿势</span><span class="sxs-lookup"><span data-stu-id="6bddb-171">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="6bddb-172">目标是指进入世界。</span><span class="sxs-lookup"><span data-stu-id="6bddb-172">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="6bddb-173">有关此设计的详细信息以及这两个姿势之间的差异，请参阅 [OpenXR 规范输入子路径](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)。</span><span class="sxs-lookup"><span data-stu-id="6bddb-173">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="6bddb-174">InputFeatureUsages **DevicePosition**、 **DeviceRotation**、 **DeviceVelocity** 和 **DeviceAngularVelocity** 提供的姿势都代表了 OpenXR **手柄** 的姿势。</span><span class="sxs-lookup"><span data-stu-id="6bddb-174">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="6bddb-175">与手柄姿势相关的 InputFeatureUsages 在 Unity 的 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)中定义。</span><span class="sxs-lookup"><span data-stu-id="6bddb-175">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="6bddb-176">InputFeatureUsages **PointerPosition**、 **PointerRotation**、 **PointerVelocity** 和 **PointerAngularVelocity** 提供的姿势均代表 OpenXR **aim** 姿势。</span><span class="sxs-lookup"><span data-stu-id="6bddb-176">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="6bddb-177">这些 InputFeatureUsages 未在包含的任何 c # 文件中定义，因此你需要定义自己的 InputFeatureUsages，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6bddb-177">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="6bddb-178">Haptics</span><span class="sxs-lookup"><span data-stu-id="6bddb-178">Haptics</span></span>

<span data-ttu-id="6bddb-179">有关在 Unity 的 XR 输入系统中使用 haptics 的信息，请参阅 unity [XR 输入-haptics 的 Unity 手册](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)中的文档。</span><span class="sxs-lookup"><span data-stu-id="6bddb-179">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="qr-codes"></a><span data-ttu-id="6bddb-180">QR 码</span><span class="sxs-lookup"><span data-stu-id="6bddb-180">QR codes</span></span>

<span data-ttu-id="6bddb-181">HoloLens 2 可以检测头戴显示设备周围环境中的 QR 码，从而在每个代码的真实位置建立坐标系统。</span><span class="sxs-lookup"><span data-stu-id="6bddb-181">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="6bddb-182">可以在 [QR 代码跟踪](../platform-capabilities-and-apis/qr-code-tracking.md) 文档中找到更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="6bddb-182">You can find more details in our [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) documentation.</span></span>  <span data-ttu-id="6bddb-183">使用 OpenXR 插件时，请[ `SpatialGraphNodeId` 从 qr API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference)获取，并使用 `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API 来查找 QR 代码。</span><span class="sxs-lookup"><span data-stu-id="6bddb-183">When using the OpenXR plugin, grab the [`SpatialGraphNodeId` from the QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) and use the `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API to locate the QR code.</span></span>

<span data-ttu-id="6bddb-184">作为参考，[在 GitHub 上有一个 QR 跟踪示例项目](https://github.com/yl-msft/QRTracking)，其中包含了有关[ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)的详细使用说明。</span><span class="sxs-lookup"><span data-stu-id="6bddb-184">For reference, we have a [QR tracking sample project on GitHub](https://github.com/yl-msft/QRTracking) with more a detailed usage explanation for the [`SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="6bddb-185">即将推出的内容</span><span class="sxs-lookup"><span data-stu-id="6bddb-185">What's coming soon</span></span>

<span data-ttu-id="6bddb-186">以下问题和缺少的功能是通过混合现实 OpenXR 插件 **版本 0.1.0** 知道的。</span><span class="sxs-lookup"><span data-stu-id="6bddb-186">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="6bddb-187">我们正在处理这些问题，将在即将发布的版本中发布修补程序和新功能。</span><span class="sxs-lookup"><span data-stu-id="6bddb-187">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="6bddb-188">尚不支持 **ARPlaneSubsystem** 。</span><span class="sxs-lookup"><span data-stu-id="6bddb-188">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="6bddb-189">HoloLens 2 上还不支持 **ARPlaneManager**、 **ARRAYCASTMANAGER** 和相关 API，如 **ARAnchorManager。**</span><span class="sxs-lookup"><span data-stu-id="6bddb-189">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="6bddb-190">全息远程处理尚不支持 **定位点暂留**，但不久后会出现此情况。</span><span class="sxs-lookup"><span data-stu-id="6bddb-190">**Anchor persistence** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="6bddb-191">目前尚不支持 **手写网格** 跟踪和 **XRMeshSubsystem** 。</span><span class="sxs-lookup"><span data-stu-id="6bddb-191">**Hand Mesh** tracking and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="6bddb-192">未来版本中将提供 **Azure 空间锚点** 支持。</span><span class="sxs-lookup"><span data-stu-id="6bddb-192">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="6bddb-193">**ARM64** 是仅适用于 HoloLens 2 应用的受支持平台。</span><span class="sxs-lookup"><span data-stu-id="6bddb-193">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="6bddb-194">**ARM** 平台即将发布。</span><span class="sxs-lookup"><span data-stu-id="6bddb-194">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="6bddb-195">故障排除</span><span class="sxs-lookup"><span data-stu-id="6bddb-195">Troubleshooting</span></span>

<span data-ttu-id="6bddb-196">当你在 HoloLens 2 上挂起和恢复 Unity 应用时，该应用无法正确恢复，这将导致在 HoloLens 视图中显示4个旋转点。</span><span class="sxs-lookup"><span data-stu-id="6bddb-196">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="6bddb-197">将 OpenXR 项目设置中的 " **深度提交模式** " 设置为 " **无** " 作为一种解决方法</span><span class="sxs-lookup"><span data-stu-id="6bddb-197">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
