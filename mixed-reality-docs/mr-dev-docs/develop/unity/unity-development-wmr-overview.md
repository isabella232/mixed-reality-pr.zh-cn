---
title: 针对 VR 的 Unity 开发
description: 开始在适合 VR 和 Windows Mixed Reality 沉浸式头戴显示设备的 Unity 中构建混合现实应用。
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合现实, 开发, 入门, 新项目, 移植, 功能, 相机, 模拟, 仿真, 文档, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 什么是虚拟现实, 什么是增强现实, MRTK, 混合现实工具包, 语音输入, 可定位相机, 仿真器, Azure, 教程
ms.openlocfilehash: 50300ff08dd06c5fc250bc93979d537e10b38044
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528712"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a><span data-ttu-id="415d6-104">针对 VR 和 Windows Mixed Reality 的 Unity 开发</span><span class="sxs-lookup"><span data-stu-id="415d6-104">Unity development for VR and Windows Mixed Reality</span></span>

![Unity 横幅徽标](../images/unity_logo_banner.png)

<span data-ttu-id="415d6-106">如果你尚不熟悉 Unity，我们建议你先在 Unity Learn 平台上浏览初学者级别[教程](https://unity3d.com/learn/tutorials)，然后再继续操作。</span><span class="sxs-lookup"><span data-stu-id="415d6-106">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="415d6-107">还有一个好主意是访问 [Unity 混合现实论坛](https://forum.unity3d.com/forums/hololens.102/)，与在线社区一起构建混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="415d6-107">It's also a good idea to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="415d6-108">你永远都不知道你可能会在未知领域发现什么样的绝佳资产或解决方案。</span><span class="sxs-lookup"><span data-stu-id="415d6-108">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="415d6-109">准备好开始使用 MRTK 时，请前往下面的开发检查点！</span><span class="sxs-lookup"><span data-stu-id="415d6-109">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="415d6-110">如果你当前有一个想要引入到 Windows Mixed Reality 沉浸式头戴显示设备的 Unity 项目，请查看[移植指南](../porting-apps/porting-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="415d6-110">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to a Windows Mixed Reality immersive headset.</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="415d6-111">开发检查点</span><span class="sxs-lookup"><span data-stu-id="415d6-111">Development checkpoints</span></span>

<span data-ttu-id="415d6-112">使用以下检查点，将 Unity 游戏和应用程序带入混合现实的世界。</span><span class="sxs-lookup"><span data-stu-id="415d6-112">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> 

### <a name="1-getting-started"></a><span data-ttu-id="415d6-113">1.入门</span><span class="sxs-lookup"><span data-stu-id="415d6-113">1. Getting started</span></span>

<span data-ttu-id="415d6-114">对于 Windows Mixed Reality 和 VR 开发，有少量的 Unity 设置需要你手动进行更改。</span><span class="sxs-lookup"><span data-stu-id="415d6-114">There are a small set of Unity settings you'll need to manually change for Windows Mixed Reality and VR development.</span></span> <span data-ttu-id="415d6-115">这些设置分为两个类别：按项目设置和按场景设置。</span><span class="sxs-lookup"><span data-stu-id="415d6-115">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="415d6-116">本部分结束时，你将获得工具和项目设置来开始创建自己的应用！</span><span class="sxs-lookup"><span data-stu-id="415d6-116">By the end of this section, you'll have the tools and project settings to start creating your own apps!</span></span>

|  <span data-ttu-id="415d6-117">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="415d6-117">Checkpoint</span></span>  |  <span data-ttu-id="415d6-118">业务成效</span><span class="sxs-lookup"><span data-stu-id="415d6-118">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="415d6-119">安装最新工具</span><span class="sxs-lookup"><span data-stu-id="415d6-119">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="415d6-120">下载并安装最新 Unity 包，并为混合现实设置你的项目</span><span class="sxs-lookup"><span data-stu-id="415d6-120">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="415d6-121">针对 WMR 配置项目</span><span class="sxs-lookup"><span data-stu-id="415d6-121">Configuring your project for WMR</span></span>](windows-xr-plugin.md) | <span data-ttu-id="415d6-122">了解如何构建在全息和 VR 显示设备上呈现数字内容的应用程序</span><span class="sxs-lookup"><span data-stu-id="415d6-122">Learn how to build applications that render digital content on holographic and VR display devices</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="415d6-123">若要详细了解如何设置项目，请查看我们的 Unity 项目[配置指南](choosing-unity-version.md)。</span><span class="sxs-lookup"><span data-stu-id="415d6-123">Check out our Unity project [configuration guide](choosing-unity-version.md) for more information on setting up your projects.</span></span>

### <a name="2-core-building-blocks"></a><span data-ttu-id="415d6-124">2.核心构建基块</span><span class="sxs-lookup"><span data-stu-id="415d6-124">2. Core building blocks</span></span>

<span data-ttu-id="415d6-125">启动新的沉浸式项目后，你需要一些基本的构建基块来开发沉浸式应用。</span><span class="sxs-lookup"><span data-stu-id="415d6-125">After starting a new immersive project, you'll need some basic building blocks to develop immersive apps.</span></span> <span data-ttu-id="415d6-126">混合现实应用程序的所有核心构建基块的公开方式与其他 Unity API 一致。</span><span class="sxs-lookup"><span data-stu-id="415d6-126">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="415d6-127">你可能不需要一次全部使用它们，但建议你尽早进行使用。</span><span class="sxs-lookup"><span data-stu-id="415d6-127">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="415d6-128">深入了解下面列出的核心构建基块后，你将拥有一个工具箱，其中包含了你可集成到 VR 项目中的各种功能。</span><span class="sxs-lookup"><span data-stu-id="415d6-128">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a VR project.</span></span>

|  <span data-ttu-id="415d6-129">功能</span><span class="sxs-lookup"><span data-stu-id="415d6-129">Feature</span></span>  |  <span data-ttu-id="415d6-130">功能</span><span class="sxs-lookup"><span data-stu-id="415d6-130">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="415d6-131">摄像头</span><span class="sxs-lookup"><span data-stu-id="415d6-131">Camera</span></span>](../unity/camera-in-unity.md) | <span data-ttu-id="415d6-132">全面优化混合现实应用中的视觉质量和全息影像稳定性</span><span class="sxs-lookup"><span data-stu-id="415d6-132">Fully optimize visual quality and hologram stability in your Mixed Reality apps</span></span> |
| [<span data-ttu-id="415d6-133">世界锁定和空间定位点</span><span class="sxs-lookup"><span data-stu-id="415d6-133">World locking and spatial anchors</span></span>](spatial-anchors-in-unity.md) | <span data-ttu-id="415d6-134">解决稳定性问题、相机调整并集成稳定的坐标系解决方案</span><span class="sxs-lookup"><span data-stu-id="415d6-134">Solve stabilization issues, camera adjustment, and integrate a stable coordinate system solution</span></span> || [<span data-ttu-id="415d6-135">运动控制器</span><span class="sxs-lookup"><span data-stu-id="415d6-135">Motion controllers</span></span>](../unity/motion-controllers-in-unity.md) | <span data-ttu-id="415d6-136">向混合现实应用添加空间操作</span><span class="sxs-lookup"><span data-stu-id="415d6-136">Add spatial actions to your Mixed Reality apps</span></span> |
| [<span data-ttu-id="415d6-137">笔势</span><span class="sxs-lookup"><span data-stu-id="415d6-137">Gestures</span></span>](../unity/gestures-in-unity.md) | <span data-ttu-id="415d6-138">在混合现实体验中将手势作为输入内容</span><span class="sxs-lookup"><span data-stu-id="415d6-138">Use hand gestures as input in your Mixed Reality experiences</span></span> |
| [<span data-ttu-id="415d6-139">空间音效</span><span class="sxs-lookup"><span data-stu-id="415d6-139">Spatial sound</span></span>](../unity/spatial-sound-in-unity.md) | <span data-ttu-id="415d6-140">使用沉浸式 3D 音频增强应用</span><span class="sxs-lookup"><span data-stu-id="415d6-140">Enhance your apps with immersive 3D audio</span></span> |
| [<span data-ttu-id="415d6-141">Text</span><span class="sxs-lookup"><span data-stu-id="415d6-141">Text</span></span>](../unity/text-in-unity.md) | <span data-ttu-id="415d6-142">获得清晰的高质量文本，其具有可管理的大小和质量渲染</span><span class="sxs-lookup"><span data-stu-id="415d6-142">Get sharp, high-quality text that has a manageable size and quality rendering</span></span> |
| [<span data-ttu-id="415d6-143">语音输入</span><span class="sxs-lookup"><span data-stu-id="415d6-143">Voice input</span></span>](../unity/voice-input-in-unity.md) | <span data-ttu-id="415d6-144">捕获用户的口语关键字、短语和听写</span><span class="sxs-lookup"><span data-stu-id="415d6-144">Capture spoken keywords, phrases, and dictation from your users</span></span>|

### <a name="3-advanced-features"></a><span data-ttu-id="415d6-145">3.高级功能</span><span class="sxs-lookup"><span data-stu-id="415d6-145">3. Advanced features</span></span>

<span data-ttu-id="415d6-146">在沉浸式应用程序中起作用的其他关键功能可通过 Unity API 获得，无需任何额外的包或设置。</span><span class="sxs-lookup"><span data-stu-id="415d6-146">Other key features that play a role in immersive applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="415d6-147">深入了解 Unity 提供的更高级功能后，你将能够生成更深层、更复杂的 VR 应用。</span><span class="sxs-lookup"><span data-stu-id="415d6-147">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex VR apps.</span></span>

|  <span data-ttu-id="415d6-148">功能</span><span class="sxs-lookup"><span data-stu-id="415d6-148">Feature</span></span>  |  <span data-ttu-id="415d6-149">功能</span><span class="sxs-lookup"><span data-stu-id="415d6-149">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="415d6-150">失跟</span><span class="sxs-lookup"><span data-stu-id="415d6-150">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="415d6-151">处理设备无法在应用程序世界空间中定位自己的情况</span><span class="sxs-lookup"><span data-stu-id="415d6-151">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="415d6-152">键盘输入</span><span class="sxs-lookup"><span data-stu-id="415d6-152">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="415d6-153">在应用中获取来自现实世界和混合现实键盘的输入</span><span class="sxs-lookup"><span data-stu-id="415d6-153">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="415d6-154">4.部署到设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="415d6-154">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="415d6-155">准备好对全息 Unity 项目进行测试以后，下一步是导出和构建 Unity Visual Studio 解决方案。</span><span class="sxs-lookup"><span data-stu-id="415d6-155">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="415d6-156">有了该 VS 解决方案后，即可在真实的或模拟的设备运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="415d6-156">With that VS solution in hand, you can run your application on real or simulated devices.</span></span> <span data-ttu-id="415d6-157">本部分结束后，你将能够在适合你的开发需求的设备或仿真器上部署应用程序。</span><span class="sxs-lookup"><span data-stu-id="415d6-157">By the end of this section, you'll be able to deploy your application on a device or emulator that fits your development needs.</span></span>

* [<span data-ttu-id="415d6-158">Windows Mixed Reality 沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="415d6-158">Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="415d6-159">Windows Mixed Reality 沉浸式头戴显示设备模拟器</span><span class="sxs-lookup"><span data-stu-id="415d6-159">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a><span data-ttu-id="415d6-160">下一步操作</span><span class="sxs-lookup"><span data-stu-id="415d6-160">What's next?</span></span>

<span data-ttu-id="415d6-161">开发人员的工作一直在更新，特别是在学习新工具或 SDK 时。</span><span class="sxs-lookup"><span data-stu-id="415d6-161">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="415d6-162">以下部分将带你进入你已完成的初学者级别资料之外的其他领域，并在你遇到问题时提供有用的资源。</span><span class="sxs-lookup"><span data-stu-id="415d6-162">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="415d6-163">请注意，这些主题和资源不按任何顺序排列，因此请随意查看并探索！</span><span class="sxs-lookup"><span data-stu-id="415d6-163">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="415d6-164">移植</span><span class="sxs-lookup"><span data-stu-id="415d6-164">Porting</span></span>

<span data-ttu-id="415d6-165">如果你当前有想要移植的应用，那么接下来请查看以下文章：</span><span class="sxs-lookup"><span data-stu-id="415d6-165">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="415d6-166">将 VR 应用移植到 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="415d6-166">Porting VR apps to Windows Mixed Reality</span></span>](../porting-apps/porting-guides.md?tabs=project)
* [<span data-ttu-id="415d6-167">更新适用于 Windows Mixed Reality 的 SteamVR 应用</span><span class="sxs-lookup"><span data-stu-id="415d6-167">Updating SteamVR apps for Windows Mixed Reality</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="additional-resources"></a><span data-ttu-id="415d6-168">其他资源</span><span class="sxs-lookup"><span data-stu-id="415d6-168">Additional resources</span></span>

<span data-ttu-id="415d6-169">在你自己进入混合现实世界之前，建议先阅读下面的额外文档。</span><span class="sxs-lookup"><span data-stu-id="415d6-169">Before going out into the world of mixed reality on your own, we recommend taking a look at the extra documentation below.</span></span> 

* [<span data-ttu-id="415d6-170">VR 发烧友指南</span><span class="sxs-lookup"><span data-stu-id="415d6-170">VR enthusiast guide</span></span>](/windows/mixed-reality/enthusiast-guide/vr-journey)
* [<span data-ttu-id="415d6-171">Unity Asset Store</span><span class="sxs-lookup"><span data-stu-id="415d6-171">Unity Asset Store</span></span>](https://assetstore.unity.com)

## <a name="see-also"></a><span data-ttu-id="415d6-172">请参阅</span><span class="sxs-lookup"><span data-stu-id="415d6-172">See also</span></span> 

* [<span data-ttu-id="415d6-173">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="415d6-173">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="415d6-174">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="415d6-174">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="415d6-175">导出和构建 Unity Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="415d6-175">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="415d6-176">使用 Unity 和 Visual Studio 的最佳做法</span><span class="sxs-lookup"><span data-stu-id="415d6-176">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)