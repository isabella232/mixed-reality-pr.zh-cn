---
title: 系统扩展提供程序
description: MRTK 扩展插件和数据提供程序
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity，HoloLens， HoloLens 2， 混合现实， 开发， MRTK， 系统扩展，
ms.openlocfilehash: add1f443edb687edfc387a316d83443779e079f9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143503"
---
# <a name="systems-extension-services-and-data-providers"></a><span data-ttu-id="7a3fe-104">系统、扩展服务和数据访问者</span><span class="sxs-lookup"><span data-stu-id="7a3fe-104">Systems, extension services and data providers</span></span>

<span data-ttu-id="7a3fe-105">在混合现实工具包中，许多功能以服务的形式提供。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-105">In the Mixed Reality Toolkit, many of the features are delivered in the form of services.</span></span> <span data-ttu-id="7a3fe-106">服务分为三个主要类别：系统、扩展服务和数据访问者。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-106">Services are grouped into three primary categories: systems, extension services and data providers.</span></span>

## <a name="systems"></a><span data-ttu-id="7a3fe-107">系统</span><span class="sxs-lookup"><span data-stu-id="7a3fe-107">Systems</span></span>

<span data-ttu-id="7a3fe-108">系统是提供混合现实工具包核心功能的服务。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-108">Systems are services that provide the core functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="7a3fe-109">所有系统都是 接口的 [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) 实现。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-109">All systems are implementations of the [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.</span></span>

- [<span data-ttu-id="7a3fe-110">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="7a3fe-110">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="7a3fe-111">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="7a3fe-111">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md)
- [<span data-ttu-id="7a3fe-112">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="7a3fe-112">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md)
- [<span data-ttu-id="7a3fe-113">InputSystem</span><span class="sxs-lookup"><span data-stu-id="7a3fe-113">InputSystem</span></span>](../features/input/overview.md)
- [<span data-ttu-id="7a3fe-114">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="7a3fe-114">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md)
- [<span data-ttu-id="7a3fe-115">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="7a3fe-115">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [<span data-ttu-id="7a3fe-116">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="7a3fe-116">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md)

<span data-ttu-id="7a3fe-117">列出的每个系统都显示于 MixedRealityToolkit 组件的配置文件 [中](../features/profiles/profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-117">Each of the listed systems are surfaced in the MixedRealityToolkit component's configuration [profile](../features/profiles/profiles.md).</span></span>

## <a name="extensions"></a><span data-ttu-id="7a3fe-118">扩展</span><span class="sxs-lookup"><span data-stu-id="7a3fe-118">Extensions</span></span>

<span data-ttu-id="7a3fe-119">扩展服务是扩展混合现实工具包功能的组件。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-119">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="7a3fe-120">所有扩展服务都必须指定它们实现 [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) 接口。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-120">All extension services must specify that they implement the [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.</span></span>

<span data-ttu-id="7a3fe-121">有关创建扩展服务的信息，请参阅扩展 [服务一](../features/extensions/extension-services.md) 文。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-121">For information on creating extension services, please reference the [Extension services](../features/extensions/extension-services.md) article.</span></span>

<span data-ttu-id="7a3fe-122">为了可供 MRTK 访问，使用 MixedRealityToolkit 组件的配置文件的"扩展"部分注册和配置扩展服务。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-122">To be accessible to the MRTK, extension services are registered and configured using the Extensions section of the MixedRealityToolkit component's configuration profile.</span></span>

![配置扩展服务](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a><span data-ttu-id="7a3fe-124">数据提供程序</span><span class="sxs-lookup"><span data-stu-id="7a3fe-124">Data providers</span></span>

<span data-ttu-id="7a3fe-125">数据访问接口是根据其名称将数据提供给混合现实工具包服务的组件。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-125">Data providers are components that, per their name, provide data to a Mixed Reality Toolkit service.</span></span> <span data-ttu-id="7a3fe-126">所有数据访问接口都必须指定它们实现 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 接口。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-126">All data providers must specify that they implement the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="7a3fe-127">并非所有服务都需要数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-127">Not all services will require data providers.</span></span> <span data-ttu-id="7a3fe-128">在混合现实工具包的系统中，输入和空间感知系统是使用数据访问接口的唯一服务。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-128">Of the Mixed Reality Toolkit's systems, the Input and Spatial Awareness systems are the only services to utilize data providers.</span></span>

<span data-ttu-id="7a3fe-129">为了能够访问特定的 MRTK 服务，数据访问接口在服务的配置文件中注册。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-129">To be accessible to the specific MRTK service, data providers are registered in the service's configuration profile.</span></span>

<span data-ttu-id="7a3fe-130">应用程序代码通过接口访问数据提供程序 [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) 。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-130">Application code accesses data providers via the [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface.</span></span> <span data-ttu-id="7a3fe-131">若要简化访问，还可以通过 helper 类检索数据访问接口 `CoreServices` 。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-131">To simplify access, data providers can also be retrieved via the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> <span data-ttu-id="7a3fe-132">尽管 `IMixedRealityDataProvider` 继承自 `IMixedRealityService` ，但数据提供程序未注册到 `MixedRealityServiceRegistry` 。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-132">Although `IMixedRealityDataProvider` inherits from `IMixedRealityService`, data providers are not registered with the `MixedRealityServiceRegistry`.</span></span> <span data-ttu-id="7a3fe-133">若要访问数据提供程序，应用程序代码必须查询为其注册的服务实例 (例如：输入系统) 。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-133">To access data providers, application code must query the service instance for which they were registered (ex: input system).</span></span>

### <a name="input"></a><span data-ttu-id="7a3fe-134">输入</span><span class="sxs-lookup"><span data-stu-id="7a3fe-134">Input</span></span>

<span data-ttu-id="7a3fe-135">MRTK 输入系统只利用实现的数据访问接口 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-135">The MRTK input system utilizes only data providers that implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager).</span></span>

![输入系统数据提供程序](../features/images/input/RegisteredServiceProviders.PNG)

<span data-ttu-id="7a3fe-137">下面的示例演示如何访问输入模拟提供程序并切换 SmoothEyeTracking 属性。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-137">The following example demonstrates accessing the input simulation provider and toggle the SmoothEyeTracking property.</span></span>

```c#
IMixedRealityDataProviderAccess dataProviderAccess = CoreServices.InputSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IInputSimulationService inputSimulation =
        dataProviderAccess.GetDataProvider<IInputSimulationService>();

    if (inputSimulation != null)
    {
        inputSimulation.SmoothEyeTracking = !inputSimulation.SmoothEyeTracking;
    }
}
```

<span data-ttu-id="7a3fe-138">通过使用 helper 类，还可以简化访问核心输入系统的数据提供程序 `CoreServices` 。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-138">Accessing a data provider for the core input system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="7a3fe-139">输入系统只返回运行应用程序的平台支持的数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-139">The input system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="7a3fe-140">有关为 MRTK 输入系统编写数据提供程序的信息，请参阅 [创建输入系统数据提供程序](../features/input/create-data-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-140">For information on writing a data provider for the MRTK input system, please see [creating an input system data provider](../features/input/create-data-provider.md).</span></span>

### <a name="spatial-awareness"></a><span data-ttu-id="7a3fe-141">空间感知</span><span class="sxs-lookup"><span data-stu-id="7a3fe-141">Spatial awareness</span></span>

<span data-ttu-id="7a3fe-142">MRTK 空间感知系统只利用实现接口的数据访问 [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 接口。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-142">The MRTK spatial awareness system utilizes only data providers that implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![空间感知系统数据提供程序](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

<span data-ttu-id="7a3fe-144">下面的示例演示如何访问已注册的空间网格数据提供程序和更改网格的可见性。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-144">The following example demonstrates accessing the registered spatial mesh data providers and changing the visibility of the meshes.</span></span>

```c#
IMixedRealityDataProviderAccess dataProviderAccess =
    CoreServices.SpatialAwarenessSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IReadOnlyList<IMixedRealitySpatialAwarenessMeshObserver> observers =
        dataProviderAccess.GetDataProviders<IMixedRealitySpatialAwarenessMeshObserver>();

    foreach (IMixedRealitySpatialAwarenessMeshObserver observer in observers)
    {
        // Set the mesh to use the occlusion material
        observer.DisplayOption = SpatialMeshDisplayOptions.Occlusion;
    }
}
```

<span data-ttu-id="7a3fe-145">使用帮助程序类还可以简化对核心空间感知系统的数据访问 `CoreServices` 接口的访问。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-145">Accessing a data provider for the core spatial awareness system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="7a3fe-146">空间感知系统仅返回运行应用程序的平台支持的数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-146">The spatial awareness system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="7a3fe-147">有关为 MRTK 空间感知系统编写数据提供程序的信息，请参阅创建空间 [感知系统数据提供程序](../features/spatial-awareness/create-data-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="7a3fe-147">For information on writing a data provider for the MRTK spatial awareness system, please see [creating a spatial awareness system data provider](../features/spatial-awareness/create-data-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a3fe-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a3fe-148">See also</span></span>

- [<span data-ttu-id="7a3fe-149">扩展服务</span><span class="sxs-lookup"><span data-stu-id="7a3fe-149">Extension services</span></span>](../features/extensions/extension-services.md)
- [<span data-ttu-id="7a3fe-150">创建输入系统数据提供程序</span><span class="sxs-lookup"><span data-stu-id="7a3fe-150">Creating an input system data provider</span></span>](../features/input/create-data-provider.md)
- [<span data-ttu-id="7a3fe-151">创建空间感知系统数据提供程序</span><span class="sxs-lookup"><span data-stu-id="7a3fe-151">Creating a spatial awareness system system data provider</span></span>](../features/spatial-awareness/create-data-provider.md)
- [<span data-ttu-id="7a3fe-152">IMixedRealityService 接口</span><span class="sxs-lookup"><span data-stu-id="7a3fe-152">IMixedRealityService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [<span data-ttu-id="7a3fe-153">IMixedRealityDataProvider 接口</span><span class="sxs-lookup"><span data-stu-id="7a3fe-153">IMixedRealityDataProvider interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="7a3fe-154">IMixedRealityExtensionService 接口</span><span class="sxs-lookup"><span data-stu-id="7a3fe-154">IMixedRealityExtensionService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
