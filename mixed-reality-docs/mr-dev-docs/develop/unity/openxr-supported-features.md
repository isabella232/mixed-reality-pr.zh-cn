---
title: OpenXR 插件支持 Unity 中的功能
description: 发现 OpenXR 支持 Unity 中混合现实开发的功能。
author: hferrone
ms.author: alexturn
ms.date: 12/15/2020
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，扩充现实，虚拟现实，混合现实耳机，学习，教程，入门
ms.openlocfilehash: dc908762d6e44e04f56b8ff82b90394106ca42e5
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2020
ms.locfileid: "97622897"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="bad66-104">混合现实 OpenXR 支持 Unity 中的功能</span><span class="sxs-lookup"><span data-stu-id="bad66-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="bad66-105">**Mixed Reality OpenXR 插件** 包是 Unity 的 **OpenXR 插件** 的扩展，支持用于 HoloLens 2 和 Windows Mixed Reality 耳机的一套功能。</span><span class="sxs-lookup"><span data-stu-id="bad66-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="bad66-106">继续之前，请确保已安装 **Unity 2020.2** 或更高版本， **OpenXR 插件版本 0.1.1** 或更高版本，并且 Unity 项目已 [配置为 OpenXR](openxr-getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="bad66-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.1** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="bad66-107">支持的操作</span><span class="sxs-lookup"><span data-stu-id="bad66-107">What's supported</span></span>

<span data-ttu-id="bad66-108">目前支持以下功能：</span><span class="sxs-lookup"><span data-stu-id="bad66-108">The following features are currently supported:</span></span>

* <span data-ttu-id="bad66-109">支持适用于 Windows Mixed Reality 耳机的适用于 HoloLens 2 和 Win32 VR 应用程序的 UWP 应用程序。</span><span class="sxs-lookup"><span data-stu-id="bad66-109">Supports both UWP applications for HoloLens 2 and Win32 VR applications for Windows Mixed Reality headsets.</span></span>
* <span data-ttu-id="bad66-110">为 HoloLens 2 应用程序优化 UWP 包和 CoreWindow 交互。</span><span class="sxs-lookup"><span data-stu-id="bad66-110">Optimizes UWP package and CoreWindow interaction for HoloLens 2 applications.</span></span>
* <span data-ttu-id="bad66-111">使用定位点和无限空间进行世界规模跟踪。</span><span class="sxs-lookup"><span data-stu-id="bad66-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="bad66-112">用于将定位点保存到 HoloLens 2 本地存储的定位存储 API。</span><span class="sxs-lookup"><span data-stu-id="bad66-112">Anchor storage API to persist anchors to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="bad66-113">运动控制器和手动交互，包括新的 HP 回音 G2 控制器。</span><span class="sxs-lookup"><span data-stu-id="bad66-113">Motion controller and hand interactions, including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="bad66-114">使用26个接合和接点输入的有向右跟踪。</span><span class="sxs-lookup"><span data-stu-id="bad66-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="bad66-115">HoloLens 2 上的目视注视交互。</span><span class="sxs-lookup"><span data-stu-id="bad66-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="bad66-116">在 HoloLens 2 上查找 (PV) 相机的照片/视频。</span><span class="sxs-lookup"><span data-stu-id="bad66-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="bad66-117">混合现实通过 PV 相机使用第三种目视渲染来捕获。</span><span class="sxs-lookup"><span data-stu-id="bad66-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="bad66-118">支持使用全息远程处理应用 "播放" 到 HoloLens 2，使开发人员无需生成并部署到设备即可调试脚本。</span><span class="sxs-lookup"><span data-stu-id="bad66-118">Supports "Play" to HoloLens 2 using the Holographic Remoting app, allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="bad66-119">与 MRTK Unity 2.5.2 通过 MRTK OpenXR 适配器包兼容。</span><span class="sxs-lookup"><span data-stu-id="bad66-119">Compatible with MRTK Unity 2.5.2 through MRTK OpenXR adapter package.</span></span> <missing link>
* <span data-ttu-id="bad66-120">与 Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 或更高版本兼容</span><span class="sxs-lookup"><span data-stu-id="bad66-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later</span></span>

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="bad66-121">Unity 编辑器播放模式下的全息远程处理</span><span class="sxs-lookup"><span data-stu-id="bad66-121">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="bad66-122">在 Visual Studio 项目中生成 UWP Unity 项目，然后将其打包并部署到 HoloLens 2 设备可能需要一些时间。</span><span class="sxs-lookup"><span data-stu-id="bad66-122">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="bad66-123">一种解决方法是启用全息编辑器远程处理，这使你能够通过网络将 "播放" 模式直接调试到 HoloLens 2 设备的 c # 脚本。</span><span class="sxs-lookup"><span data-stu-id="bad66-123">One solution is to enable the Holographic Editor Remoting, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="bad66-124">此方案可避免生成 UWP 包并将其部署到远程设备的系统开销。</span><span class="sxs-lookup"><span data-stu-id="bad66-124">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="bad66-125">首先，需要在 HoloLens 2 上从应用商店[安装全息远程处理播放器应用](https://www.microsoft.com/store/productId/9NBLGGH4SV40)</span><span class="sxs-lookup"><span data-stu-id="bad66-125">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from Store on your HoloLens 2</span></span>  
2. <span data-ttu-id="bad66-126">在 HoloLens 2 上运行全息远程处理播放器应用程序，你将看到要连接到的版本号和 IP 地址</span><span class="sxs-lookup"><span data-stu-id="bad66-126">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="bad66-127">你需要使用版本2.4 或更高版本才能使用 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="bad66-127">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

![HoloLens 中运行的全息远程处理播放机的屏幕截图](images/openxr-features-img-01.png)

3. <span data-ttu-id="bad66-129">打开 " **> 项目**" "设置"，导航到 "XR" " **插件管理**"，然后选中 " **Windows Mixed Reality 功能集** " 框：</span><span class="sxs-lookup"><span data-stu-id="bad66-129">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-features-img-02.png)

4. <span data-ttu-id="bad66-131">展开 " **OpenXR** " 下的 "**功能**" 部分，然后选择 "**全部显示**"</span><span class="sxs-lookup"><span data-stu-id="bad66-131">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
5. <span data-ttu-id="bad66-132">选中 " **全息编辑器远程处理** " 复选框并输入从全息远程处理应用获取的 IP 地址：</span><span class="sxs-lookup"><span data-stu-id="bad66-132">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了功能](images/openxr-features-img-03.png)

<span data-ttu-id="bad66-134">现在，你可以单击 "播放" 按钮，将 Unity 应用播放到 HoloLens 上的全息远程处理应用。</span><span class="sxs-lookup"><span data-stu-id="bad66-134">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="bad66-135">还可以 [将 Visual Studio 连接到 Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) ，以便在播放模式下调试 c # 脚本。</span><span class="sxs-lookup"><span data-stu-id="bad66-135">You can also [attach Visual Studio to Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="bad66-136">0.1.0 的版本不支持全息远程处理，运行时不支持定位点功能，ARAnchorManager 功能将无法通过远程处理。</span><span class="sxs-lookup"><span data-stu-id="bad66-136">As of version 0.1.0 the Holographic Remoting, runtime doesn’t support Anchor feature, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="bad66-137">此功能即将推出。</span><span class="sxs-lookup"><span data-stu-id="bad66-137">This feature is coming in future releases.</span></span>

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="bad66-138">运动控制器和手动交互</span><span class="sxs-lookup"><span data-stu-id="bad66-138">Motion controller and hand interactions</span></span>
<span data-ttu-id="bad66-139">若要了解有关 Unity 中混合现实交互的基础知识，请访问 unity [手动 For UNITY XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)。</span><span class="sxs-lookup"><span data-stu-id="bad66-139">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="bad66-140">此 Unity 文档介绍了如何将特定于控制器的输入映射到更具可归纳的 `InputFeatureUsage` ，如何识别和分类可用的 XR 输入，如何从这些输入中读取数据等。</span><span class="sxs-lookup"><span data-stu-id="bad66-140">This Unity documentation covers the mappings from controller-specific inputs to more generalizable `InputFeatureUsage`s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span> 
 
<span data-ttu-id="bad66-141">Mixed Reality OpenXR 插件提供附加的输入交互配置文件，这些配置文件映射到标准， `InputFeatureUsage` 如下所述：</span><span class="sxs-lookup"><span data-stu-id="bad66-141">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard `InputFeatureUsage`s as detailed below:</span></span> 
 
| `InputFeatureUsage` | <span data-ttu-id="bad66-142">HP 回音 G2 控制器 (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="bad66-142">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="bad66-143">HoloLens 手型 (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="bad66-143">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="bad66-144">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="bad66-144">primary2DAxis</span></span> | <span data-ttu-id="bad66-145">操纵杆</span><span class="sxs-lookup"><span data-stu-id="bad66-145">Joystick</span></span> | |
| <span data-ttu-id="bad66-146">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="bad66-146">primary2DAxisClick</span></span> | <span data-ttu-id="bad66-147">游戏杆-单击</span><span class="sxs-lookup"><span data-stu-id="bad66-147">Joystick - Click</span></span> | |
| <span data-ttu-id="bad66-148">触发器</span><span class="sxs-lookup"><span data-stu-id="bad66-148">trigger</span></span> | <span data-ttu-id="bad66-149">触发器</span><span class="sxs-lookup"><span data-stu-id="bad66-149">Trigger</span></span>  | |
| <span data-ttu-id="bad66-150">调整</span><span class="sxs-lookup"><span data-stu-id="bad66-150">grip</span></span> | <span data-ttu-id="bad66-151">调整</span><span class="sxs-lookup"><span data-stu-id="bad66-151">Grip</span></span> | <span data-ttu-id="bad66-152">空中分流或挤压</span><span class="sxs-lookup"><span data-stu-id="bad66-152">Air tap or squeeze</span></span> |
| <span data-ttu-id="bad66-153">primaryButton</span><span class="sxs-lookup"><span data-stu-id="bad66-153">primaryButton</span></span> | <span data-ttu-id="bad66-154">[X/A]-按</span><span class="sxs-lookup"><span data-stu-id="bad66-154">[X/A] - Press</span></span> | <span data-ttu-id="bad66-155">隔空敲击</span><span class="sxs-lookup"><span data-stu-id="bad66-155">Air tap</span></span> |
| <span data-ttu-id="bad66-156">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="bad66-156">secondaryButton</span></span> | <span data-ttu-id="bad66-157">[Y/B]-按</span><span class="sxs-lookup"><span data-stu-id="bad66-157">[Y/B] - Press</span></span> | |
| <span data-ttu-id="bad66-158">gripButton</span><span class="sxs-lookup"><span data-stu-id="bad66-158">gripButton</span></span> | <span data-ttu-id="bad66-159">手柄-按</span><span class="sxs-lookup"><span data-stu-id="bad66-159">Grip - Press</span></span> | |
| <span data-ttu-id="bad66-160">triggerButton</span><span class="sxs-lookup"><span data-stu-id="bad66-160">triggerButton</span></span> | <span data-ttu-id="bad66-161">触发器-按</span><span class="sxs-lookup"><span data-stu-id="bad66-161">Trigger - Press</span></span> | |
| <span data-ttu-id="bad66-162">menuButton</span><span class="sxs-lookup"><span data-stu-id="bad66-162">menuButton</span></span> | <span data-ttu-id="bad66-163">菜单</span><span class="sxs-lookup"><span data-stu-id="bad66-163">Menu</span></span> | |

#### <a name="haptics"></a><span data-ttu-id="bad66-164">Haptics</span><span class="sxs-lookup"><span data-stu-id="bad66-164">Haptics</span></span>
<span data-ttu-id="bad66-165">有关在 Unity 的 XR 输入系统中使用 haptics 的信息，请参阅 unity [XR 输入-haptics 的 Unity 手册](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)中的文档。</span><span class="sxs-lookup"><span data-stu-id="bad66-165">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span> 


## <a name="whats-coming-soon"></a><span data-ttu-id="bad66-166">即将推出的内容</span><span class="sxs-lookup"><span data-stu-id="bad66-166">What's coming soon</span></span>

<span data-ttu-id="bad66-167">以下问题和缺少的功能是通过混合现实 OpenXR 插件 **版本 0.1.0** 知道的。</span><span class="sxs-lookup"><span data-stu-id="bad66-167">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="bad66-168">我们正在处理这些问题，将在即将发布的版本中发布修补程序和新功能。</span><span class="sxs-lookup"><span data-stu-id="bad66-168">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="bad66-169">尚不支持 **ARPlaneSubsystem** 。</span><span class="sxs-lookup"><span data-stu-id="bad66-169">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="bad66-170">HoloLens 2 上还不支持 **ARPlaneManager**、 **ARRAYCASTMANAGER** 和相关 API，如 **ARAnchorManager。**</span><span class="sxs-lookup"><span data-stu-id="bad66-170">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="bad66-171">全息远程处理尚不支持 **定位点**，但不久后会推出。</span><span class="sxs-lookup"><span data-stu-id="bad66-171">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="bad66-172">目前尚不支持 **手写** 跟踪、 **QR 码** 和 **XRMeshSubsystem** 。</span><span class="sxs-lookup"><span data-stu-id="bad66-172">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="bad66-173">未来版本中将提供 **Azure 空间锚点** 支持。</span><span class="sxs-lookup"><span data-stu-id="bad66-173">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="bad66-174">**ARM64** 是仅适用于 HoloLens 2 应用的受支持平台。</span><span class="sxs-lookup"><span data-stu-id="bad66-174">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="bad66-175">**ARM** 平台即将发布。</span><span class="sxs-lookup"><span data-stu-id="bad66-175">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="bad66-176">疑难解答</span><span class="sxs-lookup"><span data-stu-id="bad66-176">Troubleshooting</span></span> 

<span data-ttu-id="bad66-177">当你在 HoloLens 2 上挂起和恢复 Unity 应用时，该应用无法正确恢复，这将导致在 HoloLens 视图中显示4个旋转点。</span><span class="sxs-lookup"><span data-stu-id="bad66-177">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span> 
* <span data-ttu-id="bad66-178">将 OpenXR 项目设置中的 " **深度提交模式** " 设置为 " **无** " 作为一种解决方法</span><span class="sxs-lookup"><span data-stu-id="bad66-178">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
