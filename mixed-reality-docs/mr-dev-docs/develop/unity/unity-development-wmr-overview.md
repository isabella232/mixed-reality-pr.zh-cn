---
title: 针对 VR 的 Unity 开发
description: 开始在适合 VR 和 Windows Mixed Reality 沉浸式头戴显示设备的 Unity 中构建混合现实应用。
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合现实, 开发, 入门, 新项目, 移植, 功能, 相机, 模拟, 仿真, 文档, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 什么是虚拟现实, 什么是增强现实, MRTK, 混合现实工具包, 语音输入, 可定位相机, 仿真器, Azure, 教程
ms.openlocfilehash: edd75def71ad31a1d29a480d0b2a7f7ffbd8c037
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226426"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a><span data-ttu-id="b946a-104">针对 VR 和 Windows Mixed Reality 的 Unity 开发</span><span class="sxs-lookup"><span data-stu-id="b946a-104">Unity development for VR and Windows Mixed Reality</span></span>

![Unity 横幅徽标](../images/unity_logo_banner.png)

<span data-ttu-id="b946a-106">如果你尚不熟悉 Unity，我们建议你先在 Unity Learn 平台上浏览初学者级别[教程](https://unity3d.com/learn/tutorials)，然后再继续操作。</span><span class="sxs-lookup"><span data-stu-id="b946a-106">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="b946a-107">还有一个好主意是访问 [Unity 混合现实论坛](https://forum.unity3d.com/forums/hololens.102/)，与在线社区一起构建混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="b946a-107">It's also a good idea to visit the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="b946a-108">你永远都不知道你可能会在未知领域发现什么样的绝佳资产或解决方案。</span><span class="sxs-lookup"><span data-stu-id="b946a-108">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="b946a-109">准备好开始使用 MRTK 时，请前往下面的开发检查点！</span><span class="sxs-lookup"><span data-stu-id="b946a-109">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b946a-110">如果你当前有一个想要引入到 Windows Mixed Reality 沉浸式头戴显示设备的 Unity 项目，请查看[移植指南](../porting-apps/porting-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b946a-110">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to a Windows Mixed Reality immersive headset.</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="b946a-111">开发检查点</span><span class="sxs-lookup"><span data-stu-id="b946a-111">Development checkpoints</span></span>

<span data-ttu-id="b946a-112">使用以下检查点，将 Unity 游戏和应用程序带入混合现实的世界。</span><span class="sxs-lookup"><span data-stu-id="b946a-112">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> 

### <a name="1-getting-started"></a><span data-ttu-id="b946a-113">1.入门</span><span class="sxs-lookup"><span data-stu-id="b946a-113">1. Getting started</span></span>

<span data-ttu-id="b946a-114">对于 Windows Mixed Reality 和 VR 开发，有少量的 Unity 设置需要你手动进行更改。</span><span class="sxs-lookup"><span data-stu-id="b946a-114">There are a small set of Unity settings you'll need to manually change for Windows Mixed Reality and VR developoment.</span></span> <span data-ttu-id="b946a-115">这些设置分为两个类别：按项目设置和按场景设置。</span><span class="sxs-lookup"><span data-stu-id="b946a-115">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="b946a-116">本部分结束时，你将获得工具和项目设置来开始创建自己的应用！</span><span class="sxs-lookup"><span data-stu-id="b946a-116">By the end of this section, you'll have the tools and project settings to start creating your own apps!</span></span>

|  <span data-ttu-id="b946a-117">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="b946a-117">Checkpoint</span></span>  |  <span data-ttu-id="b946a-118">业务成效</span><span class="sxs-lookup"><span data-stu-id="b946a-118">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="b946a-119">安装最新工具</span><span class="sxs-lookup"><span data-stu-id="b946a-119">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="b946a-120">下载并安装最新 Unity 包，并为混合现实设置你的项目</span><span class="sxs-lookup"><span data-stu-id="b946a-120">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="b946a-121">针对 WMR 配置项目</span><span class="sxs-lookup"><span data-stu-id="b946a-121">Configuring your project for WMR</span></span>](configure-unity-project.md) | <span data-ttu-id="b946a-122">了解如何构建在全息和 VR 显示设备上呈现数字内容的应用程序</span><span class="sxs-lookup"><span data-stu-id="b946a-122">Learn how to build applications that render digital content on holographic and VR display devices</span></span> |

### <a name="2-core-building-blocks"></a><span data-ttu-id="b946a-123">2.核心构建基块</span><span class="sxs-lookup"><span data-stu-id="b946a-123">2. Core building blocks</span></span>

<span data-ttu-id="b946a-124">启动新的沉浸式项目后，你需要一些基本的构建基块来开发沉浸式应用。</span><span class="sxs-lookup"><span data-stu-id="b946a-124">After starting a new immersive project, you'll need some basic building blocks to develop immersive apps.</span></span> <span data-ttu-id="b946a-125">混合现实应用程序的所有核心构建基块的公开方式与其他 Unity API 一致。</span><span class="sxs-lookup"><span data-stu-id="b946a-125">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="b946a-126">你可能不需要一次全部使用它们，但建议你尽早进行使用。</span><span class="sxs-lookup"><span data-stu-id="b946a-126">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="b946a-127">深入了解下面列出的核心构建基块后，你将拥有一个工具箱，其中包含了你可集成到 VR 项目中的各种功能。</span><span class="sxs-lookup"><span data-stu-id="b946a-127">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a VR project.</span></span>

[!INCLUDE[](../includes/unity-building-blocks-wmr.md)]

### <a name="3-advanced-features"></a><span data-ttu-id="b946a-128">3.高级功能</span><span class="sxs-lookup"><span data-stu-id="b946a-128">3. Advanced features</span></span>

<span data-ttu-id="b946a-129">在沉浸式应用程序中起作用的其他关键功能可通过 Unity API 获得，无需任何额外的包或设置。</span><span class="sxs-lookup"><span data-stu-id="b946a-129">Other key features that play a role in immersive applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="b946a-130">深入了解 Unity 提供的更高级功能后，你将能够生成更深层、更复杂的 VR 应用。</span><span class="sxs-lookup"><span data-stu-id="b946a-130">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex VR apps.</span></span>

|  <span data-ttu-id="b946a-131">功能</span><span class="sxs-lookup"><span data-stu-id="b946a-131">Feature</span></span>  |  <span data-ttu-id="b946a-132">功能</span><span class="sxs-lookup"><span data-stu-id="b946a-132">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="b946a-133">失跟</span><span class="sxs-lookup"><span data-stu-id="b946a-133">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="b946a-134">处理设备无法在应用程序世界空间中定位自己的情况</span><span class="sxs-lookup"><span data-stu-id="b946a-134">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="b946a-135">键盘输入</span><span class="sxs-lookup"><span data-stu-id="b946a-135">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="b946a-136">在应用中获取来自现实世界和混合现实键盘的输入</span><span class="sxs-lookup"><span data-stu-id="b946a-136">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="b946a-137">4.部署到设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="b946a-137">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="b946a-138">准备好对全息 Unity 项目进行测试以后，下一步是导出和构建 Unity Visual Studio 解决方案。</span><span class="sxs-lookup"><span data-stu-id="b946a-138">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="b946a-139">有了该 VS 解决方案后，即可在真实的或模拟的设备运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="b946a-139">With that VS solution in hand, you can run your application on real or simulated devices.</span></span> <span data-ttu-id="b946a-140">本部分结束后，你将能够在适合你的开发需求的设备或仿真器上部署应用程序。</span><span class="sxs-lookup"><span data-stu-id="b946a-140">By the end of this section, you'll be able to deploy your application on a device or emulator that fits your development needs.</span></span>

* [<span data-ttu-id="b946a-141">Windows Mixed Reality 沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="b946a-141">Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="b946a-142">Windows Mixed Reality 沉浸式头戴显示设备模拟器</span><span class="sxs-lookup"><span data-stu-id="b946a-142">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a><span data-ttu-id="b946a-143">下一步操作</span><span class="sxs-lookup"><span data-stu-id="b946a-143">What's next?</span></span>

<span data-ttu-id="b946a-144">开发人员的工作一直在更新，特别是在学习新工具或 SDK 时。</span><span class="sxs-lookup"><span data-stu-id="b946a-144">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="b946a-145">以下部分将带你进入你已完成的初学者级别资料之外的其他领域，并在你遇到问题时提供有用的资源。</span><span class="sxs-lookup"><span data-stu-id="b946a-145">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="b946a-146">请注意，这些主题和资源不按任何顺序排列，因此请随意查看并探索！</span><span class="sxs-lookup"><span data-stu-id="b946a-146">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="b946a-147">移植</span><span class="sxs-lookup"><span data-stu-id="b946a-147">Porting</span></span>

<span data-ttu-id="b946a-148">如果你当前有想要移植的应用，那么接下来请查看以下文章：</span><span class="sxs-lookup"><span data-stu-id="b946a-148">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="b946a-149">将 VR 应用移植到 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b946a-149">Porting VR apps to Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project)
* [<span data-ttu-id="b946a-150">更新适用于 Windows Mixed Reality 的 SteamVR 应用</span><span class="sxs-lookup"><span data-stu-id="b946a-150">Updating SteamVR apps for Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality)

### <a name="additional-resources"></a><span data-ttu-id="b946a-151">其他资源</span><span class="sxs-lookup"><span data-stu-id="b946a-151">Additional resources</span></span>

<span data-ttu-id="b946a-152">在你自己进入混合现实世界之前，建议先阅读下面的额外文档。</span><span class="sxs-lookup"><span data-stu-id="b946a-152">Before going out into the world of mixed reality on your own, we recommend taking a look at the extra documentation below.</span></span> 

* [<span data-ttu-id="b946a-153">VR 发烧友指南</span><span class="sxs-lookup"><span data-stu-id="b946a-153">VR enthusiast guide</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/vr-journey)
* [<span data-ttu-id="b946a-154">Unity Asset Store</span><span class="sxs-lookup"><span data-stu-id="b946a-154">Unity Asset Store</span></span>](https://www.assetstore.unity3d.com)

## <a name="see-also"></a><span data-ttu-id="b946a-155">请参阅</span><span class="sxs-lookup"><span data-stu-id="b946a-155">See also</span></span> 

* [<span data-ttu-id="b946a-156">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="b946a-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="b946a-157">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="b946a-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="b946a-158">导出和构建 Unity Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="b946a-158">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="b946a-159">使用 Unity 和 Visual Studio 的最佳做法</span><span class="sxs-lookup"><span data-stu-id="b946a-159">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
