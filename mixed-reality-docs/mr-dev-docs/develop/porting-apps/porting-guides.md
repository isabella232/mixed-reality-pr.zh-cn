---
title: 将 VR 应用移植到 Windows Mixed Reality
description: 介绍如何将现有沉浸式应用程序移植到 Windows Mixed Reality 的分步演练。
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: 端口，unity，unreal，中间件，引擎，UWP，Win32，移植，HoloLens 第一代，混合现实耳机，windows mixed reality 耳机，迁移，Windows 10，输入映射，
ms.openlocfilehash: bb76325c0a2d10150cff6604e29c7ead8a97df8e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394461"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a><span data-ttu-id="f987d-104">将 VR 应用移植到 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f987d-104">Porting VR apps to Windows Mixed Reality</span></span>

<span data-ttu-id="f987d-105">Windows 10 支持沉浸式和全息耳机。</span><span class="sxs-lookup"><span data-stu-id="f987d-105">Windows 10 includes support for immersive and holographic headsets.</span></span> <span data-ttu-id="f987d-106">如果为其他设备（如 Oculus Rift 或 HTC Naopak）生成了内容，则它们依赖于操作系统的平台 API 之上的库。</span><span class="sxs-lookup"><span data-stu-id="f987d-106">If you've built content for other devices like the Oculus Rift or HTC Vive, they have dependencies on libraries that exist above the operating system's platform API.</span></span> <span data-ttu-id="f987d-107">将现有的 Win32 Unity VR 应用引入 Windows Mixed Reality 涉及到重定目标使用特定于供应商的 VR Sdk 到 Unity 的跨供应商 VR Api。</span><span class="sxs-lookup"><span data-stu-id="f987d-107">Bringing existing Win32 Unity VR apps over to Windows Mixed Reality involves retargeting usage of vendor-specific VR SDKs to Unity's cross-vendor VR APIs.</span></span>

## <a name="porting-requirements"></a><span data-ttu-id="f987d-108">移植要求</span><span class="sxs-lookup"><span data-stu-id="f987d-108">Porting requirements</span></span>

<span data-ttu-id="f987d-109">在高级别上，迁移现有内容涉及以下步骤：</span><span class="sxs-lookup"><span data-stu-id="f987d-109">At a high level, the following steps are involved in porting existing content:</span></span>
1. <span data-ttu-id="f987d-110">**请确保你的电脑正在运行 Windows 10 秋季创意者更新 (16299) 。**</span><span class="sxs-lookup"><span data-stu-id="f987d-110">**Make sure your PC is running the Windows 10 Fall Creators Update (16299).**</span></span> <span data-ttu-id="f987d-111">我们不再建议从有问必答向后跳环接收预览版，因为这些版本对于混合现实开发不是最稳定的。</span><span class="sxs-lookup"><span data-stu-id="f987d-111">We no longer recommend receiving preview builds from the Insider Skip Ahead ring, as those builds won't be the most stable for mixed reality development.</span></span>
2. <span data-ttu-id="f987d-112">**升级到最新版本的图形或游戏引擎。**</span><span class="sxs-lookup"><span data-stu-id="f987d-112">**Upgrade to the latest version of your graphics or game engine.**</span></span> <span data-ttu-id="f987d-113">游戏引擎需要支持 Windows 10 SDK 版本 10.0.15063.0 (于2017年4月) 或更高版本发布。</span><span class="sxs-lookup"><span data-stu-id="f987d-113">Game engines will need to support the Windows 10 SDK version 10.0.15063.0 (released in April 2017) or higher.</span></span>
3. <span data-ttu-id="f987d-114">**升级任何中间件、插件或组件。**</span><span class="sxs-lookup"><span data-stu-id="f987d-114">**Upgrade any middleware, plug-ins, or components.**</span></span> <span data-ttu-id="f987d-115">如果你的应用程序包含任何组件，则最好升级到最新版本。</span><span class="sxs-lookup"><span data-stu-id="f987d-115">If your app contains any components, it's a good idea to upgrade to the latest version.</span></span>
4. <span data-ttu-id="f987d-116">**删除重复的 sdk 依赖项**。</span><span class="sxs-lookup"><span data-stu-id="f987d-116">**Remove dependencies on duplicate SDKs**.</span></span> <span data-ttu-id="f987d-117">根据你的内容面向哪个设备，你将需要删除或有条件地编译该 SDK，以便可以改为面向 Windows Api。</span><span class="sxs-lookup"><span data-stu-id="f987d-117">Depending on which device your content was targeting, you'll need to remove or conditionally compile out that SDK so you can target the Windows APIs instead.</span></span> <span data-ttu-id="f987d-118">这种情况的一个示例是 SteamVR。</span><span class="sxs-lookup"><span data-stu-id="f987d-118">An example of this scenario would be SteamVR.</span></span>
5. <span data-ttu-id="f987d-119">**处理生成问题。**</span><span class="sxs-lookup"><span data-stu-id="f987d-119">**Work through build issues.**</span></span> <span data-ttu-id="f987d-120">此时，迁移练习特定于您的应用程序、您的引擎和您拥有的组件依赖项。</span><span class="sxs-lookup"><span data-stu-id="f987d-120">At this point, the porting exercise is specific to your app, your engine, and the component dependencies you have.</span></span>

## <a name="common-porting-steps"></a><span data-ttu-id="f987d-121">常见的移植步骤</span><span class="sxs-lookup"><span data-stu-id="f987d-121">Common porting steps</span></span>

### <a name="1-make-sure-you-have-the-right-development-hardware"></a><span data-ttu-id="f987d-122">1. 确保拥有正确的开发硬件</span><span class="sxs-lookup"><span data-stu-id="f987d-122">1. Make sure you have the right development hardware</span></span>

<span data-ttu-id="f987d-123">" [VR 发烧友指南](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines) " 页列出了建议的开发硬件。</span><span class="sxs-lookup"><span data-stu-id="f987d-123">The [VR enthusiast guide](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines) page lists the recommended development hardware.</span></span>

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a><span data-ttu-id="f987d-124">2. 升级到 Windows 10 的最新航班</span><span class="sxs-lookup"><span data-stu-id="f987d-124">2. Upgrade to the latest flight of Windows 10</span></span>

<span data-ttu-id="f987d-125">Windows Mixed Reality 平台仍处于积极开发阶段。</span><span class="sxs-lookup"><span data-stu-id="f987d-125">The Windows Mixed Reality platform is still under active development.</span></span> <span data-ttu-id="f987d-126">建议 [加入 Windows 预览体验计划](https://insider.windows.com/) ，以访问 "Windows 有问必答 Fast" 航班。</span><span class="sxs-lookup"><span data-stu-id="f987d-126">We recommend [joining the Windows Insider Program](https://insider.windows.com/) to access the "Windows Insider Fast" flight.</span></span>
1. <span data-ttu-id="f987d-127">安装 [Windows 10 创意者更新](https://www.microsoft.com/software-download/windows10)</span><span class="sxs-lookup"><span data-stu-id="f987d-127">Install the [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)</span></span>
2. <span data-ttu-id="f987d-128">[加入](https://insider.windows.com/) Windows 预览体验计划。</span><span class="sxs-lookup"><span data-stu-id="f987d-128">[Join](https://insider.windows.com/) the Windows Insider Program.</span></span>
3. <span data-ttu-id="f987d-129">启用 [开发人员模式](/windows/uwp/get-started/enable-your-device-for-development)</span><span class="sxs-lookup"><span data-stu-id="f987d-129">Enable [Developer Mode](/windows/uwp/get-started/enable-your-device-for-development)</span></span>
4. <span data-ttu-id="f987d-130">通过 "**设置" > 更新 & 安全 "部分**，切换到 [Windows 预览体验快速航班](/archive/blogs/uktechnet/joining-insider-preview)</span><span class="sxs-lookup"><span data-stu-id="f987d-130">Switch to the [Windows Insider Fast flights](/archive/blogs/uktechnet/joining-insider-preview) through **Settings > Update & Security Section**</span></span>

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a><span data-ttu-id="f987d-131">3. 升级到最新版本的 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f987d-131">3. Upgrade to the most recent build of Visual Studio</span></span>
* <span data-ttu-id="f987d-132">如果使用的是 Visual Studio，请升级到最新版本</span><span class="sxs-lookup"><span data-stu-id="f987d-132">If you're using Visual Studio, then upgrade to the most recent build</span></span>
* <span data-ttu-id="f987d-133">请参阅 Visual Studio 2019 下 [的安装工具](../install-the-tools.md#installation-checklist) 页面</span><span class="sxs-lookup"><span data-stu-id="f987d-133">See [Install the tools](../install-the-tools.md#installation-checklist) page under Visual Studio 2019</span></span>

### <a name="4-choose-the-correct-adapter"></a><span data-ttu-id="f987d-134">4. 选择正确的适配器</span><span class="sxs-lookup"><span data-stu-id="f987d-134">4. Choose the correct Adapter</span></span>
* <span data-ttu-id="f987d-135">在包含两个 Gpu 的笔记本系统中， [针对正确的适配器](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)。</span><span class="sxs-lookup"><span data-stu-id="f987d-135">In systems like notebooks with two GPUs, [target the correct adapter](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications).</span></span> <span data-ttu-id="f987d-136">这适用于 Unity 和本机 DirectX 应用，其中 ID3D11Device 是显式或隐式 (为其功能媒体基础) 创建的。</span><span class="sxs-lookup"><span data-stu-id="f987d-136">This applies to Unity and native DirectX apps where a ID3D11Device is created, either explicitly or implicitly (Media Foundation), for its functionality.</span></span>

## <a name="unity-porting-guidance"></a><span data-ttu-id="f987d-137">Unity 移植指南</span><span class="sxs-lookup"><span data-stu-id="f987d-137">Unity porting guidance</span></span>

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a><span data-ttu-id="f987d-138">Unreal 移植指南</span><span class="sxs-lookup"><span data-stu-id="f987d-138">Unreal porting guidance</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f987d-139">如果你使用的是 HP 回音 G2 控制器，请参阅 [此文](../unreal/unreal-reverb-g2-controllers.md) ，了解更多输入映射说明。</span><span class="sxs-lookup"><span data-stu-id="f987d-139">If you're using HP Reverb G2 controllers, please refer to [this article](../unreal/unreal-reverb-g2-controllers.md) for additional input mapping instructions.</span></span>

## <a name="see-also"></a><span data-ttu-id="f987d-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f987d-140">See also</span></span>
* [<span data-ttu-id="f987d-141">Windows Mixed Reality 最小电脑硬件兼容性指南</span><span class="sxs-lookup"><span data-stu-id="f987d-141">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [<span data-ttu-id="f987d-142">了解混合现实的性能</span><span class="sxs-lookup"><span data-stu-id="f987d-142">Understanding Performance for Mixed Reality</span></span>](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="f987d-143">Unity 性能建议</span><span class="sxs-lookup"><span data-stu-id="f987d-143">Performance Recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="f987d-144">运动控制器</span><span class="sxs-lookup"><span data-stu-id="f987d-144">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="f987d-145">Unity 中的运动控制器</span><span class="sxs-lookup"><span data-stu-id="f987d-145">Motion controllers in Unity</span></span>](../unity/motion-controllers-in-unity.md)
* [<span data-ttu-id="f987d-146">UnityEngine. XR</span><span class="sxs-lookup"><span data-stu-id="f987d-146">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="f987d-147">UnityEngine. XR. InputTracking</span><span class="sxs-lookup"><span data-stu-id="f987d-147">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="f987d-148">移植指南</span><span class="sxs-lookup"><span data-stu-id="f987d-148">Porting guides</span></span>](porting-guides.md)