---
title: 针对 HoloLens 的 Unity 开发
description: 通过我们精选的检查点旅程开始在 Unity 和 HoloLens 中构建混合现实应用。
author: hferrone
ms.author: kurtie
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合现实, 开发, 入门, 新项目, 移植, 功能, 相机, 模拟, 仿真, 文档, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 什么是虚拟现实, 什么是增强现实, MRTK, 混合现实工具包, 空间映射, 语音输入, 可定位相机, 仿真器, Azure, 教程
ms.openlocfilehash: 59bb269bfb8d7e0a9cfd6963cf144ddb0e070c5f
ms.sourcegitcommit: 1304f8f0a838290c1ae3db34670b67c75ea9bdaa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/02/2021
ms.locfileid: "99421406"
---
# <a name="unity-development-for-hololens"></a><span data-ttu-id="19a5c-104">针对 HoloLens 的 Unity 开发</span><span class="sxs-lookup"><span data-stu-id="19a5c-104">Unity development for HoloLens</span></span>

![Unity 横幅徽标](../images/unity_logo_banner.png)

<span data-ttu-id="19a5c-106">在 [Unity](https://unity.com) 中生成 HoloLens [混合现实应用](../../design/app-views.md)的最快途径是使用混合现实工具包。</span><span class="sxs-lookup"><span data-stu-id="19a5c-106">The fastest path to building a HoloLens [mixed reality app](../../design/app-views.md) in [Unity](https://unity.com) is with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="19a5c-107">如果你尚不熟悉 Unity，我们建议你先在 Unity Learn 平台上浏览初学者级别[教程](https://unity3d.com/learn/tutorials)，然后再继续操作。</span><span class="sxs-lookup"><span data-stu-id="19a5c-107">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="19a5c-108">访问综合性的 [Asset Store](https://www.assetstore.unity3d.com/) 和 [Unity 混合现实论坛](https://forum.unity3d.com/forums/hololens.102/)，与在线社区一起生成混合现实应用程序也是一个好主意。</span><span class="sxs-lookup"><span data-stu-id="19a5c-108">It's also a good idea to visit the comprehensive [Asset Store](https://www.assetstore.unity3d.com/) and the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="19a5c-109">你永远都不知道你可能会在未知领域发现什么样的绝佳资产或解决方案。</span><span class="sxs-lookup"><span data-stu-id="19a5c-109">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="19a5c-110">准备好开始使用 MRTK 时，请前往下面的开发检查点！</span><span class="sxs-lookup"><span data-stu-id="19a5c-110">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="19a5c-111">如果你有一个想要引入到 HoloLens 2 的现有 Unity 项目，请查看 **[移植指南](../porting-apps/porting-overview.md)** 。</span><span class="sxs-lookup"><span data-stu-id="19a5c-111">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to HoloLens 2.</span></span> <span data-ttu-id="19a5c-112">我们有指南针对正在使用 HTK、MRTK v1 或 SteamVR 的项目。</span><span class="sxs-lookup"><span data-stu-id="19a5c-112">We have guides for projects that are using HTK, MRTK v1, or SteamVR.</span></span>

## <a name="development-checkpoints"></a><span data-ttu-id="19a5c-113">开发检查点</span><span class="sxs-lookup"><span data-stu-id="19a5c-113">Development checkpoints</span></span>

<span data-ttu-id="19a5c-114">使用以下检查点，将 Unity 游戏和应用程序带入混合现实的世界。</span><span class="sxs-lookup"><span data-stu-id="19a5c-114">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> <span data-ttu-id="19a5c-115">如果你尚未浏览[设计全息影像示例应用程序](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)，我们建议下载并使用它来熟悉混合现实 UX 的基本知识。</span><span class="sxs-lookup"><span data-stu-id="19a5c-115">If you haven't already explored the [Designing Holograms sample application](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), we recommend downloading and using it to familiarize yourself with the basics of Mixed Reality UX.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="19a5c-116">1.入门</span><span class="sxs-lookup"><span data-stu-id="19a5c-116">1. Getting started</span></span>

<span data-ttu-id="19a5c-117">若要在 Unity 中进行开发，最简单的方法是使用混合现实工具包。</span><span class="sxs-lookup"><span data-stu-id="19a5c-117">The easiest way to develop in Unity is with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="19a5c-118">MRTK 将帮助你自动为混合现实设置项目，并提供一组功能以加速开发过程。</span><span class="sxs-lookup"><span data-stu-id="19a5c-118">MRTK will help you automatically setup a project for Mixed Reality and provide a set of features to accelerate your development process.</span></span> <span data-ttu-id="19a5c-119">本部分结束时，你将对混合现实工具包有一个基本的了解、对混合现实应用有一个正确配置的开发环境以及一个你自己构建的、可在 Unity 中正常工作的 MRTK 项目。</span><span class="sxs-lookup"><span data-stu-id="19a5c-119">By the end of this section, you'll have a basic understanding of the Mixed Reality Toolkit, a properly configured development environment for Mixed Reality apps, and a working MRTK project in Unity that you built yourself.</span></span>

|  <span data-ttu-id="19a5c-120">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="19a5c-120">Checkpoint</span></span>  |  <span data-ttu-id="19a5c-121">业务成效</span><span class="sxs-lookup"><span data-stu-id="19a5c-121">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="19a5c-122">什么是 MRTK？</span><span class="sxs-lookup"><span data-stu-id="19a5c-122">What is MRTK?</span></span>](mrtk-getting-started.md) | <span data-ttu-id="19a5c-123">通过熟悉混合现实工具包及其所提供的功能开始历程</span><span class="sxs-lookup"><span data-stu-id="19a5c-123">Begin your journey by getting acquainted with the Mixed Reality Toolkit and what it has to offer</span></span> |
| [<span data-ttu-id="19a5c-124">安装最新工具</span><span class="sxs-lookup"><span data-stu-id="19a5c-124">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="19a5c-125">下载并安装最新 Unity 包，并为混合现实设置你的项目</span><span class="sxs-lookup"><span data-stu-id="19a5c-125">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="19a5c-126">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="19a5c-126">HoloLens 2 tutorial series</span></span>](tutorials/mr-learning-base-01.md) | <span data-ttu-id="19a5c-127">深入研究 HoloLens 2 硬件的初学者级别 MRTK 教程</span><span class="sxs-lookup"><span data-stu-id="19a5c-127">Dive into beginner level MRTK tutorials for HoloLens 2 hardware</span></span> |
| <span data-ttu-id="19a5c-128">**可选** [下载混合现实功能工具](welcome-to-mr-feature-tool.md)</span><span class="sxs-lookup"><span data-stu-id="19a5c-128">**Optional** [Download the Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)</span></span> | <span data-ttu-id="19a5c-129">用于发现、更新混合现实功能包并将其添加到 Unity 项目的全新开发人员工具</span><span class="sxs-lookup"><span data-stu-id="19a5c-129">A new developer tool for discovering, updating, and adding Mixed Reality feature packages to your Unity projects</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="19a5c-130">若要在不导入混合现实工具包的情况下创建新的 Unity 项目，需针对 Windows Mixed Reality 手动更改一小组 Unity 设置。</span><span class="sxs-lookup"><span data-stu-id="19a5c-130">If you'd like to create a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality.</span></span> <span data-ttu-id="19a5c-131">这些设置分为两个类别：按项目设置和按场景设置。</span><span class="sxs-lookup"><span data-stu-id="19a5c-131">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="19a5c-132">有关分步过程，请参阅我们的[配置指南](configure-unity-project.md)。</span><span class="sxs-lookup"><span data-stu-id="19a5c-132">Take a look at our [configuration guide](configure-unity-project.md) for the step-by-step process.</span></span>

> [!NOTE]
> <span data-ttu-id="19a5c-133">在项目中设置 MRTK V2，标准的 Unity 游戏对象（例如相机）就会立即启动，为你带来坐定式体验。</span><span class="sxs-lookup"><span data-stu-id="19a5c-133">Once you've setup MRTK V2 in your project, standard Unity game objects like the camera will light up immediately for a seated-scale experience.</span></span> <span data-ttu-id="19a5c-134">可在[坐标系统](coordinate-systems-in-unity.md)页面上找到有关更改应用程序的体验范围的说明。</span><span class="sxs-lookup"><span data-stu-id="19a5c-134">You can find instructions on changing the experience scale of your application on the [coordinate systems](coordinate-systems-in-unity.md) page.</span></span>

### <a name="2-core-building-blocks"></a><span data-ttu-id="19a5c-135">2.核心构建基块</span><span class="sxs-lookup"><span data-stu-id="19a5c-135">2. Core building blocks</span></span>

<span data-ttu-id="19a5c-136">混合现实应用程序的所有核心构建基块的公开方式与其他 Unity API 一致。</span><span class="sxs-lookup"><span data-stu-id="19a5c-136">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="19a5c-137">这些构建基块可以作为独立功能提供，也可以通过混合现实工具包提供。</span><span class="sxs-lookup"><span data-stu-id="19a5c-137">These building blocks are available as standalone features and through the Mixed Reality Toolkit.</span></span> <span data-ttu-id="19a5c-138">你可能不需要一次全部使用它们，但建议你尽早进行使用。</span><span class="sxs-lookup"><span data-stu-id="19a5c-138">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="19a5c-139">深入了解下面列出的核心构建基块后，你将拥有一个工具箱，其中包含了各种你可以集成到混合现实项目中的功能（通过这些功能本身或通过 MRTK 实现）。</span><span class="sxs-lookup"><span data-stu-id="19a5c-139">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a Mixed Reality project by themselves or through MRTK.</span></span>

[!INCLUDE[](../includes/unity-building-blocks.md)]

### <a name="3-advanced-features"></a><span data-ttu-id="19a5c-140">3.高级功能</span><span class="sxs-lookup"><span data-stu-id="19a5c-140">3. Advanced features</span></span>

<span data-ttu-id="19a5c-141">在混合现实应用程序中起作用的其他关键功能可通过 Unity API 获得，而无需任何额外的包或设置。</span><span class="sxs-lookup"><span data-stu-id="19a5c-141">Other key features that play a role in mixed reality applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="19a5c-142">可以在安装或未安装 MRTK 的情况下将这些功能添加到 Unity 项目中。</span><span class="sxs-lookup"><span data-stu-id="19a5c-142">These features can be added to Unity projects with or without MRTK installed.</span></span> <span data-ttu-id="19a5c-143">深入了解 Unity 提供的更高级功能后，你将能够生成更深层、更复杂的混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="19a5c-143">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex Mixed Reality apps.</span></span>

|  <span data-ttu-id="19a5c-144">功能</span><span class="sxs-lookup"><span data-stu-id="19a5c-144">Feature</span></span>  |  <span data-ttu-id="19a5c-145">功能</span><span class="sxs-lookup"><span data-stu-id="19a5c-145">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="19a5c-146">共享体验</span><span class="sxs-lookup"><span data-stu-id="19a5c-146">Shared experiences</span></span>](shared-experiences-in-unity.md) | <span data-ttu-id="19a5c-147">使用空间定位点共享，在空间中的固定点共同观看同一全息影像并与之交互</span><span class="sxs-lookup"><span data-stu-id="19a5c-147">View and interact collectively with the same hologram at a fixed point in space using spatial anchor sharing</span></span> |
| [<span data-ttu-id="19a5c-148">可定位相机</span><span class="sxs-lookup"><span data-stu-id="19a5c-148">Locatable camera</span></span>](locatable-camera-in-unity.md) | <span data-ttu-id="19a5c-149">在混合现实应用程序中捕获照片和视频内容</span><span class="sxs-lookup"><span data-stu-id="19a5c-149">Capture photos and video content in your Mixed Reality application</span></span> |
| [<span data-ttu-id="19a5c-150">焦点</span><span class="sxs-lookup"><span data-stu-id="19a5c-150">Focus point</span></span>](focus-point-in-unity.md) | <span data-ttu-id="19a5c-151">向 HoloLens 提供有关如何最好地对当前显示的全息影像执行稳定化的提示</span><span class="sxs-lookup"><span data-stu-id="19a5c-151">Provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed</span></span> |
| [<span data-ttu-id="19a5c-152">失跟</span><span class="sxs-lookup"><span data-stu-id="19a5c-152">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="19a5c-153">处理设备无法在应用程序世界空间中定位自己的情况</span><span class="sxs-lookup"><span data-stu-id="19a5c-153">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="19a5c-154">键盘输入</span><span class="sxs-lookup"><span data-stu-id="19a5c-154">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="19a5c-155">在应用中获取来自现实世界和混合现实键盘的输入</span><span class="sxs-lookup"><span data-stu-id="19a5c-155">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="19a5c-156">4.部署到设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="19a5c-156">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="19a5c-157">准备好对全息 Unity 项目进行测试以后，下一步是导出和构建 Unity Visual Studio 解决方案。</span><span class="sxs-lookup"><span data-stu-id="19a5c-157">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="19a5c-158">有了该 VS 解决方案以后，即可使用下述三种方法之一在真实的或模拟的设备运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="19a5c-158">With that VS solution in hand, you can run your application in one of three ways on a real or simulated device.</span></span> <span data-ttu-id="19a5c-159">本部分结束后，你将能够在适合你的开发需求的任何设备或仿真器上部署应用程序。</span><span class="sxs-lookup"><span data-stu-id="19a5c-159">By the end of this section, you'll be able to deploy your application on whichever device or emulator fits your development needs.</span></span>

* [<span data-ttu-id="19a5c-160">HoloLens 或 Windows Mixed Reality 沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="19a5c-160">HoloLens or Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="19a5c-161">HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="19a5c-161">HoloLens emulator</span></span>](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [<span data-ttu-id="19a5c-162">Windows Mixed Reality 沉浸式头戴显示设备模拟器</span><span class="sxs-lookup"><span data-stu-id="19a5c-162">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="5-adding-services"></a><span data-ttu-id="19a5c-163">5.添加服务</span><span class="sxs-lookup"><span data-stu-id="19a5c-163">5. Adding services</span></span>

<span data-ttu-id="19a5c-164">在开发历程中的这个阶段，你可能希望添加服务或寻求商业部署方面的帮助。</span><span class="sxs-lookup"><span data-stu-id="19a5c-164">At this point in your development journey you might be looking to add services or for a helping hand with commercial deployment.</span></span> <span data-ttu-id="19a5c-165">将 [Azure 云服务](../mixed-reality-cloud-services.md) 与 Dynamics 365 功能集成可以在很大程度上提高项目的水平。</span><span class="sxs-lookup"><span data-stu-id="19a5c-165">Integrating [Azure Cloud Services](../mixed-reality-cloud-services.md) and Dynamics 365 features can level up your projects in a major way.</span></span> <span data-ttu-id="19a5c-166">我们已编译了几个入门点，用于探索和扩展你的混合现实知识。</span><span class="sxs-lookup"><span data-stu-id="19a5c-166">We've compiled a few starting points for you to explore and expand your Mixed Reality knowledge.</span></span>

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

<span data-ttu-id="19a5c-167">我们还提供了一个[针对其他 Azure 服务的支持文档的完整列表](../mixed-reality-cloud-services.md#standalone-unity-services)，你可以自行将这些服务添加到 Unity 项目中。</span><span class="sxs-lookup"><span data-stu-id="19a5c-167">We also have a [comprehensive list of support documentation for additional Azure services](../mixed-reality-cloud-services.md#standalone-unity-services) that you can add to your Unity projects on a self-serve basis.</span></span>

## <a name="whats-next"></a><span data-ttu-id="19a5c-168">下一步操作</span><span class="sxs-lookup"><span data-stu-id="19a5c-168">What's next?</span></span>

<span data-ttu-id="19a5c-169">开发人员的工作一直在更新，特别是在学习新工具或 SDK 时。</span><span class="sxs-lookup"><span data-stu-id="19a5c-169">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="19a5c-170">以下部分将带你进入你已完成的初学者级别资料之外的其他领域，并在你遇到问题时提供有用的资源。</span><span class="sxs-lookup"><span data-stu-id="19a5c-170">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="19a5c-171">请注意，这些主题和资源不按任何顺序排列，因此请随意查看并探索！</span><span class="sxs-lookup"><span data-stu-id="19a5c-171">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="19a5c-172">移植</span><span class="sxs-lookup"><span data-stu-id="19a5c-172">Porting</span></span>

<span data-ttu-id="19a5c-173">如果你当前有想要移植的应用，那么接下来请查看以下文章：</span><span class="sxs-lookup"><span data-stu-id="19a5c-173">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="19a5c-174">HoloToolkit/MRTK 到 MRTK v2</span><span class="sxs-lookup"><span data-stu-id="19a5c-174">HoloToolkit/MRTK to MRTK v2</span></span>](../porting-apps/porting-hl1-hl2.md)
* [<span data-ttu-id="19a5c-175">沉浸式应用移植指南</span><span class="sxs-lookup"><span data-stu-id="19a5c-175">Porting guide for immersive apps</span></span>](../porting-apps/porting-guides.md)
* [<span data-ttu-id="19a5c-176">输入移植指南</span><span class="sxs-lookup"><span data-stu-id="19a5c-176">Input porting guide</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a><span data-ttu-id="19a5c-177">教程</span><span class="sxs-lookup"><span data-stu-id="19a5c-177">Tutorials</span></span>

<span data-ttu-id="19a5c-178">如果你希望将特定的混合现实功能添加到应用程序，我们提供了一些精选的教程，可以指导你从头到尾完成整个过程。</span><span class="sxs-lookup"><span data-stu-id="19a5c-178">If you're looking to add specific Mixed Reality features to your applications, we have several curated tutorials that can run you through the process from end-to-end.</span></span> <span data-ttu-id="19a5c-179">下面列出了最受欢迎的 HoloLens 2 和 HoloLens（第一代）内容，但你可以通过访问教程概述查找整个集合。</span><span class="sxs-lookup"><span data-stu-id="19a5c-179">Our most popular HoloLens 2 and HoloLens (1st Gen) content is listed below, but you can find the entire collection by visiting the tutorials overview.</span></span>

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a><span data-ttu-id="19a5c-180">其他资源</span><span class="sxs-lookup"><span data-stu-id="19a5c-180">Additional resources</span></span>

<span data-ttu-id="19a5c-181">在你自己进入混合现实世界之前，我们建议你先阅读下面列出的与 MRTK 相关的文档。</span><span class="sxs-lookup"><span data-stu-id="19a5c-181">Before going out into the world of mixed reality on your own, we recommend taking a look at the MRTK-related documentation listed below.</span></span> <span data-ttu-id="19a5c-182">这些文章详细介绍了 MRTK 是如何工作的，是非常好的起始点，它们将使你深入了解如何使应用更高效。</span><span class="sxs-lookup"><span data-stu-id="19a5c-182">These articles are great jumping off points for understanding how MRTK works in greater detail and will give you insight into making your app more performant.</span></span>

|  <span data-ttu-id="19a5c-183">主题</span><span class="sxs-lookup"><span data-stu-id="19a5c-183">Topic</span></span>  |  <span data-ttu-id="19a5c-184">说明</span><span class="sxs-lookup"><span data-stu-id="19a5c-184">Description</span></span>  |
| --- | --- |
| [<span data-ttu-id="19a5c-185">MRTK 体系结构概述</span><span class="sxs-lookup"><span data-stu-id="19a5c-185">MRTK Architecture overview</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/Overview.html) | <span data-ttu-id="19a5c-186">更深入地了解 MRTK SDK 在项目中的工作方式</span><span class="sxs-lookup"><span data-stu-id="19a5c-186">Get a deeper understanding of how the MRTK SDK works in your projects</span></span> |
| [<span data-ttu-id="19a5c-187">设置和性能</span><span class="sxs-lookup"><span data-stu-id="19a5c-187">Settings and performance</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) | <span data-ttu-id="19a5c-188">分析你的应用、更新 Unity 设置并实现最佳的全息影像稳定性能</span><span class="sxs-lookup"><span data-stu-id="19a5c-188">Profile your app, update your Unity settings, and get the best hologram stabilization performance available</span></span> |
| [<span data-ttu-id="19a5c-189">MRTK + XR 入门</span><span class="sxs-lookup"><span data-stu-id="19a5c-189">Getting started with MRTK + XR</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html) | <span data-ttu-id="19a5c-190">转到 Unity 提供的替代 XR 管道</span><span class="sxs-lookup"><span data-stu-id="19a5c-190">Transfer over to the alternative XR pipeline provided by Unity</span></span> |

### <a name="unity-resources"></a><span data-ttu-id="19a5c-191">Unity 资源</span><span class="sxs-lookup"><span data-stu-id="19a5c-191">Unity resources</span></span>

<span data-ttu-id="19a5c-192">除了 docs.microsoft.com 上提供的此文档，Unity 还配置了适用于 Windows Mixed Reality 功能和 Unity 编辑器的文档。</span><span class="sxs-lookup"><span data-stu-id="19a5c-192">In addition to this documentation available on docs.microsoft.com, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="19a5c-193">Unity 提供的文档包括两个单独的部分。</span><span class="sxs-lookup"><span data-stu-id="19a5c-193">The Unity provided documentation includes two separate sections.</span></span>

|  <span data-ttu-id="19a5c-194">资源</span><span class="sxs-lookup"><span data-stu-id="19a5c-194">Resource</span></span>  |  <span data-ttu-id="19a5c-195">说明</span><span class="sxs-lookup"><span data-stu-id="19a5c-195">Description</span></span>  |
| --- | --- |
| [<span data-ttu-id="19a5c-196">脚本引用</span><span class="sxs-lookup"><span data-stu-id="19a5c-196">Scripting reference</span></span>](https://docs.unity3d.com/ScriptReference/) | <span data-ttu-id="19a5c-197">本文档的此部分包含 Unity 提供的脚本编写 API 的详细信息，并可在 Unity 编辑器中通过单击“帮助”>“脚本编写参考”在线进行访问</span><span class="sxs-lookup"><span data-stu-id="19a5c-197">This section of the documentation contains details of the scripting API that Unity provides and is accessible online from the Unity Editor by clicking **Help > Scripting Reference**</span></span> |
| [<span data-ttu-id="19a5c-198">手动</span><span class="sxs-lookup"><span data-stu-id="19a5c-198">Manual</span></span>](https://docs.unity3d.com/Manual/index.html) | <span data-ttu-id="19a5c-199">本手册旨在帮助你了解如何使用 Unity（从基本方法到高级方法），并可在 Unity 编辑器中通过单击“帮助”>“手册”在线进行访问</span><span class="sxs-lookup"><span data-stu-id="19a5c-199">This manual is designed to help you learn how to use Unity, from basic to advanced techniques, and is accessible online or from the Unity Editor by clicking **Help > Manual**</span></span> |

> [!div class="nextstepaction"]
> [<span data-ttu-id="19a5c-200">探索 MRTK</span><span class="sxs-lookup"><span data-stu-id="19a5c-200">Explore MRTK</span></span>](mrtk-getting-started.md)

## <a name="have-feedback"></a><span data-ttu-id="19a5c-201">想提供反馈？</span><span class="sxs-lookup"><span data-stu-id="19a5c-201">Have feedback?</span></span>

<span data-ttu-id="19a5c-202">你可在 [Unity 论坛](https://aka.ms/unityforums)上找到我们，标记 Microsoft 和下列标记的组合来帮助我们了解你要就哪种插件提供反馈：</span><span class="sxs-lookup"><span data-stu-id="19a5c-202">You can find us on the [Unity Forums](https://aka.ms/unityforums) by tagging **Microsoft** and a combination of the following tags to help us understand what plugin you're providing feedback for:</span></span>

* <span data-ttu-id="19a5c-203">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="19a5c-203">HoloLens 2</span></span> 
* <span data-ttu-id="19a5c-204">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="19a5c-204">Windows Mixed Reality</span></span>
* <span data-ttu-id="19a5c-205">OpenXR</span><span class="sxs-lookup"><span data-stu-id="19a5c-205">OpenXR</span></span>
* <span data-ttu-id="19a5c-206">XRSDK</span><span class="sxs-lookup"><span data-stu-id="19a5c-206">XRSDK</span></span>
* <span data-ttu-id="19a5c-207">旧版 XR</span><span class="sxs-lookup"><span data-stu-id="19a5c-207">Legacy XR</span></span> 

## <a name="see-also"></a><span data-ttu-id="19a5c-208">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19a5c-208">See also</span></span>

* [<span data-ttu-id="19a5c-209">混合现实工具包 v2</span><span class="sxs-lookup"><span data-stu-id="19a5c-209">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="19a5c-210">MR 基础知识 100：Unity 入门</span><span class="sxs-lookup"><span data-stu-id="19a5c-210">MR Basics 100: Getting started with Unity</span></span>](tutorials/holograms-100.md)
* [<span data-ttu-id="19a5c-211">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="19a5c-211">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="19a5c-212">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="19a5c-212">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="19a5c-213">导出和构建 Unity Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="19a5c-213">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="19a5c-214">将 Windows 命名空间与 Unity 应用配合用于 HoloLens</span><span class="sxs-lookup"><span data-stu-id="19a5c-214">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="19a5c-215">使用 Unity 和 Visual Studio 的最佳做法</span><span class="sxs-lookup"><span data-stu-id="19a5c-215">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="19a5c-216">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="19a5c-216">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="19a5c-217">移植指南</span><span class="sxs-lookup"><span data-stu-id="19a5c-217">Porting guides</span></span>](../porting-apps/porting-guides.md)