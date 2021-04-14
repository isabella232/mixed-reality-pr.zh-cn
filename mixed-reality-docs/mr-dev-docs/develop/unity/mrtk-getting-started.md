---
title: 用于 Unity 的 MRTK 简介
description: 首先了解跨平台混合现实工具包提供给新的混合现实开发人员的各项内容。
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 测试, 混合现实工具包, MRTK 版本 2, MRTK, 工具, SDK, HoloLens, HoloLens 2, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 跨平台
ms.openlocfilehash: 69b7bbf073e278c17be42241e8c6e3a47be60ee9
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300442"
---
# <a name="introducing-mrtk-for-unity"></a><span data-ttu-id="de7c3-104">用于 Unity 的 MRTK 简介</span><span class="sxs-lookup"><span data-stu-id="de7c3-104">Introducing MRTK for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="de7c3-106">混合现实工具包 (MRTK) 是什么？</span><span class="sxs-lookup"><span data-stu-id="de7c3-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="de7c3-107">MRTK 是一个很棒的开源工具包，自 HoloLens 首次发布以来就有了它。</span><span class="sxs-lookup"><span data-stu-id="de7c3-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="de7c3-108">该工具包现在的优秀，归功于我们开发人员社区的努力贡献。</span><span class="sxs-lookup"><span data-stu-id="de7c3-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> <span data-ttu-id="de7c3-109">在过去 3 年里，我们听取了开发人员社区的反馈，在构建 MRTK v2 时考虑到了大家最关注的一些事项。</span><span class="sxs-lookup"><span data-stu-id="de7c3-109">Over the past three years, we've listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="de7c3-110">MRTK for Unity 是一款面向混合现实应用程序的开源跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="de7c3-110">MRTK for Unity is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="de7c3-111">安装工具包的最简单方法是使用新的混合现实功能工具应用程序。</span><span class="sxs-lookup"><span data-stu-id="de7c3-111">The easiest way to install the toolkit is with our new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="de7c3-112">遵循我们的[安装和使用说明](welcome-to-mr-feature-tool.md)并在“混合现实工具包”类别中选择“Mixed Reality Toolkit Foundation”包。</span><span class="sxs-lookup"><span data-stu-id="de7c3-112">Follow our [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality Toolkit Foundation** package in the Mixed Reality Toolkit category.</span></span>

<span data-ttu-id="de7c3-113">用于 Unity 的 MRTK 提供跨平台的输入系统、基础组件以及用于空间交互的通用构建基块。</span><span class="sxs-lookup"><span data-stu-id="de7c3-113">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="de7c3-114">MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。</span><span class="sxs-lookup"><span data-stu-id="de7c3-114">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="de7c3-115">该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。</span><span class="sxs-lookup"><span data-stu-id="de7c3-115">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

> [!div class="nextstepaction"]
> [<span data-ttu-id="de7c3-116">试用我们的 MRTK 教程</span><span class="sxs-lookup"><span data-stu-id="de7c3-116">Try out our MRTK tutorials</span></span>](tutorials/mr-learning-base-01.md)

<span data-ttu-id="de7c3-117">有关更多功能的详细信息，请参阅[关于 MRTK 的文档](/windows/mixed-reality/mrtk-unity)。</span><span class="sxs-lookup"><span data-stu-id="de7c3-117">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="de7c3-118">MRTK v2 新增功能</span><span class="sxs-lookup"><span data-stu-id="de7c3-118">New with MRTK v2</span></span>

<span data-ttu-id="de7c3-119">我们想要强调一下我们对这些平台工具的承诺。</span><span class="sxs-lookup"><span data-stu-id="de7c3-119">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="de7c3-120">事实上，我们使用 MRTK 第 2 版开发了我们的内置体验，例如开箱即用的设置体验 (OOBE) 和混合现实提示应用程序。</span><span class="sxs-lookup"><span data-stu-id="de7c3-120">In fact, we used MRTK version 2 to develop our inbox experiences, such as the out-of-box setup experience (OOBE) and our Mixed Reality Tips application.</span></span> <span data-ttu-id="de7c3-121">另外，你还会看到首先通过 MRTK 公开的全新 HoloLens 2 功能，因为我们认为这是在我们的平台上进行开发的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="de7c3-121">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span>

### <a name="modular"></a><span data-ttu-id="de7c3-122">模块化</span><span class="sxs-lookup"><span data-stu-id="de7c3-122">Modular</span></span>

<span data-ttu-id="de7c3-123">构建它时，我们采用了模块化方式，因此，你不需要将此工具包的所有组件都放到项目中。</span><span class="sxs-lookup"><span data-stu-id="de7c3-123">We have built it in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="de7c3-124">实际上，这样做有一些好处。</span><span class="sxs-lookup"><span data-stu-id="de7c3-124">There are actually a few benefits to this.</span></span>  <span data-ttu-id="de7c3-125">缩小你的项目，使之更易于管理。</span><span class="sxs-lookup"><span data-stu-id="de7c3-125">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="de7c3-126">另外，由于我们在构建它时使用了可脚本化的对象，并且它是接口驱动型的，因此你也可以将它附带的组件替换为你自己的，这样就可以支持其他服务、系统和平台。</span><span class="sxs-lookup"><span data-stu-id="de7c3-126">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="de7c3-127">跨平台</span><span class="sxs-lookup"><span data-stu-id="de7c3-127">Cross-platform</span></span>

<span data-ttu-id="de7c3-128">说到其他平台，必须指出的是，它提供跨平台支持。</span><span class="sxs-lookup"><span data-stu-id="de7c3-128">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="de7c3-129">虽然这并不意味着我们会对每个平台提供支持，但我们可以保证：当你将生成目标切换到其他平台时，工具包代码的任何部分都不会崩溃。</span><span class="sxs-lookup"><span data-stu-id="de7c3-129">And while this doesn’t mean every single platform is supported, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="de7c3-130">模块化设计稳定可靠且具有可扩展性，因此能够支持多个平台，例如 ARCore、ARKit 和 OpenVR。</span><span class="sxs-lookup"><span data-stu-id="de7c3-130">The robustness and extensibility of the modular design sets your apps up to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="de7c3-131">高性能</span><span class="sxs-lookup"><span data-stu-id="de7c3-131">Performant</span></span>

<span data-ttu-id="de7c3-132">由于要使用移动平台，因此我们在构建它时必须时时刻刻考虑到性能。</span><span class="sxs-lookup"><span data-stu-id="de7c3-132">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="de7c3-133">这相当重要，我们需要确保这些工具不会给你造成麻烦。</span><span class="sxs-lookup"><span data-stu-id="de7c3-133">This is super important, and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="de7c3-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de7c3-134">See also</span></span>

* [<span data-ttu-id="de7c3-135">安装工具</span><span class="sxs-lookup"><span data-stu-id="de7c3-135">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="de7c3-136">混合现实功能工具</span><span class="sxs-lookup"><span data-stu-id="de7c3-136">Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
* [<span data-ttu-id="de7c3-137">使用适用于 Unity 的 MRTK 进行开发</span><span class="sxs-lookup"><span data-stu-id="de7c3-137">Developing with MRTK for Unity</span></span>](unity-development-overview.md)
* [<span data-ttu-id="de7c3-138">MRTK - 文档主页</span><span class="sxs-lookup"><span data-stu-id="de7c3-138">MRTK - Documentation home</span></span>](/windows/mixed-reality/mrtk-unity/)
* [<span data-ttu-id="de7c3-139">从 HoloToolkit/MRTK 移植到 MRTK 版本 2</span><span class="sxs-lookup"><span data-stu-id="de7c3-139">Porting from HoloToolkit/MRTK to MRTK version 2</span></span>](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide)
