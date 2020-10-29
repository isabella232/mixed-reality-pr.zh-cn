---
title: 在 Unreal 中注视输入
description: 针对 HoloLens 和 Unreal 引擎设置注视输入的教程
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality，全息影像，HoloLens 2，眼睛跟踪，注视输入，head 装入显示，Unreal 引擎
ms.openlocfilehash: 477fbdc9c7ddb3b4e890e62150651d9227d4c19e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2020
ms.locfileid: "91677345"
---
# <a name="gaze-input"></a><span data-ttu-id="61196-104">注视输入</span><span class="sxs-lookup"><span data-stu-id="61196-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="61196-105">概述</span><span class="sxs-lookup"><span data-stu-id="61196-105">Overview</span></span>

<span data-ttu-id="61196-106">[Windows Mixed Reality 插件](https://docs.unrealengine.com/Platforms/VR/WMR/index.html)不提供任何用于目视输入的内置函数，但 HoloLens 2 支持目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="61196-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="61196-107">实际的跟踪功能由 Unreal 的 **Head 挂载显示** 和 **目视跟踪** api 提供，包括：</span><span class="sxs-lookup"><span data-stu-id="61196-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="61196-108">设备信息</span><span class="sxs-lookup"><span data-stu-id="61196-108">Device information</span></span>
- <span data-ttu-id="61196-109">跟踪传感器</span><span class="sxs-lookup"><span data-stu-id="61196-109">Tracking sensors</span></span>
- <span data-ttu-id="61196-110">方向和位置</span><span class="sxs-lookup"><span data-stu-id="61196-110">Orientation and position</span></span>
- <span data-ttu-id="61196-111">剪辑窗格</span><span class="sxs-lookup"><span data-stu-id="61196-111">Clipping panes</span></span>
- <span data-ttu-id="61196-112">注视数据和跟踪信息</span><span class="sxs-lookup"><span data-stu-id="61196-112">Gaze data and tracking information</span></span>

<span data-ttu-id="61196-113">可以在 Unreal 的 [安装的显示](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) 和 [目视跟踪](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) 文档中找到功能的完整列表。</span><span class="sxs-lookup"><span data-stu-id="61196-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span>

<span data-ttu-id="61196-114">除了 Unreal Api 外，还可以查看有关 HoloLens 2 的 [基于目视](../../design/eye-gaze-interaction.md) 观看的交互的文档，并了解如何 [在 hololens 2 上运行目视跟踪](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) 。</span><span class="sxs-lookup"><span data-stu-id="61196-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](../../design/eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="61196-115">仅在 HoloLens 2 上支持目视跟踪。</span><span class="sxs-lookup"><span data-stu-id="61196-115">Eye tracking is only supported on HoloLens 2.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="61196-116">启用目视跟踪</span><span class="sxs-lookup"><span data-stu-id="61196-116">Enabling eye tracking</span></span>
<span data-ttu-id="61196-117">需要在 HoloLens 项目设置中启用 "注视输入"，然后才能使用任何 Unreal Api。</span><span class="sxs-lookup"><span data-stu-id="61196-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="61196-118">当应用程序启动时，你将看到下面的屏幕截图中显示的同意提示。</span><span class="sxs-lookup"><span data-stu-id="61196-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="61196-119">选择 **"是"** 以设置权限并获取对注视输入的访问权限。</span><span class="sxs-lookup"><span data-stu-id="61196-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="61196-120">如果需要随时更改此设置，可在 " **设置** " 应用中找到它。</span><span class="sxs-lookup"><span data-stu-id="61196-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![目视输入权限](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="61196-122">Unreal 中的 HoloLens 眼睛跟踪只对这两种眼睛都有一个注视，而不是 stereoscopic 跟踪所需的两个射线，这不受支持。</span><span class="sxs-lookup"><span data-stu-id="61196-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="61196-123">这就是在 Unreal 中开始向 HoloLens 2 应用添加注视输入所需的全部设置。</span><span class="sxs-lookup"><span data-stu-id="61196-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="61196-124">有关 "注视输入" 以及它如何影响混合现实中的用户的详细信息，请参阅以下链接。</span><span class="sxs-lookup"><span data-stu-id="61196-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="61196-125">在构建交互式体验时，请务必考虑这种情况。</span><span class="sxs-lookup"><span data-stu-id="61196-125">Be sure to think about these when building your interactive experiences.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="61196-126">下一个开发检查点</span><span class="sxs-lookup"><span data-stu-id="61196-126">Next Development Checkpoint</span></span>

<span data-ttu-id="61196-127">如果遵循我们所 Unreal 的开发检查点旅程，就是在探索 MRTK 核心构建基块。</span><span class="sxs-lookup"><span data-stu-id="61196-127">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="61196-128">在这里，你可以继续执行下一个构建基块：</span><span class="sxs-lookup"><span data-stu-id="61196-128">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="61196-129">手部跟踪</span><span class="sxs-lookup"><span data-stu-id="61196-129">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="61196-130">或跳转到混合现实平台功能和 Api：</span><span class="sxs-lookup"><span data-stu-id="61196-130">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="61196-131">HoloLens 摄像头</span><span class="sxs-lookup"><span data-stu-id="61196-131">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="61196-132">随时可以随时返回到 [Unreal 开发检查点](unreal-development-overview.md#2-core-building-blocks) 。</span><span class="sxs-lookup"><span data-stu-id="61196-132">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="61196-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="61196-133">See also</span></span>
* [<span data-ttu-id="61196-134">校准</span><span class="sxs-lookup"><span data-stu-id="61196-134">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="61196-135">舒适</span><span class="sxs-lookup"><span data-stu-id="61196-135">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="61196-136">凝视和提交</span><span class="sxs-lookup"><span data-stu-id="61196-136">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="61196-137">语音输入</span><span class="sxs-lookup"><span data-stu-id="61196-137">Voice input</span></span>](../../out-of-scope/voice-design.md)
