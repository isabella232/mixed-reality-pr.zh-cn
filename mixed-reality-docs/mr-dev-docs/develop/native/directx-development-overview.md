---
title: 原生开发概述
description: 直接使用 Windows Mixed Reality Api 构建基于 DirectX 的混合现实引擎。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX，全息呈现，本机，本机应用，WinRT，WinRT 应用，平台 Api，自定义引擎，中间件
ms.openlocfilehash: fb51dfe15de26b80db255f0daca69e913f9ad35c
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903120"
---
# <a name="native-development-overview"></a><span data-ttu-id="5ab8e-104">原生开发概述</span><span class="sxs-lookup"><span data-stu-id="5ab8e-104">Native development overview</span></span>

![本机横幅徽标](../images/native_logo_banner.png)

<span data-ttu-id="5ab8e-106">3D 引擎（如 [Unity](../unity/unity-development-overview.md) 或 [Unreal](../unreal/unreal-development-overview.md) ）并不是唯一的混合现实开发途径。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="5ab8e-107">还可以通过使用 DirectX 11 或 DirectX 12 的 Windows 混合现实 Api 直接编写代码来创建混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-107">You can also create Mixed Reality apps by directly coding to the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="5ab8e-108">通过直接利用该平台，你实质上是构建自己的中间件或框架。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-108">By leveraging the platform directly, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="5ab8e-109">如果你有想要维护的现有 WinRT 项目，请转到我们的主 [winrt 文档](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="5ab8e-110">开发检查点</span><span class="sxs-lookup"><span data-stu-id="5ab8e-110">Development checkpoints</span></span>

<span data-ttu-id="5ab8e-111">使用以下检查点，将 Unity 游戏和应用程序带入混合现实的世界。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="5ab8e-112">1.入门</span><span class="sxs-lookup"><span data-stu-id="5ab8e-112">1. Getting started</span></span>

<span data-ttu-id="5ab8e-113">Windows Mixed Reality 支持 [两种类型的应用](../../design/app-views.md)：</span><span class="sxs-lookup"><span data-stu-id="5ab8e-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="5ab8e-114">**混合现实应用程序** (UWP 或 Win32) ，这些应用程序使用 [HolographicSpace API](getting-a-holographicspace.md) 或 [OpenXR api](openxr.md) 将 [沉浸式视图](../../design/app-views.md) 呈现给填充耳机显示的用户</span><span class="sxs-lookup"><span data-stu-id="5ab8e-114">**Mixed-reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) to the user that fills the headset display</span></span>
* <span data-ttu-id="5ab8e-115"> (UWP) 的 **2d 应用** ，使用 DIRECTX、XAML 或其他框架在 Windows Mixed Reality 主页上呈现清单的 [2d 视图](../../design/app-views.md#2d-views)</span><span class="sxs-lookup"><span data-stu-id="5ab8e-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="5ab8e-116">[2d 视图和沉浸式视图](../../design/app-views.md)的 DirectX 开发之间的差异主要涉及全息呈现和空间输入。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="5ab8e-117">UWP 应用程序的 [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) 或 Win32 应用程序的 HWND 是必需的，并且保持基本相同。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-117">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="5ab8e-118">适用于应用程序的 WinRT Api 也是如此。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="5ab8e-119">但您必须使用这些 Api 的不同子集才能利用全息功能。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="5ab8e-120">例如，存在和帧的存在由系统为全息应用程序管理，以便启用姿势预测帧循环。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-120">For example, the swapchain and frame present is managed by the system for holographic applications in order to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="5ab8e-121">2.核心构建基块</span><span class="sxs-lookup"><span data-stu-id="5ab8e-121">2. Core building blocks</span></span>

<span data-ttu-id="5ab8e-122">Windows Mixed Reality 应用程序使用以下 Api 为 HoloLens 和其他沉浸式耳机构建 [混合现实](../../discover/mixed-reality.md) 体验：</span><span class="sxs-lookup"><span data-stu-id="5ab8e-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="5ab8e-123">特性</span><span class="sxs-lookup"><span data-stu-id="5ab8e-123">Feature</span></span>  |  <span data-ttu-id="5ab8e-124">功能</span><span class="sxs-lookup"><span data-stu-id="5ab8e-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="5ab8e-125">凝视</span><span class="sxs-lookup"><span data-stu-id="5ab8e-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="5ab8e-126">让用户通过查看全息影像来定位它们</span><span class="sxs-lookup"><span data-stu-id="5ab8e-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="5ab8e-127">手势</span><span class="sxs-lookup"><span data-stu-id="5ab8e-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="5ab8e-128">向你的应用添加空间操作</span><span class="sxs-lookup"><span data-stu-id="5ab8e-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="5ab8e-129">全息渲染</span><span class="sxs-lookup"><span data-stu-id="5ab8e-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="5ab8e-130">在世界各地的用户的精确位置绘制一个全息图</span><span class="sxs-lookup"><span data-stu-id="5ab8e-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="5ab8e-131">运动控制器</span><span class="sxs-lookup"><span data-stu-id="5ab8e-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="5ab8e-132">让用户在混合现实环境中采取措施</span><span class="sxs-lookup"><span data-stu-id="5ab8e-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="5ab8e-133">空间映射</span><span class="sxs-lookup"><span data-stu-id="5ab8e-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="5ab8e-134">使用虚拟网格覆盖映射物理空间以标记环境边界</span><span class="sxs-lookup"><span data-stu-id="5ab8e-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="5ab8e-135">语音</span><span class="sxs-lookup"><span data-stu-id="5ab8e-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="5ab8e-136">捕获用户的口语关键字、短语和听写</span><span class="sxs-lookup"><span data-stu-id="5ab8e-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="5ab8e-137">可以在 OpenXR [路线图](openxr.md#roadmap) 文档中找到即将推出的和开发中的核心功能。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="5ab8e-138">3. 部署和测试</span><span class="sxs-lookup"><span data-stu-id="5ab8e-138">3. Deploying and testing</span></span>

<span data-ttu-id="5ab8e-139">你可在桌面上的 HoloLens 2 或 Windows Mixed Reality 沉浸式头戴显示设备上使用 OpenXR 进行开发。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-139">You can develop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset on the desktop.</span></span>  <span data-ttu-id="5ab8e-140">如果你无权访问耳机，则可以改用 [HoloLens 2 模拟器](../platform-capabilities-and-apis/using-the-hololens-emulator.md) 或 [Windows Mixed Reality 模拟器](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="5ab8e-141">下一步操作</span><span class="sxs-lookup"><span data-stu-id="5ab8e-141">What's next?</span></span>

<span data-ttu-id="5ab8e-142">开发人员的工作一直在更新，特别是在学习新工具或 SDK 时。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-142">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="5ab8e-143">以下部分将带你进入你已完成的初学者级别资料之外的其他领域，并在你遇到问题时提供有用的资源。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-143">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="5ab8e-144">请注意，这些主题和资源不按任何顺序排列，因此请随意查看并探索！</span><span class="sxs-lookup"><span data-stu-id="5ab8e-144">Note that these topics and resources are not in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="5ab8e-145">其他资源</span><span class="sxs-lookup"><span data-stu-id="5ab8e-145">Additional resources</span></span>

<span data-ttu-id="5ab8e-146">如果想要对 OpenXR 游戏进行调配，请查看以下链接：</span><span class="sxs-lookup"><span data-stu-id="5ab8e-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="5ab8e-147">OpenXR 最佳做法</span><span class="sxs-lookup"><span data-stu-id="5ab8e-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="5ab8e-148">OpenXR 性能</span><span class="sxs-lookup"><span data-stu-id="5ab8e-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="5ab8e-149">OpenXR 故障排除</span><span class="sxs-lookup"><span data-stu-id="5ab8e-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="5ab8e-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ab8e-150">See also</span></span>
* [<span data-ttu-id="5ab8e-151">应用模型</span><span class="sxs-lookup"><span data-stu-id="5ab8e-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="5ab8e-152">应用视图</span><span class="sxs-lookup"><span data-stu-id="5ab8e-152">App views</span></span>](../../design/app-views.md)
