---
title: OpenXR 插件支持 Unity 中的功能
description: 发现 OpenXR 支持 Unity 中混合现实开发的功能。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，扩充现实，虚拟现实，混合现实耳机，学习，教程，入门
ms.openlocfilehash: bad18c5f30465120bce370aa91c13ff3f229bef6
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496128"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="abc8f-104">混合现实 OpenXR 支持 Unity 中的功能</span><span class="sxs-lookup"><span data-stu-id="abc8f-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="abc8f-105">**Mixed Reality OpenXR 插件** 包是 Unity 的 **OpenXR 插件** 的扩展，支持用于 HoloLens 2 和 Windows Mixed Reality 耳机的一套功能。</span><span class="sxs-lookup"><span data-stu-id="abc8f-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="abc8f-106">继续之前，请确保已安装 **Unity 2020.2** 或更高版本， **OpenXR 插件版本 0.1.3** 或更高版本，并且 Unity 项目已 [配置为 OpenXR](openxr-getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="abc8f-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.3** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="abc8f-107">支持的操作</span><span class="sxs-lookup"><span data-stu-id="abc8f-107">What's supported</span></span>

<span data-ttu-id="abc8f-108">目前支持以下功能：</span><span class="sxs-lookup"><span data-stu-id="abc8f-108">The following features are currently supported:</span></span>

* <span data-ttu-id="abc8f-109">支持 HoloLens 2 的 UWP 应用程序，并针对 HoloLens 2 应用程序模型进行优化。</span><span class="sxs-lookup"><span data-stu-id="abc8f-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="abc8f-110">支持适用于 Windows Mixed Reality 耳机的 Win32 VR 应用程序，包含最新控制器配置文件和全息应用远程处理。</span><span class="sxs-lookup"><span data-stu-id="abc8f-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="abc8f-111">使用定位点和无限空间进行世界规模跟踪。</span><span class="sxs-lookup"><span data-stu-id="abc8f-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="abc8f-112">[用于将定位点保存](#anchors-and-anchor-persistence) 到 HoloLens 2 本地存储的定位存储 API。</span><span class="sxs-lookup"><span data-stu-id="abc8f-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="abc8f-113">[运动控制器和手动交互](#motion-controller-and-hand-interactions)，包括新的 HP 回音 G2 控制器。</span><span class="sxs-lookup"><span data-stu-id="abc8f-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="abc8f-114">使用26个接合和接点输入的有向右跟踪。</span><span class="sxs-lookup"><span data-stu-id="abc8f-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="abc8f-115">HoloLens 2 上的目视注视交互。</span><span class="sxs-lookup"><span data-stu-id="abc8f-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="abc8f-116">在 HoloLens 2 上查找 (PV) 相机的照片/视频。</span><span class="sxs-lookup"><span data-stu-id="abc8f-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="abc8f-117">混合现实通过 PV 相机使用第三种目视渲染来捕获。</span><span class="sxs-lookup"><span data-stu-id="abc8f-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="abc8f-118">支持 [通过全息远程处理应用 "播放" 到 HoloLens 2](#holographic-remoting-in-unity-editor-play-mode)，使开发人员无需生成并部署到设备即可调试脚本。</span><span class="sxs-lookup"><span data-stu-id="abc8f-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="abc8f-119">与 MRTK Unity 2.5.3 和更高版本通过 [MRTK OpenXR 提供程序支持](openxr-getting-started.md#using-mrtk-with-openxr-support)兼容。</span><span class="sxs-lookup"><span data-stu-id="abc8f-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="abc8f-120">与 Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 或更高版本兼容。</span><span class="sxs-lookup"><span data-stu-id="abc8f-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="abc8f-121"> (在 0.1.3) 中添加的功能支持从生成和部署的 Windows 独立应用进行 [桌面应用全息远程处理](#holographic-remoting-in-desktop-app) 。</span><span class="sxs-lookup"><span data-stu-id="abc8f-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](#holographic-remoting-in-desktop-app) from a built and deployed Windows Standalone app.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="abc8f-122">全息远程处理安装</span><span class="sxs-lookup"><span data-stu-id="abc8f-122">Holographic Remoting setup</span></span>

1. <span data-ttu-id="abc8f-123">首先，需要从 HoloLens 2 上的 Microsoft Store[安装全息远程处理播放器应用程序](https://www.microsoft.com/store/productId/9NBLGGH4SV40)</span><span class="sxs-lookup"><span data-stu-id="abc8f-123">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="abc8f-124">在 HoloLens 2 上运行全息远程处理播放器应用程序，你将看到要连接到的版本号和 IP 地址</span><span class="sxs-lookup"><span data-stu-id="abc8f-124">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="abc8f-125">你需要使用版本2.4 或更高版本才能使用 OpenXR 插件</span><span class="sxs-lookup"><span data-stu-id="abc8f-125">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens 中运行的全息远程处理播放机的屏幕截图](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="abc8f-127">Unity 编辑器播放模式下的全息远程处理</span><span class="sxs-lookup"><span data-stu-id="abc8f-127">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="abc8f-128">在 Visual Studio 项目中生成 UWP Unity 项目，然后将其打包并部署到 HoloLens 2 设备可能需要一些时间。</span><span class="sxs-lookup"><span data-stu-id="abc8f-128">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="abc8f-129">一种解决方案是启用全息编辑器远程处理功能，该功能使你能够通过网络将 "播放" 模式直接调试到 HoloLens 2 设备。</span><span class="sxs-lookup"><span data-stu-id="abc8f-129">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="abc8f-130">此方案可避免生成 UWP 包并将其部署到远程设备的系统开销。</span><span class="sxs-lookup"><span data-stu-id="abc8f-130">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="abc8f-131">按照[全息远程处理设置](#holographic-remoting-setup)中的步骤操作</span><span class="sxs-lookup"><span data-stu-id="abc8f-131">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="abc8f-132">打开 " **> 项目**" "设置"，导航到 "XR" " **插件管理**"，然后选中 " **Windows Mixed Reality 功能集** " 框：</span><span class="sxs-lookup"><span data-stu-id="abc8f-132">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了 XR 插件管理](images/openxr-features-img-02.png)

3. <span data-ttu-id="abc8f-134">展开 " **OpenXR** " 下的 "**功能**" 部分，然后选择 "**全部显示**"</span><span class="sxs-lookup"><span data-stu-id="abc8f-134">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="abc8f-135">选中 " **全息编辑器远程处理** " 复选框并输入从全息远程处理应用获取的 IP 地址：</span><span class="sxs-lookup"><span data-stu-id="abc8f-135">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![在 Unity 编辑器中打开的项目设置面板的屏幕截图，其中突出显示了功能](images/openxr-features-img-03.png)

<span data-ttu-id="abc8f-137">现在，你可以单击 "播放" 按钮，将 Unity 应用播放到 HoloLens 上的全息远程处理应用。</span><span class="sxs-lookup"><span data-stu-id="abc8f-137">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="abc8f-138">还可以 [将 Visual Studio 连接到 Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) ，以便在播放模式下调试 c # 脚本。</span><span class="sxs-lookup"><span data-stu-id="abc8f-138">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="abc8f-139">从版本0.1.0 起，全息远程处理运行时不支持定位点，并且 ARAnchorManager 功能将无法通过远程处理。</span><span class="sxs-lookup"><span data-stu-id="abc8f-139">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="abc8f-140">此功能即将推出。</span><span class="sxs-lookup"><span data-stu-id="abc8f-140">This feature is coming in future releases.</span></span>

## <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="abc8f-141">桌面应用中的全息远程处理</span><span class="sxs-lookup"><span data-stu-id="abc8f-141">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="abc8f-142">0.1.3 包版本中添加了 Windows 独立应用远程处理支持。</span><span class="sxs-lookup"><span data-stu-id="abc8f-142">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="abc8f-143">从版本0.1.3 起，此功能不支持 UWP 生成。</span><span class="sxs-lookup"><span data-stu-id="abc8f-143">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="abc8f-144">按照[全息远程处理设置](#holographic-remoting-setup)中的步骤操作</span><span class="sxs-lookup"><span data-stu-id="abc8f-144">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="abc8f-145">打开 " **> 项目**" "设置"，导航到 "XR" " **插件管理**"，然后选中 " **Windows Mixed Reality 功能集** " 框。</span><span class="sxs-lookup"><span data-stu-id="abc8f-145">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="abc8f-146">另外，取消选中 " **启动时初始化 XR"**：</span><span class="sxs-lookup"><span data-stu-id="abc8f-146">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![项目设置面板的屏幕截图在 Unity 编辑器中打开，并取消选中 "启动时初始化 XR"](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="abc8f-148">展开 " **OpenXR** " 下的 "**功能**" 部分，然后选择 "**全部显示**"</span><span class="sxs-lookup"><span data-stu-id="abc8f-148">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="abc8f-149">选中 " **全息应用远程处理** " 复选框：</span><span class="sxs-lookup"><span data-stu-id="abc8f-149">Check the **Holographic App Remoting** checkbox:</span></span>

    ![启用了应用远程处理的 Unity 编辑器中打开的项目设置面板的屏幕截图](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="abc8f-151">接下来，编写一些代码以设置远程处理配置和触发器 XR 初始化。</span><span class="sxs-lookup"><span data-stu-id="abc8f-151">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="abc8f-152">使用 [混合现实 OpenXR 插件](openxr-getting-started.md#hololens-2-samples) 分发的示例应用包含 AppRemoting.cs，其中显示了在运行时连接到特定 IP 地址的示例方案。</span><span class="sxs-lookup"><span data-stu-id="abc8f-152">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#hololens-2-samples) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="abc8f-153">此时，将示例应用程序部署到本地计算机，将使用 "连接" 按钮显示 IP 地址输入字段。</span><span class="sxs-lookup"><span data-stu-id="abc8f-153">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="abc8f-154">键入 IP 地址并单击 "连接" 将初始化 XR 并尝试连接到目标设备：</span><span class="sxs-lookup"><span data-stu-id="abc8f-154">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![示例应用显示示例应用远程处理 UI 的屏幕截图](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="abc8f-156">若要编写自定义连接代码，请使用已填充的进行调用 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` `RemotingConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="abc8f-156">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="abc8f-157">该示例应用在检查器中公开此内容，并演示如何在文本字段中填充 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="abc8f-157">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="abc8f-158">调用 `Connect` 将设置配置并自动初始化 XR，这就是为什么必须将其称为协同程序的原因：</span><span class="sxs-lookup"><span data-stu-id="abc8f-158">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="abc8f-159">运行时，可以使用 API 获取当前连接状态 `AppRemoting.TryGetConnectionState` ，还可以选择断开连接，并使用取消初始化 XR `AppRemoting.Disconnect()` 。</span><span class="sxs-lookup"><span data-stu-id="abc8f-159">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="abc8f-160">这可用于断开连接并重新连接到同一应用会话中的其他设备。</span><span class="sxs-lookup"><span data-stu-id="abc8f-160">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="abc8f-161">示例应用提供了一个 tappable 多维数据集，该多维数据集会在点击时断开远程处理会话。</span><span class="sxs-lookup"><span data-stu-id="abc8f-161">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="abc8f-162">从以前的 Api 迁移</span><span class="sxs-lookup"><span data-stu-id="abc8f-162">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="abc8f-163">UnityEngine. XR. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="abc8f-163">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="abc8f-164">在 [Unity 文档](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)的示例代码中：</span><span class="sxs-lookup"><span data-stu-id="abc8f-164">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="abc8f-165">XR.WSA.HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="abc8f-165">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="abc8f-166">OpenXR. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="abc8f-166">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="abc8f-167">[N/A：调用时自动发生 `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="abc8f-167">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="abc8f-168">UnityEngine. XR. WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="abc8f-168">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="abc8f-169">XR.WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="abc8f-169">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="abc8f-170">OpenXR. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="abc8f-170">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="abc8f-171">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` 和 `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="abc8f-171">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="abc8f-172">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="abc8f-172">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="abc8f-173">`AppRemoting.Connect`通过 `RemotingConfiguration` 结构传入</span><span class="sxs-lookup"><span data-stu-id="abc8f-173">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="abc8f-174">定位点和定位点持久性</span><span class="sxs-lookup"><span data-stu-id="abc8f-174">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="abc8f-175">Mixed Reality OpenXR 插件通过实现 Unity 的 ARFoundation **ARAnchorManager** 提供基本的定位点功能。</span><span class="sxs-lookup"><span data-stu-id="abc8f-175">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="abc8f-176">若要了解有关 ARFoundation 中 **ARAnchor** 的基础知识，请访问 [AR 定位管理器的 ARFoundation 手册](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)。</span><span class="sxs-lookup"><span data-stu-id="abc8f-176">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="abc8f-177">从版本0.1.0，此插件支持除创建附加到某一平面的定位点之外的所有 ARAnchorManager 功能，后者将在将来的版本中推出。</span><span class="sxs-lookup"><span data-stu-id="abc8f-177">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="abc8f-178">定位点持久性和 XRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="abc8f-178">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="abc8f-179">另外一个名为 **XRAnchorStore** 的 API 允许在会话之间保留定位点。</span><span class="sxs-lookup"><span data-stu-id="abc8f-179">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="abc8f-180">XRAnchorStore 是设备上保存的定位点的表示形式。</span><span class="sxs-lookup"><span data-stu-id="abc8f-180">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="abc8f-181">定位点可以从 Unity 场景中的 **ARAnchors** 保存、从存储加载到新 **ARAnchors** 或从存储中删除。</span><span class="sxs-lookup"><span data-stu-id="abc8f-181">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="abc8f-182">这些定位点将保存并加载到同一设备上。</span><span class="sxs-lookup"><span data-stu-id="abc8f-182">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="abc8f-183">未来版本中将通过 Azure 空间锚点支持跨设备锚定存储。</span><span class="sxs-lookup"><span data-stu-id="abc8f-183">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="abc8f-184">若要加载 XRAnchorStore，该插件会在 XRAnchorSubsystem （ARAnchorManager 的子系统）上提供扩展方法：</span><span class="sxs-lookup"><span data-stu-id="abc8f-184">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="abc8f-185">若要使用此扩展方法，请按如下所示从 ARAnchorManager 的子系统访问它：</span><span class="sxs-lookup"><span data-stu-id="abc8f-185">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="abc8f-186">若要查看保留/unpersisting 定位点的完整示例，请查看 [Mixed Reality OpenXR 插件示例场景](openxr-getting-started.md#hololens-2-samples)中的定位点 > 锚样品 GameObject 和 AnchorsSample.cs 脚本：</span><span class="sxs-lookup"><span data-stu-id="abc8f-186">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![在 Unity 编辑器中打开的 "层次结构" 面板的屏幕截图，其中突出显示了定位点示例](images/openxr-features-img-04.png)

![在 Unity 编辑器中打开的检查器面板屏幕截图，其中突出显示了定位点示例脚本](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="abc8f-189">运动控制器和手动交互</span><span class="sxs-lookup"><span data-stu-id="abc8f-189">Motion controller and hand interactions</span></span>

<span data-ttu-id="abc8f-190">若要了解有关 Unity 中混合现实交互的基础知识，请访问 unity [手动 For UNITY XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)。</span><span class="sxs-lookup"><span data-stu-id="abc8f-190">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="abc8f-191">此 Unity 文档介绍了从特定于控制器的输入到更可归纳的 **InputFeatureUsage** 的映射，如何识别和分类可用的 XR 输入，如何从这些输入中读取数据等。</span><span class="sxs-lookup"><span data-stu-id="abc8f-191">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="abc8f-192">Mixed Reality OpenXR 插件提供附加的输入交互配置文件，这些配置文件映射到标准 **InputFeatureUsage**，如下所述：</span><span class="sxs-lookup"><span data-stu-id="abc8f-192">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="abc8f-193">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="abc8f-193">InputFeatureUsage</span></span> | <span data-ttu-id="abc8f-194">HP 回音 G2 控制器 (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="abc8f-194">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="abc8f-195">HoloLens 手型 (OpenXR) </span><span class="sxs-lookup"><span data-stu-id="abc8f-195">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="abc8f-196">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="abc8f-196">primary2DAxis</span></span> | <span data-ttu-id="abc8f-197">操纵杆</span><span class="sxs-lookup"><span data-stu-id="abc8f-197">Joystick</span></span> | |
| <span data-ttu-id="abc8f-198">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="abc8f-198">primary2DAxisClick</span></span> | <span data-ttu-id="abc8f-199">游戏杆-单击</span><span class="sxs-lookup"><span data-stu-id="abc8f-199">Joystick - Click</span></span> | |
| <span data-ttu-id="abc8f-200">触发器</span><span class="sxs-lookup"><span data-stu-id="abc8f-200">trigger</span></span> | <span data-ttu-id="abc8f-201">触发器</span><span class="sxs-lookup"><span data-stu-id="abc8f-201">Trigger</span></span>  | |
| <span data-ttu-id="abc8f-202">调整</span><span class="sxs-lookup"><span data-stu-id="abc8f-202">grip</span></span> | <span data-ttu-id="abc8f-203">调整</span><span class="sxs-lookup"><span data-stu-id="abc8f-203">Grip</span></span> | <span data-ttu-id="abc8f-204">空中分流或挤压</span><span class="sxs-lookup"><span data-stu-id="abc8f-204">Air tap or squeeze</span></span> |
| <span data-ttu-id="abc8f-205">primaryButton</span><span class="sxs-lookup"><span data-stu-id="abc8f-205">primaryButton</span></span> | <span data-ttu-id="abc8f-206">[X/A]-按</span><span class="sxs-lookup"><span data-stu-id="abc8f-206">[X/A] - Press</span></span> | <span data-ttu-id="abc8f-207">隔空敲击</span><span class="sxs-lookup"><span data-stu-id="abc8f-207">Air tap</span></span> |
| <span data-ttu-id="abc8f-208">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="abc8f-208">secondaryButton</span></span> | <span data-ttu-id="abc8f-209">[Y/B]-按</span><span class="sxs-lookup"><span data-stu-id="abc8f-209">[Y/B] - Press</span></span> | |
| <span data-ttu-id="abc8f-210">gripButton</span><span class="sxs-lookup"><span data-stu-id="abc8f-210">gripButton</span></span> | <span data-ttu-id="abc8f-211">手柄-按</span><span class="sxs-lookup"><span data-stu-id="abc8f-211">Grip - Press</span></span> | |
| <span data-ttu-id="abc8f-212">triggerButton</span><span class="sxs-lookup"><span data-stu-id="abc8f-212">triggerButton</span></span> | <span data-ttu-id="abc8f-213">触发器-按</span><span class="sxs-lookup"><span data-stu-id="abc8f-213">Trigger - Press</span></span> | |
| <span data-ttu-id="abc8f-214">menuButton</span><span class="sxs-lookup"><span data-stu-id="abc8f-214">menuButton</span></span> | <span data-ttu-id="abc8f-215">菜单</span><span class="sxs-lookup"><span data-stu-id="abc8f-215">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="abc8f-216">瞄准并抓住姿势</span><span class="sxs-lookup"><span data-stu-id="abc8f-216">Aim and Grip Poses</span></span>

<span data-ttu-id="abc8f-217">通过 OpenXR 输入交互可以访问两组姿势：</span><span class="sxs-lookup"><span data-stu-id="abc8f-217">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="abc8f-218">用于呈现对象的手柄姿势</span><span class="sxs-lookup"><span data-stu-id="abc8f-218">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="abc8f-219">目标是指进入世界。</span><span class="sxs-lookup"><span data-stu-id="abc8f-219">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="abc8f-220">有关此设计的详细信息以及这两个姿势之间的差异，请参阅 [OpenXR 规范输入子路径](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)。</span><span class="sxs-lookup"><span data-stu-id="abc8f-220">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="abc8f-221">InputFeatureUsages **DevicePosition**、 **DeviceRotation**、 **DeviceVelocity** 和 **DeviceAngularVelocity** 提供的姿势都代表了 OpenXR **手柄** 的姿势。</span><span class="sxs-lookup"><span data-stu-id="abc8f-221">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="abc8f-222">与手柄姿势相关的 InputFeatureUsages 在 Unity 的 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)中定义。</span><span class="sxs-lookup"><span data-stu-id="abc8f-222">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="abc8f-223">InputFeatureUsages **PointerPosition**、 **PointerRotation**、 **PointerVelocity** 和 **PointerAngularVelocity** 提供的姿势均代表 OpenXR **aim** 姿势。</span><span class="sxs-lookup"><span data-stu-id="abc8f-223">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="abc8f-224">这些 InputFeatureUsages 未在包含的任何 c # 文件中定义，因此你需要定义自己的 InputFeatureUsages，如下所示：</span><span class="sxs-lookup"><span data-stu-id="abc8f-224">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="abc8f-225">Haptics</span><span class="sxs-lookup"><span data-stu-id="abc8f-225">Haptics</span></span>

<span data-ttu-id="abc8f-226">有关在 Unity 的 XR 输入系统中使用 haptics 的信息，请参阅 unity [XR 输入-haptics 的 Unity 手册](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)中的文档。</span><span class="sxs-lookup"><span data-stu-id="abc8f-226">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="abc8f-227">即将推出的内容</span><span class="sxs-lookup"><span data-stu-id="abc8f-227">What's coming soon</span></span>

<span data-ttu-id="abc8f-228">以下问题和缺少的功能是通过混合现实 OpenXR 插件 **版本 0.1.0** 知道的。</span><span class="sxs-lookup"><span data-stu-id="abc8f-228">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="abc8f-229">我们正在处理这些问题，将在即将发布的版本中发布修补程序和新功能。</span><span class="sxs-lookup"><span data-stu-id="abc8f-229">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="abc8f-230">尚不支持 **ARPlaneSubsystem** 。</span><span class="sxs-lookup"><span data-stu-id="abc8f-230">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="abc8f-231">HoloLens 2 上还不支持 **ARPlaneManager**、 **ARRAYCASTMANAGER** 和相关 API，如 **ARAnchorManager。**</span><span class="sxs-lookup"><span data-stu-id="abc8f-231">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="abc8f-232">全息远程处理尚不支持 **定位点**，但不久后会推出。</span><span class="sxs-lookup"><span data-stu-id="abc8f-232">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="abc8f-233">目前尚不支持 **手写** 跟踪、 **QR 码** 和 **XRMeshSubsystem** 。</span><span class="sxs-lookup"><span data-stu-id="abc8f-233">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="abc8f-234">未来版本中将提供 **Azure 空间锚点** 支持。</span><span class="sxs-lookup"><span data-stu-id="abc8f-234">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="abc8f-235">**ARM64** 是仅适用于 HoloLens 2 应用的受支持平台。</span><span class="sxs-lookup"><span data-stu-id="abc8f-235">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="abc8f-236">**ARM** 平台即将发布。</span><span class="sxs-lookup"><span data-stu-id="abc8f-236">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="abc8f-237">疑难解答</span><span class="sxs-lookup"><span data-stu-id="abc8f-237">Troubleshooting</span></span>

<span data-ttu-id="abc8f-238">当你在 HoloLens 2 上挂起和恢复 Unity 应用时，该应用无法正确恢复，这将导致在 HoloLens 视图中显示4个旋转点。</span><span class="sxs-lookup"><span data-stu-id="abc8f-238">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="abc8f-239">将 OpenXR 项目设置中的 " **深度提交模式** " 设置为 " **无** " 作为一种解决方法</span><span class="sxs-lookup"><span data-stu-id="abc8f-239">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
