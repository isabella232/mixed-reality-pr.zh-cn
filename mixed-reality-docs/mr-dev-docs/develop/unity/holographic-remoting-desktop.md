---
title: 桌面应用中的全息远程处理
description: 了解如何在桌面应用程序中通过 OpenXR 使用全息远程处理。
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr，unity，hololens，hololens 2，混合现实，MRTK，混合现实工具包，增加现实，虚拟现实，混合现实耳机，学习，教程，入门，全息远程处理，桌面
ms.openlocfilehash: f3cf43d59b74b0f47e701acc1d7312544867b0df
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624314"
---
# <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="b6c7b-104">桌面应用中的全息远程处理</span><span class="sxs-lookup"><span data-stu-id="b6c7b-104">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="b6c7b-105">0.1.3 包版本中添加了 Windows 独立应用远程处理支持。</span><span class="sxs-lookup"><span data-stu-id="b6c7b-105">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="b6c7b-106">从版本0.1.3 起，此功能不支持 UWP 生成。</span><span class="sxs-lookup"><span data-stu-id="b6c7b-106">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="b6c7b-107">按照[全息远程处理设置](openxr-supported-features.md#holographic-remoting-setup)中的步骤操作</span><span class="sxs-lookup"><span data-stu-id="b6c7b-107">Follow the steps in [Holographic Remoting setup](openxr-supported-features.md#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="b6c7b-108">打开 " **> 项目**" "设置"，导航到 "XR" " **插件管理**"，然后选中 " **Windows Mixed Reality 功能集** " 框。</span><span class="sxs-lookup"><span data-stu-id="b6c7b-108">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="b6c7b-109">另外，取消选中 " **启动时初始化 XR"**：</span><span class="sxs-lookup"><span data-stu-id="b6c7b-109">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![项目设置面板的屏幕截图在 Unity 编辑器中打开，并取消选中 "启动时初始化 XR"](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="b6c7b-111">展开 " **OpenXR** " 下的 "**功能**" 部分，然后选择 "**全部显示**"</span><span class="sxs-lookup"><span data-stu-id="b6c7b-111">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="b6c7b-112">选中 " **全息应用远程处理** " 复选框：</span><span class="sxs-lookup"><span data-stu-id="b6c7b-112">Check the **Holographic App Remoting** checkbox:</span></span>

    ![启用了应用远程处理的 Unity 编辑器中打开的项目设置面板的屏幕截图](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="b6c7b-114">接下来，编写一些代码以设置远程处理配置和触发器 XR 初始化。</span><span class="sxs-lookup"><span data-stu-id="b6c7b-114">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="b6c7b-115">使用 [混合现实 OpenXR 插件](openxr-getting-started.md#hololens-2-samples) 分发的示例应用包含 AppRemoting.cs，其中显示了在运行时连接到特定 IP 地址的示例方案。</span><span class="sxs-lookup"><span data-stu-id="b6c7b-115">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#hololens-2-samples) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="b6c7b-116">此时，将示例应用程序部署到本地计算机，将使用 "连接" 按钮显示 IP 地址输入字段。</span><span class="sxs-lookup"><span data-stu-id="b6c7b-116">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="b6c7b-117">键入 IP 地址并单击 "连接" 将初始化 XR 并尝试连接到目标设备：</span><span class="sxs-lookup"><span data-stu-id="b6c7b-117">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![示例应用显示示例应用远程处理 UI 的屏幕截图](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="b6c7b-119">若要编写自定义连接代码，请使用已填充的进行调用 `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` `RemotingConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="b6c7b-119">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="b6c7b-120">该示例应用在检查器中公开此内容，并演示如何在文本字段中填充 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="b6c7b-120">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="b6c7b-121">调用 `Connect` 将设置配置并自动初始化 XR，这就是为什么必须将其称为协同程序的原因：</span><span class="sxs-lookup"><span data-stu-id="b6c7b-121">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="b6c7b-122">运行时，可以使用 API 获取当前连接状态 `AppRemoting.TryGetConnectionState` ，还可以选择断开连接，并使用取消初始化 XR `AppRemoting.Disconnect()` 。</span><span class="sxs-lookup"><span data-stu-id="b6c7b-122">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="b6c7b-123">这可用于断开连接并重新连接到同一应用会话中的其他设备。</span><span class="sxs-lookup"><span data-stu-id="b6c7b-123">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="b6c7b-124">示例应用提供了一个 tappable 多维数据集，该多维数据集会在点击时断开远程处理会话。</span><span class="sxs-lookup"><span data-stu-id="b6c7b-124">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="b6c7b-125">从以前的 Api 迁移</span><span class="sxs-lookup"><span data-stu-id="b6c7b-125">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="b6c7b-126">UnityEngine. XR. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="b6c7b-126">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="b6c7b-127">在 [Unity 文档](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)的示例代码中：</span><span class="sxs-lookup"><span data-stu-id="b6c7b-127">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="b6c7b-128">XR.WSA.HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="b6c7b-128">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="b6c7b-129">OpenXR. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="b6c7b-129">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="b6c7b-130">[N/A：调用时自动发生 `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="b6c7b-130">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="b6c7b-131">UnityEngine. XR. WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="b6c7b-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="b6c7b-132">XR.WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="b6c7b-132">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="b6c7b-133">OpenXR. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="b6c7b-133">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="b6c7b-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` 和 `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="b6c7b-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="b6c7b-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="b6c7b-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="b6c7b-136">`AppRemoting.Connect`通过 `RemotingConfiguration` 结构传入</span><span class="sxs-lookup"><span data-stu-id="b6c7b-136">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`