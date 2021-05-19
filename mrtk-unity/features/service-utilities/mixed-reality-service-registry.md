---
title: 混合现实服务注册表和 IMixedRealityServiceRegistrar
description: MixedRealityServiceRegistry 和 IMixedRealityServiceRegistrar 上的文档
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 混合现实, 开发, MRTK,
ms.openlocfilehash: 09b20537824af42d241b6c33496cedcb4f530bc7
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145236"
---
# <a name="what-are-the-mixedrealityserviceregistry-and-imixedrealityserviceregistrar"></a><span data-ttu-id="b0325-104">什么是 MixedRealityServiceRegistry 和 IMixedRealityServiceRegistrar？</span><span class="sxs-lookup"><span data-stu-id="b0325-104">What are the MixedRealityServiceRegistry and IMixedRealityServiceRegistrar?</span></span>

<span data-ttu-id="b0325-105">混合现实工具包具有两个非常相似的命名组件，它们执行相关任务： MixedRealityServiceRegistry 和 IMixedRealityServiceRegistrar。</span><span class="sxs-lookup"><span data-stu-id="b0325-105">The Mixed Reality Toolkit has two very similarly named components that perform related tasks: MixedRealityServiceRegistry and IMixedRealityServiceRegistrar.</span></span>

## <a name="mixedrealityserviceregistry"></a><span data-ttu-id="b0325-106">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="b0325-106">MixedRealityServiceRegistry</span></span>

<span data-ttu-id="b0325-107">[MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)是包含每个注册服务的实例的组件， (核心系统和扩展服务) 。</span><span class="sxs-lookup"><span data-stu-id="b0325-107">The [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) is the component that contains instances of each registered service (core systems and extension services).</span></span>

> [!NOTE]
> <span data-ttu-id="b0325-108">MixedRealityServiceRegistry 包含实现 [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 接口的对象的实例，包括 [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)。</span><span class="sxs-lookup"><span data-stu-id="b0325-108">The MixedRealityServiceRegistry contains instances of objects that implement [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface, including [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).</span></span>
>
><span data-ttu-id="b0325-109">实现 [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (IMixedRealityService) 子类的对象在 MixedRealityServiceRegistry 中显式未注册。</span><span class="sxs-lookup"><span data-stu-id="b0325-109">Objects implementing the [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (a subclass of IMixedRealityService) are explicitly not registered in the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="b0325-110">这些对象由各个服务管理 (例如：空间感知) 。</span><span class="sxs-lookup"><span data-stu-id="b0325-110">These objects are managed by the individual services (ex: Spatial Awareness).</span></span>

<span data-ttu-id="b0325-111">MixedRealityServiceRegistry 作为静态 c # 类实现，是用于在应用程序代码中获取服务实例的建议模式。</span><span class="sxs-lookup"><span data-stu-id="b0325-111">The MixedRealityServiceRegistry is implemented as a static C# class and is the recommended pattern to use to acquire service instances in application code.</span></span>

<span data-ttu-id="b0325-112">以下代码片段演示如何获取 IMixedRealityInputSystem 实例。</span><span class="sxs-lookup"><span data-stu-id="b0325-112">The following snippet demonstrates acquiring an IMixedRealityInputSystem instance.</span></span>

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a><span data-ttu-id="b0325-113">IMixedRealityServiceRegistrar</span><span class="sxs-lookup"><span data-stu-id="b0325-113">IMixedRealityServiceRegistrar</span></span>

<span data-ttu-id="b0325-114">[IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)是定义由组件实现的功能的接口，这些组件管理一个或多个服务的注册。</span><span class="sxs-lookup"><span data-stu-id="b0325-114">The [IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) is the interface that defines the functionality implemented by components that manage the registration of one or more services.</span></span> <span data-ttu-id="b0325-115">实现 IMixedRealityServiceRegistrar 的组件负责在 MixedRealityServiceRegistry 中添加和删除数据。</span><span class="sxs-lookup"><span data-stu-id="b0325-115">Components that implement IMixedRealityServiceRegistrar are responsible for adding and removing the data within the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="b0325-116">[MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit)对象是一个组件。</span><span class="sxs-lookup"><span data-stu-id="b0325-116">The [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) object is one such component.</span></span>

<span data-ttu-id="b0325-117">可在 MRTK/SDK/实验/功能文件夹中找到其他注册机构。</span><span class="sxs-lookup"><span data-stu-id="b0325-117">Other registrars can be found in the MRTK/SDK/Experimental/Features folder.</span></span> <span data-ttu-id="b0325-118">这些组件可用于向应用程序添加单个服务 (例如：空间感知) 支持。</span><span class="sxs-lookup"><span data-stu-id="b0325-118">These components can be used to add single service (ex: Spatial Awareness) support to an application.</span></span> <span data-ttu-id="b0325-119">下面列出了这些单一服务管理器。</span><span class="sxs-lookup"><span data-stu-id="b0325-119">These single service managers are listed below.</span></span>

- [<span data-ttu-id="b0325-120">BoundarySystemManager</span><span class="sxs-lookup"><span data-stu-id="b0325-120">BoundarySystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [<span data-ttu-id="b0325-121">CameraSystemManager</span><span class="sxs-lookup"><span data-stu-id="b0325-121">CameraSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [<span data-ttu-id="b0325-122">DiagnosticsSystemManager</span><span class="sxs-lookup"><span data-stu-id="b0325-122">DiagnosticsSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [<span data-ttu-id="b0325-123">InputSystemManager</span><span class="sxs-lookup"><span data-stu-id="b0325-123">InputSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [<span data-ttu-id="b0325-124">SpatialAwarenessSystemManager</span><span class="sxs-lookup"><span data-stu-id="b0325-124">SpatialAwarenessSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [<span data-ttu-id="b0325-125">TeleportSystemManager</span><span class="sxs-lookup"><span data-stu-id="b0325-125">TeleportSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

<span data-ttu-id="b0325-126">上述每个组件（InputSystemManager 除外）负责管理单个服务类型的注册和状态。</span><span class="sxs-lookup"><span data-stu-id="b0325-126">Each of the above components, with the exception of the InputSystemManager, are responsible for managing the registration and status of a single service type.</span></span> <span data-ttu-id="b0325-127">InputSystem 需要一些额外的支持服务 (例如：FocusProvider) 由 InputSystemManager 管理。</span><span class="sxs-lookup"><span data-stu-id="b0325-127">The InputSystem requires some additional support services (ex: FocusProvider) that are also managed by the InputSystemManager.</span></span>

<span data-ttu-id="b0325-128">一般情况下，由 IMixedRealityServiceRegist分定义的方法由服务管理组件在内部调用，或者由需要其他服务组件正常运行的服务调用。</span><span class="sxs-lookup"><span data-stu-id="b0325-128">In general, the methods defined by IMixedRealityServiceRegistrar are called internally by service management components or called by services that require additional service components to function correctly.</span></span> <span data-ttu-id="b0325-129">通常，应用程序代码不应调用这些方法，因为这样做可能会导致应用程序的行为不 (例如：缓存的服务实例可能会变得) 。</span><span class="sxs-lookup"><span data-stu-id="b0325-129">Application code should, generally, not call these methods as doing so may cause the application to behave unpredictably (ex: a cached service instance may become invalid).</span></span>

## <a name="see-also"></a><span data-ttu-id="b0325-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b0325-130">See also</span></span>

- [<span data-ttu-id="b0325-131">IMixedRealityServiceRegistmix API 文档</span><span class="sxs-lookup"><span data-stu-id="b0325-131">IMixedRealityServiceRegistrar API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [<span data-ttu-id="b0325-132">MixedRealityServiceRegistry API 文档</span><span class="sxs-lookup"><span data-stu-id="b0325-132">MixedRealityServiceRegistry API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
