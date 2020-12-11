---
title: Unreal 中的 HoloLens 照片/视频摄像头
description: Unreal 中 HoloLens 照片/视频摄像头使用指南
author: hferrone
ms.author: jacksonf
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, 摄像头, PV 摄像头, MRC, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: c0c6e06e66e03934912906dbff5a93f9271a68b6
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609599"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="fbcd6-104">Unreal 中的 HoloLens 照片/视频摄像头</span><span class="sxs-lookup"><span data-stu-id="fbcd6-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="fbcd6-105">HoloLens 的面板上有一个照片/视频 (PV) 摄像头，它既可用于混合现实捕获 (MRC)，也可在 Unreal 世界空间中从相机帧中的像素坐标定位对象。</span><span class="sxs-lookup"><span data-stu-id="fbcd6-105">The HoloLens has a Photo/Video (PV) Camera on the visor that can be used for both Mixed Reality Capture (MRC) and locating objects in Unreal world space from pixel coordinates in the camera frame.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fbcd6-106">全息远程不支持 PV 摄像头，但可使用电脑上附带的网络摄像头来模拟 HoloLens PV 摄像头功能。</span><span class="sxs-lookup"><span data-stu-id="fbcd6-106">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

[!INCLUDE[](includes/tabs-pv-camera.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="fbcd6-107">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="fbcd6-107">Next Development Checkpoint</span></span>

<span data-ttu-id="fbcd6-108">如果你遵循我们规划的 Unreal 开发历程，则你处于探索混合现实平台功能和 API 的过程之中。</span><span class="sxs-lookup"><span data-stu-id="fbcd6-108">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="fbcd6-109">从这里，你可以继续了解下一个主题：</span><span class="sxs-lookup"><span data-stu-id="fbcd6-109">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fbcd6-110">QR 码</span><span class="sxs-lookup"><span data-stu-id="fbcd6-110">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="fbcd6-111">或直接跳到在设备或模拟器上部署应用：</span><span class="sxs-lookup"><span data-stu-id="fbcd6-111">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fbcd6-112">部署到设备</span><span class="sxs-lookup"><span data-stu-id="fbcd6-112">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="fbcd6-113">你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#3-platform-capabilities-and-apis)。</span><span class="sxs-lookup"><span data-stu-id="fbcd6-113">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbcd6-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fbcd6-114">See also</span></span>
* [<span data-ttu-id="fbcd6-115">可定位相机</span><span class="sxs-lookup"><span data-stu-id="fbcd6-115">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="fbcd6-116">面向开发人员的混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="fbcd6-116">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
