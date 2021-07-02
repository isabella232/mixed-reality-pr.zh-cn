---
title: MRTK 模块化
description: 介绍 MRTK 中的组件化。
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: eac96e309afc21f9a2b6efe9c3aef5975e4f0dff
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177008"
---
# <a name="mrtk-modularization"></a><span data-ttu-id="824f2-104">MRTK 模块化</span><span class="sxs-lookup"><span data-stu-id="824f2-104">MRTK modularization</span></span>

<span data-ttu-id="824f2-105">混合现实 Toolkit v2 的最新功能之一是组件化改进。</span><span class="sxs-lookup"><span data-stu-id="824f2-105">One of the great new features of Mixed Reality Toolkit v2 is improved componentization.</span></span> <span data-ttu-id="824f2-106">只要有可能，单个组件就会独立于基础的所有核心层。</span><span class="sxs-lookup"><span data-stu-id="824f2-106">Wherever possible, individual components are isolated from all but the core layer of the foundation.</span></span>

## <a name="minimized-dependencies"></a><span data-ttu-id="824f2-107">最小化依赖项</span><span class="sxs-lookup"><span data-stu-id="824f2-107">Minimized dependencies</span></span>

<span data-ttu-id="824f2-108">MRTK v2 特意开发为模块化，并最大程度地减少了系统服务之间的依赖关系 (例如：空间感知) 。</span><span class="sxs-lookup"><span data-stu-id="824f2-108">MRTK v2 was intentionally developed to be modular and to minimize dependencies between system services (ex: spatial awareness).</span></span>

<span data-ttu-id="824f2-109">由于某些系统服务的性质 (例如： input 和 teleportation) ，因此存在少量依赖项。</span><span class="sxs-lookup"><span data-stu-id="824f2-109">Due to the nature of some system services (ex: input and teleportation), a small number of dependencies exist.</span></span>

<span data-ttu-id="824f2-110">尽管服务预计需要一个或多个数据提供程序组件，但它们之间没有直接链接。</span><span class="sxs-lookup"><span data-stu-id="824f2-110">While it is expected that services will need one or more data provider components, there are no direct links between them.</span></span> <span data-ttu-id="824f2-111">这同样适用于 (ex：用户界面组件) 的 SDK 功能。</span><span class="sxs-lookup"><span data-stu-id="824f2-111">The same is true for SDK features (ex: User Interface components).</span></span>

## <a name="component-communication"></a><span data-ttu-id="824f2-112">组件通信</span><span class="sxs-lookup"><span data-stu-id="824f2-112">Component communication</span></span>

<span data-ttu-id="824f2-113">为了确保组件之间没有直接链接，MRTK v2 利用接口在服务、数据提供程序和应用程序代码之间进行通信。</span><span class="sxs-lookup"><span data-stu-id="824f2-113">To ensure that there are no direct links between components, MRTK v2 utilizes interfaces to communicate between services, data providers and application code.</span></span> <span data-ttu-id="824f2-114">这些接口在中定义，所有通信都通过混合现实 Toolkit 核心组件进行路由。</span><span class="sxs-lookup"><span data-stu-id="824f2-114">These interfaces are defined in and all communication is routed through the Mixed Reality Toolkit core component.</span></span>

![通过接口使用空间感知系统](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a><span data-ttu-id="824f2-116">最大程度减少 MRTK 导入占用量</span><span class="sxs-lookup"><span data-stu-id="824f2-116">Minimizing MRTK import footprint</span></span>

<span data-ttu-id="824f2-117">此时，MRTK 将导入为单个基础包， (忽略) 示例包，这是一个完全可选的包。</span><span class="sxs-lookup"><span data-stu-id="824f2-117">At this moment, the MRTK is imported as a single foundation package (ignoring for a moment the existence of the examples package, which is a completely optional package).</span></span> <span data-ttu-id="824f2-118">您可以通过手动对导入的文件进行处理来使此需求量更小，但这是一个高度手动的过程，该过程没有定义完善的指南。</span><span class="sxs-lookup"><span data-stu-id="824f2-118">It is possible to make this footprint smaller by manually cutting down on the files imported, though this is a highly manual process which doesn't have a well-defined guide.</span></span>

<span data-ttu-id="824f2-119">在导入基础包的过程中，可以取消选中任意项。</span><span class="sxs-lookup"><span data-stu-id="824f2-119">It is possible to uncheck arbitrary items during the import of the Foundation package.</span></span> <span data-ttu-id="824f2-120">但是，不建议在开发的早期阶段执行此操作，因为它可能会中断功能。</span><span class="sxs-lookup"><span data-stu-id="824f2-120">However, it's not recommended to do this at an early stage in development as it might break functionality.</span></span> <span data-ttu-id="824f2-121">在确定应用的最终功能集后，可以在以下文件夹中执行删除不需要的提供程序和服务：</span><span class="sxs-lookup"><span data-stu-id="824f2-121">After having figured out the final feature set of an app, pruning unneeded providers and services can be done on the following folders:</span></span>

- <span data-ttu-id="824f2-122">MRTK/服务</span><span class="sxs-lookup"><span data-stu-id="824f2-122">MRTK/Services</span></span>
- <span data-ttu-id="824f2-123">MRTK/提供程序</span><span class="sxs-lookup"><span data-stu-id="824f2-123">MRTK/Providers</span></span>
- <span data-ttu-id="824f2-124">MRTK/SDK/功能</span><span class="sxs-lookup"><span data-stu-id="824f2-124">MRTK/SDK/Features</span></span>

> [!NOTE]
> <span data-ttu-id="824f2-125">MRTK v2. x **_需要_** "资产/MRTK/核心" 文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="824f2-125">MRTK v2.x **_requires_** the contents of the Assets/MRTK/Core folder.</span></span>

## <a name="upcoming-features"></a><span data-ttu-id="824f2-126">即将推出的功能</span><span class="sxs-lookup"><span data-stu-id="824f2-126">Upcoming features</span></span>

### <a name="application-architecture"></a><span data-ttu-id="824f2-127">应用程序体系结构</span><span class="sxs-lookup"><span data-stu-id="824f2-127">Application architecture</span></span>

<span data-ttu-id="824f2-128">MRTK 将提供支持，使应用程序能够使用各种体系结构生成，其中包括：</span><span class="sxs-lookup"><span data-stu-id="824f2-128">The MRTK will have support to enable applications to be built with a variety of architectures, including:</span></span>

- [<span data-ttu-id="824f2-129">MixedRealityToolkit 服务定位符</span><span class="sxs-lookup"><span data-stu-id="824f2-129">MixedRealityToolkit service locator</span></span>](#mixedrealitytoolkit-service-locator)
- [<span data-ttu-id="824f2-130">单个服务</span><span class="sxs-lookup"><span data-stu-id="824f2-130">Individual services</span></span>](#individual-service-components)
- [<span data-ttu-id="824f2-131">自定义服务定位符</span><span class="sxs-lookup"><span data-stu-id="824f2-131">Custom service locator</span></span>](#custom-service-locator)
- [<span data-ttu-id="824f2-132">混合体系结构</span><span class="sxs-lookup"><span data-stu-id="824f2-132">Hybrid architecture</span></span>](#hybrid-architecture)

<span data-ttu-id="824f2-133">选择应用程序体系结构时，重要的是考虑设计灵活性和应用程序性能。</span><span class="sxs-lookup"><span data-stu-id="824f2-133">When selecting an application architecture, it is important to consider design flexibility and application performance.</span></span> <span data-ttu-id="824f2-134">此处所述的体系结构不一定适用于每个应用程序。</span><span class="sxs-lookup"><span data-stu-id="824f2-134">The architectures described here are not expected to be suitable for every application.</span></span>

#### <a name="mixedrealitytoolkit-service-locator"></a><span data-ttu-id="824f2-135">MixedRealityToolkit 服务定位符</span><span class="sxs-lookup"><span data-stu-id="824f2-135">MixedRealityToolkit service locator</span></span>

<span data-ttu-id="824f2-136">MRTK 启用 (，并自动将) 应用程序场景配置为使用默认 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 服务定位器组件。</span><span class="sxs-lookup"><span data-stu-id="824f2-136">The MRTK enables (and automatically configures) application scenes to use the default [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator component.</span></span> <span data-ttu-id="824f2-137">此组件包括支持通过配置检查器配置 MRTK 系统和数据提供程序，并管理组件 lifespans 和核心行为 (例如：何时更新) 。</span><span class="sxs-lookup"><span data-stu-id="824f2-137">This component includes support for configuring MRTK systems and data providers via configuration inspectors and manages component lifespans and core behaviors (ex: when to update).</span></span>

<span data-ttu-id="824f2-138">所有系统都在核心配置检查器中表示，无论它们在项目中是存在还是启用。</span><span class="sxs-lookup"><span data-stu-id="824f2-138">All systems are represented in the core configuration inspector, regardless of whether or not they are present or enabled in the project.</span></span> <span data-ttu-id="824f2-139">有关详细信息，请参阅 [混合现实配置指南](../configuration/mixed-reality-configuration-guide.md) 。</span><span class="sxs-lookup"><span data-stu-id="824f2-139">Please see the [Mixed Reality Configuration Guide](../configuration/mixed-reality-configuration-guide.md) for more information.</span></span>

#### <a name="individual-service-components"></a><span data-ttu-id="824f2-140">单个服务组件</span><span class="sxs-lookup"><span data-stu-id="824f2-140">Individual service components</span></span>

<span data-ttu-id="824f2-141">一些开发人员已表达需要将各个服务组件包含到应用场景层次结构中。</span><span class="sxs-lookup"><span data-stu-id="824f2-141">Some developers have expressed a desire to include individual service components into the application scene hierarchy.</span></span> <span data-ttu-id="824f2-142">若要启用此使用，服务需要在自定义注册机构中进行封装或自行注册/自我管理。</span><span class="sxs-lookup"><span data-stu-id="824f2-142">To enable this usage, services will either need to be encapsulated in a custom registrar or be self-registering / self-managing.</span></span>

<span data-ttu-id="824f2-143">自注册服务将实现 [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 并注册自身，以便应用程序代码可以通过注册表发现服务实例。</span><span class="sxs-lookup"><span data-stu-id="824f2-143">A self-registering service would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) and register itself so that application code could discover the service instance via a registry.</span></span>

<span data-ttu-id="824f2-144">自助管理服务可以在场景层次结构中实现为单一实例对象。</span><span class="sxs-lookup"><span data-stu-id="824f2-144">A self-managing service could be implemented as a singleton object in the scene hierarchy.</span></span> <span data-ttu-id="824f2-145">此对象将提供和实例属性，应用程序代码可以使用该属性来直接访问服务功能。</span><span class="sxs-lookup"><span data-stu-id="824f2-145">This object would provide and instance property which application code could use to directly access service functionality.</span></span>

#### <a name="custom-service-locator"></a><span data-ttu-id="824f2-146">自定义服务定位符</span><span class="sxs-lookup"><span data-stu-id="824f2-146">Custom service locator</span></span>

<span data-ttu-id="824f2-147">某些开发人员已经请求创建自定义服务定位器组件。</span><span class="sxs-lookup"><span data-stu-id="824f2-147">Some developers have requested the ability to create a custom service locator component.</span></span> <span data-ttu-id="824f2-148">自定义服务定位符将实现 [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 接口，并管理活动服务的生命周期和核心行为。</span><span class="sxs-lookup"><span data-stu-id="824f2-148">Custom service locators would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interface and manage the life cycle and core behaviors of active services.</span></span>

#### <a name="hybrid-architecture"></a><span data-ttu-id="824f2-149">混合体系结构</span><span class="sxs-lookup"><span data-stu-id="824f2-149">Hybrid architecture</span></span>

<span data-ttu-id="824f2-150">MRTK 将支持混合体系结构，在该体系结构中，开发人员可以根据需要或需要组合以上方法。</span><span class="sxs-lookup"><span data-stu-id="824f2-150">The MRTK will support a hybrid architecture in which developers can combine the previous approaches as needed or desired.</span></span> <span data-ttu-id="824f2-151">例如，开发人员可从 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 服务定位符开始，并添加自注册服务。</span><span class="sxs-lookup"><span data-stu-id="824f2-151">For example, a developer could start with the [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator and add a self-registering service.</span></span>

> [!NOTE]
> <span data-ttu-id="824f2-152">选择混合体系结构时，必须注意任何重复的工作 (例如：从多个组件) 获取控制器数据。</span><span class="sxs-lookup"><span data-stu-id="824f2-152">When opting for a hybrid architecture, it is important to be mindful of any duplication of work (ex: acquiring controller data from multiple components).</span></span>
