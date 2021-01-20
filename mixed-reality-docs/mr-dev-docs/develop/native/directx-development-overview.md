---
title: 原生开发概述
description: 了解如何直接使用 Windows Mixed Reality Api 构建基于 DirectX 的混合现实引擎。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX，全息呈现，本机，本机应用，WinRT，WinRT 应用，平台 Api，自定义引擎，中间件，混合现实耳机，windows mixed reality 耳机，虚拟现实耳机
ms.openlocfilehash: b137fad12740542deb4995485201a9bd0d1d7662
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581042"
---
# <a name="native-development-overview"></a><span data-ttu-id="010d1-104">原生开发概述</span><span class="sxs-lookup"><span data-stu-id="010d1-104">Native development overview</span></span>

![本机横幅徽标](../images/native_logo_banner.png)

<span data-ttu-id="010d1-106">3D 引擎（如 [Unity](../unity/unity-development-overview.md) 或 [Unreal](../unreal/unreal-development-overview.md) ）并不是唯一的混合现实开发途径。</span><span class="sxs-lookup"><span data-stu-id="010d1-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="010d1-107">你还可以使用 Windows Mixed Reality Api 和 DirectX 11 或 DirectX 12 来创建混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="010d1-107">You can also create Mixed Reality apps using the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="010d1-108">转到平台源实质上是构建自己的中间件或框架。</span><span class="sxs-lookup"><span data-stu-id="010d1-108">By going to the platform source, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="010d1-109">如果你有想要维护的现有 WinRT 项目，请转到我们的主 [winrt 文档](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="010d1-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="010d1-110">开发检查点</span><span class="sxs-lookup"><span data-stu-id="010d1-110">Development checkpoints</span></span>

<span data-ttu-id="010d1-111">使用以下检查点，将 Unity 游戏和应用程序带入混合现实的世界。</span><span class="sxs-lookup"><span data-stu-id="010d1-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="010d1-112">1.入门</span><span class="sxs-lookup"><span data-stu-id="010d1-112">1. Getting started</span></span>

<span data-ttu-id="010d1-113">Windows Mixed Reality 支持 [两种类型的应用](../../design/app-views.md)：</span><span class="sxs-lookup"><span data-stu-id="010d1-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="010d1-114">使用 [HOLOGRAPHICSPACE api](getting-a-holographicspace.md)或 [OpenXR api](openxr.md)呈现可填充耳机显示的 [沉浸式视图](../../design/app-views.md)的 UWP 或 Win32 **混合现实应用程序**</span><span class="sxs-lookup"><span data-stu-id="010d1-114">UWP or Win32 **Mixed Reality applications** that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) that fills the headset display</span></span>
* <span data-ttu-id="010d1-115"> (UWP) 的 **2d 应用**，使用 DIRECTX、XAML 或其他框架在 Windows Mixed Reality 主页上呈现清单的 [2d 视图](../../design/app-views.md#2d-views)</span><span class="sxs-lookup"><span data-stu-id="010d1-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="010d1-116">[2d 视图和沉浸式视图](../../design/app-views.md)的 DirectX 开发之间的差异主要涉及全息呈现和空间输入。</span><span class="sxs-lookup"><span data-stu-id="010d1-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="010d1-117">UWP 应用程序的 [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) 或 Win32 应用程序的 HWND 是必需的，并且保持基本相同。</span><span class="sxs-lookup"><span data-stu-id="010d1-117">Your UWP application's [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="010d1-118">适用于应用程序的 WinRT Api 也是如此。</span><span class="sxs-lookup"><span data-stu-id="010d1-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="010d1-119">但您必须使用这些 Api 的不同子集才能利用全息功能。</span><span class="sxs-lookup"><span data-stu-id="010d1-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="010d1-120">例如，适用于全息应用程序的系统管理存在和帧，以启用姿势预测帧循环。</span><span class="sxs-lookup"><span data-stu-id="010d1-120">For example, the system for holographic applications manages the swapchain and frame present to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="010d1-121">2.核心构建基块</span><span class="sxs-lookup"><span data-stu-id="010d1-121">2. Core building blocks</span></span>

<span data-ttu-id="010d1-122">Windows Mixed Reality 应用程序使用以下 Api 为 HoloLens 和其他沉浸式耳机构建 [混合现实](../../discover/mixed-reality.md) 体验：</span><span class="sxs-lookup"><span data-stu-id="010d1-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="010d1-123">特性</span><span class="sxs-lookup"><span data-stu-id="010d1-123">Feature</span></span>  |  <span data-ttu-id="010d1-124">功能</span><span class="sxs-lookup"><span data-stu-id="010d1-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="010d1-125">凝视</span><span class="sxs-lookup"><span data-stu-id="010d1-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="010d1-126">让用户通过查看全息影像来定位它们</span><span class="sxs-lookup"><span data-stu-id="010d1-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="010d1-127">手势</span><span class="sxs-lookup"><span data-stu-id="010d1-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="010d1-128">向你的应用添加空间操作</span><span class="sxs-lookup"><span data-stu-id="010d1-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="010d1-129">全息渲染</span><span class="sxs-lookup"><span data-stu-id="010d1-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="010d1-130">在世界各地的用户的精确位置绘制一个全息图</span><span class="sxs-lookup"><span data-stu-id="010d1-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="010d1-131">运动控制器</span><span class="sxs-lookup"><span data-stu-id="010d1-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="010d1-132">让用户在混合现实环境中采取措施</span><span class="sxs-lookup"><span data-stu-id="010d1-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="010d1-133">空间映射</span><span class="sxs-lookup"><span data-stu-id="010d1-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="010d1-134">使用虚拟网格覆盖映射物理空间以标记环境边界</span><span class="sxs-lookup"><span data-stu-id="010d1-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="010d1-135">语音</span><span class="sxs-lookup"><span data-stu-id="010d1-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="010d1-136">捕获用户的口语关键字、短语和听写</span><span class="sxs-lookup"><span data-stu-id="010d1-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="010d1-137">可以在 OpenXR [路线图](openxr.md#roadmap) 文档中找到即将推出的和开发中的核心功能。</span><span class="sxs-lookup"><span data-stu-id="010d1-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="010d1-138">3. 部署和测试</span><span class="sxs-lookup"><span data-stu-id="010d1-138">3. Deploying and testing</span></span>

<span data-ttu-id="010d1-139">可以使用 OpenXR 在 HoloLens 2 或 Windows Mixed Reality 沉浸式耳机上进行开发。</span><span class="sxs-lookup"><span data-stu-id="010d1-139">You can develop on a desktop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset.</span></span>  <span data-ttu-id="010d1-140">如果你无权访问耳机，则可以改用 [HoloLens 2 模拟器](../platform-capabilities-and-apis/using-the-hololens-emulator.md) 或 [Windows Mixed Reality 模拟器](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 。</span><span class="sxs-lookup"><span data-stu-id="010d1-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="010d1-141">下一步操作</span><span class="sxs-lookup"><span data-stu-id="010d1-141">What's next?</span></span>

<span data-ttu-id="010d1-142">开发人员的工作一直在更新，特别是在学习新工具或 SDK 时。</span><span class="sxs-lookup"><span data-stu-id="010d1-142">A developer's job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="010d1-143">以下部分可能会将你带到已完成的初级级别资料之外的区域。</span><span class="sxs-lookup"><span data-stu-id="010d1-143">The following sections can take you into areas beyond the beginner level material you've already completed.</span></span> <span data-ttu-id="010d1-144">这些主题和资源不按任何顺序排列，因此可随时跳转并浏览！</span><span class="sxs-lookup"><span data-stu-id="010d1-144">These topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="010d1-145">其他资源</span><span class="sxs-lookup"><span data-stu-id="010d1-145">Additional resources</span></span>

<span data-ttu-id="010d1-146">如果想要对 OpenXR 游戏进行调配，请查看以下链接：</span><span class="sxs-lookup"><span data-stu-id="010d1-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="010d1-147">OpenXR 最佳做法</span><span class="sxs-lookup"><span data-stu-id="010d1-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="010d1-148">OpenXR 性能</span><span class="sxs-lookup"><span data-stu-id="010d1-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="010d1-149">OpenXR 故障排除</span><span class="sxs-lookup"><span data-stu-id="010d1-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="010d1-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="010d1-150">See also</span></span>
* [<span data-ttu-id="010d1-151">应用模型</span><span class="sxs-lookup"><span data-stu-id="010d1-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="010d1-152">应用视图</span><span class="sxs-lookup"><span data-stu-id="010d1-152">App views</span></span>](../../design/app-views.md)