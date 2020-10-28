---
title: 移植指南
description: 介绍如何将现有沉浸式应用程序移植到 Windows Mixed Reality 的分步演练。
author: JBrentJ
ms.author: alexturn
ms.date: 07/07/2020
ms.topic: article
keywords: 端口，移植，unity，中间件，引擎，UWP，Win32
ms.openlocfilehash: 9822976ab7dac9ae7567e5f38ca44ceee646d098
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638536"
---
# <a name="porting-guides"></a><span data-ttu-id="3fb6e-104">移植指南</span><span class="sxs-lookup"><span data-stu-id="3fb6e-104">Porting guides</span></span>

<span data-ttu-id="3fb6e-105">Windows 10 包括对沉浸式和全息耳机的直接支持。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-105">Windows 10 includes direct support for immersive and holographic headsets.</span></span> <span data-ttu-id="3fb6e-106">如果已为其他设备（如 Oculus Rift 或 HTC Naopak）生成内容，这些内容将依赖于操作系统的平台 API 之上的库。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-106">If you've built content for other devices, such as the Oculus Rift or HTC Vive, these have dependencies on libraries that exist above the operating system's platform API.</span></span> <span data-ttu-id="3fb6e-107">将现有的 Win32 Unity VR 应用引入 Windows Mixed Reality 涉及到重定目标使用特定于供应商的 VR Sdk 到 Unity 的跨供应商 VR Api。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-107">Bringing existing Win32 Unity VR apps over to Windows Mixed Reality involves retargeting usage of vendor-specific VR SDKs to Unity's cross-vendor VR APIs.</span></span>

## <a name="porting-overview"></a><span data-ttu-id="3fb6e-108">移植概述</span><span class="sxs-lookup"><span data-stu-id="3fb6e-108">Porting overview</span></span>

<span data-ttu-id="3fb6e-109">在高级别上，迁移现有内容涉及以下步骤：</span><span class="sxs-lookup"><span data-stu-id="3fb6e-109">At a high level, the following steps are involved in porting existing content:</span></span>
1. <span data-ttu-id="3fb6e-110">**请确保你的电脑正在运行 Windows 10 秋季创意者更新 (16299) 。**</span><span class="sxs-lookup"><span data-stu-id="3fb6e-110">**Make sure your PC is running the Windows 10 Fall Creators Update (16299).**</span></span> <span data-ttu-id="3fb6e-111">我们不再建议从有问必答向后跳环接收预览版，因为这些版本对于混合现实开发不是最稳定的。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-111">We no longer recommend receiving preview builds from the Insider Skip Ahead ring, as those builds won't be the most stable for mixed reality development.</span></span>
2. <span data-ttu-id="3fb6e-112">**升级到最新版本的图形或游戏引擎。**</span><span class="sxs-lookup"><span data-stu-id="3fb6e-112">**Upgrade to the latest version of your graphics or game engine.**</span></span> <span data-ttu-id="3fb6e-113">游戏引擎需要支持 Windows 10 SDK 版本 10.0.15063.0 (于2017年4月) 或更高版本发布。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-113">Game engines will need to support the Windows 10 SDK version 10.0.15063.0 (released in April 2017) or higher.</span></span>
3. <span data-ttu-id="3fb6e-114">**升级任何中间件、插件或组件。**</span><span class="sxs-lookup"><span data-stu-id="3fb6e-114">**Upgrade any middleware, plug-ins, or components.**</span></span> <span data-ttu-id="3fb6e-115">如果你的应用程序包含任何组件，则最好升级到最新版本。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-115">If your app contains any components, it's a good idea to upgrade to the latest version.</span></span>
4. <span data-ttu-id="3fb6e-116">**删除重复的 sdk 依赖项** 。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-116">**Remove dependencies on duplicate SDKs** .</span></span> <span data-ttu-id="3fb6e-117">根据你的内容面向哪个设备，你将需要删除或有条件地编译该 SDK (例如 SteamVR) 以便可以改为面向 Windows Api。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-117">Depending on which device your content was targeting, you'll need to remove or conditionally compile out that SDK (for example, SteamVR) so you can target the Windows APIs instead.</span></span>
5. <span data-ttu-id="3fb6e-118">**处理生成问题。**</span><span class="sxs-lookup"><span data-stu-id="3fb6e-118">**Work through build issues.**</span></span> <span data-ttu-id="3fb6e-119">此时，迁移练习特定于您的应用程序、您的引擎和您拥有的组件依赖项。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-119">At this point, the porting exercise is specific to your app, your engine, and the component dependencies you have.</span></span>

## <a name="common-porting-steps"></a><span data-ttu-id="3fb6e-120">常见的移植步骤</span><span class="sxs-lookup"><span data-stu-id="3fb6e-120">Common porting steps</span></span>

### <a name="1-make-sure-you-have-the-right-development-hardware"></a><span data-ttu-id="3fb6e-121">1. 确保拥有正确的开发硬件</span><span class="sxs-lookup"><span data-stu-id="3fb6e-121">1. Make sure you have the right development hardware</span></span>

<span data-ttu-id="3fb6e-122">" [安装工具](../install-the-tools.md#immersive-vr-headset-requirements) " 页将列出推荐的开发硬件。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-122">The [install the tools](../install-the-tools.md#immersive-vr-headset-requirements) page lists the recommended development hardware.</span></span>

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a><span data-ttu-id="3fb6e-123">2. 升级到 Windows 10 的最新航班</span><span class="sxs-lookup"><span data-stu-id="3fb6e-123">2. Upgrade to the latest flight of Windows 10</span></span>

<span data-ttu-id="3fb6e-124">Windows Mixed Reality 平台仍处于积极开发阶段。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-124">The Windows Mixed Reality platform is still under active development.</span></span> <span data-ttu-id="3fb6e-125">建议 [加入 Windows 预览体验计划](https://insider.windows.com/) ，以访问 "Windows 有问必答 Fast" 航班。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-125">We recommend [joining the Windows Insider Program](https://insider.windows.com/) to access the "Windows Insider Fast" flight.</span></span>
1. <span data-ttu-id="3fb6e-126">安装 [Windows 10 创意者更新](https://www.microsoft.com/software-download/windows10)</span><span class="sxs-lookup"><span data-stu-id="3fb6e-126">Install the [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)</span></span>
2. <span data-ttu-id="3fb6e-127">[加入](https://insider.windows.com/) Windows 预览体验计划。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-127">[Join](https://insider.windows.com/) the Windows Insider Program.</span></span>
3. <span data-ttu-id="3fb6e-128">启用 [开发人员模式](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)</span><span class="sxs-lookup"><span data-stu-id="3fb6e-128">Enable [Developer Mode](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)</span></span>
4. <span data-ttu-id="3fb6e-129">通过 " **设置" > 更新 & 安全 "部分** ，切换到 [Windows 预览体验快速航班](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview)</span><span class="sxs-lookup"><span data-stu-id="3fb6e-129">Switch to the [Windows Insider Fast flights](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) through **Settings > Update & Security Section**</span></span>

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a><span data-ttu-id="3fb6e-130">3. 升级到最新版本的 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3fb6e-130">3. Upgrade to the most recent build of Visual Studio</span></span>
* <span data-ttu-id="3fb6e-131">如果使用的是 Visual Studio，请升级到最新版本</span><span class="sxs-lookup"><span data-stu-id="3fb6e-131">If you're using Visual Studio then upgrade to the most recent build</span></span>
* <span data-ttu-id="3fb6e-132">请参阅 Visual Studio 2019 下 [的安装工具](../install-the-tools.md#installation-checklist) 页面</span><span class="sxs-lookup"><span data-stu-id="3fb6e-132">See [Install the tools](../install-the-tools.md#installation-checklist) page under Visual Studio 2019</span></span>

### <a name="4-choose-the-correct-adapter"></a><span data-ttu-id="3fb6e-133">4. 选择正确的适配器</span><span class="sxs-lookup"><span data-stu-id="3fb6e-133">4. Choose the correct Adapter</span></span>
* <span data-ttu-id="3fb6e-134">在包含两个 Gpu 的笔记本系统中， [针对正确的适配器](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-134">In systems like notebooks with two GPUs, [target the correct adapter](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications).</span></span> <span data-ttu-id="3fb6e-135">这适用于 Unity 和本机 DirectX 应用，其中 ID3D11Device 是显式或隐式 (为其功能媒体基础) 创建的。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-135">This applies to Unity and native DirectX apps where a ID3D11Device is created, either explicitly or implicitly (Media Foundation), for its functionality.</span></span>

## <a name="unity-porting-guidance"></a><span data-ttu-id="3fb6e-136">Unity 移植指南</span><span class="sxs-lookup"><span data-stu-id="3fb6e-136">Unity porting guidance</span></span>

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a><span data-ttu-id="3fb6e-137">Unreal 移植指南</span><span class="sxs-lookup"><span data-stu-id="3fb6e-137">Unreal porting guidance</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3fb6e-138">如果你使用的是 HP 回音 G2 控制器，请参阅 [此文](../unreal/unreal-reverb-g2-controllers.md) ，了解更多输入映射说明。</span><span class="sxs-lookup"><span data-stu-id="3fb6e-138">If you're using HP Reverb G2 controllers, please refer to [this article](../unreal/unreal-reverb-g2-controllers.md) for additional input mapping instructions.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fb6e-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3fb6e-139">See also</span></span>
* [<span data-ttu-id="3fb6e-140">Windows Mixed Reality 最小电脑硬件兼容性指南</span><span class="sxs-lookup"><span data-stu-id="3fb6e-140">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [<span data-ttu-id="3fb6e-141">了解混合现实的性能</span><span class="sxs-lookup"><span data-stu-id="3fb6e-141">Understanding Performance for Mixed Reality</span></span>](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="3fb6e-142">Unity 性能建议</span><span class="sxs-lookup"><span data-stu-id="3fb6e-142">Performance Recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="3fb6e-143">运动控制器</span><span class="sxs-lookup"><span data-stu-id="3fb6e-143">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="3fb6e-144">Unity 中的手势和运动控制器</span><span class="sxs-lookup"><span data-stu-id="3fb6e-144">Gestures and motion controllers in Unity</span></span>](../unity/gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="3fb6e-145">UnityEngine. XR</span><span class="sxs-lookup"><span data-stu-id="3fb6e-145">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="3fb6e-146">UnityEngine. XR. InputTracking</span><span class="sxs-lookup"><span data-stu-id="3fb6e-146">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="3fb6e-147">移植指南</span><span class="sxs-lookup"><span data-stu-id="3fb6e-147">Porting guides</span></span>](porting-guides.md)