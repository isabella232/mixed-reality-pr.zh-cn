---
title: Unreal 中的 QR 码
description: Unreal 中 QR 码使用指南
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, qr 码, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: 68edfdd0dd77b1d00ceeb9c50202abd5d94b95f3
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678886"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="6da52-104">Unreal 中的 QR 码</span><span class="sxs-lookup"><span data-stu-id="6da52-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="6da52-105">概述</span><span class="sxs-lookup"><span data-stu-id="6da52-105">Overview</span></span>

<span data-ttu-id="6da52-106">HoloLens 2 可以使用网络摄像头查看世界空间中的 QR 码，这会在每个代码的实际位置使用坐标系统将其呈现为全息影像。</span><span class="sxs-lookup"><span data-stu-id="6da52-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="6da52-107">除了单个 QR 码，HoloLens 2 还可以在多个设备上的同一位置呈现全息影像，以创建共享体验。</span><span class="sxs-lookup"><span data-stu-id="6da52-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="6da52-108">请确保遵循将 QR 码添加到应用程序的最佳做法：</span><span class="sxs-lookup"><span data-stu-id="6da52-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="6da52-109">安静区域</span><span class="sxs-lookup"><span data-stu-id="6da52-109">Quiet zones</span></span>
- <span data-ttu-id="6da52-110">照明和背景</span><span class="sxs-lookup"><span data-stu-id="6da52-110">Lighting and backdrop</span></span>
- <span data-ttu-id="6da52-111">大小、距离和角度位置</span><span class="sxs-lookup"><span data-stu-id="6da52-111">Size, distance, and angular position</span></span>

<span data-ttu-id="6da52-112">将 QR 码置于应用中时，请特别注意[环境注意事项](../../environment-considerations-for-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="6da52-112">Pay special attention to the [environment considerations](../../environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="6da52-113">有关每个主题的详细信息以及下载所需 NuGet 包的说明，请参阅主 [QR 码跟踪](../platform-capabilities-and-apis/qr-code-tracking.md)文档。</span><span class="sxs-lookup"><span data-stu-id="6da52-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

## <a name="enabling-qr-detection"></a><span data-ttu-id="6da52-114">启用 QR 检测</span><span class="sxs-lookup"><span data-stu-id="6da52-114">Enabling QR detection</span></span>
<span data-ttu-id="6da52-115">由于 HoloLens 2 需要使用网络摄像头来查看 QR 码，因此需要在项目设置中将其启用：</span><span class="sxs-lookup"><span data-stu-id="6da52-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="6da52-116">打开“编辑”>“项目设置”，滚动到“平台”部分，然后单击“HoloLens”。</span><span class="sxs-lookup"><span data-stu-id="6da52-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="6da52-117">展开“功能”部分，选中“网络摄像头”。</span><span class="sxs-lookup"><span data-stu-id="6da52-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="6da52-118">还需要通过[添加 ARSessionConfig 资产](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)来选择使用 QR 码跟踪。</span><span class="sxs-lookup"><span data-stu-id="6da52-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

<span data-ttu-id="6da52-119">使用之前，应调用 `UHoloLensARFunctionLibrary::StartCameraCapture()` 来手动启用跟踪。</span><span class="sxs-lookup"><span data-stu-id="6da52-119">Right before the usage, you should manually enable the tracking by calling `UHoloLensARFunctionLibrary::StartCameraCapture()`.</span></span> <span data-ttu-id="6da52-120">结束 QR 码跟踪后，应通过 `UHoloLensARFunctionLibrary::StopCameraCapture()` 禁用它以节省设备资源。</span><span class="sxs-lookup"><span data-stu-id="6da52-120">After ending the QR code tracking, you should disable it by `UHoloLensARFunctionLibrary::StopCameraCapture()` to save the device resources.</span></span>

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="6da52-121">设置跟踪图像</span><span class="sxs-lookup"><span data-stu-id="6da52-121">Setting up a tracked image</span></span>

<span data-ttu-id="6da52-122">QR 码通过 Unreal 的 AR 跟踪几何系统显示为跟踪图像。</span><span class="sxs-lookup"><span data-stu-id="6da52-122">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="6da52-123">若要实现此操作，需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="6da52-123">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="6da52-124">创建蓝图，并添加“ARTrackableNotify”组件。</span><span class="sxs-lookup"><span data-stu-id="6da52-124">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![QR AR 可跟踪通知](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="6da52-126">选择“ARTrackableNotify”，然后在“详细信息”面板中展开“事件”部分。</span><span class="sxs-lookup"><span data-stu-id="6da52-126">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span>

![QR 事件](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="6da52-128">单击“关于添加跟踪几何”旁的 +，将节点添加到事件图中。</span><span class="sxs-lookup"><span data-stu-id="6da52-128">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="6da52-129">可以在 [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 组件 API 中找到事件的完整列表。</span><span class="sxs-lookup"><span data-stu-id="6da52-129">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![向“关于添加跟踪几何”添加节点](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="6da52-131">使用跟踪图像</span><span class="sxs-lookup"><span data-stu-id="6da52-131">Using a tracked image</span></span>
<span data-ttu-id="6da52-132">下图中的事件图显示了 OnUpdateTrackedImage 事件，该事件用于呈现 QR 码中心的一个点并输出其数据。</span><span class="sxs-lookup"><span data-stu-id="6da52-132">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

![QR 呈现示例](images/unreal-qr-render.PNG)

<span data-ttu-id="6da52-134">以下是具体过程：</span><span class="sxs-lookup"><span data-stu-id="6da52-134">Here's what's going on:</span></span>
1. <span data-ttu-id="6da52-135">首先，将跟踪图像转换为 ARTrackedQRCode，以检查当前更新的图像是否为 QR 码。</span><span class="sxs-lookup"><span data-stu-id="6da52-135">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="6da52-136">编码数据是从 QRCode 变量中检索的。</span><span class="sxs-lookup"><span data-stu-id="6da52-136">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="6da52-137">可以从 GetLocalToWorldTransform 位置获取左上方的 QR 码，并在 GetEstimateSize 中获取维度。</span><span class="sxs-lookup"><span data-stu-id="6da52-137">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="6da52-138">还可以在代码中[获取 QR 码的坐标系统](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code)。</span><span class="sxs-lookup"><span data-stu-id="6da52-138">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="6da52-139">查找唯一 ID</span><span class="sxs-lookup"><span data-stu-id="6da52-139">Finding the unique ID</span></span>
<span data-ttu-id="6da52-140">每个 QR 码都具有一个唯一的 GUID ID，可以通过以下方式查找：</span><span class="sxs-lookup"><span data-stu-id="6da52-140">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="6da52-141">拖放“作为 ARTracked QRCode”引脚并搜索“获取唯一 ID”。</span><span class="sxs-lookup"><span data-stu-id="6da52-141">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![QR GUID](images/unreal-qr-guid.PNG)

<span data-ttu-id="6da52-143">QR 码幕后还有很多内容等待挖掘，因此体验之旅并没有就此结束。</span><span class="sxs-lookup"><span data-stu-id="6da52-143">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="6da52-144">请务必查看下面的链接，以了解更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="6da52-144">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="6da52-145">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="6da52-145">Next Development Checkpoint</span></span>

<span data-ttu-id="6da52-146">如果你遵循我们规划的 Unreal 开发检查点历程，则你处于探索混合现实平台功能和 API 的过程之中。</span><span class="sxs-lookup"><span data-stu-id="6da52-146">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="6da52-147">从这里，你可以进入下一主题：</span><span class="sxs-lookup"><span data-stu-id="6da52-147">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6da52-148">WinRT</span><span class="sxs-lookup"><span data-stu-id="6da52-148">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="6da52-149">或直接跳到在设备或模拟器上部署应用：</span><span class="sxs-lookup"><span data-stu-id="6da52-149">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6da52-150">部署到设备</span><span class="sxs-lookup"><span data-stu-id="6da52-150">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="6da52-151">你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#3-platform-capabilities-and-apis)。</span><span class="sxs-lookup"><span data-stu-id="6da52-151">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="6da52-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6da52-152">See also</span></span>
* [<span data-ttu-id="6da52-153">空间映射</span><span class="sxs-lookup"><span data-stu-id="6da52-153">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="6da52-154">全息影像</span><span class="sxs-lookup"><span data-stu-id="6da52-154">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="6da52-155">坐标系统</span><span class="sxs-lookup"><span data-stu-id="6da52-155">Coordinate systems</span></span>](../../design/coordinate-systems.md)
