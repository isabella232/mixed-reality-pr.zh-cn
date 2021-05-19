---
title: MRTK 模块化
description: 介绍 MRTK 中的组件化。
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 04b2e6155e591a918b95aed20961a0450afe5f43
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144424"
---
# <a name="mixed-reality-toolkit-componentization"></a><span data-ttu-id="2253d-104">混合现实工具包组件化</span><span class="sxs-lookup"><span data-stu-id="2253d-104">Mixed Reality Toolkit componentization</span></span>

<span data-ttu-id="2253d-105">混合现实工具包 v2 的最新功能之一是组件化改进。</span><span class="sxs-lookup"><span data-stu-id="2253d-105">One of the great new features of Mixed Reality Toolkit v2 is improved componentization.</span></span> <span data-ttu-id="2253d-106">只要有可能，单个组件就会独立于基础的所有核心层。</span><span class="sxs-lookup"><span data-stu-id="2253d-106">Wherever possible, individual components are isolated from all but the core layer of the foundation.</span></span>

## <a name="minimized-dependencies"></a><span data-ttu-id="2253d-107">最小化依赖项</span><span class="sxs-lookup"><span data-stu-id="2253d-107">Minimized dependencies</span></span>

<span data-ttu-id="2253d-108">MRTK v2 特意开发为模块化，并最大程度地减少了系统服务之间的依赖关系 (例如：空间感知) 。</span><span class="sxs-lookup"><span data-stu-id="2253d-108">MRTK v2 was intentionally developed to be modular and to minimize dependencies between system services (ex: spatial awareness).</span></span>

<span data-ttu-id="2253d-109">由于某些系统服务的性质 (例如： input 和 teleportation) ，因此存在少量依赖项。</span><span class="sxs-lookup"><span data-stu-id="2253d-109">Due to the nature of some system services (ex: input and teleportation), a small number of dependencies exist.</span></span>

<span data-ttu-id="2253d-110">尽管服务预计需要一个或多个数据提供程序组件，但它们之间没有直接链接。</span><span class="sxs-lookup"><span data-stu-id="2253d-110">While it is expected that services will need one or more data provider components, there are no direct links between them.</span></span> <span data-ttu-id="2253d-111">这同样适用于 (ex：用户界面组件) 的 SDK 功能。</span><span class="sxs-lookup"><span data-stu-id="2253d-111">The same is true for SDK features (ex: User Interface components).</span></span>

## <a name="component-communication"></a><span data-ttu-id="2253d-112">组件通信</span><span class="sxs-lookup"><span data-stu-id="2253d-112">Component communication</span></span>

<span data-ttu-id="2253d-113">为了确保组件之间没有直接链接，MRTK v2 利用接口在服务、数据提供程序和应用程序代码之间进行通信。</span><span class="sxs-lookup"><span data-stu-id="2253d-113">To ensure that there are no direct links between components, MRTK v2 utilizes interfaces to communicate between services, data providers and application code.</span></span> <span data-ttu-id="2253d-114">这些接口在中定义，所有通信都通过混合现实工具包核心组件进行路由。</span><span class="sxs-lookup"><span data-stu-id="2253d-114">These interfaces are defined in and all communication is routed through the Mixed Reality Toolkit core component.</span></span>

![通过接口使用空间感知系统](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a><span data-ttu-id="2253d-116">最大程度减少 MRTK 导入占用量</span><span class="sxs-lookup"><span data-stu-id="2253d-116">Minimizing MRTK import footprint</span></span>

<span data-ttu-id="2253d-117">此时，MRTK 将导入为单个基础包， (忽略) 示例包，这是一个完全可选的包。</span><span class="sxs-lookup"><span data-stu-id="2253d-117">At this moment, the MRTK is imported as a single foundation package (ignoring for a moment the existence of the examples package, which is a completely optional package).</span></span> <span data-ttu-id="2253d-118">您可以通过手动对导入的文件进行处理来使此需求量更小，但这是一个高度手动的过程，该过程没有定义完善的指南。</span><span class="sxs-lookup"><span data-stu-id="2253d-118">It is possible to make this footprint smaller by manually cutting down on the files imported, though this is a highly manual process which doesn't have a well-defined guide.</span></span>

<span data-ttu-id="2253d-119">在导入基础包的过程中，可以取消选中任意项。</span><span class="sxs-lookup"><span data-stu-id="2253d-119">It is possible to uncheck arbitrary items during the import of the Foundation package.</span></span> <span data-ttu-id="2253d-120">但是，不建议在开发的早期阶段执行此操作，因为它可能会中断功能。</span><span class="sxs-lookup"><span data-stu-id="2253d-120">However, it's not recommended to do this at an early stage in development as it might break functionality.</span></span> <span data-ttu-id="2253d-121">在确定应用的最终功能集后，可以在以下文件夹中执行删除不需要的提供程序和服务：</span><span class="sxs-lookup"><span data-stu-id="2253d-121">After having figured out the final feature set of an app, pruning unneeded providers and services can be done on the following folders:</span></span>

- <span data-ttu-id="2253d-122">MRTK/服务</span><span class="sxs-lookup"><span data-stu-id="2253d-122">MRTK/Services</span></span>
- <span data-ttu-id="2253d-123">MRTK/提供程序</span><span class="sxs-lookup"><span data-stu-id="2253d-123">MRTK/Providers</span></span>
- <span data-ttu-id="2253d-124">MRTK/SDK/功能</span><span class="sxs-lookup"><span data-stu-id="2253d-124">MRTK/SDK/Features</span></span>

> [!NOTE]
> <span data-ttu-id="2253d-125">MRTK v2.x **_需要_** Assets/MRTK/Core 文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="2253d-125">MRTK v2.x **_requires_** the contents of the Assets/MRTK/Core folder.</span></span>

## <a name="upcoming-features"></a><span data-ttu-id="2253d-126">即将推出的功能</span><span class="sxs-lookup"><span data-stu-id="2253d-126">Upcoming features</span></span>

### <a name="application-architecture"></a><span data-ttu-id="2253d-127">应用程序体系结构</span><span class="sxs-lookup"><span data-stu-id="2253d-127">Application architecture</span></span>

<span data-ttu-id="2253d-128">MRTK 将支持使用各种体系结构生成应用程序，包括：</span><span class="sxs-lookup"><span data-stu-id="2253d-128">The MRTK will have support to enable applications to be built with a variety of architectures, including:</span></span>

- [<span data-ttu-id="2253d-129">MixedRealityToolkit 服务定位符</span><span class="sxs-lookup"><span data-stu-id="2253d-129">MixedRealityToolkit service locator</span></span>](#mixedrealitytoolkit-service-locator)
- [<span data-ttu-id="2253d-130">单个服务</span><span class="sxs-lookup"><span data-stu-id="2253d-130">Individual services</span></span>](#individual-service-components)
- [<span data-ttu-id="2253d-131">自定义服务定位符</span><span class="sxs-lookup"><span data-stu-id="2253d-131">Custom service locator</span></span>](#custom-service-locator)
- [<span data-ttu-id="2253d-132">混合体系结构</span><span class="sxs-lookup"><span data-stu-id="2253d-132">Hybrid architecture</span></span>](#hybrid-architecture)

<span data-ttu-id="2253d-133">选择应用程序体系结构时，必须考虑设计灵活性和应用程序性能。</span><span class="sxs-lookup"><span data-stu-id="2253d-133">When selecting an application architecture, it is important to consider design flexibility and application performance.</span></span> <span data-ttu-id="2253d-134">此处所述的体系结构不一定适合每个应用程序。</span><span class="sxs-lookup"><span data-stu-id="2253d-134">The architectures described here are not expected to be suitable for every application.</span></span>

#### <a name="mixedrealitytoolkit-service-locator"></a><span data-ttu-id="2253d-135">MixedRealityToolkit 服务定位符</span><span class="sxs-lookup"><span data-stu-id="2253d-135">MixedRealityToolkit service locator</span></span>

<span data-ttu-id="2253d-136">MRTK 启用 (，并自动) 应用程序场景以使用默认 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 服务定位器组件。</span><span class="sxs-lookup"><span data-stu-id="2253d-136">The MRTK enables (and automatically configures) application scenes to use the default [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator component.</span></span> <span data-ttu-id="2253d-137">此组件支持通过配置检查器配置 MRTK 系统和数据访问接口，并管理组件生命周期和核心行为 (例如：何时更新) 。</span><span class="sxs-lookup"><span data-stu-id="2253d-137">This component includes support for configuring MRTK systems and data providers via configuration inspectors and manages component lifespans and core behaviors (ex: when to update).</span></span>

<span data-ttu-id="2253d-138">所有系统都表示在核心配置检查器中，无论它们是否在项目中存在或启用。</span><span class="sxs-lookup"><span data-stu-id="2253d-138">All systems are represented in the core configuration inspector, regardless of whether or not they are present or enabled in the project.</span></span> <span data-ttu-id="2253d-139">有关详细信息， [请参阅混合现实](../configuration/mixed-reality-configuration-guide.md) 配置指南。</span><span class="sxs-lookup"><span data-stu-id="2253d-139">Please see the [Mixed Reality Configuration Guide](../configuration/mixed-reality-configuration-guide.md) for more information.</span></span>

#### <a name="individual-service-components"></a><span data-ttu-id="2253d-140">单个服务组件</span><span class="sxs-lookup"><span data-stu-id="2253d-140">Individual service components</span></span>

<span data-ttu-id="2253d-141">一些开发人员已表示希望将单个服务组件包括到应用程序场景层次结构中。</span><span class="sxs-lookup"><span data-stu-id="2253d-141">Some developers have expressed a desire to include individual service components into the application scene hierarchy.</span></span> <span data-ttu-id="2253d-142">若要启用此用法，服务需要封装在自定义注册机构中，或者需要自行注册/自我管理。</span><span class="sxs-lookup"><span data-stu-id="2253d-142">To enable this usage, services will either need to be encapsulated in a custom registrar or be self-registering / self-managing.</span></span>

<span data-ttu-id="2253d-143">自注册服务将实现 并 [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 注册自身，以便应用程序代码可以通过注册表发现服务实例。</span><span class="sxs-lookup"><span data-stu-id="2253d-143">A self-registering service would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) and register itself so that application code could discover the service instance via a registry.</span></span>

<span data-ttu-id="2253d-144">自我管理服务可以作为场景层次结构中的单一对象实现。</span><span class="sxs-lookup"><span data-stu-id="2253d-144">A self-managing service could be implemented as a singleton object in the scene hierarchy.</span></span> <span data-ttu-id="2253d-145">此对象将提供 和 实例属性，应用程序代码可以使用该属性直接访问服务功能。</span><span class="sxs-lookup"><span data-stu-id="2253d-145">This object would provide and instance property which application code could use to directly access service functionality.</span></span>

#### <a name="custom-service-locator"></a><span data-ttu-id="2253d-146">自定义服务定位符</span><span class="sxs-lookup"><span data-stu-id="2253d-146">Custom service locator</span></span>

<span data-ttu-id="2253d-147">某些开发人员已请求能够创建自定义服务定位器组件。</span><span class="sxs-lookup"><span data-stu-id="2253d-147">Some developers have requested the ability to create a custom service locator component.</span></span> <span data-ttu-id="2253d-148">自定义服务定位器将实现 [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 接口，并管理活动服务的生命周期和核心行为。</span><span class="sxs-lookup"><span data-stu-id="2253d-148">Custom service locators would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interface and manage the life cycle and core behaviors of active services.</span></span>

#### <a name="hybrid-architecture"></a><span data-ttu-id="2253d-149">混合体系结构</span><span class="sxs-lookup"><span data-stu-id="2253d-149">Hybrid architecture</span></span>

<span data-ttu-id="2253d-150">MRTK 将支持混合体系结构，开发人员可在其中根据需要合并以前的方法。</span><span class="sxs-lookup"><span data-stu-id="2253d-150">The MRTK will support a hybrid architecture in which developers can combine the previous approaches as needed or desired.</span></span> <span data-ttu-id="2253d-151">例如，开发人员可以先从服务 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 定位符开始，然后添加自注册服务。</span><span class="sxs-lookup"><span data-stu-id="2253d-151">For example, a developer could start with the [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator and add a self-registering service.</span></span>

> [!NOTE]
> <span data-ttu-id="2253d-152">选择混合体系结构时，必须注意任何重复的工作，例如 (多个组件获取控制器) 。</span><span class="sxs-lookup"><span data-stu-id="2253d-152">When opting for a hybrid architecture, it is important to be mindful of any duplication of work (ex: acquiring controller data from multiple components).</span></span>
