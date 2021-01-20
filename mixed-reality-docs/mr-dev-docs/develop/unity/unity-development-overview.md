---
title: 针对 HoloLens 的 Unity 开发
description: 通过我们精选的检查点旅程开始在 Unity 和 HoloLens 中构建混合现实应用。
author: hferrone
ms.author: kurtie
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 混合现实, 开发, 入门, 新项目, 移植, 功能, 相机, 模拟, 仿真, 文档, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 什么是虚拟现实, 什么是增强现实, MRTK, 混合现实工具包, 空间映射, 语音输入, 可定位相机, 仿真器, Azure, 教程
ms.openlocfilehash: c5b7683574378565c71e95bc6205be3dbf92fcaf
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226436"
---
# <a name="unity-development-for-hololens"></a><span data-ttu-id="bb122-104">针对 HoloLens 的 Unity 开发</span><span class="sxs-lookup"><span data-stu-id="bb122-104">Unity development for HoloLens</span></span>

![Unity 横幅徽标](../images/unity_logo_banner.png)

<span data-ttu-id="bb122-106">在 [Unity](https://unity.com) 中生成 HoloLens [混合现实应用](../../design/app-views.md)的最快途径是使用混合现实工具包。</span><span class="sxs-lookup"><span data-stu-id="bb122-106">The fastest path to building a HoloLens [mixed reality app](../../design/app-views.md) in [Unity](https://unity.com) is with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="bb122-107">如果你尚不熟悉 Unity，我们建议你先在 Unity Learn 平台上浏览初学者级别[教程](https://unity3d.com/learn/tutorials)，然后再继续操作。</span><span class="sxs-lookup"><span data-stu-id="bb122-107">If you're brand new to Unity, we recommend that you explore the beginner level [tutorials](https://unity3d.com/learn/tutorials) on the Unity Learn platform before continuing.</span></span> <span data-ttu-id="bb122-108">访问综合性的 [Asset Store](https://www.assetstore.unity3d.com/) 和 [Unity 混合现实论坛](https://forum.unity3d.com/forums/hololens.102/)，与在线社区一起生成混合现实应用程序也是一个好主意。</span><span class="sxs-lookup"><span data-stu-id="bb122-108">It's also a good idea to visit the comprehensive [Asset Store](https://www.assetstore.unity3d.com/) and the [Unity Mixed Reality forums](https://forum.unity3d.com/forums/hololens.102/) to engage with the online community building mixed reality apps.</span></span> <span data-ttu-id="bb122-109">你永远都不知道你可能会在未知领域发现什么样的绝佳资产或解决方案。</span><span class="sxs-lookup"><span data-stu-id="bb122-109">You never know what cool assets or solutions you might find out in the wild.</span></span> <span data-ttu-id="bb122-110">准备好开始使用 MRTK 时，请前往下面的开发检查点！</span><span class="sxs-lookup"><span data-stu-id="bb122-110">When you're ready to get started with MRTK head to the development checkpoints below!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bb122-111">如果你有一个想要引入到 HoloLens 2 的现有 Unity 项目，请查看 **[移植指南](../porting-apps/porting-overview.md)** 。</span><span class="sxs-lookup"><span data-stu-id="bb122-111">Take a look at our **[porting guides](../porting-apps/porting-overview.md)** if you have an existing Unity project that you want to bring over to HoloLens 2.</span></span> <span data-ttu-id="bb122-112">我们有指南针对正在使用 HTK、MRTK v1 或 SteamVR 的项目。</span><span class="sxs-lookup"><span data-stu-id="bb122-112">We have guides for projects that are using HTK, MRTK v1, or SteamVR.</span></span>

## <a name="development-checkpoints"></a><span data-ttu-id="bb122-113">开发检查点</span><span class="sxs-lookup"><span data-stu-id="bb122-113">Development checkpoints</span></span>

<span data-ttu-id="bb122-114">使用以下检查点，将 Unity 游戏和应用程序带入混合现实的世界。</span><span class="sxs-lookup"><span data-stu-id="bb122-114">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span> <span data-ttu-id="bb122-115">如果你尚未浏览[设计全息影像示例应用程序](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)，我们建议下载并使用它来熟悉混合现实 UX 的基本知识。</span><span class="sxs-lookup"><span data-stu-id="bb122-115">If you haven't already explored the [Designing Holograms sample application](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), we recommend downloading and using it to familiarize yourself with the basics of Mixed Reality UX.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="bb122-116">1.入门</span><span class="sxs-lookup"><span data-stu-id="bb122-116">1. Getting started</span></span>

<span data-ttu-id="bb122-117">若要在 Unity 中进行开发，最简单的方法是使用混合现实工具包。</span><span class="sxs-lookup"><span data-stu-id="bb122-117">The easiest way to develop in Unity is with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="bb122-118">MRTK 将帮助你自动为混合现实设置项目，并提供一组功能以加速开发过程。</span><span class="sxs-lookup"><span data-stu-id="bb122-118">MRTK will help you automatically setup a project for Mixed Reality and provide a set of features to accelerate your development process.</span></span> <span data-ttu-id="bb122-119">本部分结束时，你将对混合现实工具包有一个基本的了解、对混合现实应用有一个正确配置的开发环境以及一个你自己构建的、可在 Unity 中正常工作的 MRTK 项目。</span><span class="sxs-lookup"><span data-stu-id="bb122-119">By the end of this section, you'll have a basic understanding of the Mixed Reality Toolkit, a properly configured development environment for Mixed Reality apps, and a working MRTK project in Unity that you built yourself.</span></span>

|  <span data-ttu-id="bb122-120">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="bb122-120">Checkpoint</span></span>  |  <span data-ttu-id="bb122-121">业务成效</span><span class="sxs-lookup"><span data-stu-id="bb122-121">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="bb122-122">什么是 MRTK？</span><span class="sxs-lookup"><span data-stu-id="bb122-122">What is MRTK?</span></span>](mrtk-getting-started.md) | <span data-ttu-id="bb122-123">通过熟悉混合现实工具包及其所提供的功能开始历程</span><span class="sxs-lookup"><span data-stu-id="bb122-123">Begin your journey by getting acquainted with the Mixed Reality Toolkit and what it has to offer</span></span> |
| [<span data-ttu-id="bb122-124">安装最新工具</span><span class="sxs-lookup"><span data-stu-id="bb122-124">Install the latest tools</span></span>](../install-the-tools.md) | <span data-ttu-id="bb122-125">下载并安装最新 Unity 包，并为混合现实设置你的项目</span><span class="sxs-lookup"><span data-stu-id="bb122-125">Download and install the latest Unity package and setup your project for mixed reality</span></span> |
| [<span data-ttu-id="bb122-126">HoloLens 2 教程系列</span><span class="sxs-lookup"><span data-stu-id="bb122-126">HoloLens 2 tutorial series</span></span>](tutorials/mr-learning-base-01.md) | <span data-ttu-id="bb122-127">深入研究 HoloLens 2 硬件的初学者级别 MRTK 教程</span><span class="sxs-lookup"><span data-stu-id="bb122-127">Dive into beginner level MRTK tutorials for HoloLens 2 hardware</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="bb122-128">若要在不导入混合现实工具包的情况下创建新的 Unity 项目，需针对 Windows Mixed Reality 手动更改一小组 Unity 设置。</span><span class="sxs-lookup"><span data-stu-id="bb122-128">If you'd like to create a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality.</span></span> <span data-ttu-id="bb122-129">这些设置分为两个类别：按项目设置和按场景设置。</span><span class="sxs-lookup"><span data-stu-id="bb122-129">These are broken down into two categories: per-project and per-scene.</span></span> <span data-ttu-id="bb122-130">有关分步过程，请参阅我们的[配置指南](configure-unity-project.md)。</span><span class="sxs-lookup"><span data-stu-id="bb122-130">Take a look at our [configuration guide](configure-unity-project.md) for the step-by-step process.</span></span>

> [!NOTE]
> <span data-ttu-id="bb122-131">在项目中设置 MRTK V2，标准的 Unity 游戏对象（例如相机）就会立即启动，为你带来坐定式体验。</span><span class="sxs-lookup"><span data-stu-id="bb122-131">Once you've setup MRTK V2 in your project, standard Unity game objects like the camera will light up immediately for a seated-scale experience.</span></span> <span data-ttu-id="bb122-132">可在[坐标系统](coordinate-systems-in-unity.md)页面上找到有关更改应用程序的体验范围的说明。</span><span class="sxs-lookup"><span data-stu-id="bb122-132">You can find instructions on changing the experience scale of your application on the [coordinate systems](coordinate-systems-in-unity.md) page.</span></span>

### <a name="2-core-building-blocks"></a><span data-ttu-id="bb122-133">2.核心构建基块</span><span class="sxs-lookup"><span data-stu-id="bb122-133">2. Core building blocks</span></span>

<span data-ttu-id="bb122-134">混合现实应用程序的所有核心构建基块的公开方式与其他 Unity API 一致。</span><span class="sxs-lookup"><span data-stu-id="bb122-134">All of the core building blocks for mixed reality applications are exposed in a manner consistent with other Unity APIs.</span></span> <span data-ttu-id="bb122-135">这些构建基块可以作为独立功能提供，也可以通过混合现实工具包提供。</span><span class="sxs-lookup"><span data-stu-id="bb122-135">These building blocks are available as standalone features and through the Mixed Reality Toolkit.</span></span> <span data-ttu-id="bb122-136">你可能不需要一次全部使用它们，但建议你尽早进行使用。</span><span class="sxs-lookup"><span data-stu-id="bb122-136">You might not need all of them at once, but we recommend exploring early on.</span></span> <span data-ttu-id="bb122-137">深入了解下面列出的核心构建基块后，你将拥有一个工具箱，其中包含了各种你可以集成到混合现实项目中的功能（通过这些功能本身或通过 MRTK 实现）。</span><span class="sxs-lookup"><span data-stu-id="bb122-137">After diving into the core building blocks listed below, you'll have a toolbox full of features you can integrate into a Mixed Reality project by themselves or through MRTK.</span></span>

[!INCLUDE[](../includes/unity-building-blocks.md)]

### <a name="3-advanced-features"></a><span data-ttu-id="bb122-138">3.高级功能</span><span class="sxs-lookup"><span data-stu-id="bb122-138">3. Advanced features</span></span>

<span data-ttu-id="bb122-139">在混合现实应用程序中起作用的其他关键功能可通过 Unity API 获得，而无需任何额外的包或设置。</span><span class="sxs-lookup"><span data-stu-id="bb122-139">Other key features that play a role in mixed reality applications are available through Unity APIs without any extra packages or setup.</span></span> <span data-ttu-id="bb122-140">可以在安装或未安装 MRTK 的情况下将这些功能添加到 Unity 项目中。</span><span class="sxs-lookup"><span data-stu-id="bb122-140">These features can be added to Unity projects with or without MRTK installed.</span></span> <span data-ttu-id="bb122-141">深入了解 Unity 提供的更高级功能后，你将能够生成更深层、更复杂的混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="bb122-141">After diving into the more advanced capabilities that Unity offers, you'll be able to build deeper, complex Mixed Reality apps.</span></span>

|  <span data-ttu-id="bb122-142">功能</span><span class="sxs-lookup"><span data-stu-id="bb122-142">Feature</span></span>  |  <span data-ttu-id="bb122-143">功能</span><span class="sxs-lookup"><span data-stu-id="bb122-143">Capabilities</span></span>  |
| --- | --- |
| [<span data-ttu-id="bb122-144">共享体验</span><span class="sxs-lookup"><span data-stu-id="bb122-144">Shared experiences</span></span>](shared-experiences-in-unity.md) | <span data-ttu-id="bb122-145">使用空间定位点共享，在空间中的固定点共同观看同一全息影像并与之交互</span><span class="sxs-lookup"><span data-stu-id="bb122-145">View and interact collectively with the same hologram at a fixed point in space using spatial anchor sharing</span></span> |
| [<span data-ttu-id="bb122-146">可定位相机</span><span class="sxs-lookup"><span data-stu-id="bb122-146">Locatable camera</span></span>](locatable-camera-in-unity.md) | <span data-ttu-id="bb122-147">在混合现实应用程序中捕获照片和视频内容</span><span class="sxs-lookup"><span data-stu-id="bb122-147">Capture photos and video content in your Mixed Reality application</span></span> |
| [<span data-ttu-id="bb122-148">焦点</span><span class="sxs-lookup"><span data-stu-id="bb122-148">Focus point</span></span>](focus-point-in-unity.md) | <span data-ttu-id="bb122-149">向 HoloLens 提供有关如何最好地对当前显示的全息影像执行稳定化的提示</span><span class="sxs-lookup"><span data-stu-id="bb122-149">Provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed</span></span> |
| [<span data-ttu-id="bb122-150">失跟</span><span class="sxs-lookup"><span data-stu-id="bb122-150">Tracking loss</span></span>](tracking-loss-in-unity.md) | <span data-ttu-id="bb122-151">处理设备无法在应用程序世界空间中定位自己的情况</span><span class="sxs-lookup"><span data-stu-id="bb122-151">Handle scenarios where your device can't locate itself in the applications world space</span></span> |
| [<span data-ttu-id="bb122-152">键盘输入</span><span class="sxs-lookup"><span data-stu-id="bb122-152">Keyboard input</span></span>](keyboard-input-in-unity.md) | <span data-ttu-id="bb122-153">在应用中获取来自现实世界和混合现实键盘的输入</span><span class="sxs-lookup"><span data-stu-id="bb122-153">Get input from real-world and Mixed Reality keyboards in your apps</span></span> |

### <a name="4-deploying-to-a-device-or-emulator"></a><span data-ttu-id="bb122-154">4.部署到设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="bb122-154">4. Deploying to a device or emulator</span></span>

<span data-ttu-id="bb122-155">准备好对全息 Unity 项目进行测试以后，下一步是导出和构建 Unity Visual Studio 解决方案。</span><span class="sxs-lookup"><span data-stu-id="bb122-155">Once you've got your holographic Unity project ready for testing, your next step is to export and build a Unity Visual Studio solution.</span></span> <span data-ttu-id="bb122-156">有了该 VS 解决方案以后，即可使用下述三种方法之一在真实的或模拟的设备运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="bb122-156">With that VS solution in hand, you can run your application in one of three ways on a real or simulated device.</span></span> <span data-ttu-id="bb122-157">本部分结束后，你将能够在适合你的开发需求的任何设备或仿真器上部署应用程序。</span><span class="sxs-lookup"><span data-stu-id="bb122-157">By the end of this section, you'll be able to deploy your application on whichever device or emulator fits your development needs.</span></span>

* [<span data-ttu-id="bb122-158">HoloLens 或 Windows Mixed Reality 沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="bb122-158">HoloLens or Windows Mixed Reality immersive headset</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
* [<span data-ttu-id="bb122-159">HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="bb122-159">HoloLens emulator</span></span>](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [<span data-ttu-id="bb122-160">Windows Mixed Reality 沉浸式头戴显示设备模拟器</span><span class="sxs-lookup"><span data-stu-id="bb122-160">Windows Mixed Reality immersive headset simulator</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="5-adding-services"></a><span data-ttu-id="bb122-161">5.添加服务</span><span class="sxs-lookup"><span data-stu-id="bb122-161">5. Adding services</span></span>

<span data-ttu-id="bb122-162">在开发历程中的这个阶段，你可能希望添加服务或寻求商业部署方面的帮助。</span><span class="sxs-lookup"><span data-stu-id="bb122-162">At this point in your development journey you might be looking to add services or for a helping hand with commercial deployment.</span></span> <span data-ttu-id="bb122-163">将 [Azure 云服务](../mixed-reality-cloud-services.md) 与 Dynamics 365 功能集成可以在很大程度上提高项目的水平。</span><span class="sxs-lookup"><span data-stu-id="bb122-163">Integrating [Azure Cloud Services](../mixed-reality-cloud-services.md) and Dynamics 365 features can level up your projects in a major way.</span></span> <span data-ttu-id="bb122-164">我们已编译了几个入门点，用于探索和扩展你的混合现实知识。</span><span class="sxs-lookup"><span data-stu-id="bb122-164">We've compiled a few starting points for you to explore and expand your Mixed Reality knowledge.</span></span>

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

<span data-ttu-id="bb122-165">我们还提供了一个[针对其他 Azure 服务的支持文档的完整列表](../mixed-reality-cloud-services.md#standalone-unity-services)，你可以自行将这些服务添加到 Unity 项目中。</span><span class="sxs-lookup"><span data-stu-id="bb122-165">We also have a [comprehensive list of support documentation for additional Azure services](../mixed-reality-cloud-services.md#standalone-unity-services) that you can add to your Unity projects on a self-serve basis.</span></span>

## <a name="whats-next"></a><span data-ttu-id="bb122-166">下一步操作</span><span class="sxs-lookup"><span data-stu-id="bb122-166">What's next?</span></span>

<span data-ttu-id="bb122-167">开发人员的工作一直在更新，特别是在学习新工具或 SDK 时。</span><span class="sxs-lookup"><span data-stu-id="bb122-167">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="bb122-168">以下部分将带你进入你已完成的初学者级别资料之外的其他领域，并在你遇到问题时提供有用的资源。</span><span class="sxs-lookup"><span data-stu-id="bb122-168">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="bb122-169">请注意，这些主题和资源不按任何顺序排列，因此请随意查看并探索！</span><span class="sxs-lookup"><span data-stu-id="bb122-169">Note that these topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="porting"></a><span data-ttu-id="bb122-170">移植</span><span class="sxs-lookup"><span data-stu-id="bb122-170">Porting</span></span>

<span data-ttu-id="bb122-171">如果你当前有想要移植的应用，那么接下来请查看以下文章：</span><span class="sxs-lookup"><span data-stu-id="bb122-171">If you have existing apps that you'd like to port over, the articles listed below are your next stop:</span></span>

* [<span data-ttu-id="bb122-172">HoloToolkit/MRTK 到 MRTK v2</span><span class="sxs-lookup"><span data-stu-id="bb122-172">HoloToolkit/MRTK to MRTK v2</span></span>](mrtk-porting-guide.md)
* [<span data-ttu-id="bb122-173">沉浸式应用移植指南</span><span class="sxs-lookup"><span data-stu-id="bb122-173">Porting guide for immersive apps</span></span>](../porting-apps/porting-guides.md)
* [<span data-ttu-id="bb122-174">输入移植指南</span><span class="sxs-lookup"><span data-stu-id="bb122-174">Input porting guide</span></span>](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a><span data-ttu-id="bb122-175">教程</span><span class="sxs-lookup"><span data-stu-id="bb122-175">Tutorials</span></span>

<span data-ttu-id="bb122-176">如果你希望将特定的混合现实功能添加到应用程序，我们提供了一些精选的教程，可以指导你从头到尾完成整个过程。</span><span class="sxs-lookup"><span data-stu-id="bb122-176">If you're looking to add specific Mixed Reality features to your applications, we have several curated tutorials that can run you through the process from end-to-end.</span></span> <span data-ttu-id="bb122-177">下面列出了最受欢迎的 HoloLens 2 和 HoloLens（第一代）内容，但你可以通过访问教程概述查找整个集合。</span><span class="sxs-lookup"><span data-stu-id="bb122-177">Our most popular HoloLens 2 and HoloLens (1st Gen) content is listed below, but you can find the entire collection by visiting the tutorials overview.</span></span>

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a><span data-ttu-id="bb122-178">其他资源</span><span class="sxs-lookup"><span data-stu-id="bb122-178">Additional resources</span></span>

<span data-ttu-id="bb122-179">在你自己进入混合现实世界之前，我们建议你先阅读下面列出的与 MRTK 相关的文档。</span><span class="sxs-lookup"><span data-stu-id="bb122-179">Before going out into the world of mixed reality on your own, we recommend taking a look at the MRTK-related documentation listed below.</span></span> <span data-ttu-id="bb122-180">这些文章详细介绍了 MRTK 是如何工作的，是非常好的起始点，它们将使你深入了解如何使应用更高效。</span><span class="sxs-lookup"><span data-stu-id="bb122-180">These articles are great jumping off points for understanding how MRTK works in greater detail and will give you insight into making your app more performant.</span></span>

|  <span data-ttu-id="bb122-181">主题</span><span class="sxs-lookup"><span data-stu-id="bb122-181">Topic</span></span>  |  <span data-ttu-id="bb122-182">说明</span><span class="sxs-lookup"><span data-stu-id="bb122-182">Description</span></span>  |
| --- | --- |
| [<span data-ttu-id="bb122-183">MRTK 体系结构概述</span><span class="sxs-lookup"><span data-stu-id="bb122-183">MRTK Architecture overview</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/Overview.html) | <span data-ttu-id="bb122-184">更深入地了解 MRTK SDK 在项目中的工作方式</span><span class="sxs-lookup"><span data-stu-id="bb122-184">Get a deeper understanding of how the MRTK SDK works in your projects</span></span> |
| [<span data-ttu-id="bb122-185">设置和性能</span><span class="sxs-lookup"><span data-stu-id="bb122-185">Settings and performance</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) | <span data-ttu-id="bb122-186">分析你的应用、更新 Unity 设置并实现最佳的全息影像稳定性能</span><span class="sxs-lookup"><span data-stu-id="bb122-186">Profile your app, update your Unity settings, and get the best hologram stabilization performance available</span></span> |
| [<span data-ttu-id="bb122-187">MRTK + XR 入门</span><span class="sxs-lookup"><span data-stu-id="bb122-187">Getting started with MRTK + XR</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html) | <span data-ttu-id="bb122-188">转到 Unity 提供的替代 XR 管道</span><span class="sxs-lookup"><span data-stu-id="bb122-188">Transfer over to the alternative XR pipeline provided by Unity</span></span> |

### <a name="unity-resources"></a><span data-ttu-id="bb122-189">Unity 资源</span><span class="sxs-lookup"><span data-stu-id="bb122-189">Unity resources</span></span>

<span data-ttu-id="bb122-190">除了 docs.microsoft.com 上提供的此文档，Unity 还配置了适用于 Windows Mixed Reality 功能和 Unity 编辑器的文档。</span><span class="sxs-lookup"><span data-stu-id="bb122-190">In addition to this documentation available on docs.microsoft.com, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="bb122-191">Unity 提供的文档包括两个单独的部分。</span><span class="sxs-lookup"><span data-stu-id="bb122-191">The Unity provided documentation includes two separate sections.</span></span>

|  <span data-ttu-id="bb122-192">资源</span><span class="sxs-lookup"><span data-stu-id="bb122-192">Resource</span></span>  |  <span data-ttu-id="bb122-193">说明</span><span class="sxs-lookup"><span data-stu-id="bb122-193">Description</span></span>  |
| --- | --- |
| [<span data-ttu-id="bb122-194">脚本引用</span><span class="sxs-lookup"><span data-stu-id="bb122-194">Scripting reference</span></span>](https://docs.unity3d.com/ScriptReference/) | <span data-ttu-id="bb122-195">本文档的此部分包含 Unity 提供的脚本编写 API 的详细信息，并可在 Unity 编辑器中通过单击“帮助”>“脚本编写参考”在线进行访问</span><span class="sxs-lookup"><span data-stu-id="bb122-195">This section of the documentation contains details of the scripting API that Unity provides and is accessible online from the Unity Editor by clicking **Help > Scripting Reference**</span></span> |
| [<span data-ttu-id="bb122-196">手动</span><span class="sxs-lookup"><span data-stu-id="bb122-196">Manual</span></span>](https://docs.unity3d.com/Manual/index.html) | <span data-ttu-id="bb122-197">本手册旨在帮助你了解如何使用 Unity（从基本方法到高级方法），并可在 Unity 编辑器中通过单击“帮助”>“手册”在线进行访问</span><span class="sxs-lookup"><span data-stu-id="bb122-197">This manual is designed to help you learn how to use Unity, from basic to advanced techniques, and is accessible online or from the Unity Editor by clicking **Help > Manual**</span></span> |

> [!div class="nextstepaction"]
> [<span data-ttu-id="bb122-198">探索 MRTK</span><span class="sxs-lookup"><span data-stu-id="bb122-198">Explore MRTK</span></span>](mrtk-getting-started.md)

## <a name="have-feedback"></a><span data-ttu-id="bb122-199">想提供反馈？</span><span class="sxs-lookup"><span data-stu-id="bb122-199">Have feedback?</span></span>

<span data-ttu-id="bb122-200">你可在 [Unity 论坛](https://aka.ms/unityforums)上找到我们，标记 Microsoft 和下列标记的组合来帮助我们了解你要就哪种插件提供反馈：</span><span class="sxs-lookup"><span data-stu-id="bb122-200">You can find us on the [Unity Forums](https://aka.ms/unityforums) by tagging **Microsoft** and a combination of the following tags to help us understand what plugin you're providing feedback for:</span></span>

* <span data-ttu-id="bb122-201">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bb122-201">HoloLens 2</span></span> 
* <span data-ttu-id="bb122-202">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bb122-202">Windows Mixed Reality</span></span>
* <span data-ttu-id="bb122-203">OpenXR</span><span class="sxs-lookup"><span data-stu-id="bb122-203">OpenXR</span></span>
* <span data-ttu-id="bb122-204">XRSDK</span><span class="sxs-lookup"><span data-stu-id="bb122-204">XRSDK</span></span>
* <span data-ttu-id="bb122-205">旧版 XR</span><span class="sxs-lookup"><span data-stu-id="bb122-205">Legacy XR</span></span> 

## <a name="see-also"></a><span data-ttu-id="bb122-206">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb122-206">See also</span></span>

* [<span data-ttu-id="bb122-207">混合现实工具包 v2</span><span class="sxs-lookup"><span data-stu-id="bb122-207">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="bb122-208">MR 基础知识 100：Unity 入门</span><span class="sxs-lookup"><span data-stu-id="bb122-208">MR Basics 100: Getting started with Unity</span></span>](tutorials/holograms-100.md)
* [<span data-ttu-id="bb122-209">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="bb122-209">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="bb122-210">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="bb122-210">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="bb122-211">导出和构建 Unity Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="bb122-211">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="bb122-212">将 Windows 命名空间与 Unity 应用配合用于 HoloLens</span><span class="sxs-lookup"><span data-stu-id="bb122-212">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="bb122-213">使用 Unity 和 Visual Studio 的最佳做法</span><span class="sxs-lookup"><span data-stu-id="bb122-213">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="bb122-214">Unity 播放模式</span><span class="sxs-lookup"><span data-stu-id="bb122-214">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="bb122-215">移植指南</span><span class="sxs-lookup"><span data-stu-id="bb122-215">Porting guides</span></span>](../porting-apps/porting-guides.md)
