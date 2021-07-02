---
title: 路线图
description: 用于概述 MRTK 路线图的文档。
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
keywords: Unity、HoloLens、HoloLens 2、混合现实、开发、MRTK
ms.openlocfilehash: 7385d516e986c1602ad59e2825aa6d1262504727
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175585"
---
# <a name="roadmap"></a><span data-ttu-id="65a88-104">路线图</span><span class="sxs-lookup"><span data-stu-id="65a88-104">Roadmap</span></span>

<span data-ttu-id="65a88-105">本文档概述了混合现实Toolkit。</span><span class="sxs-lookup"><span data-stu-id="65a88-105">This document outlines the roadmap of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="65a88-106">请注意，以下内容反映了开发中的工作，目标日期反映了估计值。</span><span class="sxs-lookup"><span data-stu-id="65a88-106">Please note that the following reflects work that is in development and target dates reflect estimates.</span></span>

## <a name="current-release"></a><span data-ttu-id="65a88-107">当前版本</span><span class="sxs-lookup"><span data-stu-id="65a88-107">Current release</span></span>

<span data-ttu-id="65a88-108">Microsoft Mixed Reality Toolkit v2.6</span><span class="sxs-lookup"><span data-stu-id="65a88-108">Microsoft Mixed Reality Toolkit v2.6</span></span>

## <a name="upcoming-releases"></a><span data-ttu-id="65a88-109">即将发布的版本</span><span class="sxs-lookup"><span data-stu-id="65a88-109">Upcoming releases</span></span>

| <span data-ttu-id="65a88-110">产品</span><span class="sxs-lookup"><span data-stu-id="65a88-110">Product</span></span> | <span data-ttu-id="65a88-111">说明</span><span class="sxs-lookup"><span data-stu-id="65a88-111">Description</span></span> | <span data-ttu-id="65a88-112">时间线</span><span class="sxs-lookup"><span data-stu-id="65a88-112">Timeline</span></span> | <span data-ttu-id="65a88-113">Project板</span><span class="sxs-lookup"><span data-stu-id="65a88-113">Project board</span></span> |
| --- | --- | --- | --- |
| [<span data-ttu-id="65a88-114">MRTK V2.7</span><span class="sxs-lookup"><span data-stu-id="65a88-114">MRTK V2.7</span></span>](#270) | <span data-ttu-id="65a88-115">MRTK 的下一次迭代</span><span class="sxs-lookup"><span data-stu-id="65a88-115">Next iteration of MRTK</span></span> | <span data-ttu-id="65a88-116">2021 年 5 月</span><span class="sxs-lookup"><span data-stu-id="65a88-116">May 2021</span></span> | https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14 |

<span data-ttu-id="65a88-117">发布以主题为中心 (例如：大型) 区域，计划大约每 8-12 周发布一次。</span><span class="sxs-lookup"><span data-stu-id="65a88-117">Releases are centered around themes (ex: large feature areas) and are scheduled to occur approximately every 8-12 weeks.</span></span>

<span data-ttu-id="65a88-118">发布详细信息（包括积压工作项）可在GitHub[页上找到](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones)。</span><span class="sxs-lookup"><span data-stu-id="65a88-118">Release details, including backlog items, can be found on the [GitHub milestone pages](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones).</span></span> <span data-ttu-id="65a88-119">也可在 上找到完整的一组未[解决问题GitHub。](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)</span><span class="sxs-lookup"><span data-stu-id="65a88-119">The complete set of open issues can also be found on [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

## <a name="mixed-reality-toolkit-mrtk-roadmap"></a><span data-ttu-id="65a88-120">混合现实Toolkit (MRTK) 路线图</span><span class="sxs-lookup"><span data-stu-id="65a88-120">Mixed Reality Toolkit (MRTK) roadmap</span></span>

<span data-ttu-id="65a88-121">混合现实Toolkit设计构建为跨 MR/AR/VR/XR 平台。</span><span class="sxs-lookup"><span data-stu-id="65a88-121">The Mixed Reality Toolkit is built to be cross MR/AR/VR/XR platform by design.</span></span> <span data-ttu-id="65a88-122">该工具包当前支持 Unity 2019.4.x 和 Unity 2018.4.x。</span><span class="sxs-lookup"><span data-stu-id="65a88-122">The toolkit currently supports Unity 2019.4.x and Unity 2018.4.x.</span></span>

> <span data-ttu-id="65a88-123">Unity 发布 LTS (长期) 产品时，混合现实Toolkit将更新到 LTS 版本。</span><span class="sxs-lookup"><span data-stu-id="65a88-123">When Unity releases an LTS (Long Term Support) product, the Mixed Reality Toolkit will update to the LTS release.</span></span> <span data-ttu-id="65a88-124">尽管混合现实Toolkit在最新的非 beta 版本上运行 (例如：2020.1) Unity 技术分支版本，但不受官方支持。</span><span class="sxs-lookup"><span data-stu-id="65a88-124">Although the Mixed Reality Toolkit runs on the latest non-beta (ex: 2020.1) tech branch version of Unity, it is not officially supported.</span></span>

### <a name="270"></a><span data-ttu-id="65a88-125">2.7.0</span><span class="sxs-lookup"><span data-stu-id="65a88-125">2.7.0</span></span>

<span data-ttu-id="65a88-126">我们目前正在规划 2.7.0 版本，并且即将推出更多更新！</span><span class="sxs-lookup"><span data-stu-id="65a88-126">We are currently planning the 2.7.0 release and will have more updates for you soon!</span></span>
<span data-ttu-id="65a88-127">有关发布的最新状态，请访问里程碑 [页](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14)。</span><span class="sxs-lookup"><span data-stu-id="65a88-127">For the latest status of the release, please visit the [milestone page](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).</span></span>

<span data-ttu-id="65a88-128">状态：规划</span><span class="sxs-lookup"><span data-stu-id="65a88-128">Status: Planning</span></span>

<span data-ttu-id="65a88-129">目标时间线：2021 年 5 月</span><span class="sxs-lookup"><span data-stu-id="65a88-129">Target Timeline: May 2021</span></span>

<span data-ttu-id="65a88-130">主题：</span><span class="sxs-lookup"><span data-stu-id="65a88-130">Themes:</span></span>

- <span data-ttu-id="65a88-131">稳定性</span><span class="sxs-lookup"><span data-stu-id="65a88-131">Stability</span></span> 
- <span data-ttu-id="65a88-132">平台扩展：OpenXR</span><span class="sxs-lookup"><span data-stu-id="65a88-132">Platform Expansion: OpenXR</span></span>
- <span data-ttu-id="65a88-133">用户体验</span><span class="sxs-lookup"><span data-stu-id="65a88-133">User Experience</span></span>
- <span data-ttu-id="65a88-134">开发人员教育</span><span class="sxs-lookup"><span data-stu-id="65a88-134">Developer Education</span></span>
- <span data-ttu-id="65a88-135">打包</span><span class="sxs-lookup"><span data-stu-id="65a88-135">Packaging</span></span>

<span data-ttu-id="65a88-136">**稳定性**</span><span class="sxs-lookup"><span data-stu-id="65a88-136">**Stability**</span></span>

<span data-ttu-id="65a88-137">质量和稳定性是此版本和所有 Microsoft Mixed Reality 版本Toolkit重。</span><span class="sxs-lookup"><span data-stu-id="65a88-137">Quality and stability are the top priority for this and all Microsoft Mixed Reality Toolkit releases.</span></span> <span data-ttu-id="65a88-138">我们将继续确定影响 MRTK 组件稳定性的客户和合作伙伴问题的优先级。</span><span class="sxs-lookup"><span data-stu-id="65a88-138">We will continue to prioritize customer and partner issues that impact the stability of MRTK components.</span></span>

<span data-ttu-id="65a88-139">**平台扩展：OpenXR**</span><span class="sxs-lookup"><span data-stu-id="65a88-139">**Platform Expansion: OpenXR**</span></span>

<span data-ttu-id="65a88-140">MRTK 团队通过 [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672)支持混合现实开放的未来。</span><span class="sxs-lookup"><span data-stu-id="65a88-140">The MRTK team supports the open future of mixed reality through [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672).</span></span> <span data-ttu-id="65a88-141">对 OpenXR 的支持目前正在开发中，MRTK 2.5.2 中发布了初始预览版支持。</span><span class="sxs-lookup"><span data-stu-id="65a88-141">Support for OpenXR is currently under development, with initial preview support released in MRTK 2.5.2.</span></span>

<span data-ttu-id="65a88-142">**用户体验**</span><span class="sxs-lookup"><span data-stu-id="65a88-142">**User Experience**</span></span>

<span data-ttu-id="65a88-143">我们正在侦听你关于 MRTK 的反馈，并针对：</span><span class="sxs-lookup"><span data-stu-id="65a88-143">We're listening to your feedback about MRTK and have continued plans for:</span></span>

- <span data-ttu-id="65a88-144">Bug 修复</span><span class="sxs-lookup"><span data-stu-id="65a88-144">Bug fixes</span></span>
- <span data-ttu-id="65a88-145">使 MRTK UX 控件更易于理解</span><span class="sxs-lookup"><span data-stu-id="65a88-145">Making MRTK UX controls easier to understand</span></span>
- <span data-ttu-id="65a88-146">HoloLensShell 奇偶校验</span><span class="sxs-lookup"><span data-stu-id="65a88-146">HoloLens Shell parity</span></span>
- <span data-ttu-id="65a88-147">确保功能不会回归的测试</span><span class="sxs-lookup"><span data-stu-id="65a88-147">Tests to ensure features do not regress</span></span>

<span data-ttu-id="65a88-148">**开发人员教育**</span><span class="sxs-lookup"><span data-stu-id="65a88-148">**Developer Education**</span></span>

<span data-ttu-id="65a88-149">我们已将开发人员文档从 Github 迁移到新的文档平台！</span><span class="sxs-lookup"><span data-stu-id="65a88-149">We've migrated our developer documentation from Github to a new docs platform!</span></span> <span data-ttu-id="65a88-150">我们希望收到你的反馈，以便我们可以继续改进开发人员文档体验。</span><span class="sxs-lookup"><span data-stu-id="65a88-150">We want to hear your feedback so we can continue to improve our developer documentation experience.</span></span>
<span data-ttu-id="65a88-151">目前，我们在混合现实文档的不同部分中提供了 [MRTK](/windows/mixed-reality/develop/unity/tutorials) 教程。我们将迁移这些教程，以与 MRTK 文档的其余部分一起使用。</span><span class="sxs-lookup"><span data-stu-id="65a88-151">We currently have [MRTK tutorials](/windows/mixed-reality/develop/unity/tutorials) that live in a different section of Mixed Reality docs. We will be migrating these tutorials to live with the rest of the MRTK documentation.</span></span> 

<span data-ttu-id="65a88-152">**打包**</span><span class="sxs-lookup"><span data-stu-id="65a88-152">**Packaging**</span></span>

<span data-ttu-id="65a88-153">混合 [现实功能工具](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) 是开发人员发现、更新混合现实功能包以及将其添加到 Unity 项目中的一种新方式。</span><span class="sxs-lookup"><span data-stu-id="65a88-153">The [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="65a88-154">你可以按名称或类别搜索包，查看其依赖项，甚至在导入之前查看项目清单文件的建议更改。</span><span class="sxs-lookup"><span data-stu-id="65a88-154">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="65a88-155">我们计划在响应功能请求和 bug 时更新混合现实功能工具。</span><span class="sxs-lookup"><span data-stu-id="65a88-155">We intend to make updates to the Mixed Reality Feature Tool as we respond to feature requests and bugs.</span></span>

## <a name="backlog"></a><span data-ttu-id="65a88-156">积压工作 (backlog) </span><span class="sxs-lookup"><span data-stu-id="65a88-156">Backlog</span></span>

<span data-ttu-id="65a88-157">以下列表突出显示了 MRTK 团队打算寻求的一些关键投资。</span><span class="sxs-lookup"><span data-stu-id="65a88-157">The following list highlights some of the key investments the MRTK team intends to pursue.</span></span>

- <span data-ttu-id="65a88-158">平台扩展</span><span class="sxs-lookup"><span data-stu-id="65a88-158">Platform expansion</span></span>
- <span data-ttu-id="65a88-159">扩展性</span><span class="sxs-lookup"><span data-stu-id="65a88-159">Extensibility</span></span>
- <span data-ttu-id="65a88-160">模块化</span><span class="sxs-lookup"><span data-stu-id="65a88-160">Modularity</span></span>
- <span data-ttu-id="65a88-161">辅助功能</span><span class="sxs-lookup"><span data-stu-id="65a88-161">Accessibility features</span></span>
- <span data-ttu-id="65a88-162">全球化增强功能</span><span class="sxs-lookup"><span data-stu-id="65a88-162">Globalization enhancements</span></span>
- <span data-ttu-id="65a88-163">云服务支持</span><span class="sxs-lookup"><span data-stu-id="65a88-163">Cloud service support</span></span>
- <span data-ttu-id="65a88-164">工具</span><span class="sxs-lookup"><span data-stu-id="65a88-164">Tools</span></span>
