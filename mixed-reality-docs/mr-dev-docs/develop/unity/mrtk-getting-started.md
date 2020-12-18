---
title: MRTK 版本 2 入门
description: 面向有兴趣使用 MRTK 的新开发人员
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 测试, 混合现实工具包, MRTK 版本 2, MRTK, 工具, SDK, HoloLens, HoloLens 2, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 跨平台
ms.openlocfilehash: a8e85e27617d5c7d616d6db75941c5cf5808f3ce
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010118"
---
# <a name="getting-started-with-mrtk-for-unity"></a><span data-ttu-id="d90dd-104">MRTK for Unity 入门</span><span class="sxs-lookup"><span data-stu-id="d90dd-104">Getting started with MRTK for Unity</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="d90dd-106">混合现实工具包 (MRTK) 是什么？</span><span class="sxs-lookup"><span data-stu-id="d90dd-106">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="d90dd-107">MRTK 是一个很棒的开源工具包，自 HoloLens 首次发布以来就有了它。</span><span class="sxs-lookup"><span data-stu-id="d90dd-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="d90dd-108">该工具包现在的优秀，归功于我们开发人员社区的努力贡献。</span><span class="sxs-lookup"><span data-stu-id="d90dd-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> <span data-ttu-id="d90dd-109">在过去 3 年里，我们听取了开发人员社区的反馈，在构建 MRTK v2 时考虑到了大家最关注的一些事项。</span><span class="sxs-lookup"><span data-stu-id="d90dd-109">Over the past three years, we've listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="d90dd-110">MRTK for Unity 是一款面向混合现实应用程序的开源跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="d90dd-110">MRTK for Unity is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="d90dd-111">该工具包提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="d90dd-111">The toolkit provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="d90dd-112">MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。</span><span class="sxs-lookup"><span data-stu-id="d90dd-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="d90dd-113">该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。</span><span class="sxs-lookup"><span data-stu-id="d90dd-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="d90dd-114">查看 [GitHub 上的 MRTK 文档](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)，并通过[安装指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)开始使用。</span><span class="sxs-lookup"><span data-stu-id="d90dd-114">Take a look at the [MRTK's documentation on GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) and get started with the [installation guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html).</span></span>


## <a name="new-with-mrtk-v2"></a><span data-ttu-id="d90dd-115">MRTK v2 新增功能</span><span class="sxs-lookup"><span data-stu-id="d90dd-115">New with MRTK v2</span></span>
<span data-ttu-id="d90dd-116">我们想要强调一下我们对这些平台工具的承诺。</span><span class="sxs-lookup"><span data-stu-id="d90dd-116">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="d90dd-117">事实上，我们使用 MRTK 第 2 版开发了我们的内置体验，例如开箱即用的设置体验 (OOBE) 和混合现实提示应用程序。</span><span class="sxs-lookup"><span data-stu-id="d90dd-117">In fact, we used MRTK version 2 to develop our inbox experiences, such as the out-of-box setup experience (OOBE) and our Mixed Reality Tips application.</span></span> <span data-ttu-id="d90dd-118">另外，你还会看到首先通过 MRTK 公开的全新 HoloLens 2 功能，因为我们认为这是在我们的平台上进行开发的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="d90dd-118">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="d90dd-119">模块化</span><span class="sxs-lookup"><span data-stu-id="d90dd-119">Modular</span></span>
<span data-ttu-id="d90dd-120">构建它时，我们采用了模块化方式，因此，你不需要将此工具包的所有组件都放到项目中。</span><span class="sxs-lookup"><span data-stu-id="d90dd-120">We have built it in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="d90dd-121">实际上，这样做有一些好处。</span><span class="sxs-lookup"><span data-stu-id="d90dd-121">There are actually a few benefits to this.</span></span>  <span data-ttu-id="d90dd-122">缩小你的项目，使之更易于管理。</span><span class="sxs-lookup"><span data-stu-id="d90dd-122">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="d90dd-123">另外，由于我们在构建它时使用了可脚本化的对象，并且它是接口驱动型的，因此你也可以将它附带的组件替换为你自己的，这样就可以支持其他服务、系统和平台。</span><span class="sxs-lookup"><span data-stu-id="d90dd-123">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="d90dd-124">跨平台</span><span class="sxs-lookup"><span data-stu-id="d90dd-124">Cross-platform</span></span>
<span data-ttu-id="d90dd-125">说到其他平台，必须指出的是，它提供跨平台支持。</span><span class="sxs-lookup"><span data-stu-id="d90dd-125">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="d90dd-126">虽然这并不意味着我们会对每个平台提供支持，但我们可以保证：当你将生成目标切换到其他平台时，工具包代码的任何部分都不会崩溃。</span><span class="sxs-lookup"><span data-stu-id="d90dd-126">And while this doesn’t mean every single platform is supported, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="d90dd-127">模块化设计稳定可靠且具有可扩展性，因此能够支持多个平台，例如 ARCore、ARKit 和 OpenVR。</span><span class="sxs-lookup"><span data-stu-id="d90dd-127">The robustness and extensibility of the modular design sets your apps up to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="d90dd-128">高性能</span><span class="sxs-lookup"><span data-stu-id="d90dd-128">Performant</span></span>
<span data-ttu-id="d90dd-129">由于要使用移动平台，因此我们在构建它时必须时时刻刻考虑到性能。</span><span class="sxs-lookup"><span data-stu-id="d90dd-129">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="d90dd-130">这相当重要，我们需要确保这些工具不会给你造成麻烦。</span><span class="sxs-lookup"><span data-stu-id="d90dd-130">This is super important, and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="d90dd-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d90dd-131">See also</span></span>
* [<span data-ttu-id="d90dd-132">安装工具</span><span class="sxs-lookup"><span data-stu-id="d90dd-132">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="d90dd-133">MRTK - 安装指南 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="d90dd-133">MRTK - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="d90dd-134">MRTK - 文档主页 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="d90dd-134">MRTK - Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="d90dd-135">从 HoloToolkit/MRTK 移植到 MRTK 版本 2 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="d90dd-135">Porting from HoloToolkit/MRTK to MRTK version 2 (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
