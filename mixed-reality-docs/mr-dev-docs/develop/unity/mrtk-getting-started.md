---
title: MRTK 版本 2 入门
description: 面向有兴趣利用 MRTK 的新开发人员
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 测试, 混合现实工具包, MRTK 版本 2, MRTK, 工具, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 4513185573003510e5a7cae97ecce4cb5d2552e0
ms.sourcegitcommit: 83c9373fe5b2e07cdab921b6cab3fdd418307003
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2020
ms.locfileid: "94386203"
---
# <a name="getting-started-with-mrtk-for-unity"></a><span data-ttu-id="49e58-104">MRTK for Unity 入门</span><span class="sxs-lookup"><span data-stu-id="49e58-104">Getting started with MRTK for Unity</span></span>
![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="49e58-106">混合现实工具包 (MRTK) 是什么？</span><span class="sxs-lookup"><span data-stu-id="49e58-106">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="49e58-107">MRTK 是一个很神奇的开源工具包，自 HoloLens 首次发布后推出。它有现在这样的地位离不开为其贡献内容的开发人员社区的辛勤工作。</span><span class="sxs-lookup"><span data-stu-id="49e58-107">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="49e58-108">在过去 3 年里，我们听取了开发人员社区的反馈，在构建 MRTK v2 时考虑到了大家最关注的一些事项。</span><span class="sxs-lookup"><span data-stu-id="49e58-108">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="49e58-109">MRTK for Unity 是一款面向混合现实应用程序的开源跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="49e58-109">MRTK for Unity is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="49e58-110">MRTK 为空间交互提供了跨平台的输入系统、基础组件和常用的构建基块。</span><span class="sxs-lookup"><span data-stu-id="49e58-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="49e58-111">MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。</span><span class="sxs-lookup"><span data-stu-id="49e58-111">MRTK version 2 is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="49e58-112">该项目旨在降低准入门槛、创建混合现实应用程序，并随着我们的共同成长回馈社区。</span><span class="sxs-lookup"><span data-stu-id="49e58-112">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Setting-up-your-HoloLens-2-development-environment/player?format=ny]

<span data-ttu-id="49e58-113">要了解详细信息，请参阅 [GitHub 上的 MRTK 相关文档](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)。</span><span class="sxs-lookup"><span data-stu-id="49e58-113">See the [MRTK's documentation on GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to explore more.</span></span> <span data-ttu-id="49e58-114">若要开始使用，请按照[安装指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)页面上的步骤操作。</span><span class="sxs-lookup"><span data-stu-id="49e58-114">To get started, follow the steps on the [Installation guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) page.</span></span>


## <a name="new-with-mrtk-v2"></a><span data-ttu-id="49e58-115">MRTK v2 新增功能</span><span class="sxs-lookup"><span data-stu-id="49e58-115">New with MRTK v2</span></span>
<span data-ttu-id="49e58-116">我们想要强调一下我们对这些平台工具的承诺。</span><span class="sxs-lookup"><span data-stu-id="49e58-116">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="49e58-117">事实上，我们利用 MRTK 第 2 版开发了我们的内置体验，例如开箱即用的设置体验 (OOBE) 和混合现实提示应用程序。</span><span class="sxs-lookup"><span data-stu-id="49e58-117">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the out-of-box setup experience (OOBE) and our Mixed Reality Tips application.</span></span> <span data-ttu-id="49e58-118">另外，你还会看到首先通过 MRTK 公开的全新 HoloLens 2 功能，因为我们认为这是在我们的平台上进行开发的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="49e58-118">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="49e58-119">模块化</span><span class="sxs-lookup"><span data-stu-id="49e58-119">Modular</span></span>
<span data-ttu-id="49e58-120">构建它时，我们采用了模块化方式。因此，你不需要将此工具包的所有组件都放到项目中。</span><span class="sxs-lookup"><span data-stu-id="49e58-120">We have built it in a modular way, so there's no need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="49e58-121">实际上，这样做有一些好处。</span><span class="sxs-lookup"><span data-stu-id="49e58-121">There are actually a few benefits to this.</span></span>  <span data-ttu-id="49e58-122">缩小你的项目，使之更易于管理。</span><span class="sxs-lookup"><span data-stu-id="49e58-122">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="49e58-123">另外，由于我们在构建它时使用了可脚本化的对象，并且它是接口驱动型的，因此你也可以将它附带的组件替换为你自己的，这样就可以支持其他服务、系统和平台。</span><span class="sxs-lookup"><span data-stu-id="49e58-123">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="49e58-124">跨平台</span><span class="sxs-lookup"><span data-stu-id="49e58-124">Cross-platform</span></span>
<span data-ttu-id="49e58-125">说到其他平台，必须指出的是，它提供跨平台支持。</span><span class="sxs-lookup"><span data-stu-id="49e58-125">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="49e58-126">虽然这并不意味着我们会对每个平台提供现成的支持，但我们可以保证：当你将生成目标切换到其他平台时，工具包代码的任何部分都不会崩溃。</span><span class="sxs-lookup"><span data-stu-id="49e58-126">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="49e58-127">模块化设计稳定可靠且具有可扩展性，因此能够支持多个平台，例如 ARCore、ARKit 和 OpenVR。</span><span class="sxs-lookup"><span data-stu-id="49e58-127">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="49e58-128">高性能</span><span class="sxs-lookup"><span data-stu-id="49e58-128">Performant</span></span>
<span data-ttu-id="49e58-129">由于要使用移动平台，因此我们在构建它时必须时时刻刻考虑到性能。</span><span class="sxs-lookup"><span data-stu-id="49e58-129">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="49e58-130">这相当重要，我们需要确保这些工具不会给你造成麻烦。</span><span class="sxs-lookup"><span data-stu-id="49e58-130">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="49e58-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49e58-131">See also</span></span>
* [<span data-ttu-id="49e58-132">安装工具</span><span class="sxs-lookup"><span data-stu-id="49e58-132">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="49e58-133">MRTK - 安装指南 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="49e58-133">MRTK - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="49e58-134">MRTK - 文档主页 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="49e58-134">MRTK - Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="49e58-135">从 HoloToolkit/MRTK 移植到 MRTK 版本 2 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="49e58-135">Porting from HoloToolkit/MRTK to MRTK version 2 (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
