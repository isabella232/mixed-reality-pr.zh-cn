---
title: Unreal 中的 HoloLens 照片/视频摄像头
description: 了解如何在 Unreal 中将 HoloLens 照片和视频摄像头用于混合现实捕获和对象定位。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, 摄像头, PV 摄像头, MRC, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备
ms.openlocfilehash: 6f1301e0daeb44521dfb4e93a915d49d9aea8443
ms.sourcegitcommit: e24715fffa815c24ca411fa93eed9576ae729337
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2021
ms.locfileid: "98247760"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="a5f49-104">Unreal 中的 HoloLens 照片/视频摄像头</span><span class="sxs-lookup"><span data-stu-id="a5f49-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="a5f49-105">HoloLens 的面板上有一个照片/视频 (PV) 摄像头，它既可用于混合现实捕获 (MRC)，也可在 Unreal 世界空间中从相机帧中的像素坐标定位对象。</span><span class="sxs-lookup"><span data-stu-id="a5f49-105">The HoloLens has a Photo/Video (PV) Camera on the visor that can be used for both Mixed Reality Capture (MRC) and locating objects in Unreal world space from pixel coordinates in the camera frame.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a5f49-106">全息远程不支持 PV 摄像头，但可使用电脑上附带的网络摄像头来模拟 HoloLens PV 摄像头功能。</span><span class="sxs-lookup"><span data-stu-id="a5f49-106">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

[!INCLUDE[](includes/tabs-pv-camera.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="a5f49-107">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="a5f49-107">Next Development Checkpoint</span></span>

<span data-ttu-id="a5f49-108">如果你遵循我们规划的 Unreal 开发历程，则你处于探索混合现实平台功能和 API 的过程之中。</span><span class="sxs-lookup"><span data-stu-id="a5f49-108">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="a5f49-109">从这里，你可以继续了解下一个主题：</span><span class="sxs-lookup"><span data-stu-id="a5f49-109">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a5f49-110">QR 码</span><span class="sxs-lookup"><span data-stu-id="a5f49-110">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="a5f49-111">或直接跳到在设备或模拟器上部署应用：</span><span class="sxs-lookup"><span data-stu-id="a5f49-111">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a5f49-112">部署到设备</span><span class="sxs-lookup"><span data-stu-id="a5f49-112">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="a5f49-113">你可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#3-advanced-features)。</span><span class="sxs-lookup"><span data-stu-id="a5f49-113">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5f49-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5f49-114">See also</span></span>

* [<span data-ttu-id="a5f49-115">可定位相机</span><span class="sxs-lookup"><span data-stu-id="a5f49-115">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="a5f49-116">面向开发人员的混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="a5f49-116">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
