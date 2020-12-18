---
title: Unreal 中的流式传输
description: 从 Unreal 中流式传输到 HoloLens 2 的指南
author: sw5813
ms.author: suwu
ms.date: 12/7/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 流式传输, 电脑, 全息应用远程处理, 全息远程处理播放器, 文档, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 3638f07753355061f251bb2d6fa47233872d5b90
ms.sourcegitcommit: 0509cf6c57067cffd75a0189106e3369e9ecc5c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/08/2020
ms.locfileid: "96855876"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="2c9f4-104">Unreal 中的流式传输</span><span class="sxs-lookup"><span data-stu-id="2c9f4-104">Streaming in Unreal</span></span>

<span data-ttu-id="2c9f4-105">从电脑流式传输到 HoloLens 提供了两大优势：</span><span class="sxs-lookup"><span data-stu-id="2c9f4-105">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="2c9f4-106">它使混合现实应用可以利用电脑的计算能力。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-106">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="2c9f4-107">它有助于加快开发迭代的时间。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-107">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="2c9f4-108">首先，需要将[全息远程处理播放器](../platform-capabilities-and-apis/holographic-remoting-player.md)下载到 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-108">To get started, you'll need to download the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="2c9f4-109">通过全息远程处理播放器，应用可以从以下来源直接流式传输到 HoloLens 上的远程处理播放器：</span><span class="sxs-lookup"><span data-stu-id="2c9f4-109">The Holographic Remoting Player lets your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="2c9f4-110">Unreal Engine 编辑器</span><span class="sxs-lookup"><span data-stu-id="2c9f4-110">The Unreal Engine editor</span></span>
* <span data-ttu-id="2c9f4-111">打包的 Windows 可执行文件</span><span class="sxs-lookup"><span data-stu-id="2c9f4-111">A packaged Windows executable</span></span> 

<span data-ttu-id="2c9f4-112">进行流式传输时，你可以访问几乎所有相同的 HoloLens 功能，就像你在设备上运行应用程序时一样。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-112">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="2c9f4-113">这包括[手关节跟踪](unreal-hand-tracking.md)（如果使用的是 HoloLens 2）、[空间映射](unreal-spatial-mapping.md)和[空间定位点](unreal-spatial-anchors.md)，但此[列表](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md)上的功能除外。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-113">This includes [hand joint tracking](unreal-hand-tracking.md) if you're on a HoloLens 2, [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="2c9f4-114">流式传输的质量严重依赖于 wifi 网络的强度。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-114">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="2c9f4-115">自动为全息远程处理播放器启用所有功能。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-115">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="2c9f4-116">如果你发现有一项功能需要用户授权（例如眼动跟踪）才能用于流媒体，但在设备上运行时确不需要它，请检查确保已在项目设置下启用适当的功能。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-116">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

### <a name="streaming-limitations"></a><span data-ttu-id="2c9f4-117">流式传输限制</span><span class="sxs-lookup"><span data-stu-id="2c9f4-117">Streaming limitations</span></span>

<span data-ttu-id="2c9f4-118">不能通过流式传输使用手部网格、HoloLens 摄像头和系统键盘。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-118">Hand meshes, the HoloLens camera, and the system keyboard are unavailable over streaming.</span></span> <span data-ttu-id="2c9f4-119">请注意，可通过要作为流式传输源的电脑的麦克风获取流应用的语音输入。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-119">Note that speech input for streamed apps can be acquired via the microphone of the PC you are streaming from.</span></span>

#### <a name="openxr"></a><span data-ttu-id="2c9f4-120">OpenXR</span><span class="sxs-lookup"><span data-stu-id="2c9f4-120">OpenXR</span></span>

<span data-ttu-id="2c9f4-121">在 OpenXR 上运行的 Unreal 4.26 支持流式传输到全息远程播放器版本 2.4.0+。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-121">Unreal 4.26 running on OpenXR supports streaming to versions 2.4.0+ of the Holographic Remoting Player.</span></span> <span data-ttu-id="2c9f4-122">2\.4.0 中的 OpenXR 流式传输缺少对空间映射和空间定位点的支持。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-122">OpenXR streaming in 2.4.0 is missing support for spatial mapping and spatial anchors.</span></span> 

## <a name="device-support"></a><span data-ttu-id="2c9f4-123">设备支持</span><span class="sxs-lookup"><span data-stu-id="2c9f4-123">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2c9f4-124"><strong>源</strong></span><span class="sxs-lookup"><span data-stu-id="2c9f4-124"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="2c9f4-125"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 第一代</strong></a></span><span class="sxs-lookup"><span data-stu-id="2c9f4-125"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens first Gen</strong></a></span></span></td>
        <td><span data-ttu-id="2c9f4-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="2c9f4-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="2c9f4-127"><strong>沉浸式头戴显示设备</strong></span><span class="sxs-lookup"><span data-stu-id="2c9f4-127"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2c9f4-128">Unreal 编辑器</span><span class="sxs-lookup"><span data-stu-id="2c9f4-128">Unreal editor</span></span></td>
        <td><span data-ttu-id="2c9f4-129">✔️</span><span class="sxs-lookup"><span data-stu-id="2c9f4-129">✔️</span></span></td>
        <td><span data-ttu-id="2c9f4-130">✔️</span><span class="sxs-lookup"><span data-stu-id="2c9f4-130">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="2c9f4-131">Windows 包</span><span class="sxs-lookup"><span data-stu-id="2c9f4-131">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="2c9f4-132">✔️</span><span class="sxs-lookup"><span data-stu-id="2c9f4-132">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="2c9f4-133">从 Unreal 编辑器进行流式传输</span><span class="sxs-lookup"><span data-stu-id="2c9f4-133">Streaming from the Unreal editor</span></span>

<span data-ttu-id="2c9f4-134">作为开发人员，你会发现从 Unreal 编辑器流式传输到 HoloLens 设备在测试时会提供很大的好处，也就是说，你无需再等待应用生成和部署完成后才尝试更新。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-134">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides significant benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="2c9f4-135">教程系列中提供了[从 Unreal 编辑器流式传输](tutorials/unreal-uxt-ch6.md#device-only-streaming)的详细说明。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-135">You can find detailed instructions for [streaming from the Unreal editor](tutorials/unreal-uxt-ch6.md#device-only-streaming) in our tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="2c9f4-136">从打包的 Windows 可执行文件进行流式传输</span><span class="sxs-lookup"><span data-stu-id="2c9f4-136">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="2c9f4-137">在 Unreal 4.25.1 及更高版本中，可以将应用从打包的 Windows 可执行文件流式传输到 HoloLens 2 设备：</span><span class="sxs-lookup"><span data-stu-id="2c9f4-137">In Unreal 4.25.1 and onwards, you can stream your app to a HoloLens 2 device from a packaged Windows executable:</span></span> 

1. <span data-ttu-id="2c9f4-138">转到编辑器菜单中的“文件”>“包项目”>“Windows”。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-138">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="2c9f4-139">选择要保存包的位置，然后选择“选择文件夹”。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-139">Choose a location to save your package and select **Select Folder**.</span></span>

2. <span data-ttu-id="2c9f4-140">包生成完成后，请打开 HoloLens 2 上的“全息远程处理播放器”，并记下 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-140">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="2c9f4-141">使“全息远程处理播放器”保持打开状态，然后使用命令行提示符执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2c9f4-141">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="2c9f4-142">将 cd 插入到保存包的本地目录。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-142">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="2c9f4-143">输入以下命令：`<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span><span class="sxs-lookup"><span data-stu-id="2c9f4-143">Enter the following command: `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span></span>

> [!NOTE]
> <span data-ttu-id="2c9f4-144">项目设置中的应用程序名称应自动用于创建 Windows 包。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-144">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="2c9f4-145">如果名称因某些原因而有所不同，请在命令提示符下使用 Windows 可执行文件名称。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-145">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="2c9f4-146">按 Enter 键，随即将看到应用程序开始进行流式传输了！</span><span class="sxs-lookup"><span data-stu-id="2c9f4-146">Hit enter and watch your application start streaming!</span></span>

### <a name="command-line-options"></a><span data-ttu-id="2c9f4-147">命令行选项</span><span class="sxs-lookup"><span data-stu-id="2c9f4-147">Command line options</span></span>

<span data-ttu-id="2c9f4-148">可在下表中找到 Unreal 引擎 4.26+ 中用于从每个平台进行流式传输的其他命令行选项。</span><span class="sxs-lookup"><span data-stu-id="2c9f4-148">Additional command line options for streaming from each platform in Unreal Engine 4.26+ can be found in the table below.</span></span> 

[!INCLUDE[](includes/tabs-streaming-args.md)]

## <a name="see-also"></a><span data-ttu-id="2c9f4-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c9f4-149">See also</span></span>

* [<span data-ttu-id="2c9f4-150">全息远程处理版本历史记录</span><span class="sxs-lookup"><span data-stu-id="2c9f4-150">Holographic remoting version history</span></span>](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [<span data-ttu-id="2c9f4-151">编写自定义全息远程处理播放器应用</span><span class="sxs-lookup"><span data-stu-id="2c9f4-151">Writing a custom Holographic Remoting player app</span></span>](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [<span data-ttu-id="2c9f4-152">使用全息远程处理建立安全连接</span><span class="sxs-lookup"><span data-stu-id="2c9f4-152">Establishing a secure connection with Holographic Remoting</span></span>](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)
