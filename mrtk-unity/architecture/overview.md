---
title: 体系结构概述
description: MRTK 的体系结构概述。
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK 体系结构，
ms.openlocfilehash: 431e091cb6dc0efa0f941b95f58811d57166c82f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281917"
---
# <a name="architecture-overview"></a><span data-ttu-id="8bde2-104">体系结构概述</span><span class="sxs-lookup"><span data-stu-id="8bde2-104">Architecture overview</span></span>

<span data-ttu-id="8bde2-105">若要全面了解 MRTK 的内容，本文档中包含的体系结构信息将帮助你了解以下内容：</span><span class="sxs-lookup"><span data-stu-id="8bde2-105">For an overall introduction to the contents of MRTK, the architecture information contained in this document will help you understand the following:</span></span>

- <span data-ttu-id="8bde2-106">大量 MRTK 及其连接方式</span><span class="sxs-lookup"><span data-stu-id="8bde2-106">Large pieces of MRTK and how they connect</span></span>
- <span data-ttu-id="8bde2-107">MRTK 引入的概念，在 vanilla Unity 中可能不存在</span><span class="sxs-lookup"><span data-stu-id="8bde2-107">Concepts that MRTK introduces which may not exist in vanilla Unity</span></span>
- <span data-ttu-id="8bde2-108">一些较大的系统如何 (输入) 工作</span><span class="sxs-lookup"><span data-stu-id="8bde2-108">How some of the larger systems (such as Input) work</span></span>

<span data-ttu-id="8bde2-109">本部分并不旨在指导你如何执行任务，而是指导如何构造此类任务及其原因。</span><span class="sxs-lookup"><span data-stu-id="8bde2-109">This section isn't intended to teach you how to do tasks, but rather how such tasks are structured and why.</span></span>

## <a name="many-audiences-one-toolkit"></a><span data-ttu-id="8bde2-110">许多受众，一个工具包</span><span class="sxs-lookup"><span data-stu-id="8bde2-110">Many audiences, one toolkit</span></span>

<span data-ttu-id="8bde2-111">MRTK 没有单个统一的受众。</span><span class="sxs-lookup"><span data-stu-id="8bde2-111">MRTK doesn't have a single, uniform audience.</span></span> <span data-ttu-id="8bde2-112">它用于支持从首次黑客攻击到为企业构建复杂共享体验的个人等用例。</span><span class="sxs-lookup"><span data-stu-id="8bde2-112">It's been written to support use cases ranging from first time hackathons, to individuals building complex, shared experiences for enterprise.</span></span> <span data-ttu-id="8bde2-113">某些代码和 API 可能已针对其他代码和 API 进行了多个优化 (即，MRTK 的某些部分似乎更适用于"一键配置") ，但必须注意，其中一些代码和 API 更适用于历史和资源。</span><span class="sxs-lookup"><span data-stu-id="8bde2-113">Some code and APIs may have been written that are optimized for one more than the other (i.e. some parts of the MRTK seem more optimized for "one click configure"), but it's important to note that some of those are more for historical and resourcing reasons.</span></span> <span data-ttu-id="8bde2-114">随着 MRTK 的发展，构建的功能应设计为可缩放以支持各种用例。</span><span class="sxs-lookup"><span data-stu-id="8bde2-114">As MRTK evolves, the features that get built should be designed to scale to support the range of use cases.</span></span>

<span data-ttu-id="8bde2-115">MRTK 还需要在 VR 和 AR 体验之间正常缩放。</span><span class="sxs-lookup"><span data-stu-id="8bde2-115">MRTK also has requirements to gracefully scale across VR and AR experiences.</span></span> <span data-ttu-id="8bde2-116">在 HoloLens 2 或 HoloLens 1 上部署时，应可以轻松生成可正常回退行为的应用程序，并且应该可以轻松生成面向 OpenVR 和 WMR (以及其他平台) 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="8bde2-116">It should be easy to build applications that gracefully fallback in behavior when deployed on a HoloLens 2 OR a HoloLens 1, and it should be simple to build applications that target OpenVR and WMR (and other platforms).</span></span> <span data-ttu-id="8bde2-117">虽然有时团队可能会专注于特定系统或平台的特定迭代，但长期目标是为构建混合现实体验的任何位置构建广泛的支持。</span><span class="sxs-lookup"><span data-stu-id="8bde2-117">While at times the team may focus a particular iteration on a specific system or platform, the long term goal is to build a wide range of support for wherever people are building mixed reality experiences.</span></span>

## <a name="high-level-breakdown"></a><span data-ttu-id="8bde2-118">高级细分</span><span class="sxs-lookup"><span data-stu-id="8bde2-118">High level breakdown</span></span>

<span data-ttu-id="8bde2-119">MRTK 既是一组工具，用于快速获得混合现实 (MR) 体验，也是一个应用程序框架，对其自身的运行时、扩展方式以及配置方式有意见。</span><span class="sxs-lookup"><span data-stu-id="8bde2-119">The MRTK is both a collection of tools for getting mixed reality (MR) experiences off the ground quickly, and also an application framework with opinions on its own runtime, how it should be extended, and how it should be configured.</span></span>

<span data-ttu-id="8bde2-120">从较高层面来说，可以按以下方式细分 MRTK：</span><span class="sxs-lookup"><span data-stu-id="8bde2-120">At a high level, the MRTK can be broken down in the following ways:</span></span>

![体系结构概述关系图](../features/images/architecture/MRTK_Architecture.png)

<span data-ttu-id="8bde2-122">MRTK 还包含另一组抓取包实用工具，它们几乎不依赖于 MRTK (的其余部分，以列出一些内容：生成工具、求解器、音频影响因素、平滑实用程序和线条呈现器) </span><span class="sxs-lookup"><span data-stu-id="8bde2-122">The MRTK also contains another set of grab-bag utilities that have little to no dependencies on the rest of the MRTK (to list a few: build tools, solvers, audio influencers, smoothing utilities, and line renderers)</span></span>

<span data-ttu-id="8bde2-123">从框架和运行时开始，体系结构文档的其余部分会从下到上生成，并不断前进到更有趣、更复杂的系统，例如输入。</span><span class="sxs-lookup"><span data-stu-id="8bde2-123">The remainder of the architecture documentation will build bottom up, starting from the framework and runtime, progressing to more interesting and complex systems, such as input.</span></span> <span data-ttu-id="8bde2-124">请参阅目录以继续体系结构概述。</span><span class="sxs-lookup"><span data-stu-id="8bde2-124">Please see the table of contents to continue with the architectural overview.</span></span>
