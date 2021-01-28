---
title: 适用于 Unreal 的 MRTK 简介
description: 首先了解适用于 Unreal 的混合现实工具包提供给新的混合现实开发人员的各项内容。
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 测试, 混合现实工具包, MRTK 版本 2, MRTK, 工具, SDK, HoloLens, HoloLens 2, 混合现实头戴显示设备, windows 混合现实头戴显示设备, 虚拟现实头戴显示设备, 跨平台
ms.openlocfilehash: 4aa21cbee75c4c362abfd609add922ad9c922682
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584713"
---
# <a name="introducing-mrtk-for-unreal"></a><span data-ttu-id="1423d-104">适用于 Unreal 的 MRTK 简介</span><span class="sxs-lookup"><span data-stu-id="1423d-104">Introducing MRTK for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="1423d-106">混合现实工具包 (MRTK) 是什么？</span><span class="sxs-lookup"><span data-stu-id="1423d-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="1423d-107">MRTK 是一个很棒的开源工具包，自 HoloLens 首次发布以来就有了它。</span><span class="sxs-lookup"><span data-stu-id="1423d-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="1423d-108">该工具包现在的优秀，归功于我们开发人员社区的努力贡献。</span><span class="sxs-lookup"><span data-stu-id="1423d-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> 

<span data-ttu-id="1423d-109">适用于 Unreal 的混合现实工具包 (MRTK-Unreal) 是一组组件，包含插件、示例和文档，旨在为使用 Unreal Engine 开发混合现实应用程序提供帮助。</span><span class="sxs-lookup"><span data-stu-id="1423d-109">The Mixed Reality Toolkit for Unreal (MRTK-Unreal) is a set of components, in the form of plugins, samples and documentation, designed to help development of Mixed Reality applications using the Unreal Engine.</span></span> <span data-ttu-id="1423d-110">目前，该工具包包含：</span><span class="sxs-lookup"><span data-stu-id="1423d-110">Currently, the toolkit consists of:</span></span>
* <span data-ttu-id="1423d-111">[适用于 Unreal 的 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal)，可提供代码、蓝图和示例，用于实现 Hololens 2 应用程序的 UX 功能。</span><span class="sxs-lookup"><span data-stu-id="1423d-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), which provides code, blueprints, and examples to implement UX features for Hololens 2 applications.</span></span>
* <span data-ttu-id="1423d-112">[适用于 Unreal 的 Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal)，有助于优化混合现实应用程序的视觉保真，同时不超出性能预算。</span><span class="sxs-lookup"><span data-stu-id="1423d-112">[Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), which helps improve the visual fidelity of Mixed Reality applications while staying within performance budgets.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="1423d-113">查看 [GitHub 上的 MRTK 文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)，并通过 [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) 或 [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) 安装指南入门。</span><span class="sxs-lookup"><span data-stu-id="1423d-113">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) and get started with [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) or [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) installation guides.</span></span>

### <a name="modular"></a><span data-ttu-id="1423d-114">模块化</span><span class="sxs-lookup"><span data-stu-id="1423d-114">Modular</span></span>

<span data-ttu-id="1423d-115">构建 MRTK Unreal 时，我们采用了模块化方式，因此，你不需要将此工具包的所有组件都放到项目中。</span><span class="sxs-lookup"><span data-stu-id="1423d-115">We've built MRTK Unreal in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span> <span data-ttu-id="1423d-116">可以选择所需的插件并根据需要进行添加或删除。</span><span class="sxs-lookup"><span data-stu-id="1423d-116">You can pick and choose the plugins you need, and add or remove them whenever you see fit.</span></span> <span data-ttu-id="1423d-117">使用此方法可缩小你的项目，使之更易于管理。</span><span class="sxs-lookup"><span data-stu-id="1423d-117">This approach keeps your project size smaller and makes it easier to manage.</span></span>  

### <a name="performant"></a><span data-ttu-id="1423d-118">高性能</span><span class="sxs-lookup"><span data-stu-id="1423d-118">Performant</span></span>

<span data-ttu-id="1423d-119">由于要使用移动平台，因此我们在构建 MRTK Unreal 时必须时时刻刻考虑到性能。</span><span class="sxs-lookup"><span data-stu-id="1423d-119">Working with mobile platforms, we constructed MRTK Unreal with performance in mind.</span></span> <span data-ttu-id="1423d-120">这相当重要，我们需要确保这些工具不会给你造成麻烦。</span><span class="sxs-lookup"><span data-stu-id="1423d-120">This is super important and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="1423d-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1423d-121">See also</span></span>

* [<span data-ttu-id="1423d-122">安装工具</span><span class="sxs-lookup"><span data-stu-id="1423d-122">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="1423d-123">使用适用于 Unreal 的 MRTK 进行开发</span><span class="sxs-lookup"><span data-stu-id="1423d-123">Developing with MRTK for Unreal</span></span>](unreal-development-overview.md)
* [<span data-ttu-id="1423d-124">UX Tools - 安装指南 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="1423d-124">UX Tools - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [<span data-ttu-id="1423d-125">UX Tools - 文档主页 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="1423d-125">UX Tools- Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [<span data-ttu-id="1423d-126">Graphics Tools - 安装指南 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="1423d-126">Graphics Tools - Installation guide (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [<span data-ttu-id="1423d-127">Graphics Tools - 文档主页 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="1423d-127">Graphics Tools - Documentation home (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)